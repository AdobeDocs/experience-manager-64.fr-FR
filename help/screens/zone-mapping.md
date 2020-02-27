---
title: Éditeur de mise en page de l’affichage
seo-title: Éditeur de mise en page de l’affichage
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: 6c3b35bc-ea4f-46d4-bfed-2505ae21f764
contentOwner: jsyal
discoiquuid: 679da35f-2b6b-4910-92bd-5dbd4ae3742a
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Éditeur de mise en page de l’affichage{#display-layout-editor}

Le ***mappage de zones*** permet de créer différentes zones et d’utiliser une variété de ressources telles que des vidéos, des images et du texte, qui peuvent être regroupées en un seul écran de manière contextuelle. Vous pouvez importer des images, des vidéos et du texte, et les mélanger de façon à créer une expérience numérique intuitive et interactive. En fonction des exigences du projet, vous avez parfois besoin de plusieurs zones dans un affichage.

Par exemple, une séquence de produits avec un flux de réseaux sociaux associé qui s’exécute dans deux zones distinctes sur un seul affichage.

## Présentation {#overview}

Lors de la création d’un affichage pour le canal, vous pouvez sélectionner différentes options de modèle pour consulter/gérer le contenu dans le canal.

Les modèles suivants sont disponibles lors de la création des zones pour l’affichage :

* 2x1
* 2x2
* 3x1
* 4x1
* 5x1

En utilisant l’un de ces modèles, vous pouvez créer une expérience d’affichage dynamique interactive et intuitive dans laquelle une grande variété de contenu peut être utilisée sur un seul écran.

>[!NOTE]
>
>To learn in-depth about creating channels and displays, see [Managing Channels](managing-channels.md) and [Managing Displays](managing-displays.md) respectively in Authoring Screens.

## Description du cas d’utilisation {#use-case-description}

Ce cas d’utilisation permet de créer un projet AEM Screens avec un canal qui exploite le contenu et l’affiche à l’écran dans plusieurs zones.

>[!NOTE]
>
>Les zones ne mettent pas le contenu à l’échelle ; la mise à l’échelle doit être effectuée avant d’insérer le contenu dans vos canaux.

### Procédure à suivre pour créer un projet {#steps-for-creating-a-project}

Suivez les étapes ci-dessous pour créer un projet AEM Screens ; elles expliquent comment effectuer un mappage de zones pour votre projet AEM Screens :

1. ***Création d’un projet Screens***

   1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis Screens. Alternatively, you can ﻿go directly to: [http://localhost:4502/screens.html/content/screens](http://localhost:4502/screens.html/content/screens).
   1. Cliquez sur **Créer** pour créer un projet Screens.
   1. Sélectionnez **Screens** à partir de l’assistant **Créer un projet Screens**, puis cliquez sur **Suivant**.
   1. Enter the title as **Demo Mapping Project** and click **Create**.
   ![zm1](assets/zm1.gif)

1. ***Création d’un dossier de canaux***

   1. Accédez à** Projet de mappage de zones**.
   1. Cliquez sur **Créer** dans la barre d’actions. Un assistant s’ouvre.
   1. Choose the **Channels Folder **and click **Next**.
   1. Enter the Title as **Dual Zone **and click **Create**.
   ![zm2](assets/zm2.gif)

1. ***Création d’un canal***

   1. Navigate to the **Zone Mapping Project** you created and select the Channels folder (**Dual Zone**).
   1. Cliquez sur **Créer** dans la barre d’actions. Un assistant s’ouvre.
   1. Sélectionnez **Canal de séquence **et cliquez sur **Suivant**.
   1. Enter the **Title** as **Left** and click **Create**.
   De la même manière, créez un autre canal de séquence **Right** dans le projet **Zone Mapping Project**.

   ![zm3](assets/zm3.gif)

1. ***Ajout de contenu à des canaux***

   1. Navigate to the **Zone Mapping Project** you created and select the **Channel** you created.
   1. Cliquez sur **Modifier** dans la barre d’actions.
   1. The editor for the **Left** opens. Cliquez sur l’icône qui fait passer le panneau latéral du côté gauche de la barre d’actions pour ouvrir les ressources et les composants. 
   1. Faites glisser et déposez les composants que vous souhaitez ajouter à votre canal. 
   De même, ajoutez du contenu au canal **Right**.

   ![zm4](assets/zm4.gif)

   >[!NOTE]
   >
   >Vous pouvez remplir le contenu de vos canaux avec différentes ressources (images et vidéos) conformément aux exigences du projet.

1. ***Création d’un emplacement***

   1. Navigate to the** Zone Mapping Project** and select the **Locations** folder.
   1. Cliquez sur **Créer** en regard de l’icône plus (+) de la barre d’actions. Un assistant s’ouvre.
   1. Sélectionnez **Emplacement** dans l’assistant, puis cliquez sur **Suivant**.
   1. Enter the **Title** for your location (enter the title as **San Jose**) and click **Create**.
   ![zm5](assets/zm5.gif)

1. ***Création d’un nouvel affichage pour San Jose***

   1. Navigate to the location where you want to create your display (**Demo Mapping Project** --> **Locations** --> **San Jose**) and select **San Jose**.
   1. Cliquez sur **Créer** dans la barre d’actions. Sélectionnez **Affichage** à partir de l’assistant **Créer** et cliquez sur **Suivant**.
   1. Enter **Title** for your display location (enter the title as **Dual Zone**).
   1. Dans l’onglet **Affichage**, sélectionnez les détails de la mise en page. Sélectionnez la résolution **Full HD**.
   1. Définissez **Nombre d’appareils horizontalement****sur 2**. Définissez **Nombre d’appareils verticalement****sur 1**.
   1. Cliquez sur **Créer**.
   ![zm6](assets/zm6.gif)

1. ***Attribution d’un canal***

   1. Navigate to the display from **Zone Mapping Project** --> **Locations** --> **San Jose** --> **Dual Zone Display**.
   1. Select **Dual Zone Display **and tap/click **Assign Channel** from the action bar, Or,
   1. Vous pouvez aussi cliquer sur **Tableau de bord** et sélectionner **+Attribuer un canal** en haut à droite du panneau **CANAUX ET PLANIFICATIONS ATTRIBUÉS**, comme illustré dans la figure ci-dessous. **Affectation de canal **ouvre la boîte de dialogue.
   1. Enter the **Channel Role** as **Zone**.
   1. Sélectionnez Canal de référence  en fonction du chemin d’accès. Select the channel folder path (**Zone Mapping Project **--> **Channels** --> **Dual Zone** ) in the Channel.
   1. Définissez la **priorité** de ce canal sur **1**. Choisissez les **événements pris en charge** **Chargement initial** et **Écran inactif**.
   1. Cliquez sur **Enregistrer**.
   ![zm7](assets/zm7.gif)

1. ***Enregistrement et attribution du périphérique***

   1. Lancez une fenêtre du navigateur distincte. Accédez au lecteur Screens à l’aide du navigateur web ou lancez l’application AEM Screens. Lorsque vous ouvrez le périphérique, vous remarquez que son état est non enregistré. 
   1. From the AEM dashboard, navigate to **Zone Mapping Project** --> **Devices**.
   1. Cliquez sur **Gestionnaire de périphériques **dans la barre d’actions.
   1. Cliquez sur **Enregistrement de périphérique** pour voir les périphériques en attente.
   1. Sélectionnez le périphérique que vous voulez enregistrer et cliquez ensuite sur **Enregistrer le périphérique**.
   1. Vous devez valider le code en le vérifiant à partir du navigateur web ou du lecteur AEM Screens. Cliquez sur **Valider** pour accéder à l’écran **Enregistrement du périphérique**.
   1. Enter **Title** as **Zone Device** and click **Register** and the device will be registered.
   1. Cliquez sur **Attribuer l’affichage** pour passer à l’étape suivante où vous attribuez le périphérique à un affichage.
   1. Click **Assign Device** fand select the display path for your channel () as */content/screens/Test_Project/Locations/TestLocation/TestDisplay*. Cliquez sur **Attribuer**.
   1. Cliquez sur **Terminer** pour achever le processus. Le périphérique est désormais attribué.
   ![zm8](assets/zm8.gif)

1. ***Création de l’affichage multizone***

   1. Navigate and select the display from **Zone Mapping Project** --> **Locations** --> **San Jose **--> **Dual Zone **display and click **Dashboard** from the action bar.
   1. Sélectionnez l’icône située à gauche de **Configuration du périphérique** dans le lecteur à partir du panneau **PÉRIPHÉRIQUES** et cliquez sur **Propriétés**.
   1. Accédez à l’onglet **Configuration du périphérique**, puis renseignez les champs **Mappage** et **Modèle**. Enter *{&quot;a1&quot;:&quot;${display.channel}/left&quot;, &quot;a2&quot;: &quot;${display.channel}/right&quot;}* in the **Mapping** field and template as *grid-2x1*.
   1. Click **Save &amp; Close** and reload the player.
   >[!NOTE]
   >
   >***Présentation du mappage et des modèles dans la configuration de périphérique :***
   >
   >* Les identifiants a1 et a2 correspondent aux zones définies dans le modèle, c’est-à-dire, screens-zone-a1 et screens-zone-a2.
   >* ${display.channel}/left pointe sur le canal à incorporer dans la zone, où display.channel pointe sur le chemin du canal actuel dans l’affichage. Cela permet d’incorporer efficacement les enfants « left » et « right » du canal.


   ![screen_shot_2018-01-22at114708am](assets/screen_shot_2018-01-22at114708am.png)

#### Affichage du contenu dans le lecteur AEM Screens {#viewing-content-in-aem-screens-player}

Chargez le lecteur AEM Screens ou utilisez le navigateur web.

Vous verrez le contenu des deux canaux (Left et Right) affiché dans votre lecteur Screens. Le contenu est affiché en tant que zone d’affichage 2x1.

![](do-not-localize/screen_shot_2018-01-22at120206pm.png)

### Inférence    {#inference}

Le mappage des zones utilise l’un des modèles disponibles lors de la création d’un canal dans AEM Screens, ce qui permet d’effectuer l’aplatissement côté client. Vous pouvez créer différentes zones dans votre écran et remplir ensuite les zones avec des vidéos, des images et d’autres ressources disponibles.
