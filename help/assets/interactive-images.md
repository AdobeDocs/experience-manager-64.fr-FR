---
title: Images interactives
seo-title: Interactive Images
description: Découvrez comment utiliser des images interactives dans Dynamic Media
seo-description: Learn how to work with interactive images in dynamic media
uuid: e8f79bc1-fccb-48d0-aca1-7f319c595fe9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d630499d-740d-4979-8a34-9e3fcc3b5a23
exl-id: 4d3299e2-269b-4a41-a979-c884c707666d
feature: Interactive Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4283'
ht-degree: 63%

---

# Images interactives {#interactive-images}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez facilement créer des expériences riches et attrayantes pour vos clients à partir d’images statiques en ajoutant des zones réactives « shoppable » aux images par glisser-déposer. Les zones réactives Shoppable rassemblent des informations supplémentaires sur un produit ou un service avec une fonctionnalité directe de point de vente de type « Ajouter au panier » ou « Acheter ». Les clients peuvent appuyer sur ces zones réactives et être liés directement au produit ou au service, l’ajouter à un panier ou être associés à une page web. Les expériences directes de ce type augmentent l’engagement et la conversion des clients sur votre site web.

Voici une bannière publicitaire avec une fenêtre contextuelle d’aperçu rapide. L’utilisateur active l’aperçu rapide en appuyant sur le cercle ou la « zone réactive » du modèle.

![chlimage_1-368](assets/chlimage_1-368.png)

Consultez les images interactives en action sur la page web ci-dessus en visitant la page :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html?lang=fr](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html?lang=fr)

## Découvrir comment les bannières d’images interactives sont créées {#watch-how-interactive-image-banners-are-created}

Visionnez une présentation vidéo de 10 minutes et 33 secondes sur la [création de bannières d’images interactives](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Vous apprendrez également à prévisualiser, modifier et diffuser des bannières d’images interactives.

## Démarrage rapide : images interactives {#quick-start-interactive-images}

La description suivante du workflow étape par étape est conçue pour vous aider à mettre en route rapidement les images interactives dans AEM Assets.

Recherchez le titre **Exemple** dans certaines tâches de démarrage rapide. Il contient un court tutoriel basé sur l’exemple de page web suivant qui ne contient pas encore d’images interactives :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr)

Le tutoriel permet d’illustrer les étapes de l’intégration d’images interactives à votre propre site web.

**Workflow Images interactives**:

