---
title: Fonction Blog
seo-title: Fonction Blog
description: Informations de la communauté dans un format de journalisation
seo-description: Informations de la communauté dans un format de journalisation
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
exl-id: 12ae8b4c-73c5-4ec9-beea-b682b55ebdfd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 46%

---

# Fonction Blog {#blog-feature}

## Présentation {#introduction}

La fonction Blog pour AEM Communities a été transformée. D’une activité de création, elle est passée à une véritable activité communautaire au sein même de l’environnement de publication.

Elle présente des informations issues des membres de la communauté dans un format similaire à un journal. Les entrées de blog sont créées dans l’environnement de publication par les membres autorisés (utilisateurs inscrits et connectés).

La fonction Blog comporte les éléments suivants :

* Création du côté publication des articles et des commentaires de blog
* Modification de texte enrichi
* Images intégrées (avec glisser-déposer)
* Contenu de réseaux sociaux intégré ([prise en charge du format oEmbed](blog-developer-basics.md#allowing-rich-media))
* Mode Brouillon
* Publication planifiée
* Fonction Composer au nom d’un utilisateur (un [membre privilégié](users.md#privileged-members-group) peut créer du contenu pour le compte d’un autre membre de la communauté)
* [Modération contextuelle et globale](moderate-ugc.md) des articles et des commentaires de blog

Cette section de la documentation décrit :

* Ajout de la fonction de blog à un site AEM
* Paramètres de configuration des composants de blog

>[!NOTE]
>
>Les composants `Journal`et `Journal Sidebar` sont intitulés `Blog` et `Blog Sidebar`.
>
>La fonction Blog disponible dans AEM 6.0 et versions antérieures a été supprimée. Elle était basée sur un modèle et autorisait uniquement les auteurs à créer du contenu dans l’environnement de création.

## Ajout de composants de blog à une page {#adding-blog-components-to-a-page}

Si vous souhaitez ajouter un blog à une page en mode création, utilisez l’explorateur de composants pour accéder à :

* `Communities / Blog`
* `Communities / Blog Sidebar`

Faites-les glisser sur une page où le blog doit apparaître.

Pour plus d’informations, voir [Principes de base des composants des communautés](basics.md).

Lorsque les [bibliothèques côté client requises](blog-developer-basics.md#essentials-for-client-side) sont incluses, voici comment le composant `Blog`apparaîtra :

![chlimage_1-147](assets/chlimage_1-147.png)

Et comment le `Blog Sidebar` apparaîtra :

![chlimage_1-148](assets/chlimage_1-148.png)

### Configuration du blog {#configuring-blog}

Sélectionnez le composant `Blog` inséré pour y accéder et sélectionnez l’icône `Configure` qui ouvre la boîte de dialogue de modification.

![configuration des paramètres ](assets/chlimage_1-149.png) ![iconBlog](assets/Blog-configure.png)

#### Onglet Settings {#settings-tab}

Sous l’onglet **[!UICONTROL Paramètres]**, définissez les fonctionnalités de base du blog :

* **[!UICONTROL Autoriser la]**
miniature des pièces jointes Si cette option est cochée, une miniature de l’image jointe est créée.

* **[!UICONTROL Taille max. de la miniature de la pièce jointe]**
: taille maximale (en pixels) de la miniature de la pièce jointe. La valeur par défaut est 800 x 800.

* **[!UICONTROL Taille d’image min. pour la]**
miniature Taille minimale (en octets) de l’image pour générer une miniature pour les images intégrées. La valeur par défaut est 100000bytes (100 Ko).

* **[!UICONTROL Taille maximale de la miniature]**
: taille maximale (en pixels) de la miniature de l’image intégrée. La valeur par défaut est 800 x 800.

* **[!UICONTROL Autoriser les]**
membres privilégiés Si cette option est cochée, seuls les membres privilégiés sont autorisés à créer du contenu.

* **[!UICONTROL Autorisé]**
Membres privilégiés Ajoutez les membres privilégiés autorisés à créer du contenu.

* **[!UICONTROL Bloquer le contenu généré par l’utilisateur en]**
mode d’édition de l’auteur Si cette option est activée, bloque le contenu généré par l’utilisateur lors de la modification en mode d’auteur.

* **[!UICONTROL Titre du journal]** Titre du blog visible dans la page.
   >Remarque :
   >Le titre du journal permet de créer automatiquement l’URL du blog. 50 caractères maximum (avec 5 caractères supplémentaires pour l’unicité) sont utilisés à partir du titre du journal que vous indiquez ici pour créer l’URL du blog.

* **[!UICONTROL Description du journal]** Description du blog.

* **[!UICONTROL Sujets par page]**

   Définit le nombre d’entrées/de commentaires de blog affichés par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]**

   Si cette case est cochée, la publication des entrées et des commentaires de blog doit être approuvée avant d’apparaître sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]**

   Si cette case est cochée, le blog est fermé aux nouveaux commentaires et entrées de blog. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Éditeur de texte enrichi]**

   Si cette case est cochée, les entrées et les commentaires de blog peuvent être saisis avec des balises. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le balisage]**

   Si cette case est cochée, les membres ont le droit d’ajouter des libellés de balise à leur publication (voir l’onglet **[!UICONTROL Champ de balise]** ). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les transferts de fichiers]**

   Si cette option est cochée, les fichiers joints peuvent être ajoutés à une entrée ou à un commentaire de blog. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille maximale du fichier]**

   Convient uniquement si `Allow File Uploads` est coché. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* **[!UICONTROL Types de fichier autorisés]**

   Convient uniquement si `Allow File Uploads` est coché. Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être chargés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Taille max. du fichier image joint]**

   À définir uniquement si l’option Autoriser les chargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Permettre des réponses]**

   Si cette option est cochée, les réponses aux commentaires sont publiées dans l’entrée de blog. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer les commentaires et sujets]**

   Si cette case est cochée, autorisez les membres à supprimer les commentaires et les entrées de blog qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser abonnement]**

   Si cette case est cochée, incluez la fonction suivante pour les articles de blog, ce qui permet aux membres d’être [informés](notifications.md) des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les abonnements par courrier électronique]**

   Si cette case est cochée, autorisez les membres à être informés des nouvelles publications par e-mail ([subscription](subscriptions.md)). `Allow Following` doit être vérifié et [email configuré](email.md). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]**

   Si cette case est cochée, la fonction de vote est ajoutée à une entrée de blog. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher les badges]**

   Si cette case est cochée, affichez les [badges](implementing-scoring.md) gagnés et attribués avec l’entrée de blog d’un membre. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le contenu proposé]**

   si cette case est cochée, l’idée peut être identifiée en tant que [contenu présenté](featured.md). Cette option n’est pas cochée par défaut.

