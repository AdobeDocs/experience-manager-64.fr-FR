---
title: Création – Environnement et outils
seo-title: Authoring - the Environment and Tools
description: La console Sites web vous permet de parcourir et de gérer votre site web. Les deux volets permettent de développer la structure de votre site web et d’effectuer des actions sur les éléments souhaités.
seo-description: The Websites console allows you to manage and navigate your website. Using two panes, the structure of your website can be expanded and actions taken on the required elements.
uuid: ec4ccc63-a3b8-464c-9c1a-204fd5d3b121
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 278195a6-3452-4966-9d56-022815cf6fb4
exl-id: f073c876-94cd-405d-885f-bfe433817ff4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 89%

---

# Création – Environnement et outils{#authoring-the-environment-and-tools}

L’environnement de création d’AEM comprend divers mécanismes permettant d’organiser et de modifier votre contenu. Les outils fournis sont accessibles dans plusieurs consoles et éditeurs de page.

## Administration du site {#site-administration}

La console **Sites web** vous permet de parcourir et de gérer votre site web. Les deux volets permettent de développer la structure de votre site web et d’effectuer des actions sur l’élément souhaité :

![chlimage_1-153](assets/chlimage_1-153.png)

## Modification du contenu de la page {#editing-your-page-content}

L’IU classique comporte un éditeur de page distinct, qui utilise l’outil de recherche de contenu et le sidekick :

