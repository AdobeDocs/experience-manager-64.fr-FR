---
title: Assistant de Handlebars SCF
seo-title: SCF Handlebars Helpers
description: Méthodes Handlebars Helper pour faciliter le travail avec SCF
seo-description: Handlebars Helper methods to facilitate work with SCF
uuid: 9c514199-871e-4b68-8147-2052d2eeda15
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8b6c1697-d693-41f4-8337-f41658465107
exl-id: 66045e67-4d33-4c0c-81d7-d4287ed68ccc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1550'
ht-degree: 8%

---

# Assistant de Handlebars SCF {#scf-handlebars-helpers}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

| **[⇐ Notions fondamentales sur les fonctionnalités](essentials.md)** | **[⇒ de personnalisation côté serveur](server-customize.md)** |
|---|---|
|  | **[⇒ de personnalisation côté client](client-customize.md)** |

Handlebars Helpers (helpers) sont des méthodes appelables à partir des scripts Handlebars pour faciliter l’utilisation des composants SCF.

L’implémentation comprend une définition côté client et côté serveur. Il est également possible pour les développeurs de créer des assistants personnalisés.

Les assistants SCF personnalisés fournis avec AEM Communities sont définis dans la variable [bibliothèque cliente](../../help/sites-developing/clientlibs.md):

* /etc/clientlibs/social/commons/scf/helpers.js

