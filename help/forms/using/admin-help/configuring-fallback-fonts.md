---
title: Configuration des polices de remplacement
seo-title: Configuring fallback fonts
description: Découvrez comment configurer des polices de remplacement.
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 6942b6fc-8d04-429f-8433-1ab74c68fcc1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 69%

---

# Configuration des polices de remplacement {#configuring-fallback-fonts}

Cette section explique comment configurer manuellement le fichier FontManagerResources.properties pour associer les polices par défaut d&#39;AEM forms à des polices de remplacement (ou de substitution), qui seront utilisées si les polices par défaut ne sont pas disponibles sur le serveur. Ce fichier de propriétés se trouve dans le fichier adobe-fontmanager.jar.

>[!NOTE]
>
>la configuration des polices de remplacement s’applique également au service d’assemblage.

1. Accédez à adobe-livecycle-*[appserver]* fichier .ear dans la variable *[racine aem-forms]*/configurationManager/export directory, effectuez une copie de sauvegarde et décompressez l’original.
1. Recherchez le fichier adobe-fontmanager.jar et décompressez-le.
1. Recherchez le fichier FontManagerResources.properties et ouvrez-le dans un éditeur de texte.
1. Modifiez les emplacements et les noms des polices dans les sections Generic et Fallback de manière appropriée et enregistrez le fichier.

   Les entrées de police du fichier FontManagerResources.properties sont relatives à la variable *[racine aem-forms]* répertoire /fonts. Si vous spécifiez des polices autres que les polices par défaut d&#39;AEM forms, vous devez les installer dans cette arborescence (dans un répertoire existant ou créé à cet effet).

   >[!NOTE]
   >
   >si la police spécifiée ou la police par défaut ne contient pas un caractère Unicode spécifique, ou si elle est indisponible, le caractère est extrait d’une police de remplacement, en respectant la priorité suivante :

   * police spécifique aux paramètres régionaux ;
   * police racine si les paramètres régionaux ne sont pas définis ;
   * police générique, la recherche étant effectuée dans l’ordre de la table de remplacement.

1. Recompressez le fichier adobe-fontmanager.jar.
1. Recompressez adobe-livecycle-*[appserver]* fichier .ear, puis redéployez-le manuellement ou en exécutant Configuration Manager.

>[!NOTE]
>
>N’utilisez pas Configuration Manager pour recompresser adobe-livecycle-[appserver]fichier .ear, car il remplacera vos modifications par les valeurs par défaut d’AEM forms.
