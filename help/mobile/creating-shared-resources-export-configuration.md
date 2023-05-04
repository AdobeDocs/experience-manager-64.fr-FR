---
title: Création de la configuration de l'export des ressources partagées
seo-title: Creating Shared Resources Export Configuration
description: Consultez cette page pour en savoir plus sur l’exportation de ressources partagées à partir d’Adobe Experience Manager (AEM) en vue de leur chargement vers AEM Mobile.
seo-description: Follow this page to learn about exporting shared resources from Adobe Experience Manager (AEM) for upload to AEM Mobile.
uuid: 99b8ff94-8135-4643-a15b-aa6fb91f5401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 1edf6c76-ccb1-40b6-bdf6-924f1461cd28
exl-id: 92ee8c25-9f11-4743-a8e6-1f4986d09a6a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 8%

---

# Création de la configuration de l&#39;export des ressources partagées{#creating-shared-resources-export-configuration}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>**Prérequis**:
>
>Avant d’en savoir plus sur la création et la modification de ressources partagées, voir [Synchronisation du contenu](/help/mobile/mobile-ondemand-contentsync.md) pour comprendre les concepts de base.

Les utilisateurs d’AEM Mobile utilisent la synchronisation de contenu pour exporter du contenu en direct vers du contenu statique en vue de l’utiliser dans les applications mobiles. Cet export se produit lorsque le contenu est chargé vers Mobile On Demand Services à partir d’AEM Mobile.

La propriété ***dps-exportTemplate*** mentionné dans le tableau ci-dessus, définit le chemin d’accès aux configurations d’exportation de l’application. Définissez cette propriété pour créer et modifier des ressources partagées.

Les ressources suivantes décrivent l’exportation de ressources partagées à partir d’Adobe Experience Manager (AEM) pour chargement vers AEM Mobile.

Les ressources de HTML partagées permettent aux articles de partager des ressources de HTML qui, dans le cas contraire, auraient besoin d’être dupliquées pour tous les articles et peuvent inclure des icônes, des polices, du code JavaScript et des feuilles CSS.

La configuration de synchronisation de contenu se trouve à l’adresse **&lt;dps-exporttemplate>/dps-HTMLResources>** doit être configuré pour exporter tout le contenu nécessaire au rendu statique des propriétés sur l’appareil.

>[!CAUTION]
>
>Vous pouvez effectuer les étapes ci-dessous pour afficher les exemples de ressources partagées, uniquement si vous disposez des éléments suivants :
>
>* installation de l’exemple de contenu
>* exécution de l’instance AEM
>* aucun contexte personnalisé configuré ou port différent
>


Pour afficher un exemple de ressource partagée, procédez comme suit :

1. Ouvrez le CRXDE Lite sur votre serveur AEM.
1. Parcourir vers ce chemin *[/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)*, pour afficher les exemples de ressources partagées.

   Vous pouvez afficher toutes les propriétés requises pour créer vos ressources partagées, comme illustré dans la figure ci-dessous :

   ![chlimage_1-145](assets/chlimage_1-145.png)

>[!NOTE]
>
>Les ressources partagées doivent être chargées ou exportées vers AEM Mobile On-demand Services lorsque l’une des ressources partagées change.
