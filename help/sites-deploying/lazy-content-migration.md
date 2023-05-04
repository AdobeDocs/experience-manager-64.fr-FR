---
title: Migration différée du contenu
seo-title: Lazy Content Migration
description: Découvrez la migration différée du contenu dans AEM 6.4.
seo-description: Learn about Lazy Content Migration in AEM 6.4.
uuid: 9c84f7fe-31d3-4b63-8975-9e75a6c44b7d
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 282a828a-edb2-4643-9bf7-ec30c29dc6ce
feature: Upgrading
exl-id: 8dc2dfb8-037f-40ae-a962-ced89dd3fdd0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 18%

---

# Migration différée du contenu{#lazy-content-migration}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour des raisons de compatibilité descendante, de contenu et de configuration dans **/etc** et **/content** à partir d’AEM 6.3, ne sera pas modifié ni transformé immédiatement avec la mise à niveau. Cela permet de s’assurer que les dépendances des applications client sur ces structures restent intactes. Les fonctionnalités relatives à ces structures de contenu restent les mêmes même si le contenu d’une AEM 6.4 prête à l’emploi est hébergé à un autre endroit.

Bien que tous ces emplacements ne puissent pas être transformés automatiquement, quelques retards se produisent `CodeUpgradeTasks` également appelée migration différée du contenu. Cela permet aux utilisateurs de déclencher ces transformations automatiques en redémarrant l’instance avec cette propriété système :

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

De ce fait, les `CodeUpgradeTasks` seront exécutées pendant la migration.

Bien que l’objectif soit une exécution efficace, ce processus de mise à niveau est synchrone et s’accompagne donc d’un temps d’arrêt en fonction de la quantité de contenu à traiter. Il est recommandé d’évaluer les temps d’exécution dans un environnement intermédiaire avant un système de production afin de planifier une fenêtre de maintenance correspondante.

Comme cela nécessite généralement d’ajuster l’application, cette activité doit être effectuée avec le déploiement d’application correspondant.

Vous trouverez, ci-dessous, la liste complète des `CodeUpgradeTasks` introduites dans la version 6.4 :

| **Nom** | **Convient aux versions AEM antérieures à** | **Type de migration** | **Détails** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Immédiat |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Immédiat | Détecte toutes les `LiveRelationShips` de `VersionStorage` qui ont été supprimées et ajoute une propriété d’exclusion au parent. |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Immédiat | Restructuration des services cloud pour une configuration sécurisée par défaut |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Immédiat | Supprime la liaison basée sur la propriété de **/content** to **/conf** (remplacé par le mécanisme OSGi), génère la configuration OSGi correspondante. |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Immédiat | En raison de la gestion de merge_preserve, la règle de refus sécurisée par défaut remplace les autorisations données, ce qui entraîne la nécessité de procéder à une réorganisation lors de la mise à niveau. |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Immédiat | Détecte les composants qui utilisent le widget Html5SmartFile, recherche les utilisations du composant dans le contenu et restructure la persistance, déplaçant ainsi le binaire d’un niveau vers le bas et ne le stockant pas au niveau du composant. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Immédiat | Déplace les anciens projets de style de **/etc/projects** to **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Immédiat | Introduit un calque de conteneur dans la hiérarchie (Zones) et ajuste les références. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Immédiat | Définit des noms d’emplacement fixes pour les composants cibles. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Immédiat | Transformation complexe des modèles de workflow antérieurs à la version 6.2 des structures, instances et notifications, puis fusion à partir de l’emplacement de sauvegarde depuis **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Immédiat | Déplace les ressources, les schémas de métadonnées personnalisés et les profils de traitement depuis **/apps** to **/conf** et convertit les formulaires de profils de métadonnées et de schéma de métadonnées de coral2 à coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Immédiat | Déplace les ressources et les facettes de recherche personnalisées depuis **/apps** to **/conf** et convertit les formulaires de profils de métadonnées et de schéma de métadonnées de coral2 à coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Immédiat | Met à jour InboxItems pour l’ordre des éléments de boîte de réception (ajustement des métadonnées pour un tri efficace) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Immédiat | Ajuste la propriété metadataSchema sur le dossier en remplaçant les chemins relatifs par **/conf** à la place de **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Immédiat | Ajustement de la structure de navigation |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Immédiat | Déplace les configurations personnalisées des tableaux de bord de surveillance depuis **/libs** et **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Immédiat | Traduit la propriété processingProfile (utilisée jusqu’à la version 6.1) dans Assets afin de correspondre à la structure 6.3 et ultérieure. Ajuste également les chemins relatifs du profil à **/conf** à la place de **/apps**. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Immédiat | Tâche de mise à niveau qui supprime les entrées de menu obsolètes du CRXDE Lite et de la console web en cas de mise à niveau. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Différé | Déplacement des configurations cloud SRP, des configurations de mots-clés communautaires, nettoyage **/etc/social** et **/etc/enablement** (toutes les références et données doivent être ajustées lors de l’exécution de la migration différée ; aucune partie de l’application ne doit plus dépendre de cette structure). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Différé | Nettoie **/etc/cloudsettings** (contenant la configuration ContextHub). La configuration est automatiquement migrée lors du premier accès. Si la migration différée du contenu est lancée avec la mise à niveau de ce contenu dans **/etc/cloudsettings** doit être conservé via le package avant l&#39;upgrade et réinstallé pour que la transformation implicite entre en jeu, ainsi qu&#39;une désinstallation ultérieure du package après l&#39;achèvement. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Différé | Ajuste la structure de titre héritée au titre dans le noeud de profil utilisateur. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Différé | Migration du contenu commercial depuis **/etc/commerce** vers **/var/commerce**. Lors de la migration, le contenu est déplacé et les références au contenu déplacé sont mises à jour pour refléter le nouvel emplacement. |
