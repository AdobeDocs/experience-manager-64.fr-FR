---
title: Rapports prédéfinis dans le Rapports de processus
seo-title: Rapports prédéfinis dans le Rapports de processus
description: Requête des données de processus d’AEM Forms on JEE pour créer des rapports sur les processus à long terme, la durée du processus et le volume de flux de travail
seo-description: Requête des données de processus d’AEM Forms on JEE pour créer des rapports sur les processus à long terme, la durée du processus et le volume de flux de travail
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
translation-type: tm+mt
source-git-commit: 79dcf6816e1156604c0c9279b727ea436ad1826a
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# Rapports prédéfinis dans le Rapports de processus {#pre-defined-reports-in-process-reporting}

Le Rapports de processus AEM Forms est livré avec les rapports *prêts à l’emploi* suivants :

* **[Processus](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)** à long terme : Rapport de tous les processus AEM Forms dont l’exécution a pris plus d’un temps spécifié

* **[Graphique](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)** de durée du processus : Rapport d’un processus AEM Forms spécifié par durée

* **[Volume](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)** de flux de travaux : Rapport des instances en cours d’exécution et terminées d’un processus spécifié par date

## Processus à long terme {#long-running-processes}

Le rapport Processus à long terme affiche les processus AEM Forms dont l’exécution a pris plus d’un temps spécifié.

### Pour exécuter un rapport de processus à long terme {#to-execute-a-long-running-process-report-br}

1. Pour vue de la liste des rapports prédéfinis dans le Rapports de processus, sur la vue de l&#39;arborescence **Rapports de processus**, cliquez sur le noeud **Rapports**.
1. Cliquez sur le noeud de rapport **Processus à long terme**.

   ![long_running_node](assets/long_running_node.png)

   Lorsque vous sélectionnez un rapport, le panneau **Paramètres du rapport** s&#39;affiche à droite de la vue de l&#39;arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/report_parameters_panel.png)

   Paramètres:

   * **Durée** (*obligatoire*) : Spécifiez une durée et une unité de temps. Affichez tous les processus AEM Forms qui ont été exécutés pendant plus de la durée spécifiée.
   * **Démarré après**  (*facultatif*) : Sélectionnez une date. Filtrez le rapport pour afficher les instances de processus démarrées après la date spécifiée.
   * **Démarré avant**  (*facultatif*) : Sélectionnez une date. Filtrez le rapport pour afficher les instances de processus démarrées avant la date spécifiée.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport** à droite de la fenêtre **Rapports de processus**.

   ![long_running_processes](assets/long_running_processes.png)

   Utilisez les options situées dans le coin supérieur droit du panneau **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser** : Actualise le rapport avec les dernières données stockées dans l&#39;enregistrement
   * **Modifier la couleur** de la légende : Sélectionner et modifier la couleur de la légende du rapport
   * **Exporter au format CSV** : Exportez et téléchargez les données du rapport dans un fichier séparé par des virgules.

## Rapport Durée du processus {#process-duration-report-br}

Le rapport Durée du processus affiche le nombre d’instances d’un processus Forms par nombre de jours d’exécution de chaque instance.

### Pour exécuter un rapport Durée du processus {#to-execute-a-process-duration-report-br}

1. Pour vue des rapports prédéfinis dans le Rapports de processus, sur la vue **Rapports de processus** de l&#39;arborescence, cliquez sur le noeud **Rapports**.
1. Cliquez sur le noeud de rapport **Durée des processus**.

   ![process_duration_node](assets/process_duration_node.png)

   Lorsque vous sélectionnez un rapport, le panneau **Paramètres du rapport** s&#39;affiche à droite de la vue de l&#39;arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/process_duration_params.png)

   Paramètres:

   * **Sélectionnez Processus**  (*obligatoire*) : Sélectionnez un processus AEM Forms.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport** à droite de la fenêtre Rapports de processus.

   ![process_duration_report](assets/process_duration_report.png)

   Utilisez les options situées dans le coin supérieur droit du panneau **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser** : Actualise le rapport avec les dernières données stockées dans l&#39;enregistrement
   * **Modifier la couleur** de la légende : Sélectionner et modifier la couleur de la légende du rapport
   * **Exporter au format CSV** : Exportez et téléchargez les données du rapport dans un fichier séparé par des virgules.

## Rapport Volume de flux de travail {#workflow-volume-report}

Le rapport Volume de flux de travail affiche le nombre d’instances en cours d’exécution et terminées d’un processus AEM Forms par jour calendaire.

### Pour exécuter un rapport Volume de flux de travail {#to-execute-a-workflow-volume-report-br}

1. Pour vue des rapports prédéfinis dans le Rapports de processus, sur la vue **Rapports de processus** de l&#39;arborescence, cliquez sur le noeud **Rapports**.
1. Cliquez sur le noeud de rapport **Volume de flux de travail**.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Lorsque vous sélectionnez un rapport, le panneau **Paramètres du rapport** s&#39;affiche à droite de la vue de l&#39;arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/workflow_volume_params.png)

   Paramètres:

   * **Sélectionnez Processus** (*obligatoire*) : Sélectionnez un processus AEM Forms.
   * **Démarré après**  (*facultatif*) : Sélectionnez une date. Filtres le rapport pour afficher les instances de processus qui ont commencé après la date spécifiée.
   * **Démarré avant**  (*facultatif*) : Sélectionnez une date. Filtres le rapport pour afficher les instances de processus qui ont commencé avant la date spécifiée.

1. Cliquez sur **Aller** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport** à droite de la fenêtre **Rapports de processus**.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Utilisez les options situées dans le coin supérieur droit du panneau **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser** : Actualise le rapport avec les dernières données stockées dans l&#39;enregistrement
   * **Modifier la couleur** de la légende : Sélectionner et modifier la couleur de la légende du rapport
   * **Exporter au format CSV** : Exportez et téléchargez les données du rapport dans un fichier séparé par des virgules.

