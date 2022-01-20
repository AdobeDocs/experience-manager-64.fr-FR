---
title: Conversion de PDF en fichiers Postscript et Image
seo-title: Converting PDF to Postscript andImage Files
description: Utilisez le service Convert PDF pour convertir des documents PDF au format PostScript et dans plusieurs formats d’image (JPEG, JPEG 2000, PNG et TIFF) à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Convert PDF service to convert PDF documents to PostScript and to a number of image formats (JPEG, JPEG 2000, PNG, and TIFF) using the Java API and Web Service API.
uuid: 07da0391-7180-4197-aaa6-ae753d753b84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: f8707752-2c83-461a-b83d-708754b0f3f6
role: Developer
exl-id: 4afed537-1694-4187-8968-608f49116c2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2795'
ht-degree: 6%

---

# Conversion de PDF en fichiers Postscript et image {#converting-pdf-to-postscript-andimage-files}

**À propos du service de conversion de PDF**

Le service Convert PDF convertit les documents du PDF au format PostScript et dans divers formats d’image (JPEG, JPEG 2000, PNG et TIFF). La conversion d’un document PDF en PostScript est utile pour les impressions sans assistance reposant sur un serveur exécutées sur n’importe quelle imprimante PostScript. La conversion d’un document PDF en fichier TIFF comportant plusieurs pages est pratique lors de l’archivage de documents dans des systèmes de gestion de contenu qui ne prennent pas en charge les documents PDF.

Vous pouvez accomplir ces tâches à l’aide du service Convert PDF :

