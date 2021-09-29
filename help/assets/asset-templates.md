---
title: Modèles de ressources
description: Découvrez les modèles de ressources dans  [!DNL Experience Manager] Ressources et comment utiliser les modèles de ressources pour créer des documents marketing.
uuid: 7ba87c1d-70cd-4b89-86f3-971b93885f1e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 340b62f7-2405-4d2d-846d-2c444d6cc77b
feature: Asset Management,Developer Tools
role: User
exl-id: 9b4f16e6-dd91-4179-9629-576d801fcf43
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 68%

---

# Modèles de ressources {#asset-templates}

Les modèles de ressources sont une classe spéciale de ressources qui facilite la réorientation rapide de contenu visuellement riche pour les médias numériques et imprimés. Un modèle de ressource comprend deux parties : une section de message fixe et une section modifiable.

La section fixe peut comprendre du contenu propriétaire, comme le logo d’une marque ou des informations sur les droits d’auteur, pour lequel la modification n’est pas activée. La section modifiable peut contenir du contenu visuel et textuel dans des champs qui peuvent être modifiés pour personnaliser les messages.

Parce qu’ils permettent de réaliser des modifications limitées tout en garantissant une harmonie d’ensemble, les modèles de ressources sont des blocs de création parfaits pour adapter et diffuser rapidement votre contenu. La réutilisation de contenu permet de réduire les coûts de gestion des canaux papier et numériques. Cela garantit en outre une expérience globale cohérente, quel que soit le canal de diffusion.

En tant que marketeur, vous pouvez stocker et gérer des modèles dans [!DNL Experience Manager] Ressources et utiliser un seul modèle de base pour créer facilement plusieurs expériences d’impression personnalisées. Vous pouvez créer différents types de documents marketing, par exemple, des brochures, des prospectus, des cartes postales, des cartes de visite, etc. pour transmettre de façon claire votre message marketing à vos clients. Vous pouvez également assembler des documents papier comportant plusieurs pages à partir de documents papier nouveaux ou existants. Vous pouvez surtout diffuser des expériences à la fois numériques et papier simultanément en toute simplicité et offrir ainsi aux utilisateurs une expérience intégrée cohérente.

Si les modèles de ressources sont pour la plupart des fichiers InDesign, il n’est pas nécessaire de maîtriser InDesign pour réaliser des documents de qualité. Vous n’avez pas besoin de mapper les champs de votre modèle InDesign avec vos champs produit comme cela est nécessaire lors de la création de catalogues. Vous pouvez éditer les modèles en mode WYSIWYG directement depuis l&#39;interface web. Cependant, pour que l’InDesign traite vos modifications, vous devez d’abord configurer [!DNL Experience Manager] Ressources à intégrer au serveur InDesign.

La possibilité de modifier les modèles InDesign depuis l’interface web contribue à une meilleure collaboration entre les équipes marketing et créatives tout en réduisant le délai de diffusion des actions de promotion locales.

Avec les modèles de ressources, vous pouvez :

* Modifier des champs de modèle modifiables depuis l’interface web
* Contrôler les paramètres de base de style du texte, par exemple, la taille, le style et le type de police au niveau des balises
* Modifier les images du modèle à l’aide du sélecteur de contenu
* Prévisualiser les modifications du modèle
* Fusionner plusieurs fichiers de modèle pour créer un document multipage

Lorsque vous choisissez un modèle pour votre document, [!DNL Assets] crée une copie du modèle que vous pouvez modifier. Le modèle original est préservé, ce qui garantit que votre signalétique reste intacte et peut être réutilisée pour renforcer la cohérence de la marque.

Vous pouvez exporter le fichier mis à jour dans le dossier parent aux formats suivants :

* INDD
* PDF
* JPG

Vous pouvez également télécharger ces différents formats sur votre système local.

## Création d’un document {#creating-a-collateral}

Imaginons que vous voulez créer des contenus numériques papier, comme des brochures, des prospectus ou des publicités pour une future campagne, et les envoyer à des magasins dans le monde entier. Créer de tels documents à l’aide d’un modèle vous permet de proposer la même expérience client sur tous les canaux de diffusion. Les concepteurs peuvent créer les modèles de campagne (une ou plusieurs pages) à l’aide d’une solution créative, telle que l’InDesign et le chargement des modèles vers [!DNL Assets] pour vous. Avant de créer un document, vous devez avoir préalablement chargé un ou plusieurs modèles INDD et les mettre à disposition en Experience Manager.

1. Cliquez sur le logo [!DNL Experience Manager], puis sur **[!UICONTROL Ressources]** dans la page de navigation.
1. Dans les options, choisissez **[!UICONTROL Modèles]**.

   ![chlimage_1-306](assets/chlimage_1-306.png)

1. Cliquez/appuyez sur **[!UICONTROL Créer]**, puis choisissez dans le menu le type de document que vous souhaitez créer. Par exemple, choisissez **[!UICONTROL Brochure]**.

   ![chlimage_1-307](assets/chlimage_1-307.png)

