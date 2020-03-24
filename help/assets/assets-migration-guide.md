---
title: Migration des ressources vers Adobe Experience Manager Assets en bloc
description: Comment importer des fichiers dans AEM, appliquer des métadonnées, générer des rendus et les activer pour publier des instances.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 976d037d701eb7cc61a62e14e554675961d6179c

---


# Assets migration guide {#assets-migration-guide}

Lors de la migration des ressources dans AEM, il existe plusieurs étapes à prendre en compte. L’extraction de fichiers et de métadonnées hors de leur page d’accueil actuelle est en dehors du cadre de ce, car elle varie considérablement d’une implémentation à l’autre. Ce décrit plutôt comment importer ces ressources dans AEM, appliquer leurs métadonnées, générer des rendus et activer ou publier les ressources.

## Conditions préalables {#prerequisites}

Before performing any of the steps described below, review and implement the guidance in [Assets performance tuning tips](performance-tuning-guidelines.md). De nombreuses étapes, telles que la configuration du nombre maximal de tâches simultanées, améliorent la stabilité et les performances du serveur sous charge. D’autres étapes, telles que la configuration du magasin de données de fichiers, sont difficiles à exécuter une fois que le système a été chargé avec des ressources.

>[!NOTE]
>
>Les outils de migration de ressources suivants ne font pas partie d’Adobe Experience Manager. Le service à la clientèle d’Adobe ne prend pas en charge ces outils.
>
>* Tools Tag Maker d’ACS AEM
>* Tools CSV Asset Importer d’ACS AEM
>* Bulk Workflow Manager d’ACS Commons
>* Fast Action Manager d’ACS Commons
>* Synthetic Workflow
>
>
Il s’agit d’un logiciel Open Source et couvert par la [licence Apache version 2](https://adobe-consulting-services.github.io/pages/license.html). Pour poser une question ou signaler un problème, consultez les sections respectives [Problèmes GitHub pour les outils ACS AEM](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) et [ACS AEM Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Migrer vers AEM {#migrate-to-aem}

La migration des ressources vers AEM se déroule en plusieurs étapes et doit être considérée comme un processus échelonné. Les phases de la migration sont les suivantes :

1. Désactivation des workflow
1. Chargement des balises
1. Assimilation des ressources
1. Traitement des rendus
1. Activation des ressources.
1. Activation des workflow.

![chlimage_1-223](assets/chlimage_1-223.png)

### Désactivez les workflow {#disable-workflows}

Avant d’ une migration, désactivez les lanceurs pour le `DAM Update Asset` processus. Il est préférable d’assimiler tous les actifs dans le système, puis d’exécuter le  par lots. Si vous êtes déjà en direct pendant la migration, vous pouvez programmer l’exécution de ces   pendant les heures creuses.

### Load tags {#load-tags}

Vous avez peut-être déjà mis en place une taxonomie de balises que vous appliquez à vos images. Des outils tels que l’importateur de ressources CSV et la fonctionnalité de  de métadonnées peuvent aider à automatiser l’application de balises aux ressources. Avant cela, ajoutez les balises dans Experience Manager. The [ACS AEM Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) feature lets you populate tags by using a Microsoft Excel spreadsheet that is loaded into the system.

### Ingest assets {#ingest-assets}

Les performances et la stabilité sont des préoccupations importantes lors de l’intégration des ressources dans le système. Lors du chargement d’un grand nombre de données dans Experience Manager, assurez-vous que le système fonctionne correctement. Cela a réduit le temps nécessaire pour ajouter les données et permet d’éviter la surcharge du système. Cela permet d&#39;éviter les blocages du système, en particulier dans les systèmes déjà en production.

Il existe deux approches pour charger les ressources dans le système : une approche basée sur le push utilisant le protocole HTTP ou une approche basée sur l’extraction utilisant les API JCR.

#### Push via HTTP {#push-through-http}

L’équipe Managed Services d’Adobe utilise un outil appelé Glutton pour charger les données dans les environnements clients. Glutton est une petite application Java qui charge toutes les ressources d’un répertoire dans un autre répertoire d’une instance AEM. À la place de Glutton, vous pouvez également utiliser des outils tels que les scripts Perl pour publier les ressources dans le référentiel.

L’utilisation de l’approche consistant à faire passer le protocole https présente deux principaux inconvénients :

1. Transmettez les ressources via HTTP au serveur. Cette transmission nécessite beaucoup de temps et crée une surcharge, ce qui rallonge le temps nécessaire pour effectuer la migration.
1. Si vous disposez de balises et de métadonnées personnalisées devant être appliquées aux ressources, cette approche nécessite un deuxième processus personnalisé que vous devez exécuter pour appliquer ces métadonnées aux ressources une fois qu’elles ont été importées.

L’autre approche de l’intégration des ressources consiste à extraire les ressources du système de fichiers local. Toutefois, si vous ne parvenez pas à obtenir un lecteur externe ou un partage réseau monté sur le serveur pour effectuer une approche par extraction, la publication des ressources en utilisant HTTP est la meilleure option.

#### Extraire du système de fichiers local {#pull-from-the-local-file-system}

The [ACS AEM Tools CSV Asset Importer](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) pulls assets from the file system and asset metadata from a CSV file for the asset import. L’API AEM Asset Manager est utilisée pour importer les ressources dans le système et appliquer les propriétés des métadonnées configurées. Idéalement, les ressources sont montées sur le serveur via un montage de fichiers réseau ou via un lecteur externe.

Lorsque les ressources ne sont pas transmises sur un réseau, les performances globales s’améliorent considérablement. Cette méthode est généralement la méthode la plus efficace pour charger des actifs dans le référentiel. En outre, vous pouvez importer tous les fichiers et métadonnées en une seule étape, car l’outil prend en charge l’importation de métadonnées. Aucune autre étape n’est nécessaire pour appliquer les métadonnées, par exemple à l’aide d’un outil distinct.

### Process renditions {#process-renditions}

Après avoir chargé les ressources dans le système, vous devez les traiter via le processus Ressources de mise à jour de gestion des actifs numériques, afin d’extraire les métadonnées et de générer les rendus. Avant d’effectuer cette étape, vous devez dupliquer et modifier le processus Ressources de mise à jour de gestion des actifs numériques pour l’adapter à vos besoins. Certaines étapes du flux de travaux par défaut peuvent ne pas être nécessaires pour vous, comme la génération PTIFF Scene7 ou l’intégration du serveur InDesign.

Après avoir configuré le flux de travaux en fonction de vos besoins, vous disposez de deux options pour l’exécuter :

1. The simplest approach is [ACS Commons’ Bulk Workflow Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Cet outil permet d’exécuter une requête et de traiter les résultats de la requête via un workflow. Il existe également des options permettant de définir la taille des lots.
1. Vous pouvez utiliser [ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) de concert avec [Synthetic Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html). Bien que cette approche soit beaucoup plus impliquée, elle vous permet de supprimer la surcharge du moteur de processus AEM, tout en optimisant l’utilisation des ressources du serveur. De plus, Fast Action Manager améliore les performances en surveillant de manière dynamique les ressources du serveur et en réduisant la charge placée sur le système. Des exemples de scripts ont été fournis sur la page de fonctionnalités d’ACS Commons.

### Activez les ressources {#activate-assets}

Pour les déploiements disposant d’un niveau de publication, vous devez activer les ressources dans la ferme de serveurs de publication. Bien qu’Adobe recommande d’exécuter plusieurs instances de publication, il est plus efficace de répliquer toutes les ressources sur une seule instance de publication, puis de cloner cette instance. Lorsque vous activez un grand nombre de ressources, après le déclenchement d’une activation d’arborescence, vous devrez peut-être intervenir. Voici pourquoi : Lors de la  , les éléments sont ajoutés aux tâches/Sling. Une fois que la taille de cette file d’attente commence à dépasser environ 40 000 éléments, le traitement ralentit considérablement. Lorsque la taille de cette file d’attente dépasse 100 000 éléments, la stabilité du système commence à souffrir.

Pour contourner ce problème, vous pouvez utiliser l’outil [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) pour gérer la réplication des ressources. Il fonctionne sans utiliser les files d’attente Sling, réduisant les surcharges, tout en régulant la charge de travail pour éviter que le serveur ne soit surchargé. Un exemple d’utilisation de cet outil pour gérer la réplication est présenté sur la page de documentation de FAM.

D’autres options permettant d’envoyer des ressources vers le domaine de publication comprennent l’utilisation de [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) ou de [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), qui sont fournis en tant qu’outils dans le cadre de Jackrabbit. Une autre option consiste à utiliser un outil Open Source pour votre infrastructure AEM appelé [Grabbit](https://github.com/TWCable/grabbit), qui prétend présenter des performances plus rapides que vlt.

Pour toutes ces approches, notez que les ressources de l’instance d’auteur ne s’affichent pas comme ayant été activées. Pour marquer ces ressources avec l’état d’activation correct, vous devez également exécuter un script les marquant comme activées.

>[!NOTE]
>
>Adobe ne prend pas en charge Grabbit.

### Clone Publish {#clone-publish}

Une fois les ressources activées, vous pouvez cloner votre instance de publication afin de créer autant de copies que nécessaire pour le déploiement. Le clonage d’un serveur est relativement simple, mais il existe quelques étapes importantes à retenir. Pour cloner la publication :

1. Sauvegardez l’instance source et la banque de données.
1. Restaurez la sauvegarde de l’instance et de la banque de données à l’emplacement cible. Les étapes suivantes se rapportent toutes à cette nouvelle instance.
1. Effectuez une recherche dans le système de fichiers sous `crx-quickstart/launchpad/felix` for `sling.id`. Supprimez ce fichier.
1. Sous le chemin d’accès racine de la banque de données, recherchez et supprimez les fichiers `repository-XXX`.
1. Modifiez `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` et `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config` pointez sur l’emplacement de la banque de données sur le nouveau  de .
1. Démarrez l’environnement.
1. Mettez à jour la configuration de tous les agents de réplication sur le ou les auteurs afin de pointer vers les instances de publication ou les agents de vidage du Dispatcher corrects sur la nouvelle instance. Cela permet de pointer vers les Dispatchers appropriés du nouvel environnement.

### Activation des workflow {#enable-workflows}

Une fois la migration terminée, les lanceurs des workflow Ressources de mise à jour de gestion des actifs numériques doivent être réactivés pour prendre en charge la génération des rendus et l’extraction des métadonnées pour une utilisation quotidienne continue du système.

## Migration des ressources dans les déploiements AEM {#migrate-between-aem-instances}

Bien que ce ne soit pas aussi courant, vous devez parfois migrer de grandes quantités de données d’une instance AEM à une autre, par exemple, lorsque vous effectuez une mise à niveau d’AEM, que vous mettez à niveau votre matériel ou que vous migrez vers un nouveau centre de données, comme avec une migration AMS.

Dans ce cas, les ressources sont déjà renseignées avec les métadonnées et les rendus déjà générés. Il ne vous reste plus qu’à vous concentrer sur le déplacement des ressources d’une instance à une autre. Lors de la migration entre instances AEM, procédez comme suit :

1. Désactiver les  de : Puisque vous migrez des rendus avec nos ressources, vous souhaitez désactiver les lanceurs de processus pour la ressource de mise à jour DAM.

1. Migrer les balises : Les balises étant déjà chargées dans l’instance AEM source, vous pouvez les créer dans un package de contenu et installer le package sur l’instance  du.

1. Migrer des ressources : Il existe deux outils recommandés pour déplacer des ressources d’une instance AEM vers une autre :

   * **Vault Remote Copy**, ou `vlt rcp`, vous permet d&#39;utiliser vlt sur un réseau. Vous pouvez indiquer des répertoires source et de destination pour que vlt télécharge toutes les données du référentiel d’une instance et les charge dans l’autre. Vlt rcp is documented at [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbit** est un outil de synchronisation de contenu Open Source développé par Time Warner Cable dans le cadre de la mise en œuvre d’AEM. Comme il utilise des flux de données continus, en comparaison avec vlt rcp, sa latence est inférieure et il annonce une vitesse de deux à dix fois plus rapide que vlt rcp. Grabbit prend également en charge la synchronisation du contenu delta uniquement, ce qui lui permet de synchroniser les modifications après l’achèvement d’une passe de migration initiale.

1. Activate assets: Follow the instructions for [activating assets](#activate-assets) documented for the initial migration to AEM.

1. Cloner la publication : Comme pour une nouvelle migration, le chargement d’une instance de publication unique et son clonage sont plus efficaces que l’activation du contenu sur les deux noeuds. Voir [Clonage de la publication](#clone-publish).

1. Activation des  de : Une fois la migration terminée, réactivez les lanceurs pour le de ressources de mise à jour DAM afin de prendre en charge la génération de rendus et le de métadonnées  pour une utilisation courante du système.
