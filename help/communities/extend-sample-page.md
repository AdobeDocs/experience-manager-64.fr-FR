---
title: Ajout d’un commentaire à un exemple de page
seo-title: Ajout d’un commentaire à un exemple de page
description: Ajout de commentaires personnalisés à une page
seo-description: Ajout de commentaires personnalisés à une page
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Ajouter un commentaire à l’exemple de page {#add-comment-to-sample-page}

Maintenant que les composants du système de commentaires personnalisé sont en place dans le répertoire de l’application (/apps), il est possible d’utiliser le composant étendu. L’instance du système de commentaires d’un site web à affecter doit définir resourceType comme système de commentaires personnalisé et inclure toutes les bibliothèques clientes nécessaires.

## Identification des bibliothèques clientes requises {#identify-required-clientlibs}

Les bibliothèques clientes nécessaires au style et au fonctionnement des commentaires par défaut sont également nécessaires pour les commentaires étendus.

Le [Guide des composants de la communauté](components-guide.md) identifie les bibliothèques clientes requises. Accédez au Guide du composant et affichez le composant Commentaires , par exemple :

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Notez les trois bibliothèques clientes requises pour que les commentaires s’affichent et fonctionnent correctement. Ils doivent être inclus lorsque les commentaires étendus sont référencés, ainsi que la [bibliothèque cliente des commentaires étendue](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## Ajout de commentaires personnalisés à une page {#add-custom-comments-to-a-page}

Comme il ne peut y avoir qu’un seul système de commentaires par page, il est plus simple de créer un exemple de page, comme décrit dans le tutoriel court [Créer une page d’exemple](create-sample-page.md) .

Une fois créé, passez en mode de conception et rendez disponible le groupe de composants personnalisés pour permettre l’ajout du composant `Alt Comments` à la page.

Pour que le commentaire s’affiche et fonctionne correctement, les bibliothèques clientes pour les commentaires doivent être ajoutées à la liste clientlibslist pour la page (voir [Clientlibs for Communities Components](clientlibs.md)).

### Comments Clientlibs sur l’exemple de page {#comments-clientlibs-on-sample-page}

![Comments Clientlibs sur l’exemple de page](assets/chlimage_1-48.png)

### Auteur : Commentaire Alt sur l’exemple de page {#author-alt-comment-on-sample-page}

![Commentaire Alt sur un exemple de page](assets/chlimage_1-49.png)

### Auteur : Exemple de noeud de commentaires de page {#author-sample-page-comments-node}

Vous pouvez vérifier le type de ressource dans CRXDE en affichant les propriétés du noeud de commentaires pour l’exemple de page à l’adresse `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### Publier l’exemple de page {#publish-sample-page}

Une fois le composant personnalisé ajouté à la page, il est également nécessaire de (re) [publier la page](sites-console.md#publishing-the-site).

### Publier : Commentaire Alt sur l’exemple de page {#publish-alt-comment-on-sample-page}

Après la publication de l’application personnalisée et de l’exemple de page, il doit être possible de saisir un commentaire. Une fois connecté, avec un [utilisateur de démonstration](tutorials.md#demo-users) ou un administrateur, il doit être possible de publier un commentaire.

Voici aaron.mcdonald@mailinator.com en publiant un commentaire :

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

Maintenant qu’il apparaît que le composant étendu fonctionne correctement avec l’apparence par défaut, il est temps de modifier l’apparence.
