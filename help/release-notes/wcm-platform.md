---
title: AEM Foundation et référentiel
seo-title: AEM Foundation et référentiel
description: Notes de mise à jour spécifiques à la plateforme et au référentiel d’Adobe Experience Manager 6.3.
seo-description: Notes de mise à jour spécifiques à la plateforme et au référentiel d’Adobe Experience Manager 6.3.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
translation-type: tm+mt
source-git-commit: 966263cc94f44bcad76e7e9ba5c6ecdc93574348
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 81%

---


# AEM Foundation et référentiel  {#aem-foundation-repository}

## Liste des modifications  {#list-of-changes}

### Référentiel {#repository}

* Microkernel Oak Segment Tar

   * Mode rapide de compression (compression des révisions les plus récentes) pour le nettoyage des révisions en ligne
   * Vitesses d’écriture améliorées
   * Statistiques des opérations sur les segments exposées via JMXBean
   * Estimation de la durée du nettoyage des révisions hors ligne

* Microkernel Oak Mongo

   * Le nettoyage des révisions en continu pour MongoMK remplace la maintenance de nettoyage planifiée.

* Efficacité accrue du nettoyage des·révisions sur les magasins de nœuds de documents
* Veuillez consulter [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) et [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) pour un aperçu complet des problèmes résolus.

>[!CAUTION]
>
>* La nouvelle version d’Oak Segment Tar présente depuis AEM 6.3 nécessite une migration de référentiel. Cette étape est obligatoire si vous effectuez une mise à niveau à partir d’une ancienne version de TarMK ou si vous souhaitez remplacer le nouveau Segment Tar par un autre type de persistance. Pour en savoir plus sur les avantages du nouveau Segment Tar, voir [FAQ sur la migration vers Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

>



### Recherche et indexation {#search-amp-indexing}

* Prise en charge améliorée des opérations d’indexation par l’intermédiaire d’oak-run (interface de ligne de commande) :

   * Contrôle de la cohérence de l’index
   * Indexation des statistiques
   * Importation/exportation des configurations d’index
   * Réindexation

* Réduction de la croissance des référentiels associés à Lucene pour des performances système globales améliorées
* Index de propriété Lucene synchrones [(en savoir plus)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* La commande Expliquer la requête du gestionnaire d’index prend désormais en charge la syntaxe AEM QueryBuilder.
* Le gestionnaire d’index expose maintenant les mesures des index : taille, dernière mise à jour et contrôle de cohérence.

### Interface utilisateur {#user-interface}

* Diverses améliorations ont été apportées à l’interface utilisateur pour la rendre plus productive et plus facile à utiliser.
* Nouveau rail d’arborescence de contenu pour naviguer rapidement au sein d’une hiérarchie. Conjointement avec le mode Liste, cela restaure le modèle d’interaction de l’interface utilisateur classique.
* Défilement optimisé en modes Carte et Liste au sein de dossiers volumineux.
* Interaction améliorée avec les résultats de recherche : le bouton Retour restaure le résultat de la recherche précédente.
* Raccourcis clavier supplémentaires pour les actions les plus courantes, telles que l’ouverture d’un rail particulier, ainsi que la modification, le déplacement et la suppression d’un élément, ou l’ouverture des propriétés.
* Possibilité de désactiver les raccourcis clavier (activer/désactiver dans Préférences).
* Désactivation de l’affichage des horodatages dans toutes les interfaces utilisateur relative après 7 jours (défini par défaut dans Préférences).

>[!CAUTION]
>
>* Adobe ne prévoit pas d’apporter d’autres améliorations à l’interface utilisateur classique. AEM 6.4 inclut l’interface utilisateur classique, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que l’interface utilisateur classique reste entièrement prise en charge tout en étant obsolète [Lire la suite ](/help/sites-deploying/ui-recommendations.md).

>



### Distribution de contenu {#content-distribution}

* Performance de réplication améliorée afin de prendre en charge les publications d’actifs aux volumes importants
* Prise en charge de l’authentification OAuth 2.0 dans le transport de distribution
* Amélioration des performances des modules VLT

### Surveillance {#monitoring}

* Une nouvelle vue d&#39;ensemble du système fournit une vue d&#39;instantané sur l&#39;état et les activités de tous les systèmes liés aux performances.
* Nouveaux contrôles d’intégrité :

   * Détection d’index Lucene de grande taille
   * Intégrité d’index asynchrone
   * Index Lucene volumineux
   * Performances des requêtes
   * Limites de requête transversales
   * Horloges synchronisées
   * Maintenance du système – Nettoyage des révisions
   * Maintenance du système – GC de banque de données
   * Maintenance du système – GC de révisions en continu

* L’utilisateur peut désormais définir le domaine du téléchargement status.zip.

### Maintenance {#maintenance}

* Suppression active des binaires Lucene à l’aide d’une tâche de maintenance
* La tâche de maintenance RevisionGC pour MongoDB est maintenant désactivée en faveur du nettoyage de révisions continu, voir la section Référentiel ci-dessus.
* La configuration de purge de version permet de conserver un nombre minimal de versions.
* La purge de version s’arrête à la fin d’une fenêtre de maintenance. Elle peut également être démarrée et arrêtée manuellement, et continuera progressivement au démarrage suivant.

### Mise à niveau  {#upgrade}

* Compatibilité descendante : grâce aux fonctions de la version 6.4 compatibles avec les versions antérieures, votre code personnalisé reste compatible dans la plupart des cas, et les efforts de mise à niveau sont réduits.
* Évaluation de la complexité de la mise à niveau : le nouvel outil de détection des motifs évalue la complexité de vos mises à niveau avant que vous ne les effectuiez.
* Mises à niveau possibles : l’introduction de la surface d’API et de la classification du contenu vous permet de suivre facilement les meilleures pratiques pour une mise à niveau efficace et transparente vers la prochaine version tout au long du cycle de développement.
* Restructuration du référentiel : Une restructuration importante (principalement /etc) pour faciliter les mises à niveau et promouvoir les meilleures pratiques d&#39;implémentation. [En savoir plus.](/help/sites-deploying/repository-restructuring.md)
* Consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md) pour plus de détails sur ces fonctionnalités.

### Cloud Services {#cloud-services}

* De nombreux Cloud Services peuvent désormais être configurés via l’interface utilisateur tactile ; le reste peut être configuré sous la carte Cloud Services héritée.
* Les dossiers Sites et Ressources peuvent être configurés avec des Cloud Services chargés selon le contexte.

### Sécurité {#security}

* Interface utilisateur de création d’utilisateurs améliorée et simplifiée prenant en charge plusieurs profils d’utilisateurs.
* Performances améliorées pour les utilisateurs appartenant à des groupes de grande taille.

### Projets et workflows {#projects-and-workflows}

* Éditeur de workflow basé sur l’interface utilisateur tactile pour gérer les modèles de workflow de manière plus structurée.
* Prise en charge de la purge des tâches de projets dans les tâches de maintenance.

