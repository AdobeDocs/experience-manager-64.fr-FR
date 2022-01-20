---
title: 'Création de flux de sortie de document '
seo-title: Creating Document Output Streams
description: Utilisez le service Output pour convertir des documents en PDF (y compris des documents PDF/A), PostScript, PCL (Printer Control Language) et Zebra - ZPL, Intermec - IPL, Datamax - DPL et TecToshiba - TPCL .
seo-description: Use the Output service to convert documents as PDF (including PDF/A documents), PostScript, Printer Control Language (PCL), and Zebra - ZPL, Intermec - IPL, Datamax - DPL, and TecToshiba - TPCL label formats.
uuid: 80c28efa-35ce-4073-9ca6-2d93bcd67fdd
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: de527d50-991b-4ca3-a8ac-44d5cab988e9
role: Developer
exl-id: 31f60907-0b9c-43ac-bb9f-74eacf6976d7
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 5%

---

# Création de flux de sortie de document  {#creating-document-output-streams}

**À propos du service Output**

Le service Output vous permet de générer des documents en tant que PDF (y compris des documents PDF/A), PostScript, PCL (Printer Control Language), ainsi que les formats d’étiquettes suivants :

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Le service Output vous permet de fusionner des données de formulaire XML avec une conception de formulaire et de générer le document sur une imprimante ou un fichier réseau.

Il existe deux façons de transmettre une conception de formulaire (un fichier XDP) au service Output. Vous pouvez soit transmettre une `com.adobe.idp.Document` qui contient une conception de formulaire pour le service Output. Vous pouvez également transmettre une valeur URI qui spécifie l’emplacement de la conception de formulaire. Ces deux méthodes sont décrites dans la section *Programmation avec les AEM forms*.

>[!NOTE]
>
>Le service Output ne prend pas en charge les documents de PDF Acrobat contenant des scripts spécifiques à des objets d’application. Les documents Acroform PDF contenant des scripts spécifiques à un objet d’application ne sont pas rendus.

Les sections suivantes expliquent comment transmettre une conception de formulaire au service Output à l’aide d’une valeur URI :

