---
title: Cadre de balisage AEM
seo-title: AEM Tagging Framework
description: Balisage de contenu et utilisation du cadre de balisage AEM
seo-description: Tag content and leverage the AEM Tagging infrastructure
uuid: 55ba5977-217b-4b0f-a794-ddb9216ee62b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 4b680d17-383b-4173-a444-0b7bdb24e6c8
feature: Tagging
exl-id: bae592db-dc36-409f-b841-0582c464c3f6
source-git-commit: 381e760d1634dec6c6cdb933fd4da6b4652e6ff7
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 66%

---

# Framework de balisage AEM{#aem-tagging-framework}

Pour baliser le contenu et exploiter l’infrastructure de balisage AEM :

* La balise doit exister en tant que nœud du type [`cq:Tag`](#tags-cq-tag-node-type) sous le [nœud racine de taxonomie.](#taxonomy-root-node)
* Le `NodeType` du nœud de contenu balisé doit inclure le mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin).
* Le [TagID](#tagid) est ajouté au noeud de contenu [`cq:tags`](#tagged-content-cq-tags-property) et correspond à un noeud de type [`cq:Tag`.](#tags-cq-tag-node-type)

## Balises : type de nœud cq:Tag  {#tags-cq-tag-node-type}

La déclaration d’une balise est capturée dans le référentiel dans un nœud de type `cq:Tag.`.

Une balise peut être un mot simple (par exemple, `fruit`) ou représentent une taxonomie hiérarchique (par exemple, `fruit/apple`, c&#39;est-à-dire les fruits en général et la pomme plus spécifique).

Les balises sont identifiées par un identifiant unique.

Une balise contient des métadonnées facultatives telles qu’un titre, des titres localisés et une description. Le titre doit être affiché dans les interfaces utilisateur au lieu du `TagID`, le cas échéant.

Le framework de balisage offre également la possibilité de contraindre les auteurs et les visiteurs du site à n’utiliser que des balises prédéfinies spécifiques.

### Caractéristiques de la balise {#tag-characteristics}

* Le type de noeud est `cq:Tag`.
* Le nom du nœud est un composant de [`TagID`.](#tagid)
* Le [`TagID`](#tagid) contient toujours un [espace de noms.](#tag-namespace)
* Facultatif `jcr:title` (titre à afficher dans l’interface utilisateur)
* Facultatif `jcr:description` property
* Lorsqu’il contient des noeuds enfants, il est appelé [balise conteneur.](#container-tags)
* Il est stocké dans le référentiel sous un chemin de base appelé [noeud racine de taxonomie.](#taxonomy-root-node)

### TagID {#tagid}

Un `TagID` identifie un chemin d’accès qui est résolu sur un nœud de balise dans le référentiel.

En règle générale, la variable `TagID` est un raccourci commençant par l’espace de noms ou il peut être absolu à partir de la fonction [noeud racine de taxonomie](#taxonomy-root-node).

Lorsque le contenu est balisé, s’il n’existe pas encore, la variable [`cq:tags`](#tagged-content-cq-tags-property) est ajoutée au noeud de contenu et la propriété `TagID` est ajouté à la valeur du tableau de chaîne de la propriété.

Le `TagID` se compose d’un [espace de noms](#tag-namespace), suivi du `TagID` local. Les [balises conteneurs](#container-tags) contiennent des sous-balises qui représentent un ordre hiérarchique dans la taxonomie. Des sous-balises peuvent être utilisées pour référencer des balises identiques à tout `TagID` local. Par exemple, baliser du contenu avec `fruit` est autorisé, même s’il s’agit d’une balise conteneur avec des sous-balises, comme `fruit/apple` et `fruit/banana`.

### Nœud racine de taxonomie {#taxonomy-root-node}

Le nœud racine de taxonomie est le chemin d’accès de base pour toutes les balises du référentiel. Le nœud racine de taxonomie ne peut pas être un nœud de type `cq:Tag`.

Dans AEM, le chemin d’accès de base est `/content/cq:tags` et le nœud racine est de type `cq:Folder`.

### Espace de noms des balises {#tag-namespace}

Les espaces de noms permettent des activités de groupe. Le cas d’utilisation le plus courant consiste à disposer d’un espace de noms par site (par exemple, public, interne et portail) ou par application plus grande (par exemple, Sites, Ressources, Forms), mais les espaces de noms peuvent être utilisés pour d’autres besoins. Les espaces de noms sont utilisés dans l’interface utilisateur pour n’afficher que le sous-ensemble de balises (c’est-à-dire les balises d’un espace de noms donné) applicable au contenu actuel.

L’espace de noms de la balise est le premier niveau de la sous-arborescence de taxonomie, à savoir le nœud situé juste en dessous du [nœud racine de taxonomie](#taxonomy-root-node). Un espace de noms est un nœud de type `cq:Tag` dont le parent n’est pas de type `cq:Tag`.

Toutes les balises possèdent un espace de noms. Si aucun espace de noms n’est spécifié, la balise est affectée à l’espace de noms par défaut, qui est `TagID` `default` (le titre est `Standard Tags`) qui est `/content/cq:tags/default`.

### Balises conteneurs {#container-tags}

Une balise conteneur est un nœud de type `cq:Tag` contenant le nombre et le type des nœuds enfants, ce qui permet d’enrichir le modèle de balise avec des métadonnées personnalisées.

En outre, les balises conteneur (ou super-balises) d’une taxonomie servent de sous-résumé de toutes les sous-balises. Par exemple, du contenu balisé avec `fruit/apple` est considéré comme balisé avec `fruit` ainsi que . Cela signifie que la recherche de contenu simplement balisé avec `fruit` trouverait également le contenu balisé avec `fruit/apple`.

### Résolution d’ID de balise {#resolving-tagids}

Si l’ID de balise contient deux points `:`, le deux-points sépare l’espace de noms de la balise ou de la sous-taxonomie, qui sont ensuite séparés par des barres obliques normales. `/`. En l’absence de signe deux-points dans l’ID de balise, l’espace de noms par défaut est impliqué.

`/content/cq:tags` constitue l’emplacement standard des balises, mais aussi le seul.

Balisage faisant référence à des chemins ou chemins non existants qui ne pointent pas vers un `cq:Tag` sont considérés comme non valides et sont ignorés.

Le tableau suivant présente un exemple : `TagIDs`, leurs éléments et la manière dont la variable `TagID` résout en un chemin absolu dans le référentiel.

| `TagID` | Espace de noms | ID local | Balise(s) conteneur(s) | Balise feuille | Chemin d’accès absolu au référentiel |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Aucun | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Aucun | Aucun | Aucun | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Localisation du titre de balise {#localization-of-tag-title}

Lorsque la balise comprend une chaîne de titre facultative (`jcr:title`), il est possible de localiser le titre à afficher en ajoutant la propriété `jcr:title.<locale>`.

Pour plus d’informations, consultez :

* [Balises dans différentes langues,](/help/sites-developing/building.md#tags-in-different-languages) qui décrit l’utilisation des API.
* [Gestion des balises dans différentes langues,](/help/sites-administering/tags.md#managing-tags-in-different-languages) qui décrit l’utilisation de la console Balisage.

### Contrôle d’accès {#access-control}

Les balises existent sous la forme de nœud dans le répertoire sous le [nœud racine de taxonomie.](#taxonomy-root-node) Il est possible d’autoriser ou de refuser aux auteurs et aux visiteurs du site la possibilité de créer des balises dans un espace de noms donné en définissant des listes de contrôle d’accès appropriées dans le référentiel.

En outre, le refus d’autorisations de lecture pour certaines balises ou espaces de noms contrôle la possibilité d’appliquer des balises à un contenu spécifique.

Une configuration standard inclut :

* Accorder au groupe/rôle `tag-administrators` l’accès en écriture à tous les espaces de noms (add/modify sous `/content/cq:tags`).
   * Ce groupe est fourni en standard avec AEM.
* Accorder aux utilisateurs/auteurs l’accès en lecture à tous les espaces de noms qu’ils doivent être autorisés à lire (presque tous).
* Accorder aux utilisateurs/auteurs l’accès en écriture aux espaces de noms dont ils doivent être en mesure de définir librement les balises (`add_node` sous `/content/cq:tags/some_namespace`).

## Contenu pouvant être balisé : mixin cq:Taggable {#taggable-content-cq-taggable-mixin}

Pour que les développeurs d’application attachent le balisage à un type de contenu, l’enregistrement du nœud ([CND](https://jackrabbit.apache.org/node-type-notation.html)) doit inclure le mixin `cq:Taggable` ou `cq:OwnerTaggable`.

Le mixin `cq:OwnerTaggable`, qui hérite de `cq:Taggable`, sert à indiquer que le contenu peut être classé par propriétaire/auteur. Dans AEM, il s’agit uniquement d’un attribut du nœud `cq:PageContent`. Le mixin `cq:OwnerTaggable` n’est pas requis par le cadre de balisage.

>[!NOTE]
>
>Il est recommandé de n’activer les balises que sur le nœud de niveau supérieur d’un élément de contenu agrégé (ou sur son nœud `jcr:content`). Voici quelques exemples :
>
>* Pages ( `cq:Page`) où la variable `jcr:content`Le noeud est de type `cq:PageContent` qui inclut la variable `cq:Taggable` mixin.
>* Ressources (`cq:Asset`) dans lesquelles le nœud `jcr:content/metadata` possède toujours le mixin `cq:Taggable`.


### Notation de type de nœud (CND) {#node-type-notation-cnd}

Les définitions de type de nœud existent dans le référentiel sous la forme de fichiers CND. La notation CND est définie dans le cadre de la documentation JCR [ici](https://jackrabbit.apache.org/node-type-notation.html).

Les définitions essentielles relatives aux types de nœud inclus dans AEM sont les suivantes :

```text
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## Contenu balisé : propriété cq:tags {#tagged-content-cq-tags-property}

Le `cq:tags` est un tableau de chaîne utilisé pour stocker une ou plusieurs propriétés. `TagID`s lorsqu’elles sont appliquées au contenu par les auteurs ou les visiteurs du site. La propriété n’a de sens que lorsqu’elle est ajoutée à un nœud qui est défini avec le mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin).

>[!NOTE]
>
>Pour tirer parti de la fonctionnalité de balisage d’AEM, les applications personnalisées ne doivent pas définir de propriétés de balise autres que `cq:tags`.

## Déplacement et fusion de balises {#moving-and-merging-tags}

Vous trouverez, ci-après, la description des effets dans le référentiel lors du déplacement ou de la fusion de balises à l’aide de la [console de balisage](/help/sites-administering/tags.md) :

* Lorsqu’une balise A est déplacée ou fusionnée dans une balise B sous `/content/cq:tags` :

   * La balise A n’est pas supprimée et reçoit une `cq:movedTo` .
   * La balise B est créée (en cas de déplacement) et reçoit un `cq:backlinks` .

* `cq:movedTo` pointe vers la balise B.

   * Cette propriété signifie que la balise A a été déplacée ou fusionnée dans la balise B.
   * Le déplacement de la balise B met à jour cette propriété en conséquence. La balise A est ainsi masquée et n’est conservée dans le référentiel que pour résoudre les ID de balises dans les nœuds de contenu pointant vers la balise A.
   * Tag Garbage Collector supprime les balises telles que la balise A une fois que plus aucun nœud de contenu ne pointe vers elles.
   * Une valeur spéciale pour la propriété `cq:movedTo` est `nirvana` : elle est appliquée lorsque la balise est supprimée. Cependant, elle ne peut pas être supprimée du référentiel, car des sous-balises avec une propriété `cq:movedTo` doivent être conservées.

      >[!NOTE]
      >
      >La propriété `cq:movedTo` n’est ajoutée à la balise déplacée ou fusionnée que si l’une de ces conditions est remplie :
      >
      >1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence).
      >1. La balise comporte des enfants qui ont déjà été déplacés.


* `cq:backlinks` conserve les références dans l’autre direction, c’est-à-dire qu’elle conserve une liste de toutes les balises qui ont été déplacées vers la balise B ou fusionnées avec elle.

   * Cela est surtout nécessaire pour conserver les propriétés `cq:movedTo` à jour lorsque la balise B est également déplacée/fusionnée/supprimée ou que la balise B est activée, auquel cas toutes ses balises de liens retours doivent également être activées.

>[!NOTE]
>
>La propriété `cq:backlinks` n’est ajoutée à la balise déplacée ou fusionnée que si l’une de ces conditions est remplie :
>
>1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence).
>1. La balise comporte des enfants qui ont déjà été déplacés.


* La lecture d’une propriété `cq:tags` d’un nœud de contenu implique la résolution suivante :

   1. S’il n’existe aucune correspondance sous `/content/cq:tags`, aucune balise n’est renvoyée.
   1. Si la propriété `cq:movedTo` est définie pour la balise, l’ID de balise référencé est suivi.

      * Cette étape est répétée aussi longtemps que la balise suivie contient la propriété `cq:movedTo`.
   1. Si la balise suivie n’est pas associée à une propriété `cq:movedTo`, elle est lue.


* Pour publier la modification lorsqu’une balise a été déplacée ou fusionnée, le nœud `cq:Tag` et tous ses liens retours doivent être répliqués.
   * Cette opération est réalisée automatiquement lorsque la balise est activée dans la console d’administration des balises.

* Les mises à jour ultérieures apportées à la propriété `cq:tags` de la page nettoient automatiquement les « anciennes » références.
   * Cette opération est déclenchée, car la résolution d’une balise déplacée via l’API renvoie la balise de destination, fournissant ainsi l’ID de balise de destination.

## Migration des balises {#tags-migration}

À partir de la version 6.4 d’Adobe Experience Manager, les balises sont stockées sous `/content/cq:tags`. Cependant, dans les cas où Adobe Experience Manager a été mis à niveau à partir de la version précédente, les balises sont toujours présentes sous l’ancien emplacement `/etc/tags`. Dans les systèmes mis à niveau, les balises doivent être migrées vers `/content/cq:tags`.

>[!NOTE]
>
>Dans Propriétés de page de la page des balises, il est conseillé d’utiliser l’ID de balise (par exemple `geometrixx-outdoors:activity/biking`) au lieu de coder en dur le chemin d’accès de base de la balise (par exemple, `/etc/tags/geometrixx-outdoors/activity/biking`).
>
>Pour répertorier des balises, vous pouvez utiliser `com.day.cq.tagging.servlets.TagListServlet`.

>[!NOTE]
>
>Il est conseillé d’utiliser l’API du gestionnaire de balises comme ressource.

### Si l’instance AEM mise à niveau prend en charge l’API TagManager**

1. Au début du composant, l’API TagManager détecte s’il s’agit d’une instance AEM mise à niveau. Dans le système mis à niveau, les balises sont stockées sous `/etc/tags`.

1. L’API TagManager s’exécute ensuite en mode de compatibilité descendante, ce qui signifie que l’API utilise `/etc/tags` comme chemin de base. Si ce n’est pas le cas, il utilise le nouvel emplacement `/content/cq:tags`.

1. Mettez à jour l’emplacement des balises.

1. Après la migration des balises vers le nouvel emplacement, exécutez le script suivant.

```java
import org.apache.sling.api.resource.*
import javax.jcr.*

ResourceResolverFactory resourceResolverFactory = osgi.getService(ResourceResolverFactory.class);
ResourceResolver resolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
Session session = resolver.adaptTo(Session.class);

def queryManager = session.workspace.queryManager;
def statement = "/jcr:root/content/cq:tags//element(*, cq:Tag)[jcr:contains(@cq:movedTo,\'/etc/tags\') or jcr:contains(@cq:backlinks,\'/etc/tags\')]";
def query = queryManager.createQuery(statement, "xpath");

println "query = ${query.statement}\n";

def tags = query.execute().getNodes();


tags.each { node ->
        def tagPath = node.path;
        println "tag = ${tagPath}";

        if(node.hasProperty("cq:movedTo") && node.getProperty("cq:movedTo").getValue().toString().startsWith("/etc/tags")){

                def movedTo = node.getProperty("cq:movedTo").getValue().toString();

                println "cq:movedTo = ${movedTo} \n";

                movedTo = movedTo.replace("/etc/tags","/content/cq:tags");
                node.setProperty("cq:movedTo",movedTo);
        } else if(node.hasProperty("cq:backlinks")){

               String[] backLinks = node.getProperty("cq:backlinks").getValues();
               int count = 0;

               backLinks.each { value ->
                       if(value.startsWith("/etc/tags")){
                               println "cq:backlinks = ${value}\n";
                               backLinks[count] = value.replace("/etc/tags","/content/cq:tags");
    }
                       count++;
               }

               node.setProperty("cq:backlinks",backLinks);
  }
}
session.save();

println "---------------------------------Success-------------------------------------"
```

Le script récupère toutes les balises qui ont `/etc/tags` comme valeur de `cq:movedTo/cq:backLinks`. Il effectue ensuite une itération sur l’ensemble des résultats récupérés et résout les valeurs des propriétés `cq:movedTo` et `cq:backlinks` vers les chemins `/content/cq:tags` (dans le cas où `/etc/tags` est détecté dans la valeur).

### Si l’instance AEM mise à niveau s’exécute sur l’interface utilisateur classique**

>[!NOTE]
>
>L’interface utilisateur classique n’est pas compatible avec zéro temps d’arrêt et ne prend pas en charge le nouveau chemin d’accès de base des balises. Si vous souhaitez utiliser l’IU classique, vous devez créer `/etc/tags` puis redémarrer le composant `cq-tagging`.

Si les instances d’AEM mises à niveau sont prises en charge par l’API TagManager et s’exécutent dans l’interface utilisateur classique :

1. Une fois qu’il fait référence à l’ancien chemin d’accès à la base de balises `/etc/tags` sont remplacées par à l’aide de tagId ou d’un nouvel emplacement de balise. `/content/cq:tags`, vous pouvez migrer les balises vers le nouvel emplacement. `/content/cq:tags` dans CRX DE suivi du redémarrage du composant.

1. Après la migration des balises vers le nouvel emplacement, exécutez le script mentionné ci-dessus.
