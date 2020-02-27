---
title: Facettes de recherche
description: Cet article décrit comment créer, modifier et utiliser les facettes de recherche dans AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: adf44677a0ac833a131aad8187529b094aaca9ef

---


# Facettes de recherche {#search-facets}

Découvrez comment créer, modifier et utiliser les facettes de recherche dans AEM.

Un déploiement à l’échelle de l’entreprise d’Adobe Experience Manager (AEM) Assets permet de stocker des quantités importantes de ressources. Dans certains cas, la recherche de la bonne ressource peut être difficile et longue si vous utilisez uniquement les fonctionnalités de recherche génériques d’AEM.

Utilisez les facettes de recherche dans le panneau Filtres pour ajouter plus de granularité à votre expérience de recherche et rendre ainsi la fonctionnalité de recherche plus efficace et souple. Les facettes de recherche ajoutent des dimensions multiples (prédicats) qui permettent d’effectuer des recherches plus complexes. Le panneau Filtres inclut quelques facettes standard. Vous pouvez également ajouter des facettes de recherche personnalisées.

En résumé, les facettes de recherche vous permettent de rechercher des fichiers de plusieurs manières plutôt que dans un seul ordre taxonomique prédéterminé. Vous pouvez facilement descendre dans la hiérarchie jusqu’au niveau de détail souhaité pour effectuer une recherche plus précise.

Par exemple, si vous recherchez une image, vous pouvez indiquer si vous souhaitez une image bitmap ou vectorielle. Vous pouvez réduire davantage le champ de recherche en spécifiant le type MIME de l’image. De la même façon, si vous recherchez des documents, vous pouvez spécifier le format, par exemple PDF ou MS Word.

## Ajout d’un prédicat {#adding-a-predicate}

Les facettes de recherche qui apparaissent dans le panneau Filtres sont définies dans le formulaire de recherche sous-jacent à l’aide de prédicats. Pour afficher plusieurs facettes ou d’autres facettes, vous ajoutez des prédicats au formulaire par défaut ou utilisez un formulaire personnalisé qui inclut les facettes de votre choix.

Pour des recherches de texte intégral, ajoutez le prédicat Texte intégral au formulaire. Utilisez le prédicat Propriété pour rechercher les ressources qui correspondent à une propriété unique que vous spécifiez. Utilisez le prédicat Options pour rechercher les ressources correspondant à une ou plusieurs valeurs pour une propriété spécifique. Ajoutez le prédicat Période pour rechercher les ressources créées au cours d’une période donnée.

1. Appuyez/cliquez sur le logo AEM, puis sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Général]** > **[!UICONTROL Formulaires de recherche]**.
1. From the Search Forms page, select **[!UICONTROL Assets Admin Search Rail]**, then tap  **Edit** ![aemassets_edit](assets/aemassets_edit.png).

   ![Localisez et sélectionnez le rail de recherche d’administrateurs Ressources.](assets/assets_admin_searchrail.png)

   Localisez et sélectionnez le rail de recherche d’administrateurs Ressources.

   >[!NOTE]
   >
   >Pour utiliser la fonctionnalité de recherche de dossiers du rail **de recherche** d’administration desressources préconfiguré à partir d’une version antérieure d’AEM, procédez comme suit :
   > 
   >1. Accédez à */conf/global/settings/dam/search/facets/assets/jcr:content/items* dans CRX-DE.
   >1. Supprimez le noeud **de type** .
   >1. Dans le chemin */libs/settings/dam/search/facets/assets/jcr:content/items*, copiez les nœuds **asset, directory, typeor, excludepaths** et **search type** dans le chemin d’accès mentionné à l’étape 1.
   >1. Enregistrez les modifications.


1. Sur la page Modifier des formulaires de recherche, faites glisser un prédicat de l’onglet **[!UICONTROL Sélectionner le prédicat]** vers le volet principal. Faites glisser, par exemple, **[!UICONTROL Prédicat de la propriété]**.

   ![Faites glisser un prédicat pour personnaliser les filtres de recherche.](assets/drag_predicate.png)

   Faites glisser un prédicat pour personnaliser les filtres de recherche.

