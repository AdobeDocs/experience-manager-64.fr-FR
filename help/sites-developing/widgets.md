---
title: Utilisation et extension de widgets (IU classique)
seo-title: Using and Extending Widgets (Classic UI)
description: AEM interface web utilise AJAX et d’autres technologies de navigateur modernes pour permettre l’édition et la mise en forme WYSIWYG du contenu par les auteurs directement sur la page web.
seo-description: AEM's web-based interface uses AJAX and other modern browser technologies to enable WYSIWYG editing and formatting of content by authors right on the web page
uuid: e8dfa140-dab7-4e08-a790-d703adf86d6f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 508f4fab-dd87-4306-83ae-12e544b8b723
exl-id: c747bfda-e82a-4b2d-a4af-5792bfe82576
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '5187'
ht-degree: 69%

---

# Utilisation et extension de widgets (IU classique){#using-and-extending-widgets-classic-ui}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’interface web d’Adobe Experience Manager utilise AJAX et d’autres technologies modernes intégrées dans les navigateurs pour activer l’édition tel écran tel écrit (WYSIWYG) et permettre aux auteurs de mettre en forme le contenu directement sur la page web.

Adobe Experience Manager (AEM) utilise la variable [ExtJS](https://www.sencha.com/) bibliothèque de widgets, qui fournit des éléments d’interface utilisateur très soignés qui fonctionnent sur tous les navigateurs les plus importants et permettent de créer des expériences d’interface utilisateur de niveau bureau.

Ces widgets sont inclus dans AEM et, en plus d’être utilisés par AEM lui-même, peuvent être utilisés par n’importe quel site web créé à l’aide d’AdobeAEM.

Pour consulter la liste complète de tous les widgets disponibles dans AEM, vous pouvez vous reporter à la [documentation sur les API des widgets](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) ou à la [liste des xtypes existants](/help/sites-developing/xtypes.md). En outre, de nombreux exemples montrant comment utiliser le framework ExtJS sont disponibles sur le site de [Sencha](https://www.sencha.com/products/extjs/examples/), le propriétaire du framework.

Cette page donne quelques informations sur l’utilisation et l’extension des widgets. Elle décrit d’abord comment [inclure du code côté client dans une page ;](#including-the-client-sided-code-in-a-page). Il décrit ensuite quelques exemples de composants qui ont été créés pour illustrer une utilisation et une extension de base. Ces composants sont disponibles dans la variable **Utilisation des widgets ExtJS** module activé **Partage de modules**.

Le module comprend des exemples de :

* [Boîtes de dialogue de base](#basic-dialogs) créée avec des widgets prêts à l’emploi.
* [Boîtes de dialogue dynamiques](#dynamic-dialogs) créée avec des widgets prêts à l’emploi et une logique javascript personnalisée.
* Boîtes de dialogue basées sur [widgets personnalisés](#custom-widgets).
* A [panneau d’arborescence](#tree-overview) affichage d’une arborescence JCR sous un chemin d’accès donné.
* A [panneau grille](#grid-overview) affichage des données sous la forme d’un tableau.

>[!NOTE]
>
>L’IU classique d’Adobe Experience Manager repose sur [ExtJS 3.4.0](https://extjs.cachefly.net/ext-3.4.0/docs/).

>[!NOTE]
>
>Cette page décrit l’utilisation des widgets dans l’IU classique. Adobe vous recommande d’utiliser l’[IU tactile](/help/sites-developing/touch-ui-concepts.md) moderne basée sur l’[IU Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui) et l’[IU Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## Insertion du code côté client dans une page {#including-the-client-sided-code-in-a-page}

Le code JavaScript côté client et StyleSheet doivent être placés dans une bibliothèque cliente.

Pour créer une bibliothèque cliente, procédez comme suit :

1. Créez un nœud sous `/apps/<project>` avec les propriétés suivantes :

   ```
       name="clientlib"
       jcr:mixinTypes="[mix:lockable]"
       jcr:primaryType="cq:ClientLibraryFolder" 
       sling:resourceType="widgets/clientlib" 
       categories="[<category-name>]" 
       dependencies="[cq.widgets]"
   ```

   >[!NOTE]
   >
   >Remarque : `<category-name>` est le nom de la bibliothèque personnalisée (par ex. &quot;cq.extjstraining&quot;) et est utilisé pour inclure la bibliothèque sur la page.

1. Sous `clientlib`, créez les dossiers `css` et `js` (nt:folder).

1. Sous `clientlib`, créez les fichiers `css.txt` et `js.txt` (nt:files). Ces fichiers .txt répertorient les fichiers qui sont inclus dans la bibliothèque.

1. Modifiez le fichier `js.txt` : il doit commencer par « `#base=js` », suivi de la liste des fichiers qui seront agrégés par le service de bibliothèque cliente CQ, par exemple :

   ```
   #base=js
    components.js
    exercises.js
    CustomWidget.js
    CustomBrowseField.js
    InsertTextPlugin.js
   ```

1. Modifiez le fichier `css.txt` : il doit commencer par « `#base=css` », suivi de la liste des fichiers qui seront agrégés par le service de bibliothèque cliente CQ, par exemple :

   ```
   #base=css
    components.css
   ```

1. Sous le dossier `js`, placez les fichiers JavaScript appartenant à la bibliothèque.

1. Sous le dossier `css`, placez les fichiers `.css` et les ressources utilisées par les fichiers css (`my_icon.png`, par exemple).

>[!NOTE]
>
>La gestion des feuilles de style décrite précédemment est facultative.

Pour inclure la bibliothèque cliente dans le fichier jsp du composant de page, procédez comme suit :

* pour inclure le code JavaScript et les feuilles de style :

   `<ui:includeClientLib categories="<category-name1>, <category-name2>, ..."/>`

   where `<category-nameX>` est le nom de la bibliothèque côté client.

* pour inclure uniquement le code JavaScript :

   `<ui:includeClientLib js="<category-name>"/>`

Pour plus d’informations, reportez-vous à la description de la variable [&lt;ui:includeclientlib>](/help/sites-developing/taglib.md#amp-lt-ui-includeclientlib) balise .

Dans certains cas, une bibliothèque cliente ne doit être disponible qu’en mode création et doit être exclue en mode publication. Elle peut être réalisée comme suit :

```xml
    if (WCMMode.fromRequest(request) != WCMMode.DISABLED) {
        %><ui:includeClientLib categories="cq.collab.blog"/><%
    }
```

### Prise en main des exemples {#getting-started-with-the-samples}

Suivez les tutoriels sur cette page, installez le package nommé **Utilisation des widgets ExtJS** dans une instance AEM locale, puis créez un exemple de page dans lequel les composants seront inclus. Procédez comme suit :

1. Dans l’instance AEM, téléchargez le package nommé **Utilisation des widgets ExtJS (v01)** depuis le partage de packages, puis installez-le. Il crée le projet `extjstraining` sous `/apps` dans le référentiel.

1. Incluez la bibliothèque cliente contenant les scripts (js) et la feuille de style (css) dans la balise head du jsp de la page geometrixx, car vous allez inclure les exemples de composants dans une nouvelle page du **Geometrixx** branche :

   in **CRXDE Lite** ouvrir le fichier `/apps/geometrixx/components/page/headlibs.jsp` et ajoutez le `cq.extjstraining` à la catégorie existante ; `<ui:includeClientLib>` de la façon suivante :

   `%><ui:includeClientLib categories="apps.geometrixx-main, cq.extjstraining"/><%`

1. Créez une page dans la branche **Geometrixx** sous `/content/geometrixx/en/products` et nommez-la **Utilisation des widgets ExtJS**.

1. Passez en mode Création et ajoutez tous les composants du groupe appelé **Utilisation des widgets ExtJS** à la conception de Geometrixx.
1. Revenez au mode d’édition : les composants du groupe **Utilisation des widgets ExtJS** sont disponibles dans le sidekick.

>[!NOTE]
>
>Les exemples de cette page sont basés sur l’échantillon de contenu Geometrixx. Celui-ci n’est plus fourni avec AEM et a été remplacé par We.Retail. Pour savoir comment télécharger et installer Geometrixx, consultez le document [Implémentation de référence We.Retail](/help/sites-developing/we-retail.md#we-retail-geometrixx).

### Boîtes de dialogue de base {#basic-dialogs}

Les boîtes de dialogue sont généralement utilisées pour modifier le contenu, mais elles peuvent également simplement afficher des informations. Pour afficher facilement une boîte de dialogue complète, accédez à sa représentation au format json. Pour ce faire, pointez votre navigateur vers :

`http://localhost:4502/<path-to-dialog>.-1.json`

Le premier composant de la variable **Utilisation des widgets ExtJS** dans le sidekick est appelé **1. Principes de base des boîtes de dialogue** et comprend quatre boîtes de dialogue de base qui sont créées avec des widgets prêts à l’emploi et sans logique JavaScript personnalisée. Les boîtes de dialogue sont stockées sous `/apps/extjstraining/components/dialogbasics`. Les boîtes de dialogue de base sont les suivantes :

* Boîte de dialogue complète (nœud `full`) : elle affiche une fenêtre avec 3 onglets ayant chacun 2 champs de texte.

* Boîte de dialogue à un seul panneau (nœud `singlepanel`) : elle affiche une fenêtre avec 1 seul onglet comprenant 2 champs de texte.
* Boîte de dialogue à plusieurs panneaux (nœud `multipanel`) : l’affichage est identique à celui de la boîte de dialogue complète, mais la construction est différente.
* Boîte de dialogue de conception (nœud `design`) : elle affiche une fenêtre avec 2 onglets. Le premier onglet comprend un champ de texte, un menu déroulant et une zone de texte réductible. Le deuxième onglet comporte un jeu de champs avec 4 champs de texte et un jeu de champs réductible avec 2 champs de texte.

Inclure la variable **1. Principes de base des boîtes de dialogue** dans l’exemple de page :

1. Ajoutez le composant **1. Composant de base de boîte de dialogue** à l’exemple de page à partir de l’onglet **Utilisation des widgets ExtJS** dans le **sidekick**.

1. Le composant affiche un titre, du texte et une **PROPRIÉTÉS** link: cliquez sur le lien pour afficher les propriétés du paragraphe stocké dans le référentiel. Cliquez de nouveau sur le lien pour masquer les propriétés.

Le composant se présente sous la forme suivante :

![chlimage_1-135](assets/chlimage_1-135.png)

#### Exemple 1 : Boîte de dialogue complète {#example-full-dialog}

Le **Complet** affiche une fenêtre avec trois onglets, chacun d’eux comportant deux champs de texte. Il s’agit de la boîte de dialogue par défaut de **Principes de base des boîtes de dialogue** composant. Ses caractéristiques sont les suivantes :

* Elle est définie par un nœud : type de nœud = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog).

* Elle affiche 3 onglets (type de nœud = `cq:Panel`).
* Chaque onglet comporte 2 champs de texte (type de nœud = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Est défini par le nœud :

   `/apps/extjstraining/components/dialogbasics/full`

* Son rendu est effectué au format JSON en demandant :

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/full.-1.json`

La boîte de dialogue se présente comme suit :

![screen_shot_2012-01-31at45411pm](assets/screen_shot_2012-01-31at45411pm.png)

#### Exemple 2 : Boîte de dialogue à un seul panneau {#example-single-panel-dialog}

Le **Un seul panneau** affiche une fenêtre avec un onglet contenant deux champs de texte. Ses caractéristiques sont les suivantes :

* Elle affiche 1 onglet (type de nœud = `cq:Dialog`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* L’onglet comporte 2 champs de texte (type de nœud = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Est défini par le nœud :

   `/apps/extjstraining/components/dialogbasics/singlepanel`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/singlepanel.-1.json`

* Un avantage par rapport au **Boîte de dialogue complète** est qu’une configuration moindre est nécessaire.
* Utilisation recommandée : pour les boîtes de dialogue simples qui affichent des informations ou qui ne comportent que quelques champs.

Pour utiliser la boîte de dialogue à un seul panneau :

1. Remplacez la boîte de dialogue du **Principes de base des boîtes de dialogue** avec le composant **Un seul panneau** dialog :

   1. Dans **CRXDE Lite**, supprimez le nœud suivant : `/apps/extjstraining/components/dialogbasics/dialog`.
   1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications.
   1. Copiez le nœud : `/apps/extjstraining/components/dialogbasics/singlepanel`.
   1. Collez ci-dessous le nœud que vous avez copié : `/apps/extjstraining/components/dialogbasics`.
   1. Sélectionnez le nœud `/apps/extjstraining/components/dialogbasics/Copy of singlepanel` et renommez-le `dialog`.

1. Modifiez le composant. La boîte de dialogue s’affiche alors comme suit :

![screen_shot_2012-01-31at45952pm](assets/screen_shot_2012-01-31at45952pm.png)

#### Exemple 3 : Boîte de dialogue à plusieurs panneaux {#example-multi-panel-dialog}

Le **Panneau multi** La boîte de dialogue présente le même affichage que la boîte de dialogue **Complet** mais il est construit différemment. Ses caractéristiques sont les suivantes :

* Elle est définie par un nœud (type de nœud = `cq:Dialog`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)).

* Elle affiche 3 onglets (type de nœud = `cq:Panel`).
* Chaque onglet comporte 2 champs de texte (type de nœud = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Est défini par le nœud :

   `/apps/extjstraining/components/dialogbasics/multipanel`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/multipanel.-1.json`

* Par rapport à la **Boîte de dialogue complète**, elle présente une structure simplifiée.

* Utilisation recommandée : pour les boîtes de dialogues à plusieurs onglets.

Pour utiliser la boîte de dialogue à plusieurs panneaux, procédez comme suit :

1. Remplacez la boîte de dialogue du **Principes de base des boîtes de dialogue** avec le composant **Panneau multi** dialog :

   suivez les étapes décrites pour la [Exemple 2 : Boîte de dialogue à un seul panneau](#example-single-panel-dialog)

1. Modifiez le composant. La boîte de dialogue s’affiche alors comme suit :

![screen_shot_2012-01-31at50119pm](assets/screen_shot_2012-01-31at50119pm.png)

#### Exemple 4 : Format Riche {#example-rich-dialog}

Le **Riche** affiche une fenêtre avec deux onglets. Le premier onglet comprend un champ de texte, un menu déroulant et une zone de texte réductible. Le deuxième onglet comporte un jeu de champs avec quatre champs de texte et un jeu de champs réductible avec deux champs de texte. Ses caractéristiques sont les suivantes :

* Elle est définie par un nœud (type de nœud = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Elle affiche 2 onglets (type de nœud = `cq:Panel`).
* Le premier onglet comporte un widget [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset) avec un [`textfield`](/help/sites-developing/xtypes.md#textfield) et un widget [`selection`](/help/sites-developing/xtypes.md#selection) avec 3 options, ainsi qu’un [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset) réductible avec un widget [`textarea`](/help/sites-developing/xtypes.md#textarea).

* Le deuxième onglet comprend un widget [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset) avec 4 widgets [`textfield`](/help/sites-developing/xtypes.md#textfield), ainsi qu’un widget `dialogfieldset` réductible avec 2 widgets [`textfield`](/help/sites-developing/xtypes.md#textfield).

* Est défini par le nœud :

   `/apps/extjstraining/components/dialogbasics/rich`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/rich.-1.json`

Pour utiliser la boîte de dialogue **Riche**, procédez comme suit :

1. Remplacez la boîte de dialogue du **Principes de base des boîtes de dialogue** avec le composant **Riche** dialog :

   suivez les étapes décrites pour la [Exemple 2 : Boîte de dialogue à un seul panneau](#example-single-panel-dialog)

1. Modifiez le composant. La boîte de dialogue s’affiche alors comme suit :

![screen_shot_2012-01-31at50429pm](assets/screen_shot_2012-01-31at50429pm.png) ![screen_shot_2012-01-31at50519pm](assets/screen_shot_2012-01-31at50519pm.png)

### Boîtes de dialogue dynamiques {#dynamic-dialogs}

Le deuxième composant de la variable **Utilisation des widgets ExtJS** dans le sidekick est appelé **2. Boîtes de dialogue dynamiques** et comprend trois boîtes de dialogue dynamiques conçues avec des widgets prêts à l’emploi et **avec une logique JavaScript personnalisée**. Les boîtes de dialogue sont stockées sous `/apps/extjstraining/components/dynamicdialogs`. Les boîtes de dialogue dynamiques sont les suivantes :

* Boîte de dialogue Switch Tabs (nœud `switchtabs`) : elle affiche une fenêtre avec deux onglets. Le premier onglet comporte une sélection radio avec trois options : lorsqu’une option est sélectionnée, un onglet correspondant à l’option s’affiche. Le deuxième onglet comporte deux champs de texte.
* Boîte de dialogue Arbitrary (nœud `arbitrary`) : elle affiche une fenêtre avec un seul onglet. Cet onglet se compose d’une zone permettant de déposer ou de charger une ressource, ainsi que d’une section affichant des informations sur la page et sur la ressource, le cas échéant.
* Boîte de dialogue Toggle Fields (nœud `togglefield`) : elle affiche une fenêtre avec un seul onglet. Cet onglet comprend une case à cocher : lorsque cette case est cochée, un jeu de champs composé de deux champs de texte est affiché.

Pour inclure le composant **2. Boîtes de dialogue dynamiques** dans l’exemple de page, procédez comme suit :

1. Ajoutez le composant **2. Boîtes de dialogue dynamiques** du composant à l’exemple de page à partir de la **Utilisation des widgets ExtJS** dans le **Sidekick**.

1. Le composant affiche un titre, du texte et une **PROPRIÉTÉS** link: cliquez sur pour afficher les propriétés du paragraphe stocké dans le référentiel. Cliquez à nouveau pour masquer les propriétés.

Le composant se présente sous la forme suivante :

![chlimage_1-136](assets/chlimage_1-136.png)

#### Exemple 1 : Boîte de dialogue Switch Onglets {#example-switch-tabs-dialog}

Le **Changement d’onglets** affiche une fenêtre avec deux onglets. Le premier onglet comporte une sélection radio avec trois options : lorsqu’une option est sélectionnée, un onglet correspondant à l’option s’affiche. Le deuxième onglet comporte deux champs de texte.

Ses caractéristiques principales sont les suivantes :

* Elle est définie par un nœud (type de nœud = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Elle affiche 2 onglets (type de nœud = `cq:Panel`) : 1 onglet de sélection, le deuxième onglet dépend de la sélection effectuée dans le premier onglet (3 options).
* Elle comprend 3 onglets facultatifs (type de nœud = `cq:Panel`) ayant chacun 2 champs de texte (type de nœud = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)). Un seul onglet facultatif est affiché à la fois.

* Est défini par le nœud `switchtabs` à l’adresse :

   `/apps/extjstraining/components/dynamicdialogs/switchtabs`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/switchtabs.-1.json`

Cette logique est implémentée par le biais d’écouteurs d’événements et de code JavaScript comme suit :

* Le nœud dialog comporte un listener « `beforeshow` » qui masque tous les onglets facultatifs avant l’affichage de la boîte de dialogue :

   `beforeshow="function(dialog){Ejst.x2.manageTabs(dialog.items.get(0));}"`

   `dialog.items.get(0)` récupère le panneau d’onglets qui contient le panneau de sélection et les trois panneaux facultatifs.

* L’objet `Ejst.x2` est défini dans le fichier `exercises.js` à l’emplacement suivant :

   `/apps/extjstraining/clientlib/js/exercises.js`

* Dans la méthode `Ejst.x2.manageTabs()`, étant donné que la valeur `index` est -1, tous les onglets facultatifs sont masqués (i passe de 1 à 3).

* L’onglet de sélection comprend 2 listeners : l’un affiche l’onglet sélectionné lors du chargement de la boîte de dialogue (événement « `loadcontent` ») et l’autre affiche l’onglet sélectionné lors du changement de la sélection (événement « `selectionchanged` ») :

   `loadcontent="function(field,rec,path){Ejst.x2.showTab(field);}"`

   `selectionchanged="function(field,value){Ejst.x2.showTab(field);}"`

* Dans la méthode `Ejst.x2.showTab()` :

   `field.findParentByType('tabpanel')` obtient le panneau d’onglets qui contient tous les onglets (`field` représente le widget de sélection).

   `field.getValue()` obtient la valeur de la sélection, par exemple : tab2.

   `Ejst.x2.manageTabs()` affiche l’onglet sélectionné.

* Chaque onglet facultatif comprend un listener qui le masque lorsque l’événement « `render` » se produit :

   `render="function(tab){Ejst.x2.hideTab(tab);}"`

* Dans la méthode `Ejst.x2.hideTab()` :

   `tabPanel` est le panneau d’onglets qui contient tous les onglets.

   `index` est l’index de l’onglet facultatif.

   `tabPanel.hideTabStripItem(index)` masque l’onglet.

Il se présente comme suit :

![screen_shot_2012-02-01at114745am](assets/screen_shot_2012-02-01at114745am.png)

#### Exemple 2 : boîte de dialogue Arbitrary {#example-arbitrary-dialog}

Très souvent, une boîte de dialogue affiche du contenu provenant d’un composant sous-jacent. La boîte de dialogue décrite ici, baptisée **Arbitrary**, extrait le contenu d’un autre composant.

Le **Arbitrary** affiche une fenêtre avec un seul onglet. L’onglet comporte deux champs : une pour déposer ou charger une ressource et une qui affiche des informations sur la page contenant et sur la ressource, le cas échéant.

Ses caractéristiques principales sont les suivantes :

* Elle est définie par un nœud (type de nœud = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Elle affiche 1 widget de panneau d’onglets (type de nœud = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) avec 1 panneau (type de nœud = `cq:Panel`).

* Le panneau comprend un widget smartfile (type de nœud = `cq:Widget`, xtype = [`smartfile`](/help/sites-developing/xtypes.md#smartfile)) et un widget ownerdraw (type de nœud = `cq:Widget`, xtype = [`ownerdraw`](/help/sites-developing/xtypes.md#ownerdraw)).

* Est défini par le nœud `arbitrary` à l’adresse :

   `/apps/extjstraining/components/dynamicdialogs/arbitrary`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/arbitrary.-1.json`

Cette logique est implémentée par le biais d’écouteurs d’événements et de code JavaScript comme suit :

* Le widget ownerdraw comporte un listener « `loadcontent` » qui affiche des informations sur la page contenant le composant et la ressource référencée par le widget smartfile lors du chargement du contenu :

   `loadcontent="function(field,rec,path){Ejst.x2.showInfo(field,rec,path);}"`

   `field` est défini avec l’objet ownerdraw.

   `path` est défini avec le chemin d’accès au contenu du composant (par exemple : /content/geometrixx/fr/products/triangle/ui-tutorial/jcr:content/par/dynamicdialogs).

* L’objet `Ejst.x2` est défini dans le fichier `exercises.js` à l’emplacement suivant :

   `/apps/extjstraining/clientlib/js/exercises.js`

* Dans la méthode `Ejst.x2.showInfo()` :

   `pagePath` est le chemin d’accès de la page contenant le composant.

   `pageInfo` représente les propriétés de page au format json.

   `reference` est le chemin d’accès de la ressource référencée.

   `metadata` représente les métadonnées de la ressource au format json.

   `ownerdraw.getEl().update(html);` affiche le code HTML créé dans la boîte de dialogue.

Pour utiliser la boîte de dialogue **Arbitrary**, procédez comme suit :

1. Remplacez la boîte de dialogue du **Boîte de dialogue dynamique** avec le composant **Arbitrary** dialog :

   suivez les étapes décrites pour la [Exemple 2 : Boîte de dialogue à un seul panneau](#example-single-panel-dialog)

1. Modifiez le composant. La boîte de dialogue s’affiche alors comme suit :

![screen_shot_2012-02-01at115300am](assets/screen_shot_2012-02-01at115300am.png)

#### Exemple 3 : Boîte de dialogue Toggle Fields {#example-toggle-fields-dialog}

La boîte de dialogue **Toggle Fields** affiche une fenêtre avec un seul onglet. Cet onglet comprend une case à cocher : lorsque cette case est cochée, un jeu de champs composé de deux champs de texte est affiché.

Ses caractéristiques principales sont les suivantes :

* Elle est définie par un nœud (type de nœud = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Elle affiche 1 widget tabpanel (type de nœud = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#textpanel)) avec 1 panneau (type de nœud = `cq:Panel`).

* Le panneau comprend un widget de sélection ou case à cocher (type de nœud = `cq:Widget`, xtype = [`selection`](/help/sites-developing/xtypes.md#selection), type = [`checkbox`](/help/sites-developing/xtypes.md#checkbox)) et un widget réductible dialogfieldset (type de nœud = `cq:Widget`, xtype = [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset)), qui est masqué par défaut, avec 2 widgets textfield (type de nœud = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Est défini par le nœud `togglefields` à l’adresse :

   `/apps/extjstraining/components/dynamicdialogs/togglefields`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/togglefields.-1.json`

Cette logique est implémentée par le biais d’écouteurs d’événements et de code JavaScript comme suit :

* L’onglet de sélection comprend 2 listeners : l’un affiche le widget dialogfieldset lorsque le contenu est chargé (événement « `loadcontent` ») et l’autre affiche le widget dialogfieldset lors du changement de la sélection (événement « `selectionchanged` ») :

   `loadcontent="function(field,rec,path){Ejst.x2.toggleFieldSet(field);}"`

   `selectionchanged="function(field,value){Ejst.x2.toggleFieldSet(field);}"`

* L’objet `Ejst.x2` est défini dans le fichier `exercises.js` à l’emplacement suivant :

   `/apps/extjstraining/clientlib/js/exercises.js`

* Dans la méthode `Ejst.x2.toggleFieldSet()` :

   * `box` est l’objet de sélection.
   * `panel` est le panneau contenant la sélection et les widgets dialogfieldset.
   * `fieldSet` est l’objet dialogfieldset.
   * `show` est la valeur de la sélection (true ou false).
   * basé sur &quot; `show`&#39; le jeu de boîtes de dialogue s’affiche ou non

Pour utiliser la boîte de dialogue **Toggle Fields**, procédez comme suit :

1. Remplacez la boîte de dialogue du **Boîte de dialogue dynamique** avec le composant **Activer/désactiver les champs** dialog :

   suivez les étapes décrites pour la [Exemple 2 : Boîte de dialogue à un seul panneau](#example-single-panel-dialog)

1. Modifiez le composant. La boîte de dialogue s’affiche alors comme suit :

![screen_shot_2012-02-01at115518am](assets/screen_shot_2012-02-01at115518am.png)

### Widgets personnalisés {#custom-widgets}

Les widgets prêts à l’emploi fournis avec AEM doivent couvrir la plupart des cas d’utilisation. Cependant, il peut, dans certaines situations, s’avérer nécessaire de créer un widget personnalisé pour traiter un cas spécifique à un projet. Les widgets personnalisés peuvent être créés en étendant les widgets existants. Pour vous aider à prendre en main cette personnalisation, le **Utilisation des widgets ExtJS** Le module comprend trois boîtes de dialogue qui utilisent trois widgets personnalisés différents :

* La boîte de dialogue Multi Field (nœud `multifield`) affiche une fenêtre avec un seul onglet. Cet onglet comprend un widget multifield personnalisé qui comporte deux zones : un menu déroulant avec deux options et un champ de texte. Étant donné qu’il est basé sur le widget `multifield` prêt à l’emploi (qui comprend uniquement un champ de texte), il possède toutes les fonctionnalités du widget `multifield`.

* La boîte de dialogue Tree Browse (nœud `treebrowse`) affiche une fenêtre avec un seul onglet contenant un widget d’exploration du chemin : lorsque vous cliquez sur la flèche, une fenêtre s’ouvre dans laquelle vous pouvez parcourir une hiérarchie et sélectionner un élément. Le chemin d’accès de l’élément est ensuite ajouté au champ du chemin et conservé lorsque la boîte de dialogue est fermée.
* Une boîte de dialogue basée sur le module Éditeur de texte enrichi (nœud `rteplugin`) qui ajoute un bouton personnalisé à l’Éditeur de texte enrichi pour insérer du texte personnalisé dans le texte principal. Elle comprend un widget `richtext` (RTE) et une fonctionnalité personnalisée qui est ajoutée par le biais du module externe RTE.

Les widgets personnalisés et le module externe sont inclus dans le composant appelé **3. Widgets personnalisés** de **Utilisation des widgets ExtJS** module. Pour inclure ce composant à l’exemple de page :

1. Ajoutez le composant **3. Widgets personnalisés** du composant à l’exemple de page à partir de la **Utilisation des widgets ExtJS** dans le **Sidekick**.

1. Le composant affiche un titre, du texte et, lorsque vous cliquez sur l’icône **PROPRIÉTÉS** lien, propriétés du paragraphe stocké dans le référentiel. Cliquez à nouveau pour masquer les propriétés.

   Le composant se présente sous la forme suivante :

![chlimage_1-137](assets/chlimage_1-137.png)

#### Exemple 1 : Widget Custom Multifield {#example-custom-multifield-widget}

Le **Multichamp personnalisé** la boîte de dialogue basée sur un widget affiche une fenêtre avec un seul onglet. L’onglet comporte un widget multichamp personnalisé qui, contrairement à celui standard qui comporte un champ, comporte deux champs : un menu déroulant avec deux options et un champ de texte.

Boîte de dialogue basée sur le widget **Custom Multifield** :

* Elle est définie par un nœud (type de nœud = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Elle affiche 1 widget tabpanel (type de nœud = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) contenant un panneau (type de nœud = `cq:Widget`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* Le panneau comprend un widget `multifield` (type de nœud = `cq:Widget`, xtype = [`multifield`](/help/sites-developing/xtypes.md#multifield)).

* Le widget `multifield` comprend une option fieldconfig (type de nœud = `nt:unstructured`, xtype = `ejstcustom`, optionsProvider = `Ejst.x3.provideOptions`) basée sur le xtype personnalisé « `ejstcustom` » :

   * « `fieldconfig` » est une option de configuration de l’objet [`CQ.form.MultiField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField).
   * « `optionsProvider` » est une configuration du widget `ejstcustom`. Elle est définie avec la méthode `Ejst.x3.provideOptions` qui est définie dans `exercises.js` dans :

      `/apps/extjstraining/clientlib/js/exercises.js`

      et renvoie 2 options.

* Est défini par le nœud `multifield` à l’adresse :

   `/apps/extjstraining/components/customwidgets/multifield`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/customwidgets/multifield.-1.json`

Widget à plusieurs champs (multifield) personnalisé (xtype = `ejstcustom`) :

* Il s’agit d’un objet JavaScript appelé `Ejst.CustomWidget`.

* Il est défini dans le fichier JavaScript `CustomWidget.js` à l’emplacement suivant :

   `/apps/extjstraining/clientlib/js/CustomWidget.js`

* Il étend le widget [`CQ.form.CompositeField`.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField)

* Il comprend 3 champs : `hiddenField` (Textfield), `allowField` (ComboBox) et `otherField` (Textfield).

* Il remplace `CQ.Ext.Component#initComponent` pour ajouter les 3 champs :

   * `allowField` est un objet [CQ.form.Selection](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection) de type « select ». optionsProvider est une configuration de l’objet Selection qui est instanciée avec la configuration optionsProvider du widget personnalisé (CustomWidget) défini dans la boîte de dialogue.
   * `otherField` est un objet [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField).

* Il remplace les méthodes `setValue`, `getValue` et `getRawValue` de [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField) afin de définir et de récupérer la valeur de CustomWidget au format :

   `<allowField value>/<otherField value>, e.g.: 'Bla1/hello'`.

* S’enregistre lui-même en tant que xtype « `ejstcustom` » :

   `CQ.Ext.reg('ejstcustom', Ejst.CustomWidget);`

La boîte de dialogue basée sur le widget **Custom Multifield** se présente comme suit :

![screen_shot_2012-02-01at115840am](assets/screen_shot_2012-02-01at115840am.png)

#### Exemple 2 : Widget treebrowse personnalisé {#example-custom-treebrowse-widget}

La variable **Treebrowse** la boîte de dialogue basée sur un widget affiche une fenêtre avec un onglet contenant un widget de navigation de chemin personnalisé : lorsque vous cliquez sur la flèche, une fenêtre s’ouvre dans laquelle vous pouvez parcourir une hiérarchie et sélectionner un élément. Le chemin d’accès de l’élément est ensuite ajouté au champ du chemin et conservé lorsque la boîte de dialogue est fermée.

La boîte de dialogue treebrowse personnalisée :

* Elle est définie par un nœud (type de nœud = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Elle affiche 1 widget tabpanel (type de nœud = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) contenant un panneau (type de nœud = `cq:Widget`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* Le panneau comprend un widget personnalisé (type de nœud = `cq:Widget`, xtype = `ejstbrowse`).

* Est défini par le nœud `treebrowse` à l’adresse :

   `/apps/extjstraining/components/customwidgets/treebrowse`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/customwidgets/treebrowse.-1.json`

Widget treebrowse personnalisé (xtype = `ejstbrowse`) :

* Il s’agit d’un objet JavaScript appelé `Ejst.CustomWidget`.
* Il est défini dans le fichier JavaScript `CustomBrowseField.js` à l’emplacement suivant :

   `/apps/extjstraining/clientlib/js/CustomBrowseField.js`

* Il étend [`CQ.Ext.form.TriggerField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField).
* Il définit une fenêtre de navigation appelée `browseWindow`.

* Il remplace [`CQ.Ext.form.TriggerField` pour afficher la fenêtre de navigation lorsque l’utilisateur clique sur la flèche.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField#onTriggerClick)
* Définit un [`CQ.Ext.tree.TreePanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel) objet :

   * Il récupère ses données en appelant le servlet enregistré à l’emplacement `/bin/wcm/siteadmin/tree.json`.
   * Sa racine est « `apps/extjstraining` ».

* Définit un `window` objet ([`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)) :

   * Il est basé sur le panneau prédéfini.
   * Il comprend un bouton **OK** qui définit la valeur du chemin d’accès sélectionné et masque le panneau.

* La fenêtre est ancrée sous le champ **Chemin d’accès**.
* Le chemin d’accès est transmis du champ de navigation à la fenêtre lorsque l’événement `show` se produit.

* S’enregistre lui-même en tant que xtype « `ejstbrowse` » :

   `CQ.Ext.reg('ejstbrowse', Ejst.CustomBrowseField);`

Pour utiliser la boîte de dialogue basée sur le widget **Custom Treebrowse**, procédez comme suit :

1. Remplacez la boîte de dialogue du **Widgets personnalisés** avec le composant **Parcourir Treebrowse personnalisé** dialog :

   suivez les étapes décrites pour la [Exemple 2 : Boîte de dialogue à un seul panneau](#example-single-panel-dialog)

1. Modifiez le composant. La boîte de dialogue s’affiche alors comme suit :

![screen_shot_2012-02-01at120104pm](assets/screen_shot_2012-02-01at120104pm.png)

#### Exemple 3 : Module externe Éditeur de texte enrichi (RTE) {#example-rich-text-editor-rte-plug-in}

Le **Module externe Éditeur de texte enrichi (RTE)** La boîte de dialogue basée sur un éditeur de texte enrichi comporte un bouton personnalisé permettant d’insérer du texte personnalisé entre crochets. Le texte personnalisé peut être analysé par une logique côté serveur (non implémentée dans cet exemple), par exemple pour ajouter du texte défini à l’emplacement donné :

Boîte de dialogue basée sur le **module externe de RTE** :

* Elle est définie par le nœud rteplugin à l’emplacement suivant :

   `/apps/extjstraining/components/customwidgets/rteplugin`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/customwidgets/rteplugin.-1.json`

* Le nœud `rtePlugins` comprend un nœud enfant `inserttext` (type de nœud = `nt:unstructured`) dont le nom provient du module externe. Elle possède une propriété appelée `features`, qui définit les fonctionnalités du module externe disponibles pour l’éditeur de texte enrichi.

Module externe de RTE :

* Il s’agit d’un objet JavaScript appelé `Ejst.InsertTextPlugin`.

* Il est défini dans le fichier JavaScript `InsertTextPlugin.js` à l’emplacement suivant :

   `/apps/extjstraining/clientlib/js/InsertTextPlugin.js`

* Il étend l’objet [`CQ.form.rte.plugins.Plugin`.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)
* Les méthodes suivantes définissent l’objet [`CQ.form.rte.plugins.Plugin` et sont remplacées dans le module externe d’implémentation :](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)

   * `getFeatures()` renvoie un tableau de toutes les fonctionnalités rendues disponibles par le module externe.
   * `initializeUI()` ajoute le nouveau bouton à la barre d’outils de l’Éditeur de texte enrichi.
   * `notifyPluginConfig()` affiche le titre et le texte lorsque l’utilisateur survole le bouton avec le pointeur de la souris.
   * `execute()` est appelé lorsque l’utilisateur clique sur le bouton et exécute l’action du module externe : il affiche une fenêtre qui est utilisée pour définir le texte à inclure.

* `insertText()` insère un texte à l’aide de l’objet de boîte de dialogue correspondant `Ejst.InsertTextPlugin.Dialog` (voir plus loin).

* `executeInsertText()` est appelé par la méthode `apply()` de la boîte de dialogue, qui est déclenchée lorsque l’utilisateur clique sur le bouton **OK**.

* S’enregistre lui-même en tant que plug-in « `inserttext` » :

   `CQ.form.rte.plugins.PluginRegistry.register("inserttext", Ejst.InsertTextPlugin);`

* L’objet `Ejst.InsertTextPlugin.Dialog` définit la boîte de dialogue qui s’ouvre lorsque l’utilisateur clique sur le bouton du module externe. La boîte de dialogue se compose d’un panneau, d’un formulaire, d’un champ de texte et de 2 boutons (**OK** et **Annuler**).

Pour utiliser la boîte de dialogue basée sur le **module externe Éditeur de Texte Enrichi (RTE)**, procédez comme suit :

1. Remplacez la boîte de dialogue du **Widgets personnalisés** avec le composant **Module externe Éditeur de texte enrichi (RTE)** Boîte de dialogue basée sur :

   suivez les étapes décrites pour la [Exemple 2 : Boîte de dialogue à un seul panneau](#example-single-panel-dialog)

1. Modifiez le composant.
1. Cliquez sur la dernière icône sur la droite (celle qui comporte quatre flèches). Saisissez un chemin et cliquez sur **OK**:

   Le chemin est affiché entre crochets (`[]`).

1. Cliquez sur **OK** pour fermer l’éditeur de texte enrichi.

Le **Module externe Éditeur de texte enrichi (RTE)** La boîte de dialogue basée s’affiche comme suit :

![screen_shot_2012-02-01at120254pm](assets/screen_shot_2012-02-01at120254pm.png)

>[!NOTE]
>
>Cet exemple montre uniquement comment implémenter la partie côté client de la logique : les espaces réservés (*[text]*) doivent ensuite être analysés explicitement du côté serveur (dans le JSP du composant, par exemple).

### Tree Overview {#tree-overview}

L’objet[`CQ.Ext.tree.TreePanel` prêt à l’emploi représente les données d’interface utilisateur sous la forme d’une arborescence. ](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel) Le composant Tree Overview inclus dans le package **Utilisation des widgets ExtJS** montre comment utiliser l’objet `TreePanel` pour afficher une arborescence JCR sous un chemin d’accès donné. La fenêtre proprement dite peut être ancrée/détachée. Dans cet exemple, la logique de fenêtre est incorporée dans le fichier JSP du composant entre les balises &lt;script>&lt;/script>.

Pour inclure le composant **Tree Overview** dans l’exemple de page :

1. Ajoutez le composant **4. Tree Overview** à l’exemple de page à partir de l’onglet **Utilisation des widgets ExtJS** dans le **sidekick**.

1. Le composant affiche les éléments suivants :

   * un titre, avec du texte
   * a **PROPRIÉTÉS** link: cliquez sur pour afficher les propriétés du paragraphe stocké dans le référentiel. Cliquez à nouveau pour masquer les propriétés.
   * une fenêtre flottante avec une représentation arborescente du référentiel, qui peut être développée.

Le composant se présente sous la forme suivante :

![screen_shot_2012-02-01at120639pm](assets/screen_shot_2012-02-01at120639pm.png)

Composant Tree Overview :

* Il est défini à l’emplacement suivant :

   `/apps/extjstraining/components/treeoverview`

* Sa boîte de dialogue permet de définir la taille de la fenêtre et d’ancrer/détacher la fenêtre (voir les détails ci-dessous).

Le jsp du composant :

* Récupère les propriétés de largeur, de hauteur et d’ancrage du référentiel.
* Affiche du texte sur le format de données de présentation de l’arborescence.
* Incorpore la logique de fenêtre dans le jsp du composant entre les balises JavaScript.
* Il est défini à l’emplacement suivant :

   `apps/extjstraining/components/treeoverview/content.jsp`

Le code JavaScript incorporé dans le jsp du composant :

* Définit un objet `tree` en essayant de récupérer une fenêtre d’arborescence de la page.

* Si la fenêtre qui affiche l’arborescence n’existe pas, `treePanel` ([CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)) est créé :

   * `treePanel` contient les données utilisées pour créer la fenêtre.
   * Les données sont récupérées en appelant le servlet enregistré à l’emplacement suivant :
      `/bin/wcm/siteadmin/tree.json`

* Le listener `beforeload` s’assure que le nœud sélectionné est chargé.
* L’objet `root` définit le chemin d’accès `apps/extjstraining` en tant que racine de l’arborescence.
* `tree` ([`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)) est défini en fonction de la variable `treePanel`, et s’affiche avec :

   `tree.show();`

* Si la fenêtre existe déjà, elle est affichée en fonction de la largeur, de la hauteur et des propriétés d’ancrage extraites du référentiel.

Boîte de dialogue du composant :

* Elle affiche 1 onglet avec 2 champs pour définir la taille (largeur et hauteur) de la fenêtre d’aperçu d’arborescence et 1 champ pour ancrer/détacher la fenêtre.
* Elle est définie par un nœud (type de nœud = `cq:Dialog`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* Le panneau comprend un widget sizefield (type de nœud = `cq:Widget`, xtype = [`sizefield`](/help/sites-developing/xtypes.md#sizefield)) et un widget (type de nœud = `cq:Widget`, xtype = [`selection`](/help/sites-developing/xtypes.md#selection), type = `radio`) avec 2 options (vrai/faux)

* Elle est définie par le nœud dialog à l’emplacement suivant :

   `/apps/extjstraining/components/treeoverview/dialog`

* Son rendu est effectué au format json en demandant :

   `http://localhost:4502/apps/extjstraining/components/treeoverview/dialog.-1.json`

* Elle se présente comme suit :

![screen_shot_2012-02-01at120745pm](assets/screen_shot_2012-02-01at120745pm.png)

### Présentation de la grille {#grid-overview}

Un panneau Grille représente les données sous la forme d’un tableau de lignes et de colonnes. Il se compose des éléments suivants :

* Magasin : modèle contenant les enregistrements de données (lignes).
* Modèle de colonne : mise en page de colonne.
* Affichage : encapsule l’interface utilisateur.
* Modèle de sélection : comportement de la sélection.

Le composant Grid Overview inclus dans le package **Utilisation des widgets ExtJS** montre comment afficher les données sous la forme d’un tableau :

* L’exemple 1 utilise des données statiques.
* L’exemple 2 utilise les données extraites du référentiel.

Pour inclure le composant Grid Overview dans l’exemple de page :

1. Ajoutez le composant **5. Grid Overview** à l’exemple de page à partir de l’onglet **Utilisation des widgets ExtJS** dans le **sidekick**.

1. Le composant affiche les éléments suivants :

   * Un titre, accompagné de texte
   * a **PROPRIÉTÉS** link: cliquez sur pour afficher les propriétés du paragraphe stocké dans le référentiel. Cliquez à nouveau pour masquer les propriétés.
   * une fenêtre flottante contenant des données au format tabulaire.

Le composant se présente sous la forme suivante :

![screen_shot_2012-02-01at121109pm](assets/screen_shot_2012-02-01at121109pm.png)

#### Exemple 1 : Grille par défaut {#example-default-grid}

Dans sa version prête à l’emploi, la variable **Présentation de la grille** affiche une fenêtre avec des données statiques sous la forme d’un tableau. Dans cet exemple, la logique est incorporée dans le fichier jsp du composant de deux manières :

* la logique générique est définie entre &lt;script>&lt;/script> tags
* la logique spécifique est disponible dans un fichier .js distinct et est liée à dans le fichier jsp. Cette configuration permet de basculer facilement entre les deux logiques (statique/dynamique) en commentant les balises &lt;script> souhaitées.

Composant Grid Overview :

* Il est défini à l’emplacement suivant :

   `/apps/extjstraining/components/gridoverview`

* Sa boîte de dialogue permet de définir la taille de la fenêtre et d’ancrer/détacher la fenêtre.

Le jsp du composant :

* Récupère les propriétés de largeur, de hauteur et d’ancrage du référentiel.
* affiche du texte en guise d’introduction pour le format de données d’aperçu de grille ;
* fait référence au code JavaScript qui définit l’objet GridPanel :

   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script>`

   `defaultgrid.js` définit certaines données statiques comme base de l’objet GridPanel.

* incorpore, entre des balises JavaScript, du code JavaScript qui définit l’objet Window utilisant l’objet GridPanel ;
* Il est défini à l’emplacement suivant :

   `apps/extjstraining/components/gridoverview/content.jsp`

Le code JavaScript incorporé dans le jsp du composant :

* Définit l’objet `grid` en essayant de récupérer le composant window de la page :

   `var grid = CQ.Ext.getCmp("<%= node.getName() %>-grid");`

* Si `grid` n’existe pas, un objet [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) ( `gridPanel`) est défini en appelant la méthode `getGridPanel()` (voir ci-après). Cette méthode est définie dans `defaultgrid.js`.

* `grid` est un objet [`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) basé sur l’objet GridPanel prédéfini et affiché sous la forme : `grid.show();`.

* If `grid` existe déjà, il s’affiche en fonction des propriétés de largeur, de hauteur et d’ancrage récupérées du référentiel.

Le fichier JavaScript (`defaultgrid.js`) référencé dans le jsp du composant définit la méthode `getGridPanel()` qui est appelée par le script incorporé dans le fichier JSP et renvoie un objet [`CQ.Ext.grid.GridPanel` sur la base de données statiques. ](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) La logique est la suivante :

* `myData` est un tableau de données statiques, composé de 5 colonnes et de 4 lignes.
* `store` est un objet `CQ.Ext.data.Store` qui utilise `myData`.

* `store` est chargé en mémoire :

   `store.load();`

* `gridPanel` est un objet [`CQ.Ext.grid.GridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) qui utilise `store` :

   * Les largeurs de colonne sont redimensionnées en permanence :

      `forceFit: true`

   * Une seule ligne peut être sélectionnée à la fois :

      `singleSelect:true`

#### Exemple 2 : grille de recherche de référence {#example-reference-search-grid}

Lorsque vous installez le package, le fichier `content.jsp` du composant **Grid Overview** affiche une grille sur la base des données statiques. Il est possible de modifier le composant pour afficher une grille avec les caractéristiques suivantes :

* Comporte trois colonnes.
* Est basé sur les données récupérées du référentiel en appelant une servlet.
* Les cellules de la dernière colonne peuvent être modifiées. La valeur est conservée dans une propriété `test` sous le nœud défini par le chemin d’accès qui est affiché dans la première colonne.

Comme expliqué dans la section précédente, l’objet window obtient son [`CQ.Ext.grid.GridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) en appelant la fonction `getGridPanel()` de la méthode définie dans la variable `defaultgrid.js` fichier à l’emplacement `/apps/extjstraining/components/gridoverview/defaultgrid.js`. Le **Présentation de la grille** fournit une implémentation différente pour la variable `getGridPanel()` , définie dans la variable `referencesearch.js` fichier à l’emplacement `/apps/extjstraining/components/gridoverview/referencesearch.js`. En changeant le fichier .js qui est référencé dans le jsp du composant, la grille sera basée sur les données extraites du référentiel.

Changez le fichier .js qui est référencé dans le jsp du composant :

1. Dans **CRXDE Lite**, dans le fichier `content.jsp` du composant, mettez en commentaire la ligne qui contient le fichier `defaultgrid.js`, de sorte qu’elle se présente comme suit :

   `<!-- script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script-->`

1. Supprimez le commentaire de la ligne qui contient le fichier `referencesearch.js` afin qu’elle se présente comme suit :

   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/referencesearch.js"></script>`

1. Enregistrez les modifications.
1. Actualisez l’exemple de page.

Le composant se présente sous la forme suivante :

![screen_shot_2012-02-01at121429pm](assets/screen_shot_2012-02-01at121429pm.png)

Le fichier JavaScript référencé dans le jsp du composant (`referencesearch.js`) définit la méthode `getGridPanel()` qui est appelée par le jsp du composant et renvoie un objet [`CQ.Ext.grid.GridPanel` sur la base des données qui sont extraites de manière dynamique du référentiel. ](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) La logique contenue dans le fichier `referencesearch.js` définit des données dynamiques comme base de l’objet GridPanel :

* `reader` est un objet [`CQ.Ext.data.JsonReader`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader)qui lit la réponse du servlet au format JSON pour 3 colonnes.

* `cm` est un objet [`CQ.Ext.grid.ColumnModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) pour 3 colonnes.

   Les cellules de la colonne « Test » peuvent être modifiées, étant donné qu’elles sont définies avec un éditeur :

   `editor: new `[`CQ.Ext.form.TextField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)`({})`

* Les colonnes peuvent faire l’objet d’un tri :

   `cm.defaultSortable = true;`

* `store` est un objet [`CQ.Ext.data.GroupingStore`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore) :

   * Il récupère ses données en appelant le servlet enregistré à l’emplacement « `/bin/querybuilder.json` » ; quelques paramètres sont utilisés pour filtrer la requête.
   * Il repose sur l’objet `reader` défini précédemment.
   * Le tableau est trié selon la colonne **jcr:path** dans l’ordre croissant.

* `gridPanel` est un objet [`CQ.Ext.grid.EditorGridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel) qui peut être modifié :

   * Il repose sur l’objet `store` prédéfini et sur le modèle de colonne `cm`. 
   * Une seule ligne peut être sélectionnée à la fois :

      `sm: new `[`CQ.Ext.grid.RowSelectionModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.RowSelectionModel)`({singleSelect:true})`

   * Le listener `afteredit` vérifie les éléments suivants après la modification d’une cellule de la colonne « **Test** » :

      * La propriété `test` du nœud situé à l’emplacement défini par la colonne « **jcr:path** » est définie dans le référentiel avec la valeur de la cellule.
      * Si l’opération POST est réussie, la valeur est ajoutée à l’objet `store` ; dans le cas contraire, elle est rejetée.
