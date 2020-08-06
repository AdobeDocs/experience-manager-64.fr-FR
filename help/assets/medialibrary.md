---
title: Comparer les fonctionnalités disponibles dans l’AEM Assets et la bibliothèque de médias AEM
description: Questions fréquentes sur AEM Assets et AEM Media Library, y compris les différences.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 82%

---


# Différence entre AEM Assets et AEM Media Library {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager (AEM) Assets fait partie intégrante de la plateforme AEM. Cette intégration parfaite est vue comme un avantage important d’AEM et garantit une homogénéité de gestion de contenu et de productivité élevée pour les auteurs de contenu. 

## Forum aux questions {#frequently-asked-questions}

### Qu’est-ce qu’AEM Assets ?{#what-is-aem-assets}

AEM Assets est une application de la plateforme AEM qui permet à nos clients de gérer leurs ressources numériques (images, documents, vidéos et clips audio) dans un référentiel basé sur le web. AEM Assets comprend la prise en charge des métadonnées, les rendus, l’outil de recherche de la gestion des actifs numériques et l’interface utilisateur d’administration d’AEM Assets.

### Qu’est-ce que la bibliothèque multimédia AEM ?{#what-is-the-aem-media-library}

La bibliothèque multimédia AEM est un élément désigné du référentiel de contenu de la gestion de contenu web d’AEM où les images et d’autres ressources partagées sont enregistrées. La bibliothèque multimédia utilise les fonctionnalités de gestion des actifs numériques de la gestion de contenu web d’AEM.

### Que m’offre AEM Assets qui ne soit pas déjà inclus dans la gestion de contenu web d’AEM ?   {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Les fonctionnalités uniques disponibles uniquement pour les clients AEM Assets sont : 

1. la possibilité d’extraire et de modifier des métadonnées autres que le titre, les balises et la description.
1. L’administrateur d’AEM Assets, accessible via l’écran de bienvenue en cliquant sur le deuxième bouton à côté de `siteadmin`.
1. Toutes les étapes de flux de travail liées à la gestion des ressources numériques, à savoir l’assimilation AEM ressources, la suppression de AEM Assets, la gestion des sous-ressources AEM Assets, l’extraction des métadonnées AEM Assets.
1. libraries including `dam` im package space.

L’utilisation de ces fonctions nécessite une licence AEM Assets valide.

### AEM Assets est-il disponible en tant que module distinct ?   {#is-aem-assets-available-as-a-separate-package}

Non. Pour faciliter l’installation et le déploiement, toutes les applications et modules complémentaires d’AEM sont fournis dans un module unique dans lequel toutes les fonctionnalités sont incluses. Cela ne signifie pas que vous avez le droit d’utiliser toutes les fonctionnalités incluses dans le module.

#### Je souhaite modifier les métadonnées des ressources numériques. Ai-je besoin d’AEM Assets ?   {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Si vous prévoyez de modifier les métadonnées autres que le titre, la description et les balises, vous aurez besoin d’une licence AEM Assets. 

#### Je souhaite redimensionner automatiquement les images lors de l’importation. Ai-je besoin d’AEM Assets ?   {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

Non. Le redimensionnement et la transformation automatique des images statiques pilotée par workflow, de même que la capacité de gérer les rendus sont inclus dans la bibliothèque multimédia AEM. Ces fonctionnalités ne nécessitent pas de licence AEM Assets.

### Je souhaite redimensionner des images à l’aide d’un composant image personnalisé. Ai-je besoin d’AEM Assets ?   {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

Le composant image fait partie de la gestion du contenu web d’AEM. La bibliothèque d’images utilisée par le composant image (et par AEM Assets) fait partie de la plateforme AEM et ne nécessite de licence AEM Assets. 

### Comment puis-je empêcher mes utilisateurs d’utiliser AEM Assets si je ne dispose pas d’une licence AEM Assets ?{#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

Vous pouvez supprimer tous les workflows, composants, taxonomies et options d’AEM Assets, ainsi que l’administrateur AEM Assets à partir d’AEM. Cela évite aux utilisateurs d’utiliser accidentellement des fonctionnalités AEM Assets que vous n’aviez pas sous licence.

### Je souhaite ajouter des images à une page et recadrer ou redimensionner ces images. Ai-je besoin d’AEM Assets ?   {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

Pour ce cas d’utilisation, il n’est pas nécessaire d’acheter AEM Assets. Il n’est même pas nécessaire d’utiliser la bibliothèque multimédia pour les images d’un site web, car le composant d’image dynamique permet de transférer des images directement dans la page.

>[!MORELIKETHIS]
>
>* [liste détaillée des différences de fonction](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

