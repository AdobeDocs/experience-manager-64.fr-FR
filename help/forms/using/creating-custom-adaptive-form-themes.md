---
title: Créer des thèmes de formulaires adaptatifs personnalisés
seo-title: Creating custom adaptive form themes
description: Un thème de formulaire adaptatif est une bibliothèque cliente AEM que vous utilisez pour définir les styles (apparence) d’un formulaire adaptatif. Découvrez comment créer des thèmes de formulaire adaptatif personnalisés.
seo-description: An adaptive form theme is an AEM client library that you use to define the styles (look and feel) for an adaptive form. Learn how you can create custom adaptive form themes.
uuid: b25df10e-b07c-4e9d-a799-30f1c6fb3c44
content-type: reference
topic-tags: customization
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 437e6581-4eb1-4fbd-a6da-86b9c90cec89
exl-id: e6aa866f-3483-4db1-abaa-01ee585928dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 55%

---

# Création de thèmes de formulaires adaptatifs personnalisés {#creating-custom-adaptive-form-themes}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!CAUTION]
>
>AEM Forms fournit la fonctionnalité [Éditeur de thèmes](/help/forms/using/themes.md), qui permet de créer et de modifier des [thèmes](/help/forms/using/themes.md) de formulaires adaptatifs. Exécutez les étapes mentionnées dans cet article uniquement si vous avez effectué une mise à niveau à partir d’une version qui ne dispose pas de l’[Éditeur de thèmes](/help/forms/using/themes.md) et que vous possédez déjà des thèmes créés à l’aide de fichiers Less/CSS (méthode antérieure à l’Éditeur de thèmes).

## Prérequis {#prerequisites}

* Bien connaître la structure LESS (Leaner CSS)
* Création d’une bibliothèque cliente dans Adobe Experience Manager
* [Création d’un modèle de formulaire adaptatif](/help/forms/using/custom-adaptive-forms-templates.md) pour utiliser le thème que vous créez

## Thème de formulaire adaptatif {#adaptive-form-theme}

Un **thème de formulaire adaptatif** est une bibliothèque cliente AEM que vous utilisez pour définir les styles (apparence) d’un formulaire adaptatif.

Vous pouvez créer une **modèle adaptatif** et appliquez le thème au modèle. Vous pouvez ensuite utiliser ce modèle personnalisé pour créer une **formulaire adaptatif**.

![Formulaire adaptatif et bibliothèque cliente](assets/hierarchy.png)

## Pour créer un thème de formulaire adaptatif {#to-create-an-adaptive-form-theme}

>[!NOTE]
>
>La procédure suivante est décrite à l’aide d’exemples de noms pour des objets AEM tels que le noeud, les propriétés et les dossiers.
>
>Si vous procédez comme suit en utilisant les noms, le modèle résultant ressemble normalement à l’instantané suivant : 

![Aperçu d’un formulaire adaptatif avec thème Forêt](assets/thumbnail.png)
**Figure :** *Exemple de thème Forêt*

1. Créez un nœud de type `cq:ClientLibraryFolder` sous le nœud `/apps`.

   Par exemple, créez le nœud suivant :

   `/apps/myAfThemes/forestTheme`

1. Ajoutez une propriété à chaîne multi-valeur `categories` au nœud et définissez correctement sa valeur.

   Par exemple, définissez la propriété sur : `af.theme.forest`.

   ![Instantané du référentiel CRX](assets/3-2.png)

