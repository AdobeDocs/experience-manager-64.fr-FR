---
title: NE PAS PUBLIER, MAIS NE PAS SUPPRIMER LA Personnalisation DES Types de données pour les modèles de fragments de contenu
seo-title: Personnalisation des types de données pour les modèles de fragments de contenu
description: Les types de données utilisés dans les modèles de fragments de contenu peuvent être personnalisés.
seo-description: Les types de données utilisés dans les modèles de fragments de contenu peuvent être personnalisés.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2

---


# NE PAS PUBLIER, MAIS NE PAS SUPPRIMER LA Personnalisation DES Types de données pour les modèles de fragments de contenu{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Les fragments](/help/assets/content-fragments.md) de contenu reposent sur des modèles [de fragments de](/help/assets/content-fragments-models.md)contenu. Ces modèles sont construits à partir d’ [éléments](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) de différents types de données.

Différents types de données sont disponibles prêts à l’emploi, notamment le texte sur une seule ligne, le texte enrichi sur plusieurs lignes, les champs numériques, les sélecteurs booléens, les options de menu déroulant, la date et l’heure, etc. Les utilisateurs d’AEM peuvent sélectionner des types de données en fonction de l’intention éditoriale des fragments correspondants. Cela vous permet de prendre en charge des modèles de texte simples jusqu’à des modèles complexes avec différents types de contenu et l’expérience de création de fragments associée.

