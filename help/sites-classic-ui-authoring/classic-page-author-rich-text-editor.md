---
title: Éditeur de texte enrichi
seo-title: Rich Text Editor
description: L’éditeur de texte enrichi est un élément de base de la saisie de contenu texte dans AEM.
seo-description: The Rich Text Editor is a basic building block for inputting textual content into AEM.
uuid: 42001071-f7a7-475d-8aab-a8054303db68
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: adc697e1-4a1c-4985-8690-79ed77736fec
exl-id: 44cd0092-de40-4a72-a682-1e8f5906b2e5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1832'
ht-degree: 30%

---

# Éditeur de texte enrichi{#rich-text-editor}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’éditeur de texte enrichi est un élément de base de la saisie de contenu texte dans AEM. Il constitue la base de divers composants, notamment :

* Texte
* Texte Image
* Tableau

## Éditeur de texte enrichi {#rich-text-editor-2}

La boîte de dialogue de modification WYSIWYG offre un large éventail de fonctionnalités :

![cq55_rte_basicchars](assets/cq55_rte_basicchars.png)

>[!NOTE]
>
>Les fonctions disponibles peuvent être configurées pour chaque projet ; elles peuvent donc varier pour votre installation.

## Édition statique {#in-place-editing}

Outre le mode d’édition de texte enrichi basé sur une boîte de dialogue, AEM fournit également le mode d’édition statique, qui permet de modifier directement le texte tel qu’il est affiché dans la mise en page.

Cliquez deux fois sur un paragraphe (double-clic lent) pour passer en mode d’édition statique (la bordure du composant devient orange).

Vous pourrez modifier directement le texte sur la page, plutôt que dans une fenêtre de boîte de dialogue. Il vous suffit d’apporter vos modifications ; elles seront automatiquement enregistrées.

![cq55_rte_inlineediting](assets/cq55_rte_inlineediting.png)

>[!NOTE]
>
>Si l’outil de recherche de contenu est ouvert, une barre d’outils avec les options de mise en forme de l’éditeur de texte enrichi s’affiche en haut de l’onglet (comme ci-dessus).
>
>Si l’outil de recherche de contenu n’est pas ouvert, la barre d’outils ne s’affiche pas.

Actuellement, le mode d’édition statique est activé pour les éléments de page générés par la variable **Texte** et **Titre** composants.

>[!NOTE]
>
>Le **Titre** est conçu pour contenir un texte court sans sauts de ligne. Lorsque vous modifiez un titre en mode d’édition statique, la saisie d’un saut de ligne ouvre une nouvelle **Texte** sous le titre.

## Fonctions de l’éditeur de texte enrichi {#features-of-the-rich-text-editor}

L’éditeur de texte enrichi fournit diverses fonctions, [selon la configuration](/help/sites-administering/rich-text-editor.md) du composant. Ces fonctions sont disponibles dans les deux interfaces utilisateur (classique et optimisée pour les écrans tactiles).

### Formats de caractères de base {#basic-character-formats}

![](do-not-localize/cq55_rte_basicchars.png)

Vous pouvez y appliquer une mise en forme aux caractères que vous avez sélectionnés (mis en surbrillance). certaines options comportent également des touches de raccourci :

* Gras (Ctrl+B)
* Italique (Ctrl+I)
* Souligné (Ctrl-U)
* Indice
* Exposant

![cq55_rte_basicchars_use](assets/cq55_rte_basicchars_use.png)

Tous fonctionnent comme un bouton d’activation/désactivation. La résélection supprime donc le format.

### Styles et formats prédéfinis {#predefined-styles-and-formats}

![cq55_rte_stylesparagraph](assets/cq55_rte_stylesparagraph.png)

Votre installation peut inclure des styles et des formats prédéfinis. Ils sont disponibles avec les **Style** et **Format** liste déroulante et peut être appliqué au texte que vous avez sélectionné.

Un style peut être appliqué à une chaîne spécifique (un style correspond à CSS) :

![cq55_rte_styles_use](assets/cq55_rte_styles_use.png)

Tandis qu’une disposition est appliquée à l’intégralité d’un paragraphe texte (une mise en forme est basée sur le langage HTML) :

![cq55_rte_paragraph_use](assets/cq55_rte_paragraph_use.png)

Un format spécifique ne peut être modifié que (la valeur par défaut est **Paragraphe**).

Un style peut être supprimé. placez le curseur dans le texte auquel le style a été appliqué, puis cliquez sur l’icône Supprimer :

>[!CAUTION]
>
>Ne sélectionnez pas à nouveau le texte auquel le style a été appliqué ou l’icône sera désactivée.

### Couper, Copier, Coller {#cut-copy-paste}

