---
title: À propos de l’utilisation des scènes dans AEM 3D
seo-title: À propos de l’utilisation des scènes dans AEM 3D
description: Les scènes sont des fichiers légers de scène 3D qui offrent un environnement de visualisation de base.
seo-description: Les scènes sont des fichiers légers de scène 3D qui offrent un environnement de visualisation de base.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
translation-type: tm+mt
source-git-commit: 9cc06c16122b98146c51ac61d7fa27553a9d971e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 69%

---


# À propos de l’utilisation des scènes dans AEM 3D  {#about-the-use-of-stages-in-aem-d}

Les scènes sont des fichiers de scène 3D allégés qui offrent un environnement de visualisation de base (lumières, arrière-plans, plans au sol ou tout autre géométrie fixe), des caméras prédéfinies facultatives et des paramètres de rendu pour moteurs de rendu tiers.

>[!NOTE]
>
>Le format **[!UICONTROL OBJ 3D]** ne prend pas en charge les lumières. Par conséquent, il ne peut pas être utilisé pour fournir des scènes dans AEM 3D.

Le format de fichier de la scène détermine le rendu que vous pouvez utiliser avec cette scène. Par exemple, si Autodesk® Maya® est utilisé pour un rendu de haute qualité, la scène doit être au format `.ma` ou `.mb`. Si vous avez l’intention d’utiliser uniquement le rendu Rapid Refine™ par défaut, tout format de fichier de scène pris en charge est acceptable.

Tous les paramètres de rendu dans AEM 3D, à l’exception du type et de la taille de l’image de sortie, doivent être préconfigurés et enregistrés dans le fichier d’étape avant le téléchargement vers AEM.