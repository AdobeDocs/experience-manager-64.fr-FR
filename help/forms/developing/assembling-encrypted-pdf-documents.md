---
title: Assemblage de documents PDF chiffrés
seo-title: Assembling Encrypted PDF Documents
description: Assemblez des documents PDF chiffrés à l’aide de l’API Java et de l’API Web Service.
seo-description: Assemble encrypted PDF documents using the Java API and Web Service API.
uuid: d0948ec9-ab67-4fe4-9062-1c4938460b43
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 6d75c7b1-9c0e-47f3-bdb1-61acf16b97f9
role: Developer
exl-id: fa543e13-f920-4b77-9762-36f115261e8c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1645'
ht-degree: 6%

---

# Assemblage de documents PDF chiffrés {#assembling-encrypted-pdf-documents}

Vous pouvez chiffrer un document PDF avec un mot de passe à l’aide du service Assembler. Après le chiffrement d’un document PDF avec un mot de passe, l’utilisateur doit spécifier un mot de passe pour l’afficher dans Adobe Reader ou Acrobat. Pour chiffrer un document PDF avec un mot de passe, le document DDX doit contenir les valeurs d’élément de chiffrement requises.

Dans le cadre de cette discussion, supposons que le document DDX suivant soit utilisé.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
        <PDF result="EncryptLoan.pdf" encryption="userProtect"> 
         <PDF source="inDoc" /> 
     </PDF> 
     <PasswordEncryptionProfile name="userProtect" compatibilityLevel="Acrobat7"> 
         <OpenPassword>AdobeOpen</OpenPassword> 
        </PasswordEncryptionProfile> 
 </DDX>
```

Dans ce document DDX, notez que la valeur est affectée à l’attribut source. `inDoc`. Dans les cas où un seul document de PDF d’entrée est transmis au service Assembler et où un seul document de PDF est renvoyé, vous appelez la méthode `invokeOneDocument` opération, attribuer la valeur `inDoc` à l’attribut source du PDF. Lors de l’appel de la fonction `invokeOneDocument` l’opération `inDoc` est une clé prédéfinie qui doit être spécifiée dans le document DDX.

En revanche, lors de la transmission de plusieurs documents de PDF d’entrée au service Assembler, vous pouvez appeler la fonction `invokeDDX` opération. Dans ce cas, attribuez le nom de fichier du document du PDF d’entrée au `source` attribut.

Le service Encryption ne doit pas nécessairement faire partie de votre installation AEM forms pour chiffrer un document PDF avec un mot de passe. Voir [Chiffrement et déchiffrement des documents du PDF](/help/forms/developing/encrypting-decrypting-pdf-documents.md).

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour assembler un document de PDF chiffré, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Référencez un document de PDF non sécurisé.
1. Définissez les options d’exécution.
1. Chiffrez le document.
1. Enregistrez le document de PDF chiffré.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge autre que JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé. Pour plus d’informations sur l’emplacement de tous les fichiers JAR AEM Forms, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Assembler**

Avant d’effectuer une opération Assembler par programmation, vous devez créer un client de service Assembler.

**Référence à un document DDX existant**

Un document DDX doit être référencé pour assembler un document de PDF. Prenons l’exemple du document DDX introduit dans cette section. Pour chiffrer un document de PDF, le document DDX doit contenir le `PasswordEncryptionProfile` élément .

**Référence à un document de PDF non sécurisé**

Un document de PDF non sécurisé doit être référencé et transmis au service Assembler pour le chiffrer. Si vous référencez un document de PDF déjà chiffré, une exception est générée.

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lorsqu’il effectue une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur. Pour plus d’informations sur les options d’exécution que vous pouvez définir, voir `AssemblerOptionSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Chiffrer le document**

Après avoir créé le client de service Assembler, référencez le document DDX contenant des informations de chiffrement, référencez un document de PDF non sécurisé et définissez les options d’exécution, vous pouvez appeler le `invokeOneDocument` opération. Étant donné qu’un seul document du PDF d’entrée est transmis au service Assembler (et qu’un seul document est renvoyé), vous pouvez utiliser la variable `invokeOneDocument` au lieu de l’opération `invokeDDX` opération.

**Enregistrement du document de PDF chiffré**

Si un seul document de PDF est transmis au service Assembler, le service Assembler renvoie un seul document au lieu d’un objet de collection. En d’autres termes, lors de l’appel de la variable `invokeOneDocument` , un seul document est renvoyé. Comme le document DDX référencé dans cette section contient des informations de chiffrement, le service Assembler renvoie un document PDF chiffré avec un mot de passe.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblage d’un document de PDF chiffré à l’aide de l’API Java {#assemble-an-encrypted-pdf-document-using-the-java-api}

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Référencez un document de PDF non sécurisé.

   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement d’un document de PDF non sécurisé.
   * Créez un `com.adobe.idp.Document` et transmettez la variable `java.io.FileInputStream` contenant le document du PDF. Ceci `com.adobe.idp.Document` est transmis à l’objet `invokeOneDocument` .

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Chiffrez le document.

   Appeler la variable `AssemblerServiceClient` de `invokeOneDocument` et transmettez les valeurs suivantes :

   * A `com.adobe.idp.Document` qui représente le document DDX. Assurez-vous que ce document DX contient la valeur `inDoc` pour l’élément source du PDF.
   * A `com.adobe.idp.Document` contenant le document de PDF non sécurisé.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation des tâches.

   Le `invokeOneDocument` renvoie une `com.adobe.idp.Document` contenant un document de PDF chiffré par mot de passe.

1. Enregistrez le document de PDF chiffré.

   * Créez un `java.io.File` et assurez-vous que l’extension de nom de fichier est .pdf.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` vers le fichier . Veillez à utiliser la variable `Document` qui `invokeOneDocument` est renvoyée.

**Voir également**

[Démarrage rapide (mode SOAP) : Assemblage d’un document de PDF chiffré à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-an-encrypted-pdf-document-using-the-java-api)

## Assemblage d’un document de PDF chiffré à l’aide de l’API de service Web {#assemble-an-encrypted-pdf-document-using-the-web-service-api}

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante lors de la définition d’une référence de service : `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Référencez un document de PDF non sécurisé.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF d’entrée. Ceci `BLOB` est transmis à l’objet `invokeOneDocument` comme argument.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` membre de données.

1. Chiffrez le document.

   Appeler la variable `AssemblerServiceClient` de `invokeOneDocument` et transmettez les valeurs suivantes :

   * A `BLOB` objet représentant le document DDX
   * A `BLOB` qui représente le document de PDF non sécurisé
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeOneDocument` renvoie une `BLOB` contenant un document de PDF chiffré.

1. Enregistrez le document de PDF chiffré.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document de PDF chiffré et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` qui `invokeOneDocument` est renvoyée. Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
