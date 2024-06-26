---
title: Hébergement de deux instances d’espace de travail AEM Forms sur un serveur
seo-title: Hosting two AEM Forms workspace instances on one server
description: Comment les administrateurs LC peuvent-ils personnaliser HTML WS pour héberger deux instances sur un seul serveur accessible via différentes URL ?
seo-description: How LC administrators can customize HTML WS to host two instances on a single server accessible via different URLs.
uuid: 0584f512-6b92-4418-b71c-93605cfa1927
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 1254a7c2-2c67-4661-803e-afd53e817916
exl-id: ef2ad8e1-5007-4587-97ca-cf21070be9a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 47%

---

# Hébergement de deux instances d’espace de travail AEM Forms sur un serveur {#hosting-two-aem-forms-workspace-instances-on-one-server}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’installation et les paramètres par défaut d’AEM Forms ne permettent qu’un seul espace de travail AEM Forms soit disponible sur le serveur. Cependant, vous devrez peut-être héberger deux instances différentes de l’espace de travail AEM Forms sur un seul serveur AEM Forms. Les deux instances sont accessibles par des URL différentes.

Les administrateurs AEM Forms personnalisent l’espace de travail pour créer deux URL différentes et rendre deux espaces de travail disponibles sur le même serveur. Dans cet article sur la personnalisation, nous supposons que les deux espaces de travail sont accessibles aux adresses `https://[server]:[port]/lc/ws` et `https://[server]:[port]:/lc/ws2`.

Pour configurer l’espace de travail AEM Forms, procédez comme suit.

1. Installez le package de développement de l’espace de travail AEM Forms sur votre serveur. Voir [package de développement](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p), pour obtenir des instructions sur la création de l’application.
1. Connectez-vous à CRXDE Lite en tant qu’administrateur en accédant à `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Copiez le noeud ws dans /content et collez-le dans /content. Renommez le noeud en ws2. Cliquez sur **[!UICONTROL Enregistrer tout]**. Dans les propriétés de ce nœud, attribuez à `sling:resourceType` la valeur ws2. Cliquez sur **[!UICONTROL Enregistrer tout]**. 

1. Copiez le dossier ws depuis /libs et collez-le dans /apps. Renommez le dossier ws2. Cliquez sur **[!UICONTROL Enregistrer tout]**.
1. Dans `GET.jsp`, sur `/apps/ws2`, effectuez les modifications de code suivantes. Remplacez le code :

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" /><html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" />
   ```

   par le code suivant :

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/apps/ws2/index.html'" />
   ```

1. Dans `registry.js`, sur `/apps/ws2/js`, remplacez le chemin des modèles afin de faire référence aux modèles sur `/apps/ws2/js/runtime/templates`. Remplacez le code :

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/libs/ws/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

   par le code suivant :

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/apps/ws2/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

1. Dans `userinfo.js`, sur `/apps/ws2/js/runtime/models` et `/apps/ws2/js/runtime/views`, remplacez la chaîne `/lc/content/ws` par `lc/content/ws2`.

1. Dans `/apps/ws2/js/runtime/services/service.js`, modifiez le chemin d’accès dans la fonction `getLocalizationData` afin qu’il pointe sur `/lc/apps/ws2/Locale.html`.

1. Pour faire référence à l’élément `pdf.html` du nouvel espace de travail, modifiez le chemin d’accès de `pdf.html` dans `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. Pour faire référence à l’élément `pdf.html` du nouvel espace de travail, modifiez les chemins d’accès de `pdf.html` et `WsNextAdapter.swf` dans `startprocess.html`, `taskdetails.html` et `processinstancehistory.html` sur `/apps/ws2/js/runtime/templates`.

1. Copiez le dossier `/etc/map/ws` et collez-le sur `/etc/map`. Renommez le nouveau dossier en ws2. Cliquez sur Enregistrer tout.

1. Dans les propriétés de `ws2`, remplacez la valeur de `sling:redirect` par `content/ws2`.

1. Remplacez la valeur de `sling:match` par `^[^/\||]/[^/\||]/ws2$`.
