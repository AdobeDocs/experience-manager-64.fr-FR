---
title: Notes de mise à jour générales d’Adobe Experience Manager 6.4
seo-title: Notes de mise à jour
description: 'Notes relatives à Adobe Experience Manager 6.4, décrivant les informations de version, les nouveautés et le processus d’installation, et détaillant les modifications. '
seo-description: 'Notes relatives à Adobe Experience Manager 6.4, décrivant les informations de version, les nouveautés et le processus d’installation, et détaillant les modifications. '
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
translation-type: tm+mt
source-git-commit: 2411f1aa2853a161603d15917102d5cf1a8139b6

---


# Notes de mise à jour générales d’Adobe Experience Manager 6.4 {#general-release-notes-for-adobe-experience-manager}

## Informations sur la version {#release-information}

<table> 
 <tbody>
  <tr>
   <th>Produit</th> 
   <td>Adobe Experience Manager  <br /> </td> 
  </tr>
  <tr>
   <th>Version</th> 
   <td>6.4</td> 
  </tr>
  <tr>
   <th>Type</th> 
   <td>Version majeure</td> 
  </tr>
  <tr>
   <th>Date de disponibilité générale</th> 
   <td>4 avril 2018<br /> </td> 
  </tr>
  <tr>
   <th>Mises à jour recommandées</th> 
   <td>See <a href="https://helpx.adobe.com/experience-manager/aem-releases-updates.html">AEM releases and updates</a></td> 
  </tr>
 </tbody>
</table>

### Trivia {#trivia}

Le cycle de publication de cette version d’Adobe Experience Manager, démarré le 27 avril 2017, a fait l’objet de 22 itérations d’assurance qualité et de résolution de bogues, et s’est terminé le 22 mars 2018. Au total, 704 problèmes des utilisateurs (y compris les améliorations et les nouvelles fonctionnalités) ont été corrigés dans cette version.

Adobe Experience Manager 6.4 est disponible depuis le 4 avril 2018.

>[!NOTE]
>
>Adobe recommande d’installer le dernier Service Pack, car tous les nouveaux Feature Packs sont livrés uniquement par le biais de Service Packs [](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html)Service Packs.

## Nouveautés {#what-s-new}

Adobe Experience Manager 6.4 est une mise à niveau de la base de code d’Adobe Experience Manager 6.3. Cette version comporte de nouvelles fonctionnalités améliorées, des correctifs clés de bogues signalés par des clients, des améliorations prioritaires demandées par les clients et des correctifs de bogues généraux destinés à améliorer la stabilité du produit. Elle comprend également la majorité des packs de fonctionnalités, correctifs et Service Pack d’Adobe Experience Manager 6.3.

La liste ci-dessous donne un aperçu, tandis que les pages suivantes donnent une liste complète des détails.

### Experience Manager Foundation {#experience-manager-foundation}

Liste complète des modifications apportées à [AEM Foundation](wcm-platform.md).

La plateforme d’Adobe Experience Manager 6.4 repose sur les versions mises à jour de l’architecture OSGi (Apache Sling et Apache Felix), ainsi que sur Java Content Repository : Apache Jackrabbit Oak 1.8.2.

Le démarrage rapide (Quickstart) utilise le moteur de servlet Eclipse Jetty 9.3.22.

#### Interface utilisateur {#user-interface}

Diverses améliorations ont été apportées à l’interface utilisateur pour la rendre plus productive et plus facile à utiliser.

