---
title: Développer des composants AEM
seo-title: Developing AEM Components
description: Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages Web.
seo-description: AEM components are used to hold, format, and render the content made available on your webpages.
exl-id: d3c1559a-1a7a-46ed-a935-9ad226cdea33
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3511'
ht-degree: 64%

---

# Développer des composants AEM{#developing-aem-components}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages Web.

* Lors de la [création de pages](/help/sites-authoring/default-components.md), les composants permettent aux auteurs de modifier et de configurer le contenu.

   * Lors de la construction d’un site [marchand](/help/sites-administering/ecommerce.md), les composants peuvent, par exemple, collecter et afficher des informations issues du catalogue.

      Pour plus d’informations, consultez [Développement du e-commerce](/help/sites-developing/ecommerce.md).

   * Lors de la construction d’un site de [communauté](/help/communities/author-communities.md), les composants peuvent fournir des informations et en collecter auprès des visiteurs.

      Pour plus d’informations, consultez [Développement de communautés](/help/communities/communities.md).

* Dans l’instance de publication, les composants réalisent le rendu du contenu en le présentant comme vous le souhaitez aux visiteurs de votre site Web.

>[!NOTE]
>
>Cette page est la suite du document [Composants AEM – Notions de base](/help/sites-developing/components-basics.md).

>[!CAUTION]
>
>Les composants sous `/libs/cq/gui/components/authoring/dialog` s’utilisent uniquement dans l’éditeur (boîtes de dialogue de composants dans l’instance de création). S’ils sont utilisés ailleurs (par exemple dans une boîte de dialogue d’assistant), ils peuvent ne pas se comporter comme prévu.

## Exemples de code {#code-samples}

Cette page contient la documentation de référence (ou des liens vers la documentation de référence) requise pour développer des composants AEM. Consultez [Développement de composants AEM - Exemples de code](/help/sites-developing/developing-components-samples.md) pour des exemples pratiques.

## Structure {#structure}

