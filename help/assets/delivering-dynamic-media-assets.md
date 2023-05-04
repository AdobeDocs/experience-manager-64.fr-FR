---
title: Diffusion de ressources Dynamic Media
seo-title: Delivering Dynamic Media Assets
description: Découvrez comment diffuser des ressources Dynamic Media
seo-description: Learn how to deliver dynamic media assets
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 61%

---

# Diffusion de ressources Dynamic Media {#delivering-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La manière dont vous pouvez diffuser vos ressources Dynamic Media (vidéo et images) dépend de la mise en oeuvre de votre site web.

Avec Dynamic Media, vous disposez de plusieurs options :

* Si votre site web est hébergé sur AEM, vous souhaiterez ajouter les ressources Dynamic Media directement à votre page.
* Si votre site web n’est pas hébergé par AEM, les possibilités suivantes s’offrent à vous :

   * Incorporation de votre vidéo ou image sur votre site web.
   * Liez des URL à votre application web. Utilisez la liaison lorsque vous souhaitez présenter un lecteur vidéo dans une fenêtre contextuelle ou modale.
   * Si votre site est réactif, vous pouvez [diffuser des images optimisées.](responsive-site.md)

>[!NOTE]
>
>L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis et utilise des informations à la dernière milliseconde de la diffusion pour réduire davantage encore la taille du fichier d’image en fonction de la vitesse de connexion du réseau et du navigateur. Voir [Imagerie numérique](imaging-faq.md) pour plus d’informations.

Pour plus d’informations, reportez-vous aux rubriques suivantes :

* [Ajout de ressources Dynamic Media aux pages web](adding-dynamic-media-assets-to-pages.md)
* [Incorporation de la visionneuse de vidéos ou d’images dans une page web](embed-code.md)
* [Activation de la protection de lien dynamique dans Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-64/assets/dynamic/hotlink-protection.html?lang=fr#dynamic)
* Intégration du filigrane numérique non visible (Digimarc) à Dynamic Media (bientôt disponible)
* [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md)
* [Diffusion d’images optimisées pour un site réactif](responsive-site.md)
* [Diffusion de contenu HTTP2](http2.md)
* [Annulation de la validité du contenu mis en cache dans le réseau de diffusion de contenu (CDN)  ](invalidate-cdn-cached-content.md)
* [Utilisation de jeux de règles de transformation d’URL](using-rulesets-to-transform-urls.md)

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code incorporé pour l’image ou la vidéo peut être intégré à toute application qui accepte une ressource hébergée. Cette ressource publiée est ensuite diffusée au moyen du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Voir [Questions fréquentes sur la diffusion de contenu HTTP/2](/help/sites-administering/scene7-http2faq.md) pour en savoir plus.
