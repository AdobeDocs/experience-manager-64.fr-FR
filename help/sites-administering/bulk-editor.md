---
title: Éditeur en bloc
seo-title: The Bulk Editor
description: Découvrez comment utiliser l’éditeur en bloc.
seo-description: Learn how to use the Bulk Editor.
uuid: 65158ea4-d0fb-4992-99c6-d4b4fa4c87d2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 4da555b4-7fb2-4d55-b29f-8bd21f474c1a
exl-id: 61d85393-2764-447d-afcc-3af1d99e8dbb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 65%

---

# Éditeur en bloc{#the-bulk-editor}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’éditeur en bloc permet une modification très efficace lorsque le contexte visuel de la page n’est pas nécessaire, car il vous permet d’effectuer les opérations suivantes :

* de chercher (et d’afficher) le contenu de plusieurs pages, à l’aide du langage de requête de Google (Google Query Language, GQL) ;
* de modifier directement ce contenu dans l’éditeur en bloc ;
* d’enregistrer les modifications (dans les pages d’origine) ;
* d’exporter ce contenu vers un fichier de feuille de calcul de données séparées par des tabulations (.tsv).

>[!NOTE]
>
>Vous pouvez également importer du contenu dans le référentiel, mais cette option est désactivée par défaut pour l’éditeur en bloc comme disponible dans la variable **Outils** console.

Cette section décrit comment utiliser l’éditeur en bloc dans la console **Outils**. En général, les administrateurs utilisent l’éditeur en bloc pour chercher et modifier différents éléments. Cette opération est effectuée en renseignant le tableau à l’aide d’une requête GQL, puis en sélectionnant les éléments de contenu sur lesquels travailler. Les créateurs utilisent généralement l’éditeur en bloc dans le cadre d’une application d’éditeur en bloc personnalisée par le biais du composant [Liste de produits](/help/sites-authoring/default-components.md).

>[!CAUTION]
>
>Avec le [abandon de l’interface utilisateur classique](/help/release-notes/deprecated-removed-features.md) dans AEM 6.4, l’éditeur en bloc a également été abandonné et, par conséquent, Adobe ne prévoit pas d’améliorer davantage l’éditeur en bloc.

## Exemple de cas d’utilisation pour l’éditeur en bloc {#example-use-case-for-the-bulk-editor}

Par exemple, si vous avez besoin de tous les noms et adresses électroniques des utilisateurs qui ont rempli une enquête spécifique, l’éditeur en bloc peut fournir ces informations et vous pouvez les exporter dans une feuille de calcul.

Le site web de Geometrixx fournit un exemple illustrant ce cas pratique :

1. Accédez au **Assistance** puis à la page **Satisfaction de la clientèle** enquête.
1. **Modifiez** le paragraphe **Début du formulaire**. Dans la boîte de dialogue, cliquez sur **Avancé** , développez l’onglet **Configuration d’action**, puis cliquez sur **Afficher les données...**.

   ![customSurvey](assets/custsatsurvey.png)

1. L’éditeur en bloc est entièrement personnalisable, même si, dans cet exemple, il ne permet pas aux utilisateurs de modifier le contenu, mais seulement d’exporter les informations vers une feuille de calcul.

   ![bulkeditor](assets/bulkeditor.png)

## Utilisation de l’éditeur en bloc {#how-to-use-the-bulk-editor}

L’éditeur en bloc vous permet d’effectuer les opérations suivantes :

