---
title: Ajout de ressources Dynamic Media aux pages
seo-title: Ajout de ressources Dynamic Media aux pages
description: Comment ajouter des composants Dynamic Media à une page dans AEM
seo-description: Comment ajouter des composants Dynamic Media à une page dans AEM
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
exl-id: bb97b649-a50d-49c8-97aa-18c32f18d527
feature: Composants
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '2826'
ht-degree: 62%

---

# Ajout de ressources Dynamic Media aux pages {#adding-dynamic-media-assets-to-pages}

Pour ajouter la fonctionnalité Dynamic Media aux ressources que vous utilisez sur vos sites web, vous pouvez ajouter le composant **Dynamic Media** ou **Interactive Media** directement sur la page. Pour ce faire, vous devez activer le mode Mise en page et activer les composants Dynamic Media. Vous pouvez ensuite ajouter ces composants à la page et ajouter des ressources au composant. Les composants Dynamic Media et Interactive Media sont dynamiques : ils détectent si vous ajoutez une image ou une vidéo et les options disponibles changent en conséquence.

Vous ajoutez directement des ressources Dynamic Media à la page si vous utilisez AEM comme système de gestion de contenu web. Si vous faites appel à un tiers pour votre gestion de contenu web, [liez](linking-urls-to-yourwebapplication.md) ou [incorporez](embed-code.md) vos ressources. Pour un site web tiers réactif, reportez-vous à la section [Diffusion d’images optimisées sur un site réactif](responsive-site.md).

>[!NOTE]
>
>Vous devez publier les ressources avant de les ajouter aux pages d’AEM. Voir [Publication de ressources Dynamic Media](publishing-dynamicmedia-assets.md).

## Ajout d’un composant Dynamic Media à une page  {#adding-a-dynamic-media-component-to-a-page}

L’ajout d’un composant Dynamic Media à une page est identique à l’ajout d’un composant à n’importe quelle page. Les composants Dynamic Media sont décrits en détail dans les sections suivantes.

>[!NOTE]
>
>Si une page web contient un composant Dynamic Media accessible par un utilisateur disposant d’autorisations en lecture seule, les sauts de page et les composants ne sont pas correctement rendus. Cela est dû au fait que la page est reconstruite pour s’assurer que les propriétés des composants sont correctes et que toutes les ressources et configurations référencées sont accessibles. La page est alors rendue à nouveau, provoquant la coupure des composants. le code de composant respectif sur la page ne peut pas être rendu à nouveau en raison de l’accès en lecture seule de l’utilisateur.
>  
>Pour éviter ce problème, assurez-vous que les utilisateurs d’AEM Sites disposent des autorisations nécessaires pour accéder aux ressources.

