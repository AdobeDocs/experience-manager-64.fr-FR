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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 2%

---

# Fonction Forum Q&amp;R {#q-a-forum-feature}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

La fonction de forum Q&amp;R (questions et réponses) offre aux membres de la communauté un espace où poser leurs questions et y répondre :

* Créer de nouvelles questions
* Images intégrées (avec prise en charge du glisser-déposer)
* Afficher et répondre aux questions
* Recherche d’une question
* Aider à modérer le contenu Q&amp;R
* Identifier les meilleures réponses
* Déplacer des questions Q&amp;R d’une page vers une autre

Cette section de la documentation décrit

* Ajout de la fonction Forum Q&amp;R à un site AEM
* Paramètres de configuration de la variable `QnA`component

## Ajout d’un forum de questions-réponses à une page {#adding-a-q-a-forum-to-a-page}

Pour ajouter une `QnA` sur une page en mode création, utilisez l’explorateur de composants pour accéder à `Communities / QnA` et faites-le glisser sur une page où le forum Q&amp;R doit apparaître.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](qna-essentials.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `QnA` apparaît :

![chlimage_1-280](assets/chlimage_1-280.png)

### Configuration de Q&amp;R {#configuring-qna}

Sélectionnez le `QnA` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Onglet Paramètres {#settings-tab}

Sous , **[!UICONTROL Paramètres]** , définissez les paramètres des sujets (questions) et réponses (réponses) :

* **[!UICONTROL Sujets par page]**
Définit le nombre de questions/publications affichées par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]**
Si cette case est cochée, la publication des sujets et des commentaires doit être approuvée avant d’apparaître sur un site de publication. La case par défaut est décochée.

* **[!UICONTROL Fermé]**
Si cette case est cochée, le forum est fermé aux nouvelles questions et commentaires. La case par défaut est décochée.

* **[!UICONTROL Éditeur de texte enrichi]**
Si cette case est cochée, les sujets et les commentaires peuvent être saisis avec une annotation. La case par défaut est décochée.

* **[!UICONTROL Autoriser le balisage]**
Si cette case est cochée, les membres ont le droit d’ajouter des libellés de balise à leur publication (voir **[!UICONTROL Champ de balise]** ). La case par défaut est décochée.

* **[!UICONTROL Autoriser les chargements de fichiers]**
Si cette option est cochée, des pièces jointes peuvent être ajoutées à la question ou au commentaire. La case par défaut est décochée.

* **[!UICONTROL Taille de fichier maximale]**
Pertinent uniquement si 
`Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* **[!UICONTROL Types de fichiers autorisés]**
Pertinent uniquement si 
`Allow File Uploads` est cochée. Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être chargés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Taille max. du fichier image joint]**
À définir uniquement si l’option Autoriser les chargements de fichiers est cochée. Nombre maximal d’octets qu’un fichier image chargé peut contenir. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser l’exécution]**
Si cette case est cochée, incluez la fonction suivante pour les publications de forum, ce qui permet aux membres d’être [notify](notifications.md) de nouvelles publications. La case par défaut est décochée.

* **[!UICONTROL Permettre la mise en page]**
Si cette case est cochée, les sujets de forum peuvent être placés en haut de la liste des sujets. La case par défaut est décochée.

* **[!UICONTROL Autoriser les abonnements aux emails]**
Si cette case est cochée, autorisez les membres à être informés des nouvelles publications par courrier électronique ([abonnement](subscriptions.md)). Nécessite `Allow Following` à vérifier et [email configuré](email.md). La case par défaut est décochée.

* **[!UICONTROL Autoriser les réponses]**
Si cette case est cochée, les réponses aux commentaires sont publiées pour la question. La case par défaut est décochée.

* **[!UICONTROL Autorisation des utilisateurs à supprimer des commentaires et des sujets]**
Si cette case est cochée, autorisez les membres à supprimer les commentaires et questions qu’ils ont publiés. La case par défaut est décochée.

* **[!UICONTROL Autoriser le vote]**
Si cette option est cochée, la fonction de vote est ajoutée à une question. La case par défaut est décochée.

* **[!UICONTROL Déplacer la réponse sélectionnée vers le haut]**
Si cette case est cochée, la première réponse affichée est une réponse sélectionnée. La valeur par défaut est cochée.

* **[!UICONTROL Badges d’affichage]**
Si cette case est cochée, affichez les droits gagnés et attribués. [badges](implementing-scoring.md) avec l&#39;entrée de blog d&#39;un membre. La case par défaut est décochée.

* **[!UICONTROL Autoriser le contenu proposé]**
si cette case est cochée, l’idée peut être identifiée comme [contenu proposé](featured.md). La case par défaut est décochée.

#### Onglet Modération d’utilisateur {#user-moderation-tab}

Sous , **[!UICONTROL Modération d’utilisateur]** , indiquez comment gérer les sujets publiés (questions) et les réponses (contenu généré par l’utilisateur). Pour plus d’informations, voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

* **[!UICONTROL Refuser les réponses]**
Si cette case est cochée, les modérateurs membres approuvés seront autorisés à refuser les réponses publiées et à empêcher que la réponse ne s’affiche sur le forum Q&amp;R public. La case par défaut est décochée.

* **[!UICONTROL Fermer/rouvrir les rubriques]**
Si cette case est cochée, les membres modérateurs autorisés peuvent fermer une question (rubrique) pour apporter d’autres modifications et réponses, et peuvent également rouvrir une question. La case par défaut est décochée.

* **[!UICONTROL Déplacer les rubriques]**
Si cette case est cochée, les modérateurs côté publication peuvent déplacer les questions. La case par défaut est décochée.

* **[!UICONTROL Marquer les publications]**
Si cette option est cochée, les membres ont le droit de signaler les questions ou réponses des autres comme étant inappropriées. La case par défaut est décochée.

* **[!UICONTROL Marquer la liste de motifs]**
Si cette case est cochée, les membres ont le droit de choisir dans une liste déroulante la raison pour laquelle ils ont marqué une question ou une réponse comme étant inappropriée. La case par défaut est décochée.

* **[!UICONTROL Motif de l’indicateur personnalisé]**
Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué une question ou une réponse comme étant inappropriée. La case par défaut est décochée.

* **[!UICONTROL Seuil de modération]**
Saisissez le nombre de fois qu’une question ou une réponse doit être marquée par les membres avant que les modérateurs ne soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]**
Saisissez le nombre de fois qu&#39;une question ou une réponse doit être marquée avant qu&#39;elle ne soit plus visible pour le public. S’il est défini sur -1, la question ou la réponse marquée n’est jamais masquée de la vue du public. Sinon, ce nombre doit être supérieur ou égal au seuil de modération. La valeur par défaut est 5.

#### Onglet Champ de balise {#tag-field-tab}

Sous , **[!UICONTROL Champ de balise]** , les balises qui peuvent être appliquées, le cas échéant, sous l’onglet **[!UICONTROL Paramètres]** sont limités en fonction des espaces de noms sélectionnés.

* **[!UICONTROL Espaces de noms autorisés]**
Pertinent si 
`Allow Tagging` est coché sous **Paramètres** . Les balises qui peuvent être appliquées sont limitées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (l’espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestion]**
Saisissez le nombre de balises à afficher comme suggestion au membre qui publie sur le forum. Une valeur de 
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

## Expérience du visiteur du site {#site-visitor-experience}

### Identification des réponses {#identifying-answers}

Une réponse peut être indiquée comme réponse correcte ou utile à l’aide de la variable `Select Answer` bouton . Une fois qu&#39;une question est marquée comme ayant reçu une réponse, une autre réponse ne peut pas être sélectionnée tant que la première question n&#39;a pas été désélectionnée à l&#39;aide de la fonction `Unmark Chosen Answer`bouton .

Une fois sélectionnée comme réponse viable, elle peut être désélectionnée à l’aide de la variable `Unmark Chosen Answer` bouton .

Une fois qu&#39;une réponse est sélectionnée comme réponse viable, une indication que la question a été `Answered`s’affiche en regard de la rubrique de question sur la page Q&amp;R principale.

### Modérateurs et administrateurs {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut effectuer les tâches de modération autorisées par la configuration du composant, indépendamment de la personne qui a créé la question ou la réponse.

Ils peuvent aussi identifier les réponses.

### Membres {#members}

Lorsque le visiteur du site est connecté, selon la configuration, il peut :

* Poser une nouvelle question
* Modifier ou supprimer les questions qu’ils ont créées
* Peut également marquer les questions ou réponses d’autres utilisateurs
* Peut identifier les réponses aux questions qu’ils ont créées

### Anonyme {#anonymous}

Les visiteurs qui ne sont pas connectés peuvent uniquement lire les questions et réponses publiées, les traduire s’ils sont pris en charge, mais ne peuvent ni ajouter de question, ni répondre, ni marquer les publications d’autres visiteurs.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur la qualité de vie](qna-essentials.md) pour les développeurs.

Pour la modération des sujets et des commentaires publiés, voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser des sujets et des commentaires publiés, voir [Balisage du contenu généré par l’utilisateur](tag-ugc.md).
