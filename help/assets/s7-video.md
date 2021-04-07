---
title: Vidéo
description: Découvrez la gestion centralisée des ressources vidéo dans laquelle vous pouvez télécharger des vidéos pour les ressources du Experience Manager en vue d’un codage automatique vers Dynamic Media Classic. Vous pouvez également accéder aux vidéos Dynamic Media Classic directement à partir des ressources du Experience Manager. L’intégration vidéo Dynamic Media Classic étend la portée de la vidéo optimisée à tous les écrans grâce à la détection automatique de la bande passante et du périphérique.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
exl-id: 081e7db0-95cc-4260-8f08-318cd7d9d5b4
feature: Vidéo
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 32%

---

# Vidéo {#video}

Les ressources permettent une gestion centralisée des ressources vidéo dans laquelle vous pouvez télécharger directement des vidéos vers les ressources en vue d’un codage automatique vers Dynamic Media Classic. Vous pouvez également accéder aux vidéos Dynamic Media Classic directement à partir des ressources pour la création de pages.

L’intégration vidéo Dynamic Media Classic étend la portée de la vidéo optimisée à tous les écrans (détection de périphériques et de bande passante automatique).

Le composant **[!UICONTROL Scene7 Video]** détecte automatiquement les périphériques et la bande passante afin de lire la vidéo au bon format et de bonne qualité sur les ordinateurs de bureau, tablettes et appareils mobiles.

Vous pouvez inclure des visionneuses de vidéos adaptatives plutôt que des fichiers vidéo uniques. Une visionneuse de vidéos adaptative est un conteneur pour tous les rendus vidéo nécessaires pour lire la vidéo de manière transparente sur plusieurs écrans. Une visionneuse de vidéos adaptative regroupe les versions d’une même vidéo codées dans des débits et des formats différents. Par exemple, 400 kbit/s, 800 kbit/s et 1 000 kbit/s. Vous utilisez une visionneuse de vidéos adaptative et un composant vidéo S7 pour la diffusion de vidéo adaptative en flux continu sur plusieurs types d’écran. Par exemple, les périphériques mobiles de bureau, iOS, Android, BlackBerry et Windows.

Voir [documentation de Dynamic Media Classic sur les visionneuses de vidéos adaptatives pour plus d’informations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia).

## A propos de FFMPEG et de Dynamic Media Classic {#about-ffmpeg-and-scene}

Le processus de codage vidéo par défaut est basé sur l’utilisation d’une intégration basée sur FFMPEG aux profils vidéo. De ce fait, le processus d’assimilation de la gestion des actifs numériques prêt à l’emploi contient les deux étapes suivantes du processus basé sur FFMPEG :

* Miniatures FFMPEG
* Codage FFMPEG

L’activation et la configuration de l’intégration Dynamic Media Classic ne suppriment pas ou ne désactivent pas automatiquement ces deux étapes de flux de travaux du processus d’assimilation de DAM prêt à l’emploi. Si vous utilisez déjà le codage vidéo FFMPEG en Experience Manager, il est probable que FFMPEG soit installé sur vos environnements de création. Dans ce cas, une nouvelle vidéo ingérée à l’aide de DAM serait codée deux fois : une fois à partir de l’encodeur FFMPEG et une fois à partir de l’intégration Dynamic Media Classic.

Si le codage vidéo basé sur FFMPEG est configuré dans AEM et FFMPEG installé, vous pouvez supprimer les deux workflows FFMPEG de vos workflows d’assimilation DAM.

## Formats pris en charge {#supported-formats}

Les formats suivants sont pris en charge pour le composant vidéo Scene7 :

* F4V H.264
* MP4 H.264

## Choix de l’emplacement du téléchargement de la vidéo {#deciding-where-to-upload-your-video}

Le choix de l’emplacement du téléchargement du contenu vidéo dépend des éléments suivants :

* Avez-vous besoin d’un worfklow pour le contenu vidéo ?
* Avez-vous besoin d’un contrôle des versions pour le contenu vidéo ?

Si la réponse est « oui » à l’une des questions ou aux deux, téléchargez la vidéo directement dans la gestion des actifs numériques d’Adobe. Si la réponse est &quot;non&quot; aux deux questions, téléchargez votre vidéo directement sur Dynamic Media Classic. Le processus de chaque scénario est décrit dans les sections suivantes.

### Si vous téléchargez la vidéo directement dans la gestion des actifs numériques d’Adobe {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Si vous avez besoin d’un processus ou d’un contrôle de version pour vos ressources, téléchargez d’abord vers la gestion des actifs numériques d’Adobe. Vous trouverez ci-dessous le worfklow recommandé :

1. Téléchargez la ressource vidéo dans la gestion des actifs numériques d’Adobe et codez et publiez automatiquement la ressource vidéo dans Dynamic Media Classic.
1. En Experience Manager, accédez aux ressources vidéo dans WCM dans l’onglet **[!UICONTROL Films]** de l’outil de recherche de contenu.
1. Auteur avec le composant **[!UICONTROL Scene7 Video]** ou **[!UICONTROL Foundation Video]**.

