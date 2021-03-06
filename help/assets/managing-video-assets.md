---
title: Gestion des ressources vidéo
description: Découvrez comment télécharger, prévisualiser, annoter et publier les ressources vidéo.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: Asset Management,Video
role: User
exl-id: eb652414-5b10-45af-a8b6-f1de649994c5
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 48%

---

# Gestion des ressources vidéo  {#managing-video-assets}

Découvrez comment gérer et modifier les ressources vidéo dans Adobe Experience Manager Assets. De plus, si vous possédez une licence d’utilisation Dynamic Media, reportez-vous à la [documentation vidéo sur Dynamic Media](video.md).

## Chargement et prévisualisation des ressources vidéo {#uploading-and-previewing-video-assets}

[!DNL Experience Manager] Les ressources génèrent des aperçus pour les ressources vidéo avec l’extension MP4. Si le format de la ressource n’est pas MP4, installez le pack FFmpeg pour générer un aperçu. FFmpeg crée des rendus vidéo de type OGG et MP4. Vous pouvez prévisualiser ces rendus dans la [!DNL Experience Manager] Interface utilisateur des ressources.

1. Dans le ou les sous-dossiers Ressources numériques, accédez à l’emplacement où vous souhaitez ajouter des ressources numériques.
1. Pour télécharger le contenu, cliquez ou appuyez sur **[!UICONTROL Créer]** dans la barre d’outils, puis sélectionnez **[!UICONTROL Fichiers]**. Vous pouvez également le faire glisser directement jusqu’à la zone des ressources. Pour plus d’informations sur l’opération de téléchargement, voir [Téléchargement des ressources](managing-assets-touch-ui.md#uploading-assets).
1. Pour prévisualiser une vidéo en mode Carte, appuyez sur le bouton **[!UICONTROL Lire]** du contenu vidéo.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   Vous pouvez suspendre ou lire une vidéo dans la variable **[!UICONTROL Carte]** affichage uniquement. Le bouton Lecture/Pause n’est pas disponible dans la **[!UICONTROL Liste]** vue.

1. Appuyez sur le bouton **[!UICONTROL Modifier]** sur la carte pour prévisualiser la vidéo dans la variable **[!UICONTROL Détails]** vue.

   La vidéo se joue dans le lecteur vidéo natif du navigateur. Vous pouvez lire, suspendre, afficher la vidéo en plein écran et en contrôler le volume.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## Configuration pour télécharger des ressources d’une taille supérieure à 2 Go {#configuration-to-upload-video-assets-that-are-larger-than-gb}

Par défaut, la variable [!DNL Experience Manager] Assets ne vous permet pas de charger des ressources de plus de 2 Go en raison d’une limite de taille de fichier. Néanmoins, vous pouvez contourner cette limite en accédant à CRXDE Lite et en créant un nœud dans le répertoire `/apps`. Le nœud doit comporter le même nom, la même structure de répertoire et des propriétés comparables.

En complément de [!DNL Experience Manager] La configuration des ressources, modifiez les configurations suivantes pour charger des ressources volumineuses :

* Augmentez le délai d’expiration du jeton. Voir [!UICONTROL Adobe du servlet CSRF Granite] dans la console web à l’adresse `https://[aem_server]:[port]/system/console/configMgr`. Pour plus d’informations, voir [Protection CSRF](/help/sites-developing/csrf-protection.md).
* Augmentez la configuration `receiveTimeout` du répartiteur. Pour plus d’informations, voir [Configuration du répartiteur Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>Le [!DNL Experience Manager] L’interface utilisateur classique ne présente pas de limite de taille de fichier de deux gigaoctets. Par ailleurs, le processus de bout en bout pour des vidéos volumineuses n’est pas entièrement pris en charge.

Pour configurer une limite de taille de fichier supérieure, procédez comme suit dans le répertoire `/apps`.

1. Dans AEM, appuyez sur **[!UICONTROL Outils > Général > CRXDE Lite]**.
1. Dans le **[!UICONTROL CRXDE Lite]** , dans la fenêtre de répertoire à gauche, accédez à `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Pour afficher la fenêtre du répertoire, appuyez sur `>>` icône .
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Noeud de recouvrement]**. Vous pouvez également sélectionner **[!UICONTROL Nœud de recouvrement]** dans le menu contextuel.
1. Dans la boîte de dialogue **[!UICONTROL Nœud de recouvrement]**, appuyez sur **[!UICONTROL OK]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. Actualisez le navigateur. Le nœud de recouvrement `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` est sélectionné.
1. Dans l’onglet **[!UICONTROL Propriétés]**, saisissez la valeur appropriée en octets pour définir la taille maximale souhaitée. Par exemple, saisissez `32212254720` pour augmenter la taille limite à 30 Go.

1. Dans la barre d’outils, appuyez sur **[!UICONTROL Enregistrer tout]**.
1. Dans AEM, appuyez sur **[!UICONTROL Outils > Opérations > Console web]**.
1. Sur le **[!UICONTROL Lots de la console web Adobe Experience Manager]** , sous **[!UICONTROL Nom]** de la colonne du tableau, recherchez et appuyez sur **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Dans le **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** , définissez les secondes pour les deux **[!UICONTROL Délai d’expiration par défaut]** et **[!UICONTROL Délai d’expiration maximal]** champs à `18000` (cinq heures).
1. Appuyez sur **[!UICONTROL Enregistrer]**.
1. Dans AEM, appuyez sur **[!UICONTROL Outils > Processus > Modèles]**.
1. Sur le **[!UICONTROL Modèles de processus]** page, sélectionnez **[!UICONTROL Vidéo de codage Dynamic Media]**, puis appuyez sur **[!UICONTROL Modifier]**.
1. Sur le **[!UICONTROL Workflow]** , appuyez deux fois sur la **[!UICONTROL Processus du service vidéo Dynamic Media]** composant.
1. Dans la boîte de dialogue **[!UICONTROL Propriétés des étapes]**, sous l’onglet **[!UICONTROL Commun]**, développez **[!UICONTROL Paramètres avancés]**.
1. Dans le champ **[!UICONTROL Délai dépassé]**, spécifiez une valeur de `18000`, puis appuyez sur **[!UICONTROL OK]** pour revenir à la page de workflow **[!UICONTROL Vidéo de codage de média dynamique]**.
1. Près de la partie supérieure de la page, sous **[!UICONTROL Vidéo de codage Dynamic Media]** titre de la page, appuyez sur **[!UICONTROL Enregistrer]**.

## Publication de ressources vidéo {#publishing-video-assets}

Une fois vos ressources vidéo publiées, vous pouvez les inclure dans une page web au moyen d’une URL ou d’une incorporation. Voir [Publication de ressources](publishing-dynamicmedia-assets.md).

## Annotation de ressources vidéo {#annotating-video-assets}

1. Dans la console Ressources, appuyez sur **[!UICONTROL Modifier]** sur la carte de la ressource pour afficher la page des détails de la ressource.
1. Appuyez sur le bouton **[!UICONTROL Aperçu]** pour lire la vidéo.
1. Pour annoter la vidéo, appuyez sur la **[!UICONTROL Annoter]** bouton . Une annotation est ajoutée à un moment spécifique de la vidéo.

   Lorsque vous annotez, vous pouvez dessiner sur le canevas et inclure un commentaire avec le dessin. Les commentaires sont automatiquement enregistrés dans les ressources AEM.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   Pour quitter l’assistant d’annotation, appuyez sur **[!UICONTROL Fermer]**.

1. Pour passer à un point spécifique de la vidéo, spécifiez la durée en secondes dans le champ de texte, puis cliquez sur **[!UICONTROL Saut]**. Par exemple, pour sauter les  premières secondes de la vidéo, saisissez `20`20 dans le champ texte.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. Cliquez sur une annotation pour l’afficher dans la chronologie. Appuyer **[!UICONTROL Supprimer]** pour supprimer l’annotation de la chronologie.

   ![chlimage_1-206](assets/chlimage_1-206.png)
