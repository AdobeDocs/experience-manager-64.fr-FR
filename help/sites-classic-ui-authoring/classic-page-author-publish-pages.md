---
title: Publication de pages
seo-title: Publishing Pages
description: Une fois le contenu créé et révisé dans l’environnement de création, l’objectif est de le rendre disponible sur votre site web public.
seo-description: Once you have created and reviewed your content on the author environment, the goal is to make it available on your public website.
uuid: 2b1cb08b-dbe9-4032-8527-15a11aa59d51
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 80c9f4b7-d59f-4ed1-a457-300756962708
exl-id: 7b3f58df-036e-46a8-913e-e695de34ddd7
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 81%

---

# Publication de pages{#publishing-pages}

Une fois le contenu créé et révisé dans l’environnement de création, l’objectif est de le rendre disponible sur votre site web public (votre environnement de publication).

On parle alors de publication d’une page, ou d’annulation de publication lorsque vous souhaitez retirer une page de l’environnement de publication. En cas de publication et d’annulation de la publication, la page reste disponible pour d’autres modifications dans l’environnement de création jusqu’à ce que vous la supprimiez.

Vous pouvez également publier/annuler la publication d’une page immédiatement ou à une date/heure prédéfinies.

>[!NOTE]
>
>Certains termes relatifs à la publication peuvent prêter à confusion :
>
>* **Publier/Annuler la publication**
   >  Termes principalement utilisés pour évoquer les opérations qui rendent votre contenu publiquement accessible dans votre environnement de publication (ou non).
>
>* **Activer/Désactiver**
   >  Ces termes sont synonymes de publication/annulation de la publication.
>
>* **Répliquer/Réplication**
   >  Il s’agit de termes techniques décrivant le déplacement des données (contenu de page, fichiers, code, commentaires d’utilisateur, par exemple) d’un environnement à un autre, comme lors de la publication ou de la réplication inverse des commentaires d’utilisateur.
>


>[!NOTE]
>
>Si vous ne possédez pas les privilèges requis pour publier une page spécifique :
>
>* Un workflow est déclenché afin d’aviser la personne concernée de votre demande de publication.
>* Un message s’affiche (pendant un bref laps de temps) pour vous en informer.
>


## Publication d’une page {#publishing-a-page}

Pour activer une page, vous pouvez procéder de deux manières :

