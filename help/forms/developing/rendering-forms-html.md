---
title: Rendu de Forms en tant que HTML
seo-title: Rendering Forms as HTML
description: Utilisez le service Forms pour effectuer le rendu des formulaires en tant que HTML en réponse à une requête HTTP d’un navigateur web. Vous pouvez utiliser l’API Java et l’API Web Service pour effectuer le rendu des formulaires en tant que HTML.
seo-description: Use the Forms service to render forms as HTML in response to an HTTP request from a web browser. You can use the Java API and Web Service API to render forms as HTML.
uuid: bd8edb6f-333b-4ceb-9877-618f5377f56f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 669ede46-ea55-444b-a23f-23a86e5aff8e
role: Developer
exl-id: 2e8bcdf8-ae57-4ccd-945a-8f3fda4aa3c2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '4137'
ht-degree: 1%

---

# Rendu de Forms en tant que HTML {#rendering-forms-as-html}

Le service Forms effectue le rendu des formulaires en tant que HTML en réponse à une requête HTTP d’un navigateur web. L’un des avantages du rendu d’un formulaire en tant que HTML réside dans le fait que l’ordinateur sur lequel se trouve le navigateur Web client ne nécessite pas Adobe Reader, Acrobat ou Flash Player (pour les guides de formulaire (obsolète)).

Pour générer un formulaire en tant que HTML, la conception de formulaire doit être enregistrée en tant que fichier XDP. Une conception de formulaire enregistrée en tant que fichier de PDF ne peut pas être générée en tant que HTML. Lors du développement d’une conception de formulaire dans Designer qui sera rendue par HTML, tenez compte des critères suivants :

* N’utilisez pas les propriétés de bordure d’un objet pour tracer des lignes, des zones ou des grilles dans un formulaire. Certains navigateurs n’alignent pas les bordures exactement comme elles sont présentées dans un aperçu de Les objets risquent de se chevaucher ou de déplacer d’autres objets de manière imprévue.
* Vous pouvez utiliser des lignes, des rectangles et des cercles pour définir l’arrière-plan.
* Dessinez du texte légèrement plus grand que ce qui semble être nécessaire pour s’adapter au texte. Certains navigateurs Web n’affichent pas le texte de manière lisible.

>[!NOTE]
>
>Lors du rendu d’un formulaire contenant des images de TIFF à l’aide de la variable `FormServiceClient` de `(Deprecated) renderHTMLForm` et `renderHTMLForm2` , les images de TIFF ne sont pas visibles dans le formulaire de HTML rendu affiché dans les navigateurs Internet Explorer ou Mozilla Firefox. Ces navigateurs ne fournissent pas de prise en charge native des images de TIFF.

## Pages de HTML {#html-pages}

Lorsqu’une conception de formulaire est générée sous la forme d’un formulaire de HTML, chaque sous-formulaire de second niveau est généré sous la forme d’une page de HTML (panneau). Vous pouvez afficher la hiérarchie d’un sous-formulaire dans Designer. Les sous-formulaires enfants qui appartiennent au sous-formulaire racine (le nom par défaut d’un sous-formulaire racine est form1) sont les sous-formulaires de panneau. L’exemple suivant illustre les sous-formulaires d’une conception de formulaire.

```as3
     form1 
         Master Pages 
         PanelSubform1 
             NestedDynamicSubform 
                 TextEdit1 
         PanelSubform2 
             TextEdit1 
         PanelSubform3 
             TextEdit1 
         PanelSubform4 
             TextEdit1
```

Lorsque les conceptions de formulaire sont générées sous la forme de formulaires par HTML, les panneaux ne sont pas limités à une taille de page particulière. Si vous disposez de sous-formulaires dynamiques, ils doivent être imbriqués dans le sous-formulaire du panneau. Les sous-formulaires dynamiques peuvent s’étendre sur un nombre infini de pages de HTML.

