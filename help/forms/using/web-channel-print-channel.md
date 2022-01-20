---
title: Canal d’impression et canal web
seo-title: Print channel and web channel
description: Importation de modèles de canaux d’impression et création et activation de modèles de canaux web
seo-description: Importing print channel templates and creating and enabling web channel templates
uuid: 19e6ffab-00d2-4084-9ee7-9643b11eb6c6
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 71bba66a-3cac-445b-9941-aa4bcf9b2160
feature: Interactive Communication
exl-id: cb7a8e96-4440-47ec-b506-275d5acc774e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 65%

---

# Canal d’impression et canal web {#print-channel-and-web-channel}

Importation de modèles de canaux d’impression et création et activation de modèles de canaux web

Les communications interactives peuvent être fournies par deux canaux : impression et web. Le canal d’impression est utilisé pour créer des documents PDF et des communications papier, comme une lettre imprimée comme rappel pour le paiement de primes d’assurance, tandis que le canal web est utilisé pour fournir des expériences en ligne, comme un relevé de carte de crédit sur un site Web.

Les auteurs de communication interactive peuvent réutiliser des ressources telles que des fragments de document et des images pour créer des versions d’impression et des versions web de la communication interactive.

L’une des conditions préalables pour [Création d’une communication interactive](/help/forms/using/create-interactive-communication.md) doit disposer des modèles pour l’impression et/ou le canal web disponible sur le serveur. Alors que les auteurs de modèles créent le modèle de canal web dans AEM, le modèle de canal d’impression XDP est créé dans Adobe Forms Designer et téléchargé sur le serveur.

## Canal d’impression {#printchannel}

Le canal d’impression d’une communication interactive utilise le modèle de formulaire XFA, XDP. Les XDP sont conçus dans Adobe Forms Designer. Pour plus d’informations sur la création de modèles de canal d’impression, voir [Conception de la mise en page](/help/forms/using/layout-design-details.md). Pour utiliser un modèle de canal d’impression dans votre communication interactive, vous devez télécharger le modèle sur le serveur AEM Forms.

### Télécharger le modèle de canal d’impression Communication interactive {#upload-interactive-communication-print-channel-template}

Pour télécharger le modèle, vous devez être membre du groupe forms-user. Suivez les étapes ci-dessous pour télécharger le modèle de canal d’impression (XDP) vers AEM Forms :

1. Sélectionnez **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

1. Appuyez sur **[!UICONTROL Créer]** > **[!UICONTROL Chargement de fichier]**.

   Naviguez et sélectionnez le modèle de canal d’impression approprié (XDP), puis appuyez sur **[!UICONTROL Ouvrir]**.

## Canal web {#web-channel}

Les auteurs de modèles et les administrateurs peuvent créer, modifier et activer des modèles web. Pour autoriser d’autres utilisateurs à créer des modèles web, vous devez leur accorder des droits. Pour plus d’informations, voir [Administration des utilisateurs, des groupes et des droits d’accès](/help/sites-administering/user-group-ac-admin.md).

### Création de modèle de canal web {#authoring-web-channel-template}

Pour créer un modèle de canal web, vous devez d’abord créer un dossier modèle. Une fois que vous avez créé un modèle web dans un dossier de modèles, vous devez activer ce modèle pour permettre aux utilisateurs de formulaires de créer le canal web d’une communication interactive basée sur le modèle.

Pour créer un modèle de canal web Effectuez les étapes suivantes :

1. Créez un dossier Modèle pour conserver vos modèles web de communication interactive, si vous n’en avez pas déjà un. Pour plus d’informations, voir Dossiers de modèles dans [Modèles de page - Modifiables](/help/sites-developing/page-templates-editable.md).

   1. Appuyer **[!UICONTROL Outils]** ![tools-1](assets/tools-1.png) > **[!UICONTROL Explorateur de configuration]**.
      * Pour plus d’informations, consultez la documentation relative au [](/help/sites-administering/configurations.md)Navigateur de configuration.
   1. Sur la page du navigateur de configuration, appuyez sur . **[!UICONTROL Créer]**.
   1. Dans la boîte de dialogue Créer une configuration, indiquez un titre pour le dossier, puis cochez la case **[!UICONTROL Modèles modifiables]**, puis appuyez sur **[!UICONTROL Créer]**.

      Le dossier est créé et répertorié dans la page du navigateur de configuration.

1. Accédez au dossier de modèle approprié et créez un modèle web.

   1. Accédez au dossier de modèle approprié en sélectionnant **[!UICONTROL Outils]** > **[!UICONTROL Modèles > Dossier]**.
   1. Appuyez sur **[!UICONTROL Créer]**.
   1. Sélectionner **[!UICONTROL Communication interactive - Canal web]** et appuyez sur **[!UICONTROL Suivant]**.
   1. Entrez un titre et une description de modèle, puis appuyez sur **[!UICONTROL Créer]**.

      Le modèle est créé et une boîte de dialogue s’affiche.

   1. Appuyez sur **[!UICONTROL Ouvrir]** pour ouvrir le modèle que vous avez créé dans l’éditeur de modèles.

      L’Éditeur de modèle s’affiche.

      ![webchanneltemplate](assets/webchanneltemplate.png)

      Lors de la création ou de la modification d’un modèle, un auteur de modèles peut définir différents aspects. La création ou la modification d’un modèle est similaire à la création de pages. Pour plus d’informations, voir Modification de modèles - Créateurs de modèles dans [Création de modèles de page](/help/sites-authoring/templates.md).

1. Pour permettre l’utilisation de ce modèle pour la création de communication interactive, activez le modèle.

   1. Appuyer **[!UICONTROL Outils]** ![tools-1](assets/tools-1.png) > **[!UICONTROL Modèles]**.
   1. Accédez au modèle approprié, sélectionnez-le, puis appuyez sur **[!UICONTROL Activer]** et dans le message d’alerte, appuyez sur **[!UICONTROL Activer]**.

      Le modèle est activé et son statut s’affiche comme Activé. Vous pouvez maintenant créer une communication interactive dans laquelle vous pouvez utiliser le modèle de canal web nouvellement créé.

### Canal d’impression en tant que base du canal web {#print-channel-as-master-for-web-channel}

Lors de la création d’une communication interactive, les auteurs peuvent sélectionner cette option pour créer le canal web en synchronisation avec le canal d’impression. L’utilisation du canal d’impression comme base pour le canal web garantit que le contenu, l’héritage et la liaison des données du canal web sont dérivés du canal d’impression et que les modifications apportées au canal d’impression peuvent être répercutées sur le canal web. Les auteurs de communication interactive sont toutefois autorisés à interrompre l’héritage pour des composants spécifiques dans le canal web, selon les besoins.

![printweb_2-2](assets/printweb_2-2.png)
