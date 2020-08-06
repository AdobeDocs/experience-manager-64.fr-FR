---
title: Configuration d’une étape standard avec Autodesk Maya et Mental Ray
seo-title: Configuration d’une étape standard avec Autodesk Maya et Mental Ray
description: Comment configurer une étape standard avec Autodesk Maya et Mental Ray
seo-description: Comment configurer une étape standard avec Autodesk Maya et Mental Ray
uuid: 3895fda6-29ae-46f5-b2bc-abc989808648
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: da8fc33b-84ae-4ead-87bb-5a7870a38b1f
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 91%

---


# Configuration d’une étape standard avec Autodesk Maya et Mental Ray {#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

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

   Configurez les paramètres de rendu d’après les suggestions suivantes :

   * **[!UICONTROL Onglet courant]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all Renderable Cameras.

   * **[!UICONTROL Onglet Qualité]**

      * **[!UICONTROL Qualité]** globale `- 0.5` ou moins
      * **[!UICONTROL Mode]** Diffuse Indirecte (GI) - `Final Gather`
      * **[!UICONTROL Taille]** du filtre - `2.0`, `2.0`
   * Définissez le rendu de la scène selon les tailles de l’image type que vous comptez utiliser. Si nécessaire, affinez les lumières, ou les paramètres de rendu ou les deux pour parvenir au résultat souhaité.

       Gardez à l’esprit que le rendu avec Mental Ray, à l’aide de l’éclairage basé par image, est très lent et nécessite une utilisation importante du processeur. Adobe recommande de configurer les paramètres de qualité au niveau le plus faible, qui sont toujours capables de produire la qualité de rendu souhaité.


1. Supprimez la référence que vous avez créée à l’étape 2.

1. Enregistrez la scène, puis quittez Autodesk Maya.
1. Chargez la scène dans AEM et attendez que le traitement de chargement soit terminé.

   Voir la section [Chargement des ressources](managing-assets-touch-ui.md#uploading-assets).

   Si Autodesk® Maya® n’est pas configuré sur le serveur AEM, exportez un FBX depuis Maya et chargez-le dans AEM.

1. Ouvrez les Propriétés de ressource dans AEM. Set **[!UICONTROL Title]** to a suitable string that will appear in the **[!UICONTROL Stage Selector]** drop-down list. Vérifiez que **[!UICONTROL Classe]** est définie sur **[!UICONTROL Étape 3D]**. Enregistrez et fermez.
1. Ouvrez une ressource 3D, sélectionnez la nouvelle étape, et vérifiez qu’elle affiche un aperçu et présente un rendu comme prévu.

