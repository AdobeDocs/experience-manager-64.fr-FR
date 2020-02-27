---
title: Utilisation des profils de métadonnées pour appliquer des métadonnées par défaut à tous les fichiers d’un dossier
description: Découvrez les profils de métadonnées pour les ressources. Apprenez à créer un profil de métadonnées et à l’appliquer aux ressources d’un dossier.
contentOwner: AG
translation-type: tm+mt
source-git-commit: af1955ab1fdcf16dd9a9d3ad36336e6c1aac9312

---


# Profils de métadonnées {#metadata-profiles}

Un profil de métadonnées vous permet d’appliquer des métadonnées par défaut aux fichiers d’un dossier. Créez un profil de métadonnées et appliquez-le à un dossier. Tout fichier que vous téléchargez ensuite vers le dossier hérite des métadonnées par défaut que vous avez configurées dans le profil de métadonnées.

## Ajout d’un profil de métadonnées {#adding-a-metadata-profile}

1. Tap or click the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**, and then tap **[!UICONTROL Create]**.
1. Saisissez un titre pour le profil de métadonnées, par exemple, Exemple de métadonnées, puis cliquez sur **[!UICONTROL Envoyer]**. The **[!UICONTROL Edit Form]** for the Metadata Profile is displayed.

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. Click a component and configure its properties in the **[!UICONTROL Settings]** tab. For example, click the **[!UICONTROL Description]** component and edit its properties.

   ![chlimage_1-481](assets/chlimage_1-481.png)

   Edit the following properties for the **[!UICONTROL Description]** component:

   * **[!UICONTROL Libellé]** du champ : Nom d’affichage de la propriété de métadonnées. Il est uniquement disponible à titre référence.
   * **[!UICONTROL Associer à la propriété]**: La valeur de cette propriété fournit le chemin/nom relatif au noeud de ressource où elle est enregistrée dans le référentiel. La valeur doit toujours commencer par `./` car elle indique que le chemin d’accès se trouve sous le noeud de la ressource.
   ![chlimage_1-482](assets/chlimage_1-482.png)

   La valeur que vous spécifiez pour **[!UICONTROL Associer à la propriété]** est stockée en tant que propriété sous le noeud de métadonnées du fichier. Par exemple, si vous spécifiez . `/jcr:content/metadata/dc:desc` comme nom de la propriété **[!UICONTROL Associer à la propriété]**, AEM Assets stocke la valeur `dc:desc` au noeud de métadonnées de la ressource.

   * **[!UICONTROL Valeur par défaut]** : utilisez cette propriété pour ajouter une valeur par défaut pour le composant des métadonnées. For example, if you specify &quot;My description&quot; then this value is assigned to the property `dc:desc` at the asset&#39;s metadata node.
   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Ajout d’une valeur par défaut à une nouvelle propriété de métadonnées (qui n’existe pas déjà dans la . `/jcr:content/metadata` ) n’affiche pas la propriété et sa valeur sur la page **[!UICONTROL Propriétés]** de la ressource par défaut. Pour afficher la nouvelle propriété sur la page [!UICONTROL Propriétés] de la ressource, modifiez le formulaire de schéma correspondant.

1. (Optional) Add more components to the **[!UICONTROL Edit Form]** from the **[!UICONTROL Build Form]** tab, and configure their properties in the **[!UICONTROL Settings]** tab. The following properties are available from the **[!UICONTROL Build Form]** tab:

| Component | Propriétés |
|---|---|
| [!UICONTROL En-tête de section] | Libellé de champ, <br> description |
| [!UICONTROL Une seule ligne de texte] | Libellé de champ, <br> Associer à la propriété, <br> Valeur par défaut |
| [!UICONTROL Texte à plusieurs valeurs] | Libellé de champ, <br> Associer à la propriété, <br> Valeur par défaut |
| [!UICONTROL Nombre] | Libellé de champ, <br> Associer à la propriété, <br> Valeur par défaut |
| [!UICONTROL Date] | Libellé de champ, <br> Associer à la propriété, <br> Valeur par défaut |
| [!UICONTROL Balises standard] | Libellé de champ, <br> Associer à la propriété, <br> Valeur par défaut, <br> Description |

![chlimage_1-484](assets/chlimage_1-484.png)

1. Click **[!UICONTROL Done]**. The metadata profile is added to the list of profiles in the **[!UICONTROL Metadata Profiles]** page.

   ![chlimage_1-485](assets/chlimage_1-485.png)

## Copie d’un profil de métadonnées {#copying-a-metadata-profile}

1. From the **[!UICONTROL Metadata Profiles]** page, select a profile to make a copy of it.

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. Click **[!UICONTROL Copy]** from the toolbar.
1. In the **[!UICONTROL Copy Metadata Profile]** dialog, enter a title for the new copy of the profile.
1. Cliquez sur **[!UICONTROL Copier]**. A copy of the profile appears in the list of profiles in the **[!UICONTROL Metadata Profiles]** page.

   ![chlimage_1-487](assets/chlimage_1-487.png)

## Suppression d’un profil de métadonnées {#deleting-a-metadata-profile}

1. From the **[!UICONTROL Metadata Profiles]** page, select a profile to delete.

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. Click **[!UICONTROL Delete Metadata Profiles]** in the toolbar.
1. In the dialog box, click **[!UICONTROL Delete]** to confirm the delete operation. Le profil de métadonnées est supprimé de la liste.

