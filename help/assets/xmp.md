---
title: Métadonnées XMP
description: Découvrez la norme de métadonnées XMP (Extensible Metadata Platform) utilisée par [!DNL Experience Manager] Ressources pour la gestion des métadonnées. XMP offre un format standard pour la création, le traitement et l’échange de métadonnées pour une multitude d’applications.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 32c4ca3d-2e9e-46a3-b4c7-70dcc50daaaa
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 81%

---

# Métadonnées XMP {#xmp-metadata}

XMP (Extensible Metadata Platform) est la norme de métadonnées utilisée par [!DNL Experience Manager] Ressources pour la gestion des métadonnées. XMP offre un format standard pour la création, le traitement et l’échange de métadonnées pour une multitude d’applications.

En plus d’un codage de métadonnées universel qui peut être incorporé dans tous les formats de fichier, XMP fournit un [modèle de contenu](xmp.md#xmp-core-concepts) riche et est [pris en charge par Adobe](xmp.md#advantages-of-xmp) et d’autres sociétés. Ainsi, les utilisateurs XMP, en association avec Assets, disposent d’une plate-forme puissante sur laquelle s’appuyer.[!DNL Experience Manager]

La [spécification XMP](https://www.adobe.com/devnet/xmp.html) est disponible auprès d’Adobe.

## Présentation de la norme XMP {#what-is-xmp}

[!DNL Experience Manager] Assets prend en charge de manière native le XMP : la plateforme de métadonnées extensible pilotée par Adobe. XMP est une norme destinée au traitement et au stockage de métadonnées normalisées et propriétaires dans les ressources numériques. La norme XMP est conçue pour être la norme commune permettant à plusieurs applications de fonctionner efficacement avec les métadonnées.

Les professionnels de la production, par exemple, utilisent la prise en charge XMP intégrée dans les applications d’Adobe pour transmettre des informations sur plusieurs formats de fichiers. Le [!DNL Experience Manager] Le référentiel de ressources extrait les métadonnées XMP et les utilise pour gérer le cycle de vie du contenu et offre la possibilité de créer des workflows d’automatisation.

XMP normalise la façon dont les métadonnées sont définies, créées et traitées en fournissant un modèle de données, un modèle de stockage et des schémas. Tous ces concepts sont abordés dans cette section.

Toutes les métadonnées héritées d’EXIF, d’ID3 ou de Microsoft Office sont automatiquement converties au format XMP, qui peut être étendu pour prendre en charge le schéma de métadonnées spécifiques au client comme les catalogues de produits.

Les métadonnées de XMP se composent d’un ensemble de propriétés. Ces propriétés sont toujours associées à une propriété\
une entité particulière appelée ressource ; en d’autres termes, les propriétés portent sur la ressource. Dans le cas de XMP, il s’agit toujours de la ressource (ou actif).

### Adobe {#adobe}

Adobe a introduit pour la première fois la norme XMP dans le cadre du logiciel Adobe Acrobat. Depuis, la norme XMP a été largement adoptée.

### XMP écosystème {#xmp-ecosystem}

XMP définit un modèle de [métadonnées](https://fr.wikipedia.org/wiki/Métadonnée) exploitable avec n’importe quel ensemble défini d’éléments de métadonnées. XMP définit également des [schémas](https://en.wikipedia.org/wiki/XML_schema) spécifiques pour des propriétés de base utiles pour consigner l’historique d’une ressource lorsqu’elle passe par diverses étapes de traitement, de la photographie, en passant par la [numérisation](https://fr.wikipedia.org/wiki/Scanner_(informatique)) ou la création en tant que texte, à travers des étapes de retouche photo (comme le [recadrage](https://fr.wikipedia.org/wiki/Recadrage_(image)) ou l’ajustement de couleur), pour former une image finale. XMP permet à chaque programme ou appareil d’ajouter ses propres informations à une ressource numérique. Ces informations peuvent être ensuite conservées dans le fichier numérique final.

XMP est le plus souvent sérialisé et stocké à l’aide d’un sous-ensemble du [W3C](https://fr.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://fr.wikipedia.org/wiki/Resource_Description_Framework) (RDF), exprimé à son tour en format [XML](https://fr.wikipedia.org/wiki/Extensible_Markup_Language).

## Avantages du mode XMP {#advantages-of-xmp}

La norme XMP présente les avantages suivants par rapport aux autres normes de codage et schémas :

* Les métadonnées basées sur la norme XMP sont très puissantes et précises.
* La norme XMP permet de définir plusieurs valeurs pour une propriété.
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

Un schéma XMP est un ensemble de noms de propriété dans un espace de noms XML commun qui comprend\
le type de données et des informations descriptives. Un schéma XMP est identifié par son URI d’espace de noms XML. L’utilisation d’espaces de noms empêche les conflits entre les propriétés de différents schémas qui portent le même nom mais ont une signification différente.

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
