---
title: Déploiement de Communities
seo-title: Deploying Communities
description: Comment déployer AEM Communities
seo-description: How to deploy AEM Communities
uuid: 1f7faf1a-a339-4eaa-b728-b9110cb350a8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: d0249609-2a9c-4d3b-92ee-dbc5fbdeaac6
exl-id: 0b7496f0-0b3c-4d12-a659-d95744157f14
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2216'
ht-degree: 5%

---

# Déploiement de Communities {#deploying-communities}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Prérequis {#prerequisites}

* [Plateforme AEM 6.4](../../help/sites-deploying/deploy.md)

* Licence AEM Communities

* Licences facultatives pour :

   * [Fonctionnalités d’Adobe Analytics for Communities](analytics.md)
   * [MongoDB pour MSRP](msrp.md)
   * [Adobe Cloud pour ASRP](asrp.md)

## Liste de contrôle d’installation {#installation-checklist}

**Pour le [AEM plateforme](../../help/sites-deploying/deploy.md#what-is-aem)**

* Installer la dernière [Mises à jour AEM 6.4](#aem-updates)

* Si vous n’utilisez pas les ports par défaut (4502, 4503), [configuration des agents de réplication](#replication-agents-on-author)
* [répliquer la clé de chiffrement](#replicate-the-crypto-key)
* Si elle soutient la mondialisation, [configuration de la traduction automatisée](../../help/sites-administering/translation.md)

   (l’exemple de configuration est fourni pour le développement)

**Pour le [Fonctionnalités des communautés](overview.md)**

* Si vous déployez une [batterie de publication](../../help/sites-deploying/recommended-deploys.md#tarmk-farm), [identification de l’éditeur Principal](#primary-publisher)

* [Activation du service tunnel](#tunnel-service-on-author)
* [Activation de la connexion sociale](social-login.md#adobe-granite-oauth-authentication-handler)
* [Configuration d’Adobe Analytics](analytics.md)
* Configuration d’une [service de messagerie par défaut](email.md)
* Identifier le choix pour [stockage UGC partagé](working-with-srp.md) (**SRP**)

   * Si MongoDB SRP [(MSRP)](msrp.md)

      * [Installation et configuration de MongoDB](msrp.md#mongodb-configuration)
      * [Configuration de Solr](solr.md)
      * [Sélectionner MSRP](srp-config.md)
   * Si SRP de base de données relationnelle [(DSRP)](dsrp.md)

      * [Installation du pilote JDBC pour MySQL](#jdbc-driver-for-mysql)
      * [Installation et configuration de MySQL pour DSRP](dsrp-mysql.md)
      * [Configuration de Solr](solr.md)
      * [Sélectionner DSRP](srp-config.md)
   * Si Adobe SRP [(ASRP)](asrp.md)

      * Utilisation de votre gestionnaire de compte pour l’approvisionnement
      * [Sélectionner ASRP](srp-config.md)
   * Si JCR SRP [(JSRP)](jsrp.md)

      * Pas un magasin UGC partagé :

         * Le contenu généré par l’utilisateur n’est jamais répliqué.
         * Contenu généré par l’utilisateur visible uniquement sur l’instance AEM ou la grappe dans laquelle il a été saisi
      * La valeur par défaut est JSRP

   Pour le **[fonction d’activation](overview.md#enablement-community)**

   * [Installation et configuration de FFmpeg](ffmpeg.md)
   * [Installation du pilote JDBC pour MySQL](#jdbc-driver-for-mysql)
   * [Installation d’AEM Communities SCORM-Engine](#scorm-package)
   * [Installation et configuration de MySQL pour activation](mysql.md)






## Dernières versions {#latest-releases}

AEM 6.4 Communities GA inclut le package Communities. Pour en savoir plus sur les mises à jour d’AEM 6.4 [Communautés](/help/release-notes/release-notes.md#experience-manager-communities), voir [Notes de mise à jour d’AEM 6.4](/help/release-notes/release-notes.md#release-information).

### Mises à jour AEM 6.4 {#aem-updates}

À compter de la version 6.3 d’AEM, les mises à jour apportées aux communautés sont fournies dans le cadre d’AEM Cumulative Fix Packs et Service Packs.

Pour connaître les dernières mises à jour d’AEM 6.4, veillez à vérifier [Packs de correctifs cumulatifs et Service Packs Adobe Experience Manager 6.4](https://helpx.adobe.com/fr/experience-manager/aem-releases-updates.html).

### Historique des versions {#version-history}

Comme pour AEM 6.4 et versions ultérieures, les fonctionnalités et correctifs d’AEM Communities font partie des packs de correctifs cumulatifs et des Service Packs d’AEM Communities. Il n’existe donc aucun Feature Pack distinct.

### Pilote JDBC pour MySQL {#jdbc-driver-for-mysql}

Deux fonctionnalités de Communities utilisent une base de données MySQL :

* Pour [activation](enablement.md): enregistrement des activités SCORM et des apprenants
* Pour [DSRP](dsrp.md): stockage du contenu généré par l’utilisateur

Le connecteur MySQL doit être obtenu et installé séparément.

Les étapes nécessaires sont les suivantes :

1. Téléchargez l’archive ZIP à partir de [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * La version doit être >= 5.1.38

1. Extraire mysql-connector-java-&lt;version>-bin.jar (lot) à partir de l’archive

1. Utilisez la console web pour installer et démarrer le lot :

   * Par exemple, http://localhost:4502/system/console/bundles
   * Sélectionner **`Install/Update`**
   * Parcourir.. pour sélectionner le lot extrait de l’archive ZIP téléchargée
   * Vérifiez que *Pilote JDBC d’Oracle Corporation pour MySQLcom.mysql.jdbc* est principale et démarrez-la si ce n’est pas le cas (ou vérifiez les journaux).

1. Si vous effectuez l’installation sur un déploiement existant après la configuration de JDBC, replacez JDBC sur le nouveau connecteur en réenregistrant la configuration JDBC à partir de la console web :

   * Par exemple, http://localhost:4502/system/console/configMgr
   * Localiser `Day Commons JDBC Connections Pool` configuration
   * Sélectionner pour ouvrir
   * Sélectionner `Save`

1. Répétez les étapes 3 et 4 sur toutes les instances d’auteur et de publication.

Vous trouverez plus d’informations sur l’installation des lots sur la page [Console web](/help/sites-deploying/web-console.md#bundles) page.

#### Exemple : Bundle MySQL Connector installé {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### Package SCORM {#scorm-package}

SCORM (Share Content Object Reference Model) est un ensemble de normes et de spécifications pour l’apprentissage en ligne. SCORM définit également la manière dont le contenu peut être compressé dans un fichier ZIP transférable.

Le moteur SCORM AEM Communities est requis pour la variable [activation](overview.md#enablement-community) fonction . Les packages de notation pris en charge sur la version 6.4 d’AEM Communities sont les suivants :

* **[cq -social-scorm-package, version 1.2.11](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-pkg)**. Ce package SCORM est pris en charge par toutes les versions d’AEM Communities 6.4.

* **[cq-social-scorm-package, version 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg)** inclut [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) moteur. Ce package SCORM est pris en charge AEM Communities 6.4.2.x et versions ultérieures.

Pour une nouvelle installation du moteur SCORM, le module contenant [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) (qui est [  cq-social-scorm-package, version 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg)) doit être utilisé. Afin que vous puissiez lire les ressources d’apprentissage prises en charge par SCORM 2017.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Pour installer un package SCORM pour la première fois

1. Installez le **[cq-social-scorm-package, version 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg).**
1. Télécharger **`/libs/social/config/scorm/database_scormengine_data.sql`** à partir de l’instance cq et exécutez-la dans le serveur mysql pour créer un schéma scormEngineDB mis à niveau.
1. Ajouter `/content/communities/scorm/RecordResults` dans la propriété Chemins exclus du filtre CSRF de `https://<hostname>;:<port>/system/console/configMgr` sur les éditeurs.

Les installations SCORM existantes peuvent être mises à niveau vers [**cq-social-scorm-package, version 2.2.2**](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg) (qui utilise [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)), si le contenu du cours créé nécessite SCORM 2017.1.

>[!NOTE]
>
>La mise à niveau vers le package SCORM 2017.1 nécessite la migration de la base de données existante (comme expliqué plus loin).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Pour mettre à niveau la version de votre moteur SCORM

1. Effectuez une sauvegarde du schéma ScormEngineDB.
1. Installez le **[cq-social-scorm-package, version 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg).**
1. Téléchargez le module depuis `/libs/social/config/scorm/ScormEngine.zip` et extrayez le même.
1. Accédez à **Programme** du répertoire extrait.
1. Mettre à jour `SystemDatabaseConnectionString` avec votre `scorm db connection url` dans le fichier **[!UICONTROL EngineInstall.xml]**.
1. Exécutez l&#39;outil de mise à niveau de schéma mysql dans le dossier Installer avec la commande :

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Surveiller `engine_upgrade.log` pour tout type d’erreur et l’état de mise à niveau du schéma.
1. Ajouter `/content/communities/scorm/RecordResults` in **[!UICONTROL Chemins exclus]** propriété dans le filtre CSRF à partir de `https://<hostname>:<port>/system/console/configMgr` sur les éditeurs.

### Journalisation SCORM {#scorm-logging}

Lors de l’installation, toutes les activités d’activation sont généreusement consignées dans la console système.

Si vous le souhaitez, le niveau de journal peut être défini sur WARN pour la variable `RusticiSoftware.*` module.

Pour utiliser les journaux, voir [Utilisation des enregistrements d’audit et des fichiers journaux](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### AEM MLS avancés {#aem-advanced-mls}

Pour que la collection SRP (MSRP ou DSRP) prenne en charge la recherche multilingue avancée (MLS), de nouveaux modules externes Solr sont requis en plus d’un schéma personnalisé et d’une configuration Solr. Tous les éléments requis sont compressés dans un fichier ZIP téléchargeable.

Le téléchargement MLS avancé (également appelé &quot;phasetwo&quot;) est disponible à partir du référentiel Adobe :

* AEM-SOLR-MLS-phasetwo

   Pour obtenir le package MLS avancé, voir [AEM MLS avancés](deploy-communities.md#aem-advanced-mls) dans la section deploy de la documentation.

   * Version 1.2.40, 6 avril 2016
   * Téléchargez AEM-SOLR-MLS-phasetwo-1.2.40.zip

Pour plus d’informations sur l’installation, voir [Configuration de Solr](solr.md) pour la SRP.

### À propos des liens vers le partage de modules {#about-links-to-package-share}

**Modules visibles dans Adobe AEM Cloud**

Les liens vers les modules de cette page ne nécessitent aucune instance d’AEM en cours d’exécution, car ils doivent être partagés sur `adobeaemcloud.com`. Bien que les modules soient visibles, la variable `Install`est destiné à installer les packages sur un site hébergé par Adobe. Si vous envisagez d’installer sur une instance d’AEM locale, sélectionnez `Install`entraînera une erreur.

**Installation sur une instance d’AEM locale**

Pour installer les packages visibles dans `adobeaemcloud.com` sur une instance d’AEM locale, le package doit d’abord être téléchargé sur un disque local :

* Sélectionnez la **[!UICONTROL Ressources]** tab
* Sélectionner **[!UICONTROL télécharger sur le disque]**

Sur l’instance d’AEM locale, utilisez le gestionnaire de modules (par exemple [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)), pour charger vers le référentiel de package d’AEM local.

Vous pouvez également accéder au module à l’aide du partage de module à partir de l’instance d’AEM locale (par exemple, [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)), la variable `Download`télécharge vers le référentiel de package de l’instance AEM locale.

Une fois que vous êtes dans le référentiel de package de l’instance d’AEM locale, utilisez le gestionnaire de packages pour installer le package.

Pour plus d’informations, voir [Utilisation de modules](../../help/sites-administering/package-manager.md#package-share).

## Déploiements recommandés {#recommended-deployments}

Dans AEM Communities, un magasin commun est utilisé pour stocker le contenu généré par l’utilisateur et est souvent appelé [fournisseur de ressources de stockage (SRP)](working-with-srp.md). Le déploiement recommandé consiste à choisir une option SRP pour le magasin commun.

Le magasin commun prend en charge la modération et l’analyse du contenu créé par l’utilisateur dans l’environnement de publication, tout en éliminant la nécessité de [réplication](sync.md) de contenu généré par l’utilisateur.

* [Community Content Store](working-with-srp.md): présente les options de stockage SRP pour les communautés AEM

* [Topologies recommandées](topologies.md): aborde la topologie à utiliser en fonction du cas d’utilisation et du choix de la SRP.

## Mise à niveau {#upgrading}

Lors de la mise à niveau vers la plateforme AEM 6.4 à partir des versions précédentes d’AEM, il est important de lire Mise à niveau vers la version 6.4 d’AEM.

En plus de la mise à niveau de la plateforme, lisez [Mise à niveau vers AEM Communities 6.4](upgrade.md) pour en savoir plus sur les modifications apportées aux communautés.

## Configurations {#configurations}

### Éditeur Principal {#primary-publisher}

Lorsque le déploiement sélectionné est un [batterie de publication](topologies.md#tarmk-publish-farm), une instance de publication AEM doit être identifiée en tant que **`primary publisher`** pour les activités qui ne doivent pas se produire sur toutes les instances, telles que les fonctionnalités qui dépendent de **notifications** ou **Adobe Analytics**.

Par défaut, la variable `AEM Communities Publisher Configuration` La configuration OSGi est configurée avec le **`Primary Publisher`** case à cocher cochée, de sorte que toutes les instances de publication d’une ferme de publication s’identifient elles-mêmes comme Principales.

Par conséquent, il est nécessaire de **modifier la configuration sur toutes les instances de publication secondaires ;** pour décocher la variable **`Primary Publisher`** .

![chlimage_1-411](assets/chlimage_1-411.png)

Pour toutes les autres instances de publication (secondaires) dans une ferme de publication :

* Connexion avec droits d’administrateur
* Accédez au [console web](../../help/sites-deploying/configuring-osgi.md)

   * Par exemple : [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Recherchez la variable `AEM Communities Publisher Configuration`
* Sélectionner l’icône de modification
* Décochez la case **[!UICONTROL Éditeur Principal]** box
* Sélectionnez **[!UICONTROL Enregistrer]**.

### Agents de réplication sur l’auteur {#replication-agents-on-author}

La réplication est utilisée pour le contenu du site créé dans l’environnement de publication, comme les groupes de la communauté, ainsi que pour la gestion des membres et des groupes de membres de l’environnement de création à l’aide de la fonction [service tunnel](#tunnel-service-on-author).

Pour l’éditeur Principal, assurez-vous que la variable [Configuration de l’agent de réplication](../../help/sites-deploying/replication.md) identifie correctement le serveur de publication et l’utilisateur autorisé. l’utilisateur autorisé par défaut, `admin,` dispose déjà des autorisations appropriées (est membre de `Communities Administrators`).

Pour qu’un autre utilisateur dispose des autorisations appropriées, il doit être ajouté en tant que membre à la variable `administrators` groupe d’utilisateurs (également membre de `Communities Administrators`).

Il existe deux agents de réplication dans l’environnement de création qui ont besoin que la configuration du transport soit correctement configurée.

* Accès à la console de réplication sur l’auteur

   * À partir de la navigation globale : **[!UICONTROL Outils > Déploiement > Réplication > Agents sur l’auteur]**

* Suivez la même procédure pour les deux agents :

   * **Agent par défaut (publication)**
   * **Agent de réplication inverse (publication inversée)**

      1. Sélectionner l’agent
      1. Sélectionner **[!UICONTROL edit]**
      1. Sélectionnez la **[!UICONTROL Transport]** tab
      1. Si pas de port `4503`, modifiez la variable **[!UICONTROL URI]** pour spécifier le port correct
      1. Si l’utilisateur n’est pas `admin`, modifiez la variable **[!UICONTROL Utilisateur]** et **[!UICONTROL Mot de passe]** pour spécifier un membre de la fonction `administrators` groupe d’utilisateurs

Les images suivantes montrent les résultats du changement de port de 4503 à 6103 en :

#### Agent par défaut (publication) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Agent de réplication inverse (publication inversée) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Service Tunnel sur l’auteur {#tunnel-service-on-author}

Lors de l’utilisation de l’environnement de création dans [créer des sites ;](sites-console.md), [modification des propriétés du site](sites-console.md#modifying-site-properties) ou [gestion des membres de la communauté](members.md), il est nécessaire d’accéder aux membres (utilisateurs) enregistrés dans l’environnement de publication, et non aux utilisateurs enregistrés dans l’environnement de création.

Le service tunnel fournit cet accès à l’aide de l’agent de réplication sur l’auteur.

Pour activer le service tunnel :

* Activé **author**
* Connexion avec droits d’administrateur
* Si l’éditeur n’est pas localhost:4503 ou que l’utilisateur du transport ne l’est pas `admin`,

   Alors [configuration de l’agent de réplication](#replication-agents-on-author)

* Accédez au [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Par exemple : [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Recherchez la variable `AEM Communities Publish Tunnel Service`
* Sélectionner l’icône de modification
* Vérifiez les **[!UICONTROL enable]** box
* Sélectionnez **[!UICONTROL Enregistrer]**.

![chlimage_1-414](assets/chlimage_1-414.png)

### Réplication de la clé de chiffrement {#replicate-the-crypto-key}

Il existe deux fonctionnalités d’AEM Communities qui nécessitent que toutes les instances AEM serveur utilisent les mêmes clés de chiffrement. Voici les [Analytics](analytics.md) et [ASRP](asrp.md).

À compter de la version AEM 6.3, le matériel clé est stocké dans le système de fichiers et ne figure plus dans le référentiel.

Pour copier les documents clés de l’auteur vers toutes les autres instances, il est nécessaire de :

* Accédez à l’instance d’AEM, généralement une instance d’auteur, qui contient le matériel clé à copier.

   * Localisez le lot `com.adobe.granite.crypto.file` dans le système de fichiers local

      Par exemple,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Le `bundle.info` identifie le lot
   * Accès au dossier de données

      Par exemple,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Copiez les fichiers hmac et de noeud Principal.



* Pour chaque instance AEM cible

   * Accès au dossier de données

      Par exemple,

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Coller les 2 fichiers précédemment copiés
   * Il est nécessaire de [actualiser le lot Crypto Granite](#refresh-the-granite-crypto-bundle) si l’instance AEM cible est en cours d’exécution


>[!CAUTION]
>
>Si une autre fonctionnalité de sécurité a déjà été configurée basée sur les clés de cryptage, la réplication des clés de cryptage peut endommager la configuration. Pour obtenir de l’aide, [contactez l’assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html).

#### Réplication du référentiel {#repository-replication}

Le fait que le matériel clé soit stocké dans le référentiel, comme c’était le cas pour AEM version 6.2 et antérieure, peut être conservé en spécifiant la propriété système suivante au premier démarrage de chaque instance AEM (qui crée le référentiel initial) :

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Il est important de vérifier que la variable [agent de réplication sur l’auteur](#replication-agents-on-author) est correctement configuré.

Avec le matériel clé stocké dans le référentiel, la manière de répliquer la clé de chiffrement de l’auteur vers d’autres instances est la suivante :

Utilisation [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* accédez à [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* sélectionnez `/etc/key`
* open `Replication` tab
* sélectionnez `Replicate`

* [actualiser le lot Crypto Granite](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Actualisation du lot de chiffrement Granite {#refresh-the-granite-crypto-bundle}

* Sur chaque instance de publication, accédez au [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Par exemple : [https://&lt;server>:&lt;port>/system/console/bundles](http://localhost:4503/system/console/bundles)

* Localiser `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto)
* Sélectionner **[!UICONTROL Actualiser]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Après un moment, une **Succès** La boîte de dialogue doit s’afficher :

   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Si vous utilisez le serveur Apache HTTP, veillez à utiliser le nom de serveur correct pour toutes les entrées pertinentes.

En particulier, veillez à utiliser le nom de serveur correct, et non `localhost`, dans la variable `RedirectMatch`.

#### Exemple httpd.conf {#httpd-conf-sample}

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

* AEM [Dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher.html) documentation
* [Installation de Dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-install.html)
* [Configuration de Dispatcher pour Communities](dispatcher.md)
* [Problèmes connus](troubleshooting.md#dispatcher-refetch-fails)

## Documentation sur les communautés connexes {#related-communities-documentation}

* Visite [Administration des sites des communautés](administer-landing.md) pour en savoir plus sur la création d’un site communautaire, la configuration des modèles de site communautaire, la modération du contenu communautaire, la gestion des membres et la configuration de la messagerie.

* Visite [Développement de communautés](communities.md) pour en savoir plus sur la structure de composants sociaux (SCF) et la personnalisation des composants et fonctionnalités des communautés.

* Visite [Création de composants Communities](author-communities.md) pour savoir comment créer avec et configurer des composants Communities.
