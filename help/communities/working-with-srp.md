---
title: SRP - Stockage de contenu de la communauté
seo-title: SRP - Community Content Storage
description: Depuis AEM Communities 6.1, le contenu généré par l’utilisateur est stocké dans un seul magasin commun fourni par un fournisseur de ressources de stockage (SRP).
seo-description: As of AEM Communities 6.1, user generated content (UGC) is stored in a single, common store provided by a storage resource provider (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Admin
exl-id: 4ff530ae-c676-4259-86f2-a3881843b642
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# SRP - Stockage de contenu de la communauté {#srp-community-content-storage}

## Présentation {#introduction}

Depuis AEM Communities 6.1, le contenu généré par l’utilisateur est stocké dans un seul magasin commun fourni par un fournisseur de ressources de stockage (SRP). Il existe plusieurs options de SRP que vous pouvez sélectionner, telles que ASRP, MSRP et JSRP.

Contrairement aux versions précédentes, il n’existe pas de réplication inverse/transfert du contenu créé par l’utilisateur entre les instances AEM. Au lieu de cela, la SRP rend le contenu créé par l’utilisateur directement accessible pour les opérations CRUD (création, lecture, mise à jour et suppression) de toutes les instances d’auteur et de publication, à l’exception de JSRP.

Voici les [caractéristiques de chaque option de SRP](#characteristics-of-srp-options), qui est une information essentielle au processus de décision lors du choix de la SRP appropriée et [déploiement sous-jacent](topologies.md).

Pour plus d’informations sur l’utilisation de la SRP pour le contenu généré par l’utilisateur, voir [Présentation du fournisseur de ressources de stockage](srp.md).

>[!NOTE]
>
>La SRP s’applique uniquement au contenu de la communauté. Cela n’a aucune incidence sur l’emplacement de stockage du contenu du site ([magasin de noeuds](../../help/sites-deploying/data-store-config.md)) et n’a aucune incidence sur la gestion sécurisée de l’enregistrement des utilisateurs, des profils utilisateur et des groupes d’utilisateurs entre les instances AEM (voir aussi [Gestion des données utilisateur](#managing-user-data)).

>[!CAUTION]
>
>À partir de la version AEM 6.1, [Le contenu généré par l’utilisateur n’est jamais répliqué.](#ugc-never-replicated).
>
>Lorsque le déploiement n’inclut pas de magasin commun, tel que la valeur par défaut [JSRP](topologies.md#jsrp) topologie, le contenu généré par l’utilisateur ne sera visible que sur l’instance de publication ou d’auteur AEM sur laquelle il a été saisi. Ce n’est que si la topologie inclut une grappe de publication que le contenu généré par l’utilisateur sera visible sur n’importe quelle instance de publication.

## Caractéristiques des options SRP {#characteristics-of-srp-options}

[ASRP - Fournisseur de ressources de stockage d’Adobe](asrp.md)\
Avec cette option, le contenu créé par l’utilisateur est conservé à distance dans un service cloud hébergé et géré par Adobe. Il nécessite une licence supplémentaire et l’utilisation d’un gestionnaire de compte pour configurer le compte pour cette licence spécifique.

* Nécessite un service cloud associé fourni et pris en charge par Adobe pour stocker le contenu de la communauté
* Nécessite le choix d’un centre de données dans une zone géographique spécifique (États-Unis, EMEA, APAC)
* Nécessite tout accès programmatique au contenu généré par l’utilisateur via l’API SRP
* Adaptable à la ferme de publication TarMK
* Convient lorsqu’il n’y a aucune intention d’investir dans le stockage local

>[!NOTE]
>
>Le téléchargement des pièces jointes aux publications (ou commentaires) dans ASRP est limité à 50 Mo.

[MSRP - Fournisseur de ressources de stockage MongoDB](msrp.md)\
Avec cette option, le contenu généré par l’utilisateur est conservé directement dans une instance MongoDB locale.

* Nécessite une installation locale sous licence de MongoDB pour stocker le contenu de la communauté
* Nécessite une installation locale d’Apache Solr
* Nécessite tout accès programmatique au contenu généré par l’utilisateur via l’API SRP
* Adaptable à une ferme de publication TarMK existante
* Adapté à un cluster MongoMK ou RdbMK
* Adaptable lorsque vous attendez de gros volumes de contenu de communauté

[DSRP - Fournisseur de ressources de stockage de la base de données relationnelle](dsrp.md)\
Avec cette option, le contenu généré par l’utilisateur est conservé directement dans une instance de base de données MySQL locale.

* Nécessite une installation locale de MySQL pour stocker le contenu de la communauté
* Nécessite une installation locale d’Apache Solr
* Nécessite tout accès programmatique au contenu généré par l’utilisateur via l’API SRP
* Adaptable à une ferme de publication TarMK existante
* Adapté à un cluster MongoMK ou RdbMK
* Adaptable lorsque vous attendez de gros volumes de contenu de communauté

[JSRP - Fournisseur de ressources de stockage JCR](jsrp.md)\
Avec l’option par défaut, il n’y a pas de boutique courante. Le contenu généré par l’utilisateur n’est conservé que dans le même référentiel JCR que l’instance AEM dans laquelle il a été saisi.

* Stocke le contenu de la communauté dans le référentiel JCR de l’instance d’auteur ou de publication AEM à laquelle il a été publié.
* Nécessite tout accès programmatique au contenu généré par l’utilisateur via l’API SRP
* Nécessite une grappe de publication si plusieurs instances de publication sont déployées (il n’existe pas de mécanisme de réplication entre les instances de publication dans une ferme TarMK).
* La modération est effectuée uniquement dans l’environnement de publication (il n’existe pas de mécanisme de réplication inverse/transfert entre l’auteur et la publication).
* Généralement meilleur pour le développement, les démonstrations et la formation

## Configuration de la SRP {#configuring-srp}

La spécification de l’option de stockage par défaut, en fonction du déploiement sous-jacent, est effectuée par l’intermédiaire de la variable [Console de configuration de stockage](srp-config.md).

Pour plus d’informations sur la configuration de chaque option, voir :

* [ASRP - Fournisseur de ressources de stockage d’Adobe](asrp.md)
* [MSRP - Fournisseur de ressources de stockage MongoDB](msrp.md)
* [DSRP - Fournisseur de ressources de stockage de la base de données relationnelle](dsrp.md)
* [JSRP - Fournisseur de ressources de stockage JCR](jsrp.md)

Si aucune option de stockage n’est activement sélectionnée, JSRP est activé par défaut.

## Informations supplémentaires {#additional-information}

### UGC jamais répliqué {#ugc-never-replicated}

Dans l’environnement de création, un auteur crée du contenu de page et le réplique dans l’environnement de publication. Lorsqu’une page comprend une fonction AEM Communities interactive (commentaires, révisions, forum, blog ou Q&amp;R, par exemple), l’interaction des membres (connectés aux visiteurs du site) sur une instance de publication génère du contenu généré par l’utilisateur (UGC) entré dans l’environnement de publication.

Auparavant, ce contenu de communauté était répliqué par inverse vers les instances d’auteur et répliqué par l’auteur vers les instances de publication. Il était problématique de maintenir la cohérence entre les instances AEM avec la réplication inverse et vers l’avant.

À partir d’AEM Communities 6.1, le besoin de réplication du contenu créé par l’utilisateur a été éliminé en utilisant le stockage partagé pour le contenu créé par l’utilisateur, comme décrit ci-dessus.

Bien que le contenu du site soit répliqué, le contenu généré par l’utilisateur n’est jamais répliqué.

### Gestion des données utilisateur {#managing-user-data}

Ce qui intéresse aussi les communautés [*utilisateurs*, *groupes d’utilisateurs*, et *profils utilisateur*](users.md). Ces données liées à l’utilisateur, lorsqu’elles sont créées et mises à jour dans l’environnement de publication, doivent être mises à la disposition d’autres instances de publication lorsque la topologie est une [batterie de publication](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

Depuis AEM Communities 6.1, les données liées à l’utilisateur sont synchronisées à l’aide de la distribution Sling plutôt que de la réplication. Pour plus d’informations, voir [Synchronisation des utilisateurs](sync.md).

### Mise à niveau vers AEM Communities 6.2 {#upgrading-to-aem-communities}

Lors de la mise à niveau vers AEM Communities 6.3, si le contenu créé par l’utilisateur préexistant doit être conservé, des étapes doivent être prises selon que la communauté AEM 5.6.1 ou AEM 6.0 a utilisé le stockage Adobe à la demande ou le stockage on-premise du contenu créé par l’utilisateur.

Pour plus d’informations, rendez-vous sur [Mise à niveau vers AEM Communities 6.3](upgrade.md).
