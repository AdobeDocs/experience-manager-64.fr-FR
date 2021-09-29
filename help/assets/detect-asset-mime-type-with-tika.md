---
title: Utilisez Apache Tika pour détecter le type MIME des ressources numériques
description: Activez Apache Tika pour aider [!DNL Experience Manager] Les ressources à détecter le type MIME des ressources du flux de contenu pendant l’opération de chargement au lieu de l’extension de fichier.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 10%

---

# Utilisez Apache Tika pour détecter le type MIME des ressources numériques {#detecting-mime-type-of-assets-using-apache-tika}

En règle générale, Adobe Experience Manager Assets détecte le type MIME des ressources que vous chargez à partir de leur extension de fichier. Si vous utilisez Apache Tika pour charger des ressources, [!DNL Experience Manager] Assets détecte leur type MIME dans le flux de contenu pendant l’opération de chargement au lieu de l’extension de fichier.

Cette fonction est désactivée par défaut. Pour activer la fonction, configurez le service **Day CQ DAM Mime Type** à partir de Configuration Manager.

>[!NOTE]
>
>La détection de type MIME à l’aide de la bibliothèque Apache Tika est une opération gourmande en ressources.

1. Accédez à `https://[AEM_server]:[port]/system/console/configMgr` pour ouvrir la console web de Configuration Manager.
1. Dans la liste des services, recherchez **[!UICONTROL Day CQ DAM Mime Type Service]** et appuyez/cliquez sur l’icône **[!UICONTROL Modifier]** en regard de celui-ci pour l’ouvrir en mode d’édition.

1. Sélectionnez l’option **[!UICONTROL Détecter MIME à partir du contenu]** pour permettre l’analyse des ressources chargées afin de déterminer leur type MIME tout en ignorant les extensions de fichier. Par défaut, cette option n’est pas sélectionnée.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Cliquez ou appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.
