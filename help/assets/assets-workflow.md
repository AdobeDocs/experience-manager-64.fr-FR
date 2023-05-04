---
title: Traiter les ressources pour exécuter les processus d’entreprise, réaliser des audits, assurer la conformité et maintenir une intégrité de base
description: Traitement des ressources pour convertir des formats, créer des rendus, gérer des ressources, valider des ressources et exécuter des workflows.
contentOwner: AG
feature: Workflow,Renditions
role: User,Admin
exl-id: 4fb3d12c-feac-45b9-8d09-3b6995591b3d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 72%

---

# Traitement des ressources numériques {#process-assets}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

[!DNL Adobe Experience Manager Assets] vous permet de travailler sur vos ressources numériques de différentes manières pour permettre un traitement des ressources robuste. Vous pouvez utiliser les méthodes de traitement disponibles ou étendre les méthodes pour assurer la fin des processus d’entreprise de bout en bout à l’aide d’ , d’audits et de conformité, de découverte et de distribution de vos ressources numériques, ainsi que d’une intégrité de base. Vous pouvez effectuer toutes ces opérations tout en respectant l’échelle et la personnalisation requises.

## Présentation des workflows {#understand-workflows}

Pour le traitement des ressources, [!DNL Experience Manager] utilise des workflows. Les workflows permettent d’automatiser la logique commerciale ou les activités. Chaque étape permettant d’accomplir des tâches spécifiques sont fournies par défaut et les développeurs peuvent créer leurs propres étapes personnalisées. Ces étapes peuvent être combinées dans un ordre logique pour créer des workflows. Par exemple, un workflow peut automatiquement appliquer un filigrane sur les images téléchargées en fonction d’un critère spécifique, comme les métadonnées incorporées dans l’image, le dossier dans lequel elle est téléchargée, la résolution de l’image, etc. Un autre exemple est un workflow configuré pour filigrane des images de cette manière et répondant simultanément à plusieurs besoins de gestion des ressources, tels que l’ajout de métadonnées, la création de rendus, l’ajout de balises intelligentes pour la découverte de ressources, la publication dans une banque de données, la définition d’autorisations d’accès utilisateur, etc.

## Workflows par défaut disponibles dans Experience Manager {#default-workflows}

Par défaut, toutes les ressources chargées sont traitées à l’aide du workflow [!UICONTROL Ressource de mise à jour de la gestion des ressources numériques]. Le workflow s’exécute pour chaque ressource chargée et exécute les tâches de gestion des ressources de base telles que la génération de rendu, l’écriture différée des métadonnées, l’extraction de page, l’extraction de médias et le transcodage.

Pour consulter les différents modèles de workflow disponibles par défaut, consultez [!UICONTROL Outils > Processus > Modèles] dans [!DNL Experience Manager].

![Quelques workflows par défaut](assets/aem-default-workflows.png)

*Figure : Certains des workflows par défaut disponibles dans [!DNL Experience Manager].*

## Application de workflows à des ressources {#applying-workflows-to-assets}

L’application de workflow aux ressources numériques est identique à l’application de workflow aux pages d’un site Web. Pour obtenir des informations complètes sur la création et l’utilisation de processus, reportez-vous à la section [démarrer des workflows](/help/sites-authoring/workflows-participating.md).

Utilisez les workflows dans les ressources numériques pour activer les ressources ou créer des filigranes. La plupart des workflows des ressources sont automatiquement activés. Par exemple, le workflow qui crée automatiquement un rendu après la modification d’une image est automatiquement activé.

>[!NOTE]
>
>Si un workflow disponible dans l’IU classique n’est pas disponible dans l’IU tactile, par exemple [!UICONTROL Demande d’activation] et [!UICONTROL Demande de désactivation], voir [créer des modèles de workflow ;](/help/sites-developing/workflows-models.md#make-workflow-models-available-in-touchui).

## Appliquez un workflow à un [!DNL Experience Manager] ressource {#apply-a-workflow-to-an-aem-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->

Pour appliquer un workflow à une ressource, procédez comme suit :

1. Accédez à l’emplacement de la ressource pour laquelle vous souhaitez commencer un workflow et cliquez sur la ressource pour afficher la page de ressource.

1. Accédez à l’emplacement de la ressource pour laquelle vous souhaitez commencer un workflow et cliquez sur la ressource pour afficher la page de ressource. Sélectionnez **[!UICONTROL Chronologie]** dans le menu pour afficher la chronologie.

   ![chronologie-2](assets/timeline-2.png)

1. Cliquez sur **[!UICONTROL Actions]** dans la partie inférieure pour afficher la liste des actions disponibles pour la ressource.

1. Cliquez sur **[!UICONTROL Démarrer le workflow]** dans la liste.

1. Dans le **[!UICONTROL Démarrer le processus]** , sélectionnez un modèle de workflow dans la liste.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. (Facultatif) Spécifiez le titre du workflow, qui peut permettre de référencer l’instance du workflow.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Cliquez sur **[!UICONTROL Début]**, puis cliquez sur **[!UICONTROL Continuer]** dans la boîte de dialogue pour confirmer. Chaque étape du workflow s’affiche en tant qu’événement dans la chronologie.

   ![chlimage_1-52](assets/chlimage_1-52.png)

## Application d’un workflow à plusieurs ressources {#applying-a-workflow-to-multiple-assets}

1. Dans la console Ressources, accédez à l’emplacement des ressources pour lesquelles vous souhaitez démarrer un workflow, puis sélectionnez les ressources. Sélectionnez **[!UICONTROL Chronologie]** dans le menu pour afficher la chronologie.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Cliquez sur **[!UICONTROL Actions]** située dans la partie inférieure.

1. Cliquez sur **[!UICONTROL Démarrer le processus]**. Dans la section **[!UICONTROL Démarrer le processus]**, sélectionnez un modèle de workflow dans la liste.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Facultatif) Spécifiez le titre du workflow, qui peut permettre de référencer l’instance du workflow.

