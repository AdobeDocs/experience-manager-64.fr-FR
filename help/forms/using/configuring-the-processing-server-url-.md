---
title: Configuration des paramètres AEM DS
seo-title: Configuring AEM DS settings
description: Vous devez spécifier l’URL du serveur de traitement avant d’envoyer un formulaire.
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Admin
exl-id: f60beaae-4082-4165-8a37-9d9c94e360b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 37%

---

# Configuration des paramètres AEM DS {#configuring-aem-ds-settings}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cet article décrit comment configurer **Service de paramètres d’AEM**. Ce paramètre peut être utilisé dans plusieurs scénarios, par exemple :

* Dans Correspondence Management

   * Pour configurer le processus AEM Forms
   * Lors de l’utilisation de Forms Portal pour l’enregistrement à distance de brouillon/envoi

* Dans les formulaires adaptatifs pour les cas où le formulaire adaptatif est envoyé à partir de l’instance de publication

Vous trouverez ci-dessous les étapes de configuration de la variable **[!UICONTROL Paramètres AEM DS]**:

1. Ouvrez Configuration Manager sur l’instance de publication à l’aide de l’URL :

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. Dans la fenêtre **[!UICONTROL Configuration de la console web Adobe Experience Manager]**, recherchez et cliquez sur l’option **[!UICONTROL Paramètres AEM DS]**.

   ![ds_settings](assets/ds_settings.png)

1. La fenêtre **[!UICONTROL Service Paramètres AEM DS]** affiche les paramètres de configuration communs pour les composants AEM DS.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Ajoutez les informations suivantes dans les champs respectifs :

   **[!UICONTROL URL du serveur de traitement]** : le serveur de traitement est le serveur sur lequel les formulaires ou le workflow AEM doivent être déclenchés. Cela peut être identique à l’URL de l’instance d’auteur AEM ou à l’autre URL du serveur (c’est-à-dire http:// localhost:port/).

   **[!UICONTROL Nom d’utilisateur du serveur de traitement]** : nom d’utilisateur de l’utilisateur du workflow [basé sur l’URL du serveur utilisé].

   **[!UICONTROL Mot de passe du serveur de traitement]**: Mot de passe de l’utilisateur du workflow

   >[!NOTE]
   >
   >* Lors de l’utilisation de processus Forms ou AEM, avant d’envoyer un envoi depuis le serveur de publication, il est nécessaire de configurer le service de paramètres du répertoire de stockage global de documents. Sinon, l’envoi du formulaire échouera.