1. Dans AEM, ouvrez la page où vous souhaitez ajouter le composant Dynamic Media.
1. Dans le panneau situé à gauche de la page (vous devrez peut-être activer/désactiver l’affichage du panneau latéral), cliquez sur l’icône **[!UICONTROL Composants]** .
1. Sous l’en-tête **[!UICONTROL Composants]**, dans la liste déroulante, sélectionnez **[!UICONTROL Dynamic Media]**. Si aucune liste de composants Dynamic Media n’est disponible, vous devrez probablement activer ceux que vous souhaitez utiliser. Voir [Activation des composants Dynamic Media](#enabling-dynamic-media-components).

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. Faites glisser un composant Dynamic Media que vous souhaitez utiliser sur la page à l’emplacement souhaité.
1. Placez le pointeur de la souris directement sur le composant. Lorsque le composant est entouré d’une zone bleue, appuyez une fois pour afficher la barre d’outils du composant. Appuyez sur l’icône **** Configuration (clé à molette).
1. [Modifiez les ](#dynamic-media-components) composants selon les besoins et cliquez sur la coche pour enregistrer les modifications.

### Activation des composants Dynamic Media {#enabling-dynamic-media-components}

Si aucun composant Dynamic Media n’est disponible pour ajouter une page, cela signifie probablement que vous devez d’abord activer les composants que vous souhaitez utiliser.

1. Dans AEM, ouvrez la page où vous souhaitez ajouter le composant Dynamic Media.
1. Dans la partie gauche de la barre d’outils située en haut de la page, appuyez sur l’icône Informations de la page, puis sur **[!UICONTROL Modifier le modèle]** dans la liste déroulante.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Dans la liste déroulante située sur le côté droit de la barre d’outils, à proximité du haut de la page, appuyez sur **[!UICONTROL Structure]**.

   ![Stratégie](/help/assets/assets-dm/structure-mode.png)

1. À proximité du bas de la page, appuyez sur **[!UICONTROL Conteneur de mises en page]** pour ouvrir sa barre d’outils, puis appuyez sur l’icône Stratégie.
1. Sur la page **[!UICONTROL Conteneur de mises en page]**, sous l’en-tête **[!UICONTROL Propriétés]**, assurez-vous que l’onglet **[!UICONTROL Composants autorisés]** est sélectionné.

   ![Composants autorisés](/help/assets/assets-dm/allowed-components.png)

1. Faites défiler l’écran jusqu’à ce que vous voyiez **[!UICONTROL Média dynamique]**.
1. Appuyez sur l’icône > située à gauche de **[!UICONTROL Média dynamique]** pour développer la liste, puis sélectionnez les composants Dynamic Media à activer.

   ![Liste de composants Dynamic Media](/help/assets/assets-dm/dm-components-select.png)

1. À proximité de l’angle supérieur droit de la page **[!UICONTROL Conteneur de mises en page]**, appuyez sur l’icône Terminé (coche).

1. Dans la liste déroulante située sur le côté droit de la barre d’outils, en haut de la page, appuyez sur **[!UICONTROL Contenu initial]**, puis [ajoutez un composant Dynamic Media à une page](#adding-a-dynamic-media-component-to-a-page) comme vous le faites habituellement.

## Localisation des composants Dynamic Media {#localizing-dynamic-media-components}

Vous pouvez rechercher les composants Dynamic Media de deux façons :

* Dans une page web de Sites, ouvrez **[!UICONTROL Propriétés]** et sélectionnez l’onglet **[!UICONTROL Avancé]**. Choisissez la langue souhaitée pour la localisation.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* Depuis le sélecteur de site, sélectionnez la page ou le groupe de pages souhaité. Appuyez sur **[!UICONTROL Propriétés]** et sélectionnez l’onglet **[!UICONTROL Avancé]**. Choisissez la langue souhaitée pour la localisation.

   >[!NOTE]
   >
   >Notez que toutes les langues disponibles dans le menu **[!UICONTROL Langue]** ne sont pas actuellement associées à des jetons.

## Composants Dynamic Media {#dynamic-media-components}

Dynamic Media et Interactive Media sont disponibles sous l’onglet [!UICONTROL Dynamic Media] dans [!UICONTROL Composants]. Vous utilisez le composant [!UICONTROL Interactive Media] pour toutes les ressources interactives telles que du contenu vidéo interactif, des images interactives ou des ensembles de carrousels. Pour tous les autres composants Dynamic Media, utilisez le composant Dynamic Media.

>[!NOTE]
>
>Ces composants ne sont pas disponibles par défaut et doivent être rendus disponibles via l’éditeur de modèles avant utilisation. [Une fois les composants disponibles dans l’éditeur de modèles, vous pouvez les ajouter à votre page comme vous le feriez avec tout autre composant AEM.](/help/sites-authoring/templates.md#editing-templates-template-authors)

![chlimage_1-539](assets/chlimage_1-539.png)

### Composant Dynamic Media {#dynamic-media-component}

Le composant Dynamic Media est dynamique. Il propose différentes options selon que vous ajoutez une image ou une vidéo. Le composant prend en charge les paramètres d’image prédéfinis, ainsi que les visionneuses d’images telles que les visionneuses d’images, les visionneuses à 360°, les visionneuses de médias mixtes et le contenu vidéo. En outre, la visionneuse est réactive. En d’autres termes, la taille de l’écran change automatiquement en fonction de la taille de l’écran. Toutes les visionneuses sont des visionneuses HTML5.

>[!NOTE]
>
>S’il existe un composant Dynamic Media, un composant Interactive Media ou les deux sur une page web accessible par un utilisateur disposant d’autorisations de lecture seule, les sauts de page et le rendu des composants ne sont pas corrects. Cela est dû au fait que la page est reconstruite pour s’assurer que les propriétés des composants sont correctes et que toutes les ressources et configurations référencées sont accessibles. La page est alors rendue à nouveau, provoquant la coupure des composants. le code de composant respectif sur la page ne peut pas être rendu à nouveau en raison de l’accès en lecture seule de l’utilisateur.
>  
>Pour éviter ce problème, assurez-vous que les utilisateurs d’AEM Sites disposent des autorisations nécessaires pour accéder aux ressources.

>[!NOTE]
>
>Si vous ajoutez le composant Média dynamique et si l’option **[!UICONTROL Paramètres de média dynamique]** est vide ou s’il est impossible d’ajouter correctement une ressource, vérifiez les points suivants :
>
>* Vous avez [activé Dynamic Media](config-dynamic.md). Par défaut, ce module complémentaire est désactivé.
>* L’image possède un fichier pyramid tiff. Les images importées avant l’activation de Dynamic Media ne possèdent pas de fichier pyramid tiff.

>



#### En cas d’utilisation d’images {#when-working-with-images}

Le composant Média dynamique permet d’ajouter des images dynamiques, notamment des visionneuses d’images, à 360 ° et de supports variés. Vous pouvez effectuer un zoom avant et arrière, faire pivoter une image dans une visionneuse à 360° ou sélectionner une image dans un autre type de visionneuse.

Vous pouvez également configurer directement dans le composant les paramètres prédéfinis de la visionneuse ou de l’image ou le format de l’image. Pour rendre une image réactive, vous pouvez définir les points d’arrêt ou appliquer un paramètre prédéfini d’image réactive.

Vous devez modifier les paramètres Dynamic Media suivants en cliquant sur l’icône **[!UICONTROL Modifier]** dans le composant, puis sur **[!UICONTROL Paramètres Dynamic Media]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Par défaut, le composant d’image Dynamic Media est adaptatif. Si vous souhaitez lui donner une taille fixe, définissez-la dans le composant de l’onglet **[!UICONTROL Avancé]** avec les paramètres **[!UICONTROL Largeur]** et **[!UICONTROL Hauteur]** .

* **[!UICONTROL Paramètre]**
prédéfini de la visionneuse : sélectionnez un paramètre prédéfini de visionneuse existant. Si le paramètre prédéfini de visionneuse que vous recherchez n’est pas visible, vous devrez le rendre visible. Voir Gestion des paramètres prédéfinis de visionneuse. Si vous utilisez un paramètre prédéfini d’image, vous ne pouvez pas sélectionner de paramètre prédéfini de visionneuse, et inversement.
Il s’agit de la seule option disponible si vous affichez des visionneuses d’images, à 360° ou de supports variés. Les paramètres prédéfinis de visionneuse sont également dynamiques : seuls les paramètres pertinents s’affichent.

* **[!UICONTROL Les]**
modificateurs de visionneuse prennent la forme d’une paire nom=valeur avec un délimiteur &amp; et permettent de modifier les visionneuses comme indiqué dans le Guide de référence des visionneuses. Un exemple de modificateur de visionneuse est posterimage=img.jpg&amp;caption=text.vtt,1 qui définit une image différente pour la miniature de la vidéo et associe un fichier de sous-titre/sous-titre à la vidéo.

* **[!UICONTROL Paramètre d’image]**
prédéfini : sélectionnez un paramètre d’image prédéfini existant. Si le paramètre d’image prédéfini que vous recherchez n’est pas visible, vous devrez le rendre visible. Voir Gestion des paramètres d’image prédéfinis. Si vous utilisez un paramètre prédéfini d’image, vous ne pouvez pas sélectionner de paramètre prédéfini de visionneuse, et inversement.
Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

* **[!UICONTROL Modificateurs d’image]**
: vous pouvez appliquer des effets d’image en fournissant des commandes d’image supplémentaires. Ces commandes sont décrites dans la section Paramètres prédéfinis d’image et dans le guide de référence des commandes relatives aux images.
Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

* ****
Points d’arrêt : si vous utilisez cette ressource sur un site réactif, vous devez ajouter les points d’arrêt d’image. Les points d’arrêt d’image doivent être séparés par des virgules (,). Cette option fonctionne lorsqu’il n’existe aucune valeur de hauteur ou largeur définie dans un paramètre d’image prédéfini.
Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.
Vous pouvez modifier les paramètres avancés ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant.

* ****
TitreModifiez le titre de l’image.

* **[!UICONTROL Alt]**
TexteAjoutez un titre à l’image pour les utilisateurs pour lesquels les graphiques sont désactivés.
Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

* **[!UICONTROL URL, Ouvrir]**
dans Vous pouvez définir une ressource pour ouvrir un lien. Définissez l’URL, puis dans le champ Ouvrir dans, indiquez si vous souhaitez l’ouvrir dans la même fenêtre ou une nouvelle fenêtre.
Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

* **** Largeur et  ****
hauteurSaisissez une valeur en pixels si vous souhaitez que la taille de l’image soit fixe. Si vous ne fournissez pas de valeurs, la ressource devient adaptative.

#### En cas d’utilisation de vidéos {#when-working-with-video}

Le composant Média dynamique permet d’ajouter une vidéo dynamique à vos pages web. Lorsque vous modifiez le composant, vous pouvez choisir d’utiliser un paramètre prédéfini de la visionneuse de vidéos pour lire la vidéo sur la page.

![chlimage_1-540](assets/chlimage_1-540.png)

Vous devez modifier les paramètres Dynamic Media suivants en cliquant sur **[!UICONTROL Modifier]** dans le composant.

>[!NOTE]
>
>Par défaut le composant vidéo Dynamic Media est adaptatif. Si vous souhaitez lui donner une taille fixe, définissez-la sous l’onglet **[!UICONTROL Avancé]** du composant, grâce aux options **[!UICONTROL Largeur]** et [!UICONTROL Hauteur].

* **[!UICONTROL Paramètre]**
prédéfini de la visionneuse : sélectionnez un paramètre prédéfini de visionneuse existant. Si le paramètre prédéfini de visionneuse que vous recherchez n’est pas visible, vous devrez le rendre visible. Voir Gestion des paramètres prédéfinis de visionneuse.

* **[!UICONTROL Les]**
modificateurs de visionneuse prennent la forme d’une paire nom=valeur avec un délimiteur &amp; et permettent de modifier les visionneuses comme indiqué dans le Guide de référence des visionneuses d’Adobe. Un exemple de modificateur de visionneuse est posterimage=img.jpg&amp;caption=text.vtt,1

   Avec les modificateurs de visionneuse, par exemple, vous pouvez effectuer les opérations suivantes :

   * Associez un fichier de sous-titres à une [légende vidéo.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html?lang=fr)
   * Associez un fichier de navigation à une [navigation vidéo.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html?lang=fr)

Vous pouvez modifier les [!UICONTROL Paramètres avancés] suivants en cliquant sur **[!UICONTROL Modifier]** dans le composant.

* ****
TitreModifiez le titre de la vidéo.

* **** Largeur et  ****
HauteurSaisissez une valeur en pixels si vous souhaitez que la vidéo ait une taille fixe. Si vous ne fournissez pas de valeurs, la vidéo devient adaptative.

#### Lorsque vous utilisez le recadrage intelligent {#when-working-with-smart-crop}

Utilisez le composant Média dynamique pour ajouter des ressources d’images avec recadrage intelligent à vos pages web. Lorsque vous modifiez le composant, vous pouvez choisir d’utiliser un paramètre prédéfini de la visionneuse de vidéos pour lire la vidéo sur la page.

Voir aussi [Profils d’image](image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

Vous pouvez modifier les [!UICONTROL paramètres Dynamic Media] suivants en cliquant sur **[!UICONTROL Modifier]** dans le composant.

>[!NOTE]
>
>Par défaut, le composant d’image Dynamic Media est adaptatif. Si vous souhaitez faire en sorte qu’il ait une taille fixe, définissez-la dans le composant de l’onglet [!UICONTROL Avancé] à l’aide des options **[!UICONTROL Largeur]** et **[!UICONTROL Hauteur]**.

* **[!UICONTROL Modificateurs d’image]**
: vous pouvez appliquer des effets d’image en fournissant des commandes d’image supplémentaires. Ces commandes sont décrites dans la section Paramètres prédéfinis d’image et dans le guide de référence des commandes relatives aux images.
Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

Vous pouvez modifier les paramètres **[!UICONTROL avancés]** suivants en cliquant sur **[!UICONTROL Modifier]** dans le composant.

* ****
TitreModifiez le titre de l’image avec recadrage intelligent.

* **[!UICONTROL Alt]**
Text Ajoutez un titre à l’image de recadrage intelligent pour les utilisateurs pour lesquels les graphiques sont désactivés.
Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

* **[!UICONTROL URL, Ouvrir]**
dans Vous pouvez définir une ressource pour ouvrir un lien. Définissez l’URL, puis dans le champ Ouvrir dans, indiquez si vous souhaitez l’ouvrir dans la même fenêtre ou une nouvelle fenêtre.
Cette option n’est pas disponible si vous affichez des visionneuses d’images, à 360° ou de médias mixtes.

* **** Hauteur et  ****
LargeurSaisissez une valeur en pixels si vous souhaitez que la taille de l’image de recadrage intelligent soit fixe. Si vous ne fournissez pas de valeurs, la vidéo devient adaptative.

### Composant Interactive Media {#interactive-media-component}

Le composant Interactive Media est destiné aux ressources présentant des éléments interactifs tels que des zones réactives ou des zones cliquables. Si vous disposez d’une image interactive, d’une vidéo interactive ou d’une bannière de carrousel, utilisez le composant Interactive Media.

Le composant Interactive Media est dynamique. Il propose différentes options selon que vous ajoutez une image ou une vidéo. En outre, la visionneuse est réactive : la taille de l’écran change automatiquement en fonction de la taille d’écran. Toutes les visionneuses sont des visionneuses HTML5.

>[!NOTE]
>
>S’il existe un composant Dynamic Media, un composant Interactive Media ou les deux sur une page web accessible par un utilisateur disposant d’autorisations de lecture seule, les sauts de page et le rendu des composants ne sont pas corrects. Cela est dû au fait que la page est reconstruite pour s’assurer que les propriétés des composants sont correctes et que toutes les ressources et configurations référencées sont accessibles. La page est alors rendue à nouveau, provoquant la coupure des composants. le code de composant respectif sur la page ne peut pas être rendu à nouveau en raison de l’accès en lecture seule de l’utilisateur.
> 
>Pour éviter ce problème, assurez-vous que les utilisateurs d’AEM Sites disposent des autorisations nécessaires pour accéder aux ressources.

![chlimage_1-541](assets/chlimage_1-541.png)

Vous pouvez modifier les paramètres **[!UICONTROL Général]** ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant.

* **[!UICONTROL Paramètre]**
prédéfini de la visionneuse : sélectionnez un paramètre prédéfini de visionneuse existant. Si le paramètre prédéfini de visionneuse que vous recherchez n’est pas visible, vous devrez le rendre visible. Les paramètres de visionneuse prédéfinis doivent être publiés avant de pouvoir être utilisés. Voir Gestion des paramètres prédéfinis de visionneuse.

* ****
TitreModifiez le titre de la vidéo.

* **** Largeur et  ****
HauteurSaisissez une valeur en pixels si vous souhaitez que la vidéo ait une taille fixe. Si vous ne fournissez pas de valeurs, la vidéo devient adaptative.

Vous pouvez modifier les paramètres **[!UICONTROL Ajouter au panier]** ci-après en cliquant sur **[!UICONTROL Modifier]** dans le composant.

* **[!UICONTROL Afficher la]**
ressource de produit Par défaut, cette valeur est sélectionnée. La ressource de produit affiche une image du produit telle que définie dans le module Commerce. Désactivez la case pour ne pas afficher la ressource de produit.

* **[!UICONTROL Afficher le]**
prix des produits Par défaut, cette valeur est sélectionnée. Le prix du produit affiche le prix de l’élément tel qu’il est défini dans le module Commerce. Désactivez la case pour ne pas afficher le prix du produit.

* **[!UICONTROL Afficher le]**
formulaire du produit Par défaut, cette valeur n’est pas sélectionnée. Le formulaire de produit contient toutes les variantes de produit, telles que la taille et la couleur. Désactivez la case pour ne pas afficher les variantes de produit.

### Composant Média panoramique {#panoramic-media-component}

Le composant de média panoramique est destiné aux ressources qui sont des images panoramiques sphériques. Ces images fournissent une expérience d’affichage à 360° d’une pièce, d’une propriété, d’un lieu ou d’un paysage. Pour qu’une image soit un panorama sphérique, elle doit posséder l’une ou l’autre des propriétés suivantes, ou les deux :

* Un rapport d’aspect de 2:1.
* Balisée avec les mots-clés « équirectangulaire » ou (« sphérique » + « panorama ») ou (« sphérique » + « panoramique »). Voir [Utilisation des balises](/help/sites-authoring/tags.md).

Les critères de rapport d’aspect et de mots-clés s’appliquent tous deux aux ressources panoramiques pour la page des détails des ressources et le composant WCM « médias panoramiques ».

![panoramic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

Vous pouvez modifier le paramètre suivant en appuyant sur **[!UICONTROL Modifier]** dans le composant.

* **[!UICONTROL Paramètre]**
prédéfini de la visionneuse : sélectionnez une visionneuse existante dans le menu déroulant Paramètre prédéfini de la visionneuse.

Si le paramètre prédéfini de la visionneuse que vous recherchez n’est pas visible, vérifiez qu’il est publié. Vous devez publier les paramètres prédéfinis de la visionneuse avant que vous puissiez les utiliser. Voir [Gestion des paramètres prédéfinis de visionneuse](managing-viewer-presets.md).

### Utilisation de HTTP/2 pour la diffusion de ressources Dynamic Media {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 est le nouveau protocole web mis à jour qui améliore le mode de communication entre les navigateurs et les serveurs. Il permet un transfert rapide d’informations et réduit la puissance de traitement nécessaire. Les ressources Dynamic Media peuvent désormais être diffusées sur HTTP/2, un protocole qui garantit de meilleurs temps de réponse et de chargement.

Voir [Diffusion du contenu sur HTTP2](http2.md) pour tout savoir sur l’utilisation du protocole HTTP/2 avec votre compte Dynamic Media.

>[!MORELIKETHIS]
>
>* [Explication de la gestion des couleurs avec AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [Utilisation de miniatures vidéo personnalisées avec AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Présentation de la visionneuse d’éléments avec AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [Utilisation de la vidéo interactive avec AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [Utilisation du lecteur vidéo dans AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [Utilisation de l’accentuation d’image avec AEM Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

