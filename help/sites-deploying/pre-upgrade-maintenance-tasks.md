---
title: Tâches de maintenance avant la mise à niveau
seo-title: Pre-Upgrade Maintenance Tasks
description: Découvrez les tâches préalables à la mise à niveau dans AEM.
seo-description: Learn about the pre-upgrade tasks in AEM.
uuid: 6c0d4b31-6464-470b-9e40-1fc2abb9b2a6
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 899ea120-c96d-4dbf-85da-e5d25959d10a
feature: Upgrading
exl-id: f146cb2f-ee77-4c99-8dff-446cdb3a7797
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2204'
ht-degree: 47%

---

# Tâches de maintenance avant la mise à niveau{#pre-upgrade-maintenance-tasks}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Avant de commencer la mise à niveau, il est important de suivre ces tâches de maintenance pour vous assurer que le système est prêt et peut être restauré en cas de problème :

* [Vérification de la disponibilité de l’espace disque nécessaire](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Sauvegarde complète d’AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Sauvegarde des modifications sur /etc](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#backup-changes-etc)
* [Génération du fichier quickstart.properties](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Configuration de la purge du workflow et du journal d’audit](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Installation, configuration et exécution des tâches précédant la mise à niveau](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Désactivation des modules de connexion personnalisés](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-login-modules)
* [Suppression des mises à jour du répertoire /install](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Arrêt de toutes les instances Cold Standby](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Désactivation des tâches planifiées personnalisées](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Exécution d’un nettoyage des révisions hors ligne](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Exécution de la récupération de l’espace mémoire du magasin de données](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Mise à niveau du schéma de base de données si nécessaire](pre-upgrade-maintenance-tasks.md#upgrade-the-database-schema-if-needed)
* [Suppression des utilisateurs susceptibles d’entraver la mise à niveau](pre-upgrade-maintenance-tasks.md#delete-users-that-might-hinder-the-upgrade)
* [Rotation des fichiers journaux](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Vérification de la disponibilité de l’espace disque nécessaire {#ensure-sufficient-disk-space}

Lors de l’exécution de la mise à niveau, en plus des activités de mise à niveau de contenu et de code, une migration du référentiel doit être effectuée. La migration crée une copie du référentiel au nouveau format Segment Tar. Par conséquent, vous aurez besoin de suffisamment d’espace disque pour conserver une seconde version potentiellement plus grande de votre référentiel.

## Sauvegarde complète d’AEM {#fully-back-up-aem}

AEM doit être entièrement sauvegardé avant de commencer la mise à niveau. Veillez à sauvegarder votre référentiel, l’installation de l’application, la banque de données et les instances Mongo, le cas échéant. Pour plus d’informations sur la sauvegarde et la restauration d’une instance AEM, voir [Sauvegarde et restauration](/help/sites-administering/backup-and-restore.md).

## Sauvegarde des modifications sur /etc {#backup-changes-etc}

Le processus de mise à niveau est utile dans le maintien et la fusion du contenu existant et des configurations à partir des chemins d’accès `/apps` et `/libs` dans le référentiel. Pour les modifications apportées au chemin d’accès `/etc`, y compris les configurations Context Hub, il est souvent nécessaire de réappliquer ces modifications après la mise à niveau. Alors que la mise à niveau crée une copie de sauvegarde de toutes les modifications qui ne peuvent pas fusionner sous `/var`, nous vous recommandons de sauvegarder ces modifications manuellement avant de commencer la mise à niveau.

## Génération du fichier quickstart.properties {#generate-quickstart-properties}

Lors du démarrage d’AEM depuis le fichier jar, un fichier `quickstart.properties` est généré sous `crx-quickstart/conf`. Si AEM a uniquement été démarré avec le script de démarrage dans le passé, ce fichier ne sera pas présent et la mise à niveau échouera. Assurez-vous de vérifier l’existence de ce fichier et redémarrez l’AEM à partir du fichier jar s’il n’est pas présent.

## Configuration de la purge du workflow et du journal d’audit {#configure-wf-audit-purging}

Les tâches `WorkflowPurgeTask` et `com.day.cq.audit.impl.AuditLogMaintenanceTask` nécessitent des configurations OSGi distinctes et ne fonctionneront pas sans celles-ci. S’ils échouent lors de l’exécution de la tâche avant la mise à niveau, des configurations manquantes en sont la raison la plus probable. Par conséquent, veillez à ajouter des configurations OSGi pour ces tâches ou à les supprimer complètement de la liste des tâches d’optimisation avant la mise à niveau si vous ne souhaitez pas les exécuter. Vous trouverez la documentation relative à la configuration des tâches de purge des workflows dans la section [Administration des instances de workflow](/help/sites-administering/workflows-administering.md) et la configuration de la tâche de maintenance du journal d’audit se trouve à l’adresse [Maintenance du journal d’audit dans AEM 6](/help/sites-administering/operations-audit-log.md).

Pour la purge des workflows et des journaux d’audit sur CQ 5.6, ainsi que la purge des journaux d’audit sur AEM 6.0, voir [Purge des noeuds de workflow et d’audit](https://helpx.adobe.com/fr/experience-manager/kb/howtopurgewf.html).

## Installation, configuration et exécution des tâches précédant la mise à niveau {#install-configure-run-pre-upgrade-tasks}

En raison du niveau de personnalisation accordé par AEM, il n’existe généralement pas de méthode uniforme pour effectuer les mises à niveau. La création d’une procédure normalisée pour les mises à niveau est ainsi un processus difficile.

Dans les versions précédentes, il était également difficile d’AEM mises à niveau qui ont été arrêtées ou qui n’ont pas pu être reprise en toute sécurité. Cela a conduit à des situations où le redémarrage de la procédure de mise à niveau complète était nécessaire ou où des mises à niveau défectueuses ont été effectuées sans déclencher d’avertissement.

Pour résoudre ces problèmes, Adobe a ajouté plusieurs améliorations au processus de mise à niveau, le rendant plus résistant et plus convivial. Les tâches de maintenance préalables à la mise à niveau qui devaient auparavant être effectuées manuellement sont optimisées et automatisées. En outre, des rapports après la mise à niveau ont été ajoutés afin que le processus puisse être entièrement examiné dans l’espoir que les problèmes éventuels soient plus facilement détectés.

Les tâches de maintenance préalables à la mise à niveau sont actuellement réparties sur différentes interfaces, qui sont partiellement ou totalement exécutées manuellement. L’optimisation de la maintenance avant la mise à niveau introduite dans AEM 6.3 permet de déclencher ces tâches de manière unifiée et d’examiner leur résultat à la demande.

Toutes les tâches incluses dans l’étape d’optimisation avant la mise à niveau sont compatibles avec toutes les versions à partir d’AEM 6.0.

### Comment le configurer {#how-to-set-it-up}

Dans AEM version 6.3 et ultérieure, les tâches d’optimisation de la maintenance avant la mise à niveau sont incluses dans le fichier jar de démarrage rapide. Si vous effectuez une mise à niveau à partir d’une ancienne version d’AEM 6, elles sont disponibles via des modules distincts que vous pouvez télécharger à partir du gestionnaire de modules.

Vous trouverez les packages à ces emplacements :

* [Pour effectuer la mise à jour à partir d’AEM 6.0](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq600/product/pre-upgrade-tasks-content-cq60)

* [Pour effectuer la mise à jour à partir d’AEM 6.1](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/product/pre-upgrade-tasks-content-cq61)

* [Pour effectuer la mise à niveau à partir d’AEM 6.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/product/pre-upgrade-tasks-content-cq62)

### Comment l’utiliser {#how-to-use-it}

Le composant OSGi `PreUpgradeTasksMBean` est préconfiguré avec une liste de tâches de maintenance bénéficiant déjà de la mise à niveau, pouvant toutes être exécutées simultanément. Vous pouvez configurer les tâches en suivant la procédure ci-dessous :

1. Accédez à la console web en accédant à `https://serveraddress:serverport/system/console/configMgr`

1. Recherchez « **preupgradetasks** », puis cliquez sur le premier composant correspondant. Le nom complet du composant est `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`.

1. Modifiez la liste des tâches de maintenance devant être exécutées comme illustré ci-dessous :

   ![1487758925984](assets/1487758925984.png)

La liste des tâches varie en fonction du mode d’exécution utilisé pour démarrer l’instance. Vous trouverez ci-dessous une description du mode d’exécution pour lequel chaque tâche de maintenance est conçue.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Tâche</strong></td> 
   <td><strong>Mode d’exécution</strong></td> 
   <td><strong>Remarques</strong></td> 
  </tr> 
  <tr> 
   <td><code>TarIndexMergeTask</code></td> 
   <td>crx2</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>DataStoreGarbageCollectionTask</code></td> 
   <td>crx2</td> 
   <td>Exécute le marquage et le balayage. Pour les banques de données partagées, supprimez cette étape et exécutez<br /> préparez manuellement ou correctement les instances avant l’exécution.</td> 
  </tr> 
  <tr> 
   <td><code>ConsistencyCheckTask</code></td> 
   <td>crx2</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>WorkflowPurgeTask</code></td> 
   <td>crx2/crx3</td> 
   <td>Doit configurer la configuration OSGi de purge de workflow Granite de l’Adobe avant l’exécution.</td> 
  </tr> 
  <tr> 
   <td><code>GenerateBundlesListFileTask</code></td> 
   <td>crx2/crx3</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>RevisionCleanupTask</code></td> 
   <td>crx3</td> 
   <td>Pour les instances TarMK sur AEM 6.0 à 6.2, exécutez manuellement le nettoyage des révisions hors ligne à la place.</td> 
  </tr> 
  <tr> 
   <td><code>com.day.cq.audit.impl.AuditLogMaintenanceTask</code></td> 
   <td>crx3</td> 
   <td>Doit configurer la configuration OSGi du planificateur de purge du journal d’audit avant l’exécution.</td> 
  </tr> 
 </tbody> 
</table>

>[!CAUTION]
>
>`DataStoreGarbageCollectionTask` appelle l’opération de récupération de l’espace mémoire du magasin de données avec la phase de marquage et de balayage, le cas échéant. Pour les déploiements qui utilisent une banque de données partagée, assurez-vous de la reconfigurer correctement ou de préparer l’instance afin d’éviter la suppression des éléments référencés par une autre instance. Cela peut nécessiter l’exécution manuelle de la phase de marquage sur toutes les instances avant de déclencher cette tâche de pré-mise à niveau.

### Configuration par défaut des contrôles de l’intégrité avant la mise à niveau {#default-configuration-of-the-pre-upgrade-health-checks}

Le composant OSGi `PreUpgradeTasksMBeanImpl` est préconfiguré avec une liste de balises de vérification de l’intégrité précédant la mise à niveau à exécuter lorsque la méthode `runAllPreUpgradeHealthChecks` est appelée :

* **system** : balise utilisée par les contrôles de l’intégrité de la maintenance Granite

* **pre-upgrade** : il s’agit d’une balise personnalisée qui peut être ajoutée à toutes les vérifications d’intégrité dont vous pouvez définir l’exécution avant une mise à niveau

La liste peut être modifiée. Vous pouvez utiliser le plus **(+)** et moins **(-)** en plus des balises pour ajouter d’autres balises personnalisées ou supprimer les balises par défaut.

**Méthodes MBean**

La fonctionnalité bean gérée est accessible à l’aide du [Console JMX](/help/sites-administering/jmx-console.md).

Vous pouvez accéder aux MBeans en procédant comme suit :

1. Accédez à la console JMX à l’adresse *https://serveraddress:serverport/system/console/jmx*.
1. Recherchez **PreUpgradeTasks** et cliquez sur le résultat.

1. Sélectionnez une méthode à partir de la section **Opérations** et sélectionnez **Invoquer** dans la fenêtre suivante.

Vous trouverez ci-dessous la liste de toutes les méthodes disponibles offertes par `PreUpgradeTasksMBeanImpl` :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nom de méthode</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td><code>getAvailablePreUpgradeTasksNames()</code></td> 
   <td>INFO</td> 
   <td>Affiche la liste des noms des tâches de maintenance disponibles avant la mise à niveau.</td> 
  </tr> 
  <tr> 
   <td><code>getAvailablePreUpgradeHealthChecksTagNames()</code></td> 
   <td>INFO</td> 
   <td>Affiche la liste des noms des balises des contrôles d’intégrité avant la mise à niveau.</td> 
  </tr> 
  <tr> 
   <td><code>runAllPreUpgradeTasks()</code></td> 
   <td>ACTION</td> 
   <td>Exécute toutes les tâches de maintenance avant la mise à niveau de la liste.</td> 
  </tr> 
  <tr> 
   <td><code>runPreUpgradeTask(preUpgradeTaskName)</code></td> 
   <td>ACTION</td> 
   <td>Exécute la tâche de maintenance avant la mise à niveau avec le nom donné en tant que paramètre.</td> 
  </tr> 
  <tr> 
   <td><code>isRunAllPreUpgradeTaskRunning()</code></td> 
   <td>ACTION_INFO</td> 
   <td>Vérifie si la tâche <code>runAllPreUpgradeTasksmaintenance</code> est en cours d’exécution.</td> 
  </tr> 
  <tr> 
   <td><code>getAnyPreUpgradeTaskRunning()</code></td> 
   <td>ACTION_INFO</td> 
   <td>Vérifie si une tâche de maintenance avant la mise à niveau est en cours d’exécution et<br /> renvoie un tableau contenant les noms des tâches en cours d’exécution.</td> 
  </tr> 
  <tr> 
   <td><code>getPreUpgradeTaskLastRunTime(preUpgradeTaskName)</code></td> 
   <td>ACTION</td> 
   <td>Affiche l’heure d’exécution exacte de la tâche de maintenance avant la mise à niveau avec le nom donné en tant que paramètre.</td> 
  </tr> 
  <tr> 
   <td><code>getPreUpgradeTaskLastRunState(preUpgradeTaskName)</code></td> 
   <td>ACTION</td> 
   <td>Affiche le dernier état d’exécution de la tâche de maintenance avant la mise à niveau avec le nom donné en tant que paramètre.</td> 
  </tr> 
  <tr> 
   <td><code>runAllPreUpgradeHealthChecks(shutDownOnSuccess)</code></td> 
   <td>ACTION</td> 
   <td><p>Exécute toutes les vérifications d’intégrité avant la mise à niveau et enregistre leur statut dans un fichier nommé <code>preUpgradeHCStatus.properties</code> situé sur le chemin d’accès Sling de l’accueil. Si le paramètre <code>shutDownOnSuccess</code> est défini sur <code>true</code>, l’instance AEM est arrêtée, mais seulement si toutes les vérification d’intégrité avant la mise à niveau renvoient le statut « OK ».</p> <p>Le fichier de propriétés sera utilisé comme prérequis pour toute mise à niveau ultérieure.<br /> et le processus de mise à niveau sera arrêté si le contrôle de l’intégrité précédant la mise à niveau est effectué.<br /> l’exécution a échoué. Si vous souhaitez ignorer le résultat de la pré-mise à niveau<br /> des contrôles d’intégrité et lancer la mise à niveau, vous pouvez tout de même supprimer le fichier.</p> </td> 
  </tr> 
  <tr> 
   <td><code>detectUsageOfUnavailableAPI(aemVersion)</code></td> 
   <td>ACTION</td> 
   <td>Répertorie tous les packages importés qui ne fonctionneront plus<br /> lors du passage à la version d’AEM spécifiée. La version AEM cible doit être<br /> donné en tant que paramètre.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Les méthodes MBean peuvent être invoquées via :
>
>* Console JMX
>* Toute application externe qui se connecte à JMX
>* cURL
>


## Désactivation des modules de connexion personnalisés {#disable-custom-login-modules}

>[!NOTE]
>
>Cette étape est nécessaire uniquement si vous effectuez une mise à niveau à partir d’une version d’AEM 5. Il peut être entièrement ignoré pour les mises à niveau à partir d’AEM 6 versions plus anciennes.

La manière dont les modules de connexion `LoginModules` sont configurés pour l’authentification au niveau du référentiel a complètement changé dans Apache Oak.

Dans les versions d’AEM qui utilisaient CRX2, la configuration était placée dans le fichier `repository.xml` du référentiel alors qu’à partir de la version 6 et suivantes, cette opération est effectuée dans le service Apache Felix JAAS Configuration Factory via la console web.

En conséquence, toute configuration existante doit être désactivée et recréée pour Apache Oak après la mise à niveau.

Pour désactiver les modules personnalisés définis dans la configuration JAAS de `repository.xml`, vous devez modifier la configuration afin d’utiliser le `LoginModule` par défaut, comme dans cet exemple :

```xml
<Security >
             ....
          <!--
                 Use LoginModule authenticating against repository itself
                 -->
                 <LoginModule class = "com.day.crx.core.CRXLoginModule" >
                     <param name = "anonymousId" value = "anonymous" />
                     <param name = "adminId" value ="admin" />
                     <param name = "disableNTLMAuth" value = "true" />
                     <param name = "tokenExpiration" value = "43200000" />
                     <!-- param name="trust_credentials_attribute" value="d5b9167e95dad6e7d3b5d6fa8df48af8"/
                -->
                 </LoginModule >
         </ Security>
```

>[!NOTE]
>
>Pour plus d’informations, consultez la section [Authentification avec le module de connexion externe](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).
>
>Pour un exemple de configuration de `LoginModule` dans AEM 6, consultez la section [Configuration de LDAP avec AEM 6](/help/sites-administering/ldap-config.md).

## Suppression des mises à jour du répertoire /install {#remove-updates-install-directory}

>[!NOTE]
>
>Supprimez uniquement les packages du répertoire crx-quickstart/install APRÈS avoir arrêté l’instance AEM. Il s’agit de l’une des dernières étapes avant de commencer la procédure de mise à niveau statique.

Supprimez tous les packs de services, les packs de fonctionnalités ou les correctifs logiciels qui ont été déployés via le répertoire `crx-quickstart/install` sur le système de fichiers local. Cela empêchera l’installation accidentelle d’anciens correctifs et Service Packs en plus de la nouvelle version d’AEM une fois la mise à jour terminée.

## Arrêt de toutes les instances Cold Standby {#stop-tarmk-coldstandby-instance}

Si vous utilisez TarMK cold Secondaire, arrêtez toutes les instances Secondaires froides. Cela garantit un moyen efficace de revenir en ligne en cas de problèmes lors de la mise à niveau. Une fois la mise à niveau terminée, les instances Secondaires en froid devront être reconstruites à partir des instances Principales mises à niveau.

## Désactivation des tâches planifiées personnalisées {#disable-custom-scheduled-jobs}

Désactivez toutes les tâches OSGi planifiées incluses dans le code de votre application.

## Exécution d’un nettoyage des révisions hors ligne {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Cette étape n’est nécessaire que pour les installations TarMK

Si vous utilisez TarMK, vous devez exécuter le nettoyage des révisions hors ligne avant la mise à niveau. L’étape de migration du référentiel et les tâches de mise à niveau qui s’ensuivent s’exécuteront ainsi beaucoup plus rapidement et le nettoyage des révisions en ligne pourra s’exécuter correctement une fois la mise à niveau terminée. Pour plus d’informations sur l’exécution du nettoyage des révisions hors ligne, voir [Exécution du nettoyage des révisions hors ligne](https://helpx.adobe.com/experience-manager/6-2/sites-deploying/storage-elements-in-aem-6.html#performing-offline-revision-cleanup).

## Exécution de la récupération de l’espace mémoire du magasin de données {#execute-datastore-garbage-collection}

>[!NOTE]
>
>Cette étape n&#39;est nécessaire que pour les instances exécutant crx3

Après avoir exécuté le nettoyage des révisions sur les instances CRX3, vous devez exécuter le nettoyage de la mémoire d’entrepôt de données pour supprimer tous les objets blob non référencés dans l’entrepôt de données. Pour obtenir des instructions, consultez la documentation sur [Nettoyage de la mémoire d’entrepôt de données](/help/sites-administering/data-store-garbage-collection.md).

## Suppression des utilisateurs susceptibles d’entraver la mise à niveau {#delete-users-that-might-hinder-the-upgrade}

>[!NOTE]
>
>Cette tâche de maintenance avant la mise à niveau n’est nécessaire que si :
>
>* vous effectuez une mise à niveau à partir des versions d’AEM antérieures à AEM 6.3 ;
>* vous rencontrez les erreurs mentionnées ci-dessous lors de la mise à niveau.


Il existe des cas exceptionnels où les utilisateurs du service peuvent se retrouver dans des versions AEM plus anciennes mal balisées en tant qu’utilisateurs standard.

Si cela se produit, la mise à niveau échoue avec un message comme celui-ci :

```
ERROR [Apache Sling Repository Startup Thread] com.adobe.granite.repository.impl.SlingRepositoryManager Exception in a SlingRepositoryInitializer, SlingRepository service registration aborted
java.lang.RuntimeException: Unable to create service user [communities-utility-reader]:java.lang.RuntimeException: Existing user communities-utility-reader is not a service user.
```

Pour contourner ce problème, procédez comme suit :

Pour contourner ce problème, procédez comme suit :

* Désolidarisez l’instance du trafic d’exploitation.
* Créez une sauvegarde du ou des utilisateurs à l’origine du problème. Vous pouvez le faire via le gestionnaire de packages. Pour plus d’informations sur les packages, consultez la rubrique [Utilisation des packages](/help/sites-administering/package-manager.md).
* Supprimez le ou les utilisateurs à l’origine du problème. Vous trouverez ci-dessous une liste d’utilisateurs qui peuvent appartenir à cette catégorie :
   * dynamic-media-replication
   * communities-ugc-writer
   * communities-utility-reader
   * communities-user-admin
   * oauthservice
   * sling-scripting

## Mise à niveau du schéma de base de données si nécessaire {#upgrade-the-database-schema-if-needed}

En règle générale, la pile Apache Oak sous-jacente utilisée par AEM pour la persistance s’occupe de la mise à niveau du schéma de base de données si nécessaire.

Cependant, il peut arriver que le schéma ne puisse pas être mis à niveau automatiquement. Il s’agit principalement d’environnements de sécurité élevée dans lesquels la base de données s’exécute sous un utilisateur avec des privilèges très limités. Si cela se produit, AEM continuera à utiliser l’ancien schéma.

Pour éviter cela, vous devez mettre à niveau le schéma en suivant la procédure ci-dessous :

1. Arrêtez l’instance AEM qui doit être mise à niveau.
1. Mettez à niveau le schéma de la base de données. Consultez la documentation relative à votre type de base de données afin de connaître les outils à utiliser pour y parvenir.

   Pour plus d’informations sur la façon dont Oak gère les mises à niveau des schémas, consultez [cette page sur le site web d’Apache](https://jackrabbit.apache.org/oak/docs/nodestore/document/rdb-document-store.html#upgrade).

1. Continuez la mise à niveau d’AEM.

## Rotation des fichiers journaux {#rotate-log-files}

Nous vous recommandons d’archiver vos fichiers journaux actuels avant de commencer votre mise à niveau. Cela facilite la surveillance et l’analyse de vos fichiers journaux pendant et après la mise à niveau pour identifier et résoudre les problèmes qui peuvent se produire.
