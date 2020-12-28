---
title: Rechercher
seo-title: Rechercher
description: L’environnement de création d’AEM comporte divers mécanismes de recherche de contenu, selon le type de ressource que vous utilisez.
seo-description: L’environnement de création d’AEM comporte divers mécanismes de recherche de contenu, selon le type de ressource que vous utilisez.
uuid: b50c8144-1993-441d-8303-fcb6b0f24376
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b20e0f78-9ae4-47ba-8e9a-452a0a78b663
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 87%

---


# Recherche{#search-features}

L’environnement de création d’AEM comporte divers mécanismes de recherche de contenu, selon le type de ressource que vous utilisez.

>[!NOTE]
>
>En dehors de l’environnement de création, il existe d’autres mécanismes de recherche, tels que [Query Builder](/help/sites-developing/querybuilder-api.md) et [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Principes de base de la recherche {#search-basics}

Pour accéder au panneau de recherche, cliquez sur l’onglet **Rechercher** dans la partie supérieure du volet de gauche de la console appropriée.

![chlimage_1-140](assets/chlimage_1-140.png)

Le panneau de recherche vous permet de rechercher sur toutes les pages de votre site Web. Il contient des champs et des widgets pour les éléments suivants :

* **Texte intégral** : recherche du texte indiqué
* **Modifié après/avant** : la recherche porte uniquement sur les pages qui ont été modifiées entre les dates spécifiées.
* **Modèle** : la recherche porte uniquement sur les pages basées sur le modèle spécifié.
* **Balises** : la recherche porte uniquement sur les pages qui comprennent les balises spécifiées.

>[!NOTE]
>
>Lorsque votre instance est configurée pour la [recherche Lucene](/help/sites-deploying/queries-and-indexing.md), vous pouvez utiliser l’expression suivante en **texte intégral** :
>
>* [Caractères génériques](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Wildcard_Searches) 
>* [Opérateurs booléens](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boolean_operators)  

   >
   >
* [Expressions régulières](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Regexp_Searches)
>* [Regroupement de champs](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Field_Grouping) 
>* [Amplification](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boosting_a_Term) 

>



Pour exécuter la recherche, cliquez sur **Rechercher** au bas du volet. Cliquez sur **Réinitialiser** pour effacer les critères de recherche.

## Filtrer {#filter}

Vous pouvez définir (et effacer) un filtre pour préciser les résultats en divers emplacements :

![chlimage_1-141](assets/chlimage_1-141.png)

## Rechercher et remplacer {#find-and-replace}

Dans la console **Sites web**, l’option de menu **Rechercher et remplacer** permet de rechercher et de remplacer plusieurs instances d’une chaîne dans une partie d’un site web.

1. Sélectionnez la page racine, ou le dossier, où doit s’exécuter l’option de recherche et de remplacement.
1. Sélectionnez **Outils**, puis **Rechercher et remplacer** :

   ![screen_shot_2012-02-15at120346pm](assets/screen_shot_2012-02-15at120346pm.png)

1. La boîte de dialogue **Rechercher et remplacer** permet ce qui suit :

   * confirmer le chemin d’accès racine où doit commencer l’opération de recherche ;
   * définir le terme à rechercher ;
   * définir le terme de remplacement ;
   * indiquer si la recherche doit être sensible à la casse ;
   * indiquer si la recherche doit uniquement porter sur des mots entiers (dans le cas contraire, elle porte également sur des sous-chaînes).

   Cliquez sur **Prévisualisation** listes où le terme a été trouvé. Vous pouvez sélectionner/effacer des instances spécifiques à remplacer :

   ![screen_shot_2012-02-15at120719pm](assets/screen_shot_2012-02-15at120719pm.png)

1. Cliquez sur **Remplacer** pour procéder au remplacement de toutes les instances. Vous serez alors invité à confirmer l’opération.

L’étendue par défaut du servlet de recherche et de remplacement couvre les propriétés suivantes :

* `jcr:title`
* `jcr:description`
* `jcr:text`
* `text`

La portée peut être modifiée à l&#39;aide de la console de gestion Web Apache Felix (par exemple, à `http://localhost:4502/system/console/configMgr`). Sélectionnez `CQ WCM Find Replace Servlet (com.day.cq.wcm.core.impl.servlets.FindReplaceServlet)` et configurez l’étendue selon les besoins.

>[!NOTE]
>
>Dans une installation AEM standard, la fonction « Rechercher et remplacer » utilise Lucene comme fonctionnalité de recherche.
>
>Lucene indexe les propriétés de chaîne d’une longueur pouvant atteindre 16k. La recherche ne porte pas sur les chaînes dont la longueur est supérieure à cette valeur.

