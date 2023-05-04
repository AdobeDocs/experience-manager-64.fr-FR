---
title: Fonctionnalité du forum
seo-title: Forum Feature
description: Ajout et configuration de la fonction de forum
seo-description: How to add and configure the forum feature
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 2%

---

# Fonctionnalité du forum {#forum-feature}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

La fonction de forum fournit une zone pour les visiteurs connectés du site (membres de la communauté) dans l’environnement de publication afin que :

* Création de rubriques
* Affichage des rubriques et réponse
* Suivre une rubrique
* Recherche d’un forum
* Aider à modérer le contenu du forum
* Déplacement des sujets de forum d’une page vers une autre

Cette section de la documentation décrit

* Ajout de la fonction Forum à un site AEM
* Paramètres de configuration de la variable `Forum`component

## Ajout d’un forum à une page {#adding-a-forum-to-a-page}

Pour ajouter une `Forum` sur une page en mode création, utilisez l’explorateur de composants pour accéder à

* `Communities / Forum`

Et faites-le glisser sur la page où le forum doit apparaître.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-forum.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Forum`apparaît :

![chlimage_1-60](assets/chlimage_1-60.png)

## Configuration d’un forum {#configuring-a-forum}

Sélectionnez le `Forum` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Onglet Paramètres {#settings-tab}

Sous , **[!UICONTROL Paramètres]** , spécifiez les paramètres des sujets et réponses :

* **[!UICONTROL Sujets par page]**
Définit le nombre de rubriques/publications affichées par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]**
Si cette case est cochée, la publication des sujets et des commentaires doit être approuvée avant d’apparaître sur un site de publication. La case par défaut est décochée.

* **[!UICONTROL Fermé]**
Si cette case est cochée, le forum est fermé pour de nouveaux sujets et commentaires. La case par défaut est décochée.

* **[!UICONTROL Éditeur de texte enrichi]**
Si cette case est cochée, les sujets et les commentaires peuvent être saisis avec une annotation. La case par défaut est décochée.

* **[!UICONTROL Autoriser le balisage]**
Si cette case est cochée, les membres ont le droit d’ajouter des libellés de balise à leur publication (voir **[!UICONTROL Champ de balise]** ). La case par défaut est décochée.

* **[!UICONTROL Autoriser les chargements de fichiers]**
Si cette case est cochée, vous pouvez ajouter des pièces jointes à la rubrique ou au commentaire. La case par défaut est décochée.

* **[!UICONTROL Autoriser l’exécution]**
Si cette case est cochée, incluez la fonction suivante pour les publications de forum, ce qui permet aux membres d’être [notify](notifications.md) de nouvelles publications. La case par défaut est décochée.

* **[!UICONTROL Permettre la mise en page]**
Si cette case est cochée, les sujets de forum peuvent être placés en haut de la liste des sujets. La case par défaut est décochée.

* **[!UICONTROL Autoriser le contenu proposé]**
si cette case est cochée, l’idée peut être identifiée comme [contenu proposé](featured.md). La case par défaut est décochée.

* **[!UICONTROL Autoriser les abonnements aux emails]**
Si cette case est cochée, autorisez les membres à être informés des nouvelles publications par courrier électronique ([abonnement](subscriptions.md)). Nécessite `Allow Following` à vérifier et [email configuré](email.md). La case par défaut est décochée.

* **[!UICONTROL Taille de fichier maximale]**
Pertinent uniquement si 
`Allow File Uploads` est cochée. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 104857600 (10 Mo).

* **[!UICONTROL Types de fichiers autorisés]**
Pertinent uniquement si 
`Allow File Uploads` est cochée. Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être chargés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Taille max. du fichier image joint]**
À définir uniquement si l’option Autoriser les chargements de fichiers est cochée. Nombre maximal d’octets qu’un fichier image chargé peut contenir. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Autoriser les réponses à threads]**
Si cette case est cochée, les réponses aux commentaires sont publiées sur le sujet. La case par défaut est décochée.

* **[!UICONTROL Autorisation des utilisateurs à supprimer des commentaires et des sujets]**
Si cette case est cochée, autorisez les membres à supprimer les commentaires et les sujets qu’ils ont publiés. La case par défaut est décochée.

* **[!UICONTROL Autoriser le vote]**
Si cette case est cochée, la fonction de vote est ajoutée à un sujet. La case par défaut est décochée.

* **[!UICONTROL Afficher le chemin de navigation]**
Si cette case est cochée, les chemins de navigation s’affichent sur les pages de rubrique. La valeur par défaut est cochée.

* **[!UICONTROL Badges d’affichage]**
Si cette case est cochée, affichez les droits gagnés et attribués. [badges](implementing-scoring.md) avec l&#39;entrée de blog d&#39;un membre. La case par défaut est décochée.

>[!NOTE]
>
>Il peut être nécessaire de vérifier les deux `AllowThreaded Replies` et `Allow users to Delete Comments and Topics` pour activer les commentaires sur un sujet.

### Onglet Modération d’utilisateur {#user-moderation-tab}

Sous , **[!UICONTROL Modération d’utilisateur]** , indiquez comment les sujets et réponses publiés (contenu généré par l’utilisateur) sont gérés. Pour plus d’informations, voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

* **[!UICONTROL Refuser des publications]**
Si cette case est cochée, les modérateurs membres approuvés sont autorisés à refuser des publications et à empêcher que la publication ne s’affiche sur le forum public. La case par défaut est décochée.

* **[!UICONTROL Fermer/rouvrir les rubriques]**
Si cette case est cochée, les membres modérateurs autorisés peuvent fermer une rubrique pour ajouter d’autres modifications et commentaires et rouvrir une rubrique. La case par défaut est décochée.

* **[!UICONTROL Déplacer les rubriques]**
Si cette case est cochée, les modérateurs côté publication peuvent déplacer des rubriques. La valeur par défaut est cochée.

* **[!UICONTROL Marquer les publications]**
Si cette case est cochée, les membres ont le droit de marquer les sujets ou commentaires d’autres personnes comme étant inappropriés. La case par défaut est décochée.

* **[!UICONTROL Marquer la liste de motifs]**
Si cette case est cochée, les membres ont le droit de choisir dans une liste déroulante la raison pour laquelle ils ont marqué un sujet ou un commentaire comme étant inapproprié. La case par défaut est décochée.

* **[!UICONTROL Motif de l’indicateur personnalisé]**
Si cette case est cochée, autorisez les membres à indiquer leur propre motif de signalement d’un sujet ou d’un commentaire comme étant inapproprié. La case par défaut est décochée.

* **[!UICONTROL Seuil de modération]**
Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué par les membres avant que les modérateurs ne soient informés. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]**
Saisissez le nombre de fois qu’un sujet ou un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. S’il est défini sur -1, le sujet ou le commentaire marqué n’est jamais masqué à la vue du public. Sinon, ce nombre doit être supérieur ou égal au seuil de modération. La valeur par défaut est 5.

### Onglet Champ de balise {#tag-field-tab}

Sous , **[!UICONTROL Champ de balise]** , les balises qui peuvent être appliquées, le cas échéant, sous l’onglet **[!UICONTROL Paramètres]** sont limités en fonction des espaces de noms sélectionnés.

* **[!UICONTROL Espaces de noms autorisés]**
Pertinent si `Allow Tagging` est coché sous **[!UICONTROL Paramètres]** . Les balises qui peuvent être appliquées sont limitées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (l’espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestion]**
Saisissez le nombre de balises à afficher comme suggestion au membre qui publie sur le forum. La valeur par défaut est 
**-** 1 (aucune limite).

### Onglet Traduction {#translation-tab}

Sous , **[!UICONTROL Traduction]** , si la traduction est activée pour le site de la communauté, elle peut être définie pour traduire l’intégralité de la rubrique ou les publications sélectionnées.

* **[!UICONTROL Tout traduire]**
Si cette case est cochée, le fil du forum est traduit dans la langue préférée de l’utilisateur. La case par défaut est décochée.

### Onglet Paramètres de tri {#sort-settings-tab}

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

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur le forum](essentials-forum.md) pour les développeurs.

Pour la modération des sujets et des commentaires publiés, voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser des sujets et des commentaires publiés, voir [Balisage du contenu généré par l’utilisateur](tag-ugc.md).

Pour la traduction des sujets et des commentaires publiés, voir [Traduction de contenu généré par l’utilisateur](translate-ugc.md).
