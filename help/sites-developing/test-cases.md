---
title: Définition de cas de test
seo-title: Defining your Test Cases
description: Vos cas de test doivent être basés sur des cas d’utilisation et le cahier des charges détaillé
seo-description: Your test cases should be based upon the use cases and the detailed requirements specification
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
exl-id: ad529be3-9d31-492f-943f-ef3e99e13586
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 95%

---

# Définition de cas de test{#defining-your-test-cases}

Les cas de test doivent être basés sur les éléments suivants :

**Cas d’utilisation**

* Ceux-ci définissent les fonctionnalités requises en termes d’interaction entre les acteurs (rôles qui déclenchent certaines actions) et le système.
* Les cas d’utilisation doivent être définis par le client.

**Cahier des charges détaillé**

* Toutes les exigences fonctionnelles et de performance doivent être testées.

Les tests devraient définir clairement :

* Les conditions préalables : peuvent porter sur des systèmes spécifiques, des configurations ou l’expérience des testeurs.
* Les étapes à suivre à un niveau de détail approprié.
* Les résultats attendus.
* Des critères clairs en matière de réussite ou d’échec.

L’idée d’automatiser les cas de test est évidemment intéressante car on peut ainsi éliminer les tâches répétitives.

## Tests manuels ou tests automatisés {#manual-versus-automated-tests}

Cependant, l’automatisation des cas de test est un lourd investissement. Il faut donc prendre en compte certains aspects :

* Demande du temps, des efforts et de l’expérience pour l’installation et la configuration.
* Si les tests sont basés sur un navigateur, il existe un risque accru que des problèmes surviennent au moment où les mises à jour du navigateur sont installées. Il faut donc plus de temps pour le débogage.
* Réellement réalisable pour les projets de grande taille seulement.
* Intéressant si plusieurs versions sont générées pour les tests ou dans le plan de diffusion de versions à long terme.

## Test d’aspects spécifiques {#testing-specific-aspects}

Lors du test d’AEM, certains détails sont particulièrement intéressants :

Environnements de création et de publication

Bien que le sujet soit traité dans [Environnements](/help/sites-developing/the-basics.md#environments), il convient de souligner un facteur déterminant dans AEM pour ce qui concerne les choix de types de tests.

Vous devez traiter AEM comme s’il s’agissait de deux applications séparées :

* L’environnement **Auteur**
Cette instance permet aux auteurs de saisir et de publier du contenu.
Elle comporte un plus petit nombre prévisible d’utilisateurs, pour qui des fonctionnalités et des performances spécifiques sont indispensables.
* l’environnement de **publication**

Cette instance affiche le site web sous sa forme publiée pour que les visiteurs puissent y accéder.
Elle comporte généralement un plus grand nombre d’utilisateurs pour lequel le volume de trafic n’est pas toujours prévisible à 100 %. La performance est toujours cruciale lors de la réponse aux demandes. La mise en cache et l’équilibrage de charge doivent également être pris en compte.

Bien qu’il s’agisse du même logiciel, les deux instances :

* ont une finalité différente
* sont associées à des exigences différentes en ce qui concerne les fonctionnalités et les performances
* sont configurées différemment
* sont paramétrées séparément
* comportent chacune leur propre ensemble de tests d’acceptation

En d’autres termes, elles doivent être testées séparément et avec différents cas de test.

**Personnalisation**

Lors du test de personnalisation, chaque cas d’utilisation doit être répété en utilisant plusieurs comptes d’utilisateurs pour prouver le comportement.

La mise en cache doit également être vérifiée pour déterminer si son comportement est normal.

**Le Dispatcher**

La plupart des projets installent le dispatcher pour la mise en cache et l’équilibrage de charge.

Les tests sont difficiles (la mise en cache se fait à différents niveaux et à divers endroits) et doivent être réalisés en boîte noire. Les aspects clés à tester sont les suivants :

* **Précision**; s’assurer que les mises à jour du contenu sont visibles par le visiteur du site web.
* **Continuité**; vérifiez que le site web est toujours disponible lorsqu’un serveur est arrêté.
* **Clusters**
Les clusters sont utilisés pour garantir :
   * **Basculement**
Si un serveur tombe en panne, les autres serveurs du cluster prennent le relais.
   * **Performances**
L’équilibrage de charge avec basculement intégral améliore les performances d’un cluster.

Lorsqu’il est utilisé pour un projet client, le cluster doit être testé pour confirmer le bon fonctionnement de la configuration.

## Test de logiciels tiers {#testing-third-party-software}

Tout logiciel tiers associé à l’interface d’AEM est référencé dans le cahier des charges détaillé.

Il faut analyser tous les tests nécessaires (en fonction de la portée définie) et obtenir des résultats satisfaisants.
