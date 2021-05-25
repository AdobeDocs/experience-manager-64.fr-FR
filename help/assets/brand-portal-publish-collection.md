---
title: Publication de collections sur Brand Portal
description: Découvrez comment publier et annuler la publication de collections dans Brand Portal.
contentOwner: VG
feature: Brand Portal
role: Business Practitioner
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 63%

---

# Publication de collections sur Brand Portal {#publish-collections-to-brand-portal}

En tant qu’administrateur Adobe Experience Manager (AEM) Assets, vous pouvez publier des collections dans l’instance AEM Assets Brand Portal de votre organisation. Cependant, vous devez d’abord intégrer AEM Assets à Brand Portal. Pour plus de détails, voir [Configuration d’AEM Assets avec Brand Portal](configure-aem-assets-with-brand-portal.md).

Si vous apportez des modifications ultérieures à la collection d’origine dans AEM Assets, les modifications ne sont pas répercutées dans Brand Portal tant que vous n’avez pas republié la collection. Cette caractéristique permet de s’assurer que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

>[!NOTE]
>
>Les fragments de contenu ne peuvent pas être publiés sur Brand Portal. Par conséquent, si vous sélectionnez un ou plusieurs fragments de contenu sur l’auteur AEM, l’action **[Publier sur Brand Portal]** n’est pas disponible.
>
>Si des collections contenant des fragments de contenu sont publiées sur Brand Portal à partir de l’auteur AEM, alors tout le contenu du dossier, excepté les fragments de contenu, est répliqué sur l’interface Brand Portal.

## Publication d’une collection dans Brand Portal {#publish-a-collection-to-brand-portal}

1. Dans l’interface utilisateur d’AEM Assets, appuyez/cliquez sur le logo AEM. Ensuite, accédez à **[!UICONTROL Assets > Collections]** depuis la page **[!UICONTROL Navigation]**.
2. Dans la console Collections, sélectionnez la collection que vous souhaitez publier dans Brand Portal.

   ![select_collection](assets/select_collection.png)

3. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Publier sur Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Dans la boîte de dialogue de confirmation, appuyez/cliquez sur **[!UICONTROL Publier]**.
5. Fermez le message de confirmation.
6. Connectez-vous à Brand Portal en tant qu’administrateur. La collection publiée est disponible dans la console Collections.

   ![publish_collection](assets/published_collection.png)

## Annulation de la publication de collections {#unpublish-collections}

Vous pouvez annuler la publication de collections que vous publiez d’AEM Assets vers Brand Portal. Une fois la publication de la collection d’origine annulée, sa copie n’est plus disponible pour les utilisateurs de Brand Portal.

1. Dans la console Collections de votre instance AEM Assets, sélectionnez la collection dont vous souhaitez annuler la publication.

   ![select_collection-1](assets/select_collection-1.png)

2. Dans la barre d’outils, appuyez/cliquez sur l’icône **[!UICONTROL Supprimer de Brand Portal]** .

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Dans la boîte de dialogue, appuyez/cliquez sur **[!UICONTROL Annuler la publication]**.
4. Fermez le message de confirmation. La collection est supprimée de l’interface de Brand Portal.
