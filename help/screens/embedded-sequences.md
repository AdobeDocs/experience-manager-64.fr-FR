---
title: Séquences incorporées
seo-title: Séquences incorporées
description: Suivez cette page pour en savoir plus sur les séquences incorporées pour les canaux qui permettent à l’utilisateur d’ajouter des composants dans le canal parent, et aussi de réutiliser le contenu d’un autre canal et de l’incorporer dans le canal parent.
seo-description: Suivez cette page pour en savoir plus sur les séquences incorporées pour les canaux qui permettent à l’utilisateur d’ajouter des composants dans le canal parent, et aussi de réutiliser le contenu d’un autre canal et de l’incorporer dans le canal parent.
uuid: 3ffbe937-6b60-4eea-acfb-633270b4ded3
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 76be4cc1-4b34-4f1d-b2d3-754a84105dec
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Séquences incorporées{#embedded-sequences}

Grâce aux ***Séquences incorporées*** pour les canaux, l’utilisateur peut ajouter des composants dans le canal parent, ainsi que réutiliser le contenu d’un autre canal et l’incorporer dans le canal parent.

## Ajout de séquences incorporées {#adding-embedded-sequences}

Vous avez la possibilité d’ajouter les composants suivants à votre canal de séquence :

* Séquence incorporée
* Séquence incorporée dynamique

>[!NOTE]
>
>Pour en savoir plus sur l’utilisation d’autres composants dans votre projet Screens, voir [Ajout de composants à un canal](/help/screens/adding-components-to-a-channel.md).

### Ajout d’une séquence incorporée    {#adding-an-embedded-sequence}

Vous pouvez ajouter une séquence incorporée à votre canal. Une séquence incorporée est un autre canal qui comprend des ressources telles que des images ou des vidéos. En ajoutant une séquence incorporée, l’utilisateur peut ajouter la séquence à un canal au niveau de ***Chemin du canal***.

>[!NOTE]
>
>***Chemin du canal ***définit une référence explicite au canal.
>
>Pour en savoir plus sur *Chemin du canal*, voir [Attribution de canaux](/help/screens/channel-assignment.md) dans la section Création dans Screens.

Suivez les étapes ci-dessous pour ajouter une séquence incorporée à votre canal :

1. Sélectionnez le canal où vous souhaitez incorporer une page. Par exemple, **We.Retail en magasin** > **Canaux** >* Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir le canal en mode édition.
1. Cliquez sur l’icône de composants sur la barre de gauche pour ajouter la page incorporée. Faites glisser et déposez la **séquence incorporée** dans l’éditeur.
1. Double-cliquez sur le composant **Séquence incorporée** pour ajouter le canal à votre canal de séquence d’origine.
1. Sélectionnez le **chemin du canal.**
1. Sélectionnez la **durée (ms)** de votre canal incorporé dans la **séquence**. Par défaut, la durée est définie sur **-1**, ce qui signifie que le canal incorporé est entièrement exécuté. Si l’utilisateur spécifie une durée, la séquence secondaire est interrompue (c’est-à-dire coupée) à l’heure indiquée.

1. Définissez la **Stratégie de lecture limitée** sur **normal**.

Par défaut, elle est définie sur **normal**. La définition de la valeur sur **normal*** (Lire tous les éléments)* signifie que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parente. L’autre valeur possible est **Lire un seul élément***, ce qui afficherait un seul élément de la séquence secondaire à chaque exécution (par exemple, le premier élément de la première boucle, le deuxième élément de la deuxième boucle, et ainsi de suite).

L’exemple suivant illustre l’ajout d’une séquence incorporée (**Canal inactif - Nuit**) à un canal existant (**Canal inactif**).

![new2](assets/new2.gif)

### Ajout d’une séquence incorporée dynamique {#adding-a-dynamic-embedded-sequence}

Vous pouvez ajouter une séquence incorporée dynamique à votre canal. Une séquence incorporée dynamique est semblable à une séquence incorporée, mais permet à l’utilisateur de suivre une hiérarchie où les modifications/mises à jour effectuées sur un canal sont propagées aux autres canaux liés. Il suit une hiérarchie parent-enfant et comprend également des ressources telles que des images ou des vidéos. L’ajout d’une séquence dynamique permet à l’utilisateur d’ajouter un canal au niveau du rôle de canal.

>[!NOTE]
>
>***Rôle de canal*** définit le contexte de l’affichage.
>
>Pour en savoir plus sur le *Rôle du canal*, voir [Attribution de canaux](/help/screens/channel-assignment.md) dans la section Création dans Screens.

Suivez les étapes ci-dessous pour ajouter une séquence incorporée à votre canal :

1. Sélectionnez le canal dans lequel vous voulez incorporer une séquence dynamique. Par exemple, **We.Retail en magasin** > **Canaux** > **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir le canal en mode édition.
1. Cliquez sur l’icône de composants sur la barre de gauche pour ajouter la séquence incorporée dynamique. Drag and drop the **Dynamic Embedded Sequence** to the editor.

1. Double-click the **Dynamic Embedded Sequence** component to add the page to your sequence channel.

1. Saisissez le **Rôle d’attribution de canaux**.
1. Définissez la **Stratégie de lecture limitée** sur **normal**. Par défaut, elle est définie sur **normal**. La définition de la valeur sur **normal*** (Lire tous les éléments)* signifie que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parente. The other possible value is **Play a single item** *(Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Sélectionnez la **durée (ms)** de l&#39;onglet **Séquence** votre canal incorporé dans la séquence.

![dernier](assets/latest.gif)

