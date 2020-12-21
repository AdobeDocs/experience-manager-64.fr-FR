---
title: Fontionnalités Configuration de l’activation
seo-title: Fontionnalités Configuration de l’activation
description: Configuration des fonctions d’activation dans les communautés
seo-description: Configuration des fonctions d’activation dans les communautés
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 9%

---


# Fontionnalités Configuration de l’activation {#configuring-enablement-features}

## Présentation {#overview}

Les fonctions d&#39;activation permettent de créer des [communautés d&#39;activation](overview.md#enablement-community).

* Cette fonction nécessite une licence supplémentaire pour être utilisée dans un environnement de production.

L’utilisation des fonctions d’activation requiert les éléments suivants :

Installation de :

* **SCORMSharable Content Object Reference Model (SCORM) est un ensemble de normes et de spécifications pour l&#39;apprentissage en ligne.**
SCORM définit également comment le contenu peut être inclus dans un fichier ZIP transférable.

* ****
MySQLMySQL est une base de données relationnelle principalement utilisée pour le suivi SCORM et les données de rapports pour l&#39;activation, ainsi que des tables pour le suivi de la progression vidéo. Le pack de fonctionnalités d’activation SCORM nécessite le pilote JDBC MySQL.

* ****
FFmpegFFmpeg est une solution de conversion et de diffusion audio et vidéo en flux continu et, lorsqu’elle est installée, elle est utilisée pour le transcodage correct des fichiers [ ](../../help/sites-authoring/default-components-foundation.md#video)vidéo. Pour les communautés d’activation, elle est utilisée dans l’environnement d’auteur pour obtenir des métadonnées pour les ressources téléchargées et pour générer une miniature à afficher lors de la mise en liste de la ressource.

Configuration de :

* ****
Gestionnaires de communautéPour les communautés d&#39;activation, seuls les membres de 
`Community Enablement Managers` un groupe d’utilisateurs peut se voir attribuer le rôle de  `*Community Site* Enablement Manager`, dont les autorisations peuvent inclure la création de contenu, les affectations et la gestion des membres dans l’environnement de publication.

Configuration facultative de :

* **Adobe**
AnalyticsL’intégration à Adobe Analytics ajoute des fonctionnalités de rapports complètes et prend en charge l’ajout de la pulsation vidéo à Analytics.

* **Dispatcher**

## Étapes de configuration {#configuration-steps}

Voici les étapes nécessaires pour activer les communautés.

Chaque étape donne un lien vers la documentation qui fournit les détails nécessaires.

**Sur toutes les instances d’auteur/de publication :**

1. **[installer le pilote JDBC pour](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse Web Console (lots) : Installation de  *http://localhost:4502/system/console/*
bundlesInstallation  ** avant l’installation du pack SCORM

1. **[installer le](deploy-communities.md#scorm-package)**
package SCORMUtiliser Package Manager : 
*http://localhost:4502/crx/packmgr/*

**Sur n&#39;importe quel serveur :**

1. **[installation de MySQL, MySQL Workbench](mysql.md)**

1. **[installation de](mysql.md#database-setup)**
bases de données MySQLExécution de scripts SQL téléchargés depuis l’instance d’auteur
\
   Utiliser MySQL Workbench

**Sur le même serveur hébergeant l’instance d’auteur :**

1. **[installer FFmpeg](ffmpeg.md)**

**Sur toutes les instances d’auteur/de publication :**

1. **[configurer le](mysql.md#configure-jdbc-connections)**
pool de connexions JDBCUtilisez la console Web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[configurer le](mysql.md#aem-communities-scormengine-service)**
service du moteur SCORMUtiliser la console Web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[configurer des](mysql.md#adobe-granite-csrf-filter)**
filtres CSRFUtiliser la console Web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

**Sur l’instance d’auteur :**

1. (*facultatif*) **[configurer le service Analytics](analytics.md)**
Utiliser Outils, Déploiement, console Cloud Services : 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configurer](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegUtiliser la console Workflow/Modèles

1. **[activer Tunnel](deploy-communities.md#tunnel-service-on-author)**
ServiceUtiliser la console Web (configMgr) : 
*http://localhost:4502/system/console/configMgr*

1. **[créer des](users.md#creating-community-members)** administrateurs de communautéPour l’environnement auteur, utilisez la console de sécurité classique de l’interface utilisateur :  *http://localhost:4502/*
useradmincreate user(s) user(s) with path = /home/users/community

   * Ajoutez les membres aux groupes suivants :

      * Gestionnaires d’activation de la communauté
      * Administrateurs des communautés

## Dispatcher {#dispatcher}

Lorsque le déploiement inclut [AEM Répartiteur](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), pour que les fonctions d&#39;activation fonctionnent correctement, les sections `clientheader`et `filter`doivent être modifiées. Voir [Configuration du répartiteur pour les communautés](dispatcher.md#enablement).
