---
title: Bonnes pratiques en matière de surveillance des ressources
description: Bonnes pratiques pour surveiller l’environnement et les performances de votre [!DNL Experience Manager] une fois déployée.
contentOwner: AG
feature: Asset Management
role: Admin,Architect
exl-id: edbb275a-5ead-4ed2-8708-29e766081d75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 26%

---

# Bonnes pratiques relatives à la surveillance des ressources {#assets-monitoring-best-practices}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Du point de vue d’Adobe Experience Manager Assets, la surveillance doit inclure l’observation et la création de rapports sur les processus et technologies suivants :

* Processeur système
* Utilisation de la mémoire système
* Temps d’attente d’E/S du disque système
* IO du réseau système
* MBeans JMX pour :

   * Utilisation du tas
   * Processus asynchrones, tels que les workflows

* Contrôles de l’intégrité de la console OSGi

Typiquement, la surveillance d’[!DNL Assets] peut être effectuée de deux façons : en temps réel ou sur le long terme.

## Surveillance en temps réel {#live-monitoring}

Vous devez effectuer une surveillance en direct pendant la phase de test des performances de votre développement ou lors de situations de charge élevée afin de comprendre les caractéristiques de performances de votre environnement. En règle générale, la surveillance en direct doit être effectuée à l’aide d’une suite d’outils. Voici quelques recommandations :

