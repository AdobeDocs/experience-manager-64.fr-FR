---
title: Bonnes pratiques de déchargement dans Assets
description: Cas d’utilisation recommandés et bonnes pratiques pour le déchargement des workflows d’assimilation et de réplication de ressources dans [!DNL Experience Manager] Ressources.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 3ecc8988-add1-47d5-80b4-984beb4d8dab
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1841'
ht-degree: 1%

---

# Bonnes pratiques de déchargement dans Assets {#assets-offloading-best-practices}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!WARNING]
>
>Cette fonctionnalité est obsolète. [!DNL Experience Manager] À compter de la version 6.4, et est supprimé dans [!DNL Experience Manager] 6.5. Planifiez en conséquence.

La gestion de fichiers volumineux et l’exécution de workflows dans Adobe Experience Manager Assets peuvent consommer une quantité considérable de ressources d’unité centrale, de mémoire et d’E/S. En particulier, la taille des ressources, les workflows, le nombre d’utilisateurs et la fréquence d’assimilation des ressources peuvent affecter les performances globales du système. Les opérations les plus gourmandes en ressources comprennent l’ingestion de ressources et les workflows de réplication. L’utilisation intensive de ces workflows sur une seule instance de création peut nuire à l’efficacité de la création.

Le déchargement de ces tâches vers des instances de travail dédiées peut réduire les surcharges de processeur, de mémoire et d’E/S. En général, l’idée derrière le déchargement est de distribuer des tâches qui consomment des ressources intensives de processeur/mémoire/E/S aux instances de travail dédiées. Les sections suivantes incluent des cas d’utilisation recommandés pour le déchargement des ressources.

## [!DNL Experience Manager Assets] Déchargement {#aem-assets-offloading}

[!DNL Experience Manager] Assets met en oeuvre une extension de workflow native spécifique aux ressources pour le déchargement. Il repose sur l’extension de workflow générique fournie par la structure de déchargement, mais inclut des fonctionnalités supplémentaires spécifiques aux ressources dans l’implémentation. L’objectif du déchargement des ressources est d’exécuter efficacement le workflow Ressources de mise à jour de gestion des actifs numériques sur une ressource chargée. Le déchargement des ressources vous permet de mieux contrôler les workflows d’ingestion.

## [!DNL Experience Manager] Composants de déchargement des ressources {#aem-assets-offloading-components}

Le diagramme suivant illustre les principaux composants du processus de déchargement des ressources :

![chlimage_1-55](assets/chlimage_1-55.png)

### Workflow de déchargement des ressources de mise à jour de gestion des actifs numériques {#dam-update-asset-offloading-workflow}

Le workflow Déchargement des ressources de mise à jour de gestion des actifs numériques s’exécute sur le Principal serveur (d’auteur) sur lequel l’utilisateur charge les ressources. Ce workflow est déclenché par un lanceur de workflow ordinaire. Au lieu de traiter la ressource chargée, ce workflow de déchargement crée une tâche à l’aide de la rubrique . *com/adobe/granite/workflow/offloading*. Le workflow de déchargement ajoute le nom du workflow cible : le workflow Ressources de mise à jour de gestion des actifs numériques dans ce cas, et le chemin d’accès de la ressource à la charge utile de la tâche. Après la création de la tâche de déchargement, le workflow de déchargement sur l’instance Principale attend l’exécution de la tâche de déchargement.

### Job manager {#job-manager}

Le gestionnaire des tâches distribue les nouvelles tâches aux instances de travail. Lors de la conception du mécanisme de distribution, il est important de prendre en compte l’activation des rubriques. Les tâches ne peuvent être affectées qu’aux instances où la rubrique de la tâche est activée. Désactivation de la rubrique `com/adobe/granite/workflow/offloading` sur la Principale et activez-la sur le programme de travail pour vous assurer que la tâche est affectée au programme de travail.

### [!DNL Experience Manager] offloading {#aem-offloading}

