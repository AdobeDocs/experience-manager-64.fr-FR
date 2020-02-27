---
title: Guide de démarrage rapide
seo-title: Guide de démarrage rapide
description: Suivez cette page pour créer un projet AEM Screens de démonstration. Vous pouvez créer une expérience de signalisation numérique à partir de l’installation et configurer un nouveau projet d’affichage de contenu dans le lecteur AEM Screens.
seo-description: Suivez cette page pour créer un projet AEM Screens de démonstration. Vous pouvez créer une expérience de signalisation numérique à partir de l’installation et configurer un nouveau projet d’affichage de contenu dans le lecteur AEM Screens.
uuid: 73fff2f2-c926-4435-8ab2-891771c843aa
contentOwner: Jyotika syal
content-type: reference
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
discoiquuid: 9e03f35e-284b-43d8-b095-c94800e2e9b3
translation-type: tm+mt
source-git-commit: 5f613cbae9dccbc277287e5e58c8f0648c4f3bed

---


# Guide de démarrage rapide     {#kickstart-guide}

Cette section vous donne un premier aperçu d’AEM Screens et montre comment réaliser des actions de base. Elle vous guide à travers la configuration d’une expérience de signalisation numérique de base avec des ressources ou du contenu et la publication dans le lecteur Screens. Pour une présentation détaillée de tous les composants pour le développement de Screens, reportez-vous aux ressources indiquées à la fin de la page.

## Création d’une expérience de signalisation numérique en 5 minutes {#creating-a-digital-signage-experience-in-minutes}

Les étapes suivantes vous permettent de créer un exemple de projet pour Screens et de publier du contenu sur le lecteur Screens.

