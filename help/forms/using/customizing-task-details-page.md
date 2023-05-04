---
title: Personnaliser les détails de la tâche
seo-title: Customizing the task details page
description: Comment personnaliser la page des détails de la tâche dans l’espace de travail AEM Forms pour modifier les informations par défaut affichées sur une tâche.
seo-description: How-to customize the task details page in AEM Forms workspace to modify the default information displayed about a task.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
exl-id: de97e6f7-25bf-462b-b67d-0d3fbd86a321
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 39%

---

# Personnaliser les détails de la tâche {#customizing-the-task-details-page}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La page Détails de la tâche contient des informations relatives à une tâche et à ses processus. Cependant, vous pouvez personnaliser la page Détails de la tâche pour ajouter ou supprimer des informations.

Vous pouvez ajouter les informations suivantes à la page Détails de la tâche :

* Informations disponibles dans l’objet JSON d’une tâche (section Tâche dans [Description de l’objet JSON de l’espace de travail AEM Forms](/help/forms/using/html-workspace-json-object-description.md))
* Informations disponibles dans l’objet JSON d’une instance de processus (section Instance de processus dans [Description de l’objet JSON de l’espace de travail AEM Forms](/help/forms/using/html-workspace-json-object-description.md))

Pour personnaliser la page Détails de la tâche :

1. Suivez [Procédure générique de personnalisation de l’espace de travail AEM Forms.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Pour afficher des informations supplémentaires, ajoutez les paires clé-valeur correspondantes au fichier `translation.json` dans le bloc `todo` > bloc `details` > bloc `app` > [bloc `required`].

   Le [ bloc `required` ] fait référence aux blocs disponibles tels que le bloc de tâche pour les informations de tâche, le bloc de processus pour le traitement des informations et le bloc de tâches en attente pour les informations de tâches en attente.

   Par exemple, pour ajouter des informations sur la sélection d’itinéraire requise dans la page des détails de la tâche, vous pouvez ajouter la paire clé-valeur suivante dans le bloc de tâche :

   ```
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >Ajoutez les paires clé-valeur correspondantes pour toutes les langues prises en charge.

1. Copiez `/libs/ws/js/runtime/templates/taskdetails.html` dans `/apps/ws/js/runtime/templates/taskdetails.html`.

   Ajoutez les nouvelles informations à `/apps/ws/js/runtime/templates/taskdetails.html`. Par exemple :

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. Ouvrez /apps/ws/js/registry.js pour le modifier.

   Recherchez et remplacez `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` par `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Pour personnaliser la page des détails de la tâche avec les tâches créées dans l’onglet **Démarrer le processus** de l’espace de travail AEM Forms, ajoutez les nouvelles informations à `/apps/ws/js/runtime/templates/startprocess.html`.
>
>Pour ajouter de nouveaux styles pour les informations ajoutées dans la page Détails, modifiez le fichier CSS à l’aide de la section *Modifications de l’interface utilisateur* dans [Personnalisation de l’espace de travail](/help/forms/using/changing-locale-user-interface.md).
