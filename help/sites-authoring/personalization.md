---
title: Personnalisation et ciblage de contenu
seo-title: Personalization and Content Targeting
description: Découvrez comment AEM peut créer du contenu personnalisé
seo-description: Learn how AEM can create personalized content
uuid: 3a1aaa3d-5f57-4fb7-a4be-523f0d274b79
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 850da0da-f7c3-4dd7-bb06-404c14a2a791
exl-id: 669e2509-e563-46ff-b01c-3f05ec196df5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 61%

---

# Personnalisation et ciblage de contenu {#personalization}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Personnalisation et ciblage de contenu {#personalization-and-content-targeting}

AEM propose un ensemble d’outils permettant de créer du contenu ciblé et de présenter des expériences personnalisées.

## Mode Ciblage {#targeting-mode}

[Créez du contenu ciblé à l’aide du mode Ciblage d’AEM. ](/help/sites-authoring/content-targeting-touch.md) Le mode Ciblage et le composant Cible fournissent des outils permettant de créer du contenu pour les expériences de vos activités de marketing.

## Activités {#activities}

Les activités définissent et organisent vos efforts marketing. Les activités comprennent les audiences que vous ciblez et la période pendant laquelle le ciblage est appliqué.

Par exemple, le catalogue de produits We.Retail inclut des teasers qui attirent l’attention sur les produits saisonniers. L’activité de sports d’été définit les segments de marketing que les teasers ciblent pendant les mois d’été.

Les activités identifient également la variable [moteur de ciblage](/help/sites-authoring/personalization.md#targeting-engine) que vos pages utilisent.

Utilisez la [console Activités](/help/sites-authoring/activitylib.md) pour créer et gérer les activités de vos marques. Vous pouvez également créer des activités tout en [créant du contenu ciblé](/help/sites-authoring/content-targeting-touch.md).

## Expériences {#experiences}

Pour chaque activité, vous définissez une ou plusieurs expériences qui identifient les audiences que vous ciblez. AEM vous permet de contrôler le contenu qui constitue chaque expérience.

Les audiences sont basées sur les segments de marketing créés dans AEM ou Adobe Target. Lorsqu’un visiteur ouvre une page web, la logique de page détermine l’audience à laquelle il appartient et affiche le contenu que vous avez créé pour cette audience.

Par exemple, une activité définit les expériences destinées à deux audiences distinctes : les femmes âgées de moins de 30 ans et les femmes âgées de plus de 30 ans. La page Femmes du site web We.Retail affiche différents produits pour chaque expérience.

Vous définissez des expériences pour une activité. Vous pouvez utiliser la variable [Console Activités](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) ou [Mode Ciblage](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) pour ajouter des expériences à une activité.

## Offres {#offers}

Une offre est un contenu qui s’affiche à un emplacement sur une page pour une expérience. Utilisez différentes offres pour différentes expériences afin d’optimiser l’efficacité du contenu pour vos audiences.

Par exemple, la page pour les femmes de l’exemple We.Retail peut utiliser des offres en tant qu’image de teaser apparaissant en haut de la page. L’offre utilisée en tant que teaser de l’expérience destinée aux femmes de plus de 30 ans n’est pas la même que celle utilisée pour les femmes de moins de 30 ans.

Utilisez la variable [Console Offres](/help/sites-authoring/offerlib.md) pour créer des offres que vous pouvez utiliser dans plusieurs expériences. Créez des offres à usage unique ou ajoutez des offres à partir d’une bibliothèque d’offres lors de la [création de contenu ciblé](/help/sites-authoring/content-targeting-touch.md).

## Moteur de ciblage {#targeting-engine}

Le moteur de ciblage est le mécanisme qui oriente la logique du contenu ciblé. Les [activités](/help/sites-authoring/activitylib.md) sont configurées pour utiliser l’un des deux moteurs de ciblage disponibles : AEM et Adobe Target.

### AEM {#aem}

AEM fournit un moteur de ciblage intégré qui traite les requêtes de page et détermine le contenu à afficher. Lorsque vous utilisez le moteur de ciblage AEM, vous êtes limité(e) aux segments créés dans AEM pour définir les audiences de vos expériences.

### Adobe Target {#adobe-target}

Avec le moteur de ciblage Adobe Target, les informations recueillies suite aux visites de page font l’objet d’un suivi dans Adobe Target.

* Avec ce moteur de ciblage, vous utilisez les segments que vous importez à partir d’Adobe Target pour définir les audiences de vos expériences.
* Les activités qui utilisent le moteur Adobe Target sont les suivantes : [synchronisé avec Target](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target).

Vous pouvez utiliser ce moteur lorsque vous avez [intégré Adobe Target](/help/sites-administering/opt-in.md).
