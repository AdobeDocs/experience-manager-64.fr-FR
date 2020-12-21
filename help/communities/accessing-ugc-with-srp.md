---
title: Accès à l'UGC avec SRP
seo-title: Accès à l'UGC avec SRP
description: Lorsqu’un site est configuré pour utiliser ASRP ou MSRP, l’UGC réel n’est pas stocké dans AEM Node Store (JCR).
seo-description: Lorsqu’un site est configuré pour utiliser ASRP ou MSRP, l’UGC réel n’est pas stocké dans AEM Node Store (JCR).
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# Accès à UGC avec SRP {#accessing-ugc-with-srp}

## À propos de SRP {#about-srp}

Tous les composants et fonctionnalités AEM Communities sont construits sur la structure de composants sociaux [SCF (Social Component Framework)](scf.md), qui appelle l’API SocialResourceProvider pour accéder à tout le contenu généré par l’utilisateur (UGC).

Avant la création d&#39;un site communautaire, le [fournisseur de ressources d&#39;enregistrement (SRP)](working-with-srp.md) doit être configuré pour sélectionner une implémentation compatible avec la [topologie sous-jacente](topologies.md). Les mises en oeuvre du PRS reposent sur trois options d’enregistrement :

1. [ASRP](asrp.md)  - enregistrement à la demande Adobe
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md)  - JCR

## À propos de l&#39;Enregistrement UGC {#about-ugc-storage}

Ce qui est important à savoir sur l&#39;enregistrement de l&#39;UGC, c&#39;est que lorsqu&#39;un site est configuré pour utiliser ASRP ou MSRP, l&#39;UGC réel n&#39;est pas stocké dans AEM [Node store](../../help/sites-deploying/data-store-config.md) (JCR).

Bien qu’il puisse y avoir des noeuds dans le JCR qui cachent l’UGC pour fournir des métadonnées utiles, ces noeuds ne doivent pas être confondus avec l’UGC réel.

Voir [Présentation du fournisseur de ressources d&#39;Enregistrement.](srp.md)

## Meilleure pratique {#best-practice}

Lors du développement de composants personnalisés, les développeurs doivent veiller à coder indépendamment de la topologie actuelle choisie, en conservant ainsi la flexibilité nécessaire pour passer à une nouvelle topologie à l’avenir.

### Supposons que JCR n&#39;est pas disponible {#assume-jcr-not-available}

Les méthodes spécifiques au JCR doivent être évitées.

Méthodes à utiliser :

* API Sling (ressource Sling)
   * Ne supposez pas qu’il y ait des noeuds JCR

* ÉVÉNEMENTS OSGi
   * Ne pas supposer qu’il existe des événements JCR

* [Utilitaires de ressources sociales](socialutils.md#socialresourceutilities-package)
* [Utilitaires SCF](socialutils.md#scfutilities-package)

Méthodes à éviter :

* API de noeud
* Événements JCR
* Lancements de processus (utilisant des événements JCR)

### Utiliser les collections de recherche {#use-search-collections}

Différents fournisseurs de services de gestion des ressources peuvent avoir différentes langues de requête natives. Il est recommandé d’utiliser les méthodes du package [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) pour appeler la langue de requête appropriée.

Pour plus d&#39;informations, consultez la section [Essentials de recherche](search-implementation.md).

## Ressources {#resources}

* [Enregistrement](working-with-srp.md)  de contenu de la communauté - aborde les options SRP disponibles pour un magasin commun UGC.
* [Présentation](srp.md)  du fournisseur de ressources d&#39;Enregistrement - présentation et utilisation du référentiel
* [SRP et UGC Essentials](srp-and-ugc.md)  - Exemples et méthodes d&#39;utilitaire SRP
* [Essentials](search-implementation.md)  de recherche - informations essentielles pour rechercher l&#39;UGC
* [SocialUtils Refactoring](socialutils.md)  - mappage des méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles
