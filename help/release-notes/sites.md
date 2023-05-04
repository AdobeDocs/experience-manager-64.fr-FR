---
title: Notes de mise à jour d’AEM Sites
seo-title: AEM Sites
description: Notes de mise à jour spécifiques à Adobe Experience Manager 6.4 Sites.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 9%

---

# Notes de mise à jour d’AEM Sites {#aem-sites-release-notes}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Sites {#sites}

Pour plus d’informations sur les améliorations apportées à AEM Sites 6.4, voir les sections suivantes :

### Administration de sites {#site-administration}

* Nouveau rail d’arborescence de contenu pour parcourir rapidement une hiérarchie de site. En mode Liste, le modèle d’interaction de l’interface utilisateur classique est restauré afin de parcourir un site.
* Amélioration du défilement en mode Carte et Liste des dossiers volumineux.
* Amélioration de l’interaction avec les résultats de la recherche : le bouton Retour restaure le résultat précédent de la recherche.
* Raccourcis clavier supplémentaires pour les actions les plus courantes, telles que l’ouverture d’un rail particulier, la modification, le déplacement et la suppression de pages ou l’ouverture de propriétés.
* Possibilité de désactiver les raccourcis clavier (activer/désactiver dans Préférences).
* Arrêtez d’afficher les horodatages dans toutes les interfaces utilisateur relative après 7 jours (définissez par défaut dans Préférences).

### Éditeur de page {#page-editor}

* Mise à jour de la liste des périphériques pour l’aperçu réactif du site, incluant désormais Apple iPhone 8, 8 Plus et X et Samsung S7.
* Déplacement de l’emplacement par défaut pour les informations de conception de modèle de /etc/design afin de prendre en charge les paramètres spécifiques aux sites dans /conf. Les clients qui effectuent une mise à niveau à partir de versions AEM antérieures peuvent continuer à utiliser /etc/design.

### Développement de composants et de modèles {#component-amp-template-development}

