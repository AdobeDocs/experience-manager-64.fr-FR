---
title: Boucle de reprise multi-zone vers une seule zone
seo-title: Boucle de reprise multi-zone vers une seule zone
description: 'Suivez cette page pour en savoir plus sur la boucle de reprise multi-zone vers une seule zone dans un projet AEM Screens.  '
seo-description: 'Boucle de reprise multi-zone vers une seule zone dans un projet AEM Screens.  '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# Boucle de reprise multi-zone vers une seule zone{#single-zoneto-multizone}

## Description du cas d’utilisation {#use-case-description}

Cette section décrit un exemple de cas d’utilisation qui met l’accent sur la configuration d’un canal de mise en page à zones multiples qui alterne avec un canal de mise en page à zone unique. Chaque canal comporte un séquencement des fichiers image/vidéo.

### Conditions préalables {#preconditions}

Avant de commencer ce cas d’utilisation, vous devez comprendre comment :

* **[Création et gestion des canaux](/help/screens/managing-channels.md)**
* **[Création et gestion des emplacements](/help/screens/managing-locations.md)**
* **[Création et gestion des planifications](/help/screens/managing-schedules.md)**
* **[Enregistrement de périphériques](/help/screens/device-registration.md)**

### Acteurs principaux {#primary-actors}

Auteurs de contenu

## Configuration du projet {#setting-up-the-project}

Pour configurer un projet, procédez comme suit :

1. Créez un projet AEM Screens appelé **TakeoverLoop**, comme illustré ci-dessous.

   >[!NOTE]
   >
   >To learn more about creating and managing projects in AEM Screens, refer to [Creating a Project](/help/screens/creating-a-screens-project.md).

   ![](assets/takeover-loop1.png)

1. **Création d’un canal d’écran partagé**

   1. Sélectionnez le dossier **Channels** (Canaux), puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant afin de créer un canal.
   1. Sélectionnez **Left-L Bar Split Screen Channel** dans l’assistant et créez le canal intitulé **MultiZoneLayout**.

      ![](assets/takeover-loop2.png)

   1. Select the **MultiZoneLayout** channel and click **Edit** from the action bar to open the editor. Faites glisser les ressources vers chacune des zones. L’exemple suivant montre une vidéo, une image et une bannière de texte dans la chaîne, comme illustré ci-dessous.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ3.png)

1. **Création d’un canal 2X2 avec quatre images**

   1. Sélectionnez le dossier **Channels** (Canaux), puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant afin de créer un canal.

   1. Select **2X2 Split Screen Channel** template from the wizard and create the channel titled as **TwobyTwoChannel**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ4.png)
   1. Sélectionnez le canal, puis cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et faites glisser quatre images (quatre zones différentes) sur ce canal, comme illustré ci-dessous.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ5.png)

1. **Création d’un canal d’écran partagé 1X2 avec deux images**

   1. Sélectionnez le dossier **Channels** (Canaux), puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant afin de créer un canal.

   1. Select **1X2 Split Screen Channel** template from the wizard and create the channel titled as **OnebyTwoChannel**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ6.png)
   1. Sélectionnez le canal, puis cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et faites glisser deux images (deux zones différentes) sur ce canal, comme illustré ci-dessous.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ7.png)

1. **Création d’un canal avec une vidéo plein écran**

   1. Sélectionnez le dossier **Channels** (Canaux), puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant afin de créer un canal.

   1. Select **Sequence Channel** template from the wizard and create the channel titled as **FullScreensVideo**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ8.png)
   1. Sélectionnez le canal, puis cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et faire glisser le composant vidéo sur ce canal, puis ajoutez la vidéo de votre choix, comme illustré ci-dessous.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ9.png)