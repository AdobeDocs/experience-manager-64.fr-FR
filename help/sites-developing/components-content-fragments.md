---
title: Composants pour les fragments de contenu
seo-title: Components for Content Fragments
description: Les fragments de contenu AEM sont créés et gérés sous forme de ressources indépendantes de la page
seo-description: AEM content fragments are created and managed as page-independent assets
uuid: 289ed9cb-9531-43a9-b0d8-a3499e2e9ee5
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 76b63c7c-f7ea-46be-8d10-6c1a30af2e2b
pagetitle: Components for Content Fragments
exl-id: 516c1561-5c13-4301-8009-9b021087cec7
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 84%

---

# Composants pour les fragments de contenu{#components-for-content-fragments}

>[!CAUTION]
>
>Certaines fonctionnalités de fragment de contenu nécessitent l’application de la fonction [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md).

## Composants pour la création de fragment {#components-for-fragment-authoring}

>[!CAUTION]
>
>Il n’est pas recommandé d’étendre ou de modifier les composants utilisés dans l’éditeur de fragments, car ils peuvent encore être modifiés.

Voir [API de gestion des fragments de contenu - côté client](/help/sites-developing/customizing-content-fragments.md#the-content-fragment-management-api-client-side).

## Composants pour la création de page {#components-for-page-authoring}

>[!CAUTION]
>
>Le [composant de base Fragment de contenu](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html) est désormais recommandé. Voir [Développement de composants de base](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) pour plus d’informations.
>
>Cette section détaille le composant d’origine qui peut être utilisé avec des fragments de contenu (**Fragment de contenu** dans le groupe **Général**).

Les fragments de contenu Adobe Experience Manager (AEM) sont [créés et gérés en tant que ressources indépendantes de la page](/help/assets/content-fragments.md). Ils vous permettent de créer du contenu compatible avec tous les canaux, ainsi que des variations (éventuellement spécifiques aux canaux). [Vous pouvez ensuite utiliser ces fragments et leurs variantes lors de la création de vos pages de contenu](/help/sites-authoring/content-fragments.md). Vous pouvez également utiliser une ressource de fragment de contenu existante en procédant comme suit : [le faisant glisser de l’explorateur de ressources vers la page ;](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page) (comme pour d’autres composants basés sur des ressources, tels que le composant de base Image). Le composant de fragment de contenu prêt à l’emploi affiche un seul [élément](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) du fragment de contenu référencé. À l’aide de la boîte de dialogue du composant, vous pouvez définir la variable [élément, variation et plage de paragraphes de fragment](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) que vous souhaitez afficher sur la page.

>[!NOTE]
>
>Ce composant de fragment de contenu a été introduit dans AEM 6.2 en tant que version améliorée du composant Article, lequel a été abandonné.

>[!NOTE]
>
>Les fragments de contenu ne sont pas disponibles dans l’interface utilisateur classique.

### Définition {#definition}

Le composant **Fragment de contenu** est utilisé pour contenir une référence à un élément de fragment de contenu (éléments textuels améliorés). Le type de ressource pour le fragment de contenu est :

* `dam/cfm/components/contentfragment/contentfragment`

La référence est définie dans la propriété :

* `fileReference`

Seul l’éditeur de l’IU tactile prend entièrement en charge les composants de fragment de contenu, dont la bibliothèque cliente :

* `cq.authoring.editor.plugin.cfm`

Cette bibliothèque ajoute à l’éditeur des fonctionnalités spécifiques aux fragments de contenu. Par exemple, il est possible d’ajouter et de configurer des fragments de contenu sur la page, ainsi que de rechercher des éléments de contenu dans le navigateur de ressources et du contenu associé dans le panneau latéral.

### Contenu intermédiaire {#in-between-content}

Le composant **Fragment de contenu** vous permet de déposer des composants supplémentaires entre les différents paragraphes de l’[élément](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) affiché. À la base, l’élément affiché est composé de différents paragraphes (chaque paragraphe est marqué par un retour chariot). Entre chacun de ces paragraphes, vous pouvez insérer du contenu en utilisant d’autres composants.

D’un point de vue technique, chaque paragraphe de l’élément affichéréside dans son propre parsys, et chaque composant que vous ajoutez entre les paragraphes est (concrètement) inséré dans le parsys.

En d’autres termes, si l’instance du composant de fragment de contenu est composée de trois paragraphes, le composant possède trois parsys différents dans le référentiel. Tout le contenu intermédiaire ajouté au fragment de contenu se trouve réellement à l’intérieur de ces parsys.

Dans le référentiel, le contenu intermédiaire est stocké par rapport à sa position dans la structure de paragraphe globale, c’est-à-dire qu’il n’est pas rattaché au contenu réel du paragraphe.

Pour illustrer cela, prenons l’exemple suivant :

* Une instance d’un fragment de contenu composé de trois paragraphes
* Du contenu qui a déjà été inséré après le deuxième paragraphe

   * Cela signifie que le contenu sera stocké dans le deuxième parsys.

Fondamentalement, si la structure de paragraphe de cette instance change (en modifiant la variation, l’élément ou la plage de paragraphes affichés), cela peut affecter le contenu intermédiaire affiché lorsque le contenu du fragment de contenu :

* Est modifié et qu’un autre paragraphe est ajouté avant le deuxième paragraphe :

   * Le contenu intermédiaire est affiché après le paragraphe nouvellement créé (le second paragraphe contient alors le paragraphe nouvellement créé).

* Est modifié et que le deuxième paragraphe est supprimé :

   * Le contenu intermédiaire est affiché après le paragraphe qui était précédemment le troisième (le deuxième paragraphe contient alors le troisième paragraphe précédent).

* Est configuré de sorte que seul le premier paragraphe soit affiché :

   * Le contenu entre les deux n’est pas affiché (le deuxième parsys n’est plus rendu en raison de la nouvelle configuration).

### Personnalisation du composant Fragment de contenu {#customizing-the-content-fragment-component}

Pour utiliser le composant de fragment de contenu prêt à l’emploi comme plan directeur d’une extension, vous devez respecter le contrat suivant :

* Réutiliser le script de rendu HTL et son POJO associé pour voir comment la fonctionnalité de contenu intermédiaire est implémentée.
* Réutiliser le noeud de fragment de contenu : `cq:editConfig`

   * Le `afterinsert`/ `afteredit`/ `afterdelete` Les écouteurs sont utilisés pour déclencher des événements JS. Ces événements sont gérés dans la bibliothèque cliente `cq.authoring.editor.plugin.cfm` pour afficher le contenu associé dans le panneau latéral.
   * Les `cq:dropTargets` sont configurés de manière à prendre en charge la gestion des fragments de contenu.
   * `cq:inplaceEditing` est configuré de sorte à prendre en charge la création d’un fragment de contenu dans l’éditeur de pages. L’éditeur de fragment local est défini dans la bibliothèque cliente `cq.authoring.editor.plugin.cfm` et permet à un lien rapide d’ouvrir [l’élément/la variation](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) dans l’[éditeur de fragment](/help/assets/content-fragments-variations.md).

### Réécriture d’actifs avant le rendu {#asset-rewriting-before-rendering}

La gestion de fragments de contenu utilise un processus de rendu interne pour générer la sortie HTML finale pour une page. Ceci est utilisé en interne par le composant Fragment de contenu, mais également par le processus en arrière-plan qui met à jour les fragments référencés sur les pages de référencement.

En interne, Sling Rewriter est utilisé pour ce rendu. La configuration correspondante se trouve à l’adresse `/libs/dam/config/rewriter/cfm` et peuvent être ajustés si nécessaire. Voir [Apache Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) pour plus d’informations.

La configuration prête à l’emploi utilise les transformateurs suivants :

* `transformer-cfm-payloadfilter` - pour récupérer le `body` part ( `<body>...</body>`) du HTML du fragment uniquement

* `transformer-cfm-parfilter` : filtre les paragraphes indésirables si une plage de paragraphes est spécifiée (comme cela peut être fait avec le composant Fragment de contenu)
* `transformer-cfm-assetprocessor` : est utilisé en interne pour récupérer une liste des ressources incorporées au fragment

Le processus de rendu est exposé via ` [com.adobe.cq.dam.cfm.content.FragmentRenderService](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html)` et peut être exploité (par exemple) par des composants personnalisés, si nécessaire.
