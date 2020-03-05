---
title: Publication de dossiers sur Brand Portal
description: Découvrez comment publier et annuler la publication de fichiers sur le portail de marque.
contentOwner: VG
translation-type: tm+mt
source-git-commit: f09853921dec6602952f369982a1563c7e4a9727

---


# Publication de ressources sur Brand Portal {#publish-assets-to-brand-portal}

En tant qu’administrateur des ressources d’Adobe Experience Manager (AEM), vous pouvez publier des ressources sur l’instance de portail de marques AEM Assets (ou programmer le processus de publication à une date/heure ultérieure) pour votre entreprise. Toutefois, vous devez d’abord configurer AEM Assets avec Brand Portal. For details, see [Configure AEM Assets with Brand Portal](configure-aem-assets-with-brand-portal.md).

Une fois que vous avez publié un fichier, il est accessible aux utilisateurs du portail de marque.

Si vous apportez des modifications ultérieures à la ressource d’origine dans les ressources AEM, les modifications ne sont pas répercutées dans le portail de marque tant que vous n’avez pas republié la ressource. Cette fonctionnalité garantit que les modifications en cours ne sont pas disponibles dans le portail de marque. Seules les modifications approuvées publiées par un administrateur sont disponibles dans le portail des marques.

Une fois la réplication réussie, vous pouvez publier des ressources, des dossiers et des collections sur Brand Portal. Pour publier des ressources sur Brand Portal, procédez comme suit :

>[!NOTE]
>
>Adobe recommande la publication décalée, de préférence en dehors des heures de pointe, de sorte que l’auteur AEM n’utilise pas une quantité excessive de ressources.

1. Dans la console Assets, placez le curseur au-dessus des ressources souhaitées et sélectionnez l’option **[!UICONTROL Publier]** parmi les actions rapides.

   Vous pouvez également sélectionner les ressources que vous voulez publier sur Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Pour publier les fichiers sur Brand Portal, vous disposez de deux options :
   * [Publication immédiate des fichiers](#publish-now)
   * [Publier les ressources plus tard](#publish-later)

## Publier les ressources maintenant {#publish-now}

Pour publier les ressources sélectionnées sur Brand Portal, effectuez l’une des opérations suivantes :

* From the toolbar, select **[!UICONTROL Quick Publish]**. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.

* From the toolbar, select **[!UICONTROL Manage Publication]**.

   1. Then from the **[!UICONTROL Action]** select **[!UICONTROL Publish to Brand Portal]**, and from **[!UICONTROL Scheduling]** select **[!UICONTROL Now]**. Appuyez/cliquez sur **[!UICONTROL Suivant].**

   2. Within **[!UICONTROL Scope]**, confirm your selection and tap/ click **[!UICONTROL Publish to Brand Portal]**.

Un message indique que les ressources ont été placées en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour voir les ressources publiées.

## Publier les ressources plus tard {#publish-later}

Pour planifier la publication des ressources sur Brand Portal à une date ou une heure ultérieure :

1. Once you have selected assets/ folders to publish, select **[!UICONTROL Manage Publication]** from the tool bar at the top.
2. On **[!UICONTROL Manage Publication]** page, select **[!UICONTROL Publish to Brand Portal]** from **[!UICONTROL Action]** and select **[!UICONTROL Later]** from **[!UICONTROL Scheduling]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Select an **[!UICONTROL Activation date]** and specify time. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
4. Select an **[!UICONTROL Activation date]** and specify time. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
5. Specify a Workflow title under **[!UICONTROL Workflows]**. Tap/ click **[!UICONTROL Publish Later]**.

   ![processus de publication](assets/publishworkflow.png)

Désormais, connectez-vous à Brand Portal pour savoir si les fichiers publiés sont disponibles dans l’interface de Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
