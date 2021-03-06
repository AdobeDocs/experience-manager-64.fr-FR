---
title: Personnalisation de la console Sites web (IU classique)
seo-title: Customizing the Websites Console (Classic UI)
description: La console Administration de sites web peut être étendue pour afficher des colonnes personnalisées.
seo-description: The Websites Administration console can be extended to display custom columns
uuid: 7587d026-f974-46fe-bac3-3872d3a083ab
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 73e57f20-4022-46ab-aa5c-ec866298b645
exl-id: c7e37599-0712-44cf-8191-d444d12f95c4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 72%

---

# Personnalisation de la console Sites web (IU classique){#customizing-the-websites-console-classic-ui}

## Ajout d’une colonne personnalisée à la console Sites web (siteadmin) {#adding-a-custom-column-to-the-websites-siteadmin-console}

La console Administration de sites web peut être étendue pour afficher des colonnes personnalisées. La console est générée sur la base d’un objet JSON qui peut être étendu en créant un service OSGI qui implémente l’interface . `ListInfoProvider` Un tel service modifie l’objet JSON envoyé au client pour créer la console.

Ce tutoriel détaillé explique comment afficher une nouvelle colonne dans la console Administration de sites web en implémentant l’interface `ListInfoProvider`. Cette méthode comprend les étapes suivantes :

