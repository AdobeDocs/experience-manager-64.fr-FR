---
title: Création de votre premier formulaire adaptatif
seo-title: Create your first adaptive form
description: Apprenez à créer des formulaires professionnels, interactifs et réactifs.
seo-description: Learn to create business class, interactive, and responsive forms.
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
feature: Adaptive Forms
exl-id: f634a73a-e720-4a38-a459-6ddbe4fdc565
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 37%

---

# Création de votre premier formulaire adaptatif {#do-not-publish-create-your-first-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Présentation {#introduction}

Vous recherchez un mobile-friendly **expérience de formulaires** qui permet de simplifier l&#39;enrôlement, d&#39;augmenter l&#39;engagement et de réduire le temps de disponibilité, **formulaires adaptatifs** est parfaite pour vous. Les formulaires adaptatifs offrent une expérience de formulaires adaptée aux analyses, à l’automatisation et aux appareils mobiles. Vous pouvez facilement créer des formulaires réactifs et interactifs, utiliser des processus automatisés pour réduire les tâches administratives et répétitives et utiliser l’analyse des données pour améliorer et personnaliser l’expérience des clients avec vos formulaires.

Ce tutoriel fournit une structure de bout en bout pour créer un formulaire adaptatif. Le tutoriel est organisé en cas d’utilisation et en plusieurs guides. Chaque guide vous aide à apprendre et à ajouter de nouvelles fonctionnalités au formulaire adaptatif créé dans ce tutoriel. Vous disposez d’un formulaire adaptatif fonctionnel après chaque guide. Le guide de création d’un formulaire adaptatif est disponible. Les guides suivants seront bientôt disponibles. À la fin de ce didacticiel, vous serez capable de :

* Créez un formulaire adaptatif et un modèle de données de formulaire.
* Mettez en forme votre formulaire adaptatif.
* Utilisez l’éditeur de règles de formulaire adaptatif pour créer des règles de fonctionnement.
* Testez et publiez un formulaire adaptatif.

![create-adaptive-form-workflow](assets/create-daptive-form-workflow.png)

Le parcours commence par l’apprentissage du cas pratique :

Un site web propose une gamme de produits pour différents clients. Les clients parcourent le portail, sélectionnent et commandent les produits. Chaque client crée un compte et fournit des adresses de livraison et de facturation. Une cliente, Sara Rose, cherche à ajouter son adresse de livraison sur le site web. Le site Web fournit un formulaire en ligne pour ajouter et mettre à jour les adresses de livraison.

Le site web s’exécute sur Adobe Experience Manager (AEM) et utilise AEM Forms pour la capture et le traitement des données. Le formulaire d’ajout et de mise à jour d’adresse est un formulaire adaptatif. Le site web stocke les détails du client dans une base de données. Il utilise le formulaire d’ajout et de mise à jour d’adresse pour récupérer et afficher les adresses disponibles. Ils utilisent également le formulaire adaptatif pour accepter les adresses mises à jour et nouvelles.

### Prérequis {#prerequisite}

