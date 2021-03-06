---
title: Configurez le balisage des ressources à l’aide du service de contenu dynamique.
description: Découvrez comment configurer le balisage intelligent et le balisage intelligent amélioré dans [!DNL Adobe Experience Manager], à l’aide du service de contenu dynamique.
contentOwner: AG
feature: Smart Tags,Tagging
role: Admin
exl-id: 11c5dd92-f824-41d2-9ab2-b32bdeae01b6
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 49%

---

# Configuration du balisage des ressources à l’aide du service de contenu dynamique {#configure-asset-tagging-using-the-smart-content-service}

Vous pouvez intégrer des [!DNL Adobe Experience Manager] avec le service de contenu dynamique utilisant [!DNL Adobe Developer Console]. Utilisez cette configuration pour accéder au service de contenu dynamique à partir de [!DNL Experience Manager].

L’article détaille les tâches essentielles suivantes qui sont requises pour configurer le service de contenu dynamique. À l’arrière-plan, la variable [!DNL Experience Manager] le serveur authentifie vos informations d’identification de service auprès de la fonction [!DNL Adobe Developer Console] passerelle avant de transférer votre demande vers le service de contenu dynamique.

1. [Création d’une configuration de service de contenu dynamique dans pour générer une clé publique. ](#obtain-public-certificate)[!DNL Experience Manager] [Obtenez un certificat public](#obtain-public-certificate) pour l’intégration d’OAuth.

1. [Créez une intégration dans Adobe Developer Console](#create-adobe-i-o-integration) et chargez la clé publique générée.

1. [Configuration de votre déploiement](#configure-smart-content-service) à l’aide de la clé API et d’autres informations d’identification provenant de [!DNL Adobe Developer Console].

1. [Testez la configuration](#validate-the-configuration).

1. Éventuellement, [activation du balisage automatique lors du chargement de ressources](#enable-smart-tagging-in-the-update-asset-workflow-optional).

## Prérequis {#prerequisites}

Avant d’utiliser le service de contenu dynamique, assurez-vous des points suivants pour créer une intégration sur [!DNL Adobe Developer Console]:

* L’organisation doit disposer d’un compte Adobe ID pourvu de droits d’administrateur.

* Le de contenu dynamique est activé pour votre organisation.

Pour activer les balises intelligentes améliorées, en plus de ce qui précède, installez également la dernière version [Service Pack Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=fr).

## Création d’une configuration de service de contenu dynamique pour obtenir un certificat public {#obtain-public-certificate}

Un certificat public vous permet d’authentifier votre profil sur [!DNL Adobe Developer Console].

1. Dans le [!DNL Experience Manager] interface utilisateur, accès **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Cloud Services hérités]**.

1. Dans la page Cloud Services, cliquez sur **[!UICONTROL Configurer maintenant]** under **[!UICONTROL Balises intelligentes des ressources]**.

1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, spécifiez un titre et un nom pour la configuration de balises intelligentes. Cliquez sur **[!UICONTROL Créer]**.

1. Dans la boîte de dialogue **[!UICONTROL Service de contenu dynamique AEM]**, utilisez les valeurs suivantes :

   **[!UICONTROL URL du service]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Serveur d’autorisation]**: `https://ims-na1.adobelogin.com`

   Laissez les autres champs vides pour l’instant (pour les remplir ultérieurement). Cliquez sur **[!UICONTROL OK]**.

   ![Boîte de dialogue Service de contenu dynamique de Experience Manager pour fournir l’URL du service de contenu](assets/aem_scs.png)


   *Figure : Boîte de dialogue Smart Content Service pour fournir l’URL du service de contenu*

   >[!NOTE]
   >
   >L’URL fournie sous la forme [!UICONTROL URL du service] n’est pas accessible par le biais du navigateur et génère une erreur 404. La configuration fonctionne correctement avec la même valeur que la variable [!UICONTROL URL du service] . Pour connaître l’état général du service et le planning de maintenance, voir [https://status.adobe.com](https://status.adobe.com).

1. Cliquez sur **[!UICONTROL Télécharger le certificat public pour l’intégration OAuth]** et télécharger le fichier de certificat public `AEM-SmartTags.crt`.

   ![Représentation des paramètres créés pour le service de balisage intelligent](assets/smart-tags-download-public-cert.png)


   *Figure : Paramètres du service de balisage intelligent*

### Reconfiguration à l’expiration d’un certificat {#certrenew}

Une fois qu’un certificat a expiré, il n’est plus approuvé. Vous ne pouvez pas renouveler un certificat ayant expiré. Pour ajouter un nouveau certificat, procédez comme suit.

1. Connectez-vous en tant qu’administrateur à votre déploiement [!DNL Experience Manager]. Cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Utilisateurs]**.

1. Recherchez et cliquez sur l’utilisateur **[!UICONTROL dam-update-service]**. Cliquez sur l’onglet **[!UICONTROL KeyStore]**.

1. Supprimez le fichier de stockage de clés **[!UICONTROL similaritysearch]** existant avec le certificat arrivé à expiration. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

   ![Supprimez l’entrée similaritysearch existante dans Keystore pour ajouter un nouveau certificat de sécurité.](assets/smarttags_delete_similaritysearch_keystore.png)

   *Figure : Suppression d’une entrée existante`similaritysearch` dans le Keystore pour ajouter un nouveau certificat de sécurité.*

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Ancienne version de Cloud Services]**. Cliquez sur **[!UICONTROL Balises dynamiques de ressources]** > **[!UICONTROL Afficher la configuration]** > **[!UICONTROL Configurations disponibles]**. Cliquez sur la configuration requise.

1. Pour télécharger un certificat public, cliquez sur **[!UICONTROL Télécharger le certificat public pour l’intégration Oauth]**.

1. Accédez à [https://console.adobe.io](https://console.adobe.io) et accédez aux services de contenu intelligent existants sur la page **[!UICONTROL Intégrations]**. Téléchargez le nouveau certificat. Pour plus d’informations, voir les instructions de la section [Création de l’intégration Adobe Developer Console](#create-adobe-i-o-integration).

## Création de l’intégration Adobe Developer Console {#create-adobe-i-o-integration}

Pour utiliser les API de service de contenu dynamique, créez une intégration dans Adobe Developer Console afin d’obtenir [!UICONTROL Clé API] (généré dans [!UICONTROL ID CLIENT] champ de l’intégration d’Adobe Developer Console), [!UICONTROL ID DE COMPTE TECHNIQUE], [!UICONTROL ID D’ORGANISATION], et [!UICONTROL SECRET CLIENT] pour [!UICONTROL Paramètres du service de balisage intelligent des ressources] de la configuration cloud dans [!DNL Experience Manager].

1. Accédez à l’URL [https://console.adobe.io](https://console.adobe.io/) dans un navigateur. Sélectionnez le compte approprié et vérifiez que le rôle d’organisation associé est administrateur système.

1. Créez un projet portant le nom de votre choix. Cliquez sur **[!UICONTROL Add API]** (Ajouter une API).

1. Sur la page **[!UICONTROL Add an API]** (Ajouter une API), sélectionnez **[!UICONTROL Experience Cloud]** puis **[!UICONTROL Smart Content]** (Contenu dynamique). Cliquez sur **[!UICONTROL Next]** (Suivant).

1. Sélectionnez **[!UICONTROL Upload your public key]** (Charger votre clé publique). Fournissez le fichier de certificat téléchargé depuis [!DNL Experience Manager]. Le message [!UICONTROL Public key(s) uploaded successfully] (La ou les clés publiques ont été chargées) s’affiche. Cliquez sur **[!UICONTROL Next]** (Suivant).

   La page [!UICONTROL Create a new Service Account (JWT) credential] (Créer des informations d’identification de compte de service (JWT)) affiche la clé publique du compte de service qui vient d’être configuré.

1. Cliquez sur **[!UICONTROL Next]** (Suivant).

1. Dans la page **[!UICONTROL Select product profiles]** (Sélectionner les profils de produits), sélectionnez **[!UICONTROL Smart Content Services]** (Services de contenu dynamique). Cliquez sur **[!UICONTROL Save configured API]** (Enregistrer l’API configurée). 

   Une page affiche davantage d’informations sur la configuration. Laissez cette page ouverte pour copier et ajouter ces valeurs dans [!UICONTROL Paramètres du service de balisage intelligent des ressources] de la configuration cloud dans [!DNL Experience Manager] pour configurer des balises intelligentes.

   ![Dans l’onglet Overview (Aperçu), vous pouvez consulter les informations fournies pour l’intégration.](assets/integration_details.png)

   *Figure : Détails de l’intégration dans Adobe Developer Console*

## Configuration du service de contenu dynamique {#configure-smart-content-service}

Pour configurer l’intégration, utilisez les valeurs de [!UICONTROL ID DE COMPTE TECHNIQUE], [!UICONTROL ID D’ORGANISATION], [!UICONTROL SECRET CLIENT], et [!UICONTROL ID CLIENT] des champs de l’intégration d’Adobe Developer Console. La création d’une configuration de cloud de balises intelligentes permet d’authentifier les requêtes d’API provenant de [!DNL Experience Manager] déploiement.

1. Dans [!DNL Experience Manager], accédez à **[!UICONTROL Outils > Cloud Service > Cloud Services hérités]** pour ouvrir le [!UICONTROL Cloud Services] console.

1. Sous **[!UICONTROL Ressources – Balises intelligentes]**, ouvrez la configuration créée ci-dessus. Sur la page de paramètres du service, cliquez sur **[!UICONTROL Modifier]**.

1. Dans la boîte de dialogue **[!UICONTROL Service de contenu dynamique AEM]**, utilisez les valeurs préremplies pour les champs **[!UICONTROL URL de service]** et **[!UICONTROL Serveur d’autorisation]**.

1. Pour les champs [!UICONTROL Clé Api], [!UICONTROL Identifiant du compte technique], [!UICONTROL ID d’organisation], et [!UICONTROL Secret du client], copiez et utilisez les valeurs suivantes générées dans [Intégration d’Adobe Developer Console](#create-adobe-i-o-integration).

   | [!UICONTROL Paramètres du service de balisage intelligent des ressources] | [!DNL Adobe Developer Console] champs d&#39;intégration |
   |--- |--- |
   | [!UICONTROL Clé API] | [!UICONTROL ID CLIENT] |
   | [!UICONTROL Identifiant de compte technique] | [!UICONTROL ID DE COMPTE TECHNIQUE] |
   | [!UICONTROL Identifiant d&#39;organisation] | [!UICONTROL ID D’ORGANISATION] |
   | [!UICONTROL Secret client] | [!UICONTROL SECRET CLIENT] |

## Validation de la configuration {#validate-the-configuration}

Une fois la configuration terminée, utilisez un MBean JMX pour la valider. Pour procéder à la validation, suivez ces étapes.

1. Accédez à [!DNL Experience Manager] server at `https://[aem_server]:[port]`.

1. Accédez à **[!UICONTROL Outils > Opérations > Console Web]** pour ouvrir la console OSGi. Cliquez sur **[!UICONTROL Principal > JMX]**.

1. Cliquez sur **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Il s’ouvre. **[!UICONTROL Tâches diverses SimilaritySearch]**.

1. Cliquez sur **[!UICONTROL validateConfigs()]**. Dans le **[!UICONTROL Validation des configurations]** boîte de dialogue, cliquez sur **[!UICONTROL Appeler]**.

   Les résultats de la validation s’affichent dans la même boîte de dialogue.

## Activation du balisage intelligent dans le workflow Ressources de mise à jour de gestion des actifs numériques (facultatif) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Dans [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]**.

1. Sur la page **[!UICONTROL Modèles de processus]**, sélectionnez le modèle de processus **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques (DAM)]**.

1. Cliquez sur **[!UICONTROL Modifier]** dans la barre d’outils.

1. Développez le panneau latéral pour afficher les étapes. Faites glisser l’étape **[!UICONTROL Balisage intelligent de la ressource]** disponible dans la section Processus de DAM (gestion des actifs numériques) et placez-la après l’étape **[!UICONTROL Miniatures des processus]**.

   ![Ajout de l’étape Balisage intelligent de la ressource après l’étape Miniatures des processus dans le processus Ressources de mise à jour de gestion des actifs numériques (DAM)](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Figure : Ajout de l’étape Balisage intelligent de la ressource après l’étape Miniatures des processus dans le processus Ressources de mise à jour de gestion des actifs numériques (DAM).*

1. Ouvrez l’étape en mode édition. Dans **[!UICONTROL Paramètres avancés]**, vérifiez que l’option **[!UICONTROL Avance du gestionnaire]** est sélectionnée.

   ![Configuration du workflow Ressources de mise à jour de gestion des actifs numériques et ajout de l’étape Balisage intelligent](assets/smart-tag-step-properties-workflow1.png)


   *Figure : Configuration du workflow Ressources de mise à jour de gestion des actifs numériques et ajout de l’étape Balisage intelligent*

1. Dans l’onglet **[!UICONTROL Arguments]**, sélectionnez **[!UICONTROL Ignorer les erreurs]** si vous souhaitez que le processus se termine même si l’étape de balisage automatique échoue.

   ![Configuration du workflow Ressources de mise à jour de gestion des actifs numériques pour ajouter l’étape Balisage intelligent et sélectionner l’avance du gestionnaire](assets/smart-tag-step-properties-workflow2.png)


   *Figure : Configuration du workflow Ressources de mise à jour de gestion des actifs numériques pour ajouter l’étape Balisage intelligent et sélectionner l’avance du gestionnaire*

   Pour baliser les ressources lors de leur chargement, et ce, que le balisage intelligent soit activé ou non dans les dossiers, cochez la case **[!UICONTROL Ignorer l’indicateur de balise intelligente]**.

   ![Configurez le workflow Ressources de mise à jour de gestion des actifs numériques pour ajouter une étape de balise intelligente et sélectionnez Ignorer l’indicateur de balise intelligente .](assets/smart-tag-step-properties-workflow3.png)


   *Figure : Configurez le workflow Ressources de mise à jour de gestion des actifs numériques pour ajouter une étape de balise intelligente et sélectionnez Ignorer l’indicateur de balise intelligente .*

1. Cliquez sur **[!UICONTROL OK]** pour fermer l’étape du processus, puis enregistrez ce dernier.

>[!MORELIKETHIS]
>
>* [Gestion des balises intelligentes](managing-smart-tags.md)
>* [Présentation et entraînement des balises intelligentes](enhanced-smart-tags.md)
>* [Instructions et règles pour entraîner le service de contenu dynamique](smart-tags-training-guidelines.md)

