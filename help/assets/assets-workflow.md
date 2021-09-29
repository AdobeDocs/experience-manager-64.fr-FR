---
title: Traiter les ressources pour exécuter les processus d’entreprise, réaliser des audits, assurer la conformité et maintenir une intégrité de base
description: Traitement des ressources pour convertir des formats, créer des rendus, gérer des ressources, valider des ressources et exécuter des workflows.
contentOwner: AG
feature: Workflow,Renditions
role: User,Admin
exl-id: 4fb3d12c-feac-45b9-8d09-3b6995591b3d
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 27%

---

# Traitement des ressources numériques {#process-assets}

[!DNL Adobe Experience Manager Assets] vous permet de travailler sur vos ressources numériques de différentes manières pour permettre un traitement des ressources robuste. Vous pouvez utiliser les méthodes de traitement disponibles ou étendre les méthodes pour assurer la fin des processus d’entreprise de bout en bout à l’aide d’ , d’audits et de conformité, de découverte et de distribution de vos ressources numériques, ainsi que d’une intégrité de base. Vous pouvez effectuer toutes ces opérations tout en respectant l’échelle et la personnalisation requises.

## Présentation des workflows {#understand-workflows}

Pour le traitement des ressources, [!DNL Experience Manager] utilise des workflows. Les workflows permettent d’automatiser la logique commerciale ou les activités. Les étapes granulaires permettant d’accomplir des tâches spécifiques sont fournies par défaut et les développeurs peuvent créer leurs propres étapes personnalisées. Ces étapes peuvent être combinées dans un ordre logique pour créer des workflows. Par exemple, un workflow peut automatiquement appliquer un filigrane sur les images téléchargées en fonction d’un critère spécifique, comme les métadonnées incorporées dans l’image, le dossier dans lequel elle est téléchargée, la résolution de l’image, etc. Un autre exemple est un workflow configuré pour filigrane des images de cette manière et répondant simultanément à plusieurs besoins de gestion des ressources, tels que l’ajout de métadonnées, la création de rendus, l’ajout de balises intelligentes pour la découverte de ressources, la publication dans une banque de données, la définition d’autorisations d’accès utilisateur, etc.

## Workflows par défaut disponibles dans Experience Manager {#default-workflows}

Par défaut, toutes les ressources chargées sont traitées à l’aide du workflow [!UICONTROL Ressources de mise à jour de gestion des actifs numériques] . Le workflow s’exécute pour chaque ressource chargée et exécute les tâches de gestion des ressources de base telles que la génération de rendu, l’écriture différée des métadonnées, l’extraction de page, l’extraction de médias et le transcodage.

Pour afficher les différents modèles de workflow disponibles par défaut, voir [!UICONTROL Outils > Processus > Modèles] dans [!DNL Experience Manager].

![Certains workflows par défaut](assets/aem-default-workflows.png)

*Figure : Certains des workflows par défaut sont disponibles dans  [!DNL Experience Manager].*

## Application de workflows à des ressources {#applying-workflows-to-assets}

L’application de workflow aux ressources numériques est identique à l’application de workflow aux pages d’un site web. Pour obtenir un guide complet sur la création et l’utilisation des workflows, voir [Démarrage des workflows](/help/sites-authoring/workflows-participating.md).

Utilisez les workflows dans les ressources numériques pour activer les ressources ou créer des filigranes. La plupart des workflow destinés aux ressources sont automatiquement activés, comme le workflow permettant de créer automatiquement un rendu après la modification d’une image.

>[!NOTE]
>
>Si un workflow disponible dans l’IU classique n’est pas disponible dans l’IU tactile, par exemple [!UICONTROL Demande d’activation] et [!UICONTROL Demande de désactivation], voir [Créer des modèles de workflow](/help/sites-developing/workflows-models.md#make-workflow-models-available-in-touchui).

## Application d’un workflow à une ressource [!DNL Experience Manager] {#apply-a-workflow-to-an-aem-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->

Pour appliquer un workflow à une ressource, procédez comme suit :

1. Accédez à l’emplacement de la ressource pour laquelle vous souhaitez démarrer un workflow, puis cliquez sur la ressource pour ouvrir la page Ressource.

1. Accédez à l’emplacement de la ressource pour laquelle vous souhaitez démarrer un workflow, puis cliquez sur la ressource pour ouvrir la page Ressource. Sélectionnez **[!UICONTROL Chronologie]** dans le menu pour afficher la chronologie.

   ![chronologie-2](assets/timeline-2.png)

1. Cliquez sur **[!UICONTROL Actions]** en bas pour ouvrir la liste des actions disponibles pour la ressource.

1. Cliquez sur **[!UICONTROL Démarrer le processus]** dans la liste.

1. Dans la boîte de dialogue **[!UICONTROL Démarrer le processus]**, sélectionnez un modèle de processus dans la liste.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. (Facultatif) Spécifiez le titre du workflow, qui peut permettre de référencer l’instance du workflow.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Cliquez sur **[!UICONTROL Démarrer]**, puis sur **[!UICONTROL Continuer]** dans la boîte de dialogue pour confirmer. Chaque étape du workflow s’affiche en tant qu’événement dans la chronologie.

   ![chlimage_1-52](assets/chlimage_1-52.png)

## Application d’un workflow à plusieurs ressources {#applying-a-workflow-to-multiple-assets}

1. Dans la console Ressources, accédez à l’emplacement des ressources pour lesquelles vous souhaitez démarrer un workflow, puis sélectionnez les ressources. Sélectionnez **[!UICONTROL Chronologie]** dans le menu pour afficher la chronologie.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Cliquez sur **[!UICONTROL Actions]** dans la partie inférieure.

1. Cliquez sur **[!UICONTROL Démarrer le processus]**. Dans la section **[!UICONTROL Démarrer le processus]**, sélectionnez un modèle de workflow dans la liste.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Facultatif) Spécifiez le titre du workflow, qui peut permettre de référencer l’instance du workflow.

