---
title: Création et gestion d’une Live Copy
seo-title: Gestion des Live Copies
description: Cette page décrit la création et la gestion des Live Copies des canaux.
seo-description: Utilisez les informations de cette page pour créer la Live Copy d’un canal, afficher les propriétés, vérifier l’état et propager les modifications d’un canal à sa Live Copy.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Création et gestion d’une Live Copy{#creating-and-managing-a-live-copy}

Cette page décrit la création et la gestion des Live Copies des canaux.

Une ***Live Copy*** est une copie du contenu spécifique d’un site pour laquelle une relation directe avec la source d’origine est conservée. Ces relations en direct permettent à la Live Copy d’hériter des propriétés du contenu et de la page de la source.

Cette page décrit la création d’une Live Copy d’un canal, l’affichage des propriétés, la vérification de l’état et la propagation des modifications d’un canal à sa Live Copy.

>[!NOTE]
>
>To learn more about Live Copy Sources and Blueprint Configurations, see [MSM Best Practices](/help/sites-administering/msm-best-practices.md).

## Création d’une Live Copy {#creating-a-live-copy}

Procédez comme suit pour créer la Live Copy d’un canal dans le dossier de votre projet.

1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis **Screens**. Alternatively, you can ﻿go directly to: [http://localhost:4502/screens.html/content/screens](http://localhost:4502/screens.html/content/screens).

1. Accédez au projet Screens, puis cliquez sur **Canaux**.
1. Cliquez sur **Créer**, puis sélectionnez **Live Copy** pour créer une Live Copy du canal.

1. Sélectionnez la destination, puis cliquez sur **Suivant**.
1. Sélectionnez l’emplacement de la Live Copy.
1. Saisissez le **Titre** et le **Nom** dans la page **Créer une Live Copy**.

1. Cliquez sur **Ouvrir** pour afficher le contenu de la nouvelle Live Copy ou sur **Terminé** pour revenir à la page principale.

Sinon, suivez les étapes ci-dessous pour obtenir une représentation visuelle de la création de la Live Copy d’un canal.

L’exemple suivant illustre la création d’une Live Copy (***IdleLiveCopy***) pour le ***Canal inactif***, dont le dossier de destination est ***Canaux***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Affichage du contenu du canal de Live Copy {#viewing-content-of-the-live-copy-channel}

Une Live Copy est une copie d’un canal qui existe déjà.

Pour afficher le contenu de la Live Copy, procédez comme suit :

1. Accédez au projet Screens et cliquez sur l’emplacement dans lequel vous avez créé la Live Copy comme indiqué dans la section ci-dessus. (Ici, l’emplacement qui a été sélectionné est le dossier **Canaux**)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Cliquez sur le bouton **Modifier** de la barre d’actions pour afficher le contenu du canal.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Lors de la consultation du contenu d’un canal de Live Copy, un élément supplémentaire apparaît dans le menu : **État de Live Copy**. Voir la section ci-dessous pour plus de détails.

### Affichage des propriétés d’une Live Copy      {#viewing-properties-of-a-live-copy}

En outre, vous pouvez afficher les propriétés du canal de Live Copy.

1. Accédez au canal de Live Copy et cliquez sur **Propriétés** dans la barre d’actions.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Sélectionnez l’onglet **Live Copy** pour afficher les détails du canal.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### État de Live Copy {#live-copy-status}

Le mode **État de la Live Copy**, comme illustré ci-dessous, permet d’afficher l’état des relations de tous les éléments du canal.

1. Cliquez sur **Modifier** pour sélectionner **État de Live Copy** et afficher l’association du contenu de votre canal avec le canal d’origine (à partir duquel la Live Copy est générée).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Sélectionnez **État de Live Copy** pour afficher l’aperçu de la page.

   Lorsque les ressources comportent une bordure verte, cela signifie que le contenu est hérité du canal d’origine.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Rupture de l’héritage {#breaking-the-inheritance}

Vous pouvez également annuler l’héritage de la Live Copy. Le contenu devient alors indépendant de la branche d’origine.

L’exemple suivant montre que vous sélectionnez l’image en mode Modifier et cliquez sur le symbole d’annulation de l’héritage dans l’angle supérieur droit.

![chlimage_1-24](assets/chlimage_1-24.png)

### Propagation des modifications au canal de Live Copy {#propagating-changes-to-the-live-copy-channel}

Si vous apportez des modifications/mises à jour au canal d’origine, vous devez également les propager à votre canal de Live Copy.

Procédez comme suit pour vous assurer que les modifications sont propagées du canal d’origine au canal de Live Copy :

1. Sélectionnez le canal d’origine (***Idle Channel***) et cliquez sur **Modifier** dans la barre d’actions.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Apportez des modifications au contenu de ce canal. Par exemple, supprimez une image de ce canal.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Sélectionnez la Live Copy du canal (***IdleLiveCopy***) et cliquez sur le bouton **Modifier** de la barre d’actions. Vous remarquerez que l’image que vous avez supprimée est toujours visible dans la Live Copy.

   Pour propager les modifications, vous devez synchroniser le canal.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Pour propager les modifications au canal de Live Copy, accédez au tableau de bord AEM et choisissez le canal de Live Copy, puis cliquez sur **Propriétés** dans la barre d’actions.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Sélectionnez l’onglet **Live Copy**, puis cliquez sur **Synchroniser** dans la barre d’actions.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Cliquez sur **Synchronisation** pour confirmer les modifications. Cliquez sur **Enregistrer et fermer** pour revenir au tableau de bord AEM.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Vous remarquerez que l’image est désormais également supprimée du canal de Live Copy.

