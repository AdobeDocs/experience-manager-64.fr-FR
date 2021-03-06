---
title: Test des modèles modifiables dans We.Retail
seo-title: Trying out Editable Templates in We.Retail
description: Test des modèles modifiables dans We.Retail
seo-description: null
uuid: 0d4b97cb-efcc-4312-a783-eae3ecd6f889
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 3cc8ac23-98ff-449f-bd76-1203c7cbbed7
exl-id: 268edb9b-0f52-44c4-a75c-d9dfe39e7d17
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 86%

---

# Test des modèles modifiables dans We.Retail{#trying-out-editable-templates-in-we-retail}

Grâce aux modèles modifiables, les tâches de création et de gestion des modèles ne sont plus réservées aux seuls développeurs. Un type d’utilisateur expérimenté, appelé créateur (ou auteur) de modèles, peut également créer des modèles. Les développeurs doivent encore configurer l’environnement, créer des bibliothèques clientes et créer les composants à utiliser. Cependant, une fois ces bases en place, l’auteur de modèles peut créer et configurer des modèles sans projet de développement.

Toutes les pages We.Retail reposent sur des modèles modifiables, ce qui permet aux non-développeurs d’adapter et de personnaliser les modèles.

## Test {#trying-it-out}

1. Modifiez la page Équipement de la branche principale de langue.

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/equipment.html

1. Notez que le sélecteur de mode ne propose plus de mode Conception. Toutes les pages de We.Retail reposent sur des modèles modifiables. Pour modifier la conception de ces modèles, vous devez recourir à l’éditeur de modèles.
1. Dans la **Informations sur la page** menu **Modifier le modèle**.
1. Vous modifiez à présent le modèle « Page de modèle ».

   Le mode de structure de la page vous permet de modifier la structure du modèle. Cela comprend, par exemple, les composants qui sont autorisés dans le conteneur de mises en page.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. Configurez les stratégies du conteneur de mises en page pour définir les composant autorisés dans le conteneur.

   Les stratégies correspondent aux configurations de conception.

   ![chlimage_1-139](assets/chlimage_1-139.png)

1. Dans la boîte de dialogue de conception du conteneur de mises en page, vous pouvez effectuer les opérations suivantes :

   * Sélectionner une stratégie existante ou en créer une nouvelle pour le conteneur.
   * Sélectionner les composants autorisés dans le conteneur.
   * Définir les composants par défaut à placer lorsqu’une ressource est déplacée dans le conteneur.

   ![chlimage_1-140](assets/chlimage_1-140.png)

1. De retour dans l’éditeur de modèles, vous pouvez modifier la stratégie du composant de texte dans le conteneur de mises en page.

   Vous avez ainsi la possibilité d’effectuer les opérations suivantes :

   * Sélectionner une stratégie existante ou en créer une nouvelle pour le conteneur.
   * Définir les fonctionnalités dont dispose le créateur de la page lorsqu’il utilise ce composant :

      * Sources de collage autorisées
      * Options de mise en forme
      * Styles de paragraphe autorisés
      * Caractères spéciaux autorisés

   De nombreux composants basés sur les composants principaux permettent de configurer des options au niveau du composant par le biais de modèles modifiables, rendant ainsi inutile toute personnalisation de la part des développeurs.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. De retour dans l’éditeur de modèles, vous pouvez utiliser le sélecteur de mode pour passer en mode **Contenu initial** et définir ainsi le contenu requis sur la page.

   Le mode **Disposition** peut être utilisé tel quel sur une page normale pour définir la mise en page du modèle.

## Informations supplémentaires {#more-information}

Pour plus d’informations, reportez-vous au document de création [Création de modèles de page](/help/sites-authoring/templates.md) ou la page du document de développement [Modèles - Modifiables](/help/sites-developing/page-templates-editable.md) pour obtenir des détails techniques complets sur les modèles modifiables.

Vous pouvez également vous renseigner sur les [composants principaux](/help/sites-developing/we-retail-core-components.md). Voir le document de création [Composants principaux](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) pour une présentation des fonctionnalités des composants principaux et du document destiné aux développeurs [Développement des composants principaux](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) pour une présentation technique.
