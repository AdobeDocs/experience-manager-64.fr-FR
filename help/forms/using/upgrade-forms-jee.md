---
title: Mise à niveau vers AEM 6.4 Forms
seo-title: Mise à niveau vers AEM 6.4 Forms
description: 'Vous pouvez effectuer une mise à niveau directe à partir de AEM 6.1 Forms, AEM 6.2 Forms et LiveCycle ES4 SP1 vers AEM 6.3 Forms. '
seo-description: 'Vous pouvez effectuer une mise à niveau directe à partir de AEM 6.1 Forms, AEM 6.2 Forms et LiveCycle ES4 SP1 vers AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Administrator
exl-id: e41eb0fa-ae88-44d5-9181-0d925b8b62c6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 80%

---

# Mise à niveau vers AEM 6.4 Forms on JEE {#upgrade-to-aem-forms-jee}

Utilisez l’un des chemins de mise à niveau suivants, selon votre environnement.

## AEM 6.2 Forms on JEE ou AEM 6.3 Forms on JEE vers AEM 6.4 Forms on JEE {#aem-forms-jee-62-63-to-64}

Effectuez la procédure suivante pour mettre à niveau AEM 6.2 Forms on JEE ou AEM 6.3 Forms on JEE vers AEM 6.4 Forms on JEE :

