---
title: Enregistrement automatique d’un formulaire adaptatif
seo-title: Auto-save an adaptive form
description: Vous pouvez configurer un formulaire adaptatif pour démarrer automatiquement l’enregistrement du contenu en fonction d’un événement ou d’un intervalle de temps prédéfini
seo-description: You can configure an adaptive form to automatically start saving the content based on an event or a pre-defined time-interval
uuid: 0fe9a389-269b-438a-9489-d9d1d09558a1
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: d519ac4e-6d29-4a69-874e-792acabe87ff
feature: Adaptive Forms
exl-id: 073734e9-449b-463a-b539-d73e11f50fa4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 100%

---

# Enregistrement automatique d’un formulaire adaptatif {#auto-save-an-adaptive-form}

Vous pouvez configurer un formulaire adaptatif pour démarrer automatiquement l’enregistrement du contenu en fonction d’un événement ou d’un intervalle de temps prédéfini. Par défaut, le contenu d’un formulaire adaptatif est enregistré lors d’une action utilisateur (par exemple, lorsque l’utilisateur appuie sur le bouton d’enregistrement). L’option d’enregistrement automatique est utile pour :

* Enregistrement automatique du contenu pour les utilisateurs anonymes et connectés
* Enregistrement du contenu d’un formulaire sans intervention ou une intervention minimale de l’utilisateur
* Commencer à enregistrer le contenu d’un formulaire en fonction d’un événement utilisateur
* Enregistrer le contenu d’un formulaire à plusieurs reprises après un intervalle de temps spécifié

## Activer l’enregistrement automatique d’un formulaire adaptatif {#enable-autosave-for-an-adaptive-form}

Pour un formulaire adaptatif, l’option d’enregistrement automatique n’est par défaut pas activée. Vous pouvez activer l’option d’enregistrement automatique dans la section **Enregistrement automatique** dans les propriétés d’un formulaire adaptatif. La section **Enregistrement automatique** fournit également d’autres options de configuration. Effectuez les étapes suivantes afin d’activer et de configurer l’option d’enregistrement automatique pour un formulaire adaptatif :

