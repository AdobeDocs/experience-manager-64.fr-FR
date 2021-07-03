---
title: Activation de la détection des doublons
description: Découvrez comment activer la détection des ressources en double dans AEM.
contentOwner: AG
feature: Gestion des ressources, rapports sur les ressources
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 60%

---

# Activation de la détection des doublons {#enabling-duplicate-detection}

Si vous essayez de transférer une ressource qui existe dans Adobe Experience Manager (AEM) Assets, la fonctionnalité de détection des doublons l’identifie comme un doublon. La fonctionnalité de détection des doublons est désactivée par défaut. Pour l’activer, procédez comme suit :

1. Ouvrez la page **[!UICONTROL Configuration de la console web Adobe Experience Manager]** à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Modifiez la configuration de la servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Sélectionnez l’option **[!UICONTROL Détecter les doublons]**, puis cliquez/appuyez sur **[!UICONTROL Enregistrer]**.

   ![Sélection de l’option de détection des doublons dans le servlet](assets/chlimage_1-377.png)

La fonctionnalité de détection des doublons est maintenant activée dans AEM Assets. Lorsqu’un utilisateur tente de télécharger un fichier qui existe dans AEM, le système recherche un éventuel conflit et le signale. Les ressources sont identifiées à l’aide du hachage SHA-1 stocké à l’adresse `jcr:content/metadata/dam:sha1`, ce qui signifie que les ressources en double sont détectées quel que soit le nom de fichier.

>[!MORELIKETHIS]
>
>* [Duplication de ressources dans le référentiel existant (un tutoriel d’un membre de la communauté)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

