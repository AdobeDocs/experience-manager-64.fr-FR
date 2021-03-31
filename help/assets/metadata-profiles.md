---
title: Utiliser des profils de métadonnées pour appliquer des métadonnées par défaut à tous les fichiers d’un dossier
description: Découvrez les profils de métadonnées pour les ressources. Apprenez à créer un profil de métadonnées et à l’appliquer aux ressources d’un dossier.
contentOwner: AG
feature: 'Métadonnées  '
role: Professionnel, administrateur
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 64%

---


# Profils de métadonnées {#metadata-profiles}

Un profil de métadonnées vous permet d’appliquer des métadonnées par défaut aux fichiers d’un dossier. Créez un Profil de métadonnées et appliquez-le à un dossier. Tout fichier que vous téléchargez ensuite vers le dossier hérite des métadonnées par défaut que vous avez configurées dans le Profil de métadonnées.

## Ajout d’un profil de métadonnées {#adding-a-metadata-profile}

1. Appuyez ou cliquez sur le logo de l’AEM et accédez à **[!UICONTROL Outils > Actifs > Profils de métadonnées]**, puis appuyez sur **[!UICONTROL Créer]**.
1. Saisissez un titre pour le profil de métadonnées, par exemple, Exemple de métadonnées, puis cliquez sur **[!UICONTROL Envoyer]**. Le **[!UICONTROL formulaire de modification]** du Profil de métadonnées s’affiche.

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. Cliquez sur un composant, puis configurez ses propriétés dans l’onglet **[!UICONTROL Paramètres]**. Cliquez par exemple sur le composant **[!UICONTROL Description]** et modifiez ses propriétés.

   ![chlimage_1-481](assets/chlimage_1-481.png)

   Modifiez les propriétés suivantes pour le composant **[!UICONTROL Description]** :

   * **[!UICONTROL Libellé]** du champ : Nom d’affichage de la propriété de métadonnées. Il est uniquement disponible à titre de référence.
   * **[!UICONTROL Associer à la propriété]** : La valeur de cette propriété fournit le chemin/nom relatif au noeud de ressources où elle est enregistrée dans le référentiel. La valeur doit toujours être début avec  `./` car elle indique que le chemin d’accès se trouve sous le noeud de la ressource.

   ![chlimage_1-482](assets/chlimage_1-482.png)

   La valeur que vous indiquez pour **[!UICONTROL Associer à la propriété]** est stockée en tant que propriété sous le nœud de métadonnées de la ressource. Par exemple, si vous spécifiez . `/jcr:content/metadata/dc:desc` comme nom pour **[!UICONTROL Associer à la propriété]**, AEM Assets stocke la valeur `dc:desc` comme nœud de métadonnées de la ressource.

   * **[!UICONTROL Valeur par défaut]** : utilisez cette propriété pour ajouter une valeur par défaut pour le composant des métadonnées. Par exemple, si vous indiquez « Ma description », cette valeur est affectée à la propriété `dc:desc` au niveau du nœud de métadonnées de la ressource.

   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Ajouter une valeur par défaut à une nouvelle propriété de métadonnées (qui n’existe pas déjà dans la . `/jcr:content/metadata` ) n’affiche pas par défaut la propriété et sa valeur sur la  **** page Propriétés de la ressource. Pour vue de la nouvelle propriété sur la page [!UICONTROL Propriétés] de la ressource, modifiez le formulaire de schéma correspondant.

1. (Facultatif) Ajoutez d’autres composants à **[!UICONTROL Modifier le formulaire]** à partir de l’onglet **[!UICONTROL Créer un formulaire]** et configurez leurs propriétés dans l’onglet **[!UICONTROL Paramètres]**. Les propriétés suivantes sont disponibles dans l’onglet **[!UICONTROL Créer un formulaire]** :

