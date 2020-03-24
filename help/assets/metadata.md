---
title: Gestion des métadonnées de vos ressources numériques
description: Découvrez les types de métadonnées et comment les ressources Adobe Experience Manager permettent de gérer les métadonnées des ressources afin de faciliter la catégorisation et l’organisation des ressources. Avec la possibilité de conserver et de gérer des métadonnées arbitraires avec vos ressources, Adobe Experience Manager Assets permet d’organiser et de traiter automatiquement les ressources en fonction de leurs métadonnées.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5ef4c4e42165819191c6e3810c36183110f3f34a

---


# Gestion des métadonnées de vos ressources numériques {#managing-metadata-for-digital-assets}

Adobe Experience Manager Assets conserve les métadonnées de chaque ressource. Cela facilite la catégorisation et l&#39;organisation des ressources et aide les personnes qui recherchent un actif spécifique. Avec la possibilité d’extraire des métadonnées des fichiers téléchargés vers les ressources d’Experience Manager, la gestion des métadonnées s’intègre au processus de création. Grâce à la fonctionnalité Experience Manager permettant de conserver et de gérer les métadonnées de vos fichiers, vous pouvez organiser et traiter automatiquement les fichiers en fonction des métadonnées.

* [Métadonnées XMP](xmp.md)
* [Comment modifier ou ajouter des métadonnées](meta-edit.md)
* [Référence des schémas de métadonnées](meta-ref.md)

## Pourquoi les métadonnées sont nécessaires {#why-we-need-metadata}

Les métadonnées désignent les données relatives aux données. À cet égard, les données font référence à votre actif numérique, par exemple une image. Les métadonnées sont essentielles pour une gestion efficace des ressources.

Les métadonnées sont la collection de toutes les données disponibles pour un fichier, mais elles ne sont pas nécessairement contenues dans cette image. Voici quelques exemples de métadonnées :

* Nom du fichier.
* Heure et date de la dernière modification.
* Taille de la ressource telle qu’elle était stockée dans le référentiel.
* Nom du dossier dans lequel il se trouve.
* Ressources connexes ou balises appliquées.

Il s’agit des propriétés de métadonnées de base que Experience Manager peut gérer pour les ressources, ce qui permet aux utilisateurs de voir toutes les ressources, par exemple, classées par date de dernière modification, ce qui s’avère utile lorsque vous essayez de découvrir les ressources récemment ajoutées au référentiel.

Vous pouvez ajouter d’autres données de niveau supérieur à des ressources numériques, par exemple :

* Type de fichier (s’agit-il d’une image, d’une vidéo, d’un clip audio ou d’un  ?).
* Propriétaire de la ressource.
* Titre de la ressource.
* Description de la ressource.
* Balises affectées à un fichier.

Un plus grand nombre de métadonnées vous permet de classer davantage les fichiers et s’avère utile à mesure que la quantité d’informations numériques augmente. Il est possible de gérer quelques centaines de fichiers uniquement en fonction des noms de fichier. Toutefois, cette approche n’est pas évolutive et ne fonctionne pas rapidement lorsque le nombre de personnes impliquées et le nombre d’actifs gérés augmentent.

Lorsque des métadonnées sont ajoutées à des fichiers, la valeur de l’élément augmente, car l’élément devient :

* plus accessible - les gens peuvent le trouver beaucoup plus facile.
* plus facile à gérer : vous pouvez trouver plus facilement des ressources avec le même jeu de propriétés et leur appliquer des modifications.
* plus complexe : plus vous ajoutez de métadonnées à un fichier, plus la gestion des métadonnées devient importante.

Pour ces raisons, Experience Manager Assets vous offre les moyens adéquats de créer, de gérer et d’échanger des métadonnées pour vos ressources numériques.

## Types de métadonnées {#types-of-metadata}

Les deux types de métadonnées de base sont les métadonnées techniques et les métadonnées descriptives.

Les métadonnées techniques sont utiles pour les applications logicielles qui traitent de ressources numériques et ne doivent pas être gérées manuellement. Experience Manager Assets et d’autres logiciels déterminent automatiquement les métadonnées techniques et les métadonnées peuvent changer lorsque la ressource est modifiée. Les métadonnées techniques disponibles d’un fichier dépendent largement du type de fichier du fichier. Voici quelques exemples de métadonnées techniques :

