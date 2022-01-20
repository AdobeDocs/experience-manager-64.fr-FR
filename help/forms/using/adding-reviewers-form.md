---
title: Association de réviseurs d’envoi à un formulaire
seo-title: Associating submission reviewers with a form
description: Apprenez à associer des réviseurs d’envoi à un formulaire dans AEM Forms. Les réviseurs associés examinent un formulaire envoyé via un portail de formulaires.
seo-description: Learn how to associate submission reviewers with a form in AEM Forms. Associated reviewers review a form submitted via forms portal.
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
feature: Adaptive Forms
exl-id: b45d844e-acf9-4da2-b54e-08c67aa183a3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 98%

---

# Association de réviseurs d’envoi à un formulaire  {#associating-submission-reviewers-with-a-form}

Lorsque vous créez un formulaire, vous pouvez spécifier les utilisateurs qui passent en revue les envois du formulaire via le portail de formulaires et qui font part de leur avis. Votre entreprise peut recueillir des avis et retravailler les formulaires envoyés.

AEM Forms vous permet d’associer un groupe de réviseurs à un formulaire. Les utilisateurs ajoutés à un groupe de révision d’un formulaire examinent les envois du formulaire en question et font part de leurs commentaires.

Les groupes de réviseurs assignés à un formulaire peuvent uniquement analyser les envois du formulaire spécifié.

## Prérequis {#prerequisite}

### Activation de la propriété des groupes de réviseurs d’envoi pour des formulaires adaptatifs à l’aide de l’éditeur de schéma de métadonnées {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Pour associer un groupe de réviseurs à un formulaire, modifiez le schéma de métadonnées des formulaires adaptatifs. Par défaut, vous ne pouvez pas ajouter un groupe de réviseurs à un formulaire envoyé.

Pour modifier le schéma de métadonnées :

1. En mode Création, sous Experience Manager, cliquez sur **[!UICONTROL Outils > Actifs > Schémas de métadonnées]**.
1. Dans la page Formulaires de schéma, accédez à **[!UICONTROL Formulaires > Formulaires créés dans AEM]**.

   L’URL de la page est :

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. Sélectionnez **[!UICONTROL Formulaire adaptatif]**, puis cliquez sur **[!UICONTROL Modifier]**.
1. Dans la page Modifier un formulaire, cliquez sur **[!UICONTROL Avancé]**.
1. Dans l’onglet Avancé, effectuez un glisser-déposer du composant **[!UICONTROL Une seule ligne de texte]** disponible sous Générer un formulaire.
1. Sélectionnez le composant de texte ajouté pour afficher ses paramètres.

   Sous Paramètres, saisissez `./jcr:content/metadata/form-submission-reviewer-group` dans le champ Associer à la propriété.

   Le champ de groupe de réviseurs d’envoi dans les propriétés avancées de votre formulaire adaptatif est activé avec le nom que vous spécifiez dans le libellé du champ.

## Association de réviseurs d’envoi à un formulaire {#associating-submission-reviewers-with-a-form-1}

Pour associer des réviseurs d’envoi à un formulaire adaptatif, créez un groupe de réviseurs et ajoutez-y des utilisateurs. Ajoutez le groupe de réviseurs créé sous le champ de réviseurs d’envoi de formulaire dans les propriétés avancées du formulaire.\
Les groupes d’utilisateurs vous permettent d’associer différents ensembles de réviseurs d’envoi avec des formulaires adaptatifs différents. Cette fonctionnalité évite la révision d’un envoi d’un utilisateur non autorisé.

Avant d’effectuer les étapes suivantes, reportez-vous à la section [Prérequis](/help/forms/using/adding-reviewers-form.md#prerequisite).

Pour créer un groupe et y ajouter des membres, accédez à **[!UICONTROL Outils > Opérations > Sécurité > Groupes]**.\
Pour plus d’informations, reportez-vous à la section [Administration utilisateur et services](/help/sites-administering/security.md).\
Veillez à ajouter le groupe que vous avez créé en tant que membre du groupe d’utilisateurs prêt à l’emploi : **réviseurs-envoi-formulaires**. Ce groupe d’utilisateurs est fourni avec AEM Forms et garantit que les utilisateurs sont ajoutés en tant que réviseurs d’envoi.

Pour associer des groupes d’utilisateurs à un formulaire adaptatif :

1. En mode création, accédez à **[!UICONTROL Formulaires > Formulaires et documents]**.
1. Utilisez l’option **[!UICONTROL Sélectionner]** pour choisir un formulaire adaptatif, puis cliquez sur **[!UICONTROL Afficher les propriétés]**.
1. Dans la fenêtre Propriétés du formulaire, cliquez sur **[!UICONTROL Modifier]** puis sur **[!UICONTROL AVANCÉ]**.
1. Saisissez le groupe dans le champ de groupe de réviseurs d’envoi, puis cliquez sur **[!UICONTROL Terminé]**.

   Le champ de groupe de réviseurs d’envoi s’affiche avec le nom spécifié dans le schéma modifié de métadonnées des formulaires adaptatifs.

>[!NOTE]
>
>Dupliquez les utilisateurs et les formulaires pour assurer leur disponibilité dans l’implémentation à distance d’AEM Forms.
>
>Veillez à ce que tous les utilisateurs soient répliqués comme membres de révision des groupes d’utilisateurs dans l’implémentation distante.
