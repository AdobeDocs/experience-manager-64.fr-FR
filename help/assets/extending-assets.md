---
title: Personnalisation et extension de ressources
description: Découvrez les moyens par lesquels vous pouvez personnaliser et étendre le Partage de ressources et l’Éditeur de ressources, qui proposent aux utilisateurs une interface et un ensemble de fonctionnalités spécialement adaptés.
contentOwner: AG
feature: Developer Tools
role: Developer
exl-id: 0291690b-874a-483d-901f-f02cb6d8ab28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 45%

---

# Personnalisation et extension de ressources {#customizing-and-extending-assets}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’Éditeur de ressources est le point d’accès principal que les utilisateurs d’un site Web Adobe Enterprise Manager utiliseront pour rechercher, afficher et manipuler les ressources numériques dans votre référentiel.

En tant que développeur [!DNL Experience Manager], vous pouvez personnaliser et étendre l’Éditeur de ressources de multiples façons pour proposer aux utilisateurs une interface et un ensemble de fonctionnalités adaptés spécialement à leurs besoins.

Les aspects suivants de la fonctionnalité peuvent être adaptés ou développés :

* [Extension de l’Éditeur de ressources](asseteditorx.md)
* [Extension de la recherche de ressources](searchx.md)
* [Traitement des ressources à l’aide des workflows et des gestionnaires de médias](media-handlers.md)
* [Intégration de ressources à un flux d’activités](extending-activity-stream.md)
* [Développement de proxy Assets](proxy.md)
* [Bonnes pratiques pour la configuration d’ImageMagick](best-practices-for-imagemagick.md)

## Personnalisation de l’apparence et du ressenti {#customizing-the-look-and-feel}

Les aspects suivants de l’aspect et du comportement de l’Éditeur de ressources sont personnalisables :

* Logo : Vous pouvez ajouter le logo de votre propre organisation à l’interface.
* Couleurs et polices : Vous pouvez modifier les couleurs et les polices utilisées dans l’interface.
* Code HTML : Pour une personnalisation plus approfondie, vous pouvez modifier le code de HTML sous-jacent qui définit les interfaces.

## Personnalisation des rendus {#customizing-renditions}

Dans la terminologie d’[!DNL Experience Manager Assets], un rendu est la forme dans laquelle une ressource est présentée. En règle générale, une ressource particulière peut comporter plusieurs rendus. Par exemple, une image en couleur peut avoir un rendu dans sa taille d’origine, un autre dans sa taille réduite et un autre dans sa taille réduite et converti en niveaux de gris.

Les rendus qu’une ressource particulière est disponible dans peuvent être personnalisés et de nouveaux rendus créés.
