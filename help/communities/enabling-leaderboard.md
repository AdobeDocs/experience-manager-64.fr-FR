---
title: Fonctionnalité du tableau de bord
seo-title: Fonctionnalité du tableau de bord
description: Ajouter un composant de tableau de bord à une page
seo-description: Ajouter un composant de tableau de bord à une page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
translation-type: tm+mt
source-git-commit: 1bbd917ef20c4a618e93af66ffe8a6cfc8448e78
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 18%

---


# Fonctionnalité du tableau de bord {#leaderboard-feature}

## Présentation {#introduction}

Le composant `Leaderboard` permet d&#39;obtenir une idée de la façon dont les membres interagissent au sein de la communauté en classant les membres en fonction des points gagnés (note de base) ou de leur expertise (note avancée).

Avant d’inclure le composant Leadboard sur une page, il est nécessaire de configurer [le score des communautés et les badges](implementing-scoring.md).

Cette section de la documentation décrit :

* Ajouter le composant `Leaderboard` à un [site communautaire](overview.md#community-sites)

* Paramètres de configuration du composant `Leaderboard`

## Ajouter un tableau de bord à une page {#adding-a-leaderboard-to-a-page}

Pour ajouter un composant `Leaderboard` à une page en mode création, recherchez le composant.

* `Communities / Leaderboard`

et faites-le glisser sur la page.

Pour obtenir les informations nécessaires, consultez [Community Components Basics](basics.md).

Placé pour la première fois sur une page d’un site de communauté, voici à quoi ressemble le composant :

![chlimage_1-8](assets/chlimage_1-8.png)

## Configuration de Leaderboard {#configuring-leaderboard}

Sélectionnez le composant `Leaderboard` placé auquel accéder et sélectionnez l&#39;icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Onglet Settings {#settings-tab}

Sous l&#39;onglet **[!UICONTROL Paramètres]**, indiquez les informations relatives au membre qui s&#39;affichent :

* **[!UICONTROL Nom]**
d’affichageNom descriptif à afficher pour le panorama, reflétant les règles sélectionnées pour l’affichage des badges et des scores.

   La valeur par défaut est `Leaderboard`, si rien n’est saisi.

* ****
BadgeSi cette case est cochée, une colonne pour les icônes de badge est incluse dans le tableau de bord.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Nom du]**
badgeSi cette case est cochée, une colonne correspondant au nom du badge est incluse dans le tableau de bord.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Utiliser]**
AvatarSi cette case est cochée, l&#39;avatar du membre est inclus dans le tableau de bord, en regard du lien de son nom vers son profil membre.

   Cette option n’est pas cochée par défaut.

### Onglet Règles {#rules-tab}

Sous l&#39;onglet **[!UICONTROL Règles]**, le site communautaire et ses règles de notation et de badge

* **[!UICONTROL Emplacement]**
 de la règle (requis) Emplacement où la règle Scoring/Badging est configurée.

* **[!UICONTROL Règle]**
 de score (obligatoire) Règle spécifique générant les scores à afficher.

* **[!UICONTROL Règle]**
 de badge (obligatoire) Règle spécifique générant le badge à afficher.

* **[!UICONTROL Afficher]**
LimitNombre de membres à afficher par page.

   La valeur par défaut est 10.

## Exemple : Tableau de bord des participants {#example-participants-leaderboard}

Ce tableau de bord indique les résultats de l’application des règles de notation de base.

Configuration du composant de tableau de bord :

* **[!UICONTROL Onglet Settings:]**

   * Nom d’affichage = `Participation Board`
   * `checked` :

      * Badge
      * Nom du badge
      * Utiliser un avatar

* **** Onglet Règles :

   * Emplacement des règles = `/content/sites/communities/jcr:content`
   * Règle de notation = `/etc/community/scoring/rules/forums-scoring`
   * Règle d’attribution des badges = `/etc/community/badging/rules/reference-badging`
   * Limite d’affichage = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Exemple : Tableau de bord des experts {#example-experts-leaderboard}

Ce tableau de bord indique les résultats de l’application de règles de notation avancées.

Configuration du composant de tableau de bord :

* **[!UICONTROL Onglet Settings:]**

   * Nom d’affichage = `Expertise Board`
   * `checked` :

      * Badge
      * Utiliser un avatar

* **** Onglet Règles :

   * Emplacement des règles = `/content/sites/communities/jcr:content`
   * Règle de notation = `/etc/community/scoring/rules/adv-forums-scoring`
   * Règle d’attribution des badges = `/etc/community/badging/rules/adv-forums-badging`
   * Limite d’affichage = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Informations supplémentaires {#additional-information}

Pour plus d&#39;informations, consultez la page [Leaderboard Essentials](leaderboard.md) destinée aux développeurs.

Les instructions de création de règles sont fournies sur la page [Scores et badges des communautés](implementing-scoring.md) à l’intention des administrateurs.
