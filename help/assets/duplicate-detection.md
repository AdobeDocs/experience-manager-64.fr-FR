---
title: Activation de la détection des doublons
description: Découvrez comment activer la détection des ressources en double dans AEM.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 40%

---

# Activation de la détection des doublons {#enabling-duplicate-detection}

Si vous tentez de charger une ressource qui existe dans Adobe Experience Manager Assets, la fonction de détection des doublons l’identifie comme un doublon. La fonctionnalité de détection des doublons est désactivée par défaut. Pour l’activer, procédez comme suit :

1. Ouvrez le **[!UICONTROL Configuration de la console web Adobe Experience Manager]** page à `https://[server]:[port]/system/console/configMgr`.
1. Modification de la configuration de la servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Sélectionnez la **[!UICONTROL détecter les doublons]** , puis cliquez/appuyez sur **[!UICONTROL Enregistrer]**.

   ![Sélection de l’option de détection des doublons dans le servlet](assets/chlimage_1-377.png)

La fonction de détection des doublons est désormais activée dans [!DNL Experience Manager] Ressources. Lorsqu’un utilisateur tente de télécharger un fichier qui existe dans AEM, le système recherche un éventuel conflit et le signale. Les ressources sont identifiées à l’aide du hachage SHA-1 stocké à l’adresse `jcr:content/metadata/dam:sha1`, ce qui signifie que les ressources en double sont détectées quel que soit le nom de fichier.

>[!MORELIKETHIS]
>
>* [Duplication de ressources dans le référentiel existant (un tutoriel d’un membre de la communauté)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

