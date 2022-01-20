---
title: Déterminer si les documents sont conformes au PDF/A
seo-title: Determining Whether Documents Are PDF/A-Compliant
description: Utilisez le service Assembler pour déterminer si un document de PDF est compatible avec le PDF/A à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Assembler service to determine if a PDF document is PDF/A-compliant using the Java API and Web Service API.
uuid: 4e9d8c8f-2153-411b-9c4b-2d14b3c8f4bb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: c429d6e1-7847-43c8-bf75-cb0078dbb9d5
role: Developer
exl-id: fa9d0720-f4bf-4933-ae63-c24bb835cc60
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2082'
ht-degree: 4%

---

# Déterminer si les documents sont conformes au PDF/A {#determining-whether-documents-are-pdf-a-compliant}

Vous pouvez déterminer si un document de PDF est compatible avec le PDF/A à l’aide du service Assembler. Il existe un document PDF/A comme format d’archivage destiné à la conservation à long terme du contenu du document. Les polices sont incorporées dans le document et le fichier est décompressé. Par conséquent, un document PDF/A est généralement plus volumineux qu’un document PDF standard. De plus, un document PDF/A ne contient aucune donnée audio et vidéo.

La spécification PDF/A-1 se compose de deux niveaux de conformité, à savoir A et B. La principale différence entre les deux niveaux est la prise en charge de la structure logique (accessibilité), qui n’est pas requise pour le niveau de conformité B. Quel que soit le niveau de conformité, PDF/A-1 exige que toutes les polices soient incorporées dans le document PDF/A généré. Actuellement, seul PDF/A-1b est pris en charge dans la validation (et la conversion).

Dans le cadre de cette discussion, supposons que le document DDX suivant soit utilisé.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
         <DocumentInformation source="Loan.pdf" result="Loan_result.xml"> 
         <PDFAValidation compliance="PDF/A-1b" resultLevel="Detailed"                       ignoreUnusedResources="true" allowCertificationSignatures="true" /> 
     </DocumentInformation> 
 </DDX>
```

Dans ce document DDX, la variable `DocumentInformation` indique au service Assembler de renvoyer des informations sur le document du PDF d’entrée. Dans le `DocumentInformation` , l’élément `PDFAValidation` indique au service Assembler d’indiquer si le document du PDF d’entrée est compatible avec le PDF/A.

Le service Assembler renvoie des informations spécifiant si le document du PDF d’entrée est compatible avec le PDF/A dans un document XML contenant une `PDFAConformance` élément . Si le document du PDF d’entrée est compatible avec le PDF/A, la valeur de la variable `PDFAConformance` élément `isCompliant` attribute is `true`. Si le document du PDF n’est pas conforme à la norme PDF/A, la valeur de la variable `PDFAConformance` élément `isCompliant` attribute is `false`.

>[!NOTE]
>
>Parce que le document DDX spécifié dans cette section contient une `DocumentInformation` , le service Assembler renvoie des données XML au lieu d’un document de PDF. En d’autres termes, le service Assembler n’assemble ni ne désassemble un document PDF ; elle renvoie des informations sur le document du PDF d’entrée dans un document XML.

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour déterminer si un document de PDF est compatible avec le PDF/A, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Référencez un document de PDF utilisé pour déterminer la conformité du PDF/A.
1. Définissez les options d’exécution.
1. Récupérez des informations sur le document du PDF.
1. Enregistrez le document XML renvoyé.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge autre que JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé. Pour plus d’informations sur l’emplacement de tous les fichiers JAR AEM Forms, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Assembler PDF**

Avant d’effectuer une opération Assembler par programmation, vous devez créer un client de service Assembler.

**Référence à un document DDX existant**

Un document DDX doit être référencé pour effectuer une opération de service Assembler. Pour déterminer si un document de PDF d’entrée est compatible avec le PDF/A, assurez-vous que le document DDX contient la variable `PDFAValidation` dans un élément `DocumentInformation` élément . Le `PDFAValidation` indique au service Assembler de renvoyer un document XML spécifiant si le document du PDF d’entrée est compatible avec le PDF/A.

**Référencer un document de PDF utilisé pour déterminer la conformité du PDF/A**

Un document de PDF doit être référencé et transmis au service Assembler pour déterminer si le document de PDF est compatible avec le PDF/A.

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lorsqu’il effectue une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur. Pour plus d’informations sur les options d’exécution que vous pouvez définir, voir `AssemblerOptionSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Récupération d’informations sur le document du PDF**

Après avoir créé le client de service Assembler, référencé le document DDX, référencé un document de PDF interactif et défini les options d’exécution, vous pouvez appeler la méthode `invokeDDX` opération. Parce que le document DDX contient le `DocumentInformation` , le service Assembler renvoie des données XML au lieu d’un document de PDF.

**Enregistrement du document XML renvoyé**

