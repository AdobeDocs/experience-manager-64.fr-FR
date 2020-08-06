---
title: 'Publication de ressources Dynamic Media '
seo-title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media.
seo-description: Découvrez comment publier des ressources Dynamic Media.
uuid: b1bee905-86cf-4284-8d4e-067e11557899
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 99d7025f-d022-4213-83c0-815a4712c573
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 98%

---


# Publication de ressources Dynamic Media  {#publishing-dynamic-media-assets}

Pour publier vos ressources Dynamic Media, sélectionnez-les en appuyant sur l’icône **[!UICONTROL Publier]**. Une fois les ressources Dynamic Media publiées, vous pouvez les inclure dans une page web via une URL ou une incorporation.

Vous pouvez également publier immédiatement les ressources que vous téléchargez, sans intervention de l’utilisateur. See [Configuring Dynamic Media - Scene7 mode](config-dms7.md).

En **[!UICONTROL mode Carte]** une petite icône en forme de globe apparaît directement sous le nom d’une ressource pour indiquer que celle-ci est publiée. En mode **[!UICONTROL Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

>[!NOTE]
>
>Si une ressource est déjà publiée et que vous utilisez AEM pour la déplacer vers un autre dossier et la republier à partir du nouvel emplacement, l’emplacement d’origine de la ressource publiée est toujours disponible, avec la ressource republiée. La ressource d’origine publiée est toutefois « perdue » pour AEM et sa publication ne peut pas être annulée. Il est par conséquent recommandé d’annuler la publication des ressources avant de les déplacer vers un autre dossier.

Si vous envisagez de publier des ressources vidéo immédiatement après les avoir codées, vérifiez que le codage est entièrement terminé. Lorsque des vidéos sont en cours de codage, le système vous informe qu’un workflow de traitement vidéo est en cours. Lorsque le codage vidéo est terminé, vous êtes en mesure de prévisualiser les rendus vidéo. À ce stade, vous pouvez publier les vidéos sans rencontrer d’erreurs de publication.

Voir aussi [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Voir aussi [Incorporation de la visionneuse de vidéos dans une page web.](embed-code.md)

>[!NOTE]
>
>* Pour utiliser l’URL, les ressources doivent être publiées. Si les ressources ne sont pas publiées, la copie et le collage de l’URL ne fonctionnent pas dans un navigateur web.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.

>



Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources.](managing-assets-touch-ui.md)

## Diffusion de ressources Dynamic Media via HTTP/2  {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, reportez-vous aux [Questions fréquentes sur la diffusion de contenu HTTP/2](/help/sites-administering/scene7-http2faq.md).
