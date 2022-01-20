---
title: Présentation du site de référence de libre-service dédié aux employés
seo-title: Employee self-service
description: Le site de référence AEM Forms présente la manière dont les entreprises peuvent tirer parti des fonctionnalités AEM Forms pour mettre en œuvre des processus de recrutement et de libre-service destinés aux employés.
seo-description: AEM Forms reference site showcases how organizations can leverage AEM Forms features to implement employee recruitment and self-service workflows.
uuid: ecc98e0d-c964-44dc-b219-9ebe92632d22
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d2695f71-5126-477c-ae6b-a964fb55728b
exl-id: 7fbdd976-5a70-4af4-b449-7c2d6bcfd915
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 84%

---

# Libre-service dédié aux employés présentation du site de référence {#employee-self-service-reference-site-walkthrough}

## Prérequis {#prerequisite}

Installez les sites de référence comme décrit dans [Installation et configuration des sites de référence d’AEM Forms](/help/forms/using/setup-reference-sites.md).

## Présentation {#overview}

Les systèmes de libre-service dédié aux employés, généralement hébergés sur l’Intranet de l’entreprise, permettent aux salariés d’accéder à un certain nombre d’informations et de services qu’ils peuvent utiliser depuis leur bureau. Ils permettent et donnent le contrôle complet aux employés pour effectuer des actions telles qu’accéder aux informations sur leur poste, demander des jours de congés et envoyer des rapports de dépenses. Ils aident également les entreprises à améliorer l’efficacité des processus et à réduire les coûts tout en gardant les employés informés et impliqués.

Le site de référence de libre-service des employés montre comment vous pouvez utiliser AEM Forms pour mettre en place le système de libre-service destiné aux employés dans votre entreprise.

>[!NOTE]
>
>Les cas d’utilisation du libre-service destiné aux employés sont disponibles sur les sites de référence We.Finance et We.Gov. Les exemples, images et descriptions utilisés dans les présentations utilisent le site de référence We.Finance. Cependant, vous pouvez exécuter ces cas d’utilisation et revoir les artefacts en utilisant We.Gov. Pour ce faire, vous devez remplacer **we-finance** par **we-gov** dans les URL mentionnées.

## Présentation du questionnaire sur les conflits d’intérêt {#conflict-of-interest-questionnaire-walkthrough}

De temps à autre, les organisations demandent à leurs employés de soumettre un questionnaire sur les conflits d’intérêt afin d’identifier les activités extérieures ou les relations personnelles de leurs employés qui peuvent potentiellement entrer en conflit avec leur organisation.

Le service Conformité de l’organisation de Sarah a demandé aux employés de soumettre le questionnaire sur les conflits d’intérêt.

### Sarah envoie le questionnaire sur les conflits d’intérêt {#sarah-submits-the-conflict-of-interest-questionnaire}

Sarah se rend sur le portail de son entreprise, se connecte et clique sur Employé pour accéder au tableau de bord des employés. Elle trouve le questionnaire sur les conflits d’intérêt dans le tableau de bord des employés et clique sur **[!UICONTROL Demander]**.

![we-finance-home](assets/we-finance-home.png)
**Figure :** *Portail d’organisation*

![employee-dashboard](assets/employee-dashboard.png)
**Figure :** *Tableau de bord des employés*

Sarah navigue dans le formulaire en utilisant le bouton Suivant et lit les sections Introduction et Définition. Elle répond aux questions dans la section dédiée. Enfin, elle signe et envoie le questionnaire.

Le portail de l’entreprise et le questionnaire sont réactifs et compatibles avec les appareils mobiles. Le processus suivant montre comment Sarah navigue dans le questionnaire et l’envoie depuis son appareil mobile.

![conflict-form-on-mobile](assets/conflict-form-on-mobile.png)

**Fonctionnement**

Le portail de l’entreprise et le tableau de bord des employés sont des pages de sites AEM. Le tableau de bord répertorie plusieurs options de libre-service, telles que le questionnaire sur les conflits d’intérêt. Le bouton Demander est lié à un formulaire adaptatif.