1. Sous l’onglet Paramètres, saisissez un libellé de champ, un texte d’espace réservé et une description pour le prédicat. Indiquez un nom valide pour la propriété de métadonnées que vous souhaitez associer au prédicat.

   Le libellé de l’en-tête dans l’onglet Paramètres identifie le type du prédicat sélectionné.

   ![Utilisez l’onglet Paramètres pour définir les options requises d’un prédicat.](assets/settings.png)

   Utilisez l’onglet Paramètres pour définir les options requises d’un prédicat.

1. Dans le champ **[!UICONTROL Nom de la propriété]**, spécifiez un nom valide pour la propriété de métadonnées à associer au prédicat. Il s’agit du nom sur lequel la recherche est effectuée. Par exemple, saisissez `jcr:content/metadata/dc:description` ou `./jcr:content/metadata/dc:description`.

   Vous pouvez également sélectionner un nœud existant dans la boîte de dialogue de sélection.

   ![Associez une propriété de métadonnées à un prédicat dans le champ Nom de propriété.](assets/property_settings.png)

   Associez une propriété de métadonnées à un prédicat dans le champ Nom de propriété.

1. Tap/click the **[!UICONTROL Preview]** ![preview](assets/preview.png) to generate a preview of the Filters panel as it appears after you add the predicate.
1. Examinez la structure du prédicat en mode Aperçu.

   ![Aperçu du formulaire de recherche avant d’envoyer les modifications](assets/preview-1.png)

   Aperçu du formulaire de recherche avant d’envoyer les modifications

1. To close the preview, tap/click the **[!UICONTROL Close]** ![close](assets/close.png) on the upper-right corner of the preview.
1. Tap **[!UICONTROL Done]** to save the settings.
1. Accédez au panneau Rechercher dans l’interface utilisateur Ressources. Le prédicat Propriété est ajouté au panneau.
1. Dans la zone de texte, saisissez une description de la ressource à rechercher. Saisissez par exemple « Adobe ». Lorsque vous effectuez une recherche, les ressources dont la description correspond à « Adobe » sont répertoriées dans les résultats de la recherche.

## Ajout d’un prédicat Options {#adding-an-options-predicate}

Le prédicat Options permet d’ajouter des options de recherche multiples dans le panneau Filtres. Vous pouvez choisir une ou plusieurs options dans le panneau Filtres pour rechercher des ressources. Par exemple, pour rechercher des actifs en fonction du type de fichier, configurez des options telles que Images, Multimédia, Documents et Archives dans le formulaire de recherche. Une fois ces options configurées, la recherche est effectuée sur des fichiers de type GIF, JPEG, PNG, etc., lorsque vous sélectionnez l’option Images dans le panneau Filtres.

Pour mapper les options à la propriété correspondante, créez une structure de nœud pour les options et fournissez le chemin du nœud parent dans la propriété Nom de la propriété du prédicat Options. The parent node should be of type `sling`: `OrderedFolder`. The options should be of type `nt:unstructured`. The option nodes should have the properties `jcr:title` and `value` configured.

La propriété `jcr:title` est un nom convivial pour l’option qui apparaît dans le panneau Filtres. Le champ `value` est utilisé dans la demande pour correspondre à la propriété spécifiée.

Lorsque vous sélectionnez une option, la recherche est effectuée en fonction de la `value` propriété du noeud d’option et de ses noeuds enfants, le cas échéant. L’arborescence entière sous le noeud d’option est parcourue et la `value` propriété de chaque noeud enfant est combinée à l’aide d’une opération OU pour former la requête de recherche.

