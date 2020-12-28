---
title: Configuration d’une étape IBL avec Autodesk Maya et Mental Ray
seo-title: Configuration d’une scène IBL avec Autodesk Maya et Mental Ray
description: Découvrez comment configurer une scène IBL avec Autodesk Maya et Mental Ray.
seo-description: Découvrez comment configurer une scène IBL avec Autodesk Maya et Mental Ray.
uuid: 99878112-74c1-4a52-a7c2-c39927ce0e2a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 00f7ed25-276b-42c2-ae4c-11de357a9ec6
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 84%

---


# Configuration d’une scène IBL avec Autodesk Maya et Mental Ray{#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. Dans Maya, créez une nouvelle scène vide.

1. Créez une référence (temporaire) à un modèle représentatif. Ceci permet de faciliter l’évaluation de l’éclairage, la configuration des caméras, ainsi que celle du convertisseur.
1. Configurez l’éclairage basé par image.

   1. Dans Paramètres de rendu, sélectionnez **[!UICONTROL Rendu avec : Mental Ray]**, puis ouvrez l’onglet Scène.****
   1. Ouvrez l’accordéon **[!UICONTROL Environnement]**, puis cliquez sur **[!UICONTROL Créer un éclairage basé sur l’image]**.
   1. Cliquez sur l’icône de la boîte de dialogue qui présente une flèche vers la droite, située sur le côté gauche de la boîte de dialogue, pour sélectionner le nœud IBL `mentalRayIblShape1`[!UICONTROL , puis quittez les Paramètres de rendu].
   1. Dans l’**[!UICONTROL éditeur d’attributs]**, sélectionnez le noeud de transformation `mentalRayIbl1`, puis renommez le noeud de transformation en `AdobeIbl`.

   1. Définissez l’[!UICONTROL échelle] du noeud pour que la sphère d’environnement soit significativement plus grande que l’objet 3D le plus grand à afficher avec cette étape (par exemple, `10000,10000,10000`).
   1. Sélectionnez le nœud `AdobeIblShape` et configurez-le comme suit :

      * **[!UICONTROL Mappage]** : sphérique
      * **[!UICONTROL Type]** : fichier image
      * **[!UICONTROL Émission de lumière]** : vrai
   1. Joignez l’image TIFF de 32 bits souhaitée au noeud `AdobeIbl`.


1. Configurez le plan de masse.

   * Créez un plan approprié à utiliser comme plan de masse et redimensionnez-le pour l’adapter raisonnablement dans la sphère IBL, en passant par l’origine des coordonnées.
   * Associez un élément **[!UICONTROL Utiliser un arrière-plan]** au plan de masse et nommez-le `AdobeUseBackground` et associez-le à l’objet du plan de masse.

1. (Facultatif) Créez et configurez les caméras.

   Disposez les caméras « Look » vers le centre de la scène où cette ressource sera insérée. Assurez-vous de définir les caméras comme visionnables.

1. Configurez le rendu avec Mental Ray.

   Configurez les [!UICONTROL paramètres de rendu] avec les suggestions suivantes.

   * **** Courant

      Décochez la case **[!UICONTROL canal Alpha (masque)]** pour toutes les caméras de rendu.

   * **[!UICONTROL Onglet Qualité]**

      * **[!UICONTROL Qualité générale]** : `0.5`   ou moins
      * **[!UICONTROL Mode]**  Diffuse Indirecte (GI) -  `Final Gather`
      * **[!UICONTROL Taille]**  du filtre -  `2.0`,  `2.0`
   * Définissez le rendu de la scène selon les tailles de l’image type que vous comptez utiliser. Si nécessaire, affinez les lumières, les paramètres de rendu ou les deux pour parvenir au résultat souhaité.

       Gardez à l’esprit que le rendu avec Mental Ray, à l’aide de l’éclairage basé par image, est très lent et nécessite une utilisation importante du processeur. Adobe recommande de configurer les paramètres de qualité au niveau le plus faible, qui sont toujours capables de produire la qualité de rendu souhaité.


1. Supprimez la référence que vous avez créée à l’étape 2.

1. Enregistrez la scène, puis quittez Autodesk Maya.

1. Chargez la scène et le PTIFF IBL dans AEM et attendez que le traitement de chargement soit terminé.

   Voir la section [Chargement des ressources](/help/assets/managing-assets-touch-ui.md#uploading-assets).

1. Résolvez toutes les dépendances de fichier.

   Voir la section [Résolution des dépendances de fichier](/help/sites-classic-ui-authoring/classicui-upload-proc-3d-resolve-dependencies.md).

   AEM 3D ne pourra peut-être pas détecter l’image IBL configurée dans l’étape. Dans ce cas, vous devez résoudre manuellement les dépendances manquantes. Vous pouvez attribuer la même image PTIFF IBL précédemment chargée pour chacune des dépendances manquantes. Vous pouvez également affecter des images différentes pour un meilleur contrôle des effets IBL. Après la résolution des dépendances, assurez-vous d’appuyer sur **Enregistrer** pour lancer le retraitement.

1. Ouvrez les Propriétés de ressource dans AEM. Configurez le titre avec une chaîne appropriée qui apparaît dans la liste déroulante Sélecteur d’étapes. Vérifiez que **[!UICONTROL Classe]** est définie sur **[!UICONTROL Étape 3D]**. Enregistrez et fermez.

1. Ouvrez une ressource 3D, sélectionnez la nouvelle étape, et vérifiez qu’elle affiche un aperçu et présente un rendu comme prévu.

