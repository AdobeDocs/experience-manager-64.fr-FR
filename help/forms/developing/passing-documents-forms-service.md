---
title: Transmission de documents à FormsService
seo-title: Passing Documents to the FormsService
description: Transmettez au service Forms un objet com.adobe.idp.Document contenant la conception de formulaire. Le service Forms effectue le rendu de la conception de formulaire située dans l’objet com.adobe.idp.Document .
seo-description: Pass a com.adobe.idp.Document object that contains the form design to the Forms service. The Forms service renders the form design located in the com.adobe.idp.Document object.
uuid: 841e97f3-ebb8-4340-81a9-b6db11f0ec82
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: e23de3c3-f8a0-459f-801e-a0942fb1c6aa
role: Developer
exl-id: fe19e9b3-d662-4df2-b372-5006b794cde8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1670'
ht-degree: 3%

---

# Transmission de documents au service Forms {#passing-documents-to-the-formsservice}

Le service AEM Forms effectue le rendu de PDF forms interactifs sur les appareils clients, généralement les navigateurs Web, afin de collecter des informations auprès des utilisateurs. Un formulaire de PDF interactif est basé sur une conception de formulaire généralement enregistrée en tant que fichier XDP et créée dans Designer. À partir d’AEM Forms, vous pouvez transmettre une `com.adobe.idp.Document` contenant la conception de formulaire pour le service Forms. Le service Forms effectue ensuite le rendu de la conception de formulaire située dans l’objet `com.adobe.idp.Document` .

L’avantage de transmettre une variable `com.adobe.idp.Document` le service Forms indique que d’autres opérations de service renvoient un `com.adobe.idp.Document` instance. C&#39;est-à-dire que vous pouvez obtenir une `com.adobe.idp.Document` à partir d’une autre opération de service et d’en effectuer le rendu. Supposons, par exemple, qu’un fichier XDP soit stocké dans un noeud Content Services (obsolète) nommé `/Company Home/Form Designs`, comme illustré ci-dessous.

