---
title: Les pièges du codage
seo-title: Code pitfalls
description: Pièges de codage courants à éviter lors du développement pour AEM
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 25%

---

# Les pièges du codage{#code-pitfalls}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Éviter les liaisons Sling dans le code Java {#avoid-sling-bindings-in-java-code}

Les liaisons Sling constituent un moyen inapproprié d’accéder à un service dans 90 % des cas. À la place, vous devez utiliser *@Reference* ou *@Inject* annotations.

## Éviter d’insérer Thread.interrupt dans le code Java {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* est dangereux, car il peut fermer des fichiers, y compris des fichiers Lucene et des fichiers de cache persistants, lorsqu’il est appelé au mauvais moment.

## Évitez de mélanger la synchronisation Java avec ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Cela peut entraîner une situation de concurrence dans laquelle le code finira par se bloquer.
