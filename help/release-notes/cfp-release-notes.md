---
title: Notes de mise à jour cumulées du pack de correctifs AEM 6.4
description: Notes de mise à jour spécifiques aux packs de correctifs cumulés Adobe Experience Manager 6.4.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 3b96c351b3deb72e1381e101433f4246fd26af1b
workflow-type: tm+mt
source-wordcount: '3402'
ht-degree: 16%

---


# Notes de mise à jour cumulées du pack de correctifs AEM 6.4 {#aem-cumulative-fix-pack-release-notes}

## Informations sur la version {#release-information}

| Produits | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.2 |
| Type | Pack de correctifs cumulés  |
| Date | 3 septembre 2020 |
| Condition requise | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL de téléchargement | aem 6.4.8.2 sur la distribution de [logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-2.0.zip) |

## Fonctionnalités présentes dans AEM 6.4.8.2 {#what-s-included-in-aem}

aem Cumulative Fix Pack 6.4.8.2 est une mise à jour importante qui comprend plusieurs correctifs internes et clients depuis la disponibilité générale d&#39;AEM 6.4 Service Pack 8 (6.4.8.0) en mars 2020.

aem 6.4.8.2 est un Cumulative Fix Pack (CFP) qui dépend de AEM 6.4 Service Pack 8. Installez le CFP après avoir installé AEM 6.4 Service Pack 8.

Dans AEM 6.4.8.2, le référentiel intégré (Apache Jackrabbit Oak) est mis à jour vers la version 1.8.22.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

Adobe Experience Manager 6.4.8.2 fournit des correctifs pour les problèmes suivants.

### Sites {#sites-6482}

* Si le `RolloutConfigManagerFactoryImpl` serveur ne peut pas charger une configuration de déploiement, il ne tente pas de charger les configurations manquantes. Elle renvoie les configurations mises en cache (NPR-34091).
* Dans le composant noyau de texte, après avoir utilisé l’option d’édition HTML source, la classe de la `em` balise est supprimée (NPR-34080).
* Lorsque vous effectuez une mise à niveau de Experience Manager 6.2 vers Experience Manager 6.5, le composant Parsys des modèles statiques ne s’affiche pas correctement. La hauteur du composant Parsys est définie sur 0 et les composants qu&#39;il contient ne sont pas visibles (NPR-34044).
* Les informations d’étiquette ne s’affichent pas sur les composants autorisés dans l’éditeur de modèles (NPR-33908).

   ![Libellés manquants dans le conteneur de mise en page](assets/33908_missing_labels.png)

* Les utilisateurs ne peuvent pas ajouter ni modifier de composants à l&#39;analyse après le quatrième niveau de composants imbriqués (NPR-33873).
* Si le contenu initial d&#39;un modèle modifiable est modifié puis que le modèle est publié, toutes les nouvelles pages créées avec ce modèle affichent la date de publication du modèle même si les pages ne sont pas publiées (NPR-33822).
* Les `cq:acLinks` propriétés et les `cq:acUUID` propriétés de [!DNL Adobe Campaign] la copie sont supprimées lors de l&#39;opération de copier-coller (NPR-33793).
* Dans l’onglet Utilisation  en direct, seuls 49 résultats s’affichent. Il n&#39;affiche pas toutes les utilisations du composant (NPR-33710).
* Une page Web contenant `/` un caractère dans l’URL ne répond plus lors de la création. Lorsqu&#39;un composant est ajouté lors de la création, l&#39;utilisation du processeur augmente et le navigateur cesse de répondre (NPR-33625).
* En mode de modification en ligne dans [!DNL RTE], le fait de faire glisser une image ne fonctionne pas pour le composant Texte (NPR-33579).
* Il est possible de créer un composant dans une page de plan avec le même nom que le nom de la page. Lors du déploiement, un tel composant est renommé par suffixe `_msm_moved`. Cependant, le composant est déplacé à la fin du système [!UICONTROL de] paragraphes (NPR-33534).
* La promotion du lancement ne publie pas de pages lorsque la propriété [!UICONTROL inclure des sous-pages] n&#39;est pas cochée sur la première racine de contenu (NPR-33533).
* La redirection vers [!DNL Experience Manager] la page avec ancrage ne fonctionne pas sur l’instance d’auteur, car `PageRedirectServlets` elle place une chaîne de requête après un fragment d’URL ou une ancre (NPR-34287).
* `PageRedirectServlet` s’ajoute `.html` après le mappage Sling conduisant à des échecs de liens (NPR-34271).
* Vous pouvez suspendre l’affichage [!DNL Live Copy] d’une page et l’héritage est rompu comme dans le mode Editeur. Cependant, dans les propriétés Page, l’icône représentant l’héritage indique à tort que l’héritage existe et n’est pas rompu (NPR-34096).
* Problème d’affichage des composants autorisés dans la page Modifier le modèle (CQ-4297295).
* Après la mise à niveau de Chrome et Firefox, les menus contextuels ne fonctionnent plus comme prévu. Lors du chargement des propriétés de la page, le panneau n’apparaît pas lorsqu’il contient des données (CQ-4292995).

