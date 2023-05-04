---
title: Outil de migration CRX2OAK
seo-title: CRX2OAK Migration Tool
description: Notes de mise à jour spécifiques à l’outil de migration CRX2OAK d’Adobe Experience Manager 6.4.
seo-description: Release notes specific to the Adobe Experience Manager 6.4 CRX2OAK Migration tool.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
exl-id: 441c8ba0-f8b2-4c2c-b7be-cfdad9e1e498
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# Outil de migration CRX2OAK {#crx-oak-migration-tool}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Liste des modifications et correctifs {#list-of-changes-and-fixes}

### 1.8.6 (juin 2018) {#june}

* OAK-7339 Correction de toutes les ruptures avec UnsupportedOperationException sur MissingBlobStore en introduisant LoopbackBlobStore
* Utilisation d’Oak 1.8.4

### 1.8.4 (avril 2018) {#april}

* Utilisation d’Oak version 1.8.2
* GRANITE-18104 L’erreur de migration de Repo de 6.3 à 6.4 doit être plus significative
* GRANITE-16571 Remplacer l’utilisation de SHA-1

   * La somme de contrôle de l’outil est désormais SHA-512 lors de l’utilisation de l’option —version

* GRANITE-17601 Incorporer oak-upgrade dans CRX2Oak avec oak-blob-cloud
* GRANITE-18553 crx2oak laisse les propriétés de version sur le noeud même lorsque les versions ne sont pas migrées.

### Version 1.6.8 (mars 2017) {#version-march}

* Mise à jour de la version Oak vers la version 1.6.1
* CQ-61847 Fusionner crx2oak-quickstart-extension avec crx2oak (profils de migration ajoutés)
* CQ-97488 Promotion et suppression des modes d’exécution AEM (en réécrivant sling.options.file)
* GRANITE-12798/OAK-4260 Possibilité de passer d’un segment Oak à un segment Oak Tar

### Version 1.4.2 (mars 2016) {#version-march-1}

* Mise à niveau de la version Oak vers la version 1.4.1
* OAK-3846 / GRANITE-10748 Renommer les noeuds SNS s’ils enfreignent des contraintes de type de noeud
* OAK-3910 / GRANITE-10730 Migration du noeud héritant de `mix:versionable` sans historique de version
* OAK-4128 / GRANITE-11757 `RepositorySidegrade` ne copie pas les propriétés du noeud racine

### Version 1.3.4 (janvier 2016) {#version-january}

* Mise à niveau d’Oak vers la version 1.3.16
* OAK-3844 / GRANITE-10730 Meilleure prise en charge des noeuds versionnables sans historique des versions
* OAK-3846 Renommer les noeuds SNS s’ils ne respectent pas les contraintes de type de noeud

### Version 1.3.2 (décembre 2015) {#version-december}

* Mises à niveau de la version Oak vers la version 1.3.12
* Le répertoire de la banque de données ne doit pas être déplacé après la migration (GRANITE-10447)
* Fusion de crx2oak-quickstart-extension avec crx2oak (CQ-61847)
* Échec de crx2oak sur les valeurs en double dans le référentiel (CQ-61906)
* Démarrage AEM long après la migration à partir de CQ 5.x (GRANITE-10309)
* Prise en charge de plusieurs serveurs LDAP dans crx2oak (GRANITE-9917)
* Imposer la vérification de la longueur maximale du nom de noeud (OAK-3111)
* Prise en charge de S3DataSource comme source de migration (OAK-3685)
