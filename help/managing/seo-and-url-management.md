---
title: Meilleures pratiques relatives à l’optimisation pour les moteurs de recherche et à la gestion des URL
seo-title: SEO and URL Management Best Practices
description: Découvrez les bonnes pratiques relatives à l’optimisation pour les moteurs de recherche et les recommandations pour les suivre dans une mise en oeuvre AEM.
seo-description: Learn about SEO best practices and recommendations for achieving these on an AEM implementation.
uuid: 7fffbe30-7cf8-44ce-b275-e128732577dd
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 150b43e3-9fb3-4c1c-b1cd-ccfd162974ad
exl-id: d45fe856-4709-437b-b193-e8243a695d2c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3133'
ht-degree: 61%

---

# Meilleures pratiques relatives à l’optimisation pour les moteurs de recherche et à la gestion des URL{#seo-and-url-management-best-practices}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’optimisation pour les moteurs de recherche est devenue une préoccupation essentielle pour de nombreux spécialistes du marketing. En conséquence, les questions d’optimisation pour les moteurs de recherche doivent être traitées pour de nombreux projets AEM.

Le présent document commence par décrire certaines [bonnes pratiques relatives à l’optimisation pour les moteurs de recherche](#seo-best-practices) et explique comment les suivre lors d’une mise en œuvre d’AEM. Il approfondit ensuite certaines des [étapes de mise en œuvre plus complexes](#aem-configurations) abordées dans la première section.

## Bonnes pratiques relatives à l’optimisation pour les moteurs de recherche {#seo-best-practices}

Cette section décrit certaines bonnes pratiques générales d’optimisation pour les moteurs de recherche.

### URL {#urls}

Certaines bonnes pratiques généralement acceptées s’appliquent aux URL.

Dans votre projet AEM, lors de l’évaluation des URL, posez-vous la question suivante :

* « Si un utilisateur voyait cette URL, mais aucun des éléments de contenu de la page, pourrait-il décrire ce qu’est cette page ? »

Si la réponse est oui, il est probable que l’URL fonctionne bien pour un moteur de recherche.

Voici quelques conseils généraux sur la construction de vos URL pour l’optimisation pour les moteurs de recherche :

* Utilisez des tirets pour séparer les mots.

   * Nommez les pages en utilisant des tirets (-) comme séparateurs.
   * Évitez d’utiliser des majuscules, des traits de soulignement et des espaces.

* Dans la mesure du possible, évitez d’utiliser des paramètres de requête. Si nécessaire, limitez-les à deux ou moins.

   * Utilisez la structure de répertoire pour indiquer l’architecture des informations, le cas échéant.
   * Si une structure de répertoire n’est pas une option, utilisez des sélecteurs Sling dans l’URL plutôt que des chaînes de requête. Outre la valeur d’optimisation pour les moteurs de recherche fournie, les sélecteurs sling rendent également les pages mises en cache pour le Dispatcher.

* Plus une URL est lisible, mieux c’est. la présence de mots-clés dans l’URL augmente la valeur.

   * Lors de l’utilisation de sélecteurs sur une page, les sélecteurs qui fournissent une valeur sémantique sont recommandés.
   * Si un humain ne peut pas lire votre URL, un moteur de recherche ne le peut pas non plus.
   * Par exemple : `mybrand.com/products/product-detail.product-category.product-name.html` est préférable à `mybrand.com/products/product-detail.1234.html`

* Évitez les sous-domaines lorsque cela est possible, car les moteurs de recherche les traitent comme des entités différentes, ce qui fragmente la valeur d’optimisation pour les moteurs de recherche du site.

   * Utilisez plutôt des sous-chemins de premier niveau. Par exemple, utilisez `es.mybrand.com/home.html` plutôt que `www.mybrand.com/es/home.html`.
   * Planifiez votre hiérarchie de contenu de manière à ce qu’elle corresponde à la présentation du contenu, conformément à cette directive.

* L’efficacité des mots-clés dans les URL diminue à mesure que la longueur de l’URL et la position du mot-clé augmentent. En d&#39;autres termes, plus court est mieux.

   * Utilisez les techniques et fonctionnalités de raccourcissement d’URL fournies par AEM pour supprimer les éléments d’URL inutiles.
   * Par exemple, `mybrand.com/en/myPage.html` est préférable à `mybrand.com/content/my-brand/en/myPage.html`.

* Utilisez des URL canoniques.

   * Si une URL peut être fournie à partir de différents chemins ou avec différents paramètres ou sélecteurs, veillez à utiliser une balise `rel=canonical` sur la page.
   * Cela peut être inclus dans le code du modèle d’AEM.

* Dans la mesure du possible, faites correspondre les URL aux titres des pages.

   * Les auteurs de contenu doivent être encouragés à suivre cette pratique.

* Prise en charge de l’insensibilité à la casse dans les demandes d’URL.

   * Configurez Dispatcher pour réécrire toutes les requêtes entrantes en minuscules.
   * Formez les auteurs de contenu à créer toutes les pages à l’aide de lettres minuscules.

* Assurez-vous que chaque page n’est diffusée qu’à partir d’un seul protocole.

   * Il arrive que des sites soient diffusés via `http` jusqu’à ce qu’un utilisateur arrive sur une page avec, par exemple, un formulaire de passage en caisse ou de connexion, où il passe alors en `https`. En cas de liaison depuis cette page, si l’utilisateur peut revenir aux pages `http` et y accéder par `https`, le moteur de recherche les suit comme deux pages distinctes.
   * Actuellement, Google préfère les pages `https` aux pages `http`. Pour cette raison, il est parfois plus facile pour tous les acteurs de diffuser l’ensemble du site par `https`.

### Configuration du serveur {#server-configuration}

En termes de configuration du serveur, vous pouvez accomplir les étapes suivantes pour vous assurer que seul le contenu approprié est analysé :

* Utilisez un fichier `robots.txt` pour empêcher l’analyse de tout contenu qui ne doit pas être indexé.

   * Bloc **all** analyse sur les environnements de test.

* Lors du lancement d’un nouveau site avec des URL mises à jour, implémentez des redirections 301 pour vous assurer que votre classement d’optimisation pour les moteurs de recherche existant n’est pas perdu.
* Incluez une favicon pour votre site.
* Mettez en oeuvre un plan de site XML pour faciliter l’analyse de votre contenu par les moteurs de recherche. Veillez à inclure un plan de site mobile pour les sites mobiles et/ou réactifs.

## Configurations AEM {#aem-configurations}

Cette section décrit les étapes requises de façon à configurer AEM afin qu’il suive ces recommandations d’optimisation pour les moteurs de recherche.

### Utilisation de sélecteurs Sling {#using-sling-selectors}

Auparavant, l’utilisation des paramètres de requête était la pratique généralement acceptée lors de la création d’une application web d’entreprise.

Ces dernières années, la tendance a été de les supprimer afin de rendre les URL plus lisibles. Sur de nombreuses plates-formes, cela implique la mise en œuvre de redirections sur le serveur web ou réseau de diffusion de contenu, mais Sling simplifie cela. Sling selectors :

* Améliorez la lisibilité des URL.
* Permet de mettre en cache vos pages sur le Dispatcher et améliore souvent la sécurité.
* permettent de traiter le contenu directement, plutôt que de disposer d’une classe servlet générique qui récupère le contenu. Vous bénéficiez ainsi des avantages des listes de contrôle d’accès que vous appliquez à votre référentiel et des filtres que vous appliquez sur le Dispatcher.

#### Utilisation de sélecteurs pour les servlets {#using-selectors-for-servlets}

AEM propose deux options lors de l’écriture de servlets :

* Servlets bin
* Servlets Sling

Les exemples suivants illustrent la manière d’enregistrer des servlets qui suivent ces deux modèles, ainsi que les avantages liés à l’utilisation des servlets Sling.

#### Servlets bin (un niveau vers le bas) {#bin-servlets-one-level-down}

Les servlets bin suivent le schéma issu de la programmation J2EE auquel nombre de développeurs sont habitués. La servlet est enregistrée à un chemin spécifique qui, dans le cas d’AEM, se trouve généralement sous `/bin`, et vous extrayez les paramètres de requête nécessaires dans la chaîne de requête.

L’annotation SCR pour ce type de servlet doit ressembler à ce qui suit :

```
@SlingServlet(paths = "/bin/myApp/myServlet", extensions = "json", methods = "GET")
```

Vous extrayez ensuite les paramètres à partir de la chaîne de requête via l’objet `SlingHttpServletRequest` inclus dans la méthode `doGet`, par exemple :

```
String myParam = req.getParameter("myParam");
```

L’URL résultante utilisée doit ressembler à ce qui suit :

`https://www.mydomain.com/bin/myApp/myServlet.json?myParam=myValue`

Cette approche comporte quelques points à prendre en compte :

* L’URL elle-même perd sa valeur en termes d’optimisation pour les moteurs de recherche. Les utilisateurs accédant au site, y compris les moteurs de recherche, ne reçoivent aucune valeur sémantique de l’URL, car l’URL représente un chemin d’accès programmatique et non la hiérarchie du contenu.
* La présence de paramètres de requête dans l’URL signifie que le Dispatcher ne sera pas en mesure de mettre en cache la réponse.
* Si vous souhaitez sécuriser cette servlet, vous devez mettre en œuvre votre propre logique de sécurité personnalisée dans la servlet.
* Le Dispatcher doit être configuré (avec soin) afin d’exposer `/bin/myApp/myServlet`. Exposer simplement `/bin` permettrait d’accéder à certaines servlets qui ne doivent pas être ouvertes pour les visiteurs du site.

#### Servlets Sling (un niveau vers le bas) {#sling-servlets-one-level-down}

Les servlets Sling vous permettent d’enregistrer votre servlet de la manière opposée. Plutôt que de vous adresser à une servlet et de spécifier le contenu dont vous souhaitez qu’elle effectue le rendu en fonction des paramètres de requête, vous devez aborder le contenu souhaité et spécifier la servlet qui doit effectuer le rendu du contenu en fonction des sélecteurs Sling.

L’annotation SCR pour ce type de servlet doit ressembler à ce qui suit :

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json”, methods=”GET”)
```

Dans ce cas, la ressource que l’URL adresse (une instance de la ressource `myPageType`) est accessible dans la servlet automatiquement. Pour y accéder, vous devez appeler :

```
Resource myPage = req.getResource();
```

L’URL résultante utilisée doit ressembler à ce qui suit :

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

Les avantages de cette approche sont les suivants :

* Vous pouvez créer la valeur d’optimisation pour les moteurs de recherche, acquise par la sémantique présente dans la hiérarchie de votre site et le nom de la page.
* Comme aucun paramètre de requête n’est présent, le Dispatcher peut mettre en cache la réponse. En outre, toutes les mises à jour apportées à la page gérée invalideront ce cache lorsque la page sera activée.
* Toutes les listes ACL appliquées à `/content/my-brand/my-page` prennent effet lorsqu’un utilisateur tente d’accéder à cette servlet.
* Le Dispatcher sera déjà configuré pour diffuser ce contenu en fonction de la diffusion du site web. Aucune configuration supplémentaire n’est requise.

### Réécriture d’URL {#url-rewriting}

Dans AEM, toutes les pages web sont stockées sous `/content/my-brand/my-content`. Cela peut être utile du point de vue de la gestion des données de référentiel. Toutefois, il ne s’agit pas nécessairement de la manière dont vous souhaitez que vos clients voient votre site et cela peut être en conflit avec la recommandation d’optimisation pour les moteurs de recherche selon laquelle les URL doivent être aussi courtes que possible. En outre, vous pouvez diffuser plusieurs sites web depuis la même instance AEM et différents noms de domaines.

Cette section décrit les options disponibles dans AEM pour gérer ces URL et les présenter aux utilisateurs d’une manière plus lisible et tenant davantage compte de l’optimisation pour les moteurs de recherche.

#### URL de redirection vers un microsite {#vanity-urls}

Si un auteur souhaite qu’une page soit accessible depuis un autre emplacement à des fins publicitaires, les URL de redirection vers un microsite d’AEM, définies page par page, peuvent être utiles. Afin d’ajouter une URL de redirection vers un microsite pour une page, accédez à la console **[!UICONTROL Sites]** et modifiez les propriétés de la page. Au bas de l’onglet **[!UICONTROL Basique]** se trouve une section dans laquelle peuvent être ajoutées les URL de redirection vers un microsite. Gardez à l’esprit que le fait que la page soit accessible via plusieurs URL réduit la valeur d’optimisation pour les moteurs de recherche de la page en question. Par conséquent, une balise d’URL canonique doit être ajoutée à la page afin d’éviter ce problème.

#### Noms de pages localisés {#localized-page-names}

Vous pouvez afficher des noms de page localisés pour les utilisateurs de contenu traduit. Par exemple :

* plutôt que de demander à un utilisateur hispanophone d’accéder à :

   `www.mydomain.com/es/home.html`

* il serait préférable que l’URL soit :

   `www.mydomain.com/es/casa.html`.

La difficulté en matière de localisation du nom d’une page réside dans le fait que plusieurs outils de localisation disponibles sur la plateforme AEM nécessitent que les noms de cette page correspondent dans toutes les langues de manière à ce que le contenu reste synchronisé.

La propriété `sling:alias` permet de pallier cette difficulté. `sling:alias` peut être ajouté comme propriété à n’importe quelle ressource pour donner un nom d’alias à la ressource. Dans l’exemple précédent, vous auriez :

* une page dans le JCR à :

   `…/es/home`

* à laquelle vous ajoutez ensuite une propriété :

   `sling:alias` = `casa`

Les outils de traduction d’AEM tels que le gestionnaire multisite peuvent ainsi conserver des relations entre :

* `/en/home`

* `/es/home`

Tout en permettant aux utilisateurs finaux d’interagir avec le nom de la page dans leur langue maternelle.

>[!NOTE]
>
> La propriété `sling:alias` peut être définie à l’aide de la [propriété Alias lors de la modification des propriétés de la page](/help/sites-authoring/editing-page-properties.md#advanced)

#### /etc/map {#etc-map}

Dans une installation AEM standard :

* pour la configuration OSGi:

   **Apache Sling Resource Resolver Factory**

   (`org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl`)

* la propriété:

   **Emplacement du mappage**

   (`resource.resolver.map.location`)

* par défaut :

   `/etc/map`

Les définitions de mappage peuvent être ajoutées à cet emplacement pour mapper des requêtes entrantes, réécrire des URL sur des pages dans AEM, ou les deux.

Pour créer un mappage, créez un nœud `sling:Mapping` à cet emplacement sous `/http` ou `/https`. En fonction des propriétés `sling:match` et `sling:internalRedirect` définies sur ce nœud, AEM redirigera tout le trafic pour l’URL correspondante vers la valeur spécifiée dans la propriété `internalRedirect`.

Bien qu’il s’agisse de l’approche documentée dans la documentation officielle d’AEM et de Sling, cette mise en œuvre ne fournit qu’une prise en charge limitée des expressions régulières par rapport aux options disponibles en utilisant directement `SlingResourceResolver`. En outre, l’implémentation de mappages de cette manière peut entraîner des problèmes d’invalidation du cache du Dispatcher.

Voici un exemple de la manière dont ce problème se produit :

1. Un utilisateur visite votre site web et demande `https://www.mydomain.com/my-page.html`.
1. Le Dispatcher transmet cette requête au serveur de publication.
1. En utilisant `/etc/map`, le serveur de publication résout cette requête en `/content/my-brand/my-page` et effectue le rendu de la page.

