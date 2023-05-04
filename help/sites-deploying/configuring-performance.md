---
title: Optimiser les performances
seo-title: Performance Optimization
description: Découvrez comment configurer certains aspects d’AEM pour optimiser les performances.
seo-description: Learn how to configure certain aspects of AEM to optimize performance.
uuid: a4d9fde4-a4c7-4ee5-99b6-29b0ee7dc35b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: configuring
discoiquuid: 80118cd1-73e1-4675-bbdf-85d66d150abc
feature: Configuring
exl-id: 06b197de-f97b-451f-8037-931c8cd754b6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '6685'
ht-degree: 47%

---

# Optimiser les performances {#performance-optimization}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Pour obtenir des instructions générales sur les performances, consultez la section [Instructions de performance](/help/sites-deploying/performance-guidelines.md) page.
>
>Pour plus d’informations sur le dépannage et la résolution des problèmes de performances, voir également la section [Arborescence de performances](/help/sites-deploying/performance-tree.md).
>
>De plus, vous pouvez lire un article de la base de connaissances pour obtenir des [Conseils pour le réglage des performances.](https://helpx.adobe.com/fr/experience-manager/kb/performance-tuning-tips.html)

L’un des problèmes majeurs est le temps que met votre site web pour répondre aux requêtes des visiteurs. Bien que cette valeur varie pour chaque requête, une valeur cible moyenne peut être définie. Une fois que cette valeur s’est avérée à la fois réalisable et gérable, elle peut être utilisée pour surveiller les performances du site web et indiquer le développement de problèmes potentiels.

Les temps de réponse que vous viserez seront différents dans les environnements de création et de publication, reflétant les différentes caractéristiques de l’audience cible :

## Environnement de création {#author-environment}

Cet environnement est utilisé par les auteurs qui saisissent et mettent à jour du contenu. Il doit prendre en charge un petit nombre d’utilisateurs qui génèrent chacun un nombre élevé de requêtes gourmandes en performances lors de la mise à jour des pages de contenu et des éléments individuels sur ces pages.

## Environnement de publication {#publish-environment}

Cet environnement intègre le contenu que vous mettez à la disposition de vos utilisateurs. Ici, le nombre de demandes est un facteur encore plus important et la vitesse est tout aussi cruciale. Toutefois, dans la mesure où la nature des demandes est moins dynamique, des mécanismes supplémentaires d’amélioration des performances peuvent être appliqués, par exemple, la mise en cache du contenu ou l’équilibrage de charge.

>[!NOTE]
>
>* Une fois l’optimisation des performances configurée, suivez les procédures dans [Tough Day](/help/sites-developing/tough-day.md) pour tester l’environnement en le soumettant à une charge importante.
>* Consultez également la section [Conseils pour le réglage des performances.](https://helpx.adobe.com/fr/experience-manager/kb/performance-tuning-tips.html)


## Méthodologie d’optimisation des performances {#performance-optimization-methodology}

Une méthodologie d’optimisation des performances pour les projets AEM peut se résumer en cinq règles très simples qu’il convient de respecter pour éviter des problèmes de performance dès le départ :

1. [Planification de l’optimisation](#planning-for-optimization)
1. [Simulation de la réalité](#simulate-reality)
1. [Établissement d’objectifs solides](#establish-solid-goals)
1. [Maintien de la pertinence](#stay-relevant)
1. [Cycles d’itération agile](#agile-iteration-cycles)

Dans une large mesure, ces règles s’appliquent aux projets Web en général et sont pertinentes pour les chefs de projet et les administrateurs système car elles leur permettent d’éviter des problèmes de performances au moment du lancement de leurs projets.

### Planification de l’optimisation {#planning-for-optimization}

![chlimage_1-3](assets/chlimage_1-3.jpeg)

Environ 10 % des efforts liés à un projet doivent être planifiés en vue de la phase d’optimisation des performances. Bien sûr, les exigences d’optimisation des performances réelles dépendent du niveau de complexité d’un projet et de l’expérience de l’équipe de développement. Bien que votre projet puisse (finalement) ne pas nécessiter tout le temps alloué, il est recommandé de toujours planifier l’optimisation des performances dans la région suggérée.

Dans la mesure du possible, un projet doit d’abord être lancé en douceur pour une audience limitée afin de collecter des données d’expérience réelle et d’effectuer d’autres activités d’optimisation, sans la pression supplémentaire qui suit une annonce de lancement définitif.

Une fois que vous êtes &quot;actif&quot;, l’optimisation des performances n’est pas terminée. C’est le moment où vous faites face à la réelle charge que subit votre système. Il est important de prévoir des ajustements supplémentaires après le lancement.

Comme la charge de votre système change et que les profils de performances de votre système changent au fil du temps, une &quot;mise au point&quot; ou un &quot;contrôle de l’intégrité&quot; des performances doivent être planifiés à 6-12 mois d’intervalles.

### Simulation de la réalité {#simulate-reality}

![chlimage_1-4](assets/chlimage_1-4.jpeg)

Si vous avez mis en ligne un site Web et que vous identifiez, après le lancement, des problèmes de performances, une seule raison peut les expliquer : vos tests de charge et de performance n’ont pas simulé la réalité le plus fidèlement possible.

La simulation de la réalité est difficile et les efforts que vous êtes prêt à raisonnablement concéder pour vous approcher de la réalité dépendent de la nature de votre projet. Cette réalité signifie non seulement un « code réel » et un « trafic réel », mais aussi du « contenu réel », en particulier en ce qui concerne la taille et la structure. Gardez à l’esprit que vos modèles peuvent se comporter différemment selon la taille et la structure du référentiel.

### Établir des objectifs solides {#establish-solid-goals}

![chlimage_1-5](assets/chlimage_1-5.jpeg)

L’importance d’établir correctement les objectifs de performances ne doit pas être sous-estimée. Souvent, une fois que les équipes se concentrent sur des objectifs de performances précis, il est très difficile de faire marche arrière, même si ces objectifs sont basés sur des hypothèses imprudentes.

L’établissement d’objectifs de performances réalisables et viables est vraiment l’un des aspects les plus délicats. Il est souvent préférable de collecter les données réelles et les références d&#39;un site Web comparable (par exemple le prédécesseur du nouveau site Web).

### Maintenir la pertinence {#stay-relevant}

![chlimage_1-6](assets/chlimage_1-6.jpeg)

Il est important de résoudre un seul goulot d’étranglement à la fois. Si vous essayez de faire des choses en parallèle sans valider l’impact de l’optimisation unique, vous perdrez la trace de la mesure d’optimisation qui a réellement contribué à l’optimisation.

### Cycles d’itération agile {#agile-iteration-cycles}

![chlimage_1-7](assets/chlimage_1-7.jpeg)

L’optimisation des performances est un processus itératif qui implique des activités de mesure, d’analyse, d’optimisation et de validation jusqu’à ce que l’objectif soit atteint. Afin d’aborder correctement cet aspect, implémentez un processus de validation agile dans la phase d’optimisation plutôt qu’un processus de tests contraignant après chaque itération.

Cela signifie principalement que le développeur qui met en oeuvre l’optimisation doit disposer d’un moyen rapide de déterminer si l’optimisation a déjà atteint l’objectif. Il s’agit d’informations précieuses, car une fois l’objectif atteint, l’optimisation est terminée.

## Consignes de performances de base {#basic-performance-guidelines}

De manière générale, vos demandes html non mises en cache doivent être inférieures à 100 ms. Plus précisément, ce qui suit peut servir de ligne directrice :

* 70 % des demandes de pages doivent être traitées en moins de 100 ms.
* 25 % des demandes de pages doivent recevoir une réponse dans un délai de 100 à 300 ms.
* 4 % des demandes de pages doivent recevoir une réponse dans un délai de 300 à 500 ms.
* 1 % des demandes de pages doivent recevoir une réponse dans un délai de 500 à 1000 ms.
* Aucune page ne doit répondre plus d’une seconde.

Les chiffres ci-dessus supposent les conditions suivantes :

* Mesure prise au moment de la publication (sans surcharge liée à un environnement de création)
* Mesure prise sur le serveur (pas de surcharge réseau)
* Pas de mise en cache (pas de cache de sortie AEM, pas de cache du Dispatcher)
* Uniquement pour les éléments complexes présentant de nombreuses dépendances (HTML, JS, PDF...)
* Pas d’autre charge sur le système

Un certain nombre de problèmes contribuent fréquemment aux problèmes de performances. Elles se concentrent principalement sur :

* L’inefficacité de la mise en cache par le Dispatcher
* L’utilisation de requêtes dans des modèles d’affichage normaux

Le réglage au niveau de la JVM et du système d’exploitation n’entraîne généralement pas de grands bond en avant en termes de performances et doit donc être effectué à la toute fin du cycle d’optimisation.

La structure d’un référentiel de contenu peut également avoir un impact sur les performances. Pour de meilleures performances, le nombre de noeuds enfants associés à des noeuds individuels dans un référentiel de contenu ne doit pas dépasser 1 000 (en règle générale).

Vos meilleurs amis lors d’un exercice habituel d’optimisation des performances sont les suivants :

* la valeur `request.log`
* minutage basé sur les composants
* dernier mais pas le moindre profileur java.

### Performances lors du chargement et de la modification des ressources numériques {#performance-when-loading-and-editing-digital-assets}

En raison du volume important de données impliquées lors du chargement et de la modification des ressources numériques, les performances peuvent devenir un problème.

Deux éléments affectent les performances ici :

* Processeur : plusieurs cœurs permettent un travail plus fluide lors du transcodage
* Disque dur : les disques RAID parallèles obtiennent le même résultat

Pour améliorer les performances, tenez compte des points suivants :

* Combien d’éléments seront téléchargés par jour ? Une bonne estimation peut être basée sur :

![chlimage_1-77](assets/chlimage_1-77.png)

* le délai durant lequel les modifications sont effectuées (généralement une journée de travail, davantage pour les opérations internationales) ;
* la taille moyenne des images chargées (et la taille des rendus générés par image) en mégaoctets.
* Déterminez le débit de données moyen :

![chlimage_1-78](assets/chlimage_1-78.png)

* 80 % de toutes les modifications seront effectuées dans 20 % des cas, donc en période de trafic élevé, attendez-vous à un débit moyen quadruplé. C&#39;est votre objectif de performance.

## Surveillance des performances {#performance-monitoring}

Les performances (ou leur insuffisance) sont l’une des premières choses que vos utilisateurs remarquent. Aussi, pour toute application dotée d’une interface utilisateur, les performances sont un facteur déterminant. Pour optimiser les performances de votre installation AEM, vous devez surveiller les différents attributs de l’instance et son comportement.

Pour plus d’informations sur l’exécution de la surveillance des performances, consultez [Surveillance des performances](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance).

Les problèmes qui causent des problèmes de performances sont souvent difficiles à détecter, même lorsque leurs effets sont faciles à voir.

Un point de départ de base est une bonne connaissance de votre système lorsqu’il fonctionne normalement. À moins que vous ne sachiez à quoi votre environnement &quot;ressemble&quot; et &quot;se comporte&quot; lorsqu’il se comporte correctement, il peut être difficile de localiser le problème lorsque les performances se détériorent. Cela signifie que vous devriez passer un certain temps à enquêter sur votre système lorsqu’il s’exécute correctement et à vous assurer que la collecte des informations de performance est une tâche en cours. Vous disposerez ainsi d’une base de comparaison en cas de dégradation des performances.

Le diagramme suivant illustre le parcours que peut suivre une demande de contenu AEM, et donc le nombre d’éléments différents pouvant se répercuter sur les performances.

![chlimage_1-79](assets/chlimage_1-79.png)

Les performances sont également un compromis entre volume et capacité :

**Volume** La quantité de sortie qui est traitée et diffusée par le système.

**Capacité** Capacité du système à fournir le volume.

Cet aspect est présent à différents endroits de la chaîne Web.

![chlimage_1-80](assets/chlimage_1-80.png)

Plusieurs domaines fonctionnels sont souvent responsables de l’impact sur les performances :

* Mise en cache
* Code de l’application (votre projet)
* Fonctionnalité de recherche

### Règles de base concernant les performances {#basic-rules-regarding-performance}

Certaines règles doivent être prises en compte lors de l’optimisation des performances :

* Optimisation des performances *must* faire partie de chaque projet.
* Ne pas optimiser tôt dans le cycle de développement.
* Les performances ne sont que égales à celles du lien le plus faible.
* Pensez toujours à la capacité par rapport au volume.
* Optimisez d’abord les éléments importants.
* Ne jamais optimiser sans *réaliste* objectifs.

>[!NOTE]
>
>Gardez à l’esprit que le mécanisme que vous utilisez pour mesurer les performances affecte souvent exactement ce que vous essayez de mesurer. Vous devez toujours tenir compte de ces écarts et éliminer le plus possible leurs effets. dans la mesure du possible, les modules externes du navigateur doivent en particulier être désactivés.

## Configurer pour optimiser la performance {#configuring-for-performance}

Certains aspects d’AEM (et/ou du référentiel sous-jacent) peuvent être configurés pour optimiser la performance. Vous trouverez ci-dessous des possibilités et des suggestions. Vous devez vous assurer d’utiliser la fonctionnalité en question avant d’apporter des modifications.

>[!NOTE]
>
>Pour plus d’informations, veuillez lire [l’article de la base de connaissances](https://helpx.adobe.com/fr/experience-manager/kb/performance-tuning-tips.html).

### Indexation de recherche {#search-indexing}

À compter d’AEM 6.0, Adobe Experience Manager utilise une architecture de référentiel Oak.

Vous trouverez les informations d’indexation mises à jour ici :

* [Bonnes pratiques relatives aux requêtes et à l’indexation](/help/sites-deploying/best-practices-for-queries-and-indexing.md)
* [Requêtes et indexation](/help/sites-deploying/queries-and-indexing.md)

### Traitement de workflows simultanés {#concurrent-workflow-processing}

Limitez le nombre de workflow en cours d’exécution pour améliorer les performances. Par défaut, le moteur de workflow traite autant de workflow en parallèle qu’il y a de processeurs disponibles pour la machine virtuelle Java. Lorsque les étapes du workflow nécessitent d’importantes quantités de ressources de traitement (mémoire vive ou processeur), l’exécution simultanée de plusieurs de ces workflow peut intensifier la demande en ressources serveur disponibles.

Par exemple, lorsque des images (ou des ressources de gestion des actifs numériques en général) sont chargées, les workflows importent automatiquement les images dans la gestion des actifs numériques (DAM). Les images sont souvent à haute résolution et peuvent facilement consommer des centaines de Mo de tas pour le traitement. La gestion de ces images en parallèle place une charge élevée sur le sous-système de mémoire et le garbage collector.

Le moteur de workflow utilise les files d’attente de tâche Apache Sling pour gérer et planifier le traitement des éléments de travail. Les services de file d’attente de tâches suivants ont été créés par défaut à partir de la fabrique de services Configuration des files d’attente des tâches Apache Sling pour le traitement des tâches de workflow :

* File d’attente des workflows Granite : la plupart des étapes de workflow, telles que celles qui traitent les ressources de gestion des ressources numériques, utilisent le service File d’attente des workflows Granite.
* File d’attente des tâches de processus externe des workflows Granite : ce service est utilisé pour les étapes de workflow spéciales et externes qui servent généralement à contacter un système externe et à interroger les résultats. Par exemple, l’étape InDesign : Processus d’extraction de médias est implémentée en tant que processus externe. Le moteur de workflow utilise la file d’attente externe pour traiter l’interrogation. (Voir [com.day.cq.workflow.exec.WorkflowExternalProcess](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/WorkflowExternalProcess.html).)

Configurez ces services pour limiter le nombre maximal de workflows en cours d’exécution.

**Remarque :** La configuration de ces files d’attente de tâches affecte tous les workflows, sauf si vous avez créé une file d’attente de tâches pour un modèle de workflow spécifique (voir [Configuration de la file d’attente pour un modèle de processus spécifique](/help/sites-deploying/configuring-performance.md#configure-the-queue-for-a-specific-workflow) ci-dessous).

#### Configuration dans le référentiel {#configuration-in-the-repo}

Si vous configurez les services [à l’aide d’un nœud sling:OsgiConfig](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository), vous devez trouver le PID des services existants, par exemple : org.apache.sling.event.jobs.QueueConfiguration.370aad73-d01b -4a0b-abe4-20198d85f705. Vous pouvez détecter le PID à l’aide de la console Web.

Vous devez configurer la propriété nommée `queue.maxparallel`.

#### Configuration dans la console Web {#configuration-in-the-web-console}

Pour configurer ces services [à l’aide de la console Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console), localisez les éléments de configuration existants sous la fabrique de services Configuration de la file d’attente de tâches Apache Sling.

Vous devez configurer la propriété nommée Nombre maximal de tâches en parallèle.

### Configurer la file d’attente pour un workflow spécifique {#configure-the-queue-for-a-specific-workflow}

Créez une file d’attente de tâche pour un modèle de workflow spécifique afin de pouvoir configurer la gestion des tâches pour ce modèle de workflow. Ainsi, vos configurations affectent le traitement d’un workflow spécifique, tandis que la configuration de la file d’attente de workflow Granite par défaut contrôle le traitement d’autres workflows.

Lorsque les modèles de workflow s’exécutent, ils créent des tâches Sling pour une rubrique spécifique. Par défaut, la rubrique correspond aux rubriques configurées pour la file d’attente de workflows Granite générale ou la file d’attente de tâches de processus externe de workflows Granite :

* `com/adobe/granite/workflow/job*`
* `com/adobe/granite/workflow/external/job*`

Les rubriques de tâche réelles générées par les modèles de workflow incluent le suffixe spécifique au modèle. Par exemple, le modèle du workflow Ressource de mise à jour de la gestion des ressources numériques génère des tâches avec la rubrique suivante :

`com/adobe/granite/workflow/job/etc/workflow/models/dam/update_asset/jcr_content/model`

Par conséquent, vous pouvez créer une file d’attente de tâches pour la rubrique correspondant aux rubriques de votre modèle de workflow. La configuration des propriétés liées aux performances de la file d’attente affecte uniquement le modèle de workflow qui génère les tâches correspondant à la rubrique de la file d’attente.

La procédure suivante crée une file d’attente de tâches pour un workflow, en utilisant le workflow Ressource de mise à jour de la gestion des ressources numériques pour exemple.

1. Exécutez le modèle de workflow pour lequel vous souhaitez créer la file d’attente de tâches et générer des statistiques de rubrique. Par exemple, ajoutez une image aux Ressources pour exécuter le workflow Ressource de mise à jour de la gestion des ressources numériques.
1. Ouvrez la console Tâches Sling. (`https://<host>:<port>/system/console/slingevent`)
1. Découvrez les rubriques relatives aux workflows dans la console. Pour les ressources de mise à jour de gestion des actifs numériques, les rubriques suivantes sont disponibles :

   * `com/adobe/granite/workflow/external/job/etc/workflow/models/dam/update_asset/jcr_content/model`
   * `com/adobe/granite/workflow/job/etc/workflow/models/dam/update_asset/jcr_content/model`
   * `com/adobe/granite/workflow/job/etc/workflow/models/dam-xmp-writeback/jcr_content/model`

1. Créez une file d’attente pour chacune de ces rubriques. Pour créer une file d’attente de tâches, créez une configuration d’usine pour le service d’usine File d’attente de tâches Apache Sling.

   Les configurations de fabrique sont similaires à la file d’attente des workflows Granite décrite dans [Traitement de workflows simultanés](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing), à la différence que la propriété Rubriques correspond à la rubrique de vos tâches de workflow.

### Service AEM de synchronisation des ressources de gestion des ressources numériques {#cq-dam-asset-synchronization-service}

Le service `AssetSynchronizationService` permet de synchroniser les ressources des référentiels montés (y compris LiveLink et Documentum, entre autres). Par défaut, il effectue une vérification régulière toutes les 300 secondes (5 minutes), donc si vous n’utilisez pas de référentiels montés, vous pouvez désactiver ce service.

Vous pouvez le faire en [configurant le service OSGi](/help/sites-deploying/configuring-osgi.md) **Service de synchronisation des ressources de gestion des ressources numériques CQ** de façon à définir la **période de synchronisation** (`scheduler.period`) sur (au minimum) 1 an (spécifiée en secondes).

### Instances multiples de gestion des ressources numériques {#multiple-dam-instances}

Le déploiement de plusieurs instances de gestion des ressources numériques peut améliorer les performances si, par exemple :

* votre charge est élevée en raison du chargement régulier d’un grand nombre de ressources pour l’environnement de création. Dans ce cas, une instance distincte de gestion des ressources numériques peut être dédiée à la création.
* plusieurs de vos équipes sont basées à l’étranger (par exemple, aux États-Unis, en Europe, en Asie).

Autres points à prendre en compte :

* Séparer le « travail en cours » en mode de création du « final » en mode de publication
* Séparer les utilisateurs internes en mode de création des visiteurs/utilisateurs externes en mode de publication (par exemple les agents, la presse, les représentants, les clients, les étudiants, etc.)

## Bonnes pratiques pour l’assurance qualité {#best-practices-for-quality-assurance}

Les performances sont primordiales pour votre environnement de publication. Par conséquent, vous devez soigneusement planifier et analyser les tests de performance que vous allez effectuer pour l’environnement de publication lors de la mise en oeuvre de votre projet.

Cette section vise à donner un aperçu normalisé des problèmes liés à la définition d’un concept de test spécifique pour les tests de performances dans votre environnement de *publication*. Elle s’adresse principalement aux ingénieurs en assurance qualité, aux chefs de projet et aux administrateurs système.

Le contenu suivant présente une approche normalisée des tests de performance pour une application CQ sur l’environnement de *publication*. Cela implique les 5 phases suivantes :

* [Vérification des connaissances](#verification-of-knowledge)
* [Définition de la portée](#scope-definition)
* [Méthodologies de test](#test-methodologies)
* [Définition des objectifs de performances](#defining-the-performance-goals)
* [Optimisation](#optimization)

Le contrôle est un processus supplémentaire qui englobe tous les aspects, nécessaire mais non limité aux tests.

### Vérification des connaissances {#verification-of-knowledge}

Une première étape consiste à documenter les informations de base que vous devez connaître avant de commencer le test :

* l’architecture de votre environnement de test ;
* une carte de l’application détaillant les éléments internes qui nécessiteront des tests (à la fois de manière isolée et combinée).

#### Architecture de test {#test-architecture}

Vous devez documenter clairement l’architecture de l’environnement de test utilisé pour vos tests de performances.

Vous aurez besoin d’une reproduction de votre environnement de publication de production prévu, avec Dispatcher et l’équilibreur de charge.

#### Carte d’applications {#application-map}

Pour obtenir un aperçu clair, vous pouvez créer un mappage de l’ensemble de l’application (il se peut que vous ayez obtenu ce mappage à partir de tests dans l’environnement de création).

Un diagramme représentant les éléments internes de l’application peut donner un aperçu des exigences de test ; avec le codage par couleur, il peut également servir de base pour la création de rapports.

### Définition de la portée {#scope-definition}

Une application comporte généralement une sélection de cas d’utilisation. Certains seront très importants, d&#39;autres moins.

Pour concentrer l’étendue des tests de performance sur la publication, nous vous recommandons de définir les éléments suivants :

* Les cas d’utilisation commerciale les plus importants
* Les cas d’utilisation technique les plus critiques

Le nombre de cas d’utilisation dépend de vous, mais il doit être limité à un nombre facilement gérable (entre 5 et 10, par exemple).

Une fois les cas d’utilisation clés sélectionnés, les indicateurs de performance clés et les outils utilisés pour les mesurer peuvent être définis pour chaque cas. Voici quelques exemples d’indicateurs clés de performance courants :

* Temps de réponse de bout en bout
* Temps de réponse du servlet
* Temps de réponse pour un seul composant
* Temps de réponse des services
* Nombre de threads inactifs dans le pool de threads
* Nombre de connexions libres
* Ressources système telles que l’accès au processeur et aux E/S

### Méthodologies de test {#test-methodologies}

Ce concept comporte quatre scénarios utilisés pour définir et tester les objectifs de performances :

* Tests sur un composant unique
* Tests sur les composants combinés
* *En ligne* scenario
* Scénarios d’erreur

Sur la base des principes suivants.

#### Points d’arrêt des composants {#component-breakpoints}

* Chaque composant possède un point d’arrêt spécifique lorsqu’il est lié aux performances. Cela signifie qu’un composant sera performant jusqu’à ce qu’un seuil soit atteint, après quoi les performances se dégraderont rapidement.
* Pour obtenir une vue d’ensemble complète de l’application, vous devez d’abord vérifier vos composants afin de déterminer le moment auquel le point d’arrêt de chacun est atteint.
* Pour l’identifier, vous pouvez effectuer un test de charge où, sur une période de temps, vous augmentez le nombre d’utilisateurs pour soumettre le composant à une charge de plus en plus élevée. En surveillant cette charge, et la réponse des composants, vous rencontrerez un comportement de performance spécifique au moment où le point d’arrêt du composant est atteint. Le point peut être qualifié par le nombre de transactions simultanées par seconde, ainsi que par le nombre d’utilisateurs simultanés (si le composant est sensible à cet indicateur de performance clé).
* Ces informations peuvent ensuite servir de référence pour les améliorations, indiquer l’efficacité des mesures utilisées et aider à définir des scénarios de test.

#### Transactions {#transactions}

* Le terme transaction est utilisé pour représenter la demande d’une page web complète, y compris la page elle-même et tous les appels suivants ; c’est-à-dire la demande de page, les appels AJAX, les images et d’autres objets.**Analyse en profondeur de la requête**
* Pour analyser entièrement chaque requête, vous pouvez représenter chaque élément de la pile d’appels, puis totaliser la durée moyenne de traitement de chacune d’elles.

### Définition des objectifs de performance {#defining-the-performance-goals}

Une fois la portée et les indicateurs de performance clé associés définis, il convient de définir les objectifs de performances. Cela implique de concevoir des scénarios de test, ainsi que des valeurs cibles.

Vous devrez tester les performances en conditions moyennes et de pointe. En outre, vous aurez besoin de tests de scénario En ligne pour vous assurer que vous pouvez prendre en charge un intérêt accru pour votre site web lorsqu’il sera disponible pour la première fois.

Toute expérience ou statistique que vous avez peut-être collectée sur un site Web existant peut également être utile pour déterminer les objectifs futurs ; par exemple, le trafic le plus élevé de votre site web actif.

#### Tests sur des composants uniques {#single-component-tests}

Les composants essentiels devront être testés en conditions moyennes et de pointe.

Dans les deux cas, vous pouvez définir le nombre de transactions attendu par seconde lorsqu’un nombre prédéfini d’utilisateurs utilisent le système.

| Composant | Type de test | Nombre d’utilisateurs | T/s (attendu) | T/s (testé) | Description |
|---|---|---|---|---|---|
| Page d’accueil - Utilisateur unique | Moyenne | 1 | 1 |  |  |
|  | Crête | 1 | 3 |  |  |
| Page d’accueil 100 utilisateurs | Moyenne | 100 | 3 |  |  |
|  | Crête | 100 | 3 |  |

#### Tests de composant combinés {#combined-component-tests}

Le test combiné des composants permet de mieux visualiser le comportement des applications. Là encore, les conditions moyennes et de pointe doivent être testées.

| Scénario | Composant | Nombre d’utilisateurs | T/s (attendu) | T/s (testé) | Description |
|---|---|---|---|---|---|
| Moyenne mixte | Page d’accueil | 10 | 1 |  |  |
|  | Rechercher | 10 | 1 |  |  |
|  | Actualités | 10 | 2 |  |  |
|  | Événements | 10 | 1 |  |  |
|  | Activations | 10 | 3 |  | Simulation du comportement de l’auteur. |
| Pic mixte | Page d’accueil | 100 | 5 |  |  |
|  | Rechercher | 50 | 5 |  |  |
|  | Actualités | 100 | 10 |  |  |
|  | Événements | 100 | 10 |  |  |
|  | Activations | 20 | 20 |  | Simulation du comportement de l’auteur. |

#### Tests en direct {#going-live-tests}

Au cours des premiers jours suivant la mise en ligne de votre site web, attendez-vous à un niveau élevé d’intérêt. Il sera probablement plus important que les valeurs de pointe que vous avez testées. Il est vivement recommandé de tester les scénarios de mise en ligne afin de s’assurer que le système peut prendre en charge cette situation.

| Scénario | Type de test | Nombre d’utilisateurs | T/s (attendu) | T/s (testé) | Description |
|---|---|---|---|---|---|
| Pic de mise en service | Page d’accueil | 200 | 20 |  |  |
|  | Rechercher | 100 | 10 |  |  |
|  | Actualités | 200 | 20 |  |  |
|  | Événements | 200 | 20 |  |  |
|  | Activations | 20 | 20 |  | Simulation du comportement de l’auteur. |

#### Tests de scénario d’erreur {#error-scenario-tests}

Les scénarios d’erreur doivent également être testés pour s’assurer que le système réagit correctement et de manière appropriée. Non seulement en termes de traitement de l’erreur elle-même, mais aussi de répercussions sur les performances. Par exemple :

* Ce qui se passe lorsque l’utilisateur tente d’entrer un terme de recherche non valide dans la zone de recherche.
* Ce qui se passe lorsque le terme de recherche est tellement général qu’il renvoie un nombre excessif de résultats.

Lors de la conception de ces tests, il faut se souvenir que tous les scénarios ne se produiront pas régulièrement. Cependant, leur impact sur l&#39;ensemble du système est important.

| Scénario d’erreur | Type d’erreur | Nombre d’utilisateurs | T/s (attendu) | T/s (testé) | Description |
|---|---|---|---|---|---|
| Surcharge des composants de recherche | Recherche sur un caractère générique (astérisque) | 10 | 1 |  | Seul les &amp;ast;&amp;ast;&amp;ast; sont recherchées. |
|  | Mot de fin | 20 | 2 |  | Recherche d’un mot de fin. |
|  | Chaîne vide | 10 | 1 |  | Recherche d’une chaîne vide. |
|  | Caractères spéciaux | 10 | 1 |  | Recherche de caractères spéciaux. |

#### Tests d’endurance {#endurance-tests}

Certains problèmes ne feront surface qu’après une période continue de fonctionnement du système, qu’il s’agisse d’heures ou même de jours. Un test d&#39;endurance est utilisé pour tester une charge moyenne constante sur une période donnée. Toute dégradation des performances peut ensuite être analysée.

| Scénario | Type de test | Nombre d’utilisateurs | T/s (attendu) | T/s (testé) | Description |
|---|---|---|---|---|---|
| Test d’endurance (72 heures) | Page d’accueil | 10 | 1 |  |  |
|  | Rechercher | 10 | 1 |  |  |
|  | Actualités | 20 | 2 |  |  |
|  | Événements | 10 | 1 |  |  |
|  | Activations | 1 | 3 |  | Simulation du comportement de l’auteur. |

### Optimisation {#optimization}

Dans les dernières étapes de la mise en œuvre, vous allez optimiser l’application pour atteindre/maximiser les objectifs de performances.

Toutes les optimisations effectuées doivent être testées pour s’assurer :

* qu’elles ne dégradent pas les fonctionnalités ;
* qu’elles ont été vérifiées au moyen de tests de charge avant d’être appliquées.

Une sélection d’outils est disponible pour vous aider dans la génération de la charge, la surveillance des performances et/ou l’analyse des résultats :

* [JMeter](https://jakarta.apache.org/jmeter/)
* [Load Runner](https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview)
* [Determyne](https://www.determyne.com/) InsideApps
* [InfraRED](https://www.infraredsoftware.com/)
* [Profil interactif Java](https://jiprof.sourceforge.net/)
* beaucoup plus...

Après l’optimisation, vous devrez effectuer un nouveau test pour confirmer l’impact.

### Création de rapports {#reporting}

Des rapports continus seront nécessaires pour tenir tout le monde informé du statut. Comme mentionné précédemment avec le codage par couleur, la carte d’architecture peut être utilisée à cet effet.

Une fois tous les tests terminés, il convient de faire état :

* de toutes les erreurs critiques rencontrées ;
* des problèmes non critiques qui mériteront d’être étudiés davantage ;
* des hypothèses émises lors des tests ;
* de toute recommandation découlant des tests.

## Optimisation des performances lors de l’utilisation de Dispatcher {#optimizing-performance-when-using-the-dispatcher}

Le [dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher.html) est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe. Lorsque vous l’utilisez, pensez à optimiser votre site Web en termes de performances du cache.

>[!NOTE]
>
>Les versions de Dispatcher sont indépendantes de AEM, mais la documentation de Dispatcher est incorporée dans la documentation d’AEM. Utilisez toujours la documentation de Dispatcher incluse dans la documentation pour la dernière version d’AEM.
>
>Vous avez été redirigé vers cette page si vous avez suivi un lien vers la documentation de Dispatcher incluse dans la documentation d’une précédente version d’AEM.

Le dispatcher propose un certain nombre de mécanismes intégrés pour optimiser les performances à condition que votre site web en tire parti. Cette section vous explique comment concevoir votre site web afin d’optimiser les avantages de la mise en cache.

>[!NOTE]
>
>Il peut être utile de vous rappeler que le dispatcher stocke le cache sur un serveur web standard. Cela signifie que vous :
>
>* vous pouvez mettre en cache tous les éléments que vous pouvez enregistrer en tant que page et effectuer une demande à l’aide d’une URL ;
>* vous ne pouvez pas enregistrer d’autres éléments, tels que des cookies, des données de session et des données de formulaire.
>
>En général, de nombreuses stratégies de mise en cache impliquent de sélectionner les URL appropriées et de ne pas s’en tenir à ces informations supplémentaires.
>
>Avec la version 4.1.11 du Dispatcher, vous pouvez également mettre en cache les en-têtes de réponse, consultez [Mise en cache des en-têtes de réponse HTTP](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache).

### Calcul du ratio de cache de Dispatcher {#calculating-the-dispatcher-cache-ratio}

La formule de ratio de cache estime le pourcentage de requêtes traitées par le cache sur le nombre total de requêtes entrant dans le système. Pour calculer ce ratio, vous avez besoin des éléments suivants :

* Le nombre total de demandes. Cette information est disponible dans Apache `access.log`. Pour plus d’informations, voir [documentation officielle d’Apache](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

* Le nombre de demandes traitées par l’instance de publication. Cette information est disponible dans le fichier `request.log` de l’instance. Pour plus d’informations, consultez [Interprétation du fichier request.log](/help/sites-deploying/monitoring-and-maintaining.md#interpreting-the-request-log) et [Recherche des fichiers journaux](/help/sites-deploying/monitoring-and-maintaining.md#finding-the-log-files).

Formule de calcul du ratio :

* (nombre total de demandes **moins** le nombre de demandes sur l’instance de publication) **divisé** par le nombre total de demandes.

Par exemple, si le nombre total de requêtes est de 129491 et que le nombre de requêtes servies par l’instance de publication est de 58959, le ratio de cache est : **(129491 - 58959)/129491= 54,5 %**.

Si vous ne disposez pas d’une association d’éditeur/dispatcher unique, vous devrez ajouter ensemble les requêtes de tous les dispatchers et éditeurs pour obtenir une mesure précise. Voir aussi [Déploiements recommandés](/help/sites-deploying/recommended-deploys.md).

>[!NOTE]
>
>Pour de meilleures performances, Adobe recommande un ratio de 90 % à 95 % du cache.

#### Utilisation d’un codage cohérent de page  {#using-consistent-page-encoding}

Avec la version 4.1.11 de Dispatcher, vous pouvez mettre en cache les en-têtes de réponse. Si vous ne mettez pas en cache les en-têtes de réponse sur le dispatcher, des problèmes peuvent survenir quand vous stockez des informations de codage de page dans l’en-tête. Dans ce cas, lorsque Dispatcher diffuse une page du cache, le codage par défaut du serveur web est utilisé pour la page. Deux méthodes permettent d’éviter ce problème :

* Si vous n’utilisez qu’un seul encodage, assurez-vous que le codage utilisé sur le serveur web est identique à celui par défaut du site web AEM.
* Utilisez une balise `<META>` dans la section `head` du code HTML pour définir le codage, comme dans l’exemple suivant :

```xml
        <META http-equiv="Content-Type" content="text/html; charset=EUC-JP">
```

#### Contournement des paramètres d’URL {#avoid-url-parameters}

Si possible, évitez les paramètres d’URL des pages que vous souhaitez mettre en cache. Par exemple, si vous disposez d’une galerie d’images, l’URL suivante n’est jamais mise en cache (sauf si Dispatcher est [configuré en conséquence](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache)) :

```xml
www.myCompany.com/pictures/gallery.html?event=christmas&amp;page=1
```

Vous pouvez toutefois placer ces paramètres dans l’URL de la page, comme suit :

```xml
www.myCompany.com/pictures/gallery.christmas.1.html
```

>[!NOTE]
>
>Cette URL invoque la même page et le même modèle que `gallery.html`. Dans la définition du modèle, vous pouvez spécifier le script qui effectue le rendu de la page ou vous pouvez utiliser le même script pour toutes les pages.

#### Personnalisation par URL  {#customize-by-url}

Si vous autorisez les utilisateurs à modifier la taille de la police (ou toute autre personnalisation de la mise en page), assurez-vous que les différentes personnalisations sont reflétées dans l’URL.

Par exemple, les cookies ne sont pas mis en cache. Par conséquent, si vous stockez la taille de police dans un cookie (ou un mécanisme similaire), la taille de police n’est pas conservée pour la page mise en cache. Par conséquent, Dispatcher renvoie aléatoirement des documents de n’importe quelle taille de police.

L’inclusion de la taille de police dans l’URL en tant que sélecteur évite ce problème :

```xml
www.myCompany.com/news/main.large.html
```

>[!NOTE]
>
>Pour la plupart des aspects de mise en page, il est également possible d’utiliser des feuilles de style et/ou des scripts côté client. Ces fonctionnalités fonctionnent généralement très bien avec la mise en cache.
>
>Elles sont également utiles pour une version imprimée. Dans ce cas, vous pouvez également utiliser une URL telle que : 
>
>`www.myCompany.com/news/main.print.html`
>
>À l’aide de l’extension métacaractère de script de la définition du modèle, vous pouvez spécifier un script distinct qui effectue le rendu des pages d’impression.

#### Invalidation de fichiers image utilisés comme titres  {#invalidating-image-files-used-as-titles}

Si vous effectuez le rendu des titres de page, ou d’un autre texte, sous forme d’images, il est recommandé de stocker les fichiers afin qu’ils soient supprimés lors d’une mise à jour du contenu sur la page :

1. Placez le fichier image dans le même dossier que la page.
1. Utilisez le format d’affectation de nom suivant pour le fichier image :

   `<page file name>.<image file name>`

Par exemple, vous pouvez stocker le titre de la page myPage.html dans le fichier . `myPage.title.gif`. Ce fichier est automatiquement supprimé si la page est mise à jour. Toute modification du titre de la page est donc automatiquement répercutée dans le cache.

>[!NOTE]
>
>Le fichier image n’existe pas nécessairement physiquement sur l’instance AEM. Vous pouvez utiliser un script qui crée dynamiquement le fichier image. Dispatcher stocke ensuite le fichier sur le serveur web.

#### Invalidation des fichiers image utilisés pour la navigation  {#invalidating-image-files-used-for-navigation}

Si vous utilisez des images pour les entrées de navigation, la méthode est fondamentalement la même qu’avec les titres. Elle est seulement un peu plus complexe. Stockez toutes les images de navigation avec les pages cibles. Si vous utilisez deux images pour normal et principal, vous pouvez utiliser les scripts suivants :

* Script qui affiche la page, normalement.
* Un script qui traite les requêtes &quot;.normal&quot; et renvoie l’image normale.
* Un script qui traite les demandes &quot;.principal&quot; et renvoie l’image activée.

Il est important que vous créiez ces images avec le même nom d’utilisateur que la page, afin de vous assurer qu’une mise à jour du contenu supprime ces images ainsi que la page.

Pour les pages qui ne sont pas modifiées, les images restent dans le cache, bien que les pages elles-mêmes soient généralement invalidées automatiquement.

#### Personnalisation  {#personalization}

Il est recommandé de limiter la personnalisation à l’endroit nécessaire. Pour illustrer pourquoi :

* Si vous utilisez une page de démarrage personnalisable librement, cette page doit être composée chaque fois qu’un utilisateur la demande.
* Si, en revanche, vous offrez un choix de 10 pages de démarrage différentes, vous pouvez mettre en cache chacune d’elles, améliorant ainsi les performances.

>[!TIP]
>
>Pour plus d’informations sur la configuration du cache de Dispatcher, consultez le [Tutoriel sur le cache du Dispatcher AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/dispatcher-tutorial/overview.html?lang=fr) et sa section sur [Mise en cache du contenu protégé](https://experienceleague.adobe.com/docs/experience-manager-learn/dispatcher-tutorial/chapter-1.html?lang=fr#dispatcher-tips-and-tricks).

Si vous personnalisez chaque page (par exemple en mettant le nom d’utilisateur dans la barre de titre), cela peut avoir un impact sur les performances.

>[!TIP]
>
>Pour la mise en cache du contenu sécurisé, consultez [Mise en cache du contenu sécurisé](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=fr) dans le guide du Dispatcher.

En ce qui concerne le mélange de contenu public et restreint sur une page, vous pouvez envisager une stratégie qui tire parti des inclusions côté serveur dans le Dispatcher, ou des inclusions côté client via Ajax dans le navigateur.

>[!TIP]
>
>Pour gérer le contenu public mixte et le contenu restreint, consultez [Configurer l’inclusion dynamique Sling.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-sling-dynamic-include.html?lang=fr)

#### Connexions persistantes {#sticky-connections}

[Connexions persistantes](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher.html#the-benefits-of-load-balancing) assurez-vous que les documents d’un utilisateur sont tous composés sur le même serveur. Si un utilisateur quitte ce dossier et y revient ultérieurement, la connexion reste établie. Définissez un dossier destiné à contenir tous les documents nécessitant des connexions persistantes pour le site web. Essayez de ne pas y avoir d&#39;autres documents. Cela a un impact sur l’équilibrage de charge si vous utilisez des pages personnalisées et des données de session.

#### Types MIME  {#mime-types}

Un navigateur peut déterminer le type d’un fichier de deux manières différentes :

1. Grâce à son extension (par exemple, `.html`, `.gif`, `.jpg`, etc.)
1. Par le type MIME que le serveur envoie avec le fichier.

Pour la plupart des fichiers, le type MIME est implicite dans l’extension de fichier. i.e.:

1. Grâce à son extension (par exemple, `.html`, `.gif`, `.jpg`, etc.)
1. Par le type MIME que le serveur envoie avec le fichier.

Si le nom de fichier ne comporte aucune extension, il s’affiche sous la forme de texte brut.

Avec la version 4.1.11 de Dispatcher, vous pouvez mettre en cache les en-têtes de réponse. Si vous ne mettez pas en cache les en-têtes de réponse sur Dispatcher, sachez que le type MIME fait partie de l’en-tête HTTP. À cet égard, si votre application AEM renvoie des fichiers qui n’ont pas d’extension reconnue, mais utilisent le type MIME à la place, ces fichiers risquent d’être affichés de manière erronée.

Pour vous assurer que les fichiers sont correctement mis en cache, suivez ces instructions :

* Assurez-vous que les fichiers ont toujours l’extension appropriée.
* Évitez les scripts génériques de diffusion de fichiers avec une URL de type : `download.jsp?file=2214`. Réécrivez le script afin d’utiliser les URL contenant la spécification de fichier. Pour l’exemple précédent, il s’agit de `download.2214.pdf`.

## Performances des sauvegardes {#backup-performance}

Cette section présente une série de points de référence utilisés pour évaluer les performances des sauvegardes AEM et les effets de l’activité de sauvegarde sur les performances des applications. Une sauvegarde AEM présente une charge importante sur le système pendant son exécution. Nous mesurons cela, ainsi que les effets des paramètres de délai de sauvegarde qui tentent de moduler ces effets. L’objectif est de fournir des données de référence sur les performances attendues des sauvegardes dans des configurations réalistes et des quantités de données de production, et de fournir des conseils sur la manière d’estimer les temps de sauvegarde pour les systèmes planifiés.

### Environnement de référence {#reference-environment}

#### Système physique {#physical-system}

Les résultats signalés dans ce document ont été obtenus à partir de références exécutées dans un environnement de référence avec la configuration suivante. Cette configuration se rapproche d’un environnement de exploitation typique dans un centre de données :

* H-P ProLiant DL380 G6, 8 processeurs x 2,533 GHz
* Disques 300 Go 10 000 tr/min connectés en série
* Contrôleur RAID matériel ; 8 disques dans une baie RAID 0+5
* Image VMware CPU x 2 Intel Xeon E5540 @ 2,53GHz
* RedHat Linux 2.6.18-194.el5; Java 1.6.0_29
* Instance de création unique

Le sous-système de disque sur ce serveur est assez rapide, représentatif d&#39;une configuration RAID haute performance qui pourrait être utilisée dans un serveur de production. Les performances de sauvegarde peuvent être sensibles aux performances du disque et les résultats de cet environnement reflètent les performances sur une configuration RAID très rapide. L&#39;image VMWare est configurée pour avoir un seul gros volume de disque qui réside physiquement dans le stockage du disque local, sur la matrice RAID.

La configuration AEM place le référentiel et le magasin de données sur le même volume logique, avec tous les autres logiciels du système d’exploitation et d’AEM. Le répertoire cible des sauvegardes se trouve également sur ce système de fichiers logique.

#### Volumes de données {#data-volumes}

Le tableau suivant illustre la taille des volumes de données utilisés dans les repères de sauvegarde. Le contenu de base initial est d’abord installé, puis des quantités de données connues supplémentaires sont ajoutées pour augmenter la taille du contenu sauvegardé. Les sauvegardes seront créées à des incréments spécifiques afin de représenter une augmentation importante du contenu et de ce qui peut être produit en une journée. La distribution du contenu (pages, images, balises) dépendra approximativement de la composition réaliste des ressources de production. Les pages, images et balises sont limitées à 800 pages enfants au maximum. Chaque page comprend les composants titre, Flash, texte/image, vidéo, diaporama, formulaire, tableau, cloud et carrousel. Les images seront chargées à partir d’un pool de 400 fichiers uniques dont la taille va de 37 Ko à 594 Ko.

| Contenu | Nœuds | Pages | Images | Balises |
|---|---|---|---|---|
| Installation de base | 69 610 | 562 | 256 | 237 |
| Petit contenu pour une sauvegarde progressive |  | +100 | +2 | +2 |
| Contenu volumineux pour une sauvegarde complète |  | +10 000 | +100 | +100 |

L’essai comparatif de sauvegarde est réitéré avec des jeux de contenu supplémentaires ajoutés à chaque itération.

#### Scénarios de test {#benchmark-scenarios}

Les références de sauvegarde couvrent deux scénarios principaux : effectue des sauvegardes lorsque le système est soumis à une charge d’application importante, et des sauvegardes lorsque le système est inactif. Selon la recommandation générale, les sauvegardes doivent être effectuées lorsqu’AEM est aussi inactif que possible. Pourtant, il existe des situations où il est nécessaire que la sauvegarde soit exécutée quand le système est en charge.

* **État inactif** Les sauvegardes sont effectuées sans autre activité sur AEM.
* **Sous Chargement** Les sauvegardes sont effectuées lorsque la charge du système est inférieure à 80 % par rapport aux processus en ligne. Variation du délai de sauvegarde pour déterminer l’impact sur la charge.

La durée des sauvegardes et la taille des sauvegardes qui en résultent sont obtenues à partir des journaux du serveur AEM. Il est généralement recommandé de planifier des sauvegardes pendant des périodes d’interruption lorsqu’AEM est inactif, par exemple au milieu de la nuit. Ce scénario est représentatif de l’approche recommandée.

Le chargement se compose de la création/suppression de pages, de traversées et de requêtes, la majeure partie de la charge provenant des traversées et des requêtes de page. L’ajout et la suppression de trop de pages augmentent continuellement la taille de l’espace de travail et empêchent les sauvegardes de s’achever. La répartition de la charge que le script utilisera est de 75 % de traversées de page, 24 % de requêtes et 1 % de créations de pages (niveau unique sans sous-pages imbriquées). Le nombre moyen/maximal de transactions par seconde sur un système inactif est obtenu avec 4 threads simultanés, ce qui sera utilisé lors du test des sauvegardes avec une charge.

L’impact de la charge sur les performances de sauvegarde peut être estimé par la différence entre les performances avec et sans cette charge applicative. L’impact de la sauvegarde sur le débit de l’application est détecté en comparant le débit du scénario dans les transactions par heure avec et sans sauvegarde simultanée en cours, et avec des sauvegardes fonctionnant avec différents paramètres de &quot;délai de sauvegarde&quot;.

* **Paramètre de délai** Pour plusieurs des scénarios, nous avons également modifié le paramètre de délai de sauvegarde, en utilisant des valeurs de 10 ms (par défaut), 1 ms et 0 ms, afin d’explorer la manière dont ce paramètre a affecté les performances des sauvegardes.
* **Type de sauvegarde** Toutes les sauvegardes étaient des sauvegardes externes du référentiel effectuées dans un répertoire de sauvegarde sans créer de fichier zip, sauf dans un cas pour comparaison où la commande tar était utilisée directement. Étant donné que les sauvegardes incrémentielles ne peuvent pas être créées dans un fichier zip ou si la sauvegarde complète antérieure est un fichier zip, la méthode du répertoire de sauvegarde est la plus souvent utilisée dans des situations de exploitation.

### Résumé des résultats {#summary-of-results}

#### Durée et débit de sauvegarde {#backup-time-and-throughput}

Le principal résultat de ces repères est de montrer comment les temps de sauvegarde varient en fonction du type de sauvegarde et de la quantité globale de données. Le graphique suivant montre le temps de sauvegarde obtenu à l’aide de la configuration de sauvegarde par défaut, en fonction du nombre total de pages.

![chlimage_1-81](assets/chlimage_1-81.png)

Les durées des sauvegardes sur une instance inactive sont relativement constantes, avec une moyenne de 0,608 Mo/s, indépendamment des sauvegardes complètes ou incrémentielles (voir le tableau ci-dessous). La durée de sauvegarde est simplement fonction de la quantité de données sauvegardées. Le temps nécessaire pour effectuer une sauvegarde complète augmente nettement avec le nombre total de pages. Le temps nécessaire pour effectuer une sauvegarde incrémentielle augmente également avec le nombre total de pages, mais à un taux beaucoup plus faible. Le temps nécessaire à l’exécution de la sauvegarde incrémentielle est beaucoup plus court en raison de la quantité relativement faible de données sauvegardées.

La taille de la sauvegarde produite est le principal facteur déterminant du temps nécessaire pour effectuer une sauvegarde. Le graphique suivant montre le temps pris en fonction de la taille de sauvegarde finale.

![chlimage_1-82](assets/chlimage_1-82.png)

Ce graphique montre que les sauvegardes incrémentielles et complètes suivent un modèle simple de taille par rapport au temps que nous pouvons mesurer en tant que débit. Les temps de sauvegarde sur une instance inactive sont assez constants, avec une moyenne de 0,61 Mo/s, indépendamment des sauvegardes complètes ou incrémentielles dans l’environnement de référence.

#### Délai de sauvegarde {#backup-delay}

Le paramètre de délai de sauvegarde est fourni pour limiter la mesure dans laquelle les sauvegardes peuvent interférer avec les charges de travail de production. Le paramètre spécifie un temps d’attente en millisecondes, qui est entrecoupé dans l’opération de sauvegarde fichier par fichier. L’effet global dépend en partie de la taille des fichiers concernés. La mesure des performances de sauvegarde en Mo/s offre un moyen raisonnable de comparer les effets du délai sur la sauvegarde.

* L’exécution simultanée d’une sauvegarde avec une charge applicative normale aura un impact négatif sur le débit de la charge normale.
* L’impact peut être faible - pas plus de 5 % - ou peut être très significatif - entraînant jusqu’à 75 % de baisse du débit, et cela dépend probablement plus que tout de l’application.
* La sauvegarde ne constitue pas une charge contraignante pour le processeur. De ce fait, les charges de travail de exploitation consommatrices de ressources de processeur sont moins affectées par la sauvegarde que celles plus gourmandes en E/S.

![chlimage_1-83](assets/chlimage_1-83.png)

Pour comparer, le débit obtenu à l’aide d’une sauvegarde du système de fichiers (à l’aide de &#39;tar&#39;) pour sauvegarder les mêmes fichiers de référentiel. La performance du tar est comparable, mais légèrement supérieure à la sauvegarde avec un délai défini sur zéro. La définition d’un délai même minime réduit considérablement le débit de sauvegarde et le délai par défaut de 10 ms entraîne un débit considérablement réduit. Dans les cas où des sauvegardes peuvent être planifiées lorsque l’utilisation globale de l’application est très faible ou que l’application peut être complètement inactive, il est probablement souhaitable de réduire le délai en dessous de la valeur par défaut afin de permettre une sauvegarde plus rapide.

L’impact réel du débit d’application d’une sauvegarde en cours dépend des détails de l’application et de l’infrastructure. Le choix de la valeur de délai doit être effectué par une analyse empirique de l’application, mais doit être choisi aussi petit que possible, de sorte que les sauvegardes puissent être effectuées le plus rapidement possible. Comme il n’existe qu’une faible corrélation entre le choix de la valeur de délai et l’impact sur le débit de l’application, le choix du délai doit favoriser des temps de sauvegarde globaux plus courts, afin de minimiser l’impact global des sauvegardes. Une sauvegarde qui prend 8 heures, mais affecte le débit de -20 %, risque d’avoir un impact global plus important que celui qui prend 2 heures, mais affecte le débit de -30 %.

### Références {#references}

* [Administration – Sauvegarde et restauration](/help/sites-administering/backup-and-restore.md)
* [Gestion – Capacité et volume](/help/managing/best-practices-further-reference.md#capacity-and-volume)
