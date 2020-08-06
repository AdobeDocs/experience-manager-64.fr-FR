---
title: Ajout de ContextHub à des pages et accès à des magasins
seo-title: Ajout de ContextHub à des pages et accès à des magasins
description: Ajoutez ContextHub à vos pages pour activer les fonctionnalités ContextHub et créer un lien vers les bibliothèques JavaScript ContextHub.
seo-description: Ajoutez ContextHub à vos pages pour activer les fonctionnalités ContextHub et créer un lien vers les bibliothèques JavaScript ContextHub.
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 78%

---


# Ajout de ContextHub à des pages et accès à des magasins {#adding-contexthub-to-pages-and-accessing-stores}

Ajoutez ContextHub à vos pages pour activer les fonctionnalités ContextHub et créer un lien vers les bibliothèques JavaScript ContextHub.

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
* **Session :** Utilise le stockage de session HTML5 pour conserver les données. Le stockage de session est conservé pendant toute la durée de la session du navigateur et est disponible dans toutes les fenêtres du navigateur.
* **Cookie** : utilise la prise en charge native des cookies du navigateur pour le stockage des données. Les données de cookie sont échangées avec le serveur dans des requêtes HTTP.
* **Window.name** : utilise la propriété window.name pour conserver les données.
* **Mémoire** : utilise un objet JavaScript pour conserver les données.

Par défaut, ContextHub utilise le mode de persistance Local. Si le navigateur ne prend pas en charge ni n’autorise HTML5 localStorage, la persistance de session est utilisée. Si le navigateur ne prend pas en charge ni n’autorise HTML5 sessionStorage, la persistance Window.name est utilisée.

### Données du magasin {#store-data}

En interne, les données de magasin forment une structure arborescente, ce qui permet d’ajouter des valeurs en tant qu’objets complexes ou que types principaux. Lorsque vous ajoutez des objets complexes à des magasins, leurs propriétés forment des branches dans l’arborescence de données. Par exemple, l’objet complexe suivant est ajouté à une boutique vide nommée emplacement :

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

La structure arborescente définit les éléments de données du magasin sous la forme de paires clé/valeur. In the above example, the key `/number` corresponds with the value `321`, and the key `/data/country` corresponds with the value `Switzerland`.

### Manipulation d’objets {#manipulating-objects}

ContextHub provides the [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) class for manipulating Javascript objects. Utilisez les fonctions de cette classe pour manipuler des objets JavaScript avant de les ajouter à un magasin ou après les avoir récupérés d’un magasin.

Additionally, the [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) class provides functions for serializing objects to stings, and deserializing strings to objects. Use this class for handling JSON data to support browsers that do not natively include the `JSON.parse` and `JSON.stringify` functions.

## Interaction avec les magasins ContextHub {#interacting-with-contexthub-stores}

Utilisez l’objet JavaScript [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) pour obtenir un magasin comme objet JavaScript. Une fois que vous avez obtenu l’objet de magasin, vous pouvez manipuler les données qu’il contient. Use the [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) or the [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) function to obtain the store.

### Accès aux données du magasin {#accessing-store-data}

The [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) Javascript class defines several functions for interacting with store data. Les fonctions suivantes stockent et récupèrent plusieurs éléments de données contenus dans des objets :

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

ContextHub comprend une structure d’événements qui vous permet de répondre automatiquement aux événements du magasin. Chaque objet du magasin contient un objet [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) disponible sous la forme d’une propriété [`eventing`](/help/sites-developing/contexthub-api.md#eventing) du magasin. Utilisez la fonction [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) ou [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) pour lier une fonction JavaScript à un événement de magasin.

## Utilisation de ContextHub pour manipuler des cookies {#using-context-hub-to-manipulate-cookies}

L’API JavaScript ContextHub offre une prise en charge de plusieurs navigateurs pour la gestion des cookies de navigateur. The [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) namespace defines several functions for creating, manipulating, and deleting cookies.

## Identification de segments ContextHub résolus {#determining-resolved-contexthub-segments}

Le moteur de segments ContextHub vous permet de déterminer quels segments enregistrés sont résolus dans le contexte actuel. Utilisez la fonction getResolvedSegments de la classe [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) pour récupérer les segments résolus. Then, use the `getName` or `getPath` function of the [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) class to test for a segment.

### Segments installés {#installed-segments}

ContextHub segments are installed below the `/conf/we-retail/settings/wcm/segments` node.

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
* Season is determined from the latitude data item of the [geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) store, and the month data item of the surferinfo store.

>[!WARNING]
>
>Les segments installés sont fournis en tant que configurations de référence pour vous aider à créer votre propre configuration dédiée pour votre projet et ne doivent donc pas être utilisés directement.

## Journalisation des messages de débogage pour ContextHub {#logging-debug-messages-for-contexthub}

Configure the Adobe Granite ContextHub OSGi service (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) to log detailed Debug messages that are useful when developing.

To configure the service you can either use the [Web Console](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) or use a [JCR node in the repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* Console web : pour consigner des messages de débogage, sélectionnez la propriété Debug.
* JCR node: To log Debug messages, set the boolean `com.adobe.granite.contexthub.debug` property to `true`.

## Affichage d’un aperçu de la structure ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub fournit une [page de diagnostics](/help/sites-developing/ch-diagnostics.md) qui affiche un aperçu de sa structure.