Le formulaire adaptatif utilise des règles pour masquer ou afficher les informations en fonction de la réponse fournie dans l’onglet Questions. En outre, le formulaire utilise le composant Scribble pour la signature dans l’onglet Déclaration. Consultez le formulaire adaptatif à l’adresse `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/conflict-of-interest.html`.

**Démonstration**

Accédez à `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` et se connecter à l’aide de `srose/srose` comme nom d’utilisateur/mot de passe pour Sarah. Cliquez sur **[!UICONTROL Employé]** pour accéder au tableau de bord, puis sur **[!UICONTROL Demander]** sur le questionnaire sur les conflits d’intérêt. Vérifiez et envoyez le questionnaire.

### Gloria examine et approuve l’envoi du questionnaire sur les conflits d’intérêt {#gloria-reviews-and-approves-the-conflict-of-interest-questionnaire-submission}

Le questionnaire sur les conflits d’intérêt envoyé par Sarah est attribué à Gloria Rios pour examen. Gloria travaille en tant qu’agent de conformité dans l’entreprise. Gloria se connecte à sa boîte de réception AEM et passe en revue les tâches qui lui sont assignées. Elle approuve le questionnaire envoyé par Sarah et termine la tâche.

![conflict-inbox](assets/conflict-inbox.png)
**Figure :** *Boîte de réception de Gloria*

![approbation de conflit](assets/conflict-approved.png)
**Figure :** *Ouvrir la tâche*

**Fonctionnement**

L’action d’envoi dans le questionnaire sur les conflits d’intérêt déclenche un processus qui crée une tâche dans la boîte de réception de Gloria pour approbation. Vérifiez le Forms Workflow à l’adresse `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-conflict-of-interest.html`

![employee-self-service-reference-site](assets/employee-self-service-reference-site.png)

**Démonstration**

Accédez à `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` et se connecter à l’aide de `grios/password` comme nom d’utilisateur/mot de passe pour Gloria Rios. Ouvrez la tâche créée pour le questionnaire sur les conflits d’intérêt et approuvez-la.

## Présentation de la demande de la carte d’entreprise {#corporate-card-application-walkthrough}

Sarah voyage beaucoup pour les affaires et elle a besoin d’une carte de crédit d’entreprise pour payer ses factures lors de ses déplacements. Elle demande une carte d’entreprise via le portail des employés de son entreprise.

### Sarah envoie la demande Carte d’entreprise {#sarah-submits-the-corporate-card-application}

Sarah se rend sur le portail de son entreprise, se connecte et clique sur **[!UICONTROL Employé]** pour accéder au tableau de bord des employés. Elle trouve la demande Carte d’entreprise dans le tableau de bord des employés et clique sur **[!UICONTROL Demander]**.

![we-finance-home-1](assets/we-finance-home-1.png)
**Figure :** *Portail d’organisation*

![employee-dashboard-1](assets/employee-dashboard-1.png)
**Figure :** *Tableau de bord des employés*

Elle clique sur **[!UICONTROL Demander]** dans la demande Carte d’entreprise. Une demande d’une page s’ouvre. Elle renseigne toutes les informations et clique sur **[!UICONTROL Demander]** pour envoyer la demande.

![card-form](assets/card-form.png)

**Fonctionnement**

Le portail de l’entreprise et le tableau de bord des employés sont des pages de sites AEM. Le tableau de bord répertorie plusieurs options de libre-service, telles que la demande de carte d’entreprise. Le bouton Demander sur la demande est lié à un formulaire adaptatif.

Le formulaire adaptatif pour la demande de carte d’entreprise est un formulaire adaptatif d’une page simple et réactif. Il utilise des composants basiques de formulaire adaptatif tels que le texte, le téléphone, la zone numérique et la procédure pas à pas numérique. Consultez le formulaire adaptatif à l’adresse suivante :\
`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/corporate-card.html`.

**Démonstration**

Accédez à `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` et se connecter à l’aide de `srose/srose` comme nom d’utilisateur/mot de passe pour Sarah. Cliquez sur **[!UICONTROL Employé]** pour accéder au tableau de bord, puis sur **[!UICONTROL Demander]** sur la demande de carte d’entreprise. Renseignez les informations et envoyez la demande.

### Gloria examine et approuve la demande de carte d’entreprise {#gloria-reviews-and-approves-the-corporate-card-application}

