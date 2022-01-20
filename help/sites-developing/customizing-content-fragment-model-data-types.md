---
title: NE PAS PUBLIER, MAIS NE PAS DELETE la personnalisation des types de données pour les modèles de fragment de contenu
seo-title: Customizing Data Types for Content Fragment Models
description: Les types de données utilisés dans les modèles de fragment de contenu peuvent être personnalisés.
seo-description: Data types used in Content Fragment Models can be customized.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 2%

---


# NE PAS PUBLIER, MAIS NE PAS DELETE la personnalisation des types de données pour les modèles de fragment de contenu{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Fragments de contenu](/help/assets/content-fragments.md) sont basées sur [modèles de fragment de contenu](/help/assets/content-fragments-models.md). Ces modèles sont construits à partir de [elements](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) de différents types de données.

Plusieurs types de données sont disponibles prêts à l’emploi, notamment le texte sur une seule ligne, le texte enrichi sur plusieurs lignes, les champs numériques, les sélecteurs booléens, les options de menu déroulant, la date et l’heure, etc. AEM utilisateurs peuvent sélectionner des types de données en fonction de l’intention éditoriale du ou des fragments correspondants. Cela vous permet de prendre en charge des modèles de texte simples jusqu’à des modèles complexes avec différents types de contenu et l’expérience de création de fragments associée.

