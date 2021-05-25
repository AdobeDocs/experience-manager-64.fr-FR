---
title: Utilisez Apache Tika pour détecter le type MIME des ressources numériques
description: Activez Apache Tika afin d’aider AEM Assets à détecter le type MIME des ressources à partir du flux de contenu pendant l’opération de téléchargement au lieu de l’extension de fichier.
contentOwner: AG
feature: Métadonnées,Outils de développement,Gestion des ressources
role: Administrator,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 36%

---

# Utilisez Apache Tika pour détecter le type MIME des ressources numériques {#detecting-mime-type-of-assets-using-apache-tika}

En règle générale, Adobe Experience Manager (AEM) Assets détecte le type MIME des ressources que vous chargez à partir de leur extension de fichier. Si vous utilisez Apache Tika pour transférer des ressources, AEM Assets détecte leur type MIME à partir du flux de contenu au cours de l’opération de transfert plutôt que de l’extension de fichier.

Cette fonction est désactivée par défaut. Pour activer la fonction, configurez le service **Day CQ DAM Mime Type** à partir de Configuration Manager.

>[!NOTE]
>
>La détection de type MIME à l’aide de la bibliothèque Apache Tika est une opération gourmande en ressources.

1. Accédez à `https://[AEM_server]:[port]/system/console/configMgr` pour ouvrir la console web de Configuration Manager.
1. Dans la liste des services, recherchez **[!UICONTROL Day CQ DAM Mime Type Service]** et appuyez/cliquez sur l’icône **[!UICONTROL Modifier]** en regard de celui-ci pour l’ouvrir en mode d’édition.

1. Sélectionnez l’option **[!UICONTROL Détecter MIME à partir du contenu]** pour permettre l’analyse des ressources chargées afin de déterminer leur type MIME tout en ignorant les extensions de fichier. Par défaut, cette option n’est pas sélectionnée.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Cliquez ou appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.
