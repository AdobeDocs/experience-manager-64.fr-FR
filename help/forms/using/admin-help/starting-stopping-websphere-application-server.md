---
title: Démarrer et arrêter WebSphere Application Server
seo-title: Starting and stopping WebSphere Application Server
description: Plusieurs procédures nécessitent l’arrêt ou le démarrage de l’instance de WebSphere sur laquelle vous souhaitez déployer AEM produits forms. Ce document décrit le démarrage et l’arrêt de WebSphere Application Server.
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 8e3bb77f-b187-42c8-a90e-fe0fee50dc34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 40%

---

# Démarrer et arrêter WebSphere Application Server {#starting-and-stopping-websphere-application-server}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Plusieurs procédures nécessitent l’arrêt ou le démarrage de l’instance de WebSphere sur laquelle vous souhaitez déployer AEM produits forms. Si vous ne savez pas si le serveur d’applications a démarré, vous pouvez d’abord afficher l’état de WebSphere Application Server.

## Affichage de l’état de WebSphere Application Server {#view-the-status-of-websphere-application-server}

1. À partir d’une invite de commande, accédez au *[racine du serveur d’applications]* répertoire /bin.
1. Saisissez la commande suivante en remplaçant *nom_serveur* par le nom de WebSphere Application Server :

   * (Windows) `serverStatus.bat`*nom_serveur*
   * (Linux, UNIX) ./ `serverStatus.sh`*nom_serveur*

## Démarrez WebSphere Application Server {#start-websphere-application-server}

1. À partir d’une invite de commande, accédez au *[racine du serveur d’applications]* répertoire /bin.
1. Saisissez la commande suivante en remplaçant *nom_serveur* par le nom de WebSphere Application Server :

   * (Windows) `startServer.bat`*nom_serveur*
   * (Linux, UNIX) ./ `startServer.sh`*nom_serveur*

## Arrêt de WebSphere Application Server {#stop-websphere-application-server}

1. À partir d’une invite de commande, accédez au *[racine du serveur d’applications]* répertoire /bin.
1. Saisissez la commande suivante en remplaçant *nom_serveur* par le nom de WebSphere Application Server :

   * (Windows) `stopServer.bat`*nom_serveur*
   * (Linux, UNIX) ./ `stopServer.sh`*nom_serveur*
