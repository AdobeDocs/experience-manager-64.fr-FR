---
title: Service de gestion des utilisateurs et du contenu qu’ils génèrent dans AEM Communities
seo-title: Service de gestion des utilisateurs et du contenu qu’ils génèrent dans AEM Communities
description: 'Utilisez des API pour supprimer et exporter en masse du contenu généré par les utilisateurs et désactiver des comptes utilisateur. '
seo-description: 'Utilisez des API pour supprimer et exporter en masse du contenu généré par les utilisateurs et désactiver des comptes utilisateur. '
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
role: Admin
exl-id: f4adc53d-6809-4d89-a3dd-5d783e938a63
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 38%

---

# Service de gestion des utilisateurs et du contenu qu’ils génèrent dans AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>Le RGPD est utilisé comme exemple dans les sections ci-dessous, mais les détails couverts sont applicables à toutes les réglementations de protection des données et de confidentialité ; comme le RGPD, le CCPA, etc.

AEM Communities expose des API prêtes à l’emploi pour gérer les profils utilisateur et gérer en masse le contenu généré par l’utilisateur. Une fois activé, le service **UserUgcManagement** permet aux utilisateurs privilégiés (administrateurs de communauté et modérateurs) de désactiver les profils utilisateur et de supprimer ou d’exporter en masse le contenu créé par l’utilisateur pour des utilisateurs spécifiques. Ces API permettent également aux contrôleurs et aux processeurs des données clients de se conformer au Règlement général sur la protection des données (RGPD) de l’Union européenne et à d’autres mandats de confidentialité inspirés du RGPD.

Pour plus d’informations, voir la [page RGPD du centre de traitement des données personnelles d’Adobe](https://www.adobe.com/fr/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Si vous avez configuré [Adobe Analytics sur le site AEM Communities](analytics.md), les données utilisateur capturées sont envoyées au serveur Adobe Analytics. Adobe Analytics fournit des API qui vous permettent d’accéder, d’exporter et de supprimer des données utilisateur et de respecter le RGPD. Pour plus d’informations, voir [Soumettre les demandes d’accès et de suppression](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Pour utiliser ces API, vous devez activer le point de terminaison `/services/social/ugcmanagement` en activant le service UserUgcManagement. Pour activer ce service, installez l’[exemple de servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) disponible sur [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Ensuite, accédez au point de terminaison sur l’instance de publication de votre site Communities avec les paramètres appropriés à l’aide d’une requête http, semblable à ce qui suit :

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

Cependant, vous pouvez également créer une IU (interface utilisateur) pour gérer les profils utilisateur et le contenu généré par les utilisateurs dans le système.

Ces API permettent de remplir les fonctions suivantes.

## Récupération du contenu généré par un utilisateur {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` permet d’exporter tout le contenu généré par un utilisateur à partir du système.

* **user** : ID autorisable d’un utilisateur.
* **outputStream** : le résultat est renvoyé sous la forme d’un flux de sortie, qui est un fichier ZIP comprenant le contenu généré par l’utilisateur (un fichier JSON) et les pièces jointes (y compris les images ou les vidéos téléchargées par l’utilisateur).

Par exemple, pour exporter le contenu généré par un utilisateur nommé Weston McCall, qui utilise weston.mccall@dodgit.com comme ID autorisable afin de se connecter au site Communities, vous pouvez envoyer une requête HTTP GET similaire à ce qui suit :

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Suppression du contenu généré par un utilisateur {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** aide à supprimer du système tout le contenu généré par un utilisateur.

* **user** : ID autorisable d’un utilisateur.

Par exemple, pour supprimer le contenu généré par un utilisateur disposant d’un ID autorisable weston.mccall@dodgit.com par le biais d’une demande de POST HTTP, utilisez les paramètres suivants :

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### Suppression du contenu généré par l’utilisateur d’Adobe Analytics {#delete-ugc-from-analytics}

Pour supprimer les données utilisateur d’Adobe Analytics, suivez le processus d’analyse en vertu du RGPD ; car l’API ne supprime pas les données utilisateur d’Adobe Analytics.

Pour les mappages de variables Adobe Analytics utilisés par AEM Communities, reportez-vous à l’image suivante :

![Mappage des variables des communautés AEM pour Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Désactivation d’un compte utilisateur {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** aide à désactiver un compte utilisateur.

* **user** : ID autorisable d’un utilisateur.

>[!NOTE]
>
>La désactivation d’un utilisateur supprime tout le contenu qu’il a généré et qui se trouve sur le serveur.

Par exemple, pour supprimer le profil d’un utilisateur disposant d’un ID autorisable weston.mccall@dodgit.com via une requête de POST HTTP, utilisez les paramètres suivants :

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>L’API deleteUserAccount() désactive un seul profil utilisateur dans le système, puis supprime le contenu généré par l’utilisateur. Cependant, pour supprimer un profil utilisateur du système, accédez à **CRXDE Lite** : [https://&lt;serveur>/crx/de](http://localhost:4502/crx/de), recherchez le noeud utilisateur et supprimez-le.
