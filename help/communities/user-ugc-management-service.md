---
title: Service de gestion des utilisateurs et du contenu créé par l’utilisateur dans AEM Communities
seo-title: User and UGC Management Service in AEM Communities
description: Utilisez les API pour supprimer et exporter en bloc du contenu généré par les utilisateurs et désactiver le compte utilisateur.
seo-description: Use APIs to bulk delete and bulk export user generated content, and disable user account.
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
role: Admin
exl-id: f4adc53d-6809-4d89-a3dd-5d783e938a63
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 7%

---

# Service de gestion des utilisateurs et du contenu créé par l’utilisateur dans AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!IMPORTANT]
>
>Le RGPD est utilisé comme exemple dans les sections ci-dessous, mais les détails couverts sont applicables à toutes les réglementations de protection des données et de confidentialité, comme le RGPD, le CCPA, etc.

AEM Communities expose des API prêtes à l’emploi pour gérer les profils utilisateur et gérer en masse le contenu généré par l’utilisateur. Une fois activée, la variable **UserUgcManagement** Le service permet aux utilisateurs privilégiés (administrateurs de communauté et modérateurs) de désactiver les profils utilisateur et de supprimer ou d’exporter en masse du contenu créé par l’utilisateur pour des utilisateurs spécifiques. Ces API permettent également aux contrôleurs et aux processeurs des données clients de se conformer au Règlement général sur la protection des données (RGPD) de l’Union européenne et à d’autres mandats de confidentialité inspirés du RGPD.

Pour plus d’informations, voir [Page RGPD du Centre de traitement des données personnelles des Adobes](https://www.adobe.com/fr/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Si vous avez configuré [Adobe Analytics dans AEM Communities](analytics.md) , les données utilisateur capturées sont envoyées au serveur Adobe Analytics. Adobe Analytics fournit des API qui vous permettent d’accéder, d’exporter et de supprimer des données utilisateur et de respecter le RGPD. Pour plus d’informations, voir [Soumettre des demandes d’accès et de suppression](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Pour utiliser ces API, vous devez activer la variable `/services/social/ugcmanagement` endpoint en activant le service UserUgcManagement. Pour activer ce service, installez le [exemple de servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) disponible sur [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Ensuite, accédez au point de terminaison sur l’instance de publication de votre site Communities avec les paramètres appropriés à l’aide d’une requête http, semblable à ce qui suit :

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

Cependant, vous pouvez également créer une interface utilisateur (interface utilisateur) pour gérer les profils utilisateur et le contenu généré par les utilisateurs dans le système.

Ces API permettent d’exécuter les fonctions suivantes.

## Récupération du contenu généré par un utilisateur {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` permet d’exporter tout le contenu généré par un utilisateur à partir du système.

* **user**: ID autorisable d’un utilisateur.
* **outputStream**: result est renvoyé en tant que flux de sortie, qui est un fichier zip comprenant le contenu généré par l’utilisateur (en tant que fichier json) et les pièces jointes (qui incluent des images ou des vidéos téléchargées par l’utilisateur).

Par exemple, pour exporter le contenu généré par un utilisateur nommé Weston McCall, qui utilise weston.mccall@dodgit.com comme ID autorisable pour se connecter au site Communities, vous pouvez envoyer une demande de GET http similaire à ce qui suit :

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Suppression du contenu généré par un utilisateur {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** aide à supprimer du système tout le contenu généré par un utilisateur.

* **user**: ID autorisable de l’utilisateur.

Par exemple, pour supprimer le contenu généré par un utilisateur disposant d’un ID autorisable weston.mccall@dodgit.com par le biais d’une demande de POST HTTP, utilisez les paramètres suivants :

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### Suppression du contenu généré par l’utilisateur d’Adobe Analytics {#delete-ugc-from-analytics}

Pour supprimer les données utilisateur d’Adobe Analytics, suivez le processus d’analyse en vertu du RGPD ; car l’API ne supprime pas les données utilisateur d’Adobe Analytics.

Pour les mappages de variables Adobe Analytics utilisés par AEM Communities, reportez-vous à l’image suivante :

![Mappage des variables des communautés AEM pour Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Désactivation d’un compte d’utilisateur {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, utilisateur de chaîne)** aide à désactiver un compte d’utilisateur.

* **user**: ID autorisable de l’utilisateur.

>[!NOTE]
>
>La désactivation d’un utilisateur supprime tout le contenu généré par l’utilisateur sur le serveur.

Par exemple, pour supprimer le profil d’un utilisateur disposant d’un ID autorisable weston.mccall@dodgit.com via une requête de POST HTTP, utilisez les paramètres suivants :

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>L’API deleteUserAccount() désactive uniquement un profil utilisateur dans le système et supprime le contenu généré par l’utilisateur. Toutefois, pour supprimer un profil utilisateur du système, accédez à **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de), recherchez le noeud utilisateur et supprimez-le.
