---
title: Notes de mise à jour d’AEM Sites
seo-title: AEM Sites
description: Notes de mise à jour spécifiques à Adobe Experience Manager 6.4 Sites.
seo-description: Notes de mise à jour spécifiques à Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 80%

---


# Notes de mise à jour d’AEM Sites {#aem-sites-release-notes}

## Sites {#sites}

Voir la documentation suivante pour une description détaillée des améliorations d’AEM Sites 6.4 :

### Administration de sites  {#site-administration}

* Nouveau rail d’arborescence de contenu pour naviguer rapidement au sein d’une hiérarchie de site. Conjointement avec le mode Liste, cela restaure le modèle d’interaction de l’interface utilisateur classique afin de parcourir un site.
* Défilement optimisé en modes Carte et Liste au sein de dossiers volumineux.
* Interaction améliorée avec les résultats de recherche : le bouton Retour restaure le résultat de la recherche précédente.
* Raccourcis clavier supplémentaires pour les actions les plus courantes, telles que l’ouverture d’un rail particulier, ainsi que la modification, le déplacement et la suppression d’une page, ou l’ouverture des propriétés.
* Possibilité de désactiver les raccourcis clavier (activer/désactiver dans Préférences).
* Désactivation de l’affichage des horodatages dans toutes les interfaces utilisateur relative après 7 jours (défini par défaut dans Préférences).

### Éditeur de page {#page-editor}

* Liste de périphériques mise à jour pour l’aperçu de site dynamique, incluant maintenant Apple iPhone 8, 8 Plus et X, et Samsung S7
* Emplacement par défaut des informations de conception de modèles déplacé de /etc/design de façon à prendre en charge les paramètres spécifiques des sites dans /conf. Les clients mettant à niveau des versions antérieures d’AEM peuvent continuer à utiliser /etc/design.

### Développement de composants et de modèles {#component-amp-template-development}

