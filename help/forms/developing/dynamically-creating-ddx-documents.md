---
title: Création dynamique de documents DDX
seo-title: Dynamically Creating DDX Documents
description: Créez un document DDX de manière dynamique à l’aide de l’API Java et de l’API Web Service. La création dynamique d’un document DDX vous permet d’utiliser dans le document DDX des valeurs obtenues lors de l’exécution.
seo-description: Create a DDX document dynamically using the Java API and Web Service API. Dynamically creating a DDX document enables you to use values in the DDX document that are obtained during run-time.
uuid: b73e8069-6c9f-4517-a0ae-f3d503191d2d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 2ad227de-68a8-446f-8c4f-a33a6f95bec8
role: Developer
exl-id: 883b33c8-50b1-4df2-a762-02be67ce24f1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2149'
ht-degree: 4%

---

# Création dynamique de documents DDX {#dynamically-creating-ddx-documents}

Vous pouvez créer dynamiquement un document DDX qui peut être utilisé pour effectuer une opération Assembler. La création dynamique d’un document DDX vous permet d’utiliser dans le document DDX des valeurs obtenues lors de l’exécution. Pour créer dynamiquement un document DX, utilisez des classes appartenant au langage de programmation que vous utilisez. Par exemple, si vous développez votre application cliente à l’aide de Java, utilisez des classes appartenant à la variable `org.w3c.dom.*`module. De même, si vous utilisez Microsoft .NET, utilisez des classes appartenant à la variable `System.Xml` espace de noms.

Avant de pouvoir transmettre le document DX au service Assembler, convertissez le fichier XML à partir d’un `org.w3c.dom.Document` vers une instance `com.adobe.idp.Document` instance. Si vous utilisez des services Web, convertissez le XML à partir du type de données utilisé pour créer le XML (par exemple, `XmlDocument`) en `BLOB` instance.

Pour cette discussion, supposons que le document DDX suivant est créé dynamiquement.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
      <PDFsFromBookmarks prefix="stmt"> 
     <PDF source="AssemblerResultPDF.pdf"/> 
 </PDFsFromBookmarks> 
 </DDX>