* [Nouveau rail d’arborescence de contenu](/help/sites-authoring/basic-handling.md#content-tree) pour naviguer rapidement au sein d’une hiérarchie. Conjointement avec le mode Liste, cela restaure le modèle d’interaction de l’interface utilisateur classique.
* Expérience de défilement optimisée en modes Carte et Liste au sein de dossiers volumineux.
* [Interaction améliorée avec les résultats de recherche](/help/sites-authoring/search.md) : le bouton Retour restaure le résultat de la recherche précédente.
* [Raccourcis clavier supplémentaires](/help/sites-authoring/keyboard-shortcuts.md) pour les actions les plus courantes, telles que l’ouverture d’un rail particulier pour modifier, déplacer et supprimer un élément, ou ouvrir des propriétés.
* [Possibilité de désactiver les raccourcis clavier](/help/sites-authoring/user-properties.md) (activer/désactiver dans Préférences).
* [Désactivation de l’affichage des horodatages dans toutes les interfaces utilisateur](/help/sites-authoring/user-properties.md) relative après 7 jours (défini par défaut dans Préférences).

Pour en savoir plus sur ces fonctions, voir la [documentation sur la création.](/help/sites-authoring/home.md)

>[!CAUTION]
>
>Adobe ne prévoit pas d’apporter d’autres améliorations à l’interface utilisateur classique. AEM 6.4 inclut l’interface utilisateur classique, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que l’interface utilisateur classique reste complètement prise en charge alors qu’elle est en passe de devenir obsolète. [En savoir plus](/help/sites-deploying/ui-recommendations.md).

#### Référentiel de contenu {#content-repository}

* Une compression plus rapide et plus efficace lors du nettoyage des révisions en ligne. Les tests internes indiquent que la nouvelle compression des révisions les plus récentes est jusqu’à 10 fois plus rapide et peut libérer plus d’espace disque avec un nombre inférieur d’IOPS par rapport à AEM 6.3. Par conséquent, les performances sont moins affectées lors de l’exécution du nettoyage des révisions en ligne. Pour plus d’informations, voir la [page de documentation](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes).

* Le nettoyage des révisions en continu pour MongoMK remplace la maintenance de nettoyage planifiée.
* Efficacité accrue du nettoyage des·révisions sur les magasins de nœuds de documents

#### Recherche et indexation {#search-indexing}

* Prise en charge améliorée des opérations d’indexation par l’intermédiaire d’oak-run (interface de ligne de commande) :

   * Contrôle de la cohérence de l’index
   * Indexation des statistiques
   * Importation/exportation des configurations d’index
   * Réindexation

* Réduction de la croissance des référentiels associés à Lucene pour des performances système globales améliorées

Pour plus d’informations, voir la [page de documentation](/help/sites-deploying/indexing-via-the-oak-run-jar.md).

#### Surveillance {#monitoring}

* A new [System Overview](/help/sites-administering/operations-dashboard.md#system-overview) provides a snapshot view on all performance-related system status &amp; activities
* Un nouvel ensemble de [contrôles de l’intégrité](/help/sites-administering/operations-dashboard.md#health-checks) concernant l’indexation, les requêtes et la maintenance.

#### Projets et workflows {#projects-and-workflows}

* Un nouvel [éditeur de processus pour créer et modifier les modèles de workflows](/help/sites-developing/workflows-models.md).

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### Mise à niveau d’une version antérieure {#upgrade-from-earlier-version}

* [Compatibilité descendante](/help/sites-deploying/backward-compatibility.md) : grâce aux fonctions de la version 6.4 compatibles avec les versions antérieures, votre code personnalisé reste compatible dans la plupart des cas, et les efforts de mise à niveau sont réduits.
* [Évaluation de la complexité de la mise à niveau](/help/sites-deploying/pattern-detector.md) : le nouvel outil de détection des motifs évalue la complexité de vos mises à niveau avant que vous ne les effectuiez.
* [Restructuration](/help/sites-deploying/repository-restructuring.md)du référentiel : restructuration importante (principalement /etc.) pour faciliter les mises à niveau et promouvoir les meilleures pratiques d&#39;implémentation
* Pour des informations plus générales sur les mises à niveau, voir [cette page](/help/sites-deploying/upgrade.md).

### Experience Manager Sites {#experience-manager-sites}

Liste complète des modifications apportées à [AEM Sites et aux modules complémentaires](sites.md).

#### Experiences fluides {#fluid-experiences}

L’introduction des expériences fluides début 2017, en complément des fragments de contenu, des fragments d’expérience et de Content Services, représentait le début de l’évolution vers une gestion de contenu multi-canal. AEM 6.4 étend significativement chacun des domaines :

**[Fragments de contenu](/help/assets/content-fragments.md)**

Les nouveautés de la version 6.4 incluent un éditeur de [modèle de contenu](/help/assets/content-fragments-models.md) et un nouveau [composant configurable](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html) pour fournir la sortie HTML souple et le JSON à inclure dans Content Services.

**Fragments d’expérience**

La création de variations au sein d’un fragment avec le même contenu, mais une disposition différente, est maintenant plus efficace, grâce à la fonctionnalité de blocs de création. Outre l’envoi de fragments d’expérience vers Facebook et Pinterest, il est désormais possible de les envoyer sous forme d’offre à Adobe Target.

**Content Services**

Diverses améliorations ont été apportées à Sling Model Exporter et aux composants principaux afin de fournir une sortie JSON robuste pour incorporer du contenu dans les applications mobiles et les expériences créées avec des applications d’une seule page.

#### Obtention plus rapide des sites {#gettings-sites-built-quicker}

AEM 6.4 complète la transformation vers le modèle de composant de nouvelle génération. Le concept de composants de base introduit dans AEM 6.3, et maintenant accompagné du système de style, fournit une manière efficace pour créer des sites et étendre des sites existants.

Tutoriel recommandé pour tirer le meilleur parti du nouveau modèle de composant : [Prise en main d’AEM Sites – Tutoriel WKND](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html)

#### Module complémentaire Screens {#screens-add-on}

La diffusion d’un message cohérent sur tous les canaux marketing, y compris les réseaux Digital Signage et de kiosques, est l’acronyme d’AEM Screens. AEM 6.4 ajoute la prise en charge de l’exécution du lecteur de contenu dynamique sur le matériel reposant sur Microsoft Windows et Google Chrome OS. De plus, la gestion des périphériques à distance et les planifications (groupes de canaux) ont été améliorées.

For more information on the Screens updates, see [AEM Screens User Guide](/help/screens/home.md).

### Experience Manager Communities {#experience-manager-communities}

AEM 6.4 offre de nombreuses nouvelles fonctions et améliorations de Communities. Liste complète des modifications apportées à [AEM Communities](communities-release-notes.md). Les points forts de cette version sont :

#### Amélioration de la modération {#enhancements-to-moderation}

**Détection automatique du contenu indésirable**

Le nouveau moteur de détection du contenu indésirable fourni permet de filtrer le contenu indésirable généré par l’utilisateur sur des groupes et des sites de communautés. Une fois activé à partir de system/console/configMgr, il marque un contenu généré par un utilisateur comme indésirable en fonction d’un ensemble prédéfini de mots indésirables. Pour plus d’informations sur le moteur de détection du contenu indésirable, voir [Modération automatique du contenu généré par les utilisateurs d’une communauté](/help/communities/moderate-ugc.md#spam-detection).

![spamdetection](assets/spamdetection.png)

**Nouveaux filtres pour Q&amp;R**

De nouveaux filtres, appelés « A reçu une réponse » et « Sans réponse », ont été ajoutés à la console de modération en masse de façon à filtrer les questions Q&amp;R. Pour connaître le mode de fonctionnement des filtres d’état « A reçu une réponse » et « Sans réponse », voir [Modération en masse du contenu généré par les utilisateurs](/help/communities/moderation.md#main-pars-note-521961797).

**Marquage avec signet des filtres de modération**

Il est possible de marquer avec des signets les filtres de modération prédéfinis sur la console de modération. Ces filtres sont ajoutés à la fin de la chaîne URL et peuvent ainsi être partagés, réutilisés et reconsultés ultérieurement. Découvrez comment marquer des filtres avec des signets dans la [console de modération en masse](/help/communities/moderation.md#main-pars-note-429176623).

#### Suppression du contenu généré par l’utilisateur et des profils utilisateurs {#delete-ugc-and-user-profiles}

AEM 6.4 Communities expose les [API prêtes à l’emploi](/help/communities/user-ugc-management-service.md) et une [servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) d’exemple pour permettre aux utilisateurs finaux de contrôler leur données. Avec ces API, les organisations qui traitent et contrôlent les données peuvent également traiter des demandes de conformité au règlement général sur la protection des données (RGPD) européen.

#### Amélioration de la gestion des sites et des groupes {#enhancements-to-site-and-group-management}

**Création de groupes multirégionaux en une seule étape**

Il est maintenant possible de créer des groupes multilingues en une seule opération. Pour créer de tels groupes, les utilisateurs peuvent accéder à la collection de groupe des communautés désirées à partir de la console Sites. Créez un groupe et spécifiez les langues souhaitées sur la page Modèle de groupe de communautés. Pour plus d’informations sur cette fonctionnalité, voir [Console Groupes communautaires](/help/communities/groups.md).

![groupe multilingue](assets/multilingualgroup.png)

**[Suppression des groupes et des sites de communautés en un clic](/help/communities/groups.md)**

L’icône Supprimer est maintenant disponible sur les sites et les groupes respectifs, lorsque vous naviguez à partir de la navigation globale. Cette icône permet de supprimer tous les éléments et le contenu associé au site ou groupe, et supprime toutes les associations d’utilisateurs. Pour plus d’informations sur cette fonctionnalité, voir [Gestion des sites de communautés](/help/communities/create-site.md#main-pars-text-fe17) et [Gestion des groupes de communautés](/help/communities/groups.md#main-pars-text-5e8c).

#### Amélioration de l’activation {#enhancements-to-enablement}

Les fonctions d’affectation et de catalogue sont désormais disponibles au sein des groupes. Elles permettent de créer, gérer et publier du contenu pédagogique pour un ensemble spécifique de membres de communauté ciblés. Pour plus d’informations sur l’activation des groupes de communautés, voir [Gestion des ressources d’activation](/help/communities/resource.md).

![assignmentcatalog](assets/assignmentcatalog.png)

### Experience Manager Assets {#experience-manager-assets}

AEM 6.4 apporte plusieurs nouvelles fonctions et améliorations d’Assets, notamment l’intégration améliorée de Creative Cloud, des innovations importantes d’intelligence artificielle, la gestion perfectionnée des métadonnées, ainsi que des améliorations dans la création de rapports et l’expérience utilisateur générale. La liste complète des modifications est disponible dans [AEM Assets](assets.md). Les principales fonctionnalités de cette version sont les suivantes :

**Adobe Asset Link**

Adobe Asset Link dans Creative Cloud abonnement Entreprise simplifie la collaboration entre les créatifs et les spécialistes du marketing dans le cadre du processus de création de contenu. Il s’agit d’une nouvelle fonctionnalité native de Creative Cloud abonnement Entreprise qui relie Photoshop CC, Illustrator CC et InDesign CC à AEM, sans que les créatifs n’aient besoin d’abandonner leurs outils de prédilection.

Pour plus d’informations sur cette fonctionnalité, les conditions préalables et la façon d’y accéder, voir [Adobe Asset Link](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html).

![adobe_asset_link](assets/adobe_asset_link.png)

**Application de bureau AEM**

AEM desktop app has been updated to Version 1.8, which is compatible with AEM 6.4. The full list of changes for AEM desktop app is provided in a dedicated [AEM desktop app release notes](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html) document.

Les améliorations introduites depuis la version 6.3 d’AEM incluent la possibilité de télécharger les fichiers hiérarchiques en arrière-plan, une nouvelle interface utilisateur pour contrôler les tâches associées aux actifs en arrière-plan, l’optimisation de la mise en cache, de la mise en réseau et de la connexion réseau, ainsi que des améliorations de stabilité. La documentation comprend également un [guide de meilleures pratiques](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html).

**Adobe Sensei Services**

Parmi les nouvelles fonctionnalités, figurent les balises intelligentes améliorées, avec la possibilité d’apprendre la taxonomie métier du client, de baliser automatiquement les actifs numériques à l’aide de balises spécifiques au client, ainsi que la recherche de traduction intelligente, qui améliore l’accessibilité dans plusieurs langues en traduisant les termes de recherche à la volée. Pour plus d’informations sur cette fonction, voir [Balises intelligentes améliorées](/help/assets/enhanced-smart-tags.md).

![advanced_smart_tags2](assets/enhanced_smart_tags2.png)

**Métadonnées**

Il est désormais possible d’importer et d’exporter des métadonnées simultanément pour de grands nombres d’actifs et de constructions de métadonnées avancées telles que la [Cascade de métadonnées](/help/assets/cascading-metadata.md).

**Rapports**

La création de rapports de ressources a fait l’objet d’une modification importante dans AEM 6.4 avec un nouveau framework de rapport, une nouvelle expérience utilisateur et davantage de rapports prêts à l’emploi pour les scénarios d’utilisation des clients. Pour savoir comment générer différents rapports, voir [Rapports de ressources](/help/assets/asset-reports.md).

**Expérience utilisateur**

Diverses améliorations ont été apportées à la navigation, la recherche et l’expérience de l’administrateur pour les utilisateurs Assets, telles que l’expérience de défilement, le bouton Retour pour les recherches, les filtres de recherche améliorés et bien plus. The full list available in [AEM Assets](assets.md).

**Brand Portal**

Plusieurs améliorations ont été apportées aux métadonnées, à la création de rapports, aux droits numériques, à l’expérience de connexion et aux performances de publication pour la distribution des actifs. To know about the new enhancements and features, see [What&#39;s new in AEM Assets Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/using/whats-new.html).

#### Module complémentaire Dynamic Media {#dynamic-media-add-on}

AEM 6.4 inclut de nombreuses améliorations et nouvelles fonctions pour Dynamic Media. The full list is available in [AEM Assets](assets.md). Les principaux points saillants sont les suivants :

**Recadrage intelligent**

Le recadrage intelligent, reposant sur Adobe Sensei, recadre automatiquement les images de façon non destructrice, en préservant le point d’intérêt pour le responsive design. Vous pouvez prévisualiser les suggestions d’image recadrée et les ajuster manuellement, si nécessaire. Cette fonction permet également la génération automatique d’échantillons pour l’imagerie produit.

Voir la documentation [Profils d’images](/help/assets/image-profiles.md) pour plus d’informations sur l’utilisation du recadrage intelligent.

Voir [Ajout de ressources Dynamic Media aux pages](/help/assets/adding-dynamic-media-assets-to-pages.md) pour plus d’informations sur l’utilisation du recadrage intelligent dans le composant Dynamic Media.

**Imagerie dynamique**

L’imagerie dynamique utilise les caractéristiques de visualisation uniques de chaque utilisateur afin de diffuser automatiquement des images optimisées pour leur expérience, ce qui se traduit par des performances accrues et une meilleure interaction.

Voir [Imagerie dynamique](/help/assets/imaging-faq.md) pour plus d’informations.

![smart_culture](assets/smart_crop.png)

**Médias émergents et amélioration des visionneuses**

De nouvelles visionneuses, notamment panoramique et VR, vous permettent de fournir des expériences plus immersives.

Voir la documentation [Images panoramiques](/help/assets/panoramic-images.md) pour plus d’informations.

**Ressources 3D**

New integration with [Adobe Dimension CC](https://www.adobe.com/products/dimension.html), a Creative Cloud application for authoring 3D experiences.

Voir la documentation [Utilisation d’actifs 3D](/help/assets/assets-3d.md) pour plus d’informations.

![do-not-localize/3d](assets/do-not-localize/3d.png)

### Experience Manager Forms {#experience-manager-forms}

AEM Forms 6.4 comporte plusieurs nouvelles fonctionnalités et améliorations. En voici un aperçu :

* Communications interactives multicanal
* Préremplissage des communications interactives à partir des applications commerciales
* Modernisation des workflows et prise en charge des employés mobiles
* Chargement différé des fragments
* Mise à niveau en un seul bond de LiveCycle vers Experience Manager Forms 6.4

Pour plus d’informations, consultez la page des notes de mise à jour d’[AEM Forms](forms.md). Also, see the [Summary of new features and enhancements in AEM 6.4 Forms](/help/forms/using/whats-new.md) for information about new and improved features and documentation resources.

### Experience Manager Livefyre {#experience-manager-livefyre}

Vous pouvez intégrer Livefyre à votre instance AEM 6.4. Vous trouverez des informations sur la façon d’intégrer Livefyre à AEM en suivant ce lien :

* [Intégration de Livefyre](https://https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html)

### Tirer parti du développement axé sur le client {#leverage-customer-focused-development}

Adobe applique un modèle de développement axé sur les utilisateurs afin que ces derniers puissent contribuer à toutes les étapes du processus de développement, au cours des phases de spécification, de développement et de tests. Merci à tous les utilisateurs et partenaires qui contribuent à ce processus.

Adobe a mis en place les procédures et processus nécessaires à la collecte, à la hiérarchisation et au suivi de la résolution des bogues signalés par les utilisateurs et du développement des demandes d’amélioration. The [Adobe Marketing Cloud Support Portal](https://helpx.adobe.com/marketing-cloud/contact-support.html) is integrated with the Adobe Enhancement &amp; Defect Tracking System. Les questions des utilisateurs sont identifiées et résolues par l’assistance clientèle dans la mesure du possible. Lorsqu’elles sont transmises au service R&amp;D, toutes les informations client sont capturées et utilisées à des fins de hiérarchisation et de création de rapports. Les problèmes entrant dans le cadre de l’assistance payante et de la garantie, ainsi que les demandes d’amélioration des utilisateurs détenant un compte payant sont prioritaires.

Ce processus de hiérarchisation a généré plus de 500 modifications axées sur le client, corrigées dans AEM 6.4.

## Liste des fichiers faisant partie de la version {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Démarrage rapide autonome : cq-quickstart-6.4.0.jar
* Démarrage rapide du serveur d’applications : cq-quickstart-6.4.0.war
* Dispatcher 4.3.1 ou version ultérieure pour différents serveurs web et plates-formes ([lien de téléchargement](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html))
* Module externe pour Eclipse IDE ([plus d’infos et téléchargement](/help/sites-developing/aem-eclipse.md))

* Extension pour l’éditeur de code Brackets ([plus d’infos et téléchargement](/help/sites-developing/aem-brackets.md))
* Dépendances Maven/Gradle ([lien de téléchargement](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/))

**Sites**

* Composants de base ([projet GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components))
* Mise en œuvre de We.Retail Reference ([plus d’infos](/help/sites-developing/we-retail.md))
* Archétype de plan directeur de projet ([projet GitHub](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype))
* Lecteurs AEM Screens pour différentes plateformes cibles ([téléchargement](https://download.macromedia.com/screens/))
* Modèles linguistiques pour le contenu dynamique. La version anglaise est préinstallée ; d’autres langues peuvent être téléchargées :

   * [Allemand](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Espagnol](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italien](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Français](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [Outil de conversion de boîte de dialogue](/help/sites-developing/dialog-conversion.md) pour faire migrer les composants de l’interface utilisateur classique vers Coral 3

**Assets**

* Adobe Experience Manager desktop app ([read more](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html) and [download](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html))

* Module pour ajouter le PDF Rasterizer amélioré ([plus d’infos](/help/assets/aem-pdf-rasterizer.md) et [téléchargement](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/assets/aem-assets-pdf-rasterizer-pkg))

* Module pour ajouter la prise en charge étendue des images RAW ([plus d’infos](/help/assets/camera-raw.md))

**Forms**

* Packages des fonctionnalités d’AEM Forms :

   * [adobe-aemfd-aix-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-AIX)
   * [adobe-aemfd-linux-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-LX)
   * [adobe-aemfd-solaris-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-SOL)
   * [adobe-aemfd-win-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-WIN)
   * [adobe-aemfd-osx-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-OSX)

## Langues {#languages}

L’interface utilisateur est disponible dans les langues suivantes :

* Anglais
* Allemand
* Français
* Espagnol
* Italien
* Brésilien Portugais
* Japonais
* Chinois simplifié
* Chinois traditionnel (prise en charge limitée)
* Coréen

Experience Manager 6.4 a été certifié dans le cadre de la norme GB18030-2005 CITS pour utiliser le codage des caractères chinois.

## Installation et mise à jour {#install-update}

Reportez-vous aux [instructions d’installation](/help/sites-deploying/custom-standalone-install.md) pour connaître les exigences de configuration.

Reportez-vous à la [documentation de mise à niveau](/help/sites-deploying/upgrade.md) pour obtenir des instructions détaillées.

## Plateformes prises en charge {#supported-platforms}

Vous trouverez une matrice complète des plates-formes prises en charge, y compris leur niveau de prise en charge, sur la page des [exigences techniques d’AEM 6.4](/help/sites-deploying/technical-requirements.md)

>[!NOTE]
>
>Oracle est passé à un modèle de support à long terme (LTS) pour les produits Oracle Java SE. Java 9 and 10 are non-LTS releases by Oracle (see [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe assure uniquement la prise en charge des versions LTS de Java pour exécuter AEM en production. La version 8 de Java est donc recommandée pour une utilisation avec AEM 6.4.

## Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe évalue constamment les fonctionnalités du produit et prévoit au fil du temps de les remplacer par des versions plus puissantes ou de réimplémenter certains composants afin de mieux accommoder les futures attentes ou extensions.

Dans le cas d’Adobe Experience Manager 6.4, [consultez la liste des fonctionnalités obsolètes et supprimées](deprecated-removed-features.md). Cette page présente également les modifications prévues en 2019, ainsi qu’un avis important à l’intention des utilisateurs qui mettent à jour des versions antérieures.

## Listes détaillées des modifications {#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[AEM Communities](communities-release-notes.md)

[AEM Forms](forms.md)

[AEM Foundation](wcm-platform.md)

## Problèmes connus {#known-issues}

[Liste des problèmes connus](known-issues.md)

### Assistance technique et téléchargement du produit (sites à accès limité) {#product-download-and-support-restricted-sites}

Seuls les clients peuvent accéder à ces sites. Si vous devez y accéder en tant que client, contactez votre gestionnaire de compte Adobe.

* [](https://daycare.day.com) [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)

* [Assistance clientèle sur daycare.day.com](https://daycare.day.com)

