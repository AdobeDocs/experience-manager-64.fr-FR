---
title: Rendu de Forms sur le client
seo-title: Rendering Forms at the Client
description: Optimisez la diffusion de contenu PDF et améliorez la capacité du service Forms à gérer la charge réseau à l’aide de la fonctionnalité de rendu côté client d’Acrobat ou d’Adobe Reader.
seo-description: Optimize the delivery of PDF content and improve the Forms service’s ability to handle network load by using the client-side rendering capability of Acrobat or Adobe Reader.
uuid: 09bcc23d-28b0-473a-87f1-bc17e87620f4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 08d36e9f-cafc-478e-9781-8fc29ac6262e
role: Developer
exl-id: 641452e6-bf7e-4af4-a4f9-6e5627db9fca
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1684'
ht-degree: 2%

---

# Rendu de Forms sur le client {#rendering-forms-at-the-client}

## Rendu de Forms sur le client {#rendering-forms-at-the-client-inner}

Vous pouvez optimiser la diffusion de contenu PDF et améliorer la capacité du service Forms à gérer la charge réseau à l’aide de la fonctionnalité de rendu côté client d’Acrobat ou d’Adobe Reader. Ce processus est connu sous le nom de rendu d’un formulaire au niveau du client. Pour effectuer le rendu d’un formulaire sur le client, le périphérique client (généralement un navigateur web) doit utiliser Acrobat 7.0 ou Adobe Reader 7.0 ou une version ultérieure.

