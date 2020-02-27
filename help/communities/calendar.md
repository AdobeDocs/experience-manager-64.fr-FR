---
title: Fonction Calendrier
seo-title: Fonction Calendrier
description: Fournit des informations sur les événements de la communauté dans un format de calendrier
seo-description: Fournit des informations sur les événements de la communauté dans un format de calendrier
uuid: 6f1f327f-bf4b-4357-b8fd-4bec74016921
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 8b8e74c5-8b65-4117-9ef0-da9d9e47191f
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Fonction Calendrier {#calendar-feature}

## Présentation {#introduction}

La fonction Calendrier offre des informations relatives aux événements de la communauté dans un calendrier. Sont concernés tous les visiteurs ou uniquement ceux qui sont inscrits (membres de la communauté). Tous les membres autorisés peuvent ajouter des événements.

Cette section de la documentation décrit : :

* Ajout de la fonctionnalité de calendrier à un site AEM
* Configuration settings for `Calendar`components

## Ajout d’un calendrier à une page {#adding-a-calendar-to-a-page}

To add a `Calendar` component to a page in author mode, use the component browser to locate

* `Communities / Calendar`

et faites glisser le composant sur une page, par exemple à un endroit relatif à la fonction, pour permettre aux utilisateurs de le consulter.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](calendar-basics-for-developers.md#essentials-for-client-side) are included, this is how the `Calendar` component will appear.

![chlimage_1-112](assets/chlimage_1-112.png)

### Configuration du calendrier {#configuring-calendar}

Select the placed `Calendar`component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-113](assets/chlimage_1-113.png) ![chlimage_1-114](assets/chlimage_1-114.png)

#### Onglet Settings {#settings-tab}

Under the **[!UICONTROL Settings]** tab, specify whether or not to allow tags to be applied to calendar entries.

* **[!UICONTROL Événements par page]**

   Définit le nombre d’événements affichés par page. La valeur par défaut est 10.

* **[!UICONTROL Modéré]**

   Si cette option est cochée, la publication des événements de calendrier et des commentaires doit être approuvée avant qu’ils n’apparaissent sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermé]**

   Si cette option est cochée, le calendrier est fermé aux nouvelles entrées d’événement et aux nouveaux commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Éditeur de texte enrichi]**

   Si cette option est cochée, les événements de calendrier et les commentaires peuvent être saisis avec une annotation. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le balisage]**

   If checked, allow members to add tag labels to the events they post (see **Tag field** tab). Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les transferts de fichiers]**

   Si cette option est cochée, autorisez l’ajout de pièces jointes à un événement de calendrier ou à un commentaire. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser abonnement]**

   Si cette option est cochée, permettez aux membres de suivre les événements publiés dans le calendrier. Cette option est cochée par défaut.

* **[!UICONTROL Taille maximale du fichier]**

   N’est pertinent que si `Allow File Uploads` est coché. Ce champ limite la taille (en octets) d’un fichier chargé. La valeur par défaut est 1 048 57 600 (10 Mo).

* **[!UICONTROL Types de fichier autorisés]**

   N’est pertinent que si `Allow File Uploads` est coché. Liste d’extensions de fichiers séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichier sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés à être téléchargés. Par défaut, aucun type de fichier n’est spécifié, de sorte que tous les types de fichier soient autorisés.

* **[!UICONTROL Taille max. du fichier image joint]**

   Applicable uniquement si l’option Autoriser les téléchargements de fichiers est cochée. Taille maximale en octets pour un fichier image chargé. La valeur par défaut est 2097152 (2 Mo).

* **[!UICONTROL Types autorisés d’image de couverture]**

   Liste séparée par des virgules d’extensions de fichier image avec le séparateur &quot;point&quot;. La valeur par défaut est `.jpg,.jpeg,.png,.gif,.bmp`.

* **[!UICONTROL Autoriser les réponses à thème]**

   Si cette option est cochée, autorisez les réponses aux commentaires publiés sur l’événement de calendrier. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les utilisateurs à supprimer les commentaires et événements]**

   Si cette option est cochée, autorisez les membres à supprimer les commentaires et les événements de calendrier qu’ils ont publiés. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le vote]**

   Si cette option est cochée, incluez la fonction de vote avec un événement de calendrier. Cette option est cochée par défaut.

* **[!UICONTROL Afficher le fil d’Ariane]**

   Afficher le fil d’Ariane sur la page des événements. Cette option est cochée par défaut.

* **[!UICONTROL Filtre de plage de dates]**

   Définit le nombre de jours ajoutés à la date actuelle afin de calculer la valeur &quot;À&quot; du filtre de page de liste des événements de calendrier. Le nombre par défaut est 30.

* **[!UICONTROL Autoriser le contenu proposé]**

   Si cette option est cochée, l’idée peut être identifiée comme contenu [](featured.md)incitatif. Cette option n’est pas cochée par défaut.

Under the **[!UICONTROL User Moderation]** tab, specify how the posted topics and replies (user generated content) are managed. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

