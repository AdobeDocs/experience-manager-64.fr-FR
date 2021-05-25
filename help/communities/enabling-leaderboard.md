---
title: Fonctionnalité de classement
seo-title: Fonctionnalité de classement
description: Ajout d’un composant Leaderboard à une page
seo-description: Ajout d’un composant Leaderboard à une page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 18%

---

# Fonctionnalité du tableau de classement {#leaderboard-feature}

## Présentation {#introduction}

Le composant `Leaderboard` permet d’obtenir une idée de la façon dont les membres interagissent au sein de la communauté en classant les membres en fonction des points gagnés (notation de base) ou de leur expertise (notation avancée).

Avant d’inclure le composant de classement sur une page, il est nécessaire de configurer [Notation et badges des communautés](implementing-scoring.md).

Cette section de la documentation décrit :

* Ajout du composant `Leaderboard` à un [site communautaire](overview.md#community-sites)

* Paramètres de configuration du composant `Leaderboard`

## Ajout d’un tableau de classement à une page {#adding-a-leaderboard-to-a-page}

Pour ajouter un composant `Leaderboard` à une page en mode création, localisez le composant .

* `Communities / Leaderboard`

et faites-le glisser sur la page.

Pour plus d’informations, voir [Principes de base des composants des communautés](basics.md).

Placé pour la première fois sur une page d’un site de communauté, voici à quoi ressemble le composant :

![chlimage_1-8](assets/chlimage_1-8.png)

## Configuration de Leaderboard {#configuring-leaderboard}

Sélectionnez le composant `Leaderboard` inséré pour y accéder et sélectionnez l’icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Onglet Settings {#settings-tab}

Sous l’onglet **[!UICONTROL Paramètres]** , indiquez les informations relatives au membre qui s’affichent :

* **[!UICONTROL Nom d’affichage]**
Nom descriptif à afficher pour le panorama, reflétant les règles sélectionnées pour l’affichage des badges et des scores.

   La valeur par défaut est `Leaderboard`, si rien n’est renseigné.

* ****
BadgeSi cette option est cochée, une colonne pour les icônes de badge est incluse dans le tableau de classement.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Nom du]**
badge Si cette option est cochée, une colonne correspondant au nom du badge est incluse dans le tableau de classement.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Utiliser l’]**
avatarSi cette option est cochée, l’avatar du membre est inclus dans le tableau de classement, en regard du lien de son nom vers son profil de membre.

   Cette option n’est pas cochée par défaut.

### Onglet Règles {#rules-tab}

Sous l’onglet **[!UICONTROL Règles]**, le site de la communauté et ses règles de notation et de badge

* **[!UICONTROL Emplacement de la règle]**
 (obligatoire) Emplacement où la règle de notation/attribution de badges est configurée.

* **[!UICONTROL Règle de notation]**
 (obligatoire) règle spécifique générant les scores à afficher.

* **[!UICONTROL Règle de badge]**
 (obligatoire) Règle spécifique générant le badge à afficher.

* **[!UICONTROL Afficher la]**
limite Nombre de membres à afficher par page.

   La valeur par défaut est 10.

## Exemple : Tableau de bord des participants {#example-participants-leaderboard}

Ce tableau de classement indique les résultats de l’application de règles de notation de base.

Configuration des composants de classement :

* **[!UICONTROL Onglet Settings:]**

   * Nom d’affichage = `Participation Board`
   * `checked` :

      * Badge
      * Nom du badge
      * Utiliser l’avatar

* **** Onglet Règles :

   * Emplacement des règles = `/content/sites/communities/jcr:content`
   * Règle de notation = `/etc/community/scoring/rules/forums-scoring`
   * Règle d’attribution des badges = `/etc/community/badging/rules/reference-badging`
   * Limite d’affichage = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Exemple : Tableau de bord des experts {#example-experts-leaderboard}

Ce tableau de classement indique les résultats de l’application de règles de notation avancées.

Configuration des composants de classement :

* **[!UICONTROL Onglet Settings:]**

   * Nom d’affichage = `Expertise Board`
   * `checked` :

      * Badge
      * Utiliser l’avatar

* **** Onglet Règles :

   * Emplacement des règles = `/content/sites/communities/jcr:content`
   * Règle de notation = `/etc/community/scoring/rules/adv-forums-scoring`
   * Règle d’attribution des badges = `/etc/community/badging/rules/adv-forums-badging`
   * Limite d’affichage = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur le tableau de classement](leaderboard.md) pour les développeurs.

Les instructions de création de règles sont fournies sur la page [Notation et badges communautaires](implementing-scoring.md) pour les administrateurs.
