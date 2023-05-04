---
title: Console des composants
seo-title: Components Console
description: Console des composants
seo-description: null
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
exl-id: fa583a06-e75c-41de-a977-7e459ab8bca9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 53%

---

# Console des composants{#components-console}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La console Composants vous permet de parcourir tous les composants définis pour votre instance et d’afficher les informations clés de chaque composant.

Il est accessible à partir de **Outils** -> **Général** -> **Composants**. Dans la console, les vues Carte et Liste sont disponibles. Comme il n’existe pas de structure d’arborescence pour les composants, le mode Colonnes n’est pas disponible.

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>La console des composants affiche tous les composants du système. L’[Explorateur de composants](/help/sites-authoring/author-environment-tools.md#components-browser) affiche les composants qui sont disponibles pour les auteurs et masque tous les groupes de composants qui commencent par un point (`.`).

## Rechercher {#search-features}

Avec l’icône **Contenu uniquement** (en haut à gauche), vous pouvez ouvrir le panneau de **recherche** pour rechercher et/ou filtrer les composants :

![chlimage_1-302](assets/chlimage_1-302.png)

## Détails des composants {#component-details}

Pour afficher des détails sur un composant spécifique, appuyez/cliquez sur la ressource requise. Trois onglets sont proposés :

* **Propriétés**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   L’onglet Propriétés vous permet d’effectuer les opérations suivantes :

   * Afficher les propriétés générales du composant.
   * Afficher le mode de [une icône ou une abréviation a été définie.](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) pour le composant.

      * Cliquez sur la source de l’icône pour accéder à ce composant.
   * Afficher la variable **Type de ressource** et **Resource Super Type** (s’il est défini) pour le composant.

      * Cliquez sur le type de super-ressource pour accéder à ce composant.
   >[!NOTE]
   >
   >Étant donné que les `/apps` ne sont pas modifiables à l’exécution, la console Composants est en lecture seule.

* **Stratégies**

   ![chlimage_1-303](assets/chlimage_1-303.png)

* **Utilisation en direct**

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!CAUTION]
   >
   >En raison de la nature des informations collectées pour cette vue, la collecte/l’affichage de ces informations peut nécessiter un certain temps.

* **Documentation**

   Si le développeur a fourni [documentation du composant](/help/sites-developing/developing-components.md#documenting-your-component), il apparaîtra sur le **Documentation** . Si aucune documentation n’est disponible, l’onglet **Documentation** n’est pas affiché.

   ![chlimage_1-305](assets/chlimage_1-305.png)
