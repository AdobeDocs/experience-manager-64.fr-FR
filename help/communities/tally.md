---
title: Tally Essentials
seo-title: Tally Essentials
description: Présentation de la classe Tally
seo-description: Tally class overview
uuid: c369c6a1-9ced-4b5c-af43-8c03236eaa52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9941ba90-3d40-4c90-bca8-5db49603cbfa
exl-id: f04ec253-08b8-4ee2-9873-4a51549daeba
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Tally Essentials {#tally-essentials}

Tally est une classe abstraite qui fournit une méthode standard de collecte des commentaires des membres sur la manière dont ils évaluent des produits et services spécifiques. Les commentaires anonymes ne sont pas pris en charge. Le visiteur du site doit s’inscrire et se connecter pour participer et se connecter afin de modifier ses commentaires. L’obligation de se connecter facilite la modération et améliore la valeur des commentaires en empêchant plusieurs publications.

Un composant tally personnalisé peut être créé en étendant la classe tally abstraite.

[J’aime](essentials-liking.md) est une mise en oeuvre de tally qui est une forme simple d&#39;expression d&#39;une opinion positive.

[Vote](essentials-voting.md) est une mise en oeuvre de tally qui est une forme simple d&#39;expression d&#39;une opinion positive ou négative.

[Évaluation](rating-basics.md) est une mise en oeuvre de tally qui utilise un système star pour exprimer un éventail d&#39;opinions allant du positif au négatif.

À partir de la version AEM 6.1, la variable *sondage* n’est plus disponible.

[Révisions](reviews-basics.md) est un composant SCF qui est hybride d’ [commentaires](essentials-comments.md) et [note](rating-basics.md).

## Principes élémentaires pour le côté client {#essentials-for-client-side}

* [Personnalisations côté client](client-customize.md)

## Principes élémentaires pour le côté serveur {#essentials-for-server-side}

* [API Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Points de terminaison Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personnalisations côté serveur](server-customize.md)

### Accès aux balises publiées (UGC) {#accessing-posted-tallies-ugc}

Le contenu généré par l’utilisateur doit être modéré à l’aide de l’une des méthodes standard de modération.\
Voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

À partir de AEM 6.1 Communities, utilisez un [magasin commun](working-with-srp.md) pour le contenu généré par l’utilisateur inclut l’accès programmatique au contenu généré par l’utilisateur, quelle que soit l’option de stockage choisie (comme ASRP, MSRP ou JSRP).

**L’emplacement et le format du contenu créé par l’utilisateur dans le référentiel peuvent être modifiés sans avertissement.**.

Voir :

* [Présentation du fournisseur de ressources de stockage](srp.md) - présentation et utilisation du référentiel
* [Principes de base de la SRP et du contenu généré par l’utilisateur](srp-and-ugc.md) - Méthodes d’utilitaire SRP et exemples
* [Accès au contenu généré par l’utilisateur avec SRP](accessing-ugc-with-srp.md) - Instructions de codage
* [Refactorisation de SocialUtils](socialutils.md) - mappage de méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles
