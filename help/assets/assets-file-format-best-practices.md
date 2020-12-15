---
title: Meilleures pratiques relatives au format de fichier des ressources
description: Meilleures pratiques relatives à la prise en charge des fichiers dans AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a892ef7ab018aca715693125808d7ade540c8242
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 92%

---


# Meilleures pratiques relatives au format de fichier des ressources  {#assets-file-format-best-practices}

AEM Assets prend en charge de nombreuses bibliothèques de formats de fichiers propriétaires et tierces pour gérer les divers besoins des utilisateurs en matière de prise en charge des fichiers. Les bibliothèques Adobe prises en charge comprennent Adobe Camera Raw, Gibson, Adobe PDF Rasterizer et Adobe InDesign Server. En outre, AEM Assets prend en charge les bibliothèques tierces, y compris ImageMagick, TwelveMonkeys, etc.

Pour les formats de fichiers pris en charge, voir [Formats pris en charge par AEM Assets](assets-formats.md).

## Bibliothèque Adobe Camera Raw  {#adobe-camera-raw-library}

Pour des performances optimales, Adobe recommande d’utiliser la bibliothèque Adobe Camera Raw pour :

* RAW
* DNG

La bibliothèque Adobe Camera Raw prend en charge le profil de couleurs CMJN en entrée. Cependant, elle génère la sortie dans l’espace colorimétrique RVB et ne la prend en charge qu’au format JPEG. Elle ne conserve pas l’espace colorimétrique du fichier source (CMJN, par exemple) dans les miniatures.

Pour plus d’informations, voir [Prise en charge de Camera Raw](camera-raw.md) dans AEM Assets.

## Bibliothèque Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Pour des résultats optimaux, Adobe recommande d’utiliser la bibliothèque Adobe PDF Rasterizer pour les fichiers suivants :

* Fichiers PDF lourds ayant un contenu dense
* Fichiers AI avec des miniatures qui ne sont pas générées à l’avance
* Pour les fichiers AI avec des couleurs SPOT (PMS)

Les miniatures et les aperçus générés à l’aide de l’interpréteur de PDF sont de qualité supérieure par rapport à la sortie de trame prête à l’emploi. La bibliothèque PDF Rasterizer d’Adobe ne prend en charge aucune conversion d’espace colorimétrique. Quel que soit l’espace colorimétrique du fichier PDF source, l’interpréteur de PDF Adobe génère la sortie RVB uniquement.

## Serveur Adobe InDesign  {#adobe-indesign-cc-server}

Adobe vous recommande d’utiliser le serveur Adobe InDesign pour extraire des rendus spécifiques à Adobe InDesign, tels que IDML et HTML. Pour plus d’informations, voir [Ajouter des ressources AEM en tant que références dans Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media génère et diffuse plusieurs variations de contenu riche en temps réel via son réseau mondial, extensible et optimisé pour garantir de bonnes performances. Il diffuse des expériences d’affichage interactif et simplifie le processus de gestion des campagnes numériques. Pour en savoir plus sur l’activation de Dynamic Media, voir [Configuration de Dynamic Media](config-dynamic.md).

Actuellement, Dynamic Media peut prendre en charge jusqu’à 15 Go de contenu vidéo par fichier.

## Bibliothèque ImageMagick {#imagemagick-library}

Adobe recommande d’utiliser la bibliothèque ImageMagick dans les cas suivants :

* Pour générer des rendus de miniatures pour les fichiers EPS
* Pour conserver les informations sur les profils d’image
* Pour conserver la transparence
* Pour traiter des fichiers PSD et PSB

Pour savoir comment configurer la bibliothèque ImageMagic en AEM, voir [Utilisation d’ImageMagick](media-handlers.md#an-example-using-imagemagick). Pour une utilisation optimale, voir [Bonnes pratiques pour configurer ImageMagick](best-practices-for-imagemagick.md).

## Bibliothèque de transcodage d’imagerie (ITL)  {#image-transcoding-library}

La bibliothèque Adobe Imaging Transcoding Library est une solution de traitement des images qui exécute des fonctions essentielles de manipulation graphique, y compris le codage, le transcodage, le rééchantillonnage, le redimensionnement des images, etc.

La bibliothèque de transcodage d’imagerie (ITL) prend en charge les types MIME suivants :

* JPG/JPEG
* PNG (8 et 16 bits)
* GIF
* BMP
* TIFF/TIFF compressé (hormis pour les images Tiff et PTiff 32 bits).
* ICO
* ICN

Pour plus d’informations, voir [Bibliothèque de transcodage d’images](imaging-transcoding-library.md).