1. Pour accéder à la section d’enregistrement automatique dans les propriétés, sélectionnez un composant, puis cliquez sur ![field-level](assets/field-level.png) > **[!UICONTROL Conteneur de formulaires adaptatifs]**, puis cliquez sur ![cmppr](assets/cmppr.png).
1. Dans la section **[!UICONTROL Sauvegarde automatique]**, **[!UICONTROL activez]** l’option d’enregistrement automatique.
1. Dans la boîte de dialogue **[!UICONTROL Evénement de formulaire adaptatif]**, spécifiez 1 ou TRUE pour lancer automatiquement l’enregistrement du formulaire lorsque celui-ci est chargé dans le navigateur. Vous pouvez également spécifier une expression conditionnelle pour un événement qui, lorsqu’il est déclenché et renvoie true, commence l’enregistrement du contenu du formulaire.
1. Spécifiez le déclencheur. L’enregistrement automatique est déclenché en fonction de votre configuration. Vous avez le choix entre :

   * **[!UICONTROL Basé sur l’heure :]** sélectionnez l’option pour commencer à enregistrer le contenu selon un intervalle de temps spécifié.
   * **[!UICONTROL Basé sur les événements :]** sélectionnez l’option pour commencer à enregistrer le contenu sur la base d’un événement déclenché.

   Lorsque vous sélectionnez un déclencheur, la zone Configuration de la stratégie est activée. La zone Configuration de la stratégie vous permet d’effectuer les opérations suivantes :

   * Spécifiez un intervalle de temps si vous sélectionnez un déclencheur **[!UICONTROL basé sur l’heure]**.
   * Spécifiez un nom d’événement si vous sélectionnez un déclencheur **[!UICONTROL basé sur un événement.]**

   Vous pouvez également créer et ajouter à la liste votre propre stratégie personnalisée. Pour plus d’informations, reportez-vous à la section [Mise en œuvre d’une stratégie personnalisée pour enregistrer automatiquement les formulaires](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (Enregistrement automatique basé sur un moment uniquement) Exécutez les étapes suivantes pour configurer les options de l’enregistrement automatique basé sur un moment.

   1. Dans le champ **[!UICONTROL Enregistrement automatique sur cet intervalle]**, indiquez l’intervalle en secondes. Le formulaire est enregistré à plusieurs reprises après écoulement du nombre de secondes spécifié dans la zone d’intervalle.

1. (Enregistrement automatique basé sur un événement uniquement) Exécutez les étapes suivantes pour configurer les options d’enregistrement automatique basé sur un événement.

   1. Dans la zone **Enregistrement automatique après cet événement**, spécifiez un événement [GuideBridge](https://helpx.adobe.com/fr/aem-forms/6/javascript-api/GuideBridge.html). Le formulaire est enregistré chaque fois que l’expression renvoie TRUE.

1. (Facultatif) Pour enregistrer automatiquement le contenu pour des utilisateurs anonymes, sélectionnez l’option **Activer l’enregistrement automatique pour les utilisateurs anonymes**, puis cliquez sur **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Pour que l’option d’enregistrement automatique fonctionne pour les utilisateurs anonymes, assurez-vous de configurer le service de configuration commun aux formulaires pour autoriser tous les utilisateurs à prévisualiser, vérifier et signer des formulaires.
   >
   >Pour configurer le service, accédez à la configuration d’AEM Web Console à l’adresse `https://[server]:[host]/system/console/configMgr`, puis modifiez le **[!UICONTROL Service de configuration commun Forms]** afin de choisir l’option **[!UICONTROL Tous les utilisateurs]** dans le champ **[!UICONTROL Autoriser]** et enregistrez la configuration.

## Mise en œuvre d’une stratégie personnalisée afin d’activer l’enregistrement automatique pour les formulaires adaptatifs {#implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms}

Vous pouvez mettre en œuvre un événement personnalisé pour déclencher la fonctionnalité d’enregistrement automatique. Effectuez les étapes suivantes pour créer et mettre en œuvre l’événement personnalisé :

1. Créez une bibliothèque client et des dossiers de bibliothèque client. Pour les étapes détaillées, voir le [document Utilisation de bibliothèques côté client](/help/sites-developing/clientlibs.md).

   Par exemple, le script suivant utilise l’événement personnalisé `emailFocusChange` pour déclencher la fonctionnalité d’enregistrement automatique :

   ```
   window.addEventListener("bridgeInitializeStart", function (){   
       guideBridge.connect(function () { guideBridge.on("elementFocusChanged", function (event,data) { 
           if(data.target.name === 'Email') {
               guideBridge.trigger("emailFocusChange");
           }
       });
      });
   });
   ```

   >[!NOTE]
   >
   >Une propriété de catégorie est définie lors de la création des dossiers de bibliothèque client. Conservez à portée de main la valeur affectée à la propriété de catégorie.

1. Ouvrez le formulaire adaptatif en mode création.

1. En mode d’édition, sélectionnez un composant, puis appuyez sur ![field-level](assets/field-level.png) > **[!UICONTROL Conteneur de formulaires adaptatifs]**, puis appuyez sur ![cmppr](assets/cmppr.png).
1. Dans les propriétés, ouvrez la section **[!UICONTROL Standard]**. Dans la zone **[!UICONTROL Catégorie de bibliothèque cliente]**, entrez la valeur de la propriété de catégorie définie lors de la création des dossiers de bibliothèque cliente.
1. Ouvrez la section Enregistrement automatique. Dans le champ **[!UICONTROL Enregistrement automatique après cet événement]**, spécifiez un événement personnalisé déjà défini dans la bibliothèque client. Cliquez sur **[!UICONTROL OK]**.
