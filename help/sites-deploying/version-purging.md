---
title: Purge de version
seo-title: Version Purging
description: Cet article décrit les options disponibles pour la purge de version.
seo-description: This article describes the available options for version purging.
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
feature: Configuring
exl-id: 357d5f23-3e75-44e3-905f-4efe960858bf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 27%

---

# Purge de version{#version-purging}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Dans une installation standard, AEM crée une nouvelle version d’une page ou d’un noeud lorsque vous activez une page après la mise à jour du contenu.

>[!NOTE]
>
>Si aucune modification du contenu n’est apportée, un message s’affiche indiquant que la page a été activée, mais qu’aucune nouvelle version ne sera créée.

Vous pouvez créer des versions supplémentaires sur demande à l’aide de la méthode **Contrôle de version** de l’onglet du sidekick. Ces versions sont stockées dans le référentiel et peuvent être restaurées si nécessaire.

Ces versions ne sont jamais purgées. Par conséquent, la taille du référentiel va augmenter au fil du temps et doit donc être gérée.

AEM est fourni avec divers mécanismes pour vous aider à gérer votre référentiel :

* la valeur [Version Manager](#version-manager)

   Il peut être configuré pour purger les anciennes versions lors de la création de nouvelles versions.

* la valeur [Purge des versions](/help/sites-deploying/monitoring-and-maintaining.md#version-purging) outil

   Il est utilisé dans le cadre de la surveillance et de la maintenance de votre référentiel.

   Il vous permet d’intervenir et de supprimer les anciennes versions d’un nœud ou d’une hiérarchie de nœuds, en fonction des paramètres suivants :

   * Le nombre maximal de versions à conserver dans le référentiel.

      Une fois ce nombre dépassé, la version la plus ancienne est supprimée.

   * L’âge maximal des versions conservées dans le référentiel.
 

      Lorsque l’âge d’une version dépasse cette valeur, elle est purgée du référentiel. 

* La [tâche de maintenance Purge de version](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Vous pouvez planifier la tâche de maintenance Purge de version pour supprimer automatiquement les anciennes versions. Ainsi, cela réduit la nécessité d’utiliser manuellement les outils de purge de version.

>[!CAUTION]
>
>Pour optimiser la taille du référentiel, vous devez exécuter la tâche Purge de version fréquemment. La tâche doit être planifiée en dehors des heures de bureau lorsqu’il y a un trafic limité.

## Version Manager {#version-manager}

Outre la purge explicite au moyen de l’outil de purge, le gestionnaire de versions peut être configuré pour purger les anciennes versions lors de la création de nouvelles versions.

Pour installer le gestionnaire de versions, créez une configuration pour :

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Les options suivantes sont disponibles :

* `versionmanager.createVersionOnActivation` (booléen, valeur par défaut : true)

   si vous souhaitez créer une version lorsque des pages sont activées.

   Une version est créée, sauf si l’agent de réplication est configuré pour supprimer la création de versions, qui est honorée par le gestionnaire de versions.

   Une version n’est créée que si l’activation se produit sur un chemin contenu dans versionmanager.ivPaths (voir ci-dessous).

* `versionmanager.ivPaths` (Chaîne)[], par défaut : {&quot;/&quot;})

   chemins d’accès sur lesquels les versions sont implicitement créées lors de l’activation si versionmanager.createVersionOnActivation a la valeur true.

* `versionmanager.purgingEnabled` (booléen, valeur par défaut : false)

   l’activation ou non de la purge lors de la création de nouvelles versions

* `versionmanager.purgePaths` (Chaîne)[], par défaut : {&quot;/content&quot;})

   sur les chemins d’accès pour purger les versions lors de la création de nouvelles versions.

* `versionmanager.maxAgeDays` (int, valeur par défaut : 30)

   lors de la purge, toute version antérieure à cette valeur est supprimée. Si cette valeur est inférieure à 1, la purge n’est pas effectuée en fonction de l’âge de la version.

* `versionmanager.maxNumberVersions` (int, valeur par défaut 5)

   lors de la purge, toute version antérieure à la n dernière version est supprimée. Si cette valeur est inférieure à 1, la purge n’est pas effectuée en fonction du nombre de versions.

* `versionmanager.minNumberVersions` (int, 0 par défaut)

   Nombre minimum de versions à conserver, indépendamment de l’âge. Si cette valeur est définie sur une valeur inférieure à 1, aucun nombre minimum de versions n’est conservé.

>[!NOTE]
>
>Il n’est pas recommandé de conserver un grand nombre de versions dans le référentiel. Par conséquent, lors de la configuration de l’opération de purge de version, veillez à ne pas exclure un trop grand nombre de versions de la purge, faute de quoi la taille du référentiel ne sera pas correctement optimisée. Si vous conservez un grand nombre de versions en raison de besoins de l’entreprise, contactez l’assistance Adobe pour trouver d’autres moyens d’optimiser la taille du référentiel.

### Combinaison d’options de conservation {#combining-retention-options}

Les options qui définissent la manière dont les versions doivent être conservées (`maxAgeDays`, `maxNumberVersions`, `minNumberVersions`) peuvent être combinées en fonction de vos besoins.

Par exemple, lors de la définition du nombre maximal de versions à conserver ET de la version la plus ancienne à conserver :

* Configuration :

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* Avec :

   * 10 versions créées au cours des 60 derniers jours
   * 3 de ces versions créées au cours des 30 derniers jours

* Cela signifie que :

   * Les 3 dernières versions seront conservées.

Par exemple, lors de la définition du nombre maximal ET minimum de versions à conserver ET de la version la plus ancienne à conserver :

* Configuration :

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Avec :

   * 5 versions créées il y a 60 jours

* Cela signifie que :

   * 3 versions seront conservées

## Outil Purge des versions {#purge-versions-tool}

Le [Purge des versions](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) est destiné à purger les versions d’un noeud ou d’une hiérarchie de noeuds dans votre référentiel. Son Principal objectif est de vous aider à réduire la taille de votre référentiel en supprimant les anciennes versions de vos noeuds.
