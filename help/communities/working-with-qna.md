---
title: Fonction Forum Q&R
seo-title: Q&A Forum Feature
description: Ajout de la fonction Forum Q&R à une page
seo-description: Adding the QnA forum feature to a page
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
exl-id: af16f4df-ed8e-40e4-b117-3d612e122947
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 55%

---

# Fonction Forum Q&amp;R {#q-a-forum-feature}

## Présentation {#introduction}

La fonction de forum Q&amp;R (questions et réponses) offre aux membres de la communauté un espace où poser leurs questions et y répondre :

* Créer de nouvelles questions
* Images intégrées (avec glisser-déposer)
* Afficher et répondre aux questions
* Recherche d’une question
* Aider à modérer le contenu Q&amp;R
* Identifier les meilleures réponses
* Déplacer des questions Q&amp;R d’une page vers une autre

Cette section de la documentation décrit :

* Ajout de la fonction Forum Q&amp;R à un site AEM
* Paramètres de configuration de la variable `QnA`component

## Ajout d’un forum Q&amp;R à une page {#adding-a-q-a-forum-to-a-page}

Pour ajouter une `QnA` sur une page en mode création, utilisez l’explorateur de composants pour accéder à `Communities / QnA` et faites-le glisser sur une page où le forum Q&amp;R doit apparaître.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](qna-essentials.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `QnA` apparaît :

![chlimage_1-280](assets/chlimage_1-280.png)

### Configuration de Q&amp;R {#configuring-qna}

Sélectionnez le `QnA` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Onglet Settings {#settings-tab}

Sous l’onglet **[!UICONTROL Paramètres]**, spécifiez les paramètres pour les sujets (questions) et les réponses :

* **[!UICONTROL Sujets par page]** Définit le nombre de questions/réponses affichées par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]** Si cette option est cochée, les sujets et les commentaires doivent être approuvés avant d’être visibles sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]** Si cette option est cochée, le forum est fermé et n’accepte pas de nouveaux commentaires ou questions. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Éditeur de texte enrichi]** Si cette option est cochée, les sujets et les commentaires peuvent être saisis avec une mise en forme. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, les membres ont le droit d’ajouter des libellés de balise à leur article (voir l’onglet **[!UICONTROL Champ de balise]**). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]** Si cette option est cochée, des fichiers joints peuvent être ajoutés à une question ou à un commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille de fichier maximale]**
Pertinent uniquement si 
`Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* **[!UICONTROL Types de fichiers autorisés]**
Pertinent uniquement si 
`Allow File Uploads` est cochée. Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être chargés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Taille max. du fichier image joint]**
À définir uniquement si l’option Autoriser les chargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser l’exécution]**
Si cette case est cochée, incluez la fonction suivante pour les publications de forum, ce qui permet aux membres d’être [notify](notifications.md) de nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Permettre la mise en page]**
Si cette case est cochée, les sujets de forum peuvent être placés en haut de la liste des sujets. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les abonnements aux emails]**
Si cette case est cochée, autorisez les membres à être informés des nouvelles publications par courrier électronique ([abonnement](subscriptions.md)). Nécessite `Allow Following` à vérifier et [email configuré](email.md). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les réponses]** Si cette option est cochée, les réponses aux commentaires sont publiées pour la question. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer les commentaires et sujets]** Si cette option est cochée, les membres ont le droit de supprimer les commentaires et les questions qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]** Si cette option est cochée, la fonction de vote est ajoutée à une question. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Déplacer la réponse sélectionnée vers le haut]** Si cette option est cochée, la première réponse qui s’affiche est la réponse sélectionnée. Cette option est cochée par défaut.

* **[!UICONTROL Badges d’affichage]**
Si cette case est cochée, affichez les droits gagnés et attribués. [badges](implementing-scoring.md) avec l&#39;entrée de blog d&#39;un membre. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le contenu proposé]**
si cette case est cochée, l’idée peut être identifiée comme [contenu proposé](featured.md). Cette option n’est pas cochée par défaut.

#### Onglet Modération d’utilisateur {#user-moderation-tab}

Sous , **[!UICONTROL Modération d’utilisateur]** , indiquez comment gérer les sujets publiés (questions) et les réponses (contenu généré par l’utilisateur). Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Refuser les réponses]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de refuser des réponses et, par conséquent, d’empêcher leur publication sur le forum Q&amp;R. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de fermer une question (un sujet) pour empêcher la publication d’autres modifications et réponses, puis de le rouvrir. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Déplacer les rubriques]**
Si cette case est cochée, les modérateurs côté publication peuvent déplacer les questions. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les publications]** Si cette option est cochée, les membres ont le droit de marquer les questions ou réponses d’autres membres comme étant inappropriées. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est cochée, les membres ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué une question ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué une question ou une réponse comme étant inappropriée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’une question ou une réponse doit être marquée par les membres avant que les modérateurs n’en soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’une question ou une réponse doit être marquée avant qu’il ne soit plus visible pour le public. Si la valeur est -1, la question ou la réponse marquée est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

#### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, les balises qui peuvent être appliquées, si l’option est activée dans l’onglet **[!UICONTROL Paramètres]**, sont limitées selon les espaces de noms sélectionnés.

* **[!UICONTROL Espaces de noms autorisés]**
Pertinent si 
`Allow Tagging` est coché sous **Paramètres** . Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (l’espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestions]** Entrez le nombre de balises à afficher comme suggestion destinée au membre qui publie sur le forum. Une valeur de 
`-1` signifie pas de limites. La valeur par défaut est 0.

#### Onglet Paramètres de tri {#sort-settings-tab}

Sous , **[!UICONTROL Paramètres de tri]** , indiquez comment les commentaires publiés sont triés lorsqu’ils sont affichés.

* **[!UICONTROL Trier par]**
Cochez toutes les sélections de tri autorisées : 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. La valeur par défaut est `Newest, Oldest, Last Updated`.

* **[!UICONTROL Définir comme valeur par défaut]**
Extrayez pour sélectionner l’une des options de tri cochées à afficher par défaut. La valeur par défaut est 
`Newest`.

* **[!UICONTROL Sélection des options d’heure pour le tri Analytics]**
Menu déroulant pour sélectionner l’un des 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. La valeur par défaut est `All`.

## Expérience des visiteurs {#site-visitor-experience}

### Identification des réponses {#identifying-answers}

Une réponse peut être indiquée comme réponse correcte ou utile à l’aide de la variable `Select Answer` bouton . Une fois qu&#39;une question est marquée comme ayant reçu une réponse, une autre réponse ne peut pas être sélectionnée tant que la première question n&#39;a pas été désélectionnée à l&#39;aide de la fonction `Unmark Chosen Answer`bouton .

Une fois sélectionnée comme réponse viable, elle peut être désélectionnée à l’aide de la variable `Unmark Chosen Answer` bouton .

Une fois qu&#39;une réponse est sélectionnée comme réponse viable, une indication que la question a été `Answered`s’affiche en regard de la rubrique de question sur la page Q&amp;R principale.

### Modérateurs et administrateurs {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut se charger d’activités de modération autorisées par la configuration du composant, peu importe qui a créé la question ou la réponse.

Il peut également identifier les réponses.

### Membres {#members}

Lorsque le visiteur est connecté, selon la configuration, il peut :

* Poser une nouvelle question
* Modifier ou supprimer les questions qu’ils ont créées
* Peut également marquer les questions ou réponses d’autres utilisateurs
* Peut identifier les réponses aux questions qu’ils ont créées

### Anonyme {#anonymous}

Les visiteurs non inscrits peuvent lire les questions et les réponses publiées et les traduire lorsque cela est possible. Toutefois, ils ne sont pas autorisés à ajouter de question ou de réponse, ni à marquer les publications d’autres membres.

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur la fonction Q&amp;R](qna-essentials.md) pour les développeurs.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).
