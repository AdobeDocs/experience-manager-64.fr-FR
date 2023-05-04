---
title: NE PAS PUBLIER, MAIS NE PAS DELETE La Personnalisation Des Modèles De Fragment De Contenu
seo-title: Customizing Content Fragment Models
description: Les modèles de fragment de contenu peuvent être personnalisés et étendus.
seo-description: Content Fragment Models can be customized and extended.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: AEM Docs
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 13%

---


# NE PAS PUBLIER, MAIS NE PAS DELETE La Personnalisation Des Modèles De Fragment De Contenu{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’éditeur de modèle de fragment de contenu est un assistant basé sur `Formbuilder`, hérité de :

`granite/ui/components/foundation/form/formbuilder`

Ce composant dispose des outils nécessaires pour effectuer le rendu de l’interface glisser-déposer de l’éditeur de modèles, avec les types de données et les propriétés pour chacun d’eux.

## Emplacements {#locations}

Les modèles sont enregistrés et créés sous `/conf`, sous un dossier qui contient la propriété [Propriété Modèles de fragment de contenu](/help/assets/content-fragments-models.md#enable-content-fragment-models) activée. Ce paramètre est également visible dans la variable **Propriétés de configuration**, accessible à partir du **[Explorateur de configuration](/help/sites-administering/configurations.md)**.

1. Accédez au navigateur via **Outils**, **Général**, **Explorateur de configuration**
Par exemple : 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. Dans le navigateur, sélectionnez la configuration appropriée, puis **Propriétés** dans la barre d’outils.

   Par exemple, les propriétés de `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

Dans la console Modèles, tous les dossiers contenant la variable **Modèles de fragment de contenu** s’affiche. Navigation via **Outils**, **Ressources**, **Modèles de fragment de contenu**; par exemple, `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Un utilisateur peut [créer un modèle de fragment de contenu ;](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) en utilisant la variable **Créer un modèle** assistant (à l’aide de **Créer** dans la console).

>[!CAUTION]
>
>Vous ne devez ***rien*** modifier dans le chemin `/libs`.
>
>Cela est dû au fait que le contenu de `/libs` sera écrasé la prochaine fois que vous mettrez à niveau votre instance (et éventuellement lors de l’application d’un correctif logiciel ou d’un pack de fonctionnalités).

## Structure d’un modèle {#structure-of-a-model}

L&#39;assistant va créer une entrée avec cette structure :

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Tous les modèles sont enregistrés sous des sous-dossiers de ce dossier.

* `jcr:content`

   Chaque modèle contient un `jcr:content` qui :

   * contient des propriétés d’informations sur le modèle, telles que `jcr:title`, `lastModified`, `lastModifiedBy`
   * a généralement la variable `sling:ResourceType` de `dam/cfm/models/console/components/data/entity/default`,

      avec le `sling:ResourceSuperType` de `dam/cfm/models/console/components/data/entity`

* `model`

   Le `model` Le noeud contient une propriété `dataTypesConfig`, utilisé pour déterminer les types de données utilisés dans l’éditeur de modèles.

* `items`

   Sous , `items` , tous les types de données ajoutés au modèle sont enregistrés (comme déplacés et déposés dans l’éditeur de modèles). Chaque élément reçoit un nom de noeud aléatoire, mais pour que l’éditeur de fragment de contenu fonctionne avec ce modèle, chaque élément doit disposer d’un `name` . En outre, sur ce noeud, toutes les propriétés de configuration d’un type de données particulier sont enregistrées, y compris les propriétés par défaut nécessaires au rendu des composants.

>[!CAUTION]
>
>Tous les types de données déplacés et déposés dans un éditeur de modèles et, par conséquent, instanciés, **must** avoir la variable `name` saisie par l’utilisateur.
>
>Cela est considéré comme **Nom de la propriété &amp;ast;** dans le **Propriétés** de l’éditeur de modèles.

## Structure de l’éditeur de modèles {#structure-of-the-model-editor}

Le **Éditeur de modèle de fragment de contenu** comporte deux parties :

* Panneau de prévisualisation, ou d’affichage, sur le côté gauche, dans lequel vous pouvez déposer des éléments. Cela :

   * Affiche un aperçu de la variable **Type de données** qui est instancié.
   * Autorise l’ordre dans l’éditeur de modèles.

* Le **Types de données**/**Propriétés** dans le panneau situé à droite. Cela :

   * Affiche une liste des types de données qui peuvent être déplacés et instanciés.
   * Pour l’éditeur de modèle d’usine, la liste se trouve à l’adresse suivante :

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Tous les types de données générés comportent deux balises de script qui, lorsqu’elles sont instanciées, forment la vue (le composant rendu sur le côté gauche) et la balise **Propriétés** qui définit les propriétés qu’un utilisateur peut définir pour un composant donné.

>[!CAUTION]
>
>Vous ne devez ***rien*** modifier dans le chemin `/libs`.
>
>Cela est dû au fait que le contenu de `/libs` sera écrasé la prochaine fois que vous mettrez à niveau votre instance (et éventuellement lors de l’application d’un correctif logiciel ou d’un pack de fonctionnalités).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Lorsqu’un type de données est instancié, des entrées de HTML sont créées pour chaque propriété dont le composant doit être rendu dans un fragment de contenu. Par exemple, les éléments suivants incluent :

* **Nom de la propriété &amp;ast;** ( `name`) : agit comme identifiant pour les composants

* **Render As** ( `metaType`) : saisissez le rendu du composant.

* **Description** ( `fieldDescription`) : description du composant dans le fragment de contenu.

* et autres.

