---
title: Images panoramiques
description: Découvrez comment utiliser les images panoramiques dans Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Images panoramiques
role: Business Practitioner
source-git-commit: 489a4b42bdd5895186ba885b9a1dc33b49427e8d
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 46%

---

# Images panoramiques {#panoramic-images}

Cette section décrit comment utiliser la visionneuse d’images panoramiques pour le rendu d’images panoramiques sphériques afin de profiter d’une expérience de visionnage immersive à 360° d’une pièce, d’une propriété, d’un lieu ou d’un paysage.

Voir également [Gestion des paramètres prédéfinis de visionneuse](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Téléchargement de ressources pour une utilisation avec la visionneuse d’images panoramiques {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Pour qu’une ressource téléchargée soit une image panoramique sphérique utilisable avec la visionneuse d’images panoramiques, la ressource doit présenter l’une ou l’autre des caractéristiques suivantes, ou les deux :

* Un rapport d’aspect de 2.

   Vous pouvez remplacer le paramètre de format par défaut de 2 dans **[!UICONTROL CRXDE Lite]** à l’adresse suivante :

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Avec les mots-clés `equirectangular`, ou `spherical` et `panorama`, ou `spherical` et `panoramic`. Voir [Utilisation des balises](/help/sites-authoring/tags.md).

Les critères de rapport d’aspect et de mots-clés s’appliquent tous deux aux ressources panoramiques pour la page des détails des ressources et le composant  **[!UICONTROL Média panoramique]**.

Pour télécharger des ressources à utiliser avec la visionneuse d’images panoramiques, consultez [Téléchargement de ressources](managing-assets-touch-ui.md#uploading-assets).

## Configuration de Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Pour que la visionneuse d’images panoramiques fonctionne correctement dans AEM, vous devez synchroniser les paramètres prédéfinis de la visionneuse d’images panoramiques avec les métadonnées spécifiques à Dynamic Media Classic et Dynamic Media Classic afin que les paramètres prédéfinis de la visionneuse soient mis à jour dans JCR. Pour ce faire, configurez Dynamic Media Classic de la manière suivante :

1. [Connectez-vous à votre ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) application de bureau Dynamic Media Classic pour chaque compte d’entreprise.

1. Près du coin supérieur droit de la page, cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Configuration de la publication > Serveur d’images]**.
1. Sur la page **[!UICONTROL Publication sur serveur d’images]**, dans le menu déroulant **[!UICONTROL Contexte de publication]** près du haut, sélectionnez **[!UICONTROL Image Serving]**.

1. Sur la même page **[!UICONTROL Publication sur serveur d’images]**, recherchez l’en-tête **[!UICONTROL Attributs de requête]**.
1. Sous l’en-tête **[!UICONTROL Attributs de requête]** , recherchez **[!UICONTROL Limite de taille de l’image de réponse]**. Ensuite, dans les champs **[!UICONTROL Largeur]** et **[!UICONTROL Hauteur]** associés, augmentez la taille maximale autorisée pour les images panoramiques.

   Dynamic Media Classic est limitée à 25 000 000 pixels. La taille maximale autorisée pour les images avec un rapport d’aspect de 2:1 est de 7 000 x 3 500. Toutefois, pour des écrans d’ordinateurs de bureau habituels, une taille de 4 096 x 2 048 pixels suffit.

   >[!NOTE]
   >
   >Seules les images qui respectent la taille d’image maximale autorisée sont prises en charge. Les demandes d’images qui dépassent la taille maximale entraînent une réponse 403.

1. Sous l’en-tête **[Attributs de requête]** , procédez comme suit :

   * Définissez **[!UICONTROL Mode d’obscurcissement de requête]** sur **[!UICONTROL Désactivé]**.
   * Définissez **[!UICONTROL Mode de verrouillage de requête]** sur **[!UICONTROL Désactivé]**.

   Ces paramètres sont nécessaires pour utiliser le composant **[!UICONTROL Média panoramique]** dans AEM.

1. Au bas de la page **[!UICONTROL Publication du serveur d’images]**, sur le côté gauche, appuyez sur **[!UICONTROL Enregistrer]**.

1. Dans le coin inférieur droit, appuyez sur **[!UICONTROL Fermer]**.

### Dépannage du composant Média panoramique {#troubleshooting-the-panoramic-media-wcm-component}

Si vous avez déposé une image dans le composant **[!UICONTROL Média panoramique]** de votre WCM et que l’espace réservé du composant est réduit, vous pouvez résoudre les problèmes suivants :

* Si vous rencontrez une erreur 403 Interdit, elle peut être due à la taille excessive de l’image demandée. Vérifiez les paramètres *Limite de taille de l’image de réponse* dans [Configuration de Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* Pour un *verrou non valide* sur la ressource ou *Erreur d’analyse* affichée sur la page, cochez **[!UICONTROL Mode d’obscurcissement de requête]** et **[!UICONTROL Mode de verrouillage de requête]** pour vous assurer qu’ils sont désactivés.
* Pour une erreur de canevas taché, configurez un **[!UICONTROL chemin d’accès au fichier de définition de l’ensemble de règles et invalidez CTN]** pour les requêtes précédentes de la ressource image.
* Si la qualité d’image devient très faible après une demande d’image dont la taille dépasse la limite prise en charge, vérifiez que le paramètre **[!UICONTROL Attributs d’encodage JPEG > Qualité]** n’est pas vide. Un paramètre type pour le champ **[!UICONTROL Qualité]** est `95`. Vous pouvez trouver le paramètre sur la page **[!UICONTROL Publication du serveur d’images]**. Pour accéder à la page, voir [Configuration de Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Aperçu des images panoramiques {#previewing-panoramic-images}

Voir [Aperçu des ressources](previewing-assets.md).

## Publication des images panoramiques {#publishing-panoramic-images}

Voir [Publication de ressources](publishing-dynamicmedia-assets.md).
