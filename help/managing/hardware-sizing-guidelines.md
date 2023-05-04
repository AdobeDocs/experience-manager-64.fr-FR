---
title: Consignes de dimensionnement du matériel
seo-title: Hardware Sizing Guidelines
description: Ces consignes de dimensionnement procurent une estimation des ressources matérielles requises pour déployer un projet AEM.
seo-description: These sizing guidelines offer an approximation of the hardware resources required to deploy an AEM project.
uuid: 83f928e3-986b-461b-8b3e-8faacd11172e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 3f4feb38-eca0-4852-88f8-9b20625e18ad
exl-id: 34e4edd5-9e67-44ed-8c4c-bcdd3e161a35
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2867'
ht-degree: 42%

---

# Consignes de dimensionnement du matériel {#hardware-sizing-guidelines}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Ces consignes de dimensionnement procurent une estimation des ressources matérielles requises pour déployer un projet AEM. Les estimations de dimensionnement dépendent de l’architecture du projet, de la complexité de la solution, du trafic estimé et des exigences du projet. Ce guide vous aide à déterminer les besoins matériels pour une solution spécifique ou à trouver une estimation supérieure et inférieure pour les exigences matérielles.

Les facteurs de base à prendre en compte sont (dans cet ordre) :

* **Vitesse réseau**

   * Latence réseau
   * Bande passante disponible

* **Vitesse de calcul**

   * Efficacité de la mise en cache
   * Trafic attendu
   * Complexité des modèles, applications et composants
   * Auteurs simultanés
   * Complexité de l’opération de création (édition de contenu simple, déploiement MSM, etc.)

* **Performances des E/S**

   * Performances et efficacité du stockage du fichier ou de la base de données

* **Disque dur**

   * Au moins deux ou trois fois plus grand que la taille du référentiel

* **Mémoire**

   * Taille du site web (nombre d’objets de contenu, de pages et d’utilisateurs)
   * Nombre d’utilisateurs/sessions principaux en même temps

## Architecture {#architecture}

