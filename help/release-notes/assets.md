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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 3%

---

# Notes de mise à jour d’AEM Assets {#aem-assets-release-notes}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les fonctionnalités, points forts et améliorations clés d’AEM 6.4 Assets sont abordés dans ces notes de mise à jour. Pour plus d’informations, suivez les liens proposés.

## Adobe Asset Link {#adobe-asset-link}

Adobe Asset Link dans Creative Cloud pour les entreprises simplifie la collaboration entre les créatifs et les spécialistes du marketing dans le processus de création de contenu. Il s’agit d’une nouvelle fonctionnalité native en Creative Cloud pour les entreprises, qui permet de se connecter à AEM Assets directement à partir d’Adobe Photoshop, d’Adobe Illustrator ou d’Adobe InDesign, sans quitter ces outils.

Pour en savoir plus sur la fonctionnalité, les conditions préalables et comment y accéder, voir la section [Adobe d’un lien de ressource](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) page.

## Balises intelligentes améliorées (avec technologie Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 introduit la fonctionnalité Balises intelligentes améliorées basée sur l’intelligence artificielle en plus des balises intelligentes lancées dans AEM 6.3.

* Le service de contenu dynamique apprend la taxonomie métier du client et l’utilise pour baliser automatiquement les ressources numériques avec les balises pertinentes pour le client en plus des balises génériques. Cela améliore considérablement la visibilité des ressources et réduit le temps de mise sur le marché.
* Adobe Sensei alimente le service de contenu dynamique, ce qui vous permet d’entraîner l’algorithme de reconnaissance d’image sur votre taxonomie métier. Cette intelligence de contenu est ensuite utilisée pour appliquer des balises pertinentes sur des ressources similaires.

