---
title: Assemblage de plusieurs fragments XDP
seo-title: Assembling Multiple XDP Fragments
description: Assemblez plusieurs fragments XDP dans un seul document XDP à l’aide de l’API Java et de l’API Web Service.
seo-description: Assemble multiple XDP fragments into a single XDP document using the Java API and Web Service API.
uuid: 9e74e0e0-568d-4760-91a8-03dc1362d497
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 0ed1f69d-c212-4d47-a572-ae030f2983fc
role: Developer
exl-id: be9db93d-97e1-4d4e-8d07-1c58a4a1a44c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1887'
ht-degree: 3%

---

# Assemblage de plusieurs fragments XDP {#assembling-multiple-xdp-fragments}

Vous pouvez assembler plusieurs fragments XDP en un seul document XDP. Prenons l’exemple des fragments XDP où chaque fichier XDP contient un ou plusieurs sous-formulaires utilisés pour créer un formulaire d’intégrité. L’illustration suivante présente la vue de composition (représente le fichier tuc018_template_flowed.xdp utilisé dans la variable *Assemblage de plusieurs fragments XDP* démarrage rapide) :

![am_am_forma](assets/am_am_forma.png)

L’illustration suivante présente la section du patient (représente le fichier tuc018_contact.xdp utilisé dans la variable *Assemblage de plusieurs fragments XDP* démarrage rapide) :

![am_am_formb](assets/am_am_formb.png)

L’illustration suivante présente la section sur l’intégrité du patient (représente le fichier tuc018_patient.xdp utilisé dans la variable *Assemblage de plusieurs fragments XDP* démarrage rapide) :

![am_am_formc](assets/am_am_formc.png)

Ce fragment contient deux sous-formulaires nommés *subPatientPhysique* et *subPatientHealth*. Ces deux sous-formulaires sont référencés dans le document DDX transmis au service Assembler. À l’aide du service Assembler, vous pouvez combiner tous ces fragments XDP en un seul document XDP, comme illustré ci-dessous.

![am_am_formd](assets/am_am_formd.png)

Le document DDX suivant assemble plusieurs fragments XDP en un document XDP.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
         <XDP result="tuc018result.xdp"> 
            <XDP source="tuc018_template_flowed.xdp"> 
             <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/> 
               <XDPContent insertionPoint="ddx_fragment" source="tuc018_patient.xdp" fragment="subPatientPhysical" required="false"/> 
               <XDPContent insertionPoint="ddx_fragment" source="tuc018_patient.xdp" fragment="subPatientHealth" required="false"/> 
            </XDP> 
         </XDP>         
 </DDX>
```

Le document DDX contient un fichier XDP. `result` qui spécifie le nom du résultat. Dans ce cas, la valeur est `tuc018result.xdp`. Cette valeur est référencée dans la logique de l’application utilisée pour récupérer le document XDP une fois que le service Assembler a renvoyé le résultat. Par exemple, prenez en compte la logique d’application Java suivante utilisée pour récupérer le document XDP assemblé (notez que la valeur est en gras) :

```as3
 //Iterate through the map object to retrieve the result XDP document 
 for (Iterator i = allDocs.entrySet().iterator(); i.hasNext();) { 
     // Retrieve the Map object’s value 
     Map.Entry e = (Map.Entry)i.next(); 
                  
     //Get the key name as specified in the  
     //DDX document  
     String keyName = (String)e.getKey(); 
     if (keyName.equalsIgnoreCase("tuc018result.xdp")) 
                 {  
         Object o = e.getValue(); 
         outDoc = (Document)o; 
  
         //Save the result PDF file 
         File myOutFile = new File("C:\\AssemblerResultXDP.xdp");  
         outDoc.copyToFile(myOutFile); 
     } 
 }
```

Le `XDP source` tag spécifie le fichier XDP qui représente un document XDP complet qui peut être utilisé comme conteneur pour ajouter des fragments XDP ou comme l’un des nombreux documents qui sont ajoutés ensemble dans l’ordre. Dans ce cas, le document XDP est utilisé uniquement comme conteneur (la première illustration illustrée dans *Assemblage de plusieurs fragments XDP*). En d’autres termes, les autres fichiers XDP sont placés dans le conteneur XDP.

Pour chaque sous-formulaire, vous pouvez ajouter une `XDPContent` (cet élément est facultatif). Dans l’exemple ci-dessus, notez qu’il existe trois sous-formulaires : `subPatientContact`, `subPatientPhysical`, et `subPatientHealth`. Les deux `subPatientPhysical` et le sous-formulaire `subPatientHealth` Les sous-formulaires se trouvent dans le même fichier XDP, tuc018_patient.xdp. L’élément de fragment spécifie le nom du sous-formulaire, tel que défini dans Designer.

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour assembler plusieurs fragments XDP, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Référencez les documents XDP.
1. Définissez les options d’exécution.
1. Assemblez les documents XDP multiples.
1. Récupérez le document XDP assemblé.

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

Un document DDX doit être référencé pour assembler plusieurs documents XDP. Ce document DDX doit contenir `XDP result`, `XDP source`, et `XDPContent` éléments .

**Référence aux documents XDP**

Pour assembler plusieurs documents XDP, référencez tous les fichiers XDP utilisés pour assembler le document XDP obtenu. Assurez-vous que le nom du sous-formulaire contenu dans le document XDP référencé par le `source` est spécifié dans la variable `fragment` attribut. Un sous-formulaire est défini dans Designer. Prenons l’exemple du XML suivant.

```as3
 <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/>
