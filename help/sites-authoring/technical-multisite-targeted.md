---
title: Structuration de la gestion multisite du contenu ciblé
seo-title: How Multisite Management for Targeted Content is Structured
description: Un diagramme illustre la structure de la prise en charge de sites multiples pour le contenu ciblé
seo-description: A diagram shows how multisite support for targeted content is structured
uuid: 2d30cdf0-ab77-490d-aac0-db3a0d417a58
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 7dd851ab-3fa7-426e-89cb-08b67e9b5999
exl-id: 28c45577-e5cd-4706-b5b2-227279126ad9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 40%

---

# Structuration de la gestion multisite du contenu ciblé{#how-multisite-management-for-targeted-content-is-structured}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le diagramme suivant indique comment est structurée la prise en charge multisite du contenu ciblé.

Les zones apparaissent sous **/content/campaigns/&lt;marque>** et par défaut chaque marque comporte une zone maître, qui est créée automatiquement. Chaque zone contient son propre ensemble d’activités, d’expériences et d’offres.

![chlimage_1-268](assets/chlimage_1-268.png)

Pour rechercher du contenu ciblé, les pages ou les sites peuvent correspondre à une zone. Si aucune zone n’est configurée, AEM revient à la zone maître de cette marque spécifique.

Le diagramme suivant illustre le fonctionnement de la logique pour trois sites, nommés site1, site2 et site3.

![chlimage_1-269](assets/chlimage_1-269.png)

* site1 recherche myarea1 pour brand1 et otherarea2 pour brand2 en fonction du mappage des zones.
* site2 recherche myarea1 pour la marque1 et la zone maître pour la marque2, car seul le mappage de zone pour la marque1 est défini.
* site3 recherche la zone maître pour brand1 et brand2, car aucun autre mappage de zone n’est défini pour ce site.
