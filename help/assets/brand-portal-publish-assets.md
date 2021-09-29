---
title: Publication de dossiers sur Brand Portal
description: Découvrez comment publier des ressources et en annuler la publication sur Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 47%

---

# Publication de ressources sur Brand Portal {#publish-assets-to-brand-portal}

En tant qu’administrateur Adobe Experience Manager Assets, vous pouvez publier des ressources sur l’instance [!DNL Experience Manager Assets Brand Portal] (ou planifier le processus de publication à une date/heure ultérieure) pour votre organisation. Cependant, vous devez d’abord configurer [!DNL Assets] avec [!DNL Brand Portal]. Pour plus d’informations, voir [Configuration [!DNL Assets] avec [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md).

Une fois que vous avez publié une ressource, elle est disponible pour les utilisateurs de Brand Portal.

Si vous apportez des modifications ultérieures à la ressource d’origine dans [!DNL Assets], les modifications ne sont pas répercutées dans Brand Portal tant que vous n’avez pas republié la ressource. Cette fonction assure que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

Une fois la réplication réussie, vous pouvez publier des ressources, des dossiers et des collections sur [!DNL Brand Portal]. Pour publier des ressources sur Brand Portal, procédez comme suit :

>[!NOTE]
>
>Adobe recommande la publication décalée, de préférence aux heures creuses, de sorte que l’auteur [!DNL Experience Manager] ne consomme pas trop de ressources.

1. Dans la console Assets, placez le curseur au-dessus des ressources souhaitées et sélectionnez l’option **[!UICONTROL Publier]** parmi les actions rapides.

   Vous pouvez également sélectionner les ressources que vous voulez publier sur Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Pour publier les ressources dans Brand Portal, deux options sont disponibles :
   * [Publier les ressources immédiatement](#publish-now)
   * [Publication ultérieure des ressources](#publish-later)

## Publication immédiate des ressources {#publish-now}

Pour publier les ressources sélectionnées sur Brand Portal, effectuez l’une des opérations suivantes :

* Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**. Ensuite, dans le menu, sélectionnez **[!UICONTROL Publier sur Brand Portal]**.

* Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

   1. Ensuite, à partir de **[!UICONTROL Action]** sélectionnez **[!UICONTROL Publier sur Brand Portal]**, puis, dans **[!UICONTROL Planification]** sélectionnez **[!UICONTROL Maintenant]**. Appuyez/cliquez sur **[!UICONTROL Suivant].**

   2. Dans **[!UICONTROL Portée]**, confirmez votre sélection et appuyez/cliquez sur **[!UICONTROL Publier sur Brand Portal]**.

Un message indique que les ressources ont été placées en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour voir les ressources publiées.

## Publication ultérieure des ressources {#publish-later}

Pour planifier la publication des ressources sur Brand Portal à une date ou une heure ultérieure :

1. Une fois que vous avez sélectionné les ressources/dossiers à publier, sélectionnez **[!UICONTROL Gérer la publication]** dans la barre d’outils supérieure.
2. Sur la page **[!UICONTROL Gérer la publication]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]** dans **[!UICONTROL Action]** et sélectionnez **[!UICONTROL Plus]** dans **[!UICONTROL Planification]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
4. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
5. Spécifiez un titre de workflow sous **[!UICONTROL Processus]**. Appuyez/cliquez sur **[!UICONTROL Publier ultérieurement]**.

   ![publishworkflow](assets/publishworkflow.png)

Désormais, connectez-vous à Brand Portal pour voir si les ressources publiées sont disponibles dans l’interface de Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
