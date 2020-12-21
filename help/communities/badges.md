---
title: Console de badges
seo-title: Console de badges
description: La console Badges de communautés vous permet d'ajouter des badges personnalisés qui peuvent être affichés pour les membres lorsqu'ils sont gagnés (attribués) ou lorsqu'ils assument un rôle spécifique dans la communauté (affectés).
seo-description: La console Badges de communautés vous permet d'ajouter des badges personnalisés qui peuvent être affichés pour les membres lorsqu'ils sont gagnés (attribués) ou lorsqu'ils assument un rôle spécifique dans la communauté (affectés).
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 5%

---


# Console Badges {#badges-console}

## À propos des badges {#about-badges}

La console Badges communautaires permet d&#39;ajouter des badges personnalisés qui peuvent être affichés pour un membre lorsqu&#39;il est gagné (attribué) ou lorsqu&#39;il assume un rôle spécifique dans la communauté (attribué).

### Visibilité du badge {#badge-visibility}

Actuellement, les badges gagnés ou attribués à un membre de la communauté apparaissent avec son nom et son avatar aux emplacements suivants :

* Profils
* [Forums](forum.md)
* [Q&amp;R](working-with-qna.md)
* [Tableaux de bord](enabling-leaderboard.md)
* [Conceptualisation](ideation-feature.md)

Dans l&#39;environnement auteur, pour accéder à la console Badges

* A partir de la navigation globale : **[!UICONTROL Outils > Communautés > Badges]**

Cette console affiche les badges actuellement disponibles et à partir desquels de nouveaux badges peuvent être ajoutés.

![chlimage_1-242](assets/chlimage_1-242.png)

## Créer le badge {#create-badge}

Un badge est créé en téléchargeant une image convenablement petite (72 dpi avec une hauteur comprise entre 26 et 32 pixels) et en fournissant un nom. L’image de badge est stockée dans le référentiel à `/etc/community/badging/images` et automatiquement répliquée dans l’environnement de publication.

Si l’environnement de publication est une batterie d’éditeurs, il est nécessaire de configurer [la synchronisation utilisateur](sync.md).

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Télécharger l’image]**

   (*Obligatoire*) Image de badge d’une taille recommandée de 32 x 32 pixels à 72 ppp, au format JPEG ou PNG.

* **[!UICONTROL Nom]**

   (*Obligatoire*) Nom du badge. Il s’agit de la valeur par défaut `Display Name` ainsi que du nom du noeud du référentiel. Si `Name` n&#39;est pas un nom de noeud de référentiel valide, il sera modifié.

* **[!UICONTROL Nom d’affichage]**

   (*Facultatif*) Nom à afficher pour le badge dans l’interface utilisateur. La valeur par défaut est le texte non modifié saisi pour le `Name`.

* **[!UICONTROL Description]**

   (*Facultatif*) Description du badge.

## Informations supplémentaires {#additional-information}

Pour plus d’informations sur la configuration des règles de notation et de badge, voir [Scoring and Badges](implementing-scoring.md).

Pour la gestion des badges pour les membres, voir [Console Membres](members.md).
