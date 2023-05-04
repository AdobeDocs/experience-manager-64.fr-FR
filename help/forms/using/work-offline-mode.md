---
title: Utiliser en mode hors ligne
seo-title: Working in the offline mode
description: Mettez votre appareil mobile hors ligne en dehors de votre plage de réseau AEM Forms ou en mode hors ligne complet et travaillez sur l’application AEM Forms
seo-description: Take your mobile device offline outside your AEM Forms network range or in a completely offline mode and work on the AEM Forms app
uuid: b900a0f8-90ce-486a-bde6-6cdf11bd2801
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 9a3c6ab4-8bb9-40c7-8c56-59153b364887
exl-id: 14303b8f-40a7-4bc5-8282-7526e0319264
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 55%

---

# Utiliser en mode hors ligne {#working-in-the-offline-mode}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le mode hors ligne de l’application d’AEM Forms permet de travailler en toute facilité, même lorsque l’application se déconnecte. Vous pouvez ouvrir, mettre à jour et même envoyer un formulaire sans avoir besoin d’une connexion réseau.

Commencez à travailler dans l’application AEM Forms en la synchronisant avec le serveur AEM Forms. Tous les formulaires qui vous sont assignés sont téléchargés dans votre application. Pour AEM Forms on JEE, les tâches sont récupérées dans l’onglet Tâches et les formulaires associés aux points de départ et autres formulaires dans l’onglet Forms. Pour AEM Forms sur OSGi, seul Forms est chargé dans l’onglet Forms.

Pour plus d’informations sur la synchronisation de l’application, voir [Synchronisation de l’application](/help/forms/using/sync-app.md).

## Mise à disposition de Forms hors ligne {#making-forms-available-offline}

Lorsque vous synchronisez votre application avec le serveur AEM Forms, les formulaires sont téléchargés sur votre périphérique mobile. Cependant, par défaut, les pièces jointes associées avec le formulaire ne sont pas téléchargées. Cela signifie que si vous êtes en ligne, vous pouvez afficher les pièces jointes. Toutefois, pour vous assurer que vous pouvez afficher la pièce jointe en mode hors ligne, modifiez les paramètres par défaut de votre application.

Pour vous assurer que les pièces jointes associées sont téléchargées avec chaque formulaire, activez l’option de récupération des pièces jointes. Pour plus d’informations, voir [Mise à jour des paramètres généraux](/help/forms/using/update-general-settings.md).

Le téléchargement de données sur le périphérique mobile pouvant affecter ses performances, l’option de récupération des pièces jointes est désactivée par défaut. Les pièces jointes sont récupérées sur le périphérique pour toutes les tâches téléchargées à partir du serveur après le réglage de ce paramètre sur ON (Activé). En mode hors ligne, un utilisateur peut ensuite travailler sur toutes les tâches téléchargées sur l’équipement après avoir activé l’option de **Récupération des pièces jointes**.

## Configuration du service hors ligne pour l’application AEM Forms {#configuring-offline-service-for-aem-forms-app-br}

Le service hors ligne de l’application AEM Forms identifie les ressources utilisées dans un formulaire. L’application AEM Forms repose sur ce service pour obtenir des informations sur les dépendances des formulaires. Des informations sur les dépendances de formulaire sont requises pour activer les fonctionnalités hors ligne. Le service hors ligne de l’application AEM Forms met en cache les chemins ou les URL des ressources utilisées dans un formulaire. Le cache est mis à jour en fonction des modifications apportées au formulaire et de la période de validité configurée pour le service hors ligne. La mise en cache des chemins ou des URL des ressources utilisées dans un formulaire améliore les performances côté serveur.

Pour configurer le composant hors ligne côté serveur de l’application AEM Forms :

1. Dans l’instance de création, accédez à **Adobe Experience Manager** > **Outils** > **Formulaires** > **Configurer le service hors ligne de l’application Forms**.

   URL : `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Sous Paramètres généraux, vous pouvez effectuer les opérations suivantes :

   * **Effacer le cache**: Efface le cache côté serveur des dépendances de formulaire.
   * **Réinitialiser la configuration** : réinitialise la configuration hors ligne de l’application AEM Forms.
   * **Validité du cache**: Indique la période de validité du cache hors ligne côté serveur.
   * **Chemins d’observation des ressources**: Indique les chemins d’accès où le service hors ligne surveille les modifications des ressources. Si des modifications se produisent dans les chemins d’accès spécifiés, le cache hors ligne de tous les formulaires dépendants est mis à jour. Par exemple, `/etc/clientlibs/fd,/content/dam/images`.

1. Dans le **Cache de ressource manuel** , spécifiez les dépendances de formulaire que le service hors ligne ne peut pas identifier. Vous pouvez spécifier des ressources telles que des images chargées à partir de JavaScript. L’application AEM Forms téléchargera également ces ressources pour le mode hors ligne.
