---
title: Tableau de bord des opérations
seo-title: Operations Dashboard
description: Découvrez comment utiliser le tableau de bord des opérations.
feature: Operations
seo-description: Learn how to use the Operations Dashboard.
uuid: f1a6dcdc-307b-45f4-ade5-cedc58f0c7cf
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 7599fa42-3a47-49c9-8a7f-e0b6be302ff0
exl-id: a0cb6a30-fdd4-4806-a5fa-45c98ad15d11
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '6227'
ht-degree: 58%

---

# Tableau de bord des opérations {#operations-dashboard}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Dans AEM 6, le tableau de bord des opérations permet aux opérateurs système de surveiller d’un simple coup d’œil l’intégrité du système AEM. Il contient également des informations de diagnostic générées automatiquement concernant des aspects pertinents d’AEM et permet de configurer et d’exécuter une automatisation de maintenance autonome afin de réduire de façon significative les coûts de fonctionnement du projet et les dossiers de support. Le tableau de bord des opérations peut être étendu en y intégrant des contrôles de l’intégrité et des tâches de maintenance personnalisés. De plus, les données du tableau de bord des opérations sont accessibles à partir d’outils de surveillance externes via JMX.

**Le tableau de bord des opérations :**

* est un état système en un clic pour aider les services d’opérations à gagner en efficacité ;
* fournit une vue d’ensemble des contrôles de l’intégrité du système à un emplacement centralisé unique ;
* Réduit le temps de recherche, d’analyse et de résolution des problèmes
* Automatisation de la maintenance autonome qui permet de réduire considérablement les coûts d’exploitation du projet

Il est accessible en sélectionnant **Outils** – **Opérations** dans l’écran d’accueil d’AEM.

>[!NOTE]
>
>Pour accéder au tableau de bord des opérations, l’utilisateur connecté doit faire partie du groupe « Opérateurs ». Pour plus d’informations, consultez la documentation relative à l’[Administration des utilisateurs, des groupes et des droits d’accès](/help/sites-administering/user-group-ac-admin.md).

## Rapports d’intégrité {#health-reports}

Le système de rapports d’intégrité fournit des informations sur l’intégrité d’une instance AEM par le biais de contrôles d’intégrité Sling. Cela peut être effectué à l’aide de demandes OSGi, JMX, HTTP (via JSON) ou par le biais de l’interface utilisateur tactile. Il propose des mesures et des seuils pour certains compteurs configurables et, dans certains cas, fournira des informations sur la façon de résoudre le problème.

Il comporte différentes fonctionnalités, décrites ci-dessous.

## Contrôles de l&#39;intégrité {#health-checks}

Les **rapports d’intégrité** sont un système de cartes indiquant une intégrité satisfaisante ou non en ce qui concerne une zone spécifique du produit. Ces cartes sont des visualisations des contrôles d’intégrité Sling, qui agrègent les données de JMX et d’autres sources, et présentent de nouveau les informations traitées sous forme de MBeans. Ces MBeans peuvent également être inspectés dans la variable [Console web JMX](/help/sites-administering/jmx-console.md), sous **org.apache.sling.healthcheck** domaine.

Les rapports d’intégrité sont accessibles en sélectionnant le menu **Outils** – **Opérations** – **Rapports d’intégrité** dans l’écran d’accueil d’AEM ou directement par le biais de l’adresse URL suivante :

`https://<serveraddress>:port/libs/granite/operations/content/healthreports/healthreportlist.html`

![chlimage_1-414](assets/chlimage_1-414.png)

Le système de cartes comporte trois statuts possibles : **OK**, **AVERTISSEMENT** et **CRITIQUE**. Les statuts sont le résultat des règles et des seuils, qui peuvent être configurés en passant le curseur de la souris sur la carte, puis en cliquant sur l’icône d’engrenage de la barre d’actions :

![chlimage_1-415](assets/chlimage_1-415.png)

### Types de contrôle de l’intégrité {#health-check-types}

Il existe deux types de contrôles de l’intégrité dans AEM 6 :

1. Contrôles de l’intégrité individuels
1. Contrôles de l’intégrité composites

Un **contrôle de l’intégrité individuel** est un contrôle de l’intégrité unique, qui correspond à une carte d’état. Des contrôles de l’intégrité individuels peuvent être configurés avec des règles ou des seuils et peuvent fournir un ou plusieurs conseils et liens pour résoudre des problèmes d’intégrité identifiés. Prenons le contrôle « Erreurs de journal » comme exemple : s’il existe des entrées ERREUR dans les journaux des instances, elles seront répertoriées dans la page Détails du contrôle de l’intégrité. En haut de la page, vous trouverez un lien vers l’analyseur &quot;Message du journal&quot; dans la section Outils de diagnostic, qui vous permettra d’analyser plus en détail ces erreurs et de reconfigurer les enregistreurs.

A **Contrôle d’intégrité composite** est une vérification qui agrège les informations de plusieurs contrôles individuels.

Les contrôles de l’intégrité composites sont configurés à l’aide de **balises de filtrage**. En substance, tous les contrôles individuels possédant la même balise de filtrage sont regroupés sous le contrôle de l’intégrité composite. le statut d’un contrôle de l’intégrité composite est « OK » seulement si le statut de tous les contrôles individuels est également « OK ».

### Procédure de création de contrôles de l’intégrité {#how-to-create-health-checks}

Dans le tableau de bord des opérations, vous pouvez visualiser le résultat des contrôles de l’intégrité individuels et composites.

### Création d’un contrôle de l’intégrité individuel {#creating-an-individual-health-check}

La création d’un contrôle de l’intégrité individuel comprend deux étapes : implémentation d’un contrôle de l’intégrité Sling et ajout d’une entrée pour le contrôle de l’intégrité dans les noeuds de configuration du tableau de bord.

