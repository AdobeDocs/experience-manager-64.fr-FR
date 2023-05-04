---
title: Modification de lancements
seo-title: Editing Launches
description: Après avoir créé un lancement pour votre page (ou ensemble de pages), vous pouvez modifier le contenu dans la copie de lancement des pages.
seo-description: After creating a launch for your page (or set of pages) you can edit the content in the launch copy of the page(s).
uuid: 851bcbbe-1dff-457f-a3bc-468ace9b4ac4
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: a28539fc-c1dd-43bf-a47b-5f158c5611a7
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 9f208b13-08eb-4305-b712-379e9b9b041e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 54%

---

# Modification de lancements{#editing-launches}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Modification de pages de lancement {#editing-launch-pages}

Après avoir créé un lancement pour une page (ou un jeu de pages), vous pouvez modifier le contenu dans la copie de lancement correspondante.

1. Accédez à [Lancement à partir des références (console Sites)](/help/sites-authoring/launches.md#launches-in-references-sites-console) pour afficher les actions disponibles.
1. Sélectionner **Accéder à la page** pour ouvrir la page à modifier.

### Modification de l’objet des pages de lancement en Live Copy   {#editing-launch-pages-subject-to-a-live-copy}

Si votre lancement est basé sur une [Live Copy](/help/sites-administering/msm.md) vous pourrez ensuite :

* voir symboles de verrouillage (petits verrous) lorsque vous modifiez un composant (contenu et/ou propriétés).
* voir la **Live Copy** dans **Propriétés de la page**

Une Live Copy est utilisée pour synchroniser le contenu *depuis* la branche source *vers* votre branche de lancement (afin que votre lancement soit à jour avec les modifications apportées à la source).

Vous pouvez apporter des modifications de la même manière que vous pouvez modifier une Live Copy standard ; par exemple :

* Cliquez sur un cadenas fermé pour interrompre cette synchronisation et vous permettre d’apporter de nouvelles mises à jour au contenu de votre lancement. Une fois déverrouillé (ouverture du cadenas), vos modifications ne seront pas remplacées par des modifications effectuées au même emplacement dans la branche source.
* **Suspendre** (et **Reprendre**) l’héritage pour une page spécifique.

Pour plus d’informations, voir [Modification du contenu d’une Live Copy](/help/sites-administering/msm-livecopy.md#changing-live-copy-content).

## Comparaison d’une page de lancement avec sa page source {#comparing-a-launch-page-to-its-source-page}

Pour suivre les modifications que vous avez apportées, vous pouvez afficher le lancement dans **Références** et comparer la page de lancement à sa page source :

1. Dans le **Sites** console, [accédez à la page source de votre lancement et sélectionnez-la.](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez le **[Références](/help/sites-authoring/basic-handling.md#references)** et sélectionnez **Lancements**.
1. Sélectionnez votre lancement spécifique, puis **Comparaison avec la source**:

   ![chlimage_1-96](assets/chlimage_1-96.png)

1. Les deux pages (lancement et source) s’ouvrent côte à côte.

   Pour des informations complètes sur l’utilisation de cette fonction, consultez [Différence entre les pages](/help/sites-authoring/page-diff.md).

## Modification des pages source utilisées {#changing-the-source-pages-used}

Vous pouvez à tout moment ajouter ou supprimer des pages vers/depuis la plage de pages source pour un lancement :

1. Accédez au lancement et sélectionnez-le depuis, au choix :

   * la valeur [Console de lancements](/help/sites-authoring/launches.md#the-launches-console):

      * Sélectionnez **Modifier**.
   * [Références (console Sites)](/help/sites-authoring/launches.md#launches-in-references-sites-console) pour afficher les actions disponibles :

      * Sélectionnez **Modifier le lancement**.

   Les pages source s’affichent.

1. Effectuez les modifications requises, puis confirmez avec **Enregistrer**.

   >[!NOTE]
   >
   >Pour ajouter des pages à un lancement, elles doivent se trouver sous une racine de langue commune ; c’est-à-dire sur un seul site.

## Modification d’une configuration de lancement {#editing-a-launch-configuration}

Vous pouvez à tout moment modifier les propriétés d’un lancement :

1. Accédez au lancement et sélectionnez-le depuis, au choix :

   * la valeur [Console de lancements](/help/sites-authoring/launches.md#the-launches-console):

      * Sélectionner **Propriétés**.
   * [Références (console Sites)](/help/sites-authoring/launches.md#launches-in-references-sites-console) pour afficher les actions disponibles :

      * Sélectionnez **Modifier les propriétés**.

   Les détails s’affichent.

1. Effectuez les modifications requises, puis confirmez avec **Enregistrer**.

   Consultez [Lancements – Ordre des événements](/help/sites-authoring/launches.md#launches-the-order-of-events) pour plus d’informations sur l’objectif et l’interaction des champs **Date de lancement** et **Prêt pour la production**.

## Identification du statut de lancement d’une page {#discovering-the-launch-status-of-a-page}

Le statut s’affiche lorsque vous sélectionnez un lancement spécifique dans l’onglet Références (voir [Lancements dans les références (console Sites)](/help/sites-authoring/launches.md#launches-in-references-sites-console)).

![chlimage_1-97](assets/chlimage_1-97.png)
