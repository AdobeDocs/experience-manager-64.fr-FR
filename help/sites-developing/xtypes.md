---
title: Utiliser les xtypes (IU classique)
seo-title: Using xtypes (Classic UI)
description: Découvrez tous les xtypes disponibles avec AEM
seo-description: Learn about all the xtypes that are available with AEM
uuid: 6497caa4-2f9b-4f21-9023-88d485fd1d78
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: adb70b43-1b0b-4302-905a-c7612675dabb
exl-id: 81d7fa0c-86db-47a1-8fac-44941d3affde
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '6436'
ht-degree: 74%

---

# Utiliser les xtypes (IU classique){#using-xtypes-classic-ui}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette page décrit tous les xtypes disponibles avec Adobe Experience Manager (AEM).

Dans le langage ExtJS, un xtype est un nom symbolique donné à une classe. Vous pouvez lire le paragraphe « Composant XTypes » de la [Présentation d’ExtJS 2](https://www.sencha.com/learn/overview-of-extjs-2) pour obtenir une explication détaillée sur les xtypes et leur utilisation.

Pour obtenir des informations complètes sur tous les widgets disponibles dans AEM, reportez-vous à la [documentation relative à l’API de widget](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html).

Pour déterminer les composants dans lesquels un xtype donné est utilisé au sein d’AEM, vous pouvez utiliser la requête Xpath suivante dans CRXDE en remplaçant « checkbox » par le xtype qui vous intéresse :

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Cette page décrit l’utilisation des xtypes ExtJS dans l’IU classique.
>
>Adobe recommande d’utiliser l’[IU optimisée pour les écrans tactiles](/help/sites-developing/touch-ui-concepts.md), une version standard et moderne qui repose sur l’[IU Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui) et l’[IU Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Vous trouverez ci-dessous une liste des xtypes disponibles dans Adobe Experience Manager :

* annotation

   [CQ.wcm.Annotation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Annotation)

   La boîte de dialogue est un type spécial de fenêtre avec un formulaire dans le corps et un groupe de boutons dans le pied de page. Il est généralement utilisé pour modifier du contenu, mais il peut également simplement afficher des informations.

* arraystore

   [CQ.Ext.data.ArrayStore](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayStore)

   Anciennement connue sous le nom de &quot;SimpleStore&quot;.

   Petite classe d’aide permettant de faciliter la création des [CQ.Ext.data.Stores](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) à partir de données de tableau. Un ArrayStore est automatiquement configuré avec une [CQ.Ext.data.ArrayReader](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayReader).

* asseteditor

   [CQ.dam.AssetEditor](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.AssetEditor)

   Éditeur de ressources utilisé par l’administrateur de gestion des ressources numériques.

* assetreferencesearchdialog

   [CQ.wcm.AssetReferenceSearchDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.AssetReferenceSearchDialog)

   AssetReferenceSearchDialog est une boîte de dialogue qui apparaît lorsqu’une page fait référence à des ressources ou à des balises.

* blueprintconfig

   [CQ.wcm.msm.BlueprintConfig](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig)

    BlueprintConfig fournit un panneau pour afficher les Live Copies d’un plan directeur et modifier les propriétés de ce plan directeur (déclencheur de synchronisation et actions de synchronisation).

* blueprintstatus

   [CQ.wcm.msm.BlueprintStatus](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus)

   BlueprintStatus fournit un panneau pour afficher et modifier un plan directeur et ses relations avec les Live Copies. La navigation se fait par le biais d’une [CQ.wcm.msm.BlueprintStatus.Tree](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus.Tree), éditez au moyen d’une [CQ.wcm.msm.BlueprintConfig](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig) et a [CQ.wcm.msm.LiveCopyProperties](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties).

* box

   [CQ.Ext.BoxComponent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent)

   Classe de base pour n’importe quelle [Composant](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component) qui doit être dimensionné comme une boîte, en utilisant la largeur et la hauteur.

   BoxComponent fournit des réglages de modèle de boîte automatique pour le dimensionnement et le positionnement et fonctionne correctement dans le modèle de rendu des composants.

* browsedialog

   [CQ.BrowseDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog)

   BrowseDialog permet de parcourir le référentiel afin de sélectionner un chemin. Il est généralement utilisé par l’intermédiaire d’une [BrowseField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField).

* browsefield

   [CQ.form.BrowseField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField)

   **Obsolète : utilisez plutôt [CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField)**.

* bulkeditor

   [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor)

   BulkEditor fournit un moteur de recherche et une grille pour modifier les résultats de recherche.

   BulkEditor doit être inséré dans un formulaire de HTML (requis par la fonctionnalité d’importation). Cela fonctionne parfaitement avec un [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* bulkeditorform

   [CQ.wcm.BulkEditorForm](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditorForm)

   BulkEditorForm fournit [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor) entouré d’un formulaire HTML. Il s’agit de la version autonome de la variable [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor), un HTML est requis pour le bouton d’importation.

* button

   [CQ.Ext.Button](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button)

   Classe de bouton unique

* buttongroup

   [CQ.Ext.ButtonGroup](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ButtonGroup)

   Conteneur pour un groupe de boutons

* chart

   [CQ.Ext.chart.Chart](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart)

   Le package CQ.Ext.chart fournit la fonctionnalité de visualisation des données avec une représentation graphique basée sur Flash. Chaque graphique est directement lié à un CQ.Ext.data.Store, ce qui permet la mise à jour automatique du graphique. Pour modifier l’aspect d’un graphique, reportez-vous à la section [chartStyle](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) et [extraStyle](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) options de configuration.

* checkbox

   [CQ.Ext.form.Checkbox](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox)

   Champ de case à cocher unique. Peut être utilisé comme remplacement direct des champs de case à cocher traditionnels.

* checkboxgroup

   [CQ.Ext.form.CheckboxGroup](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.CheckboxGroup)

   Un conteneur de regroupement pour [CQ.Ext.form.Checkbox](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox) les contrôles.

* clearcombo

   [CQ.form.ClearableComboBox](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ClearableComboBox)

   ClearableComboBox est une zone de liste non modifiable avec un déclencheur pour effacer sa valeur.

* colorfield

   [CQ.form.ColorField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ColorField)

   ColorField permet de saisir une valeur hexadécimale directement ou à l’aide d’un [CQ.Ext.ColorMenu](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorMenu).

* colorlist

   [CQ.form.ColorList](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ColorList)

   ColorList permet de sélectionner une couleur dans une liste modifiable.

* colormenu

   [CQ.Ext.menu.ColorMenu](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.ColorMenu)

   Un menu contenant une [CQ.Ext.ColorPalette](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorPalette) Composant .

* colorpalette

   [CQ.Ext.ColorPalette](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorPalette)

   Classe de palette de couleurs simple pour sélectionner les couleurs. La palette peut être rendue dans n’importe quel conteneur.

* combo

   [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)

   Commande de zone de liste modifiable prenant en charge la saisie automatique, le chargement à distance, la pagination et de nombreuses autres fonctionnalités.

   Une ComboBox fonctionne de la même manière qu’un HTML traditionnel. &lt;select> champ . La différence est que pour envoyer la variable [valueField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox), vous devez spécifier une [hiddenName](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) pour créer une entrée masquée.

* composant

   [CQ.Ext.Component](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component)

   Classe de base pour tous les composants Ext. Toutes les sous-classes de Component peuvent participer au cycle de vie automatisé du composant Ext de la création, du rendu et de la destruction fourni par le [Conteneur](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) classe . Les composants peuvent être ajoutés à un conteneur par l’intermédiaire du [items](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) option de configuration au moment de la création du conteneur.

* componentextractor

   [CQ.wcm.ComponentExtractor](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ComponentExtractor)

   ComponentExtractor permet d’extraire des composants d’un site ou d’une page web.

* componentselector

   [CQ.form.ComponentSelector](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ComponentSelector)

   Sélection groupée et ordonnée de composants disponibles.

* componentstyles

   [CQ.form.ComponentStyles](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ComponentStyles)

* compositefield

   [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField)

   Classe de base pour les champs de formulaires complexes basés sur les panneaux qui comprennent un champ de formulaire ou un groupe de champs de formulaires.

* container

   [CQ.Ext.Container](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)

   Classe de base pour n’importe quelle [CQ.Ext.BoxComponent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent) qui peut contenir d’autres composants. Les conteneurs gèrent le comportement de base des éléments contenant, à savoir l’ajout, l’insertion et la suppression d’éléments.

   Les classes de conteneur les plus utilisées sont les suivantes : [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel), [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) et [CQ.Ext.TabPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel).

* contentfinder

   [CQ.wcm.ContentFinder](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder)

   ContentFinder est une colonne spécialisée de deux colonnes [Fenêtre d’affichage](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport) qui contient l’outil de recherche de contenu réel à gauche et le cadre de contenu à droite.

* contentfindertab

   [CQ.wcm.ContentFinderTab](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinderTab)

   ContentFinderTab est un panneau spécialisé qui fournit les fonctions utilisées dans les panneaux à onglets de la fonction [CQ.wcm.ContentFinder](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder). En règle générale, il comprend un formulaire de recherche (la boîte de requête) et une vue de données pour afficher la recherche.

* cq.workflow.model.combo

   [CQ.wcm.WorkflowModelCombo](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.WorkflowModelCombo)

   WorkflowModelCombo est un [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) personnalisé qui affiche la liste des modèles de workflow disponibles.

* cq.workflow.model.selector

   [CQ.wcm.WorkflowModelSelector](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.WorkflowModelSelector)

   WorkflowModelSelector combine un WorkflowModelCombo avec une image miniature du workflow et des boutons permettant de créer et de modifier des modèles de workflow.

* createsitewizard

   [CQ.wcm.CreateSiteWizard](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.CreateSiteWizard)

    CreateSiteWizard est un assistant détaillé pour créer des sites (MSM).

* createversiondialog

   [CQ.wcm.CreateVersionDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.CreateVersionDialog)

   CreateVersionDialog est une boîte de dialogue qui permet de créer une version d’une page.

* customcontentpanel

   [CQ.CustomContentPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.CustomContentPanel)

   CustomContentPanel est un type spécial de panneau à utiliser dans [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog) : son contenu est récupéré depuis et vers une URL différente des autres champs de la boîte de dialogue.

* cycle

   [CQ.Ext.CycleButton](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)

    SplitButton spécialisé contenant un menu d’éléments [CQ.Ext.menu.CheckItem](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem). Le bouton fait défiler automatiquement chaque élément de menu lors d’un clic, augmentant l’événement [change](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton) du bouton (ou appelant la fonction [changeHandler](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton) du bouton, si disponible) pour l’élément de menu actif.

* dataview

   [CQ.Ext.DataView](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView)

    Mécanisme pour l’affichage des données à l’aide des modèles de mise en page personnalisés et le formatage. DataView utilise un [CQ.Ext.XTemplate](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.XTemplate) comme mécanisme de modélisation interne et il est lié à un [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) de façon à ce que l’affichage soit automatiquement mis à jour à mesure que les données de la boutique sont modifiées.

* datefield

   [CQ.Ext.form.DateField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField)

   Fournit un champ de saisie de date avec un menu déroulant [CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker) et la validation de date automatique.

* datemenu

   [CQ.Ext.menu.DateMenu](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu)

   Un menu contenant un [CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker) Composant .

* datepicker

   [CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker)

   Sélecteur de date contextuel. Cette classe est utilisée par la variable [DateField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) pour permettre la navigation et la sélection de dates valides.

* datetime

   [CQ.form.DateTime](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DateTime)

   DateTime permet de saisir une date et une heure en combinant [CQ.Ext.form.DateField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) et [CQ.Ext.form.TimeField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField).

* boîte de dialogue

   [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog)

   La boîte de dialogue est un type spécial de fenêtre avec un formulaire dans le corps et un groupe de boutons dans le pied de page. Il est généralement utilisé pour modifier du contenu, mais il peut également simplement afficher des informations.

* dialogfieldset

   [CQ.form.DialogFieldSet](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DialogFieldSet)

   DialogFieldSet est un [FieldSet](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet) à utiliser dans les [boîtes de dialogue](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* directstore

   [CQ.Ext.data.DirectStore](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectStore)

   Petite classe d’assistance pour créer une [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) configuré avec un [CQ.Ext.data.DirectProxy](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectProxy) et [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader) pour interagir avec une [CQ.Ext.Direct](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Direct) Côté serveur [Fournisseur](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.direct.Provider) plus facile.

* displayfield

   [CQ.Ext.form.DisplayField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DisplayField)

   Champ de texte en affichage seul qui n’est ni validé ni envoyé.

* editbar

   [CQ.wcm.EditBar](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBar)

   EditBar permet de modifier du contenu à l’aide des boutons figurant dans une barre.

   Bien que non répertorié ici, EditBar comporte tous les membres de [CQ.wcm.EditBase](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBase).

* éditeur

   [CQ.Ext.Editor](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Editor)

   Champ d’éditeur de base qui gère l’affichage/le masquage sur demande et dispose d’une logique intégrée de dimensionnement et de gestion des événements.

* editorgrid

   [CQ.Ext.grid.EditorGridPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)

   Cette classe étend la propriété [Classe GridPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) pour fournir des modifications de cellule sur le [colonnes](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column). Les colonnes modifiables sont spécifiées en fournissant un [éditeur](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) dans le [configuration des colonnes](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column).

* editrollover

   [CQ.wcm.EditRollover](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditRollover)

   EditRollover permet à l’utilisateur de modifier le contenu par double-clic et fournit d’autres actions de modification via un menu contextuel. La zone modifiable est indiquée par un cadre lorsque la souris survole le contenu.

* feedimporter

   [CQ.wcm.FeedImporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FeedImporter)

   FeedImporter permet d’importer des flux RSS ou Atom et de créer des pages pour chaque entrée de flux.

* field

   [CQ.Ext.form.Field](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Field)

   Classe de base pour les champs de formulaire qui offre une gestion d’événement par défaut, le dimensionnement, la manipulation des valeurs et d’autres fonctionnalités.

* fieldset

   [CQ.Ext.form.FieldSet](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet)

    Conteneur standard utilisé pour regrouper les éléments dans un [formulaire](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FormPanel).

* fileuploaddialogbutton

   [CQ.form.FileUploadDialogButton](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadDialogButton)

   FileUploadDialogButton crée un bouton qui ouvre une boîte de dialogue pour charger un fichier via FileUploadField. Peut être utilisé dans les boîtes de dialogue de modification où le chargement doit se produire dans un formulaire distinct.

* fileuploadfield

   [CQ.form.FileUploadField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadField)

   FileUploadField permet de sélectionner un fichier unique à charger.

* findreplacedialog

   [CQ.wcm.FindReplaceDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FindReplaceDialog)

   FindReplaceDialog est une boîte de dialogue permettant de rechercher et de remplacer des jetons sur une page et ses pages enfants.

* flash

   [CQ.Ext.FlashComponent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.FlashComponent)

* grid

   [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)

   Cette classe représente l’interface principale d’un contrôle de grille basé sur un composant pour représenter des données sous forme tabulaire avec des lignes et des colonnes.

* groupingstore

   [CQ.Ext.data.GroupingStore](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)

   Mise en œuvre de boutique spéciale qui permet le regroupement des enregistrements par l’un des champs disponibles. Cette méthode est généralement utilisée conjointement avec une variable [CQ.Ext.grid.GroupingView](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GroupingView) pour prouver le modèle de données pour un GridPanel groupé.

* paradymovedialog

   [CQ.wcm.HeavyMoveDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.HeavyMoveDialog)

   HeavyMoveDialog est une boîte de dialogue permettant de déplacer une page et ses pages enfants, en prenant également en compte la réactivation des pages précédemment activées (déplacement lourd ou « heavy move » en anglais).

* masqué

   [CQ.Ext.form.Hidden](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Hidden)

   Champ masqué de base pour stocker les valeurs masquées dans des formulaires qui doivent être transmises lors de l’envoi des formulaires.

* historybutton

   [CQ.HistoryButton](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.HistoryButton)

   HistoryButton est une petite classe d’aide qui fournit facilement des boutons Précédent et Suivant. En règle générale, deux instances associées sont requises : L’instance de bouton vers l’avant est un bouton simple associé à l’instance de bouton vers l’arrière qui gère l’historique.

* htmleditor

   [CQ.Ext.form.HtmlEditor](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)

   Fournit un composant d’éditeur HTML léger. Certaines fonctionnalités de la barre d’outils ne sont pas prises en charge par Safari et seront automatiquement masquées si nécessaire. Elles sont indiquées dans les options de configuration le cas échéant.

   Les boutons de la barre d’outils de l’éditeur ont des infos-bulle définies dans la propriété [buttonTips](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor).

* iframedialog

   [CQ.IframeDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframeDialog)

   Boîte de dialogue basique affichant le contenu d’un iframe et permettant la présence de formulaires dans les iframes.

* iframepanel

   [CQ.IframePanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframePanel)

   Panneau contenant un iframe. Permet de créer facilement des iframes, un événement de chargement d’iframe et un accès facile au contenu de l’iframe.

* inlinetextfield

   [CQ.form.InlineTextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.InlineTextField)

   InlineField est un champ de texte qui s’affiche en tant que libellé lorsqu’il n’est pas dans le focus.

* jsonstore

   [CQ.Ext.data.JsonStore](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonStore)

   Petite classe d’aide permettant de faciliter la création des [CQ.Ext.data.Stores](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) à partir de données JSON. Un JsonStore est automatiquement configuré avec une [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader).

* label

   [CQ.Ext.form.Label](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Label)

   Champ de libellé de base.

* languagecopydialog

   [CQ.wcm.LanguageCopyDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.LanguageCopyDialog)

   LanguageCopyDialog est une boîte de dialogue permettant de copier les arborescences de langues.

* linkchecker

   [CQ.wcm.LinkChecker](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.LinkChecker)

   LinkChecker est un outil permettant de vérifier les liens externes dans un site.

* listview

   [CQ.Ext.list.ListView](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView)

   CQ.Ext.list.ListView est une implémentation rapide et légère d’une [Grille](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) comme une vue.

* livecopyproperties

   [CQ.wcm.msm.LiveCopyProperties](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties)

    LiveCopyProperties fournit un panneau pour afficher et modifier les propriétés des Live Copies (héritage des relations, déclencheur de synchronisation et actions de synchronisation).

* lvbooleancolumn

   [CQ.Ext.list.BooleanColumn](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.BooleanColumn)

   Classe de définition de colonne qui effectue le rendu des champs de données booléens. Voir [xtype](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) option de configuration de [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) pour plus d’informations.

* lvcolumn

   [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)

   Cette classe encapsule les données de configuration de colonne à utiliser dans l’initialisation d’une [ListView](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView).

* lvdatecolumn

   [CQ.Ext.list.DateColumn](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn)

   Classe de définition de colonne qui effectue le rendu d’une date transmise en fonction des paramètres régionaux par défaut ou d’une configuration [format](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn). Voir [xtype](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) option de configuration de [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) pour plus d’informations.

* lvnumbercolumn

   [CQ.Ext.list.NumberColumn](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)

   Classe de définition de colonne qui effectue le rendu d’un champ de données numérique selon un [format](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn) chaîne. Voir [xtype](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) option de configuration de [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) pour plus d’informations.

* mediabrowsedialog

   [CQ.MediaBrowseDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.MediaBrowseDialog)

   **Obsolète : utilisez plutôt l’[outil de recherche de contenu](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder) pour parcourir les médias.**

   MediaBrowseDialog est une boîte de dialogue permettant de parcourir la bibliothèque de médias.

* menu

   [CQ.Ext.menu.Menu](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Menu)

   Objet menu. Il s’agit du conteneur auquel vous pouvez ajouter des éléments de menu. Le menu peut également servir de classe de base lorsque vous souhaitez un menu spécialisé basé sur un autre composant (comme [CQ.Ext.menu.DateMenu](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu) par exemple).

   Les menus peuvent contenir : [éléments de menu](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item), ou général [Composant](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component)s.

* menubaseitem

   [CQ.Ext.menu.BaseItem](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem)

   Classe de base pour tous les éléments dont le rendu est effectué dans les menus. BaseItem fournit le rendu par défaut, la gestion des états activée et les options de configuration de base partagées par tous les composants de menu.

* menucheckitem

   [CQ.Ext.menu.CheckItem](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)

   Ajoute un élément de menu qui contient une case à cocher par défaut, mais peut également faire partie d’un groupe de boutons radio.

* menuitem

   [CQ.Ext.menu.Item](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item)

   Classe de base pour tous les éléments de menu qui nécessitent des fonctionnalités liées au menu (comme des sous-menus) et ne sont pas des éléments d’affichage statique. L’élément étend les fonctionnalités de base de [CQ.Ext.menu.BaseItem](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem) en ajoutant l’activation spécifique au menu et la gestion des clics.

* menuseparator

   [CQ.Ext.menu.Separator](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Separator)

   Ajoute une barre de séparation à un menu, utilisée pour diviser les groupes logiques d’éléments de menu. En règle générale, vous ajoutez l’un d’eux en utilisant &quot;-&quot; dans votre appel à add() ou dans votre configuration d’éléments plutôt que d’en créer un directement.

* menutextitem

   [CQ.Ext.menu.TextItem](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.TextItem)

   Ajoute une chaîne de texte statique à un menu, généralement utilisée comme en-tête ou séparateur de groupes.

* metadata

   [CQ.dam.form.Metadata](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.form.Metadata)

   Les métadonnées fournissent un ensemble de champs permettant de déterminer les informations requises pour un champ de métadonnées utilisé, par exemple sur les pages de l’éditeur de ressources.

   Il fournit les champs suivants :

* multifield

   [CQ.form.MultiField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField)

   MultiField est une liste modifiable de champs de formulaire permettant de modifier les propriétés de plusieurs valeurs.

* mvt

   [CQ.form.MVT](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MVT)

   Le composant de test multivarié peut être utilisé pour définir et modifier un ensemble d’images qui sont présentées comme des bannières alternatives. Les statistiques de taux de clics publicitaires sont rassemblées par bannière.

* notificationinbox

   [CQ.wcm.NotificationInbox](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.NotificationInbox)

   NotificationInbox permet de s’abonner aux actions de WCM et de gérer les notifications.

* numberfield

   [CQ.Ext.form.NumberField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.NumberField)

   Champ numérique qui fournit le filtrage de frappe automatique et la validation numérique.

* offlineimporter

   [CQ.wcm.OfflineImporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.OfflineImporter)

   OfflineImporter est un outil permettant d’importer et de convertir des documents Microsoft Word en pages AEM. Cette fonction permet de modifier le contenu hors ligne à l’aide d’un traitement de texte.

* ownerdraw

   [CQ.form.OwnerDraw](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.OwnerDraw)

   OwnerDraw peut contenir du code HTML personnalisé (saisi directement ou récupéré à partir d’une URL).

* paging

   [CQ.Ext.PagingToolbar](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.PagingToolbar)

   À mesure qu’augmente la quantité d’enregistrements, le temps requis par le navigateur pour en effectuer le rendu augmente. La pagination est utilisée pour réduire la quantité de données échangées avec le client.

* panel

   [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel)

   Le panneau est un conteneur doté de fonctionnalités spécifiques et de composants structurels qui en font le bloc de création idéal pour les interfaces utilisateur orientées application.

   En vertu de leur héritage, les panneaux proviennent de [CQ.Ext.Container](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container).

* paragraph reference

   [CQ.form.ParagraphReference](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ParagraphReference)

   Le champ de référence de paragraphe permet de parcourir les pages et de sélectionner l’un de leurs paragraphes. Il se compose d’un champ de déclenchement et d’une boîte de dialogue de navigation de paragraphe associée.

* mot de passe

   [CQ.form.Password](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Password)

   Password est similaire à un [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField), mais il conserve sa valeur privée, ce qui permet de saisir des données sensibles.

* pathcompletion

   [CQ.form.PathCompletion](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathCompletion)

   **Obsolète : utilisez plutôt [CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField)**.

* pathfield

   [CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField)

   PathField est un champ d’entrée conçu pour les chemins dont le chemin est terminé et un bouton permettant d’ouvrir un [CQ.BrowseDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog) pour parcourir le référentiel du serveur. Il peut également parcourir des paragraphes de page pour générer des liens avancés.

* progression

   [CQ.Ext.ProgressBar](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)

   Composant de barre de progression pouvant être mis à jour. La barre de progression prend en charge deux modes différents : manuel et automatique.

   En mode manuel, vous êtes responsable de l’affichage et de la mise à jour (via [updateProgress](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)) et effacez la barre de progression selon les besoins à partir de votre propre code. Cette méthode est la plus appropriée lorsque vous souhaitez afficher la progression.

* propertygrid

   [CQ.Ext.grid.PropertyGrid](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyGrid)

    Mise en œuvre de grille spécialisée conçue pour imiter la grille de propriété classique figurant généralement dans les IDE de développement. Chaque ligne dans la grille représente une propriété d’un objet, et les données sont stockées sous la forme d’un ensemble de paires nom/valeur dans [CQ.Ext.grid.PropertyRecord](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyRecord).

* propgrid

   [CQ.PropertyGrid](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.PropertyGrid)

   PropertyGrid est une grille générique utilisée pour afficher et modifier les propriétés des objets.

* quicktip

   [CQ.Ext.QuickTip](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip)

    Classe d’info-bulle spécialisée pour les info-bulles pouvant être spécifiées au niveau du balisage et gérées automatiquement par l’instance [CQ.Ext.QuickTips](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTips) globale. Consultez l’en-tête de classe QuickTips pour en savoir plus sur l’utilisation et consulter des exemples supplémentaires.

* radio

   [CQ.Ext.form.Radio](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio)

   Champ de bouton radio simple. Identique à la case à cocher, mais fournie à titre de commodité pour définir automatiquement le type d’entrée. Le regroupement de cases d’option est géré automatiquement par le navigateur si vous attribuez le même nom à chaque radio d’un groupe.

* radiogroup

   [CQ.Ext.form.RadioGroup](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.RadioGroup)

   Conteneur de regroupement pour les contrôles [CQ.Ext.form.Radio](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio).

* referencesdialog

   [CQ.wcm.ReferencesDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ReferencesDialog)

   ReferencesDialog est une boîte de dialogue permettant d’afficher les références sur une page.

* restoretreedialog

   [CQ.wcm.RestoreTreeDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.RestoreTreeDialog)

   RestoreTreeDialog est une boîte de dialogue permettant de restaurer une version antérieure d’une arborescence.

* restoreversiondialog

   [CQ.wcm.RestoreVersionDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.RestoreVersionDialog)

   RestoreVersionDialog est une boîte de dialogue permettant de restaurer une version antérieure d’une page.

* richtext

   [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText)

   RichText fournit un champ de formulaire pour la modification des informations de texte stylisé (texte enrichi).

   Le composant RichText fournit actuellement les fonctionnalités suivantes :

* rolloutplan

   [CQ.wcm.msm.RolloutPlan](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan)

   RolloutPlan fournit une boîte de dialogue pour suivre la progression du déploiement d’une page. Le plan de déploiement est démarré par une [CQ.wcm.msm.RolloutWizard](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard).

* rolloutwizard

   [CQ.wcm.msm.RolloutWizard](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard)

   RolloutWizard offre un assistant pour déployer une page. RolloutWizard démarre une [CQ.wcm.msm.RolloutPlan](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan).

* searchfield

   [CQ.form.SearchField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SearchField)

   SearchField fournit un champ de recherche qui permet d’obtenir des résultats dans une liste déroulante et peut être utilisé pour effectuer une recherche dans le référentiel.

* selection

   [CQ.form.Selection](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection)

   Selection permet de choisir entre plusieurs options. Les options peuvent faire partie de la configuration ou être chargées à partir d’une réponse JSON. La sélection peut être générée sous la forme d’une liste déroulante (sélectionner) ou d’une zone de liste déroulante (sélectionner plus une entrée de texte libre).

* sidekick

   [CQ.wcm.Sidekick](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Sidekick)

   Sidekick est un panneau latéral flottant fournissant les outils courants pour modifier les pages.

* siteadmin

   [CQ.wcm.SiteAdmin](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteAdmin)

   SiteAdmin est une console fournissant des fonctions d’administration de gestion de contenu web.

* siteimporter

   [CQ.wcm.SiteImporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteImporter)

   SiteImporter permet d’importer des sites web complets et de créer des projets initiaux.

* sizefield

   [CQ.form.SizeField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SizeField)

   SizeField permet de saisir la largeur et la hauteur (par exemple, pour une image).

* slider

   [CQ.Ext.Slider](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Slider)

   Slider qui prend en charge l’orientation verticale ou horizontale, les réglages de clavier, l’alignement configurable, le clic sur les axes et l’animation. Peut être ajouté en tant qu’élément à n’importe quel conteneur. Exemple d’utilisation : ...

* diaporama

   [CQ.form.Slideshow](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Slideshow)

   Le diaporama fournit un composant qui peut être utilisé pour définir et modifier un ensemble d’images et de titres d’images qui peuvent être affichés sous la forme d’un diaporama.

   Le composant Diaporama repose sur la fonction [CQ.form.SmartImage](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage) composant.

* smartfile

   [CQ.form.SmartFile](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartFile)

   SmartFile est un téléchargeur de fichiers intelligent.

   Si un module externe de Flash (version >= 9) est installé, les chargements sont exécutés à l’aide de la bibliothèque SWFupload qui permet de gérer facilement les chargements.

* smartimage

   [CQ.form.SmartImage](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage)

   SmartImage est un téléchargeur d’images intelligent. Il fournit des outils pour traiter une image téléchargée, par exemple un outil pour définir des zones cliquables et un recadrage d’image.

   Notez que le composant est principalement conçu pour être utilisé sur un onglet de boîte de dialogue distinct.

* spacer

   [CQ.Ext.Spacer](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Spacer)

   Utilisé pour fournir un espace dimensionnable dans une mise en page.

* spinner

   [CQ.form.Spinner](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Spinner)

   Le compteur est un champ de déclenchement pour les valeurs numériques, de date ou d’heure. La valeur peut être augmentée et réduite à l’aide des déclencheurs haut et bas fournis, de la molette de défilement ou des touches.

* splitbutton

   [CQ.Ext.SplitButton](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.SplitButton)

    Bouton de division qui intègre une flèche déroulante capable de déclencher un événement séparément de l’événement de clic par défaut du bouton. En règle générale, il est utilisé pour afficher un menu déroulant qui fournit des options supplémentaires à l’action du bouton principal, mais tout autre gestionnaire personnalisé peut fournir la mise en œuvre arrowclick.

* static

   [CQ.Static](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Static)

   Static peut être utilisé pour afficher du code HTML ou du texte arbitraire.

* statistics

   [CQ.wcm.Statistics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Statistics)

   Statistics affiche les impressions de pages sous forme graphique. Le widget permet de sélectionner une période. Les statistiques doivent être affichées pour cette période.

* store

   [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)

   La classe Store encapsule un cache côté client d’objets [Record](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Record) qui fournissent des données pour les composants tels que [GridPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), [ComboBox](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) ou [DataView](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView).

* suggestfield

   [CQ.form.SuggestField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SuggestField)

   SuggestField fournit des suggestions basées sur sa saisie.

* switcher

   [CQ.Switcher](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Switcher)

   Switcher fournit un groupe de boutons pour la barre d’en-tête dans une console pour basculer entre les sites web, les ressources numériques, les outils, le workflow et la sécurité.

* tableedit

   [CQ.form.TableEdit](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit)

   **Obsolète : utilisez plutôt [CQ.form.TableEdit2.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2)**

* tableedit2

   [CQ.form.TableEdit2](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2)

   TableEdit2 fournit un widget pour la création de tableaux.

* tabpanel

   [CQ.Ext.TabPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel)

   Conteneur d’onglets de base. TabPanels peut être utilisé exactement comme un [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel) standard pour la mise en page, mais offre également une prise en charge spéciale pour contenir des composants enfants ([`items`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)).

* tags

   [CQ.tagging.TagInputField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tagging.TagInputField)

   ```
   CQ.tagging.TagInputField
   ```

    est un widget de formulaire qui permet de saisir des balises. Il dispose d’un menu contextuel permettant de faire une sélection parmi les balises existantes, et inclut la saisie semi-automatique, ainsi que bien d’autres fonctions.

* textarea

   [CQ.Ext.form.TextArea](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea)

   Champ de texte multiligne. Peut être utilisé comme remplacement direct pour les champs textarea traditionnels, et ajoute la prise en charge du dimensionnement automatique.

* textbutton

   [CQ.TextButton](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.TextButton)

   TextButton fournit un lien de texte avec les fonctionnalités d’un [CQ.Ext.Button](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button).

* textfield

   [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)

   Champ de texte de base. Peut être utilisé comme remplacement direct pour les entrées de texte traditionnelles ou comme classe de base pour des contrôles d’entrée plus sophistiqués (comme [CQ.Ext.form.TextArea](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea) et [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)).

* thumbnail

   [CQ.form.Thumbnail](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Thumbnail)

* timefield

   [CQ.Ext.form.TimeField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField)

   Il fournit un champ de saisie de l’heure avec une liste déroulante d’heure et la validation automatique de l’heure. Exemple d’utilisation : ...

* tip

   [CQ.Ext.Tip](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tip)

    Classe de base pour [CQ.Ext.QuickTip](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip) et [CQ.Ext.Tooltip](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tooltip) qui fournit la mise en page de base et le positionnement dont toutes les classes basées sur les conseils ont besoin. Cette classe peut être utilisée directement pour obtenir des conseils simples et statiques.

* titleseparator

   [CQ.menu.TitleSeparator](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.menu.TitleSeparator)

   Ajoute une barre de séparation à un menu, utilisée pour diviser les groupes logiques d’éléments de menu. Le séparateur peut en outre porter un titre.

* toolbar

   [CQ.Ext.Toolbar](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Toolbar)

   Classe de barre d’outils de base. Bien que le [`defaultType`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) pour Toolbar soit [`button`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button), les éléments Toolbar (les éléments enfants du conteneur Toolbar) peuvent être quasiment tout type de composant. Les éléments de la barre d’outils peuvent être créés explicitement via leurs constructeurs.

* tooltip

   [CQ.Ext.ToolTip](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ToolTip)

   Mise en œuvre d’info-bulle standard pour obtenir des informations supplémentaires en passant le pointeur de la souris sur un élément cible. @xtype tooltip.

* treegrid

   [CQ.tree.TreeGrid](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tree.TreeGrid)

   @xtype treegrid

* treepanel

   [CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)

   TreePanel fournit une représentation d’interface utilisateur structurée en arborescence des données structurées en arborescence.

   [TreeNode](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode)s’ils sont ajoutés au panneau Arborescence, chacun peut contenir des métadonnées utilisées par votre application dans ses [Attributs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode) .

* trigger

   [CQ.Ext.form.TriggerField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)

   Fournit un wrapper pratique pour les objets TextField qui ajoute un bouton déclencheur cliquable (qui ressemble par défaut à une zone de liste modifiable). Le déclencheur ne comporte aucune action par défaut. Vous devez donc attribuer une fonction pour implémenter le gestionnaire de clics de déclencheur en remplaçant [onTriggerClick](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField). Vous pouvez créer un TriggerField directement, car il s’affiche exactement comme une zone de liste modifiable.

* uploaddialog

   [CQ.UploadDialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UploadDialog)

   UploadDialog permet de charger des fichiers dans le référentiel. Il crée une boîte de dialogue de chargement.

* userinfo

   [CQ.UserInfo](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UserInfo)

   Élément de barre d’outils pour afficher le nom d’utilisateur actuel et autoriser des actions d’utilisateur comme la modification des propriétés et l’emprunt d’identité.

* viewport

   [CQ.Ext.Viewport](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport)

   Conteneur spécialisé représentant la zone d’application visible (la fenêtre d’affichage du navigateur).

   La fenêtre d’affichage s’affiche dans le corps du document et se dimensionne automatiquement à la taille de la fenêtre d’affichage du navigateur et gère le redimensionnement de la fenêtre. Il ne peut y avoir qu’une seule fenêtre d’affichage créée.

* fenêtre

   [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)

   Panneau spécialisé destiné à être utilisé comme fenêtre d’application. Les fenêtres sont flottantes, [rezable](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window), et [dragable](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) par défaut. Windows peut être [maximisé](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) pour remplir la fenêtre d’affichage, restaurer sa taille antérieure et peut être [minimiser](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)d.

* xmlstore

   [CQ.Ext.data.XmlStore](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlStore)

   Petite classe d’aide permettant de faciliter la création des [CQ.Ext.data.Stores](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) à partir de données XML. Un XmlStore est automatiquement configuré avec une [CQ.Ext.data.XmlReader](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlReader).

   **cqinclude** Pseudo xtype qui comprend des définitions de widget figurant dans un chemin différent au sein du référentiel. Il est le plus souvent utilisé dans les boîtes de dialogue de page. Il n’existe aucune classe de widget JavaScript réelle pour ce xtype. Il est traité par la fonction formatData() de la classe CQ.Util. Pour plus d’informations, consultez cet article de la base de connaissances.
