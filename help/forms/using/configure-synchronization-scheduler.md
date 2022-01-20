---
title: Configuration du planificateur de synchronisation
seo-title: Configuring the synchronization scheduler
description: Apprenez à migrer et à synchroniser des ressources, à configurer le planificateur de synchronisation et à organiser les ressources dans des dossiers.
seo-description: Learn how to migrate and sync assets, configure sync scheduler, and use folders to arrange assets.
uuid: a6445b45-9c1c-4483-a32e-453648c488c5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 2c8cea3c-8d8b-41d4-8ef9-a0ada8f86be6
role: Admin
exl-id: 7f1c4bac-accf-43e4-9439-89c5420d50f2
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 77%

---

# Configuration du planificateur de synchronisation {#configuring-the-synchronization-scheduler}

Par défaut, le planificateur de synchronisation s’exécute toutes les 3 minutes pour synchroniser toutes les ressources modifiées et mises à jour dans le référentiel via LiveCycle Workbench 11. Les applications contenant des formulaires ou des ressources sont visibles dans l’interface utilisateur d’AEM Forms une fois le processus de synchronisation terminé.

## Modifier l’intervalle du planificateur de synchronisation {#change-interval-of-the-synchronization-scheduler}

Suivez les étapes suivantes pour modifier l’intervalle du planificateur de synchronisation :

1. Connectez-vous au Configuration Manager d’AEM. L’URL de Configuration Manager est la suivante : `https://[Server]:[Port]/lc/system/console/configMgr`

1. Recherchez et ouvrez le lot **FormsManagerConfiguration.**

1. Choisissez une nouvelle valeur pour l’option de fréquence du **planificateur de synchronisation**.

   Les unités de fréquence se comptent en minutes. Par exemple, pour configurer une exécution du planificateur toutes les 60 minutes, entrez 60.

## Synchronisation des ressources {#synchronizing-assets}

Vous pouvez utiliser l’option **Synchroniser les ressources à partir du référentiel** pour synchroniser manuellement les ressources. Effectuez les opérations suivantes pour synchroniser manuellement les actifs :

1. Connectez-vous à AEM Forms. L’URL par défaut est `https://[Server]:[Port]/lc/aem/forms/`.

   ![Interface utilisateur d’AEM Forms](assets/aem_forms_ui.png)

   **Figure :** *Interface utilisateur d’AEM Forms*

1. Cliquez sur le bouton ![aem6forms_sync](assets/aem6forms_sync.png) dans la barre d’outils. Si vous ne disposez d’aucune ressource dans le dernier chemin configuré, la boîte de dialogue s’affiche comme ci-dessous. Cliquez sur **Démarrer** pour lancer la synchronisation.

   ![Boîte de dialogue de synchronisation](assets/migrate-and-syncronize.png)

   **Figure :** *Boîte de dialogue de synchronisation*

## Dépannage des erreurs de synchronisation {#troubleshooting-synchronization-error}

Vous pouvez créer de nouvelles applications dans le Concepteur de flux de travaux (LiveCycle Workbench).

Si l’application nouvellement créée et un dossier situé à /content/dam/formsanddocuments portent le même nom, une erreur &quot;*Une ressource portant le même nom que cette application existe déjà au niveau racine.*&quot; est consigné.

Pour résoudre le conflit, renommez l’application puis synchronisez manuellement les actifs.

![Conflits dans la boîte de dialogue de synchronisation des ressources](assets/sync-conflict.png)

**Figure :** *Conflits dans la boîte de dialogue de synchronisation des ressources*
