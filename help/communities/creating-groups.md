---
title: Groupes communautaires
seo-title: Groupes communautaires
description: Création de groupes communautaires
seo-description: Création de groupes communautaires
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 48%

---


# Groupes communautaires {#community-groups}

La fonction des groupes communautaires permet à une sous-communauté d’être créée dynamiquement dans un site communautaire par des utilisateurs autorisés (membres de la communauté et auteurs) à partir des environnements de publication et d’auteur.

Cette capacité est présente lorsque la fonction [groupes ](functions.md#groups-function) est présente dans la structure [site communautaire](sites-console.md).

Un [modèle de groupe de communauté](tools-groups.md) fournit la conception de la page de groupe de communauté lorsqu’un groupe de communauté est créé de manière dynamique.

Un ou plusieurs modèles de groupe sont sélectionnés pour la fonction de groupes lorsque la fonction est ajoutée à la structure d’un site de communauté ou à un modèle de site de communauté. Cette liste de modèles de groupe est présentée au membre ou à l’auteur qui crée dynamiquement un nouveau groupe sur le site de la communauté.

## Création d’un nouveau groupe {#creating-a-new-group}

La possibilité de créer un nouveau groupe communautaire repose sur l&#39;existence d&#39;un site communautaire qui inclut la fonction de groupes, comme celui créé à partir du ` [Reference Site Template](sites.md)`.

Les exemples suivants utilisent le site communautaire créé à partir du `Reference Site Template` comme décrit dans le didacticiel [Prise en main de AEM Communities](getting-started.md).

Page chargée lors de la publication lorsque l&#39;option de menu **[!UICONTROL Groupes]** est sélectionnée :

![chlimage_1-236](assets/chlimage_1-236.png)

Lorsque vous sélectionnez l’icône **[!UICONTROL Nouveau groupe]**, une boîte de dialogue de modification s’ouvre.

Dans l’onglet **[!UICONTROL Paramètres]**, spécifiez les fonctionnalités de base du groupe :

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Nom de groupe]** Le titre du groupe à afficher sur le site de la communauté.

* **[!UICONTROL Description]** Une description du groupe à afficher sur le site de la communauté.

* **[!UICONTROL Invitation]** Une liste de membres à inviter au groupe. La recherche par saisie anticipée suggère des membres de la communauté à inviter.

* **[!UICONTROL Nom de l’URL de groupe]** Le nom de la page de groupe qui est intégré à l’URL.

* **[!UICONTROL Ouvrir]**
GroupeSélection 
`Open Group` indique que tout visiteur de site anonyme peut vue le contenu et se désélectionne  `Member Only Group`.

* **[!UICONTROL Membre uniquement]**
GroupeSélection 
`Member Only Group` indique que seuls les membres du groupe peuvent vue le contenu et se désélectionne  `Open Group`.

Sous l&#39;onglet **[!UICONTROL Modèle]** se trouve la possibilité de sélectionner dans la liste des modèles de groupes de la communauté qui ont été spécifiés lorsque la fonction de groupes a été incluse dans la structure du site de la communauté ou dans un modèle de site de la communauté.

![chlimage_1-238](assets/chlimage_1-238.png)

L’onglet **[!UICONTROL Image]** permet de transférer une image à afficher pour le groupe sur la page Groupes du site de la communauté. La feuille de style par défaut dimensionne l’image à 170 x 90 pixels.

![chlimage_1-239](assets/chlimage_1-239.png)

Lorsque le bouton **[!UICONTROL Créer un groupe]** est sélectionné, les pages du groupe sont créées selon le modèle sélectionné, un groupe d’utilisateurs est créé pour l’abonnement et la page Groupes est mise à jour pour afficher la nouvelle sous-communauté.

Par exemple, la page Groupes comportant une nouvelle sous-communauté nommée « Groupe d’orientation », pour laquelle une miniature a été transférée, a l’apparence suivante (l’utilisateur étant encore connecté en tant qu’administrateur de groupe de communautés) :

![chlimage_1-240](assets/chlimage_1-240.png)

La sélection du lien `Focus Group` permet d&#39;ouvrir la page Groupe de discussion dans le navigateur, qui présente un aspect initial en fonction du modèle choisi et comporte un sous-menu sous le menu principal du site communautaire :

![chlimage_1-241](assets/chlimage_1-241.png)

## Composant Liste des membres de groupes de communautés {#community-group-member-list-component}

Le composant `Community Group Member List` est destiné aux développeurs de modèles de groupe.

## Informations supplémentaires {#additional-information}

Pour plus d&#39;informations, consultez la page [Community Group Essentials](essentials-groups.md) destinée aux développeurs.

Pour obtenir d&#39;autres informations sur les groupes communautaires, consultez [Gestion des utilisateurs et des groupes d&#39;utilisateurs](users.md).
