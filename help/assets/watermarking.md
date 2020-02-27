---
title: Mettre vos images en filigrane
description: Utilisez la fonction de filigrane pour ajouter un filigrane numérique à vos images PNG ET JPEG.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e

---


# Mettre vos ressources en filigrane {#watermarking}

Les ressources d’Adobe Experience Manager (AEM) vous permettent d’ajouter un filigrane numérique aux images afin d’aider les utilisateurs à vérifier l’authenticité et la propriété des ressources par copyright. AEM Assets prend en charge le texte à utiliser comme un filigrane sur les fichiers PNG et JPEG.

To be able to apply watermark on assets, add the [!UICONTROL Watermark] step in the [!UICONTROL DAM Update Asset] workflow.

1. Tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. From the Workflow Models page, select the **[!UICONTROL DAM Update Asset]** workflow and click **[!UICONTROL Edit]**.

1. From the side panel, drag the **[!UICONTROL Add Watermark]** step and add it to the [!UICONTROL DAM Update Asset] workflow.

   ![Faire glisser l’étape Ajouter un filigrane dans le processus Ressources de mise à jour de gestion des actifs numériques](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Place the [!UICONTROL Add Watermark] step anywhere before the [!UICONTROL Process Thumbnail] step.

1. Ouvrez l’étape **[!UICONTROL Ajouter un filigrane]** pour afficher ses propriétés.
1. Sous l’onglet **[!UICONTROL Arguments]**, spécifiez des valeurs valides dans les différents champs, notamment le texte, le type de police, la taille, la couleur, l’emplacement, l’orientation, etc. Pour confirmer les modifications, appuyez/cliquez sur l’icône Terminé.

   ![Indiquer les arguments dans l’étape Ajouter un filigrane dans Assets](assets/arguments_add_watermark_aem_assets.png)

1. Enregistrez le processus **[!UICONTROL Ressources de mise à jour de DAM]** avec l’étape Filigrane.
1. Dans l’interface utilisateur d’AEM, téléchargez un exemple de fichier. Le filigrane s’affiche avec la taille de police, la couleur, etc., à la position que vous avez configurée dans les étapes ci-dessus.
