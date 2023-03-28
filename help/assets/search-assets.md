---
title: Recherche de ressources dans AEM
description: Découvrez comment rechercher les ressources souhaitées dans [!DNL Experience Manager] à l’aide du panneau Filtres et comment utiliser les ressources affichées dans la recherche.
contentOwner: AG
feature: Search,Metadata
role: User
exl-id: cc1a5946-e13d-4433-a25a-d297fd07e2e4
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 21%

---

# Recherche de ressources dans [!DNL Experience Manager] {#search-assets-in-aem}

Découvrez comment rechercher les ressources souhaitées dans[!DNL Experience Manager]à l’aide du panneau Filtres et comment utiliser les ressources affichées dans la recherche.

Utilisez le panneau Filtres pour rechercher des ressources, des dossiers, des balises et des métadonnées. Vous pouvez rechercher des parties d’une chaîne à l’aide de l’astérisque générique.

Le panneau Filtres propose différentes options pour rechercher des ressources et des dossiers de plusieurs manières plutôt que dans un ordre taxonomique générique.

Vous pouvez effectuer des recherches en fonction des options (prédicats) suivantes :

* Type de fichier
* Taille de fichier
* Nom du champ
* Dernière modification
* Statut
* Orientation
* Style
* Statistiques

<!-- TBD keystroke 65 article and port applicable changes here. This content goes. -->

Vous pouvez personnaliser le panneau Filtres et ajouter/supprimer des prédicats de recherche à l’aide des [facettes de recherche](search-facets.md). Pour afficher le panneau Filtres, procédez comme suit :

1. Dans l’interface utilisateur Assets, appuyez/cliquez sur ![search_icon](assets/search_icon.png) dans la barre d’outils pour afficher la zone Omni-recherche.
1. Saisissez le terme recherché et appuyez sur Entrée. Vous pouvez également appuyer simplement sur Entrée sans entrer de terme de recherche. N’entrez aucun espace de début, sinon la recherche ne fonctionne pas.

1. Appuyez/cliquez sur l’icône de navigation globale. Le panneau Filtres s’affiche.

   ![filters_panel-1](assets/filters_panel-1.png)

   Selon le type d’éléments que vous recherchez, le nombre de correspondances est indiqué en haut des résultats de la recherche.

   ![number_of_searches](assets/number_of_searches.png)

## Recherche de types de fichiers {#search-for-file-types}

Le panneau Filtres permet d’ajouter plus de granularité à votre expérience de recherche et rend la fonctionnalité de recherche plus polyvalente. Vous pouvez facilement descendre dans la hiérarchie jusqu’au niveau de détail souhaité.

Par exemple, si vous recherchez une image, utilisez la variable **[!UICONTROL Type de fichier]** prédicat pour choisir si vous souhaitez une image bitmap ou vectorielle.

![image_type](assets/image_type.png)

Vous pouvez affiner davantage la portée de la recherche en spécifiant le type MIME de l’image.

![mime_type](assets/mime_type.png)

De même, lors de la recherche de documents, vous pouvez spécifier le format, par exemple PDF ou MS Word.

![documents](assets/documents.png)

## Recherche en fonction de la taille du fichier {#search-based-on-file-size}

Utilisez la variable **Taille de fichier** pour rechercher des ressources en fonction de leur taille. Vous pouvez spécifier les limites inférieure et supérieure de la plage de tailles pour affiner votre recherche. Vous pouvez également spécifier l’unité de mesure, par exemple Kilobytes, mégaoctets, etc.

![unit_of_measure](assets/unit_of_measure.png)

## Recherche en fonction de la date de dernière modification des ressources {#search-based-on-when-assets-are-last-modified}

Si vous gérez des ressources en cours ou que vous surveillez un workflow de révision, vous pouvez rechercher le moment où une ressource a été modifiée pour la dernière fois en fonction des horodatages exacts. Par exemple, spécifiez des dates avant ou après lesquelles les ressources ont été modifiées.

![last_modified_dates](assets/last_modified_dates.png)

Vous pouvez également utiliser les options suivantes pour obtenir un niveau de granularité supérieur dans votre recherche :

![timestamp](assets/timestamp.png)

## Recherche en fonction de l’état {#search-based-on-status}

Utilisez la variable **État** prédicat permettant de rechercher des ressources en fonction de différents types d’état, tels que Publier, Approbation, Extraction et Expiration.

![status](assets/status.png)

Par exemple, lorsque vous surveillez la publication de ressources, vous pouvez utiliser l’option appropriée pour rechercher les ressources qui sont publiées.

![publish](assets/publish.png)

Si vous surveillez l’état de révision des ressources, utilisez l’option appropriée pour trouver les ressources qui sont approuvées ou en attente d’approbation.

![validation](assets/approval.png)

## Recherche basée sur les données d’insights {#search-based-on-insights-data}

Utilisez la variable **Insights** prédicat permettant de rechercher des ressources en fonction de leurs statistiques d’utilisation obtenues auprès de diverses applications Creative. Les données d’utilisation sont regroupées dans les catégories suivantes :

* Score d’utilisation
* Impressions
* Clics
* Canaux de médias où les ressources apparaissent

![insights](assets/insights.png)
