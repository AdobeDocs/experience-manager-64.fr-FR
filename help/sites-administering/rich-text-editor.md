---
title: Configuration de l’éditeur de texte enrichi
description: Apprenez à configurer l’éditeur de texte enrichi d’AEM.
contentOwner: AG
exl-id: 2d5e9ada-1567-43dc-ab19-6891e20e1d0b
source-git-commit: 160f403d2ec9bfbede75fac2c4315314f98ab27e
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 81%

---

# Configuration de l’éditeur de texte enrichi {#configure-the-rich-text-editor}

L’éditeur de texte enrichi met à la disposition des auteurs de nombreuses fonctionnalités pour modifier leur contenu textuel. Les icônes, les boîtes de dialogue de sélection, la barre d’outils et les menus apportent une expérience WYSIWYG de la modification des textes.

Pour savoir comment utiliser les fonctions de l’éditeur de texte enrichi pour la création, voir [Utilisation de l’éditeur de texte enrichi pour la création](/help/sites-authoring/rich-text-editor.md). L’éditeur de texte enrichi peut être configuré pour activer, désactiver et étendre les fonctions disponibles dans les composants de création. Le workflow suivant illustre l’ordre recommandé d’exécution des tâches de configuration de l’éditeur de texte enrichi dans Experience Manager.

![Workflow type de configuration de l’éditeur de texte enrichi](assets/rte_workflow_v1.png)

*Figure : Workflow type de configuration de l’éditeur de texte enrichi*

## Présentation des IU tactile et classique {#understand-touch-enabled-ui-and-classic-ui}

L’IU tactile est l’IU standard d’AEM. Adobe a introduit l’interface utilisateur tactile avec [responsive design](/help/sites-authoring/responsive-layout.md) pour l’environnement de création, dans la version 5.6. L’interface utilisateur tactile est conçue pour les appareils tactiles et de bureau. L’IU diffère considérablement de l’IU classique original.

![Barre d’outils d’éditeur de texte enrichi dans l’IU tactile](assets/chlimage_1-404.png)

*Figure : Barre d’outils de l’éditeur de texte enrichi dans l’IU tactile*

![Barre d’outils d’éditeur de texte enrichi dans l’IU classique](assets/rtedefault.png)

*Figure : Barre d’outils de l’éditeur de texte enrichi dans l’interface utilisateur classique*

