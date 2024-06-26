---
title: Configuration de l’intégration d’AEM Assets à Experience Cloud
description: Découvrez comment configurer l’intégration d’AEM Assets à Experience Cloud.
feature: Asset Management
role: User, Architect, Admin
exl-id: f8629c30-1901-4b6e-b5a6-e46ee3c72fba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 84%

---

# Configuration de l’intégration d’AEM Assets à Experience Cloud {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Si vous êtes un client d’Adobe Experience Cloud, vous pouvez synchroniser vos ressources dans Assets avec Adobe Creative Cloud, et vice versa. Vous pouvez également synchroniser vos ressources avec Experience Cloud et vice versa. Vous pouvez configurer cette synchronisation via [!DNL Adobe I/O]. Le nouveau nom d’[!DNL Adobe Marketing Cloud] est [!DNL Adobe Experience Cloud].

Le workflow pour configurer cette intégration est le suivant :

1. Créez une authentification dans [!DNL Adobe I/O] à l’aide d’une passerelle publique et obtenez un ID d’application.
1. Créez un profil sur votre instance AEM Assets à l’aide de l’ID d’application.
1. Utilisez cette configuration pour synchroniser vos ressources.

En arrière-plan, le serveur authentifie votre profil avec la passerelle, puis synchronise les données entre AEM Assets et Experience Cloud.

