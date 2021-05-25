---
title: Déchargeur de workflow de ressources
seo-title: Déchargeur de workflow de ressources
description: Familiarisez-vous avec le déchargeur de workflow de ressources.
seo-description: Familiarisez-vous avec le déchargeur de workflow de ressources.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
exl-id: 2ca8e786-042b-44f6-ac60-834eca64f79f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 31%

---

# Déchargeur de workflow de ressources{#assets-workflow-offloader}

Le déchargeur de workflow de ressources permet à plusieurs instances Adobe Experience Manager (AEM) Assets de réduire la charge de traitement sur l’instance principale. La charge de traitement est répartie entre l’instance principale et les différentes instances de déchargement (auxiliaires) que vous y ajoutez. La répartition de la charge de traitement des ressources augmente l’efficacité et la vitesse de traitement des ressources par AEM Assets. De plus, elle contribue à allouer des ressources dédiées pour traiter des ressources d’un type MIME particulier. Par exemple, vous pouvez réserver un nœud spécifique de votre topologie au traitement des ressources InDesign.

## Configuration de la topologie du déchargeur {#configure-offloader-topology}

Utilisez Configuration Manager pour ajouter l’URL de l’instance principale et les noms d’hôte des instances de déchargement pour les requêtes de connexion sur l’instance principale.

1. Appuyez/cliquez sur le logo AEM, puis sélectionnez **Outils** > **Opérations** > **Console web** pour ouvrir Configuration Manager.
1. Dans la console web, sélectionnez **Sling** > **Gestion de topologie**.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Dans la page Topology Management, appuyez/cliquez sur le lien **Configurer Discovery.Oak Service** .

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Dans la page Configuration du service de détection, spécifiez l’URL du connecteur pour l’instance principale dans le champ **URL du connecteur de topologie** .

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. Dans le champ **Liste autorisée Topology Connector** , spécifiez l’adresse IP ou les noms d’hôte des instances de déchargement autorisées à se connecter à l’instance principale. Appuyez/cliquez sur **Enregistrer**.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Pour afficher les instances de déchargement connectées à l’instance principale, sélectionnez **Tools** > **Deployment** > **Topology** et appuyez/cliquez sur la vue Cluster.

## Désactivation du déchargement  {#disable-offloading}

1. Appuyez/cliquez sur le logo AEM, puis sélectionnez **Outils** > **Déploiement** > **Déchargement**. La page **Navigateur de déchargement** affiche les rubriques et les instances de serveur qui peuvent utiliser les rubriques.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Désactivez la rubrique *com/adobe/granite/workflow/offloading* sur les instances principales avec lesquelles les utilisateurs interagissent pour charger ou modifier des ressources AEM.

   ![chlimage_1-49](assets/chlimage_1-49.png)

## Configuration des lanceurs de workflow sur l’instance principale {#configure-workflow-launchers-on-the-leader-instance}

Configurez les lanceurs de workflow pour utiliser le workflow **Déchargement des ressources de mise à jour de gestion des actifs numériques** sur l’instance principale au lieu du workflow **Ressource de mise à jour de gestion des actifs numériques** .

1. Appuyez/cliquez sur le logo AEM, puis sélectionnez **Outils** > **Workflow** > **Lanceurs** pour ouvrir la console **Lanceurs de workflow**.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Localisez les deux configurations du lanceur avec le type d’événement **Noeud créé** et **Noeud modifié** , respectivement, qui exécutent le workflow **Ressource de mise à jour de gestion des actifs numériques** .
1. Pour chaque configuration, cochez la case en regard de celle-ci et appuyez/cliquez sur l’icône **Afficher les propriétés** de la barre d’outils pour afficher la boîte de dialogue **Propriétés du lanceur**.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Dans la liste **Workflow**, sélectionnez **Déchargement des ressources de mise à jour de gestion des actifs numériques** et appuyez/cliquez sur **Enregistrer**.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. Appuyez/cliquez sur le logo AEM, puis sélectionnez **Outils** > **Processus** > **Modèles** pour ouvrir la page **Modèles de processus** .
1. Sélectionnez le workflow **Déchargement des ressources de mise à jour de gestion des actifs numériques**, puis appuyez/cliquez sur **Modifier** dans la barre d’outils pour afficher ses détails.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Affichez le menu contextuel de l’étape **Déchargement du workflow de gestion des actifs numériques**, puis sélectionnez **Modifier**. Vérifiez la saisie dans le champ **Rubrique de tâche** de l’onglet **Arguments génériques** de la boîte de dialogue de configuration.

   ![chlimage_1-54](assets/chlimage_1-54.png)

## Désactivation des lanceurs de workflow sur les instances de déchargement {#disable-the-workflow-launchers-on-the-offloader-instances}

Désactivez les lanceurs de workflow qui exécutent le workflow **Ressource de mise à jour de gestion des actifs numériques** sur l’instance principale.

1. Appuyez/cliquez sur le logo AEM, puis sélectionnez **Outils** > **Workflow** > **Lanceurs** pour ouvrir la console **Lanceurs de workflow**.

   ![chlimage_1-55](assets/chlimage_1-55.png)

1. Localisez les deux configurations du lanceur avec le type d’événement **Noeud créé** et **Noeud modifié** , respectivement, qui exécutent le workflow **Ressource de mise à jour de gestion des actifs numériques** .
1. Pour chaque configuration, cochez la case en regard de celle-ci et appuyez/cliquez sur l’icône **Afficher les propriétés** de la barre d’outils pour afficher la boîte de dialogue **Propriétés du lanceur**.

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. Dans la section **Activer **, faites glisser le curseur pour désactiver le lanceur de workflow, puis appuyez/cliquez sur **Enregistrer** pour le désactiver.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Téléchargez toute ressource de type image sur l’instance principale. Vérifiez les miniatures générées et réacheminées pour la ressource par l’instance déchargée.
