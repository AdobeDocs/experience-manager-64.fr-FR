---
title: Effectuer une mise à niveau statique
seo-title: Performing an In-Place Upgrade
description: Découvrez comment effectuer une mise à niveau statique.
seo-description: Learn how to perform an in-place upgrade.
uuid: c7428dc0-2b9e-401d-8f80-19e936f6d739
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: b1bd40f4-21c6-48f5-a41e-42daeaad3687
feature: Upgrading
exl-id: 70c5ef98-1004-46d0-b805-9435613ec36b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 41%

---

# Effectuer une mise à niveau statique{#performing-an-in-place-upgrade}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Cette page décrit la procédure de mise à niveau d’AEM 6.4. Si une installation est déployée sur un serveur d’applications, reportez-vous à la section [Procédure de mise à niveau pour les installations de serveur d’applications](/help/sites-deploying/app-server-upgrade.md).

## Étapes préalables à la mise à niveau {#pre-upgrade-steps}

Avant d&#39;exécuter votre mise à niveau, plusieurs étapes doivent être réalisées. Voir [Mise à niveau du code et des personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md) et [Tâches de maintenance avant la mise à niveau](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) pour plus d’informations. Veillez également à ce que votre système réponde aux exigences de la nouvelle version d’AEM. Découvrez comment l’outil de détection des motifs peut vous aider à estimer la complexité de votre mise à niveau et voir également la section Portée et exigences de la mise à niveau de [Planification de la mise à niveau](/help/sites-deploying/upgrade-planning.md) pour plus d’informations.

## Conditions préalables à la migration {#migration-prerequisites}

* **Version Java minimale requise :** L’outil de migration ne fonctionne qu’avec les versions 7 et ultérieures de Java. Notez que pour AEM 6.3, et versions ultérieures, l’environnement JRE 8 d’Oracle et les environnements JRE 7 et 8 d’IBM sont les seules versions prises en charge.

* **Instance mise à niveau :** Si vous effectuez une mise à niveau à partir d’une version **plus de 5.6**, vérifiez que vous avez effectué une mise à niveau statique vers AEM 6.0 en suivant la procédure décrite dans la version 6.0 de la documentation de mise à niveau.

## Préparation du fichier jar de démarrage rapide AEM {#prep-quickstart-file}

1. Arrêtez l’instance si elle est en cours d’exécution.

1. Téléchargez le nouveau fichier JAR d’AEM et utilisez-le pour remplacer l’ancien en dehors du dossier `crx-quickstart`.

1. Décompressez le nouveau fichier jar de démarrage rapide en exécutant :

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

## Migration du référentiel de contenu {#content-repository-migration}

