---
title: Écran d’accueil
seo-title: Home screen
description: Description des composants de l’écran d’accueil de l’application AEM Forms
seo-description: Description of the components of the AEM Forms app Home screen
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
exl-id: b8f515fd-7ab7-4237-9a35-2840f708e856
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 97%

---

# Écran d’accueil {#home-screen}

Lorsque vous vous connectez à l’application AEM Forms, vous êtes redirigé vers l’écran d’accueil.

## Écran d’accueil par défaut {#default-home-screen}

Par défaut, l’écran d’accueil affiche tous les formulaires, y compris les points de départ et les tâches (si le serveur connecté est activé pour le flux de travail d’AEM Forms), avec les vignettes associées. Vous pouvez spécifier les vignettes dans le serveur AEM Forms.

La figure suivante est annotée avec les légendes des principaux composants de l’écran d’accueil.
![Écran d’accueil de l’application Forms](assets/home-screen-1.png)
[Cliquez pour agrandir](assets/home-screen-1-1.png)

1. **Bouton de menu :** appuyez sur le bouton **Menu** pour accéder aux tâches, aux formulaires, à la boîte d’envoi et aux paramètres. Si votre application AEM Forms est connectée à un serveur AEM Forms JEE, vous pouvez voir l’option Tâches. L’option de tâches stocke également les brouillons créés à partir des tâches dans un processus. Pour les serveurs AEM Forms OSGi, l’option Tâches est masquée. La boîte d’envoi stocke les formulaires enregistrés et les brouillons avant sa synchronisation avec le serveur. Tous les formulaires et les brouillons enregistrés dans la boîte d’envoi sont chargés sur le serveur AEM Forms lorsque l’application est [synchronisée avec le serveur](/help/forms/using/sync-app.md). Pour plus d’informations sur les paramètres, voir [Mise à jour des paramètres généraux](/help/forms/using/update-general-settings.md).
1. **Tâche ou formulaire** : Appuyez sur la tâche ou le formulaire répertorier afin de pouvoir travailler dessus.
1. **Points de suspension horizontaux** : Indique si les actions sont disponibles pour le formulaire. Tapez sur les points de suspension pour afficher les actions et la description fournie par l’auteur. Les options **Supprimer le brouillon** et **Terminé** sont visibles lorsque vous appuyez sur les points de suspension.
1. **Icône Synchronisation** : appuyez sur l’icône d’actualisation pour synchroniser votre application avec le serveur AEM Forms.

## Personnalisation de l’écran d’accueil {#customizing-the-home-screen}

![Paramètres généraux](assets/gen-settings.png)

Vous pouvez modifier l’écran d’accueil par défaut de l’application, soit à partir de l’onglet **[Paramètres généraux](/help/forms/using/update-general-settings.md)** de l’application, soit à partir de l’onglet **Préférences** dans Workspace HTML.

Toute modification apportée au paramètre d’écran d’accueil de l’application s’applique à l’écran d’accueil de l’utilisateur connecté ou travaillant sur le périphérique mobile en cours.

Toutefois, la modification apportée à Workspace HTML s’applique à l’ensemble des utilisateurs de l’application AEM Forms connectés au serveur AEM Forms.