Par exemple, si vous sélectionnez « Images » pour les types de fichiers, la requête de recherche des ressources est créée en combinant la propriété `value` à l’aide d’une opération OU. Par exemple, la requête de recherche d’images est créée en combinant les résultats correspondants pour *image/jpeg*, *image/gif*, *image/png*, *image/pjpeg* et *image/tiff* pour la propriété `jcr:content/metadata/dc:format` à l’aide d’une opération OU.

![La propriété de valeur d’un type de fichier, telle que vue dans CRXDE, est utilisée pour que les requêtes de recherche fonctionnent.](assets/chlimage_1-418.png)

La propriété de valeur d’un type de fichier, telle que vue dans CRXDE, est utilisée pour que les requêtes de recherche fonctionnent.

Au lieu de créer manuellement une structure de nœud pour les options du référentiel CRX, vous pouvez définir les options dans un fichier JSON en spécifiant les paires clé-valeur correspondantes. Indiquez le chemin d’accès du fichier JSON dans le champ **[!UICONTROL Nom de la propriété]**. Vous pouvez, par exemple, définir les paires clé-valeur, `image/bmp`, `image/gif`, `image/jpeg` et `image/png`, et spécifier leurs valeurs comme illustré dans l’exemple de fichier JSON suivant. Dans le champ **[!UICONTROL Nom de la propriété]**, vous pouvez spécifier le chemin CRX pour ce fichier.

```json
{
    "options" :
 [
          {"value" : "image/bmp","text" : "BMP"},
          {"value" : "image/gif","text" : "GIF"},
          {"value" : "image/jpeg","text" : "JPEG"},
          {"value" : "image/png","text" : "PNG"}
 ]
}
```

Si vous souhaitez utiliser un nœud existant, indiquez-le à l’aide de la boîte de dialogue de sélection.

>[!NOTE]
>
>Le prédicat Options est un wrapper personnalisé qui inclut des prédicats de propriété pour démontrer le comportement décrit. Pour l’heure, aucun point de terminaison REST n’est disponible pour la prise en charge native de cette fonctionnalité.

1. Tap the AEM logo, and then go to **[!UICONTROL Tools > General > Search Forms]**.
1. Dans la page **[!UICONTROL Formulaires de recherche]**, sélectionnez **[!UICONTROL Rail de recherche d’administrateurs de ressources]**, puis appuyez sur l’icône de modification.
1. Dans la page **[!UICONTROL Modifier le formulaire de recherche]**, faites glisser **[!UICONTROL Options du prédicat]** depuis l’onglet **[!UICONTROL Sélectionner le prédicat]** vers le volet principal.
1. Dans l’onglet **[!UICONTROL Paramètres]**, saisissez un libellé et un nom pour la propriété. Par exemple, pour rechercher des fichiers en fonction de leur format, spécifiez un nom convivial pour le libellé, par exemple **[!UICONTROL Type de fichier]**. Spécifiez la propriété en fonction de laquelle la recherche doit être effectuée dans le champ de propriété, par exemple `jcr:content/metadata/dc:format.`
1. Utilisez l’une des méthodes suivantes :

   * In the **[!UICONTROL Property Name]** field, mention the path of the JSON file where you define the nodes for the options and specify corresponding key-value pairs.
   * Tap ![Add icon](assets/do-not-localize/aem_assets_add_icon.png) next to the Options field to specify the display text and value for the options you want to supply in the Filters panel. To add another option, tap/click ![Add icon](assets/do-not-localize/aem_assets_add_icon.png) and repeat the step.

1. Assurez-vous que l’option **[!UICONTROL Sélection unique]** est désactivée pour permettre à l’utilisateur de sélectionner plusieurs options pour les types de fichiers à la fois (par exemple, Images, Documents, Multimédia et Archives). Si vous sélectionnez **[!UICONTROL Sélection unique]**, l’utilisateur ne peut sélectionner qu’une seule option pour les types de fichiers à la fois.

   ![Champs disponibles dans le prédicat Options](assets/options_predicate.png)

   Champs disponibles dans le prédicat Options

