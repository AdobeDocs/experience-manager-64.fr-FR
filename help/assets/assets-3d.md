---
title: Utilisation des ressources 3D
seo-title: Utilisation des ressources 3D
description: Découvrez comment utiliser les ressources 3D dans AEM 3D
seo-description: Découvrez comment utiliser les ressources 3D dans AEM 3D
uuid: a1c1bb29-9d3d-4025-8142-ed9719434bf9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: 32143da1-09c8-45ce-b50d-32adf6efe383
translation-type: tm+mt
source-git-commit: 7c850ed0d20dd2ba2626242c67ba190e371f049f
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 80%

---


# Utilisation des ressources 3D {#working-with-d-assets}

AEM 3D (Adobe Experience Manager 3D) est conçu pour le téléchargement, la gestion, l’affichage et le rendu du contenu 3D. La prise en charge de l’affichage et du rendu est optimisée pour les objets individuels.

Reportez-vous également à la section [Notes de mise à jour d’AEM 3D](/help/release-notes/aem3d-release-notes.md).

Reportez-vous également à la section [Installation et configuration d’AEM 3D](install-config-3d.md).

## À propos des modèles et des scènes dans AEM 3D {#about-models-and-stages-in-aem-d}

AEM 3D permet l’affichage et la création de rendus de modèles 3D autonomes et statiques de haute qualité dans des environnements prédéfinis appelés Scènes. Plus simplement, une scène permet un « éclairage » de l’objet 3D et fournit les paramètres de rendu dans une application native, par exemple, Autodesk® Maya® ou Autodesk 3ds Max®. Par ailleurs, une scène peut inclure en option des caméras, des arrière-plans et une géométrie de plan de sol prédéfinis.

Les fichiers 3D transférés contenant des éclairages sont supposés être des scènes. Si vous préférez que ces ressources redeviennent de simples objets 3D, il suffit de les ouvrir dans la page des détails du fichier. Appuyez sur **[!UICONTROL Afficher les propriétés]**, puis sur l’onglet **[!UICONTROL De base]**. Dans la liste déroulante des catégories de ressources, sous l’en-tête Métadonnées, sélectionnez **[!UICONTROL Objet 3D]**.

Lorsque vous créez des modèles 3D pour les utiliser dans AEM 3D, vérifiez les points suivants :

* Vos fichiers de modèle 3D ne doivent contenir qu’un seul objet, sans arrière-plan, plan de sol, éclairage ou caméra.
* Placez le modèle au-dessus du plan de sol. Ce positionnement est particulièrement important lorsque vous affichez le modèle ou créez un rendu avec des scènes qui fournissent un plan de sol. Un paramètre de configuration disponible (et activé par défaut) permet de déplacer l’objet au-dessus du plan de sol lors de la prévisualisation ou de la création de rendus avec Rapid Refine. Ce paramètre n’affecte pas le rendu avec d’autres outils tiers (par exemple, avec Maya). Ainsi, les objets qui ne sont pas situés au-dessus du plan de sol peuvent être partiellement masqués.
* Positionnez le modèle de façon à ce qu’il soit plus ou moins centré latéralement autour du point zéro du système de coordonnées (0,0,0). Ce positionnement vous garantit un meilleur affichage interactif.
* Outre les textures, les références des fichiers externes sont prises en charge. Vous devez donc intégrer tout contenu référencé dans le fichier de modèle principal avant de le télécharger dans AEM.

   Reportez-vous à la section [À propos du téléchargement et du traitement des ressources 3D dans AEM](upload-processing-3d-assets.md).

* L’éclairage général est fourni par la scène. En l’état, Adobe déconseille d’inclure des éclairages dans les fichiers de modèles 3D. Vous pouvez les inclure dans le modèle, mais ils doivent lui être spécifiques. Par exemple, il peut être nécessaire d’inclure un éclairage supplémentaire pour éclairer une partie de l’objet assombrie par d’autres parties. Elle ne serait en effet pas suffisamment visible uniquement avec les éclairages fournis par la scène.

## Fichiers pris en charge dans AEM 3D {#supported-files-in-aem-d}

Une ressource 3D inclut généralement un fichier de modèle principal sans aucun autre fichier de référence. Referenced files include such things as texture maps or **IBL (Image-Based Lighting)** images.

### À propos du fichier de modèle 3D principal {#about-the-primary-d-model-file}

Le fichier de modèle 3D principal contient la géométrie réelle du modèle 3D et les définitions pour les matériaux (par défaut) qui sont appliqués aux surfaces du modèle. AEM 3D prend en charge les formats de fichier de modèle 3D principal suivants :

* Format de fichier Wavefront OBJ (`.obj`)

   Le format OBJ requiert un ou plusieurs fichiers MTL externes (Bibliothèque de modèles de matériaux) (`.mtl`) distincts.