Lorsqu’un formulaire est rendu sous la forme d’un HTML, les formats de page (requis pour paginer les formulaires rendus en tant que PDF) n’ont aucune signification. Comme un formulaire avec disposition souple peut atteindre un nombre infini de pages de HTML, il est important d’éviter les pieds de page sur le gabarit. Un pied de page situé sous la zone de contenu d’un gabarit peut remplacer le contenu du HTML qui s’étend au-delà d’une limite de page.

Vous devez explicitement passer d’un panneau à l’autre à l’aide de la méthode `xfa.host.pageUp` et `xfa.host.pageDown` méthodes. Vous pouvez modifier les pages en envoyant un formulaire au service Forms et en demandant au service Forms de le rendre à nouveau sur le périphérique client, généralement un navigateur Web.

>[!NOTE]
>
>Le processus d’envoi d’un formulaire au service Forms, puis de renvoi du formulaire par le service Forms vers le périphérique client est appelé données de basculement arrondies vers le serveur.

>[!NOTE]
>
>Si vous souhaitez personnaliser l’aspect du bouton Signature numérique du HTML sur un formulaire de HTML, vous devez modifier les propriétés suivantes dans le fichier fscdigsig.css (dans le fichier adobe-forms-ds.ear > adobe-forms-ds.war) :

**.fsc-ds-ssb**: Cette feuille de style s’applique en cas de champ de signe vide.

**.fsc-ds-ssv**: Cette feuille de style s’applique dans le cas d’un champ de signe valide.

**.fsc-ds-ssc**: Cette feuille de style s’applique dans le cas d’un champ de signe valide, mais les données ont changé.

**.fsc-ds-ssi**: Cette feuille de style s’applique en cas de champ de signature non valide.

**.fsc-ds-popup-bg**: Cette propriété de feuille de style n’est pas utilisée.

**.fsc-ds-popup-btn**: Cette propriété de feuille de style n’est pas utilisée.

## Exécution de scripts {#running-scripts}

