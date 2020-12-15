---
title: Meilleures pratiques de gestion des ressources à l’aide de AEM
description: Identifiez et respectez les meilleures pratiques qui améliorent la stabilité et les performances du système en charge, en fonction du déploiement AEM Assets et des fonctionnalités utilisées pour assimiler et traiter les ressources.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 45%

---


# Meilleures pratiques pour l&#39;AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets est essentiel pour fournir des expériences marketing numériques de qualité qui contribuent à la réussite des objectifs commerciaux en augmentant la vélocité du contenu. Si vous travaillez avec un grand nombre de ressources dans AEM Assets ou si vous téléchargez régulièrement/périodiquement de nombreuses ressources, y compris des vidéos et des médias dynamiques, l’optimisation de votre expérience de gestion des actifs numériques est essentielle pour l’efficacité du système.

Selon la place qu’occupe AEM Assets pour votre organisation et les fonctionnalités que vous utilisez pour l’intégration des ressources, la génération du rendu et l’extraction des métadonnées, l’identification et le respect des meilleures pratiques dans divers domaines renforce considérablement la stabilité et les performances du système en présence d’une charge élevée.

Après avoir passé en revue les guides suivants, vous disposerez des connaissances et des outils nécessaires pour créer et gérer un système de gestion des actifs d’entreprise qui répond à vos besoins.

* [](performance-tuning-guidelines.md)
guide d&#39;optimisation des performances des ressourcesInclut un ensemble de bonnes pratiques qui peuvent être suivies à tout moment de votre mise en oeuvre, même après votre mise en service, pour vous assurer que vous tirez le meilleur parti de votre système.
* [](assets-sizing-guide.md)
guide de dimensionnement des ressourcesLors de l&#39;élaboration des estimations d&#39;une mise en oeuvre des ressources, il est important de s&#39;assurer que les ressources disponibles sont suffisantes en termes d&#39;enregistrement des ressources, d&#39;UC, de mémoire, d&#39;E/S et de débit réseau. Pour dimensionner un grand nombre de ces éléments, il est nécessaire de connaître le nombre de ressources à charger dans le système. Ce guide comprend les bonnes pratiques qui permettent de déterminer des mesures efficaces pour estimer l’infrastructure et les ressources nécessaires pour déployer AEM Assets, ainsi qu’un outil de dimensionnement.
* [Guide de migration des ressourcesSi vous souhaitez migrer des ressources de votre système hérité vers AEM Assets, plusieurs étapes vous permettent de rationaliser le processus de migration. ](assets-migration-guide.md)
Le guide de migration inclut les bonnes pratiques concernant les tâches que vous effectuez pour importer les ressources dans AEM en plusieurs phases. Cela inclut l’application de métadonnées, la génération de rendus et l’activation des ressources pour le déploiement de publication.
* [Ressources : ](assets-network-considerations.md)
considérations relatives au réseauLors de la gestion du déploiement AEM, il est important de comprendre la topologie du réseau pour comprendre les performances du réseau, identifier les points de blocage et décrire l&#39;expérience utilisateur attendue. Le document Considérations concernant le réseau Assets aborde les éléments à considérer vis-à-vis du réseau lors de la conception de votre déploiement AEM Assets.
* [](assets-monitoring-best-practices.md)
guide de surveillance des ressourcesUne fois votre déploiement AEM déployé, vous devez surveiller certaines tâches et le système en général afin d&#39;assurer l&#39;intégrité et l&#39;efficacité du système. Le Guide de surveillance comprend les bonnes pratiques pour contrôler les différents aspects de votre système.
* (Obsolète) [Guide de déchargement des ressources](assets-offloading-best-practices.md)
La gestion de fichiers volumineux et l&#39;exécution de workflows en AEM Assets peuvent nécessiter des ressources considérables en UC, en mémoire et en E/S. Le déchargement de ces tâches peut réduire les surcharges d’unité centrale, de mémoire et d’E/S. Le Guide de déchargement Assets inclut les cas d’utilisation recommandés et les meilleures pratiques pour le déchargement dans Assets.
* [aem meilleures ](https://helpx.adobe.com/fr/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
pratiques pour les applications de bureauL&#39;application de bureau AEM associe votre solution de gestion des actifs numériques (DAM) à votre bureau afin que vous puissiez ouvrir les fichiers disponibles dans l&#39;interface utilisateur Web AEM directement sur le bureau. Le workflow convivial de l’application de bureau AEM est activé à l’aide de la technologie de partage réseau fournie par les systèmes d’exploitation de bureau. Ce guide décrit les fonctionnalités essentielles et l’utilisation recommandée de l’application de bureau AEM.
* [Meilleures ](aem-cc-integration-best-practices.md)
pratiques d&#39;intégration AEM et Creative CloudVous pouvez intégrer votre déploiement AEM à Creative Cloud de plusieurs manières. En suivant les bonnes pratiques pour simplifier votre intégration et vos workflows de transfert des ressources, vous bénéficiez d’une efficacité maximale. Ce guide inclut les bonnes pratiques concernant l’intégration d’AEM Assets à Adobe Creative Cloud.
* (Obsolète) [AEM aux bonnes pratiques de partage de dossiers Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Vous pouvez configurer AEM pour permettre aux utilisateurs dans DAM de partager des dossiers avec des utilisateurs Creative Cloud (CC), de sorte qu’ils soient disponibles sous forme de dossiers partagés dans le service Ressources du Creative Cloud. La fonctionnalité peut être utilisée pour échanger des fichiers entre les équipes créatives et les utilisateurs DAM. Ce guide décrit les meilleures pratiques pour tirer parti de la fonction de partage de dossiers AEM vers Creative Cloud.
