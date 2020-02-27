---
title: Purge de version
seo-title: Purge de version
description: Cet article décrit les options disponibles pour la purge de version.
seo-description: Cet article décrit les options disponibles pour la purge de version.
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
translation-type: tm+mt
source-git-commit: 510b6765e11a5b3238407322d847745f09183d63

---


# Purge de version{#version-purging}

Durant l’installation standard, AEM crée une version de page ou de nœud lorsque la page est activée après la mise à jour du contenu. 

>[!NOTE]
>
>Si aucune modification de contenu n’est effectuée, vous verrez un message affirmant que la page a été activée, cependant aucune nouvelle version ne sera créée.

Vous pouvez créer des versions supplémentaires sur demande à l’aide de l’onglet **Versions** du sidekick. Ces versions sont stockées dans le référentiel et peuvent être restaurées si nécessaire. 

Ces versions n’étant jamais purgées, la taille du référentiel va continuer d’augmenter et devra être gérée.

AEM est livré avec divers mécanismes vous permettant de gérer le référentiel :

* Gestionnaire de [versions](#version-manager)

   Vous pouvez configurer cette option pour purger les anciennes versions lors de la création de nouvelles versions.

* l’outil [Purger les versions](/help/sites-deploying/monitoring-and-maintaining.md#version-purging)

   Il est utilisé dans le cadre de la surveillance et de la maintenance de votre référentiel.

    Il vous permet d’intervenir et de supprimer les anciennes versions d’un nœud ou d’une hiérarchie de nœuds, en fonction des paramètres suivants :

   * Le nombre maximal de versions à conserver dans le référentiel.

      Une fois ce nombre dépassé, la version la plus ancienne est supprimée.

   * L’âge maximal des versions conservées dans le référentiel. 

       Lorsque l’âge d’une version dépasse cette valeur, elle est purgée du référentiel. 

* the [Version Purge maintenance task](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Vous pouvez planifier la tâche de maintenance Purge de version pour supprimer automatiquement les anciennes versions. Par conséquent, cela minimise la nécessité d’utiliser manuellement les outils de purge de version.

>[!CAUTION]
>
>Pour optimiser la taille du référentiel, vous devez exécuter la tâche Purge de version fréquemment. La tâche doit être planifiée en dehors des heures de bureau lorsque le trafic est limité.

## Gestionnaire de versions {#version-manager}

En plus de la purge explicite via l’outil de purge, le gestionnaire de version peut être configuré pour purger d’anciennes versions lorsque de nouvelles versions sont créées.

Pour installer le gestionnaire de version, créez une configuration pour :

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Les options suivantes sont disponibles :

* `versionmanager.createVersionOnActivation` (Boolean, par défaut : true)

   si vous souhaitez créer une version lorsque des pages sont activées.

   Une version est créée, sauf si l’agent de réplication est configuré pour supprimer la création de versions, qui est honorée par le Gestionnaire de versions

   Une version est créée uniquement si l’activation a lieu sur un chemin contenu dans versionmanager.ivPaths (voir ci-dessous).

* `versionmanager.ivPaths` (Chaîne[], valeur par défaut : {&quot;/&quot;})

   chemins d’accès sur lesquels les versions sont implicitement créées lors de l’activation si versionmanager.createVersionOnActivation est vrai.

* `versionmanager.purgingEnabled` (Boolean, par défaut : false)

   activation ou non de la purge lors de la création de nouvelles versions

* `versionmanager.purgePaths` (Chaîne[], valeur par défaut : {&quot;/content&quot;})

   chemins vers lesquels purger les versions lors de la création de nouvelles versions.

* `versionmanager.maxAgeDays` (int, valeur par défaut : 30)

   lors de la purge, toute version antérieure à cette valeur sera supprimée. Si cette valeur est inférieure à 1, la purge n’est pas effectuée en fonction de l’âge de la version

* `versionmanager.maxNumberVersions` (int, 5 par défaut)

   lors de la purge, toute version antérieure à la n-ième version sera supprimée. Si cette valeur est inférieure à 1, la purge n’est pas effectuée en fonction du nombre de versions.

* `versionmanager.minNumberVersions` (int, 0 par défaut)

   Nombre minimum de versions à conserver, quel que soit l’âge. Si cette valeur est définie sur une valeur inférieure à 1, aucun nombre minimum de versions n’est conservé.

>[!NOTE]
>
>Il n’est pas recommandé de conserver un grand nombre de versions dans le référentiel. Par conséquent, lors de la configuration de l’opération de purge de version, veillez à ne pas exclure un trop grand nombre de versions de la purge, faute de quoi la taille du référentiel ne sera pas correctement optimisée. Si vous conservez un grand nombre de versions en raison d’un besoin professionnel, contactez le service d’assistance d’Adobe pour trouver d’autres moyens d’optimiser la taille du référentiel.

### Combinaison d’options de conservation {#combining-retention-options}

The options defining how which versions should be retained ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), can be combined depending on your requirements.

Par exemple, en définissant le nombre maximum de versions à conserver ET la version la plus ancienne à conserver :

* paramètre :

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* Avec :

   * 10 versions créées dans les 60 derniers jours
   * 3 de ces versions créées dans les 30 derniers jours 

* Ce qui signifie que :

   * les 3 dernières versions seront conservées 

Par exemple, en définissant les nombres maximum ET minimum de versions à conserver ET la version la plus ancienne à conserver :

* paramètre :

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Avec :

   * 5 versions créées il y a 60 jours

* Ce qui signifie que :

   * 3 versions seront conservées

## Outil de purge des versions {#purge-versions-tool}

L’outil [Purge de versions](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) est prévu pour la purge des versions d’un nœud ou d’une hiérarchie de nœuds dans votre référentiel. Son principal objectif est de vous aider à réduire la taille du référentiel en supprimant les anciennes versions de vos nœuds. 
