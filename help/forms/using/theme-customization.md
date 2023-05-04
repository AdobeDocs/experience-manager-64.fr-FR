---
title: Personnaliser le thème
seo-title: Theme Customization
description: Comment personnaliser le thème de votre application AEM Forms.
seo-description: How to customize the theme of your AEM Forms app.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: fb1e0bec-c943-4468-920d-8ef360a01365
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 75%

---

# Personnaliser le thème {#theme-customization}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez personnaliser le code HTML et le fichier CSS pour personnaliser l’organisation et l’aspect de l’application AEM Forms. Vous pouvez, par exemple, modifier la couleur du fond d’écran ainsi que la hauteur des tâches ou des points de départ. L’exemple suivant fournit des instructions de modification :

* Afficher les instructions au lieu de la description
* nombre d’itinéraires d’affichage
* dégradé de fond

## Étapes {#steps}

1. Ouvrez votre projet.

   * Pour iOS, ouvrez `Capture.xcodeproj` dans Xcode.
   * Pour Android, ouvrez le projet Android dans Eclipse.
   * Pour Windows, ouvrez `MWSWindows.sln` dans Visual Studio.

1. Naviguez jusqu’au dossier des modèles.

   * Dans Xcode, accédez au dossier **Capture > www > wsmobile > js > runtime > templates**.
   * Dans Eclipse, accédez au dossier **assets > www > wsmobile > js > runtime > templates**.
   * Dans Visual Studio, accédez au dossier **MWSWindows > www > wsmobile > js > runtime > templates**.

1. Ouvrez le fichier `template.html` pour le modifier.
1. Recherchez la chaîne suivante :

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else 
   ```

   Remplacez-la par `<%`.

1. Rercherchez le code suivant dans le fichier `template.html` :

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Mettez la ligne suivante en commentaire et enregistrez le fichier.

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Accédez au dossier css.

   * Dans Xcode, accédez à **Capture > www > wsmobile > css**.
   * Dans Eclipse, accédez à **assets > www > wsmobile > css**.
   * Dans Visual Studio, accédez à **MWSWindows > www > wsmobile > css**.

1. Ouvrez le fichier `_style.css` pour le modifier.
1. Pour l’image d’arrière-plan, remplacez `#323232` par `#fff`.
1. Enregistrez les modifications apportées, puis fermez le fichier `_style.css`.
1. Ouvrez l’application AEM Forms.

   L’application AEM Forms affiche désormais des instructions au lieu d’une description.
