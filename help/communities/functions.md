---
title: Fonctions de la communauté
seo-title: Community Functions
description: Découvrez comment accéder à la console Fonctions de la communauté
seo-description: Learn how to access the Community Functions console
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Admin
exl-id: 2007336d-d75c-4e01-af81-181751c04cfe
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '2532'
ht-degree: 6%

---

# Fonctions de la communauté {#community-functions}

Le type de fonctionnalités attendu d’une expérience communautaire est bien connu. Les fonctions de communauté sont disponibles sous la forme de fonctions de communauté. Il s’agit essentiellement d’une ou de plusieurs pages préconfigurées pour mettre en oeuvre une fonctionnalité de communauté qui nécessite plus qu’un simple ajout d’un composant à une page en mode création. Il s’agit des blocs de construction utilisés pour définir la structure d’une [modèle de site communautaire](sites.md) à partir de quels sites communautaires [created](sites-console.md).

Une fois qu’un site communautaire est créé, le contenu peut être ajouté aux pages résultantes à l’aide de la norme [AEM mode création](../../help/sites-authoring/editing-content.md).

Un certain nombre de fonctions de communauté sont immédiatement disponibles, comme dans la console de fonctions de communauté. D’autres fonctions de communauté seront fournies dans les prochaines versions et des fonctions personnalisées pourront également être créées.

>[!NOTE]
>
>Les consoles pour la création de [sites communautaires](sites-console.md), [modèles de site de communauté](sites.md), [modèles de groupe de communautés](tools-groups.md) et [fonctions de communauté](functions.md) sont utilisables uniquement dans l’environnement de création.

## Console des fonctions de communauté {#community-functions-console}

Dans l’environnement de création, pour accéder à la console des fonctions de la communauté

