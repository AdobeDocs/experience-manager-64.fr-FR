---
title: Utilisation des commentaires
seo-title: Using Comments
description: La fonction Commentaires permet aux visiteurs connectés du site de partager leurs opinions et leurs connaissances.
seo-description: Comments feature lets signed-in site visitors share their opinions and knowledge
uuid: 30fc48ac-134c-4acb-a65c-398855c93829
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b074ebfa-2894-4a2d-aa8e-28168049971a
exl-id: 8ad5ce3e-c5dd-48d7-8812-43172eda36cc
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 39%

---

# Utilisation des commentaires {#using-comments}

## Présentation {#introduction}

La fonction Commentaires permet aux visiteurs connectés (membres) d’échanger leurs opinions et leurs connaissances concernant le contenu du site. Cette fonction est souvent déjà présente dans d’autres fonctions, mais peut être ajoutée à n’importe quel site web.

Cette section de la documentation décrit :

* Ajouter `Comments`vers une page
* Paramètres de configuration de la variable `Comments`component

>[!NOTE]
>
>La publication anonyme d’un commentaire n’est pas possible. Les visiteurs du site doivent s’inscrire (devenir membres) et se connecter pour participer.

## Ajout de commentaires à une page {#adding-comments-to-a-page}

Pour ajouter une `Comments`sur une page en mode création, utilisez l’explorateur de composants pour accéder à

* `Communities / Comments`

