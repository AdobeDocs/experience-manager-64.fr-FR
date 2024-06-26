---
title: Fonctionnalité Contenu proposé
seo-title: Featured Content Feature
description: La fonctionnalité Contenu mis en page permet aux visiteurs connectés du site de mettre en surbrillance le contenu.
seo-description: The Featured Content feature lets signed-in site visitors highlight content
uuid: 7a2ff570-01bb-46fb-8d66-3b47e2efa72e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ee39435d-80f5-4758-ae01-1ea0d221b00b
exl-id: a0dcffed-1040-4d6d-b8e9-3bbe5f30deb4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 8%

---

# Fonctionnalité Contenu proposé {#featured-content-feature}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

La fonctionnalité de contenu présenté fournit une zone pour les visiteurs connectés du site (membres de la communauté) dans l’environnement de publication afin de mettre en évidence le contenu pour

* [Blogs](blog-feature.md)
* [Calendriers](calendar.md)
* [Forums](forum.md)
* [Idées](ideation-feature.md)
* [Q&amp;R](working-with-qna.md)

Une fois que le contenu est marqué comme présenté, il est répertorié dans ce composant, qui peut être placé dans des pages d’entrée spécifiques ou des zones qui attirent facilement l’attention des membres de la communauté.

La possibilité d’afficher du contenu peut être autorisée ou non par composant.

Cette section de la documentation décrit

* Ajout de contenu présenté à un site de la communauté
* Paramètres de configuration de la variable `Featured Content`component

## Ajout de contenu proposé à une page {#adding-featured-content-to-a-page}

Pour ajouter une `Featured Content` sur une page en mode création, utilisez l’explorateur de composants pour accéder à

* `Communities / Featured Content`

et faites-le glisser sur la page où le contenu présenté doit apparaître.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](essentials-featured.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Featured Content`apparaît :

![chlimage_1-13](assets/chlimage_1-13.png)

## Configuration du contenu proposé {#configuring-featured-content}

Sélectionnez le `Featured Content` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-14](assets/chlimage_1-14.png) ![chlimage_1-15](assets/chlimage_1-15.png)

### Onglet Paramètres {#settings-tab}

Sous , **[!UICONTROL Paramètres]** , identifiez le contenu à afficher :

* **[!UICONTROL Nom d’affichage]**
Titre de la liste du contenu présenté. Par exemple : 
`Featured Questions` ou `Featured Ideas`. La valeur par défaut est `Featured Content` s’il est vide.

* **[!UICONTROL Emplacement du contenu proposé]**

   *(Obligatoire)* Accédez à la page contenant le contenu pouvant être une fonctionnalité (les composants de cette page doivent être configurés sur Autoriser le contenu proposé). Par exemple, `/content/sites/engage/en/forum`

* **[!UICONTROL Limite d’affichage]**
Nombre maximal de contenus présentés à afficher. La valeur par défaut est 5.

## Expérience du visiteur du site {#site-visitor-experience}

La capacité à marquer le contenu comme contenu présenté nécessite des privilèges de modérateur.

Lorsqu’un modérateur affiche du contenu publié, il a accès aux indicateurs de modération contextuelle, qui incluent la nouvelle `Feature` Indicateur.

![chlimage_1-16](assets/chlimage_1-16.png)

Une fois la balise marquée comme fonctionnalité, l’indicateur de modération devient `Unfeature`.

La page contenant la variable `Featured Content` inclut désormais cette publication.

![chlimage_1-17](assets/chlimage_1-17.png)

`Read More` est un lien vers la publication active.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Contenu en vedette](essentials-featured.md) pour les développeurs.

Pour marquer le contenu comme présenté, voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).
