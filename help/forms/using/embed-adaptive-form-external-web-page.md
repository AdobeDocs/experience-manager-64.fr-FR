---
title: Incorporation d’un formulaire adaptatif dans une page Web externe
seo-title: Incorporation d’un formulaire adaptatif dans une page Web externe
description: Découvrez comment incorporer un formulaire adaptatif dans une page Web externe
seo-description: Découvrez comment incorporer un formulaire adaptatif dans une page Web HTML externe
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
translation-type: tm+mt
source-git-commit: a3e7cd30ba6933e6f36734d3b431db41365b6e20
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 54%

---


# Incorporation d’un formulaire adaptatif dans une page Web externe{#embed-adaptive-form-in-external-web-page}

Découvrez comment incorporer un formulaire adaptatif dans une page Web externe

You can [Embed adaptive form in AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) page or a web page hosted outside AEM. Le formulaire adaptatif incorporé est entièrement fonctionnel et les utilisateurs peuvent le remplir et le soumettre sans quitter la page. Il permet à l’utilisateur de rester dans le contexte des autres éléments de la page Web et d’interagir simultanément avec le formulaire.

## Conditions préalables {#prerequisites}

Effectuez les étapes suivantes avant d’incorporer un formulaire adaptatif à un site Web externe :

* Publiez le formulaire adaptatif sur une instance de publication AEM.
* Créez ou identifiez une page Web sur votre site Web pour héberger le formulaire adaptatif. Ensure that the webpage can [read jQuery files from a CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) or has a local copy of the jQuery embeded. jQuery est nécessaire pour effectuer le rendu d’un formulaire adaptatif.
* Lorsque le serveur AEM et la page Web se trouvent dans des domaines différents, procédez comme indiqué dans la section ci-dessous [pour permettre à AEM Forms de diffuser des formulaires adaptatifs sur un site interdomaines](#cross-domain-sites).
* [Configurez un proxy](#reveseproxy) inverse pour activer la communication entre la page externe et le serveur AEM Forms.

## Incorporation d’un formulaire adaptatif {#embed-adaptive-form}

Vous pouvez incorporer un formulaire adaptatif en insérant quelques lignes de code JavaScript dans la page Web. L’API dans le code envoie une requête HTTP au serveur AEM pour les ressources de formulaire adaptatif et injecte le formulaire adaptatif dans le conteneur de formulaire spécifié. Voici un exemple de code pour incorporer un formulaire adaptatif à une page externe. N&#39;utilisez pas le code tel qu&#39;il se trouve dans un environnement de production. Personnalisez le code en fonction de votre site Web, comme l’utilisation d’un iFrame pour les sites Web qui utilisent leur propre version de jQuery. L’utilisation d’iFrame permet d’éviter les conflits dans les versions jQuery :


1. Incorporez le code suivant à une page Web de votre site Web :

   ```
   
   
<!doctype html>
<html>
  <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Voici le titre de la page Web !</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  </head>
  <body>
  <div class="customafsection"/>
    <p>Cette section est remplacée par le formulaire adaptatif.</p>


    &lt;script>options
    var = {path:&quot;/content/forms/af/locbasic.html&quot;, dataRef:&quot;&quot;, the epath:&quot;&quot;, CSS_Selector:&quot;.customafsection&quot;};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
    / options.path fait référence à l&#39;URL de publication le formulaire
    adaptatif// Par exemple : http:myserver:4503/content/forms/af/ABC, où ABC est le formulaire
    adaptatif// Remarque : Si AEM serveur s’exécute sur un chemin de contexte, l’URL du formulaire adaptatif doit contenir le chemin d’accès de la
    variable de contexte = options.path;
    path += &quot;/jcr:content/guideContainer.html&quot;;
    $.ajax({
    url : path,
    type : &quot;GET&quot;,
    data : {
    // Définissez le mode Wcmmode comme
    désabledwcmmode : &quot;disabled&quot;
    // Définissez la référence de données, le cas échéant
    // &quot;dataRef&quot; : options.dataRef
    // Spécifiez un thème différent pour l’objet
    de formulaire// &quot;themeOverride&quot; : options.themepath
    },
    async : false,
    succès : fonction (données) {
    // Si jquery est chargé, définissez le code html interne du conteneur
    // Si jquery n&#39;est pas chargé, utilisez les API fournies par le document pour définir le code HTML interne, mais ces API n&#39;évalueraient pas la balise de script dans le code HTML conformément à la spécification
    HTML5// Par exemple : document.getElementById().
    innerHTMLif(window.$ &amp;&amp; options.CSS_Selector){
    // L’API HTML de jquery extrait les balises, met à jour le DOM et évalue le code incorporé dans la balise de script.
    $(options.CSS_Selector).html(data);
    }
    },
    erreur : function (data) {
    // tout gestionnaire
    d&#39;erreurs}
    });
    } else {
    if (typeof(console) !== &quot;undefined&quot;) {
    console.log(&quot;Path of Adaptive Form not specified to loadAdaptiveForm&quot;);
    }
    }
    }(options);
    
    &lt;/script>
</body>
</html>
   ```

1. Dans le code incorporé :

   * Change value of the `options.path` variable with the path of the publish URL of the adaptive form. Si le serveur AEM s’exécute sur un chemin de contexte, assurez-vous que l’URL inclut ce chemin. Par exemple, le code et le formulaire adaptatif ci-dessus résident sur le même serveur AEM Forms, l’exemple utilise donc le chemin de contexte du formulaire adaptatif /content/forms/af/locbasic.html.
   * Remplacez `options.dataRef` par les attributs à transmettre avec l’URL. Vous pouvez utiliser la variable dataref pour [pré-remplir un formulaire adaptatif](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Remplacez `options.themePath` par le chemin d’accès à un thème différent de celui configuré dans le formulaire adaptatif. Vous pouvez également spécifier le chemin d’accès au thème à l’aide de l’attribut de requête.
   * `CSS_Selector` est le sélecteur CSS du conteneur de formulaire dans lequel le formulaire adaptatif est incorporé. Par exemple, la classe css .customafsection est le sélecteur CSS de l’exemple ci-dessus.

Le formulaire adaptatif est incorporé dans la page Web. Vous pouvez observer ce qui suit dans le formulaire adaptatif incorporé :

* L’en-tête et le pied de page du formulaire adaptatif d’origine ne sont pas compris dans le formulaire incorporé.
* Les brouillons et les formulaires envoyés sont disponibles dans l’onglet Brouillons et envois du portail des formulaires.
* L’action Envoyer configurée sur le formulaire adaptatif d’origine est conservée dans le formulaire incorporé.
* Les règles de formulaire adaptatif sont conservées et entièrement fonctionnelles dans le formulaire incorporé.
* Le ciblage d’expérience et les tests A/B configurés dans le formulaire adaptatif d’origine ne fonctionnent pas dans le formulaire incorporé.
* Si Adobe Analytics est configuré sur le formulaire d’origine, les données d’analyse sont capturées dans le serveur Adobe Analytics. En revanche, il ne sera pas disponible dans le rapport d’analyse des formulaires.

## Intervertir le proxy  {#reveseproxy}

La page Web externe qui incorpore le formulaire adaptatif envoie les requêtes au serveur AEM, qui se trouve généralement derrière le pare-feu dans un réseau privé. Pour garantir que les requêtes sont dirigées de manière sécurisée vers le serveur AEM, il est recommandé de configurer un serveur de proxy inverse.

Examinons un exemple de la manière dont vous pouvez configurer un serveur de proxy inverse Apache 2.4 sans répartiteur. In this example, you will host the AEM server with `/forms` context path and map `/forms` for the reverse proxy. It ensures that any request for `/forms` on Apache server are directed to the AEM instance. This topology helps reduces the number of rules at the dispatcher layer as all request prefixed with `/forms` route to the AEM server.

1. Ouvrez le fichier de configuration `httpd.conf` et supprimez les commentaires des lignes de code suivantes. Vous pouvez également ajouter ces lignes de code dans le fichier.

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Set up proxy rules by adding the following lines of code in the `httpd-proxy.conf` configuration file.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Replace `[AEM_Instance`] with the AEM server publish URL in the rules.

Si vous ne montez pas le serveur AEM sur un chemin de contexte, les règles de proxy de la couche Apache seront les suivantes :

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
>Si vous définissez une autre topologie, veillez à ajouter les URL d’envoi, de préremplissage et autres à la liste autorisée au niveau du calque du répartiteur.

## Bonnes pratiques {#best-practices}

Lorsque vous incorporez un formulaire adaptatif dans une page Web, prenez en compte les meilleures pratiques suivantes :

* Assurez-vous que les règles de style définies dans la page Web CSS ne sont pas en conflit avec l’objet de formulaire CSS. Pour éviter les conflits, vous pouvez réutiliser la page Web CSS dans le thème de formulaire adaptatif en utilisant la bibliothèque client AEM. Pour plus d’informations sur l’utilisation de la bibliothèque client dans les thèmes de formulaire adaptatif, voir [Thèmes dans AEM Forms](/help/forms/using/themes.md).
* Assurez-vous que le conteneur du formulaire dans la page Web utilise toute la largeur de la fenêtre. Cela permet aux règles CSS configurées pour les appareils mobiles de fonctionner sans aucune modification. Si le conteneur de formulaire ne prend pas toute la largeur de la fenêtre, vous devez écrire un CSS personnalisé pour que le formulaire s’adapte aux différents appareils mobiles.
* Use  [getData](https://helpx.adobe.com/fr/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API to get the XML or JSON representation of form data in client.
* Use [unloadAdaptiveForm](https://helpx.adobe.com/fr/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API to unload the adaptive form from HTML DOM.
* Configurez l’en-tête access-control-origine lors de l’envoi d’une réponse du serveur AEM.

## Activer AEM Forms pour diffuser des formulaires adaptatifs vers un site interdomaines  {#cross-domain-sites}

1. Sur AEM instance d’auteur, accédez à AEM Web Console Configuration Manager à l’adresse `http://[server]:[port]/system/console/configMgr`.
1. Locate and open the **Apache Sling Referrer** Filter configuration.
1. Dans le champ **Hôtes autorisés**, spécifiez le domaine dans lequel la page Web se trouve. Cette opération permet à l’hôte de créer des requêtes POST vers le serveur AEM. Vous pouvez également utiliser l’expression régulière pour spécifier une série de domaines d’application externes.