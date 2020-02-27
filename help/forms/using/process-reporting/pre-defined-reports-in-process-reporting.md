---
title: Rapports prédéfinis dans Process Reporting
seo-title: Rapports prédéfinis dans Process Reporting
description: Requête pour les données de processus d’AEM Forms sur JEE afin de créer des rapports sur les processus à long terme, la durée du processus et le volume de flux de travail
seo-description: Requête pour les données de processus d’AEM Forms sur JEE afin de créer des rapports sur les processus à long terme, la durée du processus et le volume de flux de travail
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
translation-type: tm+mt
source-git-commit: ec74a1c3b1d3686a1f5216e06dfc33dc1dccfb2f

---


# Rapports prédéfinis dans Process Reporting {#pre-defined-reports-in-process-reporting}

Les rapports de processus AEM Forms sont livrés avec les rapports *prêts à l’emploi* suivants :

* **[Processus](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**à long terme : Rapport de tous les processus AEM Forms qui ont pris plus d’une durée spécifiée à terminer

* **[Graphique](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**de durée du processus : Rapport d’un processus AEM Forms spécifié par durée

* **[Volume](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**du flux de travail : Rapport des instances en cours d’exécution et terminées du processus spécifié par date

## Processus à long terme {#long-running-processes}

Le rapport Processus à long terme affiche les processus AEM Forms qui ont pris plus d’une durée spécifiée pour être terminés.

### Pour exécuter un rapport Processus à long terme {#to-execute-a-long-running-process-report-br}

1. Pour afficher la liste des rapports prédéfinis dans Process Reporting, dans l’arborescence **Process Reporting** , cliquez sur le noeud **Reports** .
1. Cliquez sur le noeud de rapport Processus **à** long terme.

   ![long_running_node](assets/long_running_node.png)

   Lorsque vous sélectionnez un rapport, le panneau Paramètres **du** rapport s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/report_parameters_panel.png)

   Paramètres:

   * **Durée**(*obligatoire*) : Spécifiez une durée et une unité de temps. Affichez tous les processus AEM Forms qui ont été exécutés pendant plus de la durée spécifiée.
   * **Démarré après** (*facultatif*) : Sélectionnez une date. Filtrez le rapport pour afficher les instances de processus qui ont commencé après la date spécifiée.
   * **Démarré avant** (*facultatif*) : Sélectionnez une date. Filtrez le rapport pour afficher les instances de processus qui ont commencé avant la date spécifiée.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport **situé à droite de la fenêtre **Process Reporting** .

   ![long_running_processes](assets/long_running_processes.png)

   Utilisez les options dans le coin supérieur droit du panneau **Rapport **pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser**: Actualise le rapport avec les dernières données stockées
   * **Modifier la couleur** de la légende : Sélectionner et modifier la couleur de la légende du rapport
   * **Exporter au format CSV**: Exportez et téléchargez les données du rapport dans un fichier séparé par des virgules.

## Rapport Durée du processus {#process-duration-report-br}

Le rapport Durée du processus affiche le nombre d’instances d’un processus Forms par nombre de jours d’exécution de chaque instance.

### Pour exécuter un rapport Durée du processus {#to-execute-a-process-duration-report-br}

1. Pour afficher les rapports prédéfinis dans Process Reporting, dans l’arborescence **Process Reporting** , cliquez sur le noeud **Reports** .
1. Cliquez sur le noeud de rapport Durée des **processus** .

   ![process_length_node](assets/process_duration_node.png)

   Lorsque vous sélectionnez un rapport, le panneau Paramètres **du** rapport s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/process_duration_params.png)

   Paramètres:

   * **Sélectionnez Processus** (*obligatoire*) : Sélectionnez un processus AEM Forms.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport** à droite de la fenêtre Process Reporting.

   ![process_length_report](assets/process_duration_report.png)

   Utilisez les options situées dans le coin supérieur droit du panneau **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser**: Actualise le rapport avec les dernières données stockées
   * **Modifier la couleur** de la légende : Sélectionner et modifier la couleur de la légende du rapport
   * **Exporter au format CSV**: Exportez et téléchargez les données du rapport dans un fichier séparé par des virgules.

## Rapport Volume du flux de travail {#workflow-volume-report}

Le rapport Volume de processus affiche le nombre d’instances en cours d’exécution et terminées d’un processus AEM Forms par jour calendaire.

### Pour exécuter un rapport Volume de flux de travail {#to-execute-a-workflow-volume-report-br}

1. Pour afficher les rapports prédéfinis dans Process Reporting, dans l’arborescence **Process Reporting** , cliquez sur le noeud **Reports** .
1. Cliquez sur le noeud de rapport Volume **de** processus.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Lorsque vous sélectionnez un rapport, le panneau Paramètres **du** rapport s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/workflow_volume_params.png)

   Paramètres:

   * **Sélectionnez Processus**(*obligatoire*) : Sélectionnez un processus AEM Forms.
   * **Démarré après** (*facultatif*) : Sélectionnez une date. Filtre le rapport pour afficher les instances de processus qui ont commencé après la date spécifiée.
   * **Démarré avant** (*facultatif*) : Sélectionnez une date. Filtre le rapport pour afficher les instances de processus qui ont commencé avant la date spécifiée.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport** à droite de la fenêtre Rapport **de** processus.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Utilisez les options situées dans le coin supérieur droit du panneau **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser**: Actualise le rapport avec les dernières données stockées
   * **Modifier la couleur** de la légende : Sélectionner et modifier la couleur de la légende du rapport
   * **Exporter au format CSV**: Exportez et téléchargez les données du rapport dans un fichier séparé par des virgules.

[Contacter le support technique](https://www.adobe.com/account/sign-in.supportportal.html)
