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
source-git-commit: 1375282df15b1a1a1ab5ed760190af8d6288970e
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 5%

---


# Présentation d’AEM Communities {#aem-communities-overview}

Adobe Experience Manager (AEM) Communities permet de créer rapidement un site de communauté local doté de performances et d’une gestion de sites améliorées, et qui encourage les visiteurs à devenir membres de la communauté.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Fonctionnalités des communautés {#communities-features}

AEM Communities permet le développement d&#39;une relation avec les visiteurs du site qui fournit des informations par le biais de blogs, de questions-réponses et de calendriers de événement, tout en obtenant des informations par le biais de forums, de commentaires et d&#39;autres contenus de la communauté, souvent appelés contenu généré par l&#39;utilisateur (UGC).

De plus, AEM Communities permet la modération par des membres de confiance dans l&#39;environnement de publication, la connexion sociale avec Twitter et Facebook, la traduction en ligne du contenu de la communauté, la création de groupes communautaires à partir du site communautaire publié, le score pour attribuer des badges, le partage de fichiers, les notifications et les flux d&#39;activité.

Les fonctionnalités des communautés peuvent être démontrées à l&#39;aide de la [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponible publiquement sur GitHub.com ou avec la nouvelle implémentation de référence We.Retail.

## Sites communautaires {#community-sites}

Un site communautaire est un site AEM créé à l&#39;aide d&#39;un assistant simple qui produit un site Web avec de nombreuses fonctionnalités courantes pré-câblées dans le site.

L&#39;[Assistant de création de site](sites-console.md) :

* Assemble les fonctionnalités du site, en fonction du [modèle de site communautaire ](sites.md) sélectionné, qui est
   * Créé à partir de [fonctions de la communauté](#community-functions)
   * Fonctionnalité facultative [groupes de communautés](#communitygroups)
* Utilise les paramètres à configurer :
   * Modération
   * Connexion
   * Traduction
* Fournit des fonctionnalités essentielles :
   * Conception réactive : Utilise [les thèmes de Bootstrap Twitter](https://getbootstrap.com)
   * Connexion : Auto-inscription, [connexion sociale](social-login.md), profils utilisateur
   * Notifications : Les membres voient les événements qui les concernent
   * Messagerie : Les membres peuvent envoyer ou recevoir des messages sur le site communautaire
   * Rechercher : Capacité à effectuer des recherches sur le site de la communauté
   * Changement de langue : Possibilité de sélectionner une langue pour un [site multilingue](../../help/sites-administering/translation.md)
   * Administration : Accès des membres autorisés à modérer et à gérer les utilisateurs sur le site communautaire
* Élimine de nombreuses étapes de création au niveau de la page :
   * Marque : Téléchargement facultatif d’une image de bannière à afficher sur toutes les pages du site de la communauté
   * Menu Navigation : Des liens de navigation sont fournis pour les fonctionnalités incluses dans le modèle de site communautaire.

Pour découvrir la facilité de création rapide d&#39;un nouveau site communautaire, visitez [Prise en main de AEM Communities](getting-started.md).

## Persistance du contenu de la communauté {#community-content-persistence}

Pour améliorer les performances et la synchronisation du contenu de la communauté, AEM Communities a besoin d’un magasin commun spécifique pour le contenu généré par l’utilisateur (UGC) partagé entre toutes les instances d’AEM (auteur et publication).

Le contenu de la communauté est facilement accessible par l&#39;intermédiaire du fournisseur de ressources d&#39;enregistrement (SRP), qui fournit une couche pour séparer l&#39;accès de la topologie sous-jacente et prend en charge un magasin commun pour l&#39;UGC.

Pour en savoir plus sur la persistance du contenu de la communauté et sur les déploiements recommandés, consultez :

* [Enregistrement](working-with-srp.md) de contenu de la communauté : présente les options d&#39;enregistrement SRP disponibles pour l&#39;UGC
* [Topologies](topologies.md) recommandées : aborde les topologies en fonction du cas d’utilisation et du choix SRP
* [Mise à niveau vers AEM 6.3 Communautés](upgrade.md) : fournit des informations utiles sur l&#39;UGC lors du passage à AEM 6.3.

## Consoles de communautés {#communities-consoles}

Dans l’environnement d’auteur, la console de navigation globale permet d’accéder à la [console Communautés](consoles.md), qui contient les éléments suivants :

* La console [Sites](sites-console.md)

   * Création du site
   * Modification du site
   * Gestion du site
   * [Community ](groups.md) Groupsconsole

* [Console Modération](moderation.md)

   * Interface utilisateur commune de modération en masse pour les environnements de création et de publication
   * Nouveaux critères de filtrage

* [Consoles de gestion des membres et des ](members.md) groupes

   * Permet de créer et de gérer des utilisateurs (membres) côté publication à partir de l’environnement d’auteur.
   * Permet d&#39;interdire des membres
   * Permet de créer et de gérer des groupes d’utilisateurs côté publication (groupes de membres) à partir de l’environnement d’auteur.

* [](reports.md) Console de rapports

   * Permet de générer des rapports sur les affectations, les publications et les vues.

* [](resources.md) Resourcesconsole

   * Permet de créer des ressources d’activation et des chemins d’apprentissage
   * Fournit un accès aux rapports sur les ressources d’activation et les chemins d’apprentissage

La console d’outils globale permet d’accéder aux outils de communautés suivants :

* [Site ](tools.md#sitetemplatesconsole) Templatesconsole

   * Créer et gérer des modèles de site de la communauté

* [Group ](tools.md#grouptemplatesconsole) Templatesconsole

   * Création et gestion de modèles de groupes de communautés

* [Community ](tools.md#communityfunctionsconsole) Functionsconsole

   * Créer et gérer des fonctions de communauté

* [Enregistrement ](tools.md#storageconfiguratonconsole) Configuration Console

   * Sélectionnez et configurez le [magasin commun](working-with-srp.md) pour le site.

* [Guide du composant](components-guide.md)

   * Un exemple de site, [Composants communautaires](http://localhost:4502/editor.html/content/community-components/en.html), qui fournit un échantillon de tous les composants de communautés avec leur configuration par défaut et la possibilité de les tester.

## Modèles de site de communauté {#community-site-templates}

La création d&#39;un site communautaire est basée sur la sélection d&#39;un modèle de site communautaire pour configurer rapidement un site communautaire indépendant de tout exemple de site.

Un modèle de site communautaire, composé de fonctions communautaires et de modèles de groupe communautaire, fournit la structure d’un site communautaire comprenant les fonctions de connexion, les profils utilisateur, la messagerie, le menu du site, la recherche, le thème et les fonctions de marque.

Voir la [console Modèles de site](sites.md).

## Fonctions de la communauté {#community-functions}

Les caractéristiques attendues d&#39;une expérience communautaire sont bien connues. Avec AEM Communities, ces fonctionnalités sont disponibles sous forme de blocs de création, appelés fonctions communautaires.

Les fonctions de la communauté sont des pages AEM normales composées de composants reliés entre eux dans une fonction qui est facilement intégrée dans un modèle de site commun.

Voir la console [Fonctions de la communauté](functions.md).

## Groupes communautaires et modèles de groupe {#community-groups-and-group-templates}

La fonction des groupes communautaires permet à une sous-communauté d’être créée dynamiquement dans un site communautaire par des utilisateurs autorisés et des membres de la communauté provenant à la fois des environnements d’auteur et de publication.

À partir de l&#39;environnement auteur, des groupes communautaires (sous-communautés) peuvent être créés dans un site communautaire existant ou imbriqués dans un groupe existant, lorsque la structure du modèle contient la fonction [Groupes](functions.md#groups-function).

La création d&#39;un groupe communautaire nécessite la sélection d&#39;un modèle de groupe communautaire qui fournit la conception des pages de groupe communautaire. Lorsqu&#39;une fonction Groupes est ajoutée à une structure de modèle, elle est configurée pour spécifier un modèle de groupe ou pour fournir un choix de modèles au moment de la création d&#39;un nouveau groupe de communauté.

Voir également :

* [Console](groups.md)  Groupes de sites : création de sous-communautés dans l&#39;environnement d&#39;auteur
* [Console](tools-groups.md)  Modèles de groupe : création de la structure du site pour les groupes
* [Prise en main de AEM Communities](getting-started.md)  - didacticiel pour la création rapide d&#39;un site communautaire incluant des groupes imbriqués

## Composants de la communauté {#community-components}

Les [composants communautaires](author-communities.md) à partir desquels un site communautaire est construit peuvent être utilisés pour ajouter des fonctionnalités de communautés à tout site AEM.

Le [guide des composants de la communauté](components-guide.md) est disponible pour une exploration interactive des composants.

## Types de communautés {#types-of-communities}

### Communauté d&#39;engagement {#engagement-community}

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
* Rapports Analytics

Pour découvrir la facilité de création rapide d&#39;une nouvelle communauté d&#39;engagement, visitez [Prise en main de AEM Communities](getting-started.md).

### Communauté d&#39;activation {#enablement-community}

Une communauté d’activation est un site communautaire qui comprend des fonctionnalités d’apprentissage en ligne.

Les caractéristiques d&#39;une communauté d&#39;activation peuvent être les suivantes :

* Toutes les caractéristiques d&#39;une [communauté d&#39;engagement](#engagement-community)
* Capacité à affecter du contenu et des ressources d’apprentissage aux membres et aux groupes de membres
* Prend en charge le contenu SCORM, comme les questionnaires et les tests
* Suivi des affectations terminées
* Accès aux rapports et analyses
* La possibilité d&#39;avoir une conversation sur une ressource d&#39;apprentissage par le biais de forums, de messages, de commentaires et d&#39;évaluations

Une communauté d&#39;activation peut être créée lorsque le module complémentaire [Activation est configuré](enablement.md), ce qui nécessite une licence supplémentaire pour une utilisation dans un environnement de production. Un site de communauté d&#39;activation inclura la fonction [assignations](#community-functions).

Pour découvrir la facilité de création d&#39;une nouvelle communauté d&#39;activation, visitez [Prise en main de AEM Communities pour l&#39;activation](getting-started-enablement.md).

## aem Demo Machine {#aem-demo-machine}

La [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) gère et exécute des démos pour AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Ressources](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communautés](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Applications](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) et [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), qui nécessitent souvent plus de configuration que le lancement. Instance QuickStart. L&#39;AEM Demo Machine va installer une infrastructure [supplémentaire](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) telle que MongoDB, Solr, MySQL, FFmpeg et les serveurs de messagerie.

L&#39;AEM machine de démonstration est composée de

* Une [interface utilisateur graphique](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Scripts Apache ANT avec des propriétés [configurables](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) et [cibles](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Packages à installer
L&#39;AEM Demo Machine a été testé avec succès avec CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1,  6.2 et  6.3 sous Windows, MacOS et Linux.

L&#39;AEM Demo Machine requiert une licence AEM valide.

>[!NOTE]
>
>Vue d&#39;une [introduction vidéo](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) à l&#39;AEM Demo Machine (13:26).

## Documentation AEM Communities {#aem-communities-documentation}

* Visitez [Déploiement de communautés](deploy-communities.md) pour en savoir plus sur les déploiements recommandés.

* Visitez [Administration des sites des communautés](administer-landing.md) pour en savoir plus sur la création d&#39;un site communautaire, l&#39;ajout de groupes communautaires, la configuration des modèles de site communautaire, la modération du contenu communautaire, la gestion des membres, le balisage, les notifications, la notation et les badges.

* Visitez [Communautés en développement](communities.md) pour en savoir plus sur le cadre des composants sociaux (SCF) et sur la personnalisation des composants et fonctionnalités des communautés.

* Visitez [Création de composants de communautés](author-communities.md) pour savoir comment créer et configurer des composants de communautés.

