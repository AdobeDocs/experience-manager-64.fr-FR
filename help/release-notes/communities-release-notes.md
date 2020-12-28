---
title: Notes de mise à jour d’AEM Communities
seo-title: AEM Communities
description: Notes de mise à jour spécifiques à Adobe Experience Manager 6.4 Communities.
seo-description: Notes de mise à jour spécifiques à Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 86%

---


# AEM Communities Notes de mise à jour {#aem-communities-release-notes}

Cette section contient des informations sur les améliorations apportées à AEM Communities depuis la version 6.3. Pour plus de détails sur les nouvelles fonctions, voir [Nouveautés d’AEM 6.4 Communities](/help/communities/whats-new-aem-communities.md).

Pour obtenir la version la plus récente, consultez la section [Déploiement de Communities de la documentation.](/help/communities/deploy-communities.md#latest-releases)

## Principales améliorations {#main-improvements}

Sites de communautés :

* Les administrateurs de communauté peuvent désormais :

   * supprimer définitivement des sites de la communauté ;
   * sélectionner un dossier configuration tenant compte du contexte pour les sites de la communauté.

Groupes de communautés :

* Les administrateurs de communauté peuvent désormais :

   * supprimer définitivement des groupes de la communauté ;
   * créer des groupes de communauté en plusieurs langues ;
   * ajouter un catalogue et des affectations d’activation dans les groupes de la communauté.

* Les responsables d’activation peuvent désormais :

   * créer et affecter des ressources et des parcours de formation au sein des groupes d’une communauté.

Bibliothèque de fichiers :

* La bibliothèque de fichiers a été améliorée pour les membres de communauté, avec, par exemple, l’ordre de tri, le balisage, etc.

Notifications:

* Les membres de communauté reçoivent désormais des notifications lors de l’approbation des contributions ayant fait l’objet d’un processus de modération.

Modération :

* Filtre de détection du contenu indésirable automatisé
* Les modérateurs de communautés disposent de filtres de modération supplémentaires (par exemple, questions ayant reçu une réponse/sans réponse)
* Les modérateurs des communautés peuvent mettre en signet et lier la modération à des filtres prédéfinis (par exemple, tous les messages en attente d’approbation)

Compatibilité d’ensemble avec les modifications de base apportées à AEM 6.4.

Remarque : toutes ces fonctionnalités sont également disponibles pour AEM 6.3. Consultez les notes de mise à jour de AEM Communities pour [6.3](https://helpx.adobe.com/fr/experience-manager/6-3/release-notes.html).

## Problèmes connus {#known-issues}

* **Modération :** impossible de supprimer une publication parente en une seule opération de suppression à partir de l’interface utilisateur de modération en masse (CQ-4236797).
* **Console**  - Le lien Nom d’utilisateur ou Mot de passe oublié est redirigé vers la page de connexion au lieu du formulaire de récupération du mot de passe correspondant (CQ-4237682).

## Fonctionnalités mises en avant {#select-features}

L’évaluation des experts (*reposant sur Sensei*) est utilisée pour permettre la ludification, qui est une façon efficace d’encourager et de récompenser un comportement bénéfique au sein de la communauté. Elle peut également être utilisée dans le but d’identifier des experts à des fins de recommandation ou de marketing.

## Démonstrations {#demonstrations}

Toutes ces fonctionnalités peuvent faire l’objet d’une démonstration à l’aide d’[AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponible publiquement sur GitHub.com lors de l’utilisation du scénario de démonstration d’AEM Communities et aussi dans la nouvelle implémentation de référence We.Retail.