La demande de carte d’entreprise envoyée par Sarah est attribuée à Gloria Rios pour examen. Gloria se connecte à sa boîte de réception AEM et passe en revue les tâches qui lui sont assignées. Elle approuve la demande envoyée par Sarah et termine la tâche.

![corporation-card-inbox](assets/corporate-card-inbox.png)
**Figure :** *Boîte de réception de Gloria*

![carte d’entreprise approuvée](assets/corporate-card-approved.png)
**Figure :** *Ouvrir la tâche*

**Fonctionnement**

Le processus d’envoi dans la demande de carte d’entreprise déclenche un processus Forms qui crée une tâche dans la boîte de réception de Gloria pour approbation. Vérifiez le Forms Workflow à l’adresse `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-corporate-card.html`

![corporation-card-workflow-model](assets/corporate-card-workflow-model.png)

**Démonstration**

Accédez à `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` et se connecter à l’aide de `grios/password` comme nom d’utilisateur/mot de passe pour Gloria Rios. Ouvrez la tâche créée pour la demande de carte d’entreprise et approuvez-la.

## Présentation de l’envoi du rapport de dépenses {#expense-report-submission-walkthrough}

Sarah doit envoyer des rapports de dépenses pour approbation car ses déplacements professionnels engendrent des frais. L’option self-service dans son entreprise lui permet d’envoyer le rapport de dépenses en ligne.

### Sarah envoie la demande de rapport de dépenses {#sarah-submits-the-expense-report-application}

Sarah se rend sur le portail de son entreprise, se connecte et clique sur **[!UICONTROL Employé]** pour accéder au tableau de bord des employés. Elle trouve la demande Rapport de dépenses dans le tableau de bord des employés et clique sur **[!UICONTROL Demander]**.

![we-finance-home-2](assets/we-finance-home-2.png)
**Figure :** *Portail d’organisation*

![employee-dashboard-2](assets/employee-dashboard-2.png)
**Figure :** *Tableau de bord des employés*

Elle clique sur **[!UICONTROL Demander]** dans la demande Rapport de dépenses. Un formulaire de demande s’ouvre avec deux onglets : Nom du rapport et Détails du rapport. L’icône **+** dans l’onglet Détails du rapport lui permet d’ajouter plus de dépenses dans un rapport.

Le portail de l’entreprise et les demandes sont réactifs et compatibles avec les appareils mobiles. Le processus suivant montre comment Sarah navigue dans le rapport de dépenses et l’envoie depuis son appareil mobile.

![rapport-dépenses-sur-mobile](assets/expense-report-on-mobile.png)

**Fonctionnement**

Le portail de l’entreprise et le tableau de bord des employés sont des pages de sites AEM. Le tableau de bord répertorie plusieurs options de libre-service, telles que la demande de rapport de dépenses. Le bouton Demander est lié à un formulaire adaptatif.

Les onglets Nom du rapport et Détails du rapport du formulaire adaptatif sont des composants Panneau. Le panneau Détails du rapport contient le panneau Dépenses. Il s’agit d’un panneau répétable qui permet d’ajouter plusieurs dépenses dans le rapport. Passez en revue le formulaire adaptatif et ses configurations à l’adresse `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/expense-report.html`.

**Démonstration**

Accédez à `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` et se connecter à l’aide de `srose/srose` comme nom d’utilisateur/mot de passe pour Sarah. Cliquez sur **[!UICONTROL Employé]** pour accéder au tableau de bord, puis sur **[!UICONTROL Demander]** sur la demande de rapport de dépenses. Renseignez les informations et envoyez la demande.

### Gloria examine et approuve le rapport de dépenses {#gloria-reviews-and-approves-the-expense-report}

Le rapport de dépenses envoyé par Sarah est attribué à Gloria Rios pour examen. Gloria se connecte à sa boîte de réception AEM et passe en revue les tâches qui lui sont assignées. Elle approuve la demande envoyée par Sarah et termine la tâche.

![dépense-rapport-inbox](assets/expense-report-inbox.png)
**Figure :** *Boîte de réception de Gloria*

![rapport-dépenses-approuvé](assets/expense-report-approved.png)
**Figure :** *Ouvrir la tâche*

