---
title: Création de groupes imbriqués
seo-title: Authoring Nested Groups
description: Création de groupes imbriqués
seo-description: Create nested groups
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 4%

---

# Création de groupes imbriqués {#authoring-nested-groups}

## Création de groupes sur l’instance de création {#creating-groups-on-author}

À l’auteur, à partir de la navigation globale

* Sélectionner **[!UICONTROL Communautés > Sites]**
* Sélectionner **[!UICONTROL dossier d’engagement]** pour l’ouvrir
* Sélectionnez la carte correspondant au **[!UICONTROL Tutoriel de prise en main]**  Site en anglais
   * Sélectionner l’image de la carte
   * Do *not* sélectionner une icône ;

Le résultat est d’atteindre la variable [Console Groupes](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

La fonction de groupes s’affiche sous la forme d’un dossier dans lequel des instances de groupes sont créées. Sélectionnez le dossier Groupes pour l’ouvrir. Le groupe créé lors de la publication est visible.

![chlimage_1-54](assets/chlimage_1-54.png)

## Créer un groupe d’arts principal {#create-main-arts-group}

Ce groupe peut être créé car la structure du site pour la participation inclut une fonction de groupe. Configuration de la fonction dans le `Reference Template` autorise par défaut la sélection de tout modèle de groupe activé. Ainsi, le modèle choisi pour ce nouveau groupe sera le `Reference Group`.

Ces consoles sont très similaires à la console Sites des communautés .

* Sélectionner **[!UICONTROL Créer un groupe]**
* `1 Community Group Template` :
   * Titre du groupe de communautés : Arts
   * Groupe de communautés Description : Groupe parent pour divers groupes d’arts.
   * Racine du groupe de communautés : *leave comme valeur par défaut*
   * Langue(s) de groupe de communautés disponible(s) supplémentaire(s) : utilisez le menu déroulant pour sélectionner la ou les langues de groupe de communautés disponibles. Le menu affiche toutes les langues dans lesquelles le site de la communauté parent est créé. Les utilisateurs peuvent sélectionner l’une de ces langues pour créer des groupes dans plusieurs paramètres régionaux au cours de cette seule étape. Un même groupe est créé dans plusieurs langues spécifiées dans la console Groupes des sites de communauté respectifs.
   * Nom du groupe de communautés : arts
   * Modèle : Menu déroulant pour sélectionner `Reference Group`
   * Sélectionner `Next`

      ![parenttonestedgroup](assets/parenttonestedgroup.png)

Passez aux autres panneaux avec les paramètres suivants :

* **2 Conception**
   * Vous pouvez modifier la conception ou autoriser la définition par défaut de la conception du site parent.
   * Sélectionnez **[!UICONTROL Suivant]**
* **Paramètres 3**
   * **Modération**
      * Laissez vide (hériter du site parent)
   * **Abonnement**
      * use default `Optional Membership`
   * **Miniature**
      * `optional`
   * Sélectionner `Next`
* Sélectionnez **[!UICONTROL Créer]**

### Imbrication de groupes dans le groupe Arts {#nesting-groups-within-arts-group}

Le `groups` doit maintenant contenir deux groupes (il peut être nécessaire d’actualiser la page).

![createccommunity group](assets/createcommunitygroup.png)

#### Publier le groupe {#publish-group}

Avant de créer des groupes imbriqués dans `arts`, survolez le groupe avec la souris. `arts` et sélectionnez l’icône de publication pour la publier.

![chlimage_1-55](assets/chlimage_1-55.png)

Attendez la confirmation de la publication du groupe.

![chlimage_1-56](assets/chlimage_1-56.png)

Le `arts` Le groupe doit également contenir un `groups` , mais vide et dans lequel de nouveaux groupes peuvent être créés. Accédez au dossier du groupe d’arts et créez trois groupes imbriqués, chacun avec un paramètre d’adhésion différent :

1. Visible
   * Titre: `Visual Arts`
   * Nom : `visual`
   * Modèle: `Reference Group`
   * Adhésion : select `Optional Membership`
Un groupe public, ouvert à tous les membres
1. Auditoire
   * Titre: `Auditory Arts`
   * Nom : `auditory`
   * Modèle: `Reference Group`
   * Adhésion : select `Required Membership`
Un groupe ouvert, disponible pour que les membres se joignent à

1. Historique

   * Titre: `Art History`
   * Nom : `history`
   * Modèle: `Reference Group`
   * Adhésion : select `Restricted Membership`
Un groupe secret, visible uniquement par exemple pour les membres invités, invite 
[utilisateur de démonstration](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Actualisez la page pour afficher les trois groupes imbriqués (sous-communautés).

Si nécessaire, pour accéder aux groupes imbriqués à partir de la console Sites des communautés :

* Sélectionner **[!UICONTROL dossier d’engagement]**
* Sélectionner **[!UICONTROL Tutoriel de prise en main]** carte
* Sélectionner **[!UICONTROL Dossier Groupes]**
* Sélectionner **[!UICONTROL carte arts]**
* Sélectionner **[!UICONTROL Dossier Groupes]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Publication de groupes {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Après avoir publié le site de la communauté principale, il est nécessaire de

* Publier chaque groupe individuellement
   * En attente de confirmation de la publication du groupe
* Publier le groupe parent avant de publier les groupes imbriqués dans
   * Tous les groupes doivent être publiés de manière descendante.

![chlimage_1-59](assets/chlimage_1-59.png)

## Expérience sur publication {#experience-on-publish}

Il est possible d’expérimenter les différents groupes lorsqu’ils sont connectés, par exemple avec le [utilisateurs de démonstration](tutorials.md#demo-users) utilisé pour

* Membre du groupe Art/Historique : emily.andrews@mailinator.com/password
   * Le groupe restreint (secret), arts/histoire, sera visible
   * Peut afficher les groupes facultatifs (publics)
   * Peut rejoindre des groupes restreints (ouverts)
* Gestionnaire de groupe : aaron.mcdonald@mailinator.com/password
   * Peut afficher les groupes facultatifs (publics)
   * peuvent rejoindre des groupes restreints (ouverts) ;
   * Ne verront pas les groupes restreints (secrets)

Accès aux communautés [Consoles Membres et Groupes](members.md) sur l’auteur pour ajouter d’autres utilisateurs à différents groupes de membres qui correspondent aux groupes de la communauté.
