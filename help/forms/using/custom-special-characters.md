---
title: Caractères spéciaux personnalisés dans Correspondence Management
seo-title: Custom special characters in Correspondence Management
description: Découvrez comment ajouter des caractères spéciaux personnalisés dans Correspondence Management.
seo-description: Learn how to add custom special characters in Correspondence Management.
uuid: ac4f1353-f1ef-43b7-8e80-aba56a155e3f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 1b5e6746-3618-46fe-ba2d-ec76bb79de1d
feature: Correspondence Management
exl-id: a6206ae1-b71b-4066-b7a0-ce39a60d6dd0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 59%

---

# Caractères spéciaux personnalisés dans Correspondence Management {#custom-special-characters-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

Correspondence Management dispose d’une prise en charge par défaut intégrée de 210 caractères spéciaux que vous pouvez facilement insérer dans les lettres.

Vous pouvez par exemple insérer les caractères spéciaux suivants :

* Symboles de devise tels que €,￥et £
* Symboles mathématiques tels que ∑, √, ∂ et ^
* Les symboles de ponctuation comme « et ».

Vous pouvez insérer des caractères spéciaux sous forme de lettres :

* Dans [l’éditeur de texte](/help/forms/using/document-fragments.md#createtext).
* Dans un [module modifiable et en ligne dans une correspondance](/help/forms/using/create-correspondence.md#managecontent).

![caractères_spéciaux_dans_un_module_en_ligne](assets/specialcharactersinlinemodule.png)

L’administrateur peut ajouter la prise en charge de plus de caractères/de caractères spéciaux grâce à la personnalisation. Cet article fournit des instructions sur la manière d’ajouter la prise en charge de caractères spéciaux personnalisés supplémentaires.

## Ajout ou modification de la prise en charge des caractères spéciaux personnalisés dans Correspondence Management {#creatingfolderstructure}

Procédez comme suit pour ajouter la prise en charge des caractères spéciaux personnalisés :

1. Accédez à `https://[server]:[port]/[ContextPath]/crx/de` et connectez-vous en tant qu’administrateur.
1. Dans le dossier des applications, créez un dossier nommé **[!UICONTROL specialcharacters]** dont le chemin d’accès/la structure est similaire au dossier specialcharacters (situé dans le dossier textEditorConfig sous libs) :

   1. Cliquez avec le bouton droit sur le dossier **specialcharacters** au chemin d’accès suivant et sélectionnez **Nœud de recouvrement** :

      `/libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters`

   1. Assurez-vous que la boîte de dialogue du nœud de recouvrement possède les valeurs suivantes :

      **Chemin d’accès :** /libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters

      **Emplacement du recouvrement :** /apps/

      **Correspondance des types de nœud :** vérifié.

      >[!NOTE]
      >
      >N’apportez aucune modification à la branche /libs. Toute modification que vous apportez peut être perdue, car cette branche est sujette à des modifications lorsque vous :
      >
      >* Effectuez une mise à niveau sur votre instance
      >* Appliquer un correctif
      >* Installation d’un Feature Pack


   1. Cliquez sur **OK**, puis sur **Enregistrer tout**. Le dossier specialcharacters est créé dans le chemin d’accès spécifié.

      Après avoir créé la superposition, vérifiez les balises de structure de noeud. Chaque noeud créé dans /apps à l’aide de la superposition doit avoir la même classe et les mêmes propriétés que celles définies dans /libs pour ce noeud. Si une propriété ou une balise est manquante dans la structure de noeud sous l’emplacement /apps , synchronisez ses balises avec le noeud correspondant dans /libs.

1. Assurez-vous que la variable **[!UICONTROL textEditorConfig]** possède les propriétés et valeurs suivantes :

   | Nom | Type | Valeur |
   |---|---|---|
   | cmConfigurationType | Chaîne | cmTextEditorConfiguration |
   | cssPath | Chaîne | /libs/fd/cm/ma/gui/components/admin/createasset/textcontrol/clientlibs/textcontrol |

1. Cliquez avec le bouton droit sur le dossier **[!UICONTROL specialcharacters]** au chemin d’accès suivant et sélectionnez **Créer > Nœud enfant**, puis cliquez sur **Enregistrer tout** :

   /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters/&lt;yourchildnode>

1. Actualisez la page de l’interface utilisateur Éditeur de texte\Création de correspondance . Le noeud que vous avez ajouté est le dernier de la liste des caractères spéciaux dans l’interface utilisateur.
1. Cliquez sur **Enregistrer tout**.
1. Apportez les modifications nécessaires aux caractères spéciaux :

<table> 
 <tbody> 
  <tr> 
   <td><strong>To...</strong></td> 
   <td><strong>Effectuez les étapes suivantes</strong></td> 
  </tr> 
  <tr> 
   <td>Ajouter un caractère spécial personnalisé</td> 
   <td> 
    <ol> 
     <li>Ajoutez un nœud enfant sous « /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters » avec les propriétés obligatoires.</li> 
     <li>Cliquez sur Enregistrer tout</li> 
     <li>Actualisez la page de l’interface utilisateur Éditeur de texte\Création de correspondance pour afficher les modifications.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Mettre à jour les propriétés d’un caractère spécial existant</td> 
   <td> 
    <ol> 
     <li>Recouvrez le noeud à mettre à jour comme expliqué ci-dessus et vérifiez les balises et les classes.</li> 
     <li>Modifiez toutes les valeurs, telles que caption, value, endValue et multipleCaption. </li> 
     <li>Cliquez sur Enregistrer tout. </li> 
     <li>Actualisez la page de l’interface utilisateur Éditeur de texte\Création de correspondance pour afficher les modifications.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Masquer un caractère spécial</td> 
   <td> 
    <ol> 
     <li>Superposez le nœud à masquer sous « /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters ».</li> 
     <li>Ajoutez la propriété sling:hideResource (booléenne) au nœud à masquer (sous applications). </li> 
     <li>Cliquez sur Enregistrer tout. </li> 
     <li>Actualisez la page de l’interface utilisateur Éditeur de texte\Création de correspondance pour afficher les modifications.<br /> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Masquer plusieurs caractères spéciaux</td> 
   <td> 
    <ol> 
     <li>Ajoutez la propriété « sling:hideChildren (String or String[]) » sous « /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters ». </li> 
     <li>Ajoutez des noms de nœud (caractères spéciaux à masquer) sous forme de valeurs pour la propriété sling:hideChildren. </li> 
     <li>Cliquez sur Enregistrer tout. </li> 
     <li>Actualisez la page de l’interface utilisateur Éditeur de texte\Création de correspondance pour afficher les modifications.<br /> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Ordre des caractères spéciaux</td> 
   <td> 
    <ol> 
     <li>Ajoutez un nœud enfant sous « /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters » avec les propriétés obligatoires. </li> 
     <li>Ajoutez la propriété « sling:orderBefore (String) » au nœud enfant qui vient d’être créé. </li> 
     <li>Ajoutez le nom du nœud comme valeur devant laquelle le caractère spécial récemment ajouté doit être affiché. </li> 
     <li>Cliquez sur Enregistrer tout. </li> 
     <li>Actualisez la page de l’interface utilisateur Éditeur de texte\Création de correspondance pour afficher les modifications.<br /> </li> 
    </ol> </td> 
  </tr> 
 </tbody> 
</table>
