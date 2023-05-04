---
title: Programme d’installation du correctif JEE AEM Forms
description: Programme d’installation du correctif JEE AEM Forms
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
exl-id: ce5300ce-03f4-4e7b-bc5b-01a9968ebe06
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 69%

---

# Programme d’installation du correctif JEE AEM Forms {#aem-forms-jee-patch-installer}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>[Contactez l’assistance technique](https://www.adobe.com/account/sign-in.supportportal.html) pour plus d’informations ou pour obtenir le correctif.

## À propos du programme d’installation du correctif {#about-the-patch-installer}

Le programme d’installation du correctif JEE AEM 6.4 Forms comprend tous les problèmes résolus pour tous les composants JEE d’AEM 6.4 Forms disponibles jusqu’à la publication de ce correctif. Consultez la dernière version  [Notes de mise à jour Cumulative Fix Pack](cfp-release-notes.md) pour obtenir une liste complète des problèmes résolus.

## Prérequis pour installer le correctif {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Installation et configuration du correctif {#installing-and-configuring-the-patch}

1. Effectuez une sauvegarde du dossier de déploiement &lt;*AEM_forms_root*>/. Cela est nécessaire si vous décidez de désinstaller le Quick Fix.
1. Arrêtez le serveur d’applications.
1. Extrayez le fichier d’archive du programme d’installation de correctif sur votre disque dur.
1. Dans le répertoire, dont le nom dépend du système d’exploitation que vous utilisez :

   * **Windows**


Accédez au répertoire approprié sur le support ou dossier d’installation de votre disque dur dans lequel le programme d’installation a été copié, puis cliquez deux fois sur le fichier 
`aemforms64_cfp_install.exe`.

      * (Windows 32 bits) `Windows\Disk1\InstData\VM`
      * (Windows 64 bits) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX**
Accédez au répertoire approprié, puis, à l’invite de commande, saisissez 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Vous lancez ainsi un assistant d’installation qui vous guide tout au long de l’installation.

1. Dans l’écran d’introduction, cliquez sur **[!UICONTROL Suivant]**.
1. Dans l’écran Choisir le répertoire d’installation, vérifiez que l’emplacement par défaut affiché correspond à votre installation ou cliquez sur **[!UICONTROL Parcourir]** pour sélectionner le dossier dans lequel AEM Forms est actuellement installé, puis cliquez sur **[!UICONTROL Suivant]**.

1. Lisez le résumé du correctif Quick Fix, puis cliquez sur **[!UICONTROL Suivant]**.
1. Lisez le résumé relatif à la pré-installation, puis cliquez sur **[!UICONTROL Installer]**.
1. Une fois l’installation terminée, cliquez sur **[!UICONTROL Suivant]**pour appliquer les mises à jour de Quick Fix à vos fichiers installés.
1. [Windows uniquement] Effectuez l’une des étapes suivantes :

   * Désélectionnez l’option Démarrer le gestionnaire de configuration avant de cliquer sur Terminé. Exécutez Configuration Manager ultérieurement à l’aide de la méthode `ConfigurationManager.bat` fichier situé dans `[aem-forms root]\configurationManager\bin`. Utilisation `ConfigurationManager.bat` vous permet d’éviter la mise à jour manuelle du nom axis.jar dans les fichiers .lax .
   * Désélectionnez l’option Démarrer le gestionnaire de configuration avant de cliquer sur Terminé. Avant d’exécuter Configuration Manager à l’aide de **ConfigurationManager.exe** ou **ConfigurationManager_IPv6.exe**, accédez à *&lt;aemforms_install_dir>\configurationManager\bin* répertoire et mise à jour **axis.jar** to **axis-1.4.1.1.jar** dans les fichiers suivants :

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Unix uniquement) La case à cocher Démarrer Configuration Manager est sélectionnée par défaut. Cliquez sur **[!UICONTROL Terminé]** pour exécuter le gestionnaire de configuration.

   Pour exécuter Configuration Manager ultérieurement, désélectionnez l’option Démarrer le gestionnaire de configuration avant de cliquer sur Terminé. Vous pourrez démarrer le gestionnaire de configuration ultérieurement à l’aide du script approprié dans le répertoire `[AEM_forms_root]/configurationManager/bin`.

1. En fonction de votre serveur d’applications, sélectionnez l’un des documents suivants et suivez les instructions de la section *Configuration et déploiement d’AEM Forms*.

   * [Installation et déploiement d’AEM Forms pour JBoss](https://www.adobe.com/go/learn_aemforms_installJBoss_64_fr)
   * [Installation et déploiement d’AEM Forms pour WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64_fr)
   * [Installation et déploiement d’AEM forms pour WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64_fr)

1. (JBoss uniquement) Après avoir installé le correctif et configuré le serveur, supprimez les répertoires tmp et work du serveur d’applications JBoss.

## Configurations après le déploiement {#post-deployment-configurations}

### Configurations SAML {#saml-configurations}

Si l’authentification SAML est configurée et que vous rencontrez des problèmes avec des métadonnées IDP volumineuses, procédez comme suit après l’installation du correctif :

1. Définissez la propriété système suivante dans votre serveur d’applications :\
   `um.saml.enable.large.xml=true`

1. Redémarrez le serveur.
1. Supprimez les fournisseurs d’authentification SAML existants et ajoutez-les à nouveau pour les domaines existants, comme décrit dans les paramètres SAML.

## Modules touchés {#impacted-modules}

* Document Services
* Document Security
* Foundation JEE
* Service PDFG

[Contacter le support technique](https://www.adobe.com/account/sign-in.supportportal.html)
