---
title: Prise en charge de Camera Raw
description: Découvrez comment activer la prise en charge Camera Raw dans Adobe Experience Manager Assets.
contentOwner: AG
feature: Developer Tools
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 42%

---

# Utilisation de Camera Raw pour traiter les images {#camera-raw-support}

Vous pouvez activer la prise en charge Camera Raw pour traiter les formats de fichiers bruts, tels que CR2, NEF et RAF, et effectuer le rendu des images au format JPEG. Cette fonctionnalité est prise en charge dans Adobe Experience Manager Assets à l’aide de la fonction [Package Camera Raw](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) disponible à partir de Distribution logicielle.

>[!NOTE]
>
>La fonctionnalité ne prend en charge que les rendus JPEG. Il est pris en charge sur Windows 64 bits, Mac OS et RHEL 7.x.

Pour activer la prise en charge Camera Raw dans Adobe Experience Manager Assets, procédez comme suit :

1. Téléchargez la [Package Camera Raw](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) à partir de Distribution logicielle.

1. Accédez à l’adresse `https://[aem_server]:[port]/workflow`. Ouvrez le **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]** workflow.

1. Ouvrez le **[!UICONTROL Miniatures des processus]** étape .

1. Fournissez la configuration suivante dans la section **[!UICONTROL Miniatures]** tab :

   * **[!UICONTROL Miniatures]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL Types MIME ignorés]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![chlimage](assets/chlimage_1-334.png)

1. Dans le **[!UICONTROL Image web]** , dans le **[!UICONTROL Ignorer la liste]** champ, spécifiez `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![chlimage](assets/chlimage_1-335.png)

1. Dans le panneau latéral, ajoutez le **[!UICONTROL Gestionnaire Camera Raw/DNG]** étape sous **[!UICONTROL Création de miniatures]** étape .

1. Dans le **[!UICONTROL Gestionnaire Camera Raw/DNG]** ajoutez la configuration suivante dans la **[!UICONTROL Arguments]** tab :

   * **[!UICONTROL Types MIME]**: `image/dng` et `image/x-raw-(.*)`
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

Vous pouvez désormais importer des fichiers Camera Raw dans [!DNL Experience Manager] Ressources. Après avoir installé le package Camera Raw et configuré le workflow requis, **[!UICONTROL Réglage de l’image]** s’affiche dans la liste des panneaux latéraux.

![chlimage_1-337](assets/chlimage_1-337.png)

*Figure : Options du volet latéral*

![chlimage_1-338](assets/chlimage_1-338.png)

*Figure : Utilisez cette option pour apporter des modifications légères à vos images.*

Après avoir enregistré les modifications apportées à une image Camera Raw, un nouveau rendu `AdjustedPreview.jpg` est généré pour cette image. Pour les types d’images autres que Camera Raw, les modifications sont répercutées dans tous les rendus.

## Bonnes pratiques, problèmes connus et limites {#best-practices}

La fonctionnalité présente les limites suivantes :

* La fonctionnalité ne prend en charge que les rendus JPEG. Elle est prise en charge sous Windows 64 bits, Mac OS et RHEL 7.x.
* L’écriture différée des métadonnées n’est pas prise en charge pour les formats RAW et DNG.
* La bibliothèque Camera Raw présente des limitations quant au nombre total de pixels qu’elle peut traiter à la fois. Actuellement, il peut traiter un maximum de 6 500 pixels sur le long du côté d’un fichier ou 512 MP, quels que soient les critères rencontrés en premier.
