---
title: Modification de la police de l’interface
seo-title: Changing the font on the interface
description: Procédure de modification des polices sur l’interface utilisateur de manière sélective.
seo-description: How to change the fonts on the user interface selectively.
uuid: d079f656-76f8-4908-9989-dde79e215eb2
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 487e3966-443a-408e-b5af-899fcba6fca6
exl-id: bd7ec9d6-b1d2-4f01-8cef-05e5e1eceda1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 92%

---

# Modification de la police de l’interface {#changing-the-font-on-the-interface}

Vous pouvez modifier la police affichée dans l’espace de travail AEM Forms. Les polices utilisées dans une section spécifique de l’interface utilisateur sont définies dans la section correspondante de la feuille de style. Vous pouvez modifier les polices sur l’interface utilisateur de manière sélective.

Suivez les [Étapes génériques de personnalisation de l’espace de travail AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md) et en fonction de vos besoins, suivez les étapes de personnalisation de CSS, HTML ou des deux.

1. Modifiez ou ajoutez la famille de police dans un style existant.
1. Modifiez ou ajoutez la famille de police en ligne pour l’élément HTML.
1. Ajoutez un style et utilisez-le pour l’élément HTML.

Par exemple, pour remplacer la police du texte de la barre de navigation supérieure par Courier New, procédez comme suit :

1. Connectez-vous à CRXDE Lite en accédant à `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Utilisez l’une des méthodes suivantes :

   1. Pour modifier la famille de police dans un style existant, ajoutez la ligne suivante dans le fichier newStyle.css sous /apps/ws/css.

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. Pour ajouter la famille de police en ligne pour l’élément HTML, copiez le fichier `/libs/ws/js/runtime/templates/appnavigation.html` dans `/apps/ws/js/runtime/templates/appnavigation.html`.

      Mettez à jour le fichier apps/ws/js/runtime/templates/appnavigation.html comme suit :

      ```
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      Ouvrez le fichier /apps/ws/js/registry.js pour modifier et remplacer `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` par `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. Pour ajouter un style qui définit la famille de police, ajoutez la ligne suivante dans le fichier newStyle.css sous /apps/ws/css.

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      Pour ajouter la famille de police en ligne pour l’élément HTML, ajoutez le code suivant dans le fichier appnavigation.html sous /apps/ws/js/runtime/templates.

      ```css
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. Relancez l’espace de travail et effacez le cache du navigateur pour que les modifications soient visibles.

![change_font_before](assets/change_font_before.png)
**Figure :** *Barre de navigation supérieure avant la personnalisation de la police*

![change_font_after](assets/change_font_after.png)
**Figure :** *Barre de navigation supérieure après la personnalisation de la police du premier onglet*
