---
title: Développement et outil de comparaison des pages
seo-title: Developing and Page Diff
description: Développement et outil de comparaison des pages
seo-description: null
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
exl-id: 365e944d-d8a3-4f4e-8925-88629845232f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 73%

---

# Développement et outil de comparaison des pages{#developing-and-page-diff}

## Présentation des fonctionnalités {#feature-overview}

La création de contenu est un processus itératif. Pour être efficace lorsque vous créez du contenu, vous devez pouvoir voir ce qui a changé d’une version à l’autre. Afficher les versions en alternance est une méthode inefficace avec un fort risque d’erreur. Un auteur souhaite afficher, côte à côte, deux versions d’une page afin de les comparer en mettant les différences en évidence.

L’outil de comparaison des pages permet à un utilisateur de comparer la page active aux lancements, aux versions précédentes, etc. Pour plus d’informations sur cette fonctionnalité utilisateur, voir [Outil de comparaison des pages](/help/sites-authoring/page-diff.md).

## Détails de l’opération {#operation-details}

Lors de la comparaison des versions d’une page, la version précédente que l’utilisateur souhaite comparer est recréée en arrière-plan par AEM pour faciliter la comparaison. Cette opération est nécessaire pour pouvoir restituer le contenu [pour une comparaison côte à côte](/help/sites-authoring/page-diff.md#presentation-of-differences).

Cette opération de recréation, réalisée par AEM en interne, est transparente pour l’utilisateur et ne nécessite aucune intervention. Cependant, un administrateur qui consulte le référentiel, par exemple dans CRX DE Lite, voit ces versions recréées dans la structure de contenu.

Selon le niveau de correctif AEM, le comportement est différent et peut nécessiter certaines autorisations pour fonctionner correctement.

### Avant la version 6.4.3 d’AEM {#prior-to-aem}

Lorsque le contenu est comparé, l’ensemble de l’arborescence jusqu’à la page à comparer est recréé à l’emplacement suivant :

`/content/versionhistory/<userId>/<site structure>`

En effet, lors de l’utilisation du mécanisme de comparaison des pages, AEM recrée la version précédente de la page afin d’utiliser la fonction, l’utilisateur doit disposer de certaines autorisations JCR.

>[!CAUTION]
>
>Pour utiliser la fonction de comparaison des pages, l’utilisateur doit disposer de la variable **Modifier/Créer/Supprimer** autorisation sur le noeud `/content/versionhistory`.

### À partir de AEM 6.4.3 {#as-of-aem}

Lorsque le contenu est comparé, l’ensemble de l’arborescence jusqu’à la page à comparer est recréé à l’emplacement suivant :

`/tmp/versionhistory/`

Ce contenu est créé par un utilisateur de service avec des autorisations limitant la visibilité de l’utilisateur actuel. Pour cette raison, aucune autorisation spéciale n’est requise.

Une tâche de nettoyage s’exécute automatiquement pour nettoyer ce contenu temporaire.

## Limitations de développeur {#developer-limitations}

Auparavant, dans l’interface utilisateur classique, une attention particulière devait être accordée au développement pour faciliter AEM différences (comme l’utilisation de `cq:text` bibliothèque de balises ou intégration personnalisée `DiffService` Service OSGi dans les composants). Cela n’est plus nécessaire pour la nouvelle fonction de comparaison (diff), puisque cela s’effectue du côté client via la comparaison DOM.

Cependant, il subsiste un certain nombre de restrictions qui doivent être prises en compte par le développeur.

* Cette fonctionnalité utilise des classes CSS qui ne sont pas placées dans un espace de noms sur le produit AEM. Si d’autres classes CSS personnalisées ou des classes CSS tierces portant le même nom sont incluses sur la page, l’affichage de la comparaison peut s’en trouver affecté.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Étant donné que la comparaison s’effectue du côté client et s’exécute au chargement de la page, les réglages apportés au DOM après l’exécution de ce service de comparaison ne sont pas pris en compte. Cela peut avoir une incidence sur éléments suivants :

   * Composants qui utilisent AJAX pour intégrer du contenu
   * Applications sur une seule page
   * Composants basés sur JavaScript qui manipulent le DOM lors d’une interaction de l’utilisateur
