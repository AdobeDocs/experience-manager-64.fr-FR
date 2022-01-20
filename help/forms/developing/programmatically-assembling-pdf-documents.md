---
title: Assemblage par programmation de documents PDF
seo-title: Programmatically Assembling PDF Documents
description: Utilisez l’API du service Assembler pour assembler plusieurs documents de PDF en un seul document de PDF à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Assembler service API to assemble multiple PDF documents into a single PDF document using the Java API and the Web Service API.
uuid: aa3f8f39-1fbc-48d0-82ff-6caaadf125fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: ebe8136b-2a79-4035-b9d5-aa70a5bbd4af
role: Developer
exl-id: be09271b-3004-4866-b43b-fb03c91305ec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2110'
ht-degree: 2%

---

# Assemblage par programmation de documents PDF {#programmatically-assembling-pdf-documents}

Vous pouvez utiliser l’API du service Assembler pour assembler plusieurs documents de PDF en un seul document de PDF. L’illustration suivante présente la fusion de trois documents de PDF en un seul document de PDF.

![pa_pa_document_assembly](assets/pa_pa_document_assembly.png)

Pour assembler plusieurs documents de PDF en un seul document de PDF, vous avez besoin d’un document DDX. Un document DDX décrit le document du PDF produit par le service Assembler. En d’autres termes, le document DDX indique au service Assembler les actions à effectuer.

Dans le cadre de cette discussion, supposons que le document DDX suivant soit utilisé.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
     <PDF result="out.pdf"> 
         <PDF source="map.pdf" /> 
         <PDF source="directions.pdf" /> 
     </PDF> 
 </DDX>
```

Ce document DDX fusionne deux documents PDF nommés *map.pdf* et *directions.pdf* dans un document de PDF unique.

>[!NOTE]
>
>Pour voir un document DDX qui démonte un document de PDF, voir [Démontage programmatique de documents PDF](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents).

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Remarques concernant l’appel du service Assembler à l’aide de services web {#considerations-when-invoking-assembler-service-using-web-services}

Lorsque vous ajoutez des en-têtes et des pieds de page lors de l’assemblage de documents volumineux, vous pouvez rencontrer une `OutOfMemory` et les fichiers ne seront pas assemblés. Pour réduire les risques que ce problème se produise, ajoutez une `DDXProcessorSetting` à votre document DDX, comme illustré dans l’exemple suivant.

`<DDXProcessorSetting name="checkpoint" value="2000" />`

Vous pouvez ajouter cet élément en tant qu’enfant de la variable `DDX` élément ou en tant qu’enfant d’un `PDF result` élément . La valeur par défaut de ce paramètre est 0 (zéro), ce qui désactive la coche et le DDX se comporte comme si la variable `DDXProcessorSetting` n’est pas présent. Si vous avez rencontré une `OutOfMemory` , vous devrez peut-être définir la valeur sur un entier, généralement entre 500 et 5000. Une petite valeur de point de contrôle entraîne un pointage plus fréquent.

## Résumé des étapes {#summary-of-steps}

Pour assembler un seul document PDF à partir de plusieurs documents PDF, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Documents de PDF de saisie de référence.
1. Définissez les options d’exécution.
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

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge autre que JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un client Assembler PDF**

Avant d’effectuer une opération Assembler par programmation, vous devez créer un client Assembler.

**Référence à un document DDX existant**

Un document DDX doit être référencé pour assembler un document de PDF. Prenons l’exemple du document DDX introduit dans cette section. Ce document DDX demande au service Assembler de fusionner deux documents de PDF en un seul document de PDF.

**Documents de PDF de saisie de référence**

Référencez les documents du PDF d’entrée que vous souhaitez transmettre au service Assembler. Par exemple, si vous souhaitez transmettre deux documents de PDF d’entrée nommés Carte et Instructions, vous devez transmettre les fichiers de PDF correspondants.

Le fichier map.pdf et le fichier directions.pdf doivent être placés dans un objet de collection. Le nom de la clé doit correspondre à la valeur de l’attribut source du PDF dans le document DDX. Peu importe le nom du fichier du PDF si la clé et l’attribut source dans le document DDX correspondent.

>[!NOTE]
>
>Un `*AssemblerResult*` , qui contient un objet de collection, est renvoyé si vous appelez la méthode `*invokeDDX*` opération. Cette opération est utilisée lorsque vous transmettez au service Assembler au moins deux documents de PDF d’entrée. Cependant, si vous ne transmettez qu’un seul PDF d’entrée au service Assembler et ne vous attendez qu’à un seul document de retour, appelez la méthode `*invokeOneDocument*` opération. Lors de l’appel de cette opération, un seul document est renvoyé. Pour plus d’informations sur l’utilisation de cette opération, voir [Assemblage de documents PDF chiffrés](/help/forms/developing/assembling-encrypted-pdf-documents.md#assembling-encrypted-pdf-documents).

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lorsqu’il effectue une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur. Pour plus d’informations sur les options d’exécution que vous pouvez définir, voir `AssemblerOptionSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Assemblage des documents du PDF d’entrée**

Après avoir créé le client de service, référencé un fichier DDX, créé un objet de collection qui stocke les documents du PDF d’entrée et défini les options d’exécution, vous pouvez appeler l’opération DDX. Lors de l’utilisation du document DDX spécifié dans cette section, les fichiers map.pdf et direction.pdf sont fusionnés en un document PDF.

**Extraire les résultats**

Le service Assembler renvoie une `java.util.Map` , qui peut être obtenu à partir de la propriété `AssemblerResult` et contenant les résultats de l’opération. La valeur renvoyée `java.util.Map` contient les documents créés et les exceptions.

