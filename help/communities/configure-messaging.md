---
title: Fonction de messagerie
seo-title: Messaging Feature
description: Configuration des composants de messagerie
seo-description: Configuring Messaging components
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 3%

---

# Fonction de messagerie {#messaging-feature}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Outre les interactions publiques qui se produisent dans les forums et les commentaires, la fonction de messagerie d’AEM Communities permet aux membres de la communauté d’interagir de manière plus privée.

Cette fonctionnalité peut être incluse lors d’une [site communautaire](overview.md#communitiessites) est créée.

Les fonctionnalités de messagerie permettent d’effectuer les opérations suivantes :

* Envoyer un message à un ou plusieurs membres de la communauté
* Envoyer un message à un groupe de membres de la communauté
* Envoi d’un message avec des pièces jointes
* Transférer un message
* Répondre à un message
* Supprimer un message
* Restaurer un message supprimé

Pour activer et modifier la fonction de messagerie, consultez la page

* [Configuration de la messagerie](messaging.md) pour les administrateurs
* [Notions fondamentales sur la messagerie](essentials-messaging.md) pour les développeurs

>[!NOTE]
>
>L’ajout de n’est pas pris en charge. `Compose Message, Message, or Message List` composants (disponibles dans `Communities`groupe de composants) à une page en mode d’édition de création.

## Configuration des composants de messagerie {#configuring-messaging-components}

Lorsque la messagerie est activée pour un site de la communauté, elle est entièrement configurée sans autre configuration nécessaire. Ces informations sont fournies s’il est nécessaire de modifier la configuration par défaut.

### Configuration de la liste des messages (messagebox) {#configuring-message-list-messagebox}

Afin de modifier le paramétrage de la liste des messages pour **Boîte de réception**, **Éléments envoyés**, et **Corbeille** des pages de la fonction de messagerie, ouvrez le site dans [mode d’édition de l’auteur](sites-console.md#authoring-site-content).

Dans `Preview` , sélectionnez **[!UICONTROL Messages]** pour ouvrir la page principale de messagerie. Sélectionnez ensuite l’une des options suivantes : **[!UICONTROL Boîte de réception, éléments envoyés ou corbeille]** afin de configurer le composant pour cette liste de messages.

Dans `Edit` , sélectionnez le composant sur la page.

Pour accéder à la boîte de dialogue de configuration, il est nécessaire d’annuler l’héritage en sélectionnant le `link`icône .

Une fois la configuration terminée, il est nécessaire de restaurer l’héritage en sélectionnant l’option `broken link` icône .

![chlimage_1-396](assets/chlimage_1-396.png)

Une fois l’héritage annulé, il sera possible de sélectionner la variable `configure` pour ouvrir la boîte de dialogue de configuration.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Onglet De base {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Sélecteur de service]**
(*Obligatoire*) Définissez cette variable sur la valeur de la propriété . `serviceSelector.name` de la [Service des opérations de messagerie AEM Communities](messaging.md#messaging-operations-service).

* **[!UICONTROL Composer la page]**
(*Obligatoire*) La page à ouvrir lorsqu’un membre clique sur le bouton `Reply` bouton . La page cible doit contenir le **[!UICONTROL Composer le message]** formulaire.

* **[!UICONTROL Réponse/Afficher comme ressource]**
Si cette case est cochée, l’URL de réponse et l’URL de vue font référence à une ressource ; dans le cas contraire, les données sont transmises en tant que paramètres de requête dans l’URL.

* **[!UICONTROL Formulaire d’affichage de profil]**
Formulaire de profil à utiliser pour afficher le profil des expéditeurs.

* **[!UICONTROL Dossier de la corbeille]**
Si cette case est cochée, ce composant Liste de messages affiche uniquement les messages marqués comme supprimés (corbeille).

* **[!UICONTROL Chemins du dossier]**
(*Obligatoire*) en référençant les valeurs définies pour `inbox.path.name` et `sentitems.path.name` dans le [Service des opérations de messagerie AEM Communities](messaging.md#messaging-operations-service). Lors de la configuration d’une `Inbox`, ajoutez une entrée à l’aide de la valeur de `inbox.path.name`. Lors de la configuration d’une `Outbox`, ajoutez une entrée à l’aide de la valeur de `sentitems.path.name`. Lors de la configuration de pour `Trash`, ajoutez deux entrées avec les deux valeurs.

#### Onglet Affichage {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Bouton Marquer la lecture]**
Si cette case est cochée, une 
`Read`permettant de marquer un message comme lu.

* **[!UICONTROL Bouton Marquer comme non lu]**
Si cette case est cochée, une 
`Mark Unread` permettant de marquer un message comme lu.

* **[!UICONTROL Bouton Supprimer]**
Si cette case est cochée, une 
`Delete`permettant de marquer un message comme lu. La fonction de suppression est-elle dupliquée si **`Message Options`** est également cochée.

* **[!UICONTROL Options de message]**
Si cette case est cochée, s’affiche. 
**`Reply`**, **`Reply All`**, **`Forward`** et **`Delete`** des boutons permettant de renvoyer ou de supprimer un message. La fonction de suppression est-elle dupliquée si **`Delete Button`** est également cochée.

* **[!UICONTROL Messages par page]**
Le nombre spécifié est le nombre maximal de messages affichés par page dans un modèle de pagination. Si aucun nombre n’est spécifié (laissez le champ vide), tous les messages sont affichés et il n’y a pas de pagination.

* **[!UICONTROL Modèles d’horodatage]**
Fournir des modèles d’horodatage pour une ou plusieurs langues. La valeur par défaut est en, de, fr, it, es, ja, zh_CN, ko_KR.

* **[!UICONTROL Afficher l’utilisateur]**
Choisissez l’une 
**`Sender`** ou **`Recipients`** pour déterminer s&#39;il faut afficher l&#39;expéditeur ou les destinataires.

### Configuration d’un message de composition {#configuring-compose-message}

Pour modifier la configuration de la page de composition de messages, ouvrez le site dans [mode d’édition de l’auteur](sites-console.md#authoring-site-content).

Dans `Preview`, sélectionnez **[!UICONTROL Messages]** pour ouvrir la page principale de messagerie. Sélectionnez ensuite le bouton Nouveau message pour ouvrir le `Compose Message` page..

Dans `Edit` , sélectionnez le composant principal sur la page contenant le corps du message.

Pour accéder à la boîte de dialogue de configuration, il est nécessaire d’annuler l’héritage en sélectionnant le `link`icône .

Une fois la configuration terminée, il est nécessaire de restaurer l’héritage en sélectionnant l’option `broken link` icône .

![chlimage_1-400](assets/chlimage_1-400.png)

Une fois l’héritage annulé, il sera possible de sélectionner la variable `configure` pour ouvrir la boîte de dialogue de configuration.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Onglet De base {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL URL de redirection]**
Saisissez l&#39;URL de la page affichée après l&#39;envoi du message. Par exemple, 
`../messaging.html`.

* **[!UICONTROL Annuler l’URL]**
Saisissez l&#39;URL de la page affichée si l&#39;expéditeur annule le message. Par exemple, 
`../messaging.html`.

* **[!UICONTROL Longueur maximale de l’objet du message]**
Nombre maximal de caractères autorisés dans le champ Objet. Par exemple, 500. La valeur par défaut n’est pas limitée.

* **[!UICONTROL Longueur maximale du corps du message]**
Nombre maximal de caractères autorisés dans le champ Contenu . Par exemple, 10 000. La valeur par défaut n’est pas limitée.

* **[!UICONTROL Sélecteur de service]**
(*Obligatoire*) Définissez cette variable sur la valeur de la propriété . **`serviceSelector.name`** de la [Service des opérations de messagerie AEM Communities](messaging.md#messaging-operations-service).

#### Onglet Affichage {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Afficher le champ d’objet]**
Si cette case est cochée, le 
`Subject` et activer l’ajout d’un objet au message. La valeur par défaut n’est pas cochée.

* **[!UICONTROL Libellé du sujet]**
Saisissez le texte à afficher en regard de l’option 
`Subject` field. La valeur par défaut est `Subject`.

* **[!UICONTROL Afficher le champ de fichier joint]**
Si cette case est cochée, le 
`Attachment` et activer l’ajout de pièces jointes au message. La valeur par défaut n’est pas cochée.

* **[!UICONTROL Joindre l’étiquette du fichier]**
Saisissez le texte à afficher en regard de l’option 
`Attachment` field. La valeur par défaut est **`Attach File`**.

* **[!UICONTROL Afficher le champ de contenu]**
Si cette case est cochée, le 
`Content` et activer l’ajout d’un corps de message. La valeur par défaut n’est pas cochée.

* **[!UICONTROL Libellé de contenu]**
Saisissez le texte à afficher en regard de l’option 
`Content` field. La valeur par défaut est **`Body`**.

* **[!UICONTROL Avec l’éditeur de texte enrichi]**
Si cette case est cochée, elle indique l’utilisation d’une zone de texte de contenu personnalisée avec son propre éditeur de texte enrichi. La valeur par défaut n’est pas cochée.

* **[!UICONTROL Modèles d’horodatage]**
Fournir des modèles d’horodatage pour une ou plusieurs langues. La valeur par défaut est en, de, fr, it, es, ja, zh_CN, ko_KR.
