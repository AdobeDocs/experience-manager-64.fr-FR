---
title: Métadonnées en cascade
description: Cet article décrit comment définir des métadonnées en cascade pour des ressources.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: ea6187e8-075d-4666-afc5-01c97deccc11
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 40%

---

# Métadonnées en cascade {#cascading-metadata}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cet article décrit comment définir des métadonnées en cascade pour des ressources.

>[!CAUTION]
>
>Les métadonnées en cascade ne sont pas prises en charge pour les fragments de contenu.

Lors de la capture des informations de métadonnées d’une ressource, les utilisateurs fournissent des informations dans les différents champs disponibles. Vous pouvez afficher des champs de métadonnées ou des valeurs de champ spécifiques en fonction des options sélectionnées dans les autres champs. Ce type d’affichage conditionnel des métadonnées est appelé métadonnées en cascade. En d’autres termes, vous pouvez créer une dépendance entre un champ/une valeur de métadonnées spécifique et un ou plusieurs champs et/ou leurs valeurs.

Utilisez des schémas de métadonnées pour définir des règles d’affichage des métadonnées en cascade. Par exemple, si votre schéma de métadonnées comprend un champ de type de ressource, vous pouvez définir un ensemble de champs pertinent à afficher en fonction du type de ressource sélectionné par l’utilisateur.

Voici quelques cas d’utilisation pour lesquels vous pouvez définir des métadonnées en cascade :

* Lorsque l’emplacement de l’utilisateur est requis, affichez les noms de ville pertinents en fonction du choix de pays et d’état de l’utilisateur.
* Chargez les noms de marque pertinents dans une liste en fonction du choix de catégorie de produits par l’utilisateur.
* Active/désactive la visibilité d’un champ spécifique en fonction de la valeur spécifiée dans un autre champ. Par exemple, affichez des champs d’adresse de livraison distincts si l’utilisateur souhaite que l’envoi soit envoyé à une autre adresse.
* Désigner un champ comme obligatoire en fonction de la valeur spécifiée dans un autre champ.
* Modifiez les options affichées pour un champ particulier en fonction de la valeur spécifiée dans un autre champ.
* Définissez la valeur de métadonnées par défaut dans un champ particulier en fonction de la valeur spécifiée dans un autre champ.

## Configuration des métadonnées en cascade dans [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Supposons que vous souhaitiez afficher des métadonnées en cascade en fonction du type de ressource sélectionné. Quelques exemples

* Pour une vidéo, affichez les champs applicables tels que le format, le codec, la durée, etc.
* Pour un document Word ou PDF, affichez des champs tels que le nombre de pages, l’auteur, etc.

Sans tenir compte du type de ressource choisi, affichez les informations de copyright comme étant un champ requis.

1. Appuyez/cliquez sur le logo [!DNL Experience Manager], puis sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
1. Dans la page **[!UICONTROL Formulaires de schéma]**, sélectionnez un formulaire de schéma, puis appuyez/cliquez sur **[!UICONTROL Modifier]** dans la barre d’outils pour modifier le schéma.

   ![select_form](assets/select_form.png)

1. (Facultatif) Dans l’éditeur de schéma de métadonnées, créez un champ à conditionner. Spécifiez un nom et un chemin de propriété dans la variable **[!UICONTROL Paramètres]** .

   Pour créer un onglet, appuyez/cliquez sur **[!UICONTROL +]** pour ajouter un onglet, puis ajouter un champ de métadonnées.

   ![add_tab](assets/add_tab.png)

1. Ajoutez un champ déroulant pour le type de ressource. Spécifiez un nom et un chemin de propriété dans la variable **[!UICONTROL Paramètres]** . Ajoutez une description facultative.

   ![asset_type_field](assets/asset_type_field.png)

1. Les paires clé-valeur sont les options fournies à un utilisateur de formulaire. Vous pouvez fournir les paires clé-valeur manuellement ou à partir d’un fichier JSON.

   * Pour spécifier les valeurs manuellement, sélectionnez **[!UICONTROL Ajouter manuellement]**, puis appuyez/cliquez sur **[!UICONTROL Ajouter un choix]** et indiquez le texte et la valeur de l’option. Par exemple, spécifiez les types de ressources Vidéo, PDF, Word et Image.
   * Pour récupérer dynamiquement les valeurs d’un fichier JSON, sélectionnez **[!UICONTROL Ajout via le chemin JSON]** et indiquez le chemin d’accès au fichier JSON. [!DNL Experience Manager] récupère les paires clé/valeur en temps réel lorsque le formulaire est présenté à l’utilisateur.

   Les deux options s’excluent mutuellement. Vous ne pouvez pas importer les options d’un fichier JSON et les modifier manuellement.

   ![add_choice](assets/add_choice.png)

   >[!NOTE]
   >
   >Lorsque vous ajoutez un fichier JSON, les paires clé/valeur ne sont pas affichées dans l’éditeur de schéma de métadonnées, mais sont disponibles dans le formulaire publié.

   >[!NOTE]
   >
   >Lors de l’ajout de choix, si vous cliquez sur le champ déroulant, l’interface est déformée et l’icône de suppression des choix cesse de fonctionner. Lorsque vous ajoutez des choix à la liste déroulante, ne cliquez pas de nouveau sur la liste déroulante tant que vous n’avez pas enregistré les modifications. Si vous rencontrez ce problème, enregistrez le schéma, puis rouvrez-le pour poursuivre la modification.

