---
title: Console des composants
seo-title: Console des composants
description: 'null'
seo-description: 'null'
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 95%

---


# Console des composants{#components-console}

La console des composants vous permet de parcourir tous les composants définis pour votre instance et d’afficher les informations clés pour chacun d’eux.

Il est accessible à partir de **Outils** -> **Général** -> **Composants**. Dans la console, les modes Carte et Liste sont disponibles. Comme il n’existe pas de structure d’arborescence pour les composants, le mode Colonnes n’est pas disponible.

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>La console des composants affiche tous les composants du système. L’[Explorateur de composants](/help/sites-authoring/author-environment-tools.md#components-browser) affiche les composants qui sont disponibles pour les auteurs et masque tous les groupes de composants qui commencent par un point ( `.`).

## Recherche {#search-features}

Avec l’icône **Contenu uniquement** (en haut à gauche), vous pouvez ouvrir le panneau de **recherche** pour rechercher et/ou filtrer les composants :

![chlimage_1-302](assets/chlimage_1-302.png)

## Détails des composants {#component-details}

Pour afficher les détails correspondant à un composant spécifique, appuyez/cliquez sur la ressource requise. Trois onglets fournissent :

* **Propriétés**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   L’onglet Propriétés vous permet d’effectuer les opérations suivantes :

   * Afficher les propriétés générales du composant.
   * Observez comment l’[icône ou l’abréviation a été définie](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) pour le composant.

      * Cliquez sur la source de l’icône pour accéder à ce composant.
   * Affichez le **Type de ressource** et le **Type de super-ressource** (s’il est défini) du composant.

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

   Si le développeur a fourni la [documentation du composant](/help/sites-developing/developing-components.md#documenting-your-component), elle apparaîtra dans l’onglet **Documentation**. Si aucune documentation n’est disponible, l’onglet **Documentation** n’est pas affiché.

   ![chlimage_1-305](assets/chlimage_1-305.png)

