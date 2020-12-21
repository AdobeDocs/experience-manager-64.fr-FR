---
title: Tendances d’activité
seo-title: Tendances d’activité
description: Ajouter un composant Liste d'Activité communautaire à une page
seo-description: Ajouter un composant Liste d'Activité communautaire à une page
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 29%

---


# Tendances d’activité {#activity-trends}

## Présentation {#introduction}

Le composant `Community Activity List` permet d’ajouter des informations de tendance concernant les publications et les vues des membres, ainsi que les publications et les vues de contenu.

Cette section de la documentation décrit :

* Ajouter le composant `Community Activity List` à un [site communautaire](overview.md#community-sites)

* Paramètres de configuration du composant `Community Activity List`

## Condition requise {#requirement}

Les données de `Community Activity List` ne sont disponibles que lorsque Adobe Analytics est sous licence et configuré pour le site communautaire.

Voir [Configuration d’Analytics pour les fonctionnalités des communautés](analytics.md).

## Ajouter une Liste d&#39;Activité communautaire à une page {#adding-a-community-activity-list-to-a-page}

Pour ajouter un composant `Community Activity List` à une page en mode création, recherchez le composant `Communities / Community Activity List` et faites-le glisser sur sa place sur une page.

Pour obtenir les informations nécessaires, consultez [Community Components Basics](basics.md).

Placé pour la première fois sur une page d’un site de communauté, voici à quoi ressemble le composant :

![chlimage_1-227](assets/chlimage_1-227.png)

## Configuration de la Liste d&#39;Activité de la communauté {#configuring-community-activity-list}

Sélectionnez le composant `Community Activity List` placé auquel accéder et sélectionnez l&#39;icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-228](assets/chlimage_1-228.png)

Dans l’onglet **[!UICONTROL Commentaires]**, indiquez si et comment les commentaires pour les fichiers transférés apparaissent :

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Type]**

   Indiquez si les données relatives aux membres de la communauté ou au contenu généré par l’utilisateur doivent être affichées.

   Sélectionner dans
   * `Members`
   * `Content`

   La valeur par défaut est `Members`.

* **[!UICONTROL Titre affiché]**

   Titre descriptif à afficher au-dessus des données, tel que `Trending Content`.

   Par défaut, il n’existe aucun titre.

* **[!UICONTROL Nombre d’affichages]**

   Nombre d&#39;éléments à liste.

   La valeur par défaut est 10.

* **[!UICONTROL Type d’activité]**

   Sélectionnez l’un des
   * `Views`(visites de page)
   * `Posts`(création d’UGC)
   * `Follows`
   * `Likes`

   La valeur par défaut est Vues.

* **[!UICONTROL Période]**

   Sélectionnez l’un des
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   La valeur par défaut est `Total`.

* **[!UICONTROL Chemin d’accès au contexte]**

   Permet d’étendre l’activité à un sous-ensemble du site, tel qu’un blog spécifique.

   La valeur par défaut est le site de la communauté entier.

* **[!UICONTROL Agrégation du nombre de membres]**

   Si cette option est désactivée, seules les publications de niveau supérieur sont comptabilisées. Par exemple, si le contexte est la page racine (par défaut), un `Activity Type`de `Posts`n’affichera jamais aucune activité, car il n’est pas possible de publier du contenu sur la page racine. Lorsque cette option est cochée, les nombres sur toutes les pages descendantes sont inclus.

   Cette option est cochée par défaut.

## Exemple de page avec 4 composants {#example-page-with-components}

**Principaux visiteurs** config : Type = Membres, Type d’activité = Vues

**Top** Contributorsconfig : Type = Membres, type d’Activité = Publications

**Top** Contentconfig : Type = Contenu, type d&#39;Activité = Vues,

**Trending** Contentconfig : Type = Contenu, type d’Activité = Publications

![chlimage_1-230](assets/chlimage_1-230.png)
