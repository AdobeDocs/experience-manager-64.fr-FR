---
title: Utilisation de documents PDF/A
seo-title: Working with PDF/A Documents
description: Utilisez le service DocConverter pour déterminer si un document de PDF est un document de PDF/A et convertir des documents de PDF en documents de PDF/A.
seo-description: Use the  DocConverter service to determine if a PDF document is a PDF/A document and convert PDF documents to PDF/A documents.
uuid: c258d253-068a-4412-955a-21d8a4792d6f
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 1e6cc554-aef1-463c-906b-634b80a27917
role: Developer
exl-id: fbf6c225-5351-4589-97d3-9faf9c5939bc
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2358'
ht-degree: 7%

---

# Utilisation de documents PDF/A {#working-with-pdf-a-documents}

**À propos du service DocConverter**

Le service DocConverter peut convertir des documents de PDF en documents PDA/A. Vous pouvez accomplir ces tâches à l’aide de ce service :

* Convertissez des documents de PDF en documents de PDF/A. (Voir [Conversion de documents en documents PDF/A](pdf-a-documents.md#converting-documents-to-pdf-a-documents).)
* Déterminez si les documents du PDF sont des documents du PDF/A. (Voir [Détermination par programmation de la conformité PDF/A](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

>[!NOTE]
>
>Pour plus d’informations sur le service DocConverter, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Conversion de documents en documents PDF/A {#converting-documents-to-pdf-a-documents}

Vous pouvez utiliser le service DocConverter pour convertir un document de PDF en document de PDF/A. Comme PDF/A est un format d’archivage pour la conservation à long terme du contenu du document, toutes les polices sont incorporées et le fichier est décompressé. Par conséquent, un document PDF/A est généralement plus volumineux qu’un document PDF standard. De plus, un document PDF/A ne contient aucune donnée audio et vidéo. Avant de convertir un document de PDF en document de PDF/A, assurez-vous que le document de PDF n’est pas un document de PDF/A.

La spécification PDF/A-1 se compose de deux niveaux de conformité, à savoir A et B. La principale différence entre les deux concerne la prise en charge de la structure logique (accessibilité), qui n’est pas requise pour le niveau de conformité B. Quel que soit le niveau de conformité, PDF/A-1 exige que toutes les polices soient incorporées dans le document PDF/A généré. Actuellement, seul PDF/A-1b est pris en charge dans la validation (et la conversion).

Bien que PDF/A soit la norme d’archivage des documents de PDF, il n’est pas obligatoire que PDF/A soit utilisé pour l’archivage si un document de PDF standard répond aux exigences de votre entreprise. Le but de la norme PDF/A est d’établir un fichier PDF destiné à l’archivage à long terme et à la conservation des documents.

>[!NOTE]
>
>Pour plus d’informations sur le service DocConverter, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour convertir un document de PDF en document de PDF/A, procédez comme suit :

1. Inclure les fichiers de projet.
1. Création d’un client DocConvert
1. Référencez un document de PDF à convertir en document de PDF/A.
1. Définissez les informations de suivi.
1. Convertissez le document.
1. Enregistrez le document PDF/A.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss Application Server)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss Application Server)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client DocConvert**

Avant d’effectuer par programmation une opération DocConverter, vous devez créer un client DocConverter. Si vous utilisez l’API Java, créez une `DocConverterServiceClient` . Si vous utilisez l’API du service Web DocConverter, créez une `DocConverterServiceService` .

**Référencer un document PDF à convertir en document PDF/A**

Récupérez un document de PDF à convertir en document de PDF/A. Si vous tentez de convertir un document de PDF, tel qu’un formulaire Acrobat, en document de PDF/A, une exception est générée.

**Définition des informations de suivi**

Vous pouvez définir une option d’exécution qui détermine la quantité d’informations suivies pendant le processus de conversion. En d’autres termes, vous pouvez définir neuf niveaux différents qui spécifient le niveau d’informations suivi par le service DocConverter lors de la conversion d’un document de PDF en document de PDF/A.

**Convertir le document**

Après avoir créé le client de service DocConverter, référencez le document du PDF à convertir et définissez l’option d’exécution qui spécifie le suivi des informations, vous pouvez convertir le document du PDF en document du PDF/A.

**Enregistrement du document PDF/A**

Vous pouvez enregistrer le document du PDF/A en tant que fichier du PDF.

**Voir également**

[Convertir des documents en documents PDF/A à l’aide de l’API Java](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-java-api)

[Convertir des documents en documents de PDF/A à l’aide de l’API du service Web](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Détermination par programmation de la conformité PDF/A](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy)

### Convertir des documents en documents PDF/A à l’aide de l’API Java {#convert-documents-to-pdf-a-documents-using-the-java-api}

Convertissez un document de PDF en document de PDF/A à l’aide de l’API Java :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-docconverter-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Création d’un client DocConvert

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `DocConverterServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Référencer un document PDF à convertir en document PDF/A

   * Créez un `java.io.FileInputStream` qui représente le document du PDF à convertir en utilisant son constructeur et en transmettant une valeur string spécifiant l’emplacement du fichier du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définition des informations de suivi

   * Créez un objet `PDFAConversionOptionSpec` en utilisant son constructeur.
   * Définissez le niveau de suivi des informations en appelant la variable `PDFAConversionOptionSpec` de `setLogLevel` et transmission d’une valeur string qui spécifie le niveau de suivi. Par exemple, transmettez la valeur `FINE`. Pour plus d’informations sur les différentes valeurs, voir `setLogLevel` dans la méthode [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Convertir le document

   Convertir le document du PDF en document du PDF/A en appelant le `DocConverterServiceClient` de `toPDFA` et transmission des valeurs suivantes :

   * Le `com.adobe.idp.Document` contenant le document du PDF à convertir
   * Le `PDFAConversionOptionSpec` objet spécifiant les informations de suivi

   Le `toPDFA` renvoie une `PDFAConversionResult` contenant le document PDF/A.

1. Enregistrement du document PDF/A

   * Récupérer le document du PDF/A en appelant la fonction `PDFAConversionResult` de `getPDFA` . Cette méthode renvoie une `com.adobe.idp.Document` qui représente le document PDF/A.
   * Créez un `java.io.File` qui représente le fichier PDF/A. Assurez-vous que l’extension de nom de fichier est .pdf.
   * Renseigner le fichier avec des données de PDF/A en appelant la variable `com.adobe.idp.Document` de `copyToFile` et transmission de la méthode `java.io.File` .

**Voir également**

[Utilisation de documents PDF/A](pdf-a-documents.md#working-with-pdf-a-documents)

[Démarrage rapide (mode SOAP) : Conversion d’un document en document de PDF/A à l’aide de l’API Java](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertir des documents en documents de PDF/A à l’aide de l’API du service Web {#convert-documents-to-pdf-a-documents-using-the-web-service-api}

Convertissez un document de PDF en document de PDF/A à l’aide de l’API DocConverter (service Web) :

1. Inclure les fichiers de projet

   * Créez un assemblage client Microsoft .NET qui utilise le fichier WSDL DocConverter.
   * Référencez l’assemblage client Microsoft .NET.

1. Création d’un client DocConvert

   * À l’aide de l’assemblage client .NET Microsoft, créez une `DocConverterServiceService` en appelant son constructeur par défaut.
   * Définissez la variable `DocConverterServiceService` de `Credentials` membre de données avec un `System.Net.NetworkCredential` qui spécifie le nom d’utilisateur et le mot de passe.

1. Référencer un document PDF à convertir en document PDF/A

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF converti en document du PDF/A.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `binaryData` avec le contenu du tableau d’octets.

1. Définition des informations de suivi

   * Créez un objet `PDFAConversionOptionSpec` en utilisant son constructeur.
   * Définissez le niveau de suivi des informations en attribuant une valeur qui spécifie le niveau de suivi à la variable `PDFAConversionOptionSpec` de `logLevel` membre de données. Par exemple, affectez la valeur `FINE` à ce membre de données.

1. Convertir le document

   Convertir le document du PDF en document du PDF/A en appelant le `DocConverterServiceService` de `toPDFA` et transmission des valeurs suivantes :

   * Le `BLOB` contenant le document du PDF à convertir
   * Le `PDFAConversionOptionSpec` objet spécifiant les informations de suivi

   Le `toPDFA` renvoie une `PDFAConversionResult` contenant le document PDF/A.

1. Enregistrement du document PDF/A

   * Créez un `BLOB` qui stocke le document PDF/A en obtenant la valeur de la propriété `PDFAConversionResult` de `PDFADocument` membre de données.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui a été renvoyé à l’aide de l’objet `PDFAConversionResult` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `binaryData` membre de données.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document PDF/A.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Utilisation de documents PDF/A](pdf-a-documents.md#working-with-pdf-a-documents)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Création d’un assemblage client .NET utilisant le codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Détermination par programmation de la conformité PDF/A {#programmatically-determining-pdf-a-compliancy}

Vous pouvez utiliser le service DocConverter pour déterminer si un document de PDF est compatible avec le PDF/A. Pour plus d’informations sur un document de PDF/A et sur la conversion d’un document de PDF en document de PDF/A, voir [Conversion de documents en documents PDF/A](pdf-a-documents.md#converting-documents-to-pdf-a-documents).

>[!NOTE]
>
>Pour plus d’informations sur le service DocConverter, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-1}

Pour déterminer la conformité du PDF/A, procédez comme suit :

1. Inclure les fichiers de projet.
1. Création d’un client DocConvert
1. Référencez un document de PDF utilisé pour déterminer la conformité du PDF/A.
1. Définissez les options d’exécution.
1. Récupérez des informations sur le document du PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss Application Server)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss Application Server)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client DocConvert**

Avant d’effectuer par programmation une opération DocConverter, vous devez créer un client DocConverter. Si vous utilisez l’API Java, créez une `DocConverterServiceClient` . Si vous utilisez l’API du service Web DocConverter, créez une `DocConverterServiceService` .

**Référencer un document de PDF utilisé pour déterminer la conformité du PDF/A**

Un document de PDF doit être référencé et transmis au service DocConverter afin de déterminer si le document de PDF est compatible avec le PDF/A.

**Définition des options d’exécution**

Vous pouvez définir une option d’exécution qui détermine la quantité d’informations suivies pendant le processus de conversion. En d’autres termes, vous pouvez définir neuf niveaux différents qui spécifient le niveau d’informations suivi par le service DocConverter lors de la conversion d’un document de PDF en document de PDF/A.

**Récupération d’informations sur le document du PDF**

Après avoir créé le client de service DocConverter, référencé le document du PDF et défini les options d’exécution, vous pouvez déterminer si le document du PDF est un document compatible avec le PDF/A.

**Voir également**

[Déterminer la conformité PDF/A à l’aide de l’API Java](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[Déterminer la conformité PDF/A à l’aide de l’API de service Web](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Déterminer la conformité PDF/A à l’aide de l’API Java {#determine-pdf-a-compliancy-using-the-java-api}

Déterminez la conformité du PDF/A à l’aide de l’API Java :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-docconverter-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Création d’un client DocConvert

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `DocConverterServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Référencer un document de PDF utilisé pour déterminer la conformité du PDF/A

   * Créez un `java.io.FileInputStream` qui représente le document du PDF à convertir en utilisant son constructeur et en transmettant une valeur string spécifiant l’emplacement du fichier du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définition des options d’exécution

   * Créez un objet `PDFAValidationOptionSpec` en utilisant son constructeur.
   * Définissez le niveau de conformité en appelant la méthode `PDFAValidationOptionSpec` de `setCompliance` méthode et transmission `PDFAValidationOptionSpec.Compliance.PDFA_1B`.
   * Définissez le niveau de suivi des informations en appelant la variable `PDFAValidationOptionSpec` de `setLogLevel` et transmission d’une valeur string qui spécifie le niveau de suivi. Par exemple, transmettez la valeur `FINE`. Pour plus d’informations sur les différentes valeurs, voir `setLogLevel` dans la méthode [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Récupération d’informations sur le document du PDF

   Déterminez la conformité du PDF/A en appelant le `DocConverterServiceClient` de `isPDFA` et transmission des valeurs suivantes :

   * Le `com.adobe.idp.Document` contenant le document du PDF.
   * Le `PDFAValidationOptionSpec` qui spécifie les options d’exécution.

   Le `isPDFA` renvoie une `PDFAValidationResult` contenant les résultats de cette opération.

**Voir également**

[Utilisation de documents PDF/A](pdf-a-documents.md#working-with-pdf-a-documents)

[Démarrage rapide (mode SOAP) : Détermination de la conformité du PDF/A à l’aide de l’API Java](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Déterminer la conformité PDF/A à l’aide de l’API de service Web {#determine-pdf-a-compliancy-using-the-web-service-api}

Déterminez la conformité PDF/A à l’aide de l’API de service Web :

1. Inclure les fichiers de projet

   * Créez un assemblage client Microsoft .NET qui utilise le fichier WSDL DocConverter.
   * Référencez l’assemblage client Microsoft .NET.

1. Création d’un client DocConvert

   * À l’aide de l’assemblage client .NET Microsoft, créez une `DocConverterServiceService` en appelant son constructeur par défaut.
   * Définissez la variable `DocConverterServiceService` de `Credentials` membre de données avec un `System.Net.NetworkCredential` qui spécifie le nom d’utilisateur et le mot de passe.

1. Référencer un document de PDF utilisé pour déterminer la conformité du PDF/A

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF converti en document du PDF/A.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `binaryData` avec le contenu du tableau d’octets.

1. Définition des options d’exécution

   * Créez un objet `PDFAValidationOptionSpec` en utilisant son constructeur.
   * Définissez le niveau de conformité en attribuant la variable `PDFAValidationOptionSpec` de `compliance` membre de données avec la valeur `PDFAConversionOptionSpec_Compliance.PDFA_1B`.
   * Définissez le niveau de suivi des informations en attribuant la variable `PDFAValidationOptionSpec` de `resultLevel` membre de données avec la valeur `PDFAValidationOptionSpec_ResultLevel.DETAILED`.

1. Récupération d’informations sur le document du PDF

   Déterminez la conformité du PDF/A en appelant le `DocConverterServiceService` de `isPDFA` et transmission des valeurs suivantes :

   * Le `BLOB` contenant le document du PDF.
   * Le `PDFAValidationOptionSpec` contenant les options d’exécution.

   Le `isPDFA` renvoie une `PDFAValidationResult` contenant les résultats de cette opération.

**Voir également**

[Utilisation de documents PDF/A](pdf-a-documents.md#working-with-pdf-a-documents)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Création d’un assemblage client .NET utilisant le codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
