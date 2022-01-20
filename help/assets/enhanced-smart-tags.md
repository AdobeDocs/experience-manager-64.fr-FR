---
title: Balises intelligentes améliorées
description: Balises intelligentes améliorées
uuid: 4452ca05-1f20-4f80-884a-a739ae7b8b0e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
discoiquuid: c1b52aac-1eaf-4cfa-801f-77aeca0d90ea
feature: Smart Tags,Search
role: User
exl-id: 21a9f130-ea91-45bf-adc8-8a73a2a00c77
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 83%

---

# Balises intelligentes améliorées {#enhanced-smart-tags}

## Présentation des balises intelligentes améliorées {#overview-of-enhanced-smart-tags}

Les entreprises qui traitent des ressources numériques utilisent de plus en plus le vocabulaire contrôlé par taxonomie dans les métadonnées des ressources. Il comprend essentiellement une liste des mots-clés que les employés, les partenaires et les clients utilisent fréquemment pour mentionner et rechercher des ressources numériques d’une classe particulière. Le balisage des ressources avec vocabulaire contrôlé par taxonomie permet de s’assurer que les ressources peuvent être facilement identifiées et récupérées par des recherches reposant sur les balises.

Comparé aux vocabulaires des langages naturels, le balisage des ressources numériques basé sur la taxonomie métier aide à les aligner avec les activités d’une entreprise et à assurer que les ressources les mieux adaptées apparaissent dans les recherches.

Par exemple, un constructeur de voitures peut baliser les images de voitures avec les noms de modèles afin d’afficher uniquement les images appropriées lors de recherches d’images de différents modèles pour concevoir une campagne de promotion.

Pour que le service de contenu dynamique applique les balises adéquates, vous devez l’entraîner à reconnaître votre taxonomie. Pour entraîner le service, regroupez tout d’abord un ensemble de ressources et de balises qui décrivent le mieux ces ressources. Appliquez ces balises sur les ressources et exécutez un workflow d’entraînement pour aider le service à apprendre.

Une fois une balise entraînée et prête, le service peut appliquer ces balises sur les ressources par un workflow de balisage.

En arrière-plan, le service de contenu dynamique utilise la structure d’intelligence artificielle d’Adobe Sensei pour entraîner son algorithme de reconnaissance d’image sur votre structure de balises et votre taxonomie métier. Cette intelligence de contenu est ensuite utilisée pour appliquer les balises pertinentes sur un ensemble de ressources différentes.

Le service de contenu dynamique est un service cloud hébergé sur [!DNL Adobe I/O]. Pour l’utiliser dans Adobe Experience Manager, l’administrateur système doit intégrer votre [!DNL Experience Manager] instance avec [!DNL Adobe I/O].

En résumé, voici les principales étapes pour utiliser le service de contenu dynamique :

* Intégration 
* Passage en revue des ressources et des balises (définition de la taxonomie)
* Entraînement du service de contenu dynamique
* Balisage automatique

![organigramme](assets/flowchart.gif)

## Prérequis {#prerequisites}

Avant de pouvoir utiliser le service de contenu dynamique, assurez-vous de respecter les conditions suivantes pour créer une intégration sur [!DNL Adobe I/O]:

* L’organisation doit disposer d’un compte Adobe ID pourvu de droits d’administrateur.
* Le service de contenu dynamique est activé pour votre organisation.

## Intégration  {#onboarding}

Le service de contenu dynamique est disponible à l’achat sous la forme d’un module complémentaire pour [!DNL Experience Manager] . Une fois l’achat effectué, un courrier électronique est envoyé à l’administrateur de votre entreprise avec un lien vers [!DNL Adobe I/O].

L’administrateur peut suivre le lien pour intégrer le service de contenu dynamique à [!DNL Experience Manager] . Pour intégrer le service à [!DNL Experience Manager] Ressources, voir [Configuration des balises intelligentes](config-smart-tagging.md).

Le processus d’intégration est terminé lorsque l’administrateur configure le service et ajoute des utilisateurs dans [!DNL Experience Manager] .

## Passage en revue des ressources et des balises {#reviewing-assets-and-tags}

Après intégration, commencez par identifier un ensemble de balises qui décrit le mieux ces images dans le contexte de votre entreprise.

Ensuite, passez en revue les images de façon à identifier une série d’images qui représentent le mieux votre produit pour un besoin particulier de votre entreprise. Vérifiez que les ressources figurant dans la série sélectionnée sont conformes aux [instructions d’entraînement du service de contenu dynamique](smart-tags-training-guidelines.md).

Ajoutez les ressources à un dossier, puis appliquez les balises à chaque ressource sur la page de propriétés. Exécutez ensuite le workflow d’entraînement sur ce dossier. La série de ressources sélectionnée permet au service de contenu dynamique d’entraîner efficacement plus de ressources avec vos définitions de taxonomie.

