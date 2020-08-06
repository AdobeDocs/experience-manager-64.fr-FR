---
title: Modification du contenu de la page zéro avec Designer
seo-title: Modification du contenu de la page zéro avec Designer
description: Savez-vous comment modifier le message affiché sur la page zéro d’un PDF XFA ouvert avec un programme de visualisation PDF non Adobe ?
seo-description: Savez-vous comment modifier le message affiché sur la page zéro d’un PDF XFA ouvert avec un programme de visualisation PDF non Adobe ?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 83%

---


# Modification du contenu de la page zéro avec Designer {#changing-page-zero-content-in-designer}

Le contenu de la page zéro s’affiche par défaut lorsqu’un lecteur non Adobe PDF, tel que le lecteur PDF par défaut dans Chrome ou Firefox, ne peut pas lire le contenu du formulaire PDF/XFA. Le message par défaut de la page zéro est affiché ci-dessous.

![defaultpage0message](assets/defaultpage0message.png)

La version AEM Forms Feature Pack 1 de Designer vous permet de modifier le message affiché sur la page zéro. Pour modifier le message de la page zéro, procédez comme suit :

1. Assurez-vous que la version AEM Forms Feature Pack 1 de Designer est installée. Vous pouvez vérifier la version dans l’écran A propos de Designer.

1. Ouvrez le formulaire dont vous souhaitez modifier le contenu de la page zéro.

1. Cliquez sur **Fichier > Propriétés du formulaire**.

1. In the Form Properties dialog, click ![plus](assets/plus.png) (Plus icon) to add a custom property.

1. Spécifiez **_pagezerocontent** en tant que nom de propriété.
1. Ajoutez le nouveau message de la page zéro au format Rich Text, en tant que valeur. Par exemple :

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Enregistrez le formulaire au format PDF.

1. Affichez le formulaire PDF dans le navigateur pour vous assurer que le message a été mis à jour. La valeur d’exemple évoquée ci-dessus apparaît comme suit : 

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>La propriété personnalisée créée peut ne pas s’afficher correctement dans la boîte de dialogue Propriétés du formulaire lors de la réouverture du formulaire. Toutefois, le formulaire fonctionne correctement et affiche le message mis à jour sur la page zéro.

