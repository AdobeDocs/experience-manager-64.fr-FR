---
title: "Didacticiel\_: créer un modèle de données de formulaire "
seo-title: Create Form Data Model Tutorial
description: Le module d’intégration de données AEM Forms vous permet de créer un modèle de données de formulaire à partir de sources de données tierces telles que le profil utilisateur AEM, les services web RESTful, les services web basés sur SOAP, les services OData et les bases de données relationnelles. Découvrez comment configurer la base de données MySQL comme source de données, créer, configurer et tester un modèle de données de formulaire.
seo-description: AEM Forms data integration module allows you to create a form data model from disparate backend data sources such as AEM user profile, RESTful web services, SOAP-based web services, OData services, and relational databases. Learn how to configure MySQL database as data source, create, configure, and test a form data model.
page-status-flag: de-activated
uuid: 81d40278-4df9-4b61-93ad-eae2fce0a35c
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 31e97723-d637-4a18-999d-36e00fbd031a
feature: Adaptive Forms
exl-id: 2f83e853-2468-4ea2-85f6-8cf7fe9de6a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 53%

---

# Didacticiel : créer un modèle de données de formulaire  {#tutorial-create-form-data-model}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Ce tutoriel est une étape dans la [Créer votre premier formulaire adaptatif](/help/forms/using/create-your-first-adaptive-form.md) série. Il est recommandé de suivre la série dans un ordre chronologique pour comprendre, exécuter et démontrer le cas d’utilisation complet du tutoriel.

## À propos du tutoriel {#about-the-tutorial}

Le module d’intégration de données AEM Forms vous permet de créer un modèle de données de formulaire à partir de sources de données tierces telles que le profil utilisateur AEM, les services web RESTful, les services web basés sur SOAP, les services OData et les bases de données relationnelles. Vous pouvez configurer des objets et des services de modèle de données dans un modèle de données de formulaire et les associer à un formulaire adaptatif. Les champs de formulaire adaptatif sont liés aux propriétés de l’objet de modèle de données. Les services vous permettent de préremplir le formulaire adaptatif et d’écrire les données de formulaire envoyées dans l’objet de modèle de données.

Pour plus d’informations sur l’intégration des données de formulaire et sur le modèle de données du formulaire, voir [Intégration de données AEM Forms](/help/forms/using/data-integration.md).

Ce tutoriel vous guide tout au long des étapes nécessaires à la préparation, la création, la configuration et l’association d’un modèle de données de formulaire à un formulaire adaptatif. À la fin de ce didacticiel, vous serez capable de :

