---
title: Tâches de déchargement
seo-title: Offloading Jobs
description: Découvrez comment configurer et utiliser les instances AEM dans une topologie afin d’exécuter des types de traitement spécifiques.
seo-description: Learn how to configure and use AEM instances in a topology in order to perform specific types of processing.
uuid: e971d403-dfd2-471f-b23d-a67e35f1ed88
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 370151df-3b8e-41aa-b586-5c21ecb55ffe
feature: Configuring
exl-id: b10bf1b6-0360-45ca-b1aa-f4184cbfb5c0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2782'
ht-degree: 83%

---

# Tâches de déchargement{#offloading-jobs}

## Présentation {#introduction}

Le déchargement permet de répartir le traitement des tâches entre les instances d’Experience Manager dans une topologie. Avec le déchargement, vous pouvez utiliser des instances spécifiques d’Experience Manager pour exécuter des types de traitement spécifiques. Le traitement spécialisé permet d’optimiser l’utilisation des ressources disponibles sur le serveur.

Le déchargement est basé sur les fonctionnalités [Apache Sling Discovery](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html) et Sling JobManager. Pour utiliser le déchargement, ajoutez des clusters Experience Manager à une topologie, puis identifiez les rubriques de tâche devant être traitées par le cluster. Les clusters sont composés d’une ou de plusieurs instances Experience Manager, de sorte qu’une instance unique soit considérée comme un cluster.

