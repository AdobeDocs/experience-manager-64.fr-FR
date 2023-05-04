---
title: Le framework de protection CSRF
seo-title: The CSRF Protection Framework
description: Le framework utilise des jetons pour garantir que la demande du client est légitime
seo-description: The framework makes use of tokens to guarantee that the client request is legitimate
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
exl-id: 533c348e-517f-4d70-a89c-bfc87f71a633
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 76%

---

# Le framework de protection CSRF {#the-csrf-protection-framework}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Outre le filtre de référent Apache Sling, Adobe fournit également un nouveau framework de protection CSRF pour se protéger contre ce type d’attaque.

Le framework utilise des jetons pour garantir que la demande du client est légitime. Les jetons sont générés lorsque le formulaire est envoyé au client et validé lorsque le formulaire est renvoyé au serveur.

>[!NOTE]
>
>Il n’y a aucun jeton sur les instances de publication pour les utilisateurs anonymes.

## Conditions requises {#requirements}

### Dépendances {#dependencies}

Tout composant associé à la dépendance `granite.jquery` bénéficie automatiquement du framework de protection CSRF. Si ce n’est pas le cas pour l’un de vos composants, vous devez déclarer une dépendance à `granite.csrf.standalone` avant de pouvoir utiliser le framework.

### Réplication de la clé de chiffrement {#replicating-crypto-keys}

Pour utiliser les jetons, vous devez répliquer le binaire `/etc/keys/hmac` sur toutes les instances de votre déploiement. Un moyen pratique de copier la clé HMAC sur toutes les instances consiste à créer un package contenant la clé et à l’installer via le gestionnaire de packages sur toutes les instances.

>[!NOTE]
>
>Assurez-vous également d’effectuer les [modifications de configuration du Dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/user-guide.html) nécessaires pour utiliser le framework de protection CSRF.

>[!NOTE]
>
>Si vous utilisez le cache de manifeste avec votre application Web, veillez à ajouter « **&amp;ast;** » au manifeste afin de vous assurer que le jeton ne prend pas l’appel de génération de jeton CSRF hors ligne. Pour plus d’informations, consultez ce [lien](https://www.w3.org/TR/offline-Webapps/).
>
>Pour plus d’informations sur les attaques CSRF et les moyens de s’en protéger, consultez la page [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
