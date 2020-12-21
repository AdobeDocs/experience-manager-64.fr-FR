---
title: Configuration de l’environnement de l’application AEM Forms
seo-title: Configuration de l’environnement de l’application AEM Forms
description: Matériel, logiciels et licences permettant de générer et déployer l’application AEM Forms.
seo-description: Matériel, logiciels et licences permettant de générer et déployer l’application AEM Forms.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 66%

---


# Configuration de l’environnement de l’application AEM Forms  {#set-up-environment-for-aem-forms-app}

Vous avez besoin du matériel, des logiciels et licences ci-dessous pour générer et déployer l’application AEM Forms :

## Pour les périphériques Windows  {#for-windows-devices}

* Microsoft Windows 8.1 ou Windows 10
* Microsoft Visual Studio 2015
* Outils Microsoft Visual Studio pour Apache Cordova

## Pour les périphériques iOS {#for-ios-devices}

* Ordinateur Apple Mac à processeur Intel avec Mac OS X 10.9.5 ou version supérieure
* SDK iOS 8.4 ou version ultérieure
* Version Xcode : Xcode 6.4 pour OS X ou version supérieure
* Adhésion au programme pour développeurs iOS en entreprise
* Certificat d’entreprise pour la distribution d’applications iOS en interne
* Apple iPad avec iOS 8.4 ou version ultérieure

## Pour périphériques Android  {#for-android-devices}

* Android Development Toolkit (lot ADT) peut être téléchargé à partir de [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Si l’environnement est configuré sur un système MAC, ADT doit être installé dans le dossier Applications.
* Si l’outil ADT est installé à un autre emplacement sur MAC ou si l’environnement est configuré sur un système Windows, le chemin d’accès du SDK ADT doit être mis à jour dans le fichier `local.properties` disponible dans le dossier `src\android` de l’archive source extraite `mobileworkspace-src.zip`. Dans ce fichier, pointez la variable `sdk.dir` vers l’emplacement de ADT SDK sur votre bureau.

>[!NOTE]
>
>Le fichier adobe-lc-mobileworkspace-src.zip contient le SDK PhoneGap 5.0. Assurez-vous que le SDK PhoneGap n’est pas préinstallé.
