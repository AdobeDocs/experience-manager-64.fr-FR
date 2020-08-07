---
title: Utilisation de scènes IBL
seo-title: Utilisation de scènes IBL
description: AEM 3D prend en charge l’éclairage par image (IBL, Image-based lighting) pour l’affichage et le rendu interactifs avec le convertisseur intégré Adobe Rapid Refine™ et les convertisseurs tiers.
seo-description: AEM 3D prend en charge l’éclairage par image (IBL, Image-based lighting) pour l’affichage et le rendu interactifs avec le convertisseur intégré Adobe Rapid Refine™ et les convertisseurs tiers.
uuid: 495ba9cc-02f5-4ce5-9503-9f61ca5482db
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 658ff671-16b9-41bd-ba24-b77a32b3346b
translation-type: tm+mt
source-git-commit: 5964edfadf597652f754ca3c64343b0b90e40796
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 58%

---


# Utilisation de scènes IBL {#about-working-with-ibl-stages}

AEM 3D prend en charge l’éclairage par image (IBL, Image-based lighting) pour l’affichage et le rendu interactifs avec le convertisseur intégré Adobe Rapid Refine™ et les convertisseurs tiers. Vous pouvez créer des scènes IBL avec des outils de création courants tels qu’Autodesk® Maya® ou Autodesk® 3ds Max®.

## Images IBL {#images-for-ibl}

Pour de meilleurs résultats, les images utilisées pour l’éclairage par image doivent être en HDR. Elles doivent être au format lat./long. avec un mappage sphérique couvrant l’environnement dans son intégralité.

Actuellement, AEM 3D prend uniquement en charge les fichiers TIFF 32 bits. Si nécessaire, utilisez Adobe Photoshop ou un outil similaire pour convertir l’image HDR au format TIFF à l’aide des paramètres suivants dans la boîte de dialogue d’exportation TIFF d’Adobe Photoshop :

