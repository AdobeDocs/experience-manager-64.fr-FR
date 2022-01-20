---
title: Conversion de Postscript en documents PDF
seo-title: Converting Postscript to PDF Documents
description: Utilisez le service Distiller pour convertir des fichiers PostScript®, Encapsulated PostScript (EPS) et PRN en fichiers de PDF compacts, fiables et plus sécurisés sur un réseau. Le service Distiller convertit un grand nombre de documents imprimés en documents électroniques, tels que des factures et des instructions à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Distiller service to convert PostScript®, Encapsulated PostScript (EPS), and PRN files to compact, reliable, and more secure PDF files over a network. The Distiller service converts large volumes of print documents to electronic documents, such as invoices and statements using the Java API and Web Service API.
uuid: 2143f406-1fdd-4551-a738-1a8388f8d478
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 06ad343a-f74d-41f5-b3c8-b85bb723ceeb
role: Developer
exl-id: 8bfbeef8-d211-4e87-8cd5-adccb21a6e05
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 7%

---

# Conversion de Postscript en documents PDF {#converting-postscript-to-pdf-documents}

## À propos du service Distiller {#about-the-distiller-service}

Le service Distiller® convertit les fichiers PostScript®, Encapsulated PostScript (EPS) et PRN en fichiers de PDF compacts, fiables et plus sécurisés sur un réseau. Ce service est généralement utilisé pour convertir en documents électroniques d’importants volumes de documents papier, tels que des factures et des déclarations. La conversion de documents en PDF permet également aux entreprises d’envoyer à leurs clients un document à la fois dans sa version papier et dans sa version électronique.

>[!NOTE]
>
>Pour plus d’informations sur le service Distiller, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Conversion de PostScript en documents de PDF {#converting-postscript-to-pdf-documents-inner}

Cette rubrique décrit l’utilisation de l’API Distiller Service (Java et service Web) pour convertir par programmation des fichiers PostScript (PS), Encapsulated PostScript (EPS) et PRN en documents PDF.

>[!NOTE]
>
>Pour plus d’informations sur le service Distiller, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour convertir des fichiers PostScript en documents PDF, l’un des éléments suivants doit être installé sur le serveur hébergeant AEM Forms : Package redistribuable Acrobat 9 ou Microsoft Visual C++ 2005.

### Résumé des étapes {#summary-of-steps}

Pour convertir l’un des types pris en charge en document de PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client de service Distiller.
1. Récupérez le fichier à convertir.
1. Appelez l’opération de création de PDF.
1. Enregistrez le document du PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un client de service Distiller**

Avant de pouvoir effectuer par programmation une opération de service Distiller, vous devez créer un client de service Distiller. Si vous utilisez l’API Java, créez une `DistillerServiceClient` . Si vous utilisez l’API de service Web, créez une `DistillerServiceService` .

**Récupération du fichier à convertir**

Vous devez récupérer le fichier que vous souhaitez convertir. Par exemple, pour convertir un fichier PS en document PDF, vous devez récupérer le fichier PS.

**Appeler l’opération de création de PDF**

Après avoir créé le client de service, vous pouvez appeler l’opération de création de PDF. Cette opération nécessite des informations sur le document à convertir, y compris le chemin d’accès au document cible.

**Enregistrement du document du PDF**

Vous pouvez enregistrer le document du PDF en tant que fichier du PDF.

**Voir également**

[Convertir un fichier PostScript en PDF à l’aide de l’API Java](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[Conversion d’un fichier PostScript en PDF à l’aide de l’API du service Web](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Convertir un fichier PostScript en PDF à l’aide de l’API Java {#convert-a-postscript-file-to-pdf-using-the-java-api}

Convertissez un fichier PostScript en document PDF à l’aide de l’API Distiller Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-distiller-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un client de service Distiller.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `DistillerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Récupérez le fichier à convertir.

   * Créez un `java.io.FileInputStream` qui représente le fichier à convertir en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Appelez l’opération de création de PDF.

   Appeler la variable `DistillerServiceClient` de `createPDF` et transmettez les valeurs suivantes :

   * Le `com.adobe.idp.Document` objet représentant le fichier PS, EPS ou PRN à convertir
   * A `java.lang.String` contenant le nom du fichier à convertir
   * A `java.lang.String` contenant le nom des paramètres Adobe PDF à utiliser
   * A `java.lang.String` contenant le nom des paramètres de sécurité à utiliser
   * Une `com.adobe.idp.Document` contenant les paramètres à appliquer lors de la génération du document du PDF
   * Une `com.adobe.idp.Document` qui contient des informations de métadonnées à appliquer au document du PDF

   Le `createPDF` renvoie une `CreatePDFResult` contenant le nouveau document PDF et un fichier journal pouvant être généré. Le fichier journal contient généralement des messages d’erreur ou d’avertissement générés par la requête de conversion.

1. Enregistrez le document du PDF.

   Pour obtenir le document de PDF nouvellement créé, procédez comme suit :

   * Appeler la variable `CreatePDFResult` de `getCreatedDocument` . Cette fonction renvoie une `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document du PDF.

   De même, pour obtenir le document journal, effectuez les actions suivantes.

   * Appeler la variable `CreatePDFResult` de `getLogDocument` . Cette fonction renvoie une `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document journal.


**Voir également**

[Résumé des étapes](converting-postscript-pdf-documents.md#summary-of-steps)

[Démarrage rapide (mode SOAP) : Conversion d’un fichier PostScript en document PDF à l’aide de l’API Java](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Conversion d’un fichier PostScript en PDF à l’aide de l’API du service Web {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Convertissez un fichier PostScript en document PDF à l’aide de l’API Distiller Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client de service Distiller.

   * Créez un `DistillerServiceClient` en utilisant son constructeur par défaut.
   * Créez un `DistillerServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/DistillerService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `DistillerServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `DistillerServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `DistillerServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Récupérez le fichier à convertir.

   * Créez un objet `BLOB` en utilisant son constructeur. Ceci `BLOB` sert à stocker le fichier à convertir en document de PDF.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Appelez l’opération de création de PDF.

   Appeler la variable `DistillerServiceService` de `CreatePDF2` et transmettez les valeurs requises suivantes :

   * Le `BLOB` objet représentant le fichier PS à convertir
   * Chaîne contenant le chemin d’accès au fichier à convertir
   * Objet string contenant les paramètres Adobe PDF à utiliser (par exemple, `Standard`)
   * Un objet string contenant les paramètres de sécurité à utiliser (par exemple, `No Securit`y)
   * Une `BLOB` contenant les paramètres à appliquer lors de la génération du document du PDF
   * Une `BLOB` qui contient des informations de métadonnées à appliquer au document du PDF
   * A `BLOB` paramètre de sortie utilisé pour stocker le document du PDF
   * A `BLOB` paramètre de sortie utilisé pour stocker le journal

1. Enregistrez le document du PDF.

   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF signé et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui a été renvoyé par l’objet `CreatePDF2` (paramètre de sortie). Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
