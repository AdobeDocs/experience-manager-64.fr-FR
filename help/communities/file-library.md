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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 3%

---

# Fonctionnalité Bibliothèque de fichiers {#file-library-feature}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

La fonctionnalité Bibliothèque de fichiers fournit un emplacement où les visiteurs connectés du site (membres de la communauté) peuvent charger, gérer et télécharger des fichiers dans le site de la communauté.

Cette section de la documentation décrit

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

Sous , **[!UICONTROL Commentaires]** , indiquez si et comment les commentaires des fichiers chargés apparaissent :

* **[!UICONTROL Autorisation des commentaires sur les fichiers]**
Si cette option est cochée, les commentaires sur les fichiers chargés sont autorisés. La case par défaut est décochée.

* **[!UICONTROL Commentaires par page]**
Limite le nombre de commentaires affichés par page ainsi que le nombre de réponses affichées. La valeur par défaut est 
**10**.

* **[!UICONTROL Taille de fichier maximale]**
Cette valeur limite la taille du fichier téléchargé. La limite par défaut est 104857600 (10 Mo).

* **[!UICONTROL Longueur max. du message]**
Nombre maximal de caractères pouvant être saisis dans la zone de texte. La valeur par défaut est de 4 096 caractères.

* **[!UICONTROL Types de fichiers autorisés]**
Liste d’extensions de fichier séparées par des virgules avec le séparateur &quot;point&quot;. Par exemple : .jpg, .jpeg, .png, .doc, .docx, .pdf. Si des types de fichiers sont spécifiés, ceux qui ne sont pas spécifiés ne seront pas autorisés. Par défaut, aucun n’est spécifié, de sorte que tous les types de fichiers soient autorisés.

* **[!UICONTROL Éditeur de texte enrichi]**
Si cette case est cochée, les commentaires peuvent être saisis avec une annotation. La case par défaut est décochée.

* **[!UICONTROL Supprimer des commentaires]**
Si cette case est cochée, les utilisateurs sont autorisés à supprimer leurs propres commentaires. La valeur par défaut est cochée.

* **[!UICONTROL Autoriser le balisage]**
Si cette case est cochée, la possibilité d’ajouter une balise au fichier est activée. La case par défaut est décochée.

* **[!UICONTROL Espaces de noms autorisés]**
Si l’option Autoriser le balisage est cochée, les balises disponibles sont limitées aux espaces de noms cochés. Si aucun n’est coché, tous sont autorisés. La valeur par défaut est tous les espaces de noms.

* **[!UICONTROL Limite de suggestion]**
Si l’option Autoriser le balisage est cochée, ce paramètre limite le nombre de balises suggérées à afficher. S’il est défini sur -1, il n’y a aucune limite. La valeur par défaut est -1.

* **[!UICONTROL Autoriser le vote]**
Si cette case est cochée, la possibilité de voter pour un fichier est activée. La case par défaut est décochée.

* **[!UICONTROL Autoriser l’exécution]**
Si cette case est cochée, incluez la fonction suivante pour les articles de blog, ce qui permet aux membres d’être [notify](notifications.md) de nouvelles publications. La case par défaut est décochée.

* **[!UICONTROL Autoriser les réponses à threads]**
Si cette case est cochée, les réponses aux commentaires publiés sont autorisées. La case par défaut est décochée.

### Onglet Modération d’utilisateur {#user-moderation-tab}

Sous , **[!UICONTROL Modération d’utilisateur]** , configurez la modération des commentaires si les commentaires sont autorisés :

* **[!UICONTROL Prémodération]**
Si cette case est cochée, les commentaires doivent être approuvés avant d’apparaître sur un site de publication. La case par défaut est décochée.

* **[!UICONTROL Supprimer des commentaires]**
Si cette case est cochée, le visiteur qui a publié le commentaire peut le supprimer. La valeur par défaut est cochée.

* **[!UICONTROL Refuser les commentaires]**
Si cette case est cochée, autorisez les modérateurs de membres approuvés à refuser des commentaires. La case par défaut est décochée.

* **[!UICONTROL Fermer/rouvrir les commentaires]**
Si cette case est cochée, autorisez les modérateurs de membres approuvés à fermer et rouvrir les commentaires. La case par défaut est décochée.

* **[!UICONTROL Marquer les commentaires]**
Si cette case est cochée, autorisez les visiteurs à signaler les commentaires comme inappropriés. La case par défaut est décochée.

* **[!UICONTROL Marquer la liste de motifs]**
Si cette case est cochée, les visiteurs ont le droit de sélectionner dans une liste déroulante la ou les raisons pour lesquelles ils ont marqué un commentaire comme étant inapproprié. La case par défaut est décochée.

* **[!UICONTROL Motif de l’indicateur personnalisé]**
Si cette case est cochée, autorisez les visiteurs à indiquer leur propre raison de signaler un commentaire comme inapproprié. La case par défaut est décochée.

* **[!UICONTROL Seuil de modération]**
Saisissez le nombre de fois qu’un commentaire doit être marqué par les visiteurs avant que les modérateurs ne soient informés. La valeur par défaut est une fois (
**1**).

* **[!UICONTROL Limite de marquage]**
Saisissez le nombre de fois qu’un commentaire doit être marqué avant qu’il ne soit plus visible pour le public. Ce nombre doit être supérieur ou égal à 
**Seuil de modération**. La valeur par défaut est 5.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur la bibliothèque de fichiers](essentials-file-library.md) pour les développeurs.

Pour la modération des sujets et des commentaires publiés, voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

Pour baliser des sujets et des commentaires publiés, voir [Balisage du contenu généré par l’utilisateur](tag-ugc.md).