* À partir de la navigation globale : **[!UICONTROL Outils > Communautés > Fonctions de communauté]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Fonctions préconfigurées {#pre-built-functions}

Vous trouverez ci-dessous une brève description des fonctions fournies avec AEM Communities. Chaque fonction est composée d’une ou de plusieurs pages AEM contenant des composants Communities connectés ensemble dans une fonction qui est facilement intégrée à un [modèle de site communautaire](sites.md).

Un modèle de site de communauté fournit la structure d’un site de communauté, y compris les fonctions de connexion, les profils utilisateur, les notifications, la messagerie, le menu du site, la recherche, le thème et la marque.

### Paramètres de titre et d’URL {#title-and-url-settings}

**Titre** et **URL** sont des propriétés communes à toutes les fonctions de la communauté.

Lorsqu’une fonction de communauté est ajoutée à un modèle de site de communauté ou ajoutée lors d’une [modification](sites-console.md#modifying-site-properties) structure d’un site de communauté, la boîte de dialogue de la fonction s’ouvre afin que le titre et l’URL puissent être configurés.

#### Détails de la fonction de configuration {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Titre]**
(
*required*) Texte qui apparaît dans le menu des fonctionnalités du site.

* **[!UICONTROL URL]**
(*required*) Nom utilisé pour générer l’URI. Le nom doit être conforme à la variable [conventions de dénomination](../../help/sites-developing/naming-conventions.md) imposé par AEM et JCR.

Par exemple, en utilisant le site créé à partir de la fonction [Prise en main](getting-started.md) tutoriel, si

* Titre = Page web
* URL = page

Ensuite, l’URL de la page est http://local_host:4503/content/sites/engage/en/page.html et le lien de menu de la page s’affiche comme suit :

![chlimage_1-381](assets/chlimage_1-381.png)

### Fonction Flux d&#39;activités {#activity-stream-function}

La fonction de flux d’activités est une page avec une [Composant Flux d’activités](activities.md) avec toutes les vues sélectionnées (toutes les activités, activités utilisateur et suivantes). Voir aussi [Notions fondamentales sur les flux d’activités](essentials-activities.md) pour les développeurs.

La boîte de dialogue suivante s’ouvre lorsqu’elle est ajoutée à un modèle :

#### Détails de la fonction de configuration {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Afficher la vue &quot;Mes activités&quot;]**
Si cette case est cochée, la page Activités comprend un onglet qui filtre les activités en fonction de celles générées dans la communauté par le membre actuel. Cette option est cochée par défaut.

* **[!UICONTROL Afficher la vue &quot;Toutes les activités&quot;]**
Si cette case est cochée, la page Activités comprend un onglet qui inclut toutes les activités générées au sein de la communauté auxquelles le membre actuel a accès. Cette option est cochée par défaut.

* **[!UICONTROL Afficher la vue &quot;Flux de nouvelles&quot;]**
Si cette case est cochée, la page Activités comprend un onglet qui filtre les activités en fonction de celles que le membre actuel suit. Cette option est cochée par défaut.

### Fonction Affectations {#assignments-function}

La fonction Affectations est la fonction de base qui définit une [site communautaire pour l’activation](overview.md#enablement-community). Il permet d’affecter des ressources d’activation aux membres de la communauté. Voir aussi [Notions fondamentales sur les affectations](essentials-assignments.md) pour les développeurs.

Cette fonction est disponible en tant que fonctionnalité de la fonction [module complémentaire d’activation](enablement.md). Le module complémentaire d’activation nécessite des licences supplémentaires pour être utilisé dans un environnement de production.

Lors de l’ajout à un modèle, la seule configuration est celle de la variable [Paramètres de titre et d’URL](#title-and-url-settings).

### Fonction Blog {#blog-function}

La fonction de blog est une page avec une [Composant Blog](blog-feature.md) configuré pour le balisage, les chargements de fichiers, les suivants, les membres à modifier, le vote et la modération. Voir aussi [Notions fondamentales sur les blogs](blog-developer-basics.md) pour les développeurs.

La boîte de dialogue suivante s’ouvre lorsqu’elle est ajoutée à un modèle :

![chlimage_1-383](assets/chlimage_1-383.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Autoriser les membres privilégiés]**
Si cette case est cochée, le blog ne permettra aux membres privilégiés que de créer des articles en autorisant la sélection d’un [groupe de membres privilégiés](users.md#privileged-members-group). Si cette option n’est pas cochée, tous les membres de la communauté sont autorisés à créer. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]**
Si cette case est cochée, le blog permet aux membres de charger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses à threads]**
Si cette option n’est pas cochée, le blog autorise les réponses (commentaires) à un article, mais les réponses aux commentaires ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu proposé]**
Si cette case est cochée, l’idée peut être identifiée comme [contenu proposé](featured.md). Cette option est cochée par défaut.

### Fonction Calendrier {#calendar-function}

La fonction Calendrier est une page avec une [Composant Calendrier](calendar.md) configuré pour autoriser le balisage. Voir aussi [Principes de base du calendrier](calendar-basics-for-developers.md) pour les développeurs.

La boîte de dialogue suivante s’ouvre lorsqu’elle est ajoutée à un modèle :

![chlimage_1-384](assets/chlimage_1-384.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Permettre la mise en page]**
Si cette option est cochée, le forum permet d’épingler les réponses aux sujets au début de la liste des commentaires. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les membres privilégiés]**
Si cette case est cochée, le blog ne permettra aux membres privilégiés que de créer des articles en autorisant la sélection d’un [groupe de membres privilégiés](users.md#privileged-members-group). Si cette option n’est pas cochée, tous les membres de la communauté sont autorisés à créer. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]**
Si cette case est cochée, le blog permet aux membres de charger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses à threads]**
Si cette option n’est pas cochée, le blog autorise les réponses (commentaires) à un article, mais les réponses aux commentaires ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu proposé]**
Si cette case est cochée, l’idée peut être identifiée comme [contenu proposé](featured.md). Cette option est cochée par défaut.

### Fonction Catalogue {#catalog-function}

La fonction catalog permet d’utiliser la fonction [communauté d&#39;activation](overview.md#enablement-community) membres pour parcourir les ressources d’activation qui ne leur sont pas affectées. Voir [Balisage des ressources d’activation](tag-resources.md) et [Notions fondamentales sur le catalogue](catalog-developer-essentials.md) pour les développeurs.

Toutes les ressources d’activation et tous les parcours de formation du site de la communauté s’affichent dans tous les catalogues si leur propriété, ` [Show in Catalog](resources.md)`, est défini sur true. Pour inclure explicitement des ressources et des parcours d’apprentissage, il est nécessaire d’appliquer une [pre-filter](catalog-developer-essentials.md#pre-filters) au catalogue.

Lorsqu’elle est ajoutée à un modèle, la configuration permet de spécifier le ou les espaces de noms de balise utilisés pour configurer le filtre de balise présenté aux visiteurs du site :

![catalogfunc](assets/catalogfunc.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Sélectionner tous les espaces de noms]**

   * Les espaces de noms de balise sélectionnés définissent les balises pouvant être sélectionnées par les visiteurs pour le filtrage de la liste des ressources d’activation répertoriées dans le catalogue.
   * Si cette case est cochée, tous les espaces de noms de balise autorisés pour le site de la communauté sont disponibles.
   * Si cette option n’est pas cochée, il est possible de sélectionner un ou plusieurs espaces de noms autorisés pour le site de la communauté.
   * Cette option est cochée par défaut.

### Fonction de contenu en vedette {#featured-content-function}

La fonction de contenu présenté est une page avec une [Composant Contenu proposé](featured.md) configuré pour autoriser l’ajout et la suppression de commentaires.

La possibilité d’afficher du contenu peut être autorisée ou non par composant (voir [Fonction de blog](#blog-function), [Fonction Calendrier](#calendar-function), [Fonction Forum](#forum-function), [Idéation, fonction](#ideation-function), et [Fonction Q&amp;R](#qna-function)).

Lors de l’ajout à un modèle, la seule configuration est celle de la variable [Paramètres de titre et d’URL](#title-and-url-settings).

### Fonction Bibliothèque de fichiers {#file-library-function}

La fonction de bibliothèque de fichiers est une page avec une [Composant Bibliothèque de fichiers](file-library.md) configuré pour autoriser l’ajout et la suppression de commentaires.

Lors de l’ajout à un modèle, la seule configuration est celle de la variable [Paramètres de titre et d’URL](#title-and-url-settings).

### Fonction Forum {#forum-function}

La fonction de forum est une page avec une [Composant Forum](forum.md) configuré pour le balisage, les chargements de fichiers, les suivants, les membres à modifier, le vote et la modération.

La boîte de dialogue suivante s’ouvre lorsqu’elle est ajoutée à un modèle :

#### Détails de la fonction de configuration {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Permettre la mise en page]**
Si cette option est cochée, le forum permet d’épingler les réponses aux sujets au début de la liste des commentaires. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les membres privilégiés]**
Si cette option est cochée, le forum autorise uniquement les membres privilégiés à publier des sujets en autorisant la sélection d’une [groupe de membres privilégiés](users.md#privileged-members-group). Si cette option n’est pas cochée, tous les membres de la communauté sont autorisés à publier du contenu. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]**
Si cette option est cochée, le forum offre aux membres la possibilité de télécharger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses à threads]**
Si elle n’est pas cochée, le forum autorise les commentaires sur un sujet, mais les réponses à ces commentaires ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu proposé]**
Si cette case est cochée, l’idée peut être identifiée comme [contenu proposé](featured.md). Cette option est cochée par défaut.

### Fonction Groupes {#groups-function}

>[!CAUTION]
>
>La fonction groups doit *not* be *first ni unique* dans la structure d’un site ou dans un modèle de site communautaire.
>
>Toute autre fonction, telle que [fonction de page](#page-function), doit être inclus et répertorié en premier.

La fonction de groupes permet aux membres de la communauté de créer des sous-communautés au sein du site de la communauté dans l’environnement de publication.

Selon [paramètres](sites-console.md#groupmanagement) lorsque la fonction Groupes est incluse dans une [modèle de site communautaire](sites.md), les groupes peuvent être publics ou privés et un ou plusieurs modèles de groupes de communautés peuvent être configurés pour offrir un choix de modèles lorsque le groupe de communautés est réellement créé (à partir de l’environnement de publication, par exemple). A [modèle de groupe de communautés](tools-groups.md) permet d’indiquer les fonctionnalités de communauté qui sont créées pour les pages de groupe, telles que les forums et les calendriers.

Lorsqu’un groupe de communautés est créé, un groupe de membres est créé dynamiquement pour le nouveau groupe, auquel les membres peuvent être affectés ou rejoindre. Pour plus d’informations, voir [Gestion des utilisateurs et des groupes d’utilisateurs](users.md).

À partir des communautés [feature pack 1](deploy-communities.md#latestfeaturepack), les groupes de communautés sont créés dans l’environnement de création à l’aide de la variable [Console Groupes de sites Communities](groups.md)et peuvent être créés dans l’environnement de publication lorsqu’ils sont activés.

La boîte de dialogue suivante s’ouvre lorsqu’elle est ajoutée à un modèle :

![chlimage_1-386](assets/chlimage_1-386.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Sélectionner des modèles de groupe]**
Un menu déroulant qui permet de sélectionner un ou plusieurs modèles de groupe activés à partir desquels le futur créateur d’un nouveau groupe de communauté (dans l’environnement de publication) peut choisir.

* **[!UICONTROL Autoriser les membres privilégiés]**
Si cette option est cochée, le forum autorise uniquement les membres privilégiés à publier des sujets en autorisant la sélection d’une [groupe de sécurité des membres privilégiés](users.md#privileged-members-group). Si cette option n’est pas cochée, tous les membres de la communauté sont autorisés à publier du contenu. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser la création de publication]**
Si cette case est cochée, les membres autorisés de la communauté peuvent créer un groupe dans l’environnement de publication. Si cette option n’est pas cochée, les nouveaux groupes (sous-communautés) ne peuvent être créés que dans l’environnement de création à partir de la console Groupes de sites des communautés .

   La valeur par défaut est `checked`.

### Fonction de conceptualisation {#ideation-function}

La fonction d’idéation est une page avec une [Composant Ideation](ideation-feature.md).

Une fois ajouté à un modèle, la boîte de dialogue suivante s’ouvre, qui spécifie le titre et les noms d’URL par défaut, ainsi que les paramètres d’affichage par défaut du modèle :

![chlimage_1-387](assets/chlimage_1-387.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Autoriser les membres privilégiés]**
Si cette option est cochée, le forum autorise uniquement les membres privilégiés à publier des sujets en autorisant la sélection d’une [groupe de sécurité des membres privilégiés](users.md#privileged-members-group). Si cette option n’est pas cochée, tous les membres de la communauté sont autorisés à publier du contenu. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]**
Si cette option est cochée, l’idée inclut la possibilité pour les membres de charger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses à threads]**
Si elle n’est pas cochée, l’idée autorise les réponses (commentaires) à un sujet, mais les réponses aux commentaires ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu proposé]**
Si cette case est cochée, l’idée peut être identifiée comme [contenu proposé](featured.md). Cette option est cochée par défaut.

### Fonction de classement {#leaderboard-function}

La fonction de classement est une page comportant une seule [Composant de classement](enabling-leaderboard.md).

**REMARQUE**: Le composant Tableau de classement devra être configuré plus en détail. *after* un site communautaire est créé à partir d’un modèle communautaire qui inclut la fonction Leaderboard . Le composant Tableau de classement [rules](enabling-leaderboard.md#rules-tab) doit être spécifié, ce qui dépend de la configuration de [notation et badges](implementing-scoring.md) pour le site de la communauté.

Une fois ajouté à un modèle, la boîte de dialogue suivante s’ouvre, qui spécifie le titre et les noms d’URL par défaut, ainsi que les paramètres d’affichage par défaut du modèle :

![chlimage_1-388](assets/chlimage_1-388.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Afficher le badge]**
Si cette case est cochée, une colonne pour les icônes de badge est incluse dans le tableau de classement.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Nom du badge d’affichage]**
Si cette case est cochée, une colonne correspondant au nom du badge est incluse dans le tableau de classement.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Avatar d’affichage]**
Si cette case est cochée, l’avatar du membre est inclus dans le tableau de classement, en regard du lien de son nom vers son profil de membre.

   Cette option n’est pas cochée par défaut.

### Fonction Page {#page-function}

La fonction de page ajoute une page vierge au site de la communauté qu’elle est connectée aux fonctionnalités du site de la communauté : connexion, menu, notifications, messages, thèmes et marques. Le contenu peut être ajouté à la page à l’aide de la fonction [mode de création AEM standard](../../help/sites-authoring/editing-content.md).

Lors de l’ajout à un modèle, la seule configuration est celle de la variable [Paramètres de titre et d’URL](#title-and-url-settings).

### Fonction Q&amp;R {#qna-function}

La fonction Q&amp;R est une page avec une [Composant Q&amp;R](working-with-qna.md) configuré pour le balisage, les chargements de fichiers, les suivants, les membres à modifier, le vote et la modération.

Lorsqu’elle est ajoutée à un modèle, la configuration autorise la restriction aux membres privilégiés :

![chlimage_1-389](assets/chlimage_1-389.png)

* Voir [Paramètres de titre et d’URL](#title-and-url-settings)
* **[!UICONTROL Permettre la mise en page]**
Si cette option est cochée, le forum permet d’épingler les réponses aux sujets au début de la liste des commentaires. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les membres privilégiés]**
Si cette option est cochée, le forum Q&amp;R permet uniquement aux membres privilégiés de poser des questions en autorisant la sélection d’une [groupe de membres privilégiés](users.md#privileged-members-group). Si cette option n’est pas cochée, tous les membres de la communauté sont autorisés à publier du contenu. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]**
Si cette case est cochée, le forum Q&amp;R permet aux membres de charger des fichiers. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les réponses à threads]**
Si cette option n’est pas cochée, le forum Q&amp;R permet d’ajouter des commentaires (réponses) à une question publiée, mais les réponses aux réponses ne sont pas autorisées. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le contenu proposé]**
Si cette case est cochée, l’idée peut être identifiée comme [contenu proposé](featured.md). Cette option est cochée par défaut.

## Créer une fonction de communauté {#create-community-function}

Pour créer une fonction de communauté, sélectionnez la fonction `Create Community Function` dans la partie supérieure de la console Fonctions de communauté. Plusieurs fonctions basées sur le même plan directeur d’AEM peuvent être créées, puis personnalisées de manière unique en s’ouvrant en mode d’édition de création.

![chlimage_1-390](assets/chlimage_1-390.png)

### Nom de fonction de la communauté {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

Dans le panneau Nom de la fonction de la communauté , un nom, une description et si la fonction est activée ou désactivée sont configurés :

* **[!UICONTROL Nom de la fonction communautaire]**
Nom de fonction utilisé pour l’affichage et le stockage

* **[!UICONTROL Description de la fonction communautaire]**
Description de la fonction pour l’affichage

* **[!UICONTROL Désactivé/activé]**
Commutateur à bascule contrôlant si la fonction est référencable

### Plan directeur AEM {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

Sur le `AEM Blueprint` , il est possible de sélectionner le plan directeur qui est la mise en oeuvre sous-jacente de la fonction de communauté.

La fonction de communauté est un mini-site constitué d’une ou de plusieurs pages, pré-câblées pour inclusion dans un site de communauté, y compris les fonctions de connexion, les profils utilisateur, les notifications, la messagerie, le menu du site, la recherche, le thème et la marque. Une fois la fonction créée, il est possible de [ouvrir la fonction](#open-community-function) en mode d’édition de création et personnalisez la page et/ou les paramètres du composant.

Puisque la fonction de communauté est implémentée sous la forme d’une [Live Copy](../../help/sites-administering/msm.md#live-copies) de [plan directeur](../../help/sites-administering/msm-livecopy.md#creatingablueprint), il est possible de déployer les modifications apportées à une fonction qui affectent toutes les pages de site de communauté créées à partir de la fonction [modèle de site communautaire](sites.md) ou [modèle de groupe de communautés](tools-groups.md) qui incluait la fonction . Il est également possible de dissocier une page de son plan directeur parent afin d’effectuer des modifications au niveau de la page.

Voir aussi [Multi Site Manager](../../help/sites-administering/msm.md).

### Miniature {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

Dans le panneau Miniatures, une image peut être téléchargée pour s’afficher dans le [Console Fonctions de communauté](#community-functions-console).

## Ouvrir la fonction de communauté {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Sélectionnez la `Open Community Function` pour passer en mode d’édition de création pour créer le contenu de la page et modifier la configuration du ou des composants de fonction.

### Configuration des composants {#configuring-components}

Une fonction de communauté est implémentée en tant que Live Copy d’un plan directeur d’AEM, dont les détails sont documentés sous [Multi Site Manager](../../help/sites-administering/msm.md).

Il est possible non seulement de créer du contenu de page, mais aussi de configurer des composants.

Si vous configurez un composant sur une page d’un site de communauté créé, il peut être nécessaire d’annuler [héritage](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) pour configurer le composant. L’héritage doit être rétabli une fois la configuration terminée.

Pour plus d’informations sur la configuration, voir [Composants Communities](author-communities.md) pour les auteurs.

## Modifier la fonction de communauté {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Sélectionnez la `Edit Community Function` pour modifier les propriétés de la fonction à l’aide des mêmes panneaux que [création d’une fonction communautaire](#create-community-function), notamment l’activation ou la désactivation de la fonction .
