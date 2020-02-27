---
title: Utilisation des commentaires
seo-title: Utilisation des commentaires
description: La fonction Commentaires permet aux visiteurs du site connectés de partager leurs opinions et leurs connaissances
seo-description: La fonction Commentaires permet aux visiteurs du site connectés de partager leurs opinions et leurs connaissances
uuid: 30fc48ac-134c-4acb-a65c-398855c93829
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b074ebfa-2894-4a2d-aa8e-28168049971a
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b

---


# Utilisation des commentaires {#using-comments}

## Présentation {#introduction}

La fonction Commentaires permet aux visiteurs connectés (membres) d’échanger leurs opinions et leurs connaissances concernant le contenu du site. Cette fonction est souvent déjà présente dans d’autres fonctions, mais peut être ajoutée à n’importe quel site web.

Cette section de la documentation décrit :

* Adding `Comments`to a page
* Configuration settings for the `Comments`component

>[!NOTE]
>
>La publication anonyme d’un commentaire n’est pas possible. Les visiteurs du site doivent s&#39;inscrire (devenir membre) et se connecter pour participer.

## Ajout de commentaires à une page {#adding-comments-to-a-page}

To add a `Comments`component to a page in author mode, use the component browser to locate

* `Communities / Comments`

et faites glisser le composant sur une page, par exemple à un endroit relatif à la fonction pour que les utilisateurs puissent commenter, ou simplement au bas de la page.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](essentials-comments.md#essentials-for-client-side) are included, this is how the `Comments`component will appear.

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>Only one `Comments`component may exist on a page. Sachez que de nombreuses fonctions d’AEM Communities incluent déjà des commentaires. C’est le cas des blogs, des calendriers, des forums, des Q&amp;R et des révisions.

## Configuration des commentaires {#configuring-comments}

Select the placed `Comments` component to access and select the `Configure` icon which opens the edit dialog.

![configuration](assets/configure.png) des paramètres ![de commentaire](assets/commentssettings.png)

### Onglet Commentaires {#comments-tab}

Sous l’onglet **[!UICONTROL Commentaires]**, indiquez la façon dont les commentaires seront entrés par les visiteurs.

* **[!UICONTROL Autoriser les réponses]**

   Si elle est cochée, permet aux membres de répondre aux commentaires existants. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Commentaires par page]**

   Limite le nombre de commentaires affichés par page ainsi que le nombre de réponses affichées. La valeur par défaut est 10.

* **[!UICONTROL Autoriser les transferts de fichiers]**

   Si cette case est cochée, l’option de téléchargement d’un fichier s’affiche avec la zone de texte. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille maximale du fichier]**

   Applicable uniquement si l’option Autoriser les téléchargements de fichiers est cochée. Cette valeur limite la taille du fichier chargé. La limite par défaut est de 10 Mo.

* **[!UICONTROL Longueur de message max.]**

   Nombre maximal de caractères pouvant être saisis dans la zone de texte. La valeur par défaut est de 4 096 caractères.

* **[!UICONTROL Types de fichier autorisés]**

   Applicable uniquement si l’option Autoriser les téléchargements de fichiers est cochée. Liste d’extensions de fichiers séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichier sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés. Par défaut, aucun type de fichier n’est spécifié, de sorte que tous les types de fichier soient autorisés.

* **[!UICONTROL Éditeur de texte enrichi]**

   Si cette option est cochée, les commentaires peuvent être saisis avec une annotation. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]**

   Si cette option est cochée, l&#39;option de voter vers le haut ou vers le bas sera présentée avec la zone de texte. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser abonnement]**

   Si cette option est cochée, permettez aux membres de suivre les commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher les badges]**

   Si cette option est cochée, autorisez l’affichage des badges gagnés et attribués. Cette option n’est pas cochée par défaut.

### Onglet Modération utilisateur {#user-moderation-tab}

