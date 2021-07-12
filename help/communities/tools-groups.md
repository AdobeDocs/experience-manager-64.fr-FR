---
title: Modèles de groupe
seo-title: Modèles de groupe
description: Accès à la console Modèles de groupe
seo-description: Accès à la console Modèles de groupe
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---

# Modèles de groupe {#group-templates}

La console Modèles de groupe est très similaire à la console [Modèles de site](sites.md) . Il s’agit de plans directeurs pour un ensemble de pages préconfigurées et de fonctionnalités qui forment un site communautaire. La différence est qu’un modèle de site est destiné à la communauté principale et qu’un modèle de groupe est destiné à un groupe de communauté, une sous-communauté imbriquée dans la communauté principale.

Un groupe de communautés est intégré dans un modèle de site en incluant la [fonction Groupes](functions.md#groups-function) (qui ne peut pas être la première fonction ou la seule dans le modèle).

À partir de Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack), il est possible d’imbriquer des groupes en incluant la fonction Groupes dans un modèle de groupe.

Au moment où l’action est entreprise pour créer un nouveau groupe de communautés, le modèle (structure) du groupe est sélectionné. La sélection dépend de la manière dont la fonction Groupes a été configurée lorsqu’elle a été ajoutée au site ou au modèle de groupe.

>[!NOTE]
>
>Les consoles pour la création de [sites de communauté](sites-console.md), [modèles de site de communauté](sites.md), [modèles de groupe de communauté](tools-groups.md) et [fonctions de communauté](functions.md) ne peuvent être utilisées que dans l’environnement de création.

## Console Modèles de groupe {#group-templates-console}

Dans l’environnement de création, pour accéder à la console de modèles de groupes

* À partir de la navigation globale : **[!UICONTROL Outils > Communautés > Modèles de groupe]**

Cette console affiche les modèles à partir desquels un [site communautaire](sites-console.md) peut être créé et permet de créer des modèles de groupe.

![groupradical](assets/groupstemplate.png)

## Créer un modèle de groupe {#create-goup-template}

Pour commencer à créer un modèle de groupe, sélectionnez **[!UICONTROL Créer]**

Le panneau Éditeur de site s’affiche alors et contient trois sous-panneaux :

### Informations de base {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

Dans le panneau Informations de base , un nom, une description et si le modèle est activé ou désactivé sont configurés :

* **[!UICONTROL Nouveau]**
nom de modèle de groupe ID de nom de modèle

* ****
Description : description du modèle.

* **[!UICONTROL Désactivé/]**
activéUn commutateur à bascule contrôlant si le modèle est référencable

### Miniature {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Facultatif) Sélectionnez l’icône Télécharger l’image afin d’afficher une miniature ainsi que le nom et la description pour les créateurs de sites communautaires.

### Structure {#structure}

>[!CAUTION]
>
>Si vous utilisez AEM 6.1 Communities FP4 ou une version antérieure, n’ajoutez pas de fonction de groupe à un modèle de groupe.
>
>La fonction Groupes imbriqués est disponible à partir de Communities [FP1](communities.md#latestfeaturepack).
>
>Il n’est toujours pas autorisé d’ajouter une fonction Groupes comme première ou seule fonction dans un modèle.

![grptemplateeditor](assets/grptemplateeditor.png)

Pour ajouter des fonctions de communauté, faites glisser du côté droit vers la gauche dans l’ordre dans lequel doivent apparaître les liens du menu du site. Des styles seront appliqués au modèle lors de la création du site.

Par exemple, si vous souhaitez un forum, faites glisser la fonction de forum depuis la bibliothèque et déposez-la sous le créateur de modèles. La boîte de dialogue de configuration du forum s’ouvre alors. Voir la [console des fonctions](functions.md) pour plus d’informations sur les boîtes de dialogue de configuration.

Continuez à faire glisser et déposer toutes les autres fonctions de communauté souhaitées pour un site (groupe) de sous-communauté en fonction de ce modèle.

![dragfonctions](assets/dragfunctions.png)

Une fois que toutes les fonctions souhaitées ont été déposées dans la zone du créateur de modèles et configurées, sélectionnez **[!UICONTROL Enregistrer]** dans le coin supérieur droit.

## Modifier le modèle de groupe {#edit-group-template}

Lors de l’affichage de groupes de communautés dans la [console Modèles de groupe](#group-templates-console) principale, il est possible de sélectionner un modèle de groupe existant à modifier.

La modification d’un modèle de groupe n’affecte pas les sites de communauté déjà créés à partir du modèle. Il est possible de modifier directement [la structure d’un site communautaire](sites-console.md#modify-structure) à la place.

Ce processus fournit les mêmes panneaux que la [création d’un modèle de groupe](#create-goup-template).
