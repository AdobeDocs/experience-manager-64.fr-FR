---
title: Intégration d’AEM Forms Workspace à Microsoft Office SharePoint Server
seo-title: Integrating AEM forms workspace with Microsoft Office SharePoint Server
description: Vous pouvez intégrer AEM'espace de travail forms à Microsoft Office SharePoint Server.
seo-description: You can integrate AEM forms workspace with Microsoft Office SharePoint Server.
uuid: d43396d4-117f-47ea-91e4-10ee96107bc8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 1bada670-3e0e-40f4-b9be-8b090df910be
exl-id: 43149456-8ff8-4ce1-9c51-1d950f60ff5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 18%

---

# Intégration d’AEM Forms Workspace à Microsoft Office SharePoint Server {#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

**- Conditions requises**

**Connaissances préalables** 
Avant de pouvoir ajouter AEM Forms Workspace au serveur SharePoint, vous devez avoir accès au serveur SharePoint avec les droits appropriés et vous devez connaître l’URL d’accès à Workspace. Les étapes ci-dessous supposent que vous connaissez SharePoint Server. Pour plus d’informations sur les composants Webpart dans SharePoint Server, voir Composants Webpart dans les services SharePoint Windows.

**Niveau d’utilisateur** Début

Vous pouvez utiliser AEM Forms Workspace en tant que composant Webpart dans Microsoft Office SharePoint Server (par exemple, Microsoft Office SharePoint Server 2007). Les utilisateurs peuvent accéder à AEM Forms Workspace en se connectant à votre serveur SharePoint à l’aide d’un navigateur web pour offrir une expérience unifiée. Dans cet article, vous découvrirez les étapes de base pour afficher AEM Forms Workspace en tant que composant Webpart dans Microsoft Office SharePoint Server. Vous pouvez suivre les étapes décrites dans cet article pour offrir une expérience unifiée afin que les utilisateurs qui se connectent à votre serveur SharePoint puissent accéder à AEM Forms Workspace à partir du même port.

>[!NOTE]
>
>Les étapes répertoriées dans cet article sont spécifiques à Microsoft SharePoint Server 2007. Vous pouvez également configurer HTML Workspace avec d’autres versions prises en charge de Microsoft SharePoint.

## Intégration d’AEM Forms Workspace à Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Pour intégrer AEM Forms Workspace à un composant Webpart, procédez comme suit :

1. Dans un navigateur Web, accédez au site SharePoint, par exemple : https://*[myMOSSserver]:*44299/default.aspx où *[myMOSSserver]* est le nom ou l’adresse IP du serveur SharePoint.

   >[!NOTE]
   >
   >44299 est le numéro de port par défaut du serveur SharePoint. Le numéro de port dépend de votre installation du serveur SharePoint.

1. Dans le coin supérieur droit de la page web, cliquez sur **Actions du site** et sélectionnez **Modifier la page**.
1. Cliquez sur le bouton **Ajouter un composant Webpart.**
1. Dans la boîte de dialogue Ajouter des composants Webpart - Boîte de dialogue de la page Web, sous Divers, sélectionnez **Composant Webpart de la visionneuse de pages** puis cliquez sur **Ajouter**.
1. Dans la zone Composant Webpart de la visionneuse de pages, cliquez sur **edit** et sélectionnez **Modifier le composant WebPart partagé**.

   >[!NOTE]
   >
   >La zone Composant Webpart de la visionneuse de pages s’affiche sous **Ajout d’un composant Webpart** sur le bouton sur lequel vous avez cliqué à l’étape 3, comme illustré ci-dessous (Figure 1) :

   ![Zone Composant Webpart de la visionneuse de pages de Microsoft Office SharePoint Server.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   **Figure :** *La zone Composant Webpart de la visionneuse de pages dans le serveur SharePoint de Microsoft Office.*

1. Sur la page Visionneuse de pages, effectuez les tâches suivantes :

   1. Dans la zone Lien, saisissez l’URL d’AEM Forms Workspace, par exemple https://*[AEM_forms_Server]:*8080/lc/ws où *[AEM_forms_Server]* représente l’adresse IP ou le nom du serveur AEM forms.
   1. Cliquez sur **Apparence** et modifiez la hauteur, la largeur et le titre de sorte que vous puissiez voir l’ensemble de l’interface utilisateur de Workspace. Par exemple, vous pouvez définir la hauteur et la largeur sur 6 pouces et 11 pouces, respectivement.
   1. Cliquez sur **Lien de test**. Une nouvelle fenêtre de navigateur Web s’affiche avec Workspace affiché dedans.
   1. (Facultatif) Cliquez sur **Disposition** et modifiez la mise en page de Workspace dans le composant Webpart.
   1. (Facultatif) Cliquez sur **Avancé** et modifiez d’autres paramètres, tels que la description et si Workspace peut être réduit ou fermé dans le composant Webpart.

      Cliquez sur **Appliquer**.

1. Cliquez sur **Quitter le mode d’édition** et vérifiez que vous pouvez accéder à Workspace.

Une fois les étapes ci-dessus effectuées, votre site SharePoint ressemble à l’illustration suivante (figure 2) :

![AEM Forms Workspace intégré à Microsoft Office SharePoint Server](assets/aem-forms-workspace.jpg)

**Figure :** *AEM Forms Workspace intégré à Microsoft Office SharePoint Server*
