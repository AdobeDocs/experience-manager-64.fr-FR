---
title: Fichiers journaux
seo-title: Log files
description: Les événements, comme les erreurs d’exécution ou de démarrage, sont enregistrés dans les fichiers journaux du serveur d’applications, que vous pouvez ouvrir à l’aide d’un éditeur de texte.
seo-description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 27%

---

# Fichiers journaux {#log-files}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les événements tels que les erreurs d’exécution ou de démarrage sont enregistrés dans les fichiers journaux du serveur d’applications. Si vous rencontrez des problèmes lors du déploiement sur le serveur d’applications, vous pouvez utiliser les fichiers journaux pour vous aider à résoudre le problème. Vous pouvez ouvrir les fichiers journaux à l’aide de n’importe quel éditeur de texte.

(JBoss) Les fichiers journaux suivants se trouvent dans le répertoire `*[appserver root]*/server/*[server]*/log` :

* boot.log
* server.log.*[aaaa-mm-jj]*
* server.log

(WebLogic) Les fichiers journaux de domaine se trouvent dans la variable *[appserverdomain]* et les fichiers journaux du serveur se trouvent dans le dossier *[appserverdomain]/servers/[nom du serveur d’applications]/logs *directory :

* access.log
* *[nom du serveur d’applications]*.log
* *[nom du serveur d’applications]*.out.*[nombre incrémentiel]*

(WebSphere) Les fichiers journaux suivants se trouvent dans la variable *[racine du serveur d’applications]*/profiles/default/logs/*[nom du serveur d’applications]* directory:

* SystemErr.log
* SystemOut.log
* StartServer.log
