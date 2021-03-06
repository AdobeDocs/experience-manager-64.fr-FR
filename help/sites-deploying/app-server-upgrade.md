---
title: Procédure de mise à niveau pour les installations de serveur d’applications
seo-title: Upgrade Steps for Application Server Installations
description: Découvrez comment mettre à niveau des instances AEM qui sont déployées par le biais de serveurs d’applications.
seo-description: Learn how to upgrade instances of AEM that are deployed via Application Servers.
uuid: df3fa715-af4b-4c81-b2c5-130fbc82f395
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: c427c8b6-eb94-45fa-908f-c3d5a337427d
feature: Upgrading
exl-id: 1c72093e-82c8-49ad-bd3c-d61904aaab28
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 96%

---

# Procédure de mise à niveau pour les installations de serveur d’applications{#upgrade-steps-for-application-server-installations}

Cette section décrit la procédure qui doit être suivie afin de mettre à jour AEM pour les installations de serveur d’applications.

Tous les exemples de cette procédure utilisent JBoss comme serveur d’applications et présument que vous disposez d’une version de travail d’AEM déjà déployée. La procédure est destinée à documenter les mises à niveau d’**AEM version 5.6 vers la version 6.3**.

1. Tout d’abord, démarrez JBoss. Dans la plupart des cas, vous pouvez effectuer cette opération en exécutant le script de démarrage `standalone.sh` en lançant la commande suivante depuis le terminal :

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. Si AEM 5.6 est déjà déployé, vérifiez que les lots fonctionnent correctement en exécutant :

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Ensuite, annulez le déploiement d’AEM 5.6 :

   ```shell
   rm jboss-install-folder/standalone/deployments/cq.war
   ```

1. Arrêtez JBoss.

1. À présent, migrez le référentiel à l’aide de l’outil de migration crx2oak :

   ```shell
   java -jar crx2oak.jar crx-quickstart/repository/ crx-quickstart/oak-repository
   ```

   >[!NOTE]
   >
   >Dans cet exemple, oak-repository est le répertoire temporaire dans lequel se trouve le référentiel nouvellement converti. Avant d’effectuer cette étape, vérifiez que vous disposez de la version la plus récente de crx2oak.jar.

1. Supprimez les propriétés requises du fichier sling.properties en procédant comme suit :

   1. Ouvrez le fichier situé à l’adresse `crx-quickstart/launchpad/sling.properties`
   1. Supprimez les propriétés suivantes et enregistrez le fichier :

      1. `sling.installer.dir`
      1. `felix.cm.dir`
      1. `granite.product.version`
      1. `org.osgi.framework.system.packages`
      1. `osgi-core-packages`
      1. `osgi-compendium-services`
      1. `jre-*`
      1. `sling.run.mode.install.options`

1. Supprimez les fichiers et dossiers qui ne sont plus nécessaires. Vous devez précisément supprimer les éléments suivants :

   * Le **dossier launchpad/startup**. Vous pouvez le supprimer en exécutant la commande suivante dans le terminal :`rm -rf crx-quickstart/launchpad/startup`
   * Le **fichier base.jar**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`
   * Le **Fichier BootstrapCommandFile_timestamp.txt**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. Copiez le segmentstore (magasin de segments) nouvellement migré à son emplacement approprié :

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. Copiez également l’entrepôt de données :

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. Ensuite, vous devez créer le dossier qui contient les configurations OSGi qui seront utilisées avec la nouvelle instance mise à niveau. Plus précisément, un dossier nommé install doit être créé sous **crx-quickstart**.

1. Créez à présent les entrepôts de nœuds et de données qui seront utilisés avec AEM 6.3. Pour ce faire, vous devez créer deux fichiers portant les noms suivants sous **crx-quickstart\install** :

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Ces deux fichiers configureront AEM de façon à ce qu’ils utilisent un entrepôt de nœuds TarMK et un entrepôt de données File.

1. Modifiez les fichiers de configuration pour les rendre prêts à l’emploi. Plus précisément :

   * Ajoutez la ligne suivante à **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:

      `customBlobStore=true`

   * Ajoutez ensuite les lignes suivantes à **org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config** : 

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. Supprimez le mode d’exécution crx2 en exécutant :

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. Vous pouvez maintenant modifier les modes d’exécution du fichier war d’AEM 6.3. Pour ce faire, créez tout d’abord un dossier temporaire qui héberge le fichier war d’AEM 6.3. Le nom du dossier dans cet exemple est **temp**. Une fois le fichier war copié, extrayez son contenu en exécutant la commande suivante depuis le dossier temp :

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. Une fois le contenu extrait, accédez au dossier **WEB-INF** et modifiez le fichier `web.xml` afin de modifier les modes d’exécution. Pour trouver l’emplacement où ils sont définis dans le fichier XML, recherchez la chaîne `sling.run.modes`. Une fois que vous l’avez trouvée, définissez les modes d’exécution sur la ligne de code suivante qui, par défaut, est définie sur author :

   ```shell
   <param-value >author</param-value>
   ```

1. Modifiez la valeur author ci-dessus et définissez les modes d’exécution sur : author,crx3,crx3tar. Le bloc de code final devrait ressembler à ceci : 

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. Créez à nouveau le fichier jar avec les contenus modifiés :

   ```shell
   jar cvf aem62.war
   ```

1. Enfin, déployez le nouveau fichier war :

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```
