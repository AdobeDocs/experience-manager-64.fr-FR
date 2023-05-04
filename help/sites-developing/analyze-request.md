---
title: Script d’analyse des requêtes
seo-title: Request Analysis Script
description: Le script d’analyse des requêtes est conçu pour faciliter l’analyse des fichiers access.log et produire un rapport lisible en vue d’un traitement ultérieur.
seo-description: The request analysis script is made to ease the analysis of the access.log files producing a readable report for later processing
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: 8582bbca-c11a-4880-88ba-da22e0301dba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 76%

---

# Script d’analyse des requêtes{#request-analysis-script}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Télécharger {#download}

Ce script facilite l’analyse des fichiers `access.log` et génère un rapport lisible pour vos activités de traitement ultérieures.

[Obtenir le fichier](assets/analyse-access.sh)

## Description {#description}

Ce script facilite l’analyse des fichiers `access.log` et génère un rapport lisible pour vos activités de traitement ultérieures.

Il produit le nombre global de requêtes, GET vs POST, la répartition des requêtes au fil du temps, etc.

La sortie est présentée en syntaxe Markdown facile à convertir au format PDF avec des outils comme pandoc ou à présenter dans un navigateur avec des modules externes comme l’observateur Markdown.

Il peut également analyser le chemin personnalisé saisi dans la ligne de commande.

Se servir du commentaire dans le fichier qui vous indique comment l’exécuter :

Analysez le CQ `access.log` en extrapolant diverses informations et en générant une sortie MarkDown sur `stdout`.

## Utilisation {#usage}

`./analyse-access.sh access.log.2013-&ast;`

vous pouvez fournir des chemins personnalisés supplémentaires à analyser dans la ligne de commande

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

vous pouvez enregistrer la sortie en une seule passe

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
