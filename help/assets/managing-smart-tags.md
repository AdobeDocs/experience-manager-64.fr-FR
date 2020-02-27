---
title: Gestion des balises actives
description: Mettez à jour ou supprimez les balises actives inexactes pour améliorer la pertinence des balises.
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
translation-type: tm+mt
source-git-commit: 7771cbb218d80247f65e92cbe7e8cdfd9720b75e

---


# Gestion des balises intelligentes {#managing-smart-tags}

Vous pouvez traiter les balises intelligentes pour supprimer les balises inexactes qui ont pu être attribuées aux images de votre marque afin que seules les balises les plus pertinentes soient affichées.

La modération de balises intelligentes contribue également à affiner les résultats des recherches d’images basées sur des balises, en garantissant que votre image apparaisse dans les résultats de la recherche pour les balises les plus pertinentes. Essentiellement, cela réduit les risques que des images non pertinentes apparaissent dans les résultats de la recherche.

Vous pouvez également attribuer un rang supérieur à une balise afin d’accroître son degré de pertinence par rapport à une image. La promotion d’une balise pour une image augmente les risques qu’une image apparaisse dans les résultats de la recherche lorsqu’une recherche est basée sur cette balise.

1. Dans l’encadré Omnisearch, recherchez des ressources sur la base d’une balise.
1. Examinez les résultats de la recherche pour identifier une image que vous ne trouvez pas pertinente.
1. Sélectionnez l’image, puis cliquez/appuyez sur l’icône **[!UICONTROL Gérer les balises]** dans la barre d’outils.
1. Examinez les balises sur la page **[!UICONTROL Gérer les balises]**. Si vous ne souhaitez pas que l’image puisse être recherchée sur la base d’une balise spécifique, sélectionnez la balise, puis cliquez/appuyez sur l’icône **[!UICONTROL Supprimer]** dans la barre d’outils. Sinon, cliquez/appuyez sur le symbole (**[!UICONTROL X]**) qui apparaît en regard du libellé.
1. Pour attribuer un rang supérieur à une balise, sélectionnez-la, puis cliquez/appuyez sur l’icône **[!UICONTROL Convertir]** dans la barre d’outils. La balise faisant l’objet d’une conversion est déplacée dans la section **[!UICONTROL Balises]**.
1. Cliquez/appuyez sur **[!UICONTROL Enregistrer]**, puis sur **[!UICONTROL OK]** pour fermer la boîte de dialogue Succès.
1. Accédez à la page Propriétés de l’image. Remarquez que la balise que vous avez convertie se voit attribuer une pertinence élevée et apparaît donc plus haut dans les résultats de la recherche.

## Comprendre les résultats de recherche AEM avec des balises dynamiques {#understand-search-results-with-smart-tags}

By default, AEM search combines the search terms with an `AND` clause. L’utilisation de balises dynamiques ne modifie pas ce comportement par défaut. Using smart tags adds an additional `OR` clause to find any of the search terms in the applies smart tags. For example, consider searching for `woman running`. Assets with just `woman` or just `running` keyword in the metadata do not appear in the search results by default. However, an asset tagged with either `woman` or `running` using smart taggs appears in such a search query. Les résultats de la recherche sont donc une combinaison de

* ressources avec des mots-clés `woman` et `running` dans les métadonnées.
* ressources avec balise dynamique avec l’un des mots-clés.

Les résultats de recherche qui correspondent à tous les termes de recherche dans les champs de métadonnées s’affichent en premier, suivis des résultats de recherche correspondant à l’un des termes de recherche des balises dynamiques. Dans l’exemple ci-dessus, l’ordre approximatif de l’affichage des résultats de recherche est le suivant :

1. matches of `woman running` in the various metadata fields.
1. correspondances de `woman running` dans les balises actives.
1. matches of `woman` or of `running` in smart tags.
