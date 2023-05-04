---
title: Publication de dossiers sur Brand Portal
description: Découvrez comment publier ou dépublier des ressources sur Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 55%

---

# Publication de ressources sur Brand Portal {#publish-assets-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

En tant qu’administrateur Adobe Experience Manager Assets, vous pouvez publier des ressources sur le [!DNL Experience Manager Assets Brand Portal] de votre entreprise (ou programmez le processus de publication à une date/heure ultérieure). Toutefois, vous devez d’abord configurer [!DNL Assets] avec [!DNL Brand Portal]. Pour plus d’informations, voir [Configurer [!DNL Assets] avec [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md).

Une fois que vous avez publié une ressource, elle est disponible pour les utilisateurs de Brand Portal.

Si vous apportez des modifications ultérieures à la ressource d’origine dans [!DNL Assets], les modifications ne sont reflétées dans Brand Portal que lorsque vous republiez la ressource. Cette fonction assure que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

Une fois la réplication réussie, vous pouvez publier des ressources, des dossiers et des collections dans . [!DNL Brand Portal]. Pour publier des ressources sur Brand Portal, procédez comme suit :

>[!NOTE]
>
>Adobe recommande la publication décalée, de préférence aux heures creuses, de sorte que la variable [!DNL Experience Manager] L’auteur n’occupe pas de ressources excédentaires.

1. Dans la console Ressources, passez la souris sur les ressources souhaitées et sélectionnez **[!UICONTROL Publier]** dans les actions rapides.

   Vous pouvez également sélectionner les ressources que vous voulez publier sur Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Pour publier les ressources dans Brand Portal, deux options sont disponibles :
   * [Publication immédiate des ressources](#publish-now)
   * [Publication immédiate des ressources](#publish-later)

## Publication immédiate des ressources {#publish-now}

Pour publier les ressources sélectionnées sur Brand Portal, effectuez l’une des opérations suivantes :

* Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**. Ensuite, sélectionnez **[!UICONTROL Publier sur Brand Portal]** dans le menu.

* Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

   1. Ensuite, dans **[!UICONTROL Action]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]** et dans **[!UICONTROL Planification]**, sélectionnez **[!UICONTROL Maintenant]**. Appuyez/cliquez sur **[!UICONTROL Suivant].**

   2. Within **[!UICONTROL Portée]**, confirmez votre sélection et appuyez/cliquez sur **[!UICONTROL Publication sur Brand Portal]**.

Un message indique que les ressources ont été placées en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour afficher les ressources publiées.

## Publication ultérieure des ressources {#publish-later}

Pour planifier la publication des ressources sur Brand Portal à une date ou une heure ultérieure :

1. Une fois que vous avez sélectionné les ressources/dossiers à publier, sélectionnez **[!UICONTROL Gérer la publication]** dans la barre d’outils supérieure.
2. Sur la page **[!UICONTROL Gérer la publication]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]** dans **[!UICONTROL Action]** et sélectionnez **[!UICONTROL Plus tard]** à partir de **[!UICONTROL Planification]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
4. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
5. Spécifiez un titre de workflow sous **[!UICONTROL Processus]**. Appuyez/cliquez sur **[!UICONTROL Publier ultérieurement]**.

   ![publishworkflow](assets/publishworkflow.png)

Désormais, connectez-vous à Brand Portal pour voir si les ressources publiées sont disponibles dans l’interface de Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