Le tableau suivant récapitule certaines des valeurs clés et des types d’objets qui peuvent se trouver dans la variable renvoyée. `java.util.Map` .

<table> 
 <thead> 
  <tr> 
   <th><p>Valeur clé</p></th> 
   <th><p>Type d’objet</p></th> 
   <th><p>Description</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p><code><i>documentName</i></code></p></td> 
   <td><p><code>com.adobe.idp.Document</code></p></td> 
   <td><p>Contient les documents générés qui sont spécifiés dans un élément cible DDX</p></td> 
  </tr> 
  <tr> 
   <td><p><code><i>documentName</i></code></p></td> 
   <td><p><code>Exception</code></p></td> 
   <td><p>Contient toute exception pour le document</p></td> 
  </tr> 
  <tr> 
   <td><p><code>OutputMapConstants.LOG_NAME</code></p></td> 
   <td><p><code>com.adobe.idp.Documen</code></p></td> 
   <td><p>Contient le journal des tâches</p></td> 
  </tr> 
 </tbody> 
</table>

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démontage programmatique de documents PDF](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## Assemblage de documents PDF à l’aide de l’API Java {#assemble-pdf-documents-using-the-java-api}

Assemblez un document PDF à l’aide de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Documents de PDF de saisie de référence.

   * Créez un `java.util.Map` utilisé pour stocker des documents de PDF d’entrée à l’aide d’un objet `HashMap` constructeur.
   * Pour chaque document de PDF d’entrée, créez une `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement du document du PDF d’entrée.
   * Pour chaque document de PDF d’entrée, créez une `com.adobe.idp.Document` et transmettez la variable `java.io.FileInputStream` contenant le document du PDF.
   * Pour chaque document d’entrée, ajoutez une entrée au `java.util.Map` en appelant son objet `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX.
      * A `com.adobe.idp.Document` ou `java.util.List` qui spécifie plusieurs documents) contenant le document du PDF source.

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Assemblez les documents du PDF d’entrée.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs requises suivantes :

   * A `com.adobe.idp.Document` objet représentant le document DDX à utiliser
   * A `java.util.Map` Objet contenant les fichiers de PDF d’entrée à assembler
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation des tâches

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` contenant les résultats de la tâche et les exceptions survenues.

1. Extrayez les résultats.

   Pour obtenir le document de PDF nouvellement créé, procédez comme suit :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette fonction renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez le résultat `com.adobe.idp.Document` . (Vous pouvez utiliser l’élément de résultat PDF spécifié dans le document DDX pour obtenir le document.)
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document du PDF.

   >[!NOTE]
   >
   >If `*LOG_LEVEL*` a été défini pour générer un journal, vous pouvez extraire le journal à l’aide de la variable `*AssemblerResult*` de `*getJobLog*` .

**Voir également**

[Démarrage rapide (mode SOAP) : Assemblage d’un document de PDF à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblage de documents PDF à l’aide de l’API du service Web {#assemble-pdf-documents-using-the-web-service-api}

Assemblez des documents PDF à l’aide de l’API Assembler Service (service Web) :

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
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Documents de PDF de saisie de référence.

   * Pour chaque document de PDF d’entrée, créez une `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF d’entrée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.
   * Créez un `MyMapOf_xsd_string_To_xsd_anyType` . Cet objet de collection est utilisé pour stocker des documents de PDF d’entrée.
   * Pour chaque document de PDF d’entrée, créez une `MyMapOf_xsd_string_To_xsd_anyType_Item` . Par exemple, si deux documents de PDF d’entrée sont utilisés, créez deux `MyMapOf_xsd_string_To_xsd_anyType_Item` objets.
   * Attribuez une valeur string qui représente le nom de la clé au `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` champ . Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX. (Effectuez cette tâche pour chaque document de PDF d’entrée.)
   * Attribuez le `BLOB` qui stocke le document du PDF dans la propriété `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` champ . (Effectuez cette tâche pour chaque document de PDF d’entrée.)
   * Ajoutez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` vers l’objet `MyMapOf_xsd_string_To_xsd_anyType` . Appeler la variable `MyMapOf_xsd_string_To_xsd_anyType` de `Add` et transmettez la méthode `MyMapOf_xsd_string_To_xsd_anyType` . (Effectuez cette tâche pour chaque document de PDF d’entrée.)

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` membre de données.

1. Assemblez les documents du PDF d’entrée.

   Appeler la variable `AssemblerServiceClient` de `invoke` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document DDX.
   * Le `mapItem` qui contient les documents du PDF d’entrée. Ses clés doivent correspondre aux noms des fichiers source du PDF et ses valeurs doivent être les suivantes : `BLOB` qui correspondent à ces fichiers.
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution.

   Le `invoke` renvoie une `AssemblerResult` contenant les résultats de la tâche et les exceptions qui peuvent s’être produites.

1. Extrayez les résultats.

   Pour obtenir le document de PDF nouvellement créé, procédez comme suit :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les documents du PDF de résultats.
   * Effectuez une itération à l’aide du `Map` jusqu’à ce que vous trouviez la clé correspondant au nom du document généré. Collez ensuite le de `value` à `BLOB`.
   * Extrayez les données binaires qui représentent le document du PDF en accédant à ses `BLOB` de `MTOM` . Cette opération renvoie un tableau d’octets que vous pouvez écrire dans un fichier de PDF.

   >[!NOTE]
   >
   >If `LOG_LEVEL` a été défini pour générer un journal, vous pouvez extraire le journal en obtenant la valeur de la variable `AssemblerResult` de `jobLog` membre de données.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
