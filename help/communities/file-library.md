---
title: Fonctionnalité Bibliothèque de fichiers
seo-title: File Library Feature
description: La fonctionnalité Bibliothèque de fichiers permet aux visiteurs connectés du site de télécharger, gérer et télécharger des fichiers.
seo-description: The File Library feature lets signed-in site visitors upload, manage, and download files
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
exl-id: c72b246d-442e-4841-810d-1045e83f60f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 66%

---

# Fonctionnalité Bibliothèque de fichiers {#file-library-feature}

## Présentation {#introduction}

La fonctionnalité Bibliothèque de fichiers fournit un espace où les visiteurs du site connectés (membres de la communauté) peuvent transférer, gérer et télécharger des fichiers sur le site de la communauté.

Cette section de la documentation décrit :

* Ajout de la fonction Bibliothèque de fichiers à un site AEM
* Paramètres de configuration de la variable `File Library` component

## Ajout d’une bibliothèque de fichiers à une page {#adding-a-file-library-to-a-page}

Pour ajouter une `File Library` à une page en mode création, recherchez le composant.

* `Communities / File Library`

et faites-le glisser sur la page.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-file-library.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `File Library` apparaît :

![chlimage_1-430](assets/chlimage_1-430.png)

## Configuration de la bibliothèque de fichiers {#configuring-file-library}

Sélectionnez le `File Library` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Onglet Commentaires {#comments-tab}

Dans l’onglet **[!UICONTROL Commentaires]**, indiquez si et comment les commentaires pour les fichiers transférés apparaissent :

* **[!UICONTROL Autoriser les commentaires sur les fichiers]** Si cette option est cochée, les commentaires sur les fichiers transférés sont autorisés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Commentaires par page]** Limite le nombre de commentaires par page, ainsi que le nombre de réponses affichées. La valeur par défaut est 
**10**.

* **[!UICONTROL Taille maximale du fichier]** Cette valeur limite la taille du fichier transféré. La limite par défaut est 104857600 (10 Mo).

* **[!UICONTROL Longueur de message max.]** Nombre maximal de caractères qui peuvent être saisis dans la zone de texte. La valeur par défaut est de 4 096 caractères.

* **[!UICONTROL Types de fichier autorisés]** Une liste d’extensions de fichier séparées par des virgules avec le séparateur « point ». Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Éditeur de texte enrichi]** Si cette option est activée, les commentaires peuvent être saisis avec une mise en forme. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Supprimer des commentaires]**
Si cette case est cochée, les utilisateurs sont autorisés à supprimer leurs propres commentaires. Cette option est cochée par défaut.

* **[!UICONTROL Autoriser le balisage]** Si cette option est cochée, une balise peut être ajoutée au fichier. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Espaces de noms autorisés]**
Si l’option Autoriser le balisage est cochée, les balises disponibles sont limitées aux espaces de noms cochés. Si aucun n’est coché, tous sont autorisés. Par défaut, tous les espaces de noms sont autorisés.

* **[!UICONTROL Limite de suggestions]** Si l’option Autoriser le balisage est sélectionnée, ce paramètre limite le nombre de balises suggérées à afficher. Si la valeur est -1, il n’existe aucune limite. La valeur par défaut est -1.

* **[!UICONTROL Autoriser le vote]**
Si cette case est cochée, la possibilité de voter pour un fichier est activée. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser l’exécution]**
Si cette case est cochée, incluez la fonction suivante pour les articles de blog, ce qui permet aux membres d’être [notify](notifications.md) de nouvelles publications. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les réponses à threads]**
Si cette case est cochée, les réponses aux commentaires publiés sont autorisées. Cette option n’est pas cochée par défaut.

### Onglet Modération d’utilisateur {#user-moderation-tab}

Dans l’onglet **[!UICONTROL Modération d’utilisateur]**, configurez la modération des commentaires, si les commentaires sont autorisés :

* **[!UICONTROL Prémodération]** Si cette option est activée, les commentaires doivent être approuvés pour être visibles sur un site de publication. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Supprimer les commentaires]** Si cette option est activée, le visiteur qui a publié le commentaire a le droit de le supprimer. Cette option est cochée par défaut.

* **[!UICONTROL Refuser les commentaires]** Si cette option est activée, les modérateurs de membre approuvés ont le droit de refuser des commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Fermer/rouvrir les commentaires]** Si cette option est activée, les modérateurs de membre approuvés sont autorisés à fermer et à rouvrir les commentaires. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer les commentaires]** Si cette option est activée, les visiteurs ont le droit de marquer des commentaires comme étant inappropriés. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Marquer la liste de motifs]** Si cette option est activée, les visiteurs ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Motif de la marque personnalisée]** Si cette option est activée, les visiteurs ont le droit de préciser la raison pour laquelle ils ont marqué un commentaire comme étant inapproprié. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Seuil de modération]** Saisissez le nombre de fois qu’un commentaire doit être marqué par les visiteurs avant que les modérateurs n’en soient informés. La valeur par défaut est une fois (
**1**).

* **[!UICONTROL Limite de marquage]** Saisissez le nombre de fois qu’un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Ce nombre doit être supérieur ou égal à 
**Seuil de modération**. La valeur par défaut est 5.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur la bibliothèque de fichiers](essentials-file-library.md) pour les développeurs.

Pour des informations sur la modération des sujets et des commentaires publiés, reportez-vous à la section [Modération du contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser les sujets et les commentaires publiés, voir [Balisage de contenu généré par l’utilisateur](tag-ugc.md).
