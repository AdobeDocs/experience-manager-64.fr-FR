---
title: Configuration du courrier électronique
seo-title: Configuring Email
description: Configuration des emails pour Communities
seo-description: Email configuration for Communities
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Admin
exl-id: 0a0222e7-ca30-4603-94ad-582005b2de11
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 5%

---

# Configuration du courrier électronique {#configuring-email}

AEM Communities utilise le courrier électronique pour

* [Notifications de communautés](notifications.md)
* [Abonnements des communautés](subscriptions.md)

Par défaut, la fonctionnalité de courrier électronique n’est pas fonctionnelle, car elle nécessite la spécification d’un serveur SMTP et d’un utilisateur SMTP.

>[!CAUTION]
>
>Les emails de notifications et d’abonnements ne doivent être configurés que sur la variable [Éditeur Principal](deploy-communities.md#primary-publisher).

## Configuration du service de messagerie par défaut {#default-mail-service-configuration}

Le service de messagerie par défaut est requis pour les notifications et les abonnements.

* Sur l’éditeur Principal
* Connexion avec droits d’administrateur
* Accédez au [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Par exemple : [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Recherchez la variable `Day CQ Mail Service`
* Sélectionner l’icône de modification

Reposez-vous sur la documentation de [Configuration des notifications par e-mail](../../help/sites-administering/notification.md), mais avec une différence dans ce champ `"From" address` is *not* obligatoire et doit être laissé vide.

Par exemple (renseigné avec des valeurs à des fins d’illustration uniquement) :

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL Nom d’hôte du serveur SMTP]**: *(obligatoire)* Le serveur SMTP à utiliser.

* **[!UICONTROL Port du serveur SMTP]** *(obligatoire)* Le port du serveur SMTP doit être supérieur ou égal à 25.

* **[!UICONTROL Utilisateur SMTP]**: *(obligatoire)* L’utilisateur SMTP.

* **[!UICONTROL Mot de passe SMTP]**: *(obligatoire)* Mot de passe de l’utilisateur SMTP.

* **[!UICONTROL Adresse &quot;De&quot;]**: Laissez vide
* **[!UICONTROL SMTP use SSL]**: Si cette case est cochée, un courrier électronique sécurisé est envoyé. Assurez-vous que le port est défini sur 465 ou selon les besoins pour le serveur SMTP.
* **[!UICONTROL Debug email]**: Si cette case est cochée, la journalisation des interactions serveur SMTP est activée.

## Configuration des emails AEM Communities {#aem-communities-email-configuration}

Une fois que la variable [service de messagerie par défaut](#default-mail-service-configuration) est configuré, les deux instances existantes de la fonction `AEM Communities Email Reply Configuration` La configuration OSGi, incluse dans la version, devient fonctionnelle.

Seule l&#39;instance pour les abonnements doit être paramétrée plus précisément lors de l&#39;autorisation de la réponse par email.

1. ` [email](#configuration-for-notifications)` instance

   pour les notifications, qui ne prennent pas en charge les courriers électroniques de réponse, et ne doivent pas être modifiées.

1. ` [subscriptions-email](#configuration-for-subscriptions)` instance

   nécessite une configuration pour activer complètement la création d’une publication à partir d’un courrier électronique de réponse.

Pour accéder aux instances de configuration des emails des communautés :

* Sur l’éditeur Principal
* Connexion avec droits d’administrateur
* Accédez au [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Par exemple : [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localiser `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### Configuration des notifications {#configuration-for-notifications}

L’instance de `AEM Communities Email Reply Configuration` La configuration OSGi avec l’adresse électronique Nom est destinée à la fonctionnalité de notifications. Cette fonctionnalité n’inclut pas la réponse par courrier électronique.

Cette configuration ne doit pas être modifiée.

* Recherchez la variable `AEM Communities Email Reply Configuration`
* Sélectionner l’icône de modification
* Vérifiez les **Nom** is `email`

* Vérifier **Créer une publication à partir d’un courrier électronique de réponse** is `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Configuration des abonnements {#configuration-for-subscriptions}

Pour les abonnements Communities, il est possible d’activer ou de désactiver la possibilité pour un membre de publier du contenu en répondant à un email.

* Recherchez la variable `AEM Communities Email Reply Configuration`
* Sélectionner l’icône de modification
* Vérifiez les **Nom** is `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Nom]** : *(obligatoire)* `subscriptions-email`. Ne Pas Modifier.

* **[!UICONTROL Créer une publication à partir d’un courrier électronique de réponse]**: Si cette case est cochée, le destinataire de l’email d’abonnement peut publier du contenu en envoyant une réponse. Cette option est cochée par défaut.
* **[!UICONTROL Ajout d’un ID suivi à l’en-tête]**: La valeur par défaut est `Reply-To`.

* **[!UICONTROL Longueur maximale de l’objet]**: Si l’identifiant de suivi est ajouté à l’objet, il s’agit de la longueur maximale de l’objet, à l’exception de l’identifiant suivi, après lequel il sera rogné. Notez que cette valeur doit être aussi petite que possible pour éviter que les informations d’ID trackées ne soient perdues. La valeur par défaut est 200.
* **[!UICONTROL Adresse électronique &quot;De&quot;]**: *(obligatoire)* Adresse à partir de laquelle l’email de notification sera envoyé. Probablement le même **Utilisateur SMTP** spécifié pour la variable [service de messagerie par défaut](#configuredefaultmailservice). La valeur par défaut est `no-reply@example.com`.

* **[!UICONTROL Réponse au délimiteur]**: Si l’ID de suivi est ajouté à l’en-tête de réponse, ce délimiteur est utilisé. La valeur par défaut est `+` (signe plus).

* **[!UICONTROL Préfixe d’ID de suivi dans l’objet]**: Si l’identifiant de suivi est ajouté à l’objet, ce préfixe est utilisé. La valeur par défaut est `post#`.

* **[!UICONTROL Préfixe d’ID de suivi dans le corps du message]**: Si l’identifiant de suivi est ajouté au corps du message, ce préfixe sera utilisé. La valeur par défaut est `Please do not remove this:`.

* **[!UICONTROL Email en tant que HTML]**: Si cette case est cochée, le type de contenu de l’email est défini comme `"text/html;charset=utf-8"`. Cette option est cochée par défaut.

* **[!UICONTROL Nom d’utilisateur par défaut]**: Ce nom ne sera utilisé pour aucun nom d’utilisateur. La valeur par défaut est `no-reply@example.com`.

* **[!UICONTROL Chemin d’accès racine des modèles]**: L’email est créé à l’aide d’un modèle stocké dans ce chemin racine. La valeur par défaut est `/etc/community/templates/subscriptions-email`.

## Configuration de l’importateur d’interrogations {#configure-polling-importer}

Pour que le courrier électronique soit importé dans le référentiel, il est nécessaire de configurer un importateur d’interrogations et de configurer ses propriétés manuellement dans le référentiel.

### Ajouter un nouvel importateur d’interrogations {#add-new-polling-importer}

* Sur l’éditeur Principal
* Connexion avec droits d’administrateur
* Accédez à la console de l’importateur d’interrogations. Par exemple : [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Sélectionnez **[!UICONTROL Ajouter]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Type]**: *(obligatoire)* Menu déroulant à sélectionner `POP3 (over SSL).`

* **[!UICONTROL URL]**: *(obligatoire)* Le serveur de mail sortant. Par exemple, `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Importer dans le chemin]**&amp;ast; : *(obligatoire)* Définissez sur . `/content/usergenerated/mailFolder/postEmails`
en accédant à la 
`postEmails`et sélectionnez **OK**

* **[!UICONTROL Intervalle de mise à jour en secondes]**: *(facultatif)* Le serveur de messagerie configuré pour le service de messagerie par défaut peut avoir des exigences concernant la valeur de l’intervalle de mise à jour. Par exemple, Gmail peut nécessiter un intervalle de `300`.

* **[!UICONTROL Connexion]**: *(facultatif)*

* **[!UICONTROL Mot de passe]**: *(facultatif)*

* **[!UICONTROL Cliquez sur OK]**

### Ajuster le protocole pour le nouvel importateur d’interrogations {#adjust-protocol-for-new-polling-importer}

Une fois la nouvelle configuration d’interrogation enregistrée, il est nécessaire de modifier davantage les propriétés de l’importateur d’emails d’abonnement afin de modifier le protocole à partir de `POP3` to `emailreply`

Utilisation [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Sur l’éditeur Principal
* Connexion avec droits d’administrateur
* Accédez à [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importateurs/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Sélectionner la configuration nouvellement créée
* Modification des propriétés suivantes

   * **feedType**: replace `pop3s` avec **`emailreply`**
   * **source**: remplacer le protocole de la source `pop3s://` avec **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

Les triangles rouges indiquent les propriétés modifiées. Veillez à enregistrer les modifications :

* Sélectionnez **[!UICONTROL Enregistrer tout]**
