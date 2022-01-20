---
title: Package de compatibilité
seo-title: Compatibility Package
description: 'L’installation du package de compatibilité sur AEM Forms 6.4 vous permet d’utiliser les actifs de Correspondence Management d’AEM Forms 6.3 et les modèles et pages de formulaires adaptatifs obsolètes '
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 81%

---

# Installer le package de compatibilité {#compatibility-package}

L’installation du package de compatibilité sur AEM Forms 6.4 vous permet d’utiliser les actifs de Correspondence Management d’AEM Forms 6.3 et les modèles et pages de formulaires adaptatifs obsolètes

## Présentation {#overview}

La communication interactive est l’approche par défaut et recommandée pour créer des communications client dans AEM Forms 6.4. Pour continuer à utiliser les lettres d’AEM Forms 6.3 et 6.2, vous devez installer le [package de compatibilité AEMFD](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

Le package de compatibilité AEMFD vous permet d’utiliser les actifs suivants d’AEM Forms 6.3 et 6.2 sur AEM Forms 6.4 :

* Fragments de document créés dans AEM Forms 6.3 et 6.2
* Lettres
* Dictionnaires de données
* Modèles et pages des formulaires adaptatifs obsolètes

Pour plus d’informations, voir [Ressources rendues compatibles avec AEM Forms 6.4 en installant le package de compatibilité](/help/forms/using/compatibility-package.md#assetsmadecompatible).

## Ajout de la prise en charge des actifs AEM Forms 6.3 et 6.2 dans AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Après avoir effectué une mise à niveau, exécutez les opérations suivantes pour installer le package de compatibilité AEMFD et rendre vos actifs compatibles avec la version 6.4 :

Assurez-vous que vous avez [Package de compatibilité AEM](/help/sites-deploying/backward-compatibility.md) pré-installé.

1. Installez le [package de compatibilité](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

   Pour plus d’informations sur le téléchargement et l’installation du package, voir [Utilisation de packages](/help/sites-administering/package-manager.md).

1. Une fois les journaux stabilisés, redémarrez le serveur.
1. Utilisez l’utilitaire de migration pour rendre vos actifs compatibles avec la version 6.4.

   Pour plus d’informations, voir [utilitaire de migration](/help/forms/using/migration-utility.md).

## Actifs devenus compatibles avec AEM Forms 6.4 après l’installation du package de compatibilité {#assetsmadecompatible}

En installant le package de compatibilité, vous pouvez rendre les actifs et modèles suivants compatibles avec AEM Forms 6.4 :

* Actifs de Correspondence Management d’AEM 6.3 et versions antérieures

   * [Lettres](/help/forms/using/create-letter.md)
   * [Dictionnaires de données](/help/forms/using/data-dictionary.md)
   * Fragments de document

* Modèles obsolètes de formulaires adaptatifs

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Pages obsolètes de formulaires adaptatifs :

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
