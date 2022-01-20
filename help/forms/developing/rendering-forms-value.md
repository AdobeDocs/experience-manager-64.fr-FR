---
title: Rendu de Forms par valeur
seo-title: Rendering Forms By Value
description: Utilisez l’API Forms (Java) pour effectuer le rendu d’un formulaire par valeur à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Forms API (Java) to render a form by value using the Java API and Web Service API.
uuid: b932cc54-662f-40ae-94e0-20ac82845f3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: ddbb2b82-4c57-4845-a5be-2435902d312b
role: Developer
exl-id: 50c34781-45e3-4255-a997-44f694527c92
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '1821'
ht-degree: 3%

---

# Rendu de Forms par valeur {#rendering-forms-by-value}

En règle générale, une conception de formulaire créée dans Designer est transmise par référence au service Forms. Les conceptions de formulaire peuvent être volumineuses et, par conséquent, il est plus efficace de les transmettre par référence pour éviter d’avoir à rassembler les octets de conception de formulaire par valeur. Le service Forms peut également mettre en cache la conception de formulaire de sorte qu’elle n’ait pas à lire la conception de formulaire en permanence lorsqu’elle est mise en cache.

Si une conception de formulaire contient un attribut UID, il est mis en cache. La valeur UID est unique pour toutes les conceptions de formulaire et sert à identifier un formulaire de manière unique. Lors du rendu d’un formulaire par valeur, le formulaire ne doit être mis en cache que s’il est utilisé à plusieurs reprises. Cependant, si le formulaire n’est pas utilisé à plusieurs reprises et doit être unique, vous pouvez éviter de le mettre en cache à l’aide des options de mise en cache définies à l’aide de l’API AEM Forms.

Le service Forms peut également résoudre l’emplacement du contenu lié dans la conception de formulaire. Par exemple, les images liées référencées à partir de la conception de formulaire sont des URL relatives. On suppose toujours que le contenu lié est relatif à l’emplacement de la conception de formulaire. Par conséquent, la résolution du contenu lié consiste à déterminer son emplacement en appliquant le chemin relatif à l’emplacement de conception de formulaire absolu.

Au lieu de transmettre une conception de formulaire par référence, vous pouvez transmettre une conception de formulaire par valeur. La transmission d’une conception de formulaire par valeur est efficace lorsqu’une conception de formulaire est créée dynamiquement ; c’est-à-dire lorsqu’une application cliente génère le code XML qui crée une conception de formulaire au moment de l’exécution. Dans ce cas, une conception de formulaire n’est pas stockée dans un référentiel physique, car elle est stockée en mémoire. Lors de la création dynamique d’une conception de formulaire au moment de l’exécution et de sa transmission par valeur, vous pouvez mettre le formulaire en cache et améliorer les performances du service Forms.

**Limites de transmission d’un formulaire par valeur**

Les restrictions suivantes s’appliquent lorsqu’une conception de formulaire est transmise par valeur :

* Aucun contenu lié relatif ne peut être inclus dans la conception de formulaire. Toutes les images et tous les fragments doivent être incorporés dans la conception de formulaire ou être référencés de manière absolue.
* Les calculs côté serveur ne peuvent pas être effectués après le rendu du formulaire. Si le formulaire est renvoyé au service Forms, les données sont extraites et renvoyées sans aucun calcul côté serveur.
* Comme HTML ne peut utiliser que les images liées au moment de l’exécution, il n’est pas possible de générer un HTML avec les images incorporées. En effet, le service Forms prend en charge les images incorporées avec HTML en récupérant les images d’une conception de formulaire référencée. Étant donné qu’une conception de formulaire transmise par la valeur ne dispose pas d’un emplacement référencé, les images incorporées ne peuvent pas être extraites lorsque la page de HTML est affichée. Par conséquent, les références d’image doivent être des chemins absolus à rendre en HTML.

