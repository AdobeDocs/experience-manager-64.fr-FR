---
title: Résolution des incidents liés à AEM
seo-title: Troubleshooting AEM
description: Découvrez les problèmes de dépannage avec AEM.
seo-description: Learn about troubleshooting issues with AEM.
uuid: d68e9ead-8aa6-4108-9f1e-85d7cd7a370f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 1bc19f9a-fa3f-43e3-813e-23ab0b708d43
exl-id: 34b509d5-4e80-4229-b155-40004856e87e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 55%

---

# Résolution des incidents liés à AEM{#troubleshooting-aem}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La section suivante décrit certains problèmes que vous pouvez rencontrer lors de l’utilisation d’AEM, ainsi que des suggestions pour les résoudre.

>[!NOTE]
>
>Si vous résolvez les problèmes liés à la création dans AEM, reportez-vous à la section [Résolution des problèmes pour les auteurs.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Si vous rencontrez des problèmes, il est également intéressant de consulter la liste des [problèmes connus](/help/release-notes/known-issues.md) relatifs à votre instance (packs de version et de services).

## Scénarios de dépannage pour les administrateurs {#troubleshooting-scenarios-for-administrators}

Le tableau suivant présente un aperçu des problèmes que les administrateurs peuvent avoir à résoudre :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Rôle(s)</strong></td> 
   <td><strong>Problème </strong></td> 
  </tr> 
  <tr> 
   <td>Administrateur système</td> 
   <td><p>Lorsque vous double-cliquez sur le fichier Quickstart jar, rien ne se produit ou le fichier s’ouvre dans un autre programme (par exemple, le gestionnaire d’archives).</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrateur système</p> </td> 
   <td><p>Mon application qui s’exécute sur CRX génère des erreurs de mémoire insuffisante.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrateur système</p> </td> 
   <td><p>Après avoir double-cliqué sur Quickstart CM AEM, l’écran d’accueil d’AEM ne s’affiche pas dans le navigateur</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrateur système</p> <p>utilisateur administrateur</p> </td> 
   <td><p>Création d’une image mémoire des threads</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrateur système</p> <p>utilisateur administrateur</p> </td> 
   <td><p>Contrôle des sessions JCR non fermées</p> </td> 
  </tr> 
 </tbody> 
</table>

## Problèmes d’installation {#installation-issues}

Voir [Problèmes d’installation courants](/help/sites-deploying/troubleshooting.md#common-installation-issues) pour plus d’informations sur les scénarios de dépannage suivants :

* Double-cliquer sur le fichier Quickstart jar n’a aucun effet sur le fichier JAR avec un autre programme (tel que le gestionnaire d’archives).
* Les applications s’exécutant sur CRX renvoient des erreurs de mémoire insuffisante.
* Après avoir double-cliqué sur Quickstart AEM, l’écran d’accueil d’AEM ne s’affiche pas dans le navigateur.

## Méthodes d’analyse de dépannage {#methods-for-troubleshooting-analysis}

### Créer une image mémoire des threads {#making-a-thread-dump}

L’image mémoire des threads est une liste de toutes les unités d’exécution Java actuellement actives. Si AEM ne répond pas correctement, le thread dump peut vous aider à identifier les blocages ou d’autres problèmes.

### Utilisation de Sling Thread Dumper {#using-sling-thread-dumper}

1. Ouvrez la **console web AEM**, par exemple, à l’adresse `http://localhost:4502/system/console/`.

1. Sélectionnez les **threads** dans l’onglet **Statut**.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Utilisation de jstack (ligne de commande) {#using-jstack-command-line}

1. Recherchez le PID (ID de processus) de l’instance Java AEM.

   Vous pouvez, par exemple, utiliser `ps -ef` ou `jps`.

1. Exécutez :

   `jstack <pid>`

1. L’image mémoire des threads s’affiche.

>[!NOTE]
>
>Vous pouvez ajouter les images mémoire des threads à un fichier journal en utilisant la redirection de sortie `>>` :
>
>`jstack <pid> >> /path/to/logfile.log`

Pour plus d’informations, consultez la section [Comment utiliser les images mémoire des threads d’une machine virtuelle Java (JVM)](https://helpx.adobe.com/cq/kb/TakeThreadDump.html).

### Contrôle des sessions JCR non fermées {#checking-for-unclosed-jcr-sessions}

Lorsque la fonctionnalité est développée pour AEM WCM, il est possible d’ouvrir des sessions JCR (cela s’apparente à l’ouverture d’une connexion de base de données). Si les sessions ouvertes ne sont jamais fermées, votre système peut présenter les symptômes suivants :

* Le système devient plus lent.
* Vous constatez qu’il y a de nombreuses entrées CacheManager: resizeAll dans le fichier journal. Le nombre (size=&lt;x>) ci-dessous affiche le nombre de caches. Chaque session ouvre plusieurs caches.
* Parfois, la mémoire du système est saturée (après quelques heures, jours ou semaines, selon la gravité).

Pour analyser les sessions non fermées et déterminer le code qui ne ferme pas une session, reportez-vous à l’article de la base de connaissances [Analyse des sessions non fermées](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html).

### Utilisation de la console web Adobe Experience Manager {#using-the-adobe-experience-manager-web-console}

L’état des lots OSGi peut également donner une indication précoce des problèmes possibles.

1. Ouvrez la **console web AEM**, par exemple, à l’adresse `http://localhost:4502/system/console/`.

1. Sélectionnez **Lots** dans l’onglet **OSGI**.

1. Vérifier :

   * le statut des lots. Si le statut est Inactif ou Insatisfait, essayez d’arrêter et de redémarrer le lot. Si le problème persiste, vous devrez peut-être approfondir l’enquête en utilisant d’autres méthodes.
   * Si l’un des lots possède des dépendances manquantes. Ces détails sont visibles en cliquant sur le nom du lot individuel, qui est un lien (l’exemple suivant n’a aucun problème) :

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
