---
title: Ajout de ContextHub à des pages et accès à des magasins
seo-title: Adding ContextHub to Pages and Accessing Stores
description: Ajoutez ContextHub à vos pages pour activer les fonctionnalités ContextHub et créer un lien vers les bibliothèques JavaScript ContextHub
seo-description: Add ContextHub to your pages to enable the ContextHub features and to link to the ContextHub Javascript libraries
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
exl-id: 99efe308-bf8a-41ad-8203-b57fce20820c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 97%

---

# Ajout de ContextHub à des pages et accès à des magasins {#adding-contexthub-to-pages-and-accessing-stores}

Ajoutez ContextHub à vos pages pour activer les fonctionnalités ContextHub et créer un lien vers les bibliothèques JavaScript ContextHub

L’API JavaScript ContextHub permet d’accéder aux données contextuelles gérées par ContextHub. Cette page décrit brièvement les principales fonctionnalités de l’API pour accéder à des données contextuelles et les manipuler. Suivez les liens vers la documentation de référence de l’API pour consulter des informations détaillées et des exemples de code.

## Ajout de ContextHub à un composant de page {#adding-contexthub-to-a-page-component}

Pour activer les fonctionnalités ContextHub et créer un lien vers les bibliothèques JavaScript ContextHub, insérez le composant contexthub dans la section `head` de votre page. Le code JSP de votre composant de page ressemble à ceci :

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

Notez que vous devez également déterminer si la barre d’outils ContextHub apparaît ou non dans le mode Aperçu. Voir [Affichage et masquage de l’IU ContextHub](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui).

## À propos des magasins ContextHub {#about-contexthub-stores}

Utilisez des magasins ContextHub pour conserver des données contextuelles. ContextHub fournit les types de magasins suivants, qui constituent la base de tous les types :

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

