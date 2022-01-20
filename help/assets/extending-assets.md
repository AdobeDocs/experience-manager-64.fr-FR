---
title: Personnalisation et extension de ressources
description: Découvrez les moyens par lesquels vous pouvez personnaliser et étendre le Partage de ressources et l’Éditeur de ressources, qui proposent aux utilisateurs une interface et un ensemble de fonctionnalités spécialement adaptés.
contentOwner: AG
feature: Developer Tools
role: Developer
exl-id: 0291690b-874a-483d-901f-f02cb6d8ab28
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 67%

---

# Personnalisation et extension de ressources {#customizing-and-extending-assets}

Asset Editor est le point d’accès Principal que les utilisateurs d’un site web Enterprise Manager d’Adobe vont utiliser pour rechercher, afficher et manipuler les ressources numériques de votre référentiel.

En tant que [!DNL Experience Manager] développeur, vous pouvez personnaliser et étendre l’Éditeur de ressources de différentes manières, en présentant aux utilisateurs une interface et un ensemble de fonctionnalités spécifiquement personnalisés.

Les aspects suivants de la fonctionnalité peuvent être adaptés ou développés :

* [Extension de l’Éditeur de ressources](asseteditorx.md)
* [Extension de la recherche de ressources](searchx.md)
* [Traitement des ressources à l’aide des gestionnaires de médias et des workflows](media-handlers.md)
* [Intégration des ressources avec Flux d’activités](extending-activity-stream.md)
* [Développement d’un proxy Assets](proxy.md)
* [Meilleures pratiques de configuration d’ImageMagick](best-practices-for-imagemagick.md)

## Personnalisation de l’apparence et du comportement {#customizing-the-look-and-feel}

Les aspects suivants de l’apparence de l’Éditeur de ressources sont personnalisables :

* Logo : vous pouvez ajouter le logo de votre entreprise à l’interface.
* Couleurs et polices : vous pouvez changer les couleurs et polices de l’interface.
* Code HTML : pour une personnalisation plus approfondie, vous pouvez modifier le code HTML sous-jacent qui définit les interfaces.

## Personnalisation des rendus {#customizing-renditions}

Dans [!DNL Experience Manager Assets] terminologie : un rendu est le formulaire dans lequel une ressource est présentée. En général, une ressource particulière peut posséder plusieurs rendus. Par exemple, une image en couleur peut avoir un rendu dans sa taille d’origine, une autre à un format réduit et une autre à la fois dans un format réduit et un format converti en niveaux de gris.

Les rendus dans lesquels une ressource particulière est disponible peuvent être personnalisés, et de nouveaux rendus peuvent être créés.
