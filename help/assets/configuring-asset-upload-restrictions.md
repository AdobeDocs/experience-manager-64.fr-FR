---
title: Configuration des restrictions de téléchargement des ressources
description: Découvrez comment configurer Adobe Experience Manager Assets pour restreindre le type de ressources (fichiers) que les utilisateurs peuvent charger.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 61%

---

# Configuration des restrictions de téléchargement des ressources {#configuring-asset-upload-restrictions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez configurer Adobe Experience Manager Assets pour limiter le type de ressources (fichiers) que les utilisateurs peuvent charger. Cette fonctionnalité vous permet d’éliminer la possibilité pour les utilisateurs de charger des ressources dans un format indésirable ou de charger des fichiers malveillants. Le service `Day CQ DAM Asset Upload Restriction` (Restriction de chargement des ressources de la gestion des ressources numériques Day CQ) permet de contrôler le type de fichiers que les utilisateurs peuvent charger. Par défaut, [!DNL Experience Manager] Assets permet aux utilisateurs de charger des ressources de tous les types MIME. Cependant, vous pouvez configurer le service pour empêcher les utilisateurs de charger des fichiers disposant de types MIME spécifiques.

1. Pour ouvrir la console Web du gestionnaire de configuration, accédez à `https://[AEM_server]:[port]/system/console/configMgr`.
1. Ouvrez le service **[!UICONTROL Day CQ DAM Asset Upload Restriction]** en mode d’édition. Par défaut, la case **Autoriser tous les MIME** est cochée, ce qui permet aux utilisateurs de charger des fichiers quel que soit leur type MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Pour empêcher les utilisateurs de charger des fichiers disposant de certains types MIME, désactivez l’option **[!UICONTROL Allow all MIME]** et spécifiez les types MIME autorisés dans les champs **[!UICONTROL Allowed Asset MIMEs (regex)]** (MIME de ressources autorisés) à l’aide d’expressions régulières.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Cliquez ou appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications. Si vous spécifiez des chaînes MIME pour les types MIME autorisés, l’opération de chargement échoue pour toute ressource de type MIME qui ne correspond pas aux chaînes MIME configurées dans ces champs.
