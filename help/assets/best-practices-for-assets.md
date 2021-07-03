---
title: Bonnes pratiques pour gérer les ressources à l’aide d’AEM
description: Identifiez et respectez les bonnes pratiques qui améliorent la stabilité et les performances du système lors de la charge, en fonction du déploiement d’AEM Assets et des fonctionnalités utilisées pour l’ingestion et le traitement des ressources.
contentOwner: AG
feature: Gestion des ressources
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 45%

---

# Bonnes pratiques pour AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets est essentiel pour fournir des expériences marketing numériques de qualité qui contribuent à la réussite des objectifs commerciaux en augmentant la vélocité du contenu. Si vous travaillez avec un grand nombre de ressources dans AEM Assets ou si vous téléchargez régulièrement/périodiquement de nombreuses ressources, y compris des vidéos et des médias dynamiques, l’optimisation de votre expérience de gestion des actifs numériques est essentielle pour l’efficacité du système.

Selon la place qu’occupe AEM Assets pour votre organisation et les fonctionnalités que vous utilisez pour l’intégration des ressources, la génération du rendu et l’extraction des métadonnées, l’identification et le respect des meilleures pratiques dans divers domaines renforce considérablement la stabilité et les performances du système en présence d’une charge élevée.

Après avoir consulté les guides suivants, vous disposerez des connaissances et des outils nécessaires pour créer et gérer un système de gestion des actifs d’entreprise qui répond à vos besoins.

* [](performance-tuning-guidelines.md)
Guide d’optimisation des performances d’Assets : ce guide comprend un ensemble de bonnes pratiques que vous pouvez suivre à tout moment dans votre mise en oeuvre, même après activation, pour vous assurer que vous tirez pleinement parti de votre système.
* [](assets-sizing-guide.md)
Guide de dimensionnement des ressources : lors de l’établissement d’estimations pour une mise en oeuvre d’Assets, il est important de s’assurer qu’il existe suffisamment de ressources disponibles en termes de stockage des ressources, unité centrale, E/S et débit réseau. Pour dimensionner un grand nombre de ces éléments, il est nécessaire de connaître le nombre de ressources à charger dans le système. Ce guide comprend les bonnes pratiques qui permettent de déterminer des mesures efficaces pour estimer l’infrastructure et les ressources nécessaires pour déployer AEM Assets, ainsi qu’un outil de dimensionnement.
* [](assets-migration-guide.md)
Guide de migration des ressources : si vous souhaitez migrer des ressources de votre ancien système vers AEM Assets, plusieurs étapes sont nécessaires pour rationaliser le processus de migration. Le guide de migration inclut les bonnes pratiques concernant les tâches que vous effectuez pour importer les ressources dans AEM en plusieurs phases. Cela inclut l’application de métadonnées, la génération de rendus et l’activation des ressources pour le déploiement de publication.
* [](assets-network-considerations.md)
Considérations relatives au réseau des ressources : lors de la gestion du déploiement AEM, il est important de comprendre la topologie du réseau pour comprendre les performances du réseau, identifier les goulots d’étranglement et décrire l’expérience utilisateur attendue. Le document Considérations concernant le réseau Assets aborde les éléments à considérer vis-à-vis du réseau lors de la conception de votre déploiement AEM Assets.
* [](assets-monitoring-best-practices.md)
Guide de surveillance des ressources : une fois votre déploiement AEM déployé, vous devez surveiller certaines tâches et le système en général pour garantir l’intégrité du système et l’efficacité des opérations. Le Guide de surveillance comprend les bonnes pratiques pour contrôler les différents aspects de votre système.
* (Obsolète) [Guide de déchargement des ressources](assets-offloading-best-practices.md)
La gestion de fichiers volumineux et l’exécution de workflows dans AEM Assets peuvent consommer une quantité considérable de ressources d’unité centrale, de mémoire et d’E/S. Le déchargement de ces tâches peut réduire les surcharges d’unité centrale, de mémoire et d’E/S. Le Guide de déchargement Assets inclut les cas d’utilisation recommandés et les meilleures pratiques pour le déchargement dans Assets.
* [Bonnes ](https://helpx.adobe.com/fr/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
pratiques relatives à l’appli de bureau AEM L’appli de bureau AEM associe votre solution de gestion des ressources numériques (DAM) à votre bureau afin que vous puissiez ouvrir les fichiers disponibles dans l’interface utilisateur web d’AEM directement sur le bureau. Le workflow convivial de l’application de bureau AEM est activé à l’aide de la technologie de partage réseau fournie par les systèmes d’exploitation de bureau. Ce guide décrit les fonctionnalités essentielles et l’utilisation recommandée de l’application de bureau AEM.
* [Bonnes ](aem-cc-integration-best-practices.md)
pratiques d’intégration AEM et Creative CloudVous pouvez intégrer votre déploiement AEM à Creative Cloud de plusieurs manières. En suivant les bonnes pratiques pour simplifier votre intégration et vos workflows de transfert des ressources, vous bénéficiez d’une efficacité maximale. Ce guide inclut les bonnes pratiques concernant l’intégration d’AEM Assets à Adobe Creative Cloud.
* (Obsolète) [AEM aux bonnes pratiques en matière de partage de dossiers de Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Vous pouvez configurer AEM pour permettre aux utilisateurs de la gestion des actifs numériques de partager des dossiers avec les utilisateurs de Creative Cloud (CC) afin qu’ils soient disponibles sous forme de dossiers partagés dans le service Ressources du Creative Cloud. La fonctionnalité peut être utilisée pour échanger des fichiers entre les équipes créatives et les utilisateurs DAM. Ce guide explique les bonnes pratiques à suivre pour tirer parti de la fonctionnalité de partage de dossiers AEM à Creative Cloud.
