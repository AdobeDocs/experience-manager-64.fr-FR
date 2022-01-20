---
title: Notes de mise à jour d’AEM Assets
seo-title: AEM Assets
description: Notes de mise à jour spécifiques à Adobe Experience Manager 6.4 Assets.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Assets.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
source-git-commit: 55e904cb24bac68c0b1bbea59786cb4c0c711d61
workflow-type: tm+mt
source-wordcount: '1647'
ht-degree: 60%

---

# AEM Assets Notes de mise à jour {#aem-assets-release-notes}

Les fonctionnalités, points forts et améliorations clés d’AEM 6.4 Assets sont abordés dans ces notes de mise à jour. Pour plus d’informations, suivez les liens proposés.

## Adobe Asset Link {#adobe-asset-link}

Adobe Asset Link dans Creative Cloud abonnement Entreprise simplifie la collaboration entre les créatifs et les spécialistes du marketing dans le cadre du processus de création de contenu. Il s’agit d’une nouvelle fonctionnalité native en Creative Cloud pour les entreprises, qui permet de se connecter à AEM Assets directement à partir d’Adobe Photoshop, d’Adobe Illustrator ou d’Adobe InDesign, sans quitter ces outils.

Pour en savoir plus sur la fonctionnalité, les conditions préalables et comment y accéder, voir la section [Adobe d’un lien de ressource](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) page.

## Balises intelligentes améliorées (avec technologie Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 introduit la fonctionnalité Balises intelligentes améliorées basée sur l’intelligence artificielle en plus des balises intelligentes lancées dans AEM 6.3.

* Le service de contenu dynamique apprend la taxonomie métier du client et l’utilise pour baliser automatiquement les ressources numériques avec les balises pertinentes pour le client en plus des balises génériques. Il améliore considérablement la visibilité des ressources et réduit le délai de mise sur le marché.
* Adobe Sensei alimente le service de contenu dynamique, ce qui vous permet d’entraîner l’algorithme de reconnaissance d’image sur votre taxonomie métier. Cette intelligence de contenu est ensuite utilisée pour appliquer les balises pertinentes sur les ressources similaires.

Pour utiliser les balises intelligentes améliorées d’AEM Assets, installez le [dernier Service Pack d’AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=fr).

## Recherche de traduction dynamique (avec la technologie Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 introduit la fonctionnalité de recherche de traduction intelligente pour prendre en charge les scénarios de recherche multilingue. Les clients disposant d’équipes dispersées dans le monde et parlant différentes langues ont désormais accès à la recherche dans différentes langues sans passer par des workflows de traduction coûteux et fastidieux.

* La requête de recherche est traduite sans intervention manuelle.
* Les balises intelligentes sont générées en anglais et sont traduites automatiquement dans d’autres langues.
* La recherche multilingue est créée à l’aide de la bibliothèque Open Source Apache Joshua qui prend en charge plus de 50 langues.

## Expérience utilisateur {#user-experience}

La version 6.4 d’AEM offre des améliorations significatives de l’expérience utilisateur dans les domaines de la navigation, de la recherche, des ressources multi-pages et des outils d’administration. Détails ci-dessous :

Améliorations de la navigation

* Nouveau rail d’arborescence de contenu pour naviguer rapidement au sein d’une hiérarchie d’actifs. Conjointement avec le mode Liste, cela restaure le modèle d’interaction de l’interface utilisateur classique afin de parcourir les hiérarchies d’actifs.
* Nouveaux raccourcis clavier tels que m pour déplacer des ressources, p pour ouvrir la page des propriétés, Ctrl + C pour copier l’opération, etc.
* Amélioration du défilement et de l’expérience de chargement différé en modes Carte et Liste afin de parcourir un grand nombre de ressources.
* Mode Carte amélioré avec la prise en charge d’images de différentes dimensions en fonction du paramètre d’affichage.
* Expérience de détail des actifs améliorée avec la possibilité d’afficher l’actif actuel et de naviguer entre l’actif précédent et suivant en fonction du nombre d’actifs.

