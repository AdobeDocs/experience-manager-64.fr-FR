---
title: Déploiement de Communities
seo-title: Déploiement de Communities
description: Comment déployer le AEM Communities
seo-description: Comment déployer le AEM Communities
uuid: 1f7faf1a-a339-4eaa-b728-b9110cb350a8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: d0249609-2a9c-4d3b-92ee-dbc5fbdeaac6
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 5%

---


# Déploiement de Communities {#deploying-communities}

## Conditions préalables {#prerequisites}

* [AEM 6.4 Platform](../../help/sites-deploying/deploy.md)

* Licence AEM Communities

* Licences facultatives pour :

   * [Adobe Analytics for Communities, fonctions](analytics.md)
   * [MongoDB pour MSRP](msrp.md)
   * [Adobe Cloud pour ASRP](asrp.md)

## Liste de contrôle d&#39;installation {#installation-checklist}

**Pour la plate-forme[AEM](../../help/sites-deploying/deploy.md#what-is-aem)**

* Installer les dernières mises à jour [d’AEM 6.4](#aem-updates)

* Si vous n&#39;utilisez pas les ports par défaut (4502, 4503), [configurez les agents de réplication.](#replication-agents-on-author)
* [répliquer la clé de chiffrement](#replicate-the-crypto-key)
* En cas de prise en charge de la mondialisation, [configurer la traduction automatisée](../../help/sites-administering/translation.md)

   (l’exemple de configuration est fourni pour le développement)

**Pour la fonctionnalité[Communautés](overview.md)**

* Si vous déployez une batterie [de](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)publication, [identifiez l’éditeur principal.](#primary-publisher)

* [Activation du service de tunnel](#tunnel-service-on-author)
* [Activer la connexion sociale](social-login.md#adobe-granite-oauth-authentication-handler)
* [Configuration d’Adobe Analytics](analytics.md)
* Configuration d’un service de messagerie [par défaut](email.md)
* Identifier le choix pour l&#39;enregistrement [UGC](working-with-srp.md) partagé (**SRP**)

   * Si MongoDB SRP [(MSRP)](msrp.md)

      * [Installation et configuration de MongoDB](msrp.md#mongodb-configuration)
      * [Configurer Solr](solr.md)
      * [Sélectionner MSRP](srp-config.md)
   * Si SRP de base de données relationnelle [(DSRP)](dsrp.md)

      * [Installation du pilote JDBC pour MySQL](#jdbc-driver-for-mysql)
      * [Installation et configuration de MySQL pour DSRP](dsrp-mysql.md)
      * [Configurer Solr](solr.md)
      * [Sélectionner DSRP](srp-config.md)
   * Si Adobe SRP [(ASRP)](asrp.md)

      * Travailler avec votre gestionnaire de compte pour la mise en service
      * [Sélectionner ASRP](srp-config.md)
   * Si JCR SRP [(JSRP)](jsrp.md)

      * Pas un magasin UGC partagé :

         * UGC n’est jamais répliqué
         * UGC uniquement visible sur l’instance ou la grappe AEM dans laquelle il a été saisi
      * Par défaut, JSRP

   Pour la fonction **[d’activation](overview.md#enablement-community)**

   * [Installation et configuration de FFmpeg](ffmpeg.md)
   * [Installation du pilote JDBC pour MySQL](#jdbc-driver-for-mysql)
   * [Installation de AEM Communities SCORM-Engine](#scorm-package)
   * [Installation et configuration de MySQL pour activation](mysql.md)






## Latest Releases {#latest-releases}

AEM 6.4 Communities GA fournit un package Communities. Pour en savoir plus sur les mises à jour des [communautés](/help/release-notes/release-notes.md#experience-manager-communities)AEM 6.4, consultez les Notes [de mise à jour d’](/help/release-notes/release-notes.md#release-information)AEM 6.4.

### Mises à jour d’AEM 6.4 {#aem-updates}

À partir d’AEM 6.3, les mises à jour apportées aux communautés sont fournies dans le cadre des Service Packs et Fix Packs cumulatifs d’AEM.

Pour connaître les dernières mises à jour d’AEM 6.4, veillez à vérifier les packs de correctifs et les Service Packs de l’ [](https://helpx.adobe.com/fr/experience-manager/aem-releases-updates.html)Adobe Experience Manager 6.4.

### Version History {#version-history}

Comme pour AEM 6.4 et les versions ultérieures, les fonctionnalités et correctifs AEM Communities font partie des packs de correctifs et Service Packs cumulatifs AEM Communities. Il n&#39;y a donc pas de fonctionnalités distinctes.

### Pilote JDBC pour MySQL {#jdbc-driver-for-mysql}

Deux fonctionnalités Communities utilisent une base de données MySQL :

* Pour [l&#39;activation](enablement.md): enregistrement des activités et des apprenants SCORM
* Pour [DSRP](dsrp.md): stockage du contenu généré par l’utilisateur (UGC)

Le connecteur MySQL doit être obtenu et installé séparément.

Les étapes nécessaires sont les suivantes :

1. Téléchargez l’archive ZIP à partir de [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * La version doit être >= 5.1.38

1. Extraire mysql-connector-java-&lt;version>-bin.jar (bundle) de l&#39;archive

1. Utilisez la console Web pour installer et début le lot :

   * Par exemple, http://localhost:4502/system/console/bundles
   * Sélectionner **`Install/Update`**
   * Parcourir... pour sélectionner le lot extrait de l&#39;archive ZIP téléchargée
   * Vérifiez que le pilote JDBC d&#39; *Oracle Corporation pour MySQLcom.mysql.jdbc* est actif et début-le si ce n&#39;est pas le cas (ou vérifiez les journaux).

1. Si vous effectuez l’installation sur un déploiement existant après la configuration de JDBC, regroupez JDBC sur le nouveau connecteur en réenregistrant la configuration JDBC à partir de la console Web :

   * Par exemple, http://localhost:4502/system/console/configMgr
   * Localisation de la `Day Commons JDBC Connections Pool` configuration
   * Sélectionner pour ouvrir
   * Sélectionner `Save`

1. Répétez les étapes 3 et 4 sur toutes les instances d’auteur et de publication.

Pour plus d&#39;informations sur l&#39;installation des lots, consultez la page Console [](/help/sites-deploying/web-console.md#bundles) Web.

#### Exemple : Groupe MySQL Connector installé {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### Package SCORM {#scorm-package}

SCORM (Shareable Content Object Reference Model) est un ensemble de normes et de spécifications pour l&#39;apprentissage en ligne. SCORM définit également comment le contenu peut être inclus dans un fichier ZIP transférable.

Le moteur SCORM AEM Communities est requis pour la fonction d’ [activation](overview.md#enablement-community) . Les paquets Scorm pris en charge sur la version 6.4 AEM Communities sont les suivants :

* **[cq -social-scorm -package, version 1.2.11](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-pkg)**. Ce package SCORM est pris en charge par toutes les versions des communautés AEM 6.4.

* **[cq -social-scorm -package, version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)**inclut le moteur[SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/). Ce package SCORM est pris en charge par les communautés AEM 6.4.2.x à partir de.

Pour une nouvelle installation du moteur SCORM, le package contenant [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) (qui est [ cq -social-scorm -package, version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)) doit être utilisé. Pour que vous puissiez lire les ressources d’apprentissage prises en charge par SCORM 2017.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Pour installer un pack SCORM pour la première fois

1. Installez le **[package cq-social-scorm-package, version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Téléchargez **`/libs/social/config/scorm/database_scormengine_data.sql`** l&#39;instance cq et exécutez-la dans mysql server pour créer un schéma scormEngineDB mis à niveau.
1. Ajoutez `/content/communities/scorm/RecordResults` dans la propriété Chemins exclus du filtre CSRF depuis `https://<hostname>;:<port>/system/console/configMgr` les éditeurs.

Les installations SCORM existantes peuvent être mises à niveau vers [**cq-social-scorm-package, version 2.2.2 **](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)(qui utilise[SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)), si le contenu du cours créé nécessite SCORM 2017.1.

>[!NOTE]
>
>La mise à niveau vers le package SCORM 2017.1 nécessite la migration de la base de données existante (comme expliqué plus loin).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Pour mettre à niveau la version de votre moteur SCORM

1. Sauvegardez le schéma ScormEngineDB.
1. Installez le **[package cq-social-scorm-package, version 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Téléchargez le package à partir `/libs/social/config/scorm/ScormEngine.zip` de et extrayez le même.
1. Accédez au dossier **Installer** du répertoire extrait.
1. Effectuez une mise à jour `SystemDatabaseConnectionString` à l’aide de votre `scorm db connection url` fichier **[!UICONTROL EngineInstall.xml]**.
1. Exécutez l&#39;outil de mise à niveau de schéma mysql dans le dossier Installer avec la commande :

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Surveillez `engine_upgrade.log` le fichier pour toute erreur et tout état de mise à niveau de schéma.
1. Ajoutez `/content/communities/scorm/RecordResults` dans la propriété Chemins **** exclus du filtre CSRF depuis `https://<hostname>:<port>/system/console/configMgr` les éditeurs.

### Journalisation SCORM {#scorm-logging}

Au fur et à mesure de l&#39;installation, toute activité d&#39;activation est généreusement consignée dans la console système.

Si vous le souhaitez, le niveau de journal peut être défini sur WARN pour le `RusticiSoftware.*` package.

Pour utiliser les journaux, voir [Utilisation des enregistrements d’audit et des fichiers](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)journaux.

### MLS AEM Advanced {#aem-advanced-mls}

Pour que la collection SRP (MSRP ou DSRP) prenne en charge la recherche multilingue avancée (MLS), de nouveaux modules externes Solr sont requis en plus d&#39;un schéma personnalisé et d&#39;une configuration Solr. Tous les éléments requis sont compressés dans un fichier zip téléchargeable.

Le téléchargement MLS avancé (également appelé &quot;phasetwo&quot;) est disponible à partir du référentiel Adobe :

* [AEM-SOLR-MLS-phasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Version 1.2.40, 6 avril 2016
   * Télécharger AEM-SOLR-MLS-phasetwo-1.2.40.zip

Pour plus d&#39;informations sur l&#39;installation et les détails, consultez Configuration [](solr.md) Solr pour SRP.

### A propos des liens vers le partage de package {#about-links-to-package-share}

**Packages visibles dans Adobe AEM Cloud**

Les liens vers les packages sur cette page ne nécessitent aucune instance en cours d’exécution d’AEM, car ils sont destinés au partage de packages sur `adobeaemcloud.com`. Bien que les packages puissent être consultés, le `Install`bouton permet d’installer les packages sur un site hébergé par Adobe. Si vous prévoyez d’installer sur une instance locale AEM, la sélection `Install`provoquera une erreur.

**Installation sur une instance locale AEM**

Pour installer les packages visibles dans `adobeaemcloud.com` une instance locale AEM, le package doit d’abord être téléchargé sur un disque local :

* Select the **[!UICONTROL Assets]** tab
* Select **[!UICONTROL download to disk]**

Sur l’instance locale d’AEM, utilisez le gestionnaire de packages (par exemple [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)) pour télécharger le package vers le référentiel de packages local d’AEM.

Vous pouvez également accéder au package à l’aide du partage de package depuis l’instance locale AEM (par exemple, [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)). Le `Download`bouton sera téléchargé dans le référentiel de packages de l’instance locale AEM.

Une fois que vous êtes dans le référentiel de packages de l’instance locale AEM, utilisez le gestionnaire de packages pour installer le package.

Pour plus d’informations, consultez [Comment utiliser des packages](../../help/sites-administering/package-manager.md#package-share).

## Déploiements recommandés {#recommended-deployments}

En AEM Communities, un magasin commun est utilisé pour stocker le contenu généré par l’utilisateur et est souvent appelé fournisseur de ressources d’ [enregistrement (SRP)](working-with-srp.md). Le déploiement recommandé se concentre sur le choix d’une option SRP pour la boutique commune.

Le magasin commun prend en charge la modération et l’analyse de l’UGC dans l’environnement de publication tout en éliminant la nécessité de [réplication](sync.md) de l’UGC.

* [Community Content Store](working-with-srp.md): décrit les options d’enregistrement SRP pour les communautés AEM

* [Topologies](topologies.md)recommandées : décrit la topologie à utiliser en fonction du cas d&#39;utilisation et du choix SRP

## Mise à niveau {#upgrading}

Lors de la mise à niveau vers la plate-forme AEM 6.4 à partir des versions précédentes d’AEM, il est important de lire Mise à niveau vers AEM 6.4.

Outre la mise à niveau de la plateforme, consultez [Mise à niveau vers AEM Communities 6.4](upgrade.md) pour en savoir plus sur les modifications apportées aux communautés.

## Configurations {#configurations}

### Principal Editeur {#primary-publisher}

Lorsque le déploiement choisi est une batterie de [publication](topologies.md#tarmk-publish-farm), une instance de publication AEM doit être identifiée comme **`primary publisher`** pour les activités qui ne doivent pas se produire sur toutes les instances, telles que les fonctionnalités qui reposent sur des **notifications** ou sur le Analytics **** Adobe.

Par défaut, la configuration `AEM Communities Publisher Configuration` OSGi est configurée avec la **`Primary Publisher`** case cochée, de sorte que toutes les instances de publication d’une batterie de publication s’identifient elles-mêmes comme étant la principale.

Par conséquent, il est nécessaire de **modifier la configuration sur toutes les instances** de publication secondaires pour décocher la **`Primary Publisher`** case.

![chlimage_1-411](assets/chlimage_1-411.png)

Pour toutes les autres instances de publication (secondaires) d’une batterie de publication :

* Connexion avec droits d’administrateur
* Access the [web console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localisez la variable `AEM Communities Publisher Configuration`
* Sélectionner l’icône de modification
* Décochez la case **[!UICONTROL Principal Publisher]** (Editeur).
* Sélectionnez **[!UICONTROL Enregistrer]**

### Agents de réplication sur l’auteur {#replication-agents-on-author}

La réplication est utilisée pour le contenu du site créé dans l’environnement de publication, tel que les groupes de la communauté, ainsi que pour la gestion des membres et des groupes de membres de l’environnement d’auteur à l’aide du service [](#tunnel-service-on-author)tunnel.

Pour l’éditeur principal, assurez-vous que la configuration [de l’agent de](../../help/sites-deploying/replication.md) réplication identifie correctement le serveur de publication et l’utilisateur autorisé. L’utilisateur autorisé par défaut `admin,` dispose déjà des autorisations appropriées (est membre de `Communities Administrators`).

Pour qu’un autre utilisateur dispose des autorisations appropriées, il doit être ajouté en tant que membre du groupe d’ `administrators` utilisateurs (également membre de `Communities Administrators`).

Deux agents de réplication de l&#39;environnement d&#39;auteur doivent être configurés correctement pour la configuration du transport.

* Accès à la console de réplication sur l’auteur

   * A partir de la navigation globale : **[!UICONTROL Outils > Déploiement > Réplication > Agents sur l’auteur]**

* Suivez la même procédure pour les deux agents :

   * **Agent par défaut (publication)**
   * **Agent de réplication inverse (inversion de publication)**

      1. Sélectionner l&#39;agent
      1. Select **[!UICONTROL edit]**
      1. Select the **[!UICONTROL Transport]** tab
      1. Si ce n’est pas le port `4503`, modifiez l’ **[!UICONTROL URI]** pour spécifier le port correct.
      1. Si vous n’utilisez pas `admin`, modifiez l’ **[!UICONTROL utilisateur]** et le **[!UICONTROL mot de passe]** pour spécifier un membre du groupe `administrators` d’utilisateurs.

Les images suivantes montrent les résultats du changement de port de 4503 à 6103 par :

#### Agent par défaut (publication) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Agent de réplication inverse (inversion de publication) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Service de tunnel sur l’auteur {#tunnel-service-on-author}

Lors de l’utilisation de l’environnement d’auteur pour [créer des sites](sites-console.md), [modifier des propriétés](sites-console.md#modifying-site-properties) du site ou [gérer des membres](members.md)de la communauté, il est nécessaire d’accéder aux membres (utilisateurs) enregistrés dans l’environnement de publication, et non aux utilisateurs enregistrés dans l’ d’auteur.

Le service tunnel fournit cet accès à l&#39;aide de l&#39;agent de réplication sur l&#39;auteur.

Pour activer le service de tunnel :

* On **author**
* Connexion avec des droits d’administrateur
* Si l’éditeur n’est pas localhost:4503 ou que l’utilisateur de transport ne l’est pas `admin`,

   Then [configure the replication agent](#replication-agents-on-author)

* Access the [Web Console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Localisez la variable `AEM Communities Publish Tunnel Service`
* Sélectionner l’icône de modification
* Cochez la case **[!UICONTROL activer]** .
* Sélectionnez **[!UICONTROL Enregistrer]**

![chlimage_1-414](assets/chlimage_1-414.png)

### Réplication de la clé Crypto {#replicate-the-crypto-key}

Deux fonctions de AEM Communities nécessitent que toutes les instances de serveur AEM utilisent les mêmes clés de chiffrement. Voici [Analytics](analytics.md) et [ASRP](asrp.md).

Depuis AEM 6.3, le matériel clé est stocké dans le système de fichiers et ne se trouve plus dans le référentiel.

Pour copier la documentation clé de l&#39;auteur vers toutes les autres instances, il est nécessaire de :

* Accédez à l’instance AEM, généralement une instance d’auteur, qui contient le matériel clé à copier.

   * Locate the `com.adobe.granite.crypto.file` bundle in the local file system

      Par exemple :

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Le `bundle.info` fichier identifie le lot
   * Accédez au dossier de données

      Par exemple :

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Copier les fichiers hmac et de noeud principal



* Pour chaque instance AEM de cible

   * Accédez au dossier de données

      Par exemple :

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Coller les 2 fichiers copiés précédemment
   * Il est nécessaire d’ [actualiser le lot](#refresh-the-granite-crypto-bundle) Granite Crypto si l’instance AEM de cible est en cours d’exécution.


>[!CAUTION]
>
>Si une autre fonction de sécurité a déjà été configurée basée sur les clés de cryptage, la réplication des clés de cryptage pourrait endommager la configuration. Pour obtenir de l’aide, [contactez le service à la clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html).

#### Réplication du référentiel {#repository-replication}

La conservation du matériel clé stocké dans le référentiel, comme pour AEM 6.2 et les versions antérieures, peut s’effectuer en spécifiant la propriété système suivante au premier démarrage de chaque instance AEM (qui crée le référentiel initial) :

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Il est important de vérifier que l&#39;agent de [réplication sur l&#39;auteur](#replication-agents-on-author) est correctement configuré.

Avec le matériel clé stocké dans le référentiel, la manière de répliquer la clé de chiffrement de l&#39;auteur à d&#39;autres instances est la suivante :

Using [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* accédez à [https://&lt;serveur>:&lt;port>/crx/de.](http://localhost:4502/crx/de)
* select `/etc/key`
* ouvrir `Replication` l’onglet
* select `Replicate`

* [actualisation du lot Granite Crypto](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Actualiser l&#39;offre groupée Granite Crypto {#refresh-the-granite-crypto-bundle}

* Sur chaque instance de publication, accédez à la console [Web](../../help/sites-deploying/configuring-osgi.md)

   * Par exemple, [https://&lt;serveur>:&lt;port>/system/console/bundles](http://localhost:4503/system/console/bundles)

* Localisez le `Adobe Granite Crypto Support` lot (com.adobe.granite.crypto)
* Sélectionner **[!UICONTROL Actualiser]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Après un moment, une boîte de dialogue **Réussite** s’affiche :

   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Si vous utilisez le serveur Apache HTTP, veillez à utiliser le nom de serveur correct pour toutes les entrées appropriées.

En particulier, veillez à utiliser le nom de serveur correct, et non `localhost`le nom, dans le `RedirectMatch`.

#### exemple httpd.conf {#httpd-conf-sample}

```shell
<IfModule alias_module>
     # XAMPP does not have a favicon; this prevents any 404 errors which may arise.
     Redirect 404 /favicon.ico
     <Location /favicon.ico>
         ErrorDocument 404 "No favicon"
     </Location>

    # Return from "Sign Out" generates response header directing you to "/", generating a 404 error
    # The RedirectMatch resolves it correctly when modified for the target Community Site:
    RedirectMatch ^/$ https://[server name]/content/sites/engage/en.html
 ...
 </IfModule>
```

### Dispatcher {#dispatcher}

Si vous utilisez un Dispatcher, voir :

* Documentation du [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) d’AEM
* [Installation de Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Configuration du Dispatcher pour les communautés](dispatcher.md)
* [Problèmes connus](troubleshooting.md#dispatcher-refetch-fails)

## Documentation sur les communautés associée {#related-communities-documentation}

* Reportez-vous à la section [Administration des sites de communauté](administer-landing.md) pour en savoir plus sur la création d’un site de communauté, la configuration de modèles de sites de communauté, la modération du contenu de communauté, la gestion des membres et la configuration de la messagerie.

* Visit [Developing Communities](communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.

* Visitez la page Composants [Communautés](author-communities.md) de création pour découvrir comment créer et configurer des composants Communautés.

