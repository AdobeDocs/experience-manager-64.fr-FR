---
title: Outil de migration CRX2OAK
seo-title: Outil de migration CRX2OAK
description: Notes de mise à jour spécifiques à l’outil de migration CRX2OAK d’Adobe Experience Manager 6.4.
seo-description: Notes de mise à jour spécifiques à l’outil de migration CRX2OAK d’Adobe Experience Manager 6.4.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 66%

---


# Outil de migration CRX2OAK {#crx-oak-migration-tool}

## Liste des modifications et des corrections {#list-of-changes-and-fixes}

### 1.8.6 (juin 2018) {#june}

* OAK-7339 Correction de la rupture de toutes les versions secondaires avec UnsupportedOperationException sur MissingBlobStore en introduisant LoopbackBlobStore
* Utiliser Oak 1.8.4

### 1.8.4 (avril 2018) {#april}

* Utiliser Oak version 1.8.2
* GRANITE-18104 L&#39;erreur de migration de rebol de 6.3 à 6.4 doit être plus significative
* GRANITE-16571 Remplacer l’utilisation de SHA-1

   * La somme de contrôle de l&#39;outil est désormais SHA-512 lors de l&#39;utilisation de l&#39;option —version

* GRANITE-17601 Incorporer la mise à niveau du chêne dans CRX2Oak avec le chêne-blob-cloud
* GRANITE-18553 crx2oak laisse les propriétés de version sur le noeud même lorsque les versions ne sont pas migrées

### Version 1.6.8 (mars 2017) {#version-march}

* Passage à la version 1.6.1 d’Oak
* CQ-61847 Fusionner crx2oak-quickstart-extension avec crx2oak (profils de migration ajoutés)
* CQ-97488 Promotion et suppression des modes d’exécution d’AEM (en réécrivant sling.options.file)
* GRANITE-12798/OAK-4260 Capacité à évaluer de côté le segment de chêne au goudron de segment de chêne

### Version 1.4.2 (mars 2016) {#version-march-1}

* Mise à niveau de Oak vers la version 1.4.1
* OAK-3846 / GRANITE-10748 Nœuds SNS qui ne respectent pas les contraintes liées au type de nœud renommés
* OAK-3910 /GRANITE-10730 Migration des nœuds hérités de `mix:versionable` sans historique des versions
* OAK-4128 / GRANITE-11757 `RepositorySidegrade` ne copie pas les propriétés du noeud racine

### Version 1.3.4 (janvier 2016) {#version-january}

* Mise à niveau de Oak vers la version 1.3.16
* OAK-3844 / GRANITE-10730 Meilleure prise en charge des nœuds versionnables sans historique des versions
* OAK-3846 Nœuds SNS qui ne respectent pas les contraintes liées au type de nœud renommés

### Version 1.3.2 (décembre 2015) {#version-december}

* Mises à niveau de Oak vers la version 1.3.12
* Ne pas déplacer le répertoire de la banque de données après la migration (GRANITE-10447)
* Fusion de crx2oak-quickstart-extension avec crx2oak (CQ-61847)
* Échec de crx2oak sur les valeurs en double dans le référentiel (CQ-61906)
* Démarrage lent d’AEM après la migration de CQ 5.x (GRANITE-10309)
* Prise en charge de plusieurs serveurs LDAP dans crx2oak (GRANITE-9917)
* Mise en œuvre du contrôle de la longueur maximale des noms de nœuds (OAK-3111)
* Prise en charge de S3DataSource comme source de migration (OAK-3685)
