---
title: Incorporation d’un formulaire adaptatif dans une page web externe
seo-title: Embed adaptive form in external web page
description: Découvrez comment incorporer un formulaire adaptatif dans une page Web externe
seo-description: Learn how to embed an adaptive form in an external HTML web page
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
feature: Adaptive Forms
exl-id: 84a46197-9933-4b94-a8e3-e7baf9c644b1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 87%

---

# Incorporation d’un formulaire adaptatif dans une page web externe{#embed-adaptive-form-in-external-web-page}

Découvrez comment incorporer un formulaire adaptatif dans une page Web externe

Vous pouvez [Incorporer le formulaire adaptatif dans AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) ou une page web hébergée en dehors d’AEM. Le formulaire adaptatif incorporé est entièrement fonctionnel et les utilisateurs peuvent le remplir et le soumettre sans quitter la page. Il permet à l’utilisateur de rester dans le contexte des autres éléments de la page Web et d’interagir simultanément avec le formulaire.

## Conditions préalables {#prerequisites}

Effectuez les étapes suivantes avant d’inclure un formulaire adaptatif dans un site Web externe : :

* Publiez le formulaire adaptatif sur une instance de publication AEM.
* Créez ou identifiez une page Web sur votre site Web pour héberger le formulaire adaptatif. Assurez-vous que la page web peut [lire les fichiers jQuery à partir d’un réseau CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) ou dispose d’une copie locale du fichier jQuery incorporé. jQuery est nécessaire pour effectuer le rendu d’un formulaire adaptatif.
* Lorsque le serveur AEM et la page Web se trouvent dans des domaines différents, procédez comme indiqué dans la section ci-dessous [pour permettre à AEM Forms de diffuser des formulaires adaptatifs sur un site interdomaines](#cross-domain-sites).
* [Configuration du proxy inverse](#reveseproxy) pour activer la communication entre la page externe et le serveur AEM Forms.

## Incorporation d’un formulaire adaptatif {#embed-adaptive-form}

Vous pouvez incorporer un formulaire adaptatif en insérant quelques lignes de code JavaScript dans la page web. L’API dans le code envoie une requête HTTP au serveur AEM pour les ressources de formulaire adaptatif et injecte le formulaire adaptatif dans le conteneur de formulaire spécifié. Voici un exemple de code pour incorporer un formulaire adaptatif à une page externe. N’utilisez pas le code tel qu’il se trouve dans un environnement de production. Personnalisez le code pour l’adapter à votre site web, comme avec un iFrame pour les sites web qui utilisent leur propre version de jQuery. L’utilisation d’iFrame permet d’éviter les conflits dans les versions jQuery :


1. Incorporez le code suivant à une page web de votre site web :

   ```html
   <!doctype html>
   <html>
   <head>
    <title>This is the title of the webpage!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
   </head>
   <body>
   <div class="customafsection"/>
   <p>This section is replaced with the adaptive form.</p>
   
    <script>
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
        // options.path refers to the publish URL of the adaptive form
        // For Example: http:myserver:4503/content/forms/af/ABC, where ABC is the adaptive form
        // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path 
        var path = options.path;
        path += "/jcr:content/guideContainer.html";
        $.ajax({
            url  : path ,
            type : "GET",
            data : {
                // Set the wcmmode to be disabled
                wcmmode : "disabled"
                // Set the data reference, if any
               // "dataRef": options.dataRef
                // Specify a different theme for the form object
              //  "themeOverride" : options.themepath
            },
            async: false,
            success: function (data) {
                // If jquery is loaded, set the inner html of the container
                // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                // For example: document.getElementById().innerHTML
                if(window.$ && options.CSS_Selector){
                    // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
                    $(options.CSS_Selector).html(data);
                }
            },
            error: function (data) {
                // any error handler
            }
        });
    } else {
        if (typeof(console) !== "undefined") {
            console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
        }
    }
    }(options);
   
    </script>
   </body>
   </html>
   ```

1. Dans le code incorporé :

   * Remplacez la valeur de la variable `options.path` par le chemin d’accès de l’URL de publication du formulaire adaptatif. Si le serveur AEM s’exécute sur un chemin de contexte, assurez-vous que l’URL inclut ce chemin. Par exemple, le code et le formulaire adaptatif ci-dessus résident sur le même serveur AEM Forms, l’exemple utilise donc le chemin de contexte du formulaire adaptatif /content/forms/af/locbasic.html.
   * Remplacez `options.dataRef` par les attributs à transmettre avec l’URL. Vous pouvez utiliser la variable dataref pour [pré-remplir un formulaire adaptatif](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Remplacez `options.themePath` par le chemin d’accès à un thème différent de celui configuré dans le formulaire adaptatif. Vous pouvez également spécifier le chemin d’accès au thème à l’aide de l’attribut de requête.
   * `CSS_Selector` est le sélecteur CSS du conteneur de formulaire dans lequel le formulaire adaptatif est incorporé. Par exemple, la classe CSS .customafsection est le sélecteur CSS dans l’exemple ci-dessus.

Le formulaire adaptatif est incorporé dans la page Web. Vous pouvez observer ce qui suit dans le formulaire adaptatif incorporé :

* L’en-tête et le pied de page du formulaire adaptatif d’origine ne sont pas compris dans le formulaire incorporé.
* Les brouillons et les formulaires envoyés sont disponibles dans l’onglet Brouillons et envois du portail des formulaires.
* L’action Envoyer configurée sur le formulaire adaptatif d’origine est conservée dans le formulaire incorporé.
* Les règles de formulaire adaptatif sont conservées et entièrement fonctionnelles dans le formulaire incorporé.
* Le ciblage d’expérience et les tests A/B configurés dans le formulaire adaptatif d’origine ne fonctionnent pas dans le formulaire incorporé.
* Si Adobe Analytics est configuré sur le formulaire d’origine, les données d’analyse sont capturées dans le serveur Adobe Analytics. En revanche, il ne sera pas disponible dans le rapport d’analyse des formulaires.

## Configuration du proxy inverse  {#reveseproxy}

La page Web externe qui incorpore le formulaire adaptatif envoie les requêtes au serveur AEM, qui se trouve généralement derrière le pare-feu dans un réseau privé. Pour garantir que les requêtes sont dirigées de manière sécurisée vers le serveur AEM, il est recommandé de configurer un serveur de proxy inverse.

Examinons un exemple de la manière dont vous pouvez configurer un serveur de proxy inverse Apache 2.4 sans répartiteur. Dans cet exemple, vous allez héberger le serveur AEM avec le chemin de contexte `/forms` et mapper `/forms` pour le proxy inverse. Cela garantit que toute requête pour `/forms` sur le serveur Apache est redirigée vers une instance AEM. Cette topologie permet de réduire le nombre de règles au niveau de la couche du Dispatcher, car toute requête précédée de `/forms` dirige vers le serveur AEM.

1. Ouvrez le fichier de configuration `httpd.conf` et supprimez les commentaires des lignes de code suivantes. Vous pouvez également ajouter ces lignes de code dans le fichier.

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Configurez les règles de proxy en ajoutant les lignes de code suivantes dans le fichier de configuration `httpd-proxy.conf`.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Remplacez `[AEM_Instance]` par l’URL de publication du serveur AEM dans les règles.

Si vous ne montez pas le serveur AEM sur un chemin de contexte, les règles de proxy au niveau de la couche Apache sont les suivantes :

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Si vous configurez une autre topologie, assurez-vous de placer les URL d’envoi, de pré-remplissage et autres sur la liste autorisée au niveau de la couche du Dispatcher.

## Bonnes pratiques {#best-practices}

Lorsque vous incorporez un formulaire adaptatif dans une page Web, prenez en compte les meilleures pratiques suivantes :

* Assurez-vous que les règles de style définies dans la page Web CSS ne sont pas en conflit avec l’objet de formulaire CSS. Pour éviter les conflits, vous pouvez réutiliser la page Web CSS dans le thème de formulaire adaptatif en utilisant la bibliothèque client AEM. Pour plus d’informations sur l’utilisation de la bibliothèque client dans les thèmes de formulaire adaptatif, voir [Thèmes dans AEM Forms](/help/forms/using/themes.md).
* Assurez-vous que le conteneur du formulaire dans la page Web utilise toute la largeur de la fenêtre. Cela permet aux règles CSS configurées pour les appareils mobiles de fonctionner sans aucune modification. Si le conteneur de formulaire ne prend pas toute la largeur de la fenêtre, vous devez écrire un CSS personnalisé pour que le formulaire s’adapte aux différents appareils mobiles.
* Utilisation  [getData](https://helpx.adobe.com/fr/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API pour obtenir la représentation XML ou JSON des données de formulaire dans le client.
* Utilisation [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API pour décharger le formulaire adaptatif du DOM HTML.
* Configurez l’en-tête access-control-origin lors de l’envoi de la réponse à partir du serveur AEM.

## Activer AEM Forms pour diffuser des formulaires adaptatifs vers un site interdomaines  {#cross-domain-sites}

1. Sur l’instance de publication AEM, accédez au gestionnaire de la console web AEM à l’adresse `http://[server]:[port]/system/console/configMgr`.
1. Recherchez et ouvrez le **Référent Apache Sling** Configuration des filtres.
1. Dans le champ **Hôtes autorisés**, spécifiez le domaine dans lequel la page Web se trouve. Cette opération permet à l’hôte de créer des requêtes POST vers le serveur AEM. Vous pouvez également utiliser l’expression régulière pour spécifier une série de domaines d’application externes.
