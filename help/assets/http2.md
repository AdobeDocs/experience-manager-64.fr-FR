---
title: Diffusion de contenu HTTP/2
seo-title: HTTP2 Delivery of Content
description: HTTP/2 améliore la communication entre les navigateurs et les serveurs, ce qui accélère le transfert d’informations tout en réduisant la puissance de traitement nécessaire.
seo-description: HTTP/2 improves the way browsers and servers communicate, allowing for faster transfer of information while reducing the amount of needed processing power.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
exl-id: 59cd9f8c-6d01-448d-bf57-bdc9fd2e381b
feature: Asset Management
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 62%

---

# Diffusion de contenu HTTP/2   {#http-delivery-of-content}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Adobe est heureux d’annoncer la disponibilité de HTTP/2 pour la diffusion de contenu, protocole qui permet d’améliorer les performances globales.

## Qu’est-ce que le HTTP/2 ?  {#what-is-http}

Le HTTP/2 améliore la communication entre les navigateurs et les serveurs, en accélérant le transfert d’informations tout en réduisant la puissance de traitement nécessaire.

Le site web suivant décrit HTTP/2 et ses avantages de manière simple et rapide :

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Quels sont les principaux avantages de la transition vers le HTTP/2 pour la diffusion de contenu ?  {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

L’amélioration des performances varie considérablement en fonction de facteurs tels que le code de votre site web, la façon dont vous utilisez Dynamic Media, l’appareil, l’écran et l’emplacement du client, etc.

Les tests effectués par l’Adobe lui-même ont donné les résultats suivants :

* Pour les images, le temps de réponse s’est amélioré de 7 % à 28 % selon l’appareil et le navigateur. Les gains de performances les plus notables ont été enregistrés sur les appareils iOS.
* Pour les visionneuses, les performances de chargement ont été améliorées à 15 %.

La démonstration suivante illustre la différence entre le chargement HTTP/1 et HTTP/2 :

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Puis-je passer à HTTP/2 ? {#am-i-eligible-to-switch-over-to-http}

Pour utiliser HTTP/2, vous devez respecter les conditions suivantes :

* Utilisez le protocole HTTPS sécurisé pour vos demandes de médias riches.
* Utilisez le CDN de lots Adobe (réseau de diffusion de contenu) dans le cadre de votre licence Dynamic Media.
* Utilisez un domaine dédié (non-company-h.assetsadobe#.com).

   Si vous possédez déjà un domaine dédié, vous pouvez vous inscrire par le biais du support technique.

   Dans le cas contraire, Adobe programmera votre transition vers HTTP/2 pour 2018.

## Quel est le processus d’activation du HTTP/2 pour mon compte Dynamic Media ?  {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

Pour basculer vers le HTTP/2, vous devez en faire la demande, car cette procédure n’est pas automatique.

1. Envoyez une demande d’assistance technique pour passer à HTTP2. Voir [Accès au portail du service clientèle](https://helpx.adobe.com/fr/experience-manager/kb/accessing-aem-support-portal.html).

   1. Indiquez les informations suivantes dans votre demande de support :

      1. Nom, adresse électronique et numéro de téléphone du contact principal.
      1. Tous les domaines pour lesquels activer HTTP/2.
      1. Vérifiez que vous utilisez le protocole HTTPS sécurisé pour les demandes de médias riches.
      1. Vérifiez que vous utilisez le réseau de diffusion de contenu par Adobe et que vous n’êtes pas géré avec une relation directe.
      1. Assurez-vous d’utiliser un domaine dédié. Si vous utilisez Dynamic Media, vous utilisez déjà un domaine dédié.
   1. Le support technique vous ajoutera à la liste d’attente des clients HTTP/2 dans l’ordre dans lequel les demandes ont été envoyées.
   1. Lorsque l’Adobe est prêt à traiter votre demande, le support vous contactera pour coordonner la transition et définir une date cible.
   1. Vous recevez une notification à l’issue du processus et pouvez vérifier que la transition vers HTTP/2 abouti.

      Le navigateur ne détecte pas cette transition, il est donc nécessaire de télécharger une extension.

      Pour Firefox et Chrome, il existe une extension appelée &quot;HTTP/2 and SPDY Indicator&quot;. Les navigateurs ne prennent en charge le HTTP/2 qu’en mode sécurisé. Par conséquent, appelez une URL avec le protocole HTTPS pour vérifier. Si http/2 est pris en charge, cette extension est indiquée par l’extension sous la forme d’un symbole de Flash bleu et d’un en-tête &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.


## Quand puis-je espérer passer au HTTP/2 ?  {#when-can-i-expect-to-be-transitioned-over-to-http}

Les demandes seront traitées dans l’ordre dans lequel elles seront reçues par le support technique.

>[!NOTE]
>
>Le délai d’exécution peut être long, car la transition vers HTTP/2 implique l’effacement du cache. Par conséquent, seules quelques transitions client peuvent être traitées simultanément.

## Quels risques présente la transition vers HTTP/2 ? {#what-are-the-risks-with-moving-to-http}

La transition vers HTTP/2 efface votre cache sur le réseau de diffusion de contenu, car elle implique de passer à une nouvelle configuration du réseau de diffusion de contenu.

Le contenu non mis en cache atteint directement les serveurs Adobe d’origine jusqu’à ce que le cache soit reconstruit. C’est pour cette raison qu’Adobe prévoit de ne gérer que quelques transitions à la fois afin d’offrir des performances acceptables lors de l’extraction des demandes de notre site d’origine.

## Comment puis-je vérifier si une URL ou un site Web est activé avec le HTTP/2 ? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Le navigateur ne détecte pas cette transition, il est donc nécessaire de télécharger une extension.

Pour Firefox et Chrome, il existe une extension appelée &quot;HTTP/2 and SPDY Indicator&quot;. Les navigateurs ne prennent en charge le HTTP/2 qu’en mode sécurisé. Par conséquent, appelez une URL avec le protocole HTTPS pour vérifier. Si http/2 est pris en charge, cette extension est indiquée par l’extension sous la forme d’un symbole de Flash bleu et d’un en-tête &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.
