---
title: Procédure générique de personnalisation de l’espace de travail AEM Forms
seo-title: Procédure générique de personnalisation de l’espace de travail AEM Forms
description: Initiation à la personnalisation de l’interface utilisateur de l’espace de travail AEM Forms.
seo-description: Initiation à la personnalisation de l’interface utilisateur de l’espace de travail AEM Forms.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
exl-id: 2c0dab68-d77e-46fb-832d-90edea510750
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 52%

---

# Procédure générique de personnalisation de l’espace de travail AEM Forms {#generic-steps-for-aem-forms-workspace-customization}

Voici la procédure générique à suivre pour personnaliser Workspace HTML :

1. Connectez-vous à CRXDE Lite en accédant à `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Créez un dossier nommé `ws`à `/apps`, s’il n’existe pas. Cliquez sur **[!UICONTROL Enregistrer tout]**.
1. Accédez à `/apps/ws` et accédez à l’onglet **[!UICONTROL Contrôle d’accès]**.
1. Dans la liste **[!UICONTROL Contrôle d’accès]** , cliquez sur **[!UICONTROL +]** pour ajouter une nouvelle entrée. Cliquez de nouveau sur **[!UICONTROL +]**.
1. Recherchez et sélectionnez l’entité de sécurité **[!UICONTROL PERM_WORKSPACE_USER]**.

   ![Sélectionnez l’entité de sécurité PERM_WORKSPACE_USER dans le cadre des étapes génériques de personnalisation de Workspace HTML](assets/perm_workspace_user.png)

1. Octroyez le privilège `jcr:read` à l’entité de sécurité.
1. Cliquez sur **[!UICONTROL Enregistrer tout]**.
1. Copiez les fichiers `GET.jsp` et `html.jsp`du dossier `/libs/ws`dans le dossier `/apps/ws`.
1. Copiez le dossier `/libs/ws/locales` dans le dossier `/apps/ws` . Cliquez sur **[!UICONTROL Enregistrer tout]**.
1. Mettez à jour les références et les chemins d’accès relatifs dans le fichier `GET.jsp`, comme illustré ci-dessous, puis cliquez sur **[!UICONTROL Enregistrer tout]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Procédez comme suit pour des personnalisations CSS :

   1. Accédez au dossier `/apps/ws` et créez un dossier nommé `css`.
   1. Dans le dossier `css`,  , créez un fichier nommé `newStyle.css`.
   1. Ouvrez `/apps/ws/html`.jsp et changez à partir de

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   vers

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >placez l’entrée du fichier CSS défini par l’utilisateur après l’entrée de newStyle.css, comme indiqué ci-dessus.

1. Dans le fichier /apps/ws/html.jsp, changez

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   vers

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Procédez comme suit :

   1. Créez un dossier nommé `js`à `/apps/ws`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Créez un dossier nommé `libs`à `/apps/ws/js`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Créez un dossier nommé `jqueryui`à `/apps/ws/js/libs`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Copiez `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` dans `/apps/ws/js/libs/jqueryui`. Cliquez sur **[!UICONTROL Enregistrer tout]**.

1. Procédez comme suit pour des personnalisations HTML :

   1. Sous `/apps/ws/js`, créez un dossier nommé `runtime`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Sous `/apps/ws/js/runtime`, créez un dossier nommé `templates`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Copiez `/libs/ws/js/main.js` dans `/apps/ws/js/main.js`.
   1. Copiez /libs/ws/js/registry.js dans `/apps/ws/js/registry.js`.

1. Cliquez sur **[!UICONTROL Enregistrer tout]**, effacez le cache et actualisez l’espace de travail AEM Forms.

   Accédez à l’URL `https://[server]:[port]/lc/ws` et connectez-vous avec les informations d’identification administrateur/mot de passe. Le navigateur redirige vers `https://[server]:[port]/lc/apps/ws/index.html`.
