---
title: Fonction Forum Q&R
seo-title: Fonction Forum Q&R
description: Ajouter la fonction de forum QnA à une page
seo-description: Ajouter la fonction de forum QnA à une page
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 54%

---


# Fonction Forum Q&amp;R {#q-a-forum-feature}

## Présentation {#introduction}

La fonction de forum QnA (questions et réponses) offre aux membres de la communauté un espace où poser et répondre aux questions :

* Créer de nouvelles questions
* Images intégrées (avec glisser-déposer)
* Vue et réponses aux questions
* Rechercher une question
* Aider à modérer le contenu de QnA
* Identifier les meilleures réponses
* Déplacer les questions QnA d&#39;une page à une autre

Cette section de la documentation décrit :

* Ajouter la fonction de forum QnA à un site AEM
* Configuration settings for the `QnA`component

## Ajout d’un forum Q&amp;R à une page {#adding-a-q-a-forum-to-a-page}

Pour ajouter un `QnA` composant à une page en mode création, utilisez l’explorateur de composants pour le localiser `Communities / QnA` et faites-le glisser sur une page sur laquelle le forum QnA doit apparaître.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](qna-essentials.md#essentials-for-client-side) are included, this is how the `QnA` component will appear:

![chlimage_1-280](assets/chlimage_1-280.png)

### Configuration de Q&amp;R {#configuring-qna}

Select the placed `QnA` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Onglet Settings {#settings-tab}

Sous l’onglet **[!UICONTROL Paramètres]**, spécifiez les paramètres pour les sujets (questions) et les réponses :

* **[!UICONTROL Sujets par page]** Définit le nombre de questions/réponses affichées par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]** Si cette option est cochée, les sujets et les commentaires doivent être approuvés avant d’être visibles sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]** Si cette option est cochée, le forum est fermé et n’accepte pas de nouveaux commentaires ou questions. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Éditeur de texte enrichi]** Si cette option est cochée, les sujets et les commentaires peuvent être saisis avec une mise en forme. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, les membres ont le droit d’ajouter des libellés de balise à leur article (voir l’onglet **[!UICONTROL Champ de balise]**). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]** Si cette option est cochée, des fichiers joints peuvent être ajoutés à une question ou à un commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille]** de fichier maximale pertinente uniquement si 
`Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* **[!UICONTROL Types]** de fichiers autorisés pertinents uniquement si 
`Allow File Uploads` est cochée. liste séparée par des virgules d’extensions de fichiers avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichier sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être téléchargés. Par défaut, aucun type de fichier n’est spécifié, de sorte que tous les types de fichier soient autorisés.

* **[!UICONTROL Taille]** de fichier d’image de pièce jointe maximale adaptée uniquement si l’option Autoriser les téléchargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser le suivi]** Si coché, incluez la fonction suivante pour les publications de forum, ce qui permet aux membres d’être [informés](notifications.md) des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Permettre l’épinglage]** Si cette option est cochée, les sujets du forum peuvent être épinglés en haut de la liste des sujets. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les Abonnements]** par courriel Si cette case est cochée, autoriser les membres à être informés des nouvelles publications par courriel ([abonnement](subscriptions.md)). Nécessite `Allow Following` la vérification et la configuration [du](email.md)courrier électronique. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les réponses]** Si cette option est cochée, les réponses aux commentaires sont publiées pour la question. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer les commentaires et sujets]** Si cette option est cochée, les membres ont le droit de supprimer les commentaires et les questions qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]** Si cette option est cochée, la fonction de vote est ajoutée à une question. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Déplacer la réponse sélectionnée vers le haut]** Si cette option est cochée, la première réponse qui s’affiche est la réponse sélectionnée. Cette option est cochée par défaut.

* **[!UICONTROL Afficher les insignes]** Si coché, afficher les [insignes](implementing-scoring.md) gagnés et attribués avec l&#39;entrée de blog d&#39;un membre. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Si l’option Autoriser le contenu]** proposé est cochée, l’idée peut être identifiée comme contenu [](featured.md)phare. Cette option n’est pas cochée par défaut.

#### Onglet Modération utilisateur {#user-moderation-tab}

Under the **[!UICONTROL User Moderation]** tab, specify how the posted topics (quetions) and answers (user generated content) are managed. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Refuser les réponses]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de refuser des réponses et, par conséquent, d’empêcher leur publication sur le forum Q&amp;R. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de fermer une question (un sujet) pour empêcher la publication d’autres modifications et réponses, puis de le rouvrir. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Déplacer des rubriques]** Si cette option est cochée, autorisez les modérateurs côté publication à déplacer les questions. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les publications]** Si cette option est cochée, les membres ont le droit de marquer les questions ou réponses d’autres membres comme étant inappropriées. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est cochée, les membres ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué une question ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué une question ou une réponse comme étant inappropriée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’une question ou une réponse doit être marquée par les membres avant que les modérateurs n’en soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’une question ou une réponse doit être marquée avant qu’il ne soit plus visible pour le public. Si la valeur est -1, la question ou la réponse marquée est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

#### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, les balises qui peuvent être appliquées, si l’option est activée dans l’onglet **[!UICONTROL Paramètres]**, sont limitées selon les espaces de noms sélectionnés.

* **[!UICONTROL Espaces de nommage]** pertinents autorisés si 
`Allow Tagging` est cochée sous l’onglet **Paramètres** . Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de nommage inclut &quot;Balises standard&quot; (l’espace de nommage par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de nommage sont autorisés.

* **[!UICONTROL Limite de suggestions]** Entrez le nombre de balises à afficher comme suggestion destinée au membre qui publie sur le forum. Une valeur de 
`-1` signifie pas de limites. La valeur par défaut est 0.

#### Onglet Paramètres de tri {#sort-settings-tab}

Sous l’onglet Paramètres **[!UICONTROL de]** tri, indiquez comment les commentaires publiés sont triés lorsqu’ils s’affichent.

* **[!UICONTROL Trier par]** Vérifier toutes les sélections de tri autorisées : 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. La valeur par défaut est `Newest, Oldest, Last Updated`.

* **[!UICONTROL Définir comme valeur par défaut]** Décompressez pour sélectionner l’une des options de tri cochées à afficher comme valeur par défaut. La valeur par défaut est 
`Newest`.

* **[!UICONTROL Sélectionnez les options d’heure pour Analytics Tri]** déroulant pour sélectionner l’une des options suivantes : 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. La valeur par défaut est `All`.

## Expérience des visiteurs {#site-visitor-experience}

### Identification des réponses {#identifying-answers}

Une réponse peut être marquée comme une réponse correcte ou utile à l&#39;aide du `Select Answer` bouton. Une fois qu&#39;une question est marquée comme Réponse, une autre réponse ne peut pas être sélectionnée tant que la première n&#39;a pas été désélectionnée à l&#39;aide du `Unmark Chosen Answer`bouton.

Once selected as a viable answer, it may be unselected using the `Unmark Chosen Answer` button.

Une fois qu&#39;une réponse est sélectionnée comme réponse viable, une indication que la question a été `Answered`affichée en regard de la rubrique de la question sur la page principale d&#39;évaluation quantitative.

### Modérateurs et administrateurs {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut se charger d’activités de modération autorisées par la configuration du composant, peu importe qui a créé la question ou la réponse.

Il peut également identifier les réponses.

### Membres {#members}

Lorsque le visiteur est connecté, selon la configuration, il peut :

* Publication d’une nouvelle question
* Modifier ou supprimer les questions qu&#39;ils ont créées
* Peut aussi signaler les questions ou réponses d&#39;autres personnes
* Peut identifier les réponses aux questions qu&#39;ils ont rédigées

### Anonyme {#anonymous}

Les visiteurs non inscrits peuvent lire les questions et les réponses publiées et les traduire lorsque cela est possible. Toutefois, ils ne sont pas autorisés à ajouter de question ou de réponse, ni à marquer les publications d’autres membres.

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur la fonction Q&amp;R](qna-essentials.md) pour les développeurs.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).
