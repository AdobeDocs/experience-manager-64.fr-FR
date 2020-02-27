---
title: Affichage de ressources 3D
seo-title: Affichage de ressources 3D
description: Apprenez-en davantage sur la visionneuse 3D interactive disponible sur la page de détails de la ressource dans AEM, ainsi que sur son utilisation pour afficher des ressources 3D.
seo-description: Apprenez-en davantage sur la visionneuse 3D interactive disponible sur la page de détails de la ressource dans AEM, ainsi que sur son utilisation pour afficher des ressources 3D.
uuid: 7d8133ac-3110-4979-8e19-e65090e791be
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 65040923-a8a8-4e27-82c0-67a04348e238
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f

---


# Affichage de ressources 3D {#viewing-d-assets}

Ce document décrit comment afficher les ressources 3D sur la page Détails de l’actif et comment afficher les ressources qui se trouvent dans le composant Sites 3D.

## Affichage des ressources 3D sur la page Détails de l’actif {#viewing-d-assets-in-the-asset-details-page}

La visionneuse 3D interactive est disponible sur la page de détails de la ressource dans AEM. La visionneuse comprend, entre autres, un ensemble de contrôles de caméra interactifs qui permettent d’orbiter, de zoomer et de faire un panoramique sur la ressource 3D.

![chlimage_1-139](assets/chlimage_1-139.png)

En plus d’utiliser les scènes par défaut dans AEM 3D, vous pouvez utiliser des scènes que vous avez créées dans une application tierce et chargées dans AEM.

Voir [Utilisation de scènes dans AEM 3D](about-the-use-of-stages-in-aem-3d.md).

>[!NOTE]
>
>Pour afficher une ressource 3D, le navigateur de votre appareil ou de votre ordinateur de bureau doit être compatible avec WebGL. En outre, les capacités et la mémoire du matériel vidéo sous-jacent doivent être suffisantes pour effectuer le rendu de modèles de la taille et de la complexité souhaitées. Certaines fonctionnalités d’aperçu, telles que la projection d’ombres, ne sont pas disponibles sur tous les navigateurs.

### Facteurs de performance lors de l’affichage de ressources 3D {#performance-considerations-when-you-view-d-assets}

Le délai nécessaire pour ouvrir une ressource 3D sur la page de détails de la ressource dépend de plusieurs facteurs. Ces facteurs sont entre autres :

* Bande passante et latences du serveur
* Taille du modèle (nombre de faces)
* Nombre et taille des correspondances
* Complexité de la scène. Par exemple, la taille de l’image IBL

En outre, les fonctionnalités de l’ordinateur client (station de travail, ordinateur portable ou appareil tactile mobile, par exemple) sont également importantes à prendre en compte lorsque vous manipulez l’appareil de manière interactive. Un système relativement puissant avec de bonnes capacités graphiques peut rendre l’expérience interactive d’affichage en 3D plus fluide et plus favorable.

**Pour afficher des fichiers** 3D :

1. Assurez-vous d’avoir chargé des ressources 3D dans AEM.

   Reportez-vous à la section [À propos du téléchargement et du traitement des ressources 3D dans AEM](upload-processing-3d-assets.md).