* Format de fichier Autodesk FBX (Filmbox) (`.fbx`)

   Format d&#39;échange de fichiers Autodesk 3D ; aux formats binaire et ASCII.

   Lorsque vous créez des fichiers FBX dans des applications tierces, Adobe recommande d’utiliser les paramètres de configuration suivants (voir le tableau ci-dessous). Ces paramètres vous permettent d’obtenir les meilleurs résultats pour les fichiers 3D que vous prévoyez d’utiliser dans AEM. The option names are taken from the **[!UICONTROL Autodesk Maya FBX Export Options]** dialog box.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Option dans la boîte de dialogue Exportation Autodesk Maya FBX</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>Conserver les références<br /> </td> 
   <td><p>Désélectionner.</p> <p>AEM 3D ne prend pas en charge les références externes pour l’instant.</p> </td> 
  </tr> 
  <tr> 
   <td>Maillage lisse<br /> </td> 
   <td>Sélectionner.</td> 
  </tr> 
  <tr> 
   <td>Convertir les surfaces NURBS en</td> 
   <td><strong>Maillage de rendu logiciel</strong></td> 
  </tr> 
  <tr> 
   <td>Animation</td> 
   <td><p>Sélectionnez ou désélectionnez.</p> <p>Si vous sélectionnez cette option, AEM 3D ignore les informations relatives à l’animation dans le fichier.</p> </td> 
  </tr> 
  <tr> 
   <td>Appareils photo</td> 
   <td><p>Sélectionnez cette option pour les étapes <strong></strong>3D.</p> <p>Désélectionnez cette option pour les modèles 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Lumières</td> 
   <td><p>Sélectionnez cette option pour les étapes <strong></strong>3D.</p> <p>Deselect for <strong>3D models</strong>.</p> </td> 
  </tr> 
  <tr> 
   <td>Unités - Automatique</td> 
   <td>Sélectionner. AEM 3D effectue la conversion lors de l’importation.</td> 
  </tr> 
  <tr> 
   <td>Conversion de l'axe - Axe vers le haut</td> 
   <td><p><strong>Montage Y</strong></p> <p>L'option Y-up donne des résultats cohérents lorsque vous exportez à partir de Maya et est le repère préféré pour les fichiers FBX dans cette version AEM 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Incorporer le média</td> 
   <td>Les deux options sont prises en charge. If embedded is selected, AEM 3D extracts the embedded media to an adjacent folder that has the same name as the model file with <code>.fbm</code> appended to it.</td> 
  </tr> 
  <tr> 
   <td>Format de fichier FBX - Type</td> 
   <td><strong>Binary </strong>ou <strong>ASCII </strong>sont pris en charge.</td> 
  </tr> 
  <tr> 
   <td>Format de fichier FBX - Version</td> 
   <td>FBX 2014/2015 est recommandé. D’autres versions fonctionnent également très bien.</td> 
  </tr> 
 </tbody> 
</table>

Les formats de fichier supplémentaires suivants sont pris en charge si Autodesk Maya est installé et configuré sur les serveurs de création AEM :

* Autodesk Maya

   Formats ASCII `.ma` et binaires `.mb` .

* `Jupiter Tesselation (ISO 14306-1).jt`.

   Format de visualisation du produit, de collaboration et d’échange de données de CAO.

### Prise en charge des fichiers de texture {#support-for-texture-map-files}

Les définitions de matériaux dans les fichiers de modèle 3D peuvent inclure des références vers des fichiers d’image externes qui fournissent des textures. AEM 3D prend en charge les types de fichiers de texture suivants :

* Textures de couleur diffuse
* Textures de couleur spéculaire
* Textures de couleur ambiante
* Déplacement (également appelé Texture en relief)
* Texture normale
* Texture en opacité
* Dureté (également appelés Lustre ou Texture de réflexion ou maps Cosine Power)

Les matériaux du fichier de modèle 3D principal peuvent faire référence à d’autres types de textures inconnues d’AEM 3D.

### IBL (Image-Based Lighting) images {#ibl-image-based-lighting-images}

Un fichier de modèle 3D qui définit une scène peut ne référencer qu’une seule image d’environnement IBL. Actuellement, AEM 3D ne prend en charge que les images TIFF 32 bits au format latitude/longitude pour les images IBL diffuses et les réflexions. Les images RVB 8 bits sont également prises en charge pour les arrière-plans de scène sphériques.

Reportez-vous à la section [À propos des scènes IBL](working-with-ibl-stages.md).

>[!NOTE]
>
>À l’exception de celles décrites ci-dessus, les références de fichier présentes dans le fichier de modèle 3D principal ne sont pas prises en compte pour l’instant. AEM 3D ne prend pas en charge les références vers les fichiers de modèle 3D secondaires.
Y-vertical est le système de coordonnées préféré pour les fichiers FBX dans cette version.

## Ombrage des matériaux dans un fichier de modèle 3D principal {#material-shading-in-a-primary-d-model-file}

Le fichier de modèle natif original peut contenir des définitions de matériaux utilisées avec des nuanceurs tels que Blinn, Lambert ou avec des nuanceurs procéduraux. Ces matériaux potentiellement complexes ne sont pris en charge que lorsque vous créez un rendu à l’aide de l’application native correspondante (par exemple, Autodesk Maya).

Pour la prévisualisation ou lorsque vous créez un rendu à l’aide de l’outil d’amélioration des rendus Rapid Refine™, tous les matériaux sont simplifiés ou remplacés, ou les deux, de sorte qu’ils puissent être utilisés avec un nuanceur de type Phong. Ce nuanceur prend en charge un nombre limité d’attributs. D’autres attributs dans la définition de matériau ne sont pas pris en compte.

Voir [Visualisation de ressources 3D](viewing-3d-assets.md).

Voir [Rendu des ressources 3D](rendering-3d-assets.md).

## Nommage des matériaux dans un fichier de modèle 3D principal {#naming-materials-in-a-primary-d-model-file}

Une *surface* est définie comme la zone de la surface d’un modèle 3D couverte par le même matériau. Ce matériau fournit aussi le nom de la surface. Adobe recommande donc de nommer les matériaux inclus dans les fichiers de modèles 3D principaux en fonction de ce qu’ils représentent. Par exemple, l&#39;utilisation de noms spécifiques tels que &quot;Corps&quot;, &quot;Windows&quot;, &quot;Pneumatiques&quot; ou &quot;Rims&quot; est préférée à l&#39;utilisation de noms vagues tels que &quot;Rouge&quot;, &quot;Verre&quot;, &quot;Caoutchouc&quot;, &quot;Aluminium&quot;.

