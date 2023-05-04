---
title: Enregistrer les formulaires sous forme de modèles
seo-title: Save forms as templates
description: Découvrez comment créer des modèles à partir de formulaires avec des données requises à plusieurs reprises.
seo-description: Learn how to create templates from forms with data required repeatedly.
uuid: 090c6271-4061-4adc-a063-9df4953b47ce
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e0df2f85-664a-47b3-a8c5-e986b975d421
exl-id: 355c4810-6e45-41cb-9b60-73225bd53526
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 37%

---

# Enregistrer les formulaires sous forme de modèles {#save-forms-as-templates}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Parfois, lorsque les utilisateurs remplissent un formulaire, les entrées de quelques champs restent les mêmes. Pour de telles instances, vous pouvez remplir les champs nécessitant des valeurs identiques dans chaque instance et enregistrer le formulaire ou le brouillon comme modèle. Désormais, chaque fois que vous créez une instance du modèle, les champs spécifiés sont déjà remplis avec les valeurs spécifiées dans le modèle. Cela vous permet de gagner du temps et vous évite les efforts nécessaires pour remplir le formulaire.

Procédez comme suit pour créer un modèle :

1. Ouvrez un formulaire et sélectionnez ou remplissez les champs dont les valeurs sont identiques presqu’à chaque fois que vous l’utilisez. Vous pouvez inclure une pièce jointe au modèle que vous ajoutez généralement lorsque vous remplissez le formulaire.
1. Appuyez sur l’icône **Enregistrer en tant que modèle** ![save_as_template](assets/save_as_template.png). Une boîte de dialogue pour indiquer le nom du modèle s’affiche.
1. Indiquez le nom du modèle et appuyez sur **Enregistrer**. Le modèle apparaît dans le dossier de modèles.

   S’il existe un modèle portant le même nom, une boîte de dialogue s’affiche pour confirmer le remplacement du modèle existant. Pour remplacer le modèle existant par un nouveau modèle, appuyez sur **Continuer** ou pour enregistrer le modèle sous un autre nom, appuyez sur **Annuler**.

Vous pouvez maintenant ouvrir le modèle enregistré. Chaque fois qu’un modèle est ouvert, un nouveau formulaire ou une nouvelle tâche est créé et le formulaire affiche les données enregistrées et les options. Grâce aux modèles, vous pouvez modifier les données préremplies, ajouter une pièce jointe, enregistrer en tant que brouillon, envoyer la tâche, ou les utiliser pour créer un autre modèle. Les modèles sont spécifiques aux appareils mobiles et ne sont pas synchronisés avec le serveur Adobe Experience Manager Forms.

Vous pouvez également supprimer un modèle s’il n’est plus nécessaire. Pour supprimer un modèle, accédez au dossier Templates, appuyez sur les points de suspension et appuyez sur **Supprimer le modèle**.

>[!NOTE]
>
>Un modèle est disponible localement et n’est pas synchronisé avec le serveur. L’effacement des données locales de l’application supprime le modèle.
