---
title: Outils de test et de suivi
seo-title: Testing and Tracking Tools
description: AEM fournit une structure pour le test de l’interface utilisateur des composants et un mécanisme pour le test et le débogage des composants.
seo-description: AEM provides a framework for testing component UI and a mechanism for testing and debugging components
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
exl-id: 9387cdb4-f8de-4229-90d1-59218ac17561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 14%

---

# Outils de test et de suivi{#testing-and-tracking-tools}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Tests {#testing}

AEM fournit :

* [Un framework pour tester l’interface utilisateur des composants](/help/sites-developing/hobbes.md).
* [un mécanisme de test et de débogage des composants ;](/help/sites-developing/developer-mode.md).

Voici deux outils de test Open Source :

**Selenium**

Selenium est utilisé pour le test des fonctions dans un navigateur avec un utilisateur par activité. Il enregistre les étapes de test (clics) sous la forme de tables de HTML ou de classes Java.

Pour plus d’informations, consultez [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter est utilisé pour effectuer le suivi des demandes et peut être utilisé pour les tests fonctionnels, de performance et de stress.

Pour plus d’informations, voir [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

Il existe également de nombreux outils propriétaires pour automatiser les tests et gérer les plans de test.

## Tracking {#tracking}

Les outils suivants sont facilement disponibles. Cependant, un problème clé dans tous les cas est la disponibilité des données pour tous les membres de l’équipe du projet - partenaire et client.

**Bugzilla**

Système de suivi des bogues qui peut être configuré selon vos besoins.

**Feuilles de calcul**

Bien qu’il ne s’agisse pas spécifiquement d’un outil de suivi des bogues, les feuilles de calcul sont souvent utilisées à mauvais escient à cette fin, car elles sont faciles à comprendre et la plupart des utilisateurs connaissent leurs fonctionnalités.

Si elles sont utilisées pour le suivi, alors :

* ils devraient être simples.
* le nombre de feuilles de calcul individuelles doit être limité au minimum.
* ils doivent être mis à jour régulièrement.
* une seule copie originale doit être conservée et tout le monde doit savoir où se trouve la copie originale.
* ils doivent être accessibles à tous les membres du projet.
* si la sécurité est un problème (qui se produit souvent dans les grandes entreprises) et qu’un accès commun n’est pas possible, les copies peuvent être distribuées tant que tout le monde comprend qu’il s’agit de copies et qu’elles ne peuvent pas être mises à jour.

Pour rappel, il existe de nombreux outils propriétaires pour effectuer le suivi des bogues et des fonctionnalités demandées.
