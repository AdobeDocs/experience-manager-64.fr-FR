---
title: Présentation d’AEM Communities
seo-title: AEM Communities Overview
description: Présentation des fonctionnalités et de la configuration d’AEM Communities
seo-description: An overview of AEM Communities features and setup
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 5%

---

# Présentation d’AEM Communities {#aem-communities-overview}

Adobe Experience Manager (AEM) Communities permet de créer rapidement un site de communauté local doté de performances et d’une gestion de sites améliorées, et qui encourage les visiteurs à devenir membres de la communauté.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Fonctions de communauté {#communities-features}

AEM Communities permet le développement d’une relation avec les visiteurs du site qui fournit des informations par le biais de blogs, de questions et réponses et de calendriers d’événements, tout en obtenant des informations par le biais de forums, de commentaires et d’autres contenus de la communauté, souvent appelés contenu généré par l’utilisateur.

En outre, AEM Communities permet la modération par les membres de confiance dans l’environnement de publication, la connexion sociale avec Twitter et Facebook, la traduction en ligne du contenu de la communauté, la création de groupes de communauté à partir du site de la communauté publié, la notation des badges d’attribution, le partage de fichiers, les notifications et les flux d’activités.

Les fonctionnalités de communauté peuvent être démontrées à l’aide de la fonction [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponible publiquement sur GitHub.com ou avec la nouvelle implémentation de référence We.Retail.

## Sites communautaires {#community-sites}

Un site communautaire est un site AEM créé à l’aide d’un assistant simple qui génère un site web avec de nombreuses fonctionnalités courantes pré-câblées dans le site.

Le [assistant de création de site](sites-console.md):

* Assemble les fonctionnalités du site, en fonction de la [modèle de site communautaire](sites.md) qui
   * Construit à partir de [fonctions de communauté](#community-functions)
   * Facultatif [groupes communautaires](#communitygroups) fonctionnalité
* Utilise les paramètres à configurer :
   * Modération
   * La connexion
   * Traduction
* Fournit les fonctionnalités essentielles :
   * Responsive design : Utilisations [Thèmes de Bootstrap twitter](https://getbootstrap.com)
   * Connexion : Auto-inscription, [connexion sociale](social-login.md), profils utilisateur
   * Notifications : Les membres voient des événements qui leur sont pertinents
   * Messagerie : Les membres peuvent envoyer ou recevoir des messages sur le site de la communauté
   * Rechercher : Possibilité de rechercher dans le site de la communauté
   * Changement de langue : Possibilité de sélectionner une langue pour un [site multilingue](../../help/sites-administering/translation.md)
   * Administration : Accès des membres autorisés à modérer et gérer les utilisateurs sur le site de la communauté
* Élimine de nombreuses étapes de création au niveau de la page :
   * Marques : Chargement facultatif d’une image de bannière à afficher sur toutes les pages du site de la communauté
   * Menu de navigation : Des liens de navigation sont fournis pour les fonctionnalités incluses dans le modèle de site de la communauté.

Pour découvrir la facilité de création rapide d’un nouveau site communautaire, rendez-vous sur la page [Prise en main d’AEM Communities](getting-started.md).

## Persistance du contenu de la communauté {#community-content-persistence}

Pour améliorer les performances et la synchronisation du contenu de la communauté, AEM Communities nécessite un magasin commun spécifique au contenu généré par l’utilisateur (UGC) partagé entre toutes les instances d’AEM (auteur et publication).

Le contenu de la communauté est facilement accessible par le biais du fournisseur de ressources de stockage (SRP), qui fournit une couche pour séparer l’accès de la topologie sous-jacente et prend en charge un magasin commun pour le contenu généré par l’utilisateur.

Pour en savoir plus sur la persistance du contenu de la communauté et les déploiements recommandés, rendez-vous sur :

* [Stockage de contenu communautaire](working-with-srp.md): présente les options de stockage SRP disponibles pour le contenu généré par l’utilisateur.
* [Topologies recommandées](topologies.md): aborde les topologies en fonction du cas d’utilisation et du choix de la SRP
* [Mise à niveau vers AEM 6.3 Communities](upgrade.md): fournit des informations utiles sur le contenu généré par l’utilisateur lors du passage à AEM 6.3.

## Consoles Communities {#communities-consoles}

Dans l’environnement de création, la console de navigation globale permet d’accéder au [Console des communautés](consoles.md), qui contient :

* La console [Sites](sites-console.md)

   * Création de site
   * Modification du site
   * Gestion de site
   * [Groupes communautaires](groups.md) console

* [Console Modération](moderation.md)

   * Interface utilisateur de modération en bloc commune pour les environnements de création et de publication
   * Nouveaux critères de filtrage

* [Membres et groupes](members.md) consoles de gestion

   * Permet de créer et de gérer des utilisateurs (membres) côté publication à partir de l’environnement de création.
   * Possibilité d’interdire les membres
   * Permet de créer et de gérer des groupes d’utilisateurs côté publication (groupes de membres) à partir de l’environnement de création.

* [Rapports](reports.md) console

   * Permet de générer des rapports sur les affectations, les publications et les vues.

* [Ressources](resources.md) console

   * Permet de créer des ressources d’activation et des parcours de formation
   * Permet d’accéder aux rapports sur les ressources d’activation et les parcours de formation

La console d’outils globale permet d’accéder aux outils Communities suivants :

* [Modèles de site](tools.md#sitetemplatesconsole) console

   * Créer et gérer des modèles de site de communauté

* [Modèles de groupe](tools.md#grouptemplatesconsole) console

   * Créer et gérer des modèles de groupes de communautés

* [Fonctions de communauté](tools.md#communityfunctionsconsole) console

   * Créer et gérer des fonctions de communauté

* [Configuration de stockage](tools.md#storageconfiguratonconsole) console

   * Sélectionnez et configurez le [magasin commun](working-with-srp.md) pour le site

* [Guide du composant](components-guide.md)

   * un exemple de site, [Composants de la communauté](http://localhost:4502/editor.html/content/community-components/en.html), qui fournit un exemple de tous les composants Communities avec leur configuration par défaut et la possibilité de les tester.

## Modèles de site de communauté {#community-site-templates}

La création d’un site de communauté est basée sur la sélection d’un modèle de site de communauté afin de configurer rapidement un site de communauté indépendant de tout exemple de site.

Un modèle de site de communauté, composé de fonctions de communauté et de modèles de groupe, fournit la structure d’un site de communauté, y compris les identifiants de connexion, les profils utilisateur, la messagerie, le menu du site, la recherche, le thème et les fonctionnalités de marque.

Voir [Console Modèles de site](sites.md).

## Fonctions de la communauté {#community-functions}

Les caractéristiques attendues d’une expérience communautaire sont bien connues. Avec AEM Communities, ces fonctionnalités sont disponibles sous la forme de blocs de création, appelés fonctions de communauté.

Les fonctions de communauté sont des pages d’AEM normales composées de composants connectés dans une fonctionnalité facilement intégrée à un modèle de site de communauté.

Voir [Console Fonctions de communauté](functions.md).

## Groupes communautaires et modèles de groupe {#community-groups-and-group-templates}

La fonctionnalité de groupes de communautés permet à une sous-communauté d’être créée dynamiquement dans un site de communauté par des utilisateurs autorisés et des membres de la communauté à partir des environnements de création et de publication .

Dans l’environnement de création, les groupes de communautés (sous-communautés) peuvent être créés dans un site de communauté existant ou imbriqués dans un groupe existant, lorsque la structure du modèle contient le [Fonction Groupes](functions.md#groups-function).

La création d’un groupe de communautés nécessite la sélection d’un modèle de groupe de communautés qui fournit la conception des pages du groupe de communautés. Lorsqu’une fonction Groupes est ajoutée à une structure de modèle, elle est configurée pour spécifier un modèle de groupe ou pour offrir un choix de modèles au moment de la création d’un groupe de communautés.

Voir également :

* [Console Groupes de sites](groups.md) - création de sous-communautés dans l’environnement de création
* [Console Modèles de groupe](tools-groups.md) - création de la structure du site pour les groupes
* [Prise en main d’AEM Communities](getting-started.md) - tutoriel sur la création rapide d’un site communautaire comprenant des groupes imbriqués

## Composants de la communauté {#community-components}

Le [composants de communauté](author-communities.md) à partir duquel un site de communauté est créé peut être utilisé pour ajouter des fonctionnalités de communauté à n’importe quel site AEM.

Le [guide des composants de communauté](components-guide.md) est disponible pour l’exploration interactive des composants.

## Types de communautés {#types-of-communities}

### Communauté d’engagement {#engagement-community}

Une communauté d’engagement est un site communautaire axé sur l’interaction entre les clients et leur permettant d’informer, de solliciter des commentaires et d’interagir en tant que membres de la communauté.

Les caractéristiques d’une communauté d’engagement peuvent être les suivantes :

* La connexion
* Message
* Forums
* Commentaires
* Révisions
* Evaluations
* Vote
* Blogs
* Groupes
* Calendriers
* Traduction
* Modération
* Notifications
* Notation et badges
* Rapports Analytics

Pour découvrir la facilité de création rapide d’une nouvelle communauté d’engagement, rendez-vous sur la page [Prise en main d’AEM Communities](getting-started.md).

### Communauté d’activation {#enablement-community}

Une communauté d’activation est un site communautaire qui comprend des fonctionnalités d’apprentissage en ligne.

Les fonctionnalités d’une communauté d’activation peuvent être les suivantes :

* Toutes les fonctionnalités d’une [communauté d&#39;engagement](#engagement-community)
* Possibilité d’affecter du contenu et des ressources d’apprentissage aux membres et aux groupes de membres
* Prend en charge le contenu SCORM, comme les questionnaires et les tests
* Suivi de la fin des affectations
* Accès aux rapports et analyses
* la possibilité d’avoir une conversation sur une ressource d’apprentissage par le biais de forums, de messages, de commentaires et d’évaluations ;

Une communauté d’activation peut être créée lorsque la variable [Le module complémentaire d’activation est configuré.](enablement.md), qui nécessite des licences supplémentaires pour une utilisation dans un environnement de production. Un site de communauté d’activation comprend la variable [fonction d&#39;attribution](#community-functions).

Pour découvrir la facilité de création d’une communauté d’activation, rendez-vous sur la page [Prise en main d’AEM Communities pour l’activation](getting-started-enablement.md).

## AEM Demo Machine {#aem-demo-machine}

Le [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) gère et exécute des démonstrations pour AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Ressources](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communautés](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Applications](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) et [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), qui nécessitent souvent plus de configuration que de simplement lancer une instance QuickStart. AEM Demo Machine va configurer d’autres [infrastructure](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) comme les serveurs MongoDB, Solr, MySQL, FFmpeg et de messagerie.

La machine de démonstration d’AEM est constituée de

* A [interface utilisateur graphique](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Scripts Apache ANT configurables [properties](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) et [targets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Packages pour installer La machine de démonstration AEM a été testée avec succès avec CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, 6.2 et 6.3 sous Windows, MacOS et Linux.

AEM Demo Machine nécessite une licence AEM valide.

>[!NOTE]
>
>Afficher un [introduction vidéo](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) à la machine de démonstration AEM (13:26).

## Documentation AEM Communities {#aem-communities-documentation}

* Visite [Déploiement de communautés](deploy-communities.md) pour en savoir plus sur les déploiements recommandés.

* Visite [Administration des sites des communautés](administer-landing.md) pour en savoir plus sur la création d’un site communautaire, l’ajout de groupes communautaires, la configuration de modèles de site communautaire, la modération de contenu communautaire, la gestion des membres, le balisage, les notifications, la notation et les badges.

* Visite [Développement de communautés](communities.md) pour en savoir plus sur la structure de composants sociaux (SCF) et la personnalisation des composants et fonctionnalités des communautés.

* Visite [Création de composants Communities](author-communities.md) pour savoir comment créer avec et configurer des composants Communities.