1. Dans le champ **Description**, saisissez une description facultative, puis cliquez sur **[!UICONTROL Terminé]**.
1. Navigate to the Search panel. The Options predicate is added to the **Search** panel. Les options proposées pour **[!UICONTROL Types de fichiers]** sont présentées sous la forme de cases à cocher.

## Ajout d’un prédicat de propriété à plusieurs valeurs {#adding-a-multi-value-property-predicate}

Le prédicat de propriété à plusieurs valeurs vous permet de rechercher plusieurs valeurs dans des ressources. Supposons que vous disposiez des images de plusieurs produits dans AEM Assets et que les métadonnées de chaque image comprennent un numéro de SKU qui est associé au produit. Vous pouvez utiliser ce prédicat pour rechercher des images de produit sur la base de plusieurs numéros de SKU.

1. Cliquez sur le logo AEM, puis sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Général]** > **[!UICONTROL Formulaires de recherche]**.
1. Dans la page Rechercher des formulaires, sélectionnez **[!UICONTROL Ressources Admin Rail]** de recherche, puis appuyez sur **Modifier** aemassets_edit ![](assets/aemassets_edit.png).
1. Dans la page Modifier le formulaire de recherche, faites glisser un **[!UICONTROL prédicat de propriété de valeur multiple]** de l’onglet **[!UICONTROL Sélectionner un prédicat]** vers le volet principal.
1. In the **[!UICONTROL Settings]** tab, enter a label and placeholder text for the predicate. Specify the property name based on which the search is to be performed in the property field, for example `jcr:content/metadata/dc:value`. Vous pouvez également utiliser la boîte de dialogue de sélection pour sélectionner un nœud.
1. Assurez-vous que la **[!UICONTROL prise en charge du délimiteur]** est sélectionnée. Dans le champ **[!UICONTROL Délimiteurs d’entrée]**, spécifiez des délimiteurs pour séparer les valeurs individuelles. Par défaut, la virgule est spécifiée comme séparateur. Vous pouvez spécifier un délimiteur différent.
1. In the **Description** field, enter an optional description and then tap **[!UICONTROL Done]**.
1. Accédez au panneau Filtres de l’interface utilisateur Ressources. Le prédicat **[!UICONTROL Propriété à plusieurs valeurs]** est ajouté au panneau.
1. Indiquez plusieurs valeurs dans le champ Valeur multiple, en les séparant par des délimiteurs, puis effectuez la recherche. Le prédicat récupère une correspondance de texte exacte pour les valeurs que vous avez spécifiées.

## Ajout d’un prédicat Balises {#adding-a-tags-predicate}

Le prédicat de balise vous permet d’effectuer des recherches de ressources basées sur des balises. Par défaut, AEM Assets recherche dans les ressources une ou plusieurs correspondances de balises en fonction des balises spécifiées. En d’autres termes, la requête de recherche effectue une opération OR à l’aide des balises indiquées. Cependant, vous pouvez utiliser l’option de correspondance de toutes les balises pour rechercher les ressources qui contiennent toutes les balises que vous spécifiez.

1. Cliquez sur le logo AEM, puis sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Général]** > **[!UICONTROL Formulaires de recherche]**.
1. From the Search Forms page, select **[!UICONTROL Assets Admin Search Rail]** and then tap **Edit** ![aemassets_edit](assets/aemassets_edit.png).
1. In the Edit Search Form page, drag **[!UICONTROL Tags Predicate]** from the Select Predicate tab to the main pane.
1. Dans l’onglet Paramètres, saisissez un texte d’espace réservé pour le prédicat. Specify the property name based on which the search is to be performed in the property field, for example *jcr:content/metadata/cq:tags*. Vous pouvez également sélectionner un noeud dans CRXDE dans la boîte de dialogue de sélection.
1. Configurez la propriété Chemin d’accès aux balises racines de ce prédicat pour renseigner les différentes balises dans la liste Balises.
1. Sélectionnez l’**[!UICONTROL option Afficher la correspondance]** avec toutes les balises pour rechercher les ressources qui incluent toutes les balises que vous spécifiez.

   ![Paramètres standard du prédicat Balises](assets/tags_predicate.png)

   Paramètres standard du prédicat Balises

