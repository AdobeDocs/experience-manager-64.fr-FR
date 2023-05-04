---
title: "Base de données IBM DB2\_: exécution des commandes pour des opérations de maintenance standard"
seo-title: "IBM DB2 database: Running commands for regular maintenance"
description: Ce document répertorie les commandes IBM DB2 recommandées dans le cadre des opérations de maintenance standard de votre base de données AEM Forms.
seo-description: This document lists IBM DB2 commands that are recommended for regular maintenance of your AEM forms database.
uuid: 235d59df-b9b9-4770-8b7d-00713701c3c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a62b68b4-7735-49b1-8938-f0d9e4c4a051
exl-id: b4877c24-3450-44b6-adcd-78a694b28857
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 63%

---

# Base de données IBM DB2 : exécution des commandes pour des opérations de maintenance standard {#ibm-db-database-running-commands-for-regular-maintenance}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les commandes IBM DB2 suivantes sont recommandées pour une maintenance régulière de votre base de données forms AEM. Pour plus d’informations sur la maintenance et l’optimisation des performances de votre base de données DB2, voir *Guide d’administration d’IBM DB2*.

* **runstats :** cette commande met à jour les statistiques décrivant les caractéristiques physiques d’une table de base de données et des index associés. Les instructions SQL dynamiques générées par AEM forms utilisent automatiquement ces statistiques mises à jour, mais pour les instructions SQL statiques intégrées à une base de données, l’instruction `db2rbind` doit également être exécutée.
* **db2rbind :** cette commande recrée les liaisons de tous les packages dans la base de données. Utilisez cette commande après avoir exécuté l’utilitaire `runstats` pour revalider tous les packages dans la base de données.
* **reorg table ou index :** cette commande vérifie si une réorganisation de certains index et de certaines tables est nécessaire.

   Au fur et à mesure que vos bases de données se développent et changent, il est essentiel de recalculer les statistiques tabulaires pour améliorer les performances des bases de données et cela doit être fait régulièrement. Ces commandes peuvent être exécutées manuellement à l’aide de scripts ou d’une tâche cron.

>[!NOTE]
>
>avant d’exécuter la commande `runstats`, la base de données doit être alimentée et au moins une synchronisation de répertoires doit avoir été effectuée.

Pour une base de données de petite taille, par exemple 10 000 utilisateurs ou 2 500 groupes, il suffit d’appeler la commande `runstats` pour réduire les délais de synchronisation.

Pour les bases de données plus volumineuses, par exemple 100 000 utilisateurs ou 10 000 groupes, exécutez la commande `reorg` avant la commande `runstats`.

## Utilisation de la commande runstats sur la base de données AEM forms {#use-the-runstats-command-on-your-aem-forms-database}

Exécutez la commande `runstats` sur les tables et index de base de données AEM forms suivants.

>[!NOTE]
>
>la commande `runstats` ne doit être exécutée que lors de la première synchronisation de base de données. Toutefois, il doit être exécuté deux fois pendant ce processus : une fois lors de la synchronisation des utilisateurs et des groupes, puis lors de la synchronisation des membres du groupe. Assurez-vous que le script s’exécute complètement chaque fois que vous l’exécutez.

Pour une syntaxe et une utilisation correctes, consultez la documentation du fabricant de la base de données. Ci-dessous, `<schema>` représente le schéma associé à votre nom d’utilisateur DB2. Si vous disposez d’une installation DB2 par défaut simple, il s’agit du nom du schéma de base de données.

```as3
     TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALGROUPENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY FOR INDEXES ALL
```

## Exécution de la commande reorg sur votre base de données AEM forms {#run-the-reorg-command-on-your-aem-forms-database}

Exécutez la commande `reorg` sur les tables et index de base de données AEM forms suivants. Pour une syntaxe et une utilisation correctes, consultez la documentation du fabricant de la base de données.

```as3
     TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
```
