---
title: Fichier mpeg pour les communautés
seo-title: Fichier mpeg pour les communautés
description: Comment installer et configurer FFmpeg pour les communautés
seo-description: Comment installer et configurer FFmpeg pour les communautés
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
translation-type: tm+mt
source-git-commit: 1bbd917ef20c4a618e93af66ffe8a6cfc8448e78
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---


# Fichier mpeg pour les communautés {#ffmpeg-for-communities}

## Présentation {#overview}

FFmpeg est une solution de conversion et de diffusion audio et vidéo en flux continu et, lorsqu’elle est installée, elle est utilisée pour le transcodage correct des ressources [](../../help/sites-authoring/default-components-foundation.md#video) vidéo ainsi que pour la fonction d’activation des communautés AEM.

Le mpeg est utilisé dans l’environnement d’auteur pour obtenir des métadonnées pour les ressources d’activation téléchargées et pour générer une miniature à afficher lors de la mise en vente de la ressource d’activation.

## Installation de FFmpeg {#installing-ffmpeg}

FFmpeg doit être installé sur le ou les serveurs hébergeant les instances d&#39; *auteur* AEM.

1. Go to [https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. Téléchargez la dernière version de FFmpeg pour votre environnement spécifique (Macintosh, Windows ou Linux)

   * il est important de maintenir FFmpeg à jour en raison de vulnérabilités de sécurité dans les anciennes versions

1. Installez FFmpeg en suivant les instructions du système d&#39;exploitation.

1. Assurez-vous que l&#39;exécutable FFmpeg est défini dans le chemin d&#39;accès du système.

   Vous devriez pouvoir exécuter FFmpeg à partir de n&#39;importe quel répertoire de votre système.

   * par exemple, `ffmpeg -version`

## Configurer le service de transcodage Fmpeg {#configure-ffmpeg-transcoding-service}

Par défaut, lorsque FFmpeg est installé, plusieurs rendus sont configurés (transcodages) conformément à la définition du processus de mise à jour des actifs de gestion des actifs (DAM Update Asset).

Comme les transcodages nécessitent beaucoup de processeur, il est recommandé de modifier la liste des rendus de cible. Dans la plupart des cas, le transcodage n’est pas nécessaire.

Pour modifier le processus de mise à jour des actifs DAM et, dans cet exemple, désactiver le transcodage :

* Connectez-vous à l’instance d’auteur avec des privilèges d’administration.
* A partir de la navigation globale : **[!UICONTROL Outils > Processus > Modèles]**
* Locate **[!UICONTROL DAM Update Asset]**
* Doublon-clic pour ouvrir le processus de modification dans l’interface utilisateur classique

   Emplacement résultant : [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Doublon-clic sur l’étape de transcodage **** FFmpeg pour accéder à la boîte de dialogue Propriétés de l’étape
* Under the **[!UICONTROL Process]** tab:

   * **[!UICONTROL Arugments]**: Effacer toutes les entrées pour désactiver le transcodage Valeurs par défaut : `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* Select **[!UICONTROL OK]** to close the `Step Properties` dialog

* Select **[!UICONTROL Save]** to save the `DAM Update Asset` workflow

   (coin supérieur gauche)