La structure de base d’un composant est décrite à la page [Composants AEM – Notions de base](/help/sites-developing/components-basics.md#structure). Ce document traite à la fois les interfaces utilisateur tactile et classique. Même si vous n’avez pas besoin d’utiliser les paramètres classiques de votre nouveau composant, il peut être utile d’en prendre connaissance lors de l’héritage de composants existants.

## Extension des composants et des boîtes de dialogue existants {#extending-existing-components-and-dialogs}

Selon le composant que vous souhaitez implémenter, il peut être possible d’étendre ou de personnaliser une instance existante, plutôt que de définir et de développer l’ensemble de l’instance. [structure](#structure) à partir de zéro.

Lors de l’extension ou de la personnalisation d’un composant ou d’une boîte de dialogue existant, vous pouvez copier ou répliquer la structure entière ou la structure requise pour la boîte de dialogue avant d’apporter vos modifications.

### Extension d’un composant existant {#extending-an-existing-component}

L’extension d’un composant existant peut être réalisée avec [Hiérarchie du type de ressource](/help/sites-developing/components-basics.md#component-hierarchy-and-inheritance) et les mécanismes d&#39;héritage qui s&#39;y rapportent.

>[!NOTE]
>
>Il est également possible de redéfinir les composants avec une superposition en fonction de la logique du chemin de recherche. Cependant, dans ce cas, le [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) n’est pas déclenché et `/apps` doit définir la superposition en entier.

>[!NOTE]
>
>Le [composant de fragment de contenu](/help/sites-developing/customizing-content-fragments.md) peuvent également être personnalisés et étendus, bien que la structure complète et les relations avec Assets doivent être prises en compte.

### Personnalisation d’une boîte de dialogue de composant existante {#customizing-a-existing-component-dialog}

Il est également possible de remplacer une *boîte de dialogue de composant* en utilisant le [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) et en définissant la propriété `sling:resourceSuperType`.

Ainsi, vous avez seulement besoin de redéfinir les modifications à apporter et non pas toute la boîte de dialogue (en utilisant `sling:resourceSuperType`). Cette méthode est désormais recommandée pour étendre une boîte de dialogue de composant.

Voir [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) pour plus d’informations.

## Définition du balisage {#defining-the-markup}

Votre composant est rendu dans le langage [HTML](https://www.w3schools.com/htmL/html_intro.asp). Votre composant doit définir les balises HTML nécessaires pour réaliser le rendu du contenu selon les besoins, dans les environnements de création et de publication.

### Utilisation du langage de modèle de HTML {#using-the-html-template-language}

Le [langage de modèle HTML (HTL)](https://helpx.adobe.com/fr/experience-manager/htl/user-guide.html) a été introduit avec AEM 6.0 et remplace JSP (JavaServer Pages) en tant que système de modèle côté serveur privilégié et recommandé pour HTML. Pour les développeurs web qui doivent créer des sites web d’entreprise performants, HTL contribue à améliorer l’efficacité de la sécurité et du développement.

>[!NOTE]
>
>Bien que HTL et JSP puissent être utilisés pour le développement de composants, nous allons illustrer le développement avec HTL sur cette page, car il s’agit du langage de script recommandé pour AEM.

## Développement de la logique de contenu {#developing-the-content-logic}

Cette logique facultative sélectionne et/ou calcule le contenu dont il faut réaliser le rendu. Il est appelé à partir d’expressions HTL avec le modèle Use-API approprié.

Le mécanisme permettant de séparer la logique de l’aspect aide à définir clairement ce qui est appelé pour un affichage donné. Cela permet également une logique différente pour différentes vues d’une même ressource.

### Utilisation de Java {#using-java}

[L’Use-API Java HTL permet à un fichier HTL d’accéder aux méthodes d’assistance dans une classe Java personnalisée. ](https://helpx.adobe.com/fr/experience-manager/htl/using/use-api-java.html) Vous pouvez ainsi utiliser du code Java pour implémenter la logique de sélection et de configuration du contenu du composant.

### Utilisation de JavaScript {#using-javascript}

[L’Use-API JavaScript HTL permet à un fichier HTL d’accéder au code d’assistance écrit en JavaScript](https://helpx.adobe.com/fr/experience-manager/htl/using/use-api-javascript.html). Cela permet d’utiliser le code JavaScript pour implémenter la logique de sélection et de configuration du contenu du composant.

### Utilisation de bibliothèques de HTMLS côté client {#using-client-side-html-libraries}

Les sites web modernes reposent principalement sur un traitement côté client piloté par du code JavaScript et CSS complexe. Organiser et optimiser la diffusion de ce code est une opération qui peut se révéler complexe.

Pour résoudre ce problème, AEM fournit des **dossiers de bibliothèques côté client** qui permettent de stocker le code côté client dans le référentiel, de le classer par catégorie et de définir quand et comment chaque catégorie de code doit être diffusée au client. Le système de bibliothèque côté client se charge alors de la génération des liens appropriés dans la page Web finale pour charger le code correct.

Lecture [Utilisation de bibliothèques de HTMLS côté client](/help/sites-developing/clientlibs.md) pour plus d’informations.

## Configuration du comportement de modification {#configuring-the-edit-behavior}

Vous pouvez configurer le comportement de modification d’un composant, notamment ses attributs tels que les actions disponibles pour le composant, les caractéristiques de l’éditeur local et les écouteurs liés aux événements sur le composant. La configuration est commune aux interfaces utilisateur tactile et classique, avec toutefois certaines différences spécifiques.

La [configuration du comportement de modification d’un composant](/help/sites-developing/components-basics.md#edit-behavior) s’effectue en ajoutant un nœud `cq:editConfig` de type `cq:EditConfig` sous le nœud de composant (de type `cq:Component`), ainsi qu’en ajoutant des nœuds enfants et des propriétés spécifiques.

## Configuration du comportement de prévisualisation {#configuring-the-preview-behavior}

Le cookie [Mode Gestion de contenu Web](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) est défini lors du passage en mode **Aperçu** même lorsque la page n’est pas rafraîchie.

Pour les composants dont le rendu est sensible au Mode Gestion de contenu Web, ils doivent être définis de manière à s’actualiser eux-mêmes, puis s’appuyer sur la valeur du cookie.

>[!NOTE]
>
>Dans l’IU tactile, seules les valeurs `EDIT` et `PREVIEW` sont utilisées pour le cookie [Mode Gestion de contenu Web](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html).

## Création et configuration d’une boîte de dialogue {#creating-and-configuring-a-dialog}

Les boîtes de dialogue permettent à l’auteur d’interagir avec le composant. L’utilisation d’une boîte de dialogue permet aux auteurs et aux administrateurs de modifier le contenu, de configurer le composant ou de définir les paramètres de conception (dans une [Boîte de dialogue de conception](#creating-and-configuring-a-design-dialog)).

### IU Coral et IU Granite {#coral-ui-and-granite-ui}

[IU Coral](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) et [IU Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html) définir l&#39;aspect moderne de l&#39;AEM.

[L’IU Granite offre un vaste éventail de composants de base (widgets)](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html) nécessaires pour créer une boîte de dialogue dans l’environnement de création. Si nécessaire, vous pouvez étendre cette sélection et créer votre propre widget.

Pour plus d’informations, voir :

* IU Coral

   * Fournit une interface utilisateur uniforme dans toutes les solutions cloud.
   * [Concepts de l’IU tactile AEM - IU Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Guide de l’IU Coral](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/index.html)

* IU Granite

   * Fournit le balisage de l’IU Coral encapsulé dans les composants Sling pour la création de consoles d’interface utilisateur et de boîtes de dialogue.
   * [Concepts de l’IU tactile AEM - IU Granite](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Documentation relative à l’interface utilisateur Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)

>[!NOTE]
>
>En raison de la nature des composants de l’IU Granite (et des différences avec les widgets ExtJS), il existe des différences entre la façon dont les composants interagissent avec l’IU tactile et les widgets ExtJS. [IU classique](/help/sites-developing/developing-components-classic.md).

### Création d’une boîte de dialogue {#creating-a-new-dialog}

Boîtes de dialogue de l’interface utilisateur tactile :

* sont nommées `cq:dialog` ;
* sont définies sous forme de nœud `nt:unstructured` avec le jeu de propriétés `sling:resourceType` ;

* sont situées sous leur nœud `cq:Component` et à côté de leur définition de composant ;
* sont rendues côté serveur (en tant que composants Sling), en fonction de la structure de leur contenu et de la propriété `sling:resourceType` ;
* utilisez la structure de l’interface utilisateur Granite.
* contiennent une structure de noeud décrivant les champs de la boîte de dialogue.

   * Ces nœuds sont `nt:unstructured` avec la propriété `sling:resourceType` obligatoire.

Un exemple de structure de nœud pourrait être :

```xml
newComponent (cq:Component)
  cq:dialog (nt:unstructured)
    content 
      layout 
      items 
        column 
          items 
            file 
            description  
```

La personnalisation d’une boîte de dialogue est similaire au développement d’un composant dans la mesure où la boîte de dialogue est elle-même un composant (c’est-à-dire un balisage rendu par un script de composant avec le comportement/style fourni par une bibliothèque cliente).

Pour consulter des exemples, voir :

* `/libs/foundation/components/text/cq:dialog`
* `/libs/foundation/components/download/cq:dialog`

>[!NOTE]
>
>Si un composant ne possède pas de boîte de dialogue définie pour l’IU tactile, la boîte de dialogue de l’IU classique est utilisée comme solution de secours à l’intérieur d’une couche de compatibilité. Pour personnaliser ce type de boîte de dialogue, vous devez personnaliser la boîte de dialogue de l’IU classique. Consultez [Composants AEM pour l’IU classique](/help/sites-developing/developing-components-classic.md).

### Personnalisation des champs de boîte de dialogue {#customizing-dialog-fields}

>[!NOTE]
>
>Voir :
>
>* la session AEM Gems sur [Personnalisation des champs de boîte de dialogue](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).
>* l’exemple de code correspondant traité dans [Exemple de code - Comment personnaliser les champs de boîte de dialogue](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields).
>


#### Création d’un champ {#creating-a-new-field}

Les widgets de l’IU tactile sont implémentés en tant que composants de l’IU Granite.

Pour créer un widget à utiliser dans une boîte de dialogue de composant pour l’interface utilisateur tactile, vous devez : [créer un composant de champ d’IU Granite ;](/help/sites-developing/granite-ui-component.md).

>[!NOTE]
>
>Pour plus d’informations sur l’interface utilisateur Granite, reportez-vous à la section [Documentation de l’interface utilisateur Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html).

Si vous configurez votre boîte de dialogue comme un conteneur simple pour un élément de formulaire, vous pouvez également voir le contenu principal du contenu de la boîte de dialogue sous la forme de champs de formulaire. La création d’un champ de formulaire nécessite la création d’un type de ressource. Cela équivaut à créer un composant. Pour vous aider dans cette tâche, l’IU Granite propose un composant de champ générique duquel hériter (en utilisant `sling:resourceSuperType`) :

`/libs/granite/ui/components/coral/foundation/form/field`

Plus précisément, l’IU Granite offre divers composants de champ qui conviennent pour une utilisation dans des boîtes de dialogue (ou, de manière plus générale, dans des [formulaires](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)).

>[!NOTE]
>
>Cela diffère de l’IU classique où les widgets sont représentés par des nœuds `cq:Widgets`, chacun avec un `xtype` particulier pour établir la relation avec le widget ExtJS correspondant. Du point de vue de la mise en œuvre, ces widgets sont rendus côté client par le framework ExtJS.

Une fois que vous avez créé votre type de ressource, vous pouvez instancier le champ en ajoutant un nouveau nœud dans la boîte de dialogue, avec la propriété `sling:resourceType` faisant référence au type de ressource que vous venez d’introduire.

#### Création d’une bibliothèque cliente pour le style et le comportement {#creating-a-client-library-for-style-and-behavior}

Si vous souhaitez définir le style et le comportement de votre composant, vous pouvez créer un [bibliothèque cliente](/help/sites-developing/clientlibs.md) qui définit vos CSS/LESS et JS personnalisés.

Pour que votre bibliothèque cliente soit chargée uniquement pour votre boîte de dialogue de composant (c’est-à-dire qu’elle ne sera pas chargée pour un autre composant), vous devez définir la propriété . `extraClientlibs` de votre boîte de dialogue au nom de catégorie de la bibliothèque cliente que vous venez de créer. Ceci est conseillé si votre bibliothèque cliente est assez volumineuse ou si votre champ est spécifique à cette boîte de dialogue et n’est pas nécessaire dans les autres boîtes de dialogue.

Afin que la bibliothèque cliente soit chargée pour toutes les boîtes de dialogue, définissez la propriété Catégorie de votre bibliothèque cliente sur `cq.authoring.dialog`. Il s’agit du nom de la catégorie de la bibliothèque cliente qui est incluse par défaut lors du rendu de toutes les boîtes de dialogue. Vous souhaitez le faire si votre bibliothèque cliente est petite et/ou si votre champ est générique et peut être réutilisé dans d’autres boîtes de dialogue.

Pour consulter un exemple, voir :

* `cqgems/customizingfield/components/colorpicker/clientlibs`

   * fournie par l’[exemple de code](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Extension (héritage d’un champ) {#extending-inheriting-from-a-field}

Selon vos besoins, vous pouvez effectuer l’une des opérations suivantes :

* Étendre un champ de l’IU Granite par héritage de composant (`sling:resourceSuperType`)
* Étendez un widget donné à partir de la bibliothèque de widgets sous-jacente (dans le cas de l’IU Granite, il s’agit de l’IU Coral), en suivant l’API de bibliothèque de widgets (héritage JS/CSS).

#### Accès aux champs de boîte de dialogue {#access-to-dialog-fields}

Vous pouvez également utiliser les conditions de rendu (`rendercondition`) pour contrôler qui a accès à des onglets/champs spécifiques dans votre boîte de dialogue. Par exemple :

```xml
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

### Gestion des événements de champ {#handling-field-events}

La méthode de gestion des événements dans les champs de boîte de dialogue est désormais appliquée avec les [écouteurs d’une bibliothèque cliente personnalisée](#listeners-in-a-custom-client-library). Il s’agit d’un changement par rapport à l’ancienne méthode de [écouteurs dans la structure de contenu](#listeners-in-the-content-structure).

#### Écouteurs dans une bibliothèque cliente personnalisée {#listeners-in-a-custom-client-library}

Pour injecter une logique dans votre champ, vous devez :

1. Faites marquer votre champ avec une classe CSS donnée (le *hook*).
1. Définissez, dans votre bibliothèque cliente, un écouteur JS connecté à ce nom de classe CSS (cela garantit que votre logique personnalisée est limitée à votre champ uniquement et n’affecte pas les autres champs du même type).

Pour ce faire, vous devez connaître la bibliothèque de widgets sous-jacente avec laquelle vous souhaitez interagir. Consultez la [documentation relative à l’IU Coral](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) pour identifier l’événement auquel vous voulez réagir. Cette opération est très similaire au processus que vous deviez effectuer avec ExtJS dans le passé : recherchez la page de documentation d’un widget donné, puis vérifiez les détails de son API d’événement.

Pour consulter un exemple, voir :

* `cqgems/customizingfield/components/clientlibs/customizingfield`

   * fournie par l’[exemple de code](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Écouteurs dans la structure de contenu {#listeners-in-the-content-structure}

Dans l’IU classique avec ExtJS, il était habituel de trouver des écouteurs pour un widget donné dans la structure de contenu. L’obtention de la même valeur dans l’interface utilisateur tactile est différente, car le code d’écouteur JS (ou tout autre code du tout) n’est plus défini dans le contenu.

La structure du contenu décrit la structure sémantique ; elle ne devrait (doit) pas impliquer la nature du widget sous-jacent. En l’absence de code JS dans la structure du contenu, vous pouvez modifier les détails d’implémentation sans avoir à modifier la structure du contenu. En d’autres termes, vous pouvez modifier la bibliothèque de widgets sans avoir à toucher la structure de contenu.

#### Détection de la disponibilité de la boîte de dialogue {#dialog-ready}

Si vous utilisez un script JavaScript personnalisé qui doit être exécuté uniquement lorsque la boîte de dialogue est disponible et prête, vous devez écouter l’événement `dialog-ready`.

Ce événement est déclenché chaque fois que la boîte de dialogue se charge (ou se recharge) et est prête à l’emploi, soit chaque fois qu’une modification (création ou mise à jour) a lieu dans le DOM de la boîte de dialogue.

`dialog-ready` peut être utilisé pour associer du code personnalisé JavaScript qui effectue des personnalisations dans les champs d’une boîte de dialogue ou pour des tâches similaires.

### Validation de champ {#field-validation}

#### Champ obligatoire {#mandatory-field}

Pour marquer un champ donné comme obligatoire, définissez la propriété suivante sur le noeud de contenu de votre champ :

* Nom : `required`
* Type : `Boolean`

Pour consulter un exemple, voir :

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title
```

#### Validation de champ (IU Granite) {#field-validation-granite-ui}

La validation du champ dans l’IU Granite et les composants de l’IU Granite (équivalent aux widgets) est effectuée à l’aide de l’API `foundation-validation`. [Consultez la `foundation-valdiation`documentation de Granite pour plus de détails.](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html)

Pour consulter des exemples, voir :

* `cqgems/customizingfield/components/clientlibs/customizingfield/js/validations.js`

   * fourni par l’[exemple de code](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `/libs/cq/gui/components/authoring/dialog/clientlibs/dialog/js/validations.js`

## Création et configuration d’une boîte de dialogue Conception {#creating-and-configuring-a-design-dialog}

La boîte de dialogue Conception est utilisée lorsqu’un composant possède des détails de conception modifiables en [mode Conception](/help/sites-authoring/default-components-designmode.md).

La définition est très similaire à celle d’une boîte de dialogue[ servant à modifier le contenu](#creating-a-new-dialog), à la différence qu’elle est définie comme un nœud :

* Nom du nœud : `cq:design_dialog`
* Type : `nt:unstructured`

## Création et configuration d’un éditeur statique {#creating-and-configuring-an-inplace-editor}

Un éditeur local permet à l’utilisateur de modifier le contenu directement dans le flux de paragraphe, sans avoir besoin d’ouvrir une boîte de dialogue. Par exemple, les composants Texte et Titre standard disposent tous deux d’un éditeur statique.

Un éditeur statique n’est pas nécessaire/significatif pour chaque type de composant.

Voir [Extension de la création de pages - Ajout d’un nouvel éditeur statique](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor) pour plus d’informations.

## Personnalisation de la barre d’outils de composant {#customizing-the-component-toolbar}

Le [Barre d’outils de composant](/help/sites-developing/touch-ui-structure.md#component-toolbar) permet à l’utilisateur d’accéder à un éventail d’actions pour le composant, telles que la modification, la configuration, la copie et la suppression.

Voir [Extension de la création de page - Ajouter une nouvelle action à une barre d’outils de composant](/help/sites-developing/customizing-page-authoring-touch.md#add-new-action-to-a-component-toolbar) pour plus d’informations.

## Configuration d’un composant pour le rail de références (emprunté/prêté) {#configuring-a-component-for-the-references-rail-borrowed-lent}

Si votre nouveau composant fait référence au contenu d’autres pages, vous pouvez déterminer si vous souhaitez qu’il affecte la variable **Contenu emprunté** et **Contenu prêté** des sections [**Références**](/help/sites-authoring/basic-handling.md#references) Rail.

AEM prêt à l’emploi ne vérifie que le composant Référence. Pour ajouter votre composant, vous devez configurer le bundle OSGi **Configuration de référence du contenu de création de gestion de contenu Web**.

Créez une nouvelle entrée dans la définition, en spécifiant votre composant, avec la propriété à vérifier. Par exemple :

`/apps/<your-Project>/components/reference@parentPath`

>[!NOTE]
>
>Lorsque vous utilisez AEM, plusieurs méthodes permettent de gérer les paramètres de configuration pour ces services. Consultez [Configuration d’OSGi](/help/sites-deploying/configuring-osgi.md) pour avoir plus de détails et connaître les pratiques recommandées.

## Activation et ajout de votre composant au système de paragraphes {#enabling-and-adding-your-component-to-the-paragraph-system}

Une fois le composant développé, il doit être activé pour être utilisé dans un système de paragraphes approprié, de sorte qu’il puisse être utilisé sur les pages requises.

Pour ce faire, procédez comme suit :

* using [Mode de conception](/help/sites-authoring/default-components-designmode.md) lors de la modification d’une page spécifique.
* définition des composants [sur le système de paragraphes d’un modèle.](/help/sites-developing/components-basics.md#adding-your-component-to-the-paragraph-system).

## Configuration d’un système de paragraphes pour que le glissement d’une ressource crée une instance de composant {#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance}

AEM offre la possibilité de configurer un système de paragraphes sur votre page afin que [une instance de votre nouveau composant est automatiquement créée lorsqu’un utilisateur fait glisser une ressource (appropriée) sur une instance de cette page.](/help/sites-authoring/editing-content.md) (au lieu d’avoir toujours à faire glisser un composant vide sur la page).

Ce comportement et la relation actif-à-composant requise peuvent être configurés :

1. Sous la définition de paragraphe de votre conception de page. Par exemple :

   * `/etc/designs/<myApp>/page/par`

   Créez un nœud :

   * Nom : `cq:authoring`
   * Type : `nt:unstructured`


1. Sous cela, créez un nouveau nœud qui contiendra tous les mappages actif à composant :

   * Nom : `assetToComponentMapping`
   * Type : `nt:unstructured`

1. Pour chaque mappage actif à composant, créez un nœud :

   * Nom : text ; il est recommandé que le nom indique l’actif et le type de composant associé, par exemple, « image ».
   * Type : `nt:unstructured`

   Chacun possédant les propriétés suivantes :

   * `assetGroup` :

      * Type : `String`
      * Valeur : groupe auquel l’actif associé appartient, par exemple, `media`
   * `assetMimetype` :

      * Type : `String`
      * Valeur : type mime de l’actif associé, par exemple `image/*`
   * `droptarget` :

      * Type : `String`
      * Valeur : cible de dépôt, par exemple, `image`
   * `resourceType` :

      * Type : `String`
      * Valeur : ressource de composant associée, par exemple, `foundation/components/image`
   * `type` :

      * Type : `String`
      * Valeur : type, par exemple, `Images`






Pour voir des exemples, reportez-vous à :

* `/etc/designs/geometrixx/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-outdoors/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-media/jcr:content/article/article-content-par/cq:authoring`

CODE SUR GITHUB

Vous pouvez trouver le code de cette page sur GitHub.

* [Ouvrez le projet aem-project-archetype sur GitHub](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).
* Téléchargez le projet sous la forme d’[un fichier ZIP](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/archive/master.zip).

>[!NOTE]
>
>La création automatique d’instances de composant est désormais facile à configurer dans l’interface utilisateur lors de l’utilisation de [composants de base](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) et de modèles modifiables. Consultez [Création de modèles de page](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) pour plus d’informations sur la définition des composants automatiquement associés à des types de média donnés.

## Utilisation de l’extension AEM Brackets {#using-the-aem-brackets-extension}

L’[extension AEM Brackets](/help/sites-developing/aem-brackets.md) fournit un workflow fluide pour modifier les composants AEM et les bibliothèques clientes. Elle est basée sur la variable [Brackets](https://brackets.io/) éditeur de code.

L’extension :

* Facilite la synchronisation (aucun Maven ou File Vault requis) pour améliorer le rendement des développeurs et permet également aux développeurs de front-end ayant des connaissances limitées en matière d’AEM de participer à des projets.
* Fournit une prise en charge d’[HTL](https://helpx.adobe.com/fr/experience-manager/htl/user-guide.html), le langage de modèle conçu pour simplifier le développement des composants et renforcer la sécurité.

>[!NOTE]
>
>Brackets est le mécanisme recommandé pour créer des composants. Il remplace la fonctionnalité CRXDE Lite - Créer un composant , qui a été conçue pour l’IU classique.

## Migration à partir d’un composant classique {#migrating-from-a-classic-component}

Lors de la migration d’un composant de l’IU classique vers un composant pouvant être utilisé avec l’IU tactile (exclusivement ou conjointement), les problèmes suivants doivent être anticipés : 

* HTL

   * L’utilisation d’[HTL](https://helpx.adobe.com/fr/experience-manager/htl/user-guide.html) n’est pas obligatoire, mais si le composant doit être mis à jour, c’est l’occasion idéale pour envisager une [migration de JSP vers HTL](/help/sites-developing/components-basics.md#htl-vs-jsp).

* Les composants :

   * migrent le code [ `cq:listener`](/help/sites-developing/developing-components.md#migrating-cq-listener-code) qui utilise des fonctions spécifiques à l’IU classique ;
   * Plugin RTE. Pour plus d’informations, consultez [Configuration de l’éditeur de texte enrichi](/help/sites-administering/rich-text-editor.md) ;
   * [migrent le code `cq:listener`](#migrating-cq-listener-code) qui utilise des fonctions spécifiques à l’IU classique.

* Boîtes de dialogue

   * Vous devrez créer une boîte de dialogue à utiliser dans l’IU tactile. Pour des raisons de compatibilité, l’IU tactile peut utiliser la définition d’une boîte de dialogue d’IU classique, si aucune boîte de dialogue n’a été définie pour l’IU tactile.
   * Le [Outils de modernisation d’AEM](/help/sites-developing/modernization-tools.md) est fourni pour vous aider à étendre les composants existants.
   * Le [mappage d’ExtJS aux composants de l’IU Granite](/help/sites-developing/touch-ui-concepts.md#extjs-and-corresponding-granite-ui-components) fournit une présentation pratique des xtypes ExtJS et des types de nœud avec les types de ressources équivalents dans l’IU Granite.
   * Personnalisation des champs, pour plus d’informations, consultez la session AEM Gems sur [Personnalisation des champs de boîte de dialogue](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).
   * Migration des types vers [Validation de l’IU Granite](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/clientlibs/foundation/js/validation/index.html)
   * Utilisation des écouteurs JS, pour plus d’informations, voir [Gestion des événements de champ](#handling-field-events) et la session AEM Gems sur [Personnalisation des champs de boîte de dialogue](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).

### Migration du code cq:listener {#migrating-cq-listener-code}

Si vous migrez un projet conçu pour l’IU classique, le code `cq:listener` (et les bibliothèques clientes associées aux composants) peut utiliser des fonctions spécifiques à l’IU classique (telles que `CQ.wcm.*`). Pour la migration, vous devez mettre à jour ce code en utilisant les objets/fonctions équivalents dans l’IU tactile.

Si votre projet est complètement migré vers l’interface utilisateur tactile, vous devez remplacer ce code pour utiliser les objets et fonctions appropriés à l’interface utilisateur tactile.

Cependant, si votre projet doit prendre en charge à la fois l’IU classique et l’IU tactile pendant la période de migration (scénario habituel), vous devez mettre en oeuvre un commutateur pour différencier le code distinct référençant les objets appropriés.

Ce mécanisme de basculement peut être implémenté comme suit :

```
if (Granite.author) {
    // touch UI
} else {
    // classic UI
}
```

## Documentation de votre composant {#documenting-your-component}

En tant que développeur, vous souhaitez un accès facile à la documentation des composants afin de pouvoir rapidement comprendre :

* sa description ;
* son utilisation prévue ;
* Structure et propriétés du contenu
* API exposées et points d’extension
* Etc.

Pour cette raison, il est assez facile de rendre tout balisage de documentation existant disponible dans le composant lui-même.

Il suffit de placer un fichier `README.md` dans la structure du composant. Ce MarkDown est ensuite affiché dans la [console du composant](/help/sites-authoring/default-components-console.md).

![chlimage_1-225](assets/chlimage_1-225.png)

Le MarkDown pris en charge est le même que pour les [fragments de contenu](/help/assets/content-fragments-markdown.md).
