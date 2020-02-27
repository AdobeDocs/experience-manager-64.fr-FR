---
title: Gestion des paramètres d’image prédéfinis de média dynamique
description: Comprendre les paramètres prédéfinis d’image Contenu multimédia dynamique et apprendre à créer, modifier et gérer des paramètres d’image prédéfinis
uuid: 087e6c32-82d5-4645-8dba-0a22c62f891f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e401816d-eba5-4833-a3bd-e2e45bc3b19e
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/image-presets
translation-type: tm+mt
source-git-commit: 5b54de6af2909746a8525704bc073eb8a92098d7

---


# Managing Dynamic Media image presets {#managing-image-presets}

Les paramètres d’image prédéfinis permettent à AEM Assets d’afficher des images selon des tailles et des formats différents, ou avec d’autres propriétés d’image générées dynamiquement. Chaque paramètre d’image prédéfini représente un ensemble prédéfini de commandes de dimensionnement et de mise en forme pour l’affichage des images. Lorsque vous créez un paramètre d’image prédéfini, vous choisissez une taille pour la diffusion de l’image. Vous pouvez également choisir des commandes de mise en forme pour optimiser l’aspect de l’image lors de la diffusion de l’image.

Les administrateurs peuvent créer des paramètres prédéfinis pour l’exportation de ressources. Les utilisateurs peuvent choisir un paramètre prédéfini au moment de l’exportation des images, qui reformate également les images selon les spécifications définies par l’administrateur.

Vous pouvez également créer des paramètres d’image prédéfinis réactifs. Si vous appliquez un paramètre prédéfini d’image réactive aux ressources, elles changent en fonction de l’appareil ou de la taille d’écran utilisée pour les afficher. Vous pouvez configurer des paramètres d’image prédéfinis de manière à utiliser CMJN dans l’espace colorimétrique, en plus de RVB ou Gris.

Cette section explique comment créer, modifier et gérer des paramètres d’image prédéfinis. Vous pouvez appliquer un paramètre d’image prédéfini à une image lorsque vous la prévisualisez. See [Applying Image Presets](image-presets.md).

>[!NOTE]
>
>L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis et utilise des informations à la dernière milliseconde de diffusion pour réduire davantage encore la taille du fichier d’image en fonction de la vitesse de connexion du réseau et du navigateur. Voir [Imagerie numérique](imaging-faq.md) pour plus d’informations.

## Understanding Dynamic Media image presets {#understanding-image-presets}

Tout comme une macro logicielle, un paramètre d’image prédéfini est un ensemble prédéfini de commandes de dimensionnement et de formatage enregistrées sous un nom. Pour comprendre le fonctionnement des paramètres d’image prédéfinis, supposons que votre site Web exige que chaque image du produit apparaisse dans différentes tailles, dans différents formats et taux de compression pour la diffusion sur ordinateur de bureau et sur mobile.

You could create two Image Presets: one with 500 x 500 pixels for desktop version and 150 x 150 pixels for the mobile version. You create two Image Presets, one called *Enlarge* to display images at 500x500 pixels and one called *Thumbnail* to display images at 150 x 150 pixels. To deliver images at the Enlarge and Thumbnail size, AEM looks up the definition of the Enlarge Image Preset and Thumbnail Image Preset. Ensuite, AEM génère de manière dynamique une image dont la taille et le format correspondent à chaque paramètre d’image prédéfini.

Les images de taille réduite, lorsqu’elles sont diffusées dynamiquement, peuvent perdre en netteté et en détail. C’est la raison pour laquelle chaque paramètre d’image prédéfini contient des commandes de formatage permettant d’optimiser l’image lorsqu’elle est diffusée avec une taille particulière. Ces commandes garantissent une image nette et claire au moment de la diffusion vers le site web ou l’application.

Les administrateurs peuvent créer des paramètres d’image prédéfinis. Vous pouvez créer un paramètre d’image prédéfini ou commencer par un paramètre d’image existant et l’enregistrer sous un nouveau nom.

## Managing Dynamic Media image presets {#managing-image-presets-1}

You manage your image presets in AEM by tapping the AEM logo to access the global navigation console and then tapping the Tools icon and navigating to **[!UICONTROL Assets > Image Presets]**.

![chlimage_1-494](assets/chlimage_1-494.png)

