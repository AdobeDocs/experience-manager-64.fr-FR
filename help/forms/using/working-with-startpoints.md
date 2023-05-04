---
title: Utilisation des points de départ
seo-title: Working with Startpoints
description: Étapes à suivre pour utiliser un processus AEM Forms de votre périphérique mobile défini dans Workbench.
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 50%

---

# Utilisation des points de départ {#working-with-startpoints}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Un point de départ appelle un processus créé dans Workbench. Il est associé à un formulaire qui appelle le processus lors de l’envoi du formulaire. Voir [Présentation du site de référence financière Geometrixx](/help/forms/using/finance-reference-site-walkthrough.md) pour comprendre les processus.

>[!NOTE]
>
>Les termes « points de départ », « processus de démarrage » et « formulaire » sont indifféremment utilisés pour désigner ce concept.

Pour lancer un processus à partir de l’application AEM Forms, vous devez disposer d’un point de départ de type **Espace de travail** dans votre processus. Vous devez également sélectionner la variable **[!UICONTROL Visible dans Mobile Workspace]** pour le point de départ.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Pour démarrer un processus défini dans Workbench**

1. Pour afficher les points de départ disponibles dans l’application AEM Forms, accédez à [Écran d’accueil](/help/forms/using/home-screen.md).
1. Sur l’écran d’**[!UICONTROL Accueil]**, la liste **[!UICONTROL Tous les formulaires]** s’affiche par défaut.

   Le point de départ est associé à un formulaire. Appuyez sur le formulaire associé au point de départ dans la liste pour l’ouvrir.

   Le formulaire associé au point de départ s’ouvre.

1. Saisissez les informations dans le **[!UICONTROL formulaire]** Point de départ.

   Vous pouvez ajouter des annotations à cette tâche à l’aide du bouton de la [pièce jointe](/help/forms/using/add-attachments.md).

1. Une fois que vous avez remplir le formulaire, appuyez sur le bouton **Envoyer.**

Si l’application est hors ligne, le formulaire et ses données sont enregistrés dans le dossier de boîte d’envoi.

Si l’application est en ligne, la tâche est synchronisée avec le serveur AEM Forms et affectée à l’utilisateur spécifié dans le processus.

Pour utiliser la tâche dans votre liste de tâches, voir [Ouverture d’une tâche](/help/forms/using/open-task.md).
