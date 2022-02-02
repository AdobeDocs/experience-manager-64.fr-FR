---
title: Vidéo dans Dynamic Media
description: Découvrez comment utiliser la vidéo dans Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: Dynamic-Media
content-type: reference
exl-id: acb95a2b-0171-449e-97fa-f9a533f990de
feature: Video
role: User
source-git-commit: f2b7ffa37bcb14e7be47c10ea9d3e39f89e1858d
workflow-type: tm+mt
source-wordcount: '10401'
ht-degree: 76%

---

# Vidéo {#video}

Cette section décrit l’utilisation de vidéos dans Dynamic Media.

## Démarrage rapide : vidéos {#quick-start-videos}

Le workflow détaillé décrit ci-après vise à vous aider à maîtriser rapidement les opérations liées aux visionneuses de vidéos adaptatives dans Dynamic Media. Chaque étape comporte des renvois à des rubriques contenant de plus amples informations.

>[!NOTE]
>
>Avant d’utiliser des vidéos dans Dynamic Media, vérifiez que l’administrateur AEM a activé et configuré les Cloud Services Dynamic Media.
>
>* Voir [Configuration des services cloud Dynamic Media dans Configuration de Dynamic Media – mode hybride.](/help/assets/config-dynamic.md)
>* Voir [Configuration de Dynamic Media – mode Scene7](config-dms7.md) et [Dépannage de Dynamic Media – mode Scene7](troubleshoot-dms7.md).
>


