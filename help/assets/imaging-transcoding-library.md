---
title: Bibliothèque de transcodage d’imagerie
description: Apprenez à configurer et à utiliser la bibliothèque de transcodage de l’imagerie (ou ITL, de l’anglais Imaging Transcoding Library) d’Adobe, une solution de traitement des images qui peut réaliser des fonctions essentielles de manipulation graphique, y compris le codage, le transcodage, le rééchantillonnage et le redimensionnement des images.
contentOwner: AG
feature: Renditions,Developer Tools,Asset Processing
role: Admin
exl-id: 0314626d-e846-4f10-950e-6c1ceb7f4c06
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 93%

---

# Bibliothèque de transcodage d’imagerie {#imaging-transcoding-library}

La bibliothèque ITL (Imaging Transcoding Library) d’Adobe est une solution de traitement d’images propriétaire qui effectue des fonctions de gestion d’images essentielles, notamment :

* Encodage
* Transcodage (conversion des formats pris en charge)
* Rééchantillonnage d’images à l’aide des algorithmes PS et Intel IPP
* Préservation de la résolution binaire et du profil colorimétrique
* Compression de qualité JPEG
* Redimensionnement de l’image

La bibliothèque de transcodage d’imagerie (ITL) fournit une prise en charge des canaux CMJN et Alpha complet, à l’exception du CMJN-Alpha.

En plus de prendre en charge un large éventail de formats de fichiers et de profils, la bibliothèque ITL présente des avantages significatifs par rapport à d’autres solutions tierces en termes de performances, d’évolutivité et de qualité. Voici certains des principaux bénéfices de l’utilisation de la bibliothèque de transcodage d’imagerie (ITL) :

* **Mise à l’échelle avec augmentation de la taille ou de la résolution du fichier** : la mise à l’échelle est principalement réalisée grâce à la fonctionnalité ITL brevetée de redimensionnement des fichiers lors de leur décodage. Cette capacité garantit que l’utilisation de la mémoire d’exécution est toujours optimale et n’est pas une fonction quadratique de l’augmentation de la taille du fichier ou de la résolution de l’image. La bibliothèque ITL peut traiter des fichiers haute résolution plus volumineux et haute résolution (contenant un nombre supérieur de mégapixels). Les outils tiers, tels qu’ImageMagick, ne peuvent pas gérer les fichiers volumineux et les blocages système lors du traitement de ces fichiers.
* **Algorithmes de compression de la qualité et du redimensionnement Photoshop** : cohérence avec les normes du secteur en terme de qualité de l’échantillonnage descendant (lisse, pointu et bicubique automatique) et de la qualité de compression. En outre, la bibliothèque de transcodage d’imagerie évalue le facteur de qualité de l’image d’entrée et utilise intelligemment les tables optimales et les paramètres de qualité pour l’image de sortie. Cela permet de produire des fichiers de taille optimale sans compromettre la qualité visuelle.
* **Débit élevé :** le délai de réponse est inférieur et le débit est systématiquement supérieur à celui d’ImageMagick. Par conséquent, la bibliothèque de transcodage d’imagerie est supposé réduire le temps d’attente des utilisateurs et le coût d’hébergement.
* **Amélioration de la mise à l’échelle en cas de chargements simultanés :** la bibliothèque de transcodage d’imagerie fonctionne de manière optimale dans des conditions de chargements simultanés. La bibliothèque offre un débit élevé avec une performance du processeur et une utilisation de la mémoire optimaux, et un temps de réponse faible, ce qui permet de réduire le coût de l’hébergement.

## Plateformes prises en charge {#supported-platforms}

La bibliothèque de transcodage d’imagerie est disponible uniquement pour les distributions RHEL 7 et CentOS 7.

>[!NOTE]
>
>Les systèmes Mac OS et autres distributions de type *nix (par exemple, Debian et Ubuntu) ne sont pas pris en charge.

## Utilisation {#usage}

Les arguments de ligne de commande de la bibliothèque ITL peuvent inclure les éléments suivants :

```shell
 -destMime PNG/JPEG: Mime type of output rendition
 -BitDepth 8/16: Preserves Bit Depth. Bitdepth ‘4’ is automatically converted to ‘8’
 -preserveBitDepth: Downscales Bit Depth (No upscaling)
 -preserveCMYK: Preserves CMYK color space
 -jpegQuality: Provides jpeg quality parameter (0-12 , corresponding to Photoshop qualities)
 -ResamplingMethod BiCubic/Lanczos/PSBicubic: Provides resampling methods. PSBicubic is a Photoshop quality resampling method.
 -resize
```

Vous pouvez configurer les options suivantes pour le paramètre `-resize` :

* `X`: `Works similar to AEM. For example -resize 319.`

* `WxH`: `Aspect Ratio will not be maintained, For example -resize 319X319.`

* `Wx`: `Fixes the width and calculates the height maintaining the aspect ratio. For example -resize 319x.`

