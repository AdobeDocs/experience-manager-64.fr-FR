---
title: Actions et fonctionnalités des processus AEM sur OSGi et des processus AEM Forms JEE
seo-title: Actions and capabilities of Form-centric AEM Workflows on OSGi and AEM Forms JEE workflows
description: En savoir plus sur les différences dans les actions prises en charge par AEM boîte de réception et HTML Workspace, les différences dans les fonctionnalités prises en charge par les processus d’AEM basés sur l’utilisation de Forms sur les processus OSGi et AEM Forms JEE et les différences entre les fonctionnalités de la boîte de réception et de l’application AEM Forms.
seo-description: Learn more about the differences in actions supported by AEM Inbox and HTML Workspace, differences in capabilities supported by Form-centric AEM Workflows on OSGi and AEM Forms JEE Workflows, and differences between AEM Inbox and AEM Forms app features.
uuid: ce2a05fe-ba45-42ed-880e-fb1d6efc1d26
contentOwner: khsingh
topic-tags: publish
discoiquuid: 4c7ba430-25b2-4ba2-a5eb-4edaed0d599a
exl-id: 6172d936-9348-4f3f-a437-6465dd156f3b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 46%

---

# Actions et fonctionnalités des processus AEM sur OSGi et des processus AEM Forms JEE  {#actions-and-capabilities-of-form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## AEM Boîte de réception et Espace de travail de HTML {#aem-inbox-and-html-workspace}

AEM Boîte de réception est utilisée pour exécuter et surveiller les processus d’AEM Forms sur OSGi. HTML Workspace vous permet d’exécuter et de surveiller les processus AEM Forms JEE. Le tableau suivant répertorie les actions importantes disponibles dans AEM boîte de réception pour les processus d’AEM Forms sur OSGi et dans HTML Workspace pour les processus AEM Forms JEE.

<table> 
 <tbody>
  <tr>
   <td>Actions</td> 
   <td>Boîte de réception AEM</td> 
   <td>Espace de travail de HTML</td> 
  </tr>
  <tr>
   <td>Démarrage d’un processus, d’une tâche ou d’une application de formulaire<br /> </td> 
   <td>Pris en charge<br /> </td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Envoi de tâches</td> 
   <td>Pris en charge<br /> </td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Affectation d’une tâche à un groupe</td> 
   <td>Pris en charge<br /> </td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Envoi à plusieurs itinéraires</td> 
   <td>Pris en charge<br /> </td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Suivi de l’historique des tâches et du résumé des tâches</td> 
   <td>Pris en charge<br /> </td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Notifications par e-mail</td> 
   <td>Pris en charge<br /> </td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Réaffectation de tâches</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Pièces jointes au niveau du champ pour les formulaires adaptatifs</td> 
   <td>Pris en charge</td> 
   <td>Pas de prise en charge</td> 
  </tr>
  <tr>
   <td>Vue Calendrier</td> 
   <td>Pris en charge</td> 
   <td>Pas de prise en charge</td> 
  </tr>
  <tr>
   <td>Commentaires au niveau de la tâche</td> 
   <td>Pris en charge</td> 
   <td>Pas de prise en charge</td> 
  </tr>
  <tr>
   <td>Files d’attente (file d’attente personnelle partagée, demander des tâches de la file d’attente)</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Notification d’absence du bureau</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Affectation d’une tâche à plusieurs utilisateurs</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
 </tbody>
</table>

## Processus d’AEM axés sur les formulaires sur OSGi et les processus AEM Forms JEE {#form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

Les processus d’AEM basés sur l’utilisation de Forms on OSGi et les processus AEM Forms JEE (gestion des processus AEM Forms on JEE) ont un ensemble de fonctionnalités différent. Le tableau suivant répertorie les fonctionnalités importantes et la prise en charge des fonctionnalités des processus d’AEM basés sur l’utilisation de Forms on OSGi et des processus AEM Forms on JEE :

