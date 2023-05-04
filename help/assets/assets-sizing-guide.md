---
title: Guide de dimensionnement des ressources
description: Bonnes pratiques pour déterminer des mesures efficaces pour estimer l’infrastructure et les ressources nécessaires au déploiement [!DNL Experience Manager] Ressources.
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
feature: Asset Management
role: Architect,Admin
exl-id: 6115e5e8-9cf5-417c-91b3-0c0c9c278b5b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 25%

---

# Guide de dimensionnement des ressources {#assets-sizing-guide}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lors du dimensionnement de l’environnement pour une mise en oeuvre d’Adobe Experience Manager Assets, il est important de s’assurer qu’il existe suffisamment de ressources disponibles en termes de disque, unité centrale, mémoire, E/S et débit réseau. Le dimensionnement de plusieurs de ces ressources nécessite une compréhension du nombre de ressources chargées dans le système. Si aucune meilleure mesure n’est disponible, vous pouvez diviser la taille de la bibliothèque existante par l’âge de la bibliothèque pour trouver le taux de création des ressources.

## Disque {#disk}

### DataStore {#datastore}

Une erreur courante lors du dimensionnement de l’espace disque nécessaire à une implémentation d’Assets consiste à baser les calculs sur la taille des images brutes à ingérer dans le système. Par défaut, [!DNL Experience Manager] crée trois rendus en plus de l’image d’origine à utiliser dans le rendu de la variable [!DNL Experience Manager] Eléments de l’interface utilisateur. Dans les mises en oeuvre précédentes, ces rendus supposent deux fois la taille des ressources ingérées.

La plupart des utilisateurs définissent des rendus personnalisés en plus des rendus prêts à l’emploi. Outre les rendus, Assets vous permet d’extraire des sous-ressources à partir de types de fichiers courants, tels qu’InDesign et Illustrator.

Enfin, les fonctionnalités de contrôle de version d’AEM stockent les doublons des ressources dans l’historique des versions. Vous pouvez configurer les versions à purger aussi fréquemment que souhaité. Cependant, de nombreux utilisateurs choisissent de conserver longtemps les versions dans le système, ce qui consomme de l’espace de stockage supplémentaire.

Compte tenu de ces facteurs, vous avez besoin d’une méthodologie pour calculer un espace de stockage acceptable et précis afin de stocker les ressources des utilisateurs.

1. Déterminez la taille et le nombre de ressources qui seront chargées dans le système.
1. Obtenez un échantillon représentatif des ressources à charger dans AEM. Par exemple, si vous prévoyez de charger des fichiers PSD, JPG, AI et PDF dans le système, vous avez besoin de plusieurs exemples d’images de chaque format de fichier. En outre, ces exemples doivent être représentatifs des différentes tailles de fichiers et de la complexité des images.
1. Définissez les rendus à utiliser.
1. Créez les rendus dans [!DNL Experience Manager] à l’aide d’ImageMagick ou des applications de Creative Cloud d’Adobe. En plus des rendus que les utilisateurs spécifient, créez des rendus prêts à l’emploi. Pour les utilisateurs qui implémentent Dynamic Media Classic, vous pouvez utiliser le binaire IC pour générer les rendus PTIFF à stocker dans AEM.
1. Si vous prévoyez d’utiliser des sous-ressources, générez-les pour les types de fichiers appropriés. Consultez la documentation en ligne sur la génération de pages de sous-ressources à partir de fichiers InDesign ou de fichiers PNG/PDF à partir de calques Illustrator.
1. Comparez la taille des images, rendus et sous-ressources de sortie avec les images d’origine. Cette comparaison permet de générer un facteur de croissance attendu lorsque le système est chargé. Par exemple, si vous générez des rendus et des sous-ressources d’une taille combinée de 3 Go après le traitement de 1 Go de ressources, le facteur de croissance des rendus est de 3.
1. Déterminez la durée maximale pendant laquelle les versions de ressources doivent être conservées dans le système.
1. Permet de déterminer la fréquence de modification des ressources existantes dans le système. Si [!DNL Experience Manager] est utilisé comme centre de collaboration dans les workflow de création, le nombre de modifications est élevé. Si seules les ressources terminées sont chargées sur le système, ce nombre est beaucoup plus faible.
1. Déterminez le nombre de ressources chargées dans le système chaque mois. Si vous n’êtes pas certain, vérifiez le nombre de ressources actuellement disponibles et divisez le nombre par l’âge de la ressource la plus ancienne pour calculer un nombre approximatif.

L’exécution des étapes 1 à 9 vous permet de déterminer les éléments suivants :

* Taille brute des ressources à charger
* Nombre de ressources à charger
* Facteur de croissance du rendu
* Nombre de modifications de ressources effectuées par mois
* Nombre de mois pour la maintenance des versions de ressources
* Nombre de nouvelles ressources chargées chaque mois
* Années de croissance pour lesquelles allouer de l’espace

