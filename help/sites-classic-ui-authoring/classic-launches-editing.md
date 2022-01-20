---
title: Modification de lancements
seo-title: Editing Launches
description: Après avoir créé un lancement pour une page (ou un jeu de pages), vous pouvez modifier le contenu dans la copie de lancement correspondante.
seo-description: When a launch has been created for a page (or set of pages) you can edit the content in the launch copy of the page(s).
uuid: 3a310eeb-553d-4d2b-98b5-c5bc523b2aca
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 666b967a-e94b-4f94-a676-00adf150580f
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 98bccd13-431a-4cba-bb93-75cdcc98830a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 100%

---

# Modification de lancements{#editing-launches}

## Modification de pages de lancement {#editing-launch-pages}

Après avoir créé un lancement pour une page (ou un jeu de pages), vous pouvez modifier le contenu dans la copie de lancement correspondante.

1. Ouvrez la page à modifier.
1. Dans le sidekick, sélectionnez l’onglet **Création de versions**, puis développez le groupe **Lancements**. Le titre du lancement en cours d’édition est indiqué en caractères gras.

   ![chlimage_1-13](assets/chlimage_1-13.jpeg)

1. Sélectionnez le lancement à traiter, puis cliquez sur **Permuter**.
1. Commencez vos modifications.

   >[!NOTE]
   >
   >Vous pouvez utiliser l’onglet **Page** du sidekick pour effectuer des actions telles que **Créer une page enfant**, entre autres. 

## Modification d’une configuration de lancement {#editing-a-launch-configuration}

Après avoir créé un lancement, vous pouvez en modifier le nom et la date. Vous pouvez également indiquer une image à associer au lancement.

1. Ouvrez la page d’administration des lancements ([http://localhost:4502/libs/launches/content/admin.html](http://localhost:4502/libs/launches/content/admin.html)).

1. Sélectionnez le lancement requis et cliquez sur **Modifier** pour ouvrir la boîte de dialogue :

   * Dans l’onglet **Général**, vous pouvez modifier les éléments suivants :

      * **Titre**
      * **Date de mise en service** : ceci équivaut à la date de lancement 
      * **Prêt pour la production**

      Reportez-vous à [Lancements - Ordre des événements](/help/sites-authoring/launches.md#launches-the-order-of-events) pour obtenir des informations sur l’objectif et l’interaction de ces champs.

   * Dans l’onglet **Image**, vous pouvez télécharger un fichier d’image.


1. Cliquez sur **Enregistrer**.

## Identification du statut de lancement d’une page {#discovering-the-launch-status-of-a-page}

Lorsque vous modifiez le lancement d’une page, les informations sur le lancement s’affichent au bas de l’onglet **Création de versions** du sidekick :

* Nom du lancement
* Temps écoulé depuis la dernière modification
* Utilisateur ayant effectué la dernière modification
* L’état de l’indicateur **Prêt pour la production** (orange=non défini ; vert=défini).

![chlimage_1-186](assets/chlimage_1-186.png)
