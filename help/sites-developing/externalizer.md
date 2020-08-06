---
title: Externalisation d’URL
seo-title: Externalisation d’URL
description: Externalizer est un service OSGI qui vous permet de transformer, par programmation, un chemin d’accès aux ressources en une URL externe et absolue.
seo-description: Externalizer est un service OSGI qui vous permet de transformer, par programmation, un chemin d’accès aux ressources en une URL externe et absolue.
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 57%

---


# Externalisation d’URL{#externalizing-urls}

In AEM, the **Externalizer** is an OSGI service that allows you to programmatically transform a resource path (e.g. `/path/to/my/page`) into an external and absolute URL (for example, `https://www.mycompany.com/path/to/my/page`) by prefixing the path with a pre-configured DNS.

Une instance ne peut pas connaître son URL visible en externe si elle s’exécute derrière une couche web et il arrive qu’un lien doive être créé en dehors d’une étendue de demande. Dès lors, ce service fournit un emplacement centralisé pour configurer ces URL externes et les générer.

Cette page explique comment configurer le service **Externalizer** et l’utiliser. Pour plus d’informations, reportez-vous aux [JavaDocs](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Configuration du service Externalizer {#configuring-the-externalizer-service}

The **Externalizer** service allows you to centrally define multiple domains that can be used to programmatically prefix resource paths. Chaque domaine est identifié par un nom unique utilisé pour faire référence au domaine par programmation.

Pour définir un mappage de domaine pour le service **Externalizer**, procédez comme suit :

1. Accédez au gestionnaire de configuration via **Outils**, puis à la console **** Web, ou saisissez `https://<host>:<port>/system/console/configMgr.`
1. Click **Day CQ Link Externalizer** to open the configuration dialog box.

   >[!NOTE]
   >
   >Le lien direct vers la configuration est `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Définissez un mappage de domaine : un mappage consiste en un nom unique qui peut être utilisé dans le code pour référencer le domaine, un espace et le domaine :

   `<unique-name> [scheme://]server[:port][/contextpath]`, où:

   * **schéma** est généralement http ou https, mais peut aussi être ftp, etc.; utilisez https pour imposer des liens https si nécessaire ; ce protocole est utilisé si le code client ne remplace pas le schéma lors de la demande d’externalisation d’une URL.
   * **server** est le nom d’hôte (peut être un nom de domaine ou une adresse ip).
   * **port** (facultatif) est le numéro de port.
   * **contextpath** (facultatif) n’est défini que si AEM est installé en tant qu’application web sous un chemin de contexte différent.

   Par exemple : `production https://my.production.instance`

   Les noms de mappage suivants sont prédéfinis et doivent toujours être définis en fonction de leur utilisation AEM :

   * **local** - instance locale
   * **auteur** - DNS du système de création
   * **publish** - DNS du site Web destiné au public

   >[!NOTE]
   >
   >Une configuration personnalisée vous permet d’ajouter une nouvelle catégorie, telle que « production », « staging », voire des systèmes non AEM externes, tels que « my-internal-webservice ». Elle s’avère utile pour éviter le codage en dur de telles URL en différents points du codebase d’un projet.

1. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

>[!NOTE]
>
>Adobe recommends that you [add the configuration to the repository](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Utilisation du service Externalizer {#using-the-externalizer-service}

Cette section illustre quelques exemples d’utilisation du service **Externalizer**.

**Pour obtenir le service Externalizer dans un JSP :**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Pour externaliser un chemin d’accès avec le domaine « publish » :**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

Assuming the domain mapping &quot; `publish https://www.website.com`&quot;, myExternalizedUrl ends up with the value &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**Pour externaliser un chemin d’accès avec le domaine « author » :**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

Assuming the domain mapping &quot; `author https://author.website.com`&quot;, myExternalizedUrl ends up with the value &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**Pour externaliser un chemin d’accès avec le domaine « local », procédez comme suit :**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

Assuming the domain mapping &quot; `local https://publish-3.internal`&quot;, myExternalizedUrl ends up with the value &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Vous trouverez d’autres exemples dans les [Javadocs](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
