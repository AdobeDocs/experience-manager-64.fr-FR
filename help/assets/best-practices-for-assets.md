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


# Best practices for AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets est essentiel pour fournir des expériences marketing numériques de qualité qui contribuent à la réussite des objectifs commerciaux en augmentant la vélocité du contenu. Si vous travaillez avec un grand nombre de ressources dans AEM Assets ou si vous téléchargez régulièrement/périodiquement de nombreuses ressources, y compris des vidéos et des médias dynamiques, l’optimisation de votre expérience de gestion des actifs numériques est essentielle pour l’efficacité du système.

Selon la place qu’occupe AEM Assets pour votre organisation et les fonctionnalités que vous utilisez pour l’intégration des ressources, la génération du rendu et l’extraction des métadonnées, l’identification et le respect des meilleures pratiques dans divers domaines renforce considérablement la stabilité et les performances du système en présence d’une charge élevée.

Après avoir passé en revue les guides suivants, vous disposerez des connaissances et des outils nécessaires pour créer et gérer un système de gestion des actifs d’entreprise qui répond à vos besoins.

* [Guide](performance-tuning-guidelines.md)d’optimisation des performances des ressources Comprend un ensemble de bonnes pratiques qui peuvent être suivies à tout moment de votre mise en oeuvre, même après votre mise en service, pour vous assurer que vous tirez le meilleur parti de votre système.
* [Guide](assets-sizing-guide.md)de dimensionnement des ressources Lors de l&#39;élaboration des estimations pour une mise en oeuvre des ressources, il est important de s&#39;assurer que les ressources disponibles sont suffisantes en termes d&#39;enregistrement des ressources, d&#39;UC, de mémoire, d&#39;E/S et de débit réseau. Pour dimensionner un grand nombre de ces éléments, il est nécessaire de connaître le nombre de ressources à charger dans le système. Ce guide comprend les bonnes pratiques qui permettent de déterminer des mesures efficaces pour estimer l’infrastructure et les ressources nécessaires pour déployer AEM Assets, ainsi qu’un outil de dimensionnement.
* [Guide](assets-migration-guide.md)de migration des ressources Si vous souhaitez migrer des ressources de votre système hérité vers AEM Assets, plusieurs étapes vous permettent de rationaliser le processus de migration. Le guide de migration inclut les bonnes pratiques concernant les tâches que vous effectuez pour importer les ressources dans AEM en plusieurs phases. Cela inclut l’application de métadonnées, la génération de rendus et l’activation des ressources pour le déploiement de publication.
* [Considérations relatives](assets-network-considerations.md)au réseau des ressources Lors de la gestion du déploiement AEM, il est important de comprendre la topologie du réseau pour comprendre les performances du réseau, identifier les points de blocage et décrire l’expérience utilisateur attendue. Le document Considérations concernant le réseau Assets aborde les éléments à considérer vis-à-vis du réseau lors de la conception de votre déploiement AEM Assets.
* [Guide](assets-monitoring-best-practices.md)de surveillance des ressources Une fois votre déploiement AEM déployé, vous devez surveiller certaines tâches et le système en général afin d’assurer l’intégrité et l’efficacité du système. Le Guide de surveillance comprend les bonnes pratiques pour contrôler les différents aspects de votre système.
* (Deprecated) [Assets offloading guide](assets-offloading-best-practices.md)
Handling large files and running workflows in AEM Assets can consume considerable CPU, memory, and I/O resources. Le déchargement de ces tâches peut réduire les surcharges d’unité centrale, de mémoire et d’E/S. Le Guide de déchargement Assets inclut les cas d’utilisation recommandés et les meilleures pratiques pour le déchargement dans Assets.
* [AEM meilleures pratiques](https://helpx.adobe.com/fr/experience-manager/desktop-app/aem-desktop-app-best-practices.html)pour les applications de bureau AEM application de bureau associe votre solution de gestion des actifs numériques (DAM) à votre bureau afin que vous puissiez ouvrir les fichiers disponibles dans l’interface utilisateur Web de l’interface utilisateur Web de l’AEM, directement sur le bureau. Le workflow convivial de l’application de bureau AEM est activé à l’aide de la technologie de partage réseau fournie par les systèmes d’exploitation de bureau. Ce guide décrit les fonctionnalités essentielles et l’utilisation recommandée de l’application de bureau AEM.
* [Meilleures pratiques](aem-cc-integration-best-practices.md)d’intégration AEM et Creative Cloud Vous pouvez intégrer votre déploiement AEM à Creative Cloud de plusieurs manières. En suivant les bonnes pratiques pour simplifier votre intégration et vos workflows de transfert des ressources, vous bénéficiez d’une efficacité maximale. Ce guide inclut les bonnes pratiques concernant l’intégration d’AEM Assets à Adobe Creative Cloud.
* (Deprecated) [AEM to Creative Cloud folder sharing best practices](aem-cc-folder-sharing-best-practices.md)
You can configure AEM to allow users in DAM to share folders with Creative Cloud (CC) users, so they are available as shared folders in the Creative Cloud Assets service. La fonctionnalité peut être utilisée pour échanger des fichiers entre les équipes créatives et les utilisateurs DAM. Ce guide décrit les meilleures pratiques pour tirer parti de la fonction de partage de dossiers AEM vers Creative Cloud.
