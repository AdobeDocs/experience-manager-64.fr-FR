---
title: Publication de ressources Dynamic Media
seo-title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media.
seo-description: Découvrez comment publier des ressources Dynamic Media.
uuid: b1bee905-86cf-4284-8d4e-067e11557899
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 99d7025f-d022-4213-83c0-815a4712c573
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402

---


# Publication de ressources Dynamic Media {#publishing-dynamic-media-assets}

You publish your Dynamic Media assets by selecting the assets and tapping **[!UICONTROL Publish]**. Une fois vos fichiers de médias dynamiques publiés, vous pouvez les inclure dans une page Web par URL ou par incorporation.

Vous pouvez également publier instantanément des fichiers que vous téléchargez, sans intervention de l’utilisateur. See [Configuring Dynamic Media - Scene7 mode](config-dms7.md).

Dans le **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’un fichier pour indiquer qu’il est publié. En **[!UICONTROL mode Liste]**, une colonne **[!UICONTROL Publié]** indique les fichiers publiés ou non.

>[!NOTE]
>
>Si un fichier est déjà publié, vous utilisez AEM pour déplacer le fichier vers un autre dossier et le republier depuis son nouvel emplacement, l’emplacement du fichier publié d’origine est toujours disponible, ainsi que le fichier récemment republié. La ressource publiée d’origine est toutefois &quot;perdue&quot; pour AEM et ne peut pas être annulée. Par conséquent, il est recommandé d’annuler la publication des fichiers avant de les déplacer vers un autre dossier.

Si vous prévoyez de publier des fichiers vidéo immédiatement après leur codage, assurez-vous que le codage est terminé. Lorsque les vidéos sont toujours codées, le système vous informe qu’un processus de traitement vidéo est en cours. Une fois le codage vidéo effectué, vous devez pouvoir prévisualiser les rendus vidéo. A ce stade, vous pouvez publier les vidéos en toute sécurité sans générer d’erreurs de publication.

Reportez-vous également à la section [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Voir aussi [Incorporation de la visionneuse de vidéos dans une page web.](embed-code.md)

>[!NOTE]
>
>* Pour utiliser l’URL, les ressources doivent être publiées. Si les ressources ne sont pas publiées, la copie et le collage de l’URL ne fonctionnent pas dans un navigateur web.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.
>



Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources.](managing-assets-touch-ui.md)

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

See [HTTP/2 delivery of content frequently asked questions](/help/sites-administering/scene7-http2faq.md) to learn more.