Vous pouvez récupérer Loan.xdp par programmation à partir de Content Services (obsolète) (obsolète) et transmettre le fichier XDP au service Forms dans une `com.adobe.idp.Document` .

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Résumé des étapes {#summary-of-steps}

Pour transmettre un document obtenu à partir de Content Services (obsolète) au service Forms, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un objet Forms et un objet API Client de Document Management.
1. Récupérez la conception de formulaire auprès de Content Services (obsolète).
1. Générer le formulaire de PDF interactif.
1. Exécutez une action avec le flux de données de formulaire.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, incluez les fichiers proxy.

**Création d’un objet API Forms et client Document Management**

Avant d’effectuer par programmation une opération d’API de service Forms, créez un objet API client Forms. En outre, comme ce workflow récupère un fichier XDP de Content Services (obsolète), créez un objet API Document Management.

**Récupération de la conception de formulaire auprès de Content Services (obsolète)**

Récupérez le fichier XDP à partir de Content Services (obsolète) à l’aide de l’API Java ou de service Web. Le fichier XDP est renvoyé dans un `com.adobe.idp.Document` (ou une `BLOB` si vous utilisez des services web). Vous pouvez ensuite transmettre la variable `com.adobe.idp.Document` au service Forms.

**Rendu d’un formulaire de PDF interactif**

Pour effectuer le rendu d’un formulaire interactif, transmettez la variable `com.adobe.idp.Document` instance renvoyée par Content Services (obsolète) au service Forms.

>[!NOTE]
>
>Vous pouvez transmettre une `com.adobe.idp.Document` qui contient la conception de formulaire au service Forms. Deux nouvelles méthodes nommées `renderPDFForm2` et `renderHTMLForm2` accepter un `com.adobe.idp.Document` contenant une conception de formulaire.

**Exécution d’une action avec le flux de données de formulaire**

Selon le type d’application cliente, vous pouvez écrire le formulaire dans un navigateur Web client ou l’enregistrer en tant que fichier PDF. En règle générale, une application web écrit le formulaire dans un navigateur web. Cependant, une application de bureau enregistre généralement le formulaire sous la forme d’un fichier de PDF.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Transmission de documents au service Forms à l’aide de l’API Java {#pass-documents-to-the-forms-service-using-the-java-api}

Transmettez un document obtenu à partir de Content Services (obsolète) à l’aide du service Forms et de l’API Content Services (obsolète) (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar et adobe-contentservices-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API Forms et client Document Management

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion. (Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Créez un `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .
   * Créez un objet `DocumentManagementServiceClientImpl` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupération de la conception de formulaire auprès de Content Services (obsolète)

   Appeler la variable `DocumentManagementServiceClientImpl` de `retrieveContent` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le magasin où le contenu est ajouté. Le magasin par défaut est `SpacesStore`. Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie le chemin d’accès complet du contenu à récupérer (par exemple, `/Company Home/Form Designs/Loan.xdp`). Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie la version. Cette valeur est un paramètre facultatif et vous pouvez transmettre une chaîne vide. Dans ce cas, la dernière version est récupérée.

   Le `retrieveContent` renvoie une `CRCResult` contenant le fichier XDP. Obtention d’un `com.adobe.idp.Document` en appelant la méthode `CRCResult` de `getDocument` .

1. Rendu d’un formulaire de PDF interactif

   Appeler la variable `FormsServiceClient` de `renderPDFForm2` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` contenant la conception de formulaire récupérée dans Content Services (obsolète).
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * A `PDFFormRenderSpec` qui stocke les options d’exécution. Cette valeur est un paramètre facultatif. Vous pouvez spécifier `null` si vous ne souhaitez pas spécifier d’options d’exécution.
   * A `URLSpec` contenant des valeurs URI. Cette valeur est un paramètre facultatif. Vous pouvez spécifier `null`.
   * A `java.util.HashMap` qui stocke les pièces jointes. Cette valeur est un paramètre facultatif. Vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

   Le `renderPDFForm` renvoie une `FormsResult` contenant un flux de données de formulaire qui doit être écrit dans le navigateur Web client.

1. Exécution d’une action avec le flux de données de formulaire

   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Obtention du type de contenu de la variable `com.adobe.idp.Document` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `com.adobe.idp.Document` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets et renseignez-le avec le flux de données de formulaire en appelant la fonction `InputStream` de `read` . Transmettez le tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Démarrage rapide (mode SOAP) : Transmission de documents au service Forms à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Transmission de documents au service Forms à l’aide de l’API de service Web {#pass-documents-to-the-forms-service-using-the-web-service-api}

Transmettez un document obtenu à partir de Content Services (obsolète) à l’aide du service Forms et de l’API Content Services (obsolète) (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Comme cette application cliente appelle deux services AEM Forms, créez deux références de service. Utilisez la définition WSDL suivante pour la référence de service associée au service Forms : `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Utilisez la définition WSDL suivante pour la référence de service associée au service Document Management : `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Parce que la variable `BLOB` Le type de données est commun aux deux références de service. Il qualifie entièrement la variable `BLOB` type de données lors de son utilisation. Dans le démarrage rapide du service Web correspondant, tous les `BLOB` les instances sont entièrement qualifiées.

   >[!NOTE]
   >
   >Remplacer `localhost`* avec l’adresse IP du serveur hébergeant AEM Forms. *

1. Création d’un objet API Forms et client Document Management

   * Créez un `FormsServiceClient` en utilisant son constructeur par défaut.
   * Créez un `FormsServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/FormsService?WSDL`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `FormsServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `FormsServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `FormsServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Répétez ces étapes pour le `DocumentManagementServiceClient`* client de service. *

1. Récupération de la conception de formulaire auprès de Content Services (obsolète)

   Récupération du contenu en appelant la méthode `DocumentManagementServiceClient` de `retrieveContent` et transmission des valeurs suivantes :

   * Une valeur string qui spécifie le magasin où le contenu est ajouté. Le magasin par défaut est `SpacesStore`. Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie le chemin d’accès complet du contenu à récupérer (par exemple, `/Company Home/Form Designs/Loan.xdp`). Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie la version. Cette valeur est un paramètre facultatif et vous pouvez transmettre une chaîne vide. Dans ce cas, la dernière version est récupérée.
   * Un paramètre de sortie string qui stocke la valeur du lien de navigation.
   * A `BLOB` paramètre de sortie qui stocke le contenu. Vous pouvez utiliser ce paramètre de sortie pour récupérer le contenu.
   * A `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` paramètre de sortie qui stocke les attributs de contenu.
   * A `CRCResult` paramètre de sortie. Au lieu d’utiliser cet objet, vous pouvez utiliser la variable `BLOB` paramètre de sortie pour obtenir le contenu.

1. Rendu d’un formulaire de PDF interactif

   Appeler la variable `FormsServiceClient` de `renderPDFForm2` et transmettez les valeurs suivantes :

   * A `BLOB` contenant la conception de formulaire récupérée dans Content Services (obsolète).
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `BLOB` .
   * A `PDFFormRenderSpec` qui stocke les options d’exécution. Cette valeur est un paramètre facultatif. Vous pouvez spécifier `null` si vous ne souhaitez pas spécifier d’options d’exécution.
   * A `URLSpec` contenant des valeurs URI. Cette valeur est un paramètre facultatif. Vous pouvez spécifier `null`.
   * A `Map` qui stocke les pièces jointes. Cette valeur est un paramètre facultatif. Vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.
   * Un paramètre de sortie long utilisé pour stocker le nombre de pages.
   * Paramètre de sortie string utilisé pour stocker la valeur du paramètre régional.
   * A `FormsResult` paramètre de sortie utilisé pour stocker le formulaire de PDF interactif `.`

   Le `renderPDFForm2` renvoie une `FormsResult` contenant le formulaire de PDF interactif.

1. Exécution d’une action avec le flux de données de formulaire

   * Créez un `BLOB` qui contient des données de formulaire en obtenant la valeur de la propriété `FormsResult` de `outputContent` champ .
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF interactif et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` récupéré à partir de l’objet `FormsResult` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
