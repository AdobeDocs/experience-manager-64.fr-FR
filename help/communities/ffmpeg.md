---
title: FFmpeg pour les communautés
seo-title: FFmpeg for Communities
description: Installation et configuration de FFmpeg pour Communities
seo-description: How to install and configure FFmpeg for Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Admin
exl-id: 9ed54ee3-3509-4a43-a710-90f4543ccaf3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# FFmpeg pour les communautés {#ffmpeg-for-communities}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

FFmpeg est une solution pour la conversion et la diffusion en continu d’audio et de vidéo. Lorsqu’elle est installée, elle est utilisée pour le transcodage correct de [ressources vidéo](../../help/sites-authoring/default-components-foundation.md#video) ainsi que pour la fonction d’activation d’AEM Communities.

FFmpeg est utilisé dans l’environnement de création pour obtenir des métadonnées pour les ressources d’activation chargées, ainsi que pour générer une miniature à afficher lors de la mise en liste de la ressource d’activation.

## Installation de FFmpeg {#installing-ffmpeg}

FFmpeg doit être installé sur le ou les serveurs hébergeant l’AEM *author* instances.

1. Accédez à [https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. Téléchargez la dernière version de FFmpeg pour votre environnement spécifique (Macintosh, Windows ou Linux).

   * il est important de maintenir FFmpeg à jour en raison de vulnérabilités de sécurité dans les anciennes versions

1. Installez FFmpeg en suivant les instructions pour le système d’exploitation.

1. Assurez-vous que le fichier exécutable FFmpeg est défini dans le chemin d’accès de votre système.

   Vous devriez être en mesure d’exécuter FFmpeg à partir de n’importe quel répertoire de votre système.

   * par exemple, `ffmpeg -version`

## Configuration du service de transcodage FFmpeg {#configure-ffmpeg-transcoding-service}

Par défaut, lorsque FFmpeg est installé, plusieurs rendus sont configurés (transcodages) conformément à la définition du workflow Ressources de mise à jour de gestion des actifs numériques .

Comme les transcodages consomment beaucoup d’unité centrale, il est recommandé de modifier la liste des rendus cibles. Dans la plupart des cas, le transcodage n’est pas nécessaire.

Pour modifier le workflow Ressources de mise à jour de gestion des actifs numériques, et dans cet exemple, pour désactiver le transcodage :

* Connexion à l’instance d’auteur avec des privilèges d’administrateur
* À partir de la navigation globale : **[!UICONTROL Outils > Processus > Modèles]**
* Localiser **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**
* Double-cliquez pour ouvrir le workflow à modifier dans l’interface utilisateur classique.

   Emplacement obtenu : [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Double-cliquez sur le **[!UICONTROL Transcodage FFmpeg]** pour accéder à la boîte de dialogue Propriétés des étapes
* Sous , **[!UICONTROL Processus]** tab :

   * **[!UICONTROL Arugments]**: Effacer toutes les entrées pour désactiver le transcodage Valeurs par défaut : `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* Sélectionner **[!UICONTROL OK]** pour fermer la `Step Properties` dialog

* Sélectionner **[!UICONTROL Enregistrer]** pour enregistrer le `DAM Update Asset` workflow

   (coin supérieur gauche)