* **[!UICONTROL Profondeur]** de bits - 32 bits (flottant)
* **[!UICONTROL Ordre]** des pixels - Entrelacé (RGBRGB)
* **[!UICONTROL Compression]** d’images - LZW
* **[ !Ordre** des octets UICONTROL - PC IBM

Bien qu’une seule image HDR soit souvent suffisante pour les scènes IBL, AEM 3D offre un contrôle supplémentaire sur les effets IBL en autorisant jusqu’à trois images distinctes :

* **Image** d&#39;Environnement d&#39;éclairage diffus - Ce type d&#39;image doit être une image HDR, mais peut être relativement petite, car l&#39;image sera fortement filtrée avant de l&#39;utiliser pour l&#39;éclairage diffus.
* **Image** d&#39;Environnement de réflexion : ce type d&#39;image est utilisé pour créer des reflets sur les surfaces d&#39;objet. Il peut s’agir d’une image RVB 8 bits standard d’une taille et d’une résolution permettant d’obtenir la qualité souhaitée et des reflets nets. Si une image HDR est spécifiée, AEM 3D la convertit en RVB 8 bits avant d’utiliser un algorithme propriétaire.
* **Image** d&#39;Environnement d&#39;arrière-plan - Ce type d&#39;image est utilisé comme arrière-plan. Il peut s’agir d’une image RVB 8 bits standard. La taille/la résolution/le niveau de détail doivent correspondre aux valeurs souhaitées pour l’arrière-plan de la scène. Si une image HDR est spécifiée, AEM 3D la convertit en image RVB 8 bits à l’aide d’un algorithme propriétaire.

>[!NOTE]
>
>L’algorithme de conversion peut rencontrer des difficultés avec certaines images IBL. Par conséquent, certains arrière-plans peuvent être trop lumineux ou saturés en mode Aperçu ou lors du rendu avec Rapid Refine. Dans ces circonstances, Adobe vous recommande d’utiliser Photoshop ou un outil similaire pour convertir manuellement l’image IBL en image RVB 8 bits. Chargez cette image séparément et joignez-la à la scène en tant qu’image d’environnement d’arrière-plan. Les images d’environnement d’éclairage diffus et de reflet doivent toujours être au format TIFF 32 bits.

## Modification de l’aspect de la scène IBL {#adjusting-the-ibl-stage-appearance}

Vous pouvez modifier l’aspect de la scène IBL grâce aux propriétés de scène suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriété</strong><br /> </td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>Détails de l'IBL Sun</td> 
   <td><p>Permet d'ajuster la direction et la force de la source lumineuse supplémentaire qui simule le soleil. <span class="diff-html-added">Cette source lumineuse augmente la luminosité de l’éclairage et fait en sorte que l’objet diffuse une ombre portée sur le sol. La projection d’ombre est prise en charge lors du rendu avec Rapid Refine et pour une prévisualisation avec Google Chrome. Toutefois, elle n’est actuellement pas prise en charge par les autres navigateurs.</span></p> 
    <ul> 
     <li><strong>lat</strong> - Position verticale de la source de lumière du soleil (<code>0.0</code>-<code>1.0</code>).<br /> Un paramètre de <code>0.0</code> est à l'horizon (centre vertical de l'image de l'Environnement d'éclairage diffus); <code>1.0</code> est au zénith (bord supérieur de l'Environnement d'éclairage diffus).</li> 
     <li><strong>long</strong> - Position horizontale de la source de lumière du soleil (<code>0.0</code>-<code>1.0</code>).<br /> Un paramètre de 0,0 correspond à gauche ; 1.0 correspond au bord droit de l'Environnement d'éclairage diffus.<br /> </li> 
     <li><strong>clair</strong> - Luminosité de la source de lumière du soleil. Augmentez cette valeur pour éclaircir la source lumineuse et réduisez-la pour l’assombrir. <br /> Un paramètre de <code>0</code> désactivation de l’éclairage supplémentaire et désactive les ombres projetées. Le paramètre n’affecte pas les reflets de l’environnement.<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Hauteur de la caméra IBL</td> 
   <td>Si l'arrière-plan IBL apparaît déformé près de l'horizon, il est possible de réduire ou d'éliminer la distorsion en ajustant cette propriété. <br /> </td> 
  </tr> 
  <tr> 
   <td>Éclairage des Environnements</td> 
   <td><p><span class="diff-html-added">Permet de contrôler l’éclairage diffus. Vous devrez peut-être régler cette propriété manuellement pour corriger la luminosité de l’éclairage si l’image Environnement d’éclairage diffus est anormalement claire ou sombre (pour les scènes nocturnes, par exemple).</span></p> 
    <ul> 
     <li><strong>r, g, b</strong> - Actuellement non utilisé.</li> 
     <li><strong>clair</strong> - multiplicateur <span class="diff-html-added">de luminosité. Ajustez cette valeur pour augmenter ou réduire l’intensité lumineuse globale (éclairage de base IBL et luminosité de la source lumineuse solaire).</span></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Augmentation du diamètre d&#39;arrière-plan sphérique d&#39;une étape IBL {#increasing-the-spherical-background-diameter-of-an-ibl-stage}

Les étapes IBL utilisent des images d&#39;arrière-plan sphériques de 20 mètres de diamètre par défaut. Ces étapes fonctionnent bien pour les objets jusqu&#39;à 10 mètres. Cependant, si vous affichez des objets plus grands, vous pouvez augmenter le diamètre d’arrière-plan sphérique d’une scène IBL.

**Pour augmenter le diamètre d&#39;arrière-plan sphérique d&#39;une scène** IBL :

1. En CRXDE Lite, accédez à la scène dont vous souhaitez augmenter le diamètre d’arrière-plan sphérique. Par exemple :

   `/content/dam/test3d/stage-helipad.fbx`

1. Développez le noeud stage en `jcr:content/metadata`.
1. Définissez la propriété `dam:gPlaneRadius` sur la valeur de millimètre souhaitée.

   Pour optimiser l’efficacité du rendu, l’Adobe vous recommande de limiter cette valeur à environ la dimension la plus grande de l’objet le plus grand que vous avez l’intention d’afficher sur la scène.

   Par exemple, un modèle d&#39;avion à réaction de 20 mètres de long s&#39;affiche bien si `dam:gPlaneRadius=20000`.

1. Near the upper-left corner of the CRXDE Lite page, tap **[!UICONTROL Save All]**.

