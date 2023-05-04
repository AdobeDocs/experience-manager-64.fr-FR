---
title: Ajout d’un commentaire à un exemple de page
seo-title: Add Comment to Sample Page
description: Ajout de commentaires personnalisés à une page
seo-description: Add Custom Comments to a page
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 2%

---

# Ajout d’un commentaire à un exemple de page {#add-comment-to-sample-page}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Maintenant que les composants du système de commentaires personnalisé sont en place dans le répertoire de l’application (/apps), il est possible d’utiliser le composant étendu. L’instance du système de commentaires d’un site web à affecter doit définir resourceType comme système de commentaires personnalisé et inclure toutes les bibliothèques clientes nécessaires.

## Identification des bibliothèques clientes requises {#identify-required-clientlibs}

Les bibliothèques clientes nécessaires au style et au fonctionnement des commentaires par défaut sont également nécessaires pour les commentaires étendus.

Le [Guide des composants de communauté](components-guide.md) identifie les bibliothèques clientes requises. Accédez au Guide du composant et affichez le composant Commentaires , par exemple :

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Notez les trois bibliothèques clientes requises pour que les commentaires s’affichent et fonctionnent correctement. Ils doivent être inclus là où les commentaires étendus sont référencés, ainsi que la variable [bibliothèque cliente étendue des commentaires](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## Ajout de commentaires personnalisés à une page {#add-custom-comments-to-a-page}

Comme il ne peut y avoir qu’un seul système de commentaires par page, il est plus simple de créer un exemple de page comme décrit dans la section courte [Création d’un exemple de page](create-sample-page.md) tutoriel .

Une fois créé, accédez au mode Conception et rendez disponible le groupe de composants personnalisés pour permettre au `Alt Comments` à ajouter à la page.

Pour que le commentaire s’affiche et fonctionne correctement, les bibliothèques clientes pour les commentaires doivent être ajoutées à la liste de bibliothèques clientes pour la page (voir [Clientlibs des composants Communities](clientlibs.md)).

### Comments Clientlibs sur l’exemple de page {#comments-clientlibs-on-sample-page}

![Comments Clientlibs sur l’exemple de page](assets/chlimage_1-48.png)

### Auteur : Commentaire Alt sur un exemple de page {#author-alt-comment-on-sample-page}

![Commentaire Alt sur un exemple de page](assets/chlimage_1-49.png)

### Auteur : Exemple de noeud de commentaires de page {#author-sample-page-comments-node}

Vous pouvez vérifier le type de ressource dans CRXDE en affichant les propriétés du noeud de commentaires pour la page d’exemple à l’adresse `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### Publier l’exemple de page {#publish-sample-page}

Une fois le composant personnalisé ajouté à la page, il est également nécessaire de (re) [publier la page ;](sites-console.md#publishing-the-site).

### Publier : Commentaire Alt sur un exemple de page {#publish-alt-comment-on-sample-page}

Après la publication de l’application personnalisée et de l’exemple de page, il doit être possible de saisir un commentaire. Lorsque vous vous connectez, soit avec un [utilisateur de démonstration](tutorials.md#demo-users) ou admin, il devrait être possible de publier un commentaire.

Voici aaron.mcdonald@mailinator.com en publiant un commentaire :

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

Maintenant qu’il apparaît que le composant étendu fonctionne correctement avec l’apparence par défaut, il est temps de modifier l’apparence.