>[!NOTE]
>
>1. L’entraînement est un processus irrévocable. Adobe recommande de bien passer en revue les balises dans la série de ressources sélectionnée bien avant d’entraîner le service de contenu dynamique sur les balises.
>1. Veuillez lire [Instructions de formation du service de contenu dynamique](smart-tags-training-guidelines.md) avant de commencer l’entraînement pour n’importe quelle balise.
>1. Lorsque vous entraînez le service de contenu dynamique pour la première fois, Adobe recommande de réaliser l’entraînement sur au moins deux balises distinctes.

>


## Entraînement du service de contenu dynamique {#training-the-smart-content-service}

Pour que le service de contenu dynamique reconnaisse votre taxonomie métier, exécutez-la sur une série de ressources qui incluent déjà des balises correspondant à votre entreprise. Après l’entraînement, le service peut appliquer la même taxonomie sur un ensemble de ressources similaire.

Vous pouvez entraîner plusieurs fois le service afin d’améliorer sa capacité à appliquer les balises appropriées. Après chaque cycle d’entraînement, exécutez un workflow de balisage et vérifiez que vos ressources sont correctement balisées.

Vous pouvez entraîner le service de contenu dynamique périodiquement ou en fonction des besoins.

>[!NOTE]
>
>Le workflow d’entraînement s’exécute sur les dossiers uniquement.

### Entraînement périodique {#periodic-training}

Vous pouvez activer le service de contenu dynamique afin qu’il s’entraîne périodiquement sur les ressources et les balises associées au sein d’un dossier. Ouvrez la page des propriétés de votre dossier de ressources, puis sélectionnez **[!UICONTROL Activation des balises intelligentes]** sous le **[!UICONTROL Détails]** et enregistrez les modifications.

![enable_smart_tags](assets/enable_smart_tags.png)

Une fois cette option sélectionnée pour un dossier, [!DNL Experience Manager] exécute automatiquement un workflow d’entraînement pour entraîner le service de contenu dynamique sur les ressources du dossier et leurs balises. Par défaut, le workflow d’entraînement s’exécute sur une base hebdomadaire à 0 h 30 le samedi.

### Entraînement à la demande {#on-demand-training}

Vous pouvez entraîner le service de contenu dynamique chaque fois que cela est nécessaire à partir de la console Processus.

1. Appuyez/cliquez sur le bouton [!DNL Experience Manager] et accédez à **[!UICONTROL Outils > Processus > Modèles]**.
1. Dans la page **[!UICONTROL Modèles de processus]**, sélectionnez le processus **[!UICONTROL Entraînement des balises dynamiques]**, puis appuyez/cliquez sur **[!UICONTROL Démarrer le processus]** dans la barre d’outils.
1. Dans la boîte de dialogue **[!UICONTROL Exécuter le processus]**, localisez le dossier de charge utile qui comprend les ressources balisées pour entraîner le service.
1. Indiquez le titre du workflow et ajoutez un commentaire. Ensuite, appuyez/cliquez sur **[!UICONTROL Exécuter]**. Les ressources et les balises sont soumises à l’entraînement.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Une fois que les ressources d’un dossier sont traitées pour formation, seules les ressources modifiées sont traitées au cours des cycles de formation suivants.

### Affichage des rapports d’entraînement {#viewing-training-reports}

Pour vérifier que le service de contenu dynamique est entraîné sur vos balises dans la série de ressources d’entraînement, examinez le rapport de workflow d’entraînement dans la console Rapports.

1. Appuyez/cliquez sur le bouton [!DNL Experience Manager] et accédez à **[!UICONTROL Outils > Ressources > Rapports]**.
1. Dans la page **[!UICONTROL Rapports de ressources]**, appuyez/cliquez sur **[!UICONTROL Créer]**.
1. Sélectionnez le rapport **[!UICONTROL Entraînement des balises intelligentes]**, puis appuyez/cliquez sur **[!UICONTROL Suivant]** dans la barre d’outils.
1. Indiquez un titre et une description pour le rapport. Sous **[!UICONTROL Planifier le rapport]**, laissez l’option **[!UICONTROL Maintenant]** sélectionnée. Si vous souhaitez planifier le rapport pour une date ultérieure, sélectionnez **[!UICONTROL Plus tard]** et spécifiez une date et une heure. Ensuite, appuyez/cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Dans la page **[!UICONTROL Rapports de ressources]**, sélectionnez le rapport que vous avez généré. Pour afficher le rapport, appuyez/cliquez sur l’icône **[!UICONTROL Afficher]** dans la barre d’outils.
1. Passez en revue les détails du rapport.

   Le rapport affiche le statut d’identification des balises que vous avez entraînées. La couleur verte de la colonne **[!UICONTROL État de l’entraînement]** indique que le service de contenu dynamique est entraîné pour la balise. La couleur jaune indique que le service n’est pas complètement entraîné pour une balise particulière. Dans ce cas, ajoutez d’autres images avec la balise particulière et exécutez le workflow d’entraînement pour l’entraînement complet du service sur la balise.

   Si vous ne voyez pas vos balises dans ce rapport, lancez à nouveau le workflow d’entraînement pour ces balises.

