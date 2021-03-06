---
title: '"Correspondence Management : dépannage"'
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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 100%

---

# Correspondence Management : dépannage {#correspondence-management-troubleshooting}

## Erreurs lors de l’enregistrement d’une lettre {#errors-when-saving-a-letter}

### Problème {#issue}

L’une des erreurs suivantes s’est affichée lors de l’enregistrement d’une lettre :

* La liaison de données n’est pas définie pour le module de texte
* Fournissez les informations de propriété nécessaires pour les éléments suivants

### Raison {#reason}

Ces erreurs peuvent se produire à cause de l’une des raisons suivantes :

* Un dictionnaire de données est associé à la lettre, mais n’est pas présent sur le serveur.
* Un dictionnaire de données est associé à la lettre, mais son nom comporte un caractère de soulignement (_).

### Solution {#workaround}

Assurez-vous que le dictionnaire de données utilisé dans la lettre est présent sur le serveur et que son nom ne comporte aucun trait de soulignement (_).

## Erreur lors de la prévisualisation d’une lettre {#error-when-previewing-a-letter}

### Problème {#issue-1}

Lors de la prévisualisation d’une lettre, l’erreur « Erreur lors du chargement de la lettre : importation de l’actif impossible depuis l’entrée XML » apparaît même lorsqu’un actif de texte précédemment non publié dans la lettre est publié.

### Solution {#workaround-1}

Réinitialisez le cache de lettre sur l’instance de publication en suivant les étapes ci-après, puis réessayez d’afficher la lettre :

1. Accédez à **`https://[server]:[port]/[contextPath]/system/console/configMgr`** et connectez-vous en tant qu’administrateur.
1. Sélectionnez **Configurations de Correspondence Management**.
1. Dans **Configurations de Correspondence Management**, désactivez l’option **Activer le cache de lettre**, puis cliquez sur **Enregistrer**.
1. Activez l’option **Activer le cache de lettre**, puis cliquez sur **Enregistrer**.
1. Réessayez d’afficher la lettre.
