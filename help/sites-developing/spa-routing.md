---
title: Routage du modèle de SPA
seo-title: SPA Model Routing
description: Concernant les applications sur une seule page (SPA) dans AEM, c’est l’application qui est responsable du routage. Ce document décrit le mécanisme de routage, le contrat et les options disponibles.
seo-description: For single page applications in AEM, the app is responsible for the routing. This document describes the routing mechanism, the contract, and options available.
uuid: 93b4f85a-a240-42d4-95e2-e8b790df7723
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: d9f1e24e-51a9-4f28-b2cd-2e97aed63a24
exl-id: 865f524d-6b54-43c8-9b28-86a766e010a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 89%

---

# Routage du modèle de SPA {#spa-model-routing}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Concernant les applications sur une seule page (SPA) dans AEM, c’est l’application qui est responsable du routage. Ce document décrit le mécanisme de routage, le contrat et les options disponibles.

>[!NOTE]
>
>La fonction Éditeur d’application sur une seule page (SPA) requiert AEM Service Pack 2 ou version ultérieure.
>
>L’éditeur de SPA est la solution recommandée pour les projets nécessitant un rendu côté client basé sur un framework de SPA (par exemple React ou Angular).

## Routage du projet {#project-routing}

L’application est responsable du routage et est ensuite implémentée par les développeurs front-end du projet. Ce document décrit le routage spécifique au modèle renvoyé par le serveur AEM. La structure des données du modèle de page expose l’URL de la ressource sous-jacente. Le projet front-end peut utiliser n’importe quelle bibliothèque ou personnalisée fournissant des fonctionnalités de routage. Si un itinéraire attend un fragment de modèle, il est possible d’effectuer un appel à la fonction `PageModelManager.getData()`. Lorsqu’un itinéraire de modèle a été modifié, il est nécessaire de déclencher un événement pour avertir les bibliothèques d’écoute, notamment l’éditeur de page.

## Architecture {#architecture}

Pour obtenir une description détaillée, consultez la section [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager) du Plan directeur d’applications sur une seule page (SPA).

## ModelRouter {#modelrouter}

Lorsque l’option `ModelRouter` est activée, les fonctions de l’API d’historique HTML5 `pushState` et `replaceState` sont encapsulées pour garantir qu’un fragment donné du modèle a été récupéré au préalable et est accessible. Le composant front-end enregistré est ensuite informé que le modèle a été modifié.

## Routage manuel ou automatique {#manual-vs-automatic-model-routing}

`ModelRouter` automatise la récupération des fragments du modèle. Cependant, comme tout outil automatisé, il comporte des restrictions. Si nécessaire, il est possible de désactiver ou de configurer `ModelRouter` pour ignorer les chemins d’accès à l’aide des propriétés des métadonnées (voir la section Propriétés des métadonnées dans le document [Composant de page SPA ](/help/sites-developing/spa-page-component.md)). Les développeurs front-end peuvent alors mettre en œuvre leur propre couche de routage de modèle en demandant à la fonction `PageModelManager` de charger tout fragment de modèle donné à l’aide de la fonction `getData()`.

>[!NOTE]
>
>Actuellement, l’exemple de projet React de We.Retail Journal illustre l’approche automatisée, tandis que le projet Angular illustre l’approche manuelle. Une approche semi-automatisée serait également un cas d’utilisation valide.

>[!CAUTION]
>
>La version actuelle de `ModelRouter` ne prend en charge que l’utilisation d’URL pointant vers le chemin de ressource réel des points d’entrée de Sling Model. Elle ne prend pas en charge l’utilisation de Vanity URL ni d’alias.

## Contrat de routage {#routing-contract}

L’implémentation actuelle repose sur l’hypothèse que le projet de SPA utilise l’API d’historique HTML5 pour le routage vers les différentes pages de l’application.

### Configuration {#configuration}

`ModelRouter` prend en charge le concept de routage de modèle en écoutant les appels `pushState` et `replaceState` pour récupérer au préalable les fragments de modèle. En interne, il déclenche le chargement de `PageModelManager` pour charger le modèle correspondant à une URL donnée, et lance un `cq-pagemodel-route-changed` que d’autres modules peuvent écouter.

Par défaut, ce comportement est activé automatiquement. Pour la désactiver, le SPA doit effectuer le rendu de la propriété meta suivante :

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Notez que chaque route de la SPA doit correspondre à une ressource accessible dans AEM (par exemple, `/content/mysite/mypage"`), étant donné que `PageModelManager` essaie automatiquement de charger le modèle de page correspondant une fois la route sélectionnée. Cependant, la SPA peut, si nécessaire, définir une « liste bloquée » d’itinéraires que `PageModelManager` doit ignorer :

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
