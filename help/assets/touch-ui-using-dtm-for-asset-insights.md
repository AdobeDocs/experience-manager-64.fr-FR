---
title: Activation des statistiques sur les ressources via DTM
description: Découvrez comment utiliser la gestion dynamique des balises d’Adobe pour activer Assets Insights.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 52%

---

# Activation des statistiques sur les ressources via DTM {#enabling-asset-insights-through-dtm}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La gestion dynamique des balises Adobe est un outil permettant d’activer vos outils de marketing numérique. Il est fourni gratuitement aux clients d’Adobe Analytics. Vous pouvez personnaliser votre code de suivi pour permettre aux solutions CMS tierces d’utiliser Assets Insights ou la gestion dynamique des balises pour insérer des balises Assets Insights. Insights n’est pris en charge et fourni que pour les images.

>[!CAUTION]
>
>La gestion dynamique des balises d’Adobe est obsolète et remplacée par [!DNL Adobe Experience Platform]. Elle atteindra bientôt sa [fin de vie](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f). Adobe vous recommande d’[utiliser  [!DNL Adobe Experience Platform]  pour Assets Insights](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html?lang=fr).

Effectuez ces étapes pour activer Assets Insights grâce à la gestion dynamique des balises:

1. Appuyez/cliquez sur le bouton [!DNL Experience Manager] et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Configuration des statistiques]**.
1. [Configurer [!DNL Experience Manager] instance avec le Cloud Service DTM](../sites-administering/dtm.md)

   Le jeton API doit être disponible une fois que vous vous connectez à [https://dtm.adobe.com](https://dtm.adobe.com/) et visite **[!UICONTROL Paramètres du compte]** à partir de l’icône Profil . Cette étape n’est pas requise du point de vue d’Assets Insights, car l’intégration de [!DNL Experience Manager Sites] avec Assets Insights est toujours en cours d’exécution.

1. Connectez-vous à [https://dtm.adobe.com](https://dtm.adobe.com/), puis sélectionnez une société, le cas échéant.
1. Créer/ouvrir une propriété web existante

   * Sélectionnez la **[!UICONTROL Propriétés web]** , puis appuyez/cliquez sur **[!UICONTROL Ajouter une propriété]**.
   * Mettez les champs à jour selon les besoins, puis appuyez/cliquez sur **[!UICONTROL Créer une propriété]** (voir [documentation](https://helpx.adobe.com/fr/experience-manager/using/dtm.html)).

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. Dans le **[!UICONTROL Règles]** onglet, sélectionnez **[!UICONTROL Règles de chargement de page]** dans le volet de navigation, puis appuyez/cliquez sur **[!UICONTROL Créer une règle]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. Développer **[!UICONTROL Balises JavaScript/tierces]**. Ensuite, appuyez/cliquez sur **[!UICONTROL Ajouter un nouveau script]** dans le **[!UICONTROL HTML séquentiel]** pour ouvrir la boîte de dialogue Script.

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. Appuyez/cliquez sur le bouton [!DNL Experience Manager] et accédez à **[!UICONTROL Outils > Ressources]**.
1. Appuyez/cliquez sur **[!UICONTROL Suivi de page Insights]**, copiez le code de suivi, puis collez-le dans la boîte de dialogue Script que vous avez ouverte à l’étape 6. Enregistrez les modifications.

   >[!NOTE]
   >
   >* `AppMeasurement.js` a été supprimé. Il devrait être disponible via l’outil de gestion dynamique des balises Adobe Analytics.
   >* L’appel à `assetAnalytics.dispatcher.init()` est supprimé. La fonction devrait être appelée une fois le chargement de l’outil de gestion dynamique des balises Adobe Analytics terminé.
   >* Selon l’emplacement d’hébergement du dispositif de suivi de la page de statistiques sur les ressources (par exemple AEM, CDN, etc.), l’origine de la source du script peut nécessiter des modifications.
   >* Pour le dispositif de suivi de page hébergé AEM, la source doit pointer vers une instance de publication à l’aide du nom d’hôte de l’instance de Dispatcher.


1. Ouvrir [https://dtm.adobe.com](https://dtm.adobe.com). Cliquez sur Aperçu dans la propriété web et cliquez sur Ajouter un outil, ou ouvrez un outil Adobe Analytics existant. Pendant la création de l’outil, vous pouvez définir la méthode de configuration sur Automatique.

   ![chlimage_1-196](assets/chlimage_1-196.png)

   Sélectionnez des suites de rapports d’exploitation ou intermédiaires, selon vos besoins.

1. Développez **[!UICONTROL Gestion de la bibliothèque]** et assurez-vous que l’option **[!UICONTROL Charger la bibliothèque sur]** est définie sur **[!UICONTROL Haut de la page]**.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. Développer **[!UICONTROL Personnalisation du code de page]**, puis cliquez ou appuyez sur **[!UICONTROL Ouvrir l’éditeur]**.

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
   * Le code appelle `assetAnalytics.dispatcher.init()` après s’être assuré que `_satellite.getToolsByType('sc')[0].getS()` est initialisé et que `assetAnalytics,dispatcher.init` est disponible. Par conséquent, vous pouvez ignorer son ajout à l’étape 11.
   * Comme indiqué dans les commentaires dans le code du dispositif de suivi de la page Insights (**[!UICONTROL Outils > Ressources > Dispositif de suivi de la page Insights]**), lorsque le dispositif de suivi de la page ne crée pas d’objet `AppMeasurement`, les trois premiers arguments (RSID, Serveur de suivi et Espace de noms du visiteur) ne sont pas pertinents. Des chaînes vides sont transmises à la place pour mettre ceci en évidence.

      Les arguments restants correspondent à ce qui est configuré sur la page Configuration des statistiques (**[!UICONTROL Outils > Ressources > Configuration d’Insights]**).

   * L’objet AppMeasurement est récupéré en interrogeant `satelliteLib` pour tous les moteurs SiteCatalyst disponibles. Si plusieurs balises sont configurées, modifiez l’index du sélecteur de tableau de manière appropriée. Les entrées du tableau sont classées selon les outils par SiteCatalyst disponibles dans l’interface de DTM.

1. Enregistrez et fermez la fenêtre Éditeur de code, puis enregistrez les modifications dans la configuration Outil.
1. Dans l’onglet **[!UICONTROL Approbations]**, validez les deux approbations en attente. La balise DTM est prête à être insérée sur votre page web. Pour plus d’informations sur l’insertion de balises DTM dans des pages web, reportez-vous à la page archivée à propos de [intégration de DTM dans les modèles de page personnalisés](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template).
