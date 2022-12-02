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
ht-degree: 93%

---

# Filtre de disposition du contenu {#content-disposition-filter}

Le filtre de disposition du contenu est une fonctionnalité de sécurité permettant de lutter contre les attaques XSS sur des fichiers SVG.

Une fois installé, le filtre bloque l’accès à toutes les ressources. Par exemple, il vous a été impossible d’afficher un PDF en ligne. Cette section explique comment configurer ce filtre en fonction de vos besoins.

## Configuration du filtre de disposition du contenu {#configure-content-disposition-filter}

Vous pouvez visualiser le [filtre de disposition de contenu Apache Sling dans GitHub.](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

Les options du filtre de disposition du contenu offrent les fonctionnalités suivantes :

* **Chemins d’accès de disposition du contenu :** liste des chemins auxquels le filtre sera appliqué, suivi d’une liste de types MIME à exclure sur ces chemins. Ce chemin d’accès doit être absolu et peut contenir un caractère générique (`*`) à la fin pour s’appliquer à chaque chemin d’accès aux ressources avec le préfixe donné. Par exemple : `/content/*:image/jpeg,image/svg+xml` appliquera le filtre à chaque nœud dans `/content` à l’exception des images jpg et svg.

* **Chemins d’accès aux ressources exclues :** une liste de ressources exclues. Chaque chemin doit être absolu et complet. La correspondance des préfixes et les caractères génériques ne sont pas pris en charge.

* **Activer pour tous les chemins d’accès aux ressources :** cet indicateur contrôle l’activation de ce filtre pour tous les chemins, à l’exception des chemins d’accès aux ressources exclues. En définissant cette valeur sur « true », vous pouvez ignorer les chemins de disposition du contenu. Indépendamment de la configuration, seuls les chemins d’accès aux ressources qui contiennent une propriété nommée `jcr:data` ou
   `jcr:content jcr:data`.
