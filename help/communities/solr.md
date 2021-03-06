---
title: Configuration Solr pour SRP
seo-title: Solr Configuration for SRP
description: Une installation Apache Solr peut être partagée entre le magasin de noeuds (Oak) et le magasin commun (SRP) en utilisant différentes collections.
seo-description: An Apache Solr installation may be shared between the node store (Oak) and common store (SRP) by using different collections
uuid: 7356343d-073c-4266-bdcb-c7e999281476
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e228f1db-91ea-4ec3-86da-06d89d74bc72
role: Admin
exl-id: b506018d-67dc-4e47-a3d8-83ae288b5d7e
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1581'
ht-degree: 3%

---

# Configuration Solr pour SRP {#solr-configuration-for-srp}

## Solr pour AEM Platform {#solr-for-aem-platform}

Un [Apache Solr](https://lucene.apache.org/solr/) l’installation peut être partagée entre les [magasin de noeuds](../../help/sites-deploying/data-store-config.md) (Oak) et [magasin commun](working-with-srp.md) (SRP) en utilisant différentes collections.

If both the Oak and SRP collections are used intensively, a second Solr may be installed for performance reasons.

Pour les environnements de production, [Mode SolrCloud](#solrcloud-mode) offre de meilleures performances par rapport au mode autonome (une seule configuration Solr locale).

### Conditions requises {#requirements}

Téléchargez et installez Apache Solr :

* [Version 4.10](https://archive.apache.org/dist/lucene/solr/4.10.4/) ou [version 5](https://archive.apache.org/dist/lucene/solr/5.5.3/)

* Solr nécessite Java 1.7 ou version ultérieure
* Aucun service requis
* Choix des modes d’exécution :

   * Mode autonome
   * [Mode SolrCloud](#solrcloud-mode) (recommandé pour les environnements de production)

* Choix de la recherche multilingue (MLS)

   * [Installation de MLS standard](#installing-standard-mls)
   * [Installation de MLS avancés](#installing-advanced-mls)

## Mode SolrCloud {#solrcloud-mode}

[SolrCloud](https://cwiki.apache.org/confluence/display/solr/SolrCloud) est recommandé pour les environnements de production. Lors de l’exécution en mode SolrCloud, SolrCloud doit être installé et configuré avant d’installer la recherche multilingue (MLS).

Il est recommandé de suivre les instructions d’installation de SolrCloud :

* 3 noeuds SolrCloud sur le même serveur
* Un ZooKeeper externe Apache

Il est également recommandé de configurer JVM pour optimiser l’utilisation de la mémoire et le nettoyage de la mémoire.

### Exemple de configuration JVM {#jvm-configuration-example}

```shell
JVM_OPTS="-server -Xmx2048m -XX:MaxPermSize=768M -XX:+UseConcMarkSweepGC -XX:+CMSClassUnloadingEnabled -Xloggc:../logs/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps -Djava.awt.headless=true"  
```

### Commandes de configuration de SolrCloud {#solrcloud-setup-commands}

Lors de l’exécution en mode SolrCloud, avant l’installation de MLS, utilisez et connaissez les commandes de configuration SolrCloud suivantes.

#### 1. Télécharger une configuration sur ZooKeeper {#upload-a-configuration-to-zookeeper}

Référence:\
[https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities](https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities)

Utilisation:\
sh ./scripts/cloud-scripts/zkcli.sh \\
-cmd upconfig \\
-zkhost *server:port* \\
-confname *myconfig-name *\\
-solrhome *solr-home-path* \\
-confdir *config-dir*

#### 2. Créer une collection {#create-a-collection}

Référence:\
[https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-Create](https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-Create)

Utilisation:\
./bin/solr create \\
-c *mycollection-name*\\
-d *config-dir* \\
-n *myconfig-name* \\
-p *port*\\
-s *nombre de éclats* \\
-rf *nombre de réplication*

#### 3. Lier une collection à un jeu de configuration {#link-a-collection-to-a-configuration-set}

Liez une collection à une configuration déjà téléchargée sur ZooKeeper.

Référence:\
[https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities](https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities)

Utilisation:\
sh ./scripts/cloud-scripts/zkcli.sh \\
-cmd linkconfig \\
-zkhost *server:port* \\
-collection *mycollection-name* \\
-confname *myconfig-name*

### Comparaison des MLS standard et avancés {#comparison-of-standard-and-advanced-mls}

La recherche multilingue (MLS) pour AEM Communities est conçue pour la plateforme Solr afin de fournir une recherche améliorée dans toutes les langues prises en charge, y compris l’anglais.

MLS pour les communautés d’AEM est disponible en tant que MLS standard ou MLS avancé. Le MLS standard inclut uniquement les paramètres de configuration Solr et exclut tous les modules externes ou fichiers de ressources. Le MLS avancé est une solution plus complète qui inclut des paramètres de configuration Solr, ainsi que des modules externes et des ressources connexes.

Le MLS standard comprend des améliorations pour la recherche de contenu dans les langues suivantes :

* English: improved stemmer for attempting to match word derivations
* Japonais : amélioration de la segmentation en jetons japonais pour les caractères demi-largeur

Le MLS avancé comprend des améliorations pour la recherche de contenu dans les langues suivantes :

* Anglais : briquet remplacé par un lemmatizer
* Allemand : added décomposator
* French: added elision handling
* Chinois (simplifié) : ajout d’un jeton plus intelligent
* Diverses langues : ajout d’un moteur de recherche, d’une liste de mots vides et d’un normaliseur.

In all, the following 33 languages are supported in Advanced MLS.

| Arabe | Allemand | Norvégien |
|---|---|---|
| Bulgare | Grec | Polonais |
| Chinois (simplifié) | Créole haïtien | brésilien |
| Chinois (traditionnel) | Hébreu | Roumain |
| Tchèque | Hongrois | Russe |
| Danois | Indonésien | Slovaque |
| Néerlandais | Italien | Slovène |
| Anglais | Japonais | Espagnol |
| Estonien | Coréen | Suédois |
| Finnois | Letton | Thaï |
| Français | Lituanien | Turc |

#### Comparaison d’AEM 6.1 Solr search, Standard MLS et Advanced MLS {#comparison-of-aem-solr-search-standard-mls-and-advanced-mls}

**Remarque**: AEM 6.1 fait référence à AEM 6.1 Communities FP3 et versions antérieures.

![chlimage_1-283](assets/chlimage_1-283.png)

### Installation de MLS standard {#installing-standard-mls}

Pour la collection SRP (MSRP ou DSRP), pour prendre en charge la recherche multilingue standard (MLS), il est nécessaire de modifier deux des fichiers de configuration de Solr :

* **schema.xml**
* **solrconfig.xml**

Fichiers MLS standard (schema.xml, solrconfig.xml) pour Solr 4.10

Fichiers MLS standard (schema.xml, solrconfig.xml) pour Solr 5

Les fichiers MLS standard sont stockés dans le référentiel AEM.

**Remarque**: Bien que les fichiers Solr soient stockés dans le dossier msrp/ , ils sont également pour DSRP (aucune modification n’est nécessaire).

**Instructions de téléchargement**: replace `solrX` avec `solr4` ou `solr5` selon le cas

1. À l’aide de CRXDE|Lite, localisez

   * /libs/social/config/datastore/msrp/*solrX*/**schema.xml**
   * /libs/social/config/datastore/msrp/*solrX*/**solrconfig.xml**

1. Téléchargement vers le serveur local sur lequel Solr est déployé

   * Recherchez la variable `jcr:content` du noeud `jcr:data` property
   * Sélectionner `view` pour lancer le téléchargement
   * Assurez-vous que les fichiers sont enregistrés avec les noms et le codage appropriés (UTF8).

1. Follow the installation instructions for either standalone or SolrCloud mode

#### SolrCloud Mode - Standard MLS {#solrcloud-mode-standard-mls}

1. Installation et configuration de Solr en mode SolrCloud
1. Préparez une nouvelle configuration :

   1. Créer *new-config-dir* par exemple *solr-install-dir*/myconfig/

   1. Copiez le contenu du répertoire de configuration Solr existant dans *new-config-dir*

      * For Solr4: copy *solr-install-dir*/example/solr/collection1/conf/&amp;ast;
      * For Solr5: copy *solr-install-dir*/server/solr/configsets/data_driven_schema_configs/&amp;ast;
   1. Copiez le téléchargé **schema.xml** et **solrconfig.xml** to *new-config-dir* pour remplacer des fichiers existants


1. [Chargement de la nouvelle configuration](#upload-a-configuration-to-zookeeper) to ZooKeeper
1. [Création d’une collection](#create-a-collection) la spécification des paramètres nécessaires, tels que le nombre de shards, le nombre de répliques et le nom de configuration.
1. Si le nom de la configuration n’a pas été *fourni lors de la création de la collection, [lier cette collection nouvellement créée](#link-a-collection-to-a-configuration-set) avec la configuration téléchargée sur ZooKeeper

1. Pour MSRP, exécutez [Outil de réindexation MSRP](msrp.md#msrp-reindex-tool), sauf s’il s’agit d’une nouvelle installation

#### Mode autonome - MLS standard {#standalone-mode-standard-mls}

1. Installation de Solr en mode autonome
1. Si vous exécutez Solr5, créez une collection1 (semblable à Solr4) :

   * ./bin/solr start
   * ./bin/solr create_core -c collection1 -d sample_techproducts_configs

1. Sauvegarde **schema.xml** et **solrconfig.xml** dans le répertoire de configuration Solr, par exemple :

   * Pour Solr4 : *solr-install-dir*/exemple/solr/collection1/conf/
   * Créé pour Solr5 : *solr-install-dir*/server/solr/collection1/conf/

1. Copiez le téléchargé **schema.xml** et **solrconfig.xml** vers le même répertoire

1. Redémarrer Solr
1. Pour MSRP, exécutez [Outil de réindexation MSRP](#msrpreindextool), sauf s’il s’agit d’une nouvelle installation

### Installation de MLS avancés {#installing-advanced-mls}

Pour que la collection SRP (MSRP ou DSRP) prenne en charge les MLS avancés, de nouveaux modules externes Solr sont requis en plus d’un schéma personnalisé et d’une configuration Solr. Tous les éléments requis sont compressés dans un fichier ZIP téléchargeable. In addition, an install script is included for use when Solr is deployed in standalone mode.

Pour obtenir le package MLS avancé, voir [AEM MLS avancés](deploy-communities.md#aem-advanced-mls) dans la section deploy de la documentation.

Pour commencer à installer SolrCloud ou le mode autonome, procédez comme suit :

* Téléchargez l’archive zip AEM-SOLR-MLS sur le serveur hébergeant Solr.
* Unpack the archive

#### Mode SolrCloud - MLS avancé {#solrcloud-mode-advanced-mls}

Installation instructions - note the few differences for Solr4 and Solr5:

1. Installation et configuration de Solr en mode SolrCloud
1. Extract the contents of the Advanced MLS package to disk. The contents should include:

   * **schema.xml**
   * **solrconfig.xml**
   * **stopwords/** folder
   * **profiles/** folder
   * **extra-libs/** folder

1. Préparez une nouvelle configuration :

   1. Créez un *new-config-dir*

      * Par exemple : *solr-install-dir*/myconfig/
      * Créez des sous-dossiers stopwords/ et lang/
   1. Copiez le contenu du répertoire de configuration Solr existant dans *new-config-dir*

      * Pour Solr4 : Copier *solr-install-dir*/example/solr/collection1/conf/&amp;ast;
      * Pour Solr5 : Copier *solr-install-dir*/server/solr/configsets/data_led_schema_configs/&amp;ast;
   1. Copiez le fichier extrait **schema.xml** et **solrconfig.xml** to *new-config-dir* pour remplacer des fichiers existants
   1. Pour Solr5 : Copier *solr_install_dir*/server/solr/configsets/sample_techproducts_configs/conf/lang/&amp;ast;.txt&quot; en *new-config-dir*/lang/
   1. Copiez le fichier extrait **stopwords/** dossier vers *new-config-dir* résultant *new-config-dir*/stopwords/&amp;ast;.txt



1. [Chargement de la nouvelle configuration](#upload-a-configuration-to-zookeeper) to ZooKeeper
1. Copiez le nouveau **profiles/** dossier ...

   * Pour Solr4 : Copier dans les ressources/dossiers de chaque noeud
   * Pour Solr5 : Copiez dans chaque dossier/serveur/ressources/dossier d’installation Solr. Si tous les noeuds se trouvent dans le même répertoire d’installation Solr, cette étape n’est effectuée qu’une seule fois.

1. Créez un **lib/** dans le répertoire solr-home (contient solr.xml) de chaque noeud de SolrCloud. Copiez les jars des emplacements suivants dans le nouveau dossier lib/ de chaque noeud :

   * **extra-libs/** extrait du package MLS avancé
   * *solr-install-dir/contrib/extraction/lib/*.jar
   * *solr-install-dir/dist/solr-cell*.jar
   * *solr-install-dir/contrib/clustering/lib/*.jar
   * *solr-install-dir/dist/solr-clustering*.jar
   * *solr-install-dir/contrib/langid/lib/*.jar
   * *solr-install-dir/dist/solr-langid*.jar
   * *solr-install-dir/contrib/velocity/lib/*.jar
   * *solr-install-dir/dist/solr-velocity*.jar
   * *solr-install-dir/contrib/analysis-extras/lib/*.jar
   * *solr-install-dir/contrib/analysis-extras/lucene-libs/*.jar

1. [Création d’une collection](#create-a-collection) la spécification des paramètres nécessaires, tels que le nombre de shards, le nombre de répliques et le nom de configuration.
1. Si le nom de la configuration était *not* fourni lors de la création de la collection, [lier cette collection nouvellement créée](#link-a-collection-to-a-configuration-set) avec la configuration téléchargée sur ZooKeeper

1. Pour MSRP, exécutez [Outil de réindexation MSRP](#msrpreindextool), sauf s’il s’agit d’une nouvelle installation

#### Mode autonome - MLS avancé {#standalone-mode-advanced-mls}

Un script d’installation est inclus dans le package MLS avancé.

Une fois que le contenu du package a été extrait sur le serveur hébergeant le serveur Solr autonome, exécutez simplement le script d&#39;installation afin d&#39;installer les ressources et les fichiers de configuration nécessaires.

* Installation de Solr en mode autonome
* Si vous exécutez Solr5, créez une collection1 (semblable à Solr4) :

   * ./bin/solr start
   * ./bin/solr create_core -c collection1 -d sample_techproducts_configs

* Exécutez le script d’installation : Installer [-v 4|5] [-d solrhome] [-c collectionpath]
où :

   * -d solrhome

      Répertoire d’installation Solr

   * -c collectionpath

      Chemin d’accès de la collection dans solitaire

   * --help

      Options de ligne de commande Imprimer

   * -v [4|5]

      Définition de la version pour solder

* Exemple pour Solr 4.10.4 :

   * Install.bat -v 4 -d c:/solr-4.10.4 -c:/solr-4.10.4/example/solr/collection1

* Exemple pour Solr 5.4.0 :

   * Install.sh -v 5 -d /tmp/solr-5.4.0 -c /tmp/solr-5.4.0/server/solr/collection1

**Remarque** :

* The install script will back-up schema.xml and solrconfig.xml before installing new versions by appending &quot;.orig&quot;

### About solrconfig.xml {#about-solrconfig-xml}

Le **solrconfig.xml** contrôle l’intervalle de validation automatique et la visibilité de la recherche. Il nécessite des tests et des réglages.

&lt;autoCommit>: By default, the AutoCommit interval, which is a hard commit to stable storage, is set to 15 seconds. La visibilité de la recherche utilise par défaut l’index de pré-validation.

Pour modifier la recherche afin d’utiliser un index mis à jour pour refléter les modifications dues à la validation, modifiez le contenu &lt;opensearcher> sur true.

&lt;autosoftcommit>: Une validation &quot;soft&quot; garantit que les modifications sont visibles (l’index est mis à jour), mais ne garantit pas que les modifications sont synchronisées avec un stockage stable (hard commit). Les performances s’en trouvent améliorées. Par défaut, &lt;autosoftcommit> est désactivé avec le contenu &lt;maxtime> définissez sur -1.
