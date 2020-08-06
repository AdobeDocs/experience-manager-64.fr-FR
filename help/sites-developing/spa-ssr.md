---
title: SPA et rendu côté serveur
seo-title: SPA et rendu côté serveur
description: 'null'
seo-description: 'null'
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
translation-type: tm+mt
source-git-commit: 0e7f4a78f63808bea2aa7a5abbb31e7e5b9d21b3
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 1%

---


# SPA et rendu côté serveur{#spa-and-server-side-rendering}

>[!NOTE]
>La fonctionnalité Editeur d’application monopage (SPA) nécessite [AEM Service Pack 2](https://helpx.adobe.com/fr/experience-manager/6-4/release-notes/sp-release-notes.html) 6.4 ou ultérieur.
>
>L’éditeur d’applications monopages est la solution recommandée pour les projets qui nécessitent un rendu côté client basé sur la structure d’applications monopages (par exemple, Réagir ou Angular).

>[!NOTE]
>
>AEM version 6.4.5.0 ou ultérieure est requise pour utiliser les fonctions de rendu côté serveur SPA comme décrit dans ce document.

## Présentation {#overview}

Les applications d’une seule page (SPA) peuvent offre à l’utilisateur une expérience riche et dynamique qui réagit et se comporte de manière familière, souvent comme les applications natives. [Pour ce faire, le client doit charger le contenu à l’avance, puis gérer l’interaction](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) utilisateur de manière intensive, ce qui réduit le volume de communication nécessaire entre le client et le serveur, ce qui rend l’application plus réactive.

Toutefois, cela peut entraîner des temps de chargement initiaux plus longs, en particulier si le SPA est volumineux et riche en contenu. Pour optimiser les temps de chargement, une partie du contenu peut être rendue côté serveur. L’utilisation du rendu côté serveur (SSR) peut accélérer le chargement initial de la page, puis transmettre le rendu au client.

## Quand utiliser SSR {#when-to-use-ssr}

SSR n&#39;est pas requis pour tous les projets. Bien que l&#39;AEM appuie pleinement JS SSR pour SPA, l&#39;Adobe ne recommande pas sa mise en oeuvre systématique pour chaque projet.

Lorsque vous décidez de mettre en oeuvre des SSR, vous devez d&#39;abord estimer la complexité, les efforts et les coûts supplémentaires associés à l&#39;ajout de SSR de façon réaliste pour le projet, y compris la maintenance à long terme. Une architecture SSR ne devrait être choisie que lorsque la valeur ajoutée dépasse clairement les coûts estimés.

Le SSR fournit habituellement une certaine valeur lorsqu&#39;il y a un &quot;oui&quot; clair à l&#39;une ou l&#39;autre des questions suivantes :

* **SEO :** Est-il toujours nécessaire d&#39;utiliser la SSR pour que votre site soit correctement indexé par les moteurs de recherche qui génèrent du trafic ? Gardez à l’esprit que les principaux moteurs de recherche évaluent désormais JS.
* **Vitesse de la page :** Est-ce que la SSR améliore la vitesse de façon mesurable dans les environnements réels et ajoute à l&#39;expérience globale de l&#39;utilisateur ?

Ce n&#39;est que lorsqu&#39;au moins une de ces deux questions reçoit une réponse avec un &quot;oui&quot; clair pour votre projet que l&#39;Adobe recommande la mise en oeuvre de la SSR. Les sections suivantes décrivent comment utiliser Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-io-runtime}

Si vous êtes [sûr que votre projet nécessite la mise en oeuvre de la SSR](#when-to-use-ssr), la solution recommandée par l&#39;Adobe est d&#39;utiliser Adobe I/O Runtime.

Pour plus d’informations sur Adobe I/O Runtime, voir

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - pour une présentation du service
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - pour obtenir une documentation détaillée sur la plateforme

Les sections suivantes décrivent comment Adobe I/O Runtime peut être utilisé pour implémenter la technologie SSR pour votre application monopage dans deux modèles différents :

* [Flux de communication AEM](#aem-driven-communication-flow)
* [Flux de communication Adobe E/S piloté par l&#39;exécution](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>Adobe recommande une instance Adobe I/O Runtime distincte pour chaque environnement AEM (auteur, publication, étape, etc.).

## Configuration du rendu de contenu distant {#remote-content-renderer-configuration}

AEM doit savoir où le contenu rendu à distance peut être récupéré. Quel que soit [le modèle que vous choisissiez de mettre en oeuvre pour SSR](#adobe-io-runtime), vous devrez indiquer pour AEM comment accéder à ce service de rendu à distance.

Ceci est effectué via le service **RemoteContentRenderer - Configuration Factory** OSGi. Recherchez la chaîne &quot;RemoteContentRenderer&quot; dans la console de configuration de la console Web à `http://<host>:<port>/system/console/configMgr`.

![](assets/rendererconfig.png)

Les champs suivants sont disponibles pour la configuration :

* **Modèle** de chemin de contenu - expression régulière afin de correspondre à une partie du contenu, si nécessaire
* **URL** du point de terminaison distant - URL du point de terminaison responsable de la génération du contenu
   * Utilisez le protocole HTTPS sécurisé si ce n&#39;est pas sur le réseau local.
* **En-têtes** de demande supplémentaires - En-têtes supplémentaires à ajouter à la demande envoyée au point de terminaison distant
   * Modèle: `key=value`
* **Délai d’expiration** de la demande - Délai d’expiration de la demande d’hôte distant en millisecondes

>[!NOTE]
>
>Que vous choisissiez d’implémenter le flux [de communication](#aem-driven-communication-flow) AEM ou le flux [de communication](#adobe-io-driven-communication-flow)Adobe I/O Runtime, vous devez définir une configuration de rendu de contenu distant.
>
>Cette configuration doit également être définie si vous choisissez d’ [utiliser un serveur Node.js personnalisé](#using-node-js).

>[!NOTE]
>
>Cette configuration exploite le [Remote Content Renderer](#remote-content-renderer), qui offre des options d’extension et de personnalisation supplémentaires.

## Flux de communication AEM {#aem-driven-communication-flow}

Lors de l’utilisation de la technologie SSR, le processus [d’interaction des](/help/sites-developing/spa-overview.md#workflow) composants des applications monopages en AEM inclut une phase au cours de laquelle le contenu initial de l’application est généré par Adobe I/O Runtime.

1. Le navigateur demande le contenu de la SSR à AEM.
1. AEM publie le modèle à Adobe I/O Runtime.
1. Adobe I/O Runtime renvoie le contenu généré
1. AEM diffuse le code HTML renvoyé par Adobe I/O Runtime via le modèle HTML du composant de page d’arrière-plan.

![rendu côté serveur-cms-drivenaemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Flux de communication piloté par Adobe I/O Runtime {#adobe-io-driven-communication-flow}

La section Flux [de communication](#aem-driven-communication-flow) AEM pilotée par AEM décrit l’implémentation standard et recommandée du rendu côté serveur en ce qui concerne les applications monopages dans AEM, où l’effectue le démarrage et la diffusion du contenu.

Une autre solution consiste à mettre en oeuvre la SSR de sorte que Adobe I/O Runtime soit responsable de l&#39;amorçage, inversant ainsi le flux de communication.

Les deux modèles sont valides et pris en charge par AEM. Toutefois, il faut tenir compte des avantages et des inconvénients de chacun avant de mettre en oeuvre un modèle particulier.

| Démarrage | Avantages | Inconvénients |
|---|---|---|
| via AEM | AEM gère les bibliothèques d&#39;injection dans lesquelles les ressources<br>nécessairesLes ressources doivent uniquement être conservées sur les AEM | Peut-être pas familier avec les développeurs d’applications monopages |
| via Adobe I/O Runtime | Plus familier aux développeurs d’applications monopages | Les ressources de bibliothèque cliente requises par l&#39;application, telles que CSS et JavaScript, devront être rendues disponibles par le développeur AEM via la [`allowProxy` propriétéLes ressources doivent être synchronisées entre l&#39;exécution d&#39;E/S d&#39;AEM et l&#39;](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br><br>exécution d&#39;AdobePour permettre la création d&#39;une application d&#39;une seule page, un serveur proxy pour Adobe I/O Runtime peut être nécessaire. |

## Planification de la SSR {#planning-for-ssr}

En règle générale, seule une partie d’une application doit être rendue côté serveur. L’exemple courant est le contenu qui s’affichera au-dessus du pli lors du chargement initial de la page doit être rendu côté serveur. Cela permet de gagner du temps en fournissant au client du contenu déjà rendu. Lorsque l’utilisateur interagit avec l’application d’une seule page, le contenu supplémentaire est rendu par le client.

Lorsque vous envisagez d’implémenter le rendu côté serveur pour votre application monopage, vous devez vérifier les parties de l’application qui nécessiteront une SSR.

## Développement d’une application d’une seule page à l’aide d’une SSR {#developing-an-spa-using-ssr}

Les composants SPA peuvent être rendus par le client (dans le navigateur) ou côté serveur. Lorsqu’il est rendu côté serveur, les propriétés du navigateur telles que la taille de la fenêtre et l’emplacement ne sont pas présentes. Par conséquent, les composants de l&#39;APS doivent être isomorphiques, sans présumer de l&#39;endroit où ils seront rendus.

Pour utiliser la technologie SSR, vous devez déployer votre code dans AEM et sur Adobe I/O Runtime, qui est responsable du rendu côté serveur. La plupart du code sera identique, mais les tâches spécifiques au serveur seront différentes.

## SSR pour les applications monopages en AEM {#ssr-for-spas-in-aem}

Les applications SSR pour les applications monopages en AEM nécessitent Adobe I/O Runtime, qui est appelé pour le rendu côté serveur de contenu d’application. Dans le fichier HTL de l’application, une ressource sur Adobe I/O Runtime est appelée pour générer le contenu.

Tout comme AEM prend en charge les structures d’application monopages Angular et React prêtes à l’emploi, le rendu côté serveur est également pris en charge pour les applications Angular et React. Pour plus d&#39;informations, consultez la documentation du mécanisme national de prévention pour les deux cadres.

* Réagir : [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular : [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Pour un exemple simpliste, reportez-vous à l&#39;application [Journal](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)We.Retail. Il rend l’intégralité du côté serveur d’applications. Bien qu&#39;il ne s&#39;agisse pas d&#39;un exemple concret, il illustre bien ce qui est nécessaire pour mettre en oeuvre la RSS.

>[!CAUTION]
>L’application [de Journal](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) We.Retail est utilisée à des fins de démonstration uniquement et utilise donc Node.js comme exemple simple au lieu du Adobe I/O Runtime recommandé. Cet exemple ne doit être utilisé pour aucun travail de projet.

>[!NOTE]
>Tout projet AEM doit tirer parti de l’archétype [de projet](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM, qui prend en charge les projets d’application d’une seule page à l’aide de React ou d’Angular et qui utilise le SDK d’application d’une seule page.

## Utilisation de Node.js {#using-node-js}

Adobe I/O Runtime est la solution recommandée pour l’implémentation de la fonction SSR pour les applications monopages en AEM.

Pour les instances d’AEM prédéfinie, il est également possible d’implémenter une SSR à l’aide d’une instance personnalisée de Node.js de la même manière que décrit ci-dessus. Bien que cet aspect soit pris en charge par l’Adobe, il n’est pas recommandé.

Node.js n’est pas pris en charge pour les instances d’AEM hébergées par Adobe.

>[!NOTE]
>
>Si SSR doit être implémenté via Node.js, l’Adobe recommande une instance distincte de Node.js pour chaque environnement AEM (auteur, publication, étape, etc.).

## Rendu de contenu distant {#remote-content-renderer}

La configuration [de](#remote-content-renderer-configuration) Remote Content Renderer qui est requise pour utiliser SSR avec votre application d’une seule page d’accueil (SPA) dans AEM permet de bénéficier d’un service de rendu plus généralisé qui peut être étendu et personnalisé pour répondre à vos besoins.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` est un service OSGi permettant de récupérer le contenu rendu sur un serveur distant, par exemple à partir des E/S d’Adobe. Le contenu envoyé au serveur distant est basé sur le paramètre de requête transmis.

`RemoteContentRenderingService` peut être injecté par inversion de dépendance dans un modèle Sling personnalisé ou une servlet lorsque des manipulations de contenu supplémentaires sont requises.

Ce service est utilisé en interne par la servlet [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

Il `RemoteContentRendererRequestHandlerServlet` peut être utilisé pour définir par programmation la configuration de la requête. `DefaultRemoteContentRendererRequestHandlerImpl`, l’implémentation du gestionnaire de requêtes par défaut fournie vous permet de créer plusieurs configurations OSGi afin de mapper un emplacement dans la structure de contenu à un point de terminaison distant.

Pour ajouter un gestionnaire de requêtes personnalisé, implémentez l’ `RemoteContentRendererRequestHandler` interface. Veillez à définir la propriété `Constants.SERVICE_RANKING` du composant sur un nombre entier supérieur à 100, qui correspond au classement du `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Configuration d’OSGi du gestionnaire par défaut {#configure-default-handler}

La configuration du gestionnaire par défaut doit être configurée comme décrit dans la section Configuration [du rendu de contenu](#remote-content-renderer-configuration)distant.

###  Utilisation du rendu de contenu distant {#usage}

Pour qu’une servlet récupère et renvoie du contenu qui peut être injecté dans la page :

1. Assurez-vous que votre serveur distant est accessible.
1. Ajoutez l’un des fragments de code suivants sur le modèle HTML d’un composant AEM.
1. Vous pouvez éventuellement créer ou modifier les configurations OSGi.
1. Parcourir le contenu de votre site

En général, le modèle HTML d’un composant de page est le principal destinataire d’une telle fonctionnalité.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Conditions requises {#requirements}

Les servlets tirent parti de Sling Model Exporter pour sérialiser les données du composant. Par défaut, les cartes `com.adobe.cq.export.json.ContainerExporter` et `com.adobe.cq.export.json.ComponentExporter` sont prises en charge en tant que cartes de modèle Sling. Si nécessaire, vous pouvez ajouter des classes que la requête doit être adaptée pour utiliser la `RemoteContentRendererServlet` et mettre en oeuvre la `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. Les classes supplémentaires doivent étendre le `ComponentExporter`.
