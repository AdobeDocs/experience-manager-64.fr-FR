---
title: Rendu des PDF forms interactifs
seo-title: Rendering Interactive PDF Forms
description: Utilisez le service Forms pour effectuer le rendu des PDF forms interactifs sur les appareils clients, généralement les navigateurs Web, afin de collecter des informations auprès des utilisateurs. Vous pouvez utiliser le service Forms pour générer des formulaires interactifs à l’aide de l’API Java et de l’API Web Service.
seo-description: Use the Forms service to render interactive PDF forms to client devices, typically web browsers, to collect information from users. You can use Forms service to render interactive forms using the Java API and Web Service API.
uuid: df2a4dc8-f19e-49de-850f-85a204102631
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 3cb307ec-9b7b-4f03-b860-48553ccee746
role: Developer
exl-id: 0bca3af9-78df-44e6-96ef-62bda24d0025
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2473'
ht-degree: 0%

---

# Rendu des PDF forms interactifs {#rendering-interactive-pdf-forms}

Le service Forms effectue le rendu de PDF forms interactifs sur les appareils clients, généralement les navigateurs Web, afin de collecter des informations auprès des utilisateurs. Une fois le formulaire interactif rendu, l’utilisateur peut saisir des données dans les champs du formulaire et cliquer sur un bouton d’envoi situé sur le formulaire pour renvoyer les informations au service Forms. Adobe Reader ou Acrobat doit être installé sur l’ordinateur hébergeant le navigateur web client pour qu’un formulaire de PDF interactif soit visible.

