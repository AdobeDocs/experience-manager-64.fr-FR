---
title: Configuration du composant vidéo
seo-title: Configuration du composant vidéo
description: Découvrez comment configurer le composant vidéo.
seo-description: Découvrez comment configurer le composant vidéo.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 46d0765d-fb77-4332-8fbb-5bd2abcd6806
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 37%

---

# Configuration du composant vidéo {#configure-the-video-component}

Le [composant vidéo](/help/sites-authoring/default-components-foundation.md#video) vous permet de placer un élément vidéo prêt à l’emploi prédéfini sur votre page.

Pour qu’un transcodage correct se produise, votre administrateur doit [installer FFmpeg et configurer AEM](#install-ffmpeg) séparément. Vous pouvez aussi [configurer vos profils vidéo](#configure-video-profiles) pour les utiliser avec les éléments HTML5.

>[!CAUTION]
>
>Ce composant ne doit plus fonctionner d’usine sans une personnalisation étendue au niveau du projet.

## Configuration des profils vidéo {#configure-video-profiles}

Vous pouvez définir des profils vidéo à utiliser pour les éléments HTML5. Les profils vidéo sélectionnés ici sont utilisés dans l’ordre. Pour y accéder, utilisez le [mode de conception](/help/sites-authoring/default-components-designmode.md) (interface utilisateur classique uniquement) et sélectionnez l’onglet **[!UICONTROL Profils]** :

![chlimage_1-317](assets/chlimage_1-317.png)

Vous pouvez également configurer la conception des composants vidéo et des paramètres pour [!UICONTROL Lecture], [!UICONTROL Flash] et [!UICONTROL Avancé].

## Installez FFmpeg et configurez AEM {#install-ffmpeg}

Le composant vidéo repose sur le produit Open Source tiers FFmpeg pour le transcodage correct des vidéos qui peuvent être téléchargées à partir de [https://ffmpeg.org/](https://ffmpeg.org/). Après avoir installé FFmpeg, vous devez configurer AEM pour pouvoir utiliser un codec audio et des options d’exécution spécifiques.

**Pour installer FFmpeg pour votre plateforme** :

* **Sous Windows :**

   1. Téléchargez le fichier binaire compilé en tant que `ffmpeg.zip`
   1. Décompressez-le dans un dossier.
   1. Définissez la variable d’environnement système `PATH` sur `<*your-ffmpeg-locatio*n>\bin`
   1. Redémarrez AEM.

* **Sur Mac OS X :**

   1. Installer Xcode ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. Installez XQuartz/X11.
   1. Installez les MacPorts ([https://www.macports.org/](https://www.macports.org/))
   1. Dans la console, exécutez la commande suivante et suivez les instructions :

      `sudo port install ffmpeg`

      `FFmpeg` doit être dans  `PATH` afin que AEM puisse le récupérer via la ligne de commande.

* **Utilisation de la version précompilée d’OS X 10.6 :**

   1. Téléchargez la version précompilée.
   1. Extrayez-le dans le répertoire `/usr/local`.
   1. Depuis le terminal, exécutez :

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**Pour configurer AEM** :

1. Ouvrez [!UICONTROL CRXDE Lite] dans votre navigateur web. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Sélectionnez le noeud `/libs/settings/dam/video/format_aac/jcr:content` et vérifiez que les propriétés du noeud sont les suivantes :

   * audioCodec :

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. Pour personnaliser la configuration, créez une superposition dans le noeud `/apps/settings/` et déplacez la même structure sous le noeud `/conf/global/settings/`. Il ne peut pas être modifié dans le noeud `/libs`. Par exemple, pour recouvrir le chemin `/libs/settings/dam/video/fullhd-bp`, créez-le à l’emplacement `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Remplacez et modifiez le profile-node entier et pas seulement la propriété ayant besoin d’être modifiée. Ces ressources ne sont pas résolues via SlingResourceMerger.

1. Si vous avez modifié des propriétés, cliquez sur **[!UICONTROL Tout enregistrer]**.

>[!NOTE]
>
>Les modèles de workflow prêts à l’emploi ne sont pas conservés lors de la mise à niveau de votre instance AEM. Adobe recommande de copier les modèles de workflow prêts à l’emploi avant de les modifier. Par exemple, copiez le modèle Ressources de mise à jour de gestion des actifs numériques prêt à l’emploi avant de modifier l’étape Transcodage FFmpeg dans le modèle Ressources de mise à jour de gestion des actifs numériques pour sélectionner les noms de profil vidéo qui existaient avant la mise à niveau. Vous pouvez ensuite superposer le noeud `/apps` pour permettre AEM récupérer les modifications personnalisées apportées au modèle OOTB.