### Ressources {#assets-6482}

* L’extraction de texte des fichiers PDF téléchargés ne fonctionne pas et la recherche de texte intégral de certains mots dans un fichier PDF ne parvient pas à récupérer ce fichier PDF (NPR-34165).

   >[!NOTE]
   >Pour que ce correctif fonctionne, redémarrez votre instance Adobe Experience Manager après avoir installé le Service Pack 6.4.8.2.

* Les barres obliques inverses sont ajoutées avant les caractères spéciaux dans les suggestions de recherche de ressources, qui portent des caractères spéciaux dans leur nom (NPR-33833).

* Les filtres personnalisés enregistrés en tant que collections dynamiques ne sont pas correctement appliqués aux ressources. Par conséquent, les résultats de la recherche ne sont pas exacts (NPR-33725).

* La chronologie d’une ressource dans un dossier qui a été réorganisé indique que la ressource a été déplacée (NPR-33580).

* L’annulation de la publication des ressources en vrac à partir de [!DNL Brand Portal] entraîne `Request-URI Too Long` une erreur (NPR-34158).

* Dans la vue de colonne si l’utilisateur sélectionne l’option [!UICONTROL Filtrer] après avoir sélectionné un ensemble de ressources (les ressources sont désélectionnées), puis sélectionne un autre ensemble de ressources à déplacer, les ressources précédemment sélectionnées sont également déplacées vers le nouvel emplacement (NPR-34018).

* La barre de défilement n’est pas visible dans la vue de liste, même s’il existe de nombreux actifs à inclure dans la page (NPR-34156).

* La page [!UICONTROL Gérer la publication] pour les ressources est rompue et les options qui s’y trouvent ne fonctionnent pas (CQ-4302509).

**Dynamic Media**

* La fonctionnalité de recadrage dynamique échoue avec une erreur lorsque le profil d’image est ajouté à un dossier ayant plusieurs proportions (par exemple, 11) (NPR-34083).

* Les modifications apportées aux paramètres d’image prédéfinis dans [!UICONTROL Adobe Experience Manager] ne sont pas synchronisées avec Scene7 Publishing System (NPR-34284, CQ-4299713).

* Le libellé du modificateur [!UICONTROL PANORAMICVIEW_AUTOROTATE] est absent de l’onglet [!UICONTROL Comportement] de la page Editeur [!UICONTROL de paramètres prédéfinis de la] visionneuse (CQ-4302043).

### Plate-forme {#platform-6482}

* Les valeurs par défaut des paramètres **[!UICONTROL Connect Timeout]** et **[!UICONTROL Socket Timeout]** pour la configuration de l’agent par défaut (publication) ne sont pas spécifiées (NPR-33708).
* Le Planificateur de la tâche de maintenance début et arrête les tâches de maintenance trop souvent que configurées (NPR-33520).
* Impossible de télécharger les journaux à l&#39;aide de l&#39;outil Diagnostic sur une instance de Experience Manager mise à niveau (NPR-34419).

### Intégrations {#integrations-6482}

* La valeur de `library_path` n’est pas prise en compte lors de la génération de l’URL [!DNL Adobe Launch] de bibliothèque pour les bibliothèques migrées depuis [!DNL Adobe Dynamic Tag Management]. En outre, les bibliothèques migrées utilisent un préfixe différent de celui des [!DNL Adobe Launch] bibliothèques. (NPR-34238).
* Les propriétés héritées d’un service cloud ne sont pas conservées lors de la mise à jour des propriétés de page (NPR-33865).

### Interface utilisateur {#ui-6482}

