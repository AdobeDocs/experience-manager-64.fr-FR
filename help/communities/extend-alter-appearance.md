---
title: Modification de l’aspect (HBS)
seo-title: Alter the Appearance
description: Modification des scripts HBS
seo-description: Modify the HBS scripts
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 4%

---

# Modification de l’aspect (HBS) {#alter-the-appearance-hbs}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Maintenant que les composants du système de commentaires personnalisé dans le répertoire de l’application (/apps) sont en place, avec un resourceSuperType référençant le système de commentaires par défaut et le modèle/affichage personnalisé enregistré, il est possible de modifier l’implémentation.

Pour une démonstration simple, l’avatar affiché pour l’utilisateur connecté qui publie un commentaire est supprimé.

>[!NOTE]
>
>Pour utiliser l’extension , l’instance du système de commentaires d’un site web à affecter (/content) doit définir son resourceType comme système de commentaires personnalisé.

## Modification des scripts HBS {#modify-the-hbs-scripts}

Utilisation [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Ouvrir [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Commentez la balise qui contient l’avatar d’une publication de commentaire (~ ligne 21) :

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

* Sélectionnez **Enregistrer tout**

## Répliquer une application personnalisée {#replicate-custom-app}

Une fois l’application modifiée, il est nécessaire de répliquer à nouveau le composant personnalisé.

Pour ce faire, une méthode consiste à

* À partir du menu principal

   * Sélectionner **[!UICONTROL Outils > Opérations > Réplication]**
   * Sélectionner `Activate Tree`
   * Définir `Start Path`: to `/apps/custom`
   * Décocher `Only Modified`
   * Sélectionner `Activate` button

## Afficher le commentaire modifié sur l’exemple de page publié {#view-modified-comment-on-published-sample-page}

[Continuer l’expérience](extend-sample-page.md#publish-sample-page) sur l’instance de publication, toujours connecté en tant que même utilisateur, il est désormais possible d’actualiser la page dans l’environnement de publication pour afficher la modification afin de supprimer l’avatar :

![chlimage_1-81](assets/chlimage_1-81.png)

## Exemple de module d’extension de commentaire {#sample-comment-extension-package}

Vous trouverez ci-joint un package de l’application de commentaires personnalisés créée dans ce tutoriel.

[Obtenir le fichier](assets/sample-comment-extension-6-1-fp3.zip)
