---
title: Intégration des composants de l’espace de travail AEM Forms dans des applications Web
seo-title: Integrating AEM Forms workspace components in web applications
description: Comment réutiliser les composants de l’espace de travail AEM Forms dans vos propres applications web pour tirer parti des fonctionnalités et offrir une intégration étroite.
seo-description: How to reuse AEM Forms workspace components in your own webapps to leverage functionality and provide tight integration.
uuid: bb9b8aa0-3f41-4f44-8eb7-944e778ee8a6
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 6be87939-007e-42c7-8a41-e34ac2b8bed4
exl-id: 4e3ed3c8-ef77-432e-ad4d-7d341787cc5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 65%

---

# Intégration des composants de l’espace de travail AEM Forms dans des applications Web {#integrating-aem-forms-workspace-components-in-web-applications}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez utiliser l’espace de travail AEM Forms [components](/help/forms/using/description-reusable-components.md) dans votre propre application web. L’exemple d’implémentation suivant utilise des composants d’un package de développement d’espace de travail AEM Forms installé sur une instance CRX™ pour créer une application web. Personnalisez la solution ci-dessous en fonction de vos besoins. L’exemple d’implémentation réutilise les composants `UserInfo`, `FilterList` et `TaskList` dans un portail Web.

1. Connectez-vous à l’environnement CRXDE Lite à l’adresse `https://[server]:[port]/lc/crx/de/`. Assurez-vous que vous avez installé un package de développement d’espace de travail AEM Forms.
1. Créez un chemin d’accès `/apps/sampleApplication/wscomponents`.
1. Copiez css, images, js/libs, js/runtime et js/registry.js

   * de `/libs/ws`
   * vers `/apps/sampleApplication/wscomponents`.

1. Créez un fichier demomain.js dans le dossier /apps/sampleApplication/wscomponents/js. Copiez le code de /libs/ws/js/main.js dans demomain.js.
1. Dans demomain.js, supprimez le code pour initialiser le routeur et ajoutez le code suivant :

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

1. Créez un nœud sous /content du nom de `sampleApplication` et du type `nt:unstructured`. Dans les propriétés de ce nœud, ajoutez `sling:resourceType` du type chaîne et de la valeur `sampleApplication`. Dans la liste de contrôle d’accès de ce nœud, ajoutez une entrée pour `PERM_WORKSPACE_USER` autorisant des privilèges jcr:read. De même, dans la liste de contrôle d’accès de `/apps/sampleApplication`, ajoutez une entrée pour `PERM_WORKSPACE_USER` autorisant les privilèges jcr:read.
1. Dans `/apps/sampleApplication/wscomponents/js/registry.js`, mettez à jour les chemins d’accès de `/lc/libs/ws/` à `/lc/apps/sampleApplication/wscomponents/` pour les valeurs des modèles.
1. Dans le fichier JSP de la page d’accueil de votre portail, à l’adresse `/apps/sampleApplication/GET.jsp`, ajoutez le code suivant pour inclure les composants requis dans le portail.

   ```as3
   <script data-main="/lc/apps/sampleApplication/wscomponents/js/demomain" src="/lc/apps/sampleApplication/wscomponents/js/libs/require/require.js"></script>
   <div class="UserInfoView gcomponent" data-name="userinfo"></div> 
   <div class="filterListView gcomponent" data-name="filterlist"></div> 
   <div class="taskListView gcomponent" data-name="tasklist"></div> 
   ```

   Incluez également les fichiers CSS requis pour les composants de l’espace de travail AEM Forms.

   >[!NOTE]
   >
   >Chaque composant est ajouté à la balise du composant (ayant la classe gcomponent) pendant le rendu. Assurez-vous que votre page d’accueil contient ces balises. Voir le fichier `html.jsp` de l’espace de travail AEM Forms pour en savoir plus sur les balises de contrôle de base.

1. Pour personnaliser les composants, vous pouvez étendre les vues existantes pour le composant requis comme suit :

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

1. Modifiez le portail CSS pour configurer la mise en page, le positionnement et le style des composants souhaités sur votre portail. Par exemple, vous souhaitez garder la couleur d’arrière-plan en noir pour ce portail pour afficher correctement le composant userInfo. Vous pouvez le faire en modifiant la couleur d’arrière-plan dans `/apps/sampleApplication/wscomponents/css/style.css` comme suit :

   ```as3
   body {
       font-family: "Myriad pro", Arial;
       background: #000;    //This was origianlly #CCC    
       position: relative;
       margin: 0 auto;
   }
   ```
