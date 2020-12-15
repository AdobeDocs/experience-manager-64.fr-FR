---
title: Formats de fichier pris en charge dans AEM Assets
description: Liste des formats de fichier et des types MIME pris en charge par AEM Assets et des fonctionnalités prises en charge pour chaque format.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 2baa172088f646752e85168d432d46942ac8244e
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 62%

---


# Formats de fichiers pris en charge en AEM Assets {#assets-supported-formats}

AEM Assets prend en charge un large éventail de formats de fichier. Chaque fonctionnalité prend en charge différents types MIME.

Pour intégrer AEM Assets à d’autres solutions de gestion des actifs numériques (DAM) et logiciels de bureau conformes aux normes, utilisez la plateforme XMP (Extensible Metadata Platform) d’Adobe.

Reportez-vous à la légende pour comprendre le niveau de prise en charge.

| Niveau de prise en charge | Description |
|:---:|---|
| ✓ | Pris en charge |
| * | Prise en charge avec des fonctionnalités de composant additionnel |
| - | Non applicable |

## Formats d’image pixellisée {#supported-raster-image-formats}

Les formats d’image pixellisée pris en charge pour les fonctionnalités de gestion des ressources sont les suivants :

| Format | Stockage | Gestion des métadonnées | Extraction de métadonnées | Génération de miniatures | Modification interactive | Écriture différée des métadonnées | Statistiques |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | obj | obj | obj | obj | obj | obj | obj |
| GIF | obj | obj | obj | obj | obj |  | obj |
| TIFF | obj | obj | obj | obj |  | obj | obj |
| JPEG | obj | obj | obj | obj | obj | obj | obj |
| BMP | obj | obj | obj | obj | obj |  | obj |
| PNM | obj | obj |  |  |  |  | obj |
| PGM | obj | obj |  |  |  |  | obj |
| PBM | obj | obj |  |  |  |  | obj |
| PPM | obj | obj |  |  |  |  | obj |
| PSD **‡** | obj | obj | obj | obj |  |  | obj |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | obj | obj | obj | obj |  | obj |  |
| PICT |  |  |  |  |  |  | obj |
| PSB | obj | obj | obj | obj |  |  |  |

**‡** L’image fusionnée est extraite du fichier PSD. Il s’agit d’une image générée par Adobe Photoshop et incluse dans le fichier PSD. Selon les paramètres, l’image fusionnée peut constituer ou non l’image réelle.

Les formats d’image pixellisée pris en charge pour les fonctionnalités Dynamic Media sont les suivants :

| Format | Télécharger <br> (format d’entrée) | Créer <br> image<br> paramètre prédéfini<br> (format de sortie) | Prévisualisation<br> rendu dynamique<br> | Générer un rendu <br> dynamique<br> | Télécharger le rendu<br> dynamique<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | obj | obj | obj | obj | obj |
| GIF | obj | obj | obj | obj | obj |
| TIFF | obj | obj | obj | obj | obj |
| JPEG | obj | obj | obj | obj | obj |
| BMP | obj |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **†** | obj |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | obj | obj | obj | obj | obj |
| PICT | obj |  |  |  |  |
| PSB |  |  |  |  |  |

**‡** L’image fusionnée est extraite du fichier PSD. Il s’agit d’une image générée par Adobe Photoshop et incluse dans le fichier PSD. Selon les paramètres, l’image fusionnée peut constituer ou non l’image réelle.

Outre les informations ci-dessus, tenez compte des points suivants :

