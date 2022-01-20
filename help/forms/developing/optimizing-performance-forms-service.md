---
title: Optimisation des performances du service Forms
seo-title: Optimizing the Performance of theForms Service
description: Définissez les options d’exécution lors du rendu d’un formulaire et stockez les fichiers XDP dans le référentiel afin d’optimiser les performances du service Forms.
seo-description: Set run-time options when rendering a form and store XDP files in the repository to optimize the performance of the Forms service.
uuid: 9040c09a-e5d0-432b-b1c5-ad46ab57c4fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9f883483-b81e-42c6-a4a1-eb499dd112e7
role: Developer
exl-id: a6d468cd-2b70-4332-8277-15f8b9fc1329
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 7%

---

# Optimisation des performances du service Forms {#optimizing-the-performance-of-theforms-service}

## Optimisation des performances du service Forms {#optimizing-the-performance-of-the-forms-service}

Lors du rendu d’un formulaire, vous pouvez définir des options d’exécution qui optimiseront les performances du service Forms. Une autre tâche que vous pouvez effectuer pour améliorer les performances du service Forms consiste à stocker les fichiers XDP dans le référentiel. Toutefois, cette section ne décrit pas comment effectuer cette tâche. (Voir [Appel d’un service à l’aide d’une bibliothèque cliente Java](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).)

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour optimiser les performances du service Forms lors de la génération d’un formulaire, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un objet API client Forms.
1. Définissez les options d’exécution des performances.
1. Effectuez le rendu du formulaire.
1. Ecrivez le flux de données de formulaire dans le navigateur Web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Forms**

Avant d’effectuer par programmation une opération d’API client de service Forms, vous devez créer un client de service Forms. Si vous utilisez l’API Java, créez une `FormsServiceClient` . Si vous utilisez l’API du service Web Forms, créez une `FormsService` .

**Définition des options d’exécution des performances**

Vous pouvez définir les options d’exécution de performances suivantes afin d’améliorer les performances du service Forms :

* **Mise en cache des formulaires**: Vous pouvez mettre en cache un formulaire rendu en tant que PDF dans le cache du serveur. Chaque formulaire est mis en cache après avoir été généré pour la première fois. Sur un rendu ultérieur, si le formulaire mis en cache est plus récent que l’horodatage de conception de formulaire, le formulaire est récupéré depuis le cache. En mettant en cache des formulaires, vous améliorez les performances du service Forms, car il n’a pas à récupérer la conception de formulaire à partir d’un référentiel.
* Le rendu des guides de formulaire (obsolète) peut prendre plus de temps que les autres types de transformation. Il est recommandé de mettre en cache les guides de formulaire (obsolète) afin d’améliorer les performances.
* **Option autonome**: Si vous n’avez pas besoin du service Forms pour effectuer des calculs côté serveur, vous pouvez définir l’option Autonome sur `true`, ce qui entraîne la génération de formulaires sans informations d’état. Les informations d’état sont nécessaires si vous souhaitez rendre un formulaire interactif à un utilisateur final qui saisit ensuite les informations dans le formulaire et renvoie le formulaire au service Forms. Le service Forms effectue ensuite une opération de calcul et renvoie le formulaire à l’utilisateur avec les résultats affichés dans le formulaire. Si un formulaire sans informations d’état est renvoyé au service Forms, seules les données XML sont disponibles et les calculs côté serveur ne sont pas effectués.
* **PDF linéarisé**: Un fichier de PDF linéarisé est organisé pour permettre un accès incrémentiel efficace dans un environnement réseau. Le fichier de PDF est un PDF valide à tous les égards et est compatible avec toutes les visionneuses et autres applications de PDF existantes. En d’autres termes, un PDF linéarisé peut être affiché pendant son téléchargement.
* Cette option n’améliore pas les performances lorsqu’un formulaire de PDF est rendu sur le client.
* **Option GuideRSL**: Active la génération du guide de formulaire (obsolète) à l’aide de bibliothèques partagées d’exécution. Cela signifie que la première requête téléchargera un fichier de SWF plus petit, ainsi que des bibliothèques partagées plus volumineuses qui sont stockées dans le cache du navigateur. Pour plus d’informations, voir RSL dans la documentation Flex.
* Vous pouvez également améliorer les performances du service Forms en effectuant le rendu d’un formulaire sur le client. (Voir [Rendu de Forms sur le client](/help/forms/developing/rendering-forms-client.md).)

