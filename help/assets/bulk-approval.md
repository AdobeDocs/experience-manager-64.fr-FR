---
title: Révision de collections et de ressources situées dans un dossier
description: Mettez en place des workflows de révision pour les ressources dans un dossier ou une collection et partagez ce workflow avec les réviseurs ou les partenaires de conception afin d’obtenir leurs commentaires.
contentOwner: AG
feature: Collaboration, Collections
role: User
exl-id: 4c62e0cd-eaa5-456e-85f3-06f7a9f160f5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 69%

---

# Révision de collections et de ressources situées dans un dossier {#review-folder-assets-and-collections}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Mettez en place des workflows de révision pour les ressources dans un dossier ou une collection et partagez ce workflow avec les réviseurs ou les partenaires de conception afin d’obtenir leurs commentaires.

Adobe Experience Manager Assets vous permet de configurer un processus de révision ad hoc pour les ressources d’un dossier ou d’une collection, puis de le partager avec des réviseurs ou des partenaires créatifs pour obtenir des commentaires.

Vous pouvez associer le workflow de révision à un projet ou créer une tâche de révision indépendante.

Une fois que vous avez partagé les ressources, les réviseurs peuvent les approuver ou les rejeter. Les notifications sont envoyées à différentes étapes du workflow pour informer les destinataires prévus de l&#39;achèvement de diverses tâches. Par exemple, lorsque vous partagez un dossier ou une collection, le réviseur reçoit une notification lui indiquant qu’un dossier/une collection a été partagé pour la révision.

Une fois que le réviseur a terminé la révision (approuve ou refuse les ressources), vous recevez une notification de fin de révision.

## Création d’une tâche de révision pour des dossiers {#creating-a-review-task-for-folders}

1. Dans l’interface utilisateur Assets, sélectionnez le dossier pour lequel vous souhaitez créer une tâche de révision.
1. Dans la barre d’outils, appuyez/cliquez sur l’icône **[!UICONTROL Créer une tâche de révision]** pour ouvrir la page **[!UICONTROL Tâche de révision]**. Si l’icône n’apparaît pas dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Plus]**, puis sélectionnez l’icône.

   ![chlimage_1-403](assets/chlimage_1-403.png)

1. (Facultatif) Dans la liste **[!UICONTROL Projets]**, choisissez le projet auquel vous voulez associer la tâche de révision. Par défaut, l’option **[!UICONTROL Aucun]** est sélectionnée. Si vous ne souhaitez associer aucun projet à la tâche de révision, conservez cette sélection.

   >[!NOTE]
   >
   >Seuls les projets pour lesquels vous disposez d’autorisations de niveau Éditeur (ou supérieur) sont visibles dans la variable **[!UICONTROL Projets]** liste.

1. Entrez un nom pour la tâche de révision, puis sélectionnez un approbateur dans la liste **[!UICONTROL Affecter à.]**

   >[!NOTE]
   >
   >Les membres/groupes du projet sélectionné sont disponibles en tant qu’approbateurs dans la liste **[!UICONTROL Affecter à.]**

1. Entrez une description, la priorité et la date d’échéance de la tâche de révision.

   ![task_details](assets/task_details.png)

1. Dans l’onglet Avancé, entrez le libellé à utiliser pour créer l’URI.

   ![review_name](assets/review_name.png)

1. Appuyez/cliquez sur **[!UICONTROL Envoyer]**, puis sur **[!UICONTROL Terminé]** pour fermer le message de confirmation. Une notification pour la nouvelle tâche est envoyée à l’approbateur.
1. Connectez-vous à [!DNL Experience Manager] Assets en tant qu’approbateur et accédez à l’interface utilisateur d’Assets. Pour approuver des ressources, cliquez/appuyez sur l’icône **[!UICONTROL Notifications]**, puis sélectionnez la tâche de révision dans la liste.

   ![notification](assets/notification.png)