* La prise en charge des fichiers EPS s’applique uniquement aux images pixellisées. Par exemple, la génération de vignettes pour les images vectorielles EPS n’est pas prise en charge par défaut. Pour ajouter une prise en charge, [configurez ImageMagick](best-practices-for-imagemagick.md). Pour intégrer des outils tiers permettant d’activer des fonctionnalités supplémentaires, voir [Gestionnaire de médias basé sur la ligne de commande](media-handlers.md#command-line-based-media-handler).

* L’écriture différée des métadonnées fonctionne pour le format de fichier PSB lorsqu’elle est ajoutée au gestionnaire `NComm`.

* Pour utiliser Dynamic Media pour prévisualiser et générer des rendus dynamiques pour les fichiers EPS, voir [Adobe Illustrator (AI), Postscript (EPS) et les formats de fichier PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Concernant les fichiers EPS, l’écriture différée des métadonnées est prise en charge dans PostScript Document Structuring Convention (PS-Adobe) version 3.0 ou supérieure.

## Formats d’image pixellisée non pris en charge dans Dynamic Media {#unsupported-image-formats-dynamic-media}

La liste suivante décrit les sous-types de formats de fichier image pixellisée *non* pris en charge dans Dynamic Media.

Voir aussi [Détecter les formats de fichier non pris en charge pour Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* Fichiers PNG dont la taille de bloc IDAT est supérieure à 100 Mo.
* Fichiers PSB.
* Les fichiers PSD avec un espace colorimétrique autre que CMJN, RVB, niveaux de gris ou bitmap ne sont pas pris en charge. Les espaces colorimétriques DuoTone, Lab et indexé ne sont pas pris en charge.
* Fichiers PSD ayant une résolution binaire supérieure à 16.
* Fichiers TIFF contenant des données à virgule flottante.
* Fichiers TIFF dotés d’un espace colorimétrique Lab.

## Bibliothèque PDF Rasterizer {#supported-pdf-rasterizer-library}

La bibliothèque Adobe PDF Rasterizer génère des miniatures de haute qualité et des aperçus pour les fichiers Adobe Illustrator et PDF de grande taille et riches en contenu. Adobe recommande d’utiliser la bibliothèque PDF Rasterizer pour ce qui suit :

* Fichiers AI/PDF à forte intensité de contenu qui nécessitent beaucoup de ressources pour être traités.
* Fichiers AI/PDF pour lesquels les miniatures ne sont pas générées par défaut.
* Fichiers AI contenant des couleurs PMS (Pantone Matching System).

Voir [Utilisation de PDF Rasterizer](aem-pdf-rasterizer.md).

## Bibliothèque de transcodage d’imagerie (ITL){#supported-image-transcoding-library}

La bibliothèque de transcodage d’images d’Adobe est une solution de traitement d’images qui exécute des fonctions essentielles de gestion d’images, telles que le codage, le transcodage, le rééchantillonnage et le redimensionnement.

La bibliothèque de transcodage d’images prend en charge les formats JPG/JPEG, PNG (8 et 16 bits), GIF, BMP, TIFF/Compressed TIFF (à l’exception des fichiers TIFF 32 bits et PTIFF), ICO et ICN MIME.

Voir [Bibliothèque de transcodage d’images](imaging-transcoding-library.md).

## Camera Raw {#supported-camera-raw}

La bibliothèque Adobe Camera Raw permet à AEM Assets d’importer des images brutes. Voir [Support Camera Raw](camera-raw.md).

## Formats de document {#supported-document-formats}

Les formats de documents pris en charge pour les fonctionnalités de gestion des ressources sont les suivants:

| Format | Stockage | Gestion des métadonnées<br> | Extraction de texte complet <br> | Extraction des métadonnées<br> | Génération de miniature<br> | Extraction de sous-ressources<br> | Remise en écriture des métadonnées<br> |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | obj | obj |  | obj | obj | obj | obj |
| DOC | obj | obj | obj | obj |  |  |  |
| DOCX | obj | obj | obj | obj |  |  |  |
| ODT | obj | obj | obj |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | obj | obj | obj | obj | obj | obj | obj |
| HTML | obj | obj | obj |  |  |  |  |
| RTF | obj | obj | obj |  |  |  |  |
| TXT | obj | obj | obj |  |  |  |  |
| XLS | obj | obj | obj |  |  |  |  |
| XLSX | obj | obj | obj | obj |  |  |  |
| ODS | obj | obj | obj |  |  |  |  |
| PPT | obj | obj | obj | obj | obj | obj |  |
| PPTX | obj | obj | obj | obj | obj | obj |  |
| ODP | obj | obj | obj |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | obj | obj |  | obj | obj | obj | obj |
| PS | obj | obj |  |  |  |  |  |
| QXP | obj | obj |  |  |  |  |  |
| EPUB | obj | obj |  | obj | obj |  |  |

Les formats de document pris en charge pour les fonctionnalités Dynamic Media sont les suivants :

| Format | Télécharger <br> (format d’entrée) | Créer <br> image<br> paramètre prédéfini<br> (format de sortie) | Prévisualisation<br> rendu dynamique<br> | Générer un rendu <br> dynamique<br> | Télécharger le rendu<br> dynamique<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | obj |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | obj | obj | obj | obj | obj |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | obj |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

Outre les fonctionnalités ci-dessus, tenez compte des points suivants :

* Pour utiliser Dynamic Media de sorte à générer des rendus dynamiques pour des fichiers PDF, voir [ Adobe Illustrator (AI), Postscript (EPS) et formats de fichier PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Pour utiliser Dynamic Media de sorte à prévisualiser et générer des rendus dynamiques pour des fichiers AI, voir [Adobe Illustrator (AI), Postscript (EPS) et les formats de fichier PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Pour utiliser Dynamic Media pour générer des rendus dynamiques pour les fichiers INDD, voir [format de fichier d&#39;InDesign (INDD)](../assets/managing-image-presets.md#indesign-indd-file-format).

## Formats multimédias {#supported-multimedia-formats}

| Format | Stockage | Gestion des métadonnées | Extraction de métadonnées | Génération de miniatures | Transcodage FFMPEG |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | obj | obj |  | - | * |
| MIDI | obj | obj |  | - | * |
| 3GP | obj | obj |  | - | * |
| MP3 | obj | obj | obj | - | * |
| MPG | obj | obj |  | - | * |
| OGA | obj | obj |  | - | * |
| OGG | obj | obj |  | - | * |
| RA | obj | obj |  | - | * |
| WAV | obj | obj |  | - | * |
| WMA | obj | obj |  | - | * |
| DVI | obj | obj |  | * | * |
| FLV | obj | obj |  | * | * |
| M4V | obj | obj |  | * | * |
| MPEG | obj | obj |  | * | * |
| OGV | obj | obj |  | * | * |
| MOV | obj | obj |  | * | * |
| WMV | obj | obj |  | * | * |
| SWF | obj | obj |  |  |  |

## Formats vidéo d’entrée pour le transcodage Dynamic Media {#supported-input-video-formats-for-dynamic-media-transcoding}

| Extension de fichier vidéo | Conteneur | Codecs vidéo recommandés | Codecs vidéo non pris en charge |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (tous les profils) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 et HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (fichiers d’animation vectorielle) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Red Raw Video | MJPEG 2000 |  |
| RAM, RM | RealVideo | Non pris en charge | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Native Flac | FLAC (Free Lossless Audio Codec) |  |
| MJ2 | Motion JPEG 2000 | Codec Motion JPEG 2000 |  |

## Formats d’archivage {#supported-archive-formats}

Les formats d’archives pris en charge et l’applicabilité des flux de travail DAM courants sont traités dans le tableau suivant.

| Format | Stockage | Contrôle de version | Workflow | Publication | Contrôle d’accès | Livraison Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | obj | obj | obj | obj | obj |  |
| JAR | obj | obj | obj | obj | obj |  |
| RAR | obj | obj | obj | obj | obj |  |
| TAR | obj | obj | obj | obj | obj |  |
| ZIP **†** | obj | obj | obj | obj | obj | obj |

**†** L’image fusionnée est extraite du fichier PSD. Il s’agit d’une image générée par Adobe Photoshop et incluse dans le fichier PSD. Selon les paramètres, l’image fusionnée peut constituer ou non l’image réelle. `Deflate64`Les archives ZIP créées à l’aide de l’algorithme sont prises en charge de manière limitée dans AEM. Les opérations d’archivage et de désarchivage ne sont pas prises en charge. Cependant, les opérations comme le chargement, la consultation et le téléchargement sont prises en charge.

## Autres formats pris en charge  {#other-supported-formats}

Le tableau ci-dessous décrit l’applicabilité des processus de gestion des actifs numériques courants pour d’autres formats de fichier.

| Format | Stockage | Contrôle de version | Workflow | Publication | Contrôle d’accès | Livraison Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | obj | obj | obj | obj | obj |  |
| SVG | obj | obj | obj | obj | obj |  |
| CSS | obj | obj | obj | obj | obj | obj |
| VTT | obj | obj | obj | obj | obj | obj |
| XML | obj | obj | obj | obj | obj | obj |
| JavaScript (lorsque configuré avec son propre domaine de diffusion) |  |  |  |  |  | obj |

**#** Les autres formats sont pris en charge dans DAM pour la gestion des enregistrements, des versions, des listes de contrôle d’accès, des flux de travail, de la publication et des métadonnées.

## Types MIME pris en charge {#supported-mime-types}

Par défaut, AEM détecte le type de fichier à l’aide de l’extension de fichier. aem peut le détecter à partir du contenu des fichiers. Pour plus de détails, sélectionnez [!UICONTROL Détecter MIME à partir de l&#39;option content] dans [!UICONTROL Service de type MIME DAM DAM Day CQ] dans la console Web AEM.

Une liste de types MIME pris en charge est disponible en CRXDE Lite à l&#39;adresse `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

| Extension de fichier | Type MIME/type de support Internet | Valeur de jobParam par défaut | Valeur de jobParam autorisée |
|---|---|---|---|
| Image | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | La valeur de jobParam par défaut s’applique à toutes les ressources de type image MIME.<ul><li>[knockoutBackgroundOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>application/eps</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | vidéo/mpeg |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | vidéo/mpeg |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-chokwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF / TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExclureMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Activation de la prise en charge du paramètre de tâche de téléchargement Assets/Scene7 basé sur le type MIME](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).
>* [Configurez le type MIME en fonction de la prise en charge](config-dynamic.md) des paramètres de tâche de téléchargement.

