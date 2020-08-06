---
title: Diffusion de ressources Dynamic Media
seo-title: Diffusion de ressources Dynamic Media
description: Découvrez comment diffuser des ressources Dynamic Media
seo-description: Découvrez comment diffuser des ressources Dynamic Media
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
translation-type: tm+mt
source-git-commit: 15d933a2e71a44e84cdcc9ae28f60c67b43bd8f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 91%

---


# Diffusion de ressources Dynamic Media {#delivering-dynamic-media-assets}

La diffusion des ressources Dynamic Media (vidéos et images) dépend de la mise en œuvre de votre site web.

Avec Dynamic Media, vous disposez de plusieurs options :

* Si votre site web est hébergé sur AEM, vous souhaiterez ajouter les ressources Dynamic Media directement à votre page.
* Si votre site web n’est pas hébergé par AEM, les possibilités suivantes s’offrent à vous :

   * Intégration de votre vidéo ou image à votre site web.
   * Liez des URL à votre application web. Utilisez la liaison lorsque vous souhaitez présenter un lecteur vidéo dans une fenêtre contextuelle ou modale.
   * Si votre site est réactif, vous pouvez [diffuser des images optimisées.](responsive-site.md)

>[!NOTE]
>
>L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis et utilise des informations à la dernière milliseconde de la diffusion pour réduire davantage encore la taille du fichier d’image en fonction de la vitesse de connexion du réseau et du navigateur. Voir [Imagerie numérique](imaging-faq.md) pour plus d’informations.

Pour plus d’informations, reportez-vous aux rubriques suivantes :

* [Ajouter des ressources de médias dynamiques à des pages Web](adding-dynamic-media-assets-to-pages.md)
* [Incorporation de la visionneuse de vidéos ou d’images sur une page Web](embed-code.md)
* [Activation de la protection de lien dynamique dans Dynamic Media](https://helpx.adobe.com/fr/experience-manager/6-4/assets/using/hotlink-protection.html)
* Intégration du filigrane numérique non visible (Digimarc) avec les médias dynamiques (à venir)
* [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md)
* [Diffusion d’images optimisées pour un site réactif](responsive-site.md)
* [Diffusion de contenu HTTP2](http2.md)
* [Annulation de la validité du contenu mis en cache dans le réseau de diffusion de contenu (CDN)](invalidate-cdn-cached-content.md)
* [Utilisation de jeux de règles de transformation d’URL](using-rulesets-to-transform-urls.md)

## Diffusion de ressources Dynamic Media via HTTP/2  {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, reportez-vous aux [Questions fréquentes sur la diffusion de contenu HTTP/2](/help/sites-administering/scene7-http2faq.md).
