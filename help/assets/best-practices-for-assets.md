---
title: Bonnes pratiques pour gérer les ressources à l’aide d’AEM
description: Identifiez et respectez les bonnes pratiques qui améliorent la stabilité et les performances du système en charge, selon les [!DNL Experience Manager] Déploiement des ressources et fonctionnalités utilisées pour ingérer et traiter des ressources.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: d750c852b6367d753d18be57c8910bf5671fd5e8
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 16%

---

# Bonnes pratiques relatives aux [!DNL Experience Manager] Ressources {#best-practices-for-assets}

Adobe Experience Manager Assets est un élément essentiel de la diffusion d’expériences marketing numériques de haute qualité qui contribuent à la réalisation des objectifs de l’entreprise en augmentant la vitesse de votre contenu. Si vous utilisez un grand nombre de ressources dans [!DNL Assets] ou charger régulièrement/régulièrement de nombreuses ressources, y compris des vidéos et des médias dynamiques, l’optimisation de votre expérience de gestion des ressources numériques est essentielle à l’efficacité du système.

Selon le positionnement [!DNL Assets] pour votre entreprise et les fonctionnalités que vous utilisez pour l’ingestion de ressources, la génération de rendus et l’extraction de métadonnées, l’identification et le respect des bonnes pratiques dans différents domaines améliorent considérablement la stabilité et les performances du système en cas de charge.

Après avoir consulté les guides suivants, vous disposerez des connaissances et des outils nécessaires pour créer et gérer un système de gestion des actifs d’entreprise qui répond à vos besoins.

* [Guide d’optimisation des performances des ressources](performance-tuning-guidelines.md)
Inclut un ensemble de bonnes pratiques qui peuvent être suivies à tout moment dans votre mise en oeuvre, même après activation, pour vous assurer que vous tirez pleinement parti de votre système.
* [Guide de dimensionnement des ressources](assets-sizing-guide.md)
Lors de l’établissement d’estimations pour une mise en oeuvre d’Assets, il est important de s’assurer qu’il existe suffisamment de ressources disponibles en termes de stockage des ressources, de processeur, de mémoire, d’E/S et de débit réseau. Pour dimensionner un grand nombre de ces éléments, il est nécessaire de connaître le nombre de ressources à charger dans le système. Ce guide comprend les bonnes pratiques qui permettent de déterminer des mesures efficaces pour estimer l’infrastructure et les ressources nécessaires au déploiement. [!DNL Experience Manager] Ressources ainsi qu’un outil de dimensionnement.
* [Guide de migration des ressources](assets-migration-guide.md)
Si vous souhaitez migrer des ressources de votre système hérité vers [!DNL Experience Manager] Ressources, plusieurs étapes sont nécessaires pour rationaliser le processus de migration. Le guide de migration inclut les bonnes pratiques relatives aux tâches que vous effectuez pour importer les ressources dans [!DNL Experience Manager] par phase. Cela inclut l’application de métadonnées, la génération de rendus et l’activation des ressources pour le déploiement de publication.
* [Considérations sur le réseau d’Assets](assets-network-considerations.md)
Lors de la gestion [!DNL Experience Manager] Il est important de bien comprendre la topologie du réseau pour comprendre les performances du réseau, identifier les goulots d’étranglement et décrire l’expérience utilisateur attendue. Le document Remarques sur le réseau d’Assets décrit les considérations à prendre en compte pour le réseau lors de la conception de votre [!DNL Experience Manager] Déploiement des ressources.
* [Guide de surveillance des ressources](assets-monitoring-best-practices.md)
Après votre [!DNL Experience Manager] Le déploiement est déployé. Vous devez surveiller certaines tâches et le système en général pour garantir l’intégrité du système et l’efficacité des opérations. Le Guide de surveillance comprend les bonnes pratiques pour contrôler les différents aspects de votre système.
* (Obsolète) [Guide de déchargement des ressources](assets-offloading-best-practices.md)
Gestion des fichiers volumineux et exécution des workflows dans [!DNL Experience Manager] Les ressources peuvent consommer une quantité considérable de ressources de processeur, de mémoire et d’E/S. Le déchargement de ces tâches peut réduire les surcharges d’unité centrale, de mémoire et d’E/S. Le Guide de déchargement Assets inclut les cas d’utilisation recommandés et les meilleures pratiques pour le déchargement dans Assets.
* [[!DNL Experience Manager] Bonnes pratiques relatives aux applications de bureau](https://helpx.adobe.com/fr/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] L’appli de bureau associe votre solution de gestion des ressources numériques (DAM) à votre bureau afin que vous puissiez ouvrir les fichiers disponibles dans la [!DNL Experience Manager] interface utilisateur web directement sur le bureau. [!DNL Experience Manager] Le workflow convivial de l’appli de bureau est activé à l’aide de la technologie de partage réseau fournie par les systèmes d’exploitation de bureau. Ce guide explique les principales fonctionnalités et l’utilisation recommandée de [!DNL Experience Manager] application de bureau .
* [[!DNL Experience Manager] Bonnes pratiques d’intégration et Creative Cloud](aem-cc-integration-best-practices.md)
Vous pouvez intégrer votre [!DNL Experience Manager] déploiement avec Creative Cloud de plusieurs manières. En suivant les bonnes pratiques pour simplifier votre intégration et vos workflows de transfert des ressources, vous bénéficiez d’une efficacité maximale. Ce guide comprend les bonnes pratiques en matière d’intégration [!DNL Experience Manager] Ressources avec Adobe Creative Cloud.
* (Obsolète) [[!DNL Experience Manager] vers les bonnes pratiques de partage de dossiers Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Vous pouvez configurer [!DNL Experience Manager] pour permettre aux utilisateurs de la gestion des actifs numériques de partager des dossiers avec des utilisateurs Creative Cloud, afin qu’ils soient disponibles sous forme de dossiers partagés dans le service Ressources du Creative Cloud. La fonctionnalité peut être utilisée pour échanger des fichiers entre les équipes créatives et les utilisateurs DAM. Ce guide explique les bonnes pratiques à suivre pour utiliser la variable [!DNL Experience Manager] vers la fonction de partage de dossiers de Creative Cloud.
