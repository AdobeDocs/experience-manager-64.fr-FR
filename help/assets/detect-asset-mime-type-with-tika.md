---
title: Utilisez Apache Tika pour détecter le type MIME des ressources numériques
description: Activation d’Apache Tika pour obtenir de l’aide [!DNL Experience Manager] Les ressources détectent le type MIME des ressources du flux de contenu pendant l’opération de chargement au lieu de l’extension de fichier.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 29%

---

# Utilisez Apache Tika pour détecter le type MIME des ressources numériques {#detecting-mime-type-of-assets-using-apache-tika}

En règle générale, Adobe Experience Manager Assets détecte le type MIME des ressources que vous chargez à partir de leur extension de fichier. Si vous utilisez Apache Tika pour charger des ressources, [!DNL Experience Manager] Les ressources détectent leur type MIME à partir du flux de contenu pendant l’opération de chargement au lieu de l’extension de fichier.

Cette fonction est désactivée par défaut. Pour activer la fonction, configurez le service **Type MIME de gestion des ressources numériques Day CQ** à partir du gestionnaire de configuration.

>[!NOTE]
>
>La détection de type MIME à l’aide de la bibliothèque Apache Tika est une opération gourmande en ressources.

1. Accédez à `https://[AEM_server]:[port]/system/console/configMgr` pour ouvrir la console web de Configuration Manager.
1. Dans la liste des services, localisez **[!UICONTROL Service Day CQ DAM Mime Type]** et appuyez/cliquez sur le bouton **[!UICONTROL Modifier]** en regard de l’icône pour l’ouvrir en mode d’édition.

1. Sélectionnez l’option **[!UICONTROL Détecter le type MIME à partir du contenu]** pour permettre à l’analyse des ressources transférées de déterminer leur type MIME, tout en ignorant les extensions de fichier. Par défaut, cette option n’est pas sélectionnée.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Cliquez ou appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.
