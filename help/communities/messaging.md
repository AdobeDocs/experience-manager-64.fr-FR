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
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 1%

---


# Configuration de la messagerie {#configuring-messaging}

## Présentation {#overview}

La fonction de messagerie pour les AEM Communities permet aux visiteurs (membres) du site connectés d&#39;envoyer des messages les uns aux autres qui sont accessibles lorsqu&#39;ils sont connectés au site.

La messagerie est activée pour un site communautaire en cochant une case lors de la création [d&#39;un site](sites-console.md)communautaire.

Cette page contient des informations sur la configuration par défaut et les ajustements possibles.

For additional information for developers, see [Messaging Essentials](essentials-messaging.md).

## Service des opérations de messagerie {#messaging-operations-service}

Le service [des opérations de messagerie](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) AEM Communities identifie le point de terminaison qui traite les demandes liées à la messagerie, les dossiers que le service doit utiliser pour stocker les messages et, si les messages peuvent inclure des pièces jointes, quels types de fichiers sont autorisés.

Pour les sites communautaires créés à l&#39;aide de la console [Sites](sites-console.md)des communautés, une instance du service existe déjà, avec la boîte de réception définie sur `/mail/community/inbox`.

### Service des opérations de messagerie communautaire {#community-messaging-operations-service}

Comme illustré ci-dessous, il existe une configuration du service pour les sites créés avec l&#39;Assistant [de création de](sites-console.md)site. Vous pouvez afficher ou modifier la configuration en sélectionnant l’icône représentant un crayon en regard de la configuration :

![chlimage_1-63](assets/chlimage_1-63.png)

### Nouvelle configuration {#new-configuration}

Pour ajouter une nouvelle configuration, sélectionnez l’icône plus &quot;**+**&quot; en regard du nom du service :

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Liste autorisée]** Champs de message Indique les propriétés du composant Composer les messages que les utilisateurs peuvent modifier et conserver. Si de nouveaux éléments de formulaire sont ajoutés, l’ID d’élément doit être ajouté si vous souhaitez le stocker dans SRP. La valeur par défaut est de deux entrées : *sujet* et *contenu*.
**[!UICONTROL Taille limite]** de la zone de message Nombre maximal d’octets dans la zone de message de chaque utilisateur. La valeur par défaut est *1073741824* (1 Go).**

