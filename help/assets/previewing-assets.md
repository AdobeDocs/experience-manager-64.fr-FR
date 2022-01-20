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
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 90%

---

# Aperçu de ressources Dynamic Media {#previewing-assets}

Vous pouvez utiliser **[!UICONTROL Aperçu]** pour voir à quoi ressemble une ressource numérique Dynamic Media lorsqu’elle est affichée par un client dans son propre navigateur web. La visionneuse multi-appareils incorporée par défaut qui est affectée à la ressource est utilisée pour la variable **[!UICONTROL Aperçu]**.

Une visionneuse est un ensemble de paramètres ou de « paramètres prédéfinis », tels que la taille d’affichage de la visionneuse, le comportement du zoom, les modèles de couleurs, les bordures et les polices, qui déterminent la manière dont les utilisateurs voient le contenu multimédia enrichi sur leurs écrans d’ordinateur et appareils mobiles.

Outre l’utilisation de la fonction d’aperçu dédiée pour la vidéo, les visionneuses à 360° et les visionneuses d’images, vous pouvez également prévisualiser une ressource à l’aide des paramètres prédéfinis de visionneuse que vous avez créés. Vous pouvez également utiliser des paramètres d’image prédéfinis pour prévisualiser les rendus des images.

* [Application de paramètres d’image prédéfinis](image-presets.md)
* [Application de paramètres prédéfinis de visionneuse](viewer-presets.md)

>[!NOTE]
>
>Lorsque vous vous trouvez sur une page web (Sites) dans AEM, vous ne pouvez pas prévisualiser les ressources en mode d’**[!UICONTROL édition]**. Vous devez accéder au mode **[!UICONTROL Aperçu]** en cliquant sur **Aperçu** dans le coin supérieur droit.

**Prévisualisation d’une ressource**:

1. De **Adobe Experience Manager**, sur le **[!UICONTROL Navigation]** page, appuyez sur **[!UICONTROL Ressource]s**, puis **[!UICONTROL Fichiers]** pour accéder aux ressources.
1. Dans le coin supérieur droit de la page, dans la liste déroulante **[!UICONTROL Afficher]**, appuyez sur **[!UICONTROL Mode Liste]**.
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
