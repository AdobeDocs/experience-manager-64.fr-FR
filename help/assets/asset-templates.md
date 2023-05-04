---
title: Modèles de ressources
description: En savoir plus sur les modèles de ressources dans [!DNL Experience Manager] Ressources et utilisation des modèles de ressources pour créer des documents marketing.
uuid: 7ba87c1d-70cd-4b89-86f3-971b93885f1e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 340b62f7-2405-4d2d-846d-2c444d6cc77b
feature: Asset Management,Developer Tools
role: User
exl-id: 9b4f16e6-dd91-4179-9629-576d801fcf43
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1610'
ht-degree: 30%

---

# Modèles de ressources {#asset-templates}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les modèles de ressources correspondent à une catégorie spéciale de ressources qui permet de réutiliser rapidement des contenus riches pour les médias papier et numériques. Un modèle de ressource comprend deux parties : une section de message fixe et une section modifiable.

La section fixe peut comprendre du contenu propriétaire, comme le logo d’une marque ou des informations sur les droits d’auteur, pour lequel la modification n’est pas activée. La section modifiable peut contenir du contenu visuel et textuel dans des champs qui peuvent être modifiés afin de personnaliser le message.

La possibilité d’apporter des modifications limitées tout en sécurisant les signaux globaux rend les modèles de ressources des blocs de création idéaux pour une adaptation et une distribution rapides du contenu en tant qu’artefacts de contenu pour diverses fonctions. La réutilisation de contenu permet de réduire le coût de gestion des canaux papier et numériques et de proposer des expériences globales et cohérentes sur ces canaux.

En tant que marketeur, vous pouvez stocker et gérer des modèles dans [!DNL Experience Manager] Ressources et utiliser un seul modèle de base pour créer facilement plusieurs expériences d’impression personnalisées. Vous pouvez créer différents types de dérivés marketing, par exemple, des brochures, des prospectus, des cartes postales, des cartes de visite, etc. pour transmettre de façon claire votre message marketing à vos clients. Vous pouvez également assembler des documents papier comportant plusieurs pages à partir de documents papier nouveaux ou existants. Par-dessus tout, vous pouvez diffuser facilement des expériences digitales et papier simultanément afin de fournir une expérience cohérente et intégrée aux utilisateurs.

Bien que les modèles de ressources soient principalement des fichiers d’InDesign, la maîtrise de l’InDesign n’est pas un obstacle à la création d’artefacts stellaires. Vous n’avez pas besoin de mapper les champs de votre modèle d’InDesign avec vos champs de produit que vous avez normalement besoin de faire lors de la création de catalogues. Vous pouvez modifier les modèles en mode WYSIWYG directement depuis l’interface Web. Toutefois, pour que l’InDesign traite vos modifications, vous devez d’abord configurer [!DNL Experience Manager] Ressources à intégrer au serveur InDesign.

La possibilité de modifier des modèles d’InDesign à partir de l’interface web favorise une plus grande collaboration entre le personnel créatif et marketing, tout en réduisant le temps de mise sur le marché des initiatives de promotion locales.

Vous pouvez effectuer les opérations suivantes avec les modèles de ressources :

* Modification des champs de modèle modifiables à partir de l’interface web
* Contrôlez le style de base du texte, par exemple la taille de police, le style et le type au niveau de la balise.
* Modifier des images dans le modèle à l’aide du sélecteur de contenu
* Aperçu des modifications de modèle
* Fusionner plusieurs fichiers de modèle pour créer un artefact multi-page

Lorsque vous choisissez un modèle pour vos dérivés, [!DNL Assets] crée une copie du modèle qui peut être modifiée. Le modèle original est préservé, ce qui garantit que votre signalétique reste intacte et peut être réutilisée pour renforcer la cohérence de la marque.

Vous pouvez exporter le fichier mis à jour dans le dossier parent aux formats suivants :

* INDD
* PDF
* JPG

Vous pouvez également télécharger la sortie dans ces formats sur votre système local.

## Création d’un document {#creating-a-collateral}

Supposons que vous souhaitiez créer des documents numériques imprimables, tels que des brochures, prospectus et publicités, pour une campagne à venir et les partager avec les magasins de vente à l’échelle mondiale. La création de documents reposant sur un modèle permet d’offrir une expérience client unifiée sur plusieurs canaux. Les concepteurs peuvent créer les modèles de campagne (une ou plusieurs pages) à l’aide d’une solution créative, telle que l’InDesign et le chargement des modèles vers [!DNL Assets] pour vous. Avant de créer un document, vous devez avoir préalablement chargé un ou plusieurs modèles INDD et les mettre à disposition en Experience Manager.

1. Cliquez sur le bouton [!DNL Experience Manager] logo, puis cliquez sur **[!UICONTROL Ressources]** sur la page Navigation .
1. Dans les options, choisissez **[!UICONTROL Modèles]**.

   ![chlimage_1-306](assets/chlimage_1-306.png)