>[!NOTE]
>
>Avant de pouvoir générer un formulaire à l’aide du service Forms, créez une conception de formulaire. En règle générale, une conception de formulaire est créée dans Designer et enregistrée dans un fichier XDP. Pour plus d’informations sur la création d’une conception de formulaire, voir [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

**Exemple de demande de prêt**

Un exemple de demande de prêt est présenté pour démontrer comment le service Forms utilise des formulaires interactifs pour collecter des informations auprès des utilisateurs. Cette application permet à un utilisateur de remplir un formulaire avec les données nécessaires pour sécuriser un prêt, puis d’envoyer les données au service Forms. Le diagramme suivant illustre le flux logique de la demande de prêt.

![ri_ri_finsrv_loanapp_v1](assets/ri_ri_finsrv_loanapp_v1.png)

Le tableau suivant décrit les étapes de ce diagramme.

<table> 
 <thead> 
  <tr> 
   <th><p>Étape</p></th> 
   <th><p>Description</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>1</p></td> 
   <td><p>Le <code>GetLoanForm</code> Java Servlet est appelé à partir d’une page de HTML. </p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>Le <code>GetLoanForm</code> Java Servlet utilise l’API cliente du service Forms pour effectuer le rendu du formulaire de prêt vers le navigateur web client. (Voir <a href="#render-an-interactive-pdf-form-using-the-java-api">Rendu d’un formulaire de PDF interactif à l’aide de l’API Java</a>.)</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>Une fois que l’utilisateur a rempli le formulaire de prêt et cliqué sur le bouton d’envoi, les données sont envoyées à la variable <code>HandleData</code> Servlet Java. (Voir <i>"Formulaire de prêt"</i>.)</p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>Le <code>HandleData</code> Java Servlet utilise l’API cliente du service Forms pour traiter l’envoi du formulaire et récupérer les données du formulaire. Les données sont ensuite stockées dans une base de données d’entreprise. (Voir <a href="/help/forms/developing/handling-submitted-forms.md#handling-submitted-forms">Gestion des Forms envoyées</a>.)</p></td> 
  </tr> 
  <tr> 
   <td><p>5</p></td> 
   <td><p>Un formulaire de confirmation est rendu au navigateur web. Les données telles que le prénom et le nom de l’utilisateur sont fusionnées avec le formulaire avant son rendu. (Voir <a href="/help/forms/developing/prepopulating-forms-flowable-layouts.md">Préremplissage de Forms avec des dispositions souple</a>.)</p></td> 
  </tr> 
 </tbody> 
</table>

**Formulaire de prêt**

Ce formulaire interactif de prêt est rendu par l’exemple de demande de prêt `GetLoanForm` Servlet Java.

![ri_ri_loanform](assets/ri_ri_loanform.png)

**Formulaire de confirmation**

Ce formulaire est rendu par l’exemple de demande de prêt `HandleData` Servlet Java.

![ri_ri_confirm](assets/ri_ri_confirm.png)

Le `HandleData` Java Servlet préremplit ce formulaire avec le prénom et le nom de l’utilisateur, ainsi qu’avec le montant. Une fois le formulaire prérempli, il est envoyé au navigateur Web client. (Voir [Préremplissage de Forms avec des dispositions souple](/help/forms/developing/prepopulating-forms-flowable-layouts.md))

**Servlets Java**

L’exemple de demande de prêt est un exemple d’application de service Forms qui existe en tant que servlet Java. Un servlet Java est un programme Java exécuté sur un serveur d’applications J2EE, tel que WebSphere, qui contient le code de l’API client du service Forms.

Le code suivant affiche la syntaxe d’une servlet Java nommée GetLoanForm :

```as3
     public class GetLoanForm extends HttpServlet implements Servlet { 
         public void doGet(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
          
         } 
         public void doPost(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
              
             }
```

En règle générale, vous ne placez pas le code de l’API client du service Forms dans un servlet Java. `doGet` ou `doPost` . Il est préférable de programmer pour placer ce code dans une classe distincte, instancier la classe depuis l’élément `doPost` (ou `doGet` ) et appelez les méthodes appropriées. Toutefois, pour des raisons de concision du code, les exemples de code de cette section sont conservés au minimum et les exemples de code sont placés dans la variable `doPost` .

>[!NOTE]
>
>Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

**Résumé des étapes**

Pour effectuer le rendu d’un formulaire de PDF interactif, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API client Forms.
1. Spécifiez les valeurs URI.
1. Joindre des fichiers au formulaire (facultatif).
1. Générer un formulaire de PDF interactif.
1. Ecrivez le flux de données de formulaire dans le navigateur Web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Forms**

Avant d’effectuer par programmation une opération de l’API client du service Forms, vous devez créer un objet API client Forms. Si vous utilisez l’API Java, créez une `FormsServiceClient` . Si vous utilisez l’API du service Web Forms, créez une `FormsService` .

**Spécification de valeurs URI**

Vous pouvez spécifier les valeurs URI requises par le service Forms pour générer un formulaire. Une conception de formulaire enregistrée dans le cadre d’une application Forms peut être référencée à l’aide de la valeur URI racine du contenu. `repository:///`. Prenons l’exemple de la conception de formulaire suivante nommée *Loan.xdp* situé dans une application Forms nommée *FormsApplication*:

![ri_ri_formrepository](assets/ri_ri_formrepository.png)

Pour accéder à cette conception de formulaire, spécifiez `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` comme nom du formulaire (premier paramètre transmis à la fonction `renderPDFForm` ) et `repository:///` comme valeur de l’URI racine du contenu.

>[!NOTE]
>
>Pour plus d’informations sur la création d’une application Forms à l’aide de Workbench, voir [Aide de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).

Le chemin d’accès à une ressource située dans une application Forms est le suivant :

`Applications/Application-name/Application-version/Folder.../Filename`

Les valeurs suivantes présentent quelques exemples de valeurs URI :

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

Lorsque vous effectuez le rendu d’un formulaire interactif, vous pouvez définir des valeurs d’URI telles que l’URL cible vers laquelle les données de formulaire sont publiées. L’URL cible peut être définie de l’une des manières suivantes :

* Sur le bouton Envoyer lors de la conception de formulaire dans Designer
* En utilisant l’API client du service Forms

Si l’URL cible est définie dans la conception de formulaire, ne la remplacez pas par l’API cliente du service Forms. En d’autres termes, la définition de l’URL cible à l’aide de l’API Forms réinitialise l’URL spécifiée dans la conception de formulaire sur celle spécifiée à l’aide de l’API. Si vous souhaitez envoyer le formulaire du PDF à l’URL cible spécifiée dans la conception de formulaire, définissez l’URL cible par programmation sur une chaîne vide.

Si vous disposez d’un formulaire contenant un bouton d’envoi et un bouton de calcul (avec un script correspondant s’exécutant sur le serveur), vous pouvez définir par programmation l’URL vers laquelle le formulaire est envoyé pour exécuter le script. Utilisez le bouton d’envoi sur la conception de formulaire pour spécifier l’URL vers laquelle les données de formulaire sont publiées. (Voir [Calcul des données de formulaire](/help/forms/developing/calculating-form-data.md).)

>[!NOTE]
>
>Au lieu de spécifier une valeur d’URL pour référencer un fichier XDP, vous pouvez également transmettre une variable `com.adobe.idp.Document` au service Forms. Le `com.adobe.idp.Document` contient une conception de formulaire. (Voir [Transmission de documents au service Forms](/help/forms/developing/passing-documents-forms-service.md).)

**Joindre des fichiers au formulaire**

Vous pouvez joindre des fichiers à un formulaire. Lorsque vous générez un formulaire PDF avec des pièces jointes, les utilisateurs peuvent récupérer les pièces jointes dans Acrobat à l’aide du volet de pièces jointes. Vous pouvez joindre différents types de fichiers à un formulaire (un fichier texte, par exemple) ou à un fichier binaire (un fichier JPG, par exemple).

>[!NOTE]
>
>Il est facultatif de joindre des pièces jointes à un formulaire.

**Rendu d’un formulaire de PDF interactif**

Pour générer un formulaire, utilisez une conception de formulaire qui a été créée dans Designer et enregistrée au format XDP ou PDF. Vous pouvez également générer un formulaire créé à l’aide d’Acrobat et enregistré en tant que fichier de PDF. Pour générer un formulaire de PDF interactif, appelez la méthode `FormsServiceClient` de `renderPDFForm` ou `renderPDFForm2` .

Le `renderPDFForm` utilise une `URLSpec` . La racine de contenu du fichier XDP est transmise au service Forms à l’aide de la méthode `URLSpec` de `setContentRootURI` . Nom de la conception de formulaire ( `formQuery`) est transmis en tant que valeur de paramètre distincte. Les deux valeurs sont concaténées afin d’obtenir la référence absolue à la conception de formulaire.

Le `renderPDFForm2` accepte une `com.adobe.idp.Document` qui contient le document XDP ou PDF à rendre.

>[!NOTE]
>
>L’option d’exécution du PDF balisé ne peut pas être définie si le document d’entrée est un document de PDF. Si le fichier d’entrée est un fichier XDP, l’option de PDF balisé peut être définie.

## Rendu d’un formulaire de PDF interactif à l’aide de l’API Java {#render-an-interactive-pdf-form-using-the-java-api}

Rendre un formulaire de PDF interactif à l’aide de l’API Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Spécification de valeurs URI

   * Créez un `URLSpec` qui stocke des valeurs URI en utilisant son constructeur.
   * Appeler la variable `URLSpec` de `setApplicationWebRoot` et transmettez une valeur string qui représente la racine web de l’application.
   * Appeler la variable `URLSpec` de `setContentRootURI` et transmettez une valeur string qui spécifie la valeur de l’URI racine du contenu. Assurez-vous que la conception de formulaire se trouve dans l’URI racine du contenu. Dans le cas contraire, le service Forms renvoie une exception. Pour référencer le référentiel, spécifiez `repository:///`.
   * Appeler la variable `URLSpec` de `setTargetURL` et transmettez une valeur string qui spécifie la valeur de l’URL cible à l’endroit où les données de formulaire sont publiées. Si vous définissez l’URL cible dans la conception de formulaire, vous pouvez transmettre une chaîne vide. Vous pouvez également spécifier l’URL vers laquelle un formulaire est envoyé pour effectuer les calculs.

1. Joindre des fichiers au formulaire

   * Créez un `java.util.HashMap` pour stocker les pièces jointes en utilisant son constructeur.
   * Appeler la variable `java.util.HashMap` de `put` pour chaque fichier à joindre au formulaire rendu. Transmettez les valeurs suivantes à cette méthode :

      * Une valeur string qui spécifie le nom de la pièce jointe, y compris l’extension du nom de fichier.
   * A `com.adobe.idp.Document` contenant la pièce jointe du fichier.

   >[!NOTE]
   >
   >Répétez cette étape pour chaque fichier à joindre au formulaire. Cette étape est facultative et vous pouvez la transmettre `null`* si vous ne souhaitez pas envoyer de pièces jointes.*

1. Rendu d’un formulaire de PDF interactif

   Appeler la variable `FormsServiceClient` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * A `PDFFormRenderSpec` qui stocke les options d’exécution. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas spécifier d’options d’exécution.
   * A `URLSpec` contenant des valeurs URI requises par le service Forms.
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

## Rendu d’un formulaire de PDF interactif à l’aide de l’API de service Web {#render-an-interactive-pdf-form-using-the-web-service-api}

Rendre un formulaire de PDF interactif à l’aide de l’API Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API client Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Spécification de valeurs URI

   * Créez un `URLSpec` qui stocke des valeurs URI en utilisant son constructeur.
   * Appeler la variable `URLSpec` de `setApplicationWebRoot` et transmettez une valeur string qui représente la racine web de l’application.
   * Appeler la variable `URLSpec` de `setContentRootURI` et transmettez une valeur string qui spécifie la valeur de l’URI racine du contenu. Assurez-vous que la conception de formulaire se trouve dans l’URI racine du contenu. Dans le cas contraire, le service Forms renvoie une exception. Pour référencer le référentiel, spécifiez `repository:///`.
   * Appeler la variable `URLSpec` de `setTargetURL` et transmettez une valeur string qui spécifie la valeur de l’URL cible à l’endroit où les données de formulaire sont publiées. Si vous définissez l’URL cible dans la conception de formulaire, vous pouvez transmettre une chaîne vide. Vous pouvez également spécifier l’URL vers laquelle un formulaire est envoyé pour effectuer les calculs.

1. Joindre des fichiers au formulaire

   * Créez un `java.util.HashMap` pour stocker les pièces jointes en utilisant son constructeur.
   * Appeler la variable `java.util.HashMap` de `put` pour chaque fichier à joindre au formulaire rendu. Transmettez les valeurs suivantes à cette méthode :

      * Une valeur string qui spécifie le nom de la pièce jointe du fichier, y compris l’extension de nom de fichier
   * A `BLOB` Objet contenant la pièce jointe du fichier

   >[!NOTE]
   >
   >Répétez cette étape pour chaque fichier à joindre au formulaire.

1. Rendu d’un formulaire de PDF interactif

   Appeler la variable `FormsService` de `renderPDFForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez `null`.
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

**Écrire le flux de données de formulaire dans le navigateur Web client**

Lorsque le service Forms effectue le rendu d’un formulaire, il renvoie un flux de données de formulaire que vous devez écrire dans le navigateur Web client. Lorsqu’il est écrit dans le navigateur Web client, le formulaire est visible par l’utilisateur.
