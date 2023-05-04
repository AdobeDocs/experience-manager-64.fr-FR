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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 3%

---

# Fonctionnalité Flux d’activités {#activity-streams-feature}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Les activités d’un membre de la communauté connecté, comme la publication sur un forum ou un blog, sont regroupées dans un flux qui peut être filtré et affiché de différentes manières via la configuration de la fonction `Activity Streams` composant.

La possibilité de suivre ajoute une autre vue des activités lorsque les membres de la communauté suivent des messages d’intérêt ou suivent les activités d’autres membres de la communauté.

Cette section de la documentation décrit

* Ajout du composant Flux d’activités à un site AEM
* Paramètres de configuration du composant Flux d’activités

## Ajout de flux d’activités à une page {#adding-activity-streams-to-a-page}

Si vous souhaitez ajouter une `Activity Streams` sur une page en mode création, utilisez l’explorateur de composants pour accéder à

* `Communities / Activity Streams`

et faites-le glisser sur la page où les flux d’activités doivent apparaître.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-activities.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Activity Streams` apparaît :

![chlimage_1-195](assets/chlimage_1-195.png)

## Configuration des flux d’activités {#configuring-activity-streams}

Sélectionnez le `Activity Streams` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-196](assets/chlimage_1-196.png)

Sous , **[!UICONTROL Activités utilisateurs]** , définissez les activités à afficher :

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Nombre max. d’activités]**
Le nombre d’activités à afficher
* **[!UICONTROL Chemin de la ressource de diffusion]**
Laissez ce champ vide par défaut pour le site de la communauté ou le groupe de la communauté. Le chemin d’accès à la ressource de flux identifie la source des activités. La valeur par défaut est vide.
* **[!UICONTROL Afficher la vue des activités utilisateur]**
si cette case est cochée, la page activités comprend un onglet qui filtre les activités en fonction de celles générées au sein de la communauté par le membre actuel. La valeur par défaut est cochée.
* **[!UICONTROL Afficher la vue Toutes les activités]**
Si cette case est cochée, la page des activités comporte un onglet qui inclut toutes les activités générées au sein de la communauté auxquelles le membre actuel a accès. La valeur par défaut est cochée.
* **[!UICONTROL Afficher la vue suivante]**
Si cette case est cochée, la page Activités comprend un onglet qui filtre les activités en fonction de celles que le membre actuel suit. La valeur par défaut est cochée.

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

Vous trouverez plus d’informations sur la [Notions fondamentales sur les flux d’activités](essentials-activities.md) pour les développeurs.
