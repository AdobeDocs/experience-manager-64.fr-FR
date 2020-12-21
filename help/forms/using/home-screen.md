---
title: Écran d’accueil
seo-title: Écran d’accueil
description: Description des composants de l’écran d’accueil de l’application AEM Forms.
seo-description: Description des composants de l’écran d’accueil de l’application AEM Forms
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
translation-type: tm+mt
source-git-commit: 79dcf6816e1156604c0c9279b727ea436ad1826a
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 83%

---


# Ecran d’accueil  {#home-screen}

Lorsque vous vous connectez à l’application AEM Forms, vous êtes redirigé vers l’écran d’accueil.

## Écran d’accueil par défaut  {#default-home-screen}

Par défaut, l’écran d’accueil affiche tous les formulaires, y compris les points de départ et les tâches (si le serveur connecté est activé pour le flux de travail d’AEM forms), avec les vignettes associées. Vous pouvez spécifier les vignettes dans le serveur AEM Forms.

La figure suivante est annotée avec les légendes des principaux composants de l’écran d’accueil.
![Forms app home ](assets/home-screen-1.png)
[screenCliquez pour agrandir](assets/home-screen-1-1.png)

1. **Bouton** Menu : Appuyez sur le  **** bouton Menubutton pour accéder aux Tâches, Forms, Outbox et Settings (Paramètres). Si votre application AEM Forms est connectée à un serveur AEM Forms JEE, vous pouvez voir l’option Tâches. L’option de tâches stocke également les brouillons créés à partir des tâches dans un processus. Pour les serveurs AEM Forms OSGi, l’option Tâches est masquée. La boîte d’envoi stocke les formulaires enregistrés et les brouillons avant sa synchronisation avec le serveur. Tous les formulaires et brouillons enregistrés dans la boîte d’envoi sont téléchargés vers le serveur AEM Forms lorsque l’application est [synchronisée avec le serveur](/help/forms/using/sync-app.md). Pour plus d’informations sur les paramètres, voir [Mise à jour des paramètres généraux](/help/forms/using/update-general-settings.md).
1. **Tâche ou formulaire** : Appuyez sur la tâche ou le formulaire répertorier afin de pouvoir travailler dessus.
1. **Points de suspension horizontaux** : Indique si les actions sont disponibles pour le formulaire. Tapez sur les points de suspension pour afficher les actions et la description fournie par l’auteur. L&#39;option **Supprimer le brouillon** et **Terminer** est visible lorsque vous appuyez sur les points de suspension.
1. **Icône Synchronisation** : appuyez sur l’icône d’actualisation pour synchroniser votre application avec le serveur AEM Forms.

## Personnalisation de l’écran d’accueil  {#customizing-the-home-screen}

![Paramètres généraux](assets/gen-settings.png)

Vous pouvez modifier l’écran d’accueil par défaut de l’application, soit à partir de l’onglet **[Paramètres généraux](/help/forms/using/update-general-settings.md)** de l’application, soit à partir de l’onglet **Préférences** dans Workspace HTML.

Toute modification apportée au paramètre d’écran d’accueil de l’application s’applique à l’écran d’accueil de l’utilisateur connecté ou travaillant sur le périphérique mobile en cours.

Toutefois, la modification apportée à Workspace HTML s’applique à l’ensemble des utilisateurs de l’application AEM Forms connectés au serveur AEM Forms.