1. From AEM, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Assets]**.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL Card View]**.
1. Accédez à une ressource 3D que vous souhaitez afficher.
1. Appuyez sur la carte de la ressource 3D pour l’ouvrir sur la page Détails de l’actif.
1. Procédez de l’une des manières suivantes :

   * Dans le coin inférieur droit de la page de détails de la ressource, utilisez la palette de commandes de caméra pour modifier différents affichages de la ressource.

      Si vous utilisez un périphérique d’entrée non tactile sans roulette de défilement, par exemple une souris à un bouton Apple classique, vous pouvez tout de même modifier le zoom ou la perspective d’une ressource 3D dans chaque mode respectif. You accomplish the action by pressing and holding down the `SHIFT`key while depressing the mouse button and dragging up or down.

      Lorsque vous utilisez un pavé tactile sur un ordinateur portable classique, il est souvent difficile de contrôler le comportement du zoom ou de la perspective à l’aide du geste à deux doigts. In such cases, you can press and hold down `SHIFT`during the action. Cela réduit la vitesse du geste de pincement et permet d’obtenir plus facilement la perspective ou le facteur de zoom exact que vous souhaitez. Alternately, you can use a one finger drag up or down while the `SHIFT`key is pressed to affect zoom or perspective behaviors.
   <table> 
    <tbody> 
      <tr> 
      <td><strong>Nom du contrôle de l’appareil photo</strong><br /> </td> 
      <td><strong>Description</strong></td> 
      </tr> 
      <tr> 
      <td><p>Zoom</p> <p>ou</p> <p>Persp</p> </td> 
      <td><p>Appuyez ou cliquez pour basculer entre les modes Zoom et Perspective.</p> <p>Or, press and hold down the <code>ALT/OPTION</code> key during the action to temporarily toggle to Perspective<br /> mode. Relâchez la touche pour revenir en mode Zoom.</p> 
      <ul> 
      <li><strong>Comportement Zoom</strong>-Dolly en entrée et en sortie qui rapproche ou éloigne la caméra de la ressource<br /> que vous visualisez. Zoom est le comportement par défaut de la roulette de défilement d’une souris (le cas échéant) pour les gestes de pincement à deux doigts sur les appareils mobiles ou lorsque vous appuyez de manière prolongée sur la touche Maj tout en faisant glisser vers le haut ou vers le bas à l’aide du bouton gauche de la souris.</li> 
      <li><strong>Perspective</strong>-Modifie la distance focale (également appelée champ de vision) de la caméra tout en conservant la taille relative de la ressource dans la vue. Perspective est le comportement alternatif de la roulette de défilement (le cas échéant) pour les gestes de pincement à deux doigts sur les appareils mobiles ou lorsque vous appuyez de manière prolongée sur la touche Maj tout en faisant glisser vers le haut ou vers le bas à l’aide du bouton gauche de la souris.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Orbite</p> <p>ou</p> <p>Panoramique</p> </td> 
      <td><p>Appuyez ou cliquez pour basculer entre les modes Orbite et Panoramique.</p> <p>Or, press and hold the <code>ALT/OPTION</code> key during the action to temporarily toggle to Pan mode. Relâchez la touche pour revenir en mode Orbite.</p> 
      <ul> 
      <li><strong>Orbite</strong>- Déplace la caméra de visualisation sur une sphère centrée sur un point cible situé près du centre de la ressource 3D par défaut. Orbite est le comportement par défaut pour un glisser avec le bouton gauche ou un glisser par un seul toucher sur les appareils mobiles.</li> 
      <li><strong>Panoramique</strong>-Déplace la caméra dans le plan de visualisation. Le point cible est déplacé en conséquence. Ainsi, les actions d’orbite suivantes déplaceront la caméra autour d’un nouveau point cible. Panoramique est le comportement alternatif pour le glisser avec le bouton gauche et le glisser par un seul toucher.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Examen</p> <p>ou</p> <p>Cible</p> </td> 
      <td><p>Appuyez ou cliquez pour basculer entre les modes Examen et Target.</p> 
      <ul> 
      <li><strong>Examinez</strong>-Appuyez ou cliquez pour passer en mode Target.</li> 
      <li><strong>Target</strong>-Appuyez ou cliquez sur un point n’importe où sur la ressource 3D pour centrer la vue sur cette partie de la ressource.<br /> Les actions d’orbite utilisent le nouveau point cible.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>Réinitialiser</td> 
      <td>Appuyez ou cliquez pour rétablir le point cible de la vue au centre du modèle. Reset also moves the camera<br /> closer or further away to show the asset in its entirety and at a reasonable viewing size.</td> 
      </tr> 
    </tbody> 
    </table>

   * Near the upper-right corner of the asset details page, tap the **[!UICONTROL Stage Selector]** icon. Sélectionnez un nom de scène avec l’arrière-plan et l’éclairage à appliquer à la ressource 3D.
   ![chlimage_1-140](assets/chlimage_1-140.png)

   Les étapes fournissent l’environnement, l’arrière-plan, le plan au sol et l’éclairage dans lesquels le modèle 3D est affiché.

   Voir [Utilisation de scènes dans AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   * Near the upper-right corner of the asset details page, tap the **[!UICONTROL Camera Selector]** icon, then select a camera view that you want to apply to the 3D asset.
   ![chlimage_1-141](assets/chlimage_1-141.png)

   Les scènes fournissent souvent des caméras prédéfinies. Vous pouvez sélectionner à nouveau la caméra actuelle pour restaurer ses paramètres prédéfinis.

   Voir [Utilisation de scènes dans AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer]**.
1. Utilisez l’une des méthodes suivantes :

   * Effectuez le rendu de la ressource 3D.

      Voir [Rendu des ressources 3D](rendering-3d-assets.md).

   * Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Fermer]** pour revenir à la page Assets.

## Affichage des ressources 3D dans le composant Sites 3D {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>Cette section s’applique uniquement au lecteur webGL classique utilisé pour les types de ressources 3D autres qu’Adobe Dimension.

Selon le type de périphérique, vous accédez aux fonctions du composant 3D de diverses façons.

Pour plus d’informations, consultez les sections suivantes :

