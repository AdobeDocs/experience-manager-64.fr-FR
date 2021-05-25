---
title: Fonctionnalité d’orientation
seo-title: Fonctionnalité d’orientation
description: Ajout et configuration de la fonction Idéation
seo-description: Ajout et configuration de la fonction Idéation
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 36%

---

# Fonction d’information {#ideation-feature}

## Présentation {#introduction}

La fonction d’idéation fournit une zone pour les visiteurs connectés du site (membres de la communauté) dans l’environnement de publication afin que :

* Créer des idées à partager avec la communauté
* Afficher et commenter les idées
* Suivre une idée
* Vote sur une idée

Cette section de la documentation décrit :

* Ajout de la fonction d’idéation à un site AEM
* Paramètres de configuration du composant Idéation

## Ajout d’une idée à une page {#adding-a-ideation-to-a-page}

Pour ajouter un composant `Ideation` à une page en mode création, utilisez l’explorateur de composants pour localiser `Communities / Ideation` et faites-le glisser sur une page où l’idée doit apparaître.

Pour plus d’informations, voir [Principes de base des composants des communautés](basics.md).

Lorsque les [bibliothèques côté client requises](ideation.md#essentials-for-client-side) sont incluses, voici comment le composant `Ideation`apparaîtra :

![chlimage_1-29](assets/chlimage_1-29.png)

## Configuration d’une idée {#configuring-an-ideation}

Sélectionnez le composant `Ideation` inséré pour y accéder et sélectionnez l’icône `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Onglet Settings {#settings-tab}

Sous l’onglet **[!UICONTROL Paramètres]**, spécifiez les paramètres des idées et des commentaires :

* **[!UICONTROL Titre de l’]**
idée Titre affiché pour l’idée. La valeur par défaut est 
`Ideation`.

* **[!UICONTROL Description de l’]**
idée Description à afficher sous forme de sous-titre de l’idée. La valeur par défaut n’est pas une description.

* **[!UICONTROL Sujets par]**
page Définit le nombre d’idées/de publications affichées par page. La valeur par défaut est 10.

* ****
ModéréSi cette option est cochée, les idées et les commentaires doivent être approuvés avant d’apparaître sur un site de publication. Cette option n’est pas cochée par défaut.

* ****
FerméSi cette option est cochée, le forum d’idéation est fermé aux idées et commentaires nouveaux. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Éditeur de texte enrichi]**
Si cette option est cochée, les idées et les commentaires peuvent être saisis avec une annotation. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, les membres ont le droit d’ajouter des libellés de balise à leur article (voir l’onglet **[!UICONTROL Champ de balise]**). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les]**
chargements de fichiers Si cette option est cochée, des fichiers joints peuvent être ajoutés à l’idée ou au commentaire. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille max. de fichier]**
Relevant uniquement si 
`Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* ****
Types de fichiers autorisés Paramètre à définir uniquement si 
`Allow File Uploads` est cochée. Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être chargés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Max Attach Image File]**
SizeRelevant uniquement si l’option Autoriser les chargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser les]**
réponsesSi cette option est cochée, les réponses aux commentaires sont publiées pour l’idée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer les commentaires et]**
sujetsSi cette option est cochée, les membres ont le droit de supprimer les commentaires et idées qu’ils ont publiés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser l’]**
action suivante Si cette option est cochée, la fonction suivante est ajoutée pour les publications d’idées, ce qui permet aux membres d’être  [](notifications.md) informés des nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les]**
abonnements par e-mailSi cette option est cochée, les membres ont la possibilité d’être informés des nouvelles publications par e-mail ([abonnement](subscriptions.md)). `Allow Following` doit être vérifié et [email configuré](email.md). Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le]**
vote Si cette option est cochée, le vote est autorisé sur les commentaires d’une idée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher les]**
badges : si cette option est cochée, les  [](implementing-scoring.md) badges gagnés et attribués sont affichés avec l’idée d’un membre. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Si l’option Autoriser la]**
conservation des en-têtes est cochée, l’idée peut être identifiée en tant que contenu [ ](featured.md)en vedette. Cette option n’est pas cochée par défaut.

### Onglet Modération d’utilisateur {#user-moderation-tab}

Sous l’onglet **[!UICONTROL Modération d’utilisateur]** , indiquez comment les idées et commentaires publiés (contenu généré par l’utilisateur) sont gérés. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Refuser les publications]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de refuser des articles et, par conséquent, d’empêcher leur publication sur le forum public. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les sujets]** Si cette option est cochée, les membres modérateurs autorisés ont le droit de fermer un sujet pour empêcher la publication d’autres modifications et de commentaires, puis de le rouvrir. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les publications]** Si cette option est cochée, les membres ont le droit de marquer les sujets ou commentaires d’autres membres comme étant inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est cochée, les membres ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est cochée, les membres ont le droit de préciser la raison pour laquelle ils ont marqué un sujet ou un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué par les membres avant que les modérateurs n’en soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Si la valeur est -1, le sujet ou le commentaire marqué est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, les balises qui peuvent être appliquées, si l’option est activée dans l’onglet **[!UICONTROL Paramètres]**, sont limitées selon les espaces de noms sélectionnés.

* **[!UICONTROL Espaces de]**
noms autorisés Paramètre à définir si 
`Allow Tagging` est coché sous l’onglet  **** Paramètres . Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (l’espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestions]** Entrez le nombre de balises à afficher comme suggestion destinée au membre qui publie sur le forum. Une valeur de 
**-** 1 signifie aucune limite. La valeur par défaut est 0.

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

## Expérience des visiteurs {#site-visitor-experience}

### Création d’une idée {#creating-idea}

Comme pour toutes les fonctionnalités de Communities, si elle n’est pas connectée, un visiteur du site ne peut lire que des idées et consulter d’autres opinions (par le biais de commentaires et de votes/commentaires).

Une fois connecté, un membre peut créer une nouvelle idée.

![chlimage_1-32](assets/chlimage_1-32.png)

Avant de soumettre l’idée, le membre peut enregistrer un brouillon.

En sélectionnant le bouton `Save as Draft`, un brouillon est enregistré.

![chlimage_1-33](assets/chlimage_1-33.png)

Lors de l’affichage de brouillons enregistrés dans l’onglet `My Drafts` , sélectionnez `Read More` pour revenir en mode d’édition :

![chlimage_1-34](assets/chlimage_1-34.png)

#### Fournir des commentaires {#providing-feedback}

Une fois l&#39;idée publiée, d&#39;autres membres peuvent se connecter, ouvrir l&#39;idée ( `Read More`) et aimer l&#39;idée, ajoutant ainsi au nombre de votes, et faire des commentaires.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informations supplémentaires {#additional-information}

Pour plus d’informations, reportez-vous à la page [Notions fondamentales sur les idées](ideation.md) pour les développeurs.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).