et faites glisser le composant sur une page, par exemple à un endroit relatif à la fonction pour que les utilisateurs puissent commenter, ou simplement au bas de la page.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-comments.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Comments`s’affiche.

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>Un seul `Comments`peut exister sur une page. Sachez que de nombreuses fonctions d’AEM Communities incluent déjà des commentaires. C’est le cas des blogs, des calendriers, des forums, des Q&amp;R et des révisions.

## Configuration des commentaires {#configuring-comments}

Sélectionnez le `Comments` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![configure](assets/configure.png) ![comments settings](assets/commentssettings.png)

### Onglet Commentaires {#comments-tab}

Sous l’onglet **[!UICONTROL Commentaires]**, indiquez la façon dont les commentaires seront entrés par les visiteurs.

* **[!UICONTROL Autoriser les réponses]**

   Si cette case est cochée, les membres ont la possibilité de répondre aux commentaires existants. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Commentaires par page]**

   Limite le nombre de commentaires affichés par page ainsi que le nombre de réponses affichées. La valeur par défaut est 10.

* **[!UICONTROL Autoriser les transferts de fichiers]**

   Si cette case est cochée, l’option permettant de télécharger un fichier s’affiche avec la zone de saisie de texte. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Taille maximale du fichier]**

   À définir uniquement si l’option Autoriser les chargements de fichiers est cochée. Cette valeur limite la taille du fichier chargé. La limite par défaut est de 10 Mo.

* **[!UICONTROL Longueur de message max.]**

   Nombre maximal de caractères pouvant être saisis dans la zone de texte. La valeur par défaut est de 4 096 caractères.

* **[!UICONTROL Types de fichier autorisés]**

   À définir uniquement si l’option Autoriser les chargements de fichiers est cochée. Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Éditeur de texte enrichi]**

   Si cette case est cochée, les commentaires peuvent être saisis avec une annotation. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser le vote]**

   Si cette case est cochée, l’option permettant de voter vers le haut ou vers le bas s’affiche avec la zone de saisie de texte. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser abonnement]**

   Si cette option est cochée, les membres ont le droit de suivre les commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Afficher les badges]**

   Si cette case est cochée, les badges mérités et attribués doivent s’afficher. Cette option n’est pas cochée par défaut.

### Onglet Modération d’utilisateur {#user-moderation-tab}

Sous , **[!UICONTROL Modération d’utilisateur]** , indiquez comment les commentaires publiés sont gérés. Pour plus d’informations, voir [Modération de contenu généré par les utilisateurs](moderate-ugc.md).

* **[!UICONTROL Prémodération]**

   Si cette case est cochée, les commentaires doivent être approuvés avant d’apparaître sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Supprimer les commentaires]**

   Si cette case est cochée, le membre qui a publié le commentaire peut le supprimer. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Refuser les commentaires]**

   Si cette case est cochée, autorisez les modérateurs à refuser les commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les commentaires]**

   Si cette case est cochée, les modérateurs peuvent fermer et rouvrir les commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les commentaires]**

   Si cette case est cochée, les membres ont le droit de signaler les commentaires comme inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]**

   Si cette case est cochée, les membres ont le droit de choisir dans une liste déroulante la raison pour laquelle ils ont marqué un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]**

   Si cette case est cochée, autorisez les membres à indiquer leur propre raison de signaler un commentaire comme inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]**

   Saisissez le nombre de fois qu’un commentaire doit être marqué par les membres avant que les modérateurs ne soient informés. La valeur par défaut est une fois (1).

* **[!UICONTROL Limite de marquage]**

   Saisissez le nombre de fois qu’un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Dans le cas contraire, cette valeur doit être supérieure ou égale au **[!UICONTROL seuil de modération]**. La valeur par défaut est 5.

### Onglet Paramètres de tri {#sort-settings-tab}

Sous , **[!UICONTROL Paramètres de tri]** , indiquez comment les commentaires publiés sont triés lorsqu’ils sont affichés.

* **[!UICONTROL Champ de tri]**

   Menu déroulant pour sélectionner l’un des `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`ou `Most Liked`.

* **[!UICONTROL Ordre de tri]**

   Menu déroulant pour sélectionner l’un des `Ascending` ou `Descending`.

### Modification d’un type de commentaire personnalisé {#changing-to-a-custom-comment-type}

En modifiant le type de ressource de commentaire, le système de commentaires ne génère plus une instance d’un commentaire avec les paramètres par défaut, mais plutôt un commentaire personnalisé (étendu) par les développeurs.

Une fois les types de ressources personnalisés connus, saisissez [Mode de conception](../../help/sites-authoring/default-components-designmode.md) et double-cliquez sur le `Comments` pour ouvrir une boîte de dialogue avec un onglet supplémentaire.

Sous , **[!UICONTROL Types de ressources]** , spécifiez le type de ressource personnalisé pour les nouvelles instances de la variable `Comments or Voting`composants :

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL Type de ressource de commentaire]**

   Accédez au resourceType d’une extension `comment`composant (commentaire unique) dans /apps. Par exemple, `/apps/social/commons/components/hbs/comments/comment`

   Cette ressource identifie le type de ressource du contenu créé par un visiteur lorsqu’il publie un commentaire.

* **[!UICONTROL Type de ressource de vote]**

   Accédez au resourceType d’une extension `voting`dans /apps. Par exemple, `/apps/social/components/hbs/voting`

   Cette ressource identifie le type de ressource du contenu créé par un visiteur lorsqu’il publie un vote.

* **[!UICONTROL Type de ressource système de commentaires]**

   Accédez au resourceType d’une extension `comments`(système de commentaires) dans /apps. Laissez vide, sauf si le modèle de page [inclut dynamiquement](scf.md#add-or-include-a-communities-component) le système de commentaires dans le script sous-jacent au lieu d’être ajouté à la page en tant que ressource (noeud de commentaires). En savoir plus en lisant les [{{include} helper](handlebars-helpers.md#include).

## Expérience des visiteurs {#site-visitor-experience}

### Modérateurs et administrateurs {#moderators-and-administrators}

Lorsque l’utilisateur connecté dispose de privilèges de modérateur ou d’administrateur, il peut se charger d’activités de modération autorisées par la configuration du composant, peu importe qui a créé le commentaire.

### Membres {#members}

Lorsque le visiteur est connecté, selon la configuration, il peut :

* Publier un nouveau commentaire
* Modifier son propre commentaire
* Supprimer son propre commentaire
* Marquer les commentaires des autres

### Anonyme {#anonymous}

Les visiteurs non connectés peuvent lire les commentaires et les traduire lorsque cela est possible. Toutefois, ils ne sont pas autorisés à ajouter un commentaire, ni à marquer les commentaires d’autres membres.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur les commentaires](essentials-comments.md) pour les développeurs.

Pour la modération des commentaires publiés, voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

Pour des informations sur la traduction des commentaires publiés, voir [Traduction de contenu généré par les utilisateurs](translate-ugc.md).
