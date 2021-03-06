---
title: Conceptions et Designer
seo-title: Designs and the Designer
description: Vous devez créer une conception pour votre site web et dans AEM. Pour ce faire, vous allez utiliser le Designer.
seo-description: You will need to create a design for your website and in AEM, you do so by using the Designer
uuid: b880ab49-8bea-4925-9b7b-e911ebda14ee
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f9bcb6eb-1df4-4709-bcec-bef0931f797a
exl-id: 8a4fc7c7-03bc-44db-93f1-dbd76fc9dbd7
source-git-commit: 9ae048ca2811a56c5d6f0b2415fcfcccc4384dbf
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 55%

---

# Conceptions et Designer{#designs-and-the-designer}

>[!CAUTION]
>
>Cet article explique comment créer un site web à partir de l’IU classique. Adobe vous recommande de tirer parti des technologies AEM les plus récentes pour vos sites web. Vous en trouverez une description détaillée dans l’article [Prise en main du développement d’AEM Sites](/help/sites-developing/getting-started.md).

Designer permet de créer une conception pour votre site Web à l’aide de la méthode [IU classique](/help/release-notes/touch-ui-features-status.md) dans AEM.

>[!NOTE]
>
>Pour plus d’informations sur l’accessibilité web, voir [AEM et les instructions pour l’accessibilité web](/help/managing/web-accessibility.md).

## Utilisation de Designer {#using-the-designer}

Votre conception peut être définie dans la variable **designs** de la section **Outils** tab :

![screen_shot_2012-02-01at30237pm](assets/screen_shot_2012-02-01at30237pm.png)

Ici, vous pouvez créer la structure requise pour stocker la conception, puis stocker les feuilles de style en cascade (CSS) et les images requises.

Les conceptions sont stockées sous `/apps/<your-project>`. Le chemin d’accès à la conception à utiliser pour un site web est spécifié à l’aide de la propriété `cq:designPath` du nœud `jcr:content`.

![chlimage_1-74](assets/chlimage_1-74.png)

>[!NOTE]
>
>Toutes les modifications apportées à une page dans le mode Création sont conservées sous le nœud de conception du site et sont automatiquement appliquées à toutes les pages qui présentent la même conception.

## Éléments nécessaires {#what-you-will-need}

Pour créer votre conception, vous aurez besoin des éléments suivants :

**CSS** - Les feuilles de style en cascade définissent les formats de zones spécifiques sur vos pages.

**Images** - Toutes les images que vous utilisez pour des fonctionnalités telles que les arrière-plans et les boutons.

### Points à prendre en compte lors de la conception de votre site web {#considerations-when-designing-your-website}

Lors du développement d’un site web, il est vivement recommandé de stocker des images et des fichiers CSS sous `/apps/<your-project>` vous pouvez ainsi référencer vos ressources en fonction de la conception actuelle, comme décrit par le fragment de code suivant.

```xml
<%= currentDesign.getPath() + "/static/img/icon.gif %>
```

L’exemple précédent offre plusieurs avantages :

* Les composants peuvent avoir une apparence différente selon que chaque site utilise un chemin de conception différent.
* La reconception du site web peut simplement être effectuée en pointant le chemin de conception vers un noeud différent à la racine du site à partir de `design/v1` to `design/v2.`

* `/etc/designs` et `/content` sont les seules URL externes que le navigateur voit vous protéger d’un utilisateur externe qui se demande ce qui se trouve sous votre `/apps` arborescence. Les avantages des URL ci-dessus aident également l’administrateur système à mieux configurer la sécurité, dans la mesure où vous limitez l’exposition des ressources à une poignée d’emplacements distincts.
