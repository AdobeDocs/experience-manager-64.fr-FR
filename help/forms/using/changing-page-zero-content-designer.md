---
title: Modification du contenu de la page zéro avec Designer
seo-title: Changing Page Zero content in Designer
description: Savez-vous comment modifier le message affiché sur la page zéro d’un PDF XFA ouvert avec un programme de visualisation PDF non Adobe ?
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: Adaptive Forms
exl-id: 0ae34ddd-9a8d-48df-af2d-80c3fe6abd62
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 87%

---

# Modifier le contenu de la page zéro dans Designer {#changing-page-zero-content-in-designer}

Le contenu de la page zéro s’affiche par défaut lorsqu’une visionneuse autre qu’Adobe PDF, telle que la visionneuse de PDF par défaut dans Chrome ou Firefox, ne peut pas lire le contenu du formulaire PDF/XFA. Le message par défaut de la page zéro est affiché ci-dessous.

![defaultpage0message](assets/defaultpage0message.png)

La version AEM Forms Feature Pack 1 de Designer vous permet de modifier le message affiché sur la page zéro. Pour modifier le message de la page zéro, procédez comme suit :

1. Assurez-vous que la version AEM Forms Feature Pack 1 de Designer est installée. Vous pouvez vérifier la version dans l’écran A propos de Designer.

1. Ouvrez le formulaire dont vous souhaitez modifier le contenu de la page zéro.

1. Cliquez sur **Fichier > Propriétés du formulaire**.

1. Dans la boîte de dialogue Propriétés du formulaire, cliquez sur le signe ![plus](assets/plus.png) (icône plus) pour ajouter une propriété personnalisée.

1. Spécifiez **_pagezerocontent** en tant que nom de propriété.
1. Ajoutez le nouveau message de la page zéro au format Rich Text, en tant que valeur. Par exemple :

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Enregistrez le formulaire au format PDF.

1. Affichez le formulaire PDF dans le navigateur pour vous assurer que le message a été mis à jour. La valeur d’exemple évoquée ci-dessus apparaît comme suit :

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>La propriété personnalisée créée peut ne pas s’afficher correctement dans la boîte de dialogue Propriétés du formulaire lors de la réouverture du formulaire. Toutefois, le formulaire fonctionne correctement et affiche le message mis à jour sur la page zéro.