>[!NOTE]
>
>Cette fonctionnalité est obsolète dans AEM Assets. Vous trouverez des alternatives dans les [bonnes pratiques d’intégration d’AEM et de Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). Si vous avez des questions, [contactez le service clientèle d’Adobe](https://www.adobe.com/account/sign-in.supportportal.html).

<!-- Hiding this for now via cqdoc-16834.
![Flow of data when AEM Assets and Creative Cloud are integrated](assets/chlimage_1-287.png)

>[!NOTE]
>
>Sharing assets between Adobe Experience Cloud and Adobe Creative Cloud requires administrator privileges on the AEM instance.
-->

## Création d’une application {#create-an-application}

1. Accédez à l’interface de passerelle Adobe Developer en vous connectant à [https://legacy-oauth.cloud.adobe.io](https://legacy-oauth.cloud.adobe.io/).

   >[!NOTE]
   >
   >Vous avez besoin de privilèges d’administrateur pour créer un ID d’application.

1. Dans le volet de gauche, accédez à **[!UICONTROL Outils de développement]** > **[!UICONTROL Applications]** pour afficher la liste des applications.
1. Cliquez sur **[!UICONTROL Ajouter]** ![aem_assets_addcircle_icon](assets/aem_assets_addcircle_icon.png) pour créer une application.
1. Dans la liste **[!UICONTROL Informations d’identification du client]**, sélectionnez **[!UICONTROL Compte de service (déclaration JWT)]**, qui est un service de communication serveur à serveur pour l’authentification de serveur.

   ![chlimage_1-288](assets/chlimage_1-288.png)

1. Spécifiez le nom de l’application et une description facultative.
1. Dans la liste **[!UICONTROL Organisation]**, sélectionnez l’organisation pour laquelle vous souhaitez synchroniser les ressources.
1. Dans la liste **[!UICONTROL Portée]**, sélectionnez **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** et **[!UICONTROL cc-share]**.
1. Cliquez sur **[!UICONTROL Créer]**. Un message indique que l’application est créée.

   ![Notification de création réussie de l’application pour intégrer AEM Assets à Adobe Creative Cloud](assets/chlimage_1-289.png)

1. Copiez le **[!UICONTROL ID de l’application]** qui est généré pour la nouvelle application.

   >[!CAUTION]
   >
   >Veillez à ne pas copier par inadvertance la variable **[!UICONTROL Secret de l’application]** au lieu de **[!UICONTROL ID de l’application]**.

## Ajout d’une nouvelle configuration à Experience Cloud {#add-a-new-configuration}

1. Cliquez sur le logo AEM sur l’interface utilisateur de votre instance AEM Assets locale et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Déploiement]** > **[!UICONTROL Services cloud hérités]**.

1. Localisez le service **[!UICONTROL Adobe Experience Cloud]**. Si la configuration n’existe pas, cliquez sur **[!UICONTROL Configurer maintenant]**. Si des configurations existent, cliquez sur **[!UICONTROL Afficher les configurations]**, puis sur `+` pour ajouter une nouvelle configuration.

   >[!NOTE]
   >
   >Utilisez un compte Adobe ID pourvu de droits d’administrateur pour l’organisation.

1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un titre et un nom pour la nouvelle configuration et cliquez sur **[!UICONTROL Créer]**.

   ![Définition du nom d’une nouvelle configuration pour intégrer AEM Assets et Creative Cloud](assets/cloudservices_configure_mc.png)

1. Dans le champ **[!UICONTROL URL du client]**, spécifiez l’URL d’AEM Assets. Dans le passé, si l’URL était définie comme `https://<tenant_id>.marketing.adobe.com`, remplacez-la par `https://<tenant_id>.experiencecloud.adobe.com`.

   1. Accédez à **Outils > Services cloud > Services cloud hérités**. Sous Adobe Experience Cloud, cliquez sur **Afficher les configurations**.
   1. Sélectionnez la configuration existante à modifier. Modifiez la configuration et remplacez `marketing.adobe.com` par `experiencecloud.adobe.com`.
   1. Enregistrez la configuration. Testez les agents de réplication MAC-sync.

1. Dans le champ **[!UICONTROL ID client]**, collez l’ID d’application que vous avez copié à la fin de la procédure [Création d’une application](#create-an-application).

   ![Indication des valeurs d’ID d’application requises pour intégrer AEM Assets et Creative Cloud](assets/cloudservices_tenant_info.png)

1. Sous **[!UICONTROL Synchronisation]**, sélectionnez **[!UICONTROL Activé]** pour activer la synchronisation, puis cliquez sur **[!UICONTROL OK]**. Si vous sélectionnez **Désactivé**, la synchronisation opère dans une seule direction.

1. Sur la page de configuration, cliquez sur **[!UICONTROL Afficher la clé publique]** afin d’afficher la clé publique générée pour votre instance. Vous pouvez également cliquer sur **[!UICONTROL Télécharger la clé publique pour la passerelle OAuth]** afin de télécharger le fichier contenant la clé publique. Ouvrez ensuite le fichier pour afficher la clé publique.

## Activer la synchronisation {#enable-synchronization}

1. Affichez la clé publique en utilisant l’une des méthodes suivantes mentionnées à la dernière étape de la procédure [Ajout d’une nouvelle configuration à Experience Cloud](#add-a-new-configuration). Cliquez sur **[!UICONTROL Afficher la clé publique]**.

1. Copiez la clé publique et collez-la dans le champ **[!UICONTROL Clé publique]** de l’interface de configuration de l’application que vous avez créée dans la section [Création d’une application](#create-an-application).

   ![chlimage_1-293](assets/chlimage_1-293.png)

1. Cliquez sur **[!UICONTROL Mettre à jour]**. Synchronisez maintenant vos ressources avec l’instance AEM Assets.

## Test de la synchronisation {#test-the-synchronization}

1. Cliquez sur le logo AEM sur l’interface utilisateur de votre instance AEM Assets locale et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Déploiement]** > **[!UICONTROL Réplication]** pour localiser les profils de réplication créés en vue de la synchronisation.
1. Sur la page **[!UICONTROL Réplication]**, cliquez sur **[!UICONTROL Agents sur l’auteur]**.
1. Dans la liste des profils, cliquez sur le profil de réplication par défaut de votre entreprise pour l’ouvrir.
1. Dans la boîte de dialogue, cliquez sur **[!UICONTROL Tester la connexion]**.

   ![Test de la connexion et définition du profil de réplication par défaut pour votre organisation](assets/chlimage_1-294.png)

1. Une fois le test de réplication terminé, recherchez le message de réussite à la fin des résultats des tests.

## Ajout d’utilisateurs à Experience Cloud {#add-users-to-experience-cloud}

1. Connectez-vous à Experience Cloud avec les informations d’identification de l’administrateur.
1. À partir des rails, accédez à **[!UICONTROL Administration]**, puis cliquez sur **[!UICONTROL Démarrer le tableau de bord Grands comptes]**.
1. Sur le rail, cliquez sur **[!UICONTROL Utilisateurs]** pour ouvrir la page **[!UICONTROL Gestion des utilisateurs]**.
1. Dans la barre d’outils, cliquez sur **Ajouter** ![aem_assets_add_icon](assets/aem_assets_add_icon.png).
1. Ajoutez un ou plusieurs utilisateurs auxquels vous souhaitez offrir la possibilité de partager des ressources avec Creative Cloud.

   >[!NOTE]
   >
   >Seuls les utilisateurs que vous ajoutez à Experience Cloud peuvent partager des ressources d’AEM Assets vers Creative Cloud.

## Échange de ressources entre AEM Assets et Experience Cloud {#exchange-assets-between-aem-and-experience-cloud}

1. Connectez-vous à AEM Assets.
1. Dans la console Assets, créez un dossier et téléchargez des ressources vers ce dossier. Par exemple, créez un dossier **mc-demo** et chargez une ressource vers celle-ci.
1. Sélectionnez le dossier et cliquez sur **Partager** ![assets_share](assets/assets_share.png).
1. Dans le menu, sélectionnez **[!UICONTROL Adobe Experience Cloud]**, puis cliquez sur **[!UICONTROL Partager]**. Un message indique que le dossier est partagé avec Experience Cloud.

   ![chlimage_1-295](assets/chlimage_1-295.png)

   >[!NOTE]
   >
   >Le partage d’un dossier de ressources du type `sling:OrderedFolder` n’est pas pris en charge dans le cadre du partage dans Adobe Experience Cloud. Si vous souhaitez partager un dossier, lors de sa création dans AEM Assets, ne sélectionnez pas l’option **[!UICONTROL Ordonné]**.

1. Actualisez l’interface utilisateur d’AEM Assets. Le fichier que vous avez créé dans la console Assets de votre instance AEM Assets locale est copié dans l’interface utilisateur Experience Cloud. La ressource que vous chargez vers le dossier dans AEM Assets s’affiche dans la copie du dossier dans Experience Cloud une fois qu’elle a été traitée par le serveur AEM.
1. Vous pouvez également charger une ressource dans la copie répliquée du dossier Experience Cloud. Une fois qu’elle a été traitée, la ressource s’affiche dans le dossier partagé dans AEM Assets.

<!-- Removing as per PM guidance via https://jira.corp.adobe.com/browse/CQDOC-16834?focusedCommentId=22881523&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-22881523.
## Exchange assets between AEM Assets and Creative Cloud {#exchange-assets-between-aem-assets-and-creative-cloud}

AEM Assets lets you share folders containing assets with Adobe Creative Cloud users.

1. In the Assets console, select the folder to share with Creative Cloud.
1. From the toolbar, click **[!UICONTROL Share]** ![assets_share](assets/assets_share.png).
1. From the list, select the **[!UICONTROL Adobe Creative Cloud]** option.

   >[!NOTE]
   >
   >The options are available for users with read permissions on the root. Users must have the required permission to access the replication agent information of Marketing Cloud.

1. In the **[!UICONTROL Creative Cloud Sharing]** page, add the user to share the folder with and choose a role for the user. Click **[!UICONTROL Save]** and click **[!UICONTROL OK]**.

1. Log on to Creative Cloud with the credentials of the user you shared the folder with. The shared folder is available in Creative Cloud.

The AEM Assets-Marketing Cloud synchronization is designed in a way that the user machine instance from where the asset is uploaded retains the right to modify the asset. Only these changes are propagated to the other instance.

For example, if an asset is uploaded from an AEM Assets (on premises) instance, the changes to the asset from this instance are propagated to the Marketing Cloud instance. However, the changes done from the Marketing Cloud instance to the same asset aren’t propagated to the AEM instance and vice versa for asset uploaded from Marketing Cloud.
-->

>[!MORELIKETHIS]
>
>* [Bonnes pratiques d’intégration d’Assets et de Creative Cloud](/help/assets/aem-cc-integration-best-practices.md)
>* [Meilleures pratiques de partage de dossiers de ressources vers Creative Cloud](/help/assets/aem-cc-folder-sharing-best-practices.md)