* L&#39;affichage du nombre de ressources sélectionnées sur une page de recherche est incorrect (NPR-33540).

### Communities {#communities-6482}

* Les utilisateurs existants d’un groupe de la communauté ajouté via la console d’administration sont supprimés de la liste d’utilisateurs lors de toute modification de la console de groupe de la communauté (NPR-34312).

### Formulaires {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] Cumulative Fix Pack n’inclut pas de correctifs pour [!DNL Experience Manager Forms]. They are delivered using a separate [!DNL Forms] add-on package. In addition, a cumulative installer is released that includes fixes for [!DNL Experience Manager Forms] on JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

**Formulaires adaptatifs**

* S’il manque un fragment de formulaire adaptatif, le rendu du formulaire adaptatif échoue (NPR-34303).

* La description du contenu d’aide d’un champ de formulaire adaptatif affiche une balise HTML de paragraphe (NPR-34117).

* Lorsque vous ajoutez un conteneur Forms sur une [!DNL Experience Manager Sites] page, la page affiche le message d’erreur suivant et ne vous permet pas d’ajouter de nouveaux composants (NPR-33858) :

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Lorsque vous sélectionnez la propriété **[!UICONTROL Revalider sur le serveur]** et téléchargez plusieurs pièces jointes, le formulaire adaptatif ne parvient pas à être envoyé (NPR-33701).

* Lorsque vous sélectionnez l’option **[!UICONTROL Utiliser la langue]** de la page et le **[!UICONTROL formulaire couvre toute la largeur des options Page]** du [!DNL Experience Manager Forms] composant sur une [!DNL Experience Manager Sites] page, la traduction de la page échoue (NPR-33641).

* Lorsque vous envoyez un formulaire adaptatif compatible avec les analyses incorporé dans une [!DNL Experience Manager Sites] page, l’analyse ne fonctionne pas correctement (NPR-31359).

* Suppression des dépendances sur [!DNL Lodash] et [!DNL backbone] bibliothèques (NPR-33458).

* L’action d’envoi **[!UICONTROL Envoyer vers le point de terminaison]** REST ne fonctionne pas pour un formulaire adaptatif (NPR-34513).

* Accessibilité : Lorsque vous tentez d’envoyer un formulaire adaptatif sans télécharger de pièce jointe pour un champ obligatoire, la cible d’action ne se déplace pas automatiquement vers le champ de pièce jointe (NPR-34511).

**Processus**

* [!DNL Experience Manager] Échec de l&#39;opération de purge du flux de travail et affiche le message d&#39;erreur suivant (NPR-33576) :

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Lorsque vous installez [!DNL Experience Manager] 6.4.8.1, la liste [!UICONTROL Tâches] des éléments ne s’affiche pas sous forme de liens. Le texte des éléments [!UICONTROL À faire] comprend des balises HTML (NPR-34318).

**BackendIntegration**

* Impossible de configurer un modèle de données de formulaire dans un [!DNL Experience Manager Forms Linux] environnement hébergé par AWS (NPR-33617).

**Designer**

* Une fois [!DNL Acrobat DC] installé sur un serveur [!DNL Experience Manager] Forms, l’option **[!UICONTROL Diffuser le formulaire]** n’est pas disponible dans [!DNL Experience Manager Designer] la version 6.x (NPR-34325).

**Document Security**

* Impossible d&#39;exécuter l&#39;opération Sign avec des certificats basés sur HSM dans un fichier PDF après avoir installé la version [!DNL Experience Manager] 6.4.8.0 (NPR-34309).

**Mise à niveau**

* Lorsque vous mettez à niveau la [!DNL JBoss] version vers la version 7.0.9 pour [!DNL Experience Manager Forms] avec Document Security dans un [!DNL Linux] environnement, une erreur se produit (CQ-4300546).

Pour plus d&#39;informations sur les mises à jour de sécurité, consultez la page [Bulletins de sécurité des](https://helpx.adobe.com/security/products/experience-manager.html)Experience Manager.

## Correctifs et packs de fonctionnalités inclus dans les packs de correctifs cumulés précédents {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

aem Cumulative Fix Pack 6.4.8.1 est une mise à jour importante qui comprend plusieurs correctifs internes et clients depuis la disponibilité générale d&#39;AEM 6.4 Service Pack 8 (6.4.8.0) en mars 2020.

