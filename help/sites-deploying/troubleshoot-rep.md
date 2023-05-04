---
title: Résolution des problèmes liés à la réplication
seo-title: Troubleshooting Replication
description: Cet article fournit des informations sur la manière de résoudre les problèmes de réplication.
seo-description: This article provides information on how to troubleshoot replication issues.
uuid: 7c3fdaad-0916-4159-a26c-17ff8c6617fe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: configuring
discoiquuid: e862c8a9-b5b6-4857-a154-03d3ffac3e67
feature: Configuring
exl-id: e83317bb-e69c-4e2c-92f8-4f613786e7ae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 24%

---

# Résolution des problèmes liés à la réplication{#troubleshooting-replication}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette page fournit des informations sur la manière de résoudre les problèmes de réplication.

## Problème {#problem}

La réplication (réplication non inverse) échoue pour une raison quelconque.

## Résolution {#resolution}

Il existe plusieurs raisons pour lesquelles la réplication échoue. Cet article explique l’approche que vous pouvez adopter lors de l’analyse de ces problèmes.

**Les réplications sont-elles déclenchées en cliquant sur le bouton d’activation ? Dans le cas contraire, procédez comme suit :**

1. Accédez à /crx/explorer (CQ5.5) et connectez-vous en tant qu&#39;administrateur.
1. Ouvrez &quot;Content Explorer&quot;.
1. Vérifiez si un noeud /bin/replicate ou /bin/replicate.json existe. Si le noeud existe, supprimez-le et enregistrez-le.

**Les réplications sont-elles mises en file d’attente dans les files d’attente de l’agent de réplication ?**

Vérifiez si c’est le cas en vous rendant sur /etc/replication/agents.author.html, puis cliquez sur les agents de réplication pour vérifier les éléments suivants.

**Si une ou plusieurs files d’attente sont bloquées :**

1. Le statut de la file d’attente est-t-il **blocked** ? Le cas échéant, l’instance de publication n’est-elle pas en cours d’éxécution ou a-t-elle cessé totalement de répondre ? Vérifiez l’instance de publication pour voir ce qui ne va pas avec elle (c’est-à-dire vérifiez les journaux et vérifiez s’il existe une erreur OutOfMemory ou un autre problème). Si c&#39;est généralement lent, prenez les images mémoire de threads et analysez-les.
1. Le statut de la file d’attente est-t-il **Queue is active - # pending** ? Fondamentalement, la tâche de réplication peut être bloquée dans une lecture de socket en attente de réponse de l’instance de publication ou du dispatcher. Cela peut signifier que l’instance de publication ou le dispatcher est en charge élevée ou coincé dans un verrou. Dans ce cas, prenez les thread dumps de l’auteur et de la publication.

   * Ouvrez les thread dumps de l’auteur dans un analyseur de thread dump , vérifiez s’il indique que la tâche sling eventing de l’agent de réplication est bloquée dans un socketRead.
   * Ouvrez les thread dumps de la publication dans un analyseur de thread dump, analysez ce qui peut empêcher l’instance de publication de répondre. Vous devez voir un thread dont le nom comporte : POST /bin/receive. Il s’agit du thread recevant la réplication de l’auteur.

**Si toutes les files d’attente de l’agent sont bloquées**

1. Il est possible qu’un certain élément du contenu ne puisse pas être sérialisé sous /var/replication/data à cause de la corruption du référentiel ou d’un autre problème. Vérifiez les journaux /error.log pour détecter une erreur correspondante. Pour supprimer un élément de réplication défectueux, procédez comme suit :

   1. Accédez à https://&lt;host>:&lt;port>/crx et connectez-vous en tant qu’utilisateur administrateur. Dans CQ5.5, accédez à https://&lt;host>:&lt;port>/crx/explorer à la place.
   1. Cliquez sur &quot;Explorateur de contenu&quot;.
   1. Dans la fenêtre &quot;Explorateur de contenu&quot;, cliquez sur le bouton de loupe en haut à droite de la fenêtre et une boîte de dialogue de recherche s’affiche.
   1. Sélectionnez le bouton radio &quot;XPath&quot;.
   1. Dans la zone &quot;Requête&quot;, saisissez cette requête /jcr:root/var/eventing/jobs//element(&amp;ast;,slingevent:Job) de @slingevent:created
   1. Cliquez sur &quot;Rechercher&quot;.
   1. Dans les résultats, les principaux éléments sont les dernières tâches Sling eventing. Cliquez sur chacune d’elles et recherchez les réplications bloquées qui correspondent à ce qui apparaît en haut de la file d’attente.

1. Il se peut qu’il y ait un problème avec les files d’attente de tâche de structure sling eventing. Essayez de redémarrer le lot org.apache.sling.event dans le répertoire /system/console.
1. Il se peut que le traitement des tâches soit complètement désactivé. Vous pouvez vérifier cela sous la console Felix dans l’onglet Sling Eventing. Vérifiez s’il s’affiche - Événement Apache Sling (LE TRAITEMENT DES TÂCHES EST DÉSACTIVÉ).

   * Si oui, cochez Apache Sling Job Event Handler sous l’onglet Configuration dans la console Felix. Il se peut que la case &quot;Traitement des tâches activé&quot; ne soit pas cochée. Si cette option est cochée et qu’elle affiche toujours que &quot;le traitement des tâches est désactivé&quot;, vérifiez s’il existe un recouvrement sous /apps/system/config qui désactive le traitement des tâches. Essayez de créer un noeud osgi:config pour jobmanager.enabled avec une valeur booléenne égale à true et vérifiez à nouveau si l’activation a commencé et qu’il n’y a plus de tâches dans la file d’attente.