1. Demandez qu’un ou plusieurs modèles INDD soient chargés et disponibles en Experience Manager à l’avance. Choisissez un modèle pour votre brochure, puis cliquez/appuyez sur **[!UICONTROL Suivant]**.

   ![chlimage_1-308](assets/chlimage_1-308.png)

1. Entrez un nom et éventuellement une description pour la brochure.

   ![chlimage_1-309](assets/chlimage_1-309.png)

1. (En option) Cliquez/appuyez sur l’icône **[!UICONTROL Balises]** sous le champ **[!UICONTROL Balises]**, puis sélectionnez une ou plusieurs balises pour la brochure. Cliquez/appuyez sur **[!UICONTROL Confirmer]** pour confirmer votre sélection.

   ![chlimage_1-310](assets/chlimage_1-310.png)

1. Cliquez sur **[!UICONTROL Créer]**. Une boîte de dialogue s’ouvre pour confirmer que la nouvelle brochure a été créée. Cliquez/appuyez sur **[!UICONTROL Ouvrir]** pour ouvrir la brochure en mode Édition.

   ![chlimage_1-311](assets/chlimage_1-311.png)

   Vous pouvez aussi fermer la boîte de dialogue et accéder au dossier dans la page Modèles de départ pour afficher la brochure créée. Le type de document apparaît sur sa miniature en mode Carte. Par exemple, Brochure est ici affiché sur la miniature.

   ![chlimage_1-312](assets/chlimage_1-312.png)

## Modification d’un document {#editing-a-collateral}

Vous pouvez modifier un document immédiatement après sa création. Vous pouvez aussi choisir de l’ouvrir depuis la page Modèles ou la page des détails du fichier.

