---
title: Participation aux workflows
seo-title: Participating in Workflows
description: Les workflows incluent généralement des étapes qui nécessitent qu’une personne effectue une activité sur une page ou une ressource.
seo-description: Workflows typically include steps that require a person to perform an activity on a page or asset.
uuid: 3e195da4-b25e-459d-9a4c-84549f62d7ff
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 37c8b1bd-0e60-42d2-80ed-dece3f5c2342
exl-id: 7b645497-ddbf-403c-9e78-5e845f6bda50
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1551'
ht-degree: 61%

---

# Participation aux workflows{#participating-in-workflows}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les workflows incluent généralement des étapes qui nécessitent qu’une personne effectue une activité sur une page ou une ressource. Le workflow sélectionne un utilisateur ou un groupe pour exécuter l’activité et affecte une tâche à cette personne ou à ce groupe. L’utilisateur reçoit une notification et peut ensuite prendre la mesure appropriée :

* [Affichage des notifications](#notifications-of-available-workflow-actions)
* [Finalisation d’une étape de participant](#completing-a-participant-step)
* [Délégation d’une étape de participant](#delegating-a-participant-step)
* [Revenir d’une étape de participant en arrière](#performing-step-back-on-a-participant-step)
* [Ouverture d’un élément de workflow pour afficher les détails (et réaliser des actions)](#opening-a-workflow-item-to-view-details-and-take-actions)
* [Affichage de la charge utile de workflow (plusieurs ressources)](#viewing-the-workflow-payload-multiple-resources)

## Notifications d’actions de workflow disponibles {#notifications-of-available-workflow-actions}

Lorsqu’une tâche vous est attribuée (par exemple, **Approuver le contenu**), diverses alertes et/ou notifications s’affichent :

* Votre [notification](/help/sites-authoring/inbox.md) indicateur (barre d’outils) sera incrémenté :

   ![](do-not-localize/wf-57.png)

* L’élément est répertorié dans votre [boîte de réception](/help/sites-authoring/inbox.md) de notifications :

   ![wf-58](assets/wf-58.png)

* Lorsque vous utilisez l’éditeur de page, la barre d’état affiche :

   * Le nom du ou des workflows appliqués à la page ; par exemple, Demande d’activation.
   * Toute action disponible pour l’utilisateur actuel pour l’étape actuelle du workflow ; par exemple, Terminer, Déléguer, Afficher les détails.
   * Nombre de workflows auxquels la page est soumise. Vous pouvez :

      * utilisez les flèches gauche/droite pour parcourir les informations d’état des différents workflows.
      * cliquer/appuyer sur le nombre pour ouvrir la liste déroulante de tous les workflows applicables, puis sélectionner le workflow que vous souhaitez afficher dans la barre d’état.

   ![wf-59](assets/wf-59.png)

   >[!NOTE]
   >
   >La barre d’état est uniquement visible pour les utilisateurs disposant de droits de workflow ; par exemple, les membres du groupe `workflow-users`.
   >
   >
   >Les actions s’affichent lorsque l’utilisateur actuel est directement impliqué dans l’étape actuelle du workflow.

* When **Chronologie** est ouvert pour la ressource. L’étape du workflow s’affiche. Lorsque vous cliquez/appuyez sur la bannière d’alerte, les actions disponibles s’affichent également :

   ![wf-64](assets/wf-64.png)

### Réalisation d’une étape de participant {#completing-a-participant-step}

Vous pouvez terminer un élément pour permettre au workflow de passer à l’étape suivante.

Sur cette action, vous pouvez indiquer :

* **Étape suivante**: la prochaine étape; vous pouvez effectuer une sélection dans la liste fournie.
* **Commentaire**: si nécessaire

Vous pouvez terminer une étape de participant à partir des éléments suivants :

* [La boîte de réception](#completing-a-participant-step-inbox)
* [L’éditeur de page](#completing-a-participant-step-page-editor)
* [La chronologie](#completing-a-participant-step-timeline)
* when [ouverture d’un élément de workflow pour afficher les détails](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Réalisation d’une étape de participant – Boîte de réception {#completing-a-participant-step-inbox}

Utilisez la procédure suivante pour terminer l’élément de travail :

1. Ouvrez la **[boîte de réception AEM](/help/sites-authoring/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Sélectionnez **Terminer** dans la barre d’outils.
1. La boîte de dialogue **Terminer l’élément de travail** s’ouvre. Choisissez **Étape suivante** dans la liste déroulante et ajoutez un **commentaire** s’il y a lieu.
1. Cliquez sur **OK** pour terminer l’étape (ou **Annuler** pour annuler l’action).

#### Réalisation d’une étape de participant – Éditeur de page {#completing-a-participant-step-page-editor}

Utilisez la procédure suivante pour terminer l’élément de travail :

1. Ouvrez le [page à modifier](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Sélectionnez **Terminer** dans la barre d’état en haut.
1. La boîte de dialogue **Terminer l’élément de travail** s’ouvre. Choisissez **Étape suivante** dans la liste déroulante et ajoutez un **commentaire** s’il y a lieu.
1. Cliquez sur **OK** pour terminer l’étape (ou **Annuler** pour annuler l’action).

#### Réalisation d’une étape de participant – Chronologie {#completing-a-participant-step-timeline}

Vous pouvez également utiliser la chronologie pour terminer et avancer d’une étape :

1. Sélectionnez la page requise et ouvrez la **chronologie** (ou ouvrez la **chronologie** et sélectionnez la page) :

   ![wf-65](assets/wf-65.png)

1. Cliquez/appuyez sur la bannière d’alerte pour afficher les actions disponibles. Sélectionner **Avance**:

   ![wf-66](assets/wf-66.png)

1. Selon le workflow, vous pouvez choisir l’étape suivante :

   ![wf-67](assets/wf-67.png)

1. Sélectionnez l’option **Avancer** pour confirmer l’action.

### Délégation d’une étape de participant {#delegating-a-participant-step}

Si une étape vous a été assignée, mais que vous ne pouvez pas effectuer d’action pour une raison quelconque, vous pouvez la déléguer à un autre utilisateur ou groupe.

Les utilisateurs pouvant faire l’objet d’une délégation dépendent de la personne à qui l’élément de travail a été affecté :

* Si l’élément de travail a été affecté à un groupe, les membres du groupe sont disponibles.
* Si l’élément de travail a été attribué à un groupe puis délégué à un utilisateur, les membres du groupe et le groupe sont disponibles.
* Si l’élément de travail a été attribué à un utilisateur unique, l’élément de travail ne peut pas être délégué.

Sur cette action, vous pouvez indiquer :

* **Utilisateur**: l’utilisateur auquel vous souhaitez déléguer ; vous pouvez effectuer une sélection dans la liste fournie.
* **Commentaire**: si nécessaire

Vous pouvez déléguer une étape de participant à partir de :

* [La boîte de réception](#delegating-a-participant-step-inbox)
* [L’éditeur de page](#delegating-a-participant-step-page-editor)
* [La chronologie](#delegating-a-participant-step-timeline)
* when [ouverture d’un élément de workflow pour afficher les détails](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Délégation d’une étape de participant – Boîte de réception {#delegating-a-participant-step-inbox}

Utilisez la procédure suivante pour déléguer un élément de travail :

1. Ouvrez la **[boîte de réception AEM](/help/sites-authoring/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Sélectionnez **Déléguer** dans la barre d’outils.
1. Une boîte de dialogue s’ouvre. Définissez l’**utilisateur** dans le sélecteur déroulant (il peut également s’agir d’un groupe) et ajoutez un **commentaire** si nécessaire.
1. Cliquez sur **OK** pour terminer l’étape (ou **Annuler** pour annuler l’action).

#### Délégation d’une étape de participant – Éditeur de page {#delegating-a-participant-step-page-editor}

Utilisez la procédure suivante pour déléguer un élément de travail :

1. Ouvrez le [page à modifier](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Sélectionnez **Déléguer** dans la barre d’état en haut.
1. Une boîte de dialogue s’ouvre. Définissez l’**utilisateur** dans le sélecteur déroulant (il peut également s’agir d’un groupe) et ajoutez un **commentaire** si nécessaire.
1. Cliquez sur **OK** pour terminer l’étape (ou **Annuler** pour annuler l’action).

#### Délégation d’une étape de participant – Chronologie {#delegating-a-participant-step-timeline}

Vous pouvez également utiliser la chronologie pour déléguer et/ou attribuer une étape :

1. Sélectionnez la page requise et ouvrez la **chronologie** (ou ouvrez la **chronologie** et sélectionnez la page).
1. Cliquez/appuyez sur la bannière d’alerte pour afficher les actions disponibles. Sélectionner **Changement de cessionnaire**:

   ![wf-69](assets/wf-69.png)

1. Spécifiez un nouveau cessionnaire :

   ![wf-68](assets/wf-68.png)

1. Sélectionnez **Attribuer** pour confirmer l’action.

### Revenir d’une étape de participant en arrière {#performing-step-back-on-a-participant-step}

Si vous découvrez qu’une étape, ou une série d’étapes, doit être répétée, vous pouvez prendre du recul. Cela vous permet de sélectionner une étape qui s’est produite plus tôt dans le workflow pour la traiter à nouveau. Le workflow revient à l’étape que vous spécifiez, puis passe de là.

Sur cette action, vous pouvez indiquer :

* **Étape précédente**: l’étape à laquelle la tâche doit être renvoyée ; vous pouvez effectuer une sélection dans la liste fournie.
* **Commentaire**: si nécessaire

Vous pouvez revenir en arrière sur une étape de participant à partir de :

* [la boîte de réception ;](#performing-step-back-on-a-participant-step-inbox)
* [L’éditeur de page](#performing-step-back-on-a-participant-step-page-editor)
* [La chronologie](#performing-step-back-on-a-participant-step-timeline)
* when [ouverture d’un élément de workflow pour afficher les détails](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Revenir d’une étape de participant en arrière – Boîte de réception {#performing-step-back-on-a-participant-step-inbox}

Procédez comme suit pour revenir en arrière :

1. Ouvrez la **[boîte de réception AEM](/help/sites-authoring/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Sélectionnez **Revenir en arrière** pour ouvrir la boîte de dialogue.

1. Définissez l’**étape précédente** et ajoutez un **commentaire** si nécessaire.
1. Cliquez sur **OK** pour terminer l’étape (ou **Annuler** pour annuler l’action).

#### Revenir d’une étape de participant en arrière – Éditeur de page {#performing-step-back-on-a-participant-step-page-editor}

Procédez comme suit pour revenir en arrière :

1. Ouvrez le [page à modifier](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Sélectionnez **Revenir en arrière** dans la barre d’état en haut.
1. Définissez l’**étape précédente** et ajoutez un **commentaire** si nécessaire.
1. Cliquez sur **OK** pour terminer l’étape (ou **Annuler** pour annuler l’action).

#### Revenir d’une étape de participant en arrière – Chronologie {#performing-step-back-on-a-participant-step-timeline}

Vous pouvez également utiliser la chronologie pour revenir à une étape précédente et la restaurer :

1. Sélectionnez la page requise et ouvrez la **chronologie** (ou ouvrez la **chronologie** et sélectionnez la page).
1. Cliquez/appuyez sur la bannière d’alerte pour afficher les actions disponibles. Sélectionner **Restaurer**:

   ![wf-69-1](assets/wf-69-1.png)

1. Spécifiez l’étape à laquelle le workflow doit revenir :

   ![wf-70](assets/wf-70.png)

1. Sélectionnez **Restaurer** pour confirmer l’action.

### Ouverture d’un élément de workflow pour afficher les détails (et réaliser des actions) {#opening-a-workflow-item-to-view-details-and-take-actions}

Affichez les détails de l’élément de travail du workflow et prenez les mesures appropriées.

Les détails du workflow sont affichés dans les onglets et les actions appropriées sont disponibles dans la barre d’outils :

* Onglet **ÉLÉMENT DE TRAVAIL** :

   ![wf-72](assets/wf-72.png)

* **INFORMATIONS DU PROCESSUS**

   ![wf-73](assets/wf-73.png)

   Si des [étapes de workflow](/help/sites-developing/workflows.md#workflow-stages) ont été configurées pour le modèle, vous pouvez afficher la progression en fonction de ces éléments :

   ![wf-107](assets/wf-107.png)

* **COMMENTAIRES**

   ![wf-75](assets/wf-75.png)

Vous pouvez ouvrir les détails de l’élément de travail à partir de :

* [la boîte de réception ;](#performing-step-back-on-a-participant-step-inbox)
* [l’éditeur de page ;](#performing-step-back-on-a-participant-step-page-editor)

#### Ouverture des détails de workflow – Boîte de réception {#opening-workflow-details-inbox}

Pour ouvrir un élément de workflow et afficher les détails :

1. Ouvrez la **[boîte de réception AEM](/help/sites-authoring/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Sélectionnez **Ouvrir** pour ouvrir les onglets d’informations.

1. Si nécessaire, choisissez l’action appropriée, saisissez les informations et confirmez avec **OK** (ou **Annuler**).
1. Utilisez **Enregistrer** ou **Annuler** pour quitter.

#### Ouverture des détails de workflow – Éditeur de page {#opening-workflow-details-page-editor}

Pour ouvrir un élément de workflow et afficher les détails :

1. Ouvrez le [page à modifier](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Sélectionnez **Afficher les détails** dans la barre d’état pour ouvrir les onglets d’informations.

1. Si nécessaire, choisissez l’action appropriée, saisissez les informations et confirmez avec **OK** (ou **Annuler**).
1. Utilisez **Enregistrer** ou **Annuler** pour quitter.

### Affichage du payload de workflow (plusieurs ressources) {#viewing-the-workflow-payload-multiple-resources}

Vous pouvez afficher les détails de la charge utile associée à l’instance de workflow. Au départ, les ressources du module s’affichent, puis vous pouvez descendre dans la hiérarchie pour afficher les différentes pages.

Pour afficher la charge utile et les ressources de l’instance de workflow :

1. Ouvrez la **[boîte de réception AEM](/help/sites-authoring/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Sélectionnez **Afficher la charge utile** dans la barre d’outils pour ouvrir la boîte de dialogue.

   Un package de workflow étant simplement un ensemble de pointeurs vers les chemins d’accès au sein du référentiel, vous pouvez y ajouter, supprimer ou modifier les entrées pour définir ce qu’il référence. Utilisez la variable **Définition de ressource** pour ajouter de nouvelles entrées.

   ![wf-78](assets/wf-78.png)

1. Les liens peuvent être utilisés pour ouvrir individuellement les pages.