Vous pouvez indiquer ces chiffres dans la feuille de calcul Dimensionnement du réseau afin de déterminer l’espace total requis pour le magasin de données. C’est également un outil utile pour déterminer l’impact de la conservation des versions des ressources ou de la modification des ressources dans [!DNL Experience Manager] sur la croissance du disque.

Les exemples de données renseignés dans l’outil montrent à quel point il est important de réaliser les étapes mentionnées. Si vous dimensionnez le magasin de données uniquement en fonction des images brutes à charger (1 To), vous avez peut-être sous-estimé la taille du référentiel d’un facteur de 15.

[Obtenir le fichier](assets/disk_sizing_tool.xlsx)

### Entrepôts de données partagés {#shared-datastores}

Pour les banques de données volumineuses, vous pouvez mettre en oeuvre une banque de données partagée par le biais d’une banque de données de fichiers partagée sur un lecteur connecté au réseau ou via une banque de données S3. Dans ce cas, les instances individuelles n’ont pas besoin de conserver une copie des fichiers binaires. En outre, une banque de données partagée facilite la réplication sans fichier binaire et contribue à réduire la bande passante utilisée pour répliquer les ressources vers les environnements de publication ou les instances de déchargement.

#### Cas d’utilisation {#use-cases}

Le magasin de données peut être partagé entre une instance d’auteur principale et de secours afin de réduire le temps nécessaire à la mise à jour de l’instance de secours avec les modifications apportées à l’instance principale. Adobe recommande de partager la banque de données entre une instance d’auteur Principale et les instances d’auteur de déchargement afin de réduire les surcharges dans le déchargement du workflow. Vous pouvez également partager la banque de données entre les instances d’auteur et de publication afin de réduire le trafic pendant la réplication.

#### Inconvénients {#drawbacks}

En raison de certains écueils, le partage d’une banque de données n’est pas recommandé dans tous les cas.

#### Point d’échec unique {#single-point-of-failure}

Disposer d’une banque de données partagée introduit un point unique d’échec dans une infrastructure. Supposons que votre système dispose d’une instance de création et de deux instances de publication, chacune disposant de sa propre banque de données. Si l&#39;un d&#39;eux se bloque, les deux autres peuvent continuer à fonctionner. Cependant, si la banque de données est partagée, une seule panne de disque peut entraîner l’arrêt de toute l’infrastructure. Par conséquent, assurez-vous de conserver une sauvegarde de la banque de données partagée à partir de laquelle vous pouvez restaurer rapidement la banque de données.

Il est préférable de déployer le service AWS S3 pour les entrepôts de données partagés, car cela réduit considérablement la probabilité d’échec par rapport aux architectures de disque normales.

#### Complexité accrue {#increased-complexity}

Les banques de données partagées augmentent également la complexité des opérations, telles que le nettoyage de la mémoire. Normalement, le nettoyage de la mémoire pour une banque de données autonome peut être lancé en un seul clic. Toutefois, les banques de données partagées nécessitent des opérations de balayage des marques sur chaque membre qui utilise l’entrepôt de données, en plus d’exécuter la collection réelle sur un seul noeud.

Pour les opérations AWS, la mise en œuvre d’un emplacement central unique (via  S3) plutôt que la création d’une matrice RAID de volumes EBS peut considérablement limiter la complexité et les risques opérationnels du système.

#### Problèmes de performances {#performance-concerns}

Un magasin de données partagé nécessite que les fichiers binaires soient stockés sur un lecteur monté sur le réseau partagé entre toutes les instances. Comme ces fichiers binaires sont accessibles sur un réseau, les performances du système sont affectées. Vous pouvez partiellement atténuer cet impact en utilisant une connexion réseau rapide à une matrice rapide de disques. Toutefois, il s’agit d’une proposition coûteuse. Dans le cas des opérations AWS, tous les disques sont distants et nécessitent une connectivité réseau. Les volumes éphémères perdent des données lorsque l’instance démarre ou s’arrête.

#### Latence {#latency}

La latence dans les implémentations S3 est introduite par les threads d’écriture en arrière-plan. Les procédures de sauvegarde doivent tenir compte de cette latence et de toutes les procédures de déchargement. La ressource S3 peut ne pas être présente dans S3 lorsqu’une tâche de déchargement démarre. En outre, les index Lucene peuvent rester incomplets lors d’une sauvegarde. Il s’applique à tout fichier sensible au temps écrit dans la banque de données S3 et accessible à partir d’une autre instance.

### Magasin de noeuds/Magasin de documents {#node-store-document-store}

Il est difficile d’obtenir des chiffres de dimensionnement précis pour un NodeStore ou un DocumentStore en raison des ressources utilisées par les éléments suivants :

* Métadonnées de ressource
* Versions des ressources
* Journaux d’audit
* Workflows archivés et principaux

