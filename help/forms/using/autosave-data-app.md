---
title: Utilisation de l’enregistrement automatique dans l’application AEM Forms
seo-title: Utilisation de l’enregistrement automatique dans l’application AEM Forms
description: 'Apprenez à utiliser enregistrement automatique dans l’application AEM Forms afin d’éviter la perte de données. '
seo-description: 'Apprenez à utiliser enregistrement automatique dans l’application AEM Forms afin d’éviter la perte de données. '
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 75%

---


# Utilisation de l’enregistrement automatique dans l’application AEM Forms  {#using-autosave-in-aem-forms-app}

Lorsqu’un utilisateur saisit des données dans l’application Adobe Experience Manager Forms, la fonction d’enregistrement automatique les enregistre à intervalles réguliers. La fonction d’enregistrement automatique de l’application AEM Forms vous permet d’éviter la perte de données si l’application se ferme accidentellement.

L’application se ferme accidentellement :

* Si votre périphérique s’arrête car sa batterie est faible
* Si l’utilisateur stoppe l’application
* Si une panne inattendue se produit

Vous pouvez spécifier les intervalles auxquels l’application enregistre les données saisies.

>[!NOTE]
>
>Sélectionnez la fréquence d’enregistrement automatique de manière judicieuse. Un enregistrement automatique fréquent peut avoir un impact perceptible sur les performances de votre périphérique.

Suivez les étapes ci-après pour utiliser la fonction d’enregistrement automatique de l’application AEM Forms :

1. Connectez-vous à l’application et accédez à **[!UICONTROL Paramètres > Général]**.
1. Dans l’écran Général, utilisez l’option **[!UICONTROL Fréquence d’enregistrement automatique]** pour sélectionner les intervalles auxquels l’application doit enregistrer les données saisies.
   [ ![Définition de la fréquence d’enregistrement automatique](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Lorsque vous redémarrez l’application et que vous vous connectez avec le même nom d’utilisateur, vous êtes invité à restaurer votre tâche à l’aide de la boîte de dialogue de récupération de la tâche non enregistrée. Cliquez sur **[!UICONTROL OK]** dans la boîte de dialogue Récupérer la Tâche non enregistrée pour reprendre l&#39;utilisation de la tâche enregistrée. Vous pouvez cliquer sur **[!UICONTROL Annuler]** pour supprimer les données enregistrées correspondant au dernier enregistrement automatique déclenché et commencer à travailler sur une nouvelle tâche.

   Si vous cliquez sur **[!UICONTROL OK]**, la tâche est restaurée avec les données correspondant au dernier enregistrement automatique déclenché avant que l’application ne s’arrête. Il comprend les données du formulaire et toutes les pièces jointes associées à la tâche.
   [ ![Obtention d&#39;une tâche ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**récupéréeA.** Un formulaire de travail en cours  **B.** App fermé avec force  **C.** App redémarré avec la boîte de dialogue Récupérer une Tâche non enregistrée  **D.Formulaire restauré avec les données d&#39;origine**

