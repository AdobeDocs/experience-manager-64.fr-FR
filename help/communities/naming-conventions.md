---
title: Conventions de nommage
seo-title: Naming Conventions
description: Tirets dans le nom de module Java
seo-description: Hyphens in Java Package Name
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 7%

---

# Conventions de nommage {#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Tirets dans le nom de module Java {#hyphens-in-java-package-name}

Lors de la création d’un emplacement pour une classe Java, sachez que le nom du module doit correspondre à celui du dossier du référentiel avec tous les tirets dans le chemin d’accès correctement placés dans une séquence d’échappement.

Bien que l’utilisation de tirets dans les noms des éléments du référentiel soit une pratique recommandée dans le développement d’AEM, les tirets ne sont pas autorisés dans les noms de modules Java.

La plateforme CRX sous-jacente doit pouvoir distinguer un trait de soulignement réel &quot;_&#39; et un trait d’union &#39;-&#39;. Ainsi, dans JCR, le trait d’union doit être remplacé par sa valeur unicode (u002d) et échappé par un trait de soulignement &quot;_&#39;.

Par exemple, si le chemin d’accès au référentiel est **/apps/my-example/component/info/Info.java**, le nom du module doit être `java package apps.my_002dexample.component.info;`

Notez qu’un trait de soulignement doit être placé dans une séquence d’échappement de la même manière, de sorte que `_` devient `_005f`.
