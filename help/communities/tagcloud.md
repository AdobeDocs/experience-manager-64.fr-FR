---
title: Utilisation de Social Tag Cloud
seo-title: Using Social Tag Cloud
description: Ajout d’un composant Nuage de balises sociales à une page
seo-description: Adding a Social Tag Cloud component to a page
uuid: 8c400030-976c-457a-bb5f-e473909647a9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 23a5a65e-774d-4789-9659-09e8be0c2bcd
exl-id: 3f55a02c-2733-4f69-8112-7c6c4c98938c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 6%

---

# Utilisation de Social Tag Cloud {#using-social-tag-cloud}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Le `Social Tag Cloud` Le composant met en surbrillance les balises appliquées par les membres de la communauté lors de la publication de contenu. Il permet d’identifier les sujets de tendance et de permettre aux visiteurs du site de localiser rapidement le contenu balisé.

Pour un autre moyen d’identifier les tendances actuelles, consultez [Tendances des activités](trends.md).

Cette page documente les `Social Tag Cloud` paramètres de la boîte de dialogue du composant et décrit l’expérience utilisateur.

Pour plus d’informations sur les développeurs, voir [Notions fondamentales sur les balises](tag.md).

Consultez la section [Administration des balises](../../help/sites-administering/tags.md) pour savoir comment créer et gérer des balises et déterminer à quel contenu elles ont été appliquées.

## Ajout d’un nuage de balises sociales {#adding-a-social-tag-cloud}

Pour ajouter une `Social Tag Cloud` sur une page en mode création, utilisez l’explorateur de composants pour accéder à `Communities / Social Tag Cloud` et faites-le glisser sur la page où le nuage de balises doit apparaître.

Pour obtenir les informations nécessaires, consultez la section [Principes de base des composants des communautés](basics.md).

Lorsque la variable [bibliothèques côté client requises](tag.md#essentials-for-client-side) sont incluses, c’est ainsi que la variable `Social Tag Cloud` apparaît :

![chlimage_1-303](assets/chlimage_1-303.png)

## Configuration du cloud de balises sociales {#configuring-social-tag-cloud}

Sélectionnez le `Social Tag Cloud` pour accéder au composant et le sélectionner. `Configure` qui ouvre la boîte de dialogue de modification.

![chlimage_1-304](assets/chlimage_1-304.png)

Sous , **[!UICONTROL Nuage de balises sociales]** , spécifiez les balises à afficher et, si les balises sont des liens principaux, l’emplacement de la page pour les résultats de la recherche :

![chlimage_1-305](assets/chlimage_1-305.png)

* **[!UICONTROL Balises sociales à afficher]**
Identifiez les balises UGC à afficher. Les options de la liste déroulante sont les suivantes :

   * `From page and child pages`
   * `All tags`

   La valeur par défaut est `From page and child pages`, où &quot;page&quot; fait référence à la variable **Page** ci-dessous.

* **[!UICONTROL Page]**
(obligatoire si non 
`All tags)` Chemin d’accès au contenu généré par l’utilisateur pour une page. La valeur par défaut est la page active si rien n’est indiqué.

* **[!UICONTROL Aucun lien sur les balises]**
Si cette case est cochée, les balises s’affichent dans le nuage de balises sous forme de texte brut. Si cette option n’est pas cochée, les balises s’affichent sous la forme de principaux liens qui effectuent une recherche sur tout le contenu auquel cette balise est appliquée. La valeur par défaut n’est pas cochée et requiert le **[!UICONTROL Chemin du résultat de la recherche]** à définir.

* **[!UICONTROL Chemin du résultat de la recherche]**
Chemin d’accès à une page sur laquelle un 
`Search Result` Le composant a été placé, configuré pour référencer le contenu généré par l’utilisateur qui inclut le chemin d’accès créé par l’utilisateur spécifié par la variable **Page** .

## Modification de l’affichage du Nuage de balises sociales {#change-display-of-social-tag-cloud}

Pour modifier l’affichage de la variable **Nuage de balises sociales**, saisissez [Mode de conception](../../help/sites-authoring/default-components-designmode.md) et double-cliquez sur le `Social Tag Cloud` pour ouvrir une boîte de dialogue avec un onglet supplémentaire.

En utilisant la variable **[!UICONTROL Nuage de balises sociales (conception)]** , indiquez le mode d’affichage des balises. Une balise peut être une balise simple, un seul mot dans l’espace de noms par défaut ou une taxonomie hiérarchique :

![chlimage_1-306](assets/chlimage_1-306.png)

* **[!UICONTROL Afficher les chemins complets du titre]**
Si cette case est cochée, les titres des balises parentes et de l’espace de noms de chaque balise appliquée s’affichent.

   Par exemple :

   * Cochée: `Geometrixx Media: Gadgets / Cars`
   * Non cochée: `Cars`

   Il n’y a aucune différence pour une balise simple.

   La case par défaut est décochée.

* **[!UICONTROL Afficher uniquement les balises terminales]**
Si cette case est cochée, seules les balises appliquées ne contiennent aucune autre balise.

   Par exemple, étant donné l’ID de balise de

   `Geometrixx Media: Gadgets / Cars`

   Trois balises peuvent être appliquées : `Geometrixx Media (the namespace)`, `Gadgets`, et `Cars`

   * Cochée : only `Cars` s’affiche, le cas échéant.
   * Non coché : `Geometrixx Media` et `Gadgets`ainsi que `Cars` s’affiche, le cas échéant.

   Une balise simple est une balise terminale.

   La case par défaut est décochée.

* **[!UICONTROL Modèle de lien]**
Modèle, autre qu’un modèle par défaut, utilisé pour afficher les liens dans un nuage de balises, lorsque les liens sont activés par le biais de la boîte de dialogue de modification des composants.

* **[!UICONTROL Même taille pour toutes les balises]**
Si cette case est cochée, tous les mots du nuage de balises sont stylisés de la même manière. Si cette option n’est pas cochée, le style des mots varie en fonction de leur utilisation. La case par défaut est décochée.

## Informations supplémentaires {#additional-information}

Vous trouverez plus d’informations sur la [Notions fondamentales sur les balises](tag.md) pour les développeurs.

Voir [Balisage du contenu généré par l’utilisateur](tag-ugc.md) (contenu généré par l’utilisateur) pour plus d’informations sur la création et la gestion des balises.