| Composant | Propriétés |
|---|---|
| [!UICONTROL En-tête de section] | Libellé de champ, <br> Description |
| [!UICONTROL Une seule ligne de texte] | Libellé de champ, <br> Faire correspondre à la propriété, <br> Valeur par défaut |
| [!UICONTROL Texte à plusieurs valeurs] | Libellé de champ, <br> Faire correspondre à la propriété, <br> Valeur par défaut |
| [!UICONTROL Nombre] | Libellé de champ, <br> Faire correspondre à la propriété, <br> Valeur par défaut |
| [!UICONTROL Date] | Libellé de champ, <br> Faire correspondre à la propriété, <br> Valeur par défaut |
| [!UICONTROL Balises standard] | Libellé de champ, <br> Faire correspondre à la propriété, <br> Valeur par défaut, <br> Description |

![chlimage_1-484](assets/chlimage_1-484.png)

1. Cliquez sur **[!UICONTROL Terminé]**. Le profil de métadonnées est ajouté à la liste des profils dans la page **[!UICONTROL Profils de métadonnées]**.

   ![chlimage_1-485](assets/chlimage_1-485.png)

## Copie d’un profil de métadonnées {#copying-a-metadata-profile}

1. Dans la page **[!UICONTROL Profils de métadonnées]**, sélectionnez un profil pour en faire une copie.

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. Cliquez sur **[!UICONTROL Copier]** dans la barre d’outils.
1. Dans la boîte de dialogue **[!UICONTROL Copier le Profil de métadonnées]**, entrez le titre de la nouvelle copie du profil.
1. Cliquez sur **[!UICONTROL Copier]**. Une copie du profil apparaît dans la liste des profils de la page **[!UICONTROL Profils de métadonnées]**.

   ![chlimage_1-487](assets/chlimage_1-487.png)

## Suppression d’un profil de métadonnées {#deleting-a-metadata-profile}

1. Dans la page **[!UICONTROL Profils de métadonnées]**, sélectionnez un profil à supprimer.

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. Cliquez sur **[!UICONTROL Supprimer les Profils de métadonnées]** dans la barre d’outils.
1. Dans la boîte de dialogue, cliquez sur **[!UICONTROL Supprimer]** pour confirmer l&#39;opération de suppression. Le profil de métadonnées est supprimé de la liste.

## Application d’un profil de métadonnées à des dossiers {#applying-a-metadata-profile-to-folders}

Lorsque vous affectez un profil de métadonnées à un dossier, tout sous-dossier hérite automatiquement du profil de son dossier parent. Cela signifie que vous ne pouvez affecter qu’un seul profil de métadonnées à un dossier. Nous vous conseillons donc de choisir avec la plus grande attention la structure du dossier dans lequel vous transférez, stockez, utilisez et archivez des ressources.

Si vous avez affecté un profil de métadonnées différent à un dossier, le nouveau profil remplace le précédent. Les ressources du dossier précédent restent inchangées. Le nouveau profil est appliqué aux ressources ajoutées ultérieurement au dossier.

Les dossiers auxquels un profil est affecté sont indiqués dans l’interface utilisateur par le nom du profil apparaissant dans le nom de la carte.

![chlimage_1-489](assets/chlimage_1-489.png)

Vous pouvez appliquer des profils de métadonnées à des dossiers spécifiques ou à l’ensemble des ressources.

### Application de profils de métadonnées à des dossiers spécifiques {#applying-metadata-profiles-to-specific-folders}

Vous pouvez appliquer un profil de métadonnées à un dossier à partir du menu **[!UICONTROL Outils]** ou, si vous êtes dans le dossier, à partir de **[!UICONTROL Propriétés]**. Cette section décrit comment appliquer des profils de métadonnées aux dossiers des deux manières.

Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

