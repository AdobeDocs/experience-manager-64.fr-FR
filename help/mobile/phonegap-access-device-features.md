---
title: Accès aux fonctionnalités du périphérique
seo-title: Access Device Features
description: Consultez cette page pour en savoir plus sur la création AEM composants qui accèdent aux fonctionnalités des périphériques. Le référentiel PhoneGap Kitchen Sink Github AEM fournit aux développeurs une application AEM fonctionnelle qui illustre l’utilisation de plusieurs API Cordova de base.
seo-description: Follow this page to learn about building AEM components that access device features. The AEM PhoneGap Kitchen Sink Github repository provides developers with a functional AEM app that illustrates the use of a number of core Cordova APIs.
uuid: 1996f017-21d3-4d90-9f55-95c626bc4c60
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 0019e367-8edc-4a23-bfa4-5beda266ace6
exl-id: 7f3a5081-9640-49ce-a8e7-8061fc080ec1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 13%

---

# Accès aux fonctionnalités du périphérique{#access-device-features}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

## Création d’AEM composants qui accèdent aux fonctions des périphériques {#building-aem-components-that-access-device-features}

Le [AEM PhoneGap Kitchen Sink](https://github.com/blefebvre/aem-phonegap-kitchen-sink) Le référentiel Github fournit aux développeurs une application d’AEM fonctionnelle qui illustre l’utilisation de plusieurs API Cordova de base. Lorsqu’elle est exécutée sur iOS ou Android via l’interface de ligne de commande de PhoneGap, l’application s’ouvre sur la page suivante qui comprend un lien vers chaque API de périphérique illustrée :

![chlimage_1-107](assets/chlimage_1-107.png)

Le code source de chacun de ces composants de l’API d’appareil est : [disponible sur Github](https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/apps/brucelefebvre/kitchen-sink/components).

Pour plus d’informations sur l’utilisation de chaque API, je vous recommande de jeter un coup d’oeil au [Documentation du module externe Cordova](https://docs.phonegap.com/en/4.0.0/cordova_plugins_pluginapis.md.html).

## Les étapes suivantes {#the-next-steps}

Voir [Suivi des performances de l’application avec Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md).
