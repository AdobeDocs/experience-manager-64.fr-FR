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
translation-type: tm+mt
source-git-commit: 77cca35f74db2ced556b71c3192058b7c352ab4d
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 38%

---


# Service de gestion des utilisateurs et du contenu qu’ils génèrent dans AEM Communities  {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>Le RGPD est utilisé comme exemple dans les sections ci-dessous, mais les détails couverts sont applicables à toutes les réglementations relatives à la protection des données et à la protection de la vie privée ; comme le RGPD, l&#39;ACCP, etc.

AEM Communities expose les API prêtes à l’emploi pour gérer les profils utilisateur et gérer en bloc le contenu généré par l’utilisateur. Une fois activé, le service **UserUgcManagement** permet aux utilisateurs privilégiés (administrateurs de communauté et modérateurs) de désactiver les profils d’utilisateur et de supprimer ou d’exporter en masse l’UGC pour des utilisateurs spécifiques. Ces API permettent également aux contrôleurs et aux processeurs des données client de se conformer au Règlement général sur la protection des données (RGPD) de l&#39;Union européenne et à d&#39;autres mandats de confidentialité inspirés du RGPD.

Pour plus d’informations, voir la [page RGPD du centre de traitement des données personnelles d’Adobe](https://www.adobe.com/fr/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Si vous avez configuré [Adobe Analytics dans le site AEM Communities](analytics.md), les données utilisateur capturées sont envoyées au serveur Adobe Analytics. Adobe Analytics fournit des API qui vous permettent d’accéder, d’exporter et de supprimer des données utilisateur et de respecter les règles GDPR. Pour plus d&#39;informations, voir [Envoyer des demandes d&#39;accès et de suppression](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Pour utiliser ces API, vous devez activer le point de terminaison `/services/social/ugcmanagement` en activant le service UserUgcManagement. Pour activer ce service, installez l&#39;[exemple de servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) disponible sur [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Ensuite, accédez au point de terminaison de l’instance de publication de votre site de communautés avec les paramètres appropriés à l’aide d’une requête http, comme suit :

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

Cependant, vous pouvez également créer une IU (interface utilisateur) pour gérer les profils utilisateur et le contenu généré par les utilisateurs dans le système.

Ces API permettent de remplir les fonctions suivantes.

## Récupération du contenu généré par un utilisateur  {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` permet d’exporter tout l’UGC d’un utilisateur à partir du système.

* **utilisateur** : ID d’un utilisateur autorisé.
* **outputStream** : le résultat est renvoyé sous la forme d’un flux de sortie, qui est un fichier ZIP comprenant le contenu généré par l’utilisateur (un fichier JSON) et les pièces jointes (y compris les images ou les vidéos téléchargées par l’utilisateur).

Par exemple, pour exporter le contenu généré par un utilisateur nommé Weston McCall, qui utilise weston.mccall@dodgit.com comme ID autorisable afin de se connecter au site Communities, vous pouvez envoyer une requête HTTP GET similaire à ce qui suit :

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Suppression du contenu généré par un utilisateur {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, utilisateur de chaîne)** permet de supprimer du système tous les fichiers UGC d&#39;un utilisateur.

* **user** : ID autorisable d’un utilisateur.

Par exemple, pour supprimer l’UGC d’un utilisateur disposant d’un ID pouvant être autorisé weston.mccall@dodgit.com via une requête de POST HTTP, utilisez les paramètres suivants :

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### Supprimer l&#39;UGC de Adobe Analytics {#delete-ugc-from-analytics}

Pour supprimer les données utilisateur de l’Adobe Analytics, suivez le flux de travaux GDPR Analytics ; car l’API ne supprime pas les données utilisateur d’Adobe Analytics.

Pour les mappages de variables Adobe Analytics utilisés par AEM Communities, reportez-vous à l’image suivante :

![Mappage des variables de communautés AEM pour Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Désactivation d’un compte utilisateur {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, utilisateur String)** aide à désactiver un compte utilisateur.

* **user** : ID autorisable d’un utilisateur.

>[!NOTE]
>
>La désactivation d’un utilisateur supprime tout le contenu qu’il a généré et qui se trouve sur le serveur.

Par exemple, pour supprimer le profil d’un utilisateur disposant d’un ID weston.mccall@dodgit.com autorisé via une requête de POST HTTP, utilisez les paramètres suivants :

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>L’API deleteUserAccount() désactive un seul profil utilisateur dans le système, puis supprime le contenu généré par l’utilisateur. Cependant, pour supprimer un profil utilisateur du système, accédez à **CRXDE Lite** : [https://&lt;server>/crx/de](http://localhost:4502/crx/de), recherchez le noeud utilisateur et supprimez-le.
