---
title: Rendus vidéo
seo-title: Rendus vidéo
description: Suivez cette page afin d’en savoir plus sur la génération des rendus Full HD pour votre projet Screens.
seo-description: Suivez cette page afin d’en savoir plus sur la génération des rendus Full HD pour votre projet Screens.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Rendus vidéo{#video-renditions}

Vous pouvez générer des rendus Full HD automatiques et manuels. La section suivante décrit le workflow à suivre pour ajouter des rendus à vos ressources.

## Génération automatique de rendus Full HD          {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Au cas où les rendus vidéo d’AEM Screens ne sont pas lus de façon optimale sur votre périphérique, contactez le fournisseur de votre matériel pour obtenir les caractéristiques de la vidéo. Cela vous aidera à obtenir de meilleures performances sur le périphérique et par conséquent à créer votre propre profil vidéo personnalisé où vous fournissez les paramètres appropriés pour que FFmpeg génère le rendu. Ultérieurement, suivez les étapes ci-dessous pour ajouter votre profil vidéo personnalisé à la liste des profils.
>
>En outre, voir [Dépannage des vidéos](/help/screens/troubleshoot-videos.md) pour déboguer et dépanner les problèmes de lecture de vidéos dans votre canal.

Suivez les étapes ci-dessous pour générer automatiquement des rendus Full HD :

1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis cliquez sur l’icône en forme de marteau et sélectionnez **Workflow**.

   Cliquez sur **Modèles** pour accéder à la gestion des modèles de workflow.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Sélectionnez le modèle **Ressources de mise à jour de gestion des actifs numériques**, puis cliquez sur Modifier dans la barre d’actions pour ouvrir la fenêtre **Ressources de mise à jour de gestion des actifs numériques**.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Double-cliquez sur l’étape **Transcodage FFmpeg**.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Sélectionnez l’onglet **Processus** pour modifier les arguments du processus. Saisissez les profils Full HD pour la liste dans **Arguments** comme suit : ***,profile:fullhd-bp,profile:fullhd-hp*** et cliquez sur **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Cliquez sur **Enregistrer **en haut à gauche de l’écran **Ressources de mise à jour de gestion des actifs numériques**.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Accédez à **Actifs** et téléchargez une nouvelle vidéo. Cliquez sur la vidéo, puis ouvrez le rail latéral Rendus où vous verrez les deux vidéos Full HD.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Ouvrez **Rendus** dans le rail latéral.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Vous verrez deux nouveaux rendus Full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Génération manuelle de rendus Full HD {#manually-generating-full-hd-renditions}

Suivez les étapes ci-dessous pour générer manuellement des rendus Full HD :

1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis cliquez sur l’icône en forme de marteau et sélectionnez **Workflow**.

   Cliquez sur **Modèles** pour accéder à la gestion des modèles de workflow.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Sélectionnez le modèle **Ressources de mise à jour de gestion des actifs numériques**, puis cliquez sur **Démarrer le processus** pour ouvrir la boîte de dialogue **Exécuter le processus**.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Sélectionnez la vidéo souhaitée dans la **charge utile** et cliquez sur **Exécuter**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Accédez à **Actifs**, recherchez votre ressource en descendant dans la hiérarchie, puis cliquez dessus.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Ouvrez le rail latéral **Rendus** ; vous remarquerez les nouveaux rendus Full HD. 

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

