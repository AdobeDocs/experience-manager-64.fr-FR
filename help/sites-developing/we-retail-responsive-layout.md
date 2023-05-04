---
title: Test d’une mise en page en responsive design dans We.Retail
seo-title: Trying out Responsive Layout in We.Retail
description: Test d’une mise en page en responsive design dans We.Retail
seo-description: null
uuid: d9613655-f54e-458f-9175-d07bb868f58b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 2d374e88-ea09-43d5-986c-5d77b0705b93
exl-id: ccb792f7-e837-4790-818f-e2c446328e71
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 74%

---

# Test d’une mise en page en responsive design dans We.Retail{#trying-out-responsive-layout-in-we-retail}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Toutes les pages We.Retail utilisent le composant Conteneur de mises en page pour implémenter le responsive design. Le conteneur offre un système de paragraphe qui permet de positionner des composants sur une grille réactive. Cette grille peut réorganiser la mise en page en fonction de l’appareil/de la taille de fenêtre et du format. Le composant est utilisé en mode **Mise en page** de l’éditeur de page, ce qui permet de créer et de modifier une mise en page en mode responsive design, selon les caractéristiques de l’appareil.

## Essayer de le faire {#trying-it-out}

1. Modifiez la page Arctic Surfing dans la section Expériences de la branche principale de langue.

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html

1. Passez à **Aperçu** pour voir la page telle qu’elle serait affichée pour un internaute. Faites défiler jusqu’au contenu de l’article *Esprit Aloha dans le nord de la Norvège*.

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Redimensionnez la fenêtre de votre navigateur et observez la mise en page s’adapter dynamiquement au redimensionnement.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Passez en mode Mise en page. La barre d’outils de l’émulateur s’affiche automatiquement, ce qui vous permet de planifier votre mise en page par appareil ciblé.

   La sélection d’un composant affiche des options de flottement et de masquage dans le menu d’édition, ainsi que des poignées de redimensionnement pour le composant.

   ![chlimage_1-180](assets/chlimage_1-180.png)

1. En saisissant et en faisant glisser la poignée de redimensionnement du composant, la grille de mise en page s’affiche automatiquement pour vous assister lors du redimensionnement.

   ![chlimage_1-181](assets/chlimage_1-181.png)

## Informations supplémentaires {#further-information}

Pour plus d’informations, reportez-vous au document relatif à la création [Mise en page en responsive design](/help/sites-authoring/responsive-layout.md) ou au document administrateur [Configuration du conteneur de mise en pages et du mode Mise en page](/help/sites-administering/configuring-responsive-layout.md) pour obtenir des détails techniques complets.
