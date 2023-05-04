---
title: Vérifications et dépannage après une mise à niveau
seo-title: Post Upgrade Checks and Troubleshooting
description: Découvrez comment résoudre les problèmes qui peuvent apparaître après une mise à niveau.
seo-description: Learn how to troubleshoot issues that might appear after an upgrade.
uuid: 3f83e8fc-1c45-4ef0-b8da-d29ff483d3d5
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: bc8c9aa2-f669-41f3-a526-6146ff5cf0cd
feature: Upgrading
exl-id: edd6e933-59ed-4d7e-8934-7e2ec485cfb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 27%

---

# Vérifications et dépannage après une mise à niveau{#post-upgrade-checks-and-troubleshooting}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Vérifications après mise à niveau {#post-upgrade-checks}

En procédant comme suit : [Mise à niveau statique](/help/sites-deploying/in-place-upgrade.md) les activités suivantes doivent être exécutées pour finaliser l&#39;upgrade. On suppose que AEM a été démarré avec le jar 6.4 et que la base de code mise à niveau a été déployée.

* [Vérification des journaux pour la réussite de la mise à niveau](#verify-logs-for-upgrade-success)

* [Vérification des lots OSGi](#verify-osgi-bundles)

* [Vérification de la version Oak](#verify-oak-version)

* [Inspection de dossier PreUpgradeBackup](#inspect-preupgradebackup-folder)

* [Validation initiale des pages](#initial-validation-of-pages)
* [Application de packs de service AEM](#apply-aem-service-packs)

* [Migration des fonctionnalités AEM](#migrate-aem-features)

* [Vérification des configurations de maintenance planifiées](#verify-scheduled-maintenance-configurations)

* [Activation des agents de réplication](#enable-replication-agents)

* [Activation des tâches planifiées personnalisées](#enable-custom-scheduled-jobs)

* [Exécution du plan de test](#execute-test-plan)

### Vérification des journaux pour la réussite de la mise à niveau {#verify-logs-for-upgrade-success}

**upgrade.log**

Auparavant, la vérification de l’état de votre instance après la mise à niveau nécessitait une inspection minutieuse de divers fichiers journaux, de parties du référentiel et du pavé de lancement. La génération d’un rapport après la mise à niveau peut aider à détecter les mises à niveau défectueuses avant la mise en service.

L’objectif principal de cette fonctionnalité est de réduire la nécessité d’une interprétation manuelle ou d’une logique d’analyse complexe sur plusieurs points de terminaison requis pour que la mise à niveau soit réussie. La solution vise à fournir des informations non ambiguës pour que les systèmes d’automatisation externes réagissent au succès ou à l’échec identifié d’une mise à jour.

Plus précisément, il garantit que :

* Les échecs de mise à niveau détectés par la structure de mise à niveau peuvent être centralisés dans un seul rapport de mise à niveau ;
* Le rapport de mise à niveau comprend des indicateurs sur l’intervention manuelle nécessaire.

Pour cela, les modifications ont été apportées à la façon dont les journaux sont générés dans le fichier `upgrade.log`.

Voici un exemple de rapport n’affichant aucune erreur lors de la mise à niveau :

![1487887443006](assets/1487887443006.png)

Voici un exemple de rapport affichant un lot n’ayant pas été installé lors de la mise à niveau : 

![1487887532730](assets/1487887532730.png)

**error.log**

Le fichier error.log doit être soigneusement examiné pendant et après le démarrage de l’AEM à l’aide du fichier jar de la version cible. Les avertissements ou erreurs doivent être examinés. En général, il est préférable de rechercher les problèmes au début du journal. Les erreurs qui se produisent plus tard dans le journal peuvent être des effets secondaires d’une cause racine appelée plus tôt dans le fichier. En cas d’erreurs répétées et d’avertissements, reportez-vous à la section ci-dessous pour [Analyse des problèmes liés à la mise à niveau](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-upgrade).

### Vérification des lots OSGi {#verify-osgi-bundles}

Accédez à la console OSGi `/system/console/bundles` et vérifiez si des lots n’ont pas démarré. Si des lots sont installés, consultez le fichier `error.log` pour identifier le problème racine.

### Vérification de la version Oak {#verify-oak-version}

Après la mise à niveau, vous devez constater qu’Oak a été mis à jour vers la version **1.8.2**. Pour vérifier la version Oak, accédez à la console OSGi et inspectez la version associée aux lots Oak : Oak Core, Oak Commons, Oak Segment Tar.

### Inspection du dossier PreUpgradeBackup {#inspect-preupgradebackup-folder}

Pendant la mise à niveau, AEM essaiera de sauvegarder les personnalisations et de les stocker sous `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>`. Pour afficher ce dossier dans CRXDE Lite, vous avez peut-être besoin d’[activer temporairement CRXDE Lite](/help/sites-administering/enabling-crxde-lite.md).

Le dossier avec l’horodatage doit posséder une propriété nommée `mergeStatus` avec la valeur `COMPLETED`. Le **to-process** Le dossier doit être vide et la variable **écrasé** indique les noeuds qui ont été remplacés lors de la mise à niveau. Contenu sous le **leftovers** indique le contenu qui n’a pas pu être fusionné en toute sécurité pendant la mise à niveau. Si votre mise en oeuvre dépend de l’un des noeuds enfants (et non déjà installé par votre package de code mis à niveau), ils doivent être fusionnés manuellement.

Désactivez le CRXDE Lite suivant cet exercice dans un environnement d’évaluation ou de production.

### Validation initiale des pages {#initial-validation-of-pages}

Effectuez une validation initiale sur plusieurs pages dans AEM. En cas de mise à niveau d’un environnement de création, ouvrez la page de démarrage et la page d’accueil ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). Dans les environnements de création et de publication, ouvrez quelques pages d’application et testez-les pour vous assurer qu’elles fonctionnent correctement. En cas de problème, veuillez consulter le fichier `error.log` pour un dépannage.

### Application de packs de service AEM {#apply-aem-service-packs}

Appliquez les Service Packs AEM 6.4 appropriés s’ils ont été publiés.

### Migration des fonctionnalités AEM {#migrate-aem-features}

Plusieurs fonctions d’AEM nécessitent des étapes supplémentaires après la mise à niveau. Vous trouverez une liste complète de ces fonctionnalités et étapes pour les migrer dans AEM 6.4 sur la page [Mise à niveau du code et des personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md) page.

### Vérification des configurations de maintenance planifiées {#verify-scheduled-maintenance-configurations}

#### Activation du nettoyage de la mémoire d’entrepôt de données {#enable-data-store-garbage-collection}

Si vous utilisez un entrepôt de données basé sur les fichiers, assurez-vous que la tâche de nettoyage de la mémoire d’entrepôt de données est activée et ajoutée à la liste de maintenance hebdomadaire. Suivez les instructions [suivantes](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Ceci n’est pas recommandé pour les installations de magasin de données personnalisé S3 ou lors de l’utilisation d’un entrepôt de données partagé.

#### Activation du nettoyage des révisions en ligne {#enable-online-revision-cleanup}

Si vous utilisez MongoMK ou le nouveau format de segment TarMK, assurez-vous que la tâche de nettoyage de révision est activée et ajoutée à la liste de maintenance quotidienne. Instructions décrites [here](/help/sites-deploying/revision-cleanup.md).

### Exécution du plan de test {#execute-test-plan}

Exécuter le plan de test détaillé par rapport à tel que défini [Mise à niveau du code et des personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md) sous le **Procédure de test** .

### Activation des agents de réplication {#enable-replication-agents}

Une fois que l’environnement de publication a été entièrement mis à niveau et validé, activez les agents de réplication dans l’environnement de création. Vérifiez que les agents sont en mesure de se connecter aux instances de publication respectives. Voir [Procédure de mise à niveau](/help/sites-deploying/upgrade-procedure.md) pour plus d’informations sur l’ordre des événements.

### Activation des tâches planifiées personnalisées {#enable-custom-scheduled-jobs}

À ce stade, toutes les tâches planifiées faisant partie de la base de code peuvent être activées.

## Analyse des problèmes liés à la mise à niveau {#analyzing-issues-with-upgrade}

Cette section contient des scénarios de problèmes que vous pouvez rencontrer lors de la procédure de mise à niveau vers AEM 6.4.

Ces scénarios doivent vous aider à déterminer la cause principale des problèmes liés à la mise à niveau et à identifier les problèmes spécifiques au projet ou au produit.

### Recréation de la configuration du cloud Dynamic Media après la mise à niveau {#dynamic-media-cloud-configuration}

Après la mise à niveau vers AEM 6.4 à partir d’une version antérieure, la configuration du cloud Dynamic Media des paramètres antérieurs peut devenir inaccessible à partir de l’interface utilisateur tactile d’AEM 6.4. Pour résoudre ce problème, utilisez CRXDE Lite pour supprimer les paramètres précédents, puis créez une configuration de cloud Dynamic Media. Voir aussi [Restructuration du référentiel Dynamic Media dans AEM 6.4](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md).

### Échec de la migration du référentiel  {#repository-migration-failing-}

La migration des données de CRX2 à Oak doit être réalisable en toutes situations, à commencer par les instances source basées sur CQ 5.4. Assurez-vous de suivre de près les instructions de mise à niveau de ce document, y compris la préparation du fichier `repository.xml`. Ainsi, vous garantissez qu’aucun authentificateur personnalisé ne puisse démarrer via JAAS et que l’instance a été testée pour éviter les incohérences avant de démarrer la migration.

Si la migration est toujours en échec, vous pouvez déterminer la cause première en consultant le fichier `upgrade.log`. Si le problème n’est pas encore connu, signalez-le au service clientèle.

### La mise à niveau n’a pas été exécutée {#the-upgrade-did-not-run}

Avant de commencer les étapes de préparation, veillez à exécuter la **source** d’abord en l’exécutant avec la commande java -jar aem-quickstart.jar . Cela est nécessaire pour s’assurer que le fichier quickstart.properties est généré correctement. S’il est manquant, la mise à niveau ne fonctionnera pas. Vous pouvez également vérifier si le fichier est présent en regardant sous `crx-quickstart/conf` dans le dossier d’installation de l’instance source. De plus, lorsque vous lancez AEM de lancement de la mise à niveau, celle-ci doit être exécutée avec la commande java -jar aem-quickstart.jar . Le démarrage à partir d’un script de démarrage ne démarre pas AEM en mode de mise à niveau.

### Échec de la mise à jour des packages et des lots  {#packages-and-bundles-fail-to-update-}

Si l’installation des packages échoue pendant la mise à niveau, les lots qu’ils contiennent ne seront pas mis à jour non plus. Cette catégorie de problèmes est généralement due à une mauvaise configuration de l’entrepôt de données. Elles apparaissent également comme **ERROR** et **WARN** messages dans le fichier error.log. Comme dans la plupart de ces cas, la connexion par défaut peut échouer, vous pouvez utiliser CRXDE directement pour examiner et trouver les problèmes de configuration.

### Certains lots AEM ne passent pas à l’état Principal {#some-aem-bundles-are-not-switching-to-the-active-state}

Si les lots ne démarrent pas, vous devez rechercher les dépendances non satisfaites.

Si ce problème est présent, mais qu’il est basé sur une installation de package ayant échoué et qui a entraîné la non-mise à niveau des lots, ils seront considérés comme incompatibles pour la nouvelle version. Pour plus d’informations sur la manière de résoudre ce problème, voir **Échec de la mise à jour des packages et des lots** ci-dessus.

Il est également recommandé de comparer la liste des lots d’une instance AEM 6.4 neuve avec celle de l’instance mise à niveau afin de détecter les lots qui n’ont pas été mis à niveau. Cela permettra de réduire le champ des recherches dans le fichier `error.log`.

### Lots personnalisés sans basculement vers l’état Principal {#custom-bundles-not-switching-to-the-active-state}

Si les lots personnalisés ne passent pas à l’état actif, il est probable qu’une partie du code ne procède pas à l’importation de l’API de modification, Cela entraîne le plus souvent des dépendances insatisfaites.

Les API supprimées doivent être marquées comme obsolètes dans l’une des versions précédentes. Vous trouverez des instructions sur la migration directe de votre code dans cet avis d’obsolescence. Adobe vise le contrôle de version sémantique lorsque cela est possible afin que les versions puissent indiquer les modifications entraînant une rupture.

Il est également préférable de vérifier si la modification qui a causé le problème était absolument nécessaire et de l’annuler si ce n’est pas le cas. Vérifiez également si l’augmentation de version de l’exportation du package a été plus élevée que nécessaire, suite au contrôle de version sémantique strict.

### Interface utilisateur de Platform dysfonctionnelle {#malfunctioning-platform-ui}

Dans le cas de certaines fonctionnalités de l’interface utilisateur qui ne fonctionnent pas correctement après la mise à niveau, vous devez d’abord vérifier les superpositions personnalisées de l’interface. Certaines structures peuvent avoir changé et la superposition peut nécessiter une mise à jour ou est obsolète.

Ensuite, recherchez les erreurs JavaScript pouvant être suivies jusqu’à des extensions ajoutées personnalisées qui sont connectées aux bibliothèques clientes. Il en va de même pour les CSS personnalisées qui peuvent poser des problèmes à la mise en page AEM.

Enfin, recherchez les erreurs de configuration que Javascript peut ne pas être en mesure de gérer. C’est généralement le cas avec des extensions incorrectement désactivées.

### Fonctionnement des composants personnalisés, des modèles ou des extensions de l’interface utilisateur {#malfunctioning-custom-components-templates-or-ui-extensions}

Dans la plupart des cas, les causes premières de ces problèmes sont les mêmes que pour les lots qui ne sont pas démarrés ou les packages qui ne sont pas installés, à la seule différence que les problèmes commencent à se produire lors de la première utilisation des composants.

Pour résoudre les erreurs de code personnalisé, commencez par effectuer des tests de détection de fumée afin d’identifier la cause. Une fois que vous l’avez trouvée, consultez les recommandations de cette section de la [rubrique] pour obtenir des moyens de corriger le problème.

### Personnalisations manquantes sous etc. {#missing-customizations-under-etc}

Les `/apps` et `/libs` sont correctement gérés par la mise à niveau mais les modifications sous `/etc` peuvent nécessiter une restauration manuelle à partir de `/var/upgrade/PreUpgradeBackup` après la mise à niveau. Veillez à inspecter cet emplacement pour identifier tout contenu devant être fusionné manuellement.

### Analyse des journaux error.log et upgrade.log  {#analyzing-the-error-log-and-upgrade-log}

Dans la plupart des cas, les logs doivent être consultés pour détecter les erreurs afin de trouver la cause d&#39;un problème. Toutefois, en cas de mises à niveau, il est également nécessaire de surveiller les problèmes de dépendance, car les anciens lots peuvent ne pas être correctement mis à niveau.

Pour ce faire, la meilleure méthode consiste à supprimer le fichier error.log en supprimant tous les messages qui ne sont pas liés au problème auquel vous êtes confronté. Vous pouvez le faire via un outil comme grep, en utilisant :

```shell
grep -v UnrelatedErrorString
```

Certains messages d’erreur peuvent ne pas être immédiatement explicatifs. Dans ce cas, la consultation du contexte dans lequel elles se produisent peut également aider à comprendre où l’erreur a été créée. Vous pouvez séparer l&#39;erreur à l&#39;aide des éléments suivants :

* `grep -B` pour l’ajout de lignes avant l’erreur

ou

* `grep -A` pour l’ajout de lignes après l’erreur.

Dans certains cas, des erreurs peuvent également être trouvées dans les messages AVERTISSEMENT, car il peut y avoir des cas valides menant à cet état et l’application n’est pas toujours en mesure de décider s’il s’agit d’une erreur réelle. Veillez également à consulter ces messages.

### Contacter le support technique d’Adobe {#contacting-adobe-support}

Si vous avez suivi les conseils de cette page et que vous rencontrez toujours des problèmes, contactez l’assistance Adobe. Pour fournir le plus d’informations possible à l’ingénieur du support qui travaille sur votre dossier, veillez à inclure le fichier upgrade.log de votre mise à niveau.
