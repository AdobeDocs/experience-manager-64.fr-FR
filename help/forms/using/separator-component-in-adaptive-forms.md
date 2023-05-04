---
title: Composant Separator dans les formulaires adaptatifs
seo-title: Separator component in adaptive forms
description: Vous pouvez utiliser le composant séparateur pour isoler visuellement les sections d’un formulaire.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
feature: Adaptive Forms
exl-id: 7e37401a-8c63-4711-8a33-61e6bd4b419f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 49%

---

# Composant Separator dans les formulaires adaptatifs {#separator-component-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez utiliser le composant séparateur pour isoler visuellement les panneaux d’un formulaire. Vous pouvez définir l’aspect général et le style d’un composant séparateur en spécifiant les propriétés suivantes du composant :

* **Nom de l’élément :** Indique le nom du composant. Les expressions SOM s’adressent au composant avec la valeur spécifiée dans le champ Nom de l’élément .
* **Épaisseur :** indique l’épaisseur en pixels du composant séparateur.
* **Colspan :** Indique le nombre de colonnes sur lesquelles s’étend un composant de séparateur.
* **Classe CSS :** spécifie la classe CSS personnalisée pour le composant séparateur
* **Styles en ligne :** avec AEM Forms, vous pouvez désormais appliquer des styles CSS en ligne à chaque composant de formulaire adaptatif et prévisualiser les modifications en temps réel.

Pour définir les propriétés d’un composant séparateur :

1. Sélectionnez un composant séparateur et appuyez sur ![cmppr](assets/cmppr.png). Les propriétés s’ouvrent dans la barre latérale.
1. Cliquez sur un onglet de la section Propriétés CSS intégrées pour spécifier les propriétés CSS. Par exemple : a. Dans l’onglet Champ, cliquez sur **Ajouter un élément**. Une ligne avec deux champs est ajoutée.
1. Dans le premier champ de gauche, spécifiez une propriété CSS3 à appliquer. Par exemple : **border**. Vous pouvez également sélectionner une propriété en cliquant sur la flèche vers le bas. La liste déroulante n’est pas exhaustive et vous pouvez spécifier n’importe quel nom de propriété CSS3 prise en charge dans ce champ.
1. Dans le champ adjacent, spécifiez une valeur valide pour la propriété CSS3 spécifiée. Par exemple : **noir 3px**.
1. Cliquez sur **Ajouter un élément** pour définir une autre propriété et sa valeur.
1. Cliquez sur **Aperçu** pour prévisualiser les modifications dans le formulaire.
1. Cliquez sur **OK** pour confirmer les modifications ou **Annuler **pour quitter la boîte de dialogue sans aucune modification.
