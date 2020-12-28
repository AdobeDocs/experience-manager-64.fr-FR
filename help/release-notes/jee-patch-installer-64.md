---
title: Programme d’installation des correctifs AEM Forms JEE
description: 'null'
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
translation-type: tm+mt
source-git-commit: 610e9a54adad3abdfecb8b2c4da67d677f75175e
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 47%

---


# Programme d’installation du correctif AEM Forms JEE {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Contactez le ](https://www.adobe.com/fr/account/sign-in.supportportal.html) support technique pour plus d&#39;informations ou pour obtenir le correctif.

## À propos du programme d’installation de correctif {#about-the-patch-installer}

Le programme d&#39;installation de correctif Forms JEE 6.4 AEM comprend tous les problèmes corrigés pour tous les composants de l&#39;AEM 6.4 Forms JEE disponibles jusqu&#39;à la sortie de ce correctif. Consultez les [Notes de mise à jour Cumulative Fix Pack](cfp-release-notes.md) les plus récentes pour obtenir une liste complète des problèmes résolus.

## Conditions préalables à l&#39;installation du correctif {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Installation et configuration du correctif {#installing-and-configuring-the-patch}

1. Effectuez une sauvegarde du dossier de déploiement &lt;*AEM_forms_root*>/. Il est nécessaire si vous décidez de désinstaller le Quick Fix.
1. Arrêtez le serveur d’applications.
1. Extrayez le fichier d&#39;archive du programme d&#39;installation du correctif sur votre disque dur.
1. Dans le répertoire, dont le nom dépend du système d’exploitation que vous utilisez :

   * ****
WindowsAccédez au répertoire approprié sur le support d&#39;installation ou le dossier de votre disque dur dans lequel vous avez copié le programme d&#39;installation, puis cliquez sur le doublon 
`aemforms64_cfp_install.exe` approuvé.

      * (Windows 32 bits) `Windows\Disk1\InstData\VM`
      * (Windows 64 bits) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX** Accédez au répertoire approprié, puis, à partir d’une invite de commande, saisissez 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Un assistant s’ouvre alors et vous guide tout au long de l’installation.

1. Dans le panneau Introduction, cliquez sur **[!UICONTROL Suivant]**.
1. Dans l’écran Choisir le répertoire d’installation, vérifiez que l’emplacement par défaut affiché correspond à votre installation ou cliquez sur **[!UICONTROL Parcourir]** pour sélectionner le dossier dans lequel AEM Forms est actuellement installé, puis cliquez sur **[!UICONTROL Suivant]**.

1. Lisez le résumé du correctif Quick Fix, puis cliquez sur **[!UICONTROL Suivant]**.
1. Lisez le résumé relatif à la pré-installation, puis cliquez sur **[!UICONTROL Installer]**. 
1. Une fois l’installation terminée, cliquez sur **[!UICONTROL Suivant]**pour appliquer les mises à jour de la correction rapide à vos fichiers installés.
1. [Windows ] uniquementEffectuez l&#39;une des étapes suivantes :

   * Désélectionnez l’option Démarrer Configuration Manager avant de cliquer sur Terminé. Exécutez Configuration Manager ultérieurement en utilisant le fichier `ConfigurationManager.bat` situé dans `[aem-forms root]\configurationManager\bin`. L&#39;utilisation de `ConfigurationManager.bat` permet d&#39;éviter la mise à jour manuelle du nom axis.jar dans les fichiers .lax.
   * Désélectionnez l’option Démarrer Configuration Manager avant de cliquer sur Terminé. Avant d’exécuter Configuration Manager à l’aide de **ConfigurationManager.exe** ou **ConfigurationManager_IPv6.exe**, accédez au répertoire *&lt;AEMForms_Install_Dir>\configurationManager\bin* et mettez à jour **axis.jar** vers **axis-1.4.1.4.1.1.1.4.1.1.1.1.4.1.1.1.1 1.jar** dans les fichiers suivants :

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Unix uniquement) La case à cocher Configuration Manager Début est activée par défaut. Cliquez sur **[!UICONTROL Terminé]** pour exécuter Configuration Manager.

   Pour exécuter Configuration Manager ultérieurement, désélectionnez l’option Démarrer Configuration Manager avant de cliquer sur Terminé. Vous pouvez début Configuration Manager ultérieurement à l’aide du script approprié dans le répertoire `[AEM_forms_root]/configurationManager/bin`.

1. En fonction de votre serveur d’applications, sélectionnez l’un des documents suivants et suivez les instructions de la section *Configuration et déploiement d’AEM Forms*.

   * [Installation et déploiement d’AEM Forms pour JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64_fr)
   * [Installation et déploiement d’AEM Forms pour WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64_fr)
   * [Installation et déploiement d’AEM Forms pour WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64_fr)

1. (JBoss uniquement) Après avoir installé le correctif et configuré le serveur, supprimez les répertoires tmp et work du serveur d’applications JBoss.

## Configurations après le déploiement {#post-deployment-configurations}

### Configurations SAML {#saml-configurations}

Si l’authentification SAML est configurée et que vous rencontrez des problèmes avec les métadonnées IDP volumineuses, procédez comme suit après l’installation du correctif :

1. Définissez la propriété système suivante dans votre serveur d’applications :\
   `um.saml.enable.large.xml=true`

1. Redémarrez le serveur.
1. Supprimez les fournisseurs d’authentification SAML existants et ajoutez-les à nouveau pour les domaines existants, comme décrit dans les paramètres SAML.

## Modules touchés {#impacted-modules}

* Services de document
* Protection des documents
* Foundation JEE
* Service PDFG

[Contacter le support technique](https://www.adobe.com/account/sign-in.supportportal.html)
