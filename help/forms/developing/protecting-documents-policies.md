---
title: Protection des documents avec des stratégies
seo-title: Protecting Documents with Policies
description: Utilisez le service Document Security pour appliquer dynamiquement les paramètres de confidentialité aux documents Adobe PDF et pour conserver le contrôle sur les documents. Le service Document Security permet également aux utilisateurs de contrôler la manière dont les destinataires utilisent le document de PDF protégé par une stratégie.
seo-description: Use the Document Security service to dynamically apply confidentiality settings to Adobe PDF documents and to maintain control over the documents. The Document Security service also enables the users to maintain control over how recipients use the policy-protected PDF document.
uuid: 6feb69ef-7b61-4d0b-8c87-d65d98bae9b5
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9b1d2bf3-f28c-41b2-9026-1f3311556422
role: Developer
exl-id: 88065c4d-8ca9-4dfb-8663-ac8772e5e556
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '15500'
ht-degree: 4%

---

# Protection des documents avec des stratégies {#protecting-documents-with-policies}

**À propos du service Document Security**

Le service Document Security permet aux utilisateurs d’appliquer de manière dynamique des paramètres de confidentialité aux documents Adobe PDF et de contrôler la diffusion des documents, quelle que soit leur taille.

Le service Document Security empêche la diffusion des informations au-delà de la portée de l’utilisateur en permettant aux utilisateurs de garder un contrôle sur la manière dont les destinataires utilisent le document de PDF protégé par une stratégie. Un utilisateur peut spécifier qui peut ouvrir un document, limiter son utilisation et contrôler le document après sa distribution. Un utilisateur peut également contrôler de manière dynamique l’accès à un document protégé par une stratégie et même révoquer dynamiquement l’accès au document.

Le service Document Security protège également d’autres types de fichiers tels que les fichiers Microsoft Word (fichiers DOC). Vous pouvez utiliser l’API Client de Document Security pour utiliser ces types de fichiers. Les versions suivantes sont prises en charge :

* Fichiers Microsoft Office 2003 (DOC, XLS, fichiers PPT)
* Fichiers Microsoft Office 2007 (fichiers DOCX, XLSX, PPTX)
* Fichiers PTC Pro/E

Pour plus de clarté, les deux sections suivantes expliquent comment utiliser les documents Word :

