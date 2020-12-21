---
title: Création d’un écran de connexion
seo-title: Création d’un écran de connexion
description: Comment modifier la page de connexion des modules de LiveCycle, par exemple de l’espace de travail AEM Forms ou de Forms Manager.
seo-description: Comment modifier la page de connexion des modules de LiveCycle, par exemple de l’espace de travail AEM Forms ou de Forms Manager.
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 63%

---


# Création d’un écran de connexion  {#creating-a-new-login-screen}

Vous pouvez modifier l’écran de connexion de tous les modules AEM Forms qui utilisent l’écran de connexion AEM Forms. Par exemple, les modifications affectent à la fois l’écran de connexion de Forms Manager et de l’espace de travail AEM Forms.

## Condition requise {#prerequisite}

1. Connectez-vous à `/lc/crx/de` avec les autorisations d’administrateur.
1. Procédez comme suit :

   1. Répliquer la structure hiérarchique : de `/libs/livecycle/core/content` à `/apps/livecycle/core/content`. Conservez les mêmes propriétés (nœud/dossier) et contrôle d’accès.
   1. Copiez le dossier de contenu : de `/libs/livecycle/core` à `/apps/livecycle/core`.
   1. Supprimez le contenu du dossier `/apps/livecycle/core`.

1. Procédez comme suit :

   1. Répliquer la structure hiérarchique : de `/libs/livecycle/core/components/login` à `/apps/livecycle/core/components/login`. Conservez les mêmes propriétés (nœud/dossier) et contrôle d’accès.
   1. Copiez le dossier de composants : de `/libs/livecycle/core` à `/apps/livecycle/core`.
   1. Supprimez le contenu du dossier : `/apps/livecycle/core/components/login`.

## Ajout d’un nouveau paramètre régional {#adding-a-new-locale}

1. Copiez le dossier `i18n` :

   * de `/libs/livecycle/core/components/login`
   * vers `/apps/livecycle/core/components/login`

1. Supprimez tous les dossiers à l&#39;intérieur de `i18n`, à l&#39;exception d&#39;un, par exemple `en`.
1. Sur le dossier `en`, procédez comme suit :

   1. Donnez au dossier le nom du paramètre régional que vous souhaitez prendre en charge. Par exemple, `ar`.
   1. Remplacez la valeur de propriété `jcr:language` par `ar` (pour le dossier `ar`).

   >[!NOTE]
   >
   >Si le paramètre régional est une combinaison de code langue-pays, tel que `ar-DZ`, modifiez le nom du dossier et la valeur de la propriété en `ar-DZ`.

1. Copier `login.jsp`:

   * de `/libs/livecycle/core/components/login`
   * vers `/apps/livecycle/core/components/login`

1. Modifiez le fragment de code suivant pour `/apps/livecycle/core/components/login/login.jsp` :

   ***Le paramètre régional est un code de langue***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("ar")) {
               browserLocale = "ar";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***Le paramètre régional est un code langue-pays***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().equalsIgnoreCase("ar-DZ")) {
               browserLocale = "ar-DZ";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***Pour modifier le paramètre régional par défaut***

   ```
   String browserLocale = "en";
   for(int i=0; i<locales.length; i++)
   
   To
   
   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
   ```

## Ajout de nouveau texte ou modification du texte existant  {#adding-new-text-or-modifying-existing-text}

1. Copier le dossier `i18n` :

   * de `/libs/livecycle/core/components/login`
   * vers `/apps/livecycle/core/components/login`

1. Modifiez la valeur de la propriété `sling:message` du nœud (sous le dossier du code du paramètre régional souhaité) pour laquelle vous souhaitez modifier le texte. La traduction est effectuée via la clé mentionnée dans la valeur de la propriété `sling:key` du nœud.
1. Pour ajouter une nouvelle paire clé-valeur, effectuez les opérations suivantes : Vérifiez un exemple dans la capture d’écran qui suit.

   1. Créez un nœud de type `sling:MessageEntry` ou copiez un nœud existant et renommez-le, sous tous les dossiers de paramètres régionaux.
   1. Copier `login.jsp` :

      * de `/libs/livecycle/core/components/login`
      * vers `/apps/livecycle/core/components/login`
   1. Modifiez `/apps/livecycle/core/components/login/login.jsp` pour incorporer le texte qui vient d’être ajouté.

   ![capture](assets/capture.png)

   ```
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   
   To
   
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   ```

## Ajout d’un nouveau style ou modification d’un style existant {#adding-new-style-or-modifying-existing-style}

1. Copier le noeud `login` :

   * de `/libs/livecycle/core/content`
   * vers `/apps/livecycle/core/content`

1. Supprimez les fichiers `login.js` et `jquery-1.8.0.min.js` du noeud `/apps/livecycle/core/content/login.`.
1. Modifiez les styles définis dans le fichier CSS.
1. Pour ajouter de nouveaux styles :

   1. Ajouter de nouveaux styles à `/apps/livecycle/core/content/login/login.css`
   1. Copier `login.jsp`

      * de `/libs/livecycle/core/components/login`
      * vers `/apps/livecycle/core/components/login`
   1. Modifiez `/apps/livecycle/core/components/login/login.jsp` pour incorporer les styles récemment ajoutés.


1. Par exemple :

   * Ajoutez les éléments suivants sur `/apps/livecycle/core/content/login/login.css`.

   ```css
   .newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
   ```

   * Modifiez l’élément suivant dans /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContentArea">
   
   To
   
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>Si les images existantes dans `/apps/livecycle/core/content/login` (copiées depuis `/libs/livecycle/core/content/login`) sont supprimées, supprimez les références correspondantes dans CSS.

## Ajoutez de nouvelles images {#add-new-images}

1. Suivez les étapes pour Ajouter un nouveau style ou modifier le style existant (décrites ci-dessus).
1. Ajoutez de nouvelles images dans `/apps/livecycle/core/content/login`. Pour ajouter une image :

   1. Installez le client WebDAV.
   1. Accédez au dossier `/apps/livecycle/core/content/login` à l’aide du client webDAV. Pour plus d’informations, voir : [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. Ajoutez de nouvelles images.

1. Ajoutez de nouveaux styles dans `/apps/livecycle/core/content/login/login.css,` correspondant aux nouvelles images ajoutées dans `/apps/livecycle/core/content/login`.
1. Utilisez les nouveaux styles dans `login.jsp` à `/apps/livecycle/core/components`.
1. Par exemple :

   * Ajoutez ce qui suit à la `/apps/livecycle/core/content/login/login.css` :

   ```css
   .newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
   ```

   * Modifiez l’élément suivant dans /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContainerBkg">
   
   To
   
   <div class="newLginContainerBkg">
   ```
