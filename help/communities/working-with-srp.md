---
title: SRP - Enregistrement de contenu communautaire
seo-title: SRP - Enregistrement de contenu communautaire
description: Depuis AEM Communities 6.1, le contenu généré par l’utilisateur est stocké dans un seul magasin commun fourni par un fournisseur de ressources d’enregistrement (SRP).
seo-description: Depuis AEM Communities 6.1, le contenu généré par l’utilisateur est stocké dans un seul magasin commun fourni par un fournisseur de ressources d’enregistrement (SRP).
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---


# SRP - Enregistrement de contenu communautaire {#srp-community-content-storage}

## Présentation {#introduction}

Depuis AEM Communities 6.1, le contenu généré par l’utilisateur est stocké dans un seul magasin commun fourni par un fournisseur de ressources d’enregistrement (SRP). Il existe plusieurs options SRP à partir desquelles choisir, telles que ASRP, MSRP et JSRP.

Contrairement aux versions précédentes, il n’existe pas de réplication inverse/avancée de l’UGC entre les instances AEM. Au lieu de cela, le protocole SRP rend l’UGC directement accessible pour créer, lire, mettre à jour et supprimer des opérations CRUD de toutes les instances d’auteur et de publication, à l’exception de JSRP.

Vous trouverez ci-dessous les [caractéristiques de chaque option](#characteristics-of-srp-options)de PRS, qui est une information cruciale pour le processus décisionnel lors du choix du PRS approprié et du déploiement [](topologies.md)sous-jacent.

Pour plus d&#39;informations sur l&#39;utilisation de SRP pour UGC, consultez Présentation [des fournisseurs de ressources](srp.md)d&#39;Enregistrement.

>[!NOTE]
>
>SRP s&#39;applique uniquement au contenu de la communauté. Elle n’affecte pas l’emplacement de stockage du contenu du site (magasin[de](../../help/sites-deploying/data-store-config.md)noeuds) et n’affecte pas la gestion sécurisée de l’enregistrement des utilisateurs, des profils d’utilisateurs et des groupes d’utilisateurs entre les instances d’AEM (voir également [Gestion des données](#managing-user-data)utilisateur).

>[!CAUTION]
>
>À partir de AEM 6.1, [UGC n&#39;est jamais répliqué](#ugc-never-replicated).
>
>Lorsque le déploiement n’inclut pas de magasin commun, tel que la topologie [JSRP](topologies.md#jsrp) par défaut, l’UGC n’est visible que sur l’instance de publication ou d’auteur AEM sur laquelle il a été saisi. Ce n’est que si la topologie inclut une grappe de publication que l’UGC sera visible sur toute instance de publication.

## Caractéristiques des options SRP {#characteristics-of-srp-options}

[ASRP - Fournisseur de ressources d&#39;Enregistrement d&#39;Adobe](asrp.md)\
Avec cette option, l’UGC est conservé à distance dans un service cloud hébergé et géré par Adobe. Il nécessite une licence supplémentaire et travaille avec un gestionnaire de compte pour configurer le compte pour cette licence spécifique.

* Nécessite un service cloud associé fourni et pris en charge par l’Adobe pour stocker le contenu de la communauté
* Nécessite le choix d&#39;un centre de données dans une zone géographique spécifique (Etats-Unis, EMEA, APAC)
* Nécessite l&#39;accès programmatique à l&#39;UGC par le biais de l&#39;API SRP
* Adapté à la batterie de publication TarMK
* Approprié lorsqu&#39;il n&#39;y a pas d&#39;intention d&#39;investir dans l&#39;enregistrement local

>[!NOTE]
>
>Le téléchargement des pièces jointes aux publications (ou commentaires) dans ASRP est limité à 50 Mo.

[MSRP - Fournisseur de ressources d&#39;Enregistrement MongoDB](msrp.md)\
Avec cette option, l’UGC est conservé directement dans une instance MongoDB locale.

* Nécessite une installation locale sous licence de MongoDB pour stocker le contenu de la communauté
* Nécessite une installation locale d&#39;Apache Solr
* Nécessite l&#39;accès programmatique à l&#39;UGC par le biais de l&#39;API SRP
* Adapté à une batterie de publication TarMK existante
* Adapté à un cluster MongoMK ou RdbMK
* Convient lorsque vous attendez de gros volumes de contenu de la communauté

[DSRP - Fournisseur de ressources d&#39;Enregistrement de données relationnelles](dsrp.md)\
Avec cette option, l’UGC est conservé directement dans une instance de base de données MySQL locale.

* Nécessite une installation locale de MySQL pour stocker le contenu de la communauté
* Nécessite une installation locale d&#39;Apache Solr
* Nécessite l&#39;accès programmatique à l&#39;UGC par le biais de l&#39;API SRP
* Adapté à une batterie de publication TarMK existante
* Adapté à un cluster MongoMK ou RdbMK
* Convient lorsque vous attendez de gros volumes de contenu de la communauté

[JSRP - Fournisseur de ressources d’Enregistrement JCR](jsrp.md)\
Avec l’option par défaut, il n’existe pas de magasin commun. L’UGC n’est conservé que dans le même référentiel JCR que l’instance AEM dans laquelle il a été entré.

* Stocke le contenu de la communauté dans le référentiel JCR de l’instance d’auteur ou de publication AEM à laquelle il a été publié.
* Nécessite l&#39;accès programmatique à l&#39;UGC par le biais de l&#39;API SRP
* Nécessite une grappe de publication si plusieurs instances de publication sont déployées (il n’existe aucun mécanisme de réplication parmi les instances de publication dans une batterie TarMK)
* La modération est exécutée uniquement dans l’environnement de publication (il n’existe aucun mécanisme de réplication inverse/transfert entre l’auteur et la publication).
* Généralement le meilleur pour le développement, les démonstrations et la formation

## Configuration de SRP {#configuring-srp}

La spécification de l’option d’enregistrement par défaut, en fonction du déploiement sous-jacent, est effectuée via la console [Configuration de l’](srp-config.md)Enregistrement.

Pour plus d&#39;informations sur la configuration de chaque option, voir :

* [ASRP - Fournisseur de ressources d&#39;Enregistrement d&#39;Adobe](asrp.md)
* [MSRP - Fournisseur de ressources d&#39;Enregistrement MongoDB](msrp.md)
* [DSRP - Fournisseur de ressources d&#39;Enregistrement de données relationnelles](dsrp.md)
* [JSRP - Fournisseur de ressources d’Enregistrement JCR](jsrp.md)

Si aucune option d’enregistrement n’est activement sélectionnée, JSRP est activé par défaut.

## Informations supplémentaires {#additional-information}

### UGC jamais répliqué {#ugc-never-replicated}

Dans l’environnement d’auteur, un auteur crée du contenu de page et le répliquera dans l’environnement de publication. Lorsqu’une page comprend une fonction d’AEM Communities interactive, telle que des commentaires, des révisions, un forum, un blog ou une QnA, l’interaction des membres (connectés en visiteurs de site) sur une instance de publication génère l’entrée de contenu généré par l’utilisateur dans l’environnement de publication.

Auparavant, ce contenu de la communauté était répliqué de manière inversée aux instances d’auteur et répliqué par l’auteur aux instances de publication. Il était problématique de maintenir la cohérence entre les instances AEM avec la réplication inverse et à terme.

À partir de AEM Communities 6.1, la nécessité de reproduire le CU a été éliminée en utilisant l&#39;enregistrement partagé pour le CU, comme indiqué ci-dessus.

Bien que le contenu du site soit répliqué, l’UGC n’est jamais répliqué.

### Gestion des données utilisateur {#managing-user-data}

Les communautés s’intéressent également aux [*utilisateurs *, aux groupes* d’*utilisateurs et aux profils* d’*](users.md)utilisateurs. Une fois créées et mises à jour dans l’environnement de publication, ces données utilisateur doivent être mises à la disposition d’autres instances de publication lorsque la topologie est une batterie de[publication](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

Depuis AEM Communities 6.1, les données relatives aux utilisateurs sont synchronisées à l’aide de la distribution Sling plutôt que de la réplication. Pour plus d’informations, consultez la section Synchronisation [des](sync.md)utilisateurs.

### Upgrading to AEM Communities 6.2 {#upgrading-to-aem-communities}

Lors de la mise à niveau vers AEM Communities 6.3, si des CU préexistants doivent être conservés, des mesures doivent être prises selon que la communauté AEM 5.6.1 ou AEM 6.0 a utilisé l&#39;enregistrement à la demande de l&#39;Adobe ou l&#39;enregistrement local de CU.

Pour plus d’informations, consultez [Mise à niveau vers AEM Communities 6.3](upgrade.md).