#### Onglet Modération utilisateur {#user-moderation-tab}

* **[!UICONTROL Refuser les publications]**

   Si cette option est cochée, les modérateurs membres de confiance seront autorisés à refuser les publications et à empêcher leur publication de s’afficher sur le forum public. Cette option est cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les événements]**

   Si cette option est cochée, les modérateurs de membres de confiance peuvent fermer un événement pour apporter d’autres modifications et commentaires et peuvent également rouvrir un événement. Cette option est cochée par défaut.

* **[!UICONTROL Marquer les publications]**

   Si cette option est cochée, autorisez les membres à signaler les événements ou commentaires d’autres personnes comme étant inappropriés. Cette option est cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]**

   Si cette option est cochée, permettez aux membres de choisir, dans une liste déroulante, la raison pour laquelle ils signalent un événement ou un commentaire comme inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]**

   Si cette option est cochée, autorisez les membres à entrer leur propre raison pour signaler un événement ou un commentaire comme inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]**

   Entrez le nombre de fois où un événement ou un commentaire doit être marqué par les membres avant que les modérateurs ne soient avertis. La valeur par défaut est 1 (une fois).

* **[!UICONTROL Limite de marquage]**

   Entrez le nombre de fois où un événement ou un commentaire doit être marqué avant d’être masqué dans la vue publique. Si la valeur est -1, le sujet ou le commentaire marqué est toujours visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au seuil de modération. La valeur par défaut est 5.

#### Onglet Champ de balise {#tag-field-tab}

Dans l’onglet **[!UICONTROL Champ de balise]**, les balises qui peuvent être appliquées, si l’option est activée dans l’onglet **[!UICONTROL Paramètres]**, sont limitées selon les espaces de noms sélectionnés.

* **[!UICONTROL Espaces de noms autorisés]**

   Pertinente si `Allow Tagging` est cochée sous l’onglet **[!UICONTROL Paramètres]** . Les balises pouvant être appliquées se limitent à celles liées aux catégories d’espace de noms cochées. La liste des espaces de noms inclut &quot;Balises standard&quot; (espace de noms par défaut) ainsi que &quot;Inclure toutes les balises&quot;. La valeur par défaut n’est pas cochée, ce qui signifie que tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestions]**

   Entrez le nombre de balises à afficher comme suggestion au membre qui publie sur le forum. Default is `-1` (no limits).

>[!NOTE]
>
>Consultez la rubrique [Administration des balises](../../help/sites-administering/tags.md) pour savoir comment ajouter un espace de noms de balise (taxonomie).

#### Onglet Traduction {#translation-tab}

Sous l’onglet **[!UICONTROL Traduction]**, si la traduction est activée pour le site de la communauté, elle peut être définie de sorte à traduire le fil d’Ariane entier (événement et commentaires) au lieu de certaines publications.

* **[!UICONTROL Tout traduire]**

   Si cette option est cochée, l’événement et les commentaires sont traduits dans la langue préférée de l’utilisateur. Cette option est cochée par défaut.

## Expérience des visiteurs {#site-visitor-experience}

Dans l’environnement de publication, la fonction Calendrier présente un champ de recherche avec une plage de dates par défaut et tous les événements de calendrier prévus pour cette plage.

Lorsqu’un événement de calendrier est sélectionné, ses détails, sa description et ses commentaires sont affichés.

Les autres choix varient selon que le visiteur est modérateur, administrateur, membre de la communauté, membre privilégié ou anonyme.

### Modérateurs et administrateurs {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut se charger d’[activités de modération](moderate-ugc.md) (autorisées par la configuration du composant) pour tous les événements et commentaires de calendrier publiés pour un événement.

![chlimage_1-115](assets/chlimage_1-115.png)

### Membres {#members}

When the signed in user is a community member or [privileged member](users.md#privileged-members-group) (depending on configuration), they are able to select `New Event` to create and post a new calendar event.

Plus précisément, il est autorisé à :

* Créer un événement de calendrier
* Publication d’un commentaire sur un événement de calendrier
* Modifier leur propre événement de calendrier ou commentaire
* Supprimer leur propre événement de calendrier ou commentaire
* Marquer les événements ou les commentaires d’autres utilisateurs

![chlimage_1-116](assets/chlimage_1-116.png) ![chlimage_1-117](assets/chlimage_1-117.png)

### Anonyme {#anonymous}

Les visiteurs non inscrits peuvent lire les événements de calendrier et les traduire lorsque cela est possible. Toutefois, ils ne sont pas autorisés à ajouter un événement ou un commentaire de calendrier, ni à marquer les événements ou les commentaires d’autres membres.

![chlimage_1-118](assets/chlimage_1-118.png)

## Informations supplémentaires {#additional-information}

More information may be found on the [Calendar Essentials](calendar-basics-for-developers.md) page for developers.

Pour des informations sur la modération des événements et des commentaires de calendrier, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

For tagging calendar events and comments, see [Tagging User Generated Content](tag-ugc.md).

For translation of calendar events and comments, see [Translating User Generated Content](translate-ugc.md).
