---
title: Package de compatibilité
seo-title: Compatibility Package
description: L’installation du package de compatibilité sur AEM Forms 6.4 vous permet d’utiliser les actifs Correspondence Management d’AEM Forms 6.3 et les modèles et pages de formulaires adaptatifs obsolètes.
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 34%

---

# Installer le package de compatibilité {#compatibility-package}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’installation du package de compatibilité sur AEM Forms 6.4 vous permet d’utiliser les actifs Correspondence Management d’AEM Forms 6.3 et les modèles et pages de formulaires adaptatifs obsolètes.

## Présentation {#overview}

La communication interactive est l’approche par défaut et recommandée pour créer des communications client dans AEM Forms 6.4. Pour continuer à utiliser les lettres d’AEM 6.3 Forms et d’AEM 6.2 Forms, vous devez installer le [Package de compatibilité AEMFD](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr).

Le package de compatibilité AEMFD vous permet d’utiliser les ressources suivantes d’AEM Forms 6.3 et 6.2 sur AEM Forms 6.4 :

* Fragments de document créés dans AEM Forms 6.3 et 6.2
* Lettres
* Dictionnaires de données
* Modèles et pages obsolètes de formulaires adaptatifs

Pour plus d’informations, consultez la section [Ressources devenues compatibles avec AEM Forms 6.4 après l’installation du package de compatibilité](/help/forms/using/compatibility-package.md#assetsmadecompatible).

## Ajout de la prise en charge des ressources AEM Forms 6.3 et 6.2 dans AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Après avoir effectué une mise à niveau, exécutez les opérations suivantes pour installer le package de compatibilité AEMFD et rendre vos actifs compatibles avec la version 6.4 :

Assurez-vous que le [package de compatibilité AEM](/help/sites-deploying/backward-compatibility.md) est préinstallé.

1. Installez le [Package de compatibilité](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr).

   Pour plus d’informations sur le téléchargement et l’installation du package, voir [Utilisation des packages](/help/sites-administering/package-manager.md).

1. Une fois les journaux stabilisés, redémarrez le serveur.
1. Utilisez l’utilitaire de migration pour rendre vos actifs compatibles avec la version 6.4.

   Pour plus d’informations, consultez la section [Utilitaire de migration](/help/forms/using/migration-utility.md).

## Actifs devenus compatibles avec AEM Forms 6.4 après l’installation du package de compatibilité {#assetsmadecompatible}

En installant le package de compatibilité, vous pouvez rendre les ressources et les modèles suivants compatibles avec AEM Forms 6.4 :

* Actifs de Correspondence Management d’AEM 6.3 et versions antérieures

   * [Lettres](/help/forms/using/create-letter.md)
   * [Dictionnaires de données](/help/forms/using/data-dictionary.md)
   * Fragments de document

* Modèles de formulaire adaptatif obsolètes

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Pages obsolètes de formulaires adaptatifs :

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
