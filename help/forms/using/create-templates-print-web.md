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
ht-degree: 96%

---

# Didacticiel : Créer des modèles {#tutorial-create-templates}

Créer des modèles d’impression et web pour la communication interactive

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Ce tutoriel fait partie de la série [Création de votre première communication interactive](/help/forms/using/create-your-first-interactive-communication.md). Il est recommandé de suivre la série dans l’ordre chronologique pour comprendre, exécuter et démontrer le cas d’utilisation complet du didacticiel.

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

En fonction du [cas d’utilisation](/help/forms/using/create-your-first-interactive-communication.md) et de la [structure](/help/forms/using/planning-interactive-communications.md), créez les sous-formulaires suivants dans le modèle XDP :

* Informations de facturation : comprend un fragment de document
* Informations sur le client : comprend un fragment de document
* Récapitulatif de facturation : comprend un fragment de document
* Résumé : comprend un fragment de document (sous-formulaire Frais) et un graphique (sous-formulaire Graphiques)
* Appels détaillés : Inclut un tableau (fragment de mise en page)
* Payer maintenant : comprend une image
* Services à valeur ajoutée : comprend une image

![create_print_template](assets/create_print_template.gif)

Ces sous-formulaires sont affichés en tant que zones cibles dans le modèle d’impression après le téléchargement du fichier XDP sur le serveur Forms. Toutes les entités telles que des fragments de document, des graphiques, des fragments de mise en page et des images sont ajoutées aux zones cibles lors de la création de la communication interactive.

Exécutez les étapes suivantes pour créer un modèle XDP pour le canal d’impression :

1. Ouvrez Forms Designer, sélectionnez **Fichier** > **Nouveau** > **Utiliser un formulaire vierge,** cliquez sur **Suivant**, puis sur **Terminer** pour ouvrir le formulaire afin de créer le modèle.

   Assurez-vous que les options **Bibliothèque d’objets** et **Objet** sont sélectionnées dans le menu **Fenêtre**.

1. Faites glisser le composant **Sous-formulaire** de la **bibliothèque d’objets** vers le formulaire.
1. Sélectionnez le sous-formulaire pour afficher les options correspondantes dans la fenêtre **Objet** dans le volet de droite.
1. Sélectionnez l’onglet **Sous-formulaire** et sélectionnez **Distribué** dans la liste déroulante **Contenu**. Faites glisser l’extrémité gauche du sous-formulaire pour ajuster la longueur.
1. Dans l’onglet **Liaisons** :

   1. Spécifiez **billdetails** dans le champ **Nom**.
   1. Sélectionnez **Aucune liaison de données** dans la liste déroulante **Liaison de données**.

   ![forms_designer_subform](assets/forms_designer_subform.png)

1. De même, sélectionnez le sous-formulaire racine et l’onglet **Sous-formulaire**, puis sélectionnez **Distribué** dans la liste déroulante **Contenu**. Dans l’onglet **Liaisons** :

   1. Spécifiez **TelecaBill** dans le champ **Nom**.
   1. Sélectionnez **Aucune liaison de données** dans la liste déroulante **Liaison de données**.

   ![root_subform_print_template](assets/root_subform_print_template.png)

1. Répétez les étapes 2 à 5 pour créer les sous-formulaires suivants :

   * BillDetails
   * CustomerDetails
   * BillSummary
   * Résumé : sélectionnez l’onglet **Sous-formulaire**, puis **Positionné** dans la liste déroulante **Contenu** de ce sous-formulaire. Insérez les sous-formulaires suivants dans le sous-formulaire **Résumé**.

      * Frais
      * Graphiques
   * ItemisedCalls
   * PayNow
   * ValueAddedServices

   Pour gagner du temps, vous pouvez également copier et coller des sous-formulaires existants pour créer de nouveaux sous-formulaires.

   Pour déplacer le sous-formulaire **Graphiques** vers la droite du sous-formulaire Frais, sélectionnez le sous-formulaire **Graphiques** dans le volet gauche, puis l’onglet **Disposition** et indiquez une valeur pour le champ **AnchorX**. La valeur doit être supérieure à la valeur du champ **Largeur** pour le sous-formulaire **Frais**. Sélectionnez le sous-formulaire **Frais** et sélectionnez l’onglet **Mise en page** pour afficher la valeur du champ **Largeur.**

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

   Accédez au modèle XDP **create_first_ic_print_template**, sélectionnez-le et cliquez sur **Ouvrir** pour importer le modèle XDP sur le serveur AEM Forms.

