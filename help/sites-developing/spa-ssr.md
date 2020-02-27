---
title: Rendu SPA et côté serveur
seo-title: Rendu SPA et côté serveur
description: 'null'
seo-description: 'null'
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
translation-type: tm+mt
source-git-commit: 2abf448e0231eb6fcd9295f498a24e81e1ead11a

---


# Rendu SPA et côté serveur{#spa-and-server-side-rendering}

>[!NOTE]
>La fonctionnalité Editeur d’application monopage (SPA) requiert [AEM 6.4 Service Pack 2](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) ou version ultérieure.
>
>L’éditeur d’application d’une seule page est la solution recommandée pour les projets nécessitant un rendu côté client basé sur la structure d’application d’une seule page (par exemple, Réagir ou Angulaire).

>[!NOTE]
>
>AEM 6.4.5.0 ou version ultérieure est requis pour utiliser les fonctionnalités de rendu côté serveur SPA comme décrit dans ce document.

## Présentation {#overview}

Les applications d’une seule page (SPA) peuvent offrir à l’utilisateur une expérience riche et dynamique qui réagit et se comporte de manière familière, souvent tout comme les applications natives. [Pour ce faire, il faut compter sur le client pour charger le contenu à l’avance, puis gérer l’interaction](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) avec l’utilisateur de manière intensive, ce qui permet de réduire le volume de communication nécessaire entre le client et le serveur, ce qui rend l’application plus réactive.

Toutefois, cela peut entraîner des temps de chargement initiaux plus longs, surtout si le SPA est volumineux et riche en contenu. Pour optimiser les temps de chargement, une partie du contenu peut être rendue côté serveur. L’utilisation du rendu côté serveur (SSR) peut accélérer le chargement initial de la page, puis transmettre le rendu au client.

## Quand utiliser SSR {#when-to-use-ssr}

SSR n’est pas requis pour tous les projets. Bien qu’AEM prenne entièrement en charge JS SSR pour l’application d’une seule page, Adobe ne recommande pas de l’implémenter systématiquement pour chaque projet.

Lorsque vous décidez de mettre en oeuvre la SSR, vous devez d&#39;abord estimer la complexité, l&#39;effort et les coûts supplémentaires associés à l&#39;ajout de la SSR de façon réaliste pour le projet, y compris la maintenance à long terme. Une architecture SSR ne doit être choisie que lorsque la valeur ajoutée dépasse clairement les coûts estimés.

Le RSS fournit habituellement une certaine valeur lorsqu’il existe un &quot;oui&quot; clair à l’une des questions suivantes :

* **** SEO : Est-il encore nécessaire que la SSR soit correctement indexée par les moteurs de recherche qui génèrent du trafic ? N’oubliez pas que les principaux moteurs de recherche évaluent désormais JS.
* **** Vitesse de la page : La SSR améliore-t-elle la vitesse de manière mesurable dans les environnements réels et contribue-t-elle à l&#39;expérience globale de l&#39;utilisateur ?

Ce n’est que lorsque l’une au moins de ces deux questions reçoit une réponse &quot;oui&quot; clair pour votre projet qu’Adobe conseille d’implémenter la solution SSR. Les sections suivantes décrivent comment procéder à cette opération à l’aide d’Adobe I/O Runtime.

## Adobe E/S Runtime {#adobe-io-runtime}

Si vous êtes [certain que votre projet nécessite l’implémentation de la SSR](#when-to-use-ssr), la solution recommandée par Adobe consiste à utiliser l’environnement d’exécution d’E/S Adobe.

Pour plus d’informations sur Adobe I/O Runtime, voir

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - pour une présentation du service
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - pour obtenir une documentation détaillée sur la plateforme

Les sections suivantes décrivent comment l’exécution d’E/S Adobe peut être utilisée pour implémenter la technologie SSR pour votre application monopage dans deux modèles différents :

* [Flux de communication piloté par AEM](#aem-driven-communication-flow)
* [Flux de communication piloté par Adobe E/S à l’exécution](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>Adobe recommande une instance d’exécution E/S Adobe distincte pour chaque environnement AEM (auteur, publication, étape, etc.).

## Configuration du rendu de contenu distant {#remote-content-renderer-configuration}

AEM doit savoir où le contenu rendu à distance peut être récupéré. Quel que soit [le modèle que vous choisissiez d’implémenter pour SSR](#adobe-io-runtime), vous devez indiquer à AEM comment accéder à ce service de rendu distant.

Ceci est effectué via le service **RemoteContentRenderer - Configuration Factory** OSGi. Recherchez la chaîne &quot;RemoteContentRenderer&quot; dans la console de configuration de la console Web à `http://<host>:<port>/system/console/configMgr`.

![](assets/rendererconfig.png)

Les champs suivants sont disponibles pour la configuration :

* **Modèle** de chemin de contenu - Expression régulière afin de correspondre à une partie du contenu, le cas échéant
* **URL** du point de fin distant : URL du point de fin responsable de la génération du contenu
   * Utilisez le protocole HTTPS sécurisé si ce n’est pas dans le réseau local.
* **En-têtes** de requête supplémentaires - En-têtes supplémentaires à ajouter à la requête envoyée au point de fin distant
   * Modèle: `key=value`
* **Délai d’expiration** de la demande - Délai d’expiration de la demande d’hôte distant en millisecondes

>[!NOTE]
>
>Que vous choisissiez d’implémenter le flux [de communication piloté par](#aem-driven-communication-flow) AEM ou le flux [d’exécution d’E/S](#adobe-io-driven-communication-flow)Adobe, vous devez définir une configuration de rendu de contenu distant.
>
>Cette configuration doit également être définie si vous choisissez d’ [utiliser un serveur](#using-node-js)Node.js personnalisé.

>[!NOTE]
>
>Cette configuration tire parti de la fonctionnalité de rendu [de contenu](#remote-content-renderer)distant, qui propose des options d’extension et de personnalisation supplémentaires.

## Flux de communication piloté par AEM {#aem-driven-communication-flow}

Lors de l’utilisation de la technologie SSR, le processus [d’interaction des](/help/sites-developing/spa-overview.md#workflow) composants des applications monopages dans AEM inclut une phase au cours de laquelle le contenu initial de l’application est généré par l’exécution des E/S Adobe.

1. Le navigateur demande le contenu SSR à AEM.
1. AEM publie le modèle sur le moteur d’exécution des E/S Adobe.
1. L’exécution des E/S Adobe renvoie le contenu généré
1. AEM diffuse le code HTML renvoyé par Adobe I/O Runtime via le modèle HTL du composant de page d’arrière-plan.

![server-side-render-cms-drivenaemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Flux de communication Adobe E/S piloté par l’exécution {#adobe-io-driven-communication-flow}

La section Flux [de communication piloté par](#aem-driven-communication-flow) AEM décrit l’implémentation standard et recommandée du rendu côté serveur en ce qui concerne les applications monopages dans AEM, où AEM effectue le démarrage et la diffusion du contenu.

Une autre solution consiste à mettre en oeuvre la solution SSR de sorte qu’Adobe E/S Runtime soit responsable de l’amorçage, inversant ainsi le flux de communication.

Les deux modèles sont valides et pris en charge par AEM. Toutefois, il faut tenir compte des avantages et des inconvénients de chacun avant de mettre en oeuvre un modèle particulier.

| Démarrage | Avantages | Inconvénients |
|---|---|---|
| via AEM | AEM gère les bibliothèques d’injection où les ressources<br>nécessaires doivent uniquement être conservées sur AEM | Peut-être pas familier avec le développeur SPA |
| via Adobe I-O Runtime | Plus familier aux développeurs SPA | Les ressources Clientlib requises par l’application, telles que CSS et JavaScript, devront être rendues disponibles par le développeur AEM via la [`allowProxy` propriété](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br>Les ressources doivent être synchronisées entre AEM et l’<br>exécution des E/S Adobe. Pour activer la création de l’application monopage, un serveur proxy pour l’exécution des E/S Adobe peut être nécessaire. |

## Planification d&#39;une SSR {#planning-for-ssr}

En règle générale, seule une partie d’une application doit être rendue côté serveur. L’exemple courant est le contenu qui s’affichera au-dessus du pli lors du chargement initial de la page doit être rendu côté serveur. Cela permet de gagner du temps en diffusant le contenu déjà rendu au client. Lorsque l’utilisateur interagit avec l’application d’une seule page, le contenu supplémentaire est généré par le client.

Lorsque vous envisagez d’implémenter le rendu côté serveur pour votre application d’une seule page, vous devez examiner les parties de l’application qui nécessiteront une SSR.

## Développement d’une application monopage à l’aide de la technologie SSR {#developing-an-spa-using-ssr}

Les composants SPA peuvent être rendus par le client (dans le navigateur) ou côté serveur. Lorsqu’il est rendu côté serveur, les propriétés du navigateur, telles que la taille de la fenêtre et l’emplacement, ne sont pas présentes. Par conséquent, les composants de l&#39;APS doivent être isomorphiques, sans présumer de l&#39;endroit où ils seront rendus.

Pour utiliser la technologie SSR, vous devez déployer votre code dans AEM ainsi que sur l’environnement d’exécution d’E/S Adobe, qui est responsable du rendu côté serveur. La plupart du code sera identique, mais les tâches spécifiques au serveur seront différentes.

## SSR pour les applications monopages dans AEM {#ssr-for-spas-in-aem}

La SSR pour les applications monopages dans AEM nécessite l’exécution des E/S Adobe, qui est appelée pour le rendu côté serveur de contenu de l’application. Dans le fichier HTML de l’application, une ressource sur l’exécution des E/S Adobe est appelée pour générer le contenu.

Tout comme AEM prend en charge les structures d’application d’une seule page, le rendu côté serveur est également pris en charge pour les applications Angular et React. Pour plus de détails, consultez la documentation du mécanisme national de prévention pour les deux cadres.

* Réagir : [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular : [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Pour un exemple simpliste, reportez-vous à l’application [](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)We.Retail Journal. Il rend l’intégralité du côté serveur d’applications. Bien qu&#39;il ne s&#39;agisse pas d&#39;un exemple concret, il illustre bien ce qui est nécessaire pour mettre en oeuvre la réforme du secteur de la sécurité.

>[!CAUTION]
>L’application [Journal](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) We.Retail est utilisée à des fins de démonstration uniquement et utilise donc Node.js comme exemple simple au lieu de l’exécution d’E/S Adobe recommandée. Cet exemple ne doit être utilisé pour aucun travail de projet.

>[!NOTE]
>Tous les projets d’application d’une seule page doivent être basés sur l’archétype [Maven pour le kit](https://github.com/adobe/aem-spa-project-archetype)de démarrage SPA.

## Utilisation de Node.js {#using-node-js}

Adobe I/O Runtime est la solution recommandée pour l’implémentation de la fonction SSR pour les applications monopages dans AEM.

Pour les instances d’AEM en préfixe, il est également possible de mettre en oeuvre la SSR à l’aide d’une instance de Node.js personnalisée de la même manière que décrit ci-dessus. Bien que cette fonctionnalité soit prise en charge par Adobe, elle n’est pas recommandée.

Node.js n’est pas pris en charge pour les instances AEM hébergées par Adobe.

>[!NOTE]
>
>Si SSR doit être implémenté via Node.js, Adobe recommande une instance Node.js distincte pour chaque environnement AEM (auteur, publication, étape, etc.).

## Rendu de contenu distant {#remote-content-renderer}

La configuration [du rendu de contenu](#remote-content-renderer-configuration) distant requise pour utiliser SSR avec votre application d’une seule page dans AEM permet de bénéficier d’un service de rendu plus généralisé qui peut être étendu et personnalisé en fonction de vos besoins.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` est un service OSGi permettant de récupérer le contenu généré sur un serveur distant, tel que des E/S Adobe. Le contenu envoyé au serveur distant est basé sur le paramètre de requête transmis.

`RemoteContentRenderingService` peuvent être injectées par inversion de dépendance dans un modèle Sling personnalisé ou une servlet lorsque des manipulations de contenu supplémentaires sont requises.

Ce service est utilisé en interne par la [servletRemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

Il `RemoteContentRendererRequestHandlerServlet` peut être utilisé pour définir par programmation la configuration de la requête. `DefaultRemoteContentRendererRequestHandlerImpl`, l’implémentation du gestionnaire de requêtes par défaut fournie, vous permet de créer plusieurs configurations OSGi afin de mapper un emplacement dans la structure de contenu à un point de terminaison distant.

Pour ajouter un gestionnaire de requêtes personnalisé, implémentez l’ `RemoteContentRendererRequestHandler` interface. Veillez à définir la propriété `Constants.SERVICE_RANKING` du composant sur un nombre entier supérieur à 100, qui correspond au rang du `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Configuration OSGi du gestionnaire par défaut {#configure-default-handler}

La configuration du gestionnaire par défaut doit être configurée comme décrit dans la section Configuration [du rendu de contenu](#remote-content-renderer-configuration)distant.

###  Utilisation du rendu de contenu distant {#usage}

Pour qu’une servlet récupère et renvoie du contenu pouvant être injecté dans la page :

1. Assurez-vous que votre serveur distant est accessible.
1. Ajoutez l’un des fragments de code suivants au modèle HTML d’un composant AEM.
1. Vous pouvez éventuellement créer ou modifier les configurations OSGi.
1. Parcourir le contenu de votre site

En règle générale, le modèle HTML d’un composant de page est le principal destinataire d’une telle fonctionnalité.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Conditions requises {#requirements}

Les servlets tirent parti de Sling Model Exporter pour sérialiser les données du composant. Par défaut, les cartes `com.adobe.cq.export.json.ContainerExporter` et `com.adobe.cq.export.json.ComponentExporter` sont prises en charge en tant que cartes de modèle Sling. Si nécessaire, vous pouvez ajouter des classes que la requête doit être adaptée à l’utilisation `RemoteContentRendererServlet` et à l’implémentation de la `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. Les classes supplémentaires doivent étendre la `ComponentExporter`.