## Apply a metadata profile to folders {#applying-a-metadata-profile-to-folders}

Lorsque vous affectez un profil de métadonnées à un dossier, tout sous-dossier hérite automatiquement du profil de son dossier parent. Cela signifie que vous ne pouvez affecter qu’un seul profil de métadonnées à un dossier. Nous vous conseillons donc de choisir avec la plus grande attention la structure du dossier dans lequel vous transférez, stockez, utilisez et archivez des ressources.

Si vous avez affecté un profil de métadonnées différent à un dossier, le nouveau profil remplace le précédent. Les ressources du dossier précédent restent inchangées. Le nouveau profil est appliqué aux ressources ajoutées ultérieurement au dossier.

Les dossiers auxquels un profil est affecté sont indiqués dans l’interface utilisateur par le nom du profil apparaissant dans le nom de la carte.

![chlimage_1-489](assets/chlimage_1-489.png)

Vous pouvez appliquer des profils de métadonnées à des dossiers spécifiques ou à l’ensemble des ressources.

### Apply metadata profiles to specific folders {#applying-metadata-profiles-to-specific-folders}

Vous pouvez appliquer un profil de métadonnées à un dossier depuis le menu **[!UICONTROL Outils]** ou, si vous vous trouvez dans le dossier, depuis **[!UICONTROL Propriétés]**. Cette section décrit comment appliquer des profils de métadonnées aux dossiers des deux manières.

Les dossiers auxquels un profil est déjà affecté sont indiqués par l’affichage du nom du profil directement sous le nom du dossier.

#### Apply metadata profiles to folders from Profiles user interface {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Sélectionnez le profil de métadonnées à appliquer à un ou à plusieurs dossiers.

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. Tap **[!UICONTROL Apply Metadata Profile to Folder(s)]** and select the folder or multiple folders you want use to receive the newly uploaded assets and tap **[!UICONTROL Done]**. Les dossiers auxquels un profil est déjà affecté sont indiqués par l’affichage du nom du profil directement sous le nom du dossier.

#### Apply metadata profiles to folders from Properties {#applying-metadata-profiles-to-folders-from-properties}

1. In the left rail, tap **[!UICONTROL Assets]** then navigate to the folder that you want to apply a metadata profile to.
1. On the folder, tap the check mark to select it, then tap  **[!UICONTROL Properties]**.

1. Sélectionnez l’onglet **[!UICONTROL Profils de métadonnées]**, sélectionnez le profil dans le menu déroulant, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![chlimage_1-491](assets/chlimage_1-491.png)

   Les dossiers auxquels un profil est déjà affecté sont indiqués par l’affichage du nom du profil directement sous le nom du dossier.

### Apply a metadata profile globally {#applying-a-metadata-profile-globally}

En plus d’appliquer un profil à un dossier, vous pouvez également en appliquer un de façon globale, de sorte que tout contenu transféré dans AEM Assets soit traité par ce profil, indifféremment du dossier. Pour appliquer un profil de métadonnées globalement, procédez comme suit :

1. Utilisez l’une des méthodes suivantes :

   * Accédez à `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` et appliquez le profil approprié, puis appuyez ou cliquez sur **[!UICONTROL Enregistrer]**.

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * Navigate to CRXDE Lite to the following node: `/content/dam/jcr:content`. Ajoutez la propriété `metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>` et appuyez sur **[!UICONTROL Enregistrer tout]**.

      ![chlimage_1-493](assets/chlimage_1-493.png)

## Remove a metadata profile from folders {#removing-a-metadata-profile-from-folders}

Lorsque vous supprimez un profil de métadonnées d’un dossier, tout sous-dossier hérite automatiquement de la suppression du profil de son dossier parent. Cependant, le traitement des fichiers qui s’est produit dans les dossiers reste intact.

Vous pouvez supprimer un profil de métadonnées d’un dossier depuis le menu **[!UICONTROL Outils]** ou, si vous vous trouvez dans le dossier, depuis **[!UICONTROL Propriétés]**. Cette section décrit comment supprimer des profils de métadonnées des dossiers des deux manières.

### Remove metadata profiles from folders via Profiles user interface {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

Pour supprimer un profil de métadonnées des dossiers via l’interface utilisateur Profils, procédez comme suit :

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Sélectionnez le profil de métadonnées à supprimer d’un ou de plusieurs dossiers.
1. Tap **[!UICONTROL Remove Metadata Profile from Folder(s)]** and select the folder or multiple folders you want use to remove a profile from, then tap **[!UICONTROL Done]**.

   Le fait que le nom du profil n’apparaît plus sous celui du dossier indique que le profil de métadonnées n’est plus appliqué à un dossier.

### Remove metadata profiles from folders by way of Properties {#removing-metadata-profiles-from-folders-via-properties}

1. Tap the AEM logo and navigate **[!UICONTROL Assets]** and then to the folder that you want to remove an metadata profile from.
1. On the folder, tap the check mark to select it, then tap **[!UICONTROL Properties]**.
1. Sélectionnez l’onglet Profils **[!UICONTROL de]** métadonnées, puis **[!UICONTROL Aucun]** dans le menu déroulant. Appuyez sur **[!UICONTROL Enregistrer]**.

Les dossiers auxquels un profil est déjà affecté sont indiqués par l’affichage du nom du profil directement sous le nom du dossier.
