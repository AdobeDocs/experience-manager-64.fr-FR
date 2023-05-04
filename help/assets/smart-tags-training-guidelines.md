---
title: Instructions de formation du service de contenu dynamique
description: Formation du service AI pour appliquer des balises intelligentes aux ressources
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: User
exl-id: 14241f8d-fd0b-4bcf-b2bb-1d0e52bf7748
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 68%

---

# Instructions de formation du service de contenu dynamique {#smart-content-service-training-guidelines}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour pouvoir baliser efficacement vos images de marque, le service de contenu dynamique exige que les images d’entraînement respectent certaines instructions.

## Instructions d’entraînement {#guidelines-for-training}

Pour de meilleurs résultats, les images de votre jeu d’entraînement doivent respecter les instructions suivantes :

**Quantité et taille :****minimum 30 images par balise**. Minimum 500 pixels sur le côté le plus long.

**Cohérence** : les images associées à une même balise doivent être visuellement similaires.

Par exemple, il n’est pas recommandé de baliser toutes ces images en tant que *my-party* (pour la formation), car ils ne sont pas visuellement similaires.

![Images d’illustration donnant un exemple d’instructions d’entraînement](assets/do-not-localize/coherence.png)

**Couverture** : les images d’entraînement doivent être suffisamment variées. L’idée est de fournir quelques exemples raisonnablement différents pour apprendre à [!DNL Experience Manager] à se concentrer sur les bons éléments. Si vous appliquez la même balise sur des images visuellement différentes, incluez au moins cinq exemples de chaque type.

Par exemple, pour la balise *mannequin-pose-tête-baissée*, incluez davantage d’images d’entraînement similaires à l’image mise en évidence ci-dessous pour que le service reconnaisse les images similaires avec plus de précision lors du balisage.

![Images d’illustration donnant un exemple d’instructions d’entraînement](assets/do-not-localize/coverage_1.png)

**Distraction/obstruction** : l’entraînement du service donne de meilleurs résultats sur les images qui ont moins de distractions (telles que des arrière-plans importants ou des objets/personnes sans lien avec le sujet principal).

Par exemple, pour la balise *chaussure-décontractée*, la seconde image n’est pas un bon candidat pour l’entraînement.

![Images d’illustration donnant un exemple d’instructions d’entraînement](assets/do-not-localize/distraction.png)

**Complétude :** si une image est admissible pour plusieurs balises, ajoutez toutes les balises applicables avant d’inclure l’image à des fins de formation. Par exemple, pour les balises telles que *raincoat* et *model-side-view*, ajoutez les deux balises sur la ressource éligible avant de l’inclure pour la formation.

![Images d’illustration donnant un exemple d’instructions d’entraînement](assets/do-not-localize/completeness.png)

## Limites {#limitations}

Les balises intelligentes améliorées sont basées sur des modèles d’apprentissage d’images de marque et de leurs balises. Ces modèles ne sont pas toujours parfaits pour identifier les balises. La version actuelle du service de contenu dynamique présente les limites suivantes :

* Impossibilité d’identifier des différences subtiles dans les images. Par exemple, des chemises coupe droite ou ajustée.
* Impossible d’identifier les balises en fonction de petits motifs/parties d’une image. Par exemple, des logos sur des T-shirts.
* Le balisage est pris en charge dans les paramètres régionaux gérés par [!DNL Experience Manager]. Pour obtenir la liste des langues, consultez [Notes de mise à jour du service de contenu dynamique](/help/release-notes/smart-content-service-release-notes.md).

Pour rechercher des ressources avec des balises intelligentes (standard ou améliorées), utilisez la recherche omni-ressource (recherche de texte intégral). Il n’y a aucun prédicat de recherche distinct pour les balises intelligentes.

>[!NOTE]
>
>La capacité du service de contenu dynamique à s’entraîner à partir de vos balises et à les appliquer à d’autres images dépend de la qualité des images que vous utilisez pour l’entraînement.
>
>Pour obtenir des résultats optimaux, Adobe recommande d’utiliser des images visuellement similaires afin d’entraîner le service pour chaque balise.
