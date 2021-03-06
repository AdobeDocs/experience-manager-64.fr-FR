---
title: Intégration des composants de l’espace de travail AEM Forms dans des applications Web
seo-title: Integrating AEM Forms workspace components in web applications
description: Comment réutiliser les composants d’espace de travail AEM Forms dans vos propres applications Web pour profiter de leurs fonctionnalités et d’une intégration étroite.
seo-description: How to reuse AEM Forms workspace components in your own webapps to leverage functionality and provide tight integration.
uuid: bb9b8aa0-3f41-4f44-8eb7-944e778ee8a6
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 6be87939-007e-42c7-8a41-e34ac2b8bed4
exl-id: 4e3ed3c8-ef77-432e-ad4d-7d341787cc5c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 72%

---

# Intégration des composants de l’espace de travail AEM Forms dans des applications Web {#integrating-aem-forms-workspace-components-in-web-applications}

Vous pouvez utiliser les [composants](/help/forms/using/description-reusable-components.md) de l’espace de travail AEM Forms dans votre propre application Web. L’exemple d’implémentation suivant utilise des composants d’un paquet de développement d’espace de travail AEM Forms installé sur une instance CRX™ pour créer une application Web. Personnalisez la solution ci-dessous en fonction de vos besoins. L’exemple d’implémentation réutilise `UserInfo`, `FilterList`, et `TaskList`composants dans un portail web.

1. Connectez-vous à l’environnement CRXDE Lite à l’adresse `https://[server]:[port]/lc/crx/de/`. Assurez-vous que vous avez installé un package de développement d’espace de travail AEM Forms.
1. Création d’un chemin `/apps/sampleApplication/wscomponents`.
1. Copiez css, images, js/libs, js/runtime et js/registry.js

   * de `/libs/ws`
   * vers `/apps/sampleApplication/wscomponents`.

1. Créez un fichier demomain.js dans le dossier /apps/sampleApplication/wscomponents/js. Copiez le code de /libs/ws/js/main.js dans demomain.js.
1. Dans demomain.js, supprimez le code pour initialiser le routeur et ajoutez le code suivant :

   ```
   require(['initializer','runtime/util/usersession'], 
       function(initializer, UserSession) { 
           UserSession.initialize( 
               function() { 
                   // Render all the global components
                   initializer.initGlobal();  
               }); 
       });
   ```

1. Créez un noeud sous /content par nom `sampleApplication` et type `nt:unstructured`. Dans les propriétés de ce noeud, ajoutez `sling:resourceType` de type Chaîne et valeur `sampleApplication`. Dans la liste de contrôle d’accès de ce nœud, ajoutez une entrée pour `PERM_WORKSPACE_USER` autorisant des privilèges jcr:read. En outre, dans la liste de contrôle d’accès de `/apps/sampleApplication` ajouter une entrée pour `PERM_WORKSPACE_USER` autorisation des privilèges jcr:read.
1. Dans `/apps/sampleApplication/wscomponents/js/registry.js` mettre à jour les chemins d’accès à partir de `/lc/libs/ws/` to `/lc/apps/sampleApplication/wscomponents/` pour les valeurs de modèle.
1. Dans le fichier JSP de votre page d’accueil du portail, à l’adresse `/apps/sampleApplication/GET.jsp`, ajoutez le code suivant pour inclure les composants requis dans le portail.

   ```as3
   <script data-main="/lc/apps/sampleApplication/wscomponents/js/demomain" src="/lc/apps/sampleApplication/wscomponents/js/libs/require/require.js"></script>
   <div class="UserInfoView gcomponent" data-name="userinfo"></div> 
   <div class="filterListView gcomponent" data-name="filterlist"></div> 
   <div class="taskListView gcomponent" data-name="tasklist"></div> 
   ```

   Incluez également les fichiers CSS requis pour les composants d’espace de travail AEM Forms.

   >[!NOTE]
   >
   >Chaque composant est ajouté à la balise du composant (ayant la classe gcomponent) pendant le rendu. Assurez-vous que votre page d’accueil contient ces balises. Voir le fichier `html.jsp` de l’espace de travail AEM Forms pour en savoir plus sur les balises de contrôle de base.

1. Pour personnaliser les composants, agrandissez les vues existantes pour le composant requis comme suit :

   ```as3
   define([ 
       ‘jquery’, 
       ‘underscore’, 
       ‘backbone’, 
       ‘runtime/views/userinfo'],
       function($, _, Backbone, UserInfo){ 
           var demoUserInfo = UserInfo.extend({ 
               //override the functions to customize the functionality 
               render: function() { 
                   UserInfo.prototype.render.call(this); // call the render function of the super class 
                   … 
                   //other tasks 
                   … 
               } 
           }); 
           return demoUserInfo; 
   });
   ```

1. Modifiez le portail CSS pour configurer la mise en page, le positionnement et le style des composants souhaités sur votre portail. Par exemple, vous souhaitez garder la couleur d’arrière-plan en noir pour ce portail pour afficher correctement le composant userInfo. Pour ce faire, modifiez la couleur d’arrière-plan dans `/apps/sampleApplication/wscomponents/css/style.css` comme suit :

   ```as3
   body {
       font-family: "Myriad pro", Arial;
       background: #000;    //This was origianlly #CCC    
       position: relative;
       margin: 0 auto;
   }
   ```
