---
title: Synchronisation de l’application
seo-title: Synchronizing the app
description: Synchronisez l’application AEM Forms sur votre périphérique mobile avec le serveur AEM Forms.
seo-description: Synchronize the AEM Forms app on your mobile device with the AEM Forms server.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
exl-id: b5681fe5-69ba-4fc0-95e3-6ffdcdd95382
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 33%

---

# Synchronisation de l’application {#synchronizing-the-app}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Synchronisation de l’application {#synchronizing-the-app-1}

Les formulaires de votre application sont téléchargés à partir du serveur AEM Forms. Les formulaires sont téléchargés sous les onglets Tâches et Forms . Les brouillons créés à partir de formulaires sont téléchargés dans l’onglet Brouillons, et les brouillons créés à partir de tâches sont téléchargés dans l’onglet Tâches. Pour un formulaire autonome sur le serveur OSGi, les formulaires et les brouillons sont téléchargés respectivement dans les onglets Forms et Brouillons.

Lorsque vous remplissez et envoyez un formulaire, celui-ci est de nouveau téléchargé sur le serveur AEM Forms instantanément si l’application est en ligne. Les formulaires sont récupérés à partir du serveur lors de la synchronisation de l’application. Les brouillons, toutefois, sont synchronisés avec le serveur immédiatement lorsque l’application est en ligne.

Lorsque vous êtes connecté avec le serveur AEM Forms, votre application est synchronisée par défaut toutes les 15 minutes. Vous avez toutefois la possibilité de modifier la fréquence de synchronisation. Vous pouvez également synchroniser manuellement l’application à tout moment.

**Synchronisation manuelle de l’application**

Appuyez sur le bouton Synchroniser ![sync-app](assets/sync-app.png) dans le coin inférieur droit de l’écran d’accueil.

**Modification de la fréquence de synchronisation**

1. Pour accéder à l’écran des paramètres, appuyez sur le bouton de menu dans le coin supérieur gauche de l’écran d’accueil, puis appuyez sur **Paramètres**.
1. Dans l’écran Paramètres, appuyez sur l’onglet Général .

   ![Paramètre de fréquence de synchronisation dans la fenêtre Paramètres généraux](assets/gen-settings-1.png)

1. Sur l’option Fréquence de synchronisation , appuyez sur la valeur située à droite de la Fréquence de synchronisation.
1. Dans la liste déroulante, sélectionnez la nouvelle fréquence de synchronisation.

### Spécifications techniques {#technical-specifications}

* La logique principale d’envoi des données d’application hors ligne au serveur AEM Forms est incluse dans runtime/offline/util/offline.js.
* Dans le fichier .js, l’appel de la fonction processOfflineSubmittedSavedTasks(...) envoie vers le serveur les tâches enregistrées/envoyées. Il gère également les erreurs ou les conflits dans le processus de synchronisation. En cas d’échec de l’envoi de la tâche, la tâche est marquée comme en échec dans l’application. En outre, la tâche reste dans votre boîte d&#39;envoi.
* Les fonctions syncSubmittedTask() et syncSavedTask() effectuent des opérations sur des tâches individuelles.
* L’appel de la fonction processOfflineSubmittedSavedTasks() est lancé par le composant de liste de tâches après qu’un utilisateur a choisi de synchroniser l’état hors ligne sur le serveur ou une synchronisation automatique par le thread d’arrière-plan.
