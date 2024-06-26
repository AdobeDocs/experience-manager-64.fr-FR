---
title: Modifier les paramètres régionaux de l’interface utilisateur de l’espace de travail AEM Forms
seo-title: Changing the locale of AEM Forms workspace user interface
description: Comment modifier l’espace de travail AEM Forms pour localiser le texte, les catégories réduites, les files d’attente et les processus, ainsi que le sélecteur de date dans l’interface.
seo-description: How to modify the AEM Forms workspace to localize text, collapsed categories, queues, and processes, and the date picker on the interface.
uuid: f8e7d399-98d9-4655-b51f-0346a5713f06
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: e4ca8188-fb9a-44bf-8437-a98abaa7521a
exl-id: 9968f399-454b-4cb2-b6af-2c16428ca7b4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 59%

---

# Modifier les paramètres régionaux de l’interface utilisateur de l’espace de travail AEM Forms {#changing-the-locale-of-aem-forms-workspace-user-interface}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’espace de travail AEM Forms fournit une prise en charge immédiate des langues suivantes : anglais, français, allemand et japonais. Cette application permet également de localiser l’interface utilisateur de l’espace de travail AEM Forms dans n’importe quelle autre langue.

Pour localiser l’interface utilisateur de l’espace de travail AEM Forms dans la langue de votre choix, procédez comme suit :

* Localisez le texte de l’espace de travail AEM Forms.
* Localisez les catégories réduites, les files d’attente et les processus.
* Localisation du sélecteur de date

Avant d’exécuter les étapes ci-dessus, assurez vous de suivre les étapes indiquées dans la section [Procédure générique de personnalisation de l’espace de travail AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).

>[!NOTE]
>
>Pour modifier la langue de l’écran de connexion de l’espace de travail AEM Forms, reportez-vous à la section [Création d’un écran de connexion](/help/forms/using/creating-new-login-screen.md).

## Localisation du texte {#localizing-text}

Exécutez les étapes suivantes pour ajouter la prise en charge d’une *nouvelle* langue et le code de paramètres régionaux du navigateur *nw*.

1. Connectez-vous à CRXDE Lite.

   L’URL par défaut de CRXDE Lite est `https://[server]:[port]/lc/crx/de/index.jsp`.

1. Naviguez jusqu’à l’emplacement `apps/ws/locales` et créez un dossier `nw.`.
1. Copiez le fichier `translation.json` de l’emplacement `/apps/ws/locales/en-US` à l’emplacement `/apps/ws/locales/nw`.
1. Naviguez jusqu’à `/apps/ws/locales/nw` et ouvrez le fichier `translation.json` pour le modifier. Apportez des modifications spécifiques aux paramètres régionaux au fichier translation.json.

   Les exemples suivants contiennent le fichier translation.json pour les paramètres régionaux anglais et français de l’espace de travail AEM Forms.

   ![translation_json_in_en](assets/translation_json_in_en.png) ![translation_json_in_fr](assets/translation_json_in_fr.png)

## Localisation des catégories réduites, des files d’attente et des processus {#localizing-collapsed-categories-queues-and-processes}

L’espace de travail AEM Forms utilise des images pour afficher les en-têtes de catégories, des files d’attente et des processus. Vous avez besoin d’un package de développement pour localiser ces en-têtes. Pour plus d’informations sur la création d’un package de développement, consultez la section [Générer le code de l’espace de travail AEM Forms](introduction-customizing-html-workspace.md#building-html-workspace-code).

Dans les étapes suivantes, on considère que les nouveaux fichiers image localisés sont *Categories_nw.png*, *Queue_nw.png* et *Processes_nw.png*. La largeur recommandée des images est de 19 px.

>[!NOTE]
>
>Pour trouver le code de paramètres régionaux de la langue du navigateur de votre navigateur. Ouvrez `https://[server]:[port]/lc/libs/ws/Locale.html`.

![collapsing_panels_image](assets/collapsing_panels_image.png)

Effectuez les étapes suivantes pour localiser les images :

1. A l’aide d’un client WebDAV, placez les fichiers image dans la variable */apps/ws/images* dossier.
1. Naviguez jusqu’à&#x200B;*/apps/ws/css*. Ouvrez *newStyle.css* pour le modifier et ajoutez les entrées suivantes :

   ```
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
   
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
   
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. Effectuez toutes les modifications sémantiques répertoriées dans l’article [Personnaliser lʼespace de travail](/help/forms/using/introduction-customizing-html-workspace.md).
1. Accédez au *js/runtime/utility* et ouvrez le fichier* usersession.js* pour le modifier.
1. Recherchez le code figurant dans le bloc de code original et ajoutez la condition *lang !== ‘nw’* à l’instruction « if » :

   ```
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

   ```
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## Localisation du sélecteur de date {#localizing-date-picker}

Vous avez besoin d’un package de développement pour localiser l’API *datepicker*. Pour plus d’informations sur la création d’un package de développement, consultez la section [Générer le code de lʼespace de travail AEM Forms](introduction-customizing-html-workspace.md#building-html-workspace-code).

1. Téléchargez et extrayez le fichier [Package de l’interface utilisateur jQuery](https://jqueryui.com/download/all/), accédez à *&lt;extracted jquery=&quot;&quot; ui=&quot;&quot; package=&quot;&quot;>*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n.
1. Copiez le fichier jquery.ui.datepicker-nw.js pour le code de paramètres régionaux dans apps/ws/js/libs/jqueryui et apportez des modifications spécifiques aux paramètres régionaux au fichier.
1. Naviguez jusqu’à `apps/ws/js` et ouvrez le fichier `jquery.ui.datepicker-nw.js` pour le modifier.
1. Dans le fichier main.js, créez un alias pour `jquery.ui.datepicker-nw.js.` Le code permettant de créer un alias pour le fichier `jquery.ui.datepicker-nw.js` est :

   ```
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. Utilisez l’alias `jqueryuidatepickernw` pour ajouter le fichier `jquery.ui.datepicker-nw.js` à tous les fichiers utilisant datepicker. L’API datepicker est utilisée dans les fichiers suivants :

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   L’exemple de code ci-dessous montre comment ajouter l’entrée de jquery.ui.datepicker-nw.js :

   ```
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {
   ```

   ```
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. Dans tous les fichiers qui utilisent l’API datepicker, modifiez les paramètres par défaut de l’API datepicker. L’API datepicker est utilisée dans les fichiers suivants :

   * apps\ws\js\runtime\views\searchtemplatedetails.js
   * apps\ws\js\runtime\views\outofoffice.js

   Modifiez le code suivant pour ajouter les nouveaux paramètres régionaux :

   ```
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

vers .

```
if (locale === 'ja-JP') {
    $.datepicker.setDefaults($.datepicker.regional.ja);
} else if (locale === 'de-DE') {
    $.datepicker.setDefaults($.datepicker.regional.de);
} else if (locale === 'fr-FR') {
    $.datepicker.setDefaults($.datepicker.regional.fr);
} else if (locale === 'nw') {
    $.datepicker.setDefaults($.datepicker.regional.nw);
} else {
    $.datepicker.setDefaults($.datepicker.regional['']);
}
```