* Configurez une instance d’auteur AEM.
* Installez le [module complémentaire AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) sur une instance de création.
* Obtenez le pilote de base de données JDBC (fichier JAR) auprès du fournisseur de base de données. Les exemples du tutoriel sont basés sur la base de données MySQL et utilisent le [pilote de base de données MySQL JDBC](https://dev.mysql.com/downloads/connector/j/5.1.html) d’Oracle.

* Configurez une base de données contenant les données client avec les champs affichés ci-dessous. Une base de données n’est pas essentielle pour créer un formulaire adaptatif. Ce tutoriel utilise une base de données pour afficher le modèle de données de formulaire et les fonctionnalités de persistance d’AEM Forms.

![adaptiveformdata](assets/adaptiveformdata.png)

## Étape 1 : création d’un formulaire adaptatif {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

Les formulaires adaptatifs sont de nouvelle génération, attrayants, réactifs, dynamiques et adaptatifs par nature. Les formulaires adaptatifs vous permettent de proposer des expériences personnalisées et ciblées. AEM Forms fournit un éditeur WYSIWYG par glisser-déposer pour créer des formulaires adaptatifs. Pour plus d’informations sur les formulaires adaptatifs, voir [Présentation de la création de formulaires adaptatifs](/help/forms/using/introduction-forms-authoring.md).

Objectifs:

* Créer un formulaire adaptatif permettant à un(e) client(e) d’ajouter une adresse de livraison
* Mettre en forme les champs d’un formulaire adaptatif pour afficher et accepter les informations d’un(e) client(e)
* Créer une action d’envoi pour envoyer un courrier électronique contenant du contenu de formulaire
* Prévisualiser et envoyer un formulaire adaptatif

[ ](create-adaptive-form.md)

## Étape 2 : création d’un modèle de données de formulaire {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Un modèle de données de formulaire permet de connecter un formulaire adaptatif à des sources de données disparates. Par exemple, AEM profil utilisateur, services Web RESTful, services Web SOAP, services OData et bases de données relationnelles. Un modèle de données de formulaire est un schéma de représentation de données unifié des entités commerciales et des services disponibles dans les sources de données connectées. Vous pouvez utiliser le modèle de données de formulaire avec un formulaire adaptatif pour récupérer, mettre à jour, supprimer et ajouter des données aux sources de données connectées.

Objectifs:

* Configurer l’instance de base de données du site web (base de données MySQL) en tant que sources de données
* Créer un modèle de données de formulaire à l’aide de la base de données MySQL comme source de données
* Ajouter des objets de modèle de données pour former un modèle de données
* Configurer les services de lecture et d’écriture pour le modèle de données de formulaire
* Tester le modèle de données de formulaire et les services configurés avec des données de test

[ ](create-form-data-model.md)

## Étape 3 : application de règles aux champs de formulaires adaptatifs {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Les formulaires adaptatifs fournissent un éditeur pour l’écriture de règles sur des objets de formulaire adaptatifs. Ces règles déterminent les actions à déclencher sur des objets de formulaire en fonction des conditions prédéfinies, des entrées de l’utilisateur et des actions de l’utilisateur sur le formulaire. Cela permet d’assurer la précision et accélère le remplissage des formulaires.

Objectifs:

* Créer et appliquer des règles aux champs de formulaire adaptatif
* Utiliser des règles pour déclencher des services de modèle de données de formulaire pour mettre à jour les données dans la base de données

## Étape 4 : appliquer un style à votre formulaire adaptatif {#step-style-your-adaptive-form}

![09-Style-your-adaptive-form_small](assets/09-Style-your-adaptive-form_small.png)

Les formulaires adaptatifs comportent des thèmes et un [éditeur](/help/forms/using/themes.md) permettant de créer des thèmes pour les formulaires adaptatifs. Un thème contient des détails de style pour les composants et les panneaux, et vous pouvez réutiliser un thème dans différents formulaires. Ces styles incluent les propriétés telles que les couleurs d’arrière-plan, les couleurs d’état, la transparence, l’alignement et la taille. Lorsque vous appliquez le thème à votre formulaire, le style spécifié se reflète sur les composants correspondants de votre formulaire. Les formulaires adaptatifs prennent également en charge le style en ligne pour les styles spécifiques à un formulaire.

Objectifs:

* Application d’un thème prêt à l’emploi à un formulaire adaptatif
* Création d’un thème pour le formulaire adaptatif à l’aide de l’éditeur de thème
* Utiliser des polices web dans un thème personnalisé

[ ](style-your-adaptive-form.md)

## Étape 5 : test de votre formulaire adaptatif {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

Les formulaires adaptatifs font partie intégrante de vos interactions avec les clients. Il est important de tester vos formulaires adaptatifs à chaque modification apportée. Tester tous les champs d’un formulaire est fastidieux. AEM Forms fournit un SDK (Calvin SDK) pour automatiser le test des formulaires adaptatifs. Calvin vous permet d’automatiser les tests de vos formulaires adaptatifs dans le navigateur Web.

Objectifs:

* Installation du SDK Calvin
* Créer une suite de tests et des cas de test pour modifier le formulaire d’adresse

Pour en savoir plus sur le SDK, voir [Utilisation de tests automatisés avec AEM formulaire adaptatif](/help/forms/using/calvin.md).

## Étape 6: publication de votre formulaire adaptatif {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Vous pouvez publier des formulaires adaptatifs en tant que formulaire autonome (application d’une seule page), à inclure dans AEM [page de sites](/help/forms/using/embed-adaptive-form-aem-sites.md)ou répertoriez sur un site AEM à l’aide de [Portail Forms](/help/forms/using/introduction-publishing-forms.md).

Objectifs :

* Publier le formulaire adaptatif en tant qu’application d’une seule page
