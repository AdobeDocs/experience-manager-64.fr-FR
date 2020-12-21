---
title: Fonctionnalité Flux d’activités
seo-title: Fonctionnalité Flux d’activités
description: Activités d'un membre de la communauté inscrit
seo-description: Activités d'un membre de la communauté inscrit
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 32%

---


# Fonctionnalité Flux d’activités {#activity-streams-feature}

## Présentation {#introduction}

Les activités d&#39;un membre de la communauté connecté, comme la publication sur un forum ou un blog, sont collectées dans un flux qui peut être filtré et affiché de différentes manières via la configuration du composant `Activity Streams`.

La possibilité de suivi ajoute une autre vue des activités lorsque des membres de la communauté suivent des publications d’intérêt ou suivent les activités d’autres membres de la communauté.

Cette section de la documentation décrit :

* Ajouter le composant Flux d&#39;Activité à un site AEM
* Paramètres de configuration du composant Flux d’Activité

## Ajout de flux d’activités à une page {#adding-activity-streams-to-a-page}

Si vous souhaitez ajouter un composant `Activity Streams` à une page en mode création, utilisez l’explorateur de composants pour localiser

* `Communities / Activity Streams`

et faites-le glisser sur la page où des flux d’activités doivent apparaître.

Pour obtenir les informations nécessaires, consultez [Community Components Basics](basics.md).

Lorsque les [bibliothèques client requises](essentials-activities.md#essentials-for-client-side) sont incluses, c&#39;est ainsi que le composant `Activity Streams` apparaîtra :

![chlimage_1-195](assets/chlimage_1-195.png)

## Configuration du composant Flux d’activités {#configuring-activity-streams}

Sélectionnez le composant `Activity Streams` placé auquel accéder et sélectionnez l&#39;icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-196](assets/chlimage_1-196.png)

Dans l’onglet **[!UICONTROL Activités de l’utilisateur]**, spécifiez les activités à afficher :

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Nombre maximal d&#39;]**
activitésNombre d&#39;activités à afficher
* **[!UICONTROL Chemin d’accès aux ressources de flux]** Laissez ce champ vide pour qu’il adopte par défaut le site ou le groupe de la communauté. Le chemin d’accès aux ressources de flux identifie la source des activités. Par défaut, ce champ est vide.
* **[!UICONTROL Afficher la vue Activités de l’utilisateur]** Si cette option est cochée, la page des activités inclut un onglet qui filtre les activités en fonction des activités générées au sein de la communauté par le membre actuel. Cette option est cochée par défaut.
* **[!UICONTROL Afficher toutes les Activités]**
AfficherSi cette option est cochée, la page activités comprend un onglet qui comprend toutes les activités générées au sein de la communauté à laquelle le membre actuel a accès. Cette option est cochée par défaut.
* **[!UICONTROL Afficher après la]**
vue Si cette option est cochée, la page activités comprend un onglet qui filtres les activités en fonction de celles que suit le membre actuel. Cette option est cochée par défaut.

## Vue suivante {#following-view}

Les composants doivent être configurés pour activer les éléments suivants. Les fonctionnalités qui permettent ce qui suit sont [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendar](calendar.md), [filelibrary](file-library.md) et [commentaires](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

Le bouton **Suivre** permet de suivre les entrées en tant qu&#39;activités, [notifications](notifications.md) et/ou [abonnements](subscriptions.md). Chaque fois que le bouton **Suivre** est sélectionné, il est possible d&#39;activer ou de désactiver une sélection. La sélection `Email Subscriptions` n&#39;est présente que lorsqu&#39;elle est configurée.

Si une méthode de suivi est sélectionnée, le texte du bouton devient **Suivant**. Pour plus de commodité, il est possible de sélectionner `Unfollow All` pour désactiver toutes les méthodes.

Le bouton **Suivre** apparaît :

* Lors de l&#39;affichage du profil d&#39;un autre membre
* Sur une page de présentation principale, telle que les forums, la qualité de vie et les blogs
   * Suit toutes les activités de cette fonction générale

* Pour une entrée spécifique, telle qu’un sujet de forum, une question QnA ou un article de blog
   * Suit toutes les activités de cette entrée spécifique

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur les flux d’activités](essentials-activities.md) du développeur.
