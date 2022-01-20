---
title: Les pièges du codage
seo-title: Code pitfalls
description: Pièges de codage communs à éviter lors du développement pour AEM
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 94%

---

# Les pièges du codage{#code-pitfalls}

## Éviter les liaisons Sling dans le code Java {#avoid-sling-bindings-in-java-code}

Les liaisons Sling constituent un moyen inapproprié d’accéder à un service dans 90 % des cas. À la place, il faut utiliser les annotations *@Reference* ou *@Inject*.

## Éviter Thread.interrupt dans le code Java {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* est dangereux car il peut fermer des fichiers, y compris des fichiers Lucene et des fichiers cache persistants, s’il est appelé au mauvais moment.

## Éviter de mélanger la synchronisation Java avec ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Cela peut aboutir à une condition de concurrence dans laquelle le code finit par être bloqué.
