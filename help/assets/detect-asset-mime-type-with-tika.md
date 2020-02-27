---
title: Utilisez Apache Tika pour détecter le type MIME des ressources numériques
description: Activez Apache Tika afin d’aider AEM Assets à détecter le type MIME des ressources à partir du flux de contenu pendant l’opération de téléchargement au lieu de l’extension de fichier.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Utilisez Apache Tika pour détecter le type MIME des ressources numériques {#detecting-mime-type-of-assets-using-apache-tika}

En règle générale, Adobe Experience Manager (AEM) Assets détecte le type MIME des ressources que vous téléchargez à partir de leur extension de fichier. Si vous utilisez Apache Tika pour transférer des ressources, AEM Assets détecte leur type MIME à partir du flux de contenu au cours de l’opération de transfert plutôt que de l’extension de fichier.

Cette fonction est désactivée par défaut. To enable the feature, configure the **Day CQ DAM Mime Type** service from Configuration Manager.

>[!NOTE]
>
>La détection de type MIME à l’aide de la bibliothèque Apache Tika est une opération gourmande en ressources.

1. Accédez `https://[AEM_server]:[port]/system/console/configMgr` à pour ouvrir la console Web Configuration Manager.
1. From the list of services, locate **[!UICONTROL Day CQ DAM Mime Type Service]** and tap/click the **[!UICONTROL Edit]** icon beside it to open it in Edit mode.

1. Select the **[!UICONTROL Detect MIME from content]** option to enable the parsing of uploaded assets to determine their MIME type while ignoring file extensions. Par défaut, cette option n’est pas sélectionnée.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Cliquez/appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.
