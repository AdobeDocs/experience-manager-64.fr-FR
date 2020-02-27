---
title: Visionneuses de médias mixtes
seo-title: Visionneuses de médias mixtes
description: Découvrez comment travailler avec des visionneuses de supports variés dans Dynamic Media.
seo-description: Découvrez comment travailler avec des visionneuses de supports variés dans Dynamic Media.
uuid: e37fa648-74e2-42e3-8611-8509c92ec00d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 599c316e-b6a7-4a28-bc4b-75d48409bde0
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Visionneuses de médias mixtes {#mixed-media-sets}

Une visionneuse de supports variés permet d’offrir un mélange d’images, de visionneuses d’images, de visionneuses à 360° et de vidéos dans une même présentation.

Les visionneuses de médias mixtes sont désignées par une bannière comportant le mot **[!UICONTROL Visionneuse de médias mixtes]**. En outre, si la visionneuse de médias mixtes est publiée, la date de publication, indiquée par l’icône représentant la **[!UICONTROL Terre]** figure sur la bannière avec la date de dernière modification, indiquée par l’icône en forme de **[!UICONTROL crayon]**.

![chlimage_1-348](assets/chlimage_1-348.png)

>[!NOTE]
>
>Pour plus d’informations sur l’interface utilisateur des ressources, voir [Gestion des ressources avec l’interface utilisateur tactile](managing-assets-touch-ui.md).

## Démarrage rapide : Visionneuses de supports variés {#quick-start-mixed-media-sets}

Pour démarrer rapidement, procédez comme suit :

1. [Chargez vos ressources](#uploading-assets).

   Commencez par télécharger les images et les vidéos pour vos visionneuses de médias mixtes. Le cas échéant, créez vos [visionneuses d’images](image-sets.md) et [visionneuses à 360°](spin-sets.md). Comme les utilisateurs peuvent zoomer sur les images dans la visionneuse de médias mixtes, tenez compte du zoom lorsque vous sélectionnez des images. Assurez-vous que les images font au moins 2000 pixels dans leur dimension la plus grande.

1. [Créez une visionneuse de supports variés.](#creating-mixed-media-sets)

   Pour créer une visionneuse de supports variés, dans la page **[!UICONTROL Ressources]** , appuyez sur **[!UICONTROL Créer > Visionneuse]** de supports variés, puis nommez la visionneuse. Sélectionnez les fichiers, puis choisissez l’ordre d’affichage des images.

   Voir [Utilisation de sélecteurs](working-with-selectors.md).

1. Set up [Mixed Media Viewer presets](managing-viewer-presets.md), as needed.

   Les administrateurs peuvent créer ou modifier des paramètres prédéfinis de visionneuse de supports variés. Pour afficher votre média mixte avec un paramètre prédéfini de visionneuse, sélectionnez le jeu de médias mixtes, puis, dans le menu déroulant du rail gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   See **[!UICONTROL Tools > Assets > Viewer Presets]** to create or edit viewer presets.

   See [Adding and editing viewer presets.](managing-viewer-presets.md)

1. [Prévisualisez une visionneuse de supports variés.](#previewing-mixed-media-sets)

   Sélectionnez la visionneuse de supports variés pour pouvoir la prévisualiser. Cliquez sur les icônes des miniatures afin d’examiner votre visionneuse de supports variés dans la visionneuse sélectionnée. You can choose different Viewers from the **[!UICONTROL Viewers]** menu, available from the left rail drop-down menu.

1. [Publiez une visionneuse de supports variés.](#publishing-mixed-media-sets)

   La publication d’une visionneuse de supports variés active la chaîne URL et d’incorporation. In addition, you must [publish the viewer preset](managing-viewer-presets.md#publishing-viewer-presets).

1. [Liez des URL à l’application Web](linking-urls-to-yourwebapplication.md) ou [incorporez la vidéo ou la visionneuse d’images](embed-code.md).

   AEM Assets crée des appels URL pour les visionneuses de supports variés et les active une fois que vous avez publié les visionneuses. Vous pouvez copier ces URL lorsque vous prévisualisez les ressources. Vous pouvez également les incorporer à votre site Web.

   Select the Mixed Media Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   Voir [Liaison d’une visionneuse de médias mixtes à une page web](linking-urls-to-yourwebapplication.md) et [Intégration de la vidéo ou de la visionneuse d’images](embed-code.md).

Le cas échéant, vous pouvez modifier une [visionneuse de supports variés](#editing-mixed-media-sets). In addition, you can view and modify [Mixed Media Set properties](managing-assets-touch-ui.md#editing-properties).

>[!NOTE]
>
>If you have issues creating sets, see [Troubleshooting Dynamic Media - Scene7 mode](troubleshoot-dms7.md).

## Télécharger des ressources {#uploading-assets}

Commencez par télécharger les images et les vidéos pour vos visionneuses de médias mixtes. Comme les utilisateurs peuvent zoomer sur les images dans la visionneuse de supports variés, assurez-vous que vous tenez compte du zoom lorsque vous sélectionnez des images. Assurez-vous que les images font au moins 2000 pixels dans leur dimension la plus grande.

Si vous souhaitez ajouter des visionneuses à 360° ou des visionneuses d’images à la visionneuse de supports variés, créez-les aussi.

## Création d’une visionneuse de supports variés {#creating-mixed-media-sets}

Vous pouvez ajouter des images, des visionneuses d’images, des visionneuses à 360° et des vidéos à votre visionneuse de supports variés. Assurez-vous que les fichiers, visionneuses d’images et visionneuses à 360° sont prêts pour la publication avant de les ajouter à la visionneuse de supports variés.

Lorsque vous ajoutez des ressources à votre visionneuse, elles sont automatiquement ajoutées dans l’ordre alphanumérique. Vous pouvez réorganiser ou trier manuellement les ressources après les avoir ajoutées.

**Pour créer une visionneuse** de supports variés :

1. Dans Ressources, accédez à l’emplacement où vous souhaitez créer une visionneuse de médias mixtes, puis cliquez sur **Créer** et sélectionnez **[!UICONTROL Visionneuse de médias mixtes]**. Vous pouvez également créer la visionneuse à partir d’un dossier contenant vos fichiers.

   ![chlimage_1-349](assets/chlimage_1-349.png)

1. In the **[!UICONTROL Mixed Media Set Editor]** page, in **[!UICONTROL Title]**, enter a name for the Mixed Media Set. Le nom apparaît dans la bannière située sur la visionneuse de médias mixtes. Facultativement, saisissez une description.

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Lors de la création de la visionneuse de supports mixtes, vous pouvez modifier la miniature de la visionneuse de supports mixtes ou autoriser AEM à sélectionner automatiquement la miniature en fonction des ressources de la visionneuse de supports mixtes. To select a thumbnail, click **[!UICONTROL Change thumbnail]** and select any image (you can navigate to other folders to find images as well). If you have selected a thumbnail and then decide that you want AEM to generate one from the mixed media set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. Tap the **[!UICONTROL Asset Selector]** to select assets that you want to include in your Mixed Media Set. Select them and tap **[!UICONTROL Select]**.

   With the **[!UICONTROL Asset Selector]**, you can search for assets by typing in a keyword and tapping **[!UICONTROL Return]**. Vous pouvez également appliquer des filtres pour affiner vos résultats de recherche. Vous pouvez filtrer par chemin, collection, type de fichier et balise. Sélectionnez le filtre, puis appuyez sur l’icône **[!UICONTROL Filtre]** dans la barre d’outils. Change the view by selecting the View icon and selecting **[!UICONTROL List]**, **[!UICONTROL Column]**, or **[!UICONTROL Card]** view.

   Voir [Utilisation de sélecteurs](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. Réorganisez les ressources en les faisant glisser vers le haut ou le bas de la liste (sélectionnez l’icône de réorganisation), le cas échéant.

   ![chlimage_1-352](assets/chlimage_1-352.png)

   If you want to add thumbnails, click the **[!UICONTROL +]** icon next to the image and navigate to the thumbnail you want. Lorsque vous avez terminé, appuyez sur **[!UICONTROL Enregistrer]** pour sélectionner toutes les images miniatures.

   >[!NOTE]
   >
   >If you want to add assets, tap **[!UICONTROL Add Asset]**.

1. To delete an asset, select the corresponding check box and tap **[!UICONTROL Delete Asset]**.
1. To apply a preset, tap **[!UICONTROL Preset]** in the upper right corner and select a preset to apply to the assets.
1. Cliquez sur **[!UICONTROL Enregistrer]**. La visionneuse de médias mixtes nouvellement créée apparaît dans le dossier dans lequel vous l’avez créée.

## Modification d’une visionneuse de médias mixtes {#editing-mixed-media-sets}

Vous pouvez effectuer diverses tâches de modification sur les ressources dans les visionneuses de supports variés, directement dans l’interface utilisateur, [comme vous le feriez dans AEM Assets](managing-assets-touch-ui.md). Vous pouvez également effectuer les actions suivantes dans les visionneuses de supports variés :

* Ajouter des ressources à la visionneuse de supports variés.
* Réorganiser des ressources de la visionneuse de supports variés.
* Supprimer des ressources de la visionneuse de supports variés.
* Appliquer des paramètres prédéfinis de visionneuse.
* Modifier la vignette par défaut.

**Pour modifier des visionneuses** de supports variés :

1. Effectuez l’une des opérations suivantes :

   * Pointez sur une ressource de visionneuse de supports variés, puis appuyez sur **[!UICONTROL Modifier]** (icône crayon).
   * Pointez sur une ressource de visionneuse de supports variés, appuyez sur **[!UICONTROL Sélectionner]** (icône de coche), puis sur **[!UICONTROL Modifier]** dans la barre d’outils.
   * Appuyez sur une ressource de visionneuse de supports variés, puis sur **[!UICONTROL Modifier]** (icône crayon) dans la barre d’outils.

1. Dans l’éditeur de visionneuse de supports variés, effectuez l’une des actions suivantes :

   * Pour réorganiser les éléments : dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]** (icône image), puis faites glisser une ressource vers un nouvel emplacement.
   * Pour ajouter des ressources : dans la barre d’outils, appuyez sur **[!UICONTROL Ajouter une ressource]**. Accédez aux ressources. Pour chaque élément à ajouter, pointez sur l’image de la ressource (et non sur son nom), puis appuyez sur l’icône de coche. Dans le coin supérieur droit, appuyez sur **[!UICONTROL Sélectionner]**.
   * Pour supprimer une ressource : dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]**(icône image), puis sélectionnez la ressource. Dans la barre d’outils, appuyez sur **[!UICONTROL Supprimer la ressource]**.
   * Pour trier des ressources selon leur nom par ordre croissant ou décroissant, dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]** (icône image). À droite de l’en-tête **[!UICONTROL Ressources]**, appuyez sur les icônes lambda vers le haut ou vers le bas.
   >[!NOTE]
   >
   >* To delete an entire Mixed Media Set, from any viewing mode (such as **[!UICONTROL Card]** view or **[!UICONTROL Column]** view) navigate to the Mixed Media Set. Passez la souris sur la ressource et appuyez sur l’icône en forme de coche pour la sélectionner. Press **[!UICONTROL Backspace]** on the keyboard, or tap **[!UICONTROL More]** (three dots) on the toolbar, then tap **[!UICONTROL Delete]**.
   >* You can edit the assets in a Mixed Media Set by navigating to the set, tapping **[!UICONTROL Set Members]** in the left rail, and then tapping the **[!UICONTROL Pencil]** icon on an individual asset to open the editing window.


1. Tap **[!UICONTROL Save** when you are done editing.

   >[!NOTE]
   >
   >* Pour modifier les ressources dans une visionneuse de supports variés - Accédez à la visionneuse de supports variés. Tap (do not select) the set to open it in the AEM **[!UICONTROL Set Preview]** page. In the left rail, tap the down caret to open the drop-down list, then tap **[!UICONTROL Set Members]**. In the **[!UICONTROL Set Members]** page, hover on an asset, then tap **[!UICONTROL Edit]** (pencil icon) to open the editing page.
   >* To delete an entire Mixed Media Set - From any viewing mode (such as **[!UICONTROL Card]** view or **[!UICONTROL Column]** view), navigate to the Mixed Media Set. Placez le pointeur de souris sur la visionneuse, puis appuyez sur **[!UICONTROL Sélectionner]** (icône de coche). Appuyez sur la touche **[!UICONTROL Retour arrière]** de votre clavier ou sur **[!UICONTROL Plus]** (trois points de suspension), puis appuyez sur **[!UICONTROL Supprimer]**.


## Aperçu d’une visionneuse de supports variés {#previewing-mixed-media-sets}

Pour obtenir des informations sur l’aperçu d’une visionneuse de supports variés, voir [Aperçu des ressources](previewing-assets.md).

## Publication d’une visionneuse de supports variés {#publishing-mixed-media-sets}

Pour obtenir des informations sur la publication d’une visionneuse de supports variés, voir [Publication de ressources](publishing-dynamicmedia-assets.md).

>[!NOTE]
>
>Si la visionneuse de supports variés ne se retrouve pas entièrement dans le service de distribution lors de sa première publication, vous devrez peut-être publier la visionneuse de supports mixtes une deuxième fois.