<table> 
 <tbody>
  <tr>
   <td>Fonctionnalités</td> 
   <td>Processus AEM de formulaire sur OSGi<br /> </td> 
   <td>Processus AEM Forms JEE</td> 
  </tr>
  <tr>
   <td>Formulaires adaptatifs</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Intégration à d’autres solutions AEM</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Signature tactile</td> 
   <td>Prise en charge</td> 
   <td>Prise en charge<br /> </td> 
  </tr>
  <tr>
   <td>Modèles de courrier électronique personnalisés</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Définition de la priorité des tâches</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Expiration d’une tâche après l’échéance</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Boucles dans un workflow</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Choix dynamique d’une personne désignée </td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Utilisation de métadonnées personnalisées</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Signature électronique (Acrobat Sign)</td> 
   <td>Pris en charge <sup>[1]</sup></td> 
   <td>Pris en charge <sup>[5]</sup></td> 
  </tr>
  <tr>
   <td>Gestion des applications de tâche et de formulaire</td> 
   <td>Pris en charge <sup>[2]</sup><br /> </td> 
   <td>Pris en charge <sup>[2]</sup></td> 
  </tr>
  <tr>
   <td>Services de document</td> 
   <td>Pris en charge <sup>[3]</sup></td> 
   <td>Pris en charge <sup>[3]</sup></td> 
  </tr>
  <tr>
   <td>Rendu de la tâche terminée en tant que formulaire adaptatif ou document de PDF</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge [4]</td> 
  </tr>
  <tr>
   <td>Intégration à Correspondence Management</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Bouton Réinitialiser</td> 
   <td>Pris en charge</td> 
   <td>Pas de prise en charge</td> 
  </tr>
  <tr>
   <td>Étapes de workflow</td> 
   <td>Pris en charge</td> 
   <td>Pas de prise en charge</td> 
  </tr>
  <tr>
   <td>Formulaires adaptatifs en lecture seule</td> 
   <td>Pris en charge</td> 
   <td>Pas de prise en charge</td> 
  </tr>
  <tr>
   <td>Masquage du bouton d’enregistrement par défaut</td> 
   <td>Pris en charge</td> 
   <td>Pas de prise en charge</td> 
  </tr>
  <tr>
   <td>Contrôle granulaire de la section des détails du workflow</td> 
   <td>Pris en charge</td> 
   <td>Pas de prise en charge</td> 
  </tr>
  <tr>
   <td>Formulaires HTML5, formulaires PDF interactifs, jeu de formulaires<br /> </td> 
   <td>Pas de prise en charge<br /> </td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Rapports de workflow</td> 
   <td>Pas de prise en charge<br /> </td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Signature numérique</td> 
   <td>Pris en charge<br /> </td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Catégories de point de départ</td> 
   <td>Pas de prise en charge </td> 
   <td>Pris en charge </td> 
  </tr>
  <tr>
   <td>Approbation de tâches en masse </td> 
   <td>Pas de prise en charge </td> 
   <td>Pris en charge </td> 
  </tr>
  <tr>
   <td>Enregistrer le brouillon avec un nom personnalisé</td> 
   <td>Pas de prise en charge </td> 
   <td>Pris en charge </td> 
  </tr>
  <tr>
   <td>Lancer un processus avec des données de processus existantes<br /> </td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge </td> 
  </tr>
  <tr>
   <td>Enregistrement d’un point de départ en tant que brouillon</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>avatar de l’utilisateur</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Vue Gestionnaire</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Modèles de recherche</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge<br /> </td> 
  </tr>
  <tr>
   <td>Intégration à des applications tierces</td> 
   <td>Pris en charge <sup>[6]</sup></td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Pièces jointes au niveau de la tâche pour l’application de workflow ou le point de départ</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Email de rappel</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Modifier le titre au délai d’expiration de la tâche</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Courrier électronique pour la délégation de tâche et la demande de tâche</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Envoyer un email à la fin du workflow</td> 
   <td>Pris en charge <sup>[7]</sup></td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Déléguer entre les groupes disjoints</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Appel d’un service Web à partir d’un workflow</td> 
   <td>Pris en charge <sup>[6]</sup></td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>XSLT Transform</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Passerelles, AUCUNE ATTENTE</td> 
   <td>Pris en charge </td> 
   <td>Pris en charge </td> 
  </tr>
  <tr>
   <td>Division ET, OU</td> 
   <td>Pas de prise en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Priorité des tâches dynamiques</td> 
   <td>Non pris en charge.</td> 
   <td>Non pris en charge.</td> 
  </tr>
 </tbody>
