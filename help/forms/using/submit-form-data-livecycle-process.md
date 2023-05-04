---
title: Configuration d’AEM Forms pour envoyer des données de formulaire aux processus AEM Forms sur JEE
seo-title: Configuring AEM Forms to submit form data to an AEM Forms on JEE process
description: AEM Forms vous permet d’intégrer des formulaires adaptatifs aux processus AEM Forms on JEE pour le traitement des données de formulaire.
seo-description: AEM Forms allows you to integrate adaptive forms with AEM Forms on JEE processes for processing form data.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
role: Admin
exl-id: 260e405e-f59c-4aea-b83f-53ee103df94e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 54%

---

# Configuration d’AEM Forms pour envoyer des données de formulaire aux processus AEM Forms sur JEE {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les formulaires adaptatifs prennent en charge l’envoi de données à un processus AEM Forms on JEE pour un traitement ultérieur. Il vous permet de déclencher un processus AEM Forms on JEE avec les données disponibles à partir du formulaire envoyé. Pour permettre à votre instance AEM Forms d’envoyer un formulaire adaptatif à AEM Forms sur le processus JEE, procédez comme suit :

## Configuration de votre serveur AEM Forms {#configure-your-aem-forms-server}

Pour permettre à votre serveur d’AEM forms d’envoyer des données à un serveur AEM Forms on JEE, procédez comme suit :

1. Accédez à la configuration de console web AEM à l’adresse https://[*host*]:[*port*]/system/console/configMgr.

1. Recherchez et cliquez sur le composant **Configuration du SDK client d’Adobe LiveCycle**.
1. Cliquez pour modifier l’URL du serveur de configuration, le nom d’utilisateur et le mot de passe du serveur AEM Forms on JEE.
1. Vérifiez les paramètres et cliquez sur **Enregistrer**.

![Configuration de SDK client Adobe LiveCycle](assets/clientsdkconfiguration.jpg)

## Associez les données aux champs de processus {#map-data-with-process-fields}

Une fois votre AEM Forms configuré, mappez les données XML et les pièces jointes du formulaire envoyé aux champs du processus AEM Forms on JEE. Pour ce faire :

1. Dans AEM console de configuration web, cliquez sur pour éditer le **Localisateur et invocateur du processus de LiveCycle de guide** configuration.
1. Spécifiez les paramètres suivants :

   * **Nom du paramètre de données XML** (obligatoire) : spécifiez le fichier de propriété XML du processus AEM Forms sur JEE qui doit traiter les données envoyées. La valeur par défaut est **dataxml**.
   * **Nom du paramètre de pièces jointes**(facultatif) : spécifiez la liste d’objets de document que le processus AEM Forms sur JEE doit traiter. La valeur par défaut est **fileAttachmentsList**.

1. Vérifiez les paramètres et cliquez sur **Enregistrer**.

![Localisateur et invocateur du processus Guide LiveCycle](assets/test3.jpg)

Une fois configurée, l’action Envoi au processus de serveur de formulaires liste les processus du serveur AEM Forms sur JEE contenant le paramètre XML des données spécifié.
