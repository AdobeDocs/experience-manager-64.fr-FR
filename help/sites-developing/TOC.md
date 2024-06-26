---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: Guide de l’utilisateur pour le développement dans AEM 6.4
breadcrumb-title: Guide de développement
user-guide-description: Ce guide explique comment créer votre instance AEM.
feature: Developing
role: Developer
hide: true
source-git-commit: b61797a9096c0473658d6aabfb584a53e42095b7
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 98%

---


# Guide de l’utilisateur pour le développement dans AEM 6.4 {#developing}

+ [Aperçu du guide de l’utilisateur pour le développement](home.md)
+ Présentation pour l’équipe de développement{#introduction}
   + [Prise en main du développement d’AEM Sites – Tutoriel WKND ](getting-started.md)
   + [Concepts de base d’AEM](the-basics.md)
   + [Structure de l’interface utilisateur tactile d’AEM](touch-ui-structure.md)
   + [Concepts de l’interface utilisateur (IU) tactile d’AEM](touch-ui-concepts.md)
   + [Développement sur AEM – Conseils et bonnes pratiques](dev-guidelines-bestpractices.md)
   + [Utilisation de bibliothèques côté client](clientlibs.md)
   + [Développement et outil de comparaison des pages](pagediff.md)
   + [Limites de l’éditeur](editor-limitations.md)
   + [Le Framework de protection CSRF](csrf-protection.md)
   + [Modélisation de données – Modèle de David Nuescheler](model-data.md)
   + [Contribution à AEM](contributing-to-cq.md)
   + [Sécurité](security.md)
   + [Documents de référence](reference-materials.md)
   + [Création d’un site web complet (IU classique)](website.md)
   + [Conceptions et Designer (IU classique)](designer.md)
+ Platform{#platform}
   + [Aide-mémoire pour Sling](sling-cheatsheet.md)
   + [Utilisation des adaptateurs Sling](sling-adapters.md)
   + [Bibliothèques de balises](taglib.md)
   + Modèles{#templates}
      + [Modèles](templates.md)
      + [Modèles de pages – Modifiables ](page-templates-editable.md)
      + [Modèles de page - Statiques](page-templates-static.md)
      + [Modèles de fragment de contenu](content-fragment-templates.md)
      + [Rendu de modèle adaptatif](templates-adaptive-rendering.md)
   + [Utilisation de Sling Resource Merger dans AEM](sling-resource-merger.md)
   + [Recouvrements](overlays.md)
   + [Conventions de nommage](naming-conventions.md)
   + [Création d’un composant de champ d’IU Granite](granite-ui-component.md)
   + Query Builder{#query-builder}
      + [Mise en œuvre d’un évaluateur de prédicat personnalisé pour Query Builder](implementing-custom-predicate-evaluator.md)
      + [Référence des prédicats de Query Builder](querybuilder-predicate-reference.md)
      + [API Query Builder](querybuilder-api.md)
   + Balisage{#tagging}
      + [Balisage](tags.md)
      + [Framework de balisage AEM](framework.md)
      + [Création du balisage dans une application AEM](building.md)
   + [Personnalisation des pages affichées par le gestionnaire d’erreurs](customizing-errorhandler-pages.md)
   + [Types de nœuds personnalisés](custom-nodetypes.md)
   + [Ajout de polices pour le rendu graphique](adding-fonts.md)
   + [Connexion à des bases de données SQL](jdbc.md)
   + [Externalisation d’URL](externalizer.md)
   + [Création et utilisation de tâches pour le déchargement](dev-offloading.md)
   + [Configuration de l’utilisation de cookies](cookie-optout.md)
   + [Comment accéder au JCR AEM par programmation](access-jcr.md)
   + [Intégration de services à la console JMX](jmx-integration.md)
   + [Développement de l’éditeur en bloc](dev-bulk-editor.md)
   + [Élaboration de rapports](dev-reports.md)
   + eCommerce{#ecommerce}
      + [eCommerce](ecommerce.md)
      + [Développement (générique)](generic.md)
      + [Développement avec SAP Commerce Cloud](sap-commerce-cloud.md)
+ Composants{#components}
   + [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)
   + [Système de style](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/siteandpage/style-system.html?lang=fr)
   + [Aperçu des composants](components.md)
   + [Composants AEM - Notions de base](components-basics.md)
   + [Développement de composants AEM](developing-components.md)
   + [Développement de composants AEM – Échantillons de code](developing-components-samples.md)
   + [Exportateur JSON pour Content Services](json-exporter.md)
   + [Activation de l’exportateur JSON pour un composant](json-exporter-components.md)
   + [Éditeur d’image](image-editor.md)
   + [Balise décorative](decoration-tag.md)
   + [Utilisation de conditions de masquage](hide-conditions.md)
   + [Configuration de plusieurs éditeurs statiques](multiple-inplace-editors.md)
   + [Mode Développeur](developer-mode.md)
   + [Tester votre IU](hobbes.md)
   + [Composants pour les fragments de contenu](components-content-fragments.md)
   + [Obtention d’informations sur la page au format JSON](pageinfo.md)
   + Internationalisation{#internationalization}
      + [Internationalisation de composants](i18n.md)
      + [Internationalisation des chaînes d’interface utilisateur](i18n-dev.md)
      + [Utilisation du traducteur pour gérer les dictionnaires](i18n-translator.md)
      + [Extraction de chaînes pour la traduction](i18n-extract.md)
   + Composants de l’interface utilisateur classique{#classic-ui-components}
      + [Développement de composants AEM (IU classique)](developing-components-classic.md)
      + [Utilisation et extension de widgets (IU classique)](widgets.md)
      + [Utilisation des xtypes (IU classique)](xtypes.md)
      + [Développement de formulaires (IU classique)](developing-forms.md)
+ Gestion de l’expérience découplée{#headless}
   + [Sans affichage et hybride avec AEM](https://business.adobe.com/content/dam/dx/us/en/products/experience-manager/sites/headless-content-management-system/pdfs/aem-hybrid-architecture-wp-1-18-19.pdf)
   + [Activation de l’exportateur JSON pour un composant](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/json-exporter-components.html?lang=fr) 
   + Applications sur une seule page{#spas}
      + [Introduction et présentation des applications monopage (SPA)](spa-walkthrough.md)
      + [Tutoriel sur SPA WKND](spa-wknd.md)
      + [Prise en main des SPA dans AEM avec React](spa-getting-started-react.md)
      + [Prise en main des SPA dans AEM avec Angular](spa-getting-started-angular.md)
      + [Mise en œuvre d’un composant React pour SPA ](spa-implementing-react-component.md)
      + [Immersion dans les SPA](spa-deep-dives.md)
      + [Présentation de l’éditeur de SPA](spa-overview.md)
      + [Développement de SPA pour AEM](spa-architecture.md)
      + [Plan directeur d’applications sur une seule page (SPA)](spa-blueprint.md)
      + [Composant de page SPA](spa-page-component.md)
      + [Mappage dynamique de modèle à composant  pour les SPA](spa-dynamic-model-to-component-mapping.md)
      + [Routage du modèle de SPA](spa-routing.md)
      + [Intégration de SPA et d’Adobe Experience Platform Launch](spa-launch.md)
      + [SPA et rendu côté serveur (SSR) ](spa-ssr.md)
      + [Documents de référence SPA](spa-reference-materials.md)
   + [API HTTP](https://experienceleague.adobe.com/docs/experience-manager-64/assets/extending/mac-api-assets.html?lang=fr)
   + [Fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments.html)
   + [Fragments d’expérience](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/authoring/experience-fragments.html)
+ Outils de développement{#devtools}
   + [Outils de développement](dev-tools.md)
   + [Outils de modernisation d’AEM](modernization-tools.md)
   + [Éditeur de boîtes de dialogue](dialog-editor.md)
   + [Outil de conversion de boîte de dialogue](dialog-conversion.md)
   + [Développement dans CRXDE Lite](developing-with-crxde-lite.md)
   + [Gestion des packages à l’aide de Maven](vlt-mavenplugin.md)
   + [Développement de projets AEM à l’aide d’Eclipse](howto-projects-eclipse.md)
   + [Création de projets AEM à l’aide d’Apache Maven](ht-projects-maven.md)
   + [Développement de projets AEM à l’aide de IntelliJ IDEA](ht-intellij.md)
   + [Utilisation de l’outil VLT](ht-vlttool.md)
   + [Utilisation de l’outil de serveur proxy](ht-proxy-server.md)
   + [Extension AEM Brackets](aem-brackets.md)
   + [Outils de développement AEM pour Eclipse](aem-eclipse.md)
   + [Outil AEM Repo](aem-repo-tool.md)
+ Personnalisation{#personlization}
   + [ContextHub](contexthub.md)
   + [Guide de référence pour l’API JavaScript ContextHub](contexthub-api.md)
   + [Extension de ContextHub](ch-extend.md)
   + [Ajout de ContextHub à des pages et accès à des magasins](ch-adding.md)
   + [Exemples de magasins candidats ContextHub](ch-samplestores.md)
   + [Exemples de types de module d’IU ContextHub](ch-samplemodules.md)
   + [Diagnostic ContextHub](ch-diagnostics.md)
   + [Développement de composants pour du contenu ciblé](target.md)
   + ClientContext{#client-context}
      + [Présentation détaillée de ClientContext](client-context.md)
      + [API Javascript pour ClientContext](ccjsapi.md)
+ Extension d’AEM{#extending-aem}
   + [Personnalisation de la création de pages](customizing-page-authoring-touch.md)
   + [Personnalisation des consoles](customizing-consoles-touch.md)
   + [Personnalisation des vues des propriétés de la page](page-properties-views.md)
   + [Configuration d’une page pour la modification en bloc des propriétés de page](bulk-editing.md)
   + [Personnalisation et extensions de fragments de contenu](customizing-content-fragments.md)
   + Extension des workflows{#extending-workflows}
      + [Développement et extension des workflows](workflows.md)
      + [Création de modèles de workflow](workflows-models.md)
      + [Extension des fonctionnalités de workflows](workflows-customizing-extending.md)
      + [Interaction avec les workflows par programmation](workflows-program-interaction.md)
      + [Référence sur les étapes de workflow](workflows-step-ref.md)
      + [Bonnes pratiques en matière de workflow](workflows-best-practices.md)
      + [Référence sur les processus de workflow](workflows-process-ref.md)
   + [Extension du Multi-Site Manager](extending-msm.md)
   + Suivi et analyses{#extending-analytics}
      + [Extension du suivi des événements](extending-analytics.md)
      + [Ajout d’un suivi Adobe Analytics aux composants](extending-analytics-components.md)
      + [Personnalisation du framework Adobe Analytics](extending-analytics-framework.md)
      + [Implémentation de l’appellation des pages côté serveur pour Analytics](extending-analytics-pa-naming.md)
   + Services cloud{#extending-cloud-services}
      + [Configurations du service cloud](extending-cloud-config.md)
      + [Création d’un service cloud personnalisé](extending-cloud-config-custom-cloud.md)
   + [Création d’extensions personnalisées](extending-campaign-extensions.md)
   + Formulaires{#extending-forms}
      + [Création de mappages de formulaires personnalisés](extending-campaign-form-mapping.md)
      + [Création du modèle de page AEM personnalisé avec des composants de formulaire Adobe Campaign](extending-campaign-custom-template.md)
      + [Script d’analyse des requêtes](analyze-request.md)
   + [Intégration de services à la console JMX](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/jmx-integration.html?lang=fr)
   + [Développement de l’éditeur en bloc](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-bulk-editor.html?lang=fr)
   + Extension de l’interface utilisateur classique{#extending-classic-ui}
      + [Personnalisation de la console Sites web (IU classique)](customizing-siteadmin.md)
      + [Personnalisation de la console de bienvenue (IU classique)](customizing-the-welcome-console.md)
      + [Élaboration de rapports](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-reports.html?lang=fr)
+ Tests{#testing}
   + [Planification](planning.md)
   + [Quels environnements de test sont nécessaires ?](test-environments.md)
   + [Définition de cas de test](test-cases.md)
   + [Les tests - Quand et avec qui ?](when-who.md)
   + [Élaboration d’un plan de tests](test-plan.md)
   + [Suivi des résultats et formulation de commentaires](results-and-feedback.md)
   + [Outils de test et de suivi](tools.md)
   + [Acceptation et approbation](acceptance-signoff.md)
   + [La prochaine version…](the-next-release.md)
   + [Listes de contrôle](checklists.md)
   + [Tough Day](tough-day.md)
   + [Test de votre interface utilisateur](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/hobbes.html?lang=fr)
+ Bonnes pratiques{#bestpractices}
   + [Présentation des bonnes pratiques](best-practices.md)
   + [Développement sur AEM – Conseils et bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-64/developing/introduction/dev-guidelines-bestpractices.html?lang=fr)
   + [Bonnes pratiques de développement](development-practices.md)
   + [Architecture de contenu](content-architecture.md)
   + [Architecture logicielle](software-architecture.md)
   + Implémentation de référence We.Retail{#we-retail}
      + [Implémentation de référence We.Retail](we-retail.md)
      + [Test des fragments de contenu dans We.Retail](we-retail-content-fragments.md)
      + [Test des composants principaux dans We.Retail](we-retail-core-components.md)
      + [Test des modèles modifiables dans We.Retail](we-retail-editable-templates.md)
      + [Test d’une mise en page en responsive design dans We.Retail](we-retail-responsive-layout.md)
      + [Test de la structure de site globalisée dans We.Retail](we-retail-globalized-site-structure.md)
      + [Test des fragments d’expériences dans We.Retail](we-retail-experience-fragments.md)
   + [Conseils pour bien coder](coding-tips.md)
   + [Les pièges du codage](code-pitfalls.md)
   + [Lots OSGi](osgi-bundles.md)
   + [Intégration JCR](jcr-integration.md)
   + [Exemples de code](code-samples.md)
   + [Résolution des problèmes de lenteur des requêtes](troubleshooting-slow-queries.md)
+ Web mobile{#mobileweb}
   + [Web mobile](mobile-web.md)
   + [Création de filtres de groupe d’appareils](groupfilters.md)
   + [Responsive Design pour les pages web](responsive.md)
   + [Création de sites adaptés aux appareils mobiles](mobile.md)
   + [Émulateurs](emulators.md)

<!--
Deleted link to broken helpx video:
    + [Understanding Content Fragments and Content Services in AEM](https://helpx.adobe.com/experience-manager/kt/sites/using/content-fragments-content-services-feature-video-understand.html)
-->
