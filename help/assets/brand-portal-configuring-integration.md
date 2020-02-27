---
title: Configuration de l’intégration d’AEM Assets à Brand Portal
description: 'Découvrez comment intégrer AEM Assets à Brand Portal pour publier des ressources et des collections sur Brand Portal. '
contentOwner: VG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Configuration de l’intégration d’AEM Assets à Brand Portal {#configure-aem-assets-integration-with-brand-portal}

Découvrez comment intégrer AEM Assets à Brand Portal pour publier des ressources et des collections sur Brand Portal.

Si vous êtes un client du portail des ressources d’Adobe Experience Manager (AEM), vous pouvez intégrer AEM Assets au portail des marques afin de permettre la publication des ressources sur le portail des marques. Vous pouvez installer cette intégration à travers l’interface Adobe.io.

> [!Note]
>
>Adobe recommande d’effectuer une mise à niveau vers AEM 6.4.1.0 ou une version ultérieure pour s’assurer qu’AEM Assets Brand Portal est intégré à AEM Assets. AEM 6.4 présente une limitation, en ce sens qu’il renvoie une erreur lors de la configuration de l’intégration à Brand Portal et entraîne l’échec de la réplication.

Pour commencer, créez une application (contenant un mécanisme d’authentification) dans la passerelle publique Marketing Cloud. Créez ensuite un profil dans votre instance AEM Assets à l’aide de l’ID d’application obtenu via la passerelle.

Utilisez cette fonctionnalité pour publier des ressources à partir d’AEM Assets sur Brand Portal. À l’arrière-plan, le serveur AEM authentifie votre profil avec la passerelle, puis intègre AEM Assets à Brand Portal.

>[!NOTE]
>
>The UI for configuring oAuth integrations is hosted in [https://legacy-oauth.cloud.adobe.io/](https://legacy-oauth.cloud.adobe.io/), which was earlier hosted in [https://marketing.adobe.com/developer/](https://marketing.adobe.com/developer/).

## Création d’une application JWT {#create-jwt-application}

1. Log in to [https://legacy-oauth.cloud.adobe.io/](https://legacy-oauth.cloud.adobe.io/) with your Adobe ID. Vous accédez à la page Applications  JWT.

   >[!NOTE]
   >
   >Vous ne pouvez créer un ID d’application que si vous êtes l’administrateur système de votre entreprise. Le client est le nom technique de votre entreprise enregistré auprès d’Adobe Marketing Cloud.

2. Select **[!UICONTROL Add Application]** to create an application.
3. Spécifiez un nom **[!UICONTROL d’]** application et une **[!UICONTROL description]** facultative.
4. Dans la liste **[!UICONTROL Organisation]**, sélectionnez l’organisation pour laquelle vous souhaitez synchroniser les ressources.
5. From the **[!UICONTROL Scope]** list, select **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]**, and **[!UICONTROL cc-share]**.
6. Appuyez/cliquez sur **[!UICONTROL Ajouter]**. Une application Service JWT est créée. Vous pouvez modifier l’application et enregistrer.
7. Copiez l’ID d’application généré pour la nouvelle application.

   >[!NOTE]
   >
   >Assurez-vous de ne pas copier par inadvertance le secret d’application au lieu de l’ID d’application.

## Création d’une configuration de cloud {#create-a-new-cloud-configuration}

1. Sur la page **[!UICONTROL Navigation]** de votre instance AEM Assets locale, cliquez/appuyez sur l’icône **[!UICONTROL Outils]** située à gauche.

   ![chlimage_1-252](assets/chlimage_1-252.png)

2. Navigate to **[!UICONTROL Cloud Services > Legacy Cloud Services]**.

   ![cloudservices](assets/cloudservices.png)

3. In the [!UICONTROL Cloud Services] page, locate the **[!UICONTROL Assets Brand Portal]** service under **[!UICONTROL Adobe Experience Cloud]**.

   ![bpcloudservices](assets/bpcloudservices.png)

4. Tap/ click the **[!UICONTROL Configure now]** link below the service to display the [Create Configuration] dialog.
5. Dans la boîte de dialogue [!UICONTROL Créer une configuration], indiquez un titre et un nom pour la nouvelle configuration et cliquez/appuyez sur **[!UICONTROL Créer]**.

   ![bp-config](assets/bp-config.png)

6. In the [!UICONTROL AEM Assets Brand Portal Replication] dialog, specify the URL of your organization in the [!UICONTROL Tenant URL] field.
7. Dans le champ [!UICONTROL ID client], collez l’ID d’application que vous avez copié à la fin de la procédure [Création d’une application](#create-jwt-application). Cliquez sur **[!UICONTROL OK]**.

   ![public-folder-publish](assets/public-folder-publish.png)

8. To make the assets (published from AEM) publicly available to general users of Brand Portal, enable the **[!UICONTROL Public Folder Publish]** check box .

   >[!NOTE]
   >
   >L’option **[!UICONTROL Publication de dossier public]** est disponible à compter d’AEM 6.3.2.1.

9. Sur la page [!UICONTROL Configuration de Brand Portal], cliquez/appuyez sur **[!UICONTROL Afficher la clé publique]** afin d’afficher la clé publique générée pour votre instance.

   ![display-public-key](assets/display-public-key.png)

   Alternatively, click **[!UICONTROL Download Public Key for OAuth Gateway]** to download the file containing the public key. Ouvrez ensuite le fichier pour afficher la clé publique.

## Activation de l’intégration {#enable-integration}

1. Display the public key using one of the following methods mentioned in the last step of the procedure [Add a new configuration to Marketing Cloud](#create-a-new-cloud-configuration).

   * Cliquez sur le bouton **[!UICONTROL Afficher la clé publique]** pour afficher la clé.
   * Ouvrez le fichier téléchargé qui contient la clé.

2. Open the Marketing Cloud Developer Connection interface and click the application you created in [Create an application](#create-jwt-application).
3. Collez la clé publique dans le champ **[!UICONTROL Clé publique]** de l’interface de configuration.
4. Appuyez/cliquez sur **[!UICONTROL Enregistrer]**. Un message confirme que l’application a été mise à jour.

## Test de l’intégration {#test-the-integration}

1. Sur la page **[!UICONTROL Navigation]** de votre instance AEM Assets locale, cliquez sur l’icône **[!UICONTROL Outils]** située à gauche.

   ![chlimage_1-253](assets/chlimage_1-253.png)

2. Navigate to **[!UICONTROL Deployment > Replication]**.

   ![déploiement réplication](assets/deploymentreplication.png)

3. In the [!UICONTROL Replication] page, tap/click **[!UICONTROL Agents on author]**.

   ![agents_on_author](assets/agents_on_author.png)

4. Pour vérifier la connexion entre l’auteur AEM et Brand Portal, ouvrez n’importe lequel des quatre agents de réplication et cliquez sur **[!UICONTROL Tester la connexion]**.

   >[!NOTE]
   >
   >Les agents de réplication fonctionnent en parallèle et partagent la distribution des tâches de manière égale, augmentant ainsi la vitesse de publication de quatre fois la vitesse initiale. Une fois le service cloud configuré, une configuration supplémentaire n’est pas nécessaire pour activer les agents de réplication activés par défaut pour activer la publication parallèle de plusieurs ressources.

   >[!NOTE]
   >
   >Évitez de désactiver tout agent de réplication, car cela peut entraîner l’échec de la réplication de certaines ressources.

   ![aem_assets_parallelpublishing](assets/aem_assets_parallelpublishing.png)

5. En bas des résultats du test, vérifiez que la réplication a réussi.

   ![Replication_success](assets/replication_succeeded.png)

Une fois la réplication réussie, vous pouvez publier des ressources, des dossiers et des collections sur Brand Portal. Pour plus d’informations, voir :

* [Publication de ressources et de dossiers sur Brand Portal](brand-portal-publish-folder.md)
* [Publication de collections sur Brand Portal](brand-portal-publish-collection.md)

## Publication de ressources sur Brand Portal {#publish-assets-to-brand-portal}

Une fois la réplication réussie, vous pouvez publier des ressources, des dossiers et des collections sur Brand Portal. Pour publier des ressources sur Brand Portal, procédez comme suit :

>[!NOTE]
>
>Adobe recommande la publication décalée, de préférence en dehors des heures de pointe, de sorte que l’auteur AEM n’utilise pas une quantité excessive de ressources.

1. Dans la console Assets, placez le curseur au-dessus des ressources souhaitées et sélectionnez l’option **[!UICONTROL Publier]** parmi les actions rapides.

   Vous pouvez également sélectionner les ressources que vous voulez publier sur Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Pour publier les fichiers sur Brand Portal, vous disposez de deux options :
   * [Publication immédiate des fichiers](#publish-now)
   * [Publier les ressources plus tard](#publish-later)

### Publier les ressources maintenant {#publish-now}

Pour publier les ressources sélectionnées sur Brand Portal, effectuez l’une des opérations suivantes :

* From the toolbar, select **[!UICONTROL Quick Publish]**. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.

* From the toolbar, select **[!UICONTROL Manage Publication]**.

   1. Then from the **[!UICONTROL Action]** select **[!UICONTROL Publish to Brand Portal]**, and from **[!UICONTROL Scheduling]** select **[!UICONTROL Now]**. Appuyez/cliquez sur **[!UICONTROL Suivant].**

   2. Within **[!UICONTROL Scope]**, confirm your selection and tap/ click **[!UICONTROL Publish to Brand Portal]**.

Un message indique que les ressources ont été placées en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour voir les ressources publiées.

### Publier les ressources plus tard {#publish-later}

Pour planifier la publication des ressources sur Brand Portal à une date ou une heure ultérieure :

1. Once you have selected assets/ folders to publish, select **[!UICONTROL Manage Publication]** from the tool bar at the top.
2. On **[!UICONTROL Manage Publication]** page, select **[!UICONTROL Publish to Brand Portal]** from **[!UICONTROL Action]** and select **[!UICONTROL Later]** from **[!UICONTROL Scheduling]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Select an **[!UICONTROL Activation date]** and specify time. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
4. Select an **[!UICONTROL Activation date]** and specify time. Appuyez/cliquez sur **[!UICONTROL Suivant]**.
5. Specify a Workflow title under **[!UICONTROL Workflows]**. Tap/ click **[!UICONTROL Publish Later]**.

   ![processus de publication](assets/publishworkflow.png)

Désormais, connectez-vous à Brand Portal pour savoir si les fichiers publiés sont disponibles dans l’interface de Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
