---
title: Rendu du Forms de HTML avec des barres d’outils personnalisées
seo-title: Rendering HTML Forms with CustomToolbars
description: Utilisez le service Forms pour personnaliser une barre d’outils générée avec un formulaire de HTML. Vous pouvez générer un HTML de formulaire avec une barre d’outils personnalisée à l’aide de l’API Java et d’une API de service Web.
seo-description: Use the Forms service to customize a toolbar that is rendered with an HTML form. You can render an HTML Form with a custom toolbar using the Java API and a Web Service API.
uuid: b9c9464e-ff19-4051-a39b-4ec71c512d10
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 7eb0e8a8-d76a-43f7-a012-c21157b14cd4
role: Developer
exl-id: f4711d21-59d3-482e-8059-9ef7c6008d21
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2331'
ht-degree: 1%

---

# Rendu du Forms de HTML avec des barres d’outils personnalisées {#rendering-html-forms-with-customtoolbars}

## Forms de HTML de rendu avec barres d’outils personnalisées {#rendering-html-forms-with-custom-toolbars}

Le service Forms vous permet de personnaliser une barre d’outils générée avec un formulaire de HTML. Une barre d’outils peut être personnalisée pour modifier son aspect en remplaçant les styles CSS par défaut et pour ajouter un comportement dynamique en remplaçant les scripts Java. Une barre d’outils est personnalisée à l’aide d’un fichier XML nommé fscmenu.xml. Par défaut, le service Forms récupère ce fichier à partir d’un emplacement URI spécifié en interne.

>[!NOTE]
>
>Cet emplacement URI se trouve dans le fichier adobe-forms-core.jar situé dans le fichier adobe-forms-dsc.jar . Le fichier adobe-forms-dsc.jar se trouve dans C:\Adobe\Adobe_Experience_Manager_forms\ folder (C:\ is the installation directory). Vous pouvez utiliser un outil d’extraction de fichier, tel que Win RAR, pour ouvrir Adobe.

Vous pouvez copier le fichier fscmenu.xml à partir de cet emplacement, le modifier pour répondre à vos besoins, puis le placer dans un emplacement URI personnalisé. Ensuite, à l’aide de l’API Forms Service, définissez les options d’exécution qui entraînent l’utilisation du service Forms à l’aide de votre fichier fscmenu.xml à partir de l’emplacement spécifié. Ces actions entraînent le rendu d’un formulaire de HTML par le service Forms doté d’une barre d’outils personnalisée.

Outre le fichier fscmenu.xml , vous devez également obtenir les fichiers suivants :

* fscmenu.js
* fscattachments.js
* fscmenu.css
* fscmenu-v.css
* fscmenu-ie.css
* fscdialog.css

fscJS est le script Java associé à chaque noeud. Il est nécessaire d’en fournir un pour la variable `div#fscmenu` noeud et éventuellement pour `ul#fscmenuItem` noeuds. Les fichiers JS mettent en oeuvre la fonctionnalité de base de la barre d’outils et les fichiers par défaut fonctionnent.

fscCSS est une feuille de style associée à un noeud particulier. Les styles des fichiers CSS définissent l’aspect de la barre d’outils. *fscVCSS* est une feuille de style pour une barre d’outils verticale, qui s’affiche à gauche du formulaire de HTML rendu. *fscIECSS* est une feuille de style utilisée pour les formulaires HTML rendus dans Internet Explorer.

Assurez-vous que tous les fichiers ci-dessus sont référencés dans le fichier fscmenu.xml . En d’autres termes, dans le fichier fscmenu.xml, spécifiez les emplacements URI vers ces fichiers afin que le service Forms puisse les localiser. Par défaut, ces fichiers sont disponibles à des emplacements URI commençant par des mots-clés internes. `FSWebRoot` ou `ApplicationWebRoot`.

