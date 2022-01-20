---
title: Validation d’un document DDX à l’aide de l’API de service Web
seo-title: Validate a DDX document using theweb service API
description: Utilisez l’API du service Assembler pour valider un document DDX.
seo-description: Use the Assembler Service API to validate a DDX document.
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
role: Developer
exl-id: da303186-8f36-4fc8-a2db-b38a0b200c39
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 2%

---

# Validation d’un document DDX à l’aide de l’API de service Web {#validate-a-ddx-document-using-theweb-service-api}

Validez un document DDX à l’aide de l’API Assembler Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacez localhost par l’adresse IP du serveur Forms.

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

1. Définissez les options d’exécution pour valider le document DDX.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez l’option d’exécution qui indique au service Assembler de valider le document DDX en attribuant la valeur true à la propriété `AssemblerOptionSpec` de `validateOnly` membre de données.
   * Définissez la quantité d’informations que le service Assembler écrit dans le fichier journal en attribuant une valeur de chaîne à la variable `AssemblerOptionSpec` de `logLevel` membre de données. lors de la validation d’un document DDX, vous souhaitez obtenir plus d’informations écrites dans le fichier journal, ce qui facilite le processus de validation. Par conséquent, vous pouvez spécifier la valeur `FINE` ou `FINER`. Pour plus d’informations sur les options d’exécution que vous pouvez définir, voir `AssemblerOptionSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Effectuez la validation.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `BLOB` qui représente le document DDX.
   * La valeur `null` pour le `Map` qui stocke généralement des documents PDF.
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution.

   Le `invokeDDX` renvoie une `AssemblerResult` contenant des informations spécifiant si le document DDX est valide.

1. Enregistrez les résultats de la validation dans un fichier journal.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier journal et le mode d’ouverture du fichier. Assurez-vous que l’extension de nom de fichier est .xml.
   * Créez un `BLOB` qui stocke les informations du journal en obtenant la valeur de la variable `AssemblerResult` de `jobLog` membre de données.
   * Créez un tableau d’octets qui stocke le contenu de la variable `BLOB` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

   >[!NOTE]
   >
   >Si le document DDX n’est pas valide, une `OperationException` est généré. Dans l’instruction catch, vous pouvez obtenir la valeur de la variable `OperationException` de `jobLog` membre.

**Voir également**

[Validation de documents DDX](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
