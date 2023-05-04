---
title: Activation de la détection de doublons
description: Découvrez comment activer la détection des ressources en double dans AEM.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 26%

---

# Activation de la détection de doublons {#enabling-duplicate-detection}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Si vous tentez de charger une ressource qui existe dans Adobe Experience Manager Assets, la fonction de détection des doublons l’identifie comme un doublon. La détection des doublons est désactivée par défaut. Pour activer la fonction, procédez comme suit :

1. Ouvrez le **[!UICONTROL Configuration de la console web Adobe Experience Manager]** page à `https://[server]:[port]/system/console/configMgr`.
1. Modifiez la configuration du servlet **[!UICONTROL Ressource de création de gestion des ressources numériques Day CQ]**.
1. Sélectionnez la **[!UICONTROL détecter les doublons]** , puis cliquez/appuyez sur **[!UICONTROL Enregistrer]**.

   ![Sélection de l’option de détection des doublons dans le servlet](assets/chlimage_1-377.png)

La fonction de détection des doublons est désormais activée dans [!DNL Experience Manager] Ressources. Lorsqu’un utilisateur tente de charger une ressource qui existe dans AEM, le système recherche un conflit et l’indique. Les ressources sont identifiées à l’aide du hachage SHA-1 stocké dans `jcr:content/metadata/dam:sha1`, ce qui signifie que les ressources en double sont détectées quels que soient les noms de fichiers.

>[!MORELIKETHIS]
>
>* [Duplication de ressources dans le référentiel existant (un tutoriel d’un membre de la communauté)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

