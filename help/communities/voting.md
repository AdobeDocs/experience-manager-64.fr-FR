---
title: Utilisation du vote
seo-title: Using Voting
description: Ajout du composant Vote à une page
seo-description: Adding the Voting component to a page
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
exl-id: 660a7106-0c21-4073-8319-4d6d20b9bc49
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 8%

---

# Utilisation du vote {#using-voting}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le `Voting` est un outil utile qui permet aux membres de la communauté d’évaluer un élément de contenu particulier, tel qu’une réponse dans un composant Q&amp;R. Avec le `Voting` , les membres sélectionnent les flèches haut ou bas pour indiquer leur opinion.

## Ajout d’un vote à une page {#adding-voting-to-a-page}

Pour ajouter une `Voting` sur une page en mode création, utilisez l’explorateur de composants pour accéder à `Communities / Voting` et faites-le glisser sur la page, par exemple à un emplacement relatif à la fonction sur laquelle les utilisateurs peuvent voter.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-voting.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Voting` s’affiche.

![chlimage_1-307](assets/chlimage_1-307.png)

## Configuration du vote {#configuring-voting}

Sélectionnez le `Voting` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-308](assets/chlimage_1-308.png)

Sous , **[!UICONTROL Textes et libellés]** , spécifiez les propriétés utilisées pour enregistrer les votes.

![chlimage_1-309](assets/chlimage_1-309.png)

* **[!UICONTROL Etiquette de réponse positive]**
(
*Obligatoire*) Nom de propriété interne d’une réponse positive.

* **[!UICONTROL Etiquette de réponse négative]**
(
*Obligatoire*) Nom de propriété interne d’une réponse négative.

* **[!UICONTROL Nom Tally]**
(
*Obligatoire*) Nom de propriété interne identifiable de cette instance d’un composant Vote.

## Expérience du visiteur du site {#site-visitor-experience}

### Membres {#members}

Les membres ne peuvent voter qu&#39;une seule fois, mais peuvent changer leur vote à tout moment.

### Anonyme {#anonymous}

Le vote anonyme n&#39;est pas pris en charge. Les visiteurs du site doivent s’inscrire (devenir membre) et se connecter pour participer une fois au vote.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur le vote](essentials-voting.md) pour les développeurs.
