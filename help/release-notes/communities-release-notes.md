---
title: Notes de mise à jour d’AEM Communities
seo-title: AEM Communities
description: Notes de mise à jour spécifiques à Adobe Experience Manager 6.4 Communities.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
exl-id: 3a341e72-01c5-4c63-8942-6320e5b08440
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 9%

---

# Notes de mise à jour d’AEM Communities {#aem-communities-release-notes}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette section fournit des informations sur les améliorations apportées à AEM Communities depuis la version 6.3. Pour en savoir plus sur les nouvelles fonctionnalités, voir [Nouveautés d’AEM 6.4 Communities](/help/communities/whats-new-aem-communities.md).

Pour obtenir la version la plus récente, consultez la section [Déploiement de communautés](/help/communities/deploy-communities.md#latest-releases) de la documentation.

## Principales améliorations {#main-improvements}

Sites de la communauté:

* Les administrateurs de communauté peuvent désormais :

   * Supprimer définitivement des sites de la communauté
   * Sélectionnez un dossier de configuration contextuelle pour les sites de la communauté.

Groupes communautaires:

* Les administrateurs de communauté peuvent désormais :

   * Suppression définitive des groupes de communautés
   * Création de groupes de communautés dans plusieurs langues
   * Ajout d’un catalogue d’activation et d’affectations dans les groupes de la communauté

* Les responsables d’activation peuvent désormais

   * Créer et affecter des ressources et des parcours d’apprentissage dans les groupes communautaires

Bibliothèque de fichiers:

* Les membres de la communauté ont désormais plusieurs améliorations apportées à la bibliothèque de fichiers, par exemple les commandes de tri, le balisage, etc.

Notifications:

* Les membres de la communauté reçoivent désormais des notifications lors de l’approbation des contributions qui ont fait l’objet d’un processus de modération.

Modération:

* Filtre de détection automatisée des messages indésirables
* Les modérateurs de communauté disposent de filtres de modération supplémentaires (par exemple, questions sans réponse/réponses).
* Les modérateurs de la communauté peuvent mettre en signet et lier la modération à des filtres prédéfinis (par exemple, toutes les publications en attente d’approbation).

Compatibilité globale avec les changements fondamentaux dans AEM 6.4.

Remarque : toutes ces fonctionnalités sont également disponibles pour AEM 6.3. Veuillez consulter les notes de mise à jour d’AEM Communities pour [6.3](https://helpx.adobe.com/fr/experience-manager/6-3/release-notes.html).

## Problèmes connus {#known-issues}

* **Modération** - Impossible de supprimer la publication parente en tant qu’opération de suppression unique dans l’interface utilisateur de modération en bloc (CQ-4236797)
* **Console** - Le lien Nom d’utilisateur ou Mot de passe oublié redirige vers la page de connexion au lieu du formulaire de récupération de mot de passe correspondant (CQ-4237682).

## Sélectionner des fonctionnalités {#select-features}

Note d’expert (*Optimisé par Sensei*) - est utilisé pour activer la gamification, qui est un moyen efficace d’encourager et de récompenser un comportement communautaire précieux. Il peut également être utilisé pour identifier des experts à des fins de recommandation ou de marketing.

## Manifestations {#demonstrations}

Toutes ces fonctionnalités peuvent être illustrées à l’aide de la fonction [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponible publiquement sur GitHub.com lors de l’utilisation du scénario de démonstration AEM Communities et également dans la nouvelle implémentation de référence We.Retail.
