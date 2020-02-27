---
title: Appliquer des processus pour traiter vos ressources numériques
description: Découvrez comment appliquer des processus aux ressources, dossiers et collections dans AEM Assets pour traiter vos ressources numériques.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Application de processus à des ressources {#applying-workflows-to-assets}

L’application de workflow aux ressources numériques est identique à l’application de workflow aux pages d’un site web. Pour obtenir des informations complètes sur la création et l’utilisation de workflow dans AEM, consultez la section [Démarrage de workflow](../sites-authoring/workflows-participating.md).

Utilisez les workflow dans les ressources numériques pour activer les ressources ou créer des filigranes. La plupart des workflow destinés aux ressources sont automatiquement activés, comme le workflow permettant de créer automatiquement un rendu après la modification d’une image.

Si un workflow disponible dans l’interface utilisateur classique ne l’est pas dans l’interface utilisateur tactile, comme Demande d’activation et Demande de désactivation, consultez la section [Rendre les modèles de workflow disponibles dans l’interface utilisateur tactile](../sites-developing/workflows-models.md#make-workflow-models-available-in-touchui).

## Application d’un workflow à une ressource AEM {#applying-a-workflow-to-an-aem-asset}

Pour plus de détails sur l’application d’un workflow à une ressource AEM, reportez-vous à la section [Démarrage d’un workflow sur une ressource](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset).

## Application d’un workflow à plusieurs ressources {#applying-a-workflow-to-multiple-assets}

1. Dans la console Ressources, accédez à l’emplacement des ressources pour lesquelles vous souhaitez démarrer un workflow, puis sélectionnez les ressources.
1. Click the GlobalNav icon, and the choose **[!UICONTROL Timeline]** from the menu to display the timeline.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Click the **[!UICONTROL Actions]** (arrow) icon at the bottom.

   ![chlimage_1-137](assets/chlimage_1-137.png)

1. Cliquez sur **[!UICONTROL Démarrer le processus]**.
1. Dans la section **[!UICONTROL Démarrer le workflow]**, sélectionnez un modèle de workflow dans la liste.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Facultatif) Spécifiez le titre du workflow, qui peut permettre de référencer l’instance du workflow.
1. Cliquez sur **[!UICONTROL Démarrer]**, puis sur **[!UICONTROL Confirmer]** dans la boîte de dialogue. Le workflow s’exécute sur toutes les ressources sélectionnées.

## Application d’un workflow à plusieurs dossiers {#applying-a-workflow-to-multiple-folders}

La procédure à suivre pour appliquer un workflow à plusieurs dossiers est similaire à celle observée permettant d’appliquer un workflow à plusieurs ressources. Sélectionnez les dossiers dans la console Ressources et suivez les étapes 2-7 de la section [Application d’un workflow à plusieurs ressources](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Application d’un workflow à une collection {#applying-a-workflow-to-a-collection}

For details of applying a workflow to a collection, see [Running a workflow on a collection](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).