Pour plus d’informations sur l’ajout d’instances à une topologie, voir [Administration des topologies](/help/sites-deploying/offloading.md#administering-topologies).

### Distribution des tâches {#job-distribution}

SlingJobManager et JobConsumer permettent la création de tâches qui sont traitées dans une topologie :

* JobManager : un service qui crée des tâches pour des rubriques spécifiques.
* JobConsumer : un service qui exécute les tâches d’une ou de plusieurs rubriques. Plusieurs services JobConsumer peuvent être enregistrés dans la même rubrique.

Lorsque JobManager crée une tâche, la structure de déchargement sélectionne un cluster Experience Manager dans la topologie pour exécuter la tâche :

* Le cluster doit inclure une ou plusieurs instances exécutant un JobConsumer enregistré pour la rubrique de tâche.
* La rubrique doit être activée pour au moins une instance du cluster.

Voir [Configuration de la consommation de rubrique](/help/sites-deploying/offloading.md#configuring-topic-consumption) pour plus de détails sur l’amélioration de la distribution des tâches.

![chlimage_1-109](assets/chlimage_1-109.png)

Lorsque la structure de déchargement sélectionne un cluster pour effectuer une tâche et que ce cluster est composé de plusieurs instances, Sling Distribution détermine quelle instance du cluster exécute la tâche.

### Charges utiles de la tâche {#job-payloads}

La structure de déchargement prend en charge les charges utiles de la tâche qui associent des tâches aux ressources du référentiel. Les charges de la tâche sont utiles lorsque des tâches sont créées pour le traitement des ressources et que la tâche est déchargée sur un autre ordinateur.

Après la création d’une tâche, la charge utile n’a l’assurance que d’être située sur l’instance qui crée la tâche. En déchargeant la tâche, les agents de réplication garantissent que la charge est créée sur l’instance qui va consommer la tâche par la suite. Lorsque l’exécution d’une tâche est terminée, la réplication inverse entraîne la copie de la charge utile sur l’instance qui a créé la tâche.

## Administration des topologies {#administering-topologies}

Les topologies sont des clusters Experience Manager légèrement interconnectées qui participent au déchargement. Un cluster est composée d’une ou de plusieurs instances de serveur Experience Manager (une instance unique est considérée comme un cluster).

Chaque instance Experience Manager exécute les services liés au déchargement suivants :

* Service Discovery (service de recherche) : envoie les demandes à un connecteur de topologie pour rejoindre la topologie.
* Topology Connector (connecteur de topologie) : reçoit les demandes d’accès et accepte ou refuse chaque demande.

Le service de recherche de tous les membres du point de topologie pointe vers le connecteur de topologie de l’un des membres. Dans les sections qui suivent, ce membre est désigné sous le nom d’acteur principal.

![chlimage_1-110](assets/chlimage_1-110.png)

Chaque cluster de la topologie contient une instance qui est identifiée en tant que leader. Le leader du cluster interagit avec la topologie au nom des autres membres du cluster. Lorsque le leader quitte le cluster, un nouveau leader du cluster est automatiquement sélectionné.

### Affichage de la topologie {#viewing-the-topology}

Utilisez le navigateur de topologies pour explorer l’état de la topologie à laquelle l’instance d’Experience Manager participe. Le navigateur de topologies présente les clusters et les instances de la topologie.

Pour chaque cluster, vous voyez une liste des membres du cluster qui indique l’ordre dans lequel chaque membre a rejoint la cluster et quel membre est le leader. La propriété actuelle indique l’instance que vous êtes en train de gérer.

Pour chaque instance de cluster, vous pouvez voir plusieurs propriétés liées à la topologie :

* Liste autorisée de rubriques pour le consommateur de tâche de l’instance.
* Les points de terminaison exposés pour la connexion à la topologie.
* Les rubriques de tâche pour lesquelles l’instance est enregistrée pour le déchargement.
* Les rubriques de tâches que l’instance traite.

1. À l’aide de l’interface tactile, cliquez sur l’onglet Outils. ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Dans la zone Opérations Granite, cliquez sur Navigateur de déchargement.
1. Dans le panneau de navigation, cliquez sur Navigateur de topologies.

   Les clusters qui participent à la topologie s’affichent.

   ![chlimage_1-111](assets/chlimage_1-111.png)

1. Cliquez sur un cluster pour afficher la liste des instances du cluster et leur identifiant, leur état actuel et l’état du leader.
1. Cliquez sur l’identifiant d’une instance pour afficher des informations plus détaillées.

Vous pouvez également utiliser la console web pour afficher les informations de topologie. La console fournit des informations supplémentaires sur les clusters de topologie :

* Quelle instance est l’instance locale. 
* Les services Topology Connector que cette instance utilise pour se connecter à la topologie (sortie) et les services qui se connectent à cette instance (entrée).
* Historique des modifications des propriétés de la topologie et de l’instance.

Utilisez la procédure suivante pour ouvrir la page Topology Management de la console web :

1. Ouvrez la console web dans votre navigateur. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Cliquez sur Général > Gestion de la topologie. 

   ![chlimage_1-112](assets/chlimage_1-112.png)

### Configuration de l’appartenance de la topologie {#configuring-topology-membership}

Le service de recherche basé sur les ressources Apache Sling s’exécute sur chaque instance pour contrôler la façon dont les instances d’Experience Manager interagissent avec une topologie.

Le service de recherche (Discovery Service) envoie des demandes POST périodiques (heartbeats) aux services du connecteur de topologie (Topology Connector) pour établir et gérer les connexions avec une topologie. Le service Topology Connector conserve une liste autorisée d’adresses IP ou de noms d’hôte autorisés à rejoindre la topologie :

* Pour joindre une instance à une topologie, précisez l’URL du service Topology Connector du membre racine.
* Pour permettre à une instance de rejoindre une topologie, ajoutez-la à la liste autorisée du service Topology Connector du membre racine.

Utilisez la console web ou un nœud sling:OsgiConfig pour configurer les propriétés suivantes du service org.apache.sling.discovery.impt.Config :

<table> 
 <tbody> 
  <tr> 
   <th>Nom de la propriété</th> 
   <th>Nom OSGi</th> 
   <th>Description</th> 
   <th>Valeur par défaut</th> 
  </tr> 
  <tr> 
   <td>Délai d’expiration de pulsation (en secondes)</td> 
   <td>heartbeatTimeout</td> 
   <td>Durée, en secondes, d’attente d’une réponse de pulsation avant que l’instance ciblée ne soit considérée comme non disponible. </td> 
   <td>20</td> 
  </tr> 
  <tr> 
   <td>Intervalle de pulsation (en secondes)</td> 
   <td>heartbeatInterval</td> 
   <td>Durée, en secondes, entre les pulsations.</td> 
   <td>15</td> 
  </tr> 
  <tr> 
   <td>Délai minimal de l’événement (en secondes)</td> 
   <td>minEventDelay</td> 
   <td><p>Lorsqu’une modification se produit sur la topologie, le temps nécessaire pour retarder le changement d’état de TOPOLOGY_CHANGING à TOPOLOGY_CHANGED. Chaque modification qui se produit lorsque l’état est TOPOLOGY_CHANGING augmente ce délai. </p> <p>Ce délai empêche les écouteurs d’être submergés par les événements. </p> <p>Pour n’utiliser aucun délai, spécifiez 0 ou un chiffre négatif.</p> </td> 
   <td>3</td> 
  </tr> 
  <tr> 
   <td>URL de Topology Connector</td> 
   <td>topologyConnectorUrls</td> 
   <td>URL des services Topology Connector pour envoyer des messages de pulsation.</td> 
   <td>http://localhost:4502/libs/sling/topology/connector</td> 
  </tr> 
  <tr> 
   <td>Liste autorisée Topology Connector</td> 
   <td>topologyConnectorWhitelist</td> 
   <td>Liste d’adresses IP ou de noms d’hôtes autorisés par le service Topology Connector dans la topologie. </td> 
   <td><p>localhost</p> <p>127.0.0.1</p> </td> 
  </tr> 
  <tr> 
   <td>Nom du descripteur du référentiel</td> 
   <td>leaderElectionRepositoryDescriptor</td> 
   <td> </td> 
   <td>&lt;aucune valeur&gt;</td> 
  </tr> 
 </tbody> 
</table>

Utilisez la procédure suivante pour connecter une instance CQ au membre racine d’une topologie. La procédure indique une instance l’URL de Topology Connector du membre racine de la topologie. Exécutez cette procédure pour tous les membres de la topologie.

1. Ouvrez la console web dans votre navigateur. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Cliquez sur Général > Gestion de la topologie.
1. Cliquez sur Configurer Discovery Service (le service de recherche). 
1. Ajoutez un élément à la propriété des URL de Topology Connector, puis spécifiez l’URL du service Topology Connector du membre racine de la topologie. L’URL se présente sous la forme https://rootservername:4502/libs/sling/topology/connector.

Effectuez la procédure suivante sur le membre racine de la topologie. La procédure ajoute les noms des autres membres de la topologie à sa liste autorisée Discovery Service.

1. Ouvrez la console web dans votre navigateur. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Cliquez sur Général > Gestion de la topologie.
1. Cliquez sur Configurer Discovery Service (le service de recherche). 
1. Pour chaque membre de la topologie, ajoutez un élément à la propriété de liste autorisée Topology Connector, puis spécifiez le nom d’hôte ou l’adresse IP du membre de la topologie.

## Configuration de la consommation de rubrique {#configuring-topic-consumption}

Utiliser le navigateur de déchargement pour configurer la consommation de rubrique pour les instances Experience Manager dans la topologie. Pour chaque instance, vous pouvez spécifier les rubriques qu’elle consomme. Par exemple, pour configurer votre topologie de sorte qu’une seule instance consomme les rubriques d’un type spécifique, désactivez la rubrique pour toutes les instances sauf une. 

Les tâches sont réparties entre les instances ayant la rubrique associée activée à l’aide de la logique circulaire.

1. À l’aide de l’interface tactile, cliquez sur l’onglet Outils. ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Dans la zone Opérations Granite, cliquez sur Navigateur de déchargement.
1. Dans le panneau de navigation, cliquez sur Navigateur de déchargement.

   Les rubriques de déchargement et les instances de serveur qui peuvent utiliser les rubriques s’affichent.

   ![chlimage_1-113](assets/chlimage_1-113.png)

1. Pour désactiver la consommation d’une rubrique pour une instance, au-dessous du nom de la rubrique, cliquez sur Désactiver en regard de l’instance.
1. Pour configurer toutes les consommations de rubrique pour une instance, cliquez sur l’identificateur de l’instance au-dessous d’une rubrique.

   ![chlimage_1-114](assets/chlimage_1-114.png)

1. Cliquez sur l’un des boutons suivants à côté d’une rubrique pour configurer le comportement de consommation pour une instance, puis cliquez sur enregistrer :

   * Activé : cette instance consomme les tâches de cette rubrique. 
   * Désactivé : cette instance ne consomme pas les tâches de cette rubrique.
   * Exclusif : cette instance consomme uniquement les tâches de cette rubrique.

   **Remarque :** Lorsque vous sélectionnez Exclusif pour une rubrique, toutes les autres rubriques sont automatiquement réglées sur Désactivé.

### Consommateurs de tâches installés {#installed-job-consumers}

Plusieurs implémentations de JobConsumer sont installées avec Experience Manager. Les rubriques auxquelles ces JobConsumers sont inscrits sont affichées dans le navigateur de déchargement. Les rubriques supplémentaires qui s’affichent sont celles que les JobConsumers personnalisés ont enregistrées. Le tableau ci-dessous décrit les JobConsumers par défaut.

| Rubrique de tâche | PID de service | Description |
|---|---|---|
| / | org.apache.sling.event.impl.jobs.deprecated.EventAdminBridge | Installé avec Apache Sling. Tâches de traitement générées par l’administrateur d’événements OSGi, à des fins de rétrocompatibilité. |
| com/day/cq/replication/job/&amp;ast; | com.day.cq.replication.impl.AgentManagerImpl | Un agent de réplication qui réplique les charges utiles de la tâche. |
| com/adobe/granite/workflow/offloading | com.adobe.granite.workflow.core.offloading.WorkflowOffloadingJobConsumer | Traite les tâches que le workflow Déchargeur de ressources de mise à jour de gestion des actifs numériques génère. |

### Désactivation et activation des rubriques pour une instance {#disabling-and-enabling-topics-for-an-instance}

Le service Apache Sling Job Consumer Manager fournit les propriétés de liste autorisée et de liste bloquée des rubriques. Configurez ces propriétés pour activer ou désactiver le traitement de rubriques spécifiques sur une instance Experience Manager.

**Remarque :** Si l’instance appartient à une topologie, vous pouvez également utiliser le navigateur de déchargement sur tout ordinateur de la topologie pour activer ou désactiver les rubriques.

La logique qui crée la liste des rubriques activées permet d’abord toutes les rubriques qui se trouvent dans la liste autorisée, puis supprime les rubriques qui se trouvent sur la liste bloquée. Par défaut, toutes les rubriques sont activées (la valeur de la liste autorisée est `*`) et aucune rubrique n’est désactivée (la liste bloquée n’a aucune valeur).

Utilisez le console web ou le nœud `sling:OsgiConfig` pour configurer les propriétés suivantes. Pour les nœuds `sling:OsgiConfig`, le paramètre PID du service Job Consumer Manager est org.apache.sling.event.impl.jobs.JobConsumerManager.

| Nom de propriété dans la console web | ID OSGi | Description |
|---|---|---|
| Liste autorisée de rubrique | job.consumermanager.whitelist | Liste de rubriques traitées par le service JobManager local. La valeur par défaut de &amp;ast; entraîne l’envoi de toutes les rubriques au service TopicConsumer enregistré. |
| Liste bloquée de rubrique | job.consumermanager.blacklist | Liste de rubriques que le service JobManager local ne traite pas. |

## Création des agents de réplication pour le déchargement {#creating-replication-agents-for-offloading}

La structure de déchargement utilise la réplication pour transférer des ressources entre l’auteur et le programme de traitement. La structure de déchargement crée automatiquement des agents de réplication lorsque les instances rejoignent la topologie. Les agents sont créés avec des valeurs par défaut. Vous devez modifier manuellement le mot de passe que les agents utilisent pour l’authentification. 

>[!CAUTION]
>
>Un problème connu avec les agents de réplication générés automatiquement est le fait que vous devez créer manuellement de nouveaux agents de réplication. Suivez la procédure décrite dans [Problèmes concernant l’utilisation des agents de réplication générés automatiquement](/help/sites-deploying/offloading.md#problems-using-the-automatically-generated-replication-agents) avant de créer les agents pour le déchargement.

Créez des agents de réplication qui transportent les charges utiles des tâches entre les instances pour le déchargement. Les illustrations suivantes présentent les agents nécessaires pour le déchargement de l’auteur vers une instance de travail. L’auteur possède un identifiant Sling de 1 et l’instance de travail un identifiant Sling de 2 :

![chlimage_1-115](assets/chlimage_1-115.png)

Cette configuration nécessite les trois agents suivants :

1. Un agent sortant sur l’instance d’auteur qui effectue la réplication vers l’instance de travail.
1. Un agent inverse sur l’instance d’auteur qui sort du dossier d’envoi sur l’instance de travail.
1. Un agent d’envoi sur l’instance de travail.

Ce modèle de réplication est similaire à celui utilisé entre les instances d’auteur et de publication. Toutefois, dans le cas du déchargement, toutes les instances impliquées sont des instances de création.

>[!NOTE]
>
>La structure de déchargement utilise la topologie pour obtenir les adresses IP des instances de déchargement. La structure crée alors automatiquement des agents de réplication en fonction de ces adresses IP. Si les adresses IP des instances de déchargement changent ultérieurement, la modification se propage automatiquement sur la topologie après le redémarrage de l’instance. Toutefois, la structure de déchargement ne met pas automatiquement à jour les agents de réplication pour refléter les nouvelles adresses IP. Pour éviter cette situation, utilisez des adresses IP fixes pour toutes les instances de la topologie.

### Nommage des agents de réplication pour le déchargement {#naming-the-replication-agents-for-offloading}

Utilisez un format spécifique pour la variable ***Nom*** des agents de réplication, de sorte que la structure de déchargement utilise automatiquement l’agent correct pour des instances de programme de travail spécifiques.

**Nommer un agent sortant sur l’instance d’auteur :** 

`offloading_<slingid>`où `<slingid>` est l’identifiant Sling de l’instance de travail.

Exemple : `offloading_f5c8494a-4220-49b8-b079-360a72f71559`

**Nommer l’agent inverse sur l’instance d’auteur :** 

`offloading_reverse_<slingid>`où `<slingid>` est l’identifiant Sling de l’instance de travail.

Exemple : `offloading_reverse_f5c8494a-4220-49b8-b079-360a72f71559`

**Nommer le dossier d’envoi sur l’instance de travail :**

`offloading_outbox`

### Création de l’agent sortant {#creating-the-outgoing-agent}

1. Créez un **agent de réplication** sur l’auteur. (Voir la [documentation sur les agents de réplication](/help/sites-deploying/replication.md)). Spécifiez les **Titre**. Le **Nom** doit respecter la convention d’affectation des noms.
1. Créez un agent en utilisant les propriétés suivantes :

   | Propriété | Valeur |
   |---|---|
   | Paramètres > Type de sérialisation | Valeur par défaut |
   | Transport >URI de transport | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Transport > Utilisateur de transport | Utilisateur de réplication sur l’instance cible |
   | Transport > Mot de passe de transport | Mot de passe de l’utilisateur de réplication sur l’instance cible |
   | Extension > Méthode HTTP | POST |
   | Triggers > Ignorer la valeur par défaut | True |

### Création de l’agent inverse {#creating-the-reverse-agent}

1. Créez un **Agent de réplication inverse** sur l’auteur. (Voir la [documentation sur les agents de réplication](/help/sites-deploying/replication.md).) Spécifiez les **Titre**. Le **Nom** doit respecter la convention d’affectation des noms.
1. Créez un agent en utilisant les propriétés suivantes :

   | Propriété | Valeur |
   |---|---|
   | Paramètres > Type de sérialisation | Valeur par défaut |
   | Transport >URI de transport | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Transport > Utilisateur de transport | Utilisateur de réplication sur l’instance cible |
   | Transport > Mot de passe de transport | Mot de passe de l’utilisateur de réplication sur l’instance cible |
   | Extension > Méthode HTTP | GET |

### Création de l’agent de dossier d’envoi {#creating-the-outbox-agent}

1. Créez un **Agent de réplication** sur l’instance de travail. (Voir la [documentation sur les agents de réplication](/help/sites-deploying/replication.md).) Spécifiez les **Titre**. Le **Nom** must `offloading_outbox`.
1. Créez l’agent en utilisant les propriétés suivantes.

   | Propriété | Valeur |
   |---|---|
   | Paramètres > Type de sérialisation | Valeur par défaut |
   | Transport >URI de transport | repo://var/replication/outbox |
   | Déclencheur > Ignorer la valeur par défaut | True |

###  Recherche de l’identifiant Sling {#finding-the-sling-id}

Obtenez l’identifiant Sling d’une instance Experience Manager en utilisant l’une des méthodes suivantes :

* Ouvrez la console web et, dans les paramètres Sling, recherchez la valeur de la propriété Sling ID ([http://localhost:4502/system/console/status-slingsettings](http://localhost:4502/system/console/status-slingsettings)). Cette méthode est utile si l’instance ne fait pas encore partie de la topologie.
* Utilisez le navigateur de topologies si l’instance fait déjà partie de la topologie.

## Déchargement du traitement des ressources de gestion des actifs numériques {#offloading-the-processing-of-dam-assets}

Configurez les instances d’une topologie de sorte que les instances spécifiques exécutent le traitement en arrière-plan des ressources ajoutées ou mises à jour dans la gestion des actifs numériques.

Par défaut, Experience Manager exécute le workflow Ressource de mise à niveau de gestion des actifs numériques lorsqu’une ressource de gestion des actifs numériques est modifiée ou ajoutée à la gestion des actifs numériques. Modifiez le comportement par défaut, de sorte qu’Experience Manager exécute à la place le workflow Déchargement des ressources de mise à niveau de gestion des actifs numériques. Ce workflow génère une tâche JobManager comportant une rubrique de `com/adobe/granite/workflow/offloading`. Ensuite, configurez la topologie de sorte que la tâche soit déchargée sur un programme de travail dédié.

>[!CAUTION]
>
>Aucun workflow ne doit être transitoire lorsqu’il est utilisé avec le déchargement de workflow. Par exemple, le workflow Ressource de mise à jour de gestion des actifs numériques ne doit pas être transitoire lorsqu’il est utilisé pour le déchargement des ressources. Pour définir/annuler la définition de l’indicateur transitoire sur un workflow, voir [Processus transitoires](/help/assets/performance-tuning-guidelines.md#workflows).

La procédure suivante part des fonctionnalités suivantes pour la topologie de déchargement :

* Une ou plusieurs instances Experience Manager correspondent à des instances de création avec lesquelles les utilisateurs interagissent pour l’ajout ou la mise à jour des ressources de gestion des actifs numériques.
* Les utilisateurs ne communiquent pas directement avec une ou plusieurs instances Experience Manager traitant les ressources de gestion des actifs numériques. Ces instances sont dédiées au traitement en arrière-plan des ressources de gestion des actifs numériques. 

1. Sur chaque instance Experience Manager, configurez Discovery Service (service de recherche) afin qu’il indique le Topography Connector (connecteur de topographie) racine. (Voir [Configuration de l’appartenance à une topologie](#title4).)
1. Configurez la racine Topography Connector afin que les instances de connexion soient affichées sur la liste autorisée.
1. Ouvrez le navigateur de déchargement et désactivez l’option `com/adobe/granite/workflow/offloading` sur les instances avec lesquelles les utilisateurs interagissent pour charger ou modifier des ressources DAM.

   ![chlimage_1-116](assets/chlimage_1-116.png)

1. Sur chaque instance dont les utilisateurs se servent dans le cadre de leurs activités d’interaction pour transférer ou modifier des ressources de gestion des actifs numériques, configurez des lanceurs de workflow pour utiliser le workflow Déchargement des ressources de mise à jour de gestion des actifs numériques :

   1. Ouvrez la console Workflows.
   1. Cliquez sur l’onglet Lanceur.
   1. Repérez les deux configurations de lanceur qui exécutent le workflow Ressource de mise à jour de gestion des actifs numériques. Un type d’événement de configuration du lanceur est créé par nœud, alors que l’autre type est modifié par nœud.
   1. Modifiez les deux types d’événement de sorte qu’ils exécutent le workflow Déchargement des ressources de mise à jour de gestion des actifs numériques. (Pour plus d’informations sur les configurations du lanceur, voir [Démarrage de workflow lorsque les nœuds changent](/help/sites-administering/workflows-starting.md).)

1. Sur les instances qui exécutent le traitement en arrière-plan des ressources de gestion des actifs numériques, désactivez les lanceurs de workflow qui exécutent le workflow Ressource de mise à jour de gestion des actifs numériques.

## Informations complémentaires {#further-reading}

En plus des informations présentées sur cette page, vous pouvez également lire ce qui suit :

* Pour plus d’informations sur l’utilisation des API Java pour créer des tâches et des consommateurs de tâches, voir [Création et utilisation de tâches pour le déchargement](/help/sites-developing/dev-offloading.md).
* Pour découvrir les directives générales et les meilleures pratiques relatives au déchargement de ressources, voir [Directives générales et meilleures pratiques relatives au déchargement de ressources](/help/assets/assets-offloading-best-practices.md#general-guidance-and-best-practices-for-asset-offloading).
* Pour savoir comment désactiver la création automatique des agents de déchargement, voir [Désactivation de la gestion automatique des agents](/help/assets/assets-offloading-best-practices.md#turning-off-automatic-agent-management).
