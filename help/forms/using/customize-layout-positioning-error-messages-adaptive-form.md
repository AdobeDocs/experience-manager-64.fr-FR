---
title: Personnalisation de la disposition et de la position des messages d’erreur d’un formulaire adaptatif
seo-title: Customize layout and positioning of error messages of an adaptive form
description: 'Vous pouvez personnaliser la disposition et la position des messages d’erreur d’un formulaire adaptatif. '
seo-description: You can customize layout and positioning of the error messages of an adaptive for.
uuid: 18b6d770-8b68-4aa0-b866-6325a6ceabcf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: e1431ad9-3bae-4ac3-97e2-96dcbfce1f71
exl-id: a57bd3c4-2d50-4089-8279-1e403e9469bf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 100%

---

# Personnalisation de la disposition et de la position des messages d’erreur d’un formulaire adaptatif {#customize-layout-and-positioning-of-error-messages-of-an-adaptive-form}

Vous pouvez personnaliser la disposition et la position des messages d’erreur d’un formulaire adaptatif. Vous pouvez exécuter les personnalisations suivantes :

* Personnaliser l’emplacement et la disposition de la légende d’un champ sans apporter de modifications aux propriétés CSS correspondantes
* Personnalisation de la position des messages d’erreur intégrés
* Personnalisation du contenu d’un indicateur d’aide dynamique
* Personnaliser la position des composants de champ (légende, widget, brève description, longue description et composants d’indicateur d’aide) sans apporter de modifications aux propriétés CSS correspondantes

## Personnalisation de la disposition des champs {#customize-layout-of-fields}

Vous pouvez personnaliser la disposition d’un champ spécifique ou de tous les champs pour modifier la position de la légende et des messages d’erreur. Effectuez les étapes suivantes pour appliquer une disposition personnalisée à un champ :

### Personnalisation de la disposition d’un champ spécifique {#customize-layout-of-a-single-field}

Effectuez les étapes suivantes pour appliquer une disposition personnalisée à un champ spécifique :

1. Ouvrez le formulaire en mode **Style**. Pour ouvrir le formulaire en mode Style, écrivez dans la barre d’outils de la page ![canvas-drop-down](assets/canvas-drop-down.png) > **Style**.
1. Dans la barre latérale, sous **Objets de formulaire**, sélectionnez le champ, puis cliquez sur le bouton de modification ![edit-button](assets/edit-button.png).
1. Sélectionnez l’état du champ que vous souhaitez personnaliser, puis spécifiez le style de cet état.

   ![Spécification du style intégré d’un champ](assets/edit-error-state.png)

### Personnalisation de la disposition de tous les champs d’un formulaire {#customize-layout-of-all-the-fields-of-a-form}

Avec AEM Forms, vous pouvez désormais créer un thème et l’appliquer à votre formulaire. L’éditeur de thèmes vous permet de spécifier le style des composants de formulaire dans un seul et même endroit. Lorsque vous créez un thème, vous spécifiez le style au niveau du composant. Pour plus d’informations sur les thèmes, consultez la section [Thèmes dans AEM Forms](/help/forms/using/themes.md).

Créez un thème à l’aide de l’éditeur de thèmes pour personnaliser la mise en forme de tous les champs du formulaire. Après avoir créé un thème, effectuez les étapes suivantes pour l’appliquer à un formulaire :

1. Ouvrez votre formulaire en mode d’édition.
1. En mode d’édition, sélectionnez un composant, puis appuyez sur ![field-level](assets/field-level.png) > **Conteneur de formulaires adaptatifs**, puis appuyez sur ![cmppr](assets/cmppr.png).
1. Dans la barre latérale, sous Thème de formulaire adaptatif, sélectionnez le thème que vous avez créé à l’aide de l’éditeur de thèmes.

## Création d’une disposition de champ personnalisée {#create-a-custom-field-layout}

1. Ouvrez CRXDE Lite. L’URL par défaut est `https://[Server]:[Port]/crx/de`.
1. Copiez une disposition de champ du nœud /libs/fd/af/layouts/field (par exemple, defaultFieldLayout) vers le nœud /apps (par exemple, /apps/af-field-layout).
1. Renommez le nœud copié et le fichier defaultFieldLayout.jsp. Par exemple, errorOnRight.jsp.

1. Modifiez la valeur des propriétés qtip et jcr:description du nœud copié. Par exemple, redéfinissez la valeur des propriétés sur Erreur sur la droite

1. Pour ajouter de nouveaux styles et un nouveau comportement, créez une bibliothèque cliente sous le nœud /etc node.

   Par exemple, créez à l’emplacement /etc/af-field-layout-clientlib le nœud client-library. Ajoutez la propriété de catégories avec la valeur af.field.errorOnRight et le fichier style.less avec le code suivant :

   ```css
   .widgetErrorWrapper {
   
    height: 38px;
    margin: 5px;
   
    .guideFieldWidget{
    width: 60%;
    float: left; 
    }
   
    .guideFieldError{
    overflow:hidden;
    width:40%; 
    }
   
   }
   ```

1. Pour améliorer l’apparence et le comportement, incluez la bibliothèque client créée dans le fichier de dispositiion (errorOnRight.jsp).
1. Ouvrez la boîte de dialogue de modification et sélectionnez l’onglet **Style**. Dans la liste déroulante **Configurer la disposition de champ**, sélectionnez la disposition nouvellement créée, puis cliquez sur **OK**.

Le package ErrorOnRight.zip contient le code permettant d’afficher les messages d’erreur du côté droit des champs.

[Obtenir le fichier](assets/erroronright.zip)