Les types de données sont définis par une [combinaison de propriétés](#properties) de noeud détenues dans des emplacements [spécifiques du référentiel](#locations-in-the-repository). Vous pouvez également créer vos propres types [de](#creating-your-data-type) données et [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Emplacements dans le référentiel {#locations-in-the-repository}

Tous les types de données prêts à l&#39;emploi sont déclarés sous :

`/libs/settings`

Vous pouvez ajouter de nouveaux types de données en superposant la structure de noeud comme suit sous `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>You must not change anything in the `/libs` path.
>
>Tout ce qui existe peut changer lors de la prochaine mise à niveau ou de l&#39;installation d&#39;un service ou d&#39;un pack de correctifs.

## Propriétés {#properties}

Les propriétés de noeud sont utilisées pour définir les types de données :

* [Propriétés des types de données](#data-type-properties)
* et dans ces [propriétés field](#fieldproperties)

### Propriétés du type de données {#data-type-properties}

Tous les types de données sont représentés dans une structure de noeud comme suit :

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Chaque noeud sous `/items` possède des propriétés qui définissent la manière dont ce type de données doit être représenté dans l’éditeur de modèles.

Toutes les propriétés suivantes doivent être présentes pour que le type de données soit présent dans l’éditeur de modèles :

* `fieldIcon`

   [Icône](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) CoralUI représentant le type de données dans l’interface utilisateur de l’éditeur de modèles.

* ` [fieldProperties](#fieldproperties)`

   Tableau représentant les propriétés de configuration de chaque type de données.

* `fieldResourceType`

   Type de ressource Sling utilisé pour générer le type de données dans un fragment de contenu. Pour les types de données qui peuvent être rendus de différentes manières (par exemple, en entrée de texte simple et/ou en entrée de texte multiligne), cette propriété doit être créée sous la forme d’un tableau contenant tous les types de ressource. La `renderasfield` propriété sera ajoutée automatiquement pour `fieldProperties` permettre à l&#39;utilisateur de choisir le type de ressource qu&#39;il doit ajouter au modèle,

* `fieldPropResourceType`

   Type de ressource Sling utilisé pour générer la propriété par défaut du type de données.

   Par exemple, pour le type de données :

   * Texte d’une seule ligne, le `fieldPropResourceType` composant serait un `textfield` composant
   * Booléen, le `fieldPropResourceType` composant serait un `checkbox` composant

* `fieldViewResourceType`

   Type de ressource Sling utilisé pour effectuer le rendu du type de données dans l’aperçu lors de la création du modèle. Lorsque l’utilisateur fait glisser le type de données sur le côté gauche de l’éditeur de modèles, la `fieldViewResourceType` propriété représente le composant qui y est rendu. Cette option est utilisée dans les cas où vous ne souhaitez pas effectuer le rendu complet du composant, mais uniquement pour effectuer le rendu d’un substitut qui minimise la surcharge de l’éditeur de modèles.

* `fieldTitle`

   Propriété définissant le titre de ce type de données. Par exemple, texte **** sur une ligne pour un `textfield` composant, texte **** sur plusieurs lignes pour un composant à plusieurs champs.

* `valueType`

   Il s’agit du type de valeur que le type de données renvoie lorsqu’il est stocké en interne. Voir [Correspondances](#mappings).

* `renderType`

   Il s’agit d’une représentation interne du type de données. Il connecte le `valueType` à un composant d’interface utilisateur. Voir [Correspondances](#mappings).

* `listOrder`

   Chaque type de données a besoin d’une valeur qui représente son ordre dans la liste. Ceci permet d&#39;assurer l&#39;ordre correct des différents champs (ajoutés/déplacés par glisser-déposer) lors de l&#39;enregistrement de l&#39;éditeur de modèles. Cette valeur doit être un nombre entier et il est recommandé d’attribuer le nombre de manière croissante et ordonnée. Lors de la création d’un nouveau type de données, il est préférable d’affecter la valeur en fonction du dernier type de données de la liste (valeur la plus élevée de `listOrder` la valeur présente dans les types de données).

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
   <td>Booléen  </td> 
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
   <td>chaîne/long</td> 
   <td>énumération</td> 
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
>Certains types (par exemple `string`, `long`, entre autres) peuvent être à plusieurs valeurs. Dans ce cas, le composant utilisé pour le rendu et la modification est généralement encapsulé par un composant multichamp ( `granite/ui/components/coral/foundation/form/multifield`). L’exception concerne les balises, où le composant de modification est responsable du rendu correct.

### fieldProperties {#fieldproperties}

Propriétés de configuration pour chaque type de données. Valeurs pour `fieldProperties`:

* `base`

   C&#39;est la base de tous les `fieldProperties` composants. La définition se trouve sous `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Elle contient la variable `fieldRoot`, que `fieldProperties` vous pouvez ensuite utiliser lors de la création d’entrées pour récupérer le chemin d’accès correct.

   Exemple : pour obtenir le chemin d’accès correct pour une étiquette **de** champ, vous aurez besoin de la clé pour identifier le composant auquel elle appartient, l’entrée de ce champ doit être `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Ce composant ajoute la case à cocher par défaut pour le type de `Boolean` données, ainsi que les paramètres Sling `checked@Delete` et `checked@TypeHint`.

* `datepickerfields`

   Composant qui ajoute les entrées masquées nécessaires au fonctionnement du composant de sélecteur de date. Inclut la création des propriétés `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` et `maxDate`.

* `datetimepickerfields`

   Vous ajoutez ainsi un champ de sélection pour le type de `Date&Time` données afin de faire la distinction entre `Date` et `Date&Time` les options.

* `datevaluefield`

   Ceci ajoute un sélecteur de données aux propriétés, de sorte qu’un utilisateur puisse sélectionner un type de `Date&Time` données par défaut.

* `descriptionfield`

   Ce composant ajoute un champ de texte multiligne qui représente la description du composant actuellement sélectionné dans l’éditeur multiligne. Il est automatiquement ajouté par le rendu de l&#39;éditeur de modèle à la fin de chaque propriété de type de données.

* `labelfield`

   Composant qui ajoute une `textfield` entrée qui ajoute le libellé du champ pour un type de données pouvant avoir des libellés de champ.

* `maptopropertyfield`

   Ce composant ajoute le `Name` champ dans les propriétés, en donnant un identifiant au composant sélectionné d’un type de données. Elle doit être présente dans tous les types de données.

* `maxlengthfield`

   Il est utilisé pour ajouter la `maxLength` propriété à utiliser avec les types de données qui acceptent cette propriété. Par exemple, avec du texte **** sur une seule ligne, **un nombre**, etc.

* `multieditorfield`

   Cette opération ajoute tous les champs masqués nécessaires au fonctionnement de l’éditeur multiligne, qui est représenté par le type de données Texte **** multiligne.

* `mvfields`

   Composant qui ajoute tous les champs masqués nécessaires au fonctionnement d’un composant multichamp. Par exemple, pour la deuxième option d’un type de données Texte **** unique ligne. Ceci doit être ajouté pour tout composant rendu sous forme de champ multiple.

* `numbertypefield`

   Sélectionnez une option pour le type de données **Nombre** qui sélectionne entre **Entier** ou **Fraction** pour le type de données **Nombre.**

* `numbervaluefield`

   Sélecteur de valeurs `numberfield` par défaut pour le **nombre** . Cette opération ajoute les options saisies pour le type de données `type.options` Enumération **** , qui est utilisé pour déterminer les valeurs du composant de zone de sélection.

* `placeholderfield`

   Il s’agit d’un champ de texte qui agit comme entrée pour la `emptyText` propriété d’un composant. Il doit être utilisé par tous les types de données qui acceptent un espace réservé (ce qui n&#39;est pas très compliqué ; Par exemple, texte **** sur une seule ligne, **nombre**, etc.).

* `renderasfield`

   Il s’agit du composant rendu automatiquement lorsque plusieurs `fieldResourceTypes` sont présents dans la propriété du noeud de type de données.

* `requiredfield`

   Il s’agit d’une case à cocher qui représente la `required` propriété d’un composant. Comme la plupart des composants acceptent le `required` champ, ce champ peut être utilisé pour la plupart des types de données.

* `tagsfields`

   Composants qui ajoutent les entrées nécessaires au rendu d’un `tagfield` composant, utilisés par le type de données **Balises** .

* `tagsroot`

   Sélecteur de chemin utilisé par le type de données **Balises** pour définir le chemin racine du `tagsfield` composant.

* `textfield`

   Utilisé par le type de `Boolean` données pour définir le libellé du champ de la case à cocher définie par ce type de données.

* `textvaluefield`

   Propriété de valeur par défaut pour le type de données Texte **** sur une seule ligne.

## Création de votre type de données {#creating-your-data-type}

Pour créer votre propre type de données, vous devez :

* [Création de la structure du noeud](#creating-the-node-structure)
* [Définir les propriétés de votre type de données](#defining-the-properties-for-your-data-type)

Vous pouvez ensuite [utiliser votre type](#using-your-data-type)de données.

You can also [create your own `fieldProperties`](#creating-your-own-fieldproperties-property).

### Création de la structure du noeud {#creating-the-node-structure}

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
   >`/cfm/models/formbuilderconfig/datatypes/items` peut être nécessaire de créer les types de noeud spécifiés.

1. Sous `/items` vous pouvez ajouter de nouveaux noeuds pour représenter vos nouveaux types de données :

   * Type de noeud : `nt:unstructured`
   * &quot;Propriétés : voir [Définition des propriétés pour votre type de données](#defining-the-properties-for-your-data-type)

### Définition des propriétés de votre type de données {#defining-the-properties-for-your-data-type}

1. Déterminez les valeurs des propriétés [de type de](#data-type-properties) données suivantes requises pour votre type de données :

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`
   Elles définissent le mode de rendu des composants de votre type de données. Ils peuvent être n&#39;importe quel composant ; incluant vos propres composants personnalisés (nécessite un jeu de ` [fieldProperties](#fieldproperties)`composants correspondant).

   Définissez ces propriétés, avec les valeurs appropriées, sur le noeud pour votre type de données.

1. Déterminez le ` [fieldProperties](#fieldproperties)` à utiliser. Cela dépend des attributs ou des propriétés dont vous `fieldResourceType` avez besoin.

   Par exemple, une `granite/ui/components/coral/foundation/form/textfield`balise doit avoir un nom **de** libellé, une longueur **** maximale, un texte **** d’espace réservé et une propriété Valeur par défaut.****

   Vous pouvez choisir parmi les [propriétés](#fieldproperties)de champ prêtes à l’emploi ou [créer vos propres propriétés](#creating-your-own-fieldproperties-property).

   Définissez ces propriétés, avec les valeurs appropriées, sur le noeud pour votre type de données.

1. Déterminez les valeurs des propriétés [de type de](#data-type-properties)données suivantes :

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`
   Définissez ces propriétés, avec les valeurs appropriées, sur le noeud pour votre type de données.

### Utilisation de votre type de données {#using-your-data-type}

Après avoir enregistré cette structure de noeud, avec toutes les propriétés appliquées, vous pouvez ouvrir n’importe quel modèle avec l’éditeur de modèles et voir et utiliser votre nouveau type de données.

## Création de votre propre propriété fieldProperties {#creating-your-own-fieldproperties-property}

Vous pouvez choisir parmi les propriétés de [champ prêtes à l’emploi](#fieldproperties)ou créer les vôtres :

1. Créez un composant sous :

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Si le chemin n’existe pas, vous pouvez le créer à l’aide de `nt:folder` noeuds.

   1. Pour avoir accès aux variables, ce composant doit être étendu :

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. Le composant doit pouvoir être inclus par l’intermédiaire de :

      `sling:include`

   1. Ce composant doit effectuer le rendu d’un champ (si un utilisateur doit introduire des données) ou d’une entrée masquée avec les propriétés requises par votre type de données. Par exemple, un composant multichamp nécessite un noeud enfant avec le type de champ qu’il doit dupliquer. Par conséquent, une entrée doit créer (par le biais de la mécanique Sling POST) un noeud enfant d’un type spécifique.

1. Le nom de base de ce composant doit être ajouté à `fieldProperties`.
1. Répétez cette opération pour toutes les propriétés dont vous avez besoin.

