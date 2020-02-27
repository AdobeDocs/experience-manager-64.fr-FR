---
title: Métadonnées XMP
description: Découvrez le standard de métadonnées XMP (Extensible Metadata Platform) utilisé par AEM Assets pour la gestion des métadonnées. XMP offre un format standard pour la création, le traitement et l’échange de métadonnées pour une multitude d’applications.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Métadonnées XMP {#xmp-metadata}

XMP (« Extensible Metadata Platform », plate-forme de métadonnées extensible) est la norme de métadonnées utilisée par AEM Assets pour toute la gestion des métadonnées. XMP fournit un format standard pour la création, le traitement et l’échange de métadonnées pour toute une variété d’applications.

Aside from offering universal metadata encoding that can be embedded into all file formats, XMP provides a rich [content model](xmp.md#xmp-core-concepts) and is [supported by Adobe](xmp.md#advantages-of-xmp) and other companies, so that users of XMP in combination with AEM Assets have a powerful platform to build upon.

La [spécification XMP](https://www.adobe.com/devnet/xmp.html) est disponible auprès d’Adobe.

## What is XMP? {#what-is-xmp}

AEM Assets prend nativement en charge XMP, la plateforme de métadonnées extensible pilotée par Adobe.XMP est une norme de traitement et de stockage des métadonnées propriétaires et normalisées dans les ressources numériques.XMP est conçu pour être la norme commune qui permet à plusieurs applications de fonctionner efficacement avec les métadonnées.

Les professionnels de la production, par exemple, utilisent la prise en charge du format XMP intégré au sein des applications d’Adobe pour communiquer les informations entre divers formats de fichier. Le référentiel AEM Assets extrait les métadonnées XMP et les utilise pour gérer le cycle de vie du contenu. Il offre également la possibilité de créer des processus d’automatisation.

XMP normalise la façon dont les métadonnées sont définies, créées et traitées en fournissant un modèle de données, un modèle de stockage et des schémas. Tous ces concepts sont abordés dans cette section.

Toutes les métadonnées héritées de EXIF, ID3 ou Microsoft Office sont automatiquement converties au format XMP, qui peut être étendu pour prendre en charge le schéma de métadonnées spécifiques au client comme les catalogues de produits.

Les métadonnées dans XMP sont composées d’un ensemble de propriétés. Ces propriétés sont toujours associées à une\
une entité particulière désignée comme ressource; c&#39;est-à-dire que les propriétés sont &quot;à propos&quot; de la ressource. Dans le cas de XMP, la ressource est toujours la ressource.

### Adobe {#adobe}

Adobe a introduit pour la première fois la norme XMP dans le cadre du logiciel Adobe Acrobat. Depuis, la norme XMP a été largement adoptée.

### XMP ecosystem {#xmp-ecosystem}

XMP définit un modèle de [métadonnées](https://en.wikipedia.org/wiki/Metadata) qui peut être utilisé avec n’importe quel ensemble défini d’éléments de métadonnées. XMP définit également des [schémas](https://en.wikipedia.org/wiki/XML_schema) particuliers pour les propriétés de base utiles pour enregistrer l’historique d’une ressource lorsqu’elle passe par plusieurs étapes de traitement, depuis la photographie, la [numérisation](https://en.wikipedia.org/wiki/Image_scanner) ou la création au format texte, en passant par les étapes de retouche photo ([recadrage](https://en.wikipedia.org/wiki/Cropping_%28image%29) ou réglage des couleurs, par exemple), pour l’assembler dans une image finale. XMP permet à chaque programme logiciel ou appareil d’ajouter en cours de route ses propres informations à une ressource numérique, qui peut ensuite être conservée dans le fichier numérique final.

XMP est le plus souvent sérialisé et stocké à l’aide d’un sous-ensemble du [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF) [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium), qui est à son tour exprimé en langage [XML](https://en.wikipedia.org/wiki/XML).

## Avantages du mode XMP {#advantages-of-xmp}

La norme XMP présente les avantages suivants par rapport aux autres normes de codage et schémas :

* Les métadonnées basées sur la norme XMP sont très puissantes et précises.
* La norme XMP permet de posséder plusieurs valeurs pour une propriété.
* XMP possède un encodage normalisé, ce qui vous permet d’échanger facilement des métadonnées.
* Le format XMP est extensible. Vous pouvez ajouter d’autres informations à vos ressources.

### Extensibles {#extensible}

La norme XMP a été conçue pour être extensible, ce qui vous permet d’ajouter des types de métadonnées personnalisés dans les données XMP. En revanche, ce n’est pas le cas d’EXIF qui présente une liste des propriétés qui ne peut pas être étendue.

>[!NOTE]
>
>En règle générale, XMP ne permet pas l’incorporation des types de données binaires. Pour gérer des données binaires dans XMP, comme des images miniatures, celles-ci doivent être codées dans un format XML tel que Base64.

## Notions fondamentales relatives à XMP {#xmp-core-concepts}

Les sections ci-après décrivent les notions fondamentales relatives à XMP, notamment les espaces de noms et les schémas, les propriétés et les valeurs, ainsi que les variantes linguistiques.

### Espaces de noms et schémas {#namespaces-and-schemata}

Un schéma XMP est un ensemble de noms de propriété dans un espace de noms XML commun qui inclut\
le type de données et les informations descriptives. Un schéma XMP est identifié par son URI d’espace de noms XML. L’utilisation d’espaces de noms empêche les conflits entre les propriétés de différents schémas portant le même nom mais une signification différente.

Par exemple, la propriété **Créateur** de deux schémas conçus indépendamment peut signifier la personne ayant créé la ressource ou l’application l’ayant créée (Adobe Photoshop, par exemple).

### Propriétés et valeurs {#properties-and-values}

XMP peut inclure des propriétés de l’un ou de plusieurs des schémas.

Par exemple, un sous-ensemble classique utilisé par de nombreuses applications Adobe peut comprendre les éléments suivants :

* Schéma Dublin Core : dc:title, dc:creator, dc:subject, dc:format, dc:rights
* Schéma de base XMP : xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* Schéma de gestion des droits XMP : xmpRights:WebStatement, xmpRights:Marked
* Schéma de gestion des médias XMP : xmpMM:DocumentID

### Variantes linguistiques {#language-alternatives}

XMP vous offre la possibilité d’ajouter une propriété **xml:lang** aux propriétés de texte pour spécifier la langue du texte.
