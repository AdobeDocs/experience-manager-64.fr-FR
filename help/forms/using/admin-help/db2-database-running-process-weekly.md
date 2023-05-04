---
title: "Base de données DB2\_: exécution d’un processus hebdomadaire"
seo-title: "DB2 database: Running a process weekly"
description: Découvrez comment vous pouvez améliorer la performance de votre base de données AEM Forms DB2.
seo-description: See how you can improve the performance of your AEM forms DB2 database.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
exl-id: f40fcfab-63e0-4e43-aac5-95426e3dd1fb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 25%

---

# Base de données DB2 : exécution d’un processus hebdomadaire{#db-database-running-a-process-weekly}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Si votre base de données AEM forms DB2 commence à s’exécuter lentement, l’exécution hebdomadaire du processus suivant peut améliorer ses performances :

1. Démarrez DB2 Control Center :

   (Windows) Sélectionnez Démarrer > Programmes > IBM DB2 > General Administration Tools > Control Center.

   (Linux et UNIX) Ouvrez une invite de commande et saisissez la commande `db2jcc`.

1. Dans l’arborescence d’objets DB2 Control Center, cliquez sur All Databases.
1. Cliquez sur la base de données que vous avez créée pour AEM forms et cliquez sur le dossier Tables .
1. Sélectionnez toutes les tables de base de données dans le volet de contenu, cliquez dessus avec le bouton droit et sélectionnez Exécuter les statistiques.
1. Accédez à Statistiques > Statistiques des index.
1. Sélectionnez Collecter des statistiques pour tous les index, puis Collecter des statistiques pour les index avec des statistiques détaillées étendues et cliquez sur OK.

Un message s’affiche une fois le processus terminé. Fermez le message.
