---
title: Configurer les sources de données
seo-title: Configurer les sources de données
description: Découvrez comment configurer différents types de sources de données et tirer parti de la création de modèles de données de formulaire.
seo-description: Découvrez comment configurer différents types de sources de données et tirer parti de la création de modèles de données de formulaire.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 64%

---


# Configurer les sources de données {#configure-data-sources}

Découvrez comment configurer différents types de sources de données et tirer parti de la création de modèles de données de formulaire.

![](do-not-localize/data-integeration.png)

L’intégration de données AEM Forms permet de configurer des sources de données disparates et de s’y connecter. La prise en charge est assurée par défaut pour les types suivants. Toutefois, avec peu de personnalisation, vous pouvez intégrer d’autres sources de données.

* Bases de données relationnelles : MySQL, Microsoft SQL Server, IBM DB2 et Oracle RDBMS
* Profil utilisateur AEM
* Services web RESTful
* Services web SOAP
* Services OData

L’intégration des données prend en charge OAuth2.0, l’authentification de base et les types d’authentification de clé d’API prêts à l’emploi et permet l’implémentation de l’authentification personnalisée pour l’accès aux services Web. Alors que les services RESTful, SOAP et OData sont configurés dans les services cloud AEM, JDBC pour les bases de données relationnelles et Connector pour le profil utilisateur AEM sont configurés dans la console Web AEM.

## Configurer la base de données relationnelle {#configure-relational-database}

Vous pouvez configurer des bases de données relationnelles à l’aide de la configuration de la console Web AEM. Procédez comme suit :

1. Accédez à AEM console Web à l’adresse `https://[server]:[host]/system/console/configMgr`.
1. Recherchez la configuration **[!UICONTROL Apache Sling Connection Pooled DataSource]**. Appuyez pour ouvrir la configuration en mode édition.
1. Dans la boîte de dialogue de configuration, spécifiez les détails de la base de données que vous souhaitez configurer, tels que :

   * Nom de la source de données
   * Propriété de service de source de données qui stocke le nom de la source de données
   * Nom de classe Java pour le pilote JDBC
   * URI de connexion JDBC
   * Nom d’utilisateur et mot de passe pour établir la connexion avec le pilote JDBC

   >[!NOTE]
   >
   >Veillez à chiffrer les informations sensibles telles que les mots de passe avant de configurer la source de données. Pour chiffrer :
   >
   >1. Accédez à `https://[server]:[port]/system/console/crypto`.
   >1. Dans le champ **[!UICONTROL Texte brut]**, spécifiez le mot de passe ou toute chaîne à chiffrer et cliquez sur **[!UICONTROL Protéger]**.

   >
   >Le texte chiffré apparaît dans le champ Texte protégé que vous pouvez spécifier dans la configuration.

1. Activer **[!UICONTROL Test lors de l’emprunt]** ou **[!UICONTROL Test lors du renvoi]** pour spécifier que les objets sont validés avant d’être empruntés ou retournés depuis et vers le pool, respectivement.
1. Spécifiez une requête SQL SELECT dans le champ **[!UICONTROL Requête de validation]** pour valider les connexions du pool. La requête doit renvoyer au moins une ligne. En fonction de votre base de données, définissez l’une des options suivantes :

   * SELECT 1 (MySQL et MS SQL)
   * SELECT 1 from dual (Oracle)

1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer la configuration.

## Configurer le profil utilisateur AEM {#configure-aem-user-profile}

Vous pouvez configurer le profil utilisateur AEM à l’aide de la configuration User Profile Connector dans AEM Web Console. Procédez comme suit :

1. Accédez à AEM console Web à l’adresse `https://[server]:[host]/system/console/configMgr`.
1. Recherchez **[!UICONTROL AEM Forms Data Integrations - User Profil Connector Configuration]** et appuyez sur pour ouvrir la configuration en mode d’édition.
1. Dans la boîte de dialogue Configuration du connecteur de profil utilisateur, vous pouvez ajouter, supprimer ou mettre à jour les propriétés du profil utilisateur. Les propriétés spécifiées pourront être utilisées dans le modèle de données de formulaire. Utilisez le format suivant pour spécifier les propriétés du profil utilisateur :

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Exemples :

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >Dans l’exemple ci-dessus, **&amp;ast;** indique tous les noeuds situés sous le noeud `profile/empLocation/` dans AEM profil utilisateur de la structure CRXDE. Cela signifie que le modèle de données de formulaire peut accéder à la propriété `city` de type `string` présente dans tout noeud sous le noeud `profile/empLocation/`. Toutefois, les nœuds qui contiennent la propriété spécifiée doivent suivre une structure cohérente.

1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer la configuration.

## Configuration du dossier pour les configurations de service cloud {#cloud-folder}

>[!NOTE]
>
>La configuration du dossier des services cloud est requise pour la configuration des services cloud pour les services RESTful, SOAP et OData.

Toutes les configurations de service cloud dans AEM sont consolidées dans le dossier `/conf` du référentiel AEM. Par défaut, le dossier `conf` contient le dossier `global` dans lequel vous pouvez créer des configurations de service cloud. Toutefois, vous devez l’activer manuellement pour les configurations cloud. Vous pouvez également créer des dossiers supplémentaires dans `conf` pour créer et organiser des configurations de service cloud.

Pour configurer le dossier pour les configurations de service cloud :

1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   * Pour plus d’informations, consultez la [documentation du navigateur de configuration](/help/sites-administering/configurations.md).
1. Procédez comme suit pour activer le dossier global pour les configurations cloud ou ignorez cette étape pour créer et configurer un autre dossier pour les configurations de service cloud.

   1. Dans le **[!UICONTROL navigateur de configuration]**, sélectionnez le dossier `global` et appuyez sur **[!UICONTROL Propriétés]**.
   1. Dans la boîte de dialogue **[!UICONTROL Propriétés de configuration]**, activez **[!UICONTROL Configurations cloud]**.
   1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Dans le **[!UICONTROL navigateur de configuration]**, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un titre pour le dossier et activez **[!UICONTROL Configurations cloud]**.
