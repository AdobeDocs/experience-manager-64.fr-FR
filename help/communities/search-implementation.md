---
title: Principes de recherche
seo-title: Search Essentials
description: Recherche dans les communautés
seo-description: Search in Communities
uuid: 5f35a033-2069-499e-9cdb-db25781312f0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 300aa9f3-596f-42bc-8d46-e535f2bc4379
exl-id: 9092df98-f600-4ed8-93d8-f2e83cd8bb6a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 7%

---

# Principes de recherche {#search-essentials}

## Présentation {#overview}

La fonctionnalité de recherche est une fonctionnalité essentielle d’AEM Communities. En plus de la variable [Recherche sur AEM plateforme](../../help/sites-deploying/queries-and-indexing.md) , AEM Communities fournit les fonctionnalités suivantes : [API de recherche UGC](#ugc-search-api) dans le but de rechercher du contenu généré par l’utilisateur. Le contenu généré par l’utilisateur possède des propriétés uniques, car il est saisi et stocké séparément du contenu AEM et des données utilisateur.

Pour Communities, les deux éléments généralement recherchés sont les suivants :

* Contenu publié par des membres de la communauté

   * Utilise l’API de recherche UGC d’AEM Communities

* Utilisateurs et groupes d’utilisateurs (données utilisateur)

   * Utilise les fonctionnalités de recherche de plateforme AEM

Cette section de la documentation intéresse les développeurs qui créent des composants personnalisés qui créent ou gèrent du contenu généré par l’utilisateur.

## Noeuds de sécurité et ombre {#security-and-shadow-nodes}

Pour un composant personnalisé, il est nécessaire d’utiliser la variable [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) méthodes. Les méthodes d’utilitaire qui créent et recherchent le contenu généré par l’utilisateur établiront les [noeuds fantômes](srp.md#about-shadow-nodes-in-jcr) et assurez-vous que le membre dispose des autorisations appropriées pour la requête.

Les propriétés qui ne sont pas gérées par les utilitaires SRP sont liées à la modération.

Voir [Principes de base de la SRP et du contenu généré par l’utilisateur](srp-and-ugc.md) pour plus d’informations sur les méthodes d’utilitaire utilisées pour accéder aux noeuds fantômes UGC et ACL.

## API de recherche UGC {#ugc-search-api}

Le [Magasin commun UGC](working-with-srp.md) est fourni par l’un des différents fournisseurs de ressources de stockage (SRP), chacun pouvant avoir un langage de requête natif différent. Par conséquent, quel que soit la SRP choisie, le code personnalisé doit utiliser des méthodes de la [Package d’API UGC](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) qui appellera le langage de requête approprié pour la SRP choisie.

### Recherches ASRP {#asrp-searches}

Pour [ASRP](asrp.md), le contenu généré par l’utilisateur est stocké dans Adobe Cloud. Bien que le contenu généré par l’utilisateur ne soit pas visible dans CRX, [modération](moderate-ugc.md) est disponible dans les environnements de création et de publication. L’utilisation de la variable [API de recherche UGC](#ugc-search-api) fonctionne pour ASRP de la même manière que pour les autres SRP.

Il n’existe actuellement aucun outil pour gérer les recherches ASRP.

Lors de la création de propriétés personnalisées pouvant faire l’objet d’une recherche, il est nécessaire de respecter les [exigences d’attribution de noms](#naming-of-custom-properties).

### Recherches MSRP {#msrp-searches}

Pour [MSRP](msrp.md), le contenu généré par l’utilisateur est stocké dans MongoDB configuré pour utiliser Solr pour la recherche. Le contenu généré par l’utilisateur ne sera pas visible dans CRX, mais [modération](moderate-ugc.md) est disponible dans les environnements de création et de publication.

À propos de MSRP et Solr :

* Le Solr incorporé pour la plateforme AEM n’est pas utilisé pour MSRP.
* Si vous utilisez un Solr distant pour la plateforme AEM, il peut être partagé avec MSRP, mais il doit utiliser des collections différentes.
* Solr peut être configuré pour la recherche standard ou pour la recherche multilingue (MLS).
* Pour plus d’informations sur la configuration, voir [Configuration de Solr](msrp.md#solr-configuration) pour MSRP

Les fonctions de recherche personnalisées doivent utiliser la variable [API de recherche UGC](#ugc-search-api).

Lors de la création de propriétés personnalisées pouvant faire l’objet d’une recherche, il est nécessaire de respecter les [exigences d’attribution de noms](#naming-of-custom-properties).

### Recherches JSRP {#jsrp-searches}

Pour [JSRP](jsrp.md), le contenu généré par l’utilisateur est stocké dans [Oak](../../help/sites-deploying/platform.md) et n’est visible que dans le référentiel de l’instance d’auteur ou de publication AEM sur laquelle il a été saisi.

Comme le contenu généré par l’utilisateur est généralement saisi dans l’environnement de publication, pour les systèmes de production multi-éditeurs, il est nécessaire de configurer une [publier un cluster](topologies.md), et non une ferme de publication, de sorte que le contenu saisi soit visible par tous les éditeurs.

Pour JSRP, le contenu généré par l’utilisateur entré dans l’environnement de publication ne sera jamais visible dans l’environnement de création. Ainsi, tous les [modération](moderate-ugc.md) les tâches ont lieu dans l’environnement de publication.

Les fonctions de recherche personnalisées doivent utiliser la variable [API de recherche UGC](#ugc-search-api).

#### Indexation Oak {#oak-indexing}

Bien que les index Oak ne soient pas automatiquement créés pour la recherche de plateforme AEM, à partir de la version 6.2 d’AEM, ils ont été ajoutés pour qu’AEM Communities améliore les performances et fournisse la prise en charge de la pagination lors de la présentation des résultats de recherche UGC.

Si des propriétés personnalisées sont utilisées et que les recherches sont lentes, des index supplémentaires doivent être créés pour les propriétés personnalisées afin de les rendre plus performantes. Pour maintenir la portabilité, respectez les [exigences d’attribution de noms](#naming-of-custom-properties) lors de la création de propriétés personnalisées pouvant faire l’objet de recherches.

Pour modifier des index existants ou créer des index personnalisés, reportez-vous à la section [Requêtes et indexation Oak](../../help/sites-deploying/queries-and-indexing.md).

Le [Oak Index Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) est disponible sur ACS AEM Commons. Elle fournit les éléments suivants :

* Une vue des indices existants
* Possibilité d’initier la réindexation

Pour afficher les index Oak existants dans [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md), l’emplacement est :

* `/oak:index/socialLucene`

![chlimage_1-235](assets/chlimage_1-235.png)

## Propriétés de recherche indexées {#indexed-search-properties}

### Propriétés de recherche par défaut {#default-search-properties}

Vous trouverez ci-dessous quelques-unes des propriétés pouvant faire l’objet de recherches utilisées pour différentes fonctionnalités de Communities :

| **Propriété** | **Type de données** |
|---|---|
| isFlagged | *Booléen* |
| isSpam | *Booléen* |
| lecture | *Booléen* |
| influence | *Booléen* |
| attachments | *Booléen* |
| sentiment | *Long* |
| marqué | *Booléen* |
| ajoutée | *Date* |
| modifiedDate | *Date* |
| state | *Chaîne* |
| userIdentifier | *Chaîne* |
| responses | *Long* |
| jcr:title | *Chaîne* |
| jcr:description | *Chaîne* |
| sling:resourceType | *Chaîne* |
| allowThreadedReply | *Booléen* |
| isDraft | *Booléen* |
| publishDate | *Date* |
| publishJobId | *Chaîne* |
| répondu | *Booléen* |
| chosena | *Booléen* |
| tag | *Chaîne* |
| cq:Tag | *Chaîne* |
| author_display_name | *Chaîne* |
| location_t | *Chaîne* |
| parentPath | *Chaîne* |
| parentTitle | *Chaîne* |

### Dénomination des propriétés personnalisées {#naming-of-custom-properties}

Lors de l’ajout de propriétés personnalisées, afin que ces propriétés soient visibles pour les recherches et les types de recherche créés avec l’événement [API de recherche UGC](#ugc-search-api), il est *obligatoire* pour ajouter un suffixe au nom de la propriété.

Le suffixe est destiné aux langages de requête qui utilisent un schéma :

* Il identifie la propriété comme pouvant faire l’objet d’une recherche.
* Il identifie le type de données

Solr est un exemple de langage de requête qui utilise un schéma.

| **Suffixe** | **Type de données** |
|---|---|
| _b | *Booléen* |
| _dt | *Calendrier* |
| _d | *Double* |
| _tl | *Long* |
| _s | *Chaîne* |
| _t | *Texte* |

**Remarques:**

* *Texte* est une chaîne en jeton, *Chaîne* ne l’est pas. Utilisation *Texte* pour les recherches approximatives (plus comme celle-ci).

* Pour les types à plusieurs valeurs, ajoutez &quot;s&quot; au suffixe, par exemple :

   * `viewDate_dt`: propriété de date unique
   * `viewDates_dts`: listdates, propriété

## Filtres {#filters}

Composants qui incluent la variable [système de commentaires](essentials-comments.md) prennent en charge l’ajout du paramètre de filtre à leurs points de terminaison.

La syntaxe du filtre pour la logique ET et OU est exprimée comme suit (affichée avant d’être codée au format URL) :

* Pour spécifier OU, utilisez un paramètre de filtre avec des valeurs séparées par des virgules :

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* Pour spécifier ET, utilisez plusieurs paramètres de filtre :

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

L’implémentation par défaut de la variable [Composant Recherche](search.md) utilise cette syntaxe, comme on peut le voir dans l’URL qui ouvre la page Résultats de la recherche dans la variable [Guide des composants de communauté](components-guide.md). Pour tester, accédez à [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

Les opérateurs de filtre sont les suivants :

| EQ | égal à |
|---|---|
| NE | not equals |
| LT | inférieur à |
| LTE | inférieur ou égal à |
| GE | supérieur à |
| GTE | supérieur ou égal à |
| LIKE | correspondance approximative |

Il est important que l’URL référence le composant Communities (ressource) et non la page sur laquelle le composant est placé :

* Correct : composant de forum
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Incorrect : page de forum
   * `/content/community-components/en/forum.social.json`

## Outils SRP {#srp-tools}

Il existe un projet Adobe Marketing Cloud GitHub qui contient :

[Outils AEM Communities SRP](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Ce référentiel contient des outils pour gérer les données dans la SRP.

Actuellement, il existe un servlet qui permet de supprimer tout le contenu créé par l’utilisateur de n’importe quelle SRP.

Par exemple, pour supprimer tout le contenu généré par l’utilisateur dans ASRP :

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Résolution des problèmes {#troubleshooting}

### Requête Solr {#solr-query}

Pour résoudre les problèmes liés à une requête Solr, activez la journalisation DEBUG pour

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

La requête Solr réelle s’affichera sous forme d’URL encodée dans le journal de débogage :

La requête à résoudre est : `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

La valeur de la variable `q` est la requête. Une fois le codage de l’URL décodé, la requête peut être transmise à l’outil Solr Admin Query pour un débogage plus poussé.

## Ressources connexes {#related-resources}

* [Stockage de contenu communautaire](working-with-srp.md) - Discute des choix de SRP disponibles pour un magasin commun UGC
* [Présentation du fournisseur de ressources de stockage](srp.md) - Présentation et utilisation du référentiel
* [Accès au contenu généré par l’utilisateur avec SRP](accessing-ugc-with-srp.md) - Consignes de codage
* [Refactorisation de SocialUtils](socialutils.md) - Méthodes utilitaires pour SRP qui remplacent SocialUtils
* [Composants Résultats de recherche](search.md) - Ajout d’une fonctionnalité de recherche UGC à un modèle
