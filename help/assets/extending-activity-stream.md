---
title: Intégration des ressources avec Flux d’activités
description: Décrit les fonctionnalités d’enregistrement de [!DNL Experience Manager] et comment configurer [!DNL Experience Manager] pour enregistrer des événements spécifiques.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 66%

---

# Intégration des ressources avec Flux d’activités {#integrating-assets-with-activity-stream}

Les utilisateurs d’Adobe Experience Manager Assets effectuent de nombreuses opérations, telles que la création, le chargement et la suppression de ressources. Ces actions peuvent être enregistrées de manière à fournir un historique de toutes actions réalisées par un utilisateur. Cette section décrit les fonctionnalités d’enregistrement de [!DNL Experience Manager] et comment configurer [!DNL Experience Manager] afin d’enregistrer des événements spécifiques.

## Performances et comportement par défaut {#performance-considerations-and-default-behavior}

Cette intégration peut solliciter une puissance de processeur et un espace disque conséquents, par exemple lors d’opérations d’importation en bloc. Pour ces raisons, la variable [!DNL Experience Manager] L’intégration des ressources avec le flux d’activités est désactivée par défaut.

## Événements d’actions pris en charge {#supported-action-events}

Il est possible de configurer l’enregistrement des événements suivants : 

* Licence acceptée (ACCEPTED)
* Ressource créée (ASSET_CREATED)
* Ressource déplacée (ASSET_MOVED)
* Ressource supprimée (ASSET_REMOVED)
* Licence rejetée (REJECTED)
* Ressource téléchargée (DOWNLOADED)
* Version de la ressource (VERSIONED)
* Version de la ressource restaurée (RESTORED)
* Métadonnées de la ressource mises à jour (METADATA_UPDATED)
* Ressource publiée dans un système externe (PUBLISHED_EXTERNAL)
* Version originale de la ressource mise à jour (ORIGINAL_UPDATED)
* Rendu de la ressource mis à jour (RENDITION_UPDATED)
* Rendu de la ressource supprimé (RENDITION_REMOVED)
* Sous-ressource mise à jour (SUBASSET_UPDATED)
* Sous-ressource supprimée (SUBASSET_REMOVED)

## Configuration [!DNL Assets] Enregistrement d’événements {#configuring-aem-assets-events-recording}

Le [Console web](/help/sites-deploying/configuring-osgi.md) permet d’accéder au [!DNL Assets] Réglage de l’enregistreur d’événements. Pour configurer la variable [!DNL Assets] Enregistreur d’événements, procédez comme suit :

1. Accédez à la **[!UICONTROL console web]**.

1. Cliquez sur **[!UICONTROL Configuration]**.

1. Double-cliquez sur **[!UICONTROL Enregistreur d’événements de la gestion des actifs numériques Day CQ]**. 

1. Cochez **[!UICONTROL Activer ce service]**.

1. Vérifiez les **[!UICONTROL types d’événement]** que vous souhaitez enregistrer dans le flux d’activités de l’utilisateur. 

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Lecture des événements enregistrés {#reading-recorded-events}

Les événements enregistrés sont stockés en tant qu’activités. Vous pouvez les consulter par programmation en utilisant [l’API ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html). 
