---
title: Gestion des balises actives
description: Mettez à jour ou supprimez les balises actives inexactes afin d’améliorer la pertinence des balises.
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
translation-type: tm+mt
source-git-commit: 7771cbb218d80247f65e92cbe7e8cdfd9720b75e
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 85%

---


# Gestion des balises intelligentes {#managing-smart-tags}

Vous pouvez traiter les balises actives pour supprimer les balises inexactes qui ont pu être attribuées à vos images de marque afin que seules les balises les plus pertinentes s’affichent.

La modération de balises intelligentes contribue également à affiner les résultats des recherches d’images basées sur des balises, en garantissant que votre image apparaisse dans les résultats de la recherche pour les balises les plus pertinentes. Essentiellement, cela réduit les risques que des images non pertinentes apparaissent dans les résultats de la recherche.

Vous pouvez également attribuer un rang supérieur à une balise afin d’accroître son degré de pertinence par rapport à une image. La promotion d’une balise pour une image augmente les risques qu’une image apparaisse dans les résultats de la recherche lorsqu’une recherche est basée sur cette balise.

1. Dans l’encadré Omnisearch, recherchez des ressources sur la base d’une balise.
1. Examinez les résultats de la recherche pour identifier une image que vous ne trouvez pas pertinente.
1. Sélectionnez l’image, puis cliquez/appuyez sur l’icône **[!UICONTROL Gérer les balises]** dans la barre d’outils.
1. Examinez les balises sur la page **[!UICONTROL Gérer les balises]**. Si vous ne souhaitez pas que l’image puisse être recherchée sur la base d’une balise spécifique, sélectionnez la balise, puis cliquez/appuyez sur l’icône **[!UICONTROL Supprimer]** dans la barre d’outils. Sinon, cliquez/appuyez sur le symbole (**[!UICONTROL X]**) qui apparaît en regard du libellé.
1. Pour attribuer un rang supérieur à une balise, sélectionnez-la, puis cliquez/appuyez sur l’icône **[!UICONTROL Convertir]** dans la barre d’outils. La balise faisant l’objet d’une conversion est déplacée dans la section **[!UICONTROL Balises]**.
1. Cliquez/appuyez sur **[!UICONTROL Enregistrer]**, puis sur **[!UICONTROL OK]** pour fermer la boîte de dialogue de réussite.
1. Accédez à la page Propriétés de l’image. Remarquez que la balise que vous avez convertie se voit attribuer une pertinence élevée et apparaît donc plus haut dans les résultats de la recherche.

## Comprendre les résultats de recherche AEM avec des balises dynamiques  {#understand-search-results-with-smart-tags}

Par défaut, la recherche AEM associe les termes de recherche avec une clause `AND`. L’utilisation de balises intelligentes ne modifie pas ce comportement par défaut. Elle ajoute une clause `OR` supplémentaire pour trouver l’un des termes de recherche dans les balises intelligentes. Par exemple, pour la recherche de `woman running`. Les ressources avec les mots-clés `woman` ou `running` uniquement dans les métadonnées n’apparaissent pas dans les résultats de recherche par défaut. Cependant, un fichier balisé avec `woman` ou `running` à l’aide de balises actives apparaît dans une telle requête de recherche. Les résultats de la recherche sont donc une combinaison de :

* actifs avec les deux mots-clés, `woman` et `running` dans les métadonnées.
* ressources avec balise dynamique avec l’un des mots-clés.

Les résultats de recherche qui correspondent à tous les termes de recherche dans les champs de métadonnées s’affichent en premier, suivis des résultats de recherche correspondant à l’un des termes de recherche des balises dynamiques. Dans l’exemple ci-dessus, l’ordre approximatif de l’affichage des résultats de recherche est le suivant :

1. correspondances de `woman running` dans les différents champs de métadonnées.
1. correspondances de `woman running` dans les balises intelligentes.
1. correspondances de `woman` ou de `running` dans des balises intelligentes.