1. (Facultatif) Ajoutez les autres champs obligatoires. Par exemple, format, codec et durée pour le type de ressource vidéo.

   De même, ajoutez des champs dépendants pour d’autres types de ressources. Par exemple, ajoutez des champs Nombre de pages et Auteur pour les ressources de documents, tels que des fichiers PDF et Word.

   ![video_dependent_fields](assets/video_dependent_fields.png)

1. Pour créer une dépendance entre le champ de type de ressource et d’autres champs, sélectionnez le champ dépendant et ouvrez l’onglet **[!UICONTROL Règles]**.

   ![select_dependentfield](assets/select_dependentfield.png)

1. Sous **[!UICONTROL Condition requise]**, sélectionnez l’option **[!UICONTROL Requis, d’après la nouvelle règle]**.
1. Appuyez/cliquez sur **[!UICONTROL Ajouter une règle]** et sélectionnez le champ **[!UICONTROL Type de ressource]** pour créer une dépendance. Sélectionnez également la valeur du champ sur lequel vous souhaitez créer la dépendance. Dans ce cas, sélectionnez **[!UICONTROL Vidéo]**. Appuyez/cliquez sur **[!UICONTROL Terminé]** pour enregistrer les modifications.

   ![define_rule](assets/define_rule.png)

   >[!NOTE]
   >
   >Une liste déroulante avec des valeurs prédéfinies manuellement peut être utilisée avec des règles. Les menus déroulants avec chemin JSON configuré ne peuvent pas être utilisés avec des règles qui utilisent des valeurs prédéfinies pour appliquer des conditions. Si les valeurs sont chargées à partir de JSON au moment de l’exécution, il n’est pas possible d’appliquer une règle prédéfinie.

1. Sous **[!UICONTROL Visibilité]**, sélectionnez l’option **[!UICONTROL Visible, d’après la nouvelle règle]**.

1. Appuyez/cliquez sur **[!UICONTROL Ajouter une règle]** et sélectionnez le champ **[!UICONTROL Type de ressource]** pour créer une dépendance. Sélectionnez également la valeur du champ sur lequel vous souhaitez créer la dépendance. Dans ce cas, sélectionnez **[!UICONTROL Vidéo]**. Appuyez/cliquez sur **[!UICONTROL Terminé]** pour enregistrer les modifications.

   ![define_visibilityrule](assets/define_visibilityrule.png)

   >[!NOTE]
   >
   >Appuyez/cliquez sur des espaces (ou à tout autre endroit que les valeurs) pour réinitialiser les valeurs. Dans ce cas, vous devez les sélectionner à nouveau.

   >[!NOTE]
   >
   >Vous pouvez appliquer les conditions **[!UICONTROL Condition requise]** et **[!UICONTROL Visibilité]** indépendamment l’une de l’autre.

1. De même, créez une dépendance entre la valeur Vidéo dans le champ Type de ressource et d’autres champs, tels que Codec et Durée.
1. Répétez les étapes pour créer une dépendance entre les ressources de documents (PDF, Word) dans le champ **[!UICONTROL Type de ressource]** et des champs tels que Nombre de pages et Auteur.
1. Cliquez sur **[!UICONTROL Enregistrer]**. Appliquez le schéma de métadonnées à un dossier.

1. Accédez au dossier auquel vous avez appliqué le schéma de métadonnées et ouvrez la page des propriétés d’une ressource. Selon votre choix dans le champ Type de ressource, les champs de métadonnées en cascade pertinents s’affichent.

   ![Métadonnées en cascade pour une ressource vidéo](assets/video_asset.png)

   *Figure : Métadonnées en cascade pour une ressource vidéo*

   ![Métadonnées en cascade pour une ressource de document](assets/doc_type_fields.png)

   *Figure : Métadonnées en cascade pour une ressource de document*
