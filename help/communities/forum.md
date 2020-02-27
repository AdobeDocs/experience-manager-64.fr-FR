---
title: Fonction Forum
seo-title: Fonction Forum
description: Comment ajouter et configurer la fonction du forum
seo-description: Comment ajouter et configurer la fonction du forum
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2

---


# Fonction Forum {#forum-feature}

## Présentation {#introduction}

La fonction Forum offre un espace aux visiteurs connectés (membres de la communauté) dans l’environnement de publication pour leur permettre de :

* Création de nouvelles rubriques
* Afficher et répondre aux rubriques
* Suivre une rubrique
* Rechercher un forum
* Aider à modérer le contenu du forum
* Déplacement des rubriques de forum d’une page vers une autre

Cette section de la documentation décrit :

* Ajout de la fonctionnalité de forum à un site AEM
* Configuration settings for the `Forum`component

## Ajout d’un forum à une page {#adding-a-forum-to-a-page}

To add a `Forum` component to a page in author mode, use the component browser to locate

* `Communities / Forum`

Et faites-le glisser sur une page où le forum devrait apparaître.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](essentials-forum.md#essentials-for-client-side) are included, this is how the `Forum`component will appear:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configuration d’un forum {#configuring-a-forum}

Select the placed `Forum` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Onglet Settings {#settings-tab}

Sous l’onglet **[!UICONTROL Paramètres]**, spécifiez les paramètres des sujets et des réponses :

* **[!UICONTROL Sujets par page]** Définit le nombre de sujets/articles affichés par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]** Si cette option est cochée, les sujets et les commentaires doivent être approuvés avant d’être visibles sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]** Si cette option est cochée, le forum est fermé et n’accepte aucun nouveau sujet ou commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Éditeur de texte enrichi]** Si cette option est cochée, les sujets et les commentaires peuvent être saisis avec une mise en forme. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, les membres ont le droit d’ajouter des libellés de balise à leur article (voir l’onglet **[!UICONTROL Champ de balise]**). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]** Si cette option est cochée, des fichiers joints peuvent être ajoutés à un sujet ou à un commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le suivi]** Si coché, incluez la fonctionnalité suivante pour les publications de forum, ce qui permet aux membres d’être [informés](notifications.md) des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Permettre l’épinglage]** Si cette option est cochée, les rubriques du forum peuvent être épinglées en haut de la liste des rubriques. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Si cette option est cochée, l’idée peut être identifiée comme contenu]**[](featured.md)phare. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les abonnements]** par courrier électronique Si cette option est cochée, autorisez les membres à être avertis des nouvelles publications par courrier électronique ([abonnement](subscriptions.md)). Requiert `Allow Following` la vérification et la configuration [du](email.md)courrier électronique. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille]** de fichier maximale pertinente uniquement si `Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 1 048 57 600 (10 Mo).

* **[!UICONTROL Types]** de fichiers autorisés pertinents uniquement si `Allow File Uploads` l’option est cochée. Liste d’extensions de fichiers séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichier sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être téléchargés. Par défaut, aucun type de fichier n’est spécifié, de sorte que tous les types de fichier soient autorisés.

* **[!UICONTROL Taille]** max. du fichier image joint, applicable uniquement si l’option Autoriser les téléchargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser les réponses à thème]** Si cette option est cochée, les réponses aux commentaires sont publiées pour le sujet. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer les commentaires et sujets]** Si cette option est cochée, les membres ont le droit de supprimer les commentaires et les sujets qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]** Si cette option est cochée, la fonction de vote est ajoutée à un sujet. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher le fil d’Ariane]** Si cette option est cochée, le fil d’Ariane s’affiche dans les pages de sujet. Cette option est cochée par défaut.

* **[!UICONTROL Afficher les badges]** Si coché, afficher les [badges](implementing-scoring.md) gagnés et attribués avec l&#39;entrée de blog d&#39;un membre. Cette option n’est pas cochée par défaut.

>[!NOTE]
>
>Il peut s’avérer nécessaire de vérifier `AllowThreaded Replies` et `Allow users to Delete Comments and Topics` d’activer les commentaires sur un sujet.

### Onglet Modération utilisateur {#user-moderation-tab}

Under the **[!UICONTROL User Moderation]** tab, specify how the posted topics and replies (user generated content) are managed. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Refuser les publications]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de refuser des articles et, par conséquent, d’empêcher leur publication sur le forum public. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de fermer un sujet pour empêcher la publication d’autres modifications et de commentaires, puis de le rouvrir. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Déplacer des rubriques]** Si cette option est cochée, autorisez les modérateurs côté publication à déplacer des rubriques. Cette option est cochée par défaut.

* **[!UICONTROL Marquer les publications]** Si cette option est cochée, les membres ont le droit de marquer les sujets ou commentaires d’autres membres comme étant inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est cochée, les membres ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué par les membres avant que les modérateurs n’en soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Si la valeur est -1, le sujet ou le commentaire marqué est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, les balises qui peuvent être appliquées, si l’option est activée dans l’onglet **[!UICONTROL Paramètres]**, sont limitées selon les espaces de noms sélectionnés.

* **[!UICONTROL Espaces de noms]** autorisés pertinents si `Allow Tagging` l’option est cochée sous l’onglet **[!UICONTROL Paramètres]** . Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestions]** Entrez le nombre de balises à afficher comme suggestion destinée au membre qui publie sur le forum. Default is **-** 1 (no limits).

### Onglet Traduction {#translation-tab}

Sous l’onglet **[!UICONTROL Traduction]**, si la traduction est activée pour le site de la communauté, elle peut être définie de sorte à traduire le sujet entier ou certaines publications en particulier.

* **[!UICONTROL Tout traduire]** Si cette option est cochée, le fil d’Ariane du forum est traduit dans la langue par défaut de l’utilisateur. Cette option n’est pas cochée par défaut.

### Onglet Paramètres de tri {#sort-settings-tab}

Sous l’onglet Paramètres **[!UICONTROL de]** tri, spécifiez le mode de tri des commentaires publiés lorsqu’ils sont affichés.

* **[!UICONTROL Trier par]** Vérifier toutes les sélections de tri autorisées : `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. La valeur par défaut est `Newest, Oldest, Last Updated`.

* **[!UICONTROL Définissez cette option comme valeur par défaut]** Tirez vers le bas pour sélectionner l’une des options de tri cochées à afficher comme valeur par défaut. La valeur par défaut est `Newest`.

* **[!UICONTROL Sélectionnez Options de temps pour le tri]** Analytics. Décompressez pour sélectionner l’une des options `All, Last 24 Hours, Last 7 Days, Last 30 Days`. La valeur par défaut est `All`.

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur la fonction Forum](essentials-forum.md) pour les développeurs.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).

Pour des informations sur la traduction des sujets et des commentaires, voir [Traduction de contenu généré par les utilisateurs](translate-ugc.md).