1. Appuyez sur **[!UICONTROL Créer]** pour créer le dossier activé pour les configurations de service cloud.

## Configurer les services Web RESTful {#configure-restful-web-services}

Le service Web RESTful peut être décrit en utilisant [les spécifications Swagger](https://swagger.io/specification/) au format JSON ou YAML dans un fichier de définition Swagger. Pour configurer le service Web RESTful dans les services cloud AEM, assurez-vous que le fichier Swagger est présent dans votre système de fichiers ou l’URL où le fichier est hébergé.

Procédez comme suit pour configurer les services RESTful :

1. Accédez à **[!UICONTROL Outils > Services cloud > Sources de données]**. Appuyez sur pour sélectionner le dossier dans lequel vous souhaitez créer une configuration de cloud.

   Voir [Configuration d’un dossier pour les configurations de service cloud](/help/forms/using/configure-data-sources.md#cloud-folder) pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud.

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir la boîte de dialogue **[!UICONTROL Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service RESTful]** dans la liste déroulante **[!UICONTROL Type de service]**, recherchez et sélectionnez éventuellement une image miniature pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les informations suivantes pour le service RESTful :

   * Sélectionnez l’URL ou le fichier dans la liste déroulante Source Swagger et spécifiez l’URL Swagger du fichier de définition Swagger ou chargez le fichier Swagger à partir de votre système de fichiers local.
   * Sélectionnez le type d’authentification — Aucun, OAuth2.0, Authentification de base, Clé d’API ou Authentification personnalisée — pour accéder au service RESTful et, par conséquent, fournir des détails pour l’authentification.

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration cloud pour le service RESTful.

## Configurer les services Web SOAP {#configure-soap-web-services}

Les services Web basés sur SOAP sont décrits à l’aide des [spécifications WSDL (Web Services Description Language).](https://www.w3.org/TR/wsdl) Pour configurer le service Web SOAP dans les services cloud AEM, vérifiez que vous disposez de l’URL WSDL pour le service Web et procédez comme suit :

1. Accédez à **[!UICONTROL Outils > Services cloud > Sources de données]**. Appuyez sur pour sélectionner le dossier dans lequel vous souhaitez créer une configuration de cloud.

   Voir [Configuration d’un dossier pour les configurations de service cloud](/help/forms/using/configure-data-sources.md#cloud-folder) pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud.

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir la boîte de dialogue **[!UICONTROL Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service Web SOAP]** dans la liste déroulante **[!UICONTROL Type de service]**, sélectionnez et sélectionnez une image miniature pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les éléments suivants pour le service Web SOAP :

   * URL WSDL pour le service Web.
   * Point de fin du service. Spécifiez une valeur dans ce champ pour remplacer le point de terminaison de service mentionné dans WSDL.
   * Sélectionnez le type d’authentification — Aucun, OAuth2.0, Authentification de base, Authentification personnalisée ou Jeton X509 — pour accéder au service SOAP et, par conséquent, fournir les détails de l’authentification.

      Si vous sélectionnez Jeton X509 comme type d’authentification, configurez le certificat X509. Pour plus d’informations, voir [Configuration des certificats](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Spécifiez l’alias KeyStore pour le certificat X509 dans le champ **[!UICONTROL Alias de clé]**. Spécifiez la durée, en secondes, jusqu’à ce que la demande d’authentification reste valide, dans le champ **[!UICONTROL Durée de vie]**. Vous pouvez également choisir de signer le corps du message ou l’en-tête d’horodatage ou les deux.

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration cloud pour le service Web SOAP.

## Configurer les services OData {#config-odata}

Un service OData est identifié par son URL racine de service. Pour configurer un service OData dans les services cloud AEM, vérifiez que vous disposez de l’URL racine du service et procédez comme suit :

>[!NOTE]
>
>Pour obtenir un guide pas à pas sur la configuration de Microsoft Dynamics 365, en ligne ou sur site, voir [Configuration OData de Microsoft Dynamics](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Accédez à **[!UICONTROL Outils > Services cloud > Sources de données]**. Appuyez sur pour sélectionner le dossier dans lequel vous souhaitez créer une configuration de cloud.

   Voir [Configuration d’un dossier pour les configurations de service cloud](/help/forms/using/configure-data-sources.md#cloud-folder) pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud.

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir la boîte de dialogue **[!UICONTROL Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service OData]** dans la liste déroulante **[!UICONTROL Type de service]**, recherchez et sélectionnez éventuellement une image miniature pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les informations suivantes pour le service OData :

   * URL racine du service pour le service OData à configurer.
   * Sélectionnez le type d’authentification — Aucun, OAuth2.0, Authentification de base ou Authentification personnalisée — pour accéder au service OData et, par conséquent, fournir les détails de l’authentification.

   >[!NOTE]
   >
   >Vous devez sélectionner le type d’authentification OAuth 2.0 pour vous connecter aux services Microsoft Dynamics à l’aide du point de terminaison OData en tant que racine du service.

1. Appuyez sur **Créer** pour créer la configuration de cloud pour le service OData.

## Étapes suivantes {#next-steps}

Vous avez configuré la source de données. Vous pouvez ensuite créer un modèle de données de formulaire ou, si vous avez déjà créé un modèle de données de formulaire sans source de données, vous pouvez l’associer aux sources de données que vous venez de configurer. Voir [Création d’un modèle de données de formulaire](/help/forms/using/create-form-data-models.md) pour plus d’informations.