Cette migration n’est pas requise si vous effectuez une mise à niveau à partir d’AEM 6.3. Pour les versions antérieures à la version 6.3, Adobe fournit un outil qui peut être utilisé pour migrer le référentiel vers la nouvelle version du fichier Oak Segment Tar présent dans AEM 6.3. Il est fourni dans le cadre du module de démarrage rapide et est obligatoire pour toutes les mises à niveau qui utiliseront TarMK. Les mises à niveau pour les environnements qui utilisent MongoMK ne nécessitent pas de migration du référentiel. Pour plus d’informations sur les avantages du nouveau format Segment Tar, voir la section [FAQ sur la migration vers Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

La migration réelle est effectuée à l’aide du fichier JAR de démarrage rapide d’AEM, exécuté avec une nouvelle option `-x crx2oak`, qui exécute l’outil crx2oak afin de simplifier la mise à niveau et de la rendre plus robuste.

>[!NOTE]
>
>Si vous effectuez une migration du contenu du référentiel TarMK avec l’extension de démarrage rapide CRX2Oak, vous pouvez supprimer le mode d’exécution **samplecontent** en ajoutant la commande suivante à la ligne de commande de migration :
>
>* `--promote-runmode nosamplecontent`
>


Pour déterminer la commande à exécuter, utilisez la commande suivante :

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Où `<<YOUR_PROFILE>>` et `<<ADDITIONAL_FLAGS>>` sont remplacés par le profil et les indicateurs figurant dans le tableau suivant :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Référentiel source</strong></td> 
   <td><strong>Référentiel cible</strong></td> 
   <td><strong>Profil</strong></td> 
   <td><strong>Indicateurs supplémentaires</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>crx2 ou TarMK avec <code>FileDataStore</code></td> 
   <td>TarMK</td> 
   <td>segment-fds</td> 
   <td>Voir la section Dépannage ci-dessous</td> 
  </tr> 
  <tr> 
   <td>crx2</td> 
   <td>MongoMK</td> 
   <td>mongo-from-crx2 </td> 
   <td><code>-T mongo-uri=mongo://mongo-host:mongo-port -T mongo-db=mongo-database-name</code></td> 
  </tr> 
  <tr> 
   <td>TarMK ou crx2 avec <code>S3DataStore</code></td> 
   <td>TarMK</td> 
   <td>segment-custom-ds</td> 
   <td>Voir la section Dépannage ci-dessous</td> 
  </tr> 
  <tr> 
   <td>TarMK sans banque de données</td> 
   <td>TarMK</td> 
   <td>segment-no-ds</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>MongoMK</td> 
   <td>MongoMK</td> 
   <td>Aucune migration n’est nécessaire</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

<!--please check above table-->

**Où :**

* `mongo-host` correspond à l’IP du serveur MongoDB (par exemple, 127.0.0.1) ;

* `mongo-port` correspond au port du serveur MongoDB (par exemple, 27017) ;

* `mongo-database-name` représente le nom de la base de données (par exemple : aem-auteur).

**Vous pouvez également avoir besoin de commutateurs supplémentaires pour les scénarios suivants :**

* Si vous effectuez la mise à niveau sur un système Windows, sur lequel le mappage de la mémoire Java n’est pas géré correctement, ajoutez le paramètre `--disable-mmap` à la commande.

* Si vous utilisez Java 7, ajoutez le paramètre `-XX:MaxPermSize=2048m` juste après le paramètre `-Xmx`.

Pour plus d’informations sur l’utilisation de l’outil crx2oak, voir Utilisation de la variable [Outil de migration CRX2Oak](/help/sites-deploying/using-crx2oak.md). Le fichier JAR d’assistance crx2oak peut être mis à niveau manuellement si nécessaire, en le remplaçant manuellement par des versions plus récentes après avoir décompressé le démarrage rapide. Son emplacement dans le dossier d’installation AEM est le suivant :   `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. La dernière version de l’outil de migration CRX2Oak peut être téléchargée à partir du référentiel Adobe à l’adresse : [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/)

Si la migration a réussi, l’outil quitte avec un code de sortie égal à 0. Cherchez également des messages AVERTISSEMENT et ERREUR dans le fichier `upgrade.log`, disponible sous `crx-quickstart/logs` dans le répertoire d’installation d’AEM, car ils peuvent indiquer des erreurs non fatales qui se sont produites lors de la migration.

Vérifiez les fichiers de configuration dans le dossier `crx-quickstart/install`. Si une migration était nécessaire, celles-ci sont mises à jour pour refléter le référentiel cible.

>[!NOTE]
>
>Lorsque `FileDataStore` est la nouvelle valeur par défaut pour des installations AEM 6.3, l’utilisation d’un magasin de données externe n’est pas nécessaire. Bien que l’utilisation d’une banque de données externe soit recommandée comme une bonne pratique pour les déploiements en production, il ne s’agit pas d’un prérequis à la mise à niveau. En raison de la complexité déjà présente dans la mise à niveau d’AEM, nous vous recommandons d’effectuer la mise à niveau sans effectuer de migration de banque de données. Si vous le souhaitez, une migration de banque de données peut être exécutée par la suite dans le cadre d’un effort distinct.

## Résolution des problèmes de migration {#troubleshooting-migration-issues}

Ignorez cette section si vous effectuez une mise à niveau à partir de la version 6.3. Bien que les profils crx2oak fournis doivent répondre aux besoins de la plupart des clients, il peut arriver que des paramètres supplémentaires soient nécessaires. Si vous rencontrez une erreur lors de la migration, il est possible que certains aspects de votre environnement nécessitent des options de configuration supplémentaires. Si tel est le cas, l’erreur suivante se produira probablement :

**Les points de contrôle ne seront pas copiés, car aucun entrepôt de données externe n’a été spécifié. Cela entraînera la réindexation complète du référentiel au premier démarrage. Utilisez —skip-checkpoints pour forcer la migration ou consultez https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration pour plus d’informations.**

Pour une raison quelconque, le processus de migration doit accéder aux fichiers binaires de la banque de données et ne peut pas les trouver. Pour spécifier la configuration du magasin de données, incluez les indicateurs ci-dessous dans la partie `<<ADDITIONAL_FLAGS>>` de la commande de migration :

**Pour les magasins de données S3 :**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Où `/path/to/SharedS3DataStore.config` représente le chemin d’accès au fichier de configuration de votre magasin de données S3, et `/path/to/datastore` représente le chemin d’accès à votre magasin de données S3.

**Pour les magasins de données de fichier :**

```shell
--src-datastore=/path/to/datastore
```

Où `/path/to/datastore` représente le chemin d’accès à votre magasin de données de fichier.

## Exécution De La Mise À Niveau {#performing-the-upgrade}

**Si vous utilisez S3 :**

1. Supprimez les fichiers JAR sous `crx-quickstart/install` associés à une version antérieure du connecteur S3.

1. Téléchargez la dernière version du connecteur S3 1.8.x à partir de [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

1. Extrayez le package dans un dossier temporaire et copiez le contenu de `jcr_root/libs/system/install` dans le dossier `crx-quickstart/install`.

### Détermination de la commande de démarrage de mise à niveau appropriée {#determining-the-correct-upgrade-start-command}

Pour exécuter la mise à niveau, il est important de commencer AEM utiliser le fichier jar pour faire apparaître l’instance. Pour passer à la version 6.4, veuillez également consulter d’autres options de migration et de restructuration de contenu dans la [Migration de contenu différée](/help/sites-deploying/lazy-content-migration.md) que vous pouvez sélectionner avec la commande de mise à niveau.

Notez que le fait de démarrer AEM à partir du script de démarrage ne lance pas la mise à niveau. La plupart des clients commencent AEM à utiliser le script de démarrage et ont personnalisé ce script de démarrage afin d’inclure des commutateurs pour les configurations d’environnement telles que les paramètres de mémoire, les certificats de sécurité, etc. Pour cette raison, nous vous recommandons de suivre cette procédure pour déterminer la commande de mise à niveau appropriée :

1. Sur une instance d’AEM en cours d’exécution, exécutez les opérations ci-dessous dans une ligne de commande :

   ```shell
   ps -ef | grep java
   ```

1. Recherchez le processus AEM. Le code se présente comme suit :

   ```shell
   /usr/bin/java -server -Xmx1024m -XX:MaxPermSize=256M -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.2.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Modifiez la commande en remplaçant le chemin d’accès dans le fichier JAR existant (`crx-quickstart/app/aem-quickstart*.jar` dans ce cas) par le nouveau fichier JAR qui est un frère du dossier `crx-quickstart`. Avec la commande précédente comme exemple, la commande serait la suivante :

   ```shell
   /usr/bin/java -server -Xmx1024m -XX:MaxPermSize=256M -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar cq-quickstart-6.4.0.jar -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Cela permet de s’assurer que tous les paramètres de mémoire appropriés, les modes d’exécution personnalisés et d’autres paramètres environnementaux sont appliqués pour la mise à niveau. Une fois la mise à niveau terminée, l’instance peut être lancée à partir du script de démarrage lors des prochaines lancements.

## Déployer le code base mis à niveau {#deploy-upgraded-codebase}

Une fois le processus de mise à niveau statique terminé, la base de code mise à jour doit être déployée. La procédure de mise à jour de la base de code pour qu’elle fonctionne dans la version cible d’AEM est disponible dans la page [Mise à niveau du code et personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md).

## Effectuez les vérifications et le dépannage après la mise à niveau {#perform-post-upgrade-check-troubleshooting}

Voir [Vérifications et dépannage après la mise à niveau](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