1. Téléchargez le programme d’installation d’AEM 6.4 Forms on JEE à partir du site [Adobe Licensing Website (LWS)](https://licensing.adobe.com/). Pour télécharger le programme d’installation, vous devez disposer d’un contrat de Maintenance &amp; Support.
1. Voir [Liste de contrôle et planification de la mise à niveau](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) pour en savoir plus sur les vérifications à effectuer pour garantir la réussite de la mise à niveau.
1. Voir [Préparation à la mise à niveau vers AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) pour découvrir et exécuter les tâches permettant de garantir que la mise à niveau s’exécute correctement, avec un temps d’arrêt du serveur minimal.
1. En fonction de votre environnement et de votre serveur d’application, sélectionnez l’un des documents suivants et suivez les instructions.

   * [Mise à niveau d’AEM 6.2 Forms ou d’AEM 6.3 Forms vers AEM 6.4 Forms pour JBoss](assets/upgrade-jboss.pdf)
   * [Mise à niveau d’AEM 6.2 Forms ou d’AEM 6.3 Forms vers AEM 6.4 Forms pour WebLogic](assets/upgrade-weblogic.pdf)
   * [Mise à niveau d’AEM 6.2 Forms ou d’AEM 6.3 Forms vers AEM 6.4 Forms pour WebSphere](assets/upgrade-websphere.pdf)
   * [Mise à niveau d’AEM 6.2 Forms ou d’AEM 6.3 Forms vers AEM 6.4 Forms pour JBoss clé en main](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms on JEE > AEM 6.3 Forms on JEE {#aem-forms-jee-60-to-63}

La mise à niveau directe de LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms vers la version 6.4 Forms n’est pas disponible. Vous pouvez effectuer une mise à niveau intermédiaire vers une ou plusieurs versions de LiveCycle ou AEM Forms, puis effectuer une mise à niveau à partir d’AEM 6.4 Forms. Pour la liste des versions intermédiaires et les instructions de mise à niveau correspondantes, voir [Sélectionner un chemin de mise à niveau](upgrade.md).

## LiveCycle ES4 SP1 vers AEM 6.4 Forms on JEE {#livecycle-es4sp1-forms-jee}

La mise à niveau de LiveCycle ES4 SP1 vers AEM 6.4 Forms on JEE est une mise à niveau dynamique qui migre les actifs et données des anciennes versions des serveurs d’applications, des systèmes d’exploitation et des bases de données pris en charge vers des instances récentes (nouvelles versions). 

Voici une présentation de la procédure de mise à niveau d’un serveur LiveCycle ES4 SP1 existant vers AEM 6.4 Forms. Pour des instructions détaillées, consultez les documents répertoriés à la fin de la procédure.

1. Avant la mise à niveau:

   1. Téléchargez le programme d’installation d’AEM 6.4 Forms on JEE à partir du site [Adobe Licensing Website (LWS)](https://licensing.adobe.com/). Pour télécharger le programme d’installation, vous devez disposer d’un contrat de Maintenance &amp; Support.
   1. Choisissez un type de référentiel de contenu (référentiel CRX) à utiliser. Seules quelques fonctionnalités AEM Forms on JEE utilisent la persistance du référentiel de contenu pour stocker le contenu et les actifs. Installez et configurez Content Repository uniquement si vous prévoyez d’utiliser les fonctionnalités d’AEM Forms on JEE suivantes :

      * Dans LiveCycle ES4 SP1, les fonctionnalités Correspondence Management, Forms Portal, HTML Workspace et Process Reporting utilisent le référentiel de contenu. Si vous n’avez pas utilisé ces fonctionnalités dans LiveCycle ES4 et envisagez de ne pas les utiliser dans AEM Forms, Content Repository n’est pas requis.
      * Dans AEM Forms, Adaptive Forms, Correspondence Management, HTML5 Forms (également appelé Mobile Forms dans LiveCycle ES4 SP1), Forms Portal, HTML Workspace, Process Reporting et les processus spécifiques à Forms on OSGi, les fonctionnalités utilisent le référentiel de contenu. Si vous prévoyez d’utiliser AEM Forms pour ces fonctionnalités, Content Repository est requis.
      * Vous n’avez pas besoin de Content Repository pour AEM Forms Document Security.

      De plus, le type de référentiel de LiveCycle et d’AEM Forms est différent. Pour connaître les types de référentiel disponibles et les informations connexes, reportez-vous à la section [Choix d’un type de persistance pour l’installation d’AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Créez une sauvegarde du contenu et des données LiveCycle ES4 SP1 :

      Créez une sauvegarde de la base de données LiveCycle ES4 SP1, du stockage de données global (GDS) et du référentiel crx (non requis pour la sécurité des documents). Si vous effectuez une mise à niveau vers la persistance MongoMK ou RDBMK, exportez les actifs de gestion de correspondance de LiveCycle ES4 SP1 dans un fichier .cmp et formatez les éléments en tant que package AEM.

   1. Déterminez si votre plateforme existante (serveur d’applications, base de données, système d’exploitation, Adobe Acrobat, applications tierces ou matériel) est prise en charge par AEM 6.4 Forms on JEE. Pour plus d’informations sur les logiciels et le matériel pris en charge, consultez le document [Combinaisons de plates-formes prises en charge](/help/forms/using/aem-forms-jee-supported-platforms.md).

      Si vous créez une nouvelle instance de la base de données, importez les données sauvegardées à l’étape 3 dans la base de données. Pour plus d’informations sur l’importation de données dans une base de données, voir la documentation du fournisseur de base de données correspondant.

      >[!NOTE]
      >
      >Si vous utilisez le format de persistance RDBMK, utilisez une base de données unique pour la persistance du référentiel et les services de document s’exécutant sur AEM Forms on JEE.


1. Mettre à niveau :

   1. Installez AEM 6.4 Forms on JEE sur un nouveau serveur en exécutant le programme d’installation. Le programme d’installation place tous les fichiers requis sur votre ordinateur dans une même arborescence d’installation.
   1. Une fois l’installation terminée, exécutez **Configuration Manager** pour configurer divers modules AEM Forms et définir les configurations appropriées. Avec la configuration des paramètres, il permet de spécifier le chemin du stockage de données global (GDS) et le référentiel crx.

      >[!NOTE]
      >
      >Sur l’écran Sélection de la tâche de mise à niveau, sélectionnez l’option **[!UICONTROL Mettre à niveau à partir d’Adobe Experience Manager Forms 6.2.0]** . L’option **[!UICONTROL Mise à niveau depuis Adobe Experience Manager Forms 6.2.0]** permet au gestionnaire de configuration de mettre à niveau LiveCycle ES4 SP1 vers AEM 6.4 Forms.

   1. (Non requis pour le module de sécurité des documents AEM Forms) Importez le contenu vers le référentiel de contenu (référentiel CRX) sur le serveur AEM 6.4 Forms.

      >[!NOTE]
      >
      >* Après la mise à niveau du référentiel crx et la migration du contenu, modifiez le mot de passe du compte administrateur. Pour des instructions détaillées, voir [Modification du mot de passe pour un utilisateur existant](/help/sites-administering/granite-user-group-admin.md).


1. Effectuez les tâches de post-déploiement pour vérifier les informations d’identification de connexion, configurer les services de document, la gestion de la correspondance, la sécurité des documents, etc. en fonction de votre cas d’utilisation.
1. Vérifiez que le serveur a été mis à niveau :

   Effectuez quelques opérations de routine sur le serveur AEM Forms mis à niveau pour vous assurer que le serveur a été mis à niveau. Vous pouvez remplir et soumettre quelques formulaires migrés ou protéger des documents pour assurer une mise à niveau réussie.

   >[!NOTE]
   >
   >Dans AEM 6.4 Forms, la structure du référentiel crx a changé. Après la mise à niveau vers AEM 6.4 Forms, utilisez les chemins d’accès modifiés pour la personnalisation que vous créez à nouveau. Pour la liste complète des chemins modifiés, voir [Restructuration du référentiel des formulaires dans AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**En fonction de votre environnement et de votre serveur d’applications, sélectionnez l’un des documents suivants et suivez les instructions détaillées :**

* [Mise à niveau de LiveCycle ES4 SP1 vers AEM 6.4 Forms pour JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Mise à niveau de LiveCycle ES4 SP1 vers AEM 6.4 Forms pour WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Mise à niveau de LiveCycle ES4 SP1 vers AEM 6.4 Forms pour WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Mise à niveau de LiveCycle ES4 SP1 vers AEM 6.4 Forms à l’aide de JBoss clé en main](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 vers AEM 6.4 Forms on JEE {#livecycle-es3-forms-jee}

La mise à niveau de LiveCycle ES3 vers AEM 6.4 Forms on JEE est une mise à niveau dynamique qui migre les actifs et données des anciennes versions des serveurs d’applications, des systèmes d’exploitation et des bases de données pris en charge vers des instances récentes (nouvelles versions). 

Voici une présentation de la procédure de mise à niveau d’un serveur LiveCycle ES3 existant vers AEM 6.4 Forms. Pour des instructions détaillées, consultez les documents répertoriés à la fin de la procédure.

1. Avant la mise à niveau:

   1. Téléchargez le programme d’installation d’AEM 6.4 Forms on JEE à partir du site [Adobe Licensing Website (LWS)](https://licensing.adobe.com/). Pour télécharger le programme d’installation, vous devez disposer d’un contrat de Maintenance &amp; Support.
   1. Choisissez un type de référentiel de contenu (référentiel CRX) à utiliser. Seules quelques fonctionnalités AEM Forms on JEE utilisent la persistance du référentiel de contenu pour stocker le contenu et les actifs. Installez et configurez Content Repository uniquement si vous prévoyez d’utiliser les fonctionnalités d’AEM Forms on JEE suivantes :

      * Dans AEM Forms, Adaptive Forms, Correspondence Management, HTML5 Forms, Forms Portal, HTML Workspace, Process Reporting et Forms centric workflows on OSGi, les fonctionnalités utilisent le référentiel de contenu. Si vous prévoyez d’utiliser AEM Forms pour ces fonctionnalités, Content Repository est requis.
      * Vous n’avez pas besoin de Content Repository pour AEM Forms Document Security.

      De plus, le type de référentiel de LiveCycle et d’AEM Forms est différent. Pour connaître les types de référentiel disponibles et les informations connexes, reportez-vous à la section [Choix d’un type de persistance pour l’installation d’AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Créez une sauvegarde de la base de données LiveCycle ES3, du stockage global de données et du référentiel de contenu (non requis pour Document Security). Si vous effectuez une mise à niveau vers la persistance MongoMK ou RDBMK, exportez les actifs de gestion de correspondance de LiveCycle ES3 en tant qu’archive.
   1. Déterminez si votre plateforme existante (serveur d’applications, base de données, système d’exploitation, Adobe Acrobat, applications tierces ou matériel) est prise en charge par AEM 6.4 Forms on JEE. Pour plus d’informations sur les logiciels et le matériel pris en charge, consultez le document [Combinaisons de plates-formes prises en charge](/help/forms/using/aem-forms-jee-supported-platforms.md).

      Si vous créez une nouvelle instance de la base de données, importez les données sauvegardées à l’étape 3 dans la base de données. Pour plus d’informations sur l’importation de données dans une base de données, voir la documentation du fournisseur de base de données correspondant.

      >[!NOTE]
      >
      >Si vous utilisez le format de persistance RDBMK, utilisez une base de données unique pour la persistance du référentiel et les services de document s’exécutant sur AEM Forms on JEE.


1. Mettre à niveau :

   1. Installez AEM 6.4 Forms on JEE sur un nouveau serveur en exécutant le programme d’installation. Le programme d’installation place tous les fichiers requis sur votre ordinateur dans une même arborescence d’installation.
   1. Une fois l’installation terminée, exécutez **Configuration Manager** pour configurer divers modules AEM Forms et définir les configurations appropriées. Avec la configuration des paramètres, il permet de spécifier le chemin du stockage de données global (GDS) et le référentiel crx.

      >[!NOTE]
      >
      >Sur l’écran Sélection de la tâche de mise à niveau, sélectionnez l’option **[!UICONTROL Mettre à niveau à partir d’Adobe Experience Manager Forms 6.2.0]** . L’option **[!UICONTROL Mise à niveau depuis Adobe Experience Manager Forms 6.2.0]** permet au gestionnaire de configuration de mettre à niveau LiveCycle ES3 vers AEM 6.4 Forms.

   1. (Non requis pour le module de sécurité des documents AEM Forms) Mettez à niveau et importez le référentiel CRX vers le serveur AEM 6.4 Forms.

      >[!NOTE]
      >
      >Après la mise à niveau du référentiel crx et la migration du contenu, modifiez le mot de passe du compte administrateur. Pour des instructions détaillées, voir [Modification du mot de passe pour un utilisateur existant](/help/sites-administering/granite-user-group-admin.md).
1. Effectuez les tâches de post-déploiement pour vérifier les informations d’identification de connexion, configurer les services de document, la gestion de la correspondance, la sécurité des documents, etc. en fonction de votre cas d’utilisation.
1. Vérifiez que le serveur a été mis à niveau :

   Effectuez quelques opérations de routine sur le serveur AEM Forms mis à niveau pour vous assurer que le serveur a été mis à niveau. Vous pouvez remplir et soumettre quelques formulaires migrés ou protéger des documents pour assurer une mise à niveau réussie.

   >[!NOTE]
   >
   >Dans AEM 6.4 Forms, la structure du référentiel crx a changé. Après la mise à niveau vers AEM 6.4 Forms, utilisez les chemins d’accès modifiés pour la personnalisation que vous créez à nouveau. Pour la liste complète des chemins modifiés, voir [Restructuration du référentiel des formulaires dans AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**En fonction de votre environnement et de votre serveur d’applications, sélectionnez l’un des documents suivants et suivez les instructions détaillées :**

* [Mise à niveau de LiveCycle ES3 vers AEM 6.4 Forms pour JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Mise à niveau de LiveCycle ES3 vers AEM 6.4 Forms pour WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Mise à niveau de LiveCycle ES3 vers AEM 6.4 Forms pour WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Mise à niveau de LiveCycle ES3 vers AEM 6.4 Forms à l’aide de JBoss clé en main](assets/upgrade-turnkey-livecycle-es3.pdf)
