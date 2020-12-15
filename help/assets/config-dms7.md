---
title: Configuration de Dynamic Media – mode Scene7
seo-title: Configuration de Dynamic Media – mode Scene7
description: Informations sur la manière de configurer Dynamic Media – mode Scene7.
seo-description: Informations sur la manière de configurer Dynamic Media – mode Scene7.
uuid: 81cc208b-e95d-4a01-9817-2b6d50cfe8b8
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: cd3adbac-9868-4838-9d8a-37dde8973df4
translation-type: tm+mt
source-git-commit: df92346ca23161b8eaff293a6b9f2c8b7c72e2ec
workflow-type: tm+mt
source-wordcount: '5571'
ht-degree: 72%

---


# Configuration de Dynamic Media – mode Scene7  {#configuring-dynamic-media-scene-mode}

Si Adobe Experience Manager est configuré dans des environnements différents, tels que le développement, l’évaluation et la production, vous devez configurer Dynamic Media Cloud Services pour chacun de ces environnements.

## Schéma d’architecture de Dynamic Media – mode Scene7 {#architecture-diagram-of-dynamic-media-scene-mode}

Le schéma d’architecture suivant décrit le fonctionnement de Dynamic Media – mode Scene7.

Avec la nouvelle architecture, AEM est responsable des fichiers originaux et des synchronisations avec Dynamic Media pour le traitement et la publication des ressources :

1. Lorsque le fichier original est transféré dans AEM, il est répliqué vers Dynamic Media. À ce stade, Dynamic Media gère l’intégralité du traitement des ressources et de la génération du rendu, comme le codage vidéo et les variantes dynamiques d’une image.
1. Une fois les rendus générés, AEM peut accéder de manière sécurisée aux rendus Dynamic Media distants et en afficher un aperçu (aucune donnée binaire n’est renvoyée à l’instance AEM).
1. Une fois que le contenu est prêt à être publié et approuvé, il déclenche l’envoi du contenu par le service Dynamic Media vers les serveurs de diffusion et la mise en cache du contenu sur le réseau de diffusion de contenu.

![chlimage_1](assets/chlimage_1.png)

## Activation de Dynamic Media en mode Scene7 {#enabling-dynamic-media-in-scene-mode}

