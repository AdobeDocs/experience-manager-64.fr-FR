---
title: Fontionnalités Configuration de l’activation
seo-title: Configuring Enablement Features
description: Configuration des fonctionnalités d’activation dans Communities
seo-description: Configure enablement features in Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 9%

---

# Fontionnalités Configuration de l’activation {#configuring-enablement-features}

## Présentation {#overview}

Les fonctions d’activation permettent de créer des [communautés d’activation](overview.md#enablement-community).

* Cette fonctionnalité nécessite des licences supplémentaires pour être utilisée dans un environnement de production.

L’utilisation des fonctionnalités d’activation requiert les éléments suivants :

Installation de :

* **SCORM**
SCORM (Sharable Content Object Reference Model) est un ensemble de normes et de spécifications pour l’apprentissage en ligne. SCORM définit également la manière dont le contenu peut être compressé dans un fichier ZIP transférable.

* **MySQL**
MySQL est une base de données relationnelle principalement utilisée pour le suivi SCORM et les données de création de rapports pour l’activation, ainsi que les tableaux pour le suivi de la progression vidéo. Le pack de fonctionnalités SCORM pour l’activation nécessite le pilote JDBC MySQL.

* **FFmpeg**
FFmpeg est une solution pour la conversion et la diffusion en continu d’audio et de vidéo. Lorsqu’elle est installée, elle est utilisée pour le transcodage correct de [Ressources vidéo](../../help/sites-authoring/default-components-foundation.md#video). Pour les communautés d’activation, elle est utilisée dans l’environnement de création pour obtenir des métadonnées pour les ressources chargées et générer une miniature à afficher lors de la mise en liste de la ressource.

Configuration de :

* **Chefs de communauté**
Pour les communautés d’activation, seuls les membres de 
`Community Enablement Managers` un groupe d’utilisateurs peut se voir attribuer le rôle de `*Community Site* Enablement Manager`, dont les autorisations peuvent inclure la création de contenu, les affectations et la gestion des membres dans l’environnement de publication.

Configuration facultative de :

* **Adobe Analytics**
L’intégration à Adobe Analytics ajoute des fonctions de création de rapports complètes et prend en charge l’ajout de la pulsation vidéo à Analytics.

* **Dispatcher**

## Étapes de configuration {#configuration-steps}

Vous trouverez ci-dessous les étapes nécessaires aux communautés d’activation.

Chaque étape renvoie à la documentation qui fournit les détails nécessaires.

**Sur toutes les instances d’auteur/de publication :**

1. **[installation du pilote JDBC pour MySQL ;](deploy-communities.md#jdbc-driver-for-mysql)**
Utiliser la console web (lots) : Installer *http://localhost:4502/system/console/bundles*
Installer *before* installation du package SCORM

1. **[installer le package SCORM ;](deploy-communities.md#scorm-package)**
Utilisation de Package Manager : 
*http://localhost:4502/crx/packmgr/*

**Sur n’importe quel serveur :**

1. **[installation de MySQL, MySQL Workbench](mysql.md)**

1. **[installation des bases de données MySQL ;](mysql.md#database-setup)**
Exécution des scripts SQL téléchargés à partir de l’instance d’auteur
\
   Utilisation de MySQL Workbench

**Sur la même instance d’auteur d’hébergement de serveur :**

1. **[install FFmpeg](ffmpeg.md)**

**Sur toutes les instances d’auteur/de publication :**

1. **[configuration du pool de connexions JDBC](mysql.md#configure-jdbc-connections)**
Utiliser la console web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[configurer le service du moteur SCORM ;](mysql.md#aem-communities-scormengine-service)**
Utiliser la console web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[configuration des filtres CSRF](mysql.md#adobe-granite-csrf-filter)**
Utiliser la console web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

**Sur l’instance d’auteur :**

1. (*facultatif*) **[configuration du service Analytics](analytics.md)**
Utilisez la console Outils, Déploiement, Cloud Services : 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configuration de FFmpeg](ffmpeg.md#configure-ffmpeg-transcoding-service)**
Utilisation de la console Processus/Modèles

1. **[Activation du service de tunnel](deploy-communities.md#tunnel-service-on-author)**
Utiliser la console web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[créer des administrateurs de communauté ;](users.md#creating-community-members)** Pour l’environnement de création, utilisez la console de sécurité de l’IU classique : *http://localhost:4502/useradmin*
créer un ou plusieurs utilisateurs avec le chemin d’accès = /home/users/community

   * Ajoutez des membres aux groupes suivants :

      * Chefs d’activation de la communauté
      * Administrateurs des communautés

## Dispatcher {#dispatcher}

Lorsque le déploiement inclut [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), pour que les fonctions d’activation fonctionnent correctement, la variable `clientheader`et `filter`Les sections doivent être modifiées. Voir [Configuration de Dispatcher pour Communities](dispatcher.md#enablement).
