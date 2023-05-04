---
title: Choisir votre interface utilisateur
seo-title: Selecting your UI
description: Configuration de l’interface que vous utiliserez pour travailler dans AEM
seo-description: Configure which interface you will use to work in AEM
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
exl-id: 415efbe0-95f5-4c9e-ac33-c4a384a8271e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 38%

---

# Choisir votre interface utilisateur{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation des interfaces utilisateur

L’environnement de création permet ce qui suit :

* [Création](/help/sites-authoring/author.md) (y compris [création de pages](/help/sites-authoring/author-environment-tools.md), [gestion des ressources](/help/assets/home.md), [communities](/help/communities/author-communities.md))

* [Administration](/help/sites-administering/home.md) des tâches nécessaires pour générer et gérer le contenu sur votre site Web

Pour ce faire, deux interfaces utilisateur graphiques sont fournies. Ils sont accessibles par n’importe quel navigateur moderne.

1. Interface utilisateur optimisée pour les écrans tactiles

   * Il s’agit de l’interface utilisateur d’AEM moderne par défaut.
   * Elle est principalement grise, avec une interface propre et plate.
   * Conçu pour être utilisé à la fois sur les appareils tactiles et les ordinateurs de bureau, l’apparence est identique sur tous les appareils, mais [affichage et sélection de vos ressources](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) diffère légèrement (appuyez par rapport aux clics).

      * Bureau :

   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * Tablettes (ou bureau de moins de 1024 pixels de large) :

   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. Interface utilisateur classique

   * Il s’agit de l’ancienne interface utilisateur qui est disponible dans AEM depuis de nombreuses années.
   * Elle est principalement verte.
   * Il a été conçu pour être utilisé sur des ordinateurs de bureau.
   * La documentation suivante porte sur l’interface utilisateur moderne. Pour plus d’informations sur la création dans l’interface utilisateur classique, voir [Documentation sur la création pour l’interface utilisateur classique](/help/sites-classic-ui-authoring/classicui.md).

   ![chlimage_1-232](assets/chlimage_1-232.png)

## Changement d’interface utilisateur

Bien que l’IU tactile soit désormais l’IU standard et [parité des fonctionnalités](../release-notes/touch-ui-features-status.md) a presque été atteint avec l’administration et la modification des sites, il peut arriver que l’utilisateur souhaite passer à la [IU classique](/help/sites-classic-ui-authoring/classicui.md). Il existe plusieurs options pour ce faire.

>[!NOTE]
>
>Pour plus d’informations sur le statut de parité des fonctionnalités avec l’IU classique, consultez le document [Parité des fonctionnalités de l’IU tactile](../release-notes/touch-ui-features-status.md).

Il existe différents emplacements où vous pouvez définir l’interface utilisateur à utiliser :

