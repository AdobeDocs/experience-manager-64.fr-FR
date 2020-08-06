---
title: FAQ sur AEM
seo-title: Questions courantes sur AEM 6.4
description: Utilisez ces FAQ pour comprendre, configurer, et résoudre les problèmes ou les workflows courants dans AEM.
seo-description: Utilisez ces FAQ pour comprendre, configurer, et résoudre les problèmes ou les workflows courants dans AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 49%

---


# FAQ sur AEM{#aem-faqs}

Suivez cette page pour obtenir des réponses à certains problèmes AEM de dépannage et de configuration.

## Sites {#sites}

### How do I configure binary-less distribution? {#how-do-i-configure-binary-less-distribution}

La distribution sans fichier binaire est prise en charge pour les déploiements dans un entrepôt de données partagé et implique des agents qui exploitent le créateur de modules de l’exportateur de modules de distribution basé sur le coffre-fort (PID d’usine : `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`).

Le mode sans fichier binaire étant activé, les modules de contenu distribués contiennent des références à des fichiers binaires plutôt que des fichiers binaires réels.

### Comment activer la distribution sans fichier binaire ? {#how-do-i-enable-binary-less-distribution}

Pour activer la distribution sans fichier binaire, déployez un entrepôt de grands objets binaires partagé.\
Check the `useBinaryReferences` property in the OSGI configuration with the factory PID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*that your agent is using.

### How can I customize the error messages while navigating page hierarchy in AEM sites console? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Vérifiez le panneau Réseau (du navigateur Chrome), qui contient une configuration personnelle (JavaScript n’a pas été compressé).

View the `Initiator` column to determine what the initiator of a request was. Elle indique les fichiers et les numéros de ligne correspondant aux appels AJAX effectués. Ensuite, vous pouvez suivre la fonction de gestion des erreurs et modifier le message d’erreur selon vos besoins.

### Comment activer les autorisations tout en créant une copie de langue pour les créateurs de contenu dans AEM ? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

To create language copy feature, content-authors need permissions at `/content/projects` location.

If one requires the authors to manage projects as well, then the workaround is to add the author to `project-administrators` group.

### How to change the format while creating Language Copy for a project? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Avant de créer un projet de traduction, créez une racine de langue et une copie de langue dans la racine.

Par exemple :\
Create a language root at `/content/geometrixx` with name as `fr_LU` (and title as French (Luxembourg)). Par la suite, créez une copie de langue de la page à partir du panneau des références et accédez à l’ `Create structure only` option dans `Create & Translate`. Enfin, créez un projet de traduction, puis ajoutez la copie de langue à la tâche de traduction.

Pour plus d’informations, reportez-vous aux ressources supplémentaires ci-dessous :

* [Préparation du contenu à traduire](/help/sites-administering/tc-prep.md)
* [Gestion des projets de traduction](/help/sites-administering/tc-manage.md)

### Comment auditer les fonctionnalités d’AEM telles que les tentatives de connexion et ACL ou les modifications d’autorisation ? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM permet de consigner les modifications administratives pour améliorer les audits et la résolution des problèmes. By default, the information is logged in the `error.log` file. Pour faciliter la surveillance, il est recommandé de les rediriger vers un fichier journal distinct.\
Pour rediriger la sortie vers un fichier journal distinct, consultez [Comment auditer les opérations de gestion des utilisateurs dans AEM](/help/sites-administering/audit-user-management-operations.md).

### How to enable SSL by default? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 contient un assistant SSL et propose une interface utilisateur pour configurer la prise en charge de Jetty et Granite Jetty SSL.

Pour activer SSL par défaut, voir [SSL par défaut](/help/sites-administering/ssl-by-default.md).

### Quelle est l’architecture recommandée lors de l’utilisation des services de contenu d’AEM depuis une application mobile, idéalement React Native ? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Content Services est basé sur les modèles Sling et les développeurs AEM doivent fournir un profil de modèle Sling pour chaque composant exporté.

