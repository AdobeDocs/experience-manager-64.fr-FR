---
title: Notes de mise à jour de Smart Content Service
seo-title: Notes de mise à jour de Smart Content Service
description: Présentation de Smart Content Service et problèmes connus autour du service.
seo-description: Présentation de Smart Content Service et problèmes connus autour du service.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
translation-type: tm+mt
source-git-commit: 715cff841252d79504d702817f91db92df919bfc

---


# Notes de mise à jour de Smart Content Service {#smart-content-service-release-notes}

Présentation de Smart Content Service et problèmes connus autour du service.

Les entreprises exigent que leurs ressources numériques soient balisées en fonction de la taxonomie utilisée par les employés, les partenaires et les clients pour consulter et rechercher des ressources numériques. Par rapport aux balises génériques, les ressources balisées en fonction de la taxonomie métier sont plus facilement identifiées et récupérées par les recherches basées sur les balises.

Le service de contenu dynamique utilise la taxonomie professionnelle des ressources AEM pour baliser automatiquement les ressources numériques, ce qui garantit que les ressources les plus pertinentes apparaissent dans les recherches.

Vous devez former Smart Content Service à un ensemble de balises et de ressources AEM traité afin de reconnaître la taxonomie de votre entreprise. Une fois formé, le service peut appliquer ces balises à un ensemble de ressources similaire.

Le service de contenu intelligent est piloté par la plate-forme Adobe Sensei, ce qui vous permet de former l’algorithme de reconnaissance d’images à votre taxonomie professionnelle. Cette intelligence de contenu est ensuite utilisée pour appliquer les balises pertinentes sur les ressources similaires.

## Améliorations clés {#key-improvements}

Smart Content Service comprend les améliorations clés suivantes :

* Optimisations des algorithmes pour améliorer davantage la précision du modèle, rappeler les valeurs
* Prise en charge de la réinitialisation de la formation du modèle pour toutes les balises au niveau du client
* Prise en charge des espaces de noms des balises intelligentes améliorées pour éviter les conflits
* Nouvelle politique de remplacement des modèles pour éviter toute dégradation due au recyclage
* Surveillance par client de l’utilisation du service
* Correctifs de problèmes liés à la mise en grappe et à la connexion, qui améliorent la robustesse du service

## Problèmes résolus {#fixed-issues}

Les problèmes suivants ont été corrigés dans cette version :

* Les processus de travail pour le balisage et les processus de formation se terminent si la connexion au serveur MySQL est impossible. CQ-4242886

* Le score de précision biaisé n’est pas correctement calculé. CQ-4241797

* Calcul de PR incorrect pour le modèle. CQ-4241381

* Le processus de formation ignore les exemples de ressources lors du traitement à partir de la file d’attente CQ-4240901

* Amélioration du rappel de précision. CQ-4239895

* Stratégie de remplacement de modèle. CQ-4239886

* Les images de la chemise pour homme sont marquées avec l&#39;étiquette de la veste pour femme. CQ-4239650

* Les exemples de formation ne sont pas pris en compte lors du déploiement sur scène. CQ-4239483

* La validation d&#39;un poste de formation doit avoir lieu sur un ensemble de ressources soumises à la formation. CQ-4238834

* La création de modèle échoue pour la recherche de nourriture négative, même si le nombre minimal de positifs/négatifs est présent pour une balise. CQ-4240741

* Entrées erronées pour recherche de nourriture négative dans les journaux des formateurs. CQ-4240738

* Problème de formation initiale si les balises soumises pour la formation sont des négatifs aléatoires les unes des autres. CQ-4240118

* Journaux improvisés pour surveiller l’utilisation du service par client. CQ-4239781

## Langues {#languages}

Smart Content Service est disponible pour les paramètres régionaux suivants :

* Anglais
* Allemand
* Français
* Espagnol
* Italien
* Portugais
* Japonais
* Chinois simplifié
* Coréen

## Liens {#links}

* [Page du produit Adobe Experience Manager sur adobe.com](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [Documentation des balises actives améliorée](/help/assets/enhanced-smart-tags.md)

## Assistance technique et accès au produit (sites à accès limité) {#product-access-and-support-restricted-sites}

Ces sites sont réservés aux clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [](https://daycare.day.com) [Accès aux produits](https://login.marketing.adobe.com)

* [Assistance clientèle d’Adobe](https://helpx.adobe.com/contact/enterprise-support.ec.html)