La structure de déchargement identifie les tâches de déchargement de workflow affectées aux instances de programme de travail et utilise la réplication pour les transporter physiquement, y compris leur charge utile (par exemple, les images à ingérer), vers les programmes de travail.

### Client de tâche de déchargement de workflow {#workflow-offloading-job-consumer}

Une fois qu’une tâche est écrite sur le programme de travail, le gestionnaire de tâches appelle le consommateur de tâche responsable de la *com/adobe/granite/workflow/offloading* rubrique. Le consommateur de tâche exécute ensuite le workflow Ressource de mise à jour de gestion des actifs numériques sur la ressource.

## Topologie Sling {#sling-topology}

Groupes de topologie Sling [!DNL Experience Manager] et leur permet de se connaître les uns les autres, indépendamment de la persistance sous-jacente. Cette caractéristique de la topologie Sling permet de créer des topologies pour les scénarios non organisés en grappes, en grappes et mixtes. Une instance peut exposer les propriétés à l’ensemble de la topologie. La structure fournit des rappels pour écouter les modifications de la topologie (instances et propriétés). La topologie Sling constitue la base des tâches distribuées Sling.

### Tâches distribuées Sling {#sling-distributed-jobs}

Les tâches distribuées Sling facilitent la distribution des tâches entre un ensemble d’instances qui sont membres de la topologie. Les tâches Sling reposent sur l’idée de fonctionnalités. Une tâche est définie par sa rubrique de tâche. Pour exécuter une tâche, une instance doit fournir un consommateur de tâche pour une rubrique de tâche spécifique. La rubrique de tâche est le pilote principal du mécanisme de distribution.

Les tâches sont uniquement distribuées aux instances qui fournissent un consommateur de tâche pour la rubrique. En activant/désactivant les consommateurs de tâche sur une instance, vous pouvez définir les fonctionnalités d’une instance et influencer le mécanisme de distribution. Les consommateurs de tâche disponibles d’une instance sont diffusés sur l’ensemble de la topologie.

Dans ce contexte, le terme distribution désigne l’affectation d’une tâche à une instance spécifique qui fournit un consommateur de tâche. L’affectation à une instance est stockée dans le référentiel. En d’autres termes, les tâches distribuées Sling peuvent être affectées par défaut à n’importe quelle instance de la topologie. Cependant, d’autres tâches ne peuvent être exécutées que par des instances qui partagent le même référentiel. Cela signifie que ces tâches ne peuvent être exécutées que par des instances faisant partie du même cluster. Les tâches affectées à des instances d’un autre cluster ne sont pas exécutées.

### Structure de déchargement Granite {#granite-offloading-framework}

La structure de déchargement Granite complète la distribution des tâches Sling pour exécuter les tâches affectées à des instances non clusterisées. Il n’effectue aucune distribution (affectation d’instance). Cependant, il identifie les tâches Sling qui ont été distribuées à des instances non clusterisées et les transporte vers l’instance cible pour exécution. Actuellement, le déchargement utilise la réplication pour effectuer ce transport de tâche. Pour exécuter une tâche, le déchargement définit l’entrée et la sortie, qui sont ensuite combinées à la tâche pour créer la charge utile de la tâche.

Les tâches distribuées Sling fournissent la structure de tâche et de distribution. Le déchargement Granite prend uniquement en charge le transport pour le cas particulier où les tâches sont distribuées à des instances non clusterisées.

En plus du transport, la structure de déchargement fournit une extension pour le moteur de workflow. Il permet à la structure de créer des tâches distribuées dans le cadre d’un workflow et d’attendre leur fin avant que le workflow ne progresse. Elle est implémentée à l’aide de l’API de l’étape externe de workflow du moteur de workflow. L’une des extensions facilite la distribution générique des workflows. La distribution d’étapes de workflow uniques n’est pas prise en charge.

La structure de déchargement est également fournie avec une interface utilisateur pour visualiser et contrôler l’activation des rubriques de tâche sur l’ensemble de la topologie. L’interface utilisateur vous permet de configurer facilement l’activation des rubriques des tâches distribuées Sling. Vous pouvez également configurer le déchargement sans l’interface utilisateur.

