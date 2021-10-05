---
title: Bonnes pratiques pour gérer les ressources à l’aide d’AEM
description: 'Identifiez et respectez les bonnes pratiques qui améliorent la stabilité et les performances du système lors de la charge, en fonction du déploiement des ressources et des fonctionnalités utilisées pour l’ingestion et le traitement des ressources. [!DNL Experience Manager] '
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: d750c852b6367d753d18be57c8910bf5671fd5e8
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 16%

---

# Bonnes pratiques pour [!DNL Experience Manager] Assets {#best-practices-for-assets}

Adobe Experience Manager Assets est un élément essentiel de la diffusion d’expériences marketing numériques de haute qualité qui contribuent à la réalisation des objectifs de l’entreprise en augmentant la vitesse de votre contenu. Si vous utilisez un grand nombre de ressources dans [!DNL Assets] ou que vous chargez régulièrement/régulièrement de nombreuses ressources, y compris des vidéos et des médias dynamiques, l’optimisation de votre expérience de gestion des ressources numériques est essentielle à l’efficacité du système.

Selon la manière dont vous avez positionné [!DNL Assets] pour votre organisation et les fonctionnalités que vous utilisez pour l’assimilation de ressources, la génération de rendus et l’extraction de métadonnées, l’identification et le respect des bonnes pratiques dans différents domaines améliorent considérablement la stabilité et les performances du système en cas de charge.

Après avoir consulté les guides suivants, vous disposerez des connaissances et des outils nécessaires pour créer et gérer un système de gestion des actifs d’entreprise qui répond à vos besoins.

* [](performance-tuning-guidelines.md)
Guide d’optimisation des performances d’Assets : ce guide comprend un ensemble de bonnes pratiques que vous pouvez suivre à tout moment dans votre mise en oeuvre, même après activation, pour vous assurer que vous tirez pleinement parti de votre système.
* [](assets-sizing-guide.md)
Guide de dimensionnement des ressources : lors de l’établissement d’estimations pour une mise en oeuvre d’Assets, il est important de s’assurer qu’il existe suffisamment de ressources disponibles en termes de stockage des ressources, unité centrale, E/S et débit réseau. Pour dimensionner un grand nombre de ces éléments, il est nécessaire de connaître le nombre de ressources à charger dans le système. Ce guide comprend les bonnes pratiques qui permettent de déterminer des mesures efficaces pour estimer l’infrastructure et les ressources nécessaires au déploiement de [!DNL Experience Manager] Assets, ainsi qu’un outil de dimensionnement.
* [](assets-migration-guide.md)
Guide de migration des ressources : si vous souhaitez migrer des ressources de votre ancien système vers  [!DNL Experience Manager] Assets, vous devez suivre plusieurs étapes pour rationaliser le processus de migration. Le guide de migration inclut les bonnes pratiques relatives aux tâches que vous effectuez pour importer les ressources dans [!DNL Experience Manager] de manière progressive. Cela inclut l’application de métadonnées, la génération de rendus et l’activation des ressources pour le déploiement de publication.
* [](assets-network-considerations.md)
Considérations relatives au réseau des ressources : lors de la gestion du  [!DNL Experience Manager] déploiement, il est important de comprendre la topologie du réseau pour comprendre les performances du réseau, identifier les goulots d’étranglement et décrire l’expérience utilisateur attendue. Le document Remarques sur le réseau d’Assets aborde les considérations relatives au réseau lors de la conception de votre déploiement de ressources [!DNL Experience Manager].
* [](assets-monitoring-best-practices.md)
Guide de surveillance des ressources : une fois votre  [!DNL Experience Manager] déploiement déployé, vous devez surveiller certaines tâches, ainsi que le système en général, pour garantir l’intégrité du système et l’efficacité des opérations. Le Guide de surveillance comprend les bonnes pratiques pour contrôler les différents aspects de votre système.
* (Obsolète) [Guide de déchargement des ressources](assets-offloading-best-practices.md)
La gestion de fichiers volumineux et l’exécution de workflows dans [!DNL Experience Manager] Assets peuvent consommer une quantité considérable de ressources d’unité centrale, de mémoire et d’E/S. Le déchargement de ces tâches peut réduire les surcharges d’unité centrale, de mémoire et d’E/S. Le Guide de déchargement Assets inclut les cas d’utilisation recommandés et les meilleures pratiques pour le déchargement dans Assets.
* [[!DNL Experience Manager] Bonnes pratiques relatives aux applications de bureau](https://helpx.adobe.com/fr/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] L’appli de bureau associe votre solution de gestion des ressources numériques (DAM) à votre bureau afin que vous puissiez ouvrir les fichiers disponibles dans l’interface utilisateur  [!DNL Experience Manager] web directement sur le bureau. [!DNL Experience Manager] Le workflow convivial de l’appli de bureau est activé à l’aide de la technologie de partage réseau fournie par les systèmes d’exploitation de bureau. Ce guide explique les fonctionnalités clés et l’utilisation recommandée de l’appli de bureau [!DNL Experience Manager].
* [[!DNL Experience Manager] Bonnes ](aem-cc-integration-best-practices.md)
pratiques d’intégration et de Creative CloudVous pouvez intégrer votre  [!DNL Experience Manager] déploiement à Creative Cloud de plusieurs façons. En suivant les bonnes pratiques pour simplifier votre intégration et vos workflows de transfert des ressources, vous bénéficiez d’une efficacité maximale. Ce guide comprend les bonnes pratiques relatives à l’intégration de [!DNL Experience Manager] ressources à Adobe Creative Cloud.
* (Obsolète) [[!DNL Experience Manager] vers les bonnes pratiques de partage de dossier Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Vous pouvez configurer [!DNL Experience Manager] pour permettre aux utilisateurs de la gestion des ressources numériques de partager des dossiers avec les utilisateurs Creative Cloud afin qu’ils soient disponibles sous forme de dossiers partagés dans le service Ressources du Creative Cloud. La fonctionnalité peut être utilisée pour échanger des fichiers entre les équipes créatives et les utilisateurs DAM. Ce guide explique les bonnes pratiques à suivre pour utiliser la fonction de partage de dossiers [!DNL Experience Manager] vers Creative Cloud.
