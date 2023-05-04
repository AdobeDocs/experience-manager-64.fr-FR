---
title: Utiliser les tâches
seo-title: Working with tasks
description: Utilisez la page Recherche de tâche pour rechercher des tâches par nom d’utilisateur ou ID de tâche. En savoir plus sur l’utilisation des tâches.
seo-description: Use the Task Search page to search for tasks by user name or task ID. Learn more about working with tasks.
uuid: 630372d5-255f-4ea8-974d-d4f923108673
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9161c8ca-ef33-4ec9-affc-94b5b3e48a4c
exl-id: 130ba568-b035-4c80-b47a-e19ed8d8ac25
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 40%

---

# Utiliser les tâches {#working-with-tasks}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Utilisez la page Recherche de tâche pour rechercher des tâches par nom d’utilisateur ou ID de tâche. Les résultats de la recherche s’affichent sur la page Liste des tâches, où vous pouvez accéder à l’historique d’une tâche. Vous pouvez également réaffecter une tâche si un utilisateur a trop de tâches ou si un utilisateur a reçu une affectation de tâche par erreur.

>[!NOTE]
>
>L’exécution de recherches de tâches ne renvoie aucun résultat pour les noms d’utilisateur commençant par un signe dièse (#). Si possible, évitez de créer des noms d’utilisateur commençant par un signe numérique.

## Recherche des tâches associées à un utilisateur {#search-for-tasks-associated-with-a-user}

1. Dans Administration Console, cliquez sur Services > Processus des formulaires > Recherche de tâche.
1. Dans Rechercher par, sélectionnez Nom d’utilisateur. Si vous connaissez une partie du nom d’utilisateur que vous recherchez, saisissez-la dans la zone. Cliquez sur Rechercher un utilisateur.
1. La page Rechercher un utilisateur s’affiche. Vous pouvez affiner davantage votre recherche en effectuant une recherche par nom d’utilisateur ou adresse électronique. Lorsque vous localisez l’utilisateur que vous recherchez, sélectionnez le bouton radio situé à côté du nom, puis cliquez sur OK.
1. Par défaut, la recherche de tâches recherche les tâches actuellement affectées à l’utilisateur. Pour rechercher également les tâches précédemment affectées à l’utilisateur, sélectionnez Afficher la tâche non affectée. Pour rechercher également les tâches que l’utilisateur a terminées, sélectionnez Afficher la tâche terminée.
1. Cliquez sur Rechercher. La page Liste des tâches s’affiche, répertoriant les résultats de la recherche.

## Rechercher une tâche lorsque vous connaissez son identifiant de tâche {#search-for-a-task-when-you-know-its-task-id}

1. Dans Administration Console, cliquez sur Services > Processus des formulaires > Recherche de tâche.
1. Dans Rechercher par, sélectionnez ID de la tâche et saisissez l’ID de la tâche dans la zone.
1. Cliquez sur Rechercher. La page Liste des tâches s’affiche, répertoriant les résultats de la recherche.

## Utilisation de la liste des tâches {#working-with-the-task-list}

Les résultats d’une recherche de tâche s’affichent sur la page Liste des tâches. Vous pouvez sélectionner une tâche pour ouvrir la page Historique de la tâche. De là, vous pouvez affecter la tâche à un autre utilisateur.

Les tâches sont affichées avec les informations suivantes :

**Identifiant de tâche :** entier positif attribué par Forms Workflow lorsque la tâche est instanciée (démarrée par un utilisateur). Vous pouvez utiliser cet identifiant pour effectuer le suivi de la tâche tout au long de son cycle de vie. Cliquez sur un ID de tâche pour afficher des détails sur l’historique de la tâche ou pour réaffecter la tâche à un autre utilisateur.

**Statut :** affecté signifie que la tâche est actuellement affectée à l’utilisateur. Non affecté signifie que la tâche a été affectée auparavant à l’utilisateur. L’état peut également être Terminé.

**Activité :** indique le formulaire et le nom d’une opération initiale ou l’opération du processus qui a généré la tâche.

**Identifiant de processus :** entier positif attribué par Forms Workflow lorsque le processus est instancié (démarré par un utilisateur ou une étape automatisée). Vous pouvez utiliser cet identificateur pour assurer le suivi de l’instance du processus sur l’ensemble de son cycle de vie.

**Nom du processus - Version :** nom du processus, tel que défini dans Workbench.

**Application :** nom de l’application à laquelle appartient le processus, tel que défini dans Workbench.

**Date de création :** date et heure auxquelles la tâche a été créée.

## Affichage de l’historique des tâches et réaffectation de tâches {#viewing-task-history-and-reassigning-tasks}

La page Historique des tâches affiche la liste des utilisateurs et des groupes affectés à une tâche particulière.

Pour chaque affectation de tâche, la liste affiche les informations suivantes :

**Nom :** nom de l’utilisateur.

**Statut :** Affecté signifie que la tâche est actuellement affectée à l’utilisateur. Non affecté signifie que la tâche a été affectée auparavant à l’utilisateur.

**Identifiant de liste de tâches :** identifiant numérique de la file d’attente de l’utilisateur auquel appartient la tâche. Un processus peut être partagé par plusieurs utilisateurs.

**Type :** indique le mode d’affectation de la tâche :

**Initial :** la tâche a été affectée initialement à l’utilisateur.

**Transfert :** le propriétaire d’origine de la tâche a affecté la tâche à un autre utilisateur.

**Rejet :** une tâche transférée a été rejetée ou une tâche a été renvoyée vers une liste de tâches sans avoir été achevée.

**Demande :** l’utilisateur a demandé que la tâche lui soit affectée dans une liste de tâches partagée.

**Transmission :** une durée prédéterminée est passée (comme définie dans l’action d’utilisateur dans Workbench) sans interaction de l’utilisateur et la tâche a été affectée à un autre utilisateur.

**Consultation :** le propriétaire de la tâche l’a envoyée pour consultation à un autre utilisateur qui peut ouvrir le formulaire, enregistrer les données, modifier les pièces jointes et les notes, mais qui ne peut pas terminer l’étape. L’utilisateur doit renvoyer la tâche au propriétaire qui lui a demandé de la consulter.

**Réaffectation admin. :** la tâche a été réaffectée par un administrateur.

**Date d’affectation :** date et heure auxquelles la tâche a été affectée à l’utilisateur.

### Affectation d’un nouvel utilisateur à une tâche {#assigning-a-new-user-to-a-task}

La page Affecter un utilisateur répertorie les utilisateurs pouvant être affectés à une tâche. Pour accéder à la page Affecter un utilisateur , cliquez sur Attribuer un nouvel utilisateur dans la page Historique des tâches.

1. Dans la zone Rechercher de la page Affecter un utilisateur , saisissez une partie ou la totalité du nom d’utilisateur ou de l’adresse électronique requise.
1. Sous Utilisation, sélectionnez Nom ou Adresse électronique, puis cliquez sur Rechercher. Les utilisateurs qui correspondent à la recherche s’affichent.
1. Sélectionnez l’utilisateur dans la liste, puis cliquez sur OK. La page Historique des tâches s’affiche avec la nouvelle affectation d’utilisateur.
