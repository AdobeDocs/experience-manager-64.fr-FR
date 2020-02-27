---
title: Configuration du balisage basé sur AI à l’aide de Smart Content Service
description: Découvrez comment configurer le balisage intelligent et le balisage intelligent amélioré dans AEM à l’aide du service de contenu dynamique.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90d39315207129aa4fc616e6fffb4bad5c450a7b

---


# Configure asset tagging using the Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

Découvrez comment configurer le balisage intelligent et le balisage intelligent amélioré dans AEM à l’aide du service de contenu dynamique.

Vous pouvez intégrer Adobe Experience Manager (AEM) à Smart Content Service. Utilisez cette configuration pour accéder à Smart Content Service depuis AEM et baliser automatiquement vos images.

L’article détaille les tâches essentielles suivantes qui sont requises pour configurer le service de contenu dynamique. En arrière-plan, le serveur AEM authentifie vos informations d’identification du service auprès de la passerelle Adobe I/O avant de transférer votre demande au service de contenu dynamique.

1. Création d’une configuration de service de contenu dynamique dans AEM pour générer une clé publique. Obtention d’un certificat public pour l’intégration OAuth.
1. Création d’une intégration dans Adobe I/O et téléchargement de la clé publique générée.
1. Configuration de votre instance AEM en utilisant la clé API et d’autres informations d’identification d’Adobe I/O.
1. Facultativement, activation du balisage automatique lors du téléchargement de ressources.

## Conditions préalables {#prerequisites}

Avant de pouvoir utiliser le service de contenu dynamique, assurez-vous de respecter les conditions suivantes pour créer une intégration sur Adobe I/O :

* L’organisation doit disposer d’un compte Adobe ID pourvu de droits d’administrateur.
* Le service de contenu dynamique est activé pour votre organisation.

To enable Enhanced Smart Tags, in addition to the above, also install the latest [AEM service pack](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

## Obtention d’un certificat public {#obtain-public-certificate}

Un certificat public permet d’authentifier votre profil sur Adobe I/O.

1. Dans l’interface utilisateur AEM, appuyez sur le logo AEM et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Services cloud hérités]**.

