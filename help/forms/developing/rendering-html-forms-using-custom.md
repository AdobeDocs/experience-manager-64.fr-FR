---
title: Rendu de Forms de HTML à l’aide de fichiers CSS personnalisés
seo-title: Rendering HTML Forms Using Custom CSS Files
description: Utilisez le service Forms pour faire référence à des fichiers CSS personnalisés afin d’effectuer le rendu de HTMLS en réponse à une requête HTTP d’un navigateur web. Vous pouvez générer un formulaire de HTML qui utilise un fichier CSS à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Forms service to refer to custom CSS files to render HTML forms in response to an HTTP request from a web browser. You can render an HTML form that uses a CSS file using the Java API and Web Service API.
uuid: a44e96f1-001d-48a2-8c96-15cb9d0c71b3
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 8fe7c072-7df0-44b7-92d0-bf39dc1e688a
role: Developer
exl-id: d10cbb97-1cec-4b1b-9104-48063e75a2cd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1674'
ht-degree: 2%

---

# Rendu de Forms de HTML à l’aide de fichiers CSS personnalisés {#rendering-html-forms-using-custom-css-files}

Le service Forms effectue le rendu des HTMLS en réponse à une requête HTTP d’un navigateur Web. Lors du rendu d’un formulaire de HTML, le service Forms peut référencer un fichier CSS personnalisé. Vous pouvez créer un fichier CSS personnalisé pour répondre aux besoins de votre entreprise et référencer ce fichier CSS lors de l’utilisation du service Forms pour le rendu des formulaires de HTML.

Le service Forms analyse silencieusement le fichier CSS personnalisé. En d’autres termes, le service Forms ne signale pas les erreurs qui peuvent se produire si le fichier CSS personnalisé ne respecte pas les normes CSS. Dans ce cas, le service Forms ignore le style et continue avec les styles restants situés dans le fichier CSS.

La liste suivante spécifie les styles pris en charge dans un fichier CSS personnalisé :

* **Paires de style sélecteur de niveau classe**: S’il est présent dans un fichier CSS personnalisé, les sélecteurs utilisés dans le formulaire de HTML en tant que styles de classe sont utilisés. Les styles de classe inutilisés sont ignorés.
* **Paires de type sélecteur de niveau d’identifiant**: Tous les styles d’identifiant sont utilisés s’ils sont utilisés dans le formulaire de HTML.
* **Paires de style de sélecteur de niveau élément**: Tous les styles d’élément sont utilisés s’ils sont utilisés dans le formulaire de HTML.
* **Priorité des styles**: La priorité du style (comme importante) est prise en charge et peut être utilisée dans un fichier CSS personnalisé.
* **Type de média**: Une ou plusieurs paires de style sélecteur peuvent être enveloppées dans le style @media pour définir le type de média. Le service Forms ne vérifie pas si le type de média spécifié est pris en charge. Le type de média spécifié dans le fichier CSS personnalisé est fusionné dans le formulaire de HTML.

Vous pouvez récupérer un exemple de fichier CSS à l’aide de l’application FormsIVS. Téléchargez le formulaire, sélectionnez-le dans la page Tester la conception de formulaire, puis cliquez sur Générer un CSS. Il n’est pas nécessaire de définir le type de transformation HTML avant de cliquer sur le bouton. Sélectionnez ensuite Enregistrer. Vous pouvez modifier ce fichier CSS pour répondre aux besoins de votre entreprise.

