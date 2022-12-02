---
title: Ajout d’un filigrane à vos ressources numériques
description: Découvrez comment utiliser la fonctionnalité d’application d’un filigrane pour ajouter un filigrane numérique aux ressources.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 77%

---

# Ajoutez un filigrane à vos ressources numériques. {#watermarking}

[!DNL Adobe Experience Manager Assets] vous permet d’ajouter un filigrane numérique aux ressources pour vérifier l’authenticité et la propriété des droits d’auteur de ces ressources. [!DNL Experience Manager Assets] prend en charge le texte à utiliser comme filigrane dans les fichiers PNG et JPEG.

Adobe Experience Manager Assets vous permet d’ajouter un filigrane numérique aux images pour aider les utilisateurs à vérifier l’authenticité et la propriété des droits d’auteur des ressources. [!DNL Experience Manager] Assets prend en charge le texte à utiliser comme un filigrane sur les fichiers PNG et JPEG.

Pour appliquer le filigrane sur les ressources, ajoutez l’étape d’ajout d’un filigrane dans le workflow [!UICONTROL Ressource de mise à jour de gestion des ressources numériques].

1. Accédez à l’interface utilisateur d’[!DNL Experience Manager], puis accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]**.
1. Sur la page Modèles de workflows, sélectionnez le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**, puis cliquez sur **[!UICONTROL Modifier]**.

1. Dans le panneau latéral, faites glisser le **[!UICONTROL Ajouter un filigrane]** et l’ajouter à l’étape [!UICONTROL Ressources de mise à jour de gestion des actifs numériques] workflow.

   ![Faites glisser l’étape Ajouter un filigrane dans le workflow Ressources de mise à jour de gestion des actifs numériques](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Placez l’étape [!UICONTROL Ajouter un filigrane] n’importe où avant l’étape [!UICONTROL Traitement de la miniature].

1. Ouvrez l’étape **[!UICONTROL Ajouter un filigrane]** pour afficher ses propriétés.
1. Sous l’onglet **[!UICONTROL Arguments]**, spécifiez des valeurs valides dans les différents champs, notamment le texte, le type de police, la taille, la couleur, l’emplacement, l’orientation, etc. Pour confirmer les modifications, cliquez sur **[!UICONTROL Terminé]**.

   ![Indiquer les arguments dans l’étape Ajouter un filigrane dans Assets](assets/arguments_add_watermark_aem_assets.png)

1. Enregistrez le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]** avec l’étape Filigrane.
1. Dans l’interface utilisateur d’[!DNL Experience Manager], téléchargez un exemple de ressource. Le filigrane apparaît avec la taille de police, la couleur, etc., à l’emplacement configuré aux étapes ci-dessus.

Pour ajouter un filigrane à des documents PDF par programmation ou avec des informations dynamiques, pensez à utiliser les outils d’[[!DNL Experience Manager]  Document Services](/help/forms/using/overview-aem-document-services.md).

## Conseils et restrictions {#tips-limitations}

* Seuls les filigranes basés sur du texte sont pris en charge. Des images ne peuvent pas être utilisées comme des filigranes, même si vous pouvez charger des images lors de la création du [!UICONTROL Processus d’ajout d’un filigrane].
* Seuls les fichiers PNG et JPEG sont pris en charge pour recevoir un filigrane. Les autres formats de ressource n’accepteront pas l’ajout d’un filigrane.
