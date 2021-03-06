---
title: Architecture de contenu
seo-title: Content Architecture
description: 'Conseils pour la conception de votre contenu (conseil : tout est contenu)'
seo-description: Tips for architecting your content in Adobe Experience Manager (AEM). (hint - everything is content)
uuid: fef2bf0f-70ec-4621-8479-a62b7e1fbc07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: ca46b74c-6114-458b-98c0-2a93abffcdc3
exl-id: 9fff10fb-4b65-459a-a7a7-6ee9c0c26bf5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 86%

---

# Architecture de contenu{#content-architecture}

## Suivez le modèle de David {#follow-david-s-model}

Le modèle de David a été élaboré par David Nuescheler il y a quelques années. Cependant, les principes sont toujours valables aujourd’hui. Les principaux principes du modèle de David sont les suivants :

* Les données viennent en premier, la structure plus tard. Normalement…
* Prenez le contrôle de la hiérarchie de contenu, ne la laissez pas vous diriger.
* Les espaces de travail sont destinés à `clone()`, `merge()`, et `update()`.
* Méfiez-vous des SNS (Same Name Siblings).
* Les références sont considérées comme dangereuses.
* Les fichiers sont des fichiers, et rien d’autre.
* Les identifiants sont mauvais.

Le modèle de David est disponible sur le wiki Jackrabbit à l’adresse [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Tout est contenu {#everything-is-content}

Vous devez tout stocker dans le référentiel plutôt que dans des sources de données tierces, telles que des bases de données. Cela s’applique aussi bien au contenu généré qu’aux données binaires comme les images, le code, les configurations, etc. Il nous est ainsi possible d’utiliser un seul ensemble d’API pour gérer tout le contenu, ainsi que pour gérer la promotion de ce contenu par le biais de la réplication. Nous disposons également d’une source unique de sauvegarde, de journalisation, etc.

### Utilisez le principe de conception « Le modèle de contenu d’abord » {#use-the-content-model-first-design-principle}

Lors de la mise au point d’une fonctionnalité, commencez toujours par concevoir la structure du contenu JCR, puis tâchez de lire et d’écrire votre contenu à l’aide des servlets Sling par défaut. Vous pouvez ainsi vous assurer que votre implémentation fonctionne bien avec des mécanismes de contrôle d’accès standard. Cela vous évite également de générer des servlets de type CRUD inutiles.

### Soyez RESTful {#be-restful}

Les servlets doivent être définis en fonction des types de ressource plutôt que des chemins d’accès. Ainsi, il est possible d’utiliser les contrôles d’accès JCR, de respecter les principes REST, ainsi que d’utiliser la ressource et le résolveur de ressources qui sont mis à notre disposition dans la requête. Cela nous permet également de modifier les scripts qui effectuent le rendu des URL du côté serveur, sans devoir modifier une quelconque URL du côté client et sans révéler au client les détails d’implémentation côté serveur, d’où une sécurité accrue.

### Évitez de définir de nouveaux types de nœud {#avoid-defining-new-node-types}

Les types de nœud fonctionnent à un niveau inférieur du calque d’infrastructure. Il est, en outre, possible de répondre à la plupart des exigences en utilisant une propriété sling:resourceType affectée à un type de nœud nt:unstructured, oak:Unstructured, sling:Folder ou cq:Page. Les types de nœud correspondent au schéma dans le référentiel. Changer de type de nœud peut s’avérer très coûteux à terme.

### Respectez les conventions d’affectation de noms dans le JCR {#adhere-to-naming-conventions-in-the-jcr}

Le respect des conventions d’affectation de noms ajoute de l’homogénéité à votre codebase en réduisant le taux d’incidence des défauts et en augmentant la vitesse des développeurs qui travaillent sur le système. Les conventions suivantes sont utilisées par Adobe dans le développement d’AEM :

* Noms des nœuds

   * Tout en minuscules
   * Séparation des mots à l’aide de tirets

* Noms des propriétés

   * Casse mixte, en commençant par une minuscule

* Composants (JSP/HTML)

   * Tout en minuscules
   * Séparation des mots à l’aide de tirets