* [Configurer la base de données MySQL comme source de données](#config-database)
* [Créer un modèle de données de formulaire à l’aide de la base de données MySQL](#create-fdm)
* [Configurer un modèle de données de formulaire](#config-fdm)
* [Tester le modèle de données de formulaire](#test-fdm)

Le modèle de données de formulaire se présentera comme ceci :

![form-data-model_l](assets/form-data-model_l.png)

**A.** Sources de données configurées **B.** Schémas de sources de données **C.** Services disponibles **D.** Objets de modèle de données **E.** Services configurés

## Prérequis {#prerequisites}

Avant de commencer, assurez-vous que vous disposez des éléments suivants :

* Base de données MySQL avec des exemples de données, comme indiqué dans la section Prérequis de [Créer votre premier formulaire adaptatif](/help/forms/using/create-your-first-adaptive-form.md)
* Lot OSGi pour le pilote JDBC MySQL, comme expliqué dans la section [Regrouper le pilote de base de données JDBC](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver).
* Formulaire adaptatif, comme expliqué dans le tout premier didacticiel de mise en route [Créer un formulaire adaptatif](/help/forms/using/create-adaptive-form.md).

## Étape 1 : Configuration de la base de données MySQL comme source de données {#config-database}

Vous pouvez configurer différents types de sources de données pour créer un modèle de données de formulaire. Pour ce tutoriel, nous allons configurer la base de données MySQL que vous avez configurée et remplie avec des exemples de données. Pour plus d’informations sur les autres sources de données prises en charge et sur leur configuration, voir [Intégration de données AEM Forms](/help/forms/using/data-integration.md).

Procédez comme suit pour configurer votre base de données MySQL :

1. Installez le pilote JDBC pour la base de données MySQL en tant que lot OSGi :

   1. Connectez-vous à l’instance d’auteur AEM Forms en tant qu’administrateur et accédez aux bundles de la console web d’AEM. L’URL par défaut est [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

   1. Cliquez sur **Installer/Mettre à jour**. Une boîte de dialogue **Télécharger/installer les bundles** s’affiche.

   1. Appuyez sur **Choisir un fichier** pour rechercher et sélectionner le bundle OSGi du pilote JDBC MySQL. Sélectionnez les cases à cocher **Démarrer le bundle** et **Actualiser les packages** et cliquez sur **Installer ou mettre à jour**. Assurez-vous que le pilote JDBC de Oracle Corporation pour MySQL est principal. Le pilote est installé.

1. Configurer la base de données MySQL comme source de données :

   1. Accédez à AEM console web à l’adresse [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
   1. Recherchez la configuration **Apache Sling Connection Pooled DataSource**. Appuyez pour ouvrir la configuration en mode édition.
   1. Dans la boîte de dialogue de configuration, spécifiez les détails suivants :

      * **Nom de la source de données :** Vous pouvez spécifier n’importe quel nom. Spécifiez par exemple **WeRetailMySQL**.
      * **Nom de la propriété du service DataSource**: Indiquez le nom de la propriété de service contenant le nom DataSource. Il est spécifié lors de l’enregistrement de l’instance de source de données en tant que service OSGi. Par exemple : **datasource.name**.
      * **Classe de pilote JDBC**: Spécifiez le nom de classe Java du pilote JDBC. Pour la base de données MySQL, spécifiez **com.mysql.jdbc.Driver**.
      * **URI de connexion JDBC** : spécifiez l’URL de connexion de la base de données. Pour la base de données MySQL s’exécutant sur le port 3306 et le schéma weretail, l’URL est la suivante : `jdbc:mysql://[server]:3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **Nom d’utilisateur :** nom d’utilisateur de la base de données. Il est nécessaire d’activer le pilote JDBC pour établir une connexion avec la base de données.
      * **Mot de passe :** mot de passe de la base de données. Il est nécessaire d’activer le pilote JDBC pour établir une connexion avec la base de données.
      * **Test lors de l’emprunt :** activez l’option **Test lors de l’emprunt.**
      * **Test lors du renvoi :** activez l’option **Test lors du renvoi.**
      * **Requête de validation :** Spécifiez une requête SQL SELECT pour valider les connexions à partir du pool. La requête doit renvoyer au moins une ligne. Par exemple : **select &amp;ast; de customerdetails**.
      * **Isolation de transaction** : définissez la valeur sur **READ_COMMITTED**.

      Laissez les [valeurs](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) par défaut des autres propriétés et cliquez sur **Enregistrer**.
   Une configuration similaire à la suivante est créée.

   ![relational-database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Étape 2 : Créer un modèle de données de formulaire {#create-fdm}

AEM Forms fournit une interface utilisateur intuitive à [création d’un modèle de données de formulaire](data-integration.md) à partir de sources de données configurées. Vous pouvez utiliser plusieurs sources de données dans un modèle de données de formulaire. Pour notre cas d’utilisation, nous utiliserons la source de données MySQL configurée.

Procédez comme suit pour créer un modèle de données de formulaire :

1. Dans AEM instance d’auteur, accédez à **Forms** >  **Intégration de données** s.
1. Appuyez sur **Create** (Créer) > **Form Data Model** (Modèle de données de formulaire).
1. Dans la boîte de dialogue Créer un modèle de données de formulaire, spécifiez un **nom** pour le modèle de données de formulaire. Par exemple, **customer-shipping-billing-details**. Appuyez sur **Suivant**.
1. L’écran Sélectionner la source de données répertorie toutes les sources de données configurées. Sélectionnez la source de données **WeRetailMySQL** et cliquez sur **Créer**.

   ![data-source-selection](assets/data-source-selection.png)

Le modèle de données de formulaire **customer-shipping-billing-details** est créé.

## Étape 3 : Configuration du modèle de données de formulaire {#config-fdm}

La configuration du modèle de données de formulaire implique :

* L’ajout d’objets et de services de modèle de données
* configuration des services de lecture et d’écriture pour les objets de modèle de données

Procédez comme suit pour configurer le modèle de données de formulaire :

1. Dans l’instance d’auteur AEM, accédez à **Formulaires > Intégrations de données**. L’URL par défaut est [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. Le modèle de données de formulaire **customer-shipping-billing-details** que vous avez créé précédemment est répertorié ici. Ouvrez-le en mode d’édition.

   La source de données sélectionnée **WeRetailMySQL** est configuré dans le modèle de données de formulaire.

   ![default-fdm](assets/default-fdm.png)

1. Développez l’arborescence de la source de données WeRailMySQL. Sélectionnez les objets et services de modèle de données suivants dans le schéma **weretail** > **customerdetails** du modèle de données de formulaire :

   * **Objets de modèle de données**:

      * id
      * name
      * shippingAddress
      * ville
      * state
      * code postal
   * **Services:**

      * get
      * mise à jour

   Appuyer **Ajouter la sélection** pour ajouter des objets et des services de modèle de données sélectionnés au modèle de données de formulaire.

   ![weretail-schema](assets/weretail-schema.png)

   >[!NOTE]
   >
   >Les services par défaut d’obtention, de mise à jour et d’insertion des sources de données JDBC sont intégrés au modèle de données de formulaire.

1. Configurez les services de lecture et d’écriture pour l’objet de modèle de données.

   1. Sélectionnez la **customerdetails** objet de modèle de données et appuyez sur **Modifier les propriétés**.
   1. Sélectionnez **get** dans la liste déroulante Service de lecture. L’argument **id** qui est la clé principale de l’objet de modèle de données customerdetails est ajouté automatiquement. Cliquez sur ![aem_6_3_edit](assets/aem_6_3_edit.png) et configurez l’argument comme suit.

      ![read-default](assets/read-default.png)

   1. De même, sélectionnez **update** comme service d’écriture. Le **customerdetails** est automatiquement ajouté en tant qu’argument. L’argument est configuré comme suit.

      ![write-default](assets/write-default.png)

      Ajoutez et configurez l’argument **id** comme suit.

      ![id-arg](assets/id-arg.png)

   1. Appuyez sur **Terminé** pour enregistrer les propriétés de l’objet de modèle de données. Cliquez ensuite sur **Enregistrer** pour enregistrer le modèle de données de formulaire.

      Les services **get** et **update** sont ajoutés en tant que services par défaut pour l’objet de modèle de données.

      ![data-model-object](assets/data-model-object.png)

1. Accédez à l’onglet **Services** et configurez les services **get** et **update**.

   1. Sélectionnez le service **get** et cliquez sur **Modifier les propriétés**. La boîte de dialogue Propriétés s’ouvre.
   1. Spécifiez les éléments suivants dans la boîte de dialogue Modifier les propriétés :

      * **Titre**: Indiquez le titre du service. Par exemple : Récupérez l’adresse d’expédition.
      * **Description**: Spécifiez la description contenant le fonctionnement détaillé du service. Par exemple :

         Ce service récupère l’adresse de livraison et les autres détails du client de la base de données MySQL.

      * **Objet de modèle de sortie** : sélectionnez le schéma contenant les données du client. Par exemple :

         schéma customerdetail
      * **Tableau de retour**: Désactivez le **Tableau de retour** .
      * **Arguments**: Sélectionner l’argument nommé **ID**.

      Appuyez sur **Terminé**. Le service de récupération des détails des clients de la base de données MySQL est configuré.

      ![shiiping-address-retrieval](assets/shiiping-address-retrieval.png)

   1. Sélectionnez le service **update** et cliquez sur **Modifier les propriétés**. La boîte de dialogue Propriétés s’ouvre.

   1. Spécifiez les éléments suivants dans la boîte de dialogue Modifier les propriétés :

      * **Titre**: Indiquez le titre du service. Par exemple, Mettre à jour l’adresse de livraison.

      * **Description**: Spécifiez la description contenant le fonctionnement détaillé du service. Par exemple :

         Ce service met à jour l’adresse de livraison et les champs associés dans la base de données MySQL.

      * **Objet de modèle d’entrée** : sélectionnez le schéma contenant les données du client. Par exemple :

         schéma customerdetail

      * **Type de sortie** : sélectionnez **VALEUR BOOLEENNE**.
      * **Arguments** : sélectionnez l’argument nommé **ID** et **customerdetails**.

      Appuyez sur **Terminé**. Le **update** Le service permettant de mettre à jour les détails du client dans la base de données MySQL est configuré.

      ![shiiping-address-update](assets/shiiping-address-update.png)



L’objet de modèle de données et les services du modèle de données de formulaire sont configurés. Vous pouvez maintenant tester le modèle de données de formulaire.

## Étape 4 : Tester le modèle de données de formulaire {#test-fdm}

Vous pouvez tester les objets et services de modèle de données pour vérifier si le modèle de données de formulaire est correctement configuré.

Procédez comme suit pour effectuer le test :

1. Accédez au **Modèle** , sélectionnez la variable **customerdetails** objet de modèle de données, puis appuyez sur **Objet de modèle de test**.
1. Dans la fenêtre **Tester le modèle/service**, sélectionnez **Objet de modèle de lecture** dans le menu déroulant **Sélectionner le modèle/service**.
1. Dans le **customerdetails** , indiquez une valeur pour la variable **id** argument existant dans la base de données MySQL configurée et appuyez sur **Test**.

   Les détails du client associés à l’ID spécifié sont récupérés et affichés dans la section **Sortie**, comme indiqué ci-dessous.

   ![test-read-model](assets/test-read-model.png)

1. De même, vous pouvez tester l’objet et les services de modèle Write .

   Dans l’exemple suivant, le service update met à jour avec succès les détails de l’adresse de l’ID 7102715 dans la base de données.

   ![test-write-model](assets/test-write-model.png)

   À présent, si vous testez à nouveau le service de lecture de modèle pour l’ID 7107215, il récupérera et affichera les détails du client mis à jour comme indiqué ci-dessous.

   ![read-updated](assets/read-updated.png)
