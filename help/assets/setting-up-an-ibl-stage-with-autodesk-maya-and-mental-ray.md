---
title: Configuration d’une étape IBL avec Autodesk Maya et Mental Ray
seo-title: Configuration d’une étape IBL avec Autodesk Maya et Mental Ray
description: Comment configurer une étape IBL avec Autodesk Maya et Mental Ray
seo-description: Comment configurer une étape IBL avec Autodesk Maya et Mental Ray
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 78%

---


# Configuration d’une étape IBL avec Autodesk Maya et Mental Ray  {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. Dans Maya, créez une nouvelle scène vide.

1. Créez une référence (temporaire) à un modèle représentatif. Ceci permet de faciliter l’évaluation de l’éclairage, la configuration des caméras, ainsi que celle du convertisseur.
1. Configurez l’éclairage basé par image.

   1. Dans **[!UICONTROL Paramètres de rendu]**, sélectionnez **[!UICONTROL Rendu avec : rayon mental]**, puis ouvrez l’onglet Scène.
   1. Ouvrez l’accordéon **[!UICONTROL Render Environnement]** et cliquez sur **[!UICONTROL Render Create Image Based Lighting]**.
   1. Cliquez sur l’icône de zone contenant une flèche vers la droite sur le côté gauche de la zone pour sélectionner le noeud IBL `mentalRayIblShape1`, puis quittez **[!UICONTROL Paramètres de rendu]**.
   1. Dans l’**[!UICONTROL éditeur d’attributs]**, sélectionnez le noeud de transformation `mentalRayIbl1`, puis renommez le noeud de transformation en `AdobeIbl`.
   1. Définissez l’Échelle du nœud pour agrandir la sphère d’environnement afin que celle-ci soit bien plus grande que l’objet 3D le plus grand à afficher avec cette étape (par exemple, `10000,10000,10000`).
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

   Configurez les **[!UICONTROL paramètres de rendu]** avec les suggestions suivantes.

   * **** Courant

      Décochez la case **[!UICONTROL canal Alpha (masque)]** pour toutes les **[!UICONTROL caméras renouvelables]**.

   * **[!UICONTROL Onglet Qualité]**

      * **Qualité générale** : `0.5`   ou moins
      * **Mode**  Diffuse Indirecte (GI) -  `Final Gather`
      * **Taille**  du filtre -  `2.0`,  `2.0`
   * Définissez le rendu de la scène selon les tailles de l’image type que vous comptez utiliser. Si nécessaire, affinez les lumières, les paramètres de rendu ou les deux pour parvenir au résultat souhaité.

       Gardez à l’esprit que le rendu avec Mental Ray, à l’aide de l’éclairage basé par image, est très lent et nécessite une utilisation importante du processeur. Adobe recommande de configurer les paramètres de qualité au niveau le plus faible, qui sont toujours capables de produire la qualité de rendu souhaité.


1. Supprimez la référence que vous avez créée à l’étape 2.

1. Enregistrez la scène, puis quittez Autodesk Maya.

1. Chargez la scène et le PTIFF IBL dans AEM et attendez que le traitement de chargement soit terminé.

   Voir la section [Chargement des ressources](managing-assets-touch-ui.md#uploading-assets).

1. Résolvez toutes les dépendances de fichier.

   Voir la section [Résolution des dépendances de fichier](resolve-file-dependencies.md).

   AEM 3D ne pourra peut-être pas détecter l’image IBL configurée dans l’étape. Dans ce cas, vous devez résoudre manuellement les dépendances manquantes. Vous pouvez attribuer la même image PTIFF IBL précédemment chargée pour chacune des dépendances manquantes. Vous pouvez également affecter des images différentes pour un meilleur contrôle des effets IBL. Après la résolution des dépendances, assurez-vous d’appuyer sur **[!UICONTROL Enregistrer]** pour lancer le retraitement.

1. Ouvrez les Propriétés de ressource dans AEM. Définissez **[!UICONTROL Title]** sur une chaîne appropriée qui apparaîtra dans la liste déroulante **[!UICONTROL Sélecteur d’état]**. Vérifiez que **[!UICONTROL Classe]** est définie sur **[!UICONTROL Étape 3D]**. Enregistrez et fermez.

1. Ouvrez une ressource 3D, sélectionnez la nouvelle étape, et vérifiez qu’elle affiche un aperçu et présente un rendu comme prévu.

