---
title: Fonctionnalité Flux d’activités
seo-title: Activity Streams Feature
description: Activités d’un membre de la communauté connecté
seo-description: Activities of a signed-in community member
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 32%

---

# Fonctionnalité Flux d’activités {#activity-streams-feature}

## Présentation {#introduction}

Les activités d’un membre de la communauté connecté, comme la publication sur un forum ou un blog, sont regroupées dans un flux qui peut être filtré et affiché de différentes manières via la configuration de la fonction `Activity Streams` composant.

La possibilité de suivi ajoute une autre vue des activités lorsque des membres de la communauté suivent des publications d’intérêt ou suivent les activités d’autres membres de la communauté.

Cette section de la documentation décrit :

* Ajout du composant Flux d’activités à un site AEM
* Paramètres de configuration du composant Flux d’activités

## Ajout de flux d’activités à une page {#adding-activity-streams-to-a-page}

Si vous souhaitez ajouter une `Activity Streams` sur une page en mode création, utilisez l’explorateur de composants pour accéder à

* `Communities / Activity Streams`

et faites-le glisser sur la page où des flux d’activités doivent apparaître.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-activities.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Activity Streams` apparaît :

![chlimage_1-195](assets/chlimage_1-195.png)

## Configuration du composant Flux d’activités {#configuring-activity-streams}

Sélectionnez le `Activity Streams` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-196](assets/chlimage_1-196.png)

Dans l’onglet **[!UICONTROL Activités de l’utilisateur]**, spécifiez les activités à afficher :

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Nombre max. d’activités]**
Le nombre d’activités à afficher
* **[!UICONTROL Chemin d’accès aux ressources de flux]** Laissez ce champ vide pour qu’il adopte par défaut le site ou le groupe de la communauté. Le chemin d’accès aux ressources de flux identifie la source des activités. Par défaut, ce champ est vide.
* **[!UICONTROL Afficher la vue Activités de l’utilisateur]** Si cette option est cochée, la page des activités inclut un onglet qui filtre les activités en fonction des activités générées au sein de la communauté par le membre actuel. Cette option est cochée par défaut.
* **[!UICONTROL Afficher la vue Toutes les activités]**
Si cette case est cochée, la page des activités comporte un onglet qui inclut toutes les activités générées au sein de la communauté auxquelles le membre actuel a accès. Cette option est cochée par défaut.
* **[!UICONTROL Afficher la vue suivante]**
Si cette case est cochée, la page Activités comprend un onglet qui filtre les activités en fonction de celles que le membre actuel suit. Cette option est cochée par défaut.

## Vue suivante {#following-view}

Les composants doivent être configurés pour activer les éléments suivants. Les fonctionnalités qui permettent les suivantes sont [blog](blog-feature.md), [forum](forum.md), [Q&amp;R](working-with-qna.md), [calendar](calendar.md), [filelibrary](file-library.md), et [commentaires](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

Le **Suivez** permet de suivre les entrées en tant qu’activités, [notifications](notifications.md), et/ou [subscriptions](subscriptions.md). Chaque fois que la fonction **Suivez** est sélectionné, il est possible d’activer ou de désactiver une sélection. Le `Email Subscriptions` n’est présente que lorsqu’elle est configurée.

Si l’une des méthodes suivantes est sélectionnée, le texte du bouton devient **Suivre**. Pour des raisons pratiques, il est possible de sélectionner `Unfollow All` pour désactiver toutes les méthodes.

Le **Suivez** s’affiche :

* Lors de l’affichage du profil d’un autre membre
* Sur une page principale, telle que les forums, les Q&amp;R et les blogs
   * Suit toutes les activités pour cette fonction générale

* Pour une entrée spécifique, telle qu’un sujet de forum, une question Q&amp;R ou un article de blog.
   * Suit toutes les activités pour cette entrée spécifique

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur les flux d’activités](essentials-activities.md) du développeur.
