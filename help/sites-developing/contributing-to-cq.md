---
title: Contribution à AEM
seo-title: Contributing to AEM
description: AEM est développé selon des méthodologies éprouvées couramment pratiquées dans d’importants projets open source.
seo-description: AEM is developed following proven methodologies commonly practiced in large open source projects
uuid: ffef60ae-8a9a-4c4b-8cbd-3cd72792a42e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f52402df-f6dc-4c62-82bc-cbce489b2b74
exl-id: e07a42e2-c659-4991-b59a-d48bfb7d2972
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2745'
ht-degree: 76%

---

# Contribution à AEM{#contributing-to-aem}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Méthodologie de développement {#development-methodology}

AEM est développé selon des méthodologies éprouvées couramment pratiquées dans d’importants projets open source. De nombreux éléments de base de la pile technologique d’AEM sont en fait maintenus en tant que projets open source actifs, tels que Sling et Jackrabbit, qui ont contribué à The Apache Software Foundation. Un aspect majeur de cet esprit présent dans AEM est que vous êtes encouragé à utiliser les listes de diffusion et les forums en ligne disponibles pour des interactions directes avec l’équipe de développement.

Si vous contribuez à des composants d’AEM, vous devez vous familiariser avec AEM comme vous le feriez lorsque vous contribuez à un projet open source, et communiquer avec l’équipe principale existante comme vous le feriez lorsque vous avez l’intention de contribuer à un tel projet.

## Expérience requise {#required-experience}

Le protocole HyperText Transfer Protocol (HTTP) est au cœur de tous nos projets. Par conséquent, avant de contribuer à AEM, vous devez maîtriser HTTP, idéalement dans la mesure où vous devez être capable d’écrire votre propre implémentation Java d’un serveur HTTP multithread avec un pool de threads. Vous devez également maîtriser le comportement de persistance HTTP/1.1 et posséder une connaissance approfondie des interactions côté serveur/client avec JavaScript, en particulier du style asynchrone d’interaction représenté par AJAX.

Étant donné que le dynamisme des pages et le contenu interactif sont déterminants pour l’expérience WM, il est impératif que vous maîtrisiez le modèle d’objet de document et son potentiel pour la manipulation programmatique en réponse aux événements. Vous devez, par exemple, posséder des connaissances en matière de manipulation DOM en temps réel et de comportement de glisser-déposer sur plusieurs documents de navigateur (utilisation d’iframes, par exemple).

Au plus haut niveau, vous devez maîtriser les concepts suivants :

