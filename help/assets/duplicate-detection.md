---
title: Activation de la détection des doublons
description: Découvrez comment activer la détection des ressources en double dans AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26e860cd513d70d748f872e2ce445a042d075bc6
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 61%

---


# Activation de la détection des doublons  {#enabling-duplicate-detection}

Si vous essayez de transférer une ressource qui existe dans Adobe Experience Manager (AEM) Assets, la fonctionnalité de détection des doublons l’identifie comme un doublon. La fonctionnalité de détection des doublons est désactivée par défaut. Pour l’activer, procédez comme suit :

1. Ouvrez la page **[!UICONTROL Configuration de la console Web de Adobe Experience Manager]** à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Modifiez la configuration de la servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Sélectionnez l&#39;option **[!UICONTROL détecter le duplicata]**, puis cliquez/appuyez sur **[!UICONTROL Enregistrer]**.

   ![Sélection de l’option de détection des doublons dans le servlet](assets/chlimage_1-377.png)

La fonctionnalité de détection des doublons est maintenant activée dans AEM Assets. Lorsqu’un utilisateur tente de télécharger un fichier qui existe dans AEM, le système recherche un éventuel conflit et le signale. Les ressources sont identifiées à l’aide du hachage SHA-1 stocké à `jcr:content/metadata/dam:sha1`, ce qui signifie que les ressources de duplicata sont détectées indépendamment des noms de fichier.

>[!MORELIKETHIS]
>
>* [Duplicata de ressources dans le référentiel existant (un didacticiel d’un membre de la communauté)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

