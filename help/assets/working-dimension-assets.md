---
title: Utilisation de ressources Adobe Dimension
seo-title: Utilisation de ressources Adobe Dimension
description: Utilisation des ressources Adobe Dimension dans AEM 3D.
seo-description: Utilisation des ressources Adobe Dimension dans AEM 3D.
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f

---


# Utilisation de ressources Adobe Dimension {#working-with-adobe-dimension-assets}

Le Feature Pack AEM 3D prend en charge les ressources Adobe Dimension (`.dn` fichiers) dans les ressources AEM, les sites AEM et les écrans AEM.

Une nouvelle visionneuse 3D basée sur la norme ouverte glTF fournit des fonctionnalités d’aperçu et d’affichage Sites et écrans pour les ressources Adobe Dimension.

## À propos du service de conversion en mode cloud {#about-the-cloud-based-conversion-service}

Lorsqu’un fichier de dimension est téléchargé vers AEM, une copie du fichier est transférée vers un service cloud géré par Adobe hébergé dans Amazon AWS. Ce service convertit le format de fichier de dimension propriétaire Adobe au format glTF standard ouvert. Le modèle 3D converti est conditionné en tant que glTF binaire (`.glb`). AEM stocke le modèle converti avec la ressource Dimension principale comme rendu.

Vous pouvez configurer le format de `.glb` conversion de l’une des deux façons suivantes (voir [Installation et configuration d’AEM 3D](install-config-3d.md) pour obtenir des instructions) :

* Incluez des extensions spécifiques à Adobe pour optimiser la qualité visuelle lors de l’utilisation du lecteur Adobe glTF pour afficher les ressources de dimension dans les ressources AEM, les sites AEM ou les écrans AEM. Cela rend les rendus `.glb` incompatibles avec la plupart des applications tierces.
* Exclure les extensions spécifiques à Adobe pour assurer la compatibilité du `.glb` rendu avec les applications tierces. Cela limite la qualité visuelle lors de l’affichage dans AEM Assets, AEM Sites ou AEM Screens (par exemple, aucun éclairage IBL) afin de simuler la qualité des applications tierces standard.

Le transfert des fichiers Dimension/glTF vers ou depuis Amazon AWS et leur stockage temporaire dans AWS sont entièrement sécurisés. Ces fichiers sont conservés dans Amazon AWS pendant une durée minimale ; généralement, pas plus de quelques minutes pendant les opérations normales.

Pour activer la prise en charge des ressources de dimension, vous devez obtenir des informations d’identification d’Adobe pour accéder au service de conversion. Reportez-vous à la section [Installation et configuration d’AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Si vous installez et utilisez les informations d’identification fournies, vous comprenez et acceptez que vos ressources Adobe Dimension 3D soient transférées vers le service de conversion géré par Adobe en mode cloud hébergé dans Amazon AWS et traitées par lui.

### Affichage sur les ressources AEM {#viewing-on-aem-assets}

Le pack de fonctionnalités AEM 3D comprend une nouvelle visionneuse basée sur la norme d’ouverture glTF utilisée pour afficher les ressources Adobe Dimension. Cette visionneuse est sélectionnée automatiquement lors de l’ouverture d’un fichier de dimension ou d’un fichier glTF compressé dans la vue de détails des ressources AEM ou avec le composant 3D dans les sites AEM.

Notez que l’interface utilisateur du lecteur glTF est quelque peu différente de la visionneuse 3D standard utilisée pour tous les autres types de fichiers 3D.

#### See also the following: {#see-also-the-following}

* [Notes](/help/release-notes/aem3d-release-notes.md) de mise à jour d’AEM 3D pour connaître les restrictions et restrictions applicables aux ressources Dn et à la visionneuse glTF.
* [Utilisation du composant](using-the-3d-sites-component.md) Sites 3D pour les propriétés de composants spécifiques aux ressources Adobe Dimension.
* [Installation et configuration d’AEM 3D](install-config-3d.md) pour configurer le service de conversion en mode cloud.

