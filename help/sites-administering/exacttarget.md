---
title: Intégration à ExactTarget
seo-title: Integrating with ExactTarget
description: Découvrez comment intégrer AEM à ExactTarget.
seo-description: Learn how to integrate AEM with ExactTarget.
uuid: dafa0a1a-2d1e-40fc-a729-f2ce7ebc7807
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: d1cff2bb-9fdf-49cb-a695-d437bba5653d
exl-id: 943e5199-271f-4015-a9f7-4d39c00deabe
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 77%

---

# Intégration à ExactTarget{#integrating-with-exacttarget}

L’intégration d’AEM à ExactTarget vous permet de gérer et d’envoyer des emails créés dans AEM via ExactTarget. Il vous permet également d’utiliser les fonctionnalités de gestion des prospects d’ExactTarget via AEM forms sur les pages AEM.

L’intégration offre les fonctionnalités suivantes :

* Possibilité de créer des courriers électroniques dans AEM et de les publier dans ExactTarget pour les diffuser
* Possibilité de définir une action d’un formulaire AEM afin de créer un abonné ExactTarget

Une fois ExactTarget configuré, vous pouvez publier des newsletters ou des courriers électroniques dans ExactTarget. Voir [Publication de newsletters dans un service de messagerie](/help/sites-authoring/personalization.md).

## Création d’une configuration ExactTarget {#creating-an-exacttarget-configuration}

Il est possible d’ajouter des configurations ExactTarget par le biais d’outils ou de services cloud. Les deux méthodes sont décrites dans cette section.

### Configuration d’ExactTarget à l’aide des services cloud {#configuring-exacttarget-via-cloudservices}

Pour créer une configuration ExactTarget dans les services cloud :

1. Sur la page d’accueil, cliquez sur **Services cloud**. (Ou accéder directement à `https://<hostname>:<port>/etc/cloudservices.html`.)
1. Cliquez sur **ExactTarget** puis **Configurer**. La fenêtre de configuration d’ExactTarget s’affiche.

   ![chlimage_1-182](assets/chlimage_1-182.png)

1. Ajoutez un titre et, éventuellement, un nom, puis cliquez sur **Créer**. La fenêtre de configuration ** Paramètres ExactTarget** s’affiche.

   ![chlimage_1-31](assets/chlimage_1-31.jpeg)

1. Entrez le nom d’utilisateur, un mot de passe et sélectionnez un point de terminaison d’API (par exemple, **https://webservice.exacttarget.com/Service.asmx**).
1. Cliquez sur **Connexion à ExactTarget.** Une boîte de dialogue s’affiche pour confirmer que vous êtes bien connecté. Cliquez sur **OK** pour fermer la fenêtre.

   ![chlimage_1-32](assets/chlimage_1-32.jpeg)

1. Sélectionnez un compte, le cas échéant. Le compte est destiné aux clients Enterprise 2.0. Cliquez sur **OK**.

   ExactTarget a été configuré. Si vous souhaitez modifier la configuration, cliquez sur **Modifier**. Vous pouvez accéder à ExactTarget en cliquant sur **Accès à ExactTarget**.

1. AEM propose désormais la fonctionnalité Extension de données. Celle-ci permet d’importer des colonnes d’extensions de données ExactTarget. Pour la configurer, cliquez sur le signe « + » en regard de la configuration ExactTarget créée. Vous pouvez sélectionner l’une des extensions de données existantes dans la liste déroulante. Pour plus d’informations sur la configuration des extensions de données, voir la [documentation ExactTarget](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships).

   Vous pouvez ensuite utiliser les colonnes d’extensions de données importées dans le composant **Texte et personnalisation**.

   ![chlimage_1-33](assets/chlimage_1-33.jpeg)

### Configuration d’ExactTarget à l’aide des outils {#configuring-exacttarget-via-tools}

Pour créer une configuration ExactTarget avec les outils, procédez comme suit :

1. Sur la page d’accueil, cliquez sur **Outils**. Ou accédez-y directement en accédant à `https://<hostname>:<port>/misadmin#/etc`.
1. Sélectionnez **, Outils**, **Configuration des services en cloud**, puis **ExactTarget**.
1. Cliquez sur **Nouveau** pour ouvrir la fenêtre **Créer une page **.

   ![chlimage_1-34](assets/chlimage_1-34.jpeg)

1. Saisissez le **titre** et éventuellement le **nom**, puis cliquez sur **Créer**.
1. Saisissez les informations de configuration conformément à l’étape 4 de la procédure précédente. Suivez cette procédure pour terminer la configuration d’ExactTarget.

### Ajout de plusieurs configurations {#adding-multiple-configurations}

Pour ajouter plusieurs configurations, procédez comme suit :

1. Sur la page d’accueil, cliquez sur **Services cloud** puis sur **ExactTarget**. Cliquez sur **Afficher les configurations** qui s’affiche si une ou plusieurs configurations ExactTarget sont disponibles. Toutes les configurations disponibles sont répertoriées.
1. Cliquez sur le lien **+** en regard de Configurations disponibles. Cette action ouvre la fenêtre **Créer une configuration**. Pour créer une autre configuration, suivez la procédure de configuration précédente.
