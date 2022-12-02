---
title: Vidéo
description: Découvrez la gestion centralisée des ressources vidéo dans laquelle vous pouvez charger des vidéos pour Experience Manager Assets pour le codage automatique dans Dynamic Media Classic. Vous pouvez également accéder aux vidéos Dynamic Media Classic directement à partir de Experience Manager Assets. L’intégration vidéo Dynamic Media Classic étend la portée de la vidéo optimisée à tous les écrans avec détection automatique de périphérique et de bande passante automatique.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
exl-id: 081e7db0-95cc-4260-8f08-318cd7d9d5b4
feature: Video
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1603'
ht-degree: 66%

---

# Vidéo {#video}

Les ressources permettent une gestion centralisée des ressources vidéo dans laquelle vous pouvez charger des vidéos directement dans Assets afin de les coder automatiquement dans Dynamic Media Classic. Vous pouvez également accéder aux vidéos Dynamic Media Classic directement à partir de Ressources pour la création de pages.

L’intégration vidéo de Dynamic Media Classic étend la portée de la vidéo optimisée à tous les écrans (détection automatique de l’appareil et de la bande passante).

Le composant **[!UICONTROL vidéo Scene7]** procède automatiquement à la détection de l’appareil et de la bande passante afin de lire la vidéo au format adéquat avec la qualité optimale sur des ordinateurs de bureau, des tablettes et des téléphones mobiles.

Vous pouvez inclure des visionneuses de vidéos adaptatives au lieu de ressources vidéo uniques. Une visionneuse de vidéos adaptative est un conteneur pour tous les rendus vidéo nécessaires pour lire la vidéo en toute transparence sur plusieurs écrans. Une visionneuse de vidéos adaptative regroupe les versions d’une même vidéo codées à des débits et des formats différents. Par exemple, 400 Kbit/s, 800 Kbit/s et 1 000 Kbit/s. Vous utilisez une visionneuse de vidéos adaptative, ainsi qu’un composant vidéo S7, pour la diffusion en continu de vidéo adaptative sur plusieurs types d’écran. Par exemple, les ordinateurs de bureau, iOS, Android, BlackBerry et les appareils mobiles Windows.

Pour plus d’informations, consultez la [documentation sur Dynamic Media Classic sur les visionneuses de vidéos adaptatives](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia).

## À propos de FFMPEG et Dynamic Media Classic {#about-ffmpeg-and-scene}

Le workflow de codage vidéo par défaut est basé sur l’utilisation d’une intégration basée sur FFMPEG aux profils vidéo. De ce fait, le processus d’assimilation de la gestion des actifs numériques prêt à l’emploi contient les deux étapes suivantes du processus basé sur FFMPEG :

* Miniatures FFMPEG
* Codage FFMPEG

Gardez à l’esprit que l’activation et la configuration de l’intégration ne suppriment ou ne désactivent pas automatiquement ces deux étapes du workflow prêt à l’emploi d’assimilation de la gestion des ressources numériques. Si vous utilisez déjà le codage vidéo FFMPEG dans  Experience Manager, il est probable que FFMPEG soit installé dans vos environnements de création. Dans ce cas, une nouvelle vidéo assimilée à l’aide de la gestion des ressources numériques est codée deux fois : une fois par le codeur FFMPEG et une fois par l’intégration de Dynamic Media Classic.

Si le codage vidéo basé sur FFMPEG est configuré dans AEM et FFMPEG, vous pouvez supprimer les deux workflows FFMPEG de vos workflows d’ingestion DAM.

## Formats pris en charge {#supported-formats}

Les formats suivants sont pris en charge pour le composant vidéo Scene7 :

* F4V H.264
* MP4 H.264

## Choix de l’emplacement du téléchargement de la vidéo {#deciding-where-to-upload-your-video}

Le choix de l’emplacement du téléchargement du contenu vidéo dépend des éléments suivants :

* Avez-vous besoin d’un worfklow pour le contenu vidéo ?
* Avez-vous besoin d’un contrôle des versions pour le contenu vidéo ?

Si la réponse est « oui » à l’une des questions ou aux deux, téléchargez la vidéo directement dans la gestion des actifs numériques d’Adobe. Si la réponse est « non » aux deux questions, chargez la vidéo directement dans Dynamic Media Classic. Le workflow de chaque scénario est décrit dans les sections suivantes.

### Si vous téléchargez la vidéo directement dans la gestion des actifs numériques d’Adobe {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Si vous avez besoin d’un workflow ou d’une création de versions pour les ressources, vous devez tout d’abord les télécharger dans la gestion des ressources numériques d’Adobe. Vous trouverez ci-dessous le workflow recommandé :

1. Chargez la ressource vidéo dans la gestion des ressources numériques d’Adobe et codez et publiez automatiquement dans Dynamic Media Classic.
1. Dans Experience Manager, accédez aux contenus vidéo dans la gestion de contenu web, dans l’onglet **[!UICONTROL Films]** de l’outil de recherche de contenu.
1. Créez avec le composant **[!UICONTROL vidéo Scene7]** ou **[!UICONTROL vidéo de base]**.

