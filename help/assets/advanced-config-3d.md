---
title: Paramètres de configuration avancés
seo-title: Paramètres de configuration avancés
description: Découvrez les paramètres de configuration avancés qui s’appliquent à l’intégration AEM 3D pour les déploiements Maya et non Maya.
seo-description: Découvrez les paramètres de configuration avancés qui s’appliquent à l’intégration AEM 3D pour les déploiements Maya et non Maya.
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 61%

---


# Paramètres de configuration avancés {#advanced-configuration-settings}

Bien que les paramètres de configuration par défaut soient adaptés aux cas d’utilisation standard, il est parfois nécessaire d’effectuer des modifications.

Les paramètres de configuration avancés suivants s’appliquent à l’intégration d’AEM 3D pour les déploiements Maya et non Maya.

All settings are accessed using **CRXDE Lite** in AEM (**[!UICONTROL Tools > General > CRXDE Lite]**).

>[!NOTE]
>
>Si vous réinstallez le package, elle réinitialise tous les paramètres à leurs valeurs par défaut.

>[!CAUTION]
>
>La modification des paramètres qui ne sont pas répertoriés dans le tableau ci-dessous peuvent entraîner un dysfonctionnement du programme.

## Configuration des types de ressources {#asset-types-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Tools > General > CRXDE Lite]**), access the following configurations:

| Chemin | Description |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | Spécifie le type de fichier pour le format 3D intermédiaire créé pendant l’assimilation. Il doit être vide pour les formats de fichiers fbx et obj, ou fbx pour les formats autorisés par Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | Set to true or false to enable or disable this entry in the **[!UICONTROL assetTypes]** list. |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | Spécifiez un ou plusieurs suffixes de fichiers ou extensions de fichiers séparés par des virgules qui doivent être associés à ce type de ressource. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | Must be `native` for FBX and OBJ file formats and  `maya` for formats enabled by Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | Spécifie le type MIME pour ce type de ressource. For formats enabled by Maya it is recommended to use `application/x-ext`, where `ext` is the string specified as the `Extension` value. |