aem Cumulative Fix Pack 6.4.8.1 dépend de AEM 6.4 Service Pack 8. Par conséquent, vous devez installer AEM Cumulative Fix Pack 6.4.8.1 après avoir installé AEM 6.4 Service Pack 8.

Voici quelques-uns des points saillants de l&#39;AEM 6.4.8.1 :

* L&#39;accès anonyme au CRXDE Lite n&#39;est pas autorisé pour améliorer la sécurité. Les utilisateurs sont redirigés vers l’écran de connexion. See [developing with CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* Suppression de l’intégration Package Share avec Adobe Experience Manager.
* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.21.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

Adobe Experience Manager 6.4.8.1 apporte des correctifs aux problèmes suivants.

#### Sites {#sites-6481}

* Les utilisateurs anonymes peuvent accéder aux fonctionnalités CRX DE Lite (NPR-33522).
* Lorsque le nom d&#39;un composant local d&#39;un LiveCopy est identique au nom d&#39;un composant du plan et que le composant est déployé à partir du plan, le terme _msm_move n&#39;est pas ajouté au nom du composant local (NPR-33207).
* Les paramètres annexés à la requête d’origine ne sont pas inclus dans l’URL de redirection (NPR-33174).
* Lorsque l&#39;option Coral.Select définit emptyOption=true ou contient un élément par défaut avec la valeur = &quot;&quot;, le fichier dropdownshowhide.js rencontre une erreur : Erreur de type non interceptée : component.getValue n&#39;est pas une fonction (NPR-33163).
* Lorsqu&#39;un composant comprend un autre composant en tant que ressource de données, l&#39;espace réservé du composant de conteneur parent est remplacé par l&#39;espace réservé des composants internes (NPR-33119).
* Lorsque vous basez un fragment de contenu sur un schéma et qu’il contient une zone de texte obligatoire ou un champ de chemin d’accès, l’enregistrement du fragment de contenu échoue (NPR-33007)
* Lorsque vous créez un composant personnalisé à l’aide du composant de fragment d’expérience prêt à l’emploi et que vous l’utilisez dans les pages AEM Sites, AEM n’affiche pas les références (utilisation) du composant personnalisé (NPR-32852).
* Lorsqu’une page AEM Sites fait partie d’un grand jeu de contenu comportant plusieurs copies en direct, la prévisualisation d’historique des versions de page ne se charge pas (NPR-32772).
* Lorsque vous promouvez un lancement, il ajoute le mixin &quot;cq:LiveRelationship&quot; à chaque composant ajouté au lancement. Elle a un impact sur tous les lancements, indépendamment du fait qu&#39;un lancement soit créé avec ou sans sélectionner l&#39;option — Hériter les données en direct de la page source — (NPR-32664).
* Lors des débuts de pagination, le sélecteur de fragments d’expérience ne charge pas tous les éléments (NPR-32605).
* Impossible de créer un lancement pour une page AEM Sites. La création du lancement génère une erreur (NPR-32544).
* Gérer la publication n’inclut pas les ressources référencées dans le processus de demande d’activation (NPR-32463).
* La vérification d&#39;intégrité du répartiteur affiche un message d&#39; `Invalid cookie header` avertissement dans les fichiers journaux (NPR-33630).
* L&#39;intégration de Salesforce est vulnérable au SSRF (NPR-32671).
* XSS reflété dans PreferencesServlet (NPR-33439).

#### Ressources {#assets-6481}

* Le nombre d’actifs ne change pas en fonction du changement de sélection dans la Vue de Liste (NPR-33285).

* Le bouton Suivant n’est pas activé lors de la sélection du noeud parent (où un dossier enfant unique est visible), puis lors de la sélection du dossier enfant (NPR-33284).

* L’interface utilisateur tactile ne parvient pas à s’afficher (avec erreur) pour les utilisateurs qui n’ont pas accès en lecture à la racine du référentiel, lorsque le mode DMS7 ou hybride est activé (NPR-33175).

* Les caractères GB18030 se trouvant dans les dossiers et les noms de fichier deviennent vides dans les fichiers zip téléchargés (NPR-33150).

* Un dossier supplémentaire est créé lors du recadrage intelligent d’un fichier se trouvant dans un dossier parent dont le nom contient un caractère point `.` (NPR-32755).

