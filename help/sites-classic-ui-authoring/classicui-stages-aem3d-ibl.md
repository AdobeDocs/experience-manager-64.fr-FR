---
title: Utilisation de scènes IBL
seo-title: À propos de l’utilisation des scènes IBL
description: AEM 3D prend en charge la technique d’éclairage à base d’images (IBL) pour le rendu et la visualisation interactive avec le moteur de rendu Adobe Rapid Refine intégré et les moteurs de rendu tiers. Vous pouvez créer des scènes IBL avec des outils de création courants tels qu’Autodesk Maya ou Autodesk 3ds Max.
seo-description: AEM 3D prend en charge la technique d’éclairage à base d’images (IBL) pour le rendu et la visualisation interactive avec le moteur de rendu Adobe Rapid Refine intégré et les moteurs de rendu tiers. Vous pouvez créer des scènes IBL avec des outils de création courants tels qu’Autodesk Maya ou Autodesk 3ds Max.
uuid: 6598fb8a-65b0-4b84-8063-fdc94f6ea935
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f9291151-851a-4aff-a50e-a24330ee0c13
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 78%

---


# À propos de l’utilisation des scènes IBL{#about-working-with-ibl-stages}

AEM 3D prend en charge l’éclairage par image (IBL, Image-based lighting) pour l’affichage et le rendu interactifs avec le convertisseur intégré Adobe Rapid Refine™ et les convertisseurs tiers. Vous pouvez créer des scènes IBL avec des outils de création courants tels qu’Autodesk® Maya® ou Autodesk® 3ds Max®.

## Images IBL {#images-for-ibl}

Pour de meilleurs résultats, les images utilisées pour l’éclairage par image doivent être en HDR. Elles doivent être au format lat./long. avec un mappage sphérique couvrant l’environnement dans son intégralité.

Actuellement, AEM 3D prend uniquement en charge les fichiers TIFF 32 bits. Si nécessaire, utilisez Adobe Photoshop ou un outil similaire pour convertir l’image HDR au format TIFF à l’aide des paramètres suivants dans la boîte de dialogue d’exportation TIFF d’Adobe Photoshop :

* **[!UICONTROL Profondeur]** de bits - 32 bits (flottant)
* **[!UICONTROL Ordre]** des pixels - Entrelacé (RGBRGB)
* **[!UICONTROL Compression]** d’images - LZW
* **[!UICONTROL Ordre]** des octets - IBM PC

Bien qu’une seule image HDR soit souvent suffisante pour les scènes IBL, AEM 3D offre un contrôle supplémentaire sur les effets IBL en autorisant jusqu’à trois images distinctes :

* **[!UICONTROL Image d’environnement d’éclairage diffus]** : ce type d’image doit être en HDR, mais peut être relativement petite, car elle sera fortement filtrée avant d’être utilisée pour l’éclairage diffus.
* **[!UICONTROL Image d’environnement de reflet]** : ce type d’image est utilisé pour créer des reflets sur les surfaces d’objets. Il peut s’agir d’une image RVB 8 bits standard d’une taille et d’une résolution permettant d’obtenir la qualité souhaitée et des reflets nets. Si une image HDR est spécifiée, AEM 3D la convertit en RVB 8 bits avant d’utiliser un algorithme propriétaire.
* **[!UICONTROL Image d’environnement d’arrière-plan]** : ce type d’image est utilisé en tant qu’arrière-plan. Il peut s’agir d’une image RVB 8 bits standard. La taille/la résolution/le niveau de détail doivent correspondre aux valeurs souhaitées pour l’arrière-plan de la scène. Si une image HDR est spécifiée, AEM 3D la convertit en image RVB 8 bits à l’aide d’un algorithme propriétaire.

>[!NOTE]
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

