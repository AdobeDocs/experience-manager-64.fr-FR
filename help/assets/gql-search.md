---
title: Recherche de texte intégral GQL
description: Explorez la fonction de recherche de texte intégral GQL dans [!DNL Experience Manager] Ressources. Utilisez-le pour rechercher des ressources en fonction de métadonnées spécifiques, telles que le titre, la description et le nom de l’auteur.
contentOwner: AG
feature: Search,Metadata
role: User
exl-id: e819501c-4ac3-447f-944c-67adc42e8c61
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 16%

---

# Recherche de texte intégral GQL {#gql-full-text-search}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Explorez la fonction de recherche de texte intégral GQL dans [!DNL Experience Manager] Ressources. Utilisez-le pour rechercher des ressources en fonction de métadonnées spécifiques, telles que le titre, la description et le nom de l’auteur.

La fonction de recherche de texte intégral GQL vous permet de rechercher des ressources en fonction de métadonnées spécifiques, telles que le titre, la description, l’auteur, etc.

Pour rechercher une ressource en fonction de ses métadonnées, par exemple le titre, spécifiez le mot-clé de métadonnées suivi de sa valeur dans le panneau de recherche. La fonction de recherche en texte intégral GQL récupère uniquement les ressources dont les métadonnées correspondent exactement à la valeur saisie.

Par exemple, pour rechercher des ressources dont le titre est &quot;Target&quot;, procédez comme suit :

## Recherche de ressources {#searching-assets}

1. Dans la barre d’outils de l’interface utilisateur d’Assets, cliquez ou appuyez sur le bouton **[!UICONTROL Rechercher]** pour afficher la zone Omni-recherche.

   ![](assets/do-not-localize/chlimage_1.png)

1. Placez le curseur dans la zone Omni-recherche, puis appuyez sur Entrée.
1. Cliquez ou appuyez sur l’icône de navigation globale pour afficher le **[!UICONTROL Filtres]** du panneau.
1. Dans la zone Omni Search, indiquez la valeur &quot;Target&quot;. Pour limiter votre recherche à un dossier spécifique, cliquez ou appuyez sur l’icône Parcourir du panneau Filtres et sélectionnez le dossier. Dans ce cas, la correspondance n’est recherchée que dans le dossier et les sous-dossiers qu’il contient.

   >[!NOTE]
   >
   >Vous pouvez également effectuer une recherche de texte intégral sur un dossier. Dans ce cas, vous devez spécifier un terme de recherche de texte intégral non vide.

   ![gql_search](assets/gql_search.png)

1. Press **[!UICONTROL Entrée]**. Le [!DNL Assets] L’interface utilisateur affiche uniquement les ressources dont le titre correspond exactement à &quot;Target&quot;.

La fonction de recherche de texte intégral GQL vous permet de rechercher des ressources en fonction des éléments suivants :

* Requête complexe créée en combinant via une opération Et, les valeurs que vous spécifiez pour plusieurs champs de métadonnées (propriétés)
* Plusieurs valeurs pour un seul champ de métadonnées
* Correspondances de sous-chaîne

La fonction de recherche en texte intégral GQL vous permet de rechercher des ressources en fonction des propriétés de métadonnées suivantes. Les noms des propriétés (auteur, titre, etc.) ainsi que les valeurs sont sensibles à la casse.

>[!NOTE]
>
>La recherche de texte intégral GQL fonctionne uniquement pour les prédicats de texte intégral.

| Propriété | Format de recherche (valeur de facette) |
|---|---|
| [!UICONTROL Titre] | title:John |
| [!UICONTROL Créateur] | creator:John |
| [!UICONTROL Contributeur] | contributor:John |
| [!UICONTROL Emplacement] | location:India |
| [!UICONTROL Description] | description:&quot;Sample Image&quot; |
| [!UICONTROL Outil créateur] | creatortool:&quot;Adobe Photoshop 7.0&quot; |
| [!UICONTROL Détenteur de copyright] | copyrightowner:&quot;Adobe Systems&quot; |
| [!UICONTROL Contributeur] | contributor:John |
| [!UICONTROL Conditions d’utilisation] | usagewords:&quot;CopyRights reserve&quot; |
| [!UICONTROL Créé] | created:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-JTHH:MM:SS.000+05:30 |
| [!UICONTROL Date d’expiration] | expires:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-JTHH:MM:SS.000+05:30 |
| [!UICONTROL Heure d’activation] | ontime:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-JTHH:MM:SS.000+05:30 |
| [!UICONTROL Heure de désactivation] | offtime:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-JTHH:MM:SS.000+05:30 |
| [!UICONTROL Période] (date d’expiration, heure d’activation, heure d’arrêt) | champ de facette : lowerbound..upperbound |
| [!UICONTROL Chemin] | /content/dam/&lt;nom_dossier> |
| [!UICONTROL Titre du PDF] | pdftitle:&quot;Adobe Document&quot; |
| [!UICONTROL Objet] | subject:&quot;Training&quot; |
| [!UICONTROL Balises] | tags : &quot;Location And Travel&quot; |
| [!UICONTROL Type] | type:&quot;image\png&quot; |
| [!UICONTROL Largeur de l’image] | width:lowerbound.upperbound |
| [!UICONTROL Hauteur de l’image] | height:lowerbound.upperbound |
| [!UICONTROL Personne] | person:John |

