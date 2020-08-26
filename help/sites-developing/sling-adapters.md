---
title: 'Utilisation des adaptateurs Sling '
seo-title: 'Utilisation des adaptateurs Sling '
description: Sling propose un modèle Adaptateur permettant de convertir facilement les objets qui mettent en œuvre l’interface Adaptable
seo-description: Sling propose un modèle Adaptateur permettant de convertir facilement les objets qui mettent en œuvre l’interface Adaptable
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
translation-type: tm+mt
source-git-commit: 269facfb6351b0b7c73e963ac7c5dc0b57c78a3e
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 87%

---


# Utilisation des adaptateurs Sling {#using-sling-adapters}

[Sling](https://sling.apache.org) propose un [modèle Adaptateur](https://sling.apache.org/site/adapters.html) permettant de convertir facilement les objets qui mettent en œuvre l’interface [Adaptable](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29). Cette interface fournit une méthode [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) générique qui convertit les objets dans le type de classe qui est transmis comme argument.

Par exemple, pour convertir un objet Resource en objet Node correspondant, vous pouvez simplement procéder comme suit :

```java
Node node = resource.adaptTo(Node.class);
```

## Cas d’utilisation {#use-cases}

Il existe plusieurs scénarios d’utilisation :

* Obtenir des objets spécifiques à l’implémentation.

    Par exemple, une implémentation basée sur JCR de l’interface [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) permet d’accéder à l’objet [`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) JCR sous-jacent.

* Création de raccourcis d’objets qui nécessitent la transmission d’objets de contexte internes.

   Par exemple, le [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) basé sur JCR contient une référence à la [`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html) de la requête qui, à son tour, est nécessaire pour de nombreux objets qui s’exécuteront sur la base de cette session de requête ; [`PageManager`](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) ou [`UserManager`](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html), par exemple.

* Raccourci vers les services.

   Cas peu fréquent : `sling.getService()` s’avère également simple.

### Valeur renvoyée nulle {#null-return-value}

`adaptTo()` peut renvoyer une valeur nulle.

Plusieurs raisons peuvent expliquer cela :

* Cette implémentation ne prend pas en charge le type cible.
* Une « adapter factory » qui gère ce cas n’est pas active (en raison de références de service manquantes, par exemple.)
* La condition interne a échoué.
* Le service n’est pas disponible.

Il est important de traiter ce cas de manière appropriée. Pour les rendus JSP, l’échec de JSP est acceptable si cela se traduit par un élément de contenu vide.

### Mise en cache {#caching}

Pour améliorer les performances, les implémentations peuvent mettre en cache l’objet renvoyé par un appel `obj.adaptTo()`. Si `obj` est identique, l’objet renvoyé l’est également.

Cette mise en cache est exécutée pour tous les scénarios basés sur `AdapterFactory`.

Cependant, il n’existe pas de règle absolue : l’objet peut soit être une nouvelle instance, soit une instance existante. Cela signifie que vous ne pouvez pas compter sur un comportement en particulier. Par conséquent, il est important, notamment dans `AdapterFactory`, que les objets soient réutilisables dans ce scénario.

### Fonctionnement {#how-it-works}

`Adaptable.adaptTo()` peut être implémenté de différentes façons :

* Par l’objet proprement dit ; implémentation de la méthode et mappage sur certains objets.
* By an [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)`, which can map arbitrary objects.

   Les objets doivent cependant implémenter l’interface `Adaptable` et étendre [`SlingAdaptable`](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (qui transmet l’appel `adaptTo` à un gestionnaire d’adaptateur central).

   Cela autorise les hooks dans le mécanisme `adaptTo` pour les classes existantes, comme `Resource`.

* Une combinaison des deux.

Pour le premier cas, vous pouvez consulter les JavaDocs pour connaître les `adaptTo-targets` possibles. Cependant, pour des sous-classes spécifiques, telles que la ressource basée sur JCR, cela s’avère souvent impossible. Dans ce cas, les implémentations de `AdapterFactory` font généralement partie des classes privées d’un lot et ne sont donc pas exposées dans une API cliente ni répertoriées dans les JavaDocs. En théorie, il serait possible d’accéder à toutes les implémentations `AdapterFactory` à partir de l’exécutable de service [OSGi](/help/sites-deploying/configuring-osgi.md) et d’observer leurs configurations « adaptables » (sources et cibles), mais pas de les mapper entre elles. En définitive, cela dépend de la logique interne, qui doit être documentée, d’où cette référence.

## Référence  {#reference}

### Sling {#sling}

[**Resource**](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) s’adapte à :

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td> 
   <td>S’il s’agit d’une ressource basée sur un nœud JCR ou une propriété JCR faisant référence à un nœud.</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Property</a></td> 
   <td>S’il s’agit d’une ressource basée sur une propriété JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Item</a></td> 
   <td>S’il s’agit d’une ressource basée sur JCR (nœud ou propriété).</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">Map</a></td> 
   <td>Renvoie un mappage des propriétés, s’il s’agit d’une ressource basée sur un nœud JCR (ou une autre ressource prenant en charge les mappages de valeurs).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>Renvoie un mappage simple d’emploi des propriétés, s’il s’agit d’une ressource basée sur un nœud JCR (ou une autre ressource prenant en charge les mappages de valeurs). On peut également obtenir ce résultat (plus simplement) en utilisant<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (gestion du cas de valeur nulle, etc.).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td> 
   <td>Extension de <a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, ce qui permet la prise en compte de la hiérarchie de ressources lors de la recherche de propriétés.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersistableValueMap</a></td> 
   <td>S’il s’agit d’une ressource basée sur un nœud JCR et que l’utilisateur est autorisé à modifier des propriétés sur ce nœud.<br /> Remarque : Plusieurs mappages persistants ne partagent pas leurs valeurs.</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td> 
   <td>Renvoie le contenu binaire d’un "fichier"<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[**ResourceResolver**](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) s’adapte à :

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Session</a></td> 
   <td>Session JCR de la requête, s’il s’agit d’un résolveur de ressources basé sur JCR (par défaut).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td> 
   <td>Basé sur la session JCR, s’il s’agit d’un résolveur de ressources basé sur JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td> 
   <td>Basé sur la session JCR, s’il s’agit d’un résolveur de ressources basé sur JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td> 
   <td>Selon la session JCR, s’il s’agit d’un résolveur de ressources basé sur JCR et si l’utilisateur est autorisé à accéder à UserManager.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a> </td> 
   <td>Utilisateur actuel.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a><br /> </td> 
   <td>Utilisateur actuel.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/privileges/PrivilegeManager.html">PrivilegeManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/Preferences.html">Preferences</a></td> 
   <td>Préférences de l’utilisateur actuel (en fonction de la session JCR s’il s’agit d’un résolveur de ressources basé sur JCR).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/PreferencesService.html">PreferencesService</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/auth/pin/PinManager.html">PinManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">Externalizer</a></td> 
   <td>Pour externaliser des URL absolues, même sans l’objet de requête.<br /> </td> 
  </tr> 
 </tbody> 
</table>

[**SlingHttpServletRequest**](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) s’adapte à :

Pas encore de cible, mais implémente l’interface Adaptable et peut être utilisé comme source dans une AdapterFactory personnalisée.

[**SlingHttpServletResponse**](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) s’adapte à :

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td> 
   <td>S’il s’agit d’une réponse de réécriture sling.</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[**Page**](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) s’adapte à :

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td> 
   <td>Ressource de la page</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td> 
   <td>Ressource étiquetée (== this).</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td> 
   <td>Nœud de la page.</td> 
  </tr> 
  <tr> 
   <td>…</td> 
   <td>Tous les éléments auxquels la ressource de la page peut être adaptée.</td> 
  </tr> 
 </tbody> 
</table>

[**Component**](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) s’adapte à :

| [Resource](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource du composant. |
|---|---|
| [LabeledResource](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Ressource étiquetée (== this). |
| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud du composant. |
| … | Tous les éléments auxquels la ressource du composant peut être adaptée. |

[**Template**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) s’adapte à :

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>Ressource du modèle.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td> 
   <td>Ressource étiquetée (== this).</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td> 
   <td>Nœud de ce modèle.</td> 
  </tr> 
  <tr> 
   <td>…</td> 
   <td>Tous les éléments auxquels la ressource du modèle peut être adaptée.</td> 
  </tr> 
 </tbody> 
</table>

#### Sécurité {#security}

[**Autorisé**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html), [**utilisateur**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) et [**groupe**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) s&#39;adapter à :

| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Renvoie le nœud racine utilisateur/groupe. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Renvoie l’état de réplication pour le nœud racine utilisateur/groupe. |

#### Gestion des actifs numériques {#dam}

[**Asset**](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) s’adapte à :

| [Resource](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource de l’actif. |
|---|---|
| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud de la ressource. |
| … | Tous les éléments auxquels la ressource de l’actif peut être adaptée. |

#### Balisage {#tagging}

[**Tag**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) s’adapte à :

| [Resource](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource de la balise. |
|---|---|
| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud de la balise. |
| … | Tous les éléments auxquels la ressource de la balise peut être adaptée. |

#### Autres {#other}

Sling/JCR/OCM fournit, en outre, un ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` pour les objets OCM ([Object Content Mapping](https://jackrabbit.apache.org/object-content-mapping.html)) personnalisés.
