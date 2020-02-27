---
title: Présentation d’AEM Communities
seo-title: Présentation d’AEM Communities
description: Présentation des fonctionnalités et de la configuration des communautés AEM
seo-description: Présentation des fonctionnalités et de la configuration des communautés AEM
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7

---


# Présentation d’AEM Communities {#aem-communities-overview}

Adobe Experience Manager (AEM) Communities permet de créer rapidement un site de communauté local doté de performances et d’une gestion de sites améliorées, et qui encourage les visiteurs à devenir membres de la communauté.

Contactez votre gestionnaire de compte pour plus d’informations sur la licence des communautés AEM, ainsi que sur les licences supplémentaires pour les fonctionnalités d’activation et Adobe Analytics.

## Fonctionnalités des communautés {#communities-features}

Les communautés AEM permettent le développement d’une relation avec les visiteurs du site qui fournit des informations par le biais de blogs, de questions et réponses et de calendriers d’événements, tout en obtenant des informations par le biais de forums, de commentaires et d’autres contenus de la communauté, souvent appelés contenu généré par l’utilisateur (UGC).

En outre, les communautés AEM permettent la modération par des membres de confiance dans l’environnement de publication, la connexion sociale avec Twitter et Facebook, la traduction en ligne du contenu de la communauté, la création de groupes de communautés à partir du site de la communauté publié, le score pour attribuer des badges, le partage de fichiers, les notifications et les flux d’activités.

Les fonctionnalités des communautés peuvent être démontrées à l’aide de la machine [de démonstration](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) AEM disponible publiquement sur GitHub.com ou avec la nouvelle implémentation de référence We.Retail.

## Sites communautaires {#community-sites}

Un site communautaire est un site AEM créé à l’aide d’un assistant simple qui génère un site Web avec de nombreuses fonctionnalités courantes pré-connectées au site.

Assistant [de création de](sites-console.md)site :

