---
title: Modèles de site
seo-title: Site Templates
description: Accès à la console Modèles de site
seo-description: How to access the Site Templates console
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
role: Admin
exl-id: 5049c5df-c874-4c34-a96b-7944cd0353d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 5%

---

# Modèles de site {#site-templates}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La console Modèles de site est très similaire au [Modèles de groupe](tools-groups.md) console, qui est axée sur des fonctions présentant un intérêt pour les groupes communautaires.

>[!NOTE]
>
>Les consoles pour la création de [sites communautaires](sites-console.md), [modèles de site de communauté](sites.md), [modèles de groupe de communautés](tools-groups.md) et [fonctions de communauté](functions.md) sont utilisables uniquement dans l’environnement de création.

## Console Modèles de site {#site-templates-console}

Dans l’environnement de création, pour accéder à la console des sites de la communauté

* À partir de la navigation globale : **[!UICONTROL Outils > Communautés > Modèles de site]**

Cette console affiche les modèles à partir desquels une [site communautaire](sites-console.md) peut être créé et permet de créer des modèles de site.

![chlimage_1-18](assets/chlimage_1-18.png)

## Créer un modèle de site {#create-site-template}

Pour commencer à créer un modèle de site, sélectionnez `Create`.

Le panneau Éditeur de site s’affiche alors et contient trois sous-panneaux :

### Informations de base {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

Dans le panneau Informations de base , un nom, une description et si le modèle est activé ou désactivé sont configurés :

* **[!UICONTROL Nom du modèle de site de la communauté]**
ID du nom du modèle

* **[!UICONTROL Description du modèle de site de communauté]**
Description du modèle

* **[!UICONTROL Désactivé/activé]**
Bouton de basculement contrôlant si le modèle est référencable

### Miniature {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

(Facultatif) Sélectionnez l’icône Télécharger l’image afin d’afficher une miniature ainsi que le nom et la description des créateurs des sites de la communauté.

### Structure {#structure}

![chlimage_1-21](assets/chlimage_1-21.png)

Pour ajouter des fonctions de communauté, faites glisser du côté droit vers la gauche dans l’ordre dans lequel doivent apparaître les liens du menu du site. Des styles seront appliqués au modèle lors de la création du site.

Par exemple, si vous souhaitez une page d’accueil, faites glisser la fonction Page de la bibliothèque et déposez-la sous le créateur de modèles. La boîte de dialogue de configuration de la page s’ouvre alors. Voir [console fonctions](functions.md) pour plus d’informations sur les boîtes de dialogue de configuration.

Continuez à faire glisser et déposer toutes les autres fonctions de la communauté souhaitées pour un site de la communauté en fonction de ce modèle.

La fonction page fournit une page vide. La fonction de groupes permet de créer un site de groupe (sous-communauté) au sein du site de la communauté.

>[!CAUTION]
>
>La fonction groups doit *not* be *first ni unique* dans la structure du site.
>
>Toute autre fonction, telle que [fonction de page](functions.md#page-function), doit être inclus et répertorié en premier.

![chlimage_1-22](assets/chlimage_1-22.png)

### Modèles de groupe pour la fonction Groupes {#group-templates-for-groups-function}

Lors de l’inclusion d’une fonction de groupe dans le modèle de site, la configuration nécessite la spécification des choix de modèle de groupe autorisés lorsqu’un nouveau groupe est créé dans l’environnement de publication.

>[!CAUTION]
>
>La fonction Groups doit *not* be *first ni unique* dans la structure du site.

![chlimage_1-23](assets/chlimage_1-23.png)

En sélectionnant plusieurs modèles de groupe de communauté, l’administrateur du groupe a le choix de créer un nouveau groupe dans la communauté.

![chlimage_1-24](assets/chlimage_1-24.png)

## Modifier le modèle de site {#edit-site-template}

Lors de l’affichage des modèles de site dans l’élément principal [Console Modèles de site](#site-templates-console), il est possible de sélectionner un modèle de site existant à modifier.

Ce processus fournit les mêmes panneaux que [création d’un modèle de site](#create-site-template).
