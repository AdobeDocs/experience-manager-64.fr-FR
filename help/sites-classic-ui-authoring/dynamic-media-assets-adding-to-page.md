---
title: Ajout de ressources Dynamic Media aux pages
seo-title: Adding Dynamic Media assets to pages
description: Pour ajouter la fonctionnalité Dynamic Media aux ressources que vous utilisez sur vos sites web, vous pouvez ajouter le composant Dynamic Media ou Interactive Media directement sur la page.
seo-description: To add the dynamic media functionality to assets you use on your websites, you can add the Dynamic Media or Interactive Media component directly on the page.
uuid: 650d0867-a079-4936-a466-55b7a30803a2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 331f4980-5193-4546-a22e-f27e38bb8250
exl-id: b498d54e-ff34-49a1-bfad-c6efbb6f75f4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1721'
ht-degree: 53%

---

# Ajout de ressources Dynamic Media aux pages{#adding-dynamic-media-assets-to-pages}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour ajouter la fonctionnalité Dynamic Media aux ressources que vous utilisez sur des sites Web, vous pouvez ajouter le composant **[!UICONTROL Dynamic Media]** ou **[!UICONTROL Interactive Media]** directement aux pages. Pour ce faire, saisissez [!UICONTROL Conception] et activation des composants dynamic media. Vous pouvez ensuite ajouter ces composants à la page et ajouter des ressources au composant. Les composants Dynamic Media et Interactive Media sont intelligents : ils savent si vous ajoutez une image ou une vidéo et les options disponibles changent en conséquence.

Vous ajoutez directement des ressources Dynamic Media à la page si vous utilisez AEM comme système de gestion de contenu web.

>[!NOTE]
>
>Les zones cliquables sont disponibles et prêtes à l’emploi pour les bannières de carrousel.

## Ajout d’un composant Dynamic Media à une page {#adding-a-dynamic-media-component-to-a-page}

L’ajout d’un composant [!UICONTROL Dynamic Media] ou [!UICONTROL Interactive Media] à une page suit le même processus que l’ajout d’un composant sur n’importe quelle page. Les composants [!UICONTROL Dynamic Media] et [!UICONTROL Interactive Media] sont décrits en détail dans les sections suivantes.

Pour ajouter un composant ou une visionneuse Dynamic Media à une page, procédez comme suit :

1. Dans AEM, ouvrez la page où vous souhaitez ajouter le composant Dynamic Media.
1. Si aucun composant Dynamic Media n’est disponible, cliquez sur la règle dans le [!UICONTROL Sidekick] pour entrer **[!UICONTROL Conception]** mode, cliquez sur **[!UICONTROL Modifier]** parsys, puis sélectionnez **[!UICONTROL Dynamic Media]** pour rendre les composants Dynamic Media disponibles.

   >[!NOTE]
   >
   >Pour plus d’informations, consultez [Configuration des composants en mode Création](/help/sites-authoring/default-components-designmode.md).

