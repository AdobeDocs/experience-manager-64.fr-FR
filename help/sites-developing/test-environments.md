---
title: Quels environnements de test sont nécessaires ?
seo-title: Which Test Environments are needed?
description: Plusieurs environnements doivent être pris en compte dans le cadre du test.
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 47%

---

# Quels environnements de test sont nécessaires ?{#which-test-environments-will-be-needed}

Pour définir les configurations à tester, tenez compte des points suivants :

**Développement** - pour l’unité et certains tests d’intégration.

**Tests** - Pour la majorité des tests.

**En direct** - Pour les tests de performance et de stress finaux. Également pour les tests d’acceptation avec le client.

Vous devez également déterminer les instances dont vous aurez besoin et leur emplacement (généralement au moins un de chaque pour tous les niveaux de test) :

**Auteur** - Cette instance permet aux auteurs de saisir et de publier du contenu.

**Publier** - Cette instance présente le site web sous sa forme publiée pour l’accès des visiteurs.

Elle devrait être testée conjointement au dispatcher.

Enfin, le matériel doit être pris en compte : tous les tests de performance doivent être effectués sur un système aussi proche que possible de la configuration de l’environnement actif final. Pour cette raison, nous vous recommandons également de diviser le lancement du projet de la façon suivante :

**Soft Launch** - Une disponibilité réduite ; qui permet de gagner du temps pour les tests de performance, l’optimisation et l’optimisation dans des conditions réalistes dans l’environnement de production.

**Hard Launch** - Disponibilité complète.
