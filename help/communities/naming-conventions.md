---
title: Conventions de dénomination
seo-title: Conventions de dénomination
description: Tirets dans le nom de module Java
seo-description: Tirets dans le nom de module Java
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 4%

---

# Conventions de dénomination {#naming-conventions}

## Tirets dans le nom du module Java {#hyphens-in-java-package-name}

Lors de la création d’un emplacement pour une classe Java, sachez que le nom du module doit correspondre à celui du dossier du référentiel avec tous les tirets dans le chemin d’accès correctement placés dans une séquence d’échappement.

Bien que l’utilisation de tirets dans les noms des éléments du référentiel soit une pratique recommandée dans le développement d’AEM, les tirets ne sont pas autorisés dans les noms de modules Java.

La plateforme CRX sous-jacente doit pouvoir distinguer un trait de soulignement réel &#39;_&#39; d’un trait d’union &#39;-&#39;. Ainsi, dans JCR, le trait d’union doit être remplacé par sa valeur unicode (u002d) et échappé par un trait de soulignement &#39;_&#39;.

Par exemple, si le chemin du référentiel est **/apps/my-example/component/info/Info.java**, le nom du module doit être `java package apps.my_002dexample.component.info;`

Notez qu’un trait de soulignement doit être placé dans une séquence d’échappement de la même manière, de sorte que `_` devienne `_005f`.
