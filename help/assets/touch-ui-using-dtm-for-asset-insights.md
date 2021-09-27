---
title: Activation des statistiques sur les ressources via DTM
description: Découvrez comment utiliser Adobe Dynamic Tag Management (DTM) pour activer Assets Insights.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: 2b3a6972d703314d56d3dc711fb6a514cb1942d5
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 36%

---

# Activation des statistiques sur les ressources via DTM {#enabling-asset-insights-through-dtm}

La gestion dynamique des balises Adobe est un outil permettant d’activer vos outils de marketing numérique. Il est fourni gratuitement aux clients d’Adobe Analytics. Vous pouvez personnaliser votre code de suivi pour permettre aux solutions CMS tierces d’utiliser Assets Insights ou utiliser la gestion dynamique des balises pour insérer des balises Assets Insights. Les statistiques sont uniquement prises en charge et fournies pour les images.

>[!CAUTION]
>
>Adobe de la gestion dynamique des balises est abandonnée au profit de [!DNL Adobe Experience Platform] et atteindra bientôt la [fin de vie](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f). Adobe vous recommande [d’utiliser [!DNL Adobe Experience Platform] pour les informations sur les ressources](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html).

Effectuez les étapes suivantes pour activer Assets Insights via DTM :

1. Appuyez/cliquez sur le logo AEM, puis accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Configuration des statistiques]**.
1. [Configuration de l’instance AEM avec le service cloud de gestion dynamique des balises](../sites-administering/dtm.md)

   Le jeton API doit être disponible une fois que vous vous connectez à [https://dtm.adobe.com](https://dtm.adobe.com/) et que vous accédez à **[!UICONTROL Paramètres du compte]** à partir de l’icône Profil . Cette étape n’est pas requise du point de vue d’Assets Insights, car l’intégration d’AEM Sites à Assets Insights est toujours en cours d’exécution.

1. Connectez-vous à [https://dtm.adobe.com](https://dtm.adobe.com/) et sélectionnez une entreprise, comme approprié.
1. Création/ouverture d’une propriété web existante

   * Sélectionnez l’onglet **[!UICONTROL Propriétés web]**, puis appuyez/cliquez sur **[!UICONTROL Ajouter une propriété]**.
   * Mettez les champs à jour selon les besoins, puis appuyez/cliquez sur **[!UICONTROL Créer une propriété]** (voir [documentation](https://helpx.adobe.com/fr/experience-manager/using/dtm.html)).

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. Dans l’onglet **[!UICONTROL Règles]**, sélectionnez **[!UICONTROL Règles de chargement de page]** dans le volet de navigation, puis appuyez/cliquez sur **[!UICONTROL Créer une règle]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. Développez **[!UICONTROL Balises JavaScript/tierces]**. Ensuite, appuyez/cliquez sur **[!UICONTROL Ajouter un nouveau script]** dans l’onglet **[!UICONTROL HTML séquentiel]** pour ouvrir la boîte de dialogue Script.

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. Appuyez/cliquez sur le logo AEM, puis accédez à **[!UICONTROL Outils > Ressources]**.
1. Appuyez/cliquez sur **[!UICONTROL Dispositif de suivi de la page de statistiques]**, copiez le code de suivi, puis collez-le dans la boîte de dialogue Script que vous avez ouverte à l’étape 6. Enregistrez les modifications.

   >[!NOTE]
   >
   >* `AppMeasurement.js` a été supprimé. Il devrait être disponible via l’outil de gestion dynamique des balises Adobe Analytics.
   >* L’appel à `assetAnalytics.dispatcher.init()` est supprimé. Le système s’attend à ce que la fonction soit appelée une fois le chargement de l’outil de gestion dynamique des balises Adobe Analytics terminé.
   >* Selon l’emplacement d’hébergement du dispositif de suivi de la page de statistiques sur les ressources (par exemple AEM, CDN, etc.), l’origine de la source du script peut nécessiter des modifications.
   >* Pour le dispositif de suivi de page hébergé AEM, la source doit pointer vers une instance de publication à l’aide du nom d’hôte de l’instance de Dispatcher.


1. Ouvrez [https://dtm.adobe.com](https://dtm.adobe.com). Cliquez sur Aperçu dans la propriété web et cliquez sur Ajouter un outil ou ouvrez un outil Adobe Analytics existant. Lors de la création de l’outil, vous pouvez définir la méthode de configuration sur Automatique.

   ![chlimage_1-196](assets/chlimage_1-196.png)

   Sélectionnez des suites de rapports de production/intermédiaires, selon les besoins.

1. Développez **[!UICONTROL Gestion de bibliothèque]** et assurez-vous que **[!UICONTROL Charger la bibliothèque à]** est défini sur **[!UICONTROL Haut de page]**.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. Développez **[!UICONTROL Personnaliser le code de page]**, puis cliquez ou appuyez sur **[!UICONTROL Ouvrir l’éditeur]**.

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

   * La règle de chargement de page dans la gestion dynamique des balises inclut uniquement le code pagetracker.js . Tous les champs `assetAnalytics` sont considérés comme des remplacements des valeurs par défaut. Ils ne sont pas requis par défaut.
   * Le code appelle `assetAnalytics.dispatcher.init()` après avoir vérifié que `_satellite.getToolsByType('sc')[0].getS()` est initialisé et que `assetAnalytics,dispatcher.init` est disponible. Par conséquent, vous pouvez ignorer son ajout à l’étape 11.
   * Comme indiqué dans les commentaires dans le code de suivi de page de statistiques (**[!UICONTROL Outils > Ressources > Dispositif de suivi de la page de statistiques]**), lorsque le dispositif de suivi de page ne crée pas d’objet `AppMeasurement`, les trois premiers arguments (RSID, Serveur de suivi et Espace de noms du visiteur) ne sont pas pertinents. Des chaînes vides sont transmises à la place pour mettre ceci en évidence.

      Les arguments restants correspondent à ce qui est configuré sur la page Configuration des statistiques (**[!UICONTROL Outils > Ressources > Configuration des statistiques]**).

   * L’objet AppMeasurement est récupéré en interrogeant `satelliteLib` pour tous les moteurs SiteCatalyst disponibles. Si plusieurs balises sont configurées, modifiez l’index du sélecteur de tableau de manière appropriée. Les entrées du tableau sont triées en fonction des outils SiteCatalyst disponibles dans l’interface de gestion dynamique des balises.

1. Enregistrez et fermez la fenêtre Éditeur de code, puis enregistrez les modifications dans la configuration de l’outil.
1. Dans l&#39;onglet **[!UICONTROL Validations]** , validez les deux validations en attente. La balise DTM est prête à être insérée sur votre page web. Pour plus d’informations sur l’insertion de balises DTM dans les pages web, voir la page archivée sur [l’intégration de DTM dans les modèles de page personnalisés](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template).
