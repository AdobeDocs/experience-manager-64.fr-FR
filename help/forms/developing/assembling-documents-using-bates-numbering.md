---
title: Assemblage de documents à l’aide de la numérotation Bates
seo-title: Assembling Documents Using Bates Numbering
description: 'Utilisez la numérotation Bates pour assembler des documents PDF à l’aide de l’API Java et Web Service. '
seo-description: Use Bates numbering to assemble PDF documents using the Java and Web Service API.
uuid: 28d5faeb-6915-41a2-b6a0-78d255df024f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 77e9b895-1313-4a5b-a2d5-cdb65bdc1966
role: Developer
exl-id: 902fc62b-262e-4eb4-b580-dbfbf4344fa6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1908'
ht-degree: 5%

---

# Assemblage de documents à l’aide de la numérotation Bates {#assembling-documents-using-bates-numbering}

Vous pouvez assembler des documents PDF qui contiennent des identifiants de page uniques à l’aide de la numérotation Bates. *numérotation Bates* est une méthode d’application d’identifiants uniques à un lot de documents associés. Chaque page du document (ou ensemble de documents) se voit attribuer un numéro Bates qui identifie la page de manière unique. Par exemple, des documents d’entreprise contenant une nomenclature et liés à la production d’un assemblage peuvent contenir un identifiant. Un numéro Bates contient une valeur numérique incrémentée séquentiellement et optionnellement un préfixe et un suffixe. Le préfixe + suffixe numérique + est appelé *modèle bates*.

L’illustration suivante présente un document PDF contenant un identifiant unique, situé dans l’en-tête du document.

![au_au_batesnumber](assets/au_au_batesnumber.png)

Dans le cadre de cette discussion, l’identifiant de page unique est placé dans l’en-tête d’un document. Supposons que le document DX suivant soit utilisé.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
        <PDF result="out.pdf"> 
        <Header> 
         <Center> 
             <StyledText> 
                 <p font-size="20pt"><BatesNumber/></p> 
             </StyledText> 
         </Center> 
     </Header> 
           <PDF source="map.pdf" /> 
          <PDF source="directions.pdf" /> 
          </PDF> 
 </DDX>
```

Ce document DDX fusionne deux documents PDF nommés *map.pdf* et* directions.pdf* dans un document de PDF unique. Le document de PDF généré contient un en-tête constitué d’un identifiant de page unique. Par exemple, le document de l’illustration ci-dessus affiche 000016.

>[!NOTE]
>
>Avant de lire cette section, il est recommandé de vous familiariser avec l’assemblage de documents PDF à l’aide du service Assembler. Cette section ne traite pas des concepts tels que la création d’un objet de collection contenant des documents d’entrée ou l’extraction des résultats de l’objet de collection renvoyé. (Voir [Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour assembler un document PDF contenant un identifiant de page unique (numérotation Bates), effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Documents de PDF de saisie de référence.
1. Définissez la valeur initiale du nombre Bates.
1. Assemblez les documents du PDF d’entrée.
1. Extrayez les résultats.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

Si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge autre que JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé. Pour plus d’informations sur l’emplacement de tous les fichiers JAR AEM Forms, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Assembler PDF**

Avant d’effectuer une opération Assembler par programmation, vous devez créer un client de service Assembler.

**Référence à un document DDX existant**

Un document DDX doit être référencé pour assembler un document de PDF. Prenons l’exemple du document DDX introduit dans cette section. Pour assembler un document PDF contenant des identifiants de page uniques, le document DDX doit contenir le `BatesNumber` élément .

**Documents de PDF de saisie de référence**

Les documents de PDF d’entrée doivent être référencés pour assembler un document de PDF. Par exemple, les documents map.pdf et directions.pdf doivent être référencés pour assembler ces documents de PDF en un seul document de PDF.

**Définition de la valeur initiale du nombre Bates**

Vous pouvez définir la valeur de numéro Bates initiale pour répondre aux besoins de votre entreprise. Supposons, par exemple, qu’il soit nécessaire de définir la valeur initiale sur 000100. Si vous ne définissez pas la valeur initiale, la valeur de la première page est 000000.

**Assemblage des documents du PDF d’entrée**

Après avoir créé le client de service Assembler, référencez le document DDX qui contient `BatesNumber` informations sur les éléments, référencer un document de PDF d’entrée et définir les options d’exécution, vous pouvez appeler la fonction `invokeDDX` qui entraîne l’assemblage par le service Assembler d’un document PDF contenant des identifiants de page uniques.

**Extraire les résultats**

Le service Assembler renvoie un objet de collection contenant les résultats de la tâche. Vous pouvez extraire le document de PDF généré et les exceptions qui sont générées. Dans ce cas, un document de PDF chiffré se trouve dans l’objet de collection.

>[!NOTE]
>
>Un objet de collection est renvoyé si vous appelez la fonction `invokeDDX` opération. Cette opération est utilisée lors de la transmission de plusieurs documents de PDF d’entrée au service Assembler. Cependant, si vous ne transmettez qu’un seul document de PDF d’entrée au service Assembler, vous devez appeler la méthode `invokeOneDocument` opération. Pour plus d’informations sur l’utilisation de cette opération, voir [Assemblage de documents PDF chiffrés](/help/forms/developing/assembling-encrypted-pdf-documents.md).

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblage de documents avec numérotation Bates à l’aide de l’API Java {#assemble-documents-with-bates-numbering-using-the-java-api}

Assemblez un document PDF qui utilise des identifiants de page uniques (numérotation Bates) à l’aide de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Documents de PDF de saisie de référence.

   * Créez un `java.util.Map` utilisé pour stocker des documents de PDF d’entrée à l’aide d’un `HashMap` constructeur.
   * Pour chaque document de PDF d’entrée, créez une `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement du document du PDF d’entrée. Dans ce cas, transmettez l’emplacement d’un document de PDF non sécurisé.
   * Pour chaque document de PDF d’entrée, créez une `com.adobe.idp.Document` et transmettez la variable `java.io.FileInputStream` contenant le document du PDF.
   * Ajoutez une entrée au `java.util.Map` en appelant son objet `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX. Par exemple, le nom du fichier source du PDF spécifié dans le document DDX introduit dans cette section est Loan.pdf.
      * A `com.adobe.idp.Document` contenant le document de PDF non sécurisé.

1. Définissez la valeur initiale du nombre Bates.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez le numéro Bates initial en appelant la variable `AssemblerOptionSpec` de `setFirstBatesNumber` et transmission d’une valeur numérique qui spécifie la valeur initiale.

1. Assemblez les documents du PDF d’entrée.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs requises suivantes :

   * A `com.adobe.idp.Document` qui représente le document DDX.
   * A `java.util.Map` contenant le fichier de PDF non sécurisé d’entrée.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation des tâches.

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` contenant un document de PDF chiffré par mot de passe.

