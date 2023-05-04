---
title: Bases de la gestion des certificats et des informations d’identification
seo-title: Basics of managing certificates and credentials
description: Découvrez les principes de base de la gestion des certificats et des informations d’identification.
seo-description: Learn about the basics of managing certificates and credentials.
uuid: f421e206-e7b5-416c-b9fb-974094f10a66
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 986d16fc-4c81-4785-b1f3-fe8bd7ff669e
exl-id: 4817d150-9bfe-4cb9-8f06-6ff4eaaa6f55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 25%

---

# Bases de la gestion des certificats et des informations d’identification {#basics-of-managing-certificates-and-credentials}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

A *credential* contient les informations de clé privée nécessaires à la signature ou à l’identification des documents. A *certificate* est une information de clé publique que vous configurez pour trust. AEM forms utilise des certificats et des informations d’identification à plusieurs fins :

* Les extensions d’Acrobat Reader DC utilisent des informations d’identification pour activer les droits Adobe Reader des documents PDF. (Voir [Configuration des informations d’identification à utiliser avec les extensions Acrobat Reader DC](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).)
* Vous pouvez configurer Rights Management pour qu’il affiche les informations d’identification à utiliser dans Acrobat uniquement pour les émetteurs approuvés. (Voir [Configuration des paramètres d’affichage du Rights Management](/help/forms/using/admin-help/configuring-client-server-options.md#configure-document-security-display-settings).) Le nom commun (CN) doit être présent dans le certificat.
* Le service Signature accède aux certificats et aux informations d’identification. Pour plus d’informations sur le service Signature, voir [Référence des services](https://help.adobe.com/fr_FR/livecycle/11.0/Services/index.html).

**Génération d’une paire de clés**

AEM forms utilise son Trust Store pour stocker et gérer des certificats, des informations d’identification et des listes de révocation des certificats (CRL). De plus, vous pouvez utiliser un périphérique HSM (Hardware Security Module, module de sécurité matérielle) indépendant pour stocker des clés privées.

AEM forms ne fournit aucune option pour générer une paire de clés. Cependant, vous pouvez le générer à l’aide d’outils tels que Java keytool, et l’importer dans le Trust Store d’AEM forms. Pour plus d’informations sur Java keytool, voir :

[https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html](https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html)

[https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html](https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html)

[https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL](https://helpcenter.gsx.com/hc/fr-fr/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL)

Les types de signature suivants sont pris en charge et peuvent être importés dans AEM Forms :

* Signature XML
* XMLTimeStampToken
* RFC 3161 TimeStampToken
* PKCS#7
* PKCS#1
* Signatures DSA

**Gestion de la clé perdue ou compromise**

Si vous pensez que votre clé est perdue ou a été compromise, procédez comme suit :

1. Informer l’autorité de certification afin qu’elle ajoute la clé compromise sur la liste de révocation du certificat pour révoquer la clé.
1. Procurez-vous une nouvelle clé et ses certificats auprès de l’autorité de certification.
1. Signez à nouveau les documents qui ont été signés à l’aide de la clé compromise à l’aide de la nouvelle clé.