1. Cliquez/appuyez sur **[!UICONTROL Créer]**, puis sélectionnez le document à créer dans le menu . Par exemple, choisissez **[!UICONTROL Brochure]**.

   ![chlimage_1-307](assets/chlimage_1-307.png)

1. Demandez qu’un ou plusieurs modèles INDD soient chargés et disponibles en Experience Manager à l’avance. Sélectionnez un modèle pour votre brochure, puis cliquez/appuyez sur **[!UICONTROL Suivant]**.

   ![chlimage_1-308](assets/chlimage_1-308.png)

1. Entrez un nom et éventuellement une description pour la brochure.

   ![chlimage_1-309](assets/chlimage_1-309.png)

1. (Facultatif) Cliquez/appuyez sur le bouton **[!UICONTROL Balises]** en regard de **[!UICONTROL Balises]** puis sélectionnez une ou plusieurs balises pour la brochure. Cliquez/appuyez sur **[!UICONTROL Confirmer]** pour confirmer votre sélection.

   ![chlimage_1-310](assets/chlimage_1-310.png)

1. Cliquez sur **[!UICONTROL Créer]**. Une boîte de dialogue confirme la création d’une brochure. Cliquez/appuyez sur **[!UICONTROL Ouvrir]** pour ouvrir la brochure en mode d’édition.

   ![chlimage_1-311](assets/chlimage_1-311.png)

   Vous pouvez également fermer la boîte de dialogue et accéder au dossier dans la page Modèles à laquelle vous avez commencé pour afficher la brochure que vous avez créée. Le type de document apparaît sur sa miniature en mode Carte. Par exemple, dans ce cas, Brochure s’affiche sur la miniature.

   ![chlimage_1-312](assets/chlimage_1-312.png)

## Modification d’un document {#editing-a-collateral}

Vous pouvez modifier un dérivé immédiatement après sa création. Vous pouvez aussi choisir de l’ouvrir depuis la page Modèles ou la page des détails du fichier.