* Convertir des documents PDF en PostScript.
* Convertissez des documents PDF en formats d’image.

   >[!NOTE]
   >
   >Pour plus d’informations sur le service Convert PDF, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Conversion de documents PDF en PostScript {#converting-pdf-documents-to-postscript}

Cette rubrique décrit comment utiliser l’API Convert PDF Service (Java et service Web) pour convertir des documents PDF par programmation en fichiers PostScript. Le document du PDF converti en fichier PostScript doit être un document du PDF non interactif. En d’autres termes, si vous tentez de convertir un document de PDF interactif en fichier PostScript, une exception est générée.

>[!NOTE]
>
>Pour plus d’informations sur le service Convert PDF, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour convertir un document PDF en fichier PostScript, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client de service Convert PDF.
1. Référencez le document du PDF à convertir en fichier PostScript.
1. Définissez les options d’exécution de conversion.
1. Convertissez le document du PDF en fichier PostScript.
1. Enregistrez le fichier PostScript.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un client de PDF Convert**

Avant d’effectuer par programmation une opération de service Convert PDF, vous devez créer un client de service Convert PDF. Si vous utilisez l’API Java, créez une `ConvertPdfServiceClient` . Si vous utilisez l’API de service Web, créez une `ConvertPDFServiceService` .

Cette section utilise la fonctionnalité de service Web introduite dans AEM Forms. Pour accéder à la nouvelle fonctionnalité, vous devez construire votre objet proxy à l’aide de la fonction `lc_version` attribut. (Voir &quot;Accès aux nouvelles fonctionnalités à l’aide des services web&quot; dans [Appel d’AEM Forms à l’aide de services web](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

**Référencez le document du PDF à convertir en fichier PostScript.**

Référencez le document du PDF que vous souhaitez convertir en fichier PostScript. Comme indiqué précédemment dans cette rubrique, le document du PDF doit être un document du PDF non interactif. Si vous tentez de convertir un document de PDF interactif en fichier PostScript, une exception est générée.

**Définition des options d’exécution de conversion**

Lors de la conversion d’un document de PDF en fichier PostScript, vous pouvez définir des options d’exécution spécifiant le type PostScript créé. Vous pouvez par exemple définir un fichier PostScript de niveau 3.

En règle générale, le fichier PostScript généré reflète la taille du document du PDF d’entrée. Si vous sélectionnez la variable `ShrinkToFit` (qui réduit la sortie du fichier PostScript pour l’adapter à la page), vous ne verrez aucune différence entre le document du PDF d’entrée et le fichier PostScript généré. Le `ShrinkToFit` ne prend effet que si vous choisissez d’imprimer sur une page plus petite que le document du PDF d’entrée. Pour sélectionner une taille de page réduite, définissez la variable `PageSize` . En outre, il est recommandé de définir la variable `RotateAndCenter` option à `true` pour obtenir la sortie PostScript correcte.

De même, si vous sélectionnez l’option `ExpandToFit` (qui adapte la sortie du fichier PostScript à la page), cette option n’est prise en compte que si vous choisissez d’imprimer sur une page plus grande que le document du PDF d’entrée. Pour sélectionner une taille de page plus importante, définissez la variable `PageSize` . En outre, il est recommandé de définir la variable `RotateAndCenter` option à `true` pour obtenir la sortie PostScript correcte.

>[!NOTE]
>
>Pour plus d’informations sur les valeurs d’exécution que vous pouvez définir, voir `ToPSOptionsSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Convertir le document du PDF en fichier PostScript**

Après avoir créé le client de service et défini les options d’exécution, vous pouvez appeler l’opération de conversion PostScript. Cette opération nécessite des informations sur le document à convertir, y compris le niveau PostScript préféré pour le document cible.

**Enregistrement du fichier PostScript**

Après avoir converti le document du PDF en PostScript, vous pouvez enregistrer la sortie en tant que fichier PostScript.

**Voir également**

[Convertir un document de PDF en PS à l’aide de l’API Java](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Convertir un document de PDF en PS à l’aide de l’API de service Web](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Convert PDF Service](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Convertir un document de PDF en PS à l’aide de l’API Java {#convert-a-pdf-document-to-ps-using-the-java-api}

Convertissez un document de PDF en PostScript à l’aide de l’API Convert PDF Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-convertpdf-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un client de PDF Convert.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `ConvertPdfServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Référencez le document du PDF à convertir en fichier PostScript.

   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF à convertir.
   * Créez un `com.adobe.idp.Document` qui stocke le document du PDF à l’aide de l’objet `com.adobe.idp.Document` constructeur. Transmettez la variable `java.io.FileInputStream` contenant le document du PDF.

1. Définissez les options d’exécution de conversion.

   * Créez un `ToPSOptionsSpec` en appelant son constructeur.
   * Définissez les options d’exécution en appelant une méthode appropriée appartenant à la variable `ToPSOptionsSpec` . Par exemple, pour définir le niveau PostScript créé, appelez la méthode `ToPSOptionsSpec` de `setPsLevel` et transmettre une `PSLevel` valeur d’énumération spécifiant le niveau PostScript. Pour plus d’informations sur toutes les valeurs d’exécution que vous pouvez définir, voir `ToPSOptionsSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Convertissez le document du PDF en fichier PostScript.

   Appeler la variable `ConvertPdfServiceClient`de `toPS2` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document du PDF à convertir en fichier PostScript.
   * A `ToPSOptionsSpec` qui spécifie les options d’exécution PostScript.

   Le `toPS2` renvoie une `Document` contenant le nouveau document PostScript.

1. Enregistrez le fichier PostScript.

   * Créez un `java.io.File` et assurez-vous que l’extension de nom de fichier est .ps.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `toPS2` ).

**Voir également**

[Résumé des étapes](converting-pdf-postscript-image-files.md#summary-of-steps)

[Démarrage rapide (mode SOAP) : Conversion d’un document de PDF en PostScript à l’aide de l’API Java](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertir un document de PDF en PS à l’aide de l’API de service Web {#convert-a-pdf-document-to-ps-using-the-web-service-api}

Convertissez un document de PDF en PostScript à l’aide de l’API Convert PDF Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client de PDF Convert.

   * Créez un `ConvertPdfServiceClient` en utilisant son constructeur par défaut.
   * Créez un `ConvertPdfServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Toutefois, spécifiez `?blob=mtom`.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `ConvertPdfServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `ConvertPdfServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `ConvertPdfServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez le document du PDF à convertir en fichier PostScript.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document PDF converti en fichier PostScript.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF à convertir et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution de conversion.

   * Créez un `ToPSOptionsSpec` en appelant son constructeur.
   * Définissez les options d’exécution en attribuant une valeur à la variable `ToPSOptionsSpec` membre de données de l’objet. Par exemple, pour définir le niveau PostScript créé, affectez une `PSLevel` de la valeur de l’énumération `ToPSOptionsSpec` de `psLevel` membre de données.

1. Convertissez le document du PDF en fichier PostScript.

   Appeler la variable `GeneratePDFServiceService` de `toPS2` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document du PDF à convertir en fichier PostScript.
   * A `ToPSOptionsSpec` qui spécifie les options d’exécution

   Une fois la conversion terminée, extrayez les données binaires représentant le document PostScript en y accédant. `BLOB` de `MTOM` . Cette opération renvoie un tableau d’octets que vous pouvez écrire dans un fichier PostScript.

1. Enregistrez le fichier PostScript.

   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier PS.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `encryptPDFUsingPassword` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans le fichier PostScript en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](converting-pdf-postscript-image-files.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Conversion de documents PDF au format d’image {#converting-pdf-documents-to-image-formats}

Vous pouvez utiliser le service Convert PDF pour convertir par programmation des documents PDF en formats d’image, notamment JPEG, JPEG 2000, TIFF et PNG. En convertissant un document de PDF en fichier image, vous pouvez utiliser le document de PDF comme fichier image. Par exemple, vous pouvez placer l’image dans un système de gestion de contenu d’entreprise à des fins de stockage.

Lors de la conversion d’un document PDF en image, le service Convert PDF crée une image distincte pour chaque page du document. En d’autres termes, si le document comporte 20 pages, le service Convert PDF crée 20 fichiers image. Lors de la conversion d’un document PDF au format d’image, vous pouvez créer des images individuelles pour chaque page dans le document du PDF ou un seul fichier image pour l’ensemble du document du PDF.

>[!NOTE]
>
>Pour plus d’informations sur le service Convert PDF, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-1}

Pour convertir un document de PDF en l’un des types pris en charge, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client de service Convert PDF.
1. Récupérez le document du PDF à convertir.
1. Définissez les options d’exécution.
1. Convertissez le PDF en image.
1. Récupérez les fichiers image d’une collection.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un client de PDF Convert**

Avant d’effectuer par programmation une opération de service Convert PDF, vous devez créer un client de service Convert PDF. Si vous utilisez l’API Java, créez une `ConvertPdfServiceClient` . Si vous utilisez l’API de service Web, créez une `ConvertPDFServiceService` .

**Récupération du document du PDF à convertir**

Vous devez récupérer le document du PDF à convertir en image. Vous ne pouvez pas convertir un document de PDF interactif en image. Si vous tentez de le faire, une exception est générée. Pour convertir un document de PDF interactif en fichier image, vous devez aplatir le document du PDF avant de le convertir. (Voir [Aplatissement de documents PDF](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents).)

**Définition des options d’exécution**

Vous devez définir les options d’exécution, telles que le format de l’image et les valeurs de résolution. Pour plus d’informations sur les valeurs d’exécution, voir `ToImageOptionsSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Convertir le PDF en image**

Après avoir créé le client de service et défini les options d’exécution, vous pouvez convertir le document du PDF en image. Un objet de collection contenant les images est renvoyé.

**Récupération des fichiers image d’une collection**

Vous pouvez récupérer des fichiers image à partir d’un objet de collection renvoyé par le service Convert PDF. Chaque élément de la collection est une `com.adobe.idp.Document` (ou une `BLOB` si vous utilisez des services web) que vous pouvez enregistrer en tant que fichier image (fichier de JPG, par exemple.

Le format du fichier image dépend de la variable `ImageConvertFormat` option d’exécution. En d’autres termes, si vous définissez la variable `ImageConvertFormat` option d’exécution sur `ImageConvertFormat.JPEG`, vous pouvez enregistrer des fichiers image en tant que fichiers JPG.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Convert PDF Service](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Convertir un document de PDF en fichiers image à l’aide de l’API Java {#convert-a-pdf-document-to-image-files-using-the-java-api}

Convertir un document de PDF en format d’image à l’aide de l’API Convert PDF service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-convertpdf-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un client de PDF Convert.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `ConvertPdfServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez le document du PDF à convertir.

   * Créez un `java.io.FileInputStream` qui représente le document du PDF à convertir en utilisant son constructeur et en transmettant une valeur string spécifiant l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définissez les options d’exécution.

   * Créez un objet `ToImageOptionsSpec` en utilisant son constructeur.
   * Appelez les méthodes qui appartiennent à cet objet selon les besoins. Par exemple, définissez le type d’image en appelant la fonction `setImageConvertFormat` méthode et transmission d’une `ImageConvertFormat` valeur enum qui spécifie le type de format.

   >[!NOTE]
   >
   >La définition de la variable `ImageConvertFormat` la valeur de l&#39;énumération est obligatoire.

1. Convertissez le PDF en image.

   Appeler la variable `ConvertPdfServiceClient` de `toImage2` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le fichier de PDF à convertir.
   * A `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec` contenant les différentes préférences concernant le format d’image cible.

   Le `toImage2` renvoie une `java.util.List` contenant des images. Chaque élément de la collection est une `com.adobe.idp.Document` instance.

1. Récupérez les fichiers image d’une collection.

   Effectuez une itération à l’aide du `java.util.List` pour déterminer si des images sont présentes. Chaque élément est une `com.adobe.idp.Document` instance. Enregistrez l’image en appelant la fonction `com.adobe.idp.Document` de `copyToFile` et transmission d’une `java.io.File` .

**Voir également**

[Démarrage rapide (mode SOAP) : Conversion d’un document de PDF en fichiers de JPEG à l’aide de l’API Java](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Convertir un document de PDF en fichiers image à l’aide de l’API de service Web {#convert-a-pdf-document-to-image-files-using-the-web-service-api}

Convertir un document PDF en format d’image à l’aide de l’API Convert PDF Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client de PDF convert.

   * Créez un `ConvertPdfServiceClient` en utilisant son constructeur par défaut.
   * Créez un `ConvertPdfServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Toutefois, spécifiez `?blob=mtom`.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `ConvertPdfServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `ConvertPdfServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `ConvertPdfServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Récupérez le document du PDF à convertir.

   * Créez un objet `BLOB` en utilisant son constructeur. Ceci `BLOB` sert à stocker le formulaire du PDF.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du formulaire du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Déterminez la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution.

   * Créez un objet `ToImageOptionsSpec` en utilisant son constructeur.
   * Appelez les méthodes qui appartiennent à cet objet selon les besoins. Par exemple, définissez le type d’image en appelant la fonction `setImageConvertFormat` méthode et transmission d’une `ImageConvertFormat` valeur d’énumération spécifiant le type de format.

   >[!NOTE]
   >
   >La définition de la variable `ImageConvertFormat` la valeur de l&#39;énumération est obligatoire.

1. Convertissez le PDF en image.

   Appeler la variable `ConvertPDFServiceService` de `toImage2` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le fichier à convertir
   * A `ToImageOptionsSpec` contenant les différentes préférences concernant le format d’image cible

   Le `toImage2` renvoie une `MyArrayOfBLOB` contenant les fichiers image nouvellement créés.

1. Récupérez les fichiers image d’une collection.

   * Déterminer le nombre d’éléments dans la variable `MyArrayOfBLOB` en obtenant la valeur de son objet `Count` champ . Chaque élément est une `BLOB` contenant l’image.
   * Effectuez une itération à l’aide du `MyArrayOfBLOB` et enregistrez chaque fichier image.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
