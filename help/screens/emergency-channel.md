---
title: Canal d’urgence
seo-title: Canal d’urgence
description: Lisez ce cas d’utilisation pour en savoir plus sur la création et la gestion d’un canal d’urgence sur lequel l’auteur du contenu peut basculer depuis un canal de séquence dans certaines circonstances.
seo-description: Lisez ce cas d’utilisation pour en savoir plus sur la création et la gestion d’un canal d’urgence sur lequel l’auteur du contenu peut basculer depuis un canal de séquence dans certaines circonstances.
uuid: 527137b4-0421-4917-95e1-195611e25f54
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: example
topic-tags: use-case-examples
discoiquuid: 0d711658-5174-40c5-9e75-cc68c1836948
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Canal d’urgence{#emergency-channel}

## Description du cas d’utilisation {#use-case-description}

Cette section décrit un cas d’utilisation axé sur la création et la gestion d’un canal d’urgence vers lequel l’auteur du contenu peut basculer depuis un canal de séquence dans certaines circonstances.

### Conditions préalables {#preconditions}

Avant de commencer ce cas d’utilisation, vous devez comprendre comment :

* **[Création et gestion des canaux](/help/screens/managing-channels.md)**
* **[Création et gestion des emplacements](/help/screens/managing-locations.md)**
* **[Création et gestion des planifications](/help/screens/managing-schedules.md)**
* **[Enregistrement de périphériques](/help/screens/device-registration.md)**

### Acteurs principaux {#primary-actors}

Auteurs de contenu

## Flux de base : configuration du projet {#basic-flow-setting-up-the-project}

Pour configurer un canal d’urgence, procédez comme suit :

1. Créez un projet AEM Screens appelé **EmergencyChannel**, comme illustré ci-dessous.

   >[!NOTE]
   >
   >Pour en savoir plus sur la création et la gestion de projets dans AEM Screens, voir Création d’un projet.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Création d’un canal de séquence**

   1. Sélectionnez le dossier **Channels** (Canaux), puis cliquez sur **Créer** pour ouvrir l’assistant afin de créer un canal.
   1. Sélectionnez **Canal de séquence**dans l’assistant et créez un canal appelé **MainAdChannel**.
   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Ajout de contenu à un canal de séquence**

   1. Sélectionnez le canal (**MainAdChannel**).
   1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur. Faites glisser quelques ressources vers votre canal.
   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Création d’un canal d’urgence**

   1. Sélectionnez le dossier **Channels** (Canaux).
   1. Cliquez sur **Créer** pour ouvrir l’assistant et créer un canal.
   1. Sélectionnez **Canal de séquence **dans l’assistant et créez un canal appelé **EmergencyChannel**.
   >[!NOTE]
   >
   >Normalement, votre canal d’urgence est ajouté à votre projet de production préexistant.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Ajout de contenu à un canal d’urgence**

   1. Sélectionnez le canal (**Canal d’urgence)**.
   1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur. Faites glisser vers votre canal la ressource que vous souhaitez exécuter en cas d’urgence.
   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Création d’un emplacement**

   1. Accédez au dossier **Locations** (Emplacements).
   1. Cliquez sur **Créer** à partir de la barre d’actions, puis créez un emplacement appelé **Boutique** à partir de l’assistant.
   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Création d’affichages dans votre emplacement**

   Accédez à votre emplacement (**Boutique**) et cliquez sur **Créer** dans la barre d’actions. Suivez l’assistant pour créer deux **Affichages** appelés **StoreFront** et **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Création d’une planification**

   1. Accédez au dossier **Schedules** (Planifications).
   1. Cliquez sur **Créer** dans la barre d’actions. Suivez l’assistant pour créer une planification appelée **StoreSchedule**.
   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Affectation des deux affichages à votre planification et définition de priorités

   1. Sélectionnez la planificiation** (StoreSchedule)** et cliquez sur **Tableau de bord** dans la barre d’actions.
   1. Cliquez sur **+ Attribuer le canal** dans le panneau **CANAUX ATTRIBUÉS**.
   1. Dans la boîte de dialogue **Attribution de canaux** :

      1. Sélectionnez le chemin d’accès à **MainAdChannel**.
      1. Définissez la **priorité** sur 2.
      1. Définissez les événements pris en charge **Chargement initial** et **Écran inactif**.
      1. Cliquez sur **Enregistrer**
      Vous devrez procéder de la même manière pour affecter **EmergencyChannel** et définir sa **Priorité**.
   >[!NOTE]
   >
   >La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celle présentant la valeur la plus élevée est toujours prioritaire par rapport aux valeurs plus faibles.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. 

   1. Cliquez sur **+ Attribuer le canal** dans le panneau **CANAUX ATTRIBUÉS**.
   1. Dans la boîte de dialogue **Attribution de canaux** :

      1. Sélectionnez le chemin d’accès à **EmergencyChannel**.
      1. Définissez la **priorité** sur 1.
      1. Définissez les Événements pris en charge **Charge initiale**, **Écran inactif** et **Interaction utilisateur**
      1. Cliquez sur **Enregistrer**
   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Vous pouvez afficher les canaux affectés à partir du tableau de bord **StoreSchedule**.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Attribution d’une planification à chaque affichage**

   1. Accédez à chaque affichage, par exemple **EmergencyChannel** --> **Emplacements** --> **Boutique **-->**StoreFront**.
   1. Pour ouvrir le tableau de bord des affichages, cliquez sur **Tableau de bord** dans la barre d’actions.
   1. Cliquez sur **...** dans le panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**, puis sur **+Attribuer une planification**.
   1. Sélectionnez le chemin d’accès à la planification (par exemple, ici, **EmergencyChannel** --> **Planifications** --> **StoreSchedule**).
   1. Cliquez sur **Enregistrer**.
   Vous pouvez afficher la planification affectée à l’affichage à partir du tableau de bord **StoreSchedule** .

   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Enregistrement de périphériques**

   Terminez le processus d’enregistrement de périphériques et, une fois enregistré, vous verrez l’image suivante sur votre lecteur AEM Screens.

   ![new30](assets/new30.gif)

## Basculer vers le canal d’urgence {#switching-to-emergency-channel}

Réalisez la procédure suivante en cas d’urgence :

1. Accédez à **EmergencyChannel** --> **Planifications** --> **StoreSchedule** et sélectionnez **Tableau de bord** dans la barre d’actions.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Sélectionnez **EmergencyChannel** dans le tableau de bord **StoreSchedule** et cliquez sur **Modifier l’attribution**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Définissez la **Priorité** de **EmergencyChannel** sur **3** depuis la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Dès que la priorité du canal est mise à jour, tous les lecteurs AEM Screens affichent le contenu **EmergencyChannel**, comme illustré ci-dessous.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusion {#conclusion}

**EmergencyChannel** continue d’afficher son contenu jusqu’à ce que l’auteur du contenu réinitialise la Valeur de priorité sur 1.

Une fois que l’auteur du contenu a reçu une notification indiquant que l’urgence est terminée, il doit mettre à jour la priorité de **MainAdChannel**, ce qui entraîne la reprise de la lecture normale.
