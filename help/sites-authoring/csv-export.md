---
title: Exporter au format CSV
seo-title: Export to CSV
description: Exporter des informations sur vos pages dans un fichier CSV sur votre système local
seo-description: Export information about your pages to a CSV file on your local system
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 54%

---

# Exporter au format CSV{#export-to-csv}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

**Créer une exportation CSV** vous permet d’exporter des informations sur vos pages vers un fichier CSV situé sur votre système local.

* Le fichier téléchargé est nommé `export.csv`.
* Le contenu dépend des propriétés que vous sélectionnez.
* Vous pouvez définir le chemin, ainsi que la profondeur de l’exportation.

>[!NOTE]
>
>La fonction de téléchargement et la destination par défaut du navigateur sont utilisées.

L’assistant Créer une exportation CSV vous permet de sélectionner les éléments suivants :

* Propriétés à exporter

   * Métadonnées

      * Modifié
      * Publié
   * Analyses

      * Pages vues
      * Visiteurs uniques
      * Temps sur la page


* Profondeur

   * Chemin d’accès parent
   * Enfants directs uniquement
   * Niveaux supplémentaires d’enfants
   * Niveaux

Vous pouvez ouvrir le fichier `export.csv` obtenu dans Excel (ou toute autre application compatible).

![chlimage_1-58](assets/chlimage_1-58.png)

La création **Exportation CSV** est disponible lors de la navigation dans la **Sites** console (en mode Liste) : il s’agit d’une option de la fonction **Créer** menu déroulant :

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

Pour créer une exportation CSV :

1. Ouvrez la console **Sites**, puis, le cas échéant, accédez à l’emplacement requis.
1. Dans la barre d’outils, sélectionnez **Créer** then **Exportation CSV** pour ouvrir l’assistant :

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. Sélectionnez les propriétés à exporter.
1. Sélectionnez **Créer**.
