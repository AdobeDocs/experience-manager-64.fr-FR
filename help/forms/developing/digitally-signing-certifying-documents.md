---
title: Signature numérique et certification de documents
seo-title: Digitally Signing and Certifying Documents
description: Utilisez le service Signature pour ajouter et supprimer des champs de signature numérique à un document de PDF, récupérer les noms des champs de signature situés dans un document de PDF, modifier les champs de signature, signer numériquement des documents de PDF, certifier des documents de PDF, valider les signatures numériques situées dans un document de PDF, valider toutes les signatures numériques situées dans un document de PDF et supprimer une signature numérique d’un champ de signature.
seo-description: Use the Signature service to add and delete digital signature fields to a PDF document, retrieve the names of signature fields located in a PDF document, modify signature fields, digitally sign PDF documents, certify PDF documents, validate digital signatures located in a PDF document, validate all digital signatures located in a PDF document, and remove a digital signature from a signature field.
uuid: 6331de8a-2a9c-45bf-89d2-29f1ad5cc856
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 42de04bf-25e4-4478-a411-38671ed871ae
role: Developer
exl-id: b8488a39-44dd-4e6c-b3f0-857d67c79385
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '17032'
ht-degree: 8%

---

# Signature numérique et certification de documents {#digitally-signing-and-certifying-documents}

**À propos du service Signature**

Le service Signature permet à votre entreprise de protéger la sécurité et la confidentialité des documents Adobe PDF qu’elle distribue et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seuls les destinataires prévus peuvent modifier les documents. Les fonctions de sécurité étant appliquées au document lui-même, celui-ci reste sécurisé et contrôlé pendant tout son cycle de vie. Un document reste sécurisé au-delà du pare-feu, lorsqu’il est téléchargé hors ligne et lorsqu’il est renvoyé à votre entreprise.

>[!NOTE]
>
>Vous pouvez créer un gestionnaire de signatures personnalisé pour le service Signature qui est appelé lorsque certaines opérations sont invoquées, comme la signature d’un document de PDF.

**Noms des champs de signature**

Certaines opérations du service Signature requièrent la spécification du nom du champ de signature sur lequel une opération est effectuée. Par exemple, lors de la signature d’un document de PDF, vous spécifiez le nom du champ de signature à signer. Supposons que le nom complet d’un champ de signature soit `form1[0].Form1[0].SignatureField1[0]`. Vous pouvez indiquer `SignatureField1[0]` au lieu de `form1[0].Form1[0].SignatureField1[0]`.

Il arrive qu’un conflit entraîne le service Signature à signer (ou à effectuer une autre opération nécessitant le nom du champ de signature) le mauvais champ. Ce conflit est le résultat du nom `SignatureField1[0]` apparaissant à plusieurs endroits dans le même document de PDF. Prenons l’exemple d’un document PDF qui contient deux champs de signature nommés `form1[0].Form1[0].SignatureField1[0]` et `form1[0].Form1[0].SubForm1[0].SignatureField1[0]` et que vous spécifiez `SignatureField1[0]`. Dans ce cas, le service Signature signe le premier champ de signature qu’il détecte lors de l’itération sur tous les champs de signature du document.

Si plusieurs champs de signature sont situés dans un document de PDF, il est recommandé de spécifier le nom complet des champs de signature. Autrement dit, spécifiez `form1[0].Form1[0].SignatureField1[0]`au lieu de `SignatureField1[0]`.

Vous pouvez accomplir ces tâches à l’aide du service Signature :

