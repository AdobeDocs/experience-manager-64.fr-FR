---
title: Résolution des dépendances de fichier
seo-title: Résolution des dépendances de fichier
description: Comment résoudre les dépendances de fichier 3D telles que des fichiers de correspondance de texture lorsque la résolution automatique échoue.
seo-description: Comment résoudre les dépendances de fichier 3D telles que des fichiers de correspondance de texture lorsque la résolution automatique échoue.
uuid: 49cefabf-147b-4a78-90f3-0f2d6a8e8cae
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 05b7410b-82a1-4267-ac07-2edbc29e9ee8
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 47%

---


# Résolution des dépendances de fichier {#resolving-file-dependencies}

Les dépendances des principaux fichiers de modèle 3D, tels que les fichiers de mappage de texture, sont résolues automatiquement, lorsque cela s’avère possible. Pour exécuter cette fonctionnalité, AEM recherche dans les dossiers d’éléments voisins les fichiers ayant les mêmes noms que ceux figurant dans le fichier 3D. If one or more dependencies are unresolvable during the Creating preview processing stage, the asset&#39;s card displays the following red banner message in the **[!UICONTROL Card View]**:

![chlimage_1-124](assets/chlimage_1-124.png)

**Pour résoudre les dépendances** de fichiers :

1. In the **[!UICONTROL Card View]**, hover the pointer over the **[!UICONTROL Unresolved Dependencies]** banner message on the card, then tap the **[!UICONTROL Exclamation Point]** icon.

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. On the **[!UICONTROL Metadata Properties]** page, tap the **[!UICONTROL Dependencies]** tab.

   The files that AEM could not auto-resolve are listed under the **[!UICONTROL Original Paths]** column, in red.

1. Utilisez l’une ou plusieurs des méthodes suivantes :

   * **Rechercher et sélectionner les dépendances**. (Cette option suppose que vous ayez déjà chargé les fichiers de dépendance.)

      1. Tap the **[!UICONTROL File Browse]** icon to the left of the red path.
      1. On the **[!UICONTROL Select Content]** page, navigate to the missing file, then tap on the file&#39;s card to select it.
      1. In the upper-left corner of the **[!UICONTROL Select Content]** page, tap **[!UICONTROL Close]** (X icon) to return to the **[!UICONTROL View Properties]** page.
   * **Charger les dépendances**. (Cette option suppose que vous n’ayez pas encore chargé les fichiers manquants.)

      1. Notez les chemins et les noms de fichiers manquants.
      1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Fermer]**.

   After the files are uploaded return to **[!UICONTROL View Properties > Dependencies]** page. La nouvelle ressource chargée est désormais correctement répertoriée comme une ressource référencée.

   * **Ignorer les dépendances**.

      If a missing dependency is no longer needed, under the **[!UICONTROL Referenced Asset]** column, in the text field to the left of the missing file, type `n/a` so that AEM 3D ignores the file.



1. Near the upper-right corner of the **[!UICONTROL View Properties]** page, tap **[!UICONTROL Save]**.
1. Appuyez sur **[!UICONTROL Fermer]****[!UICONTROL pour revenir au mode Carte]**.

   La ressource est automatiquement traitée à nouveau avec les dépendances qui viennent d’être résolues.

