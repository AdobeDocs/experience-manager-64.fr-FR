---
title: Présentation du site de référence de renouvellement de l’assurance automobile We.Finance
seo-title: We.Finance Auto Insurance Renewal reference site walkthrough
description: Consultez la présentation détaillée du site de référence du cas d’utilisation de l’assurance automobile We.Finance qui présente comment AEM forms et son intégration à Microsoft Dynamics permettent de personnaliser l’expérience client dans une société de services financiers.
seo-description: Read on detailed reference site walkthrough of We.Finance Auto Insurance use case which showcases how AEM forms and its integration with Microsoft Dynamics helps personalize customer experience in a financial service company.
uuid: 18676ab4-9f8d-4014-b751-2a722fd152da
contentOwner: dekalra
topic-tags: introduction
discoiquuid: a960d489-f5a3-436a-b028-54292648c7be
exl-id: db416cbc-27a7-4a2c-b4b3-43e8963faf22
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 92%

---

# Présentation du site de référence de renouvellement de l’assurance automobile We.Finance {#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## Prérequis {#pre-requisites}

Configurez le site de référence comme décrit dans la section [Installation et configuration du site de référence Forms AEM 6.4](/help/forms/using/setup-reference-sites.md).

## Exemple d’utilisation du site de référence We.Finance  {#we-finance-reference-site-scenario}

Le site We.Finance est un site de services financiers conçu pour vous aider à découvrir les fonctionnalités de communications interactives d’AEM Forms.

Lisez la présentation détaillée du cas d’utilisation de l’assurance automobile We.Finance qui explique comment AEM Forms et son intégration à Microsoft Dynamics permettent de personnaliser l’expérience client dans une société de services financiers. La présentation interactive est conçu pour faciliter l’implémentation de transactions numériques complexes et la communication avec les clients dans une société financière.

**La présentation commence par le cas d’utilisation :**

Sarah Rose est déjà cliente chez We.Finance et a acheté une police d’assurance automobile. Elle doit renouveler sa police d’assurance aujourd’hui. Gloria Rios, courtier d’assurance chez We.Finance, envoie un rappel à Sarah concernant le renouvellement de sa police. Sarah suit les instructions figurant dans le courrier électronique et effectue la procédure.

## Présentation de la demande d’assurance automobile {#auto-insurance-application-walkthrough}

Le scénario de l’application à une assurance automobile chez We.Finance est une narration visuelle pour l’utilisateur et met deux personnes en scène :

* Sarah Rose, une cliente chez We.Finance
* Gloria Rios, courtier d’assurance chez We.Finance

### Gloria envoie une notification de renouvellement de police d’assurance à partir de We.Finance {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria se connecte à l’instance AEM, clique sur **Renouvellement de l’assurance automobile**, puis sur **Ouvrir l’interface utilisateur de l’agent.** Le clic préremplit le document d’assurance avec les détails de la police de Sarah Rose. Gloria clique sur **Envoyer** et un message « Envoi en cours » apparaît à l’écran, puis quelques secondes plus tard le message « Envoyé » s’affiche.

Sarah reçoit un e-mail dont l’objet est « Votre renouvellement d’assurance automobile ».

![agent_ui_email](assets/agent_ui_email.png)

#### Démonstration {#see-it-yourself}

Accédez à **Adobe Experience Manager** > **Formulaires** > **Formulaires et documents** > **We.Finance** > **Assurance automobile**. Sélectionnez la **Renouvellement d’assurance automobile** communication interactive et clic **Ouvrir l’interface utilisateur de l’agent**. La communication interactive s’ouvre dans l’interface utilisateur de l’agent. Saisissez une adresse électronique valide pour recevoir un e-mail contenant le document de police joint, puis cliquez sur envoyer.

Vous pouvez accéder à la communication interactive du renouvellement de l’assurance automobile et la consulter directement depuis `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.`.

### Sarah reçoit une notification de renouvellement de police d’assurance de We.Finance et décide d’effectuer le renouvellement. {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah reçoit un e-mail contenant une pièce jointe de We.Finance qui lui rappelle que sa police d’assurance automobile est sur le point d’expirer. La pièce jointe contient la version imprimée de sa lettre d’assurance automobile.

Sarah clique sur **Renouveler maintenant** et est redirigée vers la version web de sa lettre d’assurance automobile. En haut de cette lettre, Sarah trouve le nombre de jours restant avant l’expiration de sa police. La page fournit à Sarah un aperçu de base des détails de sa police d’assurance, tels que le numéro de police, le montant dû et d’autres informations telles que les offres de réduction et les récompenses de fidélité. Sarah clique à nouveau sur **Renouveler maintenant** au bas de la police.

![ref1](assets/ref1.png)

#### Fonctionnement {#how-it-works}

Les versions web et imprimées de votre lettre d’assurance automobile sont créées à l’aide des fonctionnalités multicanales des communications interactives.

Le bouton Renouveler maintenant dans le courrier électronique est lié à la demande de renouvellement d’assurance automobile qui se présente sous forme de communication interactive sur une instance de publication.

#### Démonstration {#see-it-yourself-1}

Vous devriez recevoir un courrier électronique avec un fichier PDF joint. Le fichier PDF est une version imprimée de votre lettre d’assurance automobile. Cliquez sur **Renouveler maintenant** pour accéder à la version web de la police. Vérifiez vos informations personnelles et les détails de la police, puis cliquez sur **Renouveler maintenant** pour être redirigé vers une autre communication interactive.

Le bouton **Renouveler maintenant** figurant dans l’e-mail redirige Sarah vers la version web de la police. Vous pouvez consulter l’URL suivante :

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

Vous pouvez vérifier le résumé détaillé de votre renouvellement d’assurance automobile et cliquer sur **Renouveler maintenant** au bas de la page.

### Sarah accède à la page de paiement {#sarah-reaches-the-payment-page}

We.Finance redirige Sarah vers la page de paiement. Sarah vérifie à nouveau son numéro de police et la date d’expiration dans ses dossiers. Sur le côté droit de la page, elle vérifie le récapitulatif des paiements de son renouvellement avec une réduction de 10 % sur le montant total.

#### Fonctionnement {#how-it-works-1}

Le bouton Renouveler maintenant redirige Sarah vers la page de paiement. La page de paiement est un formulaire adaptatif.

#### Démonstration {#see-it-yourself-2}

Cliquez sur **Renouveler maintenant** pour accéder à la page de paiement. Saisissez vos informations de carte de crédit, puis cliquez sur **Effectuer un paiement.**

Vous pouvez accéder à la page de paiement dans une instance de création à l’adresse suivante :

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah effectue le paiement et termine le processus. {#sarah-makes-the-payment-and-completes-the-process}

Sarah remplit ses informations de carte de crédit et clique sur **Effectuer un paiement**.

#### Fonctionnement {#how-it-works-2}

Lorsque Sarah remplit les informations de carte de crédit et clique sur le bouton Envoyer, son paiement de carte de crédit est traité et un message de remerciement configuré dans le formulaire adaptatif s’affiche à l’écran.

#### Démonstration {#see-it-yourself-3}

Vous pouvez afficher le message de confirmation après avoir cliqué sur Effectuer un paiement à l’adresse suivante :

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
