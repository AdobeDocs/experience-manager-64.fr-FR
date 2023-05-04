---
title: Configuration des polices de réserve
seo-title: Configuring fallback fonts
description: Découvrez comment configurer les polices de secours.
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 6942b6fc-8d04-429f-8433-1ab74c68fcc1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 25%

---

# Configuration des polices de réserve {#configuring-fallback-fonts}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette section explique comment configurer manuellement le fichier FontManagerResources.properties pour associer les polices par défaut d’AEM forms à des polices de remplacement (ou de substitution), qui seront utilisées si les polices par défaut ne sont pas disponibles sur le serveur. Ce fichier de propriétés se trouve dans le fichier adobe-fontmanager.jar .

>[!NOTE]
>
>La configuration des polices de secours s’applique également au service Assembler.

1. Accédez à adobe-livecycle-*[appserver]* fichier .ear dans la variable *[racine aem-forms]*/configurationManager/export directory, effectuez une copie de sauvegarde et décompressez l’original.
1. Recherchez le fichier adobe-fontmanager.jar et décompressez-le.
1. Recherchez le fichier FontManagerResources.properties et ouvrez-le dans un éditeur de texte.
1. Modifiez les noms et emplacements des polices Generic et Fallback selon les besoins, puis enregistrez le fichier.

   Les entrées de police du fichier FontManagerResources.properties sont relatives à la variable *[racine aem-forms]* répertoire /fonts. Si vous spécifiez des polices autres que les polices par défaut d’AEM forms, vous devez les installer dans cette arborescence (dans un répertoire existant ou créé à cet effet).

   >[!NOTE]
   >
   >Si la police spécifiée ou la police par défaut ne contient pas de caractère unicode spécifique ou si elle n’est pas disponible, le caractère est extrait d’une police de secours selon la priorité suivante :

   * Police spécifique aux paramètres régionaux
   * police RAOT si les paramètres régionaux ne sont pas définis ;
   * Police générique, recherchée par ordre défini dans la table de secours

1. Recompressez le fichier adobe-fontmanager.jar.
1. Recompressez adobe-livecycle-*[appserver]* fichier .ear, puis redéployez-le manuellement ou en exécutant Configuration Manager.

>[!NOTE]
>
>N’utilisez pas Configuration Manager pour recompresser adobe-livecycle-[appserver]fichier .ear, car il remplacera vos modifications par les valeurs par défaut d’AEM forms.
