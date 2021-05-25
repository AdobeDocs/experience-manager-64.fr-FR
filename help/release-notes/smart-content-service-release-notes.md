---
title: Notes de mise à jour de Smart Content Service
seo-title: Notes de mise à jour de Smart Content Service
description: Présentation du service de contenu dynamique et des problèmes connus relatifs à ce service.
seo-description: Présentation du service de contenu dynamique et des problèmes connus relatifs à ce service.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
exl-id: 6e7ac9d2-7181-48bb-82c4-61a90e594ff5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 17%

---

# Notes de mise à jour de Smart Content Service {#smart-content-service-release-notes}

Présentation du service de contenu dynamique et des problèmes connus relatifs à ce service.

Les entreprises exigent que leurs ressources numériques soient balisées en fonction de la taxonomie que les employés, les partenaires et les clients utilisent pour faire référence aux ressources numériques et les rechercher. Par rapport aux balises génériques, les ressources balisées en fonction de la taxonomie métier sont plus facilement identifiées et récupérées par des recherches basées sur des balises.

Le service de contenu dynamique utilise votre taxonomie métier d’AEM Assets pour baliser automatiquement les ressources numériques, ce qui garantit que les ressources les plus pertinentes apparaissent dans les recherches.

Vous devez former le service de contenu dynamique à un ensemble organisé de ressources et de balises AEM afin de reconnaître votre taxonomie métier. Une fois formé, le service peut appliquer ces balises sur un ensemble similaire de ressources.

Le service de contenu dynamique est optimisé par la plateforme Adobe Sensei, qui vous permet d’entraîner l’algorithme de reconnaissance d’images à votre taxonomie métier. Cette intelligence de contenu est ensuite utilisée pour appliquer les balises pertinentes sur les ressources similaires.

## Améliorations clés {#key-improvements}

Le service de contenu dynamique comprend les améliorations clés suivantes :

* Optimisations des algorithmes pour améliorer davantage la précision des modèles et rappeler les valeurs
* Prise en charge de la réinitialisation de l’entraînement des modèles pour toutes les balises au niveau du client
* Prise en charge des espaces de noms de balises intelligentes améliorées pour éviter les conflits
* Nouvelle politique de remplacement des modèles pour éviter toute dégradation due à la reconversion
* Surveillance au niveau du client pour l’utilisation du service
* Correctifs de problèmes liés à la mise en grappe et à la connexion, qui améliorent la robustesse du service.

## Problèmes résolus {#fixed-issues}

Les problèmes suivants ont été corrigés dans cette version :

* Les processus de traitement pour les workflows de balisage et de formation se terminent si la connexion au serveur MySQL est impossible. CQ-4242886

* Le score avec biais de précision n’est pas correctement calculé. CQ-4241797

* Calcul incorrect des relations publiques pour le modèle. CQ-4241381

* Les exemples de ressources manquent dans le workflow de formation lors de leur traitement à partir de la file d’attente CQ-4240901

* Améliorations du rappel de précision. CQ-4239895

* Stratégie de remplacement de modèle. CQ-4239886

* Les images de la chemise pour hommes sont marquées avec l&#39;étiquette de la veste pour femmes. CQ-4239650

* Des exemples de formation sont manqués lors du déploiement intermédiaire. CQ-4239483

* La validation d’une tâche de formation doit avoir lieu sur un ensemble de ressources envoyées pour la formation. CQ-4238834

* La création de modèles échoue pour une recherche de données négative même si un minimum de valeurs positives/négatives est présent pour une balise. CQ-4240741

* Entrées trompeuses pour une recherche de nourriture négative dans les logs des formateurs. CQ-4240738

* Problème avec la formation initiale si les balises soumises pour la formation sont des négatifs aléatoires l’une de l’autre. CQ-4240118

* Logs d’improvisation pour surveiller l’utilisation du service par client. CQ-4239781

## Langues {#languages}

Le service de contenu dynamique est disponible pour les paramètres régionaux suivants :

* Anglais
* Allemand
* Français
* Espagnol
* Italien
* brésilien
* Japonais
* Chinois simplifié
* Coréen

## Liens {#links}

* [Page du produit Adobe Experience Manager sur adobe.com](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [Documentation sur les balises intelligentes améliorée](/help/assets/enhanced-smart-tags.md)

## Assistance technique et accès au produit (sites à accès limité) {#product-access-and-support-restricted-sites}

Ces sites sont réservés aux clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [Accès aux produits](https://login.marketing.adobe.com)
* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/).
* Mises à jour de produit, correctifs et packages pour des fonctionnalités supplémentaires sur [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Assistance clientèle via Admin Console](https://adminconsole.adobe.com/). Pour plus d’informations, voir [Nouvelle expérience du service clientèle Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
