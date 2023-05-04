---
title: Définir vos cas de test
seo-title: Defining your Test Cases
description: Vos cas de test doivent être basés sur les cas d’utilisation et la spécification des exigences détaillées.
seo-description: Your test cases should be based upon the use cases and the detailed requirements specification
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
exl-id: ad529be3-9d31-492f-943f-ef3e99e13586
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 38%

---

# Définir vos cas de test{#defining-your-test-cases}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vos cas de test doivent être basés sur les éléments suivants :

**Cas d’utilisation**

* Ces fonctions définissent les fonctionnalités requises en termes d’interaction entre les acteurs (rôles qui déclenchent certaines actions) et le système.
* Les cas d’utilisation doivent être définis par le client.

**Spécification détaillée des exigences**

* Toutes les exigences fonctionnelles et de performance doivent être testées.

Les tests doivent définir clairement :

* les conditions préalables; il peut s’agir de systèmes, de configurations ou d’expériences de test spécifiques.
* les étapes à suivre; à un niveau de détail approprié.
* Résultats attendus.
* Des critères clairs pour réussir ou échouer.

La perspective d’automatiser les cas de test est évidemment attrayante, car elle peut éliminer les tâches répétitives.

## Tests manuels ou automatisés {#manual-versus-automated-tests}

L’automatisation des cas de test constitue toutefois un investissement important. Il convient donc de prendre en compte certains aspects :

* Requiert du temps, des efforts et de l’expérience pour la configuration et la configuration.
* Si le navigateur est basé sur un navigateur, le risque de problèmes augmente lorsque les mises à jour du navigateur sont installées ; nécessite davantage de temps pour corriger.
* Seulement vraiment faisable pour les grands projets.
* Ceci est utile lorsque plusieurs versions sont générées à des fins de test ou dans le plan de mise à jour à long terme.

## Test d’aspects spécifiques {#testing-specific-aspects}

Lors du test d’AEM, certains détails sont particulièrement intéressants :

Environnements de création et de publication

Bien que le sujet soit traité dans [Environnements](/help/sites-developing/the-basics.md#environments), il convient de souligner un facteur déterminant dans AEM pour ce qui concerne les choix de types de tests.

Vous devez traiter AEM comme s’il s’agissait de deux applications séparées :

* L’environnement **Auteur**
Cette instance permet aux auteurs de saisir et de publier du contenu.
Elle comporte un plus petit nombre prévisible d’utilisateurs et d’utilisatrices, pour qui des fonctionnalités et des performances spécifiques sont indispensables.
* la valeur **Publier** environnement Cette instance présente le site web sous sa forme publiée pour l’accès des visiteurs.
Elle comporte généralement un plus grand nombre d’utilisateurs pour lequel le volume de trafic n’est pas toujours prévisible à 100 %. La performance est toujours cruciale lors de la réponse aux demandes. La mise en cache et l’équilibrage de charge doivent également être pris en compte.

Bien que le même logiciel soit utilisé, ils :

* servir différents objectifs ;
* ont des exigences différentes en ce qui concerne les fonctionnalités et les performances ;
* sont configurés différemment ;
* sont affinées séparément ;
* ont chacun leur propre jeu de tests d’acceptation ;

En d’autres termes, ils doivent être testés séparément et avec des cas de test différents.

**Personnalisation**

Lors du test de la personnalisation, chaque cas d’utilisation doit être répété à l’aide de plusieurs comptes d’utilisateurs afin de prouver son comportement.

La mise en cache doit également être vérifiée pour déterminer le comportement correct.

**Le Dispatcher**

La plupart des projets installent le Dispatcher pour la mise en cache et l’équilibrage de charge.

Les tests sont difficiles (la mise en cache se fait à différents niveaux et à divers endroits) et doivent être réalisés en boîte noire. Les aspects clés à tester sont les suivants :

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
