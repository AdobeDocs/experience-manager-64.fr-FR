---
title: Création d’une page pour les appareils mobiles
seo-title: Authoring a Page for Mobile Devices
description: Lors de la création pour les appareils mobiles, vous pouvez basculer entre plusieurs émulateurs pour voir ce que l’utilisateur final voit.
seo-description: When authoring for mobile, you can switch between several emulators to see what the end-user sees
uuid: a7a1ba68-d608-4819-88d1-0dab5955d3f4
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 9554cdb3-b604-4d50-9760-89b9e7a7755f
exl-id: 97f0b0d2-7d7b-4a90-a4e5-348a306e1622
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 52%

---

# Création d’une page pour les appareils mobiles{#authoring-a-page-for-mobile-devices}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsque vous créez une page mobile, celle-ci est affichée d’une manière qui émule l’appareil mobile. Lors de la création de la page, vous pouvez basculer entre plusieurs émulateurs pour voir ce que l’utilisateur final voit lorsqu’il accède à la page.

Les périphériques sont regroupés dans les catégories fonctionnalité, intelligent et tactile selon les capacités des périphériques à effectuer le rendu d’une page. Lorsque l’utilisateur final accède à une page mobile, AEM détecte l’appareil et envoie la représentation qui correspond à son groupe d’appareils.

>[!NOTE]
>
>Pour créer un site mobile en fonction d’un site standard existant, créez une Live Copy du site standard. (Reportez-vous à [Création d’une live copy pour différents canaux](/help/sites-administering/msm-livecopy.md).)
>
>L’équipe de développement d’AEM peut créer de nouveaux groupes d’appareils. (Voir [Création de filtres de groupe d’appareils](/help/sites-developing/groupfilters.md).)

Utilisez la procédure suivante pour créer une page mobile :

1. À partir de la navigation globale, ouvrez la console **Sites**.
1. Ouvrez la page **We.Retail** -> **États-Unis**-> **Anglais**.

1. Basculez en mode **Aperçu**.
1. Passez à l’émulateur de votre choix en cliquant sur l’icône de périphérique en haut de la page.
1. Faites glisser des composants de l’explorateur de composants vers la page.

La page ressemble à ce qui suit :

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>Les émulateurs sont désactivés lorsqu’une page de l’instance de création est demandée à partir d’un appareil mobile.
