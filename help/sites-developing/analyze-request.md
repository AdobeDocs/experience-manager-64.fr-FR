---
title: Script d’analyse des requêtes
seo-title: Request Analysis Script
description: Le script d’analyse des requêtes facilite l’analyse des fichiers access.log et génère un rapport lisible pour vos activités de traitement ultérieures.
seo-description: The request analysis script is made to ease the analysis of the access.log files producing a readable report for later processing
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: 8582bbca-c11a-4880-88ba-da22e0301dba
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 39%

---

# Script d’analyse des requêtes{#request-analysis-script}

## Télécharger {#download}

Ce script est conçu pour faciliter l’analyse de la variable `access.log` fichiers produisant un rapport lisible en vue d’un traitement ultérieur.

[Obtenir le fichier](assets/analyse-access.sh)

## Description {#description}

Ce script est conçu pour faciliter l’analyse de la variable `access.log` fichiers produisant un rapport lisible en vue d’un traitement ultérieur.

Il produit le nombre global de requêtes, GET vs POST, la répartition des requêtes au fil du temps, etc.

La sortie est en syntaxe Markdown. Il sera donc plus facile de la convertir en PDF avec des outils tels que pandoc ou de l’afficher dans un navigateur avec des modules externes tels que la visionneuse Markdown.

Il peut analyser un chemin personnalisé fourni dans la ligne de commande.

Prise du commentaire dans le fichier qui vous indique comment l’exécuter :

Analyse de CQ `access.log` extrapoler diverses informations et produire une sortie Markdown sur `stdout`.

## Utilisation {#usage}

`./analyse-access.sh access.log.2013-&ast;`

vous pouvez fournir des chemins personnalisés supplémentaires à analyser dans la ligne de commande

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

vous pouvez enregistrer la sortie en une seule passe

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
