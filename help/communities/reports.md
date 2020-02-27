---
title: 'Console Rapports '
seo-title: 'Console Rapports '
description: Découvrez comment accéder aux rapports
seo-description: Découvrez comment accéder aux rapports
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7

---


# Console Rapports{#reports-console} 

## Présentation {#overview}

Pour les communautés AEM, plusieurs rapports peuvent être accessibles de plusieurs manières à partir de l’environnement d’auteur.

En général, les différents rapports sont :

* [Rapport](#assignments-report) sur les affectations - pour une communauté [d’](overview.md#enablement-community)activation, fournit un aperçu des progrès des apprenants sur leurs affectations, y compris un score associé lors de la mise en oeuvre de la norme SCORM
* [Rapport](#views-report) Vues - fournit un graphique des vues du contenu par les membres de la communauté et les visiteurs du site pour tout site communautaire
* [Rapport](#posts-report) Publications - fournit un graphique des différents types de publications des membres de la communauté sur n’importe quel site de la communauté.

Lorsque [Adobe Analytics est activé](sites-console.md#analytics), les rapports incluent le nombre de vues, de lectures, de commentaires et d’évaluations pour chaque ressource d’activation au fil du temps.

Les rapports tabulaires peuvent être exportés au format .csv pour un traitement ultérieur.

## Console de création de rapports {#reporting-consoles}

### Rapports pour les sites communautaires {#reports-for-community-sites}

* A partir de la navigation globale : **[!UICONTROL Navigation > Communautés > Rapports]**
* Choisir parmi
   * **[!UICONTROL Rapport des affectations]**
      * Générer un rapport pour le site, l’utilisateur ou le groupe de la communauté sélectionné et l’affectation
   * **[!UICONTROL Rapport des publications]**
      * Générer un rapport pour le site communautaire, le type de contenu et la période sélectionnés
   * **[!UICONTROL Rapport des vues]**
      * Générer un rapport pour le site communautaire, le type de contenu et la période sélectionnés
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Rapports sur les ressources d’activation et les chemins d’apprentissage {#reports-for-enablement-resources-and-learning-paths}

* A partir de la navigation globale : **[!UICONTROL Navigation > Communautés > Ressources]**
* Sélectionner un site de communauté d&#39;activation existant
   * Sélectionner l&#39;icône **[!UICONTROL Rapport]** pour générer des rapports qui couvrent toutes les ressources d&#39;activation
   * Sélectionner un chemin d&#39;apprentissage d&#39;activation
   * Sélectionner l’icône **[!UICONTROL Rapport]** pour laquelle générer des rapports
      * Ressources d&#39;activation incluses
      * Les apprenants affectés au chemin d&#39;apprentissage
* Ces rapports fournissent :
   * Données de tableau, téléchargeables au format CSV
      * Identification de l’apprenant
      * Leur statut
      * Affecté ou accessible via le catalogue
      * Nombre de commentaires
      * Note d&#39;étoiles donnée

Pour plus d&#39;informations, reportez-vous à la section [](resources.md#report) Rapports de la console Ressources.

## Rapport des affectations {#assignments-report}

La console Affectations permet de filtrer les rapports par site, utilisateurs ou groupes de la communauté d’activation et par affectation.

Le rapport fournit des informations sur les progrès accomplis ainsi que sur les commentaires ou les évaluations fournis.

![chlimage_1-157](assets/chlimage_1-157.png)

Sélectionnez les critères du rapport :

* **[!UICONTROL Site]** Sélectionnez un site de la communauté d&#39;activation
* **[!UICONTROL Utilisateur ou groupe]**
   * Sélectionnez Utilisateur pour générer un rapport pour un seul stagiaire
   * Sélectionnez Groupe pour générer un rapport pour un groupe d’apprenantsLe service tunnel accède aux membres et aux groupes de membres à partir de l’environnement de publication.
* **[!UICONTROL Affectation]** Faites votre choix parmi les ressources d&#39;activation affectées aux apprenants sélectionnés.

Sélectionnez **[!UICONTROL Générer]** pour créer le rapport :

![chlimage_1-158](assets/chlimage_1-158.png)

## Rapport des vues {#views-report}

La console Affichages permet de générer des rapports sur les pages vues par fonction(s) de la communauté pendant une période donnée.

![chlimage_1-159](assets/chlimage_1-159.png)

Sélectionnez les critères du rapport :

* **[!UICONTROL Site]** Sélectionnez un site communautaire
* **[!UICONTROL Type]** de contenu Peut choisir Tout le contenu ou sélectionner l’une des fonctionnalités présentes sur le site
* PériodeSélectionnez l&#39;une des options suivantes :
   * 7 derniers jours
   * 30 derniers jours
   * 90 derniers jours
   * L&#39;année dernière

Sélectionnez **[!UICONTROL Générer]** pour créer le rapport :

![chlimage_1-160](assets/chlimage_1-160.png)

## Rapport des publications {#posts-report}

La console Publications permet de générer des rapports sur le nombre de publications pour les fonctionnalités de la communauté pendant une période donnée.

![chlimage_1-161](assets/chlimage_1-161.png)

Sélectionnez les critères du rapport :

* **[!UICONTROL Site]** Sélectionnez un site communautaire
* **[!UICONTROL Type]** de contenu Peut choisir Tout le contenu ou sélectionner l’une des fonctionnalités présentes sur le site
* PériodeSélectionnez l&#39;une des options suivantes :
   * 7 derniers jours
   * 30 derniers jours
   * 90 derniers jours
   * L&#39;année dernière

Sélectionnez **[!UICONTROL Générer]** pour créer le rapport :

![chlimage_1-162](assets/chlimage_1-162.png)

## Résolution des incidents {#troubleshooting}

### Aucun site de communauté répertorié {#no-community-sites-listed}

Si aucun site de la communauté n’est répertorié, vérifiez qu’Adobe Analytics a été activé pour un site. Si vous choisissez des rapports sur les affectations, assurez-vous que la fonction des affectations est dans la structure du site de la communauté.
