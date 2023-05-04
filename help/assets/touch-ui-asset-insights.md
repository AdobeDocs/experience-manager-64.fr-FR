---
title: Utilisez la fonction Statistiques sur les ressources pour effectuer le suivi de l’utilisation de vos images.
description: La fonction Statistiques sur les ressources vous permet d’effectuer le suivi des évaluations des utilisateurs et des statistiques d’utilisation des images utilisées dans les sites web tiers, les campagnes marketing et les solutions de création d’Adobe.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 42%

---

# Assets Insights {#asset-insights}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Découvrez comment la fonction Statistiques sur les ressources vous permet d’effectuer le suivi des évaluations des utilisateurs et des statistiques d’utilisation des ressources utilisées dans des sites web tiers, des campagnes marketing et des solutions de création d’Adobe.

La fonction Statistiques sur les ressources vous permet de suivre les évaluations des utilisateurs et les statistiques d’utilisation des ressources utilisées dans les sites web tiers, les campagnes marketing et les solutions de création de l’Adobe afin d’obtenir des informations sur leurs performances et leur popularité.

La fonction Statistiques sur les ressources capture les détails de l’activité des utilisateurs, tels que le nombre de fois où une ressource est évaluée, a fait l’objet d’un clic et les impressions (nombre de fois où la ressource est chargée sur le site web). Il attribue des scores aux ressources en fonction de ces statistiques. Vous pouvez utiliser les scores et les statistiques de performances pour sélectionner les ressources populaires à inclure dans les catalogues, les campagnes marketing, etc. Vous pouvez même formuler des stratégies d’archivage et de renouvellement de licence pour les ressources en fonction de ces statistiques.

Pour que la fonction Statistiques sur les ressources capture les statistiques d’utilisation des ressources d’un site web, vous devez inclure le code incorporé de la ressource dans le code du site web.

Pour afficher les statistiques d’utilisation des ressources, commencez par configurer la fonction afin qu’elle récupère les données de rapports d’[!DNL Adobe Analytics]. Pour plus d’informations, consultez [Configuration d’Assets Insights](touch-ui-configuring-asset-insights.md). Pour utiliser cette fonctionnalité dans une installation on-premise, achetez le licence [!DNL Adobe Analytics] séparément. Les clients [!DNL Managed Services] reçoivent une licence [!DNL Analytics] groupée avec [!DNL Experience Manager]. Consultez [Description du produit Managed Services](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Les statistiques sont uniquement prises en charge et fournies pour les images.

## Affichage des statistiques pour une ressource {#viewing-statistics-for-an-asset}

Vous pouvez afficher les scores de statistiques sur les ressources à partir de la page des métadonnées.

1. Dans l’interface utilisateur d’Assets, sélectionnez la ressource, puis appuyez/cliquez sur le bouton **[!UICONTROL Propriétés]** dans la barre d’outils.
1. Sur la page Propriétés, appuyez/cliquez sur le **[!UICONTROL Insights]** .
1. Consultez les détails d’utilisation de la ressource dans l’onglet **[!UICONTROL Statistiques]**. Le **[!UICONTROL Score]** décrit les scores totaux d’utilisation et de performances d’une ressource .

   Le score d’utilisation indique le nombre de fois que la ressource est utilisée dans diverses solutions.

   Le **[!UICONTROL Impressions]** score correspond au nombre de fois où la ressource est chargée sur le site web. Le nombre affiché sous **[!UICONTROL Clics]** correspond au nombre de clics sur la ressource.

1. Passez en revue la section **[!UICONTROL Statistiques d’utilisation]** pour savoir de quelles entités la ressource faisait partie et dans quelles solutions de création elle a récemment été utilisée. Plus l’utilisation est élevée, plus la ressource a de chances d’être populaire auprès des utilisateurs. Les données d’utilisation s’affichent sous les sections suivantes :

   * **[!UICONTROL Ressource]** : nombre de fois où la ressource faisait partie d’une collection ou d’une ressource composite
   * **[!UICONTROL Web et mobile]** : nombre de fois où la ressource faisait partie de sites web et d’applications
   * **[!UICONTROL Social]** : nombre de fois où la ressource a été utilisée dans des solutions, comme Adobe Social et Adobe Campaign
   * **[!UICONTROL E-mail]** : nombre de fois où la ressource a été utilisée dans des campagnes par e-mail

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >La fonction Statistiques sur les ressources récupère les données des solutions [!DNL Adobe Analytics] de manière périodique, la section solutions peut ne pas afficher les données les plus récentes. La période pour laquelle les données sont affichées dépend du planning de l’opération de récupération exécutée par Assets Insights pour récupérer les données. [!DNL Analytics] data.

1. Pour afficher les statistiques de performances de l’actif sous forme graphique sur une période donnée, sélectionnez une période dans la section **[!UICONTROL Statistiques de performances]**. Les détails, y compris les clics et les impressions, sont affichés sous forme de lignes de tendance dans un graphique.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Contrairement aux données de la section solutions , la section Statistiques de performances affiche les données les plus récentes.

1. Pour obtenir le code intégré de la ressource que vous incluez sur les sites Web afin d’obtenir les données de performances, cliquez sur **[!UICONTROL Obtenir le code intégré]** au-dessous de la miniature de la ressource. Pour plus d’informations sur la manière d’inclure votre code intégré dans des pages web tierces, voir [Utilisation du dispositif de suivi de page et du code intégré dans les pages web](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Affichage des statistiques agrégées pour les ressources {#viewing-aggregate-statistics-for-assets}

Vous pouvez afficher les scores de toutes les ressources d’un dossier simultanément à l’aide du **[!UICONTROL mode Statistiques]**.

1. Dans l’interface utilisateur d’Assets, accédez au dossier contenant les ressources pour lesquelles vous souhaitez afficher des informations.
1. Appuyez/cliquez sur l’icône Mise en page de la barre d’outils, puis choisissez **[!UICONTROL Vue Statistiques]**.
1. La page affiche les scores d’utilisation des ressources. Comparez les évaluations des différentes ressources et tirez-en des conclusions.

## Planification d’une tâche en arrière-plan {#scheduling-background-job}

La fonction Assets Insights extrait les données d’utilisation des ressources à partir de suites de rapports Adobe Analytics de manière périodique. Par défaut, la fonction Assets Insights exécute une tâche en arrière-plan toutes les 24 heures, à 2 heures du matin, pour récupérer les données. Cependant, vous pouvez modifier la fréquence et l’heure en configurant le service de **[!UICONTROL tâche de synchronisation de rapport de performances de ressource de gestion des ressources numériques Adobe CQ]** via la console Web.

1. Appuyez sur le bouton [!DNL Experience Manager] et accédez à **[!UICONTROL Outils > Opérations > Console web]**.
1. Ouvrez la configuration de service **[!UICONTROL Tâche de synchronisation des rapports sur les performances des ressources de la gestion des actifs numériques Adobe CQ]**.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Spécifiez la fréquence du planificateur et l’heure de début de la tâche dans l’expression du planificateur de propriété. Enregistrez les modifications.
