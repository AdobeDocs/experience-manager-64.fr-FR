---
title: Incorporation d’une application REACT à l’aide de l’éditeur d’applications monopages AEM et intégration à AEM Screens Analytics
seo-title: Incorporation d’une application REACT à l’aide de l’éditeur d’applications monopages AEM et intégration à AEM Screens Analytics
description: Consultez cette page pour savoir comment incorporer une application interactive monopage en utilisant REACT (ou Angular) à l’aide de l’éditeur d’applications monopages AEM qui peut être configuré par des professionnels dans AEM et comment intégrer votre application interactive à Adobe Analytics hors ligne.
seo-description: Consultez cette page pour savoir comment incorporer une application interactive monopage en utilisant REACT (ou Angular) à l’aide de l’éditeur d’applications monopages AEM qui peut être configuré par des professionnels dans AEM et comment intégrer votre application interactive à Adobe Analytics hors ligne.
uuid: 02ae67bb-058a-4aa9-b484-0c60a8d897ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 70fdeeb8-0c82-44f3-a6fa-ee4dfb32a90b
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Incorporation d’une application REACT à l’aide de l’éditeur d’applications monopages AEM et intégration à AEM Screens Analytics{#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

Cette section décrit comment incorporer une application interactive monopage en utilisant REACT (ou Angular) à l’aide de l’éditeur d’applications monopages AEM qui peut être configuré par des professionnels dans AEM et comment intégrer votre application interactive à Adobe Analytics hors ligne.

## Utilisation de l’éditeur d’applications monopages AEM {#using-the-aem-spa-editor}

Suivez les étapes ci-dessous pour utiliser l’éditeur d’applications monopages AEM :

1. Cliquez sur le rapport de l’éditeur d’applications monopages AEM à l’adresse [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Cet archétype crée un projet Adobe Experience Manager minimal qui s’appuie sur des bonnes pratiques pour que vous puissiez démarrer vos propres projets d’application monopage (SPA). Les propriétés qui doivent être fournies lors de l’utilisation de cet archétype permettent de nommer comme vous le souhaitez toutes les parties de ce projet.

1. Suivez les instructions du fichier Lisez-moi pour créer un projet d’archétype d’éditeur SPA AEM :

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >Nous utilisons comme **GroupId** ***com.adobe.aem.screens*** et comme **ArtifactId** ***My Sample SPA*** (valeur par défaut). Vous pouvez choisir les vôtres selon vos besoins.

1. Une fois le projet créé, utilisez un IDE ou un éditeur de votre choix et importez le projet Maven généré.
1. Déployez sur votre instance AEM locale à l’aide de la commande ***mvn clean install -PautoInstallPackage***.

### Modification de contenu dans l’application REACT {#editing-content-in-the-react-app}

Pour modifier le contenu dans l’application REACT :

1. Accédez à ***http://localhost:4502/editor.html/content/mysamplespa/en/home.html*** (remplacez le nom d’hôte, le port et le nom du projet, selon le cas).
1. Vous devez pouvoir modifier le texte affiché dans l’application Hello world.

### Ajout de l’application interactive REACT à AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Suivez les étapes ci-dessous pour ajouter l’application interactive REACT à AEM Screens :

1. Créez un projet AEM Screens. Voir [Création et gestion de projets](/help/screens/creating-a-screens-project.md) pour en savoir plus.

   >[!NOTE]
   >
   >Créez un **Canal de séquence** lors de la création d’un canal dans le dossier **Canaux** de votre projet Screens.
   >
   >Voir [Création et gestion des canaux](/help/screens/managing-channels.md) pour plus d’informations.

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. Modifiez un canal de séquence et faites glisser et déposez un composant de page incorporé.

   Voir [Ajout de composants à un canal](/help/screens/adding-components-to-a-channel.md) pour en savoir plus.

   >[!NOTE]
   >
   >Veillez à ajouter l’événement d’interaction utilisateur lors de l’attribution du canal à l’affichage.

1. Cliquez sur **Modifier** dans la barre d’actions pour modifier les propriétés du canal de séquence.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Faites glisser et déposez le composant **Page incorporée** et sélectionnez la page d’accueil sous l’application mysamplespa, par exemple ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Enregistrez un lecteur sur ce projet. Vous devriez maintenant voir votre application interactive s’exécuter sur AEM Screens.

   Reportez-vous à la section [Enregistrement du périphérique](/help/screens/device-registration.md) pour en savoir plus sur l’enregistrement d’un périphérique.

## Intégration de l’application monopage avec Adobe Analytics avec la fonctionnalité hors ligne via AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Suivez les étapes ci-dessous pour intégrer l’application monopage à Adobe Analytics avec la fonctionnalité hors ligne via AEM Screens :

1. Configuration d’Adobe Analytics dans AEM Screens.

   Refer to [Configuring Adobe Analytics with AEM Screens](/help/screens/configuring-adobe-analytics-aem-screens.md) to learn how to perform sequencing in Adobe Analytics with AEM Screens and send custom events using offline Adobe Analytics.

1. Modifiez votre application de réaction dans l’IDE/l’éditeur de votre choix (en particulier le composant de texte ou tout autre composant dont vous souhaitez qu’il commence à émettre des événements).
1. Sur l’événement click ou tout autre événement que vous souhaitez capturer pour votre composant, ajoutez les informations d’analyse à l’aide du modèle de données standard.

   Refer to [Configuring Adobe Analytics with AEM Screen](/help/screens/configuring-adobe-analytics-aem-screens.md)s for more details.

1. Appelez l’API Analytics d’AEM Screens pour enregistrer l’événement hors ligne et l’envoyer en rafales à Adobe Analytics.

   Par exemple :

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().getTime(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().getTime(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().getTime(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >Le micrologiciel du lecteur ajoute automatiquement plus de détails sur le lecteur et son environnement d’exécution aux données d’analyse personnalisées que vous envoyez. Il se peut donc que vous n’ayez pas à capturer les détails du système d’exploitation/du périphérique de bas niveau, sauf si cela est absolument nécessaire. Vous devez simplement vous concentrer sur les données d’analyse de l’entreprise.

