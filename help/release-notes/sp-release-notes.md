---
title: 'Notes de mise à jour d’AEM 6.4, Pack de services '
seo-title: AEM 6.4 Service Pack Release Notes
description: Notes de mise à jour spécifiques aux Service Packs Adobe Experience Manager 6.4.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
exl-id: d0da9390-2167-47ee-82fd-8c81d8d68a3e
source-git-commit: 1537055fd88cbc3b01e4df7855a99f993f2052e4
workflow-type: tm+mt
source-wordcount: '21547'
ht-degree: 27%

---

# Notes de mise à jour d’AEM 6.4, Pack de services  {#aem-service-pack-release-notes}

## Informations sur la version {#release-information}

| Produits | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.0 |
| Type | Version du Service Pack |
| Date  | 5 mars 2020 |
| URL de téléchargement | AEM 6.4.8.0 sur [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## Fonctionnalités présentes dans AEM 6.4.8.0 {#what-s-included-in-aem}

AEM 6.4.8.0 est une mise à jour importante qui inclut de nouvelles fonctionnalités, des améliorations et des performances demandées par les clients clés, une stabilité et des améliorations de sécurité, publiée depuis la mise à disposition d’AEM 6.4 dans **Avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.8.0 inclut tous les Service Packs AEM 6.4 publiés avant.

Les principaux points forts de cette version du Service Pack incluent les éléments suivants :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.20.

* La fonctionnalité de retour automatique à la ligne est prise en charge pour les sites web japonais dans WCM-RTE.

* Le traitement des sauts de mot et des sauts de ligne est pris en charge pour les sites web japonais.

* Ajout de la prise en charge de l’utilisation de la méthode BUNSETSU pour rompre la phrase et les lignes en japonais à des emplacements appropriés.

* L’interface utilisateur CCR pour Correspondence Management prend désormais en charge les valeurs décimales pour les paramètres régionaux allemands.

* L’intégration du modèle de données de formulaire à l’aide du service Web SOAP prend désormais en charge les groupes de choix ou les attributs sur les éléments.

* AEM Assets est désormais configuré avec Brand Portal via [!DNL Adobe I/O].

* Mise à jour de la version jQuery intégrée dans ContextHub vers la version 3.2.1.

## Liste des modifications {#list-of-changes}

### Sites {#sites}

* Lorsqu’une URL d’une page AEM Sites contient un signe deux-points ou un symbole de pourcentage, le navigateur sous-jacent cesse de répondre et les cycles du processeur affichent un pic (NPR-32368, NPR-31917).
* Lorsqu’une page AEM Sites est ouverte pour modification et qu’un composant est copié, l’action de collage reste indisponible pour certains espaces réservés (NPR-32328).
* Le workflow de demande d’activation n’inclut pas les ressources référencées (NPR-32304).
* Lors de la création d’un plan directeur, si le nombre d’enregistrements est supérieur à 80, seuls les 80 premiers enregistrements sont affichés. Le plan directeur affiche des lignes vides pour le reste des enregistrements (NPR-32058).
* Les utilisateurs sont autorisés à enregistrer un fragment de contenu sans fournir d’informations dans les champs requis (NPR-31988).
* La navigation automatique ne fonctionne pas pour le chemin configuré dans un composant de fragment d’expérience principal (NPR-31921).
* Lorsque vous modifiez le type d’une cellule de tableau dans l’éditeur de texte enrichi (RTE), l’erreur suivante se produit :
   `Error: No common ancestor found, cannot continue` (NPR-31916).
* Lorsque le contenu est déplacé dans le même dossier, l’option de déplacement de page est désactivée (NPR-31841).
* Ajout de la prise en charge de la division des phrases en japonais à l’aide de la méthode BUNSETSU et de la rupture des lignes à la position appropriée (NPR-31836).
* Lorsque vous modifiez un lien hypertexte dans l’éditeur de texte enrichi (RTE), le nouveau chemin sélectionné n’est pas enregistré (NPR-31659).
* Lorsque vous supprimez un composant multichamp et annulez la suppression, le composant est restauré, mais les données ne sont pas restaurées (NPR-31617).

### Assets {#assets}

* Un dossier sans nom est créé dans Dynamic Media Classic lors du déplacement d’une ressource d’un dossier vers un autre dans Experience Manager avec configuration Dynamic Media Classic (NPR-32440).

* La page des détails des ressources des fichiers de PDF n’affiche pas les boutons d’action dans Experience Manager s’exécutant en mode Dynamic Media Scene7 (NPR-32316).

* Les rendus de ressources et vidéo ne peuvent pas être supprimés (NPR-32213).

* L’icône de calendrier pour l’activation planifiée ne s’affiche pas dans la colonne État (dans l’interface utilisateur classique de la liste de ressources DAM) pour les ressources dont l’activation est planifiée à une date et une heure ultérieures (NPR-32198).

* La relation des ressources est remplacée lorsque les ressources sont liées à plusieurs ressources à l’aide d’Autres (NPR-32196).

* Le bouton Enregistrer n’importe pas la visionneuse à distance lorsque l’utilisateur n’a apporté aucune modification à l’éditeur de visionneuses dans le client Dynamic Media (NPR-32178).

* L’ingestion de ressources par PSD provoque un pic du processeur et une instance d’auteur de Experience Manager non réactive (NPR-32165).

* Exception de mémoire insuffisante observée lorsqu’un fichier ZIP volumineux est téléchargé dans la gestion des actifs numériques du Experience Manager (NPR-32155).

* Les URL d’historique de version s’affichent sous le champ Référencé par sur la page de propriété des ressources (NPR-31889).

* L’annulation de la publication à partir de Brand Portal, sur la page Gérer la publication, échoue pour les sous-dossiers d’un dossier publié (NPR-31835).

* Le chargement des codes vidéo Dynamic Media échoue lorsque la configuration de Scene7 Cloud est placée dans un dossier privé. `/conf` au lieu de `/conf/global` (NPR-31779).

* L’image n’est pas visible sur la chronologie après l’ajout d’annotations, sur Experience Manager s’exécutant en mode Scene7 Dynamic Media (NPR-31754).

* Le fichier ZIP téléchargé à partir de DAM ne peut pas être ouvert à l’aide de WinZip (NPR-31745).

### Intégrations {#integrations-6480}

* Le **Société** et **Reporting** Les menus déroulants de la suite sont masqués une seule fois. **Source de création de rapports** est sélectionné lors de la configuration d’Adobe Analytics dans les services cloud Experience Manager (NPR-31729).

* Les propriétés Adobe Campaign ne sont pas nettoyées lorsque la copie de langue d’une newsletter liée à une Adobe Campaign est effectuée, tandis que le nettoyage se produit lorsqu’une newsletter liée à une Adobe Campaign est copiée ou collée (NPR-32540).

* ReportSuitesServlet est vulnérable aux attaques SSRF (NPR-32161).

### Sling {#sling-6480}

* L’observation des ressources ne fonctionne pas avec un effet d’ombre non déterministe (CQ-4286466).

### Projets {#projects-6480}

* Le bouton Créer n’est pas visible pour l’utilisateur, même s’il est autorisé à créer un projet dans le sous-dossier (NPR-31831).

* La fonctionnalité de basculement entre les modes Carte, Liste et Calendrier ne fonctionne pas après avoir sélectionné le mode Calendrier dans les Projets (NPR-31829).

### Traduction {#translation-6480}

* La création d’un projet de traduction pour plusieurs langues génère le projet uniquement pour certaines langues au lieu de toutes et une erreur (le résolveur de ressources est déjà fermé) est observée dans le journal (NPR-32212).

### WCM-MSM {#wcm-msm-6480}

* Les problèmes d’autorisation entraînent l’affichage d’erreurs lors du déplacement de pages dans un plan directeur (NPR-32610).

### Éditeur de page WCM {#wcm-page-editor-6480}

* Le navigateur cesse de répondre lors de la tentative d’ajout d’un composant à une page avec un format d’URL spécifique (NPR-32368, NPR-31917).

### Interface utilisateur WCM-Admin {#wcm-admin-ui-6480}

* La gestion de la publication n’inclut pas les ressources référencées dans le workflow de demande d’activation (NPR-32304).

### Communities {#communities}

* Impossible de mettre à jour la miniature du groupe pour les groupes (NPR-32603).

### Brand Portal {#brand-portal}

* L’annulation de la publication du schéma de métadonnées dans AEM Assets renseigne un message d’erreur bien que le schéma soit supprimé du serveur principal (CQ-4286871).

### Interface utilisateur de Foundation {#foundations-ui-6480}

* Des caractères non valides s’affichent dans l’URL ajoutée à un composant Bouton (NPR-32684).

### Formulaires {#forms}

>[!NOTE]
>
>Le Service Pack AEM n’inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un module complémentaire Forms distinct.  En outre, un programme d’installation cumulatif est publié, qui comprend des correctifs pour AEM Forms on JEE. Pour plus d’informations, voir [Installation du module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installation du programme d’installation d’AEM Forms JEE](#install-aem-forms-jee-installer).

* Designer : Si l’option de balisage est activée, la bordure du sous-formulaire disparaît dans la sortie de PDF générée (NPR-32546, NPR-32322).

* Designer : s’il existe des cellules fusionnées dans un tableau, le test d’accessibilité échoue pour un fichier PDF de sortie converti par le service de sortie à l’aide d’un formulaire XDP (NPR-32079).

* Document Security : Un fichier de PDF protégé ne s’ouvre pas hors ligne avec l’option DisableGlobalOfflineSynchronizationData définie sur True (NPR-32080).

* Document Security : Problèmes lors de l’ouverture d’un fichier de PDF protégé après la mise à niveau de ES4 vers AEM 6.3 (NPR-32170).

* Document Services : Un message d’erreur s’affiche lors de la tentative de conversion d’un fichier de PDF en document de PDF/A à l’aide de la méthode de conversion toPDFA (NPR-32663).

* Document Services : Une exception s’affiche lors de l’application du service Reader Extensions sur un fichier de PDF (NPR-32639).

* Document Services : Un message d’erreur s’affiche lors de l’assemblage et de la conversion de fichiers XDP en fichiers PDF (NPR-31821).

* Analytics n’affiche pas les résultats appropriés lors de l’envoi ou de l’abandon de formulaires sur une page Sites (NPR-31359).

### Correctifs et packs de fonctionnalités inclus dans les packs de service précédents {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

AEM 6.4.7.0 est une mise à jour importante qui comporte des améliorations et correctifs pour les performances, la stabilité, la sécurité et les bogues signalés par les clients depuis la mise à disposition d’AEM 6.4 dans **Avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.7.0 inclut tous les Service Packs AEM version 6.4 avant sa publication.

Voici quelques-uns des points forts d’AEM 6.4.7.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.17.
* Ajout de la prise en charge de la définition de la version d’une page Sites lors de sa suppression.
* Une nouvelle colonne pour la date de création, qui est triable, a été ajoutée dans **Liste DAM** afficher et afficher les résultats de la recherche de ressources dans **Liste** view (NPR-31311).
* Tri des ressources en fonction de **Nom** La colonne a été autorisée dans **Liste** vue.
* La taille du lot et le délai d’expiration de l’étape de workflow pour le retraitement et le transfert par lots peuvent désormais être configurés à partir de l’interface utilisateur dans Dynamic Media.
* Le `pdfBrochure` a été défini sur false dans la configuration cloud Scene 7, pour enregistrer la mémoire dans IPS.

##### Ressources {#assets-6470}

**Améliorations des produits**

* La version d’exportation du package d’API `package com.day.cq.dam.handler.standard.msoffice` pris en charge par `dam-handler` Le lot est mis à niveau vers la version 6.0.0 (CQ-4279059).
Si vous utilisez le module `com.day.cq.dam.handler.standard.msoffice` dans votre implémentation personnalisée, il est conseillé de compiler votre `dam-handler` offre groupée avec le dernier fichier uber jar.

* Une nouvelle colonne pour la date de création, qui est triable, a été ajoutée en mode Liste de la gestion des actifs numériques et dans les résultats de recherche de ressources en mode Liste (NPR-31311).

* Le tri des ressources selon la colonne Nom a été autorisé en mode Liste (NPR-31299).

**Correctifs**

* Les métadonnées de certains documents de PDF ne sont pas mises à jour et enregistrées dans le PDF lors de la modification de son titre (NPR-31575).

* Les ressources comportant le symbole &quot;+&quot; dans le nom de fichier ne peuvent pas être supprimées (NPR-30588).

* Les propriétés du dossier DAM n’affichent pas les utilisateurs ou groupes ajoutés (créés par synchronisation LDAP) dans les groupes d’utilisateurs fermés (NPR-30555).

* Les caractères spéciaux apparaissant dans la ligne Objet des modèles de courrier électronique ne s’affichent pas correctement (NPR-30547).

* Les noms des ressources sont modifiés en minuscules lors du déplacement des ressources d’un dossier à un autre dans AEM s’exécutant en mode d’exécution Dynamic Media Scene 7 (NPR-31631).

* Les noms des jeux d’images sont modifiés en minuscules dans Scene 7, lorsque les jeux d’images (ou jeux de médias) sont créés et nommés avec la convention de nommage appropriée dans la gestion des ressources numériques (NPR-31576).

* Le workflow Vidéo de codage Dynamic Media ne parvient pas à générer la miniature de la vidéo qui est migrée de Scene 7 vers Dynamic Media - mode d’exécution Scene 7 (NPR-31523).

* Une erreur interne du serveur est observée lors de l’utilisation du filtre pour rechercher des visionneuses, dans AEM s’exécutant sur le mode d’exécution Dynamic Media - Scene 7 (NPR-31388).

* Une erreur est observée lors de la modification d’un jeu d’images distant, pour l’image résidant dans le dossier nommé de la même manière que le nom de la société Scene 7 (NPR-31347).

* Les ressources contenant des références ne sont pas publiées (DM) (NPR-31179).

* La valeur d’expiration (délai d’activation du cache client) configurée pour le mode hybride de Dynamic Media n’est pas répliquée dans l’environnement de diffusion de Dynamic Media (NPR-31126).

* Les chargements depuis AEM Dynamic Media - mode d’exécution Scene 7 vers Scene 7 prennent trop de temps à se terminer (NPR-30926).

* Après avoir créé une page comportant un composant Dynamic Media lors de la publication de la même page, à partir de l’instance d’auteur s’exécutant sur le mode d’exécution Dynamic Media - Scene 7, l’utilisateur est invité à publier la configuration de Dmscene7 (NPR-30880).

* La valeur du paramètre &quot;ressource&quot; dans le code incorporé de la visionneuse reste inchangée après la modification des valeurs des champs &quot;Titre après déplacement&quot; et &quot;Nom après déplacement&quot; dans Dynamic Media - Scene 7 (NPR-30745).

* La recherche dans l’interface utilisateur tactile (effectuée par l’intermédiaire de l’omni-recherche) fait automatiquement défiler vers le haut et perd la position de défilement de l’utilisateur (NPR-31306).

* La purge de l’événement DAM supprime les dernières données d’événement (maxSavedActivities) et contient les données créées précédemment (NPR-30870).

* Le titre et le nom de la ressource ne sont pas conservés après l’opération de déplacement vers un dossier de destination qui déclenche un défilement infini lors de sa sélection (NPR-30647).

* Les collections sont supprimées de la vue lors de l’application de tout filtre dans AEM Assets accessible à partir d’Adobe Asset Link (CQ-4280534).

* La taille du lot et le délai d’expiration de l’étape de workflow pour le retraitement et le transfert par lots ne sont pas configurables à partir de l’interface utilisateur. Ils doivent être définis dans CRXDE et le workflow doit être synchronisé deux fois (CQ-4281254).

* Le nom de l’étape de workflow pour le chargement par lots et l’étape de chargement simple est identique dans Scene 7, ce qui entraîne une confusion (CQ-4281176).

* Le workflow de retraitement dans Scene 7 est bloqué si un noeud de métadonnées manque à une ressource (CQ-4281170).

* L’étape Transfert par lots du workflow de retraitement ne fonctionne pas pour le dossier comportant une ressource vidéo (CQ-4280630).

* Les options de PDF envoyées à DM sont extractionKeywords définies sur true par défaut (CQ-4280101).

* Une exception de point nul est observée lors de l’exécution du workflow de retraitement Scene 7 sur un dossier contenant des ressources non DM (CQ-4279555).

* Le changement de nom de la ressource dans AEM ne se synchronise pas avec la scène 7, lorsqu’une ressource portant un nom en double existe déjà dans Scene 7 (CQ-4276763).

* Le fichier zip envoyé par courrier électronique pour le téléchargement de ressources ne parvient pas à se décompresser lorsqu’un utilisateur disposant de droits de lecture tente de l’ouvrir (CQ-4277925).

* Le processus de rendu PPT ne parvient pas à générer les rendus des fichiers PPT chargés, car AEM 6.4 ne parvient pas à mettre à jour vers com.adobe.granite.poi version 2.0.28 (CQ-4279059).

* Les fichiers de PDF ne sont pas indexés et le contenu dans n’est pas consultable (CQ-4278916).

##### Sites {#sites-6470}

* Lorsque les lancements sont promus avec les pages modifiées uniquement et que les lancements avec les pages modifiées sont effectués, seules les pages modifiées apparaissent comme converties. De plus, lorsque la liste à promouvoir est correcte, les pages non modifiées sont toujours affichées en bas de la liste (NPR-31314).

* Lorsqu’une page AEM Sites est déplacée vers un autre emplacement, ses propriétés ne sont pas mises à jour en conséquence pour refléter son nouvel emplacement (NPR-31265).

* Pour un nouveau plan directeur, si le nombre d’enregistrements est supérieur à 40, seuls les 40 premiers enregistrements sont affichés. Le plan directeur affiche des lignes vides pour le reste des enregistrements (NPR-31182).

* Lorsque le nombre de LiveCopies est important, le rendu de l’aperçu de LiveCopy prend beaucoup de temps (NPR-30945).

* Ajout de la prise en charge de la définition d’une version d’une page lors de sa suppression. Si le contrôle de version est désactivé pour la page supprimée, AEM Sites ne peut pas restaurer ces pages (NPR-30891).

* Lorsqu’un utilisateur ajoute des caractères japonais ou coréens dans la propriété description d’un menu, le menu affiche des caractères déformés pour le texte en japonais et coréen (NPR-31331).

* Lorsqu’un utilisateur se concentre sur les champs du rail gauche et utilise un raccourci clavier pour coller du contenu, il colle le contenu du Presse-papiers de l’éditeur de page au lieu du contenu copié à partir des champs du rail gauche (NPR-31169).

* Lorsqu’un utilisateur modifie un fragment de contenu, la variante déjà supprimée du fragment de contenu est restaurée (NPR-31178).

* La requête Modèles de fragment de contenu est inefficace. Cette opération est très lente si l’instance comporte beaucoup de pages et entraîne une erreur (NPR-30666).

* Lors de l’enregistrement du modèle de fragment de contenu, l’heure dans le champ date et heure est définie sur 00:00 (NPR-30540).

##### Intégrations {#integrations-6470}

* Lors de la configuration d’Adobe Launch, une barre oblique (/) est précédée dans l’URL de la bibliothèque (NPR-30700).

* Les performances de ContextHub se dégradent après la publication (NPR-30884).

##### Sling {#sling-6470}

* Mettez à jour la version du bundle du fournisseur de sécurité de la console web vers la version 1.2.4 pour supprimer la dépendance de l’api de démarrage du launchpad à partir de webconsolesecurityprovider (NPR-30885).

##### Plateforme {#platform-6470}

* Les mises à jour de la configuration de la taille de la mémoire tampon pour le service HTTP basé sur Jetty ne sont pas enregistrées (NPR-30925).

* QueryBuilder prend désormais en charge orderby fn:name() dans les requêtes xpath (NPR-31322).

* Mise à jour de l’administration des événements distribués Sling vers la version 1.1.4 afin d’améliorer la qualité des journaux dans un environnement organisé en grappes (NPR-29256).

##### Interface utilisateur de Foundation {#foundation-6470}

* Le fait de faire défiler jusqu’à la fin de la page de résultats avec un grand nombre de résultats de recherche provoque le blocage du navigateur (NPR-31332).

* Lors du passage du mode Carte au mode Liste sur une page de résultats de recherche, un décalage s’affiche avant que la page ne puisse être défilée (NPR-31280).

##### Oak {#oak-6470}

* Les fichiers MS Office comportant des extensions de fichiers .docx et .xlsx contenant des images de JPEG ne parviennent pas à s’analyser à l’aide de l’analyseur Tika (NPR-31693).

##### Livefyre {#livefyre-6470}

* L’intégration de Livefyre avec la mise à niveau d’AEM 6.4 donne une exception Null Point Exception, lorsque l’intégration est effectuée à l’aide du module externe DITA pour les ressources de synthèse. L’intégration fonctionne toutefois lorsque des composants sont ajoutés manuellement (FYR-11066).

##### Traduction {#translation-6470}

* Le chemin d’accès au fragment d’expérience de destination n’est pas mis à jour lors de la promotion d’une page de lancement (NPR-30830).

##### Communautés {#communities-6470}

* La fonctionnalité de messagerie électronique ne fonctionne pas correctement dans certains cas, même si la messagerie électronique est activée dans les paramètres de notification, le système renvoie une exception dans NotificationsActivityStreamProvider (NPR-31521).
* Impossible de créer de nouveaux membres, un écran vide s’affiche sur l’écran Créer un membre dans AEM instance d’auteur (NPR-30951).
* L’utilisateur ne peut pas publier de commentaire sur un blog dans Internet Explorer 11 (NPR-30927).
* L’administrateur d’un groupe restreint n’est pas en mesure d’afficher la carte de groupe. Il ne peut pas effectuer d’opérations de lien rapide (groupes Modifier/Publier/Supprimer) dans AEM instance d’auteur (NPR-30810).
* Les informations des groupes/groupes de membres ne sont pas visibles lors de la création d’un site dans AEM instance d’auteur (NPR-28840).

##### Formulaires {#forms-6470}

>[!NOTE]
>
>Le Service Pack AEM n’inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un module complémentaire Forms distinct.  En outre, un programme d’installation cumulatif est publié, qui comprend des correctifs pour AEM Forms on JEE. Pour plus d’informations, voir [Installation du module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installation du programme d’installation d’AEM Forms JEE](#install-aem-forms-jee-installer).

**Package de modules complémentaires Forms**

**Formulaires adaptatifs**

* Les chaînes contiennent la clé du dictionnaire lors de la localisation des formulaires adaptatifs (NPR-31109).

* Les cases à cocher et les listes déroulantes dans Forms ne parviennent pas aux vérifications d’accessibilité (NPR-31282).

**Formulaires HTML5**

* La génération de l’aperçu HTML5 d’un formulaire XDP affiche un scintillement lors de l’ajout d’instances d’un sous-formulaire (NPR-30907).

**Services de document pour OSGi**

* L’exécution de plusieurs threads simultanés pour l’assemblage des formulaires à l’aide de la méthode com.adobe.fd.assAssembler.service.AssemblerService.invoke() affiche un message d’erreur (NPR-31164).

* Les fichiers temporaires créés par le service Assembler ne sont pas supprimés automatiquement et nécessitent un redémarrage AEM (NPR-30846).

* L’application des droits ReaderExtension à PDF génère un message d’erreur (NPR-30930).

**Processus**

* Le workflow OSGi échoue en raison de l’utilisation 100 % du processeur (NPR-31234).

**Programme d’installation de Forms JEE**

**Services de document**

* Le service Convert PDF ne parvient pas à convertir les documents du PDF en PostScript et affiche un message d’erreur (NPR-31267).

* La configuration du point d’entrée SOAP est réinitialisée après l’application d’un correctif pour corriger le HTML en cas d’échec du PDF (NPR-31309).

**Service PDFG**

* Impossible de télécharger le fichier de paramètres Adobe PDF téléchargé à l’aide de l’interface utilisateur d’administration (NPR-31273).

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0 est une mise à jour importante qui comporte des améliorations et correctifs pour les performances, la stabilité, la sécurité et les bogues signalés par les clients depuis la mise à disposition d’AEM 6.4 dans **Avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.6.0 inclut tous les Service Packs AEM version 6.4 avant sa publication.

Voici quelques-uns des points forts d’AEM 6.4.6.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.15.
* Ajout de la prise en charge du suivi des états de l’interface utilisateur dynamique dans le suivi des événements dans l’API foundation.
* Ajout de la prise en charge du rendu au composant principal de l’image.

**Ressources**

* Lien de partage de ressources d’un dossier avec espace et `&` dans le nom affiche des cartes grises vierges pour certaines ressources. NPR-29934 : correctif pour CQ-4270187
* Le workflow de gestion des actifs numériques se bloque lors de la création de ressources MP4 pour AEM. NPR-30031 : correctif pour CQ-4271352
* Problème de connectivité d’Adobe Smart Tag via Datapower. NPR-30026 : correctif pour CQ-4269457
* Le PDF est introuvable à l’aide d’OmniSearch. NPR-30046 : correctif pour GRANITE-26290
* Les chemins d’accès aux ressources dans les URL et les métadonnées des dossiers générés par l’API ACP ne sont pas codés dans les URL.  GRANITE-26198 : correctif pour CQ-4271814
* La fonctionnalité Créer une tâche de révision ne fonctionne pas en raison d’une charge utile non définie. NPR-30469 : Correctif CQ-4274263
* La possibilité de basculer du mode Carte au mode Liste et vice versa disparaît après une recherche Omni dans le sélecteur de ressources. NPR-29852 : correctif pour CQ-4269369
* (IU tactile) Lors de l’assistant de gestion de publication, les ressources sont ajoutées à la file d’attente de réplication après l’ajout des pages, ce qui entraîne l’affichage de certaines ressources au bout de quelques secondes. NPR-29985 : correctif pour CQ-4270724
* Le tri des requêtes par pertinence renvoie des documents InDesign ainsi que des modèles InDesign. Correctif pour CQ-4273864
* Si l’utilisateur dispose d’un ID de courrier électronique en majuscules, il n’est pas possible d’archiver les fichiers qui ont été précédemment extraits. Correctif pour CQ-4276575
* Configuration des Cloud Services Dynamic Media dans `DMHybrid` entraîne la création de plusieurs suites de rapports vides dans Analytics, sans identifiant de suite de rapports stocké sur AEM, ce qui entraîne la duplication des suites de rapports. Correctif pour CQ-4276855
* La boîte de dialogue d’avertissement n’apparaît pas lors de la promotion dans la page &quot;Balise gérée&quot;. Correctif pour CQ-4252851
* Lors de l’utilisation du carrousel pour la gestion des balises, le bouton de navigation ne fonctionne pas. Correctif pour CQ-4275499
* La fonctionnalité de déplacement massif des ressources est rompue, ce qui entraîne la non-circulation des ressources. Correctif pour CQ-4272987

**Sites**

* `pageinfo.json` les demandes sont extrêmement lentes et prennent trop de temps à se charger. NPR-29709 : correctif pour CQ-4269560
* `onTime` ou `offTime` les propriétés de métadonnées enregistrées sur les ressources ne sont pas rappelées si le serveur AEM est redémarré. NPR-30413 : correctif pour CQ-4272784
* En raison d’un comportement incorrect de la classe ConfigPostProcessor, la suspension de la page parente supprime cq : Type de mixage LiveRelationship de la page enfant. NPR-30536, NPR-30510 : correctif pour CQ-4254113
* Cross-site scripting (XSS) sur la boîte de dialogue Démarrer le workflow dans la page d’édition de Campaign. NPR-29747 : correctif pour CQ-4271067
* (IU classique) L’étape de verrouillage de workflow désactive l’onglet de workflow jusqu’à ce que le verrouillage soit libéré. NPR-30356 : correctif pour CQ-4237557
* (IE11) Lorsque vous collez du contenu de HTML dans un composant Éditeur de texte enrichi avec defaultPasteMode = texte brut, le HTML est collé avec la mise en forme. Par conséquent, defaultPasteMode n’a aucun effet. NPR-30045 : correctif pour GRANITE-26094
* (IU classique) Lorsque la page d’administration du site est rechargée, tous les éléments de liste déroulante du menu &quot;Nouveau&quot; sont désactivés. NPR-29980 : correctif pour CQ-4272044
* Impossible d’ajouter des styles au texte ou de modifier les styles existants créés sur le contenu. NPR-29712 : correctif pour CQ-4266249
* (IU classique) Ressources sans dc : La valeur de titre est répertoriée sans titre dans le navigateur de la boîte de dialogue du champ de chemin d’accès. NPR-30166 : demande de rétroportage pour CQ-88858
* Le cq : l’écouteur ne fonctionne pas avec les composants imbriqués, même après l’ajout du composant parsys. NPR-30422 : correctif pour CQ-4274863
* Erreur ContextHub durant l’intégration d’AEM et de Campaign. NPR-30625 : correctif pour CQ-4250790
* La valeur du paramètre de requête resourceType est copiée dans la valeur d’un attribut de balise HTML encapsulé dans des guillemets doubles. NPR-29832 : correctif pour CQ-4255365
* Une actualisation de page est nécessaire une fois les composants copiés et collés d’une page vers une autre. NPR-29982 : correctif pour CQ-4256019
* La publication/annulation de la publication d’un alias de page n’est pas prise en charge et doit être supprimée. NPR-30062 : correctif pour CQ-4271249
* Avertissement ResourceResolver non fermé dans ExperienceFragmentsReplicationListener entraînant des problèmes de stabilité au fil du temps, forçant à redémarrer les instances AEM. NPR-30416 : correctif pour CQ-4257521
* Le déplacement des fragments d’expérience référencés dans plus de 150 pages ne modifie pas fragmentPath dans les pages où ils sont référencés. NPR-30556 : correctif pour CQ-4274900
* Erreur d’analyse lors de l’ouverture d’un fragment de contenu contenant des caractères dollar (`$`) et ouvrez l’accolade (`{`) l’un après l’autre. Correctif pour CQ-4270266
* VersionPreviewServlet échoue dans NullPointerException lors de l’affichage d’une version d’un fragment d’expérience dans la chronologie. NPR-30074 : correctif pour CQ-4271881
* Impossible de verrouiller les fragments de contenu via la fonction d’archivage. NPR-29923 : correctif pour CQ-4258785
* Échec de vérification de signature dans le gestionnaire d’authentification SAML. NPR-30379 : Demande de rétroportage pour GRANITE-26567

**Réplication**

* Le résolveur de session/ressource JCR est divulgué lors de l’implémentation OAuth sur chaque réplication vers MAC/Brand Portal. NPR-30000 : correctif pour Granite-26196

**Sling**

* L’ordre des enfants affectés à l’aide des chevauchements et de l’ordre précédent provoque IndexOutOfBoundException. NPR-30408 : Correctif pour Sling-8296 et Sling-7375
* InactiveBundlesHealthCheck lit la configuration MissingPackagesHealthCheck une fois les configurations InactiveBundlesHealthCheck enregistrées. NPR-30084 : correctif pour CQ-4272644

**Commerce**

* Impossible d’exécuter le plan directeur de catalogue à partir de la console Sites. NPR-29829 : correctif pour CQ-4271461
* La ressource utilisée dans le produit n’affiche aucune référence au produit dans la section &quot;Références&quot; de la ressource, et le chemin de la ressource n’est pas mis à jour si la ressource est déplacée. NPR-30542 : correctif pour CQ-4270247

**Plate-forme**

* AEM Default Mail Sender ne peut pas envoyer de courrier à un serveur SMTP distant via TLS v1.2. NPR-30476 : Correctif pour GRANITE-26605

**Communities**

* Les groupes supprimés sur l’auteur ne sont pas synchronisés avec tous les éditeurs. NPR-29987 : correctif pour CQ-4268738
* Les utilisateurs supprimés du champ Administrateurs de la communauté ne sont pas synchronisés avec le groupe Appartenance. NPR-30389 : correctif pour CQ-4274339
* Les utilisateurs appartenant au groupe des administrateurs ne disposent pas de liens rapides pour le groupe. NPR-30546 : correctif pour CQ-4275579
* La mise à jour de tout nouveau groupe de communauté existant et créé remplace la propriété sur jcr : noeud de contenu et remplace leur nom par le titre de la première page. NPR-30109 : correctif pour CQ-4273719
* La recherche rapide et la recherche dans l’emplacement et l’adresse ne fonctionnent pas lorsque la communauté est configurée pour fonctionner avec le fournisseur de ressources de stockage de base de données (DSRP). NPR-26737 : correctif pour CQ-4258493

**Traduction**

* L’exécution automatique de la traduction ne fonctionne pas. NPR-30499 : correctif pour CQ-4276288
* L’utilisateur peut créer une copie de langue sur le chemin du contenu limité à la lecture seule. NPR-29937 : correctif pour CQ-4270708
* Problème de traduction : seuls quelques composants sont traduits à l’aide de la traduction automatique. NPR-30079 : correctif pour CQ-4273764

**Intégration**

* Le contenu personnalisé ne s’affiche pas correctement sur l’instance de publication tant que l’instance n’a pas été redémarrée. NPR-30421 : correctif pour CQ-4273706

**Projets**

* Les valeurs dam:folderThumbnailPaths ne sont pas actualisées et n’affichent pas les anciennes miniatures, même après la suppression des fichiers dans le dossier. NPR-30424 : correctif pour CQ-4273667

**UI-Consoles**

* Cross-site scripting (XSS) sur les propriétés de page Sites sous l’onglet Miniature. NPR-30048 : correctif pour Granite-26200

**UI-Foundation**

* Ajout de la prise en charge du suivi des états de l’interface utilisateur dynamique dans le suivi des événements dans l’API foundation. NPR-30742, GRANITE-26322 : Correctif pour GRANITE-26036

**Forms**

>[!NOTE]
>
>Le Service Pack AEM n’inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un module complémentaire Forms distinct.  En outre, un programme d’installation cumulatif est publié, qui comprend des correctifs pour AEM Forms on JEE. Pour plus d’informations, voir [Installation du module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installation du programme d’installation d’AEM Forms JEE](#install-aem-forms-jee-installer).

**Package de modules complémentaires Forms**

**Formulaires adaptatifs**

* La récupération du fichier .css vide prend plus de temps à partir de l’éditeur, ce qui entraîne des problèmes de performances. NPR-30558 : correctif pour CQ-4274399
* Les Forms qui sont modifiées après la publication ne sont pas republiées lors de la publication du site. NPR-30411 : correctif pour CQ-4236566

**Forms - Intégration du serveur principal**

* Une erreur est générée lors de la création du modèle de données de formulaire avec le langage WSDL (Web Service Definition Language). NPR-30388 : correctif pour CQ-4272921

**Forms - Gestion de correspondance**

* Les caractères spéciaux tels que less-than (&lt;), greater-than (>) et ampersand (&amp;) sont codés dans l’interface utilisateur de l’agent. NPR-30410 : correctif pour CQ-4273887
* Lors du déclenchement d’un fragment de texte contenant des valeurs du dictionnaire de données, l’interface utilisateur de l’agent ne répond plus. NPR-30098, NPR-30083 : correctif pour CQ-4272204
* L’interface utilisateur de création de correspondance (CCR UI) échoue par intermittence avec la variable d’erreur (objet Object). NPR-29983 : correctif pour CQ-4273874
* Le rechargement du brouillon de lettre échoue avec une exception lorsque la description des fragments de document contient des caractères spéciaux tels que inférieur à (&lt;), supérieur à (>) et une esperluette (&amp;) dans les propriétés. NPR-29930 : correctif pour CQ-4252762

**Formulaires HTML5**

* Lors de l’utilisation de l’option Accès aux ordinateurs de bureau non visuels en mode Navigation pour lire un formulaire HTML5, le navigateur Chrome affiche « graphic » avant chaque graphique vectoriel évolutif (SVG) dans la conception du formulaire. NPR-30450 : correctif pour CQ-4274732

**Programme d’installation de Forms JEE**

**Forms - Foundation JEE**

* L’ajout ou la modification d’une connexion à un service Web en appelant des services Web à partir d’AEM forms Workbench renvoie une erreur : ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116 : correctif pour CQ-4273217

**Forms - Document Services**

* Erreur manquante du libellé PDF/A dans le contrôle en amont Acrobat. NPR-30594 : correctif pour CQ-4276032
* Les liaisons de données à caractère unique en PDF provoquent l’échec des extensions de Reader avec l’erreur &quot;java.lang.StringIndexOutOfBoundsException : Index de chaîne hors plage : 1&quot;. NPR-30128 : correctif pour CQ-4273878
* Lorsqu’un test de chargement est effectué sur le service HTML en PDF, il échoue avec une erreur et les paramètres de type de fichier sont supprimés du serveur AEM Forms. NPR-30085 : correctif pour CQ-4272631
* L’aplatissement d’un PDF avec Adobe Acrobat 9.1 (XFA version 3.0) ne conserve pas l’état du formulaire du PDF : Les éléments invisibles du formulaire sont redéfinis sur un état visible. NPR-29978 : correctif pour CQ-4270888

**Forms - Document Security**

* L’application d’une signature avec horodatage échoue avec l’erreur : ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException : Erreur d&#39;appel. NPR-30696, NPR-30537 : correctif pour CQ-4273778
* Configuration Manager n’insère pas de chaînes japonaises pour les colonnes de tableau localisées. NPR-30496 : correctif pour CQ-4274868

**Service PDFG**

* Erreur de connexion lors de la tentative de conversion du document Word en PDF sous Windows Server 2016. NPR-30597 : correctif pour CQ-4275652
* L’autorisation a refusé l’exception lors de la tentative d’utilisation du service principal HTML vers PDF via la bibliothèque &quot;phantomjs&quot;. NPR-30456 : correctif pour CQ-4258077
* maxReuseCount pour le service HTML à PDF n’est pas affiché avec la console de gestion JBoss. NPR-30303, NPR-30135 : correctif pour CQ-4273763

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0 est une mise à jour importante qui inclut des améliorations et correctifs pour les performances, la stabilité, la sécurité et les bogues signalés par les clients depuis la mise à disposition d’AEM 6.4 dans **Avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.5.0 inclut tous les Service Packs AEM version 6.4 avant sa publication.

Voici quelques-uns des points forts d’AEM 6.4.5.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.13.
* Ajout du délai d’expiration du socket et du délai de connexion dans les agents de réplication Brand Portal.
* Améliorations de l’omni-recherche : Augmentation de la limite de pagination du résultat de recherche à 100 pages.
* Désactivé `AssetDownloadServlet` Composant OSGi par défaut sur AEM instances de publication. Pour plus d’informations, voir [Téléchargement de ressources à partir d’AEM](/help/assets/download-assets-from-aem.md).
* Activation de la prise en charge du Gestionnaire de sites multiples pour les ressources. Pour plus d’informations, voir [Réutilisation de ressources à l’aide de MSM pour Assets](/help/assets/reuse-assets-using-msm.md).

**Ressources**

* Les ressources dont le nom de fichier contient une apostrophe ne sont pas synchronisées avec Dynamic Media. NPR-29538 : correctif pour CQ-4270592
* Mise à jour de l’interface DAM DMGateway pour la prise en charge multipartie S3. NPR-29740 : correctif pour CQ-4226303
* La boîte de dialogue de téléchargement de ressources affiche une taille de fichier incorrecte lors du téléchargement des rendus d’une vidéo dans Dynamic Media. NPR-29642 : correctif pour CQ-4246202
* Les ressources deviennent inutilisables après que le service Day CQ DAM Mime Type applique le texte pour m3u8. NPR-29276 : correctif pour CQ-4264052
* L’ajustement de référence de ressource ne parvient pas à enregistrer la session si l’une des ressources déplacées/renommées fait partie de collections de ressources Sling. NPR-29143 : Correctif pour /CQ-4252605
* Impossible de suivre ou de rechercher des ressources en recherchant les valeurs des métadonnées. NPR-29141 : correctif pour CQ-4260215
* Lorsque vous utilisez le filtre de recherche pour enregistrer une collection dynamique, l’action de clic sur le panneau ne conserve pas la cible d’action. NPR-29000 : correctif pour CQ-4240323
* Le déplacement d’un dossier permet de créer un dossier dont les noms sont en majuscules ou en minuscules. NPR-28945 : correctif pour CQ-4265234
* Les résultats vides s’affichent dans Omni-recherche si le nom de la collection comporte de l’espace. NPR-29001 : correctif pour CQ-4236729
* Le fait de renommer un fichier à l’aide de caractères spéciaux non pris en charge tels que l’esperluette (&amp;) crée un dossier non valide. NPR-29196 : correctif pour CQ-4265037
* La fonctionnalité DAM Extract Archive for zip est incorrecte. NPR-29187 : correctif pour CQ-4254421
* L’importation de métadonnées doit permettre l’importation de métadonnées sans enregistrer d’espaces de noms. NPR-29425, NPR-28132 : correctif pour CQ-4269445
* L’enregistrement des modifications apportées aux métadonnées ne fonctionne pas pour les ressources dont le nom contient un guillemet. NPR-29395 : correctif pour CQ-4254305
* Impossible de déplacer une ressource DAM si le nom de fichier contient un espace. NPR-29270 : correctif pour CQ-4266403
* Impossible de télécharger les archives ZIP compressées avec l’algorithme Deflate64. NPR-29225 : correctif pour CQ-4253995
* Les miniatures des ressources s’affichent lentement lors de l’ouverture d’un dossier contenant des ressources de plusieurs versions. NPR-29833 : correctif pour CQ-4271629
* Impossible de saisir la collection mise en surbrillance si la touche Entrée est enfoncée après la sélection de la collection. NPR-29723 : correctif pour CQ-4261607
* Attaque de script de site à site (XSS) via la fenêtre d’alerte limitée. NPR-29671 : correctif pour CQ-4270133
* L’ajout de relations à des ressources échoue pour les utilisateurs ne disposant pas d’autorisations de suppression. NPR-29640 : correctif pour CQ-4269196
* Après avoir ajouté le titre de la ressource dans la page des propriétés, lorsque l’utilisateur tente de fermer la page, AEM rouvre la page des propriétés. NPR-29628 : correctif pour CQ-4264929
* La création d’un grand nombre de relations sur une ressource entraîne une erreur. NPR-28779 : correctif pour CQ-4250708
* L’ingestion des ressources est lente en mode d’exécution Scene7 Connect. NPR-28658 : correctif pour CQ-4263007
* Une erreur Uncaught TypeError : Impossible de lire la propriété &quot;split&quot; d’undefined s’affiche lors de la tentative d’affichage des résultats de recherche. NPR-28803 : correctif pour CQ-4248371
* La réplication d’AEM vers Brand Portal est bloquée pendant de longues périodes. NPR-28914 : correctif pour CQ-4254932
* Le déplacement de ressources dans la gestion des ressources numériques n’entraîne pas un déplacement similaire dans Scene7. NPR-28957 : correctif pour CQ-4264974
* Les mises à jour de métadonnées ne sont pas transmises à IPS si le champ de métadonnées est mis à jour dans AEM. NPR-28961 : correctif pour CQ-4255393
* VersioningTimelineEventProvider doit fournir la version racine avec le commentaire de version. Correctif pour GRANITE-26063
* L’ingestion de données entraîne l’exécution de code du côté serveur. Correctif pour CQ-4270246
* Activation de la prise en charge du Gestionnaire de sites multiples pour les ressources. Correctif pour CQ-4271453, CQ-4268621, CQ-4257491
* L’interface AEM doit afficher une entrée supplémentaire pour la version actuelle de la ressource dans la chronologie, affichant le dernier commentaire d’arrivée à partir d’Adobe Asset Link. Correctif pour CQ-4262864
* L’exemple de vidéo ne se charge pas lors de la création ou de la modification d’un visionneuse de supports variés. Correctif pour CQ-4244889
* La désactivation des autorisations de suppression de contenu côté AEM empêche l’utilisateur de publier du contenu sur Brand Portal. Correctif pour CQ-4270426
* Problèmes liés à la limite de requête avec les rapports de ressources après la mise à niveau vers AEM 6.4.3. NPR-28588 : Correctif pour CQ-4262022, CQ-4260697
* La fonctionnalité de téléchargement exploite AEM Assets par le biais du servlet de téléchargement de ressources, ce qui permet aux utilisateurs anonymes de télécharger toutes les ressources. NPR-27315, correctif pour CQ-4254732

**Sites**

* Le nom de la balise de plainte JCR doit être automatiquement renseigné en fonction du titre de la balise. NPR-28990 : correctif pour CQ-4199411
* Le bouton Annuler l’héritage n’est pas visible sur certains champs ajoutés dans les propriétés de la page. NPR-29079 : correctif pour CQ-4265686
* L’action d’aperçu du déploiement ne doit pas essayer de recréer la Live Copy ni de l’afficher dans la liste des pages de déploiement. NPR-29151 : correctif pour CQ-4266213
* (Éditeur de modèles) Régression de stratégie de style en mode structure. NPR-28981 : correctif pour CQ-4264400
* Les Live Copies imbriquées affichent des entrées en double lors du déploiement. NPR-29300 : correctif pour CQ-4268664
* La publication d’une Live Copy d’une Live Copy contenant un composant Importateur de conception échoue avec l’échec de la récupération des références pour la page sélectionnée. NPR-28944 : correctif pour CQ-4265014
* CoralUI, lorsqu’il est utilisé avec Multifield, stocke le paramètre fileReferenceParameter au niveau du composant et non au niveau de plusieurs champs. NPR-29536 : correctif pour CQ-4266129
* La référence de conception n’est pas répliquée lors de la publication après l’annulation de l’héritage sur l’importateur de conception. NPR-29648, NPR-29721 : correctif pour CQ-4269270, CQ-4271087
* Le champ de chemin dans l’éditeur de texte enrichi s’ouvre au chemin racine, quel que soit le chemin spécifié pour la recherche. NPR-29483 : correctif pour CQ-4268997
* (IE11) Copiez Coller le contenu du HTML dans un composant d’éditeur de texte enrichi avec defaultPasteMode = texte brut ne colle pas le contenu en tant que texte brut. NPR-29432, NPR-29171 : Correctif pour GRANITE-24941
* La vérification orthographique de l’éditeur de texte enrichi ne fonctionne plus dans d’autres langues. NPR-29506 : correctif pour CQ-4264990
* Cross-site scripting (XSS) sur la page Campaign. NPR-29614 : correctif pour CQ-4269322
* La réduction de l’éditeur de texte enrichi à partir du mode plein écran en mode modification de la source entraîne une perte de contenu. NPR-29574 : correctif pour CQ-4260584
* (IU classique) Il n’est pas toujours possible d’accéder au dernier onglet lorsqu’il existe un grand nombre de balises. NPR-29544 : correctif pour CQ-4264548
* (IU classique) Le menu de navigation du Admin Console disparaît et la page ne se charge pas complètement. NPR-29571 : correctif pour CQ-4264585
* Une alerte d’erreur est générée lors de l’ajout de composants à la page WCM lorsque la minification est activée sur l’instance. NPR-29396 : correctif pour CQ-4266196
* Problème lié à l’héritage des noeuds Système de style du parent. NPR-29296 : correctif pour CQ-4266041
* La page restaurée avec la distorsion du temps doit faire référence à l’image correcte au moment du contrôle de version.  NPR-29431 : correctif pour CQ-4262638
* Page vierge contenant des erreurs Javascript dans l’éditeur après l’installation de la dernière version d’instantané 6.4.5. NPR-29475 : correctif pour CQ-4266196
* Lors de l’ajout d’un composant à un parsys, la propriété de liste de composants de conception n’est pas respectée et est résolue sur un nom de noeud de modèle différent avec une structure parsys similaire. NPR-29509 : correctif pour CQ-4269044
* La zone cq:dropTargets couvre l’ensemble du composant au lieu de la taille de l’image, rendant le ciblage difficile avec les composants incorporés. NPR-29738 : correctif pour CQ-4268912
* Le composant d’image n’appelle pas l’écouteur &quot;afteredit&quot; après l’utilisation de l’éditeur statique d’image. Correctif NPR-29616 pour CQ-4268065
* Problème lors de la configuration de la publication sociale sur Facebook. NPR-29212 : correctif pour CQ-4266630
* Lors de la promotion du lancement des pages modifiées, les modifications des branches source et de lancement sont prises en compte. NPR-29308 : correctif pour CQ-4266746
* La miniature générée sur le fragment de contenu affiche une représentation de calendrier interne pour les champs Date et Heure. NPR-29531 : correctif pour CQ-4269362
* Impossible d’ajouter en masse une balise aux pages contenant des balises différentes existantes. NPR-28729 : correctif pour CQ-4262922
* L’icône Activation planifiée ne s’affiche pas dans l’administrateur du site. NPR-28725 : correctif pour CQ-4263917

**Réplication**

* Vulnérabilité de divulgation des informations sensibles dans le composant Agent de réplication. NPR-29612, NPR-24951 : Correctif pour GRANITE-25070
* Les données fournies par l’utilisateur ne sont pas ignorées lors de la sortie dans le composant cq/Replication/components/agent, ce qui entraîne une vulnérabilité Cross-site scripting (XSS) par stockage. Correctif pour CQ-4266263

**Fragments d’expérience**

* Impossible d’exporter les fragments d’expérience vers la cible lorsque une image dynamique est utilisée. Correctif pour CQ-4269606

**Social - Création de rapports**

* Les rapports de communauté AEM ne s’affichent pas dans AEM instance d’auteur. Correctif pour CQ-4266294

**Plate-forme**

* Cross-site scripting (XSS) dans le gestionnaire de packages lors de l’installation d’un package. NPR-29734, NPR-29713, NPR-29630 : Correctif pour GRANITE-26161, GRANITE-
* Plusieurs scripts intersites stockés et reflétés (XSS) dans CRXDE Lite. NPR-29634 : correctif pour GRANITE-26049
* La fonctionnalité de connexion du partage de modules utilise une requête de GET plutôt qu’une requête de POST, ce qui rend le mot de passe visible sous l’onglet réseau. NPR-29631 : correctif pour GRANITE-26048

**Felix**

* Script intersite (XSS) observé dans la console système. La page est chargée et la fenêtre contextuelle s’affiche lorsque le pointeur de la souris survole le champ de texte. NPR-29853, NPR-29633 : Correctif pour GRANITE-26188, GRANITE-26050

**Granite**

* La configuration de l’enregistreur de journalisation Apache Sling ne filtre pas le script injecté.  NPR-29775 : correctif pour GRANITE-26051

**Communautés**

* Les groupes supprimés sur l’instance de création doivent être supprimés des instances de publication. NPR-28933 : correctif pour CQ-4264645
* Le secret de l’application doit être protégé par un champ de mot de passe, et non affiché en texte brut pour les outils de connexion sociale. NPR-29728 : correctif pour CQ-4270480
* Les visiteurs et les membres, sans privilèges de modérateur, peuvent voir les publications non approuvées/en attente en collant l’URL. NPR-29726 : correctif pour CQ-4271124, CQ-4271441
* Un temps de réponse élevé allant jusqu’à 40-50 secondes est observé lors de la connexion de l’utilisateur à la Communauté. NPR-29678 : correctif pour CQ-4269444

**Traduction**

* Les utilisateurs n’ayant pas accès aux fonctions de traduction dans la navigation ne doivent pas pouvoir accéder à ses sous-pages. NPR-29644 : correctif pour CQ-4269979
* Les autorisations utilisateur non confirmées en tant qu’assistant permettent de créer la copie de traduction à un emplacement en lecture seule. NPR-29375 : correctif pour CQ-4265877

**IU - Fondation**

* Augmentation de la limite de pagination des résultats de recherche à 100 pages pour le mode Carte et à 200 pages pour le mode Liste. NPR-29332 : correctif pour GRANITE-24644
* En raison du chargement différé des balises, rien ne s’affiche sur la page de collection. NPR-29267 : correctif pour GRANITE-24902
* La modification de la limite de pagination à 100 au lieu de 40 déclenche un chargement différé supplémentaire sans demande de pagination. NPR-29246 : correctif pour GRANITE-25027
* Le champ AEM mot de passe granite n’est pas renseigné après le chiffrement. NPR-29245 : correctif pour GRANITE-24908

**Intégration**

* Un message d’exception s’affiche lorsque vous essayez de modifier et d’enregistrer la configuration de lancement de l’AEM. NPR-29086 : correctif pour CQ-4266153
* Échec des informations d’identification BrightEdge en cas d’erreur de connexion.  NPR-29167 : correctif pour CQ-4265872
* La case héritée de la case à cocher qui s’affiche au niveau racine dans les configurations de Cloud Service doit être supprimée. NPR-27856 : correctif pour CQ-4259676

**Sling**

* Le délai d’expiration de la connexion HTTP n’est pas lu à partir des configurations. NPR-29264 : correctif pour SLING-7902
* L’écriture différée du programme d’installation JCR entraîne l’utilisation d’un format non valide dans la configuration OSGi et bloque le redéploiement. NPR-29027 : correctif pour CQ-4264694

**Projets**

* Les utilisateurs ne peuvent pas terminer le workflow du projet. NPR-29621 : correctif pour CQ-4258791
* La liste Workflow du projet affiche des lignes vides au-delà de 40 workflows. NPR-28739 : correctif pour CQ-4264005
* Lorsque vous sélectionnez l’option Rendu dynamique dans Brand Portal, un fichier .zip vide est téléchargé. NPR-29420 : correctif pour CQ-4268826
* La publication des ressources du dossier /content/dam/mac d’AEM Author vers Brand Portal ne fonctionne pas. NPR-29820 : correctif pour CQ-4271118
* La ponctuation dans le nom entraîne des problèmes avec le bouton de publication. NPR-29573 : correctif pour CQ-4269317
* Impossible de créer une copie de langue de ressource via le panneau de référence. Correctif pour CQ-4269535

**Processus**

* La mise à niveau de la version 6.4.2 vers la version 6.4.4 interrompt le champ de sélecteur de calendrier du participant à la boîte de dialogue. NPR-29727 : correctif pour CQ-4270423

**WCM - Interface utilisateur d’administration**

* L’ouverture de l’onglet Autorisations dans l’implémentation Coral2 n’affiche pas les boutons. Correctif pour CQ-4269419

**WCM - MSM**

* La suppression d’un nœud enfant dans la Live Copy doit détacher les informations liveRelationship. Correctif pour CQ-4270395
* La mise à niveau vers AEM 6.4.3 fait que le déploiement de Multi-Site Manager prend du temps. Correctif pour CQ-4271410

**Vulnérabilité**

* La structure de protection CSRF ne fonctionne pas avec les formulaires AEM Foundation. NPR-28612 : correctif pour GRANITE-22231

**WCM - Éditeur de page**

* Les scripts intersites (XSS) se reflètent lors de l’utilisation d’un sélecteur non valide. Correctif pour CQ-4270397

**Forms**

Les principaux points forts d&#39;AEM Forms 6.4.5.0 sont les suivants :

**Package de modules complémentaires Forms**

**Formulaires adaptatifs**

* (IU tactile) L’option Démarrer le processus n’affiche pas la boîte de dialogue pour la configuration. NPR-29521 : correctif pour CQ-4269050

**Forms - Intégration du serveur principal**

* Activation de la prise en charge d’Active Directory Federation Services (ADFS) v3.0 pour l’intégration sur site de Microsoft Dynamics. NPR-30003, NPR-29484 : correctif pour CQ-4270586
* Le service de préremplissage échoue en raison d’un délai d’exécution prolongé du module d’intégration des données AEM Forms. NPR-28997 : correctif pour CQ-4265988
* La demande de service Web SOAP est incorrecte dans AEM Forms. NPR-29013 : correctif pour CQ-4265443
* Aucun message d’erreur ne s’affiche lors du test du service SOAP en cas de valeur de date incorrecte. Correctif pour CQ-4265445

**Forms - Communication interactive et Forms - Correspondence Management**

* L’interface utilisateur de création de correspondance (CCR UI) ne parvient pas à gérer un nombre flottant.  NPR-29210 : correctif pour CQ-4254201
* L’info-bulle définie sur une variable n’est pas visible dans l’interface utilisateur de création de correspondance (CCR UI). NPR-29739 : correctif pour CQ-4250533
* Impossible de copier ou coller à partir d’Omni-recherche dans les lettres. NPR-29808 : correctif pour CQ-4270783

**Formulaires HTML5**

* Lorsque nous ajoutons un espace dans le texte, le champ de texte ne permet pas de le remplir jusqu’à la fin. NPR-28844 : correctif pour CQ-4260239

**Programme d’installation de Forms JEE**

**Forms - Foundation JEE**

* Le composant Webservice d’AEM Forms Workbench ne peut pas appeler un service Web, qui nécessite une authentification SSL bidirectionnelle. NPR-29485 : correctif pour CQ-4246794
* Le gestionnaire de configuration d’AEM Forms JEE ne fonctionne pas avec plusieurs cartes d’identité. NPR-29236 : correctif pour CQ-4268598
* AEM erreur de démarrage provenant de GemFire : java.lang.IllegalStateException : Une seule connexion AdminDistributedSystem peut être établie en même temps. NPR-29524 : correctif pour CQ-4266295
* NoClassDefFoundError en raison d’une incohérence de la version du jar. NPR-28834 : correctif pour NPR-28834

**Forms - Document Services**

* Un fichier PDF/A non valide est signalé comme PDF/A valide à l’aide de l’opération isPDFA. NPR-29076 : correctif pour CQ-4261541
* Le PDF ne parvient pas à convertir PDF/A-1b avec le champ de formulaire sans le dictionnaire d’aspect. NPR-29534 : correctif pour CQ-4269618
* La conversion PDF/A du PDF produit avec le service Output ne passe pas la validation avec Acrobat DC. NPR-29647 : correctif pour CQ-4270448
* Le lot Apache POI échoue avec une exception. NPR-27861, NPR-28048 : correctif pour CQ-4245898, CQ-4244778

**Forms - Designer**

* Ajout de la prise en charge de PDF/UA aux formulaires XFA (XML Forms Architecture) générés à l’aide de Designer et de Output Service. NPR-23022

**Forms - Workflow**

* Les envois depuis l’espace de travail échouent avec le caractère Umlaut . NPR-29087 : correctif pour CQ-4263172

**Feature Packs inclus**

**Ressources**

* Activation de la prise en charge du Gestionnaire de sites multiples pour les ressources. Pour plus d’informations, voir [Réutilisation de ressources à l’aide de MSM pour Assets](/help/assets/reuse-assets-using-msm.md). NPR-26450 : correctif pour CQ-4259922

**Lots OSGI et packages de contenu inclus**

Le texte suivant répertorie les lots OSGI et les packages de contenu inclus dans le CFP.

Liste des lots OSGi inclus dans AEM 6.4.5.0

[Obtenir le fichier](assets/6.4.5.0_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.5.0

[Obtenir le fichier](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0 est une mise à jour importante qui inclut des améliorations et correctifs pour les performances, la stabilité, la sécurité et les bogues signalés par les clients depuis la mise à disposition d’AEM 6.4 dans **Avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.4.0 inclut tous les Service Packs AEM version 6.4 avant sa publication.

Voici quelques-uns des points forts d’AEM 6.4.4.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.11.
* Ajout de la prise en charge de la version du service de mise en cache afin d’éviter les demandes HTTP de version de service fréquentes.
* Ajout de la prise en charge de la suppression des balises automatiques.
* Mise en oeuvre d’un défilement sans fin pour l’assistant de catalogue.
* Possibilité de restreindre les autorisations en fonction des sites de la communauté (prise en charge).
* Correctifs de performances (mise en cache, exécution asynchrone, liste d’exclusion) pour le contrôle de l’intégrité du contenu Sling Granite.
* Ajout du bouton de sélecteur de ressources à la boîte de dialogue de vignette de page.
* Ajout d’une nouvelle propriété pour permettre le positionnement des info-bulles sur les champs.
* Amélioration de la prise en charge du sélecteur de couleurs dans le champ multichamp.
* Ajout d’une vérification afin d’ignorer les valeurs vides pour les champs multiples d’entrée numérique dans les clientlibs du fragment de contenu.
* Activation de la prise en charge de l’API Microsoft Translator Text v3.

**Ressources**

* Migration de l’intégration ACP-Stock vers AEM 6.4.4.0 NPR-27632
* La publication ultérieure d’un dossier de ressources vide avec des sous-dossiers entraîne la disparition des sous-dossiers. NPR-27558 : correctif pour CQ-4254701
* L’ajout de la propriété String\[\] à espace de noms unique entraîne une écriture différée XMP incomplète. NPR-26805 : correctif pour CQ-4254142
* Après avoir pixellisé le pdf d’entrée, la sortie produite comporte des images manquantes. NPR-27929 : correctif pour CTG-4150481
* L’assistant Déplacer les ressources affiche un nombre incorrect de pages de référencement pour les pages publiées. NPR-27833 : correctif pour CQ-4258014
* AssetPicker recherche uniquement la première balise pour filtrer le résultat lors du filtrage par balises. NPR-27778 : correctif pour CQ-4257705
* AEM gestionnaire de PDF prêt à l’emploi est bloqué sur le PDF de traitement avec des caractères étrangers. NPR-28778 : correctif pour CQ-4254234
* Lorsqu’un fichier CSV a une valeur qui est séparée par une virgule dans une seule colonne, AEM éditeur CSV n’échappe pas la virgule et la traite comme une colonne distincte. NPR-28801 : correctif pour CQ-4261694
* Problème avec l’éditeur de schéma de métadonnées lors de l’utilisation de l’explorateur de chemins d’accès pour sélectionner des données. NPR-28674 : correctif pour CQ-4263005
* Trop de ressources sont traitées dans le service de contenu dynamique, ce qui donne un temps énorme pour terminer le processus de balisage périodique. NPR-28640 : correctif pour CQ-4262661, CQ-4262644, CQ-4263234
* Les actions de bureau ne fonctionnent pas pour les résultats Omni-recherche provenant de `aem/start.html` page. NPR-27242 : correctif pour CQ-4248176
* L’API Assets n’autorise pas le téléchargement d’un fichier > 2 Go, ce qui entraîne l’échec du chargement. NPR-27629 : correctif pour Granite-23590
* Les métadonnées ne sont pas enregistrées dans la ressource téléchargée lors de la première tentative au cas où Dynamic Media serait activé sur l’instance. NPR-28233 : correctif pour CQ-4260759
* Le résolveur de service n’est pas fermé dans la configuration de SiteCatalyst. NPR-28015 : correctif pour CQ-4259397
* Le déplacement de ressources dans la gestion des ressources numériques n’entraîne pas un déplacement similaire sur Scene7 (configuration p2p). NPR-28313 : correctif pour CQ-4261091

**Sites**

* (IU classique) Une fraction des Live Copies s’affiche dans la liste de déploiement. NPR-28598, NPR-28574 : correctif pour CQ-4263410
* LiveRelationshipManagerImpl renvoie des exceptions lorsque cq:master est vide ou non valide. NPR-28590 : correctif pour CQ-4263115
* Le workflow &quot;Demande de suppression&quot; prêt à l’emploi ne supprime pas correctement les pages. NPR-28668 : correctif pour CQ-4263195
* L’interface utilisateur État de la relation n’affiche pas les valeurs d’année ou d’horodatage appropriées pour les champs coral-datepicker associés. NPR-28666 : correctif pour CQ-4263661
* Cross-site scripting (XSS) dans SuggestionHandler pour la version 6.4. NPR-28693 : correctif pour CQ-4253821
* Déplacer le dossier de siteadmin se termine en mémoire insuffisante et rend AEM indisponible. NPR-28346 : correctif pour CQ-4261398
* Les configurations de déploiement LiveCopy MSM sont perdues après la mise à jour. NPR-28311 : correctif pour CQ-4258705
* Impossible de faire défiler au-delà de 40 configurations de plan directeur. NPR-27640 : correctif pour CQ-4239166
* L’utilisation de SyntheticResource comme référence renvoie une exception de pointeur nul et bloque le déplacement des pages.  NPR-27576 : correctif pour CQ-4258262
* PushOnModify ne fonctionne pas sur la suppression sur l’instance mise à niveau 6.1 vers 6.4. NPR-28108 : correctif pour CQ-4259833
* (IU classique) Le bouton Annuler l’héritage est manquant et le composant peut être modifié sur une page Live Copy. NPR-28256 : correctif pour CQ-4260161
* OakState0001 : Conflits non résolus lors du déploiement. NPR-27982 : correctif pour CQ-4259548
* Lorsque vous copiez/collez une structure contenant des références SyntheticResource, le processus se termine par une erreur 500. NPR-27709 : correctif pour CQ-4259179
* Impossible d’arrêter les workflows en cours d’exécution lorsque les payloads sont activés. NPR-27672 : correctif pour CQ-4258520
* Le déploiement affiche les chemins de déploiement en double après la mise à niveau de la version 6.1 vers la version 6.4. NPR-27845 : Correctif pour CQ-4259487
* Intégrez le modal dam assetpicker dans le composant de miniature de page. NPR-28131 : correctif pour CQ-108042
* (IU classique) Impossible d’ouvrir les boîtes de dialogue avec le widget Balises. NPR-28575 : correctif pour CQ-4262680
* Le téléchargement de fichier multichamp n’affiche pas de zone de dépôt. NPR-28676 : correctif pour CQ-4263516
* Erreur « Valeur du sélecteur de récursivité non valide » lors de la migration d’un composant d’AEM 6.0 vers AEM 6.2. NPR-28609 : correctif pour CQ-4241258
* L’éditeur de texte enrichi de la boîte de dialogue scintille lorsque la fenêtre contextuelle d’un module externe est supérieure à la zone de texte, bloquant ainsi toute création ultérieure. NPR-27579 : correctif pour CQ-4257440
* (IU classique) L’éditeur cq:action ne fonctionne pas. NPR-28232 : correctif pour CQ-4257703
* La suppression des balises du panneau de recherche de ressources de filtre de balises de l’éditeur de page n’actualise pas correctement la liste. NPR-27983 : correctif pour CQ-4245567
* Si les valeurs de nombre à plusieurs champs sont vides, cliquer sur Enregistrer génère une invite de chargement infinie sans jamais avoir réellement terminé.  NPR-28400, NPR-28393 : correctif pour CQ-4244058, CQ-4244349
* Avec l’autorisation de lecture simple, les utilisateurs/groupes ne peuvent pas sélectionner un fichier XF et n’ont pas d’option pour afficher le fichier XF et ses propriétés de page. NPR-28341 : correctif pour CQ-4260412
* Les données JSON reçues de Target comportent un certain nombre de caractères d’échappement qui entraînent la coupure de la page de l’application. NPR-28318 : correctif pour CQ-4252043
* Impossible de modifier un composant après l’installation d’AEM 6.4.3. NPR-28125 : Correctif pour CQ-4261216
* La suppression de toutes les balises d’un champ de balise n’est pas conservée pour un fragment de contenu structuré. NPR-28133 : correctif pour CQ-4247241
* Lors de la modification d’une propriété &quot;jcr:lastmodifiedby&quot; et &quot;jcr:lastmodified&quot; d’un fragment de contenu, les valeurs sont mises à jour sans que l’utilisateur n’apporte de modifications. NPR-27847 : correctif pour CQ-4257138
* Améliorations de la comparaison de versions des fragments de contenu pour AEM 6.4. NPR-27764
* Si aucun modèle cq:allowedTemplates n’est défini sur /content/experience-fragments et que allowedPaths est utilisé sur le modèle de fragment d’expérience, une erreur est générée lorsque le fragment d’expérience est déplacé/copié. NPR-27487 : correctif pour CQ-4257489
* Le bouton Créer s’affiche lors de l’actualisation pour le nouvel utilisateur. NPR-27335 : correctif pour CQ-4255360
* Lors de la tentative de déplacement d’une page publiée, le nombre de &quot;pages de référencement&quot; qui s’affiche sur la première page de l’assistant &quot;Déplacer la page&quot; est incorrect. NPR-28111 : correctif pour CQ-4259663
* (IU tactile) Le rail de références n’affiche pas les liens entrants. NPR-28529 : correctif pour CQ-4262306
* Impossible de modifier les propriétés de composant et de page après l’installation d’AEM 6.4.3. NPR-27998 : Correctif pour CQ-4261216, CQ-4260441
* Migrez contexthub vers jquery 3. NPR-28397 : correctif pour GRANITE-19902

**Commerce**

* Impossible de sélectionner le catalogue s’il existe plus de 20 catalogues dans un dossier. NPR-27649 : correctif pour CQ-4258119
* Les assistants Commerce et les vues des propriétés sont rompus en raison de l’absence de header.referer. Correctif pour CQ-4261122

**Campaign - Ciblage**

* com.day.cq.pepersonalization.impl.TeaserResourceEventHandler se trouve dans une boucle infinie et entraîne des mises à jour des noeuds sur les instances de publication. Correctif pour CQ-4263096

**Réplication**

* Erreur lors de la création du contenu de réplication com.day.cq.replication.AccessDeniedException. NPR-28314 : correctif pour CQ-4261401
* Fuite de session lorsque l’ID de l’agent utilisateur est défini sur admin dans l’agent de réplication. NPR-28220 : correctif pour CQ-4255517

**DAM - Creative Cloud**

* Rétroportez l’API HTTP pour rechercher des images similaires dans AEM Assets. Correctif pour CQ-4254091
* Améliorez l’API ACP pour permettre que les résultats d’une requête soient limités aux membres d’une collection. Correctif pour CQ-4258708

**DAM - Formats**

* Une fois l’exportation des métadonnées déclenchée, la page est redirigée vers une page 404. Correctif pour CQ-4262447

**DAM - Général**

* (Intégration Adobe Stock) Le modal d’erreur du serveur s’affiche avec une erreur Oauth dans le fichier error.log. Correctif pour CQ-4260406
* L’intégration d’Adobe Stock ne fonctionne pas si la version 6.4.4 est appliquée à la version 6.4.3. Correctif pour CQ-4266009
* Le lien vers le modèle CF est manquant même après l’application du correctif SP3. Correctif pour CQ-4259029

**Plate-forme**

* (IU classique) Le bouton Modifier n’est pas disponible dans le composant Rapport de base après la mise à niveau vers la version 6.4.2. NPR-28560 : Correctif pour CQ-4262825
* Lorsque vous utilisez une requête combinant property.operation=like et property.depth, elle se retrouve dans InvalidQueryException. NPR-28570 : correctif pour CQ-4262652
* Erreur interne du serveur lorsque le noeud de langue nouvellement ajouté est supprimé du noeud de langue superposé. NPR-28661 : correctif pour CQ-4239194
* Exception de pointeur nul dans stderr.log dans le thread sling-oak-1 lors de démarrages aléatoires. NPR-28665 : correctif pour CQ-4237845

**Felix**

* webconsole.plugins.memoryusage bloque l’actualisation. NPR-27895 : correctif pour GRANITE-20715

**Granite**

* Sling Content Access Health Check effectue une validation excessive de /libs pour le chemin de recherche du résolveur de ressources personnalisé. NPR-28113 : correctif pour GRANITE-23529

**Gestion des fragments de contenu**

* Améliorations de l’utilisation et parité des fonctionnalités avec Assets pour les fragments de contenu. Correctif pour CQ-4253883

**Communautés**

* Mettez à niveau les bibliothèques d’amorçage vulnérables vers la version 3.4 et de l’éditeur de texte vers la version 4.5.11. NPR-28490 : Correctif pour CQ-4257511
* L&#39;annulation des modes de modification ne rétablit pas la pièce jointe supprimée. NPR-27902 : correctif pour CQ-4255150
* La composition au nom de la boîte ne doit être visible que par les membres privilégiés. NPR-27900 : correctif pour CQ-4251235
* Ajoutez rep:cache dans les noeuds ignorables de l’écouteur de synchronisation des utilisateurs d’AEM Communities sur les instances de publication. NPR-27842 : correctif pour CQ-4247234
* La zone de recherche affiche un caractère d’échappement au niveau de l’interface utilisateur. NPR-27838 : correctif pour CQ-4259757
* Une erreur est générée lors de la recherche de caractères spéciaux tels que ( , +, ? dans la recherche rapide. NPR-28213 : correctif pour CQ-4260969
* Créez un groupe &quot;administrateurs spécifiques à la communauté&quot; pour que les utilisateurs puissent modifier et créer le site de la communauté approprié. NPR-27731
* Ajout d’une logique pour que l’événement clavier ouvre la vidéo. NPR-27726 : correctif pour CQ-4254026
* Activation de la navigation au clavier pour les composants d’activation d’AEM Communities lors de la publication. NPR-27728 : correctif pour CQ-4254028
* Ajout d’un libellé aria pour le bouton d’affichage sous forme de liste ou de cartes. NPR-27727 : correctif pour CQ-4254027
* Gestion des sessions de résolveur de ressources ouvertes dans Social - Communities. NPR-27721 : correctif pour CQ-4258714

**Traduction**

* Prise en charge de l’API Microsoft Translator Text v3. NPR-28366 : correctif pour CQ-4249755
* jcr:language et cq:language ne sont pas automatiquement mis à jour dans la langue traduite. NPR-28338 : correctif pour CQ-4256046
* Les références cycliques provoquent StackOverflowError lors de la création d’une copie de langue. NPR-27596 : correctif pour CQ-4255621
* Dans un projet de traduction multilingue, cliquer sur Enregistrer et fermer les résultats dans les pages suivantes ajoutées au projet entraîne la création de nouveaux projets au lieu de nouvelles tâches de traduction créées dans le projet existant. NPR-28219, NPR-28236 : correctif pour CQ-4261276, CQ-4260731
* Chaîne d’erreur trop longue lors de l’ajout d’un fragment de contenu avec des données en bloc en raison de la limitation du nombre de caractères autorisés. NPR-28722 : correctif pour CQ-4262362

**Social**

* Le commentaire publié sur la page suivante est surligné en jaune chaque fois qu’un nouveau commentaire est publié. Correctif pour CQ-4261359
* Impossible de supprimer les commentaires dans le contenu créé par l’utilisateur à l’aide de l’API. NPR-28075 : correctif pour CQ-4261135
* AbstractNotificationOperationService provoque ClassCastException. Correctif pour CQ-4260456
* Supprimez la référence au cloud SCORM (Shareable Content Object Reference Model) dans le lecteur. Correctif pour CQ-4260779

**IU - Fondation**

* La fonction &quot;cache de sortie du système de fichiers&quot; intégrée au Gestionnaire de bibliothèques clientes du HTML interrompt la fonction &quot;debugClientLibs&quot; pour les scripts compilés tels que les fichiers LESS. NPR-27249 : correctif pour Granite-23313
* Le nombre de ressources affichées lorsque le mode de débogage est activé est toujours de 1 et de nombreuses erreurs JS sont générées dans la console du navigateur.  NPR-27575 : correctif pour GRANITE-23750
* Enregistrer et fermer sur les propriétés de page ne revient pas à la page correcte dans AEM WAR avec Tomcat. NPR-27566 : correctif pour GRANITE-23671

**Intégration**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` résulte en une boucle infinie et provoque des mises à jour des nœuds lors de la publication. NPR-28561 : correctif pour CQ-4263096
* Les actions cq  :actions ne sont pas prises en compte pour un composant ciblé. NPR-27616 : correctif pour CQ-4257497
* L’annulation de l’héritage de LiveCopy ne fonctionne pas correctement sur les conteneurs ciblés. NPR-28129 : correctif pour CQ-4259813
* (Configurations du service Cloud) La case « hérité de » qui apparaît au niveau racine doit être supprimée. NPR-27856 : correctif pour CQ-4259676

**Sling**

* Mise à jour de l’API des modèles Sling 1.3.8, Impl 1.4.10. NPR-27636 : Correctif pour GRANITE-23537

**OAK - Persistance des segments**

* SegmentBufferWriter n’est pas vidé après OnRC. NPR-27464

**Projets**

* Le projet de traduction multilingue ne crée pas plusieurs tâches linguistiques pour les utilisateurs qui ne font pas partie du groupe d’administrateurs. NPR-28508 : correctif pour CQ-4262023
* ProjectTaskListServlet fuit un ResourceResolver chaque fois que getTaskRenderers est appelé au démarrage du service. NPR-27590 : correctif pour CQ-4258011
* Si un répertoire contient plus de sous-répertoires que la taille de la page et que l’ordre est défini par date ou taille, une erreur empêche le déplacement au-delà de la première page. NPR-28867 : correctif pour CQ-4265039
* Rétroportez les correctifs de scripts intersites (XSS) dans les visionneuses de gestion des actifs numériques. NPR-28106 : correctif pour CQ-4253215
* Impossible d’ajouter des pages au projet de traduction par les administrateurs de projet, car le lien permettant d’ajouter de nouvelles pages au projet de traduction n’est pas visible. Correctif pour CQ-4266334

**Processus**

* Lorsque nous ouvrons la boîte de dialogue complète de l’élément de travail dans la notification de workflow qui comporte un champ Balise , un clic sur la marque croisée lui ajoute une propriété Balise. NPR-28304 : correctif pour CQ-4261321
* Le bouton d’activation/désactivation de la sélection de l’utilisateur de la boîte de dialogue Réaffecter la tâche ne fonctionne pas. NPR-28963 : correctif pour CQ-4264206

**Forms**

Les principaux points forts d&#39;AEM Forms 6.4.4.0 sont les suivants :

* Ajout de la prise en charge de l’enregistrement des API Document Security pour la signature et la certification en tant que transactions.

**Package de modules complémentaires Forms**

**Intégration Adobe Sign**

* AEM SDK client Forms 6.4 ne contient pas le package adign-recipient. NPR-27735 : correctif pour CQ-4259372

**Formulaires adaptatifs**

* Lorsque le formulaire adaptatif Wan est créé avec un modèle vierge, les clients ne peuvent pas ajouter de panneaux enfants au panneau racine du formulaire. NPR-28758 : correctif pour CQ-4264157
* Lorsque la valeur du composant de champ de date de l’année est 999, le script de validation échoue. NPR-28580 : correctif pour CQ-4262620
* Lorsqu’un formulaire adaptatif est créé avec un modèle vierge, les clients ne peuvent pas ajouter de panneaux enfants au panneau racine du formulaire. NPR-28758 : correctif pour CQ-4264157
* Impossible de définir la valeur entre les champs des fragments chargés en différé d’un formulaire adaptatif. NPR-27758 : correctif pour CQ-4259703
* Le formulaire adaptatif n’utilise pas l’éditeur de texte enrichi, mais charge ses bibliothèques.  NPR-27759 : correctif pour CQ-4259193
* La redirection vers l’URL ne fonctionne pas pour les formulaires adaptatifs incorporés dans une page AEM Sites. NPR-27620 : correctif pour CQ-4239287
* Impossible de définir la valeur entre les champs des fragments chargés en différé d’un formulaire adaptatif. NPR-28320 : correctif pour CQ-4262345
* Le formulaire adaptatif n’utilise pas l’éditeur de texte enrichi, mais charge ses bibliothèques.  NPR-28001 : correctif pour CQ-4259703, CQ-4259193
* La signature tactile ne fonctionne pas pour l’application AEM Forms s’exécutant sur Apple iOS 12.1. NPR-28497 : Correctif pour CQ-4261765
* Problèmes de création d’action Envoyer avec &quot;Forms Workflow&quot; Classic dans la version 6.4. Correctif pour CQ-4252740
* Suppression des blocs de gestion des erreurs et du stockage tmp. NPR-28806 : correctif pour CQ-4264441

**Forms - Gestion de correspondance**

* L’interface utilisateur de l’agent ne parvient pas à conserver la taille d’origine de l’image. NPR-28800 : correctif pour CQ-4259767
* CCR/Agent UI : Les libellés des champs Date sont décalés dans l’onglet Données. Correctif pour CQ-4255499

**Forms - Rapports de transactions**

* Ajout de la prise en charge de la comptabilisation à l’aide de signatures numériques ou de la certification d’un document en tant que transactions facturables. NPR-28495 : correctif pour CQ-4260236
* Ajout de la signature numérique et de la certification à l’API facturable. Correctif pour CQ-4260236

**Gestion de Forms**

Ajout de la prise en charge du remplacement de l’utilisation de la bibliothèque cliente handlebars par des traits de soulignement dans l’assistant de démarrage de la révision de Forms Manager et de l’assistant de déplacement des ressources. NPR-27643 : correctif pour CQ-4246536.
Un lot reste à l’état installé après l’installation du package de gestion Forms sur la branche release/640. Le correctif pour CQ-4265410 Forms envoyé avec des pièces jointes n’apparaît pas dans le workflow avec l’action d’envoi &quot;Appeler le processus AEM Forms&quot; et activer l’envoi du portail coché . Correctif pour CQ-4263110

**Forms - Intégration du serveur principal**

* Impossible de tester le préprocesseur/le post et l’envoi personnalisé à l’aide du SDK client, correctif pour CQ-4238469

**Programme d’installation de Forms JEE**

**Forms - Document Security**

* Lors de l’utilisation du service de mise à jour de stratégie, l’erreur d’objet impossible à interpréter se produit. NPR-28751 : correctif pour CQ-4252287
* Échec du build de signature avec l&#39;ancienne version de commons-pkg. Correctif pour CQ-4265535

**Forms - Foundation JEE**

* Lorsque AEM Forms est installé sur IBM WebSphere, la création d’un modèle de données de formulaire basé sur SOAP échoue. NPR-27923 : correctif pour CQ-4251134
* L’outil SRT de PDF Generator ne détecte pas la version installée d’Adobe Acrobat. NPR-27971

**Forms - Designer**

* Certaines images de JPEG dans un modèle XDP ne s’affichent pas correctement.  NPR-26702 : correctif pour LC-3917457

**Forms - Workflow**

* HTML5 Forms avec le processus d’envoi par défaut dans at.lca ne fonctionne pas sur JBoss 7. NPR-28675 : correctif pour CQ-4243928
* Impossible d’envoyer des PDF forms dans HTML Workspace. NPR-28058 : correctif pour CQ-4260373
* Les données client sont imprimées dans les journaux d’informations à l’aide du Forms Workflow Invoke FDM Service. Correctif pour CQ-4260385

**Feature Packs inclus**

**Sites**

* Le contrôle de version des fragments de contenu compare les améliorations de différence pour AEM 6.4. NPR-26760 : FP pour CQ-4248839
* Améliorations de la différence de variation des fragments de contenu pour AEM 6.4. NPR-27866 : FP pour CQ-4248839
* Fonctionnalité activée dans la configuration OSGI **Indicateur de fonction de retrait AEM workflow**. L’action de retrait doit arrêter l’instance de workflow après avoir défini l’indicateur . NPR-26451 : correctif pour CQ-4259090

**Plate-forme**

* Amélioration de l’extraction de facettes de Query Builder grâce à l’API Oak pour la version 6.4. NPR-26674 : FP pour CQ-4230337

**Lots OSGI et packages de contenu inclus**

Le texte suivant répertorie les lots OSGI et les packages de contenu inclus dans le CFP.

Liste des lots OSGi inclus dans AEM 6.4.4.0

[Obtenir le fichier](assets/bundles_6_4_4_0.txt)

Liste des packages de contenu inclus dans AEM 6.4.4.0

[Obtenir le fichier](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

AEM 6.4.3.0 est une mise à jour importante qui comporte des améliorations et correctifs pour les performances, la stabilité, la sécurité et les bogues signalés par les clients depuis le lancement d’AEM 6.4 en avril 2018.

Il est également cumulatif, ce qui signifie que la version 6.4.3.0 inclut tous les Service Packs AEM version 6.4 avant sa publication.

Voici quelques-uns des points forts d’AEM 6.4.3.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.9.
* Ajout de la prise en charge de la propriété allowedPaths sur les modèles de formulaires adaptatifs.
* Amélioration de la recherche par panneau des ressources dans AEM
* Correctifs de scripts intersites (XSS) sur la page Connexion .
* Amélioration de l’instrumentation de l’interface utilisateur.
* Améliorations de la gestion des données de formulaire.
* Amélioration de la gestion du nommage des éléments dans un champ multiple.
* Amélioration de la gestion des éléments d’espace réservé (mode Carte et mode Liste) lors de la sélection.
* Ajout de la prise en charge de l’authentification Adobe IMS et du Admin Console pour Managed Services.

**Ressources**

* Le workflow Ressources de mise à jour de gestion des actifs numériques n’extrait pas de références à partir de fichiers INDD si l’option Découple IDS est activée. NPR-26243; Correctif pour CQ-4250933
* Le message de réussite ne s’affiche pas lorsque des ressources sont publiées avec l’éditeur en bloc de ressources. NPR-26252; Correctif pour CQ-4251688.
* Après avoir consulté une ressource à partir d’un résultat de recherche, si vous cliquez sur le bouton Précédent dans le navigateur, un message d’erreur &quot;Requête incorrecte&quot; s’affiche avec le code d’erreur 400. NPR 26578; Correctif pour CQ-4253741
* Les métadonnées de ressource affichent une erreur d’espace de noms non valide après l’installation d’un Service Pack. NPR-22341; Correctif pour CQ-4237202
* L’option permettant de réorganiser les dossiers et les fragments de contenu en mode Liste ne s’affiche pas pour les dossiers concernés. NPR-27153; Correctif pour CQ-4255873
* Les utilisateurs ne peuvent pas ajouter de ressources à une nouvelle collection, car cela entraîne un message d’erreur avec une image rompue dans la boîte de dialogue contextuelle d’erreur. NPR-22431; Correctif pour CQ-4237086
* La liste déroulante en cascade n’est pas prise en charge dans les listes déroulantes dynamiques. NPR-27043; Correctif pour CQ-4252564
* Si les utilisateurs définissent une valeur autre que la valeur par défaut pour le &quot;dossier racine de l’entreprise&quot; dans la configuration cloud DMS7, le paramètre prédéfini de la visionneuse ne fonctionne pas comme prévu. NPR-26360; Correctif pour CQ-4249505
* La création de rapports de ressources échoue pour les instances comportant un très grand nombre de ressources. NPR-27278; Correctif pour CQ-4256748
* Les sous-dossiers n’héritent pas du profil d’image SmartCrop du dossier parent. NPR-27197; Correctif pour CQ-4256273
* Lorsque l’intégration Dynamic Media est activée, certaines propriétés de métadonnées des ressources sont modifiées. Les attributs width, height et location ne s’affichent pas. NPR-27203; Correctif pour CQ-4256258
* Dynamic Media n’utilise pas le proxy configuré pour certains types de ressources. NPR-25211; Correctif pour CQ-4244871
* La page Éditeur de métadonnées contient une exception de pointeur nul pour un paramètre d’élément non valide. NPR-26169; Correctif pour CQ-4241368.
* Si une règle de choix est appliquée à une liste déroulante et qu’une règle requise lui est appliquée, la règle requise ne peut pas être satisfaite dans l’éditeur de métadonnées. NPR-27479; Correctif de CQ-4251428

**Sites**

* Un utilisateur peut contrôler les fonctionnalités de l’éditeur de texte enrichi en mode plein écran en ligne à l’aide de stratégies de contenu, mais il ne peut pas contrôler les fonctionnalités de l’éditeur de texte enrichi de la boîte de dialogue avec les stratégies de contenu. NPR-26750 : correctif pour CQ-4241130
* L’éditeur de texte enrichi devient inutilisable lorsqu’il passe du mode plein écran à une boîte de dialogue flottante. La vue flottante contient deux éditeurs de texte enrichi. NPR-25589 : correctif pour CQ-4206008
* Lorsque la touche Retour (touche Entrée) est enfoncée dans un champ de texte, l’éditeur de texte enrichi passe en mode Plein écran. NPR-26204 : correctif pour CQ-4245893
* Le module externe Liste de l’éditeur de texte enrichi est désactivé automatiquement et n’autorise pas les modifications. NPR-26507 : correctif pour CQ-4239387
* Lorsqu’un caractère spécial est ajouté à la fenêtre de l’éditeur de texte enrichi, la fenêtre fait défiler la fenêtre vers le haut. NPR-26435 : correctif pour CQ-4249869
* Questions de caching ou de non caching de segment.js dans le contexte du client. NPR-26622 : correctif pour CQ-4253486
* Lorsqu’une règle enfant est activée de l’instance de création vers l’instance de publication, l’instance de publication cesse de fonctionner. NPR-26601 : correctif pour CQ-4253588
* En cas de combinaison de l’éditeur de texte enrichi avec plusieurs champs, l’erreur « Uncaught TypeError: fieldAPI.getName is not a function at foundation.js » se produit. NPR-27146 : correctif pour CQ-4253155
* L’intégration Salesforce ne peut pas utiliser la configuration du proxy. NPR-27244 : correctif pour CQ-4245300
* Lorsque vous planifiez l’activation d’une page à l’aide de l’option Gérer la publication pour une date ultérieure et que vous passez en mode Liste, l’icône de calendrier est absente. NPR-26974 : correctif pour CQ-4239206
* Les utilisateurs ne peuvent pas modifier les autorisations de groupe d’utilisateurs fermé dans les propriétés de la page. NPR-27138 : Correctif pour CQ-4256089 Impossible de modifier les balises par balisage. NPR-26957 : correctif pour CQ-4254858
* Lorsqu’une balise référencée à partir d’un modèle de fragment de contenu structuré est déplacée, les références existantes à la balise dans un fragment de contenu ne sont pas mises à jour. Cela se produit dans l’écran de modification du modèle de fragment de contenu. NPR-26776 : correctif pour CQ-4251805
* Lorsque vous créez et convertissez un lancement avec plusieurs pages, plusieurs versions de chaque page sont créées. NPR-26917 : correctif pour CQ-4254663
* AEM siteadmin ne gère pas les chemins d’accès saisis dans la barre d’adresse du navigateur. NPR-26780 : correctif pour CQ-4254097
* Lorsqu’une page est déplacée vers un nouvel emplacement sans la renommer, l’historique des versions de la page est perdu. NPR-26706 : correctif pour CQ-4254025
* Les URL de l’éditeur d’administration des fragments d’expérience n’autorisent pas les superpositions. NPR-26319 : correctif pour CQ-4252156
* Lorsqu’une page est créée avec un modèle contenant un fragment d’expérience vide et publiée, la page ne s’ouvre pas et une erreur DefaultSlingScript se produit. NPR-26305 : correctif pour CQ-4252460
* Lorsque data-sly-use est utilisé avec des classes portant le même nom, un code non conforme est généré. NPR-27282 : correctif pour Sling-7581
* Après l’installation du SP de mise à niveau, les sites ont une configuration de déploiement de plan directeur vide. NPR-27609 : correctif pour CQ-4257078

**DAM - Brand Portal**

* Les prédicats de balise ne sont pas publiés lorsque le formulaire de schéma de métadonnées est publié sur Brand Portal. Correctif pour CQ-4256218
* Lorsqu’un dossier de troisième niveau est publié d’AEM vers Brand Portal, sans publier les dossiers parents, le nom du dossier change. Correctif pour CQ-4255423
* Le prédicat du navigateur de chemins d’accès est publié d’AEM Assets vers Brand Portal comme prévu. Cependant, le chemin publié sur BP reste /content/dam, qui doit être mis à jour. Correctif pour CQ-4256240

**DAM - Creative Cloud**

* L’icône &quot;Rechercher des ressources d’Adobe&quot; est absente de la navigation principale AEM. Correctif pour CQ-4254343

**DAM - Client DM**

* Après l’ingestion de vidéos dans un dossier associé au profil de traitement vidéo AVS, la fenêtre du navigateur s’actualise encore et encore. Correctif pour CQ-4253563
* La publication YouTube échoue lors de l’utilisation d’une balise ad hoc contenant des caractères en majuscules. Correctif pour CQ-4252477
* Lorsqu’une annotation est créée dans une ressource telle que PDF, l’interface utilisateur lance une boucle d’actualisation de page infinie. NPR-27052 : correctif pour CQ-4255396

**Gestion des actifs numériques - Services DM**

* Dynamic Media n’utilise pas le proxy configuré pour certains types de ressources. NPR-10727; Correctif pour CQ-4244871

**Plate-forme**

* Problèmes de performances avec org.apache.sling.i18n. NPR-26812 : correctif pour SLING-7543
* Impossible d’afficher les propriétés du noeud lorsque le fichier XML d’entrée est formaté et déployé. NPR-26198 : correctif pour CQ-4250448
* IndexOutOfBoundsException dans ResourceProviderTracker. NPR-26968 : correctif pour GRANITE-23310
* La console JMX accumule de nombreuses sessions d’administration et une nouvelle session est ouverte toutes les 5 minutes. NPR-26958 : correctif pour CQ-4251090
* Après la mise à niveau de la version 6.2 vers la version 6.4, le fichier journal affiche la trace de la pile pour le résolveur de ressources non fermé com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck. NPR-26176 : correctif pour Granite-21734
* Lorsqu’un agent de vidage Dispatcher prêt à l’emploi est configuré pour mettre à jour les alias, l’opération échoue avec un StackOverflowError. NPR-26373 : correctif pour CQ-4242928
* La réplication utilise le jeton OAuth expiré jusqu’à ce qu’il échoue. NPR-25894
* Page restreinte (page Groupe d’utilisateurs fermé) avec sling : L’alias ne redirige pas l’utilisateur vers la page de connexion. NPR-25715 : Correctif pour Granite=22263
* Lors de la publication de balises, aucune activité ne s’affiche dans l’interface utilisateur. Correctif pour CQ-4255961
* Impossible de modifier les balises dans l’IU classique. Correctif pour CQ-4258697
* Mise à jour de org.apache.felix.http.bridge vers la version 4.0.4. NPR-27038 : Rétroportage pour Granite - 23334
* Les journaux d’activité du gestionnaire de packages doivent être extraits dans un fichier journal distinct. NPR-27323 : correctif pour Granite-14866
* Le programme de validation de package ne signale pas de superpositions dans CFP. NPR-27119 : correctif pour GRANITE-22825

**Projets**

* L’API ACP gère mal la pagination avec uniquement les enfants de sous-répertoire. NPR-27617 : correctif pour CQ-4258639

**OAK**

* Impossible de se connecter au référentiel après l’installation d’AEM Service Pack 2 6.4. NPR-27171 : correctif pour Granite-23317

**Réplication**

* Le journal d’audit reste ouvert avec de principales sessions qui continuent à augmenter constamment avec ~750 chaque jour. NPR-27062 : correctif pour CQ-4241350

**Communautés**

* Les publications et les réponses du forum sont ajoutées au haut de la deuxième page et, une fois actualisées, la publication se déplace à l’emplacement correct en haut de la première page. NPR-27342 : correctif pour CQ-4247338
* Les liens vers toutes les ressources déplacent le chemin d’accès au contexte (/aempublish) après le défilement. NPR-26982 : correctif pour CQ-4254345
* Les groupes ajoutés ne sont pas visibles dans la liste déroulante Chefs de communauté, Modérateurs de communauté et Membre privilégié lors de la modification d’un site publié. NPR-27190 : correctif pour CQ-4258574
* Seuls 10 groupes sont répertoriés dans la page des ressources d’activation, même si la pagination est activée pour la liste des groupes. NPR-26934 : correctif pour CQ-4252985
* L’option permettant d’activer/désactiver la recherche pour le composant Publication planifiée dans le journal est fournie dans ConfigMgr et la tâche SearchScheduledPosts est optimisée. NPR-26923 : correctif pour CQ-4250463
* La recherche par mots-clés dans l’adresse ne fonctionne pas dans la page du composant Calendrier lorsque AEM communauté est définie pour fonctionner avec DSRP. NPR-26737 : correctif pour CQ-4258493
* Mise en oeuvre d’un lien direct vers le commentaire au lieu de la publication principale dans les détails d’un commentaire, pour l’interface utilisateur de modération et les ressources d’activation. NPR-26704 : correctif pour CQ-4251381
* Le contenu modéré par le biais d’une sélection multiple sur la console de modération n’apparaît pas dans le flux d’activités. NPR-26695 : correctif pour CQ-4253244
* La recherche avec le prénom et le nom dans le champ À de la messagerie des communautés ne renvoie pas le résultat attendu. NPR-26385 : correctif pour CQ-4248673
* Erreur observée lors du chargement d’une pièce jointe autre qu’une image (par exemple .pdf) dans le forum. NPR-27360 : correctif pour CQ-4257753
* L’annulation ou la désactivation d’une publication de forum ne fonctionne pas si l’option Auteur-Publier est définie avec MySQL DSRP. NPR-26125; Correctif pour CQ-4251520
* Les composants de collection (forums, blogs, calendrier, idéation, Q&amp;R) disposent désormais d’une propriété dans la boîte de dialogue du composant pour activer/désactiver le &quot;Bloquer le contenu généré par l’utilisateur en mode d’édition de l’auteur&quot;, afin d’autoriser/refuser le chargement du contenu créé par l’utilisateur en mode d’édition de la gestion de contenu web. NPR-26978 : correctif pour CQ-4248161
* La recherche de balises ne fonctionne pas pour les termes de recherche localisés. NPR-26171 : correctif pour CQ-4249926
* Le bouton Précédent ignore une page dans la recherche de forum. NPR-26950 : correctif pour CQ-4254804
* L’instance AEM s’exécutant sur le port HTTP par défaut (80) ne peut pas atteindre le fichier imsmanifest.xml. NPR-27173 : correctif pour CQ-4252211
* Le fait de ne pas marquer le commentaire comme réponse pour Q&amp;R ne fonctionne pas si AEM Communities est défini avec DSRP. NPR-26247 : correctif pour CQ-4252232
* Impossible d’appeler Adobe Storage : Erreur 414 - URI de GET long observé lorsque les utilisateurs recherchent /content/community-components/en/search.html et sélectionnent le champ de création comme l’un des filtres pour ce terme de recherche. NPR-26643 : correctif pour CQ-4251303
* La valeur de liste déroulante pour DataCenterURL dans la configuration ASRP est changée de Dallas en Virginie (pour VA6). NPR-26936 : correctif pour CQ-4254434
* Les caractères spéciaux dans la recherche de forum renvoient des erreurs ou aucun résultat. NPR-26930 : correctif pour CQ-4247744
* Le nombre affiché pour &quot;Nombre de résultats&quot; dans la recherche de forum utilise un délimiteur incorrect pour les paramètres régionaux anglais et allemand. NPR-27050 : correctif pour CQ-4248939
* Les notifications non lues n’augmentent pas au-delà de 21. NPR-26946, NPR-27480 : correctif pour CQ-4252829, CQ-4256939
* La pagination dans la section des commentaires d’un composant permet aux utilisateurs de faire défiler l’écran pour voir le contenu de la page, en accédant à une page par le biais de la pagination. NPR-27032 : correctif pour CQ-4251228
* Il n’est pas possible de cliquer sur le dossier Site de la communauté sur l’image miniature lors de l’affichage à partir d’Admin Console sur l’instance AEM Author. NPR-26986 : correctif pour CQ-4254036
* L’option &quot;Tout marquer lire&quot; marque uniquement les 10 premières notifications comme lues et d’autres restent non lues jusqu’à l’actualisation de la page. NPR-27037 : correctif pour CQ-4254058
* La pagination n’est pas déclenchée pour Idéation et la liste des sujets (ou réponses) s’allonge, sauf si elle est rechargée. NPR-26193 : correctif pour CQ-4252104
* Les activités d’autres utilisateurs et le contenu créé par l’utilisateur supprimé sont visibles lors de la connexion avec les informations d’identification du modérateur et l’ajout de &quot;#social-activities&quot; ou &quot;#tabs-2&quot; à la fin de l’URL du profil du modérateur. Correctif pour CQ-4251355
* Toutes les balises affectées ne peuvent pas être supprimées d’un article de blog. NPR-26851 : correctif pour CQ-4253359
* Les relations avec le contenu créé par l’utilisateur ne sont pas supprimées lors de la suppression du contenu créé par l’utilisateur. NPR-27630 : correctif pour CQ-4258706
* Le lien pour les réponses ne fonctionne pas lors d’un clic sur la ligne sur les réponses du forum. NPR-27623 : correctif pour CQ-4256138
* La limite des abonnements utilisateur est limitée à 1000. NPR-27614 : correctif pour CQ-4254689
* La modification d’un site et des rôles dans les paramètres de rôle renvoie une exception de pointeur nul. NPR-27377; Correctif pour CQ-4255909

**Traduction**

* L’aperçu de traduction ne fonctionne pas avec l’exemple de contenu we.retail. NPR-26727 : correctif pour CQ-4241179

**IU - Fondation**

* Une exception NullPointerException est renvoyée lorsque vous tentez de télécharger des configurations après la mise à niveau vers AEM 6.4. NPR-27310 : Correctif pour Granite-23573
* Rétroportage proactif pour les correctifs granite.platform.login. NPR-26941
* Rétroportage proactif pour les granite.ui.content correctifs. NPR-26294
* Le composant de champ Nombre ne valide pas les nombres négatifs sur Internet Explorer 11. NPR-26701
* Rétroportage proactif pour les granite.ui.coralui3 correctifs. NPR-26662
* Rétroportage proactif pour les correctifs granite.ui.coralui3-aeon. NPR-26666
* Rétroportage proactif pour les granite.ui.foundation.components correctifs. NPR-27313
* Rétroportage proactif pour les correctifs granite.ui.commons. NPR-26753
* Rétroportages proactifs de l’interface utilisateur de Foundation. NPR-26248

**Intégration**

* Les modifications dans AEM expériences créées via le moteur de ciblage ne sont pas publiées. NPR-24869 : correctif pour CQ-4247832
* Impossible de créer plusieurs activités et expériences si leurs noms contiennent des caractères japonais. NPR-27271 : correctif pour CQ-4256857
* Mettez à jour le point d’entrée de l’API Launch. NPR-26790 : correctif pour CQ-4254380
* (Personalization) BrandsRetriever parcourt l’arbre entier. NPR-27060 : correctif pour CQ-4255790

**WCM - Interface utilisateur d’administration**

* Ajout d’un test HTTP pour la publication/annulation de la publication d’une page avec des références et d’un test d’interface utilisateur pour Live Copy. Correctif pour CQ-4256894

**WCM - Éditeur de page**

* La barre d’outils Modifier est désactivée pour les composants lors de la première modification. Correctif pour CQ-4253270

**Forms**

Les principaux points forts d&#39;AEM Forms 6.4.3.0 sont les suivants :

* Activation de la prise en charge d’un tableau/d’une liste d’objets avec la substitution d’entité dynamique.
* Activation de la conformité FIPS pour le workflow étendu Reader dans Digital Signature, Reader Extensions, CryptoProvider et TrustStore.
* Ajout de la prise en charge de PDF/UA aux formulaires XFA générés à l’aide de Designer ou de Output Service.
* Activation de la prise en charge de la propriété allowedPaths sur les modèles de formulaires adaptatifs.
* Ajout de la prise en charge de JBoss 7.1.4 pour AEM Forms 6.4.

**Package de modules complémentaires Forms**

**Intégration du serveur principal**

* Impossible de renseigner les mappages de modèle de données de formulaire en fonction des entités dynamiques dans la réponse SOAP. NPR-26428 : correctif pour CQ-4250639
* La valeur de _elementNamespace dans les données additionnelles du modèle de données de formulaire, saisie à l’aide de l’interface utilisateur de test, n’est pas correctement reflétée dans la requête SOAP. Correctif pour CQ-4255373
* Une contrainte de propriété nulle est initialisée avec une valeur par défaut et ne peut pas être synchronisée avec FDM. Correctif pour CQ-4253873
* La valeur par défaut de la propriété nullable n’est pas définie sur True pour la source de données OData. Correctif pour CQ-4253870

**Formulaires adaptatifs**

* Impossible de charger les sites et l’éditeur de formulaires. NPR-26977; Correctif pour CQ-4249170
* Problèmes lors de l’ajout d’une pièce jointe à un formulaire adaptatif à l’aide du clavier. NPR-25913 ; Correctif pour CQ-4249456

**Forms - Communication interactive**

* Impossible de déplacer un panneau qui a été ajouté à l’aide de l’option Ajouter un panneau enfant dans l’arborescence de contenu du canal web de la communication interactive et dans les formulaires adaptatifs. Correctif pour CQ-4253915
* Les noms des tables s’affichent à la place du titre de l’association FDM dans la section Sources de données du canal d’impression. Correctif pour CQ-4253669
* La fonction isUseXFABullets() n’est pas désactivée dans la classe PrintChannelRenderOptions et est disponible dans le SDK client. Correctif pour CQ-4246583, CQ-4252700

**Correspondence Management**

* Javadocs pour la version 6.4 ne contient pas com.adobe.dbforms.* package et les classes correspondantes. Correctif pour CQ-4253200
* L’interface utilisateur CCR affiche une valeur de courrier indésirable par défaut pour le champ de date, au cas où aucune entrée du fichier XML de données de test n’est renseignée. Correctif pour CQ-4252041
* Si une lettre contient un module de liste, l’espace entre la puce et le texte est perdu lors de la génération du PDF à partir de la lettre. Correctif pour CQ-4250588

**Gestionnaire de formulaires**

* Activation de la prise en charge de la propriété allowedPaths sur les modèles de formulaires adaptatifs. NPR-26598 : correctif pour CQ-4255892

**Forms - Workflow**

* Si des accolades sont incluses dans le nom de la tâche lors de l’exécution du workflow Forms, une exception s’affiche dans les journaux. Correctif pour CQ-4256626
* Impossible d’ouvrir un modèle de recherche dans l’espace de travail AEM Forms. Correctif pour CQ-4255651

**Mobile Forms**

* La notification de sortie ne s’affiche pas lorsque vous quittez le champ de date dans AEM Forms rendu en HTML dans Internet Explorer ou Chrome. NPR-26483 : correctif pour CQ-4239352
* Les dates contenues dans le XML au début du traitement provoquent une erreur de validation dans les formulaires lorsque l’utilisateur tente de quitter le formulaire. NPR-26787 : correctif pour CQ-4251211

**Programme d’installation de Forms JEE**

**Service PDF Generator**

* Impossible d’afficher les paramètres de reporting et de conformité des normes pour PDF Generator. NPR-26715 : correctif pour CQ-4253384
* Le fichier binaire convertpdf est manquant dans le module complémentaire AIX Forms, ce qui entraîne l’échec lors de l’appel du service PDFA. Correctif pour CQ-4257873
* Le service de capture papier se bloque lors du traitement des fichiers de TIFF. NPR-28079 : correctif pour CQ-4240649

**Services de document**

* Ajoutez la conformité FIPS pour le processus RE dans Digital Signature, Reader Extensions, CryptoProvider et TrustStore. NPR-27495 : correctif pour CQ-4257572
* La conversion échoue lors de l’exécution du service AssemblerService.toPDFA dans une boucle. NPR-26354 : correctif pour CQ-4248656
* Impossible de valider correctement la conformité des PDF en fonction des normes PDF/A-1b. NPR-26286 : correctif pour CQ-4227539
* Problèmes de mémoire insuffisante lors de la mise à niveau d’AEM Forms de 6.1 SP2 CFP5 vers CFP13. NPR-26285 : correctif pour CQ-4244379
* Impossible de valider correctement la conformité des PDF en fonction des normes du PDF/A. NPR-26272 : correctif pour CQ-4248823

**Forms - Foundation JEE**

* Ajout de la prise en charge de JBoss 7.1.4 pour AEM Forms 6.4. NPR-27331 ; Correctif pour CQ-4255601

**Feature Packs inclus**

* Activation de la prise en charge d’un tableau/d’une liste d’objets avec la substitution d’entité dynamique. NPR-26590 : correctif pour CQ-4254655

**Lots OSGI et packages de contenu inclus**

Liste des lots OSGi inclus dans AEM 6.4.3.0

[Obtenir le fichier](assets/6.4.3.0_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.3.0

[Obtenir le fichier](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0 est une mise à jour importante qui comporte des améliorations et correctifs pour les performances, la stabilité, la sécurité et les bogues signalés par les clients depuis la mise à disposition d’AEM 6.4 dans **Avril 2018.**
Il est également cumulatif, ce qui signifie que la version 6.4.2.0 inclut tous les Service Packs AEM version 6.4 avant sa publication.

Voici quelques-uns des points forts d’AEM 6.4.2.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.7.
* Ajout de la prise en charge des fonctionnalités de la spécification HTL 1.4 du langage de modèle de HTML
* Ajout de la prise en charge de MongoDB Enterprise 3.6.
* L’éditeur de page Sites prend en charge la modification et la composition dans le contexte avec des composants côté client créés dans React ou dans Angular, en association avec <a href="../sites-developing/spa-walkthrough.md">AEM SDK JS de l’éditeur SPA</a>.
* Améliorations des fragments de contenu : ajout de la fonctionnalité d’annotation dans les champs de texte et de comparaison côte à côte des versions.
* Ajout [intégration avec Adobe Stock](/help/assets/aem-assets-adobe-stock.md) afin que les utilisateurs puissent rechercher, prévisualiser, enregistrer et acquérir sous licence des ressources Adobe Stock directement à partir de l’interface utilisateur d’AEM. Pour plus d’informations, voir [Utilisation de ressources Adobe Stock avec AEM Assets](https://docs.adobe.com/content/help/fr/experience-manager-learn/assets/creative-workflows/adobe-stock.html).
* Ressources ajoute la prise en charge des schémas conditionnels dynamiques et la possibilité de définir un schéma de métadonnées pour les dossiers de ressources.
* Ajout d’une configuration dans chaque composant pour activer/désactiver la fonctionnalité de création/mise à jour de miniatures de dossiers.
* Améliorations de l’éditeur d’image lors de la création de pages.
* Correctif de régression dans les communautés pour que l’événement de notation ne soit pas correctement géré en cas de suppression de la réponse sélectionnée.
* Révision de la limite maximale des résultats de recherche pour solr vers MAX_INT-10000.
* La tâche de purge des transactions n’est lancée que lors du premier appel à storeTransaction.
* Le bouton &quot;Tout sélectionner&quot; est désormais disponible en mode Carte et en mode Colonnes.
* Améliorations de l’accessibilité dans CoralUI.
* Amélioration de la gestion de Coral.Keys.
* Mise à jour du fichier Moment.js vers la version 2.22.2
* Mise à jour de jquery vers la version 1.12.1
* Introduction du composant foundation-workflowstatus .
* Mise à jour de GCC vers la dernière version.
* Déplacez SAML vers une nouvelle synchronisation IDP externe.

**Ressources**

* La génération de sous-ressources pour le fichier pptx ne contient aucune image ni miniature. NPR-24286 : correctif pour CQ-4217986
* migrateAllAssets - Ajoutez la prise en charge du traitement par lots et améliorez la méthode d’AEM qui ajoute l’UUID aux anciennes ressources. NPR-24861 : correctif pour CQ-4242863 et CQ-4247874
* Problème de performance avec la génération de miniatures. NPR-24693 : correctif pour CQ-4246960
* (IU tactile) Le composant &quot;prédicat Options&quot; reste vide lorsqu’il est ajouté à la page Éditeur du partage de ressources. NPR-24643 : correctif pour CQ-4245295
* (Workflow) Le balisage intelligent des ressources ne passe pas par la configuration du proxy. NPR-25840 : correctif pour CQ-4248202
* (Omnisearch) la suppression de filetype:image des critères de recherche ne supprime pas le type d’image. NPR-25232 : correctif pour CQ-4248280
* Lors de la tentative de déplacement d’un fichier vers un autre dossier, les dossiers dont le nom contient une apostrophe ne s’affichent pas. NPR-25125 : correctif pour CQ-4248660
* Le curseur dans la page Sous-ressource ne fonctionne pas correctement lorsque les préférences linguistiques sont définies sur une autre langue que l’anglais. NPR-25274 : correctif pour CQ-4248489
* Problème avec le fichier csv d’exportation de métadonnées lorsqu’il est ouvert sur des machines au format numéro européen. NPR-26009 : correctif pour CQ-4250677
* Le bouton Créer n’est pas disponible lors de la sélection du dossier de ressources sans autorisation de suppression. NPR-25788 : correctif pour CQ-4250140
* (Rétroportage) Améliorations de l’accessibilité : Duplicate-id: La valeur de l’attribut id doit être unique, Libellé : Les éléments de formulaire doivent comporter des libellés et un nom de lien : Les liens doivent comporter du texte perceptible. NPR-24252 : correctif pour CQ-4250905, CQ-4250906, CQ-4250907
* Le téléchargement d’un fichier csv avec des champs séparés par &quot;,&quot; échoue pour les pays européens. NPR-25549 : correctif pour CQ-4249931
* (Brand Portal) Les sous-ensembles d’un fichier pdf multipage ne sont pas publiés lorsqu’une ressource est publiée. NPR-25991 : correctif pour CQ-4245162
* Publiez la fonctionnalité ultérieure pour AEM à la réplication Brand Portal. NPR-25911 : correctif pour CQ-109139
* La publication et l’annulation de la publication de la collection privée par des utilisateurs non-administrateurs génère un NPE. NPR-25906 : correctif pour CQ-4250594
* Désactivez la publication de fragments de contenu et de schémas de formulaires sur Brand Portal. NPR-24176, NPR-26004 : correctif pour CQ-4251592, CQ-4252026
* (Dynamic Media) Mise à jour des visionneuses DM vers la version 5.10.1, qui permet de rechercher des noms en double sur la page Paramètre d’image prédéfini. Voir Mise à jour des visionneuses Dynamic Media (5.10.1). NPR-24403 : correctif pour CQ-4247554
* Erreur JavaScript dans la console du navigateur en mode Colonnes lors de la sélection d’une ressource ou d’un dossier. NPR-25939 : correctif pour CQ-4250228
* (Mode Colonne) Impossible d’identifier les tâches lorsque le fichier clé apparaît comme entrée blanche vide. NPR-25903 : correctif pour CQ-4246307

**Sites**

* La requête du fichier datasource.jsp sur AEM 6.2 diffère d’AEM 6.4. NPR-24968 : Correctif pour CQ-4244235
* (IU classique) Impossible d’ajouter des balises aux pages. NPR-25255, NPR-25612 : correctif pour CQ-4249615
* Spécifications du langage de modèle de HTML 1.4 - Fonctionnalités rétroportées à AEM 6.4.2.0 NPR-24585
* Héritage incorrect sur le composant local après la copie d’une page Live Copy. NPR-25920 : correctif pour CQ-4236737, CQ-4248957
* L’heure d’activation/de désactivation est stockée dans crx/de, mais ne récupère pas la même chose dans la console de l’interface utilisateur des propriétés de page. NPR-25154 : correctif pour CQ-4243431
* Styles Le système rompt les valeurs de propriétés initiales de la boîte de dialogue. NPR-25648 : correctif pour CQ-4250073
* Lors de la définition d’une propriété cq:tagName dans un noeud cq:htmlTag , le nom de la balise n’est pas pris en compte si le composant est inclus via JSP. NPR-24154 : correctif pour CQ-4244120
* Pour les composants parsys imbriqués, la première conception satisfaisante (avec le chemin le moins imbriqué) est toujours appliquée à partir de plusieurs composants disponibles. Pour plus d’informations, voir [Résolution du chemin de conception](https://docs.adobe.com/content/help/fr-FR/experience-manager-64/developing/platform/templates/page-templates-static.html). NPR-24973 : correctif pour CQ-4246276
* Lorsque vous collez du texte dans un composant d’éditeur de texte enrichi, une boîte de dialogue contextuelle s’affiche, mais son rendu n’est pas correct. NPR-24895 : correctif pour CQ-4245901
* (RTE) Problèmes de performances avec indicateur de champ obligatoire. NPR-24894 : correctif pour CQ-4241895
* (Composant Page) L’ajout d’un composant à Parsys est rogné de la droite et la largeur de l’image de l’appareil s’affiche. NPR-25536 : correctif pour CQ-4238224
* L’éditeur de texte enrichi envoie des données non rognées et ajoute des espaces supplémentaires. NPR-25312 : correctif pour CQ-4249006
* Lors de l’ouverture du composant en mode intégré, les modules externes chargés précédemment ne sont pas visibles la seconde fois. NPR-24610 : correctif pour CQ-4236850
* Le chargement d’un fichier XF dans la vue de l’éditeur par copier/coller ne charge pas automatiquement la variation principale. NPR-24841 : correctif pour CQ-4248037
* Une structure de HTML incorrecte dans siteadmin / damadmin rompt IE11. NPR-24686 : correctif pour CQ-4246363, CQ-4248402
* (Assistant Gestion de publication) Le calendrier de la date d’activation à l’étape Options ne s’ouvre pas après certaines actions à l’étape Portée . NPR-25681 : correctif pour CQ-4250205
* L’UI classique ne permet pas de modifier le CUG pour des raisons d’obsolescence. NPR-25075 : correctif pour 4241823
* Option de création non disponible pour créer des fragments d’expérience. NPR-26053 : correctif pour CQ-4249923
* La variation XF est activée deux fois par conséquent, générant des identifiants en double pour le même élément. NPR-24179 : correctif pour CQ-4245093
* Le tableau Foundation est vulnérable au cross-site scripting par stockage. NPR-25185 : correctif pour CQ-4240760
* Erreur &quot;Valeur de sélecteur de récursivité non valide&quot; lors de la migration d’un composant d’AEM 6.2.1.13 vers AEM 6.4. NPR-24146

**WCM - Éditeur de page**

* L’empilement de plusieurs parsys en raison de requêtes longues (plus de 6) provoque un ralentissement d’AEM. Correctif pour CQ-4240247
* Erreur JS lors de l’ajout de cq:tagName vide dans le noeud cq:htmlTag . Correctif pour CQ-4251852
* Mettez à jour EditableActions en fonction de la relocalisation columnClassNames . Correctif pour CQ-4250781
* Exposez les chemins des ressources et des modèles à l’aide d’une seule propriété et d’un seul attribut. Correctif pour CQ-4251255
* Rétablir les modifications de l’API export.json qui interrompent les modifications. Correctif pour CQ-4251854
* (SPA modifiable) Candidat de version 1.0.0. Correctif pour CQ-4251991
* La barre d’outils Modifier est désactivée pour les autres composants lors de la modification d’un composant. Correctif pour CQ-4253270

**Intégration**

* Les champs Bibliothèque et URL de téléchargement doivent être modifiables. NPR-24804 : correctif pour CQ-4246864
* Problème avec plusieurs configurations de DTM. NPR-24685 : correctif pour CQ-4247293
* Ajout de la prise en charge du déploiement asynchrone pour les bibliothèques clientes hébergées. NPR-25716 : correctif pour CQ-4245745
* Le composant ciblé dont l’offre correspondante est manquante effectue le rendu de la page entière et, au lieu d’un composant ciblé vide, un autre rendu complet de la page est ajouté. NPR-25273 : correctif pour CQ-4248003
* Le moteur Target (mbox.js, at.js) n’utilise pas d’URL mal formées et utilise des URL contenant deux-points qui peuvent rencontrer des problèmes avec certains déploiements. NPR-25339 : correctif pour CQ-4237854
* (Launch) LibraryDownloadProcess stocke une valeur libraryUri incorrecte. NPR-25330 : correctif pour CQ-4250006

**Plate-forme**

* Boucle de réindexation | NPE lors de l’exécution de BinaryTextExtraction lors de la mise à niveau statique de 6.3 à 6.4. Correctif pour Granite - 21677
* Remplacement transfrontalier du chemin marqué interne /libs/cq/cloudserviceconfigs/templates/configpage/jcr:content - Problème lors de l’exécution du détecteur de motifs. NPR-25036 : correctif pour CQ-4248597
* Les entrées de journal ne sont pas écrites en raison de NPE dans LogEntryImpl. NPR-25627 : correctif pour Granite-22383
* La réplication de l’événement de suppression ne vérifie pas les droits. NPR-25679 : correctif pour CQ-4241234
* Ajout de la prise en charge de STARTTLS dans &quot;Service de messagerie Day CQ&quot;. NPR-25611 : correctif pour CQ-4249924
* Rétroportage proactif pour les correctifs granite.platform.login afin d’améliorer l’accessibilité. NPR-25176 : Correctif pour Granite 21746 et Granite-21309
* (AEM 6.4) Erreur lors de la recréation du package et de sa réinstallation. NPR-25173 : correctif pour CQ-4247939
* Suppression de la valeur par défaut MERGE_PRESERVE aclHandling. NPR-24593 : correctif pour Granite-21889
* Le type de contenu n’est pas proposé et est absent de la réponse après l’application de deux fois de ContentDispositionFilter. NPR-24175 : correctif pour Sling-7525
* État du gestionnaire de modules incorrect après la mise à niveau vers AEM branche 6.4. NPR-24551 : correctif pour Granite-21750
* Instance AMS - Analyse des logs d’erreur. Correctif pour CQ-4249567

**Sécurité**

* La reconnexion SAML redirige vers la page de déconnexion à l’aide de Okta IDP. NPR-25523 : correctif pour GRANITE-22364
* L’authentification IMS via les configurations OAuth du fournisseur IDP externe OAK désactive l’utilisateur créé dans AEM. NPR-25301 : correctif pour Granite-22363

**MAC - Intégration de Test&amp;Target**

* (Ciblage) Erreur du composant Texte lors du ciblage. Correctif pour CQ-4233343

**Communautés**

* (Bibliothèque de fichiers) Le téléchargement de ressources avec des espaces vides entraîne des problèmes de format. NPR-24260 : correctif pour CQ-4245159
* Correctifs de plusieurs problèmes affectant Adobe Social. NPR-24247 : correctif pour CQ-4245054, CQ-4245120, CQ-4245296
* Le défilement infini pour la console des membres et des groupes échoue au cas où la publication de l’auteur s’exécute sur différents chemins de contexte. NPR-24437 : correctif pour CQ-4246013
* La publication ne retourne pas à l’état sans réponse même en supprimant de l’état répondu et le score ne diminue pas. NPR-24419 : correctif pour CQ-4245797, CQ-4245932
* Les événements ajoutés à l’aide de la fonctionnalité Calendrier dans les communautés génèrent des valeurs incorrectes. NPR-24883 : correctif pour CQ-4244056
* (Forum des communautés) Problèmes liés au comportement de clic de pagination et de chargement de page. NPR-24880 : correctif pour CQ-4246109
* (Chrome) Les conversions du fuseau horaire échouent sur les événements de communauté. NPR-24881 : correctif pour CQ-4247115
* Impossible d’effectuer le rendu de l’objet incorporé dans le courrier électronique. NPR-24999 : correctif pour CQ-4248022
* La séquence d’automatisation doit être exécutée lors de la mise à jour du contenu créé par l’utilisateur en plus de la création du contenu créé par l’utilisateur. NPR-25892 : correctif pour CQ-4251399
* Réactivité de la boîte de dialogue modale sur les groupes. NPR-25623 : correctif pour CQ-4248805
* Une exception Solr est générée lors de la suppression de contenu. NPR-25869 : correctif pour CQ-4248908
* Les liens paginés vers des threads contenant de nombreuses publications ne fonctionnent pas sur les notifications. NPR-25678 : correctif pour CQ-4243038
* Les valeurs d’heure dans les résultats de recherche affichent l’heure du serveur au lieu du fuseau horaire du client. NPR-25594 : correctif pour CQ-4248986
* (Commentaires sur le forum) Le bouton Précédent du navigateur ne fonctionne pas comme prévu. NPR-25205 : correctif pour CQ-4248573
* (Résultats de la recherche) Le bouton Précédent du navigateur ne fonctionne pas comme prévu. NPR-25214 : correctif pour CQ-4248574
* La valeur null est renvoyée lors de la superposition du composant community groupmemberlist . NPR-25228 : correctif pour CQ-4248523
* (Calendrier des communautés) ClassCastException est généré lors de l’enregistrement de l’événement avec la nouvelle image de couverture. NPR-25167 : correctif pour CQ-4248662
* (Communautés) Les messages sont tronqués. NPR-25326
* (Publication AEM) La ressource de notation échoue avec le chemin d’accès au contexte et affiche un écran vide. NPR-26155 : correctif pour CQ-4251942
* (MSRP) Le nouveau calendrier est enregistré et renvoie partiellement NPE dans le journal des erreurs. NPR-26071 : correctif pour CQ-4250531
* La pagination du forum/de la rubrique n’est mise à jour que lorsque la page est actualisée. NPR-26070, NPR-25965 : correctif pour CQ-4249509
* (Forum Q&amp;R) Impossible d’accéder à la page précédente lors de l’ouverture d’un lien direct vers un commentaire. NPR-26069 : correctif pour CQ-4251699
* Le chargement d’une image dans Créer un groupe ne fonctionne pas sur mobile. NPR-26172 : correctif pour CQ-4251703
* (Messagerie) Lors de l’utilisation de DSRP, le nom du destinataire du message est toujours affiché comme &quot;Inconnu&quot;. NPR-26056 : correctif pour CQ-4251397
* Le libellé de statut d’achèvement de la ressource Scorm d’activation apparaît vide dans l’interface utilisateur. NPR-26034 : correctif pour CQ-4249994
* Lors de la création d’un groupe de communautés, un groupe de communautés en double est créé sur un cluster mongoMK principal/principal. NPR-26032 : correctif pour CQ-4245884
* (Auteur) L’assistant de création de groupe prend trop de temps pour charger/créer un groupe dans l’assistant. NPR-26031 : correctif pour CQ-4244966
* Le parsys disparaît lors de l’ajout d’une instruction d’inclusion dans le script hbs. NPR-25908 : correctif pour CQ-4250489
* Si l’option « Autoriser les privilégiés » est arrivée, les membres privilégiés ne devraient pouvoir composer que pour les utilisateurs qui sont membres de la communauté. NPR-25877 : correctif pour CQ-4248450
* Liens profonds bloqués pour activation. NPR-25966 : correctif pour CQ-4251478
* La pagination du forum n’est pas mise à jour dynamiquement lors de la suppression des réponses. NPR-25970 : correctif pour CQ-4248975, CQ-4252843
* Le défilement et la mise en surbrillance automatiques ne fonctionnent pas sur les événements de calendrier et de fichier en cas de commentaires imbriqués. NPR-25958 : correctif pour CQ-4251471
* (DSRP) Les performances des liens directs/profonds se dégradent avec une grande quantité de contenu généré par l’utilisateur. NPR-25957 : correctif pour CQ-4251470
* Impossible de modifier les propriétés des membres autorisés et des membres privilégiés. NPR-26014 : correctif pour CQ-4244592
* Tout marquer comme lu réinitialise les compteurs de notification pour toutes les pages de la communauté. NPR-25931 : correctif pour CQ-4248612
* Échec de la modification des services informatiques pour DSRP. NPR-25929 : correctif pour CQ-4251382
* Échec des e-mails en raison de NPE lors de la création de modèles d’email. NPR-26039 : correctif pour CQ-4250962
* Problèmes de thread du forum lors de l’incorporation d’images avec une résolution très élevée. NPR-26037 : correctif pour CQ-4244453, CQ-4253099
* L’heure affiche les commutateurs lorsque le fuseau horaire du serveur diffère du fuseau horaire de l’utilisateur. NPR-26036 : correctif pour CQ-4248751
* Le fait de joindre deux fois un fichier portant le même nom à une publication de forum entraîne une erreur du serveur. NPR-24172 : correctif pour CQ-4244367
* Correctifs de performances de backport : pagination de groupe sur l’auteur et la publication, recherche de groupe sur l’auteur, Eviter la sérialisation des réponses pour le journal, le calendrier et l’idéation et chargement différé pour obtenir le bouton d’adhésion à un groupe (inviter/annuler l’invitation) pour chaque groupe lors de l’affichage de la page de liste de groupes. NPR-24538 : correctif pour CQ-4246515
* Les ressources d’activation ne sont pas visibles sur l’auteur. Correctif pour CQ-4252618
* Les notifications ne sont pas générées pour le thread par un utilisateur inconnu. Correctif pour CQ-4245132
* La recherche de groupe n’apparaît pas sur le rail de gauche. Correctif pour CQ-4252621
* (Auteur) La pagination ne fonctionne pas pour la console Groupes. Correctif pour CQ-4242786
* Mise à niveau de l’interface utilisateur jQuery. Correctif pour CQ-4248894
* Effectuez la mise à niveau vers la dernière version de SCORM 2017.1. NPR-25675 : correctif pour CQ-4240671
* Les champs &quot;Composer au nom&quot; sont visibles par les utilisateurs non membres de la communauté. NPR-25331 : correctif pour CQ-4247858
* La publication est toujours visible sur l’interface utilisateur, même après suppression, et affiche une erreur sur la console. NPR-26290 : correctif pour CQ-4252803
* (Paramètres du site) Cette option peut être utilisée pour enregistrer les modifications apportées aux rôles. NPR-26274 : correctif pour CQ-4252187
* (Vulnérabilité de sécurité) Prise en charge du compte en raison d’une mauvaise configuration du jeton web JSON. NPR-26458 : correctif pour CQ-4253314
* La pagination n’est pas réinitialisée lors de la suppression des réponses. NPR-26326 : correctif pour CQ-4252997
* L’image de pièce jointe n’est pas affichée dans les versions préliminaires lors de la modification. Correctif pour CQ-4253360
* La page n’est pas actualisée lors de l’ajout de pièces jointes à la base de données relationnelle (DSRP). Correctif pour CQ-4253084
* Les groupes ne fonctionnent pas dans la ressource de site d’activation. Correctif pour CQ-4252975
* Les chemins d’apprentissage prérequis ne sont pas conservés dans l’activation. Correctif pour CQ-4252948

**Processus**

* L’interface utilisateur du lanceur de workflow n’affiche pas les configurations de lanceur 41 plus anciennes et déclenche une erreur JavaScript dans la console. NPR-25028 : correctif pour CQ-4247604
* La modification d’un workflow hérité sans modifier son lanceur entraîne la création de plusieurs workflows sur n’importe quel workflow contenant une étape Activer la page/ressource . NPR-25870 : correctif pour CQ-4250896
* Lien incorrect dans la charge utile de workflow si la page comporte un noeud de métadonnées. NPR-25916 : correctif pour CQ-4250733

**Traduction**

* Correction du fait que l’importation d’un projet traduit faisait deux demandes de POST simultanées, ce qui provoquait une erreur. NPR-24889 : correctif pour CQ-4247638
* Correction du fait que lors de la création d’un projet de traduction pour plusieurs langues, toutes les pages pour la même langue sont ajoutées à la même tâche. NPR-25091 : correctif pour CQ-4246112
* Correction du fait que dans certains cas, la tâche de traduction répertoriait uniquement les 40 premières pages. NPR-25974 : correctif pour CQ-4248661
* Composant DataPicker (Coral2) ne modifiant pas l’année. NPR-24466 : correctif pour Granite-21893

**IU - Fondation**

* Rétroportages proactifs de l’interface utilisateur de Foundation. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-25599 35, NPR-25976
* (Importateur de conception) L’importation d’une page n’importe pas le js, css. NPR-25203 : correctif pour Granite-22236
* Rétroportage proactif de l’interface utilisateur de Foundation pour améliorer la stabilité du produit. NPR-24334

**MAC - Intégration de Test&amp;Target**

* La deuxième page de l’ assistant de personnalisation ( lancée par &quot;Commencer le ciblage&quot; ) est vide et renvoie des erreurs de console. Correctif pour CQ-4253277

**Fragments d’expérience**

* Intégration des fragments d’expérience/de Target fusionnés à AEM 6.4.2.0. Correctif pour CQ-4248653

**Gestion des fragments de contenu**

* Annotations de fragments de contenu et comparaison côte à côte des versions de fragments de contenu. Correctif pour CQ-4247148

**DAM - Général**

* Le filtre &quot;Extraits par&quot; ne fonctionne pas correctement dans la recherche. Correctif pour CQ-4247070
* Lors de l’exécution du processus de mise à jour des ressources, la copie de langue de la ressource et sa miniature deviennent vides. Correctif pour CQ-4250641
* Duplicate-id: La valeur de l’attribut id doit être unique. Correctif pour CQ-4250905
* Libellé : Les éléments de formulaire doivent comporter des libellés. Correctif pour CQ-4250906
* Link-name : Les liens doivent comporter du texte perceptible. Correctif pour CQ-4250907
* Migration des modèles de métadonnées de dossier de port JMX et ServiceUserMapping. Correctif pour CQ-4252947
* WebdriverIO Tests qui ne s’exécutent pas dans la branche release/640 de CQ/dam. Correctif pour CQ-4252749
* Les liens vers les ressources déplacées ne sont pas restructurés si le lien est publié. Correctif pour CQ-4245756

**DAM - Visionneuses**

* Erreur intermittente lors du chargement de la vidéo avec de nouvelles visionneuses 5.10.1. Correctif pour CQ-4250562

**DAM-Brand Portal**

* L’annulation de la publication d’une collection à partir de Brand Portal échoue avec une erreur. Correctif pour CQ-4245990
* Impossible d’annuler la publication des paramètres d’image prédéfinis dans Brand Portal. Correctif pour CQ-4246140
* Les sous-ensembles d’un fichier pdf de plusieurs pages ne sont pas publiés lorsqu’une ressource est publiée. Correctif pour CQ-4245162

**DAM - DMClient**

* Lors de la publication d’une ressource vidéo dans YouTube, les balises qui génèrent YouTube incluent le chemin d’accès complet de la balise. Correctif pour CQ-4245549
* (Mises à niveau Opt-out et Opt-in) Problème avec la redirection CSS de la visionneuse. Correctif pour CQ-4247854
* Impossible de créer/modifier le paramètre prédéfini de la visionneuse en tant que non-membre du groupe &quot;administrateurs&quot;. Correctif pour CQ-4247618
* (6.4.1.0) L’ajout de plusieurs vidéos dans plusieurs parsys interrompt le lecteur vidéo. Correctif pour CQ-4248517
* Il est impossible de renommer et de déplacer une ressource dans une visionneuse d’images. Correctif pour CQ-4248434
* La publication de vidéos volumineuses sur YouTube génère des messages d’expiration. Correctif pour CQ-4237831
* (Mode Liste) L’interface utilisateur du sélecteur/sélecteur de ressources devient entièrement grise et est désactivée pour l’utilisateur. Correctif pour CQ-4237817
* (Zoom vertical) Échec du chargement du CSS avec une erreur 404. Correctif pour CQ-4236508
* Si vous tentez de télécharger une ressource avec le caractère de pourcentage (%) dans le nom de la ressource, une archive est vide. Correctif pour CQ-4250558
* (Mode Carte) Aucun indicateur de traitement ne s’affiche lors de l’utilisation de la fonction Copier et coller sur une ressource vidéo. Correctif pour CQ-4249037
* (Mise à niveau de la version 6.3.2 vers la version 6.4) Les paramètres d’image prédéfinis de mise à niveau s’affichent sous la forme &quot;Non publié&quot; sur la page Rendus, mais ne génèrent pas de bouton URL lorsqu’ils sont sélectionnés. Correctif pour CQ-4240406
* Améliorations techniques de la dette/des ressources mineures. Correctif pour CQ-4240648
* Le sélecteur de ressources (ou sélecteur de ressources) n’affiche pas toutes les ressources des dossiers disponibles. Correctif pour CQ-4218414
* Le paramètre d’image prédéfini sans hauteur affiche les images dont la taille est incorrecte. Correctif pour CQ-4246546
* (Ressources multi-page) L’interface utilisateur se casse lorsque vous cliquez sur les annotations. Correctif pour CQ-4251434
* La mise à niveau de la version 6.3 vers la version 6.4 et les versions ultérieures du paramètre prédéfini Analytics entraîne la création d’une nouvelle suite de rapports et d’un nouveau paramètre prédéfini Analytics, ce qui entraîne la perte des anciennes données de création de rapports de l’utilisateur. Correctif pour CQ-4244529
* (Assistant Gestion de publication) La liste des ressources semble vide lors de la publication ou de l’annulation de la publication. Correctif pour CQ-4251881
* Lors du choix des visionneuses après l’affichage des membres de la visionneuse, la lecture des vidéos AVS échoue. Correctif pour CQ-4205308
* Un nouveau paramètre prédéfini de codage vidéo ne peut pas être ajouté aux paramètres prédéfinis de traitement vidéo de mise à niveau ni modifier le ou les paramètres prédéfinis de codage existants. Correctif pour CQ-4240407
* Les paramètres d’image prédéfinis ne sont pas appliqués aux rendus dynamiques téléchargés. Correctif pour CQ-4249862
* Le bouton Tout sélectionner ne fonctionne pas correctement sur la page de liste des paramètres prédéfinis de la visionneuse. Correctif pour CQ-4252462
* Profils vidéo : Le bouton Tout sélectionner n’est pas fonctionnel. Correctif pour CQ-4253076, CQ-4251447
* Passe de validation SP2 - Passe de fumée. Correctif pour CQ-4251639

**DAM - DMServices**

* La génération des rendus Dynamic Media échouait pour le fichier EPS. Correctif pour CQ-4243688

**Granite**

* Le fait de taper dans le lot SymbolicName entraîne la duplication du lot. Correctif pour Granite-22155
* CUGConfiguration peut ne pas sélectionner CugExclude. Correctif pour Granite-21109
* Le redémarrage d’Adobe Granite Workflow Core exécute à nouveau les étapes du workflow à partir du milieu, ce qui crée des workflows inutiles. NPR-25057 : correctif pour Granite-22218
* JcrResourceBundle ne prend pas correctement en charge plusieurs noms de base. NPR-25245 : correctif pour Granite-22317
* Lors de l’installation des packages de contenu, les listes de contrôle d’accès sont regroupées par entité de sécurité, ce qui entraîne la rupture du modèle d’autorisation. NPR-24583 : correctif pour Granite-21591
* Mettez Jetty à jour vers la version 9.4.11 pour corriger les vulnérabilités. NPR-25030 : correctif pour Granite-22120

**Forms**

Les principaux points forts d&#39;AEM Forms 6.4.2.0 sont les suivants :

* Ajout d’une nouvelle propriété pour que les files d’attente soient mises à jour sans actualiser le navigateur.
* Ajout de la possibilité pour l’utilisateur d’utiliser le même fichier WSDL pour plusieurs services.
* Suppression du modèle d’horodatage non pris en charge dans la liste déroulante du sélecteur de données.
* Ajout de la prise en charge de la sous-couche xfaf et pdf dans OSGI.
* Ajout de la prise en charge de l’utilisation de la variable [fonctionnalité de rapports sur les transactions](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) aux déploiements on-premise.
* Ajout du code pour ne pas afficher la variable enfant dans l’éditeur de règles de condition.

**Package de modules complémentaires Forms**

**Reporting de transaction**

* Mettez à jour la configuration des rapports de transaction avec l’importance de la réplication inverse configurée sur un serveur de publication. NPR-26050 : correctif pour CQ-4246650
* Initialisation différée de la tâche de purge périodique. NPR-25968 : correctif pour CQ-4245024
* L’enregistrement des transactions échoue avec une exception de pointeur de valeur NULL. Correctif pour CQ-4247302

**Forms - Workflow**

* (Workspace HTML) Lorsqu’un utilisateur demande une tâche, le numéro dans la file d’attente est actualisé pour cet utilisateur, mais pas pour les autres utilisateurs, sauf si la page est actualisée. Ce problème a été résolu par une nouvelle propriété. Pour configurer cette nouvelle propriété sur votre instance AEM, consultez ses Paramètres de configuration. NPR-24536 : correctif pour CQ-4233665
* Impossible de charger un formulaire volumineux dans l’application AEM Forms sur la version 6.4. NPR-24463 : Correctif pour CQ-4245091
* Problème dans l’application Mobile Workspace lors de la tentative d’affichage de la tâche partagée. NPR-25177 : correctif pour CQ-4248733
* Comportement de validation incohérent entre le web et le kit de développement d’applications. NPR-25670 : correctif pour CQ-4248178
* Lorsqu’un appel à un service Web est effectué avec un formulaire HTML5 ouvert dans le client, il échoue et un message d’erreur est renvoyé. NPR-26048 : correctif pour CQ-4244716
* Problème lors de l&#39;appel du service dans AEM&#39;application Windows 6.3. NPR-26468 : Correctif pour CQ-4252341

**Mobile Forms**

* (Jeu de formulaires) Problème de validation du champ SSN et Mobile lors de la prévisualisation. NPR-24458 : correctif pour CQ-4244983
* Les données ne s’affichent pas avec le préremplissage des champs multilignes dans l’aperçu de HTML. NPR-24549 : correctif pour CQ-4244212
* Les données sont perdues lorsque le script est évalué sur un champ multiligne. NPR-25333, correctif pour CQ-4249610

**Forms - Communication interactive et Correspondence Management**

* La synchronisation échoue sur IC avec le modèle de base et le modèle d’impression IC de référence. NPR-24912
* (CCR) Les validateurs ne fonctionnent pas pour les champs/variables. Correctif pour CQ-4245047
* L’icône Objet de modèle de données disparaît par intermittence sur la barre d’outils Modifier le texte. Correctif pour CQ-4245122
* Les journaux d’exception s’affichent sur l’IC copié si l’IC d’origine est supprimé. Correctif pour CQ-4249378
* Dans le rendu de lettre, la condition n’est pas évaluée comme vraie même lorsque les données sont correctes. Correctif pour CQ-4245944
* Les composants générés automatiquement ne sont pas mis en surbrillance lors de la sélection dans l’arborescence de contenu. Correctif pour CQ-4246178
* Problèmes lors de l’ouverture de l’éditeur de modèles de canal web. Correctif pour CQ-4248182
* Impossible de modifier l’ordre des ressources ajoutées, car les flèches haut/bas restent désactivées. Correctif pour CQ-4252042
* Impossible de mettre à jour les propriétés du module Condition. Correctif pour CQ-4247909
* L’UX de la boîte de dialogue &quot;Annuler l’héritage&quot; lorsque l’utilisateur réorganise un objet dans le canal web doit être amélioré. Correctif pour CQ-4241076
* Les données de la lettre correspondant aux liaisons définies dans XDP ne sont pas renseignées avec l’URL de lettre directe. Correctif pour CQ-4245833
* (Problème de mise en cache) La synchronisation du canal web ne reflète pas les modifications apportées aux fragments de mise en page et au fragment de texte du canal d’impression. Correctif pour CQ-4251460
* Impossible de mettre à jour le fragment de mise en page et les propriétés du dictionnaire de données. Correctif pour CQ-4247830
* (CCR) Le rechargement du brouillon échoue en raison de l’analyse XML. Correctif pour CQ-4250950
* (Éditeur IC) Le bouton &quot;Modifier le fragment&quot; doit être plus facilement détectable. Correctif pour CQ-4244694
* (XDP) Un écran vide s’affiche lors de l’ajout d’un fragment de mise en page dans le nouveau sous-formulaire créé. Correctif pour CQ-4248810
* Échec du test de DocumentFragment-master-DeployWithServerSideTests. Correctif pour CQ-4245496
* Variable de module de texte Instance dupliquée dans le module Condition. Correctif pour CQ-4252128
* L’URL d’aperçu du PDF n’affiche pas de rapport de transaction lors de la publication. Correctif pour CQ-4246158
* Problèmes liés à la synchronisation IC avec synchronisation du canal d’impression avec le canal web. Correctif pour CQ-4251505
* Nettoyage du code EXM : Supprimez LocalFunctionMapper. Correctif pour CQ-4243265
* Pour corriger le type de ressource de TableHeader du composant de table webChannel d’IC. Correctif pour CQ-4251821
* (Éditeur IC) Problèmes d’utilisation. Correctif pour CQ-4241081
* Le sous-formulaire Canal d’impression n’affiche pas la fonctionnalité d’insertion. Correctif pour CQ-4252994
* Conserver la synchronisation des modifications échoue après la suppression du noeud FDM ou de l’espace réservé variable. Correctif pour CQ-4253178
* (Éditeur de modèles) Le modèle de base affiche les zones de dépôt de l’en-tête/du pied de page supplémentaires et les scintillements d’écran lors de l’ouverture du canal web. Correctif pour CQ-4253323
* Les composants générés automatiquement ne sont pas mis en surbrillance lors de la sélection dans l’arborescence de contenu. Correctif pour CQ-4246178

**Services de document**

* (Form Service) OSGI ne prend pas en charge XFAF. NPR-25181, correctif pour CQ-4251313
* Les caractères dans l’en-tête du fichier de PDF assemblé deviennent brouillés. NPR-25113 : correctif pour CQ-4244682

**Formulaires adaptatifs**

* L’action Envoyer comme envoyer un courrier renvoie une exception avec les champs CC/BC vides. NPR-25019 : correctif pour CQ-4243039
* Impossible d’utiliser le composant Formulaire d’AEM prêt à l’emploi en raison d’une requête inefficace. NPR-25065 : correctif pour CQ-4247256
* Supprimez sling:orderBefore des noeuds de boîte de dialogue de guideImageChoiceComponent. Correctif pour CQ-4245013
* (Sélecteur de date) Modifier le modèle ne prend pas en charge deux types de modèle d’horodatage. Correctif pour CQ-4237982
* Envoyer l’action à l’aide de problèmes de création classique &quot;Forms Workflow&quot;. Correctif pour CQ-4236981
* (Canal web) Le graphique IC doit hériter de la propriété colspan du graphique AF. Correctif pour CQ-4252143

**Intégration du serveur principal**

* (Requêtes SOAP) Les décimales volumineuses (plus de 6 chiffres) sont représentées en notation exponentielle, ce qui entraîne une erreur de validation. NPR-25283 : correctif pour CQ-4248100
* Validation incorrecte des paramètres facultatifs définis dans des types complexes. NPR-25070 : correctif pour CQ-4247107
* Ajout de la possibilité pour l’utilisateur d’utiliser le même fichier WSDL pour plusieurs services. NPR-24604, correctif pour CQ-4247756
* FDM mélange l’ordre des paramètres dans ses appels SOAP. NPR-25069, correctif pour CQ-4247180
* FDM fusionne les entités (dans List/Array) dans la requête SOAP. NPR-25284 : correctif pour CQ-4248375

**Programme d’installation de Forms JEE**

**Service PDFG**

* La fonction de création/modification des paramètres de sécurité ne fonctionne pas. NPR-24769 : correctif pour CQ-4246927
* Optimize PDF en désincorporant sélectivement les polices via un seul appel API. NPR-23287

**Services de document**

* Output Service ne fournit pas les balises correctes pour le Reader d’accessibilité. NPR-24438, NPR-24439, NPR-24440, NPR-24441 : Correctif pour CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Document Security**

* Problème avec la création de stratégies à l’aide de Document Security. NPR-25586, NPR-25547 : correctif pour CQ-4247086

**Forms - Foundation JEE**

* Processus s’exécutant en tant que compte de contexte du système par intermittence. NPR-25289, NPR-25313 : correctif pour CQ-4249331
* AEM Forms JEE affecté par l’alerte de sécurité de liaison de données Apache Struts et Jackson. NPR-25628 : correctif pour CQ-4242891
* Le processus de point de départ Email ne fonctionne pas. NPR-25253 : correctif pour CQ-4248518

**Feature Packs inclus**

**Ressources**

* Ajout [intégration avec Adobe Stock](/help/assets/aem-assets-adobe-stock.md) afin que les utilisateurs puissent rechercher, prévisualiser, enregistrer et acquérir sous licence des ressources Adobe Stock directement à partir de l’interface utilisateur d’AEM. Pour plus d’informations, voir [Utilisation de ressources Adobe Stock avec des ressources AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html). NPR-15779 : correctif pour CQ-30857
* Ajout de la prise en charge des schémas conditionnels dynamiques. Pour plus d’informations, voir [Métadonnées en cascade](/help/assets/cascading-metadata.md). NPR-25189 : correctif pour CQ-4237413
* Activation de l’option &quot;Téléchargement de ressource&quot; sur les fragments de contenu. Pour plus d’informations, voir [Rapports de ressources](/help/assets/asset-reports.md). NPR-25186 : correctif pour CQ-4237410
* Possibilité de définir un schéma de métadonnées pour les dossiers de ressources. Pour plus d’informations, voir [Schéma de métadonnées de dossier](/help/assets/folder-metadata-schema.md) et se référer à ses [Paramètres de configuration](#configuration-settings-required-for-npr) post installation d’AEM 6.4.2.0. NPR-21268 : correctif pour CQ-4221574

**Sites**

* Permet de modifier un fragment de contenu sans autorisation de suppression. Pour plus d’informations, voir [Personnalisation et extension de fragments de contenu](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-delete.html). NPR-25793 : correctif pour CQ-4248750
* Ajout de la fonctionnalité d’annotation des fragments de contenu. Pour plus d’informations, voir [Variations-création de fragments](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment). NPR-25188 : correctif pour CQ-4235336
* Contrôle de version : Comparaison des fragments de contenu côte à côte Pour plus d’informations, voir [Gestion des fragments de contenu](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions). NPR-25187 : correctif pour CQ-4237412
* Améliorations apportées à l’éditeur d’image vers AEM 6.4.2.0. Pour plus d’informations, voir [Éditeur d’image](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24467

**Lots OSGI et packages de contenu inclus**

Liste des lots OSGi inclus dans AEM 6.4.2.0

[Obtenir le fichier](assets/6.4.2.0_bundle-list.txt)

Liste des packages de contenu inclus dans AEM 6.4.2.0

[Obtenir le fichier](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

AEM 6.4.1.0 est une mise à jour importante qui comporte des améliorations et correctifs pour les performances, la stabilité, la sécurité et les bogues signalés par les clients depuis le lancement d’AEM 6.4 en avril 2018.

AEM 6.4.1.0 peut être installé sur AEM 6.4 GA. Voici les principales caractéristiques du Service Pack 1 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.3.
* Ajout de balises intelligentes améliorées.
* Correctifs dans le sélecteur de conception, le sélecteur de balises (remplacez la machine virtuelle source et la machine virtuelle cible par auto.)
* Ajout de la prise en charge de typeHint pour enregistrer des valeurs sous forme de chaîne.
* Ajout de la prise en charge du protocole SMTP vers TLS dans le service de messagerie.
* Correctif de gestion des proxy pour le transfert HTTP dans DMS7.
* Mise à jour vers /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js version 1.3.
* Correctifs dans les packages d’opt-out et d’opt-in DMHybrid.
* Correctifs du recadrage intelligent.
* Valeurs de configuration prêtes à l’emploi migrées vers le nouvel emplacement ( de /etc vers /conf).
* Ajout de profils de couleurs aux paramètres client sur les serveurs de diffusion.
* Migration des paramètres du serveur d’images depuis /etc —&amp;gt; /conf.
* Ajout du fragment de contenu source pour traduction.
* Ajout de la prise en charge d’ARIA à Print et PrintDialog.
* Ajout de la prise en charge ARIA de la validation des emails.
* Rétroportage proactif pour les correctifs de platform.clientlibs.
* Prévention de l’exécution automatique des scripts lorsqu’il n’y a aucune entrée au type de données explicite (résout CVE-2015-9251).

**Ressources**

* La valeur de la liste déroulante en cascade s’affiche vide lors de la réouverture de la page des propriétés de la ressource. NPR-23042 : correctif pour CQ-4238761
* Les liens partagés sur la page mylinkshare et les liens vers la page ne sont pas disponibles pour l’utilisateur non-administrateur NPR-23044 : Correctif pour CQ-4239004
* Pour empêcher une exception de pointeur nul dans le workflow de mise à jour des ressources de gestion des actifs numériques dans la version 6.4.0. NPR-24134 : Correctif pour CQ-4244972
* La page de gestion de contenu web publiée affiche des icônes d’espace réservé pour la zone réactive, des fichiers CSS manquants avec une erreur 403 pour les visionneuses prêtes à l’emploi. NPR-23041 : correctif pour CQ-4233716
* (Affichage des détails) La fonction Navigation suivante/arrière laisse une incrustation DIV dans la zone d’aperçu Rendu dynamique bloquant l’accès à la visionneuse. NPR-23043 : correctif pour CQ-4238499
* La saturation du rendu d’image CMJN est incorrecte. NPR-23048 : correctif pour CQ-4235470
* L’extraction XMP métadonnées par Scene7ListInfoProvider consomme beaucoup de ressources. NPR-23754
* (dam-delivery) Le transfert HTTP ne respecte pas les paramètres du proxy HTTP. NPR-24002 : correctif pour CQ-4244140

**Sites**

* Lorsque nous renommons la page au moment du déplacement, le déplacement de la page est réussi, mais la fonctionnalité de changement de nom ne fonctionne pas. NPR-22923 : correctif pour CQ-4235907
* Erreur lors de la publication d’une page Live Copy qui pointe vers une page d’importateur dans Adobe Campaigns. NPR-23053 : correctif pour CQ-4237164
* Déplacer/Renommer dans l’interface utilisateur classique échoue avec l’erreur &quot;Une erreur s’est produite lors du déplacement de la page&quot; et n’est pas renommée. NPR-23051 : correctif pour CQ-4235907
* Le passage du contenu du mode Colonne au mode Liste génère une page vierge et déclenche une exception de pointeur de valeur NULL pour les pages dont le paramètre OffTime est défini et OnTime est vide. NPR-22968, NPR-23052 : correctif pour CQ-4238940

**Commerce**

* Correction de la casse de test des Hobbes principaux (module CQ/Commerce). Correctif pour CQ-4253494

**Vulnérabilité**

* L’intégration de Salesforce est vulnérable aux attaques SSRF (Server Side Request Forgery). NPR-24289 : correctif pour CQ-4245277
* Server Side Request Forgery (SSRF) et Cross-Site Scripting (XSS) dans ReportingServicesProxyServlet. NPR-24657 : correctif pour CQ-4246880
* Cross-Site Scripting (XSS) : Reflété dans Commerce create ecatalogwizard.html/content. NPR-24642 : correctif pour CQ-4237017
* Cross-site scripting (XSS) dans les liens des Projets de l’IU d’administration. NPR-23272 : correctif pour CQ-4241795

**WCM - Composants Foundation**

* L’ouverture du sélecteur de conception entraîne une exception de pointeur nulle. NPR-23047 : correctif pour CQ-4238736

**Interface utilisateur**

* (Sélecteur de date Coral3) Ajoutez la prise en charge de typeHint pour enregistrer les valeurs sous la forme &quot;String&quot;. NPR-23398 : correctif pour Granite-21194
* La traduction de l’internationalisation ne fonctionne pas au niveau de la langue. NPR-22967, NPR-23046 : Correctif pour Granite-21111
* Rétroportage proactif pour les correctifs granite.ui.commons. NPR-23537
* Rétroportage proactif pour les granite.ui.content correctifs. NPR-23535
* Rétroportage proactif pour les granite.ui.coralui correctifs. NPR-23538
* Impossible de supprimer plusieurs utilisateurs du groupe à la fois. NPR-23846
* (OMEGA) Rapport &quot;Fonctionnalité&quot; en anglais uniquement. NPR-23989 : correctif pour Granite-21231
* (Importateur de conception) L’importation d’une page n’importe pas le js, css. NPR-25203 : correctif pour Granite-22236

**Intégration**

* Résolveur de ressources non fermé dans com.day.cq.analytics.sitecatalyst. NPR-22340 : correctif pour CQ-4236515
* TargetContentImpl ralentit AEM pendant les requêtes longues. NPR-22359 : correctif pour CQ-4236907
* Le moteur Target (mbox.js, at.js) n’utilise pas d’URL mal formées et utilise des URL contenant deux-points qui peuvent rencontrer des problèmes avec certains déploiements. NPR-22434 : correctif pour CQ-4237854
* En mode Target, les auteurs peuvent modifier un composant hérité du plan directeur sans annuler l’héritage. NPR-22865 : correctif pour CQ-4237907
* (Personnalisation) Les icônes sont déformées lors du passage en mode Carte. NPR-23373, NPR-23374 : correctif pour CQ-4240018, CQ-4240019
* (Personalization) Audience Console n’affiche pas les types nt:folder . NPR-23375 : correctif pour CQ-4242293
* Lorsqu’un composant est ciblé sur une instance de publication, le scintillement apparaît pour illustrer l’expérience par défaut avant l’expérience ciblée. NPR-23415 : correctif pour CQ-4242038
* (Console Adobe IMS) La configuration du service OSGi AccessTokenProvider réapparaît après suppression. NPR-23520 : correctif pour CQ-4208250
* La réplication de référence de configuration échoue avec la structure de dossiers intermédiaire. NPR-23485 : correctif pour CQ-4242751
* (Personalization) clientlib bloqué par le servlet proxy. NPR-23521 : correctif pour CQ-4240995
* (Console Adobe IMS) Les solutions cloud enregistrées ne sont pas récupérées dans l’assistant de configuration. NPR-23977 : correctif pour CQ-4244549
* Boucle infinie lors du chargement de contenu ciblé sur des pages sans extension de HTML. NPR-23522 : correctif pour CQ-4223600
* L’activation échoue pour une page avec des références de configuration Dynamic Tag Management héritées. NPR-23485 : correctif pour CQ-4242751

**Plate-forme**

* (IU classique) (IU tactile) Le sélecteur de balises ne s’affiche pas et renvoie une exception lors de la recherche de balises via un prédicat de balises dans le schéma de recherche de ressources. NPR-23049 : correctif pour CQ-4239371
* (IU classique) Les composants utilisant xtype=tags renvoient la valeur null et ne peuvent pas être sélectionnés à partir de la liste de balises eth. NPR-23050 : correctif pour CQ-4239937
* (Marque) La boîte de dialogue Opt-in mentionne Adobe Marketing Cloud au lieu de Adobe Experience Cloud. NPR-23210 : correctif pour CQ-4237799
* L’option de filtre rend AEM lenteur après la mise à niveau de la version 6.3 vers la version 6.4. NPR-23260 : Correctif pour CQ-4239847 (à vérifier)
* Rétroportage proactif pour les correctifs granite.omnisearch.core. NPR-23536
* Rétroportage proactif pour les correctifs de platform.clientlibs. NPR-23569
* L’héritage de la configuration du Cloud Service est rompu lors de la modification d’autres propriétés de page. NPR-23216 : correctif pour CQ-4239782
* Activation de la prise en charge de STARTTLS dans le service de messagerie Day CQ. NPR-23941 : correctif pour CQ-4240397

**Projets**

* (Fragment de contenu) La copie de langue de la ressource incorporée n’est pas créée, tandis que la ressource en anglais est ajoutée à la traduction. Correctif pour CQ-4243477
* La liste déroulante de configuration msft affiche la configuration de /libs(configurations 6.4) au lieu de /etc(configurations 6.3) en mode hérité. Correctif pour CQ-4243475
* Convertir et supprimer automatiquement les lancements de traduction dans les projets de traduction. Correctif pour CQ-4243474
* Le fragment de contenu à l’intérieur des sites n’est pas traduit. Correctif pour CQ-4243482, CQ-4243483, CQ-4245687
* Erreur du serveur lors de l’ouverture du filtre de recherche de tâche de traduction. Correctif pour CQ-4236813
* La liste déroulante de configuration des informations d’identification est vide même si le fichier est présent dans /conf/we-retail. Correctif pour CQ-4236315
* Open Project KPI : dégradation des performances à mesure que d’autres projets sont créés. NPR-23840 : correctif pour CQ-4238392
* Le lanceur de workflow ne peut pas accepter la valeur TypeHint de la chaîne. NPR-23863 : correctif pour CQ-4238356

**Communautés**

* Vulnérabilités de sécurité dans la version 1.0 de Handlebars. NPR-23636 : correctif pour CQ-4243055
* L’autorisation en bloc des messages marqués ne fonctionne pas. NPR-23867 : correctif pour CQ-4243962
* La valeur par défaut ne s’affiche pas sur le bouton de tri dans le composant Forum. NPR-23882 : correctif pour CQ-4243375
* Problèmes liés à la diffusion de messages de sites de la communauté vers des groupes. NPR-23935

**Processus**

* Le service de notification par courrier électronique de workflow Day CQ déclenche un courrier électronique par nœud Mongo pour les notifications WorkflowCompleted et WorkflowAborted. NPR-22515 : correctif pour CQ-4238172
* L’exécution du workflow de ressource de mise à jour de gestion des actifs numériques génère une exception NullPointerException. NPR-23010 : correctif pour Granite-21096
* L’étape Processus de workflow n’affiche pas les scripts de /etc/workflow/scripts. NPR-23263 : correctif pour Granite-20775
* L’étape de participant dynamique de workflow n’affiche pas les scripts de /apps/workflow/scripts. NPR-23464 : correctif pour Granite-21276
* Impossible de modifier un workflow après l&#39;avoir modifié une fois. NPR-23742 : correctif pour CQ-4238526
* (IU classique) Lors de la modification des lanceurs de workflow, les conditions disparaissent, ce qui entraîne le lancement des workflows sans conditions. NPR-23835 : correctif pour CQ-4239153
* Boîte de réception du projet : le passage en mode Calendrier affiche le contenu de la boîte de réception principale. NPR-23947 : correctif pour CQ-4241236
* Vous devez exposer les détails de la payload dans le lot afin que le composant HTL puisse afficher la valeur en mode Liste. NPR-23948 : correctif pour CQ-4240953
* Impossible de stocker les données de boîte de dialogue à l’étape Participant de la boîte de dialogue. NPR-23965 : correctif pour CQ-4234123
* (IU tactile) Lors de l’enregistrement d’un modèle de workflow, le bouton &quot;Synchroniser&quot; passe à &quot;Synchronisé&quot;, ce qui entraîne une faute d’orthographe. Correctif pour CQ-4244843
* Boîte de réception du projet : le passage en mode Calendrier affiche le contenu de la boîte de réception principale. Correctif pour CQ-4244436
* Impossible de sélectionner les boîtes de dialogue à l’étape Participant de la boîte de dialogue. Correctif pour CQ-4244532
* Rétroportage proactif pour les correctifs granite.omnisearch.core. NPR-23536
* Problème dans l’application Mobile Workspace 6.4 avec la tâche partagée. NPR-26383

**WCM - Traduction**

* (Panneau de référence) Les tâches de traduction ne sont pas exécutées lors de la création du projet. Correctif pour CQ-4245327

**WCM - MSM**

* (MSM) Amélioration des performances du déploiement. Correctif pour CQ-4231488
* (MSM) Délai d’attente dans l’écoute des événements entre le traitement réel des événements et la gestion des événements. Correctif pour CQ-4227766

**Screens**

* Échec de la page d’écran avec une erreur en raison de dépendances manquantes pour screens-core-pkg:1.4.42. Correctif pour CQ-4245918

**Projets - Traduction**

* (Fragment de contenu) La copie de langue de la ressource incorporée n’est pas créée, tandis que la ressource en anglais est ajoutée à la traduction. Correctif pour CQ-4243477
* La liste déroulante de configuration msft affiche la configuration de /libs(configurations 6.4) au lieu de /etc(configurations 6.3) en mode hérité. Correctif pour CQ-4243475
* Convertir et supprimer automatiquement les lancements de traduction dans les projets de traduction. Correctif pour CQ-4243474
* Le fragment de contenu à l’intérieur des sites n’est pas traduit. Correctif pour CQ-4243482, CQ-4243483, CQ-4245687
* Erreur du serveur lors de l’ouverture du filtre de recherche de tâche de traduction. Correctif pour CQ-4236813
* La liste déroulante de configuration des informations d’identification est vide même si le fichier est présent dans /conf/we-retail. Correctif pour CQ-4236315

**Gestion des fragments de contenu**

* La suppression du composant remplit les journaux avec des arborescences de pile. Correctif pour CQ-4242315

**DAM - Général**

* La fermeture de la vue détaillée d’une ressource revient à une page de résultats de recherche incorrecte. Correctif pour CQ-4240960
* (Camera Raw) L’option de réglage de l’image est manquante. Correctif pour CQ-4246121
* IndexOutOfBoundsException: Rapport Modification des ressources prêt à l’emploi. Correctif pour CQ-4239744
* Supprimez le score de confiance du rapport csv. Correctif pour CQ-4241491
* Diffusion de l’email de partage de lien interrompue pour l’expéditeur non &quot;admin&quot;. Correctif pour CQ-4240357
* Correction des échecs informatiques. Correctif pour CQ-4249891

**DAM - Brand Portal**

* Les propriétés de la ressource répertorient uniquement 3 propriétés sur le premier onglet ; tous les onglets semblent vides. Correctif pour CQ-4242503
* Les prédicats de type de fichier et de taille de fichier ne sont pas disponibles dans le formulaire de recherche publié. Correctif pour CQ-4242026
* La recherche dans le prédicat de répertoire doit être filtrée ou non dans les filtres de recherche. Correctif pour CQ-4241386
* La recherche par défaut depuis doit exister après l’annulation de la publication. Correctif pour CQ-4241383, CQ-4241113
* Le mouvement Publier sur Brand Portal ne fonctionne pas pour les paramètres d’image prédéfinis. Correctif pour CQ-4241074
* La publication sur Brand Portal ne fonctionne pas pour les collections. Correctif pour CQ-4241122, CQ-4246558

**DAM - Client DM**

* La mise à niveau vers la version 6.4 supprime les profils de codage vidéo créés précédemment. Correctif pour CQ-4244067
* L’attribut Texte de remplacement est rompu dans le composant Dynamic Media. Correctif pour CQ-4244081
* (DMS7) La modification d’ensembles distants dans AEM n’est pas remplacée dans Scene7. Correctif pour CQ-4243430
* Vérification de la version 6.4 SP1 sur DM Hybrid. Correctif pour CQ-4244623
* (DMS7-UA) Lorsque vous cliquez sur le bouton Incorporer d’une ressource vidéo publiée, rien ne semble se produire. La boîte de dialogue Incorporer doit s’afficher avec le code de HTML. Correctif pour CQ-4245237
* (Hybride DM) Copier l’URL pour les ressources vidéo publiées ou les visionneuses de médias mixtes reçoit &quot;`[object Object]`&quot; dans la boîte de dialogue URL. Correctif pour CQ-4245236, CQ-4245451
* (DMHybrid) La page Affichage des détails de la vidéo ne contient pas l’aperçu de l’affichage de la ressource vidéo et génère un message d’erreur à la console. Correctif pour CQ-4244320
* Encodage S7 automatique du contenu we.retail. Correctif pour CQ-4242253
* Un nouveau paramètre prédéfini de codage vidéo ne peut pas être ajouté aux paramètres prédéfinis de traitement vidéo de mise à niveau ni modifier les paramètres prédéfinis de codage existants. Correctif pour CQ-4240407
* Les paramètres d’image prédéfinis de mise à niveau s’affichent comme Non publié sur la page Rendus et ne génèrent pas d’URL. Correctif pour CQ-4240406
* (CSS) Les ressources s’affichent, mais les visionneuses utilisées sont par défaut et non les visionneuses prêtes à l’emploi. Correctif pour CQ-4239839
* Désactivation de l’exécution manuelle de l’étape de nettoyage et utilisation des classes coraux privées. Correctif pour CQ-4239729
* La visionneuse d’images génère une erreur et n’affiche pas le recadrage intelligent correct. Correctif pour CQ-4237564
* Le paramètre prédéfini hérité sous /etc semble rompu et ne pas être migré vers l’emplacement sous /conf lors de l’enregistrement. Correctif pour CQ-4237416
* Régression dans OOB VideoViewer 5.8.x : la visionneuse développe l’iFrame à droite, rompant ainsi la mise en page. Correctif pour CQ-4235465
* (DMS7) Les boutons URL de rendu de recadrage intelligent et Incorporer sont principaux pour les images qui n’ont pas été publiées. Correctif pour CQ-4233696
* (DMHybrid) Restaurer la fonction de recadrage/rotation précédente. Correctif pour CQ-4239489
* Lors de la prévisualisation d’une vidéo en mode Carte, le bouton de lecture ne bascule pas vers la pause. Correctif pour CQ-4238592
* Lors d’une mise à niveau d’Opt-in, la configuration de YouTube n’est pas déplacée/copiée de son ancien emplacement vers le nouvel emplacement. Correctif pour CQ-4238590
* Les deux profils de traitement vidéo AVS DropTwo prêts à l’emploi sont répertoriés sous Propriétés du dossier et un seul contient des encodages définis. Correctif pour CQ-4238096
* (DMS7) Recadrage intelligent : Affichage des détails : Le bouton URL est intitulé Bouton Copier pour les rendus. Correctif pour CQ-4237804
* La page de liste des paramètres prédéfinis de la visionneuse reste vide même après l’exécution des commandes curl. Correctif pour CQ-4243246
* Désactivation de l’étape de nettoyage de l’exécution manuelle de l’étape de nettoyage et utilisation des classes coraux privées. Correctif pour CQ-4239729
* La page Détails du rapport vidéo n’affiche pas de ressource vidéo. Correctif pour CQ-4246208

**DAM - DMServices**

* (DMS7) Configuration du cloud : Impossible de synchroniser le nouveau contenu avec Scene7 après la mise à jour vers SP1. Correctif pour CQ-4244437
* (DMHybrid) Les profils de couleurs et les paramètres de catalogue ne sont pas enregistrés dans un appel debug_info=catalog . Correctif pour CQ-4242346
* Ajoutez des profils de couleurs aux paramètres du client sur les serveurs de diffusion. Correctif pour CQ-4241818, CQ-4241819
* (DMHybrid) Après la version 6.3 &amp;gt; Mise à niveau vers la version 6.4, les paramètres du catalogue sont déplacés vers le noeud incorrect. Correctif pour CQ-4239974, CQ-4239975
* (DMHybrid) Le script pushviewerpresets ne crée pas les noeuds nécessaires pour modifier les paramètres du catalogue. Correctif pour CQ-4240076
* Lors de l’utilisation de la liste déroulante &quot;Format&quot; et de la sélection de formats PNG ou JPG, le fichier téléchargé est affiché comme surchargé et plus foncé que la ressource d’origine. Correctif pour CQ-4240073
* (DMS7) Supprimez le mappage du type MIME : image_x-eps. Correctif pour CQ-4240394
* (DMS7) Les paramètres de chargement en arrière-plan ne transmettent pas ipsApiService.log et ne fonctionnent donc pas. Correctif pour CQ-4240686
* La mise à niveau des profils de traitement d’image créés dans une instance 6.3 vers 6.4 rompt la propriété &quot;Crop-type&quot;. Correctif pour CQ-4237739
* (Dynamic Media) Le chargement régulier de ressources en dehors du dossier de recadrage intelligent échoue. Correctif pour CQ-4237670
* Réglez le code de secours du profil pour le nom de profil &quot;Codage vidéo adaptatif&quot; sur &quot;Codage vidéo adaptatif&quot;. Correctif pour CQ-4237666
* Les données EmbedXMP sont toujours définies comme « actives » pour le workflow de génération Ptiff. Correctif pour CQ-4234498
* La saturation du rendu d’image CMJN est incorrecte. Correctif pour CQ-4235470
* Les paramètres du serveur d’images ne sont pas répliqués vers la diffusion pendant que les journaux de réplication les marquent avec succès. Correctif pour CQ-4239480, CQ-4239046
* (DMS7) Impossible de créer des ensembles à l’aide d’anciennes références ou de nouvelles références à la configuration du cloud. Correctif pour CQ-4238078
* L’étape de workflow Scene7 lit uniquement Scene7 dans le nom et la description, mais ne clarifie pas l’étape de workflow dans le workflow de mise à jour de gestion des actifs numériques. Correctif pour CQ-4237865

**DAM - Balises intelligentes**

* Introduit [Balises intelligentes améliorées](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951

**Forms**

Les correctifs d’AEM Forms sont fournis par le biais de packages de modules complémentaires et d’autres programmes d’installation de correctifs fournis avec la version. Pour plus d’informations, voir Versions d’AEM Forms.

Les principaux aspects pour AEM Forms sont les suivants :

* AEM Forms introduit [fonctionnalité de rapports sur les transactions](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) pour effectuer le suivi et conserver le nombre de transactions telles que les formulaires envoyés, les documents traités et les documents rendus sur votre déploiement AEM Forms. Il fournit des informations sur l’utilisation des produits et aide les utilisateurs professionnels à comprendre les volumes de traitement numérique.
* Activation de la prise en charge de PDF/UA pour les formulaires XML.
* Ajout de allowProxy = true pour Clientlib. **aemfd.ccm.channel.contentpage**
* Mise à jour du code afin de rendre la recherche avancée de titre comme contient plutôt que comme égal.
* Mise à jour vers la nouvelle version de Node Package Manager (NPM) sur la machine d’intégration continue.

**Package de modules complémentaires Forms**

**Intégration du serveur principal**

* Une erreur est générée lorsque la valeur est null en tant que valeur d’un champ facultatif. NPR-24397
* L’appel WSDL échoue lorsque l’élément possède un espace de noms différent de celui de l’espace de noms global. NPR-24281
* (FDM WSDL) Obtention de DermisException : Données de liste exclues dans le cas d’un tableau de type de propriété. NPR-24265
* (FDM WSDL) Obtention de DermisException : java.lang.Exception : createSOAPParam: Paramètres non valides. NPR-24264
* (SDK client FDM) Impossible de tester le préprocesseur/le post et l’action d’envoi personnalisée. Correctif pour CQ-4238469
* Correctifs de problèmes JavaDoc dans Dermis. Correctif pour CQ-4244250
* Amélioration de l’entrée dans le WSDL (Web Services Description Language). Correctif pour CQ-4244133
* Le test d’authentification de base pour WSDL génère une erreur différente pour la même configuration dans AEM 6.3 et AEM 6.4. Correctif pour CQ-4244132
* Demande d’inclusion de ValueUtil dans client-sdk et javadocs. Correctif pour CQ-4242803
* (Configuration du cloud FDM) Impossible de configurer l’authentification SOAP à partir de la configuration cloud. Correctif pour CQ-4238462
* Dermis - Ajoutez les packages manquants dans les Javadocs. Correctif pour CQ-4242815
* WSDLInvokerParams à inclure dans le sdk client du module complémentaire Forms. NPR-23381 : correctif pour CQ-4240233

**Formulaires adaptatifs**

* Le rendu de document (IC) doit être consigné en tant que transaction à l’aide du service d’enregistrement des transactions. Correctif pour CQ-4245333
* Lors de l’exécution d’UAT5, une entrée est manquante dans le fichier PDF généré à l’étape de vérification. Correctif pour CQ-4243184
* Cas de test pour une copie en profondeur de guideContext. Correctif pour CQ-4242924
* Le champ de type BAT est manquant lors de l&#39;exécution de UAT3 sur le dernier serveur mis à niveau. Correctif pour CQ-4243120
* Sur le serveur mis à niveau, les valeurs Etat/Province/Région et Pays présentes sur le serveur de pré-mise à niveau sont absentes du formulaire envoyé. Correctif pour CQ-4241444
* (Éditeur d’expression) Erreur lors de l’accès à l’étape Vérifier lors de l’envoi du formulaire. Correctif pour CQ-4241384
* Les valeurs sont manquantes lors de la vérification de l’étape sur le serveur avant la mise à niveau et mis à niveau pour le formulaire envoyé. Correctif pour CQ-4241896
* Le bouton Quitter et enregistrer en bas de la page ne fonctionne pas. Correctif pour CQ-4240112
* Numéro de contact manquant sur la configuration mise à niveau. Correctif pour CQ-4239870
* Sous `ACTION TAKEN` dans l’onglet Type de litige , &quot;Documents supplémentaires à l’appui de ma réclamation&quot; comporte un champ supplémentaire Type de BAT enregistré &quot;dedans&quot;. Correctif pour CQ-4239873
* &quot;Erreur dans getDataAPI&quot; lors de l’étape verifyPdf. Correctif pour CQ-4239865
* Erreurs dans les journaux de migration pour les instances de création et de publication. Correctif pour CQ-4239365
* Erreurs dans les journaux de migration pour les instances de création et de publication. Correctif pour CQ-4239635
* Erreur de désérialisation telle que &quot;Désérialisation non autorisée pour la classe sun.util.calendar.ZoneInfo&quot; dans les journaux d’erreur après l’envoi d’un formulaire adaptatif. Correctif pour CQ-4240419
* Le champ État n’est pas renseigné dans le rendu de formulaire Mobile. Correctif pour CQ-4240597
* Supprimez l’utilisation de référence des composants dans les modèles de la liste anti-motif. Correctif pour CQ-4239217
* La zone numérique HTML5 définie comme flottante ou décimale donne différents résultats de validation dans différents navigateurs. NPR-23528 : correctif pour CQ-4244097
* (Chargement d’image) L’image ne s’affiche pas dans l’aperçu DOR. Correctif pour CQ-4243178
* Le serveur JEE renvoie une erreur lors de la tentative d’envoi du formulaire adaptatif avec &quot;PDF de messagerie&quot; et &quot;Inclure les pièces jointes&quot;. Correctif pour CQ-4239894
* Le graphique n’est pas tracé au moment de l’exécution à l’aide d’un tableau/panneau. Correctif pour CQ-4240010
* L’envoi du formulaire adaptatif ne fonctionne pas et aucune modification n’est apportée au nombre de transactions en raison de l’échec de l’envoi. Correctif pour CQ-4246125
* (Choix de l’image) Les options de document d’enregistrement ne sont pas visibles. Correctif pour CQ-4236976
* L’interface utilisateur de l’éditeur de modèles n’est pas stable. Correctif pour CQ-4241497
* Les formulaires adaptatifs ne s’affichent pas à l’aide de l’onglet Ressources du panneau latéral, tandis que l’option Parcourir de la boîte de dialogue des propriétés AEM composant de formulaire. Correctif pour CQ-4236751
* L’ID de processus généré pour la conversion de formulaire doit être disponible dans le formulaire adaptatif généré. Correctif pour CQ-4240014
* Impossible de sélectionner le modèle pour créer une page dans les sites à mise à niveau directe : Livecycle vers le serveur 6.4. Correctif pour CQ-4241300

**Incohérence affectant le service assembleur**

* Connexion aux transactions dans les services Assembler. Correctif pour CQ-4245018, CQ-4245017, CQ-4245016.
* La transaction n’est pas consignée lorsque la conversion PDF/A est effectuée à l’aide de DDX. Correctif pour CQ-4246039

**Gestionnaire de formulaires**

* Liste des boutons FM CREATE à trier par ordre alphabétique. Correctif pour CQ-4242307

**Portail des formulaires**

* Les brouillons enregistrés sur le serveur avant la mise à niveau ne s’ouvrent pas correctement sur le serveur mis à niveau. Correctif pour CQ-4243303
* Mise à jour de la version 7.1 pour adobe-formsmanager-core-module. Correctif pour CQ-4245753
* Les brouillons enregistrés sur le serveur avant la mise à niveau ne s’ouvrent pas correctement sur le serveur mis à niveau. Correctif pour CQ-4243303
* Les scénarios de pièce jointe se rompent lors du remplacement/de l’ajout/de la suppression de pièces jointes dans une nouvelle instance/même instance de brouillon. Correctif pour CQ-4243165
* Le nombre de brouillons récupérés lors de l’interrogation de la base de données est supérieur au nombre de brouillons présents dans le portail. Correctif pour CQ-4241489
* Les Forms envoyées sur le serveur de prémise à niveau ne sont pas présentes sur le serveur mis à niveau. Correctif pour CQ-4241490
* Le formulaire affiché dans l’interface utilisateur de l’onglet des envois est à l’état Non envoyé malgré le message d’envoi réussi. Correctif pour CQ-4241487
* Le guideContext doit être formé en copiant en profondeur les champs car guideContext contient customPropertyMap qui est lui-même un objet . Correctif pour CQ-4240126
* Erreur lors de l’enregistrement d’un formulaire. Correctif pour CQ-4240763
* L’entrée pour les formulaires enregistrés et envoyés est renseignée dans crx/de malgré la configuration de base de données fournie dans la configuration des brouillons et des envois de Forms Portal. Correctif pour CQ-4240726
* (Search &amp; Lister) La valeur fixe du titre de la recherche avancée doit fonctionner comme contenir plutôt que comme égale. Correctif pour CQ-4245499

**Mobile Forms**

* Le champ de date chevauche dans Mobile Forms. Correctif pour CQ-4242256
* L’envoi de formulaire pour Mobile Forms doit être consigné en tant que transaction à l’aide du service d’enregistrement de transaction. Correctif pour CQ-4246166
* L’envoi du formulaire dans le jeu de formulaires doit être consigné en tant que transaction à l’aide du service d’enregistrement de transaction. Correctif pour CQ-4246165

**Application AEM Forms**

* (Application Windows) Impossible de générer le formulaire. Correctif pour CQ-4238005

**Workflow OSGI**

* Connexion des transactions dans la tâche d’affectation de workflow. Correctif pour CQ-4244440
* (Étape FDM) Impossible d’utiliser les valeurs des métadonnées de workflow lorsqu’une étape Affecter une tâche est insérée entre l’étape de processus et l’étape de fdm. Correctif pour CQ-4241472
* La délégation de tâche d’affectation ne fonctionne pas dans l’intégration Forms dans les workflows OSGI. NPR-23709 : correctif pour CQ-4243700
* (Éditeur de modèle de processus) Certains modèles de processus ne sont pas modifiables via l’éditeur de modèle WF de l’interface utilisateur classique. Correctif pour CQ-4241151

**Document multicanal**

* Le champ Date dans le modèle chevauche le sous-formulaire dans la création IC. Correctif pour CQ-4240110
* L’en-tête ne doit pas être autorisé à être supprimé ou déplacé vers le haut ou vers le bas dans la création de canal web IC. Correctif pour CQ-4243358
* (Éditeur IC) Les lignes par défaut doivent être définies sur 1 pour les composants Tableau. Correctif pour CQ-4244848
* Zone cible pour rester visible même après que le contenu a été glissé-déposé dessus. Correctif pour CQ-4244534
* Le canal web ne reconnaît pas l’espace des onglets dans les fragments de document texte. Correctif pour CQ-4244481
* (Canal d’impression) Le rendu de document (IC) doit être consigné en tant que transaction à l’aide du service d’enregistrement des transactions. Correctif pour CQ-4245335
* (Canal web) Le rendu de document (IC) doit être consigné en tant que transaction à l’aide du service d’enregistrement des transactions. Correctif pour CQ-4245334
* La recherche de conteneur de documents ou la recherche de l’arborescence du modèle de données doivent être unifiées à la recherche de filtre de ressources. Correctif pour CQ-4242305
* (Fragment de document) La propriété indentation indente le texte en fonction du nombre d’unités qui ne peuvent pas être comprises. Correctif pour CQ-4241082, CQ-4240643
* (Éditeur d’interface utilisateur) L’icône Modifier le fragment sur la mosaïque du fragment de document répertoriée sous l’onglet Ressources n’est pas facilement détectable et compréhensible. Correctif pour CQ-4241047
* Autoriser l’accès anonyme à la bibliothèque cliente inaccessible IC Anonymous. Correctif pour CQ-4245588
* (Canal web) Les données ne sont résolues dans aucun des tableaux de l’aperçu web et s’affichent comme vides. Correctif pour CQ-4244476
* Les en-têtes de tableau s’affichent sous forme de variables dans le canal web lors de la génération automatique. Correctif pour CQ-4244242
* (Éditeur d’interface utilisateur) Le contenu d’un fragment de document utilisé dans une interface utilisateur doit être automatiquement redimensionné pour s’adapter à la largeur de la zone cible. Correctif pour CQ-4244094
* Le nom du canal affiché en haut du centre doit être cohérent entre le titre IC pour WEB et l’IMPRESSION. Correctif pour CQ-4242498
* Le panneau Objet de données de l’éditeur de texte ne doit répertorier que les entités de niveau supérieur, correctif pour CQ-4244121
* Le nom par défaut n’est pas attribué lors de l’ajout d’un nouveau composant dans l’éditeur. Correctif pour CQ-4244691
* Ajout de la configuration Colspan dans tous les composants de canal web. Correctif pour CQ-4244946
* La propriété Largeur du tableau de fragment de mise en page n’est pas réinitialisée et n’est pas respectée dans le canal d’impression Lettre ou Communication client. Correctif pour CQ-4241574

**Correspondence Management**

* Sous-titres supprimés du modèle de lettre après modification d’une ressource de texte contenant des espaces réservés. NPR-24196
* Le fichier XDP, lorsqu’il est téléchargé et utilisé comme mise en page pour les modèles de lettre, ne parvient pas à prévisualiser ni à modifier les modèles. NPR-24143 : correctif pour CQ-4244407
* La sélection Attribution est sélectionnée par défaut dans le fragment de liste. Correctif pour CQ-4240097
* Éditeur de conditions : l’évaluation de résultats multiples doit être activée par défaut. Correctif pour CQ-4240096
* L’image lorsqu’elle est supprimée de la liste affiche toujours l’image en aperçu. Correctif pour CQ-4239909
* La règle définie sur le module de condition est définie sur &quot;Par défaut&quot; pour tous les modules. Correctif pour CQ-4239878
* La création du dictionnaire de données échoue avec l’erreur &quot;Exception JCR inconnue&quot;. Correctif pour CQ-4244122
* Différences dans la documentation JavaDocs de contenu 6.3. Correctif pour CQ-4213586

**Programme d’installation de Forms JEE**

**Base**

* (Espace de travail de HTML) Détails du suivi manquants pour les applications dont le nom contient des parenthèses. NPR-23402

**Service PDFG**

* Journalisation des transactions dans les services PDFG. Correctif pour CQ-4244951, CQ-4244586
* Réduction des PDF en désincorporant sélectivement les polices via un seul appel API. NPR-23287
* Problème de mise à jour des configurations PDFG lors de la mise à niveau d’AEM. Correctif pour CQ-4241176
* Journalisation des transactions dans PDFUtility Service. Correctif pour CQ-4245014

**Process Management**

* (Espace de travail HTML) Les points de départ du workflow ne sont pas triés dans un ordre alphanumérique. Correctif pour CQ-4239629
* (Espace de travail de HTML) Préparez l’appel de données à venir deux fois lorsque le brouillon est ouvert la première fois. Correctif pour CQ-4243280
* (Espace de travail de HTML) Le processus de préparation des données est déclenché lors de la fermeture d’un formulaire. Correctif pour CQ-4239456
* L’espace de travail se bloque lorsqu’il est parcouru entre deux tâches. Correctif pour CQ-4237125

**Workbench**

* Gérer le profil d’action Le processus de préparation des données échoue lorsque la configuration du processus de rendu par défaut est définie sur HTML. Correctif pour CQ-4244292

**Forms Designer**

* Ajout de la prise en charge de PDF/UA aux formulaires XML générés via Designer et Output Service. NPR-23022
* Les hyperliens en ligne définis dans le Concepteur ne sont pas balisés et ne contiennent pas de texte de remplacement lors de l’enregistrement au format PDF depuis le Concepteur. NPR-23023

**Feature Packs inclus**

**Ressources**

* Ajout de la fonctionnalité Balises intelligentes améliorées. Pour plus d’informations, voir [Balises intelligentes améliorées](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951 : correctif pour CQ-4234883
* Ajout de références AEM Assets dans InDesign. Pour plus d’informations, voir [Références AEM Assets en InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sites**

* Améliorations de l’éditeur d’image (création de page). Pour plus d’informations, voir [Éditeur d’image](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24267 : correctif pour CQ-4245502

**Lots OSGI et packages de contenu inclus**

Le texte suivant répertorie les lots OSGI et les packages de contenu inclus dans le CFP.

Liste des lots OSGi inclus dans AEM 6.4.1.0

[Obtenir le fichier](assets/6_4_1_0_bundle-list.txt)

Liste des packages de contenu inclus dans AEM 6.4.1.0

[Obtenir le fichier](assets/6_4_1_0_content-package-list.txt)

### Installation de la version 6.4.8.0 {#install}

#### Conditions requises {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Utilisateurs ayant installé Feature Packs sur AEM 6.4 : les Feature Packs en option fournis par Adobe ont des dépendances sur la version et le Service Pack. Si vous avez installé un Feature Pack, contactez l’équipe d’assistance clientèle d’AEM pour valider la compatibilité de ces Feature Packs avec ce Service Pack pour AEM 6.4.

* AEM 6.4.8.0 nécessite AEM 6.4. Pour plus d’informations, reportez-vous à la section [documentation de mise à niveau](../sites-deploying/upgrade.md).
* Le téléchargement du Service Pack est disponible sur [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) pour téléchargement.
* Lors d’un déploiement avec MongoDB et plusieurs instances, installez AEM 6.4.8.0 sur l’une des instances d’auteur à l’aide du gestionnaire de modules.
* Avant d’installer le pack de service, veillez à disposer d’un instantané ou d’une nouvelle sauvegarde de votre instance AEM.
* Redémarrez l’instance avant l’installation. Cela est nécessaire uniquement lorsque l’instance reste en mode de mise à jour (ce qui est le cas lorsque l’instance vient d’être mise à jour depuis une version antérieure). Toutefois, cela est généralement recommandé si l’instance s’est exécutée pendant longtemps.

>[!NOTE]
>
>Adobe recommande de ne pas supprimer ni désinstaller le package AEM 6.4.8.0.

### Installation du Service Pack via Package Manager {#install-the-service-pack-via-package-share}

Accomplissez les étapes suivantes pour installer le Service Pack sur une instance 6.4 existante :

1. Téléchargez le module à partir de Distribution logicielle.

1. Dans AEM, connectez-vous à Package Manager et ajoutez le package AEM 6.4.8.0 téléchargé. Sélectionnez le package téléchargé et cliquez sur **[!UICONTROL Installer]**.

>[!NOTE]
>
>**La boîte de dialogue sur l’interface utilisateur de Package Manager se ferme parfois de manière impromptue lors de l’installation de la version 6.4.8.0**
>
>Il est donc recommandé d’attendre que les journaux d’erreurs se stabilisent avant d’accéder à l’instance. L’utilisateur doit attendre les journaux spécifiques liés à la désinstallation du lot de mise à jour avant de s’assurer que les installations sont réussies. Cela se produit généralement sur Safari, mais peut se produire par intermittence sur n’importe quel navigateur.

### Installation automatique {#auto-installation}

Il existe deux manières d’installer automatiquement AEM 6.4.8.0 dans une instance en cours d’exécution :

A. Placez le package dans le dossier ..*/crx-quickstart/install* pendant que le serveur est en cours d’exécution. Le package est automatiquement installé.

B. Utilisez la variable [API HTTP à partir de Package Manager](/help/sites-administering/package-manager.md) - Assurez-vous que vous utilisez `cmd=install&recursive=true` - pour que le package imbriqué soit installé.

>[!NOTE]
>
>AEM 6.4.8.0 ne prend pas en charge l’installation de Bootstrap.

### Validation de l’installation {#validate-install}

1. La page Informations sur le produit (*/system/console/ productinfo *) doit maintenant afficher la chaîne de version mise à jour &quot;Adobe Experience Manager, Version 6.4.8.0&quot; sous Produits installés.
1. Tous les lots OSGI sont ACTIFS ou FRAGMENT dans la console OSGI (utiliser la console web : /system/console/bundles).
1. Le lot OSGI org.apache.jackrabbit.oak-core est sur la version 1.8.17 ou ultérieure (Utiliser la console web : /system/console/bundles).

Pour déterminer la plateforme certifiée pour exécuter cette version d’AEM Sites et d’Assets, voir [Exigences techniques](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Une fois l’installation du module terminée, un message d’information s’affiche pour vous informer que le module a bien été installé, par exemple : **&quot;Le package de contenu AEM-6.4-Service-Pack-7 a été installé avec succès.&quot;**

### Mise à jour des visionneuses Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.8.0 contient une nouvelle version des visionneuses Dynamic Media (5.10.1) qui permet de rechercher des noms en double sur la page Paramètre d’image prédéfini. Il est conseillé aux clients Dynamic Media d’exécuter la commande suivante pour mettre à jour les paramètres prédéfinis de la visionneuse prêts à l’emploi.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

qui copiera les nouveaux paramètres prédéfinis de visionneuse à l’emplacement /conf.

### Installation du module complémentaire AEM Forms {#install-aem-forms-add-on-package}

#### Installation du module complémentaire AEM Forms {#installaemformsaddon}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms. Les correctifs dans AEM Forms sont fournis dans un module complémentaire distinct.

>[!NOTE]
>
>AEM 6.4.8.0 inclut une nouvelle version du [package de compatibilité d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). Si vous utilisez une ancienne version du package de compatibilité AEM Forms et que vous mettez à jour vers AEM 6.4.8.0, installez la dernière version du package de compatibilité AEM Forms après l’installation du package de module complémentaire Forms.

1. Vérifiez que vous avez installé le Service Pack AEM.
1. Téléchargez le module complémentaire de formulaires correspondant répertorié à l’adresse [Versions d’AEM Forms](https://helpx.adobe.com/fr/aem-forms/kb/aem-forms-releases.html) pour votre système d’exploitation.
1. Installez le module complémentaire Forms comme décrit dans la section [Installation des packages de modules complémentaires AEM forms](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installation du programme d’installation d’AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms sous JEE. Les correctifs dans AEM Forms JEE sont fournis dans un programme d’installation distinct.

Pour plus d’informations sur l’installation du programme d’installation cumulatif pour AEM Forms JEE et la configuration post-déploiement, voir [AEM Forms JEE Patch Installer 0015](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### Paramètres de configuration requis pour NPR-21268 {#configuration-settings-required-for-npr}

Si vous utilisez l’ancienne interface utilisateur de Classic et que vous avez créé des modèles de métadonnées à l’aide de celle-ci, suivez les étapes d’exécution du script JMX pour les conserver.

1. Accédez à /system/console/jmx.
1. Cliquez sur &quot;Migrer les modèles de métadonnées&quot;.
1. Cliquez sur &quot;migrateMetadataTemplatesAtPath&quot; et indiquez le chemin du dossier sous lequel vous souhaitez conserver les modèles de métadonnées.

#### Paramètres de configuration requis pour NPR-24536 {#configuration-settings-required-for-npr-1}

Par défaut, la valeur pour la file d’attente partagée n’est pas actualisée pour les autres utilisateurs lorsqu’un utilisateur demande une tâche. Nous avons créé une nouvelle propriété pour cela. Suivez les étapes ci-dessous pour configurer cette propriété sur votre instance AEM :

1. Accédez à Interface utilisateur d’administration -> Services -> Espace de travail -> Administration globale.
1. Exportez les paramètres globaux.
1. Dans le fichier XML téléchargé, ajoutez la balise . &lt;client_taskspollinginterval>10&lt;/client_taskspollinginterval> Ici, 10 est l’exemple de valeur en secondes. Vous pouvez la modifier selon vos besoins.
1. Enregistrez le fichier.
1. Revenez à l’Interface utilisateur d’administration -> Services -> Espace de travail -> Administration globale.
1. Importez le fichier xml dans la section Importer les paramètres globaux.
1. Vous pouvez maintenant vous déconnecter du système et vous reconnecter.
1. La valeur pour la file d’attente partagée commence à être actualisée pour les autres utilisateurs de l’espace de travail.
1. Pour désactiver l’interrogation, définissez la valeur sur 0 et importez à nouveau le fichier XML.

### Uber Jar {#uber-jar}

Uber Jar pour AEM 6.4.8.0 est disponible dans la section [Référentiel Maven public Adobe](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/).

Pour utiliser Uber Jar dans un projet Maven, reportez-vous à l’article [Comment utiliser Uber Jar](../sites-developing/ht-projects-maven.md) et incluez la dépendance suivante dans votre projet POM :

```shell
<dependency>
      <code>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

### Fonctionnalités supprimées / obsolètes {#removed-deprecated-features}

Cette section répertorie les fonctionnalités qui ont été supprimées ou désignées comme obsolètes dans AEM 6.4.

| Zone | Fonctionnalité | Remplacement | Version |
|---|---|---|---|
| Ressources | Gestion de l’action de balise pour les sous-ressources | Aucun remplacement. | AEM 6.4.2.0 |
| Intégration des Ressources et d’Adobe Creative Cloud | [Le partage de dossiers AEM vers Creative Cloud](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) a été introduit dans AEM 6.2 afin de permettre aux créatifs d’accéder aux ressources depuis AEM. Adobe Asset Link, nouvelle fonctionnalité proposée dans l’application Creative Cloud, offre une expérience utilisateur améliorée et un accès plus puissant aux ressources d’AEM directement à partir de Photoshop, InDesign et Illustrator. Adobe n’apportera pas d’améliorations supplémentaires à la fonctionnalité de partage de dossiers. Bien que la fonctionnalité soit incluse dans AEM, les clients sont (il est vivement conseillé d’utiliser le remplacement). | Adobe d’Asset Link ou de l’appli de bureau. Pour plus d’informations, reportez-vous à l’article [Intégration d’AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

### Problèmes connus {#known-issues}

* Les erreurs et avertissements suivants peuvent s’afficher lors de l’installation :

   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Délai d’attente avant que la modification du reg ne soit terminée sans enregistrement.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` Aucune fenêtre de maintenance n’a été trouvée sur granite/operations/maintenance
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: La méthode unbindAmendment a généré une exception (java.lang.IllegalStateException: Service déjà désinscrit).
Ces erreurs ne nécessitent aucune action, car elles n’affectent pas votre instance AEM.

### Problèmes résolus {#resolved-issues}

**AEM 6.4.4.0**

* Aucune erreur de ressource trouvée n’est observée lors de l’importation/exportation de métadonnées. CQ-4253263
* Impossible de modifier les propriétés d’un composant d’image et d’une page après l’application de la version 6.4.3.0 sur la version 6.4.2.0. CQ-4260316 et CQ-4260441 Pour contourner ce problème :
   * Accédez à Package Manager
   * Réinstallez le package &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot;.
   * Recompiler tous les JSP `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` OU Redémarrez l’instance.

### Lots OSGi et packages de contenu inclus {#osgi-bundles-and-content-packages-included}

Les documents texte suivants répertorient les lots OSGi et les packages de contenu inclus dans AEM 6.4.8.0.

Liste des lots OSGi inclus dans AEM 6.4.8.0

[Obtenir le fichier](assets/6.4.8.0_osgi_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.8.0

[Obtenir le fichier](assets/6.4.8.0_content_packages.txt)

### Ressources utiles {#helpful-resources}

* [Notes de mise à jour d’AEM 6.4](../release-notes/release-notes.md)
* [Page de produits AEM ](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentation d’AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64.html?lang=fr)
* Abonnement aux [mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html)

### Sites restreints {#restricted-sites-new}

Seuls les clients peuvent accéder à ces sites. Si vous devez y accéder en tant que client, contactez votre gestionnaire de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/).
* Mises à jour de produit, correctifs et packages pour des fonctionnalités supplémentaires sur [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Service clientèle via Admin Console](https://adminconsole.adobe.com/). Pour plus d’informations, voir [Nouvelle expérience du service clientèle Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