#### Onglet Modération d’utilisateur {#user-moderation-tab}

Sous l’onglet **[!UICONTROL Modération d’utilisateur]**, définissez les paramètres de modération :

* **[!UICONTROL Refuser les publications]**

   Si cette case est cochée, les modérateurs membres approuvés sont autorisés à refuser des publications et à empêcher que la publication ne s’affiche sur le forum public. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]**

   Si cette case est cochée, les membres modérateurs autorisés peuvent fermer une rubrique pour ajouter d’autres modifications et commentaires et rouvrir une rubrique. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les publications]**

   Si cette case est cochée, les membres ont le droit de marquer les sujets ou commentaires d’autres personnes comme étant inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]**

   Si cette case est cochée, les membres ont le droit de choisir dans une liste déroulante la raison pour laquelle ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]**

   Si cette case est cochée, autorisez les membres à indiquer leur propre motif de signalement d’un sujet ou d’un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]**

   Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué par les membres avant que les modérateurs ne soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]**

   Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Si la valeur est -1, le sujet ou le commentaire marqué est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

#### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, spécifiez les balises qui peuvent être appliquées si l’option **[!UICONTROL Autoriser le balisage]** est activée dans l’onglet **[!UICONTROL Paramètres]** :

* **[!UICONTROL Espaces de noms autorisés]**

   Convient si `Allow Tagging` est coché sous l’onglet **[!UICONTROL Paramètres]**. Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (l’espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestions]**

   Saisissez le nombre de balises à afficher comme suggestion au membre qui publie sur le forum. Une valeur de -1 signifie qu’aucune limite n’est définie. La valeur par défaut est 0.

