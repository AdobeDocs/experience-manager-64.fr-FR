---
title: Principes de base des composants des communautés
seo-title: Communities Components Basics
description: Ajout de fonctionnalités Communities à AEM sites en mode d’édition et configuration de composants
seo-description: Add Communities features to AEM sites in edit mode and configure components
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
exl-id: 17fbee1c-5657-442a-8c9d-1456b853f666
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 4%

---

# Principes de base des composants des communautés {#communities-components-basics}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

La section de création de la documentation décrit l’ajout de fonctionnalités Communities à AEM sites en mode d’édition de création, ainsi que la description des configurations de composant.

Les composants peuvent être explorés à l’aide d’une instance AEM et de l’objet interactif [Guide des composants de communauté](components-guide.md).

## Accès aux composants Communities {#accessing-communities-components}

Lors de la création du contenu d’une page, si le modèle sous-jacent permet de modifier la conception de la page, il est possible d’activer les composants qui ne sont pas déjà disponibles dans l’explorateur de composants dans le cadre de la conception du site.

Les composants de communauté disponibles sont répertoriés. [here](author-communities.md#available-communities-components).

>[!NOTE]
>
>Pour obtenir des informations générales sur la création, consultez la [guide rapide pour la création de pages](../../help/sites-authoring/qg-page-authoring.md).
>
>Si vous ne connaissez pas AEM, consultez la documentation sur [gestion de base](../../help/sites-authoring/basic-handling.md).

### Accès au mode Conception {#entering-design-mode}

Si une **Communautés** Le composant est introuvable dans l’explorateur de composants (sidekick), il sera nécessaire de saisir `Design Mode` pour ajouter d’autres composants Communities. [Bibliothèques côté client requises](#required-clientlibs) (clientlibs) doit également être ajouté.

Pour plus d’informations, voir [Configuration des composants en mode de conception](../../help/sites-authoring/default-components-designmode.md).

Vous trouverez ci-dessous des images de la sélection de quelques composants Communities et de leur affichage dans l’explorateur de composants :

![chlimage_1-424](assets/chlimage_1-424.png)

Les composants sélectionnés sont désormais disponibles dans l’explorateur de composants :

![chlimage_1-425](assets/chlimage_1-425.png)

## Clientlibs obligatoires {#required-clientlibs}

[Bibliothèques côté client](../../help/sites-developing/clientlibs.md) (clientlibs) sont nécessaires au bon fonctionnement (JavaScript) et au style (CSS) d’un composant.

Lors de l’ajout d’un composant Communities à une page, si le résultat est une erreur ou une apparence inattendue, la première chose à essayer est d’ajouter les bibliothèques client requises pour le composant Communities. Pour plus d’informations, voir [Clientlibs des composants Communities](clientlibs.md).

### Exemple : Révisions placées initialement sans bibliothèques clientes... {#example-initially-placed-reviews-without-client-libraries}

![chlimage_1-426](assets/chlimage_1-426.png)

### ... Et avec les bibliothèques clientes {#and-with-client-libraries}

![chlimage_1-427](assets/chlimage_1-427.png)

## Balisage {#tagging}

De nombreuses fonctionnalités de Communities peuvent être configurées pour permettre aux membres de baliser le contenu saisi (publié) dans l’environnement de publication.

Si le balisage est autorisé, la configuration du site de la communauté peut être définie pour limiter les espaces de noms présentés aux membres dans l’environnement de publication. Voir [Console Sites de communauté](sites-console.md#tagging).

Fonctionnalités qui permettent le balisage : [blog](blog-feature.md), [calendar](calendar.md), [bibliothèque de fichiers](file-library.md), [forum](forum.md)

Fonctionnalités qui utilisent des balises : [catalogue](catalog.md), [search](search.md), [nuage de balises sociales](tagcloud.md)

Pour les informations de création :

* [Utilisation des balises](../../help/sites-authoring/tags.md)

Pour plus d’informations sur l’administration :

* Création d’espaces de noms de balise (taxonomie) : [Administration des balises](../../help/sites-administering/tags.md)
* Configuration du site de la communauté : see [BALISAGE](sites-console.md#tagging)
* [Balisage du contenu généré par l’utilisateur](../../help/sites-authoring/tags.md)
* [Balisage des ressources d’activation](tag-resources.md)

Pour plus d’informations sur les développeurs :

* [Framework de balisage AEM](../../help/sites-developing/framework.md)
* [Notions fondamentales sur le balisage](tag.md)
