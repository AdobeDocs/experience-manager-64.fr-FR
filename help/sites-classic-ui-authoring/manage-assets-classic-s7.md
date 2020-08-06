---
title: Ajouter les fonctionnalités de Dynamic Media Classic à votre page
seo-title: Ajouter les fonctionnalités de Dynamic Media Classic à votre page
description: Adobe Dynamic Media Classic est une solution hébergée qui permet de gérer, d’améliorer, de publier et de diffuser des fichiers multimédias enrichis sur des écrans et des imprimantes Web, mobiles, électroniques et connectés à Internet.
seo-description: Adobe Dynamic Media Classic est une solution hébergée qui permet de gérer, d’améliorer, de publier et de diffuser des fichiers multimédias enrichis sur des écrans et des imprimantes Web, mobiles, électroniques et connectés à Internet.
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
translation-type: tm+mt
source-git-commit: a3a160a0281c1ea2ca050c2c747d6a5ec1d952b3
workflow-type: tm+mt
source-wordcount: '3429'
ht-degree: 32%

---


# Ajouter les fonctionnalités de Dynamic Media Classic à votre page{#adding-scene-features-to-your-page}

[Adobe Dynamic Media Classic](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) est une solution hébergée qui permet de gérer, d’améliorer, de publier et de diffuser des fichiers multimédias enrichis sur des écrans et des imprimantes Web, mobiles, électroniques et connectés à Internet.

Vous pouvez vue AEM fichiers publiés dans Dynamic Media Classic dans différentes visionneuses :

* Zoom
* Fenêtre déroulante
* Vidéo
* Modèle d’image
* Image

Vous pouvez publier des fichiers numériques directement depuis AEM vers Dynamic Media Classic et vous pouvez publier des fichiers numériques depuis Dynamic Media Classic vers AEM.

Cette section décrit comment publier des fichiers numériques d’AEM vers Dynamic Media Classic et vice versa. Les visionneuses sont également décrites en détail. Pour plus d’informations sur la configuration des AEM pour Dynamic Media Classic, voir [Intégration de Dynamic Media Classic à AEM](/help/sites-administering/scene7.md).

Voir aussi [Ajout de zones cliquables](/help/assets/image-maps.md).

Pour plus d’informations sur l’utilisation des composants vidéo avec AEM, voir :