* Ajoutez et supprimez des champs de signature numérique à un document de PDF. (Voir [Ajout de champs de signature](digitally-signing-certifying-documents.md#adding-signature-fields).)
* Récupérez les noms des champs de signature situés dans un document de PDF. (Voir [Récupération des noms des champs de signature](digitally-signing-certifying-documents.md#retrieving-signature-field-names).)
* Modifier les champs de signature. (Voir [Modification des champs de signature](digitally-signing-certifying-documents.md#modifying-signature-fields).)
* Signature numérique de documents PDF. (Voir [Signature numérique de documents PDF](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)
* Certifier les documents du PDF. (Voir [Certification de documents PDF](digitally-signing-certifying-documents.md#certifying-pdf-documents).)
* Validation des signatures numériques situées dans un document PDF. (Voir [Vérification des signatures numériques](#unresolvedlink-lc-si).)
* Validez toutes les signatures numériques présentes dans un document PDF. (Voir [Vérification de plusieurs signatures numériques](#unresolvedlink-lc-si).)
* Supprimez une signature numérique d’un champ de signature. (Voir [Suppression de signatures numériques](digitally-signing-certifying-documents.md#removing-digital-signatures).)

>[!NOTE]
>
>Pour plus d’informations sur le service Signature, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Ajout de champs de signature {#adding-signature-fields}

Les signatures numériques apparaissent dans les champs de signature qui sont des champs de formulaire contenant une représentation graphique de la signature. Les champs de signature peuvent être visibles ou invisibles. Les signataires peuvent utiliser un champ de signature préexistant ou un champ de signature peut être ajouté par programmation. Dans les deux cas, le champ de signature doit exister avant la signature du document PDF.

Vous pouvez programmer l’ajout d’un champ de signature à l’aide de l’API Java du service Signature ou de l’API du service Web de signature. Vous pouvez ajouter plusieurs champs de signature à un document de PDF ; cependant, chaque nom de champ de signature doit être unique.

>[!NOTE]
>
>Certains types de documents de PDF ne vous permettent pas d’ajouter par programmation un champ de signature. Pour plus d’informations sur le service Signature et l’ajout de champs de signature, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour ajouter un champ de signature à un document de PDF, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Signature.
1. Obtenez un document de PDF auquel un champ de signature est ajouté.
1. Ajoutez un champ de signature.
1. Enregistrez le document du PDF en tant que fichier de PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

**Création d’un client Signature**

Avant d’effectuer par programmation une opération du service Signature, vous devez créer un client du service Signature.

**Obtenir un document PDF auquel un champ de signature est ajouté**

Vous devez obtenir un document de PDF auquel un champ de signature est ajouté.

**Ajouter un champ de signature**

Pour ajouter un champ de signature à un document de PDF, vous spécifiez des valeurs de coordonnées qui identifient l’emplacement du champ de signature. (Si vous ajoutez un champ de signature invisible, ces valeurs ne sont pas requises.) En outre, vous pouvez spécifier les champs du document du PDF qui sont verrouillés après l’apposition d’une signature sur le champ de signature.

**Enregistrer le document du PDF en tant que fichier de PDF**

Une fois que le service Signature a ajouté un champ de signature au document du PDF, vous pouvez enregistrer le document en tant que fichier du PDF afin que les utilisateurs puissent l’ouvrir dans Acrobat ou Adobe Reader.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signature numérique de documents PDF](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Ajout de champs de signature à l’aide de l’API Java {#add-signature-fields-using-the-java-api}

Ajoutez un champ de signature à l’aide de l’API Signature (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar, dans le chemin d’accès aux classes de votre projet Java.

1. Création d’un client Signature

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtenir un document PDF auquel un champ de signature est ajouté

   * Créez un `java.io.FileInputStream` qui représente le document du PDF auquel un champ de signature est ajouté en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Ajouter un champ de signature

   * Créez un `PositionRectangle` qui spécifie l’emplacement du champ de signature à l’aide de son constructeur. Dans le constructeur, spécifiez des valeurs de coordonnée.
   * Si vous le souhaitez, créez une `FieldMDPOptions` qui spécifie les champs verrouillés lorsqu’une signature numérique est appliquée au champ de signature.
   * Ajoutez un champ de signature à un document de PDF en appelant la méthode `SignatureServiceClient` de `addSignatureField` et transmission des valeurs suivantes :

      * A `com.adobe.idp`. `Document` qui représente le document du PDF auquel un champ de signature est ajouté.
      * Une valeur string qui spécifie le nom du champ de signature.
      * A `java.lang.Integer` qui représente le numéro de page auquel un champ de signature est ajouté.
      * A `PositionRectangle` qui spécifie l’emplacement du champ de signature.
      * A `FieldMDPOptions` qui spécifie les champs du document du PDF verrouillés après l’application d’une signature numérique au champ de signature. Cette valeur de paramètre est facultative et vous pouvez la transmettre. `null`.
   * A `PDFSeedValueOptions` qui spécifie différentes valeurs d’exécution. Cette valeur de paramètre est facultative et vous pouvez la transmettre. `null`.

      Le `addSignatureField` renvoie une `com.adobe.idp`. `Document` qui représente un document PDF contenant un champ de signature.
   >[!NOTE]
   >
   >Vous pouvez appeler le `SignatureServiceClient` de `addInvisibleSignatureField` pour ajouter un champ de signature invisible.

1. Enregistrer le document du PDF en tant que fichier de PDF

   * Créez un objet `java.io.File` et assurez-vous que l’extension du fichier est .pdf.
   * Appeler la variable `com.adobe.idp`. `Document` de `copyToFile` pour copier le contenu de la méthode `Document` vers le fichier . Veillez à utiliser la variable `com.adobe.idp`. `Document` qui a été renvoyé par l’objet `addSignatureField` .

**Voir également**

[Démarrages rapides de l’API du service Signature](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

### Ajout de champs de signature à l’aide de l’API de service Web {#add-signature-fields-using-the-web-service-api}

Pour ajouter un champ de signature à l’aide de l’API Signature (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Signature

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Obtenir un document PDF auquel un champ de signature est ajouté

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF qui contiendra un champ de signature.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Ajouter un champ de signature

   Ajoutez un champ de signature au document du PDF en appelant la méthode `SignatureServiceClient` de `addSignatureField` et transmission des valeurs suivantes :

   * A `BLOB` qui représente le document du PDF auquel un champ de signature est ajouté.
   * Une valeur string qui spécifie le nom du champ de signature.
   * Une valeur entière qui représente le numéro de page auquel un champ de signature est ajouté.
   * A `PositionRect` qui spécifie l’emplacement du champ de signature.
   * A `FieldMDPOptions` qui spécifie les champs du document du PDF verrouillés après l’application d’une signature numérique au champ de signature. Cette valeur de paramètre est facultative et vous pouvez la transmettre. `null`.
   * A `PDFSeedValueOptions` qui spécifie différentes valeurs d’exécution. Cette valeur de paramètre est facultative et vous pouvez la transmettre. `null`.

   Le `addSignatureField` renvoie une `BLOB` qui représente un document PDF contenant un champ de signature.

1. Enregistrer le document du PDF en tant que fichier de PDF

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF qui contiendra le champ de signature et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui a été renvoyé par l’objet `addSignatureField` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `binaryData` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Récupération des noms des champs de signature {#retrieving-signature-field-names}

Vous pouvez récupérer les noms de tous les champs de signature d’un document PDF que vous souhaitez signer ou certifier. Si vous n’êtes pas certain de connaître les noms de champ de signature d’un document PDF ou si vous souhaitez vérifier leurs noms, vous pouvez programmer leur récupération. Le service Signature renvoie le nom qualifié complet du champ de signature, tel que `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

>[!NOTE]
>
>Pour plus d’informations sur le service Signature, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Résumé des étapes {#summary_of_steps-1}

Pour récupérer les noms des champs de signature, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Signature.
1. Obtenez le document du PDF qui contient les champs de signature.
1. Récupérez les noms des champs de signature.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Signature**

Avant d’effectuer par programmation une opération du service Signature, vous devez créer un client du service Signature.

**Obtention du document du PDF contenant les champs de signature**

Récupérez un document PDF contenant des champs de signature.

**Récupération des noms des champs de signature**

Vous pouvez récupérer les noms des champs de signature après avoir récupéré un document de PDF contenant un ou plusieurs champs de signature.

**Voir également**

[Récupération des noms de champ de signature à l’aide de l’API Java](digitally-signing-certifying-documents.md#retrieve-signature-field-names-using-the-java-api)

[Récupération du champ de signature à l’aide de l’API de service Web](digitally-signing-certifying-documents.md#retrieve-signature-field-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Ajout de champs de signature](digitally-signing-certifying-documents.md#adding-signature-fields)

### Récupération des noms de champ de signature à l’aide de l’API Java {#retrieve-signature-field-names-using-the-java-api}

Récupérez les noms des champs de signature à l’aide de l’API Signature (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar, dans le chemin d’accès aux classes de votre projet Java.

1. Création d’un client Signature

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtention du document du PDF contenant les champs de signature

   * Créez un `java.io.FileInputStream` qui représente le document du PDF qui contient des champs de signature en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Récupération des noms des champs de signature

   * Récupérez les noms des champs de signature en appelant la méthode `SignatureServiceClient` de `getSignatureFieldList` et transmission de la méthode `com.adobe.idp.Document` contenant le document du PDF contenant les champs de signature. Cette méthode renvoie une `java.util.List` dans lequel chaque élément contient un objet `PDFSignatureField` . Grâce à cet objet, vous pouvez obtenir des informations supplémentaires sur un champ de signature, telles que sa visibilité.
   * Effectuez une itération à l’aide du `java.util.List` pour déterminer s’il existe des noms de champ de signature. Pour chaque champ de signature du document du PDF, vous pouvez obtenir un `PDFSignatureField` . Pour obtenir le nom du champ de signature, appelez la méthode `PDFSignatureField` de `getName` . Cette méthode renvoie une valeur string qui spécifie le nom du champ de signature.

**Voir également**

[Récupération des noms des champs de signature](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[Démarrage rapide (mode SOAP) : Récupération des noms de champ de signature à l’aide de l’API Java](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Récupération du champ de signature à l’aide de l’API de service Web {#retrieve-signature-field-using-the-web-service-api}

Récupérez les noms des champs de signature à l’aide de l’API Signature (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Signature

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Obtention du document du PDF contenant les champs de signature

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF contenant les champs de signature.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` champ le contenu du tableau d’octets.

1. Récupération des noms des champs de signature

   * Récupérer les noms des champs de signature en appelant `SignatureServiceClient` de `getSignatureFieldList` et transmission de la méthode `BLOB` contenant le document du PDF contenant les champs de signature. Cette méthode renvoie une `MyArrayOfPDFSignatureField` objet de collection où chaque élément contient un objet `PDFSignatureField` .
   * Effectuez une itération à l’aide du `MyArrayOfPDFSignatureField` pour déterminer s’il existe des noms de champ de signature. Pour chaque champ de signature du document du PDF, vous pouvez obtenir un `PDFSignatureField` . Pour obtenir le nom du champ de signature, appelez la méthode `PDFSignatureField` de `getName` . Cette méthode renvoie une valeur string qui spécifie le nom du champ de signature.

**Voir également**

[Récupération des noms des champs de signature](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Modification des champs de signature {#modifying-signature-fields}

Vous pouvez modifier les champs de signature d’un document de PDF à l’aide de l’API Java et de l’API de service Web. La modification d’un champ de signature implique de manipuler ses valeurs de dictionnaire de verrouillage des champs de signature ou ses valeurs du dictionnaire de valeur de départ.

A *dictionnaire de verrouillage de champ* spécifie une liste de champs verrouillés lorsque le champ de signature est signé. Un champ verrouillé empêche les utilisateurs d’apporter des modifications au champ. A *dictionnaire de valeur de départ* contient des informations contraignantes utilisées au moment de l’application de la signature. Par exemple, vous pouvez modifier les autorisations qui contrôlent les actions pouvant se produire sans invalider la signature.

En modifiant un champ de signature existant, vous pouvez apporter des modifications au document du PDF afin de tenir compte de l’évolution des besoins de l’entreprise. Par exemple, une nouvelle exigence professionnelle peut nécessiter le verrouillage de tous les champs du document une fois le document signé.

Cette section explique comment modifier un champ de signature en modifiant les valeurs du dictionnaire de verrouillage de champ et du dictionnaire de valeur de départ. Les modifications apportées au dictionnaire de verrouillage des champs de signature entraînent le verrouillage de tous les champs du document du PDF lors de la signature d’un champ de signature. Les modifications apportées au dictionnaire des valeurs de départ interdisent des types spécifiques de modifications apportées au document.

>[!NOTE]
>
>Pour plus d’informations sur le service Signature et la modification des champs de signature, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-2}

Pour modifier les champs de signature d’un document de PDF, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Signature.
1. Obtenez le document du PDF qui contient le champ de signature à modifier.
1. Définissez les valeurs du dictionnaire.
1. Modifiez le champ de signature.
1. Enregistrez le document du PDF en tant que fichier de PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java LiveCycle](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Signature**

Avant d’effectuer par programmation une opération du service Signature, vous devez créer un client du service Signature.

**Obtention du document du PDF contenant le champ de signature à modifier**

Récupérez un document PDF contenant le champ de signature à modifier.

**Définition des valeurs du dictionnaire**

Pour modifier un champ de signature, affectez des valeurs à son dictionnaire de verrouillage de champ ou à son dictionnaire de valeur de départ. La spécification des valeurs du dictionnaire de verrouillage des champs de signature implique la spécification des champs de document du PDF verrouillés lorsque le champ de signature est signé. (Cette section explique comment verrouiller tous les champs.)

Les valeurs du dictionnaire de valeurs de départ suivantes peuvent être définies :

* **Vérification des révisions**: Indique si la vérification de révocation est effectuée lorsqu’une signature est appliquée au champ de signature.
* **Options de certificat**: Attribue des valeurs au dictionnaire de valeurs de départ de certificat. Avant de spécifier des options de certificat, il est recommandé de vous familiariser avec un dictionnaire de valeur de départ de certificat. (Voir [Référence du PDF](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Options de prétraitement**: Attribue des algorithmes digest utilisés pour la signature. Les valeurs valides sont SHA1, SHA256, SHA384, SHA512 et RIPEMD160.
* **Filtrer**: Indique le filtre utilisé avec le champ de signature. Par exemple, vous pouvez utiliser le filtre Adobe.PPKLite . (Voir [Référence du PDF](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Options d’indicateur**: Indique les valeurs d’indicateur associées à ce champ de signature. Une valeur de 1 signifie qu’un signataire ne doit utiliser que les valeurs spécifiées pour l’entrée. Une valeur de 0 signifie que d’autres valeurs sont autorisées. Voici les positions Bit :

   * **1 (Filtre) :** Le gestionnaire de signatures à utiliser pour signer le champ de signature
   * **2 (SubFilter) :** Tableau de noms indiquant des encodages acceptables à utiliser lors de la signature
   * **3 (V)**: Numéro de version minimum requis du gestionnaire de signatures à utiliser pour signer le champ de signature.
   * **4 (Raisons) :** Tableau de chaînes spécifiant les motifs possibles de la signature d’un document
   * **5 (PDFLegalWarnings) :** Tableau de chaînes spécifiant les attestations juridiques possibles

* **attestations juridiques**: Lorsqu’un document est certifié, il est automatiquement analysé à la recherche de types de contenu spécifiques qui peuvent rendre le contenu visible d’un document ambigu ou trompeur. Par exemple, une annotation peut masquer du texte important pour comprendre ce qui est certifié. Le processus d’analyse génère des avertissements indiquant la présence de ce type de contenu. Il fournit également une explication supplémentaire du contenu susceptible d’avoir généré des avertissements.
* **Autorisations**: Spécifie les autorisations pouvant être utilisées sur un document de PDF sans invalider la signature.
* **Raisons**: Indique les raisons pour lesquelles ce document doit être signé.
* **Horodatage**: Spécifie les options d’horodatage. Vous pouvez, par exemple, définir l’URL du serveur d’horodatage utilisé.
* **Version**: Indique le numéro de version minimum du gestionnaire de signatures à utiliser pour signer le champ de signature.

**Modification du champ de signature**

Après avoir créé un client de service Signature, récupérez le document du PDF qui contient le champ de signature à modifier et définissez les valeurs du dictionnaire, vous pouvez demander au service Signature de modifier le champ de signature. Le service Signature renvoie ensuite un document de PDF contenant le champ de signature modifié. Le document du PDF d’origine n’est pas affecté.

**Enregistrer le document du PDF en tant que fichier de PDF**

Enregistrez le document du PDF qui contient le champ de signature modifié comme fichier de PDF afin que les utilisateurs puissent l’ouvrir dans Acrobat ou Adobe Reader.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API du service Signature](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

[Signature numérique de documents PDF](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Modification des champs de signature à l’aide de l’API Java {#modify-signature-fields-using-the-java-api}

Modifiez un champ de signature à l’aide de l’API Signature (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un client Signature

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtention du document du PDF contenant le champ de signature à modifier

   * Créez un `java.io.FileInputStream` qui représente le document du PDF contenant le champ de signature à modifier à l’aide de son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définition des valeurs du dictionnaire

   * Créez un objet `PDFSignatureFieldProperties` en utilisant son constructeur. A `PDFSignatureFieldProperties` stocke les informations du dictionnaire de verrouillage des champs de signature et du dictionnaire de valeurs de départ.
   * Créez un objet `PDFSeedValueOptionSpec` en utilisant son constructeur. Cet objet vous permet de définir les valeurs du dictionnaire de valeurs de départ.
   * Interdire les modifications apportées au document du PDF en appelant la méthode `PDFSeedValueOptionSpec` de `setMdpValue` et transmission de la méthode `MDPPermissions.NoChanges` valeur d’énumération.
   * Créez un objet `FieldMDPOptionSpec` en utilisant son constructeur. Cet objet vous permet de définir les valeurs du dictionnaire de verrouillage des champs de signature.
   * Verrouillez tous les champs du document du PDF en appelant la méthode `FieldMDPOptionSpec` de `setMdpValue` et transmission de la méthode `FieldMDPAction.ALL` valeur d’énumération.
   * Définissez les informations du dictionnaire de valeur de départ en appelant la variable `PDFSignatureFieldProperties` de `setSeedValue` et transmission de la méthode `PDFSeedValueOptionSpec` .
   * Définissez les informations du dictionnaire de verrouillage des champs de signature en appelant la fonction `PDFSignatureFieldProperties`de `setFieldMDP` et transmission de la méthode `FieldMDPOptionSpec` .

   >[!NOTE]
   >
   >Pour afficher toutes les valeurs du dictionnaire de valeurs de départ que vous pouvez définir, reportez-vous à la section `PDFSeedValueOptionSpec` référence de classe. (Voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

1. Modification du champ de signature

   Modifiez le champ de signature en appelant la méthode `SignatureServiceClient` de `modifySignatureField` et transmission des valeurs suivantes :

   * Le `com.adobe.idp.Document` qui stocke le document du PDF contenant le champ de signature à modifier.
   * Une valeur string qui spécifie le nom du champ de signature
   * Le `PDFSignatureFieldProperties` qui stocke les informations du dictionnaire de verrouillage de champ de signature et du dictionnaire de valeur de départ

   Le `modifySignatureField` renvoie une `com.adobe.idp.Document` qui stocke un document PDF contenant le champ de signature modifié.

1. Enregistrer le document du PDF en tant que fichier de PDF

   * Créez un `java.io.File` et assurez-vous que l’extension de nom de fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` vers le fichier . Veillez à utiliser la variable `com.adobe.idp.Document` qui `modifySignatureField` est renvoyée.

### Modification des champs de signature à l’aide de l’API du service Web {#modify-signature-fields-using-the-web-service-api}

Modifiez un champ de signature à l’aide de l’API Signature (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Signature

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Obtention du document du PDF contenant le champ de signature à modifier

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF contenant le champ de signature à modifier.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` propriété le contenu du tableau d’octets.

1. Définition des valeurs du dictionnaire

   * Créez un objet `PDFSignatureFieldProperties` en utilisant son constructeur. Cet objet stocke les informations du dictionnaire de verrouillage de champ de signature et du dictionnaire de valeur de départ.
   * Créez un objet `PDFSeedValueOptionSpec` en utilisant son constructeur. Cet objet vous permet de définir les valeurs du dictionnaire de valeurs de départ.
   * Interdire les modifications apportées au document du PDF en attribuant la variable `MDPPermissions.NoChanges` de la valeur de l’énumération `PDFSeedValueOptionSpec` de `mdpValue` membre de données.
   * Créez un objet `FieldMDPOptionSpec` en utilisant son constructeur. Cet objet vous permet de définir les valeurs du dictionnaire de verrouillage des champs de signature.
   * Verrouillez tous les champs du document du PDF en attribuant la variable `FieldMDPAction.ALL` de la valeur de l’énumération `FieldMDPOptionSpec` de `mdpValue` membre de données.
   * Définissez les informations du dictionnaire de valeur de départ en attribuant la variable `PDFSeedValueOptionSpec` vers l’objet `PDFSignatureFieldProperties` de `seedValue` membre de données.
   * Définir les informations du dictionnaire de verrouillage des champs de signature en attribuant la variable `FieldMDPOptionSpec` vers l’objet `PDFSignatureFieldProperties` de `fieldMDP` membre de données.

   >[!NOTE]
   >
   >Pour afficher toutes les valeurs du dictionnaire de valeurs de départ que vous pouvez définir, reportez-vous à la section `PDFSeedValueOptionSpec` référence de classe. (Voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

1. Modification du champ de signature

   Modifiez le champ de signature en appelant la méthode `SignatureServiceClient` de `modifySignatureField` et transmission des valeurs suivantes :

   * Le `BLOB` qui stocke le document du PDF contenant le champ de signature à modifier.
   * Une valeur string qui spécifie le nom du champ de signature
   * Le `PDFSignatureFieldProperties` qui stocke les informations du dictionnaire de verrouillage de champ de signature et du dictionnaire de valeur de départ

   Le `modifySignatureField` renvoie une `BLOB` qui stocke un document PDF contenant le champ de signature modifié.

1. Enregistrer le document du PDF en tant que fichier de PDF

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF qui contiendra le champ de signature et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui `addSignatureField` renvoie . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Signature numérique de documents PDF {#digitally-signing-pdf-documents}

Les signatures numériques peuvent être appliquées aux documents PDF pour fournir un niveau de sécurité. Les signatures numériques, tout comme les signatures manuscrites, permettent aux signataires de s’identifier et d’effectuer des instructions sur le document. La technologie utilisée pour signer numériquement des documents permet de s’assurer que le signataire et les destinataires se sont accordés sur ce qui a été signé et croient en la non-altération du document signé.

Les documents PDF sont signés au moyen de la technologie de clé publique. Le signataire a deux clés : une clé publique et une clé privée. La clé privée est stockée dans les informations d’identification d’un utilisateur qui doivent être disponibles au moment de la signature. La clé publique est stockée dans le certificat de l’utilisateur et doit être accessible aux destinataires pour valider la signature. Les informations relatives aux certificats révoqués se trouvent dans les listes de révocation des certificats et les réponses OCSP (Online Certificate Status Protocol) distribuées par les autorités de certification (CA). L’heure de la signature peut être obtenue d’une source approuvée appelée Autorité de d’horodatage.

>[!NOTE]
>
>Avant de pouvoir signer numériquement un document de PDF, vous devez vous assurer d’ajouter le certificat à AEM Forms. Un certificat est ajouté à l’aide d’Administration Console ou par programmation à l’aide de l’API Trust Manager. (Voir [Importation des informations d’identification à l’aide de l’API Trust Manager](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

Vous pouvez signer numériquement des documents PDF par programmation. Lors de la signature numérique d’un document de PDF, vous devez référencer des informations d’identification de sécurité qui existent dans AEM Forms. Les informations d’identification sont la clé privée utilisée pour la signature.

Le service Signature effectue les étapes suivantes lorsqu’un document de PDF est signé :

1. Le service Signature récupère les informations d’identification de Truststore en transmettant l’alias spécifié dans la requête.
1. Truststore recherche les informations d’identification spécifiées.
1. Les informations d’identification sont renvoyées au service Signature et sont utilisées pour signer le document. Les informations d’identification sont également mises en cache par rapport à l’alias pour les futures demandes.

Pour plus d’informations sur la gestion des informations d’identification de sécurité, consultez le guide d’installation et de déploiement d’AEM Forms* correspondant à votre serveur d’applications.

>[!NOTE]
>
>Il existe des différences entre la signature et la certification de documents. (Voir [Certification de documents PDF](digitally-signing-certifying-documents.md#certifying-pdf-documents).)

>[!NOTE]
>
>Tous les documents de PDF ne prennent pas en charge la signature. Pour plus d’informations sur le service Signature et la signature numérique de documents, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Le service Signature ne prend pas en charge les fichiers XDP contenant des données de PDF incorporées en tant qu’entrée d’une opération, telle que la certification d’un document. Cette action entraîne le lancement par le service Signature d’une `PDFOperationException`. Pour résoudre ce problème, convertissez le fichier XDP en fichier de PDF à l’aide du service PDF Utilities, puis transmettez le fichier de PDF converti à une opération de service Signature. (Voir [Utilisation des utilitaires PDF](/help/forms/developing/pdf-utilities.md#working-with-pdf-utilities).)

**Informations d’identification nShield HSM**

Lors de l’utilisation d’informations d’identification HSM InShield pour signer ou certifier un document de PDF, les nouvelles informations d’identification ne peuvent pas être utilisées tant que le serveur d’applications J2EE sur lequel AEM Forms est déployé n’a pas été redémarré. Cependant, vous pouvez définir une valeur de configuration, ce qui entraîne le fonctionnement de l’opération de signature ou de certification sans redémarrer le serveur d’applications J2EE.

Vous pouvez ajouter la valeur de configuration suivante dans le fichier cknfastrc, qui se trouve sous /opt/nfast/cknfastrc (ou c:\nfast\cknfastrc) :

```as3
 CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Après avoir ajouté cette valeur de configuration au fichier .cknfastrc, les nouvelles informations d’identification peuvent être utilisées sans redémarrer le serveur d’applications J2EE.

**Signature non approuvée**

Lors de la certification et de la signature du même document de PDF, si la signature de certification n’est pas approuvée, un triangle jaune apparaît sur la première signature lors de l’ouverture du document de PDF dans Acrobat ou Adobe Reader. Pour éviter cette situation, la signature de certification doit être fiable.

**Signature de documents qui sont des formulaires XFA**

Si vous tentez de signer un formulaire basé sur XFA à l’aide de l’API du service Signature, les données peuvent ne pas figurer dans la variable `View` `Signed` `Version` situé dans Acrobat. Prenons l’exemple du workflow suivant :

* A l’aide d’un fichier XDP créé à l’aide de Designer, vous fusionnez une conception de formulaire contenant un champ de signature et des données XML contenant des données de formulaire. Vous utilisez le service Forms pour générer un document de PDF interactif.
* Vous signez le document du PDF à l’aide de l’API du service Signature.

### Résumé des étapes {#summary_of_steps-3}

Pour signer numériquement un document PDF, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client de service Signature.
1. Obtenez le document du PDF à signer.
1. Signez le document du PDF.
1. Enregistrez le document signé du PDF en tant que fichier de PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

**Création d’un client Signatures**

Avant d’effectuer par programmation une opération du service Signature, vous devez créer un client du service Signature.

**Obtention de la signature du document du PDF**

Pour signer un document de PDF, vous devez obtenir un document de PDF contenant un champ de signature. Si un document de PDF ne contient pas de champ de signature, il ne peut pas être signé. Vous pouvez ajouter un champ de signature à l’aide de Designer ou par programmation.

**Signature du document du PDF**

Lors de la signature d’un document PDF, vous pouvez définir les options d’exécution utilisées par le service Signature. Vous pouvez configurer les options suivantes :

* Options d’aspect
* Vérification de révocation
* Valeurs d’horodatage

Pour définir les options d’aspect, utilisez une `PDFSignatureAppearanceOptionSpec` . Par exemple, vous pouvez afficher la date dans une signature en appelant la fonction `PDFSignatureAppearanceOptionSpec` de `setShowDate` méthode et transmission `true`.

Vous pouvez également indiquer s’il faut effectuer ou non une vérification de révocation qui détermine si le certificat utilisé pour signer numériquement un document du PDF a été révoqué. Pour effectuer une vérification de révocation, vous pouvez spécifier l’une des valeurs suivantes :

* **NoCheck**: N’effectuez pas de vérification de révocation.
* **BestEffort**: Essayez toujours de vérifier la révocation de tous les certificats de la chaîne. Si un problème se produit lors de la vérification, la révocation est supposée être valide. En cas d’échec, supposons que le certificat n’est pas révoqué.
* **CheckIfAvailable :** Vérifiez la révocation de tous les certificats de la chaîne si des informations de révocation sont disponibles. En cas de problème lors de la vérification, la révocation est considérée comme non valide. En cas d’échec, supposons que le certificat soit révoqué et non valide. (Il s’agit de la valeur par défaut.)
* **AlwaysCheck**: Vérifiez la révocation de tous les certificats de la chaîne. Si les informations de révocation ne figurent dans aucun certificat, la révocation est considérée comme non valide.

Pour effectuer une vérification de révocation sur un certificat, vous pouvez spécifier une URL vers un serveur de liste de révocation des certificats (CRL) à l’aide d’une `CRLOptionSpec` . Cependant, si vous souhaitez effectuer une vérification de révocation et que vous ne spécifiez pas d’URL vers un serveur CRL, le service Signature obtient l’URL à partir du certificat.

Au lieu d’utiliser un serveur CRL, vous pouvez utiliser un serveur OCSP (Online Certificate Status Protocol) lors de la vérification de révocation. En règle générale, lorsque vous utilisez un serveur OCSP plutôt qu’un serveur CRL, la vérification de révocation est effectuée plus rapidement. (Voir &quot;Protocole d’état du certificat en ligne&quot; à l’adresse [https://tools.ietf.org/html/rfc2560](https://tools.ietf.org/html/rfc2560).)

Vous pouvez définir l’ordre de la CRL et du serveur OCSP que le service Signature utilise à l’aide des applications et services Adobe. Par exemple, si le serveur OCSP est d’abord défini dans Applications et services Adobe, alors le serveur OCSP est coché, suivi du serveur CRL. (Voir &quot;Gestion des certificats et des informations d’identification à l’aide de Trust Store&quot; dans l’aide d’AAC).

Si vous indiquez de ne pas effectuer de vérification de révocation, le service Signature ne vérifie pas si le certificat utilisé pour signer ou certifier un document a été révoqué. En d’autres termes, les informations de CRL et du serveur OCSP sont ignorées.

>[!NOTE]
>
>Bien qu’une liste de révocation des certificats ou un serveur OCSP puisse être spécifié dans le certificat, vous pouvez remplacer l’URL spécifiée dans le certificat à l’aide d’une `CRLOptionSpec` et un `OCSPOptionSpec` . Par exemple, pour remplacer le serveur CRL, vous pouvez appeler la variable `CRLOptionSpec` de `setLocalURI` .

L’horodatage fait référence au processus de suivi de l’heure de modification d’un document signé ou certifié. Une fois signé, le document ne doit pas être modifié, même par son propriétaire. L’horodatage permet d’assurer la validité d’un document signé ou certifié. Vous pouvez définir des options d’horodatage à l’aide d’une `TSPOptionSpec` . Par exemple, vous pouvez spécifier l’URL d’un serveur de fournisseur d’horodatage (TSP).

>[!NOTE]
>
>Dans les sections Java et service Web, la vérification de révocation est utilisée, ainsi que les démarrages rapides correspondants. Comme aucune information de CRL ou de serveur OCSP n’est spécifiée, les informations du serveur sont obtenues à partir du certificat utilisé pour signer numériquement le document du PDF.

Pour réussir la signature d’un document de PDF, vous pouvez spécifier le nom qualifié complet du champ de signature qui contiendra la signature numérique, tel que `form1[0].#subform[1].SignatureField3[3]`. Lors de l’utilisation d’un champ de formulaire XFA, le nom partiel du champ de signature peut également être utilisé : `SignatureField3[3]`.

Vous devez également référencer des informations d’identification de sécurité pour signer numériquement un document de PDF. Pour référencer des informations d’identification de sécurité, vous spécifiez un alias. L’alias est une référence à des informations d’identification réelles qui peuvent se trouver dans un fichier PKCS#12 (avec une extension .pfx) ou un module de sécurité matérielle (HSM). Pour plus d’informations sur les informations d’identification de sécurité, consultez le guide d’installation et de déploiement d’AEM Forms* correspondant à votre serveur d’applications.

**Enregistrement du document de PDF signé**

Une fois que le service Signature a signé numériquement le document du PDF, vous pouvez l’enregistrer en tant que fichier du PDF afin que les utilisateurs puissent l’ouvrir dans Acrobat ou Adobe Reader.

**Voir également**

[Signature numérique de documents PDF à l’aide de l’API Java](digitally-signing-certifying-documents.md#digitally-sign-pdf-documents-using-the-java-api)

[Signature numérique de documents PDF à l’aide de l’API du service Web](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Ajout de champs de signature](digitally-signing-certifying-documents.md#adding-signature-fields)

[Récupération des noms des champs de signature](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

### Signature numérique de documents PDF à l’aide de l’API Java {#digitally-sign-pdf-documents-using-the-java-api}

Signer numériquement un document de PDF à l’aide de l’API Signature (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar, dans le chemin d’accès aux classes de votre projet Java.

1. Création d’un client Signatures

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtention de la signature du document du PDF

   * Créez un `java.io.FileInputStream` qui représente le document du PDF à signer numériquement en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Signature du document du PDF

   Signez le document du PDF en appelant la méthode `SignatureServiceClient` de `sign` et transmission des valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document du PDF à signer.
   * Une valeur string qui représente le nom du champ de signature qui contiendra la signature numérique.
   * A `Credential` qui représente les informations d’identification utilisées pour signer numériquement le document du PDF. Créez un `Credential` en appelant le `Credential` statique de l’objet `getInstance` et transmettre une valeur string qui spécifie la valeur alias qui correspond aux informations d’identification de sécurité.
   * A `HashAlgorithm` qui spécifie un membre de données statique qui représente l’algorithme de hachage à utiliser pour condenser le document du PDF. Par exemple, vous pouvez spécifier `HashAlgorithm.SHA1` pour utiliser l’algorithme SHA1.
   * Une valeur string qui représente la raison pour laquelle le document du PDF a été signé numériquement.
   * Une valeur string qui représente les informations de contact du signataire.
   * A `PDFSignatureAppearanceOptions` qui contrôle l’aspect de la signature numérique. Vous pouvez, par exemple, utiliser cet objet pour ajouter un logo personnalisé à une signature numérique.
   * A `java.lang.Boolean` qui spécifie si la révocation doit être vérifiée sur le certificat du signataire.
   * Un `OCSPOptionSpec` qui stocke des préférences pour la prise en charge du protocole OCSP (Online Certificate Status Protocol). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `CRLPreferences` qui stocke les préférences de liste de révocation des certificats (CRL). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `TSPPreferences` qui stocke les préférences pour la prise en charge du fournisseur d’horodatage (TSP). Ce paramètre est facultatif et peut être `null`. Pour plus d’informations, voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Le `sign` renvoie une `com.adobe.idp.Document` qui représente le document du PDF signé.

1. Enregistrement du document de PDF signé

   * Créez un objet `java.io.File` et assurez-vous que l’extension du fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` méthode et transmission `java.io.File`pour copier le contenu de la fonction `Document` vers le fichier . Assurez-vous d’utiliser l’objet `com.adobe.idp.Document` qui a été retourné par la méthode `sign`.

**Voir également**

[Signature numérique de documents PDF](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Démarrage rapide (mode SOAP) : Signature numérique d’un document de PDF à l’aide de l’API Java](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Signature numérique de documents PDF à l’aide de l’API du service Web {#digitally-signing-pdf-documents-using-the-web-service-api}

Pour signer numériquement un document de PDF à l’aide de l’API Signature (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Signatures

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Obtention de la signature du document du PDF

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document PDF signé.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF à signer et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` propriété le contenu du tableau d’octets.

1. Signature du document du PDF

   Signez le document du PDF en appelant la méthode `SignatureServiceClient` de `sign` et transmission des valeurs suivantes :

   * A `BLOB` qui représente le document du PDF à signer.
   * Une valeur string qui représente le nom du champ de signature qui contiendra la signature numérique.
   * A `Credential` qui représente les informations d’identification utilisées pour signer numériquement le document du PDF. Créez un `Credential` en utilisant son constructeur et en spécifiant l’alias en attribuant une valeur à la variable `Credential` de `alias` .
   * A `HashAlgorithm` qui spécifie un membre de données statique qui représente l’algorithme de hachage à utiliser pour condenser le document du PDF. Par exemple, vous pouvez spécifier `HashAlgorithm.SHA1` pour utiliser l’algorithme SHA1.
   * Valeur boolean qui spécifie si l’algorithme de hachage est utilisé.
   * Une valeur string qui représente la raison pour laquelle le document du PDF a été signé numériquement.
   * Une valeur string qui représente l’emplacement du signataire.
   * Une valeur string qui représente les informations de contact du signataire.
   * A `PDFSignatureAppearanceOptions` qui contrôle l’aspect de la signature numérique. Vous pouvez, par exemple, utiliser cet objet pour ajouter un logo personnalisé à une signature numérique.
   * A `System.Boolean` qui spécifie si la révocation doit être vérifiée sur le certificat du signataire. Si cette vérification de révocation est effectuée, elle est incorporée dans la signature. La valeur par défaut est de `false`.
   * Un `OCSPOptionSpec` qui stocke des préférences pour la prise en charge du protocole OCSP (Online Certificate Status Protocol). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`. Pour plus d’informations sur cet objet, voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` qui stocke les préférences de liste de révocation des certificats (CRL). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `TSPPreferences` qui stocke les préférences pour la prise en charge du fournisseur d’horodatage (TSP). Ce paramètre est facultatif et peut être `null`.

   Le `sign` renvoie une `BLOB` qui représente le document du PDF signé.

1. Enregistrement du document de PDF signé

   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF signé et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui a été renvoyé par l’objet `sign` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Signature numérique de documents PDF](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Signature numérique d’un Forms interactif {#digitally-signing-interactive-forms}

Vous pouvez signer un formulaire interactif que le service Forms crée. Prenons l’exemple du workflow suivant :

* Vous fusionnez un formulaire de PDF basé sur XFA créé à l’aide de Designer et des données de formulaire situées dans un document XML à l’aide du service Forms. Le serveur Forms effectue le rendu d’un formulaire interactif.
* Vous pouvez signer le formulaire interactif à l’aide de l’API du service Signature.

Le résultat est un formulaire de PDF interactif signé numériquement. Lors de la signature d’un formulaire de PDF basé sur un formulaire XFA, veillez à enregistrer le fichier de PDF en tant que formulaire de PDF statique Adobe. Si vous tentez de signer un formulaire de PDF enregistré en tant que formulaire de PDF dynamique Adobe, une exception se produit. Puisque vous signez le formulaire renvoyé par le service Forms, assurez-vous que le formulaire contient un champ de signature.

>[!NOTE]
>
>Avant de pouvoir signer numériquement un formulaire interactif, vous devez vous assurer d’ajouter le certificat à AEM Forms. Un certificat est ajouté à l’aide d’Administration Console ou par programmation à l’aide de l’API Trust Manager. (Voir [Importation des informations d’identification à l’aide de l’API Trust Manager](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

Lors de l’utilisation de l’API Forms Service, définissez la variable `GenerateServerAppearance` option d’exécution sur `true`. Cette option d’exécution garantit que l’aspect du formulaire généré sur le serveur reste valide lorsqu’il est ouvert dans Acrobat ou Adobe Reader. Il est recommandé de définir cette option d’exécution lors de la génération d’un formulaire interactif à signer à l’aide de l’API Forms.

>[!NOTE]
>
>Avant de lire Signature numérique d’un Forms interactif, il est recommandé de bien connaître la procédure de signature des documents du PDF. (Voir [Signature numérique de documents PDF](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

### Résumé des étapes {#summary_of_steps-4}

Pour signer numériquement un formulaire interactif que le service Forms renvoie, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Forms et Signatures.
1. Obtenez le formulaire interactif à l’aide du service Forms.
1. Signez le formulaire interactif.
1. Enregistrez le document signé du PDF en tant que fichier de PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-forms-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Forms et Signatures**

Comme ce workflow appelle les services Forms et Signature, créez un client de service Forms et un client de service Signature.

**Obtention du formulaire interactif à l’aide du service Forms**

Vous pouvez utiliser le service Forms pour obtenir le formulaire de PDF interactif à signer. À partir d’AEM Forms, vous pouvez transmettre une `com.adobe.idp.Document` au service Forms contenant le formulaire à générer. Le nom de cette méthode est `renderPDFForm2`. Cette méthode renvoie une `com.adobe.idp.Document` qui contient le formulaire à signer. Vous pouvez transmettre ceci : `com.adobe.idp.Document` au service Signature.

De même, si vous utilisez des services Web, vous pouvez transmettre la variable `BLOB` instance que le service Forms renvoie au service Signature.

>[!NOTE]
>
>La section Démarrage rapide associé à la signature numérique d’un Forms interactif appelle la méthode `renderPDFForm2` .

**Signez le formulaire interactif**

Lors de la signature d’un document PDF, vous pouvez définir les options d’exécution utilisées par le service Signature. Vous pouvez configurer les options suivantes :

* Options d’aspect
* Vérification de révocation
* Valeurs d’horodatage

Pour définir les options d’aspect, utilisez une `PDFSignatureAppearanceOptionSpec` . Par exemple, vous pouvez afficher la date dans une signature en appelant la fonction `PDFSignatureAppearanceOptionSpec` de `setShowDate` méthode et transmission `true`.

**Enregistrement du document de PDF signé**

Une fois que le service Signature a signé numériquement le document du PDF, vous pouvez l’enregistrer en tant que fichier du PDF. Le fichier du PDF peut être ouvert dans Acrobat ou Adobe Reader.

**Voir également**

[Signer numériquement un formulaire interactif à l’aide de l’API Java](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-java-api)

[Signer numériquement un formulaire interactif à l’aide de l’API du service Web](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signature numérique de documents PDF](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Rendu des PDF forms interactifs](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms)

### Signer numériquement un formulaire interactif à l’aide de l’API Java {#digitally-sign-an-interactive-form-using-the-java-api}

Signer numériquement un formulaire interactif à l’aide de l’API Forms et Signature (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar et adobe-forms-client.jar, dans le chemin d’accès aux classes de votre projet Java.

1. Création d’un client Forms et Signatures

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 
   * Créez un objet `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtention du formulaire interactif à l’aide du service Forms

   * Créez un `java.io.FileInputStream` qui représente le document du PDF à transmettre au service Forms à l’aide de son constructeur. Transmettez une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 
   * Créez un `java.io.FileInputStream` qui représente le document XML contenant les données de formulaire à transmettre au service Forms à l’aide de son constructeur. Transmettez une valeur string qui spécifie l’emplacement du fichier XML.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 
   * Créez un `PDFFormRenderSpec` qui est utilisé pour définir les options d’exécution. Appeler la variable `PDFFormRenderSpec` de `setGenerateServerAppearance` méthode et transmission `true`.
   * Appeler la variable `FormsServiceClient` de `renderPDFForm2` et transmettez les valeurs suivantes :

      * A `com.adobe.idp.Document` qui contient le formulaire du PDF à afficher.
      * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire.
      * A `PDFFormRenderSpec` qui stocke les options d’exécution.
      * A `URLSpec` contenant des valeurs URI requises par le service Forms. Vous pouvez indiquer `null` pour cette valeur de paramètre.
      * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

      Le `renderPDFForm2` renvoie une `FormsResult` objet contenant un flux de données de formulaire

   * Récupérez le formulaire du PDF en appelant la fonction `FormsResult` de `getOutputContent` . Cette méthode renvoie une `com.adobe.idp.Document` qui représente le formulaire interactif.


1. Signez le formulaire interactif

   Signez le document du PDF en appelant la méthode `SignatureServiceClient` de `sign` et transmission des valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document du PDF à signer. Assurez-vous que cet objet correspond à la variable `com.adobe.idp.Document` obtenu à partir du service Forms.
   * Une valeur string qui représente le nom du champ de signature signé.
   * A `Credential` qui représente les informations d’identification utilisées pour signer numériquement le document du PDF. Créez un `Credential` en appelant le `Credential` statique de l’objet `getInstance` . Transmettez une valeur string qui spécifie la valeur alias qui correspond aux informations d’identification de sécurité.
   * A `HashAlgorithm` qui spécifie un membre de données statique qui représente l’algorithme de hachage à utiliser pour condenser le document du PDF. Par exemple, vous pouvez spécifier `HashAlgorithm.SHA1` pour utiliser l’algorithme SHA1.
   * Une valeur string qui représente la raison pour laquelle le document du PDF a été signé numériquement.
   * Une valeur string qui représente les informations de contact du signataire.
   * A `PDFSignatureAppearanceOptions` qui contrôle l’aspect de la signature numérique. Vous pouvez, par exemple, utiliser cet objet pour ajouter un logo personnalisé à une signature numérique.
   * A `java.lang.Boolean` qui spécifie si la révocation doit être vérifiée sur le certificat du signataire.
   * Un `OCSPPreferences` qui stocke des préférences pour la prise en charge du protocole OCSP (Online Certificate Status Protocol). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `CRLPreferences` qui stocke les préférences de liste de révocation des certificats (CRL). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `TSPPreferences` qui stocke les préférences pour la prise en charge du fournisseur d’horodatage (TSP). Ce paramètre est facultatif et peut être `null`.

   Le `sign` renvoie une `com.adobe.idp.Document` qui représente le document du PDF signé.

1. Enregistrement du document de PDF signé

   * Créez un `java.io.File` et assurez-vous que l’extension de nom de fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` méthode et transmission `java.io.File`pour copier le contenu de la fonction `Document` vers le fichier . Veillez à utiliser la variable `com.adobe.idp.Document` qui `sign` est renvoyée.

**Voir également**

[Signature numérique d’un Forms interactif](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[Démarrage rapide (mode SOAP) : Signature numérique d’un document de PDF à l’aide de l’API Java](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Signer numériquement un formulaire interactif à l’aide de l’API du service Web {#digitally-sign-an-interactive-form-using-the-web-service-api}

Signer numériquement un formulaire interactif à l’aide de l’API Forms et Signature (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Comme cette application cliente appelle deux services AEM Forms, créez deux références de service. Utilisez la définition WSDL suivante pour la référence de service associée au service Signature : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   Utilisez la définition WSDL suivante pour la référence de service associée au service Forms : `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Parce que la variable `BLOB` Le type de données est commun aux deux références de service. Il qualifie entièrement la variable `BLOB` type de données lors de son utilisation. Dans le démarrage rapide du service Web correspondant, tous les `BLOB` les instances sont entièrement qualifiées.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Forms et Signatures

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Répétez ces étapes pour le client de service Forms.

1. Obtention du formulaire interactif à l’aide du service Forms

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document PDF signé.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF à signer et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` propriété le contenu du tableau d’octets.
   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour stocker des données de formulaire.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier XML contenant les données de formulaire, ainsi que le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` propriété le contenu du tableau d’octets.
   * Créez un `PDFFormRenderSpec` qui est utilisé pour définir les options d’exécution. Attribuer la valeur `true` au `PDFFormRenderSpec` de `generateServerAppearance` champ .
   * Appeler la variable `FormsServiceClient` de `renderPDFForm2` et transmettez les valeurs suivantes :

      * A `BLOB` qui contient le formulaire du PDF à afficher.
      * A `BLOB` contenant les données à fusionner avec le formulaire.
      * A `PDFFormRenderSpec` qui stocke les options d’exécution.
      * A `URLSpec` contenant des valeurs URI requises par le service Forms. Vous pouvez indiquer `null` pour cette valeur de paramètre.
      * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.
      * Paramètre de sortie long utilisé pour stocker le nombre de pages dans le formulaire.
      * Paramètre de sortie string utilisé pour la valeur locale.
      * A `FormResult` valeur qui est un paramètre de sortie utilisé pour stocker le formulaire interactif.
   * Retirez le formulaire du PDF en appelant la méthode `FormsResult` de `outputContent` champ . Ce champ stocke une `BLOB` qui représente le formulaire interactif.


1. Signez le formulaire interactif

   Signez le document du PDF en appelant la méthode `SignatureServiceClient` de `sign` et transmission des valeurs suivantes :

   * A `BLOB` qui représente le document du PDF à signer. Utilisez la variable `BLOB` instance renvoyée par le service Forms.
   * Une valeur string qui représente le nom du champ de signature signé.
   * A `Credential` qui représente les informations d’identification utilisées pour signer numériquement le document du PDF. Créez un `Credential` en utilisant son constructeur et en spécifiant l’alias en attribuant une valeur à la variable `Credential` de `alias` .
   * A `HashAlgorithm` qui spécifie un membre de données statique qui représente l’algorithme de hachage à utiliser pour condenser le document du PDF. Par exemple, vous pouvez spécifier `HashAlgorithm.SHA1` pour utiliser l’algorithme SHA1.
   * Valeur boolean qui spécifie si l’algorithme de hachage est utilisé.
   * Une valeur string qui représente la raison pour laquelle le document du PDF a été signé numériquement.
   * Une valeur string qui représente l’emplacement du signataire.
   * Une valeur string qui représente les informations de contact du signataire.
   * A `PDFSignatureAppearanceOptions` qui contrôle l’aspect de la signature numérique. Vous pouvez, par exemple, utiliser cet objet pour ajouter un logo personnalisé à une signature numérique.
   * A `System.Boolean` qui spécifie si la révocation doit être vérifiée sur le certificat du signataire. Si cette vérification de révocation est effectuée, elle est incorporée dans la signature. La valeur par défaut est de `false`.
   * Un `OCSPPreferences` qui stocke des préférences pour la prise en charge du protocole OCSP (Online Certificate Status Protocol). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`. Pour plus d’informations sur cet objet, voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` qui stocke les préférences de liste de révocation des certificats (CRL). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `TSPPreferences` qui stocke les préférences pour la prise en charge du fournisseur d’horodatage (TSP). Ce paramètre est facultatif et peut être `null`.

   Le `sign` renvoie une `BLOB` qui représente le document du PDF signé.

1. Enregistrement du document de PDF signé

   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF signé et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui a été renvoyé par l’objet `sign` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Signature numérique d’un Forms interactif](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Certification de documents PDF {#certifying-pdf-documents}

Vous pouvez définir un document PDF en le certifiant avec un type de signature particulier appelé signature certifiée. Une signature certifiée se différencie d’une signature numérique de plusieurs manières :

* Elle doit être la première signature appliquée au document PDF ; cela veut dire que lorsque la signature certifiée est appliquée, tous les autres champs de signature du document doivent être non signés. Une seule signature certifiée est autorisée dans un document PDF. Si vous souhaitez signer ou certifier un document PDF, vous devez le certifier avant de le signer. Après avoir certifié un document PDF, vous pouvez signer numériquement les champs de signature supplémentaires.
* L’auteur ou l’expéditeur du document peut indiquer que le document peut être modifié de certaines manières sans invalider la signature certifiée. Par exemple, le document peut autoriser le remplissage de formulaires ou de commentaires. Si l’auteur spécifie qu’une modification spécifique est autorisée, Acrobat limite ainsi les utilisateurs dans la modification du document. Si ces modifications sont effectuées, à l’aide d’une autre application par exemple, la signature certifiée est alors non valide et Acrobat affiche un avertissement à l’ouverture du document. (Avec des signatures non certifiées, les modifications ne sont pas empêchées et les opérations normales de modification n’invalident pas la signature d’origine.)
* Au moment de la signature, les différents types de contenus du document susceptibles de rendre le document ambigu ou trompeur sont analysés. Par exemple, une annotation peut assombrir du texte sur une page qui est essentiel pour comprendre ce qui est certifié. Une explication (attestation légale) peut être fournie pour un type de contenu.

Vous pouvez certifier par programmation les documents du PDF à l’aide de l’API Java du service Signature ou de l’API du service Web de signature. Lors de la certification d’un document de PDF, vous devez référencer des informations d’identification de sécurité qui existent dans le service d’informations d’identification. Pour plus d’informations sur les informations d’identification de sécurité, voir *Installation et déploiement d’AEM Forms* guide pour votre serveur d’applications.

>[!NOTE]
>
>Lors de la certification et de la signature du même document de PDF, si la signature de certification n’est pas approuvée, un triangle jaune s’affiche en regard de la signature du premier signe lorsque vous ouvrez le document de PDF dans Acrobat ou Adobe Reader. La signature de certification doit être fiable pour éviter cette situation.

>[!NOTE]
>
>Lors de l’utilisation d’informations d’identification HSM InShield pour signer ou certifier un document de PDF, les nouvelles informations d’identification ne peuvent pas être utilisées tant que le serveur d’applications J2EE sur lequel AEM Forms est déployé n’a pas été redémarré. Cependant, vous pouvez définir une valeur de configuration, ce qui entraîne le fonctionnement de l’opération de signature ou de certification sans redémarrer le serveur d’applications J2EE.

Vous pouvez ajouter la valeur de configuration suivante dans le fichier cknfastrc, qui se trouve sous /opt/nfast/cknfastrc (ou c:\nfast\cknfastrc) :

```as3
             CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Après avoir ajouté cette valeur de configuration au fichier .cknfastrc, les nouvelles informations d’identification peuvent être utilisées sans redémarrer le serveur d’applications J2EE.

>[!NOTE]
>
>Pour plus d’informations sur le service Signature et la certification d’un document, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-5}

Pour certifier un document PDF, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Signature.
1. Obtenez le document du PDF à certifier.
1. Certifiez le document du PDF.
1. Enregistrez le document de PDF certifié en tant que fichier de PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Signature**

Avant d’effectuer par programmation une opération Signature, vous devez créer un client Signature.

**Obtention du document du PDF à certifier**

Pour certifier un document de PDF, vous devez obtenir un document de PDF contenant un champ de signature. Si un document de PDF ne contient pas de champ de signature, il ne peut pas être certifié. Vous pouvez ajouter un champ de signature à l’aide de Designer ou par programmation. Pour plus d’informations sur l’ajout par programmation d’un champ de signature, voir [Ajout de champs de signature](digitally-signing-certifying-documents.md#adding-signature-fields).

**Certifier le document du PDF**

Pour certifier correctement un document de PDF, vous avez besoin des valeurs d’entrée suivantes utilisées par le service Signature pour certifier un document de PDF :

* **Document PDF**: Un document du PDF qui contient un champ de signature, qui est un champ de formulaire qui contient une représentation graphique de la signature certifiée. Un document de PDF doit contenir un champ de signature pour pouvoir être certifié. Vous pouvez ajouter un champ de signature à l’aide de Designer ou par programmation. (Voir [Ajout de champs de signature](digitally-signing-certifying-documents.md#adding-signature-fields).)
* **Nom du champ de signature**: Nom qualifié complet du champ de signature certifié. La valeur suivante est un exemple : `form1[0].#subform[1].SignatureField3[3]`. Lors de l’utilisation d’un champ de formulaire XFA, le nom partiel du champ de signature peut également être utilisé : `SignatureField3[3]`. Si une valeur null est transmise pour le nom du champ, un champ de signature invisible est créé et certifié dynamiquement.
* **Informations d’identification de sécurité**: Informations d’identification utilisées pour certifier le document du PDF. Ces informations d’identification de sécurité contiennent un mot de passe et un alias, qui doivent correspondre à un alias qui apparaît dans les informations d’identification situées dans le service d’informations d’identification. L’alias est une référence à des informations d’identification réelles qui peuvent se trouver dans un fichier PKCS#12 (avec une extension .pfx) ou un module de sécurité matérielle (HSM).
* **Algorithme de hachage**: Algorithme de hachage à utiliser pour condenser le document du PDF.
* **Motif de la signature**: Une valeur qui s’affiche dans Acrobat ou Adobe Reader afin que d’autres utilisateurs connaissent la raison pour laquelle le document du PDF a été certifié.
* **Emplacement du signataire**: Emplacement du signataire spécifié par les informations d’identification.
* **Coordonnées**: Les informations de contact, telles que l’adresse et le numéro de téléphone, du signataire.
* **Informations d’autorisation**: Autorisations qui contrôlent les actions qu’un utilisateur final peut effectuer sur un document sans que la signature certifiée ne soit invalide. Par exemple, vous pouvez définir l’autorisation de sorte que toute modification apportée au document du PDF entraîne la non-validité de la signature certifiée.
* **Informations juridiques**: Lorsqu’un document est certifié, il est automatiquement analysé à la recherche de types de contenu spécifiques susceptibles de rendre le contenu d’un document ambigu ou trompeur. Par exemple, une annotation peut assombrir du texte sur une page qui est essentiel pour comprendre ce qui est certifié. Le processus d’analyse génère des avertissements concernant ces types de contenu. Cette valeur fournit une explication supplémentaire du contenu susceptible d’avoir généré des avertissements.
* **Options d’aspect**: Options qui contrôlent l’aspect de la signature certifiée. Par exemple, la signature certifiée peut afficher des informations sur la date.
* **Vérification de révocation**: Cette valeur indique si la vérification de révocation est effectuée pour le certificat du signataire. Le paramètre par défaut de `false` signifie que la vérification de révocation n’est pas effectuée.
* **Paramètres OCSP**: Paramètres de prise en charge du protocole OCSP (Online Certificate Status Protocol), qui fournit des informations sur l’état des informations d’identification utilisées pour certifier le document du PDF. Vous pouvez, par exemple, spécifier l’URL du serveur qui fournit des informations sur les informations d’identification que vous utilisez pour vous connecter au document du PDF.
* **Paramètres de CRL**: Paramètres des préférences de liste de révocation des certificats (CRL) si la vérification de révocation est effectuée. Par exemple, vous pouvez spécifier de toujours vérifier si des informations d’identification ont été révoquées.
* **Horodatage**: Paramètres qui définissent les informations d’horodatage appliquées à la signature certifiée. Un horodatage indique que des données spécifiques ont été établies avant une certaine période. Ces connaissances contribuent à établir une relation de confiance entre le signataire et le vérificateur.

**Enregistrement du document de PDF certifié en tant que fichier de PDF**

Une fois que le service Signature a certifié le document du PDF, vous pouvez l’enregistrer en tant que fichier du PDF afin que les utilisateurs puissent l’ouvrir dans Acrobat ou Adobe Reader.

**Voir également**

[Certifier les documents du PDF à l’aide de l’API Java](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-java-api)

[Certifier les documents du PDF à l’aide de l’API du service Web](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Ajout de champs de signature](digitally-signing-certifying-documents.md#adding-signature-fields)

### Certifier les documents du PDF à l’aide de l’API Java {#certify-pdf-documents-using-the-java-api}

Certifiez un document de PDF à l’aide de l’API Signature (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un client Signature

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtention du document du PDF à certifier

   * Créez un `java.io.FileInputStream` qui représente le document du PDF à certifier en utilisant son constructeur et en transmettant une valeur string spécifiant l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Certifier le document du PDF

   Certifiez le document du PDF en appelant la méthode `SignatureServiceClient` de `certify` et transmission des valeurs suivantes :

   * Le `com.adobe.idp.Document` qui représente le document du PDF à certifier.
   * Une valeur string qui représente le nom du champ de signature qui contiendra la signature.
   * A `Credential` qui représente les informations d’identification utilisées pour certifier le document du PDF. Créez un `Credential` en appelant le `Credential` statique de l’objet `getInstance` et transmettre une valeur string qui spécifie la valeur alias qui correspond aux informations d’identification de sécurité.
   * A `HashAlgorithm` qui spécifie un membre de données statique qui représente l’algorithme de hachage utilisé pour condenser le document du PDF. Par exemple, vous pouvez spécifier `HashAlgorithm.SHA1` pour utiliser l’algorithme SHA1.
   * Une valeur string qui représente la raison pour laquelle le document du PDF a été certifié.
   * Une valeur string qui représente les informations de contact du signataire.
   * A `MDPPermissions` qui spécifie les actions pouvant être effectuées sur le document du PDF qui invalide la signature.
   * A `PDFSignatureAppearanceOptions` qui contrôle l’aspect de la signature certifiée. Si vous le souhaitez, modifiez l’aspect de la signature en appelant une méthode, telle que `setShowDate`.
   * Une valeur string qui fournit une explication des actions qui invalident la signature.
   * A `java.lang.Boolean` qui spécifie si la révocation doit être vérifiée sur le certificat du signataire. Si cette vérification de révocation est effectuée, elle est incorporée dans la signature. La valeur par défaut est de `false`.
   * A `java.lang.Boolean` qui spécifie si le champ de signature en cours de certification est verrouillé. Si le champ est verrouillé, le champ de signature est marqué comme en lecture seule, ses propriétés ne peuvent pas être modifiées et il ne peut pas être effacé par quiconque ne dispose pas des autorisations requises. La valeur par défaut est de `false`.
   * Un `OCSPPreferences` qui stocke des préférences pour la prise en charge du protocole OCSP (Online Certificate Status Protocol). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`. Pour plus d’informations sur cet objet, voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` qui stocke les préférences de liste de révocation des certificats (CRL). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `TSPPreferences` qui stocke les préférences pour la prise en charge du fournisseur d’horodatage (TSP). Par exemple, après avoir créé une `TSPPreferences` , vous pouvez définir l’URL du serveur TSP en appelant la variable `TSPPreferences` de `setTspServerURL` . Ce paramètre est facultatif et peut être `null`. Pour plus d’informations, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

   Le `certify` renvoie une `com.adobe.idp.Document` qui représente le document de PDF certifié.

1. Enregistrement du document de PDF certifié en tant que fichier de PDF

   * Créez un objet `java.io.File` et assurez-vous que l’extension du fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` vers le fichier .

**Voir également**

[Certification de documents PDF](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[Démarrage rapide (mode SOAP) : Certification d’un document de PDF à l’aide de l’API Java](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Certifier les documents du PDF à l’aide de l’API du service Web {#certify-pdf-documents-using-the-web-service-api}

Certifiez un document de PDF à l’aide de l’API Signature (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Signature

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Obtention du document du PDF à certifier

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document PDF certifié.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF à certifier et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` membre de données : contenu du tableau d’octets.

1. Certifier le document du PDF

   Certifiez le document du PDF en appelant la méthode `SignatureServiceClient` de `certify` et transmission des valeurs suivantes :

   * Le `BLOB` qui représente le document du PDF à certifier.
   * Une valeur string qui représente le nom du champ de signature qui contiendra la signature.
   * A `Credential` qui représente les informations d’identification utilisées pour certifier le document du PDF. Créez un `Credential` en utilisant son constructeur, puis spécifiez l’alias en attribuant une valeur à la variable `Credential` de `alias` .
   * A `HashAlgorithm` qui spécifie un membre de données statique qui représente l’algorithme de hachage utilisé pour condenser le document du PDF. Par exemple, vous pouvez spécifier `HashAlgorithm.SHA1` pour utiliser l’algorithme SHA1.
   * Valeur boolean qui spécifie si l’algorithme de hachage est utilisé.
   * Une valeur string qui représente la raison pour laquelle le document du PDF a été certifié.
   * Une valeur string qui représente l’emplacement du signataire.
   * Une valeur string qui représente les informations de contact du signataire.
   * Un `MDPPermissions` membre de données statique de l’objet qui spécifie les actions pouvant être effectuées sur le document du PDF qui invalide la signature.
   * Une valeur booléenne qui spécifie si l’utilisation de la variable `MDPPermissions` qui a été transmis comme valeur du paramètre précédent.
   * Une valeur string qui explique les actions qui invalident la signature.
   * A `PDFSignatureAppearanceOptions` qui contrôle l’aspect de la signature certifiée. Créez un objet `PDFSignatureAppearanceOptions` en utilisant son constructeur. Vous pouvez modifier l’aspect de la signature en définissant l’un de ses membres de données.
   * A `System.Boolean` qui spécifie si la révocation doit être vérifiée sur le certificat du signataire. Si cette vérification de révocation est effectuée, elle est incorporée dans la signature. La valeur par défaut est de `false`.
   * A `System.Boolean` qui spécifie si le champ de signature en cours de certification est verrouillé. Si le champ est verrouillé, le champ de signature est marqué comme en lecture seule, ses propriétés ne peuvent pas être modifiées et il ne peut pas être effacé par quiconque ne dispose pas des autorisations requises. La valeur par défaut est de `false`.
   * A `System.Boolean` qui spécifie si le champ de signature est verrouillé. C&#39;est-à-dire si vous passez `true` au paramètre précédent, puis transmettez `true` à ce paramètre.
   * Un `OCSPPreferences` qui stocke des préférences pour la prise en charge du protocole OCSP (Online Certificate Status Protocol), qui fournit des informations sur l’état des informations d’identification utilisées pour certifier le document du PDF. Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `CRLPreferences` qui stocke les préférences de liste de révocation des certificats (CRL). Si la vérification de révocation n’est pas effectuée, ce paramètre n’est pas utilisé et vous pouvez spécifier `null`.
   * A `TSPPreferences` qui stocke les préférences pour la prise en charge du fournisseur d’horodatage (TSP). Par exemple, après avoir créé une `TSPPreferences` , vous pouvez définir l’URL du TSP en définissant la variable `TSPPreferences` de `tspServerURL` membre de données. Ce paramètre est facultatif et peut être `null`.

   Le `certify` renvoie une `BLOB` qui représente le document de PDF certifié.

1. Enregistrement du document de PDF certifié en tant que fichier de PDF

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF qui contiendra le document du PDF certifié et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui a été renvoyé par l’objet `certify` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `binaryData` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Certification de documents PDF](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Vérification des signatures numériques {#verifying-digital-signatures}

Les signatures numériques peuvent être vérifiées pour vous assurer qu’un document PDF signé n’a pas été modifié et que la signature numérique est valide. Lors de la vérification d’une signature numérique, vous pouvez vérifier l’état de la signature et les propriétés de la signature, telles que l’identité du signataire. Avant d’approuver une signature numérique, il est recommandé de la vérifier. Lors de la vérification d’une signature numérique, référencez un document PDF contenant une signature numérique.

Supposons que l’identité du signataire soit inconnue. Lorsque vous ouvrez le document du PDF dans Acrobat, un message d’avertissement indique que l’identité du signataire est inconnue, comme illustré ci-dessous.

![vd_vd_verifysig](assets/vd_vd_verifysig.png)

De même, lorsque vous vérifiez par programmation une signature numérique, vous pouvez déterminer l’état de l’identité du signataire. Par exemple, si vous vérifiez la signature numérique dans le document illustré ci-dessus, l’identité du signataire est inconnue.

>[!NOTE]
>
>Pour plus d’informations sur le service Signature et la vérification des signatures numériques, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-6}

Pour vérifier une signature numérique, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Signature.
1. Obtenez le document du PDF qui contient la signature à vérifier.
1. Définissez les options d’exécution PKI.
1. Vérifiez la signature numérique.
1. Déterminez l’état de la signature.
1. Déterminez l’identité du signataire.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, incluez les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Signature**

Avant d’effectuer une opération de service Signature par programmation, créez un client de service Signature.

**Obtention du document du PDF qui contient la signature à vérifier**

Pour vérifier une signature utilisée pour signer ou certifier numériquement un document de PDF, obtenez un document de PDF contenant une signature.

**Définition des options d’exécution PKI**

Définissez les options d’exécution PKI que le service Signature utilise lors de la vérification des signatures dans un document PDF :

* Heure de vérification
* Vérification de révocation
* Valeurs d’horodatage

Dans le cadre de la définition de ces options, vous pouvez spécifier l’heure de vérification. Par exemple, vous pouvez sélectionner l’heure actuelle (l’heure sur l’ordinateur du programme de validation), qui indique d’utiliser l’heure actuelle. Pour plus d’informations sur les différentes valeurs temporelles, voir `VerificationTime` valeur d’énumération dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Vous pouvez également indiquer si la vérification de révocation doit être effectuée dans le cadre du processus de vérification. Par exemple, vous pouvez effectuer une vérification de révocation pour déterminer si le certificat est révoqué. Pour plus d’informations sur les options de vérification de révocation, voir `RevocationCheckStyle` valeur d’énumération dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Pour effectuer une vérification de révocation sur un certificat, spécifiez une URL vers un serveur de liste de révocation des certificats (CRL) à l’aide d’une `CRLOptionSpec` . Cependant, si vous ne spécifiez pas d’URL vers le serveur CRL, le service Signature obtient l’URL à partir du certificat.

Au lieu d’utiliser un serveur CRL, vous pouvez utiliser un serveur OCSP (Online Certificate Status Protocol) lors de la vérification de révocation. En règle générale, lorsque vous utilisez un serveur OCSP plutôt qu’un serveur CRL, la vérification de révocation est plus rapide. (Voir [Protocole d’état du certificat en ligne](https://tools.ietf.org/html/rfc2560).)

Vous pouvez définir la liste de révocation des certificats et l’ordre du serveur OCSP que le service Signature utilise à l’aide des applications et services Adobe. Par exemple, si le serveur OCSP est d’abord défini dans Applications et services Adobe, alors le serveur OCSP est coché, suivi du serveur CRL.

Si vous n’effectuez pas de vérification de révocation, le service Signature ne vérifie pas si le certificat est révoqué. En d’autres termes, les informations de CRL et du serveur OCSP sont ignorées.

>[!NOTE]
>
>Vous pouvez remplacer l’URL spécifiée dans le certificat à l’aide d’une `CRLOptionSpec` et un `OCSPOptionSpec` . Par exemple, pour remplacer le serveur CRL, vous pouvez appeler la variable `CRLOptionSpec` de `setLocalURI` .

L’horodatage est le processus de suivi de l’heure de modification d’un document signé ou certifié. Une fois le document signé, personne ne peut le modifier. L’horodatage permet d’assurer la validité d’un document signé ou certifié. Vous pouvez définir des options d’horodatage à l’aide d’une `TSPOptionSpec` . Par exemple, vous pouvez spécifier l’URL d’un serveur de fournisseur d’horodatage (TSP).

>[!NOTE]
>
>Dans les démarrages rapides de Java et de service Web, l’heure de vérification est définie sur `VerificationTime.CURRENT_TIME` et la vérification de révocation est définie sur `RevocationCheckStyle.BestEffort`. Comme aucune information de CRL ou de serveur OCSP n’est spécifiée, les informations du serveur sont obtenues à partir du certificat.

**Vérification de la signature numérique**

Pour vérifier une signature, indiquez le nom qualifié complet du champ de signature qui contient la signature, tel que `form1[0].#subform[1].SignatureField3[3]`. Lors de l’utilisation d’un champ de formulaire XFA, vous pouvez également utiliser le nom partiel du champ de signature : `SignatureField3`.

Par défaut, le service Signature limite à 65 minutes la durée pendant laquelle un document peut être signé après validation. Si un utilisateur tente de vérifier une signature à l’heure actuelle et que l’heure de signature est postérieure à l’heure actuelle et qu’elle est inférieure à 65 minutes, le service Signature ne crée pas d’erreur de vérification.

>[!NOTE]
>
>Pour connaître les autres valeurs dont vous avez besoin lors de la vérification d’une signature, voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Déterminer l’état de la signature**

Dans le cadre de la vérification d’une signature numérique, vous pouvez vérifier l’état de la signature.

**Détermination de l’identité du signataire**

Vous pouvez déterminer l’identité du signataire, qui peut être l’une des valeurs suivantes :

* **Inconnu**: Ce signataire est inconnu, car la vérification du signataire ne peut pas être effectuée.
* **Trusted**: Ce signataire est fiable.
* **Non approuvé**: Ce signataire n’est pas approuvé.

**Voir également**

[Vérification des signatures numériques à l’aide de l’API Java](#unresolvedlink-lc-si)

[Vérification des signatures numériques à l’aide de l’API de service Web](#unresolvedlink-lc-si)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Vérification des signatures numériques à l’aide de l’API Java {#verify-digital-signatures-using-the-java-api}

Vérifiez une signature numérique à l’aide de l’API Signature Service (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar, dans le chemin d’accès aux classes de votre projet Java.

1. [Création d’un client Signature](#unresolvedlink-lc-si)

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtention du document du PDF qui contient la signature à vérifier

   * Créez un `java.io.FileInputStream` qui représente le document du PDF contenant la signature à vérifier à l’aide de son constructeur. Transmettez une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définition des options d’exécution PKI

   * Créez un objet `PKIOptions` en utilisant son constructeur.
   * Définissez l’heure de vérification en appelant la variable `PKIOptions` de `setVerificationTime` et transmission d’une `VerificationTime` valeur d’énumération qui spécifie l’heure de vérification.
   * Définissez l’option révocation-vérification en appelant `PKIOptions` de `setRevocationCheckStyle` et transmission d’une `RevocationCheckStyle` valeur d’énumération qui spécifie s’il faut effectuer une vérification de révocation.

1. Vérification de la signature numérique

   Vérifiez la signature en appelant le `SignatureServiceClient` de `verify2` et transmission des valeurs suivantes :

   * A `com.adobe.idp.Document` contenant un document de PDF signé numériquement ou certifié.
   * Une valeur string qui représente le nom du champ de signature qui contient la signature à vérifier.
   * A `PKIOptions` contenant les options d’exécution PKI.
   * A `VerifySPIOptions` qui contient des informations SPI. Vous pouvez indiquer `null` pour ce paramètre.

   Le `verify2` renvoie une `PDFSignatureVerificationInfo` contenant des informations qui peuvent être utilisées pour vérifier la signature numérique.

1. Déterminer l’état de la signature

   * Déterminez l’état de la signature en appelant la fonction `PDFSignatureVerificationInfo` de `getStatus` . Cette méthode renvoie une `SignatureStatus` qui spécifie l’état de signature. Par exemple, si un document de PDF signé n’est pas modifié, cette méthode renvoie la valeur `SignatureStatus.DocumentSigNoChanges`.

1. Détermination de l’identité du signataire

   * Déterminer l’identité du signataire en appelant la variable `PDFSignatureVerificationInfo` de `getSigner` . Cette méthode renvoie une `IdentityInformation` .
   * Appeler la variable `IdentityInformation` de `getStatus` pour déterminer l’identité du signataire. Cette méthode renvoie une `IdentityStatus` valeur d’énumération spécifiant l’identité. Par exemple, si le signataire est approuvé, cette méthode renvoie la valeur `IdentityStatus.TRUSTED`.

**Voir également**

[Vérification des signatures numériques](#unresolvedlink-lc-si)

[Démarrage rapide (mode SOAP) : Vérification d’une signature numérique à l’aide de l’API Java](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Vérification des signatures numériques à l’aide de l’API de service Web {#verify-digital-signatures-using-the-web-service-api}

Vérifiez une signature numérique à l’aide de l’API Signature Service (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Signature

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Obtention du document du PDF qui contient la signature à vérifier

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document de PDF contenant une signature numérique ou certifiée à vérifier.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF signé et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` propriété le contenu du tableau d’octets.

1. Définition des options d’exécution PKI

   * Créez un objet `PKIOptions` en utilisant son constructeur.
   * Définissez l’heure de vérification en attribuant la variable `PKIOptions` de `verificationTime` membre de données `VerificationTime` valeur d’énumération qui spécifie l’heure de vérification.
   * Définissez l’option de vérification de révocation en attribuant la variable `PKIOptions` de `revocationCheckStyle` membre de données `RevocationCheckStyle` valeur d’énumération qui spécifie s’il faut effectuer une vérification de révocation.

1. Vérification de la signature numérique

   Vérifiez la signature en appelant le `SignatureServiceClient` de `verify2` et transmission des valeurs suivantes :

   * Le `BLOB` contenant un document de PDF signé numériquement ou certifié.
   * Une valeur string qui représente le nom du champ de signature qui contient la signature à vérifier.
   * A `PKIOptions` contenant les options d’exécution PKI.
   * A `VerifySPIOptions` qui contient des informations SPI. Vous pouvez indiquer `null` pour ce paramètre.

   Le `verify2` renvoie une `PDFSignatureVerificationInfo` contenant des informations qui peuvent être utilisées pour vérifier la signature numérique.

1. Déterminer l’état de la signature

   Déterminez l’état de la signature en obtenant la valeur de la propriété `PDFSignatureVerificationInfo` de `status` membre de données. Ce membre de données stocke une `SignatureStatus` qui spécifie l’état de la signature. Par exemple, si un document de PDF signé est modifié, la variable `status` le membre de données stocke la valeur `SignatureStatus.DocumentSigNoChanges`.

1. Détermination de l’identité du signataire

   * Déterminer l’identité du signataire en récupérant la valeur de la variable `PDFSignatureVerificationInfo` de `signer` membre de données. Ce membre renvoie une `IdentityInformation` .
   * Récupération de la variable `IdentityInformation` de `status` membre de données pour déterminer l’identité du signataire. Ce membre de données renvoie une `IdentityStatus` valeur d’énumération spécifiant l’identité. Par exemple, si le signataire est approuvé, ce membre renvoie `IdentityStatus.TRUSTED`.

**Voir également**

[Vérification des signatures numériques](#unresolvedlink-lc-si)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Vérification de plusieurs signatures numériques {#verifying-multiple-digital-signatures}

AEM Forms permet de vérifier toutes les signatures numériques qui se trouvent dans un document PDF. Supposons qu’un document de PDF contienne plusieurs signatures numériques suite à un processus d’entreprise qui requiert des signatures de plusieurs signataires. Prenons l’exemple d’une transaction financière qui requiert à la fois la signature d’un agent de prêt et celle d’un responsable. Vous pouvez utiliser l’API Java du service Signature ou l’API du service Web pour vérifier toutes les signatures du document du PDF. Lors de la vérification de plusieurs signatures numériques, vous pouvez vérifier l’état et les propriétés de chaque signature. Avant de faire confiance à une signature numérique, il est recommandé de la vérifier. Il est recommandé de vous familiariser avec la vérification d’une signature numérique unique.

>[!NOTE]
>
>Pour plus d’informations sur le service Signature et la vérification des signatures numériques, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-7}

Pour vérifier plusieurs signatures numériques, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Signature.
1. Obtenez le document du PDF qui contient les signatures à vérifier.
1. Définissez les options d’exécution PKI.
1. Récupérez toutes les signatures numériques.
1. Parcourez toutes les signatures.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, incluez les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Signature**

Avant d’effectuer une opération de service Signature par programmation, créez un client de service Signature.

**Obtention du document du PDF qui contient les signatures à vérifier**

Pour vérifier une signature utilisée pour signer ou certifier numériquement un document de PDF, obtenez un document de PDF contenant une signature.

**Définition des options d’exécution PKI**

Définissez les options d’exécution PKI que le service Signature utilise lors de la vérification de toutes les signatures dans un document PDF :

* Heure de vérification
* Vérification de révocation
* Valeurs d’horodatage

Dans le cadre de la définition de ces options, vous pouvez spécifier l’heure de vérification. Par exemple, vous pouvez sélectionner l’heure actuelle (l’heure sur l’ordinateur du programme de validation), qui indique d’utiliser l’heure actuelle. Pour plus d’informations sur les différentes valeurs temporelles, voir `VerificationTime` valeur d’énumération dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Vous pouvez également indiquer si la vérification de révocation doit être effectuée dans le cadre du processus de vérification. Par exemple, vous pouvez effectuer une vérification de révocation pour déterminer si le certificat est révoqué. Pour plus d’informations sur les options de vérification de révocation, voir `RevocationCheckStyle` valeur d’énumération dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Pour effectuer une vérification de révocation sur un certificat, spécifiez une URL vers un serveur de liste de révocation des certificats (CRL) à l’aide d’une `CRLOptionSpec` . Cependant, si vous ne spécifiez pas d’URL vers un serveur CRL, le service Signature obtient l’URL à partir du certificat.

Au lieu d’utiliser un serveur CRL, vous pouvez utiliser un serveur OCSP (Online Certificate Status Protocol) lors de la vérification de révocation. En règle générale, lorsque vous utilisez un serveur OCSP plutôt qu’un serveur CRL, la vérification de révocation est plus rapide. (Voir [Protocole d’état du certificat en ligne](https://tools.ietf.org/html/rfc2560).)

Vous pouvez définir la liste de révocation des certificats et l’ordre du serveur OCSP que le service Signature utilise à l’aide des applications et services Adobe. Par exemple, si le serveur OCSP est défini en premier dans les applications et services Adobe, le serveur OCSP est coché, suivi du serveur CRL.

Si vous n’effectuez pas de vérification de révocation, le service Signature ne vérifie pas si le certificat est révoqué. En d’autres termes, les informations de CRL et du serveur OCSP sont ignorées.

>[!NOTE]
>
>Vous pouvez remplacer l’URL spécifiée dans le certificat à l’aide d’une `CRLOptionSpec` et un `OCSPOptionSpec` . Par exemple, pour remplacer le serveur CRL, vous pouvez appeler la variable `CRLOptionSpec` de `setLocalURI` .

L’horodatage est le processus de suivi de l’heure de modification d’un document signé ou certifié. Une fois le document signé, personne ne peut le modifier. L’horodatage permet d’assurer la validité d’un document signé ou certifié. Vous pouvez définir des options d’horodatage à l’aide d’une `TSPOptionSpec` . Par exemple, vous pouvez spécifier l’URL d’un serveur de fournisseur d’horodatage (TSP).

>[!NOTE]
>
>Dans les démarrages rapides de Java et de service Web, l’heure de vérification est définie sur `VerificationTime.CURRENT_TIME` et la vérification de révocation est définie sur `RevocationCheckStyle.BestEffort`. Comme aucune information de CRL ou de serveur OCSP n’est spécifiée, les informations du serveur sont obtenues à partir du certificat.

**Récupération de toutes les signatures numériques**

Pour vérifier toutes les signatures numériques figurant dans un document de PDF, récupérez les signatures numériques du document de PDF. Toutes les signatures sont renvoyées dans une liste. Dans le cadre de la vérification d’une signature numérique, vérifiez l’état de la signature.

>[!NOTE]
>
>Contrairement à ce qui se passe lorsque vous vérifiez une signature numérique unique, lorsque vous vérifiez plusieurs signatures, vous n’avez pas à spécifier le nom du champ de signature.

**Parcourir toutes les signatures**

Effectuez une itération sur chaque signature. Autrement dit, pour chaque signature, vérifiez la signature numérique et vérifiez l’identité du signataire et l’état de chaque signature. (Voir [Vérification des signatures numériques](#unresolvedlink-lc-si).)

>[!NOTE]
>
>Vous n’avez pas besoin d’effectuer une itération sur toutes les signatures si l’exigence correspond à l’intégralité du document.

**Voir également**

[Vérification de plusieurs signatures numériques à l’aide de l’API Java](#unresolvedlink-lc-si)

[Vérification de plusieurs signatures numériques à l’aide de l’API du service Web](#unresolvedlink-lc-si)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Vérification de plusieurs signatures numériques à l’aide de l’API Java {#verify-multiple-digital-signatures-using-the-java-api}

Vérifiez plusieurs signatures numériques à l’aide de l’API Signature Service (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar, dans le chemin d’accès aux classes de votre projet Java.

1. Création d’un client Signature

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtention du document du PDF qui contient les signatures à vérifier

   * Créez un `java.io.FileInputStream` qui représente le document du PDF qui contient plusieurs signatures numériques à vérifier à l’aide de son constructeur. Transmettez une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définition des options d’exécution PKI

   * Créez un objet `PKIOptions` en utilisant son constructeur.
   * Définissez l’heure de vérification en appelant la variable `PKIOptions` de `setVerificationTime` et transmission d’une `VerificationTime` valeur d’énumération qui spécifie l’heure de vérification.
   * Définissez l’option de vérification de révocation en appelant `PKIOptions` de `setRevocationCheckStyle` et transmission d’une `RevocationCheckStyle` valeur d’énumération qui spécifie s’il faut effectuer une vérification de révocation.

1. Récupération de toutes les signatures numériques

   Appeler la variable `SignatureServiceClient` de `verifyPDFDocument` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` contenant un document PDF contenant plusieurs signatures numériques.
   * A `PKIOptions` contenant les options d’exécution PKI.
   * A `VerifySPIOptions` qui contient des informations SPI. Vous pouvez indiquer `null` pour ce paramètre.

   Le `verifyPDFDocument` renvoie une `PDFDocumentVerificationInfo` contenant des informations sur toutes les signatures numériques figurant dans le document PDF.

1. Parcourir toutes les signatures

   * Parcourez toutes les signatures en appelant la méthode `PDFDocumentVerificationInfo` de `getVerificationInfos` . Cette méthode renvoie une `java.util.List` où chaque élément est un objet `PDFSignatureVerificationInfo` . Utilisez une `java.util.Iterator` pour effectuer une itération sur la liste des signatures.
   * En utilisant la variable `PDFSignatureVerificationInfo` , vous pouvez exécuter des tâches telles que déterminer l’état de la signature en appelant la fonction `PDFSignatureVerificationInfo` de `getStatus` . Cette méthode renvoie une `SignatureStatus` dont le membre de données statique vous informe sur l’état de la signature. Par exemple, si la signature est inconnue, cette méthode renvoie la valeur `SignatureStatus.DocumentSignatureUnknown`.

**Voir également**

[Vérification de plusieurs signatures numériques](#unresolvedlink-lc-si)

[Démarrage rapide (mode SOAP) : Vérification de plusieurs signatures numériques à l’aide de l’API Java](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Vérification des signatures numériques](#unresolvedlink-lc-si)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Vérification de plusieurs signatures numériques à l’aide de l’API du service Web {#verifying-multiple-digital-signatures-using-the-web-service-api}

Vérifiez plusieurs signatures numériques à l’aide de l’API Signature Service (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Signature

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Obtention du document du PDF qui contient les signatures à vérifier

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` stocke un document PDF contenant plusieurs signatures numériques à vérifier.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` propriété le contenu du tableau d’octets.

1. Définition des options d’exécution PKI

   * Créez un objet `PKIOptions` en utilisant son constructeur.
   * Définissez l’heure de vérification en attribuant la variable `PKIOptions` de `verificationTime` membre de données `VerificationTime` valeur d’énumération qui spécifie l’heure de vérification.
   * Définissez l’option de vérification de révocation en attribuant la variable `PKIOptions` de `revocationCheckStyle` membre de données `RevocationCheckStyle` valeur d’énumération qui spécifie s’il faut effectuer une vérification de révocation.

1. Récupération de toutes les signatures numériques

   Appeler la variable `SignatureServiceClient` de `verifyPDFDocument` et transmettez les valeurs suivantes :

   * A `BLOB` contenant un document PDF contenant plusieurs signatures numériques.
   * A `PKIOptions` contenant les options d’exécution PKI.
   * A `VerifySPIOptions` qui contient des informations SPI. Vous pouvez spécifier null pour ce paramètre.

   Le `verifyPDFDocument` renvoie une `PDFDocumentVerificationInfo` contenant des informations sur toutes les signatures numériques figurant dans le document PDF.

1. Parcourir toutes les signatures

   * Parcourez toutes les signatures en obtenant la variable `PDFDocumentVerificationInfo` de `verificationInfos` membre de données. Ce membre de données renvoie une `Object` tableau où chaque élément est `PDFSignatureVerificationInfo` .
   * En utilisant la variable `PDFSignatureVerificationInfo` , vous pouvez effectuer des tâches comme déterminer l’état de la signature en obtenant l’objet `PDFSignatureVerificationInfo` de `status` membre de données. Ce membre de données renvoie une `SignatureStatus` dont le membre de données statique vous informe sur l’état de la signature. Par exemple, si la signature est inconnue, cette méthode renvoie la valeur `SignatureStatus.DocumentSignatureUnknown`.

**Voir également**

[Vérification de plusieurs signatures numériques](#unresolvedlink-lc-si)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Suppression de signatures numériques {#removing-digital-signatures}

Les signatures numériques doivent être supprimées d’un champ de signature pour qu’une signature numérique plus récente puisse être appliquée. Une signature numérique ne peut pas être remplacée. Si vous tentez d’appliquer une signature numérique à un champ de signature contenant une signature, une exception se produit.

>[!NOTE]
>
>Pour plus d’informations sur le service Signature, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-8}

Pour supprimer une signature numérique d’un champ de signature, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Signature.
1. Obtenez le document du PDF contenant une signature à supprimer.
1. Supprimez la signature numérique du champ de signature.
1. Enregistrez le document du PDF en tant que fichier de PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Signature**

Avant d’effectuer par programmation une opération du service Signature, vous devez créer un client du service Signature.

**Obtention du document du PDF contenant une signature à supprimer**

Pour supprimer une signature d’un document de PDF, vous devez obtenir un document de PDF contenant une signature.

**Supprimer la signature numérique du champ de signature**

Pour supprimer une signature numérique d’un document de PDF, vous devez indiquer le nom du champ de signature qui contient la signature numérique. Vous devez également disposer des autorisations nécessaires pour supprimer la signature numérique ; dans le cas contraire, une exception se produit.

**Enregistrer le document du PDF en tant que fichier de PDF**

Une fois que le service Signature a supprimé une signature numérique d’un champ de signature, vous pouvez enregistrer le document du PDF en tant que fichier du PDF afin que les utilisateurs puissent l’ouvrir dans Acrobat ou Adobe Reader.

**Voir également**

[Suppression des signatures numériques à l’aide de l’API Java](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-java-api)

[Suppression des signatures numériques à l’aide de l’API de service Web](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Ajout de champs de signature](digitally-signing-certifying-documents.md#adding-signature-fields)

### Suppression des signatures numériques à l’aide de l’API Java {#remove-digital-signatures-using-the-java-api}

Supprimez une signature numérique à l’aide de l’API Signature (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-signatures-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un client Signature.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `SignatureServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Obtention du document du PDF contenant une signature à supprimer

   * Créez un `java.io.FileInputStream` qui représente le document du PDF contenant la signature à supprimer à l’aide de son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Supprimer la signature numérique du champ de signature

   Supprimez une signature numérique d’un champ de signature en appelant la méthode `SignatureServiceClient` de `clearSignatureField` et transmission des valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document du PDF contenant la signature à supprimer.
   * Une valeur string qui spécifie le nom du champ de signature qui contient la signature numérique.

   Le `clearSignatureField` renvoie une `com.adobe.idp.Document` qui représente le document du PDF à partir duquel la signature numérique a été supprimée.

1. Enregistrer le document du PDF en tant que fichier de PDF

   * Créez un objet `java.io.File` et assurez-vous que l’extension du fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` . Transmettez la variable `java.io.File` pour copier le contenu de l’objet `com.adobe.idp.Document` vers le fichier . Assurez-vous d’utiliser l’objet `Document` qui a été retourné par la méthode `clearSignatureField`.

**Voir également**

[Suppression de signatures numériques](digitally-signing-certifying-documents.md#removing-digital-signatures)

[Démarrage rapide (mode SOAP) : Suppression d’une signature numérique à l’aide de l’API Java](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Suppression des signatures numériques à l’aide de l’API de service Web {#remove-digital-signatures-using-the-web-service-api}

Supprimez une signature numérique à l’aide de l’API Signature (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un client Signature

   * Créez un `SignatureServiceClient` en utilisant son constructeur par défaut.
   * Créez un `SignatureServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/SignatureService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `SignatureServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Obtention du document du PDF contenant une signature à supprimer

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document PDF contenant une signature numérique à supprimer.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF signé et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Supprimer la signature numérique du champ de signature

   Supprimez la signature numérique en appelant la méthode `SignatureServiceClient` de `clearSignatureField` et transmission des valeurs suivantes :

   * A `BLOB` contenant le document signé du PDF.
   * Une valeur string qui représente le nom du champ de signature qui contient la signature numérique à supprimer.

   Le `clearSignatureField` renvoie une `BLOB` qui représente le document du PDF à partir duquel la signature numérique a été supprimée.

1. Enregistrer le document du PDF en tant que fichier de PDF

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF contenant un champ de signature vide et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui a été renvoyé par l’objet `sign` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans le fichier du PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Suppression de signatures numériques](digitally-signing-certifying-documents.md#removing-digital-signatures)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
