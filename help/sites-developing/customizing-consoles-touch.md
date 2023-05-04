---
title: Personnaliser les consoles
seo-title: Customizing the Consoles
description: AEM fournit divers mécanismes pour vous permettre de personnaliser les consoles de votre instance de création.
seo-description: AEM provides various mechanisms to enable you to customize the consoles of your authoring instance
uuid: f10cea87-ef8a-468e-94ca-89a1017dcf44
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 221ed05b-855d-4dc2-9df6-12fdeabb157a
exl-id: 31bced35-4845-40d1-9bfd-5c75d54e1a83
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 49%

---

# Personnaliser les consoles{#customizing-the-consoles}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!CAUTION]
>
>Ce document décrit comment personnaliser des consoles dans l’IU tactile moderne et ne s’applique pas à l’IU classique.

AEM fournit divers mécanismes pour vous permettre de personnaliser les consoles (et les [fonctionnalité de création de pages](/help/sites-developing/customizing-page-authoring-touch.md)) de votre instance de création.

* Clientlibs

    Les bibliothèques clientes (clientlibs) vous permettent d’étendre l’implémentation par défaut afin d’obtenir la nouvelle fonctionnalité, tout en réutilisant les fonctions, objets et méthodes standard. Lors de la personnalisation, vous pouvez créer votre propre bibliothèque cliente sous `/apps.` Par exemple, il peut contenir le code requis pour votre composant personnalisé.

* Recouvrements

   Les recouvrements sont basés sur les définitions de nœuds et vous permettent de recouvrir la fonctionnalité standard (dans `/libs`) avec votre propre fonctionnalité personnalisée (dans `/apps`). Lors de la création d’une superposition, une copie 1:1 de l’original n’est pas nécessaire, car Sling Resource Merger permet l’héritage.

Elles peuvent être utilisées de différentes manières pour étendre vos consoles AEM. Une petite sélection est abordée ci-dessous (à un niveau élevé).

>[!NOTE]
>
>Pour plus d’informations, voir :
>
>* Utilisation et création [clientlibs](/help/sites-developing/clientlibs.md).
>* Utilisation et création [superpositions](/help/sites-developing/overlays.md).
>* [Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)
>
>Ce thème est également abordé dans la session [AEM Gems – Personnalisation de l’interface utilisateur pour AEM 6.0](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-user-interface-customization-for-aem6.html).

>[!CAUTION]
>
>Vous ne devez ***rien*** modifier dans le chemin `/libs`.
>
>En effet, le contenu de `/libs` est remplacé dès que vous mettez à niveau votre instance (et risque de l’être si vous appliquez un correctif ou un Feature Pack).
>
>La méthode recommandée pour la configuration et d’autres modifications est la suivante :
>
>1. Recréez l’élément requis (tel qu’il existe dans `/libs`) sous `/apps`.
>
>1. Apportez les modifications désirées dans `/apps`.

>


Par exemple, les emplacements suivants dans la variable `/libs` peut être superposée :

* Consoles (toutes les consoles basées sur les pages de l’IU Granite), par exemple :

   * `/libs/wcm/core/content`

<!-- Needs a review by Engineering -->
<!--
* secondary (inner) rails; for example:

    * `/libs/wcm/core/content/search`

* toolbar(s) (dependent on console; for example sites):

    * default 

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/default`

    * selection mode

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/selection`

