---
title: Publication de dossiers sur Brand Portal
description: Découvrez comment publier des dossiers et en annuler la publication sur Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 49%

---

# Publication de dossiers sur Brand Portal {#publish-folders-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

En tant qu’administrateur Adobe Experience Manager Assets, vous pouvez publier des ressources et des dossiers sur le [!DNL Experience Manager Assets Brand Portal] de votre entreprise (ou programmez le processus de publication à une date/heure ultérieure). Cependant, vous devez d’abord intégrer [!DNL Experience Manager Assets] avec [!DNL Brand Portal]. Pour plus d’informations, voir [Configurer [!DNL Experience Manager Assets] avec Brand Portal](configure-aem-assets-with-brand-portal.md).

Une fois que vous avez publié une ressource ou un dossier, il est disponible dans Brand Portal.

Si vous apportez des modifications ultérieures à la ressource ou au dossier d’origine dans [!DNL Assets], les modifications ne sont reflétées dans Brand Portal que lorsque vous republiez la ressource ou le dossier. Cette fonction assure que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

## Publication de dossiers sur Brand Portal {#publish-folders-to-brand-portal-1}

1. Dans la [!DNL Assets] , passez la souris sur le dossier souhaité, puis sélectionnez **[!UICONTROL Publier]** dans les actions rapides.

   Vous pouvez aussi sélectionner le dossier souhaité et suivre les étapes supplémentaires.

   ![publish2bp](assets/publish2bp.png)

2. **Publication immédiate des dossiers**

   Pour publier les dossiers sélectionnés dans Brand Portal, effectuez l’une des opérations suivantes :

   * Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**. Ensuite, sélectionnez **[!UICONTROL Publier sur Brand Portal]** dans le menu.
   * Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

3. Ensuite, dans **[!UICONTROL Action]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]** et dans **[!UICONTROL Planification]**, sélectionnez **[!UICONTROL Maintenant]**. Appuyez sur **[!UICONTROL Suivant].**
4. Within **[!UICONTROL Portée]**, confirmez votre sélection et appuyez sur **[!UICONTROL Publication sur Brand Portal]**.

   Un message indique que le dossier a été placé en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour afficher le dossier publié.

   **Publication ultérieure de dossiers**

   Pour planifier le workflow de publication sur Brand Portal de dossiers de ressources à une date ou à une heure ultérieure :

   1. Une fois que vous avez sélectionné les ressources/dossiers à publier, sélectionnez **[!UICONTROL Gérer la publication]** dans la barre d’outils supérieure.
   2. Sur la page **[!UICONTROL Gérer la publication]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]** dans **[!UICONTROL Action]** et sélectionnez **[!UICONTROL Plus tard]** à partir de **[!UICONTROL Planification]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez sur **[!UICONTROL Suivant]**.
   4. Confirmez votre sélection dans **[!UICONTROL Portée]**. Appuyez sur **[!UICONTROL Suivant]**.
   5. Spécifiez un titre de workflow sous **[!UICONTROL Processus]**. Appuyer **[!UICONTROL Publier ultérieurement]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Dépublication de dossiers sur Brand Portal {#unpublish-folders-from-brand-portal}

Vous pouvez supprimer tout dossier de ressources publié sur Brand Portal en l’annulant à partir de [!DNL Experience Manager] Instance de création. Une fois que vous avez dépublié le dossier d’origine, sa copie n’est plus disponible pour les utilisateurs de Brand Portal.

Vous avez la possibilité d’annuler rapidement la publication de dossiers à partir de Brand Portal ou de la planifier pour une date et une heure ultérieures. Pour dépublier des dossiers de ressources de Brand Portal :

1. Dans la [!DNL Assets] dans [!DNL Experience Manager]  Instance de création, sélectionnez le dossier dont vous souhaitez annuler la publication.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Gérer la publication]**.

3. **Annuler la publication sur Brand Portal maintenant**

   Pour annuler rapidement la publication du dossier souhaité dans Brand Portal :

   1. Activé **[!UICONTROL Gérer la publication]** page, à partir de **[!UICONTROL Action]** select **[!UICONTROL Annuler la publication à partir de Brand Portal]** et de **[!UICONTROL Planification]** select **[!UICONTROL Maintenant]**.
   2. Appuyez/cliquez sur **[!UICONTROL Suivant].**
   3. Within **[!UICONTROL Portée]**, confirmez votre sélection et appuyez sur **[!UICONTROL Annuler la publication à partir de Brand Portal]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Dépublication ultérieure sur Brand Portal**

   Pour planifier l’annulation de la publication d’un dossier sur Brand Portal à une date et à une heure ultérieures :

   1. Activé **[!UICONTROL Gérer la publication]** page, à partir de **[!UICONTROL Action]** select **[!UICONTROL Annuler la publication à partir de Brand Portal]** et de **[!UICONTROL Planification]** select **[!UICONTROL Plus tard].**
   2. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez sur **[!UICONTROL Suivant]**.
   3. Within **[!UICONTROL Portée]**, confirmez votre sélection et appuyez sur **[!UICONTROL Suivant]**.
   4. Spécifiez un **[!UICONTROL Titre du workflow]** under **[!UICONTROL Workflows]**. Appuyer **[!UICONTROL Annuler la publication ultérieurement].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>La procédure de publication/de dépublication vers/depuis Brand Portal est identique à la procédure correspondante pour les dossiers.
