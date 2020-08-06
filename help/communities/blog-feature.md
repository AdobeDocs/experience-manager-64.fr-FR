---
title: Fonction Blog
seo-title: Fonction Blog
description: Information de la communauté dans un format de journalisation
seo-description: Information de la communauté dans un format de journalisation
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c
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

* Ajouter la fonction de blog à un site AEM
* Paramètres de configuration des composants de blog

>[!NOTE]
>
>Les composants `Journal`et `Journal Sidebar` sont intitulés `Blog` et `Blog Sidebar`.
>
>La fonction Blog disponible dans AEM 6.0 et versions antérieures a été supprimée. Elle était basée sur un modèle et autorisait uniquement les auteurs à créer du contenu dans l’environnement de création.

## Ajout de composants de blog à une page {#adding-blog-components-to-a-page}

Si vous souhaitez ajouter un blog à une page en mode création, utilisez le navigateur de composants pour localiser

* `Communities / Blog`
* `Communities / Blog Sidebar`

Et faites-les glisser sur une page où le blog doit apparaître.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](blog-developer-basics.md#essentials-for-client-side) are included, this is how the `Blog`component will appear:

![chlimage_1-147](assets/chlimage_1-147.png)

Et comment `Blog Sidebar` apparaîtra :

![chlimage_1-148](assets/chlimage_1-148.png)

### Configuration du blog {#configuring-blog}

Select the placed `Blog` component to access and select the `Configure` icon which opens the edit dialog.

![configurer les paramètres de l&#39;icône](assets/chlimage_1-149.png) ![de blog](assets/Blog-configure.png)

#### Onglet Settings {#settings-tab}

Sous l’onglet **[!UICONTROL Paramètres]**, définissez les fonctionnalités de base du blog :

* **[!UICONTROL Autoriser la miniature]** des pièces jointes Si cette case est cochée, une miniature de l’image jointe est créée.

* **[!UICONTROL Taille]** maximale des miniatures d’attachement (en pixels) Taille maximale de l’image miniature de la pièce jointe. La valeur par défaut est 800 x 800.

* **[!UICONTROL Taille minimale de l’image pour la miniature]** Taille minimale (en octets) de l’image pour la génération de la miniature pour les images insérées. La valeur par défaut est de 100 000 octets (100 Ko).

* **[!UICONTROL Taille]** maximale des vignettes Taille maximale (en pixels) de l’image miniature pour l’image intégrée. La valeur par défaut est 800 x 800.

* **[!UICONTROL Autoriser les membres]** privilégiés Si cette case est cochée, seuls les membres privilégiés sont autorisés à créer du contenu.

* **[!UICONTROL Les membres]** privilégiés autorisés Ajoutent les membres privilégiés autorisés à créer du contenu.

* **[!UICONTROL Bloquer le contenu généré par l’utilisateur en mode]** d’édition Auteur Si cette option est activée, bloque le contenu généré par l’utilisateur lors de la modification en mode Auteur.

* **[!UICONTROL Titre du journal]** Titre du blog visible dans la page.
   >Remarque :
   >Le titre du Journal permet de créer automatiquement l&#39;URL du blog. Le titre du journal que vous spécifiez ici permet d&#39;utiliser au maximum 50 caractères (avec 5 caractères supplémentaires pour l&#39;unicité) pour créer l&#39;URL du blog.

* **[!UICONTROL Description du journal]** Description du blog.

* **[!UICONTROL Sujets par page]**

   Définit le nombre d&#39;entrées/commentaires de blog affichés par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]**

   Si cette case est cochée, la publication des entrées et commentaires du blog doit être approuvée avant d&#39;apparaître sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]**

   Si cette case est cochée, le blog est fermé aux nouveaux commentaires et entrées de blog. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Éditeur de texte enrichi]**

   Si cette case est cochée, les entrées et commentaires de blog peuvent être saisis avec une annotation. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le balisage]**

   If checked, allow members to add tag labels to their post (see **[!UICONTROL Tag field]** tab). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les transferts de fichiers]**

   Si cette option est cochée, autorisez l&#39;ajout de pièces jointes à une entrée ou un commentaire de blog. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille maximale du fichier]**

   Ne s’applique que si `Allow File Uploads` la vérification est effectuée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* **[!UICONTROL Types de fichier autorisés]**

   Ne s’applique que si `Allow File Uploads` la vérification est effectuée. liste séparée par des virgules d’extensions de fichiers avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichier sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être téléchargés. Par défaut, aucun type de fichier n’est spécifié, de sorte que tous les types de fichier soient autorisés.

