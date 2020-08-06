---
title: Prise en charge de Camera Raw
description: Découvrez comment activer la prise en charge Camera Raw dans Adobe Experience Manager Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dea673f8999656a5c5364f74f45eba41dd17b947
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 45%

---


# Utiliser Camera Raw pour traiter les images {#camera-raw-support}

Vous pouvez activer la prise en charge Camera Raw pour traiter les formats de fichier bruts, tels que CR2, NEF et RAF, et effectuer le rendu des images au format JPEG. La fonctionnalité est prise en charge dans Adobe Experience Manager Assets à l&#39;aide du package [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) Camera Raw disponible dans Software Distribution.

>[!NOTE]
>
>La fonctionnalité ne prend en charge que les rendus JPEG. Il est pris en charge sous Windows 64 bits, Mac OS et RHEL 7.x.

Pour activer la prise en charge Camera Raw des ressources Adobe Experience Manager, procédez comme suit :

1. Download the [Camera Raw package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) from the Software Distribution.

1. Accédez à l’adresse `https://[aem_server]:[port]/workflow`. Open the **[!UICONTROL DAM Update Asset]** workflow.

1. Open the **[!UICONTROL Process Thumbnails]** step.

1. Provide the following configuration in the **[!UICONTROL Thumbnails]** tab:

   * **[!UICONTROL Miniatures]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL Types MIME ignorés]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![limage](assets/chlimage_1-334.png)

1. Dans l’onglet Image **** Web activée, dans le champ **[!UICONTROL Ignorer la Liste]** , spécifiez `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![limage](assets/chlimage_1-335.png)

1. From the side panel, add the **[!UICONTROL Camera Raw/DNG Handler]** step below the **[!UICONTROL Thumbnail creation]** step.

1. In the **[!UICONTROL Camera Raw/DNG Handler]** step, add the following configuration in the **[!UICONTROL Arguments]** tab:

   * **[!UICONTROL Types]** MIME : `image/dng` et `image/x-raw-(.*)`
   * **[!UICONTROL Commande]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

>[!NOTE]
>
>Vérifiez que la configuration ci-dessus est identique à la configuration **[!UICONTROL Exemple de ressources de mise à jour de gestion des actifs numériques avec l&#39;étape de manipulation Camera RAW et DNG]**.

Vous pouvez désormais importer des fichiers Camera Raw dans AEM Assets. After you install the Camera RAW package and configure the required workflow, **[!UICONTROL Image Adjust]** option appears in the list of side panes.

![chlimage_1-337](assets/chlimage_1-337.png)

*Figure : Options dans le volet latéral*

![chlimage_1-338](assets/chlimage_1-338.png)

*Figure : Utilisez cette option pour apporter des modifications légères à vos images*

Après avoir enregistré les modifications apportées à une image Camera Raw, un nouveau rendu `AdjustedPreview.jpg` est généré pour cette image. Pour les types d’images autres que Camera Raw, les modifications sont répercutées dans tous les rendus.

## Bonnes pratiques, problèmes connus et limites {#best-practices}

La fonctionnalité présente les limites suivantes :

* La fonctionnalité ne prend en charge que les rendus JPEG. Elle est prise en charge sous Windows 64 bits, Mac OS et RHEL 7.x.
* L’écriture différée des métadonnées n’est pas prise en charge pour les formats RAW et DNG.
* La bibliothèque Camera Raw présente des limitations quant au nombre total de pixels qu’elle peut traiter à la fois. Actuellement, il peut traiter un maximum de 65 000 pixels sur le côté long d’un fichier ou 512 MP, quels que soient les critères rencontrés en premier.
