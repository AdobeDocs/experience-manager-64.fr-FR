---
title: Exportateur de page
seo-title: The Page Exporter
description: Découvrez comment utiliser l’outil AEM d’exportation de pages.
seo-description: Learn how to use the AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 30%

---

# Exportateur de page{#the-page-exporter}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM vous permet d’exporter une page sous forme d’une page web complète comprenant des images, des fichiers .js et .css.

Une fois l’exportation configurée, il vous suffit de demander une page dans votre navigateur en remplaçant `html` avec `export.zip` dans l’URL et vous obtenez un téléchargement de fichier zip contenant la page rendue au format html et les ressources référencées. Tous les chemins d’accès de la page, par exemple les chemins d’accès aux images, sont réécrits afin de pointer vers les fichiers inclus dans le fichier zip ou vers les ressources du serveur.

## Exportation d’une page {#exporting-a-page}

Les étapes suivantes décrivent comment exporter une page et supposent qu’il existe un modèle de configuration d’exportation pour votre site. Un modèle de configuration définit la manière dont une page est exportée et est spécifique à votre site. Pour créer un modèle de configuration, reportez-vous à la section [Création d’une configuration d’exportateur de page pour votre site](#creating-a-page-exporter-configuration-for-your-site) .

Pour exporter une page, procédez comme suit :

1. Dans votre navigateur, ouvrez la page Par exemple :
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Ouvrez la boîte de dialogue Propriétés de la page, puis sélectionnez l’option **Avancé** et développez l’onglet **Exporter** jeu de champs.

1. Cliquez sur l&#39;icône de la loupe et sélectionnez un modèle de paramétrage. Sélectionnez la **geometrixx** , car il s’agit de la valeur par défaut du site de Geometrixx. Cliquez sur **OK**.

1. Cliquez sur **OK** pour fermer la boîte de dialogue des propriétés de la page.
1. Demandez la page en remplaçant `html` avec `export.zip` dans l’URL.

1. Téléchargez la `<page-name>.export.zip` vers votre système de fichiers.

1. Dans votre système de fichiers, décompressez le fichier :

   * le fichier html de la page ( `<page-name>.html`) est disponible ci-dessous `<unzip-dir>/<page-path>`
   * d’autres ressources ( fichiers .js, fichiers .css, images, etc.) sont localisées en fonction des paramètres du modèle d’exportation. Dans cet exemple, certaines ressources sont ci-dessous : `<unzip-dir>/etc`, voir ci-dessous `<unzip-dir>/<page-path>`.

1. Ouvrez le fichier HTML de la page (`<unzip-dir>/<page-path>.html`) dans votre navigateur pour contrôler le rendu.

## Création d’une configuration de l’exportateur de page pour votre site {#creating-a-page-exporter-configuration-for-your-site}

L’exportateur de page repose sur le framework de synchronisation du contenu. Les configurations disponibles dans la boîte de dialogue des propriétés de page sont des modèles de configuration. Ils définissent toutes les dépendances requises pour une page. Lorsqu’une exportation de page est déclenchée, le modèle de configuration est utilisé et le chemin de page et le chemin de conception sont appliqués dynamiquement à la configuration. Le fichier compressé est alors créé à l’aide de la fonctionnalité de synchronisation de contenu standard.

AEM incorpore quelques modèles, notamment :

* Par défaut : `/etc/contentsync/templates/default`. Ce modèle :

   * est le modèle de secours lorsqu’aucun modèle de configuration n’est trouvé dans le référentiel ;
   * Peut servir de base pour un nouveau modèle de configuration.

* Celle qui est dédiée au **Geometrixx** site, à l’adresse `/etc/contentsync/templates/geometrixx`. Ce modèle peut être utilisé comme exemple pour en créer un nouveau.

Pour créer un modèle de configuration de l’exportateur de page :

1. Dans **CRXDE Lite**, créez un nœud sous `/etc/contentsync/templates` :

   * Nom : Par exemple : `mysite`. Le nom s’affiche dans la boîte de dialogue Propriétés de la page lorsque vous sélectionnez le modèle de l’exportateur de page.
   * Type : `nt:unstructured`

1. Sous le nœud de modèle, appelé ici `mysite`, créez une structure de nœud à l’aide des nœuds de configuration décrits ci-dessous.

### Nœuds de configuration de l’exportateur de page {#page-exporter-configuration-nodes}

Le modèle de configuration se compose d’une structure de noeud. Chaque nœud possède une propriété `type` qui définit une action spécifique dans le processus de création du fichier compressé. Pour plus d’informations sur la propriété type, reportez-vous à la section Présentation des types de configuration de la page Structure de synchronisation de contenu .

Les noeuds suivants peuvent être utilisés pour créer un modèle de configuration d’exportation :

**noeud de page** Le noeud de page est utilisé pour copier le code HTML de la page dans le fichier zip. Il possède les caractéristiques suivantes :

* est un noeud obligatoire ;
* Se trouve sous `/etc/contentsync/templates/<sitename>`.
* Son nom est `page`.
* Son type de noeud est `nt:unstructured`

Le nœud `page` possède les propriétés suivantes :

* Une propriété `type` définie avec la valeur `pages`.

* Il ne comporte pas de propriété `path`, car le chemin d’accès actuel à la page est copié dynamiquement dans la configuration.

* Les autres propriétés sont décrites dans la section Présentation des types de configuration de la structure Synchronisation du contenu .

**noeud rewrite** Le noeud rewrite définit la manière dont les liens sont réécrits dans la page exportée. Les liens réécrits peuvent pointer vers les fichiers inclus dans le fichier compressé ou vers les ressources sur le serveur.

Reportez-vous à la page Synchronisation du contenu pour obtenir une description complète du `rewrite` noeud .

**noeud design** Le noeud de conception est utilisé pour copier la conception utilisée pour la page exportée. Il possède les caractéristiques suivantes :

* Il est facultatif.
* Se trouve sous `/etc/contentsync/templates/<sitename>`.
* Son nom est `design`.
* Son type de noeud est `nt:unstructured`.

Le nœud `design` possède les propriétés suivantes :

* Une propriété `type` définie avec la valeur `copy`.

* Il ne comporte pas de propriété `path`, car le chemin d’accès actuel à la page est copié dynamiquement dans la configuration.

**noeud générique** Un noeud générique est utilisé pour copier des ressources telles que des fichiers clientlibs .js ou .css dans le fichier zip. Il possède les caractéristiques suivantes :

* Il est facultatif.
* Se trouve sous `/etc/contentsync/templates/<sitename>`.
* Il ne possède pas de nom spécifique.
* Son type de noeud est `nt:unstructured`.
* Comporte un `type` de `type` propriétés connexes telles que définies dans la section Présentation des types de configuration de la structure de synchronisation de contenu.

Par exemple, le noeud de configuration suivant copie les fichiers geometrixx clientlibs.js dans le fichier zip :

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

Le **Geometrixx** le modèle de configuration d’export de page vous indique comment une exportation de page peut être configurée. Pour afficher la structure de noeud du modèle dans votre navigateur au format json, demandez l’URL suivante :

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Mise en œuvre d’une configuration personnalisée**

Comme vous l’avez peut-être remarqué dans la structure de noeud, la variable **Geometrixx** Le modèle de configuration d’exportation de page comporte une `logo` avec un noeud `type` définie sur `image`. Il s’agit d’un type de configuration spécial qui a été créé pour copier le logo de l’image dans le fichier zip. Pour répondre à certaines exigences spécifiques, vous devrez peut-être mettre en oeuvre une `type` property: pour ce faire, reportez-vous à la section Mise en oeuvre d’un gestionnaire de mise à jour personnalisé dans la page Synchronisation du contenu .

## Exportation d’une page par programmation {#programmatically-exporting-a-page}

Pour exporter une page par programmation, vous pouvez utiliser le service OSGi [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html). Ce service vous permet d’effectuer les opérations suivantes :

* Exportez une page et écrivez dans la réponse du servlet HTTP.
* Exportez une page et enregistrez le fichier zip à un emplacement spécifique.

Le servlet lié au sélecteur `export` et à l’extension `zip` utilise le service PageExporter.

## Résolution des problèmes {#troubleshooting}

Si vous rencontrez un problème lors du téléchargement du fichier compressé, supprimez le nœud `/var/contentsync` du référentiel et renvoyez la demande d’exportation.