1. Le Dispatcher met la réponse en cache à l’adresse `/my-page.html` et renvoie la réponse à l’utilisateur.
1. Un auteur de contenu modifie cette page et l’active.
1. L’agent de vidage du Dispatcher envoie une demande d’invalidation pour `/content/my-brand/my-page`**.** Étant donné que le Dispatcher ne possède pas de page mise en cache dans ce chemin, l’ancien contenu reste en cache et devient périmé.

Il existe des moyens de configurer des règles de purge de message personnalisées qui mapperont l’URL plus courte à l’URL plus longue à des fins d’invalidation du cache.

Cependant, il existe également un moyen plus simple de gérer cela :

1. **Règles SlingResourceResolver**

   À l’aide de la console web (par exemple, localhost:4502/system/console/configMgr), vous pouvez configurer le résolveur de ressources Sling :

   * **Apache Sling Resource Resolver Factory**

      `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.
   Il est conseillé d’établir les mappages requis pour raccourcir les URL sous la forme d’expressions régulières, puis de définir ces configurations sous un nœud OsgiConfignode, `config.publish`, qui est inclus dans votre version.

   Plutôt que de définir les mappages dans `/etc/map`, vous pouvez les attribuer directement à la propriété **Mappages d’URL** (`resource.resolver.mapping`) :

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   Dans cet exemple simple, vous supprimez `/content/my-brand/` du début de toute URL où il est présent.

   Cela convertirait une URL :

   * de `/content/my-brand/my-page.html`
   * en simplement `/my-page.html`

   Cela est conforme à la pratique recommandée de conserver les URL aussi courtes que possible.

1. **Mappage de la sortie d’URL sur les pages**

   Après avoir défini vos mappages dans le résolveur de ressource Apache Sling (Apache Sling Resource Resolver), vous devez les utiliser dans vos composants pour vous assurer que les URL que vous générez sur vos pages sont courtes et ordonnées. Vous pouvez effectuer cette opération à l’aide de la fonction de mappage de `ResourceResolver`.

   Par exemple, si vous mettez en œuvre un composant de navigation personnalisée qui répertorie les enfants de la page en cours, vous pouvez utiliser la méthode de mappage comme suit :

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Apache HTTP Server mod_rewrite {#apache-http-server-mod-rewrite}

Jusqu’à présent, vous avez mis en œuvre des mappages avec la logique dans vos composants pour utiliser ces mappages lors de la génération des URL sur les pages.

La gestion de ces URL raccourcies lorsqu’elles entrent dans le Dispatcher constitue la pièce finale du puzzle ; c’est là que `mod_rewrite` entre en jeu. L’utilisation de `mod_rewrite` a pour principal avantage que les URL sont mappées vers leur forme complète *avant* leur envoi au module de Dispatcher. Cela signifie que Dispatcher demande l’URL longue au serveur de publication et la met en cache en conséquence. Par conséquent, toutes les demandes de vidage du dispatcher qui arrivent du serveur de publication pourront invalider ce contenu.

Pour mettre en œuvre ces règles, vous pouvez ajouter des éléments `RewriteRule` sous votre hôte virtuel dans la configuration Apache HTTP Server. Si vous souhaitez développer les URL raccourcies de l’exemple précédent, vous pouvez mettre en œuvre une règle qui ressemble à ce qui suit :

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Balises d’URL canoniques {#canonical-url-tags}

Les balises d’URL canoniques sont des balises de lien placées dans l’en-tête d’un document de HTML afin de clarifier la manière dont les moteurs de recherche doivent traiter une page lors de l’indexation du contenu. L’avantage qu’ils offrent est de s’assurer qu’une page (différentes versions de) sera indexée de la même manière, même si l’URL de la page peut contenir des différences.

Par exemple, si un site offre une version d’une page compatible avec les imprimantes, un moteur de recherche indexerait potentiellement cette page indépendamment de la version standard de la page. La balise canonique indique au moteur de recherche qu’elles sont identiques.

Exemples :

* `https://www.mydomain.com/my-brand/my-page.html`
* `https://www.mydomain.com/my-brand/my-page.print.html`

