---
title: Activation des statistiques sur les ressources via DTM
description: Découvrez comment utiliser la gestion dynamique des balises Adobe pour activer les statistiques sur les ressources.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 50%

---


# Activation des statistiques sur les ressources via DTM {#enabling-asset-insights-through-dtm}

La gestion dynamique des balises Adobe est un outil permettant d’activer vos outils de marketing numérique. Il est fourni gratuitement aux clients d’Adobe Analytics. Vous pouvez personnaliser votre code de suivi pour permettre aux solutions CMS tierces d’utiliser Asset Insights ou utiliser la gestion dynamique des balises pour insérer des balises Asset Insights. Les statistiques sont uniquement prises en charge et fournies pour les images.

>[!CAUTION]
>
>La gestion dynamique des balises Adobe est abandonnée en faveur de Adobe Experience Platform Launch et va bientôt [prendre fin](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f). Adobe vous recommande d’ [utiliser Lancer pour obtenir des informations](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html)sur les ressources.

Effectuez les étapes suivantes pour activer les statistiques sur les ressources au moyen de la gestion dynamique des balises :

1. Appuyez/cliquez sur le logo AEM, puis accédez à **[!UICONTROL Outils > Ressources > Configuration des statistiques]**.
1. [Configuration de l’instance AEM avec le service cloud de gestion dynamique des balises](../sites-administering/dtm.md)

   The API token should be available once you log on to [https://dtm.adobe.com](https://dtm.adobe.com/) and visit **[!UICONTROL Account Settings]** from the Profile icon. Par rapport aux statistiques sur les ressources, cette étape n’est pas nécessaire car l’intégration d’AEM Sites aux statistiques sur les ressources est encore en cours.

1. Connectez-vous à [https://dtm.adobe.com](https://dtm.adobe.com/) et sélectionnez une entreprise, comme approprié.
1. Création/ouverture d’une propriété web existante

   * Select the **[!UICONTROL Web Properties]** tab, and then tap/click **[!UICONTROL Add Property]**.
   * Update the fields as appropriate, and tap/click **[!UICONTROL Create Property]** (see [documentation](https://helpx.adobe.com/fr/experience-manager/using/dtm.html)).

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. In the **[!UICONTROL Rules]** tab, select **[!UICONTROL Page Load Rules]** from the navigation pane and tap/click **[!UICONTROL Create New Rule]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. Expand **[!UICONTROL Javascript /Third Party Tags]**. Then tap/click **[!UICONTROL Add New Script]** in the **[!UICONTROL Sequential HTML]** tab to open the Script dialog.

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools > Assets]**.
1. Tap/click **[!UICONTROL Insights Page Tracker]**, copy the tracker code, and then paste it in the Script dialog you opened in step 6. Enregistrez les modifications.

   >[!NOTE]
   >
   >* `AppMeasurement.js` a été supprimé. Il devrait être disponible via l’outil de gestion dynamique des balises Adobe Analytics.
   >* The call to `assetAnalytics.dispatcher.init()` is removed. Le système s’attend à ce que la fonction soit appelée une fois le chargement de l’outil de gestion dynamique des balises Adobe Analytics terminé.
   >* Selon l’endroit où est hébergé le dispositif de suivi de la page de statistiques sur les ressources (par exemple, AEM, CDN, etc.), l’origine de la source du script peut nécessiter des modifications.
   >* Pour le suivi des pages hébergé AEM, la source doit pointer vers une instance de publication à l’aide du nom d’hôte de l’instance de répartiteur.


1. Ouvrez [https://dtm.adobe.com](https://dtm.adobe.com). Cliquez sur Aperçu dans la propriété web et cliquez sur Ajouter un outil ou ouvrez un outil Adobe Analytics existant. Lors de la création de l’outil, vous pouvez définir la méthode de configuration sur Automatique.

   ![chlimage_1-196](assets/chlimage_1-196.png)

   Sélectionnez des suites de rapports de production/intermédiaires, selon les besoins.

1. Expand **[!UICONTROL Library Management]**, and ensure that **[!UICONTROL Load Library at]** is set to **[!UICONTROL Page Top]**.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. Expand **[!UICONTROL Customize Page Code]**, and click or tap **[!UICONTROL Open Editor]**.

   ![chlimage_1-198](assets/chlimage_1-198.png)

1. Collez le code suivant dans la fenêtre :

   ```java
   var sObj;
   
   if (arguments.length > 0) {
     sObj = arguments[0];
   } else {
     sObj = _satellite.getToolsByType('sc')[0].getS();
   }
   _satellite.notify('in assetAnalytics customInit');
   (function initializeAssetAnalytics() {
     if ((!!window.assetAnalytics) && (!!assetAnalytics.dispatcher)) {
       _satellite.notify('assetAnalytics ready');
       /** NOTE:
           Copy over the call to 'assetAnalytics.dispatcher.init()' from Assets Pagetracker
           Be mindful about changing the AppMeasurement object as retrieved above.
       */
       assetAnalytics.dispatcher.init(
             "",  /** RSID to send tracking-call to */
             "",  /** Tracking Server to send tracking-call to */
             "",  /** Visitor Namespace to send tracking-call to */
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, e.g. 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, e.g. 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, e.g. 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, e.g. 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, please include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
             );
       sObj.usePlugins = true;
       sObj.doPlugins = assetAnalytics.core.updateContextData;
       assetAnalytics.core.optimizedAssetInsights();
     }
     else {
       _satellite.notify('assetAnalytics not available. Consider updating the Custom Page Code', 4);
     }
   })();
   ```

   * La règle de chargement de page dans DTM inclut uniquement le code pagetracker.js. Tous les champs `assetAnalytics` sont considérés comme des remplacements des valeurs par défaut. Ils ne sont pas requis par défaut.
   * The code calls `assetAnalytics.dispatcher.init()` after making sure that `_satellite.getToolsByType('sc')[0].getS()` is initialized and `assetAnalytics,dispatcher.init` is available. Par conséquent, vous pouvez ignorer son ajout à l’étape 11.
   * As indicated in comments within the Insights Page Tracker code (**[!UICONTROL Tools > Assets > Insights Page Tracker]**), when Page Tracker does not create an `AppMeasurement` object, the first three arguments (RSID, Tracking Server, and Visitor Namespace) are irrelevant. Des chaînes vides sont transmises à la place pour mettre ceci en évidence.

      Les arguments restants correspondent à ce qui est configuré sur la page Configuration des statistiques (**[!UICONTROL Outils > Ressources > Configuration des statistiques]**).

   * L’objet AppMeasurement est récupéré en interrogeant `satelliteLib` pour tous les moteurs SiteCatalyst disponibles. Si plusieurs balises sont configurées, modifiez l’index du sélecteur de tableau de manière appropriée. Les entrées du tableau sont triées en fonction des outils SiteCatalyst disponibles dans l’interface de gestion dynamique des balises.

1. Enregistrez et fermez la fenêtre Editeur de code, puis enregistrez les modifications dans la configuration de l’outil.
1. In the **[!UICONTROL Approvals]** tab, approve both the pending approvals. La balise DTM est prête à être insérée sur votre page web. Pour plus d’informations sur la façon d’insérer des balises DTM sur des pages web, reportez-vous à la section [Intégration de DTM dans des modèles de page personnalisés](https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template/).
