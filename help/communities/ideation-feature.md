---
title: Fonction d’orientation
seo-title: Fonction d’orientation
description: Ajoute et configuration de la fonction d’orientation
seo-description: Ajoute et configuration de la fonction d’orientation
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


# Fonction d&#39;idée {#ideation-feature}

## Présentation {#introduction}

La fonctionnalité d’idéation fournit une zone pour les visiteurs de site connectés (membres de la communauté) dans l’environnement de publication pour :

* Créer des idées à partager avec la communauté
* Vue et commentaires sur les idées
* Suivre une idée
* Voter pour une idée

Cette section de la documentation décrit :

* Ajouter la fonction d&#39;idéation à un site AEM
* Paramètres de configuration du composant Idéation

## Ajouter une idée à une page {#adding-a-ideation-to-a-page}

Pour ajouter un composant `Ideation` à une page en mode création, utilisez l&#39;explorateur de composants pour localiser `Communities / Ideation` et faites-le glisser sur une page sur laquelle l&#39;idée doit apparaître.

Pour obtenir les informations nécessaires, consultez [Community Components Basics](basics.md).

Lorsque les [bibliothèques client requises](ideation.md#essentials-for-client-side) sont incluses, c&#39;est ainsi que le composant `Ideation`s&#39;affiche :

![chlimage_1-29](assets/chlimage_1-29.png)

## Configuration d&#39;une idéation {#configuring-an-ideation}

Sélectionnez le composant `Ideation` placé auquel accéder et sélectionnez l&#39;icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Onglet Settings {#settings-tab}

Sous l&#39;onglet **[!UICONTROL Paramètres]**, spécifiez les paramètres pour les idées et les commentaires :

* **[!UICONTROL Titre]**
de l&#39;idéeTitre de l&#39;affichage de l&#39;idée. La valeur par défaut est 
`Ideation`.

* **[!UICONTROL Description]**
de l&#39;idéeDescription à afficher en tant que sous-titre de l&#39;idée. La valeur par défaut n’est pas une description.

* **[!UICONTROL Rubriques par]**
pageDéfinit le nombre d’idées/de publications affichées par page. La valeur par défaut est 10.

* ****
ModéréSi cette option est cochée, la publication d’idées et de commentaires doit être approuvée avant d’apparaître sur un site de publication. Cette option n’est pas cochée par défaut.

* ****
FerméSi cette option est cochée, le forum d&#39;idéation est fermé aux nouvelles idées et commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Editeur de texte enrichiSi cette option est cochée, les idées et les commentaires peuvent être saisis avec une annotation.]**
Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, les membres ont le droit d’ajouter des libellés de balise à leur article (voir l’onglet **[!UICONTROL Champ de balise]**). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les]**
téléchargements de fichiersSi cette case est cochée, autorisez l&#39;ajout de pièces jointes à l&#39;idée ou au commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille]**
de fichier maximaleRelevant uniquement si 
`Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* ****
Types de fichiers autorisésPertinent uniquement si 
`Allow File Uploads` est cochée. Liste séparée par des virgules d’extensions de fichiers avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichier sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être téléchargés. Par défaut, aucun type de fichier n’est spécifié, de sorte que tous les types de fichier soient autorisés.

* **[!UICONTROL Taille maximale du fichier image jointPertinente uniquement si l’option Autoriser les téléchargements de fichiers est cochée.]**
Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser les]**
réponsesSi cette case est cochée, autoriser les réponses aux commentaires publiés sur l&#39;idée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer des commentaires et des]**
rubriquesSi cette option est cochée, autorisez les membres à supprimer les commentaires et les idées qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser]**
le suivi Si coché, incluez la fonctionnalité suivante pour les publications d’idées, ce qui permet aux membres d’être  [](notifications.md) avertis des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser]**
les abonnements au courrielSi cette option est cochée, autorisez les membres à être avertis des nouvelles publications par courriel ([abonnement](subscriptions.md)). `Allow Following` doit être vérifié et [e-mail configuré](email.md). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le]**
voteSi coché, autoriser le vote sur les commentaires d&#39;une idée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher les]**
badgesSi cette case est cochée, afficher les  [](implementing-scoring.md) badges gagnés et attribués avec l&#39;idée d&#39;un membre. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Si l’option Autoriser la]**
conservation des éléments en vedette est cochée, l’idée peut être identifiée comme contenu [ ](featured.md)présenté. Cette option n’est pas cochée par défaut.

### Onglet Modération utilisateur {#user-moderation-tab}

Sous l’onglet **[!UICONTROL Modération utilisateur]**, indiquez comment les idées et commentaires publiés (contenu généré par l’utilisateur) sont gérés. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Refuser les publications]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de refuser des articles et, par conséquent, d’empêcher leur publication sur le forum public. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de fermer un sujet pour empêcher la publication d’autres modifications et de commentaires, puis de le rouvrir. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les publications]** Si cette option est cochée, les membres ont le droit de marquer les sujets ou commentaires d’autres membres comme étant inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est cochée, les membres ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué par les membres avant que les modérateurs n’en soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Si la valeur est -1, le sujet ou le commentaire marqué est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, les balises qui peuvent être appliquées, si l’option est activée dans l’onglet **[!UICONTROL Paramètres]**, sont limitées selon les espaces de noms sélectionnés.

* **[!UICONTROL Allowed]**
NamespacesRelevant si 
`Allow Tagging` est cochée sous  **** Paramètres. Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de nommage inclut &quot;Balises standard&quot; (l’espace de nommage par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de nommage sont autorisés.

* **[!UICONTROL Limite de suggestions]** Entrez le nombre de balises à afficher comme suggestion destinée au membre qui publie sur le forum. Une valeur de 
**-** 1 signifie aucune limite. La valeur par défaut est 0.

### Onglet Paramètres de tri {#sort-settings-tab}

Sous l’onglet **[!UICONTROL Paramètres de tri]**, spécifiez le mode de tri des commentaires publiés lorsqu’ils s’affichent.

* **[!UICONTROL Trier]**
parVérifier toutes les sélections de tri autorisées : 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. La valeur par défaut est `Newest, Oldest, Last Updated`.

* **[!UICONTROL Définissez comme]**
DefaultPull down pour sélectionner l’une des options de tri cochées pour apparaître comme valeur par défaut. La valeur par défaut est 
`Newest`.

* **[!UICONTROL Sélectionnez les options d’heure pour Analytics]**
TriPull vers le bas pour sélectionner l’une des options suivantes : 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. La valeur par défaut est `All`.

## Expérience des visiteurs {#site-visitor-experience}

### Création d&#39;une idée {#creating-idea}

Comme pour toutes les fonctionnalités des Communautés, si elles ne sont pas connectées, un visiteur de site ne peut lire que des idées et vue d&#39;autres opinions (par le biais de commentaires et de votes/appréciations).

Une fois connecté, un membre peut créer une nouvelle idée.

![chlimage_1-32](assets/chlimage_1-32.png)

Avant de soumettre l&#39;idée, le membre peut enregistrer un brouillon.

En sélectionnant le bouton `Save as Draft`, un brouillon est enregistré.

![chlimage_1-33](assets/chlimage_1-33.png)

Lors de l&#39;affichage des brouillons enregistrés dans l&#39;onglet `My Drafts`, sélectionnez `Read More` pour revenir en mode d&#39;édition :

![chlimage_1-34](assets/chlimage_1-34.png)

#### Fournir des commentaires {#providing-feedback}

Une fois l&#39;idée publiée, d&#39;autres membres peuvent se connecter, ouvrir l&#39;idée ( `Read More`) et aimer l&#39;idée, ajoutant ainsi au nombre de votes, et faire des commentaires.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informations supplémentaires {#additional-information}

Pour plus d&#39;informations, consultez la page [Ideation Essentials](ideation.md) destinée aux développeurs.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).
