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


# Résolution des dépendances de fichier  {#resolving-file-dependencies}

Les dépendances des principaux fichiers de modèle 3D, tels que les fichiers de mappage de texture, sont résolues automatiquement, lorsque cela s’avère possible. Pour exécuter cette fonctionnalité, AEM recherche dans les dossiers d’éléments voisins les fichiers ayant les mêmes noms que ceux figurant dans le fichier 3D. Si une ou plusieurs dépendances ne peuvent pas être résolues au cours de l’étape de traitement Création de la prévisualisation, la carte du fichier affiche le message de bannière rouge suivant dans la **[!UICONTROL Vue de carte]** :

![chlimage_1-124](assets/chlimage_1-124.png)

**Pour résoudre les dépendances** de fichiers :

1. Dans la **[!UICONTROL Vue de carte]**, passez le pointeur sur le message de bannière **[!UICONTROL Dépendances non résolues]** de la carte, puis appuyez sur l’icône **[!UICONTROL Point d’exclamation]**.

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. Sur la page **[!UICONTROL Propriétés des métadonnées]**, appuyez sur l&#39;onglet **[!UICONTROL Dépendances]**.

   Les fichiers que AEM n&#39;a pas pu résoudre automatiquement sont répertoriés en rouge sous la colonne **[!UICONTROL Chemins d&#39;origine]**.

1. Utilisez l’une ou plusieurs des méthodes suivantes :

   * **Rechercher et sélectionner les dépendances**. (Cette option suppose que vous ayez déjà chargé les fichiers de dépendance.)

      1. Appuyez sur l&#39;icône **[!UICONTROL Parcourir le fichier]** située à gauche du chemin d&#39;accès rouge.
      1. Sur la page **[!UICONTROL Sélectionner le contenu]**, accédez au fichier manquant, puis appuyez sur la carte du fichier pour le sélectionner.
      1. Dans le coin supérieur gauche de la page **[!UICONTROL Sélectionner le contenu]**, appuyez sur **[!UICONTROL Fermer]** (icône X) pour revenir à la page **[!UICONTROL Propriétés de la Vue]**.
   * **Charger les dépendances**. (Cette option suppose que vous n’ayez pas encore chargé les fichiers manquants.)

      1. Notez les chemins et les noms de fichiers manquants.
      1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Fermer]**.

   Une fois les fichiers téléchargés, revenez à la page **[!UICONTROL Propriétés de la Vue > Dépendances]**. La nouvelle ressource chargée est désormais correctement répertoriée comme une ressource référencée.

   * **Ignorer les dépendances**.

      Si une dépendance manquante n’est plus nécessaire, dans la colonne **[!UICONTROL Ressource référencée]**, dans le champ de texte à gauche du fichier manquant, tapez `n/a` afin que AEM 3D ignore le fichier.



1. Près du coin supérieur droit de la page **[!UICONTROL Propriétés de la Vue]**, appuyez sur **[!UICONTROL Enregistrer]**.
1. Appuyez sur **[!UICONTROL Fermer]****[!UICONTROL pour revenir au mode Carte]**.

   La ressource est automatiquement traitée à nouveau avec les dépendances qui viennent d’être résolues.

