---
title: Tally Essentials
seo-title: Tally Essentials
description: Présentation de la classe Tally
seo-description: Présentation de la classe Tally
uuid: c369c6a1-9ced-4b5c-af43-8c03236eaa52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9941ba90-3d40-4c90-bca8-5db49603cbfa
exl-id: f04ec253-08b8-4ee2-9873-4a51549daeba
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Tally Essentials {#tally-essentials}

Tally est une classe abstraite qui fournit une méthode standard de collecte des commentaires des membres sur la manière dont ils évaluent des produits et services spécifiques. Les commentaires anonymes ne sont pas pris en charge. Le visiteur du site doit s’inscrire et se connecter pour participer et se connecter afin de modifier ses commentaires. L’obligation de se connecter facilite la modération et améliore la valeur des commentaires en empêchant plusieurs publications.

Un composant tally personnalisé peut être créé en étendant la classe tally abstraite.

[](essentials-liking.md) Le Likingest une mise en oeuvre du décompte qui est une forme simple d&#39;expression d&#39;une opinion positive.

[](essentials-voting.md) Le vote est une mise en oeuvre d&#39;un décompte qui est une forme simple d&#39;expression d&#39;une opinion positive ou négative.

[](rating-basics.md) La notation est une mise en oeuvre d&#39;un système d&#39;étoiles qui exprime un éventail d&#39;opinions, du positif au négatif.

À compter de la version AEM 6.1, le composant *poll* n’est plus disponible.

[](reviews-basics.md) Révision d’un composant SCF hybride de  [](essentials-comments.md) commentaires et d’ [évaluations](rating-basics.md).

## Principes élémentaires pour le côté client {#essentials-for-client-side}

* [Personnalisations côté client](client-customize.md)

## Principes élémentaires côté serveur {#essentials-for-server-side}

* [API Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Points de terminaison Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personnalisations côté serveur](server-customize.md)

### Accès aux Talets publiés (UGC) {#accessing-posted-tallies-ugc}

Le contenu généré par l’utilisateur doit être modéré à l’aide de l’une des méthodes standard de modération.\
Voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

Depuis AEM 6.1 Communities, l’utilisation d’un [magasin commun](working-with-srp.md) pour le contenu généré par l’utilisateur inclut l’accès programmatique au contenu généré par l’utilisateur, quelle que soit l’option de stockage choisie (comme ASRP, MSRP ou JSRP).

**L’emplacement et le format du contenu créé par l’utilisateur dans le référentiel peuvent être modifiés sans avertissement**.

Voir :

* [Présentation du fournisseur de ressources de stockage](srp.md)  - Présentation et utilisation du référentiel
* [Notions fondamentales relatives à la SRP et au contenu généré par l’utilisateur](srp-and-ugc.md)  - Exemples et méthodes d’utilitaire SRP
* [Accès au contenu généré par l’utilisateur avec SRP](accessing-ugc-with-srp.md)  - Instructions de codage
* [Refactorisation](socialutils.md)  de SocialUtils : mappage de méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles.