1. Extrayez les résultats.

   Pour obtenir le document de PDF nouvellement créé, procédez comme suit :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette action renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez l’objet `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document du PDF.

**Voir également**

[Démarrage rapide (mode SOAP) : Assemblage d’un document PDF avec numérotation bates à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblage de documents avec numérotation Bates à l’aide de l’API du service Web {#assemble-documents-with-bates-numbering-using-the-web-service-api}

Assemblez un document PDF qui utilise des identifiants de page uniques (numérotation Bates) à l’aide de l’API Assembler Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document DDX et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Documents de PDF de saisie de référence.

   * Pour chaque document de PDF d’entrée, créez une `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF d’entrée.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.
   * Créez un `MyMapOf_xsd_string_To_xsd_anyType` . Cet objet de collection est utilisé pour stocker les documents du PDF d’entrée.
   * Pour chaque document de PDF d’entrée, créez une `MyMapOf_xsd_string_To_xsd_anyType_Item` . Par exemple, si deux documents de PDF d’entrée sont utilisés, créez deux `MyMapOf_xsd_string_To_xsd_anyType_Item` objets.
   * Attribuez une valeur string qui représente le nom de la clé au `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` champ . Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX. (Effectuez cette tâche pour chaque document de PDF d’entrée.)
   * Attribuez le `BLOB` qui stocke le document du PDF dans la propriété `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` champ . (Effectuez cette tâche pour chaque document de PDF d’entrée.)
   * Ajoutez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` vers l’objet `MyMapOf_xsd_string_To_xsd_anyType` . Appeler la variable `MyMapOf_xsd_string_To_xsd_anyType` de `Add` et transmettez la méthode `MyMapOf_xsd_string_To_xsd_anyType` . (Effectuez cette tâche pour chaque document de PDF d’entrée.)

1. Définissez la valeur initiale du nombre Bates.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez le nombre Bates initial en attribuant une valeur numérique à la variable `firstBatesNumber` membre de données qui appartient à `AssemblerOptionSpec` .

1. Assemblez les documents du PDF d’entrée.

   Appeler la variable `AssemblerServiceClient` de `invoke` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document DDX.
   * Le `MyMapOf_xsd_string_To_xsd_anyType` contenant les documents du PDF d’entrée. Ses clés doivent correspondre aux noms des fichiers source du PDF et ses valeurs doivent être les suivantes : `BLOB` qui correspond à ces fichiers.
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution.

   Le `invoke` renvoie une `AssemblerResult` contenant les résultats de la tâche et les exceptions survenues.

1. Extrayez les résultats.

   Pour obtenir le document de PDF nouvellement créé, procédez comme suit :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les documents du PDF de résultats.
   * Effectuez une itération à l’aide du `Map` jusqu’à ce que vous trouviez la clé correspondant au nom du document généré. Collez ensuite le de `value` à `BLOB`.
   * Extrayez les données binaires qui représentent le document du PDF en accédant à ses `BLOB` de `MTOM` . Cette opération renvoie un tableau d’octets que vous pouvez écrire dans un fichier de PDF.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
