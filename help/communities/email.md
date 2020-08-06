---
title: Configuration du courrier électronique
seo-title: Configuration du courrier électronique
description: Configuration des e-mails pour les communautés
seo-description: Configuration des e-mails pour les communautés
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 4%

---


# Configuration du courrier électronique {#configuring-email}

AEM Communities utilise le courrier électronique pour

* [Notifications des communautés](notifications.md)
* [Abonnements des communautés](subscriptions.md)

Par défaut, la fonction de messagerie n’est pas fonctionnelle, car elle requiert la spécification d’un serveur SMTP et d’un utilisateur SMTP.

>[!CAUTION]
>
>Le courrier électronique pour les notifications et les abonnements doit être configuré uniquement sur l’éditeur [](deploy-communities.md#primary-publisher)Principal.

## Configuration par défaut du service de messagerie {#default-mail-service-configuration}

Le service de messagerie par défaut est requis pour les notifications et les abonnements.

* Sur l’éditeur Principal
* Connecté avec des droits d’administrateur
* Access the [Web Console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localisez la variable `Day CQ Mail Service`
* Sélectionner l’icône de modification

Il est basé sur la documentation relative à la [configuration de la notification](../../help/sites-administering/notification.md)par courrier électronique, mais avec une différence dans le fait que le champ `"From" address` n’est ** pas obligatoire et doit rester vide.

Par exemple (renseigné avec des valeurs à des fins d’illustration uniquement) :

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL Nom]** d’hôte du serveur SMTP : *(obligatoire)* Serveur SMTP à utiliser.

* **[!UICONTROL Port]** du serveur SMTP *(requis)* Le port du serveur SMTP doit être supérieur ou égal à 25.

* **[!UICONTROL Utilisateur]** SMTP : *(obligatoire)* Utilisateur SMTP.

* **[!UICONTROL Mot de passe]** SMTP : *(obligatoire)* mot de passe de l’utilisateur SMTP.

* **[!UICONTROL Adresse]**&quot;De&quot; : Laisser vide
* **[!UICONTROL SMTP utilise SSL]**: Si cette case est cochée, envoie un courrier électronique sécurisé. Assurez-vous que le port est défini sur 465 ou comme requis pour le serveur SMTP.
* **[!UICONTROL Adresse électronique]** de débogage : Si cette case est cochée, active la journalisation des interactions du serveur SMTP.

## Configuration du courrier électronique AEM Communities {#aem-communities-email-configuration}

Une fois le service [de messagerie](#default-mail-service-configuration) par défaut configuré, les deux instances existantes de la configuration `AEM Communities Email Reply Configuration` OSGi, incluses dans la version, deviennent fonctionnelles.

Seule l’instance pour les abonnements doit être configurée plus avant lors de l’autorisation de la réponse par courrier électronique.

1. ` [email](#configuration-for-notifications)` instance

   pour les notifications, qui ne prennent pas en charge les courriers électroniques de réponse et ne doivent pas être modifiés

1. ` [subscriptions-email](#configuration-for-subscriptions)` instance

   requiert une configuration pour activer complètement la création de publication à partir d’un courrier électronique de réponse

Pour atteindre les instances de configuration du courrier électronique des Communautés :

* Sur l’éditeur Principal
* Connecté avec des droits d’administrateur
* Access the [Web Console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localiser `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### Configuration des notifications {#configuration-for-notifications}

L’instance de configuration `AEM Communities Email Reply Configuration` OSGi avec l’adresse électronique Nom est réservée à la fonction de notifications. Cette fonctionnalité n’inclut pas les réponses par courrier électronique.

Cette configuration ne doit pas être modifiée.

* Localisez la variable `AEM Communities Email Reply Configuration`
* Sélectionner l’icône de modification
* Vérifiez que le **nom** est `email`

* Vérifier que **Créer une publication à partir d’un courrier électronique** de réponse est `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Configuration des Abonnements {#configuration-for-subscriptions}

Pour les abonnements des communautés, il est possible d’activer ou de désactiver la possibilité pour un membre de publier du contenu en répondant à un courriel.

* Localisez la variable `AEM Communities Email Reply Configuration`
* Sélectionner l’icône de modification
* Vérifiez que le **nom** est `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Nom]** : *(obligatoire)* `subscriptions-email`. Ne pas modifier.

* **[!UICONTROL Créer une publication à partir d’un courrier électronique]** de réponse : Si cette case est cochée, le destinataire de l’abonnement de messagerie peut publier du contenu en envoyant une réponse. Cette option est cochée par défaut.
* **[!UICONTROL Ajouter l’id suivi à l’en-tête]**: La valeur par défaut est `Reply-To`.

* **[!UICONTROL Longueur maximale du sujet]**: Si l’ID d’outil de suivi est ajouté à la ligne d’objet, il s’agit de la longueur maximale de l’objet, à l’exclusion de l’ID suivi, après quoi il sera coupé. Notez que cette valeur doit être aussi petite que possible pour éviter la perte des informations d’ID de suivi. La valeur par défaut est 200.
* **[!UICONTROL Adresse]**&#x200B;électronique &quot;De&quot; : *(obligatoire)* Adresse à partir de laquelle le courrier électronique de notification est envoyé. Il est probable que le même utilisateur **** SMTP spécifié pour le service [de messagerie](#configuredefaultmailservice)par défaut. La valeur par défaut est `no-reply@example.com`.

* **[!UICONTROL Répondre au délimiteur]**: Si l’ID d’outil de suivi est ajouté à l’en-tête de réponse, ce délimiteur est utilisé. La valeur par défaut est `+` (signe plus).

* **[!UICONTROL Préfixe d&#39;ID d&#39;outil de suivi dans l&#39;objet]**: Si l’ID d’outil de suivi est ajouté à l’objet, ce préfixe est utilisé. La valeur par défaut est `post#`.

* **[!UICONTROL Préfixe d&#39;ID de suivi dans le corps]** du message : Si l&#39;ID d&#39;outil de suivi est ajouté au corps du message, ce préfixe est utilisé. La valeur par défaut est `Please do not remove this:`.

* **[!UICONTROL Courriel au format HTML]**: Si cette case est cochée, le type de contenu du courrier électronique est défini comme `"text/html;charset=utf-8"`. Cette option est cochée par défaut.

* **[!UICONTROL Nom]** d’utilisateur par défaut : Ce nom ne sera utilisé pour aucun utilisateur. La valeur par défaut est `no-reply@example.com`.

* **[!UICONTROL Chemin]** racine des modèles : Le courrier électronique est créé à l’aide d’un modèle stocké sur ce chemin d’accès racine. La valeur par défaut est `/etc/community/templates/subscriptions-email`.

## Configuration de l’importateur d’interrogations {#configure-polling-importer}

Pour que le courrier électronique soit introduit dans le référentiel, il est nécessaire de configurer un importateur d’interrogation et de configurer ses propriétés manuellement dans le référentiel.

### Ajouter un nouvel importateur d&#39;interrogation {#add-new-polling-importer}

* Sur l’éditeur Principal
* Connecté avec des droits d’administrateur
* Accédez à la console de l’importateur d’interrogationPar exemple, [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Sélectionner le **[!UICONTROL Ajoute]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Type]**: *(obligatoire)* Appuyez sur la touche &lt;Entrée> pour sélectionner `POP3 (over SSL).`

* **[!UICONTROL URL]**: *(obligatoire)* Serveur de messagerie sortant. Par exemple, `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Importer dans Path]**&amp;amp ; ast; : *(obligatoire)* Définissez cette variable sur `/content/usergenerated/mailFolder/postEmails`en accédant à la variable 
`postEmails`et sélectionnez **OK**

* **[!UICONTROL Intervalle de mise à jour en secondes]**: *(facultatif)* Le serveur de messagerie configuré pour le service de messagerie par défaut peut avoir des exigences concernant la valeur de l&#39;intervalle de mise à jour. Par exemple, Gmail peut nécessiter un intervalle de `300`temps.

* **[!UICONTROL Connexion]**: *(facultatif)*

* **[!UICONTROL Mot de passe]**: *(facultatif)*

* **[!UICONTROL Cliquez sur OK]**

### Modifier le protocole pour le nouvel importateur d&#39;interrogation {#adjust-protocol-for-new-polling-importer}

Une fois la nouvelle configuration d&#39;interrogation enregistrée, il est nécessaire de modifier davantage les propriétés de l&#39;importateur de messages électroniques d&#39;abonnement afin de modifier le protocole de `POP3` en `emailreply`

Using [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Sur l’éditeur Principal
* Connecté avec des droits d’administrateur
* Accédez à [https://&lt;serveur>:&lt;port>/crx/de/index.jsp#/etc/importateurs/polling.](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Sélectionner la configuration nouvellement créée
* Modifiez les propriétés suivantes :

   * **feedType**: remplacer `pop3s` par **`emailreply`**
   * **source**: remplacer le protocole source `pop3s://` par **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

Les triangles rouges indiquent les propriétés modifiées. Veillez à enregistrer les modifications :

* Select **[!UICONTROL Save All]**

