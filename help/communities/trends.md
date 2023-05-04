---
title: Tendances des activités
seo-title: Activity Trends
description: Ajout d’un composant Liste d’activités de la communauté à une page
seo-description: Adding a Community Activity List component to a page
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 8%

---

# Tendances des activités {#activity-trends}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Le `Community Activity List` offre la possibilité d’ajouter des informations de tendance concernant les publications et les vues par les membres, ainsi que les publications et les vues de contenu.

Cette section de la documentation décrit

* Ajouter le `Community Activity List` en un composant [site communautaire](overview.md#community-sites)

* Paramètres de configuration de la variable `Community Activity List` component

## Condition requise {#requirement}

Données pour la variable `Community Activity List` n’est disponible que si Adobe Analytics est sous licence et configuré pour le site de la communauté.

Voir [Configuration d’Analytics pour les fonctionnalités des communautés](analytics.md).

## Ajout d’une liste d’activités de la communauté à une page {#adding-a-community-activity-list-to-a-page}

Pour ajouter une `Community Activity List` à une page en mode création, recherchez le composant. `Communities / Community Activity List` et faites-le glisser sur la page.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsqu’il est placé pour la première fois sur une page d’un site de communauté, voici comment le composant apparaît :

![chlimage_1-227](assets/chlimage_1-227.png)

## Configuration de la liste des activités de la communauté  {#configuring-community-activity-list}

Sélectionnez le `Community Activity List` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-228](assets/chlimage_1-228.png)

Sous , **[!UICONTROL Commentaires]** , indiquez si et comment les commentaires des fichiers chargés apparaissent :

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Type]**

   Indiquez s’il faut afficher les données concernant les membres de la communauté ou le contenu généré par l’utilisateur.

   Sélectionner parmi
   * `Members`
   * `Content`

   La valeur par défaut est `Members`.

* **[!UICONTROL Titre affiché]**

   Titre descriptif à afficher au-dessus des données, tel que `Trending Content`.

   La valeur par défaut n’est pas le titre.

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

   La valeur par défaut est l’ensemble du site de la communauté.

* **[!UICONTROL Agrégation du nombre de membres]**

   Lorsque cette option est désactivée, seules les publications de niveau supérieur sont comptabilisées. Par exemple, si le contexte est la page racine (valeur par défaut), une `Activity Type`de `Posts`n’affichera jamais d’activité, car il n’est pas possible de publier du contenu sur la page racine. Lorsque cette case est cochée, les décomptes de toutes les pages descendantes sont inclus.

   La valeur par défaut est cochée.

## Exemple de page avec 4 composants {#example-page-with-components}

**Meilleurs visiteurs** config : Type = Membres, Type d’activité = Vues

**Principaux contributeurs** config : Type = Membres, Type d’activité = Publications

**Contenu principal** config : Type = Contenu, Type d’activité = Vues,

**Contenu de tendance** config : Type = Contenu, Type d’activité = Publications

![chlimage_1-230](assets/chlimage_1-230.png)
