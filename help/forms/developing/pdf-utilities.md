---
title: Utilisation des utilitaires PDF
seo-title: Working with PDF Utilities
description: Utilisez le service PDF Utilities pour convertir les formats de fichiers PDF et XDP, définir et récupérer les propriétés du document du PDF et manipuler XMP métadonnées.
seo-description: Use the PDF Utilities service to convert between PDF and XDP file formats, set and retrieve PDF document properties, and manipulate XMP metadata.
uuid: a2ea2359-c547-4f1b-b6ca-f276f816e36a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: d816bf2e-5236-4084-b7c4-c32b72cdff97
role: Developer
exl-id: 1fdabd73-ee74-426b-b815-68022ea27c4e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2565'
ht-degree: 5%

---

# Utilisation des utilitaires PDF {#working-with-pdf-utilities}

**À propos du service PDF Utilities**

Le service PDF Utilities peut convertir les formats de fichiers PDF et XDP, définir et récupérer les propriétés du document du PDF et manipuler XMP métadonnées. Par exemple, avant de convertir un document de PDF dans un autre format, il est utile d’examiner ses propriétés pour déterminer l’opération de service à appeler pour la conversion.

Vous pouvez accomplir ces tâches à l’aide du service PDF Utilities :

* Convertissez des documents PDF en documents XDP.
* Convertissez des documents XDP en documents PDF. (Voir [Conversion de documents XDP en documents PDF](pdf-utilities.md#converting-xdp-documents-into-pdf-documents).)
* Récupérez les propriétés du document du PDF. (Voir [Récupération des propriétés du document du PDF](pdf-utilities.md#retrieving-pdf-document-properties).)
* Enregistrez un document PDF et optimisez-le pour un affichage web rapide. (Voir [Définition des modes d’enregistrement des documents PDF](pdf-utilities.md#setting-pdf-document-save-modes).)

>[!NOTE]
>
>Pour plus d’informations sur le service PDF Utilities, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Conversion de documents PDF en documents XDP {#converting-pdf-documents-into-xdp-documents}

Vous pouvez utiliser les API Java et Web PDF Utilities pour convertir par programmation des documents PDF en documents XDP.

>[!NOTE]
>
>Pour plus d’informations sur le service PDF Utilities, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour convertir un document de PDF en document XDP, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client PDFUtilityService.
1. Appelez l’opération de conversion PDF vers XDP.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un client PDFUtilityService**

Avant d’effectuer par programmation une opération PDF Utilities, vous devez créer un client PDFUtilityService . Avec l’API Java, vous pouvez y parvenir en créant une `PDFUtilityServiceClient` . Avec l’API de service Web, vous pouvez y parvenir en utilisant une `PDFUtilityServiceService` .

**Appeler l’opération de conversion PDF vers XDP**

Après avoir créé le client de service, vous pouvez appeler l’opération de conversion PDF vers XDP.

**Voir également**

[Convertir des documents PDF en documents XDP à l’aide de l’API Java](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Convertir des documents PDF en documents XDP à l’aide de l’API de service Web](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertir des documents PDF en documents XDP à l’aide de l’API Java {#convert-pdf-documents-into-xdp-documents-using-the-java-api}

Convertissez des documents PDF en documents XDP à l’aide de l’API PDF Utilities (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-pdfutility-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Appeler l’opération de conversion PDF vers XDP

   Pour effectuer la conversion, appelez la méthode `PDFUtilityServiceClient` de `convertPDFtoXDP` et transmettre une `com.adobe.idp.Document` qui représente le fichier du PDF. La méthode renvoie une `com.adobe.idp.Document` qui représente le fichier XDP nouvellement créé.

**Voir également**

[Conversion de documents PDF en documents XDP](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertir des documents PDF en documents XDP à l’aide de l’API de service Web {#convert-pdf-documents-into-xdp-documents-using-the-web-service-api}

Convertissez des documents PDF en documents XDP à l’aide de l’API PDF Utilities (service Web) :

1. Inclure les fichiers de projet

   * Créez un assemblage client Microsoft .NET qui utilise le fichier WSDL du service PDF Utilities.
   * Référencez l’assemblage client Microsoft .NET.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceService` en utilisant votre constructeur de classe proxy.

1. Appeler l’opération de conversion PDF vers XDP

   Appeler la variable `PDFUtilityServiceService` de `convertPDFtoXDP` et transmettre une `BLOB` qui représente le fichier du PDF. La méthode renvoie une `BLOB` qui représente le fichier XDP nouvellement créé.

**Voir également**

[Conversion de documents PDF en documents XDP](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Création d’un assemblage client .NET utilisant le codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Conversion de documents XDP en documents PDF {#converting-xdp-documents-into-pdf-documents}

Vous pouvez utiliser les API Java et Web PDF Utilities pour convertir par programmation des documents XDP en documents PDF.

>[!NOTE]
>
>Pour plus d’informations sur le service PDF Utilities, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-1}

Pour convertir un document XDP en document PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client PDFUtilityService.
1. Appelez l’opération de conversion XDP vers PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un client PDFUtilityService**

Avant d’effectuer par programmation une opération PDF Utilities, vous devez créer un client PDFUtilityService . Avec l’API Java, vous pouvez y parvenir en créant une `PDFUtilityServiceClient` . Avec l’API de service Web, vous pouvez y parvenir en utilisant une `PDFUtilityServiceService` .

**Appeler l’opération de conversion XDP vers PDF**

Après avoir créé le client de service, vous pouvez appeler l’opération de conversion XDP vers PDF.

**Voir également**

[Convertir des documents XDP en documents PDF à l’aide de l’API Java](pdf-utilities.md#convert-xdp-documents-into-pdf-documents-using-the-java-api)

[Conversion de documents XDP en documents PDF à l’aide de l’API de service Web](pdf-utilities.md#converting-xdp-documents-into-pdf-documents-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertir des documents XDP en documents PDF à l’aide de l’API Java {#convert-xdp-documents-into-pdf-documents-using-the-java-api}

Convertissez des documents XDP en documents PDF à l’aide de l’API PDF Utilities (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-pdfutility-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Appeler l’opération de conversion XDP vers PDF

   Pour effectuer la conversion, appelez la méthode `PDFUtilityServiceClient` de `convertXDPtoPDF` et transmettre une `com.adobe.idp.Document` qui représente le fichier XDP. La méthode renvoie une `com.adobe.idp.Document` qui représente le fichier de PDF nouvellement créé.

**Voir également**

[Conversion de documents XDP en documents PDF](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Conversion de documents XDP en documents PDF à l’aide de l’API de service Web {#converting-xdp-documents-into-pdf-documents-using-the-web-service-api}

Convertissez des documents XDP en documents PDF à l’aide de l’API PDF Utilities (API de service Web) :

1. Inclure les fichiers de projet

   * Créez un assemblage client Microsoft .NET qui utilise le fichier WSDL du service PDF Utilities.
   * Référencez l’assemblage client Microsoft .NET.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceService` en utilisant votre constructeur de classe proxy.

1. Appeler l’opération de conversion XDP vers PDF

   Pour effectuer la conversion, appelez la méthode `PDFUtilityServiceService` de `convertXDPtoPDF` et transmettre une `BLOB` qui représente le fichier XDP. La méthode renvoie une `BLOB` qui représente le fichier de PDF nouvellement créé.

**Voir également**

[Conversion de documents XDP en documents PDF](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Création d’un assemblage client .NET utilisant le codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Récupération des propriétés du document du PDF {#retrieving-pdf-document-properties}

Vous pouvez utiliser les API Java et Web PDF Utilities pour récupérer par programmation les propriétés du document du PDF, par exemple s’il s’agit d’un formulaire à remplir ou de la version Acrobat minimale requise pour lire le document.

>[!NOTE]
>
>Pour plus d’informations sur le service PDF Utilities, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Résumé des étapes {#summary_of_steps-2}

Pour récupérer les propriétés du document PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client PDFUtilityService.
1. Appelez l’opération de récupération des propriétés.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un client PDFUtilityService**

Avant d’effectuer par programmation une opération PDF Utilities, vous devez créer un client PDFUtilityService . Avec l’API Java, vous pouvez y parvenir en créant une `PDFUtilityServiceClient` . Avec l’API de service Web, cette opération s’effectue à l’aide d’une `PDFUtilityServiceService` .

**Appeler l’opération de récupération des propriétés**

Après avoir créé le client de service, vous pouvez appeler l’opération de récupération des propriétés.

**Voir également**

[Récupération des propriétés du document du PDF à l’aide de l’API Java](pdf-utilities.md#retrieve-pdf-document-properties-using-the-java-api)

[Récupération des propriétés de document du PDF à l’aide de l’API de service Web](pdf-utilities.md#retrieve-pdf-document-properties-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Récupération des propriétés du document du PDF à l’aide de l’API Java {#retrieve-pdf-document-properties-using-the-java-api}

Récupérez les propriétés du document du PDF à l’aide de l’API PDF Utilities (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-pdfutility-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Appeler l’opération de récupération des propriétés

   Pour effectuer la conversion, appelez la méthode `PDFUtilityServiceClient` de `getPDFProperties` et transmettez les éléments suivants :

   * A `com.adobe.idp.Document` qui représente le document du PDF.
   * A `PDFPropertiesOptionSpec` contenant les propriétés à évaluer.

   La méthode renvoie une `PDFPropertiesResult` contenant les résultats de la requête.

**Voir également**

[Récupération des propriétés du document du PDF](pdf-utilities.md#retrieving-pdf-document-properties)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Récupération des propriétés de document du PDF à l’aide de l’API de service Web {#retrieve-pdf-document-properties-using-the-web-service-api}

Récupérez les propriétés de document du PDF à l’aide de l’API du service Web PDF Utilities :

1. Inclure les fichiers de projet

   * Créez un assemblage client Microsoft .NET qui utilise le fichier WSDL du service PDF Utilities.
   * Référencez l’assemblage client Microsoft .NET.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceService` en utilisant votre constructeur de classe proxy.

1. Appeler l’opération de récupération des propriétés

   Pour effectuer la conversion, appelez la méthode `PDFUtilityServiceService` de `getPDFProperties` et transmettez les éléments suivants :

   * A `BLOB` qui représente le document du PDF.
   * A `PDFPropertiesOptionSpec` contenant les propriétés à évaluer.

   La méthode renvoie une `PDFPropertiesResult` contenant les résultats de la requête.

**Voir également**

[Récupération des propriétés du document du PDF](pdf-utilities.md#retrieving-pdf-document-properties)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Création d’un assemblage client .NET utilisant le codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Définition des modes d’enregistrement des documents PDF {#setting-pdf-document-save-modes}

Vous pouvez utiliser les API Java et Web Service PDF Utilities pour configurer par programmation un mode d’enregistrement pour un document PDF. Lors de l’utilisation du service PDF Utilities pour définir un mode d’enregistrement, le service PDF Utilities définit uniquement le mode d’enregistrement et n’enregistre pas réellement le document du PDF. Le document du PDF est enregistré lorsqu’il est transmis à une autre opération de service. Par exemple, vous pouvez utiliser le service PDF Utilities pour définir un mode d’enregistrement spécifique et le transmettre au service Encryption, où le document du PDF est réellement enregistré et chiffré.

>[!NOTE]
>
>Pour plus d’informations sur le service PDF Utilities, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-3}

Pour définir l’option d’enregistrement pour les documents de PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client PDFUtilityService.
1. Définissez le mode d’enregistrement.
1. Appelez l’opération d’enregistrement.
1. Transmettez le document du PDF à une autre opération.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un client PDFUtilityService**

Avant d’effectuer par programmation une opération PDF Utilities, vous devez créer un client PDFUtilityService . Avec l’API Java, vous pouvez y parvenir en créant une `PDFUtilityServiceClient` . Avec l’API de service Web, cette opération s’effectue à l’aide d’une `PDFUtilityServiceService` .

**Définition du mode d’enregistrement**

Vous pouvez choisir l’une des options d’enregistrement suivantes :

* `INCREMENTAL`: Pour économiser de manière incrémentielle afin de réduire le temps nécessaire à l’enregistrement
* `FAST_WEB_VIEW`: enregistrer pour un affichage web rapide ;
* `FULL`: Enregistrement complet (sans optimisation)

**Appeler l’opération d’enregistrement de style**

Après avoir créé le client de service, vous pouvez appeler l’opération de récupération des propriétés.

**Transmettre le document du PDF à une autre opération AEM Forms**

Une fois que le service PDF Utilities définit le mode d’enregistrement spécifié, transmettez le document du PDF à une autre opération AEM Forms. Une fois renvoyé à partir de cette opération, le document du PDF est enregistré dans le mode spécifié. Par exemple, si vous utilisez le service PDF Utilities pour définir la variable `FAST_WEB_VIEW` puis transmettez le document du PDF au service Encryption `encryptUsingPassword` , le document de PDF renvoyé est chiffré avec un mot de passe et enregistré dans la variable `FAST_WEB_VIEW` mode .

>[!NOTE]
>
>Le didacticiel de mise en route associé à cette section définit la variable `FAST_WEB_VIEW` puis transmet le document du PDF au service Encryption. `encryptUsingPassword` opération.

**Voir également**

[Définition des options d’enregistrement de document PDF à l’aide de l’API Java](pdf-utilities.md#set-pdf-document-save-options-using-the-java-api)

[Définition des options d’enregistrement de documents PDF à l’aide de l’API de service Web](pdf-utilities.md#set-pdf-document-save-options-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Chiffrement de documents PDF avec un mot de passe](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Définition des options d’enregistrement de document PDF à l’aide de l’API Java {#set-pdf-document-save-options-using-the-java-api}

Définissez les options d’enregistrement du document du PDF à l’aide de l’API PDF Utilities (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-pdfutility-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Définition du mode d’enregistrement

   * Créez un objet `PDFUtilitySaveMode` en utilisant son constructeur.
   * Définissez le mode d’enregistrement en appelant la méthode `PDFUtilitySaveMode` de `setSaveStyle` et transmission d’une valeur string qui spécifie le mode d’enregistrement. Par exemple, pour enregistrer pour un affichage web rapide, transmettez `FAST_WEB_VIEW`.

1. Appeler l’opération d’enregistrement de style

   Appeler la variable `PDFUtilityServiceClient` de `setSaveMode` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document du PDF.
   * A `PDFUtilitySaveMode` contenant le style d’enregistrement à utiliser.
   * Valeur booléenne utilisée pour déterminer s’il faut remplacer des paramètres précédents.

   La méthode renvoie une `com.adobe.idp.Document` au format de l’objet à l’aide du style d’enregistrement spécifié.

1. Transmettre le document du PDF à une autre opération AEM Forms

   * Transmettre le `com.adobe.idp.Document` vers une autre opération AEM Forms.

**Voir également**

[Définition des modes d’enregistrement des documents PDF](pdf-utilities.md#setting-pdf-document-save-modes)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Définition des options d’enregistrement de documents PDF à l’aide de l’API de service Web {#set-pdf-document-save-options-using-the-web-service-api}

Définissez les options d’enregistrement du document PDF à l’aide de l’API PDF Utilities (service Web) :

1. Inclure les fichiers de projet

   * Créez un assemblage client Microsoft .NET qui utilise le fichier WSDL du service PDF Utilities.
   * Référencez l’assemblage client Microsoft .NET.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceService` en utilisant votre constructeur de classe proxy.

1. Définition du mode d’enregistrement

   * Créez un objet `PDFUtilitySaveMode` en utilisant son constructeur.
   * Définissez le mode d’enregistrement en attribuant une valeur de chaîne à la variable `PDFUtilitySaveMode` de `saveStyle` qui spécifie le mode d’enregistrement. Par exemple, pour enregistrer pour un affichage web rapide, spécifiez `FAST_WEB_VIEW`.

1. Appeler l’opération d’enregistrement de style

   Appeler la variable `PDFUtilityServiceService` de `setSaveMode` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document du PDF.
   * A `PDFUtilitySaveMode` contenant le style d’enregistrement à utiliser.
   * Valeur booléenne utilisée pour déterminer s’il faut remplacer des paramètres précédents.

   La méthode renvoie une `BLOB` au format de l’objet à l’aide du style d’enregistrement spécifié. Vous pouvez ensuite enregistrer cet objet en tant que document de PDF.

1. Transmettre le document du PDF à une autre opération Forms

   * Transmettre le `BLOB` vers une autre opération AEM Forms.

**Voir également**

[Définition des modes d’enregistrement des documents PDF](pdf-utilities.md#setting-pdf-document-save-modes)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Création d’un assemblage client .NET utilisant le codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Nettoyage des documents PDF {#sanitizing-pdf-documents}

Vous pouvez utiliser les API Java de PDF Utilities pour convertir par programmation des documents PDF en documents XDP.

>[!NOTE]
>
>Pour plus d’informations sur le service PDF Utilities, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-4}

Pour assainir un document PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client PDFUtilityService.
1. Appeler l’opération d’assainissement.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Pour créer une application cliente à l’aide de Java, vous devez inclure les fichiers JAR nécessaires.

**Création d’un client PDFUtilityService**

Avant de pouvoir effectuer une opération d’assainissement par programmation, vous devez créer un client PDFUtilityService . Avec l’API Java, vous pouvez y parvenir en créant une `PDFUtilityServiceClient` .

**Appeler l’opération de conversion PDF vers XDP**

Après avoir créé le client de service, vous pouvez appeler l’opération d’assainissement.

**Voir également**

[Convertir des documents PDF en documents XDP à l’aide de l’API Java](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Convertir des documents PDF en documents XDP à l’aide de l’API de service Web](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### assainir des documents PDF à l’aide de l’API Java ; {#sanitize-pdf-documents-using-the-java-api}

assainir des documents à l’aide de l’API PDF Utilities (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-pdfutility-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Création d’un client PDFUtilityService

   Créez un `PDFUtilityServiceClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Appeler l’opération de conversion PDF vers XDP

   Pour effectuer la conversion, appelez la méthode `PDFUtilityServiceClient` de `convertPDFtoXDP` et transmettre une `com.adobe.idp.Document` qui représente le fichier du PDF. La méthode renvoie une `com.adobe.idp.Document` qui représente le fichier XDP nouvellement créé.

**Voir également**

[Nettoyage des documents PDF](/help/forms/developing/pdf-utilities-service-java-api.md#quick-start-soap-mode-sanitizing-pdf-documents)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
