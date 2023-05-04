---
title: Mise à jour du type de licence pour le déploiement
seo-title: Update the license type for the deployment
description: Mettez à jour le type de licence pour le déploiement à l’aide de la page Changer de licence dans Administration Console.
seo-description: Update the license type for the deployment by using the Change License page in administration console.
uuid: 0152635e-2c00-4944-b9b6-64b368589a91
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e4f31377-ccc9-4986-a3bf-ef2e83d12448
exl-id: 07671470-59dd-4290-be9a-465fcd89ac2d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 29%

---

# Mise à jour du type de licence pour le déploiement {#update-the-license-type-for-the-deployment}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lors du processus d’installation d’AEM forms, vous avez utilisé Configuration Manager pour configurer et déployer les modules AEM forms dont vous avez besoin. Par défaut, ces modules sont configurés avec une licence d’évaluation de 60 jours. Utilisez la page Changer de licence dans Administration Console pour modifier le type de licence du déploiement. Les modules actuellement déployés s’affichent sur la page Changer de licence .

La page Changer de licence affiche des informations sur votre licence :

* Type de licence actuel
* Date et heure de la dernière mise à jour de la licence
* Qui a effectué la dernière mise à jour
* État actuel de la licence
* La date à laquelle AEM forms a été installé
* Date d’expiration de la licence actuelle

>[!NOTE]
>
>La modification de licence s’applique à tous les modules déployés. Avant de modifier le type de licence, annulez le déploiement des modules qui ne sont pas sous licence. Ne sélectionnez pas le type de licence Production si la liste des modules déployés contient des modules autres que ceux achetés sur Adobe.

## Mettre à jour le type de licence {#update-the-license-type}

1. Dans Administration Console, cliquez sur Licences.
1. Lisez le contrat de licence de l’utilisateur final d’AEM forms, sélectionnez J’accepte si vous en acceptez les termes, puis cliquez sur Suivant.
1. Sur la page Changer de licence , sélectionnez un type de licence :

   * **EVAL :** Licence d’évaluation de 60 jours
   * **DEV :** licence de développement perpétuelle
   * **NFR :** Licence d’évaluation de 2 ans
   * **IDEV :** abonnement d’un an au programme Adobe Developer
   * **Production :** licence perpétuelle

1. Sélectionnez Oui, le changement de licence est valide pour tous les modules déployés.
1. Cliquez sur Confirmer le changement de licence. Un message s’affiche, indiquant que la licence a été mise à jour avec succès.