1. Pour télécharger le **lecteur AEM Screens**, cliquez [ici](https://download.macromedia.com/screens/).

   AEM Screens est également disponible dans **Google Play**.

   Pour plus d’informations sur la mise en œuvre du lecteur Chrome OS, reportez-vous à la section [Console de gestion Chrome](implementing-chrome-os-player.md).

   Pour plus d’informations, voir [Installation et configuration de Screens](configuring-screens-introduction.md).

   >[!NOTE]
   >
   >**Paramètres OSGI**
   >
   >Vous devez activer le référent vide pour autoriser le périphérique à publier des données sur le serveur. Par exemple, si la propriété de référent vide est désactivée, le périphérique ne pourra pas publier de capture d’écran. Actuellement, certaines de ces fonctions ne sont disponibles que si l’option Allow Empty d’Apache Sling Referrer Filter est activée dans la configuration OSGi. Le tableau de bord peut afficher un avertissement indiquant que les paramètres de sécurité peuvent empêcher l’utilisation de certaines de ces fonctions.
   >
   >Pour activer l’option ***Allow Empty d’Apache Sling Referrer Filter***, procédez comme suit :
   >
   >1. Navigate to [Adobe Experience Manager Web Console Configuration](http://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter).
   >1. Cochez l’option **allow.empty**.
   >1. Cliquez sur **Enregistrer**.
   >    
   >Pour en savoir plus sur les étapes précédentes dans les détails, reportez-vous à la section ***Conditions préalables*** dans [Configuration et déploiement d’AEM Screens](configuring-screens-introduction.md).

1. **Création d’un projet**

   1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis **Screens**. Alternatively, you can ﻿go directly to: [http://localhost:4502/screens.html/content/screens](http://localhost:4502/screens.html/content/screens).
   1. Cliquez sur **Créer** pour créer un projet Screens (voir la figure ci-dessous).
   1. Sélectionnez **Screens** à partir de l’assistant **Créer un projet Screens**, puis cliquez sur **Suivant**.
   1. Saisissez le titre **Test_Project** et cliquez ensuite sur **Créer**.
   ![chlimage_1-64](assets/chlimage_1-64.png)

   Une fois le projet créé, vous êtes redirigé vers la console du projet Screens. Vous pouvez sélectionner votre projet. In a project, there are five kind of folders namely **Schedules**, **Locations**, **Applications**, **Devices** and **Channels**, as shown in the figure below.

   >[!NOTE]
   >
   >« Planifications » n’est disponible que si vous avez installé le Feature Pack 1 d’AEM 6.3 Sites. Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations nécessaires, vous pouvez le télécharger à partir de Package Share.

   ![screen_shot_2019-03-04at85952am](assets/screen_shot_2019-03-04at85952am.png)

   Voir [Créer et gérer un projet Screens](creating-a-screens-project.md) pour en savoir plus.

1. **Création d’un canal** 

   Une fois que vous avez votre projet, vous devez créer une nouveau canal où vous pouvez gérer le contenu.

   Pour créer un canal pour votre projet, procédez comme suit :

   1. Accédez au projet **Test_Project** que vous avez créé et sélectionnez ensuite le dossier **Channels** (Canaux).
   1. Cliquez sur **Créer** dans la barre d’actions (voir la figure ci-dessous). Un assistant s’ouvre.
   1. Sélectionnez **Canal de séquences** et cliquez sur **Suivant**.
   1. Saisissez le **nom** et le **titre** **TestChannel**, puis cliquez sur **Créer**.
   ![screen_shot_2019-03-04at90236am](assets/screen_shot_2019-03-04at90236am.png)

   Le canal *TestChannel* est créé et ajouté au dossier de canaux, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-03-04at90346am](assets/screen_shot_2019-03-04at90346am.png)

   Reportez-vous à la section [Gestion des canaux](managing-channels.md) pour plus de détails sur la création et la gestion des canaux.

1. **Ajout de contenu à un canal**

   Une fois votre canal en place, vous devez ajouter à votre canal du contenu que le lecteur d’écrans AEM affichera.

   Suivez les étapes ci-dessous pour ajouter du contenu au canal (*TestChannel*) dans votre projet : 

   1. Accédez au projet *Test_Project* que vous avez créé et sélectionnez ensuite le dossier **Channels** (Canaux).
   1. Cliquez sur **Modifier** dans la barre d’actions (voir la figure ci-dessous). L’éditeur de *TestChannel* s’ouvre.
   1. Cliquez sur l’icône qui fait passer le panneau latéral du côté gauche de la barre d’actions pour ouvrir les ressources et les composants. 
   1. Faites glisser et déposez les composants que vous souhaitez ajouter à votre canal. 
   ![screen_shot_2019-03-04at90507am](assets/screen_shot_2019-03-04at90507am.png)

   Dans cet exemple, l’éditeur affiche une image ajoutée au canal. 

   ![screen_shot_2019-03-04at90558am](assets/screen_shot_2019-03-04at90558am.png)

1. **Création d’un emplacement**

   Une fois que vous avez le canal, vous devez créer votre emplacement. 

   Les ***emplacements*** permettent de compartimenter vos diverses expériences de signalisation numériques et contiennent les configurations de leurs affichages en fonction de l’endroit où se trouvent les différents écrans.

   Pour créer un emplacement pour votre projet, procédez comme suit :

   1. Accédez au projet *Test_Project* que vous avez créé et sélectionnez le dossier **Emplacements**.
   1. Cliquez sur **Créer** à côté de l’icône Plus dans la barre d’actions (voir la figure ci-dessous). Un assistant s’ouvre.
   1. Sélectionnez **Emplacement** dans l’assistant, puis cliquez sur **Suivant**.
   1. Saisissez le **nom** et le **titre** de votre emplacement (saisissez le titre *TestLocation*), puis cliquez sur **Créer**.
   ![screen_shot_2019-03-04at91021am](assets/screen_shot_2019-03-04at91021am.png)

   L’emplacement *TestLocation* est créé et ajouté à votre dossier **Locations** (Emplacements).

   ![screen_shot_2019-03-04at91117am](assets/screen_shot_2019-03-04at91117am.png)

1. **Création d’un affichage pour *TestLocation ***

   Une fois que vous avez créé un emplacement, vous devez créer un affichage pour celui-ci.

   Les ***affichages*** représentent l’expérience numérique qui s’exécute sur un ou plusieurs écrans.

   1. Accédez à l’emplacement sur lequel vous souhaitez créer votre affichage (*Test_Projec* t --> **Emplacements** --> *TestLocation)* comme indiqué dans la figure ci-dessus, puis sélectionnez *TestLocation*.
   1. Cliquez sur **Créer** dans la barre d’actions.
   1. Sélectionnez **Affichage** à partir de l’assistant **Créer** et cliquez sur **Suivant**.
   1. Enter **Title** for your display location (enter the title as *TestDisplay*).
   1. Cliquez sur **Créer**.
   A new display *TestDisplay* is added to your location *TestLocation*, as shown in the figure below.

   ![screen_shot_2019-03-04at91341am](assets/screen_shot_2019-03-04at91341am.png)

1. **Ajout d’une planification**

   Dans AEM Screens, les *planifications* vous permettent d’organiser les canaux en groupes réutilisables. Ainsi, vous n’avez pas à répéter leur attribution individuellement pour chaque affichage sur lequel vous souhaitez afficher votre contenu.

   >[!NOTE]
   >
   >Cette fonctionnalité d’écrans n’est disponible que si vous avez installé AEM 6.3 Sites Feature Pack 1 ou version ultérieure. Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations nécessaires, vous pouvez le télécharger à partir de Package Share.

   1. Accédez au dossier **Planifications** depuis Test_Project --> **Planifications**.
   1. Cliquez sur **Créer** dans la barre d’actions. Un assistant s’ouvre.
   1. Sélectionnez **Planification** depuis la page de l’assistant **Créer**. 
   1. Enter the **Title** as *MorningSchedule* in the properties page.
   1. Cliquez sur **Créer** pour ajouter une planification au dossier **Planifications**, comme illustré dans la figure ci-dessous. 
   ![screen_shot_2019-03-04at91836am](assets/screen_shot_2019-03-04at91836am.png)

   En outre, sélectionnez la planification (*MorningSchedule*) et cliquez sur **Tableau de bord** dans la barre d’actions pour afficher le tableau de bord des planifications. Vous pouvez afficher/modifier les propriétés de la planification, attribuer des canaux et voir les affichages attribués à l’aide du tableau de bord. 

   ![chlimage_1-65](assets/chlimage_1-65.png)

   Voir [Créer et gérer des planifications](managing-schedules.md) pour obtenir des informations détaillées sur les planifications.

1. **Attribution d’un canal**

   1. Accédez à l’affichage depuis *Test_Project* --> **Emplacements** --> *TestLocation* --> *TestDisplay*.
   1. Sélectionnez *TestDisplay* et cliquez ou appuyez sur **Attribuer un canal **depuis la barre d’actions *.*
   1. Vous pouvez aussi cliquer sur **Tableau de bord** et sélectionner **+Attribuer un canal** en haut à droite du panneau **CANAUX ET PLANIFICATIONS ATTRIBUÉS**, comme illustré dans la figure ci-dessous. La boîte de dialogue **Attribution de canaux** s’ouvre.
   1. Sélectionnez **Canal de référence** en fonction du **chemin d’accès**.
   1. Sélectionnez **Chemin d’accès au canal** (*Test_Project* --> *Canaux* --> *TestChannel*) dans le **canal**. Le rôle **de** canal est automatiquement renseigné par le nom du canal.
   1. Définissez la **priorité** de ce canal sur *1*.
   1. Choisissez les **événements pris en charge** **Chargement initial** et **Écran inactif**.
   1. Entrez la **planification** et sélectionnez les dates dans **Active from (Actif à partir de)** et **Active until (Actif jusqu’à)**. *(Vous devez remplir ces champs uniquement si vous souhaitez que le canal s’affiche pendant un intervalle de temps donné.)*
   1. Cliquez sur **Enregistrer**.
   Le canal est affecté et ajouté au panneau.

   ![screen_shot_2019-03-04at92423am](assets/screen_shot_2019-03-04at92423am.png)

   Pour en savoir plus sur la boîte de dialogue **Attribution des canaux** et les propriétés associées, voir [Attribution des canaux.](channel-assignment.md)

1. **Ajout de la planification à un canal**

   1. Accédez à l’affichage depuis *Test_Project* --> **Emplacements** --> *TestLocation* --> *TestDisplay*.
   1. Cliquez sur **Tableau de bord** et sélectionnez **+Attribuer une planification** en haut à droite du panneau **CANAUX ET PLANIFICATIONS ATTRIBUÉS**, comme indiqué dans la figure ci-dessus. La boîte de dialogue **Attribution des planifications** s’ouvre.
   1. Sélectionnez le chemin dans lequel vous avez créé la planification (ici, *Test_Project* --> **Planifications** --> *MorningSchedule*).
   1. Cliquez sur **Enregistrer** pour ajouter la planification à votre canal. 
   ![screen_shot_2019-03-04at93309am](assets/screen_shot_2019-03-04at93309am.png)

1. **Enregistrement d’un périphérique**

   Vous devez enregistrer votre périphérique à l’aide du tableau de bord AEM. 

   >[!NOTE]
   >
   >Vous pouvez ouvrir le lecteur Screens à l’aide de l’application AEM’Screens que vous avez téléchargée ou à l’aide du navigateur web.

   Pour afficher le périphérique en attente :

   1. Lancez une fenêtre du navigateur distincte.
   1. Accédez au lecteur Screens à l’aide du [navigateur web](http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html)  ou lancez l’application AEM Screens. Lorsque vous ouvrez le périphérique, vous remarquez que son état est non enregistré. 
   1. Depuis le tableau de bord AEM, accédez à *Test_Project* --> **Périphériques**
   1. Cliquez sur **Gestionnaire de périphériques** dans la barre d’actions.
   1. Cliquez sur **Enregistrement des périphériques** et les périphériques en attente s’affichent, comme illustré dans la figure ci-dessous.
   >[!NOTE]
   >
   >Si vous utilisez AEM Screens Player en tant qu’extension ChromeOS, reportez-vous à la requête sous ***Comment installer ChromeOS Player en tant que module externe*** de navigateur Chrome dans la page FAQs [d’](aem-screens-faqs.md) AEM Screens.

   ![screen_shot_2019-03-04at94604am](assets/screen_shot_2019-03-04at94604am.png)

   Sélectionnez le périphérique que vous voulez enregistrer et cliquez ensuite sur **Enregistrer le périphérique**.

   ![screen_shot_2019-03-04at94641am](assets/screen_shot_2019-03-04at94641am.png)

   Vous devez valider le code en le vérifiant à partir du navigateur web ou du lecteur AEM Screens.

   Cliquez sur **Valider** pour accéder à l’écran **Enregistrement du périphérique**.

   ![screen_shot_2019-03-04at94738am](assets/screen_shot_2019-03-04at94738am.png)

   Saisissez le **titre** et cliquez sur **Enregistrer** pour que le périphérique soit enregistré.

   Cliquez sur **Terminer** pour terminer l’étape d’enregistrement du périphérique.

   ![screen_shot_2019-03-04at94901am](assets/screen_shot_2019-03-04at94901am.png)

   En cliquant sur **Terminer**, vous retournez à la page des périphériques qui affiche les périphériques attribués et non attribués.

   ![screen_shot_2019-03-04at94943am](assets/screen_shot_2019-03-04at94943am.png)

   >[!NOTE]
   >
   >Le périphérique que vous avez ajouté s’affiche comme **Non attribué** sous l’état **Attribué**.

1. **Attribution du périphérique à afficher**

   Une fois que vous avez enregistré le périphérique, vous devez attribuer le périphérique à un affichage.

   Suivez les étapes ci-dessous pour effectuer l’attribution d’un périphérique :

   1. Sélectionnez le périphérique que vous souhaitez attribuer.
   1. Cliquez sur **Attribuer le périphérique** dans la barre d’actions.
   1. Définissez le chemin d’affichage pour le canal sur */content/screens/Test_Project/***Locations***/TestLocation/TestDisplay.*
   1. Cliquez sur **Attribuer**.
   1. Cliquez sur **Terminer** pour achever le processus. Le périphérique est désormais attribué.
   ![screen_shot_2019-03-04at95026am](assets/screen_shot_2019-03-04at95026am.png)

   Le tableau de bord s’ouvre et affiche toutes les informations relatives aux planifications et aux canaux attribués, ainsi que les informations de configuration du périphérique.

   ![screen_shot_2019-03-04at95124am](assets/screen_shot_2019-03-04at95124am.png)

### Affichage du contenu dans le lecteur Screens {#viewing-the-content-in-screens-player}

Une fois que vous avez ajouté les configurations ci-dessus, le lecteur doit automatiquement afficher le canal par défaut pour l’affichage sur votre périphérique, par exemple une image (dans ce cas, un canal de séquence et le contenu sont visibles dans le lecteur Screens pour le navigateur web).

![screen_shot_2019-03-04at95334am](assets/screen_shot_2019-03-04at95334am.png)

See [AEM Screens Player](working-with-screens-player.md), to get more detailed information on AEM Screens player.

### Ressources supplémentaires {#additional-resources}

Pour une présentation approfondie pour tous les modules de Screens, reportez-vous aux ressources suivantes :

1. [Installation et configuration de Screens](configuring-screens-introduction.md) 
1. [Création et gestion de projet Screens](creating-a-screens-project.md)
1. [Affectation de dispositifs](managing-devices.md)
1. [Création et gestion des canaux](managing-channels.md)
1. [Création et gestion des emplacements](managing-locations.md)
1. [Création et gestion des affichages](managing-displays.md)
1. [Affectation de canaux](channel-assignment.md)
1. [Gestion des périphériques](managing-devices.md)
1. [Création et gestion des planifications](managing-schedules.md)
1. [Lecteur AEM Screens](working-with-screens-player.md)
1. [Résolution des problèmes du Centre de contrôle des périphériques](monitoring-screens.md)