>[!NOTE]
>
>Avant de générer un formulaire de HTML qui utilise un fichier CSS personnalisé, il est important de bien comprendre le rendu des formulaires de HTML. (Voir [Rendu de Forms en tant que HTML](/help/forms/developing/rendering-forms-html.md).)

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Résumé des étapes {#summary-of-steps}

Pour effectuer le rendu d’un formulaire de HTML qui utilise un fichier CSS, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un objet API Java Forms.
1. Référencez le fichier CSS.
1. Générer un HTML de formulaire.
1. Ecrivez le flux de données de formulaire dans le navigateur Web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet API Java Forms**

Avant d’effectuer par programmation une opération prise en charge par le service Forms, vous devez créer un objet client Forms.

**Référence au fichier CSS**

Pour effectuer le rendu d’un formulaire de HTML qui utilise un fichier CSS personnalisé, veillez à référencer un fichier CSS existant.

**Rendu d’un formulaire de HTML**

Pour générer un formulaire de HTML, vous devez spécifier une conception de formulaire créée dans Designer et enregistrée en tant que fichier XDP. Vous devez également sélectionner un type de transformation de HTML. Par exemple, vous pouvez spécifier le type de transformation de HTML qui effectue le rendu d’un HTML dynamique pour Internet Explorer 5.0 ou version ultérieure.

Le rendu d’un formulaire de HTML nécessite également des valeurs, telles que les valeurs URI nécessaires au rendu d’autres types de formulaires.

**Écrire le flux de données de formulaire dans le navigateur Web client**

Lorsque le service Forms effectue le rendu d’un formulaire de HTML, il renvoie un flux de données de formulaire que vous devez écrire dans le navigateur Web client pour que le formulaire de HTML soit visible par l’utilisateur.

**Voir également**

[Rendu d’un formulaire de HTML qui utilise un fichier CSS à l’aide de l’API Java](#render-an-html-form-that-uses-a-css-file-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendu des PDF forms interactifs](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendu de Forms en tant que HTML](/help/forms/developing/rendering-forms-html.md)

[Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

## Rendu d’un formulaire de HTML qui utilise un fichier CSS à l’aide de l’API Java {#render-an-html-form-that-uses-a-css-file-using-the-java-api}

Rendre un formulaire de HTML qui utilise un fichier CSS personnalisé à l’aide de l’API Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API Java Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Référence au fichier CSS

   * Créez un `HTMLRenderSpec` en utilisant son constructeur.
   * Pour effectuer le rendu du HTML qui utilise un fichier CSS personnalisé, appelez la méthode `HTMLRenderSpec` de `setCustomCSSURI` et transmettez une valeur string qui spécifie l’emplacement et le nom du fichier CSS.

1. Rendu d’un formulaire de HTML

   Appeler la variable `FormsServiceClient` de `(Deprecated) (Deprecated) renderHTMLForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` valeur enum qui spécifie le type de préférence de HTML. Par exemple, pour effectuer le rendu d’un formulaire de HTML compatible avec le HTML dynamique pour Internet Explorer 5.0 ou version ultérieure, spécifiez `TransformTo.MSDHTML`.
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * Le `HTMLRenderSpec` qui stocke les options d’exécution de HTML.
   * Une valeur string qui spécifie la variable `HTTP_USER_AGENT` valeur d’en-tête, telle que `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * A `URLSpec` qui stocke les valeurs URI requises pour générer un formulaire de HTML.
   * A `java.util.HashMap` qui stocke les pièces jointes. Il s’agit d’un paramètre facultatif que vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

   Le `(Deprecated) renderHTMLForm` renvoie une `FormsResult` contenant un flux de données de formulaire qui doit être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Obtention du type de contenu de la variable `com.adobe.idp.Document` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `com.adobe.idp.Document` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.h\ttp.HttpServletResponse` de `getOutputStream` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets et renseignez-le avec le flux de données de formulaire en appelant la fonction `InputStream` de `read` et transmission du tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Rendu de Forms de HTML à l’aide de fichiers CSS personnalisés](#rendering-html-forms-using-custom-css-files)

[Démarrage rapide (mode SOAP) : Rendu d’un formulaire de HTML qui utilise un fichier CSS à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendre un formulaire de HTML qui utilise un fichier CSS à l’aide de l’API du service Web {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Rendre un formulaire de HTML qui utilise un fichier CSS personnalisé à l’aide de l’API Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API Java Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Référence au fichier CSS

   * Créez un `HTMLRenderSpec` en utilisant son constructeur.
   * Pour effectuer le rendu du HTML qui utilise un fichier CSS personnalisé, appelez la méthode `HTMLRenderSpec` de `setCustomCSSURI` et transmettez une valeur string qui spécifie l’emplacement et le nom du fichier CSS.

1. Rendu d’un formulaire de HTML

   Appeler la variable `FormsService` de `(Deprecated) renderHTMLForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` valeur enum qui spécifie le type de préférence de HTML. Par exemple, pour effectuer le rendu d’un formulaire de HTML compatible avec le HTML dynamique pour Internet Explorer 5.0 ou version ultérieure, spécifiez `TransformTo.MSDHTML`.
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez `null`. (Voir [Préremplissage de Forms avec des dispositions souple](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Le `HTMLRenderSpec` qui stocke les options d’exécution de HTML.
   * Une valeur string qui spécifie la variable `HTTP_USER_AGENT` valeur d’en-tête, telle que `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Vous pouvez transmettre une chaîne vide si vous ne souhaitez pas définir cette valeur.
   * A `URLSpec` qui stocke les valeurs URI requises pour générer un formulaire de HTML.
   * A `java.util.HashMap` qui stocke les pièces jointes. Il s’agit d’un paramètre facultatif que vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la variable `(Deprecated) renderHTMLForm` . Cette valeur de paramètre stocke le formulaire rendu.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la variable `(Deprecated) renderHTMLForm` . Ce paramètre stocke les données XML de sortie.
   * Une valeur vide `javax.xml.rpc.holders.LongHolder` qui est renseigné par la variable `(Deprecated) renderHTMLForm` . Cet argument stocke le nombre de pages dans le formulaire.
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la variable `(Deprecated) renderHTMLForm` . Cet argument stocke la valeur du paramètre régional.
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la variable `(Deprecated) renderHTMLForm` . Cet argument stocke la valeur de rendu de HTML utilisée.
   * Une valeur vide `com.adobe.idp.services.holders.FormsResultHolder` qui contiendra les résultats de cette opération.

   Le `(Deprecated) renderHTMLForm` renseigne la méthode `com.adobe.idp.services.holders.FormsResultHolder` qui est transmis en tant que dernière valeur d’argument avec un flux de données de formulaire qui doit être écrit dans le navigateur web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `FormResult` en obtenant la valeur de la variable `com.adobe.idp.services.holders.FormsResultHolder` de `value` membre de données.
   * Créez un `BLOB` qui contient des données de formulaire en appelant la méthode `FormsResult` de `getOutputContent` .
   * Obtention du type de contenu de la variable `BLOB` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `BLOB` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un tableau d’octets et renseignez-le en appelant la variable `BLOB` de `getBinaryData` . Cette tâche affecte le contenu de la `FormsResult` vers le tableau d’octets.
   * Appeler la variable `javax.servlet.http.HttpServletResponse` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Rendu de Forms de HTML à l’aide de fichiers CSS personnalisés](#rendering-html-forms-using-custom-css-files)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