* Le chargement différé n&#39;est pas déclenché et pas plus de 100 ressources s&#39;affichent lors de la sélection pour consulter les tâches de la boîte de réception des notifications (NPR-32749).

* La page de lien vers la collecte de partage est interrompue en raison d&#39;un changement dans coral-info (NPR-32510).

* Le traitement des ressources pendant le chargement en masse est bloqué (CQ-4293916).

* Vulnérabilité SSRF en Experience Manager (NPR-33437).

#### Plate-forme {#platform-6481}

* Le [!DNL Sling] filtre n’est pas appelé si l’entrée de `sling:match` mappage est créée sous `/etc/maps` (NPR-33308).
* Tous les agents de vidage sont déclenchés lors de la désactivation d&#39;une page (NPR-32941).
* Lorsque vous utilisez l’ `ScriptProcessor` API pour réduire la taille d’une bibliothèque JavaScript, le fichier journal affiche un message d’erreur indiquant que le code JavaScript n’est pas conforme au mode strict. L’API ne fournit pas d’option permettant d’activer ou de désactiver le mode strict. (NPR-32746).
* Lorsqu&#39;une requête SQL s&#39;exécute plus longtemps, par exemple pendant 7 heures, AEM cesse de répondre (NPR-33043).

#### Interface utilisateur {#ui-6481}

* Lorsque vous recherchez ou parcourez un chemin à l’aide d’une boîte de dialogue de sélection, la boîte de dialogue de sélection affiche tout le contenu du noeud JCR sélectionné au lieu d’afficher uniquement les images (NPR-32712).

#### Projets de traduction {#tranlation-6481}

* Une `NullPointerException` erreur s&#39;affiche dans les journaux d&#39;exécution d&#39;une tâche de traduction (NPR-32220).

#### Intégrations {#integrations-6481}

* Script intersite pour JSON (NPR-32745).

#### Communities {#communities-6481}

* Les auteurs, après avoir créé un nouveau groupe, ne sont pas redirigés vers la section Groupe  communautaire le [!DNL Internet Explorer] 11 (NPR-33202).
* Une erreur se produit lors de l&#39;accès à la page [!UICONTROL Activité Stream] (NPR-33152).
* La modification d&#39;un [!DNL Communities] groupe et de l&#39;image miniature n&#39;actualise pas l&#39;image miniature du groupe (NPR-32603).
* Lors de la création d’une version de notifications et d’abonnements de contenu généré par l’utilisateur (UGC), un ID incorrect de la page source est stocké (CQ-4289703).
* Problème de script intersite (NPR-33212).

#### Workflow {#workflow-6481}

* Certains composants ne s’affichent pas dans la boîte de dialogue qui s’affiche lorsqu’un utilisateur termine un processus incluant une étape [!UICONTROL de participant à la] boîte de dialogue (NPR-32989).

* Le chargement de l&#39;option [!UICONTROL Chronologie] dans le rail de gauche prend plus de temps que prévu (NPR-32850).

#### Formulaires {#forms-6481}

>[!NOTE]
>
>aem Cumulative Fix Pack n&#39;inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un module complémentaire Forms distinct.  En outre, un programme d’installation cumulatif est publié, qui comprend des correctifs pour AEM Forms on JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* Correspondence Management : Lorsqu’un utilisateur colle du contenu à partir d’un [!DNL Word] document, le fragment de document de texte ne conserve pas la mise en forme (NPR-33213).
* Forms adaptatif : Une nouvelle ligne d’une chaîne dans un dictionnaire de formulaires adaptatifs ajoute `&#xa;` des caractères au dictionnaire (NPR-33265).
* Forms adaptatif : L’utilisateur ne peut pas enregistrer de formulaire adaptatif contenant plusieurs pièces jointes (NPR-33214).
* Forms adaptatif : `AddInstance` et `RemoveInstance` les méthodes de la classe Instance Manager n’ajoutent pas de nombre dynamique d’instances pour les fragments de chargement différé sur [!DNL Internet Explorer 11] (NPR-33201).
* Forms adaptatif : Les analyses activées sur un formulaire adaptatif incorporé dans une [!DNL Sites] page n’enregistrent pas les données des événements Envoyer et Abandon (NPR-31359).
* Forms adaptatif : Lorsqu’un utilisateur colle le contenu d’un [!DNL Word] document à un formulaire adaptatif et l’envoie, le formulaire adaptatif envoyé comprend des caractères Unicode. En outre, la conversion PDF/A échoue en raison de caractères Unicode (NPR-33348).
* BackendIntegration : Les demandes de modèle de données de formulaire échouent lorsque le jeton d’actualisation expire en raison d’un état inactif incorrect (NPR-33168).
* Document Services : Le service Convert PDF ne parvient pas à convertir les documents PDF en PostScript en raison de l’absence de jars Gibson pour [!DNL WebLogic] [!DNL Linux] le serveur (NPR-33515, CQ-4292239).
* Document Services : Lorsqu’un utilisateur convertit un fichier texte au format PDF, les caractères japonais ne s’affichent pas correctement (NPR-33239).
* Stockage de XSS avec le GuideSOMProviderServlet (NPR-32701).

