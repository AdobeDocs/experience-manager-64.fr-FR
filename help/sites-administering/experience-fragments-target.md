---
title: Intégration de fragments d’expérience dans Adobe Target
seo-title: Target Integration with Experience Fragments
description: Intégration de fragments d’expérience dans Adobe Target
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 93%

---

# Intégration de fragments d’expérience dans Adobe Target{#target-integration-with-experience-fragments}

>[!NOTE]
>
>Cette fonctionnalité nécessite l’application de la fonction [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) ou plus tard.

Vous pouvez exporter des [fragments d’expérience](/help/sites-authoring/experience-fragments.md), créés dans Adobe Experience Manager (AEM), vers Adobe Target. Ceux-ci peuvent ensuite être utilisés comme offres dans les activités Target, pour tester et personnaliser les expériences en fonction des besoins. Vous pouvez ainsi combiner la facilité d’utilisation et la puissance d’AEM avec les puissantes fonctionnalités d’intelligence automatisée et d’apprentissage automatique de Target.

## Conditions préalables {#prerequisites}

Plusieurs actions sont requises :

1. Vous devez intégrer AEM à Target. Voir [Intégration à Adobe Target](/help/sites-administering/target.md) pour plus d’informations.
1. Les fragments d’expérience sont exportés à partir de l’instance de création. Vous devez donc [configurer l’externaliseur de liens](/help/sites-developing/externalizer.md) sur l’instance de création pour vous assurer que l’ensemble des liens est externalisé pour l’instance de publication.

## Ajoutez la configuration du cloud {#add-the-cloud-configuration}

Avant d’exporter un fragment, vous devez ajouter la **configuration cloud** pour **Adobe Target** au fragment ou au dossier:

1. Accédez à la console **Fragments d’expérience**.
1. Ouvrez les **propriétés de page** pour le dossier ou le fragment approprié.

   >[!NOTE]
   >
   >Lorsque vous ajoutez la configuration cloud au dossier parent du fragment d’expérience, celle-ci est héritée par tous les enfants.
   >
   >Lorsque vous ajoutez la configuration cloud directement au fragment d’expérience, la configuration est héritée par toutes les variations.

1. Sélectionnez l’onglet **Services cloud**.

1. Sous **Configuration du service cloud**, sélectionnez **Adobe Target** dans la liste déroulante.
1. Sous **Adobe Target**, sélectionnez la configuration appropriée.

1. **Enregistrez et fermez**.

## Exportation d’un fragment d’expérience vers Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Pour les contenus multimédias, comme les images, une seule référence est exportée vers Target. La ressource elle-même reste stockée dans AEM Assets et elle est diffusée depuis l’instance de publication AEM.
>
>Le fragment d’expérience, ainsi que l’ensemble des ressources connexes, doivent être publiés avant l’exportation vers Target.

Pour exporter un fragment d’expérience d’AEM vers Target (une fois la configuration cloud spécifiée) :

1. Accédez à la console Fragment d’expérience.
1. Sélectionnez le fragment d’expérience que vous souhaitez exporter vers Target.

   >[!NOTE]
   >
   >Il doit s’agir d’une variation web de fragment d’expérience.

1. Appuyez/cliquez sur **Exporter vers Adobe Target**.

   >[!NOTE]
   >
   >Si le fragment d’expérience a déjà été exporté, sélectionnez **Mettre à jour dans Adobe Target**.

1. Appuyez/cliquez sur **Exporter sans publier** ou sur **Publier**, en fonction de vos besoins.

   >[!NOTE]
   >
   >En sélectionnant** Publier**, vous publierez immédiatement le fragment d’expérience et l’enverrez à Target.

1. Appuyez/cliquez sur **OK** dans la boîte de dialogue de confirmation.

   Votre fragment d’expérience se trouve désormais dans Target.

>[!NOTE]
>
>Vous pouvez également procéder à l’exportation via l’éditeur de page, à l’aide des commandes comparables du menu [Informations sur la page](/help/sites-authoring/author-environment-tools.md#page-information).

## Utilisation de vos fragments d’expérience dans Target {#using-your-experience-fragments-in-target}

Après avoir effectué les tâches précédentes, le fragment d’expérience s’affiche sur la page Offres de Target. Consultez la [documentation spécifique de Target](https://experiencecloud.adobe.com/resources/help/fr_FR/target/target/aem-experience-fragments.html) pour en savoir plus sur ce qui est réalisable.

## Suppression d’un fragment d’expérience déjà exporté vers Target {#deleting-an-experience-fragment-already-exported-to-target}

La suppression d’un fragment d’expérience qui a déjà été exporté vers Target peut entraîner des problèmes si le fragment est déjà utilisé pour une offre dans Target. L’offre ne serait alors plus utilisable, car c’est AEM qui fournit le contenu du fragment.

Pour éviter de tels problèmes :

* Si le fragment d’expérience n’est pas en cours d’utilisation par une activité, l’utilisateur peut le supprimer sans recevoir de message d’avertissement.
* Si le fragment d’expérience est en cours d’utilisation par une activité dans Target, un message d’erreur informe l’utilisateur d’AEM des risques que la suppression dudit fragment peut engendrer.

   Le message d’erreur apparu dans AEM n’empêche pas à l’utilisateur de forcer la suppression du fragment d’expérience. Lorsque le fragment d’expérience est supprimé :

   * l’offre Target qui utilise le fragment d’expérience AEM peut souffrir d’un comportement indésirable ;

      * l’offre effectue toujours le rendu, car le code HTML du fragment d’expérience a été transmis à Target ;
      * les références du fragment d’expérience peuvent ne pas fonctionner correctement si les ressources référencées ont également été supprimées dans AEM.
   * Bien sûr, toute modification supplémentaire apportée au fragment d’expérience est impossible, car le fragment d’expérience n’existe plus dans AEM.
