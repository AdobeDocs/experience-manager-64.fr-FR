---
title: Configurer les paramètres d’absence du bureau
seo-title: Configuring Out of Office Settings
description: La fonction Absence du bureau vous permet de spécifier quand un utilisateur sera absent du bureau et ne pourra pas effectuer les tâches assignées par AEM forms.
seo-description: The Out of Office feature enables you to specify when a user will be out of the office and unable to complete tasks assigned by AEM forms.
uuid: 0d01df0a-aa6a-40e5-bf24-423ed1c932cc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 30312159-58a5-4781-b554-29dcbce696cb
exl-id: 8787ffa9-9ddc-439d-9934-8913d1ed459e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 7%

---

# Configurer les paramètres d’absence du bureau {#configuring-out-of-office-settings}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La fonction d’absence du bureau permet aux utilisateurs ou aux administrateurs de spécifier le moment où un utilisateur sera absent du bureau et ne pourra pas effectuer les tâches affectées par AEM forms. Lorsqu’un utilisateur est déconnecté du bureau, ses tâches sont affectées à un ou plusieurs utilisateurs désignés. Les utilisateurs peuvent modifier leurs paramètres d’absence du bureau dans l’espace de travail ou les administrateurs peuvent également modifier les paramètres à la place d’un utilisateur dans Forms Workflow.

Lors de la création d’un processus, l’utilisateur de Workbench peut indiquer si une tâche peut être redirigée en raison des paramètres d’absence du bureau.

## Affichage des informations d’absence du bureau d’un utilisateur {#view-a-user-s-out-of-office-information}

1. Dans Administration Console, cliquez sur Services > Processus des formulaires > Absence du bureau.
1. Dans la zone située en haut de la page Absence du bureau, vous pouvez effectuer l’une des opérations suivantes :

   **Rechercher par nom**

   Sélectionnez l’option Rechercher par nom . Saisissez tout ou une partie du nom d’utilisateur, puis cliquez sur Rechercher. Si vous laissez le champ vide, le processus Forms renvoie une liste de tous les utilisateurs.

   **Rechercher par période**

   Sélectionnez l’option Rechercher par période . Indiquez les dates de début et de fin, ainsi que les horodatages souhaités, pour limiter le résultat de la recherche. Cliquez sur Rechercher.

1. Cliquez sur le nom d’un utilisateur pour afficher ses informations d’absence du bureau sous la liste des utilisateurs.

## Modification de l’état d’absence du bureau d’un utilisateur {#change-a-user-s-out-of-office-status}

1. Recherchez l’utilisateur, comme décrit à la section [Affichage des informations d’absence du bureau d’un utilisateur](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
1. Cliquez sur le nom de l’utilisateur que vous souhaitez modifier.
1. Dans la *Nom d’utilisateur* est actuellement répertorié, sélectionnez Au bureau ou Absence du bureau.
1. Cliquez sur Enregistrer.

## Ajout d’une plage de dates d’absence du bureau pour un utilisateur {#add-an-out-of-office-date-range-for-a-user}

1. Recherchez l’utilisateur, comme décrit à la section [Affichage des informations d’absence du bureau d’un utilisateur](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
1. Cliquez sur le nom de l’utilisateur que vous souhaitez modifier.
1. Cliquez sur Ajouter une plage de dates.
1. Saisissez une heure de début et une heure de fin. Vous pouvez cliquer sur l’icône Calendrier pour sélectionner une date. Si vous ne spécifiez pas d’heure de fin, l’utilisateur sera défini comme étant absent du bureau indéfiniment.
1. Cliquez sur Enregistrer.

## Affectation d’un utilisateur à des tâches d’absence du bureau {#assign-a-user-for-out-of-office-tasks}

Lorsqu’un utilisateur est absent du bureau, vous pouvez lui affecter un ou plusieurs utilisateurs afin d’effectuer toute nouvelle tâche. Vous pouvez configurer les configurations suivantes :

* Affectez toutes les nouvelles tâches à un utilisateur désigné par défaut.
* Ne réaffectez aucune tâche. De nouvelles tâches restent affectées à l’utilisateur absent du bureau.
* Attribuez un utilisateur par défaut qui recevra la plupart des tâches de l’utilisateur, mais indiquez que les tâches de certains processus sont réaffectées à d’autres utilisateurs ou restent affectées à l’utilisateur absent du bureau.
* N’affectez pas un utilisateur par défaut, mais attribuez certaines tâches de certains processus à des utilisateurs spécifiques.

   1. Recherchez l’utilisateur, comme décrit à la section [Affichage des informations d’absence du bureau d’un utilisateur](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
   1. Cliquez sur le nom de l’utilisateur que vous souhaitez modifier.
   1. Dans la liste Utilisateur par défaut pour les tâches d’absence du bureau, sélectionnez un utilisateur dans la liste. Si vous ne souhaitez pas désigner un utilisateur par défaut pour la réception d’éléments réaffectés, sélectionnez Ne pas affecter.

      Si le nom d’utilisateur approprié n’apparaît pas dans la liste, cliquez sur Rechercher un utilisateur , puis utilisez la boîte de dialogue Rechercher un utilisateur pour rechercher l’utilisateur. Sélectionnez l’utilisateur approprié dans la liste, puis cliquez sur Sélectionner un utilisateur. Vous pouvez également cliquer sur Afficher le planning de l’utilisateur dans la boîte de dialogue Rechercher un utilisateur pour afficher le planning d’absence du bureau de l’utilisateur sélectionné.

   1. Si des processus ne doivent pas être envoyés à l’utilisateur par défaut, cliquez sur Ajouter une exception, puis sélectionnez le processus et sélectionnez un autre utilisateur dans la liste. Vous pouvez également sélectionner Ne pas affecter pour que la tâche reste attribuée à l’utilisateur absent du bureau.
   1. Cliquez sur Enregistrer.
