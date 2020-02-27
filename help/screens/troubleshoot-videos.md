---
title: Configuration et dépannage de la lecture vidéo
seo-title: Résolution des incidents liés à des vidéos
description: null
seo-description: Pour savoir comment résoudre les problèmes liés aux vidéos, consultez cette page. Lorsque vous chargez une vidéo dans la Gestion des actifs numériques et que vous l’ajoutez à votre canal, il est possible que la vidéo ne soit pas lue dans le lecteur Screens. Cette section décrit comment déboguer et résoudre les problèmes liés à la lecture dans votre canal.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Configuration et dépannage de la lecture vidéo{#video-playback-configuration-and-troubleshooting}

Lorsque vous chargez une vidéo dans la Gestion des actifs numériques et que vous l’ajoutez à votre canal, il est possible que la vidéo ne soit pas lue dans le lecteur Screens.

Les sections qui suivent décrivent comment déboguer et résoudre les problèmes liés à la lecture de vidéos dans votre canal.

## Rendus de la gestion des actifs numériques    {#dam-renditions}

Une fois la vidéo chargée dans le canal, AEM doit commencer à créer des rendus. Les vidéos sont répertoriées sous la catégorie Ressources.

Pour visionner la vidéo, procédez comme suit :

1. Navigate to your video, for example [http://localhost:4502/assets.html/content/dam/we-retail/en/videos](http://localhost:4502/assets.html/content/dam/we-retail/en/videos).
1. Cliquez sur la vidéo, développez le menu supérieur gauche, puis cliquez sur **Rendus**.

Il doit y avoir différents rendus (MP4 ou M4V).

S’il n’existe aucun rendu, vérifiez que vous avez installé ffmpeg sur le système d’exploitation où AEM est exécuté.

>[!CAUTION]
>
>S’il n’existe aucun rendu, vérifiez que vous avez installé ffmpeg sur le système d’exploitation où AEM est exécuté.
>
>Cliquez [ici](https://evermeet.cx/ffmpeg/) pour installer ffmpeg.

## Ressources vidéo {#video-assets}

S’il n’y a pas d’attribut source sous la vidéo, il est possible que la vidéo n’ait pas été transcodée. Si la vidéo est transcodée correctement, elle s’affiche dans le tableau de bord, comme indiqué dans l’illustration ci-dessous.

Vérifiez que ffmpeg est installé dans les profils vidéo.

![chlimage_1-2](assets/chlimage_1-2.png)

### Vérification du profil vidéo {#checking-video-profile}

1. Navigate to the [Video Profile](http://localhost:4502/etc/dam/video.html) and click **Upload Test Video**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Téléchargez une vidéo de test et cliquez sur **Ok **pour commencer le transcodage.

   En cas d’échec du transcodage, développez la sortie ffmpeg pour comprendre les erreurs dans la sortie de la console de ffmpeg.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   En revanche, si la vidéo est transcodée correctement, il est possible de télécharger le fichier transcodé.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Avant de l’ajouter à un canal, veillez à laisser suffisamment de temps pour le transcodage de la vidéo (l’indicateur « Nouvelle » et non « Traitement en cours » doit s’afficher).

### Vérification du profil avec un composant vidéo     {#checking-profile-with-a-video-component}

Consultez la liste des profils dans la conception des pages si le composant vidéo n’est pas configuré correctement.

1. Accédez à votre canal et sélectionnez le mode **Conception**.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Sélectionnez la vidéo et ouvrez la boîte de dialogue **Modifier**. Ouvrez l’onglet **Profils**.

   Sélectionnez différents profils (au minimum, le profil « Qualité élevée H.264 » doit être répertorié).

   ![chlimage_1-7](assets/chlimage_1-7.png)

### Vérification de la vidéo dans le lecteur web {#checking-the-video-in-the-web-player}

Utilisez le [lecteur web](http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0) pour valider la lecture dans les navigateurs (Chrome et Safari). Chrome est utilisé sur les périphériques Android, tandis que Safari est le navigateur d’OS X et d’iOS.

Si la vidéo n’est pas lue sous Safari, elle ne fonctionnera pas dans les lecteurs OS X et iOS. Il s’agit probablement d’un problème d’encodage ; la vidéo doit être réencodée.

Pour utiliser un workflow de gestion des actifs numériques afin de créer des rendus Full HD, procédez comme suit :

1. Navigate to the [workflow model admin](http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models).
1. Sélectionnez le modèle **Screens – Mettre à jour la ressource**.
1. Cliquez sur **Démarrer le processus** dans la barre d’actions pour ouvrir la boîte de dialogue **Exécuter le processus**.

1. Sélectionnez la ressource vidéo dans **Charge utile**.
1. Cliquez sur **Exécuter**.

>[!NOTE]
>
>Patientez quelques instants avant de créer les rendus. Après quelques secondes ou minutes (selon la taille de la vidéo), rechargez le lecteur web sous Safari.

#### Dépannage de l’indicateur de stratégie de lecture automatique {#troubleshooting-autoplay-policy-flag}

Si le lecteur AEM Screens sélectionne la vidéo mais ne l’affiche pas, vous devez résoudre les problèmes liés à l’indicateur de stratégie de lecture automatique.

Pour résoudre le problème d’indicateur Stratégie de lecture automatique de Google, procédez comme suit :

1. Accédez à ***chrome://flags/#autoplay-policy***
1. Changez la **stratégie de lecture automatique** de **par défaut** à **aucun geste requis de la part de l’utilisateur**

1. Relancez votre navigateur web et mettez à jour le lecteur

>[!NOTE]
>
>To learn more about the best practices for good user experiences with the new autoplay policies in Chrome, please see documentation for [Autoplay Policy Changes.](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio)

### Synchronisation des vidéos sur plusieurs lecteurs {#syncing-video-across-multiple-players}

Pour lire des vidéos en mode synchrone sur plusieurs périphériques, utilisez la stratégie absolue pour la séquence dont fait partie la vidéo.

#### Conditions requises {#requirements}

* 2+ joueurs identiques
* Matériel similaire, dans l’idéal
* Topologie de réseau identique (les lecteurs sont connectés à un serveur NTP, qui synchronise leurs horloges système internes)

#### Configuration de la stratégie absolue {#setting-up-the-absolute-strategy}

La stratégie absolue :

* calcule une heure d’ancrage (minuit le jour courant) ;
* calcule la durée de la séquence (somme de la durée de tous ses éléments) ;
* calcule, à tout moment, l’élément qui doit être en cours de lecture et l’élément suivant à l’aide de la formule temps_restant_séquence = (heure_actuelle - heure_ancrage) % durée_séquence.

Pour configurer une stratégie absolue, procédez comme suit :

1. Accédez au créateur du canal et sélectionnez le composant Séquence, comme indiqué dans l’illustration ci-dessous.
1. Ouvrez la boîte de dialogue de configuration.
1. Modifiez la **Stratégie** et ajoutez « absolue ».

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>Le système d’exploitation des lecteurs doit posséder la même horloge.

**Alignement des horloges sur OS X** Pour aligner les horloges sur OSX, procédez comme suit :

1. Ouvrez les préférences **Date et heure** pour chaque lecteur OS X.
1. Cochez l’option ** Définir automatiquement la date et l’heure**.
1. Collez value 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com dans la liste déroulante ou exécutez simplement *sudo ntpdate -u -v 0.pool.ntp.org*.
1. Démarrez deux lecteurs ou plus.

Il peut s’écouler un certain temps avant que les lecteurs ne commencent une nouvelle séquence synchronisée.

