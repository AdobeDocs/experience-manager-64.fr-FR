---
title: Création de documents PDF avec des données XML envoyées
seo-title: Creating PDF Documents with SubmittedXML Data
description: Utilisez le service Forms pour récupérer les données de formulaire saisies par l’utilisateur dans un formulaire interactif. Transmettez les données de formulaire à une autre opération de service AEM Forms et créez un document de PDF à l’aide des données.
seo-description: Use the Forms service to retrieve the form data that the user entered into an interactive form. Pass the form data to another AEM Forms service operation and create a PDF document using the data.
uuid: 2676c614-8988-451b-ac7c-bd07731a3f5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 62490230-a24e-419d-95bb-c0bb04a03f96
role: Developer
exl-id: a0d6e4a6-751f-4cab-842b-08719b899060
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 4%

---

# Création de documents PDF avec des données XML envoyées {#creating-pdf-documents-with-submittedxml-data}

## Création de documents PDF avec des données XML envoyées {#creating-pdf-documents-with-submitted-xml-data}

Les applications Web qui permettent aux utilisateurs de remplir des formulaires interactifs requièrent que les données soient renvoyées au serveur. Le service Forms vous permet de récupérer les données de formulaire saisies par l’utilisateur dans un formulaire interactif. Vous pouvez ensuite transmettre les données de formulaire à une autre opération de service AEM Forms et créer un document de PDF à l’aide des données.

>[!NOTE]
>
>Avant de lire ce contenu, il est recommandé de bien comprendre la gestion des formulaires envoyés. Les concepts tels que la relation entre une conception de formulaire et les données XML envoyées sont abordés dans la section Gestion des Forms envoyées.

Tenez compte du workflow suivant qui implique trois services AEM Forms :

* Un utilisateur envoie des données XML au service Forms à partir d’une application Web.
* Le service Forms est utilisé pour traiter le formulaire envoyé et extraire les champs de formulaire. Les données de formulaire peuvent être traitées. Par exemple, les données peuvent être envoyées à une base de données d’entreprise.
* Les données de formulaire sont envoyées au service Output pour créer un document de PDF non interactif.
* Le document de PDF non interactif est stocké dans Content Services (obsolète).

Le diagramme suivant fournit une représentation visuelle de ce workflow.

![cd_cd_finsrv_architecture_xml_pdf1](assets/cd_cd_finsrv_architecture_xml_pdf1.png)

Une fois que l’utilisateur a envoyé le formulaire à partir du navigateur Web client, le document de PDF non interactif est stocké dans Content Services (obsolète). L’illustration suivante présente un document PDF stocké dans Content Services (obsolète).

![cd_cd_cs_gui](assets/cd_cd_cs_gui.png)

### Résumé des étapes {#summary-of-steps}

Pour créer un document de PDF non interactif avec les données XML envoyées et le stocker dans le document de PDF dans Content Services (obsolète), effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez des objets Forms, Output et Document Management.
1. Récupérez les données de formulaire à l’aide du service Forms.
1. Créez un document de PDF non interactif à l’aide du service Output.
1. Stockez le formulaire du PDF dans Content Services (obsolète) à l’aide du service Document Management.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’objets Forms, Output et Document Management**

Avant d’effectuer par programmation une opération d’API de service Forms, créez un objet API client Forms. De même, comme ce workflow appelle les services Output et Document Management, créez un objet API Output Client et un objet API Document Management Client .

**Récupération des données de formulaire à l’aide du service Forms**

Récupérez les données de formulaire qui ont été envoyées au service Forms. Vous pouvez traiter les données envoyées pour répondre aux besoins de votre entreprise. Par exemple, vous pouvez stocker des données de formulaire dans une base de données d’entreprise. Toutefois, pour créer un document de PDF non interactif, les données de formulaire sont transmises au service Output.

**Créez un document de PDF non interactif à l’aide du service Output.**

Utilisez le service Output pour créer un document de PDF non interactif basé sur une conception de formulaire et des données de formulaire XML. Dans le workflow, les données de formulaire sont récupérées à partir du service Forms.

**Stockage du formulaire du PDF dans Content Services (obsolète) à l’aide du service Document Management**

Utilisez l’API du service Document Management pour stocker un document de PDF dans Content Services (obsolète).

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

### Création d’un document PDF avec des données XML envoyées à l’aide de l’API Java {#create-a-pdf-document-with-submitted-xml-data-using-the-java-api}

