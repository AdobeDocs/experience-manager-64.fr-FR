---
title: Personnalisation des onglets d’une tâche
seo-title: Customizing tabs for a task
description: Comment personnaliser les noms des onglets de vos tâches, dans l’espace de travail AEM Forms LiveCycle.
seo-description: How-to customize the names of the tabs for your tasks, in LiveCycle AEM Forms workspace.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
exl-id: 42671435-e0f0-41db-af83-182b01742954
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 68%

---

# Personnalisation des onglets d’une tâche {#customizing-tabs-for-a-task}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez personnaliser les noms des onglets pour le `Start Process`composant dans l’affichage `Start Process` Uber et le `Task Details` composant `ToDo` de l’affichage Uber.

1. Suivez la [Procédure générique de personnalisation de l’espace de travail AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Modifiez la valeur de `tabname` dans le fichier `translation.json`.

   Par exemple, modifiez `/apps/ws/locales/en-US/translation.json`/ pour l’anglais de la façon suivante.

   * Pour des tâches lancées dans le processus de démarrage, utilisez le fragment de code ci-dessous dans le bloc `"startprocess" : {}`.

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Pour des tâches dans Tâches, utilisez le fragment de code suivant dans le bloc `"todo" : {}`.

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Ajoutez la paire clé-valeur correspondante pour toutes les langues prises en charge.
