---
title: Fonction de recherche
seo-title: Search Feature
description: Ajout et configuration de la recherche sur un site Communities
seo-description: Adding and configuring Search to a Communities site
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
exl-id: 15d8bd59-397e-4bd3-b0a2-b6893c015798
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 29%

---

# Fonction de recherche {#search-feature}

La fonction de recherche fonctionne avec d’autres fonctions, comme les forums, et permet de rechercher du contenu.

Lors de l’ajout de la possibilité de rechercher des publications saisies par des membres de la communauté, appelées contenu généré par l’utilisateur (UGC), deux composants sont disponibles : [ `Search`](#search-features) et [ `Search Results`](#search-results).

La page qui comprend la variable `Search Results` prend en charge la recherche et l’affichage des résultats.

La page qui comprend la variable `Search`fournit un emplacement où lancer une recherche avec les résultats apparaissant sur la `Search Results` page.

La fonction de recherche peut être utilisée avec n’importe quelle autre fonction permettant aux visiteurs et aux membres du site d’afficher du contenu.

## Rechercher {#search-features}

### Ajout du composant Rechercher à une page {#add-search-to-a-page}

Pour ajouter une `Search` sur une page en mode création, utilisez l’explorateur de composants pour accéder à `Communities / Search` et faites-le glisser sur la page. Utilisation de `Search` nécessite une deuxième page pour la variable `Search Results.`

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la bibliothèque côté client requise, `cq.social.hbs.search`, est inclus, c’est comme cela que la variable `Search` s’affiche.

![chlimage_1-373](assets/chlimage_1-373.png)

### Configuration du composant Rechercher {#configure-the-added-search}

Sélectionnez le `Search` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-374](assets/chlimage_1-374.png)

Sous , **[!UICONTROL Paramètres de recherche]** , indiquez comment les chemins d’accès sont des recherches lorsqu’une requête est entrée par un visiteur.

![chlimage_1-375](assets/chlimage_1-375.png)

* **[!UICONTROL Chemins de recherche]** Lorsque vous ajoutez des chemins de recherche à l’aide du bouton Ajouter un élément, la recherche de contenu est limitée. Par exemple, pour limiter la recherche à un forum spécifique, sélectionnez un composant de forum placé dans une page :

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Page de résultats]**
Les résultats s’affichent sur une page distincte spécifiée à l’aide du navigateur pour sélectionner une page contenant le 
`Search Results` component.

## Résultats de la recherche {#search-results}

### Ajout du composant Résultats de la recherche à une page {#add-search-results-to-a-page}

Pour ajouter une `Search Results` sur une page en mode création, utilisez l’explorateur de composants pour accéder à

* `Communities / Search Results`

et faites-le glisser sur la page. Contrairement au composant Rechercher, la deuxième page n’est pas nécessaire, car les résultats s’affichent sur la même page.

Si vous utilisez Rechercher ailleurs dans le site web, cette page avec `Search Results` peut être configuré pour être `Result Page` pour toutes les instances de `Search`.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la bibliothèque côté client requise, `cq.social.hbs.search`, est inclus, c’est comme cela que la variable `Search Result` apparaît :

![chlimage_1-376](assets/chlimage_1-376.png)

### Configuration du composant Résultats de la recherche ajouté {#configure-the-added-search-result}

Sélectionnez le `Search Results` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-377](assets/chlimage_1-377.png)

Sous , **[!UICONTROL Paramètres des résultats de recherche]** , il est possible de spécifier les chemins inclus dans la recherche lorsqu’une requête est entrée par un visiteur.

![chlimage_1-378](assets/chlimage_1-378.png)

* **[!UICONTROL Résultats de la recherche par page]**
Définissez le nombre de rubriques/publications affichées par page. La valeur par défaut est 10.

* **[!UICONTROL Chemins de recherche]** Lorsque vous ajoutez des chemins de recherche à l’aide du bouton Ajouter un élément, la recherche de contenu est limitée.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Principes de recherche](search-implementation.md) pour les développeurs.
