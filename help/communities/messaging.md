---
title: Configuration de la messagerie
seo-title: Configuration de la messagerie
description: Messages des communautés
seo-description: Messages des communautés
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c

---


# Configuration de la messagerie {#configuring-messaging}

## Présentation {#overview}

La fonction de messagerie des communautés AEM permet aux visiteurs (membres) du site connectés d’envoyer des messages qui sont accessibles lorsqu’ils sont connectés au site.

La messagerie est activée pour un site communautaire en cochant une case lors de la création [d&#39;un site](sites-console.md)communautaire.

Cette page contient des informations sur la configuration par défaut et les ajustements possibles.

For additional information for developers, see [Messaging Essentials](essentials-messaging.md).

## Service des opérations de messagerie {#messaging-operations-service}

Le service [](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) AEM Communities Messaging Operations identifie le point de fin qui traite les demandes liées à la messagerie, les dossiers que le service doit utiliser pour le stockage des messages et, si les messages peuvent inclure des pièces jointes, les types de fichiers autorisés.

Pour les sites communautaires créés à l’aide de la console [Sites](sites-console.md)des communautés, une instance du service existe déjà, avec la boîte de réception définie sur `/mail/community/inbox`.

### Service des opérations de messagerie communautaire {#community-messaging-operations-service}

Comme illustré ci-dessous, il existe une configuration du service pour les sites créés avec l&#39;assistant [de création de](sites-console.md)site. Vous pouvez afficher ou modifier la configuration en sélectionnant l’icône représentant un crayon en regard de la configuration :

![chlimage_1-63](assets/chlimage_1-63.png)

### New Configuration {#new-configuration}

Pour ajouter une nouvelle configuration, sélectionnez l’icône + &quot;**+**&quot; en regard du nom du service :

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Liste blanche des champs de message]** Spécifie les propriétés du composant Composer les messages que les utilisateurs peuvent modifier et conserver. Si de nouveaux éléments de formulaire sont ajoutés, l’ID d’élément doit être ajouté si vous souhaitez le stocker dans SRP. La valeur par défaut est de deux entrées : *sujet* et *contenu*.

* **[!UICONTROL Taille limite]** de la zone de message Nombre maximal d’octets dans la zone de message de chaque utilisateur. La valeur par défaut est *1073741824* (1 Go).

* **[!UICONTROL Nombre limite]** de messages Nombre total de messages autorisés par utilisateur. La valeur -1 indique qu’un nombre illimité de messages est autorisé, sous réserve de la taille limite de la zone de message. La valeur par défaut est *1 0000* (10 000).

* **[!UICONTROL Signaler l’échec]** de remise Si cette option est cochée, avertissez l’expéditeur si la remise des messages échoue à certains destinataires. Default is *checked*.

* **[!UICONTROL Échec de remise ID]** d&#39;expéditeur Nom de l&#39;expéditeur qui apparaît dans le message d&#39;échec de remise. La valeur par défaut est *failureNotifier*.

* **[!UICONTROL Chemin]** Absolu du modèle de message d’échec vers la racine du modèle de message d’échec de remise. La valeur par défaut est */etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]** Nombre de tentatives de renvoi d’un message dont la remise a échoué. La valeur par défaut est *3*.

* **[!UICONTROL minWaitBetweenRetries.name]** Nombre de secondes d’attente entre les tentatives de renvoi du message en cas d’échec de l’envoi. La valeur par défaut est *100 *(secondes).

* **[!UICONTROL Compter la taille]** du pool de mise à jour Nombre de threads simultanés utilisés pour la mise à jour du compte. La valeur par défaut est *10*.

* **[!UICONTROL inbox.path.name]**(*Obligatoire*) Chemin d’accès, relatif au noeud de l’utilisateur (/home/users/*username*), à utiliser pour le **`inbox`** dossier. Le chemin ne doit PAS se terminer par une barre oblique (/) à la fin. La valeur par défaut est */mail/inbox* .

* **[!UICONTROL stitems.path.name]**(*Obligatoire*) Chemin d’accès, relatif au noeud de l’utilisateur (/home/users/*username*), à utiliser pour le **`senditems`** dossier. Le chemin ne doit PAS se terminer par une barre oblique (/) à la fin. La valeur par défaut est */mail/stitems* .

* **[!UICONTROL supportAttachments.name]** Si cette option est cochée, les utilisateurs peuvent ajouter des pièces jointes à leurs messages. Default is *checked*.

* **[!UICONTROL batchSize.name]** Nombre de messages à traiter ensemble pour une envoi lors de l’envoi à un grand groupe de destinataires. La valeur par défaut est *100*.

* **[!UICONTROL maxTotalAttachmentSize.name]** Si supportAttachments est coché, cette valeur spécifie la taille totale maximale autorisée (en octets) de toutes les pièces jointes. Default is *104857600* (100 MB).

* **[!UICONTROL attachementTypeBlacklist.name]** Liste noire des extensions de fichier, précédée de &#39;**.**&quot;, cela sera rejeté par le système. Si elle n’est pas mise sur liste noire, l’extension est autorisée. Les extensions peuvent être ajoutées ou supprimées à l’aide des icônes &quot;**+**&quot; et &quot;**-**&quot;. Default is *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**
   **(*Action requise*)** Liste blanche des extensions de fichiers, le contraire de la liste noire. Pour autoriser toutes les extensions de fichier, à l’exception de celles qui sont bloquées, utilisez l’icône &quot;**-**&quot; pour supprimer l’entrée vide unique.

* **[!UICONTROL serviceSelector.name]**(*Obligatoire*) Chemin absolu (point de terminaison) par lequel le service est appelé (ressource virtuelle). La racine du chemin choisi doit être incluse dans le paramètre de configuration Chemins *d&#39;* exécution de la configuration OSGi [ , par exemple `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), `/bin/`et `/apps/``/services/`. Pour sélectionner cette configuration pour la fonction de messagerie d’un site, ce point de fin est fourni comme **`Service selector`** valeur pour la `Message List and Compose Message components` (voir Fonction [de](configure-messaging.md)message). La valeur par défaut est */bin/messaging* .

* **[!UICONTROL fieldWhitelist.name]** Utiliser la liste blanche des champs de **message**.

>[!CAUTION]
>
>Chaque fois qu’une `Messaging Operations Service` configuration est ouverte pour modification, si `allowedAttachmentTypes.name` elle a été supprimée, une entrée vide est ajoutée pour rendre la propriété configurable. Une seule entrée vide désactive les pièces jointes.
>
>Pour autoriser toutes les extensions de fichier, à l’exception de celles qui sont bloquées, utilisez l’icône &quot;**-**&quot; pour (à nouveau) supprimer l’entrée vide unique avant de cliquer sur **[!UICONTROL Enregistrer]**.

## Résolution des incidents {#troubleshooting}

Une manière de résoudre les problèmes consiste à activer les messages de [débogage dans le journal.](../../help/sites-administering/troubleshooting.md)

Voir aussi [Journaux et Ecrivains pour les services](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services)individuels.

Le package à surveiller est `com.adobe.cq.social.messaging`.
