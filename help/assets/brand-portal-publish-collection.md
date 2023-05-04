---
title: Publication de collections sur Brand Portal
description: Découvrez comment publier des collections et en annuler la publication sur Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 44%

---

# Publication de collections sur Brand Portal {#publish-collections-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

En tant qu’administrateur d’Adobe Experience Manager Assets, vous pouvez publier des collections sur le [!DNL Experience Manager Assets Brand Portal] pour votre organisation. Cependant, vous devez d’abord intégrer  Assets à Brand Portal. Pour plus d’informations, voir [Configuration de ressources avec Brand Portal](configure-aem-assets-with-brand-portal.md).

Si vous apportez des modifications ultérieures à la collection d’origine dans  Assets, les changements ne sont reflétés dans Brand Portal que lorsque vous republiez la collection. Cette fonction assure que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

>[!NOTE]
>
>Les fragments de contenu ne peuvent pas être publiés sur Brand Portal. Par conséquent, si vous sélectionnez un ou plusieurs fragments de contenu sur [!DNL Experience Manager] Auteur, puis **[Publication sur Brand Portal]** n’est pas disponible.
>
>Si des collections contenant des fragments de contenu sont publiées à partir de [!DNL Experience Manager] Créez dans Brand Portal, puis tout le contenu du dossier, à l’exception des fragments de contenu, est répliqué vers l’interface Brand Portal.

## Publication d’une collection dans Brand Portal {#publish-a-collection-to-brand-portal}

1. Dans l’interface utilisateur d’Assets, appuyez/cliquez sur le [!DNL Experience Manager] logo. Ensuite, accédez à **[!UICONTROL Ressources > Collections]** de la **[!UICONTROL Navigation]** page.
2. Dans la console Collections, sélectionnez la collection que vous souhaitez publier dans Brand Portal.

   ![select_collection](assets/select_collection.png)

3. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Publication sur Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Dans la boîte de dialogue de confirmation, appuyez/cliquez sur **[!UICONTROL Publier]**.
5. Fermez le message de confirmation.
6. Connectez-vous à Brand Portal en tant qu’administrateur. La collection publiée est disponible dans la console Collections.

   ![publish_collection](assets/published_collection.png)

## Dépublication de collections {#unpublish-collections}

Vous pouvez dépublier les collections que vous publiez depuis  Assets dans Brand Portal. Une fois la collection d’origine dépubliée, sa copie n’est plus disponible pour les utilisateurs de Brand Portal.

1. Dans la console Collections de votre [!DNL Assets] et sélectionnez la collection dont vous souhaitez annuler la publication.

   ![select_collection-1](assets/select_collection-1.png)

2. Dans la barre d’outils, appuyez/cliquez sur le **[!UICONTROL Supprimer de Brand Portal]** icône .

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Dans la boîte de dialogue, appuyez/cliquez sur **[!UICONTROL Annuler la publication]**.
4. Fermez le message de confirmation. La collection est supprimée de l’interface de Brand Portal.
