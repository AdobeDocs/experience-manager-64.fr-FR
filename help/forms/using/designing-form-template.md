---
title: Concevoir des modèles de formulaires HTML5
seo-title: Designing form templates for HTML5 forms
description: AEM Forms permet d’effectuer le rendu d’un modèle de formulaire XFA au format HTML5. Les concepteurs de formulaires peuvent créer des modèles de formulaire à l’aide de Designer et utiliser la fonction de génération de rendu au format HTML5.
seo-description: AEM Forms offers rendering XFA form template to HTML5 format. Form designers can design form templates using Designer and use the HTML5 rendition capability.
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 65%

---

# Concevoir des modèles de formulaires HTML5 {#designing-form-templates-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le composant HTML5 forms d’AEM offre le rendu du modèle de formulaire XFA au format HTML5. Les concepteurs de formulaires peuvent créer des modèles de formulaire à l’aide de [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_fr) et utiliser la fonction de génération de rendu au format HTML5. Ces modèles de formulaire, ainsi que leurs ressources, peuvent résider dans AEM référentiel, dans un système de fichiers ou dans un environnement exposé via http. Cependant, si vous envisagez de gérer vos formulaires à l’aide de Forms Manager, les modèles et ressources doivent résider dans le référentiel AEM.

Bien que les formulaires HTML5 adopteent dans une large mesure un comportement similaire à celui des formulaires PDF, il existe certaines fonctionnalités dans les deux formats qui ne s’appliquent pas dans l’autre format. Par exemple, la façon dont les codes à barres sont appliqués sur un formulaire PDF dans Adobe Reader varie par rapport à un formulaire pour appareils mobiles ; de même, la façon dont un formulaire est signé numériquement varie d’un format à l’autre. Pour plus d’informations sur ces variations, consultez la section [Différenciation des fonctions entre formulaires HTML5 et formulaires PDF](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Pour les fonctionnalités XFA courantes, consultez les bonnes pratiques et les instructions suivantes pour concevoir un formulaire qui fonctionne dans les deux formats.

## Capacités dans AEM Forms Designer pour les formulaires HTML5 {#capabilities-in-aem-forms-designer-for-html-forms}

### Prévisualiser le HTML {#preview-html}

L’onglet HTML de prévisualisation est ajouté en mode Conception pour permettre aux concepteurs de formulaires de prévisualiser les formulaires au format HTML5 pendant le processus de conception. Pour plus d’informations sur l’activation et la configuration de cette fonctionnalité dans AEM Forms Designer, voir [Prévisualiser le HTML](/help/forms/using/preview-xdp-forms-html.md).

### Signature tactile {#scribble-signature}

La cible clé pour les formulaires HTML5 est les périphériques tactiles. Par conséquent, une nouvelle commande de signature tactile est ajoutée à AEM Forms Designer. Vous pouvez cliquer ou faire glisser-déposer la commande de signature tactile sur votre modèle de formulaire et la configurer. Elle est générée sous la forme d’un champ de saisie tactile dans le rendu HTML5 et peut être utilisée pour apposer une signature tactile sur les appareils tactiles. Sur les ordinateurs de bureau, elle peut être utilisée comme un champ de saisie tactile à l’aide de la commande de souris. Pour plus d’informations sur l’utilisation de cette fonctionnalité, consultez la section [Champ de saisie tactile XFA](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
