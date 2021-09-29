---
title: Publication de dossiers sur Brand Portal
description: Découvrez comment publier des dossiers ou en annuler la publication sur Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 45%

---

# Publication de dossiers sur Brand Portal {#publish-folders-to-brand-portal}

En tant qu’administrateur d’Adobe Experience Manager Assets, vous pouvez publier des ressources et des dossiers sur l’instance [!DNL Experience Manager Assets Brand Portal] (ou planifier le processus de publication à une date/heure ultérieure) pour votre organisation. Cependant, vous devez d’abord intégrer [!DNL Experience Manager Assets] à [!DNL Brand Portal]. Pour plus d’informations, voir [Configuration [!DNL Experience Manager Assets] avec Brand Portal](configure-aem-assets-with-brand-portal.md).

Une fois que vous avez publié une ressource ou un dossier, il est disponible pour les utilisateurs dans Brand Portal.

Si vous apportez des modifications ultérieures à la ressource ou au dossier d’origine dans [!DNL Assets], les modifications ne sont pas répercutées dans Brand Portal tant que vous n’avez pas republié la ressource ou le dossier. Cette fonction assure que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

## Publication de dossiers sur Brand Portal {#publish-folders-to-brand-portal-1}

1. Dans l’interface [!DNL Assets], passez la souris sur le dossier souhaité et sélectionnez l’option **[!UICONTROL Publier]** dans les actions rapides.

   Vous pouvez aussi sélectionner le dossier souhaité et suivre les étapes supplémentaires.

   ![publish2bp](assets/publish2bp.png)

2. **Publication instantanée des dossiers**

   Pour publier les dossiers sélectionnés sur Brand Portal, effectuez l’une des opérations suivantes :

   * Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**. Ensuite, dans le menu, sélectionnez **[!UICONTROL Publier sur Brand Portal]**.
   * Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

3. Ensuite, à partir de **[!UICONTROL Action]** sélectionnez **[!UICONTROL Publier sur Brand Portal]**, puis, dans **[!UICONTROL Planification]** sélectionnez **[!UICONTROL Maintenant]**. Appuyez sur **[!UICONTROL Suivant].**
4. Dans **[!UICONTROL Portée]**, confirmez votre sélection et appuyez sur **[!UICONTROL Publier sur Brand Portal]**.

   Un message indique que le dossier a été placé en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour voir le dossier publié.

   **Publication ultérieure de dossiers**

   Pour planifier le workflow de publication sur Brand Portal des dossiers de ressources à une date ou une heure ultérieure :

   1. Une fois que vous avez sélectionné les ressources/dossiers à publier, sélectionnez **[!UICONTROL Gérer la publication]** dans la barre d’outils supérieure.
   2. Sur la page **[!UICONTROL Gérer la publication]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]** dans **[!UICONTROL Action]** et sélectionnez **[!UICONTROL Plus]** dans **[!UICONTROL Planification]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez sur **[!UICONTROL Suivant]**.
   4. Confirmez votre sélection dans **[!UICONTROL Portée]**. Appuyez sur **[!UICONTROL Suivant]**.
   5. Spécifiez un titre de workflow sous **[!UICONTROL Processus]**. Appuyez sur **[!UICONTROL Publier ultérieurement]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Annulation de la publication de dossiers sur Brand Portal {#unpublish-folders-from-brand-portal}

Vous pouvez supprimer tout dossier de ressources publié sur Brand Portal en l’annulant à partir de l’instance d’auteur [!DNL Experience Manager]. Une fois que vous avez annulé la publication du dossier original, sa copie n’est plus disponible pour les utilisateurs de Brand Portal.

Vous avez la possibilité d’annuler rapidement la publication de dossiers sur Brand Portal ou de planifier l’annulation à une date et une heure ultérieures. Pour annuler la publication de dossiers de ressources sur Brand Portal :

1. Dans l’interface [!DNL Assets] de l’instance d’auteur [!DNL Experience Manager], sélectionnez le dossier dont vous souhaitez annuler la publication.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Gérer la publication]**.

3. **Annulation rapide d’une publication sur Brand Portal**

   Pour annuler rapidement la publication du dossier désiré sur Brand Portal :

   1. Sur la **[!UICONTROL page Gérer la publication]**, à partir de **[!UICONTROL Action]** sélectionnez **[!UICONTROL Annuler la publication à partir de Brand Portal]** et à partir de **[!UICONTROL Planification]** sélectionnez **[!UICONTROL Maintenant]**.
   2. Appuyez/cliquez sur **[!UICONTROL Suivant].**
   3. Dans **[!UICONTROL Portée]**, confirmez votre sélection et appuyez sur **[!UICONTROL Annuler la publication à partir de Brand Portal]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Annulation ultérieure de la publication à partir de Brand Portal**

   Pour planifier l’annulation de la publication d’un dossier sur Brand Portal à une date et à une heure ultérieures :

   1. Sur la **[!UICONTROL page Gérer la publication]**, à partir de **[!UICONTROL Action]** sélectionnez **[!UICONTROL Annuler la publication à partir de Brand Portal]** et à partir de **[!UICONTROL Planification]** sélectionnez **[!UICONTROL Plus tard].**
   2. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez sur **[!UICONTROL Suivant]**.
   3. Dans **[!UICONTROL Portée]**, confirmez votre sélection et appuyez sur **[!UICONTROL Suivant]**.
   4. Spécifiez un **[!UICONTROL Titre du workflow]** sous **[!UICONTROL Workflows]**. Appuyez sur **[!UICONTROL Annuler la publication ultérieurement].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>La procédure de publication/annulation de la publication d’une ressource vers/depuis Brand Portal est similaire à la procédure correspondante pour un dossier.