1. Retournez en mode d’**[!UICONTROL édition]** en cliquant sur l’icône représentant un crayon dans le [!UICONTROL sidekick].
1. Faites glisser le composant **[!UICONTROL Dynamic Media]** ou **[!UICONTROL Interactive Media]** du groupe **[!UICONTROL Autre]** du sidekick jusqu’à l’emplacement souhaité sur la page.
1. Cliquez sur **[!UICONTROL Modifier]** pour ouvrir le composant.
1. [Modifier le composant](#dynamic-media-component) Si nécessaire, cliquez sur **[!UICONTROL OK]** pour enregistrer les modifications.

## Composants Dynamic Media {#dynamic-media-components}

[!UICONTROL Dynamic Media] et [!UICONTROL Interactive Media] sont disponibles dans le **[!UICONTROL sidekick]** sous [!UICONTROL Dynamic Media]. Vous utilisez le composant **[!UICONTROL Interactive Media]** pour toutes les ressources interactives telles que du contenu vidéo interactif, des images interactives ou des ensembles de carrousels. Pour tous les autres composants Dynamic Media, utilisez la méthode **[!UICONTROL Dynamic Media]** composant.

![chlimage_1-71](assets/chlimage_1-71.png)

>[!NOTE]
>
>Ces composants ne sont pas disponibles par défaut et doivent être sélectionnés en mode de conception avant utilisation. [Une fois qu’elles sont disponibles en mode de conception](/help/sites-authoring/default-components-designmode.md), vous pouvez ajouter les composants à votre page comme vous le feriez pour tout autre composant AEM.

### Composant Dynamic Media {#dynamic-media-component}

Le composant Média dynamique est dynamique ; il propose des options différentes selon que vous ajoutez une image ou une vidéo. Le composant prend en charge les paramètres d’image prédéfinis, ainsi que les visionneuses d’images telles que les visionneuses d’images, les visionneuses à 360°, les visionneuses de médias mixtes et le contenu vidéo. En outre, la visionneuse est réactive. En d’autres termes, la taille de l’écran change automatiquement en fonction de la taille de l’écran. Toutes les visionneuses sont basées sur le HTML5.

>[!NOTE]
>
>Si vous ajoutez le composant [!UICONTROL Dynamic Media] et si les **[!UICONTROL Paramètres de Dynamic Media]** sont vides ou s’il est impossible d’ajouter correctement une ressource, vérifiez les points suivants :
>
>* Vous avez [enabled Dynamic Media](/help/assets/config-dynamic.md). Par défaut, Dynamic Media est désactivé.
>* L’image possède un fichier pyramid tiff. Les images importées avant l’activation de Dynamic Media ne comportent pas de fichier pyramid tiff.
>


#### En cas d’utilisation d’images {#when-working-with-images}

Le composant [!UICONTROL Dynamic Media] permet d’ajouter des images dynamiques, notamment des visionneuses d’images, à 360° et de supports variés. Vous pouvez effectuer un zoom avant et arrière, faire pivoter une image dans une visionneuse à 360° ou sélectionner une image dans un autre type de visionneuse.

Vous pouvez également configurer directement dans le composant les paramètres prédéfinis de la visionneuse ou de l’image ou le format de l’image. Pour rendre une image réactive, vous pouvez définir les points d’arrêt ou appliquer un paramètre d’image prédéfini réactif.

![chlimage_1-72](assets/chlimage_1-72.png)

Vous pouvez modifier les paramètres de Dynamic Media ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant, puis sur l’onglet **[!UICONTROL Paramètres de Dynamic Media]**.

![chlimage_1-73](assets/chlimage_1-73.png)

>[!NOTE]
>
>Par défaut, le composant d’image Dynamic Media est adaptatif. Si vous souhaitez faire en sorte qu’il ait une taille fixe, définissez-la dans le composant de l’onglet **[!UICONTROL Avancé]** à l’aide des propriétés **[!UICONTROL Largeur]** et **[!UICONTROL Hauteur]**.

**[!UICONTROL Paramètre prédéfini de la visionneuse]** - Sélectionnez un paramètre prédéfini de visionneuse existant dans le menu déroulant. Si le paramètre prédéfini de visionneuse que vous recherchez n’est pas visible, vous devrez le rendre visible. Consultez [Gestion des paramètres prédéfinis de visionneuse](/help/assets/managing-viewer-presets.md). Vous ne pouvez pas sélectionner de paramètre prédéfini de visionneuse si vous utilisez un paramètre d’image prédéfini et vice versa.

Il s’agit de la seule option disponible si vous affichez des visionneuses d’images, à 360° ou de supports variés. Les paramètres de visionneuse prédéfinis affichés sont également intelligents ; seuls les paramètres de visionneuse prédéfinis pertinents s’affichent.

**[!UICONTROL Paramètre d’image prédéfini]** - Sélectionnez un paramètre d’image prédéfini existant dans le menu déroulant. Si le paramètre d’image prédéfini que vous recherchez n’est pas visible, vous devrez le rendre visible. Consultez [Gestion des paramètres d’image prédéfinis](/help/assets/managing-image-presets.md). Vous ne pouvez pas sélectionner de paramètre prédéfini de visionneuse si vous utilisez un paramètre d’image prédéfini et vice versa.

Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de supports variés.

**[!UICONTROL Modificateurs d’image]** - Vous pouvez modifier les effets d’image en fournissant des commandes d’image supplémentaires. Elles sont décrites dans la section [Gestion des paramètres d’image prédéfinis](/help/assets/managing-viewer-presets.md) et le [Référence de commande](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=fr).

Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

**[!UICONTROL Points d’arrêt]** - Si vous utilisez cette ressource sur un site réactif, vous devez ajouter les points d’arrêt de page. Les points d’arrêt d’image doivent être séparés par des virgules (,). Cette option fonctionne lorsqu’il n’existe aucune valeur de hauteur ou largeur définie dans un paramètre d’image prédéfini.

Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

Vous pouvez modifier les [!UICONTROL paramètres avancés] ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant.

**[!UICONTROL Titre]** - Modifiez le titre de l’image.

**[!UICONTROL Texte de remplacement]** - Ajoutez un titre à l’image pour les utilisateurs pour lesquels les graphiques sont désactivés.

Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

**[!UICONTROL URL, Ouvrir dans]** - Vous pouvez définir une ressource à partir de pour ouvrir un lien. Définissez l’**[!UICONTROL URL]**, puis dans **[!UICONTROL Ouvrir dans]**, indiquez si vous souhaitez que la ressource s’ouvre dans la même fenêtre ou dans une nouvelle.

Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

**[!UICONTROL Largeur et hauteur]** - Saisissez une valeur en pixels si vous souhaitez que la taille de l’image soit fixe. Si vous ne fournissez pas de valeurs, la ressource devient adaptative.

#### En cas d’utilisation de vidéos {#when-working-with-video}

Le composant [!UICONTROL Dynamic Media] permet d’ajouter une vidéo dynamique à vos pages Web. Lorsque vous modifiez le composant, vous pouvez choisir d’utiliser un paramètre prédéfini de la visionneuse de vidéos pour lire la vidéo sur la page.

![chlimage_1-74](assets/chlimage_1-74.png)

Vous pouvez modifier les paramètres [!UICONTROL Dynamic Media] ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant.

>[!NOTE]
>
>Par défaut le composant vidéo Dynamic Media est adaptatif. Si vous souhaitez lui donner une taille fixe, définissez-la sous l’onglet **[!UICONTROL Avancé]** du composant, grâce aux options **[!UICONTROL Largeur]** et **[!UICONTROL Hauteur]**.

**[!UICONTROL Paramètre prédéfini de la visionneuse]** - Sélectionnez un paramètre prédéfini de visionneuse de vidéos existant dans le menu déroulant. Si le paramètre prédéfini de visionneuse que vous recherchez n’est pas visible, vous devrez le rendre visible. Consultez [Gestion des paramètres prédéfinis de visionneuse](/help/assets/managing-viewer-presets.md).

Vous pouvez modifier les paramètres [!UICONTROL avancés] ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant.

**[!UICONTROL Titre]** - Modifiez le titre de la vidéo.

**[!UICONTROL Largeur et hauteur]** - Saisissez une valeur en pixels si vous souhaitez que la taille de la vidéo soit fixe. Si vous ne fournissez pas de valeurs, la vidéo devient adaptative.

#### Comment diffuser une vidéo sécurisée {#how-to-delivery-secure-video}

Dans AEM 6.2, lors de l’installation [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480), vous pouvez contrôler si une vidéo est diffusée via une connexion SSL sécurisée (HTTPS) ou une connexion non sécurisée (HTTP). Par défaut, le protocole de diffusion vidéo est automatiquement hérité du protocole de la page web d’intégration. Si la page web est chargée via HTTPS, la vidéo est également diffusée via HTTPS. Et vice versa, si la page web est sur HTTP, la vidéo est diffusée sur HTTP. Dans la plupart des cas, ce comportement par défaut est correct et il n’est pas nécessaire d’apporter des modifications à la configuration. Cependant, vous pouvez remplacer ce comportement par défaut en ajoutant `VideoPlayer.ssl=on` à la fin d’un chemin d’URL ou à la liste d’autres paramètres de configuration de la visionneuse dans un fragment de code intégré, pour forcer la diffusion vidéo sécurisée.

Pour plus d’informations sur la diffusion sécurisée de vidéos et l’utilisation de l’attribut de configuration `VideoPlayer.ssl` dans le chemin d’accès URL, consultez [Diffusion sécurisée de vidéos](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html?lang=fr) dans le Guide de référence des visionneuses. Outre la visionneuse vidéo, la diffusion sécurisée de vidéos est disponible pour la visionneuse de médias mixtes et la visionneuse de vidéos interactives.

### Composant Média interactif {#interactive-media-component}

Le composant Interactive Media est destiné aux ressources qui comportent de l’interactivité sur ces zones réactives ou zones cliquables. Si vous disposez d’une image interactive, d’une vidéo interactive ou d’une bannière de carrousel, utilisez la variable **[!UICONTROL Média interactif]** composant.

Le composant [!UICONTROL Interactive Media] est dynamique : il propose des options différentes selon que vous ajoutez une image ou une vidéo. En outre, la visionneuse est réactive. En d’autres termes, la taille de l’écran change automatiquement en fonction de la taille de l’écran. Toutes les visionneuses sont basées sur le HTML5.

![chlimage_1-75](assets/chlimage_1-75.png)

Vous pouvez modifier les paramètres **[!UICONTROL Général]** ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant.

**[!UICONTROL Paramètre prédéfini de la visionneuse]** - Sélectionnez un paramètre prédéfini de visionneuse existant dans le menu déroulant. Si le paramètre prédéfini de visionneuse que vous recherchez n’est pas visible, vous devrez le rendre visible. Les paramètres de visionneuse prédéfinis doivent être publiés avant de pouvoir être utilisés. Voir Gestion des paramètres prédéfinis de visionneuse.

**[!UICONTROL Titre]** - Modifiez le titre de la vidéo.

**[!UICONTROL Largeur et hauteur]** - Saisissez une valeur en pixels si vous souhaitez que la taille de la vidéo soit fixe. Si vous ne fournissez pas de valeurs, la vidéo devient adaptative.

Vous pouvez modifier les paramètres **[!UICONTROL Ajouter au panier]** ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant.

**[!UICONTROL Afficher la ressource de produit]** - Par défaut, cette valeur est sélectionnée. La ressource de produit affiche une image du produit telle que définie dans le module Commerce. Décochez la case pour ne pas afficher la ressource de produit.

**[!UICONTROL Afficher le prix du produit]** - Par défaut, cette valeur est sélectionnée. Le prix du produit affiche le prix de l’article tel que défini dans le module Commerce. Décochez la case pour ne pas afficher le prix du produit.

**[!UICONTROL Afficher le formulaire de produit]** - Par défaut, cette valeur n’est pas sélectionnée. Le formulaire de produit comprend toutes les variantes de produit, telles que la taille et la couleur. Décochez la case pour ne pas afficher les variantes de produit.
