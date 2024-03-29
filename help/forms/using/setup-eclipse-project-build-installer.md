---
title: Générez l’application Android AEM Forms.
seo-title: Build the AEM Forms Android app
description: Procédure de configuration du projet Android Studio et de création du fichier .apk pour l’application AEM Forms pour Android
seo-description: Steps to set up the Android Studio project and build the .apk file for the AEM Forms app for Android
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
exl-id: dbeed62e-eff1-47bc-b6da-cad543295170
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 74%

---

# Générez l’application Android AEM Forms. {#build-the-aem-forms-android-app}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Effectuez les étapes suivantes dans l’ordre recommandé pour créer l’application Android pour AEM Forms.

1. [Téléchargement du package de code source de l’application AEM Forms](#download-android-zip)
1. [Définition des variables d’environnement](#set-environment-variable-android)
1. [Génération d’une application AEM Forms standard](#set-up-the-xcode-project)

## Téléchargement du package de code source de l’application AEM Forms {#download-android-zip}

Le package de code source de l’application AEM Forms fait référence à l’archive `adobe-lc-mobileworkspace-src-<version>.zip`. Cette archive comprend le code source requis pour créer une application AEM Forms personnalisée. L’archive est incluse dans le package `adobe-aemfd-forms-app-src-pkg-<version>.zip`, disponible sur la Distribution logicielle.

Procédez comme suit pour télécharger le fichier `adobe-aemfd-forms-app-src-pkg-<version>.zip` :

1. Ouvrez la [Distribution de logiciels](https://experience.adobe.com/downloads). Vous avez besoin d’un Adobe ID pour vous connecter à la Distribution de logiciels.
1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** disponible dans le menu d’en-tête.
1. Dans le **[!UICONTROL Filtres]** section :
   1. Sélectionner **[!UICONTROL Forms]** de la **[!UICONTROL Solution]** liste déroulante.
   2. Sélectionnez la version et le type du package. Vous pouvez également utiliser l’option **[!UICONTROL Rechercher des téléchargements]** pour filtrer les résultats.
1. Appuyez sur le nom de package applicable à votre système d’exploitation, sélectionnez **[!UICONTROL Accepter les conditions du CLUF]**, puis appuyez sur **[!UICONTROL Télécharger]**.
1. Ouvrez [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.
1. Sélectionnez le package et cliquez sur **[!UICONTROL Installer]**.
1. Pour télécharger l’archive du code source, ouvrez **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** dans votre navigateur. Le fichier .zip de l’application Android est téléchargé sur votre appareil.
1. Extrayez le contenu du fichier .zip dans un dossier de votre système de fichiers local. Par exemple : *C:\Folder Structure\adobe-lc-mobileworkspace-src-2.4.20*

L’image suivante affiche la structure du dossier `adobe-lc-mobileworkspace-src-<version>.zip\android`.

![structure_dossier_zip_android](assets/zip_android_folder_structure.png)

## Définir les variables d’environnement {#set-environment-variable-android}

Définissez les variables d’environnement suivantes avant de démarrer le processus de création pour l’application AEM Forms :

* Définissez la variable d’environnement JAVA_HOME sur l’emplacement du logiciel JDK sur le système de fichiers local. Par exemple, C:\Program Files\Java\jdk1.8.0_181
* Définissez la variable d’environnement système `ANDROID_SDK_ROOT` sur l’emplacement du SDK pour Android. Par exemple, C:\Users\username\AppData\Local\Android\Sdk
* Définissez la variable d’environnement système `Path` pour inclure les outils de la plateforme et les emplacements de dossier d’outils pour Android. Par exemple, C:\Users\username\AppData\Local\Android\Sdk\platform-tools and C:\Users\username\AppData\Local\Android\Sdk\tools.

## Génération d’une application AEM Forms standard {#set-up-the-xcode-project}

Une fois que vous avez enregistré le fichier adobe-lc-mobileworkspace-src-&lt;version>.zip sur le système de fichiers local et défini les variables d’environnement, créez l’application Android AEM Forms standard à l’aide de l’une des options suivantes :

* [Génération de l’application AEM Forms à l’aide d’Android Studio](#using-android-studio)
* [Génération du fichier .apk à l’aide d’Android Studio](#generate-apk-android-studio)

### Générer l’application AEM Forms à l’aide d’Android Studio {#using-android-studio}

Effectuez les étapes suivantes pour créer une application AEM Forms à l’aide d’Android Studio :

1. Lancez l’application Android Studio sur votre ordinateur.
1. Cliquez sur **Ouvrir un projet Android Studio existant**. Si la boîte de dialogue pour ouvrir un projet existant ne s’affiche pas automatiquement, sélectionnez **Fichier** > **Ouvrir**.
1. Accédez à *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* sur le système de fichiers local et cliquez sur **OK**.

   L’option **android** s’affiche dans le volet de gauche.

   ![android_dossier_studio](assets/android_folder_studio.png)

1. Sélectionnez **Android** dans le volet de gauche, puis cliquez sur **Exécuter** > **Exécuter « Android »**.
1. Sélectionnez l’appareil Android dans la section Appareils connectés de la boîte de dialogue Sélectionner une cible de déploiement, puis cliquez sur OK.

   Une fois que vous avez généré l’environnement de développement, vous pouvez maintenant appliquer des personnalisations sur l’application. Utilisez les articles suivants pour personnaliser l’application :

   * [Personnalisation de l’identité graphique](/help/forms/using/branding-customization.md)
   * [Personnalisation du thème](/help/forms/using/theme-customization.md)
   * [Personnalisation de mouvement](/help/forms/using/gesture-customization.md)

   Après avoir appliqué les personnalisations appropriées à votre application, vous pouvez générer le fichier .apk à des fins de distribution.

### Générez le fichier .apk à l’aide d’Android Studio {#generate-apk-android-studio}

Exécutez les étapes suivantes pour générer le fichier .apk à l’aide d’Android Studio :

1. Lancez l’application Android Studio sur votre ordinateur.
1. Sélectionnez **Ouvrir un projet Android Studio existant**. Si la boîte de dialogue pour ouvrir un projet existant ne s’affiche pas automatiquement, sélectionnez **Fichier** > **Ouvrir**.
1. Accédez à *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* sur le système de fichiers local et cliquez sur **OK**.

   L’option android s’affiche dans le volet de gauche.

1. Sélectionnez **Générer** > **Générer APK** pour générer le fichier .apk.

   (Facultatif) Sélectionnez **Générer** > **Générer un APK signé** pour générer une [version signée](https://developer.android.com/studio/publish/app-signing) du fichier .apk.

## Utilisation d’Android Debug Bridge {#build-android-debug-bridge}

Une fois le fichier .apk généré, exécutez la commande suivante pour installer l’application sur un appareil Android en utilisant [Android Debug Bridge](https://developer.android.com/tools/help/adb.html).

**Utilisateurs de Windows :** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Utilisateurs de Mac :** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