1. In the **[!UICONTROL Description]** field, enter an optional description and then click/tap **[!UICONTROL Done]**.
1. Accédez au panneau Rechercher. The **[!UICONTROL Tags]** predicate is added to the Search panel.
1. Indiquez les balises sur la base desquelles vous souhaitez rechercher des ressources ou faites votre sélection dans la liste des suggestions.

   ![Suggestion fournie par AEM lors de la saisie du nom de la balise](assets/chlimage_1-419.png)

   Suggestion fournie par AEM lors de la saisie du nom de la balise

1. Sélectionnez **[!UICONTROL Correspondre à tous les critères]** pour rechercher les ressources qui contiennent toutes les balises que vous spécifiez.

## Ajout d’autres prédicats {#adding-other-predicates}

Tout comme vous ajoutez un prédicat Propriété ou un prédicat Options, vous pouvez ajouter les autres prédicats suivants au panneau Rechercher :

| Nom du prédicat | Description | Propriétés |
|---|---|---|
| [!UICONTROL Texte intégral] | Prédicat de recherche permettant d’effectuer une recherche de texte intégral dans un nœud de ressource entier. Il est mappé à l’opérateur jcr:contains. Vous pouvez indiquer un chemin d’accès relatif si vous souhaitez effectuer une recherche de texte intégral sur une partie spécifique du nœud de ressource. | <ul><li>Libellé</li><li>Espace réservé</li><li>Nom de la propriété</li><li>Description</li></ul> |
| [!UICONTROL Explorateur de chemins d’accès] | Prédicat de recherche pour rechercher des fichiers dans des dossiers et des sous-dossiers à un chemin racine préconfiguré | <ul><li>Espace réservé</li><li>Chemin racine</li><li>Description</li></ul> |
| [!UICONTROL Chemin] | Utilisez-le pour filtrer les résultats selon l’emplacement. Vous pouvez spécifier différents chemins d’accès sous la forme d’options. | <ul><li>Libellé</li><li>Chemin</li><li>Description</li></ul> |
| [!UICONTROL État de publication] | Prédicat de recherche permettant de rechercher des ressources en fonction de leur état de publication. | <ul><li>Libellé</li><li>Nom de la propriété</li><li>Description</li></ul> |
| [!UICONTROL Date relative] | Prédicat de recherche permettant de rechercher des ressources en fonction de leur date de création. Vous pouvez, par exemple, configurer des options telles que « il y a 2 mois », « il y a 3 semaines », etc. | <ul><li>Libellé</li><li>Nom de la propriété</li><li>Date relative</li></ul> |
| [!UICONTROL Étendue] | Prédicat de recherche permettant de rechercher des ressources comprises dans une étendue spécifiée. Dans le panneau Rechercher, vous pouvez spécifier des valeurs maximale et minimale pour l&#39;étendue. | <ul><li>Libellé</li><li>Nom de la propriété</li><li>Description</li></ul> |
| [!UICONTROL Période] | Prédicat de recherche permettant de rechercher des ressources créées pendant une période spécifiée pour une propriété de date. Vous pouvez spécifier des dates de début et de fin dans le panneau Rechercher à l’aide des sélecteurs de date. | <ul><li>Libellé</li><li>Espace réservé</li><li>Nom de la propriété</li><li>Texte de la plage (De)</li><li>Texte de la plage (À)</li><li>Description</li></ul> |
| [!UICONTROL Date] | Prédicat de recherche permettant de rechercher à l’aide d’un curseur des ressources selon une propriété de date. | <ul><li>Libellé</li><li>Nom de la propriété</li><li>Description</li></ul> |
| [!UICONTROL Taille de fichier] | Prédicat de recherche permettant de rechercher des ressources en fonction de leur taille. Il s’agit d’un prédicat basé sur un curseur, dans lequel vous sélectionnez les options de curseur à partir d’un nœud configurable. Les options par défaut sont définies sous /libs/dam/options/predicates/filesize dans le référentiel CRX. La taille du fichier est exprimée en octets. | <ul><li>Libellé</li><li>Nom de la propriété</li><li>Chemin</li><li>Description</li></ul> |
| [!UICONTROL Dernière modification de la ressource] | Prédicat de recherche pour rechercher des ressources récemment modifiées | <ul><li>Nom de la propriété</li><li>Valeur de la propriété</li><li>Description</li></ul> |
| [!UICONTROL État de publication] | Prédicat de recherche pour rechercher des ressources en fonction de leur état de publication | <ul><li>Libellé</li><li>Nom de la propriété</li><li>Description</li></ul> |
| [!UICONTROL Évaluation] | Prédicat de recherche pour rechercher des ressources en fonction de leur évaluation moyenne | <ul><li>Libellé</li><li>Nom de la propriété</li><li>Chemin d’accès aux options</li><li>Description</li></ul> |
| [!UICONTROL État d’expiration] | Prédicat de recherche pour rechercher des ressources en fonction de leur état d’expiration | <ul><li>Libellé</li><li>Nom de la propriété</li><li>Description</li></ul> |
| [!UICONTROL Masqué] | Prédicat de recherche permettant de définir une propriété de champ masqué pour rechercher des ressources. | <ul><li>Nom de la propriété</li><li>Valeur de la propriété</li><li>Description</li></ul> |

