---
title: Démontage programmatique de documents PDF
seo-title: Programmatically Disassembling PDF Documents
description: Utilisez le service Assembler pour désassembler un document de PDF unique en plusieurs documents de PDF à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Assembler service to disassemble a single PDF document into multiple PDF documents using the Java API and the Web Service API.
uuid: d71cc044-e948-4b7a-b598-b041723b69e9
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 8e38a597-5d22-4d83-95fe-4494fb04e4a3
role: Developer
exl-id: 3f757392-96a0-4f20-91d0-7fbccb1bf171
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 3%

---

# Démontage programmatique de documents PDF {#programmatically-disassembling-pdf-documents}

Vous pouvez désassembler un document de PDF en le transmettant au service Assembler. En règle générale, cette tâche est utile lorsque le document du PDF a été créé à l’origine à partir de nombreux documents individuels, tels qu’une collection d’instructions. Dans l’illustration suivante, DocA est divisé en plusieurs documents cible, où le signet de premier niveau 1 d’une page identifie le début d’un nouveau document cible.

![pd_pd_pdfsfrombookmarks](assets/pd_pd_pdfsfrombookmarks.png)

Pour désassembler un document de PDF, assurez-vous que la variable `PDFsFromBookmarks` se trouve dans le document DX. Le `PDFsFromBookmarks` element est un élément résultant et ne peut être qu’un élément enfant de la fonction `DDX` élément . Il n’y a pas de `result` car elle peut générer plusieurs documents.

Le `PDFsFromBookmarks` génère un seul document pour chaque signet de niveau 1 dans le document source.

Dans le cadre de cette discussion, supposons que le document DDX suivant soit utilisé.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
      <PDFsFromBookmarks prefix="stmt"> 
     <PDF source="AssemblerResultPDF.pdf"/> 
 </PDFsFromBookmarks> 
 </DDX>
```

>[!NOTE]
>
>Avant de lire cette section, il est recommandé de vous familiariser avec l’assemblage de documents PDF à l’aide du service Assembler. (Voir [Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Lors de la transmission d’un seul document de PDF au service Assembler et de la récupération d’un seul document, vous pouvez appeler la fonction `invokeOneDocument` opération. Toutefois, pour désassembler un document de PDF, utilisez la méthode `invokeDDX` car, bien qu’un document de PDF d’entrée soit transmis au service Assembler, le service Assembler renvoie un objet de collection contenant un ou plusieurs documents.

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour désassembler un document PDF, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Référencez un document de PDF à désassembler.
1. Définissez les options d’exécution.
1. Désassemblez le document du PDF.
1. Enregistrez les documents de PDF désassemblés.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBoss, vous devez remplacer adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un client Assembler PDF**

Avant d’effectuer une opération Assembler par programmation, vous devez créer un client de service Assembler.

**Référence à un document DDX existant**

Un document DDX doit être référencé pour désassembler un document de PDF. Ce document DDX doit contenir la variable `PDFsFromBookmarks` élément .

**Référencer un document de PDF à désassembler**

Pour désassembler un document de PDF, référencez un fichier de PDF qui représente le document de PDF à désassembler. Lorsqu’il est transmis au service Assembler, un document de PDF distinct est renvoyé pour chaque signet de niveau 1 dans le document.

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lorsqu’il effectue une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur.

**Désassemblage du document du PDF**

Après avoir créé le client de service Assembler, référencé le document DDX, référencé un document de PDF à désassembler et défini les options d’exécution, vous pouvez désassembler un document de PDF en appelant le `invokeDDX` . Si le document DDX contient des instructions pour désassembler le document du PDF, le service Assembler renvoie les documents du PDF désassemblés dans un objet de collection.

**Enregistrement des documents de PDF désassemblés**

Tous les documents de PDF désassemblés sont renvoyés dans un objet de collection. Effectuez une itération sur l’objet de collection et enregistrez chaque document de PDF en tant que fichier de PDF.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Désassemblage d’un document de PDF à l’aide de l’API Java {#disassemble-a-pdf-document-using-the-java-api}

Désassemblez un document PDF à l’aide de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Référencez un document de PDF à désassembler.

   * Créez un `java.util.Map` utilisé pour stocker des documents de PDF d’entrée à l’aide d’un objet `HashMap` constructeur.
   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement du document du PDF à désassembler.
   * Créez un `com.adobe.idp.Document` et transmettez la variable `java.io.FileInputStream` contenant le document du PDF à désassembler.
   * Ajoutez une entrée au `java.util.Map` en appelant son objet `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX.
      * A `com.adobe.idp.Document` contenant le document du PDF à désassembler.

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Désassemblez le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs requises suivantes :

   * A `com.adobe.idp.Document` objet représentant le document DDX à utiliser
   * A `java.util.Map` qui contient le document du PDF à désassembler
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation de la tâche

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` contenant les documents de PDF désassemblés et les exceptions survenues.

1. Enregistrez les documents de PDF désassemblés.

   Pour obtenir les documents de PDF désassemblés, effectuez les actions suivantes :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette fonction renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez le résultat `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document du PDF.

**Voir également**

[Démontage programmatique de documents PDF](#programmatically-disassembling-pdf-documents)

[Démarrage rapide (mode SOAP) : Démontage d’un document de PDF à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-disassembling-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Désassemblage d’un document de PDF à l’aide de l’API de service Web {#disassemble-a-pdf-document-using-the-web-service-api}

Désassemblez un document PDF à l’aide de l’API Assembler Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante lors de la définition d’une référence de service : `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client Assembler de PDF.

   * Créez un `AssemblerServiceClient` en utilisant son constructeur par défaut.
   * Créez un `AssemblerServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `AssemblerServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez un document DX existant.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour stocker le document DX.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document DDX et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Référencez un document de PDF à désassembler.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF d’entrée. Ceci `BLOB` est transmis à l’objet `invokeOneDocument` comme argument.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` champ le contenu du tableau d’octets.
   * Créez un `MyMapOf_xsd_string_To_xsd_anyType` . Cet objet de collection est utilisé pour stocker le PDF à désassembler.
   * Créez un `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Attribuez une valeur string qui représente le nom de la clé au `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` champ . Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX.
   * Attribuez le `BLOB` qui stocke le document du PDF dans la propriété `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` champ .
   * Ajoutez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` vers l’objet `MyMapOf_xsd_string_To_xsd_anyType` . Appeler la variable `MyMapOf_xsd_string_To_xsd_anyType` object’ `Add` et transmettez la méthode `MyMapOf_xsd_string_To_xsd_anyType` .

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` champ .

1. Désassemblez le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document DDX qui désassemble le document du PDF.
   * Le `MyMapOf_xsd_string_To_xsd_anyType` qui contient le document du PDF à désassembler
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeDDX` renvoie une `AssemblerResult` contenant les résultats de la tâche et les exceptions survenues.

1. Enregistrez les documents de PDF désassemblés.

   Pour obtenir les documents de PDF nouvellement créés, procédez comme suit :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les documents de PDF désassemblés.
   * Effectuez une itération à l’aide du `Map` pour obtenir chaque document généré. Convertissez ensuite le de `value` à `BLOB`.
   * Extrayez les données binaires qui représentent le document du PDF en accédant à ses `BLOB` de `MTOM` . Cette opération renvoie un tableau d’octets que vous pouvez écrire dans un fichier de PDF.

**Voir également**

[Démontage programmatique de documents PDF](#programmatically-disassembling-pdf-documents)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
