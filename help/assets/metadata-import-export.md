---
title: Importation et exportation de métadonnées en masse
description: Cet article explique comment importer et exporter des métadonnées en masse.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 254a9dec248255f8f76db3531c65b54fb4ebff0c
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 75%

---


# Importation et exportation de métadonnées en bloc {#bulk-metadata-import-and-export}

AEM Assets permet d’importer des métadonnées de ressources par lot à l’aide d’un fichier CSV. Vous pouvez effectuer des mises à jour par lot pour les ressources récemment transférées ou les ressources existantes en important un fichier CSV. Vous pouvez également assimiler des métadonnées de ressources par lot à partir d’un système tiers au format CSV.

## Importation de métadonnées   {#import-metadata}

L’importation de métadonnées est asynchrone et ne nuit pas aux performances du système. La mise à jour simultanée des métadonnées pour plusieurs ressources peut être gourmande en ressources en raison de l’activité d’écriture différée XMP si l’indicateur de workflow est coché. Planifiez une telle importation lors d’une utilisation allégée du serveur afin d’éviter un impact sur les performances des autres utilisateurs.

>[!NOTE]
>
>Pour importer des métadonnées sur des espaces de noms personnalisés, commencez par enregistrer les espaces de noms.

Pour importer des métadonnées en bloc, procédez comme suit :

1. Accédez à l’IU Assets et appuyez/cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Dans le menu, sélectionnez **[!UICONTROL Métadonnées]**.
1. Sur la page **[!UICONTROL Importation de métadonnées]**, appuyez/cliquez sur **[!UICONTROL Sélectionner un fichier]**.  Sélectionnez le fichier CSV contenant les métadonnées.
1. Assurez-vous que le fichier CSV contient les paramètres suivants :

   | Paramètres d’importation des métadonnées | Description |
   |:---|:---|
   | [!UICONTROL Taille du lot] | Nombre de ressources dans un lot pour lesquelles les métadonnées doivent être importées. La valeur par défaut est 50. La valeur maximale est 100. |
   | [!UICONTROL Séparateur de champs] | La valeur par défaut est `,` - une virgule. Vous pouvez spécifier n’importe quel autre caractère. |
   | [!UICONTROL Délimiteur à plusieurs valeurs] | Séparateur des valeurs de métadonnées. La valeur par défaut est `|` - barre verticale. |
   | [!UICONTROL Lancer les workflows] | Faux par défaut. Lorsque ce paramètre est défini sur true, les paramètres par défaut du lanceur sont appliqués à `DAM Metadata WriteBack Workflow` (qui écrit les métadonnées dans les données XMP binaires). L’activation des workflows de lancement a un impact sur les performances du système. |
   | [!UICONTROL Nom de colonne du chemin d’accès à la ressource] | Définit le nom de la colonne du fichier CSV avec des ressources. |

1. Appuyez/cliquez sur **[!UICONTROL Importer]** dans la barre d’outils. Une fois les métadonnées importées, une notification est envoyée à votre boîte de réception de notifications. Accédez à la page de propriété des ressources et vérifiez que les valeurs des métadonnées sont correctement importées pour les ressources.

Pour ajouter une date et un horodatage au cours de l’importation de métadonnées, utilisez le format de date et d’heure `YYYY-MM-DDThh:mm:ss.fff-00:00`. La date et l’heure sont séparées par `T`, `hh` correspond aux heures au format 24 heures, `fff` aux nanosecondes et `-00:00` au décalage du fuseau horaire. Par exemple, `2020-03-26T11:26:00.000-07:00` correspond au 26 mars 2020 à 11h26:00.000, heure du Pacifique.

>[!CAUTION]
>
>Si la date ne correspond pas au format `YYYY-MM-DDThh:mm:ss.fff-00:00`, les valeurs de date ne sont pas définies. Les formats de date du fichier CSV de métadonnées exportées sont au format `YYYY-MM-DDThh:mm:ss-00:00`. Si vous souhaitez l’importer, convertissez son contenu dans un format acceptable en ajoutant la valeur en nanosecondes indiquée par `fff`.

## Exportation des métadonnées {#export-metadata}

Voici quelques cas d’utilisation pour l’exportation de métadonnées par lot :

* Importation des métadonnées dans un système tiers lors de la migration des fichiers.
* Partage des métadonnées de ressources avec une équipe de projet plus large.
* Test ou contrôle des métadonnées pour la conformité.
* Externalisation des métadonnées pour une localisation distincte.

Vous pouvez exporter des métadonnées pour plusieurs fichiers au format CSV. Les métadonnées sont exportées de manière asynchrone et n’ont aucun impact sur les performances du système. Pour exporter des métadonnées, AEM parcourt les propriétés du nœud de ressource `jcr:content/metadata` et de ses nœuds enfants et exporte les propriétés de métadonnées dans un fichier CSV.

Pour exporter en bloc des métadonnées de plusieurs fichiers, procédez comme suit :

1. Sélectionnez le dossier de ressources pour lequel vous souhaitez exporter des métadonnées. Dans la barre d’outils, sélectionnez **[!UICONTROL Exporter les métadonnées]**.

1. Dans la boîte de dialogue [!UICONTROL Exportation des métadonnées], spécifiez un nom pour le fichier CSV. Pour exporter des métadonnées des ressources dans les sous-dossiers, sélectionnez **[!UICONTROL Inclure les ressources dans les sous-dossiers]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Sélectionnez les options souhaitées. Indiquez un nom de fichier et, si nécessaire, une date.
1. Dans la section **[!UICONTROL Propriétés à exporter]**, indiquez si vous souhaitez exporter toutes les propriétés ou des propriétés spécifiques. Si vous sélectionnez les propriétés **[!UICONTROL Sélective]** à exporter, ajoutez les propriétés souhaitées.

1. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Exporter]**. Un message confirme que les métadonnées ont été exportées. Fermez le message.

1. Ouvrez la notification de la boîte de réception pour la tâche d’exportation. Sélectionnez la tâche et cliquez sur **[!UICONTROL Ouvrir]** dans la barre d’outils. Pour télécharger le fichier CSV avec les métadonnées, appuyez/cliquez sur **[!UICONTROL Téléchargement CSV]** dans la barre d’outils. Cliquez sur **[!UICONTROL Fermer]**.

   ![csv_download](assets/csv_download.png)
