---
title: Configuration d’AEM Assets avec Brand Portal
description: 'Découvrez comment configurer AEM Assets avec Brand Portal pour publier des ressources et des collections dans Brand Portal. '
contentOwner: VG
feature: Brand Portal
role: Admin
exl-id: cde35555-259f-4d16-999f-2b93d597b8a5
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1649'
ht-degree: 52%

---

# Configuration d’AEM Assets avec Brand Portal {#configure-integration-64}

Adobe Experience Manager (AEM) Assets est configuré avec Brand Portal via [!DNL Adobe I/O], qui fournit un jeton IMS pour autoriser votre client Brand Portal.

>[!NOTE]
>
>La configuration d’AEM Assets avec Brand Portal via [!DNL Adobe I/O] est prise en charge sur AEM 6.4.8.0 et versions ultérieures.
>
>Auparavant, Brand Portal était configuré dans l’interface utilisateur classique via la passerelle OAuth héritée, qui fait appel à l’échange de jetons JWT pour obtenir un jeton d’accès IMS en vue de l’autorisation.

>[!TIP]
>
>***Pour les clients existants uniquement***
>
>Il est recommandé de continuer à utiliser la configuration de la passerelle OAuth héritée. Si vous rencontrez des problèmes avec la configuration héritée de la passerelle OAuth, supprimez la configuration existante et créez une configuration via [!DNL Adobe I/O].

Cette aide décrit les deux cas d’utilisation suivants :

