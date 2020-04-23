---
title: Conception de modèles de formulaires HTML5
seo-title: Conception de modèles de formulaires HTML5
description: 'AEM Forms permet d’effectuer le rendu d’un modèle de formulaire XFA au format HTML5. Les concepteurs de formulaires peuvent concevoir des modèles de formulaire à l’aide de Designer et utiliser la fonction de génération de rendu au format HTML5. '
seo-description: 'AEM Forms permet d’effectuer le rendu d’un modèle de formulaire XFA au format HTML5. Les concepteurs de formulaires peuvent concevoir des modèles de formulaire à l’aide de Designer et utiliser la fonction de génération de rendu au format HTML5. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Conception de modèles de formulaires HTML5 {#designing-form-templates-for-html-forms}

Le composant Formulaires HTML5 dans AEM permet de générer le rendu du modèle de formulaire XFA au format HTML5. Les concepteurs de formulaires peuvent créer des modèles de formulaire à l’aide de [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) et utiliser la fonction de génération de rendu au format HTML5. Ces modèles de formulaire, ainsi que leurs ressources, peuvent résider dans le référentiel AEM, un système de fichiers, ou sont accessibles via http. Toutefois, si vous prévoyez de gérer vos formulaires à l’aide de Forms Manager, les modèles et les ressources doivent résider dans le référentiel AEM.

Bien que les formulaires HTML5 adopteent dans une large mesure un comportement similaire à celui des formulaires PDF, il existe certaines fonctionnalités dans les deux formats qui ne s’appliquent pas dans l’autre format. Par exemple, la manière dont les codes à barres sont appliqués à un formulaire PDF dans Adobe Reader varie d’un formulaire pour périphériques mobiles ou la manière dont un formulaire est signé numériquement varie également d’un format à l’autre. For more information on such variations, see [Feature differentiation between HTML5 forms and PDF Forms](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Pour les fonctionnalités XFA courantes, consultez les meilleures pratiques et les directives suivantes pour concevoir un formulaire compatible avec les deux formats.

## Capacités dans AEM Forms Designer pour les formulaires HTML5 {#capabilities-in-aem-forms-designer-for-html-forms}

### Aperçu HTML {#preview-html}

L’onglet Aperçu HTML est ajouté au mode de création pour permettre aux concepteurs de formulaires de prévisualiser les formulaires au format HTML5 au cours du processus de création. Pour plus d’informations sur la procédure à suivre pour activer et configurer cette fonctionnalité dans AEM Forms Designer, voir [Aperçu HTML](/help/forms/using/preview-xdp-forms-html.md).

### Signature à main levée {#scribble-signature}

L’objectif clé des formulaires HTML5 est les périphériques tactiles. Par conséquent, une nouvelle commande de signature tactile est ajoutée à AEM Form Designer. Vous pouvez cliquer ou faire glisser et déposer le contrôle de signature tactile sur votre modèle de formulaire et le configurer. Il est rendu sous forme de champ de saisie tactile dans le rendu HTML5 et peut être utilisé pour apposer une signature tactile sur les périphériques tactiles. Sur les ordinateurs de bureau, elle peut être utilisée comme un champ de saisie tactile à l’aide de la commande de souris. For more information on how to use this feature, see [XFA Scribble Field](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