Les deux appliqueraient la balise suivante à la tête de la page :

```xml
<link rel=”canonical” href=”my-brand/my-page.html”/>
```

`href` peut être relatif ou absolu. Le code doit être inclus dans le balisage de la page pour déterminer l’URL canonique de la page et générer cette balise.

### Configuration du Dispatcher pour la non-sensibilité à la casse {#configuring-the-dispatcher-for-case-insensitivity}

La bonne pratique consiste à afficher toutes les pages en minuscules. Cependant, vous ne souhaitez pas qu’un utilisateur obtienne un 404 lorsqu’il accède à votre site web à l’aide de lettres majuscules dans son URL. Pour cette raison, Adobe recommande d’ajouter une règle de réécriture dans la configuration Apache HTTP Server de façon à mapper toutes les URL entrantes vers une version en lettres minuscules. En outre, les auteurs de contenu doivent être formés pour créer leurs pages avec des noms en minuscules.

Pour configurer Apache afin de forcer le trafic entrant à être écrit en minuscules, ajoutez les éléments suivants à la configuration `vhost` :

```xml
RewriteEngine On
RewriteMap lowercase int:tolower
```

En outre, ajoutez le code suivant au tout début du fichier `htaccess` :

```xml
RewriteCond $1 [A-Z]
RewriteRule ^(.*)$ /${lowercase:$1} [R=301,L]
```

