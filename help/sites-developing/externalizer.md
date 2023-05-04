---
title: Externalisation d’URL
seo-title: Externalizing URLs
description: Externalizer est un service OSGI qui vous permet de transformer, par programmation, un chemin d’accès à une ressource en URL absolue externe.
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 41%

---

# Externalisation d’URL{#externalizing-urls}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Dans AEM, **Externalizer** est un service OSGI qui vous permet de transformer, par programmation, un chemin d’accès aux ressources (`/path/to/my/page`) en une URL externe et absolue (`https://www.mycompany.com/path/to/my/page`, par exemple) en faisant précéder le chemin d’accès d’un DNS préconfiguré.

Comme une instance ne peut pas connaître son URL visible en externe si elle s’exécute derrière une couche web, et qu’il arrive qu’un lien doive être créé en dehors de la portée de la requête, ce service fournit un emplacement central pour configurer ces URL externes et les créer.

Cette page explique comment configurer la variable **Externalizer** et comment l’utiliser. Pour plus d’informations, reportez-vous à la section [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Configuration du service Externalizer {#configuring-the-externalizer-service}

Le service **Externalizer** vous permet de définir, de manière centralisée, plusieurs domaines pouvant être utilisés pour préfixer des chemins d’accès aux ressources par programmation. Chaque domaine est identifié par un nom unique utilisé pour référencer le domaine par programmation.

Pour définir un mappage de domaine pour la variable **Externalizer** service :

1. Accédez au gestionnaire de configuration via **Outils**, puis **Console web** ou saisissez `https://<host>:<port>/system/console/configMgr.`
1. Cliquez sur l’**Externaliseur de lien Day CQ** pour ouvrir la boîte de dialogue de configuration.

   >[!NOTE]
   >
   >Le lien direct vers la configuration est `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Définissez un mappage de domaine : un mappage se compose d’un nom unique qui peut être utilisé dans le code pour référencer le domaine, un espace et le domaine :

   `<unique-name> [scheme://]server[:port][/contextpath]`, où:

   * **scheme** est généralement http ou https, mais peut également être ftp, etc.; utilisez https pour appliquer les liens https, le cas échéant ; il sera utilisé si le code client ne remplace pas le schéma lors de la demande d’externalisation d’une URL.
   * **Server** est le nom d’hôte (il peut s’agir d’un nom de domaine ou d’une adresse IP).
   * **Port** (facultatif) est le numéro de port.
   * **contextpath** (facultatif) est défini uniquement si AEM est installé en tant qu’application Web sous un autre chemin d’accès au contexte.

   Par exemple : `production https://my.production.instance`

   Les noms de mappage suivants sont prédéfinis et doivent toujours être configurés, car AEM en dépend :

   * **local** - instance locale
   * **author** - le DNS du système de création
   * **publier** - DNS du site web public

   >[!NOTE]
   >
   >Une configuration personnalisée vous permet d’ajouter une nouvelle catégorie, telle que &quot;production&quot;, &quot;staging&quot; ou même des systèmes non AEM externes tels que &quot;my-internal-webservice&quot;. Elle s’avère utile pour éviter de coder en dur de telles URL à différents endroits dans le code base d’un projet.

1. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

>[!NOTE]
>
>Adobe vous recommande d’[ajouter la configuration au référentiel](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Utilisation du service Externalizer {#using-the-externalizer-service}

Cette section présente quelques exemples de la manière dont la fonction **Externalizer** peut être utilisé.

**Pour obtenir le service Externalizer dans un JSP :**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Pour externaliser un chemin d’accès avec le domaine « publish » :**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

En supposant le mappage de domaine &quot; `publish https://www.website.com`&quot;, myExternalizedUrl se termine par la valeur &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**Pour externaliser un chemin d’accès avec le domaine « author » :**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

En supposant le mappage de domaine &quot; `author https://author.website.com`&quot;, myExternalizedUrl se termine par la valeur &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**Pour externaliser un chemin d’accès avec le domaine « local », procédez comme suit :**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

En supposant le mappage de domaine &quot; `local https://publish-3.internal`&quot;, myExternalizedUrl se termine par la valeur &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Vous trouverez d’autres exemples dans les [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
