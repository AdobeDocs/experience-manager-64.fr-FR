---
title: AEM et les consignes pour l’accessibilité web
seo-title: AEM and the Web Accessibility Guidelines
description: Découvrez comment créer des sites web et du contenu accessibles avec AEM.
seo-description: Learn how to create accessible websites and content with AEM.
uuid: b68281af-3e8a-4842-b762-1c59f9132795
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing-accessibility, introduction
content-type: reference
discoiquuid: 13c7e0bd-54af-49f3-9743-075ce6f3314d
exl-id: f0ccdeae-3dbb-4dba-89cf-4c8b759da22b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 35%

---

# AEM et les consignes pour l’accessibilité web{#aem-and-the-web-accessibility-guidelines}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

De nombreuses motivations sociales, économiques et juridiques peuvent vous inciter à vous assurer que votre contenu web est conçu de façon à être aussi accessible que possible au public cible, quelles que soient ses situations de handicap ou ses limitations. L’accessibilité web est donc un aspect de plus en plus important d’une bonne conception web.

Création de sites web et de contenu accessibles avec un impact AEM :

* Les administrateurs chargés de configurer Adobe Experience Manager (AEM) pour assurer que les fonctions d’accessibilité sont correctement activées.
* Les auteurs utilisent ces fonctionnalités pour créer des sites web qui prennent en charge les directives clés de WCAG 2.0.

   La création de contenu accessible est un processus. AEM fournit les fonctionnalités, mais les auteurs de contenu doivent s’assurer qu’ils suivent les techniques requises pour créer du contenu accessible.

* Les développeurs de modèles doivent également être conscients de ces problèmes lors de la mise en oeuvre de la conception de site web.

## Informations supplémentaires {#further-information}

Les pages et sections suivantes contiennent des informations et des instructions :

* [Configuration de l’éditeur de texte enrichi pour produire des sites accessibles](/help/sites-administering/rte-accessible-content.md)

   Instructions relatives à la manière dont les administrateurs peuvent configurer des AEM pour produire du contenu accessible.

* [Création d’un contenu accessible (conformité WCAG 2.0)](/help/sites-authoring/creating-accessible-content.md)

   Les règles WCAG 2.0 fournissent une liste de critères de réussite pour les niveaux de conformité A et AA. Cette page détaille les critères de réussite couverts par AEM, ainsi que la manière de les satisfaire lors de la génération du contenu.

* [Guide rapide relatif à WCAG 2.0](/help/managing/qg-wcag.md)

   Informations d’arrière-plan sur WCAG 2.0.

* [Création d’un Forms adaptatif accessible](/help/forms/using/creating-accessible-adaptive-forms.md)

   Adobe Experience Manager (AEM) comprend un certain nombre de fonctions et de fonctionnalités qui améliorent la convivialité des formulaires adaptatifs pour les utilisateurs avec des fonctionnalités différentes. Cette solution aide également les auteurs à créer des formulaires adaptatifs accessibles.

## World Wide Web Consortium et WCAG 2.0 {#world-wide-web-consortium-and-wcag}

Le [World Wide Web Consortium (W3C)](https://www.w3.org/) est une communauté internationale dédiée aux normes web. Pour aider les concepteurs et les développeurs web à créer des sites web accessibles, voir [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/) publié le [Consignes relatives à l’accessibilité du contenu web (WCAG) 2.0](https://www.w3.org/TR/WCAG20/) en décembre 2008 (mise à jour de la version originale publiée en 1999).

>[!NOTE]
>
>Un [version mise à jour des instructions](https://www.w3.org/TR/WCAG21/) est actuellement en cours de développement, mais ne sera pas pris en compte pour cette version d’AEM.

Avec Adobe Experience Manager, les auteurs de contenu et/ou les propriétaires de sites web peuvent créer du contenu web qui répond aux critères de réussite des niveaux A et AA de WCAG 2.0.

Certains aspects de WCAG 2.0 sont abordés dans notre [guide rapide relatif à WCAG 2.0](/help/managing/qg-wcag.md).

### Niveaux de conformité de l’accessibilité WCAG 2.0 {#wcag-accessibility-conformance-levels}

WCAG 2.0 fournit [des instructions (avec les critères de réussite associés) couvrant les niveaux d’accessibilité ;](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html).

Celles-ci, en ce qui concerne les AEM, sont couvertes par la section [Conformité aux niveaux A et AA](/help/sites-authoring/creating-accessible-content.md). Lors de la création de votre site, vous devez déterminer à quel niveau général il doit se conformer.

>[!NOTE]
>
>Comme il n’est pas possible de satisfaire tous les critères de réussite de niveau AAA pour certains types de contenu, il n’est pas recommandé comme niveau de conformité requis.

## L’accessibilité chez Adobe  {#accessibility-at-adobe}

Pour plus d’informations, consultez le [Centre de ressources sur l’accessibilité Adobe](https://www.adobe.com/accessibility/).
