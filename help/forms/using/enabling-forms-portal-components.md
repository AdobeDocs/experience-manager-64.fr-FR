---
title: Activation des composants du portail Formulaires
seo-title: Enabling forms portal components
description: Les composants Forms Portal prêts à l’emploi sont désactivés. Activez les groupes Services de document et Prédicats de services de document pour activer les composants du portail Forms.
seo-description: Out of the box, Forms Portal components are disabled. Enable Document Services and Document Services Predicates groups to enable Forms Portal components.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
feature: Forms Portal
exl-id: 01c5eb6b-b097-4354-84b2-8bee7b7626f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 72%

---

# Activation des composants du portail Formulaires {#enabling-forms-portal-components}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les composants Forms Portal prêts à l’emploi ne sont pas disponibles. Pour que les composants apparaissent dans la liste des composants disponibles dans AEM sidekick, procédez comme suit :

1. Connectez-vous à l’instance d’auteur de votre site web et ouvrez une page AEM Sites.

1. Pour les pages utilisant un modèle statique, procédez comme suit :

   1. Dans l’en-tête de la page, appuyez sur ![menu déroulant Canvas](assets/canvas-drop-down.png) > **Conception** pour ouvrir la page en mode Conception.
   1. Cliquez sur n’importe quel composant (avec une bordure bleue), puis cliquez sur ![field-level](assets/field-level.png) pour sélectionner le système de paragraphe contenant le composant actif.
   1. Dans le système de paragraphe, appuyez sur ![settings-icon](assets/settings_icon.png) pour ouvrir la boîte de dialogue d’édition pour le système de paragraphe.
   1. Dans la liste **[!UICONTROL Composants autorisés]**, cochez les cases des composants **[!UICONTROL Services de document]** et **[!UICONTROL Prédicats de services de document]**. Appuyez sur **[!UICONTROL OK]**.

1. Pour les pages utilisant un modèle dynamique, procédez comme suit :

   1. Dans l’en-tête de la page, appuyez sur ![Propriétés](assets/properties.png) > **Modifier le modèle** pour ouvrir le modèle de la page.
   1. Appuyez sur **Conteneur de présentation** et appuyez sur ![FeedManagement](assets/FeedManagement.png). Dans l’onglet **Composants autorisés**, activez les options **Services de documents et Prédicats de services de documents** (Prédicats de services de document), puis sur ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>Vous pouvez également activer des composants spécifiques de ces catégories en les sélectionnant. Pour plus d’informations sur les composants et leur utilisation, voir [Création d’une page de portail de formulaires](/help/forms/using/creating-form-portal-page.md) et [Incorporation du composant Link dans une page](/help/forms/using/embedding-link-component-page.md).

Désormais, les catégories de composant Services de document et Prédicats de services de document sont disponibles dans l’explorateur de composants. Les composants sont activés pour toutes les pages qui utilisent le même modèle.

## Articles connexes

* [Activer des composants du portail Formulaires](/help/forms/using/enabling-forms-portal-components.md)
* [Créer une page du portail Formulaires](/help/forms/using/creating-form-portal-page.md)
* [Affichage de la liste des formulaires sur une page Web à l’aide d’API](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Utiliser le composant Brouillons et Envois](/help/forms/using/draft-submission-component.md)
* [Personnaliser le stockage des brouillons de formulaires et des formulaires envoyés](/help/forms/using/draft-submission-component.md)
* [Exemple d’intégration d’un composant brouillons &amp; envois à la base de données](/help/forms/using/integrate-draft-submission-database.md)
* [Personnalisation de modèles pour les composants Forms Portal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Présentation de la publication de formulaires sur un portail](/help/forms/using/introduction-publishing-forms.md)