</table>

1. Vous pouvez utiliser des processus d’AEM basés sur l’utilisation de Forms sur OSGi pour signer un formulaire adaptatif déjà rempli. Les processus AEM de formulaire sur OSGi prennent en charge la signature hors du formulaire. L’expérience de [signature dans le formulaire](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience) n’est pas prise en charge.

1. Vous avez besoin de l’accès à AEM Boîte de réception pour exécuter et surveiller les processus AEM Forms OSGi AEM et HTML Workspace pour exécuter et surveiller les processus AEM Forms JEE.
1. Les services documentaires AEM Forms natifs sont disponibles pour les processus AEM de formulaire sur OSGi et les processus AEM Forms on JEE. AEM Workflow utilise des services documentaires natifs pour les processus AEM de formulaire sur OSGi et les workflows AEM Forms JEE (gestion des processus).
1. Les processus AEM Forms JEE peuvent uniquement générer un formulaire adaptatif. Il ne prend pas en charge le rendu d’un formulaire adaptatif en tant que document de PDF.
1. Les processus d’AEM forms JEE ne comportent pas d’étape distincte pour Acrobat Sign. Vous avez besoin d’un formulaire adaptatif Acrobat Sign pour les processus JEE d’AEM forms. Pour plus d’informations, voir [Documentation Acrobat Sign](/help/forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component).
1. Vous pouvez utiliser l’étape [Appeler le service de modèle de données du formulaire](/help/forms/using/aem-forms-workflow-step-reference.md#p-invoke-form-data-model-service-step-p) pour appeler un service web et publier ou récupérer des données à partir d’une application tierce.
1. Vous pouvez utiliser l’étape [Envoyer un e-mail](/help/forms/using/aem-forms-workflow-step-reference.md#send-email-step) pour envoyer des e-mails.

## Différences entre les fonctionnalités de la boîte de réception AEM et l’application AEM Forms {#differences-between-aem-inbox-and-aem-forms-app-features}

Deux des moyens principaux de lancer un workflow basé sur l’utilisation de Forms sont la [boîte de réception AEM](/help/forms/using/manage-applications-inbox.md) et l’application AEM Forms. Les fonctionnalités de la boîte de réception AEM et de l’application AEM Forms sont cependant différentes. La boîte de réception AEM ne fonctionne qu’avec des [workflows basés sur l’utilisation de Forms](/help/forms/using/aem-forms-workflow.md) tandis que l’application AEM Forms fonctionne à la fois avec les workflows basés sur l’utilisation de Forms ainsi que la gestion des workflows.

La table suivante répertorie les fonctionnalités de la boîte de réception AEM et de l’application AEM Forms :

<table> 
 <tbody>
  <tr>
   <td><p><strong>Actions</strong></p> </td> 
   <td><p><strong>Boîte de réception AEM</strong></p> </td> 
   <td><p><strong>Application AEM Forms</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Démarrage d’une application de formulaire</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pris en charge</p> </td> 
  </tr>
  <tr>
   <td><p>Envoi de tâches</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pris en charge</p> </td> 
  </tr>
  <tr>
   <td><p>Délégation de tâches</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pas de prise en charge</p> </td> 
  </tr>
  <tr>
   <td><p>Suivi de l’historique des tâches et du résumé des tâches</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pas de prise en charge</p> </td> 
  </tr>
  <tr>
   <td><p>Ajout de pièces jointes au niveau de la tâche</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pris en charge</p> </td> 
  </tr>
  <tr>
   <td><p>Affichage des pièces jointes au niveau de la tâche</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pris en charge</p> </td> 
  </tr>
  <tr>
   <td><p>Ajout de pièces jointes au niveau du champ</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pris en charge</p> </td> 
  </tr>
  <tr>
   <td><p>Affichage de la vue Calendrier</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pas de prise en charge</p> </td> 
  </tr>
  <tr>
   <td><p>Ajout de commentaires</p> </td> 
   <td><p>Pris en charge</p> </td> 
   <td><p>Pris en charge</p> </td> 
  </tr>
 </tbody>
</table>