```

Ce document DDX désassemble un document PDF. Il est recommandé de vous familiariser avec le démontage de documents PDF.

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour désassembler un document PDF à l’aide d’un document DDX créé dynamiquement, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Créez le document DDX.
1. Convertissez le document DX.
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

**Création d’un client Assembler PDF**

Avant de pouvoir effectuer une opération Assembler par programmation, créez un client de service Assembler.

**Création du document DDX**

Créez un document DDX à l’aide du langage de programmation que vous utilisez. Pour créer un document DDX qui désassemble un document de PDF, assurez-vous qu’il contient la variable `PDFsFromBookmarks` élément . Convertissez le type de données utilisé pour créer le document DDX en un `com.adobe.idp.Document` si vous utilisez l’API Java. Si vous utilisez des services Web, convertissez le type de données en un `BLOB` instance.

**Convertir le document DDX**

Un document DDX créé à l’aide de `org.w3c.dom` Les classes doivent être converties en `com.adobe.idp.Document` . Pour effectuer cette tâche lors de l’utilisation de l’API Java, utilisez les classes de transformation XML Java. Si vous utilisez des services Web, convertissez le document DDX en un `BLOB` .

**Référencer un document de PDF à désassembler**

Pour désassembler un document de PDF, référencez un fichier de PDF qui représente le document de PDF à désassembler. Lorsqu’il est transmis au service Assembler, un document de PDF distinct est renvoyé pour chaque signet de niveau 1 dans le document.

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lors de l’exécution d’une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur. Pour définir les options d’exécution, vous utilisez une `AssemblerOptionSpec` .

**Désassemblage du document du PDF**

Désassemblez le document du PDF en appelant la méthode `invokeDDX` opération. Transmettez le document DDX qui a été créé dynamiquement. Le service Assembler renvoie des documents PDF désassemblés dans un objet de collection.

**Enregistrement des documents de PDF désassemblés**

Tous les documents de PDF désassemblés sont renvoyés dans un objet de collection. Effectuez une itération sur l’objet de collection et enregistrez chaque document de PDF en tant que fichier de PDF.

**Voir également**

[Création dynamique d’un document DX à l’aide de l’API Java](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-java-api)

[Création dynamique d’un document DX à l’aide de l’API de service Web](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démontage programmatique de documents PDF](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## Création dynamique d’un document DX à l’aide de l’API Java {#dynamically-create-a-ddx-document-using-the-java-api}

Créez de manière dynamique un document DX et désassemblez un document de PDF à l’aide de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Créez le document DDX.

   * Création d’un Java `DocumentBuilderFactory` en appelant la fonction `DocumentBuilderFactory` class’ `newInstance` .
   * Création d’un Java `DocumentBuilder` en appelant la fonction `DocumentBuilderFactory` de `newDocumentBuilder` .
   * Appelez le `DocumentBuilder` de `newDocument` pour instancier une `org.w3c.dom.Document` .
   * Créez l’élément racine du document DDX en appelant la méthode `org.w3c.dom.Document` de `createElement` . Cette méthode crée une `Element` qui représente l’élément racine. Transmettez une valeur string représentant le nom de l’élément au `createElement` . Convertissez la valeur de retour en `Element`. Ensuite, définissez une valeur pour l’élément enfant en appelant son `setAttribute` . Enfin, ajoutez l’élément à l’élément d’en-tête en appelant le `appendChild` et transmettez l’objet d’élément enfant en tant qu’argument. Les lignes de code suivantes présentent cette logique d’application :
      ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Créez le `PDFsFromBookmarks` en appelant la fonction `Document` de `createElement` . Transmettez une valeur string représentant le nom de l’élément au `createElement` . Convertissez la valeur de retour en `Element`. Définissez une valeur pour la variable `PDFsFromBookmarks` en appelant `setAttribute` . Ajoutez la variable `PDFsFromBookmarks` à l’élément `DDX` en appelant le de l’élément DX `appendChild` . Transmettez la variable `PDFsFromBookmarks` objet d’élément en tant qu’argument. Les lignes de code suivantes présentent cette logique d’application :

      ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Créez un `PDF` en appelant la fonction `Document` de `createElement` . Transmettez une valeur string qui représente le nom de l’élément. Convertissez la valeur de retour en `Element`. Définissez une valeur pour la variable `PDF` en appelant `setAttribute` . Ajoutez la variable `PDF` à l’élément `PDFsFromBookmarks` en appelant la fonction `PDFsFromBookmarks` élément `appendChild` . Transmettez la variable `PDF` objet d’élément en tant qu’argument. Les lignes de code suivantes présentent cette logique d’application :

      ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Convertissez le document DX.

   * Créez un `javax.xml.transform.Transformer` en appelant le `javax.xml.transform.Transformer` statique de l’objet `newInstance` .
   * Créez un `Transformer` en appelant le `TransformerFactory` de `newTransformer` .
   * Créez un objet `ByteArrayOutputStream` en utilisant son constructeur.
   * Créez un objet `javax.xml.transform.dom.DOMSource` en utilisant son constructeur. Transmettez la variable `org.w3c.dom.Document` qui représente le document DDX.
   * Créez un objet `javax.xml.transform.dom.DOMSource` en utilisant son constructeur et en transmettant l’objet `ByteArrayOutputStream`. 
   * Renseignement du code Java `ByteArrayOutputStream` en appelant le `javax.xml.transform.Transformer` de `transform` . Transmettez la variable `javax.xml.transform.dom.DOMSource` et le `javax.xml.transform.stream.StreamResult` objets.
   * Créez un tableau d’octets et affectez la taille de la variable `ByteArrayOutputStream` vers le tableau d’octets.
   * Renseignez le tableau d’octets en appelant la variable `ByteArrayOutputStream` de `toByteArray` .
   * Créez un `com.adobe.idp.Document` en utilisant son constructeur et en transmettant le tableau d’octets.

1. Référencez un document de PDF à désassembler.

   * Créez un `java.util.Map` utilisé pour stocker des documents de PDF d’entrée à l’aide d’un objet `HashMap` constructeur.
   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement du document du PDF à désassembler.
   * Créez un `com.adobe.idp.Document` . Transmettez la variable `java.io.FileInputStream` contenant le document du PDF à désassembler.
   * Ajoutez une entrée au `java.util.Map` en appelant son objet `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX. (Dans le document DDX créé dynamiquement, la valeur est `AssemblerResultPDF.pdf`.)
      * A `com.adobe.idp.Document` contenant le document du PDF à désassembler.

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Désassemblez le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document DDX créé dynamiquement
   * A `java.util.Map` qui contient le document du PDF à désassembler
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation de la tâche

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` contenant les documents de PDF désassemblés et les exceptions survenues.

1. Enregistrez les documents de PDF désassemblés.

   Pour obtenir les documents de PDF désassemblés, effectuez les actions suivantes :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette méthode renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez le résultat `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document du PDF.

