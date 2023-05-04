---
title: Présentation des formulaires HTML5
seo-title: Introduction to HTML5 forms
description: Les formulaires HTML5 sont une nouvelle fonctionnalité du logiciel Adobe Experience Manager 6.0 (AEM 6.0) qui offre le rendu des modèles de formulaires XFA au format HTML5.
seo-description: HTML5 forms is a new capability in Adobe Experience Manager 6.0 (AEM 6.0) software that offers rendering of XFA form templates in HTML5 format.
uuid: a68f1ca1-32dd-48f9-9359-8f09abd1c3de
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: b8cd2656-8bc2-4bd7-a3d6-dc76b0a2d429
feature: Mobile Forms
exl-id: c69b5ae6-c5c5-46df-8290-3e41470cd09e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 48%

---

# Présentation des formulaires HTML5 {#introduction-to-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les formulaires HTML5 sont une nouvelle fonctionnalité du logiciel Adobe Experience Manager 6.0 (AEM 6.0) qui offre le rendu des modèles de formulaires XFA au format HTML5. Cette fonctionnalité permet le rendu des formulaires sur les périphériques mobiles et les navigateurs de bureau ne prenant pas en charge les documents XFA en PDF. Les formulaires HTML5 prennent non seulement en charge les fonctionnalités existantes des modèles de formulaires XFA, mais ajoutent également de nouvelles fonctionnalités, telles que la signature tactile, pour les appareils mobiles.

Les formulaires HTML5 génèrent des documents basés sur des éléments HTML5 standards. Vous pouvez afficher les formulaires HTML5 dans tous les navigateurs récents prenant en charge le format HTML5. Il n’est pas nécessaire d’installer de module externe de navigateur supplémentaire pour les navigateurs. Pour plus d’informations sur les navigateurs pris en charge, consultez la section [Plateformes clientes prises en charge](https://adobe.com/go/learn_aemforms_supportedplatforms_63_fr).

![](do-not-localize/mobile_form_on_an_ipad_date_14.png)

## Fonctionnalités essentielles des formulaires HTML5 {#key-capabilities-of-html-forms-br}

* Rendu des formulaires XFA existants dans HTML5 pris en charge sur tous les navigateurs compatibles.
* tire parti des fonctionnalités standard de conception de formulaire XFA pour cibler des formulaires pour les périphériques mobiles.
* Utilise les fonctionnalités XFA dynamiques au format HTML5.
* Utilise une disposition de texte de SVG très précise (SVG 1.1) pour correspondre à la disposition de texte de PDF.
* Prise en charge de Javascript et de FormCalc.
* Assemblage dynamique de fragments dans des formulaires interactifs en fonction d’événements pilotés par les données ou d’entrées utilisateur.
* Prise en charge des CSS personnalisées pour correspondre à l’apparence des formulaires selon les normes de votre entreprise.
* Permet aux widgets personnalisés d’offrir une expérience de capture de données riche.
* Prise en charge de l’intégration avec des applications Web.

### Publication multicanal {#multichannel-publishing}

Les développeurs de formulaires peuvent utiliser un modèle XFA pour générer des formulaires aux formats PDF et HTML5. Cette fonctionnalité peut s’avérer utile dans les cas où vous avez un jeu de formulaires XFA important nécessitant des modifications mineures pour s’adapter aux pratiques de conception des formulaires HTML5. Vous pouvez rendre les formulaires XFA existants sur HTML5 pour cibler divers périphériques pour lesquels le PDF basé sur XFA n’est pas encore pris en charge.

## Gestion des formulaires HTML5 {#manage-html-forms}

AEM fournit également un affichage unifié permettant de répertorier et gérer tous les modèles de formulaires à l’aide de l’interface utilisateur AEM Forms. Vous pouvez activer, désactiver, publier et prévisualiser des formulaires. Pour plus d’informations, voir [Présentation de la gestion des formulaires](/help/forms/using/introduction-managing-forms.md).

### Personnalisation de Forms {#forms-customization}

Mobile Forms effectue le rendu des modèles de formulaires à l’aide d’éléments HTML5 standard. Cela facilite la personnalisation et l’extension de formulaires au format HTML5 à l’aide de technologies web, principalement CSS et JavaScript. Vous pouvez facilement personnaliser l’aspect des widgets existants, créer vos propres widgets personnalisés ou utiliser des styles personnalisés dans les formulaires. Pour plus d’informations sur la création de widgets personnalisés et la personnalisation de widgets existants, consultez la section [Ajout de widgets personnalisés aux formulaires HTML5](/help/forms/using/custom-widgets.md).