1. Pour créer un contrôle de l’intégrité Sling, vous devez créer un composant OSGi mettant en œuvre l’interface Sling HealthCheck. Vous ajoutez ce composant dans un lot. Les propriétés du composant identifient entièrement le contrôle de l’intégrité. Une fois le composant installé, un MBean JMX est automatiquement créé pour le contrôle de l’intégrité. Voir [Documentation du contrôle de l’intégrité Sling](https://sling.apache.org/documentation/bundles/sling-health-check-tool.html) pour plus d’informations.

    Exemple de composant de contrôle de l’intégrité Sling, écrit avec des annotations de composant de service OSGi :

   ```java
   @Component(service = HealthCheck.class,         
   property = {             
       HealthCheck.NAME + "=Example Check",             
       HealthCheck.TAGS + "=example",             
       HealthCheck.TAGS + "=test",             
       HealthCheck.MBEAN_NAME + "=exampleHealthCheckMBean"         
   })
    public class ExampleHealthCheck implements HealthCheck { 
       @Override     
       public Result execute() {     
           // health check code     
       }
    }
   ```

   >[!NOTE]
   >
   >La propriété `MBEAN_NAME` définit le nom du MBean généré pour ce contrôle de l’intégrité.

1. Après avoir créé un contrôle de l’intégrité, un nouveau nœud de configuration doit être créé afin de le mettre à disposition dans l’interface du tableau de bord des opérations. Pour cette étape, il est nécessaire de connaître le nom du MBean JMX du contrôle de l’intégrité (la propriété `MBEAN_NAME`). Pour créer une configuration pour le contrôle de l’intégrité, ouvrez CRXDE et ajoutez un nouveau nœud (de type **nt:unstructured**) sous le chemin d’accès suivant : `/apps/settings/granite/operations/hc`.

   Les propriétés ci-dessous doivent être définies sur le nouveau nœud :

   * **Nom :** `sling:resourceType`

      * **Type :** `String`
      * **Valeur :** `granite/operations/components/mbean`
   * **Nom :** `resource`

      * **Type :** `String`
      * **Valeur :** `/system/sling/monitoring/mbeans/org/apache/sling/healthcheck/HealthCheck/exampleHealthCheck`

   >[!NOTE]
   >
   >Le chemin d’accès à la ressource ci-dessus est créé comme suit : si le nom du MBean du contrôle de l’intégrité est « test », ajoutez « test » à la fin du chemin d’accès `/system/sling/monitoring/mbeans/org/apache/sling/healthcheck/HealthCheck`.
   >
   >Le chemin d’accès final est donc :
   >
   >`/system/sling/monitoring/mbeans/org/apache/sling/healthcheck/HealthCheck/test`

   >[!NOTE]
   >
   >Assurez-vous que les propriétés ci-dessous du chemin d’accès `/apps/settings/granite/operations/hc` sont définies sur true :
   >
   >
   >`sling:configCollectionInherit`
   >
   >`sling:configPropertyInherit`
   >
   >
   >Cela indique au gestionnaire de configuration de fusionner les nouvelles configurations avec les configurations existantes de `/libs`.

### Création d’un contrôle de l’intégrité composite {#creating-a-composite-health-check}

Un contrôle de l’intégrité composite vise à agréger différents contrôles de l’intégrité partageant un ensemble de fonctionnalités communes. Par exemple, un contrôle de l’intégrité composite de sécurité regroupe tous les contrôles de l’intégrité individuels liés à la sécurité. Pour créer un contrôle composite, la première étape consiste à ajouter une nouvelle configuration OSGi. Pour qu’il s’affiche dans le tableau de bord des opérations, un nouveau noeud de configuration doit être ajouté, de la même manière que pour une vérification simple.

1. Accédez au gestionnaire de configuration web dans la console OSGi. Vous pouvez effectuer cette opération à en accédant à `https://serveraddress:port/system/console/configMgr`.

1. Recherchez l’entrée **Apache Sling Composite Health Check**. Une fois que vous l’avez trouvé, deux configurations sont déjà disponibles : une pour les contrôles système et une autre pour les contrôles de sécurité.
1. Créez une configuration en cliquant sur le bouton « + » dans la partie droite de la configuration. Une nouvelle fenêtre s’affiche, comme illustré ci-dessous :

   ![chlimage_1-63](assets/chlimage_1-63.jpeg)

1. Créez une configuration et enregistrez-la. Un MBean sera créé avec la nouvelle configuration.

   L’objectif de chaque propriété de configuration est le suivant :

   * **Nom (hc.name) :** nom du contrôle de l’intégrité composite. Un nom significatif est recommandé.
   * **Balises (hc.tags) :** balises de ce contrôle de l’intégrité. Si ce contrôle de l’intégrité composite est destiné à faire partie d’un autre contrôle de l’intégrité composite (dans une hiérarchie de contrôles de l’intégrité, par exemple), ajoutez les balises auxquelles ce contrôle composite est associé.
   * **Nom du MBean (hc.mbean.name) :** Nom du MBean Mbean qui sera donné au MBean JMX de ce contrôle de l’intégrité composite.
   * **Balises de filtrage (filter.tags) :** il s’agit d’une propriété spécifique aux contrôles de l’intégrité composites. Ce sont les balises que le contrôle composite doit agréger. Le contrôle de l’intégrité composite agrège, sous son groupe, tous les contrôles de l’intégrité possédant une balise correspondant aux balises de filtrage de ce contrôle composite. Par exemple, un contrôle de l’intégrité composite possédant les balises de filtrage **test** et **check** agrège tous les contrôles de l’intégrité individuels et composites possédant la balise **test** ou **check** dans leur propriété de balise (`hc.tags`).

   >[!NOTE]
   >
   >Un nouveau MBean JMX est créé pour chaque nouvelle configuration du contrôle de l’intégrité composite Apache Sling.**

1. Enfin, l’entrée du contrôle de l’intégrité composite qui vient d’être créé doit être ajoutée aux nœuds de configuration du tableau de bord des opérations. La procédure est identique à celle des contrôles de l’intégrité individuels : un nœud de type **nt:unstructured** doit être créé sous `/apps/settings/granite/operations/hc`. La propriété de ressource du noeud sera définie par la valeur de **hc.mean.name** dans la configuration OSGI.

   Si, par exemple, vous avez créé une configuration et défini la variable **hc.mbean.name** valeur à **diskusage**, les noeuds de configuration se présentent comme suit :

   * **Nom :** `Composite Health Check`

      * **Type :** `nt:unstructured`

   Avec les propriétés suivantes :

   * **Nom :** `sling:resourceType`

      * **Type :** `String`
      * **Valeur :** `granite/operations/components/mbean`
   * **Nom :** `resource`

      * **Type :** `String`
      * **Valeur :** `/system/sling/monitoring/mbeans/org/apache/sling/healthcheck/HealthCheck/diskusage`

   >[!NOTE]
   >
   >Si vous créez des contrôles de l’intégrité individuels, qui font partie logiquement d’un contrôle composite déjà présent dans le tableau de bord par défaut, ils sont enregistrés et regroupés automatiquement sous le contrôle composite correspondant. Pour cette raison, il n’est pas nécessaire de créer un noeud de configuration pour ces contrôles.
   >
   >Par exemple, si vous créez un contrôle de l’intégrité individuel de sécurité, il suffit d’affecter la balise « **security** », et elle s’installe et s’affiche automatiquement sous le contrôle composite de sécurité dans le tableau de bord des opérations.

### Contrôles de l’intégrité fournis avec AEM {#health-checks-provided-with-aem}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nom du contrôle de l’intégrité</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>Performances des requêtes</td> 
   <td><p>Ce contrôle de l’intégrité a été simplifié <strong>dans AEM 6.4</strong> et contrôle maintenant le MBean <code>Oak QueryStats</code> restructuré dernièrement, plus particulièrement l’attribut <code>SlowQueries </code>. Si les statistiques contiennent des requêtes lentes, le contrôle de l’intégrité renvoie un avertissement. Sinon, elle renvoie l’état OK .<br /> </p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DqueriesStatus%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Longueur de la file d’attente d’observation</td> 
   <td><p>La longueur de la file d’attente d’observation effectue une itération sur tous les programmes d’écoute d’événement et les observateurs en arrière-plan, compare la valeur <code>queueSize </code> à leur valeur <code>maxQueueSize</code> et :</p> 
    <ul> 
     <li>renvoie le statut « Critique » si la valeur <code>queueSize</code> dépasse la valeur <code>maxQueueSize</code> (c’est-à-dire lorsque des événements seraient supprimés) ;</li> 
     <li>renvoie le statut « Avertissement » si la valeur <code>queueSize</code> dépasse la valeur <code>maxQueueSize * WARN_THRESHOLD</code> (la valeur par défaut est 0,75). </li> 
    </ul> <p>La longueur maximale de chaque file d’attente provient de configurations distinctes (Oak et AEM) et n’est pas configurable à partir de ce contrôle de l’intégrité. Le MBean pour ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DObservationQueueLengthHealthCheck%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=ObservationQueueLengthHealthCheck,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Limites de requête transversales</td> 
   <td><p>Le contrôle Limites de requête transversales contrôle le MBean <code>QueryEngineSettings</code>, plus particulièrement les attributs <code>LimitInMemory</code> et <code>LimitReads</code> et renvoie le statut suivant :</p> 
    <ul> 
     <li>« Avertissement » si l’une des limites est égale ou supérieure à  <code>Integer.MAX_VALUE</code></li> 
     <li>« Avertissement » si l’une des limites est inférieure à 10 000 (paramètre recommandé d’Oak)</li> 
     <li>« Critique » si la valeur <code>QueryEngineSettings</code> ou l’une des limites ne peut pas être extraite.</li> 
    </ul> <p>Le MBean pour ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DqueryTraversalLimitsBundle%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=queryTraversalLimitsBundle,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Horloges synchronisées</td> 
   <td><p>Ce contrôle est pertinent uniquement pour les <a href="https://github.com/apache/sling-old-svn-mirror/blob/4df9ab2d6592422889c71fa13afd453a10a5a626/bundles/extensions/discovery/oak/src/main/java/org/apache/sling/discovery/oak/SynchronizedClocksHealthCheck.java">clusters d’entrepôt de nœuds de documents</a>. Elle renvoie l’état suivant :</p> 
    <ul> 
     <li>renvoie l’état Avertissement lorsque les horloges de l’instance ne sont pas synchronisées et dépassent un seuil inférieur prédéfini.</li> 
     <li>renvoie l’état Critique lorsque les horloges de l’instance ne sont pas synchronisées et dépassent un seuil élevé prédéfini.</li> 
    </ul> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DslingDiscoveryOakSynchronizedClocks%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=slingDiscoveryOakSynchronizedClocks,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Index asynchrones</td> 
   <td><p>La vérification des index asynchrones :</p> 
    <ul> 
     <li>renvoie l’état Critique si au moins une piste d’indexation échoue</li> 
     <li>vérifie la valeur <code>lastIndexedTime</code> pour toutes les pistes d’indexation et : 
      <ul> 
       <li>renvoie « Critique » si cela remonte à plus de 2 heures ; </li> 
       <li>renvoie « Avertissement » si le délai est compris entre 2 heures et 45 minutes ; </li> 
       <li>renvoie « OK » si cela remonte à moins de 45 minutes ; </li> 
      </ul> </li> 
     <li>si aucune de ces conditions n’est remplie, l’état OK est renvoyé.</li> 
    </ul> <p>Les seuils des états Critique et Avertissement sont configurables. Le MBean pour ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DasyncIndexHealthCheck%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=asyncIndexHealthCheck,type=HealthCheck</a>.</p> <p><strong>Remarque :</strong> Ce contrôle de l’intégrité est disponible avec AEM 6.4 et a été rétroporté dans AEM 6.3.0.1.</p> </td> 
  </tr> 
  <tr> 
   <td>Index Lucene volumineux</td> 
   <td><p>Ce contrôle utilise les données exposées par le MBean <code>Lucene Index Statistics</code> afin d’identifier des index volumineux et renvoie :</p> 
    <ul> 
     <li>un état d’avertissement s’il existe un index comportant plus d’un milliard de documents ;</li> 
     <li>un statut Critique s’il existe un index comportant plus de 1,5 milliard de documents ;</li> 
    </ul> <p>Les seuils sont configurables et le MBean du contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DlargeIndexHealthCheck%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=largeIndexHealthCheck,type=HealthCheck</a>.</p> <p><strong>Remarque : </strong>Ce contrôle est disponible avec AEM 6.4 et a été rétroporté à AEM 6.3.2.0.</p> </td> 
  </tr> 
  <tr> 
   <td>Maintenance du système</td> 
   <td><p>La maintenance du système est un contrôle composite, qui renvoie l’état « OK » si toutes les tâches de maintenance sont exécutées selon la configuration. Gardez à l’esprit que :</p> 
    <ul> 
     <li>chaque tâche de maintenance est accompagnée d’un contrôle de l’intégrité associé ;</li> 
     <li>si une tâche n’est pas ajoutée à une fenêtre de maintenance, son contrôle d’intégrité renvoie "Critique"</li> 
     <li>vous devez configurer les tâches de maintenance du journal d’audit et de purge des workflows ou les supprimer des fenêtres de maintenance. Si elles ne sont pas configurées, ces tâches échouent lors de la première tentative d’exécution, de sorte que la vérification de maintenance du système renvoie l’état "Critique".</li> 
     <li><strong>Avec AEM 6.4</strong>, il existe également un contrôle pour la variable <a href="/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks">Maintenance des fichiers binaires Lucene</a> tâche</li> 
     <li>Dans AEM 6.2 et version inférieure, le contrôle de la maintenance système renvoie un état « Avertissement » après le démarrage, car les tâches ne sont jamais exécutées. À partir de la version 6.3, ils renverront OK si la première fenêtre de maintenance n’a pas encore été atteinte.</li> 
    </ul> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3Dsystemchecks%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>File d’attente de réplication</td> 
   <td><p>Ce contrôle effectue une itération sur les agents de réplication et examine leurs files d’attente. Pour l’élément en haut de la file d’attente, le contrôle examine le nombre de fois où l’agent a tenté une réplication. Si l’agent a tenté une réplication plus de fois que défini par la valeur du paramètre <code>numberOfRetriesAllowed</code>, il renvoie un avertissement. Le paramètre <code>numberOfRetriesAllowed</code> est configurable. </p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DreplicationQueue%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Tâches Sling</td> 
   <td> 
    <div>
      Le contrôle Tâches Sling vérifie le nombre de tâches dans la file d’attente du gestionnaire de tâches, le compare au seuil <code>maxNumQueueJobs</code> et : 
    </div> 
    <ul> 
     <li>renvoie « Critique » si la file d’attente comporte plus de tâches que ne le définit la valeur <code>maxNumQueueJobs</code> ;</li> 
     <li>renvoie "Critique" si de principales tâches de longue durée ont plus d’une heure.</li> 
     <li>renvoie "Critique" s’il existe des tâches en file d’attente, et que la dernière tâche terminée a plus d’une heure.</li> 
    </ul> <p>Seul le nombre maximal de tâches en file d’attente est configurable et sa valeur par défaut est 1 000.</p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DslingJobs%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=slingJobs,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Performances des demandes</td> 
   <td><p>Ce contrôle cherche l’<a href="http://localhost:4502/system/console/slingmetrics" target="_blank">indicateur Sling</a> <code>granite.request.metrics.timer</code> et :</p> 
    <ul> 
     <li>renvoie "Critique" si la valeur du 75e percentile dépasse le seuil critique (la valeur par défaut est de 500 millisecondes).</li> 
     <li>renvoie "Avertissement" si la valeur du 75e percentile est supérieure au seuil d’avertissement (la valeur par défaut est de 200 millisecondes).</li> 
    </ul> <p>Le MBean de ce contrôle de l’intégrité est<em> </em><a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DrequestsStatus%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Erreurs de journal</td> 
   <td><p>Cette vérification renvoie l’état Avertissement en cas d’erreur dans le journal.</p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DlogErrorHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Espace disque</td> 
   <td><p>Le contrôle Espace disque observe le MBean <code>FileStoreStats</code>, extrait la taille de l’entrepôt de nœuds et la quantité d’espace disque utilisable sur la partition Entrepôt de nœuds, puis :</p> 
    <ul> 
     <li>renvoie "Avertissement" si le rapport espace disque utilisable/taille du référentiel est inférieur au seuil d’avertissement (la valeur par défaut est 10).</li> 
     <li>renvoie "Critique" si le rapport espace disque utilisable/taille du référentiel est inférieur au seuil critique (la valeur par défaut est 2).</li> 
    </ul> <p>Les deux seuils sont configurables. Le contrôle fonctionne uniquement sur les instances comportant un entrepôt de segments.</p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DDiskSpaceHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=DiskSpaceHealthCheck,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Vérification de l’intégrité de l’outil de planification</td> 
   <td><p>Ce contrôle renvoie un avertissement si l’instance possède des tâches Quartz en cours d’exécution depuis plus de 60 secondes. Le seuil de durée acceptable peut être configuré.</p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DslingCommonsSchedulerHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=slingCommonsSchedulerHealthCheck,type=HealthCheck</a><em>.</em></p> </td> 
  </tr> 
  <tr> 
   <td>Contrôles de sécurité</td> 
   <td><p>Le contrôle de sécurité est un contrôle composite, qui agrège les résultats de différents contrôles liés à la sécurité. Chacun de ces contrôles d’intégrité prennent en compte différentes préoccupations de la liste de contrôle de sécurité, disponibles dans la page de documentation <a href="/help/sites-administering/security-checklist.md">Liste de contrôle de sécurité.</a> Ils sont utiles comme test de vérification de la sécurité lorsque l’instance est démarrée. </p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3Dsecuritychecks%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=securitychecks,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Lots actifs</td> 
   <td><p>Principal Bundles vérifie l’état de tous les lots et :</p> 
    <ul> 
     <li>renvoie l’état Avertissement si l’un des lots n’est pas principal ou (en commençant par l’activation différée).</li> 
     <li>il ignore l’état des lots dans la liste d’exclusion.</li> 
    </ul> <p>Le paramètre de liste d’exclusion est configurable.</p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DinactiveBundles%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Vérification du cache du code</td> 
   <td><p>Il s’agit d’un contrôle de l’intégrité qui vérifie plusieurs conditions JVM pouvant déclencher un bogue CodeCache présent dans Java 7 :</p> 
    <ul> 
     <li>renvoie "Avertir" si l’instance est en cours d’exécution sur Java 7, avec la purge du cache de code activée.</li> 
     <li>renvoie "Avertissement" si l’instance est en cours d’exécution sur Java 7 et que la taille du cache de code réservé est inférieure à un seuil minimum (la valeur par défaut est 90 Mo).</li> 
    </ul> <p>Le seuil <code>minimum.code.cache.size</code> est configurable. Pour plus d’informations sur ce bogue, <a href="https://bugs.java.com/bugdatabase/view_bug.do?bug_id=8012547">consultez</a><a href="https://bugs.java.com/bugdatabase/view_bug.do?bug_id=8012547"></a><a href="https://bugs.java.com/bugdatabase/view_bug.do?bug_id=8012547"></a><a href="https://bugs.java.com/bugdatabase/view_bug.do?bug_id=8012547"> cette page</a>.</p> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DcodeCacheHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=codeCacheHealthCheck,type=HealthCheck</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Erreurs de chemin de recherche des ressources</td> 
   <td><p>Vérifie s’il existe des ressources dans le chemin d’accès <code>/apps/foundation/components/primary</code> et :</p> 
    <ul> 
     <li>renvoie « Avertissement » s’il y a des nœuds enfants sous  <code>/apps/foundation/components/primary</code></li> 
    </ul> <p>Le MBean de ce contrôle de l’intégrité est <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DresourceSearchPathErrorHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=resourceSearchPathErrorHealthCheck,type=HealthCheck</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Surveillance avec Nagios {#monitoring-with-nagios}

Le tableau de bord des contrôles de l’intégrité peut être intégré à Nagios par le biais des MBeans JMX Granite. L’exemple ci-dessous indique comment ajouter un contrôle qui affiche la mémoire utilisée sur le serveur qui exécute AEM.

1. Configurez et installez Nagios sur le serveur de surveillance.
1. Installez ensuite Nagios Remote Plugin Executor (NRPE).

   >[!NOTE]
   >
   >Pour plus d’informations sur l’installation de Nagios et NRPE sur votre système, consultez la section [Documentation Nagios](https://library.nagios.com/library/products/nagioscore/manuals/).

1. Ajoutez une définition de l’hôte pour le serveur AEM. Pour ce faire, utilisez le gestionnaire de configuration de l’interface web de Nagios XI :

   1. Ouvrez un navigateur et pointez vers le serveur Nagios.
   1. Appuyez sur le bouton **Configure** dans le menu supérieur.
   1. Dans le volet de gauche, appuyez sur **Gestionnaire de configuration principale** sous **Configuration avancée**.
   1. Cliquez sur le lien **Hôtes** sous la section **Surveillance**.
   1. Ajoutez la définition de l’hôte :

   ![chlimage_1-416](assets/chlimage_1-416.png)

   Voici un exemple de fichier de configuration de l’hôte si vous utilisez Nagios Core :

   ```xml
   define host {
      address 192.168.0.5
      max_check_attempts 3
      check_period 24x7
      check-command check-host-alive
      contacts admin
      notification_interval 60
      notification_period 24x7
   }
   ```

1. Installez Nagios et NRPE sur le serveur AEM.
1. Installez le [check_http_json](https://github.com/phrawzty/check_http_json) sur les deux serveurs.
1. Définissez une commande de contrôle JSON générique sur les deux serveurs :

   ```xml
   define command{
   
       command_name    check_http_json-int
   
       command_line    /usr/lib/nagios/plugins/check_http_json --user "$ARG1$" --pass "$ARG2$" -u 'https://$HOSTNAME$:$ARG3$/$ARG4$' -e '$ARG5$' -w '$ARG6$' -c '$ARG7$'
   
   }
   ```

1. Ajoutez un service pour la mémoire utilisée sur le serveur AEM :

   ```xml
   define service {
   
       use generic-service
   
       host_name my.remote.host
   
       service_description AEM Author Used Memory
   
       check_command  check_http_json-int!<cq-user>!<cq-password>!<cq-port>!system/sling/monitoring/mbeans/java/lang/Memory.infinity.json!{noname}.mbean:attributes.HeapMemoryUsage.mbean:attributes.used.mbean:value!<warn-threshold-in-bytes>!<critical-threshold-in-bytes>
   
       }
   ```

1. Reportez-vous au tableau de bord Nagios du service que vous venez de créer :

   ![chlimage_1-417](assets/chlimage_1-417.png)

## Outils de diagnostic {#diagnosis-tools}

Le tableau de bord des opérations donne également accès aux outils de diagnostic qui peuvent vous aider à trouver et à résoudre les causes profondes des avertissements provenant du tableau de bord du contrôle de l’intégrité, ainsi qu’à fournir des informations de débogage importantes aux opérateurs système.

Parmi ses principales caractéristiques :

* Un analyseur de messages de journal
* La possibilité d’accéder aux vidages de tas et de threads
* Requêtes et analyseurs de performances des requêtes

Pour accéder à l’écran Outils de diagnostic, sélectionnez **Outils > Opérations > Diagnostic** dans l’écran d’accueil d’AEM. Vous pouvez également accéder à l’écran en accédant directement à l’URL suivante : `https://serveraddress:port/libs/granite/operations/content/diagnosis.html`.

![chlimage_1-418](assets/chlimage_1-418.png)

### Messages du journal {#log-messages}

Par défaut, l’interface utilisateur des messages du journal affiche tous les messages ERREUR. Si vous souhaitez afficher davantage de messages de journal, vous devez configurer un journal avec le niveau de journal approprié.

Les messages du journal utilisent un appender de journal en mémoire et ne sont donc pas liés aux fichiers journaux. En outre, la modification des niveaux de journal dans cette interface utilisateur ne modifie pas les informations consignées dans les fichiers journaux traditionnels. L’ajout et la suppression d’enregistreurs dans cette interface utilisateur affectent uniquement l’enregistreur dans la mémoire. Notez également que la modification des configurations de l’enregistreur se répercutera à l’avenir de l’enregistreur en mémoire. Les entrées déjà enregistrées et qui ne sont plus pertinentes ne sont pas supprimées, mais des entrées similaires ne seront plus enregistrées à l’avenir.

Vous pouvez configurer les éléments journalisés en fournissant des configurations d’enregistreur en cliquant sur l’icône d’engrenage dans la partie supérieure gauche de l’interface utilisateur. Vous pouvez y ajouter, supprimer ou mettre à jour des configurations d’enregistreur. Une configuration d’enregistreur se compose d’un **niveau de journal** (AVERTISSEMENT/INFO/DÉBOGAGE) et d’un **nom de filtre**. Le **nom du filtre** est chargé de filtrer la source des messages du journal consignés. Si un enregistreur doit enregistrer tous les messages du journal pour un niveau spécifié, le nom du filtre doit être « **root** ». La définition du niveau d&#39;un enregistreur déclenche la capture de tous les messages dont le niveau est égal ou supérieur à celui spécifié.

Exemples :

* Si vous envisagez d’enregistrer tous les messages **ERREUR**, aucune configuration n’est nécessaire. Tous les messages ERROR sont capturés par défaut.
* Si vous envisagez de capturer toutes les **ERROR**, **WARN** et **INFO** messages : le nom de l’enregistreur doit être défini sur : &quot;**root**&quot;, et le niveau de journalisation à : **INFO**.

* Si vous envisagez de capturer tous les messages provenant d’un certain package (par exemple com.adobe.granite), le nom de l’enregistreur doit être défini sur : &quot;com.adobe.granite&quot; et le niveau de journalisation à : **DEBUG** (cette opération capturera toutes les **ERROR**, **WARN**, **INFO** et **DEBUG** messages), comme illustré dans l’image ci-dessous.

![chlimage_1-419](assets/chlimage_1-419.png)

>[!NOTE]
>
>Vous ne pouvez pas définir un nom d’enregistreur de manière à consigner uniquement les messages ERREUR par le biais d’un filtre spécifié. Par défaut, tous les messages ERROR sont capturés.

>[!NOTE]
>
>L’interface utilisateur des messages du journal ne reflète pas le journal d’erreurs réel. À moins que vous n’ayez configuré d’autres types de messages du journal dans l’interface utilisateur, seuls les messages d’erreur s’affichent. Pour savoir comment afficher des messages de journal spécifiques, reportez-vous aux instructions ci-dessus.

>[!NOTE]
>
>Les paramètres de la page de diagnostic n’ont aucune incidence sur les éléments consignés dans les fichiers journaux et inversement. Ainsi, même si le journal d’erreurs peut capturer des messages INFO, il est possible qu’ils ne s’affichent pas dans l’interface utilisateur des messages du journal. Par ailleurs, par le biais de l’interface utilisateur, il est possible de capturer des messages DÉBOGAGE provenant de certains packages sans que cela affecte le journal des erreurs. Pour plus d’informations sur la configuration des fichiers journaux, consultez la section [Journalisation](/help/sites-deploying/configure-logging.md).

>[!NOTE]
>
>**Dans AEM 6.4**, les tâches de maintenance sont journalisées prêtes à l’emploi dans un format d’information enrichi au niveau INFO. Cela permet une meilleure visibilité de l’état des tâches de maintenance.
>
>Si vous utilisez des outils tiers (tels que Splunk) pour surveiller l’activité de tâche de maintenance et y réagir, vous pouvez utiliser les instructions de journal suivantes :

```
Log level: INFO
DATE+TIME [MaintanceLogger] Name=<MT_NAME>, Status=<MT_STATUS>, Time=<MT_TIME>, Error=<MT_ERROR>, Details=<MT_DETAILS>
```

### Performances des requêtes {#request-performance}

La page Performances des demandes permet d’analyser les demandes de page les plus lentes traitées. Seules les demandes de contenu sont enregistrées dans cette page. Plus précisément, les requêtes suivantes seront capturées :

1. Demandes d’accès aux ressources sous `/content`
1. Demandes d’accès aux ressources sous `/etc/design`
1. Demandes comportant l’extension `".html"`

![chlimage_1-420](assets/chlimage_1-420.png)

La page affiche :

* Heure à laquelle la demande a été effectuée
* L’URL et la méthode de requête
* Durée en millisecondes

Par défaut, les 20 requêtes de page les plus lentes sont capturées, mais la limite peut être modifiée dans Configuration Manager.

### Performance des requêtes {#query-performance}

La page Performance des requêtes permet d’analyser les requêtes les plus lentes exécutées par le système. Ces informations sont fournies par le référentiel dans un MBean JMX. Ces informations sont fournies par le MBean JMX `com.adobe.granite.QueryStat` dans Jackrabbit et par `org.apache.jackrabbit.oak.QueryStats.` dans le référentiel Oak.

La page affiche :

* Heure à laquelle la requête a été effectuée
* La langue de la requête
* Nombre d’envois de la requête.
* L’instruction de la requête
* Durée en millisecondes

![chlimage_1-421](assets/chlimage_1-421.png)

### Expliquer la requête {#explain-query}

Oak tente de déterminer la meilleure façon d’exécuter une requête donnée d’après les index Oak définis dans le référentiel sous le nœud **oak:index**. En fonction de la requête, Oak peut sélectionner différents index. La première étape de l’optimisation de la requête consiste à comprendre comment Oak exécute une requête.

L’outil Expliquer la requête explique la façon dont Oak exécute une requête. Pour y accéder, accédez à **Outils - Opérations - Diagnostic** dans l’écran de bienvenue AEM, puis cliquez sur **Performances des requêtes** et le passage à la fonction **Expliquer la requête** .

**Fonctionnalités**

* Prend en charge les langages de requête Xpath, JCR-SQL et JCR-SQL2.
* Indique le temps d’exécution réel de la requête spécifiée.
* Détecte les requêtes lentes et vous avertit au sujet des requêtes pouvant être potentiellement lentes.
* Indique l’index Oak utilisé pour exécuter la requête.
* Affiche l’explication réelle du moteur de requête Oak.
* Fournit une liste de clics pour charger des requêtes lentes et populaires

Une fois que vous êtes dans l’interface utilisateur Expliquer la requête , il vous suffit de saisir la requête et d’appuyer sur la touche **Expliquer** button :

![chlimage_1-422](assets/chlimage_1-422.png)

La première entrée de la section Explication de la requête est l’explication réelle. L’explication indique le type d’index utilisé pour exécuter la requête.

La seconde entrée est le plan d&#39;exécution.

Choisir le **Inclure le temps d’exécution** avant d’exécuter la requête, indique également le temps pendant lequel la requête a été exécutée, ce qui permet d’obtenir plus d’informations qui peuvent être utilisées pour optimiser les index pour votre application ou déploiement.

![chlimage_1-423](assets/chlimage_1-423.png)

### Gestionnaire d’index {#the-index-manager}

Le gestionnaire d’index a pour objectif de faciliter la gestion des index, comme la maintenance des index ou l’affichage de leur état.

Pour y accéder, sélectionnez **Outil - Opérations - Diagnostic** dans l’écran d’accueil, puis cliquez sur le bouton **Gestionnaire d’index**.

Il est également accessible directement à cette adresse : `https://serveraddress:port/libs/granite/operations/content/diagnosistools/indexManager.html`.

![chlimage_1-424](assets/chlimage_1-424.png)

L’interface utilisateur peut être utilisée pour filtrer les index du tableau en saisissant les critères de filtre dans la zone de recherche située dans le coin supérieur gauche de l’écran.

### Télécharger le ZIP d’état {#download-status-zip}

Cette option permet de télécharger un fichier ZIP contenant des informations utiles sur l’état et la configuration du système. L’archive contient des configurations d’instance, une liste de lots, OSGi, des indicateurs Sling et des statistiques. Le fichier qui en résulte peut être volumineux. Vous pouvez réduire l’impact des fichiers d’état volumineux à l’aide de la fenêtre **Télécharger le ZIP d’état**. Pour y accéder, sélectionnez **AEM > Outils > Opérations > Diagnostic > Télécharger le fichier de statut au format ZIP.**

Dans cette fenêtre, vous pouvez sélectionner les éléments à exporter (fichiers journaux et image mémoire des threads) ainsi que le nombre de jours à prendre en compte dans le téléchargement par rapport à la date actuelle.

![download_status_zip](assets/download_status_zip.png)

### Télécharger l’image mémoire des threads {#download-thread-dump}

Cette option déclenche le téléchargement d’un fichier ZIP contenant des informations sur les threads présents sur le système. Des informations sur chaque thread sont fournies, telles que son état, le chargeur de classe et la trace de pile.

### Télécharger l’image mémoire des segments de mémoire {#download-heap-dump}

Vous avez également la possibilité de télécharger un instantané du segment de mémoire afin de l’analyser ultérieurement. Notez que cela déclenchera le téléchargement d’un fichier volumineux de l’ordre de plusieurs centaines de mégaoctets.

## Tâches de maintenance automatisées {#automated-maintenance-tasks}

Depuis la page Tâches de maintenance automatisées, affichez et suivez les tâches de maintenance recommandées planifiées pour une exécution périodique. Les tâches sont intégrées au système de contrôle de l’intégrité. Les tâches peuvent également être exécutées manuellement à partir de l’interface.

Pour accéder à la page Maintenance du tableau de bord des opérations, vous devez accéder à la section **Outils - Opérations - Tableau de bord - Maintenance** à partir de l’écran de bienvenue AEM ou suivez directement ce lien :

`https://serveraddress:port/libs/granite/operations/content/maintenance.html`

Les tâches ci-dessous sont disponibles dans le tableau de bord des opérations :

1. La tâche **Nettoyage des révisions**, située sous **Période de maintenance quotidienne** .

1. La tâche **Nettoyage des binaires Lucene**, située sous **Période de maintenance quotidienne** .

1. La tâche **Purge du workflow **, située sous la tâche **Période de maintenance hebdomadaire** .

1. Tâche **Nettoyage de la mémoire d’entrepôt de données** dans le menu **Période de maintenance hebdomadaire**

1. Tâche **Maintenance des journaux d’audit** dans le menu **Période de maintenance hebdomadaire**

1. Tâche **Maintenance de la purge des versions** dans le menu **Période de maintenance hebdomadaire**

La synchronisation par défaut pour la période de maintenance quotidienne a lieu de 2 h à 5 h du matin. Les tâches configurées pour s’exécuter dans la fenêtre de maintenance hebdomadaire s’exécuteront entre 1h00 et 2h00 le samedi.

Vous pouvez également configurer les minutages en appuyant sur l’icône d’engrenage sur l’une des deux cartes de maintenance :

![chlimage_1-425](assets/chlimage_1-425.png)

>[!NOTE]
>
>Depuis AEM 6.1, les fenêtres de maintenance existantes peuvent également être configurées pour s’exécuter tous les mois.

### Nettoyage de la révision {#revision-clean-up}

Pour plus d’informations sur l’exécution du nettoyage des révisions pour AEM 6.4, [voir cet article dédié](/help/sites-deploying/revision-cleanup.md).

### Nettoyage des binaires Lucene {#lucene-binaries-cleanup}

Utilisez la tâche Nettoyage des binaires Lucene pour purger les fichiers binaires Lucene et réduire la taille nécessaire pour l’exécution de l’entrepôt de données. En effet, le taux de perte des fichiers binaires Lucene est redéclaré tous les jours, à la place de l’ancienne dépendance, lors d’une exécution réussie du [nettoyage de l’entrepôt de données](/help/sites-administering/data-store-garbage-collection.md).

Bien que la tâche de maintenance ait été développée pour réduire les déchets de révision liés à Lucene, il existe des gains d’efficacité généraux lors de l’exécution de la tâche :

* L’exécution hebdomadaire de la tâche de nettoyage de la mémoire d’entrepôt de données se terminera plus rapidement.
* Elle peut également améliorer légèrement les performances générales d’AEM.

Pour accéder à la tâche Nettoyage des binaires Lucene, sélectionnez **AEM > Outils > Opérations > Maintenance > Période de maintenance quotidienne > Nettoyage des binaires Lucene**.

### Récupération de l’espace mémoire du magasin de données {#data-store-garbage-collection}

Pour plus d’informations sur le nettoyage de la mémoire d’entrepôt de données, reportez-vous à la section dédiée [page de documentation](/help/sites-administering/data-store-garbage-collection.md).

### Purge des workflows {#workflow-purge}

Il est possible également de purger les workflows à partir du tableau de bord de maintenance. Pour exécuter la tâche Purge du workflow, vous devez :

1. Cliquez sur le bouton **Période de maintenance hebdomadaire** page.
1. Dans la page suivante, cliquez sur le bouton **Play** dans le **Purge des workflows** carte.

>[!NOTE]
>
>Pour plus d’informations sur la maintenance des workflows, voir [cette page](workflows-administering.md#regular-purging-of-workflow-instances).

### Maintenance des journaux d’audit {#audit-log-maintenance}

Pour en savoir plus sur la maintenance des journaux d’audit, consultez cette [page de la documentation](/help/sites-administering/operations-audit-log.md).

### Purge de version {#version-purge}

Vous pouvez planifier la tâche de maintenance Purge de version pour supprimer automatiquement les anciennes versions. [Vous aurez ainsi moins besoin d’utiliser manuellement les outils de purge de version](/help/sites-deploying/version-purging.md). Pour planifier et configurer la tâche Purge de version, sélectionnez **Outils > Opérations > Maintenance > Période de maintenance hebdomadaire** et procédez comme suit :

1. Cliquez sur le bouton **Ajouter**.
1. Sélectionnez **Purge de version** dans le menu déroulant.

   ![version_purge_maintenancetask](assets/version_purge_maintenancetask.png)

1. Pour configurer la tâche Purge de version, cliquez sur l’icône d’**engrenage** sur la carte de maintenance Purge de version qui vient d’être créée.

   ![version_purge_taskconfiguration](assets/version_purge_taskconfiguration.png)

**Avec AEM 6.4**, vous pouvez arrêter la tâche de maintenance Purge de version comme suit :

* Automatiquement : si la période de maintenance planifiée se termine avant que la tâche ne puisse se terminer, celle-ci s’arrête automatiquement. Elle reprend lorsque la fenêtre de maintenance suivante s’ouvre.
* Manuellement : pour arrêter manuellement la tâche, sur la carte de maintenance Purge de version, cliquez sur l’icône **Arrêter**. Lors de la prochaine exécution, la tâche reprendra en toute sécurité.

>[!NOTE]
>
>Arrêter la tâche de maintenance signifie suspendre son exécution sans perdre la trace du traitement déjà en cours.

>[!CAUTION]
>
>Pour optimiser la taille du référentiel, vous devez exécuter la tâche Purge de version fréquemment. La tâche doit être planifiée en dehors des heures de bureau lorsqu’il y a un trafic limité.

## Tâches de maintenance personnalisées {#custom-maintenance-tasks}

Les tâches de maintenance personnalisées peuvent être mises en œuvre sous forme de services OSGi. Lorsque l’infrastructure des tâches de maintenance repose sur le traitement des tâches Apache Sling, une tâche de maintenance doit mettre en œuvre l’interface Java ` [org.apache.sling.event.jobs.consumer.JobExecutor](https://sling.apache.org/apidocs/sling7/org/apache/sling/event/jobs/consumer/JobExecutor.html)`. De plus, pour être détectée comme tâche de maintenance, elle doit déclarer différentes propriétés d’enregistrement de service, comme indiqué ci-dessous :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nom de la propriété du service</strong><br /> </td> 
   <td><strong>Description</strong></td> 
   <td><strong>Exemple</strong><br /> </td> 
   <td><strong>Type</strong></td> 
  </tr> 
  <tr> 
   <td>granite.maintenance.isStoppable</td> 
   <td>Attribut booléen définissant si la tâche peut être arrêtée par l’utilisateur. Si une tâche indique qu’elle peut être arrêtée, elle doit vérifier pendant son exécution si elle a été arrêtée, puis agir en conséquence. La valeur par défaut est false.</td> 
   <td>true</td> 
   <td>Facultative</td> 
  </tr> 
  <tr> 
   <td>granite.maintenance.mandatory</td> 
   <td>Attribut booléen définissant si une tâche est obligatoire et doit être exécutée périodiquement. Si une tâche est obligatoire, mais qu’elle ne se trouve pas actuellement dans une fenêtre de planification active, un contrôle de l’intégrité signale qu’il s’agit d’une erreur. La valeur par défaut est false.</td> 
   <td>true</td> 
   <td>Facultative</td> 
  </tr> 
  <tr> 
   <td>granite.maintenance.name</td> 
   <td>Nom unique de la tâche : il est utilisé pour référencer la tâche. Il s’agit généralement d’un nom simple.</td> 
   <td>MyMaintenanceTask</td> 
   <td>Requise</td> 
  </tr> 
  <tr> 
   <td>granite.maintenance.title</td> 
   <td>Titre affiché pour cette tâche</td> 
   <td>Ma tâche de maintenance spéciale</td> 
   <td>Requise</td> 
  </tr> 
  <tr> 
   <td>job.topics</td> 
   <td>Il s’agit d’une rubrique unique à la tâche de maintenance.<br /> Le traitement des tâches Apache Sling démarre une tâche avec précisément cette rubrique afin d’exécuter la tâche de maintenance ; lorsque la tâche est enregistrée pour cette rubrique, elle est exécutée.<br /> La rubrique doit commencer par <i>com/adobe/granite/maintenance/job/</i>.</td> 
   <td>com/adobe/granite/maintenance/job/MyMaintenanceTask</td> 
   <td>Requise</td> 
  </tr> 
 </tbody> 
</table>

En dehors des propriétés de service ci-dessus, la méthode `process()` de l’interface `JobConsumer` doit être mise en œuvre en ajoutant le code à exécuter pour la tâche de maintenance. L’élément `JobExecutionContext` fourni peut être utilisé pour générer les informations de statut. Vérifiez si la tâche est interrompue par l’utilisateur et produit un résultat (réussite ou échec).

Dans les cas où une tâche de maintenance ne doit pas être exécutée sur toutes les installations (si vous l’exécutez uniquement sur l’instance de publication, par exemple), vous pouvez faire en sorte que le service doive être configuré de manière à être actif en ajoutant `@Component(policy=ConfigurationPolicy.REQUIRE)`. Vous pouvez alors marquer la configuration correspondante comme étant dépendante du mode d’exécution dans le référentiel. Pour plus d’informations, consultez la section [Configuration d’OSGi](/help/sites-deploying/configuring-osgi.md#creating-the-configuration-in-the-repository).

Vous trouverez ci-dessous un exemple de tâche de maintenance personnalisée qui supprime des fichiers d’un répertoire temporaire configurable qui ont été modifiés au cours des dernières 24 heures :

src/main/java/com/adobe/granite/samples/maintenance/impl/DeleteTempFilesTask.java

<table> 
 <tbody> 
  <tr> 
   <td><p> </p> <p><code>/*</code></p> <p><code> * #%L</code></p> <p><code> * sample-maintenance-task</code></p> <p><code> * %%</code></p> <p><code> * Copyright (C) 2014 Adobe</code></p> <p><code> * %%</code></p> <p><code> * Licensed under the Apache License, Version 2.0 (the "License");</code></p> <p><code> * you may not use this file except in compliance with the License.</code></p> <p><code> * You may obtain a copy of the License at</code></p> <p><code> * </code></p> <p><code> * <a href="https://www.apache.org/licenses/LICENSE-2.0">https://www.apache.org/licenses/LICENSE-2.0</a></code></p> <p><code> * </code></p> <p><code> * Unless required by applicable law or agreed to in writing, software</code></p> <p><code> * distributed under the License is distributed on an "AS IS" BASIS,</code></p> <p><code> * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.</code></p> <p><code> * See the License for the specific language governing permissions and</code></p> <p><code> * limitations under the License.</code></p> <p><code> * #L%</code></p> <p><code> */</code></p> <p><code> </code></p> <p><code>package com.adobe.granite.samples.maintenance.impl;</code></p> <p><code> </code></p> <p><code>import java.io.File;</code></p> <p><code>import java.util.Calendar;</code></p> <p><code>import java.util.Collection;</code></p> <p><code>import java.util.Map;</code></p> <p><code> </code></p> <p><code>import org.apache.commons.io.FileUtils;</code></p> <p><code>import org.apache.commons.io.filefilter.IOFileFilter;</code></p> <p><code>import org.apache.commons.io.filefilter.TrueFileFilter;</code></p> <p><code>import org.apache.felix.scr.annotations.Activate;</code></p> <p><code>import org.apache.felix.scr.annotations.Component;</code></p> <p><code>import org.apache.felix.scr.annotations.Properties;</code></p> <p><code>import org.apache.felix.scr.annotations.Property;</code></p> <p><code>import org.apache.felix.scr.annotations.Service;</code></p> <p><code>import org.apache.sling.commons.osgi.PropertiesUtil;</code></p> <p><code>import org.apache.sling.event.jobs.Job;</code></p> <p><code>import org.apache.sling.event.jobs.consumer.JobConsumer;</code></p> <p><code>import org.apache.sling.event.jobs.consumer.JobExecutionContext;</code></p> <p><code>import org.apache.sling.event.jobs.consumer.JobExecutionResult;</code></p> <p><code>import org.apache.sling.event.jobs.consumer.JobExecutor;</code></p> <p><code>import org.slf4j.Logger;</code></p> <p><code>import org.slf4j.LoggerFactory;</code></p> <p><code> </code></p> <p><code>import com.adobe.granite.maintenance.MaintenanceConstants;</code></p> <p><code> </code></p> <p><code>@Component(metatype = true,</code></p> <p><code> label = "Delete Temp Files Maintenance Task",</code></p> <p><code> description = "Maintatence Task which deletes files from a configurable temporary directory which have been modified in the last 24 hours.")</code></p> <p><code>@Service</code></p> <p><code>@Properties({</code></p> <p><code> @Property(name = MaintenanceConstants.PROPERTY_TASK_NAME, value = "DeleteTempFilesTask", propertyPrivate = true),</code></p> <p><code> @Property(name = MaintenanceConstants.PROPERTY_TASK_TITLE, value = "Delete Temp Files", propertyPrivate = true),</code></p> <p><code> @Property(name = JobConsumer.PROPERTY_TOPICS, value = MaintenanceConstants.TASK_TOPIC_PREFIX</code></p> <p><code> + "DeleteTempFilesTask", propertyPrivate = true) })</code></p> <p><code>public class DeleteTempFilesTask implements JobExecutor {</code></p> <p><code> </code></p> <p><code> private static final Logger log = LoggerFactory.getLogger(DeleteTempFilesTask.class);</code></p> <p><code> </code></p> <p><code> @Property(label = "Temporary Directory", description="Temporary Directory. Defaults to the java.io.tmpdir system property.")</code></p> <p><code> private static final String PROP_TEMP_DIR = "temp.dir";</code></p> <p><code> </code></p> <p><code> private File tempDir;</code></p> <p><code> </code></p> <p><code> @Activate</code></p> <p><code> private void activate(Map&lt;string, object=""&gt; properties) {</code></p> <p><code> this.tempDir = new File(PropertiesUtil.toString(properties.get(PROP_TEMP_DIR),</code></p> <p><code> System.getProperty("java.io.tmpdir")));</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code> @Override</code></p> <p><code> public JobExecutionResult process(Job job, JobExecutionContext context) {</code></p> <p><code> log.info("Deleting old temp files from {}.", tempDir.getAbsolutePath());</code></p> <p><code> Collection&lt;file&gt; files = FileUtils.listFiles(tempDir, new LastModifiedBeforeYesterdayFilter(),</code></p> <p><code> TrueFileFilter.INSTANCE);</code></p> <p><code> int counter = 0;</code></p> <p><code> for (File file : files) {</code></p> <p><code> log.debug("Deleting file {}.", file.getAbsolutePath());</code></p> <p><code> counter++;</code></p> <p><code> file.delete();</code></p> <p><code> // TODO - capture the output of delete() and do something useful with it</code></p> <p><code> }</code></p> <p><code> return context.result().message(String.format("Deleted %s files.", counter)).succeeded();</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code> /**</code></p> <p><code> * IOFileFilter which filters out files which have been modified in the last 24 hours.</code></p> <p><code> *</code></p> <p><code> */</code></p> <p><code> private static class LastModifiedBeforeYesterdayFilter implements IOFileFilter {</code></p> <p><code> </code></p> <p><code> private final long minTime;</code></p> <p><code> </code></p> <p><code> private LastModifiedBeforeYesterdayFilter() {</code></p> <p><code> Calendar cal = Calendar.getInstance();</code></p> <p><code> cal.add(Calendar.DATE, -1);</code></p> <p><code> this.minTime = cal.getTimeInMillis();</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code> @Override</code></p> <p><code> public boolean accept(File dir, String name) {</code></p> <p><code> // this method is never actually called.</code></p> <p><code> return false;</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code> @Override</code></p> <p><code> public boolean accept(File file) {</code></p> <p><code> return file.lastModified() <= this.minTime;</code></p> <p><code> }</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code>}</code></p> <p><code>&lt;file&gt;&lt;/string,&gt;</code></p> <p> </p> </td> 
  </tr> 
 </tbody> 
</table>

[experiencemanager-java-maintenancetask-sample](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-maintenancetask-sample)- [src/main/java/com/adobe/granite/samples/maintenance/impl/DeleteTempFilesTask.java](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-maintenancetask-sample/blob/master/src/main/java/com/adobe/granite/samples/maintenance/impl/DeleteTempFilesTask.java)

Une fois le service déployé, il est exposé à l’interface utilisateur du tableau de bord des opérations et peut être ajouté à l’une des plannings de maintenance disponibles :

![chlimage_1-426](assets/chlimage_1-426.png)

Une ressource correspondant sera ajoutée à l’adresse /apps/granite/operations/config/maintenance/`schedule`/`taskname`. Si la tâche dépend du mode d’exécution, la propriété granite.operations.conditions.runmode doit être définie sur ce noeud avec les valeurs des modes d’exécution qui doivent être principales pour cette tâche de maintenance.

## Présentation du système {#system-overview}

Le **tableau de bord de présentation du système** présente en détail la configuration, le matériel et l’intégrité de l’instance AEM. En d’autres termes, le statut d’intégrité du système est transparent et toutes les informations sont agrégées dans un tableau de bord unique.

>[!NOTE]
>
>Vous pouvez également [visionner cette vidéo](https://video.tv.adobe.com/v/21340) pour découvrir une présentation du tableau de bord de présentation du système.

### Accès {#how-to-access}

Pour accéder au tableau de bord de présentation du système, sélectionnez **Outils > Opérations > Présentation du système**.

![system_overview_dashboard](assets/system_overview_dashboard.png)

### Explication du tableau de bord de présentation du système {#system-overview-dashboard-explained}

Le tableau ci-dessous décrit toutes les informations affichées dans le tableau de bord de présentation du système. Gardez à l’esprit que lorsqu’il n’y a aucune information pertinente à afficher (par exemple, la sauvegarde n’est pas en cours, aucun contrôle de l’intégrité n’est critique), la section correspondante affichera le message &quot;Aucune entrée&quot;.

Vous pouvez également télécharger un fichier `JSON` qui récapitule les informations du tableau de bord en cliquant sur le bouton **Télécharger** dans le coin supérieur droit du tableau de bord. Le point d’entrée `JSON` est `/libs/granite/operations/content/systemoverview/export.json` et il peut être utilisé dans un script `curl` pour la surveillance externe.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Section</strong></td> 
   <td><strong>Informations affichées</strong></td> 
   <td><strong>Statut « Critique »</strong></td> 
   <td><strong>Est lié à</strong></td> 
  </tr> 
  <tr> 
   <td>Contrôles de l'intégrité</td> 
   <td> 
    <ul> 
     <li>Liste des contrôles qui sont à l’état Critique</li> 
     <li>Liste des vérifications dont l’état est Avertissement</li> 
    </ul> </td> 
   <td>Indiqué visuellement :<br /> 
    <ul> 
     <li>Indicateur rouge pour les contrôles critiques</li> 
     <li>Indicateur orange pour les contrôles Warn</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Page Rapports d’intégrité</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Tâches de maintenance</td> 
   <td> 
    <ul> 
     <li>Liste des tâches ayant échoué</li> 
     <li>Liste des tâches en cours d’exécution</li> 
     <li>Liste des tâches ayant réussi lors de la dernière exécution</li> 
     <li>Liste des tâches qui n’ont jamais été exécutées</li> 
     <li>Liste des tâches non planifiées</li> 
    </ul> </td> 
   <td><p>Indiqué visuellement :</p> 
    <ul> 
     <li>Indicateur rouge pour les tâches en échec</li> 
     <li>une balise orange pour l’exécution des tâches (car elles peuvent avoir un impact sur les performances).</li> 
     <li>balises grises pour chaque état</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Page Tâches de maintenance</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Système</td> 
   <td> 
    <ul> 
     <li>Système d’exploitation et version du système d’exploitation (par exemple, Mac OS X)</li> 
     <li>Charge moyenne du système, extraite de <a href="https://docs.oracle.com/javase/8/docs/api/java/lang/management/OperatingSystemMXBean.html#getSystemLoadAverage--">OperatingSystemMXBeanusable</a></li> 
     <li>espace disque (sur la partition où se trouve le répertoire racine)</li> 
     <li>Nombre maximal de segments de mémoire, renvoyé par <a href="https://docs.oracle.com/javase/8/docs/api/java/lang/management/MemoryMXBean.html#getHeapMemoryUsage--">MemoryMXBean</a></li> 
    </ul> </td> 
   <td>S/O</td> 
   <td>S/O</td> 
  </tr> 
  <tr> 
   <td>Instance</td> 
   <td> 
    <ul> 
     <li>la version AEM</li> 
     <li>liste des modes d’exécution</li> 
     <li>date de démarrage de l’instance</li> 
    </ul> </td> 
   <td>S/O</td> 
   <td>S/O</td> 
  </tr> 
  <tr> 
   <td>Référentiel</td> 
   <td> 
    <ul> 
     <li>la version Oak</li> 
     <li>type de magasin de noeuds (Segment Tar ou Document) 
      <ul> 
       <li>si le type est document, le type de magasin de documents s’affiche (RDB ou Mongo).</li> 
      </ul> </li> 
     <li>s’il existe un entrepôt de données personnalisé : 
      <ul> 
       <li>pour un entrepôt de données basé sur les fichiers, le chemin d’accès s’affiche.</li> 
       <li>pour un entrepôt de données S3, le nom du compartiment S3 s’affiche.</li> 
       <li>pour un entrepôt de données S3 partagé, le nom du compartiment S3 s’affiche.</li> 
       <li>pour un magasin de données Azure, le conteneur s’affiche.</li> 
      </ul> </li> 
     <li>s’il n’existe pas de banque de données externe personnalisée, un message indiquant ce fait s’affiche.</li> 
    </ul> </td> 
   <td>S/O</td> 
   <td>S/O</td> 
  </tr> 
  <tr> 
   <td>Agents de distribution</td> 
   <td> 
    <ul> 
     <li>une liste d’agents avec des files d’attente bloquées ;</li> 
     <li>une liste des agents mal configurés ("Erreur de configuration")</li> 
     <li>une liste d’agents dont le traitement de la file d’attente est en pause</li> 
     <li>une liste des agents inactifs</li> 
     <li>une liste des agents en cours d’exécution (qui sont actuellement des entrées de traitement) ;</li> 
    </ul> </td> 
   <td><p>Indiqué visuellement :</p> 
    <ul> 
     <li>Indicateur rouge pour les agents bloqués ou les erreurs de configuration</li> 
     <li>une balise orange pour les agents en pause</li> 
     <li>une balise grise pour les agents en pause, inactifs ou en cours d’exécution ;<br /> </li> 
    </ul> </td> 
   <td>Page de distribution<br /> </td> 
  </tr> 
  <tr> 
   <td>Agents de réplication</td> 
   <td> 
    <ul> 
     <li>une liste d’agents avec des files d’attente bloquées ;</li> 
     <li>une liste des agents inactifs</li> 
     <li>une liste des agents en cours d’exécution (qui sont actuellement des entrées de traitement) ;</li> 
    </ul> </td> 
   <td><p>Indiqué visuellement :<br /> </p> 
    <ul> 
     <li>Indicateur rouge pour les agents bloqués</li> 
     <li>une balise grise pour les agents en pause</li> 
    </ul> </td> 
   <td>Page de réplication</td> 
  </tr> 
  <tr> 
   <td>Workflows</td> 
   <td> 
    <ul> 
     <li>Tâches de workflow : 
      <ul> 
       <li>nombre de tâches de workflow ayant échoué (le cas échéant)</li> 
       <li>Nombre de tâches de workflow annulées (le cas échéant)</li> 
      </ul> </li> 
    </ul> 
    <ul> 
     <li>Nombre de workflows : nombre de workflows avec un statut donné (le cas échéant) : 
      <ul> 
       <li>running</li> 
       <li>échec</li> 
       <li>suspendu</li> 
       <li>aborted</li> 
      </ul> </li> 
    </ul> <p>Pour chacun des états présentés ci-dessus, une requête est exécutée, avec une limite de 400 millisecondes. À 400 millisecondes, le nombre d’entrées obtenues jusqu’à ce point s’affiche.</p> </td> 
   <td><p>Non interprété :</p> 
    <ul> 
     <li>l’utilisateur doit déterminer s’il existe des workflows et des traitements dont l’état est inattendu.</li> 
    </ul> </td> 
   <td>Page Échecs de workflow</td> 
  </tr> 
  <tr> 
   <td>Tâches Sling</td> 
   <td><p>Nombre de tâches Sling : nombre de tâches dans un état donné (le cas échéant) :</p> 
    <ul> 
     <li>échec</li> 
     <li>en file d'attente</li> 
     <li>annulé</li> 
     <li>En cours</li> 
    </ul> </td> 
   <td><p>Non interprété :</p> 
    <ul> 
     <li>l’utilisateur doit rechercher s’il existe des tâches dont les états sont inattendus ou dont le nombre est élevé.</li> 
    </ul> </td> 
   <td>S/O</td> 
  </tr> 
  <tr> 
   <td>Nombre de nœuds estimés</td> 
   <td><p>Nombre estimé de :</p> 
    <ul> 
     <li>pages</li> 
     <li>ressources</li> 
     <li>balises</li> 
     <li>authorizables</li> 
     <li>nombre total de noeuds<br /> </li> 
    </ul> <p>Le nombre total de nœuds est dérivé de nodeCounterMBean ; les autres statistiques proviennent d’IndexInfoService.</p> </td> 
   <td>S/O</td> 
   <td>S/O</td> 
  </tr> 
  <tr> 
   <td>Sauvegarde</td> 
   <td>Affiche "Sauvegarde en ligne en cours", le cas échéant.</td> 
   <td>S/O</td> 
   <td>S/O</td> 
  </tr> 
  <tr> 
   <td>Indexation</td> 
   <td><p>Affiche :</p> 
    <ul> 
     <li>"Indexation en cours"</li> 
     <li>"Requête en cours"</li> 
    </ul> <p>Si un thread d’indexation ou de requête est présent dans le thread dump.</p> </td> 
   <td>S/O</td> 
   <td>S/O</td> 
  </tr> 
 </tbody> 
</table>
