---
title: Accès au contenu généré par l’utilisateur avec SRP
seo-title: Accès au contenu généré par l’utilisateur avec SRP
description: Lorsqu’un site est configuré pour utiliser ASRP ou MSRP, le contenu généré par l’utilisateur réel n’est pas stocké dans AEM magasin de noeuds (JCR).
seo-description: Lorsqu’un site est configuré pour utiliser ASRP ou MSRP, le contenu généré par l’utilisateur réel n’est pas stocké dans AEM magasin de noeuds (JCR).
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Accès au contenu généré par l’utilisateur avec SRP {#accessing-ugc-with-srp}

## À propos de SRP {#about-srp}

Tous les composants et fonctionnalités AEM Communities sont créés sur la [structure de composants sociaux (SCF)](scf.md), qui appelle l’API SocialResourceProvider pour accéder à tout le contenu généré par l’utilisateur.

Avant la création d’un site communautaire, le [fournisseur de ressources de stockage (SRP)](working-with-srp.md) doit être configuré pour sélectionner une implémentation conforme à la [topologie sous-jacente](topologies.md). Les mises en oeuvre de la SRP reposent sur trois options de stockage :

1. [ASRP](asrp.md)  : stockage Adobe à la demande
2. [MSRP](msrp.md)  - MongoDB
3. [JSRP](jsrp.md)  - JCR

## À propos du stockage UGC {#about-ugc-storage}

Ce qu’il est important de savoir sur le stockage du contenu généré par l’utilisateur, c’est que lorsqu’un site est configuré pour utiliser ASRP ou MSRP, le contenu généré par l’utilisateur réel n’est pas stocké dans AEM [magasin de noeuds](../../help/sites-deploying/data-store-config.md) (JCR).

Bien qu’il puisse y avoir des noeuds dans JCR qui cachent le contenu créé par l’utilisateur pour fournir des métadonnées utiles, ces noeuds ne doivent pas être confondus avec le contenu créé par l’utilisateur réel.

Voir [Présentation du fournisseur de ressources de stockage.](srp.md)

## Bonne pratique {#best-practice}

Lors du développement de composants personnalisés, les développeurs doivent veiller à ne pas coder en fonction de la topologie actuelle choisie, en conservant ainsi la possibilité de passer à une nouvelle topologie à l’avenir.

### Supposons que JCR n’est pas disponible {#assume-jcr-not-available}

Les méthodes spécifiques à JCR doivent être évitées.

Méthodes d’utilisation :

* API Sling (ressource Sling)
   * Ne supposez pas qu’il existe des noeuds JCR

* Événements OSGi
   * Ne supposez pas qu’il y ait des événements JCR

* [Utilitaires de ressources sociales](socialutils.md#socialresourceutilities-package)
* [Utilitaires SCF](socialutils.md#scfutilities-package)

Méthodes à éviter :

* API Node
* Événements JCR
* Lanceurs de workflow (qui utilisent des événements JCR)

### Utilisation des collections de recherche {#use-search-collections}

Différents SRP peuvent avoir différents langages de requête natifs. Il est recommandé d’utiliser des méthodes du package [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) pour appeler le langage de requête approprié.

Pour plus d’informations, voir [Notions fondamentales sur la recherche](search-implementation.md).

## Ressources {#resources}

* [Stockage de contenu de la communauté](working-with-srp.md)  : discute des choix de SRP disponibles pour un magasin commun UGC.
* [Présentation du fournisseur de ressources de stockage](srp.md)  - Présentation et utilisation du référentiel
* [Notions fondamentales relatives à la SRP et au contenu généré par l’utilisateur](srp-and-ugc.md)  - Exemples et méthodes d’utilitaire SRP
* [Notions fondamentales sur la recherche](search-implementation.md)  : informations essentielles pour rechercher le contenu généré par l’utilisateur
* [Refactorisation](socialutils.md)  de SocialUtils : mappage de méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles.
