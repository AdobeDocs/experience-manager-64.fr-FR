---
title: Import et export de données
seo-title: Importing and Exporting Data
description: Utilisez le service Form Data Integration pour importer des données dans un formulaire de PDF et exporter des données d’un formulaire de PDF à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Form Data Integration service to import data into a PDF form and export data from a PDF form using the Java API and Web Service API.
uuid: 94ccb6f2-6e5f-43ea-a954-9a4402871a17
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 2e783745-c986-45ba-8e65-7437d114ca38
role: Developer
exl-id: e9d10d35-6a8d-497d-83f7-67ee6c22baed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2764'
ht-degree: 6%

---

# Import et export de données {#importing-and-exporting-data}

## À propos du service d’intégration des données de formulaire {#about-the-form-data-integration-service}

Le service Form Data Integration peut importer des données dans un formulaire de PDF et exporter des données d’un formulaire de PDF. Les opérations d’import et d’export prennent en charge deux types de PDF forms :

* Un formulaire Acrobat (créé dans Acrobat) est un document PDF qui contient des champs de formulaire.
* Un formulaire XML d’Adobe (créé dans Designer) est un document de PDF conforme à l’Adobe XML Forms Architecture (XFA).

Les données de formulaire peuvent exister dans l’un des formats suivants en fonction du type de formulaire de PDF :

* Un fichier XFDF, qui constitue une version XML du format de données de formulaire Acrobat.
* Un fichier XDP, qui correspond à un fichier XML contenant des définitions de champ de formulaire. Ce fichier peut également inclure des données de champ de formulaire, ainsi qu’un fichier PDF incorporé. Un fichier XDP généré par Designer ne peut être utilisé que s’il contient un document de PDF codé en base 64.

Vous pouvez accomplir ces tâches à l’aide du service Form Data Integration :

