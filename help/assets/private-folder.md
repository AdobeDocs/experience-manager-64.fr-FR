---
title: Partage de dossiers privés
description: Découvrez comment créer un dossier privé dans Adobe Experience Manager Assets et le partager avec d’autres utilisateurs et leur attribuer divers privilèges.
contentOwner: AG
feature: Collaboration
role: User
exl-id: b6aa3cba-4085-47ac-a249-7461baee2a00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 29%

---

# Partage de dossiers privés {#private-folder-sharing}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez créer dans l’interface utilisateur d’Adobe Experience Manager Assets un dossier privé qui vous est exclusivement accessible. Vous pouvez partager ce dossier privé avec d’autres utilisateurs et leur attribuer divers privilèges. Selon le niveau de privilège que vous attribuez, les utilisateurs peuvent effectuer différentes tâches dans le dossier, par exemple consulter des ressources du dossier ou les modifier.

1. Dans la console Ressources, appuyez ou cliquez sur **[!UICONTROL Créer]** dans la barre d’outils, puis choisissez **[!UICONTROL Dossier]** dans le menu.

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. Dans le **[!UICONTROL Ajouter un dossier]** , saisissez un titre et un nom (facultatif) pour le dossier, puis sélectionnez **[!UICONTROL Privé]**.

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. Cliquez/appuyez sur **[!UICONTROL Créer]**. Un dossier privé est créé dans l’interface utilisateur.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Pour partager le dossier avec d’autres utilisateurs et leur attribuer des privilèges, sélectionnez le dossier, puis cliquez/appuyez sur l’icône **[!UICONTROL Propriétés]** de la barre d’outils.

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >Le dossier n’est pas visible par les autres utilisateurs tant qu’il n’est pas partagé.

1. Sur la page Propriétés du dossier , sélectionnez un utilisateur dans la **[!UICONTROL Ajouter un utilisateur]** , attribuez un rôle à l’utilisateur dans votre dossier privé, puis cliquez sur **[!UICONTROL Ajouter]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Vous pouvez affecter différents rôles, tels que l’éditeur, le propriétaire ou le visualisateur, à l’utilisateur avec lequel vous partagez le dossier. Si vous attribuez un rôle de propriétaire à l’utilisateur, celui-ci dispose des droits d’éditeur sur le dossier. En outre, il peut partager le dossier avec d’autres utilisateurs. Si vous attribuez un rôle d’éditeur, l’utilisateur peut modifier les ressources de votre dossier privé. Si vous attribuez un rôle de visionneuse, l’utilisateur ne peut afficher que les ressources de votre dossier privé.

1. Cliquez sur **[!UICONTROL Enregistrer]**. Selon le rôle que vous attribuez, l’utilisateur se voit attribuer un ensemble de privilèges sur votre dossier privé lorsqu’il se connecte à [!DNL Experience Manager] Ressources.
1. Cliquez sur **[!UICONTROL OK]** pour fermer le message de confirmation.
1. L’utilisateur avec lequel vous partagez le dossier reçoit une notification de partage. Connectez-vous à [!DNL Experience Manager] Ressources avec les informations d’identification de l’utilisateur pour afficher la notification.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Appuyez/cliquez sur l’icône Notification pour ouvrir la liste de notifications.

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. Cliquez/appuyez sur l’entrée du dossier privé partagé par l’administrateur pour ouvrir le dossier.

>[!NOTE]
>
>Pour pouvoir créer un dossier privé, vous devez disposer des autorisations de lecture et d’édition de l’ACL sur le dossier parent sous lequel vous souhaitez créer un dossier privé. Si vous n’êtes pas administrateur, ces autorisations ne sont pas activées pour vous par défaut sur */content/dam*. Dans ce cas, vous devez d’abord obtenir ces autorisations pour votre identifiant utilisateur/groupe avant de tenter de créer des dossiers privés ou d’afficher les paramètres du dossier.
