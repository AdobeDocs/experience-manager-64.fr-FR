---
title: Utilisation de Maven pour Communities
seo-title: Using Maven for Communities
description: Fichier jar de l’API AEM Communities et fichier jar de l’API Uber AEM
seo-description: AEM Communities API jar and AEM Uber API jar
uuid: ea37a89a-db6c-4018-8ab9-f5717e6c0421
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a726c904-aadd-4678-be84-9e05808ab8be
exl-id: d86411b9-6ed1-4091-bf5c-d46b4e518da4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Utilisation de Maven pour Communities {#using-maven-for-communities}

## Présentation {#overview}

Cette section de la documentation d’AEM Communities s’ajoute aux éléments suivants :

* [Création de projets AEM à l’aide d’Apache Maven](../../help/sites-developing/ht-projects-maven.md).

Il n’existe qu’un seul artefact &quot;uber&quot; qui remplace les artefacts individuels :

* AEM [Fichier jar d’API Uber](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

>[!NOTE]
>
>À partir d’AEM version 6.4, les API Communities ne sont pas publiées explicitement. Toutes les API Communities sont désormais incluses dans le jar Uber lui-même.
>
>Il est recommandé de rester à jour avec la version la plus récente de Communities.
>
>Voir [Dernières versions](deploy-communities.md#latest-releases) pour identifier la version la plus récente.

## Exemple de dépendance Maven {#maven-dependency-example}

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.4.8.3</version>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Voir [Référentiel Uber jar AEM](https://mvnrepository.com/artifact/com.adobe.aem/uber-jar) pour identifier le dernier artefact Uber jar.

<!--
# Using Maven for Communities {#using-maven-for-communities}

## Overview {#overview}

This section of the AEM Communities documentation is in addition to:

* [How to Build AEM Projects using Apache Maven](../../help/sites-developing/ht-projects-maven.md)

There are now two "uber" artifacts that replace individual artifacts:

* AEM [Communities API jar](#communities-api-jar-artifact)
* AEM [Uber API jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API Jar Artifact {#communities-api-jar-artifact}

Following is an example of a GAV for the AEM Communities API jar:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>

```

Ensure thet the version specified corresponds with the Communities package version installed for AEM Communities. To verify the installed version number:

1. Login with adminstrative privileges.
2. Browse to [Package Manager](../../help/sites-administering/package-manager.md). For example, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

3. locate the package *cq-socialcommunities-pkg-1.x.xxx*
4. extract the version from the package name
    * first version for AEM 6.3 is version 1.11.170
    * feature packs will be versions 1.12.xxx
    
>[!NOTE]
>
>It is recommended to keep up-to-date with the most recent Communities release.
>
>Visit the [Latest Releases](deploy-communities.md#latest-releases) section to identify the most recent version.

## Maven Dependency Example {#maven-dependency-example}

The Communities API jar must be specified before the Uber API jar.

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.3.0</version>
    <scope>provided</scope>
    <classifier>apis</classifier>
</dependency>
```
-->
