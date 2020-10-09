---
title: Images interactives
seo-title: Images interactives
description: Découvrir comment utiliser les images interactives dans les médias dynamiques
seo-description: Découvrir comment utiliser les images interactives dans les médias dynamiques
uuid: e8f79bc1-fccb-48d0-aca1-7f319c595fe9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d630499d-740d-4979-8a34-9e3fcc3b5a23
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '4300'
ht-degree: 79%

---


# Images interactives {#interactive-images}

Vous pouvez facilement rendre les images statiques riches et attrayantes pour les clients en faisant glisser et en déplaçant des zones réactives &quot;susceptibles d’être visitées&quot; sur une image. Les points d&#39;accès disponibles dans les magasins combinent des informations supplémentaires sur un produit ou un service avec une fonctionnalité directe, au point de vente, &quot;Ajouter au panier&quot; ou &quot;Acheter&quot;. Les clients peuvent appuyer sur ces zones réactives et être directement liés au produit ou au service, l’ajouter à un panier ou être liés à une page Web. Les expériences directes de ce type augmentent l’engagement et la conversion des clients sur votre site Web.

Voici une bannière publicitaire avec une fenêtre contextuelle d’aperçu rapide. L’utilisateur active l’aperçu rapide en appuyant sur le cercle ou la « zone réactive » du modèle.

![chlimage_1-368](assets/chlimage_1-368.png)

Voir les images interactives en action sur la page web ci-dessus en visitant la page :

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## Découvrir comment les bannières d’images interactives sont créées {#watch-how-interactive-image-banners-are-created}