* Assemble les fonctionnalités du site, en fonction du modèle [de site de la](sites.md) communauté sélectionné, qui est
   * Construit à partir de fonctions [communautaires](#community-functions)
   * Fonctionnalité facultative des groupes [de](#communitygroups) communauté
* Utilise les paramètres à configurer :
   * Modération
   * Connexion
   * Traduction
* Fournit des fonctionnalités essentielles :
   * Conception réactive : Utilise les thèmes [Twitter Bootstrap](https://getbootstrap.com)
   * Connexion : Auto-inscription, connexion [](social-login.md)sociale, profils utilisateur
   * Notifications : Les membres voient les événements qui les intéressent
   * Messagerie : Les membres peuvent envoyer ou recevoir des messages sur le site communautaire
   * Rechercher : Possibilité de rechercher dans le site de la communauté
   * Changement de langue : Possibilité de sélectionner une langue pour un site [multilingue](../../help/sites-administering/translation.md)
   * Administration : Accès des membres autorisés à modérer et à gérer les utilisateurs du site communautaire
* Élimine de nombreuses étapes de création au niveau de la page :
   * Marque : Téléchargement facultatif d’une image de bannière à afficher sur toutes les pages du site de la communauté
   * Menu de navigation : Des liens de navigation sont fournis pour les fonctionnalités incluses dans le modèle de site communautaire.

Pour découvrir la facilité de création rapide d’un nouveau site communautaire, consultez [Prise en main des communautés](getting-started.md)AEM.

## Persistance du contenu de la communauté {#community-content-persistence}

Pour améliorer les performances et la synchronisation du contenu de la communauté, les communautés AEM nécessitent un magasin commun spécifique pour le contenu généré par l’utilisateur (UGC) partagé entre toutes les instances AEM (auteur et publication).

Le contenu de la communauté est facilement accessible via le fournisseur de ressources de stockage (SRP), qui fournit une couche pour séparer l&#39;accès de la topologie sous-jacente et prend en charge un magasin commun pour l&#39;UGC.

Pour en savoir plus sur la persistance du contenu de la communauté et les déploiements recommandés, consultez :

* [Stockage](working-with-srp.md)du contenu de la communauté : décrit les options de stockage SRP disponibles pour l&#39;UGC
* [Topologies](topologies.md)recommandées : aborde les topologies en fonction de la casse d’utilisation et du choix SRP
* [Mise à niveau vers les communautés](upgrade.md)AEM 6.3 : fournit des informations utiles sur l’UGC lors du passage à AEM 6.3.

## Console Communautés {#communities-consoles}

Dans l’environnement de création, la console de navigation globale permet d’accéder à la console [](consoles.md)Communautés, qui contient :

* La console [Sites](sites-console.md)

   * Création de site
   * Modification du site
   * Gestion de site
   * [Console Groupes](groups.md) de communautés

* [Console Modération](moderation.md)

   * Interface utilisateur commune de modération en bloc pour les environnements de création et de publication
   * Nouveaux critères de filtrage

* [Consoles de gestion des membres et des groupes](members.md)

   * Permet de créer et de gérer des utilisateurs (membres) côté publication à partir de l’environnement de création.
   * Permet d&#39;interdire les membres
   * Permet de créer et de gérer des groupes d’utilisateurs côté publication (groupes de membres) à partir de l’environnement d’auteur.

* [Console Rapports](reports.md)

   * Permet de générer des rapports sur les affectations, les publications et les vues

* [Console Ressources](resources.md)

   * Permet de créer des ressources d’activation et des chemins d’apprentissage
   * Fournit un accès aux rapports sur les ressources d’activation et les chemins d’apprentissage

La console d’outils globale donne accès aux outils de communautés suivants :

* [Console Modèles](tools.md#sitetemplatesconsole) de site

   * Création et gestion de modèles de site de la communauté

* [Console Modèles](tools.md#grouptemplatesconsole) de groupe

   * Création et gestion de modèles de groupes de communautés

* [Console Fonctions](tools.md#communityfunctionsconsole) de la communauté

   * Création et gestion des fonctions de la communauté

* [Console de configuration](tools.md#storageconfiguratonconsole) du stockage

   * Sélectionnez et configurez le magasin [](working-with-srp.md) commun pour le site

* [Guide du composant](components-guide.md)

   * Un exemple de site, Composants [de la](http://localhost:4502/editor.html/content/community-components/en.html)communauté, qui fournit un échantillon de tous les composants de la communauté avec leur configuration par défaut et la possibilité de les tester.

## Modèles de site de communauté {#community-site-templates}

La création d&#39;un site communautaire est basée sur la sélection d&#39;un modèle de site communautaire afin de configurer rapidement un site communautaire indépendant de tout exemple de site.

Un modèle de site de la communauté, composé de fonctions de la communauté et de modèles de groupes de la communauté, fournit la structure d’un site de la communauté, y compris les identifiants de connexion, les profils utilisateur, la messagerie, le menu du site, la recherche, le thème et les fonctionnalités de marque.

Voir la console [Modèles de](sites.md)site.

## Fonctions de la communauté {#community-functions}

Les caractéristiques attendues d&#39;une expérience communautaire sont bien connues. Avec les communautés AEM, ces fonctionnalités sont disponibles sous forme de blocs de création, appelés fonctions de communauté.

Les fonctions de la communauté sont des pages AEM normales composées de composants reliés entre eux dans une fonctionnalité facilement intégrée dans un modèle de site commun.

See the [Community Functions console](functions.md).

## Groupes de communautés et modèles de groupes {#community-groups-and-group-templates}

La fonctionnalité des groupes communautaires permet à une sous-communauté d’être créée dynamiquement dans un site communautaire par des utilisateurs autorisés et des membres de la communauté provenant des environnements d’auteur et de publication.

Dans l’environnement de l’auteur, des groupes communautaires (sous-communautés) peuvent être créés dans un site communautaire existant ou imbriqués dans un groupe existant, lorsque la structure du modèle contient la fonction [](functions.md#groups-function)Groupes.

La création d&#39;un groupe communautaire nécessite la sélection d&#39;un modèle de groupe communautaire qui fournit la conception des pages de groupe communautaire. Lorsqu’une fonction Groupes est ajoutée à une structure de modèle, elle est configurée pour spécifier un modèle de groupe ou pour fournir un choix de modèles au moment de la création d’un nouveau groupe de communauté.

Voir également:

* [Console](groups.md) Groupes de sites - création de sous-communautés dans l&#39;environnement de création
* [Console](tools-groups.md) Modèles de groupe - création de la structure du site pour les groupes
* [Prise en main des communautés](getting-started.md) AEM - didacticiel pour la création rapide d’un site communautaire incluant des groupes imbriqués

## Composants communautaires {#community-components}

Les composants [de](author-communities.md) la communauté à partir desquels un site communautaire est créé peuvent être utilisés pour ajouter des fonctionnalités de communautés à tout site AEM.

Le guide [des composants](components-guide.md) communautaires est disponible pour l’exploration interactive des composants.

## Types de communautés {#types-of-communities}

### Communauté d’engagement {#engagement-community}

Une communauté d’engagement est un site communautaire axé sur l’engagement des clients à informer, à solliciter des commentaires et à permettre aux clients d’interagir en tant que membres de la communauté.

Les caractéristiques d&#39;une communauté d&#39;engagement peuvent être les suivantes :

* Connexion
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
* Scores et badges
* Création de rapports Analytics

Pour découvrir la facilité de création rapide d’une nouvelle communauté d’engagement, consultez [Prise en main des communautés](getting-started.md)AEM.

### Communauté d&#39;activation {#enablement-community}

Une communauté d’activation est un site communautaire qui comprend des fonctionnalités d’apprentissage en ligne.

Les caractéristiques d’une communauté d’activation peuvent être les suivantes :

* Toutes les caractéristiques d&#39;une communauté [d&#39;engagement](#engagement-community)
* Capacité à affecter du contenu et des ressources d’apprentissage aux membres et aux groupes de membres
* Prend en charge le contenu SCORM, comme les questionnaires et les tests
* Suivi des affectations terminées
* Accès aux rapports et analyses
* Possibilité d’avoir une conversation sur une ressource d’apprentissage par le biais de forums, de messages, de commentaires et d’évaluations

Une communauté d&#39;activation peut être créée lorsque le module complémentaire [d&#39;activation est configuré](enablement.md), ce qui nécessite une licence supplémentaire pour une utilisation dans un environnement de production. Un site de la communauté d&#39;activation inclura la fonction [](#community-functions)assignations.

Pour découvrir la facilité de création d’une nouvelle communauté d’activation, consultez [Prise en main des communautés AEM pour l’activation](getting-started-enablement.md).

## Machine de démonstration AEM {#aem-demo-machine}

La machine [de démonstration](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) AEM gère et exécute des démos pour les [sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites)AEM, les [ressources](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets)[, les communautés, les applications et lesForms, qui nécessitent souvent plus de configuration que de simplement lancer une instance QuickStart. ](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities)[](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps)[](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) La machine de démonstration AEM installera une [infrastructure](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) supplémentaire telle que MongoDB, Solr, MySQL, FFmpeg et les serveurs de messagerie.

La machine de démonstration AEM est composée de

* Interface utilisateur [graphique](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Scripts Apache ANT avec [propriétés](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) et [cibles configurables](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Packages to installLa machine de démonstration AEM a été testée avec succès avec CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 et AEM 6.3 sous Windows, MacOS et Linux.

La machine de démonstration AEM requiert une licence AEM valide.

>[!NOTE]
>
>Visionnez une présentation [](https://www.youtube.com/watch?v=zEE_zkR9fVQ&feature=youtu.be) vidéo sur la machine de démonstration AEM (13:26).

## Documentation des communautés AEM {#aem-communities-documentation}

* Visit [Deploying Communities](deploy-communities.md) to learn about recommended deployments.

* Visitez [Administration des sites](administer-landing.md) des communautés pour en savoir plus sur la création d’un site communautaire, l’ajout de groupes communautaires, la configuration de modèles de site communautaire, la modération du contenu communautaire, la gestion des membres, le balisage, les notifications, la notation et les badges.

* Visit [Developing Communities](communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.

* Visitez [Création de composants](author-communities.md) de communautés pour apprendre à créer et à configurer des composants de communautés.