![](do-not-localize/cq55_rte_cutcopypaste.png)

Les fonctions standard de **Couper** et **Copier** sont disponibles. Plusieurs versions de **Coller** sont fournis pour prendre en charge différents formats.

* Couper (**Ctrl+X**)
* Copier (**Ctrl+C**)
* Coller

   Il s’agit du mécanisme de collage par défaut (**Ctrl+V**) pour le composant ; lorsqu’il est installé prêt à l’emploi, il est configuré pour être &quot;Coller à partir de Word&quot;.

* Coller en tant que texte

   Supprime tous les styles et la mise en forme pour coller uniquement le texte brut.

* Coller à partir de Word

   Le contenu est collé en tant que HTML (avec le reformatage nécessaire).

### Annuler, Rétablir {#undo-redo}

![](do-not-localize/cq55_rte_undoredo.png)

AEM conserve un historique de vos 50 dernières actions dans le composant actuel, dans l’ordre chronologique. Si nécessaire, ces actions peuvent être annulées (puis rétablies) dans un ordre strict.

>[!CAUTION]
>
>L’historique n’est conservé que pour la session de modification actuelle. Il est redémarré chaque fois que vous ouvrez le composant en vue de le modifier.

>[!NOTE]
>
>Cinquante est le nombre de tâches par défaut. Il peut s’agir d’une opération différente pour votre installation.

### Alignement {#alignment}

![](do-not-localize/cq55_rte_alignment.png)

Votre texte peut être aligné à gauche, au centre ou à droite.

![cq55_rte_alignment_use](assets/cq55_rte_alignment_use.png)

### Indentation {#indentation}

![](do-not-localize/cq55_rte_indent.png)

La mise en retrait d’un paragraphe peut être augmentée ou réduite. Le paragraphe sélectionné est mis en retrait, tout nouveau texte saisi conserve le niveau de mise en retrait actuel.

![cq55_rte_indent_use](assets/cq55_rte_indent_use.png)

### Listes {#lists}

![](do-not-localize/cq55_rte_lists.png)

Vous pouvez créer des listes à puces et numérotées dans votre texte. Sélectionnez le type de liste et commencez à saisir ou mettez en surbrillance le texte à convertir. Dans les deux cas, un flux de ligne lance un nouvel élément de liste.

Vous pouvez créer des listes imbriquées en mettant en retrait un ou plusieurs éléments de liste.

Vous pouvez modifier le style d’une liste en positionnant simplement le curseur dans la liste, puis en sélectionnant l’autre style. Une sous-liste peut également avoir un style différent de la liste contenante. Vous pouvez l’appliquer une fois la sous-liste créée (par mise en retrait).

![cq55_rte_lists_use](assets/cq55_rte_lists_use.png)

### Liens {#links}

![](do-not-localize/cq55_rte_links.png)

Un lien vers une URL (que ce soit dans votre site web ou un emplacement externe) est généré en mettant en surbrillance le texte requis, puis en cliquant sur l’icône **Lien hypertexte** icon :

![](do-not-localize/chlimage_1-12.png)

Une boîte de dialogue vous permet de spécifier l’URL cible, ainsi que de déterminer si elle doit s’ouvrir dans une nouvelle fenêtre.

![cq55_rte_link_use](assets/cq55_rte_link_use.png)

Vous pouvez :

* saisir directement un URI ;
* utiliser la carte du site pour sélectionner une page dans votre site web ;
* saisissez l’URI, puis ajoutez l’ancre cible ; Par exemple : `www.TargetUri.org#AnchorName`
* saisir une ancre uniquement (pour faire référence à &quot;la page en cours&quot;) ; Par exemple : `#anchor`
* recherchez une page dans l’outil de recherche de contenu, puis faites glisser et déposez l’icône de page dans la boîte de dialogue Lien hypertexte .

>[!NOTE]
>
>Vous pouvez faire précéder l’URI de l’un des protocoles configurés pour votre installation. Dans une installation standard, ces protocoles sont `https://`, `ftp://` et `mailto:`. Les protocoles non configurés pour votre installation seront rejetés et marqués comme non valides.

Pour rompre le lien, placez le curseur n’importe où dans le texte du lien et cliquez sur le bouton **Dissocier** icon :

![](do-not-localize/chlimage_1-13.png)

### Ancre {#anchors}

![](do-not-localize/cq55_rte_anchor.png)

Une ancre peut être créée n’importe où dans le texte en positionnant le curseur ou en sélectionnant du texte. Cliquez ensuite sur le bouton **Ancre** pour ouvrir la boîte de dialogue.

Saisissez le nom de l’ancre, puis cliquez sur **OK** pour enregistrer.

