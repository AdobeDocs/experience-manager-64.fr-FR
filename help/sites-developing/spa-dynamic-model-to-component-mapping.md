---
title: Mappage du modèle dynamique avec les composants pour les SPA
seo-title: Dynamic Model to Component Mapping for SPAs
description: Cet article décrit le fonctionnement du mappage du modèle dynamique avec les composants dans le SDK JavaScript SPA pour AEM.
seo-description: This article describes how the dynamic model to component mapping occurs in the Javascript SPA SDK for AEM.
uuid: 337b8d90-efd7-442e-9fac-66c33cc26212
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 8b4b0afc-8534-4010-8f34-cb10475a8e79
exl-id: 2bbbfbaa-b0a1-4f8a-9445-51325d80e368
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 87%

---

# Mappage du modèle dynamique avec les composants pour les SPA{#dynamic-model-to-component-mapping-for-spas}

Ce document décrit le fonctionnement du mappage du modèle dynamique avec les composants dans le SDK JavaScript SPA pour AEM.

>[!NOTE]
>La fonction Éditeur d’application sur une seule page (SPA) requiert AEM Service Pack 2 ou version ultérieure.
>
>L’éditeur SPA est la solution recommandée pour les projets qui nécessitent SPA rendu côté client basé sur une structure (par exemple, React ou Angular).

## Module ComponentMapping {#componentmapping-module}

Le module `ComponentMapping` est fourni au projet front-end sous la forme d’un package NPM. Il contient les composants front-end et permet à l’application sur une seule page (SPA) de mapper les composants front-end avec les types de ressources AEM. Cela permet une résolution dynamique des composants lors de l’analyse du modèle JSON de l’application.

Chaque élément présent dans le modèle contient un champ `:type` qui expose un type de ressource AEM. Une fois monté, le composant front-end peut être rendu à l’aide du fragment de modèle reçu des bibliothèques associées.

Pour plus d’informations sur l’analyse des modèles et l’accès des composants front-end au modèle, consultez le document [Plan directeur d’applications sur une seule page (SPA)](/help/sites-developing/spa-blueprint.md).

Voir aussi le package npm : [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## SPA pilotée par un modèle {#model-driven-single-page-application}

Les SPA qui utilisent le SDK JavaScript SPA pour AEM sont pilotées par des modèles :

1. Les composants front-end s’enregistrent eux-mêmes dans le [magasin de mappage de composants](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Ensuite, le [conteneur](/help/sites-developing/spa-blueprint.md#container), qui a reçu un modèle du [fournisseur de modèles](/help/sites-developing/spa-blueprint.md#the-model-provider), effectue une itération sur son contenu de modèle ( `:items`).

1. Dans le cas d’une page, ses enfants (`:children`) obtiennent d’abord une classe de composants du [mappage des composants](/help/sites-developing/spa-blueprint.md#componentmapping), puis l’instancient.

## Initialisation de l’application {#app-initialization}

Chaque composant est étendu grâce aux capacités de la fonction [ `ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider). L’initialisation se présente donc sous la forme générale suivante :

1. Chaque fournisseur de modèles s’initialise et écoute les modifications apportées au fragment de modèle qui correspond à son composant interne.
1. Le gestionnaire [`PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) doit être initialisé tel qu’il est représenté par le [flux d’initialisation](/help/sites-developing/spa-blueprint.md).

1. Une fois stocké, le gestionnaire de modèles de page renvoie le modèle complet de l’application.
1. Ce modèle est ensuite transmis au composant racine front-end [Conteneur](/help/sites-developing/spa-blueprint.md#container) de l’application.
1. Les fragments du modèle sont finalement propagés à chaque composant enfant.

![app_model_initialization](assets/app_model_initialization.png)
