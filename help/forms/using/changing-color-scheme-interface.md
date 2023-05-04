---
title: Modification des couleurs de l’interface
seo-title: Changing the color scheme of the interface
description: Comment modifier sélectivement le modèle de couleurs des parties de l’interface utilisateur de l’espace de travail AEM Forms.
seo-description: How to modify the color scheme of AEM Forms workspace user interface portions selectively.
uuid: 32c32f7a-8271-4d2c-8a1f-ad5ab3c90b83
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 18dab82a-badf-4c32-83a2-cd5cb04cae89
exl-id: efbb9a9e-0ddf-49f2-bcb8-14cd0c6de5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 55%

---

# Modification des couleurs de l’interface {#changing-the-color-scheme-of-the-interface}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez modifier les couleurs des différentes parties de l’interface utilisateur de l’espace de travail AEM Forms selon vos besoins. Voici quelques exemples de personnalisation des couleurs. En plus des étapes décrites dans cet article, voir [Procédure générique de personnalisation d’AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).

## Barre de navigation supérieure {#top-navigation-bar}

### Utilisation d’une image d’arrière-plan {#using-background-image}

Pour mettre à jour la barre de navigation en haut de l’espace de travail AEM Forms :

1. Créez une image d’arrière-plan pour mettre à jour la couleur. Nommez le fichier newBackground.jpg.
1. Téléchargez le fichier image d’arrière-plan dans le dossier /apps/ws/images à l’aide d’un client WebDAV.

   >[!NOTE]
   >
   >Pour plus d’informations sur l’accès à WebDAV, voir [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/fr/crx/current/how_to/webdav_access.html).

1. Référencez la nouvelle image d’arrière-plan dans /apps/ws/css/newStyle.css en ajoutant le style suivant.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Utilisation de la propriété de couleur dans CSS {#using-color-property-in-css}

1. Ajoutez le style suivant dans newStyle.css sous /apps/ws/css

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Composant de catégorie {#category-component}

Le composant Catégorie affiche les différentes catégories de vos tâches dans le panneau de gauche. Pour modifier sa couleur, définissez la couleur d’arrière-plan dans l’élément `.category` du fichier CSS.

## Composant de tâches {#task-component}

Les tâches sont affichées dans le volet du milieu appelé TaskList de tâches. Pour modifier sa couleur, modifiez le style associé au sélecteur .task dans la feuille de style.
