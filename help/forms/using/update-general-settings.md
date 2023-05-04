---
title: Mettre à jour les paramètres généraux
seo-title: Updating general settings
description: Mettez à jour les paramètres de l’application AEM Forms tels que l’écran d’accueil et récupérez les options de points de départ et de pièces jointes.
seo-description: Update AEM Forms app settings such as the Home screen and fetch Startpoints and attachments options
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
exl-id: 5ca6212f-d3c7-4239-beba-9a0bdac4b1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 48%

---

# Mettre à jour les paramètres généraux {#updating-general-settings}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les paramètres généraux de l’application AEM Forms vous permettent de définir des paramètres tels que la récupération des pièces jointes, le mode hors ligne, l’écran d’entrée, la catégorie par défaut et la fréquence d’enregistrement automatique.

## Mise à jour des paramètres généraux de votre application {#working-with-the-form}

Lorsque vous synchronisez votre application avec le serveur AEM Forms, tous les formulaires et tâches définies sont téléchargés sur votre périphérique mobile.

La solution prête à l’emploi AEM Forms ne transfère pas les pièces jointes associées à chaque formulaire lorsque l’application est synchronisée.

Dans l’onglet Général, modifiez les pièces jointes de téléchargement, le mode hors connexion, l’écran d’entrée, les enregistrements automatiques et les paramètres de synchronisation. Vous pouvez modifier [l’écran d’accueil](/help/forms/using/home-screen.md) de l’application.

**Accédez à l’onglet Général de l’écran Paramètres .**

1. Pour accéder à l’écran des paramètres, appuyez sur le bouton Menu dans le coin supérieur gauche de l’écran d’accueil, puis appuyez sur **Paramètres**.
1. Dans l’écran Paramètres, appuyez sur l’onglet Général .

   ![Paramètres généraux de l’application AEM Forms](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >Les options peuvent s’afficher différemment sur différents appareils mobiles.

### Paramètres généraux {#general-settings}

Vous pouvez apporter les modifications suivantes aux paramètres de votre application.

* **Extraire les pièces jointes de la tâche** : spécifie le téléchargement ou non des pièces jointes associées lors du téléchargement d’une tâche sur votre application.

* **Mode hors ligne** : activer ou désactiver le service hors ligne de l’application AEM Forms. Voir [Utilisation en mode hors ligne](/help/forms/using/work-offline-mode.md) pour plus d’informations.

* **Écran d’accueil** : définir l’emplacement de départ ([écran d’accueil](/help/forms/using/home-screen.md)) de l’application.

    Options disponibles :

   * Formulaires
   * Tâches
   * Favoris

* **Catégorie par défaut**: Permet de sélectionner la catégorie de formulaires à afficher dans l’écran d’accueil. Lorsque vous sélectionnez Tous, vous pouvez voir tous les formulaires dans l’écran d’accueil. Les catégories sont renseignées en fonction des formulaires chargés dans l’application. Les formulaires sont disponibles dans l’application en fonction des paramètres spécifiés dans le serveur AEM Forms.

* **Fréquence d’enregistrement** : permet de définir la fréquence à laquelle [l’application mobile enregistre les données](/help/forms/using/autosave-data-app.md) en local.

* **Fréquence de synchronisation**: Pour définir la fréquence à laquelle votre [l’application mobile est synchronisée](/help/forms/using/sync-app.md) avec le serveur AEM Forms en mode en ligne.

**Effacer les données locales** : effacer la base de données, y compris les paramètres et données locales pour tous les utilisateurs et le stockage des fichiers du périphérique.

>[!NOTE]
>
>L’effacement du cache vous entraîne immédiatement hors de l’application.
>
>Toutefois, vous serez invité à confirmer l’opération d’effacement du cache.