Visionnez une présentation vidéo de 10 minutes et 33 secondes sur la [création de bannières d’images interactives](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Vous apprendrez également à prévisualiser, modifier et diffuser des bannières d’images interactives.

## Démarrage rapide : images interactives {#quick-start-interactive-images}

La description suivante du workflow étape par étape est conçue pour vous aider à mettre en route rapidement les images interactives dans AEM Assets.

Recherchez le titre **Exemple** dans certaines tâches de démarrage rapide. Il contient un court tutoriel reposant sur l’exemple de page web suivant qui ne contient pas encore d’images interactives :

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

Le tutoriel permet d’illustrer les étapes d’intégration d’images interactives à votre site web.

**Flux** d’images interactives :

1. **(Facultatif) Identification des variables de zone réactive** : si vous utilisez des instances autonomes d’AEM Assets et de Dynamic Media, commencez par identifier les variables dynamiques utilisées dans votre aperçu rapide existant afin de pouvoir entrer les données de zone réactive lors de la création de l’image interactive. Voir [(Facultatif) Identification des variables de zone réactive](#optional-identifying-hotspot-variables).

   Cependant, si vous utilisez AEM Sites ou AEM eCommerce, ou les deux, cette étape n’est pas nécessaire.

   Reportez-vous à la section [Concepts de commerce électronique dans AEM Assets](/help/sites-administering/concepts.md).

1. **(Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives**. Personnalisez l’image utilisée pour représenter des zones réactives. Vous n’avez pas besoin de créer votre propre paramètre prédéfini de visionneuse d’images interactives si vous envisagez plutôt d’utiliser le paramètre prédéfini de visionneuse d’images interactives prêt à l’emploi `Shoppable_Banner`.


   Voir [(Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives](managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Téléchargement d&#39;une bannière** d&#39;image - Téléchargez les bannières d&#39;image que vous souhaitez rendre interactives.

   See [Uploading an image banner](#uploading-an-image-banner).

1. **ajouter des zones réactives à une bannière** d’image : Ajoutez une ou plusieurs zones réactives à une bannière d’image et associez-les à une action telle qu’un hyperlien, une vue rapide ou un fragment d’expérience. Après avoir ajouté des zones réactives, vous terminez cette tâche en publiant l’image interactive.

   * Voir [Ajout de zones réactives à une bannière d’image](#adding-hotspots-to-an-image-banner).
   * Voir [Prévisualisation d’images interactives](#optional-previewing-interactive-images) – Facultatif. Si vous le souhaitez, vous pouvez afficher une représentation de votre bannière Shoppable et tester son interactivité.
   * Voir [Publication de ressources](publishing-dynamicmedia-assets.md) pour obtenir des informations sur la publication de ressources d’images interactives.

1. **ajouter une image interactive à votre site Web ou à votre site Web en AEM**

   * Si vous utilisez AEM Sites, ou AEM eCommerce, ou les deux, vous pouvez ajouter l’image interactive directement à une page Web dans AEM en faisant glisser le composant Interactive Media sur la page. Reportez-vous à la section [Ajout de ressources Dynamic Media aux pages](adding-dynamic-media-assets-to-pages.md).
   * Si vous utilisez des instances autonomes d’AEM Assets et de Dynamic Media, vous devez copier le code intégré sur votre site web, puis l’intégrer à votre aperçu rapide existant. Voir [Intégration d’une image interactive à votre site web](#integrating-an-interactive-image-with-your-website).
   * Si vous utilisez un gestionnaire de contenu web (WCM) tiers, vous devez intégrer la nouvelle vidéo interactive à l’aperçu rapide existant utilisé sur votre site web. Reportez-vous à la section [Intégration d’une image interactive dans un aperçu rapide existant](#integrating-an-interactive-image-with-an-existing-quickview).

## (Facultatif) Identification des variables de zone réactive {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Cette tâche n’est nécessaire que si les conditions ci-dessous sont vraies :
>
>* Vous souhaitez ajouter de l’interactivité à votre image en déclenchant des aperçus rapides.
>* Votre mise en œuvre d’AEM n’utilise *pas* de framework d’intégration de commerce électronique pour extraire des données de produit dans AEM à partir d’une solution de commerce électronique, comme IBM WebSphere Commerce, Elastic Path, Hybris ou Intershop. Reportez-vous à la section [Concepts de commerce électronique dans AEM Assets](/help/sites-administering/concepts.md).
>
>
>Si votre mise en œuvre d’AEM utilise eCommerce, vous pouvez ignorer cette tâche et passer à la tâche suivante.

Commencez par identifier les variables dynamiques utilisées par votre mise en œuvre de l’aperçu rapide existant afin de pouvoir entrer les données de zone réactive pour créer l’image interactive.

Lorsque vous ajoutez des zones réactives à une image de bannière dans AEM Assets, vous devez affecter un SKU (unité de gestion des stocks ; un identifiant unique pour chaque produit ou service distinct que vous fournissez) et des variables supplémentaires facultatives à chaque zone réactive. Ces variables de zones réactives sont utilisées ultérieurement pour faire corresponde des zones réactives avec du contenu d’aperçu rapide.

Il est important d’identifier correctement le nombre et le type de variables à associer aux données de zone réactive. Chaque zone réactive ajoutée à une image de bannière doit comporter suffisamment d’informations pour identifier clairement le produit sur le système principal existant.

Il existe différentes manières d’identifier un jeu de variables à utiliser pour les données des zones réactives.

Il peut parfois être nécessaire de consulter les spécialistes informatiques responsables de l’implémentation d’aperçu rapide existante, car ils connaissent probablement le jeu minimum de données nécessaires pour identifier l’aperçu rapide dans le système. Cependant, dans la plupart des cas, il est également possible d’analyser le comportement existant du code frontal.

La majorité des implémentations d’aperçu rapide utilisent le paradigme suivant :

* L’utilisateur active un élément d’interface utilisateur sur le site web. For example, clicking a **[!UICONTROL Quickview]** button.
* Le site web envoie une demande Ajax au serveur principal afin de charger les données ou le contenu de l’aperçu rapide, le cas échéant.
* Les données de l’aperçu rapide sont traduites en contenu en préparation du rendu sur la page web.
* Enfin, le code frontal effectue le rendu visuel de ce contenu à l’écran.

L’approche consiste alors à visiter différentes zones du site web existant où la fonctionnalité d’aperçu rapide est implémentée, à déclencher l’aperçu rapide et à capturer l’URL Ajax envoyée par la page web pour charger les données ou le contenu de l’aperçu rapide.

Normalement, il n’est pas nécessaire d’utiliser des outils de débogage spécialisés. Les navigateurs web modernes incluent des inspecteurs web qui font un travail correct. Vous trouverez ci-dessous quelques exemples de navigateurs web qui incluent des inspecteurs web :

* To see all outgoing HTTP requests in Google Chrome, press F12 to open the **[!UICONTROL Developer Tools]** panel, and then click the **[!UICONTROL Network]** tab.

   On a Mac, press **[!UICONTROL Command+Option+I]** to open the **[!UICONTROL Developer Tools]** panel, then click the Network tab.

* In Firefox, you can either activate the Firebug plug-in by pressing F12 and use its Net tab, or you can use the built-in **[!UICONTROL Inspector]** tool and its **[!UICONTROL Network]** tab.

   On a Mac, press **[!UICONTROL Command+Option+I]** to open the **[!UICONTROL Developer Tools]** panel, then click the **[!UICONTROL Inspector]** tab.

Lorsque la surveillance de réseau est activée dans le navigateur, déclenchez l’aperçu rapide sur la page.

Vous trouvez maintenant l’URL Ajax d’aperçu rapide dans le journal réseau. Copiez l’URL enregistrée pour l’analyse ultérieure. Dans la plupart des cas, lorsque vous déclenchez l’aperçu rapide, plusieurs requêtes sont envoyées au serveur. En règle générale, l’URL Ajax d’aperçu rapide est l’une des premières dans la liste. Elle possède une partie de chaîne de requête complexe ou un chemin d’accès, et son type de réponse MIME est `text/html`, `text/xml` ou `text/javascript`.

Au cours de ce processus, il est important de parcourir différentes zones de votre site web, avec différentes catégories et types de produits. C’est pourquoi les URL d’aperçu rapide peuvent avoir des parties communes pour une catégorie de site web donnée, mais ne changent que si vous visitez une autre zone du site web.

Dans le cas le plus simple, la seule partie variable dans l’URL de l’aperçu rapide est le SKU du produit. Dans ce cas, la valeur du SKU est la seule donnée dont vous avez besoin pour ajouter des zones réactives à l’image de bannière.

Cependant, dans les cas complexes, l’URL d’aperçu rapide comporte différents éléments variables en complément du SKU, comme l’identifiant de la catégorie, le code couleur, le code taille, etc. Dans ce cas, chaque élément est une variable distincte dans votre définition de données d’images interactives dans la fonction d’image interactive publicitaire d’AEM Assets.

Consultez les exemples suivants d’URL d’aperçu rapide et les variables de zones réactives résultantes :

<table> 
     <tbody> 
      <tr> 
       <td><p>SKU unique, trouvé dans la chaîne de requête.</p> </td> 
       <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p> 
        <ul> 
         <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
        </ul> <p>La seule partie variable de l’URL est la valeur du paramètre de chaîne de requête productId=. Il s’agit clairement de la valeur d’une unité de gestion des stocks (SKU). Par conséquent, nos zones réactives ne nécessitent que des champs de SKU renseignés avec des valeurs comme <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong> et <strong><code>1898294</code></strong>.</p> </td> 
      </tr> 
      <tr> 
       <td><p>SKU unique, trouvé dans le chemin d’accès à l’URL.</p> </td> 
       <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p> 
        <ul> 
         <li><p><code>https://server/product/6422350843</code></p> </li> 
         <li><p><code>https://server/product/1607745002</code></p> </li> 
         <li><p><code>https://server/product/0086724882</code></p> </li> 
        </ul> <p>La partie variable se trouve dans la dernière partie du chemin et elle devient la valeur de SKU des zones réactives : <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong> et <strong><code>0086724882</code></strong>.</p> </td> 
      </tr> 
      <tr> 
       <td><p>SKU et ID de catégorie dans la chaîne de requête.</p> </td> 
       <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p> 
        <ul> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
        </ul> <p>Dans ce cas, l’URL comporte deux parties différentes. Le SKU est stocké dans le <code>prodId</code> paramètre et l’ID de catégorie.</p><p><code>categoryId</code></p><ul><li><p><code>305466</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>310181</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>308706</code><code>categoryId</code><code>1740148</code></p></li></ul><p></p></td></tr></tbody></table></td></tr><tr></tr></table>

**Exemple**

Vous pouvez appliquer la même approche utilisée dans les trois exemples ci-dessus à la page web de démonstration:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

The demo web page has several product thumbnails, each having a Quickview button labeled **[!UICONTROL See More]**. À l’aide de l’outil de débogage de votre navigateur web toujours activé, cliquez sur chaque bouton et notez les URL d’aperçu rapide enregistrées. Une fois que vous avez activé l’aperçu rapide des quatre produits disponibles sur la page, vous obtenez la liste suivante de demandes d’aperçu rapide exécutées en arrière-plan :

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Lorsque vous observez ces appels de serveur, vous constatez que les informations spécifiques au produit ne sont présentes que dans le chemin de la requête. Vous notez également que la chaîne de requête n’est pas du tout utilisée et que deux types de données distincts sont impliqués :

* Le premier type correspond au sexe, Homme ou Femme. Vous pouvez l’appeler « catégorie de produits ».
* Le second type correspond au nom du produit, comme « CamoPullover ». Vous pouvez considérer que c’est la SKU du produit.

Compte tenu de ces informations, l’intégralité de l’URL de l’aperçu rapide suit le schéma suivant :

`/datafeed/$categoryId$-$SKU$.json`

Sur la base de cette analyse, vous utiliseriez `categoryId` et `SKU` pour les zones réactives.

Vous êtes à présent prêt à charger une bannière d’image et à y ajouter des zones réactives à l’aide de la fonctionnalité d’images interactives Shoppable d’AEM Assets.

## (Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives    {#optional-creating-an-interactive-image-viewer-preset}

You can choose to use the default, out-of-the-box Interactive Image viewer preset called **[!UICONTROL Shoppable_Banner]** that comes with AEM Assets. Vous pouvez également créer votre propre paramètre prédéfini de visionneuse personnalisé à utiliser avec les images interactives.

Lorsque vous créez un paramètre prédéfini de visionneuse d’images interactives, vous pouvez déterminer l’aspect des zones réactives de la bannière d’image. Dans le cadre de la création du paramètre prédéfini de visionneuse, vous pouvez choisir d’utiliser une image de zone réactive provenant d’une galerie d’images prédéfinies.

After you save the viewer preset, it is automatically activated (turned on) on the **[!UICONTROL Viewer Preset]** list page in AEM Assets. Cette fonctionnalité signifie qu’elle est visible dans le composant Interactive Media et chaque fois que vous affichez une ressource. However, to *deliver* an interactive banner with this viewer preset, you must *publish* your viewer preset as well (this is true for custom or out-of-box viewer presets).

**Pour créer un paramètre prédéfini de la visionneuse pour les images interactives**:

1. Dans le rail de gauche, appuyez sur **[!UICONTROL Outils > Ressources > Paramètres visionneuse]**.
1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Créer]**.
1. In the **[!UICONTROL New Viewer Preset]** dialog box, type a name to describe the interactive banner viewer preset.

   This is the title that will appear in the **[!UICONTROL Viewer Preset]** list page after you save.
1. In the **[!UICONTROL Rich Media Type]** pull-down menu, select **[!UICONTROL Interactive Image]**.
1. Appuyez sur **Créer**. 
1. On the **[!UICONTROL Edit Viewer Preset]** page, tap the **[!UICONTROL Appearance]** tab.
1. Utilisez l’une des méthodes suivantes :

   * To upload your own hotspot image that you want to use on images, tap the **[!UICONTROL Asset Picker]** icon. In the **[!UICONTROL Select Content]** page, navigate to the hotspot image you want to use, select it, and then tap the **[!UICONTROL Check Mark]** icon in the upper-right corner.
   * To select a predefined hotspot image, tap the **[!UICONTROL Hotspot Gallery]** icon. On the hotspot gallery pallette, tap the hotspot image you want to use.

1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer]**.

   Assurez-vous de publier le nouveau paramètre prédéfini de la visionneuse.

   Voir [Publication des paramètres prédéfinis de la visionneuse que vous avez ajoutés](managing-viewer-presets.md#publishing-viewer-presets).

   Vous êtes désormais prêt à charger une bannière d’image.

## Chargement d’une bannière d’image    {#uploading-an-image-banner}

Si vous avez déjà chargé les images que vous souhaitez utiliser, passez à l’étape suivante [Ajout de zones réactives à une bannière d’image](#adding-hotspots-to-an-image-banner).

**Pour charger une bannière d’image** :

1. Chargez les bannières d’images que vous souhaitez rendre interactives.

   Voir la section [Chargement des ressources](managing-assets-touch-ui.md#uploading-assets).

   Vous êtes maintenant prêt à ajouter des zones réactives à la bannière d’image. Reportez-vous à la tâche suivante ci-dessous.

## Ajout de zones réactives à une bannière d’image    {#adding-hotspots-to-an-image-banner}

You can add hotspots to an image banner using the editor on the **[!UICONTROL Hotspot Management]** page.

Lorsque vous ajoutez des zones réactives, vous pouvez les définir comme un écran contextuel d’aperçu rapide, un lien hypertexte ou un fragment d’expérience.

Voir [Fragments d’expérience](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>N’oubliez pas que les outils de partage sur les réseaux sociaux ne sont pas pris en charge dans l’image interactive lorsque vous incorporez la visionneuse dans un fragment d’expérience.
>Pour contourner ce problème, vous pouvez utiliser ou créer des paramètres prédéfinis de visionneuse qui ne disposent pas d’outils de partage sur les réseaux sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

**[!UICONTROL Les options Annuler et Rétablir, proches du coin supérieur droit de la page, sont prises en charge au cours de la session de création/modification actuelle.]******

When you finish creating your interactive image, you can use **[!UICONTROL Preview]** to see a representation of how your interactive image will appear to customers.

Reportez-vous à la section [(Facultatif) Aperçu des images interactives ](#optional-previewing-interactive-images).

>[!NOTE]
>
>Lorsque vous ajoutez des zones réactives à une image dans une image interactive ou une bannière de carrousel, les informations de zone réactive sont stockées au même emplacement de métadonnées (par rapport à l’emplacement de l’image), qu’il s’agisse d’une image interactive ou d’une bannière de carrousel. Cette fonctionnalité signifie que vous pouvez facilement réutiliser la même image (avec ses données de zone réactive définies) dans les visionneuses.

>Notez cependant que les bannières de carrousel prennent en charge les images à zones cliquables, qui peuvent également contenir des zones réactives. Les images interactives n’en comportent pas. Pensez-y si vous envisagez de créer une image interactive ou une bannière de carrousel qui utilise la même image. Vous pouvez créer des images interactives et des bannières de carrousel à l’aide de copies distinctes de la même image.
>
>Voir aussi [Bannières de carrousel](carousel-banners.md).

>[!NOTE]
>
>Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

**Pour ajouter des zones réactives à une bannière d’image** :

1. En mode Ressources, accédez à la bannière d’image à laquelle vous souhaitez ajouter de l’interactivité.
1. Utilisez l’une des méthodes suivantes :

   * Pointez sur l’image, puis appuyez sur la touche **[!UICONTROL Sélectionner]** (icône de coche). Dans la barre d’outils, appuyez sur **[!UICONTROL Modifier]**.
   * Pointez sur l’image, puis appuyez sur **[!UICONTROL Autres actions]** (icône représentant des points de suspension) > **[!UICONTROL Modifier]**.
   * Tap the image to open it in the **[!UICONTROL Detail View]** page. Dans la barre d’outils, appuyez sur **[!UICONTROL Modifier]**.

1. Near the upper-left corner of the page, tap **[!UICONTROL Add Hotspot]** (finger tap icon) to open the **[!UICONTROL Hotspot Management]** page.
1. Dans le coin supérieur gauche de la page, appuyez sur **[!UICONTROL Zone réactive]**.
1. a. Near the upper-left corner of the **Hotspot Management** page, tap **[!UICONTROL Hotspot]**.
b. Sur l’image, appuyez sur un emplacement où vous souhaitez que la zone réactive s’affiche. Si nécessaire, faites glisser la zone réactive pour en ajuster l’emplacement.
c. Ajouter d&#39;autres points d&#39;accès si nécessaire en répétant les étapes a et b.
d. (Facultatif) Pour supprimer une zone réactive, sélectionnez-la sur l’image, puis appuyez sur **[!UICONTROL Supprimer]** (icône de poubelle) sous l’en-tête **[!UICONTROL Zones réactives]** .

1. In the **[!UICONTROL Name]** text field, type the name of the hotspot. This name also appears in the **[!UICONTROL Selected Hotspot]** drop-down list.
1. Utilisez l’une des méthodes suivantes :

   * Appuyez sur **[!UICONTROL Aperçu rapide]**.

      * If you are an AEM Sites or eCommerce customer, tap the **[!UICONTROL Product Picker]** icon (magnifying glass) to open the **[!UICONTROL Select Product]** page. Tap the product you want to use, then tap **[!UICONTROL Select]** in the upper-right corner of the page to return to the **[!UICONTROL Hotspot Management]** page.
      * Si vous *n’êtes pas* client AEM Sites ou eCommerce :

         * Voir [Identification des variables de zone réactive](#optional-identifying-hotspot-variables). Vous devez définir ces variables.
         * Ensuite, entrez manuellement la valeur de SKU. In the **[!UICONTROL SKU Value]** text field, type the product&#39;s SKU (Stock Keeping Unit), which is a unique identifier for each distinct product or service that you offer. La valeur de la SKU entrée est renseignée automatiquement dans la partie variable du modèle d’aperçu rapide afin que le système sache associer la zone réactive sur laquelle l’utilisateur appuie et l’aperçu rapide d’une SKU spécifique.
         * (Facultatif) S’il existe d’autres variables dans l’aperçu rapide dont vous avez besoin pour identifier un produit, appuyez sur **[!UICONTROL Ajouter la variable générique]**. Dans le champ de texte, spécifiez une variable supplémentaire. Par exemple, `category=Mens` est une variable ajoutée.
   * Appuyez sur **Lien hypertexte**.

      * If you are an AEM Sites customer, tap the **[!UICONTROL Site Selector]** icon (folder) to navigate to a URL. Notez que la méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages AEM Sites.
      * If you are a standalone customer, in the **[!UICONTROL HREF]** text field, specify the full URL path to a linked web page.

      Veillez à spécifier si vous souhaitez ouvrir le lien dans un nouvel onglet du navigateur (paramètre par défaut recommandé) ou dans le même onglet.

      Pour plus d’informations, reportez-vous à la section [Utilisation de sélecteurs](working-with-selectors.md).

   * Appuyez sur **Fragment d’expérience**.

      * If you are an AEM Sites customer, tap the **[!UICONTROL Search]** icon (magnifying glass) to open the **[!UICONTROL Experience Fragment]** page. Tap the Experience Fragment you want to use, then tap **[!UICONTROL Select]** in the upper-right corner of the page to return to the Hotspot management page.

         Voir [Fragments d’expérience](/help/sites-authoring/experience-fragments.md).
         >[!NOTE]
         >
         >N’oubliez pas que les outils de partage sur les réseaux sociaux ne sont pas pris en charge dans l’image interactive lorsque vous incorporez la visionneuse dans un fragment d’expérience.

Pour contourner ce problème, vous pouvez utiliser ou créer des paramètres prédéfinis de visionneuse qui ne disposent pas d’outils de partage sur les réseaux sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

      * Indiquez la largeur et la hauteur du fragment d’expérience tel qu’il apparaît dans la bannière.



1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer vos modifications et revenir à la page du navigateur.****
1. Publiez l’image interactive. La publication permet de fournir la bannière par le biais du cloud et génère également le code intégré si vous devez l’intégrer à un site web tiers.

   Voir [Publication de ressources](managing-assets-touch-ui.md#publishing-assets).

   Une fois que vous avez ajouté des zones réactives et publié l’image interactive, vous êtes prêt à l’ajouter à votre site web.

   Voir [Intégration d’une image interactive à votre site web](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

### (Facultatif) Aperçu des images interactives    {#optional-previewing-interactive-images}

Vous pouvez utiliser la prévisualisation pour afficher une représentation de votre image interactive, telle qu’elle s’affichera pour les clients, et tester les zones réactives de l’image pour vous assurer qu’elles se comportent de la façon escomptée.

Lorsque vous êtes satisfait de l’image interactive, vous pouvez la publier.\
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](embed-code.md).\
Voir [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md). Notez que la méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages AEM Sites.\
Reportez-vous à la section [Ajout de ressources Dynamic Media aux pages.](adding-dynamic-media-assets-to-pages.md)

**Pour prévisualiser des images interactives** :

1. En mode Ressources, accédez à une image interactive existante que vous avez créée et appuyez pour la prévisualiser.
1. Near the upper-left corner of the Preview page, in the **[!UICONTROL Content]** drop-down list, tap **[!UICONTROL Viewers]**.
1. In the **[!UICONTROL Viewers]** list, tap **[!UICONTROL Shoppable_Banner]** or the name of the interactive image viewer preset you have created.
1. Appuyez sur les zones réactives de l’image pour tester les actions associées.

## Publication des ressources d’images interactives {#publishing-interactive-image-assets}

Voir [Publication de ressources](publishing-dynamicmedia-assets.md) pour obtenir des informations sur la publication de ressources d’images interactives.

## Intégration d’une image interactive à votre site web {#integrating-an-interactive-image-with-your-website}

Une fois que vous avez chargé une image de bannière, ajouté des zones réactives à l’image et publié l’image interactive, vous êtes prêt à l’ajouter dans une page de votre site web.

Si vous êtes client AEM Sites, vous pouvez ajouter l’image interactive en faisant glisser le composant Interactive Media dans votre page. Reportez-vous à la section [Ajout de ressources Dynamic Media aux pages.](adding-dynamic-media-assets-to-pages.md)

Si vous êtes client AEM Assets autonome, vous pouvez ajouter manuellement l’image interactive à votre site web, comme indiqué dans cette section.

1. Copiez le code intégré de l’image interactive publiée.

   Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](embed-code.md).

1. Ajoutez le code intégré copié à l’emplacement souhaité dans la page web.

   Le code intégré copié est défini pour un environnement réactif afin qu’il s’adapte automatiquement à la zone qui lui est affectée.

**Exemple**

En vous servant du site web de démonstration comme exemple, procédez comme suit :

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

Notez que l’image des trois hommes est une balise `IMG` statique :

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

L’intégration revient simplement à supprimer la balise `IMG` et à la remplacer par le code intégré copié à partir d’AEM Assets. Vous pouvez voir le résultat dans l’URL suivante qui affiche l’image interactive pouvant être consultée sur la page avec trois zones réactives de cercle :

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
>
>À ce stade, les zones réactives de l’image interactive Shoppable du site web de démonstration sont en mode affichage uniquement ; elles ne sont pas encore intégrées aux aperçus rapides existants.

To apply a crop to a shoppable interactive image for a responsive environment, you can include the Interactive Image configuration attribute `ZoomView.iscommand` to the path—where `ZoomView` is the component to call and `iscommand` is the crop image serving command that you apply.

Voir l’attribut de configuration [ZoomView.iscommand](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html).

Voir la commande de service d’images [crop](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html)

Vous êtes désormais prêt à intégrer l’image interactive à un aperçu rapide existant de votre site web.

## Intégration d’une image interactive dans un aperçu rapide existant    {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Cette tâche ne s’applique que si vous êtes un client AEM Assets autonome.

La dernière étape de cette procédure intègre l’image interactive à un aperçu rapide existant sur votre site web. Pour ce qui est de l’intégration, il n’existe pas de solution qui fonctionne dans tous les cas. Chaque mise en œuvre de l’aperçu rapide est unique, et une approche spécifique est nécessaire, ce qui implique généralement l’assistance d’un informaticien compétent en systèmes frontaux.

L’implémentation d’aperçus rapides existante représente normalement une chaîne d’actions entre-associées qui se produisent sur la page web dans l’ordre suivant :

1. Un utilisateur déclenche un élément dans l’interface utilisateur de votre site web.
1. Le code frontal obtient une URL d’aperçu rapide basée sur l’élément d’interface utilisateur qui a été déclenché à l’étape 1.
1. Le code frontal envoie une demande Ajax en utilisant l’URL obtenue à l’étape 2.
1. La logique du serveur principal renvoie les données ou le contenu de l’aperçu rapide correspondant au code frontal.
1. Le code frontal charge les données ou le contenu de l’aperçu rapide.
1. Le code frontal convertit éventuellement les données téléchargées de l’aperçu rapide en une représentation HTML.
1. Le code frontal affiche une boîte de dialogue ou un panneau modal et effectue le rendu du contenu HTML à l’écran pour l’utilisateur final.

Ces appels peuvent ne pas représenter des appels d’API publiques indépendants qui peuvent être appelés par la logique de la page web depuis une étape arbitraire. À la place, il s’agit d’un appel chaîné où chaque étape suivante est masquée dans la dernière phase (rappel) de l’étape précédente.

En même temps que l’image interactive Shoppable remplace l’étape 1 et partiellement l’étape 2, lorsqu’un utilisateur clique sur une zone réactive dans l’image Shoppable, cette interaction est gérée par la visionneuse. La visionneuse renvoie un événement à la page web qui contient toutes les données des zones réactives ajoutées antérieurement à AEM Assets.

Dans ce type de gestionnaire d’événements, le code frontal effectue les opérations suivantes :

* Il écoute un événement émis par l’image interactive Shoppable.
* Il crée une URL d’aperçu rapide basée sur les données des zones réactives.
* Il déclenche le processus de chargement de l’aperçu rapide depuis le serveur principal et en effectue le rendu à l’écran.

Le code intégré renvoyé par AEM Assets comporte déjà un descripteur d’événement prêt à l’emploi, qui est commenté, comme vous pouvez le constater dans le fragment de code mis en surbrillance ci-dessous :

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : { 
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({ 
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 }, 
             });
        */
        s7interactiveimageviewer.init();
```

Il suffit donc de supprimer les commentaires du code et remplacer le corps factice du gestionnaire par le code spécifique à la page web.

Le processus de création de l’URL d’aperçu rapide est presque l’opposé du processus utilisé pour identifier les variables des zones réactives décrit précédemment.

Voir [Identification des variables des zones réactives](#optional-identifying-hotspot-variables).

En utilisant nos exemples précédents d’URL d’aperçu rapide, vous pouvez voir, dans les exemples suivants, comment l’URL est créée dans chaque cas :

<table> 
 <tbody> 
  <tr> 
   <td><p>SKU unique, trouvé dans la chaîne de requête</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>SKU unique, trouvé dans le chemin d’accès à l’URL</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>SKU et ID de catégorie dans la chaîne de requête</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td> 
  </tr> 
 </tbody> 
</table>

La dernière étape pour déclencher l’URL d’aperçu rapide et activer le panneau d’aperçu rapide nécessite probablement l’assistance d’un informaticien compétent de votre service informatique. Celui-ci sait comment déclencher précisément l’implémentation de l’aperçu rapide à partir de l’étape appropriée, avec une URL d’aperçu rapide prête à l’emploi.

Vous pouvez découvrir comment ces étapes sont appliquées au site web de démonstration pour l’intégration complète d’une image interactive publicitaire avec le code d’aperçu rapide. Plus tôt dans cette rubrique, la structure de l’URL de l’aperçu rapide a été identifiée comme suit :

```xml
/datafeed/$categoryId$-$SKU$.json
```

Pour reconstruire cette URL à l’intérieur du descripteur `quickViewActivate`, vous pouvez utiliser les champs `categoryId` et `SKU` disponibles dans l’objet `inData` transmis au gestionnaire par le code de la visionneuse :

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

Le site web de démonstration déclenche la boîte de dialogue d’aperçu rapide si vous utilisez un simple appel de la fonction `loadQuickView()`. Cette fonction n’accepte qu’un seul argument, qui est l’URL des données d’aperçu rapide. Ainsi, la dernière étape nécessaire pour intégrer l’image interactive Shoppable consiste à ajouter la ligne de code ci-dessous au gestionnaire `quickViewActivate` :

```xml
loadQuickView(quickViewUrl);
```

Voici le code source complet :

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : { 
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({ 
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    }, 
   });
 s7interactiveimageviewer.init();
```

Le dernier site web de démonstration avec l’image interactive totalement intégrée se présente comme suit :

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html)

## Utilisation d’aperçus rapides pour créer des fenêtres contextuelles personnalisées {#using-quickviews-to-create-custom-pop-ups}

Voir [Utilisation d’aperçus rapides pour créer des fenêtres contextuelles personnalisées](custom-pop-ups.md).
