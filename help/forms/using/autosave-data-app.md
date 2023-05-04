---
title: Utiliser l’enregistrement automatique dans l’application AEM Forms
seo-title: Using autosave in AEM Forms app
description: Découvrez comment utiliser la fonction d’enregistrement automatique dans l’application AEM Forms qui vous permet d’éviter la perte de données.
seo-description: Learn how to use autosave feature in AEM Forms app that lets you avoid data loss.
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
exl-id: 6eb00c31-6806-478a-99d1-55912798ea69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 62%

---

# Utiliser l’enregistrement automatique dans l’application AEM Forms {#using-autosave-in-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsqu’un utilisateur saisit des données dans l’application Adobe Experience Manager Forms, la fonction d’enregistrement automatique les enregistre à intervalles réguliers. La fonction d’enregistrement automatique de l’application AEM Forms vous permet d’éviter toute perte de données si l’application est accidentellement fermée.

Votre application peut se fermer accidentellement :

* Si votre appareil s’arrête en raison d’une batterie faible
* Si l’utilisateur stoppe l’application
* En cas de blocage inattendu

Vous pouvez spécifier les intervalles après lesquels l’application enregistre les données saisies.

>[!NOTE]
>
>Sélectionnez la fréquence d’enregistrement automatique de manière judicieuse. Un enregistrement automatique fréquent peut avoir un impact perceptible sur les performances de votre périphérique.

Suivez les étapes ci-après pour utiliser la fonction d’enregistrement automatique de l’application AEM Forms :

1. Connectez-vous à l’application et accédez à **[!UICONTROL Paramètres > Général]**.
1. Dans l’écran Général, utilisez l’option **[!UICONTROL Fréquence d’enregistrement automatique]** pour choisir les intervalles auxquels vous voulez que l’application enregistre les données saisies.
   [ ![Définition de la fréquence d’enregistrement automatique](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Lorsque vous redémarrez l’application et que vous vous connectez avec le même nom d’utilisateur, vous êtes invité à restaurer votre tâche à l’aide de la boîte de dialogue de récupération de la tâche non enregistrée. Cliquez sur **[!UICONTROL OK]** dans la boîte de dialogue Récupérer des documents non sauvegardés pour recommencer à travailler sur la tâche enregistrée. Vous pouvez cliquer sur **[!UICONTROL Annuler]** pour supprimer les données enregistrées correspondant au dernier enregistrement automatique déclenché et commencer à travailler sur une nouvelle tâche.

   Si vous cliquez sur **[!UICONTROL OK]**, la tâche est restaurée avec les données correspondant au dernier enregistrement automatique déclenché avant que l’application ne s’arrête. Elle inclut les données d’un formulaire et toutes les pièces jointes liées à la tâche.
   [ ![Obtenir une tâche récupérée ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** Un formulaire de travail en cours **B.** Application fermée de force **C.** L’application a redémarré avec la boîte de dialogue Récupérer la tâche non enregistrée **D.** Formulaire restauré avec les données d’origine
