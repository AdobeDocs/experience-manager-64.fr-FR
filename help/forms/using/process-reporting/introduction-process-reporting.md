---
title: Présentation des rapports de processus
seo-title: Introduction to Process Reporting
description: Présentation et principales fonctionnalités des rapports de processus d’AEM Forms on JEE
seo-description: Introduction and key capabilities of AEM Forms on JEE Process Reporting
uuid: a33ea729-7e1f-4093-bdb6-b8dc3afd59a7
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0cfe62b8-839e-414b-95e5-1bfce6a9d16a
exl-id: 279b2f89-5b91-4b8f-ab0f-8ade9b9f3932
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Présentation des rapports de processus {#introduction-to-process-reporting}

![process-reporting](assets/process-reporting.png)

Process Reporting est un outil de navigateur que vous utilisez pour créer et afficher des rapports sur les processus et tâches AEM Forms.

La création de rapports de processus fournit un ensemble de rapports d’usine qui vous permettent de filtrer, d’afficher des informations sur les processus à long terme, la durée de processus et le volume de workflow.

De plus, Process Reporting fournit une interface permettant d’exécuter des requêtes ad hoc et d’intégrer des vues de rapports personnalisées dans l’interface utilisateur Process Reporting.

Pour obtenir la liste des navigateurs pris en charge, voir [Plateformes prises en charge par AEM Forms](/help/forms/using/aem-forms-jee-supported-platforms.md).

Les rapports de processus sont construits sur des modules qui :

* Lire les données de processus de la base de données AEM Forms
* Publication de données de processus dans un référentiel de création de rapports de processus incorporé
* Fournit une interface utilisateur de navigateur pour afficher les rapports.

## Fonctionnalités clés {#key-capabilities}

### Création de rapports permanents {#always-on-reporting}

![gestion de site](assets/site-management.png)

Affichez la liste des processus à long terme, des graphiques de durée de processus et exécutez des requêtes personnalisées à l’aide de filtres.

Les rapports de processus offrent également la possibilité d’exporter le rapport et les données de requête au format CSV.

### Rapports ad hoc {#adhoc-reports}

![print-&amp;-color](assets/print-&-colour.png)

Utilisez des filtres pour obtenir une vue spécifique de vos données.

Vous pouvez rechercher des processus ou des tâches par identifiant, durée, dates de début et de fin, initiateur de processus, etc.

Vous pouvez combiner plusieurs filtres pour créer des rapports spécifiques.

Vous pouvez ensuite enregistrer les filtres de rapport pour les exécuter à une date ou une heure ultérieure.

### Historique des processus/tâches {#process-task-history}

![gestion de fichiers](assets/file-management.png)

Les serveurs AEM Forms exécutent de nombreux processus en parallèle. Ces processus continuent de passer d’un état à un autre. En publiant des données Forms dans le référentiel Process Reporting à intervalles réguliers, Process Reporting conserve les informations de transition sur les processus en cours d’exécution dans AEM Forms.

### Contrôle d’accès {#access-control-br}

![sans titre](assets/untitled.png)

La création de rapports sur les processus permet d’accéder à l’interface utilisateur en fonction des autorisations.

Cela signifie que seuls les utilisateurs disposant d’autorisations de création de rapports ont accès à l’interface utilisateur Process Reporting.
