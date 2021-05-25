---
title: Fontionnalités Configuration de l’activation
seo-title: Fontionnalités Configuration de l’activation
description: Configuration des fonctionnalités d’activation dans Communities
seo-description: Configuration des fonctionnalités d’activation dans Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Administrator
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 9%

---

# Fontionnalités Configuration de l’activation {#configuring-enablement-features}

## Présentation {#overview}

Les fonctionnalités d’activation permettent de créer des [communautés d’activation](overview.md#enablement-community).

* Cette fonctionnalité nécessite des licences supplémentaires pour être utilisée dans un environnement de production.

L’utilisation des fonctionnalités d’activation requiert les éléments suivants :

Installation de :

* ****
SCORMSharable Content Object Reference Model (SCORM) est un ensemble de normes et de spécifications pour l’e-learning. SCORM définit également la manière dont le contenu peut être compressé dans un fichier ZIP transférable.

* ****
MySQLMySQL est une base de données relationnelle principalement utilisée pour le suivi SCORM et les données de création de rapports pour l’activation, ainsi que des tableaux pour le suivi de la progression vidéo. Le pack de fonctionnalités SCORM pour l’activation nécessite le pilote JDBC MySQL.

* ****
FFmpegFFmpeg est une solution permettant de convertir et de diffuser en continu des fichiers audio et vidéo. Lorsqu’elle est installée, elle est utilisée pour le transcodage correct des ressources  [vidéo](../../help/sites-authoring/default-components-foundation.md#video). Pour les communautés d’activation, elle est utilisée dans l’environnement de création pour obtenir des métadonnées pour les ressources chargées et générer une miniature à afficher lors de la mise en liste de la ressource.

Configuration de :

* ****
Chefs de communautéPour les communautés d’activation, seuls les membres de 
`Community Enablement Managers` le groupe d’utilisateurs peut se voir attribuer le rôle de  `*Community Site* Enablement Manager`, dont les autorisations peuvent inclure la création de contenu, les affectations et la gestion des membres dans l’environnement de publication.

Configuration facultative de :

* **L’intégration**
d’Adobe Analytics à Adobe Analytics ajoute des fonctionnalités de création de rapports complètes et prend en charge l’ajout de la pulsation vidéo à Analytics.

* **Dispatcher**

## Étapes de configuration {#configuration-steps}

Vous trouverez ci-dessous les étapes nécessaires aux communautés d’activation.

Chaque étape renvoie à la documentation qui fournit les détails nécessaires.

**Sur toutes les instances d’auteur/de publication :**

1. **[installez le pilote JDBC pour la console web](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse (lots) : Installez  *http://localhost:4502/system/console/*
bundlesInstallez  ** avant d’installer le package SCORM.

1. **[installez le](deploy-communities.md#scorm-package)**
package SCORM. Utilisez Package Manager : 
*http://localhost:4502/crx/packmgr/*

**Sur n’importe quel serveur :**

1. **[installation de MySQL, MySQL Workbench](mysql.md)**

1. **[installation des](mysql.md#database-setup)**
bases de données MySQLExécution de scripts SQL téléchargés à partir de l’instance d’auteur
\
   Utilisation de MySQL Workbench

**Sur la même instance d’auteur d’hébergement de serveur :**

1. **[install FFmpeg](ffmpeg.md)**

**Sur toutes les instances d’auteur/de publication :**

1. **[configurer les connexions JDBC](mysql.md#configure-jdbc-connections)**
poolUtilisez la console web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[configurer le moteur SCORM](mysql.md#aem-communities-scormengine-service)**
serviceUtiliser la console web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[configurer les](mysql.md#adobe-granite-csrf-filter)**
filtres CSRFUtilisez la console web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

**Sur l’instance d’auteur :**

1. (*optionnel*) **[configurer le service Analytics](analytics.md)**
Utilisez la console Outils, Déploiement, Cloud Services : 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configuration de la console](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegUse Workflow/Models

1. **[Activez Tunnel](deploy-communities.md#tunnel-service-on-author)**
ServiceUse Web Console (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[créer des](users.md#creating-community-members)** administrateurs de communauté Pour l’environnement de création, utilisez la console de sécurité de l’IU classique :  *http://localhost:4502/*
useradmincreate user(s) with path = /home/users/community

   * Ajoutez des membres aux groupes suivants :

      * Chefs d’activation de la communauté
      * Administrateurs des communautés

## Dispatcher {#dispatcher}

Lorsque le déploiement comprend [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), pour que les fonctionnalités d’activation fonctionnent correctement, les sections `clientheader`et `filter`doivent être modifiées. Voir [Configuration de Dispatcher pour Communities](dispatcher.md#enablement).
