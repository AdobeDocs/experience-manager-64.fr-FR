---
title: Console Badges
seo-title: Badges Console
description: La console Badges de communauté vous permet d’ajouter des badges personnalisés qui peuvent être affichés pour les membres lorsqu’ils sont gagnés (attribués) ou lorsqu’ils assument un rôle spécifique dans la communauté (affecté).
seo-description: The Communities Badges console lets you add custom badges that can be displayed for members when earned (awarded) or when they take on a specific role in the community (assigned)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Admin
exl-id: b6aa9d73-4e20-446a-a1fc-78f8968d6844
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 7%

---

# Console Badges {#badges-console}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## A propos des badges {#about-badges}

La console Badges de communauté permet d’ajouter des badges personnalisés qui peuvent être affichés pour un membre lorsqu’il est gagné (attribué) ou lorsqu’il occupe un rôle spécifique dans la communauté (affecté).

### Visibilité du badge {#badge-visibility}

Actuellement, les badges qu’un membre de la communauté gagne ou se voit attribuer s’affichent avec son nom et son avatar aux emplacements suivants :

* Profils
* [Forums](forum.md)
* [Q&amp;R](working-with-qna.md)
* [Tableaux de bord](enabling-leaderboard.md)
* [Conceptualisation](ideation-feature.md)

Dans l’environnement de création, pour accéder à la console Badges

* À partir de la navigation globale : **[!UICONTROL Outils > Communautés > Badges]**

Cette console affiche les badges actuellement disponibles et à partir desquels de nouveaux badges peuvent être ajoutés.

![chlimage_1-242](assets/chlimage_1-242.png)

## Créer le badge {#create-badge}

Un badge est créé en téléchargeant une image de petite taille (72 dpi avec une hauteur comprise entre 26 et 32 pixels) et en fournissant un nom. L’image de badge est stockée dans le référentiel à l’adresse `/etc/community/badging/images` et est automatiquement répliqué dans l’environnement de publication.

Si l’environnement de publication est une ferme d’éditeurs, il est nécessaire de configurer [synchronisation des utilisateurs](sync.md).

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Charger l’image]**

   (*Obligatoire*) Une image de badge d’une taille recommandée de 32 x 32 pixels à 72 ppp au format JPEG ou PNG.

* **[!UICONTROL Nom]**

   (*Obligatoire*) Nom du badge. Il s’agit de la valeur par défaut `Display Name` ainsi que le nom du noeud de référentiel. Si la variable `Name` n’est pas un nom de noeud de référentiel valide, il sera modifié.

* **[!UICONTROL Nom d’affichage]**

   (*Facultatif*) Nom à afficher pour le badge dans l’interface utilisateur. La valeur par défaut est le texte non modifié saisi pour la variable `Name`.

* **[!UICONTROL Description]**

   (*Facultatif*) Description du badge.

## Informations supplémentaires {#additional-information}

Pour plus d’informations sur la configuration des règles de notation et de badge, voir [Notation et badges](implementing-scoring.md).

Pour la gestion des badges pour les membres, voir [Console Membres](members.md).
