---
title: Notifications de communautés
seo-title: Communities Notifications
description: AEM Communities comporte des notifications qui affichent des événements présentant un intérêt pour le membre de la communauté connecté
seo-description: AEM Communities has notifications that display events of interest to the signed-in community member
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 3%

---

# Notifications de communautés {#communities-notifications}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

AEM Communities fournit une section de notifications qui affiche les événements d’intérêt pour les membres de la communauté connectés.

Les notifications sont similaires à [activités](essentials-activities.md) et [subscriptions](subscriptions.md) comme résultat

* Le membre qui publie du contenu
* Le membre qui choisit de suivre un autre membre
* Le membre choisit de suivre des rubriques, des articles et d’autres threads de contenu spécifiques.

Ce qui distingue les notifications des activités et des abonnements est

* Un lien vers la section des notifications est toujours présent dans l’en-tête d’un site de la communauté.
   * Les activités requièrent la [fonction de flux d’activités](functions.md#activity-stream-function) être inclus dans la structure du site de la communauté ;
   * Abonnements requis [configuration de l&#39;email](email.md)
* La mise en oeuvre des notifications s’effectue par le biais de canaux évolutives et enfichables.
   * Les activités ne sont disponibles que sur le web
   * Les abonnements ne sont disponibles que par email.

À partir des communautés [FP1](deploy-communities.md#latestfeaturepack), les canaux de notification disponibles sont

* Le canal web, accessible à l’aide du `Notifications` link
* Canal email, disponible lorsque l&#39;email est correctement configuré

Les futurs canaux seront mobiles et de bureau.

### Conditions requises {#requirements}

**Configurer le courrier électronique**

Pour que les notifications soient fonctionnelles, le canal Email doit être configuré.

Pour obtenir des instructions sur la configuration du courrier électronique, voir [Configuration du courrier électronique](analytics.md).

**Enable Follow**

Les composants doivent être configurés pour activer les éléments suivants. Les fonctionnalités qui permettent les suivantes sont [blog](blog-feature.md), [forum](forum.md), [Q&amp;R](working-with-qna.md), [calendar](calendar.md), [filelibrary](file-library.md), et [commentaires](comments.md).

Notez que

* Composants utilisés dans la communauté [modèles de site](sites.md) et [modèles de groupe](tools-groups.md) peut déjà être configuré pour autoriser ce qui suit

* Les profils de membre sont déjà configurés pour permettre aux autres membres de suivre

## Notifications de suivi {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

Le **Suivez** permet de suivre les entrées sous forme d’activités, d’abonnements et/ou de notifications. Chaque fois que la fonction **Suivez** est sélectionné, il est possible d’activer ou de désactiver une sélection. Le `Email Subscriptions` n’est présente que lorsqu’elle est configurée.

Si l’une des méthodes suivantes est sélectionnée, le texte du bouton devient **Suivre**. Pour des raisons pratiques, il est possible de sélectionner `Unfollow All` pour désactiver toutes les méthodes.

Le **Suivez** apparaît

* Lors de l’affichage du profil d’un autre membre
* Sur une page principale, telle que les forums, les Q&amp;R et les blogs
   * Suit toutes les activités pour cette fonction générale
* Pour une entrée spécifique, telle qu’un sujet de forum, une question Q&amp;R ou un article de blog.
   * Suit toutes les activités pour cette entrée spécifique

## Gestion des paramètres de notification {#managing-notification-settings}

En sélectionnant le lien Paramètres de notification sur la page Notifications, chaque membre peut gérer le mode de réception des notifications.

Le canal web est toujours activé.

![chlimage_1-255](assets/chlimage_1-255.png)

Le canal Email, qui repose sur les [configuration de l&#39;email](email.md), fournit les mêmes paramètres que pour le canal web.

Le canal email est désactivé par défaut.

![chlimage_1-256](assets/chlimage_1-256.png)

Il peut être activé par un membre, mais dépend toujours de la configuration de l&#39;email.

![chlimage_1-257](assets/chlimage_1-257.png)

## Affichage des notifications {#viewing-notifications}

### Notifications web {#web-notifications}

A [assistant création de site de communauté](sites-console.md) comprend désormais un lien vers la variable `Notifications` dans la barre d’en-tête du site au-dessus de la bannière. Contrairement aux messages, les notifications sont créées pour chaque site de la communauté, tandis que les messages doivent être activés pendant le processus de création du site.

Lorsque vous visitez le site publié, sélectionnez la variable `Notifications` affiche toutes les notifications du membre.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notifications par e-mail {#email-notifications}

Lorsque le canal Email est activé, le membre reçoit un email contenant un lien vers le contenu sur le web.

![chlimage_1-259](assets/chlimage_1-259.png)
