---
title: Utilisation de Social Graph
seo-title: Using Social Graph
description: Ajout d’un composant Suivant à une page
seo-description: Adding a Following component to a page
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: ab829d28-278d-4139-af16-edcc24b3d56b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 5%

---

# Utilisation de Social Graph {#using-social-graph}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

La possibilité pour un membre de la communauté de suivre [activités](activities.md) et à suivre est établi par le biais de deux composants : `Follow`et `Following`.

Le `Follow`doit être associé à une autre ressource, et cette association est déjà établie pour les membres et les fonctionnalités de la communauté.

Le `Following`Le composant liste simplement les membres qui suivent le membre actuel ou qui sont suivis par le membre actuel. Ce graphique social des relations entre les membres est inclus dans le profil utilisateur établi pour une [site communautaire](overview.md#communitiessites).

## Ajout de l’option Suivant à une page {#adding-following-to-a-page}

Si vous souhaitez ajouter une `Following`à une page en mode création, recherchez le composant. `Communities / Following` et faites-le glisser sur la page où le graphique social doit apparaître.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-socialgraph.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Following` apparaît :

![chlimage_1-447](assets/chlimage_1-447.png)

## Configuration suivante {#configuring-following}

Actuellement, il est nécessaire de définir la propriété pour déterminer si le composant affiche la variable `follows`ou la variable `following`relation.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur les graphiques sociaux](essentials-socialgraph.md) pour les développeurs.
