---
title: Fonction d’orientation
seo-title: Fonction d’orientation
description: Ajoute et configuration de la fonction Idéation
seo-description: Ajoute et configuration de la fonction Idéation
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 36%

---


# Fonction d’orientation {#ideation-feature}

## Présentation {#introduction}

La fonctionnalité d’idéation fournit une zone pour les visiteurs de site connectés (membres de la communauté) dans l’environnement de publication pour :

* Créer des idées à partager avec la communauté
* Vue et commentaires sur les idées
* Suivre une idée
* Voter pour une idée

Cette section de la documentation décrit :

* Ajouter la fonction d’idéation à un site AEM
* Paramètres de configuration du composant Idéation

## Adding a Ideation to a Page {#adding-a-ideation-to-a-page}

Pour ajouter un `Ideation` composant à une page en mode création, utilisez l’explorateur de composants pour le localiser `Communities / Ideation` et faites-le glisser sur une page sur laquelle l’idée doit apparaître.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](ideation.md#essentials-for-client-side) are included, this is how the `Ideation`component will appear:

![chlimage_1-29](assets/chlimage_1-29.png)

## Configuration d’une idéation {#configuring-an-ideation}

Select the placed `Ideation` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Onglet Settings {#settings-tab}

Under the **[!UICONTROL Settings]** tab, specify settings for ideas and comments:

* **[!UICONTROL Titre]** de l’idée Titre de l’affichage de l’idée. La valeur par défaut est 
`Ideation`.

* **[!UICONTROL Description]** de l’idée Description à afficher en tant que sous-titre de l’idée. La valeur par défaut n’est pas une description.

* **[!UICONTROL Rubriques par page]** Définit le nombre d’idées/de publications affichées par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]** Si cette option est cochée, la publication d’idées et de commentaires doit être approuvée avant d’apparaître sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]** S&#39;il est coché, le forum d&#39;idéation est fermé aux idées et commentaires nouveaux. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Editeur]** de texte enrichi Si cette option est cochée, les idées et les commentaires peuvent être saisis avec des annotations. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, les membres ont le droit d’ajouter des libellés de balise à leur article (voir l’onglet **[!UICONTROL Champ de balise]**). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les téléchargements]** de fichiers Si cette option est cochée, autorisez l’ajout de pièces jointes à l’idée ou au commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille]** de fichier maximale pertinente uniquement si 
`Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* **[!UICONTROL Types]** de fichiers autorisés pertinents uniquement si 
`Allow File Uploads` est cochée. liste séparée par des virgules d’extensions de fichiers avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichier sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être téléchargés. Par défaut, aucun type de fichier n’est spécifié, de sorte que tous les types de fichier soient autorisés.

* **[!UICONTROL Taille]** de fichier d’image de pièce jointe maximale adaptée uniquement si l’option Autoriser les téléchargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser les réponses]** Si cette option est cochée, autoriser les réponses aux commentaires publiés sur l’idée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer des commentaires et des rubriques]** Si cette option est cochée, autoriser les membres à supprimer les commentaires et les idées qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le suivi]** Si coché, incluez la fonctionnalité suivante pour les publications d’idées, ce qui permet aux membres d’être [avertis](notifications.md) des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les Abonnements]** par courriel Si cette case est cochée, autoriser les membres à être informés des nouvelles publications par courriel ([abonnement](subscriptions.md)). Nécessite `Allow Following` la vérification et la configuration [du](email.md)courrier électronique. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]** Si coché, autoriser le vote sur les commentaires d&#39;une idée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher les insignes]** Si cette option est cochée, afficher les [insignes](implementing-scoring.md) gagnés et attribués avec l’idée d’un membre. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Si l’option Autoriser le contenu]** proposé est cochée, l’idée peut être identifiée comme contenu [](featured.md)phare. Cette option n’est pas cochée par défaut.

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

* **[!UICONTROL Espaces de nommage]** pertinents autorisés si 
`Allow Tagging` est cochée sous l’onglet **Paramètres** . Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de nommage inclut &quot;Balises standard&quot; (l’espace de nommage par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de nommage sont autorisés.

* **[!UICONTROL Limite de suggestions]** Entrez le nombre de balises à afficher comme suggestion destinée au membre qui publie sur le forum. Une valeur de 
**-** 1 signifie aucune limite. La valeur par défaut est 0.

### Onglet Paramètres de tri {#sort-settings-tab}

Sous l’onglet Paramètres **[!UICONTROL de]** tri, indiquez comment les commentaires publiés sont triés lorsqu’ils s’affichent.

* **[!UICONTROL Trier par]** Vérifier toutes les sélections de tri autorisées : 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. La valeur par défaut est `Newest, Oldest, Last Updated`.

* **[!UICONTROL Définir comme valeur par défaut]** Décompressez pour sélectionner l’une des options de tri cochées à afficher comme valeur par défaut. La valeur par défaut est 
`Newest`.

* **[!UICONTROL Sélectionnez les options d’heure pour Analytics Tri]** déroulant pour sélectionner l’une des options suivantes : 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. La valeur par défaut est `All`.

## Expérience des visiteurs {#site-visitor-experience}

### Création d’idées {#creating-idea}

Comme pour toutes les fonctionnalités des Communautés, si elles ne sont pas connectées, un visiteur de site ne peut lire que des idées et vue d&#39;autres opinions (par le biais de commentaires et de votes/appréciations).

Une fois connecté, un membre peut créer une nouvelle idée.

![chlimage_1-32](assets/chlimage_1-32.png)

Avant de soumettre l&#39;idée, le membre peut enregistrer un brouillon.

En sélectionnant le `Save as Draft` bouton, un brouillon est enregistré.

![chlimage_1-33](assets/chlimage_1-33.png)

Lors de l’affichage des brouillons enregistrés dans l’ `My Drafts` onglet, sélectionnez `Read More` de revenir en mode d’édition :

![chlimage_1-34](assets/chlimage_1-34.png)

#### Fournir des commentaires {#providing-feedback}

Une fois l&#39;idée publiée, d&#39;autres membres peuvent se connecter, ouvrir l&#39;idée ( `Read More`) et aimer l&#39;idée, ajoutant ainsi au nombre de votes, et faire des commentaires.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informations supplémentaires {#additional-information}

More information may be found on the [Ideation Essentials](ideation.md) page for developers.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).
