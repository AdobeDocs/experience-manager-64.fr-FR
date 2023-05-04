---
title: AEM Foundation et référentiel
seo-title: AEM Foundation & Repository
description: Notes de mise à jour spécifiques à Adobe Experience Manager 6.3 AEM Platform et au référentiel.
seo-description: Release notes specific to Adobe Experience Manager 6.3 AEM Platform and Repository.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 13%

---

# AEM Foundation et référentiel {#aem-foundation-repository}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Liste des modifications {#list-of-changes}

### Référentiel {#repository}

* MicroKernel Oak Segment Tar

   * Mode de compression rapide (compression des révisions) pour le nettoyage des révisions en ligne
   * Amélioration des taux d’écriture
   * Statistiques des opérations de segment exposées via JMXBean
   * Estimation de la durée du nettoyage des révisions hors ligne

* Microkernel Oak Mongo

   * Le nettoyage des révisions en continu pour MongoMK remplace la maintenance de nettoyage planifiée.

* Amélioration de l’efficacité du nettoyage des révisions sur les noeuds de document
* Veuillez consulter [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) et [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) pour une vue d’ensemble complète des problèmes résolus.

>[!CAUTION]
>
>* La nouvelle version d’Oak Segment Tar présente depuis AEM 6.3 nécessite une migration de référentiel. Cette étape est obligatoire si vous effectuez une mise à niveau à partir d’une ancienne version de TarMK ou souhaitez changer le nouveau Segment Tar d’un autre type de persistance. Pour plus d’informations sur les avantages du nouveau Segment Tar, voir la section [FAQ sur la migration vers Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>


### Recherche et indexation {#search-amp-indexing}

* Amélioration de la prise en charge des opérations d’indexation via oak-run (CLI) :

   * Vérification de la cohérence de l&#39;index
   * Indexation des statistiques
   * Importation/exportation de la configuration d’index
   * Réindexation

* Réduction de la croissance des référentiels liés à Lucene pour des performances système globales améliorées
* Index de propriété Lucene synchrones [(Plus d’informations)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Expliquer la requête dans le gestionnaire d’index prend désormais en charge AEM syntaxe QueryBuilder
* Le gestionnaire d’index expose maintenant les mesures d’index : taille, dernière mise à jour et vérification de cohérence

### Interface utilisateur {#user-interface}

* Diverses améliorations ont été apportées à l’interface utilisateur afin de la rendre plus productive et plus facile à utiliser.
* Nouveau rail d’arborescence de contenu pour parcourir rapidement une hiérarchie. En mode Liste, le modèle d’interaction de l’interface utilisateur classique est restauré.
* Amélioration du défilement en mode Carte et Liste des dossiers volumineux.
* Amélioration de l’interaction avec les résultats de la recherche : le bouton Retour restaure le résultat précédent de la recherche.
* Raccourcis clavier supplémentaires pour les actions les plus courantes, telles que l’ouverture d’un rail particulier, la modification, le déplacement et la suppression d’un élément ou l’ouverture de propriétés.
* Possibilité de désactiver les raccourcis clavier (activer/désactiver dans Préférences).
* Arrêtez d’afficher les horodatages dans toutes les interfaces utilisateur relative après 7 jours (définissez par défaut dans Préférences).

>[!CAUTION]
>
>* Adobe ne prévoit pas d’apporter d’autres améliorations à l’interface utilisateur classique. AEM 6.4 comprend l’interface utilisateur classique, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que l’interface utilisateur classique reste entièrement prise en charge tout en étant obsolète. [En savoir plus](/help/sites-deploying/ui-recommendations.md).
>


### Distribution de contenu {#content-distribution}

* Amélioration des performances de réplication pour la prise en charge des publications de ressources à gros volume
* Prise en charge de l’authentification OAuth 2.0 dans le transport de distribution
* Amélioration des performances des modules VLT

### Surveillance {#monitoring}

* Une nouvelle présentation du système fournit une vue instantanée de tous les états et activités du système liés aux performances.
* Nouveaux contrôles d’intégrité :

   * Détecter les index Lucene volumineux
   * Intégrité de l’indexation asynchrone
   * Index Lucene volumineux
   * Performances des requêtes
   * Limites de requête transversales
   * Horloges synchronisées
   * Maintenance du système - Nettoyage des révisions
   * Maintenance du système - GC de banque de données
   * Maintenance du système - GC de révision continue

* L’utilisateur peut désormais définir la portée du téléchargement status.zip.

### Maintenance {#maintenance}

* Suppression principale des fichiers binaires Lucene à l’aide d’une tâche de maintenance
* La tâche de maintenance RevisionGC pour MongoDB est maintenant désactivée au profit du nettoyage des révisions en continu. Consultez la section Référentiel ci-dessus.
* La configuration Purge de version permet de conserver un nombre minimum de versions.
* La purge de version s’arrête à la fin d’une fenêtre de maintenance. Il peut également être démarré et arrêté manuellement et il continuera de manière incrémentielle au prochain démarrage.

### Mise à niveau {#upgrade}

* Compatibilité descendante : Les fonctionnalités rétrocompatibles de la version 6.4 permettent à votre code personnalisé de rester compatible dans la plupart des cas et réduisent les efforts de mise à niveau.
* Évaluation de la complexité de la mise à niveau : Nouveau détecteur de motifs pour évaluer la complexité de vos mises à niveau.
* Mises à niveau possibles : Mise en place de la surface de l’API et de la classification du contenu afin de vous aider à suivre facilement les bonnes pratiques pour une mise à niveau efficace et transparente vers la version suivante tout au long de votre cycle de développement.
* Restructuration des référentiels : Une restructuration significative (principalement /etc) pour faciliter les mises à niveau et promouvoir les bonnes pratiques de mise en oeuvre. [En savoir plus.](/help/sites-deploying/repository-restructuring.md)
* Veuillez consulter la [Documentation de mise à niveau](/help/sites-deploying/upgrade.md) pour plus d’informations sur ces fonctionnalités.

### Services cloud {#cloud-services}

* De nombreux Cloud Services peuvent désormais être configurés via l’interface utilisateur tactile ; le reste peut être configuré sous la carte Cloud Services hérités .
* Les dossiers Sites et Ressources peuvent être configurés avec des Cloud Services chargés selon le contexte.

### Sécurité {#security}

* Interface utilisateur de création d’utilisateurs améliorée et simplifiée avec prise en charge de plusieurs profils d’utilisateurs.
* Amélioration des performances pour les appartenances à des groupes volumineux pour les utilisateurs.

### Projets et workflows {#projects-and-workflows}

* Éditeur de workflow basé sur l’interface utilisateur tactile pour gérer les modèles de workflow de manière plus simple.
* Prise en charge de la purge des tâches du projet dans les tâches de maintenance.