* [de rechercher du contenu en fonction de paramètres de requête afin d’afficher les propriétés spécifiées des résultats dans des colonnes, de modifier ce contenu et d’enregistrer les modifications ;](#searching-and-editing-content)
* [d’exporter ce contenu vers une feuille de calcul de données séparées par des tabulations ;](#exporting-content)

* [d’importer le contenu d’une feuille de calcul de données séparées par des tabulations.](#importing-content)

### Recherche et modification de contenu {#searching-and-editing-content}

Pour utiliser l’éditeur en bloc afin de modifier plusieurs éléments simultanément :

1. Dans le **Outils** , cliquez sur la console **Importateurs** pour le développer.
1. Double-cliquez sur le **Éditeur en bloc** pour l’ouvrir.
1. Saisissez vos exigences de sélection :

<table> 
 <tbody> 
  <tr> 
   <td>Champ</td> 
   <td>Propriété</td> 
  </tr> 
  <tr> 
   <td>Chemin racine</td> 
   <td>Indique le chemin racine que recherche l’éditeur en bloc.<br /> Par exemple, <code>/content/geometrixx/en</code>. L’éditeur en bloc effectue une recherche dans tous les nœuds enfants.</td> 
  </tr> 
  <tr> 
   <td>Paramètres de requête</td> 
   <td>À l’aide des paramètres GQL, saisissez la chaîne de recherche que l’éditeur en bloc doit rechercher dans le référentiel ; par exemple, <code>type:Page</code> recherche toutes les pages du chemin racine, <code>text:professional</code> recherche toutes les pages qui contiennent le mot « professional » et <code>"jcr:title":English</code> recherche toutes les pages dont le titre est « English ». Vous pouvez rechercher uniquement des chaînes.</td> 
  </tr> 
  <tr> 
   <td>Case à cocher Mode Contenu</td> 
   <td>Cochez cette case pour lire les propriétés dans le sous-nœud <code>jcr:content</code> des résultats de recherche, s’il existe. À utiliser uniquement pour des pages. Les noms de propriété comportent le préfixe <code>"jcr:content/"</code></td> 
  </tr> 
  <tr> 
   <td>Propriétés/Colonnes</td> 
   <td>Cochez les cases correspondant aux propriétés que l’éditeur en bloc doit renvoyer. Les propriétés que vous sélectionnez sont les titres de colonne dans le volet de résultats. Par défaut, le chemin du noeud est affiché dans les résultats.</td> 
  </tr> 
  <tr> 
   <td>Propriétés / Colonnes personnalisées</td> 
   <td>Saisissez d’autres propriétés qui ne sont pas répertoriées dans le champ <strong>Propriétés/Colonnes</strong>. Ces propriétés personnalisées s’affichent dans le volet de résultats. Vous pouvez ajouter plusieurs propriétés en les séparant par des virgules. <i>Remarque :</i> si vous ajoutez une propriété personnalisée qui n’existe pas encore, la gestion de contenu Web AEM affiche une cellule vide. Lorsque vous modifiez la cellule vide et que vous l’enregistrez, la propriété est ajoutée au nœud. La propriété nouvellement créée doit respecter les contraintes de type de noeud et les espaces de noms de propriété.</td> 
  </tr> 
 </tbody> 
</table>

Par exemple :

![searchfilter](assets/searchfilter.png)

1. Cliquez sur **Rechercher**. L’éditeur en bloc affiche les résultats.

   Pour l’exemple ci-dessus, toutes les pages qui correspondent aux critères de recherche sont renvoyées et affichées avec les colonnes demandées.

   ![chlimage_1-238](assets/chlimage_1-238.png)

1. Apportez les modifications nécessaires en double-cliquant dans une cellule.

   ![srchresult](assets/srchresultedit.png)

1. Cliquez sur **Enregistrer** pour enregistrer les modifications (le bouton **Enregistrer** est activé une fois que vous avez modifié une cellule).

   >[!CAUTION]
   >
   >Les modifications que vous apportez sont écrites dans le contenu du référentiel, par exemple la page référencée dans **Chemin d’accès**.

#### Paramètres de requête GQL supplémentaires {#additional-gql-query-parameters}

* **path :** effectue une recherche uniquement sur les nœuds sous ce chemin d’accès. Si vous spécifiez plusieurs termes avec un préfixe de chemin d’accès, seul le dernier terme sera pris en compte.
* **type :** renvoie uniquement les nœuds des types déterminés. Cela inclut le type principal, ainsi que les types Mixin. Vous pouvez spécifier plusieurs types de nœuds séparés par des virgules. GQL renvoie les noeuds de l’un des types spécifiés.
* **order :** organise le résultat en fonction des propriétés données. Vous pouvez spécifier plusieurs noms de propriété séparés par des virgules. Pour contrôler le résultat dans l’ordre descendant, ajoutez simplement le préfixe « - » (moins) au nom de la propriété. Par exemple : order:-nom. Si vous utilisez un signe « + » (plus), le résultat est renvoyé dans l’ordre ascendant, qui est également le l’ordre par défaut.
* **limit :** limite le nombre de résultats à l’aide d’un intervalle. Par exemple : limit:10..20. Notez que l’intervalle est basé sur zéro, le début étant inclusif et la fin, exclusive. Vous pouvez également spécifier un intervalle ouvert :limit:10.. ou limit:..20. Si les points sont omis et qu’une seule valeur est spécifiée, GQL renvoie, au maximum, ce nombre de résultats. Par exemple : limit:10 (renvoie les 10 premiers résultats).

### Exportation de contenu {#exporting-content}

Vous pouvez avoir besoin d’exporter du contenu et d’y apporter des modifications dans une feuille de calcul Excel. Par exemple, vous pouvez exporter une liste de diffusion et modifier l’indicatif régional de tous les numéros de téléphone répertoriés directement dans Excel, ajouter des lignes supplémentaires, etc.

Pour exporter du contenu :

1. Recherchez du contenu comme décrit dans [Recherche et modification de contenu](#searching-and-editing-content).
1. Cliquez sur **Exporter** pour exporter les modifications dans une feuille de calcul Excel de données séparées par des tabulations. AEM WCM vous demande où vous souhaitez télécharger le fichier.

   >[!NOTE]
   >
   >Par défaut, les modifications sont codées en [Windows-1252](https://fr.wikipedia.org/wiki/Windows-1252) (également appelé « CP-1252 »). Vous pouvez cocher UTF-8 pour exporter les modifications au format UTF-8.

   ![srchrsesultexport](assets/srchrsesultexport.png)

1. Sélectionnez l’emplacement et confirmez que vous souhaitez télécharger le fichier.
1. Une fois que vous avez téléchargé le fichier, vous pouvez l’ouvrir dans votre tableur, par exemple, Microsoft Excel. Le tableur importe le fichier et le convertit au format tableur.

   ![exportinexcel](assets/exportinexcel.png)

### Importation de contenu {#importing-content}

Par défaut, la fonctionnalité d’importation est masquée lorsque vous ouvrez l’éditeur en bloc. Il suffit d’ajouter le paramètre `hib=false` à l’adresse URL pour afficher le bouton **Importer** dans la page Éditeur en bloc. Vous pouvez importer du contenu à partir de n’importe quel fichier de données séparées par des tabulations (`.tsv`). Pour que l’importation fonctionne correctement, les en-têtes de colonne (première ligne de cellules) doivent correspondre aux en-têtes de colonne du tableau dans lequel vous importez.

>[!NOTE]
>
>Lorsque vous réimportez le contenu, vous effacez le contenu existant de ces nœuds. Veillez à ne pas remplacer des informations importantes.

Pour importer du contenu :

1. Ouvrez l’éditeur en bloc.
1. Ajoutez `?hib=false` à l’URL, par exemple :

   `http://localhost:4502/etc/importers/bulkeditor.html?hib=false`

1. Cliquez sur **Importer**.
1. Sélectionnez le fichier `.tsv`. Les données sont importées dans le référentiel.
