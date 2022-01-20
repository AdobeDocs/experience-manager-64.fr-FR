---
title: Attribution des droits d’utilisation
seo-title: Assigning Usage Rights
description: Utilisez l’API client Java d’Acrobat Reader DC Extensions et l’API de service Web pour appliquer et supprimer des droits d’utilisation des documents du PDF.
seo-description: Use the Acrobat Reader DC extensions Java Client API and Web Service API to apply and remove usage rights from PDF documents.
uuid: 8c2020df-ea3c-49fa-916f-38a458f40d2b
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9e8db506-9ace-4e1f-8a7b-c4e9b15dde7e
role: Developer
exl-id: c7805d8a-eb6a-4908-9662-936920ffa67a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '3912'
ht-degree: 7%

---

# Attribution des droits d’utilisation {#assigning-usage-rights}

## À propos du service des extensions Acrobat Reader DC {#about-the-acrobat-reader-dc-extensions-service}

Le service d’extensions Acrobat Reader DC permet à votre entreprise de partager facilement des documents de PDF interactifs en étendant les fonctionnalités d’Adobe Reader. Le service d’extensions Acrobat Reader DC prend entièrement en charge tout document de PDF, y compris PDF 1.7. Il fonctionne avec Adobe Reader 7.0 et versions ultérieures. Le service ajoute des droits d’utilisation à un document de PDF, activant des fonctionnalités qui ne sont généralement pas disponibles lorsqu’un document de PDF est ouvert à l’aide d’Adobe Reader. Les utilisateurs tiers n’ont pas besoin de logiciels ou de modules externes supplémentaires pour travailler avec les documents dont les droits sont activés.

Vous pouvez accomplir ces tâches à l’aide du service d’extensions Acrobat Reader DC :

