---
title: Flux d’activité dans la chronologie
description: 'Cet article décrit comment afficher les journaux d’activité pour les ressources de la chronologie. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Flux d’activité dans la chronologie {#activity-stream-in-timeline}

Cette fonctionnalité affiche les journaux d’activités correspondant aux ressources de la chronologie. Si vous effectuez les opérations liées aux ressources suivantes dans Adobe Experience Manager (AEM) Assets, la fonction de flux d’activités met à jour la chronologie afin de refléter l’activité.

Les opérations suivantes sont consignées dans le flux d’activités :

* Créer
* Supprimer
* Téléchargement (rendus compris)
* Publier
* Annuler la publication
* Approuver
* Refuser
* Déplacer

Les journaux d’activité à afficher dans le journal sont extraits de l’emplacement `/var/audit/com.day.cq.dam/content/dam` dans CRX, où sont conservés les fichiers journaux.

En outre, l’activité du journal est consignée lorsque de nouvelles ressources sont téléchargées ou que des ressources existantes sont modifiées et archivées dans AEM par le biais d’ [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) ou de l’application [de bureau AEM](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html).

>[!NOTE]
>
>Les processus transitoires ne sont pas affichés dans la chronologie, car aucune information d’historique n’est enregistrée pour ces processus.

Pour afficher le flux d’activités, effectuez une ou plusieurs des opérations sur la ressource, sélectionnez la ressource, puis sélectionnez **[!UICONTROL Chronologie]** dans la liste de navigation globale.

![timeline-3](assets/timeline-3.png)

La chronologie affiche le flux d’activités des opérations que vous effectuez sur les ressources.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>L’emplacement de stockage du journal par défaut pour les tâches **Publier** et **Annuler la publication** est `/var/audit/com.day.cq.replication/content`. Pour les tâches **Déplacer**, l’emplacement par défaut est `/var/audit/com.day.cq.wcm.core.page`.
