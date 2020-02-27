---
title: Schémas de métadonnées
description: 'Le schéma de métadonnées définit la mise en page de la page de propriétés, ainsi que les propriétés de métadonnées affichées pour les ressources. Apprenez à créer un schéma de métadonnées personnalisé, à le modifier et à l’appliquer aux ressources.  '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 57952323a3ae0990232506d551b91b724f830f20

---


# Schémas de métadonnées {#metadata-schemas}

Dans Adobe Experience Manager (AEM) Assets, un schéma de métadonnées définit la disposition de la page de propriétés et les propriétés de métadonnées affichées pour les ressources qui utilisent ce schéma particulier. Les propriétés de métadonnées incluent le titre, la description, les types MIME, les balises, etc.

Vous pouvez utiliser l’éditeur de formulaires de schéma de métadonnées pour modifier des schémas existants ou ajouter des schémas de métadonnées personnalisés.

1. To view the properties page for an asset, click or tap the **[!UICONTROL View Properties]** from **[!UICONTROL Quick Actions]** on the asset tile in Card view.

   ![chlimage_1-170](assets/chlimage_1-170.png)

   Alternatively, select an asset and then click or tap the **[!UICONTROL Properties]** icon from the toolbar.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Modifiez les propriétés de métadonnées modifiables sous les différents onglets.

   ![chlimage_1-172](assets/chlimage_1-172.png)

   Pour modifier le type MIME d’une ressource, utilisez un formulaire de schéma de métadonnées personnalisé ou modifiez un formulaire existant. Voir [Modification d’un formulaire de schéma de métadonnées](metadata-schemas.md#editing-metadata-schema-forms) pour plus d’informations. Si vous modifiez le schéma de métadonnées d’un certain type MIME, la disposition de la page des propriétés des ressources de ce type MIME et tous les sous-types de ressources sont modifiés. For example, modifying a `jpeg` schema under `default/image` only modifies the metadata layout (asset properties) for assets with MIME type `IMAGE/JPEG`. Si vous modifiez le schéma default, les modifications changent toutefois la disposition des métadonnées pour tous les types de ressources.

1. Pour afficher la liste des formulaires/modèles, cliquez sur le logo AEM, puis accédez à **[!UICONTROL Outils > Ressources > Schémas de métadonnées]**.

   ![chlimage_1-173](assets/chlimage_1-173.png)

   AEM fournit les modèles prêts à l’emploi suivants :

   * **default** : le formulaire de schéma de métadonnées de base pour les ressources.
   Les formulaires enfants suivants héritent des propriétés du formulaire par défaut :

   i. **image**: Schema form for assets with the MIME type `image`, for example, `image/jpeg`, `image/png`, and so on.

   Le formulaire « image » possède les modèles de formulaire enfant suivants :

   a. **jpeg**: Schema form for assets with sub type jpeg.

   b. **tiff**: Schema form for the assets with sub type TIFF.

   ii. **application**: Formulaire de schéma pour les ressources avec une application de type MIME, par exemple `application/pdf`, `application/zip`, etc.

   a. **pdf**: Schema form for assets with sub type PDF.

   iii. **vidéo**: Formulaire de schéma pour les fichiers avec une vidéo de type MIME, comme `video/avi`, `video/mp4` etc.

   * **collection**: Formulaire de schéma pour les collections
   * **** contentfragment : Formulaire de schéma pour les fragments de contenu
   * **formulaires**: Ce formulaire de schéma concerne [Adobe Experience Manager Forms](/help/forms/home.md)


>[!NOTE]
>
>Pour afficher les formulaires enfants d’un formulaire de schéma, cliquez/appuyez sur le nom de ce dernier.

## Ajout d’un formulaire de schéma de métadonnées {#adding-a-metadata-schema-form}

1. To add a custom template to the list, click **[!UICONTROL Create]** from the toolbar.

   >[!NOTE]
   >
   >Les modèles non modifiés affichent une icône de verrouillage avant eux.  Si vous personnalisez l’un des modèles, l’icône de verrouillage précédant le modèle disparaît.

1. In the dialog, enter the title of the schema form and click **[!UICONTROL Create]** to complete the form creation process.

   ![chlimage_1-174](assets/chlimage_1-174.png)

## Modification des formulaires de schéma de métadonnées {#editing-metadata-schema-forms}

Vous pouvez modifier un formulaire de schéma de métadonnées existant ou récemment ajouté. Le formulaire de schéma de métadonnées inclut les éléments suivants :

* Onglets
* Éléments de formulaire dans des onglets

Vous pouvez associer ou configurer ces éléments de formulaire dans un champ au sein d’un nœud de métadonnées dans le référentiel CRX.

Vous pouvez ajouter de nouveaux onglets ou éléments de formulaire au formulaire de schéma de métadonnées. Les onglets et les éléments de formulaire dérivés du parent sont à l’état verrouillé. Vous ne pouvez pas les modifier au niveau des enfants.

1. In the **[!UICONTROL Schema Forms]** page, select the check box before a form and then click **[!UICONTROL Edit]** on the toolbar.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. Dans la page **[!UICONTROL Éditeur de schéma de métadonnées]**, personnalisez la page de propriétés de la ressource en faisant glisser un ou plusieurs composants de la liste des types de composants dans l’onglet **[!UICONTROL Créer le formulaire]** vers l’onglet **[!UICONTROL De base]**.

   ![chlimage_1-176](assets/chlimage_1-176.png)

1. Pour configurer un composant, sélectionnez-le et modifiez ses propriétés dans l’onglet **[!UICONTROL Paramètres]**.

### Composants de l’onglet Créer le formulaire {#components-within-the-build-form-tab}

The **[!UICONTROL Build Form]** tab lists form items that you use in your schema form. L’onglet **[!UICONTROL Paramètres]** contient les attributs de chaque élément sélectionné dans l’onglet **[!UICONTROL Créer le formulaire]**. Le tableau suivant répertorie les éléments de formulaire disponibles dans l’onglet **[!UICONTROL Créer le formulaire]** :

| Nom du composant | Description |
|---|---|
| [!UICONTROL En-tête de section] | Permet d’ajouter un en-tête de section pour une liste de composants communs. |
| [!UICONTROL Une seule ligne de texte] | Permet d’ajouter une propriété d’une seule ligne de texte. Il est stocké sous la forme d’une chaîne. |
| [!UICONTROL Texte à plusieurs valeurs] | Permet d’ajouter une propriété de texte à plusieurs valeurs. Il est stocké sous forme de tableau de chaînes. |
| [!UICONTROL Nombre] | Permet d’ajouter un composant de nombre. |
| [!UICONTROL Date] | Permet d’ajouter un composant de date. |
| [!UICONTROL Liste déroulante] | Permet d’ajouter une liste déroulante. |
| [!UICONTROL Balises standard] | Permet d’ajouter une balise. |
| [!UICONTROL Balises intelligentes] | Ajoutez ce composant pour augmenter les capacités de recherche en ajoutant automatiquement des balises de métadonnées. |
| [!UICONTROL Champ masqué] | Permet d’ajouter un champ masqué. Il est envoyé en tant que paramètre POST lorsque la ressource est enregistrée. |
| [!UICONTROL Ressource référencée par] | Ajoutez ce composant pour afficher la liste des ressources référencées par la ressource. |
| [!UICONTROL Référencement des ressources] | Ajoutez ce composant pour afficher la liste des ressources qui référencent la ressource. |
| [!UICONTROL Références du produit] | Ajoutez ce composant pour afficher la liste des produits liés à la ressource. |
| [!UICONTROL Évaluation des ressources] | Ajoutez ce composant afin d’afficher des options pour évaluer la ressource. |
| [!UICONTROL Métadonnées contextuelles] | Ajoutez ce composant pour contrôler l’affichage des autres onglets de métadonnées dans la page de propriétés des ressources. |

### Modification du composant de métadonnées {#editing-the-metadata-component}

Pour modifier les propriétés d’un composant de métadonnées dans le formulaire, cliquez sur le composant et modifiez l’ensemble ou un sous-ensemble des propriétés suivantes dans l’onglet **[!UICONTROL Paramètres]**.

**Libellé** du champ : Nom de la propriété de métadonnées affichée sur la page de propriétés de la ressource.

**Associer à la propriété** : cette propriété spécifie le chemin/nom relatif du nœud de la ressource où elle est enregistrée dans le référentiel CRX. It starts with `./` because indicating that the path is under the asset&#39;s node.

Les valeurs admises pour cette propriété sont les suivantes :

* `./jcr:content/metadata/dc:title` : conserve la valeur au niveau du nœud de métadonnées du fichier en tant que propriété `dc:title`.

* `./jcr:created`: Affiche la propriété JCR au niveau du noeud de la ressource. Si vous configurez ces propriétés dans Afficher les propriétés, nous vous recommandons de les marquer avec l’état Désactiver la modification, car elles sont protégées. Otherwise, the error [!UICONTROL Asset(s) failed to modify] results when you save the asset&#39;s properties.

Pour garantir que le composant s’affiche correctement dans le formulaire de schéma de métadonnées, le chemin de la propriété ne doit pas comporter d’espace.

**Espace réservé** : utilisez cette propriété pour spécifier du texte dans l’espace réservé concernant la propriété de métadonnées.

**Obligatoire** : utilisez cette propriété pour marquer une propriété de métadonnées comme étant obligatoire dans la page Propriétés.

**Désactiver la modification** : Utilisez cette propriété pour rendre une propriété de métadonnées non modifiable dans la page Propriétés.

**Afficher le champ vide en lecture seule** : utilisez cette propriété pour afficher une propriété de métadonnées sur la page Propriétés même si elle ne possède pas de valeur. Par défaut, lorsqu’une propriété de métadonnées ne possède pas de valeur, elle n’est pas répertoriée sur la page Propriétés.

**Afficher la liste triée**: Utilisez cette propriété pour afficher une liste de choix ordonnés

**Choix** : utilisez cette propriété pour spécifier des choix dans une liste.

**Description** : utilisez cette propriété pour ajouter une brève description pour le composant de métadonnées.

**Classe** : classe d’objets à laquelle la propriété est associée.

**Icône** Supprimer Cliquez sur cette icône pour supprimer un composant du formulaire de schéma.

>[!NOTE]
>
>Le composant Champ masqué n’inclut pas ces attributs. À la place, il comprend des propriétés, telles que les attributs Nom, Valeur, Libellé du champ et Description. Les valeurs du composant Champ masqué sont envoyées en tant que paramètre POST lors de l’enregistrement de la ressource. Elles ne sont pas enregistrées sous forme de métadonnées pour la ressource.

Si vous sélectionnez l’option **[!UICONTROL Obligatoire]**, vous pouvez rechercher des fichiers dont les métadonnées obligatoires sont manquantes. Dans le panneau **[!UICONTROL Filtres]**, développez le prédicat **[!UICONTROL Validation des métadonnées]** et sélectionnez l’option **[!UICONTROL Non valide]**. Les résultats de la recherche affichent des fichiers dont les métadonnées obligatoires que vous avez configurées via le formulaire de schéma sont manquantes.

![chlimage_1-178](assets/chlimage_1-178.png)

Si vous ajoutez le composant Métadonnées contextuelles à un onglet d’un formulaire de schéma, le composant s’affiche sous la forme d’une liste dans la page de propriétés des ressources auxquelles le schéma spécifique est appliqué. La liste comprend tous les autres onglets, à l’exception de l’onglet auquel vous avez appliqué le composant Métadonnées contextuelles. Actuellement, cette fonctionnalité fournit des fonctions de base pour contrôler l’affichage des métadonnées en fonction du contexte.

![chlimage_1-179](assets/chlimage_1-179.png)

Pour inclure un onglet sur la page Propriétés en plus de l’onglet auquel le composant Métadonnées contextuelles est appliqué, sélectionnez-le dans la liste. L’onglet est ajouté à la page Propriétés.

![chlimage_1-180](assets/chlimage_1-180.png)

### Specify properties in JSON file {#specifying-properties-in-json-file}

Au lieu de spécifier les propriétés des options dans l’onglet **[!UICONTROL Paramètres]**, vous pouvez définir les options dans un fichier JSON en spécifiant les paires clé-valeur correspondantes. Spécifiez le chemin d’accès du fichier JSON dans le champ **[!UICONTROL Chemin JSON]**.

### Ajout ou suppression d’un onglet dans le formulaire de schéma {#adding-deleting-a-tab-in-the-schema-form}

L’éditeur de schéma vous permet d’ajouter ou de supprimer un onglet. Le formulaire de schéma par défaut comprend les onglets **[!UICONTROL Simple]**, **[!UICONTROL Avancé]**, **[!UICONTROL IPTC]** et **[!UICONTROL Extension IPTC]**, par défaut.

![chlimage_1-181](assets/chlimage_1-181.png)

Click `+` to add a new tab on a schema form. By default, the new tab has the name `Unnamed-1`. You can modify the name from the **[!UICONTROL Settings]** tab. Click `X` to delete a tab.

![chlimage_1-182](assets/chlimage_1-182.png)

## Suppression de formulaires de schéma de métadonnées {#deleting-metadata-schema-forms}

AEM vous permet uniquement de supprimer des formulaires de schéma personnalisés. Il ne vous permet pas de supprimer les formulaires/modèles de schéma par défaut. Cependant, vous pouvez supprimer toutes les modifications personnalisées dans ces formulaires.

Pour supprimer un formulaire, sélectionnez-le puis cliquez sur l’icône **[!UICONTROL Supprimer]**.

>[!NOTE]
>
>Une fois que vous avez supprimé les modifications personnalisées apportées à un formulaire par défaut, l’icône de verrouillage s’affiche à nouveau dans l’interface du schéma de métadonnées pour indiquer que le formulaire est revenu à son état par défaut.

>[!NOTE]
>
>Vous ne pouvez pas supprimer les formulaires de schéma de métadonnées prêts à l’emploi dans AEM Assets.

## Formulaires de schéma pour les types MIME {#schema-forms-for-mime-types}

AEM Assets fournit des formulaires par défaut pour plusieurs types MIME prêts à l’emploi. Vous pouvez toutefois ajouter des formulaires personnalisés pour les ressources de plusieurs types MIME.

### Add new forms for MIME types {#adding-new-forms-for-mime-types}

Créez un formulaire sous le type de formulaire approprié. For example, to add a new template for the `image/png` subtype, create the form under the `image` forms. Le titre du formulaire de schéma est le nom du sous-type. In this case, the title is `png`.

### Use an existing schema template for various MIME types {#using-an-existing-schema-template-for-various-mime-types}

Vous pouvez utiliser un modèle existant pour un type MIME différent. Par exemple, utilisez le `image/jpeg` formulaire pour les ressources de type MIME `image/png`.

Dans ce cas, créez un nœud sous `/etc/dam/metadataeditor/mimetypemappings` dans le référentiel CRX. Indiquez un nom pour le nœud et définissez les propriétés suivantes  :

| Nom | Description | Type | Valeur |
|---|---|---|---|
| `exposedmimetype` | Nom du formulaire existant à associer | `String` | `image/jpeg` |
| `mimetypes` | List of MIME types that use the form defined in the `exposedmimetype` attribute | `String` | `image/png` |

AEM Assets associe les types MIME et les formulaires de schéma suivants :

| Formulaire de schéma | Types MIME |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Octroi de l’accès aux schémas de métadonnées {#granting-access-to-metadata-schemas}

La fonctionnalité de schéma de métadonnées est disponible uniquement pour les administrateurs. Toutefois, les administrateurs peuvent fournir un accès aux utilisateurs non administrateurs en leur fournissant des autorisations **[!UICONTROL Créer]**, **[!UICONTROL Modifier]** et **[!UICONTROL Supprimer]** sur le `/conf` dossier.

## Application de métadonnées spécifiques au dossier {#applying-folder-specific-metadata}

AEM Assets vous permet de définir une variation d’un schéma de métadonnées et de l’appliquer à un dossier spécifique.

Par exemple, vous pouvez définir une variation du schéma de métadonnées par défaut et l’appliquer à un dossier. Lorsque vous appliquez le schéma modifié, il remplace le schéma de métadonnées d’origine par défaut qui est appliqué aux ressources du dossier.

Les métadonnées modifiées définies dans le schéma de métadonnées de la variation seront uniquement appliquées aux ressources chargées dans le dossier auquel est appliqué le schéma.

Les ressources d’autres dossiers auxquels le schéma d’origine est appliqué continuent à utiliser les métadonnées définies dans le schéma d’origine.

L’héritage des métadonnées par les ressources est basé sur le schéma appliqué au dossier de premier niveau dans la hiérarchie. Autrement dit, si un dossier ne contient aucun sous-dossier, les ressources du dossier héritent des métadonnées du schéma appliqué au dossier.

Si le dossier contient un sous-dossier, les ressources du sous-dossier héritent des métadonnées du schéma appliqué au niveau du sous-dossier si un schéma différent est appliqué. Cependant, si aucun schéma n’est appliqué au niveau du sous-dossier ou si le même schéma y est appliqué, les ressources du sous-dossier héritent des métadonnées du schéma appliqué au niveau du dossier parent.

1. Cliquez sur le logo AEM, puis accédez à **[!UICONTROL Outils > Ressources > Schémas de métadonnées]**. La page **[!UICONTROL Formulaires de schéma de métadonnées]** s’affiche.
1. Cochez la case en regard d’un formulaire, par exemple le formulaire de métadonnées par défaut, puis cliquez ou appuyez sur l’icône **[!UICONTROL Copier]** et enregistrez-le en tant que formulaire personnalisé. Specify a custom name for the form, for example `my_default`. Vous pouvez également créer un formulaire personnalisé.

   ![chlimage_1-184](assets/chlimage_1-184.png)

1. In the **[!UICONTROL Metadata Schema Forms]** page, select the `my_default` form, and then click **[!UICONTROL Edit]**.

1. In the **[!UICONTROL Metadata Schema Editor]** page, add a text field to the schema form. For example add a field with the label **[!UICONTROL Category]**.

   ![chlimage_1-186](assets/chlimage_1-186.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**. Le formulaire modifié figure sur la page **[!UICONTROL Formulaires de schéma de métadonnées.]**
1. Cliquez/appuyez sur **[!UICONTROL Appliquer au(x) dossier(s)]** dans la barre d’outils pour appliquer les métadonnées personnalisées à un dossier.

   ![chlimage_1-187](assets/chlimage_1-187.png)

1. Select the folder on which to apply the modified schema and then click/tap **[!UICONTROL Apply]**.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Si d’autres métadonnées sont appliquées au dossier, un message s’affiche pour vous avertir que vous êtes sur le point de remplacer le schéma de métadonnées existant. Click **[!UICONTROL Overwrite]**.
1. Click **[!UICONTROL OK]** to close the success message.
1. Accédez au dossier auquel vous avez appliqué le schéma de métadonnées modifié.

## Définition des métadonnées obligatoires {#defining-mandatory-metadata}

Vous pouvez définir des champs obligatoires au niveau d’un dossier, qui s’appliquent aux ressources chargées dans ce dossier. Si vous chargez des ressources présentant des métadonnées manquantes dans des champs obligatoires précédemment définis, une indication visuelle de métadonnées manquantes apparaît sur les ressources en mode Carte.

>[!NOTE]
>
>Un champ de métadonnées peut être défini comme obligatoire en fonction de la valeur d’un autre champ. Dans le mode Carte, AEM n’affiche pas le message d’avertissement concernant les métadonnées manquantes pour ces champs de métadonnées obligatoires.

1. Cliquez sur le logo AEM, puis accédez à **[!UICONTROL Outils > Ressources > Schémas de métadonnées]**. La page **[!UICONTROL Formulaires de schéma de métadonnées]** s’affiche.
1. Enregistrez le formulaire de métadonnées par défaut en tant que formulaire personnalisé. For example, save it as `my_default`.

   ![chlimage_1-189](assets/chlimage_1-189.png)

1. Modifiez le formulaire personnalisé. Ajoutez un champ obligatoire. For example, add a **Category** field and make the field mandatory.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**. Le formulaire modifié figure sur la page **[!UICONTROL Formulaires de schéma de métadonnées]**. Pour appliquer les métadonnées personnalisées à un dossier, sélectionnez le formulaire et cliquez/appuyez sur **[!UICONTROL Appliquer au(x)]** dossier(s) dans la barre d’outils.

1. Accédez au dossier et chargez des ressources présentant des données manquantes pour le champ obligatoire que vous avez ajouté au formulaire personnalisé. Le mode Carte des ressources affiche un message pour les métadonnées manquantes dans le champ obligatoire.

   ![chlimage_1-192](assets/chlimage_1-192.png)

1. (Facultatif) Accès `http://[server]:[port]/system/console/components/`. Configure and enable `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` component that is disabled by default. Définissez la fréquence à laquelle AEM vérifie la validité des métadonnées sur les ressources.
Cette configuration ajoute une propriété `hasValidMetadata` au nœud jcr:content des ressources. Cette propriété permet à AEM de filtrer les résultats d’une recherche.

>[!NOTE]
>
>If an asset is added after the scheduled check, the asset is not flagged with `hasValidMetadata` until  the next scheduled check. Les ressources n’apparaissent pas dans les résultats de recherche intermédiaires.

>[!CAttention]
>
>Les contrôles de validation des métadonnées sont des tâches qui nécessitent de nombreuses ressources et qui peuvent donc altérer les performances de votre système. Planifiez les contrôles en conséquence. Si le déploiement AEM rencontre des problèmes de performances, essayez de désactiver cette tâche.
