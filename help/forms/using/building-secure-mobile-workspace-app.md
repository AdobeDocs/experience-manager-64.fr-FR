---
title: Création d’une application AEM Forms sécurisée pour iOS
seo-title: Building a secure AEM Forms app for iOS
description: Procédure de création d’une application AEM Forms sécurisée.
seo-description: Steps to build a secure AEM Forms app.
uuid: 6c4b160f-4d0c-4976-9609-9196795b6c8e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 90cd8ba5-4f47-4074-bc54-6a7bb8afe256
exl-id: 7efc657e-b662-47db-8e70-62a37f3a3051
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 49%

---

# Création d’une application AEM Forms sécurisée pour iOS {#building-a-secure-aem-forms-app-for-ios}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous devez archiver le projet Xcode pour l’application AEM Forms afin de créer le programme d’installation (un fichier .ipa) et une liste de propriétés (un fichier .plist). Le fichier de liste de propriétés contient des informations de configuration de l’application interne hébergée, telles que le nom et l’emplacement d’hébergement de l’application. Pour plus d’informations sur le fichier de liste de propriétés, voir [À propos des fichiers de liste de propriétés d’informations](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Connectez-vous au site Web suivant :

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Création d’un ID d’application. Pour obtenir des instructions détaillées sur la création d’un ID d’application, voir [Création et configuration des ID d’application](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Pour configurer l’identifiant de lot de l’application iOS pour votre application, cliquez sur **[!UICONTROL Configuration de l’ID d’application]**.
1. Au bas de la page web, sélectionnez **[!UICONTROL Activation pour la protection des données]**. Spécifiez les options de protection des données.

   Cliquez sur **[!UICONTROL Terminé]**.

1. Accédez à Mise en service -> Distribution et créez un nouveau profil à l’aide de l’ID d’application configuré à l’étape 3.
1. Téléchargez le profil d’approvisionnement et ajoutez-le à Xcode et à l’iPad.
1. Ouvrez une session sur l’ordinateur Mac sur lequel Xcode et le SDK iOS sont installés et configurés.
1. Ouvrez le projet `AEM Forms.xcodeproj` dans Xcode.
1. Cliquez sur **[!UICONTROL AEM Forms]**, sous **[!UICONTROL TARGETS]**, sélectionnez **[!UICONTROL AEM Forms]**. Sélectionnez l’onglet **[!UICONTROL Paramètres de construction]**, recherchez la section **[!UICONTROL Droit de signature du code]**, puis dans la liste déroulante Droits, sélectionnez l’option **[!UICONTROL LC Enterprise]**.
1. Trouvez et ouvrez le fichier `LC Enterprise.entitlements` dans Xcode pour le modifier. Sous les droits **XCode, **ajoutez la même paire clé-valeur que celle présente dans votre profil d’approvisionnement.
1. Dans le **[!UICONTROL Paramètres de création]** , cliquez sur **[!UICONTROL Tous]** puis cliquez sur **[!UICONTROL Combiné]**.
1. Dans la **[!UICONTROL Paramètres]** list, expand **[!UICONTROL Signature de code]**.
1. Pour **[!UICONTROL Identité de signature de code]**, sélectionnez la signature appropriée. Vérifiez que la même signature est sélectionnée pour **[!UICONTROL Débogage]**, **[!UICONTROL Version finale]** et **[!UICONTROL N’importe quel SDK iOS]**.
1. Dans la liste **[!UICONTROL PROJET]**, sélectionnez **[!UICONTROL AEM Forms]** et vérifiez que la signature adéquate est sélectionnée pour **[!UICONTROL Identité de signature de code]**, **[!UICONTROL Débogage]**, **[!UICONTROL Version]** et **[!UICONTROL N’importe quel SDK iOS]**.
1. Générer et distribuer une application AEM Forms. Pour obtenir des instructions détaillées sur la génération et la distribution d’une application AEM Forms, consultez [Générer le programme d’installation de l’application AEM Forms](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app).