1. Dans la page Cloud Services, appuyez/cliquez sur **[!UICONTROL Configurer maintenant]** sous **[!UICONTROL Ressources – Balises intelligentes]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, spécifiez un titre et un nom pour la configuration de balises intelligentes. Cliquez/appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Service de contenu dynamique AEM]**, utilisez les valeurs suivantes :

   **[!UICONTROL URL du service]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Serveur d’autorisation]**: `https://ims-na1.adobelogin.com`

   Laissez les autres champs vides pour l’instant (pour les remplir ultérieurement). Appuyez/cliquez sur **[!UICONTROL OK]**.

   ![Boîte de dialogue Service de contenu dynamique AEM pour fournir une URL de service de contenu](assets/aem_scs.png)

   >[!NOTE]
   >
   >The URL provided as [!UICONTROL Service URL] is not accessible via browser and generates a 404 error. La configuration fonctionne correctement avec la même valeur que le paramètre URL [!UICONTROL du] service. Pour connaître l’état général du service d’E/S Adobe et le planning de maintenance, consultez le site Web [https://status.adobe.com](https://status.adobe.com).

1. Appuyez/cliquez sur **[!UICONTROL Télécharger le certificat public pour l’intégration OAuth]** et téléchargez le fichier de certificat public `AEM-SmartTags.crt`.

   ![Représentation des paramètres créés pour le service de balisage intelligent](assets/download_link.png)

## Création de l’intégration Adobe I/O {#create-adobe-i-o-integration}

Pour utiliser les API du service de contenu dynamique, créez une intégration dans Adobe I/O afin de générer une clé API, un identifiant de compte technique, un identifiant d’organisation et un secret de client.

1. Accédez à [https://console.adobe.io](https://console.adobe.io/).
1. Depuis la page **[!UICONTROL Integrations]** (Intégrations), sélectionnez votre organisation.
1. Appuyez/cliquez sur **[!UICONTROL New Integration]** (Nouvelle intégration).
1. Sur la page **[!UICONTROL Créer une intégration]**, sélectionnez **[!UICONTROL Accéder à une API]**. Appuyez/cliquez sur **[!UICONTROL Continuer]**.
1. Sous **[!UICONTROL Experience Cloud]**, sélectionnez **[!UICONTROL Contenu intelligent]**. Appuyez/cliquez sur **[!UICONTROL Continuer]**.

   ![Lors de la création d’une intégration, sélectionnez dans les options disponibles Contenu dynamique sous Experience Cloud.](assets/smart_content.png)

1. Sur la page suivante, sélectionnez **[!UICONTROL Nouvelle intégration]**. Appuyez/cliquez sur **[!UICONTROL Continuer]**.
1. Sur la page **[!UICONTROL Informations concernant l’intégration]**, indiquez un nom pour la passerelle d’intégration et ajoutez une description.
1. Dans **[!UICONTROL Certificats de clés publiques]**, chargez le fichier `AEM-SmartTags.crt` que vous avez téléchargé ci-dessus.
1. Appuyez/cliquez sur **[!UICONTROL Créer une intégration]**.
1. Pour afficher les informations sur l’intégration, appuyez/cliquez sur **[!UICONTROL Continuer vers les informations concernant l’intégration]**.

   ![Dans l’onglet Aperçu, vous pouvez consulter les informations fournies pour l’intégration.](assets/integration_details.png)

## Configuration du service de contenu dynamique {#configure-smart-content-service}

Pour configurer l’intégration, utilisez les valeurs des champs Identifiant de compte technique, Identifiant d’organisation, Secret du client, Serveur d’autorisation et Clé API de l’intégration Adobe I/O. La création d’une configuration cloud de balises intelligentes permet d’authentifier les demandes d’API provenant de l’instance AEM.

1. Depuis l’interface utilisateur AEM, appuyez/cliquez sur le logo AEM. Accédez à **[!UICONTROL Outils > Service cloud > Services cloud hérités]** pour ouvrir la console des services cloud.
1. Sous **[!UICONTROL Ressources – Balises intelligentes]**, ouvrez la configuration créée ci-dessus. Sur la page de paramètres du service, cliquez sur **[!UICONTROL Modifier]**.
1. Dans la boîte de dialogue **[!UICONTROL Service de contenu dynamique AEM]**, utilisez les valeurs préremplies pour les champs **[!UICONTROL URL de service]** et **[!UICONTROL Serveur d’autorisation]**.
1. Pour les champs Clé API, ID de compte technique, ID d’organisation et Client secret, utilisez les valeurs générées ci-dessus.

## Valider la configuration {#validate-the-configuration}

Une fois la configuration terminée, vous pouvez utiliser un MBean JMX pour valider la configuration. Pour procéder à la validation, suivez ces étapes.

1. Dans AEM, pour ouvrir la console OSGi, cliquez sur **[!UICONTROL Outils > Opérations > Console]** Web. Cliquez sur **[!UICONTROL Principal > JMX]**.
1. Cliquez sur **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Les **[!UICONTROL tâches relatives à SimilaritySearch]** s’ouvrent alors.
1. Cliquez sur **[!UICONTROL validateConfigs()]**. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

   Le résultat de la validation s’affiche dans la même boîte de dialogue.

## Enable smart tagging in the DAM Update Asset workflow (Optional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Dans l’interface utilisateur AEM, appuyez/cliquez sur le logo AEM et accédez à **[!UICONTROL Outils > Processus > Modèles]**.
1. Sur la page **[!UICONTROL Modèles de processus]**, sélectionnez le modèle de processus **[!UICONTROL Ressources de mise à jour de DAM]**.
1. Appuyez/cliquez sur **[!UICONTROL Modifier]** dans la barre d’outils.
1. Développez le panneau latéral pour afficher les étapes. Faites glisser l’étape **[!UICONTROL Balisage intelligent de la ressource]** disponible dans la section Processus de DAM (gestion des actifs numériques) et placez-la après l’étape **[!UICONTROL Traiter les miniatures]**.

   ![Ajouter l’étape Balisage intelligent de la ressource après l’étape Miniature des processus dans le processus Ressources de mise à jour de gestion des actifs numériques.](assets/chlimage_1-105.png)

1. Ouvrez l’étape en mode édition. Sous **[!UICONTROL Paramètres avancés]**, vérifiez que l’option **[!UICONTROL Avance du gestionnaire]** est sélectionnée.

   ![chlimage_1-106](assets/chlimage_1-106.png)

1. Dans l’onglet **[!UICONTROL Arguments]**, sélectionnez **[!UICONTROL Ignorer les erreurs]** si vous souhaitez que le processus se termine même si l’étape de balisage automatique échoue.

   ![chlimage_1-107](assets/chlimage_1-107.png)

   Pour baliser les ressources lors de leur chargement, que le balisage intelligent soit activé ou non dans les dossiers, cochez la case **[!UICONTROL Ignorer l’indicateur de balise intelligente]**.

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. Appuyez/cliquez sur **[!UICONTROL OK]** pour fermer l’étape du processus, puis enregistrez le workflow.

>[!MORELIKETHIS]
>
>* [Comprendre les balises actives dans les ressources AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-understand.html)
>* [Utilisation de balises intelligentes avec des ressources AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-use.html)
>* [Utilisation des balises actives améliorées avec les ressources AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-feature-video-use.html)
>* [Configuration de balises actives améliorées dans les ressources AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-technical-video-setup.html)

