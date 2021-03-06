---
title: Appel d’AEM Forms utilisant des services Web
seo-title: Invoking AEM Forms using Web Services
description: Appelez les processus AEM Forms à l’aide de services web avec une prise en charge complète de la génération WSDL.
seo-description: Invoke AEM Forms processes using web services with full support for WSDL generation.
uuid: 66bcd010-c476-4b66-831d-a48307d8d67a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: coding
discoiquuid: d5722281-bea9-4fc7-abdc-e678899e0a15
role: Developer
exl-id: cd4b5e40-afd5-422d-ae2e-cfde0f4d6b1a
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '9928'
ht-degree: 6%

---

# Appel d’AEM Forms utilisant des services Web {#invoking-aem-forms-using-web-services}

La plupart des services AEM Forms du conteneur de services sont configurés pour exposer un service Web, avec une prise en charge complète de la génération du langage de définition de service Web (WSDL). En d’autres termes, vous pouvez créer des objets proxy qui utilisent la pile SOAP native d’un service AEM Forms. Par conséquent, les services AEM Forms peuvent échanger et traiter les messages SOAP suivants :

* **requête SOAP**: Envoyé vers un service Forms par une application cliente demandant une action.
* **Réponse SOAP**: Envoyé à une application cliente par un service Forms après le traitement d’une requête SOAP.

Les services Web vous permettent d’effectuer les mêmes opérations de services AEM Forms que vous pouvez en utilisant l’API Java. L’utilisation des services web pour appeler les services AEM Forms présente l’avantage de permettre la création d’une application cliente dans un environnement de développement prenant en charge SOAP. Une application cliente n’est pas liée à un environnement de développement ou à un langage de programmation spécifique. Par exemple, vous pouvez créer une application cliente à l’aide de Microsoft Visual Studio .NET et C# en tant que langage de programmation.

