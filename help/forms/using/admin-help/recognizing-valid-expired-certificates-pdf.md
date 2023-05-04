---
title: Identifier les certificats valables et les certificats expirés dans les documents PDF
seo-title: Recognizing valid and expired certificates in PDF documents
description: Découvrez comment reconnaître les certificats valides et expirés dans des documents de PDF.
seo-description: Learn how to recognize valid and expired certificates in PDF documents.
uuid: ceeff57a-586f-4f7b-852f-2a637f003d7e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4559218a-65ba-4577-ad26-7721e28971bc
exl-id: 6e2c109c-381f-455d-bd1d-b08c37c0bd67
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 10%

---

# Identifier les certificats valables et les certificats expirés dans les documents PDF {#recognizing-valid-and-expired-certificates-in-pdf-documents}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsqu’un document de PDF auquel des droits d’utilisation sont appliqués par Reader Extensions s’ouvre dans Adobe Reader, une barre d’état s’affiche, décrivant les droits d’utilisation spécifiques activés dans le document de PDF.

Lorsque le certificat numérique qui spécifie les droits d’utilisation d’un document de PDF expire et que le document de PDF est ouvert dans Adobe Reader, une boîte de dialogue s’affiche pour informer l’utilisateur que le document de PDF possède des droits d’utilisation, mais que ces droits sont désactivés. Bien que le message indique que le document du PDF a été modifié ou modifié, ce n’est pas nécessairement le cas. Adobe Reader affiche ce message lorsqu’un certificat expire ou qu’un document est modifié. Dans Adobe Reader 7.0.x ou version ultérieure, vous ne pouvez pas déterminer quel cas est actuellement le problème.

Une fois la boîte de dialogue fermée, Adobe Reader ouvre le document du PDF. Les droits d’utilisation appliqués à l’aide des extensions Acrobat Reader DC ne sont pas disponibles, comme prévu. Si le document du PDF est un formulaire interactif, les champs du formulaire sont verrouillés et l’utilisateur ne peut pas modifier les données du formulaire.
