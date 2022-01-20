---
title: '"Didacticiel : Créer des modèles"'
seo-title: Create Print and Web templates for Interactive Communication
description: Créer des modèles d’impression et web pour la communication interactive
seo-description: Create Print and Web templates for Interactive Communication
uuid: d7b0d9a5-f5f0-4c21-a6f8-622bf94f4491
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 40c0a17b-6894-44cc-b1f7-490913061532
feature: Interactive Communication
exl-id: 5822145f-d317-4807-a3f0-1d2aea0a779b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 67%

---

# Didacticiel : Créer des modèles {#tutorial-create-templates}

Créer des modèles d’impression et web pour la communication interactive

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Ce tutoriel est une étape dans la [Créer votre première communication interactive](/help/forms/using/create-your-first-interactive-communication.md) série. Il est recommandé de suivre la série dans l’ordre chronologique pour comprendre, exécuter et démontrer le cas d’utilisation complet du didacticiel.

Pour créer une communication interactive, vous devez disposer de modèles disponibles sur le serveur AEM pour les canaux d’impression et web.

Les modèles pour le canal d’impression sont créés dans Adobe Forms Designer et téléchargés sur le serveur AEM. Ces modèles sont ensuite disponibles pour être utilisés lors de la création d’une communication interactive.

Les modèles pour le canal web sont créés dans AEM. Les auteurs et les administrateurs de modèles peuvent créer, modifier et activer des modèles web. Une fois créés et activés, ces modèles sont disponibles pour être utilisés lors de la création d’une communication interactive.

Ce didacticiel vous guide pas à pas dans la création de modèles pour les canaux d’impression et web, afin qu’ils soient disponibles lors de la création de communications interactives. À la fin de ce didacticiel, vous serez capable de :

* Créer des modèles XDP pour le canal d’impression à l’aide d’Adobe Forms Designer
* Télécharger les modèles XDP sur le serveur AEM Forms
* Créer et activer des modèles pour le canal web

## Créer un modèle pour le canal d’impression {#create-template-for-print-channel}

Créez et gérez un modèle pour le canal d’impression de la communication interactive à l’aide des tâches suivantes :