Pour personnaliser la barre d’outils, remplacez les mots-clés à l’aide du mot-clé externe `FSToolBarURI`. Ce mot-clé représente l’URI qui est transmis au service Forms au moment de l’exécution (cette approche est présentée plus loin dans cette section).

Vous pouvez également spécifier les emplacements absolus de ces fichiers JS et CSS, tels que https://www.mycompany.com/scripts/misc/fscmenu.js. Dans ce cas, vous n’avez pas besoin d’utiliser la variable `FSToolBarURI` mot-clé.

>[!NOTE]
>
>Il n’est pas recommandé de mélanger les méthodes de référencement de ces fichiers. En d’autres termes, tous les URI doivent être référencés à l’aide de la fonction `FSToolBarURI` ou un emplacement absolu.

Vous pouvez obtenir les fichiers JS et CSS en ouvrant adobe-forms-&lt;appserver>fichier .ear. Dans ce fichier, ouvrez le fichier adobe-forms-res.war. Tous ces fichiers se trouvent dans le fichier WAR. adobe-forms-&lt;appserver>Le fichier .ear se trouve dans le dossier d’installation d’AEM forms (C:\ is the installation directory). Vous pouvez ouvrir adobe-forms-&lt;appserver>.ear à l’aide d’un outil d’extraction de fichiers tel que WinRAR.

La syntaxe XML suivante illustre un exemple de fichier fscmenu.xml.

```as3
 <div id="fscmenu" fscJS="FSToolBarURI/scripts/fscmenu.js" fscCSS="FSToolBarURI/fscmenu.css" fscVCSS="FSToolBarURI/fscmenu-v.css" fscIECSS="FSToolBarURI/fscmenu-ie.css"> 
         <ul class="fscmenuItem" id="Home"> 
             <li> 
                 <a href="#" fscTarget="_top" tabindex="1">Home</a> 
             </li> 
         </ul> 
         <ul class="fscmenuItem" id="Upload" fscJS="FSToolBarURI/scripts/fscattachments.js" fscCSS="FSToolBarURI/fscdialog.css"> 
             <li> 
                 <a tabindex="2">Upload Attachments</a> 
                 <ul class="fscmenuPopup" id="fscUploadAttachments"> 
                     <li> 
                         <a href="javascript:doUploadDialog();" tabindex="3">Add ...</a> 
                     </li> 
                     <li> 
                         <a href="javascript:doDeleteDialog();" tabindex="4">Delete ...</a> 
                     </li> 
                 </ul> 
             </li> 
         </ul> 
         <ul class="fscmenuItem" id="Download"> 
             <li> 
                 <a tabindex="100">Download Attachments</a> 
                 <ul class="fscmenuPopup"> 
                     <li> 
                         <a tabindex="101">None available</a> 
                     </li> 
                 </ul> 
             </li> 
         </ul> 
     </div>
```

>[!NOTE]
>
>Le texte en gras représente les URI des fichiers CSS et JS qui doivent être référencés.

Les éléments suivants décrivent comment personnaliser une barre d’outils :

