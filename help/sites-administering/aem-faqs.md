---
title: FAQ sur AEM
seo-title: AEM 6.4 frequently asked questions
description: Utilisez ces FAQ pour comprendre, configurer, et résoudre les problèmes ou les workflows courants dans AEM.
seo-description: Use these FAQs to understand, configure, and troubleshoot common workflows or issues in AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
exl-id: 76110cf4-0fd8-4203-b256-c0818a1b64d2
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 55%

---

# FAQ sur AEM{#aem-faqs}

Consultez cette page pour obtenir des réponses à certains problèmes AEM de dépannage et de configuration.

## Sites {#sites}

### Comment configurer une distribution sans fichier binaire ? {#how-do-i-configure-binary-less-distribution}

La distribution sans fichier binaire est prise en charge pour les déploiements dans un entrepôt de données partagé et implique des agents qui exploitent le créateur de modules de l’exportateur de modules de distribution basé sur le coffre-fort (PID d’usine : `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`).

Le mode sans fichier binaire étant activé, les modules de contenu distribués contiennent des références à des fichiers binaires plutôt que des fichiers binaires réels.

### Comment activer la distribution sans fichier binaire ? {#how-do-i-enable-binary-less-distribution}

Pour activer la distribution sans fichier binaire, déployez un entrepôt de grands objets binaires partagé.\
Vérifiez les `useBinaryReferences` dans la configuration OSGI avec le PID d’usine ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* que votre agent utilise.

### Comment personnaliser les messages d’erreur en parcourant l’arborescence des pages dans la console AEM Sites ? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Vérifiez le panneau Réseau (du navigateur Chrome), qui contient une configuration personnelle (JavaScript n’a pas été compressé).

Afficher la variable `Initiator` pour déterminer l’initiateur d’une requête. Elle indique les fichiers et les numéros de ligne correspondant aux appels AJAX effectués. Ensuite, vous pouvez suivre la fonction de gestion des erreurs et modifier le message d’erreur selon vos besoins.

### Comment activer les autorisations tout en créant une copie de langue pour les créateurs de contenu dans AEM ? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Pour créer une fonction de copie de langue, les auteurs de contenu doivent disposer d’autorisations à l’adresse `/content/projects` emplacement.

Si les auteurs doivent également gérer des projets, la solution consiste à ajouter l’auteur à `project-administrators` groupe.

### Comment modifier le format lors de la création d’une copie de langue pour un projet ? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Avant de créer un projet de traduction, créez une racine de langue et une copie de langue dans la racine.

Par exemple,\
Créez une racine de langue à l’adresse `/content/geometrixx` avec le nom `fr_LU` (et titre en français (Luxembourg)). Ensuite, créez une copie de langue de la page à partir du panneau Références et accédez à `Create structure only` dans `Create & Translate`. Enfin, créez un projet de traduction, puis ajoutez la copie de langue à la tâche de traduction.

Pour plus d’informations, reportez-vous aux ressources supplémentaires ci-dessous :

* [Préparation du contenu à traduire](/help/sites-administering/tc-prep.md)
* [Gestion des projets de traduction](/help/sites-administering/tc-manage.md)

### Comment auditer les fonctionnalités d’AEM telles que les tentatives de connexion et ACL ou les modifications d’autorisation ? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM permet de consigner les modifications administratives pour améliorer les audits et la résolution des problèmes. Par défaut, les informations sont consignées dans la variable `error.log` fichier . Pour faciliter la surveillance, il est recommandé de les rediriger vers un fichier journal distinct.\
Pour rediriger la sortie vers un fichier journal distinct, consultez [Comment auditer les opérations de gestion des utilisateurs dans AEM](/help/sites-administering/audit-user-management-operations.md).

### Comment activer SSL par défaut ? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 contient un assistant SSL et propose une interface utilisateur pour configurer la prise en charge de Jetty et Granite Jetty SSL.

Pour activer SSL par défaut, voir [SSL par défaut](/help/sites-administering/ssl-by-default.md).

### Quelle est l’architecture recommandée lors de l’utilisation des services de contenu d’AEM depuis une application mobile, idéalement React Native ? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Les services de contenu sont basés sur les modèles Sling et les développeurs d’AEM doivent fournir un graphique de modèle Sling pour chaque composant exporté.

