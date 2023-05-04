---
title: Diffusion d’images optimisées pour un site réactif
description: Utilisation de la fonction de code réactif dans Dynamic Media pour diffuser des images optimisées
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5edcc765-c374-4368-a0d9-e02a713a24f2
exl-id: 36bb526c-a6d9-4296-8318-97ac72d6b3ba
feature: Publishing
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 72%

---

# Diffusion d’images optimisées pour un site réactif {#delivering-optimized-images-for-a-responsive-site}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Utilisez la fonctionnalité de code réactif lorsque vous souhaitez partager le code de diffusion réactive avec votre développeur web. Utilisez la fonctionnalité de code réactif (**[!UICONTROL RESS]**) lorsque vous souhaitez partager le code de diffusion réactive avec votre développeur web.

Cette fonction a un sens si votre site web se trouve sur un composant WCM tiers. Cependant, si votre site web se trouve sur AEM, un serveur d’images hors site effectue le rendu de l’image et la fournit à la page web.

Consultez également la section [Incorporation de la visionneuse de vidéos dans une page web.](embed-code.md)

Voir aussi [Liaison d’URL à une application web.](linking-urls-to-yourwebapplication.md)

**Pour diffuser des images optimisées pour un site réactif, procédez comme suit** :

1. Accédez à l’image pour laquelle vous voulez fournir du code réactif et, dans le menu déroulant, appuyez sur **[!UICONTROL Rendus]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Sélectionnez un paramètre d’image prédéfini réactif. Les boutons **[!UICONTROL URL]** et **[!UICONTROL RESS]** apparaissent.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >La ressource sélectionnée *et* le paramètre d’image prédéfini ou le paramètre de visionneuse prédéfini sélectionné doivent être publiés pour que le bouton **[!UICONTROL URL]** ou **[!UICONTROL RESS]** soit disponible.
   >
   >Le mode hybride de Dynamic Media nécessite de publier des paramètres prédéfinis d’image ; le mode Scene7 de Dynamic Media publie automatiquement les paramètres prédéfinis d’image.

1. Appuyez sur **[!UICONTROL RESS]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. Dans la boîte de dialogue **[!UICONTROL Intégrer une image réactive]**, sélectionnez et copiez le texte du code réactif et collez-le dans votre site web pour accéder au fichier réactif.
1. Modifiez les points d’arrêt par défaut dans le code incorporé pour qu’ils correspondent à ceux du site web réactif directement dans le code. Testez en outre les différentes résolutions d’image diffusées à différents points d’arrêt d’une page.

## Utilisation du protocole HTTP/2 pour diffuser vos ressources Dynamic Media {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 est le nouveau protocole Web mis à jour qui améliore la communication entre les navigateurs et les serveurs. Il permet un transfert plus rapide des informations et réduit la puissance de traitement nécessaire. La diffusion des ressources Dynamic Media est prise en charge via HTTP/2, qui offre de meilleurs temps de réponse et de chargement.

Voir [Diffusion du contenu sur HTTP2](http2.md) pour tout savoir sur l’utilisation du protocole HTTP/2 avec votre compte Dynamic Media.