[Par défaut, ce module complémentaire est désactivé. ](https://www.adobe.com/fr/marketing/experience-manager-assets/dynamic-media.html) Pour tirer parti des fonctionnalités de Dynamic Media, vous devez l’activer.

>[!NOTE]
>
>Dynamic Media - Le mode Scene7 est réservé à l’instance Auteur AEM. En tant que tel, vous devez configurer `runmode=dynamicmedia_scene7`sur l’instance d’auteur AEM et non sur l’instance de publication AEM.

Pour activer Dynamic Media, vous devez démarrer AEM à l&#39;aide du mode d&#39;exécution `dynamicmedia_scene7` à partir de la ligne de commande en saisissant ce qui suit dans une fenêtre de terminal (l&#39;exemple de port utilisé est 4502) :

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## (Facultatif) Migration des paramètres prédéfinis et des configurations Dynamic Media de 6.3 à 6.4 sans interruption {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Si vous effectuez une mise à niveau AEM Dynamic Media de 6.3 à 6.4 (qui inclut désormais la possibilité de déployer sans interruption), vous devez exécuter la commande curl suivante pour migrer tous vos paramètres prédéfinis et configurations de `/etc` à `/conf` dans le CRXDE Lite.

>[!NOTE]
>
>Si vous exécutez votre instance AEM en mode de compatibilité (c&#39;est-à-dire si le package de compatibilité est installé), vous n&#39;avez pas besoin d&#39;exécuter ces commandes.

Pour migrer vos paramètres prédéfinis et configurations personnalisés de `/etc` vers `/conf`, exécutez la commande d’URL Linux suivante :

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

Pour toutes les mises à niveau, avec ou sans le module de compatibilité, vous pouvez copier les paramètres prédéfinis de la visionneuse prête à l’emploi en exécutant la commande suivante :

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## (Facultatif) Installation de Feature Pack 18912 pour la migration des ressources en vrac {#installing-feature-pack}

Feature Pack 18912 vous permet soit d’assimiler des fichiers en vrac par FTP, soit de migrer des fichiers du mode Dynamic Media - Hybrid ou de Dynamic Media Classic vers le mode Dynamic Media - Scene7 sur AEM. Il est disponible depuis Adobe Professional Services.

Voir [Installation de Feature Pack 18912 pour la migration des ressources en vrac](bulk-ingest-migrate.md) pour plus d’informations.

## Configuration de Dynamic Media Cloud Services {#configuring-dynamic-media-cloud-services}

Modifiez le mot de passe avant de configurer les Cloud Services Dynamic Media. Après avoir reçu votre courrier électronique de mise en service avec les informations d’identification Dynamic Media, vous devez [vous connecter](https://www.adobe.com/fr/marketing-cloud/experience-manager/scene7-login.html) à Dynamic Media Classic pour modifier votre mot de passe. Le mot de passe fourni dans l’e-mail de mise en service est généré par le système et il est attribué uniquement de manière temporaire. Il est important que vous mettiez à jour le mot de passe afin que Dynamic Media Cloud Service soit configuré avec les informations d’identification correctes.

>[!NOTE]
>
>Par défaut, le chemin de configuration des Cloud Services est `/content/dam`. Tout autre chemin de configuration n&#39;est pas pris en charge par le mode Dynamic Media - Scene7.

Pour configurer les Cloud Services Dynamic Media :

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale et appuyez sur l’icône Outils, puis appuyez sur **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Sur la page Dynamic Media Configuration Browser, dans le volet de gauche, appuyez sur **[!UICONTROL global]** et sur **[!UICONTROL Créer]**. Ne touchez pas ou ne sélectionnez pas l’icône de dossier à gauche de [!UICONTROL global].
1. Sur la page [!UICONTROL Créer une configuration Dynamic Media], saisissez un titre, l’adresse email du compte Dynamic Media et un mot de passe, puis sélectionnez votre région. Ces informations vous sont fournies par Adobe dans l’e-mail de mise en service. Contactez l’assistance si vous n’avez pas reçu ce message.

   Appuyez sur **[!UICONTROL Se connecter à Dynamic Media]**.

   >[!NOTE]
   >
   >Une fois que vous avez reçu l’e-mail de mise en service avec les informations d’identification Dynamic Media, [connectez-vous](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) à Dynamic Media Classic pour modifier votre mot de passe. Le mot de passe fourni dans l’e-mail de mise en service est généré par le système et il est attribué uniquement de manière temporaire. Il est important que vous mettiez à jour le mot de passe afin que le service cloud Dynamic Media soit configuré avec les informations d’identification correctes.

1. Si la connexion est établie, vous pouvez également définir les éléments suivants :

   * **[!UICONTROL Société]** : nom du compte Dynamic Media. Il est possible que vous disposiez de plusieurs comptes Dynamic Media pour différentes sous-marques et divisions ou différents environnements d’évaluation/de production.
   * **[!UICONTROL Chemin d’accès au dossier racine de l’entreprise]**
   * **[!UICONTROL Publication des ressources]** : l’option **[!UICONTROL Immédiatement]** signifie que lorsque les ressources sont téléchargées, le système les assimile et fournit instantanément l’URL/le code intégré. Aucune intervention n’est nécessaire de la part de l’utilisateur pour publier des ressources. L’option **[!UICONTROL Lors de l’activation]** signifie que vous devez publier explicitement la ressource avant qu’un lien URL/code intégré ne soit fourni.
   * **[!UICONTROL Serveur d’aperçu sécurisé]** : permet de définir le chemin URL de votre serveur d’aperçu des rendus sécurisé. En d’autres termes, une fois les rendus générés, AEM peut accéder de manière sécurisée aux rendus Dynamic Media distants et en afficher un aperçu (aucune donnée binaire n’est renvoyée à l’instance AEM).

      À moins que vous ne disposiez d’un arrangement spécial pour utiliser votre propre serveur de société ou un serveur spécial, l’Adobe vous recommande d’utiliser le paramètre par défaut.
   >[!NOTE]
   >
   >Le contrôle de version n’est pas pris en charge dans DMS7. En outre, l’activation différée ne s’applique que si l’option **[!UICONTROL Publier des ressources]** dans la page de configuration de Dynamic Media est définie sur **[!UICONTROL Dès l’activation]**, puis uniquement jusqu’à la première activation de la ressource.
   >
   >Une fois qu’une ressource est activée, toutes les mises à jour sont immédiatement publiées en direct sur la livraison S7.

   ![dynamicmediaconfiguration2updated](assets/dynamicmediaconfiguration2updated.png)

1. Appuyez sur **[!UICONTROL Enregistrer]**.
1. Pour afficher l’aperçu du contenu Dynamic Media en toute sécurité avant qu’il ne soit modifié, vous aurez besoin de placer dans une liste autorisée l’instance d’auteur AEM à connecter à Dynamic Media :

   * Connectez-vous à votre compte Dynamic Media Classic : [https://www.adobe.com/fr/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html). Vos informations d’identification et de connexion vous ont été communiquées par Adobe au moment de la configuration. Si vous ne disposez pas de ces informations, contactez l’assistance technique.
   * Dans la barre de navigation située en haut à droite de la page, appuyez sur **[!UICONTROL Configuration > Configuration de l’application > Configuration de la publication > Image Server]**.
   * Sur la page Publication sur hébergeur d’images, dans la liste déroulante Contexte de publication, sélectionnez **[!UICONTROL Test de l’hébergeur d’images]**.
   * Pour l’option Filtre d’adresse client, appuyez sur **[!UICONTROL Ajouter]**.
   * Cochez la case permettant d’activer l’adresse, puis saisissez l’adresse IP de l’instance d’auteur AEM (et non l’IP du Dispatcher).
   * Appuyez sur **[!UICONTROL Save]** (Enregistrer).

Vous avez à présent terminé la configuration de base ; vous êtes prêt à utiliser le mode Scene7 de Dynamic Media.

Si vous souhaitez personnaliser davantage votre configuration, vous pouvez éventuellement effectuer l’une des tâches de la rubrique [(Facultatif) Configuration de paramètres avancés dans le mode Scene7 de Dynamic Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

## (Facultatif) Configuration de paramètres avancés dans le mode Scene7 de Dynamic Media {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Si vous souhaitez personnaliser davantage l’installation et la configuration du mode Scene7 de Dynamic Media, ou en optimiser les performances, vous pouvez effectuer une ou plusieurs des tâches facultatives suivantes :

* [(Facultatif) Installation et configuration des paramètres du mode Scene7 de Dynamic Media](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [(Facultatif) Optimisation des performances du mode Scene7 de Dynamic Media](#optional-tuning-the-performance-of-dynamic-media-scene-mode)
* [(Facultatif) Filtrage des ressources en vue de la réplication](#optional-filtering-assets-for-replication)

### (Facultatif) Installation et configuration des paramètres du mode Scene7 de Dynamic Media</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

Lorsque vous êtes en mode d’exécution **dynamicmedia_scene7**, vous utilisez l’interface utilisateur Dynamic Media Classic (Scene7) pour apporter des modifications à vos paramètres Dynamic Media.

Certaines des tâches ci-dessus nécessitent que vous vous connectiez à Dynamic Media Classic ici : [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

Les tâches de configuration et de configuration sont les suivantes :

* [Configuration de la publication pour Image Server](#publishing-setup-for-image-server)
* [Configuration des paramètres généraux de l’application](#configuring-application-general-settings)
* [Configuration de la gestion des couleurs](#configuring-color-management)
* [Modification des types MIME pour les formats pris en charge](#editing-mime-types-for-supported-formats)
* [Ajouter les types MIME pour les formats non pris en charge](#adding-mime-types-for-unsupported-formats)
* [Création de paramètres prédéfinis d’ensemble par lot pour générer automatiquement des visionneuses d’images et des visionneuses à 360°](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### Configuration de la publication pour Image Server  {#publishing-setup-for-image-server}

Les paramètres de configuration de la publication déterminent comment les ressources sont diffusées par défaut à partir de Dynamic Media. Si aucun paramètre n’est spécifié, Dynamic Media diffuse une ressource selon les paramètres par défaut définis dans Configuration de la publication. Par exemple, une requête de diffusion d’image qui ne comporte pas d’attribut de résolution produit une image avec le paramètre de résolution d’objet par défaut.

Pour configurer la configuration de la publication : dans Dynamic Media Classic, appuyez sur **[!UICONTROL Configuration > Configuration de l’application > Configuration de la publication > Image Server]**.

L’écran Image Server permet de définir les paramètres par défaut pour la diffusion des images. Consultez l’interface utilisateur pour obtenir une description de chaque paramètre.

* **[!UICONTROL Attributs de requête]** : ces paramètres imposent des limites aux images qui peuvent être diffusées à partir du serveur.
* **[!UICONTROL Attributs de requête par défaut]** : ces paramètres concernent l’aspect par défaut des images.
* **[!UICONTROL Attributs de miniature courants]** : ces paramètres concernent l’aspect par défaut des images miniatures.
* **[!UICONTROL Valeurs par défaut des champs de catalogue]** : ces paramètres concernent la résolution et le type de miniature par défaut des images.
* **[!UICONTROL Attributs de gestion des couleurs]** : ces paramètres déterminent les profils de couleurs ICC utilisés.
* **[!UICONTROL Attributs de compatibilité]** : ce paramètre permet aux paragraphes de début et de fin des calques de texte d’être traités tels qu’ils l’étaient dans la version 3.6, ce qui les rend rétrocompatibles.
* **[!UICONTROL Aide à la localisation]** : ces paramètres vous permettent de gérer divers attributs de paramètres régionaux. Ils vous permettent également de définir une chaîne de mappage de paramètres régionaux afin de définir les langues à prendre en charge pour les différentes info-bulles dans les visionneuses. Pour plus d’informations sur la configuration de la prise en charge de la localisation, voir [Considérations à prendre en compte lors de la configuration de la localisation des ressources](https://help.adobe.com/fr_FR/scene7/using/WS997f1dc4cb0179f034e07dc31412799d19a-8000.html).

#### Configuration des paramètres généraux de l’application {#configuring-application-general-settings}

Pour ouvrir la page [!UICONTROL Paramètres généraux de l’application], dans la barre de navigation globale de Dynamic Media Classic, appuyez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres généraux]**.

**[!UICONTROL Serveurs]** : au moment de la mise en service du compte, Dynamic Media fournit automatiquement les serveurs attribués à votre entreprise. Ces serveurs sont utilisés pour créer des chaînes URL pour votre site web et vos applications. Ces appels d’URL sont spécifiques à votre compte. Ne modifiez le nom d’aucun des serveurs à moins que le support AEM ne vous le demande explicitement.

**[!UICONTROL Écraser les images]** : Dynamic Media ne permet pas que deux fichiers portent le même nom. L’identifiant de l’URL de chaque élément (le nom de fichier sans l’extension) doit être unique. Ces options spécifient la manière dont les ressources de remplacement sont chargées : elles peuvent remplacer l’original ou devenir un doublon. Les ressources en double sont renommées en ajoutant « -1 » (par exemple, chaise.tif devient chaise-1.tif). Ces options affectent les ressources chargées dans un dossier autre que celui d’origine ou les ressources dont l’extension est différente de celle du fichier d’origine (telle que JPG, TIF ou PNG).

* **[!UICONTROL Écraser dans dossier actuel, même nom/même extension de fichier de base]** : cette option est la règle la plus stricte pour le remplacement. Elle implique que vous chargiez l’image de remplacement dans le même dossier que l’original, et qu’elle ait la même extension que le fichier d’origine. Si ces conditions ne sont pas remplies, un duplicata est créé.

>[!NOTE]
>
>Pour maintenir la cohérence avec AEM, sélectionnez **[!UICONTROL Remplacer dans le dossier actif, même nom/extension d’image de base]**.

* **[!UICONTROL Ecraser dans n’importe quel dossier, même nom/extension]**  de fichier de base : nécessite que l’image de remplacement ait la même extension que l’image d’origine (par exemple,  `chair.jpg` remplace  `chair.jpg` et non  `chair.tif`). Vous pouvez néanmoins télécharger l’image de remplacement dans un dossier différent de celui de l’image d’origine. L’image mise à jour se trouve dans le nouveau dossier ; le fichier d’origine n’est plus disponible à l’emplacement d’origine..
* **[!UICONTROL Écraser dans un dossier, même nom de fichier, extension indépendante]** : cette option est la règle de remplacement la plus inclusive. Elle vous permet de charger une image de remplacement dans un dossier autre que celui de l’image d’origine, de charger un fichier dont l’extension est différente de celle du fichier d’origine et de remplacer le fichier d’origine. Si le fichier d’origine se trouve dans un dossier différent, l’image de remplacement est enregistrée dans le nouveau dossier où elle a été chargée.

**[!UICONTROL Profils de couleurs par défaut]** : voir [Configuration de la gestion des couleurs](#configuring-color-management) pour plus d’informations.

>[!NOTE]
>
>Par défaut, le système affiche 15 rendus lorsque vous sélectionnez **[!UICONTROL Rendus]** et 15 paramètres prédéfinis de la visionneuse lorsque vous sélectionnez **[!UICONTROL Visionneuses]** dans la vue détaillée de la ressource. Vous pouvez augmenter cette limite. Voir [Augmentation du nombre de paramètres d’image prédéfinis qui s’affichent](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) ou [Augmentation du nombre de paramètres prédéfinis de visionneuse qui s’affichent](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### Configuration de la gestion des couleurs {#configuring-color-management}

La gestion des couleurs de Dynamic Media vous permet de corriger les couleurs des ressources. Avec la correction des couleurs, les ressources intégrées conservent leur espace colorimétrique (RVB, CMJN, gris) et leur profil de couleur intégré. Lorsque vous demandez un rendu dynamique, la couleur de l’image est corrigée dans l’espace colorimétrique cible en utilisant une sortie CMJN, RVB ou grise. Reportez-vous à la section [Configuration des paramètres d’image prédéfinis](managing-image-presets.md).

Pour configurer les propriétés de couleur par défaut afin d’activer la correction des couleurs lorsque vous demandez des images :

1. [Connectez-vous à Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) à l’aide des informations d’identification fournies lors de la mise en service. Accédez à **[!UICONTROL Configuration > Configuration de l’application]**.
1. Développez la zone **[!UICONTROL Configuration de la publication]** et sélectionnez **[!UICONTROL Image Server]**. Définissez **[!UICONTROL Contexte de publication]** sur **[!UICONTROL Imager Server]** lors de la définition des paramètres par défaut des instances de publication.
1. Faites défiler l’écran jusqu’à la propriété que vous devez modifier, par exemple, une propriété de la zone **[!UICONTROL Attributs de gestion des couleurs.]**

   Vous pouvez définir les propriétés de correction des couleurs suivantes :

   * [!UICONTROL Espace colorimétrique CMJN par défaut] : nom du profil de couleurs CMJN par défaut.
   * [!UICONTROL Espace colorimétrique de niveaux de gris par défaut] : nom du profil de niveaux de gris par défaut.
   * [!UICONTROL Espace colorimétrique RVB par défaut] : nom du profil de couleurs RVB par défaut.
   * [!UICONTROL Intention de rendu de conversion de couleurs] : indique l’intention de rendu. Les valeurs acceptables sont `perceptual`, `relative` `colometric`, `saturation` et `absolute colometric`. L’Adobe recommande `relative` comme valeur par défaut.

1. Appuyez sur **[!UICONTROL Save]** (Enregistrer).

Par exemple, vous pouvez définir l’**[!UICONTROL Espace colorimétrique par défaut RVB]** sur `sRGB` et **[!UICONTROL Espace colorimétrique par défaut CMJN]** sur `WebCoated`.

Cela aura les effets suivants :

* Active la correction des couleurs pour les images RVB et CMJN.
* Les images RVB qui n’ont pas de profil de couleur seront considérées comme se trouvant dans l’espace colorimétrique `sRGB`.
* Les images CMJN qui n’ont pas de profil colorimétrique seront considérées comme se trouvant dans l’espace colorimétrique `WebCoated`.
* Les rendus dynamiques qui renvoient une sortie RVB la renvoient dans l’espace colorimétrique `sRGB`.
* Les rendus dynamiques qui renvoient une sortie CMJN, la renverront dans l’espace colorimétrique `WebCoated`.

#### Modification des types MIME pour les formats pris en charge {#editing-mime-types-for-supported-formats}

Vous pouvez définir les types de ressources qui doivent être traités par Dynamic Media et personnaliser les paramètres de traitement des ressources avancé. Vous pouvez, par exemple, spécifier les paramètres de traitement des ressources de façon à ce qu’ils effectuent les opérations suivantes :

* Conversion d’un PDF Adobe en ressource de catalogue électronique.
* Conversion d’un document Adobe Photoshop (.psd) en ressource de modèle de bannière afin de permettre la personnalisation.
* Pixellisation d’un fichier Adobe Illustrator (.ai) ou d’un fichier PostScript encapsulé Adobe Photoshop (.eps).
* [Les ](/help/assets/video-profiles.md) profils vidéo et les  [profils ](/help/assets/image-profiles.md) d’imagerie peuvent être utilisés pour définir le traitement des vidéos et des images, respectivement.

Voir la section [Chargement des ressources](managing-assets-touch-ui.md#uploading-assets).

**Pour modifier les types MIME pour les formats pris en charge**

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale, puis appuyez sur l&#39;icône **[!UICONTROL Outils]** (marteau) et accédez à **[!UICONTROL Général > CRXDE Lite]**.
1. Dans le rail de gauche, accédez à ce qui suit :

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. Sous le dossier `mimeTypes`, sélectionnez un type MIME.
1. Sur le côté droit de la page CRXDE Lite, dans la partie inférieure :

   * Cliquez deux fois sur le champ **[!UICONTROL enabled]**. Par défaut, tous les types MIME des ressources sont activés (définis sur **[!UICONTROL true]**), ce qui signifie que les ressources seront synchronisées avec Dynamic Media pour le traitement. Si vous souhaitez exclure ce type MIME de ressource du traitement, définissez ce paramètre sur **[!UICONTROL false]**.
   * Cliquez deux fois sur **[!UICONTROL jobParam]** pour ouvrir le champ de texte associé. Voir [Types MIME pris en charge](assets-formats.md#supported-mime-types) pour connaître la liste des valeurs de paramètres de traitement que vous pouvez utiliser pour un type MIME donné.

1. Utilisez l’une des méthodes suivantes :

   * Répétez les étapes 3 et 4 pour modifier d’autres types MIME.
   * Dans la barre de menus de la page du CRXDE Lite, appuyez sur **[!UICONTROL Enregistrer tout]**.

1. Dans le coin supérieur gauche de la page, appuyez sur **[!UICONTROL CRXDE Lite]** pour revenir dans AEM.

#### Ajout de types MIME personnalisés pour les formats non pris en charge {#adding-custom-mime-types-for-unsupported-formats}

Vous pouvez ajouter des types MIME personnalisés pour les formats non pris en charge dans AEM Assets. Pour vous assurer que tout nouveau noeud ajouté dans le CRXDE Lite n’est pas supprimé par AEM, vous devez vous assurer que vous déplacez le type MIME avant **[!UICONTROL image_]** et que sa valeur activée est définie sur **[!UICONTROL false]**.

**Pour ajouter des types MIME personnalisés pour des formats non pris en charge**

1. Dans AEM, cliquez sur **[!UICONTROL Outils > Opérations > Console Web]**.

   ![webconsole](assets/2019-08-02_16-13-14.png)

1. Un nouvel onglet du navigateur s’ouvre sur la page **[!UICONTROL Adobe Experience Manager Web Console Configuration]** (Configuration de la console web Adobe Experience Manager).

   ![webconsole](assets/2019-08-02_16-17-29.png)

1. Sur la page, faites défiler l’écran jusqu’au nom **[!UICONTROL Adobe CQ Asset MIME type Service]**. À droite du nom, appuyez sur **[!UICONTROL Modifier les valeurs de configuration]** (icône représentant un crayon).

   ![edit](assets/2019-08-02_16-44-56.png)

1. Sur la page **[!UICONTROL Adobe CQ Asset MIME type Service]**, cliquez sur l’icône + `+`. Dans le tableau, l’emplacement du signe + sur lequel vous cliquez pour ajouter le nouveau type MIME n’est pas important.

   ![plousseur](assets/2019-08-02_16-27-27.png)

1. Entrez `DWG=image/vnd.dwg` dans le champ de texte vide que vous venez d’ajouter.

   Notez que l’exemple `DWG=image/vnd.dwg` est fourni à titre d’illustration uniquement. Le type MIME que vous ajoutez ici peut être tout autre format non pris en charge.

   ![dwg](assets/2019-08-02_16-36-36.png)

1. Dans le coin inférieur droit de la page, cliquez sur **[!UICONTROL Enregistrer]**.

   À ce stade, vous pouvez fermer l’onglet du navigateur dans lequel la page de configuration de la console web d’Adobe Experience Manager est ouverte.

1. Revenez à l’onglet du navigateur dans lequel votre console AEM est ouverte.

1. Dans AEM, cliquez sur **[!UICONTROL Outils > Général > CRXDE Lite]**.

   ![crxdelite](assets/2019-08-02_16-55-41.png)

1. Dans le rail de gauche, accédez à ce qui suit :

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Faites glisser le type MIME `image_vnd.dwg` et déposez-le directement au-dessus de `image_` dans l&#39;arborescence.

   ![glisser](assets/CRXDELite_CQDOC-14627.png)

1. Le type MIME `image_vnd.dwg` étant toujours sélectionné dans l’arborescence, dans l’onglet **[!UICONTROL Propriétés]**, dans la ligne **[!UICONTROL enabled]**, sous l’en-tête de colonne **[!UICONTROL Valeur]**, cliquez sur la valeur en doublon pour ouvrir la liste déroulante **[!UICONTROL Valeur]**.

1. Tapez `false` dans le champ (ou sélectionnez `false` dans la liste déroulante).

   ![fausevalue](assets/2019-08-02_16_60_30.png)

1. Dans le coin supérieur gauche de la page CRXDE Lite, cliquez sur **[!UICONTROL Enregistrer tout]**.

#### Création de paramètres prédéfinis d’ensemble par lot pour générer automatiquement des visionneuses d’images et des visionneuses à 360° {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

Utilisez les paramètres prédéfinis d’ensemble par lot pour automatiser la création de visionneuses d’images ou de jeux de rotation lorsque des ressources sont téléchargées sur Dynamic Media.

Tout d’abord, définissez les conventions de nommage pour la façon dont les ressources doivent être regroupées dans un ensemble. Vous pouvez ensuite créer un paramètre prédéfini d’ensemble par lot, qui est un ensemble d’instructions indépendant à nom unique, déterminant la création de la visionneuse à l’aide des images correspondant aux conventions de nommage définies dans la recette de paramètre prédéfini.

Lorsque vous téléchargez des fichiers, Dynamic Media crée automatiquement une visionneuse avec tous les fichiers qui correspondent à la convention de nommage définie dans les paramètres prédéfinis actifs.

**Configuration du nommage par défaut**

Créez une convention de nommage par défaut qui est utilisée dans n’importe quelle recette de paramètre prédéfini d’ensemble par lot. La convention de nommage par défaut sélectionnée dans la définition de paramètre prédéfini d’ensemble par lot peut être la seule convention dont votre entreprise a besoin pour générer des visionneuses par lot. Un paramètre prédéfini d’ensemble par lot est créé pour utiliser la convention de nommage par défaut que vous définissez. Vous pouvez créer autant de paramètres prédéfinis d’ensemble par lot que nécessaire avec des conventions de nommage différentes et personnalisées pour une visionneuse de contenu spécifique au cas où il existe une exception dans le nommage par défaut défini par l’entreprise.

Bien que la définition d’une convention de nommage par défaut ne soit pas nécessaire pour utiliser la fonctionnalité de paramètre prédéfini d’ensemble par lot, il est recommandé d’utiliser la convention de nommage par défaut pour définir autant d’éléments de votre convention de nommage que vous souhaitez regrouper dans une visionneuse afin de pouvoir rationaliser la création d’un ensemble par lot.

Vous pouvez également utiliser **[!UICONTROL Afficher le code]** sans champ de formulaire. Cet affichage vous permet de définir vos conventions de nommage en utilisant uniquement des expressions régulières.

Deux éléments sont disponibles pour la définition, **[!UICONTROL Correspondance]** et **[!UICONTROL Nom de base]**. Ces champs vous permettent de définir tous les éléments de la convention de nommage et d’identifier la partie de la convention utilisée pour nommer la visionneuse dans laquelle ils se trouvent. La convention de nommage individuelle d’une entreprise est susceptible d’utiliser une ou plusieurs lignes de définition pour chacun de ces éléments. Vous pouvez utiliser autant de lignes que vous le souhaitez pour votre définition unique et les regrouper dans des éléments distincts, par exemple, pour l’image principale, les éléments Couleur, Affichage secondaire et Échantillon.

**Pour configurer l’affectation de nom par défaut:**

1. Connectez-vous à votre compte Dynamic Media Classic (Scene7) : [www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Vos informations d’identification et de connexion vous ont été communiquées par Adobe au moment de la configuration. Si vous ne disposez pas de ces informations, contactez l’assistance technique.

1. Sur la barre de navigation située en haut de la page, appuyez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres prédéfinis d’ensemble par lot > Affectation de nom par défaut].**
1. Sélectionnez **[!UICONTROL Afficher le formulaire]** ou **[!UICONTROL Afficher le code]** pour indiquer le mode de visualisation et de saisie des informations sur chaque élément.

   Vous pouvez cocher la case **[!UICONTROL Afficher le code]** pour afficher la valeur d’expression régulière qui se crée à côté de vos sélections dans le formulaire. Vous pouvez saisir ou modifier ces valeurs pour définir les éléments de la convention de nommage si l’affichage sous forme de formulaire vous limite pour quelque raison que ce soit. Si vos valeurs ne peuvent pas être analysées dans l’affichage de formulaire, les champs de formulaire seront inactifs.

   >[!NOTE]
   >
   >Les champs de formulaire désactivés ne permettent pas de confirmer que vos expressions régulières sont correctes. Vous verrez les résultats de l’expression régulière que vous créez pour chaque élément après la ligne de résultat. L’expression régulière est visible en entier en bas de la page.

1. Développez chaque élément selon vos besoins et indiquez les conventions de nommage que vous souhaitez utiliser.
1. Si nécessaire, effectuez l’une des opérations suivantes :

   * Appuyez sur **[!UICONTROL Ajouter]** afin d’ajouter une autre convention d’affectation de nom pour un élément.
   * Appuyez sur **[!UICONTROL Supprimer]** afin de supprimer une convention d’affectation de nom pour un élément.

1. Utilisez l’une des méthodes suivantes :

   * Appuyez sur **[!UICONTROL Enregistrer sous]** et saisissez un nom pour le paramètre prédéfini.
   * Appuyez sur **[!UICONTROL Enregistrer]** si vous modifiez un paramètre prédéfini existant.

**Création d’un paramètre prédéfini d’ensemble par lot**

Dynamic Media utilise les paramètres prédéfinis d’ensemble par lot pour organiser les ressources en visionneuses d’images (images de remplacement, options de couleur, rotation à 360°) pour l’affichage dans des visionneuses. Les paramètres prédéfinis d’ensemble par lot s’exécutent automatiquement avec les processus de transfert des ressources dans Dynamic Media.

Vous pouvez créer, modifier et gérer vos paramètres prédéfinis d’ensemble par lot. Il existe deux formulaires de définitions de paramètres prédéfinis d’ensemble par lot : un pour une convention de nommage par défaut que vous pouvez avoir configurée, et un autre pour les conventions de nommage personnalisées que vous créez en cas de besoin.

Vous pouvez utiliser la méthode de champ de formulaire pour définir un paramètre prédéfini d’ensemble par lot ou la méthode de code, qui vous permet d’utiliser des expressions régulières. Comme dans l’affectation de nom par défaut, vous pouvez choisir [!UICONTROL Code de Vue] en même temps que vous définissez dans la [!UICONTROL Vue de formulaire] et utiliser des expressions régulières pour créer vos définitions. Vous pouvez également désélectionner l’une des deux vues pour utiliser uniquement l’une ou l’autre.

**Pour créer un paramètre prédéfini d’ensemble par lot:**

1. Connectez-vous à votre compte Dynamic Media Classic (Scene7) : [www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Vos informations d’identification et de connexion vous ont été communiquées par Adobe au moment de la configuration. Si vous ne disposez pas de ces informations, contactez l’assistance technique.

1. Dans la barre de navigation située en haut de la page, appuyez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres prédéfinis d’ensemble par lot > Paramètre prédéfini d’ensemble par lot].**

   Notez que l’option [!UICONTROL Afficher le formulaire], indiquée dans le coin supérieur droit de la page Détails, correspond à la vue par défaut.

1. Dans le panneau Liste des paramètres prédéfinis, appuyez sur **[!UICONTROL Ajouter]** pour activer les champs de définition dans le panneau Détails situé sur la droite de l’écran.****
1. Dans le panneau **[!UICONTROL Détails]**, dans le champ **[!UICONTROL Nom du paramètre prédéfini]**, saisissez le nom du paramètre prédéfini.
1. Dans le menu déroulant **[!UICONTROL Type d’ensemble par lot]**, sélectionnez un type de paramètre prédéfini.
1. Utilisez l’une des méthodes suivantes :

   * Si vous utilisez une convention d’affectation de nom par défaut que vous avez précédemment définie sous **[!UICONTROL Configuration de l’application > Paramètres prédéfinis d’ensemble par lot > Nom par défaut]**, développez **[!UICONTROL Conventions d’affectation de nom]******, puis dans la liste déroulante Affectation de nom de fichier, appuyez sur **[!UICONTROL Par défaut]**.
   * Pour définir une nouvelle convention d’affectation de nom lorsque vous configurez le paramètre prédéfini **[!UICONTROL Conventions d’affectation de nom]**, puis dans la liste déroulante **[!UICONTROL Affectation de nom de fichier]**, appuyez sur **[!UICONTROL Personnalisé]**.

1. Pour [!UICONTROL l’ordre de séquence], définissez l’ordre d’affichage des images après le regroupement de la visionneuse dans Dynamic Media.

   Par défaut, les ressources sont classées par ordre alphanumérique. Cependant, vous pouvez utiliser une liste d’expressions régulières séparées par des virgules pour définir l’ordre.

1. Pour **[!UICONTROL Définir la convention de création de nom]** et **[!UICONTROL la convention de création]**, indiquez le suffixe ou le préfixe du nom de base que vous avez défini dans la **[!UICONTROL convention de dénomination de fichier]**. En outre, définissez si la visionneuse sera créée dans la structure de dossiers de Dynamic Media.

   Si vous définissez un grand nombre de visionneuses, vous préférerez sans doute les conserver séparément des dossiers contenant les ressources elles-mêmes. Par exemple, vous pouvez créer un dossier Visionneuses d’images et y placer les visionneuses générées.

1. Dans le panneau **[!UICONTROL Détails]**, appuyez sur **[!UICONTROL Enregistrer]**.
1. Appuyez sur **[!UICONTROL Actif]** en regard du nom du nouveau paramètre prédéfini.

   L’activation du paramètre prédéfini garantit que, lorsque vous chargez des ressources vers Dynamic Media, le paramètre prédéfini d’ensemble par lot est appliqué pour générer la visionneuse.

**Création d’un paramètre prédéfini d’ensemble par lot pour la génération automatique d’une visionneuse à 360° en 2D**

Vous pouvez utiliser le type d’ensemble par lot **[!UICONTROL Visionneuse à 360° multi-axe]** pour créer une recette qui automatise la génération des visionneuses à 360° en 2D. Le regroupement des images utilise des expressions régulières de ligne et de colonne afin que les ressources d’image soient correctement alignées à l’emplacement correspondant dans le tableau multidimensionnel. Il n’existe aucune limite minimale ou maximale quant au nombre de lignes ou de colonnes nécessaires dans la visionneuse à 360° multi-axe.

Par exemple, supposons que vous souhaitiez créer une visionneuse à 360° multi-axe nommée `spin-2dspin`. Vous disposez d’un ensemble d’images de visionneuse à 360° qui contient trois lignes, avec 12 images par ligne. Les images sont nommées comme suit :

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

Avec ces informations, votre recette [!UICONTROL Type d&#39;ensemble par lot] peut être créée comme suit :

![chlimage_1-1](assets/chlimage_1-1.png)

Le regroupement de la partie du nom de ressource partagé de la visionneuse à 360° est ajouté au champ **[!UICONTROL Correspondance]** (éléments en surbrillance). La partie variable du nom de ressource contenant la ligne et la colonne est ajoutée respectivement aux champs **[!UICONTROL Ligne]** et **[!UICONTROL Colonne]**.

Lorsque la visionneuse à 360° est téléchargée et publiée, vous activez le nom de la recette de la visionneuse à 360° 2D répertoriée sous **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]** dans la boîte de dialogue **[!UICONTROL Télécharger les options de la tâche]**.

**Pour créer un paramètre prédéfini d’ensemble par lot pour la génération automatique d’une visionneuse à 360° en 2D:**

1. Connectez-vous à votre compte Dynamic Media Classic (Scene7) : [https://www.adobe.com/fr/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html).

   Vos informations d’identification et de connexion vous ont été communiquées par Adobe au moment de la configuration. Si vous ne disposez pas de ces informations, contactez l’assistance technique.

1. Dans la barre de navigation située en haut de la page, appuyez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres prédéfinis d’ensemble par lot > Paramètre prédéfini d’ensemble par lot]**.

   Notez que l’option [!UICONTROL Afficher le formulaire], indiquée dans le coin supérieur droit de la page Détails, correspond à la vue par défaut.

1. Dans le panneau **[!UICONTROL Liste prédéfinie]**, appuyez sur **[!UICONTROL Ajouter]** pour activer les champs de définition dans le panneau **[!UICONTROL Détails]** situé sur le côté droit de l’écran.
1. Dans le panneau **[!UICONTROL Détails]**, dans le champ [!UICONTROL Nom du paramètre prédéfini], saisissez le nom du paramètre prédéfini.
1. Dans le menu déroulant **[!UICONTROL Type d’ensemble par lot]**, sélectionnez **[!UICONTROL Visionneuse de fichiers]**.
1. Dans la liste déroulante **[!UICONTROL Sous-type]**, sélectionnez **[!UICONTROL Visionneuse à 360° multi-axe]**.
1. Développez **[!UICONTROL Conventions d’affectation de nom]**, puis dans la liste déroulante **[!UICONTROL Affectation de nom de fichier]**, appuyez sur **[!UICONTROL Personnalisé]**.
1. Utilisez les attributs **[!UICONTROL Correspondance]** et, éventuellement, **[!UICONTROL Nom de base]** pour définir une expression régulière pour nommer les fichiers d’image qui constituent le regroupement.

   Par exemple, votre expression régulière de correspondance littérale peut se présenter comme suit :

   `(w+)-w+-w+`

1. Développez **[!UICONTROL Position des colonnes/lignes]**, puis définissez le format de nom de la position de la ressource image dans le tableau de la visionneuse à 360° en 2D.

   Placez la position de ligne ou de colonne entre parenthèses dans le nom de fichier.

   Par exemple, l’expression régulière de ligne peut se présenter comme suit :

   `\w+-R([0-9]+)-\w+`

   ou

   `\w+-(\d+)-\w+`

   L’expression régulière de colonne peut se présenter comme suit :

   `\w+-\w+-C([0-9]+)`

   ou

   `\w+-\w+-C(\d+)`

   N’oubliez pas qu’il s’agit uniquement d’exemples. Vous pouvez créer votre expression régulière comme bon vous semble, en fonction de vos besoins.

   >[!NOTE]
   >
   >Si la combinaison des expressions régulières de ligne et de colonne ne permet pas de déterminer la position de la ressource dans le tableau de la visionneuse à 360° multidimensionnelle, cette ressource n’est pas ajoutée à la visionneuse, et une erreur est enregistrée.

1. Pour **[!UICONTROL Définir la convention de création de nom]** et **[!UICONTROL la convention de création]**, indiquez le suffixe ou le préfixe du nom de base que vous avez défini dans la **[!UICONTROL convention de dénomination de fichier]**.

   Vous pouvez également définir l’emplacement où la visionneuse à 360° sera créée dans la structure de dossiers de Dynamic Media Classic.

   Si vous définissez un grand nombre de visionneuses, vous préférerez sans doute les conserver séparément des dossiers contenant les ressources elles-mêmes. Par exemple, créez un dossier Visionneuses à 360° pour y placer les visionneuses générées.

1. Dans le panneau **[!UICONTROL Détails]**, appuyez sur **[!UICONTROL Enregistrer]**.
1. Appuyez sur **[!UICONTROL Actif]** en regard du nom du nouveau paramètre prédéfini.

   L’activation du paramètre prédéfini garantit que, lorsque vous chargez des ressources vers Dynamic Media, le paramètre prédéfini d’ensemble par lot est appliqué pour générer la visionneuse.

### (Facultatif) Optimisation des performances du mode Scene7 de Dynamic Media  {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Pour que le mode Dynamic Media - Scene7 fonctionne correctement, l’Adobe recommande les conseils de réglage précis des performances et de l’évolutivité de la synchronisation suivants :

* Mise à jour des paramètres de tâche prédéfinis pour le traitement de différents formats de fichier.
* Mise à jour des threads de traitement de file d’attente de workflows Granite prédéfinis (ressources vidéo).
* Mise à jour des threads de traitement de file d’attente de workflows Granite prédéfinis (images et ressources non vidéo).
* Mise à jour du nombre maximal de connexions de chargement au serveur Dynamic Media Classic.

#### Mise à jour des paramètres de tâche prédéfinis pour le traitement de différents formats de fichier

Vous pouvez régler les paramètres de tâche pour accélérer le traitement des fichiers lors du chargement. Par exemple, si vous téléchargez des fichiers PSD, mais que vous ne souhaitez pas les traiter en tant que modèles, vous pouvez définir l’extraction du calque sur false (désactivé). Dans ce cas, le paramètre de tâche affiné apparaîtra sous la forme `process=None&createTemplate=false`.

Adobe recommande d’utiliser les paramètres de tâche « affiné » suivants pour les fichiers PDF, Postscript et PSD :

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| Type de fichier | Paramètres de tâche recommandés |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| Postscript | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

Pour mettre à jour l’un de ces paramètres, procédez comme indiqué dans la [Activation de la prise en charge du paramètre de tâche de chargement Assets/Dynamic Media Classic basé sur le type MIME](#enabling-mime-type-based-assets-scene-upload-job-parameter-support).

#### Mise à jour de la file d’attente de workflows transitoires Granite {#updating-the-granite-transient-workflow-queue}

La file d’attente de workflows Granite est utilisée pour le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**. Dans Dynamic Media, elle est utilisée pour l’intégration et le traitement des images.

**Pour mettre à jour la file d’attente de workflows transitoires Granite**

1. Accédez à [https://&lt;serveur>/system/console/configMgr](http://localhost:4502/system/console/configMgr) et recherchez **[!UICONTROL Queue: Granite Transient Workflow Queue]** (File d’attente : file d’attente de workflows transitoires Granite).

   >[!NOTE]
   >
   >Il est nécessaire d’effectuer une recherche par texte au lieu d’utiliser une URL directe, car le PID OSGi est généré dynamiquement.

1. Dans le champ **[!UICONTROL Maximum Parallel Jobs]** (Nombre maximal de tâches en parallèle), modifiez le nombre en fonction de la valeur souhaitée.

   Vous pouvez augmenter **[!UICONTROL le nombre maximal de tâches parallèles]** afin de prendre en charge le chargement intensif de fichiers vers Dynamic Media. La valeur exacte dépend de la capacité matérielle. Dans certains cas, c’est-à-dire lors d’une migration initiale ou d’un transfert en vrac unique, vous pouvez utiliser une valeur importante. Sachez toutefois que l’utilisation d’une valeur élevée (par exemple deux fois le nombre de coeurs) peut avoir des effets négatifs sur d’autres activités simultanées. Vous devez donc tester et ajuster la valeur en fonction de votre cas d’utilisation particulier.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Appuyez sur **[!UICONTROL Save]** (Enregistrer).

#### Mise à jour de la file d’attente de workflows Granite {#updating-the-granite-workflow-queue}

La file d’attente de workflows Granite est utilisée pour les workflows non transitoires. Dans Dynamic Media, elle est utilisée pour le traitement de la vidéo avec le workflow **[!UICONTROL Vidéo de codage Dynamic Media]**.

**Pour mettre à jour la file d’attente de workflows Granite:**

1. Accédez à `https://<server>/system/console/configMgr` et recherchez **[!UICONTROL Queue: Granite Workflow Queue]** (File d’attente : file d’attente de workflows Granite).

   >[!NOTE]
   >
   >Il est nécessaire d’effectuer une recherche par texte au lieu d’utiliser une URL directe, car le PID OSGi est généré dynamiquement.

1. Dans le champ **[!UICONTROL Maximum Parallel Jobs]** (Nombre maximal de tâches en parallèle), modifiez le nombre en fonction de la valeur souhaitée.

   Par défaut, le nombre maximal de tâches en parallèle dépend du nombre de cœurs de processeur disponibles. Par exemple, sur un serveur à 4 cœurs, 2 threads de traitement sont attribués. (Une valeur comprise entre 0,0 et 1,0 est basée sur un ratio, ou tout nombre supérieur à 1 attribuera le nombre de threads de traitement.)

   Dans la plupart des cas d’utilisation, le paramètre par défaut de 0,5 est suffisant.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Appuyez sur **[!UICONTROL Save]** (Enregistrer).

#### Mise à jour de la connexion de chargement vers Scene7 {#updating-the-scene-upload-connection}

Le paramètre de connexion de chargement vers Scene7 synchronise les ressources AEM avec les serveurs Dynamic Media Classic.

**Pour mettre à jour la connexion de chargement vers Scene7:**

1. Accédez à `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`.
1. Dans le champ [!UICONTROL Number of connections] (Nombre de connexions) et/ou [!UICONTROL Active job timeout] (Délai d’expiration des tâches actives), modifiez le nombre en fonction de vos besoins.

   Le paramètre **[!UICONTROL Number of connections]** contrôle le nombre maximal de connexions HTTP autorisées pour le chargement d’AEM vers Dynamic Media. En règle générale, la valeur prédéfinie de 10 connexions est suffisante.

   Le paramètre **[!UICONTROL Active job timeout]** détermine le temps d’attente avant que les ressources Dynamic Media chargées ne soient publiées sur le serveur de diffusion. Cette valeur est de 2 100 secondes ou 35 minutes, par défaut.

   Dans la plupart des cas d’utilisation, le paramètre de 2 100 est suffisant.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Appuyez sur **[!UICONTROL Enregistrer]**.

### (Facultatif) Filtrage des ressources en vue de la réplication {#optional-filtering-assets-for-replication}

Dans les déploiements non Dynamic Media, vous dupliquez *tous les fichiers (images et vidéos) de votre environnement d’auteur AEM au noeud de publication AEM. Ce processus est nécessaire car les serveurs de publication AEM diffusent également les ressources.

Cependant, dans les déploiements Dynamic Media, dans la mesure où les ressources sont distribuées par le biais du service cloud, il n’est pas nécessaire de répliquer ces mêmes ressources sur AEM noeuds de publication. Un tel processus de &quot;publication hybride&quot; permet d’éviter des coûts d’enregistrement supplémentaires et des délais de traitement plus longs pour la réplication des ressources. Les autres contenus, tels que les pages de site, continuent à être diffusés à partir des nœuds de publication AEM.

Les filtres vous permettent d’*empêcher* que les ressources ne soient répliquées vers le nœud de publication AEM.

#### Utilisation des filtres de ressources par défaut pour la réplication {#using-default-asset-filters-for-replication}

Si vous utilisez Dynamic Media pour l’imagerie et/ou la vidéo, vous pouvez utiliser les filtres par défaut que nous fournissons en l’état. Les filtres suivants sont activés par défaut :

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Filtrer</strong></td> 
   <td><strong>Type de MIME</strong></td> 
   <td><strong>Rendus</strong></td> 
  </tr> 
  <tr> 
   <td>Dynamic Media Image Diffusion</td> 
   <td><p>filter-images</p> <p>ensembles de filtres</p> <p> </p> </td> 
   <td><p>Débuts avec <strong>image/</strong></p> <p>Contient <strong>application/</strong> et se termine par <strong>set</strong>.</p> </td> 
   <td>Les "images-filtres" prêtes à l’emploi (s’appliquent aux fichiers d’images uniques, y compris aux images interactives) et les "visionneuses de filtres" (s’appliquent aux visionneuses à 360°, aux visionneuses d’images, aux visionneuses de supports variés et aux visionneuses de carrousel) : 
    <ul> 
     <li>Suppriment de la réplication l’image d’origine et les rendus d’image statiques.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>diffusion vidéo Dynamic Media</td> 
   <td>filter-video</td> 
   <td>Débuts avec <strong>video/</strong></td> 
   <td>La "vidéo-filtre" prête à l'emploi permet de : 
    <ul> 
     <li>Exclure de la réplication les rendus vidéo et miniatures statiques d'origine.<br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Les filtres s’appliquent aux types MIME et ne peuvent pas être spécifiques à un chemin.

#### Personnalisation des filtres de ressources en vue de la réplication  {#customizing-asset-filters-for-replication}

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale et appuyez sur l&#39;icône **[!UICONTROL Outils]** et accédez à **[!UICONTROL Général > CRXDE Lite]**.
1. Dans l&#39;arborescence de dossiers de gauche, accédez à `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` pour consulter les filtres.

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. Pour définir le type MIME du filtre, vous pouvez localiser le type MIME comme suit : 

   Dans le rail de gauche, développez **[!UICONTROL content > dam > &quot;a1/> > jcr:content > metadata]**, puis dans le tableau, recherchez **[!UICONTROL dc:format]**.`locate_your_asset`

   L’illustration ci-dessous est un exemple de chemin d’une ressource vers dc:format.

   ![chlimage_1-3](assets/chlimage_1-3.png)

   Notez que `dc:format` pour l&#39;actif `Fiji Red.jpg` est `image/jpeg`.

   Pour que ce filtre s’applique à toutes les images, quel que soit leur format, définissez la valeur sur `image/*` où `*` est une expression régulière appliquée à toutes les images de n’importe quel format.

   Pour que le filtre s’applique uniquement aux images de type JPEG, entrez la valeur `image/jpeg`.

1. Définissez les rendus que vous souhaitez inclure ou exclure de la réplication.

   Voici des exemples de caractères que vous pouvez utiliser afin de filtrer la réplication :

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Caractère à utiliser</strong></td> 
    <td><strong>Filtres des ressources pour la réplication</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>Caractère générique<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>Inclut des ressources pour la réplication.</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>Exclut les actifs de la réplication.</td> 
    </tr> 
    </tbody> 
   </table>

   Accédez à **content/dam/&quot;a1/&quot;/jcr:content/renditions**.`locate your asset`

   L’illustration ci-dessous est un exemple de rendu d’une ressource.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Si vous souhaitez uniquement répliquer l’original, vous devez saisir `+original`.

