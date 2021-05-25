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
exl-id: 4b663228-9cb6-45c0-99dd-8dd7fc2aa4a6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 48%

---

# Groupes communautaires {#community-groups}

La fonctionnalité de groupes de communautés permet à une sous-communauté d’être créée dynamiquement dans un site de communauté par des utilisateurs autorisés (membres de la communauté et auteurs) à partir des environnements de publication et de création.

Cette fonctionnalité est présente lorsque la fonction [groups](functions.md#groups-function) est présente dans la structure [site communautaire](sites-console.md).

Un [modèle de groupe de communautés](tools-groups.md) fournit la conception de la page de groupe de communautés lorsqu’un groupe de communautés est créé dynamiquement.

Un ou plusieurs modèles de groupe sont sélectionnés pour la fonction de groupes lorsque la fonction est ajoutée à la structure d’un site de communauté ou à un modèle de site de communauté. Cette liste de modèles de groupe est présentée au membre ou à l’auteur qui crée dynamiquement un nouveau groupe sur le site de la communauté.

## Création d’un nouveau groupe {#creating-a-new-group}

La possibilité de créer un groupe de communautés dépend de l’existence d’un site de communauté qui inclut la fonction de groupes, comme un site créé à partir de ` [Reference Site Template](sites.md)`.

Les exemples qui suivent utilisent le site de la communauté créé à partir de `Reference Site Template` comme décrit dans le tutoriel [Prise en main d’AEM Communities](getting-started.md) .

Il s’agit de la page qui se charge lors de la publication lorsque l’option de menu **[!UICONTROL Groupes]** est sélectionnée :

![chlimage_1-236](assets/chlimage_1-236.png)

Lorsque vous sélectionnez l’icône **[!UICONTROL Nouveau groupe]**, une boîte de dialogue de modification s’ouvre.

Dans l’onglet **[!UICONTROL Paramètres]**, spécifiez les fonctionnalités de base du groupe :

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Nom de groupe]** Le titre du groupe à afficher sur le site de la communauté.

* **[!UICONTROL Description]** Une description du groupe à afficher sur le site de la communauté.

* **[!UICONTROL Invitation]** Une liste de membres à inviter au groupe. La recherche par saisie anticipée suggère des membres de la communauté à inviter.

* **[!UICONTROL Nom de l’URL de groupe]** Le nom de la page de groupe qui est intégré à l’URL.

* **[!UICONTROL Ouvrir]**
la sélection de groupe 
`Open Group` indique que tout visiteur anonyme du site peut afficher le contenu et le désélectionner  `Member Only Group`.

* **[!UICONTROL Member Only]**
GroupSelecting 
`Member Only Group` indique que seuls les membres du groupe peuvent afficher le contenu et se désélectionner  `Open Group`.

Sous l’onglet **[!UICONTROL Modèle]**, vous pouvez sélectionner dans la liste des modèles de groupe de communautés qui ont été spécifiés lorsque la fonction de groupes a été incluse dans la structure du site de la communauté ou dans un modèle de site de la communauté.

![chlimage_1-238](assets/chlimage_1-238.png)

L’onglet **[!UICONTROL Image]** permet de transférer une image à afficher pour le groupe sur la page Groupes du site de la communauté. La feuille de style par défaut dimensionne l’image à 170 x 90 pixels.

![chlimage_1-239](assets/chlimage_1-239.png)

Lorsque le bouton **[!UICONTROL Créer un groupe]** est sélectionné, les pages du groupe sont créées selon le modèle sélectionné, un groupe d’utilisateurs est créé pour l’abonnement et la page Groupes est mise à jour pour afficher la nouvelle sous-communauté.

Par exemple, la page Groupes comportant une nouvelle sous-communauté nommée « Groupe d’orientation », pour laquelle une miniature a été transférée, a l’apparence suivante (l’utilisateur étant encore connecté en tant qu’administrateur de groupe de communautés) :

![chlimage_1-240](assets/chlimage_1-240.png)

Si vous sélectionnez le lien `Focus Group`, la page Groupe d’orientation s’ouvre dans le navigateur. Celui-ci a une apparence initiale basée sur le modèle sélectionné et comprend un sous-menu sous le menu du site de la communauté principale :

![chlimage_1-241](assets/chlimage_1-241.png)

## Composant Liste des membres de groupes de communautés {#community-group-member-list-component}

Le composant `Community Group Member List` est destiné aux développeurs de modèles de groupe.

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur les groupes communautaires](essentials-groups.md) pour les développeurs.

Pour plus d’informations sur les groupes de communautés, voir [Gestion des utilisateurs et des groupes d’utilisateurs](users.md).
