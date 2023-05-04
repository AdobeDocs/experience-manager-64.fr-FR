---
title: Application de paramètres d’image prédéfinis Dynamic Media
seo-title: Applying Dynamic Media image presets
description: Découvrez comment appliquer des paramètres prédéfinis d’image Dynamic Media
seo-description: Learn how to apply image presets in Dynamic Media
uuid: 8bafcbd0-6df0-4d5b-b2f7-116ddb4ec060
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5c1f60ac-3741-4002-9c5d-c128f118342b
exl-id: 07a4f315-a60e-456b-b02d-035b3f6ad9ad
feature: Image Presets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 61%

---

# Application de paramètres d’image prédéfinis Dynamic Media {#applying-image-presets}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les préréglages d’image permettent aux ressources de fournir dynamiquement des images de différentes tailles, dans différents formats ou avec d’autres propriétés d’image qui sont générées dynamiquement. Vous pouvez choisir un paramètre prédéfini lorsque vous exportez des images, qui reformate également les images selon les spécifications définies par votre administrateur.

Vous pouvez en outre sélectionner un paramètre prédéfini d’image réactif (signalé par le bouton **[!UICONTROL RESS]** une fois que vous l’avez sélectionné).

Cette section décrit comment utiliser les paramètres d’image prédéfinis. [L’administration peut créer et configurer des paramètres prédéfinis d’image](managing-image-presets.md).

>[!NOTE]
>
>L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis et utilise des informations à la dernière milliseconde de la diffusion pour réduire davantage encore la taille du fichier d’image en fonction de la vitesse de connexion du réseau et du navigateur. Voir [Imagerie numérique](imaging-faq.md) pour plus d’informations.

Vous pouvez appliquer un paramètre d’image prédéfini à une image lorsque vous la prévisualisez.

**Pour appliquer des paramètres d’image prédéfinis Dynamic Media**:

1. Ouvrez la ressource et, dans le rail de gauche, sélectionnez dans le menu déroulant l’option **[!UICONTROL Rendus]**.

   >[!NOTE]
   >
   >* Les rendus statiques apparaissent dans la moitié supérieure du volet. Les rendus dynamiques apparaissent dans la moitié inférieure. Avec les rendus dynamiques uniquement, vous pouvez utiliser l’URL pour afficher l’image. Le **[!UICONTROL URL]** n’apparaît que si vous sélectionnez un rendu dynamique. Le **[!UICONTROL RESS]** s’affiche uniquement si vous sélectionnez un paramètre d’image prédéfini réactif.
   >
   >* Le système affiche plusieurs rendus lorsque vous sélectionnez **[!UICONTROL Rendus]** dans l’affichage des détails d’une ressource. Vous pouvez augmenter le nombre de paramètres prédéfinis visibles. Voir [Augmentation du nombre de paramètres d’image prédéfinis affichés](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display).


   ![chlimage_1-208](assets/chlimage_1-208.png)

1. Procédez de l’une des manières suivantes :

   * Sélectionnez un rendu dynamique pour prévisualiser le paramètre d’image prédéfini.
   * Appuyez sur **[!UICONTROL URL]**, **[!UICONTROL Incorporer]** ou **[!UICONTROL RESS]** pour afficher la fenêtre contextuelle.

   >[!NOTE]
   >
   >Si la ressource *et* le paramètre d’image prédéfini ne sont pas encore publiés, le bouton **[!UICONTROL URL]** (ou les boutons **[!UICONTROL URL]** et **[!UICONTROL RESS]**, le cas échéant) n’est pas disponible.
   >
   >Notez également que les paramètres prédéfinis de l’image sont automatiquement publiés sur un serveur Dynamic Media 
