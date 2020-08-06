---
title: Fichiers journaux
seo-title: Fichiers journaux
description: Les événements, comme les erreurs d’exécution ou de démarrage, sont enregistrés dans les fichiers journaux du serveur d’applications, que vous pouvez ouvrir à l’aide d’un éditeur de texte.
seo-description: Les événements, comme les erreurs d’exécution ou de démarrage, sont enregistrés dans les fichiers journaux du serveur d’applications, que vous pouvez ouvrir à l’aide d’un éditeur de texte.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 64%

---


# Fichiers journaux {#log-files}

Les événements, comme les erreurs d’exécution ou de démarrage, sont enregistrés dans les fichiers journaux du serveur d’applications. Ces fichiers peuvent vous aider à diagnostiquer les éventuels problèmes rencontrés lors du déploiement sur le serveur d’applications. Vous pouvez les ouvrir dans un éditeur de texte.

(JBoss) Les fichiers journaux suivants se trouvent dans le `*[appserver root]*/server/*[server]*/log` répertoire :

* boot.log
* server.log.*[aaaa-mm-jj]*
* server.log

(WebLogic) Domain log files are located in the *[appserverdomain]* directory, and server log files are located in the *[appserverdomain]/servers/[appserver name]/logs *directory:

* access.log
* *[appserver name]*.log
* *[appserver name]*.out.*[incremental number]*

(WebSphere) The following log files are located in the *[appserver root]*/profiles/default/logs/*[appserver name]* directory:

* SystemErr.log
* SystemOut.log
* StartServer.log

