---
title: Écriture différée XMP sur les rendus
description: Découvrez comment la fonction d’écriture différée XMP propage les modifications apportées aux métadonnées d’une ressource à l’ensemble des rendus de la ressource ou à certains d’entre eux.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 62%

---

# Écriture différée XMP sur les rendus {#xmp-writeback-to-renditions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette fonction d’écriture différée XMP dans [!DNL Adobe Experience Manager Assets] reproduit les modifications de métadonnées apportées aux rendus de la ressource d’origine. Lorsque vous modifiez les métadonnées d’une ressource à partir d’Assets ou lors du chargement de la ressource, les modifications sont initialement stockées dans le nœud des métadonnées de la hiérarchie des ressources.

La fonction Écriture différée XMP permet de propager les modifications de métadonnées à l’ensemble des rendus de la ressource ou uniquement à certains d’entre eux. La fonction réécrit uniquement les propriétés de métadonnées qui utilisent l’espace de noms `jcr`, c’est-à-dire qu’une propriété nommée `dc:title` est réécrite, mais qu’une propriété nommée `mytitle` ne l’est pas.

Supposons que vous remplaciez la propriété [!UICONTROL Titre] d’une ressource intitulée `Classic Leather` par `Nylon`.

![metadata](assets/metadata.png)

Dans ce cas, la variable [!DNL Experience Manager] Les ressources enregistrent les modifications apportées au **[!UICONTROL Titre]** dans la propriété `dc:title` pour les métadonnées de la ressource stockées dans la hiérarchie de la ressource.

![metadata_saved](assets/metadata_stored.png)

