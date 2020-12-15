---
title: Publication de dossiers sur Brand Portal
description: Découvrez comment publier et annuler la publication de fichiers sur le portail des marques.
contentOwner: VG
translation-type: tm+mt
source-git-commit: f09853921dec6602952f369982a1563c7e4a9727
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 52%

---


# Publication de ressources sur Brand Portal {#publish-assets-to-brand-portal}

En tant qu’administrateur Adobe Experience Manager (AEM) Assets, vous pouvez publier des fichiers sur l’instance AEM Assets Brand Portal (ou programmer le processus de publication à une date/heure ultérieure) pour votre entreprise. Toutefois, vous devez d’abord configurer AEM Assets avec Brand Portal. Pour plus de détails, voir [Configuration d’AEM Assets avec Brand Portal](configure-aem-assets-with-brand-portal.md).

Une fois que vous avez publié un fichier, il est accessible aux utilisateurs du portail de marque.

Si vous apportez des modifications ultérieures à l’actif d’origine dans AEM Assets, les modifications ne sont pas répercutées dans le portail des marques tant que vous n’avez pas republié l’actif. Cette fonction assure que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

Une fois la réplication réussie, vous pouvez publier des ressources, des dossiers et des collections sur Brand Portal. Pour publier des ressources sur Brand Portal, procédez comme suit :

>[!NOTE]
>
>Adobe recommande la publication décalée, de préférence en dehors des heures de pointe, de sorte que l’auteur AEM n’utilise pas une quantité excessive de ressources.

1. Dans la console Assets, placez le curseur au-dessus des ressources souhaitées et sélectionnez l’option **[!UICONTROL Publier]** parmi les actions rapides.

   Vous pouvez également sélectionner les ressources que vous voulez publier sur Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Pour publier les fichiers sur le portail des marques, deux options sont disponibles :
   * [Publication immédiate des fichiers](#publish-now)
   * [Publication ultérieure des ressources](#publish-later)

## Publication immédiate des ressources {#publish-now}

Pour publier les ressources sélectionnées sur Brand Portal, effectuez l’une des opérations suivantes :

* Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**. Ensuite, dans le menu, sélectionnez **[!UICONTROL Publier sur le portail de marque]**.

* Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

   1. Ensuite, à partir de **[!UICONTROL Action]** sélectionnez **[!UICONTROL Publier sur le portail de la marque]**, et dans **[!UICONTROL Planification]** sélectionnez **[!UICONTROL Maintenant]**. Appuyez/cliquez sur **[!UICONTROL Suivant].**

   2. Dans **[!UICONTROL Scope]**, confirmez votre sélection et cliquez sur **[!UICONTROL Publier sur le portail de marque]**.

Un message indique que les ressources ont été placées en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour voir les ressources publiées.

## Publication ultérieure des ressources {#publish-later}

Pour planifier la publication des ressources sur Brand Portal à une date ou une heure ultérieure :

1. Une fois que vous avez sélectionné les fichiers/dossiers à publier, sélectionnez **[!UICONTROL Gérer la publication]** dans la barre d’outils située en haut de l’écran.
2. Sur la **[!UICONTROL page Gérer la publication]**, sélectionnez **[!UICONTROL Publier sur le portail de la marque]** dans **[!UICONTROL Action]** et **[!UICONTROL Plus tard]** dans **[!UICONTROL Planification]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
4. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
5. Spécifiez un titre de workflow sous **[!UICONTROL Processus]**. Appuyez sur **[!UICONTROL Publier ultérieurement]**.

   ![publishworkflow](assets/publishworkflow.png)

Désormais, connectez-vous à Brand Portal pour savoir si les fichiers publiés sont disponibles sur l’interface du portail Marque.

![bp_631_landing_page](assets/bp_landing_page.png)