Pour comprendre comment consommer des services de contenu d’AEM depuis une application React, consultez le tutoriel [Prise en main des services de contenu AEM](https://helpx.adobe.com/fr/experience-manager/kt/sites/using/content-services-tutorial-use.html).

Also, if the developers want to export a tree of components they can also implement the `ComponentExporter` and `ContainerExporter` interfaces as well as use the `ModelFactory` to iterate over the child components and return their model representation. Consultez les ressources ci-dessous :

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling : Modèles Sling](https://sling.apache.org/documentation/bundles/models.html)

### How to disable AEM 6.4 survey pop-up? {#how-to-disable-aem-survey-pop-up}

Vous pouvez souscrire à la collecte de statistiques d’utilisation à l’aide de l’IU tactile ou de la console web. Pour des instructions détaillées, consultez [Souscription à la collecte de statistiques d’utilisation agrégées](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### Existe-t-il une bonne ressource qui explique les fonctionnalités clés dans le cas d’une mise à niveau vers AEM 6.4 ? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Refer to [Understanding Reasons to Upgrade AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) that describes high-level breakdown of key features for customers considering upgrading to the latest version of Adobe Experience Manager.

### Comment configurer une instance AEM pour utiliser le filtre PorterStem ? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

Le filtre PorterStem applique l&#39;algorithme de recherche Porter pour l&#39;anglais. Les résultats sont similaires à l&#39;utilisation du Snowball Porter Stemmer avec l&#39;argument *language=&quot;English&quot;* . Mais ce tige est codé directement en Java et n&#39;est pas basé sur Snowball. Il n&#39;accepte pas une liste de mots protégés et n&#39;est approprié que pour le texte en anglais.

Oak expose un ensemble d&#39;éléments de configuration de l&#39;analyseur lucene-fournit à utiliser dans AEM. Pour savoir comment utiliser les filtres, reportez-vous aux analyseurs **de chêne** Apache dans le guide [de mise en oeuvre de la recherche](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)simple.

### Comment procéder à une réindexation complète ? {#how-to-perform-a-full-re-indexing}

La réindexation doit toujours être envisagée en tenant compte de son impact sur les performances globales d’AEM et être réalisée pendant les périodes de faible activité ou de maintenance.

Consultez les [Bonnes pratiques relatives aux Requêtes et à l’indexation](/help/sites-deploying/best-practices-for-queries-and-indexing.md) pour comprendre les raisons de la réindexation.

### Prenons-nous en charge les bibliothèques JS minifiées dans l’importateur de conception ? {#do-we-support-minified-js-libs-in-design-importer}

Vous devez modifier la propriété de configuration par défaut du processeur JS de l’Adobe Granite HTML Library Manager en ***min:gcc***. Pour importer le pack de conception avec succès, il est recommandé d’inclure des bibliothèques tierces préminifiées dans nos bibliothèques côté client.

## Ressources {#assets}

### Why the Assets workflow repeats itself while uploading MP4 files (for example, using drag-and-drop method)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Lorsqu’un utilisateur charge les fichiers vidéo, s’il ne dispose pas des autorisations de suppression sous le nœud des actifs, la suppression des nœuds de bloc échoue et le chargement recommence.

### Quel est le nombre maximal de ressources numériques pouvant être gérées simultanément par AEM 6.4 ? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager (AEM) 6.4 permet actuellement de charger jusqu’à 2 Go de ressources à la fois.

Pour des informations supplémentaires sur le nombre maximal de ressources pouvant être gérées par AEM 6.4, voir le [guide des tailles Assets](/help/assets/assets-sizing-guide.md).

### Quels sont les paramètres par défaut pour les configurations prêtes à l’emploi lors de la création d’une copie de langue ? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Lors de la création de copies de langue par le biais de l’IU classique, les ressources ne sont pas déplacées sous la nouvelle hiérarchie de langue. Elles sont plutôt utilisées par le gabarit de langue.

En revanche, lorsque vous créez une copie de langue par le biais de l’IU optimisée pour les écrans tactiles (**Références** ->**Mettre à jour la copie de langue**), un nouveau dossier DAM est créé sous la nouvelle langue et les ressources sont référencées à partir de cet emplacement.

Il s’agit du paramètre par défaut pour les configurations prêtes à l’emploi. Vous pouvez définir **Traduire les ressources de page** sur **Ne pas traduire** dans les configurations de traduction.\
Pour AEM 6.4, **Outils** > **Services cloud** > **Services cloud de traduction**.

### How to disable an AEM component causing exponential growth for the AEM SegmentStore (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Vous pouvez désactiver OSGi Component Disabler. Pour utiliser ce service, voir [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Comme solution, vous pouvez également désactiver manuellement le composant via l’IU ou une commande `curl` (exemple ci-dessous) après chaque redémarrage d’AEM.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### How to configure Asset Insights with AEM 6.4 instance? {#how-to-configure-asset-insights-with-aem-instance}

To setup and configure Asset Insights for Experience Manager deployed via Adobe Activation (DTM), refer to [Set up Asset Insights with AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### How to customize admin consoles? {#how-to-customize-admin-consoles}

AEM fournit divers mécanismes permettant de personnaliser les consoles et les fonctionnalités de création de page de votre instance de création.
To learn how to create a custom console and customize a default view for a console, refer to [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md).

### What is the difference between CoralUI 2 and CoralUI 3-based components? {#what-is-the-difference-between-coralui-and-coralui-based-components}

A new set of Sling components of Granite UI Foundation is created for Coral3 and is located under [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Un jeu est adapté aux composants basés sur CoralUI 2 et un autre à ceux basés sur CoralUI 3. Le nouveau jeu ne sera pas simplement un copier-coller de l’ancien, mais il sera nettoyé (par exemple en simplifiant et en supprimant les fonctionnalités abandonnées). Il est donc recommandé qu’une page utilise un jeu basé uniquement soit sur CoralUI 3 soit sur CoralUI 2.

To learn more in detail, refer to [Migration Guide to CoralUI 3-based](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### How to customize the search component in AEM Assets? {#how-to-customize-the-search-component-in-aem-assets}

To learn about search boost/ranking and further implementation information, refer to [Simple search implementation guide.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

La mise en œuvre de recherche simple est le matériel du Summit Lab AEM Search Demystified 2017.

### Si un client achète uniquement la licence Sites dans AEM, a-t-il toujours accès aux ressources ? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

Non, le client ne peut pas accéder aux ressources (ou à tout autre élément que Sites). Même si tous les éléments Adobe Experience Manager (AEM) sur site sont inclus dans le JAR, le client n’est autorisé à accéder qu’aux composants du JAR pour lesquels il est titulaire d’une licence dans son contrat. S&#39;ils veulent explorer d&#39;autres composants, ils peuvent utiliser le programme d&#39;évaluation AEM pendant 45 jours au maximum ou signer une commande client de 0 € qui les autorise à évaluer (sans utilisation de production) des composants nommés tels que Actifs.

Consultez les ressources suivantes pour en savoir plus sur les logiciels AEM sur site et les services gérés Adobe :

* [Logiciel Adobe Experience Manager sur site](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### Comment un client peut-il étendre les propriétés par défaut d’une page ou d’une ressource ? {#how-to-extend-default-properties-page-or-asset}

Pour en savoir plus sur l’extension des propriétés par défaut d’une page ou d’une ressource, consultez les ressources ci-dessous :

* [Schémas de métadonnées dans les ressources](/help/assets/metadata-schemas.md)
* [Personnalisation des vues des propriétés de la page](/help/sites-developing/page-properties-views.md)
