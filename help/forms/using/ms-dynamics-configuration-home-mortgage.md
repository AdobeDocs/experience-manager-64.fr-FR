---
title: Configuration de Microsoft Dynamics 365 pour le processus de prêt immobilier du site de référence We.Finance
seo-title: Configure Microsoft Dynamics 365 for the home mortgage workflow of the We.Finance reference site
description: Découvrez comment optimiser les services Microsoft® Dynamics 365 via des formulaires adaptatifs pour le processus de prêt immobilier du site de référence We.Finance
seo-description: Learn how to leverage the Microsoft® Dynamics 365 services through adaptive forms for the home mortgage workflow of the We.Finance Reference site
uuid: a0656d90-84c7-46d1-9a16-dadcc19ff9ef
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: develop, Configuration
discoiquuid: 6b31397a-fb06-4043-9368-59fb4fce8afa
exl-id: 7e1f417e-6a6b-4ef2-a453-866331fe3e96
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 97%

---

# Configuration de Microsoft Dynamics 365 pour le processus de prêt immobilier du site de référence We.Finance {#configure-microsoft-dynamics-for-the-home-mortgage-workflow-of-the-we-finance-reference-site}

Découvrez comment optimiser les services Microsoft® Dynamics 365 via des formulaires adaptatifs pour le processus de prêt immobilier du site de référence We.Finance

## Présentation {#overview}

Microsoft® Dynamics 365 est un logiciel de gestion de la relation client (CRM) et de planification des ressources de l’entreprise (ERP) qui fournit des solutions d’entreprise pour la création et la gestion de comptes clients, de contacts, de prospects, d’opportunités et de dossiers.

AEM Forms fournit un service cloud pour intégrer Dynamics 365 au module [Forms Data Integration](/help/forms/using/data-integration.md). Le scénario de la [présentation de l’application de prêt immobilier avec Microsoft® Dynamics](/help/forms/using/finance-reference-site-walkthrough.md#home-mortgage-application-walkthrough-with-microsoft-dynamics) montre comment un client utilise le site de référence We.Finance pour demander un prêt lorsque le site utilise Microsoft® Dynamics pour l’intégration de données de formulaire. Avant de pouvoir utiliser la page d’accueil de l’application de prêt immobilier avec le scénario Microsoft® Dynamics, vous devez configurer Microsoft® Dynamics 365 pour l’utiliser avec le site de référence We.Finance.

## Prérequis {#prerequisites}

Avant de commencer à installer et configurer Dynamics 365, vérifiez que vous avez :

* [Installé et configuré les sites de référence d’AEM Forms](/help/forms/using/setup-reference-sites.md).

* AEM 6.3 Forms Service Pack 1 et versions ultérieures
* Compte Microsoft® Dynamics 365
* Application enregistrée du service Dynamics 365 avec Microsoft® Azure Active Directory
* ID du client et le secret du client pour l’application enregistrée

## Liaison du calculateur de prêt immobilier avec la page d’accueil de votre site {#link-the-home-mortgage-calculator-with-your-site-home-page}

1. Sur une instance d’auteur, accédez à la page suivante :

   https://[sderver]:[port]/editor.html/content/we-finance/global/en/loan-landing-page.html

1. Faites défiler l’écran vers le calculateur de prêt immobilier.
1. Sélectionnez le panneau de la colonne de droite (du calculateur) et appuyez pour afficher le menu contextuel. Dans le menu contextuel, appuyez sur Configurer. La boîte de dialogue Modifier le conteneur d’AEM Forms s’affiche.

   ![calculatorconfigurgurepanel](assets/calculatorconfigurepanel.png)

1. Dans la boîte de dialogue Modifier le conteneur d’AEM Forms, accédez au chemin d’accès à l’actif et sélectionnez le calculateur de prêt immobilier dans chemin suivant, puis appuyez sur **Confirmer** :

   formsanddocuments/We.Finance/MS Dynamics/

   ![selectassetpath](assets/selectassetpath.png)

1. Appuyez sur **Terminé**.
1. Publiez la page modifiée.

   >[!NOTE]
   >
   >La liaison des champs du calculateur avec FDM est préconfigurée via le package du site de référence We.Finance. Pour afficher la liaison, vous pouvez ouvrir le formulaire dans le mode de création et voir les références de liaison de champ.

1. Pour créer une entité personnalisée pour stocker l’enregistrement de demandeur pour une demande de prêt immobilier, importez le package de solution AEMFormsFSIRefsite_1_0.zip sur votre instance Microsoft® Dynamics :

   1. Téléchargez le package à partir de :

      `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`

   1. Importez le package de solution dans une instance de Microsoft® Dynamics. Dans votre instance Microsoft® Dynamics, accédez à **Paramètres** > **Solutions**, puis appuyez sur **Importer**.

1. Pour configurer les coordonnées de l’utilisateur utilisées dans le site de référence, importez le package Sarah Rose Contact.CSV dans votre instance Microsoft® Dynamics :

   1. Téléchargez le package à partir de :

      `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

   1. Importez le package dans votre instance Microsoft® Dynamics. Dans votre instance Microsoft® Dynamics, accédez à **Ventes** > **Contacts**, puis appuyez sur **Importer les données**.
