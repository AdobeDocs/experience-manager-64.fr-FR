---
title: Rendus vidéo
description: Rendus vidéo
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 74%

---

# Rendus vidéo {#video-renditions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Adobe Experience Manager Assets génère des rendus vidéo pour les ressources vidéo de différents formats, dont OGG, FLV, etc.

AEM Assets prend en charge les rendus statiques et dynamiques (rendus codés en MD) pour les ressources multimédias.

Les rendus statiques sont générés en mode natif à l’aide de FFMPEG (installé et disponible sur le chemin système) et stockés dans le référentiel de contenu.

Les rendus avec codage DM sont stockés dans le serveur proxy et diffusés au moment de l’exécution.

Les ressources AEM fournissent une prise en charge de lecture pour ces rendus du côté client.

Pour afficher les rendus d’une ressource vidéo spécifique, ouvrez sa page de ressource, puis appuyez sur l’icône de navigation globale. Choisissez ensuite **[!UICONTROL Rendus]** dans la liste.

![chlimage_1-478](assets/chlimage_1-478.png)

La liste des rendus vidéo s’affiche dans le panneau **[!UICONTROL Rendus.]**

![chlimage_1-479](assets/chlimage_1-479.png)

Pour configurer le serveur proxy des rendus codés DM, [configurez les services cloud Dynamic Media.](config-dynamic.md)

Pour générer des rendus vidéo avec les paramètres souhaités, procédez comme suit : [créer un profil vidéo correspondant ;](video-profiles.md).

Une fois que vous avez configuré le serveur proxy et créé les profils vidéo, vous pouvez inclure ce paramètre vidéo prédéfini dans un profil de traitement et appliquer le profil de traitement à un dossier.

>[!NOTE]
>
>La lecture audio ne fonctionne pas pour les fichiers OGG et WAV sur Internet Explorer 11. Une erreur « Source non valide » apparaît sur la page des détails des ressources présentant l’extension OGG ou WAV.
>
>Sous MS Edge et iPad, les fichiers OGG ne s’exécutent pas et génèrent une erreur de format non pris en charge.