* [Nouvelle configuration](#configure-new-integration-64) : Si vous êtes un nouvel utilisateur Brand Portal et que vous souhaitez configurer votre instance d’auteur AEM Assets avec Brand Portal, vous pouvez créer une configuration sur  [!DNL Adobe I/O].
* [Configuration](#upgrade-integration-64) de la mise à niveau : Si vous êtes déjà un utilisateur Brand Portal avec votre instance d’auteur AEM Assets configurée avec Brand Portal sur la passerelle OAuth héritée, il est recommandé de supprimer les configurations existantes et de créer une configuration sur  [!DNL Adobe I/O].

Cette aide s’adresse à un public familiarisé avec les technologies suivantes :

* Installation, configuration et administration des packages Adobe Experience Manager et AEM

* Utilisation des systèmes d’exploitation Linux et Microsoft Windows

## Prérequis {#prerequisites}

Pour configurer AEM Assets avec Brand Portal, vous devez disposer des éléments suivants :

* Une instance d’auteur AEM Assets en cours d’exécution avec le dernier Service Pack
* URL du client Brand Portal
* Un utilisateur disposant de droits d’administrateur système sur l’organisation IMS du client Brand Portal

[Télécharger et installer AEM 6.4](#aemquickstart)

[Téléchargez et installez le dernier Service Pack AEM](#servicepack)

### Télécharger et installer AEM 6.4 {#aemquickstart}

Il est recommandé d’utiliser AEM 6.4 pour configurer une instance d’auteur AEM. Si vous ne l’avez pas, téléchargez-le à partir des emplacements suivants :

* Si vous êtes déjà un client AEM, téléchargez AEM 6.4 à partir de [Adobe Licensing website](http://licensing.adobe.com).

* Si vous êtes un partenaire d’Adobe, utilisez [Programme de formation des partenaires d’Adobe](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) pour demander AEM 6.4.

Après avoir téléchargé AEM, consultez la page [Déploiement et maintenance](https://helpx.adobe.com/fr/experience-manager/6-4/sites/deploying/using/deploy.html#defaultlocalinstall) pour obtenir des instructions sur la configuration d’une instance d’auteur AEM.

### Télécharger et installer le dernier Service Pack AEM {#servicepack}

Pour obtenir des instructions détaillées, voir

* [Notes de mise à jour d’AEM 6.4, Pack de services ](https://helpx.adobe.com/fr/experience-manager/6-4/release-notes/sp-release-notes.html)

**Contactez** Customer Care si vous ne parvenez pas à trouver le dernier package AEM ou le Service Pack.

## Création d’une configuration {#configure-new-integration-64}

Effectuez les étapes suivantes dans l’ordre indiqué si vous configurez AEM Assets avec Brand Portal pour la première fois :

1. [Obtention d’un certificat public](#public-certificate)
1. [ [!DNL Adobe I/O] Création de l’intégration](#createnewintegration)
1. [Création d’une configuration de compte IMS](#create-ims-account-configuration)
1. [Configuration du service cloud](#configure-the-cloud-service)
1. [Test de la configuration](#test-integration)

>[!NOTE]
>
>Une instance d’auteur AEM Assets ne doit être configurée qu’avec un seul client Brand Portal.

### Création de la configuration IMS {#create-ims-configuration}

La configuration IMS authentifie votre client Brand Portal avec l’instance d’auteur AEM Assets.

La configuration IMS comprend deux étapes :

* [Obtention d’un certificat public](#public-certificate)
* [Création d’une configuration de compte IMS](#create-ims-account-configuration)

### Obtention d’un certificat public {#public-certificate}

Le certificat public vous permet d’authentifier votre profil sur [!DNL Adobe I/O].

1. Connexion à votre instance d’auteur AEM Assets
URL par défaut : http:// localhost:4502/aem/start.html
1. Dans le panneau **Outils** ![Outils](assets/tools.png), accédez à **[!UICONTROL Sécurité]** > **[!UICONTROL Adobe des configurations IMS]**.

   ![Interface utilisateur de configuration du compte Adobe IMS](assets/ims-config1.png)

1. La page Configurations d’Adobe IMS s’ouvre.

   Cliquez sur **[!UICONTROL Créer]**.

   Vous accédez alors à la page **[!UICONTROL Adobe de la configuration du compte technique IMS]**.

1. Par défaut, l’onglet **Certificat** s’ouvre.

   Dans **Solution cloud**, sélectionnez **[!UICONTROL Adobe Brand Portal]**.

1. Cochez la case **[!UICONTROL Créer un certificat]** et indiquez un **alias** pour le certificat. L’alias sert de nom à la boîte de dialogue.

1. Cliquez sur **[!UICONTROL Créer un certificat]**. Une boîte de dialogue s’affiche. Cliquez sur **[!UICONTROL OK]** pour générer le certificat public.

   ![Création d’un certificat](assets/ims-config2.png)

1. Cliquez sur **[!UICONTROL Télécharger la clé publique]** et enregistrez le fichier de certificat *AEM-Adobe-IMS.crt* sur votre ordinateur. Le fichier de certificat est utilisé pour [créer [!DNL Adobe I/O] l’intégration](#createnewintegration).

   ![Téléchargement du certificat](assets/ims-config3.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   Dans l’onglet **Compte**, vous créez le compte Adobe IMS, mais vous avez pour cela besoin des détails d’intégration. Gardez cette page ouverte pour l’instant.

   Ouvrez un nouvel onglet et [Créer [!DNL Adobe I/O] l’intégration](#createnewintegration) pour obtenir les détails de l’intégration pour les configurations de compte IMS.

### Créer une intégration [!DNL Adobe I/O] {#createnewintegration}

[!DNL Adobe I/O]L’intégration génère une clé API, un secret client et une charge utile (JWT), dont vous avez besoin pour configurer les configurations de compte IMS.

1. Connectez-vous à la console [!DNL Adobe I/O] avec les privilèges d’administrateur système sur l’organisation IMS du client Brand Portal.

   URL par défaut : [https://console.adobe.io/](https://console.adobe.io/)

1. Cliquez sur **[!UICONTROL Créer une intégration]**.

1. Sélectionnez **[!UICONTROL Accéder à une API]**, puis cliquez sur **[!UICONTROL Continuer]**.

   ![Création d’une intégration](assets/create-new-integration1.png)

1. La page Créer une intégration s’affiche.

   Sélectionnez votre entreprise dans la liste déroulante.

   Dans **[!UICONTROL Experience Cloud]**, sélectionnez **[!UICONTROL AEM Brand Portal]** et cliquez sur **[!UICONTROL Continuer]**.

   Si l’option Brand Portal est désactivée, assurez-vous d’avoir sélectionné la bonne entreprise dans la liste déroulante au-dessus de l’option **[!UICONTROL Adobe Services]** (Services Adobe). Si vous ne connaissez pas le nom de votre entreprise, contactez votre administrateur.

   ![Création d’une intégration](assets/create-new-integration2.png)

1. Spécifiez le nom et la description de l’intégration. Cliquez sur **[!UICONTROL Select a File from your computer]** (Sélectionner un fichier sur votre ordinateur) et téléchargez le fichier `AEM-Adobe-IMS.crt` téléchargé dans la section [obtenir des certificats publics](#public-certificate).

1. Sélectionnez le profil de votre entreprise.

   Ou sélectionnez le profil **[!UICONTROL Assets Brand Portal]** par défaut et cliquez sur **[!UICONTROL Créer une intégration]**. L’intégration est créée.

1. Appuyez sur **[!UICONTROL Continue to integration details]** (Continuer vers les détails d’intégration) pour afficher les informations d’intégration.

   Copiez la **[!UICONTROL clé API]**.

   Cliquez sur **[!UICONTROL Retrieve Client Secret]** (Récupérer le secret client) et copiez la clé secrète client.

   ![Clé API, secret client et informations de charge utile d’une intégration](assets/create-new-integration3.png)

1. Accédez à l’onglet **[!UICONTROL JWT]** et copiez la **[!UICONTROL charge JWT]**.

   Les informations de clé API, de clé secrète client et de charge utile JWT seront utilisées pour créer la configuration du compte IMS.

### Création d’une configuration de compte IMS {#create-ims-account-configuration}

Vérifiez que vous avez effectué les étapes suivantes :

* [Obtention d’un certificat public](#public-certificate)
* [Intégration de création [!DNL Adobe I/O] ](#createnewintegration)

**Procédure de création de la configuration du compte IMS :**

1. Ouvrez la page Configuration IMS de l’onglet **[!UICONTROL Comptes]**. Vous avez gardé la page ouverte à la fin de la section [Obtention d’un certificat public](#public-certificate).

1. Spécifiez un **[!UICONTROL titre]** pour le compte IMS.

   Dans **[!UICONTROL Serveur d’autorisation]**, entrez l’adresse URL : [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Collez la clé API, le secret client et la charge utile JWT que vous avez copiés à la fin de [Create [!DNL Adobe I/O] integration](#createnewintegration).

   Cliquez sur **[!UICONTROL Créer]**.

   L’intégration est créée.

   ![Configuration du compte IMS](assets/create-new-integration6.png)

1. Sélectionnez la configuration IMS et cliquez sur **[!UICONTROL Contrôle de l’intégrité]**. Une boîte de dialogue s’affiche.

   Cliquez sur **[!UICONTROL Vérifier]**. Une fois la connexion établie, le message *Jeton récupéré avec succès* s’affiche.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Vous ne devez avoir qu’une seule configuration IMS. N’en créez pas plusieurs.
>
>Assurez-vous que la configuration IMS réussit le contrôle d’intégrité. Si tel n’est pas le cas, elle n’est pas valide. Vous devez la supprimer et créer une configuration valide.

### Configuration du service cloud {#configure-the-cloud-service}

Pour créer une configuration de service cloud Brand Portal, procédez comme suit :

1. Connexion à votre instance d’auteur AEM Assets

   URL par défaut : http://localhost:4502/aem/start.html
1. Dans le panneau **Outils** ![Outils](assets/tools.png), accédez à **[!UICONTROL Cloud Services &quot; AEM Brand Portal]**.

   La page Configurations de Brand Portal s’affiche.

1. Cliquez sur **[!UICONTROL Créer]**.

1. Saisissez un **[!UICONTROL titre]** pour la configuration.

   Sélectionnez la configuration IMS que vous avez créée à l’étape [Création d’une configuration de compte IMS](#create-ims-account-configuration).

   Dans **[!UICONTROL URL du service]**, entrez votre URL du client Brand Portal.

   ![](assets/create-cloud-service.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration cloud est alors créée. Votre instance d’auteur AEM Assets est maintenant intégrée au client Brand Portal.

### Test de la configuration {#test-integration}

1. Connexion à votre instance d’auteur AEM Assets

   URL par défaut : http://localhost:4502/aem/start.html

1. Dans le panneau **Outils** ![Outils](assets/tools.png), accédez à **[!UICONTROL Déploiement &quot; Réplication]**.

   ![](assets/test-integration1.png)

1. La page Réplication s’ouvre.

   Cliquez sur **[!UICONTROL Agents sur l’auteur]**.

   ![](assets/test-integration2.png)

1. Quatre agents de réplication sont créés pour chaque client.

   Localisez les agents de réplication de votre client Brand Portal.

   Cliquez sur l’URL de l’agent de réplication.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >Les agents de réplication fonctionnent en parallèle et partagent la distribution de la tâche de manière égale, augmentant ainsi la vitesse de publication de quatre fois la vitesse d’origine. Une fois le service cloud configuré, aucune configuration supplémentaire n’est nécessaire pour activer les agents de réplication activés par défaut afin d’activer la publication parallèle de plusieurs ressources.

1. Pour vérifier la connexion entre l’auteur AEM Assets et Brand Portal, cliquez sur **[!UICONTROL Tester la connexion]**.

   ![](assets/test-integration4.png)

1. En bas des résultats du test, vérifiez que la réplication a réussi.

   ![](assets/test-integration5.png)


1. Vérifiez les résultats du test un par un sur les quatre agents de réplication.

   >[!NOTE]
   >
   >Évitez de désactiver tout agent de réplication, car cela peut entraîner l’échec de la réplication de certaines ressources.
   >
   >Assurez-vous que les quatre agents de réplication sont configurés pour éviter l’erreur de délai d’expiration. Voir [dépannage des problèmes de publication en parallèle sur Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html#connection-timeout).

Brand Portal est correctement configuré avec votre instance d’auteur AEM Assets. Vous pouvez maintenant effectuer les tâches suivantes :

* [Publication de ressources à partir d’AEM Assets sur Brand Portal](../assets/brand-portal-publish-assets.md)
* [Publication de dossiers à partir d’AEM Assets sur Brand Portal](../assets/brand-portal-publish-folder.md)
* [Publication de collections à partir d’AEM Assets sur Brand Portal](../assets/brand-portal-publish-collection.md)
* [Configurez l’](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) approvisionnement des ressources pour permettre aux utilisateurs de Brand Portal de contribuer et de publier des ressources dans AEM Assets.

## Mise à niveau de la configuration {#upgrade-integration-64}

Effectuez les étapes suivantes dans l’ordre indiqué pour mettre à niveau les configurations existantes :
1. [Vérification des tâches en cours](#verify-jobs)
1. [Suppression des configurations existantes](#delete-existing-configuration)
1. [Création d’une configuration](#configure-new-integration-64)

### Vérification des tâches en cours {#verify-jobs}

Assurez-vous qu’aucune tâche de publication n’est en cours d’exécution sur votre instance d’auteur AEM Assets avant d’apporter des modifications. Pour ce faire, vous pouvez vérifier les quatre agents de réplication et vous assurer que la file d’attente est idéale/vide.

1. Connexion à votre instance d’auteur AEM Assets

   URL par défaut : http://localhost:4502/aem/start.html

1. Dans le panneau **Outils** ![Outils](assets/tools.png), accédez à **[!UICONTROL Déploiement &quot; Réplication]**.

1. La page Réplication s’ouvre.

   Cliquez sur **[!UICONTROL Agents sur l’auteur]**.

   ![](assets/test-integration2.png)

1. Localisez les agents de réplication de votre client Brand Portal.

   Assurez-vous que la **file d’attente est inactive** pour tous les agents de réplication, qu’aucune tâche de publication n’est principale.

   ![](assets/test-integration3.png)

### Suppression des configurations existantes {#delete-existing-configuration}

Vous devez exécuter la liste de contrôle suivante lors de la suppression de la configuration existante.
* Suppression des quatre agents de réplication
* Suppression du service cloud
* Suppression d’un utilisateur MAC

Effectuez les étapes suivantes pour supprimer la configuration existante :

1. Connectez-vous à votre instance d’auteur AEM Assets et ouvrez CRX Lite en tant qu’administrateur.

   URL par défaut : http:// localhost:4502/crx/de/index.jsp

1. Accédez à `/etc/replications/agents.author` et supprimez les quatre agents de réplication de votre client Brand Portal.

   ![](assets/delete-replication-agent.png)

1. Accédez à `/etc/cloudservices/mediaportal` et supprimez la **configuration du Cloud Service**.

   ![](assets/delete-cloud-service.png)

1. Accédez à `/home/users/mac` et supprimez l’utilisateur **MAC** de votre client Brand Portal.

   ![](assets/delete-mac-user.png)


Vous pouvez désormais [créer une configuration](#configure-new-integration-64) sur votre instance d’auteur AEM 6.4 sur [!DNL Adobe I/O].



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

Une fois la réplication réussie, vous pouvez publier des ressources, des dossiers et des collections sur Brand Portal. Pour plus d’informations, voir :

* [Publication de ressources sur Brand Portal](brand-portal-publish-assets.md)
* [Publication de ressources et de dossiers sur Brand Portal](brand-portal-publish-folder.md)
* [Publication de collections sur Brand Portal](brand-portal-publish-collection.md)
