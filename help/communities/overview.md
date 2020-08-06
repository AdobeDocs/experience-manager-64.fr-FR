---
title: Présentation d’AEM Communities
seo-title: Présentation d’AEM Communities
description: Présentation des fonctionnalités et de la configuration d’AEM Communities
seo-description: Présentation des fonctionnalités et de la configuration d’AEM Communities
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 5%

---


# Présentation d’AEM Communities {#aem-communities-overview}

Adobe Experience Manager (AEM) Communities permet de créer rapidement un site de communauté local doté de performances et d’une gestion de sites améliorées, et qui encourage les visiteurs à devenir membres de la communauté.

Contactez le représentant de votre compte pour obtenir des informations sur la licence d’AEM Communities, ainsi que des licences supplémentaires pour les fonctionnalités d’activation et Adobe Analytics.

## Fonctionnalités des communautés {#communities-features}

AEM Communities permet le développement d&#39;une relation avec les visiteurs du site qui fournit des informations par le biais de blogs, de questions-réponses et de calendriers de événement, tout en obtenant des informations par le biais de forums, de commentaires et d&#39;autres contenus de la communauté, souvent appelés contenu généré par l&#39;utilisateur (UGC).

De plus, AEM Communities permet la modération par des membres de confiance dans l&#39;environnement de publication, la connexion sociale avec Twitter et Facebook, la traduction en ligne du contenu de la communauté, la création de groupes communautaires à partir du site communautaire publié, le score pour attribuer des badges, le partage de fichiers, les notifications et les flux d&#39;activité.

Les fonctionnalités des communautés peuvent être démontrées à l&#39;aide de l&#39;AEM Demo Machine [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponible publiquement sur GitHub.com ou avec la nouvelle implémentation de référence We.Retail.

## Sites communautaires {#community-sites}

Un site communautaire est un site AEM créé à l&#39;aide d&#39;un assistant simple qui produit un site Web avec de nombreuses fonctionnalités courantes pré-câblées dans le site.

Assistant [de création de](sites-console.md)site :