>[!MORELIKETHIS]
>
>* [Recommandations relatives aux IU](/help/sites-deploying/ui-recommendations.md)
>* Concernant l’obsolescence de l’IU classique, voir les [Notes de mise à jour d’AEM 6.4](/help/release-notes/deprecated-removed-features.md)
>* Pour connaître la différence entre les interfaces utilisateur, voir [IU tactile et IU classique](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
>* Pour comprendre l’IU tactile dans le détail, voir [Concepts de l’IU tactile d’AEM](/help/sites-developing/touch-ui-concepts.md)


## Différents modes de modification {#editingmodes}

Les auteurs peuvent créer et modifier du contenu textuel dans AEM en utilisant les différents modes des composants. Les options de la barre d’outils pour la création et la mise en forme du contenu, et l’expérience utilisateur des composants compatibles avec l’éditeur de texte enrichi dans différents modes de modification, varient en fonction des configurations d’éditeur de texte enrichi.

| Mode de modification | Zone de modification | Fonctions dont l’activation est recommandée | IU tactile | IU classique |
|--- |--- |--- |--- |--- |
| En ligne | Modification en ligne pour des modifications rapides et mineures ; mettez en forme sans ouvrir une boîte de dialogue | Fonctions minimales d’éditeur de texte enrichi | O | O |
| Éditeur de texte enrichi en plein écran | Couvre la page entière | Toutes les fonctions requises d’éditeur de texte enrichi | O | N |
| Boîte de dialogue | Boîte de dialogue située en haut du contenu de page sans couvrir la page entière | Toutes les fonctions requises d’éditeur de texte enrichi dans l’IU classique ; activez les fonctions judicieusement dans l’IU tactile | O | O |
| Boîte de dialogue plein écran | Identique au mode plein écran ; contient des champs de la boîte de dialogue à côté de l’éditeur de texte enrichi | Toutes les fonctions requises d’éditeur de texte enrichi | O | N |

>[!NOTE]
>
>La fonction de modification de la source n’est pas disponible en mode de modification en ligne dans l’interface utilisateur tactile. Vous ne pouvez pas faire glisser les images en mode plein écran. Toutes les autres fonctions sont utilisables dans tous les modes.

### Modification en ligne {#inline-editing}

Une fois ouvert (avec une double pression ou un double clic lent), le contenu peut être modifié dans la page. Une barre d’outils compacte avec des options de base est présentée.

![Modification en ligne avec une barre d’outils de base dans l’IU tactile](assets/chlimage_1-405.png)

*Figure : Modification en ligne avec une barre d’outils de base dans l’interface utilisateur tactile*

Dans l’IU classique, un double clic lent sur le composant permet la modification en ligne, et le contenu est encadré en orange. Si l’outil de recherche de contenu est ouvert, une barre d’outils avec les options de mise en forme disponibles de l’éditeur de texte enrichi est affichée en haut de la fenêtre. Si l’outil de recherche n’est pas ouvert, les options de mise en forme n’apparaissent pas, et vous pouvez uniquement effectuer des modifications de base sur le texte.

### Modification en plein écran {#full-screen-editing}

Les composants AEM peuvent être ouverts dans une vue plein écran qui masque le contenu de la page et occupe l’écran disponible. Considérez la modification en plein écran comme une version détaillée de la modification en ligne, car elle offre le plus grand nombre d’options de modification. Vous pouvez l’ouvrir en cliquant sur ![rte_fullscreen](assets/rte_fullscreen.png), dans la barre d’outils compacte lorsque vous utilisez le mode de modification en ligne. 

Le mode de boîte de dialogue plein écran affiche une barre d’outils détaillée d’éditeur de texte enrichi, ainsi que les options et les composants disponibles en mode de boîte de dialogue. Il s’applique seulement aux boîtes de dialogue qui contiennent l’éditeur de texte enrichi à côté d’autres composants.

![Barre d’outils détaillée d’éditeur de texte enrichi lors de la modification en plein écran dans l’IU tactile](assets/chlimage_1-406.png)

*Figure : Barre d’outils détaillée de l’éditeur de texte enrichi lors de la modification en mode plein écran dans l’interface utilisateur tactile*

### Modification dans une boîte de dialogue {#dialog-editing}

Lorsque vous double-cliquez sur un composant dans l’IU classique, une boîte de dialogue s’ouvre pour modifier le contenu. La boîte de dialogue s’ouvre dans la partie supérieure de la page existante. Dans quelques scénarios spécifiques, la boîte de dialogue s’affiche comme fenêtre contextuelle. Par exemple, quand un composant Texte fait partie d’une colonne dans une mise en page à plusieurs colonnes et que la zone disponible pour la boîte de dialogue est moindre.

![Mode de modification dans une boîte de dialogue dans l’IU tactile](assets/dialog_editing_modetouchui.png)

*Figure : Mode de modification des boîtes de dialogue dans l’IU tactile*

![Zone de dialogue dans l’IU classique qui contient la barre d’outils détaillée pour la modification](assets/chlimage_1-407.png)

*Figure : Boîte de dialogue de l’interface utilisateur classique contenant une barre d’outils détaillée pour la modification*

## À propos des modules externes de l’éditeur de texte enrichi et des fonctions associées {#aboutplugins}

Cette fonctionnalité est mise à disposition par le biais d’une série de modules externes, comportant chacun :

* A `features` property:

   * utilisée afin d’activer ou de désactiver une fonctionnalité de base pour ce module externe ;
   * configurable selon une procédure normalisée.

* Le cas échéant, des propriétés et des options supplémentaires nécessitant une configuration spécialisée.

Les fonctions de base d’éditeur de texte enrichi sont activées, ou désactivées, par la valeur de la propriété `features` sur un nœud spécifique au module externe approprié.

Le tableau ci-dessous répertorie les modules externes actuels et indique les informations suivantes :

* Les ID des modules externes avec un lien vers la documentation des API. L’ID est utilisé comme nom de nœud lors de l’[activation d’un module externe](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin).
* Les valeurs admises pour la propriété `features`.
* Une description de la fonctionnalité fournie par le module externe.

| ID du module externe | features | Description |
|--- |--- |--- |
| edit | cut copy paste-default paste-plaintext paste-wordhtml | [Couper, copier et les trois modes de collage](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles). |
| [findreplace](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | find replace | Rechercher et remplacer. |
| [format](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | bold italic underline | [Mise en forme textuelle de base](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles). |
| [image](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | image | Prise en charge de base des images (faire glisser à partir du contenu ou de l’outil de recherche de contenu). Selon le navigateur, la prise en charge présente différents comportements pour les auteurs |
| [keys](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | Pour définir cette valeur, voir [taille de tabulation](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tab-size). |
| [justify](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justifyleft justifycenter justifyright | Alignement de paragraphe. |
| [links](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | modifylink unlink anchor | [Liens hypertextes et ancres](/help/sites-administering/configure-rich-text-editor-plug-ins.md#link-styles). |
| [lists](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | ordered unordered indent outdent | Ce module externe contrôle à la fois la [mise en retrait et les listes](/help/sites-administering/configure-rich-text-editor-plug-ins.md#indent-margin), y compris les listes imbriquées. |
| [misctools](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | specialchars sourceedit | Divers outils permettent aux auteurs de saisir des [caractères spéciaux](/help/sites-administering/configure-rich-text-editor-plug-ins.md#special-char) ou de modifier la source HTML. En outre, vous pouvez ajouter toute une gamme de [caractères spéciaux](/help/sites-administering/configure-rich-text-editor-plug-ins.md#define-range-char) si vous voulez définir votre propre liste. |
| Paraformat | paraformat | Les formats de paragraphe par défaut sont : Paragraphe, En-tête 1, En-tête 2 et En-tête 3 (`<p>`, `<h1>`, `<h2>` et `<h3>`). Vous pouvez [ajouter davantage de formats de paragraphe](/help/sites-administering/configure-rich-text-editor-plug-ins.md#para-formats) ou prolonger la liste. |
| spellcheck | checktext | [Vérificateur orthographique sensible à la langue](/help/sites-administering/configure-rich-text-editor-plug-ins.md#add-dict). |
| styles | styles | Prise en charge de l’application d’un style en utilisant une classe CSS. [Ajoutez de nouveaux styles de texte](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles) si vous voulez ajouter (ou étendre) votre propre gamme de styles utilisables avec du texte. |
| subsuperscript | subscript superscript | Extensions des formats de base, en ajoutant l’indice et l’exposant. |
| table | table removetable insertrow removerow insertcolumn removecolumn cellprops mergecells splitcell selectrow selectcolumns | Voir [Configuration des styles de tableau](/help/sites-administering/configure-rich-text-editor-plug-ins.md#table-styles) si vous voulez ajouter vos propres styles pour des tableaux entiers ou des cellules individuelles. |
| undo | undo redo | Taille de l’historique des opérations [d’annulation et de rétablissement](/help/sites-administering/configure-rich-text-editor-plug-ins.md#undo-history). |

>[!NOTE]
>
>Le module externe Plein écran n’est pas pris en charge en mode de boîte de dialogue. Utilisation de la variable `dialogFullScreen` pour configurer la barre d’outils en mode plein écran.

## Présentation des chemins et des emplacements de configuration {#understand-the-configuration-paths-and-locations}

[Mode de modification d’éditeur de texte enrichi (et de l’IU)](#editingmodes) que vous fournissez pour que les auteurs déterminent l’emplacement des informations de configuration lorsque vous [activez les modules externes d’éditeur de texte enrichi](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin) :

| Mode de modification | Emplacement de l’IU tactile | Emplacement de l’IU classique |
|---|---|---|
| En ligne | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| Plein écran | `cq:editConfig/cq:inplaceEditing` | Non applicable |
| Boîte de dialogue | `cq:dialog` | `dialog` |
| Boîte de dialogue plein écran | `cq:dialog` | Non applicable |

>[!NOTE]
>
>Ne donnez pas le nom `cq:inplaceEditing` au nœud sous `config`. Sur le nœud `cq:inplaceEditing`, définissez les propriétés suivantes :
>
>* **Nom** : `configPath`
>* **Type** : `String`
>* **Valeur** : chemin du nœud qui contient la configuration proprement dite.

>
>Ne donnez pas le nom `config` au nœud de configuration de l’éditeur de texte enrichi (RTE). Autrement, les configurations de l’éditeur de texte enrichi prennent effet seulement pour les administrateurs et non pour les utilisateurs du groupe `content-author`.

Configurez les propriétés suivantes qui s’appliquent uniquement au mode de modification dans la boîte de dialogue dans l’IU tactile :

* `useFixedInlineToolbar` : configurez cette propriété booléenne définie sur le nœud d’éditeur de texte enrichi (une avec sling:resourceType=`cq/gui/components/authoring/dialog/richtext`) sur `True` pour que la barre d’outils de l’éditeur de texte enrichi reste fixe au lieu d’être flottante.

    Lorsque cette propriété est définie sur true, la modification en texte démarre par défaut sur l’événement « foundation-contentloaded ».

   Pour éviter cette situation, définissez la propriété `customStart` sur `True` et déclenchez l’événement « rte-start » pour commencer la modification avec l’éditeur de texte enrichi. Lorsque cette propriété est définie sur true, le comportement par défaut (l’éditeur de texte enrichi démarre en cas de clic) ne fonctionne pas.

* `customStart` : configurez cette propriété booléenne définie sur le nœud de l’éditeur de texte enrichi sur `True` pour contrôler à quel moment démarrer l’éditeur de texte enrichi en déclenchant l’événement `rte-start`.

* `rte-start` : déclenchez cet événement sur l’élément `contenteditable-div` d’éditeur de texte enrichi lorsque vous commencez la modification avec l’éditeur de texte enrichi. Cette option ne fonctionne que si `customStart` a été défini sur true.

Lorsque l’éditeur de texte enrichi est utilisé dans la boîte de dialogue optimisée pour les écrans tactiles, la définition de la propriété `useFixedInlineToolbar` sur true est obligatoire pour éviter des problèmes.

## Personnalisation de l’édition statique {#customizing-in-place-editing}

Vous pouvez définir sur quel sélecteur de HTML l’éditeur de texte commence en configurant les propriétés suivantes :

* **`editElementQuery`** - Défini sur `cq:InplaceEditingConfig`, cette propriété est utilisée pour spécifier un sélecteur de l’élément de HTML sur lequel la modification en ligne pour le composant de texte sera lancée. Si elle n’est pas spécifiée, la modification en ligne est directement lancée sur le HTML Composant Texte .
* **`textPropertyName`** - Défini sur `cq:InplaceEditingConfig`, cette propriété est utilisée pour spécifier le nom de la propriété qui sera enregistrée sur le noeud de contenu où la valeur de HTML du composant de texte sera conservée après modification en ligne.

La propriété correspondante pour le mode de boîte de dialogue est `name`.

## Activation des fonctionnalités d’éditeur de texte enrichi en activant des modules externes {#enable-rte-functionalities-by-activating-plug-ins}

Les fonctionnalités d’éditeur de texte enrichi sont rendues disponibles par l’intermédiaire d’une série de modules externes, chacun avec sa propriété features. Vous pouvez configurer la propriété features afin d’activer ou de désactiver une ou plusieurs fonctions de chaque module externe.

Pour consulter des configurations détaillées des modules externes de l’éditeur de texte enrichi, voir [Activation et configuration des modules externes de l’éditeur de texte enrichi](/help/sites-administering/configure-rich-text-editor-plug-ins.md).

Téléchargez cet exemple de configuration pour comprendre comment configurer l’éditeur de texte enrichi. Dans ce module, toutes les fonctionnalités sont activées.

[Obtenir le fichier](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
>
>Le [composant textuel Core Components](https://helpx.adobe.com/experience-manager/core-components/using/text.html) permet aux éditeurs de modèle de configurer de nombreux modules externes de l’éditeur de texte enrichi en tant que stratégies de contenu dans l’interface utilisateur, rendant ainsi inutile toute configuration technique. Les stratégies de contenu peuvent fonctionner avec des configurations d’interface utilisateur de l’éditeur de texte enrichi comme indiqué. Pour plus d’informations, voir [Paramètres de l’interface utilisateur de l’éditeur de texte enrichi et stratégies de contenu](/help/sites-administering/rich-text-editor.md#rtecontentpolicies), [Créer des modèles de page](/help/sites-authoring/templates.md), et la variable [Documentation destinée aux développeurs sur les composants principaux](https://helpx.adobe.com/experience-manager/core-components/using/developing.html).

>[!NOTE]
>
>À titre de référence, les composants Texte par défaut (fournis dans le cadre d’une installation standard) se trouvent sous :
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`

>
>Pour créer votre propre composant textuel, copiez le composant ci-dessus au lieu de modifier ces composants.

## Configuration de la barre d’outils de l’éditeur de texte enrichi {#dialogfullscreen}

AEM vous permet de configurer différemment l’interface utilisateur de l’éditeur de texte enrichi pour les différents modes de modification. Les paramètres par défaut sont fournis ci-dessous. Vous pouvez remplacer ces paramètres par défaut en fonction de vos besoins.

Pour une expérience de création optimale :

* Dans une boîte de dialogue flottante, activez uniquement les modules externes sans fenêtre contextuelle, car les boîtes de dialogue de ce type sont plus petites.
* Dans une boîte de dialogue plein écran, activez tous les modules externes requis, y compris ceux avec une fenêtre contextuelle plus grande, comme `Paste` plug-in . Utilisez la variable `dialogFullScreen` configuration décrite ci-dessous.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

Différents paramètres d’IU sont utilisés pour les modes en ligne et plein écran. La propriété toolbar est utilisée pour spécifier les boutons de la barre d’outils. Par exemple, si le bouton est lui-même une fonction (par exemple : `Bold`), il est spécifié comme suit : `PluginName#FeatureName` (par exemple, `links#modifylink`). Si le bouton est une fenêtre contextuelle (contenant certaines fonctionnalités d’un module externe), il est spécifié comme `#PluginName` (par exemple, `#format`). Les séparateurs ( | ) entre un groupe de boutons peuvent être spécifiés à l’aide de « – ».

Le nœud pop-up sous le mode en ligne ou plein écran contient la liste des éléments contextuels utilisés. Chaque noeud enfant sous `popovers` est nommé d’après le module externe (par exemple, `format`). Il possède une propriété . `items` contenant une liste des fonctionnalités du module externe (par exemple, `format#bold`).

## Paramètres de l’interface utilisateur de l’éditeur de texte enrichi et stratégies de contenu {#rtecontentpolicies}

Les administrateurs peuvent contrôler les options de l’éditeur de texte enrichi à l’aide de stratégies de contenu, au lieu de procéder à la configuration en suivant les instructions ci-dessus, par exemple. Les stratégies de contenu définissent les propriétés de conception d’un composant lorsqu’il est utilisé dans le cadre d’un [modèle modifiable](../sites-authoring/templates.md). Par exemple, si un composant textuel qui utilise l’éditeur de texte enrichi est employé avec un modèle modifiable, la stratégie de contenu peut définir que l’option Gras doit être disponible, au même titre que quelques options de mise en forme de paragraphe. Les stratégies de contenu sont réutilisables et peuvent être appliquées à plusieurs modèles.

À partir d’AEM 6.4 Service Pack 3, les options disponibles dans l’éditeur texte enrichi sont transmises depuis les configurations de l’interface utilisateur en amont vers les stratégies de contenu.

* Les paramètres de configuration de l’interface utilisateur définissent les options disponibles pour les stratégies de contenu.
* Si un élément a été supprimé ou n’est pas activé par la configuration d’interface utilisateur de l’éditeur de texte enrichi, la stratégie de contenu ne peut pas le configurer.
* Un auteur n’a accès à une fonctionnalité de ce type que si elle est mise à sa disposition par les configurations de l’interface utilisateur et les stratégies de contenu.

Pour consulter un exemple, reportez-vous à la [documentation du composant principal Texte](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor).

## Personnalisation de l’association entre les commandes et les icônes de la barre d’outils {#iconstoolbar}

Vous pouvez personnaliser l’association entre les icônes Coral affichées dans la barre d’outils de l’éditeur de texte enrichi et les commandes disponibles. Vous ne pouvez utiliser que les icônes Coral.

1. Créez un nœud intitulé `icons` sous `uiSettings/cui`.

1. Sous ce nœud, créez des nœuds pour les différentes icônes.
1. Sur chacun des nœuds d’icône, spécifiez une icône Coral et une commande à laquelle elle doit être associée.

Vous trouverez, ci-dessous, un exemple de fragment de code pour associer la commande Gras à l’icône Coral intitulée `textItalic`.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true"> 
    <rtePlugins jcr:primaryType="nt:unstructured"> 
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/> 
    </rtePlugins> 
    <uiSettings jcr:primaryType="nt:unstructured"> 
        <cui jcr:primaryType="nt:unstructured"> 
            <inline jcr:primaryType="nt:unstructured" 
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]"> 
            </inline> 
            <icons jcr:primaryType="nt:unstructured"> 
                <bold jcr:primaryType="nt:unstructured" 
                    command="format#bold" 
                    icon="textItalic"/> 
            </icons> 
        </cui> 
    </uiSettings> 
</text>
```

## Passage à l’éditeur de texte enrichi CoralUI 2 {#switch-to-coralui-rich-text-editor}

Sur une page, vous pouvez inclure la bibliothèque client de l’éditeur de texte enrichi CoralUI 2 ou la bibliothèque client de l’éditeur de texte enrichi CoralUI 3. Par défaut, l’éditeur de texte enrichi comprend la bibliothèque client de CoralUI 3. Pour passer à l’éditeur de texte enrichi CoralUI 2, exécutez les étapes suivantes.

>[!NOTE]
>
>Adobe déconseille d’effectuer ce changement. Passez à l’éditeur de texte enrichi CoralUI 2 en dernier recours. Les modules externes personnalisés pour l’éditeur de texte enrichi CoralUI 2 fonctionnent avec l’éditeur de texte CoralUI 3 s’ils ne dépendent pas d’éléments internes à l’éditeur de texte, tels que des classes. Si vous employez des modules externes personnalisés pour l’éditeur de texte enrichi CoralUI3, utilisez la bibliothèque `rte.coralui3`.

1. Recouvrir le noeud `/libs/cq/gui/components/authoring/editors/clientlibs/core` under `/apps`et procédez comme suit :

   * Remplacer `rte.coralui3` avec `rte.coralui2` pour la propriété dependencies.
   * Remplacer `cq.authoring.editor.core.inlineediting.rte.coralui3` avec `cq.authoring.editor.core.inlineediting.rte.coralui2` pour la propriété embed.
   * Remplacer `cq.authoring.rte.coralui3` avec `cq.authoring.rte.coralui2` pour la propriété embed.

1. Recouvrir les noeuds `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` et `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2` under `/apps`.

   Supprimer une catégorie `cq.authoring.dialog` de `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` et ajoutez-le à `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`.

1. Changez n’importe quelle autre dépendance incluse à la page de `rte.coralui3` à `rte.coralui2`. Par exemple, après avoir recouvert le noeud `/libs/mcm/campaign/components/touch-ui/clientlibs/rte` under `/apps`, modifiez toute dépendance à partir de `rte.coralui3` to `rte.coralui2`.

1. Recouvrir le noeud `cq/ui/widgets` under `/apps`. Remplacement de la dépendance `cq.rte` au niveau du noeud `/apps/cq/ui/widgets` avec `cq.coralui2.rte`.

>[!NOTE]
>
>L’éditeur de texte enrichi CoralUI 2 utilise des modèles handlebars pour les boîtes de dialogue des modules externes. Par conséquent, la bibliothèque client de l’éditeur de texte enrichi CoralUI 2 dépendait de la bibliothèque client handlebars. L’éditeur de texte enrichi CoralUI 3 n’utilise pas de modèles handlebars, et aucune dépendance n’y est associée. Si vos modules externes personnalisés utilisent des modèles handlebars, ajoutez la bibliothèque client handlebars dans votre page web.

## Informations supplémentaires {#further-information}

Pour plus d’informations sur la configuration de l’éditeur de texte enrichi, voir la référence de l’[API des widgets AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html).

En particulier, pour connaître les modules externes et les options associées disponibles :

* Le composant [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText) contient un champ de formulaire permettant de modifier les informations de texte stylisé (texte enrichi) : Pour connaître tous les paramètres disponibles pour le formulaire de texte enrichi, voir les options de configuration.
* Le composant RichText fournit un large éventail de fonctionnalités en utilisant les modules externes répertoriés sous [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin). Pour chaque module externe :

   * Pour plus d’informations sur les fonctionnalités qui peuvent être activées (ou désactivées), voir Fonctionnalités .
   * Voir les Options de configuration pour tous les paramètres disponibles pour une configuration détaillée du module externe approprié.

* Vous trouverez également plus d’informations sur les règles HTML pour les liens.

Les options ci-dessus peuvent être utilisées pour étendre et personnaliser votre propre éditeur de texte enrichi. Par exemple, pour répertorier les ancres disponibles dans la page en créant un lien, vous pouvez fournir votre propre mise en œuvre de `LinkPlugin`.

## Limitations connues {#known-limitations}

La fonctionnalité AEM RTE présente les limites suivantes :

* Les fonctionnalités de l’éditeur de texte enrichi sont prises en charge seulement dans les boîtes de dialogue des composants d’AEM. L’éditeur de texte enrichi n’est pas pris en charge sur les assistants ou les formulaires de base comme [Propriétés de la page](/help/sites-developing/page-properties-views.md) et [Génération de modèles automatique](/help/sites-authoring/scaffolding.md) sur l’IU tactile.

* AEM ne fonctionne pas sur les [dispositifs hybrides](/help/release-notes/known-issues.md).

* Ne donnez pas le nom `config` au nœud de configuration de l’éditeur de texte enrichi (RTE). Autrement, les configurations de l’éditeur de texte enrichi prennent effet seulement pour les administrateurs et non pour les utilisateurs du groupe `content-author`.

* RTE ne prend pas en charge les images intégrées ni les iframes pour incorporer un contenu.

>[!MORELIKETHIS]
>
>* [Configuration des modules externes d’éditeur de texte enrichi](configure-rich-text-editor-plug-ins.md)
>* [Utilisation de l’éditeur de texte enrichi pour la création](../sites-authoring/rich-text-editor.md)
>* [Configuration de l’éditeur de texte enrichi pour les sites accessibles](rte-accessible-content.md)
>* [Parité des fonctions entre les IU tactile et classique](../release-notes/touch-ui-features-status.md)
>* [Extrait d’un tutoriel pour créer un composant multichamp composite](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

