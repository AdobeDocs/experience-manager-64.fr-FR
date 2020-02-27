---
title: Fonctionnalité d’orientation
seo-title: Fonctionnalité d’orientation
description: Ajout et configuration de la fonction d’orientation
seo-description: Ajout et configuration de la fonction d’orientation
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Fonctionnalité d’orientation {#ideation-feature}

## Présentation {#introduction}

La fonctionnalité d’idéation fournit une zone aux visiteurs du site connectés (membres de la communauté) dans l’environnement de publication pour :

* Créer des idées à partager avec la communauté
* Afficher et commenter les idées
* Suivre une idée
* Voter pour une idée

Cette section de la documentation décrit :

* Ajout de la fonctionnalité d’idéation à un site AEM
* Paramètres de configuration du composant Ideation

## Adding a Ideation to a Page {#adding-a-ideation-to-a-page}

Pour ajouter un `Ideation` composant à une page en mode création, utilisez l’explorateur de composants pour le localiser `Communities / Ideation` et le faire glisser sur une page où l’idée doit apparaître.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](ideation.md#essentials-for-client-side) are included, this is how the `Ideation`component will appear:

![chlimage_1-29](assets/chlimage_1-29.png)

## Configuration d’une idée {#configuring-an-ideation}

Select the placed `Ideation` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Onglet Settings {#settings-tab}

Under the **[!UICONTROL Settings]** tab, specify settings for ideas and comments:

* **[!UICONTROL Titre]** de l’idée Titre de l’affichage de l’idée. La valeur par défaut est `Ideation`.

* **[!UICONTROL Description]** de l’idée Description à afficher en tant que sous-titre de l’idée. La valeur par défaut n’est pas une description.

* **[!UICONTROL Rubriques par page]** Définit le nombre d’idées/de publications affichées par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]** Si cette option est cochée, la publication d’idées et de commentaires doit être approuvée avant qu’ils ne s’affichent sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]** S&#39;il est coché, le forum d&#39;idéation est fermé aux idées et aux commentaires nouveaux. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Editeur]** de texte enrichi Si cette option est cochée, les idées et les commentaires peuvent être saisis avec un balisage. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, les membres ont le droit d’ajouter des libellés de balise à leur article (voir l’onglet **[!UICONTROL Champ de balise]**). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les téléchargements]** de fichiers Si cette option est cochée, autorisez l’ajout de pièces jointes à l’idée ou au commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille]** de fichier maximale pertinente uniquement si `Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 1 048 57 600 (10 Mo).

* **[!UICONTROL Types]** de fichiers autorisés pertinents uniquement si `Allow File Uploads` l’option est cochée. Liste d’extensions de fichiers séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichier sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être téléchargés. Par défaut, aucun type de fichier n’est spécifié, de sorte que tous les types de fichier soient autorisés.

* **[!UICONTROL Taille]** max. du fichier image joint, applicable uniquement si l’option Autoriser les téléchargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser les réponses]** Si cette option est cochée, autoriser les réponses aux commentaires publiés sur l’idée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer des commentaires et des rubriques]** Si cette option est cochée, autoriser les membres à supprimer les commentaires et idées qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le suivi]** Si cette option est cochée, incluez la fonctionnalité suivante pour les publications d’idées, ce qui permet aux membres d’être [informés](notifications.md) des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les abonnements]** par courrier électronique Si cette option est cochée, autorisez les membres à être avertis des nouvelles publications par courrier électronique ([abonnement](subscriptions.md)). Requiert `Allow Following` la vérification et la configuration [du](email.md)courrier électronique. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]** Si coché, autoriser le vote sur les commentaires d&#39;une idée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher les badges]** Si coché, afficher les [badges](implementing-scoring.md) gagnés et attribués avec l’idée d’un membre. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Si cette option est cochée, l’idée peut être identifiée comme contenu]**[](featured.md)phare. Cette option n’est pas cochée par défaut.

### Onglet Modération utilisateur {#user-moderation-tab}

Under the **[!UICONTROL User Moderation]** tab, specify how the posted ideas and comments (user generated content) are managed. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Refuser les publications]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de refuser des articles et, par conséquent, d’empêcher leur publication sur le forum public. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de fermer un sujet pour empêcher la publication d’autres modifications et de commentaires, puis de le rouvrir. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les publications]** Si cette option est cochée, les membres ont le droit de marquer les sujets ou commentaires d’autres membres comme étant inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est cochée, les membres ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué par les membres avant que les modérateurs n’en soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Si la valeur est -1, le sujet ou le commentaire marqué est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, les balises qui peuvent être appliquées, si l’option est activée dans l’onglet **[!UICONTROL Paramètres]**, sont limitées selon les espaces de noms sélectionnés.

* **[!UICONTROL Espaces de noms]** autorisés pertinents si `Allow Tagging` l’option est cochée sous l’onglet **Paramètres** . Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestions]** Entrez le nombre de balises à afficher comme suggestion destinée au membre qui publie sur le forum. La valeur **-** 1 signifie aucune limite. La valeur par défaut est 0.

### Onglet Paramètres de tri {#sort-settings-tab}

Sous l’onglet Paramètres **[!UICONTROL de]** tri, spécifiez le mode de tri des commentaires publiés lorsqu’ils sont affichés.

* **[!UICONTROL Trier par]** Vérifier toutes les sélections de tri autorisées : `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. La valeur par défaut est `Newest, Oldest, Last Updated`.

* **[!UICONTROL Définissez cette option comme valeur par défaut]** Tirez vers le bas pour sélectionner l’une des options de tri cochées à afficher comme valeur par défaut. La valeur par défaut est `Newest`.

* **[!UICONTROL Sélectionnez Options de temps pour le tri]** Analytics. Décompressez pour sélectionner l’une des options `All, Last 24 Hours, Last 7 Days, Last 30 Days`. La valeur par défaut est `All`.

## Expérience des visiteurs {#site-visitor-experience}

### Création d’une idée {#creating-idea}

Comme pour toutes les fonctionnalités des communautés, si elles ne sont pas connectées, un visiteur du site peut seulement lire des idées et consulter d&#39;autres opinions (par le biais de commentaires et de votes/appréciations).

Une fois connecté, un membre peut créer une nouvelle idée.

![chlimage_1-32](assets/chlimage_1-32.png)

Avant de soumettre l&#39;idée, il est possible que le membre enregistre un brouillon.

En sélectionnant le `Save as Draft` bouton, un brouillon est enregistré.

![chlimage_1-33](assets/chlimage_1-33.png)

Lors de l’affichage des brouillons enregistrés dans le `My Drafts` panneau, sélectionnez `Read More` pour revenir en mode d’édition :

![chlimage_1-34](assets/chlimage_1-34.png)

#### Fournir des commentaires {#providing-feedback}

Une fois l&#39;idée publiée, les autres membres peuvent se connecter, ouvrir l&#39;idée ( `Read More`) et aimer l&#39;idée, ce qui ajoute au nombre de votes, et faire des commentaires.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informations supplémentaires {#additional-information}

More information may be found on the [Ideation Essentials](ideation.md) page for developers.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).
