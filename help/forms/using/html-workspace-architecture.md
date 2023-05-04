---
title: Architecture de l’espace de travail AEM Forms
seo-title: AEM Forms Workspace Architecture
description: Informations conceptuelles et présentation de l’architecture de l’espace de travail AEM Forms LiveCycle.
seo-description: Conceptual information and overview of the architecture of LiveCycle AEM Forms workspace.
uuid: e1a48452-ed44-4ea7-ba38-d961c8faafa5
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c3a312fb-f684-477d-916d-2d3c99aa7607
exl-id: 30bde8d6-7959-4e4b-a6f4-faf52444e67a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 32%

---

# Architecture de l’espace de travail AEM Forms {#aem-forms-workspace-architecture}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’espace de travail AEM Forms est une application web hébergée sur CRX™. Lorsque l’espace de travail est ouvert dans un navigateur, une ressource CRX est accessible et l’application est rendue en tant que page de HTML dans le navigateur.

L’application accède au serveur AEM Forms sur les points d’entrée REST pour effectuer les opérations suivantes :

* Récupération des tâches utilisateur, des points de départ de processus, de l’historique des processus et des informations sur l’utilisateur
* Exécution d’une action sur les tâches
* Tâches de requête dans la base de données
* Mise à jour des préférences utilisateur, etc.

Le serveur AEM Forms accède à la base de données AEM Forms via JDBC. La base de données conserve les tâches, les processus et leurs instances, les utilisateurs et les informations associées.

L’espace de travail AEM Forms est constitué de composants modulaires JavaScript™ qui peuvent être personnalisés individuellement et réutilisés dans d’autres applications web. Les composants sont basés sur BackBone, une bibliothèque JavaScript qui fournit une structure aux applications web. Un article détaillé décrivant l’interaction des composants avec BackBone est [here](/help/forms/using/backbone-interaction.md). L’organisation des composants dans la structure de dossiers CRX est présentée dans la section [this](/help/forms/using/folder-structure.md) article.

Packages fournis pour l’espace de travail AEM Forms :

* `adobe-lc-workspace-pkg-<version>.zip` : il s’agit du package CRX, c’est-à-dire qu’il peut être déployé dans CRX en utilisant Package Manager.
* `adobe-lc-workspace-<version>-src.zip` : il s’agit d’un fichier d’archive contenant le code complet de l’espace de travail AEM Forms et les scripts permettant de créer les packages de déploiement (Ship, Debug et Dev).
