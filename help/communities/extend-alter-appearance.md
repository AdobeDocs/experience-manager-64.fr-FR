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
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---


# Modification de l’aspect (HBS) {#alter-the-appearance-hbs}

Maintenant que les composants du système de commentaires personnalisés dans le répertoire de l&#39;application (/apps) sont en place, avec un resourceSuperType référençant le système de commentaires par défaut et le modèle/Vue personnalisé enregistré, il est possible de modifier l&#39;implémentation.

Pour une simple démonstration, une fonction visuelle, l’avatar affiché par l’utilisateur connecté qui publie un commentaire, est supprimée.

>[!NOTE]
>
>Pour utiliser l&#39;extension, l&#39;instance du système de commentaires d&#39;un site Web à affecter (/content) doit définir resourceType comme système de commentaires personnalisé.

## Modification des scripts HBS {#modify-the-hbs-scripts}

Using [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Ouvrir [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Mettez en commentaire la balise qui contient l’avatar pour un commentaire (~ ligne 21) :

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Ouvrir [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Mettez en commentaire la balise qui contient l’avatar pour la prochaine entrée de commentaire (~ ligne 44) :

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Select **Save All**

## Répliquer une application personnalisée {#replicate-custom-app}

Une fois l’application modifiée, il est nécessaire de reproduire à nouveau le composant personnalisé.

Une façon de le faire est

* Dans le menu principal

   * Sélectionnez **[!UICONTROL Outils > Opérations > Réplication.]**
   * Sélectionner `Activate Tree`
   * Définir `Start Path`: to `/apps/custom`
   * Décocher `Only Modified`
   * Sélectionner le `Activate` bouton

## Commentaire modifié de la Vue sur l&#39;exemple de page publié {#view-modified-comment-on-published-sample-page}

[En poursuivant l’expérience](extend-sample-page.md#publish-sample-page) sur l’instance de publication, toujours connectée en tant que même utilisateur, il est maintenant possible d’actualiser la page dans l’environnement de publication afin de vue la modification afin de supprimer l’avatar :

![chlimage_1-81](assets/chlimage_1-81.png)

## Exemple de package d&#39;extension de commentaire {#sample-comment-extension-package}

Vous trouverez ci-joint un package de l&#39;application de commentaires personnalisés créée dans ce didacticiel.

[Obtenir le fichier](assets/sample-comment-extension-6-1-fp3.zip)