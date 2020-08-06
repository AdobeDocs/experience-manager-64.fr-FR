---
title: Développement d’applications monopages pour AEM
seo-title: Développement d’applications monopages pour AEM
description: Cet article présente des questions importantes à prendre en compte lorsqu'un développeur frontal développe un SPA pour AEM et donne un aperçu de l'architecture des AEM par rapport aux SPA à garder à l'esprit lors du déploiement d'un SPA développé sur les .
seo-description: Cet article présente des questions importantes à prendre en compte lorsqu'un développeur frontal développe un SPA pour AEM et donne un aperçu de l'architecture des AEM par rapport aux SPA à garder à l'esprit lors du déploiement d'un SPA développé sur les .
uuid: c77b37be-6acc-4cb4-9ae3-ba09583e6fff
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 3f4c17cf-6f77-4a87-b27b-f13a6a976523
translation-type: tm+mt
source-git-commit: 0e7f4a78f63808bea2aa7a5abbb31e7e5b9d21b3
workflow-type: tm+mt
source-wordcount: '2199'
ht-degree: 3%

---


# Développement d’applications monopages pour AEM{#developing-spas-for-aem}

Les applications d’une seule page (SPA) peuvent améliorer considérablement l’expérience des utilisateurs de sites web. Le souhait des développeurs est de pouvoir créer des sites avec des structures SPA. Les auteurs, pour leur part, souhaitent modifier facilement du contenu dans AEM pour un site conçu à l’aide de telles structures.

Cet article présente des questions importantes à prendre en compte lorsqu’un développeur frontal est invité à développer une application d’une seule page pour l’AEM et donne un aperçu de l’architecture de l’AEM en ce qui concerne le déploiement d’applications d’une seule page sur l’AEM.

>[!NOTE]
>
>La fonctionnalité Editeur d’application monopage (SPA) nécessite AEM Service Pack 2 6.4 ou version ultérieure.
>
>L’éditeur d’applications monopages est la solution recommandée pour les projets qui nécessitent un rendu côté client basé sur la structure d’applications monopages (par exemple, Réagir ou Angular).

## Archétype de projet AEM {#aem-project-archetype}

