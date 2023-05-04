---
title: Bonnes pratiques relatives au format de fichier des ressources
description: Bonnes pratiques relatives à la prise en charge des fichiers dans [!DNL Experience Manager] Ressources.
contentOwner: AG
feature: Asset Management,Developer Tools
role: Admin
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 19%

---

# Bonnes pratiques relatives au format de fichier des ressources {#assets-file-format-best-practices}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

[!DNL Experience Manager Assets] prend en charge de nombreuses bibliothèques de formats de fichiers propriétaires et tierces pour gérer les divers besoins des utilisateurs en matière de prise en charge des fichiers. Les bibliothèques d’Adobe prises en charge sont Adobe Camera Raw, Gibson, Adobe PDF Rasterizer et Adobe InDesign Server. En outre, [!DNL Assets] prend en charge les bibliothèques tierces, notamment ImageMagick, TwelveMonkeys, etc.

Pour les formats de fichiers pris en charge, consultez [Formats pris en charge par AEM Assets](assets-formats.md).

## Bibliothèque Adobe Camera Raw {#adobe-camera-raw-library}

Pour des performances optimales, Adobe recommande d’utiliser la bibliothèque Adobe Camera Raw pour :

* RAW
* DNG

La bibliothèque Adobe Camera Raw prend en charge le profil colorimétrique CMJN en tant qu’entrée. Cependant, il génère la sortie dans l’espace colorimétrique RGB et ne prend en charge que la sortie au format JPEG. Il ne conserve pas l’espace colorimétrique du fichier source (CMJN, par exemple) dans les miniatures.

Pour plus d’informations, voir [Prise en charge Camera Raw](camera-raw.md) in [!DNL Assets].

## Bibliothèque Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Pour de meilleurs résultats, Adobe recommande d’utiliser la bibliothèque Adobe PDF Rasterizer pour les fichiers suivants :

* Fichiers de PDF lourds et gourmands en contenu
* Fichiers AI avec des miniatures non générées prêtes à l’emploi
* Pour les fichiers AI avec des couleurs SPOT (PMS)

Les miniatures et les aperçus générés à l’aide de PDF Rasterizer sont de meilleure qualité par rapport à la sortie de pixellisation prête à l’emploi. La bibliothèque Adobe PDF Rasterizer ne prend en charge aucune conversion d’espace colorimétrique. Quel que soit l’espace colorimétrique du fichier du PDF source, Adobe PDF Rasterizer génère une sortie de RGB uniquement.

## Serveur Adobe InDesign {#adobe-indesign-cc-server}

Adobe vous recommande d’utiliser le serveur Adobe InDesign pour extraire des rendus spécifiques à Adobe InDesign, tels que IDML et HTML. Pour plus d’informations, consultez [ [!DNL Experience Manager] Ajout de ressources comme références dans Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media génère et diffuse en temps réel plusieurs variantes d’un même contenu enrichi par le biais de son réseau mondial, évolutif et aux performances optimisées. Il diffuse des expériences d’affichage interactif et simplifie le processus de gestion des campagnes numériques. Pour plus d’informations sur l’activation de Dynamic Media, voir [Configuration de Dynamic Media](config-dynamic.md).

Actuellement, Dynamic Media peut prendre en charge les vidéos jusqu’à 15 Go de contenu par fichier.

## Bibliothèque ImageMagick {#imagemagick-library}

Adobe recommande d’utiliser la bibliothèque ImageMagick dans les scénarios suivants :

* Pour générer des rendus de miniature pour les fichiers EPS
* Pour préserver les informations de profil d’image
* Pour préserver la transparence
* Traitement des fichiers PSD et PSB

Pour savoir comment configurer la bibliothèque ImageMagic dans [!DNL Experience Manager], voir [Utilisation d’ImageMagick](media-handlers.md#an-example-using-imagemagick). Pour une utilisation optimale, voir [Bonnes pratiques pour la configuration d’ImageMagick](best-practices-for-imagemagick.md).

## Bibliothèque de transcodage d’image {#image-transcoding-library}

La bibliothèque ITL est une solution de traitement des images qui exécute des fonctions essentielles de gestion des images, notamment le codage, le transcodage, le rééchantillonnage, le redimensionnement des images, etc.

La bibliothèque ITL prend en charge les types MIME suivants :

* JPG/JPEG
* PNG (8 bits et 16 bits)
* GIF
* BMP
* TIFF/TIFF compressé (hormis pour les images Tiff et PTiff 32 bits)
* ICO
* ICN

Pour plus d’informations, consultez [Bibliothèque de transcodage d’imagerie](imaging-transcoding-library.md).