## Install 6.4.8.2 {#install}

### Conditions requises {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Pour les clients dont les Feature Packs sont installés sur AEM 6.4. Les Feature Packs facultatifs fournis par Adobe dépendent de la version de publication et des Service Packs. Si vous disposez d’un pack de fonctionnalités, contactez l’équipe d’assistance AEM clientèle afin de vérifier la compatibilité de ces packs de fonctionnalités avec ce pack de correctifs cumulatif pour AEM 6.4.

* AEM 6.4.8.2 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* Lors d’un déploiement avec MongoDB et plusieurs instances, installez AEM 6.4.8.2 sur l’une des instances d’auteur à l’aide du gestionnaire de modules.
* Avant d’installer le pack de correctifs cumulatifs, veillez à disposer d’un instantané ou d’une nouvelle sauvegarde de votre instance AEM.
* Redémarrez l’instance avant l’installation. Cela est nécessaire uniquement lorsque l’instance reste en mode de mise à jour (ce qui est le cas lorsque l’instance vient d’être mise à jour depuis une version antérieure). Toutefois, cela est généralement recommandé si l’instance s’est exécutée pendant longtemps.

>[!NOTE]
>
>Adobe recommande de ne pas supprimer ni désinstaller le package AEM 6.4.8.2.

### Installation du Cumulative Fix Pack {#install-cumulative-fix-pack}

Suivez les étapes suivantes pour installer le pack de correctifs cumulés sur une instance 6.4.8.0 existante :

1. Cliquez sur le lien Distribution [de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-2.0.zip) logiciels pour télécharger le package.

1. Open [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) and click **[!UICONTROL Upload Package]** to upload the package.

1. Select the package name and click **[!UICONTROL Install]**.

>[!NOTE]
>
>**La boîte de dialogue sur l’interface utilisateur de Package Manager se ferme parfois de manière impromptue lors de l’installation de la version 6.4.8.2**
>
>Il est donc recommandé d’attendre que les journaux d’erreurs se stabilisent avant d’accéder à l’instance. L&#39;utilisateur doit attendre les journaux spécifiques liés à la désinstallation du lot de mise à jour avant de s&#39;assurer que l&#39;installation est réussie. Cela se produit généralement sur Safari, mais peut se produire par intermittence sur n’importe quel navigateur.

### Installation automatique {#auto-installation}

Il existe deux manières d’installer automatiquement AEM 6.4.8.2 dans une instance en cours d’exécution :

A. Placez le package dans le dossier ..*/crx-quickstart/install* pendant que le serveur est en cours d’exécution. Le package est automatiquement installé.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.8.2 ne prend pas en charge l’installation de Bootstrap.

### Validation de l’installation {#validate-install}

1. La page Informations sur le produit (*/system/console/productinfo*) doit maintenant afficher la chaîne de version mise à jour « Adobe Experience Manager, Version 6.4.8.2. » sous Produits installés.
1. Tous les lots OSGI sont ACTIFS ou FRAGMENT dans la console OSGI (utiliser la console web : /system/console/bundles).
1. Le lot OSGI org.apache.jackrabbit.oak-core est sur la version 1.8.17 ou ultérieure (utilisez la console Web : /system/console/bundles).

To determine the certified platform for running with this release of AEM Sites and Assets, see [Technical Requirements](../sites-deploying/technical-requirements.md).

>[!NOTE]
>On successful installation of the package, an informational message appears indicating that the content package has installed successfully, such as **&quot;Content Package AEM-6.4-Service-Pack-8 installed successfully.&quot;**