* [Visual VM](https://visualvm.github.io/) : Visual VM vous permet d’afficher des informations détaillées sur la machine virtuelle Java, et notamment l’utilisation du processeur et de la mémoire Java. En outre, il vous permet d’échantillonner et d’évaluer le code qui s’exécute sur une instance.
* [Haut](https://man7.org/linux/man-pages/man1/top.1.html): Top est une commande Linux qui ouvre un tableau de bord, qui affiche les statistiques d’utilisation, y compris l’utilisation du processeur, de la mémoire et des E/S. Il fournit un aperçu général de ce qui se passe sur une instance.
* [Htop](https://hisham.hm/htop/): Htop est une visionneuse de processus interactive. Il fournit une utilisation détaillée du processeur et de la mémoire en plus de ce que Top peut fournir. Htop peut être installé sur la plupart des systèmes Linux en utilisant `yum install htop` ou `apt-get install htop`.

* [Iotop](https://guichaz.free.fr/iotop/): Iotop est un tableau de bord détaillé de l’utilisation des E/S de disque. Il fournit des informations détaillées sur les processus qui utilisent les E/S sur les disques ainsi que le volume utilisé. Iotop peut être installé sur la plupart des systèmes Linux en utilisant `yum install iotop` ou `apt-get install iotop`.

* [Iftop](https://www.ex-parrot.com/pdw/iftop/): Iftop affiche des informations détaillées sur l’utilisation de l’Ethernet/du réseau. Iftop affiche les statistiques par canal de communication sur les entités utilisant Ethernet et la quantité de bande passante utilisée. Iftop peut être installé sur la plupart des systèmes Linux en utilisant `yum install iftop` ou `apt-get install iftop`.

* Java Flight Recorder (JFR) : JFR est un outil Oracle pouvant être utilisé gratuitement dans les environnements qui ne sont pas destinés à l’exploitation. Pour des informations détaillées, reportez-vous à la section relative à [l’utilisation de Java Flight Recorder pour diagnostiquer les problèmes d’exécution de CQ](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq).
* [!DNL Experience Manager] fichier error.log : Vous pouvez examiner la variable [!DNL Experience Manager] error.log pour plus d’informations sur les erreurs consignées dans le système. Utilisez la commande `tail -F quickstart/logs/error.log` pour identifier les erreurs que vous devez étudier.
* [Console d’administration des workflow](../sites-administering/workflows.md) : utilisez la console d’administration des workflow pour suivre les workflow en retard ou bloqués.

En règle générale, vous utilisez ces outils ensemble pour obtenir une idée complète des performances de votre [!DNL Experience Manager] instance.

>[!NOTE]
>
>Ces outils sont des outils standard qui ne sont pas directement pris en charge par Adobe. Elles ne nécessitent pas de licences supplémentaires.

![chlimage_1-142](assets/chlimage_1-142.png) ![chlimage_1-143](assets/chlimage_1-143.png)

## Surveillance à long terme {#long-term-monitoring}

Surveillance à long terme d’une [!DNL Experience Manager] l’instance implique une surveillance pendant une plus longue durée des mêmes parties que celles qui sont surveillées en direct. Elle comprend également la définition d’alertes spécifiques à votre environnement.

### Agrégation des logs et création de rapports {#log-aggregation-and-reporting}

Plusieurs outils sont disponibles pour agréger les journaux, par exemple Splunk(TM) et Elastic Search/Logstash/Kabana (ELK). Pour évaluer la disponibilité de votre [!DNL Experience Manager] il est important que vous compreniez les événements de journal spécifiques à votre système et que vous créiez des alertes en fonction de ces événements. Une bonne connaissance de votre développement et des pratiques opérationnelles peut vous aider à mieux comprendre comment adapter le processus d’agrégation des journaux pour générer des alertes critiques.

### Surveillance de l’environnement {#environment-monitoring}

La surveillance de l’environnement comprend la surveillance des éléments suivants :

* Débit réseau
* IO de disque
* Mémoire
* Utilisation du processeur
* MBeans JMX
* Sites externes

Vous avez besoin d’outils externes, tels que NewRelic(TM) et AppDynamics(TM), pour surveiller chaque élément. Grâce à ces outils, vous pouvez définir des alertes spécifiques à votre système, par exemple une utilisation élevée du système, une sauvegarde des workflows, des échecs de contrôle de l’intégrité ou un accès non authentifié à votre site web. Adobe ne recommande aucun outil particulier par rapport aux autres. Recherchez l’outil qui vous convient et utilisez-le pour surveiller les éléments abordés.

#### Surveillance des applications internes {#internal-application-monitoring}

La surveillance des applications internes consiste à surveiller les composants d’application qui constituent la pile [!DNL Experience Manager], notamment JVM et le référentiel de contenu. Elle inclut également la surveillance via le code d’application personnalisé intégré à la plateforme. En général, elle se fait via les MBeans JMX qui peuvent être contrôlés directement par de nombreuses et solutions de contrôle populaires telles que SolarWinds (TM), HP OpenView(TM), Hyperic(TM), Zabbix(TM) et bien d’autres encore. Pour les systèmes qui ne prennent pas en charge une connexion directe à JMX, vous pouvez écrire des scripts shell pour extraire les données JMX et les exposer à ces systèmes dans un format qu’ils comprennent nativement.

Par défaut, l’accès à distance aux JMX MBeans n’est pas activé. Pour plus d’informations sur la surveillance via JMX, reportez-vous à la section [Surveillance et gestion à l’aide de la technologie JMX](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html).

Dans de nombreux cas, une ligne de base est nécessaire pour contrôler efficacement une statistique. Pour créer une ligne de base, observez le système dans des conditions de travail normales pendant une période prédéterminée, puis identifiez la mesure normale.

**Surveillance JVM**

Comme toutes les piles d’application basées sur Java, [!DNL Experience Manager] dépend des ressources qui lui sont fournies via la machine virtuelle Java sous-jacente. Vous pouvez surveiller l’état de plusieurs de ces ressources via les MXBeans Platform qui sont exposés par JVM. Pour plus d’informations sur les MXBeans, voir [Utilisation du serveur MBean de plateforme et des MXBeans de plateforme](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

Voici quelques paramètres de référence que vous pouvez surveiller pour JVM :

Mémoire

* `MBean: lava.lang:type=Memory`
* URL : */system/console/jmx/java.lang:type=Memory*
* Instances : Tous les serveurs
* Seuil d&#39;alarme : Lorsque l’utilisation de la mémoire de tas ou non de tas dépasse 75 % de la mémoire maximale correspondante.
* Définition de l’alarme : Soit la mémoire système est insuffisante, soit il y a une fuite de mémoire dans le code. Analysez un vidage de thread pour obtenir une définition.

**Remarque**: Les informations fournies par ce bean sont exprimées en octets.

Threads

* MBean : `java.lang:type=Threading`
* URL : */system/console/jmx/java.lang:type=Thread*
* Instances : Tous les serveurs
* Seuil d&#39;alarme : Lorsque le nombre de threads est supérieur à 150 % de la ligne de base.
* Définition de l’alarme : Soit il y a un principal processus d&#39;exécution, soit une opération inefficace consomme une grande quantité de ressources. Analysez un vidage de thread pour obtenir une définition.

**[!DNL Experience Manager]monitoring**

[!DNL Experience Manager] présente également un ensemble de statistiques et d’opérations via JMX. Elles peuvent vous aider à évaluer l’état de santé du système et à identifier les éventuels problèmes avant qu’ils n’affectent les utilisateurs. Pour plus d’informations, reportez-vous à la [documentation](/help/sites-administering/jmx-console.md) sur les JMX MBeans d’[!DNL Experience Manager].

Voici quelques paramètres de référence que vous pouvez surveiller pour [!DNL Experience Manager] :

Agents de réplication

* MBean : `com.adobe.granite.replication:type=agent,id=”<AGENT_NAME>”`
* URL : */system/console/jmx/com.adobe.granite.replication:type=agent,id=&quot;&lt;agent_name>&quot;*
* Instances : un auteur et toutes les instances de publication (pour les agents de purge)
* Seuil d&#39;alarme : Lorsque la valeur de `QueueBlocked` est true ou la valeur de `QueueNumEntries` est supérieur à 150 % de la ligne de base.

* Définition de l’alarme : Présence d’une file d’attente bloquée dans le système indiquant que la cible de réplication est arrêtée ou inatteignable. Souvent, les problèmes de réseau ou d’infrastructure entraînent la mise en file d’attente d’entrées excessives, ce qui peut avoir un impact négatif sur les performances du système.

**Remarque**: Pour les paramètres MBean et URL, remplacez `<AGENT_NAME>` avec le nom de l’agent de réplication que vous souhaitez surveiller.

Décompte du nombre de sessions

* MBean : `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL : */system/console/jmx/org.apache.jackrabbit.oak:id=7,name=&quot;OakRepository Statistics&quot;,type*=&quot;RepositoryStats&quot;
* Instances : Tous les serveurs
* Seuil d&#39;alarme : Lorsque les sessions ouvertes dépassent la ligne de base de plus de 50 %.
* Définition de l’alarme : Les sessions peuvent être ouvertes par un morceau de code et ne jamais se fermer. Cela peut se produire lentement au fil du temps et finir par provoquer des fuites de mémoire dans le système. Le nombre de sessions doit fluctuer sur un système, mais il ne doit pas augmenter de manière continue.

Contrôles de l&#39;intégrité

Les contrôles d’intégrité disponibles dans la variable [tableau de bord des opérations](/help/sites-administering/operations-dashboard.md#health-reports) possèdent les MBeans JMX correspondants pour la surveillance. Cependant, vous pouvez écrire des contrôles d’intégrité personnalisés pour afficher des statistiques système supplémentaires.

Voici quelques contrôles d’intégrité prêts à l’emploi qui s’avèrent utiles à la surveillance :

* Contrôles système

   * MBean : `org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * URL : */system/console/jmx/org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck*
   * Instances : Un auteur, tous les serveurs de publication
   * Seuil d&#39;alarme : Lorsque l’état n’est pas OK
   * Définition de l’alarme : L’état de l’une des mesures est AVERTISSEMENT ou CRITIQUE. Vérifiez l’attribut de journal pour plus d’informations sur la cause du problème.

* File d’attente de réplication

   * MBean : `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * URL : */system/console/jmx/org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck*
   * Instances : Un auteur, tous les serveurs de publication
   * Seuil d&#39;alarme : Lorsque l’état n’est pas OK
   * Définition de l’alarme : L’état de l’une des mesures est AVERTISSEMENT ou CRITIQUE. Vérifiez l’attribut de journal pour plus d’informations sur la file d’attente qui a provoqué le problème.

* Performances des réponses

   * MBean : `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * URL : */system/console/jmx/org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck*
   * Instances : Tous les serveurs
   * Durée de l’alarme : Lorsque l’état n’est pas OK
   * Définition de l’alarme : L’état de l’une des mesures est AVERTISSEMENT ou CRITIQUE . Vérifiez l’attribut de journal pour plus d’informations sur la file d’attente qui a provoqué le problème.

* Performances des requêtes

   * MBean : `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck`
   * URL : */system/console/jmx/org.apache.sling.healthcheck:name= queryStatus,type=HealthCheck*
   * Instances : Un auteur, tous les serveurs de publication
   * Seuil d&#39;alarme : Lorsque l’état n’est pas OK
   * Définition de l’alarme : Une ou plusieurs requêtes s’exécutent lentement dans le système. Vérifiez l’attribut de journal pour plus d’informations sur les requêtes à l’origine du problème.

* Lots actifs

   * MBean : org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck
   * URL : */system/console/jmx/org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck*
   * Instances : Tous les serveurs
   * Seuil d&#39;alarme : Lorsque l’état n’est pas OK
   * Définition de l’alarme : Présence de lots OSGi inactifs ou non résolus sur le système. Vérifiez l’attribut de journal pour plus d’informations sur les lots à l’origine du problème.

* Erreurs de journal

   * MBean : `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * URL : */system/console/jmx/org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck*
   * Instances : Tous les serveurs
   * Seuil d&#39;alarme : Lorsque l’état n’est pas OK
   * Définition de l’alarme : Il existe des erreurs dans les fichiers journaux. Vérifiez l’attribut de journal pour plus d’informations sur la cause du problème.

## Problèmes courants et solutions  {#common-issues-and-resolutions}

Dans le processus de surveillance, si vous rencontrez des problèmes, voici quelques tâches de dépannage que vous pouvez effectuer pour résoudre des problèmes courants avec [!DNL Experience Manager] instances :

* Si vous utilisez TarMK, exécutez souvent la compression Tar. Pour plus d’informations, consultez la section [Maintenance du référentiel](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
* Vérifiez les journaux `OutOfMemoryError`. Pour plus d’informations, voir [Analyse des problèmes de mémoire](https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html).
* Recherchez dans les journaux des références à des requêtes non indexées, à des traversées d’arborescence ou à des traversées d’index. Elles indiquent des requêtes non indexées ou des requêtes incorrectement indexées. Pour connaître les bonnes pratiques relatives à l’optimisation des performances des requêtes et de l’indexation, voir [Bonnes pratiques relatives aux requêtes et à l’indexation](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* Utilisez la console de workflow pour vérifier que vos workflows fonctionnent comme prévu. Si possible, condensez plusieurs workflows en un seul workflow.
* Revoyez la surveillance en temps réel et recherchez toute congestion supplémentaire ou recherchez les processus fortement consommateurs de certaines ressources spécifiques.
* Examinez les points de sortie depuis le réseau client et les points d’entrée vers le [!DNL Experience Manager] réseau d’instances, y compris dispatcher. Il s&#39;agit souvent de zones de goulot d&#39;étranglement. Pour plus d’informations, voir [Considérations sur le réseau d’Assets](assets-network-considerations.md).
* Mettez à niveau votre [!DNL Experience Manager] serveur. Votre [!DNL Experience Manager] instance. L’assistance clientèle d’Adobe peut vous aider à déterminer si votre serveur est sous-dimensionné.
* Consultez les fichiers `access.log` et `error.log` pour trouver les entrées situées autour du moment où le problème est survenu. Recherchez des modèles susceptibles d’indiquer des anomalies de code personnalisé. Ajoutez-les à la liste des événements que vous surveillez.