Voici quelques exemples de formats de recherche pour des requêtes complexes :

* Pour afficher toutes les ressources avec plusieurs champs de facettes (par exemple : title=John Doe et creator tool=Adobe Photoshop) : 

tiltle:&quot;John Doe&quot; creatortool : Adobe&amp;ast;

* Pour afficher toutes les ressources lorsque la valeur de la facette n’est pas un seul mot mais une phrase (par exemple : title=Scott Reynolds)

title:&quot;Scott Reynolds&quot;

* Pour afficher les ressources avec plusieurs valeurs d’une seule propriété (par exemple : title=Scott Reynolds ou John Doe)

title:&quot;Scott Reynolds&quot; OU &quot;John Doe&quot;

* Pour afficher les ressources avec des valeurs de propriété commençant par une chaîne spécifique (par exemple : Le titre est Scott Reynolds)

title:&quot;Scott&quot;

* Pour afficher les ressources dont les valeurs de propriété se terminent par une chaîne spécifique (par exemple : Le titre est Scott Reynolds)

title:&quot;Reynolds&quot;

* Pour afficher les ressources avec une valeur de propriété contenant une chaîne spécifique (par exemple : title = Salle de réunion de Bâle)

title:&quot;Meeting&quot;;

* Pour afficher les ressources qui contiennent une chaîne spécifique et qui possèdent une valeur de propriété spécifique (par exemple : rechercher des Adobes de chaîne dans les ressources ayant le titre=John Doe) ;

&amp;ast;Adobe&amp;ast; title:&quot;John Doe &quot;OR title:&quot;John Doe&quot; &amp;ast;Adobe&amp;ast;

>[!NOTE]
>
>Les propriétés path, limit, size et orderby ne peuvent pas être combinées à une autre propriété OU.
>
>Le mot-clé d’une propriété générée par un utilisateur correspond au libellé de son champ dans l’éditeur de propriétés en minuscules et sans espace.

>[!NOTE]
>
>Si vous écrivez une requête JCR pour rechercher uniquement des sous-ressources, les ressources référencées correspondantes sont également affichées avec les sous-ressources correspondantes.

La recherche de texte intégral prend également en charge des opérateurs tels que -, ^, etc. Pour rechercher des informations sous forme de chaînes littérales, indiquez la phrase de recherche entre guillemets. Par exemple, entrez « Notebook - Beauté » au lieu de Notebook - Beauté.

## Amélioration de la recherche {#boosting-search}

Vous pouvez améliorer la pertinence des mots-clés pour des ressources particulières afin d’améliorer les recherches basées sur les mots-clés. En d’autres termes, les images pour lesquelles vous convertissez des mots-clés spécifiques apparaissent en haut des résultats de la recherche lorsque vous effectuez une recherche en fonction de ces mots-clés.

1. Dans l’interface utilisateur d’Assets, ouvrez la page des propriétés de la ressource pour laquelle vous souhaitez promouvoir un mot-clé.
1. Basculez vers le **[!UICONTROL Avancé]** et cliquez/appuyez sur **[!UICONTROL Ajouter]** under **[!UICONTROL Élever pour les mots-clés de recherche]**.

   ![elevate_for_search](assets/elevate_for_search.png)

1. Dans la boîte de dialogue **[!UICONTROL Rechercher une promotion]**, indiquez un mot-clé pour lequel vous souhaitez améliorer la recherche d’image, puis cliquez/appuyez sur **[!UICONTROL Ajouter]**. Si nécessaire, indiquez plusieurs mots-clés de la même manière.

   ![add_search_word](assets/add_search_word.png)

1. Cliquez/appuyez sur **[!UICONTROL Enregistrer et fermer]**.
1. Recherchez le mot-clé à l’aide de la zone Omni-recherche. La ressource pour laquelle vous avez promu ce mot-clé apparaît parmi les principaux résultats de recherche.