### Si vous téléchargez la vidéo dans Scene7 {#if-you-are-uploading-your-video-to-scene}

Si vous n’avez pas besoin d’un processus ou d’un contrôle de version pour vos ressources, téléchargez-les vers Scene7. Vous trouverez ci-dessous le worfklow recommandé :

1. Dans Dynamic Media Classic, [configurez un transfert et un codage FTP planifiés vers Scene7 (système automatisé)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading).
1. En Experience Manager, accédez aux ressources vidéo dans WCM dans l’onglet **[!UICONTROL Scene7]** de l’outil de recherche de contenu.
1. Auteur avec le composant **[!UICONTROL Scene7 Video]**.

## Configuration de l’intégration avec la vidéo Scene7 {#configuring-integration-with-scene-video}

Pour configurer les paramètres prédéfinis universaux :

1. Dans **[!UICONTROL Services Cloud]**, accédez à la configuration **[!UICONTROL Scene7]** et cliquez sur **[!UICONTROL Modifier]**.
1. Sélectionnez l’onglet **[!UICONTROL Vidéo]**.

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >L’onglet **[!UICONTROL Vidéo]** n’apparaît pas si la page ne comporte pas de configuration de cloud.

1. Sélectionnez le profil de codage vidéo adaptative, un profil de codage vidéo unique prêt à l’emploi ou un profil de codage vidéo personnalisé.

   >[!NOTE]
   >
   >Pour plus d’informations sur la signification des paramètres vidéo prédéfinis, voir la [documentation Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe recommande de sélectionner les deux ensembles de vidéos adaptables lors de la configuration des paramètres prédéfinis ou de sélectionner l’option **[!UICONTROL Codage vidéo adaptative]**.

1. Les profils de codage sélectionnés sont automatiquement appliqués à toutes les vidéos téléchargées dans le dossier cible de la gestion des actifs numériques CQ que vous avez défini pour cette configuration de cloud Scene7. Vous pouvez définir plusieurs configurations de cloud Scene7 avec différents dossiers cibles afin d’appliquer différents profils de codage, selon vos besoins.

## Mise à jour de la visionneuse et des paramètres prédéfinis de codage  {#updating-viewer-and-encoding-presets}

Si les paramètres prédéfinis ont été mis à jour dans Scene7, il est nécessaire de mettre à jour la visionneuse et les paramètres de codage prédéfinis pour la vidéo en Experience Manager. Dans ce cas, accédez à la configuration Scene7 dans la configuration cloud et cliquez sur **[!UICONTROL Mettre à jour la visionneuse et les paramètres prédéfinis de codage]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Téléchargement de la vidéo originale vers Scene7 à partir de la gestion des actifs numériques d’Adobe {#uploading-your-master-video}

1. Accédez au dossier cible de la gestion des actifs numériques CQ dans lequel vous avez défini la configuration de cloud avec les profils de codage Scene7.
1. Cliquez sur **[!UICONTROL Télécharger]** pour télécharger la vidéo maître. Le téléchargement et le codage des vidéos sont terminés une fois le flux de travaux de mise à jour des actifs de gestion des actifs numériques terminé et **[!UICONTROL Publier sur Scene7]** comporte une coche.

   >[!NOTE]
   >
   >La génération des miniatures vidéo prend du temps.

   Faire glisser la vidéo originale DAM sur le composant vidéo accède à *tous* les rendus proxy codés Scene7 pour la diffusion.

## Comparaison du composant vidéo de base et du composant vidéo Scene7 {#foundation-video-component-versus-scene-video-component}

Lorsque vous utilisez le Experience Manager, vous avez accès au composant vidéo disponible dans Sites et au composant vidéo Scene7. Ces composants ne sont pas interchangeables.

Le composant vidéo Scene7 ne fonctionne que pour les vidéos Scene7. Le composant foundation fonctionne avec les vidéos stockées à partir du Experience Manager (à l’aide de ffmpeg) et des vidéos Scene7.

La matrice suivante explique quand utiliser le composant :

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>Le composant vidéo S7 prêt à l’emploi utilise le profil vidéo universel. Vous pouvez toutefois obtenir le lecteur vidéo HTML5 en Experience Manager. Copiez simplement le code incorporé du lecteur vidéo HTML5 prêt à l’emploi et placez-le dans votre page de Experience Manager.

## Composant vidéo Experience Manager {#aem-video-component}

Même si l’utilisation du composant vidéo Scene7 est recommandée pour visionner des vidéos Scene7, utilisez Scene7 vidéos avec le composant vidéo Foundation, pour des raisons d’exhaustivité.

### Comparaison des vidéos Experience Manager et des vidéos Scene7 {#aem-video-and-scene-video-comparison}

Le tableau suivant présente une comparaison de haut niveau des fonctionnalités prises en charge entre le composant vidéo Experience Manager Foundation et le composant vidéo Scene7 :

|  | Vidéo Experience Manager Foundation | Vidéo Scene7 |
|---|---|---|
| Approche | Approche HTML5 en premier lieu. Flash n’est utilisé que pour le secours non HTML5. | Flash sur la plupart des ordinateurs de bureau. HTML5 est utilisé pour les mobiles et les tablettes. |
| Diffusion | Progressive | Adaptative |
| Suivi | Oui | Oui |
| Evolutivité | Oui | Oui (avec [Documentation de l’API du kit de développement de visionneuse HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) |
| Vidéo mobile | Oui | Oui |

### Configuration  {#setting-up}

#### Création de profils vidéo {#creating-video-profiles}

Les divers codages vidéo sont créés selon les paramètres prédéfinis de codage Scene7 sélectionnés dans votre configuration de cloud Scene7. Pour que le composant vidéo Foundation puisse les utiliser, un profil vidéo doit être créé pour chaque paramètre prédéfini de codage Scene7 sélectionné. Cette méthode permet au composant vidéo de sélectionner les rendus DAM en conséquence.

>[!NOTE]
>
>Les nouveaux profils vidéo et leurs modifications doivent être activés pour la publication.

1. Dans le Experience Manager, appuyez sur **[!UICONTROL Outils] > [!UICONTROL Console de configuration]**.
1. Dans **[!UICONTROL Configuration Console]**, accédez à **[!UICONTROL Outils > DAM > Profils vidéo]** dans l&#39;arborescence de navigation.
1. Création d’un Profil vidéo Scene7. Dans le **[!UICONTROL Nouveau...]** liste déroulante, sélectionnez **[!UICONTROL Créer une page]**, puis sélectionnez le modèle de Profil vidéo Scene7. Attribuez un nom à la nouvelle page de profil vidéo et cliquez sur **[!UICONTROL Créer]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Modifiez le nouveau profil vidéo. Sélectionnez tout d’abord la configuration de cloud. Puis, sélectionnez le même paramètre prédéfini de codage que celui sélectionné dans la configuration de cloud.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Propriété | Description |
   |---|---|
   | Configuration de cloud Scene7 | Configuration de cloud à utiliser pour les paramètres prédéfinis de codage. |
   | Paramètre prédéfini de codage Scene7 | Paramètre prédéfini de codage à associer à ce profil vidéo. |
   | Type de vidéo HTML5 | Cette propriété vous permet de définir la valeur de la propriété type de l’élément source vidéo HTML5. Ces informations ne sont pas fournies par les paramètres prédéfinis de codage S7 mais requises pour effectuer correctement le rendu des vidéos en utilisant l’élément vidéo HTML5. Une liste des formats courants est fournie mais ils peuvent être remplacés par d’autres formats. |

   Répétez cette étape pour tous les paramètres prédéfinis de codage sélectionnés dans la configuration de cloud que vous voulez utiliser dans le composant vidéo.

#### Configuration de la conception {#configuring-design}

Le composant **[!UICONTROL Foundation Video]** doit connaître les profils vidéo à utiliser pour créer la liste des sources vidéo. Ouvrez la boîte de dialogue de conception des composants vidéo et configurez la conception des composants pour l’utilisation des nouveaux profils vidéo.

>[!NOTE]
>
>Si vous utilisez le composant **[!UICONTROL Vidéo de base]** sur une page mobile, répétez ces étapes lors de la conception de la page mobile.

>[!NOTE]
>
>Les modifications apportées à la conception nécessitent l’activation de la conception afin qu’elle puisse prendre effet lors de la publication.

1. Ouvrez la boîte de dialogue de conception du composant **[!UICONTROL Foundation Video]** et passez à l’onglet **[!UICONTROL Profils]**. Supprimez ensuite les profils prêts à l’emploi et ajoutez les nouveaux profils vidéo S7. L’ordre de la liste de profil dans la boîte de dialogue de conception définit l’ordre de l’élément sources vidéo lors du rendu.
1. Pour les navigateurs qui ne prennent pas en charge HTML5, le composant vidéo vous permet de configurer un Flash de secours. Ouvrez la boîte de dialogue de conception des composants vidéo et passez à l’onglet **[!UICONTROL Flash]**. Configurez les paramètres du Flash Player et attribuez un profil de secours au Flash Player.

#### Liste de contrôle {#checklist}

1. Créez une configuration de cloud S7. Assurez-vous que les paramètres prédéfinis de codage vidéo sont définis et que l’importateur est en cours d’exécution.
1. Créer un profil vidéo S7 pour chaque paramètre prédéfini de codage vidéo sélectionné dans la configuration de cloud.
1. Les profils vidéo doivent être activés.
1. Configurez la conception du composant **[!UICONTROL Foundation Video]** sur votre page.
1. Activer la conception une fois que vous avez terminé les modifications de cette dernière.
