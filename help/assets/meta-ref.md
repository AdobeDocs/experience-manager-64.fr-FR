---
title: Référence des schémas de métadonnées
description: Découvrez les conventions standard pour la description des métadonnées de ressources, notamment Dublin Core, IPTC et d’autres schémas de métadonnées.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 883bebc6-8bbc-43b1-91e5-9e2bf2470b6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 61%

---

# Référence des schémas de métadonnées {#metadata-schemata-reference}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La référence ci-après contient des informations sur un schéma de métadonnées spécifique (dans l’ordre alphabétique) ainsi qu’une liste de propriétés et de leur définition.

## Dublin Core {#dublin-core}

La métadonnée Dublin Core fournit un ensemble de conventions normalisé pour décrire les ressources afin de faciliter leur recherche. Dans [!DNL Experience Manager] Assets, Dublin Core décrit les ressources numériques, notamment les vidéos, le son, les images et les documents.

Le DCMES (Dublin Core Metadata Element Set) contient 15 éléments de métadonnées qui sont répertoriés dans le tableau ci-après. Chaque élément Dublin Core est facultatif et peut être utilisé plusieurs fois. Vous pouvez ajouter ou supprimer des informations de métadonnées Dublin Core comme vous le feriez pour les métadonnées spécifiques au type de média.

Outre le DCMES, il existe d’autres éléments de métadonnées créés par le Dublin Core Initiative. Pour plus d’informations, consultez [Dublin Core Initiative](https://dublincore.org/). 

| Propriété | Description |
|---|---|
| contributor | Personne ou entreprise chargée d’apporter des contributions au contenu. |
| coverage | Emplacement géographique ou période que couvre la ressource. |
| creator | Personne ou entreprise chargée de la création du contenu. |
| date | Date ou période associée à la ressource. |
| description | Informations supplémentaires sur la ressource. |
| format | Format de fichier, support physique ou dimensions de la ressource. [!DNL Experience Manager] utilise dc:format pour représenter le type MIME de la ressource. |
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

L&#39;International Press Telecommunications Council (IPTC) est un consortium d&#39;agences de presse à travers le monde - l&#39;un de ses objectifs est de développer et de maintenir des standards techniques. L&#39;IPTC a défini un ensemble de normes de métadonnées pour les images qui est presque universellement accepté par les photographes. Ces normes de métadonnées faisaient partie de la norme plus générale connue sous le nom de IPTC Information Interchange Model (IIM), créé dans les années 1990.

Bien que les informations d’en-tête IPTC aient été principalement remplacées par XMP, un schéma de base IPTC et un schéma d’extension sont disponibles pour XMP. Dans les programmes d’image, les propriétés XMP et IPTC sont synchronisées.
