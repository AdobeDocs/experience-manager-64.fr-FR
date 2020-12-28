---
title: Développement et outil de comparaison des pages
seo-title: Développement et outil de comparaison des pages
description: 'null'
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 6de5e6f12f123ca2ec45358a138becc410c89e4e
workflow-type: tm+mt
source-wordcount: '481'
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

### Avant AEM 6.4.3 {#prior-to-aem}

Lorsque le contenu est comparé, l’ensemble de l’arborescence jusqu’à la page à comparer est recréé à l’emplacement suivant :

`/content/versionhistory/<userId>/<site structure>`

Parce que, lors de l&#39;utilisation du mécanisme de différences de page, AEM recrée la version précédente de la page, pour utiliser la fonction, l&#39;utilisateur doit disposer de certaines autorisations JCR.

>[!CAUTION]
>
>Pour utiliser la fonction de différenciation de page, l’utilisateur doit disposer de l’autorisation **Modifier/Créer/Supprimer** sur le noeud `/content/versionhistory`.

### À partir de l&#39;AEM 6.4.3 {#as-of-aem}

Lorsque le contenu est comparé, l’ensemble de l’arborescence jusqu’à la page à comparer est recréé à l’emplacement suivant :

`/tmp/versionhistory/`

Ce contenu est créé par un utilisateur de service avec des autorisations limitant la visibilité pour l’utilisateur actuel. Pour cette raison, aucune autorisation spéciale n’est requise.

Une tâche de nettoyage s’exécute automatiquement pour nettoyer ce contenu temporaire.

## Limitations de développeur {#developer-limitations}

Auparavant, dans l’interface utilisateur classique, une attention particulière devait être accordée au développement afin de faciliter la modification AEM (par exemple en utilisant `cq:text` tag lib ou en intégrant le service `DiffService` OSGi dans les composants). Cela n’est plus nécessaire pour la nouvelle fonction de comparaison (diff), puisque cela s’effectue du côté client via la comparaison DOM.

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

