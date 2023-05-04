---
title: Présentation de Health Monitor
seo-title: Overview of Health Monitor
description: Ce document présente l’aperçu du moniteur d’intégrité et fournit des détails sur la manière dont vous pouvez y accéder.
seo-description: This document provides the overview of the Health monitor, and details about how you can access it.
uuid: 5934fd2d-80a5-4c6d-b3ee-882c2865705b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c303e967-944d-40b0-96ca-f91e2f42a0d0
exl-id: 70ccc0ae-04c6-4af9-9150-72d0d71c945f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 4%

---

# Présentation de Health Monitor {#overview-of-health-monitor}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Health Monitor fournit des informations critiques sur le système d’AEM forms, telles que des informations sur le serveur, l’utilisation de la mémoire et l’utilisation du processeur. Vous pouvez également accéder aux statistiques de Work Manager, telles que le nombre de tâches dans la file d’attente et leur état. Vous pouvez effectuer les tâches suivantes à l’aide de Health Monitor :

* Vérifiez que votre système fonctionne correctement.
* Affichage des informations pour aider à diagnostiquer les problèmes système au fur et à mesure qu’ils se produisent
* Exécution d’opérations sur des tâches présentant des problèmes
* Purge des enregistrements obsolètes de la base de données de Job Manager

La page Health Monitor d’Administration Console comporte trois onglets :

* L’onglet Système affiche des graphiques de surveillance des ressources et des informations sur le serveur Forms (ou le noeud dans un environnement organisé en grappes). (Voir [Affichage des informations du système](/help/forms/using/admin-help/view-system-information.md#view-system-information).)
* L’onglet Work Manager affiche les données liées à Work Manager, telles que le nombre de tâches dans la file d’attente de Work Manager. Vous pouvez filtrer les informations à l’aide de différents critères ou gérer des tâches individuelles à l’aide des outils d’opération. (Voir [Affichage des statistiques relatives à Work Manager](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).)
* L’onglet Planificateur de purge de tâche permet de purger les enregistrements obsolètes de la base de données de Job Manager. (Voir [Purge des enregistrements de la base de données de Job Manager](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)

La page web Health Monitor est renseignée avec les statistiques collectées via une API Gemfire. Cette API détecte automatiquement tous les noeuds d’une grappe. Elle résout également les problèmes de sécurité qui se produisent lors de la collecte de statistiques depuis des serveurs proxy ou des équilibreurs de charge. Des options Java sont disponibles pour affiner Health Monitor, réduisant ainsi l’impact sur les performances de votre environnement AEM forms. (Voir [Réglage précis des performances de Health Monitor](/help/forms/using/admin-help/fine-tuning-health-monitor-performance.md#fine-tuning-health-monitor-performance).)

**Accès à Health Monitor**

1. Dans Administration Console, cliquez sur Health Monitor dans le coin supérieur droit de la page.