* help menu options (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/help`

* information shown on the card view (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/content/content/items/childpages`

-->
>[!NOTE]
>
>Consultez l’article de la base de connaissances [Résolution des problèmes liés à l’IU tactile d’AEM](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html) pour découvrir d’autres conseils et outils.

<!-- Needs a review by Engineering -->
<!--
## Code Samples {#code-samples}

Various packages have been made available on Github. These provide code samples related to the tasks covered on this page.

### aem-admin-extension-new-console {#aem-admin-extension-new-console}

`aem-admin-extension-new-console` is a sample package showing how to [create a new AEM 6 console](#create-a-custom-console). This package provides a UI for managing [Launches](/help/sites-authoring/launches.md) and adds a link in the navigation:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)

### aem-admin-extension-customize-sites {#aem-admin-extension-customize-sites}

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Create a Custom Console {#create-a-custom-console}

1. You can create a custom console with related actions; for example, Launches at the top level (below Sites):

   This involves:

    * creating the root space definition of your new console ``; for example:

        * `/apps/<yourProject>/admin/ext/launches`

    * this can contain (according to requirements):

        * the corresponding [clientlibs](/help/sites-developing/clientlibs.md) for custom actions and `less`/ `css` definitions

            * `/apps/<yourProject>/admin/ext/launches/clientlibs`

        * components that need to be redefined/adjusted; for example, the breadcrumbs, datasource and the launch

            * `/apps/<yourProject>/admin/ext/launches/components`

        * the Granite UI page resource:

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content`

              property: `sling:resourceType`

        * the page definition of the console

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/head`
            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body`

   ![chlimage_1-236](assets/chlimage_1-236.png)

   To use the new console (for example in the [rail for navigation](#add-new-navigation-option-to-rail)) an ID is used, so that it can be explicitly referenced. The ID is used to connect the console and its navigation definition. The ID is defined in the `rail` node of the page; for example, for the Sites console:

    * the rail node is: 

      `/libs/wcm/core/content/sites/jcr:content/body/rail`

        * here the `currentId` property is defined: 

          `currentId` = `cq-sites`

   For the Launches console example:

    * the node is:

        * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`

    * with the following properties:

        * `currentId` = `cq-launches`
        * `sling:resourceType` = `granite/ui/components/endor/navcolumns`
        * `srcPath` = `cq/core/content/nav`
-->

## Personnalisation de l’affichage par défaut d’une console {#customizing-the-default-view-for-a-console}

Vous pouvez personnaliser la vue par défaut (colonne, carte, liste) d’une console :

1. Vous pouvez réorganiser les vues en recouvrant l’entrée requise depuis l’emplacement suivant :

   `/libs/wcm/core/content/sites/jcr:content/views`

   La première entrée est la valeur par défaut.

   Les nœuds disponibles correspondent aux options d’affichage disponibles :

   * `column`
   * `card`
   * `list`

1. Par exemple, dans un recouvrement de liste :

   `/apps/wcm/core/content/sites/jcr:content/views/list`

   Définissez la propriété suivante :

   * **Nom** : `sling:orderBefore`
   * **Type** : `String`
   * **Valeur** : `column`

<!-- Needs a review by Engineering -->
<!--
`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
### Add New Navigation Option to Rail {#add-new-navigation-option-to-rail}

1. You can add a navigation entry in the rail (for example, a [custom console](#create-a-custom-console) such as Launches).

   To do this, you create an overlay of:

   `/libs/cq/core/content/nav`

   In the `/apps` overlay:

   `/apps/cq/core/content/nav`

   Create the new nodes and properties:

   ![chlimage_1-237](assets/chlimage_1-237.png)

    * Extend navigation:

        * `/apps/cq/core/content/nav/launches`

    * Specify location in the tree:

        * property: `sling:orderBefore`

    * To create the connection, the `id` property references (i.e. must be the same as) the `currentID` property [for the appropriate console](#create-a-custom-console):

        * property: `id`
        * value: same as for your console (e.g. `cq-launches`) 

          for example: the same value as the `currentId` property on:

          `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`
-->

## Ajouter une nouvelle action à la barre d’outils {#add-new-action-to-the-toolbar}

1. Vous pouvez créer vos propres composants et inclure les bibliothèques clientes correspondantes pour les actions personnalisées. Par exemple, un **Convertir en Twitter** Action à l’adresse :

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   Elle peut ensuite être connectée à un élément de la barre d’outils sur la console :

   `/apps/<yourProject>/admin/ext/launches`

   Par exemple, en mode de sélection :

   `content/jcr:content/body/content/header/items/selection/items/twitter`

## Limitation d’une action de barre d’outils à un groupe spécifique {#restrict-a-toolbar-action-to-a-specific-group}

1. Vous pouvez utiliser une condition de rendu personnalisée pour superposer l’action standard et imposer des conditions spécifiques qui doivent être remplies avant son rendu.

   Par exemple, créez un composant pour contrôler les conditions de rendu en fonction du groupe :

   `/apps/myapp/components/renderconditions/group`

1. Pour les appliquer à l’action Créer un site sur la console Sites :

   `/libs/wcm/core/content/sites`

   Créez le recouvrement :

   `/apps/wcm/core/content/sites`

1. Ajoutez ensuite la condition de rendu pour l’action :

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   En utilisant des propriétés sur ce nœud, vous pouvez définir les `groups` autorisés à effectuer l’action spécifique ; par exemple, les `administrators`.

<!-- Needs a review by Engineering -->
<!--
## Remove Access to Navigation Option on Rail {#remove-access-to-navigation-option-on-rail}

1. You can rename a navigation entry in the rail by overlaying the required entry from under:

   `/libs/cq/core/content/nav`

   The nodes available correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`

1. For example, on a overlay at:

   `/apps/cq/core/content/nav/sites`

   Define the following property:

    * **Name**: `sling:hideResource`
    * **Type**: `String` 
    * **Value**: `true`

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Restrict Access to Navigation Option on Rail {#restrict-access-to-navigation-option-on-rail}

You can restrict access to a navigation option using ACLs:

1. Open the [user and/or group management](/help/sites-administering/security.md) and select the user/group you want to restrict access for.

   >[!NOTE]
   >
   >Avoid assigning/restricting permissions on a user-by-user basis. It is [recommended to use groups](/help/sites-administering/security.md#best-practices).

1. Remove access [permissions](/help/sites-administering/security.md#permissions) to the appropriate node(s) under `/libs/cq/core/content/nav/sites`. These correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`
-->

## Personnalisation des colonnes dans la vue Liste {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Cette fonction est optimisée pour les champs de colonnes de texte ; pour les autres types de données, il est possible de remplacer `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` dans `/apps`.

<!-- Needs a review by Engineering -->
<!--
CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-sites-extension-listview-columns project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns/archive/master.zip)
-->

Pour personnaliser les colonnes en mode Liste :

1. Recouvrez la liste des colonnes disponibles.

   * Sur le nœud :

      `/apps/wcm/core/content/common/availablecolumns`

   * Ajoutez des colonnes ou supprimez des colonnes existantes.
   Consultez [Utilisation des recouvrements (et fusion de ressources Sling) pour plus d’informations.](/help/sites-developing/overlays.md)

1. Facultatif :

   * Si vous souhaitez connecter des données supplémentaires, vous devez écrire un ` [PageInforProvider](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html)` avec une

      `pageInfoProviderType`.
   Par exemple, consultez la classe/le lot joint (à partir de GitHub) ci-dessous.

1. Vous pouvez désormais sélectionner la colonne dans le paramétrateur de colonnes du mode Liste.

## Filtrage des ressources {#filtering-resources}

Lors de l’utilisation d’une console, un cas d’utilisation courant se présente lorsque l’utilisateur doit effectuer un choix parmi des ressources (pages, composants, ressources, etc.). Cela peut prendre la forme d’une liste, par exemple à partir de laquelle l’auteur doit choisir un élément.

Pour maintenir la liste à une taille raisonnable et adaptée au cas d’utilisation, un filtre peut être mis en oeuvre sous la forme d’un prédicat personnalisé. Voir [cet article](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) pour plus d’informations.