* [Périphériques dotés d’un écran tactile](#touchscreen-devices)
* [Périphériques dotés d’un pavé tactile](#touchpad-devices)
* [Périphériques dotés d’une souris ou d’un trackball](#mouse-and-trackball-devices)

Voir aussi [Prévisualisation d’une page Web comportant un composant](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component)3D.

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### Périphériques dotés d’un écran tactile {#touchscreen-devices}

Pour utiliser des composants 3D avec des périphériques dotés d’un écran tactile :

1. Faites glisser votre doigt sur l’écran, ou balayez l’écran d’un doigt, pour déplacer (« satelliser ») le point de vue (la « caméra ») autour de l’objet. Vous pouvez afficher l’objet dans n’importe quelle direction.

1. Effectuez un pincement de deux doigts à l’écran pour rapprocher ou éloigner la caméra de l’objet. Cette action est similaire au zoom avant ou arrière et permet d’inspecter les détails de l’objet. Vous pouvez également appuyer sur les boutons + ou - et maintenir la pression pour rapprocher ou éloigner la caméra de l’objet.

1. Utilisez un glissement à deux doigts pour faire un panoramique avec la caméra. Cette action déplace la caméra latéralement afin de vous permettre de visualiser différentes parties de l’objet au cours d’un zoom avant. Alternatively, tap the **[!UICONTROL Orbit/Pan Toggle]** button to toggle to Pan mode, then use a one-finger drag to pan the camera. Tap the **[!UICONTROL Orbit/Pan Toggle]** button to revert to **[!UICONTROL Orbit]** mode.

1. Appuyez sur **[!UICONTROL Réinitialiser la visionneuse]** pour réinitialiser la caméra. Cette action replace l’objet en plein écran et, si elle est activée, reprend la rotation automatique.

1. Appuyez sur **[!UICONTROL Plein écran]** pour passer en mode plein écran (s’il est pris en charge par le périphérique). Appuyez sur **[!UICONTROL Plein écran]** à nouveau pour restaurer la visionneuse 3D en mode de page incorporée.

### Périphériques dotés d’un pavé tactile {#touchpad-devices}

Pour utiliser des composants 3D avec des périphériques dotés d’un pavé tactile :

1. Faites glisser votre doigt, tout en maintenant la pression sur le bouton (gauche) du pavé tactile, pour déplacer (« satelliser ») le point de vue (la « caméra ») autour de l’objet. Vous pouvez afficher l’objet dans n’importe quelle direction.

1. Faites glisser deux doigts vers le bas ou le haut, sans appuyer sur les boutons du pavé tactile, pour rapprocher ou éloigner la caméra de l’objet. Cette action est similaire au zoom avant ou arrière et vous permet d’inspecter les détails de l’objet. Alternatively, click and hold the **[!UICONTROL Zoom In]** or **[!UICONTROL Zoom Out]** buttons to move the camera closer or farther away from the object.

1. Use a one-finger drag while holding the **ALT/option** key and the (left) touchpad button to pan the camera. Cette action déplace la caméra latéralement afin de vous permettre de visualiser différentes parties de l’objet au cours d’un zoom avant. Alternatively, click the **[!UICONTROL Orbit/Pan Toggle]** button to toggle to **[!UICONTROL Pan]** mode, then use a one-finger drag while holding the (left) button to pan the camera. Click the **[!UICONTROL Orbit/Pan Toggle]** button again to revert to **[!UICONTROL Orbit]** mode.

1. Click **[!UICONTROL Reset Viewer]** to reset the camera. Cette action replace l’objet en plein écran et, si elle est activée, reprend la rotation automatique.

1. Click **[!UICONTROL Full Screen]** to enter full-screen mode. Use the **Escape** key on your keyboard or click **[!UICONTROL Full Screen]** again to restore the 3D viewer to page-embedded mode.

### Périphériques dotés d’une souris ou d’un trackball {#mouse-and-trackball-devices}

Pour utiliser des composants 3D avec des périphériques dotés d’une souris ou d’un trackball :

1. Faites glisser la souris ou le trackball, tout en maintenant la pression sur le bouton gauche de la souris, pour déplacer (« placer en orbite ») le point de vue (la « caméra ») autour de l’objet. Vous pouvez afficher l’objet dans n’importe quelle direction.

1. Utilisez la roulette de défilement pour rapprocher ou éloigner la caméra de l’objet. Cette action est similaire au zoom avant ou arrière et vous permet d’inspecter les détails de l’objet. Alternatively, click and hold the **[!UICONTROL Zoom In]** or **[!UICONTROL Zoom Out]** buttons to move the camera closer or farther away from the object.

1. Drag while holding the **ALT/option** key and the left mouse button to pan the camera. Cette action déplace la caméra latéralement afin de vous permettre de visualiser différentes parties de l’objet au cours d’un zoom avant. Alternatively, click the **[!UICONTROL Orbit/Pan Toggle]** button to toggle to **[!UICONTROL Pan]** mode, then drag while holding the left mouse button to pan the camera. Click the **[!UICONTROL Orbit/Pan Toggle]** again to revert to **[!UICONTROL Orbit]** mode.
1. Click **[!UICONTROL Reset Viewer]** to reset the camera. Cette action replace l’objet en plein écran et, si elle est activée, reprend la rotation automatique.
1. Click **[!UICONTROL Full Screen]** to enter full-screen mode. Use the **[!UICONTROL Escape]** key on your keyboard or click **[!UICONTROL Full Screen]** again to restore the 3D viewer to page-embedded mode.

