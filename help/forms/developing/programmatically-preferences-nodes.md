---
title: Gestion par programmation des PreferencesNodes
seo-title: Programmatically managing the PreferencesNodes
description: Utilisez l’API Preferences Manager Service (Java) pour gérer par programmation les noeuds Preferences.
seo-description: Use the Preferences Manager Service API (Java) to programmatically manage the Preferences Nodes.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: d580b32c-a344-4a8c-bd61-0949da76d981
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Gestion par programmation des noeuds de préférences {#programmatically-managing-the-preferencesnodes}

Cette rubrique décrit comment utiliser l’API Preferences Manager Service (Java) pour gérer par programmation les noeuds Preferences.

Vous pouvez modifier manuellement les paramètres de configuration à partir de l’interface utilisateur de l’administrateur. Pour modifier les options, accédez à `Home>Settings>User Management> Configuration>Manual Configuration`. Importer `config.xml` après avoir apporté les modifications, vous remarquerez que toutes les modifications, à l’exception des modifications apportées au noeud `/Adobe/Adobe Experience Manager Forms/Config/UM persist` sont perdues. L’aperçu de l’importation et de l’exportation User Management ne prend pas en charge la modification des paramètres de configuration pour d’autres composants. Désormais, ces modifications peuvent être effectuées à l’aide de `PreferencesManagerServiceClient` API.

**Résumé des étapes** Pour gérer par programmation les noeuds de préférences, procédez comme suit :

1. Inclure les fichiers de projet.
1. Création d’un client PreferencesManagerService
1. Appeler les opérations de rôle ou d’autorisation appropriées

**Inclure les fichiers de projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Création d’un client PreferencesManagerService**

Avant d’effectuer par programmation une opération User Management PreferencesManagerService, vous devez créer un client PreferencesManagerService. Avec l’API Java, cela se fait en créant un objet PreferencesManagerServiceClient .

**Appeler les opérations de rôle ou d’autorisation appropriées**

Une fois le client de service créé, vous pouvez appeler les opérations du Gestionnaire de préférences. Le client de service vous permet de lire et de définir des autorisations.
