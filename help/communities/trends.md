---
title: Tendances d’activité
seo-title: Tendances d’activité
description: Ajout d’un composant Liste d’activités de la communauté à une page
seo-description: Ajout d’un composant Liste d’activités de la communauté à une page
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 29%

---

# Tendances d’activité {#activity-trends}

## Présentation {#introduction}

Le composant `Community Activity List` permet d’ajouter des informations de tendance concernant les publications et les vues par les membres, ainsi que les publications et les vues de contenu.

Cette section de la documentation décrit :

* Ajout du composant `Community Activity List` à un [site communautaire](overview.md#community-sites)

* Paramètres de configuration du composant `Community Activity List`

## Condition requise {#requirement}

Les données de `Community Activity List` ne sont disponibles que lorsque Adobe Analytics est sous licence et configuré pour le site de la communauté.

Voir [Configuration d’Analytics pour les fonctionnalités des communautés](analytics.md).

## Ajout d’une liste d’activités communautaires à une page {#adding-a-community-activity-list-to-a-page}

Pour ajouter un composant `Community Activity List` à une page en mode création, recherchez le composant `Communities / Community Activity List` et faites-le glisser sur la page.

Pour plus d’informations, voir [Principes de base des composants des communautés](basics.md).

Placé pour la première fois sur une page d’un site de communauté, voici à quoi ressemble le composant :

![chlimage_1-227](assets/chlimage_1-227.png)

## Configuration de la liste des activités de la communauté {#configuring-community-activity-list}

Sélectionnez le composant `Community Activity List` inséré pour y accéder et sélectionnez l’icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-228](assets/chlimage_1-228.png)

Dans l’onglet **[!UICONTROL Commentaires]**, indiquez si et comment les commentaires pour les fichiers transférés apparaissent :

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Type]**

   Indiquez s’il faut afficher les données concernant les membres de la communauté ou le contenu généré par l’utilisateur.

   Sélectionner parmi
   * `Members`
   * `Content`

   La valeur par défaut est `Members`.

* **[!UICONTROL Titre affiché]**

   Titre descriptif à afficher au-dessus des données, tel que `Trending Content`.

   Par défaut, il n’existe aucun titre.

* **[!UICONTROL Nombre d’affichages]**

   Nombre d’éléments à répertorier.

   La valeur par défaut est 10.

* **[!UICONTROL Type d’activité]**

   Sélectionnez l’un des
   * `Views`(visites de page)
   * `Posts`(création du contenu généré par l’utilisateur)
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

   Lorsque cette option est désactivée, seules les publications de niveau supérieur sont comptabilisées. Par exemple, si le contexte est la page racine (valeur par défaut), un `Activity Type`de `Posts`n’affichera jamais aucune activité, car il n’est pas possible de publier du contenu sur la page racine. Lorsque cette option est cochée, les nombres sur toutes les pages descendantes sont inclus.

   Cette option est cochée par défaut.

## Exemple de page avec 4 composants {#example-page-with-components}

**Principaux visiteurs** config : Type = Membres, Type d’activité = Vues

**Principaux** contributeurs config : Type = Membres, Type d’activité = Publications

**Top** Contentconfig : Type = Contenu, Type d’activité = Vues,

**Trending** Contentconfig : Type = Contenu, Type d’activité = Publications

![chlimage_1-230](assets/chlimage_1-230.png)
