---
title: Intégration de AEM 3D avec Autodesk 3ds Max
seo-title: Intégration de AEM 3D avec AutoDesk 3ds Max
description: Vous pouvez éventuellement intégrer AEM 3D avec le logiciel Autodesk 3ds Max pour activer la prise en charge des fichiers 3ds Max natifs (.MAX). Pour le moment, le rendu au moyen de 3ds Max n’est pas pris en charge.
seo-description: Vous pouvez éventuellement intégrer AEM 3D avec le logiciel Autodesk 3ds Max pour activer la prise en charge des fichiers 3ds Max natifs (.MAX). Pour le moment, le rendu au moyen de 3ds Max n’est pas pris en charge.
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 8%

---


# Intégration de AEM 3D avec Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>Cette tâche est facultative et concerne Windows uniquement.

Vous pouvez éventuellement intégrer AEM 3D avec le logiciel Autodesk 3ds Max pour activer la prise en charge des fichiers 3ds Max natifs (.MAX). Pour le moment, le rendu au moyen de 3ds Max n’est pas pris en charge.

Voir [Paramètres de configuration avancés](advanced-config-3d.md).

Voir aussi [Intégration de AEM 3D avec AutoDesk Maya](integrate-maya-with-3d.md).

**Pour intégrer AEM 3D avec Autodesk 3ds Max** :

1. Installez le logiciel Autodesk 3ds Max sur les mêmes serveurs que ceux sur lesquels les noeuds d’auteur AEM sont installés.

   Une fois l’installation terminée, vérifiez que vous pouvez ouvrir et utiliser Maya et qu’il n’y a aucun problème d’autorisation.

   >[!NOTE]
   >
   >Pour éviter les problèmes d’accès refusé, installez 3ds Max en utilisant le même compte d’administrateur que AEM.

1. Dans 3ds Max, cliquez sur **[!UICONTROL Personnaliser > Gestionnaire de modules complémentaires]**.

   Recherchez `FBXMAX.DLU` et vérifiez que **[!UICONTROL Status]** est **[!UICONTROL chargé]**.

   Fermez la boîte de dialogue **[!UICONTROL Plug-In Manager]** et 3ds Max.

1. Mettez à jour le script de conversion.

   aem utilise un script de ligne de commande pour appeler l&#39;utilitaire de ligne de commande 3ds Max `3dsmaxcmd.exe`. Vous devez modifier ce script si vous avez installé une version autre que 3ds Max 2016, ou si vous avez installé 3ds Max à un emplacement non standard, ou si vous avez installé AEM sur une partition ou un lecteur différent.

   1. Ouvrez le CRXDE Lite et accédez à `/libs/settings/dam/v3D/scripts/max`.
   1. Cliquez sur `export-fbx.bat` doublon pour l’ouvrir.
   1. Modifiez la première ligne du script en fonction des besoins afin de refléter l’emplacement de l’utilitaire `3dsmaxcmd.exe`. Par exemple, si 3ds Max 2017 est utilisé et que AEM est installé sur un autre lecteur de disque :

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. Près du coin supérieur gauche de la page du CRXDE Lite, appuyez sur **[!UICONTROL Enregistrer tout]**.

   Près du coin supérieur gauche de la page du CRXDE Lite, appuyez sur **[!UICONTROL Enregistrer tout]**.

1. Supprimez le dossier de travail (uniquement nécessaire si une précédente tentative d’assimilation d’un fichier .MAX a été effectuée).

   1. Dans CRXDE Lite, accédez à `/libs/settings/dam/v3D/Paths/maxWorkPath`. Par défaut, la valeur de ce paramètre est `./MaxWork`, ce qui est relatif au dossier racine d’installation AEM.
   1. Connectez-vous au serveur lui-même et utilisez l’Explorateur de fichiers pour accéder au dossier racine d’installation AEM.
   1. Supprimez le dossier **[!UICONTROL MaxWork]**, y compris son contenu entier, s’il existe.

      Le dossier est automatiquement recréé lors de la prochaine assimilation d&#39;un fichier .MAX.

1. Activez 3ds Max pour l’assimilation en procédant comme suit :

   1. Dans le CRXDE Lite, accédez à `/libs/settings/dam/v3D/assetTypes/max` et définissez la propriété **[!UICONTROL Enabled]** sur true :

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. Près du coin supérieur gauche de la page du CRXDE Lite, appuyez sur **[!UICONTROL Enregistrer tout]**.

## Test de l&#39;intégration de AEM 3D avec Autodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. Ouvrez AEM Assets, puis téléchargez le fichier `.max` situé dans `sample-3D-content/models` dans le dossier **[!UICONTROL test3d]**.

   Veuillez noter que sample-3D-content.zip a été téléchargé au préalable pour valider la fonctionnalité 3D de base.

1. Revenez à la vue **[!UICONTROL Carte]** et observez les bannières de message affichées sur les ressources téléchargées.

   La bannière Format de conversion s’affiche alors que 3ds Max convertit le format 3ds Max natif en .FBX.

1. Une fois le traitement terminé, ouvrez `logo-sphere.max` dans la vue **[!UICONTROL Détails]**.

   L’expérience de Prévisualisation est la même que pour `logo_sphere.fbx`.