Comme les fichiers binaires sont stockés dans la banque de données, chaque fichier binaire occupe un certain espace. La plupart des référentiels ont une taille inférieure à 100 Go. Cependant, il peut y avoir des référentiels de taille supérieure à 1 To. De plus, pour effectuer un compactage hors ligne, vous avez besoin d’assez d’espace sur le volume pour réécrire le référentiel compacté avec la version précompactée. Une bonne règle de base consiste à dimensionner le disque à 1,5 fois la taille attendue pour le référentiel.

Pour le référentiel, utilisez des disques SSD ou des disques dont le niveau IOPS est supérieur à 3000. Pour éviter que les IOPS n’introduisent des goulets d’étranglement en termes de performances, surveillez les niveaux d’attente des E/S du processeur pour détecter les premiers signes de problèmes.

[Obtenir le fichier](assets/aem_environment_sizingtool.xlsx)

## Réseau {#network}

[!DNL Assets] comporte plusieurs cas d’utilisation qui rendent la performance du réseau plus importante que sur la plupart de nos projets [!DNL Experience Manager]. Un client peut disposer d’un serveur rapide, mais si la connexion réseau n’est pas assez puissante pour soutenir la charge des utilisateurs qui chargent et téléchargent des ressources à partir du système, il semblera toujours lent. Il existe une bonne méthodologie pour déterminer le point d’étranglement dans la connexion réseau d’un utilisateur à [!DNL Experience Manager] at [[!DNL Experience Manager]  Considérations sur les ressources pour l’expérience utilisateur, le dimensionnement des instances, l’évaluation des workflows et la topologie de réseau](assets-network-considerations.md).

## WebDAV {#webdav}

Si vous ajoutez le [!DNL Experience Manager] L’appli de bureau en parallèle, les problèmes de réseau deviennent plus graves en raison de l’inefficacité du protocole WebDAV.

Pour illustrer ces inefficacités, Adobe a testé les performances du système à l’aide de WebDAV sur OS X. Un fichier d’InDesign de 3,5 Mo a été ouvert, modifié et les modifications enregistrées. Les observations suivantes ont été faites :

* Environ 100 requêtes HTTP ont été générées pour terminer l’opération.
* Le fichier a été chargé quatre fois sur HTTP.
* Le fichier a été téléchargé une fois sur HTTP.
* L’opération entière a duré 42 secondes.
* Un total de 18 Mo de données a été transféré.

Lors de l’analyse du temps d’enregistrement moyen des fichiers sur WebDAV, il a été constaté que les performances augmentent considérablement lorsque la bande passante augmente jusqu’au niveau de 5 à 10 Mbit/s. Par conséquent, Adobe recommande que chaque utilisateur accédant simultanément au système dispose d’au moins 10 Mbit/s de vitesse de chargement et de 5 à 10 Mbit/s de bande passante.

Pour plus d’informations, voir [Dépannage [!DNL Experience Manager] application de bureau](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html).

## Limites {#limitations}

Lors du dimensionnement d’une mise en oeuvre, il est important de garder à l’esprit les limites du système. Si l’implémentation proposée dépasse ces limites, utilisez des stratégies de création, telles que le partitionnement des ressources entre plusieurs implémentations Assets.

La taille du fichier n’est pas le seul facteur qui contribue aux problèmes de mémoire insuffisante (OOM). Cela dépend également des dimensions de l’image. Vous pouvez éviter les problèmes OOM en fournissant une taille de tas supérieure au démarrage de l’AEM.

En outre, vous pouvez modifier la propriété de taille de seuil du composant `com.day.cq.dam.commons.handler.StandardImageHandler` dans Configuration Manager pour utiliser un fichier temporaire intermédiaire supérieur à zéro.

## Nombre maximal de ressources {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

La limite du nombre de fichiers pouvant exister dans une banque de données peut être de 2,1 milliards en raison de limitations du système de fichiers. Il est probable que le référentiel rencontre des problèmes en raison d’un grand nombre de noeuds bien avant d’atteindre la limite de l’entrepôt de données.

Si les rendus sont générés de manière incorrecte, utilisez la bibliothèque Camera Raw. Toutefois, dans ce cas, le côté le plus long de l’image ne doit pas être supérieur à 65 000 pixels. En outre, l’image ne doit pas contenir plus de 512 MP (512 &amp;ast; 1024 &amp;ast; 1 024 pixels)&quot;. *La taille de la ressource est sans importance*.

Il est difficile d’estimer avec précision la taille du fichier de TIFF pris en charge prêt à l’emploi avec un tas spécifique pour [!DNL Experience Manager] car d’autres facteurs, tels que la taille des pixels, influencent le traitement. Il est possible que [!DNL Experience Manager] peut traiter un fichier de 255 Mo en standard, mais ne peut pas traiter une taille de fichier de 18 Mo car cette dernière comprend un nombre de pixels exceptionnellement supérieur à celui de la première.

## Taille des ressources {#size-of-assets}

Par défaut, [!DNL Experience Manager] vous permet de charger des ressources d’une taille de fichier pouvant aller jusqu’à 2 Go. Pour charger des ressources très volumineuses dans AEM, voir [Configuration pour charger des ressources très volumineuses](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb).