1. Pour télécharger le rapport, sélectionnez-le dans la liste, puis appuyez/cliquez sur l’icône **[!UICONTROL Télécharger]** de la barre d’outils. Le rapport est téléchargé sous la forme d’un fichier Excel.

## Balisage automatique des ressources {#tagging-assets-automatically}

Après avoir entraîné le service de contenu dynamique, vous pouvez déclencher le workflow de balisage pour appliquer automatiquement les balises appropriées sur une autre série de ressources similaire.

Vous pouvez exécuter le workflow de balisage périodiquement ou au besoin.

>[!NOTE]
>
>Le workflow de balisage s’exécute sur les ressources et les dossiers.

### Balisage périodique {#periodic-tagging}

Vous pouvez activer le service de contenu dynamique de façon à ce qu’il balise périodiquement les ressources au sein d’un dossier. Ouvrez la page des propriétés de votre dossier de ressources, puis sélectionnez **[!UICONTROL Activation des balises intelligentes]** sous le **[!UICONTROL Détails]** et enregistrez les modifications.

Une fois cette option sélectionnée pour un dossier, le service de contenu dynamique balise automatiquement les ressources qu’il contient. Par défaut, le workflow de balisage s’exécute tous les jours à 00h00.

### Balisage à la demande {#on-demand-tagging}

Vous pouvez déclencher le workflow de balisage à partir des emplacements suivants pour baliser instantanément vos ressources :

* Console de processus
* Chronologie

>[!NOTE]
>
>Si vous exécutez le workflow de balisage à partir de la chronologie, vous pouvez appliquer des balises sur un maximum de 15 ressources à la fois.

#### Balisage des actifs de la console de processus {#tagging-assets-from-the-workflow-console}

1. Appuyez/cliquez sur le bouton [!DNL Experience Manager] et accédez à **[!UICONTROL Outils > Processus > Modèles]**.
1. Dans la page **[!UICONTROL Modèles de processus]**, sélectionnez le processus **[!UICONTROL Ressources de balises dynamiques DAM]**, puis appuyez/cliquez sur **[!UICONTROL Démarrer le processus]** dans la barre d’outils.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Dans la boîte de dialogue **[!UICONTROL Exécuter le processus]**, accédez au dossier de charge utile contenant les ressources sur lesquelles vous souhaitez appliquer vos balises automatiquement.
1. Indiquez un titre pour le workflow et un commentaire facultatif. Ensuite, appuyez/cliquez sur **[!UICONTROL Exécuter]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Accédez au dossier de ressources et passez en revue les balises pour vérifier que le service de contenu dynamique a correctement balisé vos ressources. Pour plus d’informations, voir [Gestion des balises intelligentes](managing-smart-tags.md).

#### Balisage des ressources à partir de la chronologie {#tagging-assets-from-the-timeline}

1. Depuis l’interface utilisateur Assets, sélectionnez le dossier contenant les ressources ou des ressources spécifiques auxquelles vous souhaitez appliquer des balises intelligentes.
1. Appuyez/cliquez sur l’icône Navigation globale et ouvrez la chronologie.
1. Appuyez/cliquez sur la flèche vers le bas, puis sur **[!UICONTROL Démarrer le processus]**.

   ![start_workflow](assets/start_workflow.png)

1. Sélectionnez le workflow **[!UICONTROL Balisage intelligent des ressources (gestion des actifs numériques (DAM))]** et spécifiez un titre pour le workflow.
1. Appuyez/cliquez sur **[!UICONTROL Démarrer]**. Le workflow applique vos balises aux ressources. Accédez au dossier de ressources et passez en revue les balises pour vérifier que le service de contenu dynamique a correctement balisé vos ressources. Pour plus d’informations, voir [Gestion des balises intelligentes](managing-smart-tags.md).

>[!NOTE]
>
>Dans les cycles de balisage suivants, seules les ressources modifiées sont balisées à nouveau avec les balises qui viennent d’être entraînées.
>
>Toutefois, même les ressources non modifiées sont balisées si l’intervalle entre le dernier cycle de balisage et l’actuel pour le workflow de balisage dépasse 24 heures.
>
>Pour les workflows de balisage périodiques, les ressources non modifiées sont balisées lorsque l’intervalle dépasse 6 mois.