```

Le sous-formulaire nommé *subPatientContact* doit se trouver dans le fichier XDP nommé *tuc018_contact.xdp*.

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lors de l’exécution d’une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur.

**Assemblage de plusieurs documents XDP**

Pour assembler plusieurs fichiers XDP, appelez le `invokeDDX` opération. Le service Assembler renvoie le document XDP assemblé dans un objet de collection.

**Récupération du document XDP assemblé**

Un document XDP assemblé est renvoyé dans un objet de collection. Effectuez une itération sur l’objet de collection et enregistrez le document XDP en tant que fichier XDP. Vous pouvez également transmettre le document XDP à un autre service AEM Forms, tel qu’Output.

**Voir également**

[Assemblage de plusieurs fragments XDP à l’aide de l’API Java](assembling-multiple-xdp-fragments.md#assemble-multiple-xdp-fragments-using-the-java-api)

[Assemblage de plusieurs fragments XDP à l’aide de l’API du service Web](assembling-multiple-xdp-fragments.md#assemble-multiple-xdp-fragments-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

[Création de documents PDF à l’aide de fragments](/help/forms/developing/creating-document-output-streams.md)

## Assemblage de plusieurs fragments XDP à l’aide de l’API Java {#assemble-multiple-xdp-fragments-using-the-java-api}

Assemblez plusieurs fragments XDP à l’aide de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Référencez les documents XDP.

   * Créez un `java.util.Map` objet utilisé pour stocker des documents XDP d’entrée à l’aide d’un `HashMap` constructeur.
   * Créez un `com.adobe.idp.Document` et transmettez la variable `java.io.FileInputStream` qui contient le fichier XDP d’entrée (répétez cette tâche pour chaque fichier XDP).
   * Ajoutez une entrée au `java.util.Map` en appelant son objet `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la variable `source` valeur d’élément spécifiée dans le document DDX (répétez cette tâche pour chaque fichier XDP).
      * A `com.adobe.idp.Document` qui contient le document XDP correspondant au `source` (répétez cette tâche pour chaque fichier XDP).

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Assemblez les documents XDP multiples.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs requises suivantes :

   * A `com.adobe.idp.Document` objet représentant le document DDX à utiliser
   * A `java.util.Map` Objet contenant les fichiers XDP d’entrée
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation de la tâche

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` contenant le document XDP assemblé.

1. Récupérez le document XDP assemblé.

   Pour obtenir le document XDP assemblé, effectuez les actions suivantes :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette méthode renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez le résultat `com.adobe.idp.Document` .
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document XDP assemblé.

**Voir également**

[Assemblage de plusieurs fragments XDP](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)

[Démarrage rapide (mode SOAP) : Assemblage de plusieurs fragments XDP à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-multiple-xdp-fragments-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblage de plusieurs fragments XDP à l’aide de l’API du service Web {#assemble-multiple-xdp-fragments-using-the-web-service-api}

Assemblez plusieurs fragments XDP à l’aide de l’API Assembler Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante lors de la définition d’une référence de service :

   ```as3
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client Assembler de PDF.

   * Créez un `AssemblerServiceClient` en utilisant son constructeur par défaut.
   * Créez un `AssemblerServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms, par exemple `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `AssemblerServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuez AEM nom d’utilisateur aux `AssemblerServiceClient.ClientCredentials.UserName.UserName` champ .
      * Attribuez la valeur de mot de passe correspondante à la variable `AssemblerServiceClient.ClientCredentials.UserName.Password`champ .
      * Attribuez le `HttpClientCredentialType.Basic` valeur constante de la variable `BasicHttpBindingSecurity.Transport.ClientCredentialType`champ .
      * Attribuez le `BasicHttpSecurityMode.TransportCredentialOnly` valeur constante de la variable `BasicHttpBindingSecurity.Security.Mode`champ .

1. Référencez un document DX existant.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour stocker le document DX.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document DDX et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Référencez les documents XDP.

   * Pour chaque fichier XDP d’entrée, créez une `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le fichier d’entrée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.
   * Créez un `MyMapOf_xsd_string_To_xsd_anyType` . Cet objet de collection est utilisé pour stocker les fichiers d’entrée nécessaires à la création d’un document XDP assemblé.
   * Pour chaque fichier d’entrée, créez une `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Attribuez une valeur string qui représente le nom de la clé au `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` champ . Cette valeur doit correspondre à la valeur de l’élément spécifié dans le document DDX. (Effectuez cette tâche pour chaque fichier XDP d’entrée.)
   * Attribuez le `BLOB` qui stocke le fichier d’entrée dans la propriété `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` champ . (Effectuez cette tâche pour chaque fichier XDP d’entrée.)
   * Ajoutez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` vers l’objet `MyMapOf_xsd_string_To_xsd_anyType` . Appeler la variable `MyMapOf_xsd_string_To_xsd_anyType` de `Add` et transmettez la méthode `MyMapOf_xsd_string_To_xsd_anyType` . (Effectuez cette tâche pour chaque document XDP d’entrée.)

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` membre de données.

1. Assemblez les documents XDP multiples.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `BLOB` objet représentant le document DDX
   * Le `MyMapOf_xsd_string_To_xsd_anyType` contenant les fichiers requis
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeDDX` renvoie une `AssemblerResult` contenant les résultats de la tâche et les exceptions survenues.

1. Récupérez le document XDP assemblé.

   Pour obtenir le document XDP nouvellement créé, effectuez les actions suivantes :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les documents de PDF générés.
   * Effectuez une itération à l’aide du `Map` pour obtenir chaque document généré. Convertissez ensuite le de `value` à `BLOB`.
   * Extrayez les données binaires qui représentent le document du PDF en accédant à ses `BLOB` de `MTOM` . Cette opération renvoie un tableau d’octets que vous pouvez écrire dans un fichier XDP.

**Voir également**

[Assemblage de plusieurs fragments XDP](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
