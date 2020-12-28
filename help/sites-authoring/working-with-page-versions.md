---
title: Utilisation des versions de page
seo-title: Utilisation des versions de page
description: Création, comparaison et restauration des versions d’une page
seo-description: Création, comparaison et restauration des versions d’une page
uuid: b0328431-c2cf-48f4-b358-261238338241
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: fa331c03-5587-452d-ab96-ac2926ae0da3
translation-type: tm+mt
source-git-commit: 98fae2d51d73bda946f3c398e9276fe4d5a8a0fe
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 96%

---


# Utilisation des versions de page{#working-with-page-versions}

Le contrôle de version permet de créer un « instantané » d’une page à un moment donné. Avec le contrôle de version, vous pouvez effectuer les opérations suivantes :

* Créer une version d’une page donnée.
* Restaurer la version précédente d’une page (pour annuler une modification apportée à une page, par exemple).
* Comparer la version actuelle d’une page avec une version précédente (les différences dans le texte et les images sont mises en évidence).

## Création d’une version    {#creating-a-new-version}

Vous pouvez créer une version de votre ressource depuis :

* le [rail de la frise chronologique](#creating-a-new-version-timeline)
* l’option [Créer](#creating-a-new-version-create-with-a-selected-resource) (lorsqu’une ressource est sélectionnée).

### Création d’une version - Frise chronologique{#creating-a-new-version-timeline}

1. Accédez à la page pour laquelle créer une version.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Frise chronologique**.
1. Cliquez ou appuyez sur la tête de la flèche près du champ de commentaire pour afficher les options :

   ![screen_shot_2018-03-21at155035](assets/screen_shot_2018-03-21at155035.png)

1. Sélectionnez **Enregistrer comme version**.
1. Saisissez un **libellé** et un **commentaire** si nécessaire.

   ![chlimage_1-398](assets/chlimage_1-398.png)

1. Confirmez la nouvelle version avec l’option **Créer**.

   Les informations dans la frise chronologique sont mises à jour pour indiquer la nouvelle version.

### Création d’une version - Création avec une ressource sélectionnée {#creating-a-new-version-create-with-a-selected-resource}

1. Accédez à la page pour laquelle créer une version.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Sélectionnez l’option **Créer** dans la barre d’outils.
1. Une boîte de dialogue s’ouvre. Vous pouvez saisir un **libellé** et un **commentaire** si nécessaire:

   ![screen_shot_2012-02-15at105050am](assets/screen_shot_2012-02-15at105050am.png)

1. Confirmez la nouvelle version avec l’option **Créer**.

   La frise chronologique s’ouvrira avec les informations mises à jour afin d’indiquer la nouvelle version.

## Restauration de la version d’une page {#reverting-to-a-page-version}

Une fois une version créée, vous pouvez y revenir si nécessaire.

>[!NOTE]
>
>Lors de la restauration d’une page, la version créée fait partie d’une nouvelle branche.
>
>Illustration :
>
>* Créez des versions d’une page.
>* Les libellés et les noms de nœud de version initiaux sont 1.0, 1.1, 1.2, etc.
>* Restaurez la première version, soit 1.0.
>* Recréez des versions.
>* Les libellés et les noms de nœud générés sont à présent 1.0.0, 1.0.1, 1.0.2, etc.

>



Pour restaurer une ancienne version, procédez comme suit :

1. Naviguez pour afficher la page pour laquelle restaurer une ancienne version.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**. Les versions de la page sélectionnée sont répertoriées.
1. Sélectionnez la version à restaurer. Les options possibles s’affichent :

   ![screen_shot_2018-03-21at155246](assets/screen_shot_2018-03-21at155246.png)

1. Sélectionnez **Revenir à cette version**. La version sélectionnée est restaurée et les informations dans la frise chronologique sont mises à jour.

## Aperçu d’une version    {#previewing-a-version}

Vous pouvez prévisualiser une version spécifique :

1. Accédez à la page à comparer.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**.
1. Les versions de la page sont répertoriées. Sélectionnez la version à prévisualiser :

   ![screen_shot_2018-03-21at155330](assets/screen_shot_2018-03-21at155330.png)

1. Sélectionnez **Aperçu**. La page sera affichée sous un nouvel onglet.

   >[!CAUTION]
   >
   >Si une page a été déplacée, vous ne pouvez plus afficher l’aperçu des versions antérieures au déplacement.
   >
   >Si vous rencontrez des problèmes avec un aperçu, vérifiez dans la [chronologie](/help/sites-authoring/basic-handling.md#timeline) si la page a été déplacée.

## Comparaison d’une ancienne version avec la page actuelle {#comparing-a-version-with-current-page}

Pour comparer la version actuelle de la page avec une version précédente :

1. Accédez à la page à comparer.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**.
1. Les versions de la page sont répertoriées. Sélectionnez la version à comparer :

   ![screen_shot_2018-03-21at155330](assets/screen_shot_2018-03-21at155330.png)

1. Sélectionnez **Comparer à actuel**. L’[outil de comparaison des pages](/help/sites-authoring/page-diff.md) s’ouvre et affiche les différences.

## Distorsion du temps Timewarp   {#timewarp}

La fonction de distorsion du temps Timewarp permet de simuler l’état *publié* d’une page à des moments spécifiques dans le passé.

L’objectif est de vous permettre d’effectuer le suivi d’un site web publié au moment sélectionné. Cette fonction utilise les versions de page pour déterminer l’état de l’environnement de publication.

Pour ce faire :

* Le système recherche la version de page qui était active à l’heure sélectionnée.
* Cela signifie que la version affichée a été créée/activée *avant* le moment sélectionné dans Timewarp.
* Si vous accédez à une page qui a été supprimée, celle-ci est également affichée, à condition toutefois que les anciennes versions de la page soient toujours disponibles dans le référentiel.
* Si aucune version publiée n’a été trouvée, la fonction Timewarp revient à l’état actuel de la page dans l’environnement de création (et ce, afin d’éviter une erreur/page 404, ce qui rendrait impossible toute poursuite de la navigation).

### Utilisation de Timewarp {#using-timewarp}

Timewarp est un [mode](/help/sites-authoring/author-environment-tools.md#page-modes) de l’éditeur de page. Son lancement est semblable à celui de n’importe quel autre mode.

1. Démarrez l’éditeur de la page à l’endroit où vous souhaitez lancer la fonction Timewarp, puis sélectionnez **Timewarp** dans la sélection du mode.

   ![screen_shot_2018-03-21at155416](assets/screen_shot_2018-03-21at155416.png)

1. Dans la boîte de dialogue, définissez une date et une heure cibles, puis cliquez ou appuyez sur **Définir la date**. Si vous ne sélectionnez pas d’heure, l’heure actuelle est utilisée par défaut.

   ![screen_shot_2018-03-21at155513](assets/screen_shot_2018-03-21at155513.png)

1. La page s’affiche en fonction de la date définie. Le mode Timewarp est indiqué par la barre d’état bleue située dans la partie supérieure de la fenêtre. Utilisez les liens de la barre d’état pour sélectionner une nouvelle date cible ou quitter le mode Timewarp.

   ![screen_shot_2018-03-21at155544](assets/screen_shot_2018-03-21at155544.png)

### Limites du mode Timewarp

Timewarp s’efforce de reproduire au mieux une page à un moment donné. Toutefois, en raison de la complexité de la création continue de contenu dans AEM, cela n’est pas toujours possible. Ces restrictions doivent être prises en compte lors de l’utilisation de Timewarp.

* **Timewarp fonctionne sur la base de pages publiées** : toutes les fonctionnalités de Timewarp ne sont disponibles que si vous avez publié la page précédemment. Dans le cas contraire, Timewarp affiche la page en cours dans l’environnement de création.
* **Timewarp utilise des versions de page** : si vous accédez à une page qui a été supprimée du référentiel, elle s’affiche correctement si d’anciennes versions sont toujours disponibles dans le référentiel.
* **Les versions supprimées affectent Timewarp** : si des versions sont supprimées du référentiel, Timewarp n’est pas en mesure d’afficher la vue correcte.
* **Timewarp est en lecture seule** : vous ne pouvez pas modifier l’ancienne version de la page. Elle est disponible uniquement à des fins d’affichage. Si vous souhaitez restaurer l’ancienne version, vous devrez procéder manuellement à l’aide de la fonction Restaurer.
* **Timewarp est basé uniquement sur le contenu de page** : si des éléments destinés au rendu du site web (tels que du code, des feuilles css, des ressources/images, etc.) ont été modifiés, la vue sera différente de ce qu’elle était initialement, étant donné que ces éléments n’ont pas de suivi de version dans le référentiel.

>[!CAUTION]
>
>Timewarp est conçu comme un outil permettant aux auteurs de comprendre et de créer leur contenu. Il ne s’agit pas d’un journal d’audit et il n’est pas destiné à des fins juridiques.