---
title: Intégration à Salesforce
seo-title: Integrating with Salesforce
description: Découvrez l’intégration d’AEM à Salesforce.
seo-description: Learn about integrating AEM with Salesforce.
uuid: db3b25f3-b680-4054-a8db-4161d4c86201
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b9752c60-eb26-4840-9163-a99537a58727
exl-id: 4c09699a-c7ae-48ee-9423-87ff35b1e9d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 56%

---

# Intégration à Salesforce{#integrating-with-salesforce}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’intégration de Salesforce à AEM fournit des fonctions de gestion de prospect et exploite les fonctions existantes que Salesforce met à disposition commercialement. Vous pouvez configurer AEM pour publier des prospects sur Salesforce et créer des composants qui accèdent directement aux données à partir de Salesforce.

L’intégration bidirectionnelle et extensible entre AEM et Salesforce permet :

* Les entreprises doivent utiliser et mettre à jour complètement les données pour améliorer l’expérience client.
* Engagement du marketing aux activités de vente.
* Les organisations doivent transmettre et recevoir automatiquement des données d’une banque de données Salesforce.

Ce document répond aux questions suivantes :

* Configuration des Cloud Services Salesforce (configuration d’AEM à intégrer à Salesforce).
* utilisation des informations de prospect/contact Salesforce dans ClientContext et pour la personnalisation.
* Comment utiliser le modèle de workflow Salesforce pour publier des utilisateurs AEM en tant que prospects pour Salesforce.
* Découvrez comment créer un composant qui affiche les données de Salesforce.

## Configuration d’AEM à intégrer à Salesforce {#configuring-aem-to-integrate-with-salesforce}

Pour configurer AEM de manière à l’intégrer à Salesforce, vous devez d’abord configurer une application d’accès à distance dans Salesforce. Ensuite, vous configurez le service cloud Salesforce pour qu’il pointe vers cette application d’accès à distance.

>[!NOTE]
>
>Vous pouvez créer un compte développeur gratuit dans Salesforce.

Pour configurer les AEM à intégrer à Salesforce, procédez comme suit :

1. Dans AEM, accédez à **Services cloud**. Dans Services tiers, cliquez sur **Configurer maintenant** dans **Salesforce**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Créez une configuration, par exemple : **développeur**.

   >[!NOTE]
   >
   >La nouvelle configuration redirige vers une nouvelle page : **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Il s’agit de la même valeur que celle que vous devez spécifier dans l’URL de rappel lors de la création de l’application d’accès à distance dans Salesforce. Ces valeurs doivent correspondre.