* **[!UICONTROL Taille max. du fichier image joint]**

   N’est pertinent que si l’option Autoriser les téléchargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Permettre des réponses]**

   Si cette option est cochée, autorisez les réponses aux commentaires publiés sur l&#39;entrée de blog. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer les commentaires et sujets]**

   Si cette option est cochée, autorisez les membres à supprimer les commentaires et les entrées de blog qu&#39;ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser abonnement]**

   Si cette option est cochée, incluez la fonctionnalité suivante pour les articles de blog, ce qui permet aux membres d&#39;être [informés](notifications.md) des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les abonnements par courrier électronique]**

   Si cette case est cochée, autorisez les membres à être informés des nouvelles publications par courriel ([abonnement](subscriptions.md)). Nécessite `Allow Following` la vérification et la configuration [du](email.md)courrier électronique. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]**

   Si cette case est cochée, incluez la fonction de vote avec une entrée de blog. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher les badges]**

   Si cette option est cochée, affichez les [badges](implementing-scoring.md) gagnés et attribués avec l&#39;entrée de blog d&#39;un membre. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le contenu proposé]**

   si cette option est cochée, l’idée peut être identifiée comme contenu [](featured.md)phare. Cette option n’est pas cochée par défaut.

#### Onglet Modération utilisateur {#user-moderation-tab}

Sous l’onglet **[!UICONTROL Modération d’utilisateur]**, définissez les paramètres de modération :

* **[!UICONTROL Refuser les publications]**

   Si cette option est cochée, les modérateurs membres de confiance seront autorisés à refuser les publications et à empêcher que la publication ne s&#39;affiche sur le forum public. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]**

   Si cette option est cochée, les modérateurs membres approuvés peuvent fermer une rubrique pour apporter d’autres modifications et commentaires et peuvent également rouvrir une rubrique. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les publications]**

   Si cette option est cochée, autorisez les membres à signaler les sujets ou commentaires d&#39;autres personnes comme inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]**

   Si cette option est cochée, permettez aux membres de choisir, dans une liste déroulante, la raison pour laquelle ils signalent une rubrique ou un commentaire comme inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]**

   Si cette option est cochée, autorisez les membres à entrer leur propre raison de signaler une rubrique ou un commentaire comme inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]**

   Indiquez le nombre de fois où une rubrique ou un commentaire doit être marqué par les membres avant que les modérateurs ne soient avertis. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]**

   Saisissez le nombre de fois où une rubrique ou un commentaire doit être marqué avant d’être masqué dans la vue publique. Si la valeur est -1, le sujet ou le commentaire marqué est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

#### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, spécifiez les balises qui peuvent être appliquées si l’option **[!UICONTROL Autoriser le balisage]** est activée dans l’onglet **[!UICONTROL Paramètres]** :