* Modifier les valeurs de `fscJS`, `fscCSS`, `fscVCSS`, `fscIECSS` attributs (dans le fichier fscmenu.xml) pour refléter les emplacements personnalisés des fichiers référencés à l’aide de l’une des méthodes décrites dans cette section (par exemple : `fscJS="FSToolBarURI/scripts/fscmenu.js"`).
* Tous les fichiers CSS et JS doivent être spécifiés. Si aucun des fichiers n’est modifié, indiquez celui par défaut à l’emplacement personnalisé. Vous pouvez obtenir les fichiers par défaut en ouvrant différents fichiers comme décrit dans cette section.
* Le fait de fournir une référence absolue (par exemple, https://www.example.com/scripts/custom-vertical-fscmenu.css) pour n’importe quel fichier est autorisé.
* Les fichiers JS et CSS que la variable `div#fscmenu` sont essentiels pour la fonctionnalité de barre d’outils. Individuel `ul#fscmenuItem` Les noeuds peuvent prendre en charge ou non les fichiers JS ou CSS.

**Modification de la valeur locale**

Dans le cadre de la personnalisation d’une barre d’outils, vous pouvez modifier la valeur des paramètres régionaux de la barre d’outils. En d’autres termes, vous pouvez l’afficher dans une autre langue. L’illustration suivante présente une barre d’outils personnalisée qui s’affiche en français.

>[!NOTE]
>
>Il n’est pas possible de créer une barre d’outils personnalisée dans plusieurs langues. Les barres d’outils ne peuvent pas utiliser des fichiers XML différents en fonction des paramètres régionaux.

Pour modifier la valeur des paramètres régionaux d’une barre d’outils, assurez-vous que le fichier fscmenu.xml contient la langue que vous souhaitez afficher. La syntaxe XML suivante présente le fichier fscmenu.xml utilisé pour afficher une barre d’outils française.

```as3
 <div id="fscmenu" fscJS="FSToolBarURI/scripts/fscmenu.js" fscCSS="FSToolBarURI/fscmenu.css" fscVCSS="FSToolBarURI/fscmenu-v.css" fscIECSS="FSToolBarURI/fscmenu-ie.css"> 
         <ul class="fscmenuItem" id="Home"> 
             <li> 
                 <a href="#" fscTarget="_top" tabindex="1">Accueil</a> 
             </li> 
         </ul> 
         <ul class="fscmenuItem" id="Upload" fscJS="FSToolBarURI/scripts/fscattachments.js" fscCSS="FSToolBarURI/fscdialog.css"> 
             <li> 
                 <a tabindex="2">Télécharger les pièces jointes</a> 
                 <ul class="fscmenuPopup" id="fscUploadAttachments"> 
                     <li> 
                         <a href="javascript:doUploadDialog();" tabindex="3">Ajouter...</a> 
                     </li> 
                     <li> 
                         <a href="javascript:doDeleteDialog();" tabindex="4">Supprimer...</a> 
                     </li> 
                 </ul> 
             </li> 
         </ul> 
         <ul class="fscmenuItem" id="Download"> 
             <li> 
                 <a tabindex="100">Télécharger les pièces jointes</a> 
                 <ul class="fscmenuPopup"> 
                     <li> 
                         <a tabindex="101">Aucune disponible</a> 
                     </li> 
                 </ul> 
             </li> 
         </ul> 
     </div>
```

>[!NOTE]
>
>Les didacticiels de mise en route associés à cette section utilisent ce fichier XML pour afficher une barre d’outils personnalisée en français, comme illustré ci-dessus.

Spécifiez également une valeur de paramètre régional valide en appelant la variable `HTMLRenderSpec` de `setLocale` et transmission d’une valeur string qui spécifie la valeur locale. Par exemple, pass `fr_FR` pour spécifier le français. Le service Forms est fourni avec des barres d’outils localisées.

>[!NOTE]
>
>Avant d’effectuer le rendu d’un formulaire de HTML qui utilise une barre d’outils personnalisée, vous devez connaître le mode de rendu des formulaires de HTML. (Voir [Rendu de Forms en tant que HTML](/help/forms/developing/rendering-forms-html.md).)

Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Résumé des étapes {#summary-of-steps}

Pour effectuer le rendu d’un formulaire de HTML contenant une barre d’outils personnalisée, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API Java Forms.
1. Référencez un fichier XML fscmenu personnalisé.
1. Générer un HTML de formulaire.
1. Ecrivez le flux de données de formulaire dans le navigateur Web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, incluez les fichiers proxy.

**Création d’un objet API Java Forms**

Avant d’effectuer par programmation une opération prise en charge par le service Forms, vous devez créer un objet client Forms.

**Référence à un fichier XML fscmenu personnalisé**

Pour effectuer le rendu d’un formulaire de HTML contenant une barre d’outils personnalisée, référencez un fichier XML fscmenu qui décrit la barre d’outils. (Cette section fournit deux exemples d’un fichier XML fscmenu.) Assurez-vous également que le fichier fscmenu.xml spécifie correctement l’emplacement de tous les fichiers référencés. Comme indiqué plus haut dans cette section, assurez-vous que tous les fichiers sont référencés par la variable `FSToolBarURI` ou leur emplacement absolu.

**Rendu d’un formulaire de HTML**

Pour effectuer le rendu d’un formulaire de HTML, spécifiez une conception de formulaire qui a été créée dans Designer et enregistrée en tant que fichier XDP. Sélectionnez également un type de transformation de HTML. Par exemple, vous pouvez spécifier le type de transformation de HTML qui effectue le rendu d’un HTML dynamique pour Internet Explorer 5.0 ou version ultérieure.

Le rendu d’un formulaire de HTML nécessite également des valeurs, telles que des valeurs URI pour le rendu d’autres types de formulaires.

**Écrire le flux de données de formulaire dans le navigateur Web client**

Lorsque le service Forms effectue le rendu d’un formulaire de HTML, il renvoie un flux de données de formulaire que vous devez écrire dans le navigateur Web client pour que le formulaire de HTML soit visible par les utilisateurs.

**Voir également**

[Rendu d’un formulaire de HTML avec une barre d’outils personnalisée à l’aide de l’API Java](#render-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Rendu d’un formulaire de HTML avec une barre d’outils personnalisée à l’aide de l’API de service Web](#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendu des PDF forms interactifs](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendu de Forms en tant que HTML](/help/forms/developing/rendering-forms-html.md)

[Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendu d’un formulaire de HTML avec une barre d’outils personnalisée à l’aide de l’API Java {#render-an-html-form-with-a-custom-toolbar-using-the-java-api}

Rendre un formulaire de HTML contenant une barre d’outils personnalisée à l’aide de l’API Forms Service (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API Java Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un objet `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory`. 

1. Référence à un fichier XML fscmenu personnalisé

   * Créez un `HTMLRenderSpec` en utilisant son constructeur.
   * Pour générer un HTML de formulaire avec une barre d’outils, appelez la méthode `HTMLRenderSpec` de `setHTMLToolbar` et transmettre une `HTMLToolbar` valeur d’énumération. Par exemple, pour afficher une barre d’outils de HTML verticale, transmettez `HTMLToolbar.Vertical`.
   * Indiquez l’emplacement du fichier XML fscmenu en appelant la variable `HTMLRenderSpec` de `setToolbarURI` et transmission d’une valeur string qui spécifie l’emplacement URI du fichier XML.
   * Le cas échéant, définissez la valeur du paramètre régional en appelant la variable `HTMLRenderSpec` de `setLocale` et transmission d’une valeur string qui spécifie la valeur locale. La valeur par défaut est Anglais.

   >[!NOTE]
   >
   >Les didacticiels de mise en route associés à cette section définissent cette valeur sur `fr_FR`*.*

1. Rendu d’un formulaire de HTML

   Appeler la variable `FormsServiceClient` de `renderHTMLForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` valeur enum qui spécifie le type de préférence de HTML. Par exemple, pour effectuer le rendu d’un formulaire de HTML compatible avec le HTML dynamique pour Internet Explorer 5.0 ou version ultérieure, spécifiez `TransformTo.MSDHTML`.
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * Le `HTMLRenderSpec` qui stocke les options d’exécution de HTML.
   * Une valeur string qui spécifie la variable `HTTP_USER_AGENT` valeur d’en-tête, telle que `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * A `URLSpec` qui stocke les valeurs URI requises pour générer un formulaire de HTML.
   * A `java.util.HashMap` qui stocke les pièces jointes. Il s’agit d’un paramètre facultatif que vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

   Le `renderHTMLForm` renvoie une `FormsResult` contenant un flux de données de formulaire qui doit être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Obtention du type de contenu de la variable `com.adobe.idp.Document` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `com.adobe.idp.Document` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets et renseignez-le avec le flux de données de formulaire en appelant la fonction `InputStream` de `read` et transmission du tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Démarrage rapide (mode SOAP) : Rendu d’un formulaire de HTML avec une barre d’outils personnalisée à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rendu d’un formulaire de HTML avec une barre d’outils personnalisée à l’aide de l’API de service Web {#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api}

Rendre un formulaire de HTML contenant une barre d’outils personnalisée à l’aide de l’API Forms Service (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API Java Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Référence à un fichier XML fscmenu personnalisé

   * Créez un `HTMLRenderSpec` en utilisant son constructeur.
   * Pour générer un HTML de formulaire avec une barre d’outils, appelez la méthode `HTMLRenderSpec` de `setHTMLToolbar` et transmettre une `HTMLToolbar` valeur d’énumération. Par exemple, pour afficher une barre d’outils de HTML verticale, transmettez `HTMLToolbar.Vertical`.
   * Indiquez l’emplacement du fichier XML fscmenu en appelant la variable `HTMLRenderSpec` de `setToolbarURI` et transmission d’une valeur string qui spécifie l’emplacement URI du fichier XML.
   * Le cas échéant, définissez la valeur du paramètre régional en appelant la variable `HTMLRenderSpec` de `setLocale` et transmission d’une valeur string qui spécifie la valeur locale. La valeur par défaut est Anglais.

   >[!NOTE]
   >
   >Les didacticiels de mise en route associés à cette section définissent cette valeur sur `fr_FR`*.*

1. Rendu d’un formulaire de HTML

   Appeler la variable `FormsService` de `renderHTMLForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` valeur enum qui spécifie le type de préférence de HTML. Par exemple, pour effectuer le rendu d’un formulaire de HTML compatible avec le HTML dynamique pour Internet Explorer 5.0 ou version ultérieure, spécifiez `TransformTo.MSDHTML`.
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez `null`.
   * Le `HTMLRenderSpec` qui stocke les options d’exécution de HTML.
   * Une valeur string qui spécifie la variable `HTTP_USER_AGENT` valeur d’en-tête, telle que `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322`). Vous pouvez transmettre une chaîne vide si vous ne souhaitez pas définir cette valeur.
   * A `URLSpec` qui stocke les valeurs URI requises pour générer un formulaire de HTML.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif. Vous pouvez indiquer `null` si vous n’avez pas l’intention de joindre des fichiers au formulaire.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la variable `renderHTMLForm` . Cette valeur de paramètre stocke le formulaire rendu.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la variable `renderHTMLForm` . Ce paramètre stocke les données XML de sortie.
   * Une valeur vide `javax.xml.rpc.holders.LongHolder` qui est renseigné par la variable `renderHTMLForm` . Cet argument stocke le nombre de pages dans le formulaire.
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la variable `renderHTMLForm` . Cet argument stocke la valeur du paramètre régional.
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la variable `renderHTMLForm` . Cet argument stocke la valeur de rendu de HTML utilisée.
   * Une valeur vide `com.adobe.idp.services.holders.FormsResultHolder` qui contiendra les résultats de cette opération.

   Le `renderHTMLForm` renseigne la méthode `com.adobe.idp.services.holders.FormsResultHolder` qui est transmis en tant que dernière valeur d’argument avec un flux de données de formulaire qui doit être écrit dans le navigateur web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `FormResult` en obtenant la valeur de la variable `com.adobe.idp.services.holders.FormsResultHolder` de `value` membre de données.
   * Créez un `BLOB` qui contient des données de formulaire en appelant la méthode `FormsResult` de `getOutputContent` .
   * Obtention du type de contenu de la variable `BLOB` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `BLOB` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un tableau d’octets et renseignez-le en appelant la variable `BLOB` de `getBinaryData` . Cette tâche affecte le contenu de la `FormsResult` vers le tableau d’octets.
   * Appeler la variable `javax.servlet.http.HttpServletResponse` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
