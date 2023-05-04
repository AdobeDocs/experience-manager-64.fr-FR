---
title: Prise en charge des métadonnées IPTC
description: Découvrez comment Adobe Experience Manager Assets prend en charge les métadonnées IPTC, les évaluations des créations et les mots-clés ajoutés aux ressources par le biais d’Adobe Bridge et d’autres applications de création.
contentOwner: AG
feature: Metadata
role: User,Admin,Leader
exl-id: 3e22e8e4-3675-4d6d-94f4-fc1a4d4801e8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 37%

---

# Prise en charge des métadonnées IPTC {#support-for-iptc-metadata}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Découvrez comment Adobe Experience Manager Assets prend en charge les métadonnées IPTC, les évaluations des créations et les mots-clés ajoutés aux ressources par le biais d’Adobe Bridge et d’autres applications de création.

Adobe Experience Manager Assets prend en charge la norme de métadonnées IPTC qui est largement utilisée pour décrire les ressources. Cela permet à [!DNL Experience Manager Assets] de bénéficier d’une plus large acceptation de ses images auprès des différents intervenants, y compris les photographes, les agences de création, les bibliothèques, les musées, etc.

Le schéma de métadonnées par défaut des ressources intègre désormais les schémas de métadonnées IPTC Core et IPTC Extension afin de définir des propriétés de métadonnées complètes qui permettent aux utilisateurs d’ajouter des données précises et fiables sur les personnes, les emplacements et les produits affichés dans une image. Il prend également en charge les dates, les noms et les identifiants concernant la création de l’image, ainsi qu’une manière flexible d’exprimer les informations sur les droits.

La page Propriétés des ressources comprend désormais des onglets distincts pour afficher les métadonnées IPTC Core et IPTC Extension dans les champs modifiables.

1. Dans l’interface utilisateur Assets, sélectionnez une image.
1. Cliquez ou appuyez sur **[!UICONTROL Propriétés]** dans la barre d’outils.
1. Sur la page Propriétés, cliquez/appuyez sur l’onglet **[!UICONTROL IPTC]** pour afficher les métadonnées IPTC de la ressource.
1. Modifiez les propriétés de métadonnées IPTC, selon les besoins.

   ![iptc_tab](assets/iptc_tab.png)

1. Cliquez ou appuyez sur l’onglet **[!UICONTROL Extension IPTC]** pour afficher les métadonnées d’extension IPTC de la ressource.
1. Modifiez les propriétés de métadonnées d’extension IPTC, selon les besoins.
1. Appuyez ou cliquez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer les modifications.

## Prise en charge de l’évaluation de la création {#creative-rating-support}

Outre les évaluations individuelles et cumulées, la page Propriétés affiche désormais les évaluations affectées à des ressources par le biais d’Adobe Bridge et d’autres applications Creative.

Ces évaluations sont disponibles dans la section **[!UICONTROL Évaluation de la création]** de l’onglet **[!UICONTROL Avancé]**.

Cette évaluation est une propriété en lecture seule et se situe entre 1 et 5. Vous pouvez rechercher des ressources en fonction de leur évaluation créative dans le panneau de recherche.

Toutefois, cette propriété n’est actuellement pas indexée pour éviter tout conflit avec les modifications personnalisées effectuées par les utilisateurs.

## Prise en charge des mots-clés {#keyword-support}

Le **[!UICONTROL IPTC]** L’onglet de la page Propriétés affiche également les mots-clés ajoutés aux ressources par le biais d’Adobe Bridge et d’autres applications Creative. Vous pouvez aussi modifier ces mots-clés et en ajouter d’autres à partir de l’onglet **[!UICONTROL IPTC]**.

![mots-clés](assets/keywords.png)
