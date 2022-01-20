---
title: Utilisation de l’enregistrement automatique dans l’application AEM Forms
seo-title: Using autosave in AEM Forms app
description: 'Apprenez à utiliser enregistrement automatique dans l’application AEM Forms afin d’éviter la perte de données. '
seo-description: Learn how to use autosave feature in AEM Forms app that lets you avoid data loss.
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
exl-id: 6eb00c31-6806-478a-99d1-55912798ea69
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 73%

---

# Utilisation de l’enregistrement automatique dans l’application AEM Forms {#using-autosave-in-aem-forms-app}

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
1. Dans l’écran Général , utilisez la méthode **[!UICONTROL Fréquence d’enregistrement automatique]** pour sélectionner les intervalles auxquels vous souhaitez que l’application enregistre les données saisies.
   [ ![Définition de la fréquence d’enregistrement automatique](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Lorsque vous redémarrez l’application et que vous vous connectez avec le même nom d’utilisateur, vous êtes invité à restaurer votre tâche à l’aide de la boîte de dialogue de récupération de la tâche non enregistrée. Cliquez sur **[!UICONTROL OK]** dans la boîte de dialogue Récupérer la tâche non enregistrée pour reprendre l’utilisation de la tâche enregistrée. Vous pouvez cliquer sur **[!UICONTROL Annuler]** pour supprimer les données enregistrées correspondant au dernier enregistrement automatique déclenché et commencer à travailler sur une nouvelle tâche.

   Si vous cliquez sur **[!UICONTROL OK]**, la tâche est restaurée avec les données correspondant au dernier enregistrement automatique déclenché avant que l’application ne s’arrête. Il inclut les données du formulaire et toutes les pièces jointes associées à la tâche.
   [ ![Obtention d’une tâche récupérée ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** Un formulaire de travail en cours **B.** Application fermée de force **C.** L’application a redémarré avec la boîte de dialogue Récupérer la tâche non enregistrée **D.** Formulaire restauré avec les données d’origine
