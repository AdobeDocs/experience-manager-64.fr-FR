---
title: Modification de l’aspect
seo-title: Alter the Appearance
description: Modification du script
seo-description: Modify the script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 5%

---

# Modification de l’aspect {#alter-the-appearance}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Modification du script {#modify-the-script}

Le script comment.hbs est chargé de créer le HTML global de chaque commentaire.

Pour ne pas afficher l’avatar en regard de chaque commentaire publié :

1. Copier `comment.hbs`de `libs`to `apps`
   1. Sélectionner `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Sélectionnez **[!UICONTROL Copie]**
   1. Sélectionner `/apps/social/commons/components/hbs/comments/comment`
   1. Sélectionner **[!UICONTROL Coller]**
1. Ouvrir le recouvert `comment.hbs`
   * Double-cliquez sur le noeud  `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
1. Recherchez les lignes suivantes et supprimez-les ou mettez-les en commentaire :

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

Supprimez les lignes ou entourez-les de &quot;&lt;!>—&#39; et &#39;—>&#39; pour les commenter. En outre, les caractères &quot;xxx&quot; sont ajoutés comme indicateur visuel de l’emplacement de l’avatar.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Réplication de la superposition {#replicate-the-overlay}

Poussez le composant de commentaires superposés vers l’instance de publication à l’aide de l’outil de réplication.

>[!NOTE]
>
>Une forme de réplication plus robuste serait de créer un package dans le gestionnaire de modules et [activate](../../help/sites-administering/package-manager.md#replicating-packages) c&#39;est le cas. Un package peut être exporté et archivé.

Dans la navigation globale, sélectionnez **[!UICONTROL Outils > Déploiement > Réplication]** puis **[!UICONTROL Activer l’arborescence]**.

Pour le champ Chemin de début , saisissez `/apps/social/commons` et sélectionnez **[!UICONTROL Activer]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Affichage des résultats {#view-results}

Si vous vous connectez à l’instance de publication en tant qu’administrateur, par exemple http://localhost:4503/crx/de en tant qu’administrateur/administrateur, vous pouvez vérifier que les composants superposés sont présents.

Si vous vous déconnectez et vous reconnectez en tant que `aaron.mcdonald@mailinator.com/password` et actualisez la page. Vous remarquerez que le commentaire publié ne s’affiche plus avec un avatar, mais avec un simple &quot;xxx&quot;.

![chlimage_1-43](assets/chlimage_1-43.png)
