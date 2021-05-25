---
title: Prise en charge RDBMS dans AEM 6.4
seo-title: Prise en charge RDBMS dans AEM 6.4
description: 'Obtenez des informations sur la prise en charge de la persistance de la base de données relationnelle dans AEM 6.4 et les options de configuration disponibles. '
seo-description: 'Obtenez des informations sur la prise en charge de la persistance de la base de données relationnelle dans AEM 6.4 et les options de configuration disponibles. '
uuid: 599d3e61-99eb-4a1c-868b-52b20a615500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 56a984a5-4b7f-4a95-8a17-95d2d355bfed
feature: Configuration
exl-id: 89523bb4-e4c4-469c-802b-6fe27c816a2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 72%

---

# Prise en charge RDBMS dans AEM 6.4{#rdbms-support-in-aem}

## Présentation {#overview}

La prise en charge de la persistance de la base de données relationnelle dans AEM est réalisée à l’aide de Document Microkernel. Document Microkernel constitut la base également utilisée pour mettre en œuvre la persistance MongoDB.

Il se compose d’une API Java basée sur l’API Mongo Java. La mise en œuvre d’une API BlobStore est aussi fournie. Les blobs sont stockés dans la base de données par défaut.

Pour plus de détails sur la mise en œuvre, voir la documentation [ RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) et [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html).

>[!NOTE]
>
>La prise en charge pour **PostgreSQL 9.4** est également fournie, mais uniquement à des fins de démonstration. Elle ne sera pas disponible pour les environnements de production. 

## Bases de données prises en charge {#supported-databases}

Pour plus d’informations sur le niveau de prise en charge de la base de données relationnelle dans AEM, consultez la [page des exigences techniques](/help/sites-deploying/technical-requirements.md).

## Étapes de configuration {#configuration-steps}

Le référentiel est créé lors de la configuration du service OSGi `DocumentNodeStoreService`. Il a été étendu pour prendre en charge la persistance de la base de données relationnelle en plus de MongoDB.

Pour qu’il fonctionne, une source de données doit être configurée avec AEM. Cela s’effectue via le fichier `org.apache.sling.datasource.DataSourceFactory.config`. Les pilotes JDBC pour les bases de données respectives doivent être fournis séparément en tant que lots OSGi dans la configuration locale.

Pour obtenir des instructions sur la création des lots OSGi pour les pilotes JDBC, consultez cette [ documentation](https://wiki.eclipse.org/Create_and_Export_MySQL_JDBC_driver_bundle) sur le site web Apache Sling.

>[!NOTE]
>
>Certains des pilotes SQL sont déjà conditionnés en tant que lots OSGi.
>
>Si c&#39;est le cas, copiez simplement le fichier jar à install-path/crx-quickstart/install/9.

Une fois que les lots sont en place, suivez les étapes ci-dessous en vue de configurer AEM avec la persistance RDB :

1. Assurez-vous que la base de données daemon est lancée et que votre base de données est active et prête à être utilisée avec AEM.
1. Copiez le jar AEM 6.3 dans le répertoire de l’installation.
1. Créez un dossier appelé `crx-quickstart\install` dans le répertoire d’installation.
1. Configurez l’entrepôt de nœud de document en créant un fichier de configuration avec le nom suivante dans le répertoire `crx-quickstart\install`:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Configurez la source de données et les paramètres JDBC en créant un autre fichier de configuration avec le nom suivant dans le dossier `crx-quickstart\install` :

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >Pour plus d’informations sur la configuration de chaque base de données prise en charge, voir [Options de configuration de la source de données](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. Ensuite, préparez les lots OSGi JDBC à utiliser avec AEM :

   1. Téléchargez l’archive ZIP à partir de https://dev.mysql.com/downloads/connector/j/
      * version doit être >= 5.1.38
   1. Extrayez le `mysql-connector-java-version-bin.jar` (lot) de l’archive.
   1. Utilisez la console web pour installer et démarrer le lot :
      * Accédez à *http://serveraddress:serverport/system/console/bundles*
      * Sélectionnez **Installer/Mettre à jour**
      * Accédez à la sélection du lot extrait de l’archive ZIP téléchargée.
      * Vérifiez que **Oracle Corporation&#39;s JDBC Driver for MySQLcom.mysql.jdbc** est principal et démarrez-le.

1. Enfin, commencez AEM par les modes d’exécution `crx3` et `crx3rdb` :

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## Options de configuration des sources de données {#data-source-configuration-options}

La configuration OSGi de `org.apache.sling.datasource.DataSourceFactory-oak.config` sert à configurer les paramètres nécessaires pour établir la communication entre AEM et la couche de persistance de la base de données.

Les options de configuration suivantes sont disponibles :

* `datasource.name:` Nom de la source de données. La valeur par défaut est de `oak`.

* `url:` Chaîne d’URL de la base de données qui doit être utilisée avec JDBC. Chaque type de base de données est doté de son propre format de chaîne d’URL. Pour plus d’informations, reportez-vous à la section [Formats de chaîne d’URL](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) ci-dessous.

* `driverClassName:` Nom de la classe du pilote JDBC. Cela varie en fonction de la base de données que vous souhaitez utiliser et du pilote nécessaire pour s’y connecter. Vous trouverez ci-dessous les noms de classe pour toutes les bases de données prises en charge par AEM :

   * `org.postgresql.Driver` pour PostgreSQL ;
   * `com.ibm.db2.jcc.DB2Driver` pour DB2 ;
   * `oracle.jdbc.OracleDriver` pour l&#39;Oracle;
   *  `com.mysql.jdbc.Driver` pour MySQL et MariaDB (expérimentaux) ;
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` pour Microsoft SQL Server (expérimental).

* `username:` Nom d’utilisateur sous lequel s’exécute la base de données.

* `password:` Mot de passe de la base de données.

### Formats de chaîne d’URL {#url-string-formats}

Un format de chaîne d’URL différent est utilisé dans la configuration de la source de données, en fonction du type de base de données qui doit être utilisé. Vous trouverez ci-dessous la liste des formats pour les bases de données actuellement prises en charge par AEM :

* `jdbc:postgresql:databasename` pour PostgreSQL ;

* `jdbc:db2://localhost:port/databasename` pour DB2 ;
* `jdbc:oracle:thin:localhost:port:SID` pour l&#39;Oracle;
*  `jdbc:mysql://localhost:3306/databasename` pour MySQL et MariaDB (expérimentaux) ;

* `jdbc:sqlserver://localhost:1453;databaseName=name` pour Microsoft SQL Server (expérimental).

## Limites connues {#known-limitations}

Bien que l’utilisation simultanée de plusieurs instances AEM avec une seule base de données est prise en charge par la persistance SGDBDR, les installations concomitantes ne sont pas.

Pour contourner ce problème, assurez-vous d’exécuter d’abord l’installation avec un seul membre et d’ajouter les autres à la fin de l’installation.
