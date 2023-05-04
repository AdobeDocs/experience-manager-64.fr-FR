---
title: Importation et exportation de métadonnées en bloc
description: Cet article décrit comment importer et exporter des métadonnées en bloc.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 956cdec4-2ba8-43c9-9122-564d764f4681
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 50%

---

# Importation et exportation de métadonnées en bloc {#bulk-metadata-import-and-export}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

[!DNL Experience Manager] Assets permet d’importer des métadonnées de ressources par lot à l’aide d’un fichier CSV. Vous pouvez effectuer des mises à jour en masse des ressources récemment chargées ou des ressources existantes en important un fichier CSV. Vous pouvez également ingérer des métadonnées de ressources en masse à partir d’un système tiers au format CSV.

## Importation de métadonnées {#import-metadata}

L’importation de métadonnées est asynchrone et ne nuit pas aux performances du système. La mise à jour simultanée des métadonnées de plusieurs ressources peut être gourmande en ressources en raison de l’activité d’écriture différée XMP si l’indicateur de workflow est coché. Planifiez un tel import pendant l’utilisation allégée du serveur afin d’éviter un impact sur les performances des autres utilisateurs.

>[!NOTE]
>
>Pour importer des métadonnées sur des espaces de noms personnalisés, commencez par enregistrer les espaces de noms.

Pour importer des métadonnées en bloc, procédez comme suit :

1. Accédez à l’interface utilisateur d’Assets, puis appuyez/cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Dans le menu, sélectionnez **[!UICONTROL Métadonnées]**.
1. Sur le **[!UICONTROL Importation des métadonnées]** , appuyez/cliquez sur la page **[!UICONTROL Sélectionner un fichier]**.  Sélectionnez le fichier CSV contenant les métadonnées.
1. Assurez-vous que le fichier CSV contient les paramètres suivants :

   | Paramètres d’importation des métadonnées | Description |
   |:---|:---|
   | [!UICONTROL Taille du lot] | Nombre de ressources d’un lot pour lesquelles des métadonnées doivent être importées. La valeur par défaut est 50. La valeur maximale est 100. |
   | [!UICONTROL Séparateur de champs] | La valeur par défaut est `,` - une virgule. Vous pouvez spécifier n’importe quel autre caractère. |
   | [!UICONTROL Délimiteur à plusieurs valeurs] | Séparateur des valeurs de métadonnées. La valeur par défaut est `|` - une pipe. |
   | [!UICONTROL Lancer les workflows] | False par défaut. Lorsque la valeur est définie sur true et que les paramètres par défaut sont appliqués pour la variable `DAM Metadata WriteBack Workflow` (qui écrit des métadonnées dans les données XMP binaires). L’activation des workflows a un impact sur les performances du système. |
   | [!UICONTROL Nom de colonne du chemin d’accès à la ressource] | Définit le nom de la colonne du fichier CSV avec des ressources. |

1. Appuyez/cliquez sur **[!UICONTROL Importer]** dans la barre d’outils. Une fois les métadonnées importées, une notification est envoyée à votre boîte de réception de notifications. Accédez à la page de propriété des ressources et vérifiez que les valeurs des métadonnées sont correctement importées pour les ressources.

Pour ajouter une date et un horodatage au cours de l’importation de métadonnées, utilisez le format de date et d’heure `YYYY-MM-DDThh:mm:ss.fff-00:00`. La date et l’heure sont séparées par `T`, `hh` correspond aux heures au format 24 heures, `fff` aux nanosecondes et `-00:00` au décalage du fuseau horaire. Par exemple, `2020-03-26T11:26:00.000-07:00` correspond au 26 mars 2020 à 11:26:00.000, heure du Pacifique.

>[!CAUTION]
>
>Si la date ne correspond pas au format `YYYY-MM-DDThh:mm:ss.fff-00:00`, les valeurs de date ne sont pas définies. Les formats de date du fichier CSV de métadonnées exportées sont au format `YYYY-MM-DDThh:mm:ss-00:00`. Si vous souhaitez l’importer, convertissez son contenu dans un format acceptable en ajoutant la valeur en nanosecondes indiquée par `fff`.

## Exportation des métadonnées {#export-metadata}

Voici quelques cas d’utilisation pour l’exportation de métadonnées en bloc :

* Importez les métadonnées dans un système tiers lors de la migration des ressources.
* Partagez des métadonnées de ressource avec une équipe de projet plus étendue.
* Testez ou contrôlez les métadonnées en vue de leur conformité.
* Externalisez les métadonnées pour une localisation distincte.

Vous pouvez exporter des métadonnées pour plusieurs ressources au format CSV. Les métadonnées sont exportées de manière asynchrone et n’ont aucun impact sur les performances du système. Pour exporter des métadonnées, [!DNL Experience Manager] parcourt les propriétés du nœud de ressource `jcr:content/metadata` et de ses nœuds enfants et exporte les propriétés de métadonnées dans un fichier CSV.

Pour exporter des métadonnées de plusieurs ressources en bloc, procédez comme suit :

1. Sélectionnez le dossier de ressources pour lequel vous souhaitez exporter des métadonnées. Dans la barre d’outils, sélectionnez **[!UICONTROL Exporter les métadonnées]**.

1. Dans la boîte de dialogue [!UICONTROL Exportation des métadonnées], indiquez un nom pour le fichier CSV. Pour exporter des métadonnées pour des ressources situées dans des sous-dossiers, sélectionnez **[!UICONTROL Inclure des ressources dans des sous-dossiers]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Sélectionnez les options souhaitées. Indiquez un nom de fichier et, si nécessaire, une date.
1. Dans le **[!UICONTROL Propriétés à exporter]**, indiquez si vous souhaitez exporter toutes les propriétés ou des propriétés spécifiques. Si vous choisissez **[!UICONTROL Selective]** propriétés à exporter, ajoutez les propriétés souhaitées.

1. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Exporter]**. Un message confirme l’exportation des métadonnées. Fermez le message.

1. Ouvrez la notification de la boîte de réception pour la tâche d’exportation. Sélectionnez la tâche et cliquez sur **[!UICONTROL Ouvrir]** dans la barre d’outils. Pour télécharger le fichier CSV avec les métadonnées, appuyez/cliquez sur **[!UICONTROL Téléchargement CSV]** dans la barre d’outils. Cliquez sur **[!UICONTROL Fermer]**.

   ![csv_download](assets/csv_download.png)
