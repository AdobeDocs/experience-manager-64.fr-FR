---
title: Résolution des dépendances de fichier
seo-title: Résolution des dépendances de fichier
description: Les dépendances des principaux fichiers de modèle 3D, tels que les fichiers de mappage de texture, sont résolues automatiquement, lorsque cela s’avère possible. Pour exécuter cette fonctionnalité, AEM recherche dans les dossiers d’éléments voisins les fichiers ayant les mêmes noms que ceux figurant dans le fichier 3D.
seo-description: Les dépendances des principaux fichiers de modèle 3D, tels que les fichiers de mappage de texture, sont résolues automatiquement, lorsque cela s’avère possible. Pour exécuter cette fonctionnalité, AEM recherche dans les dossiers d’éléments voisins les fichiers ayant les mêmes noms que ceux figurant dans le fichier 3D.
uuid: b1b83cb7-b6e5-4417-9a53-b6d8bcf8d2e0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 14754023-e7c4-4dc5-a9d8-408b81861d95
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 60%

---


# Résolution des dépendances de fichiers{#resolving-file-dependencies}

Les dépendances des principaux fichiers de modèle 3D, tels que les fichiers de mappage de texture, sont résolues automatiquement, lorsque cela s’avère possible. Pour exécuter cette fonctionnalité, AEM recherche dans les dossiers d’éléments voisins les fichiers ayant les mêmes noms que ceux figurant dans le fichier 3D. Si une ou plusieurs dépendances ne peuvent pas être résolues au cours de l’étape de traitement Création de la prévisualisation, la carte du fichier affiche le message de bannière rouge suivant dans la [!UICONTROL Vue de carte] :

![chlimage_1-189](assets/chlimage_1-189.png)

**Pour résoudre les dépendances** de fichiers :

1. Dans la **[!UICONTROL Vue de carte]**, placez le pointeur sur le message de bannière **[!UICONTROL Dépendances non résolues]** sur la carte, puis appuyez sur l’icône du point d’exclamation.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. Sur la page Propriétés des métadonnées, appuyez sur l’onglet **[!UICONTROL Dépendances]**.

   Les fichiers qu’AEM n’a pas pu résoudre sont répertoriés sous la colonne Chemins d’origine, en rouge.

1. Utilisez l’une ou plusieurs des méthodes suivantes :

   * **[!UICONTROL Rechercher et sélectionner les dépendances]**. (Cette option suppose que vous ayez déjà chargé les fichiers de dépendance.)

      1. Appuyez sur l&#39;icône **[!UICONTROL Parcourir le fichier]** située à gauche du chemin d&#39;accès rouge.
      1. Sur la page **[!UICONTROL Sélectionner le contenu]**, accédez au fichier manquant, puis appuyez sur la carte du fichier pour le sélectionner.
      1. Dans le coin supérieur gauche de la page **[!UICONTROL Sélectionner le contenu]**, appuyez sur **[!UICONTROL Fermer]** (icône X) pour revenir à la page **[!UICONTROL Propriétés de la Vue]**.
   * **[!UICONTROL Charger les dépendances]**. (Cette option suppose que vous n’ayez pas encore chargé les fichiers manquants.)

      1. Notez les chemins et les noms de fichiers manquants.
      1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Fermer]**.

   Une fois les fichiers téléchargés, revenez à la page **[!UICONTROL Propriétés de la Vue > Dépendances]**. La nouvelle ressource chargée est désormais correctement répertoriée comme une ressource référencée.

   * **[!UICONTROL Ignorer les dépendances]**.

      Si une dépendance manquante n’est plus nécessaire, dans la colonne **[!UICONTROL Ressource référencée]**, dans le champ de texte à gauche du fichier manquant, tapez `n/a` afin que AEM 3D ignore le fichier.



1. Près du coin supérieur droit de la page **[!UICONTROL Propriétés de la Vue]**, appuyez sur **[!UICONTROL Enregistrer]**.
1. Appuyez sur **[!UICONTROL Fermer]****[!UICONTROL pour revenir au mode Carte]**.

   La ressource est automatiquement traitée à nouveau avec les dépendances qui viennent d’être résolues.

