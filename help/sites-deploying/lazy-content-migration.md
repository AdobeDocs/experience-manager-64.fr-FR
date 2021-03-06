---
title: Migration différée du contenu
seo-title: Lazy Content Migration
description: En savoir plus sur la migration différée du contenu dans AEM 6.4.
seo-description: Learn about Lazy Content Migration in AEM 6.4.
uuid: 9c84f7fe-31d3-4b63-8975-9e75a6c44b7d
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 282a828a-edb2-4643-9bf7-ec30c29dc6ce
feature: Upgrading
exl-id: 8dc2dfb8-037f-40ae-a962-ced89dd3fdd0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 93%

---

# Migration différée du contenu{#lazy-content-migration}

Dans un souci de compatibilité descendante, le contenu et les données de configuration sous **/etc** et **/content**, à partir d’AEM 6.3, ne sont ni affectés ni transformés juste après la mise à niveau. L’objectif est de garder intactes les dépendances des applications clientes sur ces structures. La fonctionnalité relative à ces structures de contenu reste la même, même si le contenu d’une version prête à l’emploi d’AEM 6.4 est hébergé à un autre endroit.

Bien que ces emplacements ne soient pas tous transformés automatiquement, il existe quelques `CodeUpgradeTasks` différées ; ce que l’on désigne sous le nom de migration différée du contenu. Cela permet aux clients de déclencher ces transformations automatiques en redémarrant l’instance avec cette propriété système :

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

De ce fait, les `CodeUpgradeTasks` seront exécutées pendant la migration.

Bien que l’objectif de l’opération soit une mise en œuvre efficace, cette mise à niveau est un processus synchrone qui s’accompagne donc d’une période d’indisponibilité qui varie en fonction du volume de contenu qui doit être traité. Il est conseillé d’évaluer les temps d’exécution dans un environnement de déploiement avant de passer à un système de production afin de planifier une fenêtre de maintenance en conséquence.

Étant donné que cette activité nécessite généralement le réglage de l’application, elle doit être effectuée parallèlement au déploiement d’applications correspondant.

Vous trouverez, ci-dessous, la liste complète des `CodeUpgradeTasks` introduites dans la version 6.4 :

| **Nom** | **Convient aux versions AEM antérieures à** | **Type de migration** | **Détails** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Immédiat |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Immédiat | Détecte toutes les `LiveRelationShips` de `VersionStorage` qui ont été supprimées et ajoute une propriété d’exclusion au parent. |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Immédiat | Restructure les services cloud pour une configuration sécurisée par défaut. |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Immédiat | Supprime la liaison basée sur la propriété entre **/content** et **/conf** (remplacée par le mécanisme OSGi) et génère la configuration OSGi correspondante. |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Immédiat | En raison du traitement de merge_preserve, la règle de refus « sécurisé par défaut » écrase les autorisations données, ce qui rend nécessaire une réorganisation lors de la mise à niveau. |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Immédiat | Détecte les composants qui utilisent le widget Html5SmartFile, recherche les utilisations du composant dans le contenu et restructure la persistance, abaissant ainsi le fichier binaire d’un niveau, sans le stocker au niveau du composant. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Immédiat | Déplace les projets de style précédent de **/etc/projects** vers **/content/projects**. |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Immédiat | Introduit un calque de conteneur dans la hiérarchie (Areas) et ajuste les références. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Immédiat | Définit des noms d’emplacement fixes sur les composants cibles. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Immédiat | Transformation complexe des modèles de workflow avec antidatage des instances, notifications et structures 6.2, suivie de la fusion depuis l’emplacement de secours à partir de **/var/backup**. |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Immédiat | Déplace des ressources, des schémas de métadonnées personnalisés et des profils de traitement depuis **/apps** vers **/conf**, et convertit les formulaires de profils de métadonnées et de schémas de métadonnées coral2 au format coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Immédiat | Déplace des ressources et des facettes de recherche personnalisées depuis **/apps** vers **/conf**, et convertit les formulaires de profils de métadonnées et de schémas de métadonnées coral2 au format coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Immédiat | Met à jour InboxItems pour le classement des éléments de la boîte de réception (réglage des métadonnées pour un tri efficace) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Immédiat | Modifie la propriété metadataSchema sur le dossier en définissant les chemins d’accès relatifs sur **/conf** au lieu de **/apps**. |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Immédiat | Modifie la structure de navigation. |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Immédiat | Déplace les configurations personnalisées pour les tableaux de bord de contrôle depuis **/libs** et **/apps**. |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Immédiat | Convertit la propriété processingProfile (utilisée jusqu’à la version 6.1) dans Assets afin de la faire correspondre à la structure 6.3 ou ultérieure. Modifie également les chemins d’accès relatifs du projet sur **/conf** au lieu de **/apps**.  |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Immédiat | Tâche de mise à niveau qui supprime les entrées de menu obsolètes de CRXDE Lite et de la console web dans le cas d’une mise à niveau. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Différé | Déplace les configurations cloud SRP et les configurations de mots-clés communautaires, nettoie **/etc/social** et **/etc/enablement** (toutes les références et données, le cas échéant, doivent être modifiées lors de l’exécution de la migration différée ; plus aucune partie de l’application ne doit désormais dépendre de cette structure). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Différé | Nettoie **/etc/cloudsettings** (contenant la configuration ContextHub). La migration de la configuration est effectuée automatiquement lors du premier accès. Si la migration différée du contenu est lancée avec la mise à niveau, le contenu de **/etc/cloudsettings** doit être conservé via le package avant la mise à niveau et réinstallé pour que la transformation implicite soit lancée, avec une désinstallation ultérieure du package une fois la procédure terminée. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Différé | Définit la structure de titre héritée sur le titre du nœud de profil utilisateur. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Différé | Migration du contenu commercial depuis **/etc/commerce** to **/var/commerce**. Lors de la migration, le contenu est déplacé et les références au contenu déplacé sont mises à jour pour refléter le nouvel emplacement. |
