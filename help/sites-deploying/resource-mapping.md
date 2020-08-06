---
title: Mappage de ressource
seo-title: Mappage de ressource
description: Découvrez comment définir des redirections, des URL Vanity et les hôtes virtuels pour AEM à l’aide du mappage de ressource.
seo-description: Découvrez comment définir des redirections, des URL Vanity et les hôtes virtuels pour AEM à l’aide du mappage de ressource.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
translation-type: tm+mt
source-git-commit: c4ac10736c937198aa0c81ecf547dd489ef93366
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 61%

---


# Mappage de ressource{#resource-mapping}

Le mappage de ressource permet de définir des redirections, des URL Vanity et des hôtes virtuels pour AEM.

Par exemple, vous pouvez utiliser ces mappages pour :

* Prefix all requests with `/content` so that the internal structure is hidden from the visitors to your website.
* Define a redirect so that all requests to the `/content/en/gateway` page of your website are redirected to `https://gbiv.com/`.

Un mappage HTTP possible [ consiste à préfixer toutes les demandes à localhost:4503 avec le répertoire /content](#configuring-an-internal-redirect-to-content). Un mappage de ce type peut être utilisé pour masquer la structure interne vis-à-vis des visiteurs du site web, car il rend :

`localhost:4503/content/geometrixx/en/products.html`

accessible à l’aide de :

`localhost:4503/geometrixx/en/products.html`

as the mapping will automatically add the prefix `/content` to `/geometrixx/en/products.html`.

>[!CAUTION]
>
>Les URL Vanity ne prennent pas en charge les modèles regex.

>[!NOTE]
>
>Voir la documentation Sling et les sections [Mappages pour la résolution de ressource](https://sling.apache.org/site/resources.html) et [Ressources](https://sling.apache.org/site/mappings-for-resource-resolution.html) pour plus d’informations.

## Affichage des définitions du mappage {#viewing-mapping-definitions}

Les mappages forment deux listes que le résolveur de ressources JCR analyse (du haut vers le bas) pour trouver une correspondance.

These lists can be viewed (together with configuration information) under the **JCR ResourceResolver** option of the Felix console; for example, `https://<host>:<port>/system/console/jcrresolver`:

* Configuration

   Shows the current configuration (as defined for the [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md).

* Test de configuration

   Cela vous permet de saisir une URL ou un chemin de ressource. Cliquez sur **Résoudre** ou **Mapper** pour confirmer la façon dont le système transforme l’entrée.

* **Resolver Map Entries (Entrées de mappage du résolveur)** La liste des entrées utilisées par les méthodes ResourceResolver.resolve pour mapper les URL aux ressources. 

* **Mapping Map Entries (Entrées de mappage)** La liste des entrées utilisées par les méthodes ResourceResolver.map pour mapper les chemins d’accès des ressources aux URL.

Les deux listes affichent différentes entrées, y compris celles définies par défaut par les applications. Cela vise souvent à simplifier les URL pour l’utilisateur. 

Les listes associe **un modèle**, une expression régulière correspondant à la demande, avec **un remplacement** qui définit la redirection à appliquer.

Par exemple :

**Modèle** `^[^/]+/[^/]+/welcome$`

déclenche :

**Remplacement** `/libs/cq/core/content/welcome.html`.

pour rediriger une requête :

`http://localhost:4503/welcome`

vers :

`http://localhost:4503/libs/cq/core/content/welcome.html`

De nouvelles définitions de mappage sont créées dans le référentiel.

>[!NOTE]
>
>There are many resources available that help explain how to define regular expressions; for example [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Création des définitions de mappage dans AEM {#creating-mapping-definitions-in-aem}

Dans une installation d’AEM standard, vous pouvez trouver le dossier :

`/etc/map/http`

Il s’agit de la structure utilisée lors de la définition des mappages pour le protocole HTTP. Other folders ( `sling:Folder`) can be created under `/etc/map` for any other protocols that you want to map.

### Configuration d’une redirection interne vers /content {#configuring-an-internal-redirect-to-content}

To create the mapping that prefixes any request to http://localhost:4503/ with `/content`:

1. Using CRXDE navigate to `/etc/map/http`.

1. Créez un nœud :

   * **Type** `sling:Mapping`

      Ce type de noeud est destiné à de tels mappages, bien que son utilisation ne soit pas obligatoire.

   * **Nom** `localhost_any`

1. Cliquez sur **Tout enregistrer**.
1. **Ajoutez** les propriétés suivantes à ce nœud :

   * **Nom** `sling:match`

      * **Type** `String`
      * **Valeur** `localhost.4503/`
   * **Nom** `sling:internalRedirect`

      * **Type** `String`
      * **Valeur** `/content/`


1. Cliquez sur **Enregistrer tout**.

Cela permettra de traiter une demande telle que :\
`localhost:4503/geometrixx/en/products.html`\
comme si :\
`localhost:4503/content/geometrixx/en/products.html`\
avait été demandé.

>[!NOTE]
>
>Voir [Ressources](https://sling.apache.org/site/mappings-for-resource-resolution.html) dans la documentation Sling pour plus d’informations sur les propriétés sling disponibles et leur configuration.

>[!NOTE]
>
>You can use `/etc/map.publish` to hold the configurations for the publish environment. These must then be replicated, and the new location ( `/etc/map.publish`) configured for the **Mapping Location** of the [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) of the publish environment.