Un auteur de formulaire indique si un script s’exécute sur le serveur ou sur le client. Le service Forms crée un environnement de traitement des événements distribué pour l’exécution des renseignements sur les formulaires qui peuvent être distribués entre le client et le serveur à l’aide de la variable `runAt` attribut. Pour plus d’informations sur cet attribut ou la création de scripts dans les conceptions de formulaire, voir [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

Le service Forms peut exécuter des scripts pendant la génération du formulaire. Par conséquent, vous pouvez préremplir un formulaire avec des données en vous connectant à une base de données ou à des services Web qui ne sont peut-être pas disponibles sur le client. Vous pouvez également définir le `Click` pour exécuter sur le serveur afin que le client puisse arrondir les données du parcours au serveur. Cela permet au client d’exécuter des scripts qui peuvent nécessiter des ressources serveur, telles qu’une base de données d’entreprise, lorsqu’un utilisateur interagit avec un formulaire. Pour les formulaires HTML, les scripts formcalc ne peuvent être exécutés que sur le serveur. Par conséquent, vous devez marquer ces scripts pour qu’ils s’exécutent sur `server` ou `both`.

Vous pouvez concevoir des formulaires qui se déplacent entre les pages (panneaux) en appelant `xfa.host.pageUp` et `xfa.host.pageDown` méthodes. Ce script est placé dans la fonction `Click` et la variable `runAt` est défini sur `Both`. La raison de votre choix `Both` permet à Adobe Reader ou Acrobat (pour les formulaires rendus en tant que PDF) de modifier les pages sans passer par le serveur et les formulaires de HTML peuvent changer les pages en arrondissant les données au serveur. En d’autres termes, un formulaire est envoyé au service Forms et un formulaire est rendu en HTML avec la nouvelle page affichée.

Il est recommandé de ne pas donner aux variables de script et aux champs de formulaire les mêmes noms que les éléments, par exemple. Certains navigateurs Web, tels qu’Internet Explorer, peuvent ne pas initialiser une variable portant le même nom qu’un champ de formulaire, ce qui entraîne une erreur de script. Il est recommandé de donner aux champs de formulaire et aux variables de script différents noms.

Lors du rendu de formulaires de HTML qui contiennent à la fois des fonctionnalités de navigation de page et des scripts de formulaire (supposons, par exemple, qu’un script récupère les données de champ d’une base de données chaque fois que le formulaire est généré), assurez-vous que le script de formulaire se trouve dans l’événement form:calculate au lieu de form:readyevent.

Les scripts de formulaire situés dans l’événement form:ready ne sont exécutés qu’une seule fois lors du rendu initial du formulaire et ne sont pas exécutés pour les récupérations de page suivantes. En revanche, l’événement form:calculate est exécuté pour chaque navigation de page dans laquelle le formulaire est rendu.

>[!NOTE]
Dans un formulaire multipage, les modifications apportées par JavaScript à une page ne sont pas conservées si vous passez à une autre page.

Vous pouvez appeler des scripts personnalisés avant d’envoyer un formulaire. Cette fonctionnalité fonctionne sur tous les navigateurs disponibles. Cependant, il ne peut être utilisé que lorsque les utilisateurs affichent le HTML dont le `Output Type` définie sur `Form Body`. Cela ne fonctionnera pas lorsque la variable `Output Type` is `Full HTML`. Pour connaître les étapes de configuration de cette fonctionnalité, voir Configuration des formulaires dans l’aide à l’administration .

Vous devez d’abord définir une fonction de rappel appelée avant d’envoyer le formulaire, où le nom de la fonction est `_user_onsubmit`. On suppose que la fonction ne renvoie aucune exception ou que, dans ce cas, l’exception est ignorée. Il est recommandé de placer la fonction JavaScript dans la section head du fichier html ; vous pouvez toutefois le déclarer n’importe où avant la fin des balises de script qui incluent `xfasubset.js`.

Lorsque le serveur de formulaires effectue le rendu d’un fichier XDP contenant une liste déroulante, en plus de créer la liste déroulante, il crée également deux champs de texte masqués. Ces champs de texte stockent les données de la liste déroulante (l’un stocke le nom d’affichage des options et l’autre stocke la valeur des options). Par conséquent, chaque fois qu’un utilisateur envoie le formulaire, toutes les données de la liste déroulante sont envoyées. En supposant que vous ne souhaitiez pas envoyer autant de données à chaque fois, vous pouvez écrire un script personnalisé pour le désactiver. Par exemple : Le nom de la liste déroulante est `drpOrderedByStateProv` et est placé sous l’en-tête de sous-formulaire. Le nom de l’élément d’entrée de HTML sera `header[0].drpOrderedByStateProv[0]`. Le nom des champs masqués qui stockent et envoient les données de la liste déroulante porte les noms suivants : `header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]`

Vous pouvez désactiver ces éléments d’entrée de la manière suivante si vous ne souhaitez pas publier les données. `var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature function _user_onsubmit() { var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]"); elems[0].disabled = true; elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]"); elems[0].disabled = true; }`

```as3
header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]
```

```as3
var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature 
    function _user_onsubmit() { 
    var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]"); 
    elems[0].disabled = true; 
    elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]"); 
    elems[0].disabled = true; 
    }
```

## Sous-ensembles XFA {#xfa-subsets}

Lors de la création de conceptions de formulaire pour le rendu en tant que HTML, vous devez limiter votre script au sous-ensemble XFA pour les scripts en langage JavaScript.

Les scripts qui s’exécutent sur le client ou s’exécutent sur le client et le serveur doivent être écrits dans le sous-ensemble XFA. Les scripts qui s’exécutent sur le serveur peuvent utiliser le modèle de script XFA complet et également FormCalc. Pour plus d’informations sur l’utilisation de JavaScript, voir [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

Lors de l’exécution de scripts sur le client, seul le panneau actuel affiché peut utiliser le script ; par exemple, vous ne pouvez pas créer de script pour les champs situés dans le panneau A lorsque le panneau B est affiché. Lors de l’exécution de scripts sur le serveur, tous les panneaux sont accessibles.

Vous devez également faire attention lorsque vous utilisez des expressions SOM (Scripting Object Model) dans des scripts exécutés sur le client. Seuls un sous-ensemble simplifié d’expressions SOM est pris en charge par les scripts qui s’exécutent sur le client.

## Heure de l’événement {#event-timing}

Le sous-ensemble XFA définit les événements XFA associés aux événements de HTML. Il existe une légère différence de comportement dans le minutage des événements de calcul et de validation. Dans un navigateur web, un événement calculate complet est exécuté lorsque vous quittez un champ. Les événements de calcul ne sont pas automatiquement exécutés lorsque vous modifiez une valeur de champ. Vous pouvez forcer un événement calculate en appelant la variable `xfa.form.execCalculate` .

Dans un navigateur web, les événements de validation ne sont exécutés que lors de la sortie d’un champ ou de l’envoi d’un formulaire. Vous pouvez forcer un événement de validation à l’aide de la variable `xfa.form.execValidate` .

Forms affiché dans un navigateur web (par opposition à Adobe Reader ou Acrobat) est conforme au test null XFA (erreurs ou avertissements) pour les champs obligatoires.

* Si le test null génère une erreur et que vous quittez un champ sans spécifier de valeur, une zone de message s’affiche et vous êtes repositionné dans le champ après avoir cliqué sur OK.
* Si un test null génère un avertissement et que vous quittez un champ sans spécifier de valeur, vous êtes invité à cliquer sur OK ou Annuler, ce qui vous donne la possibilité de continuer sans spécifier de valeur ou de revenir au champ pour saisir une valeur.

Pour plus d’informations sur un test null, voir [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

## Bouton de formulaire {#form-buttons}

Cliquer sur un bouton Envoyer envoie les données de formulaire au service Forms et représente la fin du traitement du formulaire. Le `preSubmit` peut être défini pour s’exécuter sur le client ou le serveur. Le `preSubmit` s’exécute avant l’envoi du formulaire s’il est configuré pour s’exécuter sur le client. Sinon, la variable `preSubmit` s’exécute sur le serveur pendant l’envoi du formulaire. Pour plus d’informations sur la variable `preSubmit` , voir [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

Si aucun script client n’est associé à un bouton, les données sont envoyées au serveur, les calculs sont effectués sur le serveur et le formulaire de HTML est régénéré. Si un bouton contient un script côté client, les données ne sont pas envoyées au serveur et le script côté client est exécuté dans le navigateur web.

## Navigateur web HTML 4.0 {#html-4-0-web-browser}

Un navigateur web qui ne prend en charge que le HTML 4.0 ne peut pas prendre en charge le modèle de script du sous-ensemble XFA côté client. Lors de la création d’une conception de formulaire pour fonctionner dans le HTML 4.0 et MSDHTML ou CSS2, un script marqué pour s’exécuter sur le client s’exécute sur le serveur. Supposons, par exemple, qu’un utilisateur clique sur un bouton situé sur un formulaire affiché dans un navigateur web HTML 4.0. Dans ce cas, les données de formulaire sont envoyées au serveur sur lequel le script client est exécuté.

Il est recommandé de placer la logique de formulaire dans les événements calculate, qui s’exécutent sur le serveur dans le HTML 4.0 et sur le client pour le HTML MSDHTML ou CSS2.

## Maintenir les modifications de présentation {#maintaining-presentation-changes}

Lorsque vous passez d’une page de HTML à l’autre (panneaux), seul l’état des données est conservé. Les paramètres tels que la couleur d’arrière-plan ou les paramètres de champ obligatoires ne sont pas conservés (s’ils sont différents des paramètres initiaux). Pour conserver l’état de présentation, vous devez créer des champs (généralement masqués) qui représentent l’état de présentation des champs. Si vous ajoutez un script à la variable `Calculate` qui modifie la présentation en fonction des valeurs de champ masquées, vous pouvez conserver l’état de la présentation lorsque vous passez d’une page de HTML à l’autre (panneaux).

Le script suivant conserve la fonction `fillColor` d’un champ en fonction de la valeur de `hiddenField`. Supposons que ce script se trouve dans la variable `Calculate` .

```as3
     If (hiddenField.rawValue == 1) 
         this.fillColor = "255,0,0" 
     else 
         this.fillColor = "0,255,0"
```

>[!NOTE]
Les objets statiques ne s’affichent pas dans un HTML rendu lorsqu’ils sont imbriqués dans une cellule d’un tableau. Par exemple, un cercle et un rectangle imbriqués dans une cellule de tableau ne s’affichent pas dans un formulaire de HTML de rendu. Toutefois, ces mêmes objets statiques s’affichent correctement lorsqu’ils sont situés en dehors du tableau.

## Signature numérique de HTMLS {#digitally-signing-html-forms}

Vous ne pouvez pas signer un formulaire de HTML contenant un champ de signature numérique si le formulaire est rendu comme l’une des transformations de HTML suivantes :

* AHTML
* HTML4
* StaticHTML
* NoScriptXHTML

Pour plus d’informations sur la signature numérique d’un document, voir [Signature numérique et certification de documents](/help/forms/developing/digitally-signing-certifying-documents.md)

## Rendu d’un formulaire XHTML conforme aux directives d’accessibilité {#rendering-an-accessibility-guidelines-compliant-xhtml-form}

Vous pouvez générer un formulaire de HTML complet conforme aux directives d’accessibilité. En d’autres termes, le formulaire est rendu dans des balises de HTML complètes, contrairement au formulaire de HTML généré dans des balises de corps (et non dans une page de HTML complète).

## Validation des données de formulaire {#validating-form-data}

Il est recommandé de limiter l’utilisation des règles de validation pour les champs de formulaire lors du rendu du formulaire en tant que formulaire de HTML. Certaines règles de validation peuvent ne pas être prises en charge pour les formulaires de HTML. Par exemple, lorsqu’un modèle de validation MM-JJ-AAAA est appliqué à une `Date/Time` qui se trouve dans une conception de formulaire rendue sous la forme d’un formulaire de HTML, elle ne fonctionne pas correctement, même si la date est saisie correctement. Cependant, ce modèle de validation fonctionne correctement pour les formulaires rendus en tant que PDF.

>[!NOTE]
Pour plus d’informations sur le service Forms, voir [Référence des services pour AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Résumé des étapes {#summary-of-steps}

Pour générer un HTML de formulaire, procédez comme suit :

1. Inclure les fichiers de projet.
1. Créez un objet API client Forms.
1. Définissez les options d’exécution HTML.
1. Générer un HTML de formulaire.
1. Ecrivez le flux de données de formulaire dans le navigateur Web client.

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services Web, veillez à inclure les fichiers proxy.

**Création d’un objet API client Forms**

Avant de pouvoir importer des données par programmation dans une API formClient de PDF, vous devez créer un client de service Form Data Integration . Lors de la création d’un client de service, vous définissez les paramètres de connexion requis pour appeler un service.

**Définition des options d’exécution de HTML**

Vous définissez les options d’exécution de HTML lors du rendu d’un formulaire de HTML. Par exemple, vous pouvez ajouter une barre d’outils à un formulaire de HTML pour permettre aux utilisateurs de sélectionner les pièces jointes situées sur l’ordinateur client ou de récupérer les pièces jointes générées avec le formulaire de HTML. Par défaut, une barre d’outils de HTML est désactivée. Pour ajouter une barre d’outils à un formulaire de HTML, vous devez définir par programmation les options d’exécution. Par défaut, une barre d’outils de HTML se compose des boutons suivants :

* `Home`: Fournit un lien vers la racine Web de l’application.
* `Upload`: Fournit une interface utilisateur pour sélectionner les fichiers à joindre au formulaire actif.
* `Download`: Fournit une interface utilisateur pour afficher les fichiers joints.

Lorsqu’une barre d’outils de HTML s’affiche sur un formulaire de HTML, l’utilisateur peut sélectionner un maximum de dix fichiers à envoyer avec les données de formulaire. Une fois les fichiers envoyés, le service Forms peut les récupérer.

Lors du rendu d’un formulaire en tant que HTML, vous pouvez spécifier une valeur agent-utilisateur. Une valeur agent-utilisateur fournit des informations sur le navigateur et le système. Il s’agit d’une valeur facultative que vous pouvez transmettre à une valeur de chaîne vide. Le rapport Rendu d’un formulaire de HTML à l’aide du démarrage rapide de l’API Java indique comment obtenir une valeur d’agent utilisateur et l’utiliser pour générer un formulaire en tant que HTML.

Les URL HTTP vers l’emplacement où les données de formulaire sont publiées peuvent être spécifiées en définissant l’URL cible à l’aide de l’API client du service Forms ou peuvent être spécifiées dans le bouton Envoyer contenu dans la conception de formulaire XDP. Si l’URL cible est spécifiée dans la conception de formulaire, ne définissez pas de valeur à l’aide de l’API client du service Forms.

>[!NOTE]
Le rendu d’un formulaire de HTML avec une barre d’outils est facultatif.

>[!NOTE]
Si vous générez un formulaire AHTML, il est recommandé de ne pas ajouter de barre d’outils au formulaire.

**Rendu d’un formulaire de HTML**

Pour générer un formulaire de HTML, vous devez spécifier une conception de formulaire créée dans Designer et enregistrée en tant que fichier XDP. Vous devez également sélectionner un type de transformation de HTML. Par exemple, vous pouvez spécifier le type de transformation de HTML qui effectue le rendu d’un HTML dynamique pour Internet Explorer 5.0 ou version ultérieure.

Le rendu d’un formulaire de HTML nécessite également des valeurs, telles que des valeurs URI requises pour effectuer le rendu d’autres types de formulaire.

**Écrire le flux de données de formulaire dans le navigateur Web client**

Lorsque le service Forms génère un formulaire de HTML, il renvoie un flux de données de formulaire que vous devez écrire dans le navigateur Web client. Lorsqu’il est écrit dans le navigateur Web client, le formulaire de HTML est visible par l’utilisateur.

**Voir également**

[Rendu d’un formulaire comme HTML à l’aide de l’API Java](#render-a-form-as-html-using-the-java-api)

[Rendu d’un formulaire en tant que HTML à l’aide de l’API du service Web](#render-a-form-as-html-using-the-web-service-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Démarrages rapides de l’API Forms Service](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendu des PDF forms interactifs](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Forms de HTML de rendu avec barres d’outils personnalisées](/help/forms/developing/rendering-html-forms-custom-toolbars.md)

[Création d’applications web qui renvoient Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

## Rendu d’un formulaire comme HTML à l’aide de l’API Java {#render-a-form-as-html-using-the-java-api}

Rendre un formulaire de HTML à l’aide de l’API Forms (Java) :

1. Inclure les fichiers de projet

   Incluez les fichiers JAR client, tels que adobe-forms-client.jar, dans le chemin de classe de votre projet Java.

1. Création d’un objet API client Forms

   * Créez un objet `ServiceClientFactory` qui contient des propriétés de connexion.
   * Créez un `FormsServiceClient` en utilisant son constructeur et en transmettant l’objet `ServiceClientFactory` .

1. Définition des options d’exécution de HTML

   * Créez un `HTMLRenderSpec` en utilisant son constructeur.
   * Pour générer un HTML de formulaire avec une barre d’outils, appelez la méthode `HTMLRenderSpec` de `setHTMLToolbar` et transmettre une `HTMLToolbar` valeur d’énumération. Par exemple, pour afficher une barre d’outils de HTML verticale, transmettez `HTMLToolbar.Vertical`.
   * Pour définir les paramètres régionaux du HTML, appelez la méthode `HTMLRenderSpec` de `setLocale` et transmettez une valeur string qui spécifie la valeur locale. (Il s’agit d’un paramètre facultatif.)
   * Pour effectuer le rendu du HTML dans des balises de HTML complètes, appelez la méthode `HTMLRenderSpec` de `setOutputType` méthode et transmission `OutputType.FullHTMLTags`. (Il s’agit d’un paramètre facultatif.)

   >[!NOTE]
   Forms ne s’affiche pas correctement en HTML lorsque la variable `StandAlone` option est `true` et le `ApplicationWebRoot` référence un serveur autre que le serveur d’applications J2EE hébergeant AEM Forms (le `ApplicationWebRoot` est spécifiée à l’aide de la propriété `URLSpec` qui est transmis à l’objet `FormsServiceClient` de `(Deprecated) renderHTMLForm` ). Lorsque la variable `ApplicationWebRoot`* est un autre serveur de celui qui héberge AEM Forms, la valeur de l’URI racine Web dans Administration Console doit être définie comme valeur de l’URI de l’application Web du formulaire. Pour ce faire, connectez-vous à la console d’administration, cliquez sur Services > Forms, puis définissez l’URI racine Web sur https://server-name:port/FormServer. Enregistrez ensuite vos paramètres.*

1. Rendu d’un formulaire de HTML

   Appeler la variable `FormsServiceClient` de `(Deprecated) renderHTMLForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` valeur enum qui spécifie le type de préférence de HTML. Par exemple, pour effectuer le rendu d’un formulaire de HTML compatible avec le HTML dynamique pour Internet Explorer 5.0 ou version ultérieure, spécifiez `TransformTo.MSDHTML`.
   * A `com.adobe.idp.Document` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez un `com.adobe.idp.Document` .
   * Le `HTMLRenderSpec` qui stocke les options d’exécution de HTML.
   * Une valeur string qui spécifie la variable `HTTP_USER_AGENT` valeur d’en-tête ; par exemple, `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * A `URLSpec` qui stocke les valeurs URI requises pour générer un formulaire de HTML.
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire.

   Le `(Deprecated) renderHTMLForm` renvoie une `FormsResult` contenant un flux de données de formulaire pouvant être écrit dans le navigateur Web client.

1. Écrire le flux de données de formulaire dans le navigateur Web client

   * Créez un `com.adobe.idp.Document` en appelant le `FormsResult` object ‘s `getOutputContent` .
   * Obtention du type de contenu de la variable `com.adobe.idp.Document` en appelant son objet `getContentType` .
   * Définissez la variable `javax.servlet.http.HttpServletResponse` type de contenu de l’objet en appelant sa propriété `setContentType` et transmettre le type de contenu de la méthode `com.adobe.idp.Document` .
   * Créez un `javax.servlet.ServletOutputStream` objet utilisé pour écrire le flux de données de formulaire dans le navigateur Web client en appelant la fonction `javax.servlet.http.HttpServletResponse` de `getOutputStream` .
   * Créez un `java.io.InputStream` en appelant le `com.adobe.idp.Document` de `getInputStream` .
   * Créez un tableau d’octets et renseignez-le avec le flux de données de formulaire en appelant la fonction `InputStream` de `read` et transmission du tableau d’octets en tant qu’argument.
   * Appeler la variable `javax.servlet.ServletOutputStream` de `write` pour envoyer le flux de données de formulaire au navigateur web client. Transmettez le tableau d’octets au `write` .

**Voir également**

[Rendu de Forms en tant que HTML](#rendering-forms-as-html)

[Démarrage rapide (mode SOAP) : Rendu d’un formulaire de HTML à l’aide de l’API Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-using-the-java-api)

[Inclusion des fichiers de bibliothèque Java d’AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendu d’un formulaire en tant que HTML à l’aide de l’API du service Web {#render-a-form-as-html-using-the-web-service-api}

Rendre un formulaire de HTML à l’aide de l’API Forms (service Web) :

1. Inclure les fichiers de projet

   * Créez des classes proxy Java qui utilisent le WSDL du service Forms.
   * Incluez les classes proxy Java dans le chemin de classe.

1. Création d’un objet API client Forms

   Créez un `FormsService` et définissez les valeurs d’authentification.

1. Définition des options d’exécution de HTML

   * Créez un `HTMLRenderSpec` en utilisant son constructeur.
   * Pour générer un HTML de formulaire avec une barre d’outils, appelez la méthode `HTMLRenderSpec` de `setHTMLToolbar` et transmettre une `HTMLToolbar` valeur d’énumération. Par exemple, pour afficher une barre d’outils de HTML verticale, transmettez `HTMLToolbar.Vertical`.
   * Pour définir les paramètres régionaux du HTML, appelez la méthode `HTMLRenderSpec` de `setLocale` et transmettez une valeur string qui spécifie la valeur locale. Pour plus d’informations, voir [Référence de l’API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Pour effectuer le rendu du HTML dans des balises de HTML complètes, appelez la méthode `HTMLRenderSpec` de `setOutputType` méthode et transmission `OutputType.FullHTMLTags`.

   >[!NOTE]
   Forms ne s’affiche pas correctement en HTML lorsque la variable `StandAlone` option est `true` et le `ApplicationWebRoot` référence un serveur autre que le serveur d’applications J2EE hébergeant AEM Forms (le `ApplicationWebRoot` est spécifiée à l’aide de la propriété `URLSpec` qui est transmis à l’objet `FormsServiceClient` de `(Deprecated) renderHTMLForm` ). Lorsque la variable `ApplicationWebRoot`* est un autre serveur de celui qui héberge AEM Forms, la valeur de l’URI racine Web dans Administration Console doit être définie comme valeur de l’URI de l’application Web du formulaire. Pour ce faire, connectez-vous à la console d’administration, cliquez sur Services > Forms, puis définissez l’URI racine Web sur https://server-name:port/FormServer. Enregistrez ensuite vos paramètres. *

1. Rendu d’un formulaire de HTML

   Appeler la variable `FormsService` de `(Deprecated) renderHTMLForm` et transmettez les valeurs suivantes :

   * Une valeur string qui spécifie le nom de la conception de formulaire, y compris l’extension du nom de fichier. Si vous référencez une conception de formulaire faisant partie d’une application Forms, veillez à spécifier le chemin complet, tel que `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` valeur enum qui spécifie le type de préférence de HTML. Par exemple, pour effectuer le rendu d’un formulaire de HTML compatible avec le HTML dynamique pour Internet Explorer 5.0 ou version ultérieure, spécifiez `TransformTo.MSDHTML`.
   * A `BLOB` contenant les données à fusionner avec le formulaire. Si vous ne souhaitez pas fusionner des données, transmettez `null`. (Voir [Préremplissage de Forms avec des dispositions souple](/help/forms/developing/prepopulating-forms-flowable-layouts.md#prepopulating-forms-with-flowable-layouts).)
   * Le `HTMLRenderSpec` qui stocke les options d’exécution de HTML.
   * Une valeur string qui spécifie la variable `HTTP_USER_AGENT` valeur d’en-tête ; par exemple, `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Vous pouvez transmettre une chaîne vide si vous ne souhaitez pas définir cette valeur.
   * A `URLSpec` qui stocke les valeurs URI requises pour générer un formulaire de HTML. (Voir [Spécification de valeurs URI](/help/forms/developing/rendering-interactive-pdf-forms.md).)
   * A `java.util.HashMap` qui stocke les pièces jointes. Ce paramètre est facultatif et vous pouvez spécifier `null` si vous ne souhaitez pas joindre de fichiers au formulaire. (Voir [Joindre des fichiers au formulaire](/help/forms/developing/rendering-interactive-pdf-forms.md).)
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la méthode . Cette valeur de paramètre stocke le formulaire rendu.
   * Une valeur vide `com.adobe.idp.services.holders.BLOBHolder` qui est renseigné par la méthode . Ce paramètre stocke les données XML de sortie.
   * Une valeur vide `javax.xml.rpc.holders.LongHolder` qui est renseigné par la méthode . Cet argument stocke le nombre de pages dans le formulaire.
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la méthode . Cet argument stocke la valeur du paramètre régional.
   * Une valeur vide `javax.xml.rpc.holders.StringHolder` qui est renseigné par la méthode . Cet argument stocke la valeur de rendu de HTML utilisée.
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

[Rendu de Forms en tant que HTML](#rendering-forms-as-html)

[Appel d’AEM Forms à l’aide du codage Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