### Configuration de la barre latérale de blog {#configuring-blog-sidebar}

Lorsque vous double-cliquez sur le composant `Blog Sidebar`, une boîte de dialogue de modification s’ouvre.

Sous l’onglet **[!UICONTROL Paramètres de la barre latérale du journal]**, spécifiez le format de date pour les archives et le type d’entrées à afficher dans la barre latérale :

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL Format de la date]**

   Format utilisé pour l’affichage des archives des entrées de blog. Ce format utilise des espaces réservés conformes à la convention Java.

   * yyyy : année à 4 chiffres, par exemple « 2015 »
   * yy : année à 2 chiffres, par exemple « 15 »
   * MMMMM : mois complet, par exemple juin
   * MMM : mois abrégé, par exemple juil.
   * MM : numéro du mois, par exemple 06

   La valeur par défaut est &quot;yyy MMMM&quot;, qui afficherait, par exemple, &quot;2015 June&quot;.

* **[!UICONTROL Type d&#39;affichage]**

   Titre et type des entrées de blog à afficher dans la barre latérale. Le choix est le suivant

   * Auteurs
   * Catégories
   * Archives

* **[!UICONTROL Chemin de composant de journal]**

   *(Facultatif)* Emplacement de la ressource de blog à partir de laquelle les articles de blog doivent être répertoriés. Si rien n’est indiqué, utilisez le composant resourceType `social/journal/components/hbs/journal` qui apparaît sur la même page.

   * Par exemple, `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL Limite de suggestions]**

   Nombre d’articles de blog à afficher. Une valeur de -1 signifie aucune limite. La valeur par défaut est -1.

## Expérience des visiteurs {#site-visitor-experience}

Dans l’environnement de publication, la fonction Blog présente l’article de blog le plus récent suivi des articles plus anciens, dans l’ordre décroissant de leur création. Les barres latérales de blog permettent aux visiteurs d’appliquer des filtres pour limiter la sélection aux articles de blog affichés.

L’article de blog est suivi d’un lien qui permet de publier ou d’afficher des commentaires.

Lorsqu’un article de blog est sélectionné, l’article et ses commentaires sont affichés (si les commentaires sont activés).

Les autres choix varient selon que le visiteur est modérateur, administrateur, membre de la communauté, membre privilégié ou anonyme.

### Fonctionnement des articles  {#working-with-articles}

Lors de la création d’un nouvel article de blog, vous avez le choix entre :

1. le publier immédiatement ;
1. publier son brouillon ;
1. le publier à une date et une heure définies.

Les articles de blog sont visibles sous l’onglet correspondant (Publié, Versions préliminaires ou Planifié) pour les membres autorisés à créer ou à publier.

#### Modérateurs et administrateurs  {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut se charger d’[activités de modération](moderate-ugc.md) (autorisées par la configuration du composant) pour tous les articles et commentaires de blog publiés sur un blog.

![chlimage_1-152](assets/chlimage_1-152.png)

### Membres {#members}

Lorsque l’utilisateur connecté est membre de la communauté ou [membre privilégié](users.md#privileged-members-group) (selon la configuration), il peut sélectionner `New Article` pour créer et publier un nouvel article de blog.

Plus précisément, il est autorisé à:

* Créer un article de blog
* Publier un nouvel article de blog au nom d’un autre membre
* Publication d’un commentaire sur un article de blog
* Modifier son propre article ou commentaire de blog
* Supprimer son propre article ou commentaire de blog
* Marquer les articles ou commentaires de blog d’autres

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### Anonyme {#anonymous}

Les visiteurs non inscrits peuvent lire les articles et les commentaires publiés sur un blog et les traduire lorsque cela est possible. Toutefois, ils ne sont pas autorisés à ajouter un article ou un commentaire de blog, ni à marquer les articles ou les commentaires d’autres membres.

![chlimage_1-155](assets/chlimage_1-155.png)

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous aux [notions fondamentales sur la fonction Blog](blog-developer-basics.md) pour les développeurs.

Pour des informations sur la modération des commentaires et des entrées de blog, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

Pour baliser les entrées et commentaires de blog, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).

Pour des informations sur la traduction des commentaires et des entrées de blog, voir [Traduction de contenu généré par les utilisateurs](translate-ugc.md).
