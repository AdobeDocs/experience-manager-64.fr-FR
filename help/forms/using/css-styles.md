---
title: Créer des styles CSS pour des formulaires HTML5
seo-title: Creating CSS styles for HTML5 forms
description: Découvrez comment modifier l’aspect des formulaires HTML5 en modifiant la classe CSS associée à l’élément de formulaire de HTML.
seo-description: Learn how to change the appearance of HTML5 forms by modifying the CSS class associated with the HTML form element.
uuid: 43c689b4-243c-43de-a8be-1eef10d75295
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a8d986ab-2a4c-488b-957e-4606f7391bd3
feature: Mobile Forms
exl-id: 9e381e71-63ff-41ab-a6ec-9f92447b65a0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 41%

---

# Créer des styles CSS pour des formulaires HTML5 {#creating-css-styles-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le rendu HTML5 d’un modèle de formulaire basé sur XFA se compose de plusieurs éléments de HTML. Ces éléments sont organisés dans un ordre. Chaque élément comporte des classes CSS bien définies. Vous pouvez utiliser cette classe CSS pour sélectionner et modifier l’aspect d’un élément.

>[!NOTE]
>
>Dans les classes CSS, ne modifiez pas la valeur des attributs de position et de taille : largeur, hauteur, épaisseur de bordure, haut, gauche, droite, bas, remplissage, marge. Toute modification des attributs de position et de taille modifie la disposition du formulaire.

## Classes CSS pour les éléments  {#css-classes-nbsp-for-elements-nbsp}

Chaque élément contient des classes CSS bien définies. Vous pouvez modifier ces classes pour modifier l’apparence d’un élément. Chaque élément, à l’exception des éléments de champ et de dessin, comporte deux classes CSS – Type et Nom.

* Le **type classe** représente le type du champ XFA. Vous pouvez remplacer la classe `type` pour modifier les styles de tous les éléments d’un type donné.

* Le **nom de classe** correspond au nom du champ XFA. Vous pouvez remplacer la classe `name` pour modifier un élément et lui appliquer un style personnalisé.

>[!NOTE]
>
>Certains éléments XFA n’ont pas de nom. Pour modifier les styles de ces composants, modifiez tous les composants de ce type particulier.

Pour les pages non mentionnées dans AEM Forms Designer, les pages d’un formulaire HTML5 sont nommées dans l’ordre croissant de leur numéro. Par exemple, pour un formulaire HTML5 comportant deux pages, les pages sont nommées Page1 et Page2.

## Elément de champ {#field-element}

L’élément de champ contient deux éléments imbriqués : widget et légende.

**Elément Widget**

L’élément widget contient l’élément d’interface utilisateur pour l’interaction avec les utilisateurs. Il a trois classes CSS :

* **Widget** : chaque widget comporte cette classe.
* **nom** : tous les widgets fournis avec AEM contiennent la classe de nom widget. Pour les widgets personnalisés, le développeur de widgets fournit la classe de nom Widget.
* **type** : chaque widget comporte un élément d’interface utilisateur. Cette classe définit le type de l’élément d’interface utilisateur. 

```xml
<!--field with caption-->
<div class="field numericfield NumericField3 ">
     <div class="caption">
        caption content
     </div>
     <div class="widget numericfieldwidget numericInput">
       widget content
     </div>
</div>
 
<!--field without caption-->
<div class="widget numericfieldwidget numericInput">
   widget content
</div>
```

Outre la classe de type et de nom, le composant de champ contient également une classe CSS supplémentaire nommée **subtype**. Un sous-type identifie le type de champ, par exemple NumericField, DateField, TextField. Vous pouvez remplacer la classe subtype pour modifier le style de tous les champs de type, sous-type.

## Classes CSS des différents composants {#css-classes-for-different-components}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Composant</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Nom</strong></td> 
  </tr> 
  <tr> 
   <td>Page</td> 
   <td>page</td> 
   <td>Nom défini par l’utilisateur<br /> ou<br /> Page&lt;pagenumber&gt; (par défaut)</td> 
  </tr> 
  <tr> 
   <td>Zone de contenu</td> 
   <td>contentarea</td> 
   <td>Nom défini par l’utilisateur</td> 
  </tr> 
  <tr> 
   <td>Sous-formulaire</td> 
   <td>sous-formulaire</td> 
   <td>Nom défini par l’utilisateur</td> 
  </tr> 
  <tr> 
   <td>Groupe d’exclusion</td> 
   <td>exclgroup</td> 
   <td>Nom défini par l’utilisateur</td> 
  </tr> 
  <tr> 
   <td>Draw</td> 
   <td>draw</td> 
   <td>Nom défini par l’utilisateur</td> 
  </tr> 
  <tr> 
   <td>Champ</td> 
   <td>field</td> 
   <td>Nom défini par l’utilisateur</td> 
  </tr> 
  <tr> 
   <td>Légende</td> 
   <td>caption</td> 
   <td>s.o.</td> 
  </tr> 
  <tr> 
   <td>Widget</td> 
   <td>widget</td> 
   <td>Le développeur du widget le définit (pour les widgets définis par l’utilisateur, reportez-vous au tableau de la section suivante).</td> 
  </tr> 
 </tbody> 
</table>

## Classes CSS des différents champs {#css-classes-for-different-fields}