* Importez des données dans les PDF forms. Pour plus d’informations, voir [Importation de données de formulaire](importing-exporting-data.md#importing-form-data).
* Exporter des données à partir de PDF forms. Pour plus d’informations, voir [Exportation des données de formulaire](importing-exporting-data.md#exporting-form-data).

>[!NOTE]
>
>Pour plus d’informations sur le service Form Data Integration, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Importation de données de formulaire {#importing-form-data}

Vous pouvez importer des données de formulaire dans des PDF forms interactifs à l’aide du service Form Data Integration . Un formulaire de PDF interactif est un document de PDF qui contient un ou plusieurs champs permettant de collecter des informations d’un utilisateur ou d’afficher des informations personnalisées. Le service Form Data Integration ne prend pas en charge les calculs de formulaire, la validation ou les scripts.

Pour importer des données dans un formulaire créé dans Designer, vous devez référencer une source de données XML XDP valide. Examinez l’exemple de formulaire de demande de prêt immobilier suivant.

![ie_ie_loanformdata](assets/ie_ie_loanformdata.png)

Pour importer des valeurs de données dans ce formulaire, vous devez disposer d’une source de données XML XDP valide correspondant au formulaire. Vous ne pouvez pas utiliser une source de données XML arbitraire pour importer des données dans un formulaire à l’aide du service Form Data Integration. La différence entre une source de données XML arbitraire et une source de données XML XDP est qu’une source de données XDP est conforme à l’architecture Forms XML (XFA). Le code XML suivant représente une source de données XDP XML qui correspond à l’exemple de formulaire de demande de prêt immobilier.

```as3
 <?xml version="1.0" encoding="UTF-8" ?>  
 - <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"> 
 - <xfa:data> 
 - <data> 
     - <Layer> 
         <closeDate>1/26/2007</closeDate>  
         <lastName>Johnson</lastName>  
         <firstName>Jerry</firstName>  
         <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>  
         <city>New York</city>  
         <zipCode>00501</zipCode>  
         <state>NY</state>  
         <dateBirth>26/08/1973</dateBirth>  
         <middleInitials>D</middleInitials>  
         <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>  
         <phoneNumber>5555550000</phoneNumber>  
     </Layer> 
     - <Mortgage> 
         <mortgageAmount>295000.00</mortgageAmount>  
         <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>  
         <purchasePrice>300000</purchasePrice>  
         <downPayment>5000</downPayment>  
         <term>25</term>  
         <interestRate>5.00</interestRate>  
     </Mortgage> 
 </data> 
 </xfa:data> 
 </xfa:datasets>
```

>[!NOTE]
>
>Pour plus d’informations sur le service Form Data Integration, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour importer des données de formulaire dans un formulaire PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client de service Form Data Integration.
1. Référencez un formulaire de PDF.
1. Référencez une source de données XML.
1. Importez des données dans le formulaire du PDF.
1. Enregistrez le formulaire du PDF en tant que fichier du PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utility.jar (Obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (requis si AEM Forms est déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client de service Form Data Integration**

Avant de pouvoir importer des données par programmation dans une API client de formulaire PDF, vous devez créer un client de service d’intégration de données. Lors de la création d’un client de service, vous définissez les paramètres de connexion requis pour appeler un service. Pour plus d’informations, voir [Définition des propriétés de connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Référencer un formulaire de PDF**

Pour importer des données dans un formulaire PDF, vous devez référencer un formulaire XML créé dans Designer ou un formulaire Acrobat créé dans Acrobat.

**Référence à une source de données XML**

Pour importer des données de formulaire, vous devez référencer une source de données valide. Pour importer des données dans un formulaire XML XFA créé dans Designer, vous devez utiliser une source de données XML XDP. Si vous référencez un formulaire Acrobat, vous devez utiliser une source de données XFDF. Pour chaque champ dans lequel vous souhaitez importer des données, une valeur doit être spécifiée. Si un élément situé dans la source de données XML ne correspond pas à un champ du formulaire, l’élément est ignoré.

**Importer des données dans le formulaire du PDF**

Après avoir référencé un formulaire de PDF et une source de données XML valide, vous pouvez importer les données dans le formulaire de PDF.

**Enregistrer le formulaire du PDF en tant que fichier de PDF**

Après avoir importé des données dans un formulaire, vous pouvez enregistrer le formulaire en tant que fichier de PDF. Une fois enregistré en tant que fichier de PDF, l’utilisateur peut ouvrir le formulaire dans Adobe Reader ou Acrobat et l’afficher avec les données importées.

**Voir également**

[Importation des données de formulaire à l’aide de l’API Java](importing-exporting-data.md#import-form-data-using-the-java-api)

[Importation de données de formulaire à l’aide de l’API de service Web](importing-exporting-data.md#import-form-data-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API du service d’intégration des données de formulaire](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Exportation des données de formulaire](importing-exporting-data.md#exporting-form-data)

### Importation des données de formulaire à l’aide de l’API Java {#import-form-data-using-the-java-api}

Importez des données de formulaire à l’aide de l’API Form Data Integration (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-formdataintegration-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un client de service Form Data Integration.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `FormDataIntegrationClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Référencez un formulaire de PDF.

   * Créez un objet `java.io.FileInputStream` en utilisant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du formulaire du PDF.
   * Créez un `com.adobe.idp.Document` qui stocke le formulaire du PDF à l’aide de l’objet `com.adobe.idp.Document` constructeur. Transmettez la variable `java.io.FileInputStream` qui contient le formulaire du PDF au constructeur.

1. Référencez une source de données XML.

   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier XML contenant les données à importer dans le formulaire.
   * Créez un `com.adobe.idp.Document` qui stocke les données de formulaire à l’aide de l’objet `com.adobe.idp.Document` constructeur. Transmettez la variable `java.io.FileInputStream` contenant des données de formulaire au constructeur.

1. Importez des données dans le formulaire du PDF.

   Importez des données dans un formulaire PDF en appelant le `FormDataIntegrationClient` de `importData` et transmission des valeurs suivantes :

   * Le `com.adobe.idp.Document` qui stocke le formulaire du PDF.
   * Le `com.adobe.idp.Document` qui stocke les données de formulaire.

   Le `importData` renvoie une `com.adobe.idp.Document` qui stocke un formulaire de PDF contenant les données situées dans la source de données XML.

1. Enregistrez le formulaire du PDF en tant que fichier du PDF.

   * Créez un `java.io.File` et assurez-vous que l’extension de fichier est &quot;.PDF&quot;.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `importData` ).

**Voir également**

[Résumé des étapes](importing-exporting-data.md#summary-of-steps)

[Démarrage rapide (mode SOAP) : Importation de données de formulaire à l’aide de l’API Java](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importation de données de formulaire à l’aide de l’API de service Web {#import-form-data-using-the-web-service-api}

Importez des données de formulaire à l’aide de l’API Form Data Integration (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client de service Form Data Integration.

   * Créez un `FormDataIntegrationClient` en utilisant son constructeur par défaut.
   * Créez un `FormDataIntegrationClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `FormDataIntegrationClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `FormDataIntegrationClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `FormDataIntegrationClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez un formulaire de PDF.

   * Créez un objet `BLOB` en utilisant son constructeur. Ceci `BLOB` sert à stocker le formulaire du PDF.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du formulaire du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Référencez une source de données XML.

   * Créez un objet `BLOB` en utilisant son constructeur. Ceci `BLOB` sert à stocker les données importées dans le formulaire.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du fichier XML contenant les données à importer et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Importez des données dans le formulaire du PDF.

   Importez des données dans le formulaire du PDF en appelant la méthode `FormDataIntegrationClient` de `importData` et transmission des valeurs suivantes :

   * Le `BLOB` qui stocke le formulaire du PDF.
   * Le `BLOB` qui stocke les données de formulaire.

   Le `importData` renvoie une `BLOB` qui stocke un formulaire de PDF contenant les données situées dans la source de données XML.

1. Enregistrez le formulaire du PDF en tant que fichier du PDF.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du PDF.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `importData` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](importing-exporting-data.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Exportation des données de formulaire {#exporting-form-data}

Vous pouvez exporter des données de formulaire à partir d’un formulaire de PDF interactif à l’aide du service Form Data Integration. Le format des données exportées dépend du type de formulaire. Si le type de formulaire est un formulaire Acrobat créé dans Acrobat, les données exportées sont XFDF. Si le type de formulaire est un formulaire XML qui a été créé dans Designer, les données exportées sont XDP.

>[!NOTE]
>
>Pour plus d’informations sur le service Form Data Integration, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-1}

Pour exporter les données d’un formulaire PDF, procédez comme suit :

1. Inclure les fichiers de projet
1. Créez un client de service Form Data Integration.
1. Référencez un formulaire de PDF.
1. Exportez les données du formulaire du PDF.
1. Enregistrez les données exportées sous forme de fichier XML.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utility.jar (Obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (requis si AEM Forms est déployé sur JBoss)

**Création d’un client de service Form Data Integration**

Avant de pouvoir importer des données par programmation dans une API formClient de PDF, vous devez créer un client de service d’intégration de données. Lors de la création d’un client de service, vous définissez les paramètres de connexion requis pour appeler un service. Pour plus d’informations, [Définition des propriétés de connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Référencer un formulaire de PDF**

Pour exporter des données d’un formulaire de PDF, vous devez référencer un formulaire de PDF créé dans Designer ou Acrobat et contenant des données de formulaire. Si vous tentez d’exporter des données à partir d’un formulaire de PDF vide, vous obtiendrez un schéma XML vide.

**Exporter les données du formulaire du PDF**

Après avoir référencé un formulaire de PDF contenant des données de formulaire, vous pouvez exporter les données du formulaire. Les données sont exportées dans un schéma XML basé sur le formulaire.

**Enregistrer les données du formulaire sous forme de fichier XML**

Une fois les données de formulaire exportées, vous pouvez les enregistrer au format XML. Une fois enregistré en tant que fichier XML, vous pouvez ouvrir le fichier XML dans une visionneuse XML pour afficher les données de formulaire.

**Voir également**

[Exportation des données de formulaire à l’aide de l’API Java](importing-exporting-data.md#export-form-data-using-the-java-api)

[Exportation des données de formulaire à l’aide de l’API de service Web](importing-exporting-data.md#export-form-data-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API du service d’intégration des données de formulaire](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Importation de données de formulaire](importing-exporting-data.md#importing-form-data)

### Exportation des données de formulaire à l’aide de l’API Java {#export-form-data-using-the-java-api}

Exportez les données de formulaire à l’aide de l’API Form Data Integration (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-formdataintegration-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un client de service Form Data Integration.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `FormDataIntegrationClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Référencez un formulaire de PDF.

   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du formulaire PDF contenant les données à exporter.
   * Créez un `com.adobe.idp.Document` qui stocke le formulaire du PDF à l’aide de l’objet `com.adobe.idp.Document` constructeur. Transmettez la variable `java.io.FileInputStream` qui contient le formulaire du PDF au constructeur.

1. Exportez les données du formulaire du PDF.

   Exporter des données de formulaire en appelant le `FormDataIntegrationClient` de `exportData` et transmettez la méthode `com.adobe.idp.Document` qui stocke le formulaire du PDF. Cette méthode renvoie une `com.adobe.idp.Document` qui stocke les données de formulaire sous la forme d’un schéma XML.

1. Enregistrez le formulaire du PDF en tant que fichier du PDF.

   * Créez un `java.io.File` et assurez-vous que l’extension de fichier est XML.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `exportData` ).

**Voir également**

[Résumé des étapes](importing-exporting-data.md#summary-of-steps)

[Démarrage rapide (mode SOAP) : Exportation des données de formulaire à l’aide de l’API Java](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportation des données de formulaire à l’aide de l’API de service Web {#export-form-data-using-the-web-service-api}

Exportez les données de formulaire à l’aide de l’API Form Data Integration (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   * Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client de service Form Data Integration.

   * Créez un `FormDataIntegrationClient` en utilisant son constructeur par défaut.
   * Créez un `FormDataIntegrationClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `FormDataIntegrationClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `FormDataIntegrationClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `FormDataIntegrationClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez un formulaire de PDF.

   * Créez un objet `BLOB` en utilisant son constructeur. Ceci `BLOB` sert à stocker le formulaire du PDF à partir duquel les données sont exportées.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du formulaire du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Exportez les données du formulaire du PDF.

   Importez des données dans un formulaire PDF en appelant le `FormDataIntegrationClient` de `exportData` et transmettez la méthode `BLOB` qui stocke le formulaire du PDF. Cette méthode renvoie une `BLOB` qui stocke les données de formulaire sous la forme d’un schéma XML.

1. Enregistrez le formulaire du PDF en tant que fichier du PDF.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier XML.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `exportData` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier XML en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](importing-exporting-data.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
