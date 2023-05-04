---
title: Présentation de la structure de dossiers
seo-title: Understanding the folder structure
description: Découvrez comment comprendre la structure de dossiers du code source de l’espace de travail AEM Forms à personnaliser.
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 60%

---

# Présentation de la structure de dossiers {#understanding-the-folder-structure}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les composants de l’espace de travail AEM Forms reposent sur une architecture MVC (modèle-vue-contrôleur) utilisant le modèle Backbone. Chaque composant possède un fichier pour :

* Modèle contenant la logique commerciale.
* Modèle, c’est-à-dire un fichier de HTML contenant des commandes d’interface.
* Vue, qui agit comme une classe Controller sur Template.

Les actifs de tous les composants sont placés dans la structure de dossiers décrite ci-dessous. Pour accéder aux ressources, connectez-vous à CRXDE Lite et accédez à `/libs/ws/js/runtime/`.

**modèles** contient des modèles Backbone.

**vues** contient les vues Backbone.

**modèles** contient uniquement les modèles HTML pour les composants.

**itinéraires** contient les itinéraires universels. Le dossier Templates figurant dans routes contient le code HTML et les références aux composants.

**services** contient l’interface de service permettant d’appeler les API du serveur Adobe Experience Manager au point d’entrée REST.

**util** contient des utilitaires génériques utilisables par plusieurs composants.
