---
title: Modélisation des données – Modèle de David Nuescheler
seo-title: Data Modeling - David Nuescheler's Model
description: Recommandations de David Nuescheler en matière de modélisation de contenu
seo-description: David Nuescheler's content modelling recommendations
uuid: acb27e81-9143-4e0d-a37a-ba26491a841f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 39546c0a-b72f-42df-859b-98428ee0d5fb
exl-id: 44a54278-f4b0-487f-95d5-d222778dffe9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1854'
ht-degree: 25%

---

# Modélisation des données – Modèle de David Nuescheler{#data-modeling-david-nuescheler-s-model}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Source {#source}

Les détails suivants sont des idées et des commentaires exprimés par David Nuescheler.

David a été co-fondateur et directeur technique de Day Software AG, un fournisseur leader de logiciels d’infrastructure de contenu et de gestion de contenu mondial, qui a été acquis par Adobe en 2010. Il est désormais membre et vice-président de la technologie d’entreprise chez Adobe et dirige également le développement de JSR-170, l’interface de programmation d’application (API) de Java Content Repository (JCR), la norme technologique pour la gestion de contenu.

Vous trouverez d’autres informations à l’adresse suivante : [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

## Présentation de David {#introduction-from-david}

Au cours de diverses discussions, j’ai constaté que les développeurs sont un peu mal à l’aise avec les fonctionnalités présentées par JCR en matière de modélisation de contenu. Il n’existe pas de guide et très peu d’expérience pour le moment sur la façon de modéliser le contenu dans un référentiel et pourquoi un modèle de contenu est meilleur que l’autre.

Bien que dans le monde relationnel, le secteur du logiciel ait une grande expérience de la manière de modéliser les données, nous en sommes encore aux premiers stades pour l’espace de référentiel de contenu.

Je voudrais commencer à combler ce vide en exprimant mes opinions personnelles sur la façon dont le contenu doit être modélisé, en espérant qu&#39;un jour cela pourrait devenir quelque chose de plus significatif pour la communauté des développeurs, qui n&#39;est pas seulement &quot;mon opinion&quot; mais quelque chose de plus largement applicable. Considérez que c&#39;est mon premier coup de poignet qui évolue rapidement.

>[!NOTE]
>
>Clause de non-responsabilité : ces lignes directrices sont l’expression de mes opinions personnelles, qui sont parfois sujettes à controverse. Je suis impatient d’en discuter et de les affiner.

## Sept règles simples {#seven-simple-rules}

### Règle n°1 : l es données d’abord, la structure ensuite. Normalement… {#rule-data-first-structure-later-maybe}

#### Explication {#explanation-1}

Je vous recommande de ne pas vous soucier d&#39;une structure de données déclarée au sens de l&#39;ERD. Initialement.

Apprenez à aimer nt:unstructured (&amp; amis) dans le développement.

Je pense que Stefano résume cela assez bien.

Mon bilan : La structure est coûteuse et, dans de nombreux cas, il est totalement inutile de déclarer explicitement la structure au stockage sous-jacent.

Il existe un contrat implicite sur la structure que votre application utilise par nature. Supposons que je stocke la date de modification d’une publication de blog dans une propriété lastModified. Mon application saura automatiquement lire à nouveau la date de modification à partir de cette même propriété. Il n’est vraiment pas nécessaire de la déclarer explicitement.

D’autres contraintes sur les données, telles que les contraintes obligatoires ou de type et de valeur, ne doivent être appliquées que si nécessaire pour des raisons d’intégrité des données.

#### Exemple {#example-1}

L’exemple d’utilisation de la propriété de date `lastModified` sur un nœud « article de blog » ne signifie pas vraiment qu’il faut utiliser un type de nœud particulier. Je vais à coup sûr utiliser `nt:unstructured` pour mes nœuds d’article de blog, du moins au début. Puisque, dans mon application de création de blog, je vais simplement afficher la date de la dernière modification (éventuellement en exécutant la fonction « classer par »), je me soucie peu s’il s’agit d’une date. Étant donné que je fais implicitement confiance à mon application de création de blog pour placer une « date » à cet endroit, il n’est aucunement nécessaire de déclarer la présence d’une date `lastModified` sous la forme d’un type de nœud.

### Règle n°2 : prenez le contrôle de la hiérarchie de contenu, ne la laissez pas vous diriger. {#rule-drive-the-content-hierarchy-don-t-let-it-happen}

#### Explication {#explanation-2}

La hiérarchie du contenu est un actif très précieux. Ne laissez pas simplement les choses se faire, prenez en main la conception ! Si vous ne disposez pas d’un nom facilement lisible pour un nœud, vous devriez y réfléchir un peu plus. Les nombres arbitraires ne sont pratiquement jamais un &quot;bon nom&quot;.

Bien qu&#39;il soit extrêmement facile de placer rapidement un modèle relationnel existant dans un modèle hiérarchique, il faut y réfléchir.

Dans mon expérience, si l’on pense au contrôle d’accès et au confinement, il s’agit généralement de bons pilotes pour la hiérarchie du contenu. Pensez-y comme si c&#39;était votre système de fichiers. Vous pouvez peut-être même utiliser des fichiers et des dossiers pour le modéliser sur votre disque local.

Personnellement, je préfère les conventions de hiérarchie plutôt que le système de frappe de noeud dans de nombreux cas au départ, et j&#39;introduis la saisie plus tard.

>[!CAUTION]
>
>La structure d’un référentiel de contenu peut également avoir un impact sur les performances. Pour de meilleures performances, le nombre de noeuds enfants attachés à des noeuds individuels dans un référentiel de contenu ne doit généralement pas dépasser 1 000.
>
>Pour plus d’informations, reportez-vous à la section [Quelle quantité de données CRX peut-il traiter ?](https://helpx.adobe.com/fr/experience-manager/kb/CrxLimitation.html) pour plus d’informations.

#### Exemple {#example-2}

Je modéliserais un simple système de blogs comme suit. Veuillez noter qu’au départ, je ne me soucie même pas des types de noeuds respectifs que j’utilise à ce stade.

```xml
/content/myblog
/content/myblog/posts
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping

/content/myblog/comments/iphone_shipping/i_like_it_too
/content/myblog/comments/iphone_shipping/i_like_it_too/i_hate_it
```

Il est évident que nous comprenons tous la structure du contenu sur la base de l’exemple, sans qu’aucune autre explication ne soit nécessaire.

Ce qui peut être inattendu dans un premier temps, c&#39;est pourquoi je ne stockerais pas les &quot;commentaires&quot; avec le &quot;post&quot;, ce qui est dû au contrôle d&#39;accès que je voudrais appliquer d&#39;une manière raisonnablement hiérarchique.

En utilisant le modèle de contenu ci-dessus, je peux facilement permettre à l’utilisateur &quot;anonyme&quot; de &quot;créer&quot; des commentaires, mais de garder l’utilisateur anonyme en lecture seule pour le reste de l’espace de travail.

### Règle #3 : Les espaces de travail sont destinés à clone(), merge() et update(). {#rule-workspaces-are-for-clone-merge-and-update}

#### Explication {#explanation-3}

Si vous n’utilisez pas de méthode `clone()`, `merge()` ou `update()` dans votre application, l’espace de travail unique est probablement la voie à suivre.

&quot;Noeuds correspondants&quot; est un concept défini dans la spécification JCR. Essentiellement, il se résume à des noeuds qui représentent le même contenu, dans différents soi-disant espaces de travail.

JCR introduit le concept très abstrait des espaces de travail, ce qui laisse beaucoup de développeurs mal informés sur ce qu’ils peuvent en faire. Je vous propose de mettre à l’épreuve votre utilisation des espaces de travail comme suit.

Si vous avez un chevauchement considérable des noeuds &quot;correspondants&quot; (essentiellement les noeuds avec le même UUID) dans plusieurs espaces de travail, vous pouvez probablement utiliser les espaces de travail à bon escient.

S’il n’existe aucun chevauchement de noeuds avec le même UUID, vous abusez probablement des espaces de travail.

Les espaces de travail ne doivent pas être utilisés pour le contrôle d’accès. La visibilité du contenu pour un groupe d’utilisateurs spécifique n’est pas un bon argument pour séparer les éléments dans différents espaces de travail. JCR propose un &quot;contrôle d’accès&quot; dans le référentiel de contenu pour y répondre.

Les espaces de travail sont la limite des références et des requêtes.

#### Exemple {#example-3}

Utilisez des espaces de travail pour des éléments tels que :

* v1.2 de votre projet par rapport à la version v1.3 de votre projet
* un &quot;développement&quot;, un &quot;contrôle qualité&quot; et un état de contenu &quot;publié&quot; ;

N’utilisez pas d’espaces de travail pour des éléments tels que :

* répertoires d’accueil des utilisateurs
* contenu distinct pour différentes audiences cibles, telles que public, privé, local, etc.
* boîtes de réception pour différents utilisateurs

### Règle #4 : Attention aux frères du même nom. {#rule-beware-of-same-name-siblings}

#### Explication {#explanation-4}

Bien que les SNS (Same Name Siblings) aient été introduits dans la spécification afin de permettre la compatibilité avec des structures de données conçues et exprimées au moyen de XML et qui sont donc extrêmement utiles pour JCR, ils offrent une surcharge et une complexité importantes pour le référentiel.

Tout chemin d’accès dans le référentiel de contenu qui contient un SNS dans l’un de ses segments de chemin devient beaucoup moins stable. Si un SNS est supprimé ou réorganisé, il a un impact sur les chemins de tous les autres SNS et de leurs enfants.

Pour l&#39;import de code XML ou l&#39;interaction avec des codes SNS XML existants peut-être nécessaire et utile, mais je n&#39;ai jamais utilisé de code SNS, et je ne le ferai jamais dans mes modèles de données &quot;champ vert&quot;.

#### Exemple {#example-4}

Utilisez

```xml
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping
```

au lieu de

```xml
/content/blog[1]/post[1]
/content/blog[1]/post[2]
```

### Règle #5 : Les références sont considérées comme nocives. {#rule-references-considered-harmful}

#### Explication {#explanation-5}

Les références impliquent une intégrité référentielle. Je trouve important de comprendre que les références n’ajoutent pas seulement des coûts supplémentaires pour le référentiel qui gère l’intégrité référentielle, mais qu’elles sont également coûteuses du point de vue de la flexibilité du contenu.

Personnellement, je m&#39;assure que je n&#39;utilise jamais de références que lorsque je ne peux vraiment pas gérer une référence agressive et utiliser autrement un chemin, un nom ou un UUID de chaîne pour faire référence à un autre noeud.

#### Exemple {#example-5}

Supposons que j’autorise les &quot;références&quot; d’un document (a) à un autre document (b). Si je modélise cette relation à l’aide de propriétés de référence, cela signifie que les deux documents sont liés au niveau du référentiel. Je ne peux pas exporter/importer le document (a) individuellement, car la cible de la propriété de référence n’existe peut-être pas. D’autres opérations telles que la fusion, la mise à jour, la restauration ou le clonage sont également affectées.

Je vais donc soit modéliser ces références comme &quot;références faibles&quot; (dans JCR v1.0, cela se résume essentiellement aux propriétés de chaîne qui contiennent l’uuid du noeud cible), soit utiliser simplement un chemin d’accès. Parfois, le chemin est plus significatif pour commencer.

Je pense qu&#39;il y a des cas d&#39;utilisation où un système ne peut vraiment pas fonctionner si une référence est pendouillante, mais je ne peux simplement pas trouver un bon exemple &quot;réel&quot; mais simple de mon expérience directe.

### Règle n°6 : des fichiers sont des fichiers. {#rule-files-are-files}

#### Explication {#explanation-6}

Si un modèle de contenu expose quelque chose qui, même de loin, *ressemble* à un fichier ou un dossier, j’essaie d’utiliser (ou de développer à partir de) `nt:file`, `nt:folder` et `nt:resource`.

Dans mon expérience, de nombreuses applications génériques permettent d’interagir implicitement avec nt:folder et nt:files et savent gérer et afficher ces événements s’ils sont enrichis de méta-informations supplémentaires. Par exemple, une interaction directe avec des implémentations de serveur de fichiers comme CIFS ou WebDAV assis sur le JCR devient implicite.

Je pense qu’il est judicieux d’appliquer la méthode suivante : si vous devez stocker le nom de fichier et le type MIME, `nt:resource`/`nt:file` convient parfaitement. Si vous pouvez avoir plusieurs « fichiers », nt:folder constitue l’emplacement de stockage idéal.

Si vous devez ajouter des méta-informations pour votre ressource (une propriété « description » ou « auteur », par exemple), étendez `nt:resource` et non `nt:file`. J’étends rarement un nt:file, mais souvent un `nt:resource`.

#### Exemple {#example-6}

Supposons que quelqu’un souhaite télécharger une image dans une entrée de blog à l’adresse :

```xml
/content/myblog/posts/iphone_shipping
```

et peut-être que la première réaction intestinale serait d&#39;ajouter une propriété binaire contenant l&#39;image.

Bien qu’il existe certainement de bons cas d’utilisation d’une seule propriété binaire (supposons que le nom n’est pas pertinent et que le type MIME soit implicite), je recommande la structure suivante pour mon exemple de blog.

```xml
/content/myblog/posts/iphone_shipping/attachments [nt:folder]
/content/myblog/posts/iphone_shipping/attachments/front.jpg [nt:file]
/content/myblog/posts/iphone_shipping/attachments/front.jpg/jcr:content [nt:resource]
```

### Règle #7 : Les identifiants sont mauvais. {#rule-ids-are-evil}

#### Explication {#explanation-7}

Dans les bases de données relationnelles, les identifiants sont un moyen nécessaire pour exprimer les relations. Les gens ont donc tendance à les utiliser également dans les modèles de contenu. Surtout pour les mauvaises raisons.

Si votre modèle de contenu est plein de propriétés qui se terminent par &quot;Id&quot;, vous n’utilisez probablement pas correctement la hiérarchie.

Il est vrai que certains noeuds ont besoin d’une identification stable tout au long de leur cycle de vie. Beaucoup moins que ce que vous pourriez penser. mix:referenceable fournit un tel mécanisme intégré dans le référentiel. Il n’est donc pas nécessaire de trouver un moyen supplémentaire d’identifier un noeud de manière stable.

Gardez également à l’esprit que les éléments peuvent être identifiés par chemin d’accès et que les &quot;liens symboliques&quot; sont plus logiques pour la plupart des utilisateurs que les liens matériels dans un système de fichiers unix, un chemin d’accès est logique pour la plupart des applications pour faire référence à un noeud cible.

Plus important encore : **mix**:referenceable signifie qu’il peut être appliqué à un nœud au moment où il est vraiment nécessaire de le référencer.

Dès lors, ce n’est pas parce que vous aimeriez être en mesure de référencer un nœud de type « Document » que votre type de nœud « Document » doit s’étendre de manière statique depuis mix:referenceable, car il peut être ajouté de façon dynamique à n’importe quelle instance du « Document ».

#### Exemple {#example-7}

Utilisez :

```xml
/content/myblog/posts/iphone_shipping/attachments/front.jpg
```

au lieu de :

```xml
[Blog]
-- blogId
-- author
[Post]
-- postId
-- blogId
-- title
-- text
-- date
[Attachment]
-- attachmentId
-- postId
-- filename
+ resource (nt:resource)
```
