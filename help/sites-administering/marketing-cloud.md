---
title: Intégration à Adobe Marketing Cloud
description: Découvrez comment intégrer Adobe Experience Manager à Adobe Marketing Cloud.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
exl-id: e2295f71-ea3a-483c-9d7b-29acd151845d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 58%

---

# Intégration à Adobe Marketing Cloud{#integrating-with-the-adobe-marketing-cloud}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

[Adobe Marketing Cloud](https://www.adobe.com/solutions/digital-marketing.html) inclut des produits puissants d’analyse web et d’optimisation des sites web qui proposent des données et des statistiques exploitables en temps réel pour mener à bien vos initiatives en ligne. Il constitue une plateforme ouverte et intégrée pour l’optimisation des entreprises en ligne. Le cloud est constitué d’applications intégrées permettant de collecter et de libérer la puissance des informations sur les clients afin d’optimiser les efforts d’acquisition, de conversion et de rétention des clients, ainsi que la création et la distribution de contenu.

Avec Adobe Experience Manager, vous pouvez intégrer facilement les produits Adobe Marketing Cloud suivants :

* Adobe Analytics fournit aux marketeurs des données d’analyse web exploitables et en temps réel au sujet des stratégies en ligne et des initiatives marketing.
* Adobe Target donne aux marketeurs la possibilité d’adapter continuellement leur contenu en ligne à leurs clients de manière à accroître le taux de conversion.
* Adobe Dynamic Media Classic automatise la gestion des médias, simplifie la publication web et améliore les expériences web, le tout dans un environnement hébergé.
* Adobe Dynamic Tag Management offre aux marketeurs des outils intuitifs grâce auxquels ils peuvent gérer facilement et rapidement un nombre illimité de balises Adobe et tierces.
<!-- Search&Promote was end of life September 1, 2022. * Adobe Search&Promote gives marketers the ability to control and optimize the search results on their sites. -->
* Adobe Campaign vous permet de gérer le contenu de diffusion par e-mail directement dans Adobe Experience Manager.

En outre, vous pouvez intégrer Adobe Experience Manager à la [Creative Cloud](/help/assets/aem-cc-integration-best-practices.md) et [services tiers](/help/sites-administering/third-party-services.md).

## Intégration à Adobe Analytics {#integrating-with-adobe-analytics}

[Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) est la solution leader du secteur qui fournit aux marketeurs un emplacement pour mesurer, analyser et optimiser les données intégrées de toutes les initiatives en ligne à travers plusieurs canaux marketing. Il fournit aux marketeurs des données d’analyse web en temps réel et exploitables au sujet des stratégies numériques et des initiatives marketing. Adobe Analytics permet aux marketeurs d’identifier rapidement les chemins les plus rentables d’un site web, de segmenter le trafic pour repérer les visiteurs web à forte valeur ajoutée, de déterminer où les visiteurs quittent le site et d’identifier les mesures de succès critiques pour les campagnes marketing en ligne.

Vous pouvez utiliser Adobe Analytics pour analyser les données de vos sites.

L’intégration à Adobe Analytics vous permet d’effectuer les opérations suivantes :

* Activer le suivi des utilisateurs d’Adobe Analytics
* Mappez vos modes d’exécution (par exemple, création, publication) à différentes suites de rapports.
* Envoyez les variables ClientContext en tant que variables de conversion ou propriétés de trafic.
* Utilisez des mappages de variables prédéfinis.
* Configurez toutes les sections du site à la fois.
* Suivi des événements personnalisés.

Pour plus d’informations sur l’intégration d’Adobe Experience Manager à Analytics, voir [Intégration à Adobe Analytics](/help/sites-administering/adobeanalytics.md).

Vous pouvez également utiliser l’[assistant d’accord préalable](/help/sites-administering/opt-in.md) pour exécuter facilement l’intégration.

## Intégration à Adobe Target {#integrating-with-adobe-target}

[Adobe Target](https://www.omniture.com/en/products/conversion/test-and-target) est utilisé par les spécialistes marketing pour concevoir et exécuter des tests en ligne, créer des segments ciblés à la volée (en fonction du comportement) et automatiser le ciblage du contenu et les expériences en ligne.

Les besoins des cyberconsommateurs sont aujourd’hui en constante évolution et ils attendent des très nombreux sites et sources de contenus qu’ils leur offrent des contenus pertinents, voire personnalisés. Pour séduire ce public, il est essentiel que les marketeurs identifient rapidement les offres et les contenus pertinents et attrayants pour leurs publics. Forts de ces connaissances, les marketeurs ont besoin de la capacité d’évoluer continuellement leurs sites et de cibler le contenu approprié vers différentes audiences.

[Intégration à Adobe Target](/help/sites-administering/target.md) explique comment intégrer votre site à Adobe Target.

Vous pouvez également utiliser l’[assistant d’accord préalable](/help/sites-administering/opt-in.md) pour exécuter facilement l’intégration.

## Souscription à Analytics et Target {#opting-in-to-analytics-and-target}

Adobe Experience Manager propose une procédure d’opt-in simple pour l’intégration à Adobe Analytics et Adobe Target. Lorsque vous vous connectez en tant qu’administrateur et que vous accédez à la console Projets, un assistant de souscription s’affiche.

![chlimage_1-107](assets/chlimage_1-107.png)

Souscrivez à l’intégration avec Analytics et/ou Target afin de permettre l’utilisation de leurs fonctionnalités de suivi et d’analyse des pages, ainsi que des fonctionnalités de personnalisation. Lorsque vous souscrivez, vous devez fournir les informations de votre compte utilisateur et spécifier les pages qui font l’objet d’un suivi.

Pour plus d’informations, voir [Souscription à Adobe Analytics et Adobe Target.](/help/sites-administering/opt-in.md)

## Intégration à Dynamic Media Classic {#integrating-with-scene}

Adobe Dynamic Media Classic est une solution hébergée permettant la publication, la gestion, l’enrichissement et la livraison de ressources marketing dynamiques et le merchandising visuel enrichi sur une multiplicité de canaux : web, mobiles, par e-mail, réseaux sociaux, écrans connectés à Internet et impression.

Dans Adobe Experience Manager, vous pouvez publier des ressources numériques directement d’Adobe Experience Manager vers Dynamic Media Classic et vous pouvez publier des ressources numériques de Dynamic Media Classic vers Adobe Experience Manager.

En outre, vous pouvez afficher les ressources Adobe Experience Manager publiées dans Dynamic Media Classic dans différentes visionneuses telles que le Zoom de base et la Vidéo.

Pour plus d’informations sur l’intégration d’Adobe Experience Manager à Dynamic Media Classic, voir [Intégration à Dynamic Media Classic](/help/sites-administering/scene7.md) documentation.

## Intégration à Adobe Dynamic Tag Management {#integrating-with-adobe-dynamic-tag-management}

[Adobe Dynamic Tag Management](https://www.adobe.com/fr/solutions/digital-marketing/dynamic-tag-management.html) offre aux marketeurs des outils intuitifs grâce auxquels ils peuvent gérer facilement et rapidement un nombre illimité de balises Adobe et de tierces parties. Vous pouvez optimiser pratiquement n’importe quel élément en ligne, avec une plus grande maîtrise et plus de souplesse, tout en dépendant moins des ressources informatiques.

[Intégration d’Adobe Dynamic Tag Management](/help/sites-administering/dtm.md) avec Adobe Experience Manager afin que vous puissiez utiliser vos propriétés web Dynamic Tag Management pour effectuer le suivi des sites Adobe Experience Manager.

## Intégration à Adobe Audience Manager {#integrating-with-adobe-audience-manager}

L’intégration d’Audience Manager a été supprimée dans Adobe Experience Manager 6.3.

<!-- Search&Promote was end of life September 1, 2022. ## Integrating with Search&Promote {#integrating-with-search-promote} -->

<!-- Search&Promote was end of life September 1, 2022. Adobe Search&Promote enables marketers to optimize how visitors browse, find, compare, and select relevant products and content on web and mobile sites. Businesses can easily promote priority items based on business objectives and visitor intent, as well as automate merchandising and promotions activity by way of KPI-based triggers or metrics. -->

<!-- Search&Promote was end of life September 1, 2022. Adobe Search&Promote is a reliable and scalable hosted site search application, capable of scaling to millions of pages or products, for heavily visited online businesses ranging from retail to news sites. It offers unprecedented levels of marketer control and metrics-based relevance. -->

<!-- Search&Promote was end of life September 1, 2022. For information about integrating Adobe Experience Manager and Search&Promote, see [Integrating with Adobe Search&Promote](/help/sites-administering/search-and-promote.md). -->

## Intégration à Adobe Campaign {#integrating-with-adobe-campaign}

[Adobe Campaign](https://www.adobe.com/fr/solutions/campaign-management.html) vous permet de gérer le contenu de diffusion par e-mail directement dans Adobe Experience Manager.

Pour plus d’informations sur l’intégration d’Adobe Experience Manager à Adobe Campaign, voir [Intégration à Adobe Campaign](/help/sites-administering/campaignstandard.md).