Toutefois, [!DNL Experience Manager Assets] ne propage pas automatiquement les modifications apportées aux métadonnées dans les rendus d’une ressource. Consultez la section [Activer l’écriture différée XMP](#enabling-xmp-writeback).

## Activation de l’écriture différée XMP {#enabling-xmp-writeback}

Pour activer la propagation des modifications apportées aux métadonnées aux rendus de la ressource lors de leur chargement, modifiez la configuration **Créateur de rendus de gestion des actifs numériques Adobe CQ** dans Configuration Manager.

1. Ouvrez Configuration Manager à partir de `https://[aem_server]:[port]/system/console/configMgr`.
1. Ouvrez la configuration **[!UICONTROL Créateur de rendus de gestion des actifs numériques Adobe CQ]**.
1. Sélectionnez l’option **[!UICONTROL Propager XMP]**, puis enregistrez les modifications.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Activation de l’écriture différée XMP pour des rendus spécifiques {#enabling-xmp-writeback-for-specific-renditions}

Pour permettre à la fonction Écriture différée XMP de propager les modifications de métadonnées à des rendus spécifiques, spécifiez ces rendus à l’étape de workflow Écriture différée XMP du workflow Écriture différée des métadonnées de gestion des ressources numériques. Par défaut, cette étape est configurée avec le rendu d’origine.

Pour que la fonction Écriture différée XMP propage les métadonnées aux miniatures de rendu 140.100.png et 319.319.png, procédez comme suit :

1. Dans Experience Manager, accédez à **[!UICONTROL Outils > Processus > Modèles]**.
1. Dans la [!UICONTROL Modèles] , ouvrez la page **[!UICONTROL Écriture différée des métadonnées de gestion des actifs numériques]** modèle de workflow.
1. Sur la page de propriétés **[!UICONTROL Écriture différée des métadonnées de gestion des actifs numériques]**, ouvrez l’étape **[!UICONTROL Processus d’écriture différée XMP]**.
1. Dans la boîte de dialogue **[!UICONTROL Propriétés des étapes]**, appuyez/cliquez sur l’onglet **[!UICONTROL Processus]**.
1. Dans le **[!UICONTROL Arguments]** box, ajouter `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Appuyez/cliquez sur **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Pour régénérer les rendus de TIFF pyramidaux pour les images Dynamic Media avec les nouveaux attributs, ajoutez le **[!UICONTROL Ressources d’image de processus Dynamic Media]** étape du workflow Écriture différée des métadonnées de gestion des actifs numériques .
Les rendus PTIFF sont uniquement créés et stockés localement en mode hybride Dynamic Media. Enregistrez le workflow.

Les modifications apportées aux métadonnées sont propagées aux rendus `thumbnail.140.100.png` et `thumbnail.319.319.png` de la ressource, et non des autres.

>[!NOTE]
>
>Si vous rencontrez des problèmes liés à l’écriture différée XMP sous Linux 64 bits, consultez la section [Activation de l’écriture différée XMP sous Red Hat Linux 64 bits](https://helpx.adobe.com/fr/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Pour plus d’informations sur les plateformes prises en charge, voir [XMP conditions préalables à l’écriture différée des métadonnées](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtrage des métadonnées XMP {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] prend en charge le filtrage par liste bloquée et par liste autorisée de propriétés/nœuds pour les métadonnées XMP qui sont lues à partir de binaires de ressources et stockées dans JCR quand les ressources sont ingérées.

Le filtrage par liste bloquée permet d’importer toutes les propriétés des métadonnées XMP, à l’exception des propriétés spécifiées pour l’exclusion. Cependant, pour les types de ressources tels que les fichiers INDD comportant un très grand nombre de métadonnées XMP (par exemple 1 000 nœuds avec 10 000 propriétés), les noms des nœuds à filtrer ne sont pas toujours connus à l’avance. Si le filtrage à l’aide d’une liste bloquée permet l’importation d’un grand nombre de ressources avec de nombreuses métadonnées XMP, la variable [!DNL Experience Manager] instance ou grappe peut rencontrer des problèmes de stabilité, par exemple des files d’attente d’observation bloquées.

Le filtrage par liste autorisée des métadonnées XMP résout le problème en vous permettant de définir les propriétés XMP à importer. De cette manière, toute autre propriété XMP ou inconnue est ignorée. Pour une compatibilité ascendante, vous pouvez ajouter certaines de ces propriétés au filtre qui utilise une liste bloquée.

>[!NOTE]
>
>Le filtrage fonctionne uniquement pour les propriétés dérivées de sources XMP dans les fichiers binaires de ressources. Pour les propriétés dérivées de sources non XMP, telles que les formats EXIF et IPTC, le filtrage ne fonctionne pas. Par exemple, la date de création de la ressource est stockée dans la propriété appelée `CreateDate` dans EXIF TIFF. [!DNL Experience Manager] stocke cette valeur dans le champ de métadonnées nommé `exif:DateTimeOriginal`. Comme la source est autre que XMP, le filtrage ne fonctionne pas sur cette propriété.

1. Ouvrez Configuration Manager à partir de `https://[aem_server]:[port]/system/console/configMgr`.
1. Ouvrez la configuration **[!UICONTROL Filtre XMP de gestion des actifs numériques Adobe CQ]**.
1. Pour appliquer un filtrage par liste autorisée, sélectionnez **[!UICONTROL Appliquer la liste autorisée aux propriétés XMP]**, puis spécifiez les propriétés à importer dans l’encadré **[!UICONTROL Noms XML autorisés pour le filtrage XMP]**.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Pour filtrer les propriétés XMP bloquées après l’application du filtrage par liste autorisée, spécifiez celles qui se trouvent dans la zone **[!UICONTROL Noms XML bloqués pour le filtrage XMP.]** Enregistrez les modifications.

   >[!NOTE]
   >
   >Le **[!UICONTROL Appliquer la Liste bloquée aux propriétés XMP]** est sélectionnée par défaut. En d’autres termes, le filtrage à l’aide d’une liste bloquée est activé par défaut. Pour désactiver ce filtrage, désélectionnez l’option **[!UICONTROL Appliquer la Liste bloquée aux propriétés XMP]** .