1. Il se peut également que la configuration DefaultJobManager se trouve dans un état incohérent. Cela peut se produire lorsqu’une personne modifie manuellement la configuration &quot;Apache Sling Job Event Handler&quot; via la console OSGiconsole (par exemple, désactivez et réactivez la propriété &quot;Job Processing Enabled&quot; et enregistrez la configuration).

   * À ce stade, la configuration DefaultJobManager stockée à l’adresse crx-quickstart/launchpad/config/org/apache/sling/event/impl/jobs/DefaultJobManager.config se trouve dans un état incohérent. Et même si la propriété &quot;Apache Sling Job Event Handler&quot; indique que l’état &quot;Job Processing Enabled&quot; est coché, lorsque l’on accède à l’onglet Sling Eventing, le message - JOB PROCESSING IS DISABLED (TRAITEMENT DES TÂCHES EST DÉSACTIVÉ) s’affiche et la réplication ne fonctionne pas.
   * Pour résoudre ce problème, il faut se rendre sur la page de configuration de la console OSGi et supprimer la configuration « Gestionnaire d’événements de tâche Apache Sling ». Redémarrez ensuite le noeud de Principal de la grappe afin de rétablir la configuration dans un état cohérent. Cela devrait résoudre le problème et la réplication recommence à fonctionner.

**Création d’un fichier replication.log**

Il peut parfois s’avérer très utile de définir toutes les journaux de réplication à ajouter dans un fichier journal distinct au niveau DEBUG. Pour ce faire :

1. Accédez à `https://host:port/system/console/configMgr` et connectez-vous en tant qu’administrateur.
1. Identifiez la fabrique Enregistreur de connexion Sling Apache et créez une instance en cliquant sur le bouton **+** à droite de la configuration de la fabrique. Cela créera un nouveau journal de journalisation.
1. Définissez la configuration comme suit :

   * Niveau de connexion : DÉBOGUER
   * Chemin du fichier journal : *(CQ5.4 et 5.3)* ../logs/replication.log *(CQ5.5)* logs/replication.log
   * Catégories : com.day.cq.replication

1. Si vous pensez que le problème est lié de quelque manière que ce soit à sling eventing/jobs, vous pouvez également ajouter ce package java sous categories:org.apache.sling.event.

### Suspension de la file d’attente de l’agent de réplication  {#pausing-replication-agent-queue}

Parfois, il peut être judicieux de suspendre la file d’attente de réplication afin de réduire la charge sur le système de création, sans la désactiver. Actuellement, cela n’est possible que par une erreur de configuration temporaire d’un port non valide. À partir de la version 5.4, vous pouvez voir un bouton de pause dans la file d’attente de l’agent de réplication, qui présente certaines limites.

1. L’état n’est pas conservé, ce qui signifie que si vous redémarrez un serveur ou que le lot de réplication est recyclé, il revient à l’état en cours d’exécution.
1. La pause est inactive pendant une période plus courte (OOB 1 heure après aucune activité avec réplication par d’autres threads) et non pendant une période plus longue. Parce qu’il existe une fonctionnalité dans sling qui évite les threads inactifs. Vérifiez essentiellement si un thread de file d’attente de tâches a été inutilisé pendant une plus longue période, le cas échéant, il déclenche les cycles de nettoyage. En raison du cycle de nettoyage, le thread est arrêté et le paramètre en pause est donc perdu. Comme les tâches sont conservées, il lance un nouveau thread pour traiter la file d’attente qui ne contient pas les détails de la configuration suspendue. En raison de cette file d’attente, l’état d’exécution se transforme.

### Les autorisations de page ne sont pas répliquées lors de l’activation de l’utilisateur {#page-permissions-are-not-replicated-on-user-activation}

Les autorisations de page ne sont pas répliquées car elles sont stockées sous les nœuds auxquels l’accès est accordé, pas avec l’utilisateur.

En règle générale, les autorisations de page ne doivent pas être répliquées de l’auteur vers la publication et ne le sont pas par défaut. En effet, les droits d’accès doivent être différents dans ces deux environnements. Par conséquent, il est recommandé de configurer les listes de contrôle d’accès lors de la publication séparément de l’auteur.

### File d’attente de réplication bloquée lors de la réplication des informations d’espace de noms de l’auteur à la publication {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

Dans certains cas, la file d’attente de réplication est bloquée lors de la tentative de réplication des informations sur les espaces de noms depuis l’instance d’auteur vers l’instance de publication. Ce problème se produit car l’utilisateur de la réplication ne dispose pas du privilège `jcr:namespaceManagement`. Pour éviter ce problème, vérifiez les points suivants :

* L’utilisateur de la réplication (tel que configuré sous l’onglet [Transfert](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) > Utilisateur) existe également sur l’instance de publication.
* L’utilisateur dispose des privilèges de lecture et d’écriture sur le chemin où le contenu est installé.
* L’utilisateur possède le privilège `jcr:namespaceManagement` au niveau du référentiel. Vous pouvez accorder le privilège comme suit :

1. Connectez-vous à CRX/DE (`http://localhost:4502/crx/de/index.jsp`) en tant qu’administrateur.
1. Cliquez sur le bouton **Contrôle d’accès** .
1. Sélectionner **Référentiel**.
1. Cliquez sur **Ajouter une entrée** (icône plus).
1. Saisissez le nom de l’utilisateur.
1. Sélectionnez `jcr:namespaceManagement` dans la liste des privilèges.
1. Cliquez sur OK.