1. **Chargez les vidéos Dynamic Media** en procédant comme suit :

   * Créez votre propre profil de codage vidéo. Vous pouvez également utiliser le profil prédéfini &quot;Codage vidéo adaptatif&quot; fourni avec Dynamic Media.

      * [Création d’un profil de codage vidéo](video-profiles.md).
      * En savoir plus sur les [bonnes pratiques relatives au codage vidéo](#best-practices-for-encoding-videos).
   * Associez le profil de traitement vidéo à un ou plusieurs dossiers dans lequel vous allez charger les vidéos originales.

      * [Application d’un profil vidéo à des dossiers](video-profiles.md#applying-a-video-profile-to-folders).
      * En savoir plus sur les [bonnes pratiques relatives à l’organisation des ressources numériques en vue de l’utilisation de profils de traitement](organize-assets.md#organize-using-folders).
      * En savoir plus sur l’[organisation des ressources numériques](organize-assets.md).
   * Chargez les vidéos issues de sources originales dans les dossiers. Lorsque vous ajoutez des vidéos au dossier, elles sont codées selon le profil de traitement vidéo affecté au dossier.

      * Dynamic Media prend principalement en charge les vidéos de forme courte avec une durée maximale de 30 minutes et une résolution minimale supérieure à 25 x 25.
      * Vous pouvez charger des fichiers vidéo d’une taille de 15 Go chacun au maximum.
      * [Chargement des vidéos](managing-video-assets.md#uploading-and-previewing-video-assets).
      * En savoir plus sur les [formats de fichiers d’entrée pris en charge](assets-formats.md#supported-multimedia-formats).
   * Contrôle la façon dont l’[encodage vidéo progresse](#monitoring-video-encoding-and-youtube-publishing-progress) du point de vue de la ressource ou du processus.




1. **Gérez les vidéos Dynamic Media** en effectuant les opérations suivantes :

   * Organisez, parcourez et recherchez des ressources vidéo

      * [Organisation des ressources numériques](organize-assets.md)

         En savoir plus sur les [bonnes pratiques relatives à l’organisation des ressources numériques en vue de l’utilisation de profils de traitement](organize-assets.md#organize-using-folders)

      * [Recherche de ressources vidéo](search-video-assets.md) ou [Recherche de ressources](managing-assets-touch-ui.md#searching-assets)
   * Prévisualisez et publiez des ressources vidéo

      * Affichez la vidéo source et les rendus codés de la vidéo avec les miniatures associées :

         [Prévisualisation de vidéos](managing-video-assets.md#uploading-and-previewing-video-assets) ou [Prévisualisation de ressources](previewing-assets.md)

         [Affichage des rendus vidéo](video-renditions.md)

[Gestion des rendus vidéo](managing-assets-touch-ui.md#managing-renditions)

      * [Gestion des paramètres prédéfinis de visionneuse](managing-viewer-presets.md)
      * [Publication des ressources](publishing-dynamicmedia-assets.md)
   * Utilisation des métadonnées vidéo

      * Affichez les propriétés d’un rendu vidéo codé, telles que la fréquence d’image, le débit audio et vidéo et le codec :

         [Affichage des propriétés de rendu vidéo](video-renditions.md)

      * Modifiez les propriétés vidéo telles que le titre, la description, les balises et les champs de métadonnées personnalisées :

[Modification des propriétés vidéo](managing-assets-touch-ui.md#editing-properties)

      * [Gestion des métadonnées des ressources numériques](metadata.md)
      * [Schémas de métadonnées](metadata-schemas.md)
   * Révision, approbation et annotation de vidéos

      * [Annotation de vidéos](managing-video-assets.md#annotating-video-assets) ou [Annotation de ressources](managing-assets-touch-ui.md#annotating)
      * [Application de workflows aux ressources](assets-workflow.md) ou [Démarrage d’un workflow sur une ressource](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset)
      * [Examen des ressources des dossiers](bulk-approval.md)
      * [Projets](/help/sites-authoring/projects.md)




1. Pour **publier les vidéos Dynamic Media**, effectuez l’une des opérations suivantes :

   * Si vous utilisez Adobe Experience Manager comme système de gestion de contenu web, vous pouvez ajouter des vidéos directement à vos pages web.

      * [Ajout de vidéos à des pages web](adding-dynamic-media-assets-to-pages.md).
   * Si vous utilisez un système de gestion de contenu web tiers, vous pouvez lier ou incorporer des vidéos dans vos pages web.

      * Intégrez une vidéo à l’aide d’une URL :

         [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).
      * Intégrez une vidéo à l’aide du code intégré dans la page web :

         [Incorporation de la visionneuse de vidéos dans une page web](embed-code.md).
   * [Publication de vidéos sur YouTube](#publishing-videos-to-youtube).
   * [Génération de rapports vidéo](#viewing-video-reports).
   * [Ajout de sous-titres à une vidéo](#adding-captions-to-video).



## Utilisation de vidéo dans Dynamic Media {#working-with-video-in-dynamic-media}

La vidéo dans Dynamic Media est une solution complète qui facilite la publication de vidéos adaptatives haute qualité pour la diffusion sur plusieurs écrans, notamment les postes de travail et les appareils mobiles iOS, Android, Blackberry et Windows. Une visionneuse de vidéos adaptative regroupe les versions d’une même vidéo codées dans des débits et des formats différents, par exemple 400 kbit/s, 800 kbit/s et 1 000 kbit/s. L’ordinateur de bureau ou l’appareil mobile détecte la bande passante disponible.

Par exemple, sur un appareil mobile iOS, il détecte une bande passante telle que 3G, 4G ou une connexion Wi-Fi, puis sélectionne automatiquement la vidéo codée selon le débit correspondant parmi ceux disponibles dans la visionneuse de vidéos adaptative. La vidéo est diffusée en continu sur les postes de travail, les appareils mobiles ou les tablettes.

En outre, la qualité de la vidéo est automatiquement adaptée en temps réel selon les conditions réseau sur le poste de travail ou l’appareil mobile. De même, si un client passe en mode plein écran sur un bureau, la visionneuse de vidéos adaptative réagit en utilisant une meilleure résolution, améliorant ainsi l’expérience de visionnage du client. L’utilisation des visionneuses de vidéos adaptatives offre une lecture optimale aux clients qui lisent des vidéos Dynamic Media sur plusieurs écrans et appareils.

La logique appliquée par un lecteur vidéo pour déterminer quelles sont les vidéos encodées à lire ou à sélectionner au cours de la lecture repose sur l’algorithme suivant :

1. Le lecteur vidéo charge le fragment vidéo initial basé sur le débit le plus proche de la valeur définie pour le « débit initial » dans le lecteur lui-même.
1. Le lecteur vidéo est adapté en fonction des modifications de la vitesse de bande passante d’après les critères suivants :

   1. Le lecteur sélectionne le flux de bande passante le plus élevé qui est inférieur ou égal à la bande passante estimée.
   1. Le lecteur prend uniquement en compte 80 % de la bande passante disponible. Cependant, s’il change, il est préférable que ce taux soit seulement de 70 % pour éviter toute surestimation et que le lecteur ne repasse au taux précédent.

Pour obtenir des informations techniques détaillées sur l’algorithme, consultez la page [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Pour la gestion des visionneuses de vidéos adaptative et unique, les fonctions suivantes sont prises en charge :

* Téléchargement de vidéos en différents formats vidéo et audio pris en charge et codage vidéo au format MP4 H.264 pour la lecture sur plusieurs écrans. Vous pouvez utiliser les paramètres prédéfinis de vidéo adaptative ou de codage unique ou personnaliser le codage pour contrôler la qualité et la taille de la vidéo.

   * Lorsqu’une visionneuse de vidéos adaptative est générée, elle comprend des vidéos MP4.
   * **Remarque** : Les vidéos originales/sources ne sont pas ajoutées à la visionneuse de vidéos adaptative.

* Sous-titrage des vidéos dans toutes les visionneuses de vidéo HTML5.
* Organiser, parcourir et effectuer des recherches dans la vidéo avec une prise en charge complète des métadonnées pour une gestion efficace des ressources vidéo.
* Proposer des visionneuses de vidéos adaptatives en ligne ainsi que sur des postes de travail et des appareils mobiles (iPhone, iPad, Android, Blackberry et Windows Phone notamment).

La diffusion de vidéo adaptative en flux continu est prise en charge sur diverses plates-formes iOS. Voir [Guide de référence des visionneuses Adobe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

Dynamic Media prend en charge la lecture vidéo pour mobiles au format vidéo MP4 H.264. Les appareils Blackberry qui prennent en charge ce format vidéo sont répertoriés dans la liste : [Formats vidéo pris en charge sur Blackberry](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

Les terminaux Windows qui prennent en charge ce format vidéo sont répertoriés dans la liste : [Formats vidéo pris en charge sur Windows Phone](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)

* Lecture de la vidéo à l’aide des paramètres prédéfinis de la visionneuse Dynamic Media Video, tels que :

   * des visionneuses de vidéos uniques ;
   * des visionneuses de médias mixtes combinant du contenu vidéo et des images.

* Configurer des lecteurs vidéo pour répondre à vos besoins de stratégie de marque.
* Intégrer la vidéo à votre site web, site mobile ou application mobile grâce à une simple URL ou à du code intégré.

<!-- See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480). -->

Voir aussi [A propos des visionneuses HTML5](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html?lang=fr#viewers-for-aem-assets-only) dans le Guide de référence des visionneuses Dynamic Media Adobe.

## Bonne pratique : Utilisation de la visionneuse de vidéos HTML5 {#best-practice-using-the-html-video-viewer}

Les paramètres prédéfinis de la visionneuse de vidéos HTML5 Dynamic Media sont des lecteurs vidéo fiables. Utilisez-les pour éviter la plupart des problèmes courants liés à la lecture de vidéos HTML5, ainsi que les problèmes liés aux appareils mobiles, notamment l’absence de diffusion en continu adaptative et la portée limitée du navigateur.

En ce qui concerne la conception du lecteur, vous pouvez concevoir toutes les fonctionnalités du lecteur vidéo à l’aide d’outils de développement web standard. Vous pouvez, par exemple, concevoir les boutons, les commandes et les affiches personnalisées en arrière-plan au moyen du code HTML5 et CSS afin de mieux cibler les utilisateurs avec un aspect personnalisé.

En ce qui concerne la lecture, la visionneuse, détecte automatiquement les fonctionnalités vidéo du navigateur. Elle diffuse ensuite la vidéo en flux continu HLS (diffusion en flux continu adaptatif). Si ces méthodes de distribution n’existent pas, la diffusion progressive HTML5 est utilisée à la place.

En combinant dans un lecteur unique la capacité de concevoir les composants de lecture à l’aide de code HTML5 et CSS, d’avoir accès à la lecture incorporée et d’utiliser les flux continus adaptatifs et progressifs selon la capacité du navigateur, vous pouvez étendre la portée de votre contenu multimédia aux utilisateurs d’appareils mobiles et de postes de travail et garantir ainsi une expérience vidéo rationalisée.

Voir aussi [À propos des visionneuses HTML5](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html) dans le guide de référence des visionneuses d’Adobe 

### Lecture vidéo sur les ordinateurs de bureau et les appareils mobiles à l’aide de la visionneuse de vidéos HTML5 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Pour la diffusion en flux continu de la vidéo adaptative sur un poste de travail et un appareil mobile, les vidéos utilisées pour le changement de débit reposent sur toutes les vidéos MP4 dans la visionneuse de vidéos adaptative.

La lecture vidéo est effectuée à l’aide de la diffusion vidéo en flux continu HLS (HTTP Live Streaming) ou de téléchargement de vidéo progressive. Dans les versions antérieures d’AEM, telles que 6.0, 6.1 et 6.2, les vidéos ont été diffusées via HTTP.

Toutefois, dans la version 6.3 et ultérieures d’AEM, les vidéos sont désormais diffusées en continu via HTTPS (c’est-à-dire, diffusion vidéo en flux continu HLS), car l’URL du service de la passerelle DM utilise toujours HTTPS également. Veuillez noter qu’il n’y a aucun impact pour le client dans ce comportement par défaut. Autrement dit, la diffusion en continu de vidéo s’effectuera tout de même via HTTPS, à moins qu’elle ne soit pas prise en charge par le navigateur (voir le tableau ci-dessous). Par conséquent,

* Si vous avez un site web HTTPS avec une diffusion vidéo en continu via HTTPS, la diffusion en continu est de qualité.
* Si vous avez un site web HTTP avec une diffusion vidéo en flux continu via HTTPS, la diffusion en continu est de qualité et il n’y a aucun problème de contenu mixte du navigateur web.

HLS (HTTP Live Streaming) est une norme d’Apple pour la diffusion de vidéo adaptative en continu qui ajuste automatiquement la lecture en fonction de la capacité de bande passante du réseau. Elle permet aussi au client de « rechercher » n’importe quel point de la vidéo sans avoir à attendre que le reste de la vidéo soit téléchargé (voir aussi HTTP Live Streaming).

La vidéo progressive est fournie grâce au téléchargement et à l’enregistrement de la vidéo en local sur l’écran du poste de bureau ou de l’appareil mobile de l’utilisateur.

Le tableau ci-dessous décrit l’appareil, le navigateur et la méthode de lecture des vidéos sur les ordinateurs de bureau et les appareils mobiles à l’aide de la visionneuse de vidéos Dynamic Media.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Appareil</strong></td>
   <td><strong>Navigateur</strong></td>
   <td><strong>Mode lecture vidéo</strong></td>
  </tr>
  <tr> 
   <td>Poste de travail</td>
   <td>Internet Explorer 9 et 10</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr> 
   <td>Poste de travail</td>
   <td>Internet Explorer 11+</td>
   <td>Sous Windows 8 et Windows 10 – Forcer l’utilisation de HTTPS chaque fois que HLS est demandé. Limites connues : HTTP sur HLS ne fonctionne pas avec cette combinaison de navigateur/système d’exploitation<br /> <br /> Sous Windows 7 – Téléchargement progressif. Utilise la logique standard pour sélectionner le protocole HTTP ou HTTPS.</td>
  </tr>
  <tr> 
   <td>Poste de travail</td>
   <td>Firefox 23 à 44</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr> 
   <td>Poste de travail</td>
   <td>Firefox 45 ou version ultérieure</td>
   <td>HLS diffusion vidéo en continu.</td>
  </tr>
  <tr> 
   <td>Poste de travail</td>
   <td>Chrome</td>
   <td>Diffusion vidéo HLS en continu.</td>
  </tr>
  <tr> 
   <td>Poste de travail</td>
   <td>Safari (Mac)</td>
   <td>HLS diffusion vidéo en continu.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Chrome (Android 6 ou version antérieure)</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Chrome (Android 7 ou version ultérieure)</td>
   <td>HLS diffusion vidéo en continu.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Android (navigateur par défaut)</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Safari (iOS)</td>
   <td>HLS diffusion vidéo en continu.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Chrome (iOS)</td>
   <td>HLS diffusion vidéo en continu.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Blackberry</td>
   <td>HLS diffusion vidéo en continu.</td>
  </tr>
 </tbody>
</table>

## Architecture de la solution vidéo Dynamic Media {#architecture-of-dynamic-media-video-solution}

Le graphique suivant montre le processus global de création de vidéos qui sont téléchargées et codées par le biais de DMGateway et mises à disposition pour une consommation publique.

![chlimage_1-427](assets/chlimage_1-427.png)

## Architecture de publication hybride des vidéos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Bonnes pratiques en matière de codage de vidéos {#best-practices-for-encoding-videos}

Le processus **[!UICONTROL vidéo d’encodage Dynamic Media]** encode la vidéo si vous avez activé Dynamic Media et configuré les services cloud vidéo. Ce workflow capture l’historique de traitement des workflows et les informations d’échec. Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress). Si vous avez activé Dynamic Media et configuré les services de cloud vidéo, la variable **[!UICONTROL Vidéo de codage Dynamic Media]** prend automatiquement effet lorsque vous téléchargez une vidéo. (Si vous n’utilisez pas Dynamic Media, le workflow **[!UICONTROL Ressource de mise à jour DAM]** prend effet.)

<!-- DEAD ARTICLE AND VIDEO LINK The following are best-practice tips for encoding source video files.

For advice about video encoding, see the following:

* Article: *Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution:* [www.adobe.com/go/learn_s7_streaming101_en](https://www.adobe.com/go/learn_s7_streaming101_en).
* Video: *Video Encoding Basics:* [www.adobe.com/go/learn_s7_encoding_en](https://www.adobe.com/go/learn_s7_encoding_en). -->

### Principaux fichiers vidéo source {#source-video-files}

Lorsque vous codez un fichier vidéo, utilisez un fichier vidéo source ayant la plus haute qualité possible. Évitez d’utiliser des fichiers vidéo précédemment codés, car ces fichiers sont déjà compressés, et un codage supplémentaire crée une vidéo de qualité inférieure.

* Dynamic Media prend principalement en charge les vidéos de forme courte avec une durée maximale de 30 minutes et une résolution minimale supérieure à 25 x 25.
* Vous pouvez charger des fichiers vidéo de source principale d’une taille de 15 Go chacun au maximum.

Le tableau ci-dessous décrit la taille recommandée, le format et le débit minimal requis pour vos fichiers vidéo sources au moment de leur codage :

| Taille | Format | Débit minimal |
|--- |--- |--- |
| 1024 x 768 | 4:3 | 4 500 Kbit/s pour la plupart des vidéos. |
| 1280 x 720 | 16:9 | 3 000 à 6 000 Kbit/s, selon la quantité de mouvement dans la vidéo. |
| 1 920 x 1 080 | 16:9 | 6 000 à 8 000 kbit/s en fonction de la quantité de mouvement sur la vidéo. |

### Obtention des métadonnées d’un fichier {#obtaining-a-file-s-metadata}

Vous pouvez obtenir les métadonnées d’un fichier en les affichant à l’aide d’un outil d’édition vidéo ou d’une application d’extraction de métadonnées. Voici les instructions d’utilisation de MediaInfo, une application tierce permettant d’extraire les métadonnées d’un fichier vidéo :

1. Accédez à cette page web : [https://mediaarea.net/en/MediaInfo](https://mediaarea.net/en/MediaInfo).
1. Sélectionnez et téléchargez le programme d’installation de la version avec interface utilisateur graphique que vous utilisez, puis suivez les instructions d’installation.
1. Après l’installation, cliquez avec le bouton droit sur le fichier vidéo (Windows uniquement) et sélectionnez **[!UICONTROL MediaInfo]** ou ouvrez **[!UICONTROL MediaInfo]** et faites glisser votre fichier vidéo dans l’application. Toutes les métadonnées associées à votre fichier vidéo s’affichent, y compris sa largeur, sa hauteur et le nombre d’images par seconde.

### Format {#aspect-ratio}

Lorsque vous choisissez ou créez un paramètre prédéfini de codage vidéo pour votre fichier vidéo original, assurez-vous que le paramètre prédéfini indique le même format que le fichier vidéo original. Le format fait référence au rapport largeur/hauteur de la vidéo.

Pour déterminer le format d’un fichier vidéo, récupérez les métadonnées de ce fichier et notez les valeurs de largeur et de hauteur (voir la section Obtention des métadonnées d’un fichier ci-dessus). Utilisez ensuite cette formule pour déterminer le format :

*largeur/hauteur = format*

Ce tableau décrit la façon dont les résultats de la formule se traduisent en choix de formats :

| Résultat de la formule | Format |
|--- |--- |
| 1.33 | 4:3 |
| 0,75 | 3:4 |
| 1,78 | 16:9 |
| 0.56 | 9:16 |

Par exemple, une vidéo qui a une largeur de 1440 pour une hauteur de 1080 a un format de 1440/1080, soit 1,33. Dans ce cas, vous choisissez un paramètre prédéfini de codage vidéo avec un format de 4:3 pour le codage du fichier vidéo.

### Débit binaire {#bitrate}

Le débit correspond à la quantité de données encodées pour produire une seule seconde de lecture vidéo. Le débit de données est mesuré en kilobits par seconde (kbit/s).

Du fait que tous les codecs utilisent la compression avec perte, le débit de données est le facteur le plus important de la qualité vidéo. Quand vous utilisez la compression avec perte, plus vous compressez la vidéo, plus la qualité de l’image se dégrade. Toutes les autres caractéristiques étant égales (résolution, taux de rafraîchissement et codec), plus le débit de données est faible, moins la qualité du fichier compressé est bonne.

Lorsque vous sélectionnez l’encodage du débit, vous avez le choix entre deux types :

* **Codage à débit constant** (CBR) - Pendant le codage CBR, le débit ou le nombre de bits par seconde est conservé pendant tout le processus de codage. L’encodage CBR maintient le débit défini selon votre configuration sur l’intégralité de la vidéo. En outre, le codage CBR n’optimise pas la qualité des fichiers multimédias, mais économise de l’espace de stockage.

   Utilisez le codage CBR si votre vidéo présente globalement un niveau de mouvement similaire. Le codage CBR est le plus souvent utilisé pour diffuser le contenu vidéo en continu. Voir également [Utilisation de paramètres de codage vidéo personnalisés](video-profiles.md#using-custom-added-video-encoding-parameters).

* **Codage à débit variable** (VBR) : l’encodage VBR ajuste le débit de données vers le bas et la limite supérieure que vous définissez, en fonction des données requises par le compresseur. Cela signifie que lors d’un processus de codage VBR, le débit du fichier multimédia augmente ou diminue de manière dynamique en fonction des besoins du débit de fichiers multimédias.

   Le VBR prend plus de temps au codage, mais garantit de meilleurs résultats, avec une qualité de fichier multimédia supérieure. Le codage VBR est couramment utilisé pour la diffusion http progressive de contenu vidéo.

**Quand devriez-vous utiliser le VBR ou le CBR ?**
Lorsque vous devez choisir entre le VBR et le CBR, il est presque toujours recommandé d’utiliser le VBR pour vos fichiers multimédias. Le VBR vous garantit des fichiers de meilleure qualité à des débits compétitifs. Lorsque vous utilisez le VBR, assurez-vous d’utiliser le codage à deux passages, et définissez le débit maximal afin qu’il soit 1,5 fois supérieur au débit vidéo cible.

Lorsque vous choisissez un paramètre prédéfini de codage vidéo, tenez compte de la vitesse de connexion de l’utilisateur final auquel la vidéo est destinée. Choisissez un paramètre prédéfini avec un débit de données correspondant à 80 % de cette vitesse. Par exemple, si la vitesse de connexion de l’utilisateur final est de 1 000 kbit/s, le meilleur paramètre prédéfini est celui qui comprend un débit vidéo de 800 kbit/s.

Ce tableau décrit le débit de données associé à des vitesses de connexion courantes.

| Vitesse (kbit/s) | Type de connexion |
|--- |--- |
| 256 | Connexion d’accès à distance. |
| 800 | Connexion mobile standard. Pour cette connexion, visez un débit de données de 400 à 800 kbit/s pour les expériences 3G. |
| 2000 | Connexion haut débit standard de bureau. Pour cette connexion, visez un débit de données de 800 à 2 000 kbit/s, bien qu’un débit de 1 200 à 1 500 kbit/s convienne à la plupart des cibles. |
| 5 000 | Connexion haut débit standard. Il est déconseillé de coder dans cette plage supérieure, car la diffusion de la vidéo à cette vitesse n’est pas possible pour la plupart des consommateurs. |

### Résolution {#resolution}

La **résolution** décrit la hauteur et la largeur d’un fichier vidéo, exprimée en pixels. La plupart des vidéos sources sont stockées à une résolution élevée (par exemple, 1 920 x 1 080). À des fins de diffusion en flux continu, la vidéo source est compressée à une résolution inférieure (640 x 480, voire moins).

La résolution et le débit de données sont deux facteurs étroitement liés qui déterminent la qualité de la vidéo. Pour maintenir la même qualité vidéo, plus le nombre de pixels (c’est-à-dire la résolution) est élevé dans un fichier vidéo, plus le débit de données doit l’être également. Par exemple, considérez le nombre de pixels par image dans un fichier vidéo d’une résolution de 320 x 240 pixels et dans un fichier vidéo d’une résolution de 640 x 480 pixels :

| Résolution | Pixels par image |
|--- |--- |
| 320 x 240 | 76 800 |
| 640 x 480 | 307 200 |

Le fichier de 640 x 480 possède quatre fois plus de pixels par image. Pour atteindre le même débit de données avec ces deux résolutions, vous appliquez une compression de 4 au fichier d’une résolution de 640 x 480 pixels, ce qui peut réduire la qualité de la vidéo. Par conséquent, un débit de données vidéo de 250 kbit/s produit un affichage de haute qualité à une résolution de 320 x 240 pixels, mais pas à une résolution de 640 x 480 pixels.

En général, plus le débit de données que vous utilisez est élevé, plus la qualité de votre vidéo est bonne, et plus vous utilisez une résolution élevée, plus de débit de données dont vous avez besoin est élevé pour conserver la qualité de visionnage (en comparaison avec des résolutions plus basses).

Du fait que la résolution et le débit de données sont liés, vous avez le choix entre deux options lors du codage vidéo :

* Choisir un débit de données puis, en fonction de ce paramètre, coder à la résolution la plus haute pour obtenir une vidéo de bonne qualité.
* Choisir une résolution, puis coder au débit de données nécessaire pour que la qualité vidéo soit optimale à la résolution choisie.

Lorsque vous choisissez (ou créez) un paramètre prédéfini de codage vidéo pour votre fichier vidéo original, utilisez ce tableau pour choisir la résolution cible appropriée :

| Résolution | Hauteur (pixels) | Taille d’écran |
|--- |--- |--- |
| 240p | 240 | Écran de très petite taille |
| 300p | 300 | Petit écran équipant généralement les appareils mobiles |
| 360p | 360 | Petit écran |
| 480p | 480 | Écran de taille moyenne |
| 720p | 720 | Grand écran |
| 1 080p | 1080 | Grand écran haute définition |

### Images par seconde  {#fps-frames-per-second}

Aux États-Unis et au Japon, la plupart des vidéos sont tournées à 29,97 ips (images par seconde) ; en Europe, la plupart des vidéos le sont à 25 ips. Un film est tourné à 24 ips.

Choisissez un paramètre prédéfini de codage vidéo correspondant au nombre d’images par seconde de votre vidéo originale. Par exemple, si le débit est de 25 ips pour la vidéo originale, choisissez un paramètre prédéfini de 25 ips pour le codage. Par défaut, tous les codages personnalisés utilisent le nombre d’images par seconde de la vidéo originale. C’est pourquoi il est inutile d’indiquer le nombre d’images par seconde lorsque vous créez un paramètre prédéfini de codage vidéo.

### Dimensions du codage vidéo {#video-encoding-dimensions}

Pour obtenir des résultats optimaux, sélectionnez les dimensions de codage de façon à ce que la vidéo source corresponde à un multiple entier de toutes vos vidéos codées.

Pour ce faire, il suffit de diviser la largeur de la source par la largeur codée pour obtenir le rapport de largeur, puis de diviser la hauteur de la source par la hauteur codée pour obtenir le rapport de hauteur.

Si le résultat est un nombre entier, cela signifie que la mise à l’échelle de la vidéo est parfaite. Si le résultat n’est pas un nombre entier, la qualité vidéo s’en ressentira en raison de la présence d’artefacts vidéo (pixels résiduels). Cet effet est plus visible lorsque la vidéo contient du texte.

Supposons, par exemple, que la résolution de votre vidéo source soit équivalente à 1920 x 1080 pixels. Dans le tableau ci-après, les trois vidéos codées indiquent les paramètres de codage optimaux à appliquer.

<table> 
 <tbody> 
  <tr> 
   <th><p>Type de vidéo</p> </th> 
   <th><p>Largeur x hauteur</p> </th> 
   <th><p>Rapport de largeur</p> </th> 
   <th><p>Rapport de hauteur</p> </th> 
  </tr>
  <tr> 
   <td><p>Source</p> </td> 
   <td><p>1 920 x 1 080</p> </td> 
   <td><p>1</p> </td> 
   <td><p>1</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codée</p> </td> 
   <td><p>960 x 540</p> </td> 
   <td><p>2</p> </td> 
   <td><p>2</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codée</p> </td> 
   <td><p>640 x 360</p> </td> 
   <td><p>3</p> </td> 
   <td><p>3</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codée</p> </td> 
   <td><p>480 x 270</p> </td> 
   <td><p>4</p> </td> 
   <td><p>4</p> </td> 
  </tr> 
 </tbody> 
</table>

### Format de fichier vidéo codé {#encoded-video-file-format}

Dynamic Media recommande d’utiliser les paramètres prédéfinis MP4 H.264 de codage vidéo. Comme les fichiers MP4 utilisent le codec vidéo H.264, la vidéo est de haute qualité mais dans un fichier au volume compressé.

## Publication de vidéos sur YouTube {#publishing-videos-to-youtube}

Vous pouvez publier des ressources vidéo AEM on-premise directement sur une chaîne YouTube que vous avez précédemment créée.

Pour publier des ressources vidéo sur YouTube, vous définissez AEM Assets avec des balises. Vous associez ces balises à une chaîne YouTube. Si la balise d’une ressource vidéo correspond à la balise d’une chaîne YouTube, la vidéo est publiée sur YouTube. Si la ressource vidéo ne comporte pas de balise, elle n’est pas publiée sur YouTube.

La publication sur YouTube ignore le système de profil de traitement dans AEM et, par conséquent, le profil de codage vidéo. Ce contournement se produit car YouTube dispose de son propre codage, de sorte qu’un profil de traitement vidéo n’est pas nécessaire. Dans la plupart des cas, toutefois, vos ressources vidéo devront sans doute passer par un profil de traitement vidéo. Lorsque vous ignorez le profil de traitement vidéo et que vous publiez directement dans YouTube, cela signifie simplement que votre ressource vidéo dans AEM ressource n’a pas de miniature visible. Cela signifie également que si vous utilisez le mode d’exécution dynamicmedia, les vidéos non codées ne fonctionneront pas avec les types de ressources Dynamic Media.

Pour garantir une authentification serveur à serveur sécurisée avec YouTube, la publication des vidéos sur les serveurs YouTube implique les tâches suivantes :

1. [Configuration des paramètres du cloud Google](#configuring-google-cloud-settings)
1. [Création d’une chaîne YouTube](#creating-a-youtube-channel)
1. [Ajout de balises pour la publication](#adding-tags-for-publishing)
1. [Activation de l’agent de réplication de publication YouTube](#enabling-the-youtube-publish-replication-agent)
1. [Configuration de YouTube dans AEM](#setting-up-youtube-in-aem)
1. [(Facultatif) Automatisation de la définition des propriétés YouTube par défaut pour vos vidéos chargées](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Publication de vidéos sur votre chaîne YouTube](#publishing-videos-to-your-youtube-channel)
1. [(Facultatif) Vérification de la vidéo publiée sur YouTube](video.md#optional-verifying-the-published-video-on-youtube)
1. [Liaison d’URL YouTube à votre application web](#linking-youtube-urls-to-your-web-application)

Vous pouvez également [annuler la publication de vidéos pour les supprimer de YouTube](#unpublishing-videos-to-remove-them-from-youtube).

### Configuration des paramètres de Google Cloud {#configuring-google-cloud-settings}

Pour effectuer une publication sur YouTube, vous avez besoin d’un compte Google. Si vous disposez d’un compte GMAIL, vous disposez déjà d’un compte Google. Si vous ne disposez pas d’un compte Google, vous pouvez facilement en créer un. Un compte est nécessaire, car vous avez besoin des informations d’identification pour publier des ressources vidéo sur YouTube. Si un compte a déjà été créé, ignorez cette tâche et passez à [Création d’un canal YouTube](#creating-a-youtube-channel).

>[!NOTE]
>
>Les étapes suivantes étaient exactes au moment de leur rédaction. Toutefois, Google met à jour régulièrement ses sites web sans préavis. Par conséquent, ces étapes peuvent être légèrement différentes.

**Pour configurer les paramètres de Google Cloud, procédez comme suit :**

1. Créez un compte Google.

   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   Si vous disposez déjà d’un compte Google, passez à l’étape suivante.

1. Accédez à [https://cloud.google.com/](https://cloud.google.com/).
1. Sur la page Google Cloud Platform, appuyez sur près de la partie supérieure. **[!UICONTROL Console]**. Vous devrez peut-être vous **connecter** à l’aide de vos identifiants de compte Google.
1. Sur le **[!UICONTROL Tableau de bord]** page, appuyez sur **[!UICONTROL Créer un projet]**.
1. Dans le **[!UICONTROL Nouveau projet]** , saisissez le nom d’un projet.

     Notez que votre ID de projet est basé sur le nom du projet. Par conséquent, choisissez soigneusement le nom du projet ; il ne peut pas être modifié une fois créé. En outre, vous devrez saisir à nouveau le même ID de projet lorsque vous configurerez YouTube dans Adobe Experience Manager ultérieurement. Il est conseillé de conserver l’ID de projet sur une feuille de papier.
1. Appuyez sur **[!UICONTROL Créer]**.

1. Sur le de votre projet **[!UICONTROL Tableau de bord]**, dans la variable **[!UICONTROL Prise en main]** carte, appuyez sur **[!UICONTROL Activation des API et obtention d’informations d’identification comme des clés]**.
1. Près de la partie supérieure du **[!UICONTROL Tableau de bord]** page, appuyez sur **[!UICONTROL Activer l’API]**.
1. Sur le **[!UICONTROL Bibliothèque]** page, sous API YouTube, appuyez sur **[!UICONTROL API de données YouTube]**.
1. Près de la partie supérieure du **[!UICONTROL API de données YouTube v3]** page, appuyez sur **[!UICONTROL Activer]** pour l’activer.
1. Pour utiliser l’API, vous aurez peut-être besoin d’identifiants. Si nécessaire, appuyez sur **[!UICONTROL Création d’informations d’identification]**.
1. Depuis la liste déroulante **[!UICONTROL Quelle plate-forme utilisez-vous pour appeler l’API ?]**, sélectionnez **[!UICONTROL Serveur web (exemple : node.js, Tomcat)]**.
1. Sous **[!UICONTROL À quelles données aurez-vous accès ?]** sélectionnez **[!UICONTROL Données utilisateur]**.
1. Appuyez sur **[!UICONTROL De quels identifiants ai-je besoin ?]** button.
1. Sous l’en-tête **[!UICONTROL Créer un ID client OAuth 2.0]**, saisissez un nom unique.
1. Dans le champ de texte situé sous le **[!UICONTROL Origines JavaScript autorisées]** saisissez le chemin suivant, en substituant vos propres domaine et numéro de port dans le chemin, puis appuyez sur **[!UICONTROL Entrée]** pour ajouter le chemin à la liste :

   `https://<servername.domain>:<port_number>`

   Par exemple, `https://1a2b3c.mycompany.com:4321`

   **Remarque :** L’exemple du chemin ci-dessus est fourni uniquement à titre illustratif.

1. Dans le champ de texte situé sous le **[!UICONTROL URI de redirection autorisés]** en-tête, saisissez ce qui suit, en substituant vos propres domaine et numéro de port dans le chemin, puis appuyez sur Entrée pour ajouter le chemin à la liste :

   `https://<servername.domain>:<port#>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Par exemple, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **Remarque :** L’exemple du chemin ci-dessus est fourni uniquement à titre illustratif.

1. Appuyer **[!UICONTROL Création d’un ID client]**.
1. Sur la page Informations d’identification, sous la propriété **[!UICONTROL Configuration de l’écran de consentement OAuth 2.0]** , sélectionnez l’adresse Gmail que vous utilisez actuellement.
1. Dans le champ de texte sous l’en-tête **[!UICONTROL Nom de produit présenté aux utilisateurs]**, saisissez les éléments que vous souhaitez afficher sur l’écran du consentement du visiteur.

   L’écran du consentement s’affiche à l’administrateur AEM lorsque celui-ci s’identifie sur YouTube ; AEM contactera YouTube pour l’autorisation.

1. Appuyer **[!UICONTROL Continuer]**.
1. Sous , **[!UICONTROL Téléchargement des informations d’identification]** titre, appuyez sur **[!UICONTROL Télécharger]**.
1. Enregistrez le fichier `client_id.json`.

   Vous en aurez besoin lors de la configuration ultérieure de YouTube dans Adobe Experience Manager.

1. Appuyez sur **[!UICONTROL Terminé]**.

   Vous allez maintenant créer une chaîne YouTube.

### Création d’une chaîne YouTube {#creating-a-youtube-channel}

Pour publier des vidéos sur YouTube, vous devez disposer d’une ou de plusieurs chaînes. Si vous avez déjà créé une chaîne YouTube, vous pouvez ignorer cette étape et passer à la tâche **Ajout de balises pour la publication**.

>[!CAUTION]
>
>Assurez-vous d’avoir déjà configuré un ou plusieurs canaux dans YouTube &amp;ast;before&amp;ast; vous ajoutez des canaux sous Paramètres YouTube dans AEM (voir [Configuration de YouTube dans AEM](#setting-up-youtube-in-aem) ci-dessous). Si vous n’avez pas configuré de chaîne, aucun avertissement ne s’affichera. L’authentification Google a lieu lorsque vous ajoutez une chaîne, mais il n’existe pas d’option permettant de choisir la chaîne vers laquelle la vidéo est envoyée.

**Pour créer une chaîne YouTube :**

1. Accédez à [https://www.youtube.com](https://www.youtube.com/), puis connectez-vous à l’aide des informations d’identification de votre compte Google.
1. Dans le coin supérieur droit de la page YouTube, appuyez sur l’image de votre profil (peut également apparaître sous la forme d’une lettre dans un cercle coloré plein), puis appuyez sur **[!UICONTROL Paramètres YouTube]** (icône d’engrenage rond).
1. Sur le **[!UICONTROL Présentation]** , sous **[!UICONTROL Fonctionnalités supplémentaires]** titre, appuyez sur **[!UICONTROL Afficher tous mes canaux ou créer un nouveau canal]**.
1. Sur le **[!UICONTROL Canaux]** page, appuyez sur **[!UICONTROL Création d’un canal]**.
1. Sur le **[!UICONTROL Compte de marque]** , dans la **[!UICONTROL Nom du compte de marque]** , saisissez un nom d’entreprise ou tout autre nom de canal que vous choisissez à l’endroit où vous souhaitez publier vos ressources vidéo, puis appuyez sur **[!UICONTROL Créer]**.

   Mémorisez le nom de la chaîne, car vous devrez le saisir de nouveau lors de la configuration de YouTube dans AEM.

1. (Facultatif) Si nécessaire, ajoutez d’autres chaînes.

   Vous allez à présent ajouter des balises pour la publication.

### Ajout de balises pour la publication {#adding-tags-for-publishing}

Pour publier vos vidéos sur YouTube, AEM associe des balises à une ou plusieurs chaînes YouTube. Pour ajouter des balises pour la publication, voir [Administration des balises](/help/sites-administering/tags.md).

Ou, si vous prévoyez d’utiliser les balises par défaut dans AEM, vous pouvez ignorer cette tâche et accéder à [Activation de l’agent de réplication de publication YouTube](#enabling-the-youtube-publish-replication-agent).

### Activation de l’agent de réplication de publication YouTube {#enabling-the-youtube-publish-replication-agent}

1. Dans le coin supérieur gauche de l’AEM, appuyez sur le logo AEM, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils > Déploiement > Réplication > Agents sur l’auteur]**.
1. Sur le **[!UICONTROL Agents de l’auteur]** page, appuyez sur **[!UICONTROL Publication YouTube (youtube)]**.
1. Dans la barre d’outils, à droite de Paramètres, appuyez sur **[!UICONTROL Modifier]**.
1. Cochez la case **[!UICONTROL Activé]** pour activer l’agent de réplication.
1. appuyer **[!UICONTROL OK]**.

   Vous allez maintenant installer YouTube dans AEM.

### Configuration de YouTube dans AEM {#setting-up-youtube-in-aem}

1. Dans le coin supérieur gauche de l’AEM, appuyez sur le logo AEM, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils > Déploiement > Cloud Services]**.
1. Sous , **[!UICONTROL Services tiers]** en-tête, sous YouTube, appuyez sur **[!UICONTROL Configurer maintenant]**.
1. Dans le **[!UICONTROL Créer une configuration]** , saisissez un titre (obligatoire) et un nom (facultatif) dans les champs respectifs.
1. Appuyez sur **[!UICONTROL Créer]**.
1. Dans le **[!UICONTROL Paramètres du compte YouTube]** , dans la boîte de dialogue **[!UICONTROL Nom de l’application]** , saisissez l’ID de projet Google.

   Vous avez spécifié l’ID de projet lorsque vous avez précédemment configuré les paramètres de Google Cloud.

   Laissez le champ **[!UICONTROL Paramètre du compte YouTube]** boîte de dialogue ouverte ; vous y reviendrez dans un instant.

1. À l’aide d’un éditeur de texte brut, ouvrez le fichier JSON que vous avez téléchargé et enregistré au cours de la tâche Configuration des paramètres de Google Cloud.
1. Sélectionnez l’intégralité du texte JSON et copiez-le.
1. Revenez au **[!UICONTROL Paramètres du compte YouTube]** de la boîte de dialogue Dans le **[!UICONTROL Configuration JSON]** , collez le texte JSON.
1. Appuyez sur **[!UICONTROL OK]**.

   Vous devez maintenant configurer les chaînes YouTube dans AEM.

1. À droite des **[!UICONTROL Canaux disponibles]**, appuyez sur **[!UICONTROL +]** (icône représentant un signe plus).
1. Dans le **[!UICONTROL Paramètres du canal YouTube]** , dans la boîte de dialogue **[!UICONTROL Titre]** , saisissez le nom du canal que vous avez créé dans la tâche. **C[!UICONTROL Création d’un canal YouTube]** plus tôt.

   Vous pouvez éventuellement ajouter une description.

1. Appuyez sur **[!UICONTROL OK]**.
1. L’authentification YouTube/Google s’affiche. Si vous n’êtes pas déjà connecté à un compte Google Cloud, ignorez cette étape.

   * Saisissez le nom d’utilisateur Google et le mot de passe associés à l’ID de projet Google et au texte JSON ci-dessus.
   * Selon le nombre de chaînes associées à votre compte, deux éléments au moins sont affichés. Sélectionnez une chaîne. Ne sélectionnez pas l’adresse électronique.
   * Dans la page suivante, appuyez sur **[!UICONTROL Accepter]** pour autoriser l’accès à cette chaîne.

1. Appuyez sur **[!UICONTROL Autoriser]**.

   Vous allez maintenant configurer des balises pour la publication.

1. **Configuration de balises pour la publication** - Sur le **[!UICONTROL Cloud Services > YouTube]** , appuyez sur **[!UICONTROL Crayon]** pour modifier la liste des balises que vous souhaitez utiliser.
1. Appuyez sur l’icône de liste déroulante (flèche pointant vers le bas) pour afficher la liste des balises disponibles dans AEM.
1. Appuyez sur une ou plusieurs balises afin de les ajouter.

   Pour supprimer une balise que vous avez ajoutée, sélectionnez-la et appuyez sur **[!UICONTROL X]**.

1. Lorsque vous avez terminé d’ajouter les balises souhaitées, appuyez sur **[!UICONTROL OK]**.

   Vous allez à présent publier des vidéos sur votre chaîne YouTube.

### (Facultatif) Automatisation de la définition des propriétés YouTube par défaut pour vos vidéos chargées {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

Vous pouvez automatiser la définition des propriétés YouTube lors du transfert de vos vidéos. À cet effet, créez un profil de traitement des métadonnées dans AEM.

Pour créer le profil de traitement des métadonnées, vous allez d’abord copier les valeurs des champs **[!UICONTROL Étiquette de champ]**, **[!UICONTROL Associer à la propriété]** et **[!UICONTROL Choix]**, tous situés dans les schémas de métadonnées pour la vidéo. Ensuite, vous allez créer votre propre profil de traitement des métadonnées vidéo YouTube en y ajoutant ces valeurs.

**Pour automatiser éventuellement la définition des propriétés YouTube par défaut pour vos vidéos chargées, procédez comme suit :**

1. Dans le coin supérieur gauche de l’AEM, appuyez sur le logo AEM, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils > Ressources > Schémas de métadonnées]**.
1. Appuyez sur **[!UICONTROL Valeur par défaut]**. (Ne cochez pas la case de sélection à gauche de l’option « Par défaut ».)
1. Sur le **[!UICONTROL default]** , cochez la case à gauche de **[!UICONTROL video]**, puis appuyez sur **[!UICONTROL Modifier]**.
1. Sur le **[!UICONTROL Éditeur de schéma de métadonnées]** , appuyez sur **[!UICONTROL Avancé]** .
1. Sous l’en-tête Publication YouTube, appuyez sur **[!UICONTROL Catégorie YouTube]**. (N’appuyez pas sur la liste déroulante de catégorie YouTube.)
1. Dans la partie droite de la page, sous l’onglet **[!UICONTROL Paramètres]**, procédez comme suit :

   * Dans le champ de texte **[!UICONTROL Libellé du champ]**, sélectionnez la valeur et copiez-la.

      Collez la valeur copiée dans un éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

   * Dans le champ de texte **[!UICONTROL Associer à la propriété]**, sélectionnez la valeur et copiez-la.

      Collez la valeur copiée dans l’éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

   * Sous **[!UICONTROL Choix]**, sélectionnez la valeur par défaut à utiliser (comme « Personnes et blogs » ou « Science et technologie ») et copiez-la.


      Collez la valeur copiée dans l’éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

1. Sous l’en-tête Publication YouTube, appuyez sur **[!UICONTROL Confidentialité YouTube]**. (N’appuyez pas dans la liste déroulante Confidentialité YouTube.)
1. Dans la partie droite de la page, sous l’onglet **[!UICONTROL Paramètres]**, procédez comme suit :

   * Dans le champ de texte **[!UICONTROL Libellé du champ]**, sélectionnez la valeur et copiez-la.

      Collez la valeur copiée dans un éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

   * Dans le champ de texte **[!UICONTROL Associer à la propriété]**, sélectionnez la valeur et copiez-la.

      Collez la valeur copiée dans l’éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

   * Sous **[!UICONTROL Choix]**, sélectionnez la valeur par défaut à utiliser et copiez-la. Notez que les choix sont regroupés par paires. Le champ inférieur de la paire correspond à la valeur par défaut que vous souhaitez copier, comme valeur publique, non répertoriée ou privée.

      Collez la valeur copiée dans l’éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

1. Près du coin supérieur droit du **[!UICONTROL Éditeur de schéma de métadonnées]** page, appuyez sur **[!UICONTROL Annuler]**.
1. Dans le coin supérieur gauche de l’AEM, appuyez sur le logo AEM, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils > Ressources > Profils de métadonnées]**.

1. Sur le **[!UICONTROL Profils de métadonnées]** , près du coin supérieur droit de la page, appuyez sur **[!UICONTROL Créer]**. Dans le **[!UICONTROL Ajout d’un profil de métadonnées]** , dans la boîte de dialogue **[!UICONTROL Titre du profil]** Champ de texte, saisissez le nom `YouTube Video`.
1. Sur le **[!UICONTROL Éditeur de profil de métadonnées]** , appuyez sur **[!UICONTROL Avance]** .
1. Ajoutez les valeurs de publication YouTube copiées au profil en procédant comme suit :

   * Dans la partie droite de la page, appuyez sur l’onglet **[!UICONTROL Créer le formulaire]**.
   * Faites glisser le composant intitulé **[!UICONTROL En-tête de section]** à gauche et déposez-le dans la zone de formulaire.
   * Appuyer **[!UICONTROL Libellé du champ]** pour sélectionner le composant.
   * Sur le côté droit de la page, sous **[!UICONTROL Paramètres]** , dans le **[!UICONTROL Libellé du champ]** champ de texte, saisissez `YouTube Publishing`.
   * Appuyez sur le bouton **[!UICONTROL Créer un formulaire]** , puis faites glisser le composant intitulé **[!UICONTROL Une seule ligne de texte]** et déposez-le sous le **[!UICONTROL Publication YouTube]** en-tête que vous venez de créer.
   * Appuyer **[!UICONTROL Libellé du champ]** pour sélectionner le composant.
   * Sur le côté droit de la page, sous **[!UICONTROL Paramètres]** , collez le **[!UICONTROL Publication YouTube]** valeurs (**[!UICONTROL Libellé du champ]** et **[!UICONTROL Associer à la propriété]** que vous avez copié précédemment dans leurs champs respectifs sur le formulaire. Collez le **[!UICONTROL Choix]** dans la variable **[!UICONTROL Valeur par défaut]** champ .

1. Ajoutez les valeurs de confidentialité YouTube copiées au profil en procédant comme suit :

   * Dans la partie droite de la page, appuyez sur l’onglet **[!UICONTROL Créer le formulaire]**.
   * Faites glisser le composant intitulé **[!UICONTROL En-tête de section]** à gauche et déposez-le dans la zone de formulaire.
   * Appuyer **[!UICONTROL Libellé du champ]** pour sélectionner le composant.
   * Dans la partie droite de la page, sous l’onglet Paramètres, dans le champ de texte Libellé du champ, saisissez `YouTube Privacy`.
   * Appuyez sur le bouton **[!UICONTROL Créer un formulaire]** , puis faites glisser le composant intitulé **[!UICONTROL Une seule ligne de texte]** et déposez-le sous le **[!UICONTROL Confidentialité YouTube]** en-tête que vous venez de créer.
   * Appuyer **[!UICONTROL Libellé du champ]** pour sélectionner le composant.
   * Sur le côté droit de la page, sous **[!UICONTROL Paramètres]** , collez le **[!UICONTROL Publication YouTube]** valeurs (**[!UICONTROL Libellé du champ]** et **[!UICONTROL Associer à la propriété]** que vous avez copié précédemment dans leurs champs respectifs sur le formulaire. Collez le **[!UICONTROL Choix]** dans la variable **[!UICONTROL Valeur par défaut]** champ .

1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer]**.
1. Appliquez le profil des métadonnées de publication YouTube aux dossiers dans lesquels vous allez transférer des vidéos. Vous devez avoir configuré le profil des métadonnées et le profil vidéo.

   Voir [Profils de métadonnées](metadata-profiles.md) et [Profils vidéo](video-profiles.md).

### Publication de vidéos sur votre chaîne YouTube {#publishing-videos-to-your-youtube-channel}

Vous devez maintenant associer les balises que vous avez précédemment ajoutées aux ressources vidéo. Ce processus permet à AEM de déterminer les ressources à publier sur votre chaîne YouTube.

Pour publier du contenu depuis YouTube, AEM utilise le workflow **[!UICONTROL Publier sur YouTube]**, qui vous permet de surveiller la progression et de consulter toutes les informations d’échec.
Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Pour publier des vidéos sur votre chaîne YouTube, procédez comme suit :**

1. Dans AEM, accédez à la ressource vidéo que vous souhaitez publier sur votre chaîne YouTube.
1. Sélectionnez la ressource vidéo.

   Quelle que soit la ressource vidéo que vous sélectionnez (comme la vidéo source d’origine ou un rendu encodé de cette vidéo), la vidéo de source d’origine est toujours chargée.

1. Dans la barre d’outils, appuyez sur **[!UICONTROL Propriétés]**.
1. Dans le **[!UICONTROL De base]** sous l’en-tête Métadonnées, appuyez sur . **[!UICONTROL Parcourir]** à droite du **[!UICONTROL Balises]** champ .
1. Sur le **[!UICONTROL Sélectionner des balises]** , accédez aux balises à utiliser, puis sélectionnez une ou plusieurs balises.
1. Dans le coin supérieur droit de la page, appuyez sur la **[!UICONTROL Confirmer]** icône .
1. Dans le coin supérieur droit de la page des propriétés de la vidéo, appuyez sur **[!UICONTROL Enregistrer]**.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Publier > Publier]**.

   Vous avez la possibilité de vérifier la vidéo publiée sur votre chaîne YouTube.

### (Facultatif) Vérification de la vidéo publiée sur YouTube {#optional-verifying-the-published-video-on-youtube}

Vous pouvez surveiller la progression de votre publication YouTube (ou de l’annulation de la publication).

Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

Le délai de publication peut varier considérablement en fonction de nombreux facteurs, comme le format de la vidéo originale, la taille du fichier et le trafic de téléchargement. La publication peut prendre de quelques minutes à plusieurs heures. Sachez également que les formats de haute résolution sont rendus beaucoup plus lentement. Par exemple, les vidéos à 720p et 1 080p prennent beaucoup plus de temps à s’afficher que les vidéos à 480p.

Au bout de huit heures, si un message de statut indiquant **[!UICONTROL Téléchargé (en cours de traitement, veuillez patienter)]** s’affiche toujours, essayez de supprimer la vidéo de notre site et chargez-la à nouveau.

### Liaison d’URL YouTube à votre application web {#linking-youtube-urls-to-your-web-application}

Une fois que vous avez publié la vidéo, une chaîne URL YouTube est générée par Dynamic Media. Lorsque vous copiez l’URL YouTube, elle est envoyée au Presse-Papiers dont vous pouvez coller le contenu, le cas échéant, sur les pages de votre site web ou de votre application.

L’URL YouTube ne peut pas être copiée tant que vous n’avez pas publié la ressource vidéo sur YouTube.

**Pour lier les URL YouTube à votre application web, procédez comme suit :**

1. Accédez à YouTube *publié* ressource vidéo dont vous souhaitez copier l’URL, puis sélectionnez-la.

   N’oubliez pas que les URL YouTube peuvent être copiées uniquement *après* la *publication* des ressources vidéo sur YouTube.

1. Dans la barre d’outils, appuyez sur **[!UICONTROL Propriétés]**.
1. Sélectionnez l&#39;onglet **[!UICONTROL Avancé]**.
1. Sous , **[!UICONTROL Publication YouTube]** , dans la **[!UICONTROL URL YouTube]** Listez, sélectionnez et copiez le texte de l’URL dans votre navigateur web pour prévisualiser la ressource ou l’ajouter à votre page de contenu web.

### Annulation de la publication de vidéos pour les supprimer de YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Lorsque vous annulez la publication d’une ressource vidéo dans AEM, la vidéo est supprimée de YouTube.

>[!CAUTION]
>
>Si vous supprimez une vidéo directement sur YouTube, AEM l’ignore et continue de se comporter comme si la vidéo était toujours publiée sur YouTube. Veillez toujours à annuler la publication d’une ressource vidéo sur YouTube via AEM.

Pour supprimer du contenu depuis YouTube, AEM utilise le processus **[!UICONTROL Annuler la publication sur YouTube]**, qui vous permet de surveiller la progression et de consulter toutes les informations d’échec.
Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Pour annuler la publication de vidéos afin de les supprimer de YouTube, procédez comme suit :**

1. Dans le coin supérieur gauche de l’AEM, appuyez sur le logo AEM, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils]** > **[!UICONTROL Ressources]**.
1. Accédez à la ressource vidéo que vous souhaitez publier sur votre chaîne YouTube.
1. Dans un mode de sélection de ressource, sélectionnez une ou plusieurs ressources vidéo publiées.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Annuler la publication]** > **[!UICONTROL Annuler la publication]**.

## Surveillance du codage vidéo et de la progression de la publication sur YouTube {#monitoring-video-encoding-and-youtube-publishing-progress}

Lorsque vous téléchargez une nouvelle vidéo vers un dossier auquel un codage vidéo a été appliqué ou que vous publiez votre vidéo sur YouTube, vous pouvez contrôler la manière dont votre codage vidéo/publication YouTube progresse (ou échoue) de plusieurs façons. La progression de la publication YouTube réelle est uniquement disponible via les journaux mais sa réussite ou son échec sont également répertoriés et décrits dans la procédure suivante. En outre, vous pouvez recevoir des notifications par courrier électronique lorsqu’un processus de publication YouTube ou un codage vidéo est terminé ou interrompu.

### Surveillance de la progression {#monitoring-progress}

Pour surveiller la progression (notamment l’échec du codage ou de la publication YouTube) :

1. Consultez la progression du codage vidéo dans votre dossier de ressources :

   * Dans **[!UICONTROL Mode Carte]**, la progression du codage vidéo s’affiche sur la ressource en pourcentage. Si une erreur se produit, ces informations s’affichent également sur cette ressource.

      ![chlimage_1-429](assets/chlimage_1-429.png)

   * Dans **[!UICONTROL Mode Liste]**, la progression du codage vidéo s’affiche dans la variable **[!UICONTROL État du traitement]** colonne . Si une erreur se produit, le message suivant s’affiche dans la même colonne.

      ![chlimage_1-430](assets/chlimage_1-430.png)

      Cette colonne ne s’affiche pas par défaut. Pour activer la colonne, sélectionnez **[!UICONTROL Paramètres d’affichage]** de la **[!UICONTROL Vues]** et ajoutez le **[!UICONTROL État du traitement]** colonne et appuyez sur **[!UICONTROL Mettre à jour]**.

      ![chlimage_1-431](assets/chlimage_1-431.png)

1. Consultez la progression dans les détails de la ressource. Lorsque vous appuyez sur une ressource, ouvrez le menu déroulant et sélectionnez **[!UICONTROL Chronologie]**. Pour le réduire à des activités de processus comme le codage ou la publication YouTube, sélectionnez **[!UICONTROL Processus]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   Toutes les informations de processus, telles que le codage s’affichent dans la chronologie. Pour la publication YouTube, la variable **[!UICONTROL Workflow]** La chronologie comprend également le nom du canal YouTube et l’URL de la vidéo YouTube. En outre, toutes les notifications d’échec s’affichent dans la variable **[!UICONTROL Workflow]** chronologie.

   >[!NOTE]
   >
   >L’enregistrement final des messages d’erreur/d’échec peut prendre du temps en raison de plusieurs configurations de workflow sur **[!UICONTROL reprises]**, **[!UICONTROL délai de reprise]**, et **[!UICONTROL timeout]** de [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), par exemple :
   >
   >* Configuration de la file d’attente des tâches Apache Sling
   >* Gestionnaire des tâches du processus externe de processus Adobe Granite
   >* File d’attente des délais d’attente des processus Granite

   > 
   >Vous pouvez ajuster les propriétés **[!UICONTROL reprises]**, **[!UICONTROL délai de reprise]** et **[!UICONTROL délai d’expiration]** dans ces configurations.

1. Pour les workflows en cours, voir **Instances de workflow** disponible à partir de **[!UICONTROL Outils > Processus > Instances]**.

   >[!NOTE]
   >
   >Vous aurez peut-être besoin de droits administratifs pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   Sélectionnez l’instance et appuyez sur **[!UICONTROL Ouvrir l’historique]**.

   ![chlimage_1-434](assets/chlimage_1-434.png)

   Dans la **[!UICONTROL Instances de workflow]** vous pouvez également suspendre, arrêter ou renommer des workflows. Voir [Administration des workflows](/help/sites-administering/workflows-administering.md) pour plus d’informations.

1. Pour les tâches en échec, voir **Échecs de workflow** disponible à partir de **[!UICONTROL Outils > Processus > Échecs]**. L’**[!UICONTROL échec du processus]** répertorie toutes les activités du processus ayant échoué.

   >[!NOTE]
   >
   >Vous aurez peut-être besoin de droits administratifs pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >L’enregistrement final du message d’erreur peut prendre du temps en raison de plusieurs configurations de workflow sur **[!UICONTROL reprises]**, **[!UICONTROL délai de reprise]**, et **[!UICONTROL timeout]** de [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), par exemple :
   >
   >* Configuration de la file d’attente des tâches Apache Sling
   >* Gestionnaire des tâches du processus externe de processus Adobe Granite
   >* File d’attente des délais d’attente des processus Granite

   >
   >Vous pouvez ajuster les propriétés **[!UICONTROL reprises]**, **[!UICONTROL délai de reprise]** et **[!UICONTROL délai d’expiration]** dans ces configurations.

1. Pour les workflows terminés, voir **[!UICONTROL Archive de workflow]** disponible à partir de **[!UICONTROL Outils > Processus > Archiver]**. La liste **[!UICONTROL Archive de workflow]** répertorie toutes les activités de workflow qui ont réussi.

   Vous aurez peut-être besoin de droits administratifs pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. Vous pouvez recevoir des notifications par courrier électronique sur les tâches de processus annulées ou qui ont échoué. Ces notifications peuvent être configurées par un administrateur.
Voir [Configuration des notifications par courrier électronique](#configuring-e-mail-notifications).

#### Configuration des notifications par e-mail {#configuring-e-mail-notifications}

Vous aurez peut-être besoin de droits administratifs pour accéder au menu **[!UICONTROL Outils]**.

La façon dont vous configurez les notifications varie si vous souhaitez recevoir des notifications pour les tâches de codage ou pour les tâches de publication YouTube :

* Pour les tâches de codage, vous pouvez accéder à la page de configuration de toutes les notifications électroniques de workflow AEM à l’adresse **[!UICONTROL Outils > Opérations > Console web]** et en recherchant **[!UICONTROL Service de notification par courrier électronique des workflows Day CQ]**. Voir [Configuration des notifications électroniques dans AEM](/help/sites-administering/notification.md). Vous pouvez cocher ou décocher les cases correspondant à **[!UICONTROL Notifier lors de l’abandon]** ou **[!UICONTROL Notification à la fin]** en conséquence.

* Pour les tâches de publication YouTube, procédez comme suit :

1. Dans AEM, sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]**.
1. Sélectionnez la **[!UICONTROL Publication sur YouTube]** workflow, puis appuyez sur **[!UICONTROL Modifier]**.
1. Cliquez avec le bouton droit de la souris sur le **[!UICONTROL Téléchargement de YouTube]** étape de workflow, puis appuyez sur **[!UICONTROL Modifier]**.
1. Appuyez sur le bouton **[!UICONTROL Argument]s** .
1. Vous pouvez cocher ou décocher les cases suivantes :

   * **[!UICONTROL Début de la publication]**
   * **[!UICONTROL Échec de la publication]**
   * **[!UICONTROL Publication terminée]**, qui inclut des informations sur les canaux et les URL

   Décocher une case signifie que vous ne recevrez pas de notifications par courrier électronique spécifiques du processus publication YouTube.

   >[!NOTE]
   >
   >Ces courriers électroniques sont spécifiques à YouTube et sont un complément aux notifications électroniques génériques des processus. Par conséquent, vous pouvez recevoir deux ensembles de notifications électroniques : une notification générique disponible dans le **Service de notification par courrier électronique de processus Day CQ** et une notification spécifique à YouTube en fonction de vos paramètres de configuration.

## Affichage des rapports vidéo {#viewing-video-reports}

Des rapports vidéo sont disponibles lorsque vous exécutez Dynamic Media en mode hybride. Les rapports ne sont pas disponibles lorsque vous exécutez Dynamic Media en mode Scene7.

Les rapports vidéo affichent plusieurs mesures agrégées sur une période spécifiée pour vous permettre de vérifier que les vidéos individuelles et agrégées publiées présentent les performances attendues. Les données des mesures principales suivantes sont agrégées pour toutes les vidéos publiées sur l’ensemble de votre site web :

* Lancements de vidéo
* Taux d’achèvement
* Temps moyen sur la vidéo
* Durée totale sur la vidéo
* Vidéos par visite

Un tableau de toutes les vidéos *publiées* est également fourni pour vous permettre de suivre les vidéos les plus visionnées sur votre site web en fonction du total des lancements de vidéo.

Lorsque vous appuyez sur le nom d&#39;une vidéo dans la liste, le rapport sur la rétention de l&#39;audience (taux de déperdition) de la vidéo s&#39;affiche sous la forme d&#39;un graphique en courbes. Le graphique affiche le nombre de visionnages à tout moment de la lecture vidéo. Lorsque vous lisez la vidéo, la barre verticale effectue un suivi en synchronisation avec l&#39;indicateur temporel du lecteur. Des baisses dans les données du graphique en courbes indiquent où le désintérêt de votre audience augmente.

Si la vidéo a été codée en dehors d’Adobe Experience Manager Dynamic Media, le graphique sur la rétention de l’audience (taux de déperdition) et les données de pourcentage de lecture du tableau ne sont pas disponibles.

Voir aussi [Configuration des Services cloud Dynamic Media.](/help/assets/config-dynamic.md)

>[!NOTE]
>
>Le suivi et les données de rapport reposent exclusivement sur l’utilisation du lecteur vidéo Dynamic Media et du paramètre de lecteur vidéo prédéfini associé. Vous ne pouvez donc pas effectuer le suivi et créer de rapports sur des vidéos qui sont lues par d’autres lecteurs vidéo.

Par défaut, la première fois que vous utilisez l’option Rapports vidéo, le rapport affiche des données vidéo du premier jour du mois en cours jusqu’à la date du mois en cours. Vous pouvez toutefois remplacer la période par défaut par la vôtre. La prochaine fois que vous utiliserez l’option Rapports vidéo, la période que vous avez spécifiée sera utilisée.

Pour que les rapports vidéo fonctionnent correctement, un identifiant de suite de rapports est automatiquement créé lors de la configuration des Cloud Services Dynamic Media. Dans le même temps, l’identifiant de suite de rapports est transmis au serveur de publication pour qu’il soit disponible pour la fonctionnalité de copie d’URL lors de la prévisualisation de ressources. Cela nécessite toutefois que le serveur de publication soit déjà configuré. Si le serveur de publication n’est pas configuré, vous pouvez effectuer une publication pour afficher le rapport vidéo. Vous devez toutefois retourner dans la configuration du cloud Dynamic Media et appuyer sur **OK**.

**Pour afficher un rapport vidéo, procédez comme suit :**

1. Dans le coin supérieur gauche de l’AEM, appuyez sur le logo AEM, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports vidéo]**.
1. Dans la page Rapport vidéo, effectuez l’une des opérations suivantes :

   * Dans le coin supérieur droit, appuyez sur l’icône **[!UICONTROL Actualiser le rapport vidéo.]**

      Vous ne devez utiliser la commande d’actualisation que si la date de fin du rapport correspond à la date du jour. Vous affichez ainsi le suivi vidéo qui a eu lieu depuis la dernière exécution du rapport.

   * Dans le coin supérieur droit, appuyez sur l’icône **[!UICONTROL Sélecteur de date.]**

      Indiquez la période de début et de fin pour laquelle vous souhaitez obtenir les données vidéo, puis appuyez sur **[!UICONTROL Exécuter le rapport]**.
   Le **[!UICONTROL Mesures principales]** la zone de groupe identifie différentes mesures d’agrégat pour l’ensemble *publié* vidéos sur votre site.

1. Dans le tableau qui répertorie les principales vidéos publiées, appuyez sur le nom d’une vidéo pour la lire et afficher également le rapport sur la rétention de l’audience (taux de déperdition) de celle-ci.

### Affichage de rapports vidéo à partir d’une visionneuse de vidéos que vous avez créée à l’aide du SDK de la visionneuse Dynamic Media HTML5 {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

Si vous utilisez une visionneuse de vidéos prête à l’emploi fournie par Dynamic Media ou si vous avez créé un paramètre prédéfini de visionneuse personnalisée reposant sur une visionneuse de vidéos prête à l’emploi, aucune autre étape n’est nécessaire pour afficher les rapports vidéo. Cependant, si vous avez créé votre propre visionneuse de vidéos à partir de l’API du kit de développement de visionneuses HTML5, procédez comme suit pour vous assurer que la visionneuse de vidéos envoie des événements de suivi aux rapports vidéo Dynamic Media.

Utilisez la variable [Guide de référence des visionneuses Adobe Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html) et le [API du SDK de la visionneuse HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) pour créer vos propres visionneuses de vidéos.

Pour afficher des rapports vidéo basés sur une visionneuse de vidéos que vous avez créée à l’aide de l’API du kit de développement de visionneuses HTML5 :

1. Accédez à une ressource vidéo publiée.
1. Près du coin supérieur gauche de la page du fichier, sélectionnez **[!UICONTROL Visionneuses]** dans la liste déroulante.
1. Sélectionnez un paramètre prédéfini de visionneuse de vidéos et copiez le code intégré.
1. Dans le code intégré, recherchez la ligne suivante :

   `videoViewer.setParam("config2", "<value>");`

   Le paramètre `config2` active le suivi dans les visionneuses HTML5. Il s’agit également d’un paramètre prédéfini spécifique à l’entreprise qui contient des informations de configuration pour les rapports vidéo et pour les configurations Adobe Analytics propres au client.

   La valeur correcte du paramètre config2 figure dans le **[!UICONTROL code intégré]** et la fonction Copier l’**[!UICONTROL URL]**. Dans l’URL provenant de la commande Copier l’**[!UICONTROL URL]**, le paramètre à rechercher est `&config2=<value>`. La valeur est pratiquement toujours `companypreset`, mais dans certains cas elle peut également être `companypreset-1`, `companypreset-2`, etc.

1. Dans le code de la visionneuse de vidéos personnalisée, ajoutez le fichier AppMeasurementBridge.jsp à la page de la visionneuse en procédant comme suit :

   * Tout d’abord, déterminez si vous avez besoin du paramètre `&preset`.


      Si la variable `config2` parameter is `companypreset`, vous devez *not* need `&preset=parameter`.

      Si le paramètre `config2` a une autre valeur, attribuez au paramètre preset la même valeur que le paramètre `config2`. Par exemple, si `config2=companypreset-2`, ajoutez `&param2=companypreset-2` à l’URL d’AppMeasurmentBridge.jsp.

   * Ajoutez ensuite le script AppMeasurementBridge.jsp :

      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Créez le composant TrackingManager en effectuant les opérations suivantes :

   * Après avoir appelé `s7sdk.Util.init();`, créez une instance TrackingManager pour suivre les événements en ajoutant le code suivant :

      `var trackingManager = new s7sdk.TrackingManager();`

   * Connectez les composants à TrackingManager en procédant comme suit :

      Dans le gestionnaire d’événements `s7sdk.Event.SDK_READY`, attachez le composant à suivre à TrackingManager.

      Par exemple, si le composant est `videoPlayer`, ajoutez

      `trackingManager.attach(videoPlayer);`

      pour joindre le composant à TrackingManager. Pour suivre plusieurs visionneuses sur une page, utilisez plusieurs composants de gestionnaire de suivi.

   * Créez l’objet AppMeasurementBridge en ajoutant ce qui suit :

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

   * Ajoutez la fonction de suivi en ajoutant le code suivant :

      ```
      trackingManager.setCallback(appMeasurementBridge.track, 
       appMeasurementBridge);
      ```
   L’objet appMeasurementBridge dispose d’une fonction de suivi intégrée. Vous pouvez toutefois fournir votre propre fonction pour prendre en charge plusieurs systèmes de suivi ou d’autres fonctionnalités.

<!--    For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

## Ajout de sous-titres à une vidéo {#adding-captions-to-video}

Vous pouvez étendre la portée de vos vidéos aux marchés mondiaux en ajoutant des sous-titres aux vidéos uniques ou aux visionneuses de vidéos adaptatives. En ajoutant des sous-titres, vous évitez d’avoir à réenregistrer le son ou de recourir à des locuteurs natifs pour réenregistrer la partie audio dans les différentes langues. La vidéo est lue dans la langue dans laquelle elle a été enregistrée. Les sous-titres en langue étrangère s’affichent pour que les personnes parlant d’autres langues puissent néanmoins comprendre la partie audio.

Le sous-titrage permet également une plus grande accessibilité pour les personnes sourdes ou malentendantes.

>[!NOTE]
>
>Le lecteur vidéo utilisé doit prendre en charge l’affichage des sous-titres.

Dynamic Media peut convertir des fichiers de sous-titres au format JSON (JavaScript Object Notation). Cette conversion signifie que vous pouvez intégrer le texte JSON dans une page web sous forme de transcription masquée complète de la vidéo. Les moteurs de recherche peuvent ensuite analyser et indexer le contenu pour permettre de trouver plus facilement les vidéos et fournir aux utilisateurs des informations supplémentaires sur le contenu des vidéos.

Voir [Diffusion de contenu statique (hors image)](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html?lang=fr#image-serving-api) dans le *Aide de l’API Dynamic Media Image Serving and Rendering* pour plus d’informations sur l’utilisation de la fonction JSON dans une URL.

**Pour ajouter des sous-titres à une vidéo :**

1. Utilisez une application tierce ou un service de création de fichiers de sous-titres de vidéo.

   Assurez-vous que le fichier que vous créez est conforme à la norme WebVTT (Web Video Text Tracks). L’extension de fichier des fichiers de sous-titres est .vtt. D’autres informations sur la norme de sous-titrage WebVTT sont disponibles.

   Reportez-vous à la section [WebVTT : The web video text tracks format](https://dev.w3.org/html5/webvtt/).

   Il existe des outils et des services gratuits et payants que vous pouvez utiliser pour créer les fichiers de sous-titres en dehors de Dynamic Media. Par exemple, pour créer un fichier de sous-titres vidéo simple sans style, vous pouvez utiliser l’outil de création et de modification de sous-titres en ligne gratuit suivant :

   [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   Pour de meilleurs résultats, utilisez cet outil dans Internet Explorer 9 ou version ultérieure, dans Google Chrome ou Safari.

   Dans l’outil, dans la variable **[!UICONTROL Saisie de l’URL du fichier vidéo]** collez l’URL copiée de votre fichier vidéo, puis appuyez sur **[!UICONTROL Chargement]**. Voir [Obtention d’une URL pour une ressource](linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) pour obtenir l’URL du fichier vidéo proprement dit, que vous pouvez coller ensuite dans le champ **[!UICONTROL Saisir l’URL du fichier vidéo]**. Internet Explorer, Chrome ou Safari peuvent alors lire la vidéo en mode natif.

   À présent, suivez les instructions à l’écran du site pour créer et enregistrer votre fichier WebVTT. Lorsque vous avez terminé, copiez le contenu du fichier de sous-titres et collez-le dans un éditeur de texte brut, puis enregistrez-le avec une extension de fichier .vtt.

   >[!NOTE]
   >
   >Pour une prise en charge internationale des sous-titres vidéo dans différentes langues, n’oubliez pas que la norme WebVTT implique de créer des fichiers .vtt distincts et des appels pour chaque langue à prendre en charge.

   En règle générale, vous devez attribuer au fichier de sous-titres VTT le même nom qu’au fichier vidéo et vous lui ajoutez l’indicateur de paramètres régionaux, comme -EN, -FR ou -DE, et ainsi de suite. Ainsi, vous pouvez automatiser aisément la génération des URL de vidéo avec le système de gestion de contenu web existant.

1. Dans AEM, chargez votre fichier de sous-titres WebVTT dans DAM.
1. Accédez à la ressource vidéo *publiée* à associer au fichier de sous-titres que vous avez chargé.

   N’oubliez pas que les URL ne peuvent être copiées qu’*après* la *publication* des ressources.

   Voir [Publication de ressources](publishing-dynamicmedia-assets.md).

1. Utilisez l’une des méthodes suivantes :

   * Pour une expérience de visionneuse de vidéos pop-up, appuyez sur **[!UICONTROL URL]**. Dans la boîte de dialogue URL, sélectionnez l’URL et copiez-la dans le Presse-papiers, puis collez-la dans un éditeur de texte simple. Ajoutez l’URL copiée de la vidéo avec la syntaxe suivante :

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      Notez le « `,1` » à la fin du chemin du fichier de sous-titres. Juste après l’extension de fichier .vtt dans le chemin d’accès, vous avez la possibilité d’activer ou de désactiver le bouton de sous-titres dans la barre de lecteur vidéo en définissant la valeur respectivement sur « `,1` » ou « `,0` ».

   * Pour une expérience de visionneuse de vidéos intégrée, appuyez sur **[!UICONTROL Code intégré]**. Dans la boîte de dialogue Code intégré, sélectionnez le code intégré et copiez-le dans le Presse-papiers, puis collez-le dans un simple éditeur de texte. Ajoutez le code intégré copié avec la syntaxe suivante :

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      Notez le « `,1` » à la fin du chemin du fichier de sous-titres. Juste après l’extension de fichier .vtt dans le chemin d’accès, vous avez la possibilité d’activer ou de désactiver le bouton de sous-titres dans la barre de lecteur vidéo en définissant la valeur respectivement sur « `,1` » ou « `,0` ».

## Ajout de marqueurs de chapitre à la vidéo {#adding-chapter-markers-to-video}

Vous pouvez faciliter la lecture et le parcours de vos vidéos les plus longues en ajoutant des marqueurs de chapitre aux vidéos uniques ou aux visionneuses de vidéos adaptatives. Lorsqu’un utilisateur lit la vidéo, il peut appuyer sur les marqueurs de chapitre dans la chronologie de la vidéo (également appelée défilement vidéo) pour accéder facilement à son point ciblé ou accéder immédiatement à un nouveau contenu, à des démonstrations, à des tutoriels, etc.

>[!NOTE]
>
>Le lecteur vidéo utilisé doit prendre en charge l’utilisation des marqueurs de chapitre. Les lecteurs vidéo Dynamic Media prennent en charge les marqueurs de chapitre, mais l’utilisation de lecteurs vidéo tiers ne le permet pas.

Si vous le souhaitez, vous pouvez créer votre propre visionneuse personnalisée, et lui donner le nom de votre marque, avec des chapitres au lieu d’utiliser le paramètre prédéfini de la visionneuse de vidéos. Pour plus d’informations sur la création de votre propre visionneuse HTML5 avec navigation par chapitre, dans l’API SDK de visionneuse HTML5 par Adobe, reportez-vous à la section &quot;Personnalisation du comportement à l’aide de modificateurs&quot; sous les classes . `s7sdk.video.VideoPlayer` et `s7sdk.video.VideoScrubber`. Voir [API du SDK de la visionneuse HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) documentation.

Vous créez une liste de chapitres pour votre vidéo un peu de la même façon que vous créez des sous-titres. Autrement dit, vous créez un fichier WebVTT. Notez toutefois que ce fichier doit être distinct de tout fichier de sous-titrage WebVTT que vous pourriez également être amené à utiliser ; vous ne pouvez pas combiner les sous-titres et les chapitres dans un fichier WebVTT.

Vous pouvez utiliser l’exemple suivant comme un exemple du format que vous pouvez utiliser pour créer un fichier WebVTT avec une navigation par chapitre :

### Fichier WebVTT avec navigation par chapitre vidéo {#webvtt-file-with-video-chapter-navigation}

```xml
WEBVTT 
Chapter 1 
00:00.000 --> 01:04.364 
The bicycle store behind it all. 
Chapter 2 
01:04.364 --> 02:00.944 
Creative Cloud. 
Chapter 3 
02:00.944 --> 03:02.937 
Ease of management for a working solution. 
Chapter 4 
03:02.937 --> 03:35.000 
Cost-efficient access to rapidly evolving technology.
```

Dans l’exemple ci-dessus, le `Chapter 1` est l’identifiant de repère et il est facultatif. La période de repère `00:00:000 --> 01:04:364` indique l’heure de début et l’heure de fin du chapitre au format `00:00:000`. Les trois derniers chiffres sont les millisecondes et peuvent être laissés sur `000`, selon vos préférences. Le titre du chapitre `The bicycle store behind it all` est la description réelle du contenu du chapitre. L’identifiant de repère, l’heure de départ du repère, ainsi que le titre du chapitre apparaissent tous dans une fenêtre contextuelle du lecteur vidéo lorsqu’un utilisateur pointe la souris sur un point de repère visuel dans la chronologie de la vidéo.

Étant donné que vous utilisez une visionneuse de vidéos HTML5, assurez-vous que le fichier de chapitres que vous créez est conforme à la norme WebVTT (Web Video Text Tracks). L’extension de nom de fichier de chapitres est .vtt. D’autres informations sur la norme de sous-titrage WebVTT sont disponibles.

Reportez-vous à la section [WebVTT : The web video text tracks format](https://dev.w3.org/html5/webvtt/)

**Pour ajouter des marqueurs de chapitre à la vidéo :**

1. Dans un éditeur de texte simple (en dehors d’AEM), créez votre fichier de chapitres vidéo.

   Pour une prise en charge internationale des chapitres vidéo dans des langues autres que l’anglais, n’oubliez pas que la norme WebVTT implique de créer des fichiers .vtt distincts et des appels pour chaque langue à prendre en charge.

1. Enregistrez le `.vtt` pour éviter des problèmes de rendu des caractères dans le texte du titre du chapitre.

   En règle générale, vous attribuez au fichier de chapitres VTT le même nom que celui du fichier vidéo et lui ajoutez le mot « chapitres ». Ainsi, vous pouvez automatiser aisément la génération des URL de vidéo avec le système de gestion de contenu web existant.
1. Dans AEM, chargez votre fichier de chapitres WebVTT.

   Voir la section [Chargement des ressources](managing-assets-touch-ui.md#uploading-assets).

1. Utilisez l’une des méthodes suivantes :

   <table> 
     <tbody> 
      <tr> 
       <td>Pour une expérience de visionneuse de vidéos pop-up</td> 
       <td> 
       <ol> 
       <li>Accédez à la ressource vidéo <i>publiée</i> à associer au fichier de chapitres que vous avez chargé. N’oubliez pas que les URL ne peuvent être copiées qu’<i>après</i> la <i>publication</i> des ressources. Voir <a href="/help/assets/publishing-dynamicmedia-assets.md">Publication de ressources</a>.</li> 
       <li>Dans le menu déroulant, appuyez sur <strong>Visionneuses</strong>.</li> 
       <li>Dans le rail de gauche, appuyez sur le nom du paramètre prédéfini de visionneuse de vidéos. Un aperçu de la vidéo s’ouvre dans une page distincte.</li> 
       <li>Dans le rail de gauche, dans la partie inférieure, appuyez sur <strong>URL</strong>.</li> 
       <li>Dans la boîte de dialogue URL, sélectionnez l’URL et copiez-la dans le Presse-papiers, puis collez-la dans un simple éditeur de texte.</li> 
       <li>Ajoutez l’URL copiée de la vidéo avec la syntaxe suivante pour l’associer à l’URL copiée dans votre fichier de chapitres :<br /> <br /> <code>&amp;navigation=&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;</code><br /> </li> 
      </ol> </td> 
      </tr> 
      <tr> 
       <td>Pour une expérience de visionneuse de vidéos incorporée<br /> </td> 
       <td> 
       <ol> 
       <li>Accédez à la ressource vidéo <i>publiée</i> à associer au fichier de chapitres que vous avez chargé. N’oubliez pas que les URL ne peuvent être copiées qu’<i>après</i> la <i>publication</i> des ressources. Voir <a href="/help/assets/publishing-dynamicmedia-assets.md">Publication de ressources</a>.</li> 
       <li>Dans le menu déroulant, appuyez sur <strong>Visionneuses</strong>.</li> 
       <li>Dans le rail de gauche, appuyez sur le nom du paramètre prédéfini de visionneuse de vidéos. Un aperçu de la vidéo s’ouvre dans une page distincte.</li> 
       <li>Dans le rail de gauche, dans la partie inférieure, appuyez sur <strong>Incorporer</strong>.</li> 
       <li>Dans la boîte de dialogue Code intégré, sélectionnez et copiez le code entier dans le Presse-papiers, puis collez-le dans un simple éditeur de texte.</li> 
       <li>Ajoutez le code intégré de la vidéo avec la syntaxe suivante pour l’associer à l’URL copiée dans votre fichier de chapitres :<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li> 
      </ol> </td> 
      </tr> 
     </tbody> 
    </table>

## À propos des miniatures de vidéo {#about-video-thumbnails}

Vous pouvez choisir l’une des dix images miniatures générées automatiquement par Dynamic Media pour l’ajouter à votre vidéo. Le lecteur vidéo affiche votre miniature sélectionnée lorsqu’une ressource vidéo est utilisée avec le composant Dynamic Media dans l’environnement de création de AEM Sites, AEM Mobile ou AEM Screens. La miniature sert d’image statique qui représente le mieux le contenu de l’ensemble de votre vidéo et encourage de plus les utilisateurs à appuyer sur le bouton Lecture .

Selon la durée totale de la vidéo, Dynamic Media capture dix images miniatures (par défaut) à 1 %, 11 %, 21 %, 31 %, 41 %, 51 %, 61 %, 71 %, 81 % et 91 % de la vidéo. Les dix miniatures restent, ce qui signifie que si vous décidez de sélectionner une miniature différente ultérieurement, vous n’avez pas besoin de générer de nouveau une série de miniatures. Vous prévisualisez les dix images miniatures, puis choisissez celle que vous souhaitez utiliser pour votre vidéo. Si vous souhaitez modifier cette option par défaut, vous pouvez utiliser CRXDE Lite pour configurer l’intervalle pour lequel les miniatures sont générées. Par exemple, si vous souhaitez uniquement générer une série de quatre miniatures également espacées dans votre vidéo, vous pouvez configurer l’intervalle à 24 %, 49 %, 74 % et 99 %.

Dans l’idéal, vous pouvez ajouter une miniature de vidéo à tout moment après avoir chargé votre vidéo, mais avant de la publier sur votre site web.

Si vous préférez, vous pouvez charger une miniature personnalisée pour représenter votre vidéo au lieu d’en utiliser une générée par Dynamic Media. Par exemple, vous pouvez créer une miniature personnalisée qui porte le titre de votre vidéo, une image d’ouverture attrayante, ou une image bien spécifique capturée dans votre vidéo. L’image de vidéo personnalisée que vous chargez doit avoir une résolution maximale de 1280 x 720 pixels (largeur minimale de 640 pixels) et ne pas dépasser 2 Mo.

>[!NOTE]
>
>Les miniatures vidéo personnalisées sont disponibles uniquement lorsque vous exécutez Dynamic Media en mode hybride.

### Ajout d’une miniature vidéo {#adding-a-video-thumbnail}

1. Accédez à une ressource vidéo chargée à laquelle vous souhaitez ajouter une miniature vidéo.
1. En mode de sélection des ressources, soit à partir de la fonction **[!UICONTROL Mode Liste]** ou le **[!UICONTROL Mode Carte]**, appuyez sur la ressource vidéo.
1. Dans la barre d’outils, appuyez sur l’icône **[!UICONTROL Afficher les propriétés]** (icône en forme de cercle avec un « i » à l’intérieur).
1. Sur la vidéo **[!UICONTROL Propriétés]** page, appuyez sur **[!UICONTROL Modifier la miniature]**.
1. Sur le **[!UICONTROL Modifier la miniature]** page, dans la barre d’outils, appuyez sur **[!UICONTROL Sélectionner une image]**.

   Dynamic Media génère une série de miniatures de votre vidéo, en fonction de l’intervalle par défaut ou personnalisé.

1. Prévisualisez les miniatures générées, puis sélectionnez celle que vous souhaitez ajouter à votre vidéo.
1. Appuyez sur **[!UICONTROL Enregistrer la modification]**.

   La miniature de la vidéo est mise à jour afin d’utiliser la miniature que vous avez sélectionnée. Si vous décidez par la suite de modifier la miniature, vous pouvez revenir sur la page **[!UICONTROL Modifier la miniature]** et en sélectionner une autre.

   Si vous avez configuré des intervalles par défaut, ou si vous avez chargé une nouvelle vidéo pour remplacer la vidéo existante, vous devrez générer de nouveau des miniatures via Dynamic Media.

   Voir [Configuration de l’intervalle par défaut auquel les miniatures de vidéo sont créées](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

#### Configuration de l’intervalle par défaut auquel les miniatures vidéo sont générées {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

Lorsque vous configurez et enregistrez le nouvel intervalle par défaut, votre modification s’applique automatiquement et uniquement aux vidéos que vous chargerez par la suite. Il n’applique pas automatiquement le nouveau paramètre par défaut aux vidéos que vous avez précédemment chargées. Pour les vidéos existantes, vous devez de nouveau générer les miniatures.

Voir [Ajout d’une miniature de vidéo](#adding-a-video-thumbnail).

Pour configurer l’intervalle par défaut auquel les miniatures vidéo sont créées,

1. Dans AEM, appuyez sur **[!UICONTROL Outils]** > **[!UICONTROL Général]** > **[!UICONTROL CRXDE Lite]**.

1. Dans la page du CRXDE Lite, dans le panneau du répertoire à gauche, accédez à `o etc/dam/imageserver/configuration/jcr:content/settings.`

   Si le panneau des répertoires n’est pas visible, vous devrez peut-être appuyer sur l’icône >> à gauche de l’onglet Accueil.

1. Dans le panneau inférieur droit, dans la variable **[!UICONTROL Propriétés]** onglet, double-appuyez `thumbnailtime`.
1. Dans la boîte de dialogue Modifier thumbnailtime, utilisez les champs de texte pour saisir des valeurs d’intervalle sous la forme de pourcentages.

   * Appuyez sur l’icône plus (+) pour ajouter un ou plusieurs champs de valeur d’intervalle. Vous devrez peut-être faire défiler la page jusqu’en bas de la boîte de dialogue pour voir l’icône.
   * Appuyez sur l’icône du signe moins (-) à droite du champ de valeur d’intervalle pour le supprimer de la liste.
   * Appuyez sur la flèche vers le haut ou vers le bas pour réorganiser les valeurs d’intervalle.

1. Appuyez sur **[!UICONTROL OK]** pour retourner à l’onglet Propriétés.****
1. Près du coin supérieur gauche de la page CRXDE Lite, appuyez sur **[!UICONTROL Enregistrer tout]**, puis appuyez sur icône Retour à l’accueil dans le coin supérieur gauche pour revenir à AEM.****

   Voir [Ajout d’une miniature de vidéo.](#adding-a-video-thumbnail)

### Ajout d’une miniature vidéo personnalisée {#adding-a-custom-video-thumbnail}

>[!NOTE]
>
>Cette fonction est disponible uniquement lorsque vous exécutez Dynamic Media en mode hybride.

1. Accédez à une ressource vidéo chargée à laquelle vous souhaitez ajouter une miniature vidéo.
1. En mode de sélection des ressources, soit à partir de la fonction **[!UICONTROL Mode Liste]** ou le **[!UICONTROL Mode Carte]**, appuyez sur la ressource vidéo.
1. Dans la barre d’outils, appuyez sur l’icône **[!UICONTROL Afficher les propriétés]** (icône en forme de cercle avec un « i » à l’intérieur).
1. Sur la vidéo **[!UICONTROL Propriétés]** page, appuyez sur **[!UICONTROL Modifier la miniature]**.
1. Sur le **[!UICONTROL Modifier la miniature]** page, dans la barre d’outils, appuyez sur **[!UICONTROL Charger une nouvelle miniature]**.
1. Naviguez jusqu’à une image de miniature que vous souhaitez utiliser, sélectionnez-la, puis appuyez sur **[!UICONTROL Ouvrir]** pour commencer à charger l’image sur AEM
1. Une fois l’image téléchargée, dans la variable **[!UICONTROL Modifier la miniature]** page, appuyez sur **[!UICONTROL Enregistrer les modifications]**.

   La miniature personnalisée est ajoutée à votre vidéo.