Les services AEM Forms sont exposés via le protocole SOAP et sont conformes à WSI Basic Profile 1.1. Web Services Interoperability (WSI) est une organisation de normes ouvertes qui favorise l’interopérabilité des services Web entre les plateformes. Pour plus d’informations, voir [https://www.ws-i.org/](https://www.ws-i.org).

AEM Forms prend en charge les normes de service Web suivantes :

* **Encodage**: Prend uniquement en charge le codage de document et littéral (qui est le codage préféré selon le profil WSI de base). (Voir [Appel d’AEM Forms à l’aide du codage Base64](#invoking-aem-forms-using-base64-encoding).)
* **MTOM**: Représente un moyen de coder des pièces jointes avec des requêtes SOAP. (Voir [Appel d’AEM Forms à l’aide de MTOM](#invoking-aem-forms-using-mtom).)
* **SwaRef**: Représente une autre manière de coder des pièces jointes avec des requêtes SOAP. (Voir [Appel d’AEM Forms à l’aide de SwaRef](#invoking-aem-forms-using-swaref).)
* **SOAP avec pièces jointes**: Prend en charge les formats MIME et DIME (Direct Internet Message Encapsulation). Ces protocoles sont des moyens standard d’envoyer des pièces jointes sur SOAP. Les applications Microsoft Visual Studio .NET utilisent DIME. (Voir [Appel d’AEM Forms à l’aide du codage Base64](#invoking-aem-forms-using-base64-encoding).)
* **WS-Security**: Prend en charge un profil de jeton de mot de passe de nom d’utilisateur, qui est un moyen standard d’envoyer des noms d’utilisateur et des mots de passe dans l’en-tête SOAP de sécurité WS. AEM Forms prend également en charge l’authentification de base HTTP.

Pour appeler les services AEM Forms à l’aide d’un service Web, vous créez généralement une bibliothèque proxy qui utilise le WSDL du service. Le *Appel d’AEM Forms à l’aide de services web* utilise JAX-WS pour créer des classes proxy Java pour appeler des services. (Voir [Création de classes de proxy Java à l’aide de JAX-WS](#creating-java-proxy-classes-using-jax-ws).)

Vous pouvez récupérer un WDSL de service en spécifiant la définition d’URL suivante (les éléments entre crochets sont facultatifs) :

```as3
 https://<your_serverhost>:<your_port>/soap/services/<service_name>?wsdl[&version=<version>][&async=true|false][lc_version=<lc_version>]
```

où :

* *your_serverhost* représente l’adresse IP du serveur d’applications J2EE hébergeant AEM Forms.
* *your_port* représente le port HTTP utilisé par le serveur d’applications J2EE.
* *service_name* représente le nom du service.
* *version* représente la version cible d’un service (la dernière version du service est utilisée par défaut).
* `async` spécifie la valeur `true` pour activer des opérations supplémentaires pour un appel asynchrone ( `false` par défaut).
* *lc_version* représente la version d’AEM Forms que vous souhaitez appeler.

Le tableau suivant répertorie les définitions WSDL de service (en supposant qu’AEM Forms soit déployé sur l’hôte local et que la publication soit 8080).

<table> 
 <thead> 
  <tr> 
   <th><p>Service</p></th> 
   <th><p>Définition WSDL</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Assembler</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ AssemblerService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Retour et restauration</p></td> 
   <td><p><code>http://localhost:8080/soap/services/BackupService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Barcoded Forms</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ BarcodedFormsService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Convert PDF</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ ConvertPDFService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Distiller</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ DistillerService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>DocConverter </p></td> 
   <td><p><code>http://localhost:8080/soap/services/DocConverterService?WSDL</code></p></td> 
  </tr> 
  <tr> 
   <td><p>DocumentManagement</p></td> 
   <td><p><code>http://localhost:8080/soap/services/DocumentManagementService?WSDL</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Encryption (chiffrement) </p></td> 
   <td><p><code>http://localhost:8080/soap/services/EncryptionService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Formulaires</p></td> 
   <td><p><code>http://localhost:8080/soap/services/FormsService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Form Data Integration</p></td> 
   <td><p><code>http://localhost:8080/soap/services/FormDataIntegration?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Generate PDF</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ GeneratePDFService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Générer un PDF 3D</p></td> 
   <td><p><code>http://localhost:8080/soap/services/Generate3dPDFService?WSDL</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Sortie</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ OutputService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>PDF Utilities </p></td> 
   <td><p><code>http://localhost:8080/soap/services/ PDFUtilityService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Acrobat Reader DC Extensions</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ ReaderExtensionsService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Référentiel</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ RepositoryService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Gestion des droits </p></td> 
   <td><p><code>http://localhost:8080/soap/services/ RightsManagementService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>Signature </p></td> 
   <td><p><code>http://localhost:8080/soap/services/ SignatureService?wsdl</code></p></td> 
  </tr> 
  <tr> 
   <td><p>XMP Utilities</p></td> 
   <td><p><code>http://localhost:8080/soap/services/ XMPUtilityService?wsdl</code></p></td> 
  </tr> 
 </tbody> 
</table>

**Définitions WSDL du processus AEM Forms**

Vous devez spécifier le nom de l’application et le nom du processus dans la définition WSDL pour accéder à une WSDL qui appartient à un processus créé dans Workbench. Supposons que le nom de l’application soit `MyApplication` et le nom du processus est `EncryptDocument`. Dans ce cas, spécifiez la définition WSDL suivante :

```as3
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?wsdl
```

>[!NOTE]
>
>Pour plus d’informations sur l’exemple `MyApplication/EncryptDocument` processus de courte durée, voir [Exemple de processus de courte durée](/help/forms/developing/aem-forms-processes.md).

>[!NOTE]
>
>Une application peut contenir un ou plusieurs dossiers. Dans ce cas, indiquez le ou les noms de dossier dans la définition WSDL :

```as3
 http://localhost:8080/soap/services/MyApplication/[<folderA>/.../<folderZ>/]EncryptDocument?wsdl
```

**Accès aux nouvelles fonctionnalités à l’aide des services web**

La nouvelle fonctionnalité du service AEM Forms est accessible à l’aide des services web. Par exemple, dans AEM Forms, la possibilité de coder des pièces jointes à l’aide de MTOM est introduite. (Voir [Appel d’AEM Forms à l’aide de MTOM](#invoking-aem-forms-using-mtom).)

Pour accéder aux nouvelles fonctionnalités introduites dans AEM Forms, spécifiez la variable `lc_version` dans la définition WSDL. Par exemple, pour accéder à la nouvelle fonctionnalité de service (y compris la prise en charge de MTOM), spécifiez la définition WSDL suivante :

```as3
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?wsdl&lc_version=9.0.1
```

>[!NOTE]
>
>Lors de la définition de la variable `lc_version` , veillez à utiliser trois chiffres. Par exemple, 9.0.1 est égal à la version 9.0.

**Type de données BLOB de service Web**

Les WSDL de service AEM Forms définissent de nombreux types de données. L’un des types de données les plus importants exposés dans un service Web est un `BLOB` type. Ce type de données est mappé au `com.adobe.idp.Document` lors de l’utilisation des API Java AEM Forms. (Voir [Transmission de données aux services AEM Forms à l’aide de l’API Java](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

A `BLOB` envoie et récupère des données binaires (par exemple, des fichiers de PDF, des données XML, etc.) vers et depuis les services AEM Forms. Le `BLOB` type est défini dans un WSDL de service comme suit :

```as3
 <complexType name="BLOB"> 
     <sequence> 
         <element maxOccurs="1" minOccurs="0" name="contentType" 
             type="xsd:string"/> 
         <element maxOccurs="1" minOccurs="0" name="binaryData" 
             type="xsd:base64Binary"/> 
         <element maxOccurs="1" minOccurs="0" name="attachmentID" 
             type="xsd:string"/> 
         <element maxOccurs="1" minOccurs="0" name="remoteURL" 
             type="xsd:string"/> 
         <element maxOccurs="1" minOccurs="0" name="MTOM"  
             type="xsd:base64Binary" 
             xmime:expectedContentTypes="*/*" 
             xmlns:xmime="https://www.w3.org/2005/05/xmlmime"/> 
         <element maxOccurs="1" minOccurs="0" name="swaRef"  
             type="tns1:swaRef"/> 
         <element maxOccurs="1" minOccurs="0" name="attributes" 
             type="impl:MyMapOf_xsd_string_To_xsd_anyType"/> 
     </sequence> 
 </complexType>
```

Le `MTOM` et `swaRef` ne sont pris en charge que dans AEM Forms. Vous ne pouvez utiliser ces nouveaux champs que si vous spécifiez une URL qui inclut la variable `lc_version` .

**Fourniture d’objets BLOB dans des demandes de service**

Si une opération de service AEM Forms nécessite une `BLOB` Saisissez comme valeur d’entrée, créez une instance de la variable `BLOB` saisissez la logique de votre application. (La plupart des démarrages rapides de service Web se trouvent dans *Programmation avec les AEM forms* montrer comment utiliser un type de données BLOB ;)

Affectez des valeurs aux champs qui appartiennent au `BLOB` instance comme suit :

* **Base64**: Pour transmettre des données sous forme de texte codé au format Base64, définissez les données dans la variable `BLOB.binaryData` et définir le type de données au format MIME (par exemple `application/pdf`) dans la variable `BLOB.contentType` champ . (Voir [Appel d’AEM Forms à l’aide du codage Base64](#invoking-aem-forms-using-base64-encoding).)
* **MTOM**: Pour transmettre des données binaires dans une pièce jointe MTOM, définissez les données dans la variable `BLOB.MTOM` champ . Ce paramètre associe les données à la requête SOAP à l’aide de la structure Java JAX-WS ou de l’API native de la structure SOAP. (Voir [Appel d’AEM Forms à l’aide de MTOM](#invoking-aem-forms-using-mtom).)
* **SwaRef**: Pour transmettre des données binaires dans une pièce jointe WS-I SwaRef, définissez les données dans la variable `BLOB.swaRef` champ . Ce paramètre joint les données à la requête SOAP à l’aide de la structure Java JAX-WS. (Voir [Appel d’AEM Forms à l’aide de SwaRef](#invoking-aem-forms-using-swaref).)
* **pièce jointe MIME ou DIME**: Pour transmettre des données dans une pièce jointe MIME ou DIME, joignez les données à la requête SOAP à l’aide de l’API native du framework SOAP. Définissez l’identifiant de la pièce jointe dans la variable `BLOB.attachmentID` champ . (Voir [Appel d’AEM Forms à l’aide du codage Base64](#invoking-aem-forms-using-base64-encoding).)
* **URL distante**: Si les données sont hébergées sur un serveur Web et accessibles via une URL HTTP, définissez l’URL HTTP dans la variable `BLOB.remoteURL` champ . (Voir [Appel d’AEM Forms à l’aide de données BLOB sur HTTP](#invoking-aem-forms-using-blob-data-over-http).)

**Accès aux données dans les objets BLOB renvoyés par les services**

Le protocole de transmission pour la valeur renvoyée `BLOB` dépend de plusieurs facteurs, pris en compte dans l’ordre suivant, qui s’arrêtent lorsque la condition principale est remplie :

1. **L’URL cible spécifie le protocole de transmission**. Si l’URL cible spécifiée lors de l’appel SOAP contient le paramètre `blob="`*BLOB_TYPE*&quot;, puis *BLOB_TYPE* détermine le protocole de transmission. *BLOB_TYPE* est un espace réservé pour base64, dime, mime, http, mtom ou swaref.
1. **Le point d’entrée SOAP du service est Smart**. Si les conditions suivantes sont vraies, les documents de sortie sont retournés avec le même protocole de transmission que les documents d&#39;entrée :

   * Le paramètre de point d’entrée SOAP du service Default Protocol for Output Blob Objects est défini sur Smart.

      Pour chaque service avec un point d’entrée SOAP, la console d’administration vous permet de spécifier le protocole de transmission pour les objets Blob renvoyés. (Voir [Aide à l’administration](https://www.adobe.com/go/learn_aemforms_admin_63).)

   * Le service AEM Forms prend un ou plusieurs documents en entrée.

1. **Le point d’entrée SOAP du service n’est pas dynamique**. Le protocole configuré détermine le protocole de transmission du document et les données sont renvoyées dans la balise `BLOB` champ . Par exemple, si le point de terminaison SOAP est défini sur DIME, l’objet blob renvoyé se trouve dans la variable `blob.attachmentID` indépendamment du protocole de transmission d’un document d’entrée.
1. **Sinon**. Si un service ne prend pas le type de document en entrée, les documents de sortie sont renvoyés dans la variable `BLOB.remoteURL` sur le protocole HTTP.

Comme décrit dans la première condition, vous pouvez garantir le type de transmission de tout document renvoyé en étendant l’URL du point de terminaison SOAP avec un suffixe comme suit :

```as3
     https://<your_serverhost>:<your_port>/soap/services/<service 
     name>?blob=base64|dime|mime|http|mtom|swaref
```

Voici la corrélation entre les types de transmission et le champ à partir duquel vous obtenez les données :

* **Format Base64**: Définissez la variable `blob` suffixe à `base64` pour renvoyer les données dans la variable `BLOB.binaryData` champ .
* **pièce jointe MIME ou DIME**: Définissez la variable `blob` suffixe à `DIME` ou `MIME` pour renvoyer les données sous la forme d’un type de pièce jointe correspondant avec l’identifiant de pièce jointe renvoyé dans la variable `BLOB.attachmentID` champ . Utilisez l’API propriétaire du framework SOAP pour lire les données de la pièce jointe.
* **URL distante**: Définissez la variable `blob` suffixe à `http` pour conserver les données sur le serveur applicatif et renvoyer l’URL pointant vers les données de la variable `BLOB.remoteURL` champ .
* **MTOM ou SwaRef**: Définissez la variable `blob` suffixe à `mtom` ou `swaref` pour renvoyer les données sous la forme d’un type de pièce jointe correspondant avec l’identifiant de pièce jointe renvoyé dans la variable `BLOB.MTOM` ou `BLOB.swaRef` champs. Utilisez l’API native du framework SOAP pour lire les données de la pièce jointe.

>[!NOTE]
>
>Il est recommandé de ne pas dépasser 30 Mo lors de la saisie d’une `BLOB` en appelant son objet `setBinaryData` . Sinon, il est possible qu’une `OutOfMemory`* exception.*

>[!NOTE]
>
>Les applications basées sur les services JAX qui utilisent le protocole de transmission MTOM sont limitées à 25 Mo de données envoyées et reçues. Cette limitation est due à un bogue dans JAX-WS. Si la taille combinée de vos fichiers envoyés et reçus dépasse 25 Mo, utilisez le protocole de transmission SwaRef au lieu de celui MTOM. Sinon, il est possible qu’une `OutOfMemory`* exception.*

**Transmission MTOM des tableaux d’octets codés en base64**

En plus de la variable `BLOB` , le protocole MTOM prend en charge tout paramètre de tableau d’octets ou champ de tableau d’octets d’un type complexe. Cela signifie que les frameworks SOAP client prenant en charge MTOM peuvent envoyer n’importe quel `xsd:base64Binary` élément en tant que pièce jointe MTOM (au lieu d’un texte codé en base64). Les points d’entrée SOAP AEM Forms peuvent lire ce type de codage de tableau d’octets. Cependant, le service AEM Forms renvoie toujours un type de tableau d’octets sous forme de texte codé en base64. Les paramètres du tableau d’octets de sortie ne prennent pas en charge MTOM.

Les services AEM Forms qui renvoient une grande quantité de données binaires utilisent le type Document/BLOB plutôt que le type de tableau d’octets. Le type de document est beaucoup plus efficace pour transmettre de grandes quantités de données.

## Types de données des services Web {#web-service-data-types}

Le tableau suivant répertorie les types de données Java et affiche le type de données de service Web correspondant.

<table> 
 <thead> 
  <tr> 
   <th><p>Type de données Java</p></th> 
   <th><p>Type de données de service Web</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p><code>java.lang.byte[]</code></p></td> 
   <td><p><code>xsd:base64Binary</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.lang.Boolean</code></p></td> 
   <td><p><code>xsd:boolean</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.util.Date</code></p></td> 
   <td><p>Le <code>DATE</code> type, défini dans une WSDL de service comme suit :</p><p><code>&lt;complexType name="DATE"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="date" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="calendar" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Si une opération de service AEM Forms utilise une <code>java.util.Date</code> en tant qu’entrée, l’application cliente SOAP doit transmettre la date dans la variable <code>DATE.date</code> champ . La définition de la variable <code>DATE.calendar</code> dans ce cas, entraîne une exception d’exécution. Si le service renvoie une <code>java.util.Date</code>, la date est renvoyée dans la variable <code>DATE.date</code> champ .</p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.util.Calendar</code></p></td> 
   <td><p>Le <code>DATE</code> type, défini dans une WSDL de service comme suit :</p><p><code>&lt;complexType name="DATE"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="date" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="calendar" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Si une opération de service AEM Forms utilise une <code>java.util.Calendar</code> en tant qu’entrée, l’application cliente SOAP doit transmettre la date dans la variable <code>DATE.caledendar</code> champ . La définition de la variable <code>DATE.date</code> dans ce cas, entraîne une exception d’exécution. Si le service renvoie une <code>java.util.Calendar</code>, la date est renvoyée dans la variable <code>DATE.calendar</code> champ . </p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.math.BigDecimal</code></p></td> 
   <td><p><code>xsd:decimal</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>com.adobe.idp.Document</code></p></td> 
   <td><p><code>BLOB</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.lang.Double</code></p></td> 
   <td><p><code>xsd:double</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.lang.Float</code></p></td> 
   <td><p><code>xsd:float</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.lang.Integer</code></p></td> 
   <td><p><code>xsd:int</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.util.List</code></p></td> 
   <td><p><code>MyArrayOf_xsd_anyType</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.lang.Long</code></p></td> 
   <td><p><code>xsd:long</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.util.Map</code></p></td> 
   <td><p>Le <code>apachesoap:Map</code>, qui est défini dans une WSDL de service comme suit :</p><p><code>&lt;schema elementFormDefault="qualified" targetNamespace="https://xml.apache.org/xml-soap" xmlns="https://www.w3.org/2001/XMLSchema"&gt;</code></p><p><code>&lt;complexType name="mapItem"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element name="key" nillable="true" type="xsd:anyType"/&gt;</code></p><p><code>&lt;element name="value" nillable="true" type="xsd:anyType"/&gt;</code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p><code>&lt;complexType name="Map"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="unbounded" minOccurs="0" name="item" </code><code>type="apachesoap:mapItem"/&gt;</code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p><code>&lt;/schema&gt;</code></p><p>La carte est représentée sous la forme d’une séquence de paires clé/valeur.</p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.lang.Object</code></p></td> 
   <td><p><code>$1</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.lang.Short</code></p></td> 
   <td><p><code>xsd:short</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>java.lang.String</code></p></td> 
   <td><p><code>xsd:string</code></p></td> 
  </tr> 
  <tr> 
   <td><p><code>org.w3c.dom.Document</code></p></td> 
   <td><p>Le type XML, défini dans une WSDL de service, est le suivant :</p><p><code>&lt;complexType name="XML"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="document" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="element" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Si une opération de service AEM Forms accepte une <code>org.w3c.dom.Document</code> , transmettez les données XML dans la variable <code>XML.document</code> champ .</p><p>La définition de la variable <code>XML.element</code> entraîne une exception d’exécution. Si le service renvoie une <code>org.w3c.dom.Document</code>, les données XML sont alors renvoyées dans la variable <code>XML.document</code> champ .</p></td> 
  </tr> 
  <tr> 
   <td><p><code>org.w3c.dom.Element</code></p></td> 
   <td><p>Le type XML, défini dans une WSDL de service, est le suivant :</p><p><code>&lt;complexType name="XML"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="document" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="element" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Si une opération de service AEM Forms utilise une <code>org.w3c.dom.Element</code> en tant qu’entrée, transmettez les données XML dans la variable <code>XML.element</code> champ .</p><p>La définition de la variable <code>XML.document</code> entraîne une exception d’exécution. Si le service renvoie une <code>org.w3c.dom.Element</code>, les données XML sont alors renvoyées dans la variable <code>XML.element</code> champ .</p></td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>L’appel de services web à l’aide de composants personnalisés explique comment créer un composant AEM Forms qui appelle des services web tiers.

## Création de classes de proxy Java à l’aide de JAX-WS {#creating-java-proxy-classes-using-jax-ws}

Vous pouvez utiliser JAX-WS pour convertir une WSDL de service Forms en classes proxy Java. Ces classes vous permettent d’appeler des opérations de services AEM Forms. Apache Ant vous permet de créer un script de génération qui génère des classes proxy Java en référençant un WSDL de service AEM Forms. Vous pouvez générer des fichiers proxy JAX-WS en procédant comme suit :

1. Installez Apache Ant sur l’ordinateur client. (Voir [https://ant.apache.org/bindownload.cgi](https://ant.apache.org/bindownload.cgi).)

   * Ajoutez le répertoire bin à votre chemin de classe.
   * Définissez la variable `ANT_HOME` dans le répertoire où vous avez installé Ant.

1. Installez JDK 1.6 ou version ultérieure.

   * Ajoutez le répertoire bin JDK à votre chemin de classe.
   * Ajoutez le répertoire bin JRE à votre chemin de classe. Cette corbeille se trouve dans la variable [*JDK_INSTALL_LOCATION*] répertoire /jre.
   * Définissez la variable `JAVA_HOME` dans le répertoire dans lequel vous avez installé le JDK.

   Le JDK 1.6 comprend le programme d’installation utilisé dans le fichier build.xml. Le JDK 1.5 n’inclut pas ce programme.

1. Installez JAX-WS sur l’ordinateur client. (Voir [API Java pour les services Web XML](https://jax-ws.dev.java.net/jax-ws-ea3/docs/mtom-swaref.html).)
1. Utilisez JAX-WS et Apache Ant pour générer des classes proxy Java. Créez un script de génération Ant pour accomplir cette tâche. Le script suivant est un exemple de script de build Ant nommé build.xml :

   ```as3
    <?xml version="1.0" encoding="UTF-8"?> 
     
    <project basedir="." default="compile"> 
     
    <property name="port" value="8080" /> 
    <property name="host" value="localhost" /> 
    <property name="username" value="administrator" /> 
    <property name="password" value="password" /> 
    <property name="tests" value="all" /> 
     
    <target name="clean" > 
           <delete dir="classes" /> 
    </target> 
     
    <target name="wsdl" depends="clean"> 
           <mkdir dir="classes"/> 
           <exec executable="wsimport" failifexecutionfails="false" failonerror="true" resultproperty="foundWSIMPORT"> 
               <arg line="-keep -d classes https://${host}:${port}/soap/services/EncryptionService?wsdl&lc_version=9.0.1"/> 
           </exec> 
           <fail unless="foundWSIMPORT"> 
              !!! Failed to execute JDK's wsimport tool. Make sure that JDK 1.6 (or later) is on your PATH !!! 
           </fail> 
    </target> 
     
    <target name="compile" depends="clean, wsdl" > 
         <javac destdir="./classes" fork="true" debug="true"> 
            <src path="./src"/> 
         </javac> 
    </target> 
     
    <target name="run"> 
         <java classname="Client" fork="yes" failonerror="true" maxmemory="200M"> 
            <classpath> 
              <pathelement location="./classes"/> 
            </classpath> 
            <arg value="${port}"/> 
            <arg value="${host}"/> 
            <arg value="${username}"/> 
            <arg value="${password}"/> 
            <arg value="${tests}"/> 
         </java> 
    </target> 
    </project>
   ```

   Dans ce script de génération Ant, notez que la variable `url` est définie pour référencer le fichier WSDL du service Encryption s’exécutant sur localhost. Le `username` et `password` Les propriétés doivent être définies sur un nom d’utilisateur et un mot de passe AEM forms valides. Notez que l’URL contient la variable `lc_version` attribut. Sans spécifier la variable `lc_version` , vous ne pouvez pas appeler de nouvelles opérations de service AEM Forms.

   >[!NOTE]
   >
   >Remplacer `EncryptionService`* avec le nom du service AEM Forms que vous souhaitez appeler à l’aide des classes proxy Java. Par exemple, pour créer des classes proxy Java pour le service de Rights Management, spécifiez :*

   ```as3
    http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1
   ```

1. Créez un fichier BAT pour exécuter le script de génération Ant. La commande suivante peut se trouver dans un fichier BAT responsable de l’exécution du script de génération Ant :

   ```as3
    ant -buildfile "build.xml" wsdl
   ```

   Placez le script de génération ANT dans le dossier C:\Program Files\Java\jaxws-ri\bin directory. Le script écrit les fichiers JAVA dans le .dossier /classes . Le script génère des fichiers JAVA pouvant appeler le service.

1. Regroupez les fichiers JAVA dans un fichier JAR. Si vous travaillez sur Eclipse, procédez comme suit :

   * Créez un projet Java utilisé pour compresser les fichiers JAVA du proxy dans un fichier JAR.
   * Créez un dossier source dans le projet.
   * Créez un `com.adobe.idp.services` dans le dossier Source.
   * Sélectionnez la `com.adobe.idp.services` puis importez les fichiers JAVA du dossier adobe/idp/services dans le package.
   * Si nécessaire, créez une `org/apache/xml/xmlsoap` dans le dossier Source.
   * Sélectionnez le dossier source, puis importez les fichiers JAVA à partir du dossier org/apache/xml/xmlsoap .
   * Définissez le niveau de conformité du compilateur Java sur 5.0 ou version ultérieure.
   * Créez le projet.
   * Exportez le projet sous la forme d’un fichier JAR.
   * Importez ce fichier JAR dans le chemin de classe d’un projet client. En outre, importez tous les fichiers JAR situés dans &lt;install directory=&quot;&quot;>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty.

   >[!NOTE]
   >
   >Tous les démarrages rapides des services Web Java (à l’exception du service Forms) situés dans Programmation avec AEM forms créent des fichiers proxy Java à l’aide de JAX-WS. En outre, tous les démarrages rapides de service Web Java, utilisez SwaRef. (Voir [Appel d’AEM Forms à l’aide de SwaRef](#invoking-aem-forms-using-swaref).)

**Voir également**

[Création de classes proxy Java à l’aide de l’axe Apache](#creating-java-proxy-classes-using-apache-axis)

[Appel d’AEM Forms à l’aide du codage Base64](#invoking-aem-forms-using-base64-encoding)

[Appel d’AEM Forms à l’aide de données BLOB sur HTTP](#invoking-aem-forms-using-blob-data-over-http)

[Appel d’AEM Forms à l’aide de SwaRef](#invoking-aem-forms-using-swaref)

## Création de classes proxy Java à l’aide de l’axe Apache {#creating-java-proxy-classes-using-apache-axis}

Vous pouvez utiliser l’outil Apache Axis WSDL2Java pour convertir un service Forms en classes proxy Java. Ces classes vous permettent d’appeler des opérations de service Forms. Avec Apache Ant, vous pouvez générer des fichiers de bibliothèque Axis à partir d’un WSDL de service. Vous pouvez télécharger l’axe Apache à l’adresse URL [https://ws.apache.org/axis/](https://ws.apache.org/axis/).

>[!NOTE]
>
>Les démarrages rapides des services Web associés au service Forms utilisent des classes proxy Java créées à l’aide de l’axe Apache. Les démarrages rapides du service Web Forms utilisent également Base64 comme type de codage. (Voir [Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts).)

Vous pouvez générer des fichiers de bibliothèque Java Axis en procédant comme suit :

1. Installez Apache Ant sur l’ordinateur client. Elle est disponible à l’adresse [https://ant.apache.org/bindownload.cgi](https://ant.apache.org/bindownload.cgi).

   * Ajoutez le répertoire bin à votre chemin de classe.
   * Définissez la variable `ANT_HOME` dans le répertoire où vous avez installé Ant.

1. Installez Apache Axis 1.4 sur l’ordinateur client. Elle est disponible à l’adresse [https://ws.apache.org/axis/](https://ws.apache.org/axis/).
1. Configurez le chemin de classe pour utiliser les fichiers JAR Axis dans votre client de service Web, comme décrit dans les instructions d’installation d’Axis à l’adresse [https://ws.apache.org/axis/java/install.html](https://ws.apache.org/axis/java/install.html).
1. Utilisez l’outil Apache WSDL2Java dans Axis pour générer des classes de proxy Java. Créez un script de génération Ant pour accomplir cette tâche. Le script suivant est un exemple de script de build Ant nommé build.xml :

   ```as3
    <?xml version="1.0"?> 
    <project name="axis-wsdl2java"> 
     
    <path id="axis.classpath"> 
    <fileset dir="C:\axis-1_4\lib" > 
        <include name="**/*.jar" /> 
    </fileset> 
    </path> 
     
    <taskdef resource="axis-tasks.properties" classpathref="axis.classpath" /> 
     
    <target name="encryption-wsdl2java-client" description="task"> 
    <axis-wsdl2java 
        output="C:\JavaFiles" 
        testcase="false" 
        serverside="false" 
        verbose="true" 
        username="administrator" 
        password="password" 
        url="http://localhost:8080/soap/services/EncryptionService?wsdl&lc_version=9.0.1" > 
    </axis-wsdl2java> 
    </target> 
     
    </project>
   ```

   Dans ce script de génération Ant, notez que la variable `url` est définie pour référencer le fichier WSDL du service Encryption s’exécutant sur localhost. Le `username` et `password` Les propriétés doivent être définies sur un nom d’utilisateur et un mot de passe AEM forms valides.

1. Créez un fichier BAT pour exécuter le script de génération Ant. La commande suivante peut se trouver dans un fichier BAT responsable de l’exécution du script de génération Ant :

   ```as3
    ant -buildfile "build.xml" encryption-wsdl2java-client
   ```

   Les fichiers JAVA sont écrits dans le dossier C:\JavaFiles folder as specified by the `output` . Pour appeler correctement le service Forms, importez ces fichiers JAVA dans le chemin de classe.

   Par défaut, ces fichiers appartiennent à un package Java nommé `com.adobe.idp.services`. Il est recommandé de placer ces fichiers JAVA dans un fichier JAR. Importez ensuite le fichier JAR dans le chemin de classe de votre application cliente.

   >[!NOTE]
   >
   >Il existe différentes manières de placer des fichiers .JAVA dans un fichier JAR. Une méthode consiste à utiliser un IDE Java comme Eclipse. Créez un projet Java et créez un `com.adobe.idp.services`* package (tous les fichiers .JAVA appartiennent à ce package). Importez ensuite tous les fichiers .JAVA dans le package. Enfin, exportez le projet sous la forme d’un fichier JAR.*

1. Modifiez l’URL dans le `EncryptionServiceLocator` pour spécifier le type d’encodage. Par exemple, pour utiliser base64, spécifiez `?blob=base64` pour vous assurer que la variable `BLOB` renvoie des données binaires. C’est-à-dire que dans la variable `EncryptionServiceLocator` recherchez la ligne de code suivante :

   ```as3
    http://localhost:8080/soap/services/EncryptionService;
   ```

   Localisez la chaîne et attribuez-lui la valeur:

   ```as3
    http://localhost:8080/soap/services/EncryptionService?blob=base64;
   ```

1. Ajoutez les fichiers JAR Axis suivants au chemin de classe de votre projet Java :

   * activation.jar
   * axis.jar
   * commons-codec-1.3.jar
   * commons-collections-3.1.jar
   * commons-discovery.jar
   * commons-logging.jar
   * dom3-xml-apis-2.5.0.jar
   * jai_imageio.jar
   * jaxen-1.1-beta-9.jar
   * jaxrpc.jar
   * log4j.jar
   * mail.jar
   * saaj.jar
   * wsdl4j.jar
   * xalan.jar
   * xbean.jar
   * xercesImpl.jar

   Ces fichiers JAR se trouvent dans la variable *[répertoire d’installation]*/Adobe/Adobe Experience Manager Forms/sdk/lib/thirdparty directory.

**Voir également**

[Création de classes de proxy Java à l’aide de JAX-WS](#creating-java-proxy-classes-using-jax-ws)

[Appel d’AEM Forms à l’aide du codage Base64](#invoking-aem-forms-using-base64-encoding)

[Appel d’AEM Forms à l’aide de données BLOB sur HTTP](#invoking-aem-forms-using-blob-data-over-http)

## Appel d’AEM Forms à l’aide du codage Base64 {#invoking-aem-forms-using-base64-encoding}

Vous pouvez appeler un service AEM Forms à l’aide de l’encodage Base64. Le codage Base64 code les pièces jointes envoyées avec une demande d’appel de service Web. C&#39;est-à-dire : `BLOB` Les données sont codées en Base64, pas l’intégralité du message SOAP.

&quot;Appel d’AEM Forms à l’aide de l’encodage Base64&quot; traite de l’appel du processus de courte durée AEM Forms suivant nommé `MyApplication/EncryptDocument` en utilisant le codage Base64.

>[!NOTE]
>
>Ce processus n’est pas basé sur un processus AEM Forms existant. Pour suivre l’exemple de code, créez un processus désigné par `MyApplication/EncryptDocument` à l’aide de Workbench. (Voir [Utilisation de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Lorsque ce processus est appelé, il effectue les actions suivantes :

1. Obtention du document PDF non sécurisé transmis au processus. Cette action est basée sur l’opération `SetValue`. Le paramètre d’entrée pour ce processus est une variable de processus `document` désignée par `inDoc`.
1. Chiffrement du document PDF avec un mot de passe. Cette action est basée sur l’opération `PasswordEncryptPDF`. Le document PDF chiffré avec un mot de passe est retourné dans une variable de processus nommée `outDoc`.

### Création d’un assemblage client .NET utilisant le codage Base64 {#creating-a-net-client-assembly-that-uses-base64-encoding}

Vous pouvez créer un assemblage client .NET pour appeler un service Forms à partir d’un projet Microsoft Visual Studio .NET. Pour créer un assemblage client .NET qui utilise le codage base64, procédez comme suit :

1. Créez une classe proxy basée sur une URL d’appel AEM Forms.
1. Créez un projet Microsoft Visual Studio .NET qui produit l’assemblage client .NET.

**Création d’une classe proxy**

Vous pouvez créer une classe proxy utilisée pour créer l’assemblage client .NET à l’aide d’un outil qui accompagne Microsoft Visual Studio. Le nom de l’outil est wsdl.exe et se trouve dans le dossier d’installation de Microsoft Visual Studio. Pour créer une classe proxy, ouvrez l’invite de commande et accédez au dossier contenant le fichier wsdl.exe . Pour plus d’informations sur l’outil wsdl.exe, voir *Aide de MSDN*.

Saisissez la commande suivante à l’invite de commande :

```as3
 wsdl https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
```

Par défaut, cet outil crée un fichier CSS dans le même dossier basé sur le nom du fichier WSDL. Dans ce cas, il crée un fichier CSS nommé *EncryptDocumentService.cs*. Utilisez ce fichier CS pour créer un objet proxy qui vous permet d’appeler le service spécifié dans l’URL d’appel.

Modifiez l’URL dans la classe proxy pour inclure `?blob=base64` pour vous assurer que la variable `BLOB` renvoie des données binaires. Dans la classe proxy, recherchez la ligne de code suivante :

```as3
 "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument";
```

Localisez la chaîne et attribuez-lui la valeur:

```as3
 "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64";
```

Le *Appel d’AEM Forms à l’aide du codage Base64* utilise la section `MyApplication/EncryptDocument` par exemple. Si vous créez un assemblage client .NET pour un autre service Forms, assurez-vous de remplacer `MyApplication/EncryptDocument` par le nom du service.

**Développement de l’assemblage client .NET**

Créez un projet de bibliothèque de classes Visual Studio qui crée un assemblage client .NET. Le fichier CS que vous avez créé à l’aide de wsdl.exe peut être importé dans ce projet. Ce projet produit un fichier DLL (l’assemblage client .NET) que vous pouvez utiliser dans d’autres projets Visual Studio .NET pour appeler un service.

1. Démarrez Microsoft Visual Studio .NET.
1. Créez un projet Bibliothèque de classes et nommez-le DocumentService.
1. Importez le fichier CS que vous avez créé à l’aide de wsdl.exe.
1. Dans le **Projet** menu, sélectionnez **Ajouter une référence**.
1. Dans la boîte de dialogue Ajouter une référence, sélectionnez **System.Web.Services.dll**.
1. Cliquez sur **Sélectionner** puis cliquez sur **OK**.
1. Compilez et créez le projet.

>[!NOTE]
>
>Cette procédure crée un assemblage client .NET appelé DocumentService.dll que vous pouvez utiliser pour envoyer des requêtes SOAP à `MyApplication/EncryptDocument` service.

>[!NOTE]
>
>Assurez-vous que vous avez ajouté `?blob=base64` à l’URL dans la classe proxy utilisée pour créer l’assemblage client .NET. Sinon, vous ne pourrez pas récupérer les données binaires de la variable `BLOB` .

**Référencer l’assemblage client .NET**

Placez l’assemblage client .NET que vous venez de créer sur l’ordinateur sur lequel vous développez votre application cliente. Après avoir placé l’assemblage client .NET dans un répertoire, vous pouvez le référencer à partir d’un projet. Voir également la section `System.Web.Services` de votre projet. Si vous ne référencez pas cette bibliothèque, vous ne pouvez pas utiliser l’assemblage client .NET pour appeler un service.

1. Dans le **Projet** menu, sélectionnez **Ajouter une référence**.
1. Cliquez sur le bouton **.NET** .
1. Cliquez sur **Parcourir** et recherchez le fichier DocumentService.dll .
1. Cliquez sur **Sélectionner** puis cliquez sur **OK**.

**Appel d’un service à l’aide d’un assemblage client .NET qui utilise le codage Base64**

Vous pouvez appeler le `MyApplication/EncryptDocument` service (qui a été créé dans Workbench) à l’aide d’un assemblage client .NET qui utilise l’encodage Base64. Pour appeler la fonction `MyApplication/EncryptDocument` effectuez les étapes suivantes :

1. Création d’un assemblage client Microsoft .NET qui consomme la variable `MyApplication/EncryptDocument` service WSDL.
1. Créez un projet Microsoft .NET client. Référencez l’assemblage client Microsoft .NET dans le projet client. Référence également `System.Web.Services`.
1. À l’aide de l’assemblage client .NET Microsoft, créez une `MyApplication_EncryptDocumentService` en appelant son constructeur par défaut.
1. Définissez la variable `MyApplication_EncryptDocumentService` de `Credentials` avec une propriété `System.Net.NetworkCredential` . Dans le `System.Net.NetworkCredential` constructeur, indiquez un nom d’utilisateur AEM forms et le mot de passe correspondant. Définissez des valeurs d’authentification pour permettre à votre application cliente .NET d’échanger des messages SOAP avec AEM Forms.
1. Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document PDF transmis à la variable `MyApplication/EncryptDocument` processus.
1. Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
1. Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
1. Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
1. Renseignez la variable `BLOB` en attribuant ses `binaryData` avec le contenu du tableau d’octets.
1. Appeler la variable `MyApplication/EncryptDocument` en appelant le `MyApplication_EncryptDocumentService` de `invoke` et transmission de la méthode `BLOB` contenant le document du PDF. Ce processus renvoie un document de PDF chiffré dans un `BLOB` .
1. Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document chiffré par mot de passe.
1. Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` renvoyé par l’objet `MyApplicationEncryptDocumentService` de `invoke` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `binaryData` membre de données.
1. Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
1. Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

### Appel d’un service à l’aide des classes proxy Java et du codage Base64 {#invoking-a-service-using-java-proxy-classes-and-base64-encoding}

Vous pouvez appeler un service AEM Forms à l’aide des classes proxy Java et de Base64. Pour appeler la fonction `MyApplication/EncryptDocument` à l’aide des classes proxy Java, procédez comme suit :

1. Créez des classes proxy Java à l’aide de JAX-WS qui utilise la variable `MyApplication/EncryptDocument` service WSDL. Utilisez le point d’entrée WSDL suivant :

   `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1`

   >[!NOTE]
   >
   >Remplacer `hiro-xp`* avec l’adresse IP du serveur d’applications J2EE hébergeant AEM Forms. *

1. Regroupez les classes proxy Java créées à l’aide de JAX-WS dans un fichier JAR.
1. Incluez le fichier JAR du proxy Java et les fichiers JAR situés dans le chemin d’accès suivant :

   &lt;install directory=&quot;&quot;>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   dans le chemin de classe de votre projet client Java.

1. Créez un objet `MyApplicationEncryptDocumentService` en utilisant son constructeur.
1. Créez un `MyApplicationEncryptDocument` en appelant le `MyApplicationEncryptDocumentService` de `getEncryptDocument` .
1. Définissez les valeurs de connexion requises pour appeler AEM Forms en affectant des valeurs aux membres de données suivants :

   * Affectez le point d’entrée WSDL et le type de codage au `javax.xml.ws.BindingProvider` de `ENDPOINT_ADDRESS_PROPERTY` champ . Pour appeler la fonction `MyApplication/EncryptDocument` à l’aide de l’encodage Base64, spécifiez la valeur d’URL suivante :

      `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64`

   * Affectez l’utilisateur d’AEM forms à la variable `javax.xml.ws.BindingProvider` de `USERNAME_PROPERTY` champ .
   * Attribuez la valeur de mot de passe correspondante à la variable `javax.xml.ws.BindingProvider` de `PASSWORD_PROPERTY` champ .

   L’exemple de code suivant illustre cette logique d’application :

   ```as3
    //Set connection values required to invoke AEM Forms 
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64"; 
    String username = "administrator"; 
    String password = "password"; 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url); 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username); 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Récupérer le document du PDF à envoyer à la fonction `MyApplication/EncryptDocument` en créant un `java.io.FileInputStream` en utilisant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du document du PDF.
1. Créez un tableau d’octets et renseignez-le avec le contenu de la variable `java.io.FileInputStream` .
1. Créez un objet `BLOB` en utilisant son constructeur.
1. Renseignez la variable `BLOB` en appelant son objet `setBinaryData` et transmission du tableau d’octets. Le `BLOB` de `setBinaryData` est la méthode à appeler lors de l’utilisation de l’encodage Base64. Voir Fournir des objets BLOB dans les demandes de service.
1. Appeler la variable `MyApplication/EncryptDocument` en appelant le `MyApplicationEncryptDocument` de `invoke` . Transmettez la variable `BLOB` contenant le document du PDF. La méthode invoke renvoie une `BLOB` contenant le document de PDF chiffré.
1. Créez un tableau d’octets contenant le document de PDF chiffré en appelant la méthode `BLOB` de `getBinaryData` .
1. Enregistrez le document de PDF chiffré en tant que fichier de PDF. Ecrivez le tableau d’octets dans un fichier .

**Voir également**

[Démarrage rapide : Appel d’un service à l’aide de fichiers proxy Java et du codage Base64](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-java-proxy-files-and-base64-encoding)

[Création d’un assemblage client .NET utilisant le codage Base64](#creating-a-net-client-assembly-that-uses-base64-encoding)

## Appel d’AEM Forms à l’aide de MTOM {#invoking-aem-forms-using-mtom}

Vous pouvez appeler les services AEM Forms à l’aide du MTOM standard du service Web. Cette norme définit la manière dont les données binaires, telles qu’un document de PDF, sont transmises sur Internet ou sur un intranet. Une fonctionnalité de MTOM est l’utilisation de la fonction `XOP:Include` élément . Cet élément est défini dans la spécification XOP (XML Binary Optimized Packaging) afin de référencer les pièces jointes binaires d’un message SOAP.

La discussion ici porte sur l’utilisation de MTOM pour appeler le processus de courte durée AEM Forms suivant nommé `MyApplication/EncryptDocument`.

>[!NOTE]
>
>Ce processus n’est pas basé sur un processus AEM Forms existant. Pour suivre l’exemple de code, créez un processus désigné par `MyApplication/EncryptDocument` à l’aide de Workbench. (Voir [Utilisation de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Lorsque ce processus est appelé, il effectue les actions suivantes :

1. Obtention du document PDF non sécurisé transmis au processus. Cette action est basée sur l’opération `SetValue`. Le paramètre d’entrée pour ce processus est une variable de processus `document` désignée par `inDoc`.
1. Chiffrement du document PDF avec un mot de passe. Cette action est basée sur l’opération `PasswordEncryptPDF`. Le document PDF chiffré avec un mot de passe est retourné dans une variable de processus nommée `outDoc`.

>[!NOTE]
>
>La prise en charge MTOM a été ajoutée dans AEM Forms, version 9.

>[!NOTE]
>
>Les applications basées sur les services JAX qui utilisent le protocole de transmission MTOM sont limitées à 25 Mo de données envoyées et reçues. Cette limitation est due à un bogue dans JAX-WS. Si la taille combinée de vos fichiers envoyés et reçus dépasse 25 Mo, utilisez le protocole de transmission SwaRef au lieu de celui MTOM. Sinon, il est possible qu’une `OutOfMemory`* exception.*


La discussion ici porte sur l’utilisation de MTOM dans un projet Microsoft .NET pour appeler les services AEM Forms. La structure .NET utilisée est la version 3.5 et l’environnement de développement est Visual Studio 2008. Si des améliorations de service Web (WSE) sont installées sur votre ordinateur de développement, supprimez-les. La structure .NET 3.5 prend en charge une structure SOAP nommée Windows Communication Foundation (WCF). Lors de l’appel d’AEM Forms à l’aide de MTOM, seul WCF (et non WSE) est pris en charge.

### Création d’un projet .NET qui appelle un service à l’aide de MTOM {#creating-a-net-project-that-invokes-a-service-using-mtom}

Vous pouvez créer un projet Microsoft .NET qui peut appeler un service AEM Forms à l’aide de services Web. Créez tout d’abord un projet Microsoft .NET à l’aide de Visual Studio 2008. Pour appeler un service AEM Forms, créez une référence de service vers le service AEM Forms que vous souhaitez appeler dans votre projet. Lorsque vous créez une référence de service, spécifiez une URL vers le service AEM Forms :

```as3
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
```

Remplacer `localhost` avec l’adresse IP du serveur d’applications J2EE hébergeant AEM Forms. Remplacer `MyApplication/EncryptDocument` par le nom du service AEM Forms à appeler. Par exemple, pour appeler une opération de Rights Management, spécifiez :

`http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`

Le `lc_version` permet de s’assurer que la fonctionnalité AEM Forms, telle que MTOM, est disponible. Sans spécifier la variable `lc_version` , vous ne pouvez pas appeler AEM Forms à l’aide de MTOM.

Après avoir créé une référence de service, les types de données associés au service AEM Forms peuvent être utilisés dans votre projet .NET. Pour créer un projet .NET qui appelle un service AEM Forms, procédez comme suit :

1. Créez un projet .NET à l’aide de Microsoft Visual Studio 2008.
1. Dans le **Projet** menu, sélectionnez **Ajouter une référence de service**.
1. Dans le **Adresse** , spécifiez le fichier WSDL du service AEM Forms. Par exemple,

   ```as3
    http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

1. Cliquez sur **Aller** puis cliquez sur **OK**.

### Appel d’un service à l’aide de MTOM dans un projet .NET {#invoking-a-service-using-mtom-in-a-net-project}

Considérez la variable `MyApplication/EncryptDocument` processus qui accepte un document de PDF non sécurisé et renvoie un document de PDF chiffré par mot de passe. Pour appeler la fonction `MyApplication/EncryptDocument` processus (qui a été créé dans Workbench) à l’aide de MTOM, procédez comme suit :

1. Créez un projet Microsoft .NET.
1. Créez un `MyApplication_EncryptDocumentClient` en utilisant son constructeur par défaut.
1. Créez un `MyApplication_EncryptDocumentClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms et le type de codage :

   ```as3
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=mtom
   ```

   Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service. Veillez toutefois à indiquer `?blob=mtom`.

   >[!NOTE]
   >
   >Remplacer `hiro-xp`* avec l’adresse IP du serveur d’applications J2EE hébergeant AEM Forms. *

1. Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `EncryptDocumentClient.Endpoint.Binding` membre de données. Convertissez la valeur de retour en `BasicHttpBinding`.
1. Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` membre de données à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
1. Activez l’authentification HTTP de base en effectuant les tâches suivantes :

   * Attribuer le nom d’utilisateur AEM forms au membre de données `MyApplication_EncryptDocumentClient.ClientCredentials.UserName.UserName`.
   * Attribuer la valeur de mot de passe correspondante au membre de données `MyApplication_EncryptDocumentClient.ClientCredentials.UserName.Password`.
   * Attribuer la valeur constante `HttpClientCredentialType.Basic` au membre de données `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au membre de données `BasicHttpBindingSecurity.Security.Mode`.

   L’exemple de code suivant illustre ces tâches.

   ```as3
    //Enable BASIC HTTP authentication 
    encryptProcess.ClientCredentials.UserName.UserName = "administrator"; 
    encryptProcess.ClientCredentials.UserName.Password = "password"; 
    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
    b.MaxReceivedMessageSize = 4000000; 
    b.MaxBufferSize = 4000000; 
    b.ReaderQuotas.MaxArrayLength = 4000000;
   ```

1. Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document de PDF à transmettre à la variable `MyApplication/EncryptDocument` processus.
1. Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
1. Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
1. Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
1. Renseignez la variable `BLOB` en attribuant ses `MTOM` membre de données avec le contenu du tableau d’octets.
1. Appeler la variable `MyApplication/EncryptDocument` en appelant le `MyApplication_EncryptDocumentClient` de `invoke` . Transmettez la variable `BLOB` contenant le document du PDF. Ce processus renvoie un document de PDF chiffré dans un `BLOB` .
1. Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF sécurisé.
1. Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `invoke` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
1. Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
1. Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

>[!NOTE]
>
>La plupart des opérations de service AEM Forms ont un démarrage rapide MTOM. Vous pouvez afficher ces démarrages rapides dans la section de démarrage rapide correspondante d’un service. Par exemple, pour consulter la section Démarrage rapide de la sortie, voir [Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap).

**Voir également**

[Démarrage rapide : Appel d’un service à l’aide de MTOM dans un projet .NET](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-mtom-in-a-net-project)

[Accès à plusieurs services à l’aide de services Web](#accessing-multiple-services-using-web-services)

[Création d’une application web ASP.NET qui appelle un processus de longue durée pour des intervenants humains](/help/forms/developing/invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

## Appel d’AEM Forms à l’aide de SwaRef {#invoking-aem-forms-using-swaref}

Vous pouvez appeler les services AEM Forms à l’aide de SwaRef. Le contenu de la variable `wsi:swaRef` L’élément XML est envoyé en tant que pièce jointe dans un corps SOAP qui stocke la référence à la pièce jointe. Lors de l’appel d’un service Forms à l’aide de SwaRef, créez des classes proxy Java à l’aide de l’API Java pour les services Web XML (JAX-WS). (Voir [API Java pour les services Web XML](https://jax-ws.dev.java.net/jax-ws-ea3/docs/mtom-swaref.html).)

La discussion ici porte sur l’appel du processus de courte durée Forms suivant nommé `MyApplication/EncryptDocument` en utilisant SwaRef.

>[!NOTE]
>
>Ce processus n’est pas basé sur un processus AEM Forms existant. Pour suivre l’exemple de code, créez un processus désigné par `MyApplication/EncryptDocument` à l’aide de Workbench. (Voir [Utilisation de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Lorsque ce processus est appelé, il effectue les actions suivantes :

1. Obtention du document PDF non sécurisé transmis au processus. Cette action est basée sur l’opération `SetValue`. Le paramètre d’entrée pour ce processus est une variable de processus `document` désignée par `inDoc`.
1. Chiffrement du document PDF avec un mot de passe. Cette action est basée sur l’opération `PasswordEncryptPDF`. Le document PDF chiffré avec un mot de passe est retourné dans une variable de processus nommée `outDoc`.

>[!NOTE]
>
>Ajout de la prise en charge de SwaRef dans AEM Forms

La discussion ci-dessous porte sur l’appel des services Forms à l’aide de SwaRef dans une application cliente Java. L’application Java utilise des classes proxy créées à l’aide de JAX-WS.

### Appeler un service à l’aide de fichiers de bibliothèque JAX-WS qui utilisent SwaRef {#invoke-a-service-using-jax-ws-library-files-that-use-swaref}

Pour appeler la fonction `MyApplication/EncryptDocument` Procédez comme suit en utilisant des fichiers proxy Java créés à l’aide de JAX-WS et SwaRef :

1. Créez des classes proxy Java à l’aide de JAX-WS qui utilise la variable `MyApplication/EncryptDocument` service WSDL. Utilisez le point d’entrée WSDL suivant :

   ```as3
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

   Pour plus d’informations, voir [Création de classes de proxy Java à l’aide de JAX-WS](#creating-java-proxy-classes-using-jax-ws).

   >[!NOTE]
   >
   >Remplacer `hiro-xp`* avec l’adresse IP du serveur d’applications J2EE hébergeant AEM Forms. *

1. Regroupez les classes proxy Java créées à l’aide de JAX-WS dans un fichier JAR.
1. Incluez le fichier JAR du proxy Java et les fichiers JAR situés dans le chemin d’accès suivant :

   &lt;install directory=&quot;&quot;>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   dans le chemin de classe de votre projet client Java.

1. Créez un objet `MyApplicationEncryptDocumentService` en utilisant son constructeur.
1. Créez un `MyApplicationEncryptDocument` en appelant le `MyApplicationEncryptDocumentService` de `getEncryptDocument` .
1. Définissez les valeurs de connexion requises pour appeler AEM Forms en affectant des valeurs aux membres de données suivants :

   * Affectez le point d’entrée WSDL et le type de codage au `javax.xml.ws.BindingProvider` de `ENDPOINT_ADDRESS_PROPERTY` champ . Pour appeler la fonction `MyApplication/EncryptDocument` à l’aide du codage SwaRef, spécifiez la valeur d’URL suivante :

      ` https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=swaref`

   * Affectez l’utilisateur d’AEM forms à la variable `javax.xml.ws.BindingProvider` de `USERNAME_PROPERTY` champ .
   * Attribuez la valeur de mot de passe correspondante à la variable `javax.xml.ws.BindingProvider` de `PASSWORD_PROPERTY` champ .

   L’exemple de code suivant illustre cette logique d’application :

   ```as3
    //Set connection values required to invoke AEM Forms 
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=swaref"; 
    String username = "administrator"; 
    String password = "password"; 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url); 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username); 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Récupérer le document du PDF à envoyer à la fonction `MyApplication/EncryptDocument` en créant un `java.io.File` en utilisant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du document du PDF.
1. Créez un `javax.activation.DataSource` en utilisant l’objet `FileDataSource` constructeur. Transmettez la variable `java.io.File` .
1. Créez un objet `javax.activation.DataHandler` en utilisant son constructeur et en transmettant l’objet `javax.activation.DataSource`. 
1. Créez un objet `BLOB` en utilisant son constructeur.
1. Renseignez la variable `BLOB` en appelant son objet `setSwaRef` et transmission de la méthode `javax.activation.DataHandler` .
1. Appeler la variable `MyApplication/EncryptDocument` en appelant le `MyApplicationEncryptDocument` de `invoke` et transmission de la méthode `BLOB` contenant le document du PDF. La méthode invoke renvoie une `BLOB` contenant un document de PDF chiffré.
1. Renseignez un `javax.activation.DataHandler` en appelant le `BLOB` de `getSwaRef` .
1. Convertir la variable `javax.activation.DataHandler` vers un objet `java.io.InputSteam` en appelant la méthode `javax.activation.DataHandler` de `getInputStream` .
1. Écrivez le `java.io.InputSteam` à un fichier de PDF qui représente le document de PDF chiffré.

>[!NOTE]
>
>La plupart des opérations de service AEM Forms ont un démarrage rapide de SwaRef. Vous pouvez afficher ces démarrages rapides dans la section de démarrage rapide correspondante d’un service. Par exemple, pour consulter la section Démarrage rapide de la sortie, voir [Démarrages rapides de l’API Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap).

**Voir également**

[Démarrage rapide : Appel d’un service à l’aide de SwaRef dans un projet Java](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-swaref-in-a-java-project)

## Appel d’AEM Forms à l’aide de données BLOB sur HTTP {#invoking-aem-forms-using-blob-data-over-http}

Vous pouvez appeler les services AEM Forms à l’aide de services web et transmettre des données BLOB sur HTTP. La transmission de données BLOB via HTTP est une autre technique que l’utilisation de l’encodage base64, DIME ou MIME. Par exemple, vous pouvez transmettre des données via HTTP dans un projet Microsoft .NET qui utilise l’amélioration des services web 3.0, qui ne prend pas en charge DIME ou MIME. Lors de l’utilisation de données BLOB sur HTTP, les données d’entrée sont chargées avant l’appel du service AEM Forms.

&quot;Appel d’AEM Forms à l’aide de données BLOB sur HTTP&quot; traite de l’appel du processus de courte durée AEM Forms suivant nommé `MyApplication/EncryptDocument` en transmettant les données BLOB sur HTTP.

>[!NOTE]
>
>Ce processus n’est pas basé sur un processus AEM Forms existant. Pour suivre l’exemple de code, créez un processus désigné par `MyApplication/EncryptDocument` à l’aide de Workbench. (Voir [Utilisation de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Lorsque ce processus est appelé, il effectue les actions suivantes :

1. Obtention du document PDF non sécurisé transmis au processus. Cette action est basée sur l’opération `SetValue`. Le paramètre d’entrée pour ce processus est une variable de processus `document` désignée par `inDoc`.
1. Chiffrement du document PDF avec un mot de passe. Cette action est basée sur l’opération `PasswordEncryptPDF`. Le document PDF chiffré avec un mot de passe est retourné dans une variable de processus nommée `outDoc`.

>[!NOTE]
>
>Il est recommandé de vous familiariser avec l’appel d’AEM Forms à l’aide de SOAP. (Voir [Appel d’AEM Forms à l’aide de services web](#invoking-aem-forms-using-web-services).)

### Création d’un assemblage client .NET utilisant des données sur HTTP {#creating-a-net-client-assembly-that-uses-data-over-http}

Pour créer un assemblage client qui utilise des données via HTTP, suivez le processus spécifié dans [Appel d’AEM Forms à l’aide du codage Base64](#invoking-aem-forms-using-base64-encoding). Toutefois, modifiez l’URL dans la classe proxy pour inclure `?blob=http` au lieu de `?blob=base64`. Cette action garantit que les données sont transmises via HTTP. Dans la classe proxy, recherchez la ligne de code suivante :

```as3
 "http://localhost:8080/soap/services/MyApplication/EncryptDocument";
```

Localisez la chaîne et attribuez-lui la valeur:

```as3
 "http://localhost:8080/soap/services/MyApplication/EncryptDocument?blob=http";
```

**Référencement de l’assemblage .NET clienMyApplication/EncryptDocument**

Placez votre nouvel assemblage client .NET sur l’ordinateur sur lequel vous développez votre application cliente. Après avoir placé l’assemblage client .NET dans un répertoire, vous pouvez le référencer à partir d’un projet. Référencez la variable `System.Web.Services` de votre projet. Si vous ne référencez pas cette bibliothèque, vous ne pouvez pas utiliser l’assemblage client .NET pour appeler un service.

1. Dans le **Projet** menu, sélectionnez **Ajouter une référence**.
1. Cliquez sur le bouton **.NET** .
1. Cliquez sur **Parcourir** et recherchez le fichier DocumentService.dll .
1. Cliquez sur **Sélectionner** puis cliquez sur **OK**.

**Appel d’un service à l’aide d’un assemblage client .NET qui utilise des données BLOB sur HTTP**

Vous pouvez appeler le `MyApplication/EncryptDocument` service (qui a été créé dans Workbench) à l’aide d’un assemblage client .NET qui utilise des données via HTTP. Pour appeler la fonction `MyApplication/EncryptDocument` effectuez les étapes suivantes :

1. Créez l’assemblage client .NET.
1. Référencez l’assemblage client Microsoft .NET. Créez un projet Microsoft .NET client. Référencez l’assemblage client Microsoft .NET dans le projet client. Référence également `System.Web.Services`.
1. À l’aide de l’assemblage client .NET Microsoft, créez une `MyApplication_EncryptDocumentService` en appelant son constructeur par défaut.
1. Définissez la variable `MyApplication_EncryptDocumentService` de `Credentials` avec une propriété `System.Net.NetworkCredential` . Dans le `System.Net.NetworkCredential` constructeur, indiquez un nom d’utilisateur AEM forms et le mot de passe correspondant. Définissez des valeurs d’authentification pour permettre à votre application cliente .NET d’échanger des messages SOAP avec AEM Forms.
1. Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour transmettre des données à la variable `MyApplication/EncryptDocument` processus.
1. Attribuez une valeur string à la variable `BLOB` de `remoteURL` membre de données qui spécifie l’emplacement URI d’un document de PDF à transmettre au `MyApplication/EncryptDocument`service.
1. Appeler la variable `MyApplication/EncryptDocument` en appelant le `MyApplication_EncryptDocumentService` de `invoke` et transmission de la méthode `BLOB` . Ce processus renvoie un document de PDF chiffré dans un `BLOB` .
1. Créez un `System.UriBuilder` en utilisant son constructeur et en transmettant la valeur de la valeur renvoyée `BLOB` de `remoteURL` membre de données.
1. Convertir la variable `System.UriBuilder` vers un objet `System.IO.Stream` . (Le didacticiel de mise en route C# qui suit cette liste illustre comment effectuer cette tâche.)
1. Créez un tableau d’octets et renseignez-le avec les données situées dans la variable `System.IO.Stream` .
1. Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
1. Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

### Appel d’un service à l’aide de classes proxy Java et de données BLOB sur HTTP {#invoking-a-service-using-java-proxy-classes-and-blob-data-over-http}

Vous pouvez appeler un service AEM Forms à l’aide de classes proxy Java et de données BLOB sur HTTP. Pour appeler la fonction `MyApplication/EncryptDocument` à l’aide des classes proxy Java, procédez comme suit :

1. Créez des classes proxy Java à l’aide de JAX-WS qui utilise la variable `MyApplication/EncryptDocument` service WSDL. Utilisez le point d’entrée WSDL suivant :

   ```as3
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

   Pour plus d’informations, voir [Création de classes de proxy Java à l’aide de JAX-WS](#creating-java-proxy-classes-using-jax-ws).

   >[!NOTE]
   >
   >Remplacer `hiro-xp`* avec l’adresse IP du serveur d’applications J2EE hébergeant AEM Forms. *

1. Regroupez les classes proxy Java créées à l’aide de JAX-WS dans un fichier JAR.
1. Incluez le fichier JAR du proxy Java et les fichiers JAR situés dans le chemin d’accès suivant :

   &lt;install directory=&quot;&quot;>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   dans le chemin de classe de votre projet client Java.

1. Créez un objet `MyApplicationEncryptDocumentService` en utilisant son constructeur.
1. Créez un `MyApplicationEncryptDocument` en appelant le `MyApplicationEncryptDocumentService` de `getEncryptDocument` .
1. Définissez les valeurs de connexion requises pour appeler AEM Forms en affectant des valeurs aux membres de données suivants :

   * Affectez le point d’entrée WSDL et le type de codage au `javax.xml.ws.BindingProvider` de `ENDPOINT_ADDRESS_PROPERTY` champ . Pour appeler la fonction `MyApplication/EncryptDocument` à l’aide de l’encodage BLOB sur HTTP, spécifiez la valeur d’URL suivante :

      `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=http`

   * Affectez l’utilisateur d’AEM forms à la variable `javax.xml.ws.BindingProvider` de `USERNAME_PROPERTY` champ .
   * Attribuez la valeur de mot de passe correspondante à la variable `javax.xml.ws.BindingProvider` de `PASSWORD_PROPERTY` champ .

   L’exemple de code suivant illustre cette logique d’application :

   ```as3
    //Set connection values required to invoke AEM Forms 
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=http"; 
    String username = "administrator"; 
    String password = "password"; 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url); 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username); 
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Créez un objet `BLOB` en utilisant son constructeur.
1. Renseignez la variable `BLOB` en appelant son objet `setRemoteURL` . Transmettez une valeur string qui spécifie l’emplacement URI d’un document de PDF à transmettre au `MyApplication/EncryptDocument` service.
1. Appeler la variable `MyApplication/EncryptDocument` en appelant le `MyApplicationEncryptDocument` de `invoke` et transmission de la méthode `BLOB` contenant le document du PDF. Ce processus renvoie un document de PDF chiffré dans un `BLOB` .
1. Créez un tableau d’octets pour stocker le flux de données qui représente le document de PDF chiffré. Appeler la variable `BLOB` de `getRemoteURL` (utilisez la méthode `BLOB` renvoyé par l’objet `invoke` ).
1. Créez un objet `java.io.File` en utilisant son constructeur. Cet objet représente le document de PDF chiffré.
1. Créez un objet `java.io.FileOutputStream` en utilisant son constructeur et en transmettant l’objet `java.io.File`. 
1. Appeler la variable `java.io.FileOutputStream` de `write` . Transmettez le tableau d’octets contenant le flux de données qui représente le document de PDF chiffré.

## Appel d’AEM Forms à l’aide de DIME {#invoking-aem-forms-using-dime}

Vous pouvez appeler les services AEM Forms à l’aide de SOAP avec des pièces jointes. AEM Forms prend en charge les normes de service Web MIME et DIME. DIME vous permet d’envoyer des pièces jointes binaires, telles que des documents de PDF, ainsi que des demandes d’appel au lieu de coder la pièce jointe. Le *Appel d’AEM Forms à l’aide de DIME* section aborde l’appel du processus de courte durée AEM Forms suivant nommé `MyApplication/EncryptDocument` à l’aide de DIME.

Lorsque ce processus est appelé, il effectue les actions suivantes :

1. Obtention du document PDF non sécurisé transmis au processus. Cette action est basée sur l’opération `SetValue`. Le paramètre d’entrée pour ce processus est une variable de processus `document` désignée par `inDoc`.
1. Chiffrement du document PDF avec un mot de passe. Cette action est basée sur l’opération `PasswordEncryptPDF`. Le document PDF chiffré avec un mot de passe est retourné dans une variable de processus nommée `outDoc`.

Ce processus n’est pas basé sur un processus AEM Forms existant. Pour suivre les exemples de code, créez un processus nommé `MyApplication/EncryptDocument`**à l’aide de Workbench. (Voir [Utilisation de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

>[!NOTE]
>
>L’appel des opérations de service AEM Forms à l’aide de DIME est obsolète. Il est recommandé d’utiliser MTOM. (Voir [Appel d’AEM Forms à l’aide de MTOM](#invoking-aem-forms-using-mtom).)

### Création d’un projet .NET qui utilise DIME {#creating-a-net-project-that-uses-dime}

Pour créer un projet .NET pouvant appeler un service Forms à l’aide de DIME, effectuez les tâches suivantes :

* Installez les améliorations des services Web 2.0 sur votre ordinateur de développement.
* Dans votre projet .NET, créez une référence Web au service Forms FormsAEM.

**Installation des améliorations des services web 2.0**

Installez les améliorations des services web 2.0 sur votre ordinateur de développement et intégrez-le à Microsoft Visual Studio .NET. Vous pouvez télécharger les améliorations des services Web 2.0 à partir de la [Centre de téléchargement Microsoft.](https://www.microsoft.com/downloads/search.aspx)

Sur cette page web, recherchez les améliorations apportées aux services web 2.0 et téléchargez-les sur votre ordinateur de développement. Ce téléchargement place un fichier nommé Microsoft WSE 2.0 SPI.msi sur votre ordinateur. Exécutez le programme d&#39;installation et suivez les instructions en ligne.

>[!NOTE]
>
>La version 2.0 des améliorations des services web prend en charge DIME. La version prise en charge de Microsoft Visual Studio est 2003 lors de l’utilisation des améliorations des services web 2.0. Les améliorations des services web 3.0 ne prennent pas en charge DIME ; cependant, il prend en charge MTOM.

**Création d’une référence web à un service AEM Forms**

Après avoir installé la version 2.0 des améliorations des services web sur votre ordinateur de développement et créé un projet Microsoft .NET, créez une référence web au service Forms. Par exemple, pour créer une référence web au `MyApplication/EncryptDocument` et en supposant que Forms soit installé sur l’ordinateur local, indiquez l’URL suivante :

```as3
     http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL
```

Après avoir créé une référence web, vous pouvez utiliser les deux types de données proxy suivants dans votre projet .NET : `EncryptDocumentService` et `EncryptDocumentServiceWse`. Pour appeler la fonction `MyApplication/EncryptDocument` processus à l’aide de DIME, utilisez `EncryptDocumentServiceWse` type.

>[!NOTE]
>
>Avant de créer une référence Web au service Forms, veillez à référencer les améliorations des services Web 2.0 dans votre projet. (Voir &quot;Installation des améliorations des services Web 2.0&quot;.)

**Référence à la bibliothèque WSE**

1. Dans le menu Projet, sélectionnez Ajouter une référence.
1. Dans la boîte de dialogue Ajouter une référence, sélectionnez Microsoft.Web.Services2.dll.
1. Sélectionnez System.Web.Services.dll.
1. Cliquez sur Sélectionner, puis sur OK.

**Création d’une référence web à un service Forms**

1. Dans le menu Projet, sélectionnez Ajouter une référence web.
1. Dans la boîte de dialogue URL, spécifiez l’URL du service Forms.
1. Cliquez sur Aller , puis sur Ajouter une référence.

>[!NOTE]
>
>Assurez-vous d’activer votre projet .NET pour utiliser la bibliothèque WSE. Dans l’Explorateur de projets, cliquez avec le bouton droit sur le nom du projet et sélectionnez Activer WSE 2.0. Assurez-vous que la case à cocher de la boîte de dialogue qui s’affiche est cochée.

**Appel d’un service à l’aide de DIME dans un projet .NET**

Vous pouvez appeler un service Forms à l’aide de DIME. Considérez la variable `MyApplication/EncryptDocument` processus qui accepte un document de PDF non sécurisé et renvoie un document de PDF chiffré par mot de passe. Pour appeler la fonction `MyApplication/EncryptDocument` effectuez les étapes suivantes à l’aide de DIME :

1. Créez un projet Microsoft .NET qui vous permet d’appeler un service Forms à l’aide de DIME. Veillez à inclure les améliorations des services web 2.0 et à créer une référence web au service AEM Forms.
1. Après avoir défini une référence web à la variable `MyApplication/EncryptDocument` processus, créer une `EncryptDocumentServiceWse` en utilisant son constructeur par défaut.
1. Définissez la variable `EncryptDocumentServiceWse` de `Credentials` membre de données avec un `System.Net.NetworkCredential` qui spécifie le nom d’utilisateur et le mot de passe d’AEM forms.
1. Créez un `Microsoft.Web.Services2.Dime.DimeAttachment` en utilisant son constructeur et en transmettant les valeurs suivantes :

   * Une valeur string qui spécifie une valeur GUID. Vous pouvez obtenir une valeur GUID en appelant la variable `System.Guid.NewGuid.ToString` .
   * Une valeur string qui spécifie le type de contenu. Comme ce processus nécessite un document de PDF, spécifiez `application/pdf`.
   * A `TypeFormat` valeur d’énumération. Spécifiez `TypeFormat.MediaType`.
   * Une valeur string qui spécifie l’emplacement du document du PDF à transmettre au processus AEM Forms.

1. Créez un objet `BLOB` en utilisant son constructeur.
1. Ajoutez la pièce jointe DIME à la fonction `BLOB` en attribuant l’objet `Microsoft.Web.Services2.Dime.DimeAttachment` de `Id` de la valeur du membre de données au `BLOB` de `attachmentID` membre de données.
1. Appeler la variable `EncryptDocumentServiceWse.RequestSoapContext.Attachments.Add` et transmettez la méthode `Microsoft.Web.Services2.Dime.DimeAttachment` .
1. Appeler la variable `MyApplication/EncryptDocument` en appelant le `EncryptDocumentServiceWse` de `invoke` et transmission de la méthode `BLOB` qui contient la pièce jointe DIME. Ce processus renvoie un document de PDF chiffré dans un `BLOB` .
1. Obtenez la valeur de l’identifiant de pièce jointe en obtenant la valeur de la valeur renvoyée `BLOB` de `attachmentID` membre de données.
1. Effectuez une itération sur les pièces jointes situées dans `EncryptDocumentServiceWse.ResponseSoapContext.Attachments` et utilisez la valeur d’identifiant de pièce jointe pour obtenir le document de PDF chiffré.
1. Obtention d’un `System.IO.Stream` en obtenant la valeur de la variable `Attachment` de `Stream` membre de données.
1. Créez un tableau d’octets et transmettez ce tableau d’octets à la variable `System.IO.Stream` de `Read` . Cette méthode renseigne le tableau d’octets avec un flux de données qui représente le document de PDF chiffré.
1. Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente un emplacement de fichier PDF. Cet objet représente le document de PDF chiffré.
1. Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
1. Ecrivez le contenu du tableau d’octets dans le fichier du PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

### Création de classes proxy Java Apache Axe qui utilisent DIME {#creating-apache-axis-java-proxy-classes-that-use-dime}

Vous pouvez utiliser l’outil Apache Axis WSDL2Java pour convertir un WSDL de service en classes proxy Java afin d’appeler les opérations de service. Avec Apache Ant, vous pouvez générer des fichiers de bibliothèque Axis à partir d’un WSDL de service AEM Forms qui vous permet d’appeler le service. (Voir [Création de classes proxy Java à l’aide de l’axe Apache](#creating-java-proxy-classes-using-apache-axis).)

L’outil Apache Axis WSDL2Java génère des fichiers JAVA contenant des méthodes utilisées pour envoyer des requêtes SOAP à un service. Les requêtes SOAP reçues par un service sont décodées par les bibliothèques générées par l’axe et transformées en méthodes et arguments.

Pour appeler la fonction `MyApplication/EncryptDocument` (qui a été créé dans Workbench) à l’aide de fichiers de bibliothèque générés par Axis et de DIME, effectuez les étapes suivantes :

1. Créez des classes proxy Java qui utilisent la variable `MyApplication/EncryptDocument` Service WSDL à l’aide de l’axe Apache. (Voir [Création de classes proxy Java à l’aide de l’axe Apache](#creating-java-proxy-classes-using-apache-axis).)
1. Incluez les classes proxy Java dans le chemin de classe.
1. Créez un objet `MyApplicationEncryptDocumentServiceLocator` en utilisant son constructeur.
1. Créez un `URL` en utilisant son constructeur et en transmettant une valeur string qui spécifie la définition WSDL du service AEM Forms. Assurez-vous que vous spécifiez `?blob=dime` à la fin de l’URL du point d’entrée SOAP. Utilisez par exemple

   ```as3
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=dime.
   ```

1. Créez un `EncryptDocumentSoapBindingStub` en appelant son constructeur et en transmettant l’objet `MyApplicationEncryptDocumentServiceLocator`et le `URL` .
1. Définissez la valeur du nom d’utilisateur et du mot de passe d’AEM forms en appelant la variable `EncryptDocumentSoapBindingStub` de `setUsername` et `setPassword` méthodes.

   ```as3
    encryptionClientStub.setUsername("administrator"); 
    encryptionClientStub.setPassword("password");
   ```

1. Récupérer le document du PDF à envoyer à la fonction `MyApplication/EncryptDocument` en créant un `java.io.File` . Transmettez une valeur string qui spécifie l’emplacement du document du PDF.
1. Créez un `javax.activation.DataHandler` en utilisant son constructeur et en transmettant un objet `javax.activation.FileDataSource` . Le `javax.activation.FileDataSource` peut être créé en utilisant son constructeur et en transmettant la variable `java.io.File` qui représente le document du PDF.
1. Créez un `org.apache.axis.attachments.AttachmentPart` en utilisant son constructeur et en transmettant l’objet `javax.activation.DataHandler` .
1. Joindre la pièce jointe en appelant la fonction `EncryptDocumentSoapBindingStub` de `addAttachment` et transmission de la méthode `org.apache.axis.attachments.AttachmentPart` .
1. Créez un objet `BLOB` en utilisant son constructeur. Renseignez la variable `BLOB` avec la valeur de l’identifiant de la pièce jointe en appelant `BLOB` de `setAttachmentID` et transmission de la valeur de l’identifiant de la pièce jointe. Cette valeur peut être obtenue en appelant la méthode `org.apache.axis.attachments.AttachmentPart` de `getContentId` .
1. Appeler la variable `MyApplication/EncryptDocument` en appelant le `EncryptDocumentSoapBindingStub` de `invoke` . Transmettez la variable `BLOB` qui contient la pièce jointe DIME. Ce processus renvoie un document de PDF chiffré dans un `BLOB` .
1. Obtenez la valeur de l’identifiant de la pièce jointe en appelant le `BLOB` de `getAttachmentID` . Cette méthode renvoie une valeur string qui représente la valeur d’identifiant de la pièce jointe renvoyée.
1. Récupérez les pièces jointes en appelant la méthode `EncryptDocumentSoapBindingStub` de `getAttachments` . Cette méthode renvoie un tableau de `Objects` qui représentent les pièces jointes.
1. Effectuez une itération à travers les pièces jointes (le `Object` ) et utiliser la valeur d’identifiant de pièce jointe pour obtenir le document de PDF chiffré. Chaque élément est une `org.apache.axis.attachments.AttachmentPart` .
1. Obtenez la variable `javax.activation.DataHandler` de la pièce jointe en appelant la méthode `org.apache.axis.attachments.AttachmentPart` de `getDataHandler` .
1. Obtention d’un `java.io.FileStream` en appelant le `javax.activation.DataHandler` de `getInputStream` .
1. Créez un tableau d’octets et transmettez ce tableau d’octets à la variable `java.io.FileStream` de `read` . Cette méthode renseigne le tableau d’octets avec un flux de données qui représente le document de PDF chiffré.
1. Créez un objet `java.io.File` en utilisant son constructeur. Cet objet représente le document de PDF chiffré.
1. Créez un objet `java.io.FileOutputStream` en utilisant son constructeur et en transmettant l’objet `java.io.File`. 
1. Appeler la variable `java.io.FileOutputStream` de `write` et transmettez le tableau byte qui contient le flux de données qui représente le document de PDF chiffré.

**Voir également**

[Démarrage rapide : Appel d’un service à l’aide de DIME dans un projet Java](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-dime-in-a-java-project)

## Utilisation de l’authentification SAML {#using-saml-based-authentication}

AEM Forms prend en charge différents modes d’authentification des services Web lors de l’appel de services. Un mode d’authentification consiste à spécifier un nom d’utilisateur et une valeur de mot de passe à l’aide d’un en-tête d’autorisation de base dans l’appel au service Web. AEM Forms prend également en charge l’authentification basée sur l’assertion SAML. Lorsqu’une application cliente appelle un service AEM Forms à l’aide d’un service web, l’application cliente peut fournir des informations d’authentification de l’une des manières suivantes :

* Transmission des informations d’identification dans le cadre de l’autorisation de base
* Transmission d’un jeton username dans l’en-tête WS-Security
* Transmission d’une assertion SAML dans le cadre de l’en-tête WS-Security
* Transmission du jeton Kerberos dans l’en-tête WS-Security

AEM Forms ne prend pas en charge l’authentification par certificat standard, mais l’authentification par certificat est prise en charge sous une autre forme.

>[!NOTE]
>
>Le service Web démarre rapidement dans Programmation avec AEM Forms pour spécifier les valeurs de nom d’utilisateur et de mot de passe afin d’effectuer l’autorisation.

L’identité des utilisateurs d’AEM forms peut être représentée par une assertion SAML signée à l’aide d’une clé secrète. Le code XML suivant illustre un exemple d’assertion SAML.

```as3
 <Assertion xmlns="urn:oasis:names:tc:SAML:1.0:assertion" 
     xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" 
     xmlns:samlp="urn:oasis:names:tc:SAML:1.0:protocol" 
     AssertionID="fd4bd0c87302780e0d9bbfa8726d5bc0" IssueInstant="2008-04-17T13:47:00.720Z" Issuer="LiveCycle" 
     MajorVersion="1" MinorVersion="1"> 
     <Conditions NotBefore="2008-04-17T13:47:00.720Z" NotOnOrAfter="2008-04-17T15:47:00.720Z"> 
     </Conditions> 
     <AuthenticationStatement 
         AuthenticationInstant="2008-04-17T13:47:00.720Z" 
         AuthenticationMethod="urn:oasis:names:tc:SAML:1.0:am:unspecified"> 
         <Subject> 
             <NameIdentifier NameQualifier="DefaultDom">administrator</NameIdentifier> 
             <SubjectConfirmation> 
                 <ConfirmationMethod>urn:oasis:names:tc:SAML:1.0:cm:sender-vouches</ConfirmationMethod> 
             </SubjectConfirmation> 
         </Subject> 
     </AuthenticationStatement> 
     <ds:Signature > 
         <ds:SignedInfo> 
             <ds:CanonicalizationMethod Algorithm="https://www.w3.org/2001/10/xml-exc-c14n#"></ds:CanonicalizationMethod> 
             <ds:SignatureMethod    Algorithm="https://www.w3.org/2000/09/xmldsig#hmac-sha1"></ds:SignatureMethod> 
             <ds:Reference URI="#fd4bd0c87302780e0d9bbfa8726d5bc0"> 
                 <ds:Transforms> 
                     <ds:Transform Algorithm="https://www.w3.org/2000/09/xmldsig#enveloped-signature"></ds:Transform> 
                     <ds:Transform Algorithm="https://www.w3.org/2001/10/xml-exc-c14n#"> 
                         <ec:InclusiveNamespaces     
                             PrefixList="code ds kind rw saml samlp typens #default"> 
                         </ec:InclusiveNamespaces> 
                     </ds:Transform> 
                 </ds:Transforms> 
                 <ds:DigestMethod Algorithm="https://www.w3.org/2000/09/xmldsig#sha1"></ds:DigestMethod> 
                 <ds:DigestValue>hVrtqjWr+VzaVUIpQx0YI9lIjaY=</ds:DigestValue> 
             </ds:Reference> 
         </ds:SignedInfo> 
         <ds:SignatureValue>UMbBb+cUcPtcWDCIhXes4n4FxfU=</ds:SignatureValue> 
     </ds:Signature> 
 </Assertion>
```

Cet exemple d’assertion est émis pour un utilisateur administrateur. Cette assertion contient les éléments visibles suivants :

* Il est valide pendant une certaine durée.
* Il est émis pour un utilisateur particulier.
* Il est signé numériquement. Toute modification apportée à ce dernier endommagerait la signature.
* Il peut être présenté à AEM Forms sous la forme d’un jeton d’identité de l’utilisateur similaire au nom d’utilisateur et au mot de passe.

Une application cliente peut récupérer l’assertion de toute API AEM Forms AuthenticationManager qui renvoie une `AuthResult` . Vous pouvez obtenir un `AuthResult` en effectuant l’une des deux méthodes suivantes :

* Authentification de l’utilisateur à l’aide de l’une des méthodes d’authentification exposées par l’API AuthenticationManager. En règle générale, on utilise le nom d’utilisateur et le mot de passe ; toutefois, vous pouvez également utiliser l’authentification de certificat.
* En utilisant la variable `AuthenticationManager.getAuthResultOnBehalfOfUser` . Cette méthode permet à une application cliente d’obtenir une `AuthResult` pour tout utilisateur d’AEM forms.

un utilisateur d’AEM forms peut être authentifié à l’aide d’un jeton SAML obtenu. Cette assertion SAML (fragment xml) peut être envoyée dans le cadre de l’en-tête WS-Security avec l’appel du service web pour l’authentification de l’utilisateur. En règle générale, une application client a authentifié un utilisateur, mais n’a pas stocké les informations d’identification de l’utilisateur. (Ou l’utilisateur s’est connecté à ce client par le biais d’un mécanisme autre que l’utilisation d’un nom d’utilisateur et d’un mot de passe.) Dans ce cas, l’application cliente doit appeler AEM Forms et emprunter l’identité d’un utilisateur spécifique autorisé à appeler AEM Forms.

Pour emprunter l’identité d’un utilisateur spécifique, appelez le `AuthenticationManager.getAuthResultOnBehalfOfUser` à l’aide d’un service web. Cette méthode renvoie une `AuthResult` qui contient l’assertion SAML de cet utilisateur.

Ensuite, utilisez cette assertion SAML pour appeler tout service nécessitant une authentification. Cette action implique l’envoi de l’assertion dans le cadre de l’en-tête SOAP. Lorsqu’un appel de service Web est effectué avec cette assertion, AEM Forms identifie l’utilisateur comme étant celui représenté par cette assertion. En d’autres termes, l’utilisateur spécifié dans l’assertion est l’utilisateur qui appelle le service.

### Utilisation des classes Apache Axis et de l’authentification SAML {#using-apache-axis-classes-and-saml-based-authentication}

Vous pouvez appeler un service AEM Forms par des classes proxy Java qui ont été créées à l’aide de la bibliothèque Axes. (Voir [Création de classes proxy Java à l’aide de l’axe Apache](#creating-java-proxy-classes-using-apache-axis).)

Lors de l’utilisation d’AXIS qui utilise l’authentification SAML, enregistrez le gestionnaire de requêtes et de réponses avec Axes. Apache Axis appelle le gestionnaire avant d’envoyer une demande d’appel à AEM Forms. Pour enregistrer un gestionnaire, créez une classe Java qui étend `org.apache.axis.handlers.BasicHandler`.

**Création d’un gestionnaire d’assertion avec axe**

La classe Java suivante, nommée `AssertionHandler.java`, illustre un exemple de classe Java qui étend `org.apache.axis.handlers.BasicHandler`.

```as3
 public class AssertionHandler extends BasicHandler { 
        public void invoke(MessageContext ctx) throws AxisFault { 
            String assertion = (String) ctx.getProperty(LC_ASSERTION); 
  
            //no assertion hence nothing to insert 
            if(assertion == null) return;  
      
            try { 
                MessageElement samlElement = new MessageElement(convertToXML(assertion)); 
                SOAPHeader header = (SOAPHeader) ctx.getRequestMessage().getSOAPHeader(); 
                //Create the wsse:Security element which would contain the SAML element 
                SOAPElement wsseHeader = header.addChildElement("Security", "wsse", WSSE_NS); 
                wsseHeader.appendChild(samlElement); 
                //remove the actor attribute as in LC we do not specify any actor. This would not remove the actor attribute though 
                //it would only remove it from the soapenv namespace 
                wsseHeader.getAttributes().removeNamedItem("actor"); 
            } catch (SOAPException e) { 
                throw new AxisFault("Error occured while adding the assertion to the SOAP Header",e); 
            } 
        } 
 }
```

**Enregistrer le gestionnaire**

Pour enregistrer un gestionnaire avec Axis, créez un fichier client-config.wsdd . Par défaut, Axis recherche un fichier portant ce nom. Le code XML suivant est un exemple de fichier client-config.wsdd. Voir la documentation Axes pour plus d’informations.

```as3
 <deployment xmlns="https://xml.apache.org/axis/wsdd/" xmlns:java="https://xml.apache.org/axis/wsdd/providers/java"> 
     <transport name="http" pivot="java:org.apache.axis.transport.http.HTTPSender"/> 
      <globalConfiguration > 
       <requestFlow > 
        <handler type="java:com.adobe.idp.um.example.AssertionHandler" /> 
       </requestFlow > 
      </globalConfiguration > 
 </deployment> 
 
```

**Appeler un service AEM Forms**

L’exemple de code suivant appelle un service AEM Forms à l’aide de l’authentification SAML.

```as3
 public class ImpersonationExample { 
        . . . 
        public void  authenticateOnBehalf(String superUsername,String password,  
                String canonicalName,String domainName) throws UMException, RemoteException{ 
            ((org.apache.axis.client.Stub) authenticationManager).setUsername(superUsername); 
            ((org.apache.axis.client.Stub) authenticationManager).setPassword(password); 
      
            //Step 1 - Invoke the Auth manager api to get an assertion for the user to be impersonated 
            AuthResult ar = authenticationManager.getAuthResultOnBehalfOfUser(canonicalName, domainName, null); 
            String assertion = ar.getAssertion(); 
            //Step 2 - Setting the assertion here to be picked later by the AssertionHandler. Note that stubs are not threadSafe 
            //hence should not be reused. For this simple example we have made them instance variable but care should be taken 
            //regarding the thread safety 
            ((javax.xml.rpc.Stub) authorizationManager)._setProperty(AssertionHandler.LC_ASSERTION, assertion); 
        } 
      
        public Role findRole(String roleId) throws UMException, RemoteException{ 
            //This api would be invoked under bob's user rights 
            return authorizationManager.findRole(roleId); 
        } 
      
        public static void main(String[] args) throws Exception { 
            ImpersonationExample ie = new ImpersonationExample("http://localhost:5555"); 
            //Get the SAML assertion for the user to impersonate and store it in stub 
            ie.authenticateOnBehalf( 
                    "administrator", //The Super user which has the required impersonation permission 
                    "password", // Password of the super user as referred above 
                    "bob", //Cannonical name of the user to impersonate 
                    "testdomain" //Domain of the user to impersonate 
                    ); 
      
            Role r = ie.findRole("BASIC_ROLE_ADMINISTRATOR"); 
            System.out.println("Role "+r.getName()); 
        } 
 }
```

### Utilisation d’un assemblage client .NET et d’une authentification SAML {#using-a-net-client-assembly-and-saml-based-authentication}

Vous pouvez appeler un service Forms à l’aide d’un assemblage client .NET et d’une authentification SAML. Pour ce faire, vous devez utiliser la version 3.0 (WSE) des améliorations du service Web. Pour plus d’informations sur la création d’un assemblage client .NET qui utilise WSE, voir [Création d’un projet .NET qui utilise DIME](#creating-a-net-project-that-uses-dime).

>[!NOTE]
>
>La section DIME utilise WSE 2.0. Pour utiliser l’authentification SAML, suivez les mêmes instructions que celles spécifiées dans la rubrique DIME. Cependant, remplacez WSE 2.0 par WSE 3.0. Installez les améliorations des services web 3.0 sur votre ordinateur de développement et intégrez-le à Microsoft Visual Studio .NET. Vous pouvez télécharger les améliorations des services Web 3.0 à partir de la [Centre de téléchargement Microsoft](https://www.microsoft.com/downloads/search.aspx).

L’architecture WSE utilise les types de données Policies, Assertions et SecurityToken . Pour un appel de service Web, spécifiez brièvement une stratégie. Une politique peut avoir plusieurs affirmations. Chaque assertion peut contenir des filtres. Un filtre est appelé à certaines étapes d’un appel de service Web et, à ce moment-là, il peut modifier la requête SOAP. Pour plus d’informations, reportez-vous à la documentation des améliorations de service Web 3.0 .

**Création de l’affirmation et du filtre**

L’exemple de code C# suivant crée des classes de filtre et d’assertion. Cet exemple de code crée un SamlAssertionOutputFilter. Ce filtre est appelé par le framework WSE avant l’envoi de la requête SOAP à AEM Forms.

```as3
 class LCSamlPolicyAssertion : Microsoft.Web.ServicES4.Design.PolicyAssertion 
 { 
        public override Microsoft.Web.ServicES4.SoapFilter CreateClientOutputFilter(FilterCreationContext context) 
        { 
           return new SamlAssertionOutputFilter(); 
        } 
        . . . 
 } 
  
      
 class SamlAssertionOutputFilter : SendSecurityFilter 
 { 
        public override void SecureMessage(SoapEnvelope envelope, Security security) 
        { 
           // Get the SamlToken from the SessionState 
           SamlToken samlToken = envelope.Context.Credentials.UltimateReceiver.GetClientToken<SamlToken>(); 
           security.Tokens.Add(samlToken); 
        } 
 }
```

**Création du jeton SAML**

Créez une classe pour représenter l’assertion SAML. La tâche principale que cette classe effectue est de convertir les valeurs de données d’une chaîne au format xml et de préserver l’espace blanc. Ce fichier XML d’assertion est ensuite importé dans la requête SOAP.

```as3
 class SamlToken : SecurityToken 
 { 
        public const string SAMLAssertion = "https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"; 
        private XmlElement _assertionElement; 
  
        public SamlToken(string assertion) 
             : base(SAMLAssertion) 
        { 
           XmlDocument xmlDoc = new XmlDocument(); 
           //The white space has to be preserved else the digital signature would get broken 
           xmlDoc.PreserveWhitespace = true; 
           xmlDoc.LoadXml(assertion); 
           _assertionElement = xmlDoc.DocumentElement; 
         } 
      
         public override XmlElement GetXml(XmlDocument document) 
         { 
            return (XmlElement)document.ImportNode(_assertionElement, true); 
         } 
        . . .  
 }
```

**Appeler un service AEM Forms**

L’exemple de code C# suivant appelle un service Forms à l’aide de l’authentification SAML.

```as3
 public class ImpersonationExample 
 { 
        . . . 
        public void AuthenticateOnBehalf(string superUsername, string password, string canonicalName, string domainName) 
        { 
            //Create a policy for UsernamePassword Token 
            Policy usernamePasswordPolicy = new Policy(); 
            usernamePasswordPolicy.Assertions.Add(new UsernameOverTransportAssertion()); 
      
            UsernameToken token = new UsernameToken(superUsername, password, PasswordOption.SendPlainText); 
            authenticationManager.SetClientCredential(token); 
            authenticationManager.SetPolicy(usernamePasswordPolicy); 
  
            //Get the SAML assertion for impersonated user 
            AuthClient.AuthenticationManagerService.AuthResult ar  
                = authenticationManager.getAuthResultOnBehalfOfUser(canonicalName, domainName, null); 
            System.Console.WriteLine("Received assertion " + ar.assertion); 
  
            //Create a policy for inserting SAML assertion 
            Policy samlPolicy = new Policy(); 
            samlPolicy.Assertions.Add(new LCSamlPolicyAssertion()); 
            authorizationManager.SetPolicy(samlPolicy); 
            //Set the SAML assertion obtained previously as the token 
            authorizationManager.SetClientCredential(new SamlToken(ar.assertion)); 
        } 
  
        public Role findRole(string roleId) 
        { 
            return authorizationManager.findRole(roleId); 
        } 
  
        static void Main(string[] args) 
        { 
            ImpersonationExample ie = new ImpersonationExample("http://localhost:5555"); 
            ie.AuthenticateOnBehalf( 
                 "administrator", //The Super user which has the required impersonation permission 
                 "password", // Password of the super user as referred above 
                 "bob", //Cannonical name of the user to impersonate 
                 "testdomain" //Domain of the user to impersonate 
                 ); 
          
         Role r = ie.findRole("BASIC_ROLE_ADMINISTRATOR"); 
            System.Console.WriteLine("Role "+r.name); 
     } 
 }
```

## Remarques connexes relatives à l’utilisation des services web {#related-considerations-when-using-web-services}

Parfois, des problèmes surviennent lors de l’appel de certaines opérations de services AEM Forms à l’aide de services web. L’objectif de cette discussion est d’identifier ces problèmes et de fournir une solution, le cas échéant.

### Appel des opérations de service de manière asynchrone {#invoking-service-operations-asynchronously}

Si vous tentez d’appeler une opération de service AEM Forms de manière asynchrone, telle que l’événement `htmlToPDF` une opération `SoapFaultException` survient. Pour résoudre ce problème, créez un fichier XML de liaison personnalisée qui mappe la variable `ExportPDF_Result` et d’autres éléments dans différentes classes. Le code XML suivant représente un fichier de liaison personnalisé.

```as3
 <bindings     
        xmlns:xsd="https://www.w3.org/2001/XMLSchema" 
        xmlns:jxb="https://java.sun.com/xml/ns/jaxb" jxb:version="1.0" 
        xmlns:wsdl="https://schemas.xmlsoap.org/wsdl/" 
      wsdlLocation="http://localhost:8080/soap/services/GeneratePDFService?wsdl&async=true&lc_version=9.0.0" 
        xmlns="https://java.sun.com/xml/ns/jaxws"> 
        <enableAsyncMapping>false</enableAsyncMapping> 
        <package name="external_customize.client"/> 
        <enableWrapperStyle>true</enableWrapperStyle> 
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='ExportPDF_Result']">            
            <jxb:class name="ExportPDFAsyncResult">             
            </jxb:class> 
        </bindings> 
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='CreatePDF_Result']">            
            <jxb:class name="CreatePDFAsyncResult">             
            </jxb:class> 
        </bindings> 
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='HtmlToPDF_Result']">            
            <jxb:class name="HtmlToPDFAsyncResult">             
            </jxb:class> 
        </bindings> 
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='OptimizePDF_Result']">            
            <jxb:class name="OptimizePDFAsyncResult">             
            </jxb:class> 
        </bindings> 
        <!--bindings node="//wsdl:portType[@name='GeneratePDFService']/wsdl:operation[@name='HtmlToPDF_Result']">               
            <jxb:class name="HtmlToPDFAsyncResult"/>             
        </bindings--> 
 </bindings>
```

Utilisez ce fichier XML lors de la création de fichiers proxy Java à l’aide de JAX-WS. (Voir [Création de classes de proxy Java à l’aide de JAX-WS](#creating-java-proxy-classes-using-jax-ws).)

Référencez ce fichier XML lors de l’exécution de l’outil JAX-WS (wsimport.exe) à l’aide de - `b` l’option de ligne de commande. Mettez à jour le `wsdlLocation` dans le fichier XML de liaison pour spécifier l’URL d’AEM Forms.

Pour vous assurer que l’appel asynchrone fonctionne, modifiez la valeur de l’URL du point de fin et spécifiez `async=true`. Par exemple, pour les fichiers proxy Java créés avec JAX-WS, spécifiez ce qui suit pour la variable `BindingProvider.ENDPOINT_ADDRESS_PROPERTY`.

`https://server:port/soap/services/ServiceName?wsdl&async=true&lc_version=9.0.0`

La liste suivante spécifie d’autres services qui ont besoin d’un fichier de liaison personnalisé lorsqu’ils sont appelés de manière asynchrone :

* PDFG 3D
* Gestionnaire des tâches
* Gestionnaire d’applications
* Gestionnaire de répertoires
* Distiller
* Gestion des droits
* Document Management

### Différences entre les serveurs d’applications J2EE {#differences-in-j2ee-application-servers}

Parfois, une bibliothèque proxy créée à l’aide d’un serveur d’applications J2EE spécifique n’appelle pas correctement AEM Forms hébergé sur un autre serveur d’applications J2EE. Prenons l’exemple d’une bibliothèque proxy générée à l’aide d’AEM Forms déployée sur WebSphere. Cette bibliothèque proxy ne peut pas appeler correctement les services AEM Forms déployés sur le serveur d’applications JBoss.

Certains types de données complexes AEM Forms, tels que `PrincipalReference`, sont définies différemment lorsqu’AEM Forms est déployé sur WebSphere par rapport à JBoss Application Server. Les différences dans les JDK utilisés par les différents services d’application J2EE sont la raison pour laquelle il existe des différences dans les définitions WSDL. Par conséquent, utilisez des bibliothèques proxy générées à partir du même serveur d’applications J2EE.

### Accès à plusieurs services à l’aide de services Web {#accessing-multiple-services-using-web-services}

En raison de conflits d’espace de noms, les objets de données ne peuvent pas être partagés entre plusieurs WSDL de service. Différents services peuvent partager des types de données et, par conséquent, les services partagent la définition de ces types dans les WSDL. Par exemple, vous ne pouvez pas ajouter deux assemblages client .NET contenant une `BLOB` type de données au même projet client .NET. Si vous tentez de le faire, une erreur de compilation se produit.

La liste suivante spécifie les types de données qui ne peuvent pas être partagés entre plusieurs WSDL de services :

* `User`
* `Principals`
* `PrincipalReference`
* `Groups`
* `Roles`
* `BLOB`

Pour éviter ce problème, il est recommandé de qualifier complètement les types de données. Prenons l’exemple d’une application .NET qui fait référence à la fois au service Forms et au service Signature à l’aide d’une référence de service. Les deux références de service contiendront une `BLOB` classe . Pour utiliser une `BLOB` , qualifiez complètement la variable `BLOB` lorsque vous la déclarez. Cette approche est présentée dans l’exemple de code suivant. Pour plus d’informations sur cet exemple de code, voir [Signature numérique d’un Forms interactif](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-interactive-forms).

L’exemple de code C# suivant montre comment signer un formulaire interactif rendu par le service Forms. L’application cliente comporte deux références de service. Le `BLOB` l’instance associée au service Forms appartient au `SignInteractiveForm.ServiceReference2` espace de noms. De même, la `BLOB` l’instance associée au service Signature appartient au `SignInteractiveForm.ServiceReference1` espace de noms. Le formulaire interactif signé est enregistré sous la forme d’un fichier PDF nommé *LoanXFASigned.pdf*.

```as3
 ???/** 
     * Ensure that you create a .NET project that uses  
     * MS Visual Studio 2008 and version 3.5 of the .NET 
     * framework. This is required to invoke a  
     * AEM Forms service using MTOM. 
     * 
     * For information, see "Invoking AEM Forms using MTOM" in Programming with AEM forms   
     */ 
 using System; 
 using System.Collections.Generic; 
 using System.Linq; 
 using System.Text; 
 using System.ServiceModel; 
 using System.IO; 
  
 //A reference to the Signature service  
 using SignInteractiveForm.ServiceReference1; 
  
 //A reference to the Forms service  
 using SignInteractiveForm.ServiceReference2; 
  
 namespace SignInteractiveForm 
 { 
        class Program 
        { 
            static void Main(string[] args) 
            { 
                try 
                { 
                    //Because BLOB objects are used in both service references 
                    //it is necessary to fully-qualify the BLOB objects 
  
                    //Retrieve the form -- invoke the Forms service 
                    SignInteractiveForm.ServiceReference2.BLOB formData = GetForm(); 
  
                    //Create a BLOB object associated with the Signature service 
                    SignInteractiveForm.ServiceReference1.BLOB sigData = new SignInteractiveForm.ServiceReference1.BLOB(); 
  
                    //Transfer the byte stream from one Forms BLOB object to the  
                    //Signature BLOB object 
                    sigData.MTOM = formData.MTOM; 
  
                    //Sign the Form -- invoke the Signature service 
                    SignForm(sigData); 
                } 
                catch (Exception ee) 
                { 
                    Console.WriteLine(ee.Message); 
                } 
            } 
  
            //Creates an interactive PDF form based on a XFA form - invoke the Forms service 
            private static SignInteractiveForm.ServiceReference2.BLOB GetForm() 
            { 
  
                try 
                { 
                    //Create a FormsServiceClient object 
                    FormsServiceClient formsClient = new FormsServiceClient(); 
                    formsClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/FormsService?blob=mtom"); 
  
                    //Enable BASIC HTTP authentication 
                    BasicHttpBinding b = (BasicHttpBinding)formsClient.Endpoint.Binding; 
                    b.MessageEncoding = WSMessageEncoding.Mtom; 
                    formsClient.ClientCredentials.UserName.UserName = "administrator"; 
                    formsClient.ClientCredentials.UserName.Password = "password"; 
                    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                    b.MaxReceivedMessageSize = 2000000; 
                    b.MaxBufferSize = 2000000; 
                    b.ReaderQuotas.MaxArrayLength = 2000000; 
  
                    //Create a BLOB to store form data 
                    SignInteractiveForm.ServiceReference2.BLOB formData = new SignInteractiveForm.ServiceReference2.BLOB(); 
                    SignInteractiveForm.ServiceReference2.BLOB pdfForm = new SignInteractiveForm.ServiceReference2.BLOB(); 
  
                    //Specify a XML form data 
                    string path = "C:\\Adobe\Loan.xml"; 
                    FileStream fs = new FileStream(path, FileMode.Open); 
  
                    //Get the length of the file stream  
                    int len = (int)fs.Length; 
                    byte[] ByteArray = new byte[len]; 
  
                    fs.Read(ByteArray, 0, len); 
                    formData.MTOM = ByteArray; 
  
                    //Specify a XML form data 
                    string path2 = "C:\\Adobe\LoanSigXFA.pdf"; 
                    FileStream fs2 = new FileStream(path2, FileMode.Open); 
  
                    //Get the length of the file stream  
                    int len2 = (int)fs2.Length; 
                    byte[] ByteArray2 = new byte[len2]; 
  
                    fs2.Read(ByteArray2, 0, len2); 
                    pdfForm.MTOM = ByteArray2; 
  
                    PDFFormRenderSpec renderSpec = new PDFFormRenderSpec(); 
                    renderSpec.generateServerAppearance = true; 
  
                    //Set out parameter values 
                    long pageCount = 1; 
                    String localValue = "en_US"; 
                    FormsResult result = new FormsResult(); 
  
                    //Render an interactive PDF form 
                    formsClient.renderPDFForm2( 
                        pdfForm, 
                        formData, 
                        renderSpec, 
                        null, 
                        null, 
                        out pageCount, 
                        out localValue, 
                        out result); 
  
                    //Write the data stream to the BLOB object 
                    SignInteractiveForm.ServiceReference2.BLOB outForm = result.outputContent; 
                    return outForm; 
                } 
                catch (Exception ee) 
                { 
                    Console.WriteLine(ee.Message); 
                } 
                return null; 
            } 
  
            //Sign the form -- invoke the Signature service 
            private static void SignForm(SignInteractiveForm.ServiceReference1.BLOB inDoc) 
            { 
  
                try 
                { 
                    //Create a SignatureServiceClient object 
                    SignatureServiceClient signatureClient = new SignatureServiceClient(); 
                    signatureClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/SignatureService?blob=mtom"); 
  
                    //Enable BASIC HTTP authentication 
                    BasicHttpBinding b = (BasicHttpBinding)signatureClient.Endpoint.Binding; 
                    b.MessageEncoding = WSMessageEncoding.Mtom; 
                    signatureClient.ClientCredentials.UserName.UserName = "administrator"; 
                    signatureClient.ClientCredentials.UserName.Password = "password"; 
                    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                    b.MaxReceivedMessageSize = 2000000; 
                    b.MaxBufferSize = 2000000; 
                    b.ReaderQuotas.MaxArrayLength = 2000000; 
  
                    //Specify the name of the signature field 
                    string fieldName = "form1[0].grantApplication[0].page1[0].SignatureField1[0]"; 
  
                    //Create a Credential object 
                    Credential myCred = new Credential(); 
                    myCred.alias = "secure"; 
  
                    //Specify the reason to sign the document 
                    string reason = "The document was reviewed"; 
  
                    //Specify the location of the signer 
                    string location = "New York HQ"; 
  
                    //Specify contact information 
                    string contactInfo = "Tony Blue"; 
  
                    //Create a PDFSignatureAppearanceOptions object  
                    //and show date information 
                    PDFSignatureAppearanceOptionSpec appear = new PDFSignatureAppearanceOptionSpec(); 
                    appear.showDate = true; 
  
                    //Sign the PDF document 
                    SignInteractiveForm.ServiceReference1.BLOB signedDoc = signatureClient.sign( 
                        inDoc, 
                        fieldName, 
                        myCred, 
                        HashAlgorithm.SHA1, 
                        reason, 
                        location, 
                        contactInfo, 
                        appear, 
                        true, 
                        null, 
                        null, 
                        null); 
  
                    //Populate a byte array with BLOB data that represents the signed form 
                    byte[] outByteArray = signedDoc.MTOM; 
  
                    //Save the signed PDF document 
                    string fileName = "C:\\Adobe\LoanXFASigned.pdf"; 
                    FileStream fs2 = new FileStream(fileName, FileMode.OpenOrCreate); 
  
                    //Create a BinaryWriter object 
                    BinaryWriter w = new BinaryWriter(fs2); 
                    w.Write(outByteArray); 
                    w.Close(); 
                    fs2.Close(); 
                } 
  
                catch (Exception ee) 
                { 
                    Console.WriteLine(ee.Message); 
                } 
            } 
        } 
 } 
  
 
```

### Services commençant par la lettre Je génère des fichiers proxy non valides {#services-starting-with-the-letter-i-produce-invalid-proxy-files}

Le nom de certaines classes de proxy générées par AEM Forms est incorrect lors de l’utilisation de Microsoft .Net 3.5 et WCF. Ce problème se produit lorsque des classes proxy sont créées pour IBMFilenetContentRepositoryConnector, IDPSchedulerService ou tout autre service dont le nom commence par la lettre I. Par exemple, le nom du client généré dans le cas d’IBMFileNetContentRepositoryConnector est `BMFileNetContentRepositoryConnectorClient`. La lettre I est manquante dans la classe proxy générée.
