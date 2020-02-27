---
title: Intégration d’Adobe Analytics avec AEM Screens
seo-title: Intégration d’Adobe Analytics avec AEM Screens
description: Consultez cette page pour en savoir plus sur l’intégration immédiate d’AEM Screens avec Adobe Analytics. AEM Screens vous fournit également une preuve de lecture.
seo-description: Consultez cette page pour en savoir plus sur l’intégration immédiate d’AEM Screens avec Adobe Analytics. AEM Screens vous fournit également une preuve de lecture.
uuid: f4f71c85-ab6b-4e4d-94d3-5ba55ec0a246
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: 2784b590-3402-492f-94a6-36fe16633e89
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Intégration d’Adobe Analytics avec AEM Screens{#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Cette fonctionnalité d’AEM Screens n’est disponible que si vous avez installé AEM 6.4.2 Feature Pack 2 ou AEM 6.3.3 Feature Pack 4.

>Pour accéder à l’un de ces Feature Packs, contactez l’assistance Adobe et déposez une requête dans ce sens. Une fois que vous disposez des autorisations nécessaires, vous pouvez le télécharger à partir de Package Share.
>
Cette section couvre les sujets suivants :

* **Présentation**
* **Particularités architecturales**
* **Configuration des propriétés**

## Présentation {#overview}

***AEM Screens*** tire parti d’Adobe Analytics ; vous obtenez ainsi une solution unique sur le marché : des analyses multicanaux permettant de mettre le contenu affiché à l’emplacement concerné en corrélation avec d’autres sources de données.

AEM Screens permet une intégration immédiate avec Adobe Analytics et vous fournit une preuve de lecture.

Cette section décrit les fonctionnalités suivantes liées à la connexion d’un projet AEM Screens avec Adobe Analytics :

* Permet de créer des rapports de preuve de lecture par périphérique
* Permet de créer des rapports de preuve de lecture par ressource
* Veille à ce que tous les événements du lecteur soient capturés et horodatés
* Veille à ce que tous les événements du lecteur soient stockés localement s’il n’est pas connecté à un réseau

Ainsi, l’intégration d’Adobe Analytics avec AEM Screens permet de réaliser les *objectifs* suivants :

* Obtenir un retour sur investissement des implémentations d’affichage numérique
* Intégrer Analytics comme support employé pour collecter et analyser ultérieurement les informations d’utilisation

## Particularités architecturales {#architectural-details}

Le diagramme architectural suivant explique comment Adobe Analytics s’intègre avec AEM Screens :

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Activation d’Adobe Analytics dans AEM Screens {#enabling-adobe-analytics-in-aem-screens}

Les paramètres Adobe Analytics peuvent être configurés depuis la console OSGi.

Accédez à **Configuration de la console Web Adobe Experience Manager** pour configurer Adobe Analytics pour AEM Screens, comme l’illustre la figure suivante :

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

### Configuration des propriétés {#configuring-the-properties}

>[!CAUTION]
Avant de configurer les propriétés, contactez le responsable des relations Adobe pour créer un ticket et obtenir une **clé d’API Analytics**, ainsi qu’un **projet Analytics** afin de l’utiliser avec AEM Screens.

Le tableau suivant répertorie et décrit les propriétés permettant de configurer Adobe Analytics pour AEM Screens :

<table> 
 <tbody>
  <tr>
   <td><strong>Propriétés</strong></td> 
   <td><strong>Description</strong></td> 
  </tr>
  <tr>
   <td><strong>URL Analytics</strong></td> 
   <td>URL de publication des données d’analyse depuis le lecteur<br /> </td> 
  </tr>
  <tr>
   <td><strong>Clé d’API Analytics</strong></td> 
   <td>Clé d’API utilisée à des fins d’authentification auprès du serveur Adobe Analytics (fournie par le responsable de compte Adobe)</td> 
  </tr>
  <tr>
   <td><strong>Projet Analytics</strong></td> 
   <td>Projet AEM Screens configuré sur les analyses de manière à recevoir des données (fourni par le responsable de compte Adobe)</td> 
  </tr>
  <tr>
   <td><strong>Environnement</strong></td> 
   <td><p>Environnement d’étape ou de production.</p> <p><em>Développement/étape</em> : https://cc-api-data-stage.adobe.io/ingest/<br /> Production<em></em> : https://cc-api-data.adobe.io/ingest/</p> </td> 
  </tr>
  <tr>
   <td><strong>Fréquence d’envoi des données d’analyse</strong></td> 
   <td>Fréquence d’envoi des données d’analyse depuis les lecteurs, en minutes. Par défaut, elle est définie sur 15 mn.</td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
Par défaut, la **fréquence d’envoi des données d’analyse **est de 15 minutes.

#### Utilisation d’Adobe Analytics Service dans AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Ce scénario appelle l’API Analytics en lançant des appels REST depuis un service d’analyse des principaux composants Screens de microprogramme et d’instrument pour créer et envoyer explicitement des événements propres à un cas d’utilisation donné, tout en autorisant l’extensibilité si un message personnalisé peut être envoyé à Analytics depuis un canal développé et personnalisé.

Les événements Analytics sont stockés hors ligne dans indexedDB, puis segmentés et envoyés ultérieurement vers le cloud.

>[!NOTE]
To learn more about the ***Sequencing*** and ***Standard Data Model for Events***, please refer to [Configuring Adobe Analytics for AEM Screens](configuring-adobe-analytics-aem-screens.md) in Developer&#39;s section of AEM Screens.