* [Créer un modèle XDP en utilisant Forms Designer](/help/forms/using/create-templates-print-web.md#create-xdp-template-using-forms-designer)
* [Télécharger le modèle XDP sur le serveur AEM Forms](/help/forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server)
* [Créer un modèle XDP pour des fragments de mise en page](/help/forms/using/create-templates-print-web.md#create-xdp-template-for-layout-fragments)

### Créer un modèle XDP en utilisant Forms Designer {#create-xdp-template-using-forms-designer}

Selon la variable [cas pratique](/help/forms/using/create-your-first-interactive-communication.md) et [anatomie](/help/forms/using/planning-interactive-communications.md), créez les sous-formulaires suivants dans le modèle XDP :

* Informations de facturation : comprend un fragment de document
* Détails du client : Inclut un fragment de document
* Récapitulatif de facturation : Inclut un fragment de document
* Résumé : Inclut un fragment de document (sous-formulaire Frais) et un graphique (sous-formulaire Graphiques)
* Appels détaillés : Inclut un tableau (fragment de mise en page)
* Payer maintenant : Inclut une image
* Services à valeur ajoutée : Inclut une image

![create_print_template](assets/create_print_template.gif)

Ces sous-formulaires sont affichés en tant que zones cibles dans le modèle d’impression après le téléchargement du fichier XDP sur le serveur Forms. Toutes les entités telles que des fragments de document, des graphiques, des fragments de mise en page et des images sont ajoutées aux zones cibles lors de la création de la communication interactive.

Exécutez les étapes suivantes pour créer un modèle XDP pour le canal d’impression :

1. Ouvrez Forms Designer, puis sélectionnez **Fichier** > **Nouveau** > **Utiliser un formulaire vierge,** appuyer **Suivant**, puis appuyez sur **Terminer** pour ouvrir le formulaire à des fins de création de modèle.

   Assurez-vous que les options **Bibliothèque d’objets** et **Objet** sont sélectionnées dans le menu **Fenêtre**.

1. Faites glisser le composant **Sous-formulaire** de la **bibliothèque d’objets** vers le formulaire.
1. Sélectionnez le sous-formulaire pour afficher les options correspondantes dans la fenêtre **Objet** dans le volet de droite.
1. Sélectionnez la **Subform** et sélectionnez **Distribué** de la **Contenu** liste déroulante. Faites glisser l’extrémité gauche du sous-formulaire pour ajuster la longueur.
1. Dans l’onglet **Liaisons** :

   1. Spécifier **BillDetails** dans le **Nom** champ .
   1. Sélectionnez **Aucune liaison de données** dans la liste déroulante **Liaison de données**.

   ![forms_designer_subform](assets/forms_designer_subform.png)

1. De même, sélectionnez le sous-formulaire racine, puis le **Subform** et sélectionnez **Distribué** de la **Contenu** liste déroulante. Dans l’onglet **Liaisons** :

   1. Spécifier **TelecaBill** dans le **Nom** champ .
   1. Sélectionnez **Aucune liaison de données** dans la liste déroulante **Liaison de données**.

   ![root_subform_print_template](assets/root_subform_print_template.png)

1. Répétez les étapes 2 à 5 pour créer les sous-formulaires suivants :

   * BillDetails
   * CustomerDetails
   * BillSummary
   * Résumé : sélectionnez le **Subform** et sélectionnez **Positionné** de la **Contenu** liste déroulante de ce sous-formulaire. Insérez les sous-formulaires suivants dans le sous-formulaire **Résumé**.

      * Frais
      * Graphiques
   * ItemisedCalls
   * PayNow
   * ValueAddedServices

   Pour gagner du temps, vous pouvez également copier et coller des sous-formulaires existants pour créer de nouveaux sous-formulaires.

   Pour changer le **Graphiques** Sélectionnez le sous-formulaire situé à droite du sous-formulaire Frais . **Graphiques** dans le volet de gauche, sélectionnez le sous-formulaire **Disposition** et spécifiez une valeur pour **AncreX** champ . La valeur doit être supérieure à la valeur du champ **Largeur** pour le sous-formulaire **Frais**. Sélectionnez le sous-formulaire **Frais** et sélectionnez l’onglet **Mise en page** pour afficher la valeur du champ **Largeur.**

1. Faites glisser l’objet **Texte** de la **bibliothèque d’objets** vers le formulaire et saisissez le texte **Composez le XXXX pour vous abonner** dans la zone.
1. Cliquez avec le bouton droit de la souris sur l’objet texte dans le volet de gauche, sélectionnez **Renommer l’objet** et saisissez le nom de l’objet texte **S’abonner**.

   ![print_xdp_template_subform](assets/print_xdp_template_subform.png)

1. Sélectionnez **Fichier** > **Enregistrer sous** pour enregistrer le fichier sur le système de fichiers local :

   1. Accédez à l’emplacement où vous souhaitez enregistrer le fichier et spécifiez le nom **create_first_ic_print_template**.
   1. Sélectionnez **.xdp** dans la liste déroulante **Type**.
   1. Appuyez sur **Enregistrer**.

### Télécharger le modèle XDP sur le serveur AEM Forms {#upload-xdp-template-to-the-aem-forms-server}

Une fois que vous avez créé un modèle XDP à l’aide de Forms Designer, vous devez le télécharger sur le serveur AEM Forms pour qu’il soit disponible lors de la création de la communication interactive.

1. Sélectionnez **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Appuyez sur **Créer** > **Chargement de fichier**.

   Naviguez et sélectionnez le **create_first_ic_print_template** template (XDP) et appuyez sur **Ouvrir** pour importer le modèle XDP sur le serveur AEM Forms.

### Créer un modèle XDP pour des fragments de mise en page {#create-xdp-template-for-layout-fragments}

Pour créer un fragment de mise en page pour le canal d’impression de la communication interactive, créez un XDP à l’aide de Forms Designer et chargez-le sur le serveur AEM Forms.

1. Ouvrez Forms Designer, puis sélectionnez **Fichier** > **Nouveau** > **Utiliser un formulaire vierge,** appuyer **Suivant**, puis appuyez sur **Terminer** pour ouvrir le formulaire à des fins de création de modèle.

   Assurez-vous que les options **Bibliothèque d’objets** et **Objet** sont sélectionnées dans le menu **Fenêtre**.

1. Faites glisser et déposez le **Tableau** du composant **Bibliothèque d’objets** au formulaire.
1. Dans la boîte de dialogue Insérer un tableau :

   1. Spécifiez **5** comme nombre de colonnes.
   1. Spécifiez **1** comme nombre de rangées de contenu.
   1. Cochez la case **Inclure la rangée d’en-tête dans le tableau**.
   1. Onglet **OK**.

1. Appuyez sur **+** dans le volet gauche en regard du **Tableau** 1 et cliquez avec le bouton droit de la souris sur **Cell1**, sélectionnez **Renommer l’objet** et remplacez le nom Cell1 par **Date**.

   De même, renommez respectivement **Cell2**, **Cell3**, **Cell4** et **Cell5** en **Heure**, **Numéro**, **Durée** et **Frais**.

1. Cliquez sur les champs de texte En-tête dans le **Vue Designer** et renommez-les en **Heure**, **Nombre**, **Durée**, et **Frais**.

   ![layout_fragment_print](assets/layout_fragment_print.png)

1. Sélectionnez **Rangée 1** dans le volet gauche et sélectionnez **Objet** > **Liaison** > **Rangée pour chaque élément**.

   ![layout_fragment_print_repeat](assets/layout_fragment_print_repeat.png)

1. Faites glisser et déposez le **Champ de texte** du composant **Bibliothèque d’objets** au **Vue Designer**.

   ![layout_fragment_print_text_field](assets/layout_fragment_print_text_field.png)

   De même, faites glisser le composant **Champ de texte** vers les rangées **Heure**, **Numéro**, **Durée** et **Frais**.

1. Sélectionnez **Fichier** > **Enregistrer sous** pour enregistrer le fichier sur le système de fichiers local :

   1. Accédez à l’emplacement où enregistrer le fichier et indiquez le nom en tant que **table_lf**.
   1. Sélectionnez **.xdp** dans la liste déroulante **Type**.
   1. Appuyez sur **Enregistrer**.

   Une fois que vous avez créé un modèle XDP pour le fragment de mise en page à l’aide de Forms Designer, vous devez le [télécharger](/help/forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server) sur le serveur AEM Forms pour qu’il soit disponible lors de la création des fragments de mise en page.

## Créer un modèle pour le canal web {#create-template-for-web-channel}

Créez et gérez un modèle pour le canal web de la communication interactive à l’aide des tâches suivantes :

* [Créer un dossier pour les modèles](/help/forms/using/create-templates-print-web.md#create-folder-for-templates)
* [Créer le modèle](/help/forms/using/create-templates-print-web.md#create-the-template)
* [Activer le modèle](/help/forms/using/create-templates-print-web.md#enable-the-template)
* [Activer les boutons dans les communications interactives](/help/forms/using/create-templates-print-web.md#enabling-buttons-in-interactive-communications)

### Créer un dossier pour les modèles {#create-folder-for-templates}

Pour créer un modèle de canal web, définissez un dossier dans lequel vous pouvez enregistrer les modèles créés. Une fois que vous avez créé un modèle dans un dossier, vous devez l’activer pour permettre aux utilisateurs de formulaires de créer le canal web d’une communication interactive en fonction du modèle.

Exécutez les étapes suivantes pour créer un dossier pour les modèles modifiables :

1. Appuyer **Outils** ![Outils](assets/tools-icon.svg) > **Explorateur de configuration**.
   * Pour plus d’informations, consultez la documentation relative au [](/help/sites-administering/configurations.md)Navigateur de configuration.
1. Sur la page du navigateur de configuration, appuyez sur . **Créer**.
1. Dans le **Créer une configuration** dialog, spécifiez **Create_First_IC_templates** comme titre du dossier, cochez **Modèles modifiables**, puis appuyez sur **Créer**.

   ![create_first_ic_web_template](assets/create_first_ic_web_template.png)

   Le **Create_First_IC_templates** est créé et répertorié dans la **Explorateur de configuration** page.

### Créer le modèle {#create-the-template}

Selon la variable [cas pratique](/help/forms/using/create-your-first-interactive-communication.md) et [anatomie](/help/forms/using/planning-interactive-communications.md), créez les panneaux suivants dans le modèle Web :

* Informations de facturation : comprend un fragment de document
* Détails du client : Inclut un fragment de document
* Récapitulatif de facturation : Inclut un fragment de document
* Résumé des frais : Inclut un fragment de document et un graphique (mise en page à deux colonnes)
* Appels détaillés : Inclut un tableau
* Payer maintenant : Inclut une **Payer maintenant** bouton et image
* Services à valeur ajoutée : Inclut une image et une **S’abonner** bouton .

![create_web_template](assets/create_web_template.gif)

Toutes les entités telles que des fragments de document, des graphiques, des tableaux, des images et des boutons sont ajoutées lors de la création de la communication interactive.

Exécutez les étapes suivantes pour créer un modèle pour le canal web dans le dossier **Create_First_IC_templates** :

1. Accédez au dossier de modèle approprié en sélectionnant **Outils** > **Modèles** > **Create_First_IC_templates** dossier.
1. Appuyez sur **Créer**.
1. Sur le **Sélection d’un type de modèle** assistant de configuration, sélectionnez **Communication interactive - Canal web** et appuyez sur **Suivant**.
1. Sur le **Détails du modèle** assistant de configuration, spécifiez **Create_First_IC_Web_Template** comme titre du modèle. Spécifiez une description facultative et appuyez sur **Créer**.

   Un message de confirmation indiquant que la variable **Create_First_IC_Web_Template** s’affiche.

1. Appuyez sur **Ouvrir** pour ouvrir le modèle dans l’éditeur de modèles.
1. Sélectionnez **Contenu initial** dans la liste déroulante en regard de l’option **Aperçu**.

   ![template_editor_initial_content](assets/template_editor_initial_content.png)

1. Appuyer **Panneau racine** puis appuyez sur **+** pour afficher la liste des composants que vous pouvez ajouter au modèle.
1. Sélectionnez **Panneau** dans la liste pour ajouter un panneau au-dessus du **panneau racine**.
1. Sélectionnez l’onglet **Contenu** dans le volet gauche. Le nouveau panneau ajouté à l’étape 8 est affiché sous le **panneau racine** dans l’arborescence de contenu.

   ![content_tree_root_panel](assets/content_tree_root_panel.png)

1. Sélectionnez le panneau et appuyez sur ![configure_icon](assets/configure_icon.png) (Configuration).
1. Dans le panneau Propriétés :

   1. Spécifiez **billdetails** dans le champ Nom.
   1. Spécifiez **Information de facturation** dans le champ Titre.
   1. Sélectionnez **1** dans la liste déroulante **Nombre de colonnes**.
   1. Appuyer ![done_icon](assets/done_icon.png) pour enregistrer les propriétés.

   Le nom du panneau est mis à jour vers **Information de facturation** dans l’arborescence de contenu.

1. Répétez les étapes 7 à 11 pour ajouter des panneaux avec les propriétés suivantes au modèle :

   | Nom | Titre | Nombre de colonnes |
   |---|---|---|
   | customerdetails | Informations sur le client | 1 |
   | billsummary | Récapitulatif de facturation | 1 |
   | summarycharges | Récapitulatif des frais | 2 |
   | itemisedcalls | Appels détaillés | 1 |
   | PayNow | Payez maintenant | 2 |
   | vas | Services à valeur ajoutée | 1 |

   L’image suivante illustre l’arborescence de contenu après l’ajout de tous les panneaux au modèle :

   ![content_tee_all_panels](assets/content_tee_all_panels.png)

### Activer le modèle {#enable-the-template}

Une fois que vous avez créé le modèle web, vous devez l’activer pour utiliser le modèle lors de la création de la communication interactive.

Effectuez les étapes suivantes pour activer le modèle web :

1. Appuyer **Outils** ![Outils](assets/tools-icon.svg) > **Modèles**.
1. Accédez au **Create_First_IC_Web_Template** modèle, sélectionnez-le, puis appuyez sur **Activer**.
1. Appuyez de nouveau sur **Activer** pour confirmer.

   Le modèle est activé et son statut s’affiche comme Activé. Vous pouvez utiliser ce modèle lors de la création de la communication interactive pour le canal web.

### Activer les boutons dans les communications interactives {#enabling-buttons-in-interactive-communications}

En fonction du cas d’utilisation, vous devez inclure les boutons **Payer maintenant** et **S’abonner** (composants de formulaires adaptatifs) dans la communication interactive. Pour activer l’utilisation de ces boutons dans la communication interactive, procédez comme suit :

1. Sélectionner **Structure** dans la liste déroulante en regard de la fonction **Aperçu** .
1. Sélectionnez le panneau racine **Conteneur de documents** en utilisant l’arborescence de contenu et appuyez sur **Stratégie** pour sélectionner les composants qui sont autorisés à être utilisés dans la communication interactive.

   ![structure_configure_policy](assets/structure_configure_policy.png)

1. Dans l’onglet **Composants autorisés** de la section **Propriétés**, sélectionnez **Bouton** à partir des composants de **formulaire adaptatif**.

   ![allowed_components_af](assets/allowed_components_af.png)

1. Appuyer ![done_icon](assets/done_icon.png) pour enregistrer les propriétés.
