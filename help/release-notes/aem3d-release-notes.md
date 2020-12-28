---
title: Notes de mise à jour d’AEM 3D
seo-title: Notes de mise à jour d’AEM 3D
description: Notes de mise à jour spécifiques au contenu 3D dans Adobe Experience Manager Assets.
seo-description: Notes de mise à jour spécifiques au contenu 3D dans Adobe Experience Manager Assets.
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes, 3D
content-type: reference
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: 9710c9931b4f17073c712f5869a1843c1d99ee8e
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 45%

---


# Notes de mise à jour d’AEM 3D {#aem-d-release-notes}

>[!IMPORTANT]
>
>Le pack de fonctionnalités 3D AEM dans AEM 6.4 n’est plus pris en charge. L&#39;Adobe vous recommande d&#39;utiliser la fonction de ressources 3D dans [AEM en tant que Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) ou [AEM 6.5.3 ou version ultérieure.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

aem-6.4-DynamicMedia-3D version 3.1.0 (10 octobre 2018)

Le pack de fonctionnalités 3D AEM permet la prise en charge du contenu 3D en AEM Assets. Il permet de transférer, de gérer, de prévisualiser et d’afficher des ressources 3D. La prise en charge de l’affichage et du rendu est optimisée pour les objets individuels (plutôt que pour les scènes complexes avec plusieurs objets).

aem 3D prend en charge les types de ressources Adobe Dimension (Dn) et glTF. L&#39;implémentation de ces types d&#39;actifs est sensiblement différente de celle des types 3D traditionnels décrits dans cette documentation. Voir [Utilisation des ressources Adobe Dimension](/help/assets/working-dimension-assets.md).

Les intégrations côté serveur avec Autodesk® Maya® (Windows uniquement) sont également incluses. Lorsque vous installez et configurez Maya sur le même serveur qu’AEM, vous permettez la prise en charge des formats de fichier Maya natifs, notamment le rendu de haute qualité avec le module externe NVIDIA® mental ray® pour Maya. L&#39;installation et la configuration de 3ds Max sur le serveur permettent la prise en charge du format de fichier .max natif.

Voir [Intégration avec Autodesk Maya](/help/assets/integrate-maya-with-3d.md).

Voir aussi [Installation et configuration d’AEM 3D Assets](/help/assets/install-config-3d.md) et [Paramètres avancés de configuration](/help/assets/advanced-config-3d.md).

Voir aussi [Utilisation des ressources 3D](/help/assets/assets-3d.md).

## Configuration requise {#system-requirements}

**Conditions préalables**

* aem 6.4.2 (AEM 6.4 avec Service Pack 2)
* Kit SDK Autodesk® FBX® 2016.1.2

**Systèmes d’exploitation pris en charge**

* Microsoft Windows 2012 Server ou version ultérieure
* Apple OS X El Capitan 10.6 ou version ultérieure
* RedHat Enterprise Linux 7.3

**Navigateurs Web pris en charge pour AEM Assets**

* Google Chrome 53 ou version ultérieure (recommandé).
* Apple Safari 9.1 ou version ultérieure.
* Firefox 48 ou version ultérieure.
* Microsoft Edge 25.10586 ou version ultérieure.

D’autres navigateurs ne prennent pas en charge l’affichage interactif du contenu 3D dans AEM. Seul Google Chrome prend en charge les ombres portées en aperçu.

**Configurations matérielles requises et recommandations**

* Processeur : le traitement et le rendu 3D nécessitent énormément de ressources processeur. Pour cette raison, un serveur contemporain avec un processeur à huit cœurs minimum est recommandé.
* Mémoire - 32 Go au minimum sont recommandés.
* Stockage de masse : un système de stockage SSD à large bande passante est recommandé.

   Au moment du téléchargement, les fichiers 3D sont convertis dans un format propriétaire pour un affichage rapide et interactif. Selon le type de la ressource 3D, un espace de stockage deux ou trois fois supérieur à la ressource 3D transférée est nécessaire. 

Voir aussi [Utilisation des ressources 3D](/help/assets/assets-3d.md).

## Installation et configuration d’AEM 3D  {#installing-and-configuring-aem-d}

Reportez-vous à la section [Installation et configuration d’AEM 3D](/help/assets/install-config-3d.md).

