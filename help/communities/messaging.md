---
title: Configuration de la messagerie
seo-title: Configuring Messaging
description: Messagerie des communautés
seo-description: Communities messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 4%

---

# Configuration de la messagerie {#configuring-messaging}

## Présentation {#overview}

La fonction de messagerie d’AEM Communities permet aux visiteurs (membres) du site connectés d’envoyer entre eux des messages accessibles lorsqu’ils sont connectés au site.

La messagerie est activée pour un site de communauté en cochant une case pendant [création de site communautaire](sites-console.md).

Cette page contient des informations sur la configuration par défaut et les réglages possibles.

Pour plus d’informations à l’intention des développeurs, voir [Notions fondamentales sur la messagerie](essentials-messaging.md).

## Service des opérations de messagerie {#messaging-operations-service}

Le [Service des opérations de messagerie AEM Communities](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifie le point de terminaison qui gère les requêtes liées aux messages, les dossiers que le service doit utiliser pour le stockage des messages, et si les messages peuvent inclure des pièces jointes, quels types de fichiers sont autorisés.

Pour les sites de communauté créés à l’aide de la variable [Console Sites Communities](sites-console.md), il existe déjà une instance du service, la boîte de réception étant définie sur `/mail/community/inbox`.

### Service des opérations de messagerie communautaire {#community-messaging-operations-service}

Comme illustré ci-dessous, il existe une configuration du service pour les sites créés avec le [assistant de création de site](sites-console.md). La configuration peut être visualisée ou modifiée en sélectionnant l’icône en forme de crayon en regard de la configuration :

![chlimage_1-63](assets/chlimage_1-63.png)

### Nouvelle configuration {#new-configuration}

Pour ajouter une nouvelle configuration, sélectionnez le plus &quot;**+** Icône &#39; en regard du nom du service :

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Liste autorisée des champs de message]**
Indique les propriétés du composant Composer le message que les utilisateurs peuvent modifier et conserver. Si de nouveaux éléments de formulaire sont ajoutés, l’ID d’élément doit être ajouté si vous souhaitez le stocker dans SRP. La valeur par défaut est de deux entrées : 
*subject* et *content*.

* **[!UICONTROL Limite de taille de la zone de message]**
Nombre maximal d’octets dans la zone de message de chaque utilisateur. La valeur par défaut est 
*1073741824* (1 Go).

* **[!UICONTROL Limite du nombre de messages]**
Nombre total de messages autorisés par utilisateur. La valeur -1 indique qu’un nombre illimité de messages est autorisé, sous réserve de la limite de taille de la zone de message. La valeur par défaut est 
*10 000* (10k).

* **[!UICONTROL Notifier l’échec de la diffusion]**
Si cette case est cochée, avertissez l’expéditeur si la diffusion du message échoue à certains destinataires. La valeur par défaut est 
*vérifié*.

* **[!UICONTROL Identifiant de l&#39;expéditeur de la diffusion en échec]**
Nom de l’expéditeur qui apparaît dans le message en échec de la diffusion. La valeur par défaut est 
*failureNotifier*.

* **[!UICONTROL Chemin du modèle de message d’échec]**
Chemin d’accès absolu à la racine du modèle de message en échec de la diffusion. La valeur par défaut est 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**
Nombre de tentatives d’envoi d’un message qui ne parvient pas à être diffusé. La valeur par défaut est 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
Nombre de secondes d’attente entre les tentatives de renvoi du message en cas d’échec de l’envoi. La valeur par défaut est *100 *(secondes).

* **[!UICONTROL Count update pool size]**
Nombre de threads simultanés utilisés pour la mise à jour du nombre. La valeur par défaut est 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obligatoire*) Chemin d’accès, relatif au noeud de l’utilisateur (/home/users/*username*), à utiliser pour le **`inbox`** dossier. Le chemin ne doit PAS se terminer par une barre oblique (/) à la fin. La valeur par défaut est */mail/inbox* .

* **[!UICONTROL stitems.path.name]**
(
*Obligatoire*) Chemin d’accès, relatif au noeud de l’utilisateur (/home/users/*username*), à utiliser pour le **`senditems`** dossier. Le chemin ne doit PAS se terminer par une barre oblique (/) à la fin. La valeur par défaut est */mail/stitems* .

* **[!UICONTROL supportAttachments.name]**
Si cette case est cochée, les utilisateurs peuvent ajouter des pièces jointes à leurs messages. La valeur par défaut est 
*vérifié*.

* **[!UICONTROL batchSize.name]**
Nombre de messages à grouper pour un envoi lors de l’envoi à un grand groupe de destinataires. La valeur par défaut est 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]**
Si supportAttachments est coché, cette valeur spécifie la taille totale maximale autorisée (en octets) de toutes les pièces jointes. La valeur par défaut est 
*104857600* (100 Mo).

* **[!UICONTROL attachmentTypeBlocklist.name]**
Une liste bloquée d’extensions de fichier, précédée de &quot;
**.**&#39;, qui sera rejeté par le système. Si elle n’est pas placée sur la liste bloquée, l’extension est autorisée. Les extensions peuvent être ajoutées ou supprimées à l’aide du &quot;&quot;**+**&#39; et &#39;**-**&quot;. La valeur par défaut est *PAR DÉFAUT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Action requise*)** Liste autorisée d’extensions de fichier, à l’opposé de la liste bloquée. Pour autoriser toutes les extensions de fichier, à l’exception de celles placées sur la liste bloquée, utilisez le signe &quot;&quot;.**-** icône &quot;&quot; pour supprimer l’entrée vide unique.

* **[!UICONTROL serviceSelector.name]**
(*Obligatoire*) Chemin absolu (point de terminaison) par lequel le service est appelé (une ressource virtuelle). La racine du chemin choisi doit être incluse dans la variable *Chemins d’exécution* paramètre de configuration de la configuration OSGi [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), par exemple `/bin/`, `/apps/`, et `/services/`. Pour sélectionner cette configuration pour la fonction de messagerie d’un site, ce point de terminaison est fourni en tant que **`Service selector`** de la variable `Message List and Compose Message components` (voir [Fonctionnalité du message](configure-messaging.md)). La valeur par défaut est */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Utilisation 
**Liste autorisée des champs de message**.

>[!CAUTION]
>
>Chaque fois qu’une `Messaging Operations Service` la configuration est ouverte pour modification, si `allowedAttachmentTypes.name` a été supprimé, une entrée vide est de nouveau ajoutée pour rendre la propriété configurable. Une seule entrée vide désactive efficacement les pièces jointes.
>
>Pour autoriser toutes les extensions de fichier, à l’exception de celles placées sur la liste bloquée, utilisez le signe &quot;&quot;.**-** L’icône &quot; pour (à nouveau) supprimer l’entrée vide unique avant de cliquer sur **[!UICONTROL Enregistrer]**.

## Résolution des problèmes {#troubleshooting}

Pour résoudre les problèmes, une méthode consiste à activer [débogage des messages dans le journal.](../../help/sites-administering/troubleshooting.md)

Voir aussi [Enregistreurs et rédacteurs pour les services individuels](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Le module à surveiller est `com.adobe.cq.social.messaging`.
