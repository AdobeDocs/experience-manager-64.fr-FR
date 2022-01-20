---
title: Validation de documents DDX
seo-title: Validating DDX Documents
description: Validez un document DDX par programmation à l’aide de l’API Java et de l’API Web Service.
seo-description: Validate a DDX document programmatically using the Java API and the Web Service API.
uuid: da668170-d2e9-4fff-aef5-432a856bd0bd
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 693859b0-a0c3-43f1-95c0-be48a90d7d8d
role: Developer
exl-id: 5be91b23-355b-4e50-b1f5-afed248bc8b5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1512'
ht-degree: 3%

---

# Validation de documents DDX {#validating-ddx-documents}

Vous pouvez valider par programmation un document DDX utilisé par le service Assembler. En d’autres termes, à l’aide de l’API du service Assembler, vous pouvez déterminer si un document DDX est valide ou non. Par exemple, si vous avez effectué une mise à niveau à partir d’une version précédente d’AEM Forms et que vous souhaitez vous assurer que votre document DDX est valide, vous pouvez le valider à l’aide de l’API du service Assembler.

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour valider un document DDX, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler.
1. Référencez un document DX existant.
1. Définissez les options d’exécution pour valider le document DDX.
1. Effectuez la validation.
1. Enregistrez les résultats de la validation dans un fichier journal.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge autre que JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un client Assembler PDF**

Avant d’effectuer une opération Assembler par programmation, vous devez créer un client de service Assembler.

**Référence à un document DDX existant**

Pour valider un document DDX, vous devez référencer un document DDX existant.

**Définition des options d’exécution pour valider le document DDX**

Lors de la validation d’un document DDX, vous devez définir des options d’exécution spécifiques qui demandent au service Assembler de valider le document DDX plutôt que de l’exécuter. Vous pouvez également augmenter la quantité d’informations que le service Assembler écrit dans le fichier journal.

**Effectuer la validation**

Après avoir créé le client de service Assembler, référencé le document DDX et défini les options d’exécution, vous pouvez appeler la méthode `invokeDDX` pour valider le document DDX. Lors de la validation du document DX, vous pouvez transmettre `null` comme paramètre map (ce paramètre stocke généralement les documents PDF dont Assembler a besoin pour effectuer la ou les opérations spécifiées dans le document DDX).

Si la validation échoue, une exception est générée et le fichier journal contient des détails qui expliquent pourquoi le document DDX n’est pas valide à partir de la variable `OperationException` instance. Une fois l’analyse XML de base et la vérification de schéma terminée, la validation de la spécification DDX est effectuée. Toutes les erreurs qui se trouvent dans le document DDX sont spécifiées dans le journal.

**Enregistrer les résultats de la validation dans un fichier journal**

Le service Assembler renvoie les résultats de validation que vous pouvez écrire dans un fichier journal XML. La quantité de détails que le service Assembler écrit dans le fichier journal dépend de l’option d’exécution que vous avez définie.

**Voir également**

[Validation d’un document DDX à l’aide de l’API Java](#validate-a-ddx-document-using-the-java-api)

[Validation d’un document DDX à l’aide de l’API de service Web](#validate-a-ddx-document-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Validation d’un document DDX à l’aide de l’API Java {#validate-a-ddx-document-using-the-java-api}

Validez un document DDX à l’aide de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définissez les options d’exécution pour valider le document DDX.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez l’option d’exécution qui demande au service Assembler de valider le document DDX en appelant la fonction `AssemblerOptionSpec` méthode setValidateOnly de l’objet et transmission `true`.
   * Définissez la quantité d’informations que le service Assembler écrit dans le fichier journal en appelant la variable `AssemblerOptionSpec` de `getLogLevel` et la transmission d’une valeur string répond à vos besoins. Lors de la validation d’un document DDX, vous souhaitez plus d’informations écrites dans le fichier journal, ce qui facilite le processus de validation. Par conséquent, vous pouvez transmettre la valeur `FINE` ou `FINER`.

1. Effectuez la validation.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document DDX.
   * La valeur `null` pour l’objet java.io.Map qui stocke généralement des documents de PDF.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution.

   Le `invokeDDX` renvoie une `AssemblerResult` contenant des informations spécifiant si le document DDX est valide.

1. Enregistrez les résultats de la validation dans un fichier journal.

   * Créez un `java.io.File` et assurez-vous que l’extension de nom de fichier est .xml.
   * Appeler la variable `AssemblerResult` de `getJobLog` . Cette méthode renvoie une `com.adobe.idp.Document` qui contient des informations de validation.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` vers le fichier .

   >[!NOTE]
   >
   >Si le document DDX n’est pas valide, une `OperationException` est généré. Dans l’instruction catch, vous pouvez appeler la fonction `OperationException` de `getJobLog` .

**Voir également**

[Validation de documents DDX](#validating-ddx-documents)

[Démarrage rapide (mode SOAP) : Validation des documents DDX à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api) (mode SOAP)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Validation d’un document DDX à l’aide de l’API de service Web {#validate-a-ddx-document-using-the-web-service-api}

Validez un document DDX à l’aide de l’API Assembler Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacez localhost par l’adresse IP du serveur Forms.

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
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution pour valider le document DDX.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez l’option d’exécution qui indique au service Assembler de valider le document DDX en attribuant la valeur true à la propriété `AssemblerOptionSpec` de `validateOnly` membre de données.
   * Définissez la quantité d’informations que le service Assembler écrit dans le fichier journal en attribuant une valeur de chaîne à la variable `AssemblerOptionSpec` de `logLevel` membre de données. lors de la validation d’un document DDX, vous souhaitez obtenir plus d’informations écrites dans le fichier journal, ce qui facilite le processus de validation. Par conséquent, vous pouvez spécifier la valeur `FINE` ou `FINER`. Pour plus d’informations sur les options d’exécution que vous pouvez définir, voir `AssemblerOptionSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Effectuez la validation.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document DDX.
   * La valeur `null` pour le `Map` qui stocke généralement des documents PDF.
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution.

   Le `invokeDDX` renvoie une `AssemblerResult` contenant des informations spécifiant si le document DDX est valide.

1. Enregistrez les résultats de la validation dans un fichier journal.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier journal et le mode d’ouverture du fichier. Assurez-vous que l’extension de nom de fichier est .xml.
   * Créez un `BLOB` qui stocke les informations du journal en obtenant la valeur de la variable `AssemblerResult` de `jobLog` membre de données.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

   >[!NOTE]
   >
   >Si le document DDX n’est pas valide, une `OperationException` est généré. Dans l’instruction catch, vous pouvez obtenir la valeur de la variable `OperationException` de `jobLog` membre.

**Voir également**

[Validation de documents DDX](#validating-ddx-documents)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