* [Création de documents PDF](creating-document-output-streams.md#creating-pdf-documents)
* [Création de documents PDF/A](creating-document-output-streams.md#creating-pdf-a-documents)

Les sections suivantes expliquent comment transmettre une conception de formulaire dans une `com.adobe.idp.Document` instance :

* [Transmission de documents situés dans Content Services (obsolète) vers Output Service](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Création de documents PDF à l’aide de fragments](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

Lorsque vous décidez de la technique à utiliser, vous devez savoir si vous obtenez la conception de formulaire d’un autre service AEM Forms, puis la transmettre dans un `com.adobe.idp.Document` instance. Les deux *Transmission de documents à Output Service* et *Création de documents PDF à l’aide de fragments* les sections montrent comment obtenir une conception de formulaire à partir d’un autre service AEM Forms. La première section récupère la conception de formulaire à partir de Content Services (obsolète). La deuxième section récupère la conception de formulaire à partir du service Assembler.

Si vous obtenez la conception de formulaire à partir d’un emplacement fixe, tel que le système de fichiers, vous pouvez utiliser l’une ou l’autre des techniques. En d’autres termes, vous pouvez spécifier la valeur URI d’un fichier XDP ou utiliser une `com.adobe.idp.Document` instance.

Pour transmettre une valeur URI qui spécifie l’emplacement de la conception de formulaire lors de la création d’un document de PDF, utilisez la variable `generatePDFOutput` . De même, pour transmettre une `com.adobe.idp.Document` au service Output lors de la création d’un document de PDF, utilisez la méthode `generatePDFOutput2` .

Lors de l’envoi d’un flux de sortie vers une imprimante réseau, vous pouvez également utiliser l’une ou l’autre des techniques. Pour envoyer un flux de sortie à une imprimante en transmettant un message `com.adobe.idp.Document` qui contient une conception de formulaire, utilisez la méthode `sendToPrinter2`. Pour envoyer un flux de sortie à une imprimante en transmettant une valeur URI, utilisez la méthode `sendToPrinter`. Le *Envoi de flux d’impression aux imprimantes* utilise la fonction `sendToPrinter` .

Vous pouvez accomplir ces tâches en utilisant le service Output :

* [Création de documents PDF](creating-document-output-streams.md#creating-pdf-documents)
* [Création de documents PDF/A](creating-document-output-streams.md#creating-pdf-a-documents)
* [Transmission de documents situés dans Content Services (obsolète) vers Output Service](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Création de documents PDF à l’aide de fragments](creating-document-output-streams.md#creating-pdf-documents-using-fragments)
* [Impression dans des fichiers](creating-document-output-streams.md#printing-to-files)
* [Envoi de flux d’impression aux imprimantes](creating-document-output-streams.md#sending-print-streams-to-printers)
* [Création de plusieurs fichiers de sortie](creating-document-output-streams.md#creating-multiple-output-files)
* [Création de règles de recherche](creating-document-output-streams.md#creating-search-rules)
* [Aplatissement de documents PDF](creating-document-output-streams.md#flattening-pdf-documents)

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Création de documents PDF {#creating-pdf-documents}

Vous pouvez utiliser le service Output pour créer un document PDF basé sur une conception de formulaire et des données de formulaire XML que vous fournissez. Le document de PDF créé par le service Output n’est pas un document de PDF interactif ; un utilisateur ne peut pas saisir ni modifier des données de formulaire.

Si vous souhaitez créer un document de PDF destiné au stockage à long terme, il est recommandé de créer un document de PDF/A. (Voir [Création de documents PDF/A](creating-document-output-streams.md#creating-pdf-a-documents).)

Pour créer un formulaire de PDF interactif qui permet à l’utilisateur de saisir des données, utilisez le service Forms. (Voir [Rendu des PDF forms interactifs](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms).)

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour créer un document PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet client de sortie.
1. Référencez une source de données XML.
1. Définissez les options d’exécution du PDF.
1. Définissez les options d’exécution de rendu.
1. Générez un document de PDF.
1. Récupérez les résultats de l’opération.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utility.jar (Obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (requis si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un objet client de sortie**

Avant d’effectuer une opération de service Output par programmation, vous devez créer un objet client de service Output. Si vous utilisez l’API Java, créez une `OutputClient` . Si vous utilisez l’API du service Web d’Output, créez une `OutputServiceService` .

**Référence à une source de données XML**

Pour fusionner les données avec la conception de formulaire, vous devez référencer une source de données XML contenant des données. Un élément XML doit exister pour chaque champ de formulaire que vous prévoyez de renseigner avec des données. Le nom de l’élément XML doit correspondre au nom du champ. Un élément XML est ignoré s’il ne correspond pas à un champ de formulaire ou si le nom de l’élément XML ne correspond pas au nom du champ. Il n&#39;est pas nécessaire de correspondre à l&#39;ordre dans lequel les éléments XML sont affichés si tous les éléments XML sont spécifiés.

Examinez l’exemple de formulaire de demande de prêt suivant.

![cp_cp_loanformdata](assets/cp_cp_loanformdata.png)

Pour fusionner les données dans cette conception de formulaire, vous devez créer une source de données XML correspondant au formulaire. Le code XML suivant représente une source de données XDP XML qui correspond à l’exemple de formulaire de demande de prêt immobilier.

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

**Définition des options d’exécution du PDF**

Définissez l’option URI du fichier lors de la création d’un document de PDF. Cette option spécifie le nom et l’emplacement du fichier de PDF généré par le service Output.

>[!NOTE]
>
>Au lieu de définir l’option d’exécution URI du fichier, vous pouvez récupérer par programmation le document du PDF à partir du type de données complexe renvoyé par le service Output. Toutefois, en définissant l’option d’exécution URI du fichier, vous n’avez pas besoin de créer une logique d’application qui récupère par programmation le document du PDF.

**Définition des options d’exécution de rendu**

Vous pouvez définir des options d’exécution de rendu lors de la création d’un document de PDF. Bien que ces options ne soient pas requises (contrairement aux options d’exécution de PDF qui sont requises), vous pouvez effectuer des tâches telles que l’amélioration des performances du service Output. Par exemple, vous pouvez mettre en cache la conception de formulaire utilisée par le service Output afin d’améliorer ses performances.

Si vous utilisez un formulaire Acrobat balisé comme entrée, vous ne pouvez pas utiliser l’API Java ou Web Service Output pour désactiver le paramètre balisé. Si vous tentez de définir cette option par programmation sur `false`, le document du PDF de résultats est toujours balisé.

>[!NOTE]
>
>Si vous ne spécifiez pas d’options d’exécution de rendu, les valeurs par défaut sont utilisées. Pour plus d’informations sur le rendu des options d’exécution, voir `RenderOptionsSpec` référence de classe. (Voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

**Génération d’un document de PDF**

Après avoir référencé une source de données XML valide contenant des données de formulaire et défini des options d’exécution, vous pouvez appeler le service Output, ce qui génère un document de PDF.

Lors de la génération d’un document de PDF, vous spécifiez les valeurs d’URI requises par le service Output pour créer un document de PDF. Une conception de formulaire peut être stockée dans des emplacements tels que le système de fichiers du serveur ou dans le cadre d’une application AEM Forms. Une conception de formulaire (ou d’autres ressources telles qu’un fichier image) qui existe dans le cadre d’une application Forms peut être référencée à l’aide de la valeur URI racine du contenu. `repository:///`. Prenons l’exemple de la conception de formulaire suivante nommée *Loan.xdp* situé dans une application Forms nommée *Applications/FormsApplication*:

![cp_cp_formrepository](assets/cp_cp_formrepository.png)

Pour accéder au fichier Loan.xdp affiché dans l’illustration précédente, spécifiez `repository:///Applications/FormsApplication/1.0/FormsFolder/` comme troisième paramètre transmis à la variable `OutputClient` de `generatePDFOutput` . Indiquez le nom du formulaire (*Loan.xdp*) comme second paramètre transmis à la variable `OutputClient` de `generatePDFOutput` .

Si le fichier XDP contient des images (ou d’autres ressources telles que des fragments), placez les ressources dans le même dossier d’application que le fichier XDP. AEM Forms utilise l’URI racine du contenu comme chemin d’accès de base pour résoudre les références aux images. Par exemple, si le fichier Loan.xdp contient une image, veillez à placer l’image dans `Applications/FormsApplication/1.0/FormsFolder/`.

>[!NOTE]
>
>Vous pouvez référencer un URI d’application Forms lors de l’appel de la fonction `OutputClient` de `generatePDFOutput` ou `generatePrintedOutput` méthodes.

>[!NOTE]
>
>Pour afficher un démarrage rapide complet qui crée un document de PDF en référençant un XDP situé dans une application Forms, reportez-vous à la section [Démarrage rapide (mode EJB) : Création d’un document de PDF basé sur un fichier XDP d’application à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api).

**Récupération des résultats de l’opération**

Une fois que le service Output a effectué une opération, il renvoie divers éléments de données, tels que les données XML d’état qui spécifient si l’opération a réussi.

**Voir également**

[Création d’un document de PDF à l’aide de l’API Java](creating-document-output-streams.md#create-a-pdf-document-using-the-java-api)

[Création d’un document de PDF à l’aide de l’API de service Web](creating-document-output-streams.md#create-a-pdf-document-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Création d’un document de PDF à l’aide de l’API Java {#create-a-pdf-document-using-the-java-api}

Créez un document de PDF à l’aide de l’API Output (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-output-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet client de sortie.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez une source de données XML.

   * Créez un `java.io.FileInputStream` qui représente la source de données XML utilisée pour remplir le document du PDF en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier XML.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur. Transmettez la variable `java.io.FileInputStream` .

1. Définissez les options d’exécution du PDF.

   * Créez un objet `PDFOutputOptionsSpec` en utilisant son constructeur.
   * Définissez l’option File URI en appelant la méthode `PDFOutputOptionsSpec` de `setFileURI` . Transmettez une valeur string qui spécifie l’emplacement du fichier de PDF généré par le service Output. L’option File URI est relative au serveur d’applications J2EE hébergeant AEM Forms, et non à l’ordinateur client.

1. Définissez les options d’exécution de rendu.

   * Créez un objet `RenderOptionsSpec` en utilisant son constructeur.
   * Mettez en cache la conception de formulaire pour améliorer les performances du service Output en appelant la fonction `RenderOptionsSpec` de `setCacheEnabled` et transmission `true`.

   >[!NOTE]
   >
   >Vous ne pouvez pas définir la version du document du PDF à l’aide du `RenderOptionsSpec` de `setPdfVersion` si le document d’entrée est un formulaire Acrobat (un formulaire créé dans Acrobat) ou un document XFA signé ou certifié. Le document du PDF de sortie conserve la version originale du PDF. De même, vous ne pouvez pas définir l’option Adobe PDF balisée en appelant la variable `RenderOptionsSpec` de `setTaggedPDF`* si le document d’entrée est un formulaire Acrobat ou un document XFA signé ou certifié. *

   >[!NOTE]
   >
   >Vous ne pouvez pas définir l’option de PDF linéarisé à l’aide de la variable `RenderOptionsSpec` de `setLinearizedPDF` si le document du PDF d’entrée est certifié ou signé numériquement. (Voir [Signature numérique de documents PDF ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Générez un document de PDF.

   Créez un document de PDF en appelant la méthode `OutputClient` de `generatePDFOutput` et transmission des valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie la racine de contenu où se trouve la conception de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `com.adobe.idp.Document` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.

   Le `generatePDFOutput` renvoie une `OutputResult` contenant les résultats de l’opération.

   >[!NOTE]
   >
   >Lors de la génération d’un document de PDF en appelant la méthode `generatePDFOutput` , sachez que vous ne pouvez pas fusionner des données avec un formulaire de PDF XFA signé ou certifié. (Voir [Signature numérique et certification de documents ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >Le `OutputResult` de `getRecordLevelMetaDataList` method renvoie `null`*.*

   >[!NOTE]
   >
   >Vous pouvez également créer un document de PDF en appelant la méthode `OutputClient` de `generatePDFOutput2` . (Voir [Transmission de documents situés dans Content Services (obsolète) vers Output Service ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Récupérez les résultats de l’opération.

   * Récupération d’une `com.adobe.idp.Document` qui représente l’état de la propriété `generatePDFOutput` en appelant la fonction `OutputResult` de `getStatusDoc` . Cette méthode renvoie des données XML d’état qui spécifient si l’opération a réussi.
   * Créez un `java.io.File` contenant les résultats de l’opération. Assurez-vous que l’extension de nom de fichier est .xml.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` dans le fichier (assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui a été renvoyé par l’objet `getStatusDoc` ).

   Bien que le service Output écrive le document du PDF à l’emplacement spécifié par l’argument transmis à la variable `PDFOutputOptionsSpec` de `setFileURI` , vous pouvez récupérer le document PDF/A par programmation en appelant la méthode `OutputResult` de `getGeneratedDoc` .

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode EJB) : Création d’un document de PDF à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Démarrage rapide (mode SOAP) : Création d’un document de PDF à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Création d’un document de PDF à l’aide de l’API de service Web {#create-a-pdf-document-using-the-web-service-api}

Créez un document de PDF à l’aide de l’API Output (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost`* avec l’adresse IP du serveur hébergeant AEM Forms. *

1. Créez un objet client de sortie.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Create an `OutputServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Pass a string value that specifies the WSDL to the AEM Forms service (for example, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez une source de données XML.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker les données XML qui seront fusionnées avec le document du PDF.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier XML contenant les données de formulaire.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définition des options d’exécution du PDF

   * Créez un objet `PDFOutputOptionsSpec` en utilisant son constructeur.
   * Définissez l’option File URI en attribuant une valeur string qui spécifie l’emplacement du fichier de PDF généré par le service Output à la variable `PDFOutputOptionsSpec` de `fileURI` membre de données. L’option File URI est relative au serveur d’applications J2EE hébergeant AEM Forms, et non à l’ordinateur client.

1. Définissez les options d’exécution de rendu.

   * Créez un objet `RenderOptionsSpec` en utilisant son constructeur.
   * Mettre en cache la conception de formulaire pour améliorer les performances du service Output en affectant la valeur `true` au `RenderOptionsSpec` de `cacheEnabled` membre de données.

   >[!NOTE]
   >
   >Vous ne pouvez pas définir la version du document du PDF à l’aide du `RenderOptionsSpec` de `setPdfVersion` si le document d’entrée est un formulaire Acrobat (un formulaire créé dans Acrobat) ou un document XFA signé ou certifié. Le document du PDF de sortie conserve la version originale du PDF. De même, vous ne pouvez pas définir l’option Adobe PDF balisée en appelant la variable `RenderOptionsSpec` de `setTaggedPDF`* si le document d’entrée est un formulaire Acrobat ou un document XFA signé ou certifié.*

   >[!NOTE]
   >
   >Vous ne pouvez pas définir l’option de PDF linéarisé à l’aide de la variable `RenderOptionsSpec` de `linearizedPDF` membre si le document du PDF d’entrée est certifié ou signé numériquement. (Voir [Signature numérique de documents PDF ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Générez un document de PDF.

   Créez un document de PDF en appelant la méthode `OutputServiceService` de `generatePDFOutput`et transmission des valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie la racine de contenu où se trouve la conception de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `BLOB` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec des métadonnées générées qui décrivent le document. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec les données de résultat. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).
   * Un `OutputResult` contenant les résultats de l’opération. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).

   >[!NOTE]
   >
   >Lors de la génération d’un document de PDF en appelant la méthode `generatePDFOutput` , sachez que vous ne pouvez pas fusionner des données avec un formulaire de PDF XFA signé ou certifié. (Voir [Signature numérique et certification de documents ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >Vous pouvez également créer un document de PDF en appelant la méthode `OutputClient` de `generatePDFOutput2` . (Voir [Transmission de documents situés dans Content Services (obsolète) vers Output Service ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Récupérez les résultats de l’opération.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente un emplacement de fichier XML contenant les données de résultat. Assurez-vous que l’extension de nom de fichier est .xml.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renseigné avec les données de résultat de la fonction `OutputServiceService` de `generatePDFOutput` (le huitième paramètre). Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` `field`.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans le fichier XML en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

   Voir également

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

   >[!NOTE]
   >
   >Le `OutputServiceService` de `generateOutput` est obsolète.

## Création de documents PDF/A {#creating-pdf-a-documents}

Vous pouvez utiliser le service Output pour créer un document PDF/A. Comme PDF/A est un format d’archivage pour la conservation à long terme du contenu du document, toutes les polices sont incorporées et le fichier est décompressé. Par conséquent, un document PDF/A est généralement plus volumineux qu’un document PDF standard. En outre, un document PDF/A ne contient pas de contenu audio et vidéo. Comme les autres tâches du service Output, vous fournissez une conception de formulaire et des données à fusionner avec une conception de formulaire pour créer un document PDF/A.

La spécification PDF/A-1 se compose de deux niveaux de conformité, à savoir a et b. La principale différence entre les deux concerne la prise en charge de la structure logique (accessibilité), qui n’est pas requise pour le niveau de conformité b. Quel que soit le niveau de conformité, PDF/A-1 exige que toutes les polices soient incorporées dans le document PDF/A généré.

Bien que PDF/A soit la norme d’archivage des documents de PDF, il n’est pas obligatoire que PDF/A soit utilisé pour l’archivage si un document de PDF standard répond aux besoins de votre entreprise. Le but de la norme PDF/A est d’établir un fichier de PDF qui peut être stocké pendant une longue période et qui répond aux exigences de conservation des documents. Par exemple, une URL ne peut pas être incorporée dans un PDF/A, car au fil du temps, l’URL peut devenir non valide.

Votre entreprise doit évaluer ses propres besoins, le temps que vous avez l’intention de conserver le document, les considérations de taille de fichier et déterminer votre propre stratégie d’archivage. Vous pouvez déterminer par programmation si un document de PDF est compatible avec PDF/A à l’aide du service DocConverter. (Voir [Détermination par programmation de la conformité PDF/A](/help/forms/developing/pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

Un document PDF/A doit utiliser la police spécifiée dans la conception de formulaire et les polices ne peuvent pas être remplacées. Par conséquent, si une police située dans un document de PDF n’est pas disponible sur le système d’exploitation hôte, une exception se produit.

Lorsqu’un document PDF/A est ouvert dans Acrobat, un message s’affiche pour confirmer que le document est un document PDF/A, comme illustré ci-dessous.

![cp_cp_pdfamessage](assets/cp_cp_pdfamessage.png)

>[!NOTE]
>
>Le site web d’AIIM comporte une section FAQ sur les PDF/A accessible à l’adresse [https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml](https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml).

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_64).

### Résumé des étapes {#summary_of_steps-1}

Pour créer un document PDF/A, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet client de sortie.
1. Référencez une source de données XML.
1. Définissez les options d’exécution PDF/A.
1. Définissez les options d’exécution de rendu.
1. Générez un document PDF/A.
1. Récupérez les résultats de l’opération.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application personnalisée à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utility.jar (Obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (requis si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un objet client de sortie**

Avant d’effectuer une opération de service Output par programmation, vous devez créer un objet client de service Output. Si vous utilisez l’API Java, créez une `OutputClient` . Si vous utilisez l’API du service Web d’Output, créez une `OutputServiceService` .

**Référence à une source de données XML**

To merge data with the form design, you must reference an XML data source that contains data. An XML element must exist for every form field that you want to populate with data. Le nom de l’élément XML doit correspondre au nom du champ. Un élément XML est ignoré s’il ne correspond pas à un champ de formulaire ou si le nom de l’élément XML ne correspond pas au nom du champ. Il n&#39;est pas nécessaire de correspondre à l&#39;ordre dans lequel les éléments XML sont affichés si tous les éléments XML sont spécifiés.

**Définition des options d’exécution PDF/A**

Vous pouvez définir l’option URI du fichier lors de la création d’un document de PDF/A. L’URI est relatif au serveur d’applications J2EE hébergeant AEM Forms. En d’autres termes, si vous définissez C:\Adobe, le fichier est écrit dans le dossier sur le serveur et non sur l’ordinateur client. L’URI spécifie le nom et l’emplacement du fichier PDF/A généré par le service Output.

**Définition des options d’exécution de rendu**

Vous pouvez définir des options d’exécution de rendu lors de la création de documents PDF/A. Vous pouvez définir deux options associées à PDF/A : `PDFAConformance` et `PDFARevisionNumber` valeurs. Le `PDFAConformance` fait référence à la manière dont un document PDF respecte les exigences qui spécifient la manière dont les documents électroniques à long terme sont conservés. Les valeurs valides de cette option sont `A` et `B`. Pour plus d’informations sur la conformité a et b, voir la spécification ISO PDF/A-1 intitulée *ISO 19005-1 Gestion des documents*.

Le `PDFARevisionNumber` fait référence au numéro de révision d’un document PDF/A. Pour plus d’informations sur le numéro de révision d’un document PDF/A, voir la spécification ISO PDF/A-1 intitulée *ISO 19005-1 Gestion des documents*.

>[!NOTE]
>
>Vous ne pouvez pas définir l’option Adobe PDF balisée sur `false` lors de la création d’un document PDF/A 1A. PDF/A 1A sera toujours un document de PDF balisé. En outre, vous ne pouvez pas définir l’option Adobe PDF balisée sur `true` lors de la création d’un document PDF/A 1B. PDF/A 1B sera toujours un document de PDF non balisé.

**Génération d’un document de PDF/A**

Après avoir référencé une source de données XML valide contenant des données de formulaire et défini des options d’exécution, vous pouvez appeler le service Output, ce qui génère un document PDF/A.

**Récupération des résultats de l’opération**

Une fois que le service Output a effectué une opération, il renvoie divers éléments de données, tels que des données XML qui spécifient si l’opération a réussi.

**Voir également**

[Créer un document PDF/A à l’aide de l’API Java](creating-document-output-streams.md#create-a-pdf-a-document-using-the-java-api)

[Création d’un document PDF/A à l’aide de l’API de service Web](creating-document-output-streams.md#create-a-pdf-a-document-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Créer un document PDF/A à l’aide de l’API Java {#create-a-pdf-a-document-using-the-java-api}

Create a PDF/A document by using the Output API (Java):

1. Inclure les fichiers de projet.

   Include client JAR files, such as adobe-output-client.jar, in your Java project’s class path.

1. Créez un objet client de sortie.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez une source de données XML.

   * Créez un `java.io.FileInputStream` qui représente la source de données XML utilisée pour remplir le document PDF/A en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier XML.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définissez les options d’exécution PDF/A.

   * Créez un objet `PDFOutputOptionsSpec` en utilisant son constructeur.
   * Définissez l’option File URI en appelant la méthode `PDFOutputOptionsSpec` de `setFileURI` . Transmettez une valeur string qui spécifie l’emplacement du fichier de PDF généré par le service Output. L’option File URI est relative au serveur d’applications J2EE hébergeant AEM Forms, et non à l’ordinateur client.

1. Définissez les options d’exécution de rendu.

   * Créez un objet `RenderOptionsSpec` en utilisant son constructeur.
   * Définissez la variable `PDFAConformance` en appelant la variable `RenderOptionsSpec` de `setPDFAConformance` et transmission d’une `PDFAConformance` valeur enum qui spécifie le niveau de conformité. Par exemple, pour spécifier le niveau de conformité A, transmettez `PDFAConformance.A`.
   * Définissez la variable `PDFARevisionNumber` en appelant la variable `RenderOptionsSpec` de `setPDFARevisionNumber` méthode et transmission `PDFARevisionNumber.Revision_1`.

   >[!NOTE]
   >
   >La version PDF d’un document PDF/A est 1.4, quelle que soit la valeur que vous spécifiez pour la variable `RenderOptionsSpec` de `setPdfVersion`*.*

1. Générez un document PDF/A.

   Créez un document de PDF/A en appelant la fonction `OutputClient` de `generatePDFOutput` et transmission des valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF/A, spécifiez `TransformationFormat.PDFA`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie la racine de contenu où se trouve la conception de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `com.adobe.idp.Document` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.

   Le `generatePDFOutput` renvoie une `OutputResult` contenant les résultats de l’opération.

   >[!NOTE]
   >
   >Le `OutputResult` de `getRecordLevelMetaDataList` method renvoie `null`*. *

   >[!NOTE]
   >
   >Vous pouvez également créer un document /A de PDF en appelant le `OutputClient` de `generatePDFOutput`2. (Voir [Transmission de documents situés dans Content Services (obsolète) vers Output Service](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Récupérez les résultats de l’opération.

   * Créez un `com.adobe.idp.Document` qui représente l’état de la propriété `generatePDFOutput` en appelant la méthode `OutputResult` de `getStatusDoc` .
   * Créez un `java.io.File` qui contiendra les résultats de l’opération. Assurez-vous que l’extension de nom de fichier est .xml.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` dans le fichier (assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui a été renvoyé par l’objet `getStatusDoc` ).

   >[!NOTE]
   >
   >Bien que le service Output écrive le document PDF/A à l’emplacement spécifié par l’argument transmis à la variable `PDFOutputOptionsSpec` de `setFileURI` , vous pouvez récupérer le document PDF/A par programmation en appelant la méthode `OutputResult` de `getGeneratedDoc`* method.*

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode SOAP) : Création d’un document PDF/A à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-a-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Création d’un document PDF/A à l’aide de l’API de service Web {#create-a-pdf-a-document-using-the-web-service-api}

Créez un document PDF/A à l’aide de l’API Output (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost`* avec l’adresse IP du serveur hébergeant AEM Forms. *

1. Créez un objet client de sortie.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Créez un `OutputServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez une source de données XML.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker les données qui seront fusionnées avec le document PDF/A.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF à chiffrer et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution PDF/A.

   * Créez un objet `PDFOutputOptionsSpec` en utilisant son constructeur.
   * Définissez l’option File URI en attribuant une valeur string qui spécifie l’emplacement du fichier de PDF généré par le service Output à la variable `PDFOutputOptionsSpec` de `fileURI` membre de données. L’option File URI est relative au serveur d’applications J2EE hébergeant AEM Forms, et non à l’ordinateur client.

1. Définissez les options d’exécution de rendu.

   * Créez un objet `RenderOptionsSpec` en utilisant son constructeur.
   * Définissez la variable `PDFAConformance` en attribuant une valeur `PDFAConformance` Enum value to the `RenderOptionsSpec` de `PDFAConformance` membre de données. Par exemple, pour spécifier le niveau de conformité A, affectez `PDFAConformance.A` à ce membre de données.
   * Définissez la variable `PDFARevisionNumber` en attribuant une valeur `PDFARevisionNumber` Enum value to the `RenderOptionsSpec` de `PDFARevisionNumber` membre de données. Attribuer `PDFARevisionNumber.Revision_1` à ce membre de données.

   >[!NOTE]
   >
   >La version PDF d’un document PDF/A est 1.4, quelle que soit la valeur que vous indiquez.

1. Générez un document PDF/A.

   Créez un document de PDF en appelant la méthode `OutputServiceService` de `generatePDFOutput`et transmission des valeurs suivantes :

   * Une valeur d’énumération TransformationFormat . Pour générer un document de PDF, spécifiez `TransformationFormat.PDFA`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie la racine de contenu où se trouve la conception de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `BLOB` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec des métadonnées générées qui décrivent le document. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec les données de résultat. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)
   * Un `OutputResult` contenant les résultats de l’opération. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)

   >[!NOTE]
   >
   >Vous pouvez également créer un document /A de PDF en appelant le `OutputClient` de `generatePDFOutput`2. (Voir [Transmission de documents situés dans Content Services (obsolète) vers Output Service](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Récupérez les résultats de l’opération.

   * Create a `System.IO.FileStream` object by invoking its constructor and passing a string value that represents an XML file location that contains result data. Assurez-vous que l’extension de nom de fichier est .xml.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renseigné avec les données de résultat de la fonction `OutputServiceService` de `generatePDFOutput` (le huitième paramètre). Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Write the contents of the byte array to the XML file by invoking the `System.IO.BinaryWriter` object’s `Write` method and passing the byte array.

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Transmission de documents situés dans Content Services (obsolète) vers Output Service {#passing-documents-located-in-content-services-deprecated-to-the-output-service}

Le service Output génère un formulaire de PDF non interactif basé sur une conception de formulaire généralement enregistrée en tant que fichier XDP et créée dans Designer. Vous pouvez transmettre une `com.adobe.idp.Document` qui contient la conception de formulaire au service Output. Le service Output effectue ensuite le rendu de la conception de formulaire située dans l’objet `com.adobe.idp.Document` .

L’avantage de transmettre une variable `com.adobe.idp.Document` le service Output indique que d’autres opérations du service AEM Forms renvoient un `com.adobe.idp.Document` instance. C&#39;est-à-dire que vous pouvez obtenir une `com.adobe.idp.Document` à partir d’une autre opération de service et d’en effectuer le rendu. Supposons, par exemple, qu’un fichier XDP soit stocké dans un noeud Content Services (obsolète) nommé `/Company Home/Form Designs`, comme illustré ci-dessous.

Vous pouvez récupérer Loan.xdp par programmation à partir de Content Services (obsolète) et transmettre le fichier XDP au service Output dans une `com.adobe.idp.Document` .

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-2}

Pour transmettre un document obtenu à partir de Content Services (obsolète) au service Output, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un objet d’API Output et Document Management Client.
1. Récupérez la conception de formulaire auprès de Content Services (obsolète).
1. Générer le formulaire de PDF non interactif.
1. Exécutez une action avec le flux de données.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires à votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, incluez les fichiers proxy.

**Création d’une sortie et d’un objet API client Document Management**

Avant d’effectuer par programmation une opération d’API de service Output, créez un objet API de client de sortie. En outre, comme ce workflow récupère un fichier XDP de Content Services (obsolète), créez un objet API Document Management.

**Récupération de la conception de formulaire auprès de Content Services (obsolète)**

Récupérez le fichier XDP à partir de Content Services (obsolète) à l’aide de l’API Java ou de service Web. Le fichier XDP est renvoyé dans un `com.adobe.idp.Document` (ou une `BLOB` si vous utilisez des services web). Vous pouvez ensuite transmettre la variable `com.adobe.idp.Document` au service Output.

**Rendu du formulaire de PDF non interactif**

Pour effectuer le rendu d’un formulaire non interactif, transmettez la variable `com.adobe.idp.Document` instance renvoyée par Content Services (obsolète) au service Output.

>[!NOTE]
>
>Deux nouvelles méthodes nommées `generatePDFOutput2`et g `eneratePrintedOutput2`accepter un `com.adobe.idp.Document` contenant une conception de formulaire. Vous pouvez également transmettre une `com.adobe.idp.Document`qui contient la conception de formulaire au service Output lors de l’envoi d’un flux d’impression vers une imprimante réseau.

**Exécution d’une action avec le flux de données de formulaire**

Vous pouvez enregistrer le formulaire non interactif en tant que fichier de PDF. Le formulaire peut être affiché dans Adobe Reader ou Acrobat.

**Voir également**

[Transmission de documents à Output Service à l’aide de l’API Java](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-java-api)

[Transmission de documents à Output Service à l’aide de l’API du service Web](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Création de documents PDF à l’aide de fragments](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

### Transmission de documents à Output Service à l’aide de l’API Java {#pass-documents-to-the-output-service-using-the-java-api}

Transmettez un document récupéré de Content Services (obsolète) à l’aide du service Output et de l’API Content Services (obsolète) (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-output-client.jar et adobe-contentservices-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet d’API Output et Document Management Client.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion. (Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .
   * Créez un objet `DocumentManagementServiceClientImpl` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez la conception de formulaire auprès de Content Services (obsolète).

   Appeler la variable `DocumentManagementServiceClientImpl` de `retrieveContent` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le magasin où le contenu est ajouté. Le magasin par défaut est `SpacesStore`. Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie le chemin d’accès complet du contenu à récupérer (par exemple, `/Company Home/Form Designs/Loan.xdp`). Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie la version. Cette valeur est un paramètre facultatif et vous pouvez transmettre une chaîne vide. Dans ce cas, la dernière version est récupérée.

   Le `retrieveContent` renvoie une `CRCResult` contenant le fichier XDP. Récupération d’une `com.adobe.idp.Document` en appelant la méthode `CRCResult` de `getDocument` .

1. Générer le formulaire de PDF non interactif.

   Appeler la variable `OutputClient` de `generatePDFOutput2` et transmettez les valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Une valeur string qui spécifie la racine de contenu où se trouvent les ressources supplémentaires telles que les images.
   * A `com.adobe.idp.Document` qui représente la conception de formulaire (utilisez l’instance renvoyée par le `CRCResult` de `getDocument` ).
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `com.adobe.idp.Document` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.

   Le `generatePDFOutput2` renvoie une `OutputResult` contenant les résultats de l’opération.

1. Exécutez une action avec le flux de données de formulaire.

   * Récupération d’une `com.adobe.idp.Document` qui représente le formulaire non interactif en appelant la fonction `OutputResult` de `getGeneratedDoc` .
   * Créez un `java.io.File` contenant les résultats de l’opération. Assurez-vous que l’extension de nom de fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` dans le fichier (assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui a été renvoyé par l’objet `getGeneratedDoc` ).

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode EJB) : Transmission de documents à Output Service à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Démarrage rapide (mode SOAP) : Transmission de documents à Output Service à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Transmission de documents à Output Service à l’aide de l’API du service Web {#pass-documents-to-the-output-service-using-the-web-service-api}

Transmettez un document récupéré de Content Services (obsolète) à l’aide du service Output et de l’API Content Services (obsolète) (obsolète) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Comme cette application cliente appelle deux services AEM Forms, créez deux références de service. Utilisez la définition WSDL suivante pour la référence de service associée au service Output : `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   Utilisez la définition WSDL suivante pour la référence de service associée au service Document Management : `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Parce que la variable `BLOB` Le type de données est commun aux deux références de service. Il qualifie entièrement la variable `BLOB` type de données lors de son utilisation. Dans le démarrage rapide du service Web correspondant, tous les `BLOB` les instances sont entièrement qualifiées.

   >[!NOTE]
   >
   >Remplacer `localhost`* avec l’adresse IP du serveur hébergeant AEM Forms. *

1. Créez un objet d’API Output et Document Management Client.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Créez un `OutputServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service Forms (par exemple, `http://localhost:8080/soap/services/OutputService?blob=mtom`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Répétez ces étapes pour le `DocumentManagementServiceClient`* client de service. *

1. Récupérez la conception de formulaire auprès de Content Services (obsolète).

   Récupération du contenu en appelant la méthode `DocumentManagementServiceClient` de `retrieveContent` et transmission des valeurs suivantes :

   * Une valeur string qui spécifie le magasin où le contenu est ajouté. Le magasin par défaut est `SpacesStore`. Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie le chemin d’accès complet du contenu à récupérer (par exemple, `/Company Home/Form Designs/Loan.xdp`). Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie la version. Cette valeur est un paramètre facultatif et vous pouvez transmettre une chaîne vide. Dans ce cas, la dernière version est récupérée.
   * Un paramètre de sortie string qui stocke la valeur du lien de navigation.
   * A `BLOB` paramètre de sortie qui stocke le contenu. Vous pouvez utiliser ce paramètre de sortie pour récupérer le contenu.
   * A `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` paramètre de sortie qui stocke les attributs de contenu.
   * A `CRCResult` paramètre de sortie. Au lieu d’utiliser cet objet, vous pouvez utiliser la variable `BLOB` paramètre de sortie pour récupérer le contenu.

1. Générer le formulaire de PDF non interactif.

   Appeler la variable `OutputServiceClient` de `generatePDFOutput2` et transmettez les valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Une valeur string qui spécifie la racine de contenu où se trouvent les ressources supplémentaires telles que les images.
   * A `BLOB` qui représente la conception de formulaire (utilisez l’objet `BLOB` instance renvoyée par Content Services (obsolète).
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `BLOB` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.
   * Une sortie `BLOB` qui est renseigné par la variable `generatePDFOutput2` . Le `generatePDFOutput2` renseigne cet objet avec des métadonnées générées qui décrivent le document. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).
   * Une sortie `OutputResult` contenant les résultats de l’opération. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).

   Le `generatePDFOutput2` renvoie une `BLOB` contenant le formulaire de PDF non interactif.

1. Exécutez une action avec le flux de données de formulaire.

   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF interactif et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` récupéré à partir de l’objet `generatePDFOutput2` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Transmission de documents situés dans le référentiel vers le service Output {#passing-documents-located-in-the-repository-to-the-output-service}

Le service Output génère un formulaire de PDF non interactif basé sur une conception de formulaire généralement enregistrée en tant que fichier XDP et créée dans Designer. Vous pouvez transmettre une `com.adobe.idp.Document` qui contient la conception de formulaire au service Output. Le service Output effectue ensuite le rendu de la conception de formulaire située dans l’objet `com.adobe.idp.Document` .

L’avantage de transmettre une variable `com.adobe.idp.Document` le service Output indique que d’autres opérations du service AEM Forms renvoient un `com.adobe.idp.Document` instance. C&#39;est-à-dire que vous pouvez obtenir une `com.adobe.idp.Document` à partir d’une autre opération de service et d’en effectuer le rendu. Supposons, par exemple, qu’un fichier XDP soit stocké dans le référentiel AEM Forms, comme illustré ci-dessous.

![pd_pd_formrepository](assets/pd_pd_formrepository.png)

Le *FormsFolder* est un emplacement défini par l’utilisateur dans le référentiel AEM Forms (cet emplacement est un exemple et n’existe pas par défaut). Dans cet exemple, une conception de formulaire nommée Loan.xdp se trouve dans ce dossier. Outre la conception de formulaire, d’autres documents de formulaire, tels que des images, peuvent être stockés à cet emplacement. Le chemin d’accès à une ressource située dans le référentiel AEM Forms est le suivant :

`Applications/Application-name/Application-version/Folder.../Filename`

Vous pouvez récupérer Loan.xdp par programmation à partir du référentiel AEM Forms et le transmettre au service Output dans une `com.adobe.idp.Document` .

Vous pouvez créer un PDF à partir d’un fichier XDP situé dans le référentiel de l’une des deux façons suivantes. Vous pouvez transmettre l’emplacement XDP par référence ou récupérer par programmation le XDP à partir du référentiel et le transmettre au service Output dans un fichier XDP.

[Démarrage rapide (mode EJB) : Création d’un document de PDF basé sur un fichier XDP d’application à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api) (indique comment transmettre l’emplacement du fichier XDP par référence).

[Démarrage rapide (mode EJB) : Transmission d’un document situé dans le référentiel AEM Forms au service Output à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (indique comment récupérer le fichier XDP par programmation à partir du référentiel AEM Forms et le transmettre au service Output dans une `com.adobe.idp.Document` ). (Cette section explique comment effectuer cette tâche)

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-3}

Pour transmettre un document obtenu du référentiel AEM Forms au service Output, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un objet d’API Output et Document Management Client.
1. Récupérez la conception de formulaire à partir du référentiel AEM Forms.
1. Générer le formulaire de PDF non interactif.
1. Exécutez une action avec le flux de données.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires à votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, incluez les fichiers proxy.

**Création d’une sortie et d’un objet API client Document Management**

Avant d’effectuer par programmation une opération d’API de service Output, créez un objet API de client de sortie. En outre, comme ce workflow récupère un fichier XDP de Content Services (obsolète), créez un objet API Document Management.

**Récupération de la conception de formulaire à partir du référentiel AEM Forms**

Récupérez le fichier XDP à partir du référentiel AEM Forms à l’aide de l’API Repository. (Voir [Lire les ressources](/help/forms/developing/aem-forms-repository.md#reading-resources).)

Le fichier XDP est renvoyé dans un `com.adobe.idp.Document` (ou une `BLOB` si vous utilisez des services web). Vous pouvez ensuite transmettre la variable `com.adobe.idp.Document` de l’instance du service Output.

**Rendu du formulaire de PDF non interactif**

Pour effectuer le rendu d’un formulaire non interactif, transmettez la variable `com.adobe.idp.Document` instance renvoyée à l’aide de l’API AEM Forms Repository.

>[!NOTE]
>
>Deux nouvelles méthodes nommées `generatePDFOutput2`et `generatePrintedOutput2`accepter un `com.adobe.idp.Document`contenant une conception de formulaire. Vous pouvez également transmettre une `com.adobe.idp.Document` qui contient la conception de formulaire au service Output lors de l’envoi d’un flux d’impression vers une imprimante réseau.

**Exécution d’une action avec le flux de données de formulaire**

Vous pouvez enregistrer le formulaire non interactif en tant que fichier de PDF. Le formulaire peut être affiché dans Adobe Reader ou Acrobat.

**Voir également**

[Transmettre des documents situés dans le référentiel au service Output à l’aide de l’API Java](creating-document-output-streams.md#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

ResourceRepositoryClient

### Transmettre des documents situés dans le référentiel au service Output à l’aide de l’API Java {#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api}

Transmettez un document récupéré du référentiel à l’aide du service Output et de l’API Repository (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-output-client.jar et adobe-repository-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet d’API Output et Document Management Client.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion. (Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .
   * Créez un objet `DocumentManagementServiceClientImpl` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez la conception de formulaire à partir du référentiel AEM Forms.

   Appeler la variable `ResourceRepositoryClient` de `readResourceContent` et transmettez une valeur string qui spécifie l’emplacement URI au fichier XDP. Par exemple, `/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`. Cette valeur est obligatoire. Cette méthode renvoie une `com.adobe.idp.Document` qui représente le fichier XDP.

1. Générer le formulaire de PDF non interactif.

   Appeler la variable `OutputClient` de `generatePDFOutput2` et transmettez les valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Une valeur string qui spécifie la racine de contenu où se trouvent les ressources supplémentaires telles que les images. Par exemple, `repository:///Applications/FormsApplication/1.0/FormsFolder/`.
   * A `com.adobe.idp.Document` qui représente la conception de formulaire (utilisez l’instance renvoyée par le `ResourceRepositoryClient` de `readResourceContent` ).
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `com.adobe.idp.Document` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.

   Le `generatePDFOutput2` renvoie une `OutputResult` contenant les résultats de l’opération.

1. Exécutez une action avec le flux de données de formulaire.

   * Récupération d’une `com.adobe.idp.Document` qui représente le formulaire non interactif en appelant la fonction `OutputResult` de `getGeneratedDoc` .
   * Créez un `java.io.File` contenant les résultats de l’opération. Assurez-vous que l’extension de nom de fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` dans le fichier (assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui a été renvoyé par l’objet `getGeneratedDoc` ).

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode EJB) : Transmission d’un document situé dans le référentiel AEM Forms au service Output à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Création de documents PDF à l’aide de fragments {#creating-pdf-documents-using-fragments}

Vous pouvez utiliser les services Output et Assembler pour créer un flux de sortie, tel qu’un document PDF, basé sur des fragments. Le service Assembler assemble un document XDP basé sur des fragments situés dans plusieurs fichiers XDP. Le document XDP assemblé est transmis au service Output, ce qui crée un document PDF. Bien que ce workflow affiche un document de PDF en cours de génération, le service Output peut générer d’autres types de sortie, tels que ZPL, pour ce workflow. Un document PDF est utilisé à des fins de discussion uniquement.

L’illustration suivante présente ce processus.

![cp_cp_outputassemblefragments](assets/cp_cp_outputassemblefragments.png)

Before reading *Creating PDF Documents using Fragments*, it is recommended that you become familiar with using the Assembler service to assemble multiple XDP documents. (Voir [Assemblage de plusieurs fragments XDP](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments).)

>[!NOTE]
>
>Vous pouvez également transmettre une conception de formulaire assemblée par le service Assembler au service Forms au lieu du service Output. La Principale différence entre le service Output et le service Forms réside dans le fait que le service Forms génère des documents PDF interactifs et le service Output génère des documents PDF non interactifs. De plus, le service Forms ne peut pas générer de flux de sortie basés sur l’imprimante comme ZPL.

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-4}

Pour créer un document PDF basé sur des fragments, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet client Output et Assembler.
1. Utilisez le service Assembler pour générer la conception de formulaire.
1. Utilisez le service Output pour générer le document du PDF.
1. Enregistrez le document du PDF en tant que fichier de PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet client Output et Assembler**

Avant d’effectuer par programmation une opération d’API de service Output, créez un objet API de client de sortie. En outre, comme ce processus appelle le service Assembler pour créer la conception de formulaire, créez un objet API client Assembler.

**Utilisation du service Assembler pour générer la conception de formulaire**

Utilisez le service Assembler pour générer la conception de formulaire à l’aide de fragments. Le service Assembler renvoie une `com.adobe.idp.Document` qui contient la conception de formulaire.

**Utilisation du service Output pour générer le document du PDF**

Vous pouvez utiliser le service Output pour générer un document de PDF à l’aide de la conception de formulaire créée par le service Assembler. Transmettez la variable `com.adobe.idp.Document` instance que le service Assembler a renvoyée au service Output.

**Enregistrer le document du PDF en tant que fichier de PDF**

Une fois que le service Output a généré un document de PDF, vous pouvez l’enregistrer en tant que fichier de PDF.

**Voir également**

[Création d’un document de PDF basé sur des fragments à l’aide de l’API Java](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-java-api)

[Création d’un document de PDF basé sur des fragments à l’aide de l’API de service Web](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Assemblage de plusieurs fragments XDP](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments)

[Création de documents PDF](creating-document-output-streams.md#creating-pdf-documents)

### Création d’un document de PDF basé sur des fragments à l’aide de l’API Java {#create-a-pdf-document-based-on-fragments-using-the-java-api}

Créez un document de PDF basé sur des fragments à l’aide de l’API Output Service et de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-output-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet client Output et Assembler.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Utilisez le service Assembler pour générer la conception de formulaire.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs requises suivantes :

   * A `com.adobe.idp.Document` qui représente le document DDX à utiliser.
   * A `java.util.Map` contenant les fichiers XDP d’entrée.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation de la tâche.

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` contenant le document XDP assemblé. Pour récupérer le document XDP assemblé, effectuez les actions suivantes :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette méthode renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez le résultat `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document XDP assemblé.


1. Utilisez le service Output pour générer le document du PDF.

   Appeler la variable `OutputClient` de `generatePDFOutput2` et transmettez les valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`
   * Une valeur string qui spécifie la racine de contenu où se trouvent les ressources supplémentaires, telles que les images.
   * A `com.adobe.idp.Document` objet représentant la conception de formulaire (utiliser l’instance renvoyée par le service Assembler)
   * A `PDFOutputOptionsSpec` qui contient les options d’exécution du PDF
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu
   * Le `com.adobe.idp.Document` Objet contenant la source de données XML contenant les données à fusionner avec la conception de formulaire

   Le `generatePDFOutput2` renvoie une `OutputResult` qui contient les résultats de l’opération

1. Enregistrez le document du PDF en tant que fichier de PDF.

   * Récupération d’une `com.adobe.idp.Document` qui représente le document du PDF en appelant la fonction `OutputResult` de `getGeneratedDoc` .
   * Créez un `java.io.File` contenant les résultats de l’opération. Assurez-vous que l’extension de nom de fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` vers le fichier . (Assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui `getGeneratedDoc` ).

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode EJB) : Création d’un document de PDF basé sur des fragments à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Démarrage rapide (mode SOAP) : Création d’un document de PDF basé sur des fragments à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Création d’un document de PDF basé sur des fragments à l’aide de l’API de service Web {#create-a-pdf-document-based-on-fragments-using-the-web-service-api}

Créez un document PDF basé sur des fragments à l’aide de l’API Output Service et de l’API Assembler Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Utilisez la définition WSDL suivante pour la référence de service associée au service Output :

   ```as3
    http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1.
   ```

   Utilisez la définition WSDL suivante pour la référence de service associée au service Assembler :

   ```as3
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   Parce que la variable `BLOB` Le type de données est commun aux deux références de service. Il qualifie entièrement la variable `BLOB` type de données lors de son utilisation. Dans le démarrage rapide du service Web correspondant, tous les `BLOB` les instances sont entièrement qualifiées.

   >[!NOTE]
   >
   >Remplacer `localhost`* avec l’adresse IP du serveur hébergeant AEM Forms. *

1. Créez un objet client Output et Assembler.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Créez un `OutputServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuez AEM nom d’utilisateur aux `OutputServiceClient.ClientCredentials.UserName.UserName`champ .
      * Attribuez la valeur de mot de passe correspondante à la variable `OutputServiceClient.ClientCredentials.UserName.Password`champ .
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au `BasicHttpBindingSecurity.Transport.ClientCredentialType`champ .
   * Attribuez le `BasicHttpSecurityMode.TransportCredentialOnly` valeur constante de la variable `BasicHttpBindingSecurity.Security.Mode`champ .

   >[!NOTE]
   >
   >Répétez ces étapes pour le `AssemblerServiceClient`* objet. *

1. Utilisez le service Assembler pour générer la conception de formulaire.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `BLOB` objet représentant le document DDX
   * Le `MyMapOf_xsd_string_To_xsd_anyType` contenant les fichiers requis
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeDDX` renvoie une `AssemblerResult` contenant les résultats de la tâche et les exceptions survenues. Pour obtenir le document XDP nouvellement créé, effectuez les actions suivantes :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les documents de PDF générés.
   * Effectuez une itération à l’aide du `Map` pour récupérer la conception de formulaire assemblée. Transformer le de ce membre du tableau `value` à `BLOB`. Transmettez `BLOB` au service Output.


1. Utilisez le service Output pour générer le document du PDF.

   Appeler la variable `OutputServiceClient` de `generatePDFOutput2` et transmettez les valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Une valeur string qui spécifie la racine de contenu où se trouvent les ressources supplémentaires, telles que les images.
   * A `BLOB` qui représente la conception de formulaire (utilisez l’objet `BLOB` instance renvoyée par le service Assembler).
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `BLOB` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.
   * Une sortie `BLOB` qui `generatePDFOutput2` renseigne . Le `generatePDFOutput2` renseigne cet objet avec des métadonnées générées qui décrivent le document. (This parameter value is required only for web service invocation).
   * Une sortie `OutputResult` contenant les résultats de l’opération. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).

   Le `generatePDFOutput2` renvoie une `BLOB` contenant le formulaire de PDF non interactif.

1. Enregistrez le document du PDF en tant que fichier de PDF.

   * Create a `System.IO.FileStream` object by invoking its constructor. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF interactif et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` récupéré à partir de l’objet `generatePDFOutput2` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Impression dans des fichiers {#printing-to-files}

Vous pouvez utiliser le service Output pour imprimer des flux tels que PostScript, PCL (Printer Control Language) ou les formats d’étiquette suivants dans un fichier :

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Le service Output vous permet de fusionner des données XML avec une conception de formulaire et d’imprimer le formulaire dans un fichier. L’illustration suivante présente le service Output créant des fichiers laser et d’étiquettes.

>[!NOTE]
>
>Pour plus d’informations sur l’envoi de diffusions d’impression vers des imprimantes, voir [Envoi de flux d’impression aux imprimantes](creating-document-output-streams.md#sending-print-streams-to-printers).

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-5}

Pour imprimer sur un fichier, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet client de sortie.
1. Référencez une source de données XML.
1. Définissez les options d’exécution d’impression requises pour l’impression dans un fichier.
1. Imprimer le flux d’impression dans un fichier.
1. Récupérez les résultats de l’opération.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé. (Voir [Inclusion des fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)

**Création d’un objet client de sortie**

Avant d’effectuer une opération de service Output par programmation, vous devez créer un objet client de service Output. Si vous utilisez l’API Java, créez une `OutputClient` . Si vous utilisez l’API du service Web d’Output, créez une `OutputServiceService` .

**Référence à une source de données XML**

Pour imprimer un document contenant des données, vous devez référencer une source de données XML contenant des éléments XML pour chaque champ de formulaire à remplir avec des données. Le nom de l’élément XML doit correspondre au nom du champ. Un élément XML est ignoré s’il ne correspond pas à un champ de formulaire ou si le nom de l’élément XML ne correspond pas au nom du champ. Il n&#39;est pas nécessaire de correspondre à l&#39;ordre dans lequel les éléments XML sont affichés si tous les éléments XML sont spécifiés.

**Définition des options d’exécution d’impression requises pour l’impression dans un fichier**

Pour imprimer sur un fichier, vous devez définir l’option d’exécution File URI en spécifiant l’emplacement et le nom du fichier sur lequel le service Output imprime. Par exemple, pour demander au service Output d’imprimer un fichier PostScript nommé *MortgageForm.ps* pour C:\Adobe, indiquez C:\Adobe\MortgageForm.ps.

>[!NOTE]
>
>Vous pouvez définir des options d’exécution facultatives. Pour plus d’informations sur toutes les options que vous pouvez définir, voir `PrintedOutputOptionsSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Imprimer le flux d’impression dans un fichier**

Après avoir référencé une source de données XML valide contenant des données de formulaire et défini les options d’exécution d’impression, vous pouvez appeler le service Output, ce qui entraîne l’impression d’un fichier.

**Récupération des résultats de l’opération**

Une fois que le service Output a effectué une opération, il renvoie divers éléments de données, tels que des données XML, qui indiquent si l’opération a réussi.

**Voir également**

[Imprimer dans des fichiers à l’aide de l’API Java](creating-document-output-streams.md#print-to-files-using-the-java-api)

[Imprimer dans des fichiers à l’aide de l’API de service Web](creating-document-output-streams.md#print-to-files-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Imprimer dans des fichiers à l’aide de l’API Java {#print-to-files-using-the-java-api}

Imprimer dans un fichier à l’aide de l’API Output (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-output-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet client de sortie.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez une source de données XML.

   * Créez un `java.io.FileInputStream` qui représente la source de données XML utilisée pour remplir le document en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier XML.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définissez les options d’exécution d’impression requises pour l’impression dans un fichier.

   * Créez un objet `PrintedOutputOptionsSpec` en utilisant son constructeur.
   * Spécifiez le fichier en appelant le de l’objet PrintedOutputOptionsSpec `setFileURI` et transmettre une valeur string qui représente le nom et l’emplacement du fichier. Par exemple, si vous souhaitez que le service Output s’imprime dans un fichier PostScript nommé* MortgageForm.ps* situé dans C:\Adobe, spécifiez C:\\Adobe\MortgageForm.ps.
   * Indiquez le nombre de copies à imprimer en appelant la fonction `PrintedOutputOptionsSpec` de `setCopies` et transmettre une valeur entière représentant le nombre de copies.

1. Imprimer le flux d’impression dans un fichier.

   Imprimer dans un fichier en appelant le `OutputClient` de `generatePrintedOutput` et transmission des valeurs suivantes :

   * A `PrintFormat` valeur d’énumération spécifiant le format de flux d’impression à créer. Par exemple, pour créer un flux d’impression PostScript, transmettez `PrintFormat.PostScript`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie l’emplacement des fichiers collatéraux associés, tels que les fichiers image.
   * Une valeur string qui spécifie l’emplacement du fichier XDC à utiliser (vous pouvez transmettre `null` si vous avez spécifié le fichier XDC à utiliser à l’aide de la variable `PrintedOutputOptionsSpec` ).
   * Le `PrintedOutputOptionsSpec` contenant les options d’exécution requises pour l’impression dans un fichier.
   * Le `com.adobe.idp.Document` contenant la source de données XML contenant les données de formulaire.

   Le `generatePrintedOutput` renvoie une `OutputResult` contenant les résultats de l’opération.

   >[!NOTE]
   >
   >Le `OutputResult` de `getRecordLevelMetaDataList` method renvoie `null`*. *

1. Récupérez les résultats de l’opération.

   * Créez un `com.adobe.idp.Document` qui représente l’état de la propriété `generatePrintedOutput` en appelant la méthode `OutputResult` de `getStatusDoc` (la méthode `OutputResult` a été renvoyé par la fonction `generatePrintedOutput` ).
   * Créez un `java.io.File` qui contiendra les résultats de l’opération. Assurez-vous que l’extension de fichier est XML.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` dans le fichier (assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui a été renvoyé par l’objet `getStatusDoc` ).

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode SOAP) : Impression dans un fichier à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-printing-to-a-file-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Imprimer dans des fichiers à l’aide de l’API de service Web {#print-to-files-using-the-web-service-api}

Imprimer dans un fichier à l’aide de l’API Output (service Web) :

1. Inclure les fichiers de projet.

   Create a Microsoft .NET project that uses MTOM. Ensure that you use the following WSDL definition: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost`* avec l’adresse IP du serveur hébergeant AEM Forms. *

1. Créez un objet client de sortie.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Créez un `OutputServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez une source de données XML.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour stocker des données de formulaire.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier XML contenant les données de formulaire.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `binaryData` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution d’impression requises pour l’impression dans un fichier.

   * Créez un objet `PrintedOutputOptionsSpec` en utilisant son constructeur.
   * Spécifiez le fichier en attribuant une valeur string qui représente l’emplacement et le nom du fichier au `PrintedOutputOptionsSpec` de `fileURI` membre de données. For example, if you want the Output service to print to a PostScript file named *MortgageForm.ps* located in C:\Adobe, specify C:\\Adobe\MortgageForm.ps.
   * Indiquez le nombre de copies à imprimer en attribuant une valeur entière qui représente le nombre de copies au `PrintedOutputOptionsSpec` de `copies` membres des données.

1. Imprimer le flux d’impression dans un fichier.

   Imprimer dans un fichier en appelant le `OutputServiceService` de `generatePrintedOutput` et transmission des valeurs suivantes :

   * A `PrintFormat` valeur d’énumération spécifiant le format de flux d’impression à créer. Par exemple, pour créer un flux d’impression PostScript, transmettez `PrintFormat.PostScript`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie l’emplacement des fichiers collatéraux associés, tels que les fichiers image.
   * A string value that specifies the location of the XDC file to use (you can pass `null` if you specified the XDC file to use by using the `PrintedOutputOptionsSpec` object).
   * Le `PrintedOutputOptionsSpec` contenant les options d’exécution d’impression requises pour l’impression dans un fichier.
   * Le `BLOB` contenant la source de données XML contenant les données de formulaire.
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec des métadonnées générées qui décrivent le document. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec les données de résultat. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)
   * Un `OutputResult` contenant les résultats de l’opération. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)

1. Récupérez les résultats de l’opération.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente un emplacement de fichier XML contenant les données de résultat. Assurez-vous que l’extension de fichier est XML.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renseigné avec les données de résultat de la fonction `OutputServiceService` de `generatePDFOutput` (le huitième paramètre). Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans le fichier XML en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Envoi de flux d’impression aux imprimantes {#sending-print-streams-to-printers}

Vous pouvez utiliser le service Output pour envoyer des flux d’impression tels que PostScript, PCL (Printer Control Language) ou les formats d’étiquettes suivants aux imprimantes réseau :

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Le service Output vous permet de fusionner des données XML avec une conception de formulaire et de générer le formulaire en tant que flux d’impression. Vous pouvez par exemple créer un flux d’impression PostScript et l’envoyer à une imprimante réseau. L’illustration suivante présente le service Output qui envoie des flux d’impression aux imprimantes réseau.

>[!NOTE]
>
>Pour montrer comment envoyer un flux d’impression à une imprimante réseau, cette section envoie un flux d’impression PostScript à une imprimante réseau à l’aide du protocole de l’imprimante partagée.

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-6}

Pour envoyer un flux d’impression à une imprimante réseau, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet client de sortie.
1. Référencez une source de données XML.
1. Définition des options d’exécution d’impression
1. Récupérez un document à imprimer.
1. Envoyez le document à une imprimante réseau.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utility.jar (Obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (requis si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un objet client de sortie**

Avant d’effectuer une opération de service Output par programmation, créez un objet client de service Output. Si vous utilisez l’API Java, créez une `OutputClient` . Si vous utilisez l’API du service Web d’Output, créez une `OutputServiceClient` .

**Référence à une source de données XML**

Pour imprimer un document contenant des données, vous devez référencer une source de données XML contenant des éléments XML pour chaque champ de formulaire à remplir avec des données. Le nom de l’élément XML doit correspondre au nom du champ. Un élément XML est ignoré s’il ne correspond pas à un champ de formulaire ou si le nom de l’élément XML ne correspond pas au nom du champ. Il n&#39;est pas nécessaire de correspondre à l&#39;ordre dans lequel les éléments XML sont affichés si tous les éléments XML sont spécifiés.

**Définition des options d’exécution d’impression**

Vous pouvez définir les options d’exécution lors de l’envoi d’un flux d’impression vers une imprimante, notamment les options suivantes :

* **Copies**: Indique le nombre de copies à envoyer à l’imprimante. La valeur par défaut est 1.
* **Staple**: Une option XCI est définie lorsqu’un agrafeur est utilisé. Cette option peut être spécifiée dans le modèle de configuration par l’élément de base et est utilisée uniquement pour les imprimantes PS et PCL.
* **OutputJog**: Une option XCI est définie lorsque les pages de sortie doivent être jolies (physiquement décalées dans le bac de sortie). Cette option est réservée aux imprimantes PS et PCL.
* **OutputBin**: Valeur XCI utilisée pour permettre au pilote d’impression de sélectionner la corbeille de sortie appropriée.

>[!NOTE]
>
>Pour plus d’informations sur toutes les options d’exécution que vous pouvez définir, voir `PrintedOutputOptionsSpec` référence de classe.

**Récupération d’un document à imprimer**

Récupérez un flux d’impression à envoyer à une imprimante. Par exemple, vous pouvez récupérer un fichier PostScript et l’envoyer à une imprimante.

Vous pouvez choisir d’envoyer un fichier de PDF si votre imprimante prend en charge PDF. Cependant, l’envoi d’un document de PDF à une imprimante pose un problème : chaque fabricant de l’imprimante dispose d’une mise en oeuvre différente de l’interpréteur de PDF. C&#39;est-à-dire que certains imprimeurs utilisent l&#39;interprétation d&#39;Adobe PDF, mais cela dépend de l&#39;imprimante. D&#39;autres imprimeurs ont leur propre interprète PDF. Par conséquent, les résultats de l’impression peuvent varier.

Une autre limitation de l’envoi d’un document de PDF à une imprimante réside dans le fait qu’il s’agit seulement d’impressions ; il ne peut pas accéder aux options recto verso, sélection de bac à papier et agrafage, à l’exception des paramètres de l’imprimante.

Pour récupérer un document à imprimer, vous utilisez le `generatePrintedOutput` . Le tableau suivant spécifie les types de contenu définis pour un flux d’impression donné lors de l’utilisation de la variable `generatePrintedOutput` .

<table> 
 <thead> 
  <tr> 
   <th><p>Format d’impression </p></th> 
   <th><p>Description</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>DPL </p></td> 
   <td><p>Crée un flux de sortie xdc dpl203.xdc par défaut ou personnalisé.</p></td> 
  </tr> 
  <tr> 
   <td><p>DPL 300 DPI </p></td> 
   <td><p>Crée un flux de sortie DPL 300 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>DPL 406 DPI </p></td> 
   <td><p>Crée un flux de sortie DPL 400 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>DPL 600 DPI </p></td> 
   <td><p>Crée un flux de sortie DPL 600 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>GenericColorPCL </p></td> 
   <td><p>Crée un flux de sortie PCL (5c) de couleur générique.</p></td> 
  </tr> 
  <tr> 
   <td><p>GenericPSLevel3 </p></td> 
   <td><p>Crée un flux de sortie PostScript de niveau 3 générique.</p></td> 
  </tr> 
  <tr> 
   <td><p>IPL </p></td> 
   <td><p>Crée un flux de sortie IPL personnalisé.</p></td> 
  </tr> 
  <tr> 
   <td><p>IPL 300 DPI </p></td> 
   <td><p>Creates a IPL 300 DPI output stream.</p></td> 
  </tr> 
  <tr> 
   <td><p>IPL 400 DPI </p></td> 
   <td><p>Crée un flux de sortie IPL 400 ppp.</p></td> 
  </tr> 
  <tr> 
   <td><p>PCL </p></td> 
   <td><p>Crée un flux de sortie Generic Monochrome PCL (5e).</p></td> 
  </tr> 
  <tr> 
   <td><p>PostScript </p></td> 
   <td><p>Crée un flux de sortie PostScript de niveau 2 générique.</p></td> 
  </tr> 
  <tr> 
   <td><p>TPCL </p></td> 
   <td><p>Crée un flux de sortie TPCL personnalisé.</p></td> 
  </tr> 
  <tr> 
   <td><p>TPCL 305 DPI </p></td> 
   <td><p>Crée un flux de sortie TPCL 305 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>TPCL 600 DPI </p></td> 
   <td><p>Crée un flux de sortie TPCL 600 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>ZPL </p></td> 
   <td><p>Crée un flux de sortie ZPL 203 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>ZPL 300 DPI </p></td> 
   <td><p>Crée un flux de sortie ZPL 300 DPI.</p></td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Vous pouvez également envoyer un flux d’impression à une imprimante à l’aide de la méthode `generatePrintedOutput2` . Toutefois, les démarrages rapides associés à la section Envoi de flux d’impression aux imprimantes utilisent la variable `generatePrintedOutput` .

**Envoi du flux d’impression vers une imprimante réseau**

Après avoir récupéré un document à imprimer, vous pouvez appeler le service Output, ce qui entraîne l’envoi d’un flux d’impression vers une imprimante réseau. Pour que le service Output localise correctement l’imprimante, vous devez spécifier le serveur d’impression et le nom de l’imprimante. En outre, vous devez également spécifier le protocole d’impression.

>[!NOTE]
>
>Si PDFG est installé sur le serveur Forms et que le serveur s’exécute sur Windows Server 2008, vous ne pouvez pas utiliser la propriété SharedPrinter . Dans ce cas, utilisez un protocole d’imprimante différent.

>[!NOTE]
>
>Si vous utilisez une imprimante réseau et que le mécanisme d’accès est SharedPrinter, vous devez spécifier le chemin réseau complet de l’imprimante. Envoyez un flux d’impression vers une imprimante réseau à l’aide de l’API Java.

Envoyez un flux d’impression à une imprimante réseau à l’aide de l’API Output (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-output-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet client de sortie

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référence à une source de données XML

   * Créez un `java.io.FileInputStream` qui représente la source de données XML utilisée pour remplir le document en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier XML.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définition des options d’exécution d’impression

   Créez un `PrintedOutputOptionsSpec` qui représente les options d’exécution d’impression. Par exemple, vous pouvez spécifier le nombre de copies à imprimer en appelant la variable `PrintedOutputOptionsSpec` de `setCopies` .

   >[!NOTE]
   >
   >Vous ne pouvez pas définir la valeur de pagination en utilisant la variable `PrintedOutputOptionsSpec` de `setPagination` si vous générez un flux d’impression ZPL. De même, vous ne pouvez pas définir les options suivantes pour un flux d’impression ZPL : OutputJog, PageOffset et Staple. Le `setPagination`* n’est pas valide pour la génération PostScript. Il est valide uniquement pour la génération PCL. *

1. Récupération d’un document à imprimer

   * Récupération d’un document à imprimer en appelant la fonction `OutputClient` de `generatePrintedOutput` et transmission des valeurs suivantes :

      * A `PrintFormat` valeur d’énumération qui spécifie le flux d’impression. Par exemple, pour créer un flux d’impression PostScript, transmettez `PrintFormat.PostScript`.
      * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
      * Une valeur string qui spécifie l’emplacement des fichiers collatéraux associés, tels que les fichiers image.
      * Une valeur string qui spécifie l’emplacement du fichier XDC à utiliser.
      * Le `PrintedOutputOptionsSpec` contenant les options d’exécution requises pour être imprimé dans un fichier.
      * Le `com.adobe.idp.Document` qui représente la source de données XML contenant les données de formulaire à fusionner avec la conception de formulaire.

      Cette méthode renvoie une `OutputResult` contenant les résultats de l’opération.

   * Créez un `com.adobe.idp.Document` à envoyer à l’imprimante en appelant la méthode `OutputResult` object ‘s `getGeneratedDoc` . Cette méthode renvoie une `com.adobe.idp.Document` .


1. Envoi du flux d’impression vers une imprimante réseau

   Envoyez le flux d’impression à une imprimante réseau en appelant la méthode `OutputClient` de `sendToPrinter` et transmission des valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le flux d’impression à envoyer à l’imprimante.
   * A `PrinterProtocol` valeur d’énumération spécifiant le protocole d’imprimante à utiliser. Par exemple, pour spécifier le protocole SharedPrinter, transmettez `PrinterProtocol.SharedPrinter`.
   * Une valeur string qui spécifie le nom du serveur d’impression. Par exemple, en supposant que le nom du serveur d’impression soit PrintServer1, transmettez `\\\PrintSever1`.
   * Une valeur string qui spécifie le nom de l’imprimante. Par exemple, en supposant que le nom de l’imprimante soit Printer1, transmettez `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >Le `sendToPrinter` a été ajoutée à l’API AEM Forms dans la version 8.2.1.

### Envoi d’un flux d’impression vers une imprimante à l’aide de l’API du service Web {#send-a-print-stream-to-a-printer-using-the-web-service-api}

Envoyez un flux d’impression à une imprimante réseau à l’aide de l’API Output (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost`* avec l’adresse IP du serveur hébergeant AEM Forms. *

1. Créez un objet client de sortie.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Créez un `OutputServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez une source de données XML.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour stocker des données de formulaire.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du fichier XML qui contient les données de formulaire.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Déterminez la longueur du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution d’impression.

   Créez un objet `PrintedOutputOptionsSpec` en utilisant son constructeur. Par exemple, vous pouvez spécifier le nombre de copies à imprimer en attribuant une valeur entière qui représente le nombre de copies au `PrintedOutputOptionsSpec` de `copies` membre de données.

   >[!NOTE]
   >
   >Vous ne pouvez pas définir la valeur de pagination en utilisant la variable `PrintedOutputOptionsSpec` de `pagination` membre de données si vous générez un flux d’impression ZPL. De même, vous ne pouvez pas définir les options suivantes pour un flux d’impression ZPL : OutputJog, PageOffset et Staple. Le `pagination`* Le membre de données n’est pas valide pour la génération PostScript. Il est valide uniquement pour la génération PCL. *

1. Récupérez un document à imprimer.

   * Récupération d’un document à imprimer en appelant la fonction `OutputServiceService` de `generatePrintedOutput` et transmission des valeurs suivantes :

      * A `PrintFormat` valeur d’énumération qui spécifie le flux d’impression. Par exemple, pour créer un flux d’impression PostScript, transmettez `PrintFormat.PostScript`.
      * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
      * Une valeur string qui spécifie l’emplacement des fichiers collatéraux associés, tels que les fichiers image.
      * Une valeur string qui spécifie l’emplacement du fichier XDC à utiliser.
      * Le `PrintedOutputOptionsSpec` contenant les options d’exécution d’impression utilisées lors de l’envoi d’un flux d’impression vers une imprimante réseau.
      * Le `BLOB` contenant la source de données XML contenant les données de formulaire.
      * A `BLOB` qui est renseigné par la variable `generatePrintedOutput` . Le `generatePrintedOutput` renseigne cet objet avec des métadonnées générées qui décrivent le document. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)
      * A `BLOB` qui est renseigné par la variable `generatePrintedOutput` . Le `generatePrintedOutput` renseigne cet objet avec les données de résultat. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)
      * Un `OutputResult` contenant les résultats de l’opération. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)
   * Créez un `BLOB` à envoyer à l’imprimante en obtenant la valeur de la propriété `OutputResult` object ‘s `generatedDoc` . Cette méthode renvoie une `BLOB` qui contient des données PostScript renvoyées par l’objet `generatePrintedOutput` .


1. Envoyez le flux d’impression à une imprimante réseau.

   Envoyez le flux d’impression à une imprimante réseau en appelant la méthode `OutputClient` de `sendToPrinter` et transmission des valeurs suivantes :

   * A `BLOB` qui représente le flux d’impression à envoyer à l’imprimante.
   * A `PrinterProtocol` valeur d’énumération spécifiant le protocole d’imprimante à utiliser. Par exemple, pour spécifier le protocole SharedPrinter, transmettez `PrinterProtocol.SharedPrinter`.
   * A `bool` qui spécifie s’il faut utiliser la valeur du paramètre précédent. Transmettre la valeur `true`. (Cette valeur de paramètre est requise pour l’appel de service Web uniquement.)
   * Une valeur string qui spécifie le nom du serveur d’impression. Par exemple, en supposant que le nom du serveur d’impression soit PrintServer1, transmettez `\\\PrintSever1`.
   * Une valeur string qui spécifie le nom de l’imprimante. Par exemple, en supposant que le nom de l’imprimante soit Printer1, transmettez `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >Le `sendToPrinter` a été ajoutée à l’API AEM Forms dans la version 8.2.1.

## Création de plusieurs fichiers de sortie {#creating-multiple-output-files}

Le service Output peut créer des documents distincts pour chaque enregistrement d’une source de données XML ou d’un seul fichier contenant tous les enregistrements (cette fonctionnalité est la valeur par défaut). Supposons, par exemple, que dix enregistrements se trouvent dans une source de données XML et que vous enseigniez au service Output de créer des documents PDF distincts (ou d’autres types de sortie) pour chaque enregistrement à l’aide de l’API Output Service. Par conséquent, le service Output génère dix documents PDF. (Au lieu de créer des documents, vous pouvez envoyer plusieurs flux d’impression à une imprimante.)

L’illustration suivante présente également le service Output qui traite un fichier de données XML contenant plusieurs enregistrements. Cependant, supposons que vous enseigniez au service Output de créer un document de PDF unique contenant tous les enregistrements de données. Dans ce cas, le service Output génère un document contenant tous les enregistrements.

L’illustration suivante présente le service Output qui traite un fichier de données XML contenant plusieurs enregistrements. Supposons que vous enseigniez au service Output de créer un document de PDF distinct pour chaque enregistrement de données. Dans ce cas, le service Output génère un document de PDF distinct pour chaque enregistrement de données.

![cm_outputbatchmany](assets/cm_outputbatchmany.png)

Les données XML suivantes présentent un exemple de fichier de données contenant trois enregistrements de données.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <batch> 
 <LoanRecord> 
     <mortgageAmount>500000</mortgageAmount> 
     <lastName>Blue</lastName> 
     <firstName>Tony</firstName> 
     <SSN>555666777</SSN> 
     <PositionTitle>Product Manager</PositionTitle> 
     <Address>555 No Where Dr</Address> 
     <City>New York</City> 
     <StateProv>New York</StateProv> 
     <ZipCode>51256</ZipCode> 
     <Email>TBlue@NoMailServer.com</Email> 
     <PhoneNum>555-7418</PhoneNum> 
     <FaxNum>555-9981</FaxNum> 
     <Description>Buy a home</Description> 
 </LoanRecord> 
 <LoanRecord> 
     <mortgageAmount>300000</mortgageAmount> 
     <lastName>White</lastName> 
     <firstName>Sam</firstName> 
     <SSN>555666222</SSN> 
     <PositionTitle>Program Manager</PositionTitle> 
     <Address>557 No Where Dr</Address> 
     <City>New York</City> 
     <StateProv>New York</StateProv> 
     <ZipCode>51256</ZipCode> 
     <Email>SWhite@NoMailServer.com</Email> 
     <PhoneNum>555-7445</PhoneNum> 
     <FaxNum>555-9986</FaxNum> 
     <Description>Buy a home</Description> 
 </LoanRecord> 
 <LoanRecord> 
     <mortgageAmount>700000</mortgageAmount> 
     <lastName>Green</lastName> 
     <firstName>Steve</firstName> 
     <SSN>55566688</SSN> 
     <PositionTitle>Project Manager</PositionTitle> 
     <Address>445 No Where Dr</Address> 
     <City>New York</City> 
     <StateProv>New York</StateProv> 
     <ZipCode>51256</ZipCode> 
     <Email>SGreeb@NoMailServer.com</Email> 
     <PhoneNum>555-2211</PhoneNum> 
     <FaxNum>555-2221</FaxNum> 
     <Description>Buy a home</Description> 
 </LoanRecord> 
 </batch>
```

Notez que l’élément XML qui démarre et termine chaque enregistrement de données est `LoanRecord`. Cet élément XML est référencé par la logique de l’application qui génère plusieurs fichiers.

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-7}

Pour créer plusieurs fichiers de PDF en fonction d’une source de données XML, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet client de sortie.
1. Référencez une source de données XML.
1. Définissez les options d’exécution du PDF.
1. Définissez les options d’exécution de rendu.
1. Générez plusieurs fichiers PDF.
1. Récupérez les résultats de l’opération.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un objet client de sortie**

Avant d’effectuer une opération de service Output par programmation, vous devez créer un objet client de service Output. Si vous utilisez l’API Java, créez une `OutputClient` . Si vous utilisez l’API du service Web d’Output, créez une `OutputServiceService` .

**Référence à une source de données XML**

Référencez une source de données XML qui contient plusieurs enregistrements. Un élément XML doit être utilisé pour séparer les enregistrements de données. Par exemple, dans l’exemple de source de données XML illustré précédemment dans cette section, l’élément XML qui sépare les enregistrements de données est nommé `LoanRecord`.

Un élément XML doit exister pour chaque champ de formulaire à renseigner avec des données. Le nom de l’élément XML doit correspondre au nom du champ. Un élément XML est ignoré s’il ne correspond pas à un champ de formulaire ou si le nom de l’élément XML ne correspond pas au nom du champ. Il n&#39;est pas nécessaire de correspondre à l&#39;ordre dans lequel les éléments XML sont affichés si tous les éléments XML sont spécifiés.

**Définition des options d’exécution du PDF**

Vous devez définir les options d’exécution suivantes pour que le service Output puisse créer plusieurs fichiers en fonction d’une source de données XML :

* **De nombreux fichiers**: Indique si le service Output crée un ou plusieurs documents. Vous pouvez spécifier true ou false. Pour créer un document distinct pour chaque enregistrement de données dans la source de données XML, indiquez true.
* **URI du fichier**: Indique l’emplacement des fichiers générés par le service Output. Supposons, par exemple, que vous souhaitiez spécifier C:\\Adobe\forms\Loan.pdf. Dans ce cas, le service Output crée un fichier nommé Loan.pdf et le place dans le dossier C:\\Adobe\forms folder. S’il existe plusieurs fichiers, les noms sont Loan0001.pdf, Loan0002.pdf, Loan0003.pdf, etc. Si vous indiquez un emplacement de fichier, les fichiers sont placés sur le serveur, et non sur l’ordinateur client.
* **Record Name**: Spécifie le nom de l’élément XML dans la source de données qui sépare les enregistrements de données. Par exemple, dans l’exemple de source de données XML illustré plus haut dans cette section, l’élément XML qui sépare les enregistrements de données est appelé `LoanRecord`. (Au lieu de définir l’option d’exécution Nom d’enregistrement, vous pouvez définir le niveau d’enregistrement en lui affectant une valeur numérique qui indique le niveau d’élément qui contient les enregistrements de données. Cependant, vous ne pouvez définir que le Nom de l’enregistrement ou le Niveau d’enregistrement. Vous ne pouvez pas définir les deux valeurs.)

**Définition des options d’exécution de rendu**

Vous pouvez définir des options d’exécution de rendu lors de la création de plusieurs fichiers. Bien que ces options ne soient pas requises (contrairement aux options d’exécution de sortie, qui sont requises), vous pouvez effectuer des tâches telles que l’amélioration des performances du service Output. Par exemple, vous pouvez mettre en cache la conception de formulaire utilisée par le service Output pour améliorer les performances.

Lorsque le service Output traite les enregistrements par lots, il lit les données qui contiennent plusieurs enregistrements de manière incrémentielle. En d’autres termes, le service Output lit les données en mémoire et les libère au fur et à mesure du traitement du lot d’enregistrements. Le service Output charge les données de manière incrémentielle lorsque l’une des deux options d’exécution est définie. Si vous définissez l’option d’exécution Nom d’enregistrement , le service Output lit les données de manière incrémentielle. De même, si vous définissez l’option d’exécution Niveau d’enregistrement sur 2 ou plus, le service Output lit les données de manière incrémentielle.

Vous pouvez contrôler si le service Output effectue un chargement incrémentiel à l’aide de la variable `PDFOutputOptionsSpec` ou le `PrintedOutputOptionSpec` de `setLazyLoading` . Vous pouvez transmettre la valeur `false` à cette méthode qui désactive le chargement incrémentiel.

**Génération de plusieurs fichiers de PDF**

Après avoir référencé une source de données XML valide contenant plusieurs enregistrements de données et défini des options d’exécution, vous pouvez appeler le service Output, ce qui entraîne la génération de plusieurs fichiers. Lors de la génération de plusieurs enregistrements, la variable `OutputResult` de `getGeneratedDoc` method renvoie `null`.

**Récupération des résultats de l’opération**

Une fois que le service Output a effectué une opération, il renvoie des données XML spécifiant si l’opération a réussi. Le code XML suivant est renvoyé par le service Output. Dans ce cas, le service Output a généré 42 documents.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <printResult> 
 <status>0</status> 
 <requestId>4ad85f9e2</requestId> 
 <context/> 
 <messages> 
 <message>Printed all 42 records successfully.</message> 
 </messages> 
 <printSpec> 
 <input> 
 <validated>true</validated> 
 <dataFile recordIdField="" recordLevel="0" recordName="LoanRecord"/> 
 <sniffRules lookAhead="300"/> 
 <formDesign>Loan.xdp</formDesign> 
 <contentRoot>C:\Adobe</contentRoot> 
 <metadata-spec record="false"/> 
 </input> 
 <output> 
 <format>PDF</format> 
 <fileURI>C:\Adobe\forms\Loan.pdf</fileURI> 
 <optionString>cacheenabled=true&padebug=false&linearpdf=false&pdfarevisionnumber=1&pdfaconformance=A&taggedpdf=false&TransactionTimeOut=180</optionString> 
 <waitForResponse>true</waitForResponse> 
 <outputStream>multiple</outputStream> 
 </output> 
 </printSpec> 
 </printResult>
```

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Création de plusieurs fichiers de PDF à l’aide de l’API Java {#create-multiple-pdf-files-using-the-java-api}

Créez plusieurs fichiers PDF à l’aide de l’API Output (Java) :

1. Inclure les fichiers de projet&quot;

   Incluez les fichiers JAR client, tels que adobe-output-client.jar, dans le chemin de classe de votre projet Java. .

1. Création d’un objet client de sortie

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référence à une source de données XML

   * Créez un `java.io.FileInputStream` qui représente la source de données XML contenant plusieurs enregistrements en utilisant son constructeur et en transmettant une valeur string spécifiant l’emplacement du fichier XML.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définition des options d’exécution du PDF

   * Créez un objet `PDFOutputOptionsSpec` en utilisant son constructeur.
   * Définissez l’option Plusieurs fichiers en appelant la méthode `PDFOutputOptionsSpec` de `setGenerateManyFiles` . Par exemple, transmettez la valeur `true` pour demander au service Output de créer un fichier de PDF distinct pour chaque enregistrement de la source de données XML. (Si vous transmettez `false`, le service Output génère un seul document de PDF qui contient tous les enregistrements).
   * Définissez l’option File URI en appelant la méthode `PDFOutputOptionsSpec` de `setFileUri` et transmission d’une valeur string qui spécifie l’emplacement des fichiers générés par le service Output. L’option File URI est relative au serveur d’applications J2EE hébergeant AEM Forms, et non à l’ordinateur client.
   * Définissez l’option Record Name (Nom d’enregistrement) en appelant la méthode `OutputOptionsSpec` de `setRecordName` et transmettre une valeur string qui spécifie le nom de l’élément XML dans la source de données qui sépare les enregistrements de données. (Prenons l’exemple de la source de données XML présentée plus haut dans cette section. Le nom de l’élément XML qui sépare les enregistrements de données est LoanRecord).

1. Définition des options d’exécution de rendu

   * Créez un objet `RenderOptionsSpec` en utilisant son constructeur.
   * Mettez en cache la conception de formulaire pour améliorer les performances du service Output en appelant la fonction `RenderOptionsSpec` de `setCacheEnabled` et transmission d’une `Boolean` valeur de `true`.

1. Génération de plusieurs fichiers de PDF

   Générez plusieurs fichiers PDF en appelant la fonction `OutputClient` de `generatePDFOutput` et transmission des valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie la racine de contenu où se trouve la conception de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `com.adobe.idp.Document` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.

   Le `generatePDFOutput` renvoie une `OutputResult` contenant les résultats de l’opération.

1. Récupération des résultats de l’opération

   * Créez un `java.io.File` qui représente un fichier XML qui contiendra les résultats de l’objet `generatePDFOutput` . Assurez-vous que l’extension de nom de fichier est .xml.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` dans le fichier (assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui a été renvoyé par l’objet `applyUsageRights` ).

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode EJB) : Création de plusieurs fichiers PDF à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-multiple-pdf-files-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Création de plusieurs fichiers de PDF à l’aide de l’API de service Web {#create-multiple-pdf-files-using-the-web-service-api}

Créez plusieurs fichiers PDF à l’aide de l’API Output (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet client de sortie.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Créez un `OutputServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez une source de données XML.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker des données de formulaire contenant plusieurs enregistrements.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier XML qui contient plusieurs enregistrements.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution du PDF.

   * Créez un objet `PDFOutputOptionsSpec` en utilisant son constructeur.
   * Définissez l’option Multiple Files en attribuant une valeur booléenne à la variable `OutputOptionsSpec` de `generateManyFiles` membre de données. Par exemple, affectez la valeur `true` à ce membre de données pour demander au service Output de créer un fichier de PDF distinct pour chaque enregistrement de la source de données XML. (Si vous affectez `false` à ce membre de données, le service Output génère un seul PDF (contenant tous les enregistrements).
   * Définissez l’option d’URI de fichier en attribuant une valeur string qui spécifie l’emplacement du ou des fichiers générés par le service Output à la variable `OutputOptionsSpec` de `fileURI` membre de données. L’option File URI est relative au serveur d’applications J2EE hébergeant AEM Forms, et non à l’ordinateur client.
   * Définissez l’option de nom d’enregistrement en attribuant une valeur string qui spécifie le nom de l’élément XML dans la source de données qui sépare les enregistrements de données à la valeur `OutputOptionsSpec` de `recordName` membre de données.
   * Définissez l’option Copies en attribuant une valeur entière qui spécifie le nombre de copies générées par le service Output à la variable `OutputOptionsSpec` de `copies` membre de données.

1. Définissez les options d’exécution de rendu.

   * Créez un objet `RenderOptionsSpec` en utilisant son constructeur.
   * Mettre en cache la conception de formulaire pour améliorer les performances du service Output en affectant la valeur `true` au `RenderOptionsSpec` de `cacheEnabled` membre de données.

1. Générez plusieurs fichiers PDF.

   Créez plusieurs fichiers de PDF en appelant la méthode `OutputServiceService` de `generatePDFOutput`et transmission des valeurs suivantes :

   * Une valeur d’énumération TransformationFormat . Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie la racine de contenu où se trouve la conception de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `BLOB` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec des métadonnées générées qui décrivent le document.
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec les données de résultat.
   * Un `OutputResult` contenant les résultats de l’opération.

1. Récupération des résultats de l’opération

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente un emplacement de fichier XML contenant les données de résultat. Assurez-vous que l’extension de nom de fichier est .xml.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renseigné avec les données de résultat de la fonction `OutputServiceService` de `generatePDFOutput` (le huitième paramètre). Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `binaryData` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans le fichier XML en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Création de règles de recherche {#creating-search-rules}

Vous pouvez créer des règles de recherche pour que le service Output examine les données d’entrée et utilise différentes conceptions de formulaire basées sur le contenu des données pour générer la sortie. Par exemple, si le texte *hypothèque* se trouve dans les données d’entrée, puis le service Output peut utiliser une conception de formulaire nommée Mortgage.xdp. De même, si le texte *automobile* se trouve dans les données d’entrée, puis le service Output peut utiliser une conception de formulaire enregistrée sous le nom AutomobileLoan.xdp. Bien que le service Output puisse générer différents types de sortie, cette section suppose que le service Output génère un fichier PDF. Le diagramme suivant illustre le service Output qui génère un fichier de PDF en traitant un fichier de données XML et en utilisant l’une des nombreuses conceptions de formulaire.

En outre, le service Output peut générer des packages de documents, où plusieurs enregistrements sont fournis dans le jeu de données et où chaque enregistrement est associé à une conception de formulaire et où un seul document est généré avec plusieurs conceptions de formulaire.

![cs_outputbatchmanyformdesigns2](assets/cs_outputbatchmanyformdesigns2.png)

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-8}

Pour demander au service Output d’utiliser des règles de recherche lors de la génération d’un document, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet client de sortie.
1. Référencez une source de données XML.
1. Définissez des règles de recherche.
1. Définissez les options d’exécution du PDF.
1. Définissez les options d’exécution de rendu.
1. Générez un document de PDF.
1. Récupérez les résultats de l’opération.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utility.jar (Obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (requis si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBoss, vous devez remplacer adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un objet client de sortie**

Avant d’effectuer une opération de service Output par programmation, vous devez créer un objet client de service Output.

**Référence à une source de données XML**

Un élément XML doit exister pour chaque champ de formulaire à renseigner avec des données. Le nom de l’élément XML doit correspondre au nom du champ. Un élément XML est ignoré s’il ne correspond pas à un champ de formulaire ou si le nom de l’élément XML ne correspond pas au nom du champ. Il n&#39;est pas nécessaire de correspondre à l&#39;ordre dans lequel les éléments XML sont affichés, tant que tous les éléments XML sont spécifiés.

**Définition des règles de recherche**

Pour définir des règles de recherche, vous définissez un ou plusieurs modèles de texte que les services Output recherchent dans les données d’entrée. Pour chaque modèle de texte que vous définissez, vous spécifiez une conception de formulaire correspondante utilisée si le modèle de texte est localisé. Si un modèle de texte est localisé, le service Output utilise la conception de formulaire correspondante pour générer la sortie. Exemple de modèle de texte : *hypothèque*.

>[!NOTE]
>
>Si les modèles de texte ne sont pas localisés, le formulaire par défaut est utilisé. Assurez-vous que toutes les conceptions de formulaire que vous utilisez se trouvent à la racine de contenu.

**Définition des options d’exécution du PDF**

Définissez les options d’exécution de PDF suivantes afin que le service Output puisse créer un document de PDF basé sur plusieurs conceptions de formulaire :

* **URI du fichier**: Indique le nom et l’emplacement du fichier de PDF généré par le service Output.
* **Règles**: Indique les règles que vous avez définies.
* **LookAHead**: Indique le nombre d’octets à utiliser depuis le début du fichier de données d’entrée pour rechercher les modèles de texte définis. La valeur par défaut est de 500 octets.

**Définition des options d’exécution de rendu**

Vous pouvez définir des options d’exécution de rendu lors de la création de fichiers PDF. Bien que ces options ne soient pas requises (contrairement aux options d’exécution du PDF), vous pouvez effectuer des tâches telles que l’amélioration des performances du service Output. Par exemple, vous pouvez mettre en cache la conception de formulaire utilisée par le service Output pour améliorer les performances.

**Génération d’un document de PDF**

Après avoir référencé une source de données XML valide et défini les options d’exécution, vous pouvez appeler le service Output, ce qui génère un document de PDF. Si le service Output localise un modèle de texte spécifié dans les données d’entrée, il utilise la conception de formulaire correspondante. Si aucun modèle de texte n’est utilisé, le service Output utilise la conception de formulaire par défaut.

**Retrieve the results of the operation**

Une fois que le service Output a effectué une opération, il renvoie des données XML spécifiant si l’opération a réussi.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Création de règles de recherche à l’aide de l’API Java {#create-search-rules-using-the-java-api}

Create search rules by using the Output API (Java):

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-output-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet client de sortie.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez une source de données XML.

   * Créez un `java.io.FileInputStream` qui représente la source de données XML utilisée pour remplir le document du PDF en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier XML.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Définissez des règles de recherche.

   * Créez un objet `Rule` en utilisant son constructeur.
   * Définissez un modèle de texte en appelant la méthode `Rule` de `setPattern` et transmission d’une valeur string qui spécifie un modèle de texte.
   * Définissez la conception de formulaire correspondante en appelant la méthode `Rule` de `setForm` de . Transmettez une valeur string qui spécifie le nom de la conception de formulaire.

   >[!NOTE]
   >
   >Pour chaque modèle de texte à définir, répétez les trois sous-étapes précédentes.

   * Créez un `java.util.List` en utilisant un objet `java.util.ArrayList` constructeur.
   * Pour chaque `Rule` que vous avez créé, appelez l’objet `java.util.List` de `add` et transmettez la méthode `Rule` .


1. Définissez les options d’exécution du PDF.

   * Créez un objet `PDFOutputOptionsSpec` en utilisant son constructeur.
   * Indiquez le nom et l’emplacement du fichier de PDF généré par le service Output en appelant la fonction `PDFOutputOptionsSpec` de `setFileURI` . Transmettez une valeur string qui spécifie l’emplacement du fichier du PDF. L’option File URI est relative au serveur d’applications J2EE hébergeant AEM Forms, et non à l’ordinateur client.
   * Définissez les règles que vous avez définies en appelant la variable `PDFOutputOptionsSpec` de `setRules` . Transmettez la variable `java.util.List` contenant l’objet `Rule` objets.
   * Définissez le nombre d’octets à analyser pour les modèles de texte définis en appelant la variable `PDFOutputOptionsSpec` de `setLookAhead` . Transmettez une valeur entière qui représente le nombre d’octets.

1. Définissez les options d’exécution de rendu.

   * Créez un objet `RenderOptionsSpec` en utilisant son constructeur.
   * Mettez en cache la conception de formulaire afin d’améliorer les performances du service Output en appelant la fonction `RenderOptionsSpec` de `setCacheEnabled` et transmission `true`.

1. Générez un document de PDF.

   Générer un document de PDF basé sur plusieurs conceptions de formulaire en appelant la fonction `OutputClient` de `generatePDFOutput` et transmission des valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Une valeur string qui spécifie le nom de la conception de formulaire par défaut. En d’autres termes, la conception de formulaire utilisée si aucun modèle de texte n’est localisé.
   * Une valeur string qui spécifie la racine de contenu où se trouvent les conceptions de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `com.adobe.idp.Document` contenant les données de formulaire recherchées par le service Output pour les modèles de texte définis.

   Le `generatePDFOutput` renvoie une `OutputResult` contenant les résultats de l’opération.

1. Récupérez les résultats de l’opération.

   * Créez un `com.adobe.idp.Document` qui représente l’état de la propriété `generatePDFOutput` en appelant la méthode `OutputResult` de `getStatusDoc` .
   * Créez un `java.io.File` qui contiendra les résultats de l’opération. Assurez-vous que l’extension de fichier est .xml.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` dans le fichier (assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui a été renvoyé par l’objet `getStatusDoc` ).

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode EJB) : Création de règles de recherche à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Démarrage rapide (mode SOAP) : Création de règles de recherche à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Création de règles de recherche à l’aide de l’API de service Web {#create-search-rules-using-the-web-service-api}

Créez des règles de recherche à l’aide de l’API Output (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet client de sortie.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Créez un `OutputServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Référencez une source de données XML.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker les données qui seront fusionnées avec le document du PDF.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF à chiffrer et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez des règles de recherche.

   * Créez un objet `Rule` en utilisant son constructeur.
   * Définissez un modèle de texte en attribuant une valeur string qui spécifie un modèle de texte au `Rule` de `pattern` membre de données.
   * Définissez la conception de formulaire correspondante en attribuant une valeur string qui spécifie la conception de formulaire au `Rule` de `form` membre de données.

   >[!NOTE]
   >
   >Pour chaque modèle de texte à définir, répétez les trois sous-étapes précédentes.

   * Créez un `MyArrayOf_xsd_anyType` qui stocke les règles.
   * Attribuer chaque `Rule` à un élément de la propriété `MyArrayOf_xsd_anyType` tableau. Appeler la variable `MyArrayOf_xsd_anyType` de `Add` pour chaque `Rule` .


1. Définition des options d’exécution du PDF

   * Créez un objet `PDFOutputOptionsSpec` en utilisant son constructeur.
   * Définissez l’option d’URI de fichier en attribuant une valeur string qui spécifie l’emplacement du fichier de PDF généré par le service Output à la variable `PDFOutputOptionsSpec` de `fileURI` membre de données. L’option File URI est relative au serveur d’applications J2EE hébergeant AEM Forms, et non à l’ordinateur client.
   * Définissez l’option Copies en attribuant une valeur entière qui spécifie le nombre de copies générées par le service Output à la variable `PDFOutputOptionsSpec` de `copies` membre de données.
   * Définissez les règles que vous avez définies en attribuant la variable `MyArrayOf_xsd_anyType` qui stocke les règles dans la variable `PDFOutputOptionsSpec` de `rules` membre de données.
   * Définissez le nombre d’octets à analyser pour les modèles de texte définis en attribuant une valeur entière qui représente le nombre d’octets à analyser au `PDFOutputOptionsSpec` de `lookAhead` data .

1. Définition des options d’exécution de rendu

   * Créez un objet `RenderOptionsSpec` en utilisant son constructeur.
   * Mettre en cache la conception de formulaire afin d’améliorer les performances du service Output en affectant la valeur `true` au `RenderOptionsSpec` de `cacheEnabled` membre de données.

   >[!NOTE]
   >
   >Vous ne pouvez pas définir la version du document du PDF à l’aide du `RenderOptionsSpec` de `pdfVersion` membre si le document d’entrée est un formulaire Acrobat. Le document output PDF conserve la version PDF du formulaire Acrobat. De même, vous ne pouvez pas définir l’option de PDF balisé à l’aide de la variable `RenderOptionsSpec` de `taggedPDF` si le document d’entrée est un formulaire Acrobat.

   >[!NOTE]
   >
   >Vous ne pouvez pas définir l’option de PDF linéarisé à l’aide de la variable `RenderOptionsSpec` de `linearizedPDF` membre si le document du PDF d’entrée est certifié ou signé numériquement. Pour plus d’informations, voir [Signature numérique de documents PDF](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).

1. Génération d’un document de PDF

   Créez un document de PDF en appelant la méthode `OutputServiceService` de `generatePDFOutput`et transmission des valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire.
   * Une valeur string qui spécifie la racine de contenu où se trouve la conception de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `BLOB` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire.
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec des métadonnées générées qui décrivent le document. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).
   * A `BLOB` qui est renseigné par la variable `generatePDFOutput` . Le `generatePDFOutput` renseigne cet objet avec les données de résultat. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).
   * Un `OutputResult` contenant les résultats de l’opération. (Cette valeur de paramètre est requise uniquement pour l’appel de service Web).

   >[!NOTE]
   >
   >Lors de la génération d’un document de PDF en appelant la méthode `generatePDFOutput` , sachez que vous ne pouvez pas fusionner des données avec un formulaire de PDF XFA signé, certifié ou contenant des droits d’utilisation. Pour plus d’informations sur les droits d’utilisation, voir [Application des droits d’utilisation aux documents du PDF](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).

1. Récupération des résultats de l’opération

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente un emplacement de fichier XML contenant les données de résultat. Assurez-vous que l’extension de fichier est XML.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renseigné avec les données de résultat de la fonction `OutputServiceService` de `generatePDFOutput` (le huitième paramètre). Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Write the contents of the byte array to the XML file by invoking the `System.IO.BinaryWriter` object’s `Write` method and passing the byte array.

**Voir également**

[Summary of steps](creating-document-output-streams.md#summary-of-steps)

[Invoking AEM Forms using MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Aplatissement de documents PDF {#flattening-pdf-documents}

Vous pouvez utiliser le service Output pour transformer un document de PDF interactif en PDF non interactif. Un document de PDF interactif permet aux utilisateurs de saisir ou de modifier des données figurant dans les champs du document du PDF. Le processus de transformation d’un document de PDF interactif en document de PDF non interactif est appelé *aplatissement*. Lorsqu’un document de PDF est aplati, un utilisateur ne peut pas modifier les données des champs du document. S’assurer que les données ne peuvent être modifiées est l’une des raisons de l’aplatissement d’un document PDF.

Vous pouvez aplatir les types de documents PDF suivants :

* Documents du PDF XFA interactifs
* Acrobat Forms

Toute tentative d’aplatissement d’un PDF qui est un document de PDF non interactif entraîne une exception.

>[!NOTE]
>
>Pour plus d’informations sur le service Output, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-9}

Pour aplatir un document de PDF interactif dans un document de PDF non interactif, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet client de sortie.
1. Récupérez un document de PDF interactif.
1. Transforme le document du PDF.
1. Enregistrez le document de PDF non interactif en tant que fichier de PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé. Pour plus d’informations sur l’emplacement de tous les fichiers JAR AEM Forms, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un objet client de sortie**

Avant d’effectuer une opération de service Output par programmation, vous devez créer un objet client de service Output. Si vous utilisez l’API Java, créez une `OutputClient` . Si vous utilisez l’API du service Web d’Output, créez une `OutputServiceService` .

**Récupération d’un document de PDF interactif**

Récupérez un document de PDF interactif que vous souhaitez transformer en document de PDF non interactif. Toute tentative de transformation d’un document de PDF non interactif entraîne une exception.

**Transformation du document du PDF**

Après avoir récupéré un document de PDF interactif, vous pouvez le transformer en document de PDF non interactif. Le service Output renvoie un document de PDF non interactif.

**Enregistrer le document de PDF non interactif en tant que fichier de PDF**

Vous pouvez enregistrer le document de PDF non interactif en tant que fichier de PDF.

**Voir également**

[Aplatissement d’un document de PDF à l’aide de l’API Java](creating-document-output-streams.md#flatten-a-pdf-document-using-the-java-api)

[Aplatissement d’un document de PDF à l’aide de l’API de service Web](creating-document-output-streams.md#flatten-a-pdf-document-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Aplatissement d’un document de PDF à l’aide de l’API Java {#flatten-a-pdf-document-using-the-java-api}

Aplatissement d’un document de PDF interactif vers un document de PDF non interactif à l’aide de l’API Output (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-output-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet client de sortie.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Récupérez un document de PDF interactif.

   * Créez un `java.io.FileInputStream` qui représente le document du PDF interactif à transformer à l’aide de son constructeur et en transmettant une valeur string spécifiant l’emplacement du fichier du PDF interactif.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Transforme le document du PDF.

   Transforme le document du PDF interactif en document du PDF non interactif en appelant la méthode `OutputServiceService` de `transformPDF` et transmission des valeurs suivantes :

   * Le `com.adobe.idp.Document` contenant le document du PDF interactif.
   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF non interactif, spécifiez `TransformationFormat.PDF`.
   * A `PDFARevisionNumber` valeur enum qui spécifie le numéro de révision. Comme ce paramètre est destiné à un document de PDF/A, vous pouvez indiquer `null`.
   * Une valeur string qui représente le numéro de modification et l’année, séparés par deux points. Comme ce paramètre est destiné à un document de PDF/A, vous pouvez indiquer `null`.
   * A `PDFAConformance` valeur d’énumération qui représente le niveau de conformité du PDF/A. Comme ce paramètre est destiné à un document de PDF/A, vous pouvez indiquer `null`.

   Le `transformPDF` renvoie une `com.adobe.idp.Document` contenant un document de PDF non interactif.

1. Enregistrez le document de PDF non interactif en tant que fichier de PDF.

   * Créez un `java.io.File` et assurez-vous que l’extension de nom de fichier est .pdf.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `transformPDF` ).

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Démarrage rapide (mode EJB) : Transformation d’un document de PDF à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Démarrage rapide (mode SOAP) : Transformation d’un document de PDF à l’aide de l’API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Aplatissement d’un document de PDF à l’aide de l’API de service Web {#flatten-a-pdf-document-using-the-web-service-api}

Aplatissement d’un document de PDF interactif vers un document de PDF non interactif à l’aide de l’API Output (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet client de sortie.

   * Créez un `OutputServiceClient` en utilisant son constructeur par défaut.
   * Créez un `OutputServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Toutefois, spécifiez `?blob=mtom` pour utiliser MTOM.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `OutputServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Assign the constant value `BasicHttpSecurityMode.TransportCredentialOnly` to the field `BasicHttpBindingSecurity.Security.Mode`.

1. Retrieve an interactive PDF document.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour stocker le document de PDF interactif.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document de PDF interactif.
   * Create a byte array that stores the content of the `System.IO.FileStream` object. Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Transforme le document du PDF.

   Transforme le document du PDF interactif en document du PDF non interactif en appelant la méthode `OutputClient` de `transformPDF` et transmission des valeurs suivantes :

   * A `BLOB` contenant le document du PDF interactif.
   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF non interactif, spécifiez `TransformationFormat.PDF`.
   * A `PDFARevisionNumber` valeur enum qui spécifie le numéro de révision.
   * Une valeur booléenne qui spécifie si la variable `PDFARevisionNumber` La valeur enum est utilisée. Comme ce paramètre est destiné à un document de PDF/A, vous pouvez indiquer `false`.
   * Une valeur string qui représente le numéro de modification et l’année, séparés par deux points. Comme ce paramètre est destiné à un document de PDF/A, vous pouvez indiquer `null`.
   * A `PDFAConformance` valeur d’énumération qui représente le niveau de conformité du PDF/A.
   * Valeur booléenne qui spécifie si la variable `PDFAConformance` La valeur enum est utilisée. Comme ce paramètre est destiné à un document de PDF/A, vous pouvez indiquer `false`.

   Le `transformPDF` renvoie une `BLOB` contenant un document de PDF non interactif.

1. Enregistrez le document de PDF non interactif en tant que fichier de PDF.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document de PDF non interactif.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `transformPDF` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Résumé des étapes](creating-document-output-streams.md#summary-of-steps)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
