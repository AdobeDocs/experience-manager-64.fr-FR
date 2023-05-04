---
title: Configuration de Connector for Microsoft SharePoint
seo-title: Configuring Connector for Microsoft SharePoint
description: Configurez Connector for Microsoft SharePoint pour activer la communication entre AEM forms et Microsoft SharePoint.
seo-description: Configure Connector for Microsoft SharePoint to enable communication between AEM forms and Microsoft SharePoint.
uuid: f1561b41-da20-4220-b13a-e78472a9449f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0ec881c9-8dcc-4847-9edf-24d9e6c4a7ea
exl-id: 9bd396a3-5da9-4355-ad76-e7132ac8aed8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 57%

---

# Configuration de Connector for Microsoft SharePoint {#configuring-connector-for-microsoft-sharepoint}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Connector for Microsoft SharePoint permet la communication entre AEM forms et Microsoft SharePoint. Pour plus d’informations, voir &quot;Connecteurs pour ECM&quot; dans [Référence des services](https://help.adobe.com/fr_FR/livecycle/11.0/Services/index.html).

1. Dans Administration Console, cliquez sur Services > Connecteur pour Microsoft SharePoint.
1. Définissez les paramètres suivants pour votre serveur SharePoint :

   **Nom d’hôte du serveur SharePoint :** numéro de port du nom d’hôte de l’application web sur le serveur SharePoint, au format `[hostname]:[port]`.

   **Nom d’utilisateur :** compte utilisateur servant à la connexion au serveur SharePoint.

   **Mot de passe :** mot de passe du compte utilisateur servant à la connexion au serveur SharePoint.

   **Nom de domaine :** domaine où se trouve le serveur SharePoint.

1. Cliquez sur Enregistrer.

## Service de configuration Microsoft SharePoint {#microsoft-sharepoint-configuration-service}

Le service de configuration Microsoft SharePoint `(MSSharePointConfigService)` vous permet de spécifier les informations d’identification de l’utilisateur AEM Forms disposant des droits d’emprunt d’identité. Pour plus d’informations sur les droits d’emprunt d’identité, consultez [Configuration du connecteur pour Microsoft SharePoint](https://help.adobe.com/fr/AEMForms/6.1/SharePointConfig/index.html). Suivez les étapes suivantes pour définir les paramètres de `MSSharePointConfigService` :

1. Dans Administration Console, cliquez sur Services > Applications et services > Gestion des services.
1. Parcourez la liste des services et cliquez sur `MSSharePointConfigService`.
1. Spécifiez les paramètres suivants sur la page Configuration :

   * Nom D’Utilisateur Pour Un Utilisateur Disposant D’Autorisations D’Emprunt D’Emprunt D’Identité
   * Mot De Passe De L’Utilisateur Ci-Dessus

1. Cliquez sur Enregistrer.
