---
title: Activer et désactiver le mode de sauvegarde sécurisé
seo-title: Enabling and disabling safe backup mode
description: Sur la page Paramètres de sauvegarde, vous pouvez utiliser AEM forms en mode de sauvegarde sécurisé afin de sauvegarder de manière fiable votre base de données et votre répertoire de stockage global de documents (GDS). Découvrez comment activer et désactiver le mode de sauvegarde sécurisé.
seo-description: On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory. Learn how to enable and disable safe backup mode.
uuid: 2fdeaeaf-e969-40a4-8aee-1f2b627d3942
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fda71e4-78a1-4581-9d02-bf06a75c3bcb
exl-id: 309a8cef-e84d-485b-9a7c-786a93e83c85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 8%

---

# Activer et désactiver le mode de sauvegarde sécurisé {#enabling-and-disabling-safe-backup-mode}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Sur la page Paramètres de sauvegarde, vous pouvez utiliser AEM forms en mode de sauvegarde sécurisé afin de sauvegarder de manière fiable votre base de données et votre répertoire de stockage global de documents (GDS).

AEM forms fonctionne normalement en mode de sauvegarde sécurisé, mais il ne supprime pas activement les fichiers du répertoire de stockage global de documents.

>[!NOTE]
>
>La définition de cette option ne sauvegarde pas votre système. il prépare votre système à la sauvegarde.

## Activation du mode de sauvegarde sécurisé {#enable-safe-backup-mode}

1. Dans Administration Console, cliquez sur Paramètres > Paramètres de Core System > Paramètres de sauvegarde.
1. Sur la page Paramètres de sauvegarde, sélectionnez Fonctionner en mode de sauvegarde sécurisé et cliquez sur OK.

>[!NOTE]
>
>Si le système s’exécute déjà en mode de sauvegarde sécurisé, une nouvelle réservation ne sera pas créée lorsque vous cliquerez sur OK.

## Désactivation du mode de sauvegarde sécurisé {#disable-safe-backup-mode}

1. Dans Administration Console, cliquez sur Paramètres > Paramètres de Core System > Paramètres de sauvegarde.
1. Dans la page Paramètres de sauvegarde, désélectionnez Fonctionner en mode de sauvegarde sécurisé et cliquez sur OK.
