---
title: Intégration à Salesforce
seo-title: Intégration à Salesforce
description: Découvrez l’intégration AEM à Salesforce.
seo-description: Découvrez l’intégration AEM à Salesforce.
uuid: db3b25f3-b680-4054-a8db-4161d4c86201
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b9752c60-eb26-4840-9163-a99537a58727
translation-type: tm+mt
source-git-commit: 7dc90299b7a0e5166c30702323f1678353fe39b3
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 82%

---


# Intégration à Salesforce{#integrating-with-salesforce}

L’intégration de Salesforce à AEM fournit des fonctions de gestion de prospect et exploite les fonctions existantes que Salesforce met à disposition commercialement. Vous pouvez configurer AEM de manière à publier des prospects dans Salesforce et à créer des composants qui accèdent directement aux données à partir de Salesforce.

Une intégration bidirectionnelle et évolutive entre AEM et Salesforce permet :

* aux organisations d’utiliser et de mettre à jour pleinement les données afin d’améliorer l’expérience client ;
* au marketing de s’engager dans les activités commerciales ;
* aux organisations de transmettre et de recevoir automatiquement des données d’un entrepôt de données Salesforce.

Ce document répond aux questions suivantes :

* Comment configurer des services Cloud Salesforce (configuration d’AEM pour l’intégrer à Salesforce) ?
* Comment utiliser les informations de prospect/contact Salesforce dans le contexte du client et pour la personnalisation ?
* Comment utiliser le modèle de workflow Salesforce pour publier des utilisateurs AEM en tant que prospects dans Salesforce ?
* Comment créer un composant qui affiche les données de Salesforce ?

## Configuration d’AEM de manière à l’intégrer à Salesforce {#configuring-aem-to-integrate-with-salesforce}

Pour configurer AEM de manière à l’intégrer à Salesforce, vous devez d’abord configurer une application d’accès à distance dans Salesforce. Ensuite, vous configurez le service de cloud Salesforce pour qu’il pointe vers cette application d’accès à distance.

>[!NOTE]
>
>Vous pouvez créer un compte de développeur dans Salesforce.

Pour configurer AEM de manière à l’intégrer à Salesforce :

1. In AEM, navigate to **Cloud Services**. Dans Services tiers, cliquez sur **Configurer maintenant** dans **Salesforce**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Créez une configuration, par exemple, **développeur**.

   >[!NOTE]
   >
   >La nouvelle configuration redirige vers une nouvelle page : **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Il s’agit exactement de la valeur que vous devez spécifier dans l’adresse URL de rappel lors de la création de l’application d’accès à distance dans Salesforce. Ces valeurs doivent correspondre.