* [Application de stratégies à des documents Word](protecting-documents-policies.md#applying-policies-to-word-documents)
* [Suppression de stratégies de documents Word](protecting-documents-policies.md#removing-policies-from-word-documents)

Vous pouvez accomplir ces tâches à l’aide du service Document Security :

* Créez des stratégies. Pour plus d’informations, voir [Création de stratégies](protecting-documents-policies.md#creating-policies).
* Modification des stratégies. Pour plus d’informations, voir [Modification de stratégies](protecting-documents-policies.md#modifying-policies).
* Supprimer des stratégies. Pour plus d’informations, voir [Suppression de stratégies](protecting-documents-policies.md#deleting-policies).
* Application de stratégies à des documents de PDF. Pour plus d’informations, voir [Application de stratégies à des documents PDF](protecting-documents-policies.md#applying-policies-to-pdf-documents).
* Supprimer des stratégies des documents de PDF. Pour plus d’informations, voir [Suppression de stratégies des documents PDF](protecting-documents-policies.md#removing-policies-from-pdf-documents).
* Documents protégés par une stratégie Inspect. Pour plus d’informations, voir [Inspection des documents de PDF protégés par une stratégie](protecting-documents-policies.md#inspecting-policy-protected-pdf-documents).
* Révoquez l’accès aux documents du PDF. Pour plus d’informations, voir [Révocation de l’accès aux documents](protecting-documents-policies.md#revoking-access-to-documents).
* Rétablissez l’accès aux documents révoqués. Pour plus d’informations, voir [Rétablissement de l’accès aux documents révoqués](protecting-documents-policies.md#reinstating-access-to-revoked-documents).
* Créez des filigranes. Pour plus d’informations, voir [Création de filigranes](protecting-documents-policies.md#creating-watermarks).
* Recherchez des événements. Pour plus d’informations, voir [Recherche d’événements](protecting-documents-policies.md#searching-for-events).

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Création de stratégies {#creating-policies}

Vous pouvez créer des stratégies par programmation à l’aide de l’API Java Document Security ou de l’API de service Web. A *policy* est un ensemble d’informations qui comprend les paramètres de Document Security, les utilisateurs autorisés et les droits d’utilisation. Vous pouvez créer et enregistrer un nombre indéfini de stratégies à l’aide des paramètres de sécurité appropriés pour différents utilisateurs et situations.

Les stratégies vous permettent d’effectuer les tâches suivantes :

* Indiquez les personnes qui peuvent ouvrir le document. Les destinataires peuvent appartenir à votre organisation ou être externes à celle-ci.
* Indiquez comment les destinataires peuvent utiliser le document. Vous pouvez restreindre l’accès à différentes fonctionnalités d’Acrobat et d’Adobe Reader. These features include the ability to print and copy text, add signatures, and add comments to a document.
* Modifiez à tout moment les paramètres d’accès et de sécurité, même après la distribution du document protégé par une stratégie.
* Monitor the use of the document after you distribute it. Vous pouvez voir comment le document est utilisé et qui l’utilise. Par exemple, vous pouvez savoir quand quelqu’un a ouvert le document.

### Creating a policy using web services {#creating-a-policy-using-web-services}

Lors de la création d’une stratégie à l’aide de l’API de service Web, référencez un fichier XML PDRL (Portable Document Rights Language) existant qui décrit la stratégie. Les autorisations de stratégie et l’entité principale sont définies dans le document PDRL. Le document XML suivant est un exemple de document PDRL.

```as3
 <?xml version="1.0" encoding="UTF-8" standalone="yes"?> 
 <Policy PolicyInstanceVersion="1" PolicyID="5DA3F847-DE76-F9CC-63EA-49A8D59154DE" PolicyCreationTime="2004-08-30T00:02:28.294+00:00" PolicyType="1" PolicySchemaVersion="1.0" PolicyName="SDK Test Policy -4344050357301573237" PolicyDescription="An SDK Test policy" xmlns="https://www.adobe.com/schema/1.0/pdrl"> 
       <PolicyEntry> 
          <ns1:Permission PermissionName="com.adobe.aps.onlineOpen" Access="ALLOW" xmlns:ns1="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns2:Permission PermissionName="com.adobe.aps.offlineOpen" Access="ALLOW" xmlns:ns2="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns3:Permission PermissionName="com.adobe.aps.pdf.editNotes" Access="ALLOW" xmlns:ns3="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns4:Permission PermissionName="com.adobe.aps.pdf.fillAndSign" Access="ALLOW" xmlns:ns4="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
          <Principal PrincipalNameType="SYSTEM"> 
             <PrincipalDomain>EDC_SPECIAL</PrincipalDomain> 
  
             <PrincipalName>all_internal_users</PrincipalName> 
          </Principal> 
       </PolicyEntry> 
       <PolicyEntry> 
          <ns5:Permission PermissionName="com.adobe.aps.onlineOpen" Access="ALLOW" xmlns:ns5="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns6:Permission PermissionName="com.adobe.aps.offlineOpen" Access="ALLOW" xmlns:ns6="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns7:Permission PermissionName="com.adobe.aps.pdf.copy" Access="ALLOW" xmlns:ns7="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns8:Permission PermissionName="com.adobe.aps.pdf.printLow" Access="ALLOW" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" xmlns:ns8="https://www.adobe.com/schema/1.0/pdrl" /> 
  
          <ns9:Permission PermissionName="com.adobe.aps.policySwitch" Access="ALLOW" xmlns:ns9="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns10:Permission PermissionName="com.adobe.aps.revoke" Access="ALLOW" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" xmlns:ns10="https://www.adobe.com/schema/1.0/pdrl" /> 
  
          <ns11:Permission PermissionName="com.adobe.aps.pdf.edit" Access="ALLOW" xmlns:ns11="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns12:Permission PermissionName="com.adobe.aps.pdf.editNotes" Access="ALLOW" xmlns:ns12="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns13:Permission PermissionName="com.adobe.aps.pdf.fillAndSign" Access="ALLOW" xmlns:ns13="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns14:Permission PermissionName="com.adobe.aps.pdf.printHigh" Access="ALLOW" xmlns:ns14="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <Principal PrincipalNameType="SYSTEM"> 
             <PrincipalDomain>EDC_SPECIAL</PrincipalDomain> 
  
             <PrincipalName>publisher</PrincipalName> 
          </Principal> 
       </PolicyEntry> 
  
       <OfflineLeasePeriod> 
          <Duration>P31D</Duration> 
       </OfflineLeasePeriod> 
  
       <AuditSettings isTracked="true" /> 
  
       <PolicyValidityPeriod isAbsoluteTime="false"> 
          <ValidityPeriodRelative> 
             <NotBeforeRelative>PT0S</NotBeforeRelative> 
  
             <NotAfterRelative>P20D</NotAfterRelative> 
          </ValidityPeriodRelative> 
       </PolicyValidityPeriod> 
 </Policy> 
 
```

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour créer une stratégie, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Définissez les attributs de la stratégie.
1. Créez une entrée de stratégie.
1. Enregistrez la stratégie.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

Les fichiers JAR suivants doivent être ajoutés au chemin d’accès aux classes de votre projet :

* adobe-rightsmanagement-client.jar
* namespace.jar (si AEM Forms est déployé sur JBoss)
* jaxb-api.jar (si AEM Forms est déployé sur JBoss)
* jaxb-impl.jar (si AEM Forms est déployé sur JBoss)
* jaxb-libs.jar (si AEM Forms est déployé sur JBoss)
* jaxb-xjc.jar (si AEM Forms est déployé sur JBoss)
* relaxngDatatype.jar (si AEM Forms est déployé sur JBoss)
* xsdlib.jar (si AEM Forms est déployé sur JBoss)
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar
* jbossall-client.jar (utilisez un fichier JAR différent si AEM Forms n’est pas déployé sur JBoss)

Pour plus d’informations sur l’emplacement de ces fichiers JAR, voir [Inclusion de fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, créez un objet client de service Document Security.

**Définition des attributs de la stratégie**

Pour créer une stratégie, définissez des attributs de stratégie. Un attribut obligatoire est le nom de la stratégie. Les noms des stratégies doivent être uniques pour chaque jeu de stratégies. Un jeu de stratégies est simplement un ensemble de stratégies. Deux stratégies peuvent porter le même nom si elles appartiennent à des jeux de stratégies distincts. Toutefois, deux stratégies d’un seul jeu ne peuvent pas avoir le même nom de stratégie.

La période de validité est un autre attribut utile à définir. Une période de validité est la période pendant laquelle un document protégé par une stratégie est accessible aux destinataires autorisés. Si vous ne définissez pas cet attribut, la stratégie est toujours valide.

Une période de validité peut être définie sur l’une des options suivantes :

* Nombre défini de jours pendant lesquels le document est accessible à partir de l’heure de publication du document.
* Date de fin à laquelle le document n’est pas accessible
* Une période spécifique pour laquelle le document est accessible
* Toujours valide

Vous pouvez spécifier uniquement une date de début, ce qui entraîne la validité de la stratégie après la date de début. Si vous indiquez uniquement une date de fin, la stratégie est valide jusqu’à la date de fin. Cependant, une exception est générée si aucune date de début et date de fin n’est définie.

Lors de la définition d’attributs appartenant à une stratégie, vous pouvez également définir des paramètres de chiffrement. Ces paramètres de chiffrement prennent effet lorsque la stratégie est appliquée à un document. Vous pouvez spécifier les valeurs de chiffrement suivantes :

* **AES256**: Représente l’algorithme de chiffrement AES avec une clé de 256 bits.
* **AES128**: Représente l’algorithme de chiffrement AES avec une clé de 128 bits.
* **NoEncryption :** Ne représente aucun chiffrement.

Lors de la spécification de la variable `NoEncryption` , vous ne pouvez pas définir la variable `PlaintextMetadata` option à `false`. Si vous tentez de le faire, une exception est générée.

>[!NOTE]
>
>Pour plus d’informations sur les autres attributs que vous pouvez définir, voir `Policy` description de l’interface dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Création d’une entrée de stratégie**

Une entrée de stratégie associe des entités, qui sont des groupes et des utilisateurs, ainsi que des autorisations à une stratégie. Une stratégie doit comporter au moins une entrée de stratégie. Supposons, par exemple, que vous effectuiez les tâches suivantes :

* Créez et enregistrez une entrée de stratégie qui permet à un groupe d’afficher uniquement un document en ligne et interdit aux destinataires de le copier.
* Associez l’entrée de stratégie à la stratégie.
* Sécurisez un document avec la stratégie à l’aide d’Acrobat.

Grâce à ces actions, les destinataires ne peuvent afficher que le document en ligne et ne peuvent pas le copier. Le document reste sécurisé jusqu’à ce que la sécurité soit supprimée.

**Enregistrement de la stratégie**

Une nouvelle stratégie doit être enregistrée avant de pouvoir être utilisée. Après avoir enregistré une stratégie, vous pouvez l’utiliser pour protéger les documents.

### Création d’une stratégie à l’aide de l’API Java {#create-a-policy-using-the-java-api}

Créez une stratégie à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `DocumentSecurityClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Définissez les attributs de la stratégie.

   * Créez un `Policy` en appelant le `InfomodelObjectFactory` statique de l’objet `createPolicy` . Cette méthode renvoie une `Policy` .
   * Définissez l’attribut name de la stratégie en appelant la variable `Policy` de `setName` et transmission d’une valeur string qui spécifie le nom de la stratégie.
   * Définissez la description de la stratégie en appelant la fonction `Policy` de `setDescription` et transmission d’une valeur string qui spécifie la description de la stratégie.
   * Définissez le jeu de stratégies auquel appartient la nouvelle stratégie en appelant la variable `Policy` de `setPolicySetName` et transmission d’une valeur string qui spécifie le nom du jeu de stratégies. (Vous pouvez spécifier `null` pour cette valeur de paramètre qui entraîne l’ajout de la stratégie à la variable *Mes stratégies* jeu de stratégies.)
   * Créez la période de validité de la stratégie en appelant la fonction `InfomodelObjectFactory` statique de l’objet `createValidityPeriod` . Cette méthode renvoie une `ValidityPeriod` .
   * Définissez le nombre de jours pendant lesquels un document protégé par une stratégie est accessible en appelant la variable `ValidityPeriod` de `setRelativeExpirationDays` et transmettre une valeur entière qui spécifie le nombre de jours.
   * Définissez la période de validité de la stratégie en appelant la variable `Policy` de `setValidityPeriod` et transmission de la méthode `ValidityPeriod` .

1. Créez une entrée de stratégie.

   * Créez une entrée de stratégie en appelant la méthode `InfomodelObjectFactory` statique de l’objet `createPolicyEntry` . Cette méthode renvoie une `PolicyEntry` .
   * Spécifiez les autorisations de la stratégie en appelant la fonction `InfomodelObjectFactory` statique de l’objet `createPermission` . Transmettez un membre de données statique qui appartient à la variable `Permission` qui représente l’autorisation. Cette méthode renvoie une `Permission` . Par exemple, pour ajouter l’autorisation qui permet aux utilisateurs de copier des données d’un document de PDF protégé par une stratégie, transmettez `Permission.COPY`. (Répétez cette étape pour chaque autorisation à ajouter).
   * Ajoutez l’autorisation à l’entrée de stratégie en appelant la méthode `PolicyEntry` de `addPermission` et transmission de la méthode `Permission` . (Répétez cette étape pour chaque `Permission` que vous avez créé).
   * Créez l’entité de stratégie en appelant la méthode `InfomodelObjectFactory` statique de l’objet `createSpecialPrincipal` . Transmettez un membre de données qui appartient à la variable `InfomodelObjectFactory` qui représente l’entité. Cette méthode renvoie une `Principal` . Par exemple, pour ajouter l’éditeur du document en tant qu’entité principale, transmettez `InfomodelObjectFactory.PUBLISHER_PRINCIPAL`.
   * Ajoutez l’entité de sécurité à l’entrée de stratégie en appelant la méthode `PolicyEntry` de `setPrincipal`et transmission de la méthode `Principal` .
   * Ajoutez l’entrée de stratégie à la stratégie en appelant la méthode `Policy` de `addPolicyEntry` et transmission de la méthode `PolicyEntry` .

1. Enregistrez la stratégie.

   * Créez un `PolicyManager` en appelant le `DocumentSecurityClient` de `getPolicyManager` .
   * Enregistrez la stratégie en appelant la méthode `PolicyManager` de `registerPolicy` et transmission des valeurs suivantes :

      * Le `Policy` qui représente la stratégie à enregistrer.
   * Une valeur string qui représente le jeu de stratégies auquel appartient la stratégie.

   Si vous utilisez un compte administrateur d’AEM forms dans les paramètres de connexion pour créer la variable `DocumentSecurityClient` , puis spécifiez le nom du jeu de stratégies lorsque vous appelez la variable `registerPolicy` . Si vous transmettez un `null` pour le jeu de stratégies, la stratégie est créée dans les administrateurs. *Mes stratégies* jeu de stratégies.

   Si vous utilisez un utilisateur Document Security dans les paramètres de connexion, vous pouvez appeler la variable surchargée `registerPolicy` qui accepte uniquement la stratégie. En d’autres termes, vous n’avez pas besoin de spécifier le nom du jeu de stratégies. Cependant, la stratégie est ajoutée au jeu de stratégies nommé *Mes stratégies*. Si vous ne souhaitez pas ajouter la nouvelle stratégie à ce jeu de stratégies, indiquez un nom de jeu de stratégies lorsque vous appelez la variable `registerPolicy` .

   >[!NOTE]
   >
   >Lors de la création d’une stratégie, référencez un jeu de stratégies existant. Si vous spécifiez un jeu de stratégies qui n’existe pas, une exception est générée.

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux sections suivantes :

* &quot;Démarrage rapide (mode SOAP) : Création d’une stratégie à l’aide de l’API Java&quot;

### Création d’une stratégie à l’aide de l’API de service Web {#create-a-policy-using-the-web-service-api}

Créez une stratégie à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `DocumentSecurityServiceClient` en utilisant son constructeur par défaut.
   * Créez un `DocumentSecurityServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. This attribute is used when you create a service reference.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `RightsManagementServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Définissez les attributs de la stratégie.

   * Créez un objet `PolicySpec` en utilisant son constructeur.
   * Définissez le nom de la stratégie en attribuant une valeur de chaîne à la variable `PolicySpec` de `name` membre de données.
   * Définissez la description de la stratégie en attribuant une valeur de chaîne à la variable `PolicySpec` de `description` membre de données.
   * Définissez le jeu de stratégies auquel la stratégie doit appartenir en attribuant une valeur string à la variable `PolicySpec` de `policySetName` membre de données. Vous devez spécifier un nom de jeu de stratégies existant. (Vous pouvez spécifier `null` pour cette valeur de paramètre qui entraîne l’ajout de la stratégie à *Mes stratégies*.)
   * Définissez la période d’ouverture hors connexion de la stratégie en attribuant une valeur entière à la variable `PolicySpec` de `offlineLeasePeriod` membre de données.
   * Définissez la variable `PolicySpec` de `policyXml` membre de données avec une valeur string qui représente les données XML PDRL. Pour effectuer cette tâche, créez un .NET `StreamReader` en utilisant son constructeur. Transmettez l’emplacement d’un fichier XML PDRL qui représente la stratégie à la variable `StreamReader` constructeur. Ensuite, appelez la fonction `StreamReader` de `ReadLine` et affecter la valeur renvoyée à une variable string . Effectuez une itération à l’aide du `StreamReader` jusqu’à ce que l’objet `ReadLine` renvoie null. Affectez la variable string à la variable `PolicySpec` de `policyXml` membre de données.

1. Créez une entrée de stratégie.

   Il n’est pas nécessaire de créer une entrée de stratégie lors de la création d’une stratégie à l’aide de l’API du service Web Document Security. L’entrée de stratégie est définie dans le document PDRL.

1. Enregistrez la stratégie.

   Enregistrez la stratégie en appelant la méthode `DocumentSecurityServiceClient` de `registerPolicy` et transmission des valeurs suivantes :

   * Le `PolicySpec` qui représente la stratégie à enregistrer.
   * Une valeur string qui représente le jeu de stratégies auquel appartient la stratégie. Vous pouvez définir une `null` qui entraîne l’ajout de la stratégie à la variable *MyPolices* jeu de stratégies.

   Si vous utilisez un compte administrateur d’AEM forms dans les paramètres de connexion pour créer la variable `DocumentSecurityClient` , spécifiez le nom du jeu de stratégies lors de l’appel de la variable `registerPolicy` .

   Si vous utilisez un utilisateur Document Security Document Security dans les paramètres de connexion, vous pouvez appeler la `registerPolicy` qui accepte uniquement la stratégie. En d’autres termes, vous n’avez pas besoin de spécifier le nom du jeu de stratégies. Cependant, la stratégie est ajoutée au jeu de stratégies nommé *Mes stratégies*. Si vous ne souhaitez pas ajouter la nouvelle stratégie à ce jeu de stratégies, indiquez un nom de jeu de stratégies lorsque vous appelez la variable `registerPolicy` .

   >[!NOTE]
   >
   >Lors de la création d’une stratégie et de la définition d’un jeu de stratégies, assurez-vous de spécifier un jeu de stratégies existant. Si vous spécifiez un jeu de stratégies qui n’existe pas, une exception est générée.

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Création d’une stratégie à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Création d’une stratégie à l’aide de l’API de service Web&quot;

## Modification de stratégies {#modifying-policies}

Vous pouvez modifier une stratégie existante à l’aide de l’API Java Document Security ou de l’API de service Web. Pour apporter des modifications à une stratégie existante, vous devez la récupérer, la modifier, puis la mettre à jour sur le serveur. Supposons, par exemple, que vous récupériez une stratégie existante et que vous étendiez sa période de validité. Avant que la modification ne prenne effet, vous devez mettre à jour la stratégie.

Vous pouvez modifier une stratégie lorsque les besoins de l’entreprise changent et que la stratégie ne reflète plus ces besoins. Au lieu de créer une nouvelle stratégie, vous pouvez simplement mettre à jour une stratégie existante.

Pour modifier les attributs de stratégie à l’aide d’un service Web (par exemple, à l’aide de classes proxy Java créées avec JAX-WS), vous devez vous assurer que la stratégie est enregistrée auprès du service Document Security. Vous pouvez ensuite référencer la stratégie existante à l’aide de la variable `PolicySpec.getPolicyXml` et modifiez les attributs de stratégie à l’aide des méthodes applicables. Par exemple, vous pouvez modifier la période d’ouverture hors connexion en appelant la variable `PolicySpec.setOfflineLeasePeriod` .

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-1}

Pour modifier une stratégie existante, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Récupérez une stratégie existante.
1. Modification des attributs de stratégie.
1. Mettez à jour la stratégie.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer une opération de service Document Security par programmation, vous devez créer un objet client de service Document Security. Si vous utilisez l’API Java, créez une `RightsManagementClient` . Si vous utilisez l’API du service Web Document Security, créez une `RightsManagementServiceService` .

**Récupération d’une stratégie existante**

Vous devez récupérer une stratégie existante pour la modifier. Pour récupérer une stratégie, spécifiez le nom de la stratégie et le jeu de stratégies auquel appartient la stratégie. Si vous spécifiez une `null` pour le nom du jeu de stratégies, la stratégie est récupérée à partir de la propriété *Mes stratégies* jeu de stratégies.

**Définition des attributs de la stratégie**

Pour modifier une stratégie, vous modifiez la valeur des attributs de stratégie. Le seul attribut de stratégie que vous ne pouvez pas modifier est l’attribut name. Par exemple, pour modifier la période d’ouverture hors connexion de la stratégie, vous pouvez modifier la valeur de l’attribut de période d’ouverture hors connexion de la stratégie.

Lors de la modification de la période d’ouverture hors connexion d’une stratégie à l’aide d’un service Web, la variable `offlineLeasePeriod` sur le champ `PolicySpec` est ignorée. Pour mettre à jour la période d’ouverture hors connexion, modifiez la variable `OfflineLeasePeriod` dans le document XML PDRL. Référencez ensuite le document XML PDRL mis à jour à l’aide du `PolicySpec` de l’interface `policyXML` membre de données.

>[!NOTE]
>
>Pour plus d’informations sur les autres attributs que vous pouvez définir, voir `Policy` description de l’interface dans [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Mise à jour de la stratégie**

Avant que les modifications apportées à une stratégie ne prennent effet, vous devez mettre à jour la stratégie avec le service Document Security. Les modifications apportées aux stratégies qui protègent des documents sont mises à jour la prochaine fois que le document protégé par une stratégie sera synchronisé avec le service Document Security.

### Modification des stratégies existantes à l’aide de l’API Java {#modify-existing-policies-using-the-java-api}

Modifiez une stratégie existante à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `RightsManagementClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez une stratégie existante.

   * Créez un `PolicyManager` en appelant le `RightsManagementClient` de `getPolicyManager` .
   * Créez un `Policy` qui représente la stratégie à mettre à jour en appelant le `PolicyManager` de `getPolicy` et transmission des valeurs suivantes&quot;

      * Une valeur string qui représente le nom du jeu de stratégies auquel appartient la stratégie. Vous pouvez indiquer `null` qui entraîne l’événement `MyPolicies` jeu de stratégies utilisé.
      * Une valeur string qui représente le nom de la stratégie.

1. Définissez les attributs de la stratégie.

   Modifiez les attributs de la stratégie pour répondre aux besoins de votre entreprise. Par exemple, pour modifier la période d’ouverture hors connexion de la stratégie, appelez la variable `Policy` de `setOfflineLeasePeriod` .

1. Mettez à jour la stratégie.

   Mettez à jour la stratégie en appelant `PolicyManager` de `updatePolicy` . Transmettez la variable `Policy` qui représente la stratégie à mettre à jour.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous à la section Démarrage rapide (mode SOAP) : Modification d’une stratégie à l’aide de la section API Java .

### Modification des stratégies existantes à l’aide de l’API de service Web {#modify-existing-policies-using-the-web-service-api}

Modifiez une stratégie existante à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `RightsManagementServiceClient` en utilisant son constructeur par défaut.
   * Créez un `RightsManagementServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `RightsManagementServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupérez une stratégie existante.

   Créez un `PolicySpec` qui représente la stratégie à modifier en appelant la variable `RightsManagementServiceClient` de `getPolicy` et transmission des valeurs suivantes :

   * Une valeur string qui spécifie le nom du jeu de stratégies auquel appartient la stratégie. Vous pouvez indiquer `null` qui entraîne l’événement `MyPolicies` jeu de stratégies utilisé.
   * Une valeur string qui spécifie le nom de la stratégie.

1. Définissez les attributs de la stratégie.

   Modifiez les attributs de la stratégie pour répondre aux besoins de votre entreprise.

1. Mettez à jour la stratégie.

   Mettez à jour la stratégie en appelant la méthode `RightsManagementServiceClient` de `updatePolicyFromSDK` et transmission de la méthode `PolicySpec` qui représente la stratégie à mettre à jour.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Modification d’une stratégie à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Modification d’une stratégie à l’aide de l’API de service Web&quot;

## Suppression de stratégies {#deleting-policies}

Vous pouvez supprimer une stratégie existante à l’aide de l’API Java Document Security ou de l’API de service Web. Une fois une stratégie supprimée, elle ne peut plus être utilisée pour protéger les documents. Toutefois, les documents existants protégés par une stratégie qui utilisent la stratégie sont toujours protégés. Vous pouvez supprimer une stratégie lorsqu’une nouvelle stratégie est disponible.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-2}

Pour supprimer une stratégie existante, procédez comme suit :

1. Include project files
1. Créez un objet API Client Document Security.
1. Supprimez la stratégie.

**Inclure les fichiers de projet**

Include necessary files into your development project. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, vous devez créer un objet client de service Document Security. Si vous utilisez l’API Java, créez une `RightsManagementClient` . Si vous utilisez l’API du service Web Document Security, créez une `RightsManagementServiceService` .

**Suppression de la stratégie**

Pour supprimer une stratégie, vous spécifiez la stratégie à supprimer et le jeu de stratégies auquel appartient la stratégie. L’utilisateur dont les paramètres sont utilisés pour appeler AEM Forms doit disposer des autorisations nécessaires pour supprimer la stratégie ; dans le cas contraire, une exception se produit. De même, si vous tentez de supprimer une stratégie qui n’existe pas, une exception se produit.

### Suppression de stratégies à l’aide de l’API Java {#delete-policies-using-the-java-api}

Supprimez une stratégie à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `RightsManagementClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Supprimez la stratégie.

   * Créez un `PolicyManager` en appelant le `RightsManagementClient` de `getPolicyManager` .
   * Supprimez la stratégie en appelant la méthode `PolicyManager` de `deletePolicy` et transmission des valeurs suivantes :

      * Une valeur string qui spécifie le nom du jeu de stratégies auquel appartient la stratégie. Vous pouvez indiquer `null` qui entraîne l’événement `MyPolicies` jeu de stratégies utilisé.
      * Une valeur string qui spécifie le nom de la stratégie à supprimer.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (mode SOAP) : Suppression d’une stratégie à l’aide de l’API Java&quot;

### Suppression de stratégies à l’aide de l’API de service Web {#delete-policies-using-the-web-service-api}

Supprimez une stratégie à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `RightsManagementServiceClient` en utilisant son constructeur par défaut.
   * Créez un `RightsManagementServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `RightsManagementServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Supprimez la stratégie.

   Pour supprimer une stratégie, appelez la méthode `RightsManagementServiceClient` de `deletePolicy` et transmission des valeurs suivantes :

   * Une valeur string qui spécifie le nom du jeu de stratégies auquel appartient la stratégie. Vous pouvez indiquer `null` qui entraîne l’événement `MyPolicies` jeu de stratégies utilisé.
   * Une valeur string qui spécifie le nom de la stratégie à supprimer.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Suppression d’une stratégie à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Suppression d’une stratégie à l’aide de l’API de service Web&quot;

## Application de stratégies à des documents PDF {#applying-policies-to-pdf-documents}

Vous pouvez appliquer une stratégie à un document de PDF afin de protéger le document. L’application d’une stratégie à un document de PDF permet de restreindre l’accès au document. Vous ne pouvez pas appliquer de stratégie à un document si celui-ci est déjà protégé par une stratégie.

Lorsque le document est ouvert, vous pouvez également restreindre l’accès aux fonctionnalités d’Acrobat et d’Adobe Reader, notamment la possibilité d’imprimer et de copier du texte, d’apporter des modifications et d’ajouter des signatures et des commentaires à un document. En outre, vous pouvez révoquer un document de PDF protégé par une stratégie lorsque vous ne souhaitez plus que les utilisateurs accèdent au document.

Vous pouvez contrôler l’utilisation d’un document protégé par une stratégie après sa distribution. C’est-à-dire, vous pouvez voir comment le document est utilisé et qui l’utilise. Par exemple, vous pouvez savoir quand un utilisateur a ouvert le document.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-3}

Pour appliquer une stratégie à un document de PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Récupérez un document de PDF auquel une stratégie est appliquée.
1. Appliquez une stratégie existante au document du PDF.
1. Enregistrez le document de PDF protégé par une stratégie.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, créez un objet client de service Document Security. Si vous utilisez l’API Java, créez une `DocumentSecurityClient` . Si vous utilisez l’API du service Web Document Security, créez une `DocumentSecurityServiceService` .

**Récupération d’un document de PDF**

Vous pouvez récupérer un document de PDF afin d’appliquer une stratégie. Une fois que vous avez appliqué une stratégie au document du PDF, les utilisateurs sont restreints lors de l’utilisation du document. Par exemple, si la stratégie ne permet pas l’ouverture du document hors ligne, les utilisateurs doivent être en ligne pour ouvrir le document.

**Application d’une stratégie existante au document du PDF**

Pour appliquer une stratégie à un document de PDF, référencez une stratégie existante et indiquez à quel jeu de stratégies elle appartient. L’utilisateur qui définit les propriétés de connexion doit avoir accès à la stratégie spécifiée. Dans le cas contraire, une exception se produit.

**Enregistrement du document du PDF**

Une fois que le service Document Security a appliqué une stratégie à un document de PDF, vous pouvez enregistrer le document de PDF protégé par une stratégie en tant que fichier de PDF.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Révocation de l’accès aux documents](protecting-documents-policies.md#revoking-access-to-documents)

### Application d’une stratégie à un document de PDF à l’aide de l’API Java {#apply-a-policy-to-a-pdf-document-using-the-java-api}

Appliquez une stratégie à un document de PDF à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `RightsManagementClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez un document de PDF.

   * Créez un `java.io.FileInputStream` qui représente le document du PDF à l’aide de son constructeur. Transmettez une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Appliquez une stratégie existante au document du PDF.

   * Créez un `DocumentManager` en appelant le `RightsManagementClient` de `getDocumentManager` .
   * Appliquez une stratégie au document du PDF en appelant la méthode `DocumentManager` de `protectDocument` et transmission des valeurs suivantes :

      * Le `com.adobe.idp.Document` contenant le document du PDF auquel la stratégie est appliquée.
      * Une valeur string qui spécifie le nom du document.
      * Une valeur string qui spécifie le nom du jeu de stratégies auquel appartient la stratégie. Vous pouvez définir une `null` qui entraîne la valeur `MyPolicies` jeu de stratégies utilisé.
      * Une valeur string qui spécifie le nom de la stratégie.
      * Une valeur string qui représente le nom du domaine User Manager de l’utilisateur qui est l’éditeur du document. Cette valeur de paramètre est facultative et peut être nulle (si ce paramètre est nul, la valeur de paramètre suivante doit être nulle).
      * Une valeur string qui représente le nom canonique de l’utilisateur du gestionnaire de l’utilisateur qui est l’éditeur du document. Cette valeur de paramètre est facultative et peut être `null` (si ce paramètre est nul, la valeur du paramètre précédent doit être `null`).
      * A `com.adobe.livecycle.rightsmanagement.Locale` qui représente le paramètre régional utilisé pour sélectionner le modèle MS Office. Cette valeur de paramètre est facultative et n’est pas utilisée pour les documents de PDF. Pour protéger un document de PDF, spécifiez `null`.

      Le `protectDocument` renvoie une `RMSecureDocumentResult` contenant le document de PDF protégé par une stratégie.


1. Enregistrez le document du PDF.

   * Appeler la variable `RMSecureDocumentResult` de `getProtectedDoc` pour obtenir le document de PDF protégé par une stratégie. Cette méthode renvoie une `com.adobe.idp.Document` .
   * Créez un `java.io.File` et assurez-vous que l’extension de fichier est PDF.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `getProtectedDoc` ).

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (mode EJB) : Application d’une stratégie à un document de PDF à l’aide de l’API Java&quot;
* &quot;Démarrage rapide (mode SOAP) : Application d’une stratégie à un document de PDF à l’aide de l’API Java&quot;

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Application d’une stratégie à un document de PDF à l’aide de l’API de service Web {#apply-a-policy-to-a-pdf-document-using-the-web-service-api}

Appliquez une stratégie à un document de PDF à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `RightsManagementServiceClient` en utilisant son constructeur par défaut.
   * Créez un `RightsManagementServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `RightsManagementServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupérez un document de PDF.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document de PDF auquel une stratégie est appliquée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Déterminez la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Appliquez une stratégie existante au document du PDF.

   Appliquez une stratégie au document du PDF en appelant la méthode `RightsManagementServiceClient` de `protectDocument` et transmission des valeurs suivantes :

   * Le `BLOB` contenant le document du PDF auquel la stratégie est appliquée.
   * Une valeur string qui spécifie le nom du document.
   * Une valeur string qui spécifie le nom du jeu de stratégies auquel appartient la stratégie. Vous pouvez définir une `null` qui entraîne la valeur `MyPolicies` jeu de stratégies utilisé.
   * Une valeur string qui spécifie le nom de la stratégie.
   * Une valeur string qui représente le nom du domaine User Manager de l’utilisateur qui est l’éditeur du document. Cette valeur de paramètre est facultative et peut être nulle (si ce paramètre est nul, la valeur de paramètre suivante doit être `null`).
   * Une valeur string qui représente le nom canonique de l’utilisateur du gestionnaire de l’utilisateur qui est l’éditeur du document. Cette valeur de paramètre est facultative et peut être nulle (si ce paramètre est nul, la valeur du paramètre précédent doit être `null`).
   * A `RMLocale` qui spécifie la valeur du paramètre régional (par exemple, `RMLocale.en`).
   * Paramètre de sortie string utilisé pour stocker la valeur de l’identifiant de stratégie.
   * Paramètre de sortie string utilisé pour stocker la valeur d’identifiant protégée par une stratégie.
   * Un paramètre de sortie string utilisé pour stocker le type MIME (par exemple, `application/pdf`).

   Le `protectDocument` renvoie une `BLOB` contenant le document de PDF protégé par une stratégie.

1. Enregistrez le document du PDF.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document de PDF protégé par une stratégie.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `protectDocument` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Application d’une stratégie à un document de PDF à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Application d’une stratégie à un document de PDF à l’aide de l’API de service Web&quot;

## Suppression de stratégies des documents PDF {#removing-policies-from-pdf-documents}

Vous pouvez supprimer une stratégie d’un document protégé par une stratégie afin de supprimer la protection du document. En d’autres termes, si vous ne souhaitez plus que le document soit protégé par une stratégie. Si vous souhaitez mettre à jour un document protégé par une stratégie avec une nouvelle stratégie, au lieu de supprimer la stratégie et d’ajouter la stratégie mise à jour, il est plus efficace de changer de stratégie.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-4}

Pour supprimer une stratégie d’un document de PDF protégé par une stratégie, procédez comme suit :

1. Inclure les fichiers de projet
1. Créez un objet API Client Document Security.
1. Récupérez un document de PDF protégé par une stratégie.
1. Supprimez la stratégie du document du PDF.
1. Enregistrez le document de PDF non sécurisé.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, créez un objet client de service Document Security.

**Récupération d’un document de PDF protégé par une stratégie**

Vous pouvez récupérer un document de PDF protégé par une stratégie afin de supprimer une stratégie. Si vous tentez de supprimer une stratégie d’un document de PDF qui n’est pas protégé par une stratégie, une exception est générée.

**Suppression de la stratégie du document du PDF**

Vous pouvez supprimer une stratégie d’un document de PDF protégé par une stratégie à condition qu’un administrateur soit spécifié dans les paramètres de connexion. Dans le cas contraire, la stratégie utilisée pour protéger un document doit contenir la variable `SWITCH_POLICY` pour supprimer une stratégie d’un document de PDF. En outre, l’utilisateur spécifié dans les paramètres de connexion AEM Forms doit également disposer de cette autorisation. Dans le cas contraire, une exception est générée.

**Enregistrement du document de PDF non sécurisé**

Une fois que le service Document Security a supprimé une stratégie d’un document de PDF, vous pouvez enregistrer le document de PDF non sécurisé en tant que fichier de PDF.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Application de stratégies à des documents PDF](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Suppression d’une stratégie d’un document de PDF à l’aide de l’API Java {#remove-a-policy-from-a-pdf-document-using-the-java-api}

Supprimez une stratégie d’un document de PDF protégé par une stratégie à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `DocumentSecurityClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez un document de PDF protégé par une stratégie.

   * Créez un `java.io.FileInputStream` qui représente le document de PDF protégé par une stratégie en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document de PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Supprimez la stratégie du document du PDF.

   * Créez un `DocumentManager` en appelant le `DocumentSecurityClient` de `getDocumentManager` .
   * Supprimez une stratégie du document du PDF en appelant la méthode `DocumentManager` de `removeSecurity` et transmission de la méthode `com.adobe.idp.Document` contenant le document de PDF protégé par une stratégie. Cette méthode renvoie une `com.adobe.idp.Document` contenant un document de PDF non sécurisé.

1. Enregistrez le document de PDF non sécurisé.

   * Créez un `java.io.File` et assurez-vous que l’extension de fichier est PDF.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `removeSecurity` ).

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (mode SOAP) : Suppression d’une stratégie d’un document de PDF à l’aide de l’API Java&quot;

### Suppression d’une stratégie à l’aide de l’API de service Web {#remove-a-policy-using-the-web-service-api}

Supprimez une stratégie d’un document de PDF protégé par une stratégie à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `DocumentSecurityServiceClient` en utilisant son constructeur par défaut.
   * Créez un `DocumentSecurityServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `DocumentSecurityServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupérez un document de PDF protégé par une stratégie.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document de PDF protégé par une stratégie à partir duquel la stratégie est supprimée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Supprimez la stratégie du document du PDF.

   Supprimez la stratégie du document du PDF en appelant la méthode `DocumentSecurityServiceClient` de `removePolicySecurity` et transmission de la méthode `BLOB` contenant le document de PDF protégé par une stratégie. Cette méthode renvoie une `BLOB` contenant un document de PDF non sécurisé.

1. Enregistrez le document de PDF non sécurisé.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document de PDF non sécurisé.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `removePolicySecurity` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Suppression d’une stratégie d’un document de PDF à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Suppression d’une stratégie d’un document de PDF à l’aide de l’API de service Web&quot;

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Révocation de l’accès aux documents {#revoking-access-to-documents}

Vous pouvez révoquer l’accès à un document de PDF protégé par une stratégie, ce qui rend toutes les copies du document inaccessibles aux utilisateurs. Lorsqu’un utilisateur tente d’ouvrir un document de PDF révoqué, il est redirigé vers une URL spécifiée où un document révisé peut être consulté. L’URL vers laquelle l’utilisateur est redirigé doit être spécifiée par programmation. Lorsque vous révoquez l’accès à un document, la modification prend effet la prochaine fois que l’utilisateur se synchronise avec le service Document Security en ouvrant le document en ligne protégé par une stratégie.

La possibilité de révoquer l’accès à un document offre une sécurité supplémentaire. Supposons, par exemple, qu’une version plus récente d’un document soit disponible et que vous ne souhaitiez plus que quiconque consulte la version obsolète. Dans ce cas, l’accès à l’ancien document peut être révoqué, et personne ne peut afficher le document à moins que l’accès ne soit rétabli.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-5}

Pour révoquer un document protégé par une stratégie, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Récupérez un document de PDF protégé par une stratégie.
1. Révoquez le document protégé par une stratégie.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, vous devez créer un objet client de service Document Security.

**Récupération d’un document de PDF protégé par une stratégie**

Pour pouvoir révoquer un document de PDF protégé par une stratégie, vous devez le récupérer. Vous ne pouvez pas révoquer un document qui a déjà été révoqué ou qui n’est pas un document protégé par une stratégie.

Si vous connaissez la valeur d’identifiant de licence du document protégé par une stratégie, il n’est pas nécessaire de récupérer le document de PDF protégé par une stratégie. Cependant, dans la plupart des cas, vous devrez récupérer le document du PDF pour obtenir la valeur de l’identifiant de licence.

**Révocation du document protégé par une stratégie**

Pour révoquer un document protégé par une stratégie, spécifiez l’identifiant de licence du document protégé par une stratégie. En outre, vous pouvez spécifier l’URL d’un document que l’utilisateur peut afficher lorsqu’il tente d’ouvrir le document révoqué. En d’autres termes, supposons qu’un document obsolète soit révoqué. Lorsqu’un utilisateur tente d’ouvrir le document révoqué, il voit un document mis à jour au lieu du document révoqué.

>[!NOTE]
>
>Si vous tentez de révoquer un document déjà révoqué, une exception est générée.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Application de stratégies à des documents PDF](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Rétablissement de l’accès aux documents révoqués](protecting-documents-policies.md#reinstating-access-to-revoked-documents)

### Révoquer l’accès aux documents à l’aide de l’API Java {#revoke-access-to-documents-using-the-java-api}

Révoquez l’accès à un document de PDF protégé par une stratégie à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Document Security

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `DocumentSecurityClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupération d’un document de PDF protégé par une stratégie

   * Créez un `java.io.FileInputStream` qui représentent le document de PDF protégé par une stratégie en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document de PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Révocation du document protégé par une stratégie

   * Créez un `DocumentManager` en appelant le `DocumentSecurityClient` de `getDocumentManager` .
   * Récupérez la valeur de l’identifiant de licence du document protégé par une stratégie en appelant la fonction `DocumentManager` de `getLicenseId` . Transmettez la variable `com.adobe.idp.Document` qui représente le document protégé par une stratégie. Cette méthode renvoie une valeur string qui représente la valeur de l’identifiant de licence.
   * Créez un `LicenseManager` en appelant le `DocumentSecurityClient` de `getLicenseManager` .
   * Révoquez le document protégé par une stratégie en appelant la fonction `LicenseManager` de `revokeLicense` et transmission des valeurs suivantes :

      * Une valeur string qui spécifie la valeur d’identifiant de licence du document protégé par une stratégie (spécifiez la valeur renvoyée par la propriété `DocumentManager` de `getLicenseId` ).
      * Un membre de données statique de la variable `License` qui spécifie le motif de révocation du document. Par exemple, vous pouvez spécifier `License.DOCUMENT_REVISED`.
      * A `java.net.URL` value that specifies the location to where a revised document is located. Si vous ne souhaitez pas rediriger un utilisateur vers une autre URL, vous pouvez transmettre `null`.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (mode SOAP) : Révocation d’un document à l’aide de l’API Java&quot;

### Révoquer l’accès aux documents à l’aide de l’API de service Web {#revoke-access-to-documents-using-the-web-service-api}

Révoquez l’accès à un document de PDF protégé par une stratégie à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un objet API client Document Security

   * Créez un `DocumentSecurityServiceClient` en utilisant son constructeur par défaut.
   * Créez un `DocumentSecurityServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `DocumentSecurityServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupération d’un document de PDF protégé par une stratégie

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document de PDF protégé par une stratégie révoqué.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document de PDF protégé par une stratégie à révoquer et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Révocation du document protégé par une stratégie

   * Récupérez la valeur de l’identifiant de licence du document protégé par une stratégie en appelant la fonction `DocumentSecurityServiceClient` de `getLicenseID` et transmission de la méthode `BLOB` qui représente le document protégé par une stratégie. Cette méthode renvoie une valeur string qui représente l’identifiant de licence.
   * Révoquez le document protégé par une stratégie en appelant la fonction `DocumentSecurityServiceClient` de `revokeLicense` et transmission des valeurs suivantes :

      * Une valeur string qui spécifie la valeur d’identifiant de licence du document protégé par une stratégie (spécifiez la valeur renvoyée par la propriété `DocumentSecurityServiceService` de `getLicenseId` ).
      * Un membre de données statique de la variable `Reason` Permet d’indiquer le motif de révocation du document. Par exemple, vous pouvez spécifier `Reason.DOCUMENT_REVISED`.
      * A `string` qui spécifie l’emplacement URL vers lequel se trouve un document modifié. Si vous ne souhaitez pas rediriger un utilisateur vers une autre URL, vous pouvez transmettre `null`.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Révocation d’un document à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Révocation d’un document à l’aide de l’API de service Web&quot;

**Voir également**

[Suppression de stratégies de documents Word](protecting-documents-policies.md#removing-policies-from-word-documents)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Rétablissement de l’accès aux documents révoqués {#reinstating-access-to-revoked-documents}

Vous pouvez rétablir l’accès à un document de PDF révoqué, ce qui rend toutes les copies du document révoqué accessibles aux utilisateurs. Lorsqu’un utilisateur ouvre un document restauré qui a été révoqué, il peut afficher le document.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-6}

Pour rétablir l’accès à un document de PDF révoqué, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Récupérez l’identifiant de licence du document de PDF révoqué.
1. Rétablissez l’accès au document du PDF révoqué.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, vous devez créer un objet client de service Document Security. Si vous utilisez l’API Java, créez une `DocumentSecurityClient` . Si vous utilisez l’API du service Web Document Security, créez une `DocumentSecurityServiceService` .

**Récupération de l’identifiant de licence du document du PDF révoqué**

Vous devez récupérer l’identifiant de licence du document de PDF révoqué pour rétablir un document de PDF révoqué. Après avoir obtenu la valeur d’identifiant de licence, vous pouvez rétablir un document révoqué. Si vous tentez de rétablir un document qui n’est pas révoqué, vous allez provoquer une exception.

**Rétablissement de l’accès au document du PDF révoqué**

Pour rétablir l’accès à un document de PDF révoqué, vous devez spécifier l’identifiant de licence du document révoqué. Si vous tentez de rétablir l’accès à un document de PDF qui n’est pas révoqué, une exception est générée.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Application de stratégies à des documents PDF](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Révocation de l’accès aux documents](protecting-documents-policies.md#revoking-access-to-documents)

### Rétablissement de l’accès aux documents révoqués à l’aide de l’API Java {#reinstate-access-to-revoked-documents-using-the-java-api}

Rétablissez l’accès à un document révoqué à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `DocumentSecurityClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez l’identifiant de licence du document de PDF révoqué.

   * Créez un `java.io.FileInputStream` qui représente le document du PDF révoqué en utilisant son constructeur et en transmettant une valeur string spécifiant l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 
   * Créez un `DocumentManager` en appelant le `DocumentSecurityClient` de `getDocumentManager` .
   * Récupérez la valeur de l’identifiant de licence du document révoqué en appelant la fonction `DocumentManager` de `getLicenseId` et transmission de la méthode `com.adobe.idp.Document` qui représente le document révoqué. Cette méthode renvoie une valeur string qui représente l’identifiant de licence.

1. Rétablissez l’accès au document du PDF révoqué.

   * Créez un `LicenseManager` en appelant le `DocumentSecurityClient` de `getLicenseManager` .
   * Rétablissez l’accès au document du PDF révoqué en appelant la méthode `LicenseManager` de `unrevokeLicense` et transmission de la valeur d’identifiant de licence du document révoqué.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (mode SOAP) : Rétablissement de l’accès à un document révoqué à l’aide de l’API de service Web&quot;

### Rétablissement de l’accès aux documents révoqués à l’aide de l’API de service Web {#reinstate-access-to-revoked-documents-using-the-web-service-api}

Rétablissez l’accès à un document révoqué à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `DocumentSecurityServiceClient` en utilisant son constructeur par défaut.
   * Créez un `DocumentSecurityServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `DocumentSecurityServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupérez l’identifiant de licence du document de PDF révoqué.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document de PDF révoqué dans lequel l’accès est rétabli.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF révoqué et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Populate the `BLOB` object by assigning its `MTOM` field with the contents of the byte array.

1. Rétablissez l’accès au document du PDF révoqué.

   * Récupérez la valeur de l’identifiant de licence du document révoqué en appelant la fonction `DocumentSecurityServiceClient` de `getLicenseID` et transmission de la méthode `BLOB` qui représente le document révoqué. Cette méthode renvoie une valeur string qui représente l’identifiant de licence.
   * Rétablissez l’accès au document du PDF révoqué en appelant la méthode `DocumentSecurityServiceClient` de `unrevokeLicense` et transmission d’une valeur string qui spécifie la valeur d’identifiant de licence du document de PDF révoqué (transmettez la valeur de retour de la fonction `DocumentSecurityServiceClient` de `getLicenseId` ).

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* “Quick Start (MTOM): Reinstating access to a revoked document using the web service API”
* “Quick Start (SwaRef): Reinstating access to a revoked document using the web service API”

**Voir également**

[Invoking AEM Forms using MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Invoking AEM Forms using SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Inspection des documents de PDF protégés par une stratégie {#inspecting-policy-protected-pdf-documents}

Vous pouvez utiliser l’API Document Security Service (Java et service Web) pour inspecter les documents de PDF protégés par une stratégie. L’inspection des documents de PDF protégés par une stratégie renvoie des informations sur le document de PDF protégé par une stratégie. Vous pouvez, par exemple, déterminer la stratégie utilisée pour protéger le document et la date à laquelle le document a été protégé.

Vous ne pouvez pas effectuer cette tâche si votre version de LiveCycle est 8.x ou une version antérieure. La prise en charge de l’inspection des documents protégés par une stratégie est ajoutée dans AEM Forms. Si vous tentez d’inspecter un document protégé par une stratégie à l’aide de LiveCycle 8.x (ou d’une version antérieure), une exception est générée.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-7}

Pour inspecter un document de PDF protégé par une stratégie, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Récupérez un document protégé par une stratégie à inspecter.
1. Obtention d’informations sur le document protégé par une stratégie.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, créez un objet client de service Document Security. Si vous utilisez l’API Java, créez une `RightsManagementClient` . Si vous utilisez l’API du service Web Document Security, créez une `RightsManagementServiceService` .

**Récupération d’un document protégé par une stratégie à inspecter**

Pour inspecter un document protégé par une stratégie, récupérez-le. Si vous tentez d’inspecter un document non protégé par une stratégie ou révoqué, une exception est générée.

**Inspect du document**

Après avoir récupéré un document protégé par une stratégie, vous pouvez l’inspecter.

**Obtention d’informations sur le document protégé par une stratégie**

Après avoir inspecté un document de PDF protégé par une stratégie, vous pouvez obtenir des informations à son sujet. Vous pouvez, par exemple, déterminer la stratégie utilisée pour protéger le document.

Si vous sécurisez un document avec une stratégie qui appartient à Mes stratégies, puis appelez `RMInspectResult.getPolicysetName` ou `RMInspectResult.getPolicysetId`, la valeur null est renvoyée.

Si le document est protégé à l’aide d’une stratégie contenue dans un jeu de stratégies (autre que Mes stratégies), `RMInspectResult.getPolicysetName` et `RMInspectResult.getPolicysetId` renvoient des chaînes valides.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Documents PDF protégés par une stratégie Inspect à l’aide de l’API Java {#inspect-policy-protected-pdf-documents-using-the-java-api}

Inspect est un document de PDF protégé par une stratégie à l’aide de l’API Document Security Service (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java. Pour plus d’informations sur l’emplacement de ces fichiers, voir [Inclusion des fichiers de bibliothèque Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion. (Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Créez un objet `RightsManagementClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez un document protégé par une stratégie à inspecter.

   * Créez un `java.io.FileInputStream` qui représente le document de PDF protégé par une stratégie à l’aide de son constructeur. Transmettez une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Inspect le document.

   * Créez un `DocumentManager` en appelant le `RightsManagementClient` de `getDocumentManager` .
   * Inspect du document protégé par une stratégie en appelant la méthode `LicenseManager` de `inspectDocument` . Transmettez la variable `com.adobe.idp.Document` contenant le document de PDF protégé par une stratégie. Cette méthode renvoie une `RMInspectResult` contenant des informations sur le document protégé par une stratégie.

1. Obtention d’informations sur le document protégé par une stratégie.

   Pour obtenir des informations sur le document protégé par une stratégie, appelez la méthode appropriée qui appartient. `RMInspectResult` . Par exemple, pour récupérer le nom de la stratégie, appelez la méthode `RMInspectResult` de `getPolicyName` .

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (mode SOAP) : Inspection des documents de PDF protégés par une stratégie à l’aide de l’API Java&quot;

### Documents PDF protégés par une stratégie Inspect à l’aide de l’API de service Web {#inspect-policy-protected-pdf-documents-using-the-web-service-api}

Inspect est un document de PDF protégé par une stratégie à l’aide de l’API Document Security Service (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `RightsManagementServiceClient` en utilisant son constructeur par défaut.
   * Créez un `RightsManagementServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `RightsManagementServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupérez un document protégé par une stratégie à inspecter.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document de PDF à inspecter.
   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Inspect le document.

   Inspect du document protégé par une stratégie en appelant la méthode `RightsManagementServiceClient` de `inspectDocument` . Transmettez la variable `BLOB` contenant le document de PDF protégé par une stratégie. Cette méthode renvoie une `RMInspectResult` contenant des informations sur le document protégé par une stratégie.

1. Obtention d’informations sur le document protégé par une stratégie.

   Pour obtenir des informations sur le document protégé par une stratégie, obtenez la valeur du champ approprié qui appartient à la variable `RMInspectResult` . Par exemple, pour récupérer le nom de la stratégie, obtenez la valeur de la variable `RMInspectResult` de `policyName` champ .

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Inspection des documents de PDF protégés par une stratégie à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Inspection des documents de PDF protégés par une stratégie à l’aide de l’API de service Web&quot;

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Création de filigranes {#creating-watermarks}

Les filigranes permettent d’assurer la sécurité d’un document en identifiant de manière unique le document et en contrôlant la violation du droit d’auteur. Par exemple, vous pouvez créer et placer un filigrane qui indique Confidentiel sur toutes les pages d’un document. Une fois un filigrane créé, vous pouvez l’inclure dans une stratégie. En d’autres termes, vous pouvez définir l’attribut de filigrane de la stratégie avec le nouveau filigrane. Une fois qu’une stratégie contenant un filigrane est appliquée à un document, le filigrane apparaît dans le document protégé par une stratégie.

>[!NOTE]
>
>Seuls les utilisateurs disposant de droits d’administrateur Document Security peuvent créer des filigranes. En d’autres termes, vous devez spécifier cet utilisateur lors de la définition des paramètres de connexion requis pour créer un objet client de service Document Security.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-8}

Pour créer un filigrane, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Définissez les attributs des filigranes.
1. Enregistrez le filigrane avec le service Document Security.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, vous devez créer un objet client de service Document Security. Si vous utilisez l’API Java, créez une `RightsManagementClient` . Si vous utilisez l’API du service Web Document Security, créez une `RightsManagementServiceService` .

**Définition des attributs de filigranes**

Pour créer un filigrane, vous devez définir les attributs du filigrane. L’attribut name doit toujours être défini. Outre l’attribut name , vous devez définir au moins l’un des attributs suivants :

* Texte personnalisé
* DateIncluded
* UserIdIncluded
* UserNameIncluded

Le tableau suivant répertorie les paires clé-valeur requises lors de la création d’un filigrane à l’aide des services Web.

<table> 
 <thead> 
  <tr> 
   <th><p>Nom de la clé</p></th> 
   <th><p>Description</p></th> 
   <th><p>Valeur</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p><code>WaterBackCmd:IS_USERNAME_ENABLED</code></p></td> 
   <td><p>Indique si le nom d’utilisateur de l’utilisateur qui ouvre le document fait partie du filigrane.</p></td> 
   <td><p>True ou false</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_USERID_ENABLED</code></p></td> 
   <td><p>Indique si l’identification de l’utilisateur ouvrant le document fait partie du filigrane.</p></td> 
   <td><p>True ou false</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_CURRENTDATE_ENABLED</code></p></td> 
   <td><p>Indique si la date actuelle fait partie du filigrane.</p></td> 
   <td><p>True ou false</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code></p></td> 
   <td><p>Si cette valeur est définie sur true, la valeur du texte personnalisé doit être spécifiée à l’aide de <code>WaterBackCmd:SRCTEXT</code>.</p></td> 
   <td><p>True ou false</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:OPACITY</code></p></td> 
   <td><p>Indique l’opacité du filigrane. La valeur par défaut est 0,5 si elle n’est pas spécifiée.</p></td> 
   <td><p>Valeur comprise entre 0,0 et 1,0.</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:ROTATION</code></p></td> 
   <td><p>Indique la rotation du filigrane. La valeur par défaut est 0 degré.</p></td> 
   <td><p>Valeur comprise entre 0 et 359.</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:SCALE</code></p></td> 
   <td><p>Si cette valeur est spécifiée, <code>WaterBackCmd:IS_SIZE_ENABLED</code> doit être présente et la valeur doit être true. Si cet attribut n’est pas spécifié, le comportement par défaut est adapté à la page.</p></td> 
   <td><p>Valeur supérieure à 0.0 et inférieure ou égale à 1.0.</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:HORIZ_ALIGN</code></p></td> 
   <td><p>Indique l’alignement horizontal du filigrane. La valeur par défaut est center.</p></td> 
   <td><p>gauche, centre ou droite</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:VERT_ALIGN</code></p></td> 
   <td><p>Indique l’alignement vertical du filigrane. La valeur par défaut est center.</p></td> 
   <td><p>haut, centre ou bas</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_USE_BACKGROUND</code></p></td> 
   <td><p>Indique si le filigrane est en arrière-plan. La valeur par défaut est false. </p></td> 
   <td><p>True ou false</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_SIZE_ENABLED</code></p></td> 
   <td><p>True si une échelle personnalisée est spécifiée. Si cette valeur est définie sur true, SCALE doit également être spécifié. Si cette valeur est définie sur false, la valeur par défaut est adaptée à la page.</p></td> 
   <td><p>True ou false</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:SRCTEXT</code></p></td> 
   <td><p>Indique le texte personnalisé d’un filigrane. Si cette valeur est présente, alors <code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code> doit également être présent et défini sur true.</p></td> 
   <td><p>True ou false</p></td> 
  </tr> 
 </tbody> 
</table>

L’un des attributs suivants doit être défini pour tous les filigranes :

* `WaterBackCmd:IS_USERNAME_ENABLED`
* `WaterBackCmd:IS_USERID_ENABLED`
* `WaterBackCmd:IS_CURRENTDATE_ENABLED`
* `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`

Tous les autres attributs sont facultatifs.

**Enregistrement du filigrane**

Un nouveau filigrane doit être enregistré auprès du service Document Security pour pouvoir être utilisé. Après avoir enregistré un filigrane, vous pouvez l’utiliser dans les stratégies.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Application de stratégies à des documents PDF](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Création de filigranes à l’aide de l’API Java {#create-watermarks-using-the-java-api}

Créez un filigrane à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Inclure les fichiers JAR client, tels que `adobe-rightsmanagement-client.jar`, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `RightsManagementClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Définition des attributs de filigrane

   * Créez un `Watermark` en appelant le `InfomodelObjectFactory` statique de l’objet `createWatermark` . Cette méthode renvoie une `Watermark` .
   * Définissez l’attribut name du filigrane en appelant la fonction `Watermark` de `setName` et transmission d’une valeur string qui spécifie le nom de la stratégie.
   * Définissez l’attribut d’arrière-plan du filigrane en appelant la fonction `Watermark` de `setBackground` méthode et transmission `true`. En définissant cet attribut, le filigrane apparaît en arrière-plan du document.
   * Définissez l’attribut de texte personnalisé du filigrane en appelant la fonction `Watermark` de `setCustomText` et transmission d’une valeur string qui représente le texte du filigrane.
   * Définissez l’attribut d’opacité du filigrane en appelant la variable `Watermark` de `setOpacity` et transmettre une valeur entière qui spécifie le niveau d’opacité. Une valeur de 100 indique que le filigrane est complètement opaque et une valeur de 0 indique que le filigrane est complètement transparent.

1. Enregistrez le filigrane.

   * Créez un `WatermarkManager` en appelant le `RightsManagementClient` de `getWatermarkManager` . Cette méthode renvoie une `WatermarkManager` .
   * Enregistrez le filigrane en appelant la méthode `WatermarkManager` de `registerWatermark` et transmission de la méthode `Watermark` qui représente le filigrane à enregistrer. Cette méthode renvoie une valeur string qui représente la valeur d’identification du filigrane.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (mode SOAP) : Création d’un filigrane à l’aide de l’API Java&quot;

### Création de filigranes à l’aide de l’API de service Web {#create-watermarks-using-the-web-service-api}

Créez un filigrane à l’aide de l’API Document Security (service Web) :

1. Créez un objet API Client Document Security.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `RightsManagementServiceClient` en utilisant son constructeur par défaut.
   * Créez un `RightsManagementServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `RightsManagementServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Définissez les attributs du filigrane.

   * Créez un `WatermarkSpec` en appelant le `WatermarkSpec` constructeur.
   * Définissez le nom du filigrane en attribuant une valeur de chaîne à la variable `WatermarkSpec` de `name` membre de données.
   * Définir le de `id` en attribuant une valeur de chaîne à la variable `WatermarkSpec` de `id` membre de données.
   * Pour chaque propriété de filigrane à définir, créez une propriété distincte. `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Définissez la valeur de clé en attribuant une valeur à la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` membre de données (par exemple, `WaterBackCmd:OPACITY)`.
   * Définissez la valeur en attribuant une valeur à la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` membre de données (par exemple, `.25`).
   * Créez un `MyArrayOf_xsd_anyType` . Pour chaque `MyMapOf_xsd_string_To_xsd_anyType_Item` , appelez l’objet `MyArrayOf_xsd_anyType` de `Add` . Transmettez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Attribuez le `MyArrayOf_xsd_anyType` vers l’objet `WatermarkSpec` de `values` membre de données.

1. Enregistrez le filigrane.

   Enregistrez le filigrane en appelant la méthode `RightsManagementServiceClient` de `registerWatermark` et transmission de la méthode `WatermarkSpec` qui représente le filigrane à enregistrer.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Création d’un filigrane à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Création d’un filigrane à l’aide de l’API de service Web&quot;

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Modification des filigranes {#modifying-watermarks}

Vous pouvez modifier un filigrane existant à l’aide de l’API Java Document Security ou de l’API de service Web. Pour apporter des modifications à un filigrane existant, vous devez le récupérer, modifier ses attributs, puis le mettre à jour sur le serveur. Supposons, par exemple, que vous récupériez un filigrane et que vous modifiiez son attribut d’opacité. Avant que la modification ne prenne effet, vous devez mettre à jour le filigrane.

Lorsque vous modifiez un filigrane, la modification a un impact sur les documents futurs auxquels le filigrane est appliqué. En d’autres termes, les documents de PDF existants qui contiennent le filigrane ne sont pas affectés.

>[!NOTE]
>
>Seuls les utilisateurs disposant de droits d’administrateur Document Security peuvent modifier les filigranes. En d’autres termes, vous devez spécifier cet utilisateur lors de la définition des paramètres de connexion requis pour créer un objet client de service Document Security.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-9}

Pour modifier un filigrane, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Récupérez le filigrane à modifier.
1. Définissez les attributs des filigranes.
1. Mettez à jour le filigrane.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, vous devez créer un objet client de service Document Security. Si vous utilisez l’API Java, créez une `DocumentSecurityClient` . Si vous utilisez l’API du service Web Document Security, créez une `DocumentSecurityServiceService` .

**Récupération du filigrane à modifier**

Pour modifier un filigrane, vous devez récupérer un filigrane existant. Vous pouvez récupérer un filigrane en spécifiant son nom ou sa valeur d’identifiant.

**Définition des attributs de filigranes**

Pour modifier un filigrane existant, modifiez la valeur d’un ou de plusieurs attributs de filigrane. Lors de la mise à jour par programmation d’un filigrane à l’aide d’un service Web, vous devez définir tous les attributs qui ont été définis à l’origine, même si la valeur ne change pas. Supposons, par exemple, que les attributs de filigrane suivants soient définis : `WaterBackCmd:IS_USERID_ENABLED`, `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`, `WaterBackCmd:OPACITY`, et `WaterBackCmd:SRCTEXT`. Bien que le seul attribut que vous souhaitez modifier soit `WaterBackCmd:OPACITY`, vous devez définir les autres valeurs qui conviennent.

>[!NOTE]
>
>Lorsque vous utilisez l’API Java pour modifier un filigrane, vous n’avez pas besoin de spécifier tous les attributs. Définissez l’attribut de filigrane à modifier.

>[!NOTE]
>
>Pour plus d’informations sur les noms d’attributs du filigrane, voir [Création de filigranes](protecting-documents-policies.md#creating-watermarks).

**Mise à jour du filigrane**

Après avoir modifié les attributs d’un filigrane, vous devez le mettre à jour.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Création de filigranes](protecting-documents-policies.md#creating-watermarks)

### Modification des filigranes à l’aide de l’API Java {#modify-watermarks-using-the-java-api}

Modifiez un filigrane à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `DocumentSecurityClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez le filigrane à modifier.

   Créez un `WatermarkManager` en appelant le `DocumentSecurityClient` de `getWatermarkManager` et transmettez une valeur string qui spécifie le nom du filigrane. Cette méthode renvoie une `Watermark` qui représente le filigrane à modifier.

1. Définissez les attributs du filigrane.

   Définissez l’attribut d’opacité du filigrane en appelant la variable `Watermark` de `setOpacity` et transmettre une valeur entière qui spécifie le niveau d’opacité. Une valeur de 100 indique que le filigrane est complètement opaque et une valeur de 0 indique que le filigrane est complètement transparent.

   >[!NOTE]
   >
   >Cet exemple ne modifie que l’attribut opacity.

1. Mettez à jour le filigrane.

   * Mettez à jour le filigrane en appelant la méthode `WatermarkManager` de `updateWatermark` et transmettez la méthode `Watermark` dont l’attribut a été modifié.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous à la section Démarrage rapide (mode SOAP) : Modification d’un filigrane à l’aide de la section API Java .

### Modification des filigranes à l’aide de l’API de service Web {#modify-watermarks-using-the-web-service-api}

Modifiez un filigrane à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `DocumentSecurityServiceClient` en utilisant son constructeur par défaut.
   * Créez un `RightsManagementServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `DocumentSecurityServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupérez le filigrane à modifier.

   Récupérez le filigrane à modifier en appelant la fonction `DocumentSecurityServiceClient` de `getWatermarkByName` . Transmettez une valeur string qui spécifie le nom du filigrane. Cette méthode renvoie une `WatermarkSpec` qui représente le filigrane à modifier.

1. Définissez les attributs du filigrane.

   * Pour chaque propriété de filigrane à mettre à jour, créez une `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Définissez la valeur de clé en attribuant une valeur à la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` de `key` membre de données (par exemple, `WaterBackCmd:OPACITY)`.
   * Définissez la valeur en attribuant une valeur à la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` de `value` membre de données (par exemple, `.50`).
   * Créez un `MyArrayOf_xsd_anyType` . Pour chaque `MyMapOf_xsd_string_To_xsd_anyType_Item` , appelez l’objet `MyArrayOf_xsd_anyType` de `Add` . Transmettez la variable `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Attribuez le `MyArrayOf_xsd_anyType` vers l’objet `WatermarkSpec` de `values` membre de données.

1. Mettez à jour le filigrane.

   Mettez à jour le filigrane en appelant la méthode `DocumentSecurityServiceClient` de `updateWatermark` et transmission de la méthode `WatermarkSpec` qui représente le filigrane à modifier.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous au didacticiel de mise en route suivant :

* &quot;Démarrage rapide (MTOM) : Modification d’un filigrane à l’aide de l’API de service Web&quot;

## Recherche d’événements {#searching-for-events}

Le service Rights Management effectue le suivi d’actions spécifiques au fur et à mesure qu’elles se produisent, telles que l’application d’une stratégie à un document, l’ouverture d’un document protégé par une stratégie et la révocation de l’accès aux documents. Le contrôle des événements doit être activé pour le service de Rights Management ou les événements ne sont pas suivis.

Les événements appartiennent à l’une des catégories suivantes :

* Les événements d’administrateur sont des actions liées à un administrateur, comme la création d’un compte administrateur.
* Les événements de document sont des actions liées à un document, telles que la fermeture d’un document protégé par une stratégie.
* Les événements de stratégie sont des actions liées à une stratégie, comme la création d’une stratégie.
* Les événements de service sont des actions liées au service Rights Management, telles que la synchronisation avec l’annuaire d’utilisateurs.

Vous pouvez rechercher des événements spécifiques à l’aide de l’API Java Rights Management ou de l’API de service Web. En recherchant des événements, vous pouvez effectuer des tâches, comme créer un fichier journal de certains événements.

>[!NOTE]
>
>Pour plus d’informations sur le service Rights Management, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-10}

Pour rechercher un événement de Rights Management, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API client Rights Management.
1. Indiquez l’événement pour lequel effectuer la recherche.
1. Recherchez l’événement .

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Rights Management**

Avant de pouvoir effectuer par programmation une opération de service Rights Management, vous devez créer un objet client de service Rights Management. Si vous utilisez l’API Java, créez une `DocumentSecurityClient` . Si vous utilisez l’API du service Web de Rights Management, créez une `DocumentSecurityServiceService` .

**Définition des événements à rechercher**

Vous devez spécifier l’événement à rechercher. Vous pouvez, par exemple, rechercher l’événement de création de stratégie qui se produit lors de la création d’une stratégie.

**Recherche de l’événement**

Après avoir spécifié l’événement à rechercher, vous pouvez utiliser l’API Java du Rights Management ou l’API du service Web du Rights Management pour rechercher l’événement.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Recherche d’événements à l’aide de l’API Java {#search-for-events-using-the-java-api}

Recherchez des événements à l’aide de l’API du Rights Management (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Rights Management

   Créez un `DocumentSecurityClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Définition des événements à rechercher

   * Créez un `EventManager` en appelant le `DocumentSecurityClient` de `getEventManager` . Cette méthode renvoie une `EventManager` .
   * Créez un `EventSearchFilter` en appelant son constructeur.
   * Indiquez l’événement pour lequel effectuer une recherche en appelant la variable `EventSearchFilter` de `setEventCode` et transmission d’un membre de données statique qui appartient à la méthode `EventManager` qui représente l’événement pour lequel effectuer une recherche. Par exemple, pour rechercher l’événement de création de stratégie, transmettez `EventManager.POLICY_CREATE_EVENT`.

   >[!NOTE]
   >
   >Vous pouvez définir des critères de recherche supplémentaires en appelant `EventSearchFilter` méthodes d’objet . Par exemple, appelez la fonction `setUserName` pour spécifier un utilisateur associé à l’événement.

1. Recherche de l’événement

   Recherchez l’événement en appelant la fonction `EventManager` de `searchForEvents` et transmission de la méthode `EventSearchFilter` qui définit les critères de recherche d’événement. Cette méthode renvoie un tableau de `Event` objets.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Rights Management, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (SOAP) : Recherche d’événements à l’aide de l’API Java&quot;

### Recherche d’événements à l’aide de l’API de service Web {#search-for-events-using-the-web-service-api}

Recherchez des événements à l’aide de l’API du Rights Management (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un objet API client Rights Management

   * Créez un `DocumentSecurityServiceClient` en utilisant son constructeur par défaut.
   * Créez un `DocumentSecurityServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `DocumentSecurityServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Définition des événements à rechercher

   * Créez un `EventSpec` en utilisant son constructeur.
   * Spécifiez le début de la période au cours de laquelle l’événement s’est produit en définissant la variable `EventSpec` de `firstTime.date` membre de données avec `DataTime` qui représente le début de la période au cours de laquelle l’événement s’est produit.
   * Attribuer la valeur `true` au `EventSpec` de `firstTime.dateSpecified` membre de données.
   * Indiquez la fin de la période au cours de laquelle l’événement s’est produit en définissant la variable `EventSpec` de `lastTime.date` membre de données avec `DataTime` qui représente la fin de la période au cours de laquelle l’événement s’est produit.
   * Attribuer la valeur `true` au `EventSpec` de `lastTime.dateSpecified` membre de données.
   * Définissez l’événement à rechercher en attribuant une valeur de chaîne à la variable `EventSpec` de `eventCode` membre de données. Le tableau suivant répertorie les valeurs numériques que vous pouvez attribuer à cette propriété :

   <table> 
    <thead> 
    <tr> 
    <th><p>Type d’événement</p></th> 
    <th><p>Valeur</p></th> 
    </tr> 
    </thead> 
    <tbody>
    <tr> 
    <td><p><code>ALL_EVENTS</code></p></td> 
    <td><p>999</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_CHANGE_PASSWORD_EVENT</code></p></td> 
    <td><p>1000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_REGISTER_EVENT</code></p></td> 
    <td><p>1001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_PREREGISTER_EVENT</code></p></td> 
    <td><p>1002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_ACTIVATE_EVENT</code></p></td> 
    <td><p>1003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_DEACTIVATE_EVENT</code></p></td> 
    <td><p>1004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_AUTHENTICATE_EVENT</code></p></td> 
    <td><p>1005</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_AUTHENTICATE_DENY_EVENT </code></p></td> 
    <td><p>1006</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_ACCOUNT_LOCK_EVENT</code></p></td> 
    <td><p>1007</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_DELETE_EVENT </code></p></td> 
    <td><p>1008</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_UPDATE_PROFILE_EVENT </code></p></td> 
    <td><p>1009</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_VIEW_EVENT </code></p></td> 
    <td><p>2000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_PRINT_LOW_EVENT </code></p></td> 
    <td><p>2001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_PRINT_HIGH_EVENT </code></p></td> 
    <td><p>2002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_SIGN_EVENT </code></p></td> 
    <td><p>2003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_ADD_ANNOTATION_EVENT </code></p></td> 
    <td><p>2004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_FORM_FILL_EVENT </code></p></td> 
    <td><p>2005</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_CLOSE_EVENT </code></p></td> 
    <td><p>2006</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_MODIFY_EVENT </code></p></td> 
    <td><p>2007</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_CHANGE_SECURITY_HANDLER_EVENT </code></p></td> 
    <td><p>2008</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_SWITCH_POLICY_EVENT </code></p></td> 
    <td><p>2009</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_REVOKE_EVENT </code></p></td> 
    <td><p>2010</p></td> 
    </tr> 
    <tr> 
    <td><p><code>$1</code></p></td> 
    <td><p>2011</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_SECURE_EVENT </code></p></td> 
    <td><p>2012</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_UNKNOWN_CLIENT_EVENT </code></p></td> 
    <td><p>2013</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_CHANGE_REVOKE_URL_EVENT </code></p></td> 
    <td><p>2014</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_CHANGE_EVENT </code></p></td> 
    <td><p>3000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_ENABLE_EVENT </code></p></td> 
    <td><p>3001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_DISABLE_EVENT </code></p></td> 
    <td><p>3002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_CREATE_EVENT </code></p></td> 
    <td><p>3003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_DELETE_EVENT </code></p></td> 
    <td><p>3004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_CHANGE_OWNER_EVENT </code></p></td> 
    <td><p>3005</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_CLIENT_SYNC_EVENT </code></p></td> 
    <td><p>4 000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_SYNC_DIR_INFO_EVENT </code></p></td> 
    <td><p>4001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_SYNC_DIR_COMPLETE_EVENT </code></p></td> 
    <td><p>4002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_VERSION_MISMATCH_EVENT </code></p></td> 
    <td><p>4003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_CONFIG_CHANGE_EVENT </code></p></td> 
    <td><p>4004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_ENABLE_OFFLINE_ACCESS_EVENT </code></p></td> 
    <td><p>4005</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_ADD_EVENT </code></p></td> 
    <td><p>5 000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_DELETE_EVENT </code></p></td> 
    <td><p>5001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_EDIT_EVENT </code></p></td> 
    <td><p>5002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_ACTIVATE_EVENT </code></p></td> 
    <td><p>5003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_DEACTIVATE_EVENT </code></p></td> 
    <td><p>5004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ERROR_DIRECTORY_SERVICE_EVENT </code></p></td> 
    <td><p>6 000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>CREATED_POLICYSET_EVENT</code></p></td> 
    <td><p>7000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DELETED_POLICYSET_EVENT</code></p></td> 
    <td><p>7001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>MODIFIED_POLICYSET_EVENT</code></p></td> 
    <td><p>7002</p></td> 
    </tr> 
    </tbody> 
    </table>

1. Recherche de l’événement

   Recherchez l’événement en appelant la fonction `DocumentSecurityServiceClient` de `searchForEvents` et transmission de la méthode `EventSpec` qui représente l’événement pour lequel effectuer une recherche et le nombre maximal de résultats. Cette méthode renvoie une `MyArrayOf_xsd_anyType` collection où chaque élément est une `AuditSpec` instance. Utilisation d’une `AuditSpec` vous pouvez obtenir des informations sur l’événement, telles que l’heure à laquelle il s’est produit. Le `AuditSpec` contient une instance `timestamp` membre de données qui spécifie ces informations.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Rights Management, reportez-vous aux didacticiels de mise en route suivants :

* &quot;Démarrage rapide (MTOM) : Recherche d’événements à l’aide de l’API de service Web&quot;
* &quot;Démarrage rapide (SwaRef) : Recherche d’événements à l’aide de l’API de service Web&quot;

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Application de stratégies à des documents Word {#applying-policies-to-word-documents}

Outre les documents PDF, le service Rights Management prend en charge d’autres formats de document, tels qu’un document Word Microsoft (fichier DOC) et d’autres formats de fichier Microsoft Office. Par exemple, vous pouvez appliquer une stratégie à un document Word afin de le protéger. En appliquant une stratégie à un document Word, vous restreignez l’accès au document. Vous ne pouvez pas appliquer de stratégie à un document si celui-ci est déjà protégé par une stratégie.

Vous pouvez surveiller l’utilisation d’un document Word protégé par une stratégie après sa distribution. C’est-à-dire, vous pouvez voir comment le document est utilisé et qui l’utilise. Par exemple, vous pouvez savoir quand un utilisateur a ouvert le document.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-11}

Pour appliquer une stratégie à un document Word, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Client Document Security.
1. Récupérez un document Word auquel une stratégie est appliquée.
1. Appliquez une stratégie existante au document Word.
1. Enregistrez le document Word protégé par une stratégie.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, vous devez créer un objet client de service Document Security.

**Récupération d’un document Word**

Pour appliquer une stratégie, vous devez récupérer un document Word. Une fois que vous avez appliqué une stratégie au document Word, les utilisateurs sont restreints lors de l’utilisation du document. Par exemple, si la stratégie ne permet pas l’ouverture du document hors ligne, les utilisateurs doivent être en ligne pour ouvrir le document.

**Application d’une stratégie existante au document Word**

Pour appliquer une stratégie à un document Word, vous devez référencer une stratégie existante et spécifier à quel jeu de stratégies elle appartient. L’utilisateur qui définit les propriétés de connexion doit avoir accès à la stratégie spécifiée. Dans le cas contraire, une exception se produit.

**Enregistrement du document Word**

Une fois que le service Document Security a appliqué une stratégie à un document Word, vous pouvez enregistrer le document Word protégé par une stratégie en tant que fichier DOC.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Révocation de l’accès aux documents](protecting-documents-policies.md#revoking-access-to-documents)

### Application d’une stratégie à un document Word à l’aide de l’API Java {#apply-a-policy-to-a-word-document-using-the-java-api}

Appliquez une stratégie à un document Word à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet API Client Document Security.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `DocumentSecurityClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez un document Word.

   * Créez un `java.io.FileInputStream` qui représente le document Word en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document Word.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Appliquez une stratégie existante au document Word.

   * Créez un `DocumentManager` en appelant le `DocumentSecurityClient` de `getDocumentManager` .
   * Appliquez une stratégie au document Word en appelant la méthode `DocumentManager` de `protectDocument` et transmission des valeurs suivantes :

      * Le `com.adobe.idp.Document` contenant le document Word auquel s’applique la stratégie.
      * Une valeur string qui spécifie le nom du document.
      * Une valeur string qui spécifie le nom du jeu de stratégies auquel appartient la stratégie. Vous pouvez définir une `null` qui entraîne la valeur `MyPolicies` jeu de stratégies utilisé.
      * Une valeur string qui spécifie le nom de la stratégie.
      * Une valeur string qui représente le nom du domaine User Manager de l’utilisateur qui est l’éditeur du document. Cette valeur de paramètre est facultative et peut être nulle (si ce paramètre est nul, la valeur de paramètre suivante doit être nulle).
      * Une valeur string qui représente le nom canonique de l’utilisateur du gestionnaire de l’utilisateur qui est l’éditeur du document. Cette valeur de paramètre est facultative et peut être `null` (si ce paramètre est `null`, alors la valeur du paramètre précédent doit être `null`).
      * A `com.adobe.livecycle.rightsmanagement.Locale` qui représente le paramètre régional utilisé pour sélectionner le modèle MS Office. Cette valeur de paramètre est facultative et vous pouvez spécifier `null`.

      Le `protectDocument` renvoie une `RMSecureDocumentResult` contenant le document Word protégé par une stratégie.


1. Enregistrez le document Word.

   * Appeler la variable `RMSecureDocumentResult` de `getProtectedDoc` pour obtenir le document Word protégé par une stratégie. Cette méthode renvoie une `com.adobe.idp.Document` .
   * Créez un `java.io.File` et assurez-vous que l’extension de fichier est DOC.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `getProtectedDoc` ).

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous au didacticiel de mise en route suivant :

* &quot;Démarrage rapide (mode SOAP) : Application d’une stratégie à un document Word à l’aide de l’API Java&quot;

### Application d’une stratégie à un document Word à l’aide de l’API de service Web {#apply-a-policy-to-a-word-document-using-the-web-service-api}

Appliquez une stratégie à un document Word à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/DocumentSecurityService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet API Client Document Security.

   * Créez un `DocumentSecurityServiceClient` en utilisant son constructeur par défaut.
   * Créez un `DocumentSecurityServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `DocumentSecurityServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupérez un document Word.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document Word auquel une stratégie est appliquée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document Word et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Déterminez la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Appliquez une stratégie existante au document Word.

   Appliquez une stratégie au document Word en appelant la méthode `DocumentSecurityServiceClient` de `protectDocument` et transmission des valeurs suivantes :

   * Le `BLOB` contenant le document Word auquel s’applique la stratégie.
   * Une valeur string qui spécifie le nom du document.
   * Une valeur string qui spécifie le nom du jeu de stratégies auquel appartient la stratégie. Vous pouvez définir une `null` qui entraîne la valeur `MyPolicies` jeu de stratégies utilisé.
   * Une valeur string qui spécifie le nom de la stratégie.
   * Une valeur string qui représente le nom du domaine User Manager de l’utilisateur qui est l’éditeur du document. Cette valeur de paramètre est facultative et peut être nulle (si ce paramètre est nul, la valeur de paramètre suivante doit être `null`).
   * Une valeur string qui représente le nom canonique de l’utilisateur du gestionnaire de l’utilisateur qui est l’éditeur du document. Cette valeur de paramètre est facultative et peut être nulle (si ce paramètre est nul, la valeur du paramètre précédent doit être `null`).
   * A `RMLocale` qui spécifie la valeur du paramètre régional (par exemple, `RMLocale.en`).
   * Paramètre de sortie string utilisé pour stocker la valeur de l’identifiant de stratégie.
   * Paramètre de sortie string utilisé pour stocker la valeur d’identifiant protégée par une stratégie.
   * Un paramètre de sortie string utilisé pour stocker le type MIME (par exemple, `application/doc`).

   Le `protectDocument` renvoie une `BLOB` contenant le document Word protégé par une stratégie.

1. Enregistrez le document Word.

   * Create a `System.IO.FileStream` object by invoking its constructor and passing a string value that represents the file location of the policy-protected Word document.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `protectDocument` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier Word en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous au didacticiel de mise en route suivant :

* “Quick Start (MTOM): Applying a policy to a Word document using the web service API ”

## Suppression de stratégies de documents Word {#removing-policies-from-word-documents}

Vous pouvez supprimer une stratégie d’un document Word protégé par une stratégie afin de supprimer la protection du document. That is, if you no longer want the document to be protected by a policy. If you want to update a policy-protected Word document with a newer policy, then instead of removing the policy and adding the updated policy, it is more efficient to switch the policy.

>[!NOTE]
>
>Pour plus d’informations sur le service Document Security, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-12}

Pour supprimer une stratégie d’un document Word protégé par une stratégie, procédez comme suit :

1. Inclure les fichiers de projet
1. Créez un objet API Client Document Security.
1. Récupérez un document Word protégé par une stratégie.
1. Supprimez la stratégie du document Word.
1. Enregistrez le document Word non sécurisé.s

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Document Security**

Avant d’effectuer par programmation une opération de service Document Security, créez un objet client de service Document Security.

**Récupération d’un document Word protégé par une stratégie**

Pour supprimer une stratégie, vous devez récupérer un document Word protégé par une stratégie. Si vous tentez de supprimer une stratégie d’un document Word qui n’est pas protégé par une stratégie, une exception est générée.

**Suppression de la stratégie du document Word**

Vous pouvez supprimer une stratégie d’un document Word protégé par une stratégie à condition qu’un administrateur soit spécifié dans les paramètres de connexion. Dans le cas contraire, la stratégie utilisée pour protéger un document doit contenir la variable `SWITCH_POLICY` pour supprimer une stratégie d’un document Word. En outre, l’utilisateur spécifié dans les paramètres de connexion AEM Forms doit également disposer de cette autorisation. Dans le cas contraire, une exception est générée.

**Enregistrement du document Word non sécurisé**

Une fois que le service Document Security a supprimé une stratégie d’un document Word, vous pouvez enregistrer le document Word non sécurisé en tant que fichier DOC.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Application de stratégies à des documents Word](protecting-documents-policies.md#applying-policies-to-word-documents)

### Suppression d’une stratégie d’un document Word à l’aide de l’API Java {#remove-a-policy-from-a-word-document-using-the-java-api}

Supprimez une stratégie d’un document Word protégé par une stratégie à l’aide de l’API Document Security (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-rightsmanagement-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Document Security

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `RightsManagementClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupération d’un document Word protégé par une stratégie

   * Créez un `java.io.FileInputStream` qui représente le document Word protégé par une stratégie en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document Word.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Suppression de la stratégie du document Word

   * Créez un `DocumentManager` en appelant le `RightsManagementClient` de `getDocumentManager` .
   * Supprimez une stratégie du document Word en appelant la méthode `DocumentManager` de `removeSecurity` et transmission de la méthode `com.adobe.idp.Document` contenant le document Word protégé par une stratégie. Cette méthode renvoie une `com.adobe.idp.Document` contenant un document Word non sécurisé.

1. Enregistrement du document Word non sécurisé

   * Créez un `java.io.File` et assurez-vous que l’extension de fichier est DOC.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `removeSecurity` ).

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous au didacticiel de mise en route suivant :

* &quot;Démarrage rapide (mode SOAP) : Suppression d’une stratégie d’un document Word à l’aide de l’API Java&quot;

### Suppression d’une stratégie d’un document Word à l’aide de l’API de service Web {#remove-a-policy-from-a-word-document-using-the-web-service-api}

Supprimez une stratégie d’un document Word protégé par une stratégie à l’aide de l’API Document Security (service Web) :

1. Inclure les fichiers de projet

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Création d’un objet API client Document Security

   * Créez un `RightsManagementServiceClient` en utilisant son constructeur par défaut.
   * Créez un `RightsManagementServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Vous n’avez pas besoin d’utiliser la variable `lc_version` attribut. Cet attribut est utilisé lorsque vous créez une référence de service.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `RightsManagementServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.


1. Récupération d’un document Word protégé par une stratégie

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document Word protégé par une stratégie à partir duquel la stratégie est supprimée.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document Word et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Suppression de la stratégie du document Word

   Supprimez la stratégie du document Word en appelant la méthode `RightsManagementServiceClient` de `removePolicySecurity` et transmission de la méthode `BLOB` contenant le document Word protégé par une stratégie. Cette méthode renvoie une `BLOB` contenant un document Word non sécurisé.

1. Enregistrement du document Word non sécurisé

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document Word non sécurisé.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `removePolicySecurity` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` champ .
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .

**Exemples de code**

Pour obtenir des exemples de code à l’aide du service Document Security, reportez-vous au didacticiel de mise en route suivant :

* &quot;Démarrage rapide (MTOM) : Suppression d’une stratégie d’un document Word à l’aide de l’API de service Web&quot;

**Voir également**

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
