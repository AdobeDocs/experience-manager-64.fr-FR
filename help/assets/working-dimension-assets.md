---
title: Utilisation de ressources Adobe Dimension
description: Utilisation de ressources Adobe Dimension dans AEM 3D.
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: be8f6361-607d-4529-aef0-e8978dfd04b4
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---

# Utilisation de ressources Adobe Dimension {#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>Le pack de fonctionnalités 3D AEM dans AEM 6.4 n’est plus pris en charge. Adobe vous recommande d&#39;utiliser la fonction des actifs 3D dans [AEM en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) ou [AEM 6.5.3 ou supérieur.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) lorsque vous utilisez des ressources Adobe Dimension.

Le pack de fonctionnalités 3D AEM fournit la prise en charge des fichiers Adobe Dimension (`.dn` fichiers) dans AEM Assets, AEM Sites et AEM Screens.

Une nouvelle visionneuse 3D basée sur la norme ouverte glTF offre des fonctionnalités d’affichage des prévisualisations et des sites et écrans pour les ressources Adobe Dimension.

## À propos du service de conversion basé sur le cloud {#about-the-cloud-based-conversion-service}

Lorsqu’un fichier de Dimension est téléchargé vers AEM, une copie du fichier est transférée vers un service cloud géré par Adobe hébergé dans Amazon AWS. Ce service convertit du format de fichier de Dimension propriétaire de l’Adobe au format glTF standard ouvert. Le modèle 3D converti est conditionné en tant que glTF binaire (`.glb`). AEM stocke le modèle converti avec la ressource de Dimension Principale en tant que rendu.

Vous pouvez configurer le format de conversion `.glb` de l’une des deux façons suivantes (voir [Installation et configuration de l’AEM 3D](install-config-3d.md) pour obtenir des instructions) :

* Insérez des extensions spécifiques à l’Adobe pour optimiser la qualité visuelle lors de l’utilisation de la visionneuse glTF Adobe pour vue des ressources de Dimension dans AEM Assets, AEM Sites ou AEM Screens. Cela rend les rendus `.glb` incompatibles avec la plupart des applications tierces.
* Exclure les extensions spécifiques à l&#39;Adobe pour assurer la compatibilité du rendu `.glb` avec les applications tierces. Ceci limite la qualité visuelle lors de l’affichage en AEM Assets, AEM Sites ou AEM Screens (par exemple, aucun éclairage IBL) afin de simuler la qualité des applications tierces typiques.

Le transfert des fichiers Dimension/glTF vers ou depuis Amazon AWS et leur enregistrement temporaire dans AWS sont entièrement sécurisés. Ces fichiers sont conservés dans Amazon AWS pendant un laps de temps minimal ; généralement, pas plus de quelques minutes pendant les opérations normales.

Pour activer la prise en charge des ressources de Dimension, vous devez obtenir des informations d’identification auprès de l’Adobe pour accéder au service de conversion. Reportez-vous à la section [Installation et configuration d’AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Si vous installez et utilisez les informations d’identification fournies, vous comprenez et acceptez que vos ressources Adobe Dimension 3D soient transférées vers le service de conversion en cloud géré par Adobe hébergé dans Amazon AWS et traitées par lui.

### Affichage sur AEM Assets {#viewing-on-aem-assets}

Le pack de fonctionnalités 3D AEM comprend une nouvelle visionneuse basée sur la norme ouverte glTF utilisée pour vue des ressources Adobe Dimension. Cette visionneuse est sélectionnée automatiquement lors de l’ouverture d’un fichier de Dimension ou d’un fichier glTF compressé dans la vue de détails de AEM Assets ou avec le composant 3D de AEM Sites.

Notez que l’interface utilisateur du lecteur glTF est quelque peu différente de la visionneuse 3D standard utilisée pour tous les autres types de fichier 3D.

#### Consultez également les informations suivantes : {#see-also-the-following}

* [AEM de mise à jour 3D ](/help/release-notes/aem3d-release-notes.md) note les restrictions et limitations applicables aux ressources Dn et à la visionneuse glTF.
* [Utilisation du ](using-the-3d-sites-component.md) composant Sites 3D pour les propriétés de composants spécifiques aux ressources Adobe Dimension.
* [Installation et configuration d’AEM 3](install-config-3d.md) Dpour configurer le service de conversion basé sur le cloud.
