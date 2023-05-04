---
title: "Correspondence Management\_: dépannage"
seo-title: Correspondence Management Troubleshooting
description: Dépannage de Correspondence Management
seo-description: Correspondence Management Troubleshooting
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
feature: Correspondence Management
exl-id: 82a35d81-13d0-435f-875e-6fd0a6d574d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 24%

---

# Correspondence Management : dépannage {#correspondence-management-troubleshooting}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Erreurs lors de l’enregistrement d’une lettre {#errors-when-saving-a-letter}

### Problème {#issue}

L’une des erreurs suivantes s’affichait lors de l’enregistrement d’une lettre :

* Liaison de données non présente pour le module de texte
* Indiquez les informations de propriété nécessaires pour les éléments suivants :

### Raison {#reason}

Ces erreurs peuvent se produire en raison de l’une des raisons suivantes :

* Un dictionnaire de données est lié à la lettre mais n’est pas présent sur le serveur.
* Un dictionnaire de données est lié à la lettre, mais son nom comporte un trait de soulignement (_).

### Solution {#workaround}

Assurez-vous que le dictionnaire de données que vous utilisez dans la lettre est présent sur le serveur et que son nom ne comporte pas de trait de soulignement (_).

## Erreur lors de la prévisualisation d’une lettre {#error-when-previewing-a-letter}

### Problème {#issue-1}

Lors de la prévisualisation d’une lettre, l’erreur &quot;Erreur lors du chargement de la lettre : Impossible d’importer la ressource à partir d’une entrée XML&quot; s’affiche même lorsqu’une ressource de texte précédemment non publiée dans la lettre est publiée.

### Solution {#workaround-1}

Réinitialisez le cache de lettres sur l’instance de publication en procédant comme suit, puis réessayez d’afficher la lettre :

1. Accédez à **`https://[server]:[port]/[contextPath]/system/console/configMgr`** et connectez-vous en tant qu’administrateur.
1. Sélectionnez **Configurations de Correspondence Management**.
1. Dans **Configurations de Correspondence Management**, désactivez l’option **Activer le cache de lettre**, puis cliquez sur **Enregistrer**.
1. Activez l’option **Activer le cache de lettre**, puis cliquez sur **Enregistrer**.
1. Réessayez d’afficher la lettre.