Améliorations de la recherche

* Nouveau bouton Retour pour les recherches qui permet d’accéder à un élément de recherche et de revenir à la même position dans les résultats de recherche sans exécuter à nouveau la requête de recherche.
* Nouveau compteur de résultats de recherche pour afficher le nombre de résultats d’une recherche.
* Amélioration du filtre de recherche de type de fichier avec possibilité de filtrer les résultats de recherche en fonction de types MIME plus précis, tels que JPG, PNG et PSD, par rapport aux options d’image, de document et de multimédia précédentes.
* Améliorations des filtres de recherche avec des horodatages précis au lieu de la fonctionnalité précédente de curseur temporel.

Améliorations des ressources multi-pages

* Amélioration de l’expérience de navigation parmi les actifs multi-pages avec un nombre moindre de clics.
* Prise en charge améliorée des commentaires et des annotations, tous assemblés au niveau des actifs plutôt que des pages.

Améliorations des outils d’administration

* Amélioration du sélecteur de propriété dans les outils d’administration pour les métadonnées, la recherche et les rapports avec le type, et de la fonctionnalité de navigation afin de simplifier l’expérience de l’administrateur.

Catalogues

* Amélioration de l’expérience utilisateur, alignement avec l’interface utilisateur des modèles. Pour plus d’informations, voir [Producteur de catalogue](../sites-administering/catalog-producer.md).

## Métadonnées {#metadata}

AEM 6.4 comprend plusieurs fonctionnalités avancées de gestion des métadonnées destinées à gérer les métadonnées à l’échelle et à mettre en place l’intégrité des métadonnées par l’intermédiaire de règles et de validations. Voici les fonctionnalités essentielles :

* Nouvelle fonctionnalité d’exportation en masse de métadonnées permettant d’exporter toutes les métadonnées, ou une sélection, pour un grand nombre d’actifs au format CSV pour l’édition, le partage et l’intégration tierce.
* Nouvelle fonctionnalité d’importation en masse de métadonnées permettant d’importer un fichier CSV afin d’ajouter de nouvelles métadonnées et de mettre à jour des métadonnées existantes pour plusieurs actifs en une seule opération. Cette opération est asynchrone et n’entrave pas les performances du système. Une fois l’opération terminée, l’utilisateur est informé par le biais du système de notification d’AEM.
* Nouvelles métadonnées en cascade et contextuelles à l’aide de l’outil de schéma de métadonnées. Il est désormais possible de définir les chaînes de dépendances et les mappages de valeur entre les champs. Vous pouvez également définir le contexte dans lequel les champs de formulaire de métadonnées sont affichés/masqués. De cette façon, vous pouvez afficher uniquement les champs appropriés à tout moment en fonction des valeurs dans d’autres champs.

## Rapports {#reports}

La version 6.4 d’AEM offre d’importantes améliorations au niveau du reporting des ressources :

* Nouveau framework de rapports extensibles (pour les référentiels de grande taille) au niveau de l’entreprise appliquant des tâches Sling pour le traitement asynchrone des demandes de rapports. Vous pouvez planifier un rapport à une date et une heure précises. Vous pouvez également ajouter des colonnes personnalisées à un rapport.
* Nouveaux rapports prêts à l’emploi le plus souvent demandés par les clients, tels que Utilisation du disque, Fichiers, Partages de lien, Publier sur Brand Portal et Entraînement des balises intelligentes.
* Nouvelle interface utilisateur de création et de gestion des rapports dotée d’options de granularité fine, avec la possibilité d’accéder aux rapports archivés et de voir l’état d’exécution des rapports (réussite, échoué, en file d’attente, etc.).

## Brand Portal {#brand-portal}