Les modifications apportées à un formulaire résultant de l’exécution de script côté serveur ne sont pas répercutées dans un formulaire rendu sur le client, sauf si le sous-formulaire racine contient le paramètre `restoreState` qui est défini sur `auto`. Pour plus d’informations sur cet attribut, voir [Forms Designer.](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour générer un formulaire au niveau du client, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un objet API client Forms.
1. Définissez les options d’exécution du rendu client.
1. Effectuez le rendu d’un formulaire au niveau du client.
1. Ecrivez le formulaire dans le navigateur Web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Forms**

Avant d’effectuer par programmation une opération d’API client de service Forms, vous devez créer un client de service Forms. Si vous utilisez l’API Java, créez une `FormsServiceClient` . Si vous utilisez l’API du service Web Forms, créez une `FormsService` .

**Définition des options d’exécution du rendu client**

Vous devez définir l’option d’exécution de rendu client pour qu’un formulaire s’affiche sur le client en définissant la variable `RenderAtClient` option d’exécution sur `true`. Le formulaire est ainsi transmis au périphérique client où il est rendu. If `RenderAtClient` is `auto` (valeur par défaut), la conception de formulaire détermine si le formulaire est rendu au client. La conception de formulaire doit être une conception de formulaire avec une disposition souple.

Une option d’exécution facultative que vous pouvez définir est la `SeedPDF` . Le `SeedPDF` combine le conteneur du PDF (document du PDF de contrôle) avec la conception de formulaire et les données XML. La conception de formulaire et les données XML sont transmises à Acrobat ou à Adobe Reader, où le formulaire est rendu. Le `SeedPDF` peut être utilisée lorsque l’ordinateur client ne dispose pas de polices utilisées dans le formulaire, par exemple lorsqu’un utilisateur final n’est pas autorisé à utiliser une police que le propriétaire du formulaire est autorisé à utiliser.

Vous pouvez utiliser Designer pour créer un fichier de PDF dynamique simple à utiliser comme fichier de PDF de contrôle. Pour effectuer cette tâche, procédez comme suit :

1. Déterminez si vous devez incorporer des polices dans le fichier du PDF de contrôle. Le fichier du PDF de contrôle doit contenir les polices supplémentaires requises par le formulaire en cours de rendu. Lorsque vous incorporez des polices dans le fichier du PDF de contrôle, assurez-vous de ne pas enfreindre les accords de licence des polices. Dans Designer, vous pouvez déterminer si vous pouvez incorporer légalement des polices. Lors de l’enregistrement, si vous ne pouvez pas incorporer de polices dans le formulaire, Designer affiche un message répertoriant les polices que vous ne pouvez pas incorporer. Ce message ne s’affiche pas dans Designer pour les documents de PDF statiques.
1. Si vous créez le fichier du PDF de contrôle dans Designer, il est recommandé d’ajouter au minimum un champ de texte contenant un message. Le message doit être adressé aux utilisateurs des versions antérieures d’Adobe Reader en indiquant qu’ils ont besoin d’Acrobat 7.0 ou version ultérieure ou d’Adobe Reader 7.0 ou version ultérieure pour afficher le document.
1. Enregistrez le fichier du PDF de contrôle en tant que fichier de PDF dynamique avec l’extension de nom de fichier du PDF.

>[!NOTE]
>
>Vous n’avez pas besoin de définir l’option d’exécution du PDF de contrôle pour générer un formulaire sur le client. Si vous ne spécifiez pas de PDF de contrôle, le service Forms crée un shell pdf qui ne contiendra pas d’objets COS, mais contiendra un wrapper de PDF avec le contenu XDP réel incorporé à l’instance. Les étapes de cette section ne définissent pas l’option d’exécution du PDF de contrôle. Pour plus d’informations sur les objets COS, consultez le guide de référence d’Adobe PDF.

**Rendu d’un formulaire au niveau du client**

Pour effectuer le rendu d’un formulaire sur le client, vous devez vous assurer que les options d’exécution de rendu client sont incluses dans la logique de votre application pour générer un formulaire.

**Écrire le flux de données de formulaire dans le navigateur Web client**

Le service Forms crée un flux de données de formulaire que vous devez écrire dans le navigateur Web client. Lorsqu’il est écrit dans le navigateur Web client, le formulaire est rendu par Acrobat 7.0 ou Adobe Reader 7.0 ou version ultérieure et est visible par l’utilisateur.

**Voir également**

[Rendu d’un formulaire sur le client à l’aide de l’API Java](#render-a-form-at-the-client-using-the-java-api)

[Rendu d’un formulaire au client à l’aide de l’API du service Web](#render-a-form-at-the-client-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Transmission de documents au service Forms](/help/forms/developing/passing-documents-forms-service.md)

[Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendu d’un formulaire sur le client à l’aide de l’API Java {#render-a-form-at-the-client-using-the-java-api}

Rendre un formulaire au client à l’aide de l’API Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Définition des options d’exécution du rendu client

   * Créez un objet `PDFFormRenderSpec` en utilisant son constructeur.
   * Définissez la variable `RenderAtClient` l’option d’exécution en appelant la fonction `PDFFormRenderSpec` de `setRenderAtClient` et transmission de la valeur d’énumération `RenderAtClient.Yes`.

1. Rendu d’un formulaire au niveau du client

   Appeler la variable `FormsServiceClient` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application AEM Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * A `PDFFormRenderSpec` qui stocke les options d’exécution requises pour générer un formulaire au niveau du client.
   * A `URLSpec` qui contient des valeurs URI requises par le service Forms pour générer un formulaire.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

   Le `renderPDFForm` renvoie une `FormsResult` contenant un flux de données de formulaire qui doit être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Obtention du type de contenu de la variable `com.adobe.idp.Document` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `com.adobe.idp.Document` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets et renseignez-le avec le flux de données de formulaire en appelant la fonction `InputStream` de `read` et transmission du tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Démarrage rapide (mode SOAP) : Rendu d’un formulaire au niveau du client à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rendu d’un formulaire au client à l’aide de l’API du service Web {#render-a-form-at-the-client-using-the-web-service-api}

Rendre un formulaire au client à l’aide de l’API Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API client Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Définition des options d’exécution du rendu client

   * Créez un objet `PDFFormRenderSpec` en utilisant son constructeur.
   * Définissez la variable `RenderAtClient` l’option d’exécution en appelant la fonction `PDFFormRenderSpec` de `setRenderAtClient` et transmission de la valeur de chaîne `RenderAtClient.Yes`.

1. Rendu d’un formulaire au niveau du client

   Appeler la variable `FormsService` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez `null`. (Voir [Préremplissage de Forms avec des dispositions souple](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * A `PDFFormRenderSpec` qui stocke les options d’exécution requises pour générer un formulaire au niveau du client.
   * A `URLSpec` contenant des valeurs URI requises par le service Forms.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la méthode . Ce paramètre est utilisé pour stocker le formulaire de PDF rendu.
   * Une valeur vide `javax.xml.rpc.holders.LongHolder` qui est renseigné par la méthode . (Cet argument stocke le nombre de pages dans le formulaire).
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la méthode . (Cet argument stocke la valeur du paramètre régional).
   * Une valeur vide `com.adobe.idp.services.holders.FormsResultHolder` qui contiendra les résultats de cette opération.

   Le `renderPDFForm` renseigne la méthode `com.adobe.idp.services.holders.FormsResultHolder` qui est transmis en tant que dernière valeur d’argument avec un flux de données de formulaire qui doit être écrit dans le navigateur web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `FormResult` en obtenant la valeur de la variable `com.adobe.idp.services.holders.FormsResultHolder` de `value` membre de données.
   * Créez un `BLOB` qui contient des données de formulaire en appelant la méthode `FormsResult` de `getOutputContent` .
   * Obtention du type de contenu de la variable `BLOB` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `BLOB` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un tableau d’octets et renseignez-le en appelant la variable `BLOB` de `getBinaryData` . Cette tâche affecte le contenu de la `FormsResult` vers le tableau d’octets.
   * Appeler la variable `javax.servlet.http.HttpServletResponse` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Rendu de Forms sur le client](#rendering-forms-at-the-client)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