* le protocole[HTTP/1.1](https://www.ietf.org/rfc/rfc2616.txt)
* HTML (de préférence [HTML5](https://dev.w3.org/html5/spec/Overview.html))
* Feuilles de style en cascade
* Extensible Markup Language (XML)
* Modèles de conception JavaScript et XML (AJAX) asynchrones
* Notation d’objet JavaScript (JSON)
* Modèle d’objet de document
* Interactions avec ou sans état
* [Identifiants de ressources uniques](https://www.ietf.org/rfc/rfc2396.txt)
* Cookies de navigateur
* et d’autres concepts de développement web modernes

La pile technologique d’Adobe Experience Manager est basée sur le conteneur OSGI [Apache Felix](https://felix.apache.org/) avec le framework Web [Apache Sling](https://sling.apache.org/site/index.html). Elle intègre un référentiel de contenu Java ([JCR](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/index.html)) basé sur [Apache Jackrabbit](https://jackrabbit.apache.org/jcr-api.html). Vous devez vous familiariser avec ces projets individuels, ainsi qu’avec tous les autres composants open source (par exemple, Apache Lucene) utilisés dans le domaine où vous avez l’intention d’apporter une contribution.

## Connaissances tribales {#tribal-knowledge}

Certains concepts et principes directeurs sont profondément enracinés dans l’ancienne culture du développement. Cette section énumère quelques-uns des problèmes profondément ancrés que vous devez connaître.

### Tout est contenu {#everything-is-content}

Le contenu n’inclut pas seulement les données que l’application web conserve. Le code, les bibliothèques, scripts, modèles, HTML, CSS, images et artefacts de toutes sortes, absolument tout est conservé dans le référentiel de contenu et importé/exporté sous la forme de packages via le gestionnaire de packages et le partage de packages.

### Modèle de David {#david-s-model}

La façon dont le contenu doit être modélisé dans un référentiel de contenu Java nécessite une approche totalement différente de ce qui est courant dans le secteur du développement logiciel pour la modélisation de données dans le monde relationnel. Le guide [David’s Model: A guide for content modeling](https://wiki.apache.org/jackrabbit/DavidsModel) est une lecture incontournable pour tout débutant dans la gestion de contenu selon l’approche JCR.

### RESTfulness {#restfulness}

L’approche REST est profondément ancrée dans tous nos projets. Cela signifie, entre autres, d’éviter les interactions avec état et de garder à l’esprit que les URI sont des adresses définitives pour le contenu et les services.

REST (REpresentational State Transfer) fait référence à l’architecture logicielle sur laquelle le World Wide Web est basé. Il décrit les éléments clés qui font fonctionner le web et fournit ainsi un ensemble de principes pour la conception d’un logiciel basé sur le web. Lors de la conception d’une API à utiliser sur le Web, il est donc logique de respecter ces &quot;bonnes pratiques&quot;.

Dans la mesure où REST offre une approche que nous suivons dans nombreux de nos projets, vous devriez vous attacher à maîtriser les principes de la conception RESTful. Un bon point de départ est avec [La thèse de Roy Fielding](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).

### Résolution de requête Sling {#sling-request-resolution}

Dans AEM, il est impératif de cerner la relation entre les requêtes entrantes et le comportement du contenu et des applications, de comprendre la structure du contenu dans le référentiel de contenu et de savoir où AEM recherche la logique de l’application pour gérer la requête. En savoir plus sur Apache [Décomposition de l’URL Sling](https://sling.apache.org/site/url-decomposition.html) et la manière dont elle applique le style architectural REST et ses contraintes système sans état, pouvant être mises en cache et superposées.

Les aspects clés à comprendre sur la résolution des requêtes d’Apache Sling sont la manière dont les requêtes sont principalement mappées à une ressource spécifique dans le référentiel de contenu, la manière dont les propriétés supplémentaires de la requête, ainsi que les propriétés de ces objets de contenu, déterminent le code de l’application qui sera appelé pour le rendu du contenu, et la manière dont le code dans /apps remplace le code dans /libs.

### Démarrage rapide {#quickstart}

Pas de troisième étape : pour installer et exécuter, il suffit de télécharger et de double-cliquer sur le fichier JAR Quickstart. Il n’y a pas de troisième étape. Toute fonctionnalité facultative supplémentaire ne doit nécessiter rien de plus que l’installation du package approprié à partir du partage de modules.

Petite taille du fichier Quickstart : conservez la taille minimale du fichier JAR Quickstart. Faites une utilisation intelligente et optimisée des bibliothèques, en déplaçant les fonctionnalités facultatives vers le partage de packages.

Temps de démarrage plus rapide : Lorsque vous effectuez une modification susceptible d’affecter le temps de démarrage, veillez à ce qu’elle soit plus courte et non plus longue.

### Lean et Mean {#lean-and-mean}

Nous privilégions le code et les projets qui sont légers, petits, rapides et élégants. &quot;Assez bien&quot; n&#39;est pas suffisant.

Réutilisation du code : notre architecture de produits basée sur OSGi et notre approche « tout est contenu » signifie que nous nous donnons plus d’occasions de réutiliser le code et les artefacts. Nous essayons d&#39;en profiter chaque fois que possible pour garder les fonctionnalités minces et moyennes.

Couplage lâche : nous privilégions les interactions à couplage faible à des dépendances étroites et des échanges trop serrés non souhaités. Le couplage faible permet également une réutilisation du code.

### Ne pas casser la démo {#don-t-break-the-demo}

Familiarisez-vous avec les scripts de démonstration et les fonctionnalités des produits qui sont le plus souvent présentés dans les démos. Sachez que rien de ce que vous codez ne doit endommager une fonctionnalité de « script de démonstration ». Le produit principal doit toujours être prêt pour la démonstration, même pendant le développement.

### Conception pour la fiabilité {#design-for-reliability}

Nous nous efforçons de concevoir et de coder les fonctionnalités sans qu’un bogue n’ai de lourdes répercussions. Par exemple, il faut éviter qu’un problème lié à un seul élément DOM empêche le rendu de toute une page. En d’autres termes : laisser ce qui doit être fatal l’être. Tout le reste doit être viable. Faites &quot;pardonner&quot; le produit.

### La nouvelle normalité est anormale {#abnormal-is-the-new-normal}

Ne dépendez pas des shutdown hooks, nettoyez au démarrage. Un arrêt anormal est un arrêt normal.

`shutdown == kill -9 == power outage`

### Se tenir prêt pour un clustering élastique {#be-ready-for-elastic-clustering}

Soyez toujours prêt pour un clustering élastique, supposez toujours qu’il y a un clustering. En règle générale, le respect de tout ce qui réside dans le référentiel de contenu signifie une prise en charge de clustering intégré.

### Une conception avec une compatibilité ascendante {#design-for-backward-compatibility}

Rien de ce que vous codez ne doit endommager l’ancien code d’un client. N’utilisez que la `/libs` pour stocker le code du produit qui peut être mis à jour pendant une mise à niveau. La section `/apps` du référentiel est le code du projet et `/etc` contient des configurations personnalisées qui doivent être conservées. En règle générale, ne remplacez rien dans `/content`, `/apps` et `/home`. Après une mise à niveau, l’ancien code de projet, les configurations et le contenu doivent continuer à fonctionner comme avant la mise à niveau.

Une conception prenant en charge la rétrocompatibilité garantit également que l’expérience de mise à niveau correspond à la simplicité de l’installation initiale. Il suffit en principe d’arrêter AEM, de remplacer le fichier JAR Quickstart et de redémarrer AEM. Avec une base d’installation en pleine expansion, une efficace optimale est un avantage de plus en plus recherché.

Même si les API existantes peuvent et doivent être rendues obsolètes lorsqu’une fonctionnalité plus récente et plus performante les remplace, toutes les API rendues publiques dans une version 5.x précédente doivent rester fonctionnelles, car elles peuvent être utilisées dans le code d’application personnalisé. Aucune API de ce type ne doit être supprimée.

La rétrocompatibilité doit également être gardée à l’esprit en ce qui concerne la cohérence générale de la structure du contenu et de l’expérience utilisateur.

## Concepts de base {#core-concepts}

**Instance d’auteur** - Généralement, pour des raisons de sécurité, de gouvernance et autres, un site de exploitation divise les instances d’AEM en instances de création et de publication. Pour plus d’informations sur l’architecture de déploiement (y compris les instances de création et de publication), consultez la documentation relative aux instances AEM.

**Caching, frying et baking** - Traditionnellement, les concepts de baking et de frying sont une distinction importante entre différents systèmes de gestion de contenu Web. Dans le jargon CMS, le « baking » fait référence au concept de validation de données dans des fichiers statiques au moment de la publication, tandis que le « frying » fait référence au concept de traitement des données pour la présentation finale au moment de la requête (juste à temps).

**Clustering et équilibrage de charge** - Pour augmenter la disponibilité et améliorer les performances d’un environnement d’exploitation, il est courant de combiner plusieurs instances de création et/ou de publication (en clusters), soit en les mettant à la disposition de différents groupes d’utilisateurs, soit en équilibrant leur charge derrière une configuration du dispatcher.

Il est également possible de combiner plusieurs instances du référentiel de contenu pour créer une solution JCR *haute disponibilité*, laquelle peut ensuite être intégrée à votre solution AEM pour optimiser la protection contre les défaillances matérielles et logicielles. Consultez [Déploiements recommandés](/help/sites-deploying/recommended-deploys.md#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter) pour plus d’informations.

**Composant** - Dans AEM, un composant est un type d’objet dont les instances peuvent généralement être créées en les faisant glisser depuis le sidekick, par exemple. Ainsi, par exemple, les composants prêts à l’emploi fournis avec AEM incluent les composants Texte, Titre, Nuage de balises, Carrousel, Image et Liste, tous disponibles depuis le sidekick au moment de l’exécution.

**Outil de recherche de contenu** - En mode création, l’outil de recherche de contenu est un panneau spécial (frame) sur le côté gauche de la page qui, selon l’onglet que vous sélectionnez en haut, affiche des listes d’images, de documents, des éléments Flash, des pages, des paragraphes ou des ressources de référentiel que vous pouvez faire glisser de l’outil de recherche de contenu vers la page dans laquelle vous travaillez (sur la droite).

**Eléments numériques** Dans AEM, les ressources numériques sont (généralement) des images et des fichiers multimédias. Pour plus d’informations, consultez Utilisation des ressources numériques dans la gestion des ressources numériques.

**Dispatcher** - Le Dispatcher est un outil de mise en cache et d’équilibrage de charge qui fournit certaines mesures de sécurité.

**Widgets ExtJS** - La plupart des éléments d’interface utilisateur d’AEM utilisent ExtJS, qui est une bibliothèque de widgets tiers écrite en JavaScript. ExtJS offre des widgets d’IU personnalisables et haute performance ainsi qu’un modèle de composant bien conçu et extensible.

**JCR, Java Content Repository** - La spécification de référentiel de contenu Java (JSR-283) fournit à la fois un modèle de données abstrait et une interface de programmation d’application pour élaborer un référentiel de données NoSQL massivement évolutif qui combine les fonctionnalités d’un système de fichiers et d’une base de données objet. Bien que vous n’ayez pas besoin de comprendre le JSR-283 en détail, vous devriez prendre le temps de vous familiariser avec les fonctionnalités de base de JCR et le modèle de données qui le sous-tend, car JCR est ce qui rend possible la philosophie &quot;tout est contenu&quot; de l’AEM.

En substance, JCR est un système de nœuds et de propriétés, dans lequel les nœuds peuvent hériter des autres nœuds et tout le contenu est stocké en tant que *valeurs* de propriété. Notez qu’en plus de l’héritage ordinaire, JCR autorise un concept de noeuds &quot;mixin&quot;, ce qui permet la modélisation de l’héritage multiple.

JCR possède un certain nombre de types de nœuds prédéfinis et de types de propriétés, mais en général le système de typage est assez flexible et (d’ailleurs) l’une des forces de JCR est qu’il permet de facilement stocker/gérer le contenu structuré et non structuré. En d’autres termes, JCR peut s’adapter à des données hautement structurées, mais il peut également s’adapter à des structures de données dynamiques arbitraires sans contraintes de schéma.

L’API Java de JavaDoc pour JCR est disponible [ici](http://jackrabbit.apache.org/jcr/jcr-api.html).

Avant de lire la spécification JavaDoc ou JCR elle-même, vous pouvez consulter [cette explication d’expert](/help/sites-developing/the-basics.md#java-content-repository) sur JCR, telle qu’elle est implémentée par Adobe Experience Services.

**Multi-Site Manager (MSM)** - La fonctionnalité MSM d’AEM aide les clients à gérer le contenu multilingue et multinational pour uniformiser leur branding centralisé avec du contenu localisé.

**OSGi** - OSGi est la technologie d’exécution orientée services qui constitue la base du développement Java modulaire dans AEM. C’est un framework qui fournit non seulement un environnement de chargement de classes hautement dynamique (et sécurisé) pour les ressources de code (appelés bundles), mais aussi un contrôle complet de la visibilité et du cycle de vie des différents services exposés par des bundles. Un registre de services fournit un modèle de coopération pour les bundles qui tient compte de la dynamique du cycle de vie (et des exigences de version). OSGi résout de nombreux problèmes que les serveurs d’applications étaient censés résoudre, mais de manière légère et très dynamique, ce qui permet, par exemple, de déployer à chaud des services (rendant le nouveau code immédiatement disponible sans redémarrer le serveur).

**Parsys, système de paragraphes** - Le système de paragraphe (parsys) est un composant composé qui permet aux auteurs d’ajouter des composants de différents types à une page et qui contient tous les autres composants de paragraphe. Chaque type de paragraphe est représenté en tant que composant. Le système de paragraphes lui-même est également un composant, qui contient les autres composants de paragraphe.

**Microkernel** - Chaque espace de travail du référentiel peut être configuré séparément pour stocker ses données via un micro-noyau spécifique (classe qui gère la lecture et l’écriture des données). De même, le magasin de versions à l’échelle du référentiel peut également être configuré indépendamment pour utiliser un micro-noyau particulier. Plusieurs micro-noyaux différents sont disponibles et capables de stocker des données dans une variété de formats de fichiers ou de bases de données relationnelles. (Par exemple, il existe des gestionnaires de persistance pour MongoDB, DB2 ou Oracle). Le micro-noyau par défaut pour AEM est TarMK (voir plus loin).

**Instance de publication** - Généralement, pour des raisons de sécurité, de gouvernance et autres, un site d’exploitation divise les instances d’AEM en instances de création et de publication. Pour plus d’informations sur l’architecture de déploiement (y compris les instances de création et de publication), consultez la documentation relative aux instances AEM.

**Démarrage rapide** - Contrairement à beaucoup d’autres programmes, AEM s’installe à l’aide d’un seul fichier JAR auto-extractable Quickstart. Lorsque vous double-cliquez sur le fichier JAR pour la première fois, tout ce dont vous avez besoin est automatiquement installé. Le fichier JAR Quickstart comprend tous les fichiers requis pour le référentiel CRX (y compris les fonctions administratives), les services de référentiel virtuel, les services d’indexation et de recherche, les services de workflow, la sécurité et un serveur web, ainsi que le CQ Servlet Engine (CQSE) et les services AEM. Il n’y a pas d’autres fichiers à installer : Quickstart est autonome.

La première fois que vous lancez Quickstart, il crée en arrière-plan un référentiel complet compatible JCR, ce qui peut prendre plusieurs minutes. Après ce démarrage initial, les démarrages suivants sont beaucoup plus rapides, car l’infrastructure de référentiel a déjà été définie.

De nombreuses options de démarrage (telles que le numéro de port actif et le fait d’indiquer si l’instance AEM en question doit être une instance de publication ou une instance de création, et bien d’autres) peuvent être contrôlées en renommant le fichier Quickstart de manière appropriée. Pour afficher la liste des options à cet égard, exécutez le fichier JAR avec &quot;-help&quot; sur la ligne de commande :

```shell
java -jar <quickstartfilename>.jar -help
```

**Agents de réplication** - Les agents de réplication sont au cœur d’AEM et forment le mécanisme utilisé pour Publier (activer) le contenu d’un auteur dans un environnement de publication, vider le contenu du cache du Dispatcher, renvoyer le contenu généré par l’utilisateur (par exemple, la saisie de formulaire) depuis l’environnement de publication vers l’environnement de création.

**Génération de modèles automatique** : grâce à la génération de modèles automatique, vous pouvez créer un formulaire (que l’on désigne sous le nom de modèle automatique) dont les champs représentent la structure souhaitée pour vos pages, puis l’utiliser afin de créer aisément des pages sur la base de cette structure.

**Segments** - Les visiteurs de site se rendent sur un site en fonction d’intérêts et d’objectifs divers. Le fait de comprendre ces objectifs et de satisfaire à leurs attentes est un important facteur de réussite en matière de marketing en ligne. La segmentation permet d’y parvenir en analysant et en profilant le visiteur :

**Sidekick** - Le Sidekick est une fenêtre flottante de type palette visible dans la page modifiable à partir de laquelle les nouveaux composants peuvent être déplacés et les actions qui s’appliquent à la page peuvent être exécutées.

**SiteCatalyst** - SiteCatalyst offre aux spécialistes du marketing un seul endroit pour mesurer, analyser et optimiser les données intégrées de toutes les initiatives en ligne sur plusieurs canaux marketing. Vous pouvez utiliser Adobe SiteCatalyst pour analyser les données des sites Web AEM.

**Stockage Tar (TarMK)** - TarMK est le système de persistance par défaut dans AEM. Bien qu’AEM puisse être configuré pour utiliser un autre système de persistance (tel que MongoDB), TarMK présente certains avantages en ce sens qu’il est optimisé pour les utilisations classiques de JCR (donc très rapide), utilise un format de données standard et peut être sauvegardé rapidement et facilement.

**Modèle** - Dans AEM, un modèle spécifie un type de page spécialisé. Il définit la structure d’une page (tout en spécifiant généralement une image miniature et diverses propriétés). Par exemple, vous pouvez avoir des modèles distincts pour les pages de produits, les plans de site et les informations de contact.

**Workflow** - Le système de Workflow AEM permet la création de processus automatisés associés à des pages ou des ressources.
