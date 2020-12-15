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
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 77%

---


# Visionneuses de médias mixtes {#mixed-media-sets}

Une visionneuse de médias mixtes permet d’offrir un mélange d’images, de visionneuses d’images, de visionneuses à 360° et de vidéos dans une même présentation.

Les visionneuses de médias mixtes sont désignées par une bannière contenant les mots **[!UICONTROL Visionneuse de médias mixtes]**. En outre, si la visionneuse de médias mixtes est publiée, la date de publication, indiquée par l’icône représentant la **[!UICONTROL Terre]**, figure sur la bannière avec la date de dernière modification, indiquée par l’icône représentant un **[!UICONTROL crayon]**.

![chlimage_1-348](assets/chlimage_1-348.png)

>[!NOTE]
>
>Pour plus d’informations sur l’interface utilisateur d’Assets, voir [Gestion des ressources avec l’interface utilisateur tactile](managing-assets-touch-ui.md).

## Démarrage rapide : Visionneuses de médias mixtes {#quick-start-mixed-media-sets}

Pour démarrer rapidement, procédez comme suit :

1. [Chargez vos ressources](#uploading-assets).

   Commencez par charger les images et les vidéos pour les visionneuses de médias mixtes. Le cas échéant, créez les [Visionneuses d’images](image-sets.md) et [Visionneuse à 360°](spin-sets.md). Comme les utilisateurs peuvent zoomer sur les images dans la visionneuse de médias mixtes, tenez compte du zoom lorsque vous sélectionnez des images. Assurez-vous que les images font au moins 2 000 pixels dans leur dimension la plus grande.

1. [Créez une visionneuse de médias mixtes.](#creating-mixed-media-sets)

   Pour créer une visionneuse de supports variés, sur la page **[!UICONTROL Ressources]**, appuyez sur **[!UICONTROL Créer > Visionneuse de supports variés]**, puis nommez la visionneuse. Sélectionnez les fichiers, puis choisissez l’ordre dans lequel les images s’affichent.

   Voir [Utilisation de sélecteurs](working-with-selectors.md).

1. Configurez des [paramètres prédéfinis de visionneuse de médias mixtes](managing-viewer-presets.md), suivant les besoins.

   Les administrateurs peuvent créer ou modifier les paramètres prédéfinis de visionneuse de médias mixtes. Pour afficher votre visionneuse de médias mixtes avec un paramètre prédéfini, sélectionnez la visionneuse puis, dans le menu contextuel du rail gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   Accédez à **[!UICONTROL Outils > Ressources > Paramètres visionneuse]** pour créer ou modifier les paramètres prédéfinis de la visionneuse.

   Voir [Ajout et modification de paramètres prédéfinis de la visionneuse](managing-viewer-presets.md).

1. [Prévisualisez une visionneuse de médias mixtes.](#previewing-mixed-media-sets)

   Sélectionnez la visionneuse de médias mixtes pour pouvoir la prévisualiser. Cliquez sur les icônes des miniatures afin d’examiner votre visionneuse de médias mixtes dans la visionneuse sélectionnée. Vous pouvez choisir différentes visionneuses dans le menu **[!UICONTROL Visionneuses]** disponible dans le menu déroulant du rail gauche.

1. [Publiez une visionneuse de médias mixtes.](#publishing-mixed-media-sets)

   La publication d’une visionneuse de médias mixtes active la chaîne URL et d’incorporation. Vous devez, en outre, [publier le paramètre prédéfini de la visionneuse](managing-viewer-presets.md#publishing-viewer-presets).

1. [Liez des URL à l’application web](linking-urls-to-yourwebapplication.md) ou [incorporez la vidéo ou la visionneuse d’images](embed-code.md).

   AEM Assets crée des appels URL pour les visionneuses de médias mixtes et les active une fois que vous avez publié les visionneuses. Vous pouvez copier ces URL lorsque vous prévisualisez les ressources. Vous pouvez également les incorporer à votre site web.

   Sélectionnez la visionneuse de médias mixtes puis, dans le menu déroulant du rail gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   Voir [Liaison d’une visionneuse de médias mixtes à une page web](linking-urls-to-yourwebapplication.md) et [Incorporation de la vidéo ou de la visionneuse d’images](embed-code.md).

Le cas échéant, vous pouvez modifier une [visionneuse de médias mixtes](#editing-mixed-media-sets). Vous pouvez, en outre, afficher et modifier les [propriétés de la visionneuse de médias mixtes](managing-assets-touch-ui.md#editing-properties).

>[!NOTE]
>
>Si vous rencontrez des problèmes lors de la création de visionneuses, voir [Dépannage de Dynamic Media - Mode Scene7](troubleshoot-dms7.md).

## Télécharger des ressources {#uploading-assets}

Commencez par charger les images et les vidéos pour les visionneuses de médias mixtes. Comme les utilisateurs peuvent zoomer sur les images dans la visionneuse de médias mixtes, assurez-vous que vous tenez compte du zoom lorsque vous sélectionnez des images. Assurez-vous que les images font au moins 2 000 pixels dans leur dimension la plus grande.

Si vous souhaitez ajouter des visionneuses à 360° ou des visionneuses d’images à la visionneuse de médias mixtes, créez-les aussi.

## Création d’une visionneuse de médias mixtes   {#creating-mixed-media-sets}

Vous pouvez ajouter des images, des visionneuses d’images, des visionneuses à 360° et des vidéos à votre visionneuse de médias mixtes. Assurez-vous que les fichiers, visionneuses d’images et visionneuses à 360° sont prêts pour la publication avant de les ajouter à la visionneuse de médias mixtes.

Lorsque vous ajoutez des ressources à votre visionneuse, elles sont automatiquement ajoutées dans l’ordre alphanumérique. Vous pouvez réorganiser ou trier manuellement les ressources après les avoir ajoutées.

**Création d’une visionneuse de médias mixtes**:

1. Dans Assets, accédez à l’emplacement où vous souhaitez créer une visionneuse de médias mixtes, cliquez sur **Créer**, puis sélectionnez **[!UICONTROL Visionneuse de médias mixtes]**. Vous pouvez également la créer depuis un dossier qui contient les ressources.

   ![chlimage_1-349](assets/chlimage_1-349.png)

1. Dans la page **[!UICONTROL Editeur de visionneuse de supports variés]**, dans **[!UICONTROL Titre]**, saisissez le nom de la visionneuse de supports variés. Le nom apparaît dans la bannière située sur la visionneuse de médias mixtes. Vous pouvez aussi saisir une description.

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Lors de la création de la visionneuse de médias mixtes, vous pouvez modifier la miniature de la visionneuse ou permettre à AEM de sélectionner la miniature automatiquement en fonction des ressources de la visionneuse de médias mixtes. Pour sélectionner une miniature, cliquez sur **[!UICONTROL Modifier la miniature]** et sélectionnez une image (vous pouvez également accéder à d’autres dossiers pour trouver des images). Si vous avez sélectionné une miniature, puis décidez que vous souhaitez qu’AEM en génère une depuis la visionneuse de médias mixtes, sélectionnez **[!UICONTROL Basculer vers les miniatures automatiques]**.

1. Appuyez sur le **[!UICONTROL Sélecteur de ressources]** pour sélectionner les fichiers à inclure dans votre visionneuse de supports variés. Sélectionnez-les et appuyez sur **[!UICONTROL Sélectionner]**.

   Avec le **[!UICONTROL sélecteur de ressources]**, vous pouvez rechercher des ressources en saisissant un mot-clé et en appuyant sur **[!UICONTROL Retour]**. Vous pouvez également appliquer des filtres pour affiner vos résultats de recherche. Vous pouvez filtrer par chemin, collection, type de fichier et balise. Sélectionnez le filtre, puis appuyez sur l’icône **[!UICONTROL Filtre]** dans la barre d’outils. Modifiez la vue en sélectionnant l’icône de Vue et en sélectionnant **[!UICONTROL Liste]**, **[!UICONTROL Colonne]** ou **[!UICONTROL vue Carte]**.

   Voir [Utilisation de sélecteurs](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. Réorganisez les ressources en les faisant glisser vers le haut ou le bas de la liste (sélectionnez l’icône de réorganisation), le cas échéant.

   ![chlimage_1-352](assets/chlimage_1-352.png)

   Si vous souhaitez ajouter des miniatures, cliquez sur l’icône **[!UICONTROL +]** en regard de l’image et accédez à la miniature de votre choix. Lorsque vous avez terminé de sélectionner toutes les images miniatures, appuyez sur **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >Si vous souhaitez ajouter des ressources, appuyez sur **[!UICONTROL Ajouter une ressource]**.

1. Pour supprimer une ressource, cochez la case correspondante, puis appuyez sur **[!UICONTROL Supprimer l’élément]**.
1. Pour appliquer un paramètre prédéfini aux ressources, appuyez sur **[!UICONTROL Paramètre prédéfini]** dans le coin supérieur droit, puis sélectionnez le paramètre prédéfini de votre choix.
1. Cliquez sur **[!UICONTROL Enregistrer]**. La visionneuse de médias mixtes nouvellement créée apparaît dans le dossier dans lequel vous l’avez créée.

## Modification d’une visionneuse de médias mixtes   {#editing-mixed-media-sets}

Vous pouvez effectuer diverses tâches de modification sur les ressources dans les visionneuses de médias mixtes, directement dans l’interface utilisateur, [comme vous le feriez dans AEM Assets](managing-assets-touch-ui.md). Vous pouvez également effectuer les actions suivantes dans les visionneuses de médias mixtes :

* Ajouter des ressources à la visionneuse de médias mixtes.
* Réorganiser des ressources de la visionneuse de médias mixtes.
* Supprimer des ressources de la visionneuse de médias mixtes.
* Appliquer des paramètres prédéfinis de visionneuse.
* Modifier la vignette par défaut.

**Pour modifier des visionneuses** de supports variés :

1. Effectuez l’une des opérations suivantes :

   * Pointez sur une ressource de visionneuse de médias mixtes, puis appuyez sur **[!UICONTROL Modifier]** (icône crayon).
   * Pointez sur une ressource de visionneuse de médias mixtes, appuyez sur **[!UICONTROL Sélectionner]** (icône de coche), puis sur **[!UICONTROL Modifier]** dans la barre d’outils.
   * Appuyez sur une ressource de visionneuse de médias mixtes, puis sur **[!UICONTROL Modifier]** (icône crayon) dans la barre d’outils.

1. Dans l’éditeur de visionneuse de médias mixtes, effectuez l’une des actions suivantes :

   * Pour réorganiser les éléments : dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]** (icône image), puis faites glisser une ressource vers un nouvel emplacement.
   * Pour ajouter des ressources : dans la barre d’outils, appuyez sur **[!UICONTROL Ajouter une ressource]**. Accédez aux ressources. Pour chaque élément à ajouter, pointez sur l’image de la ressource (et non sur son nom), puis appuyez sur l’icône de coche. Dans le coin supérieur droit, appuyez sur **[!UICONTROL Sélectionner]**.
   * Pour supprimer une ressource : dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]** (icône image), puis sélectionnez la ressource. Dans la barre d’outils, appuyez sur **[!UICONTROL Supprimer l’élément]**.
   * Pour trier des ressources selon leur nom par ordre croissant ou décroissant, dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]** (icône image). À droite de l’en-tête **[!UICONTROL Ressources]**, appuyez sur les icônes lambda vers le haut ou vers le bas.

   >[!NOTE]
   >
   >* Pour supprimer une visionneuse de supports variés complète, de n’importe quel mode d’affichage (par exemple, la vue **[!UICONTROL Carte]** ou la vue **[!UICONTROL Colonne]**), accédez à la visionneuse de supports variés. Placez le pointeur de la souris sur la ressource et appuyez sur l’icône de coche pour la sélectionner. Appuyez sur **[!UICONTROL Retour arrière]** sur le clavier ou sur **[!UICONTROL Plus]** (trois points) sur la barre d’outils, puis appuyez sur **[!UICONTROL Supprimer]**.
   >* Vous pouvez modifier les fichiers d’une visionneuse de supports variés en accédant à la visionneuse, en appuyant sur **[!UICONTROL Définir les membres]** dans le rail de gauche, puis en appuyant sur l’icône **[!UICONTROL Crayon]** d’une ressource individuelle pour ouvrir la fenêtre de modification.


1. Appuyez sur **[!UICONTROL Enregistrer]** lorsque vous avez terminé la modification.

   >[!NOTE]
   >
   >* Pour modifier les ressources dans une visionneuse de médias mixtes - Accédez à la visionneuse de médias mixtes. Appuyez sur (ne sélectionnez pas) le jeu pour l’ouvrir dans la page AEM **[!UICONTROL Définir la Prévisualisation]**. Dans le rail de gauche, appuyez sur le caret vers le bas pour ouvrir la liste déroulante, puis appuyez sur **[!UICONTROL Définir les membres]**. Dans la page **[!UICONTROL Définir des membres]**, passez la souris sur une ressource, puis appuyez sur **[!UICONTROL Modifier]** (icône représentant un crayon) pour ouvrir la page de modification.
   >* Pour supprimer une visionneuse de supports variés complète - De n’importe quel mode d’affichage (par exemple, la vue **[!UICONTROL Carte]** ou la vue **[!UICONTROL Colonne]**), accédez à la visionneuse de supports variés. Placez le pointeur de souris sur la visionneuse, puis appuyez sur **[!UICONTROL Sélectionner]** (icône de coche). Appuyez sur la touche **[!UICONTROL Retour arrière]** de votre clavier ou sur **[!UICONTROL Plus]** (trois points de suspension), puis appuyez sur **[!UICONTROL Supprimer]**.


## Aperçu d’une visionneuse de médias mixtes {#previewing-mixed-media-sets}

Pour obtenir des informations sur l’aperçu d’une visionneuse de médias mixtes, voir [Aperçu des ressources](previewing-assets.md).

## Publication d’une visionneuse de médias mixtes   {#publishing-mixed-media-sets}

Pour obtenir des informations sur la publication d’une visionneuse de médias mixtes, voir [Publication de ressources](publishing-dynamicmedia-assets.md).

>[!NOTE]
>
>Si la visionneuse de supports variés ne se retrouve pas entièrement dans le service de diffusion lors de sa première publication, vous devrez peut-être publier la visionneuse de supports variés une deuxième fois.