Les types de données sont définis par une [combinaison des propriétés de noeud](#properties) tenu dans [emplacements spécifiques dans le référentiel](#locations-in-the-repository). Vous pouvez également créer les vôtres [types de données](#creating-your-data-type) et [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Emplacements dans le référentiel {#locations-in-the-repository}

Tous les types de données d’usine sont déclarés sous :

`/libs/settings`

Vous pouvez ajouter de nouveaux types de données en recouvrant la structure de noeud comme suit sous `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>Vous ne devez rien modifier dans le chemin `/libs`. 
>
>Tout ce qui s’y trouve risque d’être modifié lors de la prochaine mise à niveau ou de l’installation d’un service ou d’un pack de correctifs.

## Propriétés {#properties}

Les propriétés de noeud sont utilisées pour définir les types de données :

* [Propriétés des types de données](#data-type-properties)
* et à l’intérieur de ceux-ci [fieldProperties](#fieldproperties)

### Propriétés du type de données {#data-type-properties}

Tous les types de données sont représentés dans une structure de noeud comme sous :

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Chaque noeud sous `/items` possède des propriétés qui définissent la manière dont ce type de données doit être représenté dans l’éditeur de modèles.

Toutes les propriétés suivantes doivent être présentes pour que le type de données soit présent dans l’éditeur de modèles :

* `fieldIcon`

   [Icône CoralUI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) pour représenter le type de données dans l’interface utilisateur de l’éditeur de modèles.

* ` [fieldProperties](#fieldproperties)`

   Tableau représentant les propriétés de configuration pour chaque type de données.

* `fieldResourceType`

   Type de ressource Sling utilisé pour effectuer le rendu du type de données dans un fragment de contenu. Pour les types de données qui peuvent être rendus de différentes manières (par exemple, sous la forme d’une saisie de texte simple et/ou d’une entrée de texte multiligne), cette propriété doit être créée sous la forme d’un tableau, contenant tous les types de ressources. Le `renderasfield` sera ajoutée automatiquement à `fieldProperties` pour permettre à l&#39;utilisateur de choisir le type de ressource à ajouter au modèle,

* `fieldPropResourceType`

   Type de ressource Sling utilisé pour effectuer le rendu de la propriété par défaut pour le type de données.

   Par exemple, pour le type de données :

   * Une seule ligne de texte, `fieldPropResourceType` serait un `textfield` component
   * Booléen, la variable `fieldPropResourceType` serait un `checkbox` component

* `fieldViewResourceType`

   Type de ressource Sling utilisé pour effectuer le rendu du type de données dans l’aperçu lors de la création du modèle. Lorsque l’utilisateur fait glisser le type de données sur le côté gauche de l’éditeur de modèles, la variable `fieldViewResourceType` représente le composant qui y est rendu. Cette option est utilisée dans les cas où vous ne souhaitez pas effectuer le rendu du composant complet, mais souhaitez uniquement effectuer le rendu d’un substitut qui minimise la surcharge dans l’éditeur de modèles.

* `fieldTitle`

   Propriété qui définit le titre de ce type de données. Par exemple : **Texte sur une seule ligne** pour un `textfield` composant, **Texte multi-lignes** pour un composant multichamp.

* `valueType`

   Il s’agit du type de valeur que le type de données renvoie lorsqu’il est stocké en interne. Voir [Mappages](#mappings).

* `renderType`

   Il s’agit d’une représentation interne du type de données. Il connecte la variable `valueType` à un composant d’interface utilisateur. Voir [Mappages](#mappings).

* `listOrder`

   Chaque type de données a besoin d’une valeur qui représente son ordre dans la liste. Elle permet d’assurer l’ordre correct des différents champs (ajoutés/déplacés par glisser-déposer) lors de l’enregistrement de l’éditeur de modèles. Cette valeur doit être un entier et il est recommandé d’attribuer le nombre de manière ascendante et ordonnée. Lors de la création d’un nouveau type de données, il est préférable d’attribuer la valeur en fonction du dernier type de données de la liste (la valeur la plus élevée de `listOrder` présente dans les types de données).

#### Mappages {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>Type de données<br /> </td> 
   <td>Type de valeur<br /> </td> 
   <td>Type de rendu</td> 
  </tr> 
  <tr> 
   <td>Une seule ligne de texte</td> 
   <td>chaîne</td> 
   <td>text-single</td> 
  </tr> 
  <tr> 
   <td>Plusieurs lignes de texte</td> 
   <td>chaîne, avec type de contenu<br /> </td> 
   <td>text-multi</td> 
  </tr> 
  <tr> 
   <td>Nombre (entier/long)<br /> </td> 
   <td>long</td> 
   <td>nombre</td> 
  </tr> 
  <tr> 
   <td>Nombre (double/flottant)</td> 
   <td>double</td> 
   <td>nombre</td> 
  </tr> 
  <tr> 
   <td>Booléen</td> 
   <td>booléen</td> 
   <td>booléen</td> 
  </tr> 
  <tr> 
   <td>Date et heure</td> 
   <td>calendar</td> 
   <td>l’heure.</td> 
  </tr> 
  <tr> 
   <td>Énumération</td> 
   <td>string/long</td> 
   <td>enumeration</td> 
  </tr> 
  <tr> 
   <td>Balises</td> 
   <td>chaîne</td> 
   <td>tags</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Certains types (par exemple, `string`, `long`, entre autres) peut comporter plusieurs valeurs. Dans ce cas, le composant utilisé pour le rendu et la modification est généralement encapsulé par un composant multichamp ( `granite/ui/components/coral/foundation/form/multifield`). L’exception concerne les balises, où le composant d’édition est responsable du rendu correct.

### fieldProperties {#fieldproperties}

Les propriétés de configuration pour chaque type de données. Valeurs de `fieldProperties`:

* `base`

   C&#39;est la base de tout `fieldProperties` composants. La définition se trouve sous `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Contient la variable `fieldRoot`, qui suit `fieldProperties` peut utiliser lors de la création d’entrées pour récupérer le chemin correct.

   Exemple : pour obtenir le chemin correct pour une **Libellé du champ** Si vous avez besoin de la clé pour identifier le composant auquel il appartient, l’entrée de ce champ doit être `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Ce composant ajoute la case à cocher par défaut pour la variable `Boolean` type de données, ainsi que les paramètres Sling `checked@Delete` et `checked@TypeHint`.

* `datepickerfields`

   Composant qui ajoute les entrées masquées nécessaires au fonctionnement du composant de sélecteur de date. Inclut la création des propriétés `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` et `maxDate`.

* `datetimepickerfields`

   Cela ajoute un champ de sélection pour `Date&Time` type de données à distinguer `Date` et `Date&Time` options.

* `datevaluefield`

   Un sélecteur de données est ainsi ajouté aux propriétés, de sorte qu’un utilisateur puisse sélectionner une valeur par défaut pour la variable `Date&Time` type de données.

* `descriptionfield`

   Ce composant ajoute un champ de texte multiligne qui représente la description du composant actuellement sélectionné dans l’éditeur multiligne. Il est automatiquement ajouté par le moteur de rendu de l’éditeur de modèles à la fin de chaque propriété de type de données.

* `labelfield`

   Composant qui ajoute une `textfield` entrée qui ajoute le libellé du champ pour un type de données pouvant avoir des libellés de champ.

* `maptopropertyfield`

   Ce composant ajoute le `Name` dans les propriétés, en fournissant un identifiant au composant sélectionné d’un type de données. Il doit être présent dans tous les types de données.

* `maxlengthfield`

   Il est utilisé pour ajouter la variable `maxLength` à utiliser avec les types de données qui acceptent cette propriété. Par exemple, avec **Une seule ligne de texte**, **Nombre**, etc.

* `multieditorfield`

   Cela ajoute tous les champs masqués nécessaires au fonctionnement de l’éditeur multiligne, qui est représenté par la fonction **Texte multiligne** type de données.

* `mvfields`

   Composant qui ajoute tous les champs masqués nécessaires au fonctionnement d’un composant multichamp. Par exemple, pour la deuxième option d’une **Une seule ligne de texte** type de données. Cela doit être ajouté pour tout composant rendu sous la forme d’un champ multiple.

* `numbertypefield`

   Sélectionnez l’option pour le **Nombre** type de données qui effectue une sélection entre **Entier** ou **Fraction** pour le **Nombre** type de données.

* `numbervaluefield`

   A `numberfield` sélecteur de valeurs par défaut pour la variable **Nombre** `type.options` Les options saisies pour la variable **Énumération** type de données, utilisé pour déterminer les valeurs du composant de zone de sélection.

* `placeholderfield`

   Il s’agit d’un champ de texte qui sert d’entrée pour la variable `emptyText` d’un composant. Il doit être utilisé par tous les types de données qui acceptent un espace réservé (ce qui n’est pas très compliqué ; Par exemple : **Une seule ligne de texte**, **Nombre**, etc.).

* `renderasfield`

   Il s’agit du composant rendu automatiquement lorsque plusieurs `fieldResourceTypes` sont présents dans la propriété du noeud de type de données.

* `requiredfield`

   Il s’agit d’une case à cocher qui représente la variable `required` pour un composant. Parce que la plupart des composants acceptent la variable `required` , ce champ peut être utilisé pour la plupart des types de données.

* `tagsfields`

   Composants qui ajoutent les entrées nécessaires à un `tagfield` composant à rendre, utilisé par la fonction **Balises** type de données.

* `tagsroot`

   Un sélecteur de chemin utilisé par la variable **Balises** type de données pour définir le chemin d’accès racine pour `tagsfield` composant.

* `textfield`

   Utilisé par le `Boolean` type de données pour définir le libellé du champ de la case à cocher définie par ce type de données.

* `textvaluefield`

   La propriété de valeur par défaut pour **Une seule ligne de texte** type de données.

## Création de votre type de données {#creating-your-data-type}

Pour créer votre propre type de données, vous devez :

* [Création de la structure de noeud](#creating-the-node-structure)
* [Définition des propriétés de votre type de données](#defining-the-properties-for-your-data-type)

Vous pouvez alors [utiliser votre type de données ;](#using-your-data-type).

Vous pouvez également [créer le vôtre `fieldProperties`](#creating-your-own-fieldproperties-property).

### Création de la structure de noeud {#creating-the-node-structure}

La structure de noeud doit être créée sous `/apps` afin de superposer les types de données. S’il n’existe pas déjà, vous devez créer :

1. S’il n’existe pas déjà, vous devez créer :

   ```
   + apps 
     + settings
       + dam 
         + cfm (cq:Page) 
           + models (nt:folder)
             + formbuilderconfig (sling:folder)
               + datatypes (nt:unstructured)
                 + items (nt:unstructured)
   ```

   >[!NOTE]
   >
   >`/apps/settings/dam` devrait déjà exister.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` Il peut être nécessaire de créer les types de noeuds spécifiés.

1. Sous `/items` vous pouvez ajouter de nouveaux noeuds pour représenter votre ou vos nouveaux types de données :

   * Type de noeud : `nt:unstructured`
   * &quot;Propriétés : see [Définition des propriétés de votre type de données](#defining-the-properties-for-your-data-type)

### Définition des propriétés de votre type de données {#defining-the-properties-for-your-data-type}

1. Déterminer les valeurs des éléments suivants [propriétés de type de données](#data-type-properties) qui sont requis pour votre type de données :

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Elles définissent la manière dont les composants de votre type de données seront rendus. Il peut s’agir de n’importe quel composant; comprenant vos propres composants personnalisés (nécessite un ensemble correspondant de ` [fieldProperties](#fieldproperties)`).

   Définissez ces propriétés, avec les valeurs appropriées, sur le noeud correspondant à votre type de données.

1. Déterminez la variable ` [fieldProperties](#fieldproperties)` à utiliser. Cela dépend des attributs ou des propriétés que votre `fieldResourceType` besoins.

   Par exemple, un `granite/ui/components/coral/foundation/form/textfield`doit avoir une **Nom de l’étiquette**, un **Longueur maximale**, un **Texte d’espace réservé** et un **Valeur par défaut** .

   Vous pouvez choisir parmi les [fieldProperties](#fieldproperties)ou [créer vos propres propriétés ;](#creating-your-own-fieldproperties-property).

   Définissez ces propriétés, avec les valeurs appropriées, sur le noeud correspondant à votre type de données.

1. Déterminer les valeurs des éléments suivants [propriétés de type de données](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Définissez ces propriétés, avec les valeurs appropriées, sur le noeud correspondant à votre type de données.

### Utilisation de votre type de données {#using-your-data-type}

Après avoir enregistré cette structure de noeud, avec toutes les propriétés appliquées, vous pouvez ouvrir n’importe quel modèle à l’aide de l’éditeur de modèles et afficher et utiliser votre nouveau type de données.

## Création de votre propre propriété fieldProperties {#creating-your-own-fieldproperties-property}

Vous pouvez choisir parmi les [fieldProperties](#fieldproperties)ou créez les vôtres :

1. Créez un composant sous :

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Si le chemin n’existe pas, vous pouvez le créer à l’aide de la fonction `nt:folder` noeuds.

   1. Pour avoir accès aux variables, ce composant doit étendre :

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. Le composant doit pouvoir être inclus via :

      `sling:include`

   1. Ce composant doit effectuer le rendu d’un champ (si un utilisateur doit introduire des données) ou d’une entrée masquée avec les propriétés requises par votre type de données. Par exemple, un composant multichamp nécessite un noeud enfant avec le type de champ qu’il doit dupliquer. Par conséquent, il doit y avoir une entrée qui peut créer (par le biais de la mécanique de POST Sling) un noeud enfant d’un type spécifique.

1. Le nom de base de ce composant doit être ajouté à `fieldProperties`.
1. Répétez cette opération pour toutes les propriétés dont vous avez besoin.

