---
title: Console Balisage de l’interface utilisateur (IU) classique
seo-title: Classic UI Tagging Console
description: Découvrez la console de balisage de l’interface utilisateur classique.
seo-description: Learn about the Classic UI Tagging Console.
uuid: c3080c82-0b34-4922-a263-1674a9522649
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: a7f31bc8-c583-439f-b2af-1dcc58f9c481
exl-id: 0c989965-c6cc-4ec7-a90f-6c52e8362485
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 47%

---

# Console Balisage de l’interface utilisateur (IU) classique{#classic-ui-tagging-console}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette section concerne la console de balisage de l’interface utilisateur classique.

La console de balisage de l’interface utilisateur optimisée pour les écrans tactiles est [here](/help/sites-administering/tags.md#tagging-console).

Pour accéder à la console Balisage de l’interface utilisateur classique :

* en mode de création
* connexion avec droits d’administrateur
* Accédez à la console

   par exemple, [http://localhost:4502/tagging](http://localhost:4502/tagging)

![managing_tags_usingthetagasationconsole-1](assets/managing_tags_usingthetagasministrationconsole-1.png)

## Création de balises et d’espaces de noms {#creating-tags-and-namespaces}

1. Selon le niveau à partir duquel vous commencez, vous pouvez créer une balise ou un espace de noms à l’aide de **Nouveau**:

   Si vous sélectionnez **Balises** vous pouvez créer un espace de noms :

   ![creating_tags_andnamespaces-1](assets/creating_tags_andnamespaces-1.png)

   Si vous sélectionnez un espace de noms (par exemple **Démonstration**) vous pouvez créer une balise dans cet espace de noms :

   ![creating_tags_andnamespace_innewnamespace](assets/creating_tags_andnamespacesinnewnamespace.png)

1. Dans les deux cas, saisissez

   * **Titre**
(
*Obligatoire*) Titre affiché pour la balise. Tout caractère peut être saisi,

      il est recommandé de ne pas utiliser ces caractères spéciaux :

      * `colon (:)` - Délimiteur d’espace de noms
      * `forward slash (/)` - Délimiteur de sous-balises

      Si vous saisissez ces caractères, ils ne s’affichent pas.

   * **Nom**

      (*Obligatoire*) Nom du nœud pour la balise.

   * **Description**

      (*Facultatif*) Description de la balise.

   * select **Créer**


## Modification des balises {#editing-tags}

1. Dans le volet de droite, sélectionnez la balise à modifier.
1. Cliquez sur **Modifier**.
1. Vous pouvez modifier la variable **Titre** et le **Description**.
1. Cliquez sur **Enregistrer** pour fermer la boîte de dialogue.

## Suppression des balises {#deleting-tags}

1. Dans le volet de droite, sélectionnez la balise à supprimer.
1. Cliquez sur **Supprimer**.
1. Cliquez sur **Oui** pour fermer la boîte de dialogue.

   La balise ne doit plus être répertoriée.

## Activation et désactivation des balises {#activating-and-deactivating-tags}

1. Dans le volet de droite, sélectionnez l’espace de noms ou la balise que vous souhaitez activer (publier) ou désactiver (annuler la publication).
1. Cliquez sur **Activer** ou **Désactiver** selon les besoins.

## Liste : indiquant l’emplacement de référence des balises {#list-showing-where-tags-are-referenced}

**Liste** ouvre une nouvelle fenêtre affichant les chemins de toutes les pages à l’aide de la balise mise en surbrillance :

![list_show_wheretagsarereferounded](assets/list_showing_wheretagsarereferenced.png)

## Déplacement des balises {#moving-tags}

Pour aider les administrateurs et les développeurs de balises à nettoyer la taxonomie ou à renommer un ID de balise, il est possible de déplacer une balise vers un nouvel emplacement :

1. Ouvrez le **Balisage** console.
1. Sélectionnez la balise et cliquez sur **Déplacer..** dans la barre d’outils supérieure (ou dans le menu contextuel).
1. Dans le **Déplacer la balise** dialog, définissez :

   * **to**, le noeud de destination.
   * **Renommer en**, le nouveau nom du noeud.

1. Cliquez sur **Déplacer**.

Le **Déplacer la balise** dialog se présente comme suit :

![move_tag](assets/move_tag.png)

>[!NOTE]
>
>Les créateurs ne doivent pas déplacer les balises ou renommer l’ID de balise. Lorsque cela est nécessaire, les créateurs doivent seulement [modifier le titre des balises](#editing-tags).

## Fusion de balises {#merging-tags}

Il est également possible de recourir à la fusion de balises lorsqu’une taxonomie comporte des doublons. Lorsque la balise A est fusionnée dans la balise B, toutes les pages balisées avec la balise A sont balisées avec la balise B et la balise A n’est plus disponible pour les auteurs.

Pour fusionner une balise dans une autre balise :

1. Ouvrez le **Balisage** console.
1. Sélectionnez la balise et cliquez sur **Fusionner..** dans la barre d’outils supérieure (ou dans le menu contextuel).
1. Dans le **Fusionner la balise** dialog, définissez :

   * **into**, le noeud de destination.

1. Cliquez sur **Fusion**.

La boîte de dialogue **Fusionner la balise** se présente de la manière suivante :

![mergetag](assets/mergetag.png)

## Comptage de l’utilisation des balises {#counting-usage-of-tags}

Pour savoir combien de fois une balise est utilisée :

1. Ouvrez le **Balisage** console.
1. Cliquez sur **Utilisation des nombres** dans la barre d’outils supérieure : la colonne Nombre affiche le résultat.

## Gestion des balises dans différentes langues {#managing-tags-in-different-languages}

La propriété facultative `title` d’une balise peut être traduite en plusieurs langues. Les `titles` de balises peuvent s’afficher soit dans la langue de l’utilisateur, soit dans la langue de la page.

### Définition de titres de balises dans plusieurs langues {#defining-tag-titles-in-multiple-languages}

La procédure ci-dessous indique comment traduire le `title` de la balise **Animals** en anglais, en allemand et en français :

1. Accédez à la console **Balisage**.
1. Modifiez la balise **Animals** située sous **Balises** > **Images de photothèque**.
1. Ajoutez les traductions dans les langues suivantes :

   * **Anglais**: Animals
   * **Allemand**: Tiere
   * **Français**: Animaux

1. Enregistrez les modifications.

La boîte de dialogue se présente comme suit :

![edit_tag](assets/edit_tag.png)

La console Balisage utilise la langue du créateur, dès lors, pour la balise « Animals », « Animaux » s’affiche si l’utilisateur définit la langue sur Français dans les propriétés de l’utilisateur.

Pour ajouter une nouvelle langue à la boîte de dialogue, reportez-vous à la section [Ajout d’une langue à la boîte de dialogue Modifier la balise](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog) dans la section **Balisage pour les développeurs**.

### Affichage des titres des balises dans les propriétés de page dans une langue spécifiée {#displaying-tag-titles-in-page-properties-in-a-specified-language}

Par défaut, les `titles` des balises dans les propriétés de page sont affichés dans la langue de la page. La boîte de dialogue de balise dans les propriétés de page comporte un champ Langue, qui permet d’afficher le `titles` des balises dans une autre langue. La procédure ci-dessous décrit comment afficher les `titles` des balises en français :

1. Reportez-vous à la section précédente pour ajouter la traduction française au mot-clé **Animals** en sélectionnant **Balises** > **Images de photothèque**.
1. Ouvrez les propriétés de la page **Produits** dans la branche English (Anglais) du site **Geometrixx**.
1. Ouvrez la boîte de dialogue **Balises/Mots-clés** (en sélectionnant le menu déroulant à droite de la zone d’affichage Balises/Mots-clés) et sélectionnez la langue **Français** dans le menu déroulant dans le coin inférieur droit.
1. Faites défiler la page à l’aide des flèches gauche-droite jusqu’à ce que vous puissiez sélectionner l’onglet **Images de photothèque**.

   Sélectionnez la balise **Animals** (**Animaux**) et cliquez en dehors de la boîte de dialogue pour la fermer et ajouter la balise aux propriétés de la page.

   ![French_tag](assets/french_tag.png)

Par défaut, la boîte de dialogue Propriétés de page affiche le `titles` des balises en fonction de la langue de la page.

En général, la langue de la balise est celle de la page si elle est disponible. Lorsque la variable [widget de balise](/help/sites-developing/building.md#tagging-on-the-client-side) est utilisé dans d’autres cas (dans les formulaires ou les boîtes de dialogue, par exemple), la langue de la balise dépend du contexte.

>[!NOTE]
>
>Le nuage de balises et les éléments « meta keyword » du composant Page standard utilisent les `titles` des balises localisées en fonction de la langue de la page (si elle est disponible).
