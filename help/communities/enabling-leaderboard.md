---
title: Fonctionnalité de classement
seo-title: Leaderboard Feature
description: Ajout d’un composant Leaderboard à une page
seo-description: Adding a Leaderboard component to a page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 9%

---

# Fonctionnalité de classement {#leaderboard-feature}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Le `Leaderboard` composant permet d’obtenir une idée de la façon dont les membres interagissent au sein de la communauté en classant les membres en fonction des points gagnés (notation de base) ou de leur expertise (notation avancée).

Avant d’inclure le composant de classement sur une page, il est nécessaire de configurer [Notation et badges des communautés](implementing-scoring.md).

Cette section de la documentation décrit

* Ajouter le `Leaderboard` en un composant [site communautaire](overview.md#community-sites)

* Paramètres de configuration de la variable `Leaderboard` component

## Ajout d’un panneau de classement à une page {#adding-a-leaderboard-to-a-page}

Pour ajouter une `Leaderboard` à une page en mode création, recherchez le composant.

* `Communities / Leaderboard`

et faites-le glisser sur la page.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsqu’il est placé pour la première fois sur une page d’un site de communauté, voici comment le composant apparaît :

![chlimage_1-8](assets/chlimage_1-8.png)

## Configuration du tableau de classement {#configuring-leaderboard}

Sélectionnez le `Leaderboard` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Onglet Paramètres {#settings-tab}

Sous , **[!UICONTROL Paramètres]** , indiquez les informations relatives au membre qui s’affichent :

* **[!UICONTROL Nom d’affichage]**
Nom descriptif à afficher pour le panorama, reflétant les règles sélectionnées pour l’affichage des badges et des scores.

   La valeur par défaut est `Leaderboard`, si rien n’est entré.

* **[!UICONTROL Badge]**
Si cette case est cochée, une colonne pour les icônes de badge est incluse dans le tableau de classement.

   La case par défaut est décochée.

* **[!UICONTROL Nom du badge]**
Si cette case est cochée, une colonne correspondant au nom du badge est incluse dans le tableau de classement.

   La case par défaut est décochée.

* **[!UICONTROL Utiliser l’avatar]**
Si cette case est cochée, l’avatar du membre est inclus dans le tableau de classement, en regard du lien de son nom vers son profil de membre.

   La case par défaut est décochée.

### Onglet Règles {#rules-tab}

Sous , **[!UICONTROL Règles]** , le site de la communauté et ses règles de notation et de badge

* **[!UICONTROL Emplacement des règles]**
(obligatoire) Emplacement où la règle de notation/attribution de badges est configurée.

* **[!UICONTROL Règle de notation]**
(obligatoire) règle spécifique générant les scores à afficher.

* **[!UICONTROL Règle de badge]**
(obligatoire) règle spécifique générant le badge à afficher.

* **[!UICONTROL Limite d’affichage]**
Nombre de membres à afficher par page.

   La valeur par défaut est 10.

## Exemple : Tableau de bord des participants {#example-participants-leaderboard}

Ce tableau de classement indique les résultats de l’application de règles de notation de base.

Configuration des composants de classement :

* **[!UICONTROL Paramètres]** tab :

   * Nom d’affichage = `Participation Board`
   * `checked` :

      * Badge
      * Nom du badge
      * Utiliser l’avatar

* **[!UICONTROL Règles]** tab :

   * Emplacement des règles = `/content/sites/communities/jcr:content`
   * Règle de notation = `/etc/community/scoring/rules/forums-scoring`
   * Règle d’attribution des badges = `/etc/community/badging/rules/reference-badging`
   * Limite d’affichage = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Exemple : Tableau de bord des experts {#example-experts-leaderboard}

Ce tableau de classement indique les résultats de l’application de règles de notation avancées.

Configuration des composants de classement :

* **[!UICONTROL Paramètres]** tab :

   * Nom d’affichage = `Expertise Board`
   * `checked` :

      * Badge
      * Utiliser l’avatar

* **[!UICONTROL Règles]** tab :

   * Emplacement des règles = `/content/sites/communities/jcr:content`
   * Règle de notation = `/etc/community/scoring/rules/adv-forums-scoring`
   * Règle d’attribution des badges = `/etc/community/badging/rules/adv-forums-badging`
   * Limite d’affichage = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales relatives au tableau de bord](leaderboard.md) pour les développeurs.

Les instructions de création de règles sont fournies sur la page [Notation et badges des communautés](implementing-scoring.md) pour les administrateurs.