Voir aussi [Intégration de AEM 3D avec Autodesk Maya](/help/assets/integrate-maya-with-3d.md) et [Intégration de AEM 3D avec Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md).

## Formats de fichiers 3D pris en charge {#supported-d-file-formats}

| Format | Description | Plateformes | Remarques |
|--- |--- |--- |--- |
| DN | Adobe Dimension | Tous | Nécessite l’accès à un service de conversion basé sur le cloud. |
| GLTZ | gITF Zipped | Tous |  |
| GLB | GITF binaire | Tous | Téléchargement uniquement (les rendus GLB sont créés pour les ressources DN). |
| OBJ | Wavefront OBJ 3D | Tous |  |
| FBX | Autodesk FBX (Kaydara Filmbox) | Tous | Le SDK Autodesk FBX doit être installé sur le noeud d’auteur. |
| MA, MB | Autodesk Maya natif | Windows uniquement | Autodesk Maya est requis sur le noeud d’auteur pour activer ces formats de fichier. Voir [Intégration de AEM 3D avec Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| JT | Siemens PLM Open CAD | Windows uniquement | Autodesk Maya est requis sur le noeud d’auteur pour activer ces formats de fichier. Voir [Intégration de AEM 3D avec Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| * | Des formats d’entrée 3D supplémentaires pris en charge par Autodesk Maya peuvent être activés. Voir [Activation de formats supplémentaires pris en charge par Maya](/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya). | Windows uniquement | Autodesk Maya est requis sur le noeud d’auteur pour activer ces formats de fichier. Voir [Intégration de AEM 3D avec Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| MAX | Autodesk 3x max natif | Windows uniquement | Autodesk 3ds Max est requis sur le noeud d&#39;auteur pour activer ce format de fichier. Voir [Intégration de AEM 3D avec Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md). |

## Améliorations et nouvelles fonctionnalités {#enhancements-and-new-features}

Version 3.0

* Prise en charge du format de fichier natif Autodesk 3ds Max.
* Diverses modifications et corrections de bogues pour améliorer la stabilité, la qualité et l’expérience utilisateur.
* Paramètres de configuration déplacés vers `/libs/settings/dam/v3d/`

Version 3.1

* Prise en charge limitée du format de fichier natif Adobe Dimension (.dn).
* Nouvelle visionneuse 3D pour les ressources glTF.
* Nouvelle interface à un service de conversion géré par Adobe et basé sur le cloud hébergé dans Amazon AWS. Au départ, ce service ne convertit que des formats Dn en formats glTF.

## Restrictions et problèmes connus {#restrictions-and-known-issues}

### Prise en charge de Adobe Dimension {#adobe-dimension-support}

* Cette version de AEM3D ne prend pas en charge les fichiers .dn créés avec Adobe Dimension.
* Au cours du traitement du transfert, AEM utilise un service de conversion hébergé par Adobe et basé sur le cloud pour créer un rendu glTF à partir du fichier .dn natif. L’accès au service de conversion et la sélection des points de terminaison Amazon AWS sont requis.
* Un nouveau lecteur glTF est fourni, qui prend en charge l’affichage des fichiers Dn en AEM Assets et dans Sites/écrans. La prise en charge des étapes dans le lecteur n’est pas encore disponible.
* Les modèles Dn peuvent incorporer des lumières et des arrière-plans IBL qui s&#39;affichent, s&#39;ils sont présents. Le lecteur applique également un éclairage par défaut ou une couleur d’arrière-plan par défaut, ou les deux.
* Le rendu de haute qualité pour les ressources Dn n’est pas encore disponible.
* Les dépendances, telles que les mappages de texture, sont incorporées dans les ressources Dn et ne peuvent pas être gérées explicitement dans AEM.

### Compatibilité {#compatibility}

* **La fonctionnalité Exécution en tant que service Windows n’est pas prise en charge (Windows uniquement)**. Elle peut fonctionner, mais elle n’a pas été testée.
* **Dynamic Media** (  `dynamicmedia-scene7` mode) - La compatibilité de AEM3D avec la nouvelle solution Dynamic Media sortie avec AEM 6.4 n&#39;est pas encore entièrement vérifiée. Si Dynamic Media et AEM3D sont déployés ensemble, il est recommandé de ne placer les actifs 3D et leurs dépendances que dans une zone du référentiel AEM Assets qui n’est pas affectée à Dynamic Media. Cette recommandation est particulièrement importante pour les fichiers TIFF 32 bits qui sont requis pour les étapes 3D mais ne sont pas pris en charge par Dynamic Media.

### Général {#general}

* **Raccourci Résoudre les dépendances** : ce raccourci est disponible en mode Carte sur les ressources 3D. Les cartes des ressources en mode Carte affichent la bannière « Dépendances non résolues ». Le raccourci ouvre l’onglet **Propriétés de base** au lieu de l’onglet **Dépendances**. Solution de contournement : accédez manuellement à l’onglet Dépendances.

* **Sélecteur de scènes non disponible** : les ressources 3D qui comprennent des éclairages sont automatiquement balisées par AEM comme scènes 3D. Aucun sélecteur de scènes n’est disponible pour les scènes en mode Détail. Pour marquer une ressource 3D comme objet 3D, accédez à **Propriétés de base**, remplacez **Classe de ressources** par **Objet 3D**, puis cliquez sur **Enregistrer**.

* **Téléchargement des ressources 3D avec les dépendances et les rendus** : lors du téléchargement de ressources 3D avec les **dépendances** et les **rendus** cochés, le téléchargement comprend non seulement les rendus des ressources 3D principales, mais également les rendus de toutes les dépendances.

* **Intégration**  maximale d&#39;Autodesk 3ds - Le rendu avec 3ds Max n&#39;est pas pris en charge pour le moment.

### Limites des types de fichiers {#file-type-restrictions}

* **Fichiers Mathematica (.ma)** : les fichiers Mathematica utilisent le même suffixe de fichier que les fichiers Maya natifs. Lorsque le Feature Pack est installé et que le format de fichier Maya .ma est activé, AEM3D tente d&#39;assimiler des fichiers Mathematica en cas d&#39;échec des fichiers Maya. Ces ressources affichent une bannière d’erreur dans la vue Carte.

* **Fichiers images Targa (.tga)** : les fichiers de modèle 3D plus anciens peuvent comprendre des références aux fichiers TGA. Ce format n’est pas pris en charge par AEM. Adobe vous recommande de convertir ces fichiers dans un format différent avant de télécharger les fichiers 3D en AEM.
* **Images HDR** : les images HDR sont utilisées pour les scènes avec IBL. Actuellement, seules les images TIFF 32 bits sont prises en charge à cet effet.
* **Images TIFF 32 bits** : les images TIFF 32 bits sont utilisées pour les scènes avec IBL. aem ne prend pas en charge la création de rendus pour ces ressources, ce qui se traduit par des vignettes vides et la prévisualisation n’est pas possible. Une ressource fonctionne toujours correctement lorsqu’elle est utilisée avec une scène IBL.
* **Fichiers**  Autodesk 3ds Max (.max) - Si Autodesk 3ds Max est installé et configuré sur les noeuds d&#39;auteur, AEM prend en charge l&#39;assimilation et la conversion des fichiers .max. L’utilisation de fichiers .max en tant qu’étapes n’est pas prise en charge pour le moment.

### Résolution automatique des dépendances {#automatic-dependency-resolution}

* **Dépendances de fichier non résolues après le transfert** : lorsque des ressources 3D et leurs dépendances sont transférées dans une même opération, il est possible que certaines dépendances ne soient pas automatiquement résolues. Ce problème est plus susceptible de se produire lorsque les fichiers dépendants sont volumineux. Pour corriger ce problème, accédez à la page **Propriétés/dépendances** de la ressource qui affiche les dépendances non résolues après le transfert. Les dépendances précédemment non résolues ne doivent pas être affichées. Cliquez sur **Enregistrer** pour terminer la ressource. Pour éviter ce problème à l’avenir, vous pouvez transférer toutes les dépendances dans une opération distincte avant de transférer les objets 3D.

* **Respect de la casse** : la résolution automatique des dépendances tente de respecter la casse des noms de fichier. Par exemple, si la dépendance d&#39;origine trouvée dans l&#39;actif 3D est `image.jpg`, la dépendance est résolue en une ressource nommée `Image.jpg`, `image.JPG`, ou toute autre variation de cas.

### Scènes 3D {#d-stages}

* **Miniatures pour les étapes**  - Les miniatures générées automatiquement pour les étapes peuvent ne pas représenter exactement l’étape.
* **Géométrie des scènes pour les scènes non IBL** : l’outil d’amélioration rapide des rendus n’affiche pas la géométrie des scènes avec un éclairage autre que IBL, notamment les arrière-plans et les plans de sol. Cette géométrie s&#39;affiche toujours raisonnablement dans la vue de détails de l&#39;actif (prévisualisation 3D).

* **Scènes FBX avec éclairage IBL** : vous pouvez transférer des scènes FBX avec éclairage IBL. Le format FBX ne possède toutefois pas de configurations pour transférer le nom de l’image IBL. En conséquence, la résolution des dépendances de fichier échoue. Une image IBL doit être affectée manuellement à la scène après le transfert. Vous pouvez attribuer la même image TIFF 32 bits aux trois dépendances qui sont **Image d’Environnement d’éclairage diffus**, **Image d’Environnement de réflexion** et **Image d’Environnement d’arrière-plan**, ou d’autres images peuvent être attribuées.

* **Image d’arrière-plan des scènes IBL** : pour certaines scènes IBL, l’image d’arrière-plan peut être de mauvaise qualité (trop claire ou trop floue). Pour obtenir une qualité visuelle optimale de l’arrière-plan de l’image des scènes IBL, Adobe recommande de préparer une image JPEG 8 bits haute résolution distincte et de la joindre à la scène IBL comme **image d’environnement d’arrière-plan**.

* **Image noire lors du rendu avec Maya à l’aide d’une scène IBL** : ce problème est probablement dû à Maya qui ne parvient pas à trouver la dépendance de l’image IBL, car l’image IBL d’origine référencée par la scène a été remplacée par une image portant un autre nom. Pour éviter ce problème, assurez-vous qu&#39;au moins une des trois dépendances référencées par l&#39;étape Maya IBL porte le même nom que la référence originale du fichier IBL dans le fichier Maya.
* **Image d’arrière-plan inversée pour une scène IBL** : les images des scènes IBL sont délibérément inversées horizontalement pour reproduire le comportement de l’outil de rendu NVIDIA fourni avec Autodesk Maya. Solution : Retournez les images utilisées pour les étapes IBL dans Photoshop avant de les télécharger.
* **Luminosité des scènes IBL** : l’analyse automatique de l’image IBL peut donner une scène trop sombre ou trop lumineuse. Pour régler la luminosité des étapes IBL, accédez à **Propriétés de base** et ajustez la valeur **bright** **Éclairage de l&#39;Environnement** selon les besoins.

### Composant 3D AEM Sites {#aem-sites-d-component}

* **Un composant 3D par page**  - Actuellement, une seule instance du composant 3D est autorisée sur chaque page Web. Si plusieurs composants 3D sont ajoutés à la même page, aucun de ces composants ne fonctionne correctement.
* **vue 3D manquante lors de la prévisualisation dans les sites**  : lorsque vous utilisez  **** la prévisualisation de sites, la page doit être rechargée dans le navigateur pour initialiser entièrement la visionneuse 3D. Il ne s’agit pas d’un problème lorsque vous vue directement la page Web (c’est-à-dire lorsque `edit.html` est supprimé du chemin d’accès) sur les noeuds Auteur ou Publier.

* **Mode plein écran non disponible sur les appareils**  iOS : le bouton plein écran n’est pas disponible sur les appareils iOS, quel que soit le navigateur utilisé.

### Publication de contenu 3D {#publishing-d-content}

* **Configuration**  des composants 3D - Vous devez installer le Pack de fonctionnalités 3D sur tous les noeuds de publication principaux et chaque noeud doit être configuré avec  **CRXDE** Liteto les mêmes options de configuration à  `/libs/settings/dam/v3D/WebGLSites`.

* **textures manquantes, arrière-plan ou éclairage après publication**  : le mécanisme de  **** publication dans AEM Sites publie automatiquement les Principales dépendances de la page, y compris le modèle 3D et la scène 3D référencées par le composant 3D. Les scènes et modèles 3D dépendent généralement de ressources secondaires pour les images IBL et les placages de texture, lesquels ne sont pas publiés automatiquement par le mécanisme Publication de Sites. Solution : publier tous les fichiers 3D à partir des ressources avant de publier la page Web à partir des sites. Cela permet de s’assurer que toutes les dépendances des ressources 3D sont disponibles sur les noeuds de publication.