## Configuration d’assimilation {#ingestion-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Tools > General > CRXDE Lite]**), access the following configurations:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Chemin</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnInger</td> 
   <td>Active la génération d’une ombre portée pour une occlusion ambiante lors de l’affichage ou du rendu avec une scène IBL. S’applique à l’aperçu et au rendu avec RapidRefine.</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>Définissez-le sur <strong>false</strong> pour conserver les fichiers temporaires dans le dossier MayaWork après la conversion et le rendu. Peut être utile pour déboguer des problèmes de conversion et de rendu Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnInger</td> 
   <td><p>Lorsque cette option est activée, ImageMagick est installé sur le serveur et magickPath est configuré. Rapid Refine est utilisé pour créer une animation simple pour les objets 3D qui sont utilisés comme miniatures en mode Carte et dans d’autres modes.</p> <p>La création d’animations entraîne une consommation considérable des ressources du processeur lors du processus d’assimilation.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnInger</td> 
   <td>Permet la création automatique de cartes légères lors de l’assimilation. Lorsque la valeur est définie sur <strong>false</strong> pour désactiver la création automatique de cartes légères, cela peut considérablement réduire la consommation du processeur, mais la qualité est réduite lors de l’aperçu et du rendu avec Rapid Refine. N’affecte pas le rendu avec Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>When set to <strong>true</strong> (default), objects are moved vertically, if necessary, to ensure that all parts of the object are above the ground plane (y=0).</p> <p>When set to <strong>false</strong> (default), objects are not repositioned and may be partially hidden by a stage's ground plane. (S'applique uniquement pour la prévisualisation et le rendu avec Rapid Refine.) Toutefois, cela n’affecte pas le rendu avec Maya. When set to <strong>true</strong>, the vertical position of objects in Maya may be different than in preview or when rendering with Rapid Refine.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>Chemin et nom de l’utilitaire de conversion ImageMagick. Un chemin d’accès absolu est requis si la création de miniatures animées est activée.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPourcentage</td> 
   <td><p>Spécifie le nombre maximal d’unités centrales utilisées pour le traitement d’assimilation des ressources 3D.</p> <p>Des valeurs plus élevées entraînent l’accélération de l’assimilation, mais peuvent rendre AEM globalement moins réactif. Ce paramètre est approximatif. En effet, la précision augmente avec le nombre de cœurs de processeur.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Paramètres de configuration Cloud Services {#cloud-services-configuration-settings}

Les valeurs des paramètres suivants sont fournies par votre gestionnaire de compte d’Adobe, votre expert en attribution de privilèges d’accès ou votre représentant de l’assistance.

| **Chemin** | **Description** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | ID du compte AWS Adobe. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | Nom du compartiment de transfert S3 ; normalement `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | ID unique attribué par Adobe à votre organisation. Utilisé en tant qu’ID utilisateur de cookie AWS. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | Mot de passe associé à cet ID de client. Utilisé comme mot de passe AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/region` | Région AWS dans laquelle les services cloud sont déployés. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | ID du pool d’utilisateurs AWS Cognito applicable. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | ID client AWS Cognito pour le service de conversion dncr. |

## Common processing settings {#common-processing-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Tools > General > CRXDE Lite]**), access the following configurations:

| **Chemin** | **Description** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Nom et emplacement du dossier de travail pour la conversion et le rendu Maya. Le dossier est automatiquement créé s’il n’existe pas. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | Nom et emplacement du dossier de travail pour la conversion 3ds Max. Le dossier est automatiquement créé s’il n’existe pas. |
| `/libs/settings/dam/v3D/settings/debugNative` | Définissez-le sur **[!UICONTROL true]** pour activer la création de l’information de débogage lors de la conversion de format et le rendu avec le moteur de rendu Rapid Refine. |

## Configuration du moteur de rendu {#renderer-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Tools > General > CRXDE Lite]**), access the following configurations:

| **Chemin** | **Description** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | S’il est défini sur **[!UICONTROL true]** et si les cartes légères prégénérées ne sont pas disponibles (c’est-à-dire, si invokeLightMapsOnIngest=false), le moteur de rendu Rapid Refine crée des cartes légères lors du rendu afin d’améliorer sa qualité. Ce paramètre peut augmenter considérablement la durée du rendu. Ce paramètre défini sur **[!UICONTROL false]** réduit l’utilisation du processeur dans de telles situations, mais peut générer un rendu de plus faible qualité. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | Définissez ce paramètre sur **[!UICONTROL true]** ou **[!UICONTROL false]** pour activer ou désactiver un moteur de rendu, respectivement. |
| `/libs/settings/dam/v3D/renderers/*/Display` | Permet de modifier la chaîne affichée pour un moteur de rendu activé dans le sélecteur de rendu du panneau Rendu. |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | Spécifie le nombre maximal d’unités centrales utilisées pour effectuer le rendu des scènes 3D. Des valeurs élevées accélèrent le rendu, mais peuvent rendre AEM moins réactif. Ce paramètre est approximatif. En effet, la précision augmente avec le nombre de cœurs de processeur. |

## 3D Asset preview settings {#d-asset-preview-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Tools > General > CRXDE Lite]**), access the following configurations:

| Chemin | Description |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | Set to **[!UICONTROL true]** or **[!UICONTROL false]** to enable or disable auto-spin (automatic camera orbit) on page load. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Set to **[!UICONTROL true]** to restart auto-spin after **[!UICONTROL Reset]** is pressed. Ignoré lorsque la rotation automatique est désactivée. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | Spécifie la vitesse (en tours par minute) et la direction de la rotation automatique, avec des valeurs négatives pour une rotation de droite à gauche et des valeurs positives pour une rotation de gauche à droite. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | Set to **[!UICONTROL false]** to disable continuation with gradual fadeout of viewer responses to touch and mouse gestures. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | Indique la couleur du rideau de chargement qui peut éventuellement couvrir la fenêtre d’aperçu des ressources 3D lors du chargement et de l’initialisation. Valeur R, V et B avec chaque composant de couleur dans la plage de 0 à 255. |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | When set to **[!UICONTROL true]**, the load curtain will gradually fade out during the latter parts of viewer initialization. When set to **[!UICONTROL false]**, the curtain remains opaque until loading and initialization has completed. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | Set to **[!UICONTROL true]** or **[!UICONTROL false]** to enable or disable the load curtain for 3D asset preview. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | Lorsque la rotation automatique est active, la position verticale de la caméra est ajustée automatiquement par rapport à la hauteur de l’objet 3D. Lorsqu’elle est définie sur 0,5, la caméra sera placée verticalement à la moitié de la hauteur de l’objet, ce qui permet d’obtenir un centrage vertical de l’horizon dans la fenêtre. Avec des valeurs plus élevées, la caméra regarde vers le bas sur l’objet et la hauteur de l’horizon rendu augmente ; avec des valeurs plus petites, la caméra regarde vers le haut sur l’objet et l’horizon est abaissé. |

## 3D Sites component settings {#d-sites-component-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Tools > General > CRXDE Lite]**), access the following configurations:

| Chemin | Description |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Set to **[!UICONTROL true]** to reactivate auto-spin (automatic camera orbit) after home is pressed. Ignoré lorsque la rotation automatique est désactivée. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | Set to **[!UICONTROL false]** to disable continuation with gradual fadeout of viewer responses to touch and mouse gestures. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | Indique la couleur du rideau de chargement qui peut éventuellement couvrir la fenêtre d’aperçu du composant 3D Sites lors du chargement. Valeur R, V et B avec chaque composant de couleur dans la plage de 0 à 255. |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | When set to **[!UICONTROL true]**, the load curtain will gradually fade out during the latter parts of loading and initialization. When set to **[!UICONTROL false]**, the curtain remains opaque until loading and initialization has completed. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | Set to **[!UICONTROL true]** or **[!UICONTROL false]** to enable or disable the load curtain for the 3D Sites component. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | Lorsque la rotation automatique est active, la position verticale de la caméra est ajustée automatiquement par rapport à la hauteur de l’objet 3D. Lorsqu’elle est définie sur 0,5, la caméra sera placée verticalement à la moitié de la hauteur de l’objet, ce qui permet d’obtenir un centrage vertical de l’horizon dans la fenêtre. Avec des valeurs plus élevées, la caméra regarde vers le bas sur l’objet et la hauteur de l’horizon rendu augmente ; avec des valeurs plus petites, la caméra regarde vers le haut sur l’objet et l’horizon est abaissé. |

