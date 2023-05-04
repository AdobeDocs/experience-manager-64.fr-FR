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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 46%

---

# Développement et outil de comparaison des pages{#developing-and-page-diff}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation des fonctionnalités {#feature-overview}

La création de contenu est un processus itératif. Pour être efficace lorsque vous créez du contenu, vous devez pouvoir voir ce qui a changé d’une version à l’autre. L’affichage d’une version de page, puis de l’autre, est inefficace et susceptible d’erreur. Un auteur souhaite pouvoir comparer la page active à une version précédente en même temps que les différences mises en évidence.

L’outil de comparaison des pages permet à l’utilisateur de comparer la page active aux lancements, aux versions précédentes, etc. Pour plus d’informations sur cette fonction utilisateur, voir [Outil de comparaison des pages](/help/sites-authoring/page-diff.md).

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

## Limites des développeurs {#developer-limitations}

Auparavant, dans l’IU classique, il fallait prêter une attention particulière sur le plan du développement pour permettre la comparaison AEM (par exemple pour l’utilisation de la bibliothèque de balises `cq:text` ou pour l’intégration personnalisée du service OSGi `DiffService` dans des composants). Cela n’est plus nécessaire pour la nouvelle fonction de comparaison, car la comparaison côté client se fait par le biais de la comparaison DOM.

Cependant, le développeur doit tenir compte de certaines limites.

* Cette fonctionnalité utilise des classes CSS qui ne sont pas placées dans un espace de noms sur le produit AEM. Si d’autres classes CSS personnalisées ou des classes CSS tierces portant le même nom sont incluses sur la page, l’affichage de la comparaison peut s’en trouver affecté.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Étant donné que la comparaison est côté client et s’exécute au chargement de la page, les ajustements apportés au DOM après l’exécution du service de comparaison côté client ne seront pas pris en compte. Cela peut affecter

   * Composants qui utilisent AJAX pour inclure du contenu
   * Applications sur une seule page
   * Composants JavaScript qui manipulent le DOM lors de l’interaction de l’utilisateur.