* [Vidéo](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>If Dynamic Media Classic assets do not display properly, make sure that Dynamic media is [disabled](/help/assets/config-dynamic.md#disabling-dynamic-media) and then refresh the page.

## Publication manuelle dans Dynamic Media Classic à partir de ressources {#manually-publishing-to-scene-from-assets}

Vous pouvez publier des fichiers numériques dans Dynamic Media Classic à partir de la console Ressources de l’interface utilisateur classique ou directement à partir de la ressource.

>[!NOTE]
>
>AEM publie dans Dynamic Media Classic de manière asynchrone. After you click **[!UICONTROL Publish]**, it may take several seconds for your asset to publish to Dynamic Media Classic.


### Publication depuis la console Ressources {#publishing-from-the-assets-console}

Pour publier dans Contenu multimédia dynamique classique à partir de la console Ressources si les ressources se trouvent dans un dossier de cible Contenu multimédia dynamique :

1. In the AEM classic UI, click **[!UICONTROL Digital Assets]** to access the digital asset manager.

1. Select the asset (or assets) or folder from within the target folder you want to publish to Dynamic Media Classic and right-click and select **[!UICONTROL Publish to Dynamic Media Classic]**. Vous pouvez également sélectionner **[!UICONTROL Publier dans Contenu multimédia dynamique classique]** dans le menu **[!UICONTROL Outils] .

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Accédez à Dynamic Media Classic et vérifiez que les ressources sont disponibles.

   >[!NOTE]
   >
   >If the assets are not in a Dynamic Media Classic synchronized folder, **[!UICONTROL Publish to Dynamic Media Classic]** in both menus is visible but disabled.

### Publication depuis un élément {#publishing-from-an-asset}

Vous pouvez publier manuellement un fichier tant qu’il se trouve dans le dossier Dynamic Media Classic synchronisé.

>[!NOTE]
>
>Si le fichier n’est pas situé dans le dossier synchronisé Dynamic Media Classic, le lien **[!UICONTROL Publier vers Contenu multimédia dynamique classique]** n’est pas disponible.

**Pour publier du contenu dans Dynamic Media Classic directement à partir d’un fichier** numérique :

1. Dans AEM, cliquez sur **[!UICONTROL Eléments numériques]** pour accéder au Digital Asset Manager.

1. Double-cliquez pour ouvrir un élément.

1. Dans le volet d’informations sur les ressources, sélectionnez **[!UICONTROL Publier dans Contenu multimédia dynamique classique]**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. Le lien devient **[!UICONTROL Publication...]**, puis **[!UICONTROL Publié]**. Accédez à Dynamic Media Classic et vérifiez que la ressource est disponible.

   >[!NOTE]
   >
   >If the asset does not publish properly to Dynamic Media Classic, the link changes to **[!UICONTROL Publishing Failed]**. Si le fichier a déjà été publié dans Dynamic Media Classic, le lien indique **[!UICONTROL Nouvelle publication dans Dynamic Media Classic]**. La republication vous permet d’apporter des modifications à un fichier dans AEM et de le republier.

### Publishing assets from outside the CQ target folder {#publishing-assets-from-outside-the-cq-target-folder}

Adobe vous recommande de publier des fichiers dans Dynamic Media Classic uniquement à partir des fichiers du dossier de cible Dynamic Media Classic. However, if you need to upload assets from a folder outside of the target folder, you can still do that by uploading them to an *ad-hoc* folder on Dynamic Media Classic.

Pour ce faire, vous devez configurer la configuration Cloud pour la page où apparaîtra le fichier. Vous ajoutez ensuite un composant Contenu multimédia dynamique classique à la page et faites glisser un fichier sur le composant. After the page properties are set for that page, a **[!UICONTROL Publish to Dynamic Media Classic]** link appears that when selected triggers uploading to Dynamic Media Classic.

>[!NOTE]
>
>Les fichiers qui se trouvent dans le dossier ad hoc n’apparaissent pas dans le navigateur de contenu Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu dynamique Media Classic.

**Pour publier des fichiers qui résident en dehors du dossier** de cible CQ :

1. In AEM in the classic UI, click **[!UICONTROL Websites]** and navigate to the web page that you want to add a digital asset to that is not yet published to Dynamic Media Classic. (Les règles normales d’héritage de la page s’appliquent.)

1. In the sidekick, click the **[!UICONTROL Page]** icon, then click **[!UICONTROL Page Properties]**.

1. Cliquez sur **[!UICONTROL Cloud Services > Ajouter services > Dynamic Media Classic (Scene7)**.
1. Dans la liste déroulante Adobe de données Dynamic Media Classic, sélectionnez la configuration souhaitée, puis cliquez sur **[!UICONTROL OK]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. Sur la page Web, ajoutez un composant Scene7 (Dynamic Media Classic) à l’emplacement de votre choix sur la page.
1. Depuis l’outil de recherche de contenu, faites glisser un élément numérique vers le composant. Un lien s’affiche pour vous permettre de **[!UICONTROL vérifier l’état]** de publication de Contenu multimédia dynamique classique.

   >[!NOTE]
   >
   >If the digital asset is in the CQ target folder, then no link to **[!UICONTROL Check Dynamic Media Classic Publication Status]** appears. Les éléments sont simplement placés dans le composant.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Cliquez sur **[!UICONTROL Vérifier l’état]** de publication de Contenu multimédia classique dynamique. Si le fichier n’est pas publié, AEM le publie dans Dynamic Media Classic. Une fois téléchargé, l’élément figure dans le dossier ad hoc. Par défaut, le dossier ad hoc se trouve dans le `name_of_the_company/CQ5_adhoc`. Vous pouvez [configurer ce chemin, le cas échéant](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Si la ressource ne se trouve pas dans un dossier synchronisé Dynamic Media Classic et qu’aucune configuration cloud Dynamic Media Classic n’est associée à la page active, le téléchargement échoue.

## Composants Scene7 (Dynamic Media Classic) {#scene-components}

Les composants suivants de Dynamic Media Classic sont disponibles dans AEM :

* Zoom
* Fenêtre déroulante (Zoom)
* Modèle d’image
* Image
* Vidéo

>[!NOTE]
>
>These components are not available by default and need to be selected in **[!UICONTROL Design]** mode before using.

After they are made available in **[!UICONTROL Design]** mode, you can add the components to your page like any other AEM component. Les fichiers qui n’ont pas encore été publiés dans Dynamic Media Classic sont publiés dans Dynamic Media Classic s’ils se trouvent dans un dossier synchronisé, sur une page ou avec une configuration cloud Dynamic Media Classic.

### Flash viewers end-of-life notice {#flash-viewers-end-of-life-notice}

Depuis le 31 janvier 2017, l’Adobe Dynamic Media Classic a officiellement mis fin à la prise en charge de la plate-forme du lecteur de Flash.

For more information about this important change, see [Flash viewer end-of-life FAQs](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Adding a Dynamic Media Classic component to a page {#adding-a-scene-component-to-a-page}

Ajouter un composant Contenu multimédia dynamique classique à une page revient à ajouter un composant à une page. Les composants de Dynamic Media Classic sont décrits en détail dans les sections suivantes.

**Pour ajouter un composant/visionneuse Contenu multimédia dynamique classique à une page dans l’interface utilisateur** classique :

1. Dans AEM, ouvrez la page dans laquelle vous souhaitez ajouter le composant Contenu multimédia dynamique classique.

1. If no Dynamic Media Classic components are available, click the ruler in the sidekick to enter **[!UICONTROL Design]** mode, click **[!UICONTROL Edit]** parsys, and select all the **[!UICONTROL Dynamic Media Classic]** components to make them available.

1. Return to **[!UICONTROL Edit]** mode by clicking the pencil in the sidekick.

1. Drag a component from the **[!UICONTROL Dynamic Media Classic]** group in the sidekick onto the page in the desired location.

1. Cliquez sur l’icône **[!UICONTROL Modifier]** pour ouvrir le composant.

1. Modifiez le composant comme requis et cliquez sur **[!UICONTROL OK]** pour enregistrer les modifications.

### Ajout d’expériences de visionnage interactif à un site web réactif {#adding-interactive-viewing-experiences-to-a-responsive-website}

Une conception réactive signifie que les éléments s’adaptent selon l’emplacement où ils sont affichés. Avec une conception adaptée, les mêmes ressources s’affichent efficacement sur plusieurs périphériques.

**Pour ajouter une expérience de visualisation interactive à un site réactif dans l’interface utilisateur** classique :

1. Log in to AEM, and ensure that you have [configured Adobe Dynamic Media Classic Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) and that Dynamic Media Classic components are available.

   >[!NOTE]
   >
   >Si les composants de gestion de contenu Web de Dynamic Media Classic ne sont pas disponibles, veillez à les activer en mode **[!UICONTROL Design] .

1. In a website with the Dynamic Media Classic components enabled, drag an **[!UICONTROL Image]** viewer to the page.
1. Edit the component and adjust the breakpoints in the **[!UICONTROL Dynamic Media Classic Settings]** tab.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Confirmez que les visionneuses se redimensionnent de manière réactive et que toutes les interactions sont optimisées pour les ordinateurs de bureau, les tablettes et les appareils mobiles.

### Paramètres communs à tous les composants Dynamic Media Classic {#settings-common-to-all-scene-components}

Bien que les options de configuration varient, les éléments suivants sont communs à tous les composants de Dynamic Media Classic :

* **[!UICONTROL Référence du fichier]** : accédez à un fichier que vous souhaitez référencer. La référence de fichier affiche l’URL du fichier et pas nécessairement l’URL complète de Contenu multimédia dynamique classique, y compris les commandes et paramètres d’URL. Vous ne pouvez pas ajouter de commandes d’URL et de paramètres Dynamic Media Classic dans ce champ. Ils doivent être ajoutés par l’intermédiaire de la fonctionnalité correspondante du composant.
* **[!UICONTROL Largeur]** : permet de définir la largeur.
* **[!UICONTROL Hauteur]** : permet de définir la hauteur.

You set these configuration options by double-clicking a Dynamic Media Classic component, for example, when you open a **[!UICONTROL Zoom]** component:

![chlimage_1-80](assets/chlimage_1-80.png)

### Zoom {#zoom}

Le composant Zoom HTML5 affiche une image plus grande lorsque vous appuyez sur le bouton +.

L’élément comporte des outils de zoom dans sa partie inférieure. Cliquez sur **[!UICONTROL +]** pour agrandir. Cliquez sur **[!UICONTROL -]** pour réduire. Clicking **[!UICONTROL x]** or the reset zoom arrow brings the image back to the original size it was imported as. Cliquez sur les flèches en diagonale pour passer en mode plein écran. Cliquez sur **[!UICONTROL Modifier]** pour configurer le composant. With this component, you can configure [settings common to all Dynamic Media Classic components](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-5.png)

### Flyout {#flyout}

Dans le composant Fenêtre déroulante HTML5, l’élément s’affiche sous la forme d’un écran partagé : à gauche se trouve l’élément à la taille spécifiée, à droite la partie sur laquelle le zoom a été effectué. Cliquez sur **[!UICONTROL Modifier]** pour configurer le composant. With this component, you can configure [settings common to all Dynamic Media Classic components](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents).

>[!NOTE]
>
>Si le composant Fenêtre déroulante utilise une taille personnalisée, cette taille personnalisée est utilisée et la configuration réactive du composant est désactivée.
>
>If your Flyout component uses the default size, as set in the [!UICONTROL Design] view, then the default size is used and the component stretches to accomodate the page layout size with responsive setup of the component enabled. Sachez toutefois qu’il existe une limite à la configuration réactive du composant. Lorsque vous utilisez le composant Fenêtre déroulante avec la configuration réactive, vous ne devez pas l’utiliser avec l’étirement de pleine page. Dans le cas contraire, la fenêtre déroulante peut s’étendre au-delà de la bordure droite de la page.

![chlimage_1-81](assets/chlimage_1-81.png)

### Image {#image}

Le composant Image de Contenu multimédia dynamique classique vous permet d’ajouter des fonctionnalités de Contenu multimédia dynamique classique à vos images, telles que les modificateurs de Contenu multimédia dynamique classique, les paramètres prédéfinis d’image ou de visionneuse et l’accentuation. Le composant d’image Contenu multimédia dynamique classique est similaire à d’autres composants d’image dans AEM avec une fonctionnalité spéciale Contenu multimédia dynamique classique. Dans cet exemple, le modificateur URL Dynamic Media Classic de l’image est `&op_invert=1` appliqué.

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL Titre, Texte]** de remplacement : dans l’onglet [!UICONTROL Avancé] , ajoutez un titre à l’image et un texte de remplacement pour les utilisateurs dont les graphiques sont désactivés.

**[!UICONTROL URL, Ouvrir dans]** : vous pouvez définir un fichier à partir duquel ouvrir un lien. Set the **[!UICONTROL URL]** and **[!UICONTROL Open in]** to indicate whether you want it to open in the same window or a new window.

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL Paramètre]** prédéfini de visionneuse : sélectionnez un paramètre prédéfini de visionneuse existant dans le menu déroulant. Si le paramètre prédéfini de visionneuse que vous recherchez n’est pas visible, vous devrez le rendre visible. Voir [Gestion des paramètres prédéfinis de visionneuse](/help/assets/managing-viewer-presets.md). Si vous utilisez un paramètre prédéfini d’image, vous ne pouvez pas sélectionner de paramètre prédéfini de visionneuse, et inversement.

**[!UICONTROL Configuration]** de Dynamic Media Classic : sélectionnez la configuration de Dynamic Media Classic que vous souhaitez utiliser pour récupérer les paramètres d’image prédéfinis principaux à partir de Scene7 Publishing System.

**[!UICONTROL Paramètre]** d’image prédéfini : sélectionnez un paramètre d’image prédéfini existant dans le menu déroulant. Si le paramètre d’image prédéfini que vous recherchez n’est pas visible, vous devrez le rendre visible. Voir [Gestion des paramètres d’image prédéfinis](/help/assets/managing-image-presets.md). Si vous utilisez un paramètre prédéfini d’image, vous ne pouvez pas sélectionner de paramètre prédéfini de visionneuse, et inversement.

**[!UICONTROL Format]** de sortie : sélectionnez le format de sortie de l&#39;image, par exemple jpeg. Selon le format de sortie que vous sélectionnez, vous pouvez ajouter des options de configuration supplémentaires. Voir [Gestion des paramètres d’image prédéfinis](/help/assets/managing-image-presets.md).

**[!UICONTROL Accentuation]** : sélectionnez le mode d’accentuation de l’image. L’accentuation est expliquée en détail dans [*Adobe Dynamic Media Classic Image Quality and Sharpening Best Practices (Qualité des images dynamiques classiques et Meilleures pratiques *](/help/assets/assets/s7_sharpening_images.pdf)d’accentuation).

**[!UICONTROL Modificateurs]** d’URL : vous pouvez modifier les effets d’image en fournissant d’autres commandes d’image Dynamic Media Classic. These are described in [Managing Image Presets](/help/assets/managing-image-presets.md) and the [Command reference](https://docs.adobe.com/content/help/fr-FR/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL Points d’arrêt]** : si votre site Web est réactif, vous souhaitez ajuster les points d’arrêt. Les points d’arrêt doivent être séparés par des virgules `,`.

### Modèle d’image {#image-template}

[Les modèles](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) d’image Dynamic Media Classic sont du contenu Photoshop superposé qui a été importé dans Dynamic Media Classic, où le contenu et les propriétés ont été paramétrés en fonction de la variabilité. Le composant **[!UICONTROL Modèle d’image]** permet d’importer des images et de modifier le texte dynamiquement dans AEM. En outre, vous pouvez configurer le composant **[!UICONTROL Modèle d’image]** afin d’utiliser des valeurs provenant de ClientContext de sorte que chaque utilisateur voit l’image d’une manière personnalisée.

Cliquez sur **[!UICONTROL Modifier]** pour configurer le composant. You can configure [settings common to all Dynamic Media Classic components](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents) as well as other settings described in this section.

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL Référence du fichier, Largeur, Hauteur]** - Voir les paramètres communs à tous les composants Dynamic Media Classic.

>[!NOTE]
>
>Les commandes et paramètres d’URL de Dynamic Media Classic ne peuvent pas être ajoutés directement à l’URL de référence de fichier. Ils ne peuvent être définis que dans l’interface utilisateur du composant, dans le panneau **[!UICONTROL Paramètre]**.

**[!UICONTROL Titre, Texte]** de remplacement Dans l’onglet Modèle [!UICONTROL d’image] Contenu multimédiadynamique classique, ajoutez un titre à l’image et ajoutez un texte de remplacement pour les utilisateurs dont les graphiques sont désactivés.

**[!UICONTROL URL, Ouvrir dans]** Vous pouvez définir un fichier à partir duquel ouvrir un lien. Définissez l’**[!UICONTROL URL]**, puis dans le champ **[!UICONTROL Ouvrir dans]**, indiquez si vous souhaitez l’ouvrir dans la même fenêtre ou une nouvelle fenêtre.

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL Panneau]** de paramètres Lors de l’importation d’une image, les paramètres sont prérenseignés avec les informations de l’image. En l’absence de contenu pouvant être modifié dynamiquement, cette fenêtre est vide.

![chlimage_1-85](assets/chlimage_1-85.png)

#### Modification dynamique du texte {#changing-text-dynamically}

Pour une modification dynamique du texte, saisissez le nouveau texte dans les champs, puis cliquez sur **[!UICONTROL OK]**. Dans cet exemple, le **[!UICONTROL Prix]** est désormais de 50 $ et l’expédition de 99 cents.

![chlimage_1-86](assets/chlimage_1-86.png)

Le texte de l’image change. Vous pouvez réinitialiser le texte sur la valeur d’origine en cliquant sur **[!UICONTROL Réinitialiser]** en regard du champ.

![chlimage_1-87](assets/chlimage_1-87.png)

#### Modification du texte afin de refléter une valeur ClientContext {#changing-text-to-reflect-the-value-of-a-client-context-value}

To link a field to a client context value, click **[!UICONTROL Select]** to open the client-context menu, select the client context, and click **[!UICONTROL OK]**. Dans cet exemple, le nom change selon la liaison entre le Nom et le nom formaté du profil.

![chlimage_1-88](assets/chlimage_1-88.png)

Le texte reflète le nom de l’utilisateur actuellement connecté. Vous pouvez réinitialiser le texte sur la valeur d’origine en cliquant sur **[!UICONTROL Réinitialiser]** en regard du champ.

![chlimage_1-89](assets/chlimage_1-89.png)

#### Création d’un lien avec le modèle d’image Contenu multimédia dynamique classique {#making-the-scene-image-template-a-link}

**Pour faire du modèle d’image Dynamic Media Classic un lien**:

1. On the page with the Dynamic Media Classic image template component, click **[!UICONTROL Edit]**.
1. Dans le champ **[!UICONTROL URL]**, saisissez l’URL à laquelle l’utilisateur accède lorsqu’il clique sur l’image. Dans le champ **[!UICONTROL Ouvrir dans]**, choisissez où vous souhaitez que la cible s’ouvre (une nouvelle fenêtre ou la même fenêtre).

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Cliquez sur **[!UICONTROL OK]**.

### Composant vidéo {#video-component}

The Dynamic Media Classic **[!UICONTROL Video]** component (available from the Dynamic Media Classic section of the sidekick) uses device and bandwidth detection to serve the right video to each screen. Ce composant est un lecteur vidéo HTML5. Il s’agit d’une visionneuse unique pouvant être utilisée sur plusieurs canaux.

Il peut être utilisé pour des ensembles de vidéos adaptables, une vidéo MP4 unique ou une vidéo F4V unique.

See [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) for more information on how videos work with Dynamic Media Classic integration. In addition, see how [the **Dynamic Media Classic video** component compares to the foundation **video** component](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![chlimage_1-91](assets/chlimage_1-91.png)

### Limitations connues du composant vidéo {#known-limitations-for-the-video-component}

La gestion des actifs numériques et la gestion de contenu web d’Adobe indiquent si une vidéo maître est téléchargée. Elles n’affichent pas les éléments proxy suivants :

* Rendus codés Dynamic Media Classic
* Visionneuses de vidéos adaptatives Dynamic Media Classic

Lors de l’utilisation d’une visionneuse de vidéos adaptative avec le composant vidéo Contenu multimédia dynamique classique, vous devez redimensionner le composant pour l’adapter aux dimensions de la vidéo.

## Explorateur de contenu Dynamic Media Classic {#scene-content-browser}

L’explorateur de contenu Dynamic Media Classic vous permet de vue de contenu à partir de Contenu Dynamic Media Classic directement en AEM. To access the content browser, in the Content Finder, select **[!UICONTROL Dynamic Media Classic]** in the touch-optimized user interface or the **[!UICONTROL S7]** icon in the classic user interface. La fonctionnalité est identique pour les deux interfaces utilisateur.

Si vous disposez de plusieurs configurations, AEM affiche la [configuration par défaut](/help/sites-administering/scene7.md#configuring-a-default-configuration). Vous pouvez sélectionner différentes configurations directement dans l’explorateur de contenu Dynamic Media Classic du menu déroulant.

>[!NOTE]
>
>* Les fichiers situés dans le dossier ad hoc n’apparaissent pas dans l’explorateur de contenu Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu dynamique Media Classic.
>* Lorsque la Prévisualisation [sécurisée est activée](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), les fichiers publiés et non publiés dans Dynamic Media Classic s’affichent dans le navigateur de contenu Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu de Contenu
>* If you do not see **[!UICONTROL Dynamic Media Classic]** or the **[!UICONTROL S7]** icon as an option in the content browser, you need to [configure Dynamic Media Classic to work with AEM](/help/sites-administering/scene7.md).

   >
   >
* Pour la vidéo, l’explorateur de contenu Dynamic Media Classic prend en charge :
   >
   >
* Les ensembles de vidéos adaptables. Il s’agit de conteneurs de tous les rendus vidéo requis pour lire la vidéo sans difficultés sur plusieurs écrans.
>* La vidéo MP4 unique
>* Vidéo F4V simple


### Parcours du contenu dans l’interface utilisateur classique {#browsing-content-in-the-classic-ui}

Parcourez le contenu dans Dynamic Media Classic en cliquant sur l’onglet **[!UICONTROL S7]** .

Vous pouvez modifier la configuration à laquelle vous accédez en sélectionnant la configuration. Les dossiers changent en fonction de la configuration sélectionnée.

![chlimage_1-92](assets/chlimage_1-92.png)

Comme avec l’outil de recherche de contenu des ressources, vous pouvez effectuer une rechercher des éléments et filtrer les résultats. Néanmoins, à la différence de l’outil de recherche de contenu des ressources, lors de la saisie d’un mot-clé dans l’onglet **[!UICONTROL S7]**, le nom du fichier *commence par* la chaîne que vous avez saisie au lieu de *contenir* le mot-clé.

Par défaut, les éléments sont affichés par nom de fichier. Vous pouvez également filtrer les résultats par type d’élément.

>[!NOTE]
>
>Pour la vidéo, l’explorateur de contenu Dynamic Media Classic de WCM prend en charge :
>
>* Les ensembles de vidéos adaptables. Il s’agit de conteneurs de tous les rendus vidéo requis pour lire la vidéo sans difficultés sur plusieurs écrans.
>* La vidéo MP4 unique
>* Vidéo F4V simple

>



### Recherche de fichiers Dynamic Media Classic dans l’explorateur de contenu {#searching-for-scene-assets-with-the-content-browser}

La recherche de ressources de Contenu multimédia dynamique classique est similaire à la recherche de AEM ressources, sauf que lorsque vous effectuez une recherche, une vue distante des ressources s’affiche dans le système Contenu multimédia dynamique classique, plutôt que de les importer directement dans AEM.

Vous pouvez utiliser l’interface utilisateur classique ou l’interface utilisateur optimisée pour les écrans tactiles pour visualiser et rechercher des éléments. Selon l’interface, le mode de recherche est légèrement différent.

Lors d’une recherche dans l’une ou l’autre des interfaces, vous pouvez filtrer selon les critères suivants (présentés ici dans l’interface utilisateur optimisée pour les écrans tactiles) :

**[!UICONTROL Entrez des mots-clés]** : vous pouvez rechercher des ressources par nom. Lors de la recherche par mots-clés, vous saisissez le début du nom du fichier. Par exemple, la saisie du mot « swimming » recherche tous les noms de fichier qui commencent par ces lettres, dans cet ordre. Veillez à appuyer sur Entrée après avoir tapé le mot-clé de recherche de l’élément.

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL Dossier/chemin]** : le nom du dossier qui s’affiche dépend de la configuration que vous avez sélectionnée. Vous pouvez descendre vers des niveaux inférieurs en cliquant sur l’icône du dossier et en sélectionnant un sous-dossier, puis en cliquant sur la coche pour le sélectionner.

Si vous saisissez un mot-clé et sélectionnez un dossier, AEM recherche ce dossier et tous les sous-dossiers. Néanmoins, si vous ne saisissez pas de mots-clés lors de la recherche, la sélection du dossier n’affiche que les éléments de ce dossier et n’inclut pas les sous-dossiers.

Par défaut, AEM recherche le dossier sélectionné et tous les sous-dossiers.

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL Type de fichier]** Sélectionnez Contenu multimédia dynamique classique pour parcourir le contenu Contenu multimédia dynamique classique. Cette option n’est disponible que si vous avez déjà configuré Dynamic Media Classic.

![chlimage_1-95](assets/chlimage_1-95.png)

**[!UICONTROL Configuration]** Si plusieurs configurations de Dynamic Media Classic sont définies en [!UICONTROL Cloud Services], vous pouvez les sélectionner ici. De ce fait, le dossier change selon la configuration que vous avez choisie.

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL Type]** de fichier Dans le navigateur Contenu multimédia dynamique classique, vous pouvez filtrer les résultats pour inclure les éléments suivants : images, modèles, vidéos et visionneuses de vidéos adaptatives. Si vous ne sélectionnez aucun type d’élément, AEM recherche par défaut tous les types d’élément.

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* Lors de la recherche de vidéos, vous recherchez un seul rendu. Les résultats renvoient le rendu d’origine (uniquement &amp;amp ; ast ; .mp4) et le rendu codé.
>* Lors de la recherche d’une visionneuse de vidéos adaptative, vous recherchez le dossier et tous les sous-dossiers, mais uniquement si vous avez ajouté un mot-clé à la recherche. Si vous n’avez pas ajouté de mot-clé, AEM ne recherche pas les sous-dossiers.

>



**[!UICONTROL Etat]** de publication Vous pouvez filtrer les fichiers en fonction de l’état de publication : [!UICONTROL Publié] ou [!UICONTROL non publié]. If you do not select any [!UICONTROL Publish status], AEM by default searches all publish statuses.

![chlimage_1-98](assets/chlimage_1-98.png)

