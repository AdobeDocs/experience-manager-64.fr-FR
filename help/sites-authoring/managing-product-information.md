---
title: Projet créatif et intégration à PIM
seo-title: Creative Project and PIM Integration
description: Le projet de création simplifie l’ensemble du processus de séance photo, y compris la génération d’une demande de séance photo, le téléchargement d’une séance photo, la collaboration sur une séance photo et le regroupement des ressources approuvées.
seo-description: Creative Project streamlines the entire photo shoot workflow that including generating a photo shoot request, uploading a photo shoot, collaborating on a photo shoot, and packaging approved assets
uuid: 09f27d36-e725-45cb-88d1-27383aedceed
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: projects
content-type: reference
discoiquuid: 0e5d0a45-c663-4d91-b793-03d39119d103
exl-id: b477d6ab-126a-489a-a13f-2b6f439ab85b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3016'
ht-degree: 32%

---

# Projet créatif et intégration à PIM{#creative-project-and-pim-integration}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Si vous êtes spécialiste du marketing ou professionnel de la création, vous pouvez utiliser les outils Projet de création d’Adobe Experience Manager (AEM) pour gérer la photographie de produits liés à l’e-commerce et les processus de création associés au sein de votre organisation.

En particulier, vous pouvez utiliser Creative Project pour rationaliser les tâches suivantes dans votre workflow de séance photo :

* Génération d’une demande de séance photo
* Téléchargement d’une séance photo
* Collaboration sur une séance photo
* Modules de ressources approuvées

