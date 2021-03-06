---
title: Mappage de ressource
seo-title: Resource Mapping
description: Découvrez comment définir des redirections, des URL Vanity et les hôtes virtuels pour AEM à l’aide du mappage de ressource.
seo-description: Learn how to define redirects, vanity URLs and virtual hosts for AEM by using resource mapping.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
feature: Configuring
exl-id: 81dddbab-1a9e-49ee-b2a5-a8e4de3630d1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 59%

---

# Mappage de ressource{#resource-mapping}

Le mappage de ressource permet de définir des redirections, des URL Vanity et des hôtes virtuels pour AEM.

Par exemple, vous pouvez utiliser ces mappages pour :

* Préfixe toutes les requêtes avec `/content` afin que la structure interne soit masquée aux visiteurs de votre site web.
* Définissez une redirection afin que toutes les requêtes envoyées à la variable `/content/en/gateway` La page de votre site web est redirigée vers `https://gbiv.com/`.

Un mappage HTTP possible [ consiste à préfixer toutes les demandes à localhost:4503 avec le répertoire /content](#configuring-an-internal-redirect-to-content). Un mappage de ce type peut être utilisé pour masquer la structure interne vis-à-vis des visiteurs du site web, car il rend :

`localhost:4503/content/geometrixx/en/products.html`

accessible à l’aide de :

`localhost:4503/geometrixx/en/products.html`

car le mappage ajoutera automatiquement le préfixe `/content` to `/geometrixx/en/products.html`.

>[!CAUTION]
>
>Les URL Vanity ne prennent pas en charge les modèles regex.

>[!NOTE]
>
>Voir la documentation Sling et les sections [Mappages pour la résolution de ressource](https://sling.apache.org/site/resources.html) et [Ressources](https://sling.apache.org/site/mappings-for-resource-resolution.html) pour plus d’informations.

## Affichage des définitions du mappage {#viewing-mapping-definitions}

Les mappages forment deux listes que le résolveur de ressources JCR analyse (du haut vers le bas) pour trouver une correspondance.

Ces listes peuvent être affichées (ainsi que des informations de configuration) sous la **JCR ResourceResolver** l’option de la console Felix ; par exemple, `https://<host>:<port>/system/console/jcrresolver`:

* Configuration

   Affiche la configuration actuelle (telle que définie pour la variable [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md).

* Test de configuration

   Vous pouvez ainsi saisir une URL ou un chemin d’accès à la ressource. Cliquez sur **Résoudre** ou **Mapper** pour confirmer la façon dont le système transforme l’entrée.

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

vers:

`http://localhost:4503/libs/cq/core/content/welcome.html`

De nouvelles définitions de mappage sont créées dans le référentiel.

>[!NOTE]
>
>De nombreuses ressources sont disponibles pour expliquer comment définir des expressions régulières. par exemple [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Création des définitions de mappage dans AEM {#creating-mapping-definitions-in-aem}

Dans une installation d’AEM standard, vous pouvez trouver le dossier :

`/etc/map/http`

Il s’agit de la structure utilisée lors de la définition des mappages pour le protocole HTTP. Autres dossiers ( `sling:Folder`) peut être créé sous `/etc/map` pour tous les autres protocoles que vous souhaitez mapper.

### Configuration d’une redirection interne vers /content {#configuring-an-internal-redirect-to-content}

Pour créer le mappage qui préfixe toute requête à http://localhost:4503/ avec `/content`:

1. À l’aide de CRXDE, accédez à `/etc/map/http`.

1. Créez un nœud :

   * **Type** `sling:Mapping`

      Ce type de noeud est destiné à de tels mappages, bien que son utilisation ne soit pas obligatoire.

   * **Nom** `localhost_any`

1. Cliquez sur **Enregistrer tout**.
1. **Ajoutez** les propriétés suivantes à ce nœud :

   * **Nom** `sling:match`

      * **Type** `String`
      * **Valeur** `localhost.4503/`
   * **Nom** `sling:internalRedirect`

      * **Type** `String`
      * **Valeur** `/content/`


1. Cliquez sur **Enregistrer tout**.

Cela permet de gérer une requête telle que :\
`localhost:4503/geometrixx/en/products.html`\
comme si :\
`localhost:4503/content/geometrixx/en/products.html`\
avait été demandé.

>[!NOTE]
>
>Voir [Ressources](https://sling.apache.org/site/mappings-for-resource-resolution.html) dans la documentation Sling pour plus d’informations sur les propriétés sling disponibles et leur configuration.

>[!NOTE]
>
>Vous pouvez utiliser `/etc/map.publish` pour contenir les configurations de l’environnement de publication. Ils doivent ensuite être répliqués et le nouvel emplacement ( `/etc/map.publish`) configuré pour la variable **Emplacement du mappage** de [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) de l’environnement de publication.
