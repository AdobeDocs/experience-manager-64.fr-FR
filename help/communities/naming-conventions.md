---
title: Conventions de dénomination
seo-title: Conventions de dénomination
description: Tirets dans le nom du package Java
seo-description: Tirets dans le nom du package Java
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
translation-type: tm+mt
source-git-commit: f78f83ef3b9373bcbee3e5179a9bbec4d9462255
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 4%

---


# Conventions de dénomination {#naming-conventions}

## Tirets dans le nom du package Java {#hyphens-in-java-package-name}

Lors de la création d&#39;un emplacement pour une classe Java, n&#39;oubliez pas que le nom du package doit correspondre à celui du dossier du référentiel avec tous les tirets du chemin d&#39;accès correctement échappés.

Bien que l&#39;utilisation de tirets dans les noms d&#39;éléments du référentiel soit une pratique recommandée dans le développement AEM, les tirets ne sont pas autorisés dans les noms de paquets Java.

La plate-forme CRX sous-jacente doit pouvoir distinguer un trait de soulignement réel &quot;_&quot; et un trait d’union &quot;-&quot;. Ainsi, dans le JCR, le trait d’union doit être remplacé par sa valeur unicode (u002d) et s’échapper par un trait de soulignement &quot;_&quot;.

Par exemple, si le chemin d’accès au référentiel est **/apps/my-example/component/info/Info.java**, le nom du package doit être `java package apps.my_002dexample.component.info;`

Vous remarquerez qu’un trait de soulignement doit de la même façon être échappé, de telle sorte que `_` devienne `_005f`.
