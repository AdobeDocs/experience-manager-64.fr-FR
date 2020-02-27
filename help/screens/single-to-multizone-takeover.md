---
title: Prise en charge d’une zone unique vers plusieurs zones
seo-title: Prise en charge d’une zone unique vers plusieurs zones
description: 'Suivez cette page pour en savoir plus sur la prise en charge d’une zone unique en zone multizone dans un projet AEM Screens.  '
seo-description: 'Suivez cette page pour en savoir plus sur la prise en charge d’une zone unique en zone multizone dans un projet AEM Screens.    '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# Prise en charge d’une zone unique vers plusieurs zones {#single-zoneto-multizone}

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

1. Create an AEM Screens Project named as **ZonesDemo**, as shown below.

   >[!NOTE]
   >
   >To learn more about creating and managing projects in AEM Screens, refer to [Creating a Project](/help/screens/creating-a-screens-project.md).

   ![screen_shot_2019-02-21at35809pm](assets/SZtoMZ1.png)

1. **Création d’un canal de séquence avec une image**

   1. Sélectionnez le dossier **Channels** (Canaux), puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant afin de créer un canal.
   1. Select **Sequence Channel** from the wizard and create the channel titled as **FullScreenOne**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ2.png)
   1. Sélectionnez le canal, puis cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et faire glisser une image vers ce canal, comme illustré ci-dessous.
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

## Configuration du canal de reprise en transition d&#39;une zone unique à une zone multiple {#takeover-channel-setup}

1. **Modification du canal d’une seule zone pour le reprise multi-zone**

   1. Sélectionnez le canal (**FullScreenOne)** que vous avez créé à l’étape 1.
   1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur. Faites glisser deux composants de canal et un composant vidéo vers l’éditeur.
   ![screen_shot_2019-02-21at40516pm](assets/SZtoMZ10.png)

1. **Renseigner les composants ajoutés au canal FullScreenOne**

   1. Sélectionnez le premier composant de canal dans l’éditeur de **FullScreenOne** et cliquez sur **Configurer** pour pointer vers le canal créé lors des étapes précédentes. Ajoutez le chemin d’accès au canal dans Chemin **du** canal aux deux composants du canal et faites glisser la vidéo vers le composant vidéo comme illustré ci-dessous.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo1.gif)

1. **Configuration de la durée des canaux pendant la transition**

   >[!NOTE]
   >
   >Par défaut, la transition des ressources s’effectue toutes les 8 secondes, mais si vous souhaitez que la transition des ressources s’effectue après une durée spécifique, procédez comme suit.

   1. Sélectionnez le deuxième composant de canal dans l’éditeur de **FullScreenOne** et cliquez sur **Paramètres** pour configurer la durée de ce canal. De même, configurez la durée du canal 2, comme illustré ci-dessous.
Dans cet exemple, la durée est définie sur 3 secondes.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo2.gif)

## Aperçu du résultat {#previewing-result}

Vous pouvez cliquer sur **Aperçu** dans l’éditeur et vérifier comment les ressources vont passer d’une zone unique à une zone multizone.

![](assets/SZ_MZvideo3.gif)
