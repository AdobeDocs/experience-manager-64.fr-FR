---
title: Prévisualisation de ressources Dynamic Media
seo-title: Prévisualisation de ressources Dynamic Media
description: Découvrez comment prévisualiser des ressources dans Dynamic Media
seo-description: Découvrez comment prévisualiser des ressources dans Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 90%

---


# Prévisualisation de ressources Dynamic Media {#previewing-assets}

Vous pouvez utiliser **[!UICONTROL Prévisualisation]** pour voir à quoi ressemble un fichier numérique Dynamic Media lorsqu’il est affiché par un client dans son propre navigateur Web. La visionneuse multipériphériques incorporée par défaut affectée à la ressource est utilisée pour la **[!UICONTROL Prévisualisation]**.

Une visionneuse est un ensemble de paramètres ou de « paramètres prédéfinis », tels que la taille d’affichage de la visionneuse, le comportement du zoom, les modèles de couleurs, les bordures et les polices, qui déterminent la manière dont les utilisateurs voient le contenu multimédia enrichi sur leurs écrans d’ordinateur et appareils mobiles.

Outre l’utilisation de la fonction de prévisualisation dédiée pour la vidéo, les visionneuses à 360° et les visionneuses d’images, vous pouvez également prévisualisation d’un fichier à l’aide des paramètres prédéfinis de visionneuse que vous avez créés. Vous pouvez également utiliser des paramètres d’image prédéfinis pour prévisualisation des rendus d’images.

* [Application de paramètres d’image prédéfinis](image-presets.md)
* [Application de paramètres prédéfinis de la visionneuse](viewer-presets.md)

>[!NOTE]
>
>Lorsque vous vous trouvez sur une page web (Sites) dans AEM, vous ne pouvez pas prévisualiser les ressources en mode d’**[!UICONTROL édition]**. Vous devez accéder au mode **[!UICONTROL Aperçu]** en cliquant sur **Aperçu** dans le coin supérieur droit.

**Prévisualisation d’une ressource**:

1. À partir de **Adobe Experience Manager**, sur la page **[!UICONTROL Navigation]**, appuyez sur **[!UICONTROL Asset]s**, puis **[!UICONTROL Files]** pour accéder aux ressources.
1. Dans le coin supérieur droit de la page, dans la liste déroulante **[!UICONTROL Afficher]**, appuyez sur **[!UICONTROL Mode Liste]**.
1. (Facultatif) Utilisez la colonne **[!UICONTROL Type]** pour trier les ressources en fonction du type que vous souhaitez prévisualiser.
1. Sous la colonne **[!UICONTROL Titre]**, cliquez sur le nom du titre (et non sur l’image miniature) de la ressource à prévisualiser.
1. Selon le type de ressource sur lequel vous avez cliqué, procédez de l’une des manières suivantes :

<table> 
 <tbody>
  <tr>
   <td><strong>Type de ressource que vous avez sélectionné</strong><br /> </td> 
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
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un appareil mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous avez atteint le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser le zoom. Placez-vous sur l’image et faites glisser pour effectuer un panoramique.</p> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimédia</td> 
   <td>Oui</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans un rendu particulier</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Rendus</strong> dans la liste, puis sélectionnez un rendu spécifique à prévisualiser.</li> 
    </ul> <p>La vidéo peut apparaître tronquée si vous sélectionnez une résolution plus élevée pour le rendu vidéo. En effet, l’aperçu du rendu vous indique la résolution exacte que vos clients verront, le tout dans le contexte de la visionneuse incorporée utilisée pour l’aperçu.</p> <p>Lorsque vous prévisualisez un ensemble de vidéos adaptables au niveau des ressources, les rendus sont regroupés en une seule lecture. C’est-à-dire que la vidéo adaptable est dimensionnée de manière appropriée pour le visionnage et est lue avec la meilleure résolution possible pour l’appareil de visionnage et la vitesse de connexion utilisés.<br /> </p> <p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse d’images</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un appareil mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous avez atteint le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser le zoom. Placez-vous sur l’image et faites glisser pour effectuer un panoramique.</p> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse à 360°</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un appareil mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous avez atteint le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser le zoom. Placez-vous sur l’image et faites glisser pour effectuer un panoramique.</p> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
  </tr>
  <tr>
   <td>Visionneuse de médias mixtes</td> 
   <td>Non</td> 
   <td>Oui</td> 
   <td><p><strong>Pour prévisualiser une ressource dans une visionneuse particulière</strong></p> 
    <ul> 
     <li>En haut à gauche de la page, cliquez sur l’icône pour afficher la liste déroulante. Cliquez sur <strong>Visionneuses</strong> dans la liste, puis sélectionnez une visionneuse à appliquer à la ressource.</li> 
    </ul> <p>Utilisez les icônes <strong>+</strong> et <strong>-</strong> pour augmenter ou réduire le zoom de l’image sélectionnée. Cliquez sur <strong>Réinitialiser</strong> pour rétablir l’image sur le zoom d’origine.<br /> Si vous utilisez un appareil mobile, appuyez deux fois sur l’image pour effectuer un zoom avant par étapes. Lorsque vous avez atteint le zoom maximal, appuyez à nouveau deux fois sur l’image pour réinitialiser le zoom. Placez-vous sur l’image et faites glisser pour effectuer un panoramique.</p> <p>Pour activer ou désactiver les paramètres prédéfinis de visionneuse dans l’interface utilisateur, voir <a href="/help/assets/managing-viewer-presets.md">Gestion des paramètres prédéfinis de visionneuse</a>.</p> </td> 
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