1. Cliquez sur **[!UICONTROL Démarrer]**, puis sur **[!UICONTROL Confirmer]** dans la boîte de dialogue. Le workflow s’exécute sur toutes les ressources sélectionnées.

## Application d’un workflow à plusieurs dossiers {#applying-a-workflow-to-multiple-folders}

La procédure à suivre pour appliquer un workflow à plusieurs dossiers est similaire à celle observée permettant d’appliquer un workflow à plusieurs ressources. Sélectionnez les dossiers dans la console Ressources et effectuez les étapes 2 à 7 de la procédure [appliquer un workflow à plusieurs ressources](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Application d’un workflow à une collection {#applying-a-workflow-to-a-collection}

Pour plus d’informations sur l’application d’un workflow à une collection, voir [Application d’un workflow à une collection](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Démarrage automatique d’un workflow pour traiter les ressources de manière conditionnelle {#auto-execute-workflow-on-some-assets}

Les administrateurs peuvent configurer le workflow pour exécuter et traiter automatiquement les ressources en fonction de conditions prédéfinies. Cette fonctionnalité est utile pour les utilisateurs et les spécialistes du marketing du secteur, par exemple pour créer un workflow personnalisé sur des dossiers spécifiques. Disons que toutes les ressources de la séance photo d’une agence peuvent être filigrane ou que toutes les ressources téléchargées par un programme de travail indépendant peuvent être traitées pour créer des rendus spécifiques.

Pour un modèle de workflow, les utilisateurs peuvent créer un lanceur de workflow qui l’exécute. Un lanceur de workflow surveille les modifications du référentiel de contenu et exécute le workflow lorsque les conditions prédéfinies sont remplies. Les administrateurs peuvent donner accès aux marketeurs pour créer les workflows et configurer le lanceur. Les utilisateurs peuvent modifier le workflow [!UICONTROL Ressource de mise à jour de gestion des actifs numériques] par défaut pour ajouter les étapes supplémentaires requises pour traiter des ressources spécifiques. Le workflow s’exécute sur toutes les ressources nouvellement chargées. Utilisez l’une des méthodes suivantes pour limiter l’exécution des étapes supplémentaires sur des ressources spécifiques :

* Effectuez une copie du workflow [!UICONTROL Ressource de mise à jour de gestion des actifs numériques] et modifiez-le pour l’exécuter sur une hiérarchie de dossiers spécifique. Cette approche est utile pour quelques dossiers.
* Les étapes de traitement supplémentaires peuvent être ajoutées à l’aide d’un [Division OU](/help/sites-developing/workflows-step-ref.md#or-split), applicable de manière conditionnelle au plus grand nombre de dossiers nécessaire.

## Bonnes pratiques et restrictions {#best-practices-limitations-tips}

* Pour la conception des workflows, prenez en compte vos besoins pour tous les types de rendus. Si vous ne prévoyez pas la nécessité d’un rendu futur, supprimez son étape de création dans le workflow. Il est impossible par la suite de supprimer les rendus en masse. Les rendus superflus peuvent occuper beaucoup d’espace de stockage suite à une utilisation prolongée d’[!DNL Experience Manager]. Pour les ressources individuelles, vous pouvez supprimer manuellement les rendus à l’aide de l’interface utilisateur. Si plusieurs ressources sont concernées, vous pouvez, au choix, personnaliser [!DNL Experience Manager] pour supprimer des rendus spécifiques, ou supprimer les ressources et les charger à nouveau.
* Par défaut, le workflow [!UICONTROL Ressource de mise à jour de gestion des actifs numériques] comprend quelques étapes pour créer des miniatures et des rendus web. Si des rendus par défaut sont supprimés du workflow, l’interface utilisateur de [!DNL Assets] n’est pas correctement rendue.

>[!MORELIKETHIS]
>
>* [Application et participation aux workflows](/help/sites-authoring/workflows.md)
>* [Création de modèles de workflow et extension de la fonctionnalité de workflow](/help/sites-developing/workflows.md)
>* [Méthodes d’exécution de workflows](/help/sites-administering/workflows-starting.md)
>* [Bonnes pratiques relatives aux workflows](/help/sites-developing/workflows-best-practices.md)