* `xH`: `Fixes the height and calculates the width maintaining the aspect ratio. For example -resize x319.`

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Configuration de la bibliothèque de transcodage d’imagerie {#configuring-imaging-transcoding-library}

Pour configurer le traitement de la bibliothèque de transcodage d’imagerie, créez un fichier de configuration et mettez à jour le workflow pour l’exécuter.

### Création d’un fichier de configuration pour le lot extrait {#create-conf-file}

Pour configurer la bibliothèque, créez un fichier .conf pour indiquer les bibliothèques en procédant comme suit. Vous avez besoin d’autorisations de type administrateur ou racine.

1. Téléchargez le [module de la bibliothèque de transcodage d’imagerie dans la distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) et installez-le à l’aide du gestionnaire de modules. Le module est compatible avec [!DNL Experience Manager] 6.5.

1. Pour connaître un ID de lot pour `com.day.cq.dam.cq-dam-switchengine`, connectez-vous à la console web et appuyez sur **[!UICONTROL OSGi > Lots]**. Pour ouvrir la console des lots, vous pouvez également accéder à l’URL `https://[aem_server:[port]/system/console/bundles/`. Localisez le lot `com.day.cq.dam.cq-dam-switchengine` et son identifiant.

1. Vérifiez que toutes les bibliothèques requises sont extraites en vérifiant le dossier à l’aide de la commande `ls -la /aem64/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/`, où le nom du dossier est construit à l’aide de l’ID de lot. Par exemple, la commande sera `ls -la /aem64/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/` si l’ID de lot est `588`.

1. Créez un fichier `SWitchEngineLibs.conf` pour créer un lien vers la bibliothèque.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Ajoutez un chemin d’accès `/aem64/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` au fichier CONF à l’aide de la commande `cat SWitchEngineLibs.conf`.

1. Exécutez la commande `ldconfig` pour créer les liens et le cache nécessaires.

1. Dans le compte utilisé pour commencer AEM, modifiez `.bash_profile` fichier . Ajoutez `LD_LIBRARY_PATH` en ajoutant ce qui suit.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. Pour vous assurer que la valeur du chemin est définie sur `.`, utilisez la commande `echo $LD_LIBRARY_PATH`. La sortie doit simplement être `.`. Si la valeur n’est pas définie sur `.`, redémarrez la session.

### Configuration du workflow Ressource de mise à jour de la gestion des ressources numériques. {#configure-dam-asset-update-workflow}

Mettez à jour le workflow [!UICONTROL Ressource de mise à jour de gestion des ressources numériques] pour utiliser la bibliothèque pour le traitement des images.

1. Appuyez/cliquez sur le bouton [!DNL Experience Manager] et accédez à **[!UICONTROL Outils > Processus > Modèles]**.

1. Sur la page **[!UICONTROL Modèles de workflow]**, ouvrez le modèle de workflow **[!UICONTROL Ressource de mise à jour de gestion des ressources numériques]** en mode d’édition.

1. Ouvrez l’étape de traitement de workflow des **[!UICONTROL Miniatures des processus]**. Dans l’onglet **[!UICONTROL Miniatures]**, ajoutez les types MIME pour lesquels vous souhaitez ignorer le processus de génération de miniatures par défaut dans la liste **[!UICONTROL Ignorer les types MIME]**.
Par exemple, si vous souhaitez créer des miniatures pour une image TIFF à l’aide de la bibliothèque de transcodage d’imagerie, spécifiez `image/tiff` dans le champ **[!UICONTROL Ignorer les types MIME]**.

1. Dans l’onglet **[!UICONTROL Image activée pour le web]**, ajoutez les types MIME pour lesquels vous souhaitez ignorer le processus de génération de rendu web par défaut dans la **[!UICONTROL Liste à ignorer]**. Par exemple, si vous avez ignoré le type MIME `image/tiff` à l’étape ci-dessus, ajoutez `image/tiff` à la liste à ignorer.

1. Ouvrez l’étape **[!UICONTROL Miniatures EPS (avec la technologie ImageMagick)]** et accédez à l’onglet **[!UICONTROL Arguments]**. Dans la liste **[!UICONTROL Types MIME]**, ajoutez les types MIME que la bibliothèque de transcodage d’imagerie doit traiter. Par exemple, si vous avez ignoré le type MIME `image/tiff` à l’étape ci-dessus, ajoutez `image/jpeg` à la liste **[!UICONTROL Types MIME]**.

1. Supprimez les commandes par défaut, si elles existent.

1. Activez le panneau latéral et ajoutez le **[!UICONTROL gestionnaire SWitchEngine]** à la liste des étapes.

1. Ajoutez des commandes au [!UICONTROL Gestionnaire SwitchEngine] en fonction de vos besoins. Réglez les paramètres des commandes que vous spécifiez pour répondre à vos besoins. Par exemple, si vous souhaitez préserver le profil colorimétrique de votre image JPEG, ajoutez les commandes suivantes à la liste **[!UICONTROL Commandes]** :

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![chlimage](assets/chlimage_1-199.png)

1. (Facultatif) Générez des miniatures à partir d’un rendu intermédiaire à l’aide d’une seule commande. Le rendu intermédiaire sert de source pour générer des rendus statiques et des rendus web. Cette méthode est plus rapide que la méthode précédente. Toutefois, vous ne pouvez pas appliquer de paramètres personnalisés aux miniatures à l’aide de cette méthode.

   ![chlimage](assets/chlimage_1-200.png)

1. Pour générer des rendus web, configurez les paramètres dans l’onglet **[!UICONTROL Image web]**.

1. Synchronisez le modèle de workflow [!UICONTROL Ressource de mise à jour de gestion des ressources numériques]. Enregistrez le workflow.

Pour vérifier la configuration, chargez une image TIFF et surveillez le fichier error.log. Vous remarquerez des messages `INFO` qui mentionnent `SwitchEngineHandlingProcess execute: executing command line`. Les journaux mentionnent les rendus générés. Une fois le workflow terminé, vous pouvez afficher les nouveaux rendus dans AEM.

>[!MORELIKETHIS]
>
>* [Article sur les types MIME pris en charge](assets-formats.md#supported-image-transcoding-library)