* **Mise à niveau de la plate-forme 6.3** : Brand Portal mis à niveau d’AEM 6.0 à 6.3 avec de nouvelles fonctionnalités et améliorations des performances.
* **Publication en parallèle** : jusqu’à réplications peuvent se produire entre AEM Assets et Brand Portal (contre une auparavant), ce qui améliore considérablement les performances de publication.
* **Publication des schémas et des facettes de recherche** : possibilité de publier les schémas de métadonnées et les facettes de recherche personnalisée sur Brand Portal, évitant ainsi le dédoublement des efforts.
* **Publication en masse des balises** : possibilité de publier les taxonomies (avec les hiérarchies) sur Brand Portal, évitant ainsi le dédoublement des efforts.
* **Auto-inscription ou demande d’accès**: Workflow pour les utilisateurs non enregistrés dans Brand Portal.
* **Notification de maintenance dans l’application (à l’écran)** : les notifications sont affichées longtemps à l’avance afin d’éviter toute interruption de l’activité.
* **Amélioration de la création des rapports** : trois rapports prêts à l’emploi sont disponibles (téléchargements, publication et partages de lien).
* **Restrictions basées sur DRM** : lorsqu’un actif sous licence expire, il n’est plus disponible en téléchargement depuis Brand Portal.

## Application de bureau AEM {#aem-desktop-app}

L’appli de bureau AEM a été mise à jour vers la version 1.8, qui est compatible avec AEM 6.4. La liste complète des modifications apportées à l’appli de bureau Adobe est fournie dans un dossier dédié. [Notes de mise à jour de l’appli de bureau AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-desktop-app/using/release-notes.html) document.\
Voici une liste des principales caractéristiques de l’appli de bureau AEM depuis AEM 6.3 :

* Possibilité de télécharger des dossiers hiérarchiques en arrière-plan.
* Interface utilisateur permettant de surveiller les téléchargements des actifs en arrière-plan.
* Amélioration de la mise en cache, dont une interface utilisateur pour gérer les paramètres de mise en cache.
* Prise en charge élargie des configurations d’authentication AEM (SAML/SSO) et du proxy réseau.
* Compatibilité de la prise en charge : accès facile aux journaux à partir de l’interface utilisateur.
* Stabilité améliorée et correctifs pour les problèmes rencontrés par les clients.

Pour accéder plus facilement à la documentation et aux meilleures pratiques, la documentation suivante est disponible :