1. Pour ouvrir un dérivé pour le modifier, procédez de l’une des façons suivantes :

   * Ouvrez le document (brochure dans ce cas) que vous avez créé à l’étape 7 de la [Création d’un document](asset-templates.md#creating-a-collateral).
   * Sur la page Modèles , accédez au dossier dans lequel vous avez créé le document, puis cliquez/appuyez sur l’action rapide Modifier de la miniature d’un document.
   * Dans la page Ressource du document, cliquez/appuyez sur l’icône Modifier de la barre d’outils.
   * Sélectionnez le document, puis cliquez/appuyez sur l’icône Modifier de la barre d’outils.

   ![chlimage_1-313](assets/chlimage_1-313.png)

   L’outil de recherche de ressources et l’éditeur de texte sont affichés à gauche de la page. L’éditeur de texte s’ouvre par défaut.

   Vous pouvez utiliser l’éditeur de texte pour modifier le texte que vous souhaitez afficher dans le champ de texte. Vous pouvez modifier la taille, le style, la couleur et le type de la police au niveau de la balise.

   À l’aide de l’outil de recherche de ressources, vous pouvez rechercher des images dans [!DNL Assets] et remplacer les images modifiables du modèle par d’autres que vous aurez choisies.

   ![chlimage_1-314](assets/chlimage_1-314.png)

   Les champs modifiables sont affichés à droite. Pour qu’un champ soit modifiable dans [!DNL Assets], le champ correspondant dans le modèle doit être balisé dans InDesign. En d’autres termes, elles doivent être rendues modifiables dans InDesign.

   ![chlimage_1-315](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >Assurez-vous que la variable [!DNL Experience Manager] est intégrée à un serveur InDesign pour permettre [!DNL Assets] pour extraire les données du modèle d’InDesign et les rendre disponibles pour modification. Pour plus d’informations, voir [Intégration [!DNL Assets] avec InDesign Server](indesign.md).

1. Pour modifier le texte d’un champ modifiable, cliquez/appuyez sur le champ de texte dans la liste des champs modifiables et modifiez le texte dans le champ.

   ![chlimage_1-316](assets/chlimage_1-316.png)

   Vous pouvez modifier les propriétés du texte, par exemple le style, la couleur et la taille de la police à l’aide des options fournies.

1. Cliquez/appuyez sur **[!UICONTROL Aperçu]** pour prévisualiser les modifications de texte.

   ![chlimage_1-317](assets/chlimage_1-317.png)

1. Pour permuter une image, cliquez/appuyez sur le bouton **[!UICONTROL Outil de recherche de ressources]** icône .

   ![chlimage_1-318](assets/chlimage_1-318.png)

1. Sélectionnez le champ d’image dans la liste des champs modifiables, puis faites glisser l’image souhaitée du sélecteur de ressource vers le champ modifiable.

   ![chlimage_1-319](assets/chlimage_1-319.png)

   Vous pouvez également rechercher des images à l’aide de mots-clés, de balises ou selon leur statut de publication. Vous pouvez parcourir le référentiel d’[!DNL Assets] et accéder à l’emplacement de l’image souhaitée.

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. Cliquez/appuyez sur **[!UICONTROL Aperçu]** pour prévisualiser l’image.

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. Pour modifier une page spécifique dans un document multipage, utilisez le navigateur de page en bas de la page.

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. Cliquez/appuyez sur **[!UICONTROL Aperçu]** sur la barre d’outils pour prévisualiser toutes les modifications. Cliquez/appuyez sur **[!UICONTROL Terminé]** pour enregistrer les modifications apportées au document.

   >[!NOTE]
   >
   >Les icônes Aperçu et Terminé sont activées uniquement lorsque les champs d’image modifiables dans le document ne comportent aucune icône manquante. S’il manque des icônes dans votre document, c’est parce que [!DNL Experience Manager] ne parvient pas à résoudre les images dans le modèle d’InDesign. Généralement, [!DNL Experience Manager] ne peut pas résoudre les images dans les cas suivants :
   >
   >* Les images ne sont pas incorporées dans le modèle d’InDesign sous-jacent.
   >* Les images ne sont pas liées depuis le système de fichiers local

   >
   >Pour permettre à [!DNL Experience Manager] de résoudre les images, procédez de la façon suivante :
   >
   >* Incorporer des images lors de la création de modèles d’InDesign (voir [A propos des liens et des graphiques incorporés](https://helpx.adobe.com/fr/indesign/using/graphics-links.html)).
   >* Mont [!DNL Experience Manager] à votre système de fichiers local, puis mappez les icônes manquantes avec les [!DNL Experience Manager] ressources.

   >
   >Pour plus d’informations sur l’utilisation des documents InDesign, voir [Bonnes pratiques relatives à l’utilisation de documents d’InDesign dans [!DNL Experience Manager]](https://helpx.adobe.com/fr/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Pour générer un rendu PDF pour la brochure, sélectionnez l’option Acrobat dans la boîte de dialogue, puis cliquez sur **[!UICONTROL Continuer]**.
1. Le document est créé dans le dossier avec lequel vous avez commencé. Pour afficher les rendus, ouvrez le document et choisissez **[!UICONTROL Rendus]** dans la liste de navigation globale.

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. Cliquez/appuyez sur le rendu du PDF dans la liste des rendus pour télécharger le fichier du PDF. Ouvrez le fichier PDF pour réviser le dérivé.

   ![chlimage_1-324](assets/chlimage_1-324.png)

## Fusionner les documents collatéraux {#merge-collateral}


1. Cliquez ou appuyez sur **[!UICONTROL Outils > Ressources]**.
1. Dans les options, choisissez **[!UICONTROL Modèles]**.
1. Cliquez/appuyez sur **[!UICONTROL Créer]** et choisissez **[!UICONTROL Fusion]** dans le menu.

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Sur la page Fusion de modèles , cliquez/appuyez sur l’icône Fusion .

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. Accédez à l’emplacement des documents que vous souhaitez fusionner, cliquez/appuyez sur les miniatures des documents que vous souhaitez fusionner pour les sélectionner.

   ![chlimage_1-327](assets/chlimage_1-327.png)

   Vous pouvez même rechercher des modèles à partir de la zone Omni-recherche.

   ![chlimage_1-328](assets/chlimage_1-328.png)

   Vous pouvez parcourir le référentiel ou les collections d’[!DNL Assets], puis accéder à l’emplacement des modèles souhaités et les sélectionner pour les fusionner.

   ![chlimage_1-329](assets/chlimage_1-329.png)

   Vous pouvez appliquer différents filtres pour rechercher les modèles souhaités. Par exemple, vous pouvez rechercher des modèles en fonction du type de fichier ou des balises.

   ![chlimage_1-330](assets/chlimage_1-330.png)

1. Cliquez/appuyez sur **[!UICONTROL Suivant]** dans la barre d’outils.
1. Dans l’écran **[!UICONTROL Aperçu et réorganisation]**, réorganisez les modèles si nécessaire et prévisualisez la sélection de modèles à fusionner. Ensuite, cliquez/appuyez sur **[!UICONTROL Suivant]** dans la barre d’outils.

   ![chlimage_1-331](assets/chlimage_1-331.png)

1. Dans l’écran Configurer le modèle, entrez un nom pour le dérivé. Vous pouvez également spécifier les balises que vous considérez appropriées. Si vous souhaitez exporter la sortie au format PDF, sélectionnez l’option **[!UICONTROL Acrobat (.PDF)]** . Par défaut, le document est exporté au format JPG et InDesign. Pour modifier la miniature d’affichage pour le document multi-page, cliquez/appuyez sur . **[!UICONTROL Modifier la miniature]**.

   ![chlimage_1-332](assets/chlimage_1-332.png)

1. Cliquez/appuyez sur **[!UICONTROL Enregistrer]** puis cliquez/appuyez sur . **[!UICONTROL OK]** dans la boîte de dialogue pour fermer la boîte de dialogue. Le document multi-page est créé dans le dossier avec lequel vous avez commencé.

   >[!NOTE]
   >
   >Vous ne pouvez pas modifier ultérieurement un dérivé fusionné ni l’utiliser pour créer d’autres dérivés.