Créez un document de PDF avec les données XML envoyées à l’aide de l’API Forms, Output et Document Management (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, adobe-output-client.jar et adobe-contentservices-client.jar dans le chemin de classe de votre projet Java.

1. Création d’objets Forms, Output et Document Management

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 
   * Créez un `OutputClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .
   * Créez un objet `DocumentManagementServiceClientImpl` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupération des données de formulaire à l’aide du service Forms

   * Appeler la variable `FormsServiceClient` de `processFormSubmission` et transmettez les valeurs suivantes :

      * Le `com.adobe.idp.Document` contenant les données de formulaire.
      * Une valeur string qui spécifie les variables d’environnement, y compris tous les en-têtes HTTP pertinents. Indiquez le type de contenu à gérer en spécifiant une ou plusieurs valeurs pour la variable `CONTENT_TYPE` Variable d’environnement. Par exemple, pour gérer les données XML, spécifiez la valeur de chaîne suivante pour ce paramètre : `CONTENT_TYPE=text/xml`.
      * Une valeur string qui spécifie la variable `HTTP_USER_AGENT` valeur d’en-tête, telle que `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * A `RenderOptionsSpec` qui stocke les options d’exécution.

      Le `processFormSubmission` renvoie une `FormsResult` contenant les résultats de l’envoi du formulaire.

   * Déterminez si le service Forms a terminé le traitement des données de formulaire en appelant la fonction `FormsResult` de `getAction` . Si cette méthode renvoie la valeur `0`, les données sont prêtes à être traitées.
   * Récupération des données de formulaire en créant une `com.adobe.idp.Document` en appelant le `FormsResult` de `getOutputContent` . (Cet objet contient des données de formulaire qui peuvent être envoyées au service Output.)
   * Créez un `java.io.InputStream` en appelant le `java.io.DataInputStream` constructeur et transmission de `com.adobe.idp.Document` .
   * Créez un `org.w3c.dom.DocumentBuilderFactory` en appelant le statique `org.w3c.dom.DocumentBuilderFactory` de `newInstance` .
   * Créez un `org.w3c.dom.DocumentBuilder` en appelant le `org.w3c.dom.DocumentBuilderFactory` de `newDocumentBuilder` .
   * Créez un `org.w3c.dom.Document` en appelant le `org.w3c.dom.DocumentBuilder` de `parse` et transmission de la méthode `java.io.InputStream` .
   * Récupérez la valeur de chaque noeud dans le document XML. Pour accomplir cette tâche, vous pouvez créer une méthode personnalisée qui accepte deux paramètres : la valeur `org.w3c.dom.Document` et le nom du noeud dont vous souhaitez récupérer la valeur. Cette méthode renvoie une valeur string représentant la valeur du noeud. Dans l’exemple de code qui suit ce processus, cette méthode personnalisée est appelée `getNodeText`. Le corps de cette méthode s’affiche.


1. Créez un document de PDF non interactif à l’aide du service Output.

   Créez un document de PDF en appelant la méthode `OutputClient` de `generatePDFOutput` et transmission des valeurs suivantes :

   * A `TransformationFormat` valeur d’énumération. Pour générer un document de PDF, spécifiez `TransformationFormat.PDF`.
   * Valeur string spécifiant le nom de la nouvelle conception de formulaire. Assurez-vous que la conception de formulaire est compatible avec les données de formulaire extraites du service Forms.
   * Une valeur string qui spécifie la racine de contenu où se trouve la conception de formulaire.
   * A `PDFOutputOptionsSpec` contenant les options d’exécution du PDF.
   * A `RenderOptionsSpec` contenant les options d’exécution de rendu.
   * Le `com.adobe.idp.Document` contenant la source de données XML contenant les données à fusionner avec la conception de formulaire. Assurez-vous que cet objet a été renvoyé par la variable `FormsResult` de `getOutputContent` .
   * Le `generatePDFOutput` renvoie une `OutputResult` contenant les résultats de l’opération.
   * Récupérez le document de PDF non interactif en appelant la méthode `OutputResult` de `getGeneratedDoc` . Cette méthode renvoie une `com.adobe.idp.Document` qui représente le document de PDF non interactif.

1. Stockage du formulaire du PDF dans Content Services (obsolète) à l’aide du service Document Management

   Ajoutez le contenu en appelant la méthode `DocumentManagementServiceClientImpl` de `storeContent` et transmission des valeurs suivantes :

   * Une valeur string qui spécifie le magasin où le contenu est ajouté. Le magasin par défaut est `SpacesStore`. Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie le chemin d’accès complet de l’espace où le contenu est ajouté (par exemple, `/Company Home/Test Directory`). Cette valeur est un paramètre obligatoire.
   * Nom du noeud qui représente le nouveau contenu (par exemple, `MortgageForm.pdf`). Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie le type de noeud. Pour ajouter un nouveau contenu, tel qu’un fichier de PDF, spécifiez `{https://www.alfresco.org/model/content/1.0}content`. Cette valeur est un paramètre obligatoire.
   * A `com.adobe.idp.Document` qui représente le contenu. Cette valeur est un paramètre obligatoire.
   * Une valeur string qui spécifie la valeur de codage (par exemple, `UTF-8`). Cette valeur est un paramètre obligatoire.
   * Un `UpdateVersionType` valeur d’énumération qui spécifie comment gérer les informations de version (par exemple, `UpdateVersionType.INCREMENT_MAJOR_VERSION` pour incrémenter la version du contenu. ) Cette valeur est un paramètre obligatoire.
   * A `java.util.List` qui spécifie les aspects liés au contenu. Cette valeur est un paramètre facultatif et vous pouvez spécifier `null`.
   * A `java.util.Map` qui stocke les attributs de contenu.

   Le `storeContent` renvoie une `CRCResult` qui décrit le contenu. Utilisation d’une `CRCResult` , vous pouvez, par exemple, obtenir la valeur d’identifiant unique du contenu. Pour effectuer cette tâche, appelez la fonction `CRCResult` de `getNodeUuid` .

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
