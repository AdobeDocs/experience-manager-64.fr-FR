---
title: Rendu de Forms basé sur des fragments
seo-title: Rendering Forms Based on Fragments
description: Utilisez le service Forms pour effectuer le rendu de formulaires reposant sur des fragments créés à l’aide de Designer.
seo-description: Use the Forms service to render forms that are based on fragments created using Designer.
uuid: 9c9a730d-f970-41f8-afed-4e6b6d3d393d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: a65c5303-0ebd-43a9-a777-401042d8fcad
role: Developer
exl-id: 49c4af9a-5797-468c-b3ad-f3140d445ff2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2195'
ht-degree: 9%

---

# Rendu de Forms basé sur des fragments {#rendering-forms-based-on-fragments}

## Rendu de Forms basé sur des fragments {#rendering-forms-based-on-fragments-inner}

Le service Forms peut générer des formulaires basés sur des fragments que vous créez à l’aide de Designer. A *fragment* est une partie réutilisable d’un formulaire et est enregistrée en tant que fichier XDP distinct pouvant être inséré dans plusieurs conceptions de formulaire. Un fragment peut très bien inclure un bloc d’adresse ou un paragraphe juridique, par exemple.

L’utilisation de fragments simplifie et accélère la création et la gestion d’un grand nombre de formulaires. Lors de la création d’un formulaire, vous insérez une référence au fragment requis qui s’affiche dans le formulaire. La référence au fragment contient un sous-formulaire pointant vers le fichier XDP physique. Pour plus d’informations sur la création de conceptions de formulaire basées sur des fragments, voir [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

Un fragment peut inclure plusieurs sous-formulaires qui sont placés dans un jeu de sous-formulaires de choix. Les jeux de sous-formulaires de choix contrôlent l’affichage des sous-formulaires en fonction du flux de données d’une connexion aux données. Vous vous servez d’instructions conditionnelles pour déterminer le sous-formulaire du jeu devant s’afficher dans le formulaire obtenu. Par exemple, chaque sous-formulaire d’un jeu peut inclure des informations sur un emplacement géographique particulier et le sous-formulaire affiché peut être déterminé en fonction de l’emplacement de l’utilisateur.

A *fragment de script* contient des fonctions ou des valeurs JavaScript réutilisables stockées séparément des objets, tels qu’un analyseur de dates ou un appel de service Web. Les fragments de ce type comprennent un seul objet de script figurant comme enfant de variables dans la palette Hiérarchie. Ils ne peuvent pas être créés à partir de scripts correspondant à des propriétés d’autres objets, tels que les scripts d’événements (validate, calculate ou initialize, par exemple).

L’utilisation de fragments présente les avantages suivants :

* **Réutilisation du contenu**: Vous pouvez utiliser des fragments pour réutiliser du contenu dans plusieurs conceptions de formulaire. Lorsque vous devez utiliser un même contenu dans plusieurs formulaires, il est plus rapide et plus simple d’utiliser un fragment que de copier ou recréer le contenu. L’emploi de fragments permet par ailleurs de garantir l’homogénéité du contenu et de l’aspect de parties de formulaire reprises dans les différents formulaires de référencement.
* **Mises à jour globales**: Vous ne pouvez utiliser des fragments pour apporter des modifications globales à plusieurs formulaires en une seule fois, dans un seul fichier. Vous pouvez modifier le contenu, les objets de script, les liaisons de données, la mise en page ou les styles d’un fragment, et tous les formulaires XDP qui font référence au fragment seront pris en compte dans les modifications.
* Par exemple, un élément courant dans de nombreux formulaires peut être un bloc d’adresse qui inclut un objet de liste déroulante pour le pays. Si vous devez mettre à jour les valeurs de l’objet de liste déroulante, vous devez ouvrir de nombreux formulaires pour effectuer les modifications. Si vous incluez le bloc d’adresse dans un fragment, il vous suffit d’ouvrir un fichier de fragment pour effectuer les modifications.
* Pour mettre à jour un fragment dans un formulaire PDF, vous devez réenregistrer le formulaire dans Designer.
* **Création de formulaires partagés**: Vous pouvez utiliser des fragments pour partager la création de formulaires entre plusieurs ressources. Les développeurs de formulaires familiarisés avec l’utilisation de scripts ou d’autres fonctions avancées de Designer peuvent développer et partager des fragments tirant avantage des fonctions de script et des propriétés dynamiques. Les concepteurs de formulaires peuvent ensuite se servir de ces fragments pour définir la disposition de leurs conceptions de formulaire et s’assurer que toutes les parties de formulaires créés par plusieurs personnes revêtent un aspect, une présentation et des fonctionnalités homogènes.

### Assemblage d’une conception de formulaire à l’aide de fragments {#assembling-a-form-design-assembled-using-fragments}

Vous pouvez assembler une conception de formulaire à transmettre au service Forms en fonction de plusieurs fragments. Pour assembler plusieurs fragments, utilisez le service Assembler. Pour consulter un exemple d’utilisation du service Assemble pour créer une conception de formulaire utilisée par un autre service Forms (le service Output), voir [Création de documents PDF à l’aide de fragments](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments). Au lieu d’utiliser le service Output, vous pouvez exécuter le même workflow à l’aide du service Forms.

Lors de l’utilisation du service Assembler, vous transmettez une conception de formulaire qui a été assemblée à l’aide de fragments. La conception de formulaire qui a été créée ne fait pas référence à d’autres fragments. En revanche, cette rubrique aborde la transmission d’une conception de formulaire qui référence d’autres fragments au service Forms. Toutefois, la conception de formulaire n’a pas été assemblée par Assembler. Il a été créé dans Designer.

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Pour plus d’informations sur la création d’une application web qui effectue le rendu de formulaires à partir de fragments, voir [Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md).

### Résumé des étapes {#summary-of-steps}

Pour générer un formulaire à partir de fragments, effectuez les tâches suivantes :

1. Inclure les fichiers de projet.
1. Créez un objet API client Forms.
1. Spécifiez les valeurs URI.
1. Effectuez le rendu du formulaire.
1. Ecrivez le flux de données de formulaire dans le navigateur Web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Forms**

Avant d’effectuer par programmation une opération d’API client de service Forms, vous devez créer un client de service Forms.

**Spécification de valeurs URI**

Pour réussir le rendu d’un formulaire basé sur des fragments, vous devez vous assurer que le service Forms peut localiser le formulaire et les fragments (fichiers XDP) auxquels la conception de formulaire fait référence. Supposons, par exemple, que le formulaire soit nommé PO.xdp et que ce formulaire utilise deux fragments nommés FooterUS.xdp et FooterCanada.xdp. Dans ce cas, le service Forms doit pouvoir localiser les trois fichiers XDP.

Vous pouvez organiser un formulaire et ses fragments en plaçant le formulaire à un emplacement et les fragments à un autre emplacement, ou vous pouvez placer tous les fichiers XDP au même emplacement. Pour les besoins de cette section, supposons que tous les fichiers XDP se trouvent dans le référentiel AEM Forms. Pour plus d’informations sur le placement de fichiers XDP dans le référentiel AEM Forms, voir [Écriture de ressources](/help/forms/developing/aem-forms-repository.md#writing-resources).

Lors du rendu d’un formulaire basé sur des fragments, vous devez référencer uniquement le formulaire lui-même et non les fragments. Par exemple, vous devez référencer PO.xdp et non FooterUS.xdp ou FooterCanada.xdp. Veillez à placer les fragments à un emplacement où le service Forms peut les localiser.

**Rendu du formulaire**

Un formulaire basé sur des fragments peut être rendu de la même manière que les formulaires non fragmentés. En d’autres termes, vous pouvez générer le formulaire sous la forme de guides de PDF, de HTML ou de formulaire (obsolète). L’exemple de cette section présente un formulaire basé sur des fragments comme formulaire de PDF interactif. (Voir [Rendu des PDF forms interactifs](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**Écrire le flux de données de formulaire dans le navigateur Web client**

Lorsque le service Forms effectue le rendu d’un formulaire, il renvoie un flux de données de formulaire que vous devez écrire dans le navigateur Web client. Lorsqu’il est écrit dans le navigateur Web client, le formulaire est visible par l’utilisateur.

**Voir également**

[Rendu de formulaires reposant sur des fragments à l’aide de l’API Java](#render-forms-based-on-fragments-using-the-java-api)

[Rendu de formulaires basés sur des fragments à l’aide de l’API de service Web](#render-forms-based-on-fragments-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendu des PDF forms interactifs](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendu de formulaires reposant sur des fragments à l’aide de l’API Java {#render-forms-based-on-fragments-using-the-java-api}

Rendre un formulaire basé sur des fragments à l’aide de l’API Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Spécification de valeurs URI

   * Créez un `URLSpec` qui stocke des valeurs URI en utilisant son constructeur.
   * Appeler la variable `URLSpec` de `setApplicationWebRoot` et transmettez une valeur string qui représente la racine web de l’application.
   * Appeler la variable `URLSpec` de `setContentRootURI` et transmettez une valeur string qui spécifie la valeur de l’URI racine du contenu. Assurez-vous que la conception de formulaire et les fragments se trouvent dans l’URI racine du contenu. Dans le cas contraire, le service Forms renvoie une exception. Pour référencer le référentiel, spécifiez `repository://`.
   * Appeler la variable `URLSpec` de `setTargetURL` et transmettez une valeur string qui spécifie la valeur de l’URL cible à l’endroit où les données de formulaire sont publiées. Si vous définissez l’URL cible dans la conception de formulaire, vous pouvez transmettre une chaîne vide. Vous pouvez également spécifier l’URL vers laquelle un formulaire est envoyé pour effectuer les calculs.

1. Rendu du formulaire

   Appeler la variable `FormsServiceClient` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * A `PDFFormRenderSpec` qui stocke les options d’exécution.
   * A `URLSpec` qui contient des valeurs URI requises par le service Forms pour générer un formulaire basé sur des fragments.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

   Le `renderPDFForm` renvoie une `FormsResult` contenant un flux de données de formulaire qui doit être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Obtention du type de contenu de la variable `com.adobe.idp.Document` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `com.adobe.idp.Document` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets pour le remplir avec le flux de données de formulaire en appelant la fonction `InputStream` de `read`et transmission du tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Rendu de Forms basé sur des fragments](#rendering-forms-based-on-fragments)

[Démarrage rapide (mode SOAP) : Rendu d’un formulaire basé sur des fragments à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rendu de formulaires basés sur des fragments à l’aide de l’API de service Web {#render-forms-based-on-fragments-using-the-web-service-api}

Rendre un formulaire basé sur des fragments à l’aide de l’API Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API client Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Spécification de valeurs URI

   * Créez un `URLSpec` stockant des valeurs URI en utilisant son constructeur.
   * Appeler la variable `URLSpec` de `setApplicationWebRoot` et transmettez une valeur string qui représente la racine web de l’application.
   * Appeler la variable `URLSpec` de `setContentRootURI` et transmettez une valeur string qui spécifie la valeur de l’URI racine du contenu. Assurez-vous que la conception de formulaire se trouve dans l’URI racine du contenu. Dans le cas contraire, le service Forms renvoie une exception. Pour référencer le référentiel, spécifiez `repository://`.
   * Appeler la variable `URLSpec` de `setTargetURL` et transmettez une valeur string qui spécifie la valeur de l’URL cible à l’endroit où les données de formulaire sont publiées. Si vous définissez l’URL cible dans la conception de formulaire, vous pouvez transmettre une chaîne vide. Vous pouvez également spécifier l’URL vers laquelle un formulaire est envoyé pour effectuer les calculs.

1. Rendu du formulaire

   Appeler la variable `FormsService` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez `null`.
   * A `PDFFormRenderSpec` qui stocke les options d’exécution. Notez que l’option de PDF balisé ne peut pas être définie si le document d’entrée est un document de PDF. Si le fichier d’entrée est un fichier XDP, l’option de PDF balisé peut être définie.
   * A `URLSpec` contenant les valeurs URI requises par le service Forms.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la méthode . Ce paramètre est utilisé pour stocker le formulaire rendu.
   * Une valeur vide `javax.xml.rpc.holders.LongHolder` qui est renseigné par la méthode . Cet argument stocke le nombre de pages dans le formulaire.
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la méthode . Cet argument stocke la valeur du paramètre régional.
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

[Rendu de Forms basé sur des fragments](#rendering-forms-based-on-fragments)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