Tout projet AEM doit tirer parti de l’archétype [de projet](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM, qui prend en charge les projets d’application d’une seule page à l’aide de React ou d’Angular et qui utilise le SDK d’application d’une seule page.

## Principes de développement des ZPS pour les AEM {#spa-development-principles-for-aem}

Le développement d’applications d’une seule page sur AEM suppose que le développeur principal respecte les meilleures pratiques standard lors de la création d’une application d’une seule page. Si en tant que développeur frontal vous suivez ces bonnes pratiques générales ainsi que quelques principes AEM spécifiques, votre application d’une seule page sera fonctionnelle avec [AEM et ses capacités](/help/sites-developing/spa-walkthrough.md#content-editing-experience-with-spa)de création de contenu.

* **[Portabilité](/help/sites-developing/spa-architecture.md#portability)-**Comme pour tout composant, les composants doivent être construits pour être aussi portables que possible. L’application d’une seule page doit être créée avec des composants portatifs et réutilisables, ce qui évite les chemins statiques faisant référence à la structure de contenu.
* **[AEM pilote la structure](/help/sites-developing/spa-architecture.md#aem-drives-site-structure)**du site : le développeur principal crée des composants et possède leur structure interne, mais compte sur AEM pour définir la structure du contenu du site.
* **[Rendu](/help/sites-developing/spa-architecture.md#dynamic-rendering)**dynamique : tous les rendus doivent être dynamiques.
* **[Routage](#dynamic-routing)dynamique -**L’application d’une seule page est responsable du routage et AEM l’écoute et récupère les données du composant en fonction de celui-ci. Tout routage devrait également être dynamique.

Si vous gardez ces principes à l’esprit lorsque vous développez votre application d’une seule page, elle sera aussi flexible et aussi future que possible, tout en activant toutes les fonctionnalités de création d’AEM prises en charge.

Si vous n’avez pas besoin de prendre en charge AEM fonctions de création, vous devrez peut-être envisager un modèle [de conception](/help/sites-developing/spa-architecture.md#spa-design-models)d’application d’une seule page.

### Portabilité {#portability}

Comme lors du développement de n&#39;importe quel composant, vos composants doivent être conçus de manière à optimiser leur portabilité. Tout modèle qui va à l&#39;encontre de la portabilité ou de la réutilisation des composants doit être évité pour assurer la compatibilité, la flexibilité et la maintenabilité à l&#39;avenir.

Le développeur doit éviter d’utiliser des chemins statiques faisant référence à la structure de contenu, car les chemins peuvent être modifiés à tout moment par les auteurs de contenu. Cela limite également la réutilisation de la bibliothèque et empêche l’AEM Éditeur de modèles d’être utilisé car sa structure se trouve à un autre emplacement que le contenu.

L&#39;application d&#39;une seule page doit être construite avec des composants hautement portables et réutilisables.

### AEM lecteurs Structure du site {#aem-drives-site-structure}

Le développeur principal doit se considérer comme responsable de la création d’une bibliothèque de composants SPA utilisés pour créer l’application. Le développeur frontal a un contrôle total de la structure interne des composants. [Cependant, AEM possède toujours la structure du site.](/help/sites-developing/spa-overview.md)

Cela signifie que le développeur principal peut ajouter du contenu client avant ou après le point d’entrée des composants et peut également effectuer des appels tiers à l’intérieur du composant. Cependant, le développeur frontal ne contrôle pas entièrement la manière dont les composants sont imbriqués, par exemple.

### Rendu dynamique {#dynamic-rendering}

L’application d’une seule page doit reposer sur le rendu dynamique du contenu. Il s’agit de l’attente par défaut où AEM récupère et rend tous les enfants de la structure de contenu.

Tout rendu explicite pointant vers un contenu spécifique est considéré comme un rendu statique et bien que pris en charge ne sera pas compatible avec AEM fonctionnalités de création de contenu. Cela va aussi à l&#39;encontre du principe de [portabilité](/help/sites-developing/spa-architecture.md#portability).

### Routage dynamique {#dynamic-routing}

Comme pour le rendu, tous les routages doivent également être dynamiques. En AEM, [l’application d’une seule page doit toujours être propriétaire du routage](/help/sites-developing/spa-routing.md) et AEM l’écoute et récupère le contenu en fonction de celui-ci.

Tout routage statique va à l&#39;encontre du [principe de portabilité](/help/sites-developing/spa-architecture.md#portability) et limite l&#39;auteur en n&#39;étant pas compatible avec les fonctionnalités de création de contenu de l&#39;AEM. Par exemple, avec un routage statique, si l’auteur du contenu souhaite modifier un itinéraire ou une page, il doit demander au développeur principal de le faire.

## Modèles de conception SPA {#spa-design-models}

Si les [principes de développement des applications monopages en AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem) sont respectés, votre application d’une seule page sera fonctionnelle avec toutes les fonctionnalités de création de contenu AEM prises en charge.

Il peut toutefois y avoir des cas où cela n&#39;est pas tout à fait nécessaire. Le tableau suivant présente un aperçu des différents modèles de conception, leurs avantages et leurs inconvénients.

<table> 
 <tbody>
  <tr>
   <th><strong>Modèle de conception<br /> </strong></th> 
   <th><strong>Avantages</strong></th> 
   <th><strong>Inconvénients</strong></th> 
  </tr>
  <tr>
   <td>AEM est utilisé en tant que CMS sans en-tête sans utiliser la structure <a href="/help/sites-developing/spa-reference-materials.md">SPA Editor SDK.</a></td> 
   <td>Le développeur frontal a un contrôle total sur l’application.</td> 
   <td><p>Les auteurs de contenu ne peuvent pas exploiter AEM expérience de création de contenu.</p> <p>Le code n'est ni portable ni réutilisable s'il contient des références statiques ou un routage.</p> <p>N’autorise pas l’utilisation de l’éditeur de modèles ; le développeur principal doit donc gérer les modèles modifiables via le JCR.</p> </td> 
  </tr>
  <tr>
   <td>Le développeur principal utilise la structure du SDK de l’éditeur d’applications monopages, mais n’ouvre que certaines zones à l’auteur du contenu.</td> 
   <td>Le développeur garde le contrôle de l’application en activant uniquement la création dans des zones restreintes de l’application.</td> 
   <td><p>Les auteurs de contenu sont limités à un ensemble limité d’AEM expérience de création de contenu.</p> <p>Le code risque de ne pas être portable ni réutilisable s'il contient des références statiques ou un routage.</p> <p>N’autorise pas l’utilisation de l’éditeur de modèles ; le développeur principal doit donc gérer les modèles modifiables via le JCR.</p> </td> 
  </tr>
  <tr>
   <td>Le projet tire pleinement parti du SDK de l’éditeur d’applications monopages et les composants frontaux sont développés en tant que bibliothèque et la structure de contenu de l’application est déléguée à AEM.</td> 
   <td><p>L'application est réutilisable et portable.</p> <p>L’auteur du contenu peut modifier l’application à l’aide de AEM expérience de création de contenu.<br /> </p> <p>L’application d’une seule page est compatible avec l’éditeur de modèles.</p> </td> 
   <td><p>Le développeur ne contrôle pas la structure de l’application et la partie du contenu déléguée à AEM.</p> <p>Le développeur peut toujours réserver des zones de l’application pour le contenu qui ne doit pas être créé à l’aide d’AEM.</p> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Bien que tous les modèles soient pris en charge en AEM, ce n&#39;est qu&#39;en mettant en oeuvre le troisième (et en respectant ainsi les principes de développement [des ZPS recommandés dans AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)) que les auteurs de contenu pourront interagir et modifier le contenu de l&#39;ZPS dans l&#39;, comme ils s&#39;y habituent.

## Migration des applications monopages existantes vers AEM {#migrating-existing-spas-to-aem}

En règle générale, si votre application d’une seule page respecte les Principes de développement de l’ [application d’une seule page pour AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem), elle fonctionne en AEM et peut être modifiée à l’aide de l’éditeur d’une seule page d’une seule page.

Suivez ces étapes pour préparer votre application d’une seule page à travailler avec AEM.

1. **Rendez vos composants JS modulaires.**

   Rendez-les capables d’être rendus dans n’importe quel ordre, position et taille.

1. **Utilisez les conteneurs fournis par notre SDK pour placer vos composants à l’écran.**

   AEM fournit un composant système de page et de paragraphe que vous pouvez utiliser.

1. **Créez un composant AEM pour chaque composant JS.**

   Les composants AEM définissent la boîte de dialogue et la sortie JSON.

## Instructions destinées aux développeurs de premier plan {#instructions-for-front-end-developers}

La tâche principale de la mise en oeuvre d’un développeur frontal pour créer une application d’une seule page d’accueil pour AEM est de convenir des composants et de leurs modèles JSON.

Vous trouverez ci-dessous un aperçu des étapes que doit suivre un développeur frontal lors du développement d’une application d’une seule page pour AEM.

1. **Accepter les composants et leur modèle JSON**

   Les développeurs frontaux et les développeurs d&#39;AEM dorsaux doivent s&#39;entendre sur les composants nécessaires et sur un modèle pour qu&#39;il y ait une correspondance individuelle entre les composants d&#39;une application d&#39;une seule page et les composants d&#39;arrière-plan.

   AEM composants sont toujours nécessaires principalement pour fournir des boîtes de dialogue de modification et pour exporter le modèle de composant.

1. **Dans les composants Réagir, accédez au modèle via`this.props.cqModel`**

   Une fois les composants acceptés et le modèle JSON en place, le développeur frontal est libre de développer l&#39;application d&#39;une seule page et peut simplement accéder au modèle JSON via `this.props.cqModel`.

1. **Mise en oeuvre de la`render()`méthode du composant**

   Le développeur frontal met en oeuvre la `render()` méthode à sa convenance et peut utiliser les champs de la `cqModel` propriété. Cette opération génère le DOM et les fragments HTML qui seront insérés dans la page. Il s’agit de la méthode standard de création d’une application dans React.

1. **Faites correspondre le composant au type de ressource AEM via`MapTo()`**

   Le mappage stocke les classes de composants et est utilisé en interne par le `Container` composant fourni pour récupérer et instancier dynamiquement les composants en fonction du type de ressource donné.

   Il sert de &quot;colle&quot; entre l&#39;avant et l&#39;arrière-plan afin que l&#39;éditeur sache quels composants correspondent les composants réactifs.

   Les `Page` et `ResponsiveGrid` sont de bons exemples de classes qui étendent la base `Container`.

1. **Définissez le composant comme`EditConfig`paramètre pour`MapTo()`**

   Ce paramètre est nécessaire pour indiquer à l’éditeur comment le composant doit être nommé aussi longtemps qu’il n’est pas encore rendu ou n’a aucun contenu à rendre.

1. **Étendre la`Container`classe fournie pour les pages et les conteneurs**

   Les systèmes de pages et de paragraphes doivent étendre cette classe afin que la délégation aux composants internes fonctionne comme prévu.

1. **Implémentez une solution de routage qui utilise l’`History`API HTML5.**

   Lorsque la fonction `ModelRouter` est activée, l’appel des `pushState` fonctions et `replaceState` déclenche une demande à la `PageModelManager` fonction pour récupérer un fragment manquant du modèle.

   La version actuelle du modèle `ModelRouter` ne prend en charge que l&#39;utilisation d&#39;URL pointant vers le chemin de ressource réel des points d&#39;entrée du modèle Sling. Il ne prend pas en charge l’utilisation d’URL ou de alias mineurs.

   Il `ModelRouter` peut être désactivé ou configuré pour ignorer une liste d&#39;expressions régulières.

## AEM-Agnostique {#aem-agnostic}

Ces blocs de code illustrent comment vos composants Réagir et Angular n&#39;ont besoin de rien qui soit spécifique à l&#39;Adobe ou à l&#39;AEM.

* Tout ce qui se trouve à l’intérieur du composant JavaScript est indifférent aux AEM.
* Ce qui est toutefois spécifique à AEM est que le composant JS doit être mappé à un composant AEM avec l&#39;aide MapTo.

![screen_shot_2018-12-11at144019](assets/screen_shot_2018-12-11at144019.png)

L&#39; `MapTo` aide est la &quot;colle&quot; qui permet de faire correspondre les composants back-end et front-end :

* Il indique au conteneur JS (ou système de paragraphes JS) quel composant JS est responsable du rendu de chacun des composants présents dans le fichier JSON.
* Il ajoute un attribut de données HTML au code HTML généré par le composant JS, de sorte que l’éditeur d’applications monopages sache quelle boîte de dialogue afficher à l’auteur lors de la modification du composant.

Pour plus d’informations sur l’utilisation `MapTo` et la création d’applications monopages pour AEM en général, consultez le guide de prise en main de votre structure choisie.

* [Prise en main des applications monopages dans AEM - Réagir](/help/sites-developing/spa-getting-started-react.md)
* [Prise en main des applications monopages en AEM - Angular](/help/sites-developing/spa-getting-started-angular.md)

## Architecture AEM et applications monopages {#aem-architecture-and-spas}

L’architecture générale des AEM, y compris les environnements de développement, de création et de publication, ne change pas lors de l’utilisation d’applications monopages. Cependant, il est utile de comprendre comment le développement des applications SPA s&#39;intègre dans cette architecture.

![screen_shot_2018-12-11at145348](assets/screen_shot_2018-12-11at145348.png)

* **Créer un Environnement**

   C’est ici que la source de l’application SPA et la source du composant sont extraites.

   * Le générateur NPM clientlib crée une bibliothèque cliente à partir du projet SPA.
   * Cette bibliothèque sera prise par Maven et déployée par le module externe Maven Build avec le composant dans AEM Author.

* **Auteur AEM**

   Le contenu est créé sur l’AEM auteur, y compris la création d’applications monopages.

   Lorsqu’une application d’une seule page est modifiée à l’aide de l’éditeur d’applications d’une seule page sur l’environnement de création :

   1. L’application d’une seule page demande le code HTML externe.
   1. Le fichier CSS est chargé.
   1. Le script JavaScript de l’application SPA est chargé.
   1. Lorsque l’application d’une seule page est exécutée, le fichier JSON est demandé, ce qui permet à l’application de créer le DOM de la page, y compris les `cq-data` attributs.
   1. Ces `cq-data` attributs permettent à l’éditeur de charger des informations de page supplémentaires afin de connaître les configurations de modification disponibles pour les composants.

* **Publication AEM**

   C’est ici que le contenu créé et les bibliothèques compilées, y compris les artefacts d’application SPA, les clientlibs et les composants, sont publiés pour la consommation publique.

* **Répartiteur / CDN**

   Le répartiteur sert de couche de mise en cache des AEM pour les visiteurs sur le site.

   * Les requêtes sont traitées de la même manière que sur l’auteur AEM. Toutefois, aucune requête d’informations de page n’est envoyée, car cette requête n’est requise que par l’éditeur.
   * Javascript, CSS, JSON et HTML sont mis en cache, ce qui optimise la page pour une diffusion rapide.

>[!NOTE]
>
>Dans AEM il n&#39;est pas nécessaire d&#39;exécuter les mécanismes de création Javascript ni d&#39;exécuter le JavaScript lui-même. AEM héberge uniquement les artefacts compilés de l’application SPA.

## Étapes suivantes {#next-steps}

Pour une vue d’ensemble de la structure d’une seule application d’une seule page d’accueil en AEM et de son fonctionnement, consultez le guide de prise en main pour [réagir](/help/sites-developing/spa-getting-started-react.md) et [Angular](/help/sites-developing/spa-getting-started-angular.md).

Pour obtenir un guide détaillé sur la création de votre propre application d’une seule page d’accueil, consultez le didacticiel [](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html)Prise en main de l’éditeur d’applications d’une seule page d’AEM - Événements WKND.

Pour plus d’informations sur le mappage du modèle dynamique aux composants et son fonctionnement dans les applications monopages dans AEM, voir l’article Mappage du modèle [dynamique aux composants pour les applications monopages](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Si vous souhaitez mettre en oeuvre des applications monopages dans AEM pour une structure autre que React ou Angular ou si vous souhaitez simplement plonger dans le fonctionnement du SDK SPA pour AEM, reportez-vous à l’article [SPA Blueprint](/help/sites-developing/spa-blueprint.md) .