## Restauration de facettes de recherche par défaut {#restoring-default-search-facets}

By default, a Lock icon appears before **[!UICONTROL Assets Admin Search Rail]** in the **[!UICONTROL Search Forms]** page. L’icône représentant un cadenas disparaît lorsque vous ajoutez des facettes de recherche au formulaire, ce qui indique que le formulaire par défaut a été modifié.

![L’icône de verrouillage d’une option de la page Rechercher des formulaires indique que les paramètres par défaut sont intacts et ne sont pas personnalisés.](assets/locked_admin_rail.png)

L’icône de verrouillage d’une option de la page Rechercher des formulaires indique que les paramètres par défaut sont intacts et ne sont pas personnalisés.

Pour restaurer la facette de recherche par défaut, procédez comme suit :

1. Select **[!UICONTROL Assets Admin Search Rail]** in the **[!UICONTROL Search Forms]** page.
1. Appuyez sur **[!UICONTROL Supprimer]** et supprimer ![](assets/deleteoutline.png) dans la barre d’outils.
1. In the confirmation dialog, tap **[!UICONTROL Delete]** to remove the custom changes.

   Après avoir supprimé les modifications personnalisées apportées aux facettes de recherche, l’icône de verrouillage s’affiche à nouveau avant **[!UICONTROL Rail de recherche d’administrateurs de ressources]** dans la page **[!UICONTROL Formulaires de recherche]**.

## Autorisations d’utilisateur {#user-permissions}

Si le rôle d’administrateur ne vous a pas été attribué, voici la liste des autorisations dont vous avez besoin pour réaliser des actions de modification, de suppression et d’affichage d’aperçu impliquant des facettes de recherche.

| Action | Permissions |
|---|---|
| [!UICONTROL Modifier] | Autorisations de lecture et d&#39;écriture sur le nœud /apps dans CRX. |
| [!UICONTROL Supprimer] | Autorisations de lecture, d’écriture et de suppression sur le noeud /apps dans CRX |
| [!UICONTROL Aperçu] | Autorisations de lecture, d’écriture et de suppression sur le noeud /var/dam/content dans CRX. En outre, les autorisations de lecture et d’écriture sur le noeud /apps. |

>[!MORELIKETHIS]
>
>* [Recherche d’extensions de ressources](searchx.md)
>* [Recherche de ressources](search-assets.md)
>* [Recherche de ressources vidéo](search-video-assets.md)

