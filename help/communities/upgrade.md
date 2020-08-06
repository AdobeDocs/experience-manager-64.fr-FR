---
title: Mise à niveau vers les communautés AEM 6.4
seo-title: Mise à niveau vers les communautés AEM 6.4
description: Mise à niveau d’une version antérieure vers AEM 6.4 Communautés
seo-description: Mise à niveau d’une version antérieure vers AEM 6.4 Communautés
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 5%

---


# Mise à niveau vers les communautés AEM 6.4 {#upgrading-to-aem-communities}

En fonction de la topologie et des fonctionnalités de chaque site, les actions suivantes peuvent s’avérer nécessaires lors de la mise à niveau vers AEM Communities 6.4 ou de l’installation du dernier pack de fonctionnalités.

Cette section est spécifique aux communautés et complète les informations fournies dans [Mise à niveau vers AEM 6.4](../../help/sites-deploying/upgrade.md) (plateforme).

## Mise à niveau à partir de AEM 6.1 ou version ultérieure {#upgrading-from-aem-or-later}

### Réindexer Solr {#reindex-solr}

Lors de l’installation d’un nouveau pack de fonctionnalités Communautés sur un déploiement configuré avec MSRP, il sera nécessaire de :

1. Installer le [dernier Feature Pack](deploy-communities.md#latestfeaturepack)
2. Installation des [derniers fichiers de configuration Solr](msrp.md#upgrading)
3. Réindexer MSRP

   voir la section Outil de réindexation [MSRP](msrp.md#msrp-reindex-tool)

### Enablement 2.0 {#enablement}

A partir de AEM 6.3, les fonctions d&#39;activation ne stockent plus d&#39;informations de rapports dans MySQL. La dépendance MySQL est présente uniquement pour le suivi du contenu SCORM.

Contactez le service à la [clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html) pour obtenir de l’aide sur la migration de contenu à partir d’Activation 1.0.

## Mise à niveau depuis AEM 6.0 {#upgrading-from-aem}

Si le contenu UGC préexistant doit être conservé, les moyens de le faire dépendent du stockage [sur site](#on-premise-storage) ou dans le cloud [d&#39;](#adobe-cloud-storage)Adobe du déploiement.

### Enregistrement Adobe Cloud {#adobe-cloud-storage}

Si le site mis à niveau a été configuré pour utiliser l&#39;enregistrement Adobe Cloud, il peut apparaître (incorrectement) comme si l&#39;ensemble de l&#39;UGC avait été perdu car les méthodes SRP ne pourront pas localiser l&#39;UGC préexistant à l&#39;ancien emplacement.

Ainsi, il est possible de demander à l&#39;ASRP d&#39;utiliser `AEM 6.0 compatability-mode` pour accéder à l&#39;UGC.

Pour toutes les instances d’auteur et de publication AEM 6.3

1. Connexion avec droits d’administrateur
2. Configuration d’ [ASRP](asrp.md)
3. Pour rendre visible la CU préexistante, procédez comme suit :
i. Accédez à la console Web, par exemple
   [https://&lt;hôte>:&lt;port>/system/console/configMgr](http://localhost:4502/system/console/configMgr)ii. Localisez **[!UICONTROL AEM Communities Utilities]** Configuration iii. Sélectionner pour développer le panneau de configuration
   * *Décocher* **`Cloud Storage`**
   * Sélectionnez **[!UICONTROL Enregistrer]**

![chlimage_1-126](assets/chlimage_1-126.png)

### Enregistrement sur site {#on-premise-storage}

Si le site mis à niveau n&#39;a pas utilisé l&#39;enregistrement de cloud, tout CU préexistant doit être converti pour se conformer à la nouvelle structure introduite dans AEM 6.1 Collectivités à l&#39;appui du magasin commun.

À cette fin, un outil de migration open source est disponible sur GitHub :\
[Outil de migration UGC AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### API Java {#java-apis}

Lors de la mise à niveau des communautés sociales AEM 6.0 vers AEM 6.3 communautés, sachez que de nombreuses API ont été réorganisées en différents packages. La plupart d&#39;entre elles doivent être facilement résolues lors de l&#39;utilisation d&#39;un IDE pour la personnalisation des fonctionnalités des communautés.

Pour plus d’informations sur le package SocialUtils obsolète, consultez [SocialUtils Refactoring](socialutils.md).

Voir aussi [Utilisation de Maven pour les communautés](maven.md).

### Aucun modèle de composant JSP {#no-jsp-component-templates}

Le cadre [du composant](scf.md) social (SCF) utilise le langage de modèle [HandlebarsJS](https://www.handlebarsjs.com/) (HBS) à la place du JSP (Java Server Pages) utilisé avant AEM 6.0.

Dans AEM 6.0, les composants JSP sont restés aux côtés des nouveaux composants de la structure HBS au même emplacement, les composants HBS étant généralement situés dans des sous-dossiers nommés &quot;hbs&quot;.

À partir de l&#39;AEM 6.1, les composants JSP ont été complètement supprimés. Pour les communautés, il est recommandé de remplacer toute utilisation de composants JSP par des composants SCF.

## Outil de migration UGC AEM Communities {#aem-communities-ugc-migration-tool}

L&#39;outil [de migration](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) AEM Communities UGC est un outil de migration open source, disponible sur GitHub, qui peut être personnalisé pour exporter l&#39;UGC à partir de versions antérieures de communautés sociales AEM et l&#39;importer dans AEM Communities 6.1 ou version ultérieure.

En plus de déplacer l&#39;UGC des versions antérieures, il est également possible d&#39;utiliser l&#39;outil pour déplacer l&#39;UGC d&#39;un [SRP](working-with-srp.md) à un autre, par exemple de MSRP à DSRP.

## Mise à niveau à partir de AEM 5.6.1 ou version antérieure {#upgrading-from-aem-or-earlier}

Sur le plan conceptuel, il y a trois générations de composantes communautaires :

**Gen 1**: environ CQ 5.4 à AEM 5.6.0 : il s&#39;agit des composants **collab** qui ont stocké l&#39;UGC dans le référentiel local en utilisant la réplication comme moyen de synchroniser l&#39;UGC sur les plateformes. D’autres différences concernent l’implémentation à l’aide de Java Server Pages (JSP) ainsi que la fonction de blog consistant à créer uniquement dans l’environnement d’auteur.

**Gen 2**: de AEM 5.6.1 à AEM 6.1 - il s&#39;agit d&#39;un mélange de **collab** et de composants **sociaux** . AEM 6.0 a introduit le nouveau cadre [des composants](scf.md) sociaux et AEM 6.2 a introduit un magasin [UGC](working-with-srp.md) commun où l’on peut accéder à UGC à l’aide d’un fournisseur [de ressources](srp.md) enregistrement (SRP).

**Gen 3**: à partir de l&#39;AEM 6.2, il n&#39;y a que des composants **sociaux** , mis en oeuvre dans SCF en tant que composants Handlebars (HBS) nécessitant un choix de SRP pour UGC.
