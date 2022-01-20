---
title: Rapports prédéfinis dans les rapports de processus
seo-title: Pre-defined reports in Process Reporting
description: Requête pour les données de processus AEM Forms on JEE afin de créer des rapports sur les processus à long terme, la durée du processus et le volume de processus.
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# Rapports prédéfinis dans les rapports de processus {#pre-defined-reports-in-process-reporting}

La création de rapports de processus AEM Forms est fournie avec les éléments suivants : *d&#39;usine* rapports :

* **[Processus à long terme](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**: Rapport de tous les processus AEM Forms dont l’exécution a pris plus d’un temps spécifié

* **[Graphique de durée du processus](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**: Rapport d’un processus AEM Forms spécifié par la durée

* **[Volume de workflow](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**: Rapport des instances en cours d’exécution et terminées du processus spécifié par date

## Processus à long terme {#long-running-processes}

Le rapport Long Running Processes affiche les processus AEM Forms dont l’exécution a pris plus d’un temps spécifié.

### Pour exécuter un rapport de processus à long terme {#to-execute-a-long-running-process-report-br}

1. Pour afficher la liste des rapports prédéfinis dans les rapports de processus, sur la page **Rapports de processus** arborescence, cliquez sur **Rapports** noeud .
1. Cliquez sur le bouton **Processus à long terme** noeud du rapport.

   ![long_running_node](assets/long_running_node.png)

   Lorsque vous sélectionnez un rapport, la variable **Paramètres des rapports** s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/report_parameters_panel.png)

   Paramètres:

   * **Durée**(*mandatory*) : Spécifiez une durée et une unité de temps. Affichez tous les processus AEM Forms qui ont été exécutés pendant plus de la durée spécifiée.
   * **Démarré après** (*facultatif*) : Sélectionnez une date. Filtrez le rapport pour afficher les instances de processus démarrées après la date spécifiée.
   * **Démarré avant** (*facultatif*) : Sélectionnez une date. Filtrez le rapport pour afficher les instances de processus qui ont démarré avant la date spécifiée.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans la variable **Rapport** panneau à droite du panneau **Rapports de processus** fenêtre.

   ![long_running_processes](assets/long_running_processes.png)

   Utilisez les options situées dans le coin supérieur droit du **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser**: Actualise le rapport avec les dernières données stockées
   * **Changer la couleur de la légende**: Sélectionner et modifier la couleur de la légende du rapport
   * **Exportation au format CSV**: Exporter et télécharger les données du rapport dans un fichier séparé par des virgules

## Rapport Durée du processus {#process-duration-report-br}

Le rapport Durée du processus affiche le nombre d’instances d’un processus Forms par nombre de jours d’exécution de chaque instance.

### Pour exécuter un rapport Durée du processus {#to-execute-a-process-duration-report-br}

1. Pour afficher les rapports prédéfinis dans les rapports de processus, sur la page **Rapports de processus** arborescence, cliquez sur **Rapports** noeud .
1. Cliquez sur le bouton **Durée des processus** noeud du rapport.

   ![process_duration_node](assets/process_duration_node.png)

   Lorsque vous sélectionnez un rapport, la variable **Paramètres des rapports** s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/process_duration_params.png)

   Paramètres:

   * **Select Process** (*mandatory*) : Sélectionnez un processus AEM Forms.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans la variable **Rapport** à droite de la fenêtre Process Reporting.

   ![process_duration_report](assets/process_duration_report.png)

   Utilisez les options situées dans le coin supérieur droit du **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser**: Actualise le rapport avec les dernières données stockées
   * **Changer la couleur de la légende**: Sélectionner et modifier la couleur de la légende du rapport
   * **Exportation au format CSV**: Exporter et télécharger les données du rapport dans un fichier séparé par des virgules

## Rapport Volume de workflow {#workflow-volume-report}

Le rapport Volume de workflow affiche le nombre d’instances en cours d’exécution et terminées d’un processus AEM Forms par jour calendaire.

### Pour exécuter un rapport Volume de workflow {#to-execute-a-workflow-volume-report-br}

1. Pour afficher les rapports prédéfinis dans les rapports de processus, sur la page **Rapports de processus** arborescence, cliquez sur **Rapports** noeud .
1. Cliquez sur le bouton **Volume de workflow** noeud du rapport.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Lorsque vous sélectionnez un rapport, la variable **Paramètres des rapports** s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/workflow_volume_params.png)

   Paramètres:

   * **Select Process**(*mandatory*) : Sélectionnez un processus AEM Forms.
   * **Démarré après** (*facultatif*) : Sélectionnez une date. Filtre le rapport afin d’afficher les instances de processus démarrées après la date spécifiée.
   * **Démarré avant** (*facultatif*) : Sélectionnez une date. Filtre le rapport pour afficher les instances de processus qui ont démarré avant la date spécifiée.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans la variable **Rapport** panneau à droite du panneau **Rapports de processus** fenêtre.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Utilisez les options situées dans le coin supérieur droit du **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser**: Actualise le rapport avec les dernières données stockées
   * **Changer la couleur de la légende**: Sélectionner et modifier la couleur de la légende du rapport
   * **Exportation au format CSV**: Exporter et télécharger les données du rapport dans un fichier séparé par des virgules
