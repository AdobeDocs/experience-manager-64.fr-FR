---
title: Minimiser les fichiers JavaScript
seo-title: Minification of the JavaScript files
description: Instructions de génération du code minimisé après les personnalisations de l’espace de travail AEM Forms afin d’optimiser les fichiers JS pour le web.
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: 8394151e-e9cf-4f68-97a3-ba1d1dd6a2d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 50%

---

# Minimiser les fichiers JavaScript {#minification-of-the-javascript-files}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La minimisation supprime du code source les caractères redondants, comme les espaces blancs, les nouvelles lignes et les commentaires. Cela améliore les performances en réduisant la taille du code. Bien que la minimisation n’ait aucune incidence sur les fonctionnalités, elle réduit la lisibilité du code.

Pour générer du code minimisé pour les modifications sémantiques, procédez comme suit.

1. Copiez `client-html/src/main/webapp/js` de src-package dans filesystem.

   >[!NOTE]
   >
   >Voir [Introduction à la personnalisation de l’espace de travail AEM Forms](/help/forms/using/introduction-customizing-html-workspace.md) pour plus d’informations sur les packages.

1. Mettez à jour les chemins dans `main.js` sous client-html/src/main/webapp/js, pour added/updated models/views.

   Par exemple, pour ajouter un nouveau modèle Sharequeue, par exemple mySharequeue, modifiez :

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Mettez à jour `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` en cas de changement/ajout d’alias dans `main.js`.

   Par exemple, pour ajouter un nouveau modèle Sharequeue, par exemple mySharequeue, modifiez :

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   
   To
   
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. Sur client-html/src/main/webapp/js/minifier, exécutez la commande :

   ```shell
   mvn clean install
   ```

   Il génère un dossier minified-files, sous client-html/src/main/webapp/js avec main.js minifié et registry.js.

>[!NOTE]
>
>La minimisation fonctionne uniquement sur JVM 64 bits.

>[!NOTE]
>
>Si vous réduisez, la mise à niveau est affectée.
