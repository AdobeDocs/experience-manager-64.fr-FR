---
title: Importation et exportation de métadonnées en masse
description: Cet article explique comment importer et exporter des métadonnées en masse.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Importation et exportation de métadonnées en masse {#bulk-metadata-import-and-export}

AEM Assets permet d’importer des métadonnées de ressources par lot à l’aide d’un fichier CSV. Vous pouvez effectuer des mises à jour par lot pour les ressources récemment transférées ou les ressources existantes en important un fichier CSV. Vous pouvez également assimiler des métadonnées de ressources par lot à partir d’un système tiers au format CSV.

## Importation de métadonnées {#import-metadata}

L’importation de métadonnées est asynchrone et ne nuit pas aux performances du système. La mise à jour simultanée des métadonnées pour plusieurs ressources peut être gourmande en ressources en raison de l’activité d’écriture différée XMP si l’indicateur de workflow est coché. Planifiez une importation de ce type quand le serveur est peu utilisé afin que les performances d’autres utilisateurs ne soient pas affectées.

>[!NOTE]
>
>Pour importer des métadonnées sur des espaces de noms personnalisés, commencez par enregistrer les espaces de noms.

1. Accédez à l’IU Assets et appuyez/cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Dans le menu, sélectionnez **[!UICONTROL Métadonnées]**.
1. On the **[!UICONTROL Metadata Import]** page, tap/click the **[!UICONTROL Select File]**.  Sélectionnez le fichier CSV contenant les métadonnées.
1. Spécifiez les paramètres suivants :

   | Paramètres d’importation de métadonnées | Description |
   |:---|:---|
   | [!UICONTROL Taille du lot] | Nombre de ressources dans un lot pour lesquelles les métadonnées doivent être importées. La valeur par défaut est 50. La valeur maximale est 100. |
   | [!UICONTROL Séparateur de champs] | La valeur par défaut est une virgule. Vous pouvez spécifier n’importe quel autre caractère. |
   | [!UICONTROL Délimiteur à plusieurs valeurs] | Séparateur des valeurs de métadonnées. La valeur par défaut est  | . |
   | [!UICONTROL Lancer les workflows] | Faux par défaut. Lorsque la valeur est définie sur true, les paramètres de lanceur par défaut sont appliqués au flux de travail DAM Metadata WriteBack (qui écrit les métadonnées dans les données XMP binaires). L’activation des workflows de lancement ralentit le système. |
   | [!UICONTROL Nom de colonne du chemin d’accès à l’actif] | Définit le nom de la colonne du fichier CSV avec des ressources. |

1. Appuyez/cliquez sur **[!UICONTROL Importer]** dans la barre d’outils. Une fois les métadonnées importées, une notification est envoyée à votre boîte de réception de notifications. Accédez à la page de propriété des ressources et vérifiez que les valeurs des métadonnées sont correctement importées pour les ressources.

<!-- TBD: Format characters in the table using backticks and add UICONTROL after table is converted to MD
-->

## Exportation des métadonnées {#export-metadata}

Vous pouvez exporter des métadonnées pour plusieurs fichiers au format CSV. Les métadonnées sont exportées de manière asynchrone et n’ont aucun impact sur les performances du système. To export metadata, AEM traverses through the properties of the asset node `jcr:content/metadata` and its child nodes and exports the metadata properties in a CSV file.

Voici quelques cas d’utilisation pour l’exportation de métadonnées par lot :

* Importation des métadonnées dans un système tiers lors de la migration des fichiers.
* Partage des métadonnées de ressources avec une équipe de projet plus large.
* Test ou contrôle des métadonnées pour la conformité.
* Externalisation des métadonnées pour une localisation distincte.

1. Sélectionnez le dossier de ressources pour lequel vous souhaitez exporter des métadonnées. Dans la barre d’outils, sélectionnez **[!UICONTROL Exporter les métadonnées]**.

1. Dans la boîte de dialogue Exportation des métadonnées, indiquez un nom pour le fichier CSV. Pour exporter des métadonnées des ressources dans les sous-dossiers, sélectionnez **[!UICONTROL Inclure les ressources dans les sous-dossiers]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Sélectionnez les options souhaitées. Indiquez un nom de fichier et, si nécessaire, une date.
1. In the **[!UICONTROL Properties to be exported]** specify whether you want to export all or specific properties. If you choose **[!UICONTROL Selective]** properties to be exported, add the desired properties.

1. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Exporter]**. Un message confirme que les métadonnées ont été exportées. Fermez le message.

1. Ouvrez la notification de la boîte de réception pour la tâche d’exportation. Sélectionnez la tâche et cliquez sur **[!UICONTROL Ouvrir]** dans la barre d’outils. Pour télécharger le fichier CSV avec les métadonnées, appuyez/cliquez sur **[!UICONTROL Téléchargement CSV]** dans la barre d’outils. Cliquez sur **[!UICONTROL Fermer]**.

   ![csv_download](assets/csv_download.png)