* [depuis la console Sites Web ;](#activating-a-page-from-the-websites-console)
* [depuis le sidekick sur la page elle-même.](#activating-a-page-from-sidekick)

>[!NOTE]
>
>Vous pouvez également activer une sous-arborescence de plusieurs pages à l’aide de l’option [Activer l’arborescence](#howtoactivateacompletesectiontreeofyourwebsite) sur la console Outils.

### Activation d’une page à partir de la console Sites web {#activating-a-page-from-the-websites-console}

Vous pouvez activer des pages dans la console Sites web. Après avoir ouvert une page et modifié son contenu, vous revenez à la console Sites web : 

1. Dans la console Sites web, sélectionnez la page à activer.
1. Sélectionnez **Activer** dans le menu supérieur ou dans le menu déroulant de l’élément de page sélectionné. 

   Pour activer le contenu de la page et toutes ses pages secondaires, utilisez la console [**Outils**](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#howtoactivateacompletesectiontreeofyourwebsite).

   ![screen_shot_2012-02-08at13817pm](assets/screen_shot_2012-02-08at13817pm.png)

   >[!NOTE]
   >
   >Au besoin, AEM vous demande d’activer ou de réactiver toute ressource liée à la page. Vous pouvez activer ou désactiver les cases à cocher pour activer ces ressources.

1. Au besoin, AEM vous demande d’activer ou de réactiver toute ressource liée à la page. Vous pouvez activer ou désactiver les cases à cocher pour activer ces ressources.

   ![chlimage_1-135](assets/chlimage_1-135.png)

1. La Gestion de contenu web AEM active le contenu sélectionné. La ou les pages publiées apparaissent dans la console [Sites web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) (avec une marque verte), accompagnées d’informations sur la personne qui a activé le contenu, ainsi que la date et l’heure de l’activation.

   ![screen_shot_2012-02-08at14335pm](assets/screen_shot_2012-02-08at14335pm.png)

### Activation d’une page à partir de Sidekick {#activating-a-page-from-sidekick}

Vous pouvez également activer une page ouverte à des fins d’édition.

Après avoir ouvert la page et modifié son contenu, procédez comme suit :

1. Sélectionnez l’onglet **Page** dans le sidekick.
1. Cliquez sur **Activer la page**.

   Un message s’affiche dans le coin supérieur droit de la fenêtre pour confirmer l’activation de la page.

## Annulation de publication d’une page {#unpublishing-a-page}

Pour supprimer une page de l’environnement de publication, désactivez le contenu.

Pour désactiver une page :

1. Dans la console Sites web, sélectionnez la page à désactiver.
1. Sélectionnez **Désactiver** dans le menu supérieur ou dans le menu déroulant de l’élément de page sélectionné. Vous êtes invité à confirmer la suppression.

   ![screen_shot_2012-02-08at14859pm](assets/screen_shot_2012-02-08at14859pm.png)

1. Actualisez la [console Sites web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) et le contenu est marqué en rouge, ce qui indique qu’il n’est plus publié.

   ![screen_shot_2012-02-08at15018pm](assets/screen_shot_2012-02-08at15018pm.png)

## Activer/Désactiver ultérieurement {#activate-deactivate-later}

### Activer plus tard {#activate-later}

Pour planifier l’activation à une heure ultérieure :

1. Dans la console Sites Web, accédez au menu **Activer** et sélectionnez ensuite **Activer plus tard**.
1. Dans la boîte de dialogue qui s’ouvre, indiquez la date et l’heure d’activation, puis cliquez sur **OK**. Cette opération crée une version de la page qui est activée à l’heure indiquée.

   ![screen_shot_2012-02-08at14751pm](assets/screen_shot_2012-02-08at14751pm.png)

L’activation différée lance un workflow pour activer cette version de la page à l’heure indiquée. À l’inverse, la désactivation différée lance un workflow pour désactiver cette version de la page à l’heure indiquée.

Pour annuler cette activation/désactivation, rendez-vous dans la [console Worfklow](/help/sites-administering/workflows-administering.md#main-pars-title-3-yjqslz-refd) pour mettre un terme au workflow correspondant.

### Désactiver plus tard {#deactivate-later}

Pour planifier la désactivation à une heure ultérieure :

1. Dans la console Sites Web, accédez à la **Désactiver** et sélectionnez **Désactiver plus tard**.

1. Dans la boîte de dialogue qui s’ouvre, indiquez la date et l’heure de désactivation, puis cliquez sur **OK**.

   ![screen_shot_2012-02-08at15129pm](assets/screen_shot_2012-02-08at15129pm.png)

La **désactivation différée** lance un workflow pour désactiver cette version de la page à l’heure indiquée.

Pour annuler cette désactivation, rendez-vous dans la [console Worfklow](/help/sites-administering/workflows-administering.md#main-pars-title-3-yjqslz-refd) pour mettre un terme au workflow correspondant.

## Activation/désactivation planifiée (heure d’activation/désactivation) {#scheduled-activation-deactivation-on-off-time}

Pour programmer les heures de publication/annulation de publication d’une page, utilisez les options **Heure d’activation** et **Heure de désactivation** dans les [Propriétés de la page](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md).

### Définition de l’état de publication de la page - IU classique {#determining-page-publication-status-classic-ui}

Vous pouvez vérifier l’état dans la [console Sites web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console). Les couleurs indiquent l’état de publication.

## Activation d’une section (arborescence) complète de votre site web {#activating-a-complete-section-tree-of-your-website}

Vous pouvez activer les différentes pages à partir de l’onglet **Sites web**. Après avoir saisi ou mis à jour un nombre élevé de pages de contenu (toutes résidant sous la même page racine), il peut s’avérer plus simple d’activer toute l’arborescence en une seule opération. Vous pouvez également effectuer une exécution d’essai afin d’émuler une activation et de mettre en surbrillance les pages à activer.

1. Ouvrez le **Outils** en la sélectionnant dans la console **Bienvenue** puis double-cliquez sur **Réplication** pour ouvrir la console ( `http://localhost:4502/etc/replication.html`).

   ![screen_shot_2012-02-08at125033pm](assets/screen_shot_2012-02-08at125033pm.png)

1. Sur la console **Réplication**, cliquez sur **Activer l’arborescence**.

   La fenêtre suivante ( `http://localhost:4502/etc/replication/treeactivation.html`) s’affiche.

   ![screen_shot_2012-02-08at125033pm-1](assets/screen_shot_2012-02-08at125033pm-1.png)

1. Saisissez le **Chemin de début**. Cela spécifie le chemin d’accès à la racine de la section que vous souhaitez activer (publier). Cette page et toutes les pages sous-jacentes sont prises en compte pour l’activation (ou utilisées dans l’émulation si une Exécution d’essai est sélectionnée).
1. Activez les critères de sélection suivant vos besoins :

   * **Uniquement Modifié** : active uniquement les pages qui ont été modifiées.
   * **Uniquement Activé** : active uniquement les pages qui ont (déjà) été activées. Cette option agit, en quelque sorte, comme une réactivation.
   * **Ignorer Désactivé** : ignore les pages qui ont été désactivées.

1. Sélectionnez l’opération à effectuer :

   1. Sélectionner **Exécution d’essai** si vous souhaitez vérifier les pages *serait* être activée. Il s’agit uniquement d’une émulation. Aucune page ne sera activée.
   1. Sélectionner **Activer** si vous souhaitez activer les pages.