## Conseils généraux et bonnes pratiques relatives au déchargement des ressources {#general-guidance-and-best-practices-for-asset-offloading}

Chaque mise en oeuvre est unique et, en tant que telle, il n’existe pas de configuration de déchargement universelle. Les sections suivantes fournissent des conseils et des bonnes pratiques concernant le déchargement de l’ingestion de ressources.

Le déchargement des ressources impose également des surcharges sur le système, y compris des surcharges d’opération. Si vous rencontrez des problèmes avec la charge d’ingestion des ressources, Adobe vous recommande d’améliorer d’abord la configuration sans déchargement. Tenez compte des options suivantes avant de passer au déchargement des ressources :

* Évolutivité du matériel
* Optimisation des workflows
* Utilisation de workflows transitoires
* Limiter le nombre de coeurs utilisés pour les workflows

Si vous estimez que le déchargement des ressources est une approche appropriée, Adobe fournit les conseils suivants :

* Un déploiement basé sur TarMK est recommandé
* Le déchargement des ressources basé sur TarMK n’est pas conçu pour une mise à l’échelle horizontale étendue.
* S’assurer que les performances du réseau entre l’auteur et les travailleurs sont satisfaisantes

### Déploiement de déchargement des ressources recommandé {#recommended-assets-offloading-deployment}

Avec [!DNL Experience Manager] et Oak, il existe plusieurs scénarios de déploiement possibles. Pour le déchargement des ressources, un déploiement basé sur TarMK avec une banque de données partagée est recommandé. Le diagramme suivant décrit le déploiement recommandé :

![chlimage_1-56](assets/chlimage_1-56.png)

Pour plus d’informations sur la configuration d’une banque de données, voir [Configuration des entrepôts de noeuds et de données dans AEM](../sites-deploying/data-store-config.md).

### Désactivation de la gestion automatique des agents {#turning-off-automatic-agent-management}

Adobe recommande de désactiver la gestion automatique des agents, car elle ne prend pas en charge la réplication sans fichier binaire et peut prêter à confusion lors de la configuration d’une nouvelle topologie de déchargement. De plus, il ne prend pas automatiquement en charge le flux de réplication vers l’avant requis par la réplication sans fichier binaire.

1. Ouvrez Configuration Manager à partir de l’URL. `http://localhost:4502/system/console/configMgr`.
1. Ouvrez la configuration pour `OffloadingAgentManager` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`).
1. Désactivez la gestion automatique des agents.

### Utilisation de la réplication vers l’avant {#using-forward-replication}

Par défaut, le transport de déchargement utilise la réplication inverse pour extraire les ressources déchargées du programme de travail vers la Principale. Les agents de réplication inverse ne prennent pas en charge la réplication sans fichier binaire. Vous devez configurer le déchargement pour utiliser la réplication vers l’avant afin de repousser les ressources déchargées du programme de travail vers Principal.

1. Si vous migrez à partir de la configuration par défaut à l’aide de la réplication inverse, désactivez ou supprimez tous les agents nommés &quot; `offloading_outbox`&quot; et &quot; `offloading_reverse_*`&quot; sur Principal et worker, où &amp;ast; représente l’identifiant Sling de l’instance cible.
1. Sur chaque programme de travail, créez un agent de réplication vers l’avant pointant vers la Principale. La procédure est la même que la création d’agents de transfert de Principal à worker. Voir [Création d’agents de réplication pour le déchargement](../sites-deploying/offloading.md#creating-replication-agents-for-offloading) pour obtenir des instructions sur la configuration des agents de réplication de déchargement.
1. Ouvrir la configuration pour `OffloadingDefaultTransporter`  (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`).
1. Modification de la valeur de la propriété `default.transport.agent-to-master.prefix` de `offloading_reverse` to `offloading`.

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### Utilisation de la banque de données partagée et de la réplication sans binaires entre l’auteur et les programmes de travail  {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