Une configuration d’AEM standard consiste en un environnement de création et de publication. Ces environnements ont des exigences différentes en ce qui concerne la taille matérielle et la configuration système sous-jacentes. Vous trouverez des considérations sur ces deux environnements dans les sections [Environnement de création](/help/managing/hardware-sizing-guidelines.md#author-environment-specific-calculations) et [Environnement de publication](/help/managing/hardware-sizing-guidelines.md#publish-environment-specific-calculations).

Dans une configuration de projet type, vous disposez de plusieurs environnements sur lesquels définir les phases du projet :

* **Environnement de développement**
Pour le développement de nouvelles fonctions ou pour apporter des modifications importantes. La meilleure pratique consiste à travailler avec un environnement de développement par développeur (généralement des installations locales sur leurs systèmes personnels).

* **Environnement de test de création**
Pour vérifier les modifications. Le nombre d’environnements de test varie selon les exigences du projet (qui nécessite, par exemple, un environnement distinct pour l’assurance qualité, le test de l’intégration ou le test d’acceptation utilisateur).

* **Environnement de test de publication**
Principalement pour tester les cas d’utilisation de collaboration sociale ou l’interaction entre l’instance de création et plusieurs instances de publication.

* **Environnement d’exploitation de création**
Pour que les auteurs modifient le contenu.

* **Environnement d’exploitation de publication**
Pour servir du contenu publié.

En outre, les environnements peuvent varier, allant d’un système à serveur unique exécutant AEM et un serveur d’applications, à un ensemble d’instances en grappe multi-serveur et multi-processeur à très grande échelle. Nous vous recommandons d’utiliser un ordinateur distinct pour chaque système de production et de ne pas exécuter d’autres applications sur ces ordinateurs.

## Considérations génériques sur le dimensionnement du matériel {#generic-hardware-sizing-considerations}

Les sections ci-dessous fournissent des conseils sur la manière de calculer les exigences matérielles, en tenant compte de diverses considérations. Pour les systèmes de grande taille, nous suggérons que vous réalisiez un simple jeu de tests d’évaluation des performances en interne sur une configuration de référence.

L’optimisation des performances est une tâche fondamentale qui doit être effectuée avant que toute évaluation des performances ne puisse être réalisée pour un projet spécifique. Veillez à suivre les conseils fournis dans la [documentation d’optimisation des performances](/help/sites-deploying/configuring-performance.md) avant de procéder aux tests d’évaluation des performances et d’utiliser leurs résultats pour les calculs de dimensionnement du matériel.

Les exigences de dimensionnement du matériel pour les cas d’utilisation avancés doivent être basées sur une évaluation détaillée des performances du projet. Les caractéristiques des cas d’utilisation avancés nécessitant des ressources matérielles exceptionnelles incluent les combinaisons suivantes :

* Un payload ou un débit de contenu élevé
* utilisation étendue de code personnalisé, de workflows personnalisés ou de bibliothèques de logiciels tierces
* intégration à des systèmes externes non pris en charge

### Espace disque/disque dur {#disk-space-hard-drive}

L’espace disque requis dépend largement du volume et du type de votre application web. Les calculs doivent prendre en compte :

* la quantité et la taille des pages, des ressources et d’autres entités stockées dans le référentiel telles que les workflows, les profils, etc.
* la fréquence estimée des changements de contenu et, par conséquent, la création de versions de contenu ;
* le volume de rendus de ressources DAM qui seront générés ;
* la croissance globale du contenu au fil du temps ;

L’espace disque est surveillé en permanence pendant le nettoyage des révisions en ligne et hors ligne. Si l’espace disque disponible tombe en dessous d’une valeur critique, le processus sera annulé. La valeur critique est de 25 % de l’empreinte disque actuelle du référentiel et elle n’est pas configurable. Il est recommandé de dimensionner le disque de sorte qu’il soit au moins deux ou trois fois plus large que la taille du référentiel, y compris sa croissance estimée.

Envisagez une configuration de tableaux redondants de disques indépendants (RAID, par exemple RAID10) pour la redondance des données.

>[!NOTE]
>
>Le répertoire temporaire d’une instance de production doit contenir au moins 6 Go d’espace disponible.

### Virtualisation {#virtualization}

AEM fonctionne bien dans les environnements virtualisés, mais certains facteurs tels que le processeur ou les E/S ne peuvent pas être directement liés au matériel physique. Il est recommandé de choisir une vitesse d’E/S plus élevée (en général), car c’est un facteur essentiel dans la plupart des cas. L’évaluation comparative de votre environnement est nécessaire pour obtenir une compréhension précise des ressources requises.

### Mise en parallèle des instances AEM {#parallelization-of-aem-instances}

#### Prévention de défaillance {#fail-safeness}

Un site web doté de la prévention de défaillance est déployé sur au moins deux systèmes distincts. Si un système tombe en panne, un autre système peut prendre la relève de façon à compenser la défaillance du système.

#### Évolutivité des ressources système {#system-resources-scalability}

Pendant que tous les systèmes sont en cours d’exécution, une performance de calcul accrue est disponible. Cette performance supplémentaire n’est pas nécessairement linéaire par rapport au nombre de nœuds de grappes, car les relations dépendent lourdement de l’environnement technique. Consultez la [documentation relative aux cluster](/help/sites-deploying/recommended-deploys.md) pour plus d’informations.

L’estimation du nombre de noeuds de grappe nécessaires repose sur les exigences de base et les cas d’utilisation spécifiques du projet web spécifique :

* Du point de vue de la sécurité des défaillances, il est nécessaire de déterminer, pour tous les environnements, l’importance de l’échec et le temps de compensation de l’échec en fonction du temps nécessaire à la récupération d’un noeud de grappe.
* En ce qui concerne l’évolutivité, le nombre d’opérations d’écriture est fondamentalement le facteur le plus important. Consultez la section [Auteurs travaillant en parallèle](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel) pour l’environnement de création et [Collaboration sociale](/help/managing/hardware-sizing-guidelines.md#aem-communities-sizing-considerations) pour l’environnement de publication. L’équilibrage de charge peut être établi pour les opérations qui accèdent au système uniquement afin de traiter les opérations de lecture. Consultez la section [Dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/user-guide.html) pour plus d’informations.

## Calculs spécifiques à l’environnement de création {#author-environment-specific-calculations}

À des fins d’évaluation des performances, Adobe a développé des tests d’évaluation des performances pour les instances d’auteur autonomes.

* **Test d’évaluation 1**

   Calculez le débit maximal d’un profil de chargement pour lequel les utilisateurs effectuent un simple exercice de création de page en plus d’un chargement de base de 300 pages existantes, toutes de nature similaire. Les étapes impliquées étaient la connexion au site, la création d’une page contenant un SWF et une image ou du texte, l’ajout d’un nuage de balises, puis l’activation de la page.

   * **Résultat**

      Le débit maximal d’un simple exercice de création de page comme ci-dessus (considéré comme une transaction) est de 1 730 transactions par heure.

* **Test d’évaluation 2**

   Calculez le débit maximal lorsque le profil de chargement comporte un mélange de création de page (10 %), de modification d’une page existante (80 %) et de création, puis de modification successive d’une page (10 %). La complexité des pages reste la même que dans le profil du test de référence 1. La modification de base de la page s’effectue en ajoutant une image et en modifiant le contenu texte. Là encore, l’exercice a été effectué sur une charge de base de 300 pages de la même complexité que celle définie dans le test de référence 1.

   * **Résultat**

      Le débit maximal d’un tel scénario d’opération de mélange a été de 3 252 transactions par heure.

>[!NOTE]
>
>Le débit ne fait pas la distinction entre les types de transaction dans un profil de charge. L’approche utilisée pour mesurer le débit permet de s’assurer qu’une proportion fixe de chaque type de transaction est incluse dans la charge de travail.

Les deux tests ci-dessus montrent clairement que le débit varie en fonction du type d&#39;opération. Utilisez les activités de votre environnement comme base pour dimensionner votre système. Vous obtiendrez un meilleur débit avec des actions moins intensives telles que la modification (qui est également plus courante).

### Mise en cache {#caching}

Dans l’environnement de création, l’efficacité de la mise en cache est en général bien plus faible, car les modifications du site web sont plus fréquentes et en raison du caractère hautement interactif et personnalisé du contenu. En utilisant le Dispatcher, vous pouvez mettre en cache des bibliothèques AEM, des scripts JavaScript, des fichiers CSS et des images de disposition. Cela permet d’accélérer certains aspects du processus de création. La configuration du serveur web afin de définir des en-têtes supplémentaires pour la mise en cache de ces ressources dans le navigateur, réduit le nombre de requêtes HTTP et améliore ainsi la réactivité du système pour les auteurs.

### Auteurs travaillant en parallèle {#authors-working-in-parallel}

Dans l’environnement de création, le nombre d’auteurs qui travaillent en parallèle et la charge que leurs interactions ajoutent au système constituent les principaux facteurs de limitation. Par conséquent, nous vous recommandons de mettre votre système à l’échelle en fonction du débit partagé des données.

Pour de tels scénarios, Adobe exécute des tests de référence sur un cluster à deux noeuds sans partage d’instances d’auteur.

* **Test d’évaluation des performances 1a**

   Avec une principale grappe sans partage de 2 instances d’auteur, calculez le débit maximal avec un profil de chargement où les utilisateurs effectuent un simple exercice de création de page en plus d’un chargement de base de 300 pages existantes, de nature similaire.

   * **Résultat**

      Le débit maximal d’un simple exercice de création de page, tel que ci-dessus (considéré comme une transaction) est de 2 016 transactions/heure. Il s’agit d’une augmentation d’environ 16 % par rapport à une instance de création autonome pour la même évaluation des performances.

* **Test d’évaluation des performances 2b**

   Avec une principale grappe sans partage de 2 instances d’auteur, calculez le débit maximal lorsque le profil de chargement comporte un mélange de création de pages (10 %), de modification de pages existantes (80 %) et de création et de modification d’une page l’une après l’autre (10 %). La complexité de la page reste la même que dans le profil du test de référence 1. La modification de base de la page s’effectue en ajoutant une image et en modifiant le contenu texte. Encore une fois, l’exercice a été effectué sur une charge de base de 300 pages de complexité identique à celle définie dans le test de référence 1.

   * **Résultat**

      Le débit maximal d’un tel scénario d’exploitation mixte a été de 6 288 transactions/heure. Il s’agit d’une augmentation d’environ 93 % par rapport à une instance de création autonome pour la même évaluation des performances.

>[!NOTE]
>
>Le débit ne fait pas la distinction entre les types de transaction dans un profil de charge. L’approche utilisée pour mesurer le débit permet de s’assurer qu’une proportion fixe de chaque type de transaction est incluse dans la charge de travail.

Les deux tests ci-dessus montrent clairement que AEM s’adapte bien aux auteurs qui effectuent des opérations de modification de base avec AEM. En général, AEM est plus efficace pour dimensionner les opérations de lecture.

Sur un site web type, la plupart des opérations de création se produisent pendant la phase du projet. Une fois le site web lancé, le nombre d’auteurs travaillant en parallèle atteint généralement une moyenne inférieure (mode opérationnel).

Vous pouvez calculer le nombre d’ordinateurs (ou unités centrales) requis pour l’environnement de création comme suit :

`n = numberOfParallelAuthors / 30`

Cette formule peut servir de ligne directrice générale pour la mise à l’échelle des processeurs lorsque les auteurs effectuent des opérations de base avec AEM. Cela suppose que le système et l’application soient optimisés. Toutefois, la formule ne contiendra pas la valeur true pour les fonctionnalités avancées telles que MSM ou Assets (voir les sections ci-dessous).

Consultez également les commentaires supplémentaires dans la section [Mise en parallèle](/help/managing/hardware-sizing-guidelines.md#parallelization-of-aem-instances) et [Optimisation des performances](/help/sites-deploying/configuring-performance.md).

### Recommendations matériel {#hardware-recommendations}

En règle générale, vous pouvez utiliser le même matériel pour votre environnement de création que celui recommandé pour votre environnement de publication. En règle générale, le trafic sur le site web est beaucoup plus faible sur les systèmes de création, mais l’efficacité du cache est également plus faible. Cependant, le facteur fondamental ici est le nombre d’auteurs travaillant en parallèle, ainsi que le type d’actions effectuées sur le système. En général, le clustering AEM (de l’environnement de création) est plus efficace pour dimensionner les opérations de lecture ; en d’autres termes, un cluster AEM se dimensionne correctement avec les auteurs qui effectuent des opérations de modification de base.

Adobe a effectué les tests d’évaluation des performances à l’aide du système d’exploitation Red Hat 5.5, exécuté sur une plateforme matérielle Hewlett-Packard ProLiant DL380 G5 avec la configuration suivante :

* Deux unités centrales Intel Xeon Quad Core X5450 à 3 GHz
* 8 Go de RAM
* Broadcom NetXtreme II BCM5708 gigabit Ethernet
* Contrôleur RAID HP Smart Array, cache de 256 Mo
* Deux disques SAS à 10 000 tr/min de 146 Go configurés en tant qu’ensemble à bandes RAID0
* Le score de référence de taux SPEC CINT2006 est de 110

AEM instances s’exécutaient avec une taille de tas minimale de 256 M, une taille de tas maximale de 1 024 M.

## Calculs spécifiques à l’environnement de publication {#publish-environment-specific-calculations}

### Efficacité de la mise en cache et trafic {#caching-efficiency-and-traffic}

L’efficacité du cache est essentielle à la vitesse du site web. Le tableau suivant indique le nombre de pages qu’un système AEM optimisé peut gérer par seconde à l’aide d’un proxy inverse, comme Dispatcher :

| Ratio de cache | Pages/s (pic) | Millions de pages/jour (moyenne) |
|---|---|---|
| 100% | 1000-2000 | 35-70 |
| 99% | 910 | 32 |
| 95% | 690 | 25 |
| 90% | 520 | 18 |
| 60% | 220 | 8 |
| 0% | 100 | 3,5 |

>[!CAUTION]
>
>Clause de non-responsabilité : Les nombres dépendent d’une configuration matérielle par défaut et peuvent varier en fonction du matériel utilisé.

Le ratio de cache est le pourcentage de pages que le Dispatcher peut renvoyer sans avoir à accéder à AEM. 100 % indique que le Dispatcher répond à toutes les requêtes, 0 % signifie que AEM calcule chaque page.

### Complexité des modèles et des applications {#complexity-of-templates-and-applications}

Si vous utilisez des modèles complexes, AEM plus de temps sera nécessaire pour effectuer le rendu d’une page. Les pages extraites du cache ne sont pas affectées par cette situation, mais la taille de la page reste pertinente en ce qui concerne le temps de réponse global. Le rendu d’une page complexe peut facilement prendre dix fois plus de temps que le rendu d’une page simple.

### Formule {#formula}

À l’aide de la formule suivante, vous pouvez faire une estimation de la complexité globale de votre solution AEM :

`complexity = applicationComplexity + ((1-cacheRatio) * templateComplexity)`

Selon la complexité, vous pouvez déterminer le nombre de serveurs (ou de cœurs d’unité centrale) dont vous avez besoin pour l’environnement de publication comme suit :

`n = (traffic * complexity / 1000 ) * activations`

Les variables de l’équation sont les suivantes :

<table>
 <tbody>
  <tr>
   <td>traffic</td>
   <td>Le trafic en pic attendu par seconde. Vous pouvez l’estimer comme le nombre de visites de pages par jour, divisé par 35 000.</td>
  </tr>
  <tr>
   <td>applicationComplexity</td>
   <td><p>Utilisez 1 pour une application simple, 2 pour une application complexe, ou une valeur intermédiaire :</p>
    <ul>
     <li>1 - Un site entièrement anonyme, orienté contenu</li>
     <li>1.1 - Un site entièrement anonyme, orienté contenu, avec personnalisation côté client/Target</li>
     <li>1.5 - Un site orienté contenu avec des sections anonymes et connectées, personnalisation côté client/Target</li>
     <li>1.7 - Pour un site orienté contenu avec des sections anonymes et connectées, une personnalisation côté client/Target et un contenu généré par l’utilisateur</li>
     <li>2 - Où l’ensemble du site nécessite une connexion, avec une utilisation intensive du contenu généré par l’utilisateur et diverses techniques de personnalisation</li>
    </ul> </td>
  </tr>
  <tr>
   <td>cacheRatio</td>
   <td>Pourcentage de pages qui sortent du cache du Dispatcher. Utilisez 1 si toutes les pages proviennent du cache ou 0 si chaque page est calculée par AEM.</td>
  </tr>
  <tr>
   <td>templateComplexity</td>
   <td>Utilisez une valeur comprise entre 1 et 10 pour indiquer la complexité de vos modèles. Des valeurs plus élevées indiquent des modèles plus complexes ; utilisez une valeur de 1 pour les sites avec une moyenne de 10 composants par page, une valeur de 5 pour une moyenne de 40 composants par page et 10 pour une moyenne de plus de 100 composants.</td>
  </tr>
  <tr>
   <td>activations</td>
   <td>Nombre d’activations moyennes (réplication de pages et de ressources de taille moyenne de l’auteur vers le niveau de publication) par heure divisé par x, où x est le nombre d’activations effectuées sur un système sans effets secondaires sur la performance des autres tâches traitées par le système. Vous pouvez également prédéfinir une valeur initiale pessimiste comme x = 100.<br /> </td>
  </tr>
 </tbody>
</table>

Si vous possédez un site web plus complexe, vous avez également besoin de serveurs web plus puissants afin qu’AEM réponde à une requête dans un délai acceptable.

* Complexité inférieure à 4 :
   * JVM RAM&amp;ast 1024 Mo ;
   * Processeur basse à moyenne performance

* Complexité entre 4 et 8 :
   * JVM RAM&amp;ast 2 048 Mo ;
   * Processeur milieu à hautes performances

* Complexité supérieure à 8 :
   * JVM RAM&amp;ast 4096 Mo ;
   * Processeur hautes performances de bout en bout

>[!NOTE]
>
>&amp;ast; Réservez suffisamment de RAM pour votre système d’exploitation en plus de la mémoire requise pour votre JVM.

## Autres calculs spécifiques à un cas d’utilisation {#additional-use-case-specific-calculations}

Outre le calcul d’une application web par défaut, vous devrez peut-être prendre en compte des facteurs spécifiques pour les cas d’utilisation suivants. Les valeurs calculées doivent être ajoutées au calcul par défaut.

### Considérations spécifiques aux ressources {#assets-specific-considerations}

Le traitement étendu des ressources numériques nécessite des ressources matérielles optimisées, les facteurs les plus pertinents sont la taille de l’image et le débit maximal des images traitées.

Allouez au moins 16 Go de segment de mémoire et configurez le workflow Ressource de mise à jour de gestion des ressources numériques pour qu’il utilise le [package Camera Raw](/help/assets/camera-raw.md) pour l’ingestion des images au format RAW.

>[!NOTE]
>
>Un débit d’images plus élevé signifie que les ressources informatiques doivent pouvoir suivre le rythme des E/S système et vice versa. Par exemple, si les workflows sont lancés par l&#39;import d&#39;images, le téléchargement de nombreuses images via WebDAV peut entraîner un retard de workflows.
>
>L’utilisation de disques distincts pour TarPM, le magasin de données et l’index de recherche peut aider à optimiser le comportement d’E/S du système (il est toutefois généralement préférable de conserver l’index de recherche localement).

>[!NOTE]
>
>Voir aussi [Guide des performances des ressources](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/assets-sizing-guide.html).

### Multi-site Manager {#multi-site-manager}

La consommation des ressources lors de l’utilisation d’AEM MSM dans un environnement de création dépend fortement des cas d’utilisation spécifiques. Les facteurs de base sont les suivants :

* Nombre de Live Copies
* Périodicité des déploiements
* Taille de l’arborescence de contenu à déployer
* Fonctionnalité connectée des actions de déploiement

Le test du cas d’utilisation prévu avec un extrait de contenu représentatif peut vous aider à mieux comprendre la consommation de ressources. Si vous extrapolez les résultats avec la fréquence prévue, vous pouvez évaluer les ressources supplémentaires requises pour AEM MSM.

Veuillez également tenir compte du fait que les auteurs travaillant en parallèle percevront des effets secondaires sur les performances si AEM cas d’utilisation MSM consomment plus de ressources que prévu.

### Considérations relatives au dimensionnement d’AEM Communities {#aem-communities-sizing-considerations}

Les sites AEM qui incluent des fonctions AEM Communities connaissent un haut niveau d’interaction des visiteurs du site (membres) dans l’environnement de publication.

Les considérations de dimensionnement d’un site de communauté dépendent de l’interaction anticipée des membres de la communauté et de l’importance accrue des performances optimales du contenu de la page.

Les membres envoyés du contenu généré par l’utilisateur sont stockés séparément du contenu de la page. Alors que la plateforme AEM utilise un magasin de nœuds qui réplique le contenu du site de l’instance de création vers l’instance de publication, AEM Communities utilise un magasin simple et commun pour le contenu généré par les utilisateurs qui n’est jamais répliqué.

Pour le magasin du contenu généré par les utilisateurs, il est nécessaire de sélectionner un fournisseur de ressources de stockage qui influence le déploiement sélectionné.\
Voir

* [Stockage de contenu de la communauté](/help/communities/working-with-srp.md)
* [Topologies recommandées pour Communities](/help/communities/topologies.md)