* [Guide de l’utilisateur](https://docs.adobe.com/content/help/fr-FR/experience-manager-desktop-app/using/using.html), destiné aux utilisateurs finaux utilisant l’application.
* [Guide d’installation](https://docs.adobe.com/content/help/fr-FR/experience-manager-desktop-app/using/install-upgrade.html), destiné aux administrateurs configurant l’appli de bureau AEM et AEM pour qu’ils travaillent ensemble

## Stockage à plusieurs niveaux {#tiered-storage}

AEM 6.4 comprend un ensemble de fonctions prenant en charge différentes préférences de stockage à plusieurs niveaux et mettant en œuvre les règles de cycle de vie. Les options de stockage prennent également en charge (sans toutefois s’y limiter) les clouds publics AWS et Azure.

* La possibilité pour les utilisateurs de sélectionner et de modifier ultérieurement la classe de stockage à leur gré et de définir des règles pour le stockage des ressources d’une classe à une autre ou de gérer le cycle de vie de leurs ressources.
* Possibilité pour les utilisateurs de réduire leurs coûts de stockage en choisissant un autre cloud AWS ou Azure.

Pour une présentation des plateformes prises en charge, consultez la [documentation sur les exigences techniques](../sites-deploying/technical-requirements.md).

## Groupe d’utilisateurs fermé {#closed-user-group}

* Dans AEM 6.4, le groupe d’utilisateurs fermé ou le groupe d’utilisateurs fermé permet de restreindre l’accès aux dossiers sur l’instance de publication. Il s’agit d’une option d’interface utilisateur tactile permettant d’ajouter des entités via la page des propriétés du dossier au niveau du dossier et de les appliquer à tous les dossiers et sous-dossiers/ressources à l’intérieur.
* En mode de publication, si un groupe d’utilisateurs fermé est configuré et que l’autorisation est activée sur un dossier, les utilisateurs sont redirigés vers une page de connexion lorsqu’ils tentent d’accéder au dossier. Par conséquent, les utilisateurs autorisés peuvent accéder au dossier et à ses actifs uniquement après la réussite de la connexion. Par conséquent, le CUG restreint l’accès en lecture à une arborescence donnée au sein du référentiel de contenu pour tout le monde à l’exception des entités sélectionnées.

## Module complémentaire Dynamic Media {#dynamic-media-add-on}

Dans la version 6.4, Dynamic Media prend en charge un nouveau mode, dans lequel l’actif original est téléchargé et géré à l’aide de l’interface utilisateur web d’AEM Assets, tandis que les rendus dynamiques et autres fonctions de médias dynamiques sont traités en arrière-plan par le service de livraison sur le cloud de Dynamic Media.

Dans ce mode (introduit en premier avec la sortie de [AEM 6.3 Feature Packs 14410 et 18912](https://helpx.adobe.com/fr/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), les utilisateurs bénéficient des fonctionnalités de gestion de ressources de bout en bout et de Dynamic Media à l’aide de l’interface utilisateur web moderne d’AEM Assets, tout en tirant parti des services de diffusion rétrocompatibles avec Dynamic Media Classic (Scene7), y compris les URL de diffusion inchangées.

En outre, AEM 6.4 introduit de nouvelles fonctions reposant sur Adobe Sensei pour les médias émergents, tels que VR et 3D, les visionneuses Dynamic Media et la prise en charge des fragments d’expérience au sein des images interactives et des bannières de carrousel.

### Recadrage intelligent (avec technologie Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* Le recadrage intelligent fournit automatiquement le recadrage non destructeur des images de façon à préserver le point d’intérêt pour le responsive design. Vous pouvez prévisualiser les suggestions de recadrage et les ajuster manuellement, si nécessaire.
* Cette fonction permet également la génération automatique d’échantillons pour l’imagerie produit. La génération d’échantillons automatisée permet d’ajouter automatiquement des nuanciers, des échantillons de motifs ou les deux à la fois aux images de produit.

Voir la documentation [Profils d’images](../assets/image-profiles.md) pour en savoir plus.

Voir également [Ajout de ressources Dynamic Media aux pages](../assets/adding-dynamic-media-assets-to-pages.md) pour plus d’informations sur l’utilisation du recadrage intelligent avec le composant Dynamic Media.

### Imagerie dynamique {#smart-imaging}

* L’imagerie dynamique tire parti des caractéristiques de visualisation uniques de chaque utilisateur pour diffuser automatiquement des images optimisées pour leur expérience, ce qui se traduit par de meilleures performances et un meilleur engagement.
* Les images sont automatiquement converties en différents formats en fonction des fonctionnalités du navigateur.
* Les paramètres de qualité d’image sont déterminés dans le navigateur et appliqués respectivement. Grâce à cette intelligence, les performances de chargement des images restent acceptables en cas de bande passante limitée ou de faibles débits de connexion.

Voir [Imagerie dynamique](../assets/imaging-faq.md) pour plus d’informations.

### Médias émergents et améliorations apportées aux visionneuses {#emerging-media-amp-viewer-enhancements}

* De nouvelles visionneuses sont prises en charge de façon à fournir de meilleures expériences immersives à l’utilisateur.
* La visionneuse panoramique permet d’interagir avec l’utilisateur et d’offrir une meilleure expérience des scènes de la salle, des propriétés, des lieux et des paysages. Voir la documentation [Images panoramiques](../assets/panoramic-images.md) pour plus d’informations.

* La visionneuse VR offre une expérience immersive pour les propriétés, les lieux et les paysages.
* La visionneuse d’image verticale est optimisée pour l’imagerie produit.
* Amélioration de l’accessibilité du clavier.
