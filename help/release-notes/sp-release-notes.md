---
title: 'Notes de mise à jour d’AEM 6.4, Pack de services '
seo-title: 'Notes de mise à jour d’AEM 6.4, Pack de services '
description: Notes de mise à jour spécifiques aux Service Packs Adobe Experience Manager 6.4.
seo-description: Notes de mise à jour spécifiques aux Service Packs Adobe Experience Manager 6.4.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '21621'
ht-degree: 25%

---


# Notes de mise à jour d’AEM 6.4, Pack de services {#aem-service-pack-release-notes}

## Informations sur la version {#release-information}

| Produits | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.0 |
| Type | Version du Service Pack |
| Date | 5 mars 2020 |
| URL de téléchargement | aem 6.4.8.0 sur [Distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## Fonctionnalités présentes dans AEM 6.4.8.0 {#what-s-included-in-aem}

aem 6.4.8.0 est une mise à jour importante qui comprend de nouvelles fonctionnalités, les améliorations et les performances demandées par les clients clés, la stabilité et les améliorations de sécurité, publiée depuis la disponibilité générale de AEM 6.4 en **avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.8.0 inclut tous les Service Packs AEM 6.4 qui ont été lancés avant elle.

Les principaux points forts de cette version du Service Pack incluent les éléments suivants :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.20.

* La fonctionnalité de renvoi à la ligne de mots est prise en charge pour les sites Web japonais dans WCM-RTE.

* Le traitement des sauts de mot et des sauts de ligne est pris en charge pour les sites Web japonais.

* Prise en charge Ajoutée de l&#39;utilisation de la méthode BUNSETSU pour rompre la phrase et les lignes en japonais à des emplacements appropriés.

* L’interface utilisateur CCR pour la gestion de la correspondance prend désormais en charge les valeurs décimales pour les paramètres régionaux allemands.

* L’intégration du modèle de données de formulaire à l’aide du service Web SOAP prend désormais en charge les groupes de choix ou les attributs sur les éléments.

* AEM Assets est désormais configuré avec le portail de marque via Adobe I/O.

* Mise à jour de la version jQuery fournie dans ContextHub à 3.2.1.

## Liste des modifications  {#list-of-changes}

### Sites {#sites}

* Lorsqu’une URL d’une page AEM Sites contient un symbole deux-points ou un pourcentage, le navigateur sous-jacent cesse de répondre et les cycles de processeur montrent un pic (NPR-32368, NPR-31917).
* Lorsqu’une page AEM Sites est ouverte pour modification et qu’un composant est copié, l’action de collage reste indisponible pour certains espaces réservés (NPR-32328).
* Le processus de demande d’activation n’inclut pas les ressources référencées (NPR-32304).
* Lorsqu&#39;un schéma directeur est créé, si le nombre d&#39;enregistrements est supérieur à 80, seuls les 80 premiers enregistrements sont affichés. Le plan directeur affiche des lignes vierges pour le reste des enregistrements (NPR-32058).
* Les utilisateurs sont autorisés à enregistrer un fragment de contenu sans fournir aucune information dans les champs requis (NPR-31988).
* La navigation automatique ne fonctionne pas pour le chemin configuré dans un composant de fragment d’expérience principale (NPR-31921).
* Lorsque vous modifiez le type d’une cellule de tableau dans l’éditeur de texte enrichi (RTE), l’erreur suivante se produit :
   `Error: No common ancestor found, cannot continue` (NPR-31916).
* Lorsque le contenu est déplacé dans le même dossier, l’option de déplacement de page est désactivée (NPR-31841).
* Prise en charge Ajoutée de la division des phrases en japonais à l&#39;aide de la méthode BUNSETSU et de la séparation des lignes à la position appropriée (NPR-31836).
* Lorsque vous modifiez un hyperlien dans l’éditeur de texte enrichi (RTE), le chemin d’accès nouvellement sélectionné n’est pas enregistré (NPR-31659).
* Lorsque vous supprimez un composant multichamp et annulez la suppression, le composant est restauré mais les données ne sont pas restaurées (NPR-31617).

### Ressources {#assets}

* Un dossier sans nom est créé dans SPS (Scene7 Publishing System) lors du déplacement d’un fichier d’un dossier à un autre en Experience Manager avec la configuration Dynamic Media (NPR-32440).

* La page des détails des ressources des fichiers PDF n’affiche pas les boutons d’action dans le Experience Manager s’exécutant en mode Scene7 (NPR-32316).

* Impossible de supprimer les rendus de fichier et de vidéo (NPR-32213).

* L&#39;icône de calendrier pour l&#39;activation planifiée ne s&#39;affiche pas dans la colonne État (dans l&#39;interface utilisateur classique de la liste des ressources DAM) pour les ressources dont l&#39;activation est planifiée pour une date et une heure ultérieures (NPR-32198).

* La relation des actifs est remplacée lorsque les actifs sont liés à plusieurs actifs à l’aide d’Autres (NPR-32196).

* Le bouton Enregistrer n’importe pas la visionneuse à distance lorsque l’utilisateur n’a apporté aucune modification à l’éditeur de visionneuses dans le client Dynamic Media (NPR-32178).

* L’ingestion de ressources PSD provoque un pic de l’UC et une instance d’auteur Experience Manager non réactive (NPR-32165).

* Exception de mémoire insuffisante observée lorsqu’un fichier ZIP volumineux est téléchargé dans la gestion des actifs numériques Experience Manager (NPR-32155).

* Les URL d’historique des versions s’affichent sous le champ Référencé par sur la page de propriétés des ressources (NPR-31889).

* L’annulation de la publication à partir du portail de marque, sur la page Gérer les publications, échoue pour les sous-dossiers d’un dossier publié (NPR-31835).

* Le transfert des codes vidéo Dynamic Media échoue lorsque la configuration de Scene7 Cloud est placée dans un dossier privé `/conf` au lieu de `/conf/global` (NPR-31779).

* L’image n’est pas visible sur la chronologie après l’ajout d’annotations, sur le Experience Manager s’exécutant en mode d’exécution Scene7 (NPR-31754).

* Impossible d&#39;ouvrir le fichier ZIP téléchargé à partir de DAM à l&#39;aide de WinZip (NPR-31745).

### Intégrations {#integrations-6480}

* Les menus déroulants **Société** et **Rapports** Suite sont masqués une fois que **Source du Rapports** est sélectionné lors de la configuration de Adobe Analytics dans les services de cloud Experience Manager (NPR-31729).

* Les propriétés Adobe Campaign ne sont pas nettoyées lorsque la copie de langue d&#39;un bulletin d&#39;information lié à un Adobe Campaign est faite, alors que le nettoyage se produit lorsqu&#39;un bulletin d&#39;information lié à un Adobe Campaign est copié ou collé (NPR-32540).

* ReportSuitesServlet est vulnérable au SSRF (NPR-32161).

### Sling {#sling-6480}

* L&#39;observation des ressources ne fonctionne pas avec un ombrage non déterministe (CQ-4286466).

### Projets {#projects-6480}

* Le bouton Créer n’est pas visible pour l’utilisateur, même s’il est autorisé à créer un projet dans le sous-dossier (NPR-31831).

* La fonctionnalité permettant de basculer entre la Vue de carte, la Vue de Liste et la Vue de calendrier ne fonctionne pas après avoir sélectionné vue de calendrier dans les projets (NPR-31829).

### Traduction {#translation-6480}

* La création d&#39;un projet de traduction pour plusieurs langues génère le projet uniquement pour certaines langues au lieu de toutes et une erreur (le résolveur de ressources est déjà fermé) est observée dans le journal (NPR-32212).

### WCM-MSM {#wcm-msm-6480}

* Les problèmes d&#39;autorisation entraînent l&#39;affichage d&#39;erreurs lors du déplacement de pages dans un plan directeur (NPR-32610).

### Éditeur de page WCM {#wcm-page-editor-6480}

* Le navigateur cesse de répondre lors de la tentative d&#39;ajout d&#39;un composant à une page avec un format d&#39;URL spécifique (NPR-32368, NPR-31917).

### Interface utilisateur WCM-Admin {#wcm-admin-ui-6480}

* La gestion de la publication n’inclut pas les ressources référencées dans le processus de demande d’activation (NPR-32304).

### Communities {#communities}

* Impossible de mettre à jour l&#39;image miniature de groupe pour les groupes (NPR-32603).

### Brand Portal {#brand-portal}

* L’annulation de la publication du schéma de métadonnées dans AEM Assets renseigne un message d’erreur bien que le schéma soit supprimé sur le serveur principal (CQ-4286871).

### Interface utilisateur de Foundation {#foundations-ui-6480}

* Les caractères non valides s&#39;affichent dans l&#39;URL ajoutée à un composant Button (NPR-32684).

### Formulaires {#forms}

>[!NOTE]
>
>Le Service Pack AEM n’inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un module complémentaire Forms distinct.  En outre, un programme d’installation cumulatif est publié, qui comprend des correctifs pour AEM Forms on JEE. Pour plus d’informations, voir [Installer le module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installer le programme d’installation AEM Forms JEE](#install-aem-forms-jee-installer).

* Designer : Si l’option de balisage est activée, la bordure du sous-formulaire disparaît dans la sortie PDF générée (NPR-32546, NPR-32322).

* Designer : S’il existe des cellules fusionnées dans un tableau, le test d’accessibilité échoue pour le fichier PDF de sortie converti à partir d’un formulaire XDP à l’aide du service de sortie (NPR-32079).

* Sécurité du document : Un fichier PDF protégé ne parvient pas à s&#39;ouvrir hors connexion avec l&#39;option DisableGlobalOfflineSynchronizationData définie sur True (NPR-32080).

* Sécurité du document : Problèmes lors de l’ouverture d’un fichier PDF protégé après la mise à niveau d’ES4 vers AEM 6.3 (NPR-32170).

* Document Services : Un message d’erreur s’affiche lors de la tentative de conversion d’un fichier PDF en document PDF/A à l’aide de la méthode de conversion toPDFA (NPR-32663).

* Document Services : Une exception s’affiche lors de l’application du service Reader Extensions sur un fichier PDF (NPR-32639).

* Document Services : Un message d’erreur s’affiche lors de l’assemblage et de la conversion de fichiers XDP en fichiers PDF (NPR-31821).

* Analytics n’affiche pas les résultats appropriés lors de l’envoi ou de l’abandon de formulaires sur une page de sites (NPR-31359).

### Correctifs et packs de fonctionnalités inclus dans les packs de service précédents {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

aem 6.4.7.0 est une mise à jour importante qui comprend des améliorations et des correctifs concernant les performances, la stabilité, la sécurité et les clients clés publiés depuis la disponibilité générale de AEM 6.4 en **avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.7.0 inclut tous les Service Packs AEM 6.4 version antérieure.

Voici quelques-uns des points saillants de l&#39;AEM 6.4.7.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.17.
* Prise en charge Ajoutée de la définition de la version d&#39;une page Sites lors de sa suppression.
* Une nouvelle colonne pour la date créée, qui peut être triée, a été ajoutée dans la vue **liste DAM** et dans les résultats de la recherche de ressources dans la vue **Liste** (NPR-31311).
* Le tri des ressources basé sur la colonne **Nom** a été autorisé dans la vue **Liste**.
* La taille du lot et le délai d’expiration du flux de travail pour le retraitement et le transfert par lot sont désormais configurables à partir de l’interface utilisateur de Dynamic Media.
* Le paramètre `pdfBrochure` a été défini sur false dans la configuration cloud de Scene7, afin d’enregistrer de la mémoire dans IPS.

##### Ressources {#assets-6470}

**Améliorations des produits**

* La version d’exportation du package d’API `package com.day.cq.dam.handler.standard.msoffice` prise en charge par le lot `dam-handler` est mise à niveau vers 6.0.0 (CQ-4279059).
Si vous utilisez le package `com.day.cq.dam.handler.standard.msoffice` dans votre implémentation personnalisée, il est conseillé de compiler votre lot `dam-handler` avec le dernier fichier jar uber.

* Une nouvelle colonne pour la date de création, qui peut être triée, a été ajoutée dans la vue de liste DAM et sur les résultats de la recherche de ressources dans la vue de liste (NPR-31311).

* Le tri des ressources basé sur la colonne Nom a été autorisé dans la vue de Liste (NPR-31299).

**Correctifs**

* Les métadonnées de certains documents PDF ne sont pas mises à jour et enregistrées dans le PDF lors de la modification de son titre (NPR-31575).

* Les fichiers dont le nom de fichier contient le symbole &quot;+&quot; ne peuvent pas être supprimés (NPR-30588).

* Les propriétés du dossier DAM n’affichent pas les utilisateurs ou groupes ajoutés (créés par synchronisation LDAP) dans les groupes d’utilisateurs fermés (NPR-30555).

* Les caractères spéciaux se trouvant dans la ligne Objet des modèles de courrier électronique ne s’affichent pas correctement (NPR-30547).

* Les noms des fichiers sont changés en minuscules lorsque vous déplacez des fichiers d’un dossier à un autre dans AEM exécution en mode d’exécution Dynamic Media Scene 7 (NPR-31631).

* Les noms des visionneuses d’images sont changés en minuscules dans Scene 7, lorsque des visionneuses d’images (ou visionneuse de supports) sont créées et nommées avec la convention d’affectation de nom appropriée dans DAM (NPR-31576).

* Le flux de travail Dynamic Media Encode Video ne parvient pas à générer la miniature de la vidéo qui est migrée de Scene7 vers le mode d’exécution Dynamic Media - Scene 7 (NPR-31523).

* Une erreur de serveur interne est observée lors de l’utilisation du filtre pour rechercher des visionneuses, en AEM s’exécutant en mode d’exécution Dynamic Media - Scene 7 (NPR-31388).

* Une erreur est observée lors de la modification d’un ensemble d’images distant, pour l’image résidant dans le dossier portant le même nom que le nom de la société Scene7 (NPR-31347).

* Les ressources contenant des références ne sont pas publiées (DM) (NPR-31179).

* La valeur d’expiration (délai d’activation du cache client) configurée pour le mode hybride de Dynamic Media n’est pas répliquée dans l’environnement de diffusion de Dynamic Media (NPR-31126).

* Les téléchargements depuis AEM Dynamic Media - Mode d’exécution Scene7 vers Scene7 prennent trop de temps à se terminer (NPR-30926).

* Après avoir créé une page comportant un composant Dynamic Media lors de la publication de la même page, à partir de l’instance d’auteur s’exécutant sur le mode d’exécution Dynamic Media - Scene 7, l’utilisateur est invité à publier la configuration dmscene7 (NPR-30880).

* La valeur du paramètre &quot;asset&quot; dans le code incorporé de la visionneuse reste inchangée après avoir modifié les valeurs des champs Titre après déplacement et Nom après déplacement dans Dynamic Media - Scene7 (NPR-30745).

* La page de résultats de la recherche tactile dans l&#39;interface utilisateur (effectuée via Omnisearch) défile automatiquement vers le haut et perd la position de défilement de l&#39;utilisateur (NPR-31306).

* DAM Événement Purge supprime les dernières données du événement (maxSavedActivities) et conserve les données créées précédemment (NPR-30870).

* La modification du titre et du nom de la ressource n’est pas conservée après l’opération de déplacement vers un dossier de destination qui déclenche un défilement infini lors de sa sélection (NPR-30647).

* Les collections sont supprimées de la vue lors de l’application d’un filtre dans AEM Assets accessible à partir du lien d’actif d’Adobe (CQ-4280534).

* La taille du lot et le délai d’expiration du flux de travail pour le retraitement et le transfert par lot ne sont pas configurables à partir de l’interface utilisateur et doivent être définis dans CRXDE et le flux de travail doit être synchronisé deux fois (CQ-4281254).

* Le nom de l’étape de flux de travail pour le transfert par lot et l’étape de transfert simple est identique dans Scene7, ce qui entraîne une certaine confusion (CQ-4281176).

* Le processus de retraitement dans Scene7 se bloque si un fichier ne comporte pas de noeud de métadonnées (CQ-4281170).

* L’étape de transfert par lot dans le processus de retraitement ne fonctionne pas pour le dossier contenant une ressource vidéo (CQ-4280630).

* Par défaut, les options PDF envoyées à DM contiennent la valeur extractKeywords définie sur true (CQ-4280101).

* Une exception de point nul est observée lors de l’exécution du processus de retraitement de Scene7 dans un dossier contenant des ressources non DM (CQ-4279555).

* Le changement de nom des fichiers dans AEM ne parvient pas à se synchroniser avec la scène 7, lorsqu’un fichier portant un nom de duplicata existe déjà dans Scene7 (CQ-4276763).

* Le fichier zip envoyé par courrier électronique pour le téléchargement de fichier ne se décompresse pas lorsqu’un utilisateur disposant d’autorisations de lecture tente de l’ouvrir (CQ-4277925).

* Le flux de travaux de rendu PPT ne parvient pas à générer des rendus des fichiers PPT téléchargés, car AEM 6.4 ne parvient pas à mettre à jour vers com.adobe.granite.poi version 2.0.28 (CQ-4279059).

* Les fichiers PDF ne sont pas indexés et le contenu au sein de ne peut pas faire l’objet de recherches (CQ-4278916).

##### Sites {#sites-6470}

* Lorsque les lancements sont promus avec les pages uniquement modifiées et que les lancements avec les pages modifiées sont effectués, seules les pages modifiées apparaissent en promotion. De plus, lorsque la liste à promouvoir est correcte, les pages non modifiées sont toujours affichées au bas de la liste (NPR-31314).

* Lorsqu’une page AEM Sites est déplacée à un autre emplacement, ses propriétés ne sont pas mises à jour en conséquence pour refléter son nouvel emplacement (NPR-31265).

* Pour un nouveau plan directeur, si le nombre d&#39;enregistrements est supérieur à 40, seuls les 40 premiers enregistrements sont affichés. Le plan directeur affiche des lignes vierges pour le reste des enregistrements (NPR-31182).

* Lorsque le nombre de LiveCopies est important, l’aperçu de LiveCopy prend du temps pour générer la prévisualisation (NPR-30945).

* Prise en charge Ajoutée de la définition d’une version d’une page lors de sa suppression. Si le contrôle de version est désactivé pour la page supprimée, AEM Sites ne peut pas restaurer ces pages (NPR-30891).

* Lorsqu&#39;un utilisateur ajoute des caractères japonais ou coréens à la propriété description d&#39;un menu, celui-ci affiche des caractères déformés pour le texte en japonais et en coréen (NPR-31331).

* Lorsqu’un utilisateur se concentre sur les champs du rail gauche et utilise un raccourci clavier pour coller du contenu, il colle le le contenu du Presse-papiers de l’éditeur de page au lieu du contenu copié à partir des champs du rail gauche (NPR-31169).

* Lorsqu’un utilisateur modifie un fragment de contenu, la variante déjà supprimée du fragment de contenu est restaurée (NPR-31178).

* La requête Modèles de fragments de contenu est inefficace. Il est très lent si l&#39;instance comporte beaucoup de pages et génère une erreur (NPR-30666).

* Lors de l’enregistrement du modèle de fragment de contenu, l’heure dans le champ de date et d’heure est définie sur 00:00 (NPR-30540).

##### Intégrations {#integrations-6470}

* Lors de la configuration du lancement d’Adobe, une barre oblique (/) est précédée dans l’URL de la bibliothèque (NPR-30700).

* Les performances de ContextHub se dégradent après la publication (NPR-30884).

##### Sling {#sling-6470}

* Mettez à jour la version du lot du fournisseur de sécurité de webconsole vers la version 1.2.4 afin de supprimer la dépendance de l’api de démarrage du pavé de lancement de webconsolesecurityprovider (NPR-30885).

##### Plate-forme {#platform-6470}

* Les mises à jour de la configuration de la taille de la mémoire tampon pour le service HTTP basé sur Jetty ne sont pas enregistrées (NPR-30925).

* QueryBuilder prend désormais en charge orderby fn:name() dans les requêtes xpath (NPR-31322).

* Mise à jour de l’administration de événement distribuée Sling vers la version 1.1.4 afin d’améliorer la qualité des journaux dans un environnement organisé en grappes (NPR-29256).

##### Interface utilisateur de Foundation {#foundation-6470}

* Si vous faites défiler la page jusqu’à la fin de la page de résultats avec un grand nombre de résultats de recherche, le navigateur se bloque (NPR-31332).

* Lorsque vous passez de la vue Carte à la vue Liste sur une page de résultats de recherche, il y a un décalage avant que la page puisse être défilée (NPR-31280).

##### Chêne {#oak-6470}

* Les fichiers MS Office avec des extensions de fichiers .docx et .xlsx contenant des images JPEG ne sont pas analysés à l&#39;aide de l&#39;analyseur Tika (NPR-31693).

##### Livefyre {#livefyre-6470}

* L’intégration de Livefyre avec la mise à niveau AEM 6.4 donne une exception Null Point, lorsque l’intégration est effectuée à l’aide du module externe DITA pour les ressources synthétiques. L’intégration fonctionne toutefois lorsque des composants sont ajoutés manuellement (FYR-11066).

##### Traduction {#translation-6470}

* Le chemin d’accès au fragment d’expérience de destination n’est pas mis à jour lors de la promotion d’une page de lancement (NPR-30830).

##### Communautés {#communities-6470}

* La fonctionnalité de courrier électronique ne fonctionne pas correctement dans certains cas, même si la messagerie électronique est activée dans les paramètres de notification, le système renvoie une exception dans NotificationsActivityStreamProvider (NPR-31521).
* Impossible de créer de nouveaux membres, un écran vide s&#39;affiche sur l&#39;écran Créer un membre de l&#39;instance d&#39;auteur AEM (NPR-30951).
* L&#39;utilisateur ne peut pas publier de commentaire sur un blog dans Internet Explorer 11 (NPR-30927).
* L&#39;administrateur d&#39;un groupe restreint n&#39;est pas en mesure de vue de la carte de groupe, il ne peut pas effectuer d&#39;opérations de lien rapide (groupes Modifier/Publier/Supprimer) dans AEM instance d&#39;auteur (NPR-30810).
* Les informations des groupes de membres et des groupes ne sont pas visibles lors de la création d&#39;un nouveau site dans AEM instance d&#39;auteur (NPR-28840).

##### Formulaires {#forms-6470}

>[!NOTE]
>
>Le Service Pack AEM n’inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un module complémentaire Forms distinct.  En outre, un programme d’installation cumulatif est publié, qui comprend des correctifs pour AEM Forms on JEE. Pour plus d’informations, voir [Installer le module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installer le programme d’installation AEM Forms JEE](#install-aem-forms-jee-installer).

**Package de modules complémentaires Forms**

**Formulaires adaptatifs**

* Les chaînes contiennent la clé du dictionnaire lors de la localisation des formulaires adaptatifs (NPR-31109).

* Les cases à cocher et les listes déroulantes de Forms ne permettent pas de vérifier l’accessibilité (NPR-31282).

**Formulaires HTML5**

* La génération de l’aperçu HTML5 d’un formulaire XDP affiche un scintillement lors de l’ajout d’instances d’un sous-formulaire (NPR-30907).

**Document Services pour OSGi**

* L’exécution simultanée de plusieurs threads pour assembler les formulaires à l’aide de la méthode com.adobe.fd.assassembler.service.AssemblerService.invoke() affiche un message d’erreur (NPR-31164).

* Les fichiers temporaires créés par Assembler Service ne sont pas automatiquement supprimés et nécessitent un redémarrage AEM (NPR-30846).

* L’application des droits ReaderExtension au format PDF génère un message d’erreur (NPR-30930).

**Processus**

* Le processus OSGi échoue en raison d’une utilisation 100 % du processeur (NPR-31234).

**Programme d’installation de Forms JEE**

**Services de document**

* Le service Convert PDF ne parvient pas à convertir les documents PDF en PostScript et affiche un message d’erreur (NPR-31267).

* La configuration du point de terminaison SOAP se réinitialise après l’application d’un correctif pour corriger l’échec de HTML en PDF (NPR-31309).

**Service PDFG**

* Impossible de télécharger le fichier de paramètres Adobe PDF téléchargé à l&#39;aide de l&#39;interface utilisateur d&#39;administration (NPR-31273).

#### aem 6.4.6.0 {#experience-manager-6460}

aem 6.4.6.0 est une mise à jour importante qui comprend des améliorations et des correctifs concernant les performances, la stabilité, la sécurité et les clients clés publiés depuis la publication de AEM 6.4 en **avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.6.0 inclut tous les Service Packs AEM 6.4 version antérieure.

Voici quelques-uns des points saillants de l&#39;AEM 6.4.6.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.15.
* Prise en charge Ajoutée du suivi des états de l’interface utilisateur dynamique dans le événement de suivi dans l’API de base.
* Prise en charge Ajoutée du rendu pour le composant principal d’image.

**Ressources**

* Le lien de partage de ressources d’un dossier avec espace et caractère `&` dans le nom affiche des cartes grises vierges pour certains fichiers. NPR-29934 : correctif pour CQ-4270187
* Le flux de travail DAM se bloque lors de la création de ressources MP4 pour AEM. NPR-30031 : correctif pour CQ-4271352
* Problème de connectivité d’Adobe Smart Tag via Datapower. NPR-30026 : correctif pour CQ-4269457
* Impossible de trouver le fichier PDF à l&#39;aide d&#39;OmniSearch. NPR-30046 : correctif pour GRANITE-26290
* Les chemins d’accès aux ressources dans les URL et les métadonnées des dossiers générés par l’API ACP ne sont pas codés dans les URL.  GRANITE-26198 : correctif pour CQ-4271814
* La fonctionnalité Créer une tâche de révision ne fonctionne pas en raison d’une charge utile non définie. NPR-30469 : Correctif CQ-4274263
* La possibilité de basculer la vue de la vue de carte à la vue de liste et vice versa disparaît après avoir effectué une recherche OmniSearch sur le sélecteur de ressources. NPR-29852 : correctif pour CQ-4269369
* (Interface utilisateur tactile) Au cours de l’assistant de gestion de publication, des ressources sont ajoutées à la file d’attente de réplication après l’ajout des pages, ce qui entraîne l’affichage de certaines ressources après quelques secondes. NPR-29985 : correctif pour CQ-4270724
* Le tri des requêtes par pertinence renvoie des documents InDesign ainsi que des modèles InDesign. Correctif pour CQ-4273864
* Si l’utilisateur dispose d’un ID de courrier électronique en majuscules, il n’est pas possible d’archiver les fichiers qui ont été précédemment extraits. Correctif pour CQ-4276575
* La configuration des Cloud Services Dynamic Media en mode `DMHybrid` entraîne la création de plusieurs suites de rapports vides dans Analytics, sans ID de suite de rapports stocké sur AEM, ce qui entraîne la duplication des suites de rapports. Correctif pour CQ-4276855
* La boîte de dialogue d’avertissement n’apparaît pas lors de la promotion dans la page &quot;Balise gérée&quot;. Correctif pour CQ-4252851
* Lors de l’utilisation du carrousel pour la gestion des balises, le bouton de navigation ne fonctionne pas. Correctif pour CQ-4275499
* La fonctionnalité de déplacement en masse des ressources est interrompue, ce qui entraîne la non-circulation des ressources. Correctif pour CQ-4272987

**Sites**

* `pageinfo.json` les requêtes sont extrêmement lentes et leur chargement prend trop de temps. NPR-29709 : correctif pour CQ-4269560
* `onTime` ou les propriétés de  `offTime` métadonnées enregistrées sur des ressources ne sont pas rappelées si le serveur AEM est redémarré. NPR-30413 : correctif pour CQ-4272784
* En raison d&#39;un comportement incorrect de la classe ConfigPostProcessor, la suspension de la page parente supprime cq : Type de mixage LiveRelationship à partir de la page enfant. NPR-30536, NPR-30510 : correctif pour CQ-4254113
* Création de scripts intersites (XSS) dans la boîte de dialogue de flux de travaux au Début de la page de modification de Campaign. NPR-29747 : correctif pour CQ-4271067
* (Interface utilisateur classique) L’étape de verrouillage de processus désactive l’onglet de processus jusqu’à ce que le verrouillage soit libéré. NPR-30356 : correctif pour CQ-4237557
* (IE11) Lors du collage de contenu HTML dans un composant Editeur de texte enrichi avec defaultPasteMode = texte brut, le code HTML est collé avec la mise en forme. Par conséquent, defaultPasteMode n’a aucun effet. NPR-30045 : correctif pour GRANITE-26094
* (IU classique) Lorsque la page d’administration du site est rechargée, tous les éléments de liste déroulante du menu &quot;Nouveau&quot; sont désactivés. NPR-29980 : correctif pour CQ-4272044
* Impossible d&#39;ajouter des styles au texte ou de modifier les styles existants créés sur le contenu. NPR-29712 : correctif pour CQ-4266249
* (IU classique) Fichiers sans dc : la valeur de titre est répertoriée sans titre dans le navigateur de la boîte de dialogue de champ de chemin. NPR-30166 : demande de rétroportage pour CQ-88858
* Le cq : le module d’écoute ne fonctionne pas avec les composants imbriqués, même après l’ajout du composant parsys. NPR-30422 : correctif pour CQ-4274863
* Erreur ContextHub durant l’intégration d’AEM et de Campaign. NPR-30625 : correctif pour CQ-4250790
* La valeur du paramètre de requête resourceType est copiée dans la valeur d’un attribut de balise HTML encapsulé dans des guillemets doubles. NPR-29832 : correctif pour CQ-4255365
* Une actualisation de page est nécessaire une fois que les composants sont copiés et collés d’une page à une autre. NPR-29982 : correctif pour CQ-4256019
* La fonction Publier/Annuler la publication d’un alias de page n’est pas prise en charge et doit être supprimée. NPR-30062 : correctif pour CQ-4271249
* Avertissement ResourceResolver non fermé dans ExperienceFragmentsReplicationListener provoquant des problèmes de stabilité au fil du temps, forçant à redémarrer les instances AEM. NPR-30416 : correctif pour CQ-4257521
* Le déplacement des fragments d’expérience référencés dans plus de 150 pages ne modifie pas fragmentPath dans les pages où ils sont référencés. NPR-30556 : correctif pour CQ-4274900
* Erreur d’analyse lors de l’ouverture d’un fragment de contenu contenant des caractères dollar (`$`) et accolade ouverte (`{`) l’un après l’autre. Correctif pour CQ-4270266
* VersionPreviewServlet échoue dans NullPointerException lors de l’affichage d’une version d’un fragment d’expérience dans la chronologie. NPR-30074 : correctif pour CQ-4271881
* Impossible de verrouiller les fragments de contenu par l&#39;intermédiaire de la fonction d&#39;archivage. NPR-29923 : correctif pour CQ-4258785
* Échec de la vérification de la signature dans le gestionnaire d&#39;authentification SAML. NPR-30379 : Demande de report pour GRANITE-26567

**Réplication**

* La session JCR / Resource Resolver est divulguée lors de l&#39;implémentation OAuth sur chaque réplication vers MAC / Brand Portal. NPR-30000 : correctif pour Granite-26196

**Sling**

* L&#39;ordre des enfants affectés par le chevauchement et l&#39;ordre antérieur provoque IndexOutOfBoundException. NPR-30408 : Correctif pour Sling-8296 et Sling-7375
* InactiveBundlesHealthCheck lit la configuration MissingPackagesHealthCheck une fois les configurations InactiveBundlesHealthCheck enregistrées. NPR-30084 : correctif pour CQ-4272644

**Commerce**

* Impossible d&#39;exécuter le plan de catalogue à partir de la console Sites. NPR-29829 : correctif pour CQ-4271461
* L’actif utilisé dans le produit n’affiche aucune référence au produit dans la section &quot;Références&quot; de l’actif, ni le chemin d’accès à l’actif n’est mis à jour si l’actif est déplacé. NPR-30542 : correctif pour CQ-4270247

**Plate-forme**

* AEM Default Mail Sender ne peut pas envoyer de courrier à un serveur SMTP distant via TLS v1.2. NPR-30476 : Correctif pour GRANITE-26605

**Communities**

* Les groupes supprimés sur l’auteur ne sont pas synchronisés avec tous les éditeurs. NPR-29987 : correctif pour CQ-4268738
* Les utilisateurs supprimés du champ Administrateurs de la communauté ne sont pas synchronisés avec le groupe Membres. NPR-30389 : correctif pour CQ-4274339
* Les utilisateurs du groupe d’administrateurs ne disposent pas de liens rapides pour ce groupe. NPR-30546 : correctif pour CQ-4275579
* La mise à jour de tout nouveau groupe de la communauté créé et existant remplace la propriété sur jcr : noeud de contenu et remplace leur nom par le titre de la première page. NPR-30109 : correctif pour CQ-4273719
* La recherche rapide et la recherche dans l&#39;emplacement et l&#39;adresse ne fonctionnent pas lorsque la communauté est configurée pour travailler avec le fournisseur de ressources d&#39;Enregistrement de données (DSRP). NPR-26737 : correctif pour CQ-4258493

**Traduction**

* L’exécution automatique de la traduction ne fonctionne pas. NPR-30499 : correctif pour CQ-4276288
* L’utilisateur peut créer une copie de langue dans le chemin d’accès au contenu limité à la lecture seule. NPR-29937 : correctif pour CQ-4270708
* Problème de traduction : seuls quelques composants sont traduits à l’aide de la traduction automatique. NPR-30079 : correctif pour CQ-4273764

**Intégration**

* Le contenu personnalisé ne s’affiche pas correctement sur l’instance de publication tant que l’instance n’a pas été redémarrée. NPR-30421 : correctif pour CQ-4273706

**Projets**

* Les valeurs dam:folderThumbnailPaths ne sont pas actualisées et n’affichent pas les anciennes miniatures, même après la suppression des fichiers dans le dossier. NPR-30424 : correctif pour CQ-4273667

**IU-Consoles**

* Création de scripts intersites (XSS) sur les propriétés de page Sites sous l’onglet Miniature. NPR-30048 : correctif pour Granite-26200

**UI-Foundation**

* Prise en charge Ajoutée du suivi des états de l’interface utilisateur dynamique dans le événement de suivi dans l’API de base. NPR-30742, GRANITE-26322 : Correctif pour GRANITE-26036

**Formulaires**

>[!NOTE]
>
>Le Service Pack AEM n’inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un module complémentaire Forms distinct.  En outre, un programme d’installation cumulatif est publié, qui comprend des correctifs pour AEM Forms on JEE. Pour plus d’informations, voir [Installer le module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installer le programme d’installation AEM Forms JEE](#install-aem-forms-jee-installer).

**Package de modules complémentaires Forms**

**Formulaires adaptatifs**

* La récupération d’un fichier .css vide prend plus de temps à l’éditeur, ce qui entraîne des problèmes de performances. NPR-30558 : correctif pour CQ-4274399
* Les Forms qui sont modifiées après la publication ne sont pas republiées sur la publication du site. NPR-30411 : correctif pour CQ-4236566

**Forms - Intégration du serveur principal**

* Une erreur est générée lors de la création du modèle de données de formulaire avec le langage WSDL (Web Service Definition Language). NPR-30388 : correctif pour CQ-4272921

**Forms - Gestion de correspondance**

* Les caractères spéciaux tels que Inférieur à (&lt;), Supérieur à (>) et Esperluette (&amp;) sont codés dans l’interface utilisateur de l’agent. NPR-30410 : correctif pour CQ-4273887
* Lors du déclenchement d’un fragment de texte contenant des valeurs du dictionnaire de données, l’interface utilisateur de l’agent ne répond plus. NPR-30098, NPR-30083 : correctif pour CQ-4272204
* L’interface utilisateur de création de correspondance échoue par intermittence avec la variable d’erreur (objet Object). NPR-29983 : correctif pour CQ-4273874
* Le rechargement du brouillon de lettre échoue avec une exception lorsque la description des fragments de Document contient des caractères spéciaux tels que Inférieur à (&lt;), Supérieur à (>) et Esperluette (&amp;) dans les propriétés. NPR-29930 : correctif pour CQ-4252762

**Formulaires HTML5**

* Lors de l’utilisation de l’option Accès aux ordinateurs de bureau non visuels en mode Navigation pour lire un formulaire HTML5, le navigateur Chrome affiche &quot;graphic&quot; avant chaque graphique vectoriel évolutif (SVG) dans la conception du formulaire. NPR-30450 : correctif pour CQ-4274732

**Programme d’installation de Forms JEE**

**Forms - Foundation JEE**

* L’Ajoute ou la modification d’une connexion à un service Web en appelant des services Web à partir d’AEM Forms Workbench génère une erreur : ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116 : correctif pour CQ-4273217

**Forms - Document Services**

* Erreur manquante de l’étiquette PDF/A dans le contrôle en amont Acrobat. NPR-30594 : correctif pour CQ-4276032
* Les liaisons de données à caractère unique dans le PDF provoquent l’échec des extensions de Reader avec l’erreur &quot;java.lang.StringIndexOutOfBoundsException: Index de chaîne hors plage : 1&quot;. NPR-30128 : correctif pour CQ-4273878
* Lorsqu’un test de chargement est effectué sur le service HTML en PDF, il échoue avec une erreur et les paramètres de type de fichier sont supprimés du serveur AEM Forms. NPR-30085 : correctif pour CQ-4272631
* L’aplatissement d’un fichier PDF avec Adobe Acrobat 9.1 (XFA version 3.0) ne conserve pas l’état du formulaire PDF : Les éléments invisibles du formulaire sont redéfinis sur un état visible. NPR-29978 : correctif pour CQ-4270888

**Forms - Document Security**

* L’application d’une signature avec horodatage échoue avec l’erreur : ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException : Erreur d&#39;appel. NPR-30696, NPR-30537 : correctif pour CQ-4273778
* Configuration Manager n’insère pas de chaînes japonaises pour les colonnes de table localisées. NPR-30496 : correctif pour CQ-4274868

**Service PDFG**

* Erreur de connexion lors de la tentative de conversion du document Word en PDF sous Windows Server 2016. NPR-30597 : correctif pour CQ-4275652
* Exception refusée lors de l’utilisation du service principal HTML vers PDF via la bibliothèque &quot;phantomjs&quot;. NPR-30456 : correctif pour CQ-4258077
* maxReuseCount pour le service HTML vers PDF n’est pas affiché avec la console de gestion JBoss. NPR-30303, NPR-30135 : correctif pour CQ-4273763

#### aem 6.4.5.0 {#experience-manager-6450}

aem 6.4.5.0 est une mise à jour importante qui comprend des améliorations et des correctifs concernant les performances, la stabilité, la sécurité et les clients clés publiés depuis la disponibilité générale de AEM 6.4 en **avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.5.0 inclut tous les Service Packs AEM 6.4 version antérieure.

Voici quelques-uns des points saillants de l&#39;AEM 6.4.5.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.13.
* Délai d&#39;expiration de socket et de connexion Ajoutés dans les agents de réplication du portail de marque.
* Améliorations d&#39;Omnisearch : Augmentation à 100 pages de la limite de pagination des résultats de la recherche.
* Désactivation du composant `AssetDownloadServlet` OSGi par défaut sur AEM instances de publication. Pour plus d’informations, voir [Téléchargement de ressources à partir d’AEM](/help/assets/download-assets-from-aem.md).
* Activation de la prise en charge du Gestionnaire de sites multiples pour les ressources. Pour plus d’informations, voir [Réutilisation des actifs à l’aide de MSM pour les actifs](/help/assets/reuse-assets-using-msm.md).

**Ressources**

* Les fichiers dont le nom de fichier contient une apostrophe ne sont pas synchronisés avec Dynamic Media. NPR-29538 : correctif pour CQ-4270592
* Mise à jour de l&#39;interface DAM DMGGateway pour la prise en charge multipartie S3. NPR-29740 : correctif pour CQ-4226303
* La boîte de dialogue de téléchargement de fichier affiche une taille de fichier incorrecte lors du téléchargement de rendus pour une vidéo dans Dynamic Media. NPR-29642 : correctif pour CQ-4246202
* Les ressources deviennent inutilisables après que le service DAM DAM DAM Service applique le texte pour m3u8. NPR-29276 : correctif pour CQ-4264052
* L&#39;ajustement de la référence de ressource n&#39;enregistre pas la session si l&#39;une des ressources déplacées/renommées fait partie des collections de ressources Sling. NPR-29143 : Correctif pour /CQ-4252605
* Impossible de suivre ou de trouver des fichiers en recherchant les valeurs de métadonnées. NPR-29141 : correctif pour CQ-4260215
* Lorsque vous utilisez le filtre de recherche pour enregistrer une collection dynamique, l’action de clic du panneau ne conserve pas la cible d’action. NPR-29000 : correctif pour CQ-4240323
* Le déplacement d’un dossier permet la création d’un dossier dont les noms sont en majuscules ou en minuscules. NPR-28945 : correctif pour CQ-4265234
* Les résultats s&#39;affichent dans Omnisearch si le nom de la collection est vide. NPR-29001 : correctif pour CQ-4236729
* Le fait de renommer un fichier à l’aide de caractères spéciaux non pris en charge tels que l’esperluette (&amp;) crée un dossier non valide. NPR-29196 : correctif pour CQ-4265037
* La fonctionnalité DAM Extract Archive for zip file est interrompue. NPR-29187 : correctif pour CQ-4254421
* L’importation de métadonnées doit permettre l’importation de métadonnées sans enregistrer d’espaces de nommage. NPR-29425, NPR-28132 : correctif pour CQ-4269445
* L’enregistrement des modifications de métadonnées ne fonctionne pas pour les fichiers dont le nom contient un guillemet. NPR-29395 : correctif pour CQ-4254305
* Impossible de déplacer un fichier DAM si le nom de fichier contient un espace blanc. NPR-29270 : correctif pour CQ-4266403
* Impossible de télécharger les archives ZIP compressées avec l&#39;algorithme Deflate64. NPR-29225 : correctif pour CQ-4253995
* Les miniatures des ressources s’affichent lentement lors de l’ouverture d’un dossier contenant des ressources de plusieurs versions. NPR-29833 : correctif pour CQ-4271629
* Impossible de saisir la collection mise en surbrillance si la touche Entrée est enfoncée après avoir sélectionné la collection. NPR-29723 : correctif pour CQ-4261607
* Attaque de script intersite (XSS) via la fenêtre d&#39;alerte restreinte. NPR-29671 : correctif pour CQ-4270133
* L’Ajoute des relations aux ressources échoue pour les utilisateurs sans autorisations de suppression. NPR-29640 : correctif pour CQ-4269196
* Après avoir ajouté le titre du fichier dans la page de propriétés, lorsque l’utilisateur tente de fermer la page, AEM ouvre à nouveau la page de propriétés. NPR-29628 : correctif pour CQ-4264929
* La création d’un grand nombre de relations sur un fichier entraîne une erreur. NPR-28779 : correctif pour CQ-4250708
* L’assimilation des ressources est lente en mode d’exécution Scene7 Connect. NPR-28658 : correctif pour CQ-4263007
* Erreur Uncatch TypeError : Impossible de lire la propriété &quot;split&quot; d&#39;undefined s&#39;affiche lors de la tentative de vue des résultats de la recherche. NPR-28803 : correctif pour CQ-4248371
* La réplication de AEM vers Brand Portal est bloquée pendant de longues périodes. NPR-28914 : correctif pour CQ-4254932
* Le déplacement de ressources dans DAM n’entraîne pas un déplacement similaire sur Scene7. NPR-28957 : correctif pour CQ-4264974
* Les mises à jour des métadonnées ne sont pas transmises à IPS si le champ de métadonnées est mis à jour dans AEM. NPR-28961 : correctif pour CQ-4255393
* VersioningTimelineEventProvider doit fournir la version racine avec le commentaire de la version. Correctif pour GRANITE-26063
* L’injection de données conduit à l’exécution du code côté serveur. Correctif pour CQ-4270246
* Activation de la prise en charge du Gestionnaire de sites multiples pour les ressources. Correctif pour CQ-4271453, CQ-4268621, CQ-4257491
* L’interface AEM doit afficher une entrée supplémentaire pour la version actuelle de la ressource dans la chronologie, affichant le dernier commentaire d’arrivée à partir d’Adobe Asset Link. Correctif pour CQ-4262864
* L’exemple de vidéo ne se charge pas lors de la création ou de la modification d’une visionneuse de supports variés. Correctif pour CQ-4244889
* La désactivation des autorisations de suppression de contenu du côté AEM empêche l’utilisateur de publier sur le portail des marques. Correctif pour CQ-4270426
* Problèmes liés à la limite de requête avec les rapports sur les actifs après la mise à niveau vers AEM 6.4.3. NPR-28588 : Correctif pour CQ-4262022, CQ-4260697
* La fonctionnalité de téléchargement exploite AEM Assets par le biais de la servlet de téléchargement de ressources, ce qui permet aux utilisateurs anonymes de télécharger tous les fichiers. NPR-27315, Correctif pour CQ-4254732

**Sites**

* Le nom de la balise de plainte JCR doit être renseigné automatiquement en fonction du titre de la balise. NPR-28990 : correctif pour CQ-4199411
* Le bouton Annuler l’héritage n’est pas visible sur certains des champs ajoutés dans les propriétés de la page. NPR-29079 : correctif pour CQ-4265686
* L&#39;action de prévisualisation de déploiement ne doit pas tenter de recréer la copie dynamique ni de l&#39;afficher dans la liste des pages de déploiement. NPR-29151 : correctif pour CQ-4266213
* (Éditeur de modèle) Régression de stratégie de style en mode structure. NPR-28981 : correctif pour CQ-4264400
* Les copies dynamiques imbriquées affichent les entrées de duplicata pendant le déploiement. NPR-29300 : correctif pour CQ-4268664
* La publication d’une Live Copy d’une Live Copy contenant un composant d’importateur de conception échoue avec l’échec de récupération des références pour la page sélectionnée. NPR-28944 : correctif pour CQ-4265014
* CoralUI, lorsqu’il est utilisé avec Multifield, stocke le paramètre fileReferenceParameter au niveau du composant et non au niveau de plusieurs champs. NPR-29536 : correctif pour CQ-4266129
* La référence de conception n’est pas répliquée lors de la publication après l’annulation de l’héritage sur Design Importer. NPR-29648, NPR-29721 : correctif pour CQ-4269270, CQ-4271087
* Le champ de chemin dans l’éditeur de texte enrichi s’ouvre à la racine, quel que soit le chemin spécifié pour la recherche. NPR-29483 : correctif pour CQ-4268997
* (IE11) Copiez coller le contenu HTML dans un composant RTE avec defaultPasteMode = texte brut ne colle pas le contenu en tant que texte brut. NPR-29432, NPR-29171 : Correctif pour GRANITE-24941
* La vérification orthographique de l’éditeur de texte enrichi ne fonctionne plus dans d’autres langues. NPR-29506 : correctif pour CQ-4264990
* Création de scripts intersites (XSS) sur la page Campaign. NPR-29614 : correctif pour CQ-4269322
* La réduction de l’éditeur de texte enrichi à partir du mode plein écran en mode modification de la source entraîne une perte de contenu. NPR-29574 : correctif pour CQ-4260584
* (IU classique) Il n’est pas toujours possible de naviguer jusqu’au dernier onglet lorsqu’il existe un grand nombre de balises. NPR-29544 : correctif pour CQ-4264548
* (IU classique) Le menu de navigation du Admin Console disparaît et la page ne se charge pas complètement. NPR-29571 : correctif pour CQ-4264585
* Une alerte d’erreur est générée lors de l’ajout de composants à la page WCM lorsque la minification est activée sur l’instance. NPR-29396 : correctif pour CQ-4266196
* Problème d’héritage des noeuds Style System du parent. NPR-29296 : correctif pour CQ-4266041
* La page restaurée avec la distorsion du temps doit faire référence à l’image correcte au moment du contrôle de version.  NPR-29431 : correctif pour CQ-4262638
* Page vierge contenant des erreurs JavaScript dans l’éditeur après l’installation de la dernière version d’instantané 6.4.5. NPR-29475 : correctif pour CQ-4266196
* Lors de l’ajout d’un composant à un parsys, la propriété de liste du composant de conception n’est pas respectée et est résolue sur un autre nom de noeud de modèle avec une structure parsys similaire. NPR-29509 : correctif pour CQ-4269044
* la zone cq:dropTargets couvre l’ensemble du composant au lieu de la taille de l’image, rendant le ciblage difficile avec les composants incorporés. NPR-29738 : correctif pour CQ-4268912
* Le composant d’image n’appelle pas l’écouteur &quot;after edit&quot; après l’utilisation de l’éditeur d’images en place. Correctif NPR-29616 pour CQ-4268065
* Problème lors de la configuration de la publication sur Facebook. NPR-29212 : correctif pour CQ-4266630
* Lors de la promotion du lancement des pages modifiées, les modifications des branches source et de lancement sont prises en compte. NPR-29308 : correctif pour CQ-4266746
* La miniature générée sur le fragment de contenu affiche une représentation de calendrier interne pour les champs Date et Heure. NPR-29531 : correctif pour CQ-4269362
* Impossible d&#39;ajouter en bloc une balise aux pages contenant des balises différentes existantes. NPR-28729 : correctif pour CQ-4262922
* L&#39;icône Activation planifiée ne s&#39;affiche pas dans l&#39;administrateur du site. NPR-28725 : correctif pour CQ-4263917

**Réplication**

* Vulnérabilité de divulgation d&#39;informations sensibles dans le composant Agent de réplication. NPR-29612, NPR-24951 : Correctif pour GRANITE-25070
* Les données fournies par l’utilisateur ne sont pas ignorées lors de la sortie dans le composant cq/Replication/components/agent, ce qui entraîne une vulnérabilité Cross-site scripting (XSS) par stockage. Correctif pour CQ-4266263

**Fragments d’expérience**

* Impossible d’exporter les fragments d’expérience vers la cible lorsque une image dynamique est utilisée. Correctif pour CQ-4269606

**Social - Rapports**

* aem rapports de la communauté ne s’affichent pas dans AEM instance d’auteur. Correctif pour CQ-4266294

**Plate-forme**

* XSS (Cross-site scripting) dans le gestionnaire de packages lors de l’installation d’un package. NPR-29734, NPR-29713, NPR-29630 : Correctif pour GRANITE-26161, GRANITE-
* Plusieurs scripts XSS (Cross-site scripting) stockés et réfléchis dans le CRXDE Lite. NPR-29634 : correctif pour GRANITE-26049
* La fonctionnalité de connexion pour Package Share utilise la requête de GET plutôt que la requête de POST, ce qui rend le mot de passe visible sous l’onglet réseau. NPR-29631 : correctif pour GRANITE-26048

**Felix**

* Script intersite (XSS) observé dans la console système. La page est chargée et s’affiche lorsque le pointeur de la souris survole le champ de texte. NPR-29853, NPR-29633 : Correctif pour GRANITE-26188, GRANITE-26050

**Granite**

* La configuration du journal de journalisation Apache Sling ne filtre pas le script injecté.  NPR-29775 : correctif pour GRANITE-26051

**Communautés**

* Les groupes supprimés sur l’auteur doivent être supprimés des instances de publication. NPR-28933 : correctif pour CQ-4264645
* Le secret de l’application doit être protégé par un champ de mot de passe et non pas affiché en texte brut pour les outils de connexion sociale. NPR-29728 : correctif pour CQ-4270480
* Les visiteurs et les membres, sans privilège de modérateur, peuvent afficher les publications non approuvées/en attente en collant l’URL. NPR-29726 : correctif pour CQ-4271124, CQ-4271441
* Un temps de réponse élevé allant jusqu’à 40-50 secondes est observé lors de la connexion de l’utilisateur à la Communauté. NPR-29678 : correctif pour CQ-4269444

**Traduction**

* Les utilisateurs qui n’ont pas accès à la fonction de traduction dans la navigation ne doivent pas pouvoir accéder à ses sous-pages. NPR-29644 : correctif pour CQ-4269979
* Les autorisations d’utilisateur non confirmées en tant qu’assistant permettent la création de la copie de traduction dans un emplacement en lecture seule. NPR-29375 : correctif pour CQ-4265877

**IU - Fondation**

* Augmentation de la limite de pagination du résultat de la recherche à 100 pages pour la vue de cartes et à 200 pages pour la vue de listes. NPR-29332 : correctif pour GRANITE-24644
* En raison du chargement différé des balises, rien ne s’affiche sur la page de collecte. NPR-29267 : correctif pour GRANITE-24902
* La modification de la limite de pagination à 100 au lieu de 40 déclenche un chargement différé supplémentaire sans demande de pagination. NPR-29246 : correctif pour GRANITE-25027
* aem champ de mot de passe granite n&#39;est pas renseigné après le chiffrement. NPR-29245 : correctif pour GRANITE-24908

**Intégration**

* Un message d’exception s’affiche lorsque vous tentez de modifier et d’enregistrer la configuration de lancement AEM. NPR-29086 : correctif pour CQ-4266153
* Échec des informations d’identification BrightEdge en cas d’erreur de connexion.  NPR-29167 : correctif pour CQ-4265872
* La case héritée de la case à cocher apparaissant au niveau racine dans les configurations Cloud Service doit être supprimée. NPR-27856 : correctif pour CQ-4259676

**Sling**

* Le délai d&#39;expiration de la connexion HTTP n&#39;est pas lu à partir des configurations. NPR-29264 : correctif pour SLING-7902
* L’écriture différée du programme d’installation JCR entraîne l’utilisation d’un format non valide par la configuration OSGi et bloque le redéploiement. NPR-29027 : correctif pour CQ-4264694

**Projets**

* Les utilisateurs ne peuvent pas terminer le processus du projet. NPR-29621 : correctif pour CQ-4258791
* La liste de processus du projet affiche des lignes vides au-delà de 40 workflows. NPR-28739 : correctif pour CQ-4264005
* Si vous sélectionnez l’option Rendu dynamique dans le portail de marque, un fichier .zip vide est téléchargé. NPR-29420 : correctif pour CQ-4268826
* La publication des ressources du dossier /content/dam/mac d’AEM Author vers Brand Portal ne fonctionne pas. NPR-29820 : correctif pour CQ-4271118
* La ponctuation dans le nom provoque des problèmes avec le bouton de publication. NPR-29573 : correctif pour CQ-4269317
* Impossible de créer une copie de langue de ressource via le panneau de référence. Correctif pour CQ-4269535

**Processus**

* La mise à niveau de 6.4.2 à 6.4.4 rompt le champ du sélecteur de calendrier du participant à la boîte de dialogue. NPR-29727 : correctif pour CQ-4270423

**WCM - Interface utilisateur d’administration**

* L&#39;ouverture de l&#39;onglet des autorisations dans l&#39;implémentation Coral2 n&#39;affiche pas les boutons. Correctif pour CQ-4269419

**WCM - MSM**

* La suppression d’un nœud enfant dans la Live Copy doit détacher les informations liveRelationship. Correctif pour CQ-4270395
* La mise à niveau vers AEM 6.4.3 fait que le déploiement de Multi-Site Manager prend du temps. Correctif pour CQ-4271410

**Vulnérabilité**

* La structure de protection CSRF ne fonctionne pas avec les formulaires AEM Foundation. NPR-28612 : correctif pour GRANITE-22231

**WCM - Éditeur de page**

* Les scripts intersites (XSS) se reflètent lors de l’utilisation d’un sélecteur non valide. Correctif pour CQ-4270397

**Formulaires**

Les principaux points forts d&#39;AEM Forms 6.4.5.0 sont les suivants :

**Package de modules complémentaires Forms**

**Formulaires adaptatifs**

* (Interface utilisateur tactile) L’option de flux de travaux de Début n’affiche pas la boîte de dialogue de configuration. NPR-29521 : correctif pour CQ-4269050

**Forms - Intégration du serveur principal**

* Activation de la prise en charge d’Active Directory Federation Services (ADFS) v3.0 pour l’intégration sur site de Microsoft Dynamics. NPR-30003, NPR-29484 : correctif pour CQ-4270586
* Le service de préremplissage échoue en raison d’un délai de réponse prolongé du module d’intégration des données AEM Forms. NPR-28997 : correctif pour CQ-4265988
* La demande de service Web SOAP est incorrecte dans AEM Forms. NPR-29013 : correctif pour CQ-4265443
* Aucun message d’erreur ne s’affiche lors du test du service SOAP, en cas de valeur de date incorrecte. Correctif pour CQ-4265445

**Forms - Communication interactive et Forms - Correspondence Management**

* L’interface utilisateur de création de correspondance (interface utilisateur CCR) ne parvient pas à gérer un nombre à virgule flottante.  NPR-29210 : correctif pour CQ-4254201
* L’info-bulle définie sur une variable n’est pas visible dans l’interface utilisateur de création de correspondance (IU CCR). NPR-29739 : correctif pour CQ-4250533
* Impossible de copier ou coller à partir d&#39;Omnisearch dans des lettres. NPR-29808 : correctif pour CQ-4270783

**Formulaires HTML5**

* Lorsque nous ajoutons un espace dans le texte, le champ de texte ne permet pas de le remplir jusqu’à la fin. NPR-28844 : correctif pour CQ-4260239

**Programme d’installation de Forms JEE**

**Forms - Foundation JEE**

* Le composant Webservice d’AEM Forms Workbench ne peut pas appeler un service Web, ce qui nécessite une authentification SSL bidirectionnelle. NPR-29485 : correctif pour CQ-4246794
* Le gestionnaire de configuration AEM Forms JEE ne fonctionne pas avec plusieurs cartes d’interface réseau. NPR-29236 : correctif pour CQ-4268598
* aem erreur de démarrage provenant de GemFire : java.lang.IllegalStateException : Une seule connexion AdminDistributedSystem peut être établie en même temps. NPR-29524 : correctif pour CQ-4266295
* NoClassDefFoundError en raison d&#39;une incompatibilité de version de jar. NPR-28834 : correctif pour NPR-28834

**Forms - Services Documents**

* Un fichier PDF/A non valide est signalé comme PDF/A valide à l’aide de l’opération isPDFA. NPR-29076 : correctif pour CQ-4261541
* La conversion du fichier PDF en PDF/A-1b avec le champ de formulaire n’a pas de code d’apparence. NPR-29534 : correctif pour CQ-4269618
* La conversion PDF/A à partir d’un fichier PDF produit avec Output Service ne réussit pas la validation avec Acrobat DC. NPR-29647 : correctif pour CQ-4270448
* Le lot Apache POI échoue avec une exception. NPR-27861, NPR-28048 : correctif pour CQ-4245898, CQ-4244778

**Forms - Designer**

* Prise en charge PDF/UA Ajoutée des formulaires XFA (XML Forms Architecture) générés à l’aide de Designer et Output Service. NPR-23022

**Forms - Workflow**

* Les envois à partir de l&#39;espace de travail échouent avec le caractère Umlaut. NPR-29087 : correctif pour CQ-4263172

**Packs de fonctionnalités inclus**

**Ressources**

* Activation de la prise en charge du Gestionnaire de sites multiples pour les ressources. Pour plus d’informations, voir [Réutilisation des actifs à l’aide de MSM pour les actifs](/help/assets/reuse-assets-using-msm.md). NPR-26450 : correctif pour CQ-4259922

**bundles OSGI et packages de contenu inclus**

Le texte suivant documents la liste des lots OSGI et des packages de contenu inclus dans le CFP.

Liste des lots OSGi inclus dans AEM 6.4.5.0

[Obtenir le fichier](assets/6.4.5.0_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.5.0

[Obtenir le fichier](assets/6.4.5.0_OSGI.txt)

#### aem 6.4.4.0 {#experience-manager-6440}

aem 6.4.4.0 est une mise à jour importante qui comprend des améliorations et des correctifs concernant les performances, la stabilité, la sécurité et les clients clés publiés depuis la publication de AEM 6.4 en **avril 2018.**

Il est également cumulatif, ce qui signifie que la version 6.4.4.0 inclut tous les Service Packs AEM 6.4 version antérieure.

Voici quelques-uns des points saillants de l&#39;AEM 6.4.4.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.11.
* Prise en charge Ajoutée de la version du service de mise en cache pour éviter les demandes HTTP fréquentes de version de service.
* Prise en charge Ajoutée de la suppression des balises automatiques.
* Mise en oeuvre du défilement sans fin pour l’assistant de catalogue.
* Capacité refusée de restreindre les autorisations en fonction des sites de la communauté.
* Correctifs de performances (mise en cache, exécution asynchrone, liste d’exclusion) pour Sling Granite Content Health Check.
* Bouton de sélection de ressources Ajouté vers la boîte de dialogue de miniature de page.
* Nouvelle propriété Ajoutée pour autoriser le positionnement des info-bulles dans les champs.
* Amélioration de la prise en charge du sélecteur de couleurs dans le champ Multichamp.
* Ajouté une vérification pour ignorer les valeurs vides pour les champs multiples d’entrée numérique dans les clientlibs du fragment de contenu.
* Prise en charge de l’API de texte Microsoft Translator v3 activée.

**Ressources**

* Migration de l&#39;intégration ACP et stock vers AEM 6.4.4.0 NPR-27632
* La publication ultérieure d’un dossier de ressources vide contenant des sous-dossiers entraîne la disparition des sous-dossiers. NPR-27558 : correctif pour CQ-4254701
* L&#39;ajout de la propriété Chaîne unique non espacée de noms\[\] entraîne une écriture différée XMP incomplète. NPR-26805 : correctif pour CQ-4254142
* Après avoir pixellisé le fichier pdf d’entrée, les images manquantes apparaissent dans la sortie. NPR-27929 : correctif pour CTG-4150481
* L’Assistant Déplacement de ressources affiche un nombre incorrect de pages de référencement pour les pages publiées. NPR-27833 : correctif pour CQ-4258014
* AssetPicker recherche uniquement la première balise pour filtrer le résultat lors du filtrage avec des balises. NPR-27778 : correctif pour CQ-4257705
* aem gestionnaire PDF prêtes à l’emploi se bloque lors du traitement du PDF avec des caractères étrangers. NPR-28778 : correctif pour CQ-4254234
* Lorsqu’un fichier CSV comporte une valeur séparée par des virgules dans une seule colonne, AEM éditeur CSV n’échappe pas la virgule et la traite comme une colonne distincte. NPR-28801 : correctif pour CQ-4261694
* Problème avec l’éditeur de Schéma de métadonnées lors de l’utilisation du navigateur de chemins pour sélectionner des données. NPR-28674 : correctif pour CQ-4263005
* Trop de ressources sont traitées dans Smart Content Service, ce qui se traduit par un temps considérable pour terminer le processus de balisage périodique. NPR-28640 : correctif pour CQ-4262661, CQ-4262644, CQ-4263234
* Les actions de bureau ne fonctionnent pas pour les résultats d&#39;Omnisearch à partir de la page `aem/start.html`. NPR-27242 : correctif pour CQ-4248176
* L’API Ressources n’autorise pas le téléchargement de fichier > 2 Go, ce qui entraîne l’échec du téléchargement. NPR-27629 : correctif pour Granite-23590
* Les métadonnées ne sont pas enregistrées dans le fichier téléchargé lors de la première tentative au cas où Dynamic Media serait activé sur l’instance. NPR-28233 : correctif pour CQ-4260759
* Le résolveur de service n&#39;est pas fermé dans la configuration du SiteCatalyst. NPR-28015 : correctif pour CQ-4259397
* Le déplacement de ressources dans DAM n’entraîne pas un déplacement similaire sur Scene7 (configuration p2p). NPR-28313 : correctif pour CQ-4261091

**Sites**

* (IU classique) Une fraction des copies dynamiques s’affiche dans la liste de déploiement. NPR-28598, NPR-28574 : correctif pour CQ-4263410
* LiveRelationshipManagerImpl renvoie des exceptions lorsque cq:master est vide ou non valide. NPR-28590 : correctif pour CQ-4263115
* Le flux de travaux &quot;Demande de suppression&quot; prêt à l&#39;emploi ne supprime pas correctement les pages. NPR-28668 : correctif pour CQ-4263195
* L’interface utilisateur État de la relation n’affiche pas les valeurs d’année ou d’horodatage appropriées pour les champs coral-datepicker associés. NPR-28666 : correctif pour CQ-4263661
* Cross-site scripting (XSS) dans SuggestionHandler pour la version 6.4. NPR-28693 : correctif pour CQ-4253821
* Déplacer le dossier du site admin se termine en mémoire insuffisante et rend AEM indisponible. NPR-28346 : correctif pour CQ-4261398
* Les configurations de déploiement MSM LiveCopy sont perdues après la mise à jour. NPR-28311 : correctif pour CQ-4258705
* Impossible de faire défiler plus de 40 configurations de plan. NPR-27640 : correctif pour CQ-4239166
* L&#39;utilisation de SyntheticResource comme référence renvoie une exception Null Pointer et bloque le déplacement des pages.  NPR-27576 : correctif pour CQ-4258262
* PushOnModify ne fonctionne pas sur la suppression sur l&#39;instance mise à niveau 6.1 à 6.4. NPR-28108 : correctif pour CQ-4259833
* (IU classique) Le bouton Annuler l’héritage est manquant et le composant peut être modifié sur une page de copie dynamique. NPR-28256 : correctif pour CQ-4260161
* OakState0001 : Conflits non résolus lors du déploiement. NPR-27982 : correctif pour CQ-4259548
* Lorsque vous copiez/collez une structure contenant des références SyntheticResource, le processus se termine par une erreur 500. NPR-27709 : correctif pour CQ-4259179
* Impossible d&#39;arrêter les workflows en cours d&#39;exécution lorsque les charges sont activées. NPR-27672 : correctif pour CQ-4258520
* Le déploiement montre les chemins de déploiement du duplicata après la mise à niveau de la version 6.1 à la version 6.4. NPR-27845 : Correctif pour CQ-4259487
* Intégrez le module de sélecteur de ressources de barrage dans le composant de miniature de page. NPR-28131 : correctif pour CQ-108042
* (IU classique) Impossible d&#39;ouvrir les boîtes de dialogue avec le widget Balises. NPR-28575 : correctif pour CQ-4262680
* Le téléchargement de fichiers multichamps n’affiche pas de zone de dépôt. NPR-28676 : correctif pour CQ-4263516
* Erreur de &quot;valeur de sélecteur de récursion non valide&quot; lors de la migration d&#39;un composant de AEM 6.0 à AEM 6.2. NPR-28609 : Correctif pour CQ-4241258
* L’Editeur de texte enrichi dans la boîte de dialogue clignote lorsque la superposition d’un module externe est supérieure à la zone de texte, ce qui bloque toute création ultérieure. NPR-27579 : correctif pour CQ-4257440
* (IU classique) l’éditeur cq:action ne fonctionne pas. NPR-28232 : correctif pour CQ-4257703
* Le fait de supprimer des balises du panneau de recherche de ressources du filtre de balises de l’éditeur de page n’actualise pas correctement la liste. NPR-27983 : correctif pour CQ-4245567
* Si les valeurs numériques de champs multiples sont vides, le fait de cliquer sur Enregistrer génère une invite de chargement infinie sans jamais terminer.  NPR-28400, NPR-28393 : correctif pour CQ-4244058, CQ-4244349
* Avec l’autorisation de lecture, les utilisateurs/groupes ne peuvent pas sélectionner de XF et n’ont pas d’option pour vue du XF et de ses propriétés de page. NPR-28341 : correctif pour CQ-4260412
* Les données JSON reçues de la Cible comportent plusieurs caractères d’échappement qui provoquent le saut de page de l’application. NPR-28318 : correctif pour CQ-4252043
* Impossible de modifier un composant après avoir installé AEM 6.4.3. NPR-28125 : Correctif pour CQ-4261216
* La suppression de toutes les balises d’un champ de balise n’est pas conservée pour un fragment de contenu structuré. NPR-28133 : correctif pour CQ-4247241
* Lors de la modification d’une propriété de fragment de contenu &quot;jcr:lastModiedby&quot; et &quot;jcr:lastchanged&quot;, les valeurs sont mises à jour sans que l’utilisateur n’apporte de modifications. NPR-27847 : correctif pour CQ-4257138
* Le contrôle de version des fragments de contenu compare les différentes améliorations pour AEM 6.4. NPR-27764
* S’il n’existe pas de modèles cq:allowedTemplates définis sur /content/experience-fragments et que les chemins d’accès autorisés sont utilisés sur le modèle de gestion de l’expérience, une erreur est générée lorsque la gestion de l’expérience est déplacée/copiée. NPR-27487 : correctif pour CQ-4257489
* Le bouton Créer s’affiche lors de l’actualisation pour le nouvel utilisateur. NPR-27335 : correctif pour CQ-4255360
* Lors de la tentative de déplacement d’une page publiée, le nombre de &quot;Pages de référence&quot; qui s’affiche sur la première page de l’assistant &quot;Déplacer la page&quot; est incorrect. NPR-28111 : correctif pour CQ-4259663
* (Interface utilisateur tactile) Références Le rail n’affiche pas les liens entrants. NPR-28529 : correctif pour CQ-4262306
* Impossible de modifier les composants et les propriétés de page après l&#39;installation de AEM 6.4.3. NPR-27998 : Correctif pour CQ-4261216, CQ-4260441
* Migrez contextub vers jquery 3. NPR-28397 : correctif pour GRANITE-19902

**Commerce**

* Impossible de sélectionner le catalogue s&#39;il y a plus de 20 catalogues dans un dossier. NPR-27649 : correctif pour CQ-4258119
* Les assistants commerciaux et les vues de propriétés sont rompus en raison de l’absence de header.referer. Correctif pour CQ-4261122

**Campaign - Ciblage**

* com.day.cq.personalization.impl.TeaserResourceEventHandler se trouve dans une boucle infinie et entraîne des mises à jour des noeuds sur les instances de publication. Correctif pour CQ-4263096

**Réplication**

* Erreur lors de la création du contenu de réplication com.day.cq.replication.AccessDeniedException. NPR-28314 : correctif pour CQ-4261401
* Fuite de session lorsque l&#39;ID d&#39;agent utilisateur est défini sur admin dans l&#39;agent de réplication. NPR-28220 : correctif pour CQ-4255517

**DAM - Creative Cloud**

* Exportez l’API HTTP pour rechercher des images similaires dans AEM Assets. Correctif pour CQ-4254091
* Améliorez l&#39;API ACP pour autoriser la restriction des résultats d&#39;une requête aux membres d&#39;une collection. Correctif pour CQ-4258708

**DAM - Formats**

* Une fois l’exportation des métadonnées déclenchée, la page est redirigée vers une page 404. Correctif pour CQ-4262447

**DAM - Général**

* (Intégration Adobe Stock) Le modal d’erreur du serveur s’affiche avec une erreur Oauth dans le fichier error.log. Correctif pour CQ-4260406
* L’intégration Adobe Stock ne fonctionne pas si la version 6.4.4 est appliquée à la version 6.4.3. Correctif pour CQ-4266009
* Le lien vers le modèle CF est manquant même après l&#39;application du correctif SP3. Correctif pour CQ-4259029

**Plate-forme**

* (IU classique) Le bouton Modifier n&#39;est pas disponible dans le composant Rapport de base après la mise à niveau vers la version 6.4.2. NPR-28560 : Correctif pour CQ-4262825
* Lorsque vous utilisez une requête combinant property.operation=like et property.depth, elle se retrouve dans une InvalidQueryException. NPR-28570 : correctif pour CQ-4262652
* Erreur interne du serveur lorsque le nouveau noeud de langue ajouté est supprimé du noeud de langue superposé. NPR-28661 : correctif pour CQ-4239194
* Exception de pointeur nul dans stderr.log dans le thread sling-oak-1 sur des débuts aléatoires. NPR-28665 : correctif pour CQ-4237845

**Félix**

* webconsole.plugins.memyusage provoque un blocage lors de l’actualisation. NPR-27895 : correctif pour GRANITE-20715

**Granite**

* Sling Content Access Health Check effectue une longue validation /libs excessive pour le chemin de recherche du résolveur de ressources personnalisé. NPR-28113 : correctif pour GRANITE-23529

**Gestion des fragments de contenu**

* Améliorations de la convivialité et parité des fonctionnalités avec les ressources pour les fragments de contenu. Correctif pour CQ-4253883

**Communautés**

* Mettez à niveau les bibliothèques d&#39;amorçage vulnérables vers la version 3.4 et les bibliothèques ckeditor vers la version 4.5.11. NPR-28490 : Correctif pour CQ-4257511
* L&#39;annulation des modes de modification ne rétablit pas la pièce jointe supprimée. NPR-27902 : correctif pour CQ-4255150
* La composition au nom de la boîte ne doit être visible que pour les membres privilégiés. NPR-27900 : correctif pour CQ-4251235
* Ajoutez rep:cache dans Noeuds ignorables dans le module d’écoute AEM Communities User Sync sur les instances de publication. NPR-27842 : correctif pour CQ-4247234
* La zone de recherche affiche un caractère d’échappement au niveau de l’interface utilisateur. NPR-27838 : correctif pour CQ-4259757
* Une erreur est générée lors de la recherche de caractères spéciaux tels que ( , +, ? dans quicksearch. NPR-28213 : correctif pour CQ-4260969
* Créez un groupe &quot;administrateurs spécifiques à la communauté&quot; pour que les utilisateurs puissent modifier et créer le site communautaire approprié. NPR-27731
* Logique Ajoutée pour le événement clavier permettant d’ouvrir la vidéo. NPR-27726 : correctif pour CQ-4254026
* Activation de la navigation au clavier pour les composants d’activation d’AEM Communities lors de la publication. NPR-27728 : correctif pour CQ-4254028
* Libellé aria Ajouté pour le bouton liste et vue de carte. NPR-27727 : correctif pour CQ-4254027
* Gestion des sessions de résolution de ressources ouvertes dans les communautés de réseaux sociaux. NPR-27721 : correctif pour CQ-4258714

**Traduction**

* Prise en charge de Microsoft Translator Text API v3. NPR-28366 : correctif pour CQ-4249755
* jcr:language &amp; cq:language ne sont pas automatiquement mis à jour dans la langue traduite. NPR-28338 : correctif pour CQ-4256046
* Les références cycliques provoquent StackOverflowError lors de la création d’une copie de langue. NPR-27596 : correctif pour CQ-4255621
* Dans un projet de traduction multilingue, cliquer sur Enregistrer et fermer les résultats dans les pages suivantes ajoutées au projet entraîne la création de nouveaux projets au lieu de la création de nouvelles tâches de traduction dans le projet existant. NPR-28219, NPR-28236 : correctif pour CQ-4261276, CQ-4260731
* Chaîne d’erreur trop longue lors de l’ajout d’un fragment de contenu avec des données en vrac en raison de la limitation du nombre de caractères autorisés. NPR-28722 : correctif pour CQ-4262362

**Social**

* Le commentaire publié sur la page suivante est surligné en jaune chaque fois qu’un nouveau commentaire est publié. Correctif pour CQ-4261359
* Impossible de supprimer les commentaires dans le contenu créé par l’utilisateur à l’aide de l’API. NPR-28075 : correctif pour CQ-4261135
* AbstractNotificationOperationService cause ClassCastException. Correctif pour CQ-4260456
* Supprimez la référence au cloud SCORM (Shareable Content Object Reference Model) dans le lecteur. Correctif pour CQ-4260779

**IU - Fondation**

* La fonction &quot;cache de sortie du système de fichiers&quot; intégrée dans le Gestionnaire de bibliothèque client HTML rompt la fonction &quot;debugClientLibs&quot; pour les scripts compilés tels que LESS files. NPR-27249 : correctif pour Granite-23313
* Le nombre de fichiers affichés lorsque le mode de débogage est activé est toujours égal à 1 et de nombreuses erreurs JS sont générées dans la console du navigateur.  NPR-27575 : correctif pour GRANITE-23750
* Enregistrer et fermer sur les propriétés de la page ne revient pas à la page appropriée dans AEM WAR avec Tomcat. NPR-27566 : correctif pour GRANITE-23671

**Intégration**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` résulte en une boucle infinie et provoque des mises à jour des nœuds lors de la publication. NPR-28561 : correctif pour CQ-4263096
* Les actions cq:actions ne sont pas prises en compte pour un composant ciblé. NPR-27616 : correctif pour CQ-4257497
* L’annulation de l’héritage de LiveCopy ne fonctionne pas correctement sur les conteneurs ciblés. NPR-28129 : correctif pour CQ-4259813
* (Configurations du Cloud Service) La case &quot;hérité de&quot; qui s’affiche au niveau racine doit être supprimée. NPR-27856 : correctif pour CQ-4259676

**Sling**

* Mise à jour de l’API Sling Models 1.3.8, Impl 1.4.10. NPR-27636 : Correctif pour GRANITE-23537

**OAK - Persistance des segments**

* SegmentBufferWriter n&#39;a pas été vidé après OnRC. NPR-27464

**Projets**

* Le projet de traduction multilingue ne crée pas plusieurs tâches linguistiques pour les utilisateurs qui ne font pas partie du groupe d’administrateurs. NPR-28508 : correctif pour CQ-4262023
* Le servlet ProjectTaskListServlet fuit un ResourceResolver chaque fois que getTaskRenderers est appelé au démarrage du service. NPR-27590 : correctif pour CQ-4258011
* Si un répertoire comporte plus de sous-répertoires que la taille et l’ordre de la page sont par date ou par taille, une erreur empêche le déplacement au-delà de la première page. NPR-28867 : correctif pour CQ-4265039
* Résolution des problèmes de scripts intersites (XSS) dans les visionneuses de gestion des actifs numériques. NPR-28106 : correctif pour CQ-4253215
* Impossible d&#39;ajouter des pages au projet de traduction par les administrateurs de projet, car le lien permettant d&#39;ajouter de nouvelles pages au projet de traduction n&#39;est pas visible. Correctif pour CQ-4266334

**Processus**

* Lorsque nous ouvrons la boîte de dialogue complète de la tâche dans la notification de flux de travail qui comporte un champ Balise, un clic sur une coche lui ajoute une propriété Balise. NPR-28304 : correctif pour CQ-4261321
* Le bouton bascule Sélection utilisateur de la boîte de dialogue Réaffecter la Tâche ne fonctionne pas. NPR-28963 : correctif pour CQ-4264206

**Formulaires**

Les principaux points forts d&#39;AEM Forms 6.4.4.0 sont les suivants :

* Prise en charge Ajoutée de l&#39;enregistrement des API de sécurité des documents pour la signature et la certification en tant que transactions.

**Package de modules complémentaires Forms**

**Intégration d’Adobe Sign**

* aem 6.4 Forms Client SDK ne contient pas de package adobésité-recipent. NPR-27735 : correctif pour CQ-4259372

**Formulaires adaptatifs**

* Lorsque le formulaire adaptatif Wan est créé avec un modèle vide, les clients ne peuvent pas accéder aux panneaux enfants du panneau racine du formulaire. NPR-28758 : correctif pour CQ-4264157
* Lorsque la valeur du composant de champ de date année est 9999, le script de validation échoue. NPR-28580 : correctif pour CQ-4262620
* Lorsqu’un formulaire adaptatif est créé avec un modèle vide, les clients ne peuvent pas accéder aux panneaux enfants du panneau racine du formulaire. NPR-28758 : correctif pour CQ-4264157
* Impossible de définir la valeur entre les champs des fragments chargés différés d&#39;un formulaire adaptatif. NPR-27758 : correctif pour CQ-4259703
* Le formulaire adaptatif n’utilise pas l’éditeur de texte enrichi, mais charge ses bibliothèques.  NPR-27759 : correctif pour CQ-4259193
* La redirection vers l’URL ne fonctionne pas pour les formulaires adaptatifs incorporés dans une page AEM Sites. NPR-27620 : correctif pour CQ-4239287
* Impossible de définir la valeur entre les champs des fragments chargés différés d&#39;un formulaire adaptatif. NPR-28320 : correctif pour CQ-4262345
* Le formulaire adaptatif n’utilise pas l’éditeur de texte enrichi, mais charge ses bibliothèques.  NPR-28001 : correctif pour CQ-4259703, CQ-4259193
* La signature tactile ne fonctionne pas pour l’application AEM Forms s’exécutant sur Apple iOS 12.1. NPR-28497 : Correctif pour CQ-4261765
* Action d’envoi à l’aide de problèmes de création classique &quot;Forms Workflow&quot; dans la version 6.4. Correctif pour CQ-4252740
* Erreur lors de la gestion de la suppression du bloc et de l&#39;enregistrement tmp. NPR-28806 : correctif pour CQ-4264441

**Forms - Gestion de correspondance**

* L&#39;interface utilisateur de l&#39;agent ne parvient pas à conserver la taille d&#39;origine de l&#39;image. NPR-28800 : correctif pour CQ-4259767
* Interface utilisateur CCR/Agent : Les étiquettes des champs Date ont été décalées dans l’onglet Données. Correctif pour CQ-4255499

**Forms - Rapports des transactions**

* Prise en charge Ajoutée de la comptabilisation à l’aide de signatures numériques ou de la certification d’un document en tant que transactions facturables. NPR-28495 : correctif pour CQ-4260236
* Signature numérique Ajoutée et API de certification vers facturable. Correctif pour CQ-4260236

**Gestion des Forms**

Prise en charge Ajoutée pour remplacer l’utilisation de la bibliothèque cliente des barres de poignées par un trait de soulignement dans l’assistant de révision des débuts de Forms Manager et l’assistant de déplacement des ressources. NPR-27643 : correctif pour CQ-4246536.
Un lot reste à l’état installé après l’installation du package Forms Management sur la branche release/640. Correctif pour CQ-4265410
Les Forms envoyés avec leurs pièces jointes n’apparaissent pas dans le processus avec l’action d’envoi &quot;Invoke AEM Forms Workflow&quot; et activez l’envoi du portail coché. Correctif pour CQ-4263110

**Forms - Intégration du serveur principal**

* Impossible de tester le préprocesseur et l’envoi personnalisé avant/après à l’aide du SDK client, correctif pour CQ-4238469

**Programme d’installation de Forms JEE**

**Forms - Sécurité Document**

* Lors de l’utilisation du service updatepolicy, l’erreur d’objet ne peut pas grossir se produit. NPR-28751 : correctif pour CQ-4252287
* Échec de la création de signature avec l&#39;ancienne version de commons-pkg. Correctif pour CQ-4265535

**Forms - Foundation JEE**

* Lorsque AEM Forms est installé sur IBM WebSphere, la création d’un modèle de données de formulaire basé sur SOAP échoue. NPR-27923 : correctif pour CQ-4251134
* L’outil SRT de PDF Generator ne détecte pas la version installée d’Adobe Acrobat. NPR-27971

**Forms - Designer**

* Certaines images JPEG d’un modèle XDP ne s’affichent pas correctement.  NPR-26702 : correctif pour LC-3917457

**Forms - Workflow**

* HTML5 Forms avec un processus d’envoi par défaut dans an.lca ne fonctionne pas sur JBoss 7. NPR-28675 : correctif pour CQ-4243928
* Impossible d&#39;envoyer des PDF forms dans Workspace HTML. NPR-28058 : correctif pour CQ-4260373
* Les données du client sont imprimées dans les journaux d’informations à l’aide du Forms Workflow Invoke FDM Service. Correctif pour CQ-4260385

**Packs de fonctionnalités inclus**

**Sites**

* Le contrôle de version des fragments de contenu compare les améliorations apportées aux différences pour AEM 6.4. NPR-26760 : FP pour CQ-4248839
* Améliorations des différences de variation des fragments de contenu pour AEM 6.4. NPR-27866 : FP pour CQ-4248839
* Fonction activée dans la configuration OSGI **AEM Flux de travaux de retrait Indicateur de fonction**. L&#39;action de retrait doit arrêter l&#39;instance de workflow après avoir défini l&#39;indicateur. NPR-26451 : correctif pour CQ-4259090

**Plate-forme**

* Requête améliorée Facet Facet Extraction du créateur de  exploitant l&#39;API Oak pour la version 6.4. NPR-26674 : FP pour CQ-4230337

**bundles OSGI et packages de contenu inclus**

Le texte suivant documents la liste des lots OSGI et des packages de contenu inclus dans le CFP.

Liste des lots OSGi inclus dans AEM 6.4.4.0

[Obtenir le fichier](assets/bundles_6_4_4_0.txt)

Liste des packages de contenu inclus dans AEM 6.4.4.0

[Obtenir le fichier](assets/osgi_package_6_440.txt)

#### aem 6.4.3.0 {#experience-manager-6430}

aem 6.4.3.0 est une mise à jour importante qui comprend des améliorations et correctifs concernant les performances, la stabilité, la sécurité et les clients clés depuis la publication de l’AEM 6.4 en avril 2018.

Il est également cumulatif, ce qui signifie que la version 6.4.3.0 inclut tous les Service Packs AEM 6.4 version antérieure.

Voici quelques-uns des points saillants de l&#39;AEM 6.4.3.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.9.
* Prise en charge Ajoutée de la propriété allowedPaths dans les modèles de formulaires adaptatifs.
* Amélioration de la recherche par panneau des ressources dans AEM
* Correctifs de scripts intersites (XSS) dans la page Connexion.
* Amélioration de l’instrumentation de l’interface utilisateur.
* Améliorations de la gestion des données de formulaire.
* Amélioration de la gestion du nommage d’article dans un champ multichamp.
* Amélioration de la gestion des éléments d’espace réservé (Vue de carte et Vue de Liste) lors de la sélection.
* Authentification IMS de l&#39;Adobe Ajouté et prise en charge des Admin Console pour Managed Services.

**Ressources**

* Le processus de mise à jour des actifs de gestion des actifs numériques n’extrait pas les références des fichiers INDD si l’option Découple IDS est activée. NPR-26243; Correctif pour CQ-4250933
* Le message de réussite ne s’affiche pas lorsque des ressources sont publiées avec l’éditeur en bloc Ressources. NPR-26252; Correctif pour CQ-4251688.
* Après avoir examiné un fichier à partir d’un résultat de recherche, si vous cliquez sur le bouton Précédent dans le navigateur, un message d’erreur &quot;Mauvaise requête&quot; s’affiche avec le code d’erreur 400. NPR 26578 ; Correctif pour CQ-4253741
* Les métadonnées de fichier affichent une erreur d&#39;espace de nommage non valide après l&#39;installation d&#39;un Service Pack. NPR-22341; Correctif pour CQ-4237202
* L’option permettant de réorganiser les dossiers et les fragments de contenu dans la vue de liste ne s’affiche pas pour les dossiers concernés. NPR-27153; Correctif pour CQ-4255873
* Les utilisateurs ne peuvent pas ajouter de ressources à une nouvelle collection, car un message d’erreur s’affiche avec une image rompue dans la boîte de dialogue contextuelle d’erreur. NPR-22431; Correctif pour CQ-4237086
* La liste déroulante en cascade n’est pas prise en charge dans les listes déroulantes dynamiques. NPR-27043 ; Correctif pour CQ-4252564
* Si les utilisateurs définissent une valeur autre que la valeur par défaut pour le dossier racine de la Société dans la configuration cloud de DMS7, le paramètre prédéfini de visionneuse ne fonctionne pas comme prévu. NPR-26360; Correctif pour CQ-4249505
* Le rapports des ressources échoue pour les instances comportant un très grand nombre de ressources. NPR-27278; Correctif pour CQ-4256748
* Les sous-dossiers n’héritent pas du profil d’image SmartCrop du dossier parent. NPR-27197; Correctif pour CQ-4256273
* Lorsque l’intégration Dynamic Media est activée, certaines propriétés de métadonnées des ressources sont modifiées. Les attributs de largeur, de hauteur et d’emplacement ne s’affichent pas. NPR-27203; Correctif pour CQ-4256258
* Dynamic Media n’utilise pas le proxy configuré pour certains types de ressources. NPR-25211 ; Correctif pour CQ-4244871
* La page Editeur de métadonnées contient une exception de pointeur nul pour un paramètre d’élément non valide. NPR-26169 ; Correctif pour CQ-4241368.
* Si une règle de choix est appliquée à une liste déroulante et qu’une règle obligatoire lui est appliquée, la règle requise ne peut pas être satisfaite dans l’éditeur de métadonnées. NPR-27479; Correctif de CQ-4251428

**Sites**

* Un utilisateur peut contrôler les fonctions de l’éditeur de texte enrichi en mode plein écran en ligne à l’aide de stratégies de contenu, mais il ne peut pas contrôler les fonctions de l’éditeur de texte enrichi de la boîte de dialogue avec les stratégies de contenu. NPR-26750 : correctif pour CQ-4241130
* L’éditeur de texte enrichi devient inutilisable lorsqu’il passe du mode plein écran au mode flottant. La vue flottante contient deux éditeurs de texte enrichi. NPR-25589 : correctif pour CQ-4206008
* Lorsque la touche Retour (touche Entrée) est enfoncée dans un champ de texte, l’éditeur de texte enrichi passe en mode plein écran. NPR-26204 : correctif pour CQ-4245893
* Le module externe liste de l’éditeur de texte enrichi est désactivé automatiquement et n’autorise pas les modifications. NPR-26507 : correctif pour CQ-4239387
* Lorsqu’un caractère spécial est ajouté à la fenêtre de l’éditeur de texte enrichi, la fenêtre défile vers le haut. NPR-26435 : correctif pour CQ-4249869
* Questions de caching ou de non caching de segment.js dans le contexte du client. NPR-26622 : correctif pour CQ-4253486
* Lorsqu’une règle enfant est activée de l’instance d’auteur à l’instance de publication, l’instance de publication cesse de fonctionner. NPR-26601 : correctif pour CQ-4253588
* En cas de combinaison de l’éditeur de texte enrichi avec plusieurs champs, l’erreur « Uncaught TypeError: fieldAPI.getName is not a function at foundation.js » se produit. NPR-27146 : correctif pour CQ-4253155
* L&#39;intégration Salesforce ne peut pas utiliser la configuration du proxy. NPR-27244 : correctif pour CQ-4245300
* Lorsque vous planifiez l’activation d’une page à l’aide de l’option Gérer la publication pour une date ultérieure et que vous passez à la vue de liste, l’icône de calendrier est manquante. NPR-26974 : correctif pour CQ-4239206
* Les utilisateurs ne peuvent pas modifier les autorisations de groupe d’utilisateurs fermés dans les propriétés de la page. NPR-27138 : Correctif pour CQ-4256089
Impossible de modifier les balises par balisage. NPR-26957 : correctif pour CQ-4254858
* Lorsqu’une balise référencée à partir d’un modèle de fragment de contenu structuré est déplacée, les références existantes à la balise dans un fragment de contenu ne sont pas mises à jour. Cela se produit dans l’écran de modification du modèle de fragment de contenu. NPR-26776 : correctif pour CQ-4251805
* Lorsque vous créez et promouvez un lancement comportant plusieurs pages, plusieurs versions de chaque page sont créées. NPR-26917 : correctif pour CQ-4254663
* aem siteadmin ne gère pas les chemins tapés dans la barre d&#39;adresse du navigateur. NPR-26780 : correctif pour CQ-4254097
* Lorsqu&#39;une page est déplacée à un nouvel emplacement sans le renommer, l&#39;historique des versions de la page est perdu. NPR-26706 : correctif pour CQ-4254025
* Les URL de l’éditeur d’administration des fragments d’expérience n’autorisent pas les incrustations. NPR-26319 : correctif pour CQ-4252156
* Lorsqu’une page est créée avec un modèle contenant un fragment d’expérience vide et publié, la page ne s’ouvre pas et une erreur DefaultSlingScript se produit. NPR-26305 : correctif pour CQ-4252460
* Lorsque l’utilisation simple des données est utilisée avec des classes portant le même nom, un code non conforme est généré. NPR-27282 : correctif pour Sling-7581
* Après l&#39;installation du SP de mise à niveau, les sites disposent d&#39;une configuration de déploiement de plan blanc. NPR-27609 : correctif pour CQ-4257078

**DAM - Portail de marque**

* Les prédicats de balise ne sont pas publiés lorsque le formulaire de schéma de métadonnées est publié sur le portail de la marque. Correctif pour CQ-4256218
* Lorsqu’un dossier de troisième niveau est publié d’AEM à Brand Portal sans publier les dossiers parents, le nom du dossier est modifié. Correctif pour CQ-4255423
* Le prédicat du navigateur de chemins d’accès est publié d’AEM Assets vers le portail de marques, comme prévu. Cependant, le chemin publié à BP reste /content/dam, qui doit être mis à jour. Correctif pour CQ-4256240

**DAM - Creative Cloud**

* L’icône &quot;Rechercher dans les ressources d’Adobe&quot; est absente de la navigation principale AEM. Correctif pour CQ-4254343

**DAM - Client DM**

* Après l’importation de vidéos dans un dossier associé au Profil de traitement vidéo AVS, la fenêtre du navigateur s’actualise encore et encore. Correctif pour CQ-4253563
* La publication YouTube échoue lors de l’utilisation d’une balise ad hoc contenant des caractères en majuscules. Correctif pour CQ-4252477
* Lorsqu’une annotation est créée dans un fichier tel que PDF, l’interface utilisateur début une boucle d’actualisation de page infinie. NPR-27052 : correctif pour CQ-4255396

**DAM - Services DM**

* Dynamic Media n’utilise pas le proxy configuré pour certains types de ressources. NPR-10727; Correctif pour CQ-4244871

**Plate-forme**

* Problèmes de performances avec org.apache.sling.i18n. NPR-26812 : correctif pour SLING-7543
* Impossible d&#39;afficher les propriétés du noeud lorsque le XML d&#39;entrée est formaté et déployé. NPR-26198 : correctif pour CQ-4250448
* IndexOutOfBoundsException dans ResourceProviderTracker. NPR-26968 : correctif pour GRANITE-23310
* La console JMX accumule de nombreuses sessions d’administration et une nouvelle session est ouverte toutes les 5 minutes. NPR-26958 : correctif pour CQ-4251090
* Après la mise à niveau de la version 6.2 vers la version 6.4, le fichier journal affiche le suivi de pile pour le résolveur de ressources non fermé com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck. NPR-26176 : correctif pour Granite-21734
* Lorsqu&#39;un agent de vidage de répartiteur prêt à l&#39;emploi est configuré pour mettre à jour les alias, l&#39;opération échoue avec un StackOverflowError. NPR-26373 : correctif pour CQ-4242928
* La réplication utilise le jeton OAuth expiré jusqu’à ce qu’il échoue. NPR-25894
* Page restreinte (page Groupe d’utilisateurs fermé) avec sling : l’alias ne redirige pas l’utilisateur vers la page de connexion. NPR-25715 : Correctif pour Granite=22263
* Sur les balises de publication, aucune activité n’est affichée dans l’interface utilisateur. Correctif pour CQ-4255961
* Impossible de modifier les balises dans l&#39;interface utilisateur classique. Correctif pour CQ-4258697
* Mise à jour de org.apache.felix.http.bridge vers la version 4.0.4. NPR-27038 : Backport pour Granite - 23334
* Les journaux d’activité du gestionnaire de packages doivent être extraits dans un fichier journal distinct. NPR-27323 : correctif pour Granite-14866
* Le programme de validation de package ne signale pas les recouvrements dans le CFP. NPR-27119 : correctif pour GRANITE-22825

**Projets**

* L&#39;API ACP gère mal la pagination avec uniquement les enfants de sous-répertoire. NPR-27617 : correctif pour CQ-4258639

**OAK**

* Impossible de se connecter au référentiel après avoir installé AEM Service Pack 2 6.4. NPR-27171 : correctif pour Granite-23317

**Réplication**

* Le journal d&#39;audit reste ouvert avec de principales sessions qui continuent à augmenter constamment avec environ 750 par jour. NPR-27062 : correctif pour CQ-4241350

**Communautés**

* Les publications et les réponses du forum sont ajoutées au haut de la deuxième page et, une fois actualisées, la publication se déplace à l’emplacement correct en haut de la première page. NPR-27342 : correctif pour CQ-4247338
* Les liens vers toutes les ressources ignorent le chemin de contexte (/aempublish) après le défilement. NPR-26982 : correctif pour CQ-4254345
* Les groupes Ajoutés ne sont pas visibles dans la liste déroulante Gestionnaires de communauté, Modérateurs de communauté et Membres privilégiés lors de la modification d’un site publié. NPR-27190 : correctif pour CQ-4258574
* Seuls 10 groupes sont répertoriés dans la page des ressources d’activation, même si la pagination est activée pour la liste des groupes. NPR-26934 : correctif pour CQ-4252985
* L’option permettant d’activer/de désactiver la recherche pour les publications planifiées dans le composant journal est fournie dans ConfigMgr et le travail SearchScheduledPosts est optimisé. NPR-26923 : correctif pour CQ-4250463
* La recherche par mots-clés dans l&#39;adresse ne fonctionne pas dans la page des composants du calendrier lorsque AEM communauté est définie pour fonctionner avec DSRP. NPR-26737 : correctif pour CQ-4258493
* Mise en oeuvre d’un lien direct vers le commentaire au lieu de la publication principale dans les détails d’un commentaire, pour les ressources d’activation et d’interface utilisateur de modération. NPR-26704 : correctif pour CQ-4251381
* Le contenu modéré par le biais de la sélection multiple sur la console de modération n’apparaît pas dans le flux d’Activité. NPR-26695 : correctif pour CQ-4253244
* La recherche avec prénom et nom dans le champ À de la messagerie des communautés ne renvoie pas le résultat attendu. NPR-26385 : correctif pour CQ-4248673
* Erreur observée lors du téléchargement d’une pièce jointe autre qu’une image (par exemple .pdf) dans le forum. NPR-27360 : correctif pour CQ-4257753
* La désactivation ou la désactivation d’une publication de forum ne fonctionne pas si la fonction Auteur-Publier est définie avec MySQL DSRP. NPR-26125 ; Correctif pour CQ-4251520
* Les composants de collection (forums, blogs, calendrier, idéation, QnA) disposent désormais d’une propriété dans la boîte de dialogue des composants pour activer/désactiver &quot;Bloquer l’UGC en mode d’édition Auteur&quot;, afin d’autoriser/de refuser le chargement de l’UGC en mode d’édition WCM. NPR-26978 : correctif pour CQ-4248161
* Balises La recherche ne fonctionne pas pour les termes de recherche localisés. NPR-26171 : correctif pour CQ-4249926
* Le bouton Précédent saute une page dans la recherche de forum. NPR-26950 : correctif pour CQ-4254804
* L&#39;instance AEM s&#39;exécutant sur le port HTTP par défaut (80) ne peut pas atteindre le fichier imsmanifest.xml. NPR-27173 : correctif pour CQ-4252211
* Ne pas marquer le commentaire comme réponse pour QnA ne fonctionne pas si AEM Communities est défini avec DSRP. NPR-26247 : correctif pour CQ-4252232
* Impossible d&#39;appeler l&#39;Enregistrement d&#39;Adobe : Erreur 414 - Long GET URI observé lorsque les utilisateurs recherchent /content/community-components/en/search.html et sélectionnent le champ d’auteur comme l’un des filtres de ce terme de recherche. NPR-26643 : correctif pour CQ-4251303
* La valeur de liste déroulante pour DataCentreURL dans la configuration ASRP est changée de Dallas en Virginie (pour VA6). NPR-26936 : correctif pour CQ-4254434
* Les caractères spéciaux dans la recherche de forum renvoient des erreurs ou aucun résultat. NPR-26930 : correctif pour CQ-4247744
* Le nombre affiché pour &quot;Nombre de résultats&quot; dans la recherche de forum utilise un délimiteur incorrect pour les paramètres régionaux anglais et allemand. NPR-27050 : correctif pour CQ-4248939
* Les notifications non lues n’augmentent pas au-delà de 21. NPR-26946, NPR-27480 : correctif pour CQ-4252829, CQ-4256939
* La pagination dans la section des commentaires de n’importe quel composant permet aux utilisateurs de faire défiler la page pour voir le contenu de la page, dès qu’ils atteignent une page par pagination. NPR-27032 : correctif pour CQ-4251228
* Le dossier Site de la communauté ne peut pas être cliqué sur l’image miniature lors de l’affichage à partir de la console d’administration sur l’instance d’auteur AEM. NPR-26986 : correctif pour CQ-4254036
* L&#39;option &quot;marquer tout lire&quot; ne marque que les 10 premières notifications comme lues et d&#39;autres restent non lues jusqu&#39;à l&#39;actualisation de la page. NPR-27037 : correctif pour CQ-4254058
* La pagination n’est pas déclenchée pour l’idéation et la liste des rubriques (ou des réponses) est plus longue, sauf si elle est rechargée. NPR-26193 : correctif pour CQ-4252104
* Activités d’autres utilisateurs et contenu UGC supprimé visibles lors de la connexion avec les informations d’identification du modérateur et l’ajout de &quot;#social-activités&quot; ou &quot;#tabs-2&quot; à la fin de l’URL de profil du modérateur. Correctif pour CQ-4251355
* Toutes les balises attribuées ne peuvent pas être supprimées d&#39;un article de blog. NPR-26851 : correctif pour CQ-4253359
* Les relations avec l’UGC ne sont pas supprimées lors de la suppression de l’UGC. NPR-27630 : correctif pour CQ-4258706
* Le lien des réponses ne fonctionne pas sur les clics sur la ligne des réponses du Forum. NPR-27623 : correctif pour CQ-4256138
* La limite des abonnements utilisateur est limitée à 1000. NPR-27614 : correctif pour CQ-4254689
* La modification d’un site et des rôles dans les paramètres du rôle entraîne l’exception Null Pointer. NPR-27377; Correctif pour CQ-4255909

**Traduction**

* La prévisualisation de traduction ne fonctionne pas avec l’exemple de contenu we.commerce. NPR-26727 : correctif pour CQ-4241179

**IU - Fondation**

* Une exception NullPointerException est renvoyée lorsque vous tentez de télécharger des configurations après la mise à niveau vers AEM 6.4. NPR-27310 : Correctif pour Granite-23573
* Backport proactif pour les correctifs granite.platform.login. NPR-26941
* Prise en charge proactive pour les granite.ui.co de contenu. NPR-26294
* Le composant de champ Numéro ne valide pas les nombres négatifs dans Internet Explorer 11. NPR-26701
* Prise en charge proactive pour les granite.ui.co de ralui3. NPR-26662
* Backport proactif pour les granite.ui.co de ralui3-aeon. NPR-26666
* Backport proactif pour granite.ui.foundation.components correctifs. NPR-27313
* Prise en charge proactive des granite.ui.com de mise à jour. NPR-26753
* Rétroportages proactifs de l’interface utilisateur de Foundation. NPR-26248

**Intégration**

* Les modifications dans les expériences AEM créées par le moteur de ciblage ne sont pas publiées. NPR-24869 : correctif pour CQ-4247832
* Impossible de créer plusieurs activités et expériences si leurs noms comportent des caractères japonais. NPR-27271 : correctif pour CQ-4256857
* Mettre à jour le point de terminaison de l’API de lancement. NPR-26790 : correctif pour CQ-4254380
* (Personnalisation) BrandsRetriever parcourt l&#39;arbre entier. NPR-27060 : correctif pour CQ-4255790

**WCM - Interface utilisateur d’administration**

* Test HTTP Ajouté pour la publication/l’annulation de la publication d’une page avec des références et d’un test d’interface utilisateur pour Live Copy. Correctif pour CQ-4256894

**WCM - Éditeur de page**

* La barre d’outils Modifier est désactivée pour les composants lors de la première modification. Correctif pour CQ-4253270

**Formulaires**

Les principaux points forts d&#39;AEM Forms 6.4.3.0 sont les suivants :

* Activation de la prise en charge d&#39;un tableau/liste d&#39;objets avec la substitution d&#39;entité dynamique.
* Activation de la conformité FIPS pour le flux de travaux étendu Reader dans Digital Signature, Reader Extensions, CryptoProvider et TrustStore.
* Prise en charge PDF/UA Ajoutée des formulaires XFA générés à l’aide de Designer ou de Output Service.
* Activation de la prise en charge de la propriété allowedPaths dans les modèles de formulaires adaptatifs.
* Prise en charge Ajoutée de JBoss 7.1.4 pour AEM Forms 6.4.

**Package de modules complémentaires Forms**

**Intégration du serveur principal**

* Impossible de renseigner les mappages de modèles de données de formulaire basés sur des entités dynamiques dans la réponse SOAP. NPR-26428 : correctif pour CQ-4250639
* La valeur de _elementNamespace dans les données supplémentaires du modèle de données de formulaire, saisie à l’aide de l’interface utilisateur de test, n’est pas correctement reflétée dans la requête SOAP. Correctif pour CQ-4255373
* Une contrainte de propriété nullable est initialisée avec une valeur par défaut et ne peut pas être synchronisée avec FDM. Correctif pour CQ-4253873
* La valeur par défaut de la propriété nullable n’est pas définie sur True pour la source de données OData. Correctif pour CQ-4253870

**Formulaires adaptatifs**

* Impossible de charger les sites et l’éditeur de formulaires. NPR-26977 ; Correctif pour CQ-4249170
* Problèmes lors de l’ajout d’une pièce jointe à un formulaire adaptatif à l’aide du clavier. NPR-25913 ; Correctif pour CQ-4249456

**Forms - Communication interactive**

* Impossible de déplacer un panneau qui a été ajouté à l&#39;aide de l&#39;option Ajouter le panneau enfant dans l&#39;arborescence de contenu dans le canal Web d&#39;Interactive Communication et dans les formulaires adaptatifs. Correctif pour CQ-4253915
* Les noms des tables s’affichent à la place du titre de l’association FDM dans la section Sources de données du canal d’impression. Correctif pour CQ-4253669
* La fonction isUseXFABullets() n&#39;est pas désactivée dans la classe PrintChannelRenderOptions et est disponible dans le SDK client. Correctif pour CQ-4246583, CQ-4252700

**Correspondence Management**

* Javadocs 6.4 ne contient pas com.adobe.dbforms.* package et les classes correspondantes. Correctif pour CQ-4253200
* L’interface utilisateur CCR affiche une valeur de jonction par défaut pour le champ de date au cas où aucune entrée des données de test XML n’aurait été effectuée. Correctif pour CQ-4252041
* Si une lettre contient un module de liste, l’espace entre la puce et le texte est perdu lors de la génération du fichier PDF à partir de la lettre. Correctif pour CQ-4250588

**Gestionnaire de formulaires**

* Activation de la prise en charge de la propriété allowedPaths dans les modèles de formulaires adaptatifs. NPR-26598 : correctif pour CQ-4255892

**Forms - Workflow**

* Si des accolades sont incluses dans le nom de la tâche lors de l’exécution du processus Forms, une exception s’affiche dans les journaux. Correctif pour CQ-4256626
* Impossible d&#39;ouvrir un modèle de recherche dans l&#39;espace de travail AEM Forms. Correctif pour CQ-4255651

**Mobile Forms**

* La notification de sortie ne s’affiche pas lorsque vous quittez le champ de date dans AEM Forms rendu au format HTML dans Internet Explorer ou Chrome. NPR-26483 : correctif pour CQ-4239352
* Les dates contenues dans le XML au début du traitement provoquent une erreur de validation dans les formulaires lorsque l’utilisateur tente de quitter le formulaire. NPR-26787 : correctif pour CQ-4251211

**Programme d’installation de Forms JEE**

**Service PDF Generator**

* Impossible d&#39;afficher les paramètres de Rapports et de conformité des normes pour PDF Generator. NPR-26715 : correctif pour CQ-4253384
* le fichier binaire convertpdf est absent du package de module complémentaire Forms AIX, ce qui entraîne un échec lors de l’appel du service PDFA. Correctif pour CQ-4257873
* Le service de capture de papier se bloque lors du traitement des fichiers TIFF. NPR-28079 : correctif pour CQ-4240649

**Services de document**

* Ajoutez la conformité FIPS pour le flux de travaux RE dans Digital Signature, Reader Extensions, CryptoProvider et TrustStore. NPR-27495 : correctif pour CQ-4257572
* La conversion échoue lors de l’exécution du service AssemblerService.toPDFA dans une boucle. NPR-26354 : correctif pour CQ-4248656
* Impossible de valider correctement la conformité des fichiers PDF en fonction des normes PDF/A-1b. NPR-26286 : correctif pour CQ-4227539
* Problèmes de mémoire lors de la mise à niveau de AEM Forms de 6.1 SP2 CFP5 vers CFP13. NPR-26285 : correctif pour CQ-4244379
* Impossible de valider correctement la conformité des fichiers PDF en fonction des normes PDF/A. NPR-26272 : correctif pour CQ-4248823

**Forms - Foundation JEE**

* Prise en charge Ajoutée de JBoss 7.1.4 pour AEM Forms 6.4. NPR-27331 ; Correctif pour CQ-4255601

**Packs de fonctionnalités inclus**

* Activation de la prise en charge d&#39;un tableau/liste d&#39;objets avec la substitution d&#39;entité dynamique. NPR-26590 : correctif pour CQ-4254655

**Unités OSGI et packages de contenu inclus**

Liste des lots OSGi inclus dans AEM 6.4.3.0

[Obtenir le fichier](assets/6.4.3.0_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.3.0

[Obtenir le fichier](assets/6.4.3.0_OSGI.txt)

#### aem 6.4.2.0 {#experience-manager-6420}

aem 6.4.2.0 est une mise à jour importante qui comprend des améliorations et des correctifs concernant les performances, la stabilité, la sécurité et les clients clés depuis la publication de l&#39;AEM 6.4 en **avril 2018.**
Il est également cumulatif, ce qui signifie que la version 6.4.2.0 inclut tous les Service Packs AEM 6.4 version antérieure.

Voici quelques-uns des points saillants de l&#39;AEM 6.4.2.0 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.7.
* Prise en charge Ajoutée des fonctionnalités HTML Template Language (HTL) Specification 1.4
* Prise en charge Ajoutée de MongoDB Enterprise 3.6.
* L&#39;éditeur de page Sites ajoute la prise en charge de la modification et de la composition dans le contexte avec des composants côté client créés en React ou Angular en combinaison avec <a href="../sites-developing/spa-walkthrough.md">AEM éditeur SPA SDK JS SDK</a>.
* Améliorations des fragments de contenu : ajout de la capacité d’annoter dans les champs de texte et de comparer côte à côte les versions.
* Intégration [Ajoutée avec Adobe Stock](/help/assets/aem-assets-adobe-stock.md) afin que les utilisateurs puissent rechercher, prévisualisation, enregistrer et mettre sous licence des actifs Adobe Stock directement à partir de l’interface utilisateur AEM. Pour plus d’informations, voir [Utilisation de ressources Adobe Stock avec AEM Assets](https://docs.adobe.com/content/help/fr/experience-manager-learn/assets/creative-workflows/adobe-stock.html).
* Les ressources prennent également en charge les métaschémiques conditionnelles dynamiques et permettent de définir un schéma de métadonnées pour les dossiers de ressources.
* Configuration Ajoutée dans chaque composant pour activer/désactiver la fonctionnalité de création/mise à jour de miniatures de dossier.
* Amélioration de l’éditeur d’images lors de la création de pages.
* Correctif de régression dans les communautés pour le événement de notation qui n&#39;est pas correctement géré en cas de suppression de la réponse sélectionnée.
* Révision de la limite de résultats de recherche maximale pour solr à MAX_INT-10000.
* La tâche de vidage des transactions n&#39;est lancée que lors du premier appel à storeTransaction.
* Le bouton Sélectionner tout est désormais disponible dans la Vue de cartes et la Vue de colonnes.
* Améliorations de l’accessibilité dans CoralUI.
* Amélioration de la gestion de Coral.Keys.
* Mise à jour de moment.js vers la version 2.2.2
* Mise à jour de jquery vers 1.12.1
* Mise en place du composant d’état Fondations-Processus.
* Mise à jour de GCC vers la dernière version.
* Déplacez SAML vers une nouvelle synchronisation externe IDP.

**Ressources**

* La génération de sous-ensembles pour le fichier pptx ne contient aucune image ni miniature. NPR-24286 : correctif pour CQ-4217986
* migrateAllAssets - Ajoutez la prise en charge du traitement par lots et améliorez la méthode AEM qui ajoute un UUID aux anciens actifs. NPR-24861 : correctif pour CQ-4242863 et CQ-4247874
* Problème de performances avec la génération de miniatures. NPR-24693 : correctif pour CQ-4246960
* (Interface utilisateur tactile) Le composant &quot;prédicat d’options&quot; reste vide lorsqu’il est ajouté à la page d’éditeur Asset Share. NPR-24643 : correctif pour CQ-4245295
* (Flux de travaux) Les ressources de balises actives ne sont pas traitées par le biais de la configuration du proxy. NPR-25840 : correctif pour CQ-4248202
* (Omnisearch) la suppression de filetype:image des critères de recherche ne supprime pas le type d&#39;image. NPR-25232 : correctif pour CQ-4248280
* Lors de la tentative de déplacement d’un fichier vers un autre dossier, les dossiers dont le nom contient une apostrophe ne s’affichent pas. NPR-25125 : correctif pour CQ-4248660
* Le curseur de la page Sous-ressource ne fonctionne pas correctement lorsque les préférences de langue sont définies sur un autre format que l’anglais. NPR-25274 : correctif pour CQ-4248489
* Problème avec le fichier csv d’exportation de métadonnées lorsqu’il est ouvert sur des machines au format numérique européen. NPR-26009 : correctif pour CQ-4250677
* Le bouton Créer n’est pas disponible lors de la sélection du dossier de ressources sans autorisation de suppression. NPR-25788 : correctif pour CQ-4250140
* (Backport) Améliorations de l’accessibilité : Duplicata-id : La valeur de l&#39;attribut id doit être unique, Libellé : Les éléments de formulaire doivent avoir des libellés et un nom de lien : Les liens doivent présenter un texte perceptible. NPR-24252 : correctif pour CQ-4250905, CQ-4250906, CQ-4250907
* Le téléchargement d’un fichier CSV avec des champs séparés par &quot;,&quot; échoue pour les pays européens. NPR-25549 : correctif pour CQ-4249931
* (Portail de marques) Les sous-ensembles d’un fichier PDF de plusieurs pages ne sont pas publiés lorsqu’un fichier est publié. NPR-25991 : correctif pour CQ-4245162
* Publiez les fonctionnalités ultérieures pour la réplication AEM sur le portail des marques. NPR-25911 : correctif pour CQ-109139
* La publication et la dépublication de la collection privée par des utilisateurs non administrateurs génèrent un NPE. NPR-25906 : correctif pour CQ-4250594
* Désactivez la publication de fragments de contenu et de schémas de formulaires sur le portail de marque. NPR-24176, NPR-26004 : correctif pour CQ-4251592, CQ-4252026
* (Dynamic Media) Mise à jour des visionneuses DM vers la version 5.10.1 qui permet de vérifier les noms de duplicata sur la page Paramètres d’image prédéfinis. Reportez-vous à Mise à jour des visionneuses Dynamic Media (5.10.1). NPR-24403 : correctif pour CQ-4247554
* Erreur JavaScript dans la console du navigateur dans la vue de colonne lors de la sélection d’un fichier ou d’un dossier. NPR-25939 : correctif pour CQ-4250228
* (vue des colonnes) Impossible d&#39;identifier les tâches car le fichier de clé apparaît comme une entrée blanche vide. NPR-25903 : correctif pour CQ-4246307

**Sites**

* La requête du fichier datasource.jsp sur AEM 6.2 diffère de l&#39;AEM 6.4. NPR-24968 : Correctif pour CQ-4244235
* (IU classique) Impossible d’ajouter des balises aux pages. NPR-25255, NPR-25612 : correctif pour CQ-4249615
* Spécification du langage de modèle HTML 1.4 fonctionnalités renvoyées à AEM 6.4.2.0 NPR-24585
* Héritage incorrect sur le composant local après la copie d’une page de copie dynamique. NPR-25920 : correctif pour CQ-4236737, CQ-4248957
* L’heure d’activation/de désactivation est stockée dans crx/de, mais elle n’est pas récupérée dans la console de l’interface utilisateur des propriétés de page. NPR-25154 : correctif pour CQ-4243431
* Styles Système rompt les valeurs de propriétés initiales de la boîte de dialogue. NPR-25648 : correctif pour CQ-4250073
* Lors de la définition d’une propriété cq:tagName dans un noeud cq:htmlTag, le nom de la balise n’est pas pris en compte si le composant est inclus via JSP. NPR-24154 : correctif pour CQ-4244120
* Pour les composants d’analyse imbriqués, la première conception satisfaisante (avec le chemin le moins imbriqué) est toujours appliquée à partir de plusieurs composants disponibles. Pour plus d’informations, voir [Résolution du chemin de conception](https://docs.adobe.com/content/help/en/experience-manager-64/developing/platform/templates/page-templates-static.html). NPR-24973 : correctif pour CQ-4246276
* Lorsque vous collez du texte dans un composant RTE, une boîte de dialogue contextuelle s’affiche, mais son rendu n’est pas correct. NPR-24895 : correctif pour CQ-4245901
* (RTE) Problèmes de performance avec indicateur de terrain obligatoire. NPR-24894 : correctif pour CQ-4241895
* (Composant de page) L’Ajoute d’un composant à Parsys est coupée de la droite et ressort sur la largeur de l’image du périphérique. NPR-25536 : correctif pour CQ-4238224
* L’éditeur de texte brut envoie des données non ajustées et ajoute des espaces supplémentaires. NPR-25312 : correctif pour CQ-4249006
* Lors de l’ouverture du composant en mode intégré, les modules externes chargés précédemment ne sont pas visibles la deuxième fois. NPR-24610 : correctif pour CQ-4236850
* Le chargement d’un fichier XF dans la vue d’éditeur par copier/coller ne charge pas automatiquement la variation principale. NPR-24841 : correctif pour CQ-4248037
* Une structure HTML incorrecte dans siteadmin / damadmin rompt IE11. NPR-24686 : correctif pour CQ-4246363, CQ-4248402
* (Assistant Gestion de la publication) Le calendrier pour la date d’activation à l’étape Options ne s’ouvre pas après certaines actions à l’étape Étendue. NPR-25681 : correctif pour CQ-4250205
* L’UI classique ne permet pas de modifier le CUG pour des raisons d’obsolescence. NPR-25075 : correctif pour 4241823
* Option de création indisponible pour créer des fragments d’expérience. NPR-26053 : correctif pour CQ-4249923
* La variation XF est activée deux fois, ce qui génère des ID de duplicata pour le même élément. NPR-24179 : correctif pour CQ-4245093
* Le tableau Foundation est vulnérable au cross-site scripting par stockage. NPR-25185 : correctif pour CQ-4240760
* Erreur de &quot;valeur de sélecteur de récursion non valide&quot; lors de la migration d&#39;un composant de AEM 6.2.1.13 vers AEM 6.4. NPR-24146

**WCM - Éditeur de page**

* L’empilement de plusieurs parsys en raison de requêtes longues (plus de 6) provoque un ralentissement d’AEM. Correctif pour CQ-4240247
* Erreur JS lors de l&#39;ajout de cq:tagName vide dans le noeud cq:htmlTag. Correctif pour CQ-4251852
* Mettez à jour EditableActions en fonction du déplacement columnClassNames. Correctif pour CQ-4250781
* Exposez les chemins des ressources et des modèles à l’aide d’une propriété et d’un attribut uniques. Correctif pour CQ-4251255
* Annulation des modifications de l’API export.json. Correctif pour CQ-4251854
* (SPA modifiable) Version candidate pour la version 1.0.0. Correctif pour CQ-4251991
* La barre d’outils Modifier est désactivée pour les autres composants lors de la modification d’un composant. Correctif pour CQ-4253270

**Intégration**

* Les champs Bibliothèque et URL de téléchargement doivent être modifiables. NPR-24804 : correctif pour CQ-4246864
* Problème avec plusieurs configurations de gestion dynamique des balises. NPR-24685 : correctif pour CQ-4247293
* Prise en charge Ajoutée du déploiement asynchrone pour les bibliothèques clientes hébergées. NPR-25716 : correctif pour CQ-4245745
* Le composant ciblé avec l’offre correspondante manquante effectue le rendu de la page entière et, au lieu d’un composant ciblé vide, un autre rendu complet de la page est ajouté. NPR-25273 : correctif pour CQ-4248003
* Le moteur Target (mbox.js, at.js) n’utilise pas d’URL mal formées et utilise des URL contenant deux-points qui peuvent rencontrer des problèmes avec certains déploiements. NPR-25339 : correctif pour CQ-4237854
* (Launch)LibraryDownloadProcess stocke une valeur libraryUri incorrecte. NPR-25330 : correctif pour CQ-4250006

**Plate-forme**

* boucle de réindexation | NPE lors de l&#39;exécution de BinaryTextExtraction lors de la mise à niveau statique de 6.3 à 6.4. Correctif logiciel pour Granite - 21677
* Remplacement transfrontalier du chemin marqué interne /libs/cq/cloudserviceconfigs/templates/configpage/jcr:content - Problème lors de l&#39;exécution du détecteur de modèles. NPR-25036 : correctif pour CQ-4248597
* Les entrées de journal n&#39;ont pas été écrites en raison de NPE dans LogEntryImpl. NPR-25627 : correctif pour Granite-22383
* La réplication du événement de suppression ne vérifie pas les droits. NPR-25679 : correctif pour CQ-4241234
* Prise en charge STARTTLS Ajoutée dans &quot;Day CQ Mail Service&quot;. NPR-25611 : correctif pour CQ-4249924
* Rétroport proactif pour les correctifs granite.platform.login afin d’améliorer l’accessibilité. NPR-25176 : Correctif pour Granite 21746 et Granite-21309
* (AEM 6.4) Erreur lors de la recréation du package et de sa réinstallation. NPR-25173 : correctif pour CQ-4247939
* Suppression de la valeur par défaut MERGE_PRESERVE aclHandling. NPR-24593 : correctif pour Granite-21889
* Content-Type n&#39;est pas proposé et est absent dans la réponse après avoir appliqué le ContentDispositionFilter deux fois. NPR-24175 : correctif pour Sling-7525
* État de Package Manager incorrect après la mise à niveau vers AEM branche 6.4. NPR-24551 : correctif pour Granite-21750
* Instance AMS - L’analyse des journaux d’erreurs est consignée. Correctif pour CQ-4249567

**Sécurité**

* SAML reconnecte les redirections vers la page de déconnexion à l’aide du IDP Okta. NPR-25523 : correctif pour GRANITE-22364
* L’authentification IMS via les configurations OAuth Provider pour IDP externe OAK désactive l’utilisateur créé dans AEM. NPR-25301 : correctif pour Granite-22363

**MAC - Intégration de Test&amp;Target**

* (Ciblage) Erreur de composant de texte lors du ciblage. Correctif pour CQ-4233343

**Communautés**

* (Bibliothèque de fichiers) Le téléchargement de fichiers avec des espaces vides entraîne des problèmes de format. NPR-24260 : correctif pour CQ-4245159
* Correctifs de plusieurs problèmes affectant Adobe Social. NPR-24247 : correctif pour CQ-4245054, CQ-4245120, CQ-4245296
* Le défilement infidèle de la console des membres et des groupes échoue au cas où la publication de l’auteur s’exécuterait sur différents chemins de contexte. NPR-24437 : correctif pour CQ-4246013
* La publication ne revient pas à l’état sans réponse même en supprimant de l’état répondu et le score ne diminue pas. NPR-24419 : correctif pour CQ-4245797, CQ-4245932
* Les événements ajoutés à l’aide de la fonctionnalité de calendrier dans les communautés génèrent des valeurs incorrectes. NPR-24883 : correctif pour CQ-4244056
* (Forum des communautés) Problèmes liés au comportement des clics de pagination et du chargement de page. NPR-24880 : correctif pour CQ-4246109
* (Chrome) Les conversions du fuseau horaire échouent sur les événements des communautés. NPR-24881 : correctif pour CQ-4247115
* Impossible d&#39;afficher l&#39;objet incorporé dans le courrier électronique. NPR-24999 : correctif pour CQ-4248022
* La séquence d’automatisation doit être exécutée lors de la mise à jour UGC en plus de la création UGC. NPR-25892 : correctif pour CQ-4251399
* Réactivité modale de la boîte de dialogue sur les groupes. NPR-25623 : correctif pour CQ-4248805
* Une exception Solr est levée lors de la suppression du contenu. NPR-25869 : correctif pour CQ-4248908
* Les liens paginés vers des threads avec de nombreuses publications ne fonctionnent pas sur les notifications. NPR-25678 : correctif pour CQ-4243038
* Les valeurs d’heure dans les résultats de recherche affichent l’heure du serveur au lieu du fuseau horaire du client. NPR-25594 : correctif pour CQ-4248986
* (Commentaires sur le forum) Le bouton Retour du navigateur ne fonctionne pas comme prévu. NPR-25205 : correctif pour CQ-4248573
* (Résultats de la recherche) Le bouton Retour du navigateur ne fonctionne pas comme prévu. NPR-25214 : correctif pour CQ-4248574
* La valeur Null est renvoyée lors de la superposition du composant community_groupmemberlist. NPR-25228 : correctif pour CQ-4248523
* (Calendrier des communautés) ClassCastException est généré lors de l&#39;enregistrement du événement avec la nouvelle image de couverture. NPR-25167 : correctif pour CQ-4248662
* (Communautés) Messages tronqués. NPR-25326
* (AEM Publish) La ressource Scorm échoue avec le chemin de contexte et affiche un écran vide. NPR-26155 : correctif pour CQ-4251942
* (MSRP) Le nouveau calendrier est enregistré en affichant partiellement NPE dans le journal des erreurs. NPR-26071 : correctif pour CQ-4250531
* La pagination du forum/de la rubrique n’est mise à jour que lorsque la page est actualisée. NPR-26070, NPR-25965 : correctif pour CQ-4249509
* (Forum des questions et réponses) Impossible d’accéder à la page précédente lors de l’ouverture d’un lien direct vers un commentaire. NPR-26069 : correctif pour CQ-4251699
* Le téléchargement d’image dans le groupe Créer ne fonctionne pas sur les périphériques mobiles. NPR-26172 : correctif pour CQ-4251703
* (Messagerie) Lors de l’utilisation de DSRP, le nom du destinataire du message s’affiche toujours sous la forme &quot;Inconnu&quot;. NPR-26056 : correctif pour CQ-4251397
* Le libellé de statut d’achèvement de la ressource Scorm d’activation apparaît vide dans l’interface utilisateur. NPR-26034 : correctif pour CQ-4249994
* Lors de la création d’un nouveau groupe de communauté, un groupe de communauté de duplicata est créé sur un cluster mongoMK principal/principal. NPR-26032 : correctif pour CQ-4245884
* (Auteur) L’assistant de création de groupe prend trop de temps pour charger/créer un groupe dans l’assistant. NPR-26031 : correctif pour CQ-4244966
* Parsys disparaît lors de l’ajout d’une instruction include dans le script hbs. NPR-25908 : correctif pour CQ-4250489
* Si l’option « Autoriser les privilégiés » est arrivée, les membres privilégiés ne devraient pouvoir composer que pour les utilisateurs qui sont membres de la communauté. NPR-25877 : correctif pour CQ-4248450
* Liens profonds bloqués pour activation. NPR-25966 : correctif pour CQ-4251478
* La pagination du forum n’est pas mise à jour de manière dynamique lors de la suppression des réponses. NPR-25970 : correctif pour CQ-4248975, CQ-4252843
* Le défilement et la mise en surbrillance automatiques ne fonctionnent pas sur les événements de calendrier et de fichier en cas de commentaires imbriqués. NPR-25958 : correctif pour CQ-4251471
* (DSRP) Les performances des liens directs/profonds se dégradent avec une grande quantité de contenu généré par l’utilisateur. NPR-25957 : correctif pour CQ-4251470
* Impossible de modifier les propriétés des membres autorisés et des membres privilégiés. NPR-26014 : correctif pour CQ-4244592
* Marquer tout comme lu réinitialise les compteurs de notification pour toutes les pages de la communauté. NPR-25931 : correctif pour CQ-4248612
* La modification des services informatiques échoue pour DSRP. NPR-25929 : correctif pour CQ-4251382
* Echec des services informatiques de messagerie en raison de NPE lors de la création de modèles de courrier électronique. NPR-26039 : correctif pour CQ-4250962
* Problèmes de thread du forum lors de l’incorporation d’images à très haute résolution. NPR-26037 : correctif pour CQ-4244453, CQ-4253099
* L’heure affiche les commutateurs lorsque le fuseau horaire du serveur diffère du fuseau horaire de l’utilisateur. NPR-26036 : correctif pour CQ-4248751
* Le fait de joindre deux fois un fichier portant le même nom à une publication de forum entraîne une erreur du serveur. NPR-24172 : correctif pour CQ-4244367
* Correctifs de performances de Backport : pagination de groupe sur l’auteur et la publication, recherche de groupe sur l’auteur, évitement de la sérialisation des réponses pour le journal, le calendrier et l’idéation et chargement différé pour obtenir un bouton d’adhésion de groupe (invitation/annulation de l’invitation) pour chaque groupe lors de l’affichage de la page de liste des groupes. NPR-24538 : correctif pour CQ-4246515
* Les ressources d’activation ne sont pas visibles sur l’auteur. Correctif pour CQ-4252618
* Les notifications ne sont pas générées pour le thread par l&#39;utilisateur inconnu. Correctif pour CQ-4245132
* La recherche de groupe n’apparaît pas sur le rail de gauche. Correctif pour CQ-4252621
* (Auteur) La pagination ne fonctionne pas pour la console Groupes. Correctif pour CQ-4242786
* Mise à niveau de l’interface utilisateur jQuery. Correctif pour CQ-4248894
* Effectuez la mise à niveau vers la dernière version de SCORM 2017.1. NPR-25675 : correctif pour CQ-4240671
* Les champs &quot;Composer au nom&quot; sont visibles pour les utilisateurs non membres de la communauté. NPR-25331 : correctif pour CQ-4247858
* La publication est toujours visible dans l’interface utilisateur, même après suppression, et affiche une erreur sur la console. NPR-26290 : correctif pour CQ-4252803
* (Paramètres du site) Impossible d&#39;enregistrer les modifications apportées aux rôles. NPR-26274 : correctif pour CQ-4252187
* (Vulnérabilité de sécurité) Prise en charge du compte en raison d’une erreur de configuration du jeton Web JSON. NPR-26458 : correctif pour CQ-4253314
* La pagination n&#39;est pas réinitialisée lors de la suppression des réponses. NPR-26326 : correctif pour CQ-4252997
* L’image de pièce jointe ne s’affiche pas dans les versions préliminaires lors de la modification. Correctif pour CQ-4253360
* La page n’est pas actualisée lors de l’ajout de pièces jointes dans la base de données relationnelle (DSRP). Correctif pour CQ-4253084
* Les groupes ne fonctionnent pas dans la ressource du site d&#39;activation. Correctif pour CQ-4252975
* Conditions préalables Les chemins d’apprentissage ne sont pas conservés dans Activation. Correctif pour CQ-4252948

**Processus**

* L’interface utilisateur du lanceur de flux de travail n’affiche pas les configurations de lanceur antérieures à la limite 41 et déclenche une erreur javascript dans la console. NPR-25028 : correctif pour CQ-4247604
* La modification d’un processus hérité sans modifier son lanceur entraîne la création de plusieurs workflows sur tout processus contenant une étape Activer la page/le fichier. NPR-25870 : correctif pour CQ-4250896
* Lien incorrect dans la charge utile du processus si la page comporte un noeud de métadonnées. NPR-25916 : correctif pour CQ-4250733

**Traduction**

* Correction du fait que l&#39;importation d&#39;un projet traduit faisait deux demandes de POST simultanées, ce qui provoquait des erreurs. NPR-24889 : correctif pour CQ-4247638
* Correction du fait que lors de la création d’un projet de traduction pour plusieurs langues, toutes les pages pour la même langue étaient ajoutées à la même tâche. NPR-25091 : correctif pour CQ-4246112
* Correction du problème qui, dans certains cas, ne faisait liste que les 40 premières pages de la tâche de traduction. NPR-25974 : correctif pour CQ-4248661
* Composant DataPicker (Coral2) ne modifiant pas l’année. NPR-24466 : correctif pour Granite-21893

**IU - Fondation**

* Rétroportages proactifs de l’interface utilisateur de Foundation. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-2599 35, NPR-25976
* (Importateur de conceptions) L’importation d’une page n’importe pas les js, css. NPR-25203 : correctif pour Granite-22236
* Prise en charge proactive de l’interface utilisateur de Foundation pour améliorer la stabilité du produit. NPR-24334

**MAC - Intégration de Test&amp;Target**

* La deuxième page de l’Assistant Personnalisation ( lancée par &quot;Ciblage de Début&quot; ) est vide et renvoie des erreurs de console. Correctif pour CQ-4253277

**Fragments d’expérience**

* Fragments d’expérience fusionnés/Intégration de Cibles à AEM 6.4.2.0. Correctif pour CQ-4248653

**Gestion des fragments de contenu**

* Annotations de fragments de contenu et comparaison côte à côte des versions de fragments de contenu. Correctif pour CQ-4247148

**DAM - Général**

* Le filtre &quot;Extrait par&quot; ne fonctionne pas correctement dans la recherche. Correctif pour CQ-4247070
* Lors de la mise à jour de la ressource, la copie de langue de la ressource et sa miniature deviennent vides. Correctif pour CQ-4250641
* Duplicata-id : La valeur de l’attribut id doit être unique. Correctif pour CQ-4250905
* Libellé : Les éléments de formulaire doivent avoir des libellés. Correctif pour CQ-4250906
* Nom du lien : Les liens doivent présenter un texte perceptible. Correctif pour CQ-4250907
* JMX de migration du modèle de métadonnées du dossier de ports et ServiceUserMapping. Correctif pour CQ-4252947
* WebdriverIO Tests non exécutés dans la branche release/640 de CQ/dam. Correctif pour CQ-4252749
* Les liens vers les ressources déplacées ne sont pas refactorisés si le lien est publié. Correctif pour CQ-4245756

**DAM - Visionneuses**

* Erreur intermittente lors du chargement de la vidéo avec les nouvelles visionneuses 5.10.1. Correctif pour CQ-4250562

**Portail de marque DAM**

* L’annulation de la publication de la collection à partir du portail de marque échoue avec une erreur. Correctif pour CQ-4245990
* Impossible d&#39;annuler la publication des paramètres d&#39;image prédéfinis à partir de Brand Portal. Correctif pour CQ-4246140
* Les sous-ensembles d’un fichier pdf de plusieurs pages ne sont pas publiés lorsqu’un fichier est publié. Correctif pour CQ-4245162

**DAM - DMClient**

* Lors de la publication d’un fichier vidéo sur YouTube, les balises qui en résultent sur YouTube incluent le chemin complet de la balise. Correctif pour CQ-4245549
* (Mises à niveau d’exclusion et d’inclusion) Problème de redirection CSS du lecteur de contenu. Correctif pour CQ-4247854
* Impossible de créer/modifier le paramètre prédéfini de visionneuse en tant que non membre du groupe &quot;administrateurs&quot;. Correctif pour CQ-4247618
* (6.4.1.0) Ajouter plusieurs vidéos dans plusieurs paramètres interrompt le lecteur vidéo. Correctif pour CQ-4248517
* Le fait de renommer et de déplacer un fichier dans une visionneuse d’images rend la modification impossible. Correctif pour CQ-4248434
* La publication de vidéos volumineuses sur YouTube envoie des messages d’expiration. Correctif pour CQ-4237831
* (Vue de Liste) L’interface utilisateur du sélecteur/sélecteur de ressources est entièrement grise et désactivée pour l’utilisateur. Correctif pour CQ-4237817
* (Zoom vertical) Le chargement du fichier CSS échoue avec une erreur 404. Correctif pour CQ-4236508
* Si vous tentez de télécharger un fichier avec un pourcentage (%) dans le nom du fichier, l’archive est vide. Correctif pour CQ-4250558
* (Vue de carte) Aucun indicateur de traitement n’est affiché lors de l’utilisation de la fonction Copier et Coller sur une ressource vidéo. Correctif pour CQ-4249037
* (Mise à niveau de la version 6.3.2 vers la version 6.4) Les paramètres d’image prémise à niveau s’affichent sous la forme &quot;Non publié&quot; sur la page Rendus, mais ne renvoient pas de bouton URL lorsqu’ils sont sélectionnés. Correctif pour CQ-4240406
* Améliorations techniques de la dette/des éléments mineurs. Correctif pour CQ-4240648
* Le sélecteur de ressources (ou Sélecteur de ressources) n’affiche pas tous les fichiers des dossiers disponibles. Correctif pour CQ-4218414
* Le paramètre d’image prédéfini sans hauteur affiche les images dont la taille est incorrecte. Correctif pour CQ-4246546
* (Ressources multipages) L’interface utilisateur se casse lorsque vous cliquez sur les annotations. Correctif pour CQ-4251434
* En passant de la version 6.3 à la version 6.4 et ultérieure du paramètre prédéfini Analytics, un nouveau paramètre prédéfini de suite de rapports et d’analyses est créé, ce qui entraîne la perte des données de rapports plus anciennes de l’utilisateur. Correctif pour CQ-4244529
* (Assistant Gestion de la publication) La Liste des ressources semble vide lors de la tentative de publication ou d’annulation de publication. Correctif pour CQ-4251881
* Lorsque vous choisissez des visionneuses après avoir consulté les membres de la visionneuse, la lecture des vidéos AVS échoue. Correctif pour CQ-4205308
* Un nouveau paramètre prédéfini de codage vidéo ne peut pas être ajouté aux paramètres prédéfinis de traitement vidéo avant la mise à niveau, ni modifier les paramètres prédéfinis de codage existants. Correctif pour CQ-4240407
* Les paramètres d’image prédéfinis ne sont pas appliqués aux rendus dynamiques téléchargés. Correctif pour CQ-4249862
* Le bouton Sélectionner tout ne fonctionne pas correctement sur la page de liste des paramètres prédéfinis de la visionneuse. Correctif pour CQ-4252462
* Profils vidéo : Le bouton Sélectionner tout n’est pas fonctionnel. Correctif pour CQ-4253076, CQ-4251447
* Passe de validation SP2 - Passe de fumée. Correctif pour CQ-4251639

**DAM - DMServices**

* La génération de rendus Dynamic Media a échoué pour le fichier EPS. Correctif pour CQ-4243688

**Granite**

* Un type dans le lot SymbolicName conduit à un lot de duplicata. Correctif pour Granite-22155
* CUGConfiguration ne peut pas récupérer CugExclude. Correctif pour Granite-21109
* Redémarrage de l&#39;Adobe Granite Workflow Core (Noyau de flux de travaux granitiques) réexécute les étapes du processus à partir du milieu, créant des workflows inutiles. NPR-25057 : correctif pour Granite-22218
* JcrResourceBundle ne prend pas correctement en charge plusieurs noms de base. NPR-25245 : correctif pour Granite-22317
* Lors de l’installation des packages de contenu, les ACL sont regroupées par entité de sécurité, ce qui rompt le modèle d’autorisation. NPR-24583 : correctif pour Granite-21591
* Mettez Jetty à jour vers la version 9.4.11 pour corriger les vulnérabilités. NPR-25030 : correctif pour Granite-22120

**Formulaires**

Les principaux points forts d&#39;AEM Forms 6.4.2.0 sont les suivants :

* Nouvelle propriété Ajoutée pour la mise à jour des files d’attente sans actualiser le navigateur.
* Capacité Ajoutée de l’utilisateur d’utiliser le même fichier WSDL pour plusieurs services.
* Suppression du modèle d’horodatage non pris en charge dans la liste déroulante datepicker.
* Prise en charge Ajoutée de la sous-couche xfaf et pdf dans OSGI.
* Prise en charge Ajoutée de l&#39;utilisation de la fonctionnalité [rapports de transactions](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) dans les déploiements sur site.
* Code Ajouté pour ne pas afficher la variable enfant dans l’éditeur de règles de condition.

**Package de modules complémentaires Forms**

**Rapports de transaction**

* Mettez à jour la configuration du Rapports de transactions avec l’importance de la réplication inversée configurée sur un serveur de publication. NPR-26050 : correctif pour CQ-4246650
* Initialisation différée de la tâche de vidage périodique. NPR-25968 : correctif pour CQ-4245024
* Échec de l&#39;enregistrement des transactions avec une exception Null Pointer. Correctif pour CQ-4247302

**Forms - Workflow**

* (Workspace HTML) Lorsqu’un utilisateur demande une tâche, le nombre de files d’attente est actualisé pour cet utilisateur particulier, mais pas pour les autres utilisateurs, sauf si la page est actualisée. Ce problème a été corrigé par une nouvelle propriété. Pour configurer cette nouvelle propriété sur votre instance AEM, consultez ses Paramètres de configuration. NPR-24536 : correctif pour CQ-4233665
* Impossible de charger un formulaire volumineux dans l&#39;application AEM Forms sur la version 6.4. NPR-24463 : Correctif pour CQ-4245091
* Problème dans l’application Mobile Workspace lors de la tentative de vue de la tâche partagée. NPR-25177 : correctif pour CQ-4248733
* Comportement de validation incohérent entre Web et APK. NPR-25670 : correctif pour CQ-4248178
* Lorsqu’un appel à un service Web est effectué, un formulaire HTML5 ouvert dans le client échoue et un message d’erreur est renvoyé. NPR-26048 : correctif pour CQ-4244716
* Problème lors de l&#39;appel du service dans AEM Forms Application Windows 6.3. NPR-26468 : Correctif pour CQ-4252341

**Forms mobile**

* (Jeu de formulaires) Problème de validation des champs SSN et Mobile lors de la prévisualisation. NPR-24458 : correctif pour CQ-4244983
* Les données ne s’affichent pas avec le préremplissage de champs multilignes dans la prévisualisation HTML. NPR-24549 : correctif pour CQ-4244212
* Les données se perdent lorsque le script est évalué sur un champ multiligne. NPR-25333, Correctif pour CQ-4249610

**Forms - Communication interactive et gestion de correspondance**

* Échec de la synchronisation sur IC avec modèle de base et modèle d&#39;impression IC de référence. NPR-24912
* (CCR) Les validateurs ne fonctionnent pas pour les champs/variables. Correctif pour CQ-4245047
* L’icône Objet de modèle de données disparaît par intermittence sur la barre d’outils Edition de texte. Correctif pour CQ-4245122
* Les journaux des exceptions s’affichent sur l’IC copiée si l’IC d’origine est supprimé. Correctif pour CQ-4249378
* Dans le rendu de lettre, la condition n’est pas évaluée sur true même si les données sont correctes. Correctif pour CQ-4245944
* Les composants générés automatiquement ne sont pas mis en surbrillance lors de la sélection dans l’arborescence de contenu. Correctif pour CQ-4246178
* Problèmes lors de l’ouverture de l’éditeur de modèles de Canal Web. Correctif pour CQ-4248182
* Impossible de modifier l’ordre des actifs ajoutés car les flèches vers le haut/vers le bas restent désactivées. Correctif pour CQ-4252042
* Impossible de mettre à jour les propriétés du module Condition. Correctif pour CQ-4247909
* UX de la boîte de dialogue &quot;Annuler l&#39;héritage&quot; lorsque l&#39;utilisateur réorganise un objet dans le Canal Web doit être amélioré. Correctif pour CQ-4241076
* Les données de la lettre correspondant aux liaisons définies dans XDP ne sont pas renseignées à l’aide de l’URL de lettre directe. Correctif pour CQ-4245833
* (Problème de mise en cache) La synchronisation du canal Web ne reflète pas les modifications apportées aux fragments de mise en page, fragment de texte du canal d’impression. Correctif pour CQ-4251460
* Impossible de mettre à jour les propriétés de fragment de mise en page et de dictionnaire de données. Correctif pour CQ-4247830
* (CCR) Le rechargement du brouillon échoue en raison de l’analyse XML. Correctif pour CQ-4250950
* (Editeur IC) Le bouton &quot;Modifier le fragment&quot; doit être plus visible. Correctif pour CQ-4244694
* (XDP) Un écran vide s’affiche lors de l’ajout d’un fragment de mise en page dans le nouveau sous-formulaire créé. Correctif pour CQ-4248810
* Échec du test de DocumentFragment-master-DeployWithServerSideTests. Correctif pour CQ-4245496
* Variable de module de texte Instance dupliquée dans le module de condition. Correctif pour CQ-4252128
* L’URL de la prévisualisation PDF n’affiche pas le rapports de transaction lors de la publication. Correctif pour CQ-4246158
* Problèmes liés à IC Sync avec la synchronisation Canal d&#39;impression sur Canal Web. Correctif pour CQ-4251505
* ExM Code clean : Supprimez LocalFunctionMapper. Correctif pour CQ-4243265
* Pour corriger le type de ressource de TableHeader du composant de table webChannel d&#39;IC. Correctif pour CQ-4251821
* (Éditeur IC) Problèmes de convivialité. Correctif pour CQ-4241081
* Le sous-formulaire Imprimer le canal n’affiche pas la fonctionnalité d’insertion. Correctif pour CQ-4252994
* Échec de la synchronisation des modifications après la suppression du noeud FDM ou de l&#39;espace réservé de variable. Correctif pour CQ-4253178
* (Editeur de modèle) Le modèle de base affiche les zones de glisser-déposer supplémentaires de l’en-tête/pied de page et les scintillements d’écran à l’ouverture du Canal Web. Correctif pour CQ-4253323
* Les composants générés automatiquement ne sont pas mis en surbrillance lors de la sélection dans l’arborescence Contenu. Correctif pour CQ-4246178

**Services de document**

* (Form Service) OSGI ne prend pas en charge XFAF. NPR-25181, Correctif pour CQ-4251313
* Les caractères de l’en-tête du fichier PDF assemblé commencent à être altérés. NPR-25113 : correctif pour CQ-4244682

**Formulaires adaptatifs**

* L’action Envoyer comme envoi de courrier envoie une exception avec les champs CC/BC vides. NPR-25019 : correctif pour CQ-4243039
* Impossible d&#39;utiliser le composant Formulaire d&#39;AEM prête à l&#39;emploi en raison d&#39;une requête inefficace. NPR-25065 : correctif pour CQ-4247256
* Supprimez sling:orderBefore des noeuds de boîte de dialogue de guideImageChoiceComponent. Correctif pour CQ-4245013
* (Sélecteur de date) Le modèle de saisie ne prend pas en charge deux types de modèle d’horodatage. Correctif pour CQ-4237982
* Envoyer une action en utilisant les problèmes de création classique &quot;Forms Workflow&quot;. Correctif pour CQ-4236981
* (Canal Web) IC Chart doit hériter de la propriété colspan du graphique AF. Correctif pour CQ-4252143

**Intégration du serveur principal**

* (Demandes SOAP) Les décimales volumineuses (plus de 6 chiffres) sont représentées par une notation exponentielle, ce qui entraîne une erreur de validation. NPR-25283 : correctif pour CQ-4248100
* Validation incorrecte des paramètres facultatifs définis dans des types complexes. NPR-25070 : correctif pour CQ-4247107
* Capacité Ajoutée de l’utilisateur d’utiliser le même fichier WSDL pour plusieurs services. NPR-24604, Correctif pour CQ-4247756
* FDM mélange l&#39;ordre des paramètres dans ses appels SOAP. NPR-25069, Correctif pour CQ-4247180
* FDM fusionne des entités (dans Liste/tableau) dans la demande SOAP. NPR-25284 : correctif pour CQ-4248375

**Programme d’installation de Forms JEE**

**Service PDFG**

* La fonction de création/modification des paramètres de sécurité ne fonctionne pas. NPR-24769 : correctif pour CQ-4246927
* Optimize PDF en désincorporant sélectivement les polices via un appel d’API unique. NPR-23287

**Services de document**

* Output Service ne fournit pas les balises correctes pour le Reader d’accessibilité. NPR-24438, NPR-24439, NPR-24440, NPR-24441 : Correctif pour CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Document Security**

* Problème de création de stratégie à l&#39;aide de la sécurité des Documents. NPR-25586, NPR-25547 : correctif pour CQ-4247086

**Forms - Foundation JEE**

* Processus s’exécutant en tant que compte de contexte système par intermittence. NPR-25289, NPR-25313 : correctif pour CQ-4249331
* AEM Forms JEE affecté par Apache Struts et l’alerte de sécurité de liaison de données Jackson. NPR-25628 : correctif pour CQ-4242891
* Le processus de point de début de courriel ne fonctionne pas. NPR-25253 : correctif pour CQ-4248518

**Packs de fonctionnalités inclus**

**Ressources**

* Intégration [Ajoutée avec Adobe Stock](/help/assets/aem-assets-adobe-stock.md) afin que les utilisateurs puissent rechercher, prévisualisation, enregistrer et mettre sous licence des actifs Adobe Stock directement à partir de l’interface utilisateur AEM. Pour plus d’informations, voir [Utilisation d’actifs Adobe Stock avec des actifs AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html). NPR-15779 : correctif pour CQ-30857
* Prise en charge Ajoutée de la métaschie conditionnelle dynamique. Pour plus d’informations, voir [Métadonnées en cascade](/help/assets/cascading-metadata.md). NPR-25189 : correctif pour CQ-4237413
* Activation de l’option &quot;Téléchargement de fichier&quot; sur les fragments de contenu. Pour plus d’informations, voir [Rapports sur les ressources](/help/assets/asset-reports.md). NPR-25186 : correctif pour CQ-4237410
* Possibilité de définir un schéma de métadonnées pour les dossiers de fichiers. Pour plus d’informations, voir [Schéma de métadonnées de dossier](/help/assets/folder-metadata-schema.md) et voir ses [Paramètres de configuration](#configuration-settings-required-for-npr) après l’installation AEM 6.4.2.0. NPR-21268 : correctif pour CQ-4221574

**Sites**

* Permet de modifier un fragment de contenu sans autorisation de suppression. Pour plus d’informations, voir [Personnalisation et extension des fragments de contenu](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-delete.html). NPR-25793 : correctif pour CQ-4248750
* Ajouté la capacité d’annoter des fragments de contenu. Pour plus d’informations, voir [Variations-Création de fragments](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment). NPR-25188 : correctif pour CQ-4235336
* Versioning : Comparaison des fragments de contenu côte à côte. Pour plus d’informations, voir [Gestion des fragments de contenu](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions). NPR-25187 : correctif pour CQ-4237412
* Améliorations apportées à l’éditeur d’images reportées à AEM 6.4.2.0. Pour plus d’informations, voir [Éditeur d’images](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24467

**Unités OSGI et packages de contenu inclus**

Liste des lots OSGi inclus dans AEM 6.4.2.0

[Obtenir le fichier](assets/6.4.2.0_bundle-list.txt)

Liste des packages de contenu inclus dans AEM 6.4.2.0

[Obtenir le fichier](assets/6_4_2_0content-package-list.txt)

#### aem 6.4.1.0 {#experience-manager-6410}

aem 6.4.1.0 est une mise à jour importante qui comprend des améliorations et correctifs concernant les performances, la stabilité, la sécurité et les clients clés depuis la publication de l’AEM 6.4 en avril 2018.

aem 6.4.1.0 peut être installé sur AEM 6.4 GA. Voici les principales caractéristiques du Service Pack 1 :

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.3.
* Ajout de balises actives améliorées.
* Correctifs dans le sélecteur de conception, le sélecteur de balises (remplacez la machine virtuelle source et la machine virtuelle de cible par auto.)
* Prise en charge Ajoutée de typeHint pour enregistrer les valeurs sous forme de chaîne.
* Prise en charge Ajoutée de SMTP sur TLS dans le service de messagerie.
* Correctif de gestion du proxy pour le transfert HTTP dans DMS7.
* Mise à jour vers /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js version 1.3.
* Correctifs dans les packages d’exclusion et d’inclusion DMHybrid.
* Correctifs dans la recadrage dynamique.
* Migration des valeurs de configuration OOTB vers le nouvel emplacement ( de /etc à /conf).
* Profils de couleur Ajoutés aux paramètres du client sur les serveurs de diffusion.
* Migration des paramètres d’Image Server à partir de /etc —&amp;gt; /conf.
* Fragment de contenu source Ajouté pour traduction.
* Prise en charge Ajoutée de ARIA pour Print et PrintDialog.
* Prise en charge Ajoutée de la validation de courrier électronique ARIA.
* Backport proactif pour les correctifs de platform.clientlibs.
* Prévention de l’exécution automatique des scripts lorsqu’il n’y a pas d’entrée au type de données explicite (résout CVE-2015-9251).

**Ressources**

* La valeur de liste déroulante en cascade s’affiche vide lors de la réouverture de la page des propriétés de la ressource. NPR-23042 : correctif pour CQ-4238761
* Les liens partagés sur la page mylinkshare et les liens vers la page ne sont pas disponibles pour l&#39;utilisateur non-administrateur NPR-23044 : Correctif pour CQ-4239004
* Pour éviter une exception de pointeur nul dans le flux de travaux de mise à jour des ressources DAM de la version 6.4.0. NPR-24134 : Correctif pour CQ-4244972
* La page WCM publiée affiche des icônes d’espace réservé pour la zone réactive, des fichiers CSS manquants avec l’erreur 403 pour les visionneuses prêtes à l’emploi. NPR-23041 : correctif pour CQ-4233716
* (Vue des détails) La fonction de navigation suivante/arrière laisse une incrustation DIV dans la zone de prévisualisation de rendu dynamique qui bloque l’accès à la visionneuse. NPR-23043 : correctif pour CQ-4238499
* La saturation du rendu d’image CMJN est incorrecte. NPR-23048 : correctif pour CQ-4235470
* L&#39;extraction de métadonnées XMP par Scene7ListInfoProvider est gourmande en ressources. NPR-23754
* (diffusion-barrage) Le redirecteur HTTP ne respecte pas les paramètres du proxy HTTP. NPR-24002 : correctif pour CQ-4244140

**Sites**

* Lorsque nous renommons la page pendant que nous la déplacons, le déplacement de la page a réussi, mais la fonctionnalité de changement de nom ne fonctionne pas. NPR-22923 : correctif pour CQ-4235907
* Erreur lors de la publication d’une page Live Copy qui pointe vers une page d’importateur dans Adobe Campaigns. NPR-23053 : correctif pour CQ-4237164
* Le déplacement/changement de nom dans l’interface utilisateur classique échoue avec l’erreur &quot;Une erreur s’est produite lors du déplacement de la page&quot; et n’est pas renommée. NPR-23051 : correctif pour CQ-4235907
* Le passage d’une vue de colonnes à une vue de liste génère une page vierge et déclenche une exception de pointeur nul pour les pages dont la valeur OffTime est définie et OnTime vide. NPR-22968, NPR-23052 : correctif pour CQ-4238940

**Commerce**

* Correction de la casse des hobbes principaux d&#39;échec (module CQ/Commerce). Correctif pour CQ-4253494

**Vulnérabilité**

* L’intégration de Salesforce est vulnérable aux attaques SSRF (Server Side Request Forgery). NPR-24289 : correctif pour CQ-4245277
* SSRF (Server Side Request Forgery) et XSS (Cross-Site Scripting) dans ReportingServicesProxyServlet. NPR-24657 : correctif pour CQ-4246880
* Script intersite (XSS) : Reflété dans le catalogue électronique de création de commercewizard.html/content. NPR-24642 : correctif pour CQ-4237017
* Cross-site scripting (XSS) dans les liens des Projets de l’IU d’administration. NPR-23272 : correctif pour CQ-4241795

**WCM - Composants Foundation**

* L’ouverture du sélecteur de conception entraîne une exception de pointeur nulle. NPR-23047 : correctif pour CQ-4238736

**Interface utilisateur**

* (Coral3 Datepicker) Ajoutez la prise en charge de typeHint pour enregistrer les valeurs sous la forme &quot;String&quot;. NPR-23398 : correctif pour Granite-21194
* La traduction de l’internationalisation ne fonctionne pas au niveau de la langue. NPR-22967, NPR-23046 : Correctif pour Granite-21111
* Prise en charge proactive des granite.ui.com de mise à jour. NPR-23537
* Prise en charge proactive pour les granite.ui.co de contenu. NPR-23535
* Prise en charge proactive pour les granite.ui.co de ralui. NPR-23538
* Impossible de supprimer plusieurs utilisateurs du groupe à la fois. NPR-23846
* (OMEGA) Rapport &quot;Feature&quot; en anglais uniquement. NPR-23989 : correctif pour Granite-21231
* (Importateur de conceptions) L’importation d’une page n’importe pas les js, css. NPR-25203 : correctif pour Granite-22236

**Intégration**

* Résolveur de ressources non fermé dans com.day.cq.analytics.sitecatalyst. NPR-22340 : correctif pour CQ-4236515
* TargetContentImpl ralentit AEM pendant les requêtes longues. NPR-22359 : correctif pour CQ-4236907
* Le moteur Target (mbox.js, at.js) n’utilise pas d’URL mal formées et utilise des URL contenant deux-points qui peuvent rencontrer des problèmes avec certains déploiements. NPR-22434 : correctif pour CQ-4237854
* En mode Target, les auteurs peuvent modifier un composant hérité du plan directeur sans annuler l’héritage. NPR-22865 : correctif pour CQ-4237907
* (Personnalisation) Les icônes sont déformées lors du passage à la vue de carte. NPR-23373, NPR-23374 : correctif pour CQ-4240018, CQ-4240019
* (Personnalisation) La console d’Audience n’affiche pas les types nt:folder. NPR-23375 : correctif pour CQ-4242293
* Lorsqu’un composant est ciblé sur une instance de publication, le scintillement s’affiche, affichant l’expérience par défaut avant l’expérience ciblée. NPR-23415 : correctif pour CQ-4242038
* (Adobe de la console IMS) La configuration du service OSGi AccessTokenProvider réapparaît après suppression. NPR-23520 : correctif pour CQ-4208250
* La réplication de référence de configuration échoue avec la structure de dossiers intermédiaire. NPR-23485 : correctif pour CQ-4242751
* (Personnalisation) clientlib bloquée par la servlet proxy. NPR-23521 : correctif pour CQ-4240995
* (Adobe IMS Console) Les solutions cloud enregistrées ne sont pas reprises dans l’assistant de configuration. NPR-23977 : correctif pour CQ-4244549
* Boucle infinie lors du chargement de contenu ciblé sur des pages sans extension HTML. NPR-23522 : correctif pour CQ-4223600
* L’Activation échoue pour une page avec les références de configuration de la gestion dynamique des balises héritées. NPR-23485 : correctif pour CQ-4242751

**Plate-forme**

* (IU classique) (interface utilisateur tactile) Le sélecteur de balises ne s’affiche pas et renvoie une exception lors de la recherche de balises par le biais d’un prédicat de balises dans le schéma de recherche de ressources. NPR-23049 : correctif pour CQ-4239371
* (IU classique) Les composants utilisant xtype=tags renvoient la valeur null et ne peuvent pas être sélectionnés à partir de la liste de balises eth. NPR-23050 : correctif pour CQ-4239937
* (Identité graphique) La boîte de dialogue d’inclusion mentionne Adobe Marketing Cloud au lieu de Adobe Experience Cloud. NPR-23210 : correctif pour CQ-4237799
* L&#39;option Filtre rend l&#39;AEM lenteur après la mise à niveau de 6.3 à 6.4. NPR-23260 : Correctif pour CQ-4239847 (à vérifier)
* Backport proactif pour les correctifs granite.omnisearch.core. NPR-23536
* Backport proactif pour les correctifs de platform.clientlibs. NPR-23569
* Héritage de la configuration du Cloud Service rompu lors de la modification d’autres propriétés de page. NPR-23216 : correctif pour CQ-4239782
* Activation de la prise en charge de STARTTLS dans le service de messagerie Day CQ. NPR-23941 : correctif pour CQ-4240397

**Projets**

* (Fragment de contenu) La copie de langue de la ressource incorporée n’est pas créée alors que la ressource en anglais est ajoutée à la traduction. Correctif pour CQ-4243477
* La liste déroulante de configuration msft affiche la configuration de /libs(6.4 configs) au lieu de /etc(6.3 configs) en mode hérité. Correctif pour CQ-4243475
* Promouvoir et supprimer automatiquement les lancements de traduction dans les projets de traduction. Correctif pour CQ-4243474
* Fragment de contenu dans les sites qui n’est pas traduit. Correctif pour CQ-4243482, CQ-4243483, CQ-4245687
* Erreur du serveur lors de l&#39;ouverture du filtre de recherche de tâche de traduction. Correctif pour CQ-4236813
* La liste déroulante de configuration des informations d’identification est vide même si tif est présent dans /conf/we-commerce. Correctif pour CQ-4236315
* Open Project KPI : dégradation des performances au fur et à mesure de la création de nouveaux projets. NPR-23840 : correctif pour CQ-4238392
* Workflow Starter ne peut pas accepter la valeur TypeHint de String. NPR-23863 : correctif pour CQ-4238356

**Communautés**

* Vulnérabilités de sécurité dans la version 1.0 de Handlebars. NPR-23636 : correctif pour CQ-4243055
* L&#39;autorisation en bloc des messages marqués ne fonctionne pas. NPR-23867 : correctif pour CQ-4243962
* La valeur par défaut ne s’affiche pas sur le bouton de tri dans le composant de forum. NPR-23882 : correctif pour CQ-4243375
* Problèmes liés à la diffusion des messages des sites communautaires vers les groupes. NPR-23935

**Processus**

* Le service de notification par courrier électronique de flux de travaux Day CQ déclenche un e-mail par noeud Mongo pour les notifications WorkflowCompleted et WorkflowAborted. NPR-22515 : correctif pour CQ-4238172
* L’exécution du processus de mise à jour de la ressource DAM génère une exception NullPointerException. NPR-23010 : correctif pour Granite-21096
* L’étape Processus de workflow n’affiche pas les scripts de /etc/workflow/scripts. NPR-23263 : correctif pour Granite-20775
* L’étape du participant dynamique de processus n’affiche pas les scripts de /apps/workflow/scripts. NPR-23464 : correctif pour Granite-21276
* Impossible de modifier un flux de travail après l&#39;avoir modifié une fois. NPR-23742 : correctif pour CQ-4238526
* (Interface utilisateur classique) Lors de la modification des lanceurs de processus, les conditions disparaissent et les workflows se lancent sans conditions. NPR-23835 : correctif pour CQ-4239153
* Boîte de réception du projet : le passage à la vue de calendrier affiche le contenu de la boîte de réception principale. NPR-23947 : correctif pour CQ-4241236
* Vous devez exposer les détails de la charge utile dans le lot afin que le composant HTML puisse afficher la valeur dans la vue de liste. NPR-23948 : correctif pour CQ-4240953
* Impossible de stocker les données de boîte de dialogue dans l&#39;étape Participant de la boîte de dialogue. NPR-23965 : correctif pour CQ-4234123
* (Interface utilisateur tactile) Lors de l’enregistrement d’un modèle de processus, le bouton &quot;Synchroniser&quot; devient &quot;Synchronisé&quot;, ce qui entraîne une faute d’orthographe. Correctif pour CQ-4244843
* Boîte de réception du projet : le passage à la vue de calendrier affiche le contenu de la boîte de réception principale. Correctif pour CQ-4244436
* Impossible de sélectionner les boîtes de dialogue à l&#39;étape Participant de la boîte de dialogue. Correctif pour CQ-4244532
* Backport proactif pour les correctifs granite.omnisearch.core. NPR-23536
* Problème dans l’application Mobile Workspace 6.4 avec Tâche partagée. NPR-26383

**WCM - Traduction**

* (Panneau de référence) Les tâches de traduction ne sont pas exécutées lors de la création du projet. Correctif pour CQ-4245327

**WCM - MSM**

* (MSM) Amélioration des performances du déploiement. Correctif pour CQ-4231488
* (MSM) Délai d’attente dans l’écoute des Événements entre le événement en cours et la gestion des événements. Correctif pour CQ-4227766

**Screens**

* Échec de la page d&#39;écran avec une erreur en raison de dépendances manquantes pour screens-core-pkg:1.4.42. Correctif pour CQ-4245918

**Projets - Traduction**

* (Fragment de contenu) La copie de langue de la ressource incorporée n’est pas créée alors que la ressource en anglais est ajoutée à la traduction. Correctif pour CQ-4243477
* La liste déroulante de configuration msft affiche la configuration de /libs(6.4 configs) au lieu de /etc(6.3 configs) en mode hérité. Correctif pour CQ-4243475
* Promouvoir et supprimer automatiquement les lancements de traduction dans les projets de traduction. Correctif pour CQ-4243474
* Fragment de contenu dans les sites qui n’est pas traduit. Correctif pour CQ-4243482, CQ-4243483, CQ-4245687
* Erreur du serveur lors de l&#39;ouverture du filtre de recherche de tâche de traduction. Correctif pour CQ-4236813
* La liste déroulante de configuration des informations d’identification est vide même si tif est présent dans /conf/we-commerce. Correctif pour CQ-4236315

**Gestion des fragments de contenu**

* La suppression du composant remplit les journaux avec des traces de pile. Correctif pour CQ-4242315

**DAM - Général**

* La fermeture de la vue détaillée d’un fichier revient à une page de résultats de recherche incorrecte. Correctif pour CQ-4240960
* (Camera Raw) L’option de réglage de l’image est manquante. Correctif pour CQ-4246121
* IndexOutOfBoundsException : Rapport Modification des ressources prêtes à l&#39;emploi. Correctif pour CQ-4239744
* Supprimez le score de confiance du rapport csv. Correctif pour CQ-4241491
* Diffusion de messagerie de partage de lien rompue pour l’expéditeur non &quot;administrateur&quot;. Correctif pour CQ-4240357
* Résolution des problèmes informatiques. Correctif pour CQ-4249891

**DAM - Portail de marque**

* Propriétés de la ressource liste uniquement 3 propriétés sur le premier onglet, toutes les onglets semblent vides. Correctif pour CQ-4242503
* Les prédicats de type de fichier et de taille de fichier ne sont pas disponibles dans le formulaire de recherche publié. Correctif pour CQ-4242026
* La recherche dans le prédicat d&#39;annuaire doit être filtrée/non affichée dans les filtres de recherche. Correctif pour CQ-4241386
* La recherche par défaut à partir de doit exister après l’annulation de la publication. Correctif pour CQ-4241383, CQ-4241113
* Le mouvement Publier sur le portail de la marque ne fonctionne pas pour les paramètres d’image prédéfinis. Correctif pour CQ-4241074
* La publication sur le portail de marque ne fonctionne pas pour les collections. Correctif pour CQ-4241122, CQ-4246558

**DAM - Client DM**

* La mise à niveau vers la version 6.4 supprime les profils de codage vidéo précédemment créés. Correctif pour CQ-4244067
* L’attribut Texte de remplacement est rompu dans le composant Dynamic Media. Correctif pour CQ-4244081
* (DMS7) La modification d’ensembles distants dans AEM n’est pas remplacée dans Scene7. Correctif pour CQ-4243430
* Vérification de la version 6.4 SP1 sur DM Hybrid. Correctif pour CQ-4244623
* (DMS7-UA) Lorsque vous cliquez sur le bouton Incorporer d’une ressource vidéo publiée, rien ne semble se produire. La boîte de dialogue Incorporer s’affiche normalement avec du code HTML. Correctif pour CQ-4245237
* (hybride DM) Copier l’URL pour les fichiers vidéo ou les visionneuses de supports variés publiés reçoit &quot;`[object Object]`&quot; dans la boîte de dialogue URL. Correctif pour CQ-4245236, CQ-4245451
* (DMHybrid) La page Détails de la vidéo ne contient pas la prévisualisation de l’affichage des fichiers vidéo et génère un message d’erreur dans la console. Correctif pour CQ-4244320
* Encodage S7 automatique du contenu we.commerce. Correctif pour CQ-4242253
* Un nouveau paramètre prédéfini de codage vidéo ne peut pas être ajouté aux paramètres prédéfinis de traitement vidéo avant la mise à niveau, ni modifier les paramètres prédéfinis de codage existants. Correctif pour CQ-4240407
* Les paramètres d’image prémis à niveau s’affichent comme Non publié sur la page Rendus et ne renvoient pas d’URL. Correctif pour CQ-4240406
* (CSS) Les ressources s’affichent, mais les visionneuses utilisées sont par défaut et non les visionneuses prêtes à l’emploi. Correctif pour CQ-4239839
* Désactivation de l&#39;exécution manuelle des étapes de nettoyage et utilisation de classes de coraux privées. Correctif pour CQ-4239729
* La visionneuse d’images génère une erreur et n’affiche pas le recadrage intelligent correct. Correctif pour CQ-4237564
* Le paramètre prédéfini hérité sous /etc semble rompu et n’a pas été migré vers l’emplacement sous /conf lors de l’enregistrement. Correctif pour CQ-4237416
* Régression dans OOB VideoViewer 5.8.x : la visionneuse développe iframe vers la droite, rompant ainsi la mise en page. Correctif pour CQ-4235465
* (DMS7) Les boutons URL de rendu de recadrage dynamique et Incorporer sont principaux pour les images qui n’ont pas été publiées. Correctif pour CQ-4233696
* (DMHybrid) Restaurer la fonction de recadrage/rotation précédente. Correctif pour CQ-4239489
* Lors de la prévisualisation d’une vidéo dans la vue de carte, le bouton de lecture ne bascule pas sur pause. Correctif pour CQ-4238592
* Lors d’une mise à niveau d’inclusion, la configuration YouTube n’est pas déplacée/copiée depuis son ancien emplacement vers le nouvel emplacement. Correctif pour CQ-4238590
* Les Profils de traitement vidéo AVS DropTwo prêtes à l&#39;emploi sont répertoriés sous Propriétés du dossier et un seul contient des encodages définis. Correctif pour CQ-4238096
* (DMS7) Recadrage intelligent : Vue de détails : Le bouton URL est intitulé Copier pour les rendus. Correctif pour CQ-4237804
* La page de liste des paramètres prédéfinis de la visionneuse reste vide même après avoir exécuté les commandes d’activation. Correctif pour CQ-4243246
* Désactivation de l&#39;étape de nettoyage accroche l&#39;exécution manuelle et l&#39;utilisation des classes de coraux privées. Correctif pour CQ-4239729
* La page Détails du rapport vidéo n’affiche pas de fichier vidéo. Correctif pour CQ-4246208

**DAM - DMServices**

* (DMS7) Configuration du cloud : Impossible de synchroniser le nouveau contenu avec Scene7 après la mise à jour vers SP1. Correctif pour CQ-4244437
* (DMHybrid) Les profils de couleur et les paramètres de catalogue ne sont pas enregistrés dans un appel debug_info=catalog. Correctif pour CQ-4242346
* Ajoutez des profils de couleur aux paramètres du client sur les serveurs de diffusion. Correctif pour CQ-4241818, CQ-4241819
* (DMHybrid) Après 6,3 &amp;gt; 6.4 mise à niveau, les paramètres du catalogue sont déplacés vers un noeud incorrect. Correctif pour CQ-4239974, CQ-4239975
* (DMHybrid) Le script pushviewerpresets ne crée pas les noeuds nécessaires pour modifier les paramètres du catalogue. Correctif pour CQ-4240076
* Lors de l’utilisation de la liste déroulante &quot;Format&quot; et de la sélection des formats PNG ou JPG, le fichier téléchargé s’affiche comme sursaturé et plus foncé que le fichier d’origine. Correctif pour CQ-4240073
* (DMS7) Supprimez le mappage de type MIME : image_x-eps. Correctif pour CQ-4240394
* (DMS7) Les paramètres de téléchargement pour le masquage en arrière-plan ne transmettent pas ipsApiService.log et ne fonctionnent donc pas. Correctif pour CQ-4240686
* La mise à niveau des Profils de traitement des images créés dans une instance 6.3 à 6.4 rompt la propriété &quot;Crop-type&quot;. Correctif pour CQ-4237739
* (Dynamic Media) Echec du téléchargement régulier de ressources en dehors du dossier smartculture. Correctif pour CQ-4237670
* Réglez le code de profil de secours pour le nom de profil &quot;Codage de vidéo adaptative&quot; sur &quot;Codage de vidéo adaptative&quot;. Correctif pour CQ-4237666
* Les données EmbedXMP sont toujours définies comme « actives » pour le workflow de génération Ptiff. Correctif pour CQ-4234498
* La saturation du rendu d’image CMJN est incorrecte. Correctif pour CQ-4235470
* Les paramètres du serveur d’images ne sont pas répliqués vers la diffusion tant que les journaux de réplication les marquent. Correctif pour CQ-4239480, CQ-4239046
* (DMS7) Impossible de créer des visionneuses à l’aide d’anciennes/nouvelles références à la configuration Cloud. Correctif pour CQ-4238078
* L’étape de flux de travaux Scene7 lit uniquement Scene7 dans le nom et la description, mais ne précise pas l’étape de flux de travaux dans le flux de travaux de mise à jour de gestion des actifs numériques. Correctif pour CQ-4237865

**DAM - Balises dynamiques**

* [Balises dynamiques améliorées](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951

**Formulaires**

Les correctifs d’AEM Forms sont fournis par le biais de packages de modules complémentaires et d’autres programmes d’installation de correctifs fournis avec la version. Pour plus d’informations, voir Versions d’AEM Forms.

Les principaux aspects pour AEM Forms sont les suivants :

* AEM Forms offre la [fonctionnalité de rapports de transactions](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) pour suivre et conserver le nombre de transactions telles que les formulaires envoyés, les documents traités et les documents rendus sur votre déploiement AEM Forms. Il fournit des informations sur l’utilisation des produits et permet aux utilisateurs d’entreprise de comprendre les volumes de traitement numérique.
* Activation de la prise en charge de PDF/UA pour les formulaires XML.
* allowProxy Ajouté = true pour Clientlib **aemfd.ccm.canal.contentpage**
* Mise à jour du code pour effectuer une recherche avancée de titre sous forme de contient plutôt que d’égal.
* Mise à jour vers la nouvelle version de Node Package Manager (NPM) sur la machine d’intégration continue.

**Package de modules complémentaires Forms**

**Intégration du serveur principal**

* Une erreur est générée lors de la fourniture de la valeur null en tant que valeur à un champ facultatif. NPR-24397
* L’appel WSDL échoue lorsque l’élément a un espace de nommage différent de l’espace de nommage global. NPR-24281
* (FDM WSDL) Obtention de DermisException : Données de liste exceptées en cas de tableau de type de propriété. NPR-24265
* (FDM WSDL) Obtention de DermisException : java.lang.Exception : createSOAPParam : Params non valides. NPR-24264
* (SDK client FDM) Impossible de tester le préprocesseur/post et l’action d’envoi personnalisée. Correctif pour CQ-4238469
* Correctifs des problèmes de Javadoc dans Dermis. Correctif pour CQ-4244250
* Amélioration de la saisie dans le langage WSDL (Web Services Description Language). Correctif pour CQ-4244133
* Les tests d’authentification de base pour WSDL génèrent une erreur différente pour la même configuration dans AEM 6.3 et AEM 6.4. Correctif pour CQ-4244132
* Demande d’inclusion de ValueUtil dans client-sdk et javadocs. Correctif pour CQ-4242803
* (Configuration de Cloud FDM) Impossible de configurer l’authentification SOAP à partir de la configuration de cloud. Correctif pour CQ-4238462
* Dermis - Ajouter des paquets manquants dans Javadocs. Correctif pour CQ-4242815
* WSDLInvokerParams à inclure dans le sdk client Forms Ajoute-On. NPR-23381 : correctif pour CQ-4240233

**Formulaires adaptatifs**

* Le rendu de document (IC) doit être consigné en tant que transaction à l’aide du service d’enregistrement des transactions. Correctif pour CQ-4245333
* Lors de l’exécution d’UAT5, une entrée est manquante dans le fichier pdf généré au stade de vérification. Correctif pour CQ-4243184
* Cas de test pour une copie en profondeur de guideContext. Correctif pour CQ-4242924
* Le champ de type BAT est manquant lors de l&#39;exécution de l&#39;UAT3 sur le dernier serveur mis à niveau. Correctif pour CQ-4243120
* Sur le serveur mis à niveau, les valeurs Etat/Province/Région et Pays présentes sur le serveur antérieur à la mise à niveau sont manquantes dans le formulaire envoyé. Correctif pour CQ-4241444
* (ExpressionEditor) Erreur lors de l’accès à l’étape Vérifier lors de l’envoi du formulaire. Correctif pour CQ-4241384
* Il manque des valeurs à l’étape de vérification sur le serveur avant la mise à niveau et mis à niveau pour le formulaire envoyé. Correctif pour CQ-4241896
* Le bouton Quitter et Enregistrer au bas de la page ne fonctionne pas. Correctif pour CQ-4240112
* Numéro de contact manquant sur la configuration mise à niveau. Correctif pour CQ-4239870
* Sous la section `ACTION TAKEN` de l&#39;onglet Type de litige, &quot;documents supplémentaires à l&#39;appui de ma réclamation&quot; a un BAT de champ supplémentaire Type enregistré &quot;dedans&quot;. Correctif pour CQ-4239873
* Erreur dans getDataAPI lors de l&#39;étape verifyPdf. Correctif pour CQ-4239865
* Erreurs dans les journaux de migration pour les instances d’auteur et de publication. Correctif pour CQ-4239365
* Erreurs dans les journaux de migration pour les instances d’auteur et de publication. Correctif pour CQ-4239635
* Erreur de désérialisation telle que &quot;Désérialisation non autorisée pour la classe sun.util.calendar.ZoneInfo&quot; dans les journaux d’erreurs après envoi d’un formulaire adaptatif. Correctif pour CQ-4240419
* Le champ d’état n’est pas renseigné dans le rendu de formulaire pour périphériques mobiles. Correctif pour CQ-4240597
* Supprimez l’utilisation de référence des composants dans les modèles de la liste anti-motif. Correctif pour CQ-4239217
* La zone numérique HTML5 définie sous la forme d’une virgule flottante ou d’une virgule donne des résultats de validation différents dans différents navigateurs. NPR-23528 : correctif pour CQ-4244097
* (Téléchargement d’image) L’image ne s’affiche pas dans la prévisualisation DOR. Correctif pour CQ-4243178
* Le serveur JEE affiche une erreur lors de la tentative d’envoi du formulaire adaptatif avec les options &quot;PDF par courrier électronique&quot; et &quot;Inclure les pièces jointes&quot;. Correctif pour CQ-4239894
* Le graphique n’est pas tracé au moment de l’exécution à l’aide d’un tableau/panneau. Correctif pour CQ-4240010
* L’envoi du formulaire adaptatif ne fonctionne pas et le nombre de transactions ne change pas en raison d’un échec de l’envoi. Correctif pour CQ-4246125
* (Choix de l’image) Les options de Document d’enregistrement ne sont pas visibles. Correctif pour CQ-4236976
* L&#39;interface utilisateur de l&#39;éditeur de modèles n&#39;est pas stable. Correctif pour CQ-4241497
* Les formulaires adaptatifs ne s’affichent pas à l’aide de l’onglet Fichiers du panneau latéral, alors qu’ils s’affichent à l’aide de l’option Parcourir pour AEM boîte de dialogue de propriétés du composant de formulaire. Correctif pour CQ-4236751
* L’ID de flux de travail généré pour la conversion de formulaire doit être disponible dans le formulaire adaptatif généré. Correctif pour CQ-4240014
* Impossible de sélectionner le modèle pour créer une page dans les sites sur la mise à niveau directe : Livecycle vers le serveur 6.4. Correctif pour CQ-4241300

**Incohérence affectant le service**

* Connexion des transactions dans Assembler Services. Correctif pour CQ-4245018, CQ-4245017, CQ-4245016.
* La transaction n’est pas consignée lorsque la conversion PDF/A est effectuée à l’aide de DDX. Correctif pour CQ-4246039

**Gestionnaire de formulaires**

* LISTE du bouton FM CREATE à trier par ordre alphabétique. Correctif pour CQ-4242307

**Portail des formulaires**

* Les brouillons enregistrés sur le serveur antérieur à la mise à niveau ne s’ouvrent pas correctement sur le serveur mis à niveau. Correctif pour CQ-4243303
* Mise à jour de la version 7.1 pour adobe-formsmanager-core-module. Correctif pour CQ-4245753
* Les brouillons enregistrés sur le serveur antérieur à la mise à niveau ne s’ouvrent pas correctement sur le serveur mis à niveau. Correctif pour CQ-4243303
* Les scénarios de pièces jointes se rompent lors du remplacement/ajout/suppression de pièces jointes dans la nouvelle instance/la même instance de brouillon. Correctif pour CQ-4243165
* Le nombre de brouillons récupérés lors de l&#39;interrogation de la base de données est supérieur au nombre de brouillons présents dans le portail. Correctif pour CQ-4241489
* Les Forms envoyées sur un serveur antérieur à la mise à niveau ne sont pas présentes sur le serveur mis à niveau. Correctif pour CQ-4241490
* Le formulaire affiché dans l’interface utilisateur de l’onglet des envois est à l’état Non envoyé malgré le message d’envoi réussi. Correctif pour CQ-4241487
* Le guideContext doit être formé en copiant en profondeur les champs car guideContext contient customPropertyMap qui est lui-même un objet. Correctif pour CQ-4240126
* Erreur lors de la tentative d’enregistrement d’un formulaire. Correctif pour CQ-4240763
* L’entrée pour les formulaires enregistrés et envoyés est renseignée dans crx/de malgré la configuration de base de données donnée dans la configuration des brouillons et des envois de Forms Portal. Correctif pour CQ-4240726
* (Recherche et énumérateur) La valeur fixe du titre de la recherche avancée doit fonctionner comme contenir plutôt que comme égale. Correctif pour CQ-4245499

**Forms mobile**

* Le champ de date se chevauche dans Mobile Forms. Correctif pour CQ-4242256
* L’envoi de formulaire pour Mobile Forms doit être consigné en tant que transaction à l’aide du service d’enregistrement des transactions. Correctif pour CQ-4246166
* L’envoi de formulaire dans le jeu de formulaires doit être consigné en tant que transaction à l’aide du service d’enregistrement des transactions. Correctif pour CQ-4246165

**Application AEM Forms**

* (Application Windows) Impossible de générer le formulaire. Correctif pour CQ-4238005

**Workflow OSGI**

* Journalisation des transactions dans la Tâche d’affectation de processus. Correctif pour CQ-4244440
* (Étape FDM) Impossible d&#39;utiliser les valeurs issues des métadonnées de flux de travaux lorsqu&#39;une étape Attribuer une Tâche est insérée entre l&#39;étape de processus et l&#39;étape fdm. Correctif pour CQ-4241472
* La délégation de tâche d&#39;affectation ne fonctionne pas dans l&#39;intégration Forms dans les Workflows OSGI. NPR-23709 : correctif pour CQ-4243700
* (Éditeur de modèle de flux de travail) Certains modèles de flux de travail ne sont pas modifiables via l’éditeur de modèle WF ClassicUI. Correctif pour CQ-4241151

**Document multicanaux**

* Le champ Date dans le modèle chevauche le sous-formulaire dans la création d’interface de ligne de commande. Correctif pour CQ-4240110
* L&#39;en-tête ne doit pas être autorisé à être supprimé ou déplacé vers le haut ou vers le bas dans la création de canaux Web IC. Correctif pour CQ-4243358
* (Editeur IC) Les lignes par défaut doivent être définies sur 1 pour les composants Tableau. Correctif pour CQ-4244848
* Zone de cible pour rester visible même après que le contenu a été glissé-déposé dessus. Correctif pour CQ-4244534
* Le canal Web ne reconnaît pas l’espace des onglets dans les fragments de Document de texte. Correctif pour CQ-4244481
* (canal d&#39;impression) Le rendu du Document (IC) doit être consigné en tant que transaction à l&#39;aide du service d&#39;enregistrement des transactions. Correctif pour CQ-4245335
* (canal Web) Le rendu du Document (IC) doit être consigné en tant que transaction à l’aide du service d’enregistrement des transactions. Correctif pour CQ-4245334
* La recherche par Conteneur de document ou par arbre de modèle de données doit être unifiée à la recherche par filtre de ressources. Correctif pour CQ-4242305
* (Fragment de Document) La propriété indentation met le texte en retrait en fonction du nombre d’unités incompréhensibles. Correctif pour CQ-4241082, CQ-4240643
* (Editeur IC) L’icône Modifier le fragment sur la mosaïque du fragment de document répertoriée sous l’onglet Ressources n’est pas facilement détectable et compréhensible. Correctif pour CQ-4241047
* Autoriser l&#39;accès anonyme à la bibliothèque cliente inaccessible IC Anonymous. Correctif pour CQ-4245588
* (canal Web) Les données ne sont résolues dans aucun tableau de la prévisualisation Web et sont affichées en blanc. Correctif pour CQ-4244476
* Les en-têtes de tableau s’affichent sous forme de variables dans le canal Web lors de la génération automatique. Correctif pour CQ-4244242
* (Éditeur IC) Le contenu d’un fragment de Document utilisé dans une interface de ligne de commande doit être automatiquement redimensionné pour s’adapter à la largeur de la zone de Cible. Correctif pour CQ-4244094
* Le nom du canal affiché en haut du centre doit être cohérent soit pour le titre IC pour WEB / IMPRESSION. Correctif pour CQ-4242498
* Editeur de texte Le panneau d’objet de données ne doit liste que les entités de niveau supérieur, Correctif pour CQ-4244121
* Le nom par défaut n’est pas affecté lors de l’ajout d’un nouveau composant dans l’éditeur. Correctif pour CQ-4244691
* Ajouter la configuration de Colspan dans tous les composants du canal Web. Correctif pour CQ-4244946
* La propriété Largeur du tableau du fragment de mise en page n’est pas réinitialisée et n’est pas respectée dans le Canal d’impression Lettre ou Communication client. Correctif pour CQ-4241574

**Correspondence Management**

* Légendes supprimées du modèle de lettre après modification d’un actif de texte contenant des espaces réservés. NPR-24196
* Le fichier XDP, lorsqu’il est téléchargé et utilisé comme mise en page pour les modèles de lettre, ne parvient pas à prévisualisation ni à modifier les modèles. NPR-24143 : correctif pour CQ-4244407
* La sélection d’affectation est sélectionnée par défaut dans le fragment de liste. Correctif pour CQ-4240097
* Éditeur de conditions : l’évaluation de plusieurs résultats doit être activée par défaut. Correctif pour CQ-4240096
* L&#39;image supprimée de la Liste affiche toujours l&#39;image en prévisualisation. Correctif pour CQ-4239909
* La règle définie sur le module de condition est définie sur &quot;Par défaut&quot; pour tous les modules. Correctif pour CQ-4239878
* La création du dictionnaire de données échoue avec l’erreur &quot;Exception JCR inconnue&quot;. Correctif pour CQ-4244122
* Lacunes dans les documents JavaDocs de contenu 6.3. Correctif pour CQ-4213586

**Programme d’installation de Forms JEE**

**Base**

* (Workspace HTML) Les détails du suivi sont absents pour les applications dont le nom contient des parenthèses. NPR-23402

**Service PDFG**

* Journalisation des transactions dans les services PDFG. Correctif pour CQ-4244951, CQ-4244586
* Réduction des fichiers PDF en désincorporant sélectivement les polices via un appel d’API unique. NPR-23287
* Problème de mise à jour des configurations PDFG lors de la mise à niveau AEM. Correctif pour CQ-4241176
* Connexion des transactions dans PDFUtility Service. Correctif pour CQ-4245014

**Process Management**

* (Workspace HTML) Les points de départ du processus ne sont pas triés par ordre alphanumérique. Correctif pour CQ-4239629
* (Espace de travail HTML) Préparez l’appel de données à venir deux fois lors de la première ouverture du brouillon. Correctif pour CQ-4243280
* (Workspace HTML) Le processus de préparation des données est déclenché lors de la fermeture d’un formulaire. Correctif pour CQ-4239456
* L&#39;espace de travail se bloque lorsqu&#39;il est traversé entre deux tâches. Correctif pour CQ-4237125

**Workbench**

* Gérer le Profil d’action Le processus de préparation des données échoue lorsque la configuration du processus de rendu par défaut est définie sur HTML. Correctif pour CQ-4244292

**Concepteur Forms**

* Ajout de la prise en charge de PDF/UA aux formulaires XML générés via Designer et Output Service. NPR-23022
* Les hyperliens en ligne définis dans le Concepteur ne sont pas balisés et ne contiennent pas de texte de remplacement lors de l’enregistrement au format PDF depuis le Concepteur. NPR-23023

**Packs de fonctionnalités inclus**

**Ressources**

* Ajouté la fonctionnalité Balises dynamiques améliorées. Pour plus d’informations, voir [Balises dynamiques améliorées](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951 : correctif pour CQ-4234883
* Introduction de références AEM Assets en InDesign. Pour plus d’informations, voir [Références AEM Assets dans InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sites**

* (Création de page) Améliorations de l’éditeur d’images. Pour plus d’informations, voir [Éditeur d’image](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24267 : correctif pour CQ-4245502

**bundles OSGI et packages de contenu inclus**

Le texte suivant documents la liste des lots OSGI et des packages de contenu inclus dans le CFP.

Liste des lots OSGi inclus dans AEM 6.4.1.0

[Obtenir le fichier](assets/6_4_1_0_bundle-list.txt)

Liste des packages de contenu inclus dans AEM 6.4.1.0

[Obtenir le fichier](assets/6_4_1_0_content-package-list.txt)

### Installer 6.4.8.0 {#install}

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

* aem 6.4.8.0 requiert AEM 6.4. Pour plus d’informations, voir [documentation de mise à niveau](../sites-deploying/upgrade.md).
* Le téléchargement du Service Pack est disponible sur le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) pour téléchargement.
* Lors d’un déploiement avec MongoDB et plusieurs instances, installez AEM 6.4.8.0 sur l’une des instances d’auteur à l’aide du gestionnaire de modules.
* Avant d’installer le pack de service, veillez à disposer d’un instantané ou d’une nouvelle sauvegarde de votre instance AEM.
* Redémarrez l’instance avant l’installation. Cela est nécessaire uniquement lorsque l’instance reste en mode de mise à jour (ce qui est le cas lorsque l’instance vient d’être mise à jour depuis une version antérieure). Toutefois, cela est généralement recommandé si l’instance s’est exécutée pendant longtemps.

>[!NOTE]
>
>Adobe recommande de ne pas supprimer ni désinstaller le package AEM 6.4.8.0.

### Installer le Service Pack via Package Manager {#install-the-service-pack-via-package-share}

Accomplissez les étapes suivantes pour installer le Service Pack sur une instance 6.4 existante :

1. Téléchargez le package à partir de Software Distribution.

1. Dans AEM, connectez-vous à Package Manager et ajoutez le package AEM 6.4.8.0 téléchargé. Sélectionnez le package téléchargé et cliquez sur **[!UICONTROL Installer]**.

>[!NOTE]
>
>**La boîte de dialogue sur l’interface utilisateur de Package Manager se ferme parfois de manière impromptue lors de l’installation de la version 6.4.8.0**
>
>Il est donc recommandé d’attendre que les journaux d’erreurs se stabilisent avant d’accéder à l’instance. L’utilisateur doit attendre les journaux spécifiques liés à la désinstallation du lot de mise à jour avant de s’assurer que les installations sont réussies. Cela se produit généralement sur Safari, mais peut se produire par intermittence sur n’importe quel navigateur.

### Installation automatique  {#auto-installation}

Il existe deux manières d’installer automatiquement AEM 6.4.8.0 dans une instance en cours d’exécution :

A. Placez le package dans le dossier ..*/crx-quickstart/install* pendant que le serveur est en cours d’exécution. Le package est automatiquement installé.

B. Utilisez l&#39;API [HTTP de Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - assurez-vous d&#39;utiliser `cmd=install&recursive=true` pour installer le package imbriqué.

>[!NOTE]
>
>AEM 6.4.8.0 ne prend pas en charge l’installation de Bootstrap.

### Validation de l’installation {#validate-install}

1. La page Informations sur le produit (*/system/console/ productinfo *) doit maintenant afficher la chaîne de version mise à jour &quot;Adobe Experience Manager, Version 6.4.8.0&quot; sous Produits installés.
1. Tous les lots OSGI sont ACTIFS ou FRAGMENT dans la console OSGI (utiliser la console web : /system/console/bundles).
1. Le lot OSGI org.apache.jackrabbit.oak-core est sur la version 1.8.17 ou ultérieure (utilisez la console Web : /system/console/bundles).

Pour déterminer la plate-forme certifiée pour l’exécution avec cette version d’AEM Sites et d’Assets, voir [Exigences techniques](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Une fois le package installé avec succès, un message >informationnel s’affiche indiquant que le package content >a été installé avec succès, tel que **&quot;Package de contenu AEM-6.4-Service-Pack-7 installé avec succès.&quot;**

### Mettre à jour les visionneuses Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">aem 6.4.8.0 contient la nouvelle version des visionneuses Dynamic Media (5.10.1) qui permet de vérifier les noms de duplicata sur la page Paramètres d’image prédéfinis. Il est conseillé aux clients de Dynamic Media d’exécuter la commande suivante afin de mettre à jour les paramètres prédéfinis de la visionneuse prête à l’emploi.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

qui copiera les nouveaux paramètres prédéfinis de la visionneuse à l’emplacement /conf.

### Installation du module complémentaire AEM Forms {#install-aem-forms-add-on-package}

#### Installation du module complémentaire AEM Forms {#installaemformsaddon}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms. Les correctifs dans AEM Forms sont fournis dans un module complémentaire distinct.

>[!NOTE]
>
>AEM 6.4.8.0 inclut une nouvelle version du [package de compatibilité d’AEM Forms](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/AEM-FORMS-6.4.7.0-COMPAT). Si vous utilisez une ancienne version du package de compatibilité AEM Forms et que vous mettez à jour vers AEM 6.4.8.0, installez la dernière version du package de compatibilité AEM Forms après l&#39;installation du package de Ajoute Forms.

1. Vérifiez que vous avez installé le Service Pack AEM.
1. Téléchargez le module complémentaire de formulaires correspondant figurant dans les [versions AEM Forms](https://helpx.adobe.com/fr/aem-forms/kb/aem-forms-releases.html) de votre système d’exploitation.
1. Installez le module complémentaire de formulaires comme décrit dans [Installation des modules complémentaires de formulaires AEM](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installation du programme d’installation d’AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms sous JEE. Les correctifs dans AEM Forms JEE sont fournis dans un programme d’installation distinct.

Pour plus d’informations sur l’installation du programme d’installation cumulatif pour AEM Forms JEE et la configuration post-déploiement, voir [AEM Forms JEE Patch Installer 0015](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### Paramètres de configuration requis pour NPR-21268 {#configuration-settings-required-for-npr}

Si vous utilisez l’interface utilisateur classique (ancienne) et avez créé des modèles de métadonnées à l’aide de celle-ci, suivez les étapes pour exécuter le script JMX afin de les conserver.

1. Accédez à /system/console/jmx.
1. Cliquez sur &quot;Migrer les modèles de métadonnées&quot;.
1. Cliquez sur &quot;migrateMetadataTemplatesAtPath&quot; et indiquez le chemin d’accès au dossier sous lequel vous souhaitez conserver les modèles de métadonnées.

#### Paramètres de configuration requis pour NPR-24536 {#configuration-settings-required-for-npr-1}

Par défaut, le nombre de files d’attente partagées n’est pas actualisé pour les autres utilisateurs lorsqu’un utilisateur demande une tâche. Pour cela, nous avons introduit une nouvelle propriété. Suivez les étapes ci-dessous pour configurer cette propriété sur votre instance AEM :

1. Accédez à Interface utilisateur d’administration -> Services -> Espace de travail -> Administration globale.
1. Exporter les paramètres globaux.
1. Dans le fichier XML téléchargé, ajoutez la balise &lt;client_tasksPollingInterval>10&lt;/client_tasksPollingInterval> Ici, 10 est l’exemple de valeur en secondes. Vous pouvez le modifier en conséquence.
1. Enregistrez le fichier .
1. Revenez à l’interface utilisateur d’administration -> Services -> Espace de travail -> Administration globale.
1. Importez le fichier xml dans la section Importer les paramètres globaux.
1. Vous pouvez maintenant vous déconnecter du système et vous reconnecter.
1. Nombre de débuts de file d’attente partagés actualisés pour d’autres utilisateurs de l’espace de travail.
1. Pour désactiver l’interrogation, définissez la valeur sur 0 et importez à nouveau le fichier XML.

### Uber Jar {#uber-jar}

Le Jar Uber pour AEM 6.4.8.0 est disponible dans le [référentiel Adobe Public Maven](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/).

Pour utiliser Uber Jar dans un projet Maven, reportez-vous à l&#39;article [Comment utiliser Uber jar](../sites-developing/ht-projects-maven.md) et incluez la dépendance suivante dans votre POM de projet :

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
| Assets | Gérer l’action de balise pour les sous-ensembles | Aucun remplacement. | AEM 6.4.2.0 |
| Intégration des Ressources et d’Adobe Creative Cloud | [aem au ](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) partage de dossiers Creative Cloud a été introduit dans AEM 6.2 pour permettre aux utilisateurs créatifs d’accéder aux ressources provenant d’AEM. Adobe Asset Link, nouvelle fonctionnalité proposée dans l’application Creative Cloud, offre une expérience utilisateur améliorée et un accès plus puissant aux ressources d’AEM directement à partir de Photoshop, InDesign et Illustrator. Adobe n’apportera pas d’améliorations supplémentaires à la fonctionnalité de partage de dossiers. Bien que la fonction soit incluse dans AEM, les clients sont (il est fortement conseillé d’utiliser le remplacement). | Lien de ressources d’Adobe ou application de bureau. Pour plus d’informations, reportez-vous à l’article [Intégration d’AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

### Problèmes connus {#known-issues}

* Les erreurs et avertissements suivants peuvent s’afficher pendant l’installation :

   * Les erreurs de création d’instance de composant et de renvoi de valeur nulle par Service Factory se produisent en raison du redémarrage du référentiel :

      * com.day.cq.cq-personalization \[com.day.cq.personalization.impl.DefaultProfileProvider(938)\] Impossible de créer une instance de composant en raison d&#39;un échec de liaison de profileManager
      * org.apache.sling.commons.Planificateur FrameworkEvent ERROR (org.osgi.framework.ServiceException : La fabrique de services a renvoyé la valeur null. (Composant : com.day.cq.tagging.impl.TagGarbageCollector (1687))
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Délai d’attente en attente de la modification de l’enregistrement non enregistrée.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` Aucune fenêtre de maintenance n’a été trouvée sur granite/operations/maintenance
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: La méthode unbindAmendment a généré une exception (java.lang.IllegalStateException : Service déjà non enregistré).
Ces erreurs ne nécessitent aucune action, car elles n’affectent pas votre instance AEM.


### Problèmes résolus {#resolved-issues}

**AEM 6.4.4.0**

* Aucune erreur de ressource trouvée n&#39;est observée lors de l&#39;importation/exportation de métadonnées. CQ-4253263
* Impossible de modifier un composant d’image et les propriétés de page après l’application de la version 6.4.3.0 en plus de la version 6.4.2.0. CQ-4260316 et CQ-4260441
Pour résoudre ce problème :
   * Accéder à Package Manager
   * Réinstallez le package &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot;.
   * Recompilez tous les JSP `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` OU Redémarrez l’instance.

### Lots OSGi et packages de contenu inclus {#osgi-bundles-and-content-packages-included}

Les documents de texte suivants liste les lots OSGi et les packages de contenu inclus dans AEM 6.4.8.0.

Liste des lots OSGi inclus dans AEM 6.4.8.0

[Obtenir le fichier](assets/6.4.8.0_osgi_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.8.0

[Obtenir le fichier](assets/6.4.8.0_content_packages.txt)

### Ressources utiles {#helpful-resources}

* [Notes de mise à jour d’AEM 6.4](../release-notes/release-notes.md)
* [Page de produits AEM ](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentation d’AEM 6.4](https://helpx.adobe.com/fr/support/experience-manager/6-4.html)
* S’abonner aux [mises à jour de produits prioritaires par Adobe](https://www.adobe.com/subscription/priority-product-update.html)

### Sites restreints {#restricted-sites-new}

Seuls les clients peuvent accéder à ces sites. Si vous devez y accéder en tant que client, contactez votre gestionnaire de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/).
* Mises à jour des produits, correctifs et packages pour des fonctionnalités supplémentaires sur [Distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Assistance clientèle via Admin Console](https://adminconsole.adobe.com/). Pour plus d’informations, voir [Nouvelle expérience de l’assistance clientèle d’Adobes](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