* Projet Archetype 13+, voir [Github pour les notes de mise à jour](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL version 1.3.1, voir [Github pour les notes de mise à jour](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Core Components 2.0.4+, voir [Github pour les notes de mise à jour](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Système de style

   * Ajout d’un tout nouveau concept pour affecter des classes CSS aux composants et pour permettre aux utilisateurs de l’éditeur de pages de faire leur sélection parmi un sous-ensemble de styles dans l’interface utilisateur
   * Ajout de la possibilité de définir le nom de l’élément HTML rendu autour du composant (par exemple, &lt;main> et &lt;aside>)

* Système de grille pour le conteneur de mises en page, voir [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid) .
* Éditeur de modèles et stratégies

   * Les stratégies prennent maintenant en charge les configurations de système de style par composant, par conteneur et par modèle.
   * Prise en charge améliorée de la définition de la mise en page dans les modèles au niveau des composants modifiables

* Site de référence We.Retail 3.0, voir [Github pour les notes de mise à jour](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>aem inclut la version 1.12.4 de la bibliothèque jQuery afin de fournir une compatibilité maximale avec le code personnalisé existant. Adobe a procédé à des modifications de façon à résoudre les problèmes de sécurité connus.

### Fragments de contenu et éditeur  {#content-fragments-amp-editor}

* Introduction des modèles de contenu structurés comme base des fragments de contenu

   * Interface utilisateur de l’éditeur de modèles
   * Éléments de données préconfigurés pour les modèles de fragments de contenu (texte sur une seule ligne, texte sur plusieurs lignes, nombre, booléen, date et heure, énumération, référence de contenu, balises)

* Amélioration de l&#39;utilisation de l&#39;éditeur AEM de fragments de contenu

   * Aperçu comprenant tous les éléments
   * Modification d’éléments uniques en plein écran
   * Amélioration des fonctionnalités de modification de texte enrichi (liste à puces, listes numérotées, retraits, liens hypertexte, tableaux, rechercher et remplacer, et correcteur orthographique)

* Ajout d’options de sortie améliorées pour les fragments de contenu AEM

   * Nouveau composant de fragment de contenu au sein des composants de base. [Voir le code sur GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Prise en charge des services de contenu avec sortie JSON via l’outil d’exportation de modèles Sling

### Fragments d’expérience {#experience-fragments}

* Introduction des blocs de création de fragments d’expérience, de façon à faciliter la réutilisation du contenu entre les variations de fragments d’expérience en regroupant les composants et facilitant les références au sein des variations.
* Ajout de la possibilité d’ajouter des fragments d’expérience aux projets de traduction via le rail de référence
* Ajouté la capacité de début de workflows avec des fragments d’expérience via le rail de chronologie
* Le rail de référence indique maintenant où un fragment d’expérience est utilisé dans AEM
* La configuration des emplacements de modèles permet désormais aux auteurs de définir au niveau global ou de dossier ce que les modèles de fragments d’expérience sont autorisés à utiliser
* La recherche à facettes prend désormais en charge le filtrage avancé, par exemple, publié, non publié, exporté sur les réseaux sociaux et Adobe Target
* Ajout de la connexion unique aux réseaux sociaux lors de l’exportation de fragments de contenu vers Pinterest ou Facebook
* Intégration des fragments de contenu AEM à Adobe Target. La synchronisation des fragments d’expérience avec Adobe Target créera dans ce dernier des offres utilisables avec son outil de composition d’expérience visuelle afin de l’incorporer dans n’importe quelle expérience optimisée par Target.

### Traduction  {#translation}

* Utilisation améliorée des projets de traduction AEM :

   * Prise en charge de plusieurs langues cibles·dans un projet
   * Option de promotion et suppression automatique des lancements de traduction
   * Option pour planifier l’exécution périodique des projets de traduction (quotidien, hebdomadaire, mensuel ou annuel)
   * Mosaïques de projets de traduction améliorées avec des informations d’état plus détaillées

* Introduction de la mise à jour des mémoires de traduction inverse afin de mettre à jour les mémoires de traduction dans un système de gestion des traductions tiers suite à des modifications du contenu local dans AEM.
* Les workflows de traduction prennent désormais en charge les racines de langues groupées
* Ajout de la possibilité d’affecter des noms arbitraires aux racines de langues et d’utiliser la propriété JCR pour mapper avec le code ISO
* Les mises à jour de traduction intelligente reconnaissent désormais les nouvelles pages ajoutées à une branche de gabarit de langue
* Introduction de la création de rapports d’état dans le mode Liste de l’administration de site

### Gestion multisite (MSM, Multi-Site Management)  {#multi-site-management-msm}

* Évolutivité MSM améliorée en utilisant un index basé sur Oak plutôt qu’en mémoire (LiveCopyIndex)

### Lancements {#launches}

* Amélioration des performances des lancements contenant une grande arborescence de site et lorsque de nombreux lancements sont actifs.
* Amélioration de l’autopromotion et de la publication des lancements avec plusieurs pages racines.
* Correction d’un problème qui empêchait la prévisualisation de périphérique réactive de fonctionner avec les pages modifiées dans le contexte d’un lancement.

### Ciblage et simulation de contenu {#content-targeting-simulation}

* Dossiers de prise en charge pour organiser les segments en fonction du site/contexte (CQ-94620)
* Emplacement par défaut des segments déplacé dans /conf pour disposer de listes de segments spécifiques en fonction du site/contexte.

### AEM et Adobe Target   {#aem-amp-adobe-target-nbsp}

* Intégration des fragments de contenu AEM à Adobe Target. La synchronisation des fragments d’expérience avec Adobe Target créera dans ce dernier des offres utilisables avec son outil de composition d’expérience visuelle afin de l’incorporer dans n’importe quelle expérience optimisée par Target.
* La version 63 de mbox.js Adobe Target est désormais incluse. Adobe recommande de choisir at.js pour la mise en œuvre.
* Version 1.2.2 de at.js désormais intégrée. Adobe recommande d’utiliser la gestion dynamique des balises (DTM) ou [Adobe Experience Platform Launch](https://www.adobe.com/fr/enterprise/cloud-platform/launch.html) pour configurer at.js dans le site.

### AEM et Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 est désormais inclus. L’Adobe recommande de basculer l’implémentation vers AppMeasurement.js
* AppMeasurement.js 1.8.0 est désormais inclus. L’Adobe recommande d’utiliser la gestion dynamique des balises (DTM) ou [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) pour configurer AppMeasurement.js dans le site.

## Module complémentaire Communities {#communities-add-on}

Voir la [page de notes de mise à jour sur Communities](/help/release-notes/communities-release-notes.md)

## Module complémentaire Screens  {#screens-add-on}

* Ajout de la prise en charge de la connexion des lecteurs Screens aux serveurs de publication AEM pour les téléchargements de commande, de contrôle et de canal (au lieu de se connecter directement sur le serveur de création AEM).
* Ajout de la possibilité de regrouper les affectations des canaux dans les planifications.
* Les affectations des canaux ont désormais une date de début et de fin.
* Le tableau de bord du périphérique affiche désormais la version de shell et de micrologiciel du lecteur.
* Le tableau de bord du périphérique affiche l’état de connexion du lecteur.
* Prise en charge Ajoutée de Google Chrome OS pour AEM Screens Player
* Microsoft Windows 10 Ajouté pour AEM Screens Player
