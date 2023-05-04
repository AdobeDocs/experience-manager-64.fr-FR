---
title: Notes de mise à jour du pack de correctifs cumulés AEM 6.4
description: Notes de mise à jour spécifiques aux packs de correctifs cumulatifs Adobe Experience Manager 6.4.
contentOwner: AK
mini-toc-levels: 1
exl-id: a63e77a3-da48-4072-bc75-c4c41a2f62a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4717'
ht-degree: 31%

---

# Notes de mise à jour du pack de correctifs cumulés AEM 6.4 {#aem-cumulative-fix-pack-release-notes}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Informations sur la version {#release-information}

<!-- TBD: Update the SD URL. -->

| Produits | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.4 |
| Type | Pack de correctifs cumulatif |
| Date | 25 février 2021 |
| Prérequis | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL de téléchargement | [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## Éléments inclus dans AEM 6.4.8.4 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.4 est une mise à jour importante qui comporte plusieurs correctifs internes et clients depuis la disponibilité générale d’AEM 6.4 Service Pack 8 (6.4.8.0) en mars 2020.

AEM 6.4.8.4 est un pack de correctifs cumulatifs (CFP) qui dépend d’AEM 6.4 Service Pack 8. Installez le CFP après l’installation AEM Service Pack 8 6.4.

Les principales fonctionnalités et améliorations introduites dans [!DNL Adobe Experience Manager] 6.4.8.4 sont les suivantes :

* Possibilité d’activer ou de désactiver le [!DNL Experience Manager Forms] modifications du registre lors de l’exécution d’une conversion PDFG.

* Authentification par certificat X-509 pour les services web SOAP dans le modèle de données de formulaire.

* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.24.

Pour plus d’informations sur les CFP et d’autres types de mises à jour, voir [AEM mettre à jour les définitions des véhicules de version](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.4 fournit des correctifs pour les problèmes suivants.

### Sites {#sites-6484}

* Après avoir installé le Service Pack Experience Manager 6.4.8.2, les utilisateurs ne peuvent pas modifier les modèles de fragments de contenu et rencontrer l’erreur suivante :

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* Lorsqu’un utilisateur clique sur le bouton de déconnexion, il n’est pas déconnecté de Package Manager. (NPR-35161)
* Après la mise à niveau de Experience Manager 6.4.x vers Experience Manager 6.4.8.3, les utilisateurs ne peuvent pas publier une page via Gérer la publication. (CQ-4312511)
* Lorsque vous déplacez une page enfant de plan directeur vers l’emplacement d’origine, la configuration cq:liveSyncConfig n’est pas supprimée d’une page enfant de Live Copy. (NPR-35900)
* Lorsque vous déplacez un plan directeur avec des Live Copies, seul le premier déplacement fonctionne, puis il échoue et aucun message d’erreur n’est affiché. (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` causes `OutOfMemoryError` erreur car la fonctionnalité de balisage intelligent crée une grande `/oak:index/lucene` et `/oak:index/ntBaseLucene` indices (NPR-35650).
* Les utilisateurs ne peuvent pas archiver des ressources après les avoir modifiés dans [!DNL Adobe InDesign] et reçoivent une erreur à propos de l’absence d’autorisations nécessaires (NPR-35340).
* Lorsqu’une nouvelle version d’une ressource existante est créée après la résolution du conflit de dénomination, les métadonnées de la ressource d’origine sont écrasées (NPR-35939).
* Les groupes générés automatiquement par le dossier privé ne sont pas conservés et ne sont pas supprimés lors de la suppression du dossier ou de la mise à jour du dossier avec l’événement [!UICONTROL Suppression des restrictions de dossier privé] ensemble d’options (NPR-35625).

#### [!DNL Dynamic Media] {#dynamic-media}

* Une erreur ImageServer intermittente provoque une réponse 403 pour et par conséquent l’échec de certaines fonctionnalités de [!DNL Experience Manager]. (CQ-4308565)

### Intégrations {#integrations-6484}

* Lorsque vous ouvrez les propriétés d’une page après la mise à niveau vers Experience Manager 6.4.8.3, des erreurs JavaScript commencent à apparaître dans la console (NPR-35649).

### Forms {#forms-6484}

>[!NOTE]
>
>[!DNL Experience Manager Forms] publie les packages de modules complémentaires une semaine après la date de publication prévue du pack de correctifs cumulés [!DNL Experience Manager].

**Gestion des correspondances**

* Lorsque vous modifiez une lettre, le chargement des modules contenant des conditions prend plus de temps (NPR-35326).

* Lors de la modification d’une lettre, le contenu et les liaisons de données ne s’affichent pas dans l’interface utilisateur (CQ-4312905).

**Services de document**

* Impossible d’assembler les PDF après la mise à niveau [!DNL JAVA] to [!DNL JDK1.8.0_261] (NPR-35761, NPR-35848).

**JEE Foundation**

* Lorsque vous modifiez une notification de tâche dans [!DNL Forms] , vous ne pouvez pas l’enregistrer (CQ-4315055).

**Problèmes résolus dans AEM Forms-6.4.0-0027**

* (JEE uniquement) Vulnérabilités de sécurité critiques (CVE-2021-44228 et CVE-2021-45046) signalées pour Apache Log4j2.

Pour plus d’informations sur les mises à jour de sécurité, consultez la [page des bulletins de sécurité d’Experience Manager](https://helpx.adobe.com/fr/security/products/experience-manager.html).

## Correctifs et Feature Packs inclus dans les packs de correctifs cumulés précédents {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM Cumulative Fix Pack 6.4.8.3 est une mise à jour importante qui comporte plusieurs correctifs internes et clients depuis la disponibilité générale d’AEM 6.4 Service Pack 8 (6.4.8.0) en mars 2020.

AEM 6.4.8.3 est un pack de correctifs cumulatifs (CFP) qui dépend d’AEM 6.4 Service Pack 8. Installez le CFP après l’installation AEM Service Pack 8 6.4.

Dans AEM 6.4.8.3, le référentiel intégré (Apache Jackrabbit Oak) est mis à jour vers la version 1.8.23.

Pour plus d’informations sur les CFP et d’autres types de mises à jour, voir [AEM mettre à jour les définitions des véhicules de version](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.3 fournit des correctifs pour les problèmes suivants.

#### Sites {#sites-6483}

* Lorsque vous mettez à jour le texte d’une variation d’un fragment de contenu, le contenu du fragment de contenu maître est mis à jour à la place de la variation (NPR-35080).

* Lorsque vous définissez une valeur numérique pour la propriété d’étiquette de type Chaîne d’un composant, supprimez le composant, puis utilisez l’option Annuler pour le rétablir, le type de propriété d’étiquette passe automatiquement de String à Long (NPR-34738).

* Lorsque vous ajoutez un composant Transfert de fichier à plusieurs champs, le chemin d’accès à l’image est stocké dans le noeud de composant au lieu du noeud Multi-Field (NPR-34423).

* Dans l’assistant Déplacer la page , même si aucune destination n’est sélectionnée, le bouton suivant reste activé (NPR-34460).

* Lorsque le composant parent inclut la variable `cq:isContainer` , le composant hérité n’inclut pas automatiquement la propriété (CQ-4308409).

* Lorsque vous utilisez la minimisation CSS à l’aide de `calc()` , les espaces vides autour de la fonction `+` le signe est supprimé (NPR-34991).

* Lorsque vous démarrez une instance AEM, la variable `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` et `com.adobe.granite.maintenance.impl.TaskScheduler` les composants ne s’affichent pas dans `Active` state (NPR-34952).

#### [!DNL Assets] {#assets-6483}

* Lors de la création d’une version d’une ressource existante, les mises à jour utilisateur apportées aux métadonnées ne sont pas conservées si un profil de métadonnées est appliqué au dossier (NPR-34833).
* Lors de l’utilisation d’[!DNL Adobe Asset Link] avec [!DNL Adobe InDesign], les résultats de recherche ne contiennent pas de dossiers et de collections, mais uniquement des ressources (NPR-34700).
* Lorsque vous faites glisser une ressource sur un dossier pour la déplacer, l’interface utilisateur affiche également l’option [!UICONTROL Déposer dans Lightbox] et [!UICONTROL Déposer dans la collection]. Même si l’opération de déplacement est annulée, l’interface utilisateur continue d’afficher les deux dernières options (NPR-34525).
* Lorsque l’interface Gérer la publication est ouverte, l’option de publication n’est pas disponible et lorsque vous sélectionnez l’option d’annulation de publication, la page de portée est vide (CQ-4302509).

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* Dans les paramètres de paramètre d’image prédéfini, lorsque l’option [!UICONTROL Activer le sous-échantillonnage de la chrominance JPG] est désélectionné dans [!DNL Experience Manager], la modification n’est pas synchronisée avec [!DNL Dynamic Media] (NPR-34284).
* Dans l’[!UICONTROL Éditeur de paramètres prédéfinis de visionneuse], lors de la modification du paramètre prédéfini [!UICONTROL PanoramicImage/PanoramicImage_VR], dans le composant `PanoramicView`, le libellé de modificateur `PANORAMICVIEW_AUTOROTATE` n’est pas disponible (CQ-4302043).
* Annulation de la publication d’une vidéo depuis [!DNL Experience Manager] n’annule pas la publication de la visionneuse de vidéos adaptative sur Dynamic Media Classic configuré. (CQ-4304405).

#### Plateforme {#platform-6483}

* Le `emitUseStrict` Un indicateur est ajouté à la fonction de processeur du Compilateur de fermeture Google (GCC). `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. L’indicateur supprime la sortie de la variable `use strict` (NPR-34830).
* A `NullPointerException` est renvoyé lors du démarrage des tâches de maintenance quotidiennes ou hebdomadaires (NPR-34702).
* Le [!DNL Apache Sling Health Check] est obsolète. À la place, utilisez [Outil de détection des motifs](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html?lang=fr) pour détecter des violations de contenu (NPR-33929).

#### Intégrations {#integrations-6483}

* Le [!UICONTROL Créer] s’affiche sur le bouton [!UICONTROL Audiences] lors de la navigation d’un dossier vers le [!UICONTROL Audiences] (NPR-35152).

#### Interface utilisateur {#ui-6483}

* Le [!UICONTROL Filtres] panneau de recherche sur [!UICONTROL Omnisearch] L’interface utilisateur renvoie également les résultats à partir d’emplacements autres que l’emplacement d’exécution de la recherche (NPR-34877).
* À la fermeture de la [!UICONTROL Filtres] panneau [!UICONTROL Omnisearch] interface utilisateur, le rail de gauche n’est pas réinitialisé sur [!UICONTROL Contenu] , ce qui empêche la réouverture de la propriété [!UICONTROL Filtres] (NPR-34483).
* A `NullPointerException` est renvoyée lors de l’accès aux propriétés de la page (NPR-34509).

#### Communities {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* Tous les cas de terminologie inéquitable du produit sont remplacés par des équivalents acceptés (NPR-34506).

#### Commerce {#commerce-6483}

* Lorsqu’une collection comprend plus de 15 produits, elle n’affiche que les 15 premiers produits (NPR-34494).

#### Forms {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] publie les packages de modules complémentaires une semaine après la date de publication prévue du pack de correctifs cumulés [!DNL Experience Manager].

>[!NOTE]
>
>[!DNL Experience Manager] Le pack de correctifs cumulés n’inclut pas de correctifs pour [!DNL Experience Manager Forms]. Les correctifs sont fournis à l’aide d’un package complémentaire [!DNL Forms] distinct. En outre, un programme d’installation cumulatif est publié, qui inclut des correctifs pour [!DNL Experience Manager Forms] sous JEE. Pour plus d’informations, voir [Installation du module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installation du programme d’installation d’AEM Forms JEE](#install-aem-forms-jee-installer).

**Formulaires adaptatifs**

* Impossible de modifier un formulaire adaptatif à l’aide de l’interface utilisateur classique après l’application de la variable [!DNL Experience Manager] Pack de correctifs cumulés (NPR-35127).

* Le chargement des fragments prend plus de temps dans un formulaire adaptatif en raison de l’invalidation du cache (NPR-34655).

* Accessibilité : La navigation par onglets ne fonctionne pas correctement pour les lecteurs d’écran d’un formulaire adaptatif (NPR-34550).

**Gestion des correspondances**

* Lorsque vous migrez les ressources à partir d’ES3, les ressources incluent deux conditions par défaut non modifiables (NPR-34971).

**JEE Foundation**

* Migrer [!DNL AEM Forms] des utilisateurs de Flash en HTML (CQ-4304075).

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2 est une mise à jour importante qui comporte plusieurs correctifs internes et clients depuis la disponibilité générale d’AEM 6.4 Service Pack 8 (6.4.8.0) en mars 2020.

AEM 6.4.8.2 est un pack de correctifs cumulatifs (CFP) qui dépend d’AEM 6.4 Service Pack 8. Installez le CFP après l’installation AEM Service Pack 8 6.4.

Dans AEM 6.4.8.2, le référentiel intégré (Apache Jackrabbit Oak) est mis à jour vers la version 1.8.22.

Pour plus d’informations sur les CFP et d’autres types de mises à jour, voir [AEM mettre à jour les définitions des véhicules de version](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.2 fournit des correctifs pour les problèmes suivants.

#### Sites {#sites-6482}

* Si `RolloutConfigManagerFactoryImpl` ne peut pas charger une configuration de déploiement, elle ne tente pas de charger les configurations manquantes. Elle renvoie les configurations mises en cache (NPR-34091).
* Dans le composant principal Texte, après avoir utilisé l’option de modification du HTML source, la classe de la balise `em` est supprimée (NPR-34080).
* Lorsque vous effectuez une mise à niveau de Experience Manager 6.2 vers Experience Manager 6.5, le composant Parsys des modèles statiques ne s’affiche pas correctement. La hauteur du composant Parsys est définie sur 0 et les composants qu’il contient ne sont pas visibles (NPR-34044).
* Les informations d’étiquette ne s’affichent pas pour les composants autorisés dans l’éditeur de modèles (NPR-33908).

   ![Libellés manquants dans le conteneur de mises en page](assets/33908_missing_labels.png)

* Les utilisateurs ne peuvent pas ajouter ni modifier des composants au parsys après le quatrième niveau des composants imbriqués (NPR-33873).
* Si le contenu initial d’un modèle modifiable est modifié puis que le modèle est publié, toutes les nouvelles pages créées avec ce modèle affichent la date de publication du modèle, même si les pages ne sont pas publiées (NPR-33822).
* Les propriétés `cq:acLinks` et `cq:acUUID` pour [!DNL Adobe Campaign] sur la copie sont supprimées pendant l’opération de copier-coller (NPR-33793).
* Dans le [!UICONTROL Utilisation en direct] , seuls 49 résultats s’affichent. Il n’affiche pas toute l’utilisation du composant (NPR-33710).
* Une page web avec `/` dans l’URL ne répond plus lors de la création. Lorsqu’un composant est ajouté lors de la création, l’utilisation du processeur augmente et le navigateur cesse de répondre (NPR-33625).
* En mode de modification en ligne dans [!DNL RTE], il n’est pas possible de faire glisser une image pour le composant Texte (NPR-33579).
* Il est possible de créer un composant dans une page de plan directeur portant le même nom que le nom de la page. Au cours du déploiement, un tel composant est renommé par suffixe. `_msm_moved`. Cependant, le composant est déplacé à la fin de la [!UICONTROL Système de paragraphes] (NPR-33534).
* La promotion de Launch ne publie pas de pages lorsque [!UICONTROL inclure des sous-pages] n’est pas cochée sur la première racine de contenu (NPR-33533).
* La redirection vers la page [!DNL Experience Manager] avec ancre ne fonctionne pas sur l’instance d’auteur, puisque `PageRedirectServlets` place la chaîne de requête après un fragment d’URL ou une ancre (NPR-34287).
* `PageRedirectServlet` appends `.html` après le mappage Sling entraînant des échecs de lien (NPR-34271).
* Vous pouvez suspendre la [!DNL Live Copy] d’une page, et l’héritage sera rompu, tel que vous pouvez le voir en mode Éditeur. Cependant, dans les propriétés Page, l’icône représentant l’héritage indique incorrectement que l’héritage existe et n’est pas rompu (NPR-34096).
* Problème avec l’affichage des composants autorisés dans la page Modifier le modèle (CQ-4297295).
* Après la mise à niveau de Chrome et Firefox, les menus contextuels ne fonctionnent pas comme prévu. Lors du chargement des propriétés de la page, le panneau n’apparaît pas lorsqu’il contient des données (CQ-4292995).
* Plusieurs instances de cross-site scripting dans des composants [!DNL Experience Manager Sites] (NPR-33926).
* Les entrées utilisateur ne sont pas codées correctement pour divers composants lors de l’envoi d’informations au client (NPR-33696).
* Une URL se terminant par `childrenlist.html` affiche une page HTML au lieu d’une réponse 404. Ces URL sont vulnérables au cross-site scripting (NPR-33441).

#### Ressources {#assets-6482}

* L’extraction de texte pour les fichiers de PDF chargés ne fonctionne pas et la recherche de texte intégral de certains mots dans un fichier de PDF ne parvient pas à récupérer ce fichier de PDF (NPR-34165).

   >[!NOTE]
   >Pour que ce correctif fonctionne, redémarrez votre instance Adobe Experience Manager après l’installation du Service Pack 6.4.8.2.

* Des barres obliques inverses sont ajoutées avant les caractères spéciaux dans les suggestions de recherche de ressources qui portent des caractères spéciaux dans leur nom (NPR-33833).

* Les filtres personnalisés enregistrés en tant que collections dynamiques ne sont pas correctement appliqués aux ressources. Par conséquent, les résultats de la recherche ne sont pas précis (NPR-33725).

* La chronologie d’une ressource dans un dossier qui a été réorganisé indique que la ressource a été déplacée (NPR-33580).

* Annulation de la publication en bloc des ressources à partir de [!DNL Brand Portal] mène à `Request-URI Too Long` erreur (NPR-34158).

* En mode Colonne si l’utilisateur sélectionne [!UICONTROL Filtrer] après avoir sélectionné un ensemble de ressources (les ressources sont désélectionnées), puis sélectionne un autre ensemble de ressources à déplacer, puis les ressources sélectionnées précédemment sont également déplacées vers le nouvel emplacement (NPR-34018).

* La barre de défilement n’est pas visible en mode Liste, même si la page contient de nombreuses ressources (NPR-34156).

* Le [!UICONTROL Gérer la publication] La page des ressources est rompue et les options qui y sont présentes ne fonctionnent pas (CQ-4302509).

**Dynamic Media**

* La fonctionnalité de recadrage intelligent échoue avec un message d’erreur lorsque le profil d’image est ajouté à un dossier avec plusieurs proportions (par exemple, 11) (NPR-34083).

* Modifications des paramètres d’image prédéfinis dans [!UICONTROL Adobe Experience Manager] ne pas effectuer de synchronisation avec Dynamic Media Classic (NPR-34284, CQ-4299713).

* Le [!UICONTROL PANORAMICVIEW_AUTOROTATE] l’étiquette de modificateur est manquante dans [!UICONTROL Comportement] dans [!UICONTROL Éditeur de paramètres prédéfinis de la visionneuse] (CQ-4302043).

#### Plateforme {#platform-6482}

* Les valeurs par défaut des paramètres **[!UICONTROL Délai de connexion]** et **[!UICONTROL Délai d’expiration du socket]** de la configuration de l’agent par défaut (publication) ne sont pas spécifiées (NPR-33708).
* Le planificateur de tâches de maintenance démarre et arrête les tâches de maintenance trop souvent qu’il n’a été configuré (NPR-33520).
* Impossible de télécharger les journaux à l’aide de l’outil de diagnostic sur une instance d’Experience Manager mise à niveau (NPR-34419).

#### Intégrations {#integrations-6482}

* La valeur de `library_path` n’est pas pris en compte lors de la génération [!DNL Adobe Launch] URL de bibliothèque pour les bibliothèques migrées à partir de [!DNL Adobe Dynamic Tag Management]. En outre, les bibliothèques migrées utilisent un préfixe différent de [!DNL Adobe Launch] bibliothèques. (NPR-34238).
* Les propriétés héritées d’un service cloud ne persistent pas lors de la mise à jour des propriétés de page (NPR-33865).

#### Interface utilisateur {#ui-6482}

* L’affichage du nombre de ressources sélectionnées sur une page de recherche est incorrect (NPR-33540).

#### Communities {#communities-6482}

* Les utilisateurs existants d’un groupe de la communauté ajoutés par le biais de l’Admin Console sont supprimés de la liste des utilisateurs lors de toute modification dans la console du groupe de la communauté (NPR-34312).

#### Forms {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] Le pack de correctifs cumulés n’inclut pas de correctifs pour [!DNL Experience Manager Forms]. Les correctifs sont fournis à l’aide d’un package complémentaire [!DNL Forms] distinct. En outre, un programme d’installation cumulatif est publié, qui inclut des correctifs pour [!DNL Experience Manager Forms] sous JEE. Pour plus d’informations, voir [Installation du module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installation du programme d’installation d’AEM Forms JEE](#install-aem-forms-jee-installer).

**Formulaires adaptatifs**

* Lorsqu’il manque un fragment de formulaire adaptatif, le rendu du formulaire adaptatif échoue (NPR-34303).

* La description du contenu d’aide d’un champ de formulaire adaptatif affiche une balise HTML de paragraphe (NPR-34117).

* Lorsque vous ajoutez un conteneur Forms à un [!DNL Experience Manager Sites] , la page affiche le message d’erreur suivant et ne vous permet pas d’ajouter de nouveaux composants (NPR-33858) :

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Lorsque vous sélectionnez la variable **[!UICONTROL Revalider sur le serveur]** et télécharger plusieurs pièces jointes, le formulaire adaptatif ne parvient pas à envoyer (NPR-33701).

* Lorsque vous sélectionnez la variable **[!UICONTROL Utiliser la langue de la page]** et **[!UICONTROL Le formulaire couvre toute la largeur de la page.]** options dans [!DNL Experience Manager Forms] d’un composant [!DNL Experience Manager Sites] , la page ne parvient pas à traduire (NPR-33641).

* Lorsque vous envoyez un formulaire adaptatif compatible avec les analyses incorporé dans un [!DNL Experience Manager Sites] , analytics ne fonctionne pas correctement (NPR-31359).

* Suppression des dépendances sur [!DNL Lodash] et [!DNL backbone] bibliothèques (NPR-33458).

* Le **[!UICONTROL Envoyer vers le point de fin REST]** L’action d’envoi ne fonctionne pas pour un formulaire adaptatif (NPR-34513).

* Accessibilité : Lorsque vous essayez d’envoyer un formulaire adaptatif sans télécharger de pièce jointe pour un champ obligatoire, la sélection ne se déplace pas automatiquement vers le champ de pièce jointe (NPR-34511).

* Les entrées utilisateur ne sont pas codées correctement pour les composants [!DNL Forms] lors de l’envoi d’informations au client (NPR-33611).

**Processus**

* L’opération de purge du workflow d’[!DNL Experience Manager] échoue et affiche le message d’erreur suivant (NPR-33576) :

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Lors de l’installation [!DNL Experience Manager] 6.4.8.1, la variable [!UICONTROL À faire] La liste des éléments ne s’affiche pas sous forme de liens. Le texte des éléments [!UICONTROL À faire] incluent des balises HTML (NPR-34318).

**BackendIntegration**

* Impossible de configurer un modèle de données de formulaire dans un AWS hébergé [!DNL Experience Manager Forms Linux] environnement (NPR-33617).

**Designer**

* When [!DNL Acrobat DC] est installé sur un [!DNL Experience Manager] le serveur Forms, **[!UICONTROL Diffuser le formulaire]** n’est pas disponible dans [!DNL Experience Manager Designer] version 6.x (NPR-34325).

**Document Security**

* Impossible d’exécuter l’opération Sign avec des certificats basés sur HSM dans un fichier de PDF après l’installation [!DNL Experience Manager] 6.4.8.0 (NPR-34309).

**Mise à niveau**

* Lorsque vous mettez à niveau la variable [!DNL JBoss] vers la version 7.0.9 pour [!DNL Experience Manager Forms] avec Document Security dans une [!DNL Linux] , une erreur se produit (CQ-4300546).

Pour plus d’informations sur les mises à jour de sécurité, consultez la [page des bulletins de sécurité d’Experience Manager](https://helpx.adobe.com/fr/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1 est une mise à jour importante qui comporte plusieurs correctifs internes et clients depuis la disponibilité générale d’AEM 6.4 Service Pack 8 (6.4.8.0) en mars 2020.

Le pack de correctifs cumulés AEM 6.4.8.1 nécessite la présence du Service Pack 8 AEM 6.4. Par conséquent, vous devez installer le package AEM Cumulative Fix Pack 6.4.8.1 après avoir installé AEM 6.4 Service Pack 8.

Voici quelques-uns des points forts d’AEM 6.4.8.1 :

* L’accès anonyme à CRXDE Lite n’est pas autorisé pour améliorer la sécurité. Les utilisateurs sont redirigés vers l’écran de connexion. Voir [développement avec CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* Suppression de l’intégration du partage de modules avec Adobe Experience Manager.
* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.21.

Pour plus d’informations sur les CFP et d’autres types de mises à jour, voir [AEM mettre à jour les définitions des véhicules de version](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.1 fournit des correctifs pour les problèmes suivants.

#### Sites {#sites-6481}

* Les utilisateurs anonymes peuvent accéder aux fonctionnalités CRX DE Lite (NPR-33522).
* Lorsque le nom d’un composant local dans une LiveCopy est identique au nom d’un composant dans le plan directeur et que le composant est déployé à partir du plan directeur, le terme _msm_moved n’est pas ajouté au nom du composant local (NPR-33207).
* Les paramètres annexés à la requête d’origine ne sont pas inclus dans l’URL de redirection (NPR-33174).
* Lorsque l’option Coral.Select définit emptyOption=true ou contient un élément par défaut avec la valeur = &quot;&quot;, le fichier dropdownshowhide.js rencontre une erreur : Uncaught TypeError: component.getValue n’est pas une fonction (NPR-33163).
* Lorsqu’un composant inclut un autre composant en tant que data-sly-resource, l’espace réservé du composant de conteneur parent est remplacé par l’espace réservé des composants internes (NPR-33119).
* Lorsque vous basez un fragment de contenu sur un schéma qui contient une zone de texte obligatoire ou un champ de chemin d’accès, l’enregistrement du fragment de contenu échoue (NPR-33007)
* Lorsque vous créez un composant personnalisé à l’aide du composant de fragment d’expérience d’usine et que vous l’utilisez dans les pages AEM Sites, AEM n’affiche pas de références (utilisation) pour le composant personnalisé (NPR-32852).
* Lorsqu’une page AEM Sites fait partie d’un grand jeu de contenu avec plusieurs Live Copies, l’aperçu de l’historique des versions de page ne se charge pas (NPR-32772).
* Lorsque vous convertissez un lancement, il ajoute le mixin &quot;cq:LiveRelationship&quot; à chaque composant ajouté au lancement. Cela a un impact sur tous les lancements, même si un lancement est créé avec ou sans sélectionner l’option — Hériter des données actives de la page source — (NPR-32664).
* Au démarrage de la pagination, le sélecteur de fragments d’expérience ne charge pas tous les éléments (NPR-32605).
* Impossible de créer un lancement pour une page AEM Sites. La création d’un lancement entraîne une erreur (NPR-32544).
* La fonction Gérer la publication n’inclut pas les ressources référencées dans le workflow de demande d’activation (NPR-32463).
* Le contrôle de l’intégrité du Dispatcher affiche un message d’avertissement `Invalid cookie header` dans les journaux (NPR-33630).
* L’intégration de Salesforce est vulnérable à SSRF (NPR-32671).
* XSS reflété dans PreferencesServlet (NPR-33439).

#### Ressources {#assets-6481}

* Le nombre de ressources ne change pas en fonction du changement de sélection en mode Liste (NPR-33285).

* Le bouton Suivant n’est pas activé lors de la sélection du noeud parent (où un seul dossier enfant est visible), puis de la sélection du dossier enfant (NPR-33284).

* L’interface utilisateur tactile ne parvient pas à effectuer le rendu (avec erreur) pour les utilisateurs qui n’ont pas d’accès en lecture sur la racine du référentiel, lorsque le mode DMS7 ou hybride est activé (NPR-33175).

* Les caractères GB18030 apparaissant dans les noms de dossier et de ressource sont laissés vides dans les fichiers zip téléchargés (NPR-33150).

* Un dossier supplémentaire est créé lors du recadrage intelligent d’une ressource qui se trouve dans un dossier parent avec un point `.` dans son nom (NPR-32755).

* Le chargement différé n’est pas déclenché et pas plus de 100 ressources s’affichent lors de la sélection pour passer en revue les tâches de la boîte de réception de notifications (NPR-32749).

* La page du lien vers la collection de partage est endommagée en raison d’un changement dans coral-info (NPR-32510).

* Le traitement des ressources pendant le chargement en masse est bloqué (CQ-4293916).

* Vulnérabilité SSRF dans Experience Manager (NPR-33437).

#### Plateforme {#platform-6481}

* Le filtre [!DNL Sling] n’est pas appelé si l’entrée map `sling:match` est créée sous `/etc/maps` (NPR-33308).
* Tous les agents de vidage sont déclenchés lors de la désactivation d’une page (NPR-32941).
* Lorsque vous utilisez la variable `ScriptProcessor` Pour réduire une bibliothèque JavaScript, le fichier journal affiche un message d’erreur indiquant que le code JavaScript n’est pas conforme au mode strict. L’API ne fournit pas d’option pour activer ou désactiver le mode strict. (NPR-32746).
* Lorsqu’une requête SQL s’exécute pendant une durée plus longue, par exemple 7 heures, AEM arrête de répondre (NPR-33043).

#### Interface utilisateur {#ui-6481}

* Lorsque vous recherchez ou parcourez un chemin à l’aide d’une boîte de dialogue de sélection, la boîte de dialogue de sélection affiche tout le contenu du noeud JCR sélectionné au lieu d’afficher uniquement les images (NPR-32712).

#### Projets de traduction {#tranlation-6481}

* Une erreur `NullPointerException` s’affiche dans les journaux lors de l’exécution d’une tâche de traduction (NPR-32220).

#### Intégrations {#integrations-6481}

* Cross-site scripting pour JSON (NPR-32745).

#### Communities {#communities-6481}

* Les auteurs, après la création d’un groupe, ne sont pas redirigés vers la section [!UICONTROL Groupe de la communauté] dans [!DNL Internet Explorer] 11 (NPR-33202).
* Une erreur se produit lors de l’accès à la page [!UICONTROL Flux d’activités] (NPR-33152).
* La modification d’un groupe [!DNL Communities] et de l’image de la miniature ne mettent pas à jour l’image de la miniature du groupe (NPR-32603).
* Lors de la création d’une version de notifications et d’abonnements au contenu généré par l’utilisateur (UGC), un ID incorrect de page source est stocké (, CQ-4289703).
* Problème de cross-site scripting (NPR-33212).

#### Workflow {#workflow-6481}

* Certains composants ne s’affichent pas dans la boîte de dialogue qui s’affiche lorsqu’un utilisateur termine un workflow qui comprend une [!UICONTROL Étape Participant de boîte de dialogue] (NPR-32989).

* Le chargement de l’option [!UICONTROL Chronologie] dans le rail de gauche prend plus de temps que prévu (NPR-32850).

#### Forms {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack n’inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un package complémentaire Forms distinct. En outre, un programme d’installation cumulatif est publié, qui inclut des correctifs pour AEM Forms sous JEE. Pour plus d’informations, voir [Installation du module complémentaire AEM Forms](#install-aem-forms-add-on-package) et [Installation du programme d’installation d’AEM Forms JEE](#install-aem-forms-jee-installer).

* Correspondence Management : Lorsqu’un utilisateur colle du contenu à partir d’une [!DNL Word] document, le fragment de document texte ne conserve pas la mise en forme (NPR-33213).
* Formulaires adaptatifs : une nouvelle ligne ajoutée à une chaîne dans un dictionnaire de formulaires adaptatifs ajoute les caractères `&#xa;` au dictionnaire (NPR-33265).
* Formulaires adaptatifs : l’utilisateur ne peut pas enregistrer de formulaire adaptatif avec plusieurs pièces jointes (NPR-33214).
* Adaptive Forms : `AddInstance` et `RemoveInstance` Les méthodes de la classe Instance Manager n’ajoutent pas de nombre dynamique d’instances pour les fragments de chargement différé sur [!DNL Internet Explorer 11] (NPR-33201).
* Adaptive Forms : Analytics activé sur un formulaire adaptatif incorporé dans un [!DNL Sites] n’enregistrez pas de données pour les événements d’envoi et d’abandon (NPR-31359).
* Adaptive Forms : Lorsqu’un utilisateur colle le contenu à partir d’une [!DNL Word] à un formulaire adaptatif et l’envoyer, le formulaire adaptatif envoyé comprend des caractères Unicode. En outre, la conversion du PDF vers PDF/A échoue en raison de caractères Unicode (NPR-33348).
* Intégration backend : les demandes de modèle de données de formulaire échouent lorsque le jeton d’actualisation expire en raison d’un statut inactif incorrect (NPR-33168).
* Document Services : Le service de conversion de PDF ne parvient pas à convertir les documents de PDF en PostScript en raison de l’absence de jars Gibson pour [!DNL WebLogic] sur le [!DNL Linux] server (NPR-33515, CQ-4292239).
* Document Services : Lorsqu’un utilisateur convertit un fichier texte en PDF, les caractères japonais ne s’affichent pas correctement (NPR-33239).
* XSS stocké avec le GuideSOMProviderServlet (NPR-32701).

## Installation de la version 6.4.8.4 {#install}

### Configuration requise {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Pour les clients disposant de Feature Packs installés sur AEM 6.4. Les Feature Packs facultatifs fournis par Adobe ont des dépendances sur la version de publication et les Service Packs. Si vous avez installé un Feature Pack, contactez l’équipe d’assistance AEM clientèle pour valider la compatibilité de ces Feature Packs avec ce pack de correctifs cumulatif pour AEM 6.4.

* AEM 6.4.8.4 nécessite AEM 6.4.8.0. Veuillez consulter [documentation de mise à niveau](../sites-deploying/upgrade.md) pour obtenir des instructions détaillées.
* Sur un déploiement avec MongoDB et plusieurs instances, installez AEM 6.4.8.4 sur l’une des instances d’auteur à l’aide du gestionnaire de modules.
* Avant d’installer le pack de correctifs cumulatifs, veillez à disposer d’un instantané ou d’une nouvelle sauvegarde de votre instance AEM.
* Redémarrez l’instance avant l’installation. Bien que cela ne soit nécessaire que lorsque l’instance est toujours en mode de mise à jour (et c’est le cas lorsque l’instance vient d’être mise à jour à partir d’une version antérieure), il est généralement recommandé que l’instance s’exécute pendant une plus longue période.

>[!NOTE]
>
>Adobe ne recommande pas de supprimer ou de désinstaller le package AEM 6.4.8.4.

### Installation du pack de correctifs cumulés {#install-cumulative-fix-pack}

Procédez comme suit pour installer le pack de correctifs cumulés sur une instance AEM 6.4.8.0 existante :

1. Cliquez sur le lien [Distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) pour télécharger le package.

1. Ouvrez [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.

1. Sélectionnez le nom du package et cliquez sur **[!UICONTROL Installer]**.

>[!NOTE]
>
>**La boîte de dialogue de l’interface utilisateur de Package Manager se ferme parfois de manière impromptue lors de l’installation de la version 6.4.8.4**
>
>Par conséquent, il est recommandé d’attendre que les journaux d’erreurs se stabilisent avant d’accéder à l’instance. L’utilisateur doit attendre les journaux spécifiques liés à la désinstallation du lot de mise à jour avant de s’assurer que l’installation est réussie. Cela se produit généralement sur Safari, mais peut se produire par intermittence sur n’importe quel navigateur.

### Installation automatique {#auto-installation}

Il existe deux manières d’installer automatiquement AEM 6.4.8.4 dans une instance en cours d’exécution :

A. Placez le package dans ..*/crx-quickstart/install* pendant l’exécution du serveur. Le package est automatiquement installé.

B. Utilisez la variable [API HTTP à partir de Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - Assurez-vous que vous utilisez `cmd=install&recursive=true` - pour que le package imbriqué soit installé.

>[!NOTE]
>
>AEM 6.4.8.4 ne prend pas en charge l’installation de Bootstrap.

### Validation de l’installation {#validate-install}

1. La page Informations sur le produit (*/system/console/productinfo*) doit maintenant afficher la chaîne de version mise à jour &quot;Adobe Experience Manager, version 6.4.8.4&quot; sous Produits installés.
1. Tous les lots OSGI sont ACTIFS ou FRAGMENT dans la console OSGI (utiliser la console web : /system/console/bundles).
1. Le lot OSGI org.apache.jackrabbit.oak-core est sur la version 1.8.17 ou ultérieure (Utiliser la console web : /system/console/bundles).

Pour déterminer la plateforme certifiée pour exécuter cette version d’AEM Sites et d’Assets, voir [Exigences techniques](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Une fois l’installation du module terminée, un message d’information s’affiche pour vous informer que le module de contenu a bien été installé, par exemple : **&quot;Le package de contenu AEM-6.4-Service-Pack-8 a été installé avec succès.&quot;**

### Mise à jour des visionneuses Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.4 contient une nouvelle version des visionneuses Dynamic Media (5.10.1) qui permet de rechercher des noms en double sur la page Paramètre d’image prédéfini. Il est conseillé aux clients Dynamic Media d’exécuter la commande suivante pour mettre à jour les paramètres prédéfinis de la visionneuse prêts à l’emploi.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

qui copiera les nouveaux paramètres prédéfinis de visionneuse à l’emplacement /conf.

### Installation AEM package de module complémentaire Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] publie les packages de modules complémentaires une semaine après la date de publication prévue du pack de correctifs cumulés [!DNL Experience Manager].

>[!NOTE]
>
>Ignorez si vous n’utilisez pas AEM Forms. Les correctifs dans AEM Forms sont fournis par le biais d’un module complémentaire distinct.

1. Vérifiez que vous avez installé le AEM Cumulative Fix Pack.
1. Téléchargez le module complémentaire de formulaires correspondant répertorié à l’adresse [Versions d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr#forms-updates) pour votre système d’exploitation.
1. Installez le module complémentaire Forms comme décrit dans la section [Installation des packages de modules complémentaires AEM forms](https://experienceleague.adobe.com/docs/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installation du programme d’installation d’AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms sous JEE. Les correctifs dans AEM Forms JEE sont fournis dans un programme d’installation distinct.

Pour plus d’informations sur l’installation du programme d’installation cumulatif pour AEM Forms JEE et la configuration après le déploiement, voir [Programme d’installation des correctifs d’AEM Forms JEE](jee-patch-installer-64.md).

>[!NOTE]
>
>Après avoir installé le programme d’installation cumulatif de Experience Manager Forms sous JEE, installez le dernier package complémentaire Forms, supprimez le package complémentaire Forms du dossier `crx-repository\install` et redémarrez le serveur.

### Uber Jar {#uber-jar}

Uber Jar pour AEM 6.4.8.4 est disponible dans la section [Référentiel Maven Central](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/).

Pour utiliser Uber Jar dans un projet Maven, reportez-vous à l’article [Comment utiliser Uber Jar](../sites-developing/ht-projects-maven.md) et incluez la dépendance suivante dans votre projet POM :

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.4</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar et d’autres artefacts associés sont disponibles sur le référentiel central de Maven au lieu du référentiel Maven public Adobe (repo.adobe.com). Le fichier UberJar principal est renommé `uber-jar-<version>.jar`. Par conséquent, il n’y a pas de `classifier`, avec `apis` comme valeur, pour la propriété `dependency` balise .

## Fonctionnalités supprimées / obsolètes {#removed-deprecated-features}

Cette section répertorie les fonctionnalités qui ont été supprimées ou désignées comme obsolètes dans AEM 6.4.

| Domaine | Fonctionnalité | Remplacement | Version  |
|---|---|---|---|
| Ressources | Gestion de l’action de balise pour les sous-ressources | Aucun remplacement | AEM 6.4.2.0 |
| Intégration d’Assets et de Adobe Creative Cloud | [Le partage de dossiers AEM vers Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) a été introduit dans AEM 6.2 afin de permettre aux créatifs d’accéder aux ressources depuis AEM. Adobe Asset Link, une nouvelle fonctionnalité proposée dans l’application Creative Cloud, offre une expérience utilisateur améliorée et un accès plus puissant aux ressources d’AEM directement à partir de Photoshop, InDesign et Illustrator. Adobe n’apporte pas d’autres améliorations à la fonctionnalité de partage de dossiers. Bien que la fonctionnalité soit incluse dans AEM, les clients sont (il est vivement conseillé d’utiliser le remplacement). | Adobe d’Asset Link ou de l’appli de bureau. Pour plus d’informations, voir [Intégration d’AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md) article. | AEM 6.4.4.0 |

## Problèmes connus {#known-issues}

* Si vous effectuez une mise à niveau à partir de [!DNL Experience Manager] 6.4 à [!DNL Experience Manager] 6.5, certains lots peuvent ne pas afficher leur état comme `Active`. Installez la dernière [!DNL Experience Manager] 6.5 Service Pack pour résoudre le problème.

Pour plus d’informations sur les problèmes connus du Service Pack AEM 6.4.8.0, voir [Notes de mise à jour d’AEM 6.4.8.0 Service Pack](sp-release-notes.md).

## Lots OSGi et packages de contenu inclus {#osgi-bundles-and-content-packages-included}

Les documents texte suivants répertorient les lots OSGi et les packages de contenu inclus dans AEM 6.4.8.4.

Liste des lots OSGi inclus dans AEM 6.4.8.4

[Obtenir le fichier](assets/6.4.8.4_osgi_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.8.4

[Obtenir le fichier](assets/6.4.8.4_content_packages.txt)

## Ressources utiles {#helpful-resources}

* [Notes de mise à jour d’AEM 6.4](../release-notes/release-notes.md)
* [Page de produits AEM ](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentation d’AEM 6.4](https://helpx.adobe.com/fr/support/experience-manager/6-4.html)
* Abonnement aux [mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html)

## Sites à accès limité {#restricted-sites-new}

Ces sites sont réservés aux clients. Si vous êtes client et avez besoin d’un accès, contactez votre gestionnaire de compte d’Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance clientèle](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=fr)