>[!NOTE]
>
>Bien que vous puissiez générer différents types de formulaires par valeur (par exemple, des formulaires de HTML ou des formulaires contenant des droits d’utilisation), cette section traite du rendu des PDF forms interactifs.

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Résumé des étapes {#summary-of-steps}

Pour générer un formulaire par valeur, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API client Forms.
1. Référencez la conception de formulaire.
1. Générer un formulaire par valeur.
1. Ecrivez le flux de données de formulaire dans le navigateur Web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Forms**

Avant de pouvoir importer des données par programmation dans une API client de formulaire PDF, vous devez créer un client de service d’intégration de données. Lors de la création d’un client de service, vous définissez les paramètres de connexion requis pour appeler un service.

**Référence à la conception de formulaire**

Lors du rendu d’un formulaire par valeur, vous devez créer une `com.adobe.idp.Document` contenant la conception de formulaire à rendre. Vous pouvez référencer un fichier XDP existant ou créer dynamiquement une conception de formulaire au moment de l’exécution et renseigner une `com.adobe.idp.Document` avec ces données.

>[!NOTE]
>
>Cette section et le démarrage rapide correspondant font référence à un fichier XDP existant.

**Rendu d’un formulaire par valeur**

Pour générer un formulaire par valeur, transmettez une `com.adobe.idp.Document` qui contient la conception de formulaire pour la méthode de rendu `inDataDoc` (peut être l’un des paramètres suivants : `FormsServiceClient` les méthodes de rendu d’objet telles que `renderPDFForm`, `(Deprecated) renderHTMLForm`, etc.). Cette valeur de paramètre est normalement réservée aux données fusionnées avec le formulaire. De même, transmettez une valeur de chaîne vide à la variable `formQuery` . Normalement, ce paramètre nécessite une valeur string qui spécifie le nom de la conception de formulaire.

>[!NOTE]
>
>Si vous souhaitez afficher des données dans le formulaire, les données doivent être spécifiées dans la variable `xfa:datasets` élément . Pour plus d’informations sur l’architecture XFA, voir [https://www.pdfa.org/norm-refs/XFA-3_3.pdf](https://www.pdfa.org/norm-refs/XFA-3_3.pdf).

**Écrire le flux de données de formulaire dans le navigateur Web client**

Lorsque le service Forms effectue le rendu d’un formulaire par valeur, il renvoie un flux de données de formulaire que vous devez écrire dans le navigateur Web client. Lorsqu’il est écrit dans le navigateur Web client, le formulaire est visible par l’utilisateur.

**Voir également**

[Rendu d’un formulaire par valeur à l’aide de l’API Java](#render-a-form-by-value-using-the-java-api)

[Rendu d’un formulaire par valeur à l’aide de l’API du service Web](#render-a-form-by-value-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Transmission de documents au service Forms](/help/forms/developing/passing-documents-forms-service.md)

[Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

## Rendu d’un formulaire par valeur à l’aide de l’API Java {#render-a-form-by-value-using-the-java-api}

Rendre un formulaire par valeur à l’aide de l’API Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Référence à la conception de formulaire

   * Créez un `java.io.FileInputStream` qui représente la conception de formulaire à rendre en utilisant son constructeur et en transmettant une valeur string qui spécifie l’emplacement du fichier XDP.
   * Créez un objet `com.adobe.idp.Document` en utilisant son constructeur et en transmettant l’objet `java.io.FileInputStream`. 

1. Rendu d’un formulaire par valeur

   Appeler la variable `FormsServiceClient` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string vide. (Normalement, ce paramètre nécessite une valeur string qui spécifie le nom de la conception de formulaire.)
   * A `com.adobe.idp.Document` contenant la conception de formulaire. Normalement, cette valeur de paramètre est réservée aux données fusionnées avec le formulaire.
   * A `PDFFormRenderSpec` qui stocke les options d’exécution. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas spécifier d’options d’exécution.
   * A `URLSpec` contenant des valeurs URI requises par le service Forms.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

   Le `renderPDFForm` renvoie une `FormsResult` contenant un flux de données de formulaire pouvant être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Obtention du type de contenu de la variable `com.adobe.idp.Document` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `com.adobe.idp.Document` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets et affectez la taille de la variable `InputStream` . Appeler la variable `InputStream` de `available` pour obtenir la taille de la variable `InputStream` .
   * Renseignez le tableau d’octets avec le flux de données de formulaire en appelant la variable `InputStream` de `read`et transmission du tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Rendu de Forms par valeur](/help/forms/developing/rendering-forms.md)

[Démarrage rapide (mode SOAP) : Rendu par valeur à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendu d’un formulaire par valeur à l’aide de l’API du service Web {#render-a-form-by-value-using-the-web-service-api}

Rendre un formulaire par valeur à l’aide de l’API Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API client Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Référence à la conception de formulaire

   * Créez un objet `java.io.FileInputStream` en utilisant son constructeur. Transmettez une valeur string qui spécifie l’emplacement du fichier XDP.
   * Créez un objet `BLOB` en utilisant son constructeur. Le `BLOB` sert à stocker un document PDF chiffré avec un mot de passe.
   * Créez un tableau d’octets qui stocke le contenu de la variable `java.io.FileInputStream` . Vous pouvez déterminer la taille du tableau d’octets en obtenant la variable `java.io.FileInputStream` la taille de l’objet en utilisant sa `available` .
   * Renseignez le tableau d’octets avec les données de diffusion en appelant la variable `java.io.FileInputStream` de `read` et transmission du tableau d’octets.
   * Renseignez la variable `BLOB` en appelant son objet `setBinaryData` et transmission du tableau d’octets.

1. Rendu d’un formulaire par valeur

   Appeler la variable `FormsService` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string vide. (Normalement, ce paramètre nécessite une valeur string qui spécifie le nom de la conception de formulaire.)
   * A `BLOB` contenant la conception de formulaire. Normalement, cette valeur de paramètre est réservée aux données fusionnées avec le formulaire.
   * A `PDFFormRenderSpec` qui stocke les options d’exécution. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas spécifier d’options d’exécution.
   * A `URLSpec` contenant des valeurs URI requises par le service Forms.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la méthode . Il est utilisé pour stocker le formulaire de PDF rendu.
   * Une valeur vide `javax.xml.rpc.holders.LongHolder` qui est renseigné par la méthode . (Cet argument stocke le nombre de pages dans le formulaire.)
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la méthode . (Cet argument stocke la valeur du paramètre régional.)
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

[Rendu de Forms par valeur](#rendering-forms-by-value)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
