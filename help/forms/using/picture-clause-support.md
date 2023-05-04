---
title: Prise en charge des clauses d’image pour HTML5 forms
seo-title: Picture clause support for HTML5 forms
description: HTML5 forms prend en charge les clauses d’image XFA pour afficher la valeur et la valeur formatée de la date, du texte et des synboles numériques.
seo-description: HTML5 forms supports XFA Picture clause for display value and formatted value for date, text, and numeric symbols.
uuid: ca5074ce-8219-4f27-a37c-b1f0dca4ce03
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 5e344be7-46cd-4e1f-ae3a-1f89c645cffe
feature: Mobile Forms
exl-id: b63758f1-b375-4c05-bd53-69e0346733c6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 22%

---

# Prise en charge des clauses d’image pour HTML5 forms {#picture-clause-support-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

HTML5 forms prend en charge les clauses d’image XFA pour afficher la valeur et la valeur formatée de la date, du texte et des synboles numériques. Les expressions de clause d’image suivantes sont prises en charge :

* category(locale){picture-clause} | category(locale){picture-clause} | category(locale){picture-clause}
* category.subcategory{}

>[!NOTE]
>
>Actuellement, Mobile Forms ne prend pas en charge la clause de modification de l’image. De plus, les symboles des clauses DateTime et Time Picture ne sont pas pris en charge.

## Symboles de champ de date pris en charge {#supported-date-field-symbols}

Expression prise en charge pour la clause d’image de date :

* date.long{}
* date.short{}
* date.medium{}
* date.full{}
* date.short{}
* date{symboles de la clause d’image de date}

>[!NOTE]
>
>{MMM D, YYYY} représente le motif par défaut de la clause d’image. Si aucun modèle n’est appliqué, le modèle par défaut est utilisé.

<table> 
 <tbody>
  <tr>
   <th><strong>Symbole</strong></th> 
   <th>Interprétation</th> 
  </tr>
  <tr>
   <td>D</td> 
   <td>Jour du mois à 1 ou 2 chiffres (1-31)</td> 
  </tr>
  <tr>
   <td>DD</td> 
   <td>Jour du mois à deux chiffres avec le zéro (01-31).<br /> </td> 
  </tr>
  <tr>
   <td>M</td> 
   <td>Mois de l’année à 1 ou 2 chiffres (1-12).<br /> </td> 
  </tr>
  <tr>
   <td>MM</td> 
   <td>Mois de l’année à deux chiffres avec le zéro (01-12).<br /> </td> 
  </tr>
  <tr>
   <td>MMM</td> 
   <td>Nom abrégé du mois dans la langue courante<br /> </td> 
  </tr>
  <tr>
   <td>MMMM</td> 
   <td>Nom complet du mois dans la langue courante<br /> </td> 
  </tr>
  <tr>
   <td>EEE</td> 
   <td>Nom abrégé du jour de la semaine dans la langue courante<br /> </td> 
  </tr>
  <tr>
   <td>EEEE</td> 
   <td>Nom complet du jour de la semaine dans la langue courante<br /> </td> 
  </tr>
  <tr>
   <td>AA</td> 
   <td>Année à 2 chiffres, où 00 = 2000, 29 = 2029, 30 = 1930 et 99 = 1999<br /> </td> 
  </tr>
  <tr>
   <td>AAAA</td> 
   <td>Année à 4 chiffres<br /> </td> 
  </tr>
 </tbody>
</table>

## Clause d’image numérique {#numeric-picture-clause}

Les formulaires HTML5 prennent en charge les symboles d’image numérique. Cependant, il existe une différence dans la prise en charge entre les PDF forms et HTML Forms.

Dans **PDF forms**, un nombre est formaté quel que soit le nombre de symboles contenus dans la clause d’image.

Dans **HTML Forms**, un nombre n’est formaté que s’il contient des chiffres inférieurs au nombre de symboles dans la clause d’image.

**Exemple**: Considérons une clause d’image : num{zzz,zzz,zz9}.

