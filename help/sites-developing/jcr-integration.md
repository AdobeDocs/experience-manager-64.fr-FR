---
title: Intégration JCR
seo-title: JCR Integration
description: Conseils pour savoir quand il faut intégrer au niveau JCR
seo-description: Tips for when you must integrate at the JCR level
uuid: 11518baf-521e-471d-ad4f-2baa76075cfa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: e6647a11-a36e-4808-bb61-29b2895c6b1d
exl-id: 3e9727a5-32f8-40ad-aa06-619f50d109b2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 87%

---

# Intégration JCR{#jcr-integration}

## Privilégier l’API Sling Resource à l’API JCR {#prefer-the-sling-resource-api-to-jcr-api}

L’API Sling fonctionne à un niveau plus avancé et plus abstrait que l’API JCR. Ainsi, votre code est plus réutilisable et indépendant du stockage sous-jacent. Cela facilite l’ajout de données virtuelles externes via le mécanisme ResourceProvider si nécessaire.

## Éviter les requêtes autant que possible {#avoid-queries-wherever-possible}

Pour récupérer des données, il est toujours plus simple de naviguer dans le référentiel plutôt que d’exécuter une requête. Dans certains cas, les requêtes sont nécessaires, par exemple, une requête d’utilisateur final ou s’il faut trouver du contenu structuré à travers le référentiel entier, mais pour toutes les autres situations, il est préférable de naviguer jusqu’aux nœuds demandés. Les requêtes doivent toujours être évitées dans la logique de rendu, comme les composants de navigation, une &quot;liste d’éléments récents&quot;, le nombre d’éléments, etc. Dans ces cas, il est préférable de parcourir la hiérarchie ou de pré-mettre en cache le résultat afin qu’il puisse être utilisé directement lors du rendu.

## Limiter la portée de l’observation JCR {#restrict-the-scope-of-jcr-observation}

Lors de l’écoute des événements dans le référentiel, il est important de réduire la portée autant que possible. Par exemple, il est préférable d’écouter un événement à l’adresse `/etc/mycompany` que d&#39;écouter à `/etc`. N’écoutez jamais les événements à la racine du référentiel. En outre, assurez-vous que les méthodes de rappel s’exécutent aussi rapidement que possible quand il n’y a pas de requêtes.

## Éliminer l’utilisation de l’accès administrateur JCR {#eliminate-use-of-jcr-admin-access}

Depuis la version AEM 6, la connexion à l’administration a été abandonnée, de même que l’obtention d’une session administrative à partir de ResourceResolverFactory. Au contraire, les comptes de service doivent être créés pour les opérations de back-office qui nécessiteraient ce type d’accès, et ResourceResolverFactory peut être utilisé pour obtenir un ResourceResolver pour ce compte.
