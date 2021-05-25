---
title: Fonction de messagerie
seo-title: Fonction de messagerie
description: Configuration des composants de messagerie
seo-description: Configuration des composants de messagerie
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 29%

---

# Fonction de messagerie {#messaging-feature}

Outre les interactions publiques qui se produisent dans les forums et les commentaires, la fonction de messagerie d’AEM Communities permet aux membres de la communauté d’interagir de manière plus privée.

Cette fonctionnalité peut être incluse lors de la création d’un [site communautaire](overview.md#communitiessites).

La fonction de messagerie permet :

* Envoyer un message à un ou plusieurs membres de la communauté
* Envoyer un message à un groupe de membres de la communauté
* Envoi d’un message avec des pièces jointes
* Transférer un message
* Répondre à un message
* Supprimer un message
* Restaurer un message supprimé

Pour activer et modifier la fonction de messagerie, consultez la page

* [Configuration de la ](messaging.md) messagerie pour les administrateurs
* [Concepts ](essentials-messaging.md) essentiels de la messagerie pour les développeurs

>[!NOTE]
>
>Il n’est pas pris en charge d’ajouter des composants `Compose Message, Message, or Message List` (qui se trouvent dans le groupe de composants `Communities`) à une page en mode d’édition de création.

## Configuration des composants de messagerie {#configuring-messaging-components}

Lorsque la messagerie est activée pour un site de la communauté, elle est entièrement configurée sans autre configuration nécessaire. Ces informations sont fournies s’il est nécessaire de modifier la configuration par défaut.

### Configuration de la liste des messages (messagebox) {#configuring-message-list-messagebox}

Pour modifier la configuration de la liste des messages pour les pages **Boîte de réception**, **Éléments envoyés** et **Corbeille** de la fonction de messagerie, ouvrez le site en [mode d’édition de l’auteur](sites-console.md#authoring-site-content).

En mode `Preview` , sélectionnez le lien **[!UICONTROL Messages]** pour ouvrir la page de messagerie principale. Sélectionnez ensuite **[!UICONTROL Boîte de réception, Éléments envoyés ou Corbeille]** afin de configurer le composant pour cette liste de messages.

En mode `Edit`, sélectionnez le composant sur la page.

Pour accéder à la boîte de dialogue de configuration, il est nécessaire d’annuler l’héritage en sélectionnant l’icône `link`.

Une fois la configuration terminée, il est nécessaire de restaurer l’héritage en sélectionnant l’icône `broken link`.

![chlimage_1-396](assets/chlimage_1-396.png)

Une fois l’héritage annulé, il sera possible de sélectionner l’icône `configure` pour ouvrir la boîte de dialogue de configuration.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Onglet De Base {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Sélecteur de service]**
 (*Obligatoire*) Définissez-le sur la valeur de la propriété  `serviceSelector.name` du  [service des opérations de messagerie AEM Communities](messaging.md#messaging-operations-service).

* **[!UICONTROL Composer la page]**
 (*Obligatoire*) Page à ouvrir lorsqu’un membre clique sur le  `Reply` bouton. La page cible devrait contenir le formulaire **[!UICONTROL Composer le message.]**

* **[!UICONTROL Répondre/Afficher en tant que ressource]** Si vous cochez cette case, les URL de réponse et d’affichage font référence à une ressource. Dans le cas contraire, les données sont transmises sous forme de paramètres de requête dans l’URL. 

* **[!UICONTROL Formulaire d’affichage du profil]** Formulaire de profil à utiliser pour afficher le profil de l’expéditeur.

* **[!UICONTROL Dossier Corbeille]** Si vous cochez cette case, ce composant Liste des messages affiche uniquement les messages marqués comme supprimés (corbeille).

* **[!UICONTROL Chemins d’accès aux dossiers]**
 (*Obligatoire*) Référençant les valeurs définies pour  `inbox.path.name` et  `sentitems.path.name` dans le  [service d’opérations de messagerie AEM Communities](messaging.md#messaging-operations-service). Lors de la configuration pour un `Inbox`, ajoutez une entrée à l’aide de la valeur `inbox.path.name`. Lors de la configuration pour un `Outbox`, ajoutez une entrée à l’aide de la valeur `sentitems.path.name`. Lors de la configuration de pour `Trash`, ajoutez deux entrées avec les deux valeurs.

#### Onglet Affichage {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Marquer le]**
bouton de lecture Si cette option est cochée, une 
`Read`permettant de marquer un message comme lu.

* **[!UICONTROL Marquer comme non lu]**
BoutonSi cette option est cochée, une 
`Mark Unread` permettant de marquer un message comme lu.

* **[!UICONTROL Supprimer le]**
boutonSi cette option est cochée, un 
`Delete`permettant de marquer un message comme lu. dupliquera la fonctionnalité de suppression si **`Message Options`** est également coché.

* **[!UICONTROL Options de message]**
Si cette option est cochée, elle s’affiche. 
**`Reply`** les boutons  **`Reply All`**,  **`Forward`** et  **`Delete`** permettant de renvoyer ou de supprimer un message. dupliquera la fonctionnalité de suppression si **`Delete Button`** est également coché.

* **[!UICONTROL Messages par page]** Le nombre spécifié est le nombre maximal de messages affichés par page dans le modèle de pagination. Si aucun chiffre n’est spécifié (si vous laissez le champ vide), tous les messages s’affichent sans pagination.

* **[!UICONTROL Modèles d’horodatage]** Indiquez des modèles d’horodatage pour une ou plusieurs langues. Des valeurs sont fournies par défaut pour en, de, fr, it, es, ja, zh_CN et ko_KR.

* **[!UICONTROL Afficher]**
UserChoose 
**`Sender`** ou  **`Recipients`** pour déterminer s&#39;il faut afficher l&#39;expéditeur ou les destinataires.

### Configuration de Composer le message {#configuring-compose-message}

Pour modifier la configuration de la page de composition de messages, ouvrez le site en [mode d’édition de l’auteur](sites-console.md#authoring-site-content).

En mode `Preview`, sélectionnez le lien **[!UICONTROL Messages]** pour ouvrir la page de messagerie principale. Sélectionnez ensuite le bouton Nouveau message pour ouvrir la page `Compose Message`.

En mode `Edit` , sélectionnez le composant principal sur la page contenant le corps du message.

Pour accéder à la boîte de dialogue de configuration, il est nécessaire d’annuler l’héritage en sélectionnant l’icône `link`.

Une fois la configuration terminée, il est nécessaire de restaurer l’héritage en sélectionnant l’icône `broken link`.

![chlimage_1-400](assets/chlimage_1-400.png)

Une fois l’héritage annulé, il sera possible de sélectionner l’icône `configure` pour ouvrir la boîte de dialogue de configuration.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Onglet De Base {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL URL de redirection]** Saisissez l’URL de la page affichée une fois le message envoyé. Par exemple, 
`../messaging.html`.

* **[!UICONTROL Annuler l’URL]** Saisissez l’URL de la page affichée si l’expéditeur annule le message. Par exemple, 
`../messaging.html`.

* **[!UICONTROL Longueur maximale de l’objet du message]** Nombre maximal de caractères autorisé dans le champ Objet. Par exemple, 500. La valeur par défaut n’est pas limitée.

* **[!UICONTROL Longueur maximale du corps du message]** Nombre maximal de caractères autorisé dans le champ Contenu. Par exemple, 10000. La valeur par défaut n’est pas limitée.

* **[!UICONTROL Sélecteur de service]**
 (*Obligatoire*) Définissez-le sur la valeur de la propriété  **`serviceSelector.name`** du  [service des opérations de messagerie AEM Communities](messaging.md#messaging-operations-service).

#### Onglet Affichage {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Afficher le]**
champ d’objet Si cette option est cochée, le champ 
`Subject` et activer l’ajout d’un objet au message. Cette option n’est pas cochée par défaut.

* ****
Libellé de l’objet Saisissez le texte à afficher en regard du champ 
`Subject` field. La valeur par défaut est `Subject`.

* **[!UICONTROL Afficher le]**
champ Joindre le fichier Si cette option est cochée, le paramètre 
`Attachment` et activer l’ajout de pièces jointes au message. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Joindre le]**
libellé du fichier Saisissez le texte à afficher en regard de l’option 
`Attachment` champ . La valeur par défaut est **`Attach File`**.

* **[!UICONTROL Afficher le]**
champ de contenu Si cette option est cochée, le paramètre 
`Content` et activer l’ajout d’un corps de message. Cette option n’est pas cochée par défaut.

* ****
Libellé du contenuSaisissez le texte à afficher en regard du champ 
`Content` champ . La valeur par défaut est **`Body`**.

* **[!UICONTROL Avec l’éditeur de texte enrichi]** Si vous cochez cette case, une zone de texte personnalisée Contenu est utilisée avec son propre éditeur de texte enrichi. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Modèles d’horodatage]** Indiquez des modèles d’horodatage pour une ou plusieurs langues. Des valeurs sont fournies par défaut pour en, de, fr, it, es, ja, zh_CN et ko_KR.
