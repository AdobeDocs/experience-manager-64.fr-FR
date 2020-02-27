---
title: Activation au niveau du canal - Lecture d’un événement unique
seo-title: Activation au niveau du canal - Lecture d’un événement unique
description: Suivez ce guide pour comprendre l’activation au niveau du canal à l’aide de la lecture d’événement unique.
seo-description: Suivez ce guide pour comprendre l’activation au niveau du canal à l’aide de la lecture d’événement unique.
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
translation-type: tm+mt
source-git-commit: 3addef2141ebb831f8677d011d68faf88e648dc2

---


# Activation au niveau du canal - Lecture d’un événement unique{#channel-level-activation-single-event-playback}

L’activation au niveau du canal couvre les rubriques suivantes :

* **[Présentation](/help/screens/channel-level-activation.md#overview)**
* **[Utilisation de l’activation au niveau du canal comme lecture d’événement unique](/help/screens/channel-level-activation.md#using-channel-level-activation)**

   * **[Conditions préalables](/help/screens/channel-level-activation.md#prerequisites)**
   * **[Mise en œuvre](/help/screens/channel-level-activation.md#implementation)**

* **[Affichage des résultats](/help/screens/channel-level-activation.md#viewing-the-results)**

## Présentation {#overview}

***L’activation*** au niveau du canal permet aux canaux de basculer après une planification définie. Le canal d’événement unique remplace le canal principal après une planification définie et il est lu pendant une période donnée, jusqu’à ce que le canal principal exécute à nouveau son contenu.

L’exemple suivant fournit une solution en se concentrant sur les termes clés suivants :

* un ***canal de séquence principal*** pour la séquence globale
* un ***canal d’événement unique*** qui s’exécute une seule fois à un moment défini
* une ***planification et une priorité définies*** de l’événement de lecture unique qui se produit dans le canal de séquence principal

## Utilisation de l’activation au niveau du canal {#using-channel-level-activation}

La section suivante explique la création d’une lecture d’événement unique dans un canal pour un projet AEM Screens.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, veillez à ce que les conditions préalables suivantes sont satisfaites avant de commencer à implémenter l’activation au niveau du canal :

* Create an AEM Screens project (in this example, **Channel Level Activation**)

* Créez un canal dénommé **MainAdChannel** principal sous le dossier **Canaux**

* Créez un autre canal dénommé **TargetedSinglePlay** sous le dossier **Canaux**

* Ajoutez les ressources appropriées aux deux canaux

L’image suivante montre le projet **Channel Level Activation** avec les canaux **MainAdChannel** et **TargetedSinglePlay** ciblés dans le dossier **Canaux**.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Pour plus d’informations sur la création d’un projet et la création d’un canal de séquence, reportez-vous aux ressources ci-dessous :
>
>* [Créer et gérer des projets](/help/screens/creating-a-screens-project.md)
   >
   >
* [Gestion d’un canal](/help/screens/managing-channels.md)
>



### Mise en œuvre {#implementation}

L’implémentation de l’activation au niveau du canal dans un projet AEM Screens implique trois tâches principales :

1. **Configuration de la taxonomie du projet, y compris les canaux, emplacements et écrans**
1. **Affectation de canaux à un affichage**
1. **Configuration d’un calendrier et d’une priorité**

Suivez les étapes ci-dessous pour mettre en œuvre la fonctionnalité :

1. **Créez un emplacement**

   Accédez au dossier **Emplacements** dans votre projet AEM Screens et créez un emplacement en tant que **Région**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Pour savoir comment créer un emplacement, reportez-vous à **[Création et gestion des emplacements](/help/screens/managing-locations.md)**.

1. **Créer un affichage sous Emplacement**

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région**.
   1. Sélectionnez **Région**, puis cliquez sur **+Créer** dans la barre d’actions.
   1. Sélectionnez **Afficher** dans l’assistant et créez un affichage intitulé **RegionDisplay.**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Affectation de canaux à un affichage**

   Pour **MainAdChannel :**

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région** > **RegionDisplay** puis cliquez sur **Affecter un canal** dans la barre d’actions.
   1. La boîte de dialogue **Attribution de canaux** s’ouvre.
   1. Sélectionnez **Canal de référence**.. en fonction du chemin d’accès.
   1. Select the **Channel Path** as **Channel Level Activation** --> ***Channels*** --> ***MainAdChannel***.
   1. Le **Rôle du canal** est défini comme **mainadchannel**.
   1. Sélectionnez la **Priorité** **1**.
   1. Choisissez les **Événements pris en charge** **Chargement initial** et **Écran inactif**.
   1. Cliquez sur **Enregistrer**.
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Vous pouvez également affecter un canal à partir du tableau de bord d’affichage en accédant à **Channel Level Activation** —> **Emplacements** —> **Région** —> **RegionDisplay** et en cliquant sur **Tableau de bord** dans la barre d’actions. Cliquez sur **+ Attribuer un canal** dans le panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**.

   De même, affectez le canal **TargetedSinglePlay** afin qu’il soit affiché** :

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région** > **RegionDisplay** puis cliquez sur **Affecter un canal** dans la barre d’actions.
   1. La boîte de dialogue **Attribution de canaux** s’ouvre.
   1. Sélectionnez **Canal de référence**.. en fonction du chemin d’accès.
   1. Select the **Channel Path** as **Channel Level Activation*** --> ***Channels*** --> ***TargetedSinglePlay***.*
   1. Le **Rôle de canal** est renseigné avec le contenu **targetedsingleplay**.
   1. Définissez la **Priorité** sur **2**.
   1. Select the **Supported Events** as **Initial Load**, **Idle Screen** and **Timer***, *as shown in the figure below.
   1. Choisissez la date **active à partir** du 27 novembre 2018 à 23h59 et **active jusqu’au** 28 novembre 2018 à 12h05.*
*
   1. Cliquez sur **Enregistrer**.*
*
   >[!CAUTION]
   Vous devez définir pour le canal **TargetSinglePlay** une priorité plus élevée que le canal **MainAdSegment** .

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Pour choisir le même jour, vous devez sélectionner le jour suivant et modifier manuellement la date en choisissant le même jour, mais à une heure ultérieure. L’utilisateur ne peut donc pas sélectionner une date antérieure. Reportez-vous à l’exemple ci-dessous :

   ![new1](assets/new1.gif)

## Affichage des résultats {#viewing-the-results}

Une fois que vous aurez configuré les canaux et l’affichage, veuillez lancer le lecteur AEM Screens pour afficher le contenu.

Le lecteur affiche le contenu de **MainAdChannel** et exactement à 23h59 (comme défini dans la planification), le canal **TargetedSinglePlay** affiche son contenu jusqu’à 12h05, puis le canal **MainAdChannel** reprend la lecture de son contenu.

>[!NOTE]
Pour en savoir plus sur le lecteur d’écran AEM, consultez les ressources suivantes :
* [**Téléchargements du lecteur AEM Screens **](https://download.macromedia.com/screens/)
* [**Utilisation du lecteur AEM Screens **](/help/screens/working-with-screens-player.md)