* Taille d’un fichier
* Dimensions (hauteur et largeur) d’une image
* Débit d’un fichier audio ou vidéo
* Résolution (niveau de détail) d’une image

Les métadonnées descriptives sont des métadonnées qui concernent le domaine d’application, par exemple l’entreprise d’où provient un fichier. Les métadonnées descriptives ne peuvent pas être déterminées automatiquement. Elle est créée manuellement ou semi-automatiquement. Par exemple, une caméra GPS peut automatiquement suivre la latitude et la longitude et ajouter une balise géographique à l’image.

En raison du coût élevé de la création manuelle des informations de métadonnées descriptives, des normes ont été définies pour faciliter l’échange des métadonnées entre les systèmes logiciels et les structures.

Experience Manager Assets prend en charge toutes les normes pertinentes pour la gestion des métadonnées.

En raison de l’importance des métadonnées et de l’implication pour créer des métadonnées, des normes ont été définies pour en faciliter l’échange.

## Encoding standards {#encoding-standards}

Il existe différentes manières d’incorporer des métadonnées dans des fichiers. Certaines normes de codage sont prises en charge :

* XMP : utilisé par Experience Manager Assets pour stocker les métadonnées extraites dans le référentiel.
* ID3 : pour les fichiers audio et vidéo
* Exif : pour les fichiers image.
* Autre/Hérité : à partir de Microsoft Word, PowerPoint, Excel, etc.

### XMP {#xmp}