### Créer un modèle XDP pour des fragments de mise en page {#create-xdp-template-for-layout-fragments}

Pour créer un fragment de mise en page pour le canal d’impression de la communication interactive, créez un XDP à l’aide de Forms Designer et chargez-le sur le serveur AEM Forms.

1. Ouvrez Forms Designer, sélectionnez **Fichier** > **Nouveau** > **Utiliser un formulaire vierge**, cliquez sur **Suivant**, puis sur **Terminer** pour ouvrir le formulaire afin de créer le modèle.

   Assurez-vous que les options **Bibliothèque d’objets** et **Objet** sont sélectionnées dans le menu **Fenêtre**.

1. Faites glisser le composant **Tableau** de la **bibliothèque d’objets** vers le formulaire.
1. Dans la boîte de dialogue Insérer un tableau :

   1. Spécifiez **5** comme nombre de colonnes.
   1. Spécifiez **1** comme nombre de rangées de contenu.
   1. Cochez la case **Inclure la rangée d’en-tête dans le tableau**.
   1. Onglet **OK**.

1. Appuyez sur **+** dans le volet gauche en regard du **Tableau** 1 et cliquez avec le bouton droit de la souris sur **Cell1**, sélectionnez **Renommer l’objet** et remplacez le nom Cell1 par **Date**.

   De même, renommez respectivement **Cell2**, **Cell3**, **Cell4** et **Cell5** en **Heure**, **Numéro**, **Durée** et **Frais**.

1. Cliquez sur les champs de texte d’en-tête dans l’**affichage Designer** et renommez-les comme suit : **Heure**, **Numéro**, **Durée** et **Frais**.

   ![layout_fragment_print](assets/layout_fragment_print.png)

1. Sélectionnez **Rangée 1** dans le volet gauche et sélectionnez **Objet** > **Liaison** > **Rangée pour chaque élément**.

   ![layout_fragment_print_repeat](assets/layout_fragment_print_repeat.png)

1. Faites glisser le composant **Champ de texte** de la **bibliothèque d’objets** vers l’**affichage Designer**.

   ![layout_fragment_print_text_field](assets/layout_fragment_print_text_field.png)

   De même, faites glisser le composant **Champ de texte** vers les rangées **Heure**, **Numéro**, **Durée** et **Frais**.

1. Sélectionnez **Fichier** > **Enregistrer sous** pour enregistrer le fichier sur le système de fichiers local :

   1. Accédez à l’emplacement où vous souhaitez enregistrer le fichier et spécifiez le nom **table_lf**.
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
1. Sur la page du navigateur de configuration, cliquez sur **Créer**.
1. Dans la boîte de dialogue **Créer une configuration**, spécifiez le titre **Create_First_IC_templates** pour le dossier, vérifiez **Modèles modifiables**, puis cliquez sur **Créer**.

   ![create_first_ic_web_template](assets/create_first_ic_web_template.png)

   Le dossier **Create_First_IC_templates** est créé et répertorié sur la page du **navigateur de configuration**.

### Créer le modèle {#create-the-template}

En fonction du [cas d’utilisation](/help/forms/using/create-your-first-interactive-communication.md) et de la [structure](/help/forms/using/planning-interactive-communications.md), créez les panneaux suivants dans le modèle web :

