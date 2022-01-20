---
title: Assemblage de documents de PDF non interactifs
seo-title: Assembling Non-Interactive PDF Documents
description: Utilisez un formulaire de PDF non interactif comme entrée pour assembler un document de PDF non interactif à l’aide de l’API Java et de l’API Web Service.
seo-description: Use a non-interactive PDF form as input to assemble a non-interactive PDF document using the Java API and Web Service API.
uuid: 0c7adeb4-9a3a-4ec5-ba33-c3642928d4ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 8a75c201-bd88-4809-be08-69de94656489
role: Developer
exl-id: d4e40d68-781d-4fc8-8557-bf36462ca1d9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1775'
ht-degree: 2%

---

# Assemblage de documents de PDF non interactifs {#assembling-non-interactive-pdf-documents}

Vous pouvez assembler un document de PDF non interactif lorsque vous utilisez un formulaire de PDF interactif comme entrée. En d’autres termes, supposons que vous ayez un formulaire que les utilisateurs peuvent utiliser pour saisir des données dans ses champs. Vous pouvez transmettre ce formulaire au service Assembler, ce qui entraîne le renvoi par le service Assembler d’un document de PDF qui empêche les utilisateurs de saisir des données dans ses champs. Ce document est un formulaire de PDF non interactif. Par exemple, l’illustration suivante présente une demande de prêt immobilier qui représente un formulaire interactif.

Dans le cadre de cette discussion, supposons que le document DDX suivant soit utilisé.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
      <PDF result="out.pdf"> 
        <PDF source="inDoc"/> 
        <NoXFA/> 
      </PDF> 
 </DDX>
```

Dans ce document DDX, notez que la valeur est affectée à l’attribut source. `inDoc`. Dans les cas où un seul document de PDF d’entrée est transmis au service Assembler et où un seul document de PDF est renvoyé, vous appelez la méthode `invokeOneDocument` opération, attribuer la valeur `inDoc` à l’attribut source du PDF. Lors de l’appel de la fonction `invokeOneDocument` l’opération `inDoc` est une clé prédéfinie qui doit être spécifiée dans le document DDX.

En revanche, lors de la transmission de plusieurs documents de PDF d’entrée au service Assembler, vous pouvez appeler la fonction `invokeDDX` opération. Dans ce cas, attribuez le nom de fichier du document du PDF d’entrée au `source` attribut.

Ce document DDX contient la variable `NoXFA` , qui indique au service Assembler de renvoyer un document de PDF non interactif.

Le service Assembler peut assembler des documents de PDF non interactifs sans que le service Output ne fasse partie de votre installation AEM forms si le document du PDF d’entrée est basé sur un formulaire Acrobat ou un formulaire XFA statique. Cependant, si le document du PDF d’entrée est un formulaire XFA dynamique, le service Output doit faire partie de votre installation AEM forms. Si le service Output ne fait pas partie de votre installation d’AEM forms lors de l’assemblage d’un formulaire XFA dynamique, une exception est générée. Voir [Création de flux de sortie de document](/help/forms/developing/creating-document-output-streams.md).

>[!NOTE]
>
>Avant de lire cette section, il est recommandé de vous familiariser avec l’assemblage de documents PDF à l’aide du service Assembler. Cette section ne traite pas des concepts, tels que la création d’un objet de collection contenant des documents d’entrée ou l’apprentissage de l’extraction des résultats à partir de l’objet de collection renvoyé. (Voir [Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour assembler un document de PDF non interactif, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Référencez un document de PDF interactif.
1. Définissez les options d’exécution.
1. Assemblez le document du PDF.
1. Enregistrez le document de PDF non interactif.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge autre que JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé.

**Création d’un client Assembler**

Avant d’effectuer une opération Assembler par programmation, vous devez créer un client de service Assembler.

**Référence à un document DDX existant**

Un document DDX doit être référencé pour assembler un document de PDF. Ce document DDX doit contenir la variable `NoXFA` , qui indique au service Assembler de renvoyer un document de PDF non interactif.

**Référence à un document de PDF interactif**

Un document de PDF interactif doit être référencé et transmis au service Assembler pour récupérer un document de PDF non interactif.

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lors de l’exécution d’une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur.

**Assemblage du document du PDF**

Après avoir créé le client de service Assembler, référencé le document DDX, référencé un document de PDF interactif et défini les options d’exécution, vous pouvez appeler la méthode `invokeOneDocument` opération. Étant donné qu’un seul document du PDF d’entrée est transmis au service Assembler et qu’un seul document est renvoyé, vous pouvez utiliser la variable `invokeOneDocument` par opposition à l’opération `invokeDDX` opération.

**Enregistrement du document de PDF non interactif**

Si un seul document de PDF est transmis au service Assembler, le service Assembler renvoie un seul document au lieu d’un objet de collection. En d’autres termes, lors de l’appel de la variable `invokeOneDocument` , un seul document est renvoyé. Comme le document DDX référencé dans cette section contient des instructions pour créer un document de PDF non interactif, le service Assembler renvoie un document de PDF non interactif qui peut être enregistré en tant que fichier de PDF.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblage d’un document de PDF non interactif à l’aide de l’API Java {#assemble-a-non-interactive-pdf-document-using-the-java-api}

Assemblez un document de PDF non interactif à l’aide de l’API du service Assembler (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Référencez un document de PDF interactif.

   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement d’un document de PDF interactif.
   * Créez un `com.adobe.idp.Document` et transmettez la variable `java.io.FileInputStream` contenant le document du PDF. Ceci `com.adobe.idp.Document` est transmis à l’objet `invokeOneDocument` .

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Assemblez le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeOneDocument` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document DDX. Assurez-vous que ce document DX contient la valeur `inDoc` pour l’élément source du PDF.
   * A `com.adobe.idp.Document` contenant le document du PDF interactif.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation des tâches.

   Le `invokeOneDocument` renvoie une `com.adobe.idp.Document` contenant un document de PDF non interactif.

1. Enregistrez le document de PDF non interactif.

   * Créez un `java.io.File` et assurez-vous que l’extension de nom de fichier est .pdf.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` vers le fichier . Veillez à utiliser la variable `Document` qui `invokeOneDocument` est renvoyée.

* &quot;Démarrage rapide (mode SOAP) : Assemblage d’un document de PDF non interactif à l’aide de l’API Java&quot;

## Assemblage d’un document de PDF non interactif à l’aide de l’API de service Web {#assemble-a-non-interactive-pdf-document-using-the-web-service-api}

Assemblez un document de PDF non interactif à l’aide de l’API Assembler Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un client Assembler.

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

1. Référencez un document de PDF interactif.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF d’entrée. Ceci `BLOB` est transmis à l’objet `invokeOneDocument` comme argument.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` membre de données.

1. Assemblez le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeOneDocument` et transmettez les valeurs suivantes :

   * A `BLOB` objet représentant le document DDX
   * A `BLOB` objet représentant le document de PDF interactif
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeOneDocument` renvoie une `BLOB` contenant un document de PDF non interactif.

1. Enregistrez le document de PDF non interactif.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document de PDF non interactif et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui `invokeOneDocument` est renvoyée. Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

* &quot;Démarrage rapide (MTOM) : Assemblage d’un document de PDF non interactif à l’aide de l’API de service Web&quot;.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
