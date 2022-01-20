---
title: Personnalisation du thème
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
source-git-commit: 2208d23985ebd913b6aa9dee3bf16ce7529a8fa6
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 56%

---

# Personnalisation du thème {#theme-customization}

Vous pouvez personnaliser le code HTML et le fichier CSS pour personnaliser l’organisation et l’aspect de l’application AEM Forms. Vous pouvez, par exemple, modifier la couleur du fond d’écran ainsi que la hauteur des tâches ou des points de départ. L’exemple suivant donne des instructions pour modifier les paramètres suivants :

* Afficher les instructions au lieu de la description
* nombre d’itinéraires d’affichage
* dégradé de couleur d’arrière-plan

## Étapes {#steps}

1. Ouvrez votre projet.

   * Pour iOS, ouvrez `Capture.xcodeproj` dans Xcode
   * Pour Android, ouvrez le projet Android dans Eclipse.
   * Pour Windows, ouvrez `MWSWindows.sln` dans Visual Studio.

1. Naviguez jusqu’au dossier des modèles.

   * Dans Xcode, accédez au **Capture > www > wsmobile > js > runtime > modèles** dossier.
   * Dans Eclipse, accédez au **ressources > www > wsmobile > js > runtime > modèles** dossier.
   * Dans Visual Studio, accédez au **MWSWindows > www > wsmobile > js > runtime > modèles** dossier.

1. Ouvrez le `template.html` pour modification.
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

   * Dans Xcode, accédez à **Capture > www > wsmobile > css**.
   * Dans Eclipse, accédez à **ressources > www > wsmobile > css**.
   * Dans Visual Studio, accédez à **MWSWindows > www > wsmobile > css**.

1. Ouvrez le `_style.css` pour modification.
1. Pour l’image d’arrière-plan, modifiez `#323232` to `#fff`.
1. Enregistrez les modifications et fermez `_style.css` fichier .
1. Ouvrez l’application AEM Forms.

   L’application AEM Forms affiche maintenant les instructions à la place de la description.
