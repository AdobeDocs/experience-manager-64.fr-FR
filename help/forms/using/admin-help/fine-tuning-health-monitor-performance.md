---
title: Optimiser les performances de Health Monitor
seo-title: Fine-tuning Health Monitor performance
description: Découvrez comment optimiser les performances de Health Monitor
seo-description: Learn how to fine-tune Health Monitor performance
uuid: 770b10cb-065f-41b5-9594-a291e4311151
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b8f8bddc-0d38-4d5e-b33f-978f04bc16c6
exl-id: b2814b0d-e843-4aba-8c74-a3be0a96f726
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 20%

---

# Optimiser les performances de Health Monitor{#fine-tuning-health-monitor-performance}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La collecte des statistiques système qui renseignent Health Monitor a un impact sur les performances de votre environnement d’AEM forms. Vous pouvez contrôler cet impact en définissant les options Java répertoriées ci-dessous dans votre serveur d’applications.

<table> 
 <thead> 
  <tr> 
   <th><p>Propriété</p></th> 
   <th><p>Objectif</p></th> 
   <th><p>Valeur par défaut</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>adobe.healthmonitor.enabled</p></td> 
   <td><p>Activer ou désactiver le thread Health Monitor</p></td> 
   <td><p>true</p></td> 
  </tr> 
  <tr> 
   <td><p>adobe.cache.statistics-enabled</p></td> 
   <td><p>Activation ou désactivation de la mise en cache de Gemfire</p></td> 
   <td><p>true</p></td> 
  </tr> 
  <tr> 
   <td><p>adobe.healthmonitor.refresh-interval</p></td> 
   <td><p>Intervalle en millisecondes après lequel le thread Health Monitor collecte les statistiques</p></td> 
   <td><p>10 minutes (600 000 millisecondes)</p></td> 
  </tr> 
  <tr> 
   <td><p>adobe.cache.multicast-port</p></td> 
   <td><p>Port multidiffusion utilisé pour communiquer avec d’autres membres du système distribué. S’il est défini sur zéro, la multidiffusion est désactivée pour la découverte et la distribution de membres. </p><p>Remarque : Sélectionnez différentes adresses et ports de multidiffusion pour différents systèmes distribués. N’utilisez pas uniquement des adresses différentes.</p></td> 
   <td><p>Pas de valeur par défaut. Les valeurs valides sont comprises entre 0 et 65 535.</p></td> 
  </tr> 
  <tr> 
   <td><p>statistics-sample-rate</p></td> 
   <td><p>Taux en millisecondes auquel les statistiques sont échantillonnées. Les statistiques du système d’exploitation ne sont mises à jour que lorsqu’un échantillon est prélevé.</p></td> 
   <td><p>600000</p></td> 
  </tr> 
  <tr> 
   <td><p>adobe.workmanager.healthmonitor.enabled</p></td> 
   <td><p>Cette propriété active ou désactive la collecte de statistiques Work Manager, telles que le nombre de tâches ou d’éléments de travail.</p></td> 
   <td><p>true</p></td> 
  </tr> 
 </tbody> 
</table>

## Ajout d’options Java à JBoss {#add-java-options-to-jboss}

1. Arrêtez le serveur d’applications JBoss.
1. Ouvrez la *[racine du serveur d’applications]*/bin/run.bat (Windows) ou run.sh (Linux ou UNIX) dans un éditeur et ajoutez toutes les options Java requises.
1. Redémarrez le serveur.

## Ajout d’options Java à WebLogic {#add-java-options-to-weblogic}

1. Démarrez WebLogic Administration Console en saisissant https://[nom d’hôte]:[port]/console dans la ligne d’adresse d’un navigateur web.
1. Saisissez le nom d’utilisateur et le mot de passe que vous avez créés pour le domaine WebLogic Server, puis cliquez sur Journal sous Change Center, puis sur Lock &amp; Edit.
1. Sous Domain Structure, cliquez sur Environment > Servers et, dans le volet de droite, cliquez sur le nom du serveur géré.
1. Dans l’écran suivant, cliquez sur les onglets Configuration > Server Start.
1. Dans la zone Arguments , ajoutez les arguments dont vous avez besoin à la fin du contenu actuel. Par exemple, ajouter ‑ `Dadobe.healthmonitor.enabled=false` permet de désactiver Health Monitor.
1. Cliquez sur Save, puis sur Activate Changes.
1. Redémarrez le serveur géré WebLogic.

## Ajout d’options Java à WebSphere {#add-java-options-to-websphere}

1. Dans l’arborescence de navigation de la console d’administration WebSphere, procédez comme suit pour votre serveur d’applications :

   (WebSphere 6.x) Cliquez sur Servers > Application servers

   (WebSphere 7.x) Cliquez sur Servers > Server Types > WebSphere application servers .

1. Dans le volet de droite, cliquez sur le nom du serveur.
1. Sous Server Infrastructure, cliquez sur Java and forms workflow > Process Definition.
1. Sous Additional Properties, cliquez sur Java Virtual Machine.
1. Dans la zone Generic JVM arguments , saisissez les arguments dont vous avez besoin.
1. Cliquez sur OK ou sur Apply, puis sur Save directly to master configuration.
