---
title: Activation et désactivation du mode de sauvegarde sécurisé
seo-title: Enabling and disabling safe backup mode
description: La page Paramètres de sauvegarde vous permet d’exécuter AEM forms en mode de sauvegarde sécurisé, de façon à sauvegarder votre base de données et votre répertoire de stockage global de documents en toute sécurité. Découvrez comment activer et désactiver le mode de sauvegarde sécurisé.
seo-description: On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory. Learn how to enable and disable safe backup mode.
uuid: 2fdeaeaf-e969-40a4-8aee-1f2b627d3942
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fda71e4-78a1-4581-9d02-bf06a75c3bcb
exl-id: 309a8cef-e84d-485b-9a7c-786a93e83c85
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 100%

---

# Activation et désactivation du mode de sauvegarde sécurisé {#enabling-and-disabling-safe-backup-mode}

La page Paramètres de sauvegarde vous permet d’exécuter AEM forms en mode de sauvegarde sécurisé, de façon à sauvegarder votre base de données et votre répertoire de stockage global de documents en toute sécurité.

En mode de sauvegarde sécurisé, AEM forms fonctionne normalement, mais sans supprimer activement les fichiers du répertoire de stockage global de documents.

>[!NOTE]
>
>la définition de cette option ne sauvegarde pas le système, mais le prépare à cette opération.

## Activation du mode de sauvegarde sécurisé {#enable-safe-backup-mode}

1. Dans Administration Console, cliquez sur Paramètres > Paramètres de Core System > Paramètres de sauvegarde.
1. Dans la page Paramètres de sauvegarde, sélectionnez Fonctionner en mode de sauvegarde sécurisé et cliquez sur OK.

>[!NOTE]
>
>si le système fonctionne déjà en mode de sauvegarde sécurisé, aucune réservation n’est créée lorsque vous cliquez sur OK.

## Désactivation du mode de sauvegarde sécurisé {#disable-safe-backup-mode}

1. Dans Administration Console, cliquez sur Paramètres > Paramètres de Core System > Paramètres de sauvegarde.
1. Dans la page Paramètres de sauvegarde, désélectionnez Fonctionner en mode de sauvegarde sécurisé et cliquez sur OK.