1. Sur la page **[!UICONTROL Tâche de révision]**, examinez les détails de la tâche de révision, puis appuyez/cliquez sur **[!UICONTROL Réviser]**.
1. Sur la page **[!UICONTROL Tâche de révision]**, sélectionnez les ressources, puis appuyez/cliquez sur l’icône **[!UICONTROL Approuver/Rejeter]** pour approuver ou rejeter, de manière appropriée.

   ![review_task](assets/review_task.png)

1. Appuyez/cliquez sur l’icône **[!UICONTROL Terminé]** dans la barre d’outils. Dans la boîte de dialogue, saisissez un commentaire, puis appuyez/cliquez sur **[!UICONTROL Terminé]** pour confirmer.
1. Accédez à l’interface utilisateur d’Assets et ouvrez le dossier. Les icônes d’état d’approbation des ressources s’affichent en mode Carte et Liste.

   **Mode Carte**

   ![chlimage_1-404](assets/chlimage_1-404.png)

   **Vue Liste**

   ![review_status_listview](assets/review_status_listview.png)

## Création d’une tâche de révision pour les collections {#creating-a-review-task-for-collections}

1. Sur la page Collections, sélectionnez la collection pour laquelle vous souhaitez créer une tâche de révision.
1. Dans la barre d’outils, appuyez/cliquez sur l’icône **[!UICONTROL Créer une tâche de révision]** pour ouvrir la page **[!UICONTROL Tâche de révision]**. Si l’icône n’apparaît pas dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Plus]**, puis sélectionnez l’icône.

   ![chlimage_1-405](assets/chlimage_1-405.png)

1. (Facultatif) Dans la liste **[!UICONTROL Projets]**, choisissez le projet auquel vous voulez associer la tâche de révision. Par défaut, l’option **[!UICONTROL Aucun]** est sélectionnée. Si vous ne souhaitez associer aucun projet à la tâche de révision, conservez cette sélection.

   >[!NOTE]
   >
   >Seuls les projets pour lesquels vous disposez d’autorisations de niveau Éditeur (ou supérieur) sont visibles dans la variable **[!UICONTROL Projets]** liste.

1. Entrez un nom pour la tâche de révision, puis sélectionnez un approbateur dans la liste **[!UICONTROL Affecter à.]**

   >[!NOTE]
   >
   >Les membres/groupes du projet sélectionné sont disponibles en tant qu’approbateurs dans la liste **[!UICONTROL Affecter à.]**

1. Entrez une description, la priorité et la date d’échéance de la tâche de révision.

   ![task_details-collection](assets/task_details-collection.png)

1. Appuyez/cliquez sur **[!UICONTROL Envoyer]**, puis sur **[!UICONTROL Terminé]** pour fermer le message de confirmation. Une notification pour la nouvelle tâche est envoyée à l’approbateur.
1. Connectez-vous à [!DNL Experience Manager] Ressources en tant qu’approbateur et accédez à la console Ressources. Pour approuver des ressources, appuyez/cliquez sur l’icône **[!UICONTROL Notifications]**, puis sélectionnez la tâche de révision dans la liste.
1. Sur la page **[!UICONTROL Tâche de révision]**, examinez les détails de la tâche de révision, puis appuyez/cliquez sur **[!UICONTROL Réviser]**.
1. Toutes les ressources situées dans la collection sont visibles dans le panneau de révision. Sélectionnez les ressources, puis appuyez/cliquez sur l’icône **[!UICONTROL Approuver/Rejeter]** pour approuver ou rejeter les ressources selon les besoins.

   ![review_task_collection](assets/review_task_collection.png)

1. Appuyez/cliquez sur l’icône **[!UICONTROL Terminé]** dans la barre d’outils. Dans la boîte de dialogue, saisissez un commentaire, puis appuyez/cliquez sur **[!UICONTROL Terminé]** pour confirmer.
1. Accédez à la console Collections et ouvrez la collection. Les icônes d’état d’approbation des ressources s’affichent en mode Carte et Liste.

   **Mode Carte**

   ![collection_reviewstatuscardview](assets/collection_reviewstatuscardview.png)

   **Vue Liste**

   ![collection_reviewstatuslistview](assets/collection_reviewstatuslistview.png)
