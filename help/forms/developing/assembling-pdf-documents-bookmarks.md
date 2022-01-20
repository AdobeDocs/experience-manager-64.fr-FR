---
title: Assemblage de documents PDF avec des signets
seo-title: Assembling PDF Documents with Bookmarks
description: Utilisez le service Assembler pour modifier un document PDF qui contient des signets afin d’inclure des signets à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Assembler service to modify a PDF document that does contain bookmarks to include bookmarks using the Java API and the Web Service API.
uuid: a306d2a6-0b12-4eb3-bff4-968a33417486
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9f4711a8-033c-4051-ab41-65a26838899b
role: Developer
exl-id: 2506835b-a75b-4d15-8fd4-1292d40a2132
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2544'
ht-degree: 2%

---

# Assemblage de documents PDF avec des signets {#assembling-pdf-documents-with-bookmarks}

Vous pouvez assembler un document de PDF qui contient des signets. Supposons, par exemple, que vous ayez un document de PDF qui ne contient pas de signets et que vous souhaitiez le modifier en fournissant des signets. À l’aide du service Assembler, vous pouvez lui transmettre un document de PDF qui ne contient pas de signets et récupérer un document de PDF contenant des signets.

Les signets contiennent les propriétés suivantes :

* Titre qui s’affiche sous forme de texte à l’écran.
* Action qui spécifie ce qui se produit lorsqu’un utilisateur clique sur le signet. L’action type d’un signet consiste à déplacer vers un autre emplacement du document actif ou à ouvrir un autre document PDF, bien que d’autres actions puissent être spécifiées.

Dans le cadre de cette discussion, supposons que le document DDX suivant soit utilisé.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
       <PDF result="FinalDoc.pdf"> 
          <PDF source="Loan.pdf"> 
             <Bookmarks source="doc2" /> 
          </PDF> 
       </PDF> 
 </DDX>
```

Dans ce document DDX, notez que la valeur est affectée à l’attribut source. `Loan.pdf`. Ce document DDX indique qu’un seul document de PDF est transmis au service Assembler. Lors de l’assemblage d’un document de PDF avec des signets, vous devez spécifier un document XML de signet qui décrit les signets dans le document obtenu. Pour spécifier un document XML de signet, assurez-vous que la variable `Bookmarks` est spécifié dans votre document DX.

Dans cet exemple de document DX, la variable `Bookmarks` element indique `doc2` comme valeur. Cette valeur indique que la carte d’entrée transmise au service Assembler contient une clé nommée `doc2`. La valeur de la variable `doc2` key is a `com.adobe.idp.Document` qui représente le document XML du signet. (Voir &quot;Langue des signets&quot; dans la section [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).)

Cette rubrique utilise le langage de signets XML suivant pour assembler un document de PDF contenant des signets.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <Bookmarks xmlns="https://ns.adobe.com/pdf/bookmarks" version="1.0"> 
       <Bookmark> 
          <Action> 
             <Launch NewWindow="true"> 
                <File Name="C:\Adobe\LoanDetails.pdf" /> 
             </Launch> 
          </Action> 
         <Title>Open the Loan document</Title> 
       </Bookmark> 
 <Bookmark> 
          <Action> 
             <Launch> 
                <Win Name="C:\WINDOWS\notepad.exe" /> 
             </Launch> 
          </Action> 
     <Title>Launch NotePad</Title> 
       </Bookmark> 
 </Bookmarks>
```

Dans ce document XML de signet, notez l’élément Action qui définit l’action effectuée lorsqu’un utilisateur clique sur le signet. Sous l’élément Action se trouve l’élément Launch qui lance des applications, telles que RemarquePad, et ouvre des fichiers, tels que des fichiers PDF. Pour ouvrir un fichier de PDF, vous devez utiliser l’élément File qui spécifie le fichier à ouvrir. Par exemple, dans le fichier XML du signet spécifié dans cette section, le nom du fichier ouvert est LoanDetails.pdf.

