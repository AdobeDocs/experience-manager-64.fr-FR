---
title: Utilisation des évaluations
seo-title: Using Ratings
description: Ajout d’un composant Évaluation à une page
seo-description: Adding a Rating component to a page
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
exl-id: 1de28140-5334-4ca2-a476-5ad253809808
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 6%

---

# Utilisation des évaluations {#using-ratings}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le `Rating`est utilisé de manière autonome ou conjointement avec d’autres fonctionnalités de Communities. Ce composant permet aux membres de la communauté connectés d’exprimer leurs opinions en évaluant le contenu.

## Ajout d’une évaluation à une page {#adding-a-rating-to-a-page}

Pour ajouter une `Rating`à une page en mode création, recherchez le composant. `Communities / Rating` et faites-le glisser sur la page, par exemple à une position relative à la fonction que les membres peuvent évaluer.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](rating-basics.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Rating` s’affiche.

![chlimage_1-493](assets/chlimage_1-493.png)

## Configuration de l’évaluation {#configuring-rating}

Sélectionnez le `Rating` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-494](assets/chlimage_1-494.png)

Sous , **[!UICONTROL Textes et libellés]** vous pouvez spécifier l’identifiant interne de l’évaluation.

![chlimage_1-495](assets/chlimage_1-495.png)

**[!UICONTROL Nom Tally]**
(*Obligatoire*) Un nom simple pour la variable `Rating`qui identifie de manière unique cette instance. Doit être un nom de noeud valide pour le référentiel.

## Expérience du visiteur du site {#site-visitor-experience}

### Membres {#members}

Une seule évaluation par membre est autorisée. Le membre peut modifier sa note à tout moment.

### Anonyme {#anonymous}

La publication anonyme d’une évaluation n’est pas prise en charge. Les visiteurs du site doivent s’inscrire (devenir membres) et se connecter pour participer.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur la notation](rating-basics.md) pour les développeurs.