**Fonctionnement**

Le processus d’envoi dans la demande de rapport de dépenses déclenche un processus Forms qui crée une tâche dans la boîte de réception de Gloria pour approbation. Vérifiez le Forms Workflow à l’adresse `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-expense-report-workflow.html`

![carte-entreprise-dépense-rapport-workflow-modèle](assets/corporate-card-expense-report-workflow-model.png)

**Démonstration**

Accédez à `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` et se connecter à l’aide de `grios/password` comme nom d’utilisateur/mot de passe pour Gloria Rios. Ouvrez la tâche créée pour la demande de rapport de dépenses et approuvez-la.

## Présentation de la demande de congés {#leave-application-walkthrough}

Sarah prévoit des vacances en famille le mois prochain et veut demander une semaine de congé.

### Sarah envoie la demande de congés {#sarah-submits-the-leave-application}

Sarah se rend sur le portail de son entreprise, se connecte et clique sur **[!UICONTROL Employé]** pour accéder au tableau de bord des employés. Elle trouve la demande de congés dans le tableau de bord des employés et clique sur **[!UICONTROL Demander]**.

![we-finance-home-3](assets/we-finance-home-3.png)
**Figure :** *Portail d’organisation*

![employee-dashboard-3](assets/employee-dashboard-3.png)
**Figure :** *Tableau de bord des employés*

La demande de congés s’ouvre avec le nom de Sarah et son ID d’employée pré-renseignés dans le formulaire. Elle affiche également son nombre de jours de congé et l’historique. Elle remplit les informations du congé et envoie la demande pour approbation.

Le portail de l’entreprise et les demandes sont réactifs et compatibles avec les appareils mobiles. Le processus suivant montre comment Sarah navigue dans la demande et l’envoie depuis son appareil mobile.

![leave-form-on-mobile](assets/leave-form-on-mobile.png)

**Fonctionnement**

Le portail de l’entreprise et le tableau de bord des employés sont des pages de sites AEM. Le tableau de bord répertorie plusieurs options de libre-service, telles que la demande de congés. Le bouton Demander est lié à un formulaire adaptatif.

Le formulaire adaptatif de la demande de congés est basé sur le modèle de données de formulaire de congés des employés. Dans la section Solde de congés, le tableau dédié est rempli à l’aide du service du modèle de données de formulaire `getLeavesOf`. Les champs Date de début et Date de fin utilisent des règles pour valider le fait que les valeurs de date sont égales ou ultérieures à la date actuelle. La durée du congé est calculée à l’aide de la fonction `calcBusinessDays`.

Vous pouvez consulter le formulaire adaptatif et le modèle de données de formulaire aux adresses suivantes :

`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/leave-application.html`

`https://[authorHost]:[authorPort]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/db`

**Démonstration**

Accédez à `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` et se connecter à l’aide de `srose/srose` comme nom d’utilisateur/mot de passe pour Sarah. Cliquez sur **[!UICONTROL Employé]** pour accéder au tableau de bord, puis sur **[!UICONTROL Demander]** sur la demande de congés. Renseignez les informations et envoyez la demande.

### Gloria examine et approuve la demande de congés {#gloria-reviews-and-approves-the-leave-application}

La demande de congés envoyée par Sarah est attribuée à Gloria Rios pour examen. Gloria se connecte à sa boîte de réception AEM et passe en revue les tâches qui lui sont assignées. Elle approuve la demande envoyée par Sarah et termine la tâche.

![leave-inbox](assets/leave-inbox.png)
**Figure :** *Boîte de réception de Gloria*

![leave-approved](assets/leave-approved.png)
**Figure :** *Ouvrir la tâche*

**Fonctionnement**

Le processus d’envoi dans la demande de congés déclenche un processus Forms qui crée une tâche dans la boîte de réception de Gloria pour approbation. Vérifiez le Forms Workflow à l’adresse `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-leave-application.html`

![corporation-card-leave-application-workflow-model](assets/corporate-card-leave-application-workflow-model.png)

**Démonstration**

Accédez à `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` et se connecter à l’aide de `grios/password` comme nom d’utilisateur/mot de passe pour Gloria Rios. Ouvrez la tâche créée pour la demande de congés et approuvez-la.
