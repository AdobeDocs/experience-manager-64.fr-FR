---
title: Utilisation des points de départ
seo-title: Working with Startpoints
description: Travailler avec un processus AEM Forms défini dans Workbench depuis votre périphérique mobile.
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 80%

---

# Utilisation des points de départ {#working-with-startpoints}

Un point de départ appelle un processus créé dans Workbench. Il est associé à un formulaire qui appelle le processus lors de l’envoi du formulaire. Voir [Présentation du site de référence Geometrixx Finance](/help/forms/using/finance-reference-site-walkthrough.md) pour comprendre les processus.

>[!NOTE]
>
>Les termes « points de départ », « processus de démarrage » et « formulaire » sont indifféremment utilisés pour désigner ce concept.

Pour lancer un processus à partir de l’application AEM Forms, vous devez disposer d’un point de départ de type **Workspace** dans votre processus. En outre, vous devez sélectionner l’option **[!UICONTROL Visible dans Mobile Workspace]** pour le point de départ.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Démarrage d’un processus défini dans Workbench**

1. Pour afficher les points de départ disponibles dans l’application AEM Forms, accédez à l’écran [Accueil](/help/forms/using/home-screen.md).
1. Sur le **[!UICONTROL Accueil]** par défaut, l’écran **[!UICONTROL Toutes les Forms]** s’affiche.

   Le point de départ est associé à un formulaire. Appuyez sur le formulaire associé au point de départ dans la liste pour l’ouvrir.

   Le formulaire associé au point de départ s’ouvre.

1. Saisissez les informations dans le **[!UICONTROL formulaire]** Point de départ.

   Vous pouvez ajouter des annotations à cette tâche à l’aide du bouton de la [pièce jointe](/help/forms/using/add-attachments.md).

1. Une fois que vous avez remplir le formulaire, appuyez sur le bouton **Envoyer.**

Si l’application est hors ligne, le formulaire et ses données sont enregistrés dans le dossier de boîte d’envoi.

Si l’application est en ligne, la tâche est synchronisée avec le serveur AEM Forms et assignée à l’utilisateur spécifié dans le processus.

Pour effectuer la tâche présente dans la liste des tâches, consultez la section [Ouverture d’une tâche](/help/forms/using/open-task.md).
