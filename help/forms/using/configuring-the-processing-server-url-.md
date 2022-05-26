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
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 94%

---

# Configuration des paramètres AEM DS {#configuring-aem-ds-settings}

Cet article explique comment configurer le **service de paramètres AEM DS**. Ce paramètre peut être utilisé dans plusieurs cas de figure, par exemple :

* Dans Correspondence Management

   * Pour configurer les processus AEM Forms
   * En utilisant le portail des formulaires pour enregistrer à distance un brouillon/un envoi

* Dans les formulaires adaptatifs pour les cas où le formulaire adaptatif est envoyé à partir d’une instance de publication

Voici les étapes pour configurer les **[!UICONTROL paramètres AEM DS]** :

1. Ouvrez Configuration Manager sur l’instance de publication à l’aide de l’URL :

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. Dans la fenêtre **[!UICONTROL Configuration de la console web Adobe Experience Manager]**, recherchez et cliquez sur l’option **[!UICONTROL Paramètres AEM DS]**.

   ![ds_settings](assets/ds_settings.png)

1. La fenêtre **[!UICONTROL Service Paramètres AEM DS]** affiche les paramètres de configuration communs pour les composants AEM DS.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Ajoutez les informations suivantes dans les champs respectifs :

   **[!UICONTROL URL du serveur de traitement]** : le serveur de traitement est le serveur sur lequel les formulaires ou le workflow AEM doivent être déclenchés. Elle peut être identique à l’URL de l’instance d’auteur AEM ou de l’autre URL du serveur (c’est-à-dire http://localhost:port/).

   **[!UICONTROL Nom d’utilisateur du serveur de traitement]** : nom d’utilisateur de l’utilisateur du workflow [basé sur l’URL du serveur utilisé].

   **[!UICONTROL Mot de passe du serveur de traitement]** : mot de passe de l’utilisateur du processus

   >[!NOTE]
   >
   >* Lorsque vous utilisez des processus AEM ou des formulaires, vous devez configurer le service de paramètres DS avant tout envoi depuis le serveur de publication. Dans le cas contraire, l’envoi du formulaire échouera.