* **[!UICONTROL Espaces de noms autorisés]**

   Pertinent si `Allow Tagging` est coché sous l’onglet **[!UICONTROL Paramètres]** . Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de nommage inclut &quot;Balises standard&quot; (l’espace de nommage par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de nommage sont autorisés.

* **[!UICONTROL Limite de suggestions]**

   Entrez le nombre de balises à afficher comme suggestion au membre qui publie sur le forum. La valeur -1 signifie qu’aucune limite n’est définie. La valeur par défaut est 0.

### Configuration de la barre latérale de blog {#configuring-blog-sidebar}

When you double-click the `Blog Sidebar` component, an edit dialog opens up.

Sous l’onglet **[!UICONTROL Paramètres de la barre latérale du journal]**, spécifiez le format de date pour les archives et le type d’entrées à afficher dans la barre latérale :

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL Format de la date]**

   Format utilisé pour afficher les archives des entrées de blog. Ce format utilise des espaces réservés conformes à la convention Java.

   * yyyy : année à 4 chiffres, par exemple « 2015 »
   * yy : année à 2 chiffres, par exemple « 15 »
   * MMMMM : mois complet, par exemple juin
   * MMM : mois abrégé, par exemple juil.
   * MM : numéro du mois, par exemple 06

   La valeur par défaut est &quot;yyy MMMM&quot; qui s’affichera, par exemple, &quot;juin 2015&quot;.

* **[!UICONTROL Type d&#39;affichage]**

   Titre et type des entrées de blog à afficher dans la barre latérale. Le choix est le suivant

   * Auteurs
   * Catégories
   * Archives

* **[!UICONTROL Chemin de composant de journal]**

   *(Facultatif)* Emplacement de la ressource de blog à partir de laquelle les articles de blog doivent être répertoriés. S&#39;il reste vide, utilise le composant de resourceType `social/journal/components/hbs/journal` qui apparaît sur la même page.

   * Par exemple, `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL Limite de suggestions]**

   Nombre d&#39;articles de blog à afficher. La valeur -1 signifie aucune limite. La valeur par défaut est -1.

## Expérience des visiteurs {#site-visitor-experience}

Dans l’environnement de publication, la fonction Blog présente l’article de blog le plus récent suivi des articles plus anciens, dans l’ordre décroissant de leur création. Les barres latérales de blog permettent aux visiteurs d’appliquer des filtres pour limiter la sélection aux articles de blog affichés.

L’article de blog est suivi d’un lien qui permet de publier ou d’afficher des commentaires.

Lorsqu’un article de blog est sélectionné, l’article et ses commentaires sont affichés (si les commentaires sont activés).

Les autres choix varient selon que le visiteur est modérateur, administrateur, membre de la communauté, membre privilégié ou anonyme.

### Fonctionnement des articles {#working-with-articles}

Lors de la création d’un nouvel article de blog, vous avez le choix entre :

1. le publier immédiatement ;
1. publier son brouillon ;
1. le publier à une date et une heure définies.

Les articles de blog sont visibles sous l’onglet correspondant (Publié, Versions préliminaires ou Planifié) pour les membres autorisés à créer ou à publier.

#### Modérateurs et administrateurs {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut se charger d’[activités de modération](moderate-ugc.md) (autorisées par la configuration du composant) pour tous les articles et commentaires de blog publiés sur un blog.

![chlimage_1-152](assets/chlimage_1-152.png)

### Membres {#members}

When the signed in user is a community member or [privileged member](users.md#privileged-members-group) (depending on configuration), they are able to select `New Article` to create and post a new blog article.

Plus précisément, il est autorisé à:

* Création d’un article de blog
* Publier un nouvel article de blog pour le compte d&#39;un autre membre
* Publication d’un commentaire sur un article de blog
* Modifier leur propre article ou commentaire de blog
* Supprimer leur propre article ou commentaire de blog
* Signaler les articles ou commentaires sur le blog d&#39;autres internautes

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### Anonyme {#anonymous}

Les visiteurs non inscrits peuvent lire les articles et les commentaires publiés sur un blog et les traduire lorsque cela est possible. Toutefois, ils ne sont pas autorisés à ajouter un article ou un commentaire de blog, ni à marquer les articles ou les commentaires d’autres membres.

![chlimage_1-155](assets/chlimage_1-155.png)

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous aux [notions fondamentales sur la fonction Blog](blog-developer-basics.md) pour les développeurs.

Pour des informations sur la modération des commentaires et des entrées de blog, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

Pour baliser les entrées et commentaires de blog, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).

Pour des informations sur la traduction des commentaires et des entrées de blog, voir [Traduction de contenu généré par les utilisateurs](translate-ugc.md).