1. [Création du service OSGI](#creating-the-osgi-service) et déploiement du lot où il réside sur le serveur AEM.
1. (Facultatif)[Test du nouveau service](#testing-the-new-service) en effectuant un appel JSON pour demander l’objet JSON qui est utilisé pour créer la console.
1. [Affichage de la nouvelle colonne](#displaying-the-new-column) en étendant la structure des nœuds de la console dans le référentiel.

>[!NOTE]
>
>Ce tutoriel peut également être utilisé pour étendre les consoles d’administration suivantes :
>
>* Console Digital Assets
>* Console Community

>


### Création du service OSGI {#creating-the-osgi-service}

L’interface `ListInfoProvider` définit deux méthodes :

* `updateListGlobalInfo`, pour mettre à jour les propriétés globales de la liste,
* `updateListItemInfo`, pour mettre à jour un seul élément de liste.

Les arguments pour les deux méthodes sont les suivants :

* `request`, l’objet de requête HTTP Sling associé,
* `info`, l’objet JSON à mettre à jour, à savoir la liste globale ou l’élément de liste en cours,
* `resource`, une ressource Sling.

L’exemple d’implémentation ci-dessous :

* ajoute une propriété *starred* pour chaque élément, à savoir `true` si le nom de page commence par un *e* et `false` dans les autres cas ;

* ajoute une propriété *starredCount* qui est « global » pour la liste et qui contient le nombre d’éléments de liste signalés par un astérisque.

Pour créer le service OSGI, procédez comme suit :

1. Dans CRXDE Lite, [créez un lot](/help/sites-developing/developing-with-crxde-lite.md#managing-a-bundle).
1. Ajoutez l’exemple de code ci-dessous.
1. Créez le lot.

Le nouveau service est opérationnel.

```java
package com.test;

import com.day.cq.commons.ListInfoProvider;
import com.day.cq.i18n.I18n;
import com.day.cq.wcm.api.Page;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;

@Component(metatype = false)
@Service(value = ListInfoProvider.class)
public class StarredListInfoProvider implements ListInfoProvider {

    private int count = 0;

    public void updateListGlobalInfo(SlingHttpServletRequest request, JSONObject info, Resource resource) throws JSONException {
        info.put("starredCount", count);
        count = 0; // reset for next execution
    }

    public void updateListItemInfo(SlingHttpServletRequest request, JSONObject info, Resource resource) throws JSONException {
        Page page = resource.adaptTo(Page.class);
        if (page != null) {
            // Consider starred if page name starts with 'e'
            boolean starred = page.getName().startsWith("e");
            if (starred) {
                count++;
            }
            I18n i18n = new I18n(request);
            info.put("starred", starred ? i18n.get("Yes") : i18n.get("No"));
        }
    }

}
```

>[!CAUTION]
>
>* Votre implémentation doit déterminer, sur la base de la requête et/ou de la ressource fournies, si elle doit ou non ajouter les informations à l’objet JSON.
>* Si votre implémentation de `ListInfoProvider` définit une propriété qui existe déjà dans l’objet de réponse, sa valeur est remplacée par celle que vous fournissez.\
   >   Vous pouvez utiliser le [classement de service](https://www.osgi.org/javadoc/r2/org/osgi/framework/Constants.html#SERVICE_RANKING) pour gérer l’ordre d’exécution de plusieurs implémentations de `ListInfoProvider`.

>


### Test du nouveau service {#testing-the-new-service}

Lorsque vous ouvrez la console Administration de sites web et parcourez votre site, le navigateur génère un appel ajax pour obtenir l’objet JSON qui est utilisé pour créer la console. Par exemple, lorsque vous accédez au `/content/geometrixx` , la requête suivante est envoyée au serveur AEM pour créer la console :

[http://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](http://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

Pour vous assurer que le nouveau service s’exécute après le déploiement du lot où il réside, procédez comme suit :

1. Pointez votre navigateur vers l’URL suivante :

   [http://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](http://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

1. La réponse doit afficher les nouvelles propriétés comme suit :

![screen_shot_2012-02-13at163046](assets/screen_shot_2012-02-13at163046.png)

### Affichage de la nouvelle colonne {#displaying-the-new-column}

La dernière étape consiste à adapter la structure des noeuds de la console d’administration des sites web afin d’afficher la nouvelle propriété pour toutes les pages de Geometrixx en recouvrant `/libs/wcm/core/content/siteadmin`. Procédez comme suit :

1. Dans CRXDE Lite, créez la structure des noeuds. `/apps/wcm/core/content` avec des noeuds de type `sling:Folder` pour refléter la structure `/libs/wcm/core/content`.

1. Copiez le noeud `/libs/wcm/core/content/siteadmin` et collez-le ci-dessous `/apps/wcm/core/content`.

1. Copiez le noeud `/apps/wcm/core/content/siteadmin/grid/assets` to `/apps/wcm/core/content/siteadmin/grid/geometrixx` et modifie ses propriétés :

   * Supprimez **pageText**
   * Définir **pathRegex** to `/content/geometrixx(/.*)?`

      De cette manière, la configuration de grille sera active pour tous les sites web geometrixx.

   * Définir **storeProxySuffix** to `.pages.json`
   * Modifiez la propriété à plusieurs valeurs **storeReaderFields** et ajoutez la valeur `starred`.
   * Pour activer la fonctionnalité MSM, ajoutez les paramètres MSM suivants à la propriété multi-String . **storeReaderFields**:

      * **msm:isSource**
      * **msm:isInBlueprint**
      * **msm:isLiveCopy**

1. Ajouter un `starred` noeud (de type **nt:unstructured**) ci-dessous `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns` avec les propriétés suivantes :

   * **dataIndex**: `starred` de type Chaîne
   * **header**: `Starred` de type Chaîne
   * **xtype**: `gridcolumn` de type Chaîne

1. (Facultatif) Déposez les colonnes que vous ne souhaitez pas afficher à l’adresse `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns`

1. `/siteadmin` est un chemin de redirection vers un microsite qui, par défaut, pointe vers `/libs/wcm/core/content/siteadmin`.

   Pour le rediriger vers votre version de siteadmin sur `/apps/wcm/core/content/siteadmin` définir la propriété ; `sling:vanityOrder` avoir une valeur supérieure à celle définie sur `/libs/wcm/core/content/siteadmin`. La valeur par défaut est de 300 ; toute valeur plus élevée est donc acceptable.

1. Accédez à la console Administration de sites web et accédez au site Geometrixx :

   [http://localhost:4502/siteadmin#/content/geometrixx](http://localhost:4502/siteadmin#/content/geometrixx).

1. La nouvelle colonne nommée **Starred** affiche des informations personnalisées comme suit :

![screen_shot_2012-02-14at104602](assets/screen_shot_2012-02-14at104602.png)

>[!CAUTION]
>
>Si plusieurs configurations de grille correspondent au chemin d’accès demandé défini par la propriété **pathRegex**, c’est la première qui est utilisée, et non la plus spécifique. Cela signifie que l’ordre des configurations est important.

### Exemple de module {#sample-package}

Le résultat de ce tutoriel est disponible dans la section [Personnalisation de la console d’administration des sites web](http://localhost:4502/crx/packageshare/index.html/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/helper/customizing-siteadmin) module sur Package Share.
