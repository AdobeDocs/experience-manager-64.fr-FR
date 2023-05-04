---
title: Intégration de ressources à un flux d’activités
description: Décrit les fonctionnalités d’enregistrement de [!DNL Experience Manager] et comment configurer [!DNL Experience Manager] pour enregistrer des événements spécifiques.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 38%

---

# Intégration de ressources à un flux d’activités {#integrating-assets-with-activity-stream}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les utilisateurs d’Adobe Experience Manager Assets effectuent de nombreuses opérations, telles que la création, le chargement et la suppression de ressources. Ces actions peuvent être enregistrées de manière à fournir un historique de toutes les actions réalisées par un utilisateur. Cette section décrit les fonctionnalités d’enregistrement d’[!DNL Experience Manager] ainsi que la procédure de configuration d’[!DNL Experience Manager] pour enregistrer des événements spécifiques.

## Considérations de performance et comportement par défaut {#performance-considerations-and-default-behavior}

Cette intégration peut solliciter une puissance de processeur et un espace disque conséquents, par exemple lors d’opérations d’importation en bloc. Pour ces raisons, la variable [!DNL Experience Manager] L’intégration des ressources avec le flux d’activités est désactivée par défaut.

## Événements d’action pris en charge {#supported-action-events}

Il est possible de configurer l’enregistrement des événements suivants : 

* Licence acceptée (ACCEPTÉE)
* Ressource créée (ASSET_CREATED)
* Ressource déplacée (ASSET_MOVED)
* Ressource supprimée (ASSET_REMOVED)
* Licence refusée (REJECTED)
* Ressource téléchargée (TÉLÉCHARGÉE)
* Ressource versionnée (VERSIONED)
* Version des ressources restaurée (RESTAURÉE)
* Métadonnées de ressource mises à jour (METADATA_UPDATED)
* Ressource publiée sur un système externe (PUBLISHED_EXTERNAL)
* Mise à jour d’origine de la ressource (ORIGINAL_UPDATED)
* Rendu de la ressource mis à jour (RENDITION_UPDATED)
* Rendu de la ressource supprimé (RENDITION_REMOVED)
* Sous-ressource mise à jour (SUBASSET_UPDATED)
* Sous-ressource supprimée (SUBASSET_REMOVED)

## Configuration [!DNL Assets] Enregistrement d’événements {#configuring-aem-assets-events-recording}

Le [Console web](/help/sites-deploying/configuring-osgi.md) permet d’accéder au [!DNL Assets] Réglage de l’enregistreur d’événements. Pour configurer la variable [!DNL Assets] Enregistreur d’événements, procédez comme suit :

1. Accédez au **[!UICONTROL Console web]**

1. Cliquez sur **[!UICONTROL Configuration]**.

1. Double-cliquez sur **[!UICONTROL Enregistreur d’événements de la gestion des ressources numériques Day CQ]**. 

1. Cochez **[!UICONTROL Activer ce service]**.

1. Vérifiez les **[!UICONTROL types d’événement]** que vous souhaitez enregistrer dans le flux d’activités de l’utilisateur. 

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Lecture d’événements enregistrés {#reading-recorded-events}

Les événements enregistrés sont stockés en tant qu’activités. Vous pouvez les lire par programmation à l’aide du [API ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