* Informations de facturation : comprend un fragment de document
* Informations sur le client : comprend un fragment de document
* Récapitulatif de facturation : comprend un fragment de document
* Récapitulatif des frais : comprend un fragment de document et un graphique (disposition en deux colonnes)
* Appels détaillés : comprend un tableau
* Payer maintenant : comprend un bouton et une image **Payer maintenant**
* Services à valeur ajoutée : comprend un bouton et une image **S’abonner**.

![create_web_template](assets/create_web_template.gif)

Toutes les entités telles que des fragments de document, des graphiques, des tableaux, des images et des boutons sont ajoutées lors de la création de la communication interactive.

Exécutez les étapes suivantes pour créer un modèle pour le canal web dans le dossier **Create_First_IC_templates** :

1. Accédez au dossier de modèle approprié en sélectionnant le dossier **Outils** > **Modèles** > **Create_First_IC_templates**.
1. Appuyez sur **Créer**.
1. Dans l’assistant de configuration **Choisir un type de modèle**, sélectionnez **Communication interactive - Canal web** et cliquez sur **Suivant**.
1. Dans l’assistant de configuration **Détails du modèle**, spécifiez comme titre pour le modèle **Create_First_IC_Web_Template**. Spécifiez une description facultative et appuyez sur **Créer**.

   Un message de confirmation indiquant que **Create_First_IC_Web_Template** sʼaffiche.

1. Appuyez sur **Ouvrir** pour ouvrir le modèle dans l’éditeur de modèles.
1. Sélectionnez **Contenu initial** dans la liste déroulante en regard de l’option **Aperçu**.

   ![template_editor_initial_content](assets/template_editor_initial_content.png)

1. Cliquez sur **Panneau racine**, puis sur **+** afin dʼafficher la liste des composants que vous pouvez ajouter au modèle.
1. Sélectionnez **Panneau** dans la liste pour ajouter un panneau au-dessus du **panneau racine**.
1. Sélectionnez l’onglet **Contenu** dans le volet gauche. Le nouveau panneau ajouté à l’étape 8 est affiché sous le **panneau racine** dans l’arborescence de contenu.

   ![content_tree_root_panel](assets/content_tree_root_panel.png)

1. Sélectionnez le tableau et cliquez sur ![configure_icon](assets/configure_icon.png) (Configurer).
1. Dans le panneau Propriétés :

   1. Spécifiez **billdetails** dans le champ Nom.
   1. Spécifiez **Information de facturation** dans le champ Titre.
   1. Sélectionnez **1** dans la liste déroulante **Nombre de colonnes**.
   1. Cliquez sur ![icône terminé](assets/done_icon.png) pour enregistrer les propriétés.

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
1. Accédez au modèle **Create_First_IC_Web_Template**, sélectionnez-le, puis cliquez sur **Activer**.
1. Appuyez de nouveau sur **Activer** pour confirmer.

   Le modèle est activé et son statut s’affiche comme Activé. Vous pouvez utiliser ce modèle lors de la création de la communication interactive pour le canal web.

### Activer les boutons dans les communications interactives {#enabling-buttons-in-interactive-communications}

En fonction du cas d’utilisation, vous devez inclure les boutons **Payer maintenant** et **S’abonner** (composants de formulaires adaptatifs) dans la communication interactive. Pour activer l’utilisation de ces boutons dans la communication interactive, procédez comme suit :

1. Sélectionnez **Structure** dans la liste déroulante en regard de l’option **Prévisualisation**.
1. Sélectionnez le panneau racine **Conteneur de documents** en utilisant l’arborescence de contenu et appuyez sur **Stratégie** pour sélectionner les composants qui sont autorisés à être utilisés dans la communication interactive.

   ![structure_configure_policy](assets/structure_configure_policy.png)

1. Dans l’onglet **Composants autorisés** de la section **Propriétés**, sélectionnez **Bouton** à partir des composants de **formulaire adaptatif**.

   ![allowed_components_af](assets/allowed_components_af.png)

1. Cliquez sur ![icône terminé](assets/done_icon.png) pour enregistrer les propriétés.
