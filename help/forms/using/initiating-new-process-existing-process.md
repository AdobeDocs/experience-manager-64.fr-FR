---
title: Démarrer un nouveau processus avec les données de processus existantes dans l’espace de travail AEM Forms
seo-title: Initiating a new process with existing process data in AEM Forms workspace
description: Découvrez comment lancer un nouveau processus avec les données de processus existantes dans l’espace de travail AEM Forms.
seo-description: See how you can initiate a new process with existing process data in AEM Forms workspace.
uuid: 57a7f414-c9f2-4acc-890a-e29e1adff084
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 4d55a100-1876-41f0-a06f-7a009c934f3d
exl-id: d7bdbd22-97b0-45cd-8e72-43ca3d0d1215
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 25%

---

# Démarrer un nouveau processus avec les données de processus existantes dans l’espace de travail AEM Forms {#initiating-a-new-process-with-existing-process-data-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez lancer un nouveau processus à l’aide des données d’un processus existant. La nécessité d’initier un nouveau processus à partir des données de processus existantes survient lorsque nous devons fréquemment utiliser le même formulaire avec peu de modifications de contenu, comme les formulaires pour congés payés. Cette fonctionnalité permet aux utilisateurs de gagner du temps et de faire des efforts, en particulier lorsque le processus a un long formulaire à remplir.

Voici les étapes pour lancer un nouveau processus à partir des données de processus existantes : -

1. Effectuez l’une des opérations suivantes :

   * Dans Tracking, cliquez sur l’instance de processus dont vous souhaitez utiliser les données. Dans la vue Historique des processus du volet de droite, cliquez sur la ligne de tâche correspondant au point de départ.
   * Dans Suivi, sélectionnez un modèle de recherche pour afficher une liste des instances de processus. Sélectionnez l&#39;instance dont vous souhaitez utiliser les données.
   * Dans le **[!UICONTROL Tâches]** , sélectionnez la tâche. Cliquez sur le bouton **[!UICONTROL Histoire]** et sélectionnez la tâche qui a lancé l’instance de processus.

   ![start3](assets/start3.png) ![start1](assets/start1.png)

1. Dans la barre d’outils de l’action Tâche, cliquez sur **[!UICONTROL Démarrer]**. Un formulaire adaptatif pour la nouvelle instance de processus est affiché avec des données préremplies.

1. Mettez à jour les données le cas échéant, et cliquez sur **[!UICONTROL Terminer]** ou sur le bouton approprié dans le formulaire.
