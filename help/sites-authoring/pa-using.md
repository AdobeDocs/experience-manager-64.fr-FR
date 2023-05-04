---
title: Affichage des données d’analyse de page
seo-title: Seeing Page Analytics Data
description: Utilisez les données d’analyse de page pour évaluer l’efficacité du contenu de leur page.
seo-description: Use page analytics data to gauge the effectiveness of their page content
uuid: 8dda89be-13e3-4a13-9a44-0213ca66ed9c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 42d2195a-1327-45c0-a14c-1cf5ca196cfc
exl-id: 6509c0ce-fc3a-4248-8dc7-db10602c30d6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 44%

---

# Affichage des données d’analyse de page{#seeing-page-analytics-data}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Utilisez les données d’analyse de page pour évaluer l’efficacité du contenu de la page.

## Analytics visible à partir de la console {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

Les données d’analyse de page s’affichent dans [Mode Liste](/help/sites-authoring/basic-handling.md#list-view) de la console Sites. Lorsque les pages sont affichées au format liste, les colonnes suivantes sont disponibles par défaut :

* Pages vues
* Visiteurs uniques
* Temps sur la page

Chaque colonne indique une valeur pour la période de création de rapports actuelle et indique également si la valeur a augmenté ou diminué depuis la période de création de rapports précédente. Les données que vous voyez sont mises à jour toutes les 12 heures.

>[!NOTE]
>
>Pour modifier la période de mise à jour, [configuration de l’intervalle d’importation](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Ouvrez la console **Sites** (par exemple, [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)).
1. À l’extrême droite de la barre d’outils (dans le coin supérieur droit), appuyez ou cliquez sur l’icône pour sélectionner **Vue Liste** (l’icône affichée dépendra de la [vue actuelle](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)).

1. Encore une fois, à l’extrémité droite de la barre d’outils (coin supérieur droit), cliquez ou appuyez sur l’icône, puis sélectionnez **Paramètres d’affichage**. Le **Configuration des colonnes** s’ouvre. Apportez les modifications requises et confirmez-les avec la commande **Mettre à jour**.

   ![aa-04](assets/aa-04.png)

### Sélection de la période de création de rapports {#selecting-the-reporting-period}

Sélectionnez la période de création de rapports pour laquelle les données Analytics apparaissent sur la console Sites :

* Données des 30 derniers jours
* Données des 90 derniers jours
* Données de cette année

La période de création de rapports actuelle apparaît sur la barre d’outils de la console Sites (à droite dans la barre d’outils supérieure). Utilisez le menu déroulant pour sélectionner la période de création de rapports requise. \
![aa-05](assets/aa-05.png)

### Configuration des colonnes de données disponibles {#configuring-available-data-columns}

Les membres du groupe d’utilisateurs analytics-administrateurs peuvent configurer la console Sites pour permettre aux auteurs d’afficher des colonnes Analytics supplémentaires.

>[!NOTE]
>
>Lorsqu’une arborescence de pages contient des enfants associés à différentes configurations de cloud Adobe Analytics, vous ne pouvez pas configurer les colonnes de données disponibles pour les pages.

1. En mode Liste, utilisez les sélecteurs d’affichage (à droite de la barre d’outils), puis sélectionnez **Paramètres d’affichage** puis A **Ajouter des données Analytics personnalisées**.

   ![aa-15](assets/aa-15.png)

1. Sélectionnez les mesures à présenter aux auteurs dans la console Sites, puis cliquez sur **Ajouter**.

   Les colonnes affichées sont obtenues à partir d’Adobe Analytics.

   ![aa-16](assets/aa-16.png)

### Ouverture de Content Insights à partir de la console Sites {#opening-content-insights-from-sites}

Ouvrez [Content Insight](/help/sites-authoring/content-insights.md) à partir de la console Sites pour continuer à évaluer en détail l’efficacité des pages.

1. Dans la console Sites, sélectionnez la page pour laquelle vous souhaitez afficher Content Insights.
1. Dans la barre d’outils, cliquez sur l’icône Analytics et Recommendations .

   ![](do-not-localize/chlimage_1-16.png)

## Les données d’analyse sont visibles dans l’éditeur de page (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>En raison de modifications de sécurité dans l’API Adobe Analytics, il n’est plus possible d’utiliser la version d’Activity Map incluse dans AEM.
>
>Le [plug-in Activity Map fourni par Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=fr) doit désormais être utilisé.
