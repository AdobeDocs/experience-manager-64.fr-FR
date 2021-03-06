---
title: Utilisation du composant Vote
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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 26%

---

# Utilisation du composant Vote {#using-voting}

Le `Voting` est un outil utile qui permet aux membres de la communauté d’évaluer un élément de contenu particulier, tel qu’une réponse dans un composant Q&amp;R. Avec le `Voting` , les membres sélectionnent les flèches haut ou bas pour indiquer leur opinion.

## Ajout d’un composant Vote à une page {#adding-voting-to-a-page}

Pour ajouter une `Voting` sur une page en mode création, utilisez l’explorateur de composants pour accéder à `Communities / Voting` et faites-le glisser sur la page, par exemple à un emplacement relatif à la fonction sur laquelle les utilisateurs peuvent voter.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-voting.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Voting` s’affiche.

![chlimage_1-307](assets/chlimage_1-307.png)

## Configuration du composant Vote {#configuring-voting}

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

## Expérience des visiteurs {#site-visitor-experience}

### Membres {#members}

Les membres ne peuvent voter qu’une seule fois, mais peuvent changer leur vote à tout moment.

### Anonyme {#anonymous}

Le vote anonyme n’est pas possible. Les visiteurs du site doivent s’enregistrer (devenir membres) et se connecter pour participer au vote.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur le vote](essentials-voting.md) pour les développeurs.