### Si vous téléchargez la vidéo dans Scene7 {#if-you-are-uploading-your-video-to-scene}

Si vous n’avez pas besoin d’un workflow ou d’une création de versions pour vos ressources, chargez-les vers Scene7. Vous trouverez ci-dessous le workflow recommandé :

1. Dans Dynamic Media Classic, [configurez un chargement FTP et un codage programmés dans Scene7 (système automatisé)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading).
1. Dans Experience Manager, accédez aux contenus vidéo dans la gestion de contenu web, dans l’onglet **[!UICONTROL Scene7]** de l’outil de recherche de contenu.
1. Créez avec le composant **[!UICONTROL vidéo Scene7]**.

## Configuration de l’intégration avec la vidéo Scene7 {#configuring-integration-with-scene-video}

Pour configurer les paramètres prédéfinis universaux :

1. Dans **[!UICONTROL Services Cloud]**, accédez à la configuration **[!UICONTROL Scene7]** et cliquez sur **[!UICONTROL Modifier]**.
1. Sélectionnez l’onglet **[!UICONTROL Vidéo]**.

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >L’onglet **[!UICONTROL Vidéo]** n’apparaît pas si la page ne comporte pas de configuration cloud.

1. Sélectionnez le profil de codage vidéo adaptative, un profil de codage vidéo unique prêt à l’emploi ou un profil de codage vidéo personnalisé.

   >[!NOTE]
   >
   >Pour plus d’informations sur la signification des paramètres prédéfinis de vidéo, consultez la [documentation de Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html?lang=fr#video-presets-for-encoding-video-files).
   >
   >Adobe recommande de sélectionner les deux visionneuses de vidéos adaptatives lors de la configuration des paramètres prédéfinis ou de sélectionner l’option **[!UICONTROL Codage vidéo adaptatif]**.

1. Les profils de codage sélectionnés sont automatiquement appliqués à toutes les vidéos téléchargées dans le dossier cible de la gestion des actifs numériques CQ que vous avez défini pour cette configuration de cloud Scene7. Vous pouvez définir plusieurs configurations de cloud Scene7 avec différents dossiers cibles afin d’appliquer différents profils de codage, selon vos besoins.

## Mise à jour de la visionneuse et des paramètres prédéfinis de codage {#updating-viewer-and-encoding-presets}

Si les paramètres prédéfinis ont été mis à jour dans Scene7, il est nécessaire de mettre à jour la visionneuse et les paramètres prédéfinis de codage pour la vidéo en Experience Manager. Dans ce cas, accédez à la configuration Scene7 dans la configuration cloud et cliquez sur **[!UICONTROL Mise à jour de la visionneuse et des paramètres prédéfinis de codage]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Chargement de la vidéo originale vers Scene7 à partir de la gestion des ressources numériques Adobe {#uploading-your-master-video}

1. Accédez au dossier cible de la gestion des ressources numériques CQ dans lequel vous avez défini la configuration de cloud avec les profils de codage Scene7.
1. Cliquez sur **[!UICONTROL Télécharger]** pour télécharger la vidéo maître. Le chargement et le codage vidéo sont terminés une fois le workflow Ressources de mise à jour de gestion des actifs numériques terminé et **[!UICONTROL Publication sur Scene7]** comporte une coche.

   >[!NOTE]
   >
   >La génération des miniatures vidéo prend du temps.

   Glissement de la vidéo principale de gestion des actifs numériques vers les composants vidéo *all* les rendus proxy codés Scene7 pour la diffusion.

## Comparaison du composant vidéo de base et du composant vidéo Scene7 {#foundation-video-component-versus-scene-video-component}

Lorsque vous utilisez Experience Manager, vous avez accès à la fois au composant vidéo disponible dans Sites et au composant vidéo Scene7. Ces composants ne sont pas interchangeables.

Le composant vidéo Scene7 ne fonctionne que pour les vidéos Scene7. Le composant de base fonctionne avec les vidéos stockées depuis Experience Manager (à l’aide de FFMPEG) et les vidéos Scene7.

Le tableau suivant explique les cas d’utilisation de chaque composant :

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>Par défaut, le composant vidéo S7 utilise le profil vidéo universel. Vous pouvez toutefois obtenir le lecteur vidéo basé sur HTML5 en Experience Manager. Copiez simplement le code incorporé du lecteur vidéo HTML5 prêt à l’emploi et collez-le dans votre page de Experience Manager.

## Composant vidéo Experience Manager {#aem-video-component}

Même si l’utilisation du composant vidéo Scene7 est recommandée pour l’affichage de vidéos Scene7, utilisez des vidéos Scene7 avec le composant vidéo Foundation, par souci d’exhaustivité.

### Comparaison des vidéos Experience Manager et des vidéos Scene7 {#aem-video-and-scene-video-comparison}

Le tableau suivant fournit une comparaison de niveau élevé des fonctions prises en charge par le composant vidéo de base d’Experience Manager et le composant vidéo Scene7 :

|  | Vidéo de base Experience Manager | Vidéo Scene7 |
|---|---|---|
| Approche | Approche HTML5 en premier lieu. Flash n’est utilisé que pour le secours non HTML5. | Flash sur la plupart des ordinateurs de bureau. HTML5 est utilisé pour les mobiles et les tablettes. |
| Diffusion | Progressive | Adaptative |
| Suivi | Oui | Oui |
| Evolutivité | Oui | Oui (avec [Documentation de l’API du SDK de la visionneuse HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) |
| Vidéo mobile | Oui | Oui |

### Configuration {#setting-up}

#### Création de profils vidéo {#creating-video-profiles}

Les différents codages vidéo sont créés selon les paramètres prédéfinis de codage Scene7 sélectionnés dans votre configuration cloud Scene7. Pour que le composant vidéo de base les utilise, un profil vidéo doit être créé pour chaque paramètre prédéfini de codage Scene7 sélectionné. Cela permet au composant vidéo de sélectionner les rendus de la gestion des ressources numériques en conséquence.

>[!NOTE]
>
>Les nouveaux profils vidéo et leurs modifications doivent être activés pour la publication.

1. Dans Experience Manager, appuyez sur **[!UICONTROL Outils] > [!UICONTROL Console de configuration]**.
1. Dans la **[!UICONTROL Console de configuration]** accéder à **[!UICONTROL Outils > Gestion des actifs numériques > Profils vidéo]** dans l’arborescence de navigation.
1. Création d’un profil vidéo Scene7. Dans le **[!UICONTROL Nouveau...]** liste déroulante, sélectionnez **[!UICONTROL Créer une page]** puis sélectionnez le modèle Profil vidéo Scene7 . Attribuez un nom à la nouvelle page de profil vidéo et cliquez sur **[!UICONTROL Créer]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Modifiez le nouveau profil vidéo. Sélectionnez tout d’abord la configuration de cloud. Puis, sélectionnez le même paramètre prédéfini de codage que celui sélectionné dans la configuration de cloud.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Propriété | Description |
   |---|---|
   | Configuration de cloud Scene7 | Configuration cloud à utiliser pour les paramètres prédéfinis de codage. |
   | Paramètre prédéfini de codage Scene7 | Paramètre prédéfini de codage à associer à ce profil vidéo. |
   | Type de vidéo HTML5 | Cette propriété vous permet de définir la valeur de la propriété du type de l’élément source vidéo HTML5. Ces informations ne sont pas fournies par les paramètres prédéfinis de codage S7 mais requises pour effectuer correctement le rendu des vidéos en utilisant l’élément vidéo HTML5. Une liste des formats courants est fournie mais ils peuvent être remplacés par d’autres formats. |

   Répétez cette étape pour tous les paramètres prédéfinis de codage sélectionnés dans la configuration cloud que vous voulez utiliser dans le composant vidéo.

#### Configuration de la conception {#configuring-design}

Le **[!UICONTROL Vidéo de base]** doit connaître les profils vidéo à utiliser pour créer la liste des sources vidéo. Vous devez ouvrir la boîte de dialogue de conception des composants vidéo et configurer la conception des composants pour l’utilisation des nouveaux profils vidéo.

>[!NOTE]
>
>Si vous utilisez le composant **[!UICONTROL vidéo de base]** sur une page mobile, vous devrez peut-être répéter ces étapes pour la conception de la page mobile.

>[!NOTE]
>
>Les modifications apportées à la conception nécessitent l’activation de celle-ci afin qu’elles puissent prendre effet lors de la publication.

1. Ouvrez la boîte de dialogue de conception des composants **[!UICONTROL vidéo de base]** et sélectionnez l’onglet **[!UICONTROL Profils]**. Supprimez ensuite les profils prêts à l’emploi et ajoutez les nouveaux profils vidéo S7. L’ordre de la liste des profils de la boîte de dialogue de conception définit également l’ordre des sources vidéo lors du rendu.
1. Pour les navigateurs ne prenant pas en charge le HTML5, le composant vidéo permet de configurer Flash comme solution de secours. Ouvrez la boîte de dialogue de conception des composants vidéo et sélectionnez l’onglet **[!UICONTROL Flash]**. Configurez les paramètres de Flash Player et affectez un profil de secours pour le Flash Player.

#### Liste de contrôle {#checklist}

1. Créez une configuration de cloud S7. Assurez-vous que les paramètres prédéfinis de codage vidéo sont définis et que l’importateur fonctionne.
1. Créer un profil vidéo S7 pour chaque paramètre prédéfini de codage vidéo sélectionné dans la configuration de cloud.
1. Les profils vidéo doivent être activés.
1. Configurez la conception du composant **[!UICONTROL vidéo de base]** sur votre page.
1. Activez la conception une fois que vous avez terminé les modifications sur cette dernière.
