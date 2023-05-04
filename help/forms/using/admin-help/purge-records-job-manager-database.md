---
title: Purger les enregistrements de la base de données de Job Manager
seo-title: Purge records from the Job Manager database
description: Les données de processus volumineuses peuvent entraîner une baisse des performances d’AEM forms. Il est recommandé de purger les données de processus lorsque les enregistrements ne sont plus nécessaires.
seo-description: Large process data can result in lower AEM forms performance. It is good practice to purge process data when records are no longer necessary.
uuid: cf214498-36e9-4dcc-b4d4-e7c46f80dbab
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 69a406f2-4fa8-40bb-b671-7b0f5b6a2c4c
exl-id: be2e2a4b-5aac-4612-81b6-b4bbb3036d77
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 5%

---

# Purger les enregistrements de la base de données de Job Manager {#purge-records-from-the-job-manager-database}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les données de processus générées lors de l’appel d’un processus de longue durée peuvent devenir trop volumineuses, ce qui entraîne des performances d’AEM forms plus faibles et une utilisation d’espace disque inutile. Il est recommandé de purger les données de processus lorsque les enregistrements ne sont plus nécessaires.

Vous pouvez utiliser Administration Console pour effectuer une purge individuelle des enregistrements obsolètes ou planifier des purges automatiques régulières. D’autres méthodes de purge des enregistrements obsolètes sont présentées dans la section [Purge des données de processus](/help/forms/using/admin-help/purging-process-data.md#purging-process-data).

**Accès à la page Planificateur de purge de tâche**

1. Dans Administration Console, cliquez sur Health Monitor dans le coin supérieur droit de la page.
1. Cliquez sur l’onglet Planificateur de purge de tâche .

Les informations sur les purges actuellement planifiées s’affichent dans la zone Informations du planificateur de purge de tâche.

>[!NOTE]
>
>Cliquer sur Arrêter le planificateur arrête les purges planifiées à l’avenir, mais n’arrête pas une tâche de purge déjà en cours.

**Planification d’une purge unique**

1. Sélectionnez Une seule fois.
1. Dans la zone Purge Completed Records Filter, indiquez le nombre de jours ou de semaines après lesquels un enregistrement est considéré comme obsolète et prêt à être purgé.

   >[!NOTE]
   >
   >Les enregistrements liés à des processus qui n’ont pas été terminés ne sont pas purgés, même s’ils sont plus anciens que l’âge spécifié.

1. Spécifiez quand la purge aura lieu. Cochez la case Utiliser la date et l’heure actuelles ou décochez la case et cliquez sur les icônes de calendrier et d’horloge pour spécifier la date et l’heure auxquelles la purge sera effectuée.

   >[!NOTE]
   >
   >Si vous spécifiez une date et une heure de début antérieures à la date actuelle, la purge se produit immédiatement lorsque vous cliquez sur Démarrer le planificateur.

1. Cliquez sur Démarrer le planificateur. Tous les paramètres du planificateur précédemment planifiés sont remplacés par les nouveaux paramètres.

**Configuration d’un calendrier de purge automatique**

1. Sélectionnez Récurrent Every et indiquez le nombre de jours ou de semaines entre les purges.
1. Dans la zone Purge Completed Records Filter, indiquez le nombre de jours ou de semaines après lesquels un enregistrement est considéré comme obsolète et prêt à être purgé. Vous ne pouvez pas définir la valeur sur `0`.

   >[!NOTE]
   >
   >Les enregistrements liés à des processus qui n’ont pas été terminés ne sont pas purgés, même s’ils sont plus anciens que l’âge spécifié.

1. Spécifiez quand les purges commenceront. Cochez la case Utiliser la date et l’heure actuelles ou décochez la case et cliquez sur les icônes de calendrier et d’horloge pour spécifier la date et l’heure auxquelles la purge sera effectuée.

   >[!NOTE]
   >
   >Si vous spécifiez une date et une heure de début antérieures à la date actuelle, AEM forms calcule la prochaine date de début logique en fonction de la date que vous avez spécifiée. Si, par exemple, vous programmez que les purges de la tâche se produisent chaque semaine à partir du 7 avril, et qu’elles sont désormais le 9 avril, la première purge aura lieu le 14 avril.

1. Cliquez sur Démarrer le planificateur. Tous les paramètres du planificateur précédemment planifiés sont remplacés par les nouveaux paramètres.