Nombre **10 000** est formaté en tant que **10 000** en HTML et en PDF forms.

Le nombre 1000000 est formaté au format 1 000 000 en PDF forms. Toutefois, dans HTML Forms, le nombre n’est pas formaté comme 1000000.

Expressions prises en charge pour la clause d’image numérique dans les **formulaires HTML** :

* num.integer{}
* num.decimal{}
* num.currency{}
* num.percent{}
* num{symboles de la clause d’image numérique}

<table> 
 <tbody>
  <tr>
   <th><strong>Symbole</strong></th> 
   <th><strong>Interprétation</strong></th> 
   <th>Analyse des entrées</th> 
  </tr>
  <tr>
   <td>9</td> 
   <td><strong>Formatage des valeurs</strong>: un seul chiffre. Ou pour le chiffre zéro si les données d’entrée sont vides ou un espace à la position correspondante.<br /> </td> 
   <td>Chiffre simple</td> 
  </tr>
  <tr>
   <td>z</td> 
   <td><strong>Formatage des valeurs</strong>: un seul chiffre. Ou pour un espace si les données d’entrée sont vides, un espace ou le chiffre zéro à la position correspondante.<br /> </td> 
   <td>Un seul chiffre ou un espace</td> 
  </tr>
  <tr>
   <td>z</td> 
   <td><strong>Formatage des valeurs</strong>: un seul chiffre. Ou pour rien si les données d’entrée sont vides, un espace ou le chiffre zéro à la position correspondante.<br /> </td> 
   <td>Un seul chiffre ou rien</td> 
  </tr>
  <tr>
   <td>Erreurs</td> 
   <td><strong>Formatage des valeurs</strong>: la partie exposant d’un nombre à virgule flottante composée du symbole exponentiel (E). Suivi du signe plus ou moins facultatif. Suivi de la valeur de l’exposant.<br /> </td> 
   <td>Identique au formatage des valeurs de sortie</td> 
  </tr>
  <tr>
   <td>CR ou cr<br /> </td> 
   <td>Symbole du crédit (CR) si le nombre est négatif. Sinon rien.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>S ou s<br /> </td> 
   <td>Formatage des sorties : un signe moins si le nombre est négatif. Sinon un espace.<br /> </td> 
   <td>Signe moins si le nombre est négatif. Signe plus si le nombre est positif</td> 
  </tr>
  <tr>
   <td>V</td> 
   <td>Base décimale du jeu de paramètres régionaux dominant. Permet d’indiquer la base décimale lors de l’analyse de l’entrée.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>v</td> 
   <td>Base décimale du jeu de paramètres régionaux dominant. Permet d’indiquer la base décimale lors de l’analyse des entrées et de la mise en forme des sorties.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>.</td> 
   <td>Base décimale du jeu de paramètres régionaux dominant.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>, (U+FF0C)</td> 
   <td>Séparateur d’un groupe de valeurs du jeu de paramètres régionaux dominant.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>$ (U+FF04)</td> 
   <td>Symbole de devise du jeu de paramètres régionaux dominant.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>% (U+FF05)</td> 
   <td>Symbole de pourcentage du jeu de paramètres régionaux dominant.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>( (U+FF08)</td> 
   <td>Parenthèse gauche si le nombre est négatif. Sinon un espace.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>) (U+FF09)</td> 
   <td>Parenthèse droite si le nombre est négatif. Sinon un espace.</td> 
   <td><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>t</td> 
   <td>Caractère de tabulation</td> 
   <td><br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

## Clause d’image de texte {#text-picture-clause}

Les formulaires HTML5 prennent en charge les expressions de clause d’image de texte suivantes :

* text{text Picture clause symbols}

| **Symbole** | **Interprétation** |
|---|---|
| A | Caractère alphabétique simple. |
| X | Caractère simple. |
| O | Caractère alphanumérique simple. |
| 0 (zéro) | Caractère alphanumérique simple. |
| 9 | Chiffre simple. |
