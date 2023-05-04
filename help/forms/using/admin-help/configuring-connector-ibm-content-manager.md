---
title: Configurer Connector for IBM Content Manager
seo-title: Configuring Connector for IBM Content Manager
description: Configurez Connector for IBM Content Manager pour permettre la communication entre AEM forms et IBM Content Manager.
seo-description: Configure the Connector for IBM Content Manager to enable communication between AEM forms and IBM Content Manager.
uuid: 3d55169d-93e3-4d4e-b18b-2a3394e1de3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3094b178-3b1a-46b3-8fbd-c20388afa3a7
exl-id: 8c65531e-f4f0-4cc4-b328-eaefb5662cf1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 8%

---

# Configurer Connector for IBM Content Manager{#configuring-connector-for-ibm-content-manager}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Connector for IBM Content Manager permet la communication entre AEM forms et IBM Content Manager. Pour plus d’informations, voir &quot;Connecteurs pour ECM&quot; dans [Référence des services](https://help.adobe.com/fr_FR/livecycle/11.0/Services/index.html).

## Configuration de la connexion à IBM Content Manager {#configure-the-ibm-content-manager-connection}

1. Dans Administration Console, cliquez sur Services > Connecteur pour IBM Content Manager.
1. Dans la zone Datastore Name , saisissez le nom de la banque de données IBM Content Manager à laquelle vous souhaitez vous connecter. Si la base de données est locale, saisissez son nom. Si la base est distante, indiquez son nom d&#39;alias.
1. Dans la zone Nom d’utilisateur , saisissez l’ID d’un utilisateur qui se connectera à la banque de données IBM Content Manager.
1. Dans la zone Mot de passe, saisissez le mot de passe de l’utilisateur.
1. (Facultatif) Dans la zone Chaîne de connexion de l’alias, saisissez des arguments de connexion supplémentaires. Dans la plupart des cas, cette zone doit être vide. Pour plus d’informations, consultez votre documentation IBM.
1. Cliquez sur Enregistrer.

## Validation des paramètres du service {#validation-of-service-settings}

Si vous saisissez un alias de banque de données, un nom d’utilisateur ou un mot de passe incorrects, les résultats sont les suivants, selon que le service Content Repository Connector for IBM Content Manager est en cours d’exécution ou non :

* Si le service est arrêté, aucune erreur n’apparaît lorsque vous enregistrez les informations de configuration du service. Cependant, la prochaine fois que vous démarrez le service, une exception est générée et le service ne démarre pas.
* Si le service est démarré, lorsque vous enregistrez les informations de configuration du service, celui-ci tente de valider immédiatement les informations d’identification. Dans ce cas, une erreur se produit et les informations de configuration ne sont pas enregistrées.