1. Pour ouvrir un document pour le modifier, procédez de l’une des façons suivantes :

   * Ouvrez le document marketing (une brochure ici) créé à l’étape 7 de la section [Création d’un document](asset-templates.md#creating-a-collateral).
   * Depuis la page Modèles, accédez au dossier où vous avez placé le document créé, puis cliquez/appuyez sur l’option d’édition rapide depuis la miniature d’un document.
   * Dans la page des détails du document, cliquez/appuyez sur l’icône Modifier dans la barre d’outils.
   * Sélectionnez le document, puis cliquez/appuyez sur l’icône Modifier de la barre d’outils.

   ![chlimage_1-313](assets/chlimage_1-313.png)

   L’outil de recherche de ressources et l’éditeur de texte sont affichés à gauche de la page. L’éditeur de texte s’ouvre par défaut.

   Vous pouvez utiliser l’éditeur de texte pour modifier le texte à afficher dans le champ de texte. Vous pouvez modifier la taille, le style, la couleur et le type de police au niveau de la balise.

   À l’aide de l’outil de recherche de ressources, vous pouvez parcourir ou rechercher des images dans [!DNL Assets] et remplacer les images modifiables du modèle par les images de votre choix.

   ![chlimage_1-314](assets/chlimage_1-314.png)

   Les champs modifiables sont affichés à droite. Pour qu’un champ soit modifiable dans [!DNL Assets], le champ correspondant dans le modèle doit être balisé en InDesign. Plus exactement, il doit être indiqué comme étant modifiable dans InDesign.

   ![chlimage_1-315](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >Assurez-vous que votre instance [!DNL Experience Manager] est intégrée à un serveur d’InDesign pour permettre à [!DNL Assets] d’extraire des données du modèle d’InDesign et de les rendre disponibles pour modification. Pour plus d’informations, voir [Intégration [!DNL Assets] à InDesign Server](indesign.md).

1. Pour modifier le texte d’un champ modifiable, cliquez/appuyez sur le champ de texte dans la liste des champs modifiables, puis modifiez le texte dans le champ.

   ![chlimage_1-316](assets/chlimage_1-316.png)

   Vous pouvez modifier les propriétés de texte, par exemple la taille, la couleur ou le style de police à l’aide des options fournies.

1. Cliquez/appuyez sur l’icône **[!UICONTROL Aperçu]** pour prévisualiser les modifications.

   ![chlimage_1-317](assets/chlimage_1-317.png)

1. Pour permuter une image, cliquez/appuyez sur l’icône **[!UICONTROL Outil de recherche de ressources]**.

   ![chlimage_1-318](assets/chlimage_1-318.png)

1. Sélectionnez le champ d’image dans la liste des champs modifiables, puis faites glisser l’image souhaitée du sélecteur de ressource vers le champ modifiable.

   ![chlimage_1-319](assets/chlimage_1-319.png)

   Vous pouvez également rechercher des images à l’aide de mots-clés, de balises ou selon leur état de publication. Vous pouvez parcourir le référentiel [!DNL Assets] et accéder à l’emplacement de l’image souhaitée.

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. Cliquez/appuyez sur l’icône **[!UICONTROL Aperçu]** pour prévisualiser l’image.

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. Pour modifier une page en particulier dans un document contenant plusieurs pages, utilisez l’outil de navigation au bas de la page.

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. Cliquez/appuyez sur l’icône **[!UICONTROL Aperçu]** dans la barre d’outils pour prévisualiser toutes les modifications. Cliquez/appuyez sur **[!UICONTROL Terminé]** pour enregistrer les modifications apportées au document.

   >[!NOTE]
   >
   >Les icônes Aperçu et Terminé sont activées uniquement lorsqu’il ne manque aucune icône aux champs d’image modifiables dans le document. S’il manque des icônes dans votre document, c’est parce que [!DNL Experience Manager] ne peut pas résoudre les images dans le modèle d’InDesign. En règle générale, [!DNL Experience Manager] ne peut pas résoudre les images dans les cas suivants :
   >
   >* Les images ne sont pas incorporées dans le modèle d’InDesign sous-jacent.
   >* Les images ne sont pas liées depuis le système de fichiers local.

   >
   >Pour permettre à [!DNL Experience Manager] de résoudre les images, procédez comme suit :
   >
   >* Incorporez les images lorsque vous créez les modèles InDesign (reportez-vous à la section [À propos des liens et des objets graphiques incorporés](https://helpx.adobe.com/fr/indesign/using/graphics-links.html)).
   >* Montez [!DNL Experience Manager] sur votre système de fichiers local, puis mappez les icônes manquantes avec les ressources [!DNL Experience Manager] existantes.

   >
   >Pour plus d’informations sur l’utilisation des documents InDesign, voir [Bonnes pratiques relatives à l’utilisation des documents InDesign dans  [!DNL Experience Manager]](https://helpx.adobe.com/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Pour générer un rendu PDF pour la brochure, sélectionnez l’option Acrobat dans la boîte de dialogue, puis cliquez sur **[!UICONTROL Continuer]**.
1. Le document est créé dans le dossier où vous avez commencé. Pour afficher les rendus, ouvrez le document et choisissez **[!UICONTROL Rendus]** dans la liste de navigation globale.

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. Cliquez/appuyez sur le rendu PDF dans la liste des rendus pour télécharger le fichier PDF. Ouvrez le fichier PDF pour réviser le document.

   ![chlimage_1-324](assets/chlimage_1-324.png)

## Création d’un document fusionné {#merge-collateral}


1. Cliquez ou appuyez sur **[!UICONTROL Outils > Ressources]**.
1. Dans les options, choisissez **[!UICONTROL Modèles]**.
1. Cliquez/appuyez sur **[!UICONTROL Créer]** et choisissez **[!UICONTROL Fusionner]** dans le menu.

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Dans la page Fusion de modèle, cliquez/appuyez sur l’icône Fusionner.

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. Accédez aux documents que vous souhaitez fusionner, cliquez/appuyez sur les miniatures des documents que vous souhaitez fusionner pour les sélectionner.

   ![chlimage_1-327](assets/chlimage_1-327.png)

   Vous pouvez également rechercher des modèles avec OmniSearch.

   ![chlimage_1-328](assets/chlimage_1-328.png)

   Vous pouvez parcourir le référentiel [!DNL Assets] ou les collections, accéder à l’emplacement des modèles souhaités, puis les sélectionner pour la fusion.

   ![chlimage_1-329](assets/chlimage_1-329.png)

   Vous pouvez appliquer différents filtres pour rechercher les modèles souhaités. Par exemple, vous pouvez rechercher des modèles en fonction de leur type ou de leurs balises.

   ![chlimage_1-330](assets/chlimage_1-330.png)

1. Cliquez ou appuyez sur **[!UICONTROL Suivant]** dans la barre d’outils.
1. Dans l’écran **[!UICONTROL Aperçu et réorganisation]**, réorganisez les modèles si nécessaire et prévisualisez la sélection de modèles à fusionner. Cliquez/appuyez ensuite sur **[!UICONTROL Suivant]** dans la barre d’outils.

   ![chlimage_1-331](assets/chlimage_1-331.png)

1. Dans l’écran Configurer le modèle, indiquez un nom pour le document. Vous pouvez également spécifier les balises que vous considérez appropriées. Pour exporter le résultat au format PDF, sélectionnez l’option **[!UICONTROL Acrobat (.PDF)]**. Par défaut, le document est exporté aux formats JPG et InDesign. Pour modifier la miniature du document multipage, cliquez/appuyez sur **[!UICONTROL Modifier la miniature]**.

   ![chlimage_1-332](assets/chlimage_1-332.png)

1. Cliquez/appuyez sur **[!UICONTROL Enregistrer]**, puis cliquez/appuyez sur **[!UICONTROL OK]** dans la boîte de dialogue pour fermer la boîte de dialogue. Le document multipage est créé dans le dossier de départ.

   >[!NOTE]
   >
   >Vous ne pouvez pas modifier ultérieurement un document fusionné ni l’utiliser pour créer d’autres documents.