* **[!UICONTROL Limite]** du nombre de messages Nombre total de messages autorisés par utilisateur. La valeur -1 indique qu’un nombre illimité de messages est autorisé, sous réserve de la taille limite de la zone de message. La valeur par défaut est *10000* (10 Ko).
**[!UICONTROL Signaler l&#39;échec]** de la diffusion Si cette case est cochée, avertissez l&#39;expéditeur si la diffusion de message ne parvient pas à certains destinataires. Default is *checked*.*

* **[!UICONTROL ID]** de l&#39;expéditeur de la diffusion d&#39;échec Nom de l&#39;expéditeur qui apparaît dans le message d&#39;échec de la diffusion. La valeur par défaut est *failureNotifier*.
**[!UICONTROL Chemin]** du modèle de message d’échec Chemin absolu vers la racine du modèle de message d’échec de la diffusion. La valeur par défaut est */etc/notification/messaging/default*.*

* **[!UICONTROL maxRetries.name]** Nombre de tentatives de renvoi d’un message dont la remise échoue. La valeur par défaut est *3*.
**[!UICONTROL minWaitBetweenRetries.name]** Nombre de secondes d&#39;attente entre les tentatives de renvoi d&#39;un message en cas d&#39;échec de l&#39;envoi. La valeur par défaut est *100 *(secondes).*

* **[!UICONTROL Compter la taille]** du pool de mise à jour Nombre de threads simultanés utilisés pour la mise à jour de la comptabilisation. La valeur par défaut est *10*.
**[!UICONTROL inbox.path.name]**(*Obligatoire*) Chemin d’accès, relatif au noeud de l’utilisateur (/home/users/*username*), à utiliser pour le **`inbox`** dossier. Le chemin ne doit PAS se terminer par une barre oblique (/) à la fin. La valeur par défaut est */mail/inbox* .*

* **[!UICONTROL stitems.path.name]**(*Obligatoire*) Chemin d’accès, relatif au noeud de l’utilisateur (/home/users/*username*), à utiliser pour le **`senditems`** dossier. Le chemin ne doit PAS se terminer par une barre oblique (/) à la fin. La valeur par défaut est */mail/stitems* .
**[!UICONTROL supportAttachments.name]** Si cette case est cochée, les utilisateurs peuvent ajouter des pièces jointes à leurs messages. Default is *checked*.*

* **[!UICONTROL batchSize.name]** Nombre de messages à regrouper par lots pour un envoi lors de l&#39;envoi à un grand groupe de destinataires. La valeur par défaut est *100*.
**[!UICONTROL maxTotalAttachmentSize.name]** Si supportAttachments est coché, cette valeur spécifie la taille totale maximale autorisée (en octets) de toutes les pièces jointes. Default is *104857600* (100 MB).*

* **[!UICONTROL attachementTypeAllowlist.name]** liste bloquée d&#39;extensions de fichier, précédée de &#39;**.**&quot;, cela sera rejeté par le système. Si elle n’est pas placée sur l&#39;liste bloquée, l’extension est autorisée. Les extensions peuvent être ajoutées ou supprimées à l&#39;aide des icônes &quot;**+**&quot; et &quot;**-**&quot;. Default is *DEFAULT*.

* **[!UICONTROL allowAttachmentTypes.name]**

**(*Action requise*)** liste autorisée des extensions de fichier, à l’opposé de la liste bloquée. Pour autoriser toutes les extensions de fichier, à l&#39;exception de celles placées sur l&#39;liste bloquée, utilisez l&#39;icône &quot;**-**&quot; pour supprimer l&#39;entrée vide unique.

* **[!UICONTROL serviceSelector.name]**(*Obligatoire*) Chemin absolu (point de terminaison) par lequel le service est appelé (une ressource virtuelle). La racine du chemin choisi doit être incluse dans le paramètre de configuration *Execution Paths* de la configuration OSGi [`Apache Sling Servlet/Script Resolver and Error Handler`[#$tu39], telle que `/bin/`, `/apps/`et `/services/`. Pour sélectionner cette configuration pour la fonction de messagerie d&#39;un site, ce point de terminaison est fourni comme **`Service selector`** valeur pour la `Message List and Compose Message components` (voir Fonction [de](configure-messaging.md)message). La valeur par défaut est */bin/messaging* .


* 


* 


* 


* 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeAllowlist.name]**
A blocklist of file extensions, prefixed with &#39;
**.**&#39;, that will be rejected by the system. If not blocklisted, then the extension is allowed. Extensions may be added or removed using the &#39;**+**&#39; and &#39;**-**&#39; icons. Default is *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Action Required*)** An allowlist of file extensions, the opposite of the blocklist. To allow all file extensions, except for those blocklisted, use the &#39;**-**&#39; icon to remove the single empty entry.

* **[!UICONTROL serviceSelector.name]**
(*Required*) An absolute path (endpoint) through which the service is invoked (a virtual resource). The root of the path chosen must be one included in the *Execution Paths* configuration setting of OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`-ERR:REF-NOT-FOUND-, such as `/bin/`, `/apps/`, and `/services/`. To select this configuration for a site&#39;s messaging feature, this endpoint is provided as the **`Service selector`** value for the `Message List and Compose Message components` (see [Message Feature](configure-messaging.md)). The default is */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Use 
**Message Fields Allowlist**.

>[!CAUTION]
>
>Each time a `Messaging Operations Service` configuration is opened for edit, if `allowedAttachmentTypes.name` had been removed, an empty entry is re-added to make the property configurable. A single empty entry effectively disables file attachments.
>
>To allow all file extensions, except for those blocklisted, use the &#39;**-**&#39; icon to (again) remove the single empty entry before clicking **[!UICONTROL Save]**.

## Troubleshooting {#troubleshooting}

One way to troubleshoot problems is to enable [debugging messages in the log.](../../help/sites-administering/troubleshooting.md)

See also [Loggers and Writers for Individual Services](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

The package to monitor is `com.adobe.cq.social.messaging`.