**Voir également**

[Démarrage rapide (mode SOAP) : Création dynamique d’un document DX à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-dynamically-creating-a-ddx-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Création dynamique d’un document DX à l’aide de l’API de service Web {#dynamically-create-a-ddx-document-using-the-web-service-api}

Créez de manière dynamique un document DX et désassemblez un document de PDF à l’aide de l’API Assembler Service (service Web) :

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

1. Créez le document DDX.

   * Créez un objet `System.Xml.XmlElement` en utilisant son constructeur.
   * Créez l’élément racine du document DDX en appelant la méthode `XmlElement` de `CreateElement` . Cette méthode crée une `Element` qui représente l’élément racine. Transmettez une valeur string représentant le nom de l’élément au `CreateElement` . Définissez une valeur pour l’élément DDX en appelant son `SetAttribute` . Enfin, ajoutez l’élément au document DDX en appelant la fonction `XmlElement` de `AppendChild` . Transmettez l’objet DDX en tant qu’argument. Les lignes de code suivantes présentent cette logique d’application :

      ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * Création du document DDX `PDFsFromBookmarks` en appelant la fonction `XmlElement` de `CreateElement` . Transmettez une valeur string représentant le nom de l’élément au `CreateElement` . Ensuite, définissez une valeur pour l’élément en appelant son `SetAttribute` . Ajoutez la variable `PDFsFromBookmarks` à l’élément racine en appelant la méthode `DDX` élément `AppendChild` . Transmettez la variable `PDFsFromBookmarks` objet d’élément en tant qu’argument. Les lignes de code suivantes présentent cette logique d’application :

      ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * Création du document DDX `PDF` en appelant la fonction `XmlElement` de `CreateElement` . Transmettez une valeur string représentant le nom de l’élément au `CreateElement` . Ensuite, définissez une valeur pour l’élément enfant en appelant son `SetAttribute` . Ajoutez la variable `PDF` à l’élément `PDFsFromBookmarks` en appelant la fonction `PDFsFromBookmarks` élément `AppendChild` . Transmettez la variable `PDF` objet d’élément en tant qu’argument. Les lignes de code suivantes présentent cette logique d’application :

      ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Convertissez le document DX.

   * Créez un objet `System.IO.MemoryStream` en utilisant son constructeur.
   * Renseignez la variable `MemoryStream` avec le document DDX en utilisant la propriété `XmlElement` qui représente le document DDX. Appeler la variable `XmlElement` de `Save` et transmettez la méthode `MemoryStream` .
   * Créez un tableau d’octets et renseignez-le avec les données situées dans la variable `MemoryStream` . Le code suivant présente la logique de l’application :

      ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Créez un `BLOB` . Affectez le tableau d’octets au `BLOB` de `MTOM` champ .

1. Référencez un document de PDF à désassembler.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF d’entrée. Ceci `BLOB` est transmis à l’objet `invokeOneDocument` comme argument.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` propriété le contenu du tableau d’octets.

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` membre de données.

1. Désassemblez le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document DDX créé dynamiquement
   * Le `mapItem` tableau contenant le document du PDF d’entrée
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeDDX` renvoie une `AssemblerResult` contenant les résultats de la tâche et les exceptions survenues.

1. Enregistrez les documents de PDF désassemblés.

   Pour obtenir les documents de PDF nouvellement créés, procédez comme suit :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les documents de PDF désassemblés.
   * Effectuez une itération à l’aide du `Map` pour obtenir chaque document généré. Convertissez ensuite le de `value` à `BLOB`.
   * Extrayez les données binaires qui représentent le document du PDF en accédant à ses `BLOB` de `MTOM` . Cette opération renvoie un tableau d’octets que vous pouvez écrire dans un fichier de PDF.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
