---
title: Aperçu de ressources Dynamic Media
seo-title: Previewing Dynamic Media assets
description: Découvrez comment prévisualiser des ressources dans Dynamic Media
seo-description: Learn how to preview assets in Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 55%

---

# Aperçu de ressources Dynamic Media {#previewing-assets}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez utiliser **[!UICONTROL Aperçu]** pour voir à quoi ressemble une ressource numérique Dynamic Media lorsqu’elle est affichée par un client dans son propre navigateur web. La visionneuse multi-appareils incorporée par défaut qui est affectée à la ressource est utilisée pour la variable **[!UICONTROL Aperçu]**.

Une visionneuse est un ensemble de différents paramètres ou &quot;paramètres prédéfinis&quot;, tels que la taille d’affichage de la visionneuse, le comportement du zoom, les schémas de couleurs, les bordures, les polices, etc., qui déterminent la manière dont les utilisateurs voient les ressources multimédias enrichies sur leurs écrans d’ordinateur et appareils mobiles.

Outre l’utilisation de la fonction d’aperçu dédiée pour la vidéo, les visionneuses à 360° et les visionneuses d’images, vous pouvez également prévisualiser une ressource à l’aide des paramètres prédéfinis de visionneuse que vous avez créés. Vous pouvez également utiliser des paramètres d’image prédéfinis pour prévisualiser les rendus des images.

* [Application de paramètres d’image prédéfinis](image-presets.md)
* [Application de paramètres prédéfinis de visionneuse](viewer-presets.md)

>[!NOTE]
>
>Lorsque vous vous trouvez sur une page web (Sites) dans AEM, vous ne pouvez pas prévisualiser les ressources en mode d’**[!UICONTROL édition]**. Vous devez accéder au mode **[!UICONTROL Aperçu]** en cliquant sur **Aperçu** dans le coin supérieur droit.

**Prévisualisation d’une ressource**:

1. De **Adobe Experience Manager**, sur le **[!UICONTROL Navigation]** page, appuyez sur **[!UICONTROL Ressource]s**, puis **[!UICONTROL Fichiers]** pour accéder aux ressources.
1. Dans le coin supérieur droit de la page, dans la liste déroulante **[!UICONTROL Afficher]**, appuyez sur **[!UICONTROL Vue Liste]**.
1. (Facultatif) Utilisez la colonne **[!UICONTROL Type]** pour trier les ressources en fonction du type que vous souhaitez prévisualiser.
1. Sous , **[!UICONTROL Titre]** , cliquez sur le nom du titre (et non sur l’image miniature) de la ressource à prévisualiser.
1. Selon le type de ressource sur lequel vous avez cliqué, effectuez l’une des opérations suivantes :

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
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Rendus </strong>dans la liste, sélectionnez un rendu particulier à prévisualiser.</li> 
    </ul> <p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un périphérique mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous atteignez le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser l’état du zoom. Faites glisser sur l’image pour effectuer un panoramique.</p> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimédia</td> 
   <td>Oui</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans un rendu particulier</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Rendus </strong>dans la liste, sélectionnez un rendu particulier à prévisualiser.</li> 
    </ul> <p>La vidéo peut apparaître tronquée si vous sélectionnez une résolution plus élevée pour le rendu vidéo. En effet, l’aperçu du rendu vous indique la résolution exacte que vos clients verront, le tout dans le contexte de la visionneuse incorporée utilisée pour l’aperçu.</p> <p>Lorsque vous prévisualisez un ensemble de vidéos adaptables au niveau des ressources, les rendus sont regroupés en une seule lecture. C’est-à-dire que la vidéo adaptable est dimensionnée de manière appropriée pour le visionnage et est lue avec la meilleure résolution possible pour l’appareil de visionnage et la vitesse de connexion utilisés.<br /> </p> <p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse d’images</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un périphérique mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous atteignez le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser l’état du zoom. Faites glisser sur l’image pour effectuer un panoramique.</p> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse à 360°</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un périphérique mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous atteignez le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser l’état du zoom. Faites glisser sur l’image pour effectuer un panoramique.</p> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse de supports variés</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un périphérique mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous atteignez le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser l’état du zoom. Faites glisser sur l’image pour effectuer un panoramique.</p> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
  </tr>
  <tr>
   <td>Ensemble de carrousel</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
  </tr>
 </tbody>
</table>
