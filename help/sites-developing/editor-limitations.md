---
title: Limites de l’éditeur
seo-title: Editor Limitations
description: L’éditeur de l’interface utilisateur tactile utilise des superpositions pour interagir avec le contenu confiné dans un iframe. Cette interaction présente certaines limites pour l’utilisation de l’éditeur, mais également pour les développeurs.
seo-description: The editor in the touch-enabled UI makes use of overlays to interact with content confined in an iframe. This interaction creates some limitations in both usage of the editor and also for developers.
uuid: ff524530-3f3a-4c5b-9f94-4aa9aeb9d461
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: introduction
discoiquuid: d748decb-a614-4c9e-a502-d6176b720f1a
exl-id: ce860880-5954-4f72-8ec6-60209c1ec659
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 61%

---

# Limites de l’éditeur{#editor-limitations}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’éditeur de l’interface utilisateur tactile utilise des superpositions pour interagir avec le contenu confiné dans un iframe. Cette interaction présente certaines limites pour l’utilisation de l’éditeur, mais également pour les développeurs. Cette page résume ces limites et fournit des solutions ou des solutions lorsque cela s’avère possible.

## Limites fonctionnelles {#functional-limitations}

Un auteur peut être confronté aux limites fonctionnelles suivantes lors de l’utilisation de l’éditeur pour créer des pages.

### Liens inactifs {#links-not-active}

Lors de la [modification d’une page](/help/sites-authoring/editing-content.md), les liens ne sont pas actifs.

* [Basculez vers le mode **Aperçu**](/help/sites-authoring/editing-content.md#preview-mode) pour naviguer à l’aide des liens de votre contenu.

### Pages de structure {#structure-pages}

Les pages ne peuvent pas être nommées `structure`. Les pages nommées `structure` ne seront pas modifiables dans l’éditeur de page.

## Limitations de CSS {#css-limitations}

Un développeur peut être confronté aux limites suivantes concernant les interactions de l’éditeur avec CSS.

### Éléments à positionnement absolu {#absolutely-positioned-elements}

Les éléments positionnés de manière absolue peuvent entraîner des problèmes de position de leur superposition.

* Si cela se produit, assurez-vous que les dimensions de l’élément à positionnement absolu sont correctes, car l’éditeur crée une superposition avec les mêmes dimensions.

### Unités vh {#vh-units}

Les unités `vh` ne sont pas prises en charge, car la hauteur de l’iFrame doit être réglée automatiquement par AEM.

### Images d’arrière-plan fixes {#fixed-background-images}

Les images d’arrière-plan fixes peuvent ne pas être affichées comme fixes lors du défilement, car elles sont incorporées dans un iframe.

* Sélectionnez **Afficher la page comme publiée** dans les actions de la barre d’en-tête pour afficher correctement la page.

### Hauteur de 100 % {#height}

La hauteur de 100 % n’est pas prise en charge sur l’élément de corps d’une page.

* Il est possible d’appliquer une solution afin d’implémenter un corps plein écran en « étirant » l’élément de corps comme suit :

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Réduction de marge {#margin-collapsing}

Des problèmes de réduction de marge peuvent apparaître si le premier élément enfant de l’élément de corps comporte une marge.

* La solution consiste à ajouter un clearfix au niveau de l’élément de corps comme suit :

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
