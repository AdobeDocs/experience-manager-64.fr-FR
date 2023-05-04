---
title: Intégration de Target avec les fragments d’expérience
seo-title: Target Integration with Experience Fragments
description: Intégration de Target avec les fragments d’expérience
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 39%

---

# Intégration de Target avec les fragments d’expérience{#target-integration-with-experience-fragments}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Cette fonctionnalité nécessite l’application de la fonction [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) ou plus tard.

Vous pouvez exporter [Fragments d’expérience](/help/sites-authoring/experience-fragments.md), créé dans Adobe Experience Manager (AEM), dans Adobe Target. Ceux-ci peuvent ensuite être utilisés comme offres dans les activités Target, pour tester et personnaliser les expériences en fonction des besoins. Cela vous permet de combiner la facilité d’utilisation et la puissance d’AEM, avec les puissantes fonctionnalités d’intelligence automatisée (AI) et d’apprentissage automatique (ML) de Target.

## Conditions préalables {#prerequisites}

Plusieurs actions sont requises :

1. Vous devez intégrer AEM à Target. Voir [Intégration à Adobe Target](/help/sites-administering/target.md) pour plus d’informations.
1. Les fragments d’expérience sont exportés à partir de l’instance d’auteur. Vous devez donc [Configuration de l’externaliseur de liens](/help/sites-developing/externalizer.md) sur l’instance de création pour vous assurer que les liens sont externalisés pour l’instance de publication.

## Ajoutez la configuration du cloud {#add-the-cloud-configuration}

Avant d’exporter un fragment, vous devez ajouter la **configuration cloud** pour **Adobe Target** au fragment ou au dossier:

1. Accédez à la console **Fragments d’expérience**.
1. Ouvrez les **propriétés de page** pour le dossier ou le fragment approprié.

   >[!NOTE]
   >
   >Si vous ajoutez la configuration cloud au dossier parent du fragment d’expérience, elle est héritée par tous les enfants.
   >
   >Si vous ajoutez la configuration cloud au fragment d’expérience lui-même, celle-ci est héritée par toutes les variations.

1. Sélectionnez l’onglet **Services cloud**.

1. Sous **Configuration du Cloud Service**, sélectionnez **Adobe Target** dans la liste déroulante.
1. Sous **Adobe Target**, sélectionnez la configuration appropriée.

1. **Enregistrer et fermer**.

## Exportation d’un fragment d’expérience vers Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Pour les contenus multimédias, comme les images, une seule référence est exportée vers Target. La ressource elle-même reste stockée dans AEM Assets et est diffusée à partir de l’instance de publication AEM.
>
>C’est pourquoi le fragment d’expérience, avec toutes les ressources associées, doit être publié avant l’exportation vers Target.

Pour exporter un fragment d’expérience d’AEM vers Target (après avoir spécifié la configuration cloud) :

1. Accédez à la console Fragment d’expérience .
1. Sélectionnez le fragment d’expérience que vous souhaitez exporter vers la cible.

   >[!NOTE]
   >
   >Il doit s’agir d’une variation web de fragment d’expérience.

1. Appuyez/cliquez sur **Exporter vers Adobe Target**.

   >[!NOTE]
   >
   >Si le fragment d’expérience a déjà été exporté, sélectionnez **Mise à jour dans Adobe Target**.

1. Appuyez/cliquez sur **Exportation sans publication** ou **Publier** selon les besoins.

   >[!NOTE]
   >
   >En sélectionnant** Publier**, vous publierez immédiatement le fragment d’expérience et l’enverrez à Target.

1. Appuyez/cliquez sur **OK** dans la boîte de dialogue de confirmation.

   Votre fragment d’expérience se trouve désormais dans Target.

>[!NOTE]
>
>Vous pouvez également effectuer l’exportation à partir de l’éditeur de page, à l’aide de commandes comparables dans la variable [Informations sur la page](/help/sites-authoring/author-environment-tools.md#page-information) .

## Utilisation de vos fragments d’expérience dans Target {#using-your-experience-fragments-in-target}

Après avoir effectué les tâches précédentes, le fragment d’expérience s’affiche sur la page Offres de Target. Veuillez jeter un coup d’oeil au [documentation spécifique de Target](https://experiencecloud.adobe.com/resources/help/fr_FR/target/target/aem-experience-fragments.html) pour en savoir plus sur ce que vous pouvez y réaliser.

## Suppression d’un fragment d’expérience déjà exporté vers Target {#deleting-an-experience-fragment-already-exported-to-target}

La suppression d’un fragment d’expérience qui a déjà été exporté vers Target peut entraîner des problèmes si le fragment est déjà utilisé pour une offre dans Target. La suppression du fragment rendrait l’offre inutilisable, car le contenu du fragment est diffusé par AEM.

Pour éviter de telles situations :

* Si le fragment d’expérience n’est pas actuellement utilisé dans une activité, AEM permet à l’utilisateur de le supprimer sans message d’avertissement.
* Si le fragment d’expérience est actuellement utilisé par une activité dans Target, un message d’erreur avertit l’utilisateur AEM des conséquences possibles de la suppression du fragment sur l’activité.

   Le message d’erreur apparu dans AEM n’empêche pas à l’utilisateur de forcer la suppression du fragment d’expérience. Lorsque le fragment d’expérience est supprimé :

   * l’offre Target qui utilise le fragment d’expérience AEM peut souffrir d’un comportement indésirable ;

      * l’offre effectue toujours le rendu, car le code HTML du fragment d’expérience a été transmis à Target ;
      * les références du fragment d’expérience peuvent ne pas fonctionner correctement si les ressources référencées ont également été supprimées dans AEM.
   * Bien sûr, toute modification supplémentaire apportée au fragment d’expérience est impossible, car le fragment d’expérience n’existe plus dans AEM.
