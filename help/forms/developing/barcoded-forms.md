---
title: Utilisation de formulaires à code-barres
seo-title: Working with barcoded forms
description: Décodez les données d’un formulaire de PDF ou d’une image contenant un code à barres à l’aide de l’API Java et de l’API Web Service.
seo-description: Decode data from a PDF form or an image that contains a barcode using the Java API and Web Service API.
uuid: e56c3c94-384d-401f-b418-dd34cdc57eda
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: eb28ac30-265c-4611-8247-1f4bc826f254
role: Developer
exl-id: 9d459939-a311-4770-84db-f2a4b7869072
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1906'
ht-degree: 2%

---

# Utilisation de formulaires à code-barres {#working-with-barcoded-forms}

## À propos du service Barcoded Forms {#about-the-barcoded-forms-service}

Le service Barcoded Forms automatise la capture de données à partir de formulaires de remplissage et d’impression et intègre les informations capturées aux systèmes informatiques de base d’une entreprise.

Grâce au service Barcoded Forms, vous pouvez ajouter des codes à barres unidimensionnels et bidimensionnels aux PDF forms interactifs. Vous pouvez ensuite publier les formulaires à code-barres sur un site web ou les distribuer par email ou CD. Lorsqu’un utilisateur remplit un formulaire à code à barres à l’aide d’Adobe Reader, d’Acrobat Professional ou d’Acrobat Standard, le code à barres est automatiquement mis à jour pour coder les données de formulaire fournies par l’utilisateur. L’utilisateur peut envoyer le formulaire par voie électronique ou l’imprimer sur papier et le soumettre par courrier, par fax ou main. Vous pouvez ensuite extraire les données fournies par l’utilisateur dans le cadre d’un workflow automatisé, en acheminant les données entre les processus d’approbation et les systèmes d’entreprise.

