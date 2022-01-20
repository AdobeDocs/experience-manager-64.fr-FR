---
title: Assemblage de Portfolios de PDF
seo-title: Assembling PDF Portfolios
description: Assemblez un portfolio de PDF afin de combiner plusieurs documents de différents types, y compris des fichiers Word, images et PDF. Vous pouvez assembler un portfolio de PDF à l’aide d’une API Java et d’une API de service Web.
seo-description: Assemble a PDF portfolio to combine several documents of various types, including word file, image files, and PDF documents. You can assemble a PDF portfolio using a Java API and a Web Service API.
uuid: 1778c90b-9d26-466b-a7c7-401d737395e0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 023f0d9e-bfde-4879-a839-085fadffb48e
role: Developer
exl-id: 767d89bc-d243-46a1-a954-9977f4906566
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1814'
ht-degree: 3%

---

# Assemblage de Portfolios de PDF {#assembling-pdf-portfolios}

Vous pouvez assembler un Portfolio de PDF à l’aide de l’API Java Assembler et de l’API Web Service. Un portfolio peut combiner plusieurs documents de différents types, y compris un fichier Word, des fichiers image (par exemple, un fichier jpeg) et des documents PDF. La mise en page du portfolio peut être définie sur différents styles, comme le *Grille avec aperçu*, la variable *Sur une image* mise en page ou même *Révolve*.

L’illustration suivante est une capture d’écran d’un portfolio avec *Sur une image* mise en page de style.

![ap_ap_portfolio](assets/ap_ap_portfolio.png)

La création d’un Portfolio de PDF constitue une alternative sans papier à la transmission d’une collection de documents. Avec AEM Forms, vous pouvez créer des portefeuilles en appelant le service Assembler avec un document DDX structuré. Le document DDX suivant est un exemple de document DDX qui crée un Portfolio de PDF.

```as3
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
     <PDF result="portfolio1.pdf"> 
         <Portfolio>   
             <Navigator source="myNavigator">   
                 <Resource name="navigator/image.xxx" source="myImage.png"/> 
             </Navigator> 
         </Portfolio> 
         <PackageFiles source="dog1"  > 
              <FieldData name="X">72</FieldData> 
             <FieldData name="Y">72</FieldData> 
             <File filename="saint_bernard.jpg" mimetype="image/jpeg"/> 
         </PackageFiles> 
         <PackageFiles source="dog2"  > 
             <FieldData name="X">120</FieldData> 
             <FieldData name="Y">216</FieldData> 
             <File filename="greyhound.pdf"/> 
         </PackageFiles>     
     </PDF> 
 </DDX>
```

Le document DXX doit contenir un `Portfolio` avec une balise imbriquée `Navigator` balise . Notez la balise `<Resource name="navigator/image.xxx" source="myImage.png"/>` n’est nécessaire que si `myNavigator` est affecté en tant que navigateur de mise en page onImage : `AdobeOnImage.nav`. Cette balise permet au service Assembler de sélectionner l’image à utiliser comme arrière-plan du portfolio. Inclure `PackageFiles` et `File` balises pour définir le nom de fichier et le type MIME du fichier empaqueté.

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour créer un Portfolio de PDF, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Référencez les documents requis.
1. Définissez les options d’exécution.
1. Assemblez le portfolio.
1. Enregistrez le portfolio assemblé.

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

**Référence à un document DDX existant**

Un document DDX doit être référencé pour assembler un Portfolio de PDF. Ce document DDX doit contenir la variable `Portfolio`, `Navigator` et `PackageFiles` éléments .

**Référencer les documents requis**

Pour assembler un Portfolio de PDF, référencez tous les fichiers représentant les documents à assembler. Par exemple, transmettez tous les fichiers image spécifiés dans le document DDX au service Assembler. Notez que ces fichiers sont référencés dans le document DDX spécifié dans cette section : *myImage.png* et *saint_bernard.jpg*.

Lors de l’assemblage d’un Portfolio de PDF, transmettez un fichier NAV (un fichier de navigateur) au service Assembler. Le fichier NAV que vous transmettez au service Assembler dépend du type de Portfolio de PDF à créer. Par exemple, pour créer une *Sur une image* , transmettez le fichier AdobeOnImage.nav . Vous pouvez localiser les fichiers NAV dans le dossier suivant :

`<Install folder>\Acrobat 9.0\Acrobat\Navigators`

Copiez le fichier NAV du répertoire d’installation d’Acrobat 9 (ou version ultérieure). Placez le fichier NAV à un emplacement accessible par votre application cliente. Tous les fichiers sont transmis au service Assembler dans un objet de collection Map.

>[!NOTE]
>
>Les démarrages rapides associés aux Portfolios du PDF d’assemblage utilisent AdobeOnImage.nav.

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lors de l’exécution d’une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur.

