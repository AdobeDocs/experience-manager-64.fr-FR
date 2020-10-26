---
title: NE PAS PUBLIER, MAIS NE PAS Personnaliser DELETE les modèles de fragments de contenu
seo-title: Personnalisation des modèles de fragments de contenu
description: Les modèles de fragments de contenu peuvent être personnalisés et étendus.
seo-description: Les modèles de fragments de contenu peuvent être personnalisés et étendus.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 3%

---


# NE PAS PUBLIER, MAIS NE PAS Personnaliser DELETE les modèles de fragments de contenu{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

L’éditeur de modèle de fragment de contenu est un assistant basé sur `Formbuilder`les éléments suivants :

`granite/ui/components/foundation/form/formbuilder`

Ce composant dispose des outils nécessaires pour effectuer le rendu de l&#39;interface glisser-déposer de l&#39;éditeur de modèles, avec les types de données et les propriétés pour chacun d&#39;eux.

## Emplacements {#locations}

Les modèles sont enregistrés et créés sous `/conf`, sous un dossier dans lequel la propriété [Modèles de fragment de](/help/assets/content-fragments-models.md#enable-content-fragment-models) contenu est activée. Ce paramètre est également visible dans les Propriétés **de** configuration, accessibles depuis le navigateur **[de](/help/sites-administering/configurations.md)** configuration.

1. Naviguer jusqu’au navigateur à l’aide des **outils**, **Général**, Navigateur **de** configuration, par exemple : 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. Dans le navigateur, sélectionnez la configuration appropriée, puis **Propriétés** dans la barre d’outils.

   Par exemple, les propriétés pour `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

Dans la console des modèles, tous les dossiers contenant la propriété Modèles **de fragment de** contenu s’affichent. Accédez à l’aide des **outils**, des **ressources**, des modèles **de fragment de** contenu ; par exemple, `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Un utilisateur peut [créer un modèle](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) de fragment de contenu à l’aide de l’assistant **Créer un modèle** (à l’aide de **Créer** à partir de la console).

>[!CAUTION]
>
>Vous ne devez ***rien*** modifier dans le chemin `/libs`.
>
>This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may be overwritten when you apply either a hotfix or feature pack).

## Structure d&#39;un modèle {#structure-of-a-model}

L&#39;Assistant va créer une entrée avec cette structure :

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Tous les modèles sont enregistrés sous des sous-dossiers de ce dossier.

* `jcr:content`

   Chaque modèle contient un `jcr:content` noeud qui :

   * contient des propriétés d’informations sur le modèle, telles que `jcr:title`, `lastModified`, `lastModifiedBy`
   * a généralement la `sling:ResourceType` valeur de `dam/cfm/models/console/components/data/entity/default`,

      avec la valeur `sling:ResourceSuperType` de `dam/cfm/models/console/components/data/entity`

* `model`

   Le `model` noeud contient une propriété `dataTypesConfig`, utilisée pour déterminer les types de données utilisés dans l’éditeur de modèles.

* `items`

   Sous le `items` noeud, tous les types de données ajoutés au modèle sont enregistrés (comme glissés-déposés dans l’éditeur de modèles). Chaque élément reçoit un nom de noeud aléatoire, mais pour que l’éditeur de fragments de contenu fonctionne avec ce modèle, chaque élément doit posséder une `name` propriété. De plus, sur ce noeud, toutes les propriétés de configuration d’un type de données particulier sont enregistrées, y compris les propriétés par défaut nécessaires au rendu des composants.

>[!CAUTION]
>
>Tous les types de données glissés-déposés dans un éditeur de modèles, et par conséquent instanciés, **doivent** `name` avoir la propriété saisie par l’utilisateur.
>
>Il s’agit du nom de la **propriété &amp;ast;** dans l’onglet **Propriétés** de l’éditeur de modèles.

## Structure de l&#39;éditeur de modèles {#structure-of-the-model-editor}

L’éditeur **de modèle de fragment de** contenu comporte deux parties :

* Panneau de prévisualisation, ou vue, sur le côté gauche, dans lequel vous pouvez déposer des éléments. Cela :

   * Affiche une prévisualisation du type **de** données appelé.
   * Autorise l&#39;ordre dans l&#39;éditeur de modèles.

* Les onglets Types **de** données/**Propriétés** du panneau situé à droite s’affichent. Cela :

   * Affiche une liste de types de données qui peuvent être déplacés et instanciés.
   * Pour l’éditeur de modèles prêt à l’emploi, la liste est présente à l’adresse suivante :

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Tous les types de données générés comportent deux balises de script qui, lorsqu’elles sont instanciées, forment la vue (le composant rendu sur le côté gauche) et l’onglet **Propriétés** , qui définit les propriétés qu’un utilisateur peut définir pour un composant donné.

>[!CAUTION]
>
>Vous ne devez ***rien*** modifier dans le chemin `/libs`.
>
>This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may be overwritten when you apply either a hotfix or feature pack).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Lorsqu’un type de données est instancié, des entrées HTML sont créées pour chaque propriété dont le composant doit être rendu dans un fragment de contenu. Par exemple :

* **Nom de la propriété &amp;ast;** ( `name`) - agit comme identificateur pour les composants

* **Rendu en tant que** ( `metaType`) - tapez le composant à rendre en tant que

* **Description** ( `fieldDescription`) - description du composant dans le fragment de contenu

* Autres.

