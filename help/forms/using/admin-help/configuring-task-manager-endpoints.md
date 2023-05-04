---
title: Configurer des points d’entrée TaskManager
seo-title: Configuring Task Manager endpoints
description: Découvrez comment configurer les points de fin Task Manager.
seo-description: Learn how to configure Task Manager endpoints.
uuid: 07604b10-0bd7-4bce-9624-7ebac4754f56
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9c55feb9-23d8-4798-a3c5-70ec736df3ad
exl-id: 546a699e-975f-42a1-8ab5-0de4bd7f4a8f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 77%

---

# Configuration des points d’entrée TaskManager {#configuring-task-manager-endpoints}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les points de fin TaskManager permettent aux utilisateurs de Workspace d’appeler le service.

**Paramètres des points de fin TaskManager**

Utilisez les paramètres suivants pour configurer un point de fin TaskManager.

**Nom :** (obligatoire) identifie le point d’entrée. Le nom est affiché dans l’affichage carte de Workspace. N’incluez pas de caractère « &lt; », car le nom affiché dans Workspace serait tronqué. Si vous saisissez une URL en tant que nom de point d’entrée, assurez-vous que celle-ci est conforme aux normes syntaxiques en la matière précisées dans le document RFC1738.

**Description :** fournit une description du point d’entrée. N’incluez pas de caractère « &lt; », car la description affichée dans Workspace serait tronquée.

**Instructions :** instructions destinées à l’utilisateur qui démarre ce workflow.

**Responsable du processus :** nom de la personne chargée du processus.

**L’utilisateur peut transférer la tâche :** permet à l’utilisateur de transférer la tâche initiale.

**Afficher la fenêtre de pièce jointe :** autorise l’utilisateur à voir la fenêtre de pièce jointe.

**Autoriser l’ajout de pièces jointes :** autorise l’utilisateur à ajouter des pièces jointes et des notes.

**Tâche initialement verrouillée :** verrouille la tâche initiale.

**Ajout de listes ACL pour les files d’attente partagées :** la tâche initiale est créée avec des listes de contrôle d’accès pour les utilisateurs de file d’attente partagée.

**Catégorisation :** (obligatoire) catégorie dans laquelle l’utilisateur verra le formulaire dans Workspace. Sélectionnez une catégorie dans la liste ou sélectionnez Nouvelle catégorie pour ajouter une catégorie.

**Nom de l’opération :** (obligatoire) liste des opérations pouvant être attribuées au point d’entrée.
