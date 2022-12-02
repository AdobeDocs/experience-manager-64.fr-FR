---
title: Modification en masse des métadonnées de plusieurs ressources et collections
description: Découvrez comment modifier simultanément les métadonnées de nombreuses ressources et collections afin de propager rapidement les modifications de métadonnées courantes.
contentOwner: AG
feature: Asset Management,Metadata,Collections
role: User
exl-id: 3541b50a-f226-4a6a-9c2a-03a5f47f1c23
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 77%

---

# Gestion de plusieurs ressources et collections {#managing-multiple-assets-and-collections}

Découvrez comment modifier les métadonnées de plusieurs ressources et collections simultanément pour propager rapidement les modifications courantes des métadonnées.

Adobe Enterprise Manager Assets vous permet de modifier les métadonnées de plusieurs ressources simultanément afin que vous puissiez rapidement propager les modifications de métadonnées communes en masse aux ressources. Vous pouvez également modifier en bloc les métadonnées de plusieurs collections.

Utilisez la page des propriétés pour effectuer des modifications de métadonnées sur plusieurs ressources ou collections :

* Remplacer les propriétés de métadonnées par une valeur commune
* Ajouter ou modifier des balises

Pour personnaliser la page des propriétés de métadonnées, notamment ajouter, modifier et supprimer des propriétés de métadonnées, utilisez l’éditeur de schéma.

>[!NOTE]
>
>Les méthodes de modification en masse fonctionnent pour les ressources disponibles dans un dossier ou une collection. Pour les ressources disponibles dans plusieurs dossiers ou correspondant à un critère commun, il est possible de mettre à jour les métadonnées en masse à partir des résultats de la recherche de ressources.

## Modification des propriétés de métadonnées de plusieurs ressources {#editing-metadata-properties-of-multiple-assets}

1. Dans l’interface utilisateur Ressources, accédez à l’emplacement des ressources à modifier.
1. Sélectionnez les ressources dont vous souhaitez modifier les propriétés communes.
1. Dans la barre d’outils, cliquez sur **[!UICONTROL Propriétés]** pour ouvrir la page Propriétés des ressources sélectionnées.
1. Modifiez les propriétés de métadonnées des ressources sélectionnées dans les différents onglets.
1. Pour afficher les métadonnées d’une ressource spécifique, désélectionnez les autres ressources dans la liste. Si vous annulez la sélection de quelques ressources sur la page [!UICONTROL Propriétés], les métadonnées de ces ressources ne sont pas mises à jour.
1. Pour sélectionner un schéma de métadonnées différent pour les ressources, cliquez sur **[!UICONTROL Paramètres]** dans la barre d’outils, puis sélectionnez le schéma souhaité. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.
1. Pour ajouter les nouvelles métadonnées aux métadonnées existantes dans les champs contenant plusieurs valeurs, sélectionnez **[!UICONTROL Mode d’ajout]**. Si vous ne sélectionnez pas cette option, les nouvelles métadonnées remplacent les métadonnées existantes dans les champs. Cliquez sur **[!UICONTROL Envoyer]**.

![Le schéma de métadonnées s’applique en bloc à plusieurs ressources.](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>Pour les champs à une seule valeur, les nouvelles métadonnées ne sont pas ajoutées à la valeur existante dans le champ, même si vous sélectionnez **[!UICONTROL Mode d’ajout]**.

## Configuration du nombre maximal de paramètres pour la mise à jour des métadonnées en masse {#configure-limit-for-bulk-metadata-update}

Pour éviter une situation similaire à DOS, procédez comme suit : [!DNL Experience Manager] limite le nombre de paramètres pris en charge dans une requête Sling. Lors de la mise à jour simultanée de plusieurs fichiers, vous pouvez atteindre le nombre maximal de paramètres et les métadonnées ne sont pas mises à jour pour d’autres fichiers. [!DNL Experience Manager] génère l’avertissement suivant dans les journaux :

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Pour modifier le nombre maximal de paramètres, accédez à la console **[!UICONTROL Outils > Opérations > Console web]**, puis changez la valeur de [!UICONTROL Paramètres POST maximum] dans la configuration OSGi de [!UICONTROL gestion des paramètres de requête Sling Apache].

>[!MORELIKETHIS]
>
>* [Modification en bloc des métadonnées de plusieurs collections](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