1. Ajoutez deux dossiers, `less` et `css`, et un fichier `css.txt` au nœud créé à l’étape 1 :

   * Le dossier `less` contient les fichiers de variables `less` dans lesquels vous définissez les variables `less` et les éléments `less mixins` utilisés pour gérer les styles .css.

      Ce dossier se compose de fichiers de variables `less`, de fichiers mixin `less` et de fichiers `less` de définition utilisant les mixins et les variables. Et tous ces fichiers less sont ensuite importés dans styles.less.

   * dossier`css` : contient les fichiers .css dans lesquels vous définissez les styles statiques à utiliser dans le thème.

   **Fichiers de variables less**: Il s’agit des fichiers dans lesquels vous définissez ou remplacez les variables utilisées pour définir les styles CSS.

   Les formulaires adaptatifs fournissent des variables prêtes à l’emploi définies dans les fichiers .less suivants :

   * `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less`
   * `/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   Les formulaires adaptatifs offrent également des variables tierces définies dans :

   `/apps/clientlibs/fd/af/third-party/less/variables.less`

   Vous pouvez utiliser les variables less fournies avec les formulaires adaptatifs, vous pouvez remplacer ces variables ou créer de nouvelles variables less.

   >[!NOTE]
   >
   >Lors de l’importation des fichiers du préprocesseur less, spécifiez le chemin d’accès relatif des fichiers dans l’instruction d’importation.

   Exemples de variables de remplacement :

   ```
   @button-background-color: rgb(19, 102, 44);
   @button-border-color: rgb(19, 102, 44);
   @button-border-size: 0px;
   @button-padding: 10px 15px;
   @button-font-color: #ffffff;
   ```

   Pour remplacer les variables `less` :

   1. Importez les variables de formulaire adaptatif par défaut :

      `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   1. Importez ensuite le fichier less contenant les variables remplacées.

   Exemples de définitions de nouvelles variables :

   ```
   @button-focus-bg-color: rgb(40, 208, 90);
   @button-hover-bg-color: rgb(30, 156, 67);
   ```

   **Fichiers mixin less :** Vous pouvez définir les fonctions qui acceptent les variables comme arguments. La sortie de ces fonctions correspond aux styles résultants. Utilisez ces mixins dans différents styles pour éviter de répéter les styles CSS.

   Les formulaires adaptatifs fournissent des mixins prêts à l’emploi définis dans :

   * `/apps/clientlibs/fd/af/guidetheme/common/less/adaptiveforms-mixins.less`

   Les formulaires adaptatifs offrent également des mixins tiers définis dans :

   * `/apps/clientlibs/fd/af/third-party/less/mixins.less`

   Exemple de définition de mixin : 

   ```
   .rounded-corners (@radius) {
     -webkit-border-radius: @radius;
     -moz-border-radius: @radius;
     -ms-border-radius: @radius;
     -o-border-radius: @radius;
     border-radius: @radius;
   }
   
   .border(@color, @type, @size) {
      border: @color @size @type;
   }
   ```

   **Fichier Styles.less :** Utilisez ce fichier pour inclure tous les fichiers less (variables, mixins, styles) que vous devez utiliser dans la bibliothèque cliente.

   Dans l’exemple de fichier`styles.less` suivant, les instructions d’importation peuvent être placées dans n’importe quel ordre.

   Les instructions pour importer les fichiers .less suivants sont obligatoires :

   * `globalvariables.less`
   * `layoutvariables.less`
   * `components.less`
   * `layouts.less`

   ```
   @import "../../../clientlibs/fd/af/guidetheme/common/less/globalvariables.less";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/layoutvariables.less";
   @import "forestTheme-variables";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/components.less";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/layouts.less";
   
   /* custom styles */
   
   .guidetoolbar {
     input[type="button"], button, .button {
       .rounded-corners (@button-radius);
       &:hover {
         background-color: @button-hover-bg-color;
       }
       &:focus {
         background-color: @button-focus-bg-color;
       }
     }
   }
   
   form {
       background-image: url(../images/forest.png);
    background-repeat: no-repeat;
    background-size: 100%;
   }
   ```

   Le dossier `css.txt` contient les chemins des fichiers .css à télécharger pour la bibliothèque.

   Par exemple :

   ```
   #base=/apps/clientlibs/fd/af/third-party/css
   bootstrap.css
   
   #base=less
   styles.less
   
   #base=/apps/clientlibs/fd/xfaforms/xfalib/css
   datepicker.css
   listboxwidget.css
   scribble.css
   dialog.css
   ```

   >[!NOTE]
   >
   >Le fichier styles.less n’est pas obligatoire. Cela signifie que vous n’avez pas besoin de créer ce fichier si vous n’avez défini aucun style, variable ou mixin personnalisé.
   >
   >Cependant, si vous ne créez pas de fichier style.less, dans le fichier css.txt, vous devez annuler la mise en commentaire de la ligne suivante :
   >
   >**`#base=less`**
   >
   >Et commenter la ligne suivante :
   >
   >**`styles.less`**

## Pour utiliser un thème dans un formulaire adaptatif {#to-use-a-theme-in-an-adaptive-form}

Après avoir créé un thème de formulaire adaptatif, effectuez les étapes suivantes pour utiliser ce thème dans un formulaire adaptatif : 

1. Pour inclure le thème créé dans [Création d’un thème de formulaire adaptatif](/help/forms/using/creating-custom-adaptive-form-themes.md#p-to-create-an-adaptive-form-theme-p), créez une page personnalisée de type `cq:Component`.

   Par exemple, `/apps/myAfCustomizations/myAfPages/forestPage`

   1. Ajoutez une propriété `sling:resourceSuperType` et définissez sa valeur sur `fd/af/components/page/base`.

      ![Instantané du référentiel CRX](assets/1-2.png)

   1. Pour utiliser un thème dans la page, vous devez ajouter au noeud un fichier de remplacement library.jsp.

      Vous importez ensuite le thème créé dans la section Pour créer un thème de formulaire adaptatif de cet article.

      L’exemple de fragment de code suivant importe le thème `af.theme.forest`.

      ```
      <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
      <cq:includeClientLib categories="af.theme.forest"/>
      ```

   1. **Facultatif** : dans la page personnalisée, remplacez les fichiers header.jsp, footer.jsp, et body.jsp le cas échéant.

1. Créez un modèle personnalisé (par exemple, `/apps/myAfCustomizations/myAfTemplates/forestTemplate`) dont le fichier jcr:content désigne la page personnalisée créée à l’étape précédente (par exemple, `myAfCustomizations/myAfPages/forestPage)`.

   ![Instantané du référentiel CRX](assets/2-1.png)

1. Créez un formulaire adaptatif à l&#39;aide du modèle créé à l&#39;étape précédente. L’aspect du formulaire adaptatif est défini par le thème créé dans la section Pour créer un thème de formulaire adaptatif de cet article.