Tous les types de magasins sont des extensions de la classe [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core). Pour plus d’informations sur la création d’un type de magasin, voir [Création de magasins personnalisés](/help/sites-developing/ch-extend.md#creating-custom-store-candidates). Pour plus d’informations sur les exemples de types de magasins, voir [Exemples de candidats au titre de magasins ContextHub](/help/sites-developing/ch-samplestores.md).

### Modes de persistance {#persistence-modes}

Les magasins ContextHub utilisent l’un des modes de persistance suivants :

* **Local** : utilise HTML5 localStorage pour conserver les données. L’espace de stockage local est conservé sur le navigateur entre les sessions.
* **Session** : utilise HTML5 sessionStorage pour conserver les données. Le stockage de session est conservé pendant toute la durée de la session du navigateur et est disponible dans toutes les fenêtres du navigateur.
* **Cookie** : utilise la prise en charge native des cookies du navigateur pour le stockage des données. Les données de cookie sont échangées avec le serveur dans des requêtes HTTP.
* **Window.name** : utilise la propriété window.name pour conserver les données.
* **Memory** : utilise un objet JavaScript pour conserver les données.

Par défaut, ContextHub utilise le mode de persistance Local. Si le navigateur ne prend pas en charge ni n’autorise HTML5 localStorage, la persistance de session est utilisée. Si le navigateur ne prend pas en charge ni n’autorise HTML5 sessionStorage, la persistance Window.name est utilisée.

### Données du magasin {#store-data}

En interne, les données de magasin forment une structure arborescente, ce qui permet d’ajouter des valeurs en tant qu’objets complexes ou que types principaux. Lorsque vous ajoutez des objets complexes à des magasins, leurs propriétés forment des branches dans l’arborescence de données. Par exemple, l’objet complexe suivant est ajouté à un magasin vide nommé location :

```xml
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

La structure arborescente du magasin peut être conceptualisée comme suit :

```xml
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

La structure arborescente définit les éléments de données du magasin sous la forme de paires clé/valeur. Dans l’exemple ci-dessus, la clé `/number` correspond à la valeur `321` et la clé `/data/country` à la valeur `Switzerland`.

### Manipulation d’objets {#manipulating-objects}

ContextHub fournit la classe [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) pour manipuler des objets JavaScript. Utilisez les fonctions de cette classe pour manipuler des objets JavaScript avant de les ajouter à un magasin ou après les avoir récupérés d’un magasin.

En outre, la classe [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) fournit des fonctions pour sérialiser des objets en chaînes et désérialiser des chaînes en objets. Utilisez cette classe pour gérer les données JSON afin de prendre en charge les navigateurs qui n’intègrent pas, en natif, les fonctions `JSON.parse` et `JSON.stringify`.

## Interaction avec les magasins ContextHub {#interacting-with-contexthub-stores}

Utilisez l’objet JavaScript [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) pour obtenir un magasin comme objet JavaScript. Une fois que vous avez obtenu l’objet de magasin, vous pouvez manipuler les données qu’il contient. Utilisez la fonction [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) ou [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) pour obtenir le magasin.

### Accès aux données du magasin {#accessing-store-data}

La classe JavaScript [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) définit plusieurs fonctions permettant d’interagir avec les données du magasin. Les fonctions suivantes stockent et récupèrent plusieurs éléments de données contenus dans des objets :

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

Les différents éléments de données sont stockés sous la forme d’un ensemble de paires clé/valeur. Pour stocker et récupérer des valeurs, spécifiez la clé correspondante :

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

Notez que les magasins candidats personnalisés peuvent définir des fonctions supplémentaires qui permettent d’accéder aux données du magasin.

>[!NOTE]
>
>Par défaut, ContextHub ne connaît pas les utilisateurs actuellement connectés sur les serveurs de publication. Il considère ces utilisateurs comme étant anonymes.
>
>Vous pouvez faire en sorte que ContextHub connaisse les utilisateurs connectés en chargeant le magasin « profile » tel qu’il est implémenté sur le [site de référence We.Retail](/help/sites-developing/we-retail.md). Consultez le [code approprié sur GitHub ici](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### Génération d’événements ContextHub {#contexthub-eventing}

ContextHub comprend un framework d’événements qui vous permet de répondre automatiquement aux événements du magasin. Chaque objet du magasin contient un objet [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) disponible sous la forme d’une propriété [`eventing`](/help/sites-developing/contexthub-api.md#eventing) du magasin. Utilisez la fonction [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) ou [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) pour lier une fonction JavaScript à un événement de magasin.

## Utilisation de ContextHub pour manipuler des cookies {#using-context-hub-to-manipulate-cookies}

L’API JavaScript ContextHub offre une prise en charge de plusieurs navigateurs pour la gestion des cookies de navigateur. L’espace de noms [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) définit plusieurs fonctions permettant de créer, de manipuler et de supprimer des cookies.

## Identification de segments ContextHub résolus {#determining-resolved-contexthub-segments}

Le moteur de segments ContextHub vous permet de déterminer quels segments enregistrés sont résolus dans le contexte actuel. Utilisez la fonction getResolvedSegments de la classe [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) pour récupérer les segments résolus. Utilisez ensuite la fonction `getName` ou `getPath` de la classe [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) pour tester un segment.

### Segments installés {#installed-segments}

Les segments ContextHub sont installés sous le nœud `/conf/we-retail/settings/wcm/segments`.

* female
* female-over-30
* female-under-30
* male
* male-over-30
* male-under-30
* order-value-75-to-100
* order-value-over-100
* over-30
* summer
* summer-female
* summer-female-over-30
* summer-female-under-30
* summer-male
* summer-male-over-30
* summer-male-under-30
* under-30
* winter
* winter-female
* winter-female-over-30
* winter-female-under-30
* winter-male
* winter-male-over-30
* winter-male-under-20

Les règles utilisées pour résoudre ces segments sont résumées comme suit :

* Le genre « Homme » ou « Femme » est déterminé à partir de l’élément de données `gender` du magasin [profile](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate).

* L’âge est déterminé à partir de l’élément de données « age » du magasin « profile ».
* La saison est déterminée à partir de l’élément de données de latitude de la variable [géolocalisation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) et l’élément de données month du magasin surferinfo.

>[!WARNING]
>
>Les segments installés sont fournis en tant que configurations de référence afin de vous aider à créer votre propre configuration dédiée pour votre projet et, en tant que tels, ne doivent pas être utilisés directement.

## Journalisation des messages de débogage pour ContextHub {#logging-debug-messages-for-contexthub}

Configurez le service OSGi ContextHub d’Adobe Granite (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) pour consigner des messages de débogage détaillés qui s’avèrent utiles dans le cadre du développement.

Pour configurer le service, vous pouvez utiliser la [Console web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ou un [nœud JCR du référentiel](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) :

* Console web : pour consigner des messages de débogage, sélectionnez la propriété Debug.
* Nœud JCR : pour consigner des messages de débogage, définissez la propriété booléenne `com.adobe.granite.contexthub.debug` sur `true`.

## Affichage d’un aperçu de la structure ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub fournit une [page de diagnostics](/help/sites-developing/ch-diagnostics.md) qui affiche un aperçu de son framework.
