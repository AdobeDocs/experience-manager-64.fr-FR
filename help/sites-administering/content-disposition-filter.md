---
title: Filtre de disposition du contenu
seo-title: Content Disposition Filter
description: Découvrez comment utiliser le filtre de disposition du contenu pour empêcher les attaques XSS.
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: 8cc85728be93d58e3aaee69c96f59ee98d5484a1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 30%

---

# Filtre de disposition du contenu {#content-disposition-filter}

Le filtre de disposition du contenu est une fonctionnalité de sécurité permettant de lutter contre les attaques XSS sur des fichiers SVG.

Une fois installé, le filtre bloque l’accès à toutes les ressources. Par exemple, vous ne pouviez pas afficher un PDF en ligne. Cette section explique comment configurer ce filtre en fonction de vos besoins.

## Configuration du filtre de disposition du contenu {#configure-content-disposition-filter}

Vous pouvez afficher la variable [Filtre de disposition de contenu Apache Sling dans GitHub.](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

Les options Filtre de disposition du contenu offrent les fonctionnalités suivantes :

* **Chemins de disposition du contenu :** une liste des chemins où le filtre sera appliqué, suivie d’une liste des types MIME à exclure sur ce chemin. Ce chemin doit être un chemin absolu et peut contenir un caractère générique (`*`) à la fin, pour faire correspondre chaque chemin de ressource avec le préfixe de chemin donné. Par exemple : `/content/*:image/jpeg,image/svg+xml` applique le filtre à chaque noeud dans `/content` à l’exception des images jpg et svg

* **Chemins de ressources exclus :** une liste de ressources exclues, chaque chemin de ressource doit être donné comme chemin absolu et complet. La correspondance des préfixes et les caractères génériques ne sont pas pris en charge.

* **Activer Pour Tous Les Chemins De Ressources :** cet indicateur contrôle s’il faut activer ce filtre pour tous les chemins, à l’exception des chemins exclus définis par les chemins d’accès aux ressources exclues. En définissant cette valeur sur « true », vous pouvez ignorer les chemins de disposition du contenu. Indépendamment de la configuration, seuls les chemins d’accès aux ressources qui contiennent une propriété nommée `jcr:data` ou
   `jcr:content jcr:data`.