1. Cliquez sur **[!UICONTROL Démarrer]**, puis sur **[!UICONTROL Confirmer]** dans la boîte de dialogue. Le workflow s’exécute sur toutes les ressources sélectionnées.

## Application d’un workflow à plusieurs dossiers {#applying-a-workflow-to-multiple-folders}

La procédure à suivre pour appliquer un workflow à plusieurs dossiers est similaire à celle observée permettant d’appliquer un workflow à plusieurs ressources. Sélectionnez les dossiers dans la console Ressources et effectuez les étapes 2 à 7 de la procédure. [application d’un workflow à plusieurs ressources](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Application d’un workflow à une collection {#applying-a-workflow-to-a-collection}

Pour plus d’informations sur l’application d’un workflow à une collection, voir [appliquer un workflow à une collection ;](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Démarrage automatique d’un workflow pour traiter les ressources de manière conditionnelle {#auto-execute-workflow-on-some-assets}

Les administrateurs peuvent configurer un workflow pour exécuter et traiter automatiquement les ressources en fonction de conditions prédéfinies. Cette fonctionnalité est utile pour les utilisateurs et les spécialistes du marketing du secteur, par exemple pour créer un workflow personnalisé sur des dossiers spécifiques. Disons que toutes les ressources de la séance photo d’une agence peuvent recevoir un filigrane ou que toutes les ressources téléchargées par un programme de travail indépendant peuvent être traitées pour créer des rendus spécifiques.

Pour chaque modèle de workflow, les utilisateurs peuvent créer un lanceur de workflow qui l’exécute. Un lanceur de workflow surveille les modifications du référentiel de contenu et exécute le workflow lorsque les conditions prédéfinies sont remplies. Les administrateurs peuvent donner accès aux marketeurs pour leur permettre de créer les workflows et de configurer le lanceur. Les utilisateurs peuvent modifier le workflow [!UICONTROL Ressource de mise à jour de la gestion des ressources numériques] par défaut pour ajouter les étapes supplémentaires requises pour traiter des ressources spécifiques. Le workflow s’exécute sur toutes les ressources nouvellement chargées. Utilisez l’une des méthodes suivantes pour limiter l’exécution des étapes supplémentaires sur des ressources spécifiques :

* Effectuez une copie du workflow [!UICONTROL Ressource de mise à jour de la gestion des ressources numériques] et modifiez-la pour l’exécuter sur une hiérarchie de dossiers spécifique. Cette approche est utile pour quelques dossiers.
* Les étapes de traitement supplémentaires peuvent être ajoutées à l’aide d’une [Division OU](/help/sites-developing/workflows-step-ref.md#or-split) qui s’applique de manière conditionnelle au plus grand nombre de dossiers requis.

## Bonnes pratiques et restrictions {#best-practices-limitations-tips}

* Pour la conception des workflows, prenez en compte vos besoins pour tous les types de rendus. Si vous ne prévoyez pas la nécessité d’un rendu futur, supprimez son étape de création dans le workflow. Il est impossible par la suite de supprimer les rendus en masse. Les rendus superflus peuvent occuper beaucoup d’espace de stockage suite à une utilisation prolongée d’[!DNL Experience Manager]. Pour les ressources individuelles, vous pouvez supprimer manuellement les rendus à l’aide de l’interface utilisateur. Si plusieurs ressources sont concernées, vous pouvez, au choix, personnaliser [!DNL Experience Manager] pour supprimer des rendus spécifiques, ou supprimer les ressources et les charger à nouveau.
* Par défaut, le workflow [!UICONTROL Ressource de mise à jour de la gestion des ressources numériques] comprend quelques étapes pour créer des miniatures et des rendus Web. Si des rendus par défaut sont supprimés du workflow, l’interface utilisateur d’[!DNL Assets] ne s’affiche pas correctement.

>[!MORELIKETHIS]
>
>* [Application et participation aux workflows](/help/sites-authoring/workflows.md)
>* [Création de modèles de workflow et extension de la fonctionnalité de workflow](/help/sites-developing/workflows.md)
>* [Méthodes d’exécution de workflows](/help/sites-administering/workflows-starting.md)
>* [Bonnes pratiques relatives aux workflows](/help/sites-developing/workflows-best-practices.md)