* Appliquez des droits d’utilisation aux documents de PDF. Pour plus d’informations, voir [Application des droits d’utilisation aux documents du PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).
* Supprimez les droits d’utilisation des documents de PDF. Pour plus d’informations, voir [Suppression des droits d’utilisation des documents de PDF](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).
* Récupérez les informations d’identification. Pour plus d’informations, voir [Récupération des informations d’identification](assigning-usage-rights.md#retrieving-credential-information).

>[!NOTE]
>
>Pour plus d’informations sur le service d’extensions Acrobat Reader DC, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Application des droits d’utilisation aux documents du PDF {#applying-usage-rights-to-pdf-documents}

Vous pouvez appliquer des droits d’utilisation aux documents de PDF à l’aide de l’API client Java Acrobat Reader DC extensions et du service Web. Les droits d’utilisation appartiennent à la fonctionnalité disponible par défaut dans Acrobat mais non dans Adobe Reader, telle que la capacité à ajouter des commentaires à un formulaire ou à remplir des champs de formulaire et enregistrer ce dernier. Les documents PDF dotés de droits d’utilisation sont appelés des documents dont les droits sont activés. Un utilisateur qui ouvre un document dont les droits sont activés dans Adobe Reader peut effectuer les opérations autorisées pour ce document spécifique.

>[!NOTE]
>
>Lors de l’application de droits d’utilisation aux documents de PDF à l’aide de la variable `applyUsageRights` , qui fait partie de l’API Java, vous pouvez définir la variable `isModeFinal` du paramètre `ReaderExtensionsOptionSpec` vers `false`. Le compteur de formulaires traités n’est alors pas mis à jour et les performances s’en trouvent améliorées. Si la mise à jour du compteur de formulaires ne vous préoccupe pas, il est recommandé de définir la variable `isModeFinal` du paramètre `false`.

>[!NOTE]
>
>Pour plus d’informations sur le service d’extensions Acrobat Reader DC, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour appliquer des droits d’utilisation à un document de PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet Client d’extensions Acrobat Reader DC.
1. Récupérez un document de PDF.
1. Spécifiez les droits d’utilisation à appliquer.
1. Appliquez des droits d’utilisation au document du PDF.
1. Enregistrez le document de PDF dont les droits sont activés.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet client d’extensions Acrobat Reader DC**

Pour effectuer par programmation une opération de service d’extension Acrobat Reader DC, vous devez créer un objet client de service Acrobat Reader DC Extensions. Si vous utilisez l’API Java des extensions Acrobat Reader DC, créez une `ReaderExtensionsServiceClient` . Si vous utilisez l’API du service Web des extensions Acrobat Reader DC, créez une `ReaderExtensionsServiceService` .

**Récupération d’un document de PDF**

Vous devez récupérer un document de PDF pour appliquer des droits d’utilisation. Les documents de PDF dont les droits sont activés contiennent un dictionnaire de droits d’utilisation. Lorsqu’Adobe Reader ouvre un document contenant un tel dictionnaire, il active uniquement les droits d’utilisation spécifiés dans le dictionnaire pour ce document. Si le document ne contient pas de dictionnaire des droits d’utilisation, le service d’extensions Acrobat Reader DC en crée un. S’il contient déjà un dictionnaire, le service d’extensions Acrobat Reader DC remplace les droits d’utilisation existants par ceux que vous spécifiez. Le dictionnaire spécifie les droits d’utilisation activés. Lorsqu’un utilisateur ouvre le document dans Adobe Reader, seuls les droits d’utilisation spécifiés dans le dictionnaire sont autorisés.

**Spécification des droits d’utilisation à appliquer**

Les droits d’utilisation que vous pouvez définir sont déterminés par des informations d’identification que vous achetez à Adobe Systems Incorporated. Les informations d’identification permettent généralement de définir un groupe de droits d’utilisation associés, tels que ceux relatifs aux formulaires interactifs. Chaque information d’identification permet de créer un certain nombre de documents de PDF dont les droits sont activés. Les informations d’identification d’évaluation permettent de créer un nombre illimité de brouillons de documents.

>[!NOTE]
>
>Si vous tentez d’attribuer un droit d’utilisation non autorisé par vos informations d’identification, vous déclencherez une exception.

**Application des droits d’utilisation au document du PDF**

Pour appliquer des droits d’utilisation à un document de PDF, vous référencez l’alias des informations d’identification que vous utilisez pour appliquer des droits d’utilisation (les informations d’identification sont généralement installées lors de l’installation d’AEM Forms). Vous devez également spécifier le document du PDF auquel des droits d’utilisation sont appliqués. Pour plus d’informations sur la configuration d’informations d’identification, consultez le guide d’installation et de déploiement de votre serveur d’applications.

**Enregistrer le document du PDF dont les droits sont activés**

Une fois que le service d’extensions Acrobat Reader DC a appliqué des droits d’utilisation à un document de PDF, vous pouvez enregistrer le document de PDF dont les droits sont activés en tant que fichier de PDF.

**Voir également**

[Application des droits d’utilisation à l’aide de l’API Java](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Application des droits d’utilisation à l’aide de l’API de service Web](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API du service d’extensions Acrobat Reader DC](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Application des droits d’utilisation à l’aide de l’API Java {#apply-usage-rights-using-the-java-api}

Appliquez des droits d’utilisation à un document de PDF à l’aide de l’API Acrobat Reader DC Extensions (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-reader-extensions-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet Client d’extensions Acrobat Reader DC.

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `ReaderExtensionsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Récupérez un document de PDF.

   * Créez un `java.io.FileInputStream` qui représente le document du PDF en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Spécifiez les droits d’utilisation à appliquer.

   * Créez un `UsageRights` qui représente les droits d’utilisation à l’aide de son constructeur.
   * Pour chaque droit d’utilisation à appliquer, appelez une méthode correspondante qui appartient à la propriété `UsageRights` . Par exemple, pour ajouter la variable `enableFormFillIn` droit d’utilisation, appelez la fonction `UsageRights` de `enableFormFillIn` méthode et transmission `true`. (Répétez cette étape pour chaque droit d’utilisation à appliquer).

1. Appliquez des droits d’utilisation au document du PDF.

   * Créez un objet `ReaderExtensionsOptionSpec` en utilisant son constructeur. Cet objet contient des options d’exécution requises par le service d’extensions Acrobat Reader DC. Lors de l’appel de ce constructeur, vous devez spécifier les valeurs suivantes :

      * Le `UsageRights` contenant les droits d’utilisation à appliquer au document.
      * Une valeur string qui spécifie un message visible par un utilisateur lorsqu’un document de PDF avec droits activés est ouvert dans Adobe Reader 7.x. Ce message ne s’affiche pas dans Adobe Reader 8.0.
   * Appliquez des droits d’utilisation au document du PDF en appelant la méthode `ReaderExtensionsServiceClient` de `applyUsageRights` et transmission des valeurs suivantes :

      * Le `com.adobe.idp.Document` contenant le document du PDF auquel des droits d’utilisation sont appliqués.
      * Une valeur string qui spécifie l’alias des informations d’identification qui vous permettent d’appliquer des droits d’utilisation.
      * Valeur string qui spécifie la valeur du mot de passe correspondant. (Actuellement, ce paramètre est ignoré. Vous pouvez transmettre `null`.)
   * Le `ReaderExtensionsOptionSpec` contenant les options d’exécution.

   Le `applyUsageRights` renvoie une `com.adobe.idp.Document` contenant le document de PDF dont les droits sont activés.

1. Enregistrez le document de PDF dont les droits sont activés.

   * Créez un objet `java.io.File` et assurez-vous que l’extension du fichier est .pdf.
   * Appeler la variable `com.adobe.idp.Document` de `copyToFile` pour copier le contenu de la méthode `com.adobe.idp.Document` dans le fichier (assurez-vous d’utiliser la variable `com.adobe.idp.Document` qui a été renvoyé par l’objet `applyUsageRights` ).

**Voir également**

[Application des droits d’utilisation aux documents du PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Démarrage rapide (mode SOAP) : application des droits d’utilisation à l’aide de l’API Java](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Application des droits d’utilisation à l’aide de l’API de service Web {#apply-usage-rights-using-the-web-service-api}

Appliquez des droits d’utilisation à un document de PDF à l’aide de l’API Acrobat Reader DC Extensions (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet Client d’extensions Acrobat Reader DC.

   * Créez un `ReaderExtensionsServiceClient` en utilisant son constructeur par défaut.
   * Créez un `ReaderExtensionsServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Assurez-vous de spécifier `?blob=mtom`.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `ReaderExtensionsServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Récupérez un document de PDF.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document de PDF auquel des droits d’utilisation sont appliqués.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` . Transmettez le tableau d’octets, la position de départ et la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Spécifiez les droits d’utilisation à appliquer.

   * Créez un `UsageRights` qui représente les droits d’utilisation à l’aide de son constructeur.
   * Pour chaque droit d’utilisation à appliquer, affectez la valeur `true` au membre de données correspondant qui appartient à la variable `UsageRights` . Par exemple, pour ajouter la variable `enableFormFillIn` droit d’utilisation, affecter `true` au `UsageRights` de `enableFormFillIn` membre de données. (Répétez cette étape pour chaque droit d’utilisation à appliquer).

1. Appliquez des droits d’utilisation au document du PDF.

   * Créez un objet `ReaderExtensionsOptionSpec` en utilisant son constructeur. Cet objet contient des options d’exécution requises par le service d’extensions Acrobat Reader DC.
   * Attribuez le `UsageRights` vers l’objet `ReaderExtensionsOptionSpec` de `usageRights` membre de données.
   * Attribuez une valeur string qui spécifie le message qu’un utilisateur voit lorsqu’un document de PDF dont les droits sont activés est ouvert dans Adobe Reader au `ReaderExtensionsOptionSpec` de `message` membre de données.
   * Appliquez des droits d’utilisation au document du PDF en appelant la méthode `ReaderExtensionsServiceClient` de `applyUsageRights` et transmission des valeurs suivantes :

      * Le `BLOB` contenant le document du PDF auquel des droits d’utilisation sont appliqués.
      * Une valeur string qui spécifie l’alias des informations d’identification qui vous permettent d’appliquer des droits d’utilisation.
      * Valeur string qui spécifie la valeur du mot de passe correspondant. (Actuellement, ce paramètre est ignoré. Vous pouvez transmettre `null`.)
   * Le `ReaderExtensionsOptionSpec` contenant les options d’exécution.

   Le `applyUsageRights` renvoie une `BLOB` contenant le document de PDF dont les droits sont activés.

1. Enregistrez le document de PDF dont les droits sont activés.

   * Créez un `System.IO.FileStream` en appelant son constructeur. Transmettez une valeur string qui représente l’emplacement du fichier du document du PDF dont les droits sont activés.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `applyUsageRights` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .
   * Ecrivez le contenu du tableau d’octets dans un fichier de PDF en appelant la méthode `System.IO.BinaryWriter` de `Write` et transmission du tableau d’octets.

**Voir également**

[Application des droits d’utilisation aux documents du PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Suppression des droits d’utilisation des documents de PDF {#removing-usage-rights-from-pdf-documents}

Vous pouvez supprimer des droits d’utilisation d’un document dont les droits sont activés. La suppression des droits d’utilisation d’un document de PDF dont les droits sont activés est également nécessaire pour effectuer d’autres opérations AEM Forms sur celui-ci. Vous devez par exemple signer numériquement (ou certifier) un document PDF avant de définir ses droits d’utilisation. Par conséquent, si vous souhaitez effectuer des opérations sur un document dont les droits sont activés, vous devez supprimer les droits d’utilisation du document du PDF, effectuer les autres opérations, telles que la signature numérique du document, puis réappliquer les droits d’utilisation au document.

>[!NOTE]
>
>Pour plus d’informations sur le service d’extensions Acrobat Reader DC, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-1}

Pour supprimer des droits d’utilisation d’un document de PDF dont les droits sont activés, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet Client d’extensions Acrobat Reader DC.
1. Récupérez un document de PDF dont les droits sont activés.
1. Supprimez les droits d’utilisation du document du PDF.
1. Enregistrez le document du PDF.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet client d’extensions Acrobat Reader DC**

Avant d’effectuer par programmation une opération de service d’extensions Acrobat Reader DC, vous devez créer un objet client de service d’extensions Acrobat Reader DC. Si vous utilisez l’API Java, créez une `ReaderExtensionsServiceClient` . Si vous utilisez l’API du service Web des extensions Acrobat Reader DC, créez une `ReaderExtensionsServiceService` .

**Récupération d’un document de PDF dont les droits sont activés**

Récupérez un document de PDF dont les droits sont activés afin de supprimer les droits d’utilisation.

**Suppression des droits d’utilisation du document du PDF**

Après avoir récupéré un document de PDF dont les droits sont activés, vous pouvez supprimer les droits d’utilisation. Une fois les droits d’utilisation supprimés, le document du PDF ne comporte aucune fonctionnalité supplémentaire lors de son affichage dans Adobe Reader.

**Enregistrement du document du PDF**

Vous pouvez enregistrer le document du PDF qui ne contient plus les droits d’utilisation en tant que fichier du PDF. Une fois enregistré en tant que fichier de PDF, le document de PDF peut être affiché dans Adobe Reader ou Acrobat.

**Voir également**

[Suppression des droits d’utilisation à l’aide de l’API Java](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Suppression des droits d’utilisation à l’aide de l’API de service Web](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API du service d’extensions Acrobat Reader DC](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Application des droits d’utilisation aux documents du PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Suppression des droits d’utilisation à l’aide de l’API Java {#remove-usage-rights-using-the-java-api}

Supprimez les droits d’utilisation d’un document de PDF dont les droits sont activés à l’aide de l’API Acrobat Reader DC extensions (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-reader-extensions-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet Client d’extensions Acrobat Reader DC.

   Créez un `ReaderExtensionsServiceClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Récupérez un document de PDF.

   * Créez un `java.io.FileInputStream` qui représentent le document du PDF dont les droits sont activés en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Supprimez les droits d’utilisation du document du PDF.

   Supprimez les droits d’utilisation du document du PDF en appelant la méthode `ReaderExtensionsServiceClient` de `removeUsageRights` et transmission de la méthode `com.adobe.idp.Document` contenant le document de PDF dont les droits sont activés. Cette méthode renvoie une `com.adobe.idp.Document` qui contient un document PDF ne disposant pas de droits d’utilisation.

1. Appliquez des droits d’utilisation au document du PDF.

   * Créez un `java.io.File` et assurez-vous que l’extension de fichier est .PDF.
   * Appeler la variable `Document` de `copyToFile` pour copier le contenu de la méthode `Document` dans le fichier (assurez-vous d’utiliser la variable `Document` qui a été renvoyé par l’objet `removeUsageRights` ).

**Voir également**

[Suppression des droits d’utilisation des documents de PDF](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Démarrage rapide (mode SOAP) : Suppression des droits d’utilisation d’un document de PDF à l’aide de l’API Java](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Suppression des droits d’utilisation à l’aide de l’API de service Web {#remove-usage-rights-using-the-web-service-api}

Supprimez les droits d’utilisation d’un document de PDF dont les droits sont activés à l’aide de l’API des extensions Acrobat Reader DC (service Web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet Client d’extensions Acrobat Reader DC.

   * Créez un `ReaderExtensionsServiceClient` en utilisant son constructeur par défaut.
   * Créez un `ReaderExtensionsServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Assurez-vous de spécifier `?blob=mtom`.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `ReaderExtensionsServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Récupérez un document de PDF.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker le document du PDF dont les droits sont activés et à partir duquel les droits d’utilisation sont supprimés.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document du PDF et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Supprimez les droits d’utilisation du document du PDF.

   Supprimez les droits d’utilisation du document du PDF en appelant la méthode `ReaderExtensionsServiceClient` de `removeUsageRights` et transmission de la méthode `BLOB` contenant le document de PDF dont les droits sont activés. Cette méthode renvoie une `BLOB` qui contient un document PDF ne disposant pas de droits d’utilisation.

1. Appliquez des droits d’utilisation au document du PDF.

   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du PDF.
   * Créez un tableau d’octets qui stocke le contenu des données de la variable `BLOB` qui a été renvoyé par l’objet `removeUsageRights` . Renseignez le tableau d’octets en obtenant la valeur de la variable `BLOB` de `MTOM` membre de données.
   * Créez un `System.IO.BinaryWriter` en appelant son constructeur et en transmettant l’objet `System.IO.FileStream` .

**Voir également**

[Suppression des droits d’utilisation des documents de PDF](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Récupération des informations d’identification {#retrieving-credential-information}

Vous pouvez récupérer des informations sur les informations d’identification utilisées pour appliquer des droits d’utilisation à un document de PDF dont les droits sont activés. En récupérant des informations sur les informations d’identification, vous pouvez obtenir des informations telles que la date à laquelle le certificat n’est plus valide.

>[!NOTE]
>
>Pour plus d’informations sur le service d’extensions Acrobat Reader DC, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary_of_steps-2}

Pour récupérer des informations sur les informations d’identification utilisées pour appliquer des droits d’utilisation à un document de PDF, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet Client d’extensions Acrobat Reader DC.
1. Récupérez un document de PDF dont les droits sont activés.
1. Récupérez des informations sur les informations d’identification.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet client d’extensions Acrobat Reader DC**

Avant d’effectuer par programmation une opération de service d’extensions Acrobat Reader DC, vous devez créer un objet client de service d’extensions Acrobat Reader DC. Si vous utilisez l’API Java, créez une `ReaderExtensionsServiceClient` . Si vous utilisez l’API du service Web des extensions Acrobat Reader DC, créez une `ReaderExtensionsServiceService` .

**Récupération d’un document de PDF dont les droits sont activés**

Pour récupérer des informations sur les informations d’identification, vous devez récupérer un document de PDF dont les droits sont activés. Vous pouvez également récupérer des informations sur une information d’identification en spécifiant son alias ; toutefois, si vous souhaitez récupérer des informations sur des informations d’identification qui ont été utilisées pour appliquer des droits d’utilisation à un document de PDF spécifique dont les droits sont activés, vous devez récupérer le document.

**Récupération d’informations sur les informations d’identification**

Après avoir récupéré un document de PDF dont les droits sont activés, vous pouvez obtenir des informations sur les informations d’identification qui ont été utilisées pour lui appliquer des droits d’utilisation. Vous pouvez obtenir les informations d’identification suivantes :

* Message affiché dans Adobe Reader à l’ouverture du document PDF dont les droits sont activés.
* Date à laquelle les informations d’identification ne sont plus valides.
* Date avant laquelle les informations d’identification ne sont pas valides.
* Droits d’utilisation définis pour ce document de PDF dont les droits sont activés.
* Nombre d’utilisations des informations d’identification.

**Voir également**

[Suppression des droits d’utilisation à l’aide de l’API Java](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Suppression des droits d’utilisation à l’aide de l’API de service Web](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API du service d’extensions Acrobat Reader DC](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Récupération des informations d’identification à l’aide de l’API Java {#retrieve-credential-information-using-the-java-api}

Récupérez les informations d’identification à l’aide de l’API des extensions Acrobat Reader DC (Java) :

1. Inclure les fichiers de projet.

   Incluez les fichiers JAR client, tels que adobe-reader-extensions-client.jar, dans le chemin de classe de votre projet Java.

1. Créez un objet Client d’extensions Acrobat Reader DC.

   Créez un `ReaderExtensionsServiceClient` en utilisant son constructeur et en transmettant un objet `ServiceClientFactory` contenant des propriétés de connexion.

1. Récupérez un document de PDF.

   * Créez un `java.io.FileInputStream` qui représentent le document du PDF dont les droits sont activés en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du document du PDF dont les droits sont activés.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Supprimez les droits d’utilisation du document du PDF.

   * Récupérez des informations sur les informations d’identification utilisées pour appliquer des droits d’utilisation au document du PDF en appelant la méthode `ReaderExtensionsServiceClient` de `getDocumentUsageRights` et transmission de la méthode `com.adobe.idp.Document` contenant le document de PDF dont les droits sont activés. Cette méthode renvoie une `GetUsageRightsResult` contenant des informations d’identification.
   * Récupérez la date à laquelle les informations d’identification ne sont plus valides en appelant la variable `GetUsageRightsResult` de `getNotAfter` . Cette méthode renvoie une `java.util.Date` qui représente la date à laquelle les informations d’identification ne sont plus valides.
   * Récupérez le message qui s’affiche dans Adobe Reader lorsque le document PDF dont les droits sont activés est ouvert en appelant la fonction `GetUsageRightsResult` de `getMessage` . Cette méthode renvoie une valeur string qui représente le message.

**Voir également**

[Récupération des informations d’identification](assigning-usage-rights.md#retrieving-credential-information)

[Démarrage rapide (mode SOAP) : Récupération des informations d’identification à l’aide de l’API Java](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Récupération des informations d’identification à l’aide de l’API de service Web {#retrieve-credential-information-using-the-web-service-api}

Récupérez les informations d’identification à l’aide de l’API des extensions Acrobat Reader DC (service web) :

1. Inclure les fichiers de projet.

   Créez un projet Microsoft .NET qui utilise MTOM. Assurez-vous d’utiliser la définition WSDL suivante : `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Remplacer `localhost` avec l’adresse IP du serveur hébergeant AEM Forms.

1. Créez un objet Client d’extensions Acrobat Reader DC.

   * Créez un `ReaderExtensionsServiceClient` en utilisant son constructeur par défaut.
   * Créez un `ReaderExtensionsServiceClient.Endpoint.Address` en utilisant l’objet `System.ServiceModel.EndpointAddress` constructeur. Transmettez une valeur string qui spécifie le WSDL au service AEM Forms (par exemple, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Assurez-vous de spécifier `?blob=mtom`.)
   * Créez un `System.ServiceModel.BasicHttpBinding` en obtenant la valeur de la variable `ReaderExtensionsServiceClient.Endpoint.Binding` champ . Convertissez la valeur de retour en `BasicHttpBinding`.
   * Définissez la variable `System.ServiceModel.BasicHttpBinding` de `MessageEncoding` champ à `WSMessageEncoding.Mtom`. Cette valeur garantit l’utilisation de MTOM.
   * Activez l’authentification HTTP de base en effectuant les tâches suivantes :

      * Attribuer le nom d’utilisateur AEM forms au champ `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Attribuer la valeur de mot de passe correspondante au champ `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Attribuer la valeur constante `HttpClientCredentialType.Basic` au champ `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Attribuer la valeur constante `BasicHttpSecurityMode.TransportCredentialOnly` au champ `BasicHttpBindingSecurity.Security.Mode`.

1. Récupérez un document de PDF.

   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` est utilisé pour stocker un document de PDF dont les droits sont activés.
   * Créez un `System.IO.FileStream` en appelant son constructeur et en transmettant une valeur string qui représente l’emplacement du fichier du document de PDF dont les droits sont activés et le mode d’ouverture du fichier.
   * Créez un tableau d’octets qui stocke le contenu de la variable `System.IO.FileStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `System.IO.FileStream` de `Length` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `System.IO.FileStream` de `Read` et transmission du tableau d’octets, de la position de départ et de la longueur du flux à lire.
   * Renseignez la variable `BLOB` en attribuant ses `MTOM` avec le contenu du tableau d’octets.

1. Supprimez les droits d’utilisation du document du PDF.

   * Récupérez des informations sur les informations d’identification utilisées pour appliquer des droits d’utilisation au document du PDF en appelant la méthode `ReaderExtensionsServiceClient` de `getDocumentUsageRights` et transmission de la méthode `com.adobe.idp.Document` contenant le document de PDF dont les droits sont activés. Cette méthode renvoie une `GetUsageRightsResult` contenant des informations d’identification.
   * Récupérez la date à laquelle les informations d’identification ne sont plus valides en obtenant la valeur de la variable `GetUsageRightsResult` de `notAfter` membre de données. Le type de données de ce membre de données est `System.DateTime`.
   * Récupérez le message qui s’affiche lorsque le document de PDF dont les droits sont activés est ouvert dans Adobe Reader en obtenant la valeur de la variable `GetUsageRightsResult` de `message` membre de données. Le type de données de ce membre de données est une chaîne.
   * Récupérez le nombre de fois où les informations d’identification sont utilisées en obtenant la valeur de la variable `GetUsageRightsResult` de `useCount` membre de données. Le type de données de ce membre de données est un entier.

**Voir également**

[Récupération des informations d’identification](assigning-usage-rights.md#retrieving-credential-information)

[Appel d’AEM Forms à l’aide de MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Appel d’AEM Forms à l’aide de SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
