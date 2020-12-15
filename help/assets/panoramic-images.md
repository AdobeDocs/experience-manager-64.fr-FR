---
title: Images panoramiques
seo-title: Images panoramiques
description: Découvrez comment utiliser les images panoramiques dans Dynamic Media.
seo-description: Découvrez comment utiliser les images panoramiques dans Dynamic Media.
uuid: dfd7a55c-7bcc-4d62-8c3a-a73726881103
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: fc285b25-2bce-493c-87bc-5f1a8a26eb42
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 48%

---


# Images panoramiques {#panoramic-images}

Cette section décrit comment utiliser la visionneuse d’images panoramiques pour le rendu d’images panoramiques sphériques afin de profiter d’une expérience de visionnage immersive à 360° d’une pièce, d’une propriété, d’un lieu ou d’un paysage.

Voir également [Gestion des paramètres prédéfinis de visionneuse](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Téléchargement de ressources pour une utilisation avec la visionneuse d’images panoramiques {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Pour qu’une ressource téléchargée soit une image panoramique sphérique utilisable avec la visionneuse d’images panoramiques, la ressource doit présenter l’une ou l’autre des caractéristiques suivantes, ou les deux :

* Un rapport d’aspect de 2.

   Vous pouvez remplacer le paramètre de format par défaut de 2 dans **[!UICONTROL CRXDE Lite]** par le paramètre suivant :

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Avec les mots-clés `equirectangular`, ou `spherical` et `panorama`, ou `spherical` et `panoramic`. Voir [Utilisation des balises](/help/sites-authoring/tags.md).

Les critères de rapport d’aspect et de mots-clés s’appliquent tous deux aux ressources panoramiques pour la page des détails des ressources et le composant  **[!UICONTROL Média panoramique]**.

Pour télécharger des ressources à utiliser avec la visionneuse d’images panoramiques, consultez [Téléchargement de ressources](managing-assets-touch-ui.md#uploading-assets).

## Configuration de Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Pour que la visionneuse d’images panoramiques fonctionne correctement dans AEM, vous devez synchroniser les paramètres prédéfinis de la visionneuse d’images panoramiques avec les métadonnées spécifiques à Dynamic Media Classic et Dynamic Media Classic afin que les paramètres prédéfinis de la visionneuse soient mis à jour dans le JCR. Pour ce faire, configurez Dynamic Media Classic de la manière suivante :

1. [Connectez-vous à votre instance de Dynamic Media ](https://www.adobe.com/fr/marketing-cloud/experience-manager/scene7-login.html) Classicic pour chaque compte de société.

1. Près du coin supérieur droit de la page, cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Configuration de la publication > Serveur d’images]**.
1. Sur la page **[!UICONTROL Publication sur hébergeur d’images]**, dans le menu déroulant **[!UICONTROL Contexte de publication]** situé en haut, sélectionnez **[!UICONTROL Diffusion d’images]**.

1. Sur la même page **[!UICONTROL Publication sur hébergeur d’images]**, recherchez l’en-tête **[!UICONTROL Attributs de demande]**.
1. Sous l’en-tête **[!UICONTROL Request Attributes]**, recherchez **[!UICONTROL Reply Image Size Limit]**. Ensuite, dans les champs **[!UICONTROL Largeur]** et **[!UICONTROL Hauteur]** associés, augmentez la taille d’image maximale autorisée pour les images panoramiques.

   Dynamic Media Classic est limité à 25 000 000 pixels. La taille maximale autorisée pour les images de rapport 2:1 est de 7 000 x 3 500. Toutefois, pour des écrans d’ordinateurs de bureau habituels, une taille de 4 096 x 2 048 pixels suffit.

   >[!NOTE]
   >
   >Seules les images qui respectent la taille d’image maximale autorisée sont prises en charge. Les demandes d’images qui dépassent la taille maximale entraînent une réponse 403.

1. Sous l’en-tête **[Request Attributes]**, procédez comme suit :

   * Définissez **[!UICONTROL Mode d’obscurcissement de la demande]** sur **[!UICONTROL Désactivé]**.
   * Définissez **[!UICONTROL Mode de verrouillage de la demande]** sur **[!UICONTROL Désactivé]**.

   Ces paramètres sont nécessaires pour utiliser le composant **[!UICONTROL Média panoramique]** dans AEM.

1. Au bas de la page **[!UICONTROL Publication Image Server]**, sur le côté gauche, appuyez sur **[!UICONTROL Enregistrer]**.

1. Dans le coin inférieur droit, appuyez sur **[!UICONTROL Fermer]**.

### Dépannage du composant Média panoramique {#troubleshooting-the-panoramic-media-wcm-component}

Si vous avez déposé une image dans le composant **[!UICONTROL Média panoramique]** de votre WCM et que l’espace réservé du composant est réduit, vous pouvez résoudre les problèmes suivants :

* Si vous rencontrez une erreur 403 Interdit, elle peut être due à la taille excessive de l’image demandée. Vérifiez les paramètres *Limite de taille de l’image de réponse* dans [Configuration de Dynamic Media Classic (Scene7)](#configuring-dynamic-media-classic-scene).

* Pour un verrou *non valide* sur la ressource ou *erreur d’analyse* affichée sur la page, vérifiez **[!UICONTROL Mode d’obscurcissement de la demande]** et **[!UICONTROL Mode de verrouillage de la demande]** pour vous assurer qu’ils sont désactivés.
* Pour une erreur de canevas teinté, configurez un **[!UICONTROL chemin de fichier de définition de l’ensemble de règles et invalidez le CTN]** pour les requêtes précédentes pour le fichier d’image.
* Si la qualité d’image devient très faible après une demande d’image dont la taille dépasse la limite prise en charge, vérifiez que le paramètre **[!UICONTROL Attributs d’encodage JPEG > Qualité]** n’est pas vide. Un paramètre type du champ **[!UICONTROL Qualité]** est `95`. Vous pouvez trouver le paramètre sur la page **[!UICONTROL Publication sur hébergeur d’images]**. Pour accéder à la page, voir [Configuration de Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Aperçu des images panoramiques {#previewing-panoramic-images}

Voir aussi [Aperçu des ressources](previewing-assets.md).

## Publication des images panoramiques    {#publishing-panoramic-images}

Voir [Publication de ressources](publishing-dynamicmedia-assets.md).
