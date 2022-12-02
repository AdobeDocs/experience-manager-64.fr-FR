---
title: ASRP - Fournisseur de ressources de stockage d’Adobe
seo-title: ASRP - Adobe Storage Resource Provider
description: Configurer AEM Communities pour utiliser une base de données relationnelle comme magasin commun
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: Admin
exl-id: 136c0913-c8b8-451d-bb28-3c3285c172a1
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 3%

---

# ASRP - Fournisseur de ressources de stockage d’Adobe {#asrp-adobe-storage-resource-provider}

## A propos d’ASRP {#about-asrp}

Lorsqu’AEM Communities est configuré pour utiliser ASRP comme magasin commun, le contenu généré par l’utilisateur est accessible à partir de toutes les instances d’auteur et de publication sans avoir besoin de synchronisation ni de réplication.

Voir aussi [Caractéristiques des options SRP](working-with-srp.md#characteristics-of-srp-options) et [Topologies recommandées](topologies.md).

## Conditions requises {#requirements}

Une licence supplémentaire est requise pour l’utilisation d’ASRP.

Pour configurer votre site AEM Communities afin d’utiliser ASRP pour le contenu généré par l’utilisateur, contactez votre gestionnaire de compte pour :

* URL du centre de données (adresse du point de terminaison ASRP)
* Clé du client
* Clé secrète
* Identifiants de suite de rapports

Les clés client et secrète sont partagées dans toutes les suites de rapports d’une société. Il existe une suite de rapports par client.

## Configuration {#configuration}

### Sélectionner ASRP {#select-asrp}

Le [Console de configuration de stockage](srp-config.md) permet de sélectionner la configuration de stockage par défaut, qui identifie l’implémentation de la SRP à utiliser.

**À l’auteur**:

* À partir de la navigation globale : **[!UICONTROL Outils > Communautés > Configuration de stockage]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Sélectionner **[!UICONTROL Fournisseur de ressources de stockage Adobe (ASRP)]**
* Les informations suivantes proviennent du processus de mise en service :

   * **[!UICONTROL URL du centre de données]**

      Menu déroulant pour sélectionner le centre de données de production identifié par le représentant de votre compte.

   * **[!UICONTROL Suite de rapports par défaut]**

      Saisissez le nom de la suite de rapports par défaut.

   * **[!UICONTROL Clé du client]**

      Entrez la clé du consommateur

   * **[!UICONTROL Secret]**

      Entrez la clé secrète

* Sélectionnez **[!UICONTROL Envoyer]**

Préparez les instances de publication :

* [Réplication de la clé de cryptage](#replicate-the-crypto-key)
* [Réplication de la configuration](#publishing-the-configuration)

Après avoir soumis la configuration, testez la connexion :

* Sélectionner **[!UICONTROL Configuration du test]**
pour chaque instance d’auteur et de publication, testez la connexion au centre de données à partir de la console Configuration de stockage .

* Enfin, assurez-vous que les URL de site pour les données de profil sont routables à partir du centre de données par [externalisation des liens](#externalize-links).

### Réplication de la clé de chiffrement {#replicate-the-crypto-key}

La clé du client et la clé secrète sont chiffrées. Pour que les clés soient chiffrées/déchiffrées correctement, la Principale clé Crypto Granite doit être la même sur toutes les instances AEM.

Suivez les instructions de la section [Réplication de la clé de chiffrement](deploy-communities.md#replicate-the-crypto-key).

### Externaliser les liens {#externalize-links}

Pour des liens d’image de profil et de profil corrects, veillez à [Configuration de l’externaliseur de liens](../../help/sites-developing/externalizer.md).

Veillez à définir les domaines comme des URL routables à partir de l’URL du centre de données (point de terminaison ASRP).

### Synchronisation des heures {#time-synchronization}

Pour que l’authentification avec le point de terminaison ASRP réussisse, les machines qui exécutent votre AEM Communities hébergé doivent être synchronisées, comme avec la variable [NTP (Network Time Protocol)](https://www.ntp.org/).

### Publication de la configuration {#publishing-the-configuration}

ASRP doit être identifié comme le magasin commun sur toutes les instances d’auteur et de publication.

Pour rendre la configuration identique disponible dans l’environnement de publication :

* **À l’auteur**:

   * Accédez à à partir du menu principal **[!UICONTROL Outils > Opérations > Réplication]**
   * Sélectionner **[!UICONTROL Activer l’arborescence]**
   * **[!UICONTROL Chemin de début]**:

      * Accédez à `/etc/socialconfig/srpc/`
   * Décocher **[!UICONTROL Modifié uniquement]**
   * Sélectionner **[!UICONTROL Activer]**


## Mise à niveau à partir d’AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Si vous activez ASRP sur un site de communauté publié, tout contenu UGC déjà stocké dans [JCR](jsrp.md) ne sera plus visible, car il n’existe aucune synchronisation entre le stockage on-premise et le stockage dans le cloud.

**`AEM Communities Extension`** a été précédemment introduit dans les communautés sociales d’AEM 6.0 en tant que service cloud. À compter de la version 6.1 d’AEM Communities, aucune configuration de cloud n’est nécessaire, il vous suffit de sélectionner ASRP dans la [console de configuration de stockage](srp-config.md).

En raison de la nouvelle structure de stockage, il est nécessaire de suivre le [upgrade](upgrade.md#adobe-cloud-storage) instructions lors de la mise à niveau des communautés de réseaux sociaux vers les communautés.

## Gestion des données utilisateur {#managing-user-data}

Pour plus d’informations sur *utilisateurs*, *profils utilisateur* et *groupes d’utilisateurs*, souvent entrées dans l’environnement de publication, consultez

* [Synchronisation des utilisateurs](sync.md)
* [Gestion des utilisateurs et des groupes d’utilisateurs](users.md)

## Résolution des problèmes {#troubleshooting}

### Le contenu généré par l’utilisateur disparaît après la mise à niveau {#ugc-disappears-after-upgrade}

Si vous effectuez une mise à niveau à partir d’un site de communauté sociale AEM 6.0 existant, veillez à suivre le [instructions de mise à niveau](upgrade.md#adobe-cloud-storage), sinon UGC *apparence* à perdre.

### Erreurs d’authentification {#authentication-errors}

Si vous recevez des erreurs d’authentification par rapport à l’URL du centre de données et que le fichier error.log AEM contient des messages sur les horodatages obsolètes, vérifiez que la synchronisation est en cours.

Il est recommandé d’utiliser un outil tel que [NTP (Network Time Protocol)](https://www.ntp.org/) pour synchroniser tous les serveurs de création et de publication d’AEM.

### Le nouveau contenu n’apparaît pas dans les recherches {#new-content-does-not-appear-in-searches}

L’infrastructure de stockage dans le cloud Adobe utilise *cohérence éventuelle* pour atteindre les objectifs de mise à l’échelle et de performances. Pour cette raison, le nouveau contenu n’est pas immédiatement disponible et il peut s’écouler plusieurs secondes avant qu’il n’apparaisse dans les résultats de recherche.

Bien que l’intervalle qui affecte la cohérence éventuelle soit surveillé, contactez votre gestionnaire de compte si l’affichage du nouveau contenu dans les recherches prend plus de quelques secondes.

### UGC non visible dans ASRP {#ugc-not-visible-in-asrp}

Vérifiez que l&#39;option ASRP a été configurée pour être le fournisseur par défaut en vérifiant la configuration de l&#39;option de stockage. Par défaut, le fournisseur de ressources de stockage est JSRP, et non ASRP.

Sur toutes les instances d’AEM de création et de publication, consultez à nouveau la console Configuration de stockage ou vérifiez le référentiel AEM :

* Dans JCR, si [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Ne contient pas d’objet [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) , cela signifie que le fournisseur de stockage est JSRP.
   * Si le noeud srpc existe et contient le noeud [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), les propriétés de la configuration par défaut doivent définir ASRP comme fournisseur par défaut.