>[!NOTE]
>
>Voir [Rôles utilisateur du projet pour plus d’informations](/help/sites-authoring/projects.md#user-roles-in-a-project) lors de l’affectation de rôles utilisateur et de workflows à certains types d’utilisateurs.

## Exploration des workflows Séance photo du produit  {#exploring-product-photo-shoot-workflows}

La fonction Projet de création fournit divers modèles de projet pour satisfaire aux différentes exigences des projets. Le modèle **Projet de séance photo du produit** est disponible prêt à l’emploi. Ce modèle comprend des processus de séance photo qui vous permettent de lancer et de gérer des demandes de séance photo de produit. Il comprend également une série de tâches qui vous permettent d’obtenir des images numériques des produits par l’intermédiaire de processus de révision et d’approbation appropriés.

Le modèle comprend les workflows suivants :

* **Workflow Séance photo du produit (intégration commerciale)**: Ce workflow exploite l’intégration commerciale au système de gestion de l’information sur les produits (PIM) pour générer automatiquement une liste de plans pour les produits sélectionnés (hiérarchie). Vous pouvez afficher les données de produit parmi les métadonnées des ressources une fois que le worfklow est terminé.
* **Workflow Séance photo du produit**: Ce workflow permet de fournir une liste de plans plutôt que de dépendre de l&#39;intégration commerciale. Il mappe les images chargées à un fichier CSV dans le dossier des ressources du projet.

>[!NOTE]
>
>Le fichier CSV chargé dans la tâche Transférer la liste de plans du workflow Séance photo du produit doit porter le nom shotlist.csv.

## Création d’un projet Séance photo du produit {#create-a-product-photo-shoot-project}

1. Dans le **Projets** console, appuyez/cliquez **Créer** puis choisissez **Créer un projet** dans la liste.

   ![chlimage_1-132](assets/chlimage_1-132.png)

1. Dans le **Créer un projet** , sélectionnez le modèle de projet de séance photo, puis appuyez/cliquez sur **Suivant**.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Saisissez les détails du projet, notamment le titre, la description et l’échéance. Ajoutez des utilisateurs et attribuez-leur différents rôles. Vous pouvez également ajouter une miniature pour le projet.

   ![chlimage_1-134](assets/chlimage_1-134.png)

1. Cliquez/appuyez sur **Créer**. Un message de confirmation indique que le projet est créé.
1. Appuyez/cliquez sur **Terminé** pour revenir au **Projets** console. Vous pouvez également appuyer/cliquer sur **Ouvrir** pour afficher les ressources du projet de séance photo.

## Commencer à travailler dans un projet de séance photo de produit {#starting-work-in-a-product-photo-shoot-project}

Pour lancer une demande de séance photo, appuyez ou cliquez sur un projet, puis appuyez/cliquez sur **Ajouter un travail** dans la page des détails du projet pour démarrer un workflow.

![chlimage_1-135](assets/chlimage_1-135.png)

Un projet Séance photo du produit comprend les processus prêts à l’emploi suivants :

* Workflow Séance photo du produit (Intégration de commerce)
* Workflow de séance photo du produit

Utilisez le workflow Séance photo de produit (intégration de Commerce) pour mapper les ressources d’images aux produits dans AEM. Ce workflow exploite l’intégration Commerce pour lier les images approuvées aux données de produit existantes à l’emplacement */etc/commerce*.

Le workflow de séance photo de produit (intégration de Commerce) comprend les tâches suivantes :

* Créer une liste de plans
* Transférer la séance photo
* Retoucher la séance photo
* Réviser et approuver
* Déplacer vers la tâche de production

Si les informations produit ne sont pas disponibles dans AEM, utilisez le workflow Séance photo de produit pour associer les ressources d’images aux produits en fonction des détails que vous chargez dans un fichier CSV. Le fichier CSV doit contenir des informations de base sur le produit, telles que l’ID, la catégorie et la description du produit. Le workflow récupère les ressources approuvées pour les produits.

Ce workflow comprend les tâches suivantes :

* Transférer la liste de plans
* Transférer la séance photo
* Retoucher la séance photo
* Réviser et approuver
* Déplacer vers la tâche de production

Vous pouvez personnaliser ce workflow à l’aide de l’option de configuration des workflows.

Les deux workflows incluent des étapes pour lier les produits à leurs ressources approuvées. Chaque workflow comprend les étapes suivantes :

* Configuration de workflow : Décrit les options de personnalisation du workflow
* Démarrage d’un workflow de projet : Explique comment démarrer une séance photo du produit
* Détails des tâches de workflow : Fournit des détails sur les tâches disponibles dans le workflow.

## Suivi de la progression du projet {#tracking-project-progress}

Vous pouvez suivre la progression d’un projet en surveillant les tâches principales/terminées au sein d’un projet.

Utilisez les éléments suivants pour surveiller la progression d’un projet :

* **Carte des tâches**

* **Liste des tâches**

La carte Tâche illustre la progression globale du projet. Il apparaît sur la page Détails du projet uniquement si le projet comporte des tâches associées. La carte Tâche affiche l’état d’achèvement actuel du projet en fonction du nombre de tâches terminées. Elle n’inclut pas les tâches ultérieures.

La carte Tâche fournit les détails suivants :

* Pourcentage de tâches principales
* Pourcentage de tâches terminées

![chlimage_1-136](assets/chlimage_1-136.png)

La liste Tâche fournit des informations détaillées sur la tâche de workflow actuellement principale pour le projet. Pour afficher la liste, appuyez/cliquez sur la carte Tâche . La liste Tâche affiche également des métadonnées telles que la date de début, l’échéance, la personne désignée, la priorité et l’état de la tâche.

![chlimage_1-137](assets/chlimage_1-137.png)

## Configuration du workflow {#workflow-configuration}

Cette tâche implique d’affecter des étapes de workflow aux utilisateurs en fonction de leur rôle.

Pour configurer la variable **Séance photo du produit** workflow :

1. Accédez à **Outils** > **Workflows**, puis appuyez sur la mosaïque **Modèles** afin d’ouvrir la page **Modèles de workflow**.
1. Sélectionnez le workflow **Séance photo de produit**, puis appuyez sur l’icône **Modifier** de la barre d’outils pour l’ouvrir en mode d’édition.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. Dans la page du workflow **Séance photo de produit**, ouvrez une tâche de projet. Par exemple, ouvrez la tâche **Charger la liste de plans**.

   ![chlimage_1-139](assets/chlimage_1-139.png)

1. Cliquez sur le bouton **Tâche** pour configurer les éléments suivants :

   * Nom de la tâche
   * Utilisateur par défaut (rôle) qui reçoit la tâche
   * Priorité par défaut de la tâche, affichée dans la liste des tâches de l’utilisateur
   * Description de la tâche à afficher lorsque la personne désignée ouvre la tâche
   * Date d’échéance d’une tâche, calculée en fonction de l’heure à laquelle la tâche a commencé.

1. Cliquez sur **OK** pour enregistrer les paramètres de configuration.

   De même, vous pouvez configurer les tâches suivantes pour la variable **Séance photo du produit** workflow :

   * Transférer la séance photo
   * Retoucher la séance photo du produit
   * Critique de la séance photo
   * Déplacer vers la production

   Effectuez une procédure similaire pour configurer les tâches dans la variable **Workflow Séance photo du produit (Intégration de commerce)**.

Cette section décrit comment intégrer la gestion des informations produit (PIM) à votre projet de création.

## Démarrage d’un worfklow de projet {#starting-a-project-workflow}

1. Accédez à un projet Séance photo du produit, puis appuyez/cliquez sur le **Ajouter un travail** sur l’icône **Workflows** carte.
1. Sélectionnez le workflow **Séance photo de produit (intégration de Commerce)** pour démarrer le workflow Séance photo de produit (intégration de Commerce). Si les informations sur le produit ne sont pas disponibles sous /etc/commerce, sélectionnez la variable **Séance photo du produit** et démarrez le workflow Séance photo du produit .

   ![chlimage_1-140](assets/chlimage_1-140.png)

1. Appuyez/cliquez sur **Suivant** pour lancer le workflow dans le projet.
1. Saisissez les détails du worfklow sur la page suivante.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   Cliquez sur **Envoyer** pour démarrer le processus de séance photo. La page de détails du projet de séance photo s’affiche.

   ![chlimage_1-142](assets/chlimage_1-142.png)

### Détails des tâches de workflow {#workflow-tasks-details}

Le workflow de séance photo comprend plusieurs tâches. Chaque tâche est affectée à un groupe d’utilisateurs en fonction de la configuration définie pour la tâche.

#### Tâche Créer une liste de plans {#create-shot-list-task}

La tâche **Créer une liste de plans** permet au propriétaire du projet de sélectionner les produits pour lesquels des images sont requises. Selon l’option sélectionnée par l’utilisateur, un fichier CSV est généré avec les informations de base sur les produits.

1. Dans le dossier du projet, appuyez/cliquez sur les ellipses du dossier [Carte des tâches](#tracking-project-progress) pour afficher l’élément de tâche dans le workflow.

   ![chlimage_1-143](assets/chlimage_1-143.png)

1. Sélectionnez la tâche **Créer une liste de plans**, puis appuyez ou cliquez sur l’icône **Ouvrir** dans la barre d’outils.

   ![chlimage_1-144](assets/chlimage_1-144.png)

1. Passez en revue les détails de la tâche, puis appuyez ou cliquez sur le bouton **Créer une liste de plans**.

   ![chlimage_1-145](assets/chlimage_1-145.png)

1. Sélectionnez les produits pour lesquels des données de produit existent sans images associées.

   ![chlimage_1-146](assets/chlimage_1-146.png)

1. Appuyez/cliquez sur le bouton **Ajouter à la liste de plans** pour créer un fichier CSV contenant la liste de tous ces produits. Un message confirme la création de la liste de plans pour les produits sélectionnés. Cliquez sur **Fermer** pour terminer le workflow.
1. Après avoir créé une liste de plans, la variable **Afficher la liste de plans** s’affiche. Pour ajouter d’autres produits à la liste de plans, appuyez/cliquez sur **Ajouter à la liste de plans**. Dans ce cas, les données sont ajoutées à la liste de plans créée.

   ![chlimage_1-147](assets/chlimage_1-147.png)

1. Appuyez/cliquez sur **Afficher la liste de plans** pour afficher la nouvelle liste de plans.

   ![chlimage_1-148](assets/chlimage_1-148.png)

   Pour modifier les données existantes ou ajouter de nouvelles données, appuyez/cliquez sur **Modifier** dans la barre d’outils. Seuls les champs **Produit** et **Description** sont modifiables.

   ![chlimage_1-149](assets/chlimage_1-149.png)

   Après avoir mis à jour le fichier, appuyez/cliquez sur **Enregistrer** sur la barre d’outils pour enregistrer le fichier.

1. Après avoir ajouté les produits, appuyez/cliquez sur l’icône **Terminer** sur la page de détails de la tâche **Créer une liste de plans ** pour marquer la tâche comme terminée. Vous pouvez ajouter un commentaire facultatif.

   La fin de la tâche introduit les modifications suivantes dans le projet :

   * Les ressources correspondant à la hiérarchie des produits sont créées dans un dossier portant le même nom que le titre du workflow.
   * Les métadonnées des ressources peuvent être modifiées à l’aide de la console Ressources, avant même que le photographe ne fournisse les images.
   * Un dossier Séance photo est créé pour stocker les images fournies par le photographe. Le dossier Séance photo contient des sous-dossiers pour chaque entrée de produit dans la liste de plans.

   Pour le workflow Séance photo du produit (sans intégration de commerce), la première tâche est de télécharger la liste de plans . Appuyez/cliquez sur **Transférer la liste de plans** pour charger un **shotlist.csv** fichier . Le fichier CSV doit contenir l’ID de produit. Les autres champs sont facultatifs. Vous pouvez les utiliser pour mapper des ressources à des produits.

### Charger une tâche de liste de plans {#upload-shot-list-task}

Cette tâche fait partie du workflow Séance photo du produit . Vous effectuez cette tâche si les informations sur les produits ne sont pas disponibles dans AEM. Dans ce cas, vous téléchargez une liste de produits dans un fichier CSV pour lequel des ressources d’image sont requises. En fonction des détails du fichier CSV, vous mappez les ressources d’images aux produits.

Utilisez la variable **Afficher la liste de plans** lien sous la carte du projet dans la procédure précédente pour télécharger un exemple de fichier CSV. Consultez le fichier d’exemple pour connaître le contenu habituel d’un fichier CSV.

La liste de produits ou le fichier CSV peut contenir des champs, tels que **Catégorie, Produit, Id, Description**, et **Chemin**. Le champ **ID** est obligatoire et contient l’ID du produit. Les autres champs sont facultatifs.

Un produit peut appartenir à une catégorie particulière. La catégorie du produit peut être indiquée dans le fichier CSV sous la colonne **Catégorie**. Le champ **Produit** contient le nom du produit. Dans le champ **Description**, saisissez la description du produit ou les instructions pour le photographe.

>[!NOTE]
>
>Le nom des images à télécharger doit commencer par &quot;**&lt;productid>_&quot;** où l’ID de produit est référencé à partir de la variable **Id** dans le champ *shotlist.csv* fichier . Par exemple, pour un produit de la liste de plans avec **Id 397122**, vous pouvez charger des fichiers avec des noms. **397122_Highcontraste.jpg**, **397122_lowlight.png**, etc.

1. Dans le dossier du projet, appuyez/cliquez sur les ellipses du dossier [Carte des tâches](#tracking-project-progress) pour afficher la liste des tâches du workflow.
1. Sélectionnez la **Transférer la liste de plans** , puis appuyez/cliquez sur l’icône **Ouvrir** dans la barre d’outils.

   ![chlimage_1-150](assets/chlimage_1-150.png)

1. Vérifiez les détails de la tâche, puis appuyez/cliquez sur l’icône **Transférer la liste de plans** bouton .

   ![chlimage_1-151](assets/chlimage_1-151.png)

1. Appuyez/cliquez sur le bouton **Transférer la liste de plans** pour télécharger le fichier CSV avec le nom shotlist.csv. Le workflow reconnaît ce fichier comme une source à utiliser pour extraire les données de produit pour la tâche suivante.
1. Téléchargez un fichier CSV contenant les informations sur les produits au format approprié. Le lien **Afficher les ressources chargées** apparaît sous la carte une fois le fichier CSV chargé.

   ![chlimage_1-152](assets/chlimage_1-152.png)

   Cliquez sur l’icône **Terminé** pour terminer la tâche.

1. Appuyez/cliquez sur l’icône **Terminé** pour terminer la tâche.

### Tâche Charger la séance photo {#upload-photo-shoot-task}

Si vous êtes un éditeur, vous pouvez charger des plans pour les produits répertoriés dans le fichier **shotlist.csv** créé ou chargé lors de la tâche précédente.

Le nom des images à télécharger doit commencer par **&quot;&lt;productid>_&quot;** où l’ID de produit est référencé à partir de la variable **Id** dans le champ **shotlist.csv** fichier . Par exemple, pour un produit avec **ID 397122** dans la liste de plans, vous pouvez charger des fichiers avec des noms. **397122_Highcontraste.jpg**, **397122_lowlight.png**, etc.

Vous pouvez charger les images directement ou charger un fichier ZIP contenant les images. En fonction de leurs noms, les images sont placées dans les dossiers de produit respectifs au sein des **Séance photo** dossier.

1. Sous le dossier du projet, appuyez/cliquez sur les points de suspension dans le [Task Card](#tracking-project-progress) pour afficher l’élément de tâche dans le workflow.
1. Sélectionnez la **Télécharger la séance photo** , puis appuyez/cliquez sur l’icône **Ouvrir** dans la barre d’outils.

   ![chlimage_1-153](assets/chlimage_1-153.png)

1. Appuyez/cliquez sur **Télécharger la séance photo **et chargez les images de la séance photo.
1. Appuyez/cliquez sur le bouton **Terminer** dans la barre d’outils pour terminer la tâche.

### Tâche Retoucher la séance photo {#retouch-photo-shoot-task}

Si vous disposez de droits de modification, effectuez la tâche Retoucher la séance photo pour modifier les images téléchargées dans le dossier Séance photo .

1. Sous le dossier du projet, appuyez/cliquez sur les points de suspension dans le [Task Card](#tracking-project-progress) pour afficher l’élément de tâche dans le workflow.
1. Sélectionnez la tâche **Retoucher la séance photo**, puis appuyez/cliquez sur l’icône **Ouvrir** dans la barre d’outils.

   ![chlimage_1-154](assets/chlimage_1-154.png)

1. Appuyez/cliquez sur le bouton **Affichage des ressources téléchargées** dans le **Retoucher la séance photo** pour parcourir les images téléchargées.

   ![chlimage_1-155](assets/chlimage_1-155.png)

   Si nécessaire, modifiez les images à l’aide d’une application Adobe Creative Cloud.

   ![chlimage_1-156](assets/chlimage_1-156.png)

1. Appuyez/cliquez sur le bouton **Terminer** dans la barre d’outils pour terminer la tâche.

### Tâche de révision et d’approbation {#review-and-approve-task}

Dans cette tâche, vous passez en revue les images de la séance photo téléchargées par un photographe et marquez les images comme approuvées pour utilisation.

1. Sous le dossier du projet, appuyez/cliquez sur les points de suspension dans le [Task Card](#tracking-project-progress) pour afficher l’élément de tâche dans le workflow.
1. Sélectionnez la **Réviser et approuver** , puis appuyez/cliquez sur l’icône **Ouvrir** dans la barre d’outils.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Dans le **Réviser et approuver** , affectez la tâche de révision au rôle, par exemple les réviseurs, puis appuyez/cliquez sur **Réviser** pour commencer à examiner les images de produit chargées.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. Sélectionnez une image de produit, puis appuyez/cliquez sur l’icône Approuver de la barre d’outils pour la marquer comme approuvée.

   ![chlimage_1-159](assets/chlimage_1-159.png)

   Une fois que vous avez approuvé une image, une bannière « Approuvée » s’affiche par-dessus.

   >[!NOTE]
   Vous pouvez laisser certains produits sans image. Vous pourrez ensuite revoir la tâche et la marquer comme terminée une fois terminée.

1. Appuyez/cliquez sur **Terminer**. Les images approuvées sont liées aux ressources vides qui ont été créées.

Vous pouvez accéder aux ressources du projet à l’aide de l’interface utilisateur Ressources et vérifier les images approuvées.

Appuyez/cliquez sur le niveau suivant pour afficher les produits selon votre hiérarchie de données de produit.

La fonction Projet de création associe les ressources approuvées au produit référencé. Les métadonnées de la ressource sont mises à jour avec la référence du produit et des informations de base dans l’onglet **Données du produit** sous Propriétés de la ressource ; elles apparaissent dans la section AEM métadonnées de la ressource.

>[!NOTE]
Dans le workflow Séance photo du produit (sans intégration de Commerce), les images approuvées n’ont aucune association avec des produits.

### Déplacer vers la tâche de production {#move-to-production-task}

Cette tâche déplace les ressources approuvées dans le dossier Prêt pour la production afin de les rendre disponibles pour utilisation.

1. Sous le dossier du projet, appuyez/cliquez sur les points de suspension dans le [Task Card](#tracking-project-progress) pour afficher l’élément de tâche dans le workflow.
1. Sélectionnez la **Déplacer vers la production** , puis appuyez/cliquez sur l’icône **Ouvrir** dans la barre d’outils.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. Pour afficher les ressources approuvées pour la séance photo avant de les déplacer dans le dossier Prêt pour l’exploitation, cliquez sur le lien **Afficher les ressources approuvées** situé au-dessous de la miniature du projet sur la page de la tâche **Déplacer en exploitation**.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. Saisissez le chemin du dossier Prêt pour l’exploitation dans le champ **Déplacer vers**.

   ![chlimage_1-162](assets/chlimage_1-162.png)

   Appuyez/cliquez sur **Déplacer vers la production**. Fermez le message de confirmation. Les ressources sont déplacées vers le chemin d’accès mentionné et une visionneuse à 360° est créée automatiquement pour les ressources approuvées pour chaque produit en fonction de la hiérarchie des dossiers.

1. Appuyez ou cliquez sur l’icône **Terminé** dans la barre d’outils. Le workflow se termine lorsque la dernière étape est marquée comme étant terminée.

## Affichage des métadonnées des ressources DAM {#viewing-dam-asset-metadata}

Après votre approbation, les ressources sont liées aux produits correspondants. La [page des propriétés](/help/assets/managing-assets-touch-ui.md#editing-properties) des ressources approuvées comprend maintenant un nouvel onglet **Données du produit** (les informations sur les produits liés) Cet onglet affiche les détails du produit, le numéro de SKU ainsi que d’autres détails relatifs au produit lié à la ressource. Appuyez/cliquez sur le bouton **Modifier** pour mettre à jour une propriété de ressource. Les informations relatives aux produits restent en lecture seule.

Appuyez/cliquez sur le lien qui s’affiche pour accéder à la page des détails du produit correspondante dans la console du produit à laquelle la ressource est associée.

## Personnalisation des worfklow de séance photo du projet {#customizing-the-project-photo-shoot-workflows}

Vous pouvez personnaliser les processus de séance photo du projet en fonction des besoins. Il s’agit d’une tâche facultative, basée sur les rôles, que vous effectuez pour définir la valeur d’une variable dans le projet. Par la suite, vous pourrez utiliser la valeur configurée pour prendre une décision.

1. Cliquez/appuyez sur le logo AEM, puis accédez à **Outils** > **Workflow** > **Modèles** pour ouvrir la page Modèles de processus .
1. Sélectionnez la **Séance photo du produit (intégration Commerce)** ou le workflow **Séance photo du produit** workflow et clic/clic **Modifier** de la barre d’outils pour ouvrir le workflow en mode d’édition.
1. Ouvrez le **Projets** tâches dans le sidekick, puis faites glisser l’objet **Créer une tâche de projet basée sur un rôle** au workflow.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Ouvrez l’étape **Tâche basée sur le rôle**.
1. Dans le **Tâche** , indiquez un nom pour la tâche qui s’affichera dans le **Tâche** Liste. Vous pouvez également affecter la tâche à un rôle, définir la priorité par défaut, fournir une description et spécifier l’échéance de la tâche.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Dans le **Routage** , spécifiez les actions de la tâche. Pour ajouter plusieurs actions, appuyez/cliquez sur le lien **Ajouter un élément**.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Après avoir ajouté les options, cliquez sur **OK** pour ajouter les modifications à l’étape.

   >[!NOTE]
   Appuyer/cliquer **OK** n’enregistre pas les modifications dans le workflow. Pour enregistrer les modifications dans le processus, appuyez/cliquez sur **Enregistrer**.

1. Ouvrez le **Workflow** tâches à partir du sidekick et ajoutez une **Atteindre** tâche.
1. Ouvrez le **Atteindre** et appuyez/cliquez sur l’icône **Processus** .
1. Spécifiez le code suivant dans la variable **Script** box :

```
   function check() {

   if (workflowData.getMetaDataMap().get("lastTaskAction","") == "Reject All") {

   return true

   }

   // set copywriter user in metadata

   var previousId = workflowData.getMetaDataMap().get("lastTaskCompletedBy", "");

   workflowData.getMetaDataMap().put("copywriter", previousId);

   return false;

   }
```

>[!NOTE]
Pour plus d’informations sur les scripts des étapes de processus, voir [Définition d’une règle pour une division OU](/help/sites-developing/workflows-models.md).

![chlimage_1-166](assets/chlimage_1-166.png)

1. Appuyez/cliquez sur **OK**.

1. Appuyez/cliquez sur **Enregistrer** pour enregistrer le workflow.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Une nouvelle tâche d’acceptation du propriétaire du projet apparaît maintenant après la [Tâche Déplacer vers la production](#move-to-production-task) est terminée et est affectée au propriétaire.

   L’utilisateur avec le rôle de propriétaire peut terminer la tâche et sélectionner une action (parmi la liste des actions ajoutées dans les configurations d’étape de workflow) à partir de la liste dans la fenêtre contextuelle de commentaires.

   ![chlimage_1-168](assets/chlimage_1-168.png)

   Sélectionnez l’option appropriée et cliquez sur **Terminer** pour exécuter la variable **Atteindre l’étape** dans le workflow.

>[!NOTE]
Lorsque vous démarrez un serveur, le servlet de liste des tâches du projet met en cache les mappages entre les types de tâches et les URL définis sous `/libs/cq/core/content/projects/tasktypes`. Vous pouvez ensuite exécuter le recouvrement habituel et ajouter des types de tâches personnalisés en les plaçant sous `/apps/cq/core/content/projects/tasktypes`.
