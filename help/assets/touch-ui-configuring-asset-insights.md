---
title: Configuration des statistiques sur les ressources
description: Découvrez comment configurer les statistiques sur les ressources dans [!DNL Experience Manager] Ressources.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 57%

---

# Configuration des statistiques sur les ressources {#configuring-asset-insights}

Adobe Experience Manager Assets récupère les données d’utilisation autour de [!DNL Experience Manager] ressources utilisées par des sites web tiers à partir d’Adobe Analytics. Pour activer Assets Insights afin de récupérer ces données et de générer des informations, commencez par configurer la fonction à intégrer à Adobe Analytics.

>[!NOTE]
>
>Les statistiques sont uniquement prises en charge et fournies pour les images.

1. Dans AEM, cliquez sur **[!UICONTROL Outils > Ressources]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Cliquez sur la carte **[!UICONTROL Configuration des statistiques]**.
1. Dans l’assistant, sélectionnez un centre de données et fournissez vos informations d’identification, notamment le nom de votre société, votre nom d’utilisateur et votre mot de passe.

   ![chlimage_1-211](assets/insights_config2.png)

1. Cliquez/appuyez sur **[!UICONTROL Authentifier]**.
1. Une fois que [!DNL Experience Manager] a authentifié vos identifiants, dans la liste **[!UICONTROL Suite de rapports]**, sélectionnez une suite de rapports Adobe Analytics à partir de laquelle la fonction Statistiques sur les ressources doit récupérer les données. Cliquez sur **[!UICONTROL Ajouter]**.
1. Après [!DNL Experience Manager] configure votre suite de rapports, cliquez/appuyez sur . **[!UICONTROL Terminé]**.

## Suivi de page {#page-tracker}

Une fois que vous avez configuré votre compte Analytics, le code de suivi de page est généré pour vous. Pour activer le suivi des statistiques sur les ressources [!DNL Experience Manager] ressources utilisées dans des sites web tiers, incluez le code de suivi de page dans le code du site web. Utilisez l’utilitaire de suivi de page dans [!DNL Experience Manager] Ressources pour générer le code de suivi de page. Pour plus d’informations sur la manière d’inclure votre code de suivi de page sur des pages web tierces, reportez-vous à la section [Utilisation du dispositif de suivi de page et du code intégré sur les pages web](touch-ui-using-page-tracker.md).

1. Dans AEM, cliquez sur le bouton **[!UICONTROL Outils > Ressources]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Sur la page **[!UICONTROL Navigation]**, cliquez sur la carte **[!UICONTROL Dispositif de suivi de la page de statistiques]**.
1. Cliquez sur l’icône **[!UICONTROL Télécharger]** pour télécharger le code de suivi de page.