L’utilisation de la réplication sans fichier binaire est recommandée pour réduire la surcharge de transport pour le déchargement des ressources. Pour savoir comment configurer une réplication sans fichier binaire pour une banque de données partagée, voir [Configuration des entrepôts de noeuds et de données dans AEM](/help/sites-deploying/data-store-config.md). La procédure n’est pas différente pour le déchargement des ressources, sauf qu’elle implique d’autres agents de réplication. Comme la réplication sans fichier binaire fonctionne uniquement avec les agents de réplication de transfert, vous devez également utiliser la réplication de transfert pour tous les agents de déchargement.

### Désactivation des packages de transport {#turning-off-transport-packages}

Par défaut, le déchargement crée un module de contenu qui contient la tâche de déchargement et la charge utile de la tâche (la ressource d’origine), et transporte ce module de déchargement unique à l’aide d’une seule requête de réplication. La création de ces modules de déchargement est contre-productive lors de l’utilisation d’une réplication sans fichier binaire, car les fichiers binaires sont à nouveau sérialisés dans le module lors de la création du module. L’utilisation de ces packages de transport peut être désactivée, ce qui entraîne le transport de la tâche de déchargement et de la charge utile dans plusieurs demandes de réplication, une pour chaque entrée de charge utile. De cette manière, l’avantage de la réplication sans fichier binaire peut être utilisé.

1. Ouvrez la configuration du composant de *OffloadingDefaultTransporter* component at [http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)
1. Désactivation de la propriété *Package de réplication (default.transport.contentpackage)*.

### Désactivation du transport du modèle de workflow {#disabling-the-transport-of-workflow-model}

Par défaut, la variable *Déchargement des ressources de mise à jour de gestion des actifs numériques* le workflow de déchargement ajoute le modèle de workflow pour appeler le programme de travail à la charge utile de la tâche. Parce que ce workflow suit le modèle d&#39;usine *Ressources de mise à jour de gestion des actifs numériques* par défaut, cette payload supplémentaire peut être supprimée.

Si le modèle de workflow est désactivé à partir de la charge utile de la tâche, veillez à distribuer les modifications au modèle de workflow référencé à l’aide d’autres outils, tels que le gestionnaire de modules.

Pour désactiver le transport du modèle de workflow, modifiez le workflow Déchargement des ressources de mise à jour de gestion des actifs numériques .

1. Ouvrez la console de processus à partir de [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).
1. Ouvrez l’onglet Modèles .
1. Ouvrez le modèle de workflow Déchargement des ressources de mise à jour de gestion des actifs numériques .
1. Ouvrez les propriétés de l’étape Déchargement du workflow de gestion des actifs numériques .
1. Ouvrez l’onglet Arguments et désélectionnez les options Ajouter un modèle à l’entrée et Ajouter un modèle à la sortie .
1. Enregistrez les modifications dans le modèle.

### Optimisation de l’intervalle d’interrogation {#optimizing-the-polling-interval}

Le déchargement des workflows est mis en oeuvre à l’aide d’un workflow externe sur la Principale, qui interroge la fin du workflow déchargé sur le programme de travail. L’intervalle d’interrogation par défaut pour les processus de workflow externes est de cinq secondes. Adobe recommande d’augmenter l’intervalle d’interrogation de l’étape de déchargement des ressources à au moins 15 secondes afin de réduire la surcharge de déchargement sur la Principale.

1. Ouvrez la console de processus à partir de [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).

1. Ouvrez l’onglet Modèles .
1. Ouvrez le modèle de workflow Déchargement des ressources de mise à jour de gestion des actifs numériques .
1. Ouvrez les propriétés de l’étape Déchargement du workflow de gestion des actifs numériques .
1. Ouvrez l’onglet Commons et ajustez la valeur de la propriété Period.
1. Enregistrez les modifications dans le modèle.

## Plus de ressources {#more-resources}

Ce document porte sur le déchargement des ressources. Voici une documentation supplémentaire sur le déchargement :

* [Tâches de déchargement](/help/sites-deploying/offloading.md)
* [Déchargeur de workflow de ressources](/help/sites-administering/workflow-offloader.md)
