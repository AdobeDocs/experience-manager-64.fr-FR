---
title: Utilisation de l’option J’aime
seo-title: Using Liking
description: Ajout et configuration du composant J’aime
seo-description: Adding and configuring the Liking component
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 8%

---

# Utilisation de l’option J’aime {#using-liking}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le `Liking`component est un outil utile qui permet aux utilisateurs d’exprimer une opinion sur un élément de contenu particulier, comme un commentaire dans un forum. Avec le `Liking`, les membres sélectionnent l’icône coeur pour indiquer une opinion positive.

## Ajout de mentions J’aime à une page {#adding-liking-to-a-page}

Pour ajouter une `Liking` sur une page en mode création, utilisez l’explorateur de composants pour accéder à

* `Communities / Liking`

et faites-le glisser sur la page, par exemple à une position relative à la fonction que les utilisateurs peuvent aimer.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-liking.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Liking` s’affiche.

![chlimage_1-93](assets/chlimage_1-93.png)

## Configuration de l’option J’aime {#configuring-liking}

Sélectionnez le `Liking` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-94](assets/chlimage_1-94.png)

Sous , **[!UICONTROL Textes et libellés]** , spécifiez les propriétés utilisées pour enregistrer les mentions J’aime.

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL Etiquette de réponse positive]**
(
*Obligatoire*) Nom de propriété d’une réponse positive.

* **[!UICONTROL Etiquette de réponse négative]**
(
*Obligatoire*) Nom de propriété d’une réponse négative.

* **[!UICONTROL Nom Tally]**
(
*Obligatoire*) Nom de propriété interne identifiable de cette instance d’un composant Vote.

## Expérience du visiteur du site {#site-visitor-experience}

### Membres {#members}

Les membres peuvent changer de comportement à tout moment.

### Anonyme {#anonymous}

Les liens anonymes ne sont pas pris en charge. Les visiteurs du site doivent s’inscrire (devenir membres) et se connecter pour participer à l’activité de votre choix.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales relatives aux mentions J’aime](essentials-liking.md) pour les développeurs.