### Mise en œuvre de robots.txt pour protéger les environnements de développement {#implementing-robots-txt-to-protect-development-environments}

Les moteurs de recherche *doivent* normalement vérifier la présence d’un fichier `robots.txt` à la racine du site avant d’analyser votre site. « Doivent » est ici en italique, car si les principaux moteurs de recherche (Google, Yahoo ou Bing, par exemple) le font, d’autres ne le font pas.

La façon la plus simple de bloquer l’accès à l’ensemble de votre site consiste à placer un fichier nommé `robots.txt` à la racine du site avec le contenu suivant :

```xml
User-agent: *
Disallow: /
```

Sur un environnement de production, vous pouvez également choisir de désactiver certains chemins que vous ne voulez pas voir indexer.

Lorsque vous placez le fichier `robots.txt` à la racine du site, il est possible que les requêtes de vidage du Dispatcher effacent ce fichier ; les mappages d’URL placeront alors probablement la racine du site à un emplacement différent du `DOCROOT`, comme défini dans la configuration Apache HTTP Server. Pour cette raison, il est courant de placer ce fichier sur l’instance de création à la racine du site et de le répliquer dans l’instance de publication.

### Création d’un plan de site XML sur AEM {#building-an-xml-sitemap-on-aem}

Les navigateurs utilisent des plans de site XML pour mieux comprendre la structure des sites web. Bien qu’il n’y ait aucune garantie que la fourniture d’un plan de site conduise à de meilleurs classements SEO, il s’agit d’une bonne pratique convenue. Vous pouvez gérer manuellement un fichier XML sur le serveur web pour l’utiliser comme plan du site, mais il est recommandé de générer le plan du site par programmation, ce qui garantit que, lorsque les auteurs créent du contenu, le plan du site reflète automatiquement leurs modifications.

