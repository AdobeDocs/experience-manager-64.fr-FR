---
title: Envoi d’un accusé de réception d’envoi de formulaire par e-mail
seo-title: Sending a form submission acknowledgement via email
description: AEM Forms vous permet de configurer l’action d’envoi par courrier électronique qui envoie un accusé de réception à un utilisateur lors de l’envoi du formulaire.
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 22%

---

# Envoi d’un accusé de réception d’envoi de formulaire par e-mail {#sending-a-form-submission-acknowledgement-via-email}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Envoi de données de formulaire adaptatif {#adaptive-form-data-submission}

Les formulaires adaptatifs fournissent plusieurs [actions d’envoi](/help/forms/using/configuring-submit-actions.md) processus pour envoyer les données de formulaire à différents points de terminaison.

Par exemple, la variable **Action Courrier électronique** l’action d’envoi envoie un courrier électronique lors de l’envoi réussi d’un formulaire adaptatif. Elle peut également être configurée pour envoyer les données de formulaire et le fichier PDF dans l’e-mail.

Cet article décrit les étapes à suivre pour activer l’action Courrier électronique sur un formulaire adaptatif et les différentes configurations fournies.

>[!NOTE]
>
>Vous pouvez également utiliser la variable **Action du PDF de messagerie** pour envoyer le formulaire complété par courrier électronique en tant que pièce jointe du PDF. Les options de configuration disponibles pour cette action sont les mêmes que celles disponibles pour l’action Courrier électronique. L’action PDF par courrier électronique est disponible uniquement pour les formulaires adaptatifs basés sur XFA.

## Action Courrier électronique {#email-action}

L’action Courrier électronique permet à un auteur d’envoyer automatiquement un courrier électronique à un ou plusieurs destinataires lors de l’envoi réussi d’un formulaire adaptatif.

>[!NOTE]
>
>Pour utiliser l’action Courrier électronique, vous devez configurer le service de messagerie d’AEM comme décrit dans la section [Configuration du service de messagerie](/help/sites-administering/notification.md#configuring-the-mail-service).

### Activation de l’action Courrier électronique sur un formulaire adaptatif {#enabling-email-action-on-an-adaptive-form}

1. Ouvrez un formulaire adaptatif en mode d’édition.

1. Cliquez sur **Modifier** en regard de **Début d’un formulaire adaptatif** de la barre d’outils.

   La boîte de dialogue Modifier le composant s’ouvre.

   ![Boîte de dialogue Modifier le composant d’un formulaire adaptatif](assets/start_of_adp_form.png)

1. Sélectionnez la **Actions Envoyer** et choisissez **Action Courrier électronique** dans la liste déroulante Action Envoyer .

   L’onglet affiche les options permettant de configurer l’action Courrier électronique pour le formulaire actif.

   ![Onglet Actions Envoyer](assets/dialog.png)

1. Spécifiez des ID de courrier électronique valides dans les champs De, CC et Cci.

   Indiquez respectivement l&#39;objet et le corps de l&#39;email dans les champs Objet et Modèle de courrier électronique .

   Vous pouvez également spécifier des espaces réservés aux variables dans les champs. Dans ce cas, les valeurs des champs sont traitées lorsque le formulaire est envoyé avec succès par un utilisateur final. Pour plus d’informations, voir [Utilisation des noms de champ de formulaire adaptatif pour créer dynamiquement le contenu d’un email](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Cochez la case Inclure les pièces jointes si le formulaire contient des pièces jointes que vous souhaitez joindre à l’e-mail.

   >[!NOTE]
   >
   >Si vous choisissez l’option **Action du PDF de messagerie**, vous devez sélectionner l’option Inclure les pièces jointes .

1. Pour enregistrer les modifications, cliquez sur **OK**.

### Utilisation des noms de champ de formulaire adaptatif pour créer dynamiquement le contenu d’un email {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Les noms de champ d’un formulaire adaptatif sont appelés espaces réservés, remplacés par la valeur de ce champ après l’envoi du formulaire par un utilisateur.

Dans l’onglet Action Courrier électronique, vous pouvez utiliser des espaces réservés qui sont traités lors de l’exécution de l’action. Cela implique que les en-têtes de l’email (tels que Mailto, CC, Cci, Objet) soient générés lorsque l’utilisateur envoie le formulaire.

Pour définir un espace réservé, spécifiez `${<field name>}` dans un champ de l’onglet Actions Envoyer .

Par exemple, si le formulaire contient la variable **Adresse électronique** champ, nommé `email_addr`, pour capturer l’e-mail d’un utilisateur, vous pouvez spécifier les éléments suivants dans les champs De, CC ou Cci.

`${email_addr}`

Lorsqu’un utilisateur envoie le formulaire, un e-mail est envoyé à l’identifiant d’adresse électronique entré dans le champ `email_addr` du formulaire.

>[!NOTE]
>
>Vous pouvez trouver le nom d’un champ dans la boîte de dialogue **Modifier** de ce champ.

Les espaces réservés aux variables peuvent également être utilisés dans la variable **Objet** et **Modèle de courrier électronique** champs.

Par exemple :

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Les champs des panneaux répétables ne peuvent pas être utilisés en tant qu’espaces réservés aux variables.
