---
title: Fonctions de la communauté
seo-title: Fonctions de la communauté
description: Découvrez comment accéder à la console Fonctions de la communauté
seo-description: Découvrez comment accéder à la console Fonctions de la communauté
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 6%

---


# Fonctions de la communauté {#community-functions}

Le type de caractéristiques attendues d&#39;une expérience communautaire est bien connu. Les fonctions communautaires sont disponibles en tant que fonctions communautaires. Il s’agit essentiellement d’une ou de plusieurs pages pré-programmées pour mettre en oeuvre une fonctionnalité de communauté qui nécessite plus qu’un simple ajout d’un composant à une page en mode création. Il s’agit des éléments de base utilisés pour définir la structure d’un modèle [de site](sites.md) communautaire à partir duquel des sites communautaires sont [créés](sites-console.md).

Une fois un site communautaire créé, le contenu peut être ajouté aux pages résultantes en utilisant le mode [de création](../../help/sites-authoring/editing-content.md)AEM standard.

Un certain nombre de fonctions communautaires sont immédiatement disponibles, comme le montre la console des fonctions communautaires. D&#39;autres fonctions de la communauté seront assurées dans les prochaines versions et des fonctions personnalisées pourront également être créées.

>[!NOTE]
>
>Les consoles pour la création de sites [](sites-console.md)communautaires, de modèles [de sites](sites.md)communautaires, de modèles de groupes de [communautés et de fonctions de](tools-groups.md) [communauté ne sont utilisées que dans l&#39;environnement d&#39;auteur.](functions.md)

## Console des fonctions de la communauté {#community-functions-console}

Dans l&#39;environnement auteur, pour accéder à la console des fonctions communautaires

* A partir de la navigation globale : **[!UICONTROL Outils > Communautés > Fonctions de communauté]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Fonctions préétablies {#pre-built-functions}

Voici une brève description des fonctions fournies avec AEM Communities. Chaque fonction comprend une ou plusieurs pages AEM contenant des composants Communities connectés ensemble à une fonction qui est facilement intégrée dans un modèle [de site](sites.md)communautaire.

Un modèle de site communautaire fournit la structure d’un site communautaire, y compris les fonctions de connexion, les profils utilisateur, les notifications, les messages, le menu du site, la recherche, le thème et l’identité graphique.

### Paramètres de titre et d’URL {#title-and-url-settings}

**Le titre** et l’ **URL** sont des propriétés communes à toutes les fonctions de la communauté.

Lorsqu’une fonction de communauté est ajoutée à un modèle de site de communauté ou ajoutée lors de la [modification](sites-console.md#modifying-site-properties) de la structure d’un site de communauté, la boîte de dialogue de la fonction s’ouvre afin que le titre et l’URL puissent être configurés.

#### Détails de la fonction de configuration {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Titre]**
(
*obligatoire*) Le texte qui apparaît dans le menu des fonctionnalités du site

* **[!UICONTROL URL]**(*obligatoire*) Nom utilisé pour générer l’URI. Le nom doit être conforme aux conventions [de](../../help/sites-developing/naming-conventions.md) dénomination imposées par AEM et JCR.

Par exemple, si vous utilisez le site créé à partir du didacticiel [Prise en main](getting-started.md) , si

* Titre = Page Web
* URL = page

Ensuite, l’URL de la page est http://local_host:4503/content/sites/engage/en/page.html et le lien de menu de la page s’affiche comme suit :

![chlimage_1-381](assets/chlimage_1-381.png)

### Fonction Flux d&#39;activités {#activity-stream-function}

La fonction de flux d’activité est une page avec un composant [Flux d’](activities.md) Activité avec toutes les vues sélectionnées (toutes les activités, les activités utilisateur et les suivantes). Voir aussi [Activité Stream Essentials](essentials-activities.md) pour les développeurs.

Lorsqu’elle est ajoutée à un modèle, la boîte de dialogue suivante s’ouvre :

#### Détails de la fonction de configuration {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Afficher la vue]**&quot;Mes Activités&quot; Si cochée, la page Activités comprend un onglet qui filtres les activités en fonction de celles générées dans la communauté par le membre actuel. Cette option est cochée par défaut.

* **[!UICONTROL Afficher la vue]**&quot;Toutes les Activités&quot; Si cochée, la page Activités comprend un onglet qui comprend toutes les activités générées au sein de la communauté à laquelle le membre actuel a accès. Cette option est cochée par défaut.

* **[!UICONTROL Afficher la vue]**&quot;Flux d’informations&quot; Si cochée, la page Activités comprend un onglet qui filtres les activités en fonction de celles que suit le membre actuel. Cette option est cochée par défaut.

### Fonction Affectations {#assignments-function}

La fonction assignations est la fonction de base qui définit un site [communautaire pour l&#39;activation](overview.md#enablement-community). Il permet d&#39;affecter des ressources d&#39;habilitation aux membres de la communauté. Voir aussi [Affectations Essentials](essentials-assignments.md) pour les développeurs.

Cette fonction est disponible en tant que fonction du module complémentaire [d’](enablement.md)activation. Le module complémentaire d’activation nécessite une licence supplémentaire pour une utilisation dans un environnement de production.

Lorsqu’elle est ajoutée à un modèle, la seule configuration concerne les paramètres [de](#title-and-url-settings)titre et d’URL.

### Fonction Blog {#blog-function}

La fonction de blog est une page dont un composant [de](blog-feature.md) blog est configuré pour le balisage, les téléchargements de fichiers, les éléments suivants, les membres à modifier eux-mêmes, le vote et la modération. Voir aussi [Blog Essentials](blog-developer-basics.md) pour les développeurs.

Lorsqu’elle est ajoutée à un modèle, la boîte de dialogue suivante s’ouvre :

![chlimage_1-383](assets/chlimage_1-383.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Permettre aux membres]** privilégiés Si cette option est cochée, le blog ne permettra aux membres privilégiés que de créer des articles en permettant la sélection d&#39;un groupe [de membres](users.md#privileged-members-group)privilégiés. Si elle n’est pas cochée, tous les membres de la communauté sont autorisés à créer. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les téléchargements]** de fichiers Si cette option est cochée, le blog permet aux membres de télécharger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses]** filetées Si elles ne sont pas cochées, le blog autorise les réponses (commentaires) à un article, mais les réponses aux commentaires ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu]** phare Si cette option est cochée, l&#39;idée peut être identifiée comme contenu [](featured.md)phare. Cette option est cochée par défaut.

### Fonction Calendrier {#calendar-function}

La fonction de calendrier est une page dont le composant [](calendar.md) Calendrier est configuré pour autoriser le balisage. Voir aussi [Calendrier Essentials](calendar-basics-for-developers.md) pour les développeurs.

Lorsqu’elle est ajoutée à un modèle, la boîte de dialogue suivante s’ouvre :

![chlimage_1-384](assets/chlimage_1-384.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Autoriser l’épinglage]** Si cette option est cochée, le forum permet d’épingler les réponses aux sujets jusqu’au début de la liste des commentaires. Cette option est cochée par défaut.

* **[!UICONTROL Permettre aux membres]** privilégiés Si cette option est cochée, le blog ne permettra aux membres privilégiés que de créer des articles en permettant la sélection d&#39;un groupe [de membres](users.md#privileged-members-group)privilégiés. Si elle n’est pas cochée, tous les membres de la communauté sont autorisés à créer. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les téléchargements]** de fichiers Si cette option est cochée, le blog permet aux membres de télécharger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses]** filetées Si elles ne sont pas cochées, le blog autorise les réponses (commentaires) à un article, mais les réponses aux commentaires ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu]** phare Si cette option est cochée, l&#39;idée peut être identifiée comme contenu [](featured.md)phare. Cette option est cochée par défaut.

### Fonction Catalogue {#catalog-function}

La fonction de catalogue permet aux membres de la communauté [d’](overview.md#enablement-community) activation de parcourir les ressources d’activation qui ne leur sont pas affectées. Voir Ressources [d’](tag-resources.md) activation du balisage et [Catalogue essentiel](catalog-developer-essentials.md) pour les développeurs.

Toutes les ressources d’activation et tous les chemins d’apprentissage pour le site de la communauté s’affichent dans tous les catalogues si leur propriété, ` [Show in Catalog](resources.md)`est définie sur true. Pour inclure explicitement des ressources et des chemins d’apprentissage, il est nécessaire d’appliquer un [pré-filtre](catalog-developer-essentials.md#pre-filters) au catalogue.

Lorsqu’elle est ajoutée à un modèle, la configuration permet de spécifier les espaces de nommage de balise utilisés pour configurer le filtre de balise présenté aux visiteurs du site :

![catalogfunc](assets/catalogfunc.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Sélectionner tous les espaces de noms]**

   * Les espaces de nommage de balises sélectionnés définissent les balises sélectionnables par les visiteurs pour le filtrage de la liste des ressources d’activation répertoriées dans le catalogue.
   * Si cette case est cochée, tous les espaces de nommage de balises autorisés pour le site de la communauté sont disponibles.
   * Si cette option n’est pas cochée, il est possible de sélectionner un ou plusieurs espaces de nommage autorisés pour le site communautaire.
   * Cette option est cochée par défaut.

### Fonction de contenu proposé {#featured-content-function}

La fonction de contenu incitatif est une page dont un composant [Contenu proposé](featured.md) est configuré pour permettre l&#39;ajout et la suppression de commentaires.

La fonctionnalité de contenu peut être autorisée ou refusée par composant (voir Fonction [](#blog-function)de blog, Fonction [](#calendar-function)Calendrier, Fonction [](#forum-function)Forum, Fonction [Idéation et Fonction QnA).](#ideation-function)[](#qna-function)

Lorsqu’elle est ajoutée à un modèle, la seule configuration concerne les paramètres [de](#title-and-url-settings)titre et d’URL.

### Fonction Bibliothèque de fichiers {#file-library-function}

La fonction de bibliothèque de fichiers est une page dont le composant [Bibliothèque de](file-library.md) fichiers est configuré pour permettre l’ajout et la suppression de commentaires.

Lorsqu’elle est ajoutée à un modèle, la seule configuration concerne les paramètres [de](#title-and-url-settings)titre et d’URL.

### Fonction Forum {#forum-function}

La fonction de forum est une page avec un composant [](forum.md) Forum configuré pour le balisage, les téléchargements de fichiers, les suivants, les membres à modifier eux-mêmes, le vote et la modération.

Lorsqu’elle est ajoutée à un modèle, la boîte de dialogue suivante s’ouvre :

#### Détails de la fonction de configuration {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Autoriser l’épinglage]** Si cette option est cochée, le forum permet d’épingler les réponses aux sujets jusqu’au début de la liste des commentaires. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les membres]** privilégiés Si cette case est cochée, le forum ne permettra aux membres privilégiés que de publier des sujets en permettant la sélection d&#39;un groupe [de membres](users.md#privileged-members-group)privilégiés. Si elle n’est pas cochée, tous les membres de la communauté sont autorisés à publier. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les téléchargements]** de fichiers Si cette option est cochée, le forum permet aux membres de télécharger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses]** filetées Si elles ne sont pas cochées, le forum autorise les commentaires sur un sujet, mais les réponses à ces commentaires ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu]** phare Si cette option est cochée, l&#39;idée peut être identifiée comme contenu [](featured.md)phare. Cette option est cochée par défaut.

### Fonction Groupes {#groups-function}

>[!CAUTION]
>
>La fonction de groupes *ne doit pas* être la *première ou la seule* fonction dans la structure d&#39;un site ou dans un modèle de site communautaire.
>
>Toute autre fonction, telle que la fonction [de](#page-function)page, doit être incluse et répertoriée en premier.

La fonction de groupes permet aux membres de la communauté de créer des sous-communautés au sein du site communautaire dans l’environnement de publication.

En fonction des [paramètres](sites-console.md#groupmanagement) lorsque la fonction Groupes est incluse dans un modèle [de site](sites.md)communautaire, les groupes peuvent être publics ou privés et un ou plusieurs modèles de groupes communautaires peuvent être configurés pour fournir un choix de modèles lorsque le groupe de communauté est effectivement créé (à partir de l’environnement de publication, par exemple). Un modèle [de groupe de](tools-groups.md) communautés spécifie les fonctions de communautés qui sont créées pour les pages de groupe, telles que les forums et les calendriers.

Lorsqu’un groupe de communauté est créé, un groupe de membres est créé dynamiquement pour le nouveau groupe, auquel les membres peuvent être affectés ou rejoints. For more information, see [Managing Users and User Groups](users.md).

A compter de la version 1 [de](deploy-communities.md#latestfeaturepack)Feature Pack des communautés, les groupes communautaires sont créés dans l’environnement d’auteur à l’aide de la console [Groupes de sites des](groups.md)communautés et peuvent être créés dans l’environnement de publication lorsqu’ils sont activés.

Lorsqu’elle est ajoutée à un modèle, la boîte de dialogue suivante s’ouvre :

![chlimage_1-386](assets/chlimage_1-386.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Sélectionnez Modèles]** de groupe Un menu déroulant qui permet de sélectionner un ou plusieurs modèles de groupe activés à partir desquels le futur créateur d’un nouveau groupe de communauté (dans l’environnement de publication) peut choisir.

* **[!UICONTROL Autoriser les membres]** privilégiés Si cette case est cochée, le forum ne permettra aux membres privilégiés que de publier des sujets en permettant la sélection d&#39;un groupe [de sécurité de membres](users.md#privileged-members-group)privilégiés. Si elle n’est pas cochée, tous les membres de la communauté sont autorisés à publier. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser la création]** de publication Si cette option est cochée, les membres autorisés de la communauté peuvent créer un groupe dans l’environnement de publication. Si cette option n&#39;est pas cochée, de nouveaux groupes (sous-communautés) ne peuvent être créés que dans l&#39;environnement d&#39;auteur à partir de la console Groupes de sites des communautés.

   La valeur par défaut est `checked`.

### Fonction de conceptualisation {#ideation-function}

La fonction d’idéation est une page avec un composant [](ideation-feature.md)d’idéation.

Lorsqu’elle est ajoutée à un modèle, la boîte de dialogue suivante s’ouvre, qui spécifie les noms de titre et d’URL par défaut, ainsi que les paramètres d’affichage par défaut du modèle :

![chlimage_1-387](assets/chlimage_1-387.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Autoriser les membres]** privilégiés Si cette case est cochée, le forum ne permettra aux membres privilégiés que de publier des sujets en permettant la sélection d&#39;un groupe [de sécurité de membres](users.md#privileged-members-group)privilégiés. Si elle n’est pas cochée, tous les membres de la communauté sont autorisés à publier. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les téléchargements]** de fichiers Si cette option est cochée, l’idée inclura la possibilité pour les membres de télécharger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses]** filetées Si elle n’est pas cochée, l’idée autorise les réponses (commentaires) à un sujet, mais les réponses aux commentaires ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu]** phare Si cette option est cochée, l&#39;idée peut être identifiée comme contenu [](featured.md)phare. Cette option est cochée par défaut.

### Fonction de classement {#leaderboard-function}

La fonction de classement est une page avec un composant [de](enabling-leaderboard.md)classement.

**REMARQUE**: le composant Leaderboard aura besoin d&#39;une configuration plus poussée *après* la création d&#39;un site communautaire à partir d&#39;un modèle communautaire qui inclut la fonction Leaderboard. Les [règles](enabling-leaderboard.md#rules-tab) du composant Leaderboard devront être spécifiées, qui dépendent de la configuration de la [notation et des badges](implementing-scoring.md) pour le site communautaire.

Lorsqu’elle est ajoutée à un modèle, la boîte de dialogue suivante s’ouvre, qui spécifie les noms de titre et d’URL par défaut, ainsi que les paramètres d’affichage par défaut du modèle :

![chlimage_1-388](assets/chlimage_1-388.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Afficher un badge]** Si cette case est cochée, une colonne pour les icônes de badge est incluse dans le tableau de bord.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher le nom]** du badge Si cette case est cochée, une colonne correspondant au nom du badge est incluse dans le tableau de bord.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher l&#39;avatar]** Si cette option est cochée, l&#39;avatar du membre est inclus dans le tableau de bord, en regard du lien de son nom vers son profil membre.

   Cette option n’est pas cochée par défaut.

### Fonction Page {#page-function}

La fonction de page ajoute une page vierge au site communautaire qu’elle est intégrée aux fonctionnalités du site communautaire : connexion, menu, notifications, messagerie, thème et marque. Le contenu peut être ajouté à la page à l’aide du mode [de création AEM](../../help/sites-authoring/editing-content.md)standard.

Lorsqu’elle est ajoutée à un modèle, la seule configuration concerne les paramètres [de](#title-and-url-settings)titre et d’URL.

### Fonction Q&amp;R {#qna-function}

La fonction QnA est une page dont le composant [](working-with-qna.md) QnA est configuré pour le balisage, les téléchargements de fichiers, les suivants, les membres à modifier eux-mêmes, le vote et la modération.

Lorsqu’elle est ajoutée à un modèle, la configuration autorise la restriction aux membres privilégiés :

![chlimage_1-389](assets/chlimage_1-389.png)

* Voir Paramètres [de titre et d’URL.](#title-and-url-settings)
* **[!UICONTROL Autoriser l’épinglage]** Si cette option est cochée, le forum permet d’épingler les réponses aux sujets jusqu’au début de la liste des commentaires. Cette option est cochée par défaut.

* **[!UICONTROL Permettre aux membres]** privilégiés Si cette option est cochée, le forum QnA ne permettra aux membres privilégiés que de poser des questions en permettant la sélection d&#39;un groupe [de membres](users.md#privileged-members-group)privilégiés. Si elle n’est pas cochée, tous les membres de la communauté sont autorisés à publier. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les téléchargements]** de fichiers Si cette option est cochée, le forum QnA permet aux membres de télécharger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses]** filetées Si elles ne sont pas cochées, le forum QnA permet de faire des commentaires (réponses) à une question publiée, mais les réponses aux réponses ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu]** phare Si cette option est cochée, l&#39;idée peut être identifiée comme contenu [](featured.md)phare. Cette option est cochée par défaut.

## Créer une fonction de communauté {#create-community-function}

Pour créer une fonction de communauté, sélectionnez l’ `Create Community Function` icône située en haut de la console Fonctions de la communauté. Il est possible de créer plusieurs fonctions basées sur le même modèle AEM, puis de les personnaliser de manière unique en s’ouvrant en mode d’édition Auteur.

![chlimage_1-390](assets/chlimage_1-390.png)

### Nom de fonction de la communauté {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

Dans le panneau Nom de la fonction communautaire, un nom, une description et si la fonction est activée ou désactivée sont configurés :

* **[!UICONTROL Nom]** de fonction de la communauté Nom de fonction utilisé pour l’affichage et l’enregistrement

* **[!UICONTROL Description]** de la fonction communautaire Description de la fonction pour l&#39;affichage

* **[!UICONTROL Désactivé/Activé]** Un commutateur à bascule contrôlant si la fonction est référente

### Plan directeur AEM {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

Sur le `AEM Blueprint` panel, il est possible de sélectionner le plan directeur qui est la mise en oeuvre sous-jacente de la fonction communautaire.

La fonction communautaire est un mini site composé d&#39;une ou de plusieurs pages, pré-programmé pour l&#39;inclusion dans un site communautaire, y compris les informations de connexion, les profils d&#39;utilisateur, les notifications, les messages, le menu du site, la recherche, le thème et les fonctionnalités de marque. Une fois la fonction créée, il est possible d’ [ouvrir la fonction](#open-community-function) en mode d’édition Auteur et de personnaliser les paramètres de page et/ou de composant.

Comme la fonction communautaire est mise en oeuvre en tant que copie [](../../help/sites-administering/msm.md#live-copies) en direct d&#39;un [plan directeur](../../help/sites-administering/msm-livecopy.md#creatingablueprint), il est possible de mettre en oeuvre les modifications apportées à une fonction qui affecte toutes les pages du site de la communauté créées à partir du modèle [de site de la](sites.md) communauté ou du modèle de groupe de [la communauté qui incluait la fonction. ](tools-groups.md) Il est également possible de dissocier une page de son plan parent afin d’effectuer des modifications au niveau de la page.

Voir aussi Gestionnaire [](../../help/sites-administering/msm.md)multisite.

### Miniature  {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

Dans le panneau Miniature, une image peut être chargée pour s’afficher dans la console [Fonctions de la](#community-functions-console)communauté.

## Ouvrir la fonction de communauté {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Sélectionnez l’ `Open Community Function` icône permettant de passer en mode d’édition de l’auteur pour la création du contenu de la page et la modification de la configuration des composants de fonction.

### Configuration des composants {#configuring-components}

Une fonction communautaire est mise en oeuvre sous forme de Live Copy d&#39;un plan directeur AEM, dont les détails sont documentés dans le Gestionnaire [](../../help/sites-administering/msm.md)multisite.

Il est possible non seulement de créer du contenu de page, mais aussi de configurer des composants.

Si vous configurez un composant sur une page d’un site communautaire créé, il peut s’avérer nécessaire d’annuler l’ [héritage](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) pour configurer le composant. L&#39;héritage doit être rétabli une fois la configuration terminée.

Pour plus d’informations sur la configuration, consultez Composants [](author-communities.md) Communautés pour les auteurs.

## Modifier la fonction de communauté {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Sélectionnez l&#39; `Edit Community Function` icône pour modifier les propriétés de la fonction à l&#39;aide des mêmes panneaux que ceux qui [créent une fonction](#create-community-function)communautaire, y compris l&#39;activation ou la désactivation de la fonction.
