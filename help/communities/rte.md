---
title: Principes élémentaires de l’éditeur de texte enrichi
seo-title: Rich Text Editor Essentials
description: Présentation de la fonction Éditeur de texte enrichi
seo-description: Rich text Editor feature overview
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
exl-id: d236a8d3-20ad-4568-a7c2-87d146aa0532
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 5%

---

# Principes élémentaires de l’éditeur de texte enrichi {#rich-text-editor-essentials}

## Présentation {#overview}

Un éditeur de texte enrichi (RTE) permet de saisir du texte avec des balises.

Pour les composants Communities, tout en étant similaire à [éditeur de texte enrichi dans l’environnement de création](../../help/sites-authoring/rich-text-editor.md), cela affecte le texte saisi dans l’environnement de publication.

![chlimage_1-410](assets/chlimage_1-410.png)

## Activation de l’éditeur de texte enrichi {#enabling-rich-text-editor}

Les composants de communauté qui autorisent le contenu généré par l’utilisateur peuvent être activés pour autoriser l’éditeur de texte enrichi. Selon que le composant a été ajouté à une page ou inclus dans une [function](functions.md), l’éditeur de texte enrichi peut être activé ou non par défaut.

S’il n’est pas activé, il vous suffit de saisir [mode d’édition de l’auteur](sites-console.md#authoring-site-content), sélectionnez le composant à modifier, puis sélectionnez l’option `Rich Text Editor` .

L’éditeur de texte enrichi est disponible pour les composants Communities suivants :

* [Blog](blog-feature.md)
* [Calendrier](calendar.md)
* [Commentaires](comments.md)
* [Filelibrary](file-library.md)
* [Forum](forum.md)
* [Message](configure-messaging.md)
* [Q&amp;R](working-with-qna.md)
* [Révisions](reviews.md)

## Personnalisation {#customization}

La personnalisation de l’éditeur de texte enrichi est possible, car l’implémentation est basée sur [CKEditor](https://www.ckeditor.com/).

La configuration actuelle des composants Communities se trouve dans la variable `cq.social.  scf   clientlib`, situé dans le référentiel à l’adresse

`/libs/clientlibs/social/commons/scf/ckrte.js`

La modification de la bibliothèque cliente cq.social.scf n’est pas recommandée, car les futures mises à niveau peuvent remplacer toute modification.

### Exemple de personnalisation : Liens intégrés {#example-customization-inline-links}

En raison de problèmes de sécurité, les options de lien hypertexte ne sont pas incluses dans l’ensemble d’icônes de texte enrichi présentées aux membres par défaut. Les risques de malentendu sont importants lorsque les trois-quarts sont autorisés dans le contenu généré par l’utilisateur.

Pour ajouter les options de lien hypertexte à la barre d’outils :

* Ajoutez une barre d’outils nommée &quot; `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Sélectionnez **[!UICONTROL Enregistrer tout]**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links', 
           items: [ 'Link','Unlink','Anchor' ] 
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```
