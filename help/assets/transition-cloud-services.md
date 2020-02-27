---
title: Application de services cloud de traduction à des dossiers
description: Application de services cloud de traduction à des dossiers
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Application de services cloud de traduction à des dossiers {#applying-translation-cloud-services-to-folders}

Adobe Experience Manager (AEM) vous offre des services de traduction basés sur le cloud du fournisseur de traduction de votre choix afin de vous assurer que vos ressources sont traduites en fonction de vos besoins.

Vous pouvez appliquer le service cloud de traduction directement à votre dossier de ressources afin qu’elles puissent être utilisées au cours des processus de traduction.

## Application des services de traduction {#applying-the-translation-services}

L’application de services cloud directement à votre dossier de ressources élimine le besoin de configurer des services de traduction lorsque vous créez ou mettez à jour les processus de traduction.

1. Depuis l’interface utilisateur Ressources, sélectionnez le dossier auquel vous souhaitez appliquer des services de traduction.
1. Dans la barre d’outils, cliquez/appuyez sur l’icône **[!UICONTROL Propriétés]** pour afficher la page **[!UICONTROL Propriétés du dossier]**.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Accédez à l’onglet **[!UICONTROL Cloud Services]**.
1. Dans la liste Configurations du service Cloud, sélectionnez un fournisseur de traduction. Par exemple, si vous souhaitez utiliser les services de traduction de Microsoft, choisissez **[!UICONTROL Traducteur Microsoft]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Sélectionnez le connecteur pour le fournisseur de traduction.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. Depuis la barre d’outils, cliquez ou appuyez sur **[!UICONTROL Enregistrer]**, puis sur **[!UICONTROL OK]** pour fermer la boîte de dialogue. Le service de traduction est appliqué au dossier.

## Application du connecteur de traduction personnalisé  {#applying-custom-translation-connector}

Si vous souhaitez appliquer un connecteur personnalisé aux services de traduction que vous souhaitez utiliser dans les processus de traduction. Pour appliquer un connecteur personnalisé, installez d’abord le connecteur à partir de Package Manager. Configurez ensuite le connecteur à partir de la console Cloud Services. Une fois que vous avez configuré le connecteur, il est disponible dans la liste des connecteurs de l’onglet Cloud Services décrite dans [Application des services de traduction](transition-cloud-services.md#applying-the-translation-services). Après avoir appliqué le connecteur personnalisé et exécuté les processus de traduction, la mosaïque **[!UICONTROL Résumé de traduction]** du projet de traduction affiche les détails du connecteur sous les en-têtes **[!UICONTROL Fournisseur]** et **[!UICONTROL Méthode]**.

1. Installez le connecteur depuis le gestionnaire de modules.
1. Cliquez/appuyez sur le logo AEM et accédez à **[!UICONTROL Outils > Déploiement > Services cloud]**.
1. Localisez le connecteur que vous avez installé sous **[!UICONTROL Services tiers]** dans la page **[!UICONTROL Cloud Services]**.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Cliquez ou appuyez sur le lien **[!UICONTROL Configurer maintenant]** pour ouvrir la boîte de dialogue **[!UICONTROL Créer une configuration]**.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Indiquez un titre et un nom pour le connecteur, puis cliquez/appuyez sur **[!UICONTROL Créer]**. Le connecteur personnalisé est disponible dans la liste des connecteurs de l’onglet **[!UICONTROL Cloud Services]** décrite à l’étape 5 de [l’application des services de traduction](#applying-the-translation-services).
1. Exécutez tout processus de traduction décrit dans [Création de projets](translation-projects.md) de traduction après avoir appliqué le connecteur personnalisé. Vérifiez les détails du connecteur dans la mosaïque **[!UICONTROL Résumé de traduction]** du projet de traduction dans la console **[!UICONTROL Projets]**.

   ![chlimage_1-220](assets/chlimage_1-220.png)
