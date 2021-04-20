---
title: Ajout d’un filigrane à vos ressources numériques
description: Découvrez comment utiliser la fonctionnalité d’application d’un filigrane pour ajouter un filigrane numérique aux ressources.
contentOwner: AG
feature: Asset Management
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 36%

---


# Mettre vos ressources numériques en filigrane {#watermarking}

[!DNL Adobe Experience Manager Assets] vous permet d’ajouter un filigrane numérique aux fichiers afin d’aider les utilisateurs à vérifier l’authenticité et la propriété des fichiers sur les droits d’auteur. [!DNL Experience Manager Assets] prend en charge le texte à utiliser comme un filigrane sur les fichiers PNG et JPEG.

Adobe Experience Manager (AEM) Assets (Actifs) permet d’ajouter un filigrane numérique aux images, ce qui permet aux utilisateurs de vérifier l’authenticité et la propriété des fichiers sous copyright. AEM Assets prend en charge le texte à utiliser comme un filigrane sur les fichiers PNG et JPEG.

Pour pouvoir appliquer un filigrane aux ressources, ajoutez l’étape de filigrane dans le flux de travaux [!UICONTROL DAM Update Asset].

1. Accédez à l&#39;interface utilisateur [!DNL Experience Manager] et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]**.
1. Sur la page Modèles de workflows, sélectionnez le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**, puis cliquez sur **[!UICONTROL Modifier]**.

1. Dans le panneau latéral, faites glisser l’étape **[!UICONTROL Ajouter le filigrane]** et ajoutez-la au workflow [!UICONTROL DAM Update Asset].

   ![Faites glisser l’étape d’ajout de filigrane dans le processus de mise à jour de la gestion des actifs numériques.](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Placez l’étape [!UICONTROL Ajouter le filigrane] n’importe où avant l’étape [!UICONTROL Traiter la miniature].

1. Ouvrez l’étape **[!UICONTROL Ajouter un filigrane]** pour afficher ses propriétés.
1. Sous l’onglet **[!UICONTROL Arguments]**, spécifiez des valeurs valides dans les différents champs, notamment le texte, le type de police, la taille, la couleur, l’emplacement, l’orientation, etc. Pour confirmer les modifications, cliquez sur **[!UICONTROL Terminé]**.

   ![Indiquer les arguments dans l’étape Ajouter un filigrane dans Assets](assets/arguments_add_watermark_aem_assets.png)

1. Enregistrez le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]** avec l’étape Filigrane.
1. Dans l’interface utilisateur AEM, téléchargez un exemple de fichier. Le filigrane s’affiche avec la taille de police, la couleur, etc., à la position que vous avez configurée dans les étapes ci-dessus.

Pour mettre en filigrane des documents PDF par programmation ou avec des informations dynamiques, pensez à utiliser l’offre [AEM Document Services](/help/forms/using/overview-aem-document-services.md).

## Conseils et restrictions {#tips-limitations}

* Seuls les filigranes basés sur du texte sont pris en charge. Les images ne sont pas utilisées comme filigranes, même si vous pouvez télécharger des images lors de la création du processus [!UICONTROL Ajouter le filigrane].
* Seuls les fichiers PNG et JPEG sont pris en charge pour être mis en filigrane. Les autres formats de fichier ne sont pas filigrane.
