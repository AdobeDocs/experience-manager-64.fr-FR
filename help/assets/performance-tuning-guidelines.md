---
title: Guide d’optimisation des performances des ressources
description: Principaux domaines d’intérêt [!DNL Experience Manager] configuration, modifications apportées aux composants matériels, logiciels et réseau pour supprimer les goulets d’étranglement et optimiser les performances de [!DNL Experience Manager] Ressources.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: 6c1bff46-f9e0-4638-9374-a9e820d30534
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3203'
ht-degree: 50%

---

# Guide d’optimisation des performances des ressources {#assets-performance-tuning-guide}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Une configuration d’Adobe Experience Manager Assets contient un certain nombre de composants matériels, logiciels et réseau. Selon votre scénario de déploiement, vous pouvez avoir besoin d’apporter des modifications spécifiques à la configuration des composants matériels, logiciels et réseau pour supprimer les goulots d’étranglement en termes de performances.

En outre, l’identification et le respect de certaines instructions relatives à l’optimisation du matériel et des logiciels vous aident à créer une base solide qui permet à vos [!DNL Experience Manager] Déploiement de ressources pour répondre aux attentes en matière de performances, d’évolutivité et de fiabilité.

Mauvaise performance dans [!DNL Experience Manager] Les ressources peuvent avoir un impact sur l’expérience utilisateur en ce qui concerne les performances interactives, le traitement des ressources, la vitesse de téléchargement et d’autres aspects.

En fait, l’optimisation des performances est une tâche essentielle que vous effectuez avant d’établir des mesures cibles pour chacun de vos projets.

Voici quelques éléments principaux essentiels pour lesquels vous devez identifier et corriger les problèmes de performances avant que ceux-ci aient un impact sur les utilisateurs.

## Plateforme {#platform}

while [!DNL Experience Manager] est pris en charge sur un certain nombre de plateformes. Adobe a trouvé la meilleure prise en charge des outils natifs sous Linux et Windows, ce qui contribue à des performances optimales et à une facilité d’implémentation. Idéalement, vous devez déployer un système d’exploitation 64 bits pour répondre aux exigences de mémoire élevée d’un [!DNL Experience Manager] Déploiement des ressources. Comme avec tout [!DNL Experience Manager] déploiement, vous devez implémenter TarMK chaque fois que possible. Bien que TarMK ne puisse pas mesurer au-delà d’une instance d’auteur simple, il semble offrir de meilleurs résultats que MongoMK. Vous pouvez ajouter des instances de déchargement TarMK pour augmenter la puissance de traitement du workflow de votre [!DNL Experience Manager] Déploiement des ressources.

### Dossier temp  {#temp-folder}

Afin de réduire les délais de chargement des ressources, utilisez un stockage haute performance pour le répertoire temporaire Java. Sous Linux et Windows, un disque SSD ou RAM peut être utilisé. Dans des environnements cloud, un type de stockage à grande vitesse équivalent peut être utilisé. Par exemple, dans Amazon EC2, une [disque éphémère](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) Le lecteur peut être utilisé pour le dossier temporaire.

En supposant que le serveur dispose de suffisamment de mémoire, configurez un disque RAM. Sous Linux, exécutez les commandes suivantes pour créer un disque RAM de 8 Go :

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Sous Windows OS, vous devez utiliser un pilote tiers pour créer un disque RAM ou utiliser simplement un stockage haute performance tel que SSD.

