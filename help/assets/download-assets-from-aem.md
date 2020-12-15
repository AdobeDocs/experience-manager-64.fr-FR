---
title: Téléchargez des ressources numériques à partir de  [!DNL Adobe Experience Manager].
description: Découvrez comment télécharger des ressources à partir de  [!DNL Adobe Experience Manager] et activer ou désactiver la fonctionnalité de téléchargement.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 75%

---


# Télécharger des ressources depuis [!DNL Adobe Experience Manager] {#download-assets-from-aem}

Vous pouvez télécharger des ressources, dont des rendus statiques et dynamiques. Vous pouvez également envoyer des liens vers des ressources par courrier électronique, directement depuis [!DNL Adobe Experience Manager Assets]. Les ressources téléchargées sont compressées dans un fichier ZIP. La taille maximale du fichier ZIP compressé est de 1 Go pour la tâche d’exportation. Un maximum de 500 ressources par tâche d’exportation est autorisé.

>[!NOTE]
>
>Les destinataires du courrier électronique doivent être membres du groupe `dam-users` pour accéder au lien de téléchargement ZIP contenu dans le message. Pour télécharger les ressources, ils doivent disposer des autorisations de lancement des workflows qui déclenchent le téléchargement.

Les types de ressources Visionneuses d’images, Visionneuses à 360°, Visionneuses de supports variés et Visionneuses de carrousel ne peuvent pas être téléchargés.

Pour télécharger des ressources, procédez comme suit :

1. Dans le coin supérieur gauche de l&#39;AEM, appuyez sur le logo AEM, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Navigation]**.
1. Sur la page Navigation, appuyez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers.]**
1. Accédez à un dossier contenant les ressources à télécharger.
1. Sélectionnez le dossier ou une ou plusieurs ressources qu’il contient.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Télécharger.]**

   ![Options disponibles lors du téléchargement de ressources à partir d’Experience Manager Assets](/help/assets/assets/asset_download_dialog.png)

   *Figure : Options de la boîte de dialogue Télécharger.*

1. Dans la boîte de dialogue Télécharger, sélectionnez les options de téléchargement de votre choix.

   | Option d’exportation ou de téléchargement | Description |
   |---|---|
   | **[!UICONTROL Créer un dossier distinct pour chaque ressource]** | Sélectionnez cette option pour inclure chaque ressource que vous téléchargez (y compris les ressources dans des dossiers enfants imbriqués sous le dossier parent de la ressource) dans un dossier sur votre ordinateur local. Lorsque cette option n’est pas sélectionnée, par défaut, la hiérarchie de dossiers est ignorée et toutes les ressources sont téléchargées dans un dossier de votre ordinateur local. |
   | **[!UICONTROL Courrier électronique]** | Une notification électronique est envoyée à l’utilisateur. Les modèles standard d’email sont disponibles aux emplacements suivants :<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> Les modèles que vous personnalisez lors du déploiement sont disponibles aux emplacements suivants : <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>Vous pouvez stocker des modèles personnalisés spécifiques au client à ces emplacements :<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Ressources]** | Sélectionnez cette option pour télécharger la ressource dans son format d’origine sans aucun rendu.<br>L’option Sous-ressources est disponible si la ressource d’origine comporte des sous-ressources. |
   | **[!UICONTROL Rendus]** | Un rendu est une représentation binaire d’une ressource. Les ressources possèdent une représentation principale, à savoir celle du fichier transféré. Elles peuvent avoir un nombre illimité de représentations. <br> Avec cette option, vous pouvez sélectionner les rendus que vous souhaitez télécharger. Les rendus disponibles dépendent de la ressource que vous sélectionnez. Cette option est disponible si le fichier comporte des rendus. |
   | **[!UICONTROL Rendus dynamiques]** | Sélectionnez cette option pour générer une série de rendus alternatifs en temps réel. Lorsque vous sélectionnez cette option, vous sélectionnez également les rendus que vous souhaitez créer dynamiquement en effectuant une sélection dans la liste [Paramètres d’image prédéfinis](image-presets.md). <br>De plus, vous pouvez sélectionner la taille, l’unité de mesure, le format, l’espace colorimétrique, la résolution, ainsi que les éventuels modificateurs d’image (pour inverser l’image, par exemple). Cette option n’est disponible que si vous avez activé [!DNL Dynamic Media]. |

1. Dans la boîte de dialogue, appuyez sur **[!UICONTROL Télécharger.]**.

Lorsque vous sélectionnez un dossier à télécharger, l’ensemble de la hiérarchie des ressources sous ce dossier est téléchargé. Pour inclure chaque ressource que vous téléchargez (dont les ressources dans les dossiers enfants imbriqués sous le dossier parent) dans un dossier individuel, sélectionnez **[!UICONTROL Créer un dossier distinct pour chaque ressource]**.

## Activation du servlet de téléchargement de ressources {#enable-asset-download-servlet}

La servlet par défaut de [!DNL Experience Manager] permet aux utilisateurs authentifiés d’émettre des demandes de téléchargement simultanées et arbitraires pour créer des fichiers ZIP de ressources visibles qui peuvent surcharger le serveur et le réseau. Pour atténuer les risques d’attaques par déni de service, le composant OSGi `AssetDownloadServlet` est désactivé par défaut pour les instances de publication.

Pour permettre le téléchargement de fichiers depuis votre DAM (par exemple, lorsque vous utilisez un élément comme Asset Share Commons ou une autre implémentation de type portail), activez manuellement le servlet via une configuration OSGi. Adobe recommande de définir la taille de téléchargement autorisée sur la valeur la plus basse possible sans affecter les exigences de téléchargement au quotidien. Une valeur élevée peut avoir une incidence sur les performances.

1. Créez un dossier avec une convention d’affectation de nom qui cible le mode d’exécution de publication (`config.publish`) : `/apps/<your-app-name>/config.publish`. Pour définir les propriétés de configuration d&#39;un mode d&#39;exécution, voir [Modes d&#39;exécution](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).
1. Dans le dossier de configuration, créez un fichier de type `nt:file` nommé `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Remplissez `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` avec les éléments suivants. Définit une taille maximale (en octets) pour le téléchargement en tant que valeur de `asset.download.prezip.maxcontentsize`. L’exemple ci-dessous configure la taille maximale du téléchargement ZIP pour qu’il ne dépasse pas 100 Ko.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Désactivation du servlet de téléchargement de ressources {#disable-asset-download-servlet}

Le `Asset Download Servlet` peut être désactivé sur les instances de publication [!DNL Experience Manager] en mettant à jour la configuration du Dispatcher afin de bloquer toute demande de téléchargement de ressources. Le servlet peut également être désactivé manuellement par l’intermédiaire de la console OSGi.

1. Pour bloquer les demandes de téléchargement de ressources via une configuration de répartiteur, modifiez la configuration `dispatcher.any` et ajoutez une règle à la section [filtre](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#configuring-access-to-content-filter). `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Pour désactiver le composant OSGi sur une instance de publication, accédez à la console OSGi à l’adresse `http://[aem_server]:[port]/system/console/components`. Recherchez `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` et cliquez ensuite sur **[!UICONTROL Désactiver]**.

>[!MORELIKETHIS]
>
>* [Téléchargement de ressources protégées par DRM](drm.md).
>* [Téléchargement de ressources à l’aide de l’appli de bureau Experience Manager sur un poste de travail Windows ou Mac](https://helpx.adobe.com/fr/experience-manager/desktop-app/aem-desktop-app.html).
>* [Téléchargement de ressources à l’aide d’Adobe Assets Link depuis les applications Adobe Creative Cloud prises en charge](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html).

