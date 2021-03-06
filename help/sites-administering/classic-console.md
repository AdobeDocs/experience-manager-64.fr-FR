---
title: Console Balisage de l’interface utilisateur (IU) classique
seo-title: Classic UI Tagging Console
description: Découvrez la console Balisage de l’interface utilisateur classique.
seo-description: Learn about the Classic UI Tagging Console.
uuid: c3080c82-0b34-4922-a263-1674a9522649
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: a7f31bc8-c583-439f-b2af-1dcc58f9c481
exl-id: 0c989965-c6cc-4ec7-a90f-6c52e8362485
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 67%

---

# Console Balisage de l’interface utilisateur (IU) classique{#classic-ui-tagging-console}

Cette section est réservée à la console Balisage de l’interface utilisateur classique.

La console Balisage de l’interface utilisateur optimisée pour les écrans tactiles se trouve [ici](/help/sites-administering/tags.md#tagging-console).

Pour accéder à la console Balisage de l’interface utilisateur classique :

* en mode de création
* Connectez-vous avec des droits d’administrateur.
* Accédez à la console

   par exemple, [http://localhost:4502/tagging](http://localhost:4502/tagging)

![managing_tags_usingthetagasationconsole-1](assets/managing_tags_usingthetagasministrationconsole-1.png)

## Créations de balises et d’espaces de noms {#creating-tags-and-namespaces}

1. En fonction du niveau de départ, vous pouvez créer une balise ou un espace de noms à l’aide de l’option **Nouveau** :

   Si vous sélectionnez **Balises**, vous pouvez créer un espace de noms :

   ![creating_tags_andnamespaces-1](assets/creating_tags_andnamespaces-1.png)

   Si vous sélectionnez un espace de noms (**Demo**, par exemple), vous pouvez y créer une balise :

   ![creating_tags_andnamespace_innewnamespace](assets/creating_tags_andnamespacesinnewnamespace.png)

1. Dans les deux cas, saisissez

   * **Titre**
(
*Obligatoire*) Titre affiché pour la balise. Tout caractère peut être saisi,

      il est recommandé de ne pas utiliser ces caractères spéciaux :

      * `colon (:)` - délimiteur d’espace de noms
      * `forward slash (/)` - délimiteur de sous-balises

      Si vous saisissez ces caractères, ils ne s’affichent pas.

   * **Nom**

      (*Obligatoire*) Nom du noeud de la balise.

   * **Description**

      (*facultatif*) Description de la balise.

   * Sélectionnez **Créer**.


## Modification de balises {#editing-tags}

1. Dans le volet de droite, sélectionnez la balise à modifier.
1. Cliquez sur **Modifier**.
1. Vous pouvez modifier le **Titre** et la **Description**.
1. Cliquez sur **Enregistrer** pour fermer la boîte de dialogue.

## Suppression des balises {#deleting-tags}

1. Dans le volet de droite, sélectionnez la balise à supprimer.
1. Cliquez sur **Supprimer**.
1. Cliquez sur **Oui** pour fermer la boîte de dialogue.

   La balise ne doit plus figurer dans la liste.

## Activation et désactivation de balises {#activating-and-deactivating-tags}

1. Dans le volet de droite, sélectionnez l’espace de noms ou la balise à activer (publication) ou à désactiver (annulation de la publication).
1. Cliquez sur **Activer** ou **Désactiver**, suivant les besoins.

## Liste : indiquant où les balises sont référencées {#list-showing-where-tags-are-referenced}

L’option **Liste** ouvre une nouvelle fenêtre qui présente les chemins d’accès de toutes les pages utilisant la balise mise en surbrillance :

![list_show_wheretagsarereferounded](assets/list_showing_wheretagsarereferenced.png)

## Déplacement des balises {#moving-tags}

Pour aider les administrateurs et les développeurs de balises à nettoyer la taxonomie ou à renommer un ID de balise, il est possible de déplacer une balise vers un nouvel emplacement :

1. Ouvrez la console **Tagging**.
1. Sélectionnez le tag et cliquez sur **Déplacer...** dans la barre d’outils supérieure (ou dans le menu contextuel).
1. Dans la boîte de dialogue **Déplacer le tag**, définissez :

   * **vers**, le nœud de destination.
   * **Renommer en**, le nouveau nom du nœud.

1. Cliquez sur **Déplacer**.

La boîte de dialogue **Déplacer le tag** se présente comme suit :

![move_tag](assets/move_tag.png)

>[!NOTE]
>
>Les créateurs ne doivent pas déplacer les balises ou renommer l’ID de balise. Si nécessaire, les auteurs ne doivent [modification des titres des balises](#editing-tags).

## Fusion des balises {#merging-tags}

Il est également possible de recourir à la fusion de balises lorsqu’une taxonomie comporte des doublons. Lorsque la balise A est fusionnée dans la balise B, toutes les pages balisées avec la balise A sont balisées avec la balise B, et la balise A n’est plus disponible pour les auteurs.

Pour fusionner un tag dans un autre :

1. Ouvrez la console **Tagging**.
1. Sélectionnez le tag et cliquez sur **Fusionner...** dans la barre d’outils supérieure (ou dans le menu contextuel).
1. Dans la boîte de dialogue **Fusionner le tag**, définissez :

   * **en**, le nœud de destination.

1. Cliquez sur **Fusionner**.

Le **Fusionner la balise** dialog se présente comme suit :

![mergetag](assets/mergetag.png)

## Compte d’utilisation des balises {#counting-usage-of-tags}

Pour afficher le nombre d’utilisations d’un tag :

1. Ouvrez la console **Tagging**.
1. Cliquez sur **Compteur d’utilisations** dans la barre d’outils supérieure : la colonne Décompte affiche le résultat.

## Gestion de tags dans diverses langues {#managing-tags-in-different-languages}

La propriété facultative `title`   d’une balise peut être traduite en plusieurs langues. Balise `titles` peut ensuite s’afficher en fonction de la langue de l’utilisateur ou de la langue de la page.

### Définition de titres de balises dans plusieurs langues {#defining-tag-titles-in-multiple-languages}

La procédure suivante montre comment traduire les `title`de la balise **Animals** en anglais, allemand et français :

1. Accédez au **Balisage** console.
1. Modifier la balise **Animals** below **Balises** > **Images de photothèque**.
1. Ajoutez les traductions dans les langues suivantes :

   * **Anglais** : Animals
   * **Allemand** : Tiere
   * **Français** : Animaux

1. Enregistrez les modifications.

La boîte de dialogue se présente comme suit :

![edit_tag](assets/edit_tag.png)

La console Balisage utilise la langue du créateur, dès lors, pour la balise « Animals », « Animaux » s’affiche si l’utilisateur définit la langue sur Français dans les propriétés de l’utilisateur.

Pour ajouter une nouvelle langue à la boîte de dialogue, reportez-vous à la section [Ajout d’une langue à la boîte de dialogue Modifier la balise](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog) dans la section **Balisage pour les développeurs**.

### Affichage des titres des balises dans les propriétés de page dans une langue spécifiée {#displaying-tag-titles-in-page-properties-in-a-specified-language}

Par défaut, la balise `titles`dans la page , les propriétés s’affichent dans la langue de la page. La boîte de dialogue de balise dans les propriétés de page comporte un champ de langue qui permet l’affichage de la balise. `titles`dans une autre langue. La procédure suivante décrit l’affichage de la balise . `titles`en français :

1. Reportez-vous à la section précédente pour ajouter la traduction française au **Animals** below **Balises** > **Images de photothèque**.
1. Ouvrez les propriétés de la page **Produits** dans la branche English (Anglais) du site **Geometrixx**.
1. Ouvrez le **Balises/Mots-clés** (en sélectionnant le menu déroulant à droite de la zone d’affichage Balises/Mots-clés) et en sélectionnant **Français** dans le menu déroulant en bas à droite.
1. Faites défiler l’écran à l’aide des flèches gauche-droite jusqu’à ce que vous puissiez sélectionner la variable **Images de photothèque** tab

   Sélectionnez la **Animals** (**Animaux**) et sélectionnez en dehors de la boîte de dialogue pour la fermer et ajouter la balise aux propriétés de la page.

   ![French_tag](assets/french_tag.png)

Par défaut, la boîte de dialogue Propriétés de la page affiche la balise . `titles`selon la langue de la page.

En général, la langue de la balise est celle de la page si elle est disponible. Lorsque le [widget](/help/sites-developing/building.md#tagging-on-the-client-side) balise est utilisé dans d’autres cas (formulaires ou boîtes de dialogue, par exemple), la langue da la balise dépend du contexte.

>[!NOTE]
>
>Le nuage de balises et les méta-mots-clés dans le composant de page standard utilisent la balise localisée . `titles`selon la langue de la page, le cas échéant.
