---
title: Rechercher
seo-title: Search
description: L’environnement de création d’AEM comporte divers mécanismes de recherche de contenu, selon le type de ressource que vous utilisez.
seo-description: The author environment of AEM provides various mechanisms for searching for content, dependent on the resource type.
uuid: b50c8144-1993-441d-8303-fcb6b0f24376
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b20e0f78-9ae4-47ba-8e9a-452a0a78b663
exl-id: 9c1d8969-6aa6-41b9-a797-3e6431475fc6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 48%

---

# Rechercher{#search-features}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’environnement de création d’AEM comporte divers mécanismes de recherche de contenu, selon le type de ressource que vous utilisez.

>[!NOTE]
>
>En dehors de l’environnement de création, d’autres mécanismes sont également disponibles pour la recherche, tels que le [Query Builder](/help/sites-developing/querybuilder-api.md) et [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Principes de base de la recherche {#search-basics}

Pour accéder au panneau de recherche, cliquez sur l’onglet **Rechercher** dans la partie supérieure du volet de gauche de la console appropriée.

![chlimage_1-140](assets/chlimage_1-140.png)

Dans le panneau de recherche, vous pouvez effectuer des recherches dans toutes les pages de votre site Web. Il contient des champs et des widgets pour les éléments suivants :

* **Texte intégral**: Recherche du texte spécifié
* **Modifié après/avant**: Recherche uniquement les pages qui ont été modifiées entre les dates spécifiques
* **Modèle**: Recherche uniquement ces pages en fonction du modèle spécifié
* **Balises**: Recherche uniquement les pages contenant les balises spécifiées

>[!NOTE]
>
>Lorsque votre instance est configurée pour la [recherche Lucene](/help/sites-deploying/queries-and-indexing.md), vous pouvez utiliser l’expression suivante en **texte intégral** :
>
>* [Caractères génériques](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Wildcard_Searches)
>* [Opérateurs booléens](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boolean_operators)
>
>* [Expressions régulières](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Regexp_Searches)
>* [Regroupement de champs](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Field_Grouping)
>* [Amélioration](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boosting_a_Term)
>


Exécutez la recherche en cliquant sur **Rechercher** au bas du volet. Cliquez sur **Réinitialiser** pour effacer les critères de recherche.

## Filtrer {#filter}

À différents emplacements, un filtre peut être défini (et effacé) pour analyser en profondeur et affiner votre vue :

![chlimage_1-141](assets/chlimage_1-141.png)

## Rechercher et remplacer {#find-and-replace}

Dans le **Sites web** console **Chercher et Remplacer** l’option de menu vous permet de rechercher et de remplacer plusieurs instances d’une chaîne dans une section du site web.

1. Sélectionnez la page racine, ou le dossier, dans lequel vous souhaitez que l’action de recherche et de remplacement soit effectuée.
1. Sélectionner **Outils** then **Chercher et Remplacer**:

   ![screen_shot_2012-02-15at120346pm](assets/screen_shot_2012-02-15at120346pm.png)

1. Le **Chercher et Remplacer** La boîte de dialogue effectue les opérations suivantes :

   * confirme le chemin racine où l’action de recherche doit commencer
   * définit le terme à rechercher.
   * définit le terme qui doit le remplacer ;
   * indique si la recherche doit être sensible à la casse
   * indique si seuls des mots entiers doivent être trouvés (sinon des sous-chaînes sont également trouvées)

   Cliquez sur **Aperçu** pour savoir où a été trouvé le terme. Vous pouvez sélectionner/désélectionner des instances spécifiques à remplacer :

   ![screen_shot_2012-02-15at120719pm](assets/screen_shot_2012-02-15at120719pm.png)

1. Cliquez sur **Remplacer** pour remplacer toutes les instances. Vous serez alors invité à confirmer l’opération.

L’étendue par défaut du servlet de recherche et de remplacement couvre les propriétés suivantes :

* `jcr:title`
* `jcr:description`
* `jcr:text`
* `text`

L’étendue peut être modifiée à l’aide de la console de gestion Web Apache Felix (par exemple, `http://localhost:4502/system/console/configMgr`). Sélectionnez `CQ WCM Find Replace Servlet (com.day.cq.wcm.core.impl.servlets.FindReplaceServlet)` et configurez l’étendue suivant les besoins.

>[!NOTE]
>
>Dans une installation d’AEM standard, Find and Replace utilise Lucene comme fonctionnalité de recherche.
>
>Lucene indexe les propriétés de chaîne d’une longueur maximale de 16 Ko. Les chaînes en trop ne seront pas recherchées.
