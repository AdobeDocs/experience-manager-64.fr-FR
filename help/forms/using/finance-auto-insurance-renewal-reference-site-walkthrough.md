---
title: Présentation du site de référence de renouvellement de l’assurance automobile We.Finance
seo-title: Présentation du site de référence de renouvellement de l’assurance automobile We.Finance
description: 'null'
seo-description: 'null'
uuid: 18676ab4-9f8d-4014-b751-2a722fd152da
contentOwner: dekalra
topic-tags: introduction
discoiquuid: a960d489-f5a3-436a-b028-54292648c7be
translation-type: tm+mt
source-git-commit: 4466161992d877b17d43fe73e3298dd6252733c0

---


# Présentation du site de référence de renouvellement de l’assurance automobile We.Finance {#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## Conditions préalables {#pre-requisites}

Setup the reference site as described in [Setup and configure AEM 6.4 Forms Reference Site](/help/forms/using/setup-reference-sites.md).

## Exemple d’utilisation du site de référence We.Finance  {#we-finance-reference-site-scenario}

Le site Web We.Finance est un site de services financiers conçu pour vous aider à apprendre les fonctionnalités de communication interactive d’AEM Forms.

Lisez la présentation détaillée du cas d&#39;utilisation de l&#39;assurance auto de We.Finance qui montre comment AEM forms et son intégration à Microsoft Dynamics permettent de personnaliser l&#39;expérience client dans une société de services financiers. La présentation interactive est conçue pour faciliter la mise en oeuvre de transactions numériques complexes et la communication client dans une société financière.

**La présentation commence par le cas d’utilisation :**

Sarah Rose est déjà cliente chez We.Finance et a acheté une police d’assurance automobile. Elle doit renouveler sa police d’assurance aujourd’hui. Gloria Rios, courtier d’assurance chez We.Finance, envoie un rappel à Sarah concernant le renouvellement de sa police. Sarah suit les instructions figurant dans le courrier électronique et effectue la procédure.

## Présentation de la demande d’assurance automobile {#auto-insurance-application-walkthrough}

Le scénario de l’application d’assurance automatique We.Finance est une narration visuelle pour l’utilisateur et repose sur deux personnages :

* Sarah Rose, une cliente chez We.Finance
* Gloria Rios, courtier d’assurance chez We.Finance

### Gloria envoie une notification de renouvellement de police d’assurance à partir de We.Finance {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria logs into AEM instance, clicks **Auto Insurance Renewal,** and then clicks **Open Agent UI.** Le clic préremplit le document d’assurance avec les détails de la stratégie de Sarah Rose. Gloria clicks **Submit** and a message is displayed on the screen “Submission Initiated” and then in few seconds “Submitted Successfully”.

Sarah reçoit un courrier électronique contenant le sujet &quot;Votre renouvellement d’assurance automobile&quot;.

![agent_ui_email](assets/agent_ui_email.png)

#### Démonstration {#see-it-yourself}

Go to **Adobe Experience Manager** > **Forms** > **Forms &amp; Documents** > **We.Finance** > **Auto Insurance**. Select the **Auto Insurance Renewal** interactive communication and click **Open Agent UI**. La communication interactive s’ouvre dans l’interface utilisateur de l’agent. Entrez une adresse électronique valide pour recevoir le courrier électronique contenant le document de stratégie joint, puis cliquez sur Envoyer.

Vous pouvez accéder à la communication interactive Renouvellement d&#39;assurance et la consulter directement à partir de `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.`

### Sarah reçoit une notification de renouvellement de police d’assurance de We.Finance et décide d’effectuer le renouvellement.{#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah reçoit un e-mail avec une pièce jointe de We.Finance qui lui rappelle que sa police d’assurance auto est sur le point d’expirer. La pièce jointe est la version imprimée de sa lettre d&#39;assurance auto.

Sarah clicks **Renew Now** and is directed to the web version of her Auto Insurance letter. En plus de cette lettre, Sarah trouve le nombre de jours restants avant l’expiration de sa stratégie. La page fournit à Sarah un aperçu de base des détails de sa police d’assurance, tels que le numéro de police, le montant dû et d’autres informations, telles que les offres de remise et les récompenses de fidélité. Sarah again clicks **Renew Now** at the bottom of the policy.

![ref1](assets/ref1.png)

#### Fonctionnement {#how-it-works}

La sortie Web et imprimée de votre lettre d&#39;assurance auto sont créées à l&#39;aide des fonctionnalités multicanaux d&#39;Interactive Communications.

Le bouton Renouveler maintenant dans le courrier électronique est lié à la demande de renouvellement d’assurance automobile qui se présente sous forme de communication interactive sur une instance de publication.

#### Démonstration {#see-it-yourself-1}

Vous devriez recevoir un courrier électronique avec un fichier PDF joint. Le PDF est une version imprimée de votre lettre d&#39;assurance auto. Click **Renew Now** to reach to the web version of the policy. Check your personal information and policy details and click **Renew Now** which takes you to another Interactive Communication.

The **Renew Now** button in the email directs Sarah to the web version of the policy. Vous pouvez consulter l’URL suivante :

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

You can check the detailed summary of your Auto Insurance Renewal and click **Renew Now** at the bottom of the page.

### Sarah accède à la page de paiement {#sarah-reaches-the-payment-page}

We.Finance redirige Sarah vers la page de paiement. Sarah vérifie à nouveau son numéro de police et sa date d’expiration avec ses enregistrements. Sur le côté droit de la page, elle vérifie le Sommaire des paiements de son renouvellement avec une réduction de 10 % sur le montant total.

#### Fonctionnement {#how-it-works-1}

Le bouton Renouveler maintenant dirige Sarah vers la page de paiement. La page de paiement est un formulaire adaptatif.

#### Démonstration {#see-it-yourself-2}

Cliquez sur **Renouveler maintenant** pour accéder à la page de paiement. Fill in your Credit Card information, and click **Make Payment.**

Vous pouvez accéder à la page de paiement dans l’instance de création à l’adresse

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah effectue le paiement et termine le processus.{#sarah-makes-the-payment-and-completes-the-process}

Sarah remplit ses informations de carte de crédit et clique sur **Effectuer un paiement**.

#### Fonctionnement {#how-it-works-2}

Lorsque Sarah remplit les informations de carte de crédit et clique sur le bouton Envoyer, son paiement de carte de crédit est traité et un message de remerciement configuré dans le formulaire adaptatif s’affiche à l’écran.

#### Démonstration {#see-it-yourself-3}

Vous pouvez afficher le message de confirmation après avoir cliqué sur Effectuer le paiement à l’adresse

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