Pour générer un plan de site par programmation, enregistrez une servlet Sling qui écoute les appels de `sitemap.xml`. Le servlet peut ensuite utiliser la ressource fournie via l’API servlet pour examiner la page active et ses enfants, en générant du code XML. Le fichier XML sera alors mis en cache dans le Dispatcher. Cet emplacement doit être référencé dans la propriété sitemap du fichier `robots.txt`. En outre, une règle de vidage personnalisée doit être mise en œuvre pour veiller à vider ce fichier chaque fois qu’une nouvelle page est activée.

>[!NOTE]
>
>Vous pouvez enregistrer une servlet Sling pour écouter le sélecteur `sitemap` avec l’extension `xml`. Ainsi, la servlet traite la requête à chaque fois qu’une URL demandée se termine par :
>
>`/<*path-to*>/page.sitemap.xml`
>
>Vous pouvez ensuite obtenir la ressource demandée à partir de la requête et générer un plan du site à partir de ce point dans l’arborescence de contenu à l’aide des API JCR.
>
>L’avantage d’une telle approche est que plusieurs sites sont diffusés à partir de la même instance. Une requête `/content/siteA.sitemap.xml` génère un plan de site pour `siteA`, tandis que la requête `/content/siteB.sitemap.xml` génère un plan de site pour `siteB` sans devoir écrire du code supplémentaire.