Une fois que le volume temporaire haute performance est prêt, définissez le paramètre JVM -Djava.io.tmpdir. Par exemple, vous pouvez ajouter le paramètre JVM ci-dessous à la variable CQ_JVM_OPTS dans le script bin/start d’AEM :

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Configuration Java {#java-configuration}

### Version Java {#java-version}

Comme Oracle a cessé de publier les mises à jour de Java 7 depuis avril 2015, Adobe recommande de déployer [!DNL Experience Manager] Ressources sur Java 8. Dans certains cas, une amélioration des performances a été constatée.

### Paramètres JVM    {#jvm-parameters}

Vous devez définir les paramètres JVM suivants :

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Configuration du magasin de données et de la mémoire {#data-store-and-memory-configuration}

### Configuration du magasin de données basé sur les fichiers {#file-data-store-configuration}

Il est recommandé de séparer l’entrepôt de données de l’entrepôt de segments pour tous les [!DNL Experience Manager] Utilisateurs des ressources. En outre, la configuration des paramètres `maxCachedBinarySize` et `cacheSizeInMB` peut vous aider à optimiser les performances. Définissez le paramètre `maxCachedBinarySize` selon la plus petite taille de fichier pouvant être contenue dans le cache. Spécifiez la taille du cache en mémoire à utiliser pour l’entrepôt de données dans `cacheSizeInMB`. Adobe vous recommande de définir cette valeur entre 2 et 10 % de la taille totale du tas. Toutefois, les tests de charge/performance peuvent vous aider à déterminer le paramètre idéal.

### Configuration de la taille maximale du cache d’images mis en mémoire tampon    {#configure-the-maximum-size-of-the-buffered-image-cache}

Lors du chargement d’un grand nombre de ressources vers Adobe Experience Manager, réduisez la taille maximale configurée du cache d’images mis en mémoire tampon. De cette façon, vous tiendrez compte des pics inattendus de consommation de la mémoire et éviterez l’échec de JVM avec des erreurs de mémoire insuffisante. Prenez l’exemple d’un système présentant un tas maximal (paramètre -`Xmx`) de 5 Go, un BlobCache Oak défini sur 1 Go et un cache de documents défini sur 2 Go. Dans ce cas, le cache mis en mémoire tampon prendrait 1,25 Go au maximum et la mémoire, ce qui laisserait seulement 0,75 Go de mémoire pour les pics inattendus.

Configurez la taille du cache mis en mémoire tampon dans la console web OSGi. À l’emplacement `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`, définissez la propriété `cq.dam.image.cache.max.memory` en octets. Par exemple, 1073741824 représente 1 Go (1 024 x 1 024 x 1 024 = 1 Go).

De [!DNL Experience Manager] 6.1 SP1, si vous utilisez une `sling:osgiConfig` pour configurer cette propriété, veillez à définir le type de données sur Long. Pour plus d’informations, voir [CQBufferedImageCache utilise le tas lors des chargements de ressources](https://helpx.adobe.com/fr/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Entrepôts de données partagés    {#shared-data-stores}

La mise en œuvre d’un magasin de données basé sur les fichiers, partagé ou S3, peut vous aider à économiser de l’espace disque et à augmenter le débit réseau dans des implémentations à grande échelle. Pour plus d’informations sur les avantages et inconvénients de l’utilisation d’une banque de données partagée, voir [Guide de dimensionnement des ressources](assets-sizing-guide.md).

### Magasin de données S3 {#s-data-store}

La configuration du magasin de données S3 suivante (`org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) a permis à Adobe d’extraire 12,8 To d’objets BLOB (Binary Large Objects) d’un magasin de données basé sur les fichiers existant dans un magasin de données S3 vers un site client :

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Optimisation du réseau {#network-optimization}

Adobe recommande d’activer HTTPS, car de nombreuses entreprises qui possèdent des pare-feu analysent le trafic HTTP, ce qui a une incidence sur les chargements et endommage les fichiers. Pour les chargements de fichiers volumineux, assurez-vous que les utilisateurs disposent d’une connexion filaire au réseau, car les réseaux Wi-Fi saturent rapidement. Pour obtenir des instructions sur l’identification des goulets d’étranglement réseau, voir [Guide de dimensionnement des ressources](assets-sizing-guide.md). Pour évaluer les performances du réseau en analysant sa topologie, consultez les [Remarques sur le réseau des ressources](assets-network-considerations.md).

Votre stratégie d’optimisation du réseau dépend essentiellement de la quantité de bande passante disponible et du chargement sur votre instance [!DNL Experience Manager]. Les options de configuration courantes, notamment les pare-feu ou les proxys, peuvent améliorer les performances du réseau. Voici quelques points essentiels à garder à l’esprit :

* En fonction du type d’instance (petite, moyenne, grande), assurez-vous que vous disposez de suffisamment de bande passante réseau pour votre [!DNL Experience Manager] instance. L’allocation d’une bande passante appropriée est particulièrement importante si [!DNL Experience Manager] est hébergé sur AWS.
* Si votre instance [!DNL Experience Manager] est hébergée sur AWS, vous pouvez tirer profit d’une stratégie de mise à l’échelle polyvalente. Augmentez la taille de l’instance si les utilisateurs prévoient une charge élevée. Décompressez-le pour une charge moyenne/faible.
* HTTPS : La plupart des utilisateurs disposent de pare-feu qui détectent le trafic HTTP, ce qui peut avoir un impact négatif sur le chargement des fichiers ou même endommager les fichiers lors de l’opération de chargement.
* Chargements de fichiers volumineux : Assurez-vous que les utilisateurs disposent de connexions câblées au réseau (les connexions Wi-Fi se saturent rapidement).

## Workflows    {#workflows}

### Workflows transitoires {#transient-workflows}

Dans la mesure du possible, définissez le workflow Ressource de mise à jour de gestion des ressources numériques sur l’option Transitoire. Le paramètre réduit considérablement les surcharges nécessaires pour traiter les workflows car, dans ce cas, ils n’ont pas besoin de faire l’objet d’un suivi et de processus d’archivage classiques.

>[!NOTE]
>
>Par défaut, le workflow Ressources de mise à jour de gestion des actifs numériques est défini sur Transitoire dans [!DNL Experience Manager] 6.3. Dans ce cas, vous pouvez ignorer la procédure suivante.

1. Ouvrir `http://localhost:4502/miscadmin` sur le [!DNL Experience Manager] instance que vous souhaitez configurer.

1. Dans l’arborescence de navigation, développez **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]** > **[!UICONTROL dam]**.
1. Double-cliquez sur **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]** (DAM).
1. Depuis le panneau d’outils flottant, basculez vers l’onglet **[!UICONTROL Page]**, puis cliquez sur **[!UICONTROL Propriétés de la page]**.
1. Sélectionner **[!UICONTROL Processus transitoire]** Cliquez sur **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Certaines fonctions ne prennent pas en charge les workflows transitoires. Si votre [!DNL Experience Manager] Le déploiement des ressources requiert ces fonctionnalités, mais ne configurez pas de workflows transitoires.

   Dans les cas où les workflows transitoires ne peuvent pas être utilisés, exécutez la purge des workflows régulièrement pour supprimer les workflows Ressource de mise à jour de gestion des ressources numériques afin de garantir que les performances système ne se dégraderont pas.

   En règle générale, vous devez exécuter la purge des workflows sur une base hebdomadaire. Cependant, dans les scénarios gourmands en ressources, tels que l’ingestion de ressources à grande échelle, vous pouvez l’exécuter plus fréquemment.

   Pour configurer la purge des workflows, ajoutez une nouvelle configuration de purge de workflow d’Adobe Granite via la console OSGi. Ensuite, configurez et planifiez le workflow dans le cadre de la fenêtre de maintenance hebdomadaire.

   Si la purge s’exécute trop longtemps, elle s’arrête. Par conséquent, vous devez vous assurer que vos tâches de purge sont terminées afin d’éviter les situations où la purge des workflows ne se termine pas en raison du nombre élevé de workflows.

   Par exemple, après l’exécution d’un grand nombre de workflows transitoires (ce qui crée des nœuds d’instance de workflow), vous pouvez exécuter l’[outil de suppression de workflow ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) sur une base ponctuelle. Il supprime immédiatement les instances de workflow redondantes et terminées au lieu d’attendre que le planificateur de purge de workflow Granite Adobe s’exécute.

### Tâches parallèles maximales    {#maximum-parallel-jobs}

Par défaut, [!DNL Experience Manager] exécute un nombre maximal de tâches parallèles qui est égal au nombre de processeurs sur le serveur. Le problème avec ce paramètre est que pendant les périodes de charge importante, tous les processeurs sont occupés par des workflows Ressource de mise à jour de gestion des ressources numériques, ce qui ralentit la réactivité de l’interface utilisateur et empêche [!DNL Experience Manager] d’exécuter d’autres processus qui assurent la stabilité et les performances du serveur. En tant que bonne pratique, définissez cette valeur sur la moitié des processeurs disponibles sur le serveur en procédant comme suit :

1. Activé [!DNL Experience Manager] Création, accédez à [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent).
1. Cliquez sur Modifier sur chaque file d’attente de workflow appropriée à votre implémentation (par exemple, la file d’attente de workflow transitoire de Granite).
1. Modifiez la valeur de Maximum Parallel Jobs (Nombre maximal de tâches en parallèle), puis cliquez sur Enregistrer.

Configurer une file d’attente à la moitié des processeurs disponibles est une solution exploitable pour commencer. Cependant, vous pouvez être amené à augmenter ou à réduire ce nombre pour atteindre un débit maximal et l’ajuster selon l’environnement. Il existe des files d’attente distinctes pour les workflows transitoires et non transitoires, ainsi que d’autres processus, tels que les workflows externes. Si plusieurs files d’attente configurées à 50 % des processeurs sont activées simultanément, le système peut devenir rapidement surchargé. Les files d’attente utilisées varient considérablement selon les différentes implémentations de l’utilisateur. Par conséquent, vous devrez peut-être les configurer de manière réfléchie pour une efficacité maximale sans sacrifier la stabilité du serveur.

### Déchargement {#offloading}

Pour les workflows de volume élevé ou les workflows gourmands en ressources, tels que le transcodage vidéo, vous pouvez décharger les workflows Ressources de mise à jour de gestion des actifs numériques vers une deuxième instance d’auteur. Souvent, le problème avec le déchargement est que toute charge enregistrée lors du déchargement du traitement du workflow est compensée par le coût de réplication du contenu entre les instances.

À partir de [!DNL Experience Manager] 6.2 et avec un Feature Pack pour [!DNL Experience Manager] 6.1, vous pouvez effectuer le déchargement avec une réplication sans fichier binaire. Dans ce modèle, les instances d’auteur partagent une banque de données commune et envoient uniquement les métadonnées par le biais de la réplication différée. Bien que cette approche fonctionne bien avec un entrepôt de données de fichiers partagé, il peut y avoir des problèmes avec un entrepôt de données S3. Les threads d’écriture en arrière-plan pouvant provoquer une latence, il est possible qu’une ressource n’ait pas été écrite dans la banque de données avant le démarrage de la tâche de déchargement.

### Configuration des ressources de mise à jour de gestion des ressources numériques {#dam-update-asset-configuration}

Le workflow Ressource de mise à jour de gestion des actifs numériques contient une suite complète d’étapes configurées pour les tâches, telles que la génération PTIFF Dynamic Media Classic et l’intégration des InDesigns Server. Cependant, plusieurs de ces étapes peuvent être inutiles à la plupart des utilisateurs. Adobe vous recommande de créer une copie personnalisée du modèle de workflow Ressource de mise à jour de gestion des ressources numériques, et de supprimer toutes les étapes inutiles. Dans ce cas, mettez à jour les lanceurs pour que les ressources de mise à jour de gestion des ressources numériques pointent vers le nouveau modèle.

>[!NOTE]
>
>L’exécution intensive du workflow Ressources de mise à jour de gestion des ressources numériques peut augmenter de manière importante la taille de votre magasin de données basé sur les fichiers. Les résultats d’une expérience effectuée par Adobe ont montré que la taille de l’entrepôt de données peut augmenter d’environ 400 Go si environ 5 500 workflows sont effectués dans les 8 heures.
>
>Il s’agit d’une augmentation temporaire, et la banque de données est restaurée à sa taille d’origine après l’exécution de la tâche de nettoyage de la mémoire d’entrepôt de données.
>
>En règle générale, la tâche de nettoyage de la mémoire d’entrepôt de données s’exécute chaque semaine avec d’autres tâches de maintenance planifiées.
>
>Si vous disposez d’un espace disque limité et exécutez de façon intensive le workflow Ressources de mise à jour de gestion des actifs numériques, pensez à planifier la tâche de nettoyage plus fréquemment.

#### Génération de rendus au moment de l’exécution {#runtime-rendition-generation}

Les clients utilisent des images de tailles et de formats différents sur leur site web ou pour les distribuer à leurs partenaires professionnels. Étant donné que chaque rendu s’ajoute à l’encombrement d’une ressource dans le référentiel, Adobe recommande d’utiliser cette fonction judicieusement. Pour réduire la quantité de ressources nécessaires au traitement et au stockage des images, vous pouvez générer ces images au moment de l’exécution plutôt que sous forme de rendus lors de l’ingestion.

De nombreux clients de sites mettent en œuvre un servlet d’image qui redimensionne ou recadre les images lorsque cela est nécessaire, ce qui a pour effet d’appliquer une charge supplémentaire à l’instance de publication. Cependant, tant que ces images peuvent être mises en cache, le défi peut être atténué.

Une autre approche consiste à utiliser la technologie Dynamic Media Classic pour abandonner entièrement la manipulation d’images. En outre, vous pouvez déployer Brand Portal qui prend en charge les responsabilités de génération de rendu de la [!DNL Experience Manager] mais également l’ensemble du niveau de publication.

#### ImageMagick {#imagemagick}

Si vous personnalisez le workflow Ressources de mise à jour de gestion des actifs numériques pour générer des rendus à l’aide d’ImageMagick, Adobe vous recommande de modifier le fichier policy.xml à l’adresse */etc/ImageMagick/*. Par défaut, ImageMagick utilise l’espace disque disponible entier pour le volume du système d’exploitation et la quantité de mémoire disponible. Apportez les modifications de configuration suivantes dans le `policymap` de policy.xml pour limiter ces ressources.

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

En outre, définissez le chemin d’accès au dossier temporaire d’ImageMagick dans la variable *configure.xml* (ou en définissant la variable d’environnement) `MAGIC_TEMPORARY_PATH`) à une partition de disque disposant de suffisamment d’espace et d’IOPS.

>[!CAUTION]
>
>Une configuration incorrecte peut rendre votre serveur instable si ImageMagick utilise tout l’espace disque disponible. Les modifications de stratégie requises pour traiter des fichiers volumineux à l’aide d’ImageMagick peuvent avoir une incidence sur les performances d’[!DNL Experience Manager]. Pour plus d’informations, consultez la section [Installation et configuration d’ImageMagick](best-practices-for-imagemagick.md).

>[!NOTE]
>
>ImageMagick `policy.xml` et `configure.xml` Les fichiers se trouvent sous `/usr/lib64/ImageMagick-*/config/` au lieu de `/etc/ImageMagick/`. Voir [Documentation d’ImageMagick](https://www.imagemagick.org/script/resources.php) pour plus d’informations sur les emplacements des fichiers de configuration.

Si vous utilisez [!DNL Experience Manager] dans Adobe Managed Services (AMS), contactez l’assistance clientèle d’Adobe si vous envisagez de traiter un grand nombre de fichiers PSD ou PSB volumineux. Experience Manager ne peut pas traiter de fichiers PSB à très haute résolution, de plus de 30 000 x 23 000 pixels.

<!-- 

#### Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model 
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents **workflow model 

-->

<!--
# Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model.
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents** workflow model.
-->

### Écriture différée XMP {#xmp-writeback}

XMP écriture différée met à jour la ressource d’origine chaque fois que des métadonnées sont modifiées dans AEM, ce qui se traduit par les éléments suivants :

* La ressource elle-même est modifiée.
* Une version de la ressource est créée.
* La Ressource de mise à jour de gestion des ressources numériques est exécutée par rapport à la ressource.

Les résultats répertoriés consomment une grande quantité de ressources. Par conséquent, Adobe recommande [désactivation de l’écriture différée XMP](https://helpx.adobe.com/fr/experience-manager/kb/disable-xmp-writeback.html), s’il n’est pas obligatoire.

L’importation d’une grande quantité de métadonnées peut entraîner une activité d’écriture différée XMP gourmande en ressources si l’indicateur d’exécution des workflows est coché. Planifiez un tel import pendant l’utilisation du serveur afin que les performances des autres utilisateurs ne soient pas affectées.

## Réplication {#replication}

Lors de la réplication des ressources vers un grand nombre d’instances de publication (par exemple, dans une implémentation de sites), Adobe vous recommande d’utiliser la réplication par chaîne. Dans ce cas, l’instance d’auteur se réplique sur une instance de publication unique qui, à son tour, se réplique sur les autres instances de publication, libérant ainsi l’instance d’auteur.

### Configuration de la réplication en chaîne    {#configure-chain-replication}

1. Sélectionnez l’instance de publication vers laquelle vous souhaitez effectuer les réplications en chaîne
1. Sur cette instance de publication, ajoutez des agents de réplication qui pointent vers les autres instances de publication.
1. Sur chacun de ces agents de réplication, activez **[!UICONTROL À réception]** sur le **[!UICONTROL Triggers]** tab

>[!NOTE]
>
>Adobe ne recommande pas d’activer automatiquement les ressources. Cependant, si nécessaire, Adobe recommande d’effectuer cette opération en tant qu’étape finale d’un workflow, généralement Ressource de mise à jour de gestion des actifs numériques.

## Recherche des index    {#search-indexes}

Veillez à mettre en œuvre les derniers Service Packs et les correctifs liés aux performances étant donné qu’ils contiennent souvent des mises à jour des index du système. Voir [Conseils de réglage des performances | 6.x](https://helpx.adobe.com/fr/experience-manager/kb/performance-tuning-tips.html) pour connaître certaines optimisations d’index qui peuvent être appliquées en fonction de votre version d’AEM.

Créez des index personnalisés pour les demandes que vous exécutez régulièrement. Pour plus d’informations, consultez la [méthodologie pour l’analyse des requêtes lentes](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) et la [création d’index personnalisés](/help/sites-deploying/queries-and-indexing.md). Pour des informations complémentaires au sujet des bonnes pratiques concernant les requêtes et les index, consultez les [Bonnes pratiques relatives aux requêtes et à l’indexation](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Configurations de l’index Lucene {#lucene-index-configurations}

Certaines optimisations peuvent être effectuées sur les configurations d’index Oak qui peuvent contribuer à améliorer [!DNL Experience Manager] Performances des ressources :

Mettez à jour la configuration LuceneIndexProvider :

1. Accédez à /system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. Activer **[!UICONTROL CopyOnRead , CopyOnWrite et Prérécupération des fichiers d’index]** dans les versions antérieures à [!DNL Experience Manager] 6.2. Ces valeurs sont activées par défaut dans [!DNL Experience Manager] 6.2 et versions ultérieures.

Mettez à jour les configurations d’index pour améliorer le temps de réindexation :

1. Ouvrez CRXDe /crx/de/index.jsp et connectez-vous en tant qu’utilisateur administrateur.
1. Accédez à /oak:index/lucene
1. Ajouter une chaîne[] property nommée **[!UICONTROL excludedPaths]** avec les valeurs &quot;/var&quot;, &quot;/etc/workflow/instances&quot; et &quot;/etc/replication&quot;
1. Naviguez jusqu’à /oak:index/damAssetLucene.
1. Ajouter une chaîne[] property nommée **[!UICONTROL includedPaths]** avec une valeur &quot;/content/dam&quot;
1. Enregistrez.

(AEM 6.1 et 6.2 uniquement) Mettez à jour l’index ntBaseLucene pour améliorer les performances lors de la suppression et du déplacement des ressources :

1. Naviguez jusqu’à */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Ajout de deux noeuds nt:unstructured **[!UICONTROL slingResource]** et **[!UICONTROL damResolvedPath]** under */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Définissez les propriétés ci-dessous sur les noeuds (où les propriétés ordered et propertyIndex sont de type *Booléen*:

   slingResource

   name=&quot;sling:resource&quot;

   ordered=false

   propertyIndex= true

   type=&quot;String&quot;

   damResolvedPath

   name=&quot;dam:resolvedPath&quot;

   ordered=false

   propertyIndex=true

   type=&quot;String&quot;

1. Sur le nœud /oak:index/ntBaseLucene, définissez la propriété `reindex=true`.
1. Cliquez sur **[!UICONTROL Enregistrer tout]**
1. Surveillez le fichier error.log pour savoir quand l’indexation est terminée :

   Réindexation terminée pour les index : [/oak:index/ntBaseLucene]

1. Vous pouvez également constater que l’indexation est terminée en actualisant le noeud /oak:index/ntBaseLucene dans CRXDe, car la propriété reindex retourne à false
1. Une fois l’indexation terminée, revenez à CRXDe et définissez la variable **[!UICONTROL type]** pour désactiver la propriété sur ces deux index

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Cliquez sur **[!UICONTROL Enregistrer tout]**

Désactiver l’extraction de texte Lucene :

Si vos utilisateurs n’ont pas besoin de pouvoir rechercher le contenu des ressources, par exemple, en recherchant le texte contenu dans les documents du PDF, vous pouvez améliorer les performances de l’index en désactivant cette fonction.

1. Accédez au [!DNL Experience Manager] gestionnaire de modules /crx/packmgr/index.jsp
1. Téléchargez et installez le module ci-dessous.

[Obtenir le fichier](assets/disable_indexingbinarytextextraction-10.zip)

### Paramètre guessTotal {#guess-total}

Lors de la création de requêtes qui génèrent d’importants ensembles de résultats, utilisez le paramètre `guessTotal` de façon à éviter une utilisation élevée de la mémoire lors de l’exécution.

## Problèmes connus {#known-issues}

### Fichiers volumineux {#large-files}

Il existe deux problèmes importants connus relatifs aux fichiers volumineux dans AEM. Lorsque la taille des fichiers est supérieure à 2 Go, la synchronisation de reprise progressive peut s’exécuter en cas de mémoire insuffisante. Dans certains cas, cela empêche la synchronisation de reprise de s’exécuter. Dans d’autres cas, cela entraîne le blocage de l’instance principale. Ce scénario s’applique à tous les fichiers dans [!DNL Experience Manager] dont la taille est supérieure à 2 Go, y compris les packages de contenu.

De même, lorsque les fichiers atteignent une taille de 2 Go lors de l’utilisation d’une banque de données S3 partagée, il peut s’écouler un certain temps avant que le fichier soit entièrement conservé du cache vers le système de fichiers. Par conséquent, lorsque vous avez recours à une réplication sans binaire, il est possible que les données binaires ne soient pas conservées avant la fin de la réplication. Cette situation peut entraîner des problèmes, en particulier si la disponibilité des données est importante, par exemple dans les scénarios de déchargement.

## Test de performance {#performance-testing}

Pour chaque déploiement d’[!DNL Experience Manager], créez un régime de tests de performances qui permet d’identifier et de résoudre les goulots d’étranglement rapidement. Voici quelques points clés.

### Test réseau    {#network-testing}

Pour toutes les préoccupations de performances du réseau du client, effectuez les tâches suivantes :

* Tester les performances du réseau depuis le réseau client
* Testez les performances du réseau sur le réseau Adobe. Pour les clients AMS, consultez votre CSE pour effectuer des tests sur le réseau Adobe.
* Test des performances du réseau à partir d’un autre point d’accès
* En utilisant un outil de référence de réseau
* Test par rapport au Dispatcher

### [!DNL Experience Manager] test d’instance {#aem-instance-testing}

Pour réduire la latence et atteindre un débit élevé grâce à une utilisation efficace du processeur et au partage de la charge, surveillez les performances de votre [!DNL Experience Manager] régulièrement. En particulier :

* Exécutez des tests de chargement sur le [!DNL Experience Manager] instance
* Surveillez les performances de chargement et la réactivité de l’interface utilisateur

## [!DNL Experience Manager] Liste de contrôle des performances des ressources {#aem-assets-performance-checklist}

* Autoriser HTTPS à contourner tous les renifleurs de trafic HTTP d’entreprise.
* Utilisez une connexion câblée pour le chargement de ressources volumineuses.
* Définissez des paramètres JVM optimaux.
* Configurez un entrepôt de données de système de fichiers ou un entrepôt de données S3.
* Désactivez la génération de sous-ressources. Si elle est activée, le workflow d’AEM crée une ressource distincte pour chaque page dans une ressource multi-page. Chacune de ces pages est une ressource en elle-même, qui consomme de l’espace disque supplémentaire et requiert la création de versions et un traitement de workflow supplémentaire. Si vous n’avez pas besoin de pages séparées, désactivez les activités d’extraction de page et de génération de sous-ressources.
* Activez les workflows transitoires.
* Réglez les files d’attente de workflows Granite pour limiter les tâches concurrentes.
* Configurez ImageMagick pour limiter la consommation des ressources.
* Supprimez les étapes inutiles du workflow Ressource de mise à jour de gestion des ressources numériques.
* Configurez la purge des workflows et des versions.
* Optimisez la configuration de l’index Lucene.
* Optimisez les index avec les derniers Service Pack et correctifs. Vérifiez auprès de l’assistance clientèle Adobe toutes les optimisations d’index supplémentaires qui pourraient être disponibles.
* Utilisation `guessTotal` pour optimiser les performances des requêtes.
* Si vous configurez [!DNL Experience Manager] pour détecter les types de fichiers à partir du contenu des fichiers (en configurant [!UICONTROL Service Day CQ DAM Mime Type] dans le [!UICONTROL [!DNL Experience Manager] Console web]), téléchargez de nombreux fichiers en bloc pendant les heures creuses, car l’opération consomme beaucoup de ressources.