![cq55_rte_anchor_use](assets/cq55_rte_anchor_use.png)

L’ancre s’affiche lorsque le composant est en cours d’édition ; elle peut désormais être utilisée dans une cible pour les liens.

![chlimage_1-145](assets/chlimage_1-145.png)

### Rechercher et remplacer {#find-and-replace}

![](do-not-localize/cq55_rte_findreplace.png)

AEM fournit à la fois une **Rechercher** et un **Remplacer** (rechercher et remplacer).

Les deux ont une **Rechercher suivant** pour rechercher le texte spécifié dans le composant ouvert. Vous pouvez également indiquer si la casse (supérieure/inférieure) doit être mise en correspondance.

La recherche commence toujours à partir de la position actuelle du curseur dans le texte. Lorsque la fin du composant est atteinte, un message vous informe que la prochaine opération de recherche démarre à partir du haut.

![cq55_rte_find_use](assets/cq55_rte_find_use.png)

L’option **Remplacer** permet de **rechercher**, puis de **remplacer** une instance par le texte indiqué ou de **remplacer toutes** les instances du composant actif.

![cq55_rte_findreplace_use](assets/cq55_rte_findreplace_use.png)

### Images {#images}

Vous pouvez faire glisser des images à partir de l’outil de recherche de contenu pour les ajouter au texte.

![cq55_rte_image_use](assets/cq55_rte_image_use.png)

>[!NOTE]
>
>AEM propose également des composants spécialisés permettant une configuration d’image plus détaillée ; **Image** et **Texte et image**, par exemple.

### Vérificateur orthographique {#spelling-checker}

![](do-not-localize/cq55_rte_spellchecker.png)

Le vérificateur orthographique vérifie l’intégralité du texte dans le composant actif.

Toute faute d’orthographe est mise en surbrillance :

![cq55_rte_spellchecker_use](assets/cq55_rte_spellchecker_use.png)

>[!NOTE]
>
>Le correcteur orthographique fonctionne dans la langue du site Web soit en prenant la propriété de langue de la sous-arborescence, soit en extrayant la langue de l’URL ;  Par exemple, la vérification sera effectuée en anglais pour la branche `en`, en allemand pour la branche `de`, etc.

### Tableaux {#tables}

Les tableaux sont disponibles dans les deux cas :

* Comme la variable **Tableau** component

   ![chlimage_1-146](assets/chlimage_1-146.png)

* à l’intérieur du composant **Texte**

   ![](do-not-localize/chlimage_1-14.png)

   >[!NOTE]
   >
   >Bien que les tableaux soient disponibles dans l’éditeur de texte enrichi, il est conseillé d’utiliser le composant **Tableau** lors de leur création.

Dans les composants **Texte** et **Tableau**, la fonctionnalité de tableau est accessible par le biais du menu contextuel (qui s’ouvre généralement à l’aide du bouton droit de la souris) ; par exemple :

![cq55_rte_tablemenu](assets/cq55_rte_tablemenu.png)

>[!NOTE]
>
>Dans le **Tableau** , une barre d’outils spécialisée est également disponible, notamment diverses fonctions standard de l’éditeur de texte enrichi, ainsi qu’un sous-ensemble de fonctions spécifiques au tableau.

Les fonctions spécifiques au tableau sont les suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><a href="#table-properties">Propriétés du tableau</a><br /> </td> 
  </tr> 
  <tr> 
   <td><a href="#cell-properties">Propriétés de la cellule<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-rows">Ajouter ou Supprimer des lignes<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-columns">Ajouter ou Supprimer des colonnes<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#selecting-entire-rows-or-columns">Sélectionner des lignes ou colonnes entières<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#merge-cells">Fusionner des cellules<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#split-cells">Diviser des cellules<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#creating-nested-tables">Tableaux imbriqués</a></td> 
  </tr> 
  <tr> 
   <td><a href="#remove-table">Supprimer le tableau</a> </td> 
  </tr> 
 </tbody> 
</table>

#### Propriétés du tableau {#table-properties}

![cq55_rte_tableproperties_icon](assets/cq55_rte_tableproperties_icon.png)

Les propriétés de base du tableau peuvent être configurées avant de cliquer sur **OK** pour l’enregistrement :

![cq55_rte_tableproperties_dialog](assets/cq55_rte_tableproperties_dialog.png)

* **Largeur**

   Largeur totale du tableau.

* **Hauteur**

   Hauteur totale du tableau.

* **Bordure**

   Taille de la bordure du tableau.

* **Marge intérieure des cellules**

   Définit l’espace blanc entre le contenu de la cellule et ses bordures.

* **Espacement des cellules**

   Cette option définit la distance entre les cellules.