>[!NOTE]
>
>Pour plus d’informations sur les actions prises en charge, voir &quot; `Action` &quot; dans le [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

Compte tenu du document DDX spécifié dans cette section et du signet du fichier XML en entrée, le service Assembler assemble un document PDF contenant les signets suivants.

![aw_aw_bmark](assets/aw_aw_bmark.png)

Lorsqu’un utilisateur clique sur la variable *Ouvrir les détails du prêt* , le fichier LoanDetails.pdf est ouvert. De même, lorsque l’utilisateur clique sur la variable *Launch NotePad* , RemarquePad est démarré.

>[!NOTE]
>
>Avant de lire cette section, il est recommandé de vous familiariser avec l’assemblage de documents PDF à l’aide du service Assembler. Cette section ne traite pas des concepts, tels que la création d’un objet de collection contenant des documents d’entrée ou l’apprentissage de l’extraction des résultats à partir de l’objet de collection renvoyé. (Voir [Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents).)

>[!NOTE]
>
>Pour plus d’informations sur le service Assembler, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur un document DDX, voir [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Résumé des étapes {#summary-of-steps}

Pour assembler un document PDF contenant des signets, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un client Assembler de PDF.
1. Référencez un document DX existant.
1. Référencez un document de PDF auquel des signets sont ajoutés.
1. Référencez le document XML du signet.
1. Ajoutez le document du PDF et le document XML du signet à une collection Map.
1. Définissez les options d’exécution.
1. Assemblez le document du PDF.
1. Enregistrez le document du PDF qui contient des signets.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin de classe de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utility.jar (obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (obligatoire si AEM Forms est déployé sur JBoss)

si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge autre que JBoss, vous devez remplacer les fichiers adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé. Pour plus d’informations sur l’emplacement de tous les fichiers JAR AEM Forms, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un client Assembler PDF**

Avant d’effectuer une opération Assembler par programmation, vous devez créer un client de service Assembler.

**Référence à un document DDX existant**

Un document DDX doit être référencé pour assembler un document de PDF. Ce document DDX doit contenir la variable `Bookmarks` qui indique au service Assembler d’assembler un PDF contenant des signets. (Pour obtenir un exemple, reportez-vous au document DDX présenté précédemment dans cette section.)

**Référence à un document de PDF auquel des signets sont ajoutés**

Référencez un document de PDF auquel des signets sont ajoutés. Peu importe que le document de PDF référencé contienne déjà des signets. Si la variable `Bookmarks` Élément est un enfant de l’élément source du PDF, puis les signets remplaceront ceux qui existent déjà dans la source du PDF. Toutefois, si vous souhaitez conserver les signets existants, assurez-vous que `Bookmarks` est un frère de l’élément source du PDF. Prenons l’exemple suivant :

```as3
 <PDF result="foo"> 
      <PDF source="inDoc"/> 
      <Bookmarks source="doc2"/> 
 </PDF>
```

**Référence au document XML du signet**

Pour assembler un PDF contenant de nouveaux signets, vous devez référencer un document XML de signet. Le document XML du signet est transmis au service Assembler dans l’objet de collection Map. (Pour consulter un exemple, reportez-vous au document XML de signet illustré précédemment dans cette section.)

>[!NOTE]
>
>Voir &quot;Langue des signets&quot; dans la section [Guide de référence du service Assembler et de DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

**Ajout du document du PDF et du document XML du signet à une collection Map**

Vous devez ajouter le document du PDF auquel les signets sont ajoutés et le document XML du signet à la collection de cartes. Par conséquent, l’objet de collection Map contient deux éléments : un document PDF et le document XML du signet.

**Définition des options d’exécution**

Vous pouvez définir des options d’exécution qui contrôlent le comportement du service Assembler lors de l’exécution d’une tâche. Par exemple, vous pouvez définir une option qui indique au service Assembler de continuer à traiter une tâche en cas d’erreur. Pour plus d’informations sur les options d’exécution que vous pouvez définir, voir `AssemblerOptionSpec` référence de classe dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Assemblage du document du PDF**

Pour assembler un document PDF contenant de nouveaux signets, utilisez le `invokeDDX` opération. La raison pour laquelle vous devez utiliser la variable `invokeDDX` par opposition aux autres opérations du service Assembler, telles que `invokeOneDocument` car le service Assembler requiert un document XML de signet transmis dans l’objet de collection Map . Cet objet est un paramètre de la variable `invokeDDX` opération.

**Enregistrez le document du PDF qui contient des signets.**

Vous devez extraire les résultats de l’objet map renvoyé et enregistrer le document PDF correspondant. (Voir &quot;Extraction des résultats&quot; dans [Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Assemblage par programmation de documents PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblage de documents PDF avec des signets à l’aide de l’API Java {#assemble-pdf-documents-with-bookmarks-using-the-java-api}

Assemblez un document PDF avec des signets à l’aide de l’API Assembler Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-assembler-client.jar, dans le chemin d’accès à la classe de votre projet Java.

1. Créez un client Assembler de PDF.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion. (Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Créez un `AssemblerServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référencez un document DX existant.

   * Créez un `java.io.FileInputStream` qui représente le document DDX en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier DDX.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Référencez un document de PDF auquel des signets sont ajoutés.

   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement du document du PDF.
   * Créez un `com.adobe.idp.Document` en utilisant son constructeur et en transmettant la variable `java.io.FileInputStream` contenant le document du PDF.

1. Référencez le document XML du signet.

   * Créez un `java.io.FileInputStream` en utilisant son constructeur et en transmettant l’emplacement du fichier XML qui représente le document XML du signet.
   * Créez un `com.adobe.idp.Document` et transmettez la variable `java.io.FileInputStream` contenant le document du PDF.

1. Ajoutez le document du PDF et le document XML du signet à une collection Map.

   * Créez un `java.util.Map` qui permet de stocker le document du PDF d’entrée et le document XML du signet.
   * Ajoutez le document du PDF d’entrée en appelant la méthode `java.util.Map` de `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX.
      * A `com.adobe.idp.Document` contenant le document du PDF d’entrée.
   * Ajoutez le document XML du signet en appelant la fonction `java.util.Map` de `put` et transmission des arguments suivants :

      * Une valeur string qui représente le nom de la clé. Cette valeur doit correspondre à la valeur de l’élément source Signets spécifié dans le document DDX.
      * A `com.adobe.idp.Document` contenant le document XML du signet.


1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en appelant une méthode appartenant à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, appelez la fonction `AssemblerOptionSpec` de `setFailOnError` méthode et transmission `false`.

1. Assemblez le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs requises suivantes :

   * A `com.adobe.idp.Document` objet représentant le document DDX à utiliser
   * A `java.util.Map` qui contient le document de PDF d’entrée et le document XML de signet.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` qui spécifie les options d’exécution, y compris la police par défaut et le niveau de journalisation des tâches

   Le `invokeDDX` renvoie une `com.adobe.livecycle.assembler.client.AssemblerResult` contenant les résultats de la tâche et les exceptions survenues.

1. Enregistrez le document du PDF qui contient des signets.

   Pour obtenir le document de PDF nouvellement créé, procédez comme suit :

   * Appeler la variable `AssemblerResult` de `getDocuments` . Cette fonction renvoie une `java.util.Map` .
   * Effectuez une itération à l’aide du `java.util.Map` jusqu’à ce que vous trouviez le résultat `com.adobe.idp.Document` . (Vous pouvez utiliser l’élément de résultat PDF spécifié dans le document DDX pour obtenir le document.)
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour extraire le document du PDF.

**Voir également**

[Démarrage rapide (mode SOAP) : Assemblage de documents PDF avec des signets à l’aide de l’API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-documents-with-bookmarks-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblage de documents PDF avec des signets à l’aide de l’API du service Web {#assemble-pdf-documents-with-bookmarks-using-the-web-service-api}

Assemblez un document PDF avec des signets à l’aide de l’API Assembler Service (service Web) :

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

1. Référencez un document de PDF auquel des signets sont ajoutés.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le PDF d’entrée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Référencez le document XML du signet.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document XML du signet.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF d’entrée et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Ajoutez le document du PDF et le document XML du signet à une collection Map.

   * Créez un `MyMapOf_xsd_string_To_xsd_anyType` . Cet objet de collection est utilisé pour stocker les documents du PDF d’entrée et le document XML du signet.
   * Pour chaque document de PDF d’entrée et le document XML de signet , créez un `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Attribuez une valeur string qui représente le nom de la clé au `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` champ . Cette valeur doit correspondre à la valeur de l’élément source PDF spécifié dans le document DDX.
   * Attribuez le `BLOB` qui stocke le document du PDF dans la propriété `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` champ .
   * Ajoutez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` vers l’objet `MyMapOf_xsd_string_To_xsd_anyType` . Appeler la variable `MyMapOf_xsd_string_To_xsd_anyType` de `Add` et transmettez la méthode `MyMapOf_xsd_string_To_xsd_anyType` . (Effectuez cette tâche pour chaque document de PDF d’entrée et le document XML de signet.)

1. Définissez les options d’exécution.

   * Créez un `AssemblerOptionSpec` qui stocke les options d’exécution en utilisant son constructeur.
   * Définissez des options d’exécution pour répondre aux besoins de votre entreprise en attribuant une valeur à un membre de données qui appartient à la variable `AssemblerOptionSpec` . Par exemple, pour demander au service Assembler de continuer à traiter une tâche en cas d’erreur, affectez `false` au `AssemblerOptionSpec` de `failOnError` membre de données.

1. Assemblez le document du PDF.

   Appeler la variable `AssemblerServiceClient` de `invokeDDX` et transmettez les valeurs suivantes :

   * A `BLOB` objet représentant le document DDX
   * Le `MyMapOf_xsd_string_To_xsd_anyType` tableau contenant les documents d’entrée
   * Un `AssemblerOptionSpec` qui spécifie les options d’exécution

   Le `invokeDDX` renvoie une `AssemblerResult` contenant les résultats de la tâche et les exceptions qui peuvent s’être produites.

1. Enregistrez le document du PDF qui contient des signets.

   Pour obtenir le document de PDF nouvellement créé, procédez comme suit :

   * Accédez au `AssemblerResult` de `documents` , qui est un `Map` contenant les documents du PDF de résultats.
   * Effectuez une itération à l’aide du `Map` jusqu’à ce que vous trouviez la clé correspondant au nom du document généré. Collez ensuite le de `value` à `BLOB`.
   * Extrayez les données binaires qui représentent le document du PDF en accédant à ses `BLOB` de `MTOM` champ . Cette opération renvoie un tableau d’octets que vous pouvez écrire dans un fichier de PDF.

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