**Rendu du formulaire**

Pour générer le formulaire après avoir défini les options de performances, vous utilisez la même logique d’application que pour générer un formulaire sans options de performances.

**Écrire le flux de données de formulaire dans le navigateur Web client**

Une fois que le service Forms a rendu un formulaire, il renvoie un flux de données de formulaire que vous devez écrire dans le navigateur Web client. Lorsqu’il est écrit dans le navigateur Web client, le formulaire est visible par l’utilisateur.

**Voir également**

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendu des PDF forms interactifs](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendu de Forms en tant que HTML](/help/forms/developing/rendering-forms-html.md)

[Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Optimisation des performances à l’aide de l’API Java {#optimize-the-performance-using-the-java-api}

Rendre un formulaire avec des performances optimisées à l’aide de l’API Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Définition des options d’exécution des performances

   * Créez un objet `PDFFormRenderSpec` en utilisant son constructeur.
   * Définissez l’option de cache de formulaire en appelant la méthode `PDFFormRenderSpec` de `setCacheEnabled` méthode et transmission `true`.
   * Définissez l’option linéarisée en appelant la variable `PDFFormRenderSpec` de `setLinearizedPDF` méthode et transmission `true.`

1. Rendu du formulaire

   Appeler la variable `FormsServiceClient` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier.
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * A `PDFFormRenderSpec` qui stocke des options d’exécution afin d’améliorer les performances.
   * A `URLSpec` contenant des valeurs URI requises par le service Forms.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

   Le `renderPDFForm` renvoie une `FormsResult` contenant un flux de données de formulaire qui doit être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `javax.servlet.ServletOutputStream` utilisé pour envoyer un flux de données de formulaire au navigateur Web client.
   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets et renseignez-le avec le flux de données de formulaire en appelant la fonction `InputStream` de `read`et transmission du tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Démarrage rapide (mode SOAP) : Optimisation des performances à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Optimisation des performances à l’aide de l’API de service Web {#optimize-the-performance-using-the-web-service-api}

Rendre un formulaire avec des performances optimisées à l’aide de l’API Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API client Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Définition des options d’exécution des performances

   * Créez un objet `PDFFormRenderSpec` en utilisant son constructeur.
   * Définissez l’option de cache de formulaire en appelant la méthode `PDFFormRenderSpec` de `setCacheEnabled` et transmettre la valeur true.
   * Définissez l’option autonome en appelant la méthode `PDFFormRenderSpec` de `setStandAlone` et transmettre la valeur true.
   * Définissez l’option linéarisée en appelant la variable `PDFFormRenderSpec` de `setLinearizedPDF` et transmettre la valeur true.

1. Rendu du formulaire

   Appeler la variable `FormsService` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier.
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez `null`.
   * A `PDFFormRenderSpecc` qui stocke les options d’exécution.
   * A `URLSpec` contenant des valeurs URI requises par le service Forms.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la méthode . Il est utilisé pour stocker le formulaire de PDF rendu.
   * Une valeur vide `javax.xml.rpc.holders.LongHolder` qui est renseigné par la méthode . (Cet argument stocke le nombre de pages dans le formulaire).
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la méthode . (Cet argument stocke la valeur du paramètre régional).
   * Une valeur vide `com.adobe.idp.services.holders.FormsResultHolder` qui contiendra les résultats de cette opération.

   Le `renderPDFForm` renseigne la méthode `com.adobe.idp.services.holders.FormsResultHolder` qui est transmis en tant que dernière valeur d’argument avec un flux de données de formulaire qui doit être écrit dans le navigateur web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `FormResult` en obtenant la valeur de la variable `com.adobe.idp.services.holders.FormsResultHolder` de `value` membre de données.
   * Créez un `javax.servlet.ServletOutputStream` utilisé pour envoyer un flux de données de formulaire au navigateur Web client.
   * Créez un `BLOB` qui contient des données de formulaire en appelant la méthode `FormsResult` de `getOutputContent` .
   * Créez un tableau d’octets et renseignez-le en appelant la variable `BLOB` de `getBinaryData` . Cette tâche affecte le contenu de la `FormsResult` vers le tableau d’octets.
   * Appeler la variable `javax.servlet.http.HttpServletResponse` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