1. Log in to your salesforce account (or if you do not have one, create one at [https://developer.force.com](https://developer.force.com).)
1. In Salesforce, navigate to **Create** > **Apps** to get to **Connected Apps** (in former versions of salesforce, the workflow was **Deploy** > **Remote Access**).
1. Click **New** to connect AEM with Salesforce.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Saisissez le **nom de l’application connectée**, le **nom de l’API** et l’**adresse électronique de contact**. Cochez la case **Activer les paramètres OAuth**, saisissez l’**adresse URL de rappel** et ajoutez une portée OAuth (accès intégral, par exemple). The callback URL looks similar to this: `http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   Modifiez le nom/numéro de port du serveur et le nom de la page correspondant à votre configuration.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. Cliquez sur **Enregistrer** pour enregistrer la configuration Salesforce. Salesforce crée une **clé du client** et un **secret du consommateur**, dont vous avez besoin pour la configuration d’AEM.

   ![chlimage_1-87](assets/chlimage_1-87.png)

   >[!NOTE]
   >
   >Vous devrez peut-être patienter quelques minutes (jusqu’à 15 minutes) que l’application d’accès à distance soit activée dans Salesforce.

1. Dans AEM, accédez à **Services cloud** et à la configuration de Salesforce que vous avez créée précédemment (par exemple, **développeur**). Cliquez sur **Modifier**, puis saisissez la clé du client et le secret du client salesforce.com.

   ![chlimage_1-23](assets/chlimage_1-23.jpeg)

   | URL de connexion | Il s&#39;agit du point de terminaison de l&#39;autorisation Salesforce. Sa valeur est prérenseignée et convient dans la plupart des cas. |
   |---|---|
   | Clé client | Saisissez la valeur obtenue à partir de la page Enregistrement des demandes d&#39;accès à distance sur salesforce.com |
   | Secret client | Saisissez la valeur obtenue à partir de la page Enregistrement des demandes d&#39;accès à distance sur salesforce.com |

1. Cliquez sur **Connexion à Salesforce** pour vous connecter. Salesforce vous demande d’autoriser votre configuration à se connecter à Salesforce.

   ![chlimage_1-88](assets/chlimage_1-88.png)

   Dans AEM, une boîte de dialogue de confirmation s’affiche pour confirmer que vous êtes bien connecté.

1. Accédez à la page principale de votre site web et cliquez sur **Propriétés de la page**. Then select **Cloud Services** and add **Salesforce** and select the correct configuration (for example, **developer**).

   ![chlimage_1-89](assets/chlimage_1-89.png)

   Vous pouvez maintenant configurer le modèle de processus de manière à publier des prospects dans Salesforce et à créer des composants qui accèdent à des données à partir de Salesforce.

## Exportation des utilisateurs AEM en tant que prospects Salesforce {#exporting-aem-users-as-salesforce-leads}

Si vous souhaitez exporter un utilisateur AEM en tant que prospect Salesforce, vous devez configurer le processus de manière à publier des prospects dans Salesforce.

Pour exporter des utilisateurs AEM en tant que prospects Salesforce :

1. Navigate to the Salesforce workflow at `http://localhost:4502/workflow` by right-clicking the workflow **Salesforce.com Export** and clicking **Start**.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Sélectionnez l’utilisateur AEM à créer en tant que prospect de type **Contenu** pour ce processus (accueil –> utilisateurs). Veillez à sélectionner le nœud de profil de l’utilisateur, car il contient des informations, comme **givenName**, **familyName**, etc., qui sont mises en correspondance avec les champs **Prénom** et **Nom de famille** des prospects Salesforce.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >Avant de commencer ce processus, le nœud de prospect dans AEM doit comporter certains champs obligatoires avant d’être publié dans Salesforce. These are **givenName**, **familyName**, **company** and **email**. To see a complete list of mapping between AEM user and Salesforce lead, see [Mapping Configuration between AEM user and Slaesforce lead.](#mapping-configuration-between-aem-user-and-salesforce-lead)

1. Cliquez sur **OK**. Les informations de l’utilisateur sont exportées vers salesforce.com. Vous pouvez le vérifier sur salesforce.com.

   >[!NOTE]
   >
   >Les journaux d’erreurs indiquent si un prospect est importé. Pour plus d’informations, consultez le journal d’erreurs.

### Configuration du processus d’exportation salesforce.com {#configuring-the-salesforce-com-export-workflow}

Vous devrez peut-être configurer le processus d’exportation salesforce.com pour le faire correspondre à la configuration salesforce.com appropriée ou apporter d’autres modifications.

Pour configurer le processus d’exportation Salesforce.com :

1. Accédez à `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`.

   ![chlimage_1-24](assets/chlimage_1-24.jpeg)

1. Open the Salesforce.com Export step, select the **Arguments** tab, and select the correct configuration is selected and click **OK**. De plus, si vous souhaitez que le processus recrée un prospect supprimé dans Salesforce, cochez la case.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

   ![chlimage_1-93](assets/chlimage_1-93.png)

### Configuration des correspondances entre un utilisateur AEM et un prospect Salesforce {#mapping-configuration-between-aem-user-and-salesforce-lead}

To view or edit the current mapping configuration between an AEM user and a Salesforce lead, open the Configuration Manager: `https://<hostname>:<port>/system/console/configMgr` and search for **Salesforce Lead Mapping Configuration**.

1. Ouvrez Configuration Manager en cliquant sur Console **** Web ou en accédant directement à `https://<hostname>:<port>/system/console/configMgr.`
1. Search for **Salesforce Lead Mapping Configuration**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Modifiez les correspondances, au besoin. Le mappage par défaut suit le modèle** aemUserAttribute=sfLeadAttribute**. Cliquez sur **Enregistrer** pour enregistrer les modifications.

## Configuration de l’entrepôt de contexte client Salesforce {#configuring-salesforce-client-context-store}

L’entrepôt de contexte client Salesforce affiche des informations sur l’utilisateur actuellement connecté, qui complètent les informations déjà disponibles dans AEM. Il extrait ces informations supplémentaires de Salesforce en fonction de la connexion de l’utilisateur à Salesforce.

À cet effet, vous devez configurer ce qui suit :

1. Liez un utilisateur AEM à un ID de Salesforce par le biais du composant Salesforce Connect.
1. Ajoutez les données de profil Salesforce dans la page de contexte client pour configurer les propriétés à afficher.
1. (Facultatif) Créez un segment qui utilise les données de l’entrepôt de contexte client Salesforce.

### Liaison d’un utilisateur AEM à un ID Salesforce {#linking-an-aem-user-with-a-salesforce-id}

Vous devez associer un utilisateur AEM à un ID Salesforce afin de le charger dans le contexte client. Dans un scénario réel, vous effectueriez la liaison en fonction des données connues de l’utilisateur avec la validation. À des fins de démonstration, dans cette procédure, vous utilisez le composant **Salesforce Connect**.

1. Accédez à un site web dans AEM, connectez-vous, faites glisser et déposez le composant **Salesforce du Connect** à partir du Sidekick.

   >[!NOTE]
   >
   >Si le composant **Salesforce Connect** n’est pas disponible, accédez au mode **Conception** et sélectionnez-le pour le mettre à disposition en mode **Modification**.

   ![chlimage_1-25](assets/chlimage_1-25.jpeg)

   Lorsque vous faites glisser le composant vers la page, il affiche **Lien vers Salesforce=Désactivé**.

   ![chlimage_1-95](assets/chlimage_1-95.png)

   >[!NOTE]
   >
   >Ce composant n’est fourni qu’à titre de démonstration. Pour les scénarios réels, le processus pour lier/associer des utilisateurs à des prospects est différent.

1. Après avoir fait glisser le composant dans la page, ouvrez-le pour le configurer. Sélectionnez la configuration, le type de contact et le prospect ou le contact Salesforce, puis cliquez sur **OK**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   AEM lie l’utilisateur au contact ou au prospect Salesforce.

   ![chlimage_1-97](assets/chlimage_1-97.png)

### Ajout de données Salesforce au contexte client {#adding-salesforce-data-to-client-context}

Vous pouvez charger des données utilisateur de Salesforce dans le contexte client à utiliser pour la personnalisation :

1. Open the client context you want to extend by navigating there, for example, `http://localhost:4502/etc/clientcontext/default/content.html.`

   ![chlimage_1-26](assets/chlimage_1-26.jpeg)

1. Faites glisser le composant **Données du profil Salesforce** vers le contexte du client.

   ![chlimage_1-27](assets/chlimage_1-27.jpeg)

1. Double-cliquez sur le composant pour l’ouvrir. Sélectionnez **Ajouter un élément** et sélectionnez une propriété dans la liste déroulante. Ajoutez autant de propriétés que vous le souhaitez et sélectionnez **OK**.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. À présent, les propriétés spécifiques à Salesforce s’affichent dans le contexte client.

   ![chlimage_1-99](assets/chlimage_1-99.png)

### Création d’un segment à l’aide de données de l’entrepôt de contexte client Salesforce {#building-a-segment-using-data-from-salesforce-client-context-store}

Vous pouvez créer un segment qui utilise les données de l’entrepôt de contexte client Salesforce. Pour ce faire :

1. Navigate to segmentation in AEM either by going to **Tools** > **Segmentation** or going to [http://localhost:4502/miscadmin#/etc/segmentation](http://localhost:4502/miscadmin#/etc/segmentation).
1. Créez ou mettez à jour un segment pour inclure des données de Salesforce. Pour plus d’informations, voir [Segmentation](/help/sites-administering/campaign-segmentation.md).

## Recherche de prospects {#searching-leads}

AEM est fourni avec un exemple de composant Recherche, qui cherche des prospects dans Salesforce en fonction des critères déterminés. Ce composant montre comment utiliser l’API REST Salesforce pour rechercher des objets Salesforce. Vous devez lier une page à une configuration Salesforce pour déclencher un appel de salesforce.com.

>[!NOTE]
>
>Voici un exemple de composant, qui montre comment utiliser l’API REST Salesforce pour créer une requête portant sur des objets Salesforce. Utilisez-le comme exemple pour créer des composants plus complexes en fonction de vos besoins.

Pour utiliser ce composant :

1. Accédez à la page dans laquelle vous souhaitez utiliser cette configuration. Ouvrez Propriétés de la page et sélectionnez **Services cloud.** Cliquez sur **Ajouter des services**, sélectionnez **Salesforce** et la configuration appropriée et cliquez sur **OK**.

   ![chlimage_1-28](assets/chlimage_1-28.jpeg)

1. Faites glisser le composant Recherche de Salesforce vers la page (sous réserver qu’elle a été activée. Pour l’activer, accédez au mode Conception et ajoutez-le à la zone appropriée).

   ![chlimage_1-29](assets/chlimage_1-29.jpeg)

1. Ouvrez le composant Recherche, spécifiez les paramètres de recherche et cliquez sur **OK**.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. AEM affiche les prospects spécifiés dans votre composant Recherche correspondant aux critères spécifiés.

   ![chlimage_1-101](assets/chlimage_1-101.png)

