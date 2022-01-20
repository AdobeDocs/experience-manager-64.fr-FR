---
title: Configuration du projet Xcode et génération de l’application iOS
seo-title: Set up the Xcode project and build the iOS app
description: Explique comment générer une application AEM Forms standard pour iOS.
seo-description: Explains how to build standard AEM Forms app for iOS.
uuid: 33ccf014-05af-43c2-abb2-e0bd9c89ce32
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 2dec23f7-6cca-4cc9-a78a-acd23ae7da5f
exl-id: e03beca1-1a95-42c7-b20b-4a2d9eab4df9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 66%

---

# Configuration du projet Xcode et génération de l’application iOS {#set-up-the-xcode-project-and-build-the-ios-app}

AEM Forms fournit le code source complet de l’application AEM Forms. La source contient tous les composants nécessaires pour créer l’application personnalisée AEM Forms. l&#39;archive du code source, `adobe-lc-mobileworkspace-src-<version>.zip` fait partie de la variable `adobe-aemfd-forms-app-src-pkg-<version>.zip` module sur Distribution logicielle.

Pour obtenir le code source de l’application AEM Forms, procédez comme suit :

1. Ouvrez la [Distribution de logiciels](https://experience.adobe.com/downloads). Vous avez besoin d’un Adobe ID pour vous connecter à la Distribution de logiciels.
1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** disponible dans le menu d’en-tête.
1. Dans la section **[!UICONTROL Filtres]** :
   1. Sélectionnez **[!UICONTROL Formulaires]** dans la liste déroulante **[!UICONTROL Solution]**.
   2. Sélectionnez la version et le type du package. Vous pouvez également utiliser la variable **[!UICONTROL Recherche de téléchargements]** pour filtrer les résultats.
1. Appuyez sur le nom du package correspondant à votre système d’exploitation, puis sélectionnez **[!UICONTROL Accepter les termes du contrat de licence de l’utilisateur]**, puis appuyez sur **[!UICONTROL Télécharger]**.
1. Ouvrez [Package Manager](https://docs.adobe.com/content/help/fr/experience-manager-65/administering/contentmanagement/package-manager.html) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.
1. Sélectionnez le package et cliquez sur **[!UICONTROL Installer]**.

1. Pour télécharger l’archive du code source, ouvrez `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` dans votre navigateur.

   Le package source est téléchargé sur votre périphérique.

L&#39;image suivante affiche le contenu extrait du fichier`adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content](assets/mws-content.png)

Le tableau suivant détaille le contenu de la variable `adobe-lc-mobileworkspace-src-[version]/ios` dossier.

<table> 
 <tbody> 
  <tr> 
   <th><p>Répertoire</p> </th> 
   <th><p>Contenu</p> </th> 
  </tr> 
  <tr> 
   <td><p><code>CordovaLib</code></p> </td> 
   <td><p>PhoneGap SDK 6.4.0</p> </td> 
  </tr> 
  <tr> 
   <td><p><code>AEM Forms</code></p> </td> 
   <td><p>Ressources, modules externes PhoneGap et module principal de l’application</p> </td> 
  </tr> 
  <tr> 
   <td><p><code>AEM Forms.xcodeproj</code></p> </td> 
   <td><p>Projet Xcode pour l’application AEM Forms</p> </td> 
  </tr> 
  <tr> 
   <td><p><code>www</code></p> </td> 
   <td><p>Fichiers HTML, CSS, images et JavaScript pour le projet de l’application AEM Forms</p> </td> 
  </tr> 
 </tbody> 
</table>

Pour avoir des informations détaillées sur la signature de code et l’ajout de périphériques au portail d’approvisionnement iOS, consultez [Signature de code iOS : configuration, traitement et dépannage](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html).

## Génération d’une application AEM Forms standard {#set-up-the-xcode-project}

1. Effectuez les étapes suivantes pour configurer un projet dans Xcode et fournir une identité de signature :

   Connectez-vous à l’ordinateur Mac sur lequel Xcode et le SDK iOS sont installés et configurés.

1. Copiez le `adobe-lc-mobileworkspace-src-<version>.zip` archivez du dossier des téléchargements dans `[*User_Home*]/Projects/`.
1. Extrayez l’archive dans le `[*User_Home*]/Projects/[your-project]`répertoire .
1. Accédez au ` [*User_Home*]/Projects/ `[your-project]`/adobe-lc-mobileworkspace-src-[version]/ios` répertoire .
1. Ouvrez le projet `AEM Forms.xcodeproj` dans Xcode.
1. Cliquez sur **AEM Forms**, sous **TARGETS**, sélectionnez **AEM Forms**. Sélectionnez la **Paramètres de création** , recherchez la variable **Droit de signature de code** et dans les champs Débogage et Version , effectuez l’une des opérations suivantes :

   * Laisser les champs non spécifiés pour créer une application Mobile Workspace standard
   * Indiquez les champs à définir, en suivant la procédure décrite à la section [Création d’une application AEM Forms sécurisée pour iOS](/help/forms/using/building-secure-mobile-workspace-app.md) pour créer une application AEM Forms sécurisée.

1. Sous l’onglet **Paramètres de génération**, cliquez sur **Tous**, puis sur **Combiné**.
1. Dans la liste des **Paramètres**, développez **Signature de code**. 
1. Pour **Identité de signature de code**, sélectionnez la signature appropriée. Pour plus d’informations sur la création de signatures, voir [Création et téléchargement de profils d’approvisionnement de développement](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Vérifiez que la même signature est sélectionnée pour **Débogage**, **Version finale** et **N’importe quel SDK iOS**.
1. Remplacez le code suivant dans la fonction `AEM Forms-info.plist` fichier :

   ```java
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSAllowsArbitraryLoads</key>
   <true/>
   </dict>
   ```

   par ce qui suit si vous remplacez `yourserver.com`   par un nom d’hôte approprié pour votre serveur.

   ```java
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSExceptionDomains</key>
   <dict>
   <key>yourserver.com</key>
   <dict>
   <!-Include to allow subdomains->
   <key>NSIncludesSubdomains</key>
   <true/>
   <!-Include to allow HTTP requests->
   <key>NSTemporaryExceptionAllowsInsecureHTTPLoads</key>
   <true/>
   <!-Include to support forward secrecy->
   <key>NSExceptionRequiresForwardSecrecy</key>
   <false/>
   <!-Include to specify minimum TLS version->
   <key>NSTemporaryExceptionMinimumTLSVersion</key>
   <string>TLSv1.1</string>
   </dict>
   </dict>
   </dict>
   ```

   >[!NOTE]
   >
   >Cette étape est requise uniquement si l’application AEM Forms doit se connecter à un serveur qui ne respecte pas les exigences de sécurité du transport des applications.

1. Sous **PROJET**, sélectionnez **AEM Forms** et assurez-vous que la signature appropriée est sélectionnée pour **Identité de signature de code**, **Déboguer**, **Version** et **Tout SDK iOS**.
1. Connectez un iPad muni d’un profil d’approvisionnement à un ordinateur Mac.
1. Sélectionnez l’appareil configuré pour le **AEM Forms** projet.

   ![ipad](assets/ipad.png)

   Un périphérique muni d’un profil d’approvisionnement, iPad Air 2, est sélectionné.

1. Sélectionnez **Produit** > **Nettoyer**.
1. Sélectionnez **Produit** > **Générer**.

## Générer le programme d’installation de l’application AEM Forms {#build-the-installer-for-the-mobile-workspace-app}

Vous devez archiver le projet Xcode pour générer le programme d’installation (un fichier .ipa) et une liste de propriétés (un fichier .plist). Le fichier de liste de propriétés contient les informations de configuration de l’application interne hébergée, telles que le nom de l’application et l’emplacement où elle est hébergée. Pour en savoir plus sur le fichier de liste de propriétés, consultez [A propos des fichiers de liste de propriétés d’informations](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Connectez un iPad muni d’un profil d’approvisionnement à un ordinateur Mac. Pour plus d’informations sur la configuration d’iPad, voir [Création et téléchargement de profils d’approvisionnement de développement](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html)
1. Sélectionnez l’appareil configuré pour le **AEM Forms** projet.

   ![ipad-1](assets/ipad-1.png)

   Un périphérique muni d’un profil d’approvisionnement, iPad Air 2, est sélectionné.

1. Sélectionnez **Produit** > **Nettoyer**.
1. Sélectionnez **Produit** > **Générer**.
1. Sélectionnez **Produit** > **Archiver**.
1. Dans Organisateur - Archives, sélectionnez la dernière archive de votre projet et cliquez sur **Distribuer**.
1. Sélectionnez **Enregistrer pour déploiement en entreprise ou ad hoc** comme méthode de distribution et cliquez sur **Suivant**.
1. Sélectionnez l’identité de signature qui convient dans le champ **Code Signing Identity** et cliquez sur **Next**. Cliquez sur **Allow** (Autoriser) pour appliquer la signature.
1. Indiquez le nom de l’application et sélectionnez **Enregistrer pour distribution en entreprise**.
1. Indiquez l’URL de l’application dans le champ **Application URL**. Par exemple, pour héberger l’application sur un serveur CRX, fournissez une URL. `https://[*LC_host*]:[*port*]/lc/content/distribution/mobileworkspace/APP_NAME.ipa`.
1. Dans le champ **Titre**, indiquez AEM Forms.
1. Cliquez sur **Enregistrer** et fermez Xcode.

   Un fichier de programme d’installation, `AEM Forms.ipa`, et un fichier de liste de propriétés, `AEM Forms-info.plist`, sont alors créés à l’emplacement spécifié.

1. Ouvrez le `AEM Forms-info.plist` dans un éditeur.
1. Remplacez tous les espaces dans l’URL de votre fichier .ipa par %20. 
1. Enregistrez et fermez le fichier `AEM Forms-info.plist`.
