---
title: Notifications des communautés
seo-title: Notifications des communautés
description: AEM Communities dispose de notifications qui affichent les événements d'intérêt pour le membre de la communauté connecté
seo-description: AEM Communities dispose de notifications qui affichent les événements d'intérêt pour le membre de la communauté connecté
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 2%

---


# Notifications des communautés {#communities-notifications}

## Présentation {#overview}

AEM Communities fournit une section de notifications qui affiche les événements d’intérêt pour les membres de la communauté connectés.

Les notifications sont similaires aux [activités](essentials-activities.md) et aux [abonnements](subscriptions.md) qui peuvent provenir de

* Le membre qui publie du contenu
* Le membre qui choisit de suivre un autre membre
* Le membre choisissant de suivre des rubriques spécifiques, des articles et d&#39;autres threads de contenu

Ce qui distingue les notifications des activités et des abonnements est

* Un lien vers la section des notifications est toujours présent dans l’en-tête d’un site communautaire.
   * Les Activités exigent que la fonction [de flux d&#39;](functions.md#activity-stream-function) activité soit incluse dans la structure du site communautaire.
   * Les Abonnements nécessitent [la configuration des courriers électroniques](email.md)
* La mise en oeuvre des notifications s’effectue au moyen de canaux évolutives et enfichables.
   * Les Activités ne sont disponibles que sur le Web
   * Les Abonnements ne sont disponibles que par courrier électronique

À compter du [FP1](deploy-communities.md#latestfeaturepack)des Communautés, les canaux de notification disponibles sont

* canal Web, accessible à l’aide du `Notifications` lien
* Le canal de messagerie, disponible lorsque le courrier électronique est correctement configuré

Les futurs canaux sont mobiles et de bureau.

### Conditions requises {#requirements}

**Configurer le courrier électronique**

Le courrier électronique doit être configuré pour que le canal de courrier électronique pour que les notifications fonctionnent.

Pour obtenir des instructions sur la configuration du courrier électronique, voir [Configuration du courrier électronique](analytics.md).

**Activer le suivi**

Les composants doivent être configurés pour activer les éléments suivants. Les fonctionnalités qui permettent ce qui suit sont [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendar, filelibrary et les commentaires.](calendar.md)[](file-library.md)[](comments.md)

Notez que

* Les composants utilisés dans les modèles [de](sites.md) site de la communauté et les modèles [de](tools-groups.md) groupe peuvent déjà être configurés pour autoriser les éléments suivants

* Les profils membres sont déjà configurés pour permettre aux autres membres de suivre

## Notifications de suivi {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

Le bouton **Suivre** permet de suivre les entrées comme activités, abonnements et/ou notifications. Chaque fois que le bouton **Suivre** est sélectionné, il est possible d’activer ou de désactiver une sélection. La `Email Subscriptions` sélection n’est présente que lorsqu’elle est configurée.

Si une méthode de suivi est sélectionnée, le texte du bouton devient **Suivant**. Pour plus de commodité, il est possible de choisir `Unfollow All` de désactiver toutes les méthodes.

Le bouton **Suivre** apparaît.

* Lors de l&#39;affichage du profil d&#39;un autre membre
* Sur une page de présentation principale, telle que les forums, la qualité de vie et les blogs
   * Suit toutes les activités de cette fonction générale
* Pour une entrée spécifique, telle qu’un sujet de forum, une question QnA ou un article de blog
   * Suit toutes les activités de cette entrée spécifique

## Gestion des paramètres de notification {#managing-notification-settings}

En sélectionnant le lien Paramètres de notification dans la page Notifications, chaque membre peut gérer le mode de réception des notifications.

Le canal Web est toujours activé.

![chlimage_1-255](assets/chlimage_1-255.png)

Le canal de messagerie électronique, qui repose sur une [configuration appropriée du courrier électronique](email.md), fournit les mêmes paramètres que pour le canal Web.

Le canal de messagerie est désactivé par défaut.

![chlimage_1-256](assets/chlimage_1-256.png)

Il peut être activé par un membre, mais dépend toujours de la configuration du courrier électronique.

![chlimage_1-257](assets/chlimage_1-257.png)

## Affichage des notifications {#viewing-notifications}

### Notifications Web {#web-notifications}

Un [assistant a créé un site](sites-console.md) communautaire et inclut désormais un lien vers la `Notifications` fonction dans la barre d’en-tête du site au-dessus de la bannière. Contrairement aux messages, les notifications sont créées pour chaque site de la communauté, tandis que les messages doivent être activés pendant le processus de création du site.

Lors de la visite du site publié, la sélection du `Notifications` lien affichera toutes les notifications pour le membre.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notifications par e-mail {#email-notifications}

Lorsque le canal de messagerie est activé, le membre reçoit un courrier électronique contenant un lien vers le contenu sur le Web.

![chlimage_1-259](assets/chlimage_1-259.png)