Le document XML renvoyé par le service Assembler indique si le document du PDF d’entrée est compatible avec le PDF/A. Par exemple, si le document du PDF d’entrée n’est pas conforme à la norme PDF/A, le service Assembler renvoie un document XML contenant l’élément suivant :

```as3
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Enregistrez le document XML en tant que fichier XML afin que vous puissiez ouvrir le fichier et visualiser les résultats.

**Voir également**

[Déterminer si un document est compatible avec le PDF/A à l’aide de l’API Java](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api)

[Déterminer si un document est compatible avec le PDF/A à l’aide de l’API du service Web](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Déterminer si un document est compatible avec le PDF/A à l’aide de l’API Java {#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api}

Déterminez si un document de PDF est compatible avec le PDF/A à l’aide de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX. Pour déterminer si le document du PDF est compatible avec le PDF/A, assurez-vous que le document DDX contient la variable `PDFAValidation` élément contenu dans un `DocumentInformation` élément .
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Référencez un document de PDF utilisé pour déterminer la conformité du PDF/A.

   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement d’un document de PDF utilisé pour déterminer la conformité du PDF/A.
   * Créez un `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream` contenant le document du PDF.
   * Créez un `java.util.Map` objet utilisé pour stocker le document du PDF d’entrée à l’aide d’un `HashMap` constructeur.
   * Ajoutez une entrée au `java.util.Map` en appelant son objet `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la valeur de l’élément source spécifié dans le document DDX. Par exemple, la valeur de l’élément source situé dans le document DDX introduit dans cette section est Loan.pdf.
      * A `com.adobe.idp.Document` contenant le document du PDF d’entrée.

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Récupérez des informations sur le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs requises suivantes :

   * A `com.adobe.idp.Document` objet représentant le document DDX à utiliser
   * A `java.util.Map` qui contient le fichier de PDF d’entrée utilisé pour déterminer la conformité du PDF/A
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` qui contient des données XML spécifiant si le document du PDF d’entrée est compatible avec PDF/A.

1. Enregistrez le document XML renvoyé.

   Pour obtenir des données XML qui spécifient si le document du PDF d’entrée est un document du PDF/A, effectuez les actions suivantes :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette fonction renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez le résultat `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document XML. Veillez à enregistrer les données XML sous forme de fichier XML.

**Voir également**

[Démarrage rapide (mode SOAP) : Déterminer si un document est compatible avec le PDF/A à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api) (mode SOAP)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Déterminer si un document est compatible avec le PDF/A à l’aide de l’API du service Web {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}

Déterminez si un document de PDF est compatible avec le PDF/A à l’aide de l’API Assembler Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client Assembler de PDF.

   * Créez un `AssemblerServiceClient` en utilisant son constructeur par défaut.
   * Créez un `AssemblerServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `AssemblerServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez un document DX existant.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour stocker le document DX.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document DDX et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Référencez un document de PDF utilisé pour déterminer la conformité du PDF/A.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF d’entrée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.
   * Créez un `MyMapOf_xsd_string_To_xsd_anyType` . Cet objet de collection est utilisé pour stocker le document du PDF.
   * Créez un `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Attribuez une valeur string qui représente le nom de la clé au `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` champ . Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX.
   * Attribuez le `BLOB` qui stocke le document du PDF dans la propriété `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` champ .
   * Ajoutez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` vers l’objet `MyMapOf_xsd_string_To_xsd_anyType` . Appeler la variable `MyMapOf_xsd_string_To_xsd_anyType` object&#39; `Add` et transmettez la méthode `MyMapOf_xsd_string_To_xsd_anyType` .

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` membre de données.

1. Récupérez des informations sur le document du PDF.

   Appeler la variable `AssemblerServiceService` de `invoke` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document DDX.
   * Le `MyMapOf_xsd_string_To_xsd_anyType` contenant le document du PDF d’entrée. Ses clés doivent correspondre aux noms des fichiers source du PDF et ses valeurs doivent être les suivantes : `BLOB` qui correspond au fichier du PDF d’entrée.
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution.

   Le `invoke` renvoie une `AssemblerResult` qui contient des données XML spécifiant si le document du PDF d’entrée est un document PDF/A.

1. Enregistrez le document XML renvoyé.

   Pour obtenir des données XML qui spécifient si le document du PDF d’entrée est un document du PDF/A, effectuez les actions suivantes :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les données XML qui spécifient si le document du PDF d’entrée est un document PDF/A.
   * Effectuez une itération à l’aide du `Map` pour obtenir chaque document généré. Convertissez ensuite la valeur de ce membre de tableau en une `BLOB`.
   * Extrayez les données binaires qui représentent les données XML en accédant à leurs `BLOB` de `MTOM` champ . Ce champ stocke un tableau d’octets que vous pouvez écrire dans en tant que fichier XML.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