Pour utiliser les balises intelligentes améliorées d’AEM Assets, installez le [dernier Service Pack d’AEM 6.4](https://helpx.adobe.com/fr/experience-manager/aem-releases-updates.html).

## Recherche de traduction dynamique (avec la technologie Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 introduit la fonctionnalité de recherche de traduction intelligente pour prendre en charge les scénarios de recherche multilingue. Les clients disposant d’équipes réparties dans plusieurs paramètres régionaux ont désormais accès à la recherche dans différentes langues sans avoir à recourir à des processus de traduction coûteux et fastidieux.

* La requête de recherche est traduite sans intervention manuelle.
* Les balises intelligentes sont générées en anglais et sont traduites automatiquement dans d’autres langues.
* La recherche multilingue est créée à l’aide de la bibliothèque Open Source Apache Joshua qui prend en charge plus de 50 langues.

## Expérience utilisateur {#user-experience}

La version 6.4 d’AEM offre des améliorations significatives de l’expérience utilisateur dans les domaines de la navigation, de la recherche, des ressources multi-pages et des outils d’administration. Détails ci-dessous :

Améliorations de la navigation

* Nouveau rail Arborescence de contenu pour parcourir rapidement une hiérarchie de ressources. En mode Liste, le modèle d’interaction de l’interface utilisateur classique est restauré afin de parcourir les hiérarchies de ressources.
* Nouveaux raccourcis clavier tels que m pour déplacer des ressources, p pour ouvrir la page des propriétés, Ctrl + C pour copier l’opération, etc.
* Amélioration du défilement et de l’expérience de chargement différé dans les vues Carte et Liste afin de parcourir un grand nombre de ressources.
* Amélioration du mode Carte avec la prise en charge de différentes cartes de taille en fonction du paramètre d’affichage.
* Expérience améliorée des détails de la ressource avec possibilité d’afficher la ressource &quot;précédente&quot; ou &quot;suivante&quot;, ainsi que le nombre de ressources, la ressource actuelle.

Améliorations de la recherche

* Nouveau bouton Retour de la recherche permettant de naviguer jusqu’à un élément de recherche et de revenir à la même position dans les résultats de recherche sans relancer la requête.
* Nouveau nombre de résultats de recherche pour afficher le nombre de résultats de recherche.
* Amélioration du filtre de recherche de type de fichier avec possibilité de filtrer les résultats de recherche en fonction de types MIME plus précis, tels que JPG, PNG et PSD, par rapport aux options d’image, de document et de multimédia précédentes.
* Amélioration des filtres de recherche avec des horodatages précis au lieu de la fonctionnalité précédente de curseur temporel.

Améliorations des ressources multi-pages

* Amélioration de l’expérience de navigation des ressources multi-pages avec un nombre réduit de clics.
* Amélioration de la prise en charge des commentaires et des annotations, tous rassemblés au niveau de la ressource plutôt qu’au niveau de la page.

Améliorations des outils d’administration

* Amélioration du sélecteur de propriétés dans les outils d’administration pour les métadonnées, la recherche et les rapports avec le type , ainsi que la fonctionnalité de navigation afin de simplifier l’expérience de l’administrateur.

Catalogues

* Amélioration de l’expérience utilisateur, alignement avec l’interface utilisateur des modèles. Pour plus d’informations, voir [Producteur de catalogue](../sites-administering/catalog-producer.md).

## Métadonnées {#metadata}

AEM version 6.4 comprend plusieurs fonctionnalités avancées de gestion des métadonnées pour gérer les métadonnées à grande échelle et appliquer l’intégrité des métadonnées par le biais de règles et de validations. Voici les principales fonctionnalités :

* Nouvelle fonctionnalité d’exportation de métadonnées en bloc permettant d’exporter (toutes, de manière sélective) des métadonnées pour un grand nombre de ressources au format CSV pour la modification, le partage et l’intégration tierce.
* Nouvelle fonctionnalité d’importation de métadonnées en bloc pour importer un fichier CSV afin d’ajouter de nouvelles métadonnées, en mettant à jour les métadonnées existantes pour plusieurs ressources en une seule fois. Cette opération est asynchrone et n’entrave pas les performances du système. Une fois l’opération terminée, l’utilisateur est informé via AEM système de notification.
* Nouvelles métadonnées en cascade et contextuelles à l’aide de l’outil de schéma de métadonnées. Il est désormais possible de définir des chaînes de dépendances et des mappages de valeurs entre les champs. Vous pouvez également définir le contexte dans lequel les champs de formulaire de métadonnées sont affichés/masqués. Ainsi, vous ne pouvez afficher que les champs pertinents à tout moment, en fonction des valeurs des autres champs.

## Rapports {#reports}

La version 6.4 d’AEM offre d’importantes améliorations au niveau du reporting des ressources :

* Nouvelle structure de rapports évolutive au niveau de l’entreprise (pour les référentiels volumineux) qui applique les tâches Sling pour le traitement asynchrone des demandes de rapports. Vous pouvez planifier le rapport à une date et une heure spécifiques. Vous pouvez également ajouter des colonnes personnalisées à un rapport.
* Nouveaux rapports prêts à l’emploi le plus souvent demandés par les clients, tels que Utilisation du disque, Fichiers, Partages de lien, Publier sur Brand Portal et Entraînement des balises intelligentes.
* Nouvelle interface utilisateur de création et de gestion des rapports avec des options précises, possibilité d’accéder aux rapports archivés, d’afficher l’état d’exécution des rapports (succès, échec, mise en file d’attente, etc.).

## Brand Portal {#brand-portal}

* **6.3 Mise à niveau de la plateforme**: Brand Portal a été mis à niveau d’AEM 6.0 vers AEM 6.3, avec de nouvelles fonctionnalités et des améliorations de performances.
* **Publication parallèle**: Des réplications peuvent se produire entre AEM Assets et Brand Portal (1 auparavant), ce qui améliore considérablement les performances de publication.
* **Publication de la facette de recherche et du schéma**: Possibilité de publier des schémas de métadonnées et des facettes de recherche personnalisées dans Brand Portal, ce qui élimine la duplication des efforts.
* **Publication de balises en bloc**: Possibilité de publier la taxonomie (avec la hiérarchie) sur Brand Portal, ce qui élimine la duplication des efforts.
* **Auto-inscription ou demande d’accès**: Workflow pour les utilisateurs non enregistrés dans Brand Portal.
* **Notification de maintenance In-App (à l’écran)**: Les notifications s’affichent bien à l’avance afin d’éviter toute perturbation de l’activité.
* **Amélioration des rapports**: Trois rapports prêts à l’emploi sont disponibles : téléchargements, publication et partages de liens.
* **Restrictions basées sur DRM**: Une fois qu’une ressource sous licence est arrivée à expiration, elle n’est plus disponible pour téléchargement à partir de Brand Portal.

## Application de bureau AEM {#aem-desktop-app}

L’appli de bureau AEM a été mise à jour vers la version 1.8, qui est compatible avec AEM 6.4. La liste complète des modifications apportées à l’appli de bureau Adobe est fournie dans un dossier dédié. [Notes de mise à jour de l’appli de bureau AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=fr) document.\
Voici une liste des principales caractéristiques de l’appli de bureau AEM depuis AEM 6.3 :

* Possibilité de charger des dossiers hiérarchiques en arrière-plan.
* Interface utilisateur permettant de surveiller les chargements de ressources en arrière-plan.
* Améliorations de la mise en cache, notamment une interface utilisateur pour gérer les paramètres de mise en cache.
* Prise en charge plus large des configurations d’authentification AEM (SAML/SSO) et du proxy réseau.
* Compatibilité de la prise en charge : accès facile aux journaux à partir de l’interface utilisateur.
* Stabilité améliorée et correctifs pour les problèmes des clients.

Pour accéder plus facilement à la documentation et aux bonnes pratiques, la documentation suivante est disponible :

* [Guide de l’utilisateur](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr), destiné aux utilisateurs finaux utilisant l’application.
* [Guide d’installation](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/install-upgrade.html), destiné aux administrateurs configurant l’appli de bureau AEM et AEM pour qu’ils travaillent ensemble

## Stockage à plusieurs niveaux {#tiered-storage}

AEM 6.4 comprend un ensemble de fonctionnalités qui prennent en charge diverses préférences de stockage à plusieurs niveaux et mettent en oeuvre des règles de cycle de vie. Les options de stockage prennent également en charge (sans s’y limiter) les clouds publics : AWS ou Azure.

* La possibilité pour les utilisateurs de sélectionner et de modifier ultérieurement la classe de stockage à leur gré et de définir des règles pour le stockage des ressources d’une classe à une autre ou de gérer le cycle de vie de leurs ressources.
* La possibilité pour les utilisateurs de réduire leur coût de stockage en sélectionnant un autre AWS ou Azure.

Pour une présentation des plateformes prises en charge, reportez-vous à la section [Documentation sur les exigences techniques](../sites-deploying/technical-requirements.md).

## Groupe d’utilisateurs fermé {#closed-user-group}

* Dans AEM 6.4, le groupe d’utilisateurs fermé ou le groupe d’utilisateurs fermé permet de restreindre l’accès aux dossiers sur l’instance de publication. Il s’agit d’une option d’interface utilisateur tactile permettant d’ajouter des entités via la page des propriétés du dossier au niveau du dossier et de les appliquer à tous les dossiers et sous-dossiers/ressources à l’intérieur.
* En mode de publication, si un groupe d’utilisateurs fermé est configuré et que l’autorisation est activée sur un dossier, les utilisateurs sont redirigés vers une page de connexion lorsqu’ils tentent d’accéder au dossier. Par conséquent, les utilisateurs autorisés ne peuvent accéder au dossier et à ses ressources qu’après une connexion réussie. Par conséquent, le CUG limite l’accès en lecture à une arborescence donnée dans le référentiel de contenu pour tous, à l’exception des entités sélectionnées.

## Module complémentaire Dynamic Media {#dynamic-media-add-on}

Dynamic Media dans la version 6.4 prend en charge un nouveau mode : la ressource principale est chargée et gérée à l’aide de l’interface utilisateur web d’AEM Assets. Les rendus dynamiques et d’autres fonctionnalités de média dynamique sont gérés en arrière-plan par le service de diffusion cloud Dynamic Media.

Dans ce mode (introduit en premier avec la sortie de [AEM 6.3 Feature Packs 14410 et 18912](https://helpx.adobe.com/fr/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), les utilisateurs bénéficient des fonctionnalités de gestion de ressources de bout en bout et de Dynamic Media à l’aide de l’interface utilisateur web moderne d’AEM Assets, tout en tirant parti des services de diffusion rétrocompatibles avec Dynamic Media Classic (Scene7), y compris les URL de diffusion inchangées.

En outre, AEM 6.4 introduit de nouvelles fonctionnalités optimisées par Adobe Sensei, des améliorations pour les médias émergents tels que VR et 3D, les visionneuses Dynamic Media et la prise en charge des fragments d’expérience dans les images interactives et les bannières de carrousel.

### Recadrage intelligent (avec technologie Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* Le recadrage intelligent fournit automatiquement un recadrage non destructif des images pour préserver le point d’intérêt du responsive design. Vous pouvez prévisualiser les suggestions recadrées et les ajuster manuellement, si nécessaire.
* Cette fonctionnalité permet également la génération automatique d’échantillons pour l’imagerie du produit. La génération automatisée d’échantillons permet d’ajouter automatiquement des échantillons de couleurs, des échantillons de motifs ou les deux aux images de produits.

Voir [Profils d’image](../assets/image-profiles.md) pour en savoir plus.

Voir aussi [Ajout de ressources Dynamic Media aux pages](../assets/adding-dynamic-media-assets-to-pages.md) documentation pour en savoir plus sur l’utilisation du recadrage intelligent avec le composant Dynamic Media.

### Imagerie dynamique {#smart-imaging}

* L’imagerie dynamique tire parti des caractéristiques de visualisation uniques de chaque utilisateur pour diffuser automatiquement des images optimisées pour leur expérience, ce qui se traduit par de meilleures performances et un meilleur engagement.
* Les images sont automatiquement converties dans différents formats en fonction des fonctionnalités du navigateur.
* Les paramètres de qualité d’image sont déterminés dans le navigateur et appliqués respectivement. Cette intelligence maintient les performances de chargement des images acceptables pour une bande passante limitée et des vitesses de connexion lentes.

Voir [Imagerie dynamique](../assets/imaging-faq.md) pour en savoir plus.

### Médias émergents et améliorations apportées aux visionneuses {#emerging-media-amp-viewer-enhancements}

* Les nouvelles visionneuses sont prises en charge, ce qui permet à l’utilisateur de bénéficier d’une expérience immersive plus agréable.
* La visionneuse panoramique permet d’interagir avec l’utilisateur et d’offrir une meilleure expérience des scènes de la salle, des propriétés, des lieux et des paysages. Voir [Images panoramiques](../assets/panoramic-images.md) pour en savoir plus.

* La visionneuse VR offre une expérience immersive pour les propriétés, les lieux et les paysages.
* Visionneuse d’images verticale optimisée pour l’imagerie du produit.
* Améliorations de l’accessibilité du clavier.
