---
title: Modification de l’aspect (HBS)
seo-title: Modification de l’aspect
description: Modification des scripts HBS
seo-description: Modification des scripts HBS
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# Modifier l’aspect (HBS) {#alter-the-appearance-hbs}

Maintenant que les composants du système de commentaires personnalisé dans le répertoire de l’application (/apps) sont en place, avec un resourceSuperType référençant le système de commentaires par défaut et le modèle/affichage personnalisé enregistré, il est possible de modifier l’implémentation.

Pour une démonstration simple, l’avatar affiché pour l’utilisateur connecté qui publie un commentaire est supprimé.

>[!NOTE]
>
>Pour utiliser l’extension , l’instance du système de commentaires d’un site web à affecter (/content) doit définir son resourceType comme système de commentaires personnalisé.

## Modification des scripts HBS {#modify-the-hbs-scripts}

Utilisation de [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) :

* Ouvrez [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Commentez la balise qui contient l’avatar d’une publication de commentaire (~ ligne 21) :

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Ouvrez [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Mettez en commentaire la balise qui contient l’avatar pour la prochaine entrée de commentaire (~ ligne 44) :

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Sélectionnez **Enregistrer tout**.

## Répliquer l’application personnalisée {#replicate-custom-app}

Une fois l’application modifiée, il est nécessaire de répliquer à nouveau le composant personnalisé.

Pour ce faire, une méthode consiste à

* À partir du menu principal

   * Sélectionnez **[!UICONTROL Outils > Opérations > Réplication]**
   * Sélectionner `Activate Tree`
   * Définissez `Start Path` : à `/apps/custom`
   * Décochez `Only Modified`
   * Bouton Sélectionner `Activate`

## Afficher le commentaire modifié sur l’exemple de page publié {#view-modified-comment-on-published-sample-page}

[En poursuivant l’](extend-sample-page.md#publish-sample-page) expérience sur l’instance de publication, toujours connecté en tant qu’utilisateur identique, il est désormais possible d’actualiser la page dans l’environnement de publication pour afficher la modification afin de supprimer l’avatar :

![chlimage_1-81](assets/chlimage_1-81.png)

## Exemple de module d’extension de commentaire {#sample-comment-extension-package}

Vous trouverez ci-joint un package de l’application de commentaires personnalisés créée dans ce tutoriel.

[Obtenir le fichier](assets/sample-comment-extension-6-1-fp3.zip)
