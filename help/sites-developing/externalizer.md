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
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 57%

---

# Externalisation d’URL{#externalizing-urls}

Dans AEM, **Externalizer** est un service OSGI qui vous permet de transformer par programmation un chemin d’accès à une ressource (par exemple, `/path/to/my/page`) dans une URL externe et absolue (par exemple, `https://www.mycompany.com/path/to/my/page`) en ajoutant un préfixe au chemin d’accès avec un DNS préconfiguré.

Une instance ne peut pas connaître son URL visible en externe si elle s’exécute derrière une couche web et il arrive qu’un lien doive être créé en dehors d’une étendue de demande. Dès lors, ce service fournit un emplacement centralisé pour configurer ces URL externes et les générer.

Cette page explique comment configurer le service **Externalizer** et l’utiliser. Pour plus d’informations, reportez-vous aux [JavaDocs](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Configuration du service Externalizer {#configuring-the-externalizer-service}

Le service **Externalizer** vous permet de définir de manière centralisée plusieurs domaines qui peuvent être utilisés pour préfixer par programmation les chemins d’accès aux ressources. Chaque domaine est identifié par un nom unique utilisé pour faire référence au domaine par programmation.

Pour définir un mappage de domaine pour le service **Externalizer**, procédez comme suit :

1. Accédez au gestionnaire de configuration via **Outils**, puis **Console web** ou saisissez `https://<host>:<port>/system/console/configMgr.`
1. Cliquez sur **Day CQ Link Externalizer** pour ouvrir la boîte de dialogue de configuration.

   >[!NOTE]
   >
   >Le lien direct vers la configuration est `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Définissez un mappage de domaine : un mappage se compose d’un nom unique qui peut être utilisé dans le code pour référencer le domaine, un espace et le domaine :

   `<unique-name> [scheme://]server[:port][/contextpath]`, où:

   * **Les schémas**  sont généralement http ou https, mais peuvent également être ftp, etc.; utilisez https pour imposer des liens https si nécessaire ; ce protocole est utilisé si le code client ne remplace pas le schéma lors de la demande d’externalisation d’une URL.
   * **** server est le nom d’hôte (il peut s’agir d’un nom de domaine ou d’une adresse ip).
   * **port**  (facultatif) est le numéro de port.
   * **contextpath**  (facultatif) n’est défini que si AEM est installé en tant qu’application web sous un autre chemin de contexte.

   Par exemple : `production https://my.production.instance`

   Les noms de mappage suivants sont prédéfinis et doivent toujours être définis car AEM s’y appuie :

   * **local**  : instance locale
   * **author**  : DNS du système de création
   * **publish**  : DNS du site web public

   >[!NOTE]
   >
   >Une configuration personnalisée vous permet d’ajouter une nouvelle catégorie, telle que « production », « staging », voire des systèmes non AEM externes, tels que « my-internal-webservice ». Elle s’avère utile pour éviter le codage en dur de telles URL en différents points du codebase d’un projet.

1. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

>[!NOTE]
>
>Adobe vous recommande [d’ajouter la configuration au référentiel](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Utilisation du service Externalizer {#using-the-externalizer-service}

Cette section illustre quelques exemples d’utilisation du service **Externalizer**.

**Pour obtenir le service Externalizer dans un JSP :**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Pour externaliser un chemin d’accès avec le domaine « publish » :**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

En supposant que le mappage de domaine &quot;`publish https://www.website.com`&quot;, myExternalizedUrl se termine par la valeur &quot;`https://www.website.com/contextpath/my/page.html`&quot;.

**Pour externaliser un chemin d’accès avec le domaine « author » :**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

En supposant que le mappage de domaine &quot;`author https://author.website.com`&quot;, myExternalizedUrl se termine par la valeur &quot;`https://author.website.com/contextpath/my/page.html`&quot;.

**Pour externaliser un chemin d’accès avec le domaine « local », procédez comme suit :**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

En supposant que le mappage de domaine &quot;`local https://publish-3.internal`&quot;, myExternalizedUrl se termine par la valeur &quot;`https://publish-3.internal/contextpath/my/page.html`&quot;.

Vous trouverez d’autres exemples dans les [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
