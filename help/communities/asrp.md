---
title: ASRP - Fournisseur de ressources d'Enregistrement d'Adobe
seo-title: ASRP - Fournisseur de ressources d'Enregistrement d'Adobe
description: Configurer AEM Communities pour utiliser une base de données relationnelle comme magasin commun
seo-description: Configurer AEM Communities pour utiliser une base de données relationnelle comme magasin commun
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 2%

---


# ASRP - Fournisseur de ressources d&#39;Enregistrement d&#39;Adobe {#asrp-adobe-storage-resource-provider}

## A propos d&#39;ASRP {#about-asrp}

Lorsque AEM Communities est configuré pour utiliser ASRP en tant que magasin commun, le contenu généré par l’utilisateur est accessible à partir de toutes les instances d’auteur et de publication sans avoir besoin de synchronisation ni de réplication.

Voir aussi [Caractéristiques des options](working-with-srp.md#characteristics-of-srp-options) SRP et Topologies [](topologies.md)recommandées.

## Conditions requises {#requirements}

Une licence supplémentaire est requise pour l&#39;utilisation de ASRP.

Pour configurer votre site AEM Communities de manière à utiliser ASRP pour UGC, contactez votre gestionnaire de compte pour :

* URL du centre de données (adresse du point de terminaison ASRP)
* Clé du client
* Clé secrète
* ID de suite de rapports

Les clés secrètes et de consommation sont partagées dans toutes les suites de rapports pour une société. Il existe une suite de rapports par client.

## Configuration {#configuration}

### Sélectionner ASRP {#select-asrp}

La console [Configuration de l&#39;](srp-config.md) Enregistrement permet de sélectionner la configuration d&#39;enregistrement par défaut, qui identifie l&#39;implémentation de SRP à utiliser.

**Sur l&#39;auteur**:

* A partir de la navigation globale : **[!UICONTROL Outils > Communautés > Configuration des Enregistrements]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Select **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**
* Les informations suivantes proviennent du processus de mise en service

   * **[!UICONTROL URL du centre de données]**

      Menu déroulant pour sélectionner le centre de données de production identifié par votre gestionnaire de compte

   * **[!UICONTROL Suite de rapports par défaut]**

      Entrez le nom de la Report Suite par défaut.

   * **[!UICONTROL Clé du client]**

      Entrez le consumer key

   * **[!UICONTROL Secret]**

      Saisissez la clé secrète

* Sélectionnez **[!UICONTROL Envoyer]**

Préparez les instances de publication :

* [Répliquer la clé de chiffrement](#replicate-the-crypto-key)
* [Réplication de la configuration](#publishing-the-configuration)

Après avoir envoyé la configuration, testez la connexion :

* Sélectionnez **[!UICONTROL Tester la configuration]** pour chaque instance d’auteur et de publication, testez la connexion au centre de données à partir de la console de configuration de l’Enregistrement.

* Enfin, veillez à ce que les URL du site pour les données de profil soient routables à partir du centre de données en [externalisant les liens](#externalize-links).

### Réplication de la clé Crypto {#replicate-the-crypto-key}

Le Consumer key et la clé secrète sont chiffrés. Pour que les clés soient chiffrées/déchiffrées correctement, la Principale clé Crypto de granit doit être la même sur toutes les instances AEM.

Suivez les instructions de la section [Répliquer la clé](deploy-communities.md#replicate-the-crypto-key)Crypto.

### Liens externes {#externalize-links}

Pour des liens d’image de profil et de profil corrects, veillez à [configurer correctement l’Externalisateur de liens](../../help/sites-developing/externalizer.md).

Veillez à définir les domaines comme des URL routables à partir de l’URL du centre de données (point de terminaison ASRP).

### Synchronisation du temps {#time-synchronization}

Pour que l&#39;authentification avec le point de terminaison ASRP réussisse, les machines exécutant votre AEM Communities hébergée doivent être synchronisées dans le temps, par exemple avec le protocole NTP ( [Network Time Protocol)](https://www.ntp.org/).

### Publication de la configuration {#publishing-the-configuration}

ASRP doit être identifié comme le magasin commun sur toutes les instances d’auteur et de publication.

Pour rendre la configuration identique disponible dans l’environnement de publication :

* **Sur l&#39;auteur**:

   * Accédez au menu principal à **[!UICONTROL Outils > Opérations > Réplication.]**
   * Sélectionner **[!UICONTROL Activer l&#39;arborescence]**
   * **[!UICONTROL Chemin de début]**:

      * Naviguer jusqu’à `/etc/socialconfig/srpc/`
   * Désélectionner **[!UICONTROL uniquement modifié]**
   * Sélectionner **[!UICONTROL Activer]**


## Mise à niveau depuis AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Si vous activez ASRP sur un site de communauté publié, les UGC déjà stockées dans [JCR](jsrp.md) ne seront plus visibles car il n’y a pas de synchronisation des données entre l’enregistrement sur site et l’enregistrement cloud.

**`AEM Communities Extension`** était auparavant introduit dans AEM 6.0 communautés sociales en tant que service cloud. À partir de AEM 6.1 Communautés, aucune configuration de cloud n&#39;est nécessaire, il vous suffit de sélectionner ASRP dans la console [de configuration de l&#39;](srp-config.md)enregistrement.

En raison de la nouvelle structure d’enregistrement, il est nécessaire de suivre les instructions de [mise à niveau](upgrade.md#adobe-cloud-storage) lors de la mise à niveau des communautés sociales vers les communautés.

## Gestion des données utilisateur {#managing-user-data}

Pour plus d’informations sur *les utilisateurs*, les profils ** utilisateur et les groupes *d’* utilisateurs, souvent saisis dans l’environnement de publication, consultez la page

* [Synchronisation des utilisateurs](sync.md)
* [Gestion des utilisateurs et des groupes d’utilisateurs](users.md)

## Résolution des incidents {#troubleshooting}

### UGC disparaît après la mise à niveau {#ugc-disappears-after-upgrade}

Si la mise à niveau à partir d’un site de communauté sociale AEM 6.0 existe déjà, veillez à suivre les instructions [de](upgrade.md#adobe-cloud-storage)mise à niveau, sinon l’UGC *semble* être perdu.

### Erreurs d’authentification {#authentication-errors}

Si vous recevez des erreurs d’authentification par rapport à l’URL du centre de données et que l’AEM error.log contient des messages sur les horodatages obsolètes, vérifiez que la synchronisation de l’heure est en cours.

Il est recommandé d’utiliser un outil tel que le protocole NTP ( [Network Time Protocol)](https://www.ntp.org/) pour synchroniser tous les serveurs d’auteur et de publication AEM.

### Le nouveau contenu n&#39;apparaît pas dans les recherches {#new-content-does-not-appear-in-searches}

L&#39;infrastructure d&#39;enregistrement de cloud d&#39;Adobes utilise *éventuellement la cohérence* pour aider à atteindre ses objectifs de mise à l&#39;échelle et de performance. Pour cette raison, le nouveau contenu n’est pas instantanément disponible et il peut s’écouler plusieurs secondes avant qu’il ne s’affiche dans les résultats de la recherche.

Bien que l’intervalle affectant la cohérence éventuelle soit surveillé, contactez le représentant du compte si l’affichage du nouveau contenu dans les recherches prend plus de quelques secondes.

### UGC invisible dans ASRP {#ugc-not-visible-in-asrp}

Vérifiez que ASRP a été configuré pour être le fournisseur par défaut en vérifiant la configuration de l&#39;option enregistrement. Par défaut, le fournisseur de ressources d’enregistrement est JSRP et non ASRP.

Sur toutes les instances d’AEM création et de publication, revisitez la console de configuration de l’Enregistrement ou vérifiez le référentiel AEM :

* Dans JCR, si [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Ne contient pas de noeud [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) , cela signifie que le fournisseur d’enregistrements est JSRP
   * Si le noeud srpc existe et contient la configuration [par](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)défaut du noeud, les propriétés de la configuration par défaut doivent définir ASRP comme fournisseur par défaut.

