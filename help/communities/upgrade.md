---
title: Mise à niveau vers les communautés AEM 6.4
seo-title: Mise à niveau vers les communautés AEM 6.4
description: Mise à niveau d’une version antérieure vers AEM 6.4 Communities
seo-description: Mise à niveau d’une version antérieure vers AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c

---


# Mise à niveau vers les communautés AEM 6.4 {#upgrading-to-aem-communities}

Selon la topologie et les fonctionnalités de chaque site, les actions suivantes peuvent être nécessaires lors de la mise à niveau vers AEM Communities 6.4 ou de l’installation du dernier Feature Pack.

Cette section est spécifique aux communautés et complète les informations fournies dans [Mise à niveau vers AEM 6.4](../../help/sites-deploying/upgrade.md) (plateforme).

## Mise à niveau à partir d’AEM 6.1 ou version ultérieure {#upgrading-from-aem-or-later}

### Réindexer Solr {#reindex-solr}

Lors de l’installation d’un nouveau Feature Pack de communautés sur un déploiement configuré avec MSRP, vous devez effectuer les opérations suivantes :

1. Installation du [dernier Feature Pack](deploy-communities.md#latestfeaturepack)
2. Installation des [derniers fichiers de configuration Solr](msrp.md#upgrading)
3. Réindexer le MSRP

   voir la section Outil de réindexation [MSRP](msrp.md#msrp-reindex-tool)

### Enablement 2.0 {#enablement}

Depuis AEM 6.3, les fonctionnalités d’activation ne stockent plus les informations de création de rapports dans MySQL. La dépendance MySQL est présente uniquement pour le suivi du contenu SCORM.

Contactez le service à la [clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html) pour obtenir de l’aide sur la migration de contenu à partir d’Activation 1.0.

## Mise à niveau à partir d’AEM 6.0 {#upgrading-from-aem}

S’il est nécessaire de conserver les fichiers UGC préexistants, les moyens d’y parvenir dépendent du stockage [local](#on-premise-storage) ou dans le cloud [](#adobe-cloud-storage)Adobe du déploiement.

### Stockage Adobe Cloud {#adobe-cloud-storage}

Si le site mis à niveau a été configuré pour utiliser le stockage en mode cloud Adobe, il se peut qu’il s’affiche (à tort) comme si toutes les données UGC avaient été perdues, car les méthodes SRP ne pourront pas localiser le fichier UGC préexistant à l’ancien emplacement.

Ainsi, il est possible de demander à l&#39;ASRP d&#39;utiliser `AEM 6.0 compatability-mode` l&#39;UGC pour accéder à l&#39;UGC.

Pour toutes les instances d’auteur et de publication AEM 6.3

1. Connexion avec droits d’administrateur
2. Configuration d’ [ASRP](asrp.md)
3. Procédez comme suit pour rendre visible le contenu UGC préexistant :
i. Accédez à la console Web, par exemple
   [https://&lt;hôte>:&lt;port>/system/console/configMgr](http://localhost:4502/system/console/configMgr)ii. Localisez **[!UICONTROL AEM Communities Utilities]** Configuration iii. Sélectionner pour développer le panneau de configuration
   * *Désélectionner***`Cloud Storage`**
   * Sélectionnez **[!UICONTROL Enregistrer]**

![chlimage_1-126](assets/chlimage_1-126.png)

### Stockage sur site {#on-premise-storage}

Si le site mis à niveau n’utilisait pas le stockage en mode cloud, tout fichier UGC préexistant doit être converti pour être conforme à la nouvelle structure introduite dans les communautés AEM 6.1 pour prendre en charge le magasin commun.

À cette fin, un outil de migration Open Source est disponible sur GitHub :\
[Outil de migration UGC des communautés AEM](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### API Java {#java-apis}

Lors de la mise à niveau des communautés sociales AEM 6.0 vers les communautés AEM 6.3, sachez que de nombreuses API ont été réorganisées en différents packages. La plupart d&#39;entre elles doivent être facilement résolues lors de l&#39;utilisation d&#39;un IDE pour la personnalisation des fonctionnalités des communautés.

Pour plus d’informations sur le package SocialUtils obsolète, consultez [SocialUtils Refactoring](socialutils.md).

Voir aussi [Utilisation de Maven pour les communautés](maven.md).

### Aucun modèle de composant JSP {#no-jsp-component-templates}

Le cadre [du composant](scf.md) social (SCF) utilise le langage de modèle [HandlebarsJS](https://www.handlebarsjs.com/) (HBS) à la place du JSP (Java Server Pages) utilisé avant AEM 6.0.

Dans AEM 6.0, les composants JSP sont restés aux côtés des nouveaux composants de la structure HBS au même emplacement, les composants HBS étant généralement situés dans des sous-dossiers nommés &quot;hbs&quot;.

Depuis AEM 6.1, les composants JSP ont été complètement supprimés. Pour les communautés, il est recommandé de remplacer toute utilisation de composants JSP par des composants SCF.

## Outil de migration UGC des communautés AEM {#aem-communities-ugc-migration-tool}

L’outil [de migration UGC des communautés](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) AEM est un outil de migration Open Source disponible sur GitHub. Il peut être personnalisé pour exporter l’UGC à partir des versions antérieures des communautés sociales AEM et l’importer dans les communautés AEM 6.1 ou une version ultérieure.

En plus de déplacer l&#39;UGC des versions antérieures, il est également possible d&#39;utiliser l&#39;outil pour déplacer l&#39;UGC d&#39;un [SRP](working-with-srp.md) à un autre, par exemple du MSRP vers le DSRP.

## Mise à niveau à partir d’AEM 5.6.1 ou version antérieure {#upgrading-from-aem-or-earlier}

D&#39;un point de vue conceptuel, il existe trois générations d&#39;éléments communautaires :

**Gen 1**: environ CQ 5.4 à AEM 5.6.0 : il s’agit des composants **collab** qui stockaient l’UGC dans le référentiel local à l’aide de la réplication comme moyen de synchroniser l’UGC sur les plateformes. D’autres différences concernent l’implémentation à l’aide de Java Server Pages (JSP) ainsi que la fonctionnalité de blog consistant à créer uniquement dans l’environnement de création.

**Gen 2**: d’AEM 5.6.1 à AEM 6.1 : il s’agit d’un mélange de composants **collab** et **sociaux** . AEM 6.0 a introduit la nouvelle structure [des composants](scf.md) sociaux (SCF) et AEM 6.2 a introduit une boutique [UGC](working-with-srp.md) commune dans laquelle l’accès à l’UGC est effectué à l’aide d’un fournisseur [de ressources de](srp.md) stockage (SRP).

**Gen 3**: depuis AEM 6.2, il n’existe que des composants **sociaux** , implémentés dans SCF en tant que composants HBS (Handlebars) nécessitant un choix de SRP pour UGC.
