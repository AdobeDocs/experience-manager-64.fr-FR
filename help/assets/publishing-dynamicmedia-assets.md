---
title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media y compris la diffusion HTTP/2 de ces ressources.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: ebe30c07-1d76-4338-b301-49591f981688
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 78%

---

# Publication de ressources Dynamic Media {#publishing-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour publier vos ressources Dynamic Media, sélectionnez-les en appuyant sur l’icône **[!UICONTROL Publier]**. Une fois les ressources Dynamic Media publiées, vous pouvez les inclure dans une page web via une URL ou une incorporation.

Vous pouvez également publier immédiatement les ressources que vous téléchargez, sans intervention de l’utilisateur. Voir [Configuration de Dynamic Media - mode Scene7](config-dms7.md).

En **[!UICONTROL mode Carte]** une petite icône en forme de globe apparaît directement sous le nom d’une ressource pour indiquer que celle-ci est publiée. Dans la vue **[!UICONTROL Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

>[!NOTE]
>
>Si une ressource est déjà publiée et que vous utilisez AEM pour la déplacer vers un autre dossier et la republier à partir du nouvel emplacement, l’emplacement d’origine de la ressource publiée est toujours disponible, avec la ressource republiée. La ressource d’origine publiée est toutefois « perdue » pour AEM et elle ne peut pas être dépubliée. Il est par conséquent recommandé de dépublier les ressources avant de les déplacer vers un autre dossier.

Si vous envisagez de publier des ressources vidéo immédiatement après les avoir codées, vérifiez que le codage est entièrement terminé. Lorsque des vidéos sont en cours de codage, le système vous informe qu’un workflow de traitement vidéo est en cours. Lorsque le codage vidéo est terminé, vous êtes en mesure de prévisualiser les rendus vidéo. À ce stade, vous pouvez publier les vidéos sans rencontrer d’erreurs de publication.

Voir aussi [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Consultez également la section [Incorporation de la visionneuse de vidéos dans une page web.](embed-code.md)

>[!NOTE]
>
>* Pour utiliser l’URL, les ressources doivent être publiées. Si les ressources ne sont pas publiées, la copie et le collage de l’URL dans un navigateur web ne fonctionneront pas.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.
>


Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources.](managing-assets-touch-ui.md)

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code incorporé pour l’image ou la vidéo peut être intégré à toute application qui accepte une ressource hébergée. Cette ressource publiée est ensuite diffusée au moyen du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, reportez-vous aux [Questions fréquentes sur la diffusion de contenu HTTP/2](/help/sites-administering/scene7-http2faq.md).
