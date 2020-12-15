---
title: Utilisez Apache Tika pour détecter le type de ressources numériques MIME
description: Activez Apache Tika afin d’aider AEM Assets à détecter le type MIME des ressources à partir du flux de contenu pendant l’opération de téléchargement au lieu de l’extension de fichier.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 37%

---


# Utilisez Apache Tika pour détecter le type MIME de ressources numériques {#detecting-mime-type-of-assets-using-apache-tika}

En règle générale, Adobe Experience Manager (AEM) Assets détecte le type MIME de ressources que vous téléchargez à partir de leur extension de fichier. Si vous utilisez Apache Tika pour transférer des ressources, AEM Assets détecte leur type MIME à partir du flux de contenu au cours de l’opération de transfert plutôt que de l’extension de fichier.

Cette fonction est désactivée par défaut. Pour activer la fonction, configurez le service **Day CQ DAM Mime Type** à partir de Configuration Manager.

>[!NOTE]
>
>La détection de type MIME à l&#39;aide de la bibliothèque Apache Tika est une opération gourmande en ressources.

1. Accédez à `https://[AEM_server]:[port]/system/console/configMgr` pour ouvrir la console Web de Configuration Manager.
1. À partir de la liste des services, recherchez **[!UICONTROL Day CQ MIM Type Service]** et appuyez/cliquez sur l&#39;icône **[!UICONTROL Modifier]** en regard de celle-ci pour l&#39;ouvrir en mode d&#39;édition.

1. Sélectionnez l&#39;option **[!UICONTROL Détecter MIME du contenu]** pour permettre l&#39;analyse des fichiers téléchargés afin de déterminer leur type MIME tout en ignorant les extensions de fichier. Par défaut, cette option n’est pas sélectionnée.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Cliquez ou appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.
