---
title: Définition de cas de test
seo-title: Définition de cas de test
description: Vos cas de test doivent être basés sur des cas d’utilisation et le cahier des charges détaillé
seo-description: Vos cas de test doivent être basés sur des cas d’utilisation et le cahier des charges détaillé
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
translation-type: tm+mt
source-git-commit: 0edddfde1e66ec487139f98e9ffafee885e61dfd
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 77%

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

## Test d&#39;aspects spécifiques {#testing-specific-aspects}

Lors des tests AEM quelques détails spécifiques présentent un intérêt particulier :

Environnements de création et de publication

Although, covered in [Environments](/help/sites-developing/the-basics.md#environments) it is worth highlighting a deciding factor of AEM with regard to testing.

Vous devez considérer AEM comme deux applications :

* l’environnement **Auteur** Cette instance permet aux auteurs d’entrer et de publier du contenu.
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

**Le dispatcher**

La plupart des projets installent le dispatcher pour la mise en cache et l’équilibrage de charge.

Les tests sont difficiles (la mise en cache se fait à différents niveaux et à divers endroits) et doivent être réalisés en boîte noire. Les aspects clés à tester sont les suivants :

* **Précision**; s’assurer que les mises à jour de contenu sont affichées par le visiteur du site Web.
* **la continuité**; assurez-vous que le site Web est toujours disponible lorsqu’un serveur est arrêté.
* **Les grappes** Les grappes servent à :
   * **Basculement** en panne d’un serveur, les autres serveurs de la grappe prennent le relais du traitement.
   * **L’équilibrage des performances** de charge avec basculement complet augmente les performances d’une grappe.

Lorsqu’il est utilisé pour un projet client, le cluster doit être testé pour confirmer le bon fonctionnement de la configuration.

## Test de logiciels tiers {#testing-third-party-software}

Tout logiciel tiers relié à AEM sera référencé dans les Spécifications détaillées des besoins.

Il faut analyser tous les tests nécessaires (en fonction de la portée définie) et obtenir des résultats satisfaisants.
