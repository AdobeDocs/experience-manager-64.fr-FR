---
title: Modifier le logo de l’organisation pour l’identité graphique
seo-title: Changing the organization logo for branding
description: Pour attribuer une marque à l’espace de travail AEM Forms, fournissez le logo de votre organisation en personnalisant le logo par défaut.
seo-description: To brand AEM Forms workspace provide the logo of your organization by customizing the default logo.
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 890e98af-0491-4b59-9a9b-6c245db54f0f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 42%

---

# Modifier le logo de l’organisation pour l’identité graphique {#changing-the-organization-logo-for-branding}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le logo de l’organisation s’affiche dans le coin supérieur gauche de l’espace de travail AEM Forms. Pour mettre à jour le logo, suivez le [Étapes génériques de la personnalisation de l’espace de travail AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) puis les étapes suivantes.

1. Créez un logo et nommez le fichier `NewWorkspace.png`. Placez le fichier image dans le dossier /apps/ws/images à l’aide d’un client WebDAV.

   >[!NOTE]
   >
   >La taille recommandée de l’image de logo est de 218 px × 20 px.

   >[!NOTE]
   >
   >Pour plus d’informations sur l’accès à WebDAV, consultez la section [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/fr/crx/current/how_to/webdav_access.html).

1. Reportez-vous à l’image du nouveau logo dans la feuille de style sous /apps/ws/css/newStyle.css en ajoutant le style suivant.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px; 
         }
   ```