AEM Forms Designer prend en charge différents types de champs d’un formulaire, tels que NumericField, DecimalField et le champ Date. Tous ces champs en HTML contiennent les classes CSS mentionnées ci-dessus. Elles contiennent également des classes supplémentaires en fonction du type de champ.

Chaque champ est associé à un widget représentant l’élément de l’interface utilisateur. Les classes de chaque champ et les widgets associés à chaque champ sont répertoriés ci-dessous.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Type de champ</strong></td> 
   <td><strong>Sous-type</strong></td> 
   <td><strong>Nom du widget</strong></td> 
   <td><strong>Type de widget</strong></td> 
   <td><strong>Balise d’interface utilisateur HTML</strong></td> 
  </tr> 
  <tr> 
   <td>Bouton<br type="_moz" /> </td> 
   <td>s.o.</td> 
   <td>xfaButton<br type="_moz" /> </td> 
   <td>buttonfieldwidget<br type="_moz" /> </td> 
   <td>input type=button<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>CheckButton<br type="_moz" /> </td> 
   <td>checkboxfield<br /> </td> 
   <td>XfaCheckBox<br type="_moz" /> </td> 
   <td>checkboxfieldwidget<br type="_moz" /> </td> 
   <td>input type=checkbox<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>DateField<br type="_moz" /> </td> 
   <td>datefield<br type="_moz" /> </td> 
   <td>dateField<br type="_moz" /> </td> 
   <td>datefieldwidget<br type="_moz" /> </td> 
   <td>inputtype = text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>DateTimeField<br type="_moz" /> </td> 
   <td>textfield<br type="_moz" /> </td> 
   <td>textField<br type="_moz" /> </td> 
   <td>textfieldwidget</td> 
   <td>inputtype = text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>DecimalField<br type="_moz" /> </td> 
   <td>numericfield<br type="_moz" /> </td> 
   <td>numericInput<br type="_moz" /> </td> 
   <td>numericfieldwidget<br type="_moz" /> </td> 
   <td>inputtype = text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>DropDown<br type="_moz" /> </td> 
   <td>choicelist<br type="_moz" /> </td> 
   <td>dropDownListWidget<br type="_moz" /> </td> 
   <td>choicelistwidget<br type="_moz" /> </td> 
   <td>select</td> 
  </tr> 
  <tr> 
   <td>ListBox<br type="_moz" /> </td> 
   <td>choicelist<br type="_moz" /> </td> 
   <td>listBoxWidget<br type="_moz" /> </td> 
   <td>choicelistwidget<br type="_moz" /> </td> 
   <td>ol</td> 
  </tr> 
  <tr> 
   <td>NumericField<br type="_moz" /> </td> 
   <td>numericfield<br type="_moz" /> </td> 
   <td>numericInput<br type="_moz" /> </td> 
   <td>numericfieldwidget<br type="_moz" /> </td> 
   <td>inputtype = text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>PasswordField<br type="_moz" /> </td> 
   <td>passwordfield<br type="_moz" /> </td> 
   <td>defaultWidget<br type="_moz" /> </td> 
   <td>passwordfieldwidget<br type="_moz" /> </td> 
   <td>input type=password<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>RadioButton<br type="_moz" /> </td> 
   <td>radiofield<br type="_moz" /> </td> 
   <td>XfaCheckBox<br type="_moz" /> </td> 
   <td>radiofieldwidget<br type="_moz" /> </td> 
   <td>input type=radio<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>TextField<br type="_moz" /> </td> 
   <td>textfield<br type="_moz" /> </td> 
   <td>textField<br type="_moz" /> </td> 
   <td>textfieldwidget<br type="_moz" /> </td> 
   <td>inputtype = text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>TimeField<br type="_moz" /> </td> 
   <td>textfield<br type="_moz" /> </td> 
   <td>textField<br type="_moz" /> </td> 
   <td>textfieldwidget<br type="_moz" /> </td> 
   <td>inputtype = text<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

## Classes CSS des différents éléments de dessin {#css-classes-for-different-draw-elements}

Vous pouvez insérer des éléments statiques de dessin comme un texte et des images à l’aide d’AEM Forms Designer. Pour chaque élément de dessin, une classe CSS distincte est associée à cet élément. La liste des classes CSS pour les éléments draw est ci-dessous. Chaque élément draw est associé à une classe draw.

| **Type de dessin** | **Classe CSS** |
|---|---|
| Texte | text |
| Image | image |
| Rectangle | rectangle |
| Line | ligne |

## Style des autres parties du formulaire {#styling-other-parts-of-the-form}

Outre l’aspect des composants de l’interface utilisateur dans le formulaire HTML, vous pouvez modifier le style des éléments comme les erreurs en ligne, les avertissements en ligne et les champs contenant des erreurs de validation.

`Styling Inline Errors`

Lorsque la validation d&#39;un champ génère une erreur, une erreur insérée s&#39;affiche lorsque le champ est principal. Pour modifier le style des erreurs intégrées, remplacez l’identifiant CSS. **error-msg**.

`Styling Inline Warnings`

Lorsque la validation d’un champ génère un avertissement, un avertissement intégré s’affiche lorsque le champ est principal. Pour modifier le style de ces avertissements intégrés, remplacez l’identifiant CSS. **warning-msg**.

`Styling Fields with Validation Errors`

Lorsque la fonction de validation d’un champ échoue, le style du widget change. Cette modification du style est effectuée en appliquant une classe CSS **widgetError** au composant widget. Pour modifier le style par défaut, remplacez la classe **widgetError**.