### Mise à jour des visionneuses de médias dynamiques (5.10.1) {#update-dynamic-media-viewers}

aem 6.4.8.2 contient la nouvelle version des visionneuses de contenu Contenu multimédia dynamique (5.10.1) qui permet de vérifier les noms des duplicata sur la page Paramètres d’image prédéfinis. Il est conseillé aux utilisateurs de Contenu multimédia dynamique d’exécuter la commande suivante afin de mettre à jour les paramètres prédéfinis de la visionneuse prête à l’emploi.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

qui copiera les nouveaux paramètres prédéfinis de la visionneuse à l’emplacement /conf.

### Installation du module complémentaire AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms. Les correctifs dans AEM Forms sont fournis dans un module complémentaire distinct.

1. Assurez-vous d’avoir installé l’AEM Cumulative Fix Pack.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/fr/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installation du programme d’installation d’AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms sous JEE. Les correctifs dans AEM Forms JEE sont fournis dans un programme d’installation distinct.

Pour plus d’informations sur l’installation du programme d’installation cumulatif pour AEM Forms JEE et la configuration post-déploiement, voir [AEM Forms JEE Patch Installer 0019](jee-patch-installer-64.md).

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.2 is available in the [Maven Central repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.2-1.0/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.2-1.0</version>  
      <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>A partir de cette version, UberJar et d’autres artefacts associés sont disponibles dans le référentiel Maven Central et non dans le référentiel Adobe Public Maven (repo.adobe.com). Le fichier UberJar principal est renommé `uber-jar-<version>.jar`. Par conséquent, il n’existe aucune `classifier`valeur, avec `apis` comme valeur, pour la `dependency` balise.

## Fonctionnalités supprimées / obsolètes {#removed-deprecated-features}

Cette section répertorie les fonctionnalités qui ont été supprimées ou désignées comme obsolètes dans AEM 6.4.

| Zone | Fonctionnalité | Remplacement | Version |
|---|---|---|---|
| Ressources | Gérer l’action de balise pour les sous-ensembles | Aucun remplacement. | AEM 6.4.2.0 |
| Intégration des Ressources et d’Adobe Creative Cloud | [aem au partage](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) des dossiers des Creative Cloud a été introduit dans AEM 6.2 pour permettre aux utilisateurs créatifs d’accéder aux ressources à partir d’AEM. Adobe Asset Link, nouvelle fonctionnalité proposée dans l’application Creative Cloud, offre une expérience utilisateur améliorée et un accès plus puissant aux ressources d’AEM directement à partir de Photoshop, InDesign et Illustrator. Adobe n’apportera pas d’améliorations supplémentaires à la fonctionnalité de partage de dossiers. Bien que la fonction soit incluse dans AEM, les clients sont (il est fortement conseillé d’utiliser le remplacement). | Lien de ressources d’Adobe ou application de bureau. Pour plus d’informations, reportez-vous à l’article [Intégration d’AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Problèmes connus {#known-issues}

* Si vous effectuez une mise à niveau de Experience Manager 6.4.8.2 vers Experience Manager 6.5, certains lots risquent de ne pas afficher leur état `Active`en tant que. Installez la dernière version de Experience Manager 6.5 Service Pack 6 pour résoudre le problème.

Pour plus d’informations sur les problèmes connus du Service Pack AEM 6.4.8.0, voir [AEM 6.4.8.0 Notes](sp-release-notes.md)de mise à jour du Service Pack.

## Lots OSGi et packages de contenu inclus {#osgi-bundles-and-content-packages-included}

Les documents de texte suivants liste les lots OSGi et les packages de contenu inclus dans l&#39;AEM 6.4.8.2.

Liste des lots OSGi inclus dans AEM 6.4.8.2

[Obtenir le fichier](assets/6.4.8.2_osgi_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.8.2

[Obtenir le fichier](assets/6.4.8.2_content_packages.txt)

## Ressources utiles {#helpful-resources}

* [Notes de mise à jour d’AEM 6.4](../release-notes/release-notes.md)
* [Page de produits AEM ](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentation d’AEM 6.4](https://helpx.adobe.com/fr/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## Sites restreints {#restricted-sites-new}

Seuls les clients peuvent accéder à ces sites. Si vous devez y accéder en tant que client, contactez votre gestionnaire de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance client](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
