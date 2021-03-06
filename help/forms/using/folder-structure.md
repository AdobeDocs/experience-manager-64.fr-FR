---
title: Présentation de la structure de dossiers
seo-title: Understanding the folder structure
description: Description de la structure des dossiers du code source de l’espace de travail AEM Forms à personnaliser.
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 62%

---

# Présentation de la structure de dossiers {#understanding-the-folder-structure}

Les composants de l’espace de travail AEM Forms reposent sur une architecture MVC (modèle-vue-contrôleur) utilisant le modèle Backbone. Chaque composant possède un fichier pour :

* Un modèle contenant une logique de gestion.
* Un fichier HTML contrôleur contenant des commandes d’interface.
* Une vue agissant comme une classe Controller sur le contrôleur.

Les actifs de tous les composants sont placés dans la structure de dossiers décrite ci-dessous. Pour accéder aux ressources, connectez-vous à CRXDE Lite et accédez à `/libs/ws/js/runtime/`.

**models** Contient des modèles Backbone.

**views** Contient les vues Backbone.

**templates** Contient uniquement les modèles de HTML pour les composants.

**routes** Contient des itinéraires universels. Le dossier Templates figurant dans routes contient le code HTML et les références aux composants.

**services** Contient l’interface de service pour appeler les API du serveur Adobe Experience Manager sur le point de terminaison REST.

**util** Contient des utilitaires génériques utilisables par plusieurs composants.