* [Configuration de l’IU par défaut pour votre instance](#configuring-the-default-ui-for-your-instance) - L’interface utilisateur par défaut sera définie lors de la connexion de l’utilisateur, bien que l’utilisateur puisse la remplacer et sélectionner une autre interface utilisateur pour son compte ou la session en cours.

* [Définition de la création d’interfaces utilisateur classiques pour votre compte](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account) - L’interface utilisateur sera définie comme valeur par défaut lors de la modification des pages, bien que l’utilisateur puisse remplacer cette valeur et sélectionner une autre interface utilisateur pour son compte ou la session en cours.

* [Passage à l’IU classique pour la session en cours](#switching-to-classic-ui-for-the-current-session) - Cette option passe à l’IU classique pour la session en cours.

* Pour le cas de [création de pages Le système effectue certains remplacements dans la relation avec l’interface utilisateur](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Plusieurs options permettant de passer à l’IU classique ne sont pas immédiatement disponibles clé en main. Elles doivent être configurées spécifiquement pour votre instance.
>
>Pour plus d’informations, reportez-vous à la section [Activation de l’accès à l’IU classique](/help/sites-administering/enable-classic-ui.md).

>[!NOTE]
>
>Les instances mises à niveau à partir d’une version précédente conservent l’IU classique pour la création de pages.
>
>Après la mise à niveau, la création de pages ne bascule pas automatiquement vers l’IU tactile. Vous pouvez cependant configurer ce basculement à l’aide de la [configuration OSGi](/help/sites-deploying/configuring-osgi.md) du **service Mode d’IU de création de la gestion de contenu web** (service `AuthoringUIMode`). Consultez la section [IU par défaut en fonction de l’éditeur](#ui-overrides-for-the-editor).

## Configuration de l’interface utilisateur par défaut pour votre instance {#configuring-the-default-ui-for-your-instance}

Un administrateur système peut configurer l’interface utilisateur qui s’affiche au démarrage et lors de la connexion à l’aide de [Mappage racine](/help/sites-deploying/osgi-configuration-settings.md).

Il peut être remplacé par les paramètres par défaut de l’utilisateur ou les paramètres de session.

## Définition de la création d’interfaces utilisateur classiques pour votre compte {#setting-classic-ui-authoring-for-your-account}

Chaque utilisateur peut accéder à ses [préférences utilisateur](/help/sites-authoring/user-properties.md) pour définir s’il souhaite utiliser l’IU classique pour la création de pages (au lieu de l’IU par défaut).

Il peut être remplacé par les paramètres de session.

## Passage à l’IU classique pour la session en cours {#switching-to-classic-ui-for-the-current-session}

Ainsi, si l’IU tactile est activée sur un ordinateur de bureau, les utilisateurs peuvent souhaiter revenir à l’IU classique (ordinateur de bureau uniquement). Plusieurs méthodes permettent de basculer vers l’IU classique pour la session en cours :

* **Liens de navigation**

   >[!CAUTION]
   >
   >Cette option permettant de passer à l’IU classique n’est pas immédiatement disponible, elle doit être configurée spécifiquement pour votre instance.
   >
   >
   >Pour plus d’informations, reportez-vous à la section [Activation de l’accès à l’IU classique](/help/sites-administering/enable-classic-ui.md).

   Si cette option est activée, lorsque vous faites passer le pointeur de la souris sur une console appropriée, une icône s’affiche (symbole d’écran). En appuyant ou cliquant sur cette dernière, vous accédez à l’emplacement correspondant dans l’IU classique.

   Par exemple, les liens de **Sites** à **siteadmin** :

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   Pour accéder à l’IU classique, utilisez l’URL de l’écran d’accueil à l’adresse `welcome.html`. Par exemple :

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >L’IU tactile est accessible via `sites.html`. Par exemple :
   >
   >
   >`http://localhost:4502/sites.html`

### Activation de l’IU classique en cours de modification de page {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>Cette option permettant de passer à l’IU classique n’est pas immédiatement disponible, elle doit être configurée spécifiquement pour votre instance.
>
>Pour plus d’informations, reportez-vous à la section [Activation de l’accès à l’IU classique](/help/sites-administering/enable-classic-ui.md).

Si cette option est activée, l’option **Ouvrir l’IU classique** est disponible dans la boîte de dialogue **Informations sur la page** :

![chlimage_1-49](assets/chlimage_1-49.png)

### Remplacements de l’interface utilisateur de l’éditeur {#ui-overrides-for-the-editor}

Les paramètres définis par un utilisateur ou un administrateur système peuvent être remplacés par le système dans le cas de la création de pages.

* Lors de la création de pages :

   * le recours à l’éditeur classique est forcé lors de l’accès à la page à l’aide de `cf#` dans l’URL. Par exemple :

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Le recours à l’éditeur tactile est forcé lors de l’utilisation de `/editor.html` dans l’URL ou lors de l’utilisation d’un appareil tactile. Par exemple :

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Tout recours forcé à un certain éditeur est temporaire et valide uniquement pour la session en cours.

   * Un jeu de cookies est défini selon qu’il s’agit de l’éditeur tactile (`editor.html`) ou classique (`cf#`).

* Lors de l’ouverture de pages en tant que `siteadmin`, plusieurs contrôles ont lieu :

   * Présence du cookie
   * Préférence utilisateur
   * En l’absence de tels paramètres, l’IU définie par défaut dans la [configuration OSGi](/help/sites-deploying/configuring-osgi.md) du service **Mode d’IU de création de la gestion de contenu web** (service `AuthoringUIMode`) est utilisée.

>[!NOTE]
>
>If [un utilisateur a déjà défini une préférence pour la création de pages ;](#setting-classic-ui-authoring-for-your-account), qui ne sera pas remplacé par la modification de la propriété OSGi.

>[!CAUTION]
>
>En raison de l’utilisation de cookies, comme déjà décrit, il n’est pas recommandé de :
>
>* Modifier manuellement l’URL : une URL non standard peut entraîner une situation inconnue et un manque de fonctionnalité.
>* Ouvrir les deux éditeurs en même temps ; dans des fenêtres distinctes, par exemple.
>