>[!NOTE]
>
>**Largeur**, **Hauteur** et certaines propriétés de cellule peuvent être définies dans :
>
>* pixels
>* pourcentages


>[!CAUTION]
>
>Adobe recommande vivement de définir une **Largeur** pour votre table.

#### Propriétés de la cellule {#cell-properties}

![cq55_rte_cellproperties_icon](assets/cq55_rte_cellproperties_icon.png)

Les propriétés d’une cellule spécifique ou d’une série de cellules peuvent être configurées :

![cq55_rte_cellproperties_dialog](assets/cq55_rte_cellproperties_dialog.png)

* **Largeur**
* **Hauteur**
* **Alignement horizontal** - Gauche, Centre ou Droite
* **Alignement vertical** - Haut, Milieu, Bas ou Ligne de base
* **Type de cellule** - Données ou En-tête
* **Appliquer à:**
   * Une seule cellule
   * Ligne entière
   * Colonne entière

#### Ajouter ou Supprimer des lignes {#add-or-delete-rows}

![cq55_rte_rows](assets/cq55_rte_rows.png)

Les lignes peuvent être ajoutées au-dessus ou au-dessous de la ligne actuelle.

La ligne actuelle peut également être supprimée.

#### Ajouter ou supprimer des colonnes {#add-or-delete-columns}

![cq55_rte_columns](assets/cq55_rte_columns.png)

Vous pouvez ajouter des colonnes à gauche ou à droite de la colonne active.

La colonne actuelle peut également être supprimée.

#### Sélectionner des lignes ou colonnes entières {#selecting-entire-rows-or-columns}

![chlimage_1-147](assets/chlimage_1-147.png)

Sélectionne toute la ligne ou la colonne active. Des actions spécifiques (par exemple, fusion) sont alors disponibles.

#### Fusionner des cellules {#merge-cells}

![cq55_rte_cellmerge](assets/cq55_rte_cellmerge.png) ![cq55_rte_cellmerge-1](assets/cq55_rte_cellmerge-1.png)

* Si vous avez sélectionné un groupe de cellules, vous pouvez les fusionner en une seule.
* Si une seule cellule est sélectionnée, vous pouvez la fusionner avec la cellule à droite ou en dessous.

#### Diviser des cellules {#split-cells}

![cq55_rte_cellsplit](assets/cq55_rte_cellsplit.png)

Sélectionnez une seule cellule pour la fractionner :

* Le fractionnement horizontal d’une cellule génère une nouvelle cellule à droite de la cellule active, dans la colonne active.
* Le fractionnement vertical d’une cellule génère une nouvelle cellule sous la cellule active, mais dans la ligne actuelle.

#### Création de tableaux imbriqués {#creating-nested-tables}

![chlimage_1-148](assets/chlimage_1-148.png)

La création d’un tableau imbriqué crée un tableau autonome dans la cellule active.

>[!NOTE]
>
>Certains comportements supplémentaires dépendent du navigateur :
>
>* Windows IE : Utilisez les touches Ctrl+Principal-clic-bouton-souris (généralement gauche) pour sélectionner plusieurs cellules.
>* Firefox : Faites glisser la souris pour sélectionner une plage de cellules.
>


#### Supprimer le tableau {#remove-table}

![cq55_rte_removetable](assets/cq55_rte_removetable.png)

Cette opération supprime le tableau de la section **Texte** composant.

### Caractères spéciaux {#special-characters}

![](do-not-localize/cq55_rte_specialchars.png)

Des caractères spéciaux peuvent être mis à la disposition de votre éditeur de texte enrichi ; elles peuvent varier en fonction de votre installation.

![cq55_rte_specialchars_use](assets/cq55_rte_specialchars_use.png)

Pointez la souris pour afficher une version agrandie du caractère, puis cliquez pour qu’il soit inclus à l’emplacement actuel dans votre texte.

### Mode d’édition de la source {#source-editing-mode}

![](do-not-localize/cq55_rte_sourceedit.png)

Le mode d’édition source vous permet d’afficher et de modifier le HTML sous-jacent du composant.

Donc le texte :

![cq55_rte_sourcemode_1](assets/cq55_rte_sourcemode_1.png)

Se présentera comme suit dans le mode source (la source étant bien souvent plus longue, un défilement s’avérera nécessaire) :

![cq55_rte_sourcemode_2](assets/cq55_rte_sourcemode_2.png)

>[!CAUTION]
>
>Lors de la sortie du mode source, AEM effectue certaines vérifications de validation (par exemple, s’assurer que le texte est correctement contenu/imbriqué dans des blocs). Cela peut entraîner des modifications de vos modifications.
