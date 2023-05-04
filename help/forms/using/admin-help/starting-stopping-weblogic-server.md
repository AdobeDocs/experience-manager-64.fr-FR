---
title: Démarrage et arrêt de WebLogic Server
seo-title: Starting and stopping WebLogic Server
description: Plusieurs procédures nécessitent de démarrer ou d’arrêter l’instance de WebLogic Server sur laquelle vous souhaitez déployer les modules d’AEM forms. Ce document décrit le démarrage et l’arrêt de WebLogic Server.
seo-description: Several procedures require you to start or stop the instance of WebLogic Server where you want to deploy AEM forms modules. This document describes how to start and stop the WebLogic Server.
uuid: 957787fe-4cea-4ecd-b49a-c33023c5c309
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c908d064-6596-473a-b218-22a2496c83f7
exl-id: c7a74e20-4cfb-4674-af41-f3333c9b5397
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 31%

---

# Démarrage et arrêt de WebLogic Server {#starting-and-stopping-weblogic-server}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Plusieurs procédures nécessitent de démarrer ou d’arrêter l’instance de WebLogic Server sur laquelle vous souhaitez déployer les modules d’AEM forms. Vérifiez que WebLogic Server est arrêté ou en cours d’exécution, selon la tâche que vous effectuez.

<table> 
 <thead> 
  <tr> 
   <th><p>Activité</p></th> 
   <th><p>État WebLogic requis</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Création d’un domaine WebLogic</p></td> 
   <td><p>Arrêté</p></td> 
  </tr> 
  <tr> 
   <td><p>Création d’un serveur géré WebLogic</p></td> 
   <td><p>Exécution en cours</p></td> 
  </tr> 
  <tr> 
   <td><p>Augmentation du nombre de threads du serveur</p></td> 
   <td><p>Exécution en cours</p></td> 
  </tr> 
  <tr> 
   <td><p>Déploiement des produits d’AEM forms</p></td> 
   <td><p>Exécution en cours</p></td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Si vous exécutez WebLogic Server sous Red Hat® Enterprise Linux Advanced Server 4.0, définissez la variable d’environnement `LD_ASSUME_KERNEL` sur 2.4.19 à l’aide de la commande `export LD_ASSUME_KERNEL=2.4.19`. Exécutez ensuite WebLogic Server à partir du shell dans lequel vous définissez cette variable d’environnement.

## Démarrage de WebLogic Server {#start-weblogic-server}

1. À partir d’une invite de commande, accédez à *[racine du serveur d’applications]*/user_projects/domains/*[domaine du serveur d’applications]*.
1. Saisissez la commande suivante :

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

## Arrêt de WebLogic Server {#stop-weblogic-server}

1. Démarrez la console dʼadministration de WebLogic Server en saisissant `https://[host name]:7001/console` dans la ligne d’adresse d’un navigateur web.
1. Connectez-vous en saisissant le nom d’utilisateur et le mot de passe utilisés lors de la création de cette configuration WebLogic, puis cliquez sur Log In.
1. Sous Centre des modifications, cliquez sur Verrouiller et modifier.
1. Sous Domain Structure, cliquez sur Environment > Servers.
1. Cliquez sur AdminServer puis, dans le volet Paramètres d’AdminServer, cliquez sur l’onglet Contrôle .
1. Assurez-vous qu’AdminServer est sélectionné dans le tableau Server Status (Statut du serveur) et cliquez sur Shutdown.
1. Sélectionnez Lorsque le travail se termine pour arrêter normalement le serveur ou Forcer l’arrêt maintenant pour arrêter immédiatement le serveur sans exécuter les tâches en cours.
1. Dans le volet Server Life Cycle Assistant, cliquez sur Yes pour terminer l’arrêt.

WebLogic Server Administration Console n’est plus disponible et l’invite de commande à partir de laquelle vous avez exécuté la commande start est disponible.

## Démarrage de WebLogic Administration Console {#start-weblogic-administration-console}

1. Si WebLogic Admin Server n’est pas en cours d’exécution, ouvrez une invite de commande, accédez au répertoire *[racine du serveur d’applications]\user_projects\domains\[nom de domaine]* et saisissez la commande suivante :

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

1. Accédez à WebLogic Server Administration Console en saisissant `https://*[host name]:`[Port] `/console` dans la ligne d’URL d’un navigateur web, où *[Port]* est le port d’écoute non sécurisé. Par défaut, cette valeur de port est 7001.
1. Dans l’écran de connexion, saisissez le nom d’utilisateur et le mot de passe de l’administrateur, puis cliquez sur Log In.

## Démarrage de Node Manager {#start-node-manager}

1. Vérifiez que WebLogic Server est en cours d’exécution.
1. A partir d’une nouvelle invite de commande, accédez à *[racine du serveur d’applications]*/server/bin.
1. Saisissez la commande suivante :

   * (Windows) `startNodeManager.cmd`
   * (Linux, UNIX) `./startNodeManager.sh`

## Arrêter Node Manager {#stop-node-manager}

Après avoir arrêté WebLogic Server, vous pouvez fermer l’invite de commande à partir de laquelle vous avez appelé Node Manager.

## Démarrage d’un serveur géré WebLogic {#start-a-weblogic-managed-server}

>[!NOTE]
>
>Cette tâche ne peut être effectuée qu’après la création d’un domaine WebLogic et d’un serveur géré.

1. Vérifiez que WebLogic Server et Node Manager sont en cours d’exécution.
1. Ouvrez la console d’administration de WebLogic Server en saisissant `https://`*[nom d’hôte]:[port ]*`/console` dans la ligne d’URL d’un navigateur web.
1. Sous Domain Structure, cliquez sur Environment > Servers.
1. Dans le volet de droite, cliquez sur l’onglet Contrôle .
1. Sélectionnez le serveur géré que vous souhaitez démarrer.
1. Cliquez sur le bouton Démarrer sous le serveur géré que vous souhaitez démarrer.

## Arrêt d’un serveur géré WebLogic {#stop-a-weblogic-managed-server}

1. Ouvrez la console d’administration de WebLogic Server en saisissant `https://`*[nom d’hôte]:[port ]*`/console` dans la ligne d’URL d’un navigateur web.
1. Sous Domain Structure, cliquez sur Environment > Servers.
1. Dans le volet de droite, cliquez sur l’onglet Contrôle .
1. Sélectionnez le serveur géré que vous souhaitez arrêter.
1. Cliquez sur le bouton Arrêter sous le serveur géré que vous souhaitez arrêter.
1. Sélectionnez Lorsque le travail se termine pour arrêter normalement le serveur ou Forcer l’arrêt maintenant pour arrêter immédiatement le serveur sans exécuter les tâches en cours.
1. Dans le volet Server Life Cycle Assistant, cliquez sur Yes pour terminer l’arrêt.