`http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

![chlimage_1-154](assets/chlimage_1-154.png)

## Accès à l’Aide   {#accessing-help}

Plusieurs ressources d’**Aide** sont accessibles directement depuis AEM :

Outre les [barres d’outils de la console](/help/sites-classic-ui-authoring/author-env-basic-handling.md#accessing-help), vous pouvez également accéder à l’aide à partir du sidekick (à l’aide de l’icône ?) lorsque vous modifiez une page :

![](do-not-localize/sidekick-collapsed-2.png)

Vous pouvez également utiliser le bouton **Aide** dans la boîte de dialogue de modification de certains éléments. Vous obtiendrez alors une aide contextuelle.

## Sidekick {#sidekick}

Dans l’onglet **Composants** du sidekick, vous pouvez parcourir les composants pouvant être ajoutés à la page active. Le groupe requis peut être développé, puis un composant glissé jusqu’à l’emplacement de votre choix sur la page.

![chlimage_1-155](assets/chlimage_1-155.png)

## Outil de recherche de contenu {#the-content-finder}

L’outil de recherche de contenu constitue un moyen simple et rapide de rechercher des ressources ou du contenu dans le référentiel lors de la modification d’une page.

Utilisez l’outil de recherche de contenu pour localiser une plage de ressources. Au besoin, faites glisser un élément sur un paragraphe de la page :

* [Images](#finding-images)
* [Documents](#finding-documents)
* [Films](#finding-movies)
* [Explorateur Dynamic Media](/help/sites-administering/scene7.md#scene7contentbrowser)
* [Pages](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#finding-pages)
* [Paragraphes](#referencing-paragraphs-from-other-pages)
* [Produits](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#products)
* Ou pour [parcourir le site web par structure de référentiel](#the-content-finder)

Vous pouvez [rechercher des éléments spécifiques](#the-content-finder) avec toutes les options.

### Trouver des images {#finding-images}

Cet onglet répertorie toutes les images présentes dans le référentiel.

Après avoir créé un paragraphe Image sur votre page, vous pouvez y faire glisser un élément.

![chlimage_1-156](assets/chlimage_1-156.png)

### Trouver des documents {#finding-documents}

Cet onglet répertorie tous les documents présents dans le référentiel.

Après avoir créé un paragraphe Téléchargement sur votre page, vous pouvez y faire glisser un élément.

![chlimage_1-157](assets/chlimage_1-157.png)

### Trouver des films {#finding-movies}

Cet onglet répertorie toutes les vidéos (éléments Flash, par ex.) présentes dans le référentiel.

Après avoir créé un paragraphe approprié (par ex. Flash) sur votre page, vous pouvez y faire glisser un élément.

![chlimage_1-158](assets/chlimage_1-158.png)

### Produits {#products}

Cet onglet répertorie tous les produits. Après avoir créé un paragraphe approprié (par ex. Produit) sur votre page, vous pouvez y faire glisser un élément.

![chlimage_1-159](assets/chlimage_1-159.png)

### Trouver des pages {#finding-pages}

Cet onglet affiche toutes les pages. Double-cliquez sur une page pour l’ouvrir en vue de la modifier.

![chlimage_1-160](assets/chlimage_1-160.png)

### Référencer des paragraphes à partir d’autres pages {#referencing-paragraphs-from-other-pages}

Cet onglet vous permet de rechercher une autre page. Tous les paragraphes de cette page sont répertoriés. Vous pouvez ensuite faire glisser un paragraphe vers la page en cours ; cela a pour effet de créer une référence vers le paragraphe d’origine.

![chlimage_1-161](assets/chlimage_1-161.png)

### Utilisation de l’affichage du référentiel entier {#using-the-full-repository-view}

Cet onglet affiche toutes les ressources du référentiel.

![chlimage_1-162](assets/chlimage_1-162.png)

### Recherche avec l’explorateur de contenu {#using-search-with-the-content-browser}

Vous pouvez rechercher des éléments spécifiques pour toutes les options. Toutes les balises et ressources correspondant au modèle de recherche sont répertoriées :

![screen_shot_2012-02-08at100746am](assets/screen_shot_2012-02-08at100746am.png)

Vous pouvez également utiliser des caractères génériques pour la recherche. Les caractères génériques suivants sont pris en charge :

* `*` - correspond à une suite de zéro ou plusieurs caractères.

* `?` - correspond à un seul caractère.

>[!NOTE]
>
>Un « nom » de propriété pseudo doit être utilisé pour effectuer une recherche de caractères génériques.

Par exemple, si l’image disponible se nomme :

`ad-nmvtis.jpg`

les schémas de recherche suivants la trouvent (ainsi que toute autre image correspondant au schéma) :

* `name:*nmv*`
* `name:AD*` - la correspondance de caractères n’est *pas* sensible à la casse.
* `name:ad?nm??is.*` - Vous pouvez utiliser un nombre indéfini de caractères génériques dans une requête.

>[!NOTE]
>
>Vous pouvez également utiliser [SQL2](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/commons/query/sql2/package-summary.html) rechercher.

## Affichage de références {#showing-references}

AEM vous permet de visualiser les pages liées à la page en cours de traitement.

Pour afficher les références de page directes :

1. Dans le sidekick, sélectionnez l’icône de l’onglet **Page**.

   ![screen_shot_2012-02-16at83127pm](assets/screen_shot_2012-02-16at83127pm.png)

1. Sélectionner **Afficher les références...** AEM ouvre la fenêtre Références et affiche les pages qui font référence à la page sélectionnée, y compris leurs chemins d’accès.

   ![screen_shot_2012-02-16at83311pm](assets/screen_shot_2012-02-16at83311pm.png)

Dans certains cas, le sidekick permet d’exécuter d’autres actions, notamment :

* [Lancements](/help/sites-classic-ui-authoring/classic-launches.md)
* [Live Copies](/help/sites-administering/msm.md)

* [Blueprint](/help/sites-administering/msm-best-practices.md)

D’autres [relations entre pages sont visibles dans la console Sites web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console).

## Journal d’audit {#audit-log}

Le **journal d’audit** est accessible depuis l’onglet **Informations** du sidekick. Il répertorie les actions récentes ayant eu lieu sur la page active ; par exemple :

![chlimage_1-163](assets/chlimage_1-163.png)

## Informations sur la page {#page-information}

La console Sites Web [fournit des informations sur l’état actuel de la page.](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) telles que publication, modification, verrouillé, live copy, etc.

## Modes de page {#page-modes}

Lors de la modification d’une page dans l’IU classique, plusieurs modes sont accessibles à l’aide des icônes au bas du sidekick :

![](do-not-localize/chlimage_1-15.png)

La rangée d’icônes située au bas du sidekick permet de changer de mode pour le traitement des pages :

* [Modifier](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md)

   Il s’agit du mode par défaut qui vous permet de modifier la page, d’ajouter ou de supprimer des composants et d’effectuer d’autres modifications.

* [Aperçu](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#previewing-pages)

   Ce mode permet d’afficher un aperçu de la page comme si elle apparaissait sur votre site Web sous sa forme définitive.

* [Conception](/help/sites-classic-ui-authoring/classic-page-author-design-mode.md#main-pars-procedure-0)

   Dans ce mode, vous avez la possibilité de modifier la conception de la page en configurant les composants accessibles.

>[!NOTE]
>
>D’autres options sont également disponibles :
>
>* [Génération de modèles automatique](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md)
>* [Contexte client](/help/sites-administering/client-context.md)
>* Sites web - Ouvre la console Sites web.
>* Recharger - Actualise la page.


## Raccourcis clavier {#keyboard-shortcuts}

Divers [raccourcis clavier](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) sont disponibles.
