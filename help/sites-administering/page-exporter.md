---
title: Exportateur de page
seo-title: Exportateur de page
description: Découvrez comment utiliser l’exportateur de page d’AEM.
seo-description: Découvrez comment utiliser l’exportateur de page d’AEM.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
translation-type: tm+mt
source-git-commit: aac5026a249e1cb09fec66313cc03b58597663f0
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 63%

---


# Exportateur de page{#the-page-exporter}

Dans AEM, vous pouvez exporter une page sous la forme d’une page web complète, comprenant des images, des fichiers .js et des fichiers .css.

Une fois l’exportation configurée, il vous suffit de demander une page dans le navigateur en remplaçant `html` par `export.zip` dans l’URL ; vous obtenez alors un fichier compressé à télécharger contenant la page rendue au format HTML avec les ressources référencées. Tous les chemins d’accès dans la page, par exemple les chemins d’accès aux images, sont réécrits de manière à pointer vers les fichiers inclus dans le fichier compressé ou vers les ressources disponibles sur le serveur.

## Exportation d’une page {#exporting-a-page}

La procédure ci-dessous décrit comment exporter une page et considère qu’il existe un modèle de configuration de l’exportation pour votre site. Un modèle de configuration définit la méthode d’exportation d’une page. Il est spécifique à votre site. Pour créer un modèle de configuration, reportez-vous à la section [Création d’une configuration d’exportateur de pages pour votre site](#creating-a-page-exporter-configuration-for-your-site).

Pour exporter une page, procédez comme suit :

1. Ouvrez la page dans un navigateur. Par exemple :
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Ouvrez la boîte de dialogue Propriétés de la page, sélectionnez l’onglet **Avancé**, puis développez l’ensemble de champs **Exporter**.

1. Cliquez sur l’icône de loupe et sélectionnez un modèle de configuration. Sélectionnez le modèle **geometrixx**, car il s’agit du modèle par défaut pour le site Geometrixx. Cliquez sur **OK**.

1. Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés de la page.
1. Demandez la page en remplaçant `html` par `export.zip` dans l’URL.

1. Téléchargez le fichier `<page-name>.export.zip` sur votre système de fichiers.

1. Dans votre système de fichiers, décompressez le fichier :

   * le fichier html de la page ( `<page-name>.html`) est disponible sous `<unzip-dir>/<page-path>`
   * Les autres ressources (fichiers .js, fichiers .css, images, etc.) se trouvent à un emplacement dépendant des paramètres du modèle d’exportation. Dans cet exemple, certaines ressources sont inférieures à `<unzip-dir>/etc`, certaines inférieures à `<unzip-dir>/<page-path>`.

1. Ouvrez le fichier HTML de la page ( `<unzip-dir>/<page-path>.html`) dans votre navigateur pour vérifier le rendu.

## Création d’une configuration de l’exportateur de page pour votre site {#creating-a-page-exporter-configuration-for-your-site}

L’exportateur de page repose sur la structure de synchronisation du contenu. Les configurations disponibles dans la boîte de dialogue des propriétés de page sont des modèles de configuration. Elles définissent toutes les dépendances nécessaires pour une page. Lorsqu’une exportation de page est déclenchée, le modèle de configuration est utilisé et le chemin de page et le chemin de conception sont appliqués dynamiquement à la configuration. Le fichier compressé est alors créé à l’aide de la fonctionnalité de synchronisation de contenu standard.

AEM comporte quelques modèles, notamment :

* Un paramètre par défaut à `/etc/contentsync/templates/default`. Ce modèle :

   * est le modèle de secours lorsque aucun modèle de configuration ne se trouve dans le référentiel ;
   * Peut servir de base à un nouveau modèle de configuration.

* Un site dédié au site **Geometrixx**, à `/etc/contentsync/templates/geometrixx`. Ce modèle peut être utilisé comme exemple pour en créer un autre.

Pour créer un modèle de configuration de l’exportateur de page, procédez comme suit :

1. Dans **CRXDE Lite**, créez un noeud sous `/etc/contentsync/templates` :

   * Nom : par ex. `mysite`. Le nom s’affiche dans la boîte de dialogue des propriétés de la page lors du choix du modèle d’exportateur de page.
   * Type : `nt:unstructured`

1. Sous le noeud de modèle, appelé ici `mysite`, créez une structure de noeud à l’aide des noeuds de configuration décrits ci-dessous.

### Nœuds de configuration de l’exportateur de page {#page-exporter-configuration-nodes}

Le modèle de configuration est constitué d’une structure de nœud. Chaque nœud possède une propriété `type` qui définit une action spécifique dans le processus de création du fichier compressé. Pour plus d’informations sur la propriété de type, voir la section Présentation des types de configuration dans la page de structure Content Sync.

Les nœuds ci-dessous peuvent être utilisés pour créer un modèle de configuration d’exportation :

**page** nodeLe noeud de page est utilisé pour copier le code html de la page dans le fichier zip. Il possède les caractéristiques suivantes :

* C’est un nœud obligatoire.
* Se trouve sous `/etc/contentsync/templates/<sitename>`.
* Son nom est `page`.
* Son type de noeud est `nt:unstructured`

Le nœud `page` possède les propriétés suivantes :

* Propriété `type` définie avec la valeur `pages`.

* Il ne comporte pas de propriété `path`, car le chemin d’accès actuel à la page est copié dynamiquement dans la configuration.

* Les autres propriétés sont décrites dans la section Présentation des types de configuration de la structure Content Sync.

**rewrite** nodeLe noeud rewrite définit comment les liens sont réécrits dans la page exportée. Les liens réécrits peuvent pointer vers les fichiers inclus dans le fichier compressé ou vers les ressources sur le serveur.

Consultez la page Synchronisation du contenu pour obtenir une description exhaustive du nœud `rewrite`.

**design** nodeLe noeud de conception est utilisé pour copier la conception utilisée pour la page exportée. Il possède les caractéristiques suivantes :

* Il est facultatif.
* Se trouve sous `/etc/contentsync/templates/<sitename>`.
* Son nom est `design`.
* Son type de noeud est `nt:unstructured`.

Le nœud `design` possède les propriétés suivantes :

* Propriété `type` définie sur la valeur `copy`.

* Il ne comporte pas de propriété `path`, car le chemin d’accès actuel à la page est copié dynamiquement dans la configuration.

**** nodeUn noeud générique est utilisé pour copier des ressources telles que les fichiers clientlibs.js ou .css dans le fichier zip. Il possède les caractéristiques suivantes :

* Il est facultatif.
* Se trouve sous `/etc/contentsync/templates/<sitename>`.
* Il ne possède pas de domaine spécifique.
* Son type de noeud est `nt:unstructured`.
* Possède une propriété `type` et toute propriété `type` associée telle que définie dans la section Présentation des types de configuration de la structure Content Sync.

Par exemple, le nœud de configuration ci-dessous copie les fichiers .js des bibliothèques clientes geometrixx dans le fichier compressé :

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

Le modèle de configuration de l’exportation de page **Geometrixx** explique comment vous pouvez configurer une exportation de page. Pour afficher la structure du nœud du modèle dans le navigateur au format JSON, demandez l’adresse URL suivante :

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Mise en œuvre d’une configuration personnalisée**

Comme vous l’avez peut-être constaté dans la structure du nœud, le modèle de configuration de l’exportation de page **Geometrixx** comporte un nœud `logo` avec une propriété `type` définie sur `image`. Il s’agit d’un type de configuration spécial, créé pour copier le logo de l’image dans le fichier compressé. Pour respecter certaines exigences spécifiques, il vous faudra peut-être mettre en œuvre une propriété `type` personnalisée : à cet effet, consultez la section Mise en œuvre d’un gestionnaire de mise à jour personnalisé dans la page Synchronisation du contenu.

## Exportation d’une page par programmation {#programmatically-exporting-a-page}

Pour exporter une page par programmation, vous pouvez utiliser le service OSGi [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html). Ce service permet ce qui suit :

* exporter une page et écrire la réponse du servlet HTTP ;
* exporter une page et enregistrer le fichier compressé à un emplacement spécifique.

Le servlet lié au sélecteur `export` et à l’extension `zip` utilise le service PageExporter.

## Résolution des incidents {#troubleshooting}

Si vous rencontrez un problème de téléchargement du fichier zip, vous pouvez supprimer le noeud `/var/contentsync` dans le référentiel et envoyer à nouveau la demande d’exportation.

