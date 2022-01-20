---
title: Rendu de Forms compatible avec les droits
seo-title: Rendering Rights-Enabled Forms
description: Utilisez le service Forms pour effectuer le rendu des formulaires auxquels des droits d’utilisation sont appliqués. Vous pouvez générer des formulaires dont les droits sont activés à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Forms service to render forms that have usage rights applied to them. You can render rights-enabled forms using the Java API and Web Service API.
uuid: ce5e4be6-d9b0-4989-a0e1-a8c3b98aed77
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: d4c2b2f0-613a-409d-b39b-8e37fdb96eea
role: Developer
exl-id: 0cee94ba-1a72-4021-b606-8fa945312483
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1463'
ht-degree: 5%

---

# Rendu de Forms compatible avec les droits {#rendering-rights-enabled-forms}

Le service Forms peut effectuer le rendu des formulaires auxquels des droits d’utilisation sont appliqués. Les droits d’utilisation appartiennent à la fonctionnalité disponible par défaut dans Acrobat mais non dans Adobe Reader, telle que la capacité à ajouter des commentaires à un formulaire ou à remplir des champs de formulaire et enregistrer ce dernier. Les Forms auxquelles des droits d’utilisation sont appliqués sont appelées des formulaires dont les droits sont activés. Un utilisateur qui ouvre un formulaire dont les droits sont activés dans Adobe Reader peut effectuer les opérations activées pour ce formulaire.

Pour appliquer des droits d’utilisation à un formulaire, le service d’extensions Acrobat Reader DC doit faire partie de votre installation d’AEM forms. En outre, vous devez disposer d’informations d’identification valides qui vous permettent d’appliquer des droits d’utilisation aux documents de PDF. En d’autres termes, vous devez configurer correctement le service d’extensions Acrobat Reader DC avant de pouvoir générer un formulaire dont les droits sont activés. (Voir [À propos du service des extensions Acrobat Reader DC](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).)

>[!NOTE]
>
>Pour générer un formulaire contenant des droits d’utilisation, vous devez utiliser un fichier XDP comme entrée, et non un fichier PDF. Si vous utilisez un fichier de PDF comme entrée, le formulaire est toujours rendu ; cependant, il ne s’agira pas d’un formulaire dont les droits sont activés.

