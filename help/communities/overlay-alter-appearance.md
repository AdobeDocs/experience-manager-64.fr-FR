---
title: Modification de l’aspect
seo-title: Modification de l’aspect
description: Modification du script
seo-description: Modification du script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
translation-type: tm+mt
source-git-commit: 1ae2d7f99286e0b958d343778159e2d35095510e
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 1%

---


# Modification de l’aspect {#alter-the-appearance}

## Modification du script {#modify-the-script}

Le script comment.hbs est responsable de la création du code HTML global pour chaque commentaire.

Pour ne pas afficher l’avatar en regard de chaque commentaire publié :

1. Copier `comment.hbs`de `libs`vers `apps`
   1. Sélectionner `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Sélectionner une **[!UICONTROL copie]**
   1. Sélectionner `/apps/social/commons/components/hbs/comments/comment`
   1. Sélectionner **[!UICONTROL Coller]**
1. Ouvrir le recouvrement `comment.hbs`
   * Doublon-clic sur le noeud `comment.hbs`dans `/apps/social/commons/components/hbs/comments/comment folder`
1. Recherchez les lignes suivantes et supprimez-les ou placez-les en commentaire :

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

Supprimez les lignes ou entourez-les de &#39;&lt; !—&#39; et &#39;—>&#39; pour les commenter. En outre, les caractères &#39;xxx&#39; sont ajoutés comme indicateur visuel de l&#39;endroit où l&#39;avatar aurait été.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Réplication de l’incrustation {#replicate-the-overlay}

Poussez le composant de commentaires superposés sur l’instance de publication à l’aide de l’outil de réplication.

>[!NOTE]
>
>Une forme de réplication plus robuste consisterait à créer un package dans Package Manager et à l’ [activer](../../help/sites-administering/package-manager.md#replicating-packages) . Un package peut être exporté et archivé.

Dans la navigation globale, sélectionnez **[!UICONTROL Outils > Déploiement > Réplication]** , puis **[!UICONTROL activer l’arborescence]**.

Pour le chemin d’accès au Début, saisissez `/apps/social/commons` et sélectionnez **[!UICONTROL Activer]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Résultats de la Vue {#view-results}

Si vous vous connectez à l’instance de publication en tant qu’administrateur (http://localhost:4503/crx/de en tant qu’administrateur/administrateur, par exemple), vous pouvez vérifier que les composants superposés sont bien présents.

Si vous vous déconnectez et vous vous reconnectez en tant que `aaron.mcdonald@mailinator.com/password` et actualisez la page, vous constaterez que le commentaire publié ne s’affiche plus avec un avatar, mais un simple &quot;xxx&quot; s’affiche.

![chlimage_1-43](assets/chlimage_1-43.png)

