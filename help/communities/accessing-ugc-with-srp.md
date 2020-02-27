---
title: Accès UGC avec SRP
seo-title: Accès UGC avec SRP
description: Lorsqu’un site est configuré pour utiliser ASRP ou MSRP, l’UGC réel n’est pas stocké dans le magasin de noeuds d’AEM (JCR).
seo-description: Lorsqu’un site est configuré pour utiliser ASRP ou MSRP, l’UGC réel n’est pas stocké dans le magasin de noeuds d’AEM (JCR).
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192

---


# Accès UGC avec SRP {#accessing-ugc-with-srp}

## À propos de SRP {#about-srp}

Tous les composants et fonctionnalités des communautés AEM sont construits sur le cadre des composants [sociaux (SCF)](scf.md), qui appelle l’API SocialResourceProvider pour accéder à tout le contenu généré par l’utilisateur (UGC).

Avant de créer un site communautaire, le fournisseur de ressources de [stockage (SRP)](working-with-srp.md) doit être configuré pour sélectionner une implémentation compatible avec la [topologie](topologies.md)sous-jacente. Les implémentations SRP reposent sur trois options de stockage :

1. [ASRP](asrp.md) - Stockage à la demande Adobe
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## A propos du stockage UGC {#about-ugc-storage}

Ce qui est important à savoir sur le stockage des fichiers UGC, c’est que lorsqu’un site est configuré pour utiliser ASRP ou MSRP, le fichier UGC réel n’est pas stocké dans le magasin [de](../../help/sites-deploying/data-store-config.md) noeuds d’AEM (JCR).

Bien qu’il puisse y avoir des noeuds dans le JCR qui cachent l’UGC pour fournir des métadonnées utiles, ces noeuds ne doivent pas être confondus avec l’UGC réel.

Voir Présentation [du fournisseur de ressources de stockage.](srp.md)

## Best Practice {#best-practice}

Lors du développement de composants personnalisés, les développeurs doivent prendre soin de coder indépendamment de la topologie actuelle choisie, ce qui leur permet de conserver une certaine souplesse pour passer à une nouvelle topologie dans le futur.

### Supposons que JCR n’est pas disponible {#assume-jcr-not-available}

Les méthodes spécifiques au RJC doivent être évitées.

Méthodes à utiliser :

* API Sling (ressource Sling)
   * Ne pas supposer qu’il existe des noeuds JCR

* Evénements OSGi
   * Ne supposez pas qu’il existe des événements JCR

* [Utilitaires de ressources sociales](socialutils.md#socialresourceutilities-package)
* [Utilitaires SCF](socialutils.md#scfutilities-package)

Méthodes à éviter :

* API de noeud
* Evénements JCR
* Lancements de processus (qui utilisent des événements JCR)

### Utiliser les collections de recherche {#use-search-collections}

Différents SRP peuvent avoir différentes langues de requête natives. Il est recommandé d’utiliser les méthodes du package [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) pour appeler le langage de requête approprié.

For more information, see [Search Essentials](search-implementation.md).

## Ressources {#resources}

* [Stockage](working-with-srp.md) du contenu de la communauté - aborde les choix SRP disponibles pour un magasin commun UGC
* [Présentation](srp.md) du fournisseur de ressources de stockage - présentation et présentation de l&#39;utilisation du référentiel
* [SRP et UGC Essentials](srp-and-ugc.md) - Méthodes et exemples d&#39;utilitaires SRP
* [Essentials](search-implementation.md) de recherche - informations essentielles pour la recherche UGC
* [SocialUtils Refactoring](socialutils.md) - mappage des méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles
