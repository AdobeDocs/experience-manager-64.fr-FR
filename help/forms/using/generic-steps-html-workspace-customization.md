---
title: Procédure générique de personnalisation de l’espace de travail AEM Forms
seo-title: Generic steps for AEM Forms workspace customization
description: Comment commencer à personnaliser l’interface utilisateur de l’espace de travail AEM Forms.
seo-description: How to get started customizing AEM Forms workspace user interface.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
exl-id: 2c0dab68-d77e-46fb-832d-90edea510750
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 70%

---

# Procédure générique de personnalisation de l’espace de travail AEM Forms {#generic-steps-for-aem-forms-workspace-customization}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les étapes génériques pour effectuer toute personnalisation sont les suivantes :

1. Connectez-vous à CRXDE Lite en accédant à lʼadresse `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Créez un dossier  nommé `ws` dans `/apps`, s’il n’existe pas. Cliquez sur **[!UICONTROL Enregistrer tout]**.
1. Naviguez jusqu’à `/apps/ws` et accédez à l’onglet **[!UICONTROL Contrôle d’accès]**.
1. Dans la liste **[!UICONTROL Contrôle d’accès]**, cliquez sur **[!UICONTROL +]** pour ajouter une nouvelle entrée. Cliquez de nouveau sur **[!UICONTROL +]**.
1. Recherchez et sélectionnez le principal de sécurité **[!UICONTROL PERM_WORKSPACE_USER]**.

   ![Sélectionnez le principal de sécurité PERM_WORKSPACE_USER dans le cadre des étapes génériques de personnalisation de Workspace HTML](assets/perm_workspace_user.png)

1. Octroyez le privilège `jcr:read` au principal de sécurité.
1. Cliquez sur **[!UICONTROL Enregistrer tout]**.
1. Copiez le `GET.jsp` et `html.jsp`des fichiers `/libs/ws`vers le dossier `/apps/ws` dossier.
1. Copiez le dossier `/libs/ws/locales` dans le dossier `/apps/ws`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
1. Mettez à jour les références et les chemins d’accès relatifs dans le fichier `GET.jsp`, comme indiqué ci-dessous, puis cliquez sur **[!UICONTROL Enregistrer tout]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Procédez comme suit pour des personnalisations CSS :

   1. Naviguez jusqu’au dossier `/apps/ws` et créez un dossier nommé `css`.
   1. Dans le `css`dossier, créer un fichier nommé `newStyle.css`.
   1. Ouvrez `/apps/ws/html`.jsp et changez

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
   >Placez l’entrée du fichier CSS défini par l’utilisateur après l’entrée de newStyle.css, comme illustré ci-dessus.

1. Dans le fichier /apps/ws/html.jsp, changez de

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   vers

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Procédez comme suit :

   1. Créez un dossier nommé `js` dans `/apps/ws`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Créez un dossier nommé `libs` dans `/apps/ws/js`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Créez un dossier nommé `jqueryui` dans `/apps/ws/js/libs`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Copiez `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` dans `/apps/ws/js/libs/jqueryui`. Cliquez sur **[!UICONTROL Enregistrer tout]**.

1. Procédez comme suit pour les personnalisations de HTML :

   1. Sous `/apps/ws/js`, créez un dossier nommé `runtime`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Sous `/apps/ws/js/runtime`, créez un dossier nommé `templates`. Cliquez sur **[!UICONTROL Enregistrer tout]**.
   1. Copiez `/libs/ws/js/main.js` dans `/apps/ws/js/main.js`.
   1. Copiez /libs/ws/js/registry.js dans `/apps/ws/js/registry.js`.

1. Cliquez sur **[!UICONTROL Enregistrer tout]**, effacez le cache et actualisez l’espace de travail AEM Forms.

   Accédez à l’URL `https://[server]:[port]/lc/ws` et connectez-vous à l’aide des informations d’identification administrator/password. Le navigateur vous redirige vers `https://[server]:[port]/lc/apps/ws/index.html`.
