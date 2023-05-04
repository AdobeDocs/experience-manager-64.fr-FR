---
title: Content Insight
seo-title: Content Insight
description: Content Insight fournit des informations sur les performances des pages à l’aide de l’analyse Web et des recommandations d’optimisation pour les moteurs de recherche.
seo-description: Content Insight provides information about page performance using web analytics and SEO recommendation
uuid: 32f5b37c-2a82-462a-9f0a-c19bed46e198
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 60f980fd-049e-43c1-8b5d-60a8279b357a
exl-id: 54ec1b84-bee2-4c1f-acbc-8e6bd0d76c87
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 19%

---

# Content Insight{#content-insight}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Content Insight fournit des informations sur les performances des pages à l’aide de l’analyse web et des recommandations d’optimisation pour les moteurs de recherche. Utilisez Content Insight pour prendre des décisions sur la modification des pages ou pour découvrir comment les modifications précédentes ont modifié les performances. Pour chaque page que vous créez, vous pouvez ouvrir Content Insight afin d’analyser la page.

![chlimage_1-311](assets/chlimage_1-311.png)

La disposition de la page Content Insight s’adapte à la dimension et à l’orientation de l’écran du périphérique que vous utilisez.

## Données de rapport

La page Content Insight comprend des rapports qui utilisent les données Adobe SiteCatalyst, Adobe Target, Adobe Social et BrightEdge :

* SiteCatalyst : Les rapports pour les mesures suivantes sont disponibles :

   * Pages vues
   * Durée moyenne de consultation de la page
   * Sources

* Cible : Rapports sur l’activité de campagne pour laquelle votre page contient des offres.
* BrightEdge : Rapports sur les fonctionnalités de la page qui améliorent la visibilité de la page pour les moteurs de recherche et recommande les fonctionnalités à mettre en oeuvre.

Reportez-vous à [Ouverture de l’analyse et des recommandations concernant une page](/help/sites-authoring/ci-analyze.md#opening-analytics-and-recommendations-for-a-page).

## Période de reporting

Les rapports présentent les données pour une période que vous contrôlez. Lorsque vous ajustez la période de création de rapports, les rapports s’actualisent automatiquement avec les données de cette période. Des repères visuels indiquent le moment où les versions de page ont changé, de sorte que vous pouvez comparer les performances de chaque version.

Vous pouvez également spécifier la granularité des données signalées ; vous pouvez, par exemple, afficher les données quotidiennes, hebdomadaires, mensuelles ou annuelles.

Voir [Modification de la période de création de rapports](/help/sites-authoring/ci-analyze.md#changing-the-reporting-period).

>[!NOTE]
>
>Les rapports Content Insights nécessitent que votre administrateur ait intégré AEM à SiteCatalyst, Target et BrightEdge. Reportez-vous à [Intégration avec SightCatalyst](/help/sites-administering/adobeanalytics.md), [Intégration avec Adobe Target](/help/sites-administering/target.md) et [Intégration avec BrightEdge](/help/sites-administering/brightedge.md).

## Rapport Vues {#the-views-report}

Le rapport Vues comprend les fonctionnalités suivantes pour évaluer le trafic de pages :

* Nombre total de vues pour une page pendant la période de création de rapports.
* Graphique montrant le nombre de vues sur la période du rapport :

   * Nombre total de vues.
   * Visiteurs uniques.

![chlimage_1-312](assets/chlimage_1-312.png)

## Rapport Moyenne d’engagement de la page {#the-page-average-engaged-report}

Le rapport Moyenne de page active comprend les fonctionnalités suivantes pour évaluer l’efficacité des pages :

* Durée moyenne pendant laquelle la page reste ouverte pendant toute la période de création de rapports.
* Graphique montrant la durée moyenne d’une page vue au cours de la période de création de rapports.

![chlimage_1-313](assets/chlimage_1-313.png)

## Rapport Sources {#the-sources-report}

Le rapport Sources indique comment les utilisateurs ont accédé à la page, par exemple à partir des résultats du moteur de recherche ou à l’aide de l’URL connue.

![chlimage_1-314](assets/chlimage_1-314.png)

## Rapport Rebonds {#the-bounces-report}

Le rapport Rebonds comprend un graphique qui indique le nombre de rebonds qui se sont produits pour une page au cours de la période de rapport sélectionnée.

![chlimage_1-315](assets/chlimage_1-315.png)

## Rapport Activité de campagne {#the-campaign-activity-report}

Pour chaque campagne pour laquelle la page est principale, un rapport s’affiche nommé *Nom de la campagne* Activité. Le rapport affiche les impressions et les conversions de page pour chaque segment pour lequel une offre est fournie.

![chlimage_1-316](assets/chlimage_1-316.png)

## Rapport Recommendations d’optimisation pour les moteurs de recherche {#the-seo-recommendations-report}

Le rapport Recommendations d’optimisation pour les moteurs de recherche contient les résultats de l’analyse BrightEdge pour la page. Le rapport est une liste de contrôle des fonctionnalités de page qui indique quelles fonctionnalités de la page incluent ou non pour optimiser la recherche à l’aide des moteurs de recherche.

Le rapport permet de créer des tâches afin d&#39;améliorer la recherche des pages. Recommendations indique que des tâches ont été créées pour la mise en oeuvre de la recommandation. Voir [Attribution de tâches à Recommendations pour l’optimisation pour les moteurs de recherche](/help/sites-authoring/ci-analyze.md#assigning-tasks-for-seo-recommendations).

![chlimage_1-317](assets/chlimage_1-317.png)