1. **(Facultatif) Identification des variables de zone réactive** - Si vous utilisez des instances autonomes d’AEM Assets et de Dynamic Media, commencez par identifier les variables dynamiques utilisées dans votre mise en oeuvre existante de l’aperçu rapide afin de pouvoir entrer les données de zone réactive lors de la création de l’image interactive. Voir [(Facultatif) Identification des variables de zone réactive](#optional-identifying-hotspot-variables).

   Cependant, si vous utilisez AEM Sites ou AEM eCommerce, ou les deux, cette étape n’est pas nécessaire.

   Voir [Concepts d’eCommerce dans AEM Assets](/help/sites-administering/concepts.md).

1. **(Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives** - Personnalisez l’image utilisée pour représenter les zones réactives. Vous n’avez pas besoin de créer votre propre paramètre prédéfini de visionneuse d’images interactives si vous envisagez plutôt d’utiliser le paramètre prédéfini de visionneuse d’images interactive prêt à l’emploi `Shoppable_Banner`.


   Voir [(Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives](managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Chargement d’une bannière d’image** - Téléchargez les bannières d’image que vous souhaitez rendre interactives.

   Voir [Chargement d’une bannière d’image](#uploading-an-image-banner).

1. **Ajout de zones réactives à une bannière d’image** - Ajoutez une ou plusieurs zones réactives à une bannière d’image et associez chacune d’elles à une action telle qu’un lien hypertexte, un aperçu rapide ou un fragment d’expérience. Après avoir ajouté des zones réactives, vous terminez cette tâche en publiant l’image interactive.

   * Voir [Ajout de zones réactives à une bannière d’image](#adding-hotspots-to-an-image-banner).
   * Voir [Prévisualisation d’images interactives](#optional-previewing-interactive-images) – Facultatif. Si vous le souhaitez, vous pouvez afficher une représentation de votre bannière Shoppable et tester son interactivité.
   * Voir [Publication de ressources](publishing-dynamicmedia-assets.md) pour obtenir des informations sur la publication de ressources d’images interactives.

1. **Ajout d’une image interactive à votre site web ou à votre site web dans AEM**

   * Si vous utilisez AEM Sites, ou AEM eCommerce, ou les deux, vous pouvez ajouter l’image interactive directement à une page web dans AEM en faisant glisser le composant Interactive Media sur la page. Reportez-vous à [Ajout de ressources Dynamic Media aux pages](adding-dynamic-media-assets-to-pages.md).
   * Si vous utilisez des instances autonomes d’AEM Assets et de Dynamic Media, vous devez copier le code intégré sur votre site web, puis l’intégrer à votre aperçu rapide existant. Voir [Intégration d’une image interactive à votre site web](#integrating-an-interactive-image-with-your-website).
   * Si vous utilisez un gestionnaire de contenu web (WCM) tiers, vous devez intégrer la nouvelle vidéo interactive à l’aperçu rapide existant utilisé sur votre site web. Reportez-vous à la section [Intégration d’une image interactive dans un aperçu rapide existant](#integrating-an-interactive-image-with-an-existing-quickview).

## (Facultatif) Identification des variables de zone réactive {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Cette tâche n’est nécessaire que si les conditions ci-dessous sont vraies :
>
>* Vous souhaitez ajouter de l’interactivité à votre image en déclenchant des aperçus rapides.
>* Votre mise en œuvre d’AEM n’utilise *pas* de framework d’intégration de commerce électronique pour extraire des données de produit dans AEM à partir d’une solution de commerce électronique, comme IBM WebSphere Commerce, Elastic Path, Hybris ou Intershop. Voir [Concepts d’eCommerce dans AEM Assets](/help/sites-administering/concepts.md).
>
>Si votre mise en œuvre d’AEM utilise eCommerce, vous pouvez ignorer cette tâche et passer à la tâche suivante.

Commencez par identifier les variables dynamiques utilisées par votre mise en œuvre de l’aperçu rapide existant afin de pouvoir entrer les données de zone réactive pour créer l’image interactive.

Lorsque vous ajoutez des zones réactives à une image de bannière dans AEM Assets, vous devez affecter un SKU (unité de gestion des stocks ; un identifiant unique pour chaque produit ou service distinct que vous fournissez) et des variables supplémentaires facultatives à chaque zone réactive. Ces variables de zones réactives sont utilisées ultérieurement pour faire correspondre ces zones réactives avec du contenu d’aperçu rapide.

Il est important d’identifier correctement le nombre et le type de variables à associer aux données de zone réactive. Chaque zone réactive ajoutée à une image de bannière doit comporter suffisamment d’informations pour identifier clairement le produit sur le système principal existant.

Il existe différentes manières d’identifier un jeu de variables à utiliser pour les données des zones réactives.

Il peut parfois être nécessaire de consulter les spécialistes informatiques responsables de l’implémentation d’aperçu rapide existante, car ils connaissent probablement le jeu minimum de données nécessaires pour identifier l’aperçu rapide dans le système. Cependant, dans la plupart des cas, il est également possible d’analyser simplement le comportement existant du code frontal.

La plupart des implémentations d’aperçu rapide utilisent le paradigme suivant :

* L’utilisateur active un élément d’interface utilisateur sur le site web. Par exemple, en cliquant sur un **[!UICONTROL Aperçu rapide]** bouton .
* Le site Web envoie une requête Ajax au serveur principal afin de charger les données ou le contenu de l’aperçu rapide, le cas échéant.
* Les données de l’aperçu rapide sont traduites en contenu en préparation du rendu sur la page Web.
* Enfin, le code en front-end effectue le rendu visuel de ce contenu à l’écran.

L’approche consiste ensuite à visiter différentes zones du site web existant où la fonction d’aperçu rapide est mise en oeuvre, à déclencher l’aperçu rapide et à capturer l’URL Ajax envoyée par la page web pour le chargement des données ou du contenu de l’aperçu rapide.

Normalement, il n’est pas nécessaire d’utiliser des outils de débogage spécialisés. Les navigateurs web modernes incluent des inspecteurs web qui font un travail correct. Vous trouverez ci-dessous quelques exemples de navigateurs web qui incluent des inspecteurs web :

* Pour afficher toutes les requêtes HTTP sortantes dans Google Chrome, appuyez sur F12 pour ouvrir le **[!UICONTROL Outils de développement]** puis cliquez sur le bouton **[!UICONTROL Réseau]** .

   Sur une Mac, appuyez sur **[!UICONTROL Commande + Option + I]** pour ouvrir le **[!UICONTROL Outils de développement]** , puis cliquez sur l’onglet Réseau .

* Dans Firefox, vous pouvez activer le module externe Firebug en appuyant sur F12 et utiliser son onglet Réseau, ou vous pouvez utiliser le **[!UICONTROL Inspecteur]** et son **[!UICONTROL Réseau]** .

   Sur une Mac, appuyez sur **[!UICONTROL Commande + Option + I]** pour ouvrir le **[!UICONTROL Outils de développement]** , puis cliquez sur le bouton **[!UICONTROL Inspecteur]** .

Lorsque la surveillance de réseau est activée dans le navigateur, déclenchez l’aperçu rapide sur la page.

Vous trouvez maintenant l’URL Ajax d’aperçu rapide dans le journal réseau. Copiez l’URL enregistrée pour l’analyse ultérieure. Dans la plupart des cas, lorsque vous déclenchez l’aperçu rapide, plusieurs requêtes sont envoyées au serveur. En règle générale, l’URL Ajax d’aperçu rapide est l’une des premières dans la liste. Elle possède une partie de chaîne de requête complexe ou un chemin d’accès, et son type de réponse MIME est `text/html`, `text/xml` ou `text/javascript`.

Au cours de ce processus, il est important de parcourir différentes zones de votre site web, avec différentes catégories et types de produits. C’est pourquoi les URL d’aperçu rapide peuvent avoir des parties communes pour une catégorie de site web donnée, mais ne changent que si vous visitez une autre zone du site web.

Dans le cas le plus simple, la seule partie variable dans l’URL de l’aperçu rapide est le SKU du produit. Dans ce cas, la valeur de SKU est la seule donnée dont vous avez besoin pour ajouter des zones réactives à l’image de bannière.

Cependant, dans les cas complexes, l’URL d’aperçu rapide comporte différents éléments variables en complément du SKU, comme l’identifiant de la catégorie, le code couleur, le code taille, etc. Dans ce cas, chaque élément est une variable distincte dans votre définition de données de zone réactive dans la fonction d’image interactive Shoppable d’AEM Assets.

Examinez les exemples suivants d’URL d’aperçu rapide et les variables de zone réactive qui en résultent :

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
        </ul> <p>Dans ce cas, l’URL comporte deux parties différentes. Le SKU est stocké dans la variable <code>prodId</code> et l’ID de catégorie</p><p><code>categoryId</code></p><ul><li><p><code>305466</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>310181</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>308706</code><code>categoryId</code><code>1740148</code></p></li></ul><p></p></td></tr></tbody></table></td></tr><tr></tr></table>

**Exemple**

Vous pouvez appliquer la même approche utilisée dans les trois exemples ci-dessus à la page web de démonstration :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr)

La page web de démonstration comporte plusieurs miniatures de produit, chacune disposant d’un bouton d’aperçu rapide intitulé &quot;Aperçu rapide&quot;. **[!UICONTROL Voir Plus]**. À l’aide de l’outil de débogage de votre navigateur web toujours activé, cliquez sur chaque bouton et notez les URL d’aperçu rapide enregistrées. Après avoir activé les quatre aperçus rapides de produit disponibles sur la page, la liste suivante de demandes d’aperçu rapide est envoyée au serveur principal :

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

En examinant ces appels de serveur, vous voyez que les informations spécifiques au produit ne sont présentes que dans le chemin de requête. Vous notez également que la chaîne de requête n’est pas du tout utilisée et que deux types de données distincts sont impliqués :

* Le premier type est Hommes ou Femmes. Vous pouvez l’appeler « catégorie de produits ».
* Le deuxième type est le nom du produit, tel que CamoPullover. Vous pouvez supposer qu’il s’agit du SKU du produit.

Compte tenu de ces informations, l’intégralité de l’URL de l’aperçu rapide suit le schéma suivant :

`/datafeed/$categoryId$-$SKU$.json`

Sur la base de cette analyse, vous utiliseriez `categoryId` et `SKU` pour les zones réactives.

Vous êtes à présent prêt à charger une bannière d’image et à y ajouter des zones réactives à l’aide de la fonctionnalité d’images interactives Shoppable d’AEM Assets.

## (Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives {#optional-creating-an-interactive-image-viewer-preset}

Vous pouvez choisir d’utiliser le paramètre prédéfini de visionneuse d’images interactives par défaut, appelé **[!UICONTROL Shoppable_Banner]** qui est fourni avec AEM Assets. Vous pouvez également créer votre propre paramètre prédéfini de visionneuse personnalisé à utiliser avec les images interactives.

Lorsque vous créez un paramètre prédéfini de visionneuse d’images interactives, vous pouvez déterminer l’aspect des zones réactives de la bannière d’image. Dans le cadre de la création du paramètre prédéfini de visionneuse, vous pouvez choisir d’utiliser une image de zone réactive provenant d’une galerie d’images prédéfinies.

Une fois le paramètre prédéfini de visionneuse enregistré, il est automatiquement activé sur la **[!UICONTROL Paramètre prédéfini de la visionneuse]** page de liste dans AEM Assets. Cette fonctionnalité signifie qu’elle est visible dans le composant Interactive Media et chaque fois que vous affichez une ressource. Toutefois, pour *delivery* une bannière interactive avec ce paramètre prédéfini de visionneuse, vous devez *publier* votre paramètre prédéfini de visionneuse (c’est également le cas pour les paramètres prédéfinis de visionneuse personnalisés ou prêts à l’emploi).

**Pour créer un paramètre prédéfini de la visionneuse pour les images interactives**:

1. Dans le rail de gauche, appuyez sur **[!UICONTROL Outils > Ressources > Paramètres visionneuse]**.
1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Créer]**.
1. Dans le **[!UICONTROL Nouveau paramètre prédéfini de visionneuse]** , saisissez un nom pour décrire le paramètre prédéfini de visionneuse de bannière interactive.

   Il s’agit du titre qui apparaîtra dans la variable **[!UICONTROL Paramètre prédéfini de la visionneuse]** page de liste après l’enregistrement.
1. Dans le **[!UICONTROL Type de média enrichi]** menu déroulant, sélectionnez **[!UICONTROL Image interactive]**.
1. Appuyez sur **Créer**.
1. Sur le **[!UICONTROL Modifier le paramètre prédéfini de la visionneuse]** , appuyez sur **[!UICONTROL Apparence]** .
1. Utilisez l’une des méthodes suivantes :

   * Pour télécharger votre propre image de zone réactive que vous souhaitez utiliser sur les images, appuyez sur la **[!UICONTROL Sélecteur de ressources]** icône . Dans le **[!UICONTROL Sélectionner le contenu]** , accédez à l’image de zone réactive que vous souhaitez utiliser, sélectionnez-la, puis appuyez sur **[!UICONTROL Coche]** dans le coin supérieur droit.
   * Pour sélectionner une image de zone réactive prédéfinie, appuyez sur la **[!UICONTROL Galerie de zones réactives]** icône . Dans la palette de la galerie de zones réactives, appuyez sur l’image de zone réactive que vous souhaitez utiliser.

1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer]**.

   Assurez-vous de publier le nouveau paramètre prédéfini de la visionneuse.

   Voir [Publication des paramètres prédéfinis de visionneuse que vous avez ajoutés](managing-viewer-presets.md#publishing-viewer-presets).

   Vous êtes désormais prêt à charger une bannière d’image.

## Chargement d’une bannière d’image {#uploading-an-image-banner}

Si vous avez déjà chargé les images que vous souhaitez utiliser, passez à l’étape suivante [Ajout de zones réactives à une bannière d’image](#adding-hotspots-to-an-image-banner).

**Pour charger une bannière d’image** :

1. Chargez les bannières d’images que vous souhaitez rendre interactives.

   Voir la section [Chargement des ressources](managing-assets-touch-ui.md#uploading-assets).

   Vous êtes maintenant prêt à ajouter des zones réactives à la bannière d’image. Reportez-vous à la tâche suivante ci-dessous.

## Ajout de zones réactives à une bannière d’image {#adding-hotspots-to-an-image-banner}

Vous pouvez ajouter des zones réactives à une bannière d’image à l’aide de l’éditeur sur la page **[!UICONTROL Gestion des zones réactives]** page.

Lorsque vous ajoutez des zones réactives, vous pouvez les définir comme un affichage contextuel d’aperçu rapide, comme lien hypertexte ou comme fragment d’expérience.

Voir [Fragments d’expérience](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>N’oubliez pas que les outils de partage sur les médias sociaux ne sont pas pris en charge dans l’image interactive lorsque vous incorporez la visionneuse dans un fragment d’expérience. Pour contourner ce problème, vous pouvez utiliser ou créer des paramètres prédéfinis de visionneuse qui ne disposent pas d’outils de partage sur les médias sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

**[!UICONTROL Les options Annuler et Rétablir, proches du coin supérieur droit de la page, sont prises en charge au cours de la session de création/modification actuelle.]******

Une fois la création de votre image interactive terminée, vous pouvez utiliser **[!UICONTROL Aperçu]** pour afficher une représentation de votre image interactive telle qu’elle s’affichera pour les clients.

Reportez-vous à la section [(Facultatif) Aperçu des images interactives](#optional-previewing-interactive-images).

>[!NOTE]
>
>Lorsque vous ajoutez des zones réactives à une image dans une image interactive ou bannière de carrousel, les informations de zone réactive sont stockées au même emplacement de métadonnées (par rapport à l’emplacement de l’image), qu’il s’agisse d’une image interactive ou d’une bannière de carrousel. Cette fonctionnalité signifie que vous pouvez facilement réutiliser la même image (ainsi que ses données de zone réactive définies) dans n’importe quelle visionneuse.
>
>Notez cependant que les bannières de carrousel prennent en charge les images à zones cliquables, qui peuvent également contenir des zones réactives. Les images interactives n’en comportent pas. Gardez cela à l’esprit si vous envisagez de créer une image interactive ou une bannière de carrousel qui utilise la même image. Vous pouvez créer des images interactives et des bannières de carrousel à l’aide de copies distinctes de la même image.
>
>Voir aussi [Bannières de carrousel](carousel-banners.md).

>[!NOTE]
>
>Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

**Pour ajouter des zones réactives à une bannière d’image** :

1. Dans la vue Ressources, accédez à la bannière d’image que vous souhaitez rendre interactive.
1. Utilisez l’une des méthodes suivantes :

   * Pointez sur l’image, puis appuyez sur la touche **[!UICONTROL Sélectionner]** (icône de coche). Dans la barre d’outils, appuyez sur **[!UICONTROL Modifier]**.
   * Pointez sur l’image, puis appuyez sur **[!UICONTROL Autres actions]** (icône représentant trois points) > **[!UICONTROL Modifier]**.
   * Appuyez sur l’image pour l’ouvrir dans le **[!UICONTROL Affichage des détails]** page. Dans la barre d’outils, appuyez sur **[!UICONTROL Modifier]**.

1. Dans le coin supérieur gauche de la page, appuyez sur **[!UICONTROL Ajouter une zone réactive]** (icône d’appui à l’aide du doigt) pour ouvrir la fenêtre **[!UICONTROL Gestion des zones réactives]** page.
1. Dans le coin supérieur gauche de la page, appuyez sur **[!UICONTROL Zone réactive]**.
1. a. Près du coin supérieur gauche de la **Gestion des zones réactives** page, appuyez sur **[!UICONTROL Zone réactive]**.
b. Sur l’image, appuyez sur l’emplacement où vous souhaitez que la zone réactive s’affiche. Si nécessaire, faites glisser la zone réactive pour en ajuster l’emplacement.
c. Ajoutez d’autres zones réactives si nécessaire en répétant les étapes a et b. d. (Facultatif) Pour supprimer une zone réactive, sélectionnez-la sur l’image, puis appuyez sur **[!UICONTROL Supprimer]** (icône poubelle) sous la **[!UICONTROL Zones réactives]** en-tête.

1. Dans le **[!UICONTROL Nom]** Champ de texte, saisissez le nom de la zone réactive. Ce nom apparaît également dans la variable **[!UICONTROL Zone réactive sélectionnée]** liste déroulante.
1. Utilisez l’une des méthodes suivantes :

   * Appuyez sur **[!UICONTROL Aperçu rapide]**.

      * Si vous êtes un client AEM Sites ou eCommerce, appuyez sur **[!UICONTROL Sélecteur de produits]** (loupe) pour ouvrir la **[!UICONTROL Sélectionner un produit]** page. Appuyez sur le produit que vous souhaitez utiliser, puis sur **[!UICONTROL Sélectionner]** dans le coin supérieur droit de la page pour revenir à la **[!UICONTROL Gestion des zones réactives]** page.
      * Si vous *n’êtes pas* client AEM Sites ou eCommerce :

         * Voir [Identification des variables de zone réactive](#optional-identifying-hotspot-variables). Vous devez définir ces variables.
         * Ensuite, entrez manuellement la valeur de SKU. Dans le **[!UICONTROL Valeur SKU]** Champ de texte, saisissez la SKU (unité de gestion des stocks) du produit, qui est un identifiant unique pour chaque produit ou service distinct que vous proposez. La valeur de la SKU entrée est renseignée automatiquement dans la partie variable du modèle d’aperçu rapide afin que le système sache associer la zone réactive sur laquelle l’utilisateur appuie et l’aperçu rapide d’une SKU spécifique.
         * (Facultatif) S’il existe d’autres variables dans l’aperçu rapide dont vous avez besoin pour identifier un produit, appuyez sur **[!UICONTROL Ajouter la variable générique]**. Dans le champ de texte, spécifiez une variable supplémentaire. Par exemple, `category=Mens` est une variable ajoutée.
   * Appuyez sur **Lien hypertexte**.

      * Si vous êtes un client AEM Sites, appuyez sur **[!UICONTROL Sélecteur de site]** pour accéder à une URL. Notez que la méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages AEM Sites.
      * Si vous êtes un client autonome, dans la variable **[!UICONTROL HREF]** Champ de texte, indiquez le chemin URL complet vers une page web liée.

      Veillez à spécifier si vous souhaitez ouvrir le lien dans un nouvel onglet du navigateur (paramètre par défaut recommandé) ou dans le même onglet.

      Pour plus d’informations, voir [Utilisation de sélecteurs](working-with-selectors.md).

   * Appuyez sur **Fragment d’expérience**.

      * Si vous êtes un client AEM Sites, appuyez sur **[!UICONTROL Rechercher]** (loupe) pour ouvrir la **[!UICONTROL Fragment d’expérience]** page. Appuyez sur le fragment d’expérience que vous souhaitez utiliser, puis appuyez sur **[!UICONTROL Sélectionner]** dans le coin supérieur droit de la page pour revenir à la page de gestion des zones réactives.

         Voir [Fragments d’expérience](/help/sites-authoring/experience-fragments.md).
         >[!NOTE]
         >N’oubliez pas que les outils de partage sur les médias sociaux ne sont pas pris en charge dans l’image interactive lorsque vous incorporez la visionneuse dans un fragment d’expérience. Pour contourner ce problème, vous pouvez utiliser ou créer des paramètres prédéfinis de visionneuse qui ne disposent pas d’outils de partage sur les médias sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

      * Indiquez la largeur et la hauteur du fragment d’expérience tel qu’il apparaît dans la bannière.



1. Appuyer **[!UICONTROL Enregistrer]** pour enregistrer votre travail et revenir au **[!UICONTROL Parcourir]** page.
1. Publiez l’image interactive. La publication permet à la bannière d’être diffusée par le cloud et génère également du code intégré si vous devez l’intégrer à un site web tiers.

   Voir [Publication de ressources](managing-assets-touch-ui.md#publishing-assets).

   Une fois que vous avez ajouté des zones réactives et publié l’image interactive, vous êtes prêt à l’ajouter à votre site web.

   Voir [Intégration d’une image interactive à votre site web](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

### (Facultatif) Aperçu des images interactives {#optional-previewing-interactive-images}

Vous pouvez utiliser la prévisualisation pour afficher une représentation de votre image interactive, telle qu’elle s’affichera pour les clients, et tester les zones réactives de l’image pour vous assurer qu’elles se comportent de la façon escomptée.

Lorsque vous êtes satisfait de l’image interactive, vous pouvez la publier.\
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](embed-code.md).\
Voir [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md). Notez que la méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages AEM Sites.\
Reportez-vous à la section [Ajout de ressources Dynamic Media aux pages.](adding-dynamic-media-assets-to-pages.md)

**Pour prévisualiser des images interactives** :

1. En mode Ressources, accédez à une image interactive existante que vous avez créée et appuyez pour la prévisualiser.
1. Près du coin supérieur gauche de la page Aperçu, dans la **[!UICONTROL Contenu]** liste déroulante, appuyez sur **[!UICONTROL Visionneuses]**.
1. Dans le **[!UICONTROL Visionneuses]** liste, appuyez sur **[!UICONTROL Shoppable_Banner]** ou le nom du paramètre prédéfini de visionneuse d’images interactives que vous avez créé.
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

Utiliser le site web de démonstration comme exemple :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr)

Remarquez que la photo des trois hommes est statique. `IMG` tag :

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

L’intégration revient simplement à supprimer la balise `IMG` et à la remplacer par le code intégré copié à partir d’AEM Assets. Vous pouvez voir le résultat dans l’URL suivante qui montre l’image interactive shoppable sur la page avec trois zones réactives en cercle :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html?lang=fr](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html?lang=fr)

>[!NOTE]
>
>À ce stade, les zones réactives de l’image interactive Shoppable du site web de démonstration sont en mode affichage uniquement ; elles ne sont pas encore intégrées aux aperçus rapides existants.

Pour appliquer un recadrage à une image interactive Shoppable pour un environnement réactif, vous pouvez inclure l’attribut de configuration de l’image interactive `ZoomView.iscommand` au chemin d’accès, où `ZoomView` est le composant à appeler et `iscommand` est la commande de service d’images de recadrage que vous appliquez.

Voir l’attribut de configuration [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html?lang=fr).

Voir la commande de service d’images [crop](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html?lang=fr).

Vous êtes maintenant prêt à intégrer l’image interactive à un aperçu rapide existant sur votre site web.

## Intégration d’une image interactive dans un aperçu rapide existant {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Cette tâche ne s’applique que si vous êtes un client AEM Assets autonome.

La dernière étape de cette procédure intègre l’image interactive à un aperçu rapide existant sur votre site web. Pour ce qui est de l’intégration, il n’existe pas de solution qui fonctionne dans tous les cas. Chaque mise en oeuvre d’aperçu rapide est unique et une approche spécifique est nécessaire, qui implique probablement l’assistance d’un informaticien compétent.

L’implémentation d’aperçus rapides existante représente normalement une chaîne d’actions interdépendantes qui se produisent sur la page web dans l’ordre suivant :

1. Un utilisateur déclenche un élément dans l’interface utilisateur de votre site web.
1. Le code en front-end obtient une URL d’aperçu rapide basée sur l’élément d’interface utilisateur qui a été déclenché à l’étape 1.
1. Le code en front-end envoie une demande Ajax en utilisant l’URL obtenue à l’étape 2.
1. La logique du serveur principal renvoie les données ou le contenu de l’aperçu rapide correspondant au code en front-end.
1. Le code en front-end charge les données ou le contenu de l’aperçu rapide.
1. Facultativement, le code en front-end convertit les données chargées de l’aperçu rapide en une représentation HTML.
1. Le code en front-end affiche une boîte de dialogue ou un panneau modal et effectue le rendu du contenu HTML à l’écran pour l’utilisateur final.

Ces appels peuvent ne pas représenter des appels d’API publiques indépendants qui peuvent être appelés par la logique de la page web depuis une étape arbitraire. À la place, il s’agit d’un appel chaîné où chaque étape suivante est masquée dans la dernière phase (rappel) de l’étape précédente.

Au même moment que l’image interactive Shoppable remplace l’étape 1 et partiellement l’étape 2, lorsqu’un utilisateur clique sur une zone réactive dans l’image Shoppable, cette interaction utilisateur est gérée par la visionneuse. La visionneuse renvoie un événement à la page web qui contient toutes les données des zones réactives ajoutées précédemment dans AEM Assets.

Dans ce type de gestionnaire d’événements, le code en front-end effectue les opérations suivantes :

* Écoute un événement émis par l’image interactive Shoppable.
* Construit une URL d’aperçu rapide basée sur les données de zone réactive.
* Il déclenche le processus de chargement de l’aperçu rapide depuis le serveur principal et en effectue le rendu à l’écran.

Le code incorporé renvoyé par AEM Assets dispose déjà d’un gestionnaire d’événements prêt à l’emploi qui est commenté, comme illustré dans le fragment de code mis en surbrillance suivant :

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

Il suffit donc de supprimer les commentaires du code et de remplacer le corps factice du gestionnaire par le code spécifique à la page web.

Le processus de création de l’URL d’aperçu rapide est essentiellement l’opposé du processus utilisé pour identifier les variables de zone réactive décrit précédemment.

Voir [Identification des variables des zones réactives](#optional-identifying-hotspot-variables).

En utilisant nos exemples précédents d’URL d’aperçu rapide, vous pouvez voir, dans les exemples suivants, comment l’URL d’aperçu rapide est créée dans chaque cas :

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

La dernière étape pour déclencher l’URL d’aperçu rapide et activer le panneau d’aperçu rapide nécessite probablement l’assistance d’un informaticien compétent de votre service informatique. Celui-ci sait comment déclencher précisément l’implémentation de l’aperçu rapide à l’aide de l’étape appropriée, avec une URL d’aperçu rapide prête à l’emploi.

Vous pouvez découvrir comment ces étapes sont appliquées au site web de démonstration pour l’intégration complète d’une image interactive publicitaire avec le code d’aperçu rapide. Auparavant, la structure de l’URL d’aperçu rapide était identifiée comme suit :

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

Le dernier site web de démonstration avec l’image interactive entièrement intégrée ressemble à ce qui suit :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html?lang=fr](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html?lang=fr)

## Utilisation d’aperçus rapides pour créer des fenêtres contextuelles personnalisées {#using-quickviews-to-create-custom-pop-ups}

Voir [Création de fenêtres contextuelles personnalisées à l’aide d’aperçus rapides](custom-pop-ups.md).
