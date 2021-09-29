---
title: Gérez des ressources composites et générez des sous-ressources.
description: Découvrez comment créer des références aux  [!DNL Experience Manager] ressources dans des fichiers InDesign, Adobe Illustrator et Photoshop. Découvrez également comment utiliser la fonction Visionneuse de page pour afficher des pages individuelles de fichiers de plusieurs pages.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '1377'
ht-degree: 31%

---

# Gestion des ressources composites avec des sous-ressources {#managing-compound-assets}

Adobe Experience Manager Assets peut déterminer si un fichier chargé contient des références à des ressources qui existent déjà dans le référentiel. Cette fonctionnalité est disponible uniquement pour les types de formats pris en charge. Si la ressource chargée contient des références aux ressources [!DNL Experience Manager], un lien bidirectionnel est créé entre les ressources chargées et référencées.

Outre l’élimination de la redondance, le référencement des ressources [!DNL Experience Manager] dans les applications Adobe Creative Cloud améliore la collaboration et accroît l’efficacité et la productivité des utilisateurs.

[!DNL Experience Manager] Assets prend en charge le référencement  **bidirectionnel**. Vous trouverez des ressources référencées dans la page des détails de la ressource du fichier chargé. En outre, vous pouvez afficher les fichiers de référencement des ressources [!DNL Experience Manager] dans la page des détails de la ressource référencée.

Les références sont résolues sur la base du chemin d’accès, du document et de l’ID d’instance des ressources référencées.

## Adobe Illustrator : Ajout de ressources en tant que références {#refai}

Vous pouvez référencer des ressources [!DNL Experience Manager] existantes dans un fichier Adobe Illustrator.

