---
title: Bonnes pratiques
description: Découvrez les bonnes pratiques d’Adobe Experience Manager compilées par les équipes d’ingénierie et de conseil d’Adobe afin d’aider les administrateurs à se familiariser avec le fonctionnement.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
exl-id: 8c41dba4-bedc-4747-b67d-fd89d71c8b2c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 55%

---

# Bonnes pratiques{#best-practices}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La section Meilleures pratiques décrit comment développer, administrer ou utiliser AEM de la manière la plus efficace possible. Cette liste croissante de sujets englobe un large éventail de domaines dans AEM.

La documentation relative aux bonnes pratiques est disponible dans les domaines suivants :

* [Assets](#assets)
* [Sites](#sites)

Pour connaître les bonnes pratiques concernant la création, le déploiement et la maintenance ou le développement, consultez l’une des rubriques suivantes :

* [Bonnes pratiques de création](/help/sites-authoring/best-practices.md)
* [Bonnes pratiques de développement](/help/sites-developing/best-practices.md)
* [Bonnes pratiques de déploiement](/help/sites-deploying/best-practices.md)

Les documents spécifiques sont décrits et associés dans les tables qui suivent.

## Assets {#assets}

Les bonnes pratiques concernant Assets, y compris les fonctionnalités Dynamic Media et son intégration, sont décrites dans les rubriques suivantes :

<table> 
 <tbody>
  <tr>
   <td>Bonnes pratiques dans différents domaines liés à Assets pour améliorer la stabilité du système et les performances en cas de forte charge</td> 
   <td><a href="/help/assets/organize-assets.md">Bonnes pratiques pour Assets</a></td> 
   <td>Inclut des liens vers des guides de bonnes pratiques dans différents domaines d’Assets. Après avoir consulté ce contenu, vous disposerez des connaissances et des outils vous permettant de créer et gérer un système de gestion de ressources d’entreprise.</td> 
  </tr>
  <tr>
   <td>Comment organiser votre contenu (hiérarchie des dossiers)</td> 
   <td><a href="/help/assets/organize-assets.md">Bonnes pratiques relatives à la gestion des fichiers</a></td> 
   <td>La plupart des profils de traitement reposent sur des dossiers, car les vidéos, les métadonnées et le traitement des images sont toujours appliqués aux dossiers. Ce document de bonnes pratiques décrit comment définir et configurer votre hiérarchie de dossiers, car la hiérarchie a un impact significatif sur le traitement du contenu. </td> 
  </tr>
  <tr>
   <td>Intégration de Dynamic Media Classic et d’AEM</td> 
   <td><a href="/help/sites-administering/scene7.md#best-practices-for-integrating-scene-with-aem">Bonnes pratiques pour intégrer Dynamic Media Classic à AEM</a></td> 
   <td><p>Décrit quand activer l’importateur d’interrogations, comment tester votre intégration et quand utiliser l’explorateur de contenu plutôt qu’un téléchargement direct vers Assets.</p> </td> 
  </tr>
  <tr>
   <td>Options des paramètres prédéfinis d’image</td> 
   <td>Comprendre les <a href="/help/assets/managing-image-presets.md#understanding-image-presets">paramètres prédéfinis d’image</a> et <a href="/help/assets/managing-image-presets.md#image-preset-options">les bonnes pratiques en matière de paramètres prédéfinis d’image</a></td> 
   <td>Dans le cadre de la documentation sur <a href="/help/assets/managing-image-presets.md">Gestion des paramètres d’image prédéfinis</a>, ces rubriques décrivent les paramètres d’image prédéfinis et les bonnes pratiques concernant la sélection des options de paramètres d’image prédéfinis.</td> 
  </tr>
  <tr>
   <td>Dynamic Media et intégration directe à Dynamic Media Classic</td> 
   <td><a href="/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media">Intégration Dynamic Media Classic/AEM par rapport à Dynamic Media</a></td> 
   <td>Indique quand est préférable d’utiliser la solution Dynamic Media, d’utiliser l’intégration S7 avec AEM ou d’utiliser les deux.</td> 
  </tr>
 </tbody>
</table>

## Sites {#sites}

La gestion et la création du contenu de votre site web comportent les bonnes pratiques suivantes :

<table> 
 <tbody>
  <tr>
   <td>Conformité au RGPD</td> 
   <td><a href="/help/sites-administering/gdpr-compliance-sites.md">AEM Sites – Conformité au RGPD</a></td> 
   <td>Le règlement général sur la protection des données (RGPD) de l’Union européenne sur les droits de confidentialité des données entre en vigueur en mai 2018. AEM Sites est conforme au RGPD. Cette page guide les clients à travers les procédures de gestion des demandes RGPD dans AEM Sites. Elle décrit l’emplacement des données privées stockées et la procédure pour les supprimer manuellement ou à l’aide de code.</td> 
  </tr>
  <tr>
   <td>Définissez l’interface utilisateur par défaut de votre instance.</td> 
   <td><p><a href="/help/sites-authoring/select-ui.md#configuring-the-default-ui-for-your-instance">Configuration de l’IU par défaut pour votre instance</a></p> </td> 
   <td>AEM comporte deux interfaces utilisateur : une interface classique et une interface optimisée pour les écrans tactiles. Cette section explique comment définir l’interface utilisateur par défaut de votre instance.</td> 
  </tr>
  <tr>
   <td>Gestion multisite</td> 
   <td><a href="/help/sites-administering/msm-best-practices.md">Bonnes pratiques relatives au MSM</a></td> 
   <td>Bonnes pratiques concernant l’utilisation du MSM pour automatiser le déploiement du contenu. </td> 
  </tr>
  <tr>
   <td>Traduction du contenu</td> 
   <td><a href="/help/sites-administering/tc-bp.md">Bonnes pratiques en matière de traduction</a></td> 
   <td>Bonnes pratiques pour la planification et la mise en oeuvre de votre site multilingue.</td> 
  </tr>
  <tr>
   <td>Administration des utilisateurs</td> 
   <td><a href="/help/sites-administering/security.md#best-practices">Bonnes pratiques concernant les autorisations et droits d’accès</a></td> 
   <td>Décrit les bonnes pratiques lorsque vous travaillez avec des autorisations et droits d’accès </td> 
  </tr>
  <tr>
   <td>Workflows</td> 
   <td><a href="/help/sites-developing/workflows-best-practices.md#configuration">Bonnes pratiques de workflows : configuration</a></td> 
   <td>Les workflows vous permettent d’automatiser les activités d’Adobe Experience Manager (AEM) et peuvent représenter une grande partie du traitement qui se produit dans un environnement AEM. Il est donc hautement recommandé de planifier et de configurer avec soin les implémentations de workflows.</td> 
  </tr>
 </tbody>
</table>
