---
title: Publication de dossiers sur Brand Portal
description: Découvrez comment publier des dossiers ou en annuler la publication sur Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1

---


# Publication de dossiers sur Brand Portal {#publish-folders-to-brand-portal}

En tant qu’administrateur d’Adobe Experience Manager (AEM) Assets, vous pouvez publier des ressources et des dossiers sur l’instance AEM Assets Brand Portal (ou planifier le workflow de planification à une date/heure ultérieure) pour votre organisation. Cependant, vous devez d’abord intégrer AEM Assets à Brand Portal. For details, see [Configure AEM Assets with Brand Portal](configure-aem-assets-with-brand-portal.md).

Une fois que vous avez publié un fichier ou un dossier, il est accessible aux utilisateurs dans le portail de marque.

Si vous apportez des modifications ultérieures à la ressource ou au dossier d’origine dans les ressources AEM, les modifications ne sont pas répercutées dans le portail de marque tant que vous n’avez pas republié la ressource ou le dossier. Cette fonctionnalité garantit que les modifications en cours ne sont pas disponibles dans le portail de marque. Seules les modifications approuvées publiées par un administrateur sont disponibles dans le portail des marques.

## Publication de dossiers sur Brand Portal {#publish-folders-to-brand-portal-1}

1. From the AEM Assets interface, hover over the desired folder and select **[!UICONTROL Publish]** option from the quick actions.

   Vous pouvez aussi sélectionner le dossier souhaité et suivre les étapes supplémentaires.

   ![publish2bp](assets/publish2bp.png)

2. **Publication instantanée des dossiers**

   Pour publier les dossiers sélectionnés sur Brand Portal, effectuez l’une des opérations suivantes :

   * From the toolbar, select **[!UICONTROL Quick Publish]**. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.
   * From the toolbar, select **[!UICONTROL Manage Publication]**.

3. Then from the **[!UICONTROL Action]** select **[!UICONTROL Publish to Brand Portal]**, and from **[!UICONTROL Scheduling]** select **[!UICONTROL Now]**. Appuyez sur **[!UICONTROL Suivant].**
4. Within **[!UICONTROL Scope]**, confirm your selection and tap **[!UICONTROL Publish to Brand Portal]**.

   Un message indique que le dossier a été placé en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour voir le dossier publié.

   **Publication ultérieure de dossiers**

   Pour programmer la publication sur le portail de marque des dossiers de fichiers à une date ou une heure ultérieure :

   1. Once you have selected assets/folders to publish, select **[!UICONTROL Manage Publication]** from the tool bar at the top.
   2. On **[!UICONTROL Manage Publication]** page, select **[!UICONTROL Publish to Brand Portal]** from **[!UICONTROL Action]** and select **[!UICONTROL Later]** from **[!UICONTROL Scheduling]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Select an **[!UICONTROL Activation date]** and specify time. Appuyez sur **[!UICONTROL Suivant]**.
   4. Confirm your selection in **[!UICONTROL Scope]**. Appuyez sur **[!UICONTROL Suivant]**.
   5. Specify a Workflow title under **[!UICONTROL Workflows]**. Tap **[!UICONTROL Publish Later]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Annulation de la publication de dossiers sur Brand Portal {#unpublish-folders-from-brand-portal}

Vous pouvez supprimer n’importe quel dossier de ressources publié sur Brand Portal en en annulant la publication à partir de l’instance d’auteur AEM. Une fois le dossier d’origine dépublié, sa copie n’est plus disponible pour les utilisateurs du portail de marque.

Vous avez la possibilité d’annuler rapidement la publication de dossiers sur Brand Portal ou de planifier l’annulation à une date et une heure ultérieures. Pour annuler la publication de dossiers de ressources sur Brand Portal :

1. Depuis l’interface d’AEM Assets de l’instance d’auteur AEM, sélectionnez le dossier dont vous souhaitez annuler la publication.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Gérer la publication]**.

3. **Annulation rapide d’une publication sur Brand Portal**

   Pour annuler rapidement la publication du dossier désiré sur Brand Portal :

   1. On **[!UICONTROL Manage Publication]** page, from **[!UICONTROL Action]** select **[!UICONTROL Unpublish from Brand Portal]** and from **[!UICONTROL Scheduling]** select **[!UICONTROL Now]**.
   2. Appuyez/cliquez sur **[!UICONTROL Suivant].**
   3. Within **[!UICONTROL Scope]**, confirm your selection and tap **[!UICONTROL Unpublish from Brand Portal]**.
   ![confirmer-annuler la publication](assets/confirm-unpublish.png)

   **Annuler la publication de Brand Portal ultérieurement**

   Pour planifier l’annulation de la publication d’un dossier sur Brand Portal à une date et à une heure ultérieures :

   1. On **[!UICONTROL Manage Publication]** page, from **[!UICONTROL Action]** select **[!UICONTROL Unpublish from Brand Portal]** and from **[!UICONTROL Scheduling]** select **[!UICONTROL Later].**
   2. Select an **[!UICONTROL Activation date]** and specify the time. Appuyez sur **[!UICONTROL Suivant]**.
   3. Within **[!UICONTROL Scope]**, confirm your selection and tap **[!UICONTROL Next]**.
   4. Specify a **[!UICONTROL Workflow title]** under **[!UICONTROL Workflows]**. Tap **[!UICONTROL Unpublish Later].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>La procédure de publication/annulation de la publication d’un fichier depuis/vers le portail de marque est similaire à la procédure correspondante pour un dossier.
