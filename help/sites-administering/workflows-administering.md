---
title: Administration d’instances de workflow
seo-title: Administering Workflow Instances
description: Découvrez comment administrer des instances de workflows.
seo-description: Lear how to administer Workflow Instances.
uuid: 81e53ef5-fe62-4ed4-b2d4-132aa986d5aa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: d9c96e7f-9416-48e1-a6af-47384f7bee92
exl-id: 70d4117b-5e49-46e4-a0b8-f56cf985536e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 94%

---

# Administration d’instances de workflow{#administering-workflow-instances}

La console de workflows fournit plusieurs outils permettant d’administrer les instances de workflow pour vérifier qu’elles s’exécutent comme prévu.

>[!NOTE]
>
>Le [Console JMX](/help/sites-administering/jmx-console.md#workflow-maintenance) fournit des opérations de maintenance de workflow supplémentaires.

Différentes consoles sont à votre disposition pour administrer les workflows. Utilisez la [navigation globale](/help/sites-authoring/basic-handling.md#global-navigation) pour ouvrir le panneau **Outils**, puis sélectionnez **Workflows** :

* **Modèles** : gérez les définitions de workflows.
* **Instances** : affichez et gérez l’exécution des instances de workflow.
* **Lanceurs** : gérez le lancement des workflows.
* **Archiver** : affichez l’historique des workflows correctement terminés.
* **Échecs** : affichez l’historique des workflows terminés avec des erreurs.

## Suivi du statut des instances de workflow {#monitoring-the-status-of-workflow-instances}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Instances** pour afficher la liste des instances de workflow en cours.

   ![wf-96](assets/wf-96.png)

1. Sélectionnez un élément spécifique, puis **Ouvrir l’historique** pour afficher plus de détails :

   ![wf-97](assets/wf-97.png)

## Suspension, reprise ou arrêt d’une instance de workflows {#suspending-resuming-and-terminating-a-workflow-instance}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Instances** pour afficher la liste des instances de workflow en cours.

   ![wf-96-1](assets/wf-96-1.png)

1. Sélectionnez un élément spécifique, puis utilisez **Arrêter**, **Suspendre** ou **Reprendre**, selon le cas. Une confirmation et/ou d’autres détails sont requis :

   ![wf-97-1](assets/wf-97-1.png)

## Affichage des workflows archivés {#viewing-archived-workflows}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Archiver** pour afficher la liste des instances de workflow qui se sont terminées avec succès.

   ![wf-98](assets/wf-98.png)

   >[!NOTE]
   >
   >Le statut d’abandon est considéré comme un arrêt réussi, car il se produit suite à une action de l’utilisateur. Par exemple :
   >
   >* Utilisation de l’action **Terminer**
   >* Lorsqu’une page, qui est soumise à un workflow, est supprimée (de force), le workflow est arrêté.


1. Sélectionnez un élément spécifique, puis **Ouvrir l’historique** pour afficher plus de détails :

   ![wf-99](assets/wf-99.png)

## Correction des échecs d’instance de workflows {#fixing-workflow-instance-failures}

Lorsqu’un workflow échoue, AEM fournit la console **Échecs** pour vous permettre d’enquêter et de prendre la mesure appropriée une fois la cause d’origine traitée :

* **Détails de l’échec**
Ouvre une fenêtre pour afficher le 
**Message d’échec**, l’**Étape** et la **Pile des échecs**.

* **Ouvrir l’historique**
Affiche des détails sur l’historique des workflows.

* **Relancer l’étape** Exécute à nouveau l’instance du composant d’étape de test. Utilisez la commande Relancer l’étape après avoir corrigé la cause de l’erreur d’origine. Par exemple, relancez l’étape après avoir corrigé un bogue dans le script que l’étape de processus exécute.
* **Arrêter** Arrêtez le workflow si l’erreur a provoqué une situation irréconciliable pour le workflow. Par exemple, le workflow peut se baser sur des conditions environnementales comme des informations figurant dans le référentiel qui ne sont plus valides pour l’instance de workflow.
* **Arrêter et réessayer** Similaire à **Arrêter**, à ceci près qu’une nouvelle instance de workflow est lancée à l’aide de la charge utile, du titre et de la description d’origine.

Pour examiner les échecs, puis reprendre ou arrêter le workflow par la suite, utilisez les étapes suivantes :

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Échecs** pour afficher la liste des instances de workflow qui ne se sont pas terminées avec succès.
1. Sélectionnez un élément spécifique, puis l’action appropriée :

   ![wf-47](assets/wf-47.png)

## Purge régulière des instances de workflow {#regular-purging-of-workflow-instances}

Réduire le nombre d’instances de workflow améliore les performances du moteur de workflows. Vous pouvez donc purger régulièrement les instances de workflow terminées ou en cours d’exécution du référentiel.

Configurez la **configuration de la purge du workflow Adobe Granite** pour purger les instances de workflow en fonction de leur âge et de leur statut. Vous pouvez également purger les instances de workflow de tous les modèles ou d’un modèle spécifique.

Vous pouvez également créer plusieurs configurations du service pour purger les instances de workflow qui répondent à différents critères. Par exemple, créez une configuration qui purge les instances d’un modèle de workflow particulier lorsqu’elles s’exécutent beaucoup plus longtemps que prévu. Créez une autre configuration qui purge tous les workflows terminés après un certain nombre de jours pour réduire la taille du référentiel.

Pour configurer le service, vous pouvez utiliser la [console Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ou [ajouter une configuration OSGi au référentiel](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository). Le tableau suivant décrit les propriétés dont vous avez besoin pour l’une ou l’autre de ces méthodes.

>[!NOTE]
>
>Pour ajouter la configuration au référentiel, le PID de service est :
>
>`com.adobe.granite.workflow.purge.Scheduler`
>
>Le service étant un service d’usine, le nom du nœud `sling:OsgiConfig` nécessite un suffixe d’identifiant, tel que :
>
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

<table> 
 <tbody> 
  <tr> 
   <th>Nom de propriété (console Web)</th> 
   <th>Nom de propriété OSGi</th> 
   <th>Description</th> 
  </tr> 
  <tr> 
   <td>Nom de la tâche</td> 
   <td>scheduledpurge.name</td> 
   <td>Nom explicite de la purge planifiée.</td> 
  </tr> 
  <tr> 
   <td>État du workflow</td> 
   <td>scheduledpurge.workflowStatus</td> 
   <td><p>Statut des instances de workflow à purger. Les valeurs suivantes sont valides :</p> 
    <ul> 
     <li>TERMINÉ : les instances de workflow terminées sont purgées.</li> 
     <li>EN COURS : les instances de workflow en cours d’exécution sont purgées.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Modèles à purger</td> 
   <td>scheduledpurge.modelIds</td> 
   <td><p>ID des modèles de workflows à purger. L’ID est le chemin d’accès au nœud de modèle, par exemple :<br /> /conf/global/settings/workflow/models/dam/update_asset/jcr:content/model<br /> Pour purger les instances de tous les modèles de workflows, ne spécifiez aucune valeur.</p> <p>Pour spécifier plusieurs modèles, cliquez sur le bouton + dans la console web. </p> </td> 
  </tr> 
  <tr> 
   <td>Âge de workflow</td> 
   <td>scheduledpurge.daysold</td> 
   <td>L’âge des instances de workflow à purger, exprimé en jours.</td> 
  </tr> 
 </tbody> 
</table>

## Définition de la taille maximale de la boîte de réception {#setting-the-maximum-size-of-the-inbox}

Vous pouvez définir la taille maximale de la boîte de réception en configurant la variable **Service de processus Adobe Granite**, à l’aide de la fonction [Console web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ou [ajouter une configuration OSGi au référentiel ;](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository). Le tableau suivant décrit la propriété que vous configurez pour l’une ou l’autre des méthodes.

>[!NOTE]
>
>Pour ajouter la configuration au référentiel, le PID de service est :
>
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Nom de propriété (console Web) | Nom de propriété OSGi |
|---|---|
| Taille de requête de boîte de réception maximale | granite.workflow.inboxQuerySize |
