---
title: Configuration des statistiques des ressources
description: Découvrez comment configurer Assets Insights en AEM Assets.
contentOwner: AG
feature: Statistiques sur les ressources,Rapports sur les ressources
role: Business Practitioner,Administrator
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 70%

---

# Configuration des informations sur les ressources {#configuring-asset-insights}

Adobe Experience Manager (AEM) Assets récupère les données d’utilisation des ressources AEM utilisées par les sites web tiers à partir d’Adobe Analytics. Pour permettre à Assets Insights de récupérer ces données et de générer des statistiques, configurez d’abord la fonction à intégrer à Adobe Analytics.

>[!NOTE]
>
>Les statistiques sont uniquement prises en charge et fournies pour les images.

1. Dans AEM, cliquez sur **[!UICONTROL Outils > Ressources]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Cliquez sur la carte **[!UICONTROL Configuration des statistiques]**.
1. Dans l’assistant, sélectionnez un centre de données et fournissez vos informations d’identification, notamment le nom de votre société, votre nom d’utilisateur et votre mot de passe.

   ![chlimage_1-211](assets/insights_config2.png)

1. Cliquez/appuyez sur **[!UICONTROL Authentifier]**.
1. Une fois AEM authentifié vos informations d’identification, dans la liste **[!UICONTROL Report Suite]**, choisissez une suite de rapports Adobe Analytics à partir de laquelle vous souhaitez que Assets Insights récupère les données. Cliquez sur **[!UICONTROL Ajouter]**.
1. Une fois qu’AEM configure votre suite de rapports, appuyez/cliquez sur **[!UICONTROL Terminé]**.

## Suivi de page {#page-tracker}

Une fois que vous avez configuré votre compte Analytics, le code de suivi de page est généré pour vous. Pour permettre à la fonction Statistiques sur les ressources de surveiller les ressources AEM utilisées sur les sites web tiers, incluez le code de suivi de page dans le code du site web. Utilisez l’utilitaire de suivi de page d’AEM Assets pour générer le code de suivi de page. Pour plus d’informations sur la manière d’inclure votre code de suivi de page sur des pages web tierces, reportez-vous à la section [Utilisation du dispositif de suivi de page et du code intégré sur les pages web](touch-ui-using-page-tracker.md).

1. Dans AEM, cliquez sur **[!UICONTROL Outils > Ressources]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Sur la page **[!UICONTROL Navigation]**, cliquez sur la carte **[!UICONTROL Dispositif de suivi de la page de statistiques]**.
1. Cliquez sur l’icône **[!UICONTROL Télécharger]** pour télécharger le code de suivi de page.
