---
title: Configuration du projet Visual Studio et création d’une application Windows
seo-title: Set up the Visual Studio project and build the Windows app
description: Découvrez comment configurer un projet Visual Studio pour créer l’application pour périphérique mobile AEM Forms Windows.
seo-description: Learn how to set up a Visual Studio project to build the AEM Forms Windows mobile device app.
uuid: 0a72387a-d920-4f66-8983-d500ef0ecd90
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 85048fe4-ca1b-41fa-8e19-6eeb8dd09962
exl-id: ae0463de-271f-47c0-b947-f6d149ded8ab
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 53%

---

# Configuration du projet Visual Studio et création d’une application Windows {#set-up-the-visual-studio-project-and-build-the-windows-app}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM Forms fournit le code source complet de l’application AEM Forms. La source contient tous les composants nécessaires pour générer une application d’espace de travail personnalisée. L’archive du code source `adobe-lc-mobileworkspace-src-<version>.zip` fait partie du package `adobe-aemfd-forms-app-src-pkg-<version>.zip` dans la distribution de logiciels.

Pour obtenir le code source de l’application AEM Forms, procédez comme suit :

1. Ouvrez la [Distribution de logiciels](https://experience.adobe.com/downloads). Vous avez besoin d’un Adobe ID pour vous connecter à la Distribution de logiciels.
1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** disponible dans le menu d’en-tête.
1. Dans le **[!UICONTROL Filtres]** section :
   1. Sélectionner **[!UICONTROL Forms]** de la **[!UICONTROL Solution]** liste déroulante.
   2. Sélectionnez la version et le type du package. Vous pouvez également utiliser l’option **[!UICONTROL Rechercher des téléchargements]** pour filtrer les résultats.
1. Appuyez sur le nom de package applicable à votre système d’exploitation, sélectionnez **[!UICONTROL Accepter les conditions du CLUF]**, puis appuyez sur **[!UICONTROL Télécharger]**.
1. Ouvrez [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.
1. Sélectionnez le package et cliquez sur **[!UICONTROL Installer]**.

1. Pour télécharger l’archive du code source, ouvrez `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` dans votre navigateur.

   Le package source est téléchargé sur votre périphérique.

L’image suivante affiche le contenu extrait du fichier`adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content-2](assets/mws-content-2.png)

L’image suivante affiche la structure du répertoire dans le dossier `windows` dans le dossier `src`.

![win-dir](assets/win-dir.png)

## Configuration de l’environnement {#setting-up-the-environment}

Pour les périphériques Windows, vous avez besoin des éléments suivants :

* Microsoft Windows 8.1 ou Windows 10
* Microsoft Visual Studio 2015
* Outils Visual Studio Microsoft pour Apache Cordova

## Configuration du projet Visual Studio pour l’application AEM Forms {#setting-up-visual-studio-project-for-aem-forms-app}

Effectuez les étapes suivantes pour configurer le projet d’application AEM Forms dans Visual Studio.

1. Copiez l’archive `adobe-lc-mobileworkspace-src-<version>.zip` du dossier `%HOMEPATH%\Projects` dans le périphérique utilisant Windows 8.1 ou Windows 10 avec Visual Studio 2015 installé et configuré.
1. Extrayez l’archive dans le répertoire `%HOMEPATH%\Projects\MobileWorkspace`.
1. Accédez au répertoire `%HOMEPATH%\Projects\MobileWorkspace\adobe-lc-mobileworkspace-src-[versionsrc]\windows`.
1. Ouvrez le fichier `CordovaApp.sln` à l’aide de Visual Studio 2015 et continuez à créer l’application AEM Forms.

## Création de l’application AEM Forms {#build-aem-forms-app}

Effectuez les étapes suivantes pour créer et déployer l’application AEM Forms.

>[!NOTE]
>
>Les données stockées sur le système de fichiers Windows de l’application AEM Forms ne sont pas chiffrées. Nous vous recommandons d’utiliser un outil tiers comme Windows BitLocker Drive Encryption pour chiffrer des données du disque.

1. Dans la barre d’outils standard de Visual Studio, sélectionnez **Version** dans le menu déroulant du mode de création. 

1. Sélectionnez Windows-AnyCPU, Windows-x64 ou Windows-x86 en fonction de votre plateforme. Windows-AnyCPU est recommandé.
1. Dans Visual Studio Solution Explorer, effectuez un clic droit sur le projet **CordovaApp.Windows** et sélectionnez **Store > Créer des packages d’application**.

   ![createapppackages](assets/createapppackages.png)

   L’assistant Créer des packages d’application s’affiche.

   Le fichier d’installation CordovaApp.Windows_3.0.2.0_anycpu.appx est créé dans le répertoire platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test.

   Si vous rencontrez l’erreur `Retarget to windows 8.1 required`, faites un clic droit sur l’erreur et sélectionnez **Recibler vers Windows 8.1** dans le menu contextuel.

   ![retarget-solution](assets/retarget-solution.png)

1. Dans l’assistant Créer des packages d’application, indiquez si vous souhaitez charger votre application dans Windows Store, puis cliquez sur **Suivant**.

   ![createapppackageswizard1](assets/createapppackageswizard1.png)

1. Effectuez les modifications dans les paramètres, tels que la version et l’emplacement de sortie de la build de l’application, selon les besoins.

   ![createapppackageswizard2](assets/createapppackageswizard2.png)

1. Une fois le projet créé, vous pouvez installer l’application à l’aide des éléments suivants :

   * Windows PowerShell
   * Visual Studio

   Le package `.appx` nécessite les éléments suivants pour s’installer correctement :

   1. Bibliothèque WinJS
   1. Assurez-vous que le package s’accompagne d’un certificat auto-signé ou qu’une autorité de confiance a signé un certificat public tel que VeriSign.
   1. Licence de développeur

   Le répertoire Platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test contient les quatre principaux composants :

   1. `.appx` approuvé
   1. Certificat (il s’agit actuellement d’un certificat signé Apache Cordova)
   1. Dossier de dépendance
   1. Fichier PowerShell (extension .ps1)



## Déploiement d’une application à l’aide de Windows PowerShell {#deploying-an-app-using-windows-powershell}

Il existe deux manières d’installer l’application sur un périphérique Windows.

### Via l’acquisition d’une licence développeur {#by-acquiring-the-developer-license}

1. Effectuez un clic droit sur le fichier PowerShell `Add-AppDevPackage.ps1)` et sélectionnez **Exécuter avec PowerShell**.

1. La configuration vous invite à obtenir une licence de développeur. Utilisez les informations d’identification du compte Microsoft pour acquérir une licence de développeur.

   Cette licence est valable pendant 30 jours et peut être renouvelée gratuitement.

1. Lorsque vous acquérez la licence de développeur, la configuration installe le certificat auto-signé sur le système et l’application s’installe correctement.

### En utilisant des périphériques d’entreprise {#by-using-enterprise-owned-devices}

Pour les périphériques d’entreprise connectés au domaine de l’entreprise, l’acquisition d’une licence de développeur n’est pas requise.

Les périphériques d’entreprise utilisent les éditions Professional et Enterprise de Windows.

Microsoft vous recommande d’installer un certificat public émis par une autorité de confiance, tel que VeriSign.

Pour déployer l’application :

* Assurez-vous que le périphérique est connecté au domaine de l’entreprise.
* Activez le paramètre de stratégie de groupe.

**Pour activer le paramètre de stratégies de groupe :** 

1. Sur votre appareil, exécutez `gpedit.msc`.
1. Accédez à **Configuration de l’ordinateur > Modèles d’administration > Composant Windows > Déploiement du module d’application**.
1. Cliquez avec le bouton droit de la souris sur **Autoriser l’installation de toutes les applications approuvées**.
1. Cliquez sur **Modifier** et sélectionnez **Activé**.

1. Cliquez sur **OK**.

Modifiez le script PowerShell généré par Visual Studio pour l’empêcher d’acquérir la licence de développeur.

Dans le script de PowerShell, définissez la variable `$NeedDeveloperLicense = $false`.

Pour les appareils qui ne sont pas connectés au domaine, une clé d’activation de produit de chargement latéral est requise. Vous pouvez l’acheter auprès d’un revendeur Windows.

Pour l’édition d’accueil de Windows 8.1, il n’existe aucune stratégie de groupe, le chargement latéral d’entreprise n’est pas autorisé et vous ne pouvez pas le joindre au domaine d’entreprise. Déployez l’application sur un appareil Windows 8.1 Home Edition à l’aide de la licence de développeur.

Pour plus d’informations, cliquez sur [here](https://blogs.msdn.com/b/mvpawardprogram/archive/2014/03/24/side-loading-deployment-of-windows-store-apps-in-enterprises-step-by-step.aspx).

## Déploiement d’une application à l’aide de Visual Studio {#deploying-an-app-using-visual-studio}

Pour installer l’application sous Windows à l’aide de Visual Studio :

1. Connectez le périphérique à l’aide du débogueur à distance.

   Pour plus d’informations, voir [Exécution d’applications Windows Store sur un ordinateur distant](https://docs.microsoft.com/fr-fr/visualstudio/debugger/run-windows-store-apps-on-a-remote-machine).

1. Lorsque votre application est ouverte dans Visual Studio, sélectionnez Windows-x64, Windows-x86 ou Windows-AnyCPU dans la liste Plateformes de solution, puis sélectionnez **Machine distante**.
1. Votre application est déployée sur l’ordinateur distant.