Under the **[!UICONTROL User Moderation]** tab, specify how the posted comments are managed. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Prémodération]**

   Si cette option est cochée, les commentaires doivent être approuvés avant d’apparaître sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Supprimer les commentaires]**

   Si cette option est cochée, le membre qui a publié le commentaire peut le supprimer. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Refuser les commentaires]**

   Si cette option est cochée, autorisez les modérateurs à refuser les commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les commentaires]**

   Si cette option est cochée, autorisez les modérateurs à fermer et rouvrir les commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les commentaires]**

   Si cette option est cochée, permettez aux membres de signaler les commentaires comme inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]**

   Si cette option est cochée, permettez aux membres de choisir, dans une liste déroulante, la raison pour laquelle ils signalent un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]**

   Si cette option est cochée, autorisez les membres à entrer leur propre raison pour signaler un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]**

   Entrez le nombre de fois où un commentaire doit être marqué par les membres avant que les modérateurs ne soient avertis. La valeur par défaut est une fois (1).

* **[!UICONTROL Limite de marquage]**

   Entrez le nombre de fois où un commentaire doit être marqué avant d’être masqué dans la vue publique. Dans le cas contraire, cette valeur doit être supérieure ou égale au **[!UICONTROL seuil de modération]**. La valeur par défaut est 5.

### Onglet Paramètres de tri {#sort-settings-tab}

Sous l’onglet Paramètres **[!UICONTROL de]** tri, spécifiez le mode de tri des commentaires publiés lorsqu’ils sont affichés.

* **[!UICONTROL Champ de tri]**

   Tirez vers le bas pour sélectionner l’un des `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`, ou `Most Liked`.

* **[!UICONTROL Ordre de tri]**

   Tirez vers le bas pour sélectionner l’un des `Ascending` ou `Descending`.

### Modification d’un type de commentaire personnalisé {#changing-to-a-custom-comment-type}

En modifiant le type de ressource de commentaire, le système de commentaires ne génère plus une instance d’un commentaire avec les paramètres par défaut, mais plutôt un commentaire personnalisé (étendu) par les développeurs.

Once the custom resource types is known, enter [Design Mode](../../help/sites-authoring/default-components-designmode.md) and double click on the placed `Comments` component to open a dialog with an additional tab.

Under the **[!UICONTROL Resource Types]** tab, specify the custom resourceType for new instances of the `Comments or Voting`components:

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL Type de ressource de commentaire]**

   Accédez à resourceType d’un `comment`composant étendu (commentaire unique) dans /apps. Par exemple, `/apps/social/commons/components/hbs/comments/comment`

   Cette ressource identifie le type de ressource de l’UGC créé lorsqu’un visiteur publie un commentaire.

* **[!UICONTROL Type de ressource de vote]**

   Accédez à resourceType d’un `voting`composant étendu dans /apps. Par exemple, `/apps/social/components/hbs/voting`

   Cette ressource identifie le type de ressource de l’UGC créé lorsqu’un visiteur publie un vote.

* **[!UICONTROL Type de ressource système de commentaires]**

   Accédez à resourceType d’un `comments`composant étendu (système de commentaires) dans /apps. Leave blank unless the page template [dynamically includes](scf.md#add-or-include-a-communities-component) the Comment System in the underlying script instead of being added to the page as a resource (comments node). Learn more by reading about the [{{include}} helper](handlebars-helpers.md#include).

## Expérience des visiteurs {#site-visitor-experience}

### Modérateurs et administrateurs {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut se charger d’activités de modération autorisées par la configuration du composant, peu importe qui a créé le commentaire.

### Membres {#members}

Lorsque le visiteur est connecté, selon la configuration, il peut :

* Publier un nouveau commentaire
* Modifier son propre commentaire
* Supprimer leur propre commentaire
* Signaler les commentaires des autres

### Anonyme {#anonymous}

Les visiteurs non connectés peuvent lire les commentaires et les traduire lorsque cela est possible. Toutefois, ils ne sont pas autorisés à ajouter un commentaire, ni à marquer les commentaires d’autres membres.

## Informations supplémentaires {#additional-information}

More information may be found on the [Comments Essentials](essentials-comments.md) page for developers.

For moderation of posted comments, see [Moderating User Generated Content](moderate-ugc.md).

Pour des informations sur la traduction des commentaires publiés, voir [Traduction de contenu généré par les utilisateurs](translate-ugc.md).