**Assemblage du portfolio**

Pour assembler un Portfolio de PDF, vous appelez le `invokeDDX` opération. Le service Assembler renvoie le Portfolio du PDF dans un objet de collection.

**Enregistrer le portfolio assemblé**

Un Portfolio de PDF est renvoyé dans un objet de collection. Effectuez une itération sur l’objet de collection et enregistrez le Portfolio de PDF en tant que fichier de PDF.

**Voir également**

[Assemblage d’un Portfolio de PDF à l’aide de l’API Java](#assemble-a-pdf-portfolio-using-the-java-api)

[Assemblage d’un Portfolio de PDF à l’aide de l’API de service Web](#assemble-a-pdf-portfolio-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblage d’un Portfolio de PDF à l’aide de l’API Java {#assemble-a-pdf-portfolio-using-the-java-api}

Assemblez un Portfolio de PDF à l’aide de l’API du service Assembler (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Référencez les documents requis.

   * Créez un `java.util.Map` utilisé pour stocker des documents de PDF d’entrée à l’aide d’un objet `HashMap` constructeur.
   * Créez un objet `java.io.FileInputStream` en utilisant son constructeur. Transmettez l’emplacement du fichier NAV requis (répétez cette tâche pour chaque fichier requis pour créer un portfolio).
   * Créez un `com.adobe.idp.Document` et transmettez la variable `java.io.FileInputStream` qui contient le fichier NAV (répétez cette tâche pour chaque fichier requis pour créer un portfolio).
   * Ajoutez une entrée au `java.util.Map` en appelant son objet `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la valeur de l’élément source spécifié dans le document DDX. (répétez cette tâche pour chaque fichier requis pour créer un portfolio).
      * A `com.adobe.idp.Document` contenant le document du PDF. (répétez cette tâche pour chaque fichier requis pour créer un portfolio).

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Assemblez le portfolio.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs requises suivantes :

   * A `com.adobe.idp.Document` objet représentant le document DDX à utiliser
   * A `java.util.Map` contenant les fichiers requis pour créer un Portfolio de PDF.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation de la tâche

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` contenant le Portfolio de PDF assemblé et les exceptions survenues.

1. Enregistrez le portfolio assemblé.

   Pour obtenir le Portfolio du PDF, procédez comme suit :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette méthode renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez le résultat `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le Portfolio du PDF.

**Voir également**

[Démarrage rapide (mode SOAP) : Assemblage de Portfolios PDF à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-portfolios-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblage d’un Portfolio de PDF à l’aide de l’API de service Web {#assemble-a-pdf-portfolio-using-the-web-service-api}

Assemblez un Portfolio de PDF à l’aide de l’API Assembler Service (service Web) :

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
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document DDX et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Référencez les documents requis.

   * Pour chaque fichier d’entrée, créez une `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le fichier d’entrée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.
   * Créez un `MyMapOf_xsd_string_To_xsd_anyType` . Cet objet de collection est utilisé pour stocker les fichiers d’entrée nécessaires à la création d’un Portfolio de PDF.
   * Pour chaque fichier d’entrée, créez une `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Attribuez une valeur string qui représente le nom de la clé au `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` champ . Cette valeur doit correspondre à la valeur de l’élément spécifié dans le document DDX. (Effectuez cette tâche pour chaque fichier d’entrée.)
   * Attribuez le `BLOB` qui stocke le fichier d’entrée dans la propriété `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` champ . (Effectuez cette tâche pour chaque document de PDF d’entrée.)
   * Ajoutez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` vers l’objet `MyMapOf_xsd_string_To_xsd_anyType` . Appeler la variable `MyMapOf_xsd_string_To_xsd_anyType` de `Add` et transmettez la méthode `MyMapOf_xsd_string_To_xsd_anyType` . (Effectuez cette tâche pour chaque document de PDF d’entrée.)

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` membre de données.

1. Assemblez le portfolio.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `BLOB` objet représentant le document DDX
   * Le `MyMapOf_xsd_string_To_xsd_anyType` contenant les fichiers requis
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeDDX` renvoie une `AssemblerResult` contenant les résultats de la tâche et les exceptions survenues.

1. Enregistrez le portfolio assemblé.

   Pour obtenir le Portfolio de PDF nouvellement créé, procédez comme suit :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les documents de PDF générés.
   * Effectuez une itération à l’aide du `Map` pour obtenir chaque document généré. Convertissez ensuite le de `value` à `BLOB`.
   * Extrayez les données binaires qui représentent le document du PDF en accédant à ses `BLOB` de `MTOM` . Cette opération renvoie un tableau d’octets que vous pouvez écrire dans un fichier de PDF.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