* Assemble les fonctionnalités du site, en fonction du modèle [de site](sites.md) communautaire sélectionné qui est
   * Construit à partir de fonctions [communautaires](#community-functions)
   * Fonctionnalité facultative des groupes [](#communitygroups) de la communauté
* Utilise les paramètres à configurer :
   * Modération
   * Connexion
   * Traduction
* Fournit des fonctionnalités essentielles :
   * Conception réactive : Utilise les thèmes de Bootstrap [Twitter](https://getbootstrap.com)
   * Connexion : Auto-inscription, connexion [](social-login.md)sociale, profils utilisateur
   * Notifications : Les membres voient les événements qui les concernent
   * Messagerie : Les membres peuvent envoyer ou recevoir des messages sur le site communautaire
   * Rechercher : Capacité à effectuer des recherches sur le site de la communauté
   * Changement de langue : Possibilité de sélectionner une langue pour un site [multilingue](../../help/sites-administering/translation.md)
   * Administration : Accès des membres autorisés à modérer et à gérer les utilisateurs sur le site communautaire
* Élimine de nombreuses étapes de création au niveau de la page :
   * Marque : Téléchargement facultatif d’une image de bannière à afficher sur toutes les pages du site de la communauté
   * Menu Navigation : Des liens de navigation sont fournis pour les fonctionnalités incluses dans le modèle de site communautaire.

Pour découvrir la facilité de création rapide d&#39;un nouveau site communautaire, consultez [Prise en main avec AEM Communities](getting-started.md).

## Persistance du contenu de la communauté {#community-content-persistence}

Pour améliorer les performances et la synchronisation du contenu de la communauté, AEM Communities a besoin d’un magasin commun spécifique pour le contenu généré par l’utilisateur (UGC) partagé entre toutes les instances d’AEM (auteur et publication).

Le contenu de la communauté est facilement accessible par l&#39;intermédiaire du fournisseur de ressources d&#39;enregistrement (SRP), qui fournit une couche pour séparer l&#39;accès de la topologie sous-jacente et prend en charge un magasin commun pour l&#39;UGC.

Pour en savoir plus sur la persistance du contenu de la communauté et sur les déploiements recommandés, consultez :

* [Enregistrement](working-with-srp.md)de contenu de la communauté : présente les options d&#39;enregistrement SRP disponibles pour l&#39;UGC
* [Topologies](topologies.md)recommandées : aborde les topologies en fonction du cas d’utilisation et du choix SRP
* [Mise à niveau vers AEM 6.3 Communautés](upgrade.md): fournit des informations utiles sur l&#39;UGC lors du passage à AEM 6.3.

## Consoles de communautés {#communities-consoles}

Dans l’environnement d’auteur, la console de navigation globale permet d’accéder à la console [](consoles.md)Communautés, qui contient les éléments suivants :

* La console [Sites](sites-console.md)

   * Création du site
   * Modification du site
   * Gestion du site
   * [Console Groupes](groups.md) communautaires

* [Console Modération](moderation.md)

   * Interface utilisateur commune de modération en masse pour les environnements de création et de publication
   * Nouveaux critères de filtrage

* [Consoles de gestion des membres et des groupes](members.md)

   * Permet de créer et de gérer des utilisateurs (membres) côté publication à partir de l’environnement d’auteur.
   * Permet d&#39;interdire des membres
   * Permet de créer et de gérer des groupes d’utilisateurs côté publication (groupes de membres) à partir de l’environnement d’auteur.

* [Console Rapports](reports.md)

   * Permet de générer des rapports sur les affectations, les publications et les vues.

* [Console Ressources](resources.md)

   * Permet de créer des ressources d’activation et des chemins d’apprentissage
   * Fournit un accès aux rapports sur les ressources d’activation et les chemins d’apprentissage

La console d’outils globale permet d’accéder aux outils de communautés suivants :

* [Console Modèles](tools.md#sitetemplatesconsole) de site

   * Créer et gérer des modèles de site de la communauté

* [Console Modèles](tools.md#grouptemplatesconsole) de groupe

   * Création et gestion de modèles de groupes de communautés

* [Console des fonctions](tools.md#communityfunctionsconsole) de la communauté

   * Créer et gérer des fonctions de communauté

* [Console de configuration](tools.md#storageconfiguratonconsole) des Enregistrements

   * Sélectionner et configurer la boutique [](working-with-srp.md) commune pour le site

* [Guide du composant](components-guide.md)

   * Un exemple de site, Composants [](http://localhost:4502/editor.html/content/community-components/en.html)communautaires, qui fournit un échantillon de tous les composants Communautés avec leur configuration par défaut et la possibilité de les tester.

## Modèles de site de communauté {#community-site-templates}

La création d&#39;un site communautaire est basée sur la sélection d&#39;un modèle de site communautaire pour configurer rapidement un site communautaire indépendant de tout exemple de site.

Un modèle de site communautaire, composé de fonctions communautaires et de modèles de groupe communautaire, fournit la structure d’un site communautaire comprenant les fonctions de connexion, les profils utilisateur, la messagerie, le menu du site, la recherche, le thème et les fonctions de marque.

Voir la console [Modèles de](sites.md)site.

## Fonctions de la communauté {#community-functions}

Les caractéristiques attendues d&#39;une expérience communautaire sont bien connues. Avec AEM Communities, ces fonctionnalités sont disponibles sous forme de blocs de création, appelés fonctions communautaires.

Les fonctions de la communauté sont des pages AEM normales composées de composants reliés entre eux dans une fonction qui est facilement intégrée dans un modèle de site commun.

See the [Community Functions console](functions.md).

## Groupes communautaires et modèles de groupe {#community-groups-and-group-templates}

La fonction des groupes communautaires permet à une sous-communauté d’être créée dynamiquement dans un site communautaire par des utilisateurs autorisés et des membres de la communauté provenant à la fois des environnements d’auteur et de publication.

À partir de l&#39;environnement de l&#39;auteur, des groupes communautaires (sous-communautés) peuvent être créés dans un site communautaire existant ou imbriqués dans un groupe existant, lorsque la structure du modèle contient la fonction [](functions.md#groups-function)Groupes.

La création d&#39;un groupe communautaire nécessite la sélection d&#39;un modèle de groupe communautaire qui fournit la conception des pages de groupe communautaire. Lorsqu&#39;une fonction Groupes est ajoutée à une structure de modèle, elle est configurée pour spécifier un modèle de groupe ou pour fournir un choix de modèles au moment de la création d&#39;un nouveau groupe de communauté.

Voir également :

* [Console](groups.md) Groupes de sites - création de sous-communautés dans l&#39;environnement d&#39;auteur
* [Console](tools-groups.md) Modèles de groupe - création de la structure du site pour les groupes
* [Prise en main d’AEM Communities](getting-started.md) - didacticiel pour la création rapide d’un site communautaire incluant des groupes imbriqués

## Composants communautaires {#community-components}

Les composants [](author-communities.md) communautaires à partir desquels un site communautaire est construit peuvent être utilisés pour ajouter des fonctionnalités de communautés à tout site AEM.

Le guide [des composants](components-guide.md) communautaires est disponible pour l&#39;exploration interactive des composants.

## Types de communautés {#types-of-communities}

### Communauté d’engagement {#engagement-community}

Une communauté d’engagement est un site communautaire axé sur la mobilisation des clients pour informer, solliciter des commentaires et permettre aux clients d’interagir en tant que membres de la communauté.

Les caractéristiques d&#39;une communauté d&#39;engagement peuvent inclure :

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
* rapports Analytics

Pour découvrir la facilité de création rapide d&#39;une nouvelle communauté d&#39;engagement, consultez [Prise en main avec AEM Communities](getting-started.md).

### Communauté d&#39;activation {#enablement-community}

Une communauté d’activation est un site communautaire qui comprend des fonctionnalités d’apprentissage en ligne.

Les caractéristiques d&#39;une communauté d&#39;activation peuvent être les suivantes :

* Toutes les caractéristiques d&#39;une communauté d&#39; [engagement](#engagement-community)
* Capacité à affecter du contenu et des ressources d’apprentissage aux membres et aux groupes de membres
* Prend en charge le contenu SCORM, comme les questionnaires et les tests
* Suivi des affectations terminées
* Accès aux rapports et analyses
* La possibilité d&#39;avoir une conversation sur une ressource d&#39;apprentissage par le biais de forums, de messages, de commentaires et d&#39;évaluations

Une communauté d&#39;activation peut être créée lorsque le module complémentaire [d&#39;activation est configuré](enablement.md), ce qui nécessite une licence supplémentaire pour une utilisation dans un environnement de production. Un site communautaire d&#39;activation inclut la fonction [](#community-functions)assignations.

Pour découvrir la facilité de création d’une communauté d’activation, consultez [Prise en main d’AEM Communities pour l’activation](getting-started-enablement.md).

## AEM machine de démonstration {#aem-demo-machine}

L’AEM [Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) gère et exécute des démos pour AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities, Appset Forms, qui nécessitent souvent plus de configuration que de simplement lancer une instance QuickStart. ](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities)[](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps)[](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) AEM Demo Machine va installer une [infrastructure](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) supplémentaire telle que MongoDB, Solr, MySQL, FFmpeg et les serveurs de messagerie.

L&#39;AEM machine de démonstration est composée de

* Interface utilisateur [graphique](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Scripts Apache ANT avec [propriétés](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) et [cibles configurables](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Packages à installerL&#39;AEM Demo Machine a été testé avec succès avec CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1,  6.2 et l&#39; 6.3 sous Windows, MacOS et Linux.

L&#39;AEM Demo Machine requiert une licence AEM valide.

>[!NOTE]
>
>Vue une présentation [](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) vidéo de l&#39;AEM Demo Machine (13:26).

## Documentation de l’AEM Communities {#aem-communities-documentation}

* Visit [Deploying Communities](deploy-communities.md) to learn about recommended deployments.

* Visitez [Administration des sites](administer-landing.md) des communautés pour en savoir plus sur la création d’un site communautaire, l’ajout de groupes communautaires, la configuration de modèles de site communautaire, la modération du contenu communautaire, la gestion des membres, le balisage, les notifications, la notation et les badges.

* Visit [Developing Communities](communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.

* Visitez la page Composants [Communautés](author-communities.md) de création pour découvrir comment créer et configurer des composants Communautés.