>[!NOTE]
>
>Vous ne pouvez pas préremplir un formulaire avec des données XML lorsque vous spécifiez les droits d’utilisation suivants : `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles`ou `enableDigitalSignatures`. (Voir [Préremplissage de Forms avec des dispositions souple](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Résumé des étapes {#summary-of-steps}

Pour effectuer le rendu d’un formulaire dont les droits sont activés, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un objet API client Forms.
1. Définissez les options d’exécution des droits d’utilisation.
1. Générer un formulaire dont les droits sont activés.
1. Ecrivez le formulaire dont les droits sont activés dans le navigateur web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Forms**

Avant d’effectuer par programmation une opération d’API client de service Forms, vous devez créer un client de service Forms.

**Définition des options d’exécution des droits d’utilisation**

Vous devez définir les options d’exécution des droits d’utilisation pour générer un formulaire dont les droits sont activés. Vous devez également spécifier l’alias des informations d’identification utilisées pour appliquer des droits d’utilisation à un formulaire. Après avoir défini la valeur d’alias, vous indiquez chaque droit d’utilisation à appliquer au formulaire.

**Rendu d’un formulaire dont les droits sont activés**

Pour générer un formulaire dont les droits sont activés, vous utilisez la même logique d’application que pour générer un formulaire sans droits d’utilisation. La seule différence est que vous devez vous assurer que les options d’exécution des droits d’utilisation sont incluses dans la logique de votre application.

>[!NOTE]
>
>Lors du rendu d’un formulaire dont les droits sont activés à l’aide de l’API du service Web Forms, vous ne pouvez pas joindre de fichiers au formulaire.

**Écrire le flux de données de formulaire dans le navigateur Web client**

Lorsque le service Forms génère un formulaire dont les droits sont activés, il renvoie un flux de données de formulaire que vous devez écrire dans le navigateur Web client. Une fois écrit dans le navigateur Web client, le formulaire est visible par l’utilisateur. Un utilisateur qui consulte le formulaire dont les droits sont activés dans Adobe Reader peut effectuer les opérations qui sont activées pour ce formulaire.

**Voir également**

[Rendu des formulaires activés pour les droits à l’aide de l’API Java](#render-rights-enabled-forms-using-the-java-api)

[Rendu de formulaires activés pour les droits à l’aide de l’API de service Web](#render-rights-enabled-forms-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendu des PDF forms interactifs](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendu des formulaires activés pour les droits à l’aide de l’API Java {#render-rights-enabled-forms-using-the-java-api}

Rendre un formulaire dont les droits sont activés à l’aide de l’API Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Définition des options d’exécution des droits d’utilisation

   * Créez un objet `ReaderExtensionSpec` en utilisant son constructeur.
   * Spécifiez l’alias des informations d’identification en appelant la fonction `ReaderExtensionSpec` de `setReCredentialAlias` et indiquez une valeur string qui représente la valeur d’alias.
   * Définissez les droits d’utilisation en appelant la méthode correspondante qui appartient à la propriété `ReaderExtensionSpec` . Cependant, vous ne pouvez définir un droit d’utilisation que si les informations d’identification que vous référencez vous permettent de le faire. En d’autres termes, vous ne pouvez pas définir un droit d’utilisation si les informations d’identification ne vous permettent pas de le définir. Par exemple. pour définir le droit d’utilisation qui permet à l’utilisateur de remplir des champs de formulaire et d’enregistrer le formulaire, appelez la méthode `ReaderExtensionSpec` de `setReFillIn` méthode et transmission `true`.

   >[!NOTE]
   >
   >Il n’est pas nécessaire d’appeler la variable `ReaderExtensionSpec` de `setReCredentialPassword`* . Cette méthode n’est pas utilisée par le service Forms. *

1. Rendu d’un formulaire dont les droits sont activés

   Appeler la variable `FormsServiceClient` de `renderPDFFormWithUsageRights` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * A `PDFFormRenderSpec` qui stocke les options d’exécution.
   * A `ReaderExtensionSpec` qui stocke les options d’exécution des droits d’utilisation.
   * A `URLSpec` contenant des valeurs URI requises par le service Forms.

   Le `renderPDFFormWithUsageRights` renvoie une `FormsResult` contenant un flux de données de formulaire qui doit être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Obtention du type de contenu de la variable `com.adobe.idp.Document` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `com.adobe.idp.Document` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets pour le remplir avec le flux de données de formulaire en appelant la fonction `InputStream` de `read` et transmission du tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Démarrage rapide (mode SOAP) : Rendu d’un formulaire dont les droits sont activés à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendu de formulaires activés pour les droits à l’aide de l’API de service Web {#render-rights-enabled-forms-using-the-web-service-api}

Rendre un formulaire dont les droits sont activés à l’aide de l’API Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API client Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Définition des options d’exécution des droits d’utilisation

   * Créez un objet `ReaderExtensionSpec` en utilisant son constructeur.
   * Spécifiez l’alias des informations d’identification en appelant la fonction `ReaderExtensionSpec` de `setReCredentialAlias` et indiquez une valeur string qui représente la valeur d’alias.
   * Définissez les droits d’utilisation en appelant la méthode correspondante qui appartient à la propriété `ReaderExtensionSpec` . Cependant, vous ne pouvez définir un droit d’utilisation que si les informations d’identification que vous référencez vous permettent de le faire. En d’autres termes, vous ne pouvez pas définir un droit d’utilisation si les informations d’identification ne vous permettent pas de le définir. Pour définir le droit d’utilisation qui permet à l’utilisateur de remplir des champs de formulaire et d’enregistrer le formulaire, appelez la méthode `ReaderExtensionSpec` de `setReFillIn` méthode et transmission `true`.

1. Rendu d’un formulaire dont les droits sont activés

   Appeler la variable `FormsService` de `renderPDFFormWithUsageRights` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données avec le formulaire, vous devez transmettre une `BLOB` basé sur une source de données XML vide. Vous ne pouvez pas transmettre une `BLOB` objet nul ; dans le cas contraire, une exception est générée.
   * A `PDFFormRenderSpec` qui stocke les options d’exécution.
   * A `ReaderExtensionSpec` qui stocke les options d’exécution des droits d’utilisation.
   * A `URLSpec` contenant des valeurs URI requises par le service Forms.

   Le `renderPDFFormWithUsageRights` renvoie une `FormsResult` contenant un flux de données de formulaire qui doit être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `BLOB` qui contient des données de formulaire en appelant la méthode `FormsResult` de `getOutputContent` .
   * Obtention du type de contenu de la variable `BLOB` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `BLOB` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un tableau d’octets et renseignez-le en appelant la variable `BLOB` de `getBinaryData` . Cette tâche affecte le contenu de la `FormsResult` vers le tableau d’octets.
   * Appeler la variable `javax.servlet.http.HttpServletResponse` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Rendu de Forms compatible avec les droits](#rendering-rights-enabled-forms)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
