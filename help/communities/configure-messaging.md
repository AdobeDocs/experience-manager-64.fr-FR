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
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 29%

---


# Fonction de messagerie {#messaging-feature}

Outre les interactions visibles par le public qui se produisent dans les forums et les commentaires, la fonction de messagerie d&#39;AEM Communities permet aux membres de la communauté d&#39;interagir entre eux de manière plus privée.

This feature may be included when a [community site](overview.md#communitiessites) is created.

La fonction de messagerie permet :

* Envoyer un message à un ou plusieurs membres de la communauté
* Envoyer un message à un groupe de membres de la communauté
* Envoyer un message avec des pièces jointes
* Transférer un message
* Réponse à un message
* Suppression d’un message
* Restaurer un message supprimé

Pour activer et modifier la fonction de messagerie, visitez

* [Configuration de la messagerie](messaging.md) pour les administrateurs
* [Messaging Essentials](essentials-messaging.md) pour les développeurs

>[!NOTE]
>
>Il n’est pas pris en charge d’ajouter `Compose Message, Message, or Message List` des composants (figurant dans le groupe de `Communities`composants) à une page en mode d’édition Auteur.

## Configuration des composants de messagerie {#configuring-messaging-components}

Lorsque la messagerie est activée pour un site communautaire, elle est complètement configurée sans autre configuration nécessaire. Ces informations sont fournies s’il est nécessaire de modifier la configuration par défaut.

### Configuration de la Liste de messages (boîte de message) {#configuring-message-list-messagebox}

Afin de modifier la configuration de la liste des messages pour la boîte de **réception**, les éléments **** envoyés et les pages **de corbeille** de la fonction de messagerie, ouvrez le site en mode d&#39;édition [auteur.](sites-console.md#authoring-site-content)

En `Preview` mode, sélectionnez le lien **[!UICONTROL Messages]** pour ouvrir la page de messagerie principale. Sélectionnez ensuite **[!UICONTROL Boîte de réception, Éléments envoyés ou Corbeille]** pour configurer le composant pour cette liste de messages.

En `Edit` mode, sélectionnez le composant sur la page.

Pour accéder à la boîte de dialogue de configuration, il est nécessaire d&#39;annuler l&#39;héritage en sélectionnant l&#39; `link`icône .

Une fois la configuration terminée, il est nécessaire de restaurer l&#39;héritage en sélectionnant l&#39; `broken link` icône.

![chlimage_1-396](assets/chlimage_1-396.png)

Une fois l&#39;héritage annulé, il sera possible de sélectionner l&#39; `configure` icône pour ouvrir la boîte de dialogue de configuration.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Basic tab {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Sélecteur]** de service (*Obligatoire*) Définissez cette valeur sur la valeur de la propriété `serviceSelector.name` du service [de messagerie](messaging.md#messaging-operations-service)AEM Communities.

* **[!UICONTROL Composer la page]**(*Obligatoire*) La page à ouvrir lorsqu&#39;un membre clique sur le `Reply` bouton. La page cible devrait contenir le formulaire **[!UICONTROL Composer le message.]**

* **[!UICONTROL Répondre/Afficher en tant que ressource]** Si vous cochez cette case, les URL de réponse et d’affichage font référence à une ressource. Dans le cas contraire, les données sont transmises sous forme de paramètres de requête dans l’URL. 

* **[!UICONTROL Formulaire d’affichage du profil]** Formulaire de profil à utiliser pour afficher le profil de l’expéditeur.

* **[!UICONTROL Dossier Corbeille]** Si vous cochez cette case, ce composant Liste des messages affiche uniquement les messages marqués comme supprimés (corbeille).

* **[!UICONTROL Chemins]** des dossiers (*Obligatoire*) Référençant les valeurs définies pour `inbox.path.name` et `sentitems.path.name` dans le service [d&#39;opérations de messagerie](messaging.md#messaging-operations-service)AEM Communities. Lors de la configuration d’une `Inbox`entrée, ajoutez une entrée en utilisant la valeur de `inbox.path.name`. Lors de la configuration d’une `Outbox`entrée, ajoutez une entrée en utilisant la valeur de `sentitems.path.name`. Lors de la configuration pour `Trash`, ajoutez deux entrées avec les deux valeurs.

#### Onglet Affichage {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Marquer le bouton]** Lecture Si coché, affiche un 
`Read`permettant de marquer un message comme lu.

* **[!UICONTROL Marquer le bouton]** Non lu Si coché, affiche un 
`Mark Unread` permettant de marquer un message comme lu.

* **[!UICONTROL Bouton]** Supprimer Si coché, affiche un 
`Delete`permettant de marquer un message comme lu. Will duplicate the delete functionality if **`Message Options`** is also checked.

* **[!UICONTROL Options]** de message Si cette case est cochée, affiche 
**`Reply`**, **`Reply All`**, **`Forward`** et **`Delete`** les boutons permettant de renvoyer ou de supprimer un message. Will duplicate the delete functionality if **`Delete Button`** is also checked.

* **[!UICONTROL Messages par page]** Le nombre spécifié est le nombre maximal de messages affichés par page dans le modèle de pagination. Si aucun chiffre n’est spécifié (si vous laissez le champ vide), tous les messages s’affichent sans pagination.

* **[!UICONTROL Modèles d’horodatage]** Indiquez des modèles d’horodatage pour une ou plusieurs langues. Des valeurs sont fournies par défaut pour en, de, fr, it, es, ja, zh_CN et ko_KR.

* **[!UICONTROL Afficher l’utilisateur]** Choisir 
**`Sender`** ou **`Recipients`** pour déterminer s&#39;il faut afficher l&#39;expéditeur ou les Destinataires.

### Configuration d&#39;un message de composition {#configuring-compose-message}

Pour modifier la configuration de la page de composition du message, ouvrez le site en mode [d’édition](sites-console.md#authoring-site-content)auteur.

En `Preview`mode, sélectionnez le lien **[!UICONTROL Messages]** pour ouvrir la page de messagerie principale. Sélectionnez ensuite le bouton Nouveau message pour ouvrir la `Compose Message` page.

En `Edit` mode, sélectionnez le composant principal sur la page contenant le corps du message.

Pour accéder à la boîte de dialogue de configuration, il est nécessaire d&#39;annuler l&#39;héritage en sélectionnant l&#39; `link`icône .

Une fois la configuration terminée, il est nécessaire de restaurer l&#39;héritage en sélectionnant l&#39; `broken link` icône.

![chlimage_1-400](assets/chlimage_1-400.png)

Une fois l&#39;héritage annulé, il sera possible de sélectionner l&#39; `configure` icône pour ouvrir la boîte de dialogue de configuration.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Basic tab {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL URL de redirection]** Saisissez l’URL de la page affichée une fois le message envoyé. Par exemple : 
`../messaging.html`.

* **[!UICONTROL Annuler l’URL]** Saisissez l’URL de la page affichée si l’expéditeur annule le message. Par exemple : 
`../messaging.html`.

* **[!UICONTROL Longueur maximale de l’objet du message]** Nombre maximal de caractères autorisé dans le champ Objet. Par exemple, 500. La valeur par défaut n’est pas une limite.

* **[!UICONTROL Longueur maximale du corps du message]** Nombre maximal de caractères autorisé dans le champ Contenu. Par exemple, 10000. La valeur par défaut n’est pas une limite.

* **[!UICONTROL Sélecteur]** de service (*Obligatoire*) Définissez cette valeur sur la valeur de la propriété **`serviceSelector.name`** du service [de messagerie](messaging.md#messaging-operations-service)AEM Communities.

#### Onglet Affichage {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Afficher le champ]** Objet Si cette case est cochée, afficher la variable 
`Subject` et activez l’ajout d’un objet au message. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Libellé]** du sujet Entrez le texte à afficher en regard de 
`Subject` field. La valeur par défaut est `Subject`.

* **[!UICONTROL Afficher le champ]** Joindre le fichier Si coché, affichez le 
`Attachment` et activez l’ajout de pièces jointes au message. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Joindre le libellé]** du fichier Entrez le texte à afficher en regard de 
`Attachment` field. La valeur par défaut est **`Attach File`**.

* **[!UICONTROL Afficher le champ]** de contenu Si cette case est cochée, afficher la variable 
`Content` et activez l’ajout d’un corps de message. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Libellé]** du contenu Entrez le texte à afficher en regard de 
`Content` field. La valeur par défaut est **`Body`**.

* **[!UICONTROL Avec l’éditeur de texte enrichi]** Si vous cochez cette case, une zone de texte personnalisée Contenu est utilisée avec son propre éditeur de texte enrichi. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Modèles d’horodatage]** Indiquez des modèles d’horodatage pour une ou plusieurs langues. Des valeurs sont fournies par défaut pour en, de, fr, it, es, ja, zh_CN et ko_KR.

