---
title: Configuration d’une étape standard avec Autodesk Maya et Mental Ray
seo-title: Configuration d’une scène standard avec Autodesk Maya et Mental Ray
description: Découvrez comment configurer une scène standard avec Autodesk Maya et Mental Ray.
seo-description: Découvrez comment configurer une scène standard avec Autodesk Maya et Mental Ray.
uuid: 05c4858b-6261-4de3-a87a-03dd6bc519a4
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f30c4039-3bbf-4d02-a9b5-bda6ccce16b9
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 88%

---


# Configuration d’une scène standard avec Autodesk Maya et Mental Ray{#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

1. Dans Maya, créez une nouvelle scène vide.
1. Créez une référence (temporaire) à un modèle représentatif. Ceci permet de faciliter l’évaluation de l’éclairage, la configuration des caméras, ainsi que celle du convertisseur.

1. Ajoutez des lumières comme d’ordinaire. Actuellement, AEM 3D prend en charge les types de lumière suivants :

   * Lumières directionnelles
   * Projecteurs
   * Lumières ponctuelles

   D’autres types de lumière sont ignorés ou convertis dans l’un des types pris en charge ci-dessus lorsque l’étape est chargée dans AEM 3D. Les types convertis sont utilisés lorsque vous affichez la ressource et lorsque vous utilisez le convertisseur Rapid Refine intégré pour le rendu. Les types de lumière d’origine sont utilisés lors du rendu avec Maya.

1. Créez un plan de masse, si nécessaire, et appliquez un matériau approprié.

   Adobe recommande de définir un plan de masse à un seul côté. Cela vous garantit un affichage de la ressource sous AEM 3D sans que le plan de masse ne masque la ressource.

1. (Facultatif) Créez et configurez les caméras.

   Disposez les caméras « Look » vers le centre de la scène où cette ressource sera insérée. Assurez-vous de définir les caméras comme visionnables.

1. Configurez le rendu avec Mental Ray.

   Configurez les **[!UICONTROL paramètres de rendu]** avec les suggestions suivantes :

   * **** Courant

      Décochez la case **[!UICONTROL canal Alpha (masque)]** pour toutes les [!UICONTROL caméras renouvelables].

   * **[!UICONTROL Onglet Qualité]**

      * **** `- 0.5` Qualité globale ou moins
      * **[!UICONTROL Mode]**  Diffuse Indirecte (GI) -  `Final Gather`
      * **[!UICONTROL Taille]**  du filtre -  `2.0`,  `2.0`
   * Définissez le rendu de la scène selon les tailles de l’image type que vous comptez utiliser. Si nécessaire, affinez les lumières ou [!UICONTROL Render settings], ou effectuez les deux pour obtenir les résultats souhaités.

       Gardez à l’esprit que le rendu avec Mental Ray, à l’aide de l’éclairage basé par image, est très lent et nécessite une utilisation importante du processeur. Adobe recommande de configurer les paramètres de qualité au niveau le plus faible, qui sont toujours capables de produire la qualité de rendu souhaité.


1. Supprimez la référence que vous avez créée à l’étape 2.
1. Enregistrez la scène, puis quittez Autodesk Maya.
1. Chargez la scène dans AEM et attendez que le traitement de chargement soit terminé.

   Voir la section [Chargement des ressources](/help/assets/managing-assets-touch-ui.md#uploading-assets).

   Si Autodesk® Maya® n’est pas configuré sur le serveur AEM, exportez un FBX depuis Maya et chargez-le dans AEM.

1. Ouvrez les Propriétés de ressource dans AEM. Configurez le titre avec une chaîne appropriée qui apparaît dans la liste déroulante Sélecteur d’étapes. Vérifiez que **[!UICONTROL Classe]** est définie sur **[!UICONTROL Étape 3D]**. Enregistrez et fermez.
1. Ouvrez une ressource 3D, sélectionnez la nouvelle étape, et vérifiez qu’elle affiche un aperçu et présente un rendu comme prévu.