XMP (Extensible Metadata Platform) est une norme ouverte utilisée par les ressources d’Experience Manager pour la gestion de toutes les métadonnées. Le standard  le codage de métadonnées universel qui peut être incorporé dans tous les formats de fichier. Adobe et d’autres  prennent en charge la norme XMP car elle fournit un modèle de contenu enrichi. Les utilisateurs de XMP standard et d’Experience Manager Assets disposent d’une plateforme puissante sur laquelle s’appuyer. Pour plus d’informations, voir [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

Les données stockées dans ces balises ID3 s’affichent lors de la lecture d’un fichier audio numérique sur un ordinateur ou un lecteur MP3 portable.

Les balises ID3 sont destinées au format de fichier MP3. Informations supplémentaires sur les formats :

* Les balises ID3 fonctionnent dans les fichiers MP3 et mp3PRO.
* Le format WAV ne comprend pas de balises.
* WMA possède des balises propriétaires qui n’autorisent pas l’implémentation open-source.
* Le format Ogg Vorbis utilise des commentaires Xiph incorporés dans le conteneur Ogg.
* Le format AAC utilise un format de balisage propriétaire.

### Exif {#exif}

Le format de fichier d’image échangeable (Exif) est le format de métadonnées le plus utilisé dans la photographie numérique. Il permet d’incorporer un vocabulaire fixe des propriétés de métadonnées dans de nombreux formats de fichier, tels que JPEG, TIFF, RIFF et WAV. Exif stocke les métadonnées sous forme de paires d’un nom de métadonnées et d’une valeur de métadonnées. Ces paires nom-valeur-métadonnées sont également appelées balises, à ne pas confondre avec le balisage dans Experience Manager. Comme Exif est automatiquement créé par les appareils photo numériques modernes et pris en charge par les logiciels graphiques modernes, il peut être considéré comme le plus petit dénominateur commun pour la gestion des métadonnées.

Une des principales limites d’Exif est que quelques formats de fichier d’image courants, tels que BMP, GIF ou PNG, ne le prennent pas en charge.

Les champs de métadonnées habituellement définis par Exif sont de nature technique et sont d’une utilité limitée pour la gestion descriptive des métadonnées. C’est pourquoi Experience Manager Assets  le mappage des propriétés Exif en  de métadonnées [courantes](metadata-schemas.md) et en [XMP](xmp-writeback.md).

### Other metadata {#other-metadata}

Les autres métadonnées pouvant être incorporées à partir de fichiers sont Microsoft Word, PowerPoint, Excel, etc.

## Metadata schemata {#metadata-schemata}

Les  de métadonnées sont des jeux prédéfinis de définitions de propriétés de métadonnées qui peuvent être utilisées dans diverses applications. Les propriétés sont toujours associées à une ressource, ce qui signifie que les propriétés sont &quot;relatives&quot; à la ressource.

Vous pouvez également concevoir vos propres schémas de métadonnées s’il n’en existe aucun qui réponde à vos besoins. Ne  pas les informations existantes. Au sein d’une entreprise, la séparation des schémas facilite le partage des métadonnées. Experience Manager fournit un par défaut des données de schéma de métadonnées les plus populaires. Le vous permet de lancer rapidement votre stratégie de métadonnées et de sélectionner rapidement les propriétés de métadonnées dont vous avez besoin.

Les schémas de métadonnées pris en charge sont répertoriés ci-dessous.

### Standard metadata {#standard-metadata}

* dc - Dublin Core - l’ensemble de métadonnées le plus important et le plus utilisé.
* DICOM - Digital Imaging and Communications in Medicine.
* Iptc4xmpCore et iptc4xmpExt - International Press Communications Standard - un grand nombre de métadonnées spécifiques au sujet.
* rdf - Resource Description Framework : pour les métadonnées web de sémantique générique.
* xmp - Extensible Metadata Platform.
* xmpBJ - Basic Job Ticketing.

### Application-specific metadata {#application-specific-metadata}

Les métadonnées propres à l’application comprennent des métadonnées techniques et descriptives. Si vous les utilisez, il se peut que d’autres applications ne puissent pas utiliser les métadonnées. Par exemple, si vous disposez d’un fichier avec des métadonnées Adobe Photoshop et qu’une autre application de rendu d’image tente d’accéder aux métadonnées, il se peut qu’elle ne puisse pas accéder aux métadonnées. Si vous constatez que vos fichiers contiennent de nombreuses métadonnées spécifiques à l’application, vous pouvez créer une étape de flux de travail qui transforme une propriété spécifique à l’application en propriété standard.

* acdsee - metadata managed by the ACDSee program [www.acdsee.com/](https://www.acdsee.com/).
* album - Adobe Photoshop Album.
* cq - utilisé par Experience Manager Assets.
* dam - utilisé par Experience Manager Assets.
* dex - Optima SC Description Explorer.
* crs - Adobe Photoshop Camera Raw.
* lr - Adobe Lightroom.
* mediapro - IView MediaPro.
* MicrosoftPhoto et MP - Microsoft Photo.
* pdf et pdfx
* photoshop et psAux - Adobe Photoshop

### Digital Rights Management metadata {#digital-rights-management-metadata}

* cc - creative commons
* xmpRights
* plus - Système universel de licences d&#39;image - https://www.useplus.com/
* prism - https://www.idealliance.org/prism-metadata de publication DPS pour les métadonnées standard du secteur
* prl - Prism Rights Language
* pur - Prism Usage Rights
* xmpPlus - intégration de PLUS avec XMP

### Photography-specific metadata {#photography-specific-metadata}

* exif - de nombreuses informations techniques de l’appareil photo, notamment la position GPS
* crs - photoshop camera raw
* Iptc4xmpCore et iptc4xmpExt
* TIFF - métadonnées d’image (pas seulement pour les images TIFF)

### Print-specific metadata {#print-specific-metadata}

* pdf et pdfx - Adobe PDF et applications tierces
* prism - [www.prismstandard.org](https://www.prismstandard.org) Publishing Requirements for Industry Standard Metadata
* xmp
* xmpPG - xmp pour le texte paginé

### Multimedia-specific metadata {#multimedia-specific-metadata}

* xmpDM - Dynamic Media
* xmpMM - Gestion des médias

## Metadata-driven workflows {#metadata-driven-workflows}

La création d’un axé sur les métadonnées permet d’automatiser certains processus, ce qui améliore l’efficacité. Dans un flux de travail axé sur les métadonnées, le système de gestion du flux de travail lit le flux de travail et effectue par conséquent une action prédéfinie. Voici quelques exemples d’utilisation des processus pilotés par les métadonnées :

* Le processus peut vérifier si une image possède un titre. Si elle n’en possède pas, le système demande à un utilisateur spécifique d’ajouter un titre.
* Le processus peut vérifier si un avis de droit d’auteur sur une ressource autorise la distribution. S’il l’autorise, le système envoie la ressource à un serveur. S’il ne l’autorise pas, le système envoie la ressource à un autre serveur.
* Un processus peut rechercher des fichiers sans métadonnées prédéfinies et obligatoires ou avec des métadonnées *non valides* .