Pour comprendre comment consommer des services de contenu d’AEM depuis une application React, consultez le tutoriel [Prise en main des services de contenu AEM](https://helpx.adobe.com/fr/experience-manager/kt/sites/using/content-services-tutorial-use.html).

En outre, si les développeurs souhaitent exporter une arborescence de composants, ils peuvent également mettre en oeuvre la variable `ComponentExporter` et `ContainerExporter` mais aussi utiliser la fonction `ModelFactory` pour effectuer une itération sur les composants enfants et renvoyer leur représentation de modèle. Consultez les ressources ci-dessous :

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling : Modèles Sling](https://sling.apache.org/documentation/bundles/models.html)

### Comment désactiver la fenêtre contextuelle d’enquête d’AEM 6.4 ? {#how-to-disable-aem-survey-pop-up}

Vous pouvez souscrire à la collecte de statistiques d’utilisation à l’aide de l’IU tactile ou de la console web. Pour des instructions détaillées, consultez [Souscription à la collecte de statistiques d’utilisation agrégées](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### Existe-t-il une bonne ressource qui explique les fonctionnalités clés dans le cas d’une mise à niveau vers AEM 6.4 ? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Voir [Comprendre les raisons de la mise à niveau AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) qui décrit la ventilation de haut niveau des fonctionnalités clés pour les clients qui envisagent d’effectuer une mise à niveau vers la dernière version d’Adobe Experience Manager.

### Comment configurer une instance AEM pour utiliser le filtre PorterStem ? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

Le filtre PorterStem applique l’algorithme de test Porter pour l’anglais. Les résultats sont similaires à l’utilisation de l’événement Snowball Porter avec la méthode *language=&quot;English&quot;* argument . Mais ce radical est codé directement en Java et n’est pas basé sur Snowball. Il n’accepte pas la liste des mots protégés et n’est approprié que pour le texte en anglais.

Oak expose un ensemble d’éléments de configuration de l’analyseur Lucene-fournit à utiliser dans AEM. Pour savoir comment utiliser les filtres, reportez-vous à la section **Analyseurs Apache Oak** in [Guide de mise en oeuvre de recherche simple](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

### Comment effectuer une réindexation complète ? {#how-to-perform-a-full-re-indexing}

La réindexation doit toujours être envisagée en tenant compte de son impact sur les performances globales d’AEM et être réalisée pendant les périodes de faible activité ou de maintenance.

Reportez-vous à la section [Bonnes pratiques relatives aux requêtes et à l’indexation](/help/sites-deploying/best-practices-for-queries-and-indexing.md) pour comprendre les raisons de la réindexation.

### Prenons-nous en charge les bibliothèques JS minifield dans l’importateur de conception ? {#do-we-support-minified-js-libs-in-design-importer}

Vous devez modifier la propriété de configuration par défaut du processeur JS du Gestionnaire de bibliothèques de HTMLS Adobe Granite en ***min:gcc***. Pour importer le module de conception avec succès, il est recommandé d’inclure des bibliothèques tierces préminifiées dans nos bibliothèques côté client.

## Ressources {#assets}

### Pourquoi le workflow des ressources se répète-t-il lors du chargement de fichiers MP4 (par exemple, par glisser-déposer) ? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Lorsqu’un utilisateur charge les fichiers vidéo, s’il ne dispose pas des autorisations de suppression sous le nœud des actifs, la suppression des nœuds de bloc échoue et le chargement recommence.

### Quel est le nombre maximal de ressources numériques pouvant être gérées simultanément par AEM 6.4 ? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager (AEM) 6.4 permet actuellement de charger jusqu’à 2 Go de ressources à la fois.

Pour des informations supplémentaires sur le nombre maximal de ressources pouvant être gérées par AEM 6.4, voir le [guide des tailles Assets](/help/assets/assets-sizing-guide.md).

### Quels sont les paramètres par défaut pour les configurations prêtes à l’emploi lors de la création d’une copie de langue ? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Lors de la création de copies de langue par le biais de l’IU classique, les ressources ne sont pas déplacées sous la nouvelle hiérarchie de langue. Elles sont plutôt utilisées par le gabarit de langue.

En revanche, lorsque vous créez une copie de langue par le biais de l’IU optimisée pour les écrans tactiles (**Références** ->**Mettre à jour la copie de langue**), un nouveau dossier DAM est créé sous la nouvelle langue et les ressources sont référencées à partir de cet emplacement.

Il s’agit du paramètre par défaut pour les configurations prêtes à l’emploi. Vous pouvez définir **Traduire les ressources de page** sur **Ne pas traduire** dans les configurations de traduction.\
Pour AEM 6.4, **Outils** > **Services cloud** > **Services cloud de traduction**.

### Comment désactiver un composant AEM entraînant la croissance exponentielle de SegmentStore AEM (AEM 6.3.1.1) ? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Vous pouvez désactiver OSGi Component Disabler. Pour utiliser ce service, voir [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Comme solution, vous pouvez également désactiver manuellement le composant via l’IU ou une commande `curl` (exemple ci-dessous) après chaque redémarrage d’AEM.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### Comment configurer Assets Insights avec l’instance AEM 6.4 ? {#how-to-configure-asset-insights-with-aem-instance}

Pour configurer Assets Insights pour le Experience Manager déployé via Adobe Activation (DTM), reportez-vous à la section [Configuration des statistiques sur les ressources avec AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### Comment personnaliser les consoles d’administration ? {#how-to-customize-admin-consoles}

AEM fournit divers mécanismes pour vous permettre de personnaliser les consoles et les fonctionnalités de création de page de votre instance de création.
Pour savoir comment créer une console personnalisée et personnaliser une vue par défaut pour une console, reportez-vous à la section [Personnalisation des consoles](/help/sites-developing/customizing-consoles-touch.md).

### Quelle est la différence entre les composants basés sur CoralUI 2 et CoralUI 3 ? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Un nouvel ensemble de composants Sling de Granite UI Foundation est créé pour Coral3 et se trouve sous [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Un jeu est adapté aux composants basés sur CoralUI 2 et un autre à ceux basés sur CoralUI 3. Le nouveau jeu ne sera pas simplement un copier-coller de l’ancien, mais il sera nettoyé (par exemple en simplifiant et en supprimant les fonctionnalités abandonnées). Il est donc recommandé qu’une page utilise un jeu basé uniquement soit sur CoralUI 3 soit sur CoralUI 2.

Pour en savoir plus, reportez-vous à la section [Guide de migration vers CoralUI 3](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### Comment personnaliser le composant de recherche dans AEM Assets ? {#how-to-customize-the-search-component-in-aem-assets}

Pour en savoir plus sur l’amplification/le classement des recherches et les informations supplémentaires sur l’implémentation, reportez-vous à la section [Guide de mise en oeuvre de la recherche simple.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

La mise en œuvre de recherche simple est le matériel du Summit Lab AEM Search Demystified 2017.

### Si un client achète uniquement la licence Sites dans AEM, a-t-il toujours accès à Assets ? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

Non, le client ne peut pas accéder aux ressources (ou à tout autre élément que Sites). Même si tous les composants Adobe Experience Manager (AEM) On-Premise sont inclus dans le fichier JAR, le client n’est autorisé à accéder qu’aux composants du fichier JAR pour lesquels il détient une licence dans le cadre de son contrat. S’ils souhaitent explorer d’autres composants, ils peuvent utiliser le programme d’évaluation AEM pendant 45 jours au maximum ou signer une commande de ventes de 0 $ qui les autorise à évaluer (sans utilisation en production) les composants nommés tels que Ressources.

Pour en savoir plus sur AEM logiciel On-premise et Adobe Managed Services, reportez-vous aux ressources suivantes :

* [Logiciel Adobe Experience Manager On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### Comment un client peut-il étendre les propriétés par défaut d’une page ou d’une ressource ? {#how-to-extend-default-properties-page-or-asset}

Pour en savoir plus sur l’extension des propriétés par défaut d’une page ou d’une ressource, reportez-vous aux ressources ci-dessous :

* [Schémas de métadonnées dans Assets](/help/assets/metadata-schemas.md)
* [Personnalisation des vues des propriétés de la page](/help/sites-developing/page-properties-views.md)