>[!NOTE]
>
>Veillez à installer le [dernier Feature Pack Communities](deploy-communities.md#latestfeaturepack).

## Abréger {#abbreviate}

Une aide permettant de renvoyer une chaîne abrégée conforme aux propriétés maxWords et maxLength.

La chaîne à abréger est fournie comme contexte. Si aucun contexte n’est fourni, une chaîne vide est renvoyée.

Tout d’abord, le contexte est réduit à maxLength, puis le contexte est divisé en mots et réduit à maxWords.

Si safeString est défini sur true, la chaîne renvoyée est une SafeString.

### Paramètres {#parameters}

* **contexte**: Chaîne

   (facultatif) La valeur par défaut est la chaîne vide

* **maxLength**: Nombre

   (facultatif) La valeur par défaut est la longueur du contexte.

* **maxWords**: Nombre

   (facultatif) La valeur par défaut est le nombre de mots de la chaîne rognée.

* **safeString**: Booléen

   (facultatif) Renvoie une valeur Handlebars.SafeString() si la valeur est true. La valeur par défaut est false.

### Exemples {#examples}

```
{{abbreviate subject maxWords=2}}

/*
If subject =
    "AEM Communities - Site Creation Wizard"

Then abbreviate would return
    "AEM Communities".
*/
```

```
{{{abbreviate message safeString=true maxLength=30}}}

/*
If message =
    "The goal of AEM Communities is to quickly create a community engagement site."

Then abbreviate would return
    "The goal of AEM Communities is"
*/
```

## Content-loadmore {#content-loadmore}

Permet d’ajouter deux étendues sous une balise div, l’une pour le texte intégral, l’autre pour le texte secondaire, avec la possibilité de basculer entre les deux vues.

### Paramètres {#parameters-1}

* **contexte**: Chaîne

   (facultatif) La valeur par défaut est la chaîne vide.

* **numChars**: Nombre

   (facultatif) Nombre de caractères à afficher lorsque le texte intégral ne s’affiche pas. La valeur par défaut est 100.

* **moreText**: Chaîne

   (facultatif) Texte à afficher indiquant qu’il y a plus de texte à afficher. La valeur par défaut est &quot;plus&quot;.

* **ellipsesText**: Chaîne

   (facultatif) Texte à afficher indiquant qu’il existe un texte masqué. La valeur par défaut est &quot;...&quot;.

* **safeString**: Booléen

   (facultatif) Valeur booléenne indiquant s’il faut appliquer Handlebars.SafeString() avant de renvoyer le résultat. La valeur par défaut est false.

### Exemple {#example}

```
{{content-loadmore  context numChars=32  moreText="go on"  ellipsesText="..." }}

/*
If context = 
    "Here is the initial less content and this is more content."

Then content-loadmore would return
    "Here is the initial less content<span class="moreelipses">...</span> <span class="scf-morecontent"><span>and this is more content.</span>  <a href="" class="scf-morelink" evt="click=toggleContent">go on</a></span>"
*/
```

## DateUtil {#dateutil}

Une aide permettant de renvoyer une chaîne de date formatée.

### Paramètres {#parameters-2}

* **contexte**: Nombre

   (facultatif) un décalage de valeur en millisecondes par rapport au 1er janvier 1970 (époque). La date par défaut est la date actuelle.

* **format**: Chaîne

   (facultatif) Format de date à appliquer. La valeur par défaut est &quot;AAAA-MM-JJTHH&quot;:mm:s.sssZ&quot; et le résultat apparaît sous la forme &quot;2015-03-18T18:17:13-07:00&quot;

### Exemples {#examples-1}

```
{{dateUtil this.memberSince format="dd MMM yyyy, hh:mm"}}

// returns "18 Mar 2015, 18:17"
```

```
{{dateUtil this.birthday format="MM-DD-YYYY"}}

// returns "03-18-2015"
```

## Est égal à {#equals}

Un assistant pour renvoyer du contenu en fonction d’une condition d’égalité.

### Paramètres {#parameters-3}

* **lvalue**: Chaîne

   Valeur de gauche à comparer

* **rvalue**: Chaîne

   Valeur de droite à comparer

### Exemple {#example-1}

```
{{#equals  value "some-value"}}
  <div>They are EQUAL!</div>
{{else}}
  <div>They are NOT equal!</div>
{{/equals}}
```

## If-wcm-mode {#if-wcm-mode}

Une assistance par bloc qui teste la valeur actuelle de [Mode WCM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) dans une liste de modes séparés par des chaînes.

### Paramètres {#parameters-4}

* **contexte**: Chaîne

   (facultatif) Chaîne à traduire. Obligatoire si aucune valeur par défaut n’est fournie.

* **mode**: Chaîne

   (facultatif) Liste séparée par des virgules de [Modes WCM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) pour tester si défini.

### Exemple {#example-2}

```xml
{{#if-wcm-mode mode="DESIGN, EDIT"}}
 ...
{{else}}
 ...
{{/if-wcm-mode}}
```

## i18n {#i-n}

Cette aide remplace l’aide Handlebars &quot;i18n&quot;.

Voir aussi [Internationalisation de chaînes dans un code JavaScript](../../help/sites-developing/i18n-dev.md#internationalizing-strings-in-javascript-code).

### Paramètres {#parameters-5}

* **contexte**: Chaîne

   (facultatif) Chaîne à traduire. Obligatoire si aucune valeur par défaut n’est fournie.

* **default**: Chaîne

   (facultatif) Chaîne par défaut à traduire. Obligatoire si aucun contexte n’est fourni.

* **comment**: Chaîne

   (facultatif) Conseil de traduction

### Exemple {#example-3}

```
{{i18n "hello"}}
{{i18n "hello" comment="greeting" default="bonjour"}}
```

## Inclure {#include}

Une aide pour inclure un composant en tant que ressource non existante dans un modèle.

Cela permet à la ressource d’être personnalisée par programmation plus facilement qu’il n’est possible pour une ressource ajoutée en tant que noeud JCR. Voir [Ajout ou inclusion d’un composant Communautés](scf.md#add-or-include-a-communities-component).

Seuls quelques-uns des composants Communities sont incluables. Pour AEM 6.1, les inclusions sont [commentaires](essentials-comments.md), [note](rating-basics.md), [critiques](reviews-basics.md), et [vote](essentials-voting.md).

Cette assistance, appropriée uniquement côté serveur, fournit des fonctionnalités similaires à [cq:include](../../help/sites-developing/taglib.md) pour les scripts JSP.

### Paramètres {#parameters-6}

* **contexte**: Chaîne ou objet

   (facultatif, sauf si vous fournissez un chemin relatif)

   use `this`pour transmettre le contexte actuel

   use `this.id` pour obtenir la ressource à l’adresse `id` pour le rendu de resourceType demandé

* **resourceType**: Chaîne

   (facultatif) le type de ressource est défini par défaut sur le type de ressource du contexte.

* **modèle**: Chaîne

   chemin d’accès au script du composant

* **path**: Chaîne

   (obligatoire) chemin d’accès à la ressource. Si le chemin est relatif, un contexte doit être fourni, sinon la chaîne vide est renvoyée.

* **authoringDisabled**: Booléen

   (facultatif) La valeur par défaut est false. Pour une utilisation interne uniquement.

### Exemple {#example-4}

```
{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}
```

Cela inclura un nouveau composant de commentaires à l’adresse `this.id` + /comments

## IncludeClientLib {#includeclientlib}

Une aide qui comprend une bibliothèque cliente HTML AEM, qui peut être une bibliothèque js, css ou thème. Pour plusieurs inclusions de différents types, par exemple js et css, cette balise doit être utilisée plusieurs fois dans le script Handlebars.

Cette assistance, appropriée uniquement côté serveur, fournit des fonctionnalités similaires à [ui:includeClientLib](../../help/sites-developing/taglib.md) pour les scripts JSP.

### Paramètres {#parameters-7}

* **categories**: Chaîne

   (facultatif) Une liste de catégories de bibliothèques clientes séparées par des virgules. Cela inclut toutes les bibliothèques JavaScript et CSS pour les catégories données. Le nom du thème est extrait de la requête.

* **thème**: Chaîne

   (facultatif) Une liste de catégories de bibliothèques clientes séparées par des virgules. Cela inclut toutes les bibliothèques (CSS et JS) relatives au thème pour les catégories données. Le nom du thème est extrait de la requête.

* **js**: Chaîne

   (facultatif) Une liste de catégories de bibliothèques clientes séparées par des virgules. Cela inclut toutes les bibliothèques JavaScript et CSS pour les catégories données.

* **css**: Chaîne

   (facultatif) Une liste de catégories de bibliothèques clientes séparées par des virgules. Cela inclut toutes les bibliothèques CSS pour les catégories données.

### Exemples {#examples-2}

```
// all: js + theme (theme-js + css) 
{{includeClientLib categories="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/socialgraph.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/socialgraph.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// only js libs
{{includeClientLib js="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/socialgraph.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// theme only (theme-js + css) 
{{includeClientLib theme="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// css only
{{includeClientLib css="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/socialgraph.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
```

## Plutôt temps {#pretty-time}

Une aide permettant d’afficher le temps écoulé jusqu’à un point de coupure, après lequel un format de date normal est affiché.

Par exemple :

* Il y a 12 heures
* 7 jours auparavant

### Paramètres {#parameters-8}

* **contexte**: Nombre

   Un temps dans le passé à comparer avec &quot;maintenant&quot;. Le temps est exprimé sous la forme d’un décalage de valeur en millisecondes par rapport au 1er janvier 1970 (époque).

* **daysCutoff**: Nombre

   Nombre de jours auparavant avant de passer à une date réelle. La valeur par défaut est 60.

### Exemple {#example-5}

```
{{pretty-time this.published daysCutoff=7}}

/*
Depending on how long in the past, may return
  
  "3 minutes ago"

  "3 hours ago"

  "3 days ago"
*/
```

## Xss-html {#xss-html}

Une aide qui code une chaîne source pour le contenu d’élément de HTML afin de vous protéger contre XSS.

REMARQUE : il ne s’agit pas d’un programme de validation et il ne doit pas être utilisé pour écrire des valeurs d’attribut.

### Paramètres {#parameters-9}

* **contexte**: objet

   le HTML à coder

### Exemple {#example-6}

```
<p>{{xss-html forum-ugc}}</p>
```

## Xss-htmlAttr {#xss-htmlattr}

Une aide qui code une chaîne source pour l’écriture sur une valeur d’attribut de HTML afin de vous aider à vous protéger contre XSS.

REMARQUE : il ne s’agit pas d’un programme de validation et il ne doit pas être utilisé pour écrire des attributs activables (href, src, gestionnaires d’événements).

### Paramètres {#parameters-10}

* **contexte**: Objet

   Le HTML à coder

### Exemple {#example-7}

```
<div id={{xss-htmlAttr id}} />
```

## Xss-jsString {#xss-jsstring}

Une aide qui code une chaîne source pour l’écriture dans du contenu de chaîne JavaScript afin de vous protéger contre XSS.

REMARQUE : il ne s’agit pas d’un validateur et ne doit pas être utilisé pour écrire du code JavaScript arbitraire.

### Paramètres {#parameters-11}

* **contexte**: Objet

   Le HTML à coder

### Exemple {#example-8}

```
var input = {{xss-jsString topic-title}}
```

## Xss-validHref {#xss-validhref}

Une assistance qui assainit une URL pour écrire en tant que href HTML ou valeur d’attribut source afin de vous aider à vous protéger contre XSS.

REMARQUE : cela peut renvoyer une chaîne vide

### Paramètres {#parameters-12}

* **contexte**: Objet

   URL à assainir

### Exemple {#example-9}

```
<a href="{{xss-validHref url}}">my link</a>
```

## Présentation de base de Handlebars.js {#handlebars-js-basic-overview}

* Un appel d’assistance Handlebars est un identifiant simple (le *nom* de l’assistant), suivi de zéro ou de plusieurs paramètres séparés par des espaces.
* Les paramètres peuvent être un simple objet String, Number, boolean ou JSON, ainsi qu’une séquence facultative de paires clé-valeur (arguments de hachage) comme dernier(s) paramètre(s).
* Les clés des arguments de hachage doivent être des identifiants simples.
* Les valeurs des arguments de hachage sont des expressions Handlebars : identifiants, chemins ou chaînes simples.
* Le contexte actuel, `this`, est toujours disponible pour les assistants Handlebars.
* Le contexte peut être une chaîne, un nombre, une valeur booléenne ou un objet de données JSON.
* Il est possible de transmettre un objet imbriqué dans le contexte actuel en tant que contexte, par exemple `this.url` ou `this.id` (voir les exemples suivants d’aides simples et par blocs).

* Les assistants de bloc sont des fonctions qui peuvent être appelées à partir de n’importe quel emplacement du modèle. Ils peuvent appeler un bloc du modèle zéro ou plusieurs fois avec un contexte différent à chaque fois. Ils contiennent un contexte entre {{#*name*}} and {{/*name*}}.

* Handlebars fournit un paramètre final aux assistants nommés &quot;options&quot;. L’objet spécial &quot;options&quot; inclut

   * Données privées facultatives (options.data)
   * Propriétés de clé-valeur facultatives de l’appel (options.hash)
   * Possibilité d’appeler lui-même (options.fn())
   * Possibilité d’appeler l’inverse de lui-même (options.inverse())

* Il est recommandé que le contenu de chaîne de HTML renvoyé par un assistant soit une SafeString.

### Exemple d’un simple assistant de la documentation Handlebars.js : {#an-example-of-a-simple-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link_to', function(title, options) {
    return new Handlebars.SafeString('<a href="/posts' + this.url + '">' + title + "!</a>");
});

var context = {posts: [
    {url: "/hello-world",
      body: "Hello World!"}
  ] };

// when link_to is called, posts is the current context
var source = '<ul>{{#posts}}<li>{{{link_to "Post"}}}</li>{{/posts}}</ul>'

var template = Handlebars.compile(source);

template(context);
```

Rendre :

&lt;ul>\
&lt;li>&lt;a href=&quot;/posts/hello-world&quot;>Publiez !&lt;/a>&lt;/li>\
&lt;/ul>

### Exemple d’assistance de bloc à partir de la documentation Handlebars.js : {#an-example-of-a-block-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link', function(options) {
    return new Handlebars.SafeString('<a href="/people/' + this.id + '">' + options.fn(this) + '</a>');
});

var data = { "people": [
  { "name": "Alan", "id": 1 },
  { "name": "Yehuda", "id": 2 }
]};

// when link is called, people is the current context
var source = "<ul>{{#people}}<li>{{#link}}{{name}}{{/link}}</li>{{/people}}</ul>";

var template = Handlebars.compile(source);

template(data);
```

Rendre :\
&lt;ul>\
&lt;li>&lt;a href=&quot;/people/1&quot;>Alan&lt;/a>&lt;/li>\
&lt;li>&lt;a href=&quot;/people/2&quot;>Yehuda&lt;/a>&lt;/li>\
&lt;/ul>

## Aide SCF personnalisée {#custom-scf-helpers}

Les assistants personnalisés doivent être implémentés côté serveur et côté client, en particulier lors de la transmission de données. Pour SCF, la plupart des modèles sont compilés et rendus côté serveur, car le serveur génère le HTML pour un composant donné lorsque la page est demandée.

### Aide personnalisée côté serveur {#server-side-custom-helpers}

Pour mettre en oeuvre et enregistrer un assistant SCF personnalisé côté serveur, il vous suffit de mettre en oeuvre l’interface Java. [TemplateHelper](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/handlebars/api/TemplateHelper.html), faites en sorte qu’il soit [Service OSGi](../../help/sites-developing/the-basics.md#osgi) et installez-le dans le cadre d’un regroupement OSGi.

Par exemple :

### FooTextHelper.java {#footexthelper-java}

```java
/** Custom Handlebars Helper */

package com.my.helpers;

import java.io.IOException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

import com.adobe.cq.social.handlebars.api.TemplateHelper;
import com.github.jknack.handlebars.Options;

@Service
@Component
public class FooTextHelper implements TemplateHelper<String>{

    @Override
    public CharSequence apply(String context, Options options) throws IOException {
        return "foo-" + context;
    }

    @Override
    public String getHelperName() {
        return "foo-text";
    }

    @Override
    public Class<String> getContextType() {
        return String.class;
    }
}
```

>[!NOTE]
>
>Une assistance créée côté serveur doit également être créée côté client.
>
>Le composant est de nouveau rendu côté client pour l’utilisateur connecté. Si l’assistant côté client est introuvable, le composant disparaît.

### Aide personnalisée côté client {#client-side-custom-helpers}

Les assistants côté client sont des scripts Handlebars enregistrés en appelant `Handlebars.registerHelper()`.\
Par exemple :

### custom-helpers.js {#custom-helpers-js}

```
function(Handlebars, SCF, $CQ) {

    Handlebars.registerHelper('foo-text', function(context, options) {
        if (!context) {
            return "";
        }
        return "foo-" + context;
    });

})(Handlebars, SCF, $CQ);
```

Les assistants côté client personnalisés doivent être ajoutés à une bibliothèque client personnalisée.\
La bibliothèque cliente doit :

* Inclure une dépendance sur `cq.social.scf`
* Chargement après le chargement des Guidons
* Be [included](clientlibs.md)

Remarque : Les assistants SCF sont définis dans `/etc/clientlibs/social/commons/scf/helpers.js`.

| **[⇐ Notions fondamentales sur les fonctionnalités](essentials.md)** | **[⇒ de personnalisation côté serveur](server-customize.md)** |
|---|---|
|  | **[⇒ de personnalisation côté client](client-customize.md)** |
