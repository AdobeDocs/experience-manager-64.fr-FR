---
title: Mise à niveau vers les communautés AEM 6.4
seo-title: Upgrading to AEM 6.4 Communities
description: Mise à niveau d’une version antérieure vers AEM 6.4 Communities
seo-description: How to upgrade from an earlier version to AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: 0f82e82cf6e09a2734893a98d67ed1a84b1fec5e
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 4%

---

# Mise à niveau vers les communautés AEM 6.4 {#upgrading-to-aem-communities}

Selon la topologie et les fonctionnalités de chaque site, les actions suivantes peuvent être nécessaires lors de la mise à niveau vers AEM Communities 6.4 ou de l’installation du dernier Feature Pack.

Cette section est spécifique aux communautés et complète les informations fournies dans la section [Mise à niveau vers AEM 6.4](../../help/sites-deploying/upgrade.md) (plateforme).

## Mise à niveau à partir d’AEM 6.1 ou version ultérieure {#upgrading-from-aem-or-later}

### Réindexation Solr {#reindex-solr}

Lors de l’installation d’un nouveau Feature Pack Communities sur un déploiement configuré avec MSRP, il sera nécessaire de :

1. Installez le [dernier Feature Pack](deploy-communities.md#latestfeaturepack)
2. Installez le [les derniers fichiers de configuration Solr](msrp.md#upgrading)
3. Réindexation MSRP

   voir section [Outil de réindexation MSRP](msrp.md#msrp-reindex-tool)

### Activation 2.0 {#enablement}

Depuis la version 6.3 d’AEM, les fonctionnalités d’activation ne stockent plus les informations de création de rapports dans MySQL. La dépendance MySQL est présente uniquement pour le suivi du contenu SCORM.

Veuillez contacter [service clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html) pour obtenir de l’aide sur la migration de contenu à partir d’Activation 1.0.

## Mise à niveau à partir d’AEM 6.0 {#upgrading-from-aem}

Si le contenu généré par l’utilisateur préexistant doit être conservé, les moyens de le faire dépendent du stockage ou non du contenu stocké par le déploiement. [on-premise](#on-premise-storage) ou dans la variable [Adobe Cloud](#adobe-cloud-storage).

### Stockage dans le cloud Adobe {#adobe-cloud-storage}

Si le site mis à niveau a été configuré pour utiliser l’espace de stockage dans le cloud Adobe, il peut s’afficher (de manière incorrecte) comme si tout le contenu généré par l’utilisateur a été perdu, car les méthodes SRP ne pourront pas localiser le contenu créé par l’utilisateur existant à l’ancien emplacement.

Il est donc possible d’ordonner à ASRP d’utiliser `AEM 6.0 compatability-mode` pour accéder au contenu généré par l’utilisateur.

Pour toutes les instances de création et de publication AEM 6.3 :

1. Connexion avec droits d’administrateur et configuration [ASRP](asrp.md).
1. Pour rendre visible le contenu créé par l’utilisateur existant, procédez comme suit :

   i. Accédez à la console web. L’URL par défaut est 
   `https://localhost:4502/system/console/configMgr`.

   ii. Localiser **[!UICONTROL Utilitaires AEM Communities]** et sélectionnez pour développer le panneau de configuration.

   iii. Décocher **[!UICONTROL Stockage dans le cloud]** et cliquez sur **[!UICONTROL Enregistrer]**.

![chlimage_1-126](assets/chlimage_1-126.png)

### Stockage On-premise {#on-premise-storage}

Si le site mis à niveau n’a pas utilisé l’espace de stockage dans le cloud, tout contenu généré par l’utilisateur préexistant doit être converti pour se conformer à la nouvelle structure introduite dans AEM 6.1 Communities pour prendre en charge le magasin commun.

À cette fin, un outil de migration Open Source est disponible sur GitHub :\
[Outil de migration UGC AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### API Java {#java-apis}

Lors de la mise à niveau d’AEM 6.0 communautés sociales vers AEM 6.3 communautés, sachez que de nombreuses API ont été réorganisées en différents packages. La plupart de ces problèmes doivent être facilement résolus lors de l’utilisation d’un IDE pour la personnalisation des fonctionnalités de Communities.

Pour plus d’informations sur le module SocialUtils obsolète, consultez la page [Refactorisation de SocialUtils](socialutils.md).

Voir aussi [Utilisation de Maven pour Communities](maven.md).

### Aucun modèle de composant JSP {#no-jsp-component-templates}

Le [structure des composants sociaux](scf.md) (SCF) utilise la variable [HandlebarsJS](https://handlebarsjs.com/) (HBS) langage de modèle à la place de Java Server Pages (JSP) utilisé avant AEM 6.0.

Dans AEM 6.0, les composants JSP sont restés aux côtés des nouveaux composants de structure HBS au même emplacement, les composants HBS se trouvant généralement dans des sous-dossiers appelés &quot;hbs&quot;.

À compter de la version AEM 6.1, les composants JSP ont été complètement supprimés. Pour Communities, il est recommandé de remplacer toute utilisation de composants JSP par des composants SCF.

## Outil de migration UGC AEM Communities {#aem-communities-ugc-migration-tool}

Le [Outil de migration UGC AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) est un outil de migration Open Source, disponible sur GitHub, qui peut être personnalisé pour exporter du contenu créé par l’utilisateur à partir de versions antérieures d’AEM communautés sociales et l’importer dans AEM Communities 6.1 ou version ultérieure.

En plus de déplacer le contenu créé par l’utilisateur des versions antérieures, il est également possible d’utiliser l’outil pour déplacer le contenu créé par l’utilisateur d’une version à l’autre. [SRP](working-with-srp.md) à un autre, comme de MSRP à DSRP.

## Mise à niveau à partir d’AEM 5.6.1 ou d’une version antérieure {#upgrading-from-aem-or-earlier}

D&#39;un point de vue conceptuel, il existe trois générations de composantes de communautés :

**Gen 1**: environ CQ 5.4 à AEM 5.6.0 : **collab** les composants qui ont stocké le contenu généré par l’utilisateur dans le référentiel local à l’aide de la réplication comme moyen de synchroniser le contenu créé par l’utilisateur sur toutes les plateformes. D’autres différences concernent l’implémentation à l’aide de Java Server Pages (JSP) ainsi que la fonctionnalité de blog consistant à créer uniquement dans l’environnement de création.

**Gen 2**: d’AEM 5.6.1 à AEM 6.1 - ceci est un mélange de **collab** et **social** composants. AEM 6.0 a introduit la nouvelle [structure des composants sociaux](scf.md) (SCF) et AEM 6.2 ont introduit une [magasin UGC commun](working-with-srp.md) où le contenu généré par l’utilisateur est accessible à l’aide d’une [fournisseur de ressources de stockage](srp.md) (SRP).

**Gen 3**: à partir de la version 6.2 d’AEM, il n’y a que **social** composants, implémentés dans SCF en tant que composants Handlebars (HBS) nécessitant un choix de SRP pour le contenu généré par l’utilisateur.
