---
title: Fonction Forum
seo-title: Fonction Forum
description: Ajout et configuration de la fonction de forum
seo-description: Ajout et configuration de la fonction de forum
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 58%

---

# Fonction Forum {#forum-feature}

## Présentation {#introduction}

La fonction Forum offre un espace aux visiteurs connectés (membres de la communauté) dans l’environnement de publication pour leur permettre de :

* Création de rubriques
* Affichage des rubriques et réponse
* Suivre une rubrique
* Recherche d’un forum
* Aider à modérer le contenu du forum
* Déplacement des sujets de forum d’une page vers une autre

Cette section de la documentation décrit :

* Ajout de la fonction Forum à un site AEM
* Paramètres de configuration du composant `Forum`

## Ajout d’un forum à une page {#adding-a-forum-to-a-page}

Pour ajouter un composant `Forum` à une page en mode création, utilisez l’explorateur de composants pour accéder à :

* `Communities / Forum`

Et faites-le glisser sur la page où le forum doit apparaître.

Pour plus d’informations, voir [Principes de base des composants des communautés](basics.md).

Lorsque les [bibliothèques côté client requises](essentials-forum.md#essentials-for-client-side) sont incluses, voici comment le composant `Forum`apparaîtra :

![chlimage_1-60](assets/chlimage_1-60.png)

## Configuration d’un forum {#configuring-a-forum}

Sélectionnez le composant `Forum` inséré pour y accéder et sélectionnez l’icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Onglet Settings {#settings-tab}

Sous l’onglet **[!UICONTROL Paramètres]**, spécifiez les paramètres des sujets et des réponses :

* **[!UICONTROL Sujets par page]** Définit le nombre de sujets/articles affichés par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]** Si cette option est cochée, les sujets et les commentaires doivent être approuvés avant d’être visibles sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]** Si cette option est cochée, le forum est fermé et n’accepte aucun nouveau sujet ou commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Éditeur de texte enrichi]** Si cette option est cochée, les sujets et les commentaires peuvent être saisis avec une mise en forme. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, les membres ont le droit d’ajouter des libellés de balise à leur article (voir l’onglet **[!UICONTROL Champ de balise]**). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les chargements de fichiers]** Si cette option est cochée, des fichiers joints peuvent être ajoutés à un sujet ou à un commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser l’]**
action suivante Si cette option est cochée, la fonction suivante est ajoutée aux publications de forum, ce qui permet aux membres d’être  [](notifications.md) informés des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser l’]**
épinglage Si cette option est cochée, les rubriques des forums peuvent être collées en haut de la liste des rubriques. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Si l’option Autoriser la]**
conservation des en-têtes est cochée, l’idée peut être identifiée en tant que contenu [ ](featured.md)en vedette. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les]**
abonnements par e-mailSi cette option est cochée, les membres ont la possibilité d’être informés des nouvelles publications par e-mail ([abonnement](subscriptions.md)). `Allow Following` doit être vérifié et [email configuré](email.md). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille max. de fichier]**
Relevant uniquement si 
`Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* ****
Types de fichiers autorisés Paramètre à définir uniquement si 
`Allow File Uploads` est cochée. Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être chargés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Max Attach Image File]**
SizeRelevant uniquement si l’option Autoriser les chargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser les réponses à thème]** Si cette option est cochée, les réponses aux commentaires sont publiées pour le sujet. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer les commentaires et sujets]** Si cette option est cochée, les membres ont le droit de supprimer les commentaires et les sujets qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]** Si cette option est cochée, la fonction de vote est ajoutée à un sujet. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher le fil d’Ariane]** Si cette option est cochée, le fil d’Ariane s’affiche dans les pages de sujet. Cette option est cochée par défaut.

* **[!UICONTROL Afficher les]**
badges : si cette option est cochée, les  [](implementing-scoring.md) badges gagnés et attribués sont affichés avec l’entrée de blog d’un membre. Cette option n’est pas cochée par défaut.

>[!NOTE]
>
>Il peut être nécessaire de vérifier `AllowThreaded Replies` et `Allow users to Delete Comments and Topics` pour activer les commentaires sur un sujet.

### Onglet Modération d’utilisateur {#user-moderation-tab}

Sous l’onglet **[!UICONTROL Modération d’utilisateur]** , indiquez comment les sujets et réponses publiés (contenu généré par l’utilisateur) sont gérés. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Refuser les publications]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de refuser des articles et, par conséquent, d’empêcher leur publication sur le forum public. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de fermer un sujet pour empêcher la publication d’autres modifications et de commentaires, puis de le rouvrir. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Déplacer les]**
rubriques Si cette option est cochée, les modérateurs côté publication peuvent déplacer les rubriques. Cette option est cochée par défaut.

* **[!UICONTROL Marquer les publications]** Si cette option est cochée, les membres ont le droit de marquer les sujets ou commentaires d’autres membres comme étant inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est cochée, les membres ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué par les membres avant que les modérateurs n’en soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Si la valeur est -1, le sujet ou le commentaire marqué est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, les balises qui peuvent être appliquées, si l’option est activée dans l’onglet **[!UICONTROL Paramètres]**, sont limitées selon les espaces de noms sélectionnés.

* **[!UICONTROL Espaces de]**
noms autorisésRelevant si  `Allow Tagging` est coché sous l’onglet  **** Paramètres. Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (l’espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestions]** Entrez le nombre de balises à afficher comme suggestion destinée au membre qui publie sur le forum. La valeur par défaut est 
**-** 1 (aucune limite).

### Onglet Traduction {#translation-tab}

Sous l’onglet **[!UICONTROL Traduction]**, si la traduction est activée pour le site de la communauté, elle peut être définie de sorte à traduire le sujet entier ou certaines publications en particulier.

* **[!UICONTROL Tout traduire]** Si cette option est cochée, le fil d’Ariane du forum est traduit dans la langue par défaut de l’utilisateur. Cette option n’est pas cochée par défaut.

### Onglet Paramètres de tri {#sort-settings-tab}

Sous l’onglet **[!UICONTROL Paramètres de tri]**, indiquez comment les commentaires publiés sont triés lorsqu’ils sont affichés.

* **[!UICONTROL Trier]**
par coche toutes les sélections de tri autorisées : 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. La valeur par défaut est `Newest, Oldest, Last Updated`.

* **[!UICONTROL Définissez comme]**
DefaultPull pour sélectionner l’une des options de tri cochées à afficher comme valeur par défaut. La valeur par défaut est 
`Newest`.

* **[!UICONTROL Sélectionnez Options de temps pour Analytics]**
TriPull afin de sélectionner l’une des options suivantes : 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. La valeur par défaut est `All`.

## Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur la fonction Forum](essentials-forum.md) pour les développeurs.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).

Pour des informations sur la traduction des sujets et des commentaires, voir [Traduction de contenu généré par les utilisateurs](translate-ugc.md).
