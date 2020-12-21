---
title: Configuration de la messagerie
seo-title: Configuration de la messagerie
description: Messagerie des communautés
seo-description: Messagerie des communautés
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
translation-type: tm+mt
source-git-commit: 9fa89ca34843d41a5ab5711c1090fcc7a1077760
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 4%

---


# Configuration de la messagerie {#configuring-messaging}

## Présentation {#overview}

La fonction de messagerie pour AEM Communities permet aux visiteurs (membres) du site connectés d&#39;envoyer des messages les uns aux autres qui sont accessibles lorsqu&#39;ils sont connectés au site.

La messagerie est activée pour un site communautaire en cochant une case lors de la création [du site communautaire](sites-console.md).

Cette page contient des informations sur la configuration par défaut et les ajustements possibles.

Pour plus d’informations pour les développeurs, voir [Messaging Essentials](essentials-messaging.md).

## Service des opérations de messagerie {#messaging-operations-service}

Le [service d&#39;opérations de messagerie d&#39;AEM Communities ](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifie le point de terminaison qui traite les demandes liées à la messagerie, les dossiers que le service doit utiliser pour stocker les messages et, si les messages peuvent inclure des pièces jointes, quels types de fichiers sont autorisés.

Pour les sites communautaires créés à l&#39;aide de la [console Sites des communautés](sites-console.md), il existe déjà une instance du service, avec la boîte de réception définie sur `/mail/community/inbox`.

### Service des opérations de messagerie communautaire {#community-messaging-operations-service}

Comme indiqué ci-dessous, il existe une configuration du service pour les sites créés avec l&#39;[assistant de création de site](sites-console.md). Vous pouvez afficher ou modifier la configuration en sélectionnant l’icône représentant un crayon en regard de la configuration :

![chlimage_1-63](assets/chlimage_1-63.png)

### Nouvelle configuration {#new-configuration}

Pour ajouter une nouvelle configuration, sélectionnez l’icône plus &quot;**+**&quot; en regard du nom du service :

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Champs de message]**
AllowlistSpécifie les propriétés du composant Composer un message que les utilisateurs peuvent modifier et conserver. Si de nouveaux éléments de formulaire sont ajoutés, l’ID d’élément doit être ajouté si vous souhaitez le stocker dans SRP. La valeur par défaut est de deux entrées : 
** sujet et  *contenu*.

* **[!UICONTROL Taille]**
limite de la zone de messageNombre maximal d’octets dans la zone de message de chaque utilisateur. La valeur par défaut est 
*1073741824* (1 Go).

* **[!UICONTROL Nombre de messages]**
limitéNombre total de messages autorisés par utilisateur. La valeur -1 indique qu’un nombre illimité de messages est autorisé, sous réserve de la taille limite de la zone de message. La valeur par défaut est 
*10000* (10k).

* **[!UICONTROL Signaler l&#39;]**
échec de la diffusionSi cette case est cochée, avertissez l&#39;expéditeur si la diffusion du message ne parvient pas à certains destinataires. La valeur par défaut est 
*vérifié*.

* **[!UICONTROL Diffusion d&#39;échec expéditeur]**
idName de l&#39;expéditeur qui apparaît dans le message d&#39;échec de la diffusion. La valeur par défaut est 
*failureNotifier*.

* **[!UICONTROL Modèle de message d&#39;échec]**
pathChemin absolu vers la racine du modèle de message d&#39;échec de la diffusion. La valeur par défaut est 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.]**
nameNombre de tentatives de renvoi d’un message dont la remise a échoué. La valeur par défaut est 
*3*.

* **[!UICONTROL minWaitBetweenRetries.]**
nameNombre de secondes d&#39;attente entre les tentatives de renvoi d&#39;un message en cas d&#39;échec de l&#39;envoi. La valeur par défaut est *100 *(secondes).

* **[!UICONTROL Compter la]**
taille du pool de mise à jourNombre de threads simultanés utilisés pour la mise à jour de la comptabilisation. La valeur par défaut est 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obligatoire*) Chemin d’accès, relatif au noeud de l’utilisateur (/home/users/*username*), à utiliser pour le  **`inbox`** dossier. Le chemin ne doit PAS se terminer par une barre oblique (/) à la fin. La valeur par défaut est */mail/inbox*.

* **[!UICONTROL stitems.path.name]**
(
*Obligatoire*) Chemin d’accès, relatif au noeud de l’utilisateur (/home/users/*username*), à utiliser pour le  **`senditems`** dossier. Le chemin ne doit PAS se terminer par une barre oblique (/) à la fin. La valeur par défaut est */mail/stitems*.

* **[!UICONTROL supportAttachments.]**
nameSi cette case est cochée, les utilisateurs peuvent ajouter des pièces jointes à leurs messages. La valeur par défaut est 
*vérifié*.

* **[!UICONTROL batchSize.]**
nameNombre de messages à regrouper par lots pour un envoi lors de l&#39;envoi à un grand groupe de destinataires. La valeur par défaut est 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.]**
nameSi supportAttachments est coché, cette valeur spécifie la taille totale maximale autorisée (en octets) de toutes les pièces jointes. La valeur par défaut est 
*104857600*  (100 Mo).

* **[!UICONTROL attachementTypeBlocklist.]**
nameliste bloquée d&#39;extensions de fichiers, précédée de &#39;
**.**&quot;, cela sera rejeté par le système. Si elle n’est pas placée sur la liste bloquée, l’extension est autorisée. Les extensions peuvent être ajoutées ou supprimées à l&#39;aide des icônes &#39;**+**&#39; et &#39;**-**&#39;. La valeur par défaut est *DEFAULT*.

* **[!UICONTROL allowAttachmentTypes.name]**

   **(*Action requise*)** liste autorisée des extensions de fichier, à l’opposé de la liste bloquée. Pour autoriser toutes les extensions de fichier, à l&#39;exception de celles placées sur la liste bloquée, utilisez l&#39;icône &quot;**-**&quot; pour supprimer l&#39;entrée vide unique.

* **[!UICONTROL serviceSelector.name]**
(*Obligatoire*) Chemin absolu (point de terminaison) par lequel le service est appelé (une ressource virtuelle). La racine du chemin choisi doit être incluse dans le paramètre de configuration *Chemins d&#39;exécution* d&#39;OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), tel que `/bin/`, `/apps/` et `/services/`. Pour sélectionner cette configuration pour la fonction de messagerie d&#39;un site, ce point de terminaison est fourni en tant que valeur **`Service selector`** pour `Message List and Compose Message components` (voir [Fonction du message](configure-messaging.md)). La valeur par défaut est */bin/messaging*.

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**Liste autorisée Champs de message**.

>[!CAUTION]
>
>Chaque fois qu&#39;une configuration `Messaging Operations Service` est ouverte pour modification, si `allowedAttachmentTypes.name` a été supprimée, une entrée vide est ajoutée pour rendre la propriété configurable. Une seule entrée vide désactive efficacement les pièces jointes.
>
>Pour autoriser toutes les extensions de fichier, à l’exception de celles placées sur la liste bloquée, utilisez l’icône &quot;**-**&quot; pour (à nouveau) supprimer l’entrée vide unique avant de cliquer sur **[!UICONTROL Enregistrer]**.

## Résolution des incidents {#troubleshooting}

Une façon de résoudre les problèmes consiste à activer les [messages de débogage dans le journal.](../../help/sites-administering/troubleshooting.md)

Voir aussi [Journaliseurs et écrivains pour les services individuels](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Le package à surveiller est `com.adobe.cq.social.messaging`.
