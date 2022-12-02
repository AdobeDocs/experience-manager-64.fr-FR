---
title: Conventions de nommage pour le test des ressources
seo-title: Naming conventions for assets
description: Les nœuds dans le référentiel sont soumis aux conventions de dénomination de Java Content Repository. Toutefois, Adobe Experience Manager impose d’autres conventions pour le nom des nœuds de ressource.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 100%

---

# Conventions de nommage pour le test des ressources{#naming-conventions-for-assets-testing}

Les nœuds dans le référentiel sont soumis aux conventions de dénomination de [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Toutefois, Adobe Experience Manager impose d’autres conventions pour le nom des nœuds de ressource.

## Interface utilisateur classique {#classic-ui}

L’IU classique applique des restrictions plus strictes :

* Valide le nom de ressource dans le cas d’un nom de nœud explicite lorsque :

   * un titre de ressource est fourni pour la conversion dans le nom de nœud
   * un nom de nœud explicite est fourni

* Caractères valides (seuls ces caractères sont effectivement valides lorsqu’une ressource est créée dans l’IU classique) :

   * « a » à « z »
   * « A » à « Z »
   * « 0 » à « 9 »
   * _ (trait de soulignement)
   * `-` (tiret/moins)
