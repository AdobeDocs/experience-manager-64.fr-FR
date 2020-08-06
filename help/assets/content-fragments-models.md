---
title: Modèles de fragment de contenu
seo-title: Modèles de fragment de contenu
description: Les modèles de fragment de contenu sont utilisés pour créer des fragments de contenu avec du contenu structuré.
seo-description: Les modèles de fragment de contenu sont utilisés pour créer des fragments de contenu avec du contenu structuré.
uuid: 59176a32-1255-4a46-ad00-344bde843ea6
content-type: reference
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 45e67357-4524-4d25-b5f1-21182b8e803c
translation-type: tm+mt
source-git-commit: 8b83be510a67fadaa666f2ba96fbb3fc82b9cb3d
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 92%

---


# Modèles de fragment de contenu {#content-fragment-models}

>[!CAUTION]
>
>Certaines fonctionnalités de fragment de contenu nécessitent l’application de [AEM 6.4 Service Pack 2 (6.4.2.0) ou version ultérieure](../release-notes/sp-release-notes.md).

Les modèles de fragment de contenu définissent la structure du contenu pour vos[ fragments de contenu](content-fragments.md).

## Activation des modèles de fragment de contenu   {#enable-content-fragment-models}

>[!CAUTION]
>
>If you do not enable **[!UICONTROL Content Fragment Models]**, the **[!UICONTROL Create]** option will not be available for creating new models.

Pour activer les modèles de fragment de contenu, vous devez :

* activer l’utilisation des modèles de fragment de contenu dans Configuration Manager ;
* appliquer la configuration à votre dossier de ressources ;

### Activation des modèles de fragment de contenu dans Configuration Manager   {#enable-content-fragment-models-in-configuration-manager}

Pour [créer un nouveau modèle de fragment de contenu](#creating-a-content-fragment-model), vous **devez** d’abord activer ces modèles à l’aide du gestionnaire de configuration :

1. Accédez à **[!UICONTROL Outils]**, **[!UICONTROL Général]**, puis ouvrez l’**[!UICONTROL explorateur de configurations]**.
1. Sélectionnez l’emplacement approprié pour votre site web.
1. Utilisez le bouton **[!UICONTROL Créer]** pour ouvrir la boîte de dialogue.

   1. Spécifiez un **[!UICONTROL Titre]**.
   1. Sélectionnez **[!UICONTROL Modèles de fragment de contenu]** pour activer leur utilisation.

   ![cfm-6420-09](assets/cfm-6420-09.png)

1. Sélectionnez **[!UICONTROL Créer]** pour enregistrer la définition.

### Application de la configuration à votre dossier de ressources {#apply-the-configuration-to-your-assets-folder}

Lorsque la configuration **[!UICONTROL globale]** est activée pour les modèles de fragment de contenu, tous les modèles que les utilisateurs créent peuvent être utilisés dans n’importe quel dossier de ressources.

Pour utiliser d’autres configurations (c’est-à-dire à l’exclusion de la version globale) avec un dossier de ressources comparable, vous devez définir la connexion. Pour ce faire, vous devez utiliser **[!UICONTROL Configuration]** dans l’onglet **[!UICONTROL Cloud Services]** des **[!UICONTROL Propriétés du dossier]** du dossier approprié.

## Création d’un modèle de fragment de contenu {#creating-a-content-fragment-model}

1. Accédez à **[!UICONTROL Outils]**, **[!UICONTROL Ressources]**, puis ouvrez les **[!UICONTROL modèles de fragment de contenu]**.
1. Accédez au fichier adapté votre [configuration](#enable-content-fragment-models).
1. Utilisez le bouton **[!UICONTROL Créer]** pour ouvrir l’assistant.

   >[!CAUTION]
   >
   >Si[ l’utilisation des modèles de contenu du fragment n’a pas été activée](#enable-content-fragment-models), l’option **Créer** n’est pas disponible.

1. Spécifiez le **[!UICONTROL Titre du modèle]**. Vous pouvez également ajouter une **[!UICONTROL description]** si nécessaire.

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. Utilisez le bouton **[!UICONTROL Créer]** pour enregistrer le modèle vide. Un message indique que l’action a réussi. Vous pouvez alors sélectionner **[!UICONTROL Ouvrir]** pour publier immédiatement le modèle ou **[!UICONTROL Terminé]** pour revenir à la console.

## Définition de votre modèle de fragment de contenu   {#defining-your-content-fragment-model}

Le modèle de fragment de contenu définit la structure des fragments de contenu qui en résultent. À l’aide de l’éditeur de modèles, vous pouvez ajouter et configurer les champs obligatoires :

>[!CAUTION]
>
>La modification d’un modèle de fragment de contenu existant peut avoir un impact sur les fragments dépendants.

1. Accédez à **[!UICONTROL Outils]**, **[!UICONTROL Ressources]**, puis ouvrez les **[!UICONTROL modèles de fragment de contenu]**.

1. Accédez au dossier contenant votre modèle de fragment de contenu.
1. Ouvrez le modèle requis pour l’**[!UICONTROL édition]**. Utilisez l’action rapide ou sélectionnez le modèle puis l’action dans la barre d’outils.

   Une fois ouvert, l’éditeur de modèles affiche :

   * à gauche : les champs déjà définis 
   * à droite : les **[!UICONTROL types de données]** disponibles pour la création des champs (et les **[!UICONTROL propriétés]** à utiliser une fois les champs créés).

   >[!NOTE]
   >
   >When a field is **Required**, the **Label** indicated in the left pane will be marked with an asterix (**&amp;ast;**).

   ![cfm-6420-12](assets/cfm-6420-12.png)

1. **Pour ajouter un champ**

   * Faites glisser un type de données à l’emplacement souhaité pour un champ :

   ![cfm-6420-11](assets/cfm-6420-11.png)

   * Une fois qu’un champ a été ajouté au modèle, le panneau de droite affiche les **propriétés** qui peuvent être définies pour ce type de données spécifique. Vous pouvez définir ce qui est obligatoire pour ce champ. Par exemple :

   ![cfm-6420-13](assets/cfm-6420-13.png)

1. **Pour supprimer un champ**

   Sélectionnez le champ, puis cliquez/appuyez sur l’icône représentant une corbeille. Vous serez alors invité à confirmer l’opération.

   ![cf-32](assets/cf-32.png)

1. Après avoir ajouté tous les champs requis et défini les propriétés, utilisez le bouton **[!UICONTROL Enregistrer]** pour conserver la définition. Par exemple :

   ![cfm-6420-14](assets/cfm-6420-14.png)

## Suppression d’un modèle de fragment de contenu {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>La suppression d’un modèle de fragment de contenu peut avoir un impact sur les fragments dépendants.

Pour supprimer un modèle de fragment de contenu :

1. Accédez à **[!UICONTROL Outils]**, **[!UICONTROL Ressources]**, puis ouvrez les **[!UICONTROL modèles de fragment de contenu]**.

1. Accédez au dossier contenant votre modèle de fragment de contenu.
1. Sélectionnez votre modèle, puis utilisez l’option **[!UICONTROL de suppression]** de la barre d’outils.

   >[!NOTE]
   >
   >Si le modèle est référencé, un avertissement s’affiche. Prenez alors les mesures qui s’imposent.

## Publication d’un modèle de fragment de contenu   {#publishing-a-content-fragment-model}

Les modèles de fragment de contenu doivent être publiés avant ou pendant la publication des fragments de contenu dépendants.

Pour publier un modèle de fragment de contenu :

1. Accédez à **[!UICONTROL Outils]**, **[!UICONTROL Ressources]**, puis ouvrez les **[!UICONTROL modèles de fragment de contenu]**.

1. Accédez au dossier contenant votre modèle de fragment de contenu.
1. Sélectionnez votre modèle, puis l’option de **[!UICONTROL publication]** dans la barre d’outils.

   >[!NOTE]
   >
   >Si vous publiez un fragment de contenu pour lequel le modèle n’a pas encore été publié, une liste de sélection indique cela, ainsi que le fait que le modèle sera publié avec le fragment.