#### Application de profils de métadonnées à des dossiers à partir de l’interface utilisateur des profils {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Appuyez sur le logo AEM et accédez à **[!UICONTROL Outils > Ressources > Profils de métadonnées]**.
1. Sélectionnez le profil de métadonnées à appliquer à un ou à plusieurs dossiers.

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. Appuyez sur **[!UICONTROL Appliquer le profil de métadonnées au ou aux dossiers]** et sélectionnez ensuite le(s) dossier(s) que vous souhaitez utiliser pour recevoir les ressources récemment chargées. Ensuite, appuyez sur **[!UICONTROL Terminé]**. Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

#### Application de profils de métadonnées aux dossiers à partir des propriétés {#applying-metadata-profiles-to-folders-from-properties}

1. Dans le rail de gauche, appuyez sur **[!UICONTROL Ressources]**, puis accédez au dossier auquel vous souhaitez appliquer un profil de métadonnées.
1. Dans le dossier, appuyez sur la coche pour le sélectionner, puis sur **[!UICONTROL Propriétés]**.

1. Sélectionnez l’onglet **[!UICONTROL Profils de métadonnées]**, sélectionnez le profil dans le menu déroulant, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![chlimage_1-491](assets/chlimage_1-491.png)

   Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

### Application d’un profil de métadonnées à l’ensemble des ressources {#applying-a-metadata-profile-globally}

En plus d’appliquer un profil à un dossier, vous pouvez en appliquer un de façon globale, de sorte que tout contenu chargé dans AEM Assets soit traité par ce profil, indifféremment du dossier. Pour appliquer un profil de métadonnées globalement, procédez comme suit :

1. Utilisez l’une des méthodes suivantes :

   * Accédez à `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` et appliquez le profil approprié et appuyez ou cliquez sur **[!UICONTROL Enregistrer]**.

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * Accédez au nœud suivant de CRXDE Lite : `/content/dam/jcr:content`. Ajoutez la propriété `metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>` et appuyez sur **[!UICONTROL Enregistrer tout]**.

      ![chlimage_1-493](assets/chlimage_1-493.png)

## Supprimer un profil de métadonnées des dossiers {#removing-a-metadata-profile-from-folders}

Lorsque vous supprimez un profil de métadonnées d’un dossier, tout sous-dossier hérite automatiquement de la suppression du profil de son dossier parent. Cependant, le traitement des fichiers qui s’est produit dans les dossiers reste intact.

Vous pouvez supprimer un profil de métadonnées d’un dossier à partir du menu **[!UICONTROL Outils]** ou, si vous êtes dans le dossier, à partir de **[!UICONTROL Propriétés]**. Cette section décrit comment supprimer des profils de métadonnées des dossiers des deux manières.

### Supprimer les profils de métadonnées des dossiers via l’interface utilisateur des Profils {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

Pour supprimer un profil de métadonnées des dossiers via l’interface utilisateur des Profils, procédez comme suit :

1. Appuyez sur le logo AEM et accédez à **[!UICONTROL Outils > Ressources > Profils de métadonnées]**.
1. Sélectionnez le profil de métadonnées à supprimer d’un ou de plusieurs dossiers.
1. Appuyez sur **[!UICONTROL Supprimer le Profil de métadonnées du dossier(s)]** et sélectionnez le ou les dossiers à utiliser pour supprimer un profil, puis appuyez sur **[!UICONTROL Terminé]**.

   Le fait que le nom du profil n’apparaît plus sous celui du dossier indique que le profil de métadonnées n’est plus appliqué à un dossier.

### Supprimer les profils de métadonnées des dossiers au moyen de Propriétés {#removing-metadata-profiles-from-folders-via-properties}

1. Appuyez sur le logo AEM, puis accédez à **[!UICONTROL Ressources]** et au dossier duquel vous souhaitez supprimer un profil de métadonnées.
1. Dans le dossier, appuyez sur la coche pour le sélectionner, puis sur **[!UICONTROL Propriétés]**.
1. Sélectionnez l’onglet **[!UICONTROL Profils de métadonnées]**, puis **[!UICONTROL Aucun]** dans le menu déroulant. Appuyez sur **[!UICONTROL Enregistrer]**.

Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.
