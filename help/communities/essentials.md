---
title: Notions fondamentales sur les composants, les fonctions et les fonctionnalités
seo-title: Component, Function and Feature Essentials
description: Fonctionnement des sites, modèles et groupes de communautés
seo-description: How community sites, templates, and groups function
uuid: 6edfca2d-fe5b-4261-b033-51dc2f9dbfd7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 2d308756-79d1-4d69-b51c-d4b6e692a137
exl-id: bde29d3a-8bc8-4c30-b764-a2fa1ac34069
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 19%

---

# Notions fondamentales sur les composants, les fonctions et les fonctionnalités {#component-function-and-feature-essentials}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les fonctionnalités AEM Communities exigent que les visiteurs du site deviennent membres et se connectent au [site communautaire](overview.md#communitiessites) avant de pouvoir publier du contenu. Ainsi, [modèles de site de communauté](sites.md), à partir de laquelle un site communautaire est [created](sites-console.md), sont conçues pour inclure une fonction de connexion, ainsi que des profils utilisateur, des messages, des recherches, de la modération et des traductions.

Un site communautaire permet aux membres de créer des groupes communautaires lorsque la variable [fonction de groupes communautaires](functions.md#groups-function) est inclus dans le modèle de site de la communauté sélectionné.

Vous trouverez ci-dessous des liens vers des informations essentielles pour les composants, fonctions et fonctionnalités de Communities.

## Composants de base {#base-components}

* [Commentaires](essentials-comments.md)
* [Révisions](reviews-basics.md)
* [Tally](tally.md)

   * [Aimer](essentials-liking.md)
   * [Évaluation](rating-basics.md)
   * [Votant](essentials-voting.md)
   * *Sondage (n’est plus disponible)*

## Composants avec fonctions {#components-with-functions}

* [Flux d’activités](essentials-activities.md)
* [Affectations](essentials-assignments.md)
* [Blog](blog-developer-basics.md) ( `Journal`)

* [Calendrier](calendar-basics-for-developers.md)
* [Catalogue](catalog-developer-essentials.md)
* [Contenu proposé](essentials-featured.md)
* [Bibliothèque de fichiers](essentials-file-library.md)
* [Forum](essentials-forum.md)
* [Groupes](essentials-groups.md)
* [Conceptualisation](ideation.md)
* [Classement](leaderboard.md)
* [Questions et réponses](qna-essentials.md) `(QnA)`

## Fonctions {#features}

* [Bibliothèques clientes](clientlibs.md)
* [Sites de la communauté](sites-for-developers.md)
* [Événements OSGi des composants](events.md)
* [Chargement partiel des composants](sideloading.md)
* [Message](essentials-messaging.md)
* [Éditeur de texte enrichi](rte.md)
* [Notation et badges](configure-scoring.md)
* [Recherche](search-implementation.md)
* [Graphique des réseaux sociaux](essentials-socialgraph.md)
* [Fournisseur de ressources de stockage](srp-and-ugc.md) `(SRP)`

* [Balisage](tag.md)

## Javadocs {#javadocs}

Le [javadocs en ligne](../../help/sites-developing/reference-materials.md) reflètent les API disponibles dans la version 6.3 d’AEM.\
Les API Communities se trouvent dans `com.adobe.cq.social.*` modules.

Pour chaque [feature pack](deploy-communities.md#latestfeaturepack), un jar javadoc est disponible. Pour plus d’informations, voir [Utilisation de Maven pour Communities](maven.md#javadocs).

## Informations supplémentaires {#additional-information}

* [Structure des composants sociaux (SCF)](scf.md)

   * [Personnalisations côté client](client-customize.md)
   * [Personnalisations côté serveur](server-customize.md)
   * [Présentation du fournisseur de ressources de stockage](srp.md)

* [Consignes de codage](code-guide.md)
* [Tutoriels](tutorials.md)
* [Résolution des problèmes](troubleshooting.md)