>[!NOTE]
>
>Tous les paramètres d’image prédéfinis que vous créez sont également disponibles en tant que rendus dynamiques lorsque vous prévisualisez ou livrez des ressources.
>
>Dans le *mode Scene7 de Dynamic Media*, vous *n’avez pas* besoin de publier les paramètres prédéfinis d’image car les paramètres d’image prédéfinis sont publiés automatiquement.
>
>Dans le *mode hybride de Dynamic Media*, vous devez publier manuellement les paramètres d’image prédéfinis.
>
>Voir [Publication de paramètres d’image prédéfinis.](#publishing-image-presets)

>[!NOTE]
>
>Le système affiche une grande variété de rendus lorsque vous sélectionnez **[!UICONTROL Rendus]** dans l’affichage des détails d’une ressource.**** Vous pouvez augmenter le nombre de paramètres d’image prédéfinis affichés. Voir [Augmentation du nombre de paramètres d’image prédéfinis affichés](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Formats de fichiers Adobe Illustrator (AI), PostScript (EPS) et PDF {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

Si vous avez l’intention de prendre en charge l’assimilation de fichiers AI, EPS et PDF de manière à pouvoir générer des rendus dynamiques de ces formats de fichiers, vous pouvez consulter les informations suivantes avant de créer des paramètres d’image prédéfinis.

Le format de fichier d’Adobe Illustrator est une variante du format PDF. Les principales différences, dans le cadre d’AEM Assets, sont les suivantes :

* Les documents Adobe Illustrator se composent d’une seule page avec plusieurs calques. Chaque calque est extrait sous la forme d’une sous-ressource PNG sous la ressource Illustrator principale.
* Les documents PDF se composent d’une ou de plusieurs pages. Chaque page est extraite sous la forme d’une sous-ressource PDF d’une seule page sous le document PDF multi-pages principal.

Les sous-ressources sont créées par le `Create Sub Asset process` composant dans le flux de travail global `DAM Update Asset` . Pour voir ce composant de processus dans le processus, appuyez sur **[!UICONTROL Outils > Processus > Modèles > Ressource de mise à jour de gestion des actifs numériques > Modifier]**.

Voir aussi [Affichage des pages d’un fichier multi-pages](/help/assets/managing-linked-subassets.md#view-pages-of-a-multi-page-file).

Vous pouvez afficher les sous-ressources ou les pages lorsque vous ouvrez la ressource, appuyez sur le menu Contenu et sélectionnez **[!UICONTROL Sous-ressources]** ou **[!UICONTROL Pages]**. Les sous-ressources sont de véritables ressources. That is, PDF pages are extracted by the `Create Sub Asset` workflow component. They are then stored as `page1.pdf`, `page2.pdf`, and so on below the main asset. Une fois qu’elles sont stockées, le processus **[!UICONTROL Ressource de mise à jour de gestion des actifs numériques]** les traite.

  Pour utiliser Dynamic Media afin de prévisualiser et de générer des rendus dynamiques pour des fichiers AI, EPS ou PDF, les étapes de traitement suivantes doivent être exécutées :

1. In the **[!UICONTROL DAM Update Asset]** workflow, the **[!UICONTROL Rasterize PDF/AI Image Preview Rendition]** process component rasterizes the first page of the original asset–using the configured resolution–into a `cqdam.preview.png` rendition.

1. Le rendu `cqdam.preview.png` est ensuite optimisé dans un fichier PTIFF par le composant de processus **[!UICONTROL Ressources d’image du processus de média dynamique]** à l’intérieur du processus.

>[!NOTE]
>
>In the **[!UICONTROL DAM Update Asset]** workflow, the **[!UICONTROL EPS thumbnails]** step generates thumbnails for EPS files.

### Propriétés des métadonnées de ressource PDF/AI/EPS {#pdf-ai-eps-asset-metadata-properties}

| **Propriété de métadonnées** | **Description** |
|---|---|
| dam:Physicallargthinches | Largeur du document en pouces. |
| dam:Physicalheightininches | Hauteur du document en pouces. |

Vous accédez aux options du composant de processus **[!UICONTROL Pixelliser le rendu d’aperçus d’image PDF/AI]** par l’intermédiaire du processus **[!UICONTROL Ressource de mise à jour de gestion des actifs numériques]**.

Tap on Adobe Experience Manager in the upper left, navigate to **[!UICONTROL Tools > Workflow > Models]**. On the **[!UICONTROL Workflow Models]** page, select **[!UICONTROL DAM Update Asset]**, then on the toolbar tap **[!UICONTROL Edit]**. On the **[!UICONTROL DAM Update Asset workflow]** page, double-tap the **[!UICONTROL Rasterize PDF/AI Image Preview Rendition]** process component to open its **[!UICONTROL Step Properties]** dialog box.

### Rasterize PDF/AI image preview rendition options {#rasterize-pdf-ai-image-preview-rendition-options}

![Arguments pour pixelliser le processus PDF ou AI](assets/rasterize_pdf_ai_image_preview.png)

**Arguments pour pixelliser le processus PDF ou AI**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Argument de processus</strong></td> 
   <td><strong>Paramètre par défaut</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>Types MIME</td> 
   <td><p>application/pdf</p> <p>application/postscript</p> <p>application/illustrator<br /> </p> </td> 
   <td>Liste des types MIME de documents considérés comme des documents PDF ou Illustrator.<br /> </td> 
  </tr> 
  <tr> 
   <td>Largeur max.</td> 
   <td>2048</td> 
   <td>Largeur maximale du rendu d’aperçu généré, en pixels.<br /> </td> 
  </tr> 
  <tr> 
   <td>Hauteur max.</td> 
   <td>2048</td> 
   <td>Hauteur maximale du rendu d’aperçu généré, en pixels.<br /> </td> 
  </tr> 
  <tr> 
   <td>Résolution</td> 
   <td>72</td> 
   <td>Résolution permettant de pixelliser la première page, en ppp (pixels par pouce).</td> 
  </tr> 
 </tbody> 
</table>

À l’aide des arguments de processus par défaut, la première page d’un document PDF/AI est pixellisée à 72 ppp et l’image de prévisualisation générée est dimensionnée à 2 048 x 2 048 pixels. Pour un déploiement standard, vous pouvez augmenter la résolution sur une valeur minimale de 150 ppp ou plus. Par exemple, un document de format Lettre US à 300 ppp doit avoir une largeur et une hauteur maximales de 2 550 x 3 300 pixels, respectivement.

******[!UICONTROL Largeur max. et Hauteur max. limitent la résolution à laquelle la pixellisation doit être effectuée.]** Par exemple, si les valeurs maximales restent inchangées, et que la résolution est définie sur 300 ppp, le document Lettre US est pixellisé à 186 ppp. En d’autres termes, la taille du document sera de 1 581 x 2 046 pixels.

Une valeur maximale est définie pour le composant de processus **[!UICONTROL Pixelliser le rendu d’aperçus d’image PDF/AI]**, afin de s’assurer qu’il ne crée pas d’images exagérément grandes en mémoire. Ces images volumineuses peuvent, en effet, dépasser la capacité de mémoire allouée à la machine virtuelle Java (JVM). Il faut veiller à fournir suffisamment de mémoire à la machine virtuelle Java pour gérer le nombre configuré de processus parallèles, de sorte que chacun d’eux soit en mesure de créer une image à la taille maximale configurée. 

### Format de fichier InDesign (INDD) {#indesign-indd-file-format}

Si vous avez l’intention de prendre en charge l’assimilation de fichiers INDD de manière à pouvoir générer le rendu dynamique de ce format de fichier, vous pouvez consulter les informations suivantes avant de créer des paramètres d’image prédéfinis.

Dans le cas des fichiers InDesign, les sous-ressources ne sont extraites que si Adobe InDesign Server est intégré à AEM. Les ressources référencées sont reliées en fonction de leurs métadonnées. InDesign Server n’est pas requis pour la liaison. Cependant, les ressources référencées doivent être présentes dans AEM avant que les fichiers InDesign soient traités, pour que les liens soient créés entre les fichiers InDesign et les ressources référencées.

Voir [Intégration d’AEM Assets à InDesign Server](indesign.md).

Le composant Extraction de médias du processus **[!UICONTROL Ressource de mise à jour de gestion des actifs numériques]****** exécute plusieurs scripts d’extension préconfigurés pour traiter des fichiers InDesign.

![Chemins Extend Script dans les arguments du processus Media Extraction](assets/media_extraction_arguments.png)

The **[!UICONTROL Extend Script]** paths in the arguments of **[!UICONTROL Media Extraction]** process component in the **[!UICONTROL DAM Update Asset]** workflow.

Les scripts suivants sont utilisés par l’intégration de Dynamic Media :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Etendre le nom du script</strong></td> 
   <td><strong>Default</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>ThumbnailExport.jsx</td> 
   <td>Oui</td> 
   <td>Génère un rendu <code>thumbnail.jpg</code> de 300 ppp optimisé et transformé en rendu PTIFF par composant <code>Dynamic Media Process Image Assets</code> de processus.<br /> </td> 
  </tr> 
  <tr> 
   <td>JPEGPagesExport.jsx</td> 
   <td>Oui</td> 
   <td>Génère un sous-fichier JPEG de 300 ppp pour chaque page. Une sous-ressource JPEG est une véritable ressource stockée sous la ressource InDesign. Il est également optimisé et transformé en PTIFF par le <code>DAM Update Asset</code> processus.<br /> </td> 
  </tr> 
  <tr> 
   <td>PDFPagesExport.jsx</td> 
   <td>Non</td> 
   <td>Génère un sous-fichier PDF pour chaque page. La sous-ressource PDF est traitée comme indiqué précédemment. Étant donné que le PDF ne contient qu’une seule page, aucune sous-ressource n’est générée.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Configuration de la taille de la miniature {#configuring-image-thumbnail-size}

Vous pouvez définir la taille des miniatures en configurant ces paramètres dans le processus **[!UICONTROL Ressource de mise à jour de gestion des actifs numériques]**. Le processus comprend deux étapes au cours desquelles vous pouvez configurer la taille de miniature des ressources d’images. Bien qu’un composant (**[!UICONTROL Ressources d’image du processus de média dynamique]**) soit utilisé pour les ressources d’images dynamiques et que l’autre (**[!UICONTROL Miniatures des processus]**) soit exécuté pour la génération des miniatures statiques ou lorsqu’aucun autre processus ne parvient à générer des miniatures, *tous deux* doivent posséder les mêmes paramètres.

Avec l’étape **[!UICONTROL Ressources d’image du processus Dynamic Media]**, les miniatures sont générées par le serveur d’images et cette configuration est indépendante de la configuration appliquée à l’étape des **[!UICONTROL miniatures de processus]**. La génération de miniatures à l’étape **[!UICONTROL Traiter les miniatures]** est la méthode la plus lente et la plus gourmande en mémoire pour créer des miniatures.

Le dimensionnement des miniatures est défini au format suivant : **width:height:center** (largeur:hauteur:centrer), par exemple *80:80:false*. La largeur et la hauteur déterminent la taille en pixels de la miniature. La valeur « centrer » est soit false soit true. Si elle est définie sur true, elle indique que la miniature a exactement la taille spécifiée dans la configuration. Si l’image redimensionnée est plus petite, elle est centrée dans la miniature.

>[!NOTE]
>
>* La taille des miniatures des fichiers EPS est configurée à l’étape des **[!UICONTROL miniatures EPS]**, dans l’onglet **[!UICONTROL Arguments]****[!UICONTROL sous Miniatures]**.
   >
   >
* La taille des miniatures des vidéos est configurée à l’étape des **[!UICONTROL miniatures FFmpeg]**, dans l’onglet **[!UICONTROL Processus]** sous **[!UICONTROL Arguments]**.
>



**Pour configurer la taille** des miniatures :

1. Tap **[!UICONTROL Tools > Workflow > Models > DAM Update Asset > Edit]**.
1. Tap the **[!UICONTROL Dynamic Media Process Image Assets]** step, then tap the **[!UICONTROL Thumbnails]** tab. Modifiez la taille de la vignette, le cas échéant, puis appuyez sur **[!UICONTROL OK]**.

   ![step_properties_thumbnailarguments](assets/step_properties_thumbnailarguments.png)

1. Appuyez sur l’étape **[!UICONTROL Traiter les miniatures]**, puis sur l’onglet **[!UICONTROL Miniatures]**. Change the thumbnail size, as needed, and tap **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Les valeurs de l’argument des miniatures de l’étape **[!UICONTROL Miniatures des processus]** doivent correspondre à l’argument des miniatures de l’étape **[!UICONTROL Ressources d’image du processus Dynamic Media]**.

1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications apportées au workflow.

### Increasing or decreasing the number of Dynamic Media image presets that display {#increasing-or-decreasing-the-number-of-image-presets-that-display}

Les paramètres d’image prédéfinis que vous créez sont disponibles sous la forme de rendus dynamiques lorsque vous prévisualisez des ressources. AEM affiche une grande variété de rendus dynamiques lors de l’affichage de ressources à partir de **[!UICONTROL Affichage des détails > Rendus]**. Vous pouvez augmenter ou diminuer la limite des rendus affichés.

**Pour augmenter ou diminuer le nombre de paramètres d’image prédéfinis de média dynamique affichés**:

1. Navigate to **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Accédez au noeud de liste des paramètres d’image prédéfinis à l’adresse `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![Augmentation_decreasethenumberofimagepresetsthatdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. In the **[!UICONTROL limit]** property, change the **[!UICONTROL value]**, which is set to 15 by default, to the desired number.
1. Accédez à la source de données des paramètres d’image prédéfinis à l’adresse `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. In the limit property, change the number to the desired number, for example `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Appuyez sur **[!UICONTROL Enregistrer tout]**.

### Creating Dynamic Media image presets {#creating-image-presets}

La création d’un paramètre d’image prédéfini Contenu multimédia dynamique vous permet d’appliquer ces paramètres à toute image lors de la prévisualisation ou de la publication.

>[!NOTE]
>
>Si vous utilisez Internet Explorer 9, la création d’un paramètre prédéfini n’apparaît pas dans la liste des paramètres prédéfinis immédiatement après l’enregistrement. Pour contourner ce problème, désactivez le cache pour IE9.

Si vous avez l’intention de prendre en charge l’assimilation de fichiers AI, PDF et EPS de manière à pouvoir générer un rendu dynamique de ces formats de fichiers, vous pouvez consulter les informations suivantes avant de créer des paramètres d’image prédéfinis.\
Voir [Formats de fichiers Adobe Illustrator (AI), PostScript (EPS) et PDF](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Si vous avez l’intention de prendre en charge l’assimilation de fichiers INDD de manière à pouvoir générer le rendu dynamique de ce format de fichier, vous pouvez consulter les informations suivantes avant de créer des paramètres d’image prédéfinis.   Voir [Format de fichier InDesign (INDD)](#indesign-indd-file-format).

>[!NOTE]
>
>Pour créer des paramètres d’image prédéfinis de média dynamique, vous devez disposer de droits d’administrateur en tant qu’administrateur AEM ou administrateur de la console d’administration.

**Pour créer un paramètre** d’image prédéfini de média dynamique :

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale.
1. Appuyez sur l’icône **[!UICONTROL Outils]** , puis accédez à **[!UICONTROL Ressources > Paramètres d’image prédéfinis]**.
1. Appuyez sur **[!UICONTROL Créer]**.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >Pour rendre ce paramètre d’image prédéfini réactif, effacez les valeurs des champs **[!UICONTROL largeur]** et **[!UICONTROL hauteur]** et laissez-les vides.

1. On the **[!UICONTROL Edit Image Preset]** page, enter values into the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs as appropriate, including a name. Les options sont décrites dans [Options d’image prédéfinies](#image-preset-options). Les paramètres prédéfinis s’affichent dans le volet de gauche et peuvent être utilisés à la volée avec d’autres ressources.

   ![chlimage_1-497](assets/chlimage_1-497.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

### Creating a responsive image preset {#creating-a-responsive-image-preset}

Pour créer un paramètre d&#39;image prédéfini réactif, suivez la procédure décrite dans la section [Création d&#39;un paramètre d&#39;image prédéfini](#creating-image-presets). Lorsque vous devez saisir la hauteur et la largeur dans la fenêtre **[!UICONTROL Modifier le paramètre d’image prédéfini]**, effacez les valeurs et laissez-les vides.

Lorsque ces valeurs sont vides, AEM détermine que ce paramètre d’image prédéfini est réactif. Vous pouvez ajuster les autres valeurs, le cas échéant.

![chlimage_1-498](assets/chlimage_1-498.png)

>[!NOTE]
>
>Pour que les boutons **[!UICONTROL URL]** et **[!UICONTROL RESS]** soient affichés lors de l’application d’un paramètre d’image prédéfini à une ressource, celle-ci doit être publiée.
>
>Dans le mode Scene7 de Dynamic Media, les paramètres d’image prédéfinis et les fichiers d’image sont publiés automatiquement.
>
>Dans le mode hybride de Dynamic Media, vous devez publier manuellement les paramètres d’image prédéfinis et les fichiers d’image.

### Image Preset options {#image-preset-options}

Lorsque vous créez ou modifiez des paramètres d’image prédéfinis, vous disposez des options décrites dans cette section. En outre, Adobe recommande les trois options de bonnes pratiques ** suivantes pour commencer :

* **[!UICONTROL Format]** (**[!UICONTROL onglet de base]** ) - Sélectionnez **[!UICONTROL JPEG]** ou un autre format qui répond à vos besoins.Tous les navigateurs Web prennent en charge le format d’image JPEG ; il offre un bon équilibre entre la taille des petits fichiers et la qualité des images.Toutefois, les images au format JPEG utilisent un modèle de compression avec perte qui peut introduire des artefacts d’image indésirables si le paramètre de compression est trop faible. Pour cette raison, Adobe recommande de définir la qualité de compression sur 75. Ce paramètre offre un bon équilibre entre la qualité d’image et la taille de fichier réduite.
* **[!UICONTROL Activer l’accentuation]** simple - Ne sélectionnez pas **[!UICONTROL Activer l’accentuation]** simple (ce filtre d’accentuation offre moins de contrôle que les paramètres de masquage flou).
* **[!UICONTROL Accentuation : Mode]** de ré-échantillonnage - Sélectionnez **[!UICONTROL Bi-Cubique]**.

#### Options de l’onglet De base {#basic-tab-options}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Champ</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Nom</strong></td> 
   <td>Saisissez un nom descriptif sans espaces. Ajoutez la spécification de taille de l’image dans le nom pour permettre aux utilisateurs d’identifier ce paramètre d’image prédéfini.</td> 
  </tr> 
  <tr> 
   <td><strong>Largeur et hauteur</strong></td> 
   <td>Saisissez la taille (en pixels) à utiliser pour la diffusion de l’image. La largeur et la hauteur doivent être supérieures à 0 pixel. Aucun paramètre prédéfini n’est en effet créé si l’une de ces valeurs est définie sur 0. Si aucune valeur n’est renseignée, un paramètre d’image prédéfini réactif est créé.</td> 
  </tr> 
  <tr> 
   <td><strong>Format</strong></td> 
   <td><p>Sélectionnez un format dans le menu.</p> <p>La sélection du format <strong>JPEG</strong> présente les options supplémentaires suivantes :</p> 
    <ul> 
     <li><strong>Qualité</strong> - Contrôle le niveau de compression JPEG. Ce paramètre affecte à la fois la taille du fichier et la qualité de l’image. L’échelle de qualité JPEG est de 1 à 100. L’échelle est visible lorsque vous faites glisser le curseur.</li> 
     <li><strong>Activer le sous-échantillonnage</strong> chromatique JPG - Comme l’oeil est moins sensible aux informations sur les couleurs haute fréquence qu’à la luminance haute fréquence, les images JPEG divisent les informations sur les images en composantes de luminance et de couleur. Lorsqu’une image JPEG est compressée, le composant de luminance reste à pleine résolution, tandis que les composants de couleur sont sous-échantillonnés en calculant la moyenne des groupes de pixels. Le sous-échantillonnage réduit le volume de données d’un demi-tiers ou d’un tiers, sans incidence sur la qualité perçue. Le sous-échantillonnage ne s’applique pas aux images en niveaux de gris. Cette technique permet de réduire la compression utile pour les images à contraste élevé (par exemple, les images avec du texte superposé).</li> 
    </ul> 
    <div>
      La sélection de l'option <strong>GIF</strong> ou <strong>GIF avec couche alpha</strong> offre les options <strong>Quantification de couleurs GIF</strong> supplémentaires suivantes : 
    </div> 
    <ul> 
     <li><strong>Type </strong>- Sélectionnez <strong>Adaptatif</strong> (valeur par défaut), <strong>Web</strong>ou <strong>Macintosh</strong>. Si vous sélectionnez <strong>GIF avec Alpha</strong>, l’option Macintosh n’est pas disponible.</li> 
     <li><strong>Dither</strong> - Sélectionnez <strong>Diffuse</strong> ou <strong>Désactivé</strong>.</li> 
     <li><strong>Nombre de couleurs</strong> : saisissez un nombre compris entre 2 et 256.</li> 
     <li><strong>Liste de couleurs</strong> : entrez une liste séparée par des virgules. Par exemple, pour le blanc, le gris et le noir, entrez 000000,888888,ffffff.</li> 
    </ul> 
    <div>
      Lorsque vous sélectionnez les options <strong>PDF</strong>, <strong>TIFF</strong> ou <strong>TIFF avec couche alpha</strong>, les autres options suivantes sont proposées : 
    </div> 
    <ul> 
     <li><strong>Compression</strong> : choisissez un algorithme de compression. Les options d'algorithme pour le format PDF sont <strong>Aucun</strong>, <strong>Zip</strong> et <strong>Jpeg</strong>. Les options pour le format TIFF sont <strong>Aucun</strong>, <strong>LZW</strong>, <strong>Jpeg</strong> et <strong>Zip</strong>. Les options pour le format TIFF avec couche alpha sont <strong>Aucun</strong>, <strong>LZW</strong> et <strong>Zip</strong>.</li> 
    </ul> <p>Aucune option supplémentaire n’est fournie si vous sélectionnez <strong>PNG</strong>, <strong>PNG avec couche alpha</strong> ou <strong>EPS</strong>.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Accentuation</strong></td> 
   <td>Sélectionnez l'option <strong>Activer l’accentuation simple</strong> pour appliquer un filtre d’accentuation de base à l’image à l’issue des opérations de mise à l’échelle. L’accentuation peut compenser le flou produit lors de l’affichage d’une image à une taille différente. </td> 
  </tr> 
 </tbody> 
</table>

#### Options de l’onglet Avancé {#advanced-tab-options}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Champ</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Espace colorimétrique</strong></td> 
   <td>Select <strong>RGB, CMYK,</strong> or <strong>Grayscale</strong> for the color space.</td> 
  </tr> 
  <tr> 
   <td><strong>Profil colorimétrique</strong></td> 
   <td>Sélectionnez le profil de l’espace colorimétrique de sortie dans lequel doit être convertie la ressource s’il diffère du profil en cours d’utilisation.</td> 
  </tr> 
  <tr> 
   <td><strong>Intention de rendu</strong></td> 
   <td>Vous pouvez remplacer l’intention de rendu par défaut. Les intentions de rendu déterminent ce qu’il advient des couleurs qui ne peuvent pas être reproduites dans le profil colorimétrique cible (hors de la gamme des couleurs). L’intention de rendu est ignorée si elle n’est pas compatible avec le profil ICC. 
    <ul> 
     <li>Sélectionnez <strong>Perception</strong> pour compresser toute la gamme des couleurs d’un espace colorimétrique dans un autre lorsqu’une ou plusieurs couleurs de l’image d’origine se situent en dehors de la gamme de l’espace colorimétrique de destination.</li> 
     <li>Sélectionnez <strong>Colorimétrie relative</strong> si une couleur de l’espace colorimétrique actuel se situe hors de la gamme des couleurs dans l’espace cible et si vous souhaitez la faire correspondre à la couleur la plus proche dans la gamme des couleurs de cet espace cible, sans affecter d’autres couleurs. </li> 
     <li>Sélectionnez <strong>Saturation</strong> pour reproduire la saturation des couleurs de l’image d’origine lors de sa conversion dans l’espace colorimétrique cible. </li> 
     <li>Sélectionnez <strong>Colorimétrie absolue</strong> pour faire correspondre exactement les couleurs sans aucun ajustement pour le point blanc ou noir qui altérerait la luminosité de l’image.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>Compensation du point noir</strong></td> 
   <td>Sélectionnez cette option si le profil de sortie prend en charge cette fonction. La compensation du point noir est ignorée si elle n’est pas compatible avec le profil ICC spécifié.</td> 
  </tr> 
  <tr> 
   <td><strong>Tramage</strong></td> 
   <td>Sélectionnez cette option pour réduire les artefacts de bandes de couleurs ou éventuellement les éviter. </td> 
  </tr> 
  <tr> 
   <td><strong>Type d’accentuation</strong></td> 
   <td><p>Sélectionnez <strong>Aucun</strong>, <strong>Accentuer</strong> ou <strong>Masquage flou</strong>. </p> 
    <ul> 
     <li>Sélectionnez <strong>Aucun</strong> pour désactiver l’accentuation.</li> 
     <li>Sélectionnez l'option <strong>Accentuer</strong> pour appliquer un filtre d’accentuation de base à l’image à l’issue des opérations de mise à l’échelle. L’accentuation peut compenser le flou produit lors de l’affichage d’une image à une taille différente. </li> 
     <li>Select<strong> Unsharp mask</strong> to fine-tune a sharpening filter effect on the final downsampled image. You can control intensity of effect, radius of the effect (measured in pixels) and a threshold of contrast that will be ignored. This effect uses the same options as Photoshop’s “Unsharp Mask” filter.</li> 
    </ul> <p>L’option <strong>Masquage flou</strong> propose les options suivantes :</p> 
    <ul> 
     <li><strong>Montant</strong> - Contrôle le degré de contraste appliqué aux pixels de contour. La valeur réelle par défaut est de 1,0. Pour les images à haute résolution, vous pouvez l’augmenter jusqu’à 5,0. Envisagez la quantité comme une mesure de l’intensité du filtre.</li> 
     <li><strong>Rayon</strong> - Détermine le nombre de pixels entourant les pixels de contour qui affectent l’accentuation. Pour les images haute résolution, entrez un nombre réel compris entre 1 et 2. Une valeur faible accentue uniquement les pixels de contour ; une valeur élevée accentue une bande plus large de pixels. La valeur appropriée dépend de la taille de l’image.</li> 
     <li><strong>Seuil</strong> : détermine la plage de contraste à ignorer lorsque le filtre de masquage flou est appliqué. En d’autres termes, cette option détermine la différence entre les pixels accentués et la zone environnante avant qu’ils ne soient considérés comme des pixels de contour et soient accentués. Pour éviter d’introduire du bruit, testez des valeurs entières comprises entre 2 et 20. </li> 
     <li><strong>Appliquer à</strong> : détermine si l'accentuation s'applique à chaque couleur ou à chaque luminosité.</li> 
    </ul> 
    <div>
      L’accentuation est décrite dans <a href="https://marketing.adobe.com/resources/help/en_US/s7/sharpening/s7_sharpening_images.pdf">Accentuation des images</a>. 
    </div> </td> 
  </tr> 
  <tr> 
   <td><strong>Mode Rééchantillonnage</strong></td> 
   <td>Sélectionnez une option <strong>Mode Rééchantillonnage</strong>. Ces options accentuent l’image lorsque sa résolution est réduite : 
    <ul> 
     <li><strong>Bi-Linéaire</strong> - Méthode de rééchantillonnage la plus rapide. Certains artefacts de crénelage sont visibles.</li> 
     <li><strong>Bi-cubique</strong> : augmente l’utilisation du processeur, mais produit des images plus nettes avec des artefacts de crénelage moins visibles.</li> 
     <li><strong>Sharp2</strong> - Peut produire des résultats légèrement plus nets que Bi-Cubique, mais à un coût CPU encore plus élevé.</li> 
     <li><strong>Bi-Sharp</strong> - Sélectionne le rééchantillonneur par défaut de Photoshop pour réduire la taille de l’image, appelé <strong>accentuation</strong> bicubique dans Adobe Photoshop.</li> 
     <li><strong>Chaque couleur</strong> et <strong>Luminosité</strong> : chaque méthode peut être basée sur la couleur ou la luminosité. Par défaut, l’option <strong>Chaque couleur</strong> est sélectionnée.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>Résolution d'impression</strong></td> 
   <td>Choisissez une résolution d’impression pour cette image ; 72 pixels est la valeur par défaut.</td> 
  </tr> 
  <tr> 
   <td><strong>Modificateur d’image</strong></td> 
   <td><p>Beyond the common image settings available in the UI, Dynamic Media supports numerous advanced image modifications that you can specify in the <strong>Image Modifiers</strong> field. These parameters are defined in the <a href="https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/c_command_reference.html">Image Server Protocol command reference</a>.</p> <p>Important : La fonctionnalité suivante répertoriée dans l’API n’est pas prise en charge :</p> 
    <ul> 
     <li>Commandes de base de création de modèles et de rendu de texte : <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> et <code>textPs=</code></li> 
     <li>Commandes de localisation : <code>locale=</code> et <code>req=xlate</code></li> 
     <li><code>req=set</code> n’est pas disponible pour une utilisation générale.</li> 
     <li><code>req=mbrset</code></li> 
     <li><code>req=saveToFile</code></li> 
     <li><code>req=targets</code></li> 
     <li><code>template=</code></li> 
     <li>Services Dynamic Media non essentiels : SVG, rendu d’image et impression en ligne</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Defining Image Preset options with image modifiers {#defining-image-preset-options-with-image-modifiers}

Outre les options disponibles dans les onglets **[!UICONTROL Simple]** et **[!UICONTROL Avancé]** , vous pouvez définir des modificateurs d’image afin de vous donner plus d’options lorsque vous définissez des paramètres d’image prédéfinis. Le rendu des images dépend de l’API de rendu des images de Contenu multimédia dynamique. L’API est définie en détail dans la référence [du protocole](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/c_http_protocol_reference.html)HTTP.

Vous trouverez ci-dessous des exemples de tâches que vous pouvez exécuter à l’aide des modificateurs d’image.

>[!NOTE]
>
>Some image modifiers [cannot be used in AEM](#advanced-tab-options).

* [op_invert](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_invert.html) - Inverse chaque composante de couleur pour obtenir un effet d’image négatif.

   ```xml
   &op_invert=1
   ```

   ![chlimage_1-499](assets/chlimage_1-499.png)

* [op_blur](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_blur.html) : applique un effet de flou à l’image.

   ```xml
   &op_blur=25
   ```

   ![chlimage_1-500](assets/chlimage_1-500.png)

* Commandes combinées : op_blur et op-invert

   ```xml
   &op_invert=1&op_blur=25
   ```

   ![chlimage_1-501](assets/chlimage_1-501.png)

* [op_brightness](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_brightness.html) : diminue ou augmente la luminosité.

   ```xml
   &op_brightness=75
   ```

   ![chlimage_1-502](assets/chlimage_1-502.png)

* [opac](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/r_opac.html) : permet de régler l’opacité de l’image. Cet attribut vous permet de diminuer l’opacité du premier plan.

   ```xml
   opac=50
   ```

   ![chlimage_1-503](assets/chlimage_1-503.png)

## Modification des paramètres d’image prédéfinis {#modifying-image-presets}

**Pour modifier les paramètres** d’image prédéfinis :

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale.
1. Appuyez sur l’icône **[!UICONTROL Outils]** , puis accédez à **[!UICONTROL Ressources > Paramètres d’image prédéfinis]**.

   ![chlimage_1-504](assets/chlimage_1-504.png)

1. Sélectionnez un paramètre prédéfini, puis appuyez sur **[!UICONTROL Modifier]**.
1. Sur la page **[!UICONTROL Modifier les paramètres]** d’image prédéfinis, effectuez les modifications souhaitées, puis appuyez sur **[!UICONTROL Enregistrer]**.

## Publishing Dynamic Media image presets {#publishing-image-presets}

Si vous exécutez le mode hybride de Dynamic Media, vous devez publier manuellement les paramètres d’image prédéfinis.

Si vous exécutez le mode Scene7 de Dynamic Media, les paramètres d’image prédéfinis sont automatiquement publiés ; vous n’avez pas besoin de réaliser ces étapes.

**Pour publier des paramètres d’image prédéfinis dans Contenu multimédia dynamique - Mode** hybride :

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale.
1. Appuyez sur l’icône **[!UICONTROL Outils]** , puis accédez à **[!UICONTROL Ressources > Paramètres d’image prédéfinis]**.
1. Select the image preset or multiple image presets from the list of image presets, then tap **[!UICONTROL Publish]**.
1. Une fois le paramètre d’image prédéfini publié, l’état passe de Non publié à Publié.

   ![chlimage_1-505](assets/chlimage_1-505.png)

## Deleting Dynamic Media image presets {#deleting-image-presets}

**Pour supprimer les paramètres d’image prédéfinis** Contenu multimédia dynamique :

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale.
1. Appuyez sur l’icône **[!UICONTROL Outils]** , puis accédez à **[!UICONTROL Ressources > Paramètres d’image prédéfinis]**.
1. Sélectionnez un paramètre prédéfini, puis appuyez sur **[!UICONTROL Supprimer]**. Dynamic Media vous invite à confirmer la suppression. Appuyez sur **[!UICONTROL Supprimer]**.

