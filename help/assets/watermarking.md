---
title: Mettre vos images en filigrane
description: Utilisez la fonction de filigrane pour ajouter un filigrane numérique à vos images PNG ET JPEG.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 04de28347ddf0082d2e224aa3853297cad3aacd8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 41%

---


# Mise en filigrane de vos ressources {#watermarking}

Adobe Experience Manager (AEM) Assets (Actifs) permet d’ajouter un filigrane numérique aux images, ce qui permet aux utilisateurs de vérifier l’authenticité et la propriété des fichiers sous copyright. AEM Assets prend en charge le texte à utiliser comme un filigrane sur les fichiers PNG et JPEG.

Pour pouvoir appliquer un filigrane aux ressources, ajoutez l&#39;étape [!UICONTROL Filigrane] dans le flux de travaux [!UICONTROL DAM Update Asset].

1. Appuyez sur le logo de l&#39;AEM et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]**.
1. Sur la page Modèles de workflows, sélectionnez le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**, puis cliquez sur **[!UICONTROL Modifier]**.

1. Dans le panneau latéral, faites glisser l’étape **[!UICONTROL Ajouter le filigrane]** et ajoutez-la au workflow [!UICONTROL DAM Update Asset].

   ![Faire glisser l’étape Ajouter un filigrane dans le processus Ressources de mise à jour de gestion des actifs numériques](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Placez l’étape [!UICONTROL Ajouter le filigrane] n’importe où avant l’étape [!UICONTROL Traiter la miniature].

1. Ouvrez l’étape **[!UICONTROL Ajouter un filigrane]** pour afficher ses propriétés.
1. Sous l’onglet **[!UICONTROL Arguments]**, spécifiez des valeurs valides dans les différents champs, notamment le texte, le type de police, la taille, la couleur, l’emplacement, l’orientation, etc. Pour confirmer les modifications, appuyez/cliquez sur l’icône Terminé.

   ![Indiquer les arguments dans l’étape Ajouter un filigrane dans Assets](assets/arguments_add_watermark_aem_assets.png)

1. Enregistrez le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]** avec l’étape Filigrane.
1. Dans l’interface utilisateur AEM, téléchargez un exemple de fichier. Le filigrane s’affiche avec la taille de police, la couleur, etc., à la position que vous avez configurée dans les étapes ci-dessus.

Pour mettre en filigrane des documents PDF par programmation ou avec des informations dynamiques, pensez à utiliser l’offre [AEM Document Services](/help/forms/using/overview-aem-document-services.md).