1. Connectez-vous à votre compte Salesforce (ou si vous n’en avez pas, créez-en un, à l’adresse [https://developer.force.com](https://developer.force.com)).
1. Dans Salesforce, sélectionnez **Créer** > **Applications** pour accéder à **Applications connectées** (dans les anciennes versions de Salesforce, le workflow est **Déployer** > **Accès à distance**).
1. Cliquez sur **Nouveau** pour connecter AEM à Salesforce.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Saisissez le **nom de l’application connectée**, le **nom de l’API** et l’**adresse électronique de contact**. Cochez la case **Activer les paramètres OAuth**, saisissez l’**adresse URL de rappel** et ajoutez une portée OAuth (accès intégral, par exemple). L’adresse URL de rappel se présente comme suit : `http://localhost:4502/etc/cloudservices/salesforce/developer.html`.

   Modifiez le nom et le numéro de port du serveur et le nom de la page correspondant à votre configuration.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. Cliquez sur **Enregistrer** pour enregistrer la configuration Salesforce. Salesforce crée une **clé du client** et un **secret du client**, dont vous avez besoin pour la configuration d’AEM.

   ![chlimage_1-87](assets/chlimage_1-87.png)

   >[!NOTE]
   >
   >Vous devrez peut-être attendre plusieurs minutes (jusqu’à 15 minutes) pour que l’application d’accès à distance dans Salesforce soit activée.

1. Dans AEM, accédez à **Services cloud** et à la configuration de Salesforce que vous avez créée précédemment (par exemple, **développeur**). Cliquez sur **Modifier** et saisissez la clé du client et le secret client à partir de salesforce.com.

   ![chlimage_1-23](assets/chlimage_1-23.jpeg)

   | URL de connexion | Il s’agit du point d’entrée d’autorisation Salesforce. Sa valeur est prérenseignée et convient dans la plupart des cas. |
   |---|---|
   | Clé du client | Saisissez la valeur obtenue à partir de la page Enregistrement de l’application d’accès à distance dans salesforce.com. |
   | Secret du client | Saisissez la valeur obtenue à partir de la page Enregistrement de l’application d’accès à distance dans salesforce.com. |

1. Cliquez sur **Connexion à Salesforce** pour vous connecter. Salesforce vous demande d’autoriser votre configuration à vous connecter à Salesforce.

   ![chlimage_1-88](assets/chlimage_1-88.png)

   Dans AEM, une boîte de dialogue de confirmation s’affiche pour confirmer que vous êtes bien connecté.

1. Accédez à la page principale de votre site web et cliquez sur **Propriétés de la page**. Ensuite, sélectionnez **Services cloud**, ajoutez **Salesforce** et sélectionnez la configuration appropriée (par exemple, **développeur**).

   ![chlimage_1-89](assets/chlimage_1-89.png)

   Vous pouvez maintenant utiliser le modèle de workflow pour publier des prospects sur Salesforce et créer des composants qui accèdent aux données de Salesforce.

## Exportation des utilisateurs AEM en tant que prospects Salesforce {#exporting-aem-users-as-salesforce-leads}

Si vous souhaitez exporter un utilisateur AEM en tant que prospect Salesforce, vous devez configurer le workflow pour publier des prospects dans Salesforce.

Pour exporter AEM utilisateurs en tant que prospects Salesforce, procédez comme suit :

1. Accédez au workflow Salesforce à l’adresse `http://localhost:4502/workflow` en cliquant avec le bouton droit sur le workflow **Exportation de Salesforce.com** et en cliquant sur **Démarrer**.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Sélectionnez l’utilisateur AEM à créer en tant que prospect de type **Contenu** pour ce processus (accueil –> utilisateurs). Veillez à sélectionner le noeud de profil de l’utilisateur, car il contient des informations telles que **givenName**, **familyName**, etc., qui sont mappés aux pistes Salesforce **FirstName** et **LastName** champs.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >Avant de lancer ce workflow, le nœud de prospect dans AEM doit comporter certains champs obligatoires avant d’être publié dans Salesforce. Ces champs sont **Prénom**, **Nom de famille**, **Entreprise** et **Adresse électronique**. Pour afficher la liste complète des correspondances entre un utilisateur AEM et un prospect Salesforce, consultez la section [Configuration du mappage entre un utilisateur AEM et un prospect Salesforce](#mapping-configuration-between-aem-user-and-salesforce-lead).

1. Cliquez sur **OK**. Les informations de l’utilisateur sont exportées vers salesforce.com. Vous pouvez le vérifier sur salesforce.com.

   >[!NOTE]
   >
   >Les journaux d’erreurs indiquent si un prospect est importé. Pour plus d’informations, consultez le journal des erreurs.

### Configuration du workflow d’exportation Salesforce.com {#configuring-the-salesforce-com-export-workflow}

Vous devrez peut-être configurer le workflow d’exportation Salesforce.com pour qu’il corresponde à la configuration Salesforce.com correcte ou pour apporter d’autres modifications.

Pour configurer le workflow d’exportation Salesforce.com :

1. Accédez à `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`.

   ![chlimage_1-24](assets/chlimage_1-24.jpeg)

1. Ouvrez l’étape d’exportation de salesforce.com, sélectionnez l’onglet **Arguments**, sélectionnez la configuration appropriée et cliquez sur **OK**. De plus, si vous souhaitez que le workflow recrée un prospect supprimé dans Salesforce, cochez cette case.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

   ![chlimage_1-93](assets/chlimage_1-93.png)

### Configuration du mappage entre un utilisateur AEM et un prospect Salesforce {#mapping-configuration-between-aem-user-and-salesforce-lead}

Pour afficher ou modifier la configuration des correspondances actuelle entre un utilisateur AEM et un prospect Salesforce, ouvrez le gestionnaire de configuration :`https://<hostname>:<port>/system/console/configMgr` et cherchez **Configuration des correspondances d’un prospect Salesforce**.

1. Ouvrez le gestionnaire de configuration en cliquant sur **Console web** ou en accédant directement à `https://<hostname>:<port>/system/console/configMgr.`.
1. Cherchez **Configuration du mappage d’un prospect Salesforce**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Modifiez les correspondances, au besoin. Le mappage par défaut suit le modèle** aemUserAttribute=sfLeadAttribute**. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

## Configuration du magasin de contexte client Salesforce {#configuring-salesforce-client-context-store}

L’entrepôt de contexte client Salesforce affiche des informations sur l’utilisateur actuellement connecté, qui complètent les informations déjà disponibles dans AEM. Il extrait ces informations supplémentaires de Salesforce en fonction de la connexion de l’utilisateur à Salesforce.

Pour cela, vous devez configurer les éléments suivants :

1. Associez un utilisateur AEM à un identifiant Salesforce via le composant Salesforce Connect.
1. Ajoutez les données de profil Salesforce dans la page contextuelle du client pour configurer les propriétés que vous souhaitez afficher.
1. (Facultatif) Créez un segment qui utilise les données de l’entrepôt de contexte client Salesforce.

### Liaison d’un utilisateur AEM à un identifiant Salesforce {#linking-an-aem-user-with-a-salesforce-id}

Vous devez associer un utilisateur AEM à un ID Salesforce afin de le charger dans le contexte client. Dans un scénario réel, vous effectueriez la liaison en fonction des données connues de l’utilisateur avec la validation. À des fins de démonstration, dans cette procédure, vous utilisez la méthode **Salesforce Connect** composant.

1. Accédez à un site web dans AEM, connectez-vous, puis faites glisser et déposez le **Salesforce Connect** du sidekick.

   >[!NOTE]
   >
   >Si la variable **Salesforce Connect** n’est pas disponible, accédez à **Conception** afficher et sélectionner le contenu pour le rendre disponible dans **Modifier** vue.

   ![chlimage_1-25](assets/chlimage_1-25.jpeg)

   Lorsque vous faites glisser le composant vers la page, il affiche **Lien vers Salesforce=Désactivé**.

   ![chlimage_1-95](assets/chlimage_1-95.png)

   >[!NOTE]
   >
   >Ce composant n’est fourni qu’à titre de démonstration. Dans le cas de scénarios réels, il existe un autre processus pour lier/associer les utilisateurs à des pistes.

1. Après avoir fait glisser le composant dans la page, ouvrez-le pour le configurer. Sélectionnez la configuration, le type de contact et le prospect ou le contact Salesforce, puis cliquez sur **OK**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   AEM lie l’utilisateur au contact ou au prospect Salesforce.

   ![chlimage_1-97](assets/chlimage_1-97.png)

### Ajout de données Salesforce à ClientContext {#adding-salesforce-data-to-client-context}

Vous pouvez charger des données utilisateur à partir de Salesforce dans ClientContext à utiliser pour la personnalisation :

1. Ouvrez le contexte client à étendre en accédant à cet emplacement, par exemple, `http://localhost:4502/etc/clientcontext/default/content.html.`.

   ![chlimage_1-26](assets/chlimage_1-26.jpeg)

1. Faites glisser le composant **Données du profil Salesforce** vers le contexte du client.

   ![chlimage_1-27](assets/chlimage_1-27.jpeg)

1. Double-cliquez sur le composant pour l’ouvrir. Sélectionnez **Ajouter un élément** et sélectionnez une propriété dans la liste déroulante. Ajoutez autant de propriétés que vous le souhaitez et sélectionnez **OK**.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. À présent, les propriétés spécifiques à Salesforce s’affichent dans le contexte client.

   ![chlimage_1-99](assets/chlimage_1-99.png)

### Création d’un segment à l’aide des données du magasin de contexte client Salesforce {#building-a-segment-using-data-from-salesforce-client-context-store}

Vous pouvez créer un segment qui utilise les données de l’entrepôt de contexte client Salesforce. Pour ce faire :

1. Accédez à la segmentation dans AEM en sélectionnant **Outils** > **Segmentation** ou en consultant [http://localhost:4502/miscadmin#/etc/segmentation](http://localhost:4502/miscadmin#/etc/segmentation).
1. Créez ou mettez à jour un segment pour inclure des données de Salesforce. Pour plus d’informations, voir [Segmentation](/help/sites-administering/campaign-segmentation.md).

## Recherche de pistes {#searching-leads}

AEM est fourni avec un exemple de composant Recherche, qui cherche des prospects dans Salesforce en fonction des critères déterminés. Ce composant montre comment utiliser l’API REST Salesforce pour rechercher des objets Salesforce. Vous devez lier une page à une configuration Salesforce pour déclencher un appel à salesforce.com.

>[!NOTE]
>
>Voici un exemple de composant, qui montre comment utiliser l’API REST Salesforce pour créer une requête portant sur des objets Salesforce. Utilisez-le comme exemple pour créer des composants plus complexes en fonction de vos besoins.

Pour utiliser ce composant :

1. Accédez à la page dans laquelle vous souhaitez utiliser cette configuration. Ouvrez les propriétés de page et sélectionnez **Cloud Services.** Cliquez sur **Ajout de services** et sélectionnez **Salesforce** et la configuration appropriée, puis cliquez sur **OK**.

   ![chlimage_1-28](assets/chlimage_1-28.jpeg)

1. Faites glisser le composant Recherche de Salesforce vers la page (sous réserver qu’elle a été activée. Pour l’activer, accédez au mode Conception et ajoutez-le à la zone appropriée).

   ![chlimage_1-29](assets/chlimage_1-29.jpeg)

1. Ouvrez le composant Recherche, spécifiez les paramètres de recherche et cliquez sur **OK**.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. AEM affiche les prospects spécifiés dans votre composant Recherche correspondant aux critères spécifiés.

   ![chlimage_1-101](assets/chlimage_1-101.png)
