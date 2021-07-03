---
title: Configurez les opérations asynchrones dans  [!DNL Adobe Experience Manager].
description: Effectuez de manière asynchrone certaines tâches gourmandes en ressources afin d’optimiser les performances dans  [!DNL Experience Manager Assets].
contentOwner: AG
feature: Gestion des ressources
role: User
exl-id: 0abdfe87-d932-41dd-b1e6-9f5fa5b924fe
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 19%

---

# Opérations asynchrones {#asynchronous-operations}

Pour réduire l’impact négatif sur les performances, [!DNL Adobe Experience Manger Assets] traite de manière asynchrone certaines opérations de ressources longues et gourmandes en ressources. Le traitement asynchrone implique de mettre plusieurs tâches en file d’attente et de les exécuter en série selon la disponibilité des ressources système. Ces opérations incluent :

* Suppression de nombreuses ressources.
* Déplacement de nombreuses ressources ou de ressources avec de nombreuses références.
* Exportation et importation de métadonnées de ressources en bloc.

Vous pouvez afficher l’état des tâches asynchrones à partir de la page **[!UICONTROL État des tâches asynchrones]** .

>[!NOTE]
>
>Par défaut, les tâches [!DNL Assets] s’exécutent en parallèle. Si `N` correspond au nombre de coeurs de processeur, les tâches `N/2` peuvent s’exécuter en parallèle, par défaut. Pour utiliser des paramètres personnalisés pour la file d’attente des tâches, modifiez la configuration **[!UICONTROL File d’attente par défaut des opérations asynchrones]** à partir de la [!UICONTROL console web]. Pour plus d’informations, voir [Configurations de files d’attente](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Surveillance de l’état des opérations asynchrones {#monitoring-the-status-of-asynchronous-operations}

Chaque fois que [!DNL Assets] traite une opération de manière asynchrone, vous recevez une notification dans votre [!DNL Experience Manager] [boîte de réception](/help/sites-authoring/inbox.md) et par courrier électronique. Pour afficher l’état des opérations asynchrones en détail, accédez à la page **[!UICONTROL État des tâches asynchrones]**.

1. Dans l’interface [!DNL Experience Manager], cliquez sur **[!UICONTROL Opérations]** > **[!UICONTROL Tâches]**.

1. Sur la page **[!UICONTROL État des tâches asynchrones]**, passez en revue les détails des opérations.

   ![État et détails des opérations asynchrones](assets/job_status.png)

   Pour vérifier la progression d’une opération, voir la colonne **[!UICONTROL État]**. Selon la progression, l’un des états suivants s’affiche :

   * **[!UICONTROL Actif]** : l’opération est en cours de traitement..
   * **[!UICONTROL Succès]** : L’opération est terminée.
   * **** Erreur  **[!UICONTROL de l’échec]** : L’opération n’a pas pu être traitée.
   * **[!UICONTROL Planifié]** : L’opération est planifiée à une date ultérieure.

1. Pour arrêter une opération principale, sélectionnez-la dans la liste et cliquez sur **[!UICONTROL Arrêter]** ![Icône d’arrêt](assets/do-not-localize/stop_icon.svg) dans la barre d’outils.

1. Pour afficher des détails supplémentaires, par exemple la description et les journaux, sélectionnez l’opération, puis cliquez sur **[!UICONTROL Ouvrir]** ![open_icon](assets/do-not-localize/edit_icon.svg) dans la barre d’outils. La page Détails de la tâche s’affiche.

   ![Détails d’une tâche d’importation de métadonnées](assets/job_details.png)

1. Pour supprimer l’opération de la liste, sélectionnez **[!UICONTROL Supprimer]** dans la barre d’outils. Pour télécharger les détails dans un fichier CSV, cliquez sur **[!UICONTROL Télécharger]**.

   >[!NOTE]
   >
   >Vous ne pouvez pas supprimer une tâche si son état est principal ou en file d’attente.

## Purge des tâches terminées {#purge-completed-tasks}

[!DNL Experience Manager Assets] exécute une tâche de purge tous les jours à 10 h pour supprimer les tâches asynchrones terminées depuis plus d’un jour.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

Vous pouvez modifier le planning de la tâche de purge et la durée pendant laquelle les détails des tâches terminées sont conservés avant d’être supprimés. Vous pouvez également configurer le nombre maximal de tâches terminées pour lesquelles les détails sont conservés à tout moment.

1. Dans l’interface [!DNL Experience Manager], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Console web]**.
1. Ouvrez la tâche **[!UICONTROL Purge des tâches asynchrones de la gestion des actifs numériques Adobe CQ planifiée]** .
1. Indiquez le nombre seuil de jours après lequel les tâches terminées sont supprimées et le nombre maximal de tâches pour lesquelles les détails sont conservés dans l’historique. Enregistrez les modifications.

   ![Configuration pour planifier la purge des tâches asynchrones](assets/purge_job.png)

## Configuration du seuil pour les opérations de suppression asynchrones {#configure-thresholds-for-asynchronous-delete-operations}

Si le nombre de ressources ou de dossiers à supprimer dépasse le nombre seuil défini, l’opération de suppression est effectuée de manière asynchrone.

1. Dans l’interface [!DNL Experience Manager], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Console web]**.
1. Dans la [!UICONTROL console web], ouvrez la configuration **[!UICONTROL Traitement des tâches des opérations de suppression asynchrones]**.
1. Dans la zone **[!UICONTROL Nombre seuil de ressources]**, spécifiez les nombres seuil pour supprimer de manière asynchrone des ressources, dossiers ou références. Enregistrez les modifications.

   ![Définition de la limite de seuil pour la tâche de suppression des ressources](assets/delete_threshold.png)

## Configuration du seuil pour les opérations de déplacement asynchrones {#configure-thresholds-for-asynchronous-move-operations}

Si le nombre de ressources, dossiers ou références à déplacer dépasse le nombre seuil défini, l’opération de déplacement est effectuée de manière asynchrone.

1. Dans l’interface [!DNL Experience Manager], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Console web]**.
1. Dans la [!UICONTROL console web], ouvrez la configuration **[!UICONTROL Traitement des tâches des opérations de déplacement asynchrones]**.
1. Dans la zone **[!UICONTROL Nombre seuil de ressources/références]**, spécifiez les nombres seuil pour déplacer de manière asynchrone les ressources, dossiers ou références. Enregistrez les modifications.

   ![Définition de la limite de seuil pour la tâche de déplacement des ressources](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Configurez le courrier électronique dans Experience Manager](/help/sites-administering/notification.md).
>* [Importation et exportation des métadonnées de ressources par lot](/help/assets/metadata-import-export.md).

