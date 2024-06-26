---
title: Annotations lors de la modification d’une page
seo-title: Annotations when Editing a Page
description: De nombreux composants directement liés au contenu permettent d’ajouter une annotation.
seo-description: Many components directly related to content allow you to add an annotation
uuid: 157be55c-8ab8-472e-be32-0dcc02bfa41d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: aa89326a-ad33-4b0b-8d09-c68c5a5c790a
exl-id: 65e534ec-7f73-4333-b225-7adf082f66d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 57%

---

# Annotations lors de la modification d’une page{#annotations-when-editing-a-page}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’ajout de contenu aux pages de votre site web est souvent l’objet de discussions avant la publication réelle. Pour faciliter cette opération, de nombreux composants directement liés au contenu (par opposition, à la mise en page, par exemple) vous permettent d’ajouter une annotation.

Une annotation place une note autocollante colorée sur la page. L’annotation vous permet (ainsi qu’aux autres utilisateurs) de laisser des commentaires ou des questions à l’intention d’autres auteurs ou réviseurs.

>[!NOTE]
>
>La définition d’un type de composant individuel détermine s’il est possible d’ajouter une annotation sur des instances de ce composant.

>[!NOTE]
>
>Les annotations créées dans l’interface utilisateur classique s’affichent dans l’interface utilisateur tactile. Toutefois, les esquisses sont spécifiques à l’interface utilisateur et elles ne s’affichent que dans l’interface dans laquelle elles ont été créées.

>[!CAUTION]
>
>Si vous supprimez une ressource (un paragraphe, par exemple), toutes les annotations et tous les schémas associés sont également supprimés, quelle que soit leur position sur la page dans son ensemble.

>[!NOTE]
>
>Selon vos besoins, vous pouvez également développer un workflow pour envoyer des notifications lorsque celles-ci sont ajoutées, mises à jour ou supprimées.

## Annotations {#annotations}

Un [mode](/help/sites-authoring/author-environment-tools.md#page-modes) spécial est utilisé pour la création et l’affichage des annotations.

>[!NOTE]
>
>Pour rappel, des [commentaires](/help/sites-authoring/basic-handling.md#timeline) sont également disponibles pour fournir un retour d’informations sur une page.

>[!NOTE]
>
>Vous pouvez annoter un large éventail de ressources :
>
>* [Annotation de ressources](/help/assets/managing-assets-touch-ui.md#annotating)
>* [Annotation de ressources vidéo](/help/assets/managing-video-assets.md#annotating-video-assets)
>


### Annotation d’un composant {#annotating-a-component}

Le mode Annotation vous permet de créer, modifier, déplacer ou supprimer des annotations sur votre contenu :

1. Vous pouvez entrer en mode Annotation à l’aide de l’icône de la barre d’outils (en haut à droite) lors de la modification d’une page :

   ![](do-not-localize/screen_shot_2018-03-22at110414.png)

   Vous pouvez maintenant afficher les annotations existantes.

   >[!NOTE]
   >
   >Pour quitter le mode Annotation, appuyez/cliquez sur l’icône Annoter (symbole x) située à droite de la barre d’outils supérieure.

1. Cliquez/appuyez sur l’icône Ajouter une annotation (symbole plus à gauche de la barre d’outils) pour commencer à ajouter des annotations.

   >[!NOTE]
   >
   >Pour arrêter l’ajout d’annotations (et revenir à l’affichage), appuyez/cliquez sur l’icône Annuler (symbole x dans un cercle blanc) à gauche de la barre d’outils supérieure.

1. Cliquez/appuyez sur le composant requis (les composants pouvant être annotés sont mis en surbrillance avec une bordure bleue) pour ajouter l’annotation et ouvrir la boîte de dialogue :

   ![screen_shot_2018-03-22at110606](assets/screen_shot_2018-03-22at110606.png)

   Ici, vous pouvez utiliser le champ et/ou l’icône appropriés pour :

   * Saisissez le texte de l’annotation.
   * Créez une esquisse (traits et formes) pour mettre en surbrillance une zone du composant.

      Le curseur prend la forme d’une croix lorsque vous créez une esquisse. Vous pouvez tracer plusieurs lignes distinctes. La ligne d’esquisse reflète la couleur de l’annotation et peut être une flèche, un cercle ou un ovale.
   ![](do-not-localize/screen_shot_2018-03-22at110640.png)

   * Choisissez/changez la couleur :

   ![](do-not-localize/chlimage_1-19.png)

   * Supprimez l’annotation.

   ![](do-not-localize/screen_shot_2018-03-22at110647.png)

1. Pour fermer la boîte de dialogue de l’annotation, cliquez ou appuyez en dehors de la boîte de dialogue. Une vue tronquée (le premier mot) de l’annotation, ainsi que les schémas, s’affiche :

   ![screen_shot_2018-03-22at110850](assets/screen_shot_2018-03-22at110850.png)

1. Après avoir modifié une annotation, vous pouvez effectuer ce qui suit :

   * Cliquez ou appuyez sur le marqueur de texte pour ouvrir l’annotation. Une fois ouvert, vous pouvez afficher le texte intégral, apporter des modifications ou supprimer l’annotation.

      * Les schémas ne peuvent pas être supprimés indépendamment de l’annotation.
   * Repositionner la marque de texte.
   * Cliquez/appuyez sur un trait du schéma pour le sélectionner et le faire glisser jusqu’à la position voulue.
   * Déplacer ou copier un composant

      * Toutes les annotations associées et leurs schémas sont également déplacés ou copiés et leur position par rapport au paragraphe reste la même.


1. Pour quitter le mode Annotation et revenir au mode précédemment utilisé, appuyez/cliquez sur l’icône Annoter (symbole x) à droite de la barre d’outils supérieure.

>[!NOTE]
>Les annotations ne peuvent pas être ajoutées à une page verrouillée par un autre utilisateur.

### Indicateur d’annotations {#annotation-indicator}

Les annotations n’apparaissent pas en mode d’édition, mais le badge en haut à droite de la barre d’outils indique le nombre d’annotations figurant sur la page active. Le badge remplace l’icône Annotations par défaut ; il fonctionne comme un lien rapide pour activer/désactiver le mode Annotation :

![chlimage_1-242](assets/chlimage_1-242.png)
