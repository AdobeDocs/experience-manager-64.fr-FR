---
title: Création de groupes imbriqués
seo-title: Création de groupes imbriqués
description: Création de groupes imbriqués
seo-description: Création de groupes imbriqués
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 4%

---


# Création de groupes imbriqués {#authoring-nested-groups}

## Création de groupes sur l’auteur {#creating-groups-on-author}

Sur l’auteur, à partir de la navigation globale

* Sélectionnez **[!UICONTROL Communautés > Sites]**
* Sélectionnez **[!UICONTROL dossier d&#39;engagement]** pour l&#39;ouvrir.
* Sélectionnez la carte pour le site en anglais **[!UICONTROL Didacticiel de prise en main]**
   * Sélectionner l’image de la carte
   * Ne *pas* sélectionner une icône

Le résultat est d&#39;atteindre la console [Groupes](groups.md) :

![chlimage_1-53](assets/chlimage_1-53.png)

La fonction de groupes s&#39;affiche sous la forme d&#39;un dossier dans lequel des instances de groupes sont créées. Sélectionnez le dossier Groupes pour l’ouvrir. Le groupe créé lors de la publication est visible.

![chlimage_1-54](assets/chlimage_1-54.png)

## Créer le groupe des arts principaux {#create-main-arts-group}

Ce groupe peut être créé car la structure du site pour engager inclut une fonction de groupes. La configuration de la fonction dans `Reference Template` du site autorise par défaut la sélection de tout modèle de groupe activé. Ainsi, le modèle choisi pour ce nouveau groupe sera le `Reference Group`.

Ces consoles sont très similaires à la console Sites des communautés.

* Sélectionner **[!UICONTROL Créer un groupe]**
* `1 Community Group Template` :
   * Titre du groupe communautaire : Arts
   * Description du groupe de la communauté : Groupe parent pour divers groupes artistiques.
   * Racine du groupe de communautés : *laisser comme valeur par défaut*
   * Langue(s) de groupe(s) communautaire(s) disponible(s) supplémentaire(s) : utilisez le menu déroulant pour sélectionner la ou les langue(s) de groupe communautaire disponible(s). Le menu affiche toutes les langues dans lesquelles le site de la communauté parent est créé. Les utilisateurs peuvent sélectionner l’une de ces langues pour créer des groupes dans plusieurs paramètres régionaux au cours de cette seule étape. Un même groupe est créé dans plusieurs langues spécifiées dans la console Groupes des sites communautaires respectifs.
   * Nom du groupe de la communauté : arts
   * Modèle : descendre pour sélectionner `Reference Group`
   * Sélectionner `Next`

      ![parenttonestedgroup](assets/parenttonestedgroup.png)

Passez ensuite aux autres panneaux avec les paramètres suivants :

* **2 Conception**
   * Vous pouvez modifier la conception ou autoriser la définition par défaut de la conception du site parent
   * Sélectionnez **[!UICONTROL Suivant]**
* **3 Paramètres**
   * **Modération**
      * Laisser vide (hériter du site parent)
   * **Abonnement**
      * utiliser la valeur par défaut `Optional Membership`
   * **Miniature**
      * `optional`
   * Sélectionner `Next`
* Sélectionnez **[!UICONTROL Créer]**

### Groupes imbriqués dans le groupe Arts {#nesting-groups-within-arts-group}

Le dossier `groups` doit maintenant contenir deux groupes (il peut s’avérer nécessaire d’actualiser la page).

![createcommunitgroup](assets/createcommunitygroup.png)

#### Publier le groupe {#publish-group}

Avant de créer des groupes imbriqués dans le groupe `arts`, passez la souris sur la carte `arts` et sélectionnez l’icône de publication pour la publier.

![chlimage_1-55](assets/chlimage_1-55.png)

Attendez la confirmation de la publication du groupe.

![chlimage_1-56](assets/chlimage_1-56.png)

Le groupe `arts` doit également contenir un dossier `groups`, mais un dossier vide dans lequel de nouveaux groupes peuvent être créés. Accédez au dossier du groupe arts et créez 3 groupes imbriqués, chacun avec un paramètre d’adhésion différent :

1. Visible
   * Titre: `Visual Arts`
   * Nom : `visual`
   * Template: `Reference Group`
   * Adhésion : sélectionner `Optional Membership`
Un groupe public, ouvert à tous les membres
1. Auditoire
   * Titre: `Auditory Arts`
   * Nom : `auditory`
   * Modèle : `Reference Group`
   * Adhésion : sélectionner `Required Membership`
Un groupe ouvert, accessible aux membres pour les rejoindre

1. Historique

   * Titre: `Art History`
   * Nom : `history`
   * Modèle : `Reference Group`
   * Adhésion : sélectionner `Restricted Membership`
Un groupe secret, visible uniquement pour les membres invités comme exemple, invite 
[utilisateur de démonstration](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Actualisez la page pour afficher les trois groupes imbriqués (sous-communautés).

Si nécessaire, pour accéder aux groupes imbriqués à partir de la console Sites des communautés :

* Sélectionner **[!UICONTROL dossier d&#39;engagement]**
* Sélectionnez la carte **[!UICONTROL Didacticiel de prise en main]**.
* Sélectionner le dossier **[!UICONTROL Groupes]**
* Sélectionner **[!UICONTROL carte arts]**
* Sélectionner le dossier **[!UICONTROL Groupes]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Groupes de publication {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Après avoir publié le site communautaire principal, il est nécessaire de

* Publier chaque groupe individuellement
   * En attente de confirmation de la publication du groupe
* Publier le groupe parent avant de publier tout groupe imbriqué dans
   * Tous les groupes doivent être publiés de manière descendante.

![chlimage_1-59](assets/chlimage_1-59.png)

## Expérience sur la publication {#experience-on-publish}

Il est possible d’expérimenter les différents groupes lorsqu’ils sont connectés, par exemple avec les [utilisateurs de démonstration](tutorials.md#demo-users) utilisés pour

* Membre du groupe Art/Historique : emily.andrews@mailinator.com/password
   * Le groupe restreint (secret), arts/histoire, sera visible
   * Peut afficher les groupes facultatifs (publics)
   * Peut rejoindre des groupes restreints (ouverts)
* Gestionnaire de groupe : aaron.mcdonald@mailinator.com/password
   * Peut afficher les groupes facultatifs (publics)
   * peut rejoindre des groupes restreints (ouverts)
   * Ne verra pas les groupes limités (secrets)

Accédez aux consoles Communautés [Membres et Groupes](members.md) sur l&#39;auteur pour ajouter d&#39;autres utilisateurs à divers groupes de membres qui correspondent aux groupes communautaires.