Pour plus d’informations sur le service Barcoded Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Décodage des données de formulaire à code-barres {#decoding-barcoded-form-data}

Vous pouvez utiliser l’API du service Barcoded Forms pour décoder les données d’un formulaire de PDF ou d’une image contenant un code à barres. Le décodage des données de formulaire consiste à extraire les données qui se trouvent dans le code à barres. Avant que les données ne puissent être décodées à partir d’un formulaire (ou d’une image) de PDF, un utilisateur doit remplir le formulaire avec des données.

>[!NOTE]
>
>Pour plus d’informations sur le service Barcoded Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour décoder les données d’un formulaire de PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Barcoded FormsClient .
1. Obtenez un formulaire de PDF contenant des données à code à barres.
1. Décodez les données du formulaire du PDF.
1. Convertissez les données en une source de données XML.
1. Traitez les données décodées.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utility.jar (Obligatoire si AEM Forms est déployé sur JBoss)
* jbossall-client.jar (requis si AEM Forms est déployé sur JBoss)
* xercesImpl.jar (situé dans &lt;install directory=&quot;&quot;>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdparty)

Si AEM Forms est déployé sur un serveur d’applications J2EE pris en charge qui n’est pas JBOSS, vous devez remplacer adobe-utility.jar et jbossall-client.jar par des fichiers JAR spécifiques au serveur d’applications J2EE sur lequel AEM Forms est déployé. Pour plus d’informations sur l’emplacement de tous les fichiers JAR AEM Forms, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un objet API client de formulaires à code à barres**

Avant de pouvoir effectuer par programmation une opération de service Barcoded Forms, vous devez créer un client de service Barcoded Forms. Si vous utilisez l’API Java, créez une `BarcodedFormsServiceClient` . Si vous utilisez l’API du service Web de formulaires à code à barres, créez une `BarcodedFormsServiceService` .

**Obtention d’un formulaire PDF contenant des données à code à barres**

Vous devez obtenir un formulaire PDF contenant un code à barres contenant des données utilisateur.

**Décoder les données du formulaire du PDF**

Après avoir obtenu un formulaire (ou une image) de PDF contenant un code à barres, vous pouvez décoder les données. Le service Barcoded Forms prend en charge les types de codes à barres suivants :

* Codes à barres PDF417.
* Codes à barres de la matrice de données.
* Codes à barres de code QR.
* Codes à barres Codabar.
* Codes à barres Code 128.
* Codes à barres Code 39.
* Codes à barres EAN-13.
* Codes à barres EAN-8.

L’entrée de jeu de caractères au format hexadécimal dans l’API de décodage implique que le contenu du code à barres soit codé en tant que chaîne hexadécimale. Par exemple, si UTF-8 est spécifié en tant que codage de caractères dans le formulaire et que Hex est spécifié dans l’opération de décodage, le contenu du code à barres est codé sous la forme d’une chaîne hexadécimale dans la balise &lt; `xb:content`> dans la sortie décodée. Vous pouvez convertir cette valeur Hex pour obtenir le contenu d’origine en créant la logique d’application dans votre application cliente.

**Convertir les données en source de données XML**

Après avoir décodé les données de formulaire, vous pouvez les convertir en données XDP ou XFDF. Supposons, par exemple, que vous souhaitiez importer les données dans un autre formulaire. Pour importer les données dans un formulaire XFA, vous devez convertir les données en données XDP. Pour plus d’informations, voir [Importation de données de formulaire](/help/forms/developing/importing-exporting-data.md#importing-form-data).

**Traitement des données décodées**

Vous pouvez traiter les données converties pour répondre aux besoins de votre entreprise. Par exemple, après avoir décodé et converti les données, vous pouvez les enregistrer dans un fichier, les stocker dans une base de données d’entreprise, remplir un autre formulaire, etc. Cette section explique comment enregistrer les données converties sous la forme d’un fichier XML.

>[!NOTE]
>
>Le service Barcoded Forms ne parvient pas à décoder les données de code à barres lorsque le délimiteur de ligne et les paramètres de délimiteur de champ ont la même valeur.

**Voir également**

[Décodez les données de formulaire à code à barres à l’aide de l’API Java.](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[Décodez les données de formulaire à code à barres à l’aide de l’API du service Web.](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Décodez les données de formulaire à code à barres à l’aide de l’API Java. {#decode-barcoded-form-data-using-the-java-api}

Décodez les données de formulaire à l’aide de l’API Barcoded Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client dans le chemin de classe de votre projet Java.

1. Création d’un objet API client de formulaires à code à barres

   Créez un `BarcodedFormsServiceClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Obtention d’un formulaire PDF contenant des données à code à barres

   * Créez un `java.io.FileInputStream` qui représente le formulaire du PDF contenant des données à code à barres en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Décoder les données du formulaire du PDF

   Décodez les données du formulaire en appelant la fonction `BarcodedFormsServiceClient` de `decode` et transmission des valeurs suivantes :

   * Le `com.adobe.idp.Document` contenant le formulaire du PDF.
   * A `java.lang.Boolean` qui spécifie s’il faut décoder un code à barres PDF417.
   * A `java.lang.Boolean` qui spécifie s’il faut décoder un code à barres de la matrice de données.
   * A `java.lang.Boolean` qui spécifie s’il faut décoder un code à barres de code QR.
   * A `java.lang.Boolean` qui spécifie s’il faut décoder un code à barres codabar.
   * A `java.lang.Boolean` qui spécifie s’il faut décoder un code à barres 128.
   * A `java.lang.Boolean` qui spécifie s’il faut décoder un code à barres 39.
   * A `java.lang.Boolean` qui spécifie s’il faut décoder un code à barres EAN-13.
   * A `java.lang.Boolean` qui spécifie s’il faut décoder un code à barres EAN-8.
   * A `com.adobe.livecycle.barcodedforms.CharSet` valeur d’énumération spécifiant la valeur de codage du jeu de caractères utilisée dans le code à barres.

   Le `decode` renvoie une `org.w3c.dom.Document` contenant des données de formulaire décodées.

1. Convertir les données en source de données XML

   Convertissez les données décodées en données XDP ou XFDF en appelant la fonction `BarcodedFormsServiceClient` de `extractToXML` et transmission des valeurs suivantes :

   * Le `org.w3c.dom.Document` qui contient des données décodées (veillez à utiliser l’objet `decode` valeur renvoyée par la méthode).
   * A `com.adobe.livecycle.barcodedforms.Delimiter` valeur d’énumération qui spécifie le délimiteur de ligne. Il est recommandé de spécifier `Delimiter.Carriage_Return`.
   * A `com.adobe.livecycle.barcodedforms.Delimiter` valeur d’énumération qui spécifie le délimiteur de champ. Par exemple, spécifiez `Delimiter.Tab`.
   * A `com.adobe.livecycle.barcodedforms.XMLFormat` valeur d’énumération qui spécifie s’il faut convertir les données du code à barres en données XML XDP ou XFDF. Par exemple, spécifiez `XMLFormat.XDP` pour convertir les données en données XDP.

   >[!NOTE]
   >
   >Ne spécifiez pas les mêmes valeurs pour les paramètres de délimiteur de ligne et de délimiteur de champ.

   Le `extractToXML` renvoie une `java.util.List` où chaque élément est un objet `org.w3c.dom.Document` . Il existe un élément distinct pour chaque code à barres situé sur le formulaire. En d’autres termes, s’il y a quatre codes à barres sur le formulaire, il y a quatre éléments dans le renvoyé. `java.util.List` .

1. Traitement des données décodées

   * Effectuez une itération à l’aide du `java.util.List` pour obtenir chaque objet `org.w3c.dom.Document` situé dans la liste.
   * Pour chaque élément de la liste, convertissez la variable `org.w3c.dom.Document` vers un objet `com.adobe.idp.Document` . (logique de l’application qui convertit une `org.w3c.dom.Document` en objet `com.adobe.idp.Document` s’affiche dans l’exemple Décodage des données de formulaire à code à barres à l’aide de l’API Java ).
   * Enregistrez les données XML en tant que fichier XML en appelant la méthode `com.adobe.idp.Document` de `copyToFile`, et transmission d’un objet File représentant le fichier XML.

**Voir également**

[Démarrage rapide (mode SOAP) : Décodage des données de formulaire à code à barres à l’aide de l’API Java](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Décodez les données de formulaire à code à barres à l’aide de l’API du service Web. {#decode-barcoded-form-data-using-the-web-service-api}

Décodez les données de formulaire à l’aide de l’API Barcoded Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez un assemblage client Microsoft .NET qui utilise le WSDL du service Barcoded Forms. Pour plus d’informations, voir [Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).
   * Référencez l’assemblage client Microsoft .NET. Pour plus d’informations, voir &quot;Référence à l’assemblage client .NET&quot; dans [Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Création d’un objet API client de formulaires à code à barres

   À l’aide de l’assemblage client Microsoft .NET qui utilise le WSDL du service Barcoded Forms, créez une `BarcodedFormsServiceService` en appelant son constructeur par défaut.

1. Obtention d’un formulaire PDF contenant des données à code à barres

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document PDF contenant un code à barres.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `binaryData` avec le contenu du tableau d’octets.

1. Décoder les données du formulaire du PDF

   Décodez les données du formulaire en appelant la fonction `BarcodedFormsServiceService` de `decode` et transmission des valeurs suivantes :

   * Le `BLOB` contenant le formulaire du PDF.
   * A `Boolean` qui spécifie s’il faut décoder un code à barres PDF417.
   * A `Boolean` qui spécifie s’il faut décoder un code à barres de la matrice de données.
   * A `Boolean` qui spécifie s’il faut décoder un code à barres de code QR.
   * A `Boolean` qui spécifie s’il faut décoder un code à barres codabar.
   * A `Boolean` qui spécifie s’il faut décoder un code à barres 128.
   * A `Bolean` qui spécifie s’il faut décoder un code à barres 39.
   * A `Boolean` qui spécifie s’il faut décoder un code à barres EAN-13.
   * A `Boolean` qui spécifie s’il faut décoder un code à barres EAN-8.
   * A `CharSet` valeur d’énumération spécifiant la valeur de codage du jeu de caractères utilisée dans le code à barres.

   Le `decode` renvoie une valeur string qui contient les données de formulaire décodées.

1. Convertir les données en source de données XML

   Convertissez les données décodées en données XDP ou XFDF en appelant la fonction `BarcodedFormsServiceService` de `extractToXML` et transmission des valeurs suivantes :

   * Une valeur string qui contient des données décodées (veillez à utiliser la variable `decode` valeur renvoyée par la méthode).
   * A `Delimiter` valeur d’énumération qui spécifie le délimiteur de ligne. Il est recommandé de spécifier `Delimiter.Carriage_Return`.
   * A `Delimiter` valeur d’énumération qui spécifie le délimiteur de champ. Par exemple, spécifiez `Delimiter.Tab`.
   * A `XMLFormat` valeur d’énumération qui spécifie s’il faut convertir les données du code à barres en données XML XDP ou XFDF. Par exemple, spécifiez `XMLFormat.XDP` pour convertir les données en données XDP.

   >[!NOTE]
   >
   >Ne spécifiez pas les mêmes valeurs pour les paramètres de délimiteur de ligne et de délimiteur de champ.

   Le `extractToXML` renvoie une `Object` tableau où chaque élément est un `BLOB` instance. Il existe un élément distinct pour chaque code à barres situé sur le formulaire. En d’autres termes, s’il y a quatre codes à barres sur le formulaire, il y a quatre éléments dans le renvoyé. `Object` tableau.

1. Traitement des données décodées

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF sécurisé.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `encryptPDFUsingPassword` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `binaryData` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