### Création de redirections 301 pour les URL héritées {#creating-redirects-for-legacy-urls}

Lors du lancement d’un site avec une nouvelle structure, la mise en œuvre et le test des redirections 301 dans Apache HTTP Server sont importants pour deux raisons :

* Les URL héritées ont créé une valeur d’optimisation pour les moteurs de recherche au fil du temps. En implémentant une redirection, le moteur de recherche peut appliquer cette valeur à la nouvelle URL.
* Les utilisateurs de votre site peuvent avoir créé des signets sur ces pages. En implémentant des redirections, vous pouvez vous assurer d’orienter l’utilisateur vers la page du nouveau site qui correspond le mieux à l’emplacement où il tentait d’accéder à l’ancien site.

Veillez à consulter la section Ressources supplémentaires qui suit pour obtenir des instructions sur l’implémentation des redirections 301 ainsi qu’un outil permettant de tester le fonctionnement normal de vos redirections.

## Ressources supplémentaires {#additional-resources}

Pour plus d’informations, consultez les ressources supplémentaires suivantes :

* [Mappage de ressource](/help/sites-deploying/resource-mapping.md)
* [https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url](https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url)
* [https://moz.com/blog/15-seo-best-practices-for-structuring-urls](https://moz.com/blog/15-seo-best-practices-for-structuring-urls)
* [https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/](https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/)
* [https://sling.apache.org/documentation/the-sling-engine/servlets.html](https://sling.apache.org/documentation/the-sling-engine/servlets.html)
* [https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
* [https://httpd.apache.org/docs/current/mod/mod_rewrite.html](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)
* [https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps](https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps)
* [https://en.wikipedia.org/wiki/Robots_exclusion_standard](https://en.wikipedia.org/wiki/Robots_exclusion_standard)
* [https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/](https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/)
* [https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester)
* [https://adobe-consulting-services.github.io/](https://adobe-consulting-services.github.io/)
