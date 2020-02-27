---
title: Aperçu de ressources Dynamic Media
seo-title: Aperçu de ressources Dynamic Media
description: Découvrez comment prévisualiser des fichiers dans Contenu multimédia dynamique
seo-description: Découvrez comment prévisualiser des fichiers dans Contenu multimédia dynamique
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402

---


# Aperçu de ressources Dynamic Media {#previewing-assets}

You can use **[!UICONTROL Preview]** to see how a Dynamic Media digital asset looks when it is viewed by a customer in their own web browser. The default embedded, cross-device viewer that is assigned to the asset is used for the **[!UICONTROL Preview]**.

Une visionneuse est un ensemble de paramètres ou de « paramètres prédéfinis », tels que la taille d’affichage de la visionneuse, le comportement du zoom, les modèles de couleurs, les bordures et les polices, qui déterminent la manière dont les utilisateurs voient le contenu multimédia enrichi sur leurs écrans d’ordinateur et appareils mobiles.

Outre l’utilisation de la fonction d’aperçu dédiée pour la vidéo, les visionneuses à 360° et les visionneuses d’images, vous pouvez également prévisualiser un fichier à l’aide des paramètres prédéfinis de visionneuse que vous avez créés. Vous pouvez également utiliser des paramètres d’image prédéfinis pour prévisualiser les rendus d’images.

* [Application de paramètres d’image prédéfinis](image-presets.md)
* [Application de paramètres prédéfinis de la visionneuse](viewer-presets.md)

>[!NOTE]
>
>Lorsque vous vous trouvez sur une page web (Sites) dans AEM, vous ne pouvez pas prévisualiser les ressources en mode d’**[!UICONTROL édition]**. Vous devez accéder au mode **[!UICONTROL Aperçu]** en cliquant sur **Aperçu** dans le coin supérieur droit.

**Pour prévisualiser des fichiers**:

1. From **Adobe Experience Manager**, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Asset]s **, then**[!UICONTROL Files ]**to access assets.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL List View]**.
1. (Facultatif) Utilisez la colonne **[!UICONTROL Type]** pour trier les ressources en fonction du type que vous souhaitez prévisualiser.
1. Sous la colonne **[!UICONTROL Titre]**, cliquez sur le nom du titre (et non sur l’image miniature) de la ressource à prévisualiser.
1. Selon le type de ressource sur lequel vous avez cliqué, procédez de l’une des manières suivantes :

<table> 
 <tbody>
  <tr>
   <td><strong>Type de ressource sur lequel vous avez appuyé</strong><br /> </td> 
   <td><strong>Est-il possible d’afficher un aperçu de la ressource dans un rendu particulier ?</strong></td> 
   <td><strong>Est-il possible d’afficher un aperçu de la ressource dans une visionneuse particulière ?</strong></td> 
  </tr>
  <tr>
   <td><p>Image</p> </td> 
   <td>Oui</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans un rendu particulier</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Rendus</strong> dans la liste, puis sélectionnez un rendu spécifique à prévisualiser.</li> 
    </ul> <p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un appareil mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous avez atteint le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser le zoom. Placez-vous sur l’image et faites glisser pour effectuer un panoramique.</p> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimédia</td> 
   <td>Oui</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans un rendu particulier</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Rendus</strong> dans la liste, puis sélectionnez un rendu spécifique à prévisualiser.</li> 
    </ul> <p>Si vous sélectionnez un rendu vidéo haute résolution à prévisualiser, la vidéo risque d’être tronquée. En effet, l’aperçu du rendu vous montre la résolution exacte que vos clients verront, tout cela dans le contexte de la visionneuse intégrée utilisée pour l’aperçu.</p> <p>Lorsque vous prévisualisez une visionneuse de vidéos adaptative au niveau du fichier, les rendus sont regroupés en une seule expérience de lecture. That is, the adaptive video is sized properly for viewing and played back using the best resolution in the context of your viewing device and connection speed.<br /> </p> <p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse d’images</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un appareil mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous avez atteint le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser le zoom. Placez-vous sur l’image et faites glisser pour effectuer un panoramique.</p> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse à 360°</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un appareil mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous avez atteint le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser le zoom. Placez-vous sur l’image et faites glisser pour effectuer un panoramique.</p> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse de médias mixtes</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un appareil mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous avez atteint le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser le zoom. Placez-vous sur l’image et faites glisser pour effectuer un panoramique.</p> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
  <tr>
   <td>Ensemble de carrousel</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>To enable or disable viewer presets in the user interface, see <a href="/help/assets/managing-viewer-presets.md">Managing Viewer Presets</a>.</p> </td> 
  </tr>
 </tbody>
</table>

