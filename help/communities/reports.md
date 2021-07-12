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
role: Admin
exl-id: 766711ea-f3d3-49ab-8346-4e4477c261bd
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 8%

---

# Console Rapports  {#reports-console}

## Présentation {#overview}

Pour AEM Communities, plusieurs rapports sont accessibles de plusieurs manières à partir de l’environnement de création.

En général, les différents rapports sont les suivants :

* [Rapport d’affectations](#assignments-report)  : pour une communauté d’ [activation](overview.md#enablement-community), fournit un aperçu de l’avancement des apprenants sur leurs affectations, y compris un score associé lors de la mise en oeuvre de la norme SCORM.
* [Rapport Vues](#views-report)  : fournit un tableau des vues du contenu par les membres de la communauté et les visiteurs du site pour n’importe quel site de la communauté.
* [Rapport Publications](#posts-report)  : fournit un graphique des différents types de publications par les membres de la communauté sur n’importe quel site de la communauté.

Lorsque [Adobe Analytics est activé](sites-console.md#analytics), les rapports comprennent le nombre de vues, lectures, commentaires et évaluations pour chaque ressource d’activation au fil du temps.

Les rapports tabulaires peuvent être exportés au format .csv pour un traitement ultérieur.

## Consoles de création de rapports {#reporting-consoles}

### Rapports pour les sites de la communauté {#reports-for-community-sites}

* À partir de la navigation globale : **[!UICONTROL Navigation > Communautés > Rapports]**
* Choisir parmi
   * **[!UICONTROL Rapport des affectations]**
      * Générer un rapport pour le site, l’utilisateur ou le groupe de la communauté sélectionné et l’affectation
   * **[!UICONTROL Rapport des publications]**
      * Générer un rapport pour le site de la communauté, le type de contenu et la période sélectionnés
   * **[!UICONTROL Rapport des vues]**
      * Générer un rapport pour le site de la communauté, le type de contenu et la période sélectionnés
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Rapports pour les ressources d’activation et les chemins d’apprentissage {#reports-for-enablement-resources-and-learning-paths}

* À partir de la navigation globale : **[!UICONTROL Navigation > Communautés > Ressources]**
* Sélectionner un site de communauté d’activation existant
   * Sélectionnez **[!UICONTROL Icône Report]** pour générer des rapports qui couvrent toutes les ressources d’activation.
   * Sélection d’un chemin d’apprentissage d’activation
   * Sélectionnez **[!UICONTROL Icône Report]** pour générer des rapports pour
      * Ressources d’activation incluses
      * Les apprenants affectés au parcours d’apprentissage
* Ces rapports fournissent les éléments suivants :
   * Données de tableau, téléchargeables au format CSV
      * Identification de l’apprenant
      * Leur statut
      * Attribué ou accessible par le biais du catalogue
      * Nombre de commentaires effectués
      * Note de l&#39;étoile donnée

Pour plus d’informations, voir [Section Rapports](resources.md#report) de la console Ressources.

## Rapport des affectations {#assignments-report}

La console Affectations permet de filtrer les rapports par site de communauté d’activation, utilisateurs ou groupes, et par affectation.

Le rapport fournit des informations sur leurs progrès ainsi que sur les commentaires ou évaluations fournis.

![chlimage_1-157](assets/chlimage_1-157.png)

Sélectionnez les critères du rapport :

* ****
SiteSélectionner un site de la communauté d’activation
* **[!UICONTROL Utilisateur ou groupe]**
   * Sélectionnez Utilisateur pour générer un rapport destiné à un apprenant.
   * Sélectionnez Groupe pour générer un rapport pour un groupe d’apprenants.
Le service Tunnel accède aux membres et aux groupes de membres à partir de l’environnement de publication.
* ****
AttributionChoisissez parmi les ressources d’activation affectées aux apprenants sélectionnés.

Sélectionnez **[!UICONTROL Générer]** pour créer le rapport :

![chlimage_1-158](assets/chlimage_1-158.png)

## Rapport des vues {#views-report}

La console Vues permet de générer des rapports sur les pages vues par fonction(s) de la communauté pendant une période donnée.

![chlimage_1-159](assets/chlimage_1-159.png)

Sélectionnez les critères du rapport :

* ****
SiteSelect a community site
* **[!UICONTROL Type]**
de contenuPeut sélectionner tout le contenu ou l’une des fonctionnalités présentes sur le site.
* Période
Sélectionnez l’une des options suivantes :
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

* ****
SiteSelect a community site
* **[!UICONTROL Type]**
de contenuPeut sélectionner tout le contenu ou l’une des fonctionnalités présentes sur le site.
* Période
Sélectionnez l’une des options suivantes :
   * 7 derniers jours
   * 30 derniers jours
   * 90 derniers jours
   * L&#39;année dernière

Sélectionnez **[!UICONTROL Générer]** pour créer le rapport :

![chlimage_1-162](assets/chlimage_1-162.png)

## Résolution des problèmes {#troubleshooting}

### Aucun site de communauté répertorié {#no-community-sites-listed}

Si aucun site de communauté n’est répertorié, vérifiez qu’Adobe Analytics a été activé pour un site. Si vous choisissez des rapports sur les affectations, assurez-vous que la fonction des affectations se trouve dans la structure du site de la communauté.
