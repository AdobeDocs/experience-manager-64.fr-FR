---
title: Configuration de l’environnement de l’application AEM Forms
seo-title: Set up environment for AEM Forms app
description: Matériel, logiciels et licences permettant de générer et déployer l’application AEM Forms.
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 100%

---

# Configuration de l’environnement de l’application AEM Forms {#set-up-environment-for-aem-forms-app}

Vous avez besoin du matériel, des logiciels et licences ci-dessous pour générer et déployer l’application AEM Forms :

## Pour les périphériques Windows {#for-windows-devices}

* Microsoft Windows 8.1 ou Windows 10
* Microsoft Visual Studio 2015
* Outils Microsoft Visual Studio pour Apache Cordova

## Pour les périphériques iOS {#for-ios-devices}

* Ordinateur Apple Mac à processeur Intel avec Mac OS X 10.9.5 ou version supérieure
* SDK iOS 8.4 ou version supérieure
* Version Xcode : Xcode 6.4 pour OS X ou version supérieure
* Adhésion au programme pour développeurs iOS en entreprise
* Certificat d’entreprise pour la distribution d’applications iOS en interne
* Apple iPad avec iOS 8.4 ou version ultérieure

## Pour périphériques Android {#for-android-devices}

* Android Development Toolkit (lot ADT) peut être téléchargé depuis [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Si l’environnement est configuré sur un système MAC, ADT doit être installé dans le dossier Applications.
* Si l’ADT est installé à un autre emplacement sur MAC, ou si l’environnement est configuré sur un système Windows, le chemin d’accès à ADT SDK doit être mis à jour dans le fichier `local.properties` qui est disponible dans le dossier `src\android` de l’archive source extraite `mobileworkspace-src.zip`. Dans ce fichier, pointez la variable `sdk.dir` vers l’emplacement d’ADT SDK sur votre bureau.

>[!NOTE]
>
>Le fichier adobe-lc-mobileworkspace-src.zip contient le PhoneGAP SDK 5.0. Assurez-vous que le PhoneGap SDK n’est pas préinstallé.
