---
title: Personnaliser les images utilisées dans les actions d’itinéraire
seo-title: Customize images used in route actions
description: Comment personnaliser les images utilisées dans les actions d’itinéraire dans l’espace de travail AEM Forms LiveCycle.
seo-description: How-to customize the images used in route actions in LiveCycle AEM Forms workspace.
uuid: 42608376-587e-4b57-a9d5-8f9ebd981426
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 10158c13-47b4-43e3-ac47-690f3cbab158
exl-id: 7b1f60e7-c8fa-43b6-bef4-88b42e7bbc36
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 69%

---

# Personnaliser les images utilisées dans les actions d’itinéraire {#customize-images-used-in-route-actions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour personnaliser les images utilisées dans les actions d’itinéraire, suivez la procédure décrite à la section [Procédure générique de personnalisation](/help/forms/using/generic-steps-html-workspace-customization.md) suivi des étapes décrites dans cet article.

## Images pour les actions d’itinéraire {#images-for-route-actions}

1. Ajoutez les styles définissant les images dans le CSS à l’emplacement suivant pour les nouvelles actions d’itinéraire :

   `/apps/ws/css/newStyle.css`

   Par exemple : ajoutez un nouveau style appelé `myStyle1` comme indiqué ci-dessous et chargez le fichier image `myStyleIcon1.png` dans le dossier `/apps/ws/image` à l’aide d’un client WebDAV.

   >[!NOTE]
   >
   >Pour plus d’informations sur l’accès à WebDAV, voir [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/fr/crx/current/how_to/webdav_access.html).

   >[!NOTE]
   >
   >Préférez l’utilisation du nom du style pour qu’il soit identique au nom de l’action d’itinéraire.

   ```css
   .myStyle1{
   
           background-image: url('../images/myStyleIcon1.png');
   
       }
   ```

## Fenêtre contextuelle d’action de tâche Liste de tâches {#task-list-task-action-popup}

1. Créez un menu déroulant d’actions de liste de tâches, voir [Création du code de l’espace de travail AEM Forms](introduction-customizing-html-workspace.md#building-html-workspace-code). Vous devez utiliser le package de développement.

1. Copiez `/libs/ws/js/runtime/templates/task.html` dans `/apps/ws/js/runtime/templates/task.html`.

1. Si le nom du style CSS est identique au nom de l’action d’itinéraire provenant du serveur, modifiez le code suivant dans `/apps/ws/js/runtime/templates/task.html` :

   ```
   <%if(routeList == null){%>
               <li>
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li>
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   
   To
   
   <%if(routeList == null){%>
               <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li class="<%= availableCommands.directCommands[i]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   ```

1. Si le nom du style CSS est différent du nom de l’action d’itinéraire provenant du serveur, modifiez le code suivant dans `/apps/ws/js/runtime/templates/task.html`. Il ajoute une pile des conditions de servlet `if-else` pour mapper le style avec le nom de l’action d’itinéraire.

```
<%if(routeList == null){%>
            <li>
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
            <li>
                <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
            </li>
            <%}%>
            <%}%>
 
To
 
<%if(routeList == null){%>
            <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
                <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                     <li class="myStyle1" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                     <li class="myStyle2" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}%>
            <%}%>
            <%}%>
```

## Menu déroulant de l’action de tâche Détails de la tâche {#task-details-task-action-popup}

1. Copiez `/libs/ws/js/runtime/templates/taskdetails.html` dans `/apps/ws/js/runtime/templates/taskdetails.html`.

1. Si le nom du style CSS est identique au nom de l’action d’itinéraire provenant du serveur, modifiez le code suivant dans `/apps/ws/js/runtime/templates/taskdetails.html` :

   ```
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                       <%}%>
   ```

1. Si le nom du style CSS est différent du nom de l’action d’itinéraire provenant du serveur, modifiez le code suivant dans `/apps/ws/js/runtime/templates/taskdetails.html`. Il ajoute une pile des conditions de servlet `if-else` pour mapper le style avec le nom de l’action d’itinéraire.

   ```
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                   <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle1" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle2" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}%>
               <%}%>
   ```

1. Ouvrez `/apps/ws/js/registry.js` pour le modifier et recherchez le texte suivant :\
   `"text!/lc/libs/ws/js/runtime/templates/taskdetails.html"`

1. Remplacez le texte par le texte suivant :\
   `"text!/lc/apps/ws/js/runtime/templates/taskdetails.html"`
