---
title: Abonnements des communautés
seo-title: Communities Subscriptions
description: 'Les membres de la communauté interagissent avec d’autres membres par courrier électronique. '
seo-description: Community members interact with other members through email
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
role: Admin
exl-id: 8a756328-0405-49b7-b94d-3dd5a87c782a
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 2%

---

# Abonnements des communautés {#communities-subscriptions}

## Présentation {#overview}

À partir des communautés [FP1](deploy-communities.md#latestfeaturepack), les membres de la communauté peuvent interagir avec la communauté par courrier électronique à l’aide d’une fonctionnalité appelée abonnements.

Les abonnements sont similaires aux [notifications](notifications.md) Les membres peuvent s’abonner lorsqu’ils suivent des articles de blog, des sujets de forum ou des questions Q&amp;R.

Ce qui distingue les abonnements des notifications est :

* Les membres ne peuvent pas s’abonner lorsqu’ils suivent d’autres membres
* La seule action que les membres peuvent effectuer est de sélectionner `Email Subscriptions` lorsque
* Lorsque la réponse par courrier électronique est configurée, les membres peuvent effectivement publier du contenu en répondant simplement au courrier électronique reçu.

### Conditions requises {#requirements}

**Configurer le courrier électronique**

L&#39;email doit être paramétré pour que les abonnements soient fonctionnels et que les membres puissent répondre par email.

Pour obtenir des instructions sur la configuration du courrier électronique, voir [Configuration du courrier électronique](email.md).

**Activation des abonnements et suivez**

Les composants doivent être configurés pour activer les abonnements. *et* suivant . Fonctionnalités qui autorisent les abonnements : [blog](blog-feature.md), [forum](forum.md) et [Q&amp;R](working-with-qna.md).

## Abonnements à partir de {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

Le **Suivez** permet de suivre les entrées sous forme d’activités, d’abonnements et/ou de notifications. Chaque fois que la fonction **Suivez** est sélectionné, il est possible d’activer ou de désactiver une sélection.

Si l’une des méthodes suivantes est sélectionnée, le texte du bouton devient **Suivre**. Pour des raisons pratiques, il est possible de sélectionner `Unfollow All` pour désactiver toutes les méthodes.

Le **Suivez** inclut le bouton `Email Subscriptions` n’est disponible que lorsqu’un forum, QnA ou blog est configuré pour activer les abonnements aux emails. Ce bouton s’affiche.

* Sur la page principale des fonctionnalités du forum activé, de la qualité de service ou du blog

   * Envoie un courrier électronique pour toutes les activités sous cette fonctionnalité.

* Pour une entrée spécifique, telle qu’un sujet de forum, une question Q&amp;R ou un article de blog.

   * Envoie un courrier électronique lorsqu’il y a une activité pour cette entrée spécifique.

## Répondre par email {#reply-by-email}

Lorsque le courrier électronique est [configuré pour répondre par email](email.md#configure-polling-importer), le membre qui s’est abonné recevra un email avec le contenu publié et un lien vers le contenu en ligne.

S&#39;ils répondent à l&#39;email, le contenu qu&#39;ils saisissent dans la réponse apparaîtra en ligne.

![chlimage_1-6](assets/chlimage_1-6.png)

Le temps nécessaire à la publication d’une réponse est contrôlé par la variable [intervalle de mise à jour de l’importateur d’interrogations](email.md#configure-polling-importer).

![chlimage_1-7](assets/chlimage_1-7.png)
