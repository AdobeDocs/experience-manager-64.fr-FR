---
title: Gestion des balises intelligentes
description: Mettre à jour ou supprimer les balises intelligentes inexactes pour améliorer la pertinence des balises
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: User
exl-id: 05f43e43-ac72-4ab1-a373-687c137d2bed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 44%

---

# Gestion des balises intelligentes {#managing-smart-tags}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez organiser les balises intelligentes pour supprimer les balises inexactes qui peuvent avoir été affectées à vos images de marque afin que seules les balises les plus pertinentes s’affichent.

La modération de balises intelligentes contribue également à affiner les résultats des recherches d’images basées sur des balises, en garantissant que votre image apparaisse dans les résultats de la recherche pour les balises les plus pertinentes. Essentiellement, cela permet d’éliminer les risques d’affichage d’images sans rapport dans les résultats de recherche.

Vous pouvez également attribuer un rang supérieur à une balise pour accroître sa pertinence par rapport à une image. La promotion d’une balise pour une image augmente les risques qu’une image apparaisse dans les résultats de la recherche lorsqu’une recherche est basée sur cette balise.

1. Dans la zone Omni-recherche, recherchez des ressources en fonction d’une balise.
1. Examinez les résultats de la recherche pour identifier une image que vous ne trouvez pas pertinente.
1. Sélectionnez l’image, puis cliquez/appuyez sur la propriété **[!UICONTROL Gestion des balises]** dans la barre d’outils.
1. Examinez les balises sur la page **[!UICONTROL Gérer les balises]**. Si vous ne souhaitez pas que l’image soit recherchée sur la base d’une balise spécifique, sélectionnez la balise, puis cliquez/appuyez sur la balise **[!UICONTROL Supprimer]** dans la barre d’outils. Vous pouvez également cliquer/appuyer sur le (**[!UICONTROL X]**) qui s’affiche en regard du libellé.
1. Pour attribuer un rang supérieur à une balise, sélectionnez-la, puis cliquez/appuyez sur la balise **[!UICONTROL Convertir]** dans la barre d’outils. La balise faisant l’objet d’une conversion est déplacée dans la section **[!UICONTROL Balises]**.
1. Cliquez/appuyez sur **[!UICONTROL Enregistrer]**, puis sur **[!UICONTROL OK]** pour fermer la boîte de dialogue de réussite.
1. Accédez à la page des propriétés de l’image. Remarquez que la balise que vous avez convertie se voit attribuer une pertinence élevée et apparaît donc plus haut dans les résultats de la recherche.

## Comprendre les résultats de recherche [!DNL Experience Manager] avec les balises intelligentes {#understand-search-results-with-smart-tags}

Par défaut, la recherche [!DNL Experience Manager] associe les termes de recherche avec une clause `AND`. L’utilisation de balises intelligentes ne modifie pas ce comportement par défaut. Elle ajoute une clause `OR` supplémentaire pour trouver l’un des termes de recherche dans les balises intelligentes. Par exemple, pour la recherche de `woman running`. Les ressources avec les mots-clés `woman` ou `running` uniquement dans les métadonnées n’apparaissent pas dans les résultats de recherche par défaut. Cependant, une ressource balisée avec l’une des fonctions suivantes : `woman` ou `running` l’utilisation de balises intelligentes apparaît dans une telle requête de recherche. Les résultats de la recherche sont donc une combinaison de :

* ressources avec les deux mots-clés, `woman` et `running` dans les métadonnées.
* ressources balisées intelligemment avec l’un des mots-clés.

Les résultats de recherche qui correspondent à tous les termes de recherche des champs de métadonnées sont affichés en premier, suivis des résultats de recherche qui correspondent à l’un des termes de recherche des balises intelligentes. Dans l’exemple ci-dessus, l’ordre approximatif d’affichage des résultats de recherche est le suivant :

1. correspondances de `woman running` dans les différents champs de métadonnées.
1. correspondances de `woman running` dans les balises intelligentes.
1. correspondances de `woman` ou de `running` dans des balises intelligentes.
