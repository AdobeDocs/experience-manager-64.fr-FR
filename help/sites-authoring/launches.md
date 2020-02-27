---
title: Présentation des lancements
seo-title: Présentation des lancements
description: La fonction Lancements permet de développer efficacement du contenu en vue d’une publication ultérieure. Les lancements permettent de préparer les modifications pour une publication à venir, tout en conservant vos pages actuelles.
seo-description: La fonction Lancements permet de développer efficacement du contenu en vue d’une publication ultérieure. Les lancements permettent de préparer les modifications pour une publication à venir, tout en conservant vos pages actuelles.
uuid: ff6a2898-7a77-4315-bb1f-efa9caa5f3b2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: a7ec190d-056e-4fc9-8f2d-f4164273674d
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Présentation des lancements{#launches}

La fonction Lancements permet de développer efficacement du contenu en vue d’une publication ultérieure.

Le lancement vous permet de préparer des modifications en vue d’une publication future (tout en conservant vos pages actives). Une fois vos modifications apportées aux pages de lancement, vous devez les convertir de nouveau en pages source, puis activer ces dernières (au niveau supérieur). L’opération de conversion duplique le contenu de lancement sur les pages source et peut être appliquée manuellement ou automatiquement (selon les champs définis lors de la création et de la modification du lancement).

Par exemple, les pages de produits saisonniers de votre boutique en ligne sont mises à jour tous les trimestres, de telle sorte que les offres spéciales soient en phase avec la saison. Pour préparer la prochaine mise à jour trimestrielle, vous pouvez créer un lancement des pages web en question. Pendant tout le trimestre, les modifications suivantes sont accumulées dans la copie de lancement :

* Modifications apportées aux pages source dans le cadre des tâches de maintenance normales. Ces modifications sont automatiquement dupliquées dans les pages de lancement.
* Modifications effectuées directement sur les pages de lancement en vue du prochain trimestre.

À l’approche du trimestre suivant, vous convertissez les pages de lancement pour pouvoir modifier les pages source (contenant le contenu mis à jour). Vous pouvez convertir toutes les pages ou uniquement celles que vous avez modifiées. 

Les lancements peuvent également être :

* Créés pour plusieurs branches racine. Même si vous pouvez créer un lancement pour le site dans son intégralité (et y apporter des modifications), cette méthode n’est pas pratique puisque l’ensemble du site doit être copié. Lorsque des centaines, voire des milliers, de pages sont utilisées, les configurations et les performances du système dépendent de l’action de copie et ultérieurement des comparaisons nécessaires pour les tâches de conversion.
* Imbriqués (un lancement dans un lancement). Vous pouvez ainsi créer un lancement à partir d’un lancement existant pour que les développeurs de contenu exploitent les modifications déjà apportées, au lieu de répercuter ces mêmes modifications à plusieurs reprises pour chaque lancement.

Cette section explique comment créer, modifier et convertir (et, le cas échéant, [supprimer](/help/sites-authoring/launches-creating.md#deleting-a-launch)) les pages de lancement de la console Sites ou de la console [Lancements](#the-launches-console) :

* [Création de lancements](/help/sites-authoring/launches-creating.md)
* [Modification de lancements](/help/sites-authoring/launches-editing.md)
* [Conversion de lancements](/help/sites-authoring/launches-promoting.md)

## Lancements - Ordre des événements {#launches-the-order-of-events}

La fonction Lancements vous permet de développer efficacement le contenu en vue d’une publication future d’une ou de plusieurs pages web activées.

La fonction Lancements vous permet de :

* Créez une copie de vos pages source :

   * La copie est votre lancement.
   * Les pages source de niveau supérieur sont connues sous le nom de **Production**.

      * Les pages source peuvent être extraites de plusieurs branches (distinctes).
   >[!CAUTION]
   >
   >Dans l’interface utilisateur classique, il n’est pas possible d’utiliser plusieurs branches sources pour un lancement.

   ![chlimage_1-233](assets/chlimage_1-233.png)

* Modifier la configuration de lancement :

   * Ajoutez ou supprimez des pages et/ou des branches vers/à partir du lancement.
   * Modifiez les propriétés de lancement telles que **Titre**, **Date de lancement** et l’indicateur **Prêt pour la production**.

* Vous pouvez convertir et modifier le contenu manuellement ou automatiquement :

   * Manuellement :

      * Convertissez votre contenu de lancement en **Cible** (pages source) lorsqu’il est prêt à être publié.
      * Modifiez le contenu des pages source (après les avoir à nouveau converties).
      * Convertissez toutes les pages ou uniquement celles qui ont été modifiées.
   * Automatiquement, ce qui implique les étapes suivantes : 

      * Le champ **Date de** **lancement** (**En direct**) : ce paramètre peut être défini lors de la création ou de la modification d’un lancement.
      * L’indicateur **Prêt pour la production** : cette option n’est sélectionnable que lors de la modification d’un lancement.
      * Si l’indicateur **Prêt pour la production** est défini, le lancement sera automatiquement converti en pages de production à la date de **lancement** (**En direct**) spécifiée ****. Après la promotion, les pages de production sont automatiquement publiées.

         Si aucune date n’a été définie, l’indicateur n’a aucun effet.


* Mettez à jour vos pages source et de lancement en parallèle :

   * Les modifications apportées aux pages source sont automatiquement appliquées à la copie de lancement (si elle a été configurée avec un héritage, c’est-à-dire comme Live Copy). 
   * Les modifications apportées à la copie de lancement peuvent l’être sans interrompre les mises à jour automatiques ou modifier les pages source. 
   ![chlimage_1-234](assets/chlimage_1-234.png)

* [Créer un lancement imbriqué](/help/sites-authoring/launches-creating.md#creating-a-nested-launch) (lancement dans un lancement) :

   * La source est un lancement existant.
   * Vous pouvez [promouvoir un lancement imbriqué](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch) dans n’importe quelle cible. Il peut s’agir d’un lancement parent ou des pages source de niveau supérieur (production).
   ![chlimage_1-235](assets/chlimage_1-235.png)

   >[!CAUTION]
   >
   >La suppression d’un lancement supprime le lancement lui-même et tous les lancements imbriqués qui en sont des descendants.

>[!NOTE]
>
>Creating and editing launches requires access rights to `/content/launches` - as with the default group `content-authors`.
>
>Si vous rencontrez des difficultés, contactez votre administrateur système. 

### Console de lancements {#the-launches-console}

La console de lancements fournit un aperçu de vos lancements et permet d’appliquer des actions sur les lancements répertoriés. Vous pouvez accéder à la console via :

* La console **Outils** : **Outils**, **Sites**, **Lancements**.

* Ou directement avec [http://localhost:4502/libs/launches/content/launches.html](http://localhost:4502/libs/launches/content/launches.html)

## Lancements dans les références (console de sites) {#launches-in-references-sites-console}

1. Dans la console **Sites**, accédez à la source des lancements.
1. Ouvrez le rail **Références** et sélectionnez la page source.
1. Sélectionnez **Lancements**. Les lancements existants seront répertoriés :

   ![chlimage_1-236](assets/chlimage_1-236.png)

1. Appuyez/cliquez sur le lancement qui vous intéresse. La liste des actions possibles s’affiche :

   ![chlimage_1-237](assets/chlimage_1-237.png)

