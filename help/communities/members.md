---
title: Consoles de gestion des membres et des groupes
seo-title: Members & Groups Management Consoles
description: Accès aux consoles de gestion des membres et des groupes
seo-description: How to access Members and Groups Management consoles
uuid: 2e93e861-a066-4189-91db-f8b784bc5aea
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ccabf301-b417-48aa-8501-8360fd9f3e36
role: Admin
exl-id: 2d0154b3-4cd7-439a-869d-cb116f60b69d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 5%

---

# Consoles de gestion des membres et des groupes {#members-groups-management-consoles}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

Les fonctionnalités AEM Communities nécessitent souvent que les visiteurs du site soient enregistrés et connectés avant de participer à une communauté dans l’environnement de publication. Leur enregistrement d’utilisateur n’a besoin d’exister que dans l’environnement de publication ; il est généralement appelé *members* pour les distinguer de *utilisateurs* enregistré dans l’environnement de création.

### Membres (utilisateurs) sur la publication {#members-users-on-publish}

À l’aide des consoles Membres et groupes des communautés , des membres et des groupes de membres enregistrés dans la variable *publier* peut être créé et géré à partir de l’ *author* environnement. Cela n’est possible que lorsque la variable [service tunnel](deploy-communities.md#tunnel-service-on-author) est activée.

### Utilisateurs sur l’auteur {#users-on-author}

Pour gérer les utilisateurs et les groupes enregistrés dans la variable *author* , est nécessaire pour utiliser la console de sécurité de la plateforme :

* Dans la navigation globale, sélectionnez `Tools, Security, Users`
* Dans la navigation globale, sélectionnez `Tools, Security, Groups`

>[!NOTE]
>
>Avec les exemples de contenu déployés et activés, de nombreux exemples d’utilisateurs existent dans les environnements de création et de publication. Ces utilisateurs ne seront pas présents lors de l’exécution de avec [nosamplecontent runmode](../../help/sites-administering/production-ready.md).

## Console Membres {#members-console}

Dans l’environnement de création, pour accéder à la console Membres afin de gérer les membres enregistrés dans l’environnement de publication :

* À partir de la navigation globale : **[!UICONTROL Navigation > Communautés > Membres]**

>[!CAUTION]
>
>Il ne sera pas possible d’utiliser la console Membres si la variable [service tunnel](deploy-communities.md#tunnel-service-on-author) n’est pas activé.

![chlimage_1-119](assets/chlimage_1-119.png)

### Recherche {#search-features}

Sélectionnez l’icône du panneau latéral sur le côté gauche de la `Members` pour ouvrir le panneau latéral de recherche.

![chlimage_1-120](assets/chlimage_1-120.png) ![chlimage_1-121](assets/chlimage_1-121.png)

Sélectionnez l’icône de recherche sur le côté gauche de la `Members` pour fermer le panneau latéral de recherche.

### Statistiques des membres {#member-statistics}

Les colonnes qui s&#39;affichent `Views`, `Posts`, `Follows`et `Likes` sont mis à jour lorsque l’utilisateur est membre d’un ou de plusieurs sites de la communauté avec Adobe Analytics ; [enabled](sites-console.md#analytics).

### Exporter CSV {#export-csv}

En sélectionnant le `Export CSV` entraîne le téléchargement de tous les membres sous la forme d’une liste de valeurs séparées par des virgules, adaptées à l’importation dans une feuille de calcul.

Les en-têtes de colonne sont :

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Créer un membre {#create-new-member}

Sélectionner `Create Member` afin de créer un utilisateur dans l’environnement de publication.

![chlimage_1-122](assets/chlimage_1-122.png)

### GÉNÉRAL - Détails du membre {#general-member-details}

La plupart des champs sont des champs facultatifs que le membre peut remplir ultérieurement sur son profil.

* **[!UICONTROL ID]**
(
*required*) L’ID autorisable est l’ID de connexion du membre.
Par défaut, l’ID est défini sur la valeur de l’adresse électronique requise.
   *Une fois créé, l&#39;identifiant ne peut plus être modifié.*

* **[!UICONTROL Adresse électronique]**
(
*required*) Adresse électronique du membre.
Le membre peut modifier son adresse email lors de la mise à jour de son profil. Si l&#39;identifiant est l&#39;adresse email par défaut, l&#39;identifiant sera *not* change lorsque l’adresse électronique est modifiée.

* **[!UICONTROL Password]**
(
*required*) Mot de passe de connexion.

* **[!UICONTROL Confirmer le mot de passe]**
(
*required*) Saisissez à nouveau le mot de passe à vérifier.

* **[!UICONTROL Ajouter le membre aux sites]**
(
*facultatif*) Sélectionnez parmi les sites de la communauté existants pour ajouter le membre au groupe de membres du site de la communauté.

* **[!UICONTROL Ajouter un membre aux groupes]**
(
*facultatif*) Effectuez une sélection parmi les groupes de membres existants pour ajouter le membre à ce groupe.

* Sélectionnez **[!UICONTROL Enregistrer]**.

### GÉNÉRAL - Paramètres du compte {#general-account-settings}

Dans les paramètres du compte, un administrateur de communauté peut

* **[!UICONTROL Statut]**
   * Interdit\
      Un membre ne parvient pas à se connecter, ce qui l’empêche d’afficher des pages ou de participer à des activités nécessitant une connexion. Ils peuvent encore visiter anonymement un site communautaire ouvert.

   * Non interdit Un membre a un accès complet au site de la communauté.

   La valeur par défaut est `Not Banned`.

* **[!UICONTROL Limites de contribution]**
Si cette case est cochée, la capacité du membre à publier du contenu est limitée.
La valeur par défaut dépend de la configuration des limites de contribution.
Voir [Limites des contributions des membres](limits.md).

* **[!UICONTROL Modifier le mot de passe]**
Lien présent lors de la modification d’un membre existant. Permet à un administrateur de la communauté de réinitialiser un mot de passe pour un membre.

### GÉNÉRAL - Photo {#general-photo}

Pour fournir un avatar au membre, commencez par sélectionner **[!UICONTROL Télécharger l’image]** et choisissez une image de type .jpg, .png, .tif ou .gif. La taille préférée d’une image est de 240 x 240 pixels à 72 ppp.

### GÉNÉRAL - Ajouter un membre à Sites {#general-add-member-to-sites}

Le membre peut être ajouté à un ou plusieurs groupes de membres de sites de communauté. Saisissez tout d’abord du texte dans la zone de texte.

### GÉNÉRAL - Ajouter un membre aux groupes {#general-add-member-to-groups}

Le membre peut être ajouté à un ou plusieurs groupes de membres. Saisissez tout d’abord du texte dans la zone de texte.

### Onglet BADGES {#badges-tab}

Le `BADGES` panneau permet d’attribuer manuellement des badges et de les révoquer. Les badges peuvent être pour les rôles attribués ainsi que pour les badges généralement gagnés.

Voir aussi [Notation et badges](implementing-scoring.md).

![chlimage_1-123](assets/chlimage_1-123.png)

* **[!UICONTROL Ajouter des badges]**
   * Commencer à saisir pour effectuer une sélection dans [badges disponibles](badges.md). Une fois qu’un badge est sélectionné, sélectionnez chaque site, ou tous les sites, sur lesquels le badge doit s’afficher avec l’avatar du membre.
   * Plusieurs badges et sites peuvent être choisis.
* **[!UICONTROL Suppression des badges]**
   * Sélectionnez l’icône de corbeille en regard d’un badge pour le supprimer.

## Console Groupes {#groups-console}

La console Groupes , disponible dans l’environnement de création, permet la création et la gestion des groupes de membres enregistrés dans l’environnement de publication. Elle est particulièrement utile pour :
* [Groupes de membres privilégiés](users.md#privilegedmembersgroups)
* Affectation basée sur un groupe de [ressources d&#39;activation](resources.md)

Pour accéder à la console Groupes , procédez comme suit :
* À partir de la navigation globale : **[!UICONTROL Navigation > Communautés > Groupes]**

>[!CAUTION]
>
>Il ne sera pas possible d’utiliser la console Groupes si la variable [service tunnel](deploy-communities.md#tunnel-service-on-author) n’est pas activé.

### Créer un groupe {#create-new-group}

Sélectionner `Add Group` afin de créer un groupe dans l’environnement de publication.

![chlimage_1-124](assets/chlimage_1-124.png)

Les champs requis pour créer un groupe de membres côté publication sont les suivants :

* **[!UICONTROL ID]**
(
*required*) Identifiant unique du groupe.
   *Une fois créé, l&#39;identifiant ne peut plus être modifié.*

* **[!UICONTROL Nom]**
(
*facultatif*) Nom d’affichage du groupe.

   La valeur par défaut est l’ID.

* **[!UICONTROL Description]**
(
*facultatif*) Description de l’objectif et des autorisations du groupe.

* **[!UICONTROL Ajouter des membres au groupe]**
(
*facultatif*) Sélectionnez les membres côté publication à inclure en tant que membres initiaux du groupe.

* Sélectionnez **[!UICONTROL Enregistrer]**.

## Administrateurs autorisés {#authorized-administrators}

Lorsque vous travaillez avec des membres dans la console des membres de Communities, il est nécessaire de se connecter en tant qu’utilisateur avec les autorisations appropriées, ainsi que pour l’agent de réplication utilisé par la fonction [service tunnel](deploy-communities.md#tunnel-service-on-author) pour être correctement configurés.

Si vous n’êtes pas connecté en tant que `admin`, l’utilisateur connecté doit être membre du `administrators` groupe d’utilisateurs.

Voir aussi [Agents de réplication sur l’auteur](deploy-communities.md#replication-agents-on-author).
