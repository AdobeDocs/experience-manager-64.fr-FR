---
title: "Base de données SQL Server\_: réglage précis de la configuration"
seo-title: "Microsoft SQL Server database: Fine-tuning the configuration"
description: Découvrez comment vous pouvez affiner la configuration de votre base de données Microsoft SQL Server.
seo-description: Learn how you can fine tune the configuration of your Microsoft SQL Server database.
uuid: 2d618aab-3c67-4edb-a28f-a20904689e6f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS, SG_AEMFORMS
discoiquuid: 70559a94-42ea-411a-a32f-5f38bc17ff96
exl-id: 5392027c-eb5a-49c4-bf9b-fe7d399ae0a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 10%

---

# Base de données SQL Server : réglage précis de la configuration {#microsoft-sql-server-database-fine-tuning-the-configuration}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous devez modifier les paramètres de configuration par défaut lors de l’utilisation de Microsoft SQL Server. Cliquez avec le bouton droit sur le serveur local dans Oracle Enterprise Manager pour accéder à la boîte de dialogue des propriétés.

## Paramètres de mémoire {#memory-settings}

Remplacez l’allocation de mémoire minimale par un nombre aussi grand que possible. Si la base de données est exécutée sur un ordinateur distinct, utilisez toute la mémoire. Les paramètres par défaut n’allouent pas de manière agressive la mémoire, ce qui nuit aux performances sur presque toutes les bases de données. Vous devez être plus agressif dans l’allocation de mémoire sur les machines de production.

## Paramètres du processeur {#processor-settings}

Modifiez les paramètres du processeur et, surtout, cochez la case Renforcer la priorité SQL Server sous Windows afin que le serveur utilise autant de cycles que possible. Le paramètre Utiliser les fibres NT est moins important, mais vous pouvez également le sélectionner.

## Paramètres de base de données {#database-settings}

Modifiez les paramètres de la base de données. Le paramètre le plus important est l’ Intervalle de récupération , qui spécifie le temps maximal d’attente de récupération après un blocage. Le paramètre par défaut est d’une minute. L’utilisation d’une valeur plus élevée, comprise entre 5 et 15 minutes, améliore les performances car elle donne au serveur plus de temps pour écrire les modifications du journal de base de données dans les fichiers de base de données.

>[!NOTE]
>
>Ce paramètre ne compromet pas le comportement transactionnel, car il ne modifie que la longueur de relecture du fichier journal qui doit être effectuée au démarrage.

Définissez la taille d’ espace alloué pour le journal et le fichier de données sur une taille beaucoup plus grande que la base de données initiale. Tenez compte de la croissance de la base de données sur une année. Idéalement, le journal et les fichiers de données sont alloués de manière contiguë afin que les données ne soient pas fragmentées sur tout le disque.
