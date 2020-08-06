---
title: Référence des schémas de métadonnées
description: 'Découvrez les conventions standard permettant de décrire les métadonnées des ressources, y compris Dublin Core, IPTC et d’autres schémas de métadonnées. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 97%

---


# Référence des schémas de métadonnées {#metadata-schemata-reference}

La référence ci-après contient des informations sur un schéma de métadonnées spécifique (dans l’ordre alphabétique) ainsi qu’une liste de propriétés et de leur définition.

## Dublin Core {#dublin-core}

La métadonnée Dublin Core fournit un ensemble de conventions normalisé pour décrire les ressources afin de faciliter leur recherche. Dans AEM Assets, Dublin Core décrit les ressources numériques, y compris les vidéos, le son, les images et les documents.

Le DCMES (Dublin Core Metadata Element Set) contient 15 éléments de métadonnées qui sont répertoriés dans le tableau ci-après. Chaque élément Dublin Core est facultatif et peut être utilisé plusieurs fois. Vous pouvez ajouter ou supprimer des informations de métadonnées Dublin Core comme vous le feriez pour les métadonnées spécifiques au type de média.

Outre le DCMES, il existe d’autres éléments de métadonnées créés par le Dublin Core Initiative. Pour plus d’informations, consultez [Dublin Core Initiative](http://dublincore.org/). 

| Propriétés | Description |
|---|---|
| contributor | Personne ou entreprise chargée d’apporter des contributions au contenu. |
| coverage | Emplacement géographique ou période que couvre la ressource. |
| creator | Personne ou entreprise chargée de la création du contenu. |
| date | Date ou période associée à la ressource. |
| description | Informations supplémentaires sur la ressource. |
| format | Format de fichier, support physique ou dimensions de la ressource. AEM utilise le format dc:format pour indiquer le type mime de la ressource. |
| identifier | Référence unique à la ressource. |
| language | Langue de la ressource (« en » pour l’anglais, par exemple). |
| publisher | Personne ou entreprise chargée de rendre la ressource disponible. |
| relation | Ressource connexe. |
| rights | Informations sur la personne qui dispose des droits sur cette ressource. |
| source | Ressource connexe à partir de laquelle la ressource est dérivée. |
| subject | Objet de la ressource. |
| title | Nom de la ressource. |
| type | Nature ou genre de la ressource. |

## IPTC {#iptc}

L’ITPC (International Press Telecommunications Council) est un consortium réunissant les principales agences de presse à travers le monde. L’un de ses principaux objectifs est de développer et maintenir des normes techniques. L’IPTC a défini un ensemble de normes de métadonnées photographiques qui est presque universellement accepté par les photographes. Ces normes de métadonnées faisaient partie de la norme plus générale appelée IPTC Information Interchange Model (IIM) créée dans les années 1990.

Bien que les informations d’en-tête IPTC ont été essentiellement remplacées par XMP, un schéma de base IPTC et un schéma d’extension sont disponibles pour XMP. Dans les programmes de traitement d’images, les propriétés XMP et IPTC sont synchronisées.