* Archétype de projet 13+, voir [Github pour les notes de mise à jour](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL version 1.3.1 : consultez la section [Github pour les notes de mise à jour](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Core Components 2.0.4+ : consultez la section [Github pour les notes de mise à jour](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Système de style

   * Ajout d’un nouveau concept pour affecter des classes CSS aux composants et permettre aux utilisateurs de l’éditeur de page de sélectionner un sous-ensemble de styles via l’interface utilisateur.
   * Ajout de la possibilité de définir le nom de l’élément de HTML rendu autour du composant, par exemple &lt;main>, &lt;aside>

* Système de grille pour le conteneur de dispositions : consultez la section [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Éditeur de modèles et stratégies

   * Les stratégies prennent désormais en charge les configurations du système de style par composant, par conteneur et par modèle.
   * Amélioration de la prise en charge de la définition de la mise en page dans les modèles sur les composants modifiables

* Pour le site de référence We.Retail 3.0, accédez à la question [Github pour les notes de mise à jour](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM comprend la version 1.12.4 de la bibliothèque jQuery pour fournir une compatibilité maximale avec le code personnalisé existant. Adobe a procédé à des modifications de façon à résoudre les problèmes de sécurité connus.

### Fragments de contenu et éditeur {#content-fragments-amp-editor}

* Introduction de modèles de contenu structuré comme base pour les fragments de contenu

   * Interface utilisateur de l’éditeur de modèles
   * Éléments de données préconfigurés pour les modèles de fragment de contenu (texte sur une seule ligne, texte sur plusieurs lignes, nombre, booléen, date et heure, énumération, référence de contenu, balises)

* Amélioration de l’utilisation de l’éditeur de fragment de contenu AEM

   * Présentation de la vue de tous les éléments
   * Modification en plein écran pour des éléments uniques
   * Amélioration des fonctionnalités d’édition de texte enrichi (listes à puces, listes numérotées, mise en retrait, liens hypertexte, tableaux, rechercher et remplacer, vérification orthographique)

* Ajout d’options de sortie améliorées pour les fragments de contenu AEM

   * Nouveau composant Fragment de contenu, dans le cadre des composants principaux. [Voir code sur GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Prise en charge de Content Services avec la sortie JSON via l’exportateur de modèle Sling

### Fragments d’expérience {#experience-fragments}

* Introduction de blocs de création de fragments d’expérience afin de faciliter la réutilisation du contenu entre les variations de fragments d’expérience en regroupant les composants et en autorisant une référence facile dans les variations.
* Ajout de la possibilité d’ajouter des fragments d’expérience aux projets de traduction via le rail de référence
* Ajout de la possibilité de démarrer des workflows avec des fragments d’expérience via le rail de frise chronologique.
* Le rail de référence indique maintenant où un fragment d’expérience est utilisé dans AEM
* La configuration des emplacements de modèles permet désormais aux auteurs de définir au niveau global ou au niveau du dossier ce que les modèles de fragments d’expérience sont autorisés à utiliser.
* La recherche à facettes prend désormais en charge le filtrage avancé, tel que publié/non publié, exporté vers les médias sociaux et Adobe Target.
* Ajout d’une connexion unique aux médias sociaux lors de l’exportation de fragments d’expérience vers Pinterest ou Facebook
* Intégration des fragments d’expérience AEM à Adobe Target. La synchronisation des fragments d’expérience avec Target crée des offres dans Adobe Target qui peuvent être utilisées avec le compositeur d’expérience visuelle de Target pour les incorporer dans n’importe quelle expérience activée par Target.

### Traduction {#translation}

* Amélioration de la convivialité des projets AEM traduction :

   * Prise en charge de plusieurs langues cibles dans un seul projet
   * Option de promotion et de suppression automatiques des lancements de traduction
   * Option de planification de l’exécution récurrente des projets de traduction (quotidien, hebdomadaire, mensuel, annuel)
   * Mosaïques de projet de traduction améliorées avec des informations d’état plus détaillées

* Mise à jour de la mémoire de traduction inverse pour mettre à jour la mémoire de traduction dans un système de gestion des traductions tiers après les modifications de contenu local dans AEM
* Les workflows de traduction prennent désormais en charge les racines de langue regroupées
* Ajout de la possibilité d’attribuer des noms arbitraires aux racines de langue et d’utiliser la propriété JCR pour mapper le code ISO.
* Les mises à jour de traduction dynamique reconnaissent désormais les nouvelles pages ajoutées à une branche principale de langue
* Introduction de la création de rapports d’état de traduction dans la vue Liste des administrateurs de sites

### Gestion multisite (MSM, Multi-Site Management) {#multi-site-management-msm}

* Amélioration de l’évolutivité MSM à l’aide d’un index basé sur Oak par rapport à la mémoire (LiveCopyIndex)

### Lancements {#launches}

* Amélioration des performances des lancements qui contiennent une grande arborescence de site et s’il y a de nombreux lancements principaux
* Amélioration de la promotion automatique et de la publication des lancements avec plusieurs pages racine.
* Correction d’un problème qui empêchait l’aperçu réactif de fonctionner avec les pages modifiées dans le contexte d’un lancement.

### Ciblage et simulation de contenu {#content-targeting-simulation}

* Dossiers d’assistance pour l’organisation des segments en fonction du site/contexte (CQ-94620)
* Déplacement de l’emplacement par défaut des segments dans /conf afin qu’ils aient des listes de segments spécifiques au site/contexte.

### AEM et Adobe Target  {#aem-amp-adobe-target-nbsp}

* Intégration des fragments d’expérience AEM à Adobe Target. La synchronisation des fragments d’expérience avec Target crée des offres dans Adobe Target qui peuvent être utilisées avec le compositeur d’expérience visuelle de Target pour les incorporer dans n’importe quelle expérience activée par Target.
* Adobe Target mbox.js version 63 est désormais inclus. Adobe recommande de passer à la version at.js de l’implémentation.
* at.js version 1.2.2 est désormais inclus. Adobe recommande d’utiliser Dynamic Tag Management (DTM) ou [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) pour provisionner at.js dans le site.

### AEM et Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 désormais inclus. Adobe recommande de passer à la mise en oeuvre du fichier AppMeasurement.js .
* AppMeasurement.js 1.8.0 désormais inclus. Adobe recommande d’utiliser Dynamic Tag Management (DTM) ou [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) pour provisionner AppMeasurement.js dans le site.

## Module complémentaire Communities {#communities-add-on}

Voir [Page Notes de mise à jour de Communities](/help/release-notes/communities-release-notes.md)

## Module complémentaire Screens {#screens-add-on}

* Ajout de la prise en charge de la connexion des lecteurs Screens aux serveurs de publication AEM pour les téléchargements de commande et de contrôle et de canal (au lieu de se connecter directement à AEM auteur).
* Ajout de la possibilité de regrouper les affectations de canal dans les planifications
* Les affectations de canal ont désormais une date de début et de fin.
* Le tableau de bord du périphérique affiche désormais la version du shell et du micrologiciel du lecteur.
* La liste Tableau de bord du périphérique affiche l’état de connexion du lecteur
* Ajout de la prise en charge de Google Chrome OS pour AEM Screens Player
* Ajout de Microsoft Windows 10 pour le lecteur AEM Screens