1. Utilisez l’[[!DNL Experience Manager] application de bureau ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr) pour monter le référentiel Assets en tant que lecteur sur votre ordinateur local. [!DNL Experience Manager] Dans le lecteur monté, accédez à l’emplacement de la ressource à référencer.
1. Faites glisser la ressource du volume monté jusqu’au fichier Illustrator.
1. Enregistrez le fichier Illustrator sur le lecteur monté ou [chargez-le](managing-assets-touch-ui.md#uploading-assets) dans le référentiel [!DNL Experience Manager]
1. Une fois le workflow terminé, accédez à la page des détails de la ressource. Les références aux ressources [!DNL Experience Manager] existantes sont répertoriées sous **[!UICONTROL Dépendances]** dans la colonne **[!UICONTROL Références]**.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Les ressources référencées qui apparaissent sous **[!UICONTROL Dépendances]** peuvent également être référencées par des fichiers autres que celui qui est actif. Pour afficher une liste des fichiers de référencement d’une ressource, cliquez sur son nom sous **[!UICONTROL Dépendances]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Dans la barre d’outils, cliquez sur l’icône **[!UICONTROL Afficher les propriétés]**. Dans la page des propriétés, la liste des fichiers qui référencent la ressource en cours est visible sous la colonne **[!UICONTROL Références]** dans l’onglet **[!UICONTROL De base]**.

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign : Ajout de ressources en tant que références {#add-aem-assets-as-references-in-adobe-indesign}

Pour référencer des ressources [!DNL Experience Manager] à partir d’un fichier d’InDesign, faites glisser les ressources [!DNL Experience Manager] vers le fichier d’InDesign ou exportez le fichier d’InDesign sous la forme d’un fichier ZIP.

Les ressources référencées existent déjà dans [!DNL Experience Manager] Assets. Vous pouvez extraire des sous-ressources en [configurant le serveur d’InDesign](indesign.md). Les ressources intégrées à un fichier InDesign sont extraites sous la forme de sous-ressources.

>[!NOTE]
>
>Si le serveur InDesign est soumis à un proxy, l’aperçu des fichiers InDesign est intégré à leurs métadonnées XMP. Dans ce cas, l’extraction de miniature n’est pas explicitement requise. Toutefois, si le serveur InDesign n’est pas soumis à un proxy, les miniatures doivent être explicitement extraites pour les fichiers InDesign.

Lorsqu’un fichier INDD est chargé, les références sont récupérées en interrogeant des ressources ayant des propriétés `xmpMM:InstanceID` et `xmpMM:DocumentID` dans le référentiel.

### Création de références en faisant glisser des ressources {#create-references-by-dragging-aem-assets}

Cette procédure est similaire à [Ajouter des ressources en tant que références dans Adobe Illustrator](#refai).

### Création de références aux ressources en exportant un fichier ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Suivez les étapes de la section [Création de modèles de processus](/help/sites-developing/workflows-models.md) pour créer un nouveau processus.
1. Utilisez la fonction [Package d’Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) pour exporter le document. Adobe InDesign peut exporter un document et les actifs liés sous la forme d’un package. Dans ce cas, le dossier exporté contient un dossier `Links` contenant des sous-ressources dans le fichier InDesign. Le dossier `Links` est présent dans le même dossier que le fichier INDD.
1. Créez un fichier ZIP et téléchargez-le dans le référentiel [!DNL Experience Manager].
1. Commencez le workflow de désarchivage.
1. Une fois le workflow terminé, les références contenues dans le dossier Liens sont automatiquement référencées en tant que sous-ressources. Pour afficher la liste des ressources référencées, accédez à la page des détails de la ressource InDesign et fermez le [rail](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop : Ajout de ressources en tant que références {#refps}

1. A l’aide d’un client WebDav, montez [!DNL Experience Manager] Ressources en tant que lecteur.
1. Pour créer des références aux ressources [!DNL Experience Manager] dans un fichier Photoshop, accédez aux ressources correspondantes dans le lecteur monté à l’aide de la fonctionnalité Placer les ressources liées dans Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Enregistrez le fichier Photoshop sur le lecteur monté ou [chargez ](managing-assets-touch-ui.md#uploading-assets) dans le référentiel [!DNL Experience Manager].
1. Une fois le workflow terminé, les références aux ressources [!DNL Experience Manager] existantes sont répertoriées dans la page des détails de la ressource.

   Pour afficher les ressources référencées, fermez le [rail](/help/sites-authoring/basic-handling.md#rail-selector) dans la page des détails de la ressource.

1. Les ressources référencées contiennent également la liste des ressources à partir desquelles elles sont référencées. Pour afficher la liste des ressources référencées, accédez à la page des détails de la ressource et fermez le [rail](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Les ressources contenues dans des ressources composites peuvent également être référencées par ID de document et ID d’instance. Cette fonctionnalité est disponible avec les versions d’Adobe Illustrator et d’Adobe Photoshop uniquement. Pour les autres, le référencement s’effectue sur la base du chemin d’accès relatif des ressources liées dans la ressource composite principale, comme dans les versions précédentes d’AEM.

## Création de sous-ressources {#generate-subassets}

Pour les ressources prises en charge avec des formats multi-pages (fichiers PDF, AI, Microsoft PowerPoint et Apple Keynote et fichiers Adobe InDesign), [!DNL Experience Manager] peut générer des sous-ressources qui correspondent à chaque page de la ressource d’origine. Ces sous-ressources sont liées à la ressource *parent* et facilitent l’affichage de plusieurs pages. Pour tous les autres usages, les sous-ressources sont traitées comme des ressources normales dans AEM.

La génération de sous-ressources est désactivée par défaut. Pour activer la génération de sous-ressources, procédez comme suit :

1. Connectez-vous à Experience Manager en tant qu’administrateur. Accédez à **[!UICONTROL Outils > Processus > Modèles]**.
1. Sélectionnez le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]** et cliquez sur **[!UICONTROL Modifier]**.
1. Cliquez sur **[!UICONTROL Activer/désactiver le panneau latéral]** et recherchez l’étape **[!UICONTROL Créer un sous-contenu]** . Ajoutez l’étape au workflow. Cliquez sur **[!UICONTROL Synchroniser]**.

Pour générer les sous-ressources, effectuez l’une des opérations suivantes :

* Nouvelles ressources : Le workflow [!UICONTROL Ressources de mise à jour de gestion des actifs numériques] s’exécute sur toute nouvelle ressource qui est chargée dans AEM. Les sous-ressources sont générées automatiquement pour les nouvelles ressources multi-pages.
* Ressources multi-pages existantes : Exécutez manuellement le workflow [!UICONTROL Ressources de mise à jour de gestion des actifs numériques] en procédant comme suit :

   * Sélectionnez une ressource et cliquez sur [!UICONTROL Chronologie] pour ouvrir le panneau de gauche. Vous pouvez également utiliser le raccourci clavier `alt + 3`. Cliquez sur [!UICONTROL Démarrer le processus], sélectionnez [!UICONTROL Ressources de mise à jour de gestion des actifs numériques], cliquez sur [!UICONTROL Démarrer], puis cliquez sur [!UICONTROL Continuer].
   * Sélectionnez une ressource et cliquez sur [!UICONTROL Créer > Workflow] dans la barre d’outils. Dans la boîte de dialogue contextuelle, sélectionnez le workflow [!UICONTROL Ressources de mise à jour de gestion des actifs numériques], cliquez sur [!UICONTROL Démarrer], puis sur [!UICONTROL Continuer].

Pour les documents Microsoft Word, exécutez le workflow **[!UICONTROL Documents Word d’analyse de gestion des actifs numériques]**. Il génère un composant `cq:Page` à partir du contenu du document Microsoft Word. Les images extraites du document sont référencées à partir du composant `cq:Page`. Elles sont extraites même si la génération des sous-ressources est désactivée.

## Affichage des sous-ressources {#viewing-subassets}

Les sous-ressources ne s’affichent que si elles sont générées et disponibles pour la ressource multi-page sélectionnée. Pour afficher les sous-ressources générées, ouvrez la ressource multi-page. Dans la zone supérieure gauche de la page, cliquez sur ![Icône du rail de gauche](assets/do-not-localize/aem_leftrail_contentonly.png) et cliquez sur **[!UICONTROL Sous-ressources]** dans la liste. Lorsque vous sélectionnez **[!UICONTROL Sous-ressources]** dans la liste. Vous pouvez également utiliser le raccourci clavier `alt + 5`.

![Affichage des sous-ressources pour une ressource multi-page](assets/view_subassets_simulation.gif)

## Affichage des pages d’un fichier multipage   {#view-pages-of-a-multi-page-file}

Vous pouvez afficher un fichier de plusieurs pages, tel que PDF, INDD, PPT, PPTX et AI, à l’aide de la fonction Visionneuse de page des ressources [!DNL Experience Manager]. Ouvrez une ressource de plusieurs pages et cliquez sur **[!UICONTROL Afficher les pages]** dans le coin supérieur gauche de la page. La Visionneuse de page qui s’ouvre affiche les pages de la ressource et les commandes permettant de parcourir et de zoomer sur chaque page.

![Affichage et affichage des pages d’une ressource multipage](assets/view_multipage_asset_fmr.gif)

S’agissant d’InDesign, vous pouvez extraire des pages à l’aide du serveur InDesign. Si les aperçus des pages sont enregistrés lors de la création du fichier InDesign, le serveur InDesign n’est pas nécessaire pour l’extraction des pages.

Les options suivantes sont disponibles dans la barre d’outils, dans le rail de gauche, ainsi que dans les commandes de la visionneuse de page :

* **[!UICONTROL Actions]** de bureau pour ouvrir ou afficher une sous-ressource spécifique à l’aide de l’appli de  [!DNL Experience Manager] bureau . Découvrez comment [configurer les actions de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr#desktopactions-v2) si vous utilisez l’appli de bureau [!DNL Experience Manager].

* **** L’option Propriétés ouvre la   page Propriétés de la sous-ressource spécifique.

* **** L’option Annotation vous permet d’annoter la sous-ressource spécifique. Les annotations que vous utilisez sur des sous-ressources distinctes sont collectées et affichées ensemble lorsque la ressource parent est ouverte pour affichage.

* **[!UICONTROL L’option]** Aperçu de page affiche toutes les sous-ressources simultanément.

* **** L’option Chronologie du rail de gauche après avoir cliqué sur l’ ![icône du rail de ](assets/do-not-localize/aem_leftrail_contentonly.png) gauche affiche le flux d’activité du fichier.

## Bonnes pratiques et limitation {#best-practice-limitation-tips}

* La génération de sous-ressources peut être très gourmande en ressources pour tout déploiement de Experience Manager. Si vous générez des sous-ressources lors du chargement de ressources complexes, ajoutez l’étape dans le workflow Ressources de mise à jour de gestion des actifs numériques . Si vous générez des sous-ressources à la demande, créez un workflow distinct pour générer des sous-ressources. Un workflow dédié vous permet d’ignorer les autres étapes du workflow Ressources de mise à jour de gestion des actifs numériques et d’enregistrer les ressources de calcul.

>[!MORELIKETHIS]
>
>* [Utilisation de l’appli de bureau Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr)

